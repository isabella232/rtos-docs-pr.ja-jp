---
title: 第 2 章 - Azure RTOS NetX Duo DHCP クライアントのインストールと使用
description: この章では、Azure RTOS NetX Duo DHCP クライアント コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8c3df64be337b557f492617c1ef20adc7c0f8d6e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810940"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dhcp-client"></a><span data-ttu-id="86cb3-103">第 2 章 - Azure RTOS NetX Duo DHCP クライアントのインストールと使用</span><span class="sxs-lookup"><span data-stu-id="86cb3-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo DHCP Client</span></span>

<span data-ttu-id="86cb3-104">この章では、Azure RTOS NetX Duo DHCP クライアント コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo DHCP Client component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="86cb3-105">製品の配布</span><span class="sxs-lookup"><span data-stu-id="86cb3-105">Product Distribution</span></span>

<span data-ttu-id="86cb3-106">Azure RTOS NetX Duo は、<https://github.com/azure-rtos/netxduo> のパブリック ソース コード リポジトリから入手できます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-106">Azure RTOS NetX Duo can be obtained from our public source code repository at <https://github.com/azure-rtos/netxduo>.</span></span> <span data-ttu-id="86cb3-107">パッケージには、次のファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="86cb3-107">The package includes the following files:</span></span>

- <span data-ttu-id="86cb3-108">**nxd_dhcp_client.h**: NetX Duo DHCP のヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="86cb3-108">**nxd_dhcp_client.h**: Header file for NetX Duo DHCP</span></span>
- <span data-ttu-id="86cb3-109">**nxd_dhcp_client.c**: DHCP NetX Duo の C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="86cb3-109">**nxd_dhcp_client.c**: C Source file for DHCP NetX Duo</span></span>
- <span data-ttu-id="86cb3-110">**nxd_dhcp_client.pdf**: NetX Duo DHCP のユーザー ガイド</span><span class="sxs-lookup"><span data-stu-id="86cb3-110">**nxd_dhcp_client.pdf**: User Guide for NetX Duo DHCP</span></span> 
    - <span data-ttu-id="86cb3-111">**demo_netxduo_dhcp.c**: NetX Duo DHCP クライアントのデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="86cb3-111">**demo_netxduo_dhcp.c**: NetX Duo DHCP Client demonstration</span></span>
    - <span data-ttu-id="86cb3-112">**demo_netxduo_multihome_dhcp_client.c**: 複数のインターフェイスで DHCP を使用する NetX Duo DHCP クライアントのデモ</span><span class="sxs-lookup"><span data-stu-id="86cb3-112">**demo_netxduo_multihome_dhcp_client.c**: NetX Duo DHCP Client demonstration of DHCP on multiple interfaces</span></span>

## <a name="dhcp-installation"></a><span data-ttu-id="86cb3-113">DHCP のインストール</span><span class="sxs-lookup"><span data-stu-id="86cb3-113">DHCP Installation</span></span>

<span data-ttu-id="86cb3-114">NetX Duo DHCP クライアントを使用するためには、前述の配布全体を、NetX Duo がインストールされているのと同じディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-114">To use NetX Duo DHCP Client, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="86cb3-115">たとえば、NetX Duo がディレクトリ " *\threadx\arm7\green*" にインストールされている場合、*nxd_dhcp_client.h* ファイルと *nxd_dhcp_client.c* ファイルをこのディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="86cb3-115">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_dhcp_client.h* and *nxd_dhcp_client.c* files should be copied into this directory.</span></span>

## <a name="using-dhcp"></a><span data-ttu-id="86cb3-116">DHCP の使用</span><span class="sxs-lookup"><span data-stu-id="86cb3-116">Using DHCP</span></span>

<span data-ttu-id="86cb3-117">NetX Duo 用 DHCP は簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-117">Using DHCP for NetX Duo is easy.</span></span> <span data-ttu-id="86cb3-118">基本的には、ThreadX と NetX Duo を使用するために、アプリケーション コードにそれぞれ *tx_api.h* と *nx_api.h* をインクルードした後に、*nxd_dhcp_client.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-118">Basically, the application code must include *nxd_dhcp_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX Duo, respectively.</span></span> <span data-ttu-id="86cb3-119">*nxd_dhcp_client.h* をインクルードすると、このガイドで後述する DHCP 関数呼び出しを、そのアプリケーション コードで実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-119">Once *nxd_dhcp_client.h* is included, the application code is then able to make the DHCP function calls specified later in this guide.</span></span> <span data-ttu-id="86cb3-120">このアプリケーションには、ビルド プロセスで *nxd_dhcp_client.c* もインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-120">The application must also include *nxd_dhcp_client.c* in the build process.</span></span> <span data-ttu-id="86cb3-121">このファイルは、他のアプリケーション ファイルと同様にコンパイルし、オブジェクトとしてアプリケーションのファイルと共にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-121">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="86cb3-122">NetX DHCP の使用に必要なものはこれですべてです。</span><span class="sxs-lookup"><span data-stu-id="86cb3-122">This is all that is required to use NetX DHCP.</span></span>

<span data-ttu-id="86cb3-123">DHCP では NetX Duo UDP サービスを利用するため、DHCP を使用するときは、前もって *nx_udp_enable* を呼び出して UDP を有効にしておく必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="86cb3-123">Note that since DHCP utilizes NetX Duo UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DHCP.</span></span>

<span data-ttu-id="86cb3-124">割り当て済みの IP アドレスを取得するために、DHCP クライアントでは、要求メッセージおよびオプション 50 "要求された IP アドレス" を DHCP サーバーに送信することで DHCP 処理を開始できます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-124">To obtain a previously assigned IP address, the DHCP Client can initiate the DHCP process with the Request message and Option 50 “Requested IP Address” to the DHCP Server.</span></span> <span data-ttu-id="86cb3-125">DHCP サーバーでは、クライアントに IP アドレスを割り当てる場合は ACK メッセージで、拒否する場合は NACK で応答します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-125">The DHCP Server will respond with either an ACK message if it grants the IP address to the Client or a NACK if it refuses.</span></span> <span data-ttu-id="86cb3-126">後者の場合、DHCP クライアントでは Discover メッセージを送信し、要求された IP アドレスを与えずに、DCHP 処理を Init の状態からやり直します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-126">In the latter case, the DHCP Client restarts the DHCP process at the Init state with a Discover message and no requested IP address.</span></span> <span data-ttu-id="86cb3-127">ホスト アプリケーションでは最初に DHCP クライアントを作成し、次に *nx_dhcp_request_client_ip* API サービスを呼び出して要求する IP アドレスを設定し、その後で *nx_dhcp_start* により DHCP 処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-127">The host application first creates the DHCP Client, then calls the *nx_dhcp_request_client_ip* API service to set the requested IP address before starting the DHCP process with *nx_dhcp_start*.</span></span> <span data-ttu-id="86cb3-128">詳細は、このドキュメントの他の箇所に挙げる DHCP アプリケーションの例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="86cb3-128">An example DHCP application is provided elsewhere in this document for more details.</span></span>

## <a name="in-the-bound-state"></a><span data-ttu-id="86cb3-129">バインド状態</span><span class="sxs-lookup"><span data-stu-id="86cb3-129">In the Bound State</span></span>

<span data-ttu-id="86cb3-130">DHCP クライアントがバインド状態である間、DHCP クライアント スレッドはクライアントの状態を一定 (NX_DHCP_TIME_INTERVAL で指定された) の間隔で処理し、クライアントに割り当てられた IP リース時間の残り時間を減らします。</span><span class="sxs-lookup"><span data-stu-id="86cb3-130">While the DHCP Client is in the bound state, the DHCP Client thread processes the Client state once per interval (as specified by NX_DHCP_TIME_INTERVAL) and decrements the time remaining on the IP lease assigned to the Client.</span></span> <span data-ttu-id="86cb3-131">更新時間が経過すると、DHCP クライアントの状態は RENEW 状態に更新され、クライアントでは DHCP サーバーによる更新を要求します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-131">When the renewal time has elapsed the DHCP Client state is updated to the RENEW state where the Client will request a renewal from the DHCP Server.</span></span>

## <a name="sending-dhcp-messages-to-the-server"></a><span data-ttu-id="86cb3-132">サーバーへの DHCP メッセージの送信</span><span class="sxs-lookup"><span data-stu-id="86cb3-132">Sending DHCP Messages To The Server</span></span>

<span data-ttu-id="86cb3-133">DHCP クライアントには、ホスト アプリケーションが DHCP サーバーにメッセージを送信するための API サービスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="86cb3-133">The DHCP Client has API services that allow the host application to send a message to the DHCP Server.</span></span> <span data-ttu-id="86cb3-134">これらのサービスは、ホスト アプリケーションで DHCP クライアント プロトコルを手動で実行するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="86cb3-134">Note these services are NOT intended for the host application to manually run the DHCP Client protocol.</span></span>

  - <span data-ttu-id="86cb3-135">*nx_dhcp_release*: ホスト アプリケーションがネットワークを離れるとき、または IP アドレスを手放す必要があるときに、RELEASE メッセージをサーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-135">*nx_dhcp_release*: this sends a RELEASE message to the Server when the host application is either leaving the network or needs relinquish its IP address.</span></span>
  - <span data-ttu-id="86cb3-136">*nx_dhcp_decline*: ホスト アプリケーションが、DHCP クライアントの判断とは無関係に、自身の IP アドレスが既に使用されていると判断した場合に、DECLINE メッセージをサーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-136">*nx_dhcp_decline*: this sends a DECLINE message to the Server if the host application determines independently of the DHCP Client that its IP address is already in use.</span></span>
  - <span data-ttu-id="86cb3-137">*nx_dhcp_forcerenew*: サーバーに FORCERENEW メッセージを送信します</span><span class="sxs-lookup"><span data-stu-id="86cb3-137">*nx_dhcp_forcerenew*: this sends a FORCERENEW message to the Server</span></span>
  - <span data-ttu-id="86cb3-138">*nx_dhcp_send_request*: *nx_dhcp_client.h* に指定された DHCP メッセージの種類を引数に取ってサーバーにメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-138">*nx_dhcp_send_request*: This takes as an argument a DHCP message type, as specified in *nxd_dhcp_client.h*, and sends the message to the Server.</span></span> <span data-ttu-id="86cb3-139">DHCP INFORM メッセージを送信することが主な目的です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-139">This is intended primarily for sending the DHCP INFORM message.</span></span>

<span data-ttu-id="86cb3-140">これらのサービスの詳細については、[DHCP サービスの説明](chapter3.md)に関するページを参照してください</span><span class="sxs-lookup"><span data-stu-id="86cb3-140">See [Description of DHCP Services](chapter3.md) for more information about these services</span></span> 

## <a name="starting-and-stopping-the-dhcp-client"></a><span data-ttu-id="86cb3-141">DHCP クライアントの起動と停止</span><span class="sxs-lookup"><span data-stu-id="86cb3-141">Starting and Stopping the DHCP Client</span></span>

<span data-ttu-id="86cb3-142">DHCP クライアントを停止するには、バインド状態になっているかどうかにかかわらず、ホスト アプリケーションで *nx_dhcp_stop* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-142">To stop the DHCP Client, regardless if it has achieved a bound state, the host application calls *nx_dhcp_stop*.</span></span>

<span data-ttu-id="86cb3-143">DHCP クライアントを再起動するには、最初に、ホスト アプリケーションで前述の *nx_dhcp_stop* サービスを使用して DHCP クライアントを停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-143">To restart a DHCP Client, the host application must first stop the DHCP Client using the *nx_dhcp_stop* service described above.</span></span> <span data-ttu-id="86cb3-144">それから、ホストで *nx_dhcp_start* を呼び出して DHCP クライアントを再開できます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-144">Then the host can call *nx_dhcp_start* to resume the DHCP Client.</span></span> <span data-ttu-id="86cb3-145">古い DHCP クライアント プロファイル、たとえば他のネットワーク上にあった以前の DHCP サーバーから取得したものの削除をホスト アプリケーションが求める場合、そのホスト アプリケーションで *nx_dhcp_reinitialize* を呼び出してこのタスクを内部的に実行し、その後で *nx_dhcp_start* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-145">If the host application wishes to clear a previous DHCP Client profile, for example, one obtained from a previous DHCP Server on another network, the host application should call *nx_dhcp_reinitialize* to perform this task internally before calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="86cb3-146">典型的なシーケンスは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-146">A typical sequence might be:</span></span>

```c
nx_dhcp_stop(&my_dhcp);
nx_dhcp_reinitialize(&my_dhcp);
nx_dhcp_start(&my_dhcp);
```

<span data-ttu-id="86cb3-147">DHCP アプリケーションを単一の DHCP インターフェイスで実行している場合、DHCP クライアントを停止すると、DHCP クライアントのタイマーも無効になります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-147">For DHCP applications running on only a single DHCP interface, stopping the DHCP Client also inactivates the DHCP CLIENT timer.</span></span> <span data-ttu-id="86cb3-148">こうして IP リース時間の残り時間が監視されなくなります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-148">Thus it is no longer keeping track of the time remaining on the IP lease.</span></span> <span data-ttu-id="86cb3-149">特定のインターフェイスで DHCP クライアントを停止すると、DHCP クライアントのタイマーは無効になりませんが、そのインターフェイスで IP リース時間の残り時間のタイマーが停止します</span><span class="sxs-lookup"><span data-stu-id="86cb3-149">Stopping DHCP Client on a particular interface will not inactivate the DHCP Client timer but will stop timer updates to the time remaining on the IP lease on that interface</span></span>

<span data-ttu-id="86cb3-150">そのため、ホスト アプリケーションでネットワークの再起動または切り替えが必要な場合を除き、DHCP クライアントを停止することは推奨しません。</span><span class="sxs-lookup"><span data-stu-id="86cb3-150">Therefore, stopping the DHCP Client is not advised unless the host application requires rebooting or switching networks.</span></span>

## <a name="using-the-dhcp-client-with-auto-ip"></a><span data-ttu-id="86cb3-151">Auto IP と共に DHCP クライアントを使用</span><span class="sxs-lookup"><span data-stu-id="86cb3-151">Using the DHCP Client with Auto IP</span></span>

<span data-ttu-id="86cb3-152">DHCP サーバーが使用可能であること、または応答していることが保証されない場合に DHCP と Auto IP による IP アドレスの割り当てが保証されるアプリケーションでは、NetX Duo DHCP クライアントを Auto IP プロトコルと共に使用します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-152">The NetX Duo DHCP Client works concurrently with the Auto IP protocol in applications where DHCP and Auto IP guarantee an address where a DHCP Server is not guaranteed to be available or responding.</span></span> <span data-ttu-id="86cb3-153">ただし、ホストがサーバーを検出できない、または IP アドレスの割り当てを受けることができない場合は、ローカル IP アドレスの処理を Auto IP プロトコルに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-153">However, If the host is unable to detect a Server or get an IP address assigned, it can switch to the Auto IP protocol for a local IP address.</span></span> <span data-ttu-id="86cb3-154">ただし、そうする前に DHCP クライアントを一時的に停止して、Auto IP が "プローブ" と "防御" の段階を過ぎるのを待つことを推奨します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-154">However before doing so, it is advisable to stop the DHCP Client temporarily while Auto IP goes through the “probe” and “defense” stages.</span></span> <span data-ttu-id="86cb3-155">Auto IP アドレスがホストに割り当てられたら DHCP クライアントを再起動できます。また、DHCP サーバーが実際に使用できるようになったら、アプリケーション実行中に DHCP サーバーによって提供される IP アドレスを、ホストの IP アドレスとして受け入れることができます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-155">Once an Auto IP address is assigned to the host, the DHCP Client can be restarted and if a DHCP Server does become available, the host IP address can accept the IP address offered by the DHCP Server while the application is running.</span></span>

<span data-ttu-id="86cb3-156">NetX Duo Auto IP には、IP アドレスが変更された場合にホストがそのアドレスの振る舞いを監視するための、アドレス変更通知があります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-156">The NetX Duo Auto IP has an address change notification for the host to monitor its activities in the event of an IP address change.</span></span>

## <a name="packet-chaining"></a><span data-ttu-id="86cb3-157">パケット チェーン</span><span class="sxs-lookup"><span data-stu-id="86cb3-157">Packet Chaining</span></span>

<span data-ttu-id="86cb3-158">パケット プールとメモリ リソースをより効率的に使用するために、DHCP クライアントでは、イーサネット ドライバーからチェーン化された受信パケット (ドライバーの MTU を超えるデータグラム) を処理できます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-158">For more efficient use of packet pool and memory resources, the DHCP Client can handle incoming chained packets (datagrams exceeding the driver MTU) from the Ethernet driver.</span></span> <span data-ttu-id="86cb3-159">ドライバーがこの機能を備えている場合、アプリケーションではパケットを受信するためのパケット プールを、必須の NX_DHCP_PACKET_PAYLOAD バイト以下に設定できます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-159">If the driver has this capability, the application can set the packet pool for receiving packets to below the mandatory NX_DHCP_PACKET_PAYLOAD bytes.</span></span> <span data-ttu-id="86cb3-160">NX_DHCP_PACKET_PAYLOAD では、物理ネットワーク (通常はイーサネット) フレームと、548 バイトの DHCP メッセージ データ (IP と UDP) に対応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-160">NX_DHCP_PACKET_PAYLOAD should accommodate the physical network (typically Ethernet) frame, plus 548 bytes of DHCP message data, and IP and UDP.</span></span>

<span data-ttu-id="86cb3-161">なお、アプリケーションでは、パケット ペイロードに加え、DHCP クライアントの一部であり、かつ DHCP メッセージを送信するために使用されるパケット プール内のパケットの数を最適化できます。予想される使用量と DHCP クライアント メッセージのサイズに基づいて、サイズが最適化されます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-161">Note that the application can optimize the packet payload and number of packets in the packet pool that is part of the DHCP Client, and which is used for sending DHCP messages out. It can optimize the size based on expected usage and size of the DHCP Client messages.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="86cb3-162">簡単なシステムの例</span><span class="sxs-lookup"><span data-stu-id="86cb3-162">Small Example System</span></span>

<span data-ttu-id="86cb3-163">NetX Duo を使用する方法の例を以下の図 1.1 に示します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-163">An example of how to use NetX Duo is shown in Figure 1.1 below.</span></span> <span data-ttu-id="86cb3-164">アプリケーション スレッド エントリ関数 *my_thread_entry* は 101 行目に作成されます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-164">The application thread entry function “*my_thread_entry*” is created at line 101.</span></span> <span data-ttu-id="86cb3-165">正常に作成されると、108 行目の *nx_dhcp_start* 呼び出しを使用して DHCP 処理が開始されます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-165">After successful creation, DHCP processing is initiated with the *nx_dhcp_start* call at line 108.</span></span> <span data-ttu-id="86cb3-166">この時点で、DHCP クライアント スレッド タスクは、個別に DHCP サーバーへの接続を試みます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-166">At this point, the DHCP Client thread task separately attempts to contact a DHCP server.</span></span> <span data-ttu-id="86cb3-167">この処理中、アプリケーションのコードは、95 行目の *nx_ip_status_check* サービス (セカンダリ インターフェイスの場合は *nx_ip_interface_status_check*) を使用して、有効な IP アドレスが IP インスタンスに登録されるのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-167">During this process, the application code waits for a valid IP address to be registered with the IP instance using the *nx_ip_status_check* service (or *nx_ip_interface_status_check* for a secondary interface) on line 95.</span></span> <span data-ttu-id="86cb3-168">これは、待機時間を短縮するオプションのあるループではより一般的です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-168">This is more commonly done in a loop with a shorter wait option.</span></span>

<span data-ttu-id="86cb3-169">127 行目を過ぎた時点で DHCP では有効な IP アドレスを受け取っており、アプリケーションでは必要に応じて NetX Duo の TCP/IP サービスを使用しながら、処理を進めることができます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-169">After line 127, DHCP has received a valid IP address and the application can then proceed, utilizing NetX Duo TCP/IP services as desired.</span></span>

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_client.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_DHCP                 my_dhcp;

/* Define function prototypes.  */

void    my_thread_entry(ULONG thread_input);
void    my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point.  */
intmain()
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

    /* Create “my_thread”.  */
      tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                        pointer, DEMO_STACK_SIZE, 2, 2, 
                        TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duo system.  */
    nx_system_initialize();

    /* Create a packet pool.  */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                     1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error.  */
    if (status)
        error_counter++;

    /* Create an IP instance without an IP address. */
    status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
                          0xFFFFFF00, &my_pool, my_netx_driver, pointer, 
                          DEMO_STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors.  */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for my IP Instance.  */
    status =  nx_arp_enable(&my_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
        error_counter++;

    /* Enable UDP.  */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
 }


 /* Define my thread.  */

 void    my_thread_entry(ULONG thread_input)
 {

 UINT        status;
 ULONG       actual_status;
 NX_PACKET   *my_packet;

    /* Wait for the link to come up.  */
    do
    {
    /* Get the link status.  */
        status =  nx_ip_status_check(&my_ip, NX_IP_LINK_ENABLED, 
                                     &actual_status, 100);
    } while (status != NX_SUCCESS);

    /* Create a DHCP instance.  */
    status =  nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

    /* Check for DHCP create error.  */
    if (status)
        error_counter++;

    /* Start DHCP.  */
    nx_dhcp_start(&my_dhcp);

    /* Check for DHCP start error.  */
    if (status)
        error_counter++;

    /* Wait for IP address to be resolved through DHCP.  */
    nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                       (ULONG *) &status, 100000);

    /* Check to see if we have a valid IP address.  */
    if (status)
    {
      error_counter++;
      return;
    }
    else
    {

  /* Yes, a valid IP address is now on lease…  All NetX Duo
        services are available.
    }
 }

```
## <a name="multi-server-environments"></a><span data-ttu-id="86cb3-170">マルチサーバー環境</span><span class="sxs-lookup"><span data-stu-id="86cb3-170">Multi-Server Environments</span></span>

<span data-ttu-id="86cb3-171">複数の DHCP サーバーが存在するネットワークでは、DHCP クライアントは最初に受信した DHCP サーバーの Offer メッセージを受け入れて Request 状態に進み、受信した他のオファーをすべて無視します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-171">On networks where there is more than one DHCP Server, the DHCP Client accepts the first received DHCP Server Offer message, advances to the Request state, and ignores any other received offers.</span></span>

## <a name="arp-probes"></a><span data-ttu-id="86cb3-172">ARP プローブ</span><span class="sxs-lookup"><span data-stu-id="86cb3-172">ARP Probes</span></span>

<span data-ttu-id="86cb3-173">DHCP クライアントを構成することで、DHCP サーバーによる IP アドレスの割り当てが済んだ後で、1 つまたは複数の ARP プローブを送信して、その IP アドレスがまだ使用されていないことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-173">The DHCP Client can be configured to send one or more ARP probes after IP address assignment from the DHCP Server to verify the IP address is not already in use.</span></span> <span data-ttu-id="86cb3-174">RFC 2131 は ARP プローブのステップを推奨しています。これは特に複数の DHCP サーバーが存在する環境で重要です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-174">The ARP probe step is recommended by RFC 2131 and is particularly important in environments with more than one DHCP Server.</span></span> <span data-ttu-id="86cb3-175">ホスト アプリケーションで NX_DHCP_CLIENT_SEND_ARP_PROBE オプションを有効にすると (他の ARP プローブ オプションについては、第 2 章の「**構成オプション**」を参照)、DHCP クライアントは "自分宛ての" ARP プローブを送信し、指定された時間応答を待ちます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-175">If the host application enables the NX_DHCP_CLIENT_SEND_ARP_PROBE option (see **Configuration Options** in Chapter Two for additional ARP probe options), the DHCP Client will send a ‘self addressed’ ARP probe and wait for the specified time for a response.</span></span> <span data-ttu-id="86cb3-176">何も受信できない場合、DHCP クライアントはバインド状態に進みます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-176">If none is received, the DHCP Client advances to the Bound state.</span></span> <span data-ttu-id="86cb3-177">応答を受信した場合、DHCP クライアントでは、アドレスが既に使用されているものとみなします。</span><span class="sxs-lookup"><span data-stu-id="86cb3-177">If a response is received, the DHCP Client assumes the address is already in use.</span></span> <span data-ttu-id="86cb3-178">すると自動的に DECLINE メッセージがサーバーに送信され、クライアントを再初期化して、INIT 状態から DHCP プローブを再開します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-178">It automatically sends a DECLINE message to the Server, and reinitializes the Client to restart the DHCP probes again from the INIT state.</span></span> <span data-ttu-id="86cb3-179">これにより DHCP ステート マシンが再起動し、クライアントが DISCOVER メッセージをもう一度サーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-179">This restarts the DHCP state machine and the Client sends another DISCOVER message to the Server.</span></span>

## <a name="bootp-protocol"></a><span data-ttu-id="86cb3-180">BOOTP プロトコル</span><span class="sxs-lookup"><span data-stu-id="86cb3-180">BOOTP Protocol</span></span>

<span data-ttu-id="86cb3-181">DHCP クライアントでは、DHCP プロトコル同様に BOOTP プロトコルもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="86cb3-181">The DHCP Client also supports the BOOTP protocol as well the DHCP protocol.</span></span> <span data-ttu-id="86cb3-182">このオプションを有効にして DHCP の代わりに BOOTP を使用するには、ホスト アプリケーションで NX_DHCP_BOOTP_ENABLE 構成オプションを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-182">To enable this option and use BOOTP instead of DHCP, the host application must set the NX_DHCP_BOOTP_ENABLE configuration option.</span></span> <span data-ttu-id="86cb3-183">ホスト アプリケーションでは、BOOTP プロトコルでも特定の IP アドレスを要求できます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-183">The host application can still request specific IP addresses in the BOOTP protocol.</span></span> <span data-ttu-id="86cb3-184">なお、BOOTP はホスト オペレーティング システムの読み込みに使用される場合もありますが、DHCP クライアントではこれをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="86cb3-184">However, the DHCP Client does not support loading the host operating system as BOOTP is sometimes used to do.</span></span>

## <a name="dhcp-on-a-secondary-interface"></a><span data-ttu-id="86cb3-185">セカンダリ インターフェイスでの DHCP</span><span class="sxs-lookup"><span data-stu-id="86cb3-185">DHCP on a Secondary Interface</span></span>

<span data-ttu-id="86cb3-186">NetX Duo DHCP クライアントは、既定のプライマリ インターフェイスの代わりにセカンダリ インターフェイスでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-186">The NetX Duo DHCP Client can run on secondary interfaces rather than the default primary interface.</span></span>

<span data-ttu-id="86cb3-187">セカンダリ ネットワーク インターフェイスで NetX Duo DHCP クライアントを実行するには、ホスト アプリケーションで、*nx_dhcp_set_interface_index* API サービスを使用して、DHCP クライアントのインターフェイス インデックスをセカンダリ インターフェイスに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-187">To run NetX Duo DHCP Client on a secondary network interface, the host application must set the interface index of the DHCP Client to the secondary interface using the *nx_dhcp_set_interface_index* API service.</span></span> <span data-ttu-id="86cb3-188">インターフェイスは、*nx_ip_interface_attach* サービスを使用して、プライマリ ネットワーク インターフェイスに前もってアタッチしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-188">The interface must already be attached to the primary network interface using the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="86cb3-189">セカンダリ インターフェイスのアタッチの詳細については、NetX Duo ユーザー ガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="86cb3-189">See the NetX Duo User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="86cb3-190">次に示すのは (図 1.2)、ホスト アプリケーションをセカンダリ インターフェイス上の DHCP サーバーに接続するシステムの例です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-190">Below is an example system (Figure 1.2) in which the host application connects to the DHCP server on its secondary interface.</span></span> <span data-ttu-id="86cb3-191">65 行目で、null 値の IP アドレスを使用してセカンダリ インターフェイスを IP タスクにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="86cb3-191">On line 65, the secondary interface is attached to the IP task with a null IP address.</span></span> <span data-ttu-id="86cb3-192">104 行目で、DHCP クライアント インスタンスを作成してから、*nx_dhcp_set_interface_index* を呼び出して、DHCP クライアントのインターフェイス インデックスを 1 に設定します (自身のインデックスが 0 であるプライマリ インターフェイスとの差に相当)。</span><span class="sxs-lookup"><span data-stu-id="86cb3-192">On line 104, after the DHCP Client instance is created, the DHCP Client interface index is set to 1 (e.g. the offset from the primary interface which itself is index 0) by calling *nx_dhcp_set_interface_index*.</span></span> <span data-ttu-id="86cb3-193">その後 108 行目で DHCP クライアントが起動できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-193">Then the DHCP Client is ready to be started in line 108.</span></span>

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_client.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_DHCP                 my_dhcp;

/* Define function prototypes.  */

void    my_thread_entry(ULONG thread_input);
void    my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point.  */

intmain()
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

    /* Create “my_thread”.  */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                      pointer, DEMO_STACK_SIZE, 
                      2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duo system.  */
    nx_system_initialize();

  /* Create a packet pool.  */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                     1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error.  */
    if (status)
        error_counter++;

    /* Create an IP instance without an IP address. */
    status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
                           0xFFFFFF00, &my_pool, my_netx_driver, pointer, STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors.  */
    if (status)
        error_counter++;

    status =  _nx_ip_interface_attach(&ip_0, "port_2", IP_ADDRESS(0, 0, 0,0), 
                                       0xFFFFFF00UL, my_netx_driver);

    /* Enable ARP and supply ARP cache memory for my IP Instance.  */
    status =  nx_arp_enable(&my_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
        error_counter++;

    /* Enable UDP.  */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
}


void    my_thread_entry(ULONG thread_input)
{

UINT        status;
ULONG       status;
NX_PACKET   *my_packet;

    /* Wait for the link to come up.  */
    do
    {
      /* Get the link status.  */
        status =  nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,& status,100);
    } while (status != NX_SUCCESS);

    /* Create a DHCP instance.  */
    status =  nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

    /* Check for DHCP create error.  */
    if (status)
        error_counter++;

    /* Set the DHCP client interface to the secondary interface. */
    status = nx_dhcp_set_interface_index(&my_dhcp, 1);


    /* Start DHCP.  */
    nx_dhcp_start(&my_dhcp);

    /* Check for DHCP start error.  */
    if (status)
        error_counter++;

    /* Wait for IP address to be resolved through DHCP.  */
    nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                       (ULONG *) &status, 100000);

    /* Check to see if we have a valid IP address.  */
    if (status)
    {
        error_counter++;
        return;
    }
    else
    {
    /* Yes, a valid IP address is now on lease…  All NetX Duo
        services are available.*/
    }
}
```

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a><span data-ttu-id="86cb3-194">複数のインターフェイスでの DHCP クライアントの同時実行</span><span class="sxs-lookup"><span data-stu-id="86cb3-194">DHCP Client on Multiple Interfaces Simultaneously</span></span>

<span data-ttu-id="86cb3-195">DHCP クライアントを複数のインターフェイスで実行するには、*nx_api.h* の NX_MAX_PHYSICAL_INTERFACES を、デバイスに接続している物理インターフェイスの数に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-195">To run DHCP Client on multiple interfaces, NX_MAX_PHYSICAL_INTERFACES in *nx_api.h* must be set to the number of physical interfaces connected to the device.</span></span> <span data-ttu-id="86cb3-196">既定値は 1 です (プライマリ インターフェイスを表しています)。</span><span class="sxs-lookup"><span data-stu-id="86cb3-196">By default, this value is 1 (e.g. the primary interface).</span></span> <span data-ttu-id="86cb3-197">追加のインターフェイスを IP インスタンスに登録するには *nx_ip_interface_attach* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-197">To register an additional interface to the IP instance use the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="86cb3-198">セカンダリ インターフェイスのアタッチの詳細については、NetX Duo ユーザー ガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="86cb3-198">See the NetX Duo User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="86cb3-199">次のステップでは、*nxd_dhcp_client.h* の NX_DHCP_CLIENT_MAX_RECORDS を、DHCP を同時に実行する予定のインターフェイスの最大数に設定します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-199">The next step is to set the NX_DHCP_CLIENT_MAX_RECORDS in *nxd_dhcp_client.h* to the maximum number of interfaces expected to run DHCP simultaneously.</span></span> <span data-ttu-id="86cb3-200">NX_DHCP_CLIENT_MAX_RECORDS を NX_MAX_PHYSICAL_INTERFACES と一致させる必要はありません。</span><span class="sxs-lookup"><span data-stu-id="86cb3-200">Note that NX_DHCP_CLIENT_MAX_RECORDS does not have to equal NX_MAX_PHYSICAL_INTERFACES.</span></span> <span data-ttu-id="86cb3-201">たとえば、NX_MAX_PHYSICAL_INTERFACES を 3、NX_DHCP_CLIENT_MAX_RECORDS を 2 に設定できます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-201">For example, NX_MAX_PHYSICAL_INTERFACES can be 3 and NX_DHCP_CLIENT_MAX_RECORDS equal to 2.</span></span> <span data-ttu-id="86cb3-202">この構成だと、DHCP を同時に実行できるのが、3 つの物理インターフェイスのうち 2 つだけということになります (3 つの物理インターフェイスのうちの 2 つは、あらゆる時点でどの組み合わせにもなり得ます)。</span><span class="sxs-lookup"><span data-stu-id="86cb3-202">In this configuration, only two interfaces (and they can be any two of the three physical interfaces at any time) of the three physical interfaces can run DHCP at any one time.</span></span> <span data-ttu-id="86cb3-203">DHCP クライアント レコードは、ネットワーク インターフェイスに対して 1 対 1 でマッピングされません。たとえば、クライアント レコード 1 と物理インターフェイス インデックス 1 が自動的に関連付けられることはありません。</span><span class="sxs-lookup"><span data-stu-id="86cb3-203">DHCP Client Records do not have a one to one mapping to network interfaces e.g. Client Record 1 does not automatically correlate to physical interface index 1.</span></span>

<span data-ttu-id="86cb3-204">NX_DHCP_CLIENT_MAX_RECORDS を NX_MAX_PHYSICAL_INTERFACES より大きく設定することもできますが、使用しないクライアント レコードを作成することになり、メモリの使用効率が悪くなります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-204">NX_DHCP_CLIENT_MAX_RECORDS can also be set to greater than NX_MAX_PHYSICAL_INTERFACES but this would create unused client records and be an inefficient use of memory.</span></span>

<span data-ttu-id="86cb3-205">どのインターフェイスで DHCP を起動する場合も、前もってアプリケーションで *nx_dhcp_interface_enable* を呼び出し、それらのインターフェイスを有効にしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-205">Before it can start DHCP on any interface, the application must enable those interfaces by calling *nx_dhcp_interface_enable*.</span></span> <span data-ttu-id="86cb3-206">*nx_dhcp_create* の呼び出しで自動的に有効になるプライマリ インターフェイスはこの例外です (後述の *nx_dhcp_interface_disable* サービスを使用すれば無効にできます)。</span><span class="sxs-lookup"><span data-stu-id="86cb3-206">Note that the exception is the primary interface which is automatically enabled in the *nx_dhcp_create* call (and which can be disabled using the *nx_dhcp_interface_disable* service discussed below).</span></span>

<span data-ttu-id="86cb3-207">DHCP を実行している他のインターフェイスとは無関係に、いつでも DHCP でインターフェイスを無効にしたり、またはそのインターフェイス上で DHCP を停止したりできます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-207">At any time, an interface can be disabled for DHCP or DHCP can be stopped on that interface independently of other interfaces running DHCP.</span></span>

<span data-ttu-id="86cb3-208">前述のとおり特定のインターフェイスで DHCP を有効にするには、*nx_dhcp_interface_enable* サービスを使用し、入力の引数で物理インターフェイスのインデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-208">As mentioned above, to enable a specific interface for DHCP, use the *nx_dhcp_interface_enable* service and specify the physical interface index in the input argument.</span></span> <span data-ttu-id="86cb3-209">インターフェイスは NX_DHCP_CLIENT_MAX_RECORDS で指定された数まで有効にできますが、唯一の制約として、入力の引数で指定するインターフェイス インデックスは NX_MAX_PHYSICAL_INTERFACES 未満でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="86cb3-209">Up to NX_DHCP_CLIENT_MAX_RECORDS interfaces can be enabled with the only limitation that the interface index input argument be less than NX_MAX_PHYSICAL_INTERFACES.</span></span>

<span data-ttu-id="86cb3-210">特定のインターフェイスで DHCP を起動するには *nx_dhcp_interface_start* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-210">To start DHCP on a specific interface, use the *nx_dhcp_interface_start* service.</span></span> <span data-ttu-id="86cb3-211">有効になっているすべてのインターフェイスで DHCP を起動するには *nx_dhcp_start* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-211">To start DHCP on all enabled interfaces, use the *nx_dhcp_start* service.</span></span> <span data-ttu-id="86cb3-212">(既に DHCP を起動しているインターフェイスでは *nx_dhcp_start* の影響はありません。)</span><span class="sxs-lookup"><span data-stu-id="86cb3-212">(Interfaces that have already started DHCP will not be affected by *nx_dhcp_start*.)</span></span>

<span data-ttu-id="86cb3-213">インターフェイスで DHCP を停止するには、*nx_dhcp_interface_stop* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-213">To stop DHCP on an interface, use the *nx_dhcp_interface_stop* service.</span></span> <span data-ttu-id="86cb3-214">DHCP はそのインターフェイスで前もって起動しておく必要があります。そうでないとエラー状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-214">DHCP must already have started on that interface or an error status is returned.</span></span> <span data-ttu-id="86cb3-215">有効になっているすべてのインターフェイスで DHCP を停止するには *nx_dhcp_stop* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-215">To stop DHCP on all enabled interfaces, use the *nx_dhcp_stop* service.</span></span> <span data-ttu-id="86cb3-216">DHCP は、他のインターフェイスとは別個に、いつでも停止できます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-216">DHCP can be stopped independently of other interfaces at any time.</span></span>

<span data-ttu-id="86cb3-217">既存の DHCP クライアント サービスのほとんどには、"インターフェイス" と同等のものがあります。たとえば、*nx_dhcp_release* のインターフェイス固有で同等であるのが *nx_dhcp_interface_release* です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-217">Most of the existing DHCP Client services have an ‘interface’ equivalent e.g. *nx_dhcp_interface_release* is the interface specific equivalent of *nx_dhcp_release.*</span></span> <span data-ttu-id="86cb3-218">単一のインターフェイスで DHCP クライアントを構成する場合、そのアクションに違いはありません。</span><span class="sxs-lookup"><span data-stu-id="86cb3-218">If DHCP Client is configured for a single interface, they perform the same action.</span></span>

<span data-ttu-id="86cb3-219">インターフェイス別ではない DHCP クライアント サービスは通常すべてのインターフェイスに適用されますが、そうでない場合もあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="86cb3-219">Note that non-interface specific DHCP Client services typically apply to all interfaces but not all.</span></span> <span data-ttu-id="86cb3-220">後者の場合、インターフェイス別ではないサービスは、DHCP が有効になっているインターフェイスのうち、インターフェイス レコードの DHCP クライアント リストを検索して最初に見つかったものに適用されます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-220">In the latter case, the non-interface specific service applies to the first DHCP enabled interface found in searching the DHCP Client list of interface records.</span></span> <span data-ttu-id="86cb3-221">複数のインターフェイスで DHCP を有効にしたときに、インターフェイス別でないサービスがどのように機能するかは、第 3 章の「**サービスの説明**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86cb3-221">See **Description of Services** in Chapter Three for how a non-interface specific service performs when multiple interfaces are enabled for DHCP.</span></span>

<span data-ttu-id="86cb3-222">下のシーケンス例では、IP インスタンスに 2 つのネットワーク インターフェイスがあり、セカンダリ インターフェイスで先に DHCP を実行します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-222">In the example sequence below, the IP instance has two network interfaces and first runs DHCP on the secondary interface.</span></span> <span data-ttu-id="86cb3-223">しばらく後で、プライマリ インターフェイスで DHCP が起動します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-223">At some time later, it starts DHCP on the primary interface.</span></span> <span data-ttu-id="86cb3-224">それからプライマリ インターフェイスで IP アドレスを解放し、プライマリ インターフェイスで DHCP を再起動します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-224">Then it releases the IP address on the primary interface and restarts DHCP on the primary interface:</span></span>

```c
nx_dhcp_create(&my_dhcp_client); /* By default this enables primary interface for DHCP. */

nx_dhcp_interface_enable(&my_dhcp_client, 1); /* Secondary interface is enabled. */

nx_dhcp_interface_start(&my_dhcp_client, 1); /* DHCP is started on secondary interface. */

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); /* DHCP is started on primary interface. */

nx_dhcp_interface_release(&my_dhcp_client, 0); /* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); /* DHCP is restarted on primary interface. */
```

<span data-ttu-id="86cb3-225">インターフェイス別のすべてのサービスのリストは、第 3 章の「**サービスの説明**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86cb3-225">For a complete list of interface specific services see **Description of Services** in Chapter Three.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="86cb3-226">構成オプション</span><span class="sxs-lookup"><span data-stu-id="86cb3-226">Configuration Options</span></span>

<span data-ttu-id="86cb3-227">*nxd_dhcp_client.h* にあるユーザーが構成可能な DHCP オプションを使用すると、ホスト アプリケーションで、DHCP クライアントの特定の要件を細かく調整できます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-227">User configurable DHCP options in *nxd_dhcp_client.h* allow the host application to fine tune DHCP Client for its particular requirements.</span></span> <span data-ttu-id="86cb3-228">次のリストにそれらのパラメーターを挙げます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-228">The following is a list of these parameters:</span></span>  
  
- <span data-ttu-id="86cb3-229">**NX_DHCP_ENABLE_BOOTP**: このオプションを有効にすると、DHCP の代わりに BOOTP プロトコルが有効になります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-229">**NX_DHCP_ENABLE_BOOTP**: Defined, this option enables the BOOTP protocol instead of DHCP.</span></span> <span data-ttu-id="86cb3-230">既定では、このオプションは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="86cb3-230">By default this option is disabled.</span></span>
- <span data-ttu-id="86cb3-231">**NX_DHCP_CLIENT_RESTORE_STATE**: 定義されていると、DHCP クライアントで、リース時間の残り時間を含む現在の DHCP クランアントのライセンスの "状態" を保存し、DHCP クライアント アプリケーションを再起動してもこの状態を復元できるようになります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-231">**NX_DHCP_CLIENT_RESTORE_STATE**: If defined, this enables the DHCP Client to save its current DHCP Client license ‘state’ including time remaining on the lease, and restore this state between DHCP Client application reboots.</span></span> <span data-ttu-id="86cb3-232">既定値は、無効です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-232">The default value is disabled.</span></span>
- <span data-ttu-id="86cb3-233">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL**: 設定されている場合、DHCP クライアントで専用のパケット プールを作成しなくなります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-233">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL**: If set, the DHCP Client will not create its own packet pool.</span></span> <span data-ttu-id="86cb3-234">ホスト アプリケーションで *nx_dhcp_packet_pool_set* サービスを使用して DHCP クライアントのパケット プールを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-234">The host application must use the *nx_dhcp_packet_pool_set* service to set the DHCP Client packet pool.</span></span> <span data-ttu-id="86cb3-235">既定値は、無効です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-235">The default value is disabled.</span></span>
- <span data-ttu-id="86cb3-236">**NX_DHCP_CLIENT_SEND_ARP_PROBE**: 定義されている場合、IP アドレスを割り当てられた後で DHCP クライアントが ARP プローブを送信し、割り当てられた DHCP アドレスがまだ他のホストに所持されていないことを確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-236">**NX_DHCP_CLIENT_SEND_ARP_PROBE**: Defined, this enables the DHCP Client to send an ARP probe after IP address assignment to verify the assigned DHCP address is not owned by another host.</span></span> <span data-ttu-id="86cb3-237">既定では、このオプションは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="86cb3-237">By default, this option is disabled.</span></span>
- <span data-ttu-id="86cb3-238">**NX_DHCP_ARP_PROBE_WAIT**: ARP プローブを送信してから DHCP クライアントが応答を待つ時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-238">**NX_DHCP_ARP_PROBE_WAIT**: Defines the length of time the DHCP Client waits for a response after sending an ARP probe.</span></span> <span data-ttu-id="86cb3-239">既定値は 1 秒 (1 x NX_IP_PERIODIC_RATE) です</span><span class="sxs-lookup"><span data-stu-id="86cb3-239">The default value is one second (1 \* NX_IP_PERIODIC_RATE)</span></span>
- <span data-ttu-id="86cb3-240">**NX_DHCP_ARP_PROBE_MIN**: ARP プローブを送信する間隔の最小値を定義します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-240">**NX_DHCP_ARP_PROBE_MIN**: Defines the minimum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="86cb3-241">既定値は 1 秒です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-241">The value is defaulted to 1 second.</span></span>
- <span data-ttu-id="86cb3-242">**NX_DHCP_ARP_PROBE_MAX**: ARP プローブを送信する間隔の最大値を定義します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-242">**NX_DHCP_ARP_PROBE_MAX**: Defines the maximum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="86cb3-243">既定値は 2 秒です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-243">The value is defaulted to 2 seconds.</span></span>
- <span data-ttu-id="86cb3-244">**NX_DHCP_ARP_PROBE_NUM**: DHCP サーバーが割り当てた IP アドレスが既に使用されているかどうかを判断するために ARP プローブを送信する回数を定義します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-244">**NX_DHCP_ARP_PROBE_NUM**: Defines the number of ARP probes sent for determining if the IP address assigned by the DHCP server is already in use.</span></span> <span data-ttu-id="86cb3-245">既定値は 3 回です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-245">The value is defaulted to 3 probes.</span></span>
- <span data-ttu-id="86cb3-246">**NX_DHCP_RESTART_WAIT**: DHCP クライアントに割り当てた IP アドレスが既に使用されている場合に、DHCP クライアントが DHCP の再起動を待つ時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-246">**NX_DHCP_RESTART_WAIT**: Defines the length of time the DHCP Client waits to restart DHCP if the IP address assigned to the DHCP Client is already in use.</span></span> <span data-ttu-id="86cb3-247">既定値は 10 秒です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-247">The value is defaulted to 10 seconds.</span></span>
- <span data-ttu-id="86cb3-248">**NX_DHCP_CLIENT_MAX_RECORDS**: DHCP クライアント インスタンスに保存するインターフェイス レコードの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-248">**NX_DHCP_CLIENT_MAX_RECORDS**: Specifies the maximum number of interface records to save to the DHCP Client instance.</span></span> <span data-ttu-id="86cb3-249">DHCP クライアント インターフェイス レコードは、特定のインターフェイスで実行している DHCP クライアントのレコードです。</span><span class="sxs-lookup"><span data-stu-id="86cb3-249">A DHCP Client interface record is a record of the DHCP Client running on a specific interface.</span></span> <span data-ttu-id="86cb3-250">既定値は、物理インターフェイス数 (NX_MAX_PHYSICAL_INTERFACES) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="86cb3-250">The default value is set as physical interfaces count(NX_MAX_PHYSICAL_INTERFACES).</span></span>
- <span data-ttu-id="86cb3-251">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION**: 定義されていると、DHCP メッセージ サイズ オプションの最大数まで、DHCP クライアントからメッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-251">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION**: Defined, this enables the DHCP Client to send maximum DHCP message size option.</span></span> <span data-ttu-id="86cb3-252">既定では、このオプションは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="86cb3-252">By default, this option is disabled.</span></span>
- <span data-ttu-id="86cb3-253">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK**: 定義されていると、nx_dhcp_create の呼び出しで入力したホスト名の文字と長さが無効でないかどうかを、DHCP クライアントで確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-253">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK**: Defined, this enables the DHCP Client to check the input host name in the nx_dhcp_create call for invalid characters or length.</span></span> <span data-ttu-id="86cb3-254">既定では、このオプションは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="86cb3-254">By default, this option is disabled.</span></span>
- <span data-ttu-id="86cb3-255">**NX_DHCP_THREAD_PRIORITY**: DHCP スレッドの優先度です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-255">**NX_DHCP_THREAD_PRIORITY**: Priority of the DHCP thread.</span></span> <span data-ttu-id="86cb3-256">既定では、この値によって DHCP スレッドが優先度 3 で 実行されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-256">By default, this value specifies that the DHCP thread runs at priority 3.</span></span>
- <span data-ttu-id="86cb3-257">**NX_DHCP_THREAD_STACK_SIZE**: DHCP スレッドのスタックのサイズです。</span><span class="sxs-lookup"><span data-stu-id="86cb3-257">**NX_DHCP_THREAD_STACK_SIZE**: Size of the DHCP thread stack.</span></span> <span data-ttu-id="86cb3-258">既定のサイズは 2048 バイトです。</span><span class="sxs-lookup"><span data-stu-id="86cb3-258">By default, the size is 2048 bytes.</span></span>
- <span data-ttu-id="86cb3-259">**NX_DHCP_TIME_INTERVAL**: DHCP クライアント タイマーの有効期限関数を実行する秒単位の間隔です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-259">**NX_DHCP_TIME_INTERVAL**: Interval in seconds when the DHCP Client timer expiration function executes.</span></span> <span data-ttu-id="86cb3-260">この関数では、DHCP 処理のすべてのタイムアウトが更新されます。たとえば、メッセージを再送する必要がある場合や、DHCP クライアントの状態が変更された場合などです。</span><span class="sxs-lookup"><span data-stu-id="86cb3-260">This function updates all the timeouts in the DHCP process e.g. if messages should be retransmitted or DHCP Client state changed.</span></span> <span data-ttu-id="86cb3-261">既定値は 1 秒です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-261">By default, this value is 1 second.</span></span>
- <span data-ttu-id="86cb3-262">**NX_DHCP_OPTIONS_BUFFER_SIZE**: DHCP のオプションのバッファーのサイズです。</span><span class="sxs-lookup"><span data-stu-id="86cb3-262">**NX_DHCP_OPTIONS_BUFFER_SIZE**: Size of DHCP options buffer.</span></span> <span data-ttu-id="86cb3-263">既定値は 312 バイトです。</span><span class="sxs-lookup"><span data-stu-id="86cb3-263">By default, this value is 312 bytes.</span></span>
- <span data-ttu-id="86cb3-264">**NX_DHCP_PACKET_PAYLOAD**: DHCP クライアントのパケットのペイロードのサイズをバイト単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-264">**NX_DHCP_PACKET_PAYLOAD**: Specifies the size in bytes of the DHCP Client packet payload.</span></span> <span data-ttu-id="86cb3-265">既定値は NX_DHCP_MINIMUM_IP_DATAGRAM + 物理ヘッダーのサイズです。</span><span class="sxs-lookup"><span data-stu-id="86cb3-265">The default value is NX_DHCP_MINIMUM_IP_DATAGRAM + physical header size.</span></span> <span data-ttu-id="86cb3-266">有線ネットワークでの物理ヘッダー サイズは、通常イーサネット フレームのサイズです。</span><span class="sxs-lookup"><span data-stu-id="86cb3-266">The physical header size in a wireline network is usually the Ethernet frame size.</span></span>
- <span data-ttu-id="86cb3-267">**NX_DHCP_PACKET_POOL_SIZE**: DHCP クライアントのパケット プールのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-267">**NX_DHCP_PACKET_POOL_SIZE**: Specifies the size of the DHCP Client packet pool.</span></span> <span data-ttu-id="86cb3-268">既定値は 5 x NX_DHCP_PACKET_PAYLOAD です。これは、パケット 4 個に、内部のパケット プールのオーバーヘッドを処理できるサイズを加えたものです。</span><span class="sxs-lookup"><span data-stu-id="86cb3-268">The default value is (5 \*NX_DHCP_PACKET_PAYLOAD) which will provide four packets plus room for internal packet pool overhead.</span></span>
- <span data-ttu-id="86cb3-269">**NX_DHCP_MIN_RETRANS_TIMEOUT**: クライアントのメッセージに対する DHCP サーバーの応答を受け取ってからメッセージが再送されるまでの最小待機時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-269">**NX_DHCP_MIN_RETRANS_TIMEOUT**: Specifies the minimum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="86cb3-270">既定値は RFC 2131 で推奨されている 4 秒です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-270">The default value is the RFC 2131 recommended 4 seconds.</span></span>
- <span data-ttu-id="86cb3-271">**NX_DHCP_MAX_RETRANS_TIMEOUT**: クライアントのメッセージに対する DHCP サーバーの応答を受け取ってからメッセージが再送されるまでの最大待機時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-271">**NX_DHCP_MAX_RETRANS_TIMEOUT**: Specifies the maximum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="86cb3-272">既定値は 64 秒です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-272">The default value is 64 seconds.</span></span>
- <span data-ttu-id="86cb3-273">**NX_DHCP_MIN_RENEW_TIMEOUT**: DHCP クライアントを IP アドレスにバインドした後、DHCP サーバーのメッセージを受信してから更新要求を送信するまでの、最小待機時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-273">**NX_DHCP_MIN_RENEW_TIMEOUT**: Specifies minimum wait option for receiving a DHCP Server message and sending a renewal request after the DHCP Client is bound to an IP address.</span></span> <span data-ttu-id="86cb3-274">既定値は 60 秒です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-274">The default value is 60 seconds.</span></span> <span data-ttu-id="86cb3-275">ただし、DHCP クライアントでは、DHCP サーバーのメッセージで指定される Renew および Rebind の有効期限を使用してから、更新のタイムアウト時間の既定最小値に戻ります。</span><span class="sxs-lookup"><span data-stu-id="86cb3-275">However, the DHCP Client uses the Renew and Rebind expiration times from the DHCP server message before defaulting to the minimum renew timeout.</span></span>
- <span data-ttu-id="86cb3-276">**NX_DHCP_TYPE_OF_SERVICE**: DHCP UDP 要求に必要なサービスの種類です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-276">**NX_DHCP_TYPE_OF_SERVICE**: Type of service required for the DHCP UDP requests.</span></span> <span data-ttu-id="86cb3-277">既定では、この値は通常の IP パケット サービスを示す NX_IP_NORMAL に定義されています。</span><span class="sxs-lookup"><span data-stu-id="86cb3-277">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="86cb3-278">**NX_DHCP_FRAGMENT_OPTION**: DHCP UDP 要求の断片化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="86cb3-278">**NX_DHCP_FRAGMENT_OPTION**: Fragment enable for DHCP UDP requests.</span></span> <span data-ttu-id="86cb3-279">既定値は NX_DONT_FRAGMENT であり DHCP UDP の断片化は無効になっています。</span><span class="sxs-lookup"><span data-stu-id="86cb3-279">By default, this value is NX_DONT_FRAGMENT to disable DHCP UDP fragmenting.</span></span>
- <span data-ttu-id="86cb3-280">**NX_DHCP_TIME_TO_LIVE**: このパケットが通過できるルーターの数を指定します。この数を超えるとパケットは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="86cb3-280">**NX_DHCP_TIME_TO_LIVE**: Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="86cb3-281">既定値は 0x80 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="86cb3-281">The default value is set to 0x80.</span></span>
- <span data-ttu-id="86cb3-282">**NX_DHCP_QUEUE_DEPTH**: 受信キューの深さの最大値を指定します。</span><span class="sxs-lookup"><span data-stu-id="86cb3-282">**NX_DHCP_QUEUE_DEPTH**: Specifies the number of maximum depth of receive queue.</span></span> <span data-ttu-id="86cb3-283">既定値は 4 です。</span><span class="sxs-lookup"><span data-stu-id="86cb3-283">The default value is set to 4.</span></span>