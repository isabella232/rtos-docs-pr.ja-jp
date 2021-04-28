---
title: 第 2 章 - Azure RTOS NetX DHCP Client のインストールと使用
description: この章では、Azure RTOS NetX DHCP のクライアント コンポーネントのインストール、セットアップ、使用に関するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9224a4df70b8199032066e30108250a3baeb65f5
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811615"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dhcp-client"></a><span data-ttu-id="0eda8-103">第 2 章 - Azure RTOS NetX DHCP Client のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="0eda8-103">Chapter 2 - Installation and use of Azure RTOS NetX DHCP Client</span></span>

<span data-ttu-id="0eda8-104">この章では、Azure RTOS NetX DHCP のコンポーネントのインストール、セットアップ、使用に関するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX DHCP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="0eda8-105">製品の配布パッケージ</span><span class="sxs-lookup"><span data-stu-id="0eda8-105">Product Distribution</span></span>

<span data-ttu-id="0eda8-106">NetX の DHCP は [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-106">DHCP for NetX is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="0eda8-107">このパッケージには、下に挙げるとおり、ソース ファイル 2 つと、このドキュメントを含む PDF ファイル 1 つが含まれています:</span><span class="sxs-lookup"><span data-stu-id="0eda8-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="0eda8-108">**nx_dhcp.h** NetX の DHCP のヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="0eda8-108">**nx_dhcp.h** Header file for DHCP for NetX</span></span>

- <span data-ttu-id="0eda8-109">**nx_dhcp.c** NetX の DHCP の C 言語のソース ファイル</span><span class="sxs-lookup"><span data-stu-id="0eda8-109">**nx_dhcp.c** C Source file for DHCP for NetX</span></span>

- <span data-ttu-id="0eda8-110">**nx_dhcp.pdf** NetX の DHCP の説明書の PDF ファイル</span><span class="sxs-lookup"><span data-stu-id="0eda8-110">**nx_dhcp.pdf** PDF description of DHCP for NetX</span></span>

- <span data-ttu-id="0eda8-111">**demo_netx_dhcp.c** NetX DHCP のデモ</span><span class="sxs-lookup"><span data-stu-id="0eda8-111">**demo_netx_dhcp.c** NetX DHCP demonstration</span></span>

- <span data-ttu-id="0eda8-112">**demo_netx_multihome_dhcp_client.c** 複数のインターフェイスで DHCP を使用する NetX DHCP Client のデモ</span><span class="sxs-lookup"><span data-stu-id="0eda8-112">**demo_netx_multihome_dhcp_client.c** NetX DHCP Client demonstration of DHCP on multiple interfaces</span></span>

## <a name="dhcp-installation"></a><span data-ttu-id="0eda8-113">DHCP のインストール</span><span class="sxs-lookup"><span data-stu-id="0eda8-113">DHCP Installation</span></span>

<span data-ttu-id="0eda8-114">NetX で DHCP を使用するには、NetX がインストールされているのと同じディレクトリに、前述の配布パッケージを丸ごとコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-114">To use DHCP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="0eda8-115">たとえば、NetX が " *\threadx\arm7\green*" ディレクトリにインストールされている場合は、*nx_dhcp.h* ファイルと *nx_dhcp.c* ファイルをこのディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0eda8-115">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_dhcp.h* and *nx_dhcp.c* files should be copied into this directory.</span></span>

## <a name="using-dhcp"></a><span data-ttu-id="0eda8-116">DHCP を使用する</span><span class="sxs-lookup"><span data-stu-id="0eda8-116">Using DHCP</span></span>

<span data-ttu-id="0eda8-117">NetX DHCP の使用方法は簡単です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-117">Using DHCP for NetX is easy.</span></span> <span data-ttu-id="0eda8-118">ThreadX と NetX をそれぞれ使用するためには、基本的に、アプリケーションのコードで *tx_api.h* と *nx_api.h* をインクルードしてから *nx_dhcp.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-118">Basically, the application code must include *nx_dhcp.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="0eda8-119">*nx_dhcp.h* をインクルードすると、このガイドで後述する DHCP の関数を、そのアプリケーションのコードで呼び出せるようになります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-119">Once *nx_dhcp.h* is included, the application code is then able to make the DHCP function calls specified later in this guide.</span></span> <span data-ttu-id="0eda8-120">また、アプリケーションのビルドには *nx_dhcp.c* を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-120">The application must also include *nx_dhcp.c* in the build process.</span></span> <span data-ttu-id="0eda8-121">このファイルは、他のアプリケーション ファイルと同様にコンパイルし、オブジェクトとしてアプリケーションのファイルと共にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-121">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="0eda8-122">NetX DHCP の使用に必要なものはこれですべてです。</span><span class="sxs-lookup"><span data-stu-id="0eda8-122">This is all that is required to use NetX DHCP.</span></span>

<span data-ttu-id="0eda8-123">DHCP では NetX UDP サービスを利用するため、DHCP を使用するときは、前もって *nx_udp_enable* を呼び出して UDP を有効にしておく必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0eda8-123">Note that since DHCP utilizes NetX UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DHCP.</span></span>

<span data-ttu-id="0eda8-124">割り当て済みの IP アドレスを取得するために、DHCP クライアントは、要求メッセージおよびオプション 50 "要求された IP アドレス" を DHCP サーバーに送信することで DHCP 処理を開始できます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-124">To obtain a previously assigned IP address, the DHCP Client can initiate the DHCP process with the Request message and Option 50 “Requested IP Address” to the DHCP Server.</span></span> <span data-ttu-id="0eda8-125">DHCP サーバーは、クライアントに IP アドレスを割り当てる場合は ACK メッセージで応答し、拒否する場合は NACK で応答します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-125">The DHCP Server will respond with either an ACK message if it grants the IP address to the Client or a NACK if it refuses.</span></span> <span data-ttu-id="0eda8-126">後者の場合、DHCP クライアントから Discover メッセージが送信され、要求された IP アドレスを与えずに、DHCP 処理を Init の状態からやり直します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-126">In the latter case, the DHCP Client restarts the DHCP process at the Init state with a Discover message and no requested IP address.</span></span> <span data-ttu-id="0eda8-127">ホスト アプリケーションは最初に DHCP クライアントを作成し、次に *nx_dhcp_request_client_ip* API サービスを呼び出して要求する IP アドレスを設定し、その後で *nx_dhcp_start* により DHCP 処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-127">The host application first creates the DHCP Client, then calls the *nx_dhcp_request_client_ip* API service to set the requested IP address before starting the DHCP process with *nx_dhcp_start*.</span></span> <span data-ttu-id="0eda8-128">詳細は、このドキュメントの他の箇所に挙げる DHCP アプリケーションの例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0eda8-128">An example DHCP application is provided elsewhere in this document for more details.</span></span>

## <a name="in-the-bound-state"></a><span data-ttu-id="0eda8-129">バインド状態</span><span class="sxs-lookup"><span data-stu-id="0eda8-129">In the Bound State</span></span>

<span data-ttu-id="0eda8-130">DHCP クライアントがバインド状態である間、DHCP クライアント スレッドはクライアントの状態を一定間隔で (NX_DHCP_TIME_INTERVAL で指定された間隔で) 処理し、クライアントに割り当てられた IP アドレスのリースの残り時間を減らします。</span><span class="sxs-lookup"><span data-stu-id="0eda8-130">While the DHCP Client is in the bound state, the DHCP Client thread processes the Client state once per interval (as specified by NX_DHCP_TIME_INTERVAL) and decrements the time remaining on the IP lease assigned to the Client.</span></span> <span data-ttu-id="0eda8-131">更新時間が経過すると、DHCP クライアントの状態は RENEW 状態に更新され、クライアントは DHCP サーバーによる更新を要求します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-131">When the renewal time has elapsed the DHCP Client state is updated to the RENEW state where the Client will request a renewal from the DHCP Server.</span></span>


## <a name="sending-dhcp-messages-to-the-server"></a><span data-ttu-id="0eda8-132">DHCP メッセージをサーバーに送信する</span><span class="sxs-lookup"><span data-stu-id="0eda8-132">Sending DHCP Messages To The Server</span></span>

<span data-ttu-id="0eda8-133">DHCP クライアントには、ホスト アプリケーションが DHCP サーバーにメッセージを送信するための API サービスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="0eda8-133">The DHCP Client has API services that allow the host application to send a message to the DHCP Server.</span></span> <span data-ttu-id="0eda8-134">これらのサービスは、ホスト アプリケーションで直接 DHCP クライアント プロトコルを実行することを意図したものではありません。主な用途はメッセージの送信であり、DHCP クライアントの状態を更新することではありません。</span><span class="sxs-lookup"><span data-stu-id="0eda8-134">Note these services are NOT intended for the host application to manually run the DHCP Client protocol as they primarily send the message without necessarily updating the DHCP Client internal state.</span></span>

  - <span data-ttu-id="0eda8-135">*nx_dhcp_release*: ホスト アプリケーションがネットワークを離れるとき、または IP アドレスを手放す必要があるときに、RELEASE メッセージをサーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-135">*nx_dhcp_release*: this sends a RELEASE message to the Server when the host application is either leaving the network or needs relinquish its IP address.</span></span>

  - <span data-ttu-id="0eda8-136">*nx_dhcp_decline*: ホスト アプリケーションが、DHCP クライアントの判断とは無関係に、自身の IP アドレスが既に使用されていると判断した場合に、DECLINE メッセージをサーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-136">*nx_dhcp_decline*: this sends a DECLINE message to the Server if the host application determines independently of the DHCP Client that its IP address is already in use.</span></span>

  - <span data-ttu-id="0eda8-137">*nx_dhcp_forcerenew*: サーバーに FORCERENEW メッセージを送信します</span><span class="sxs-lookup"><span data-stu-id="0eda8-137">*nx_dhcp_forcerenew*: this sends a FORCERENEW message to the Server</span></span>

  - <span data-ttu-id="0eda8-138">*nx_dhcp_send_request*: *nx_dhcp.h* に指定された DHCP メッセージの種類を引数に取ってサーバーにメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-138">*nx_dhcp_send_request*: This takes as an argument a DHCP message type, as specified in *nx_dhcp.h*, and sends the message to the Server.</span></span> <span data-ttu-id="0eda8-139">DHCP INFORM メッセージを送信することが主な用途です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-139">This is intended primarily for sending the DHCP INFORM message.</span></span>

<span data-ttu-id="0eda8-140">これらのサービスの詳しい情報は、このドキュメントの「*DHCP サービスの説明*」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0eda8-140">See “*Description of DHCP Services*” for more information about these services elsewhere in this document.</span></span>

## <a name="starting-and-stopping-the-dhcp-client"></a><span data-ttu-id="0eda8-141">DHCP クライアントを起動および停止する</span><span class="sxs-lookup"><span data-stu-id="0eda8-141">Starting and Stopping the DHCP Client</span></span>

<span data-ttu-id="0eda8-142">DHCP クライアントを停止するには、バインド状態になっているかどうかにかかわらず、ホスト アプリケーションで *nx_dhcp_stop* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-142">To stop the DHCP Client, regardless if it has achieved a bound state, the host application calls *nx_dhcp_stop*.</span></span>

<span data-ttu-id="0eda8-143">DHCP クライアントを再起動するには、最初に、ホスト アプリケーションで前述の *nx_dhcp_stop* サービスを使用して DHCP クライアントを停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-143">To restart a DHCP client, the host application must first stop the DHCP Client using the *nx_dhcp_stop* service described above.</span></span> <span data-ttu-id="0eda8-144">それから、ホストで *nx_dhcp_start* を呼び出して DHCP クライアントを再開できます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-144">Then the host can call *nx_dhcp_start* to resume the DHCP Client.</span></span> <span data-ttu-id="0eda8-145">古い DHCP クライアント プロファイル、たとえば他のネットワーク上にあった以前の DHCP サーバーから取得したプロファイルの削除がホスト アプリケーションから求められる場合、そのホスト アプリケーションで *nx_dhcp_reinitialize* を呼び出してこのタスクを内部的に実行し、その後で nx_dhcp_start を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-145">If the host application wishes to clear a previous DHCP Client profile, for example, one obtained from a previous DHCP Server on another network, the host application should call *nx_dhcp_reinitialize* to perform this task internally before calling nx_dhcp_start.</span></span>

<span data-ttu-id="0eda8-146">典型的なプロセス進行:</span><span class="sxs-lookup"><span data-stu-id="0eda8-146">A typical sequence might be:</span></span>

```C
nx_dhcp_stop(&my_dhcp);

nx_dhcp_reinitialize(&my_dhcp);

nx_dhcp_start(&my_dhcp);
```

<span data-ttu-id="0eda8-147">DHCP アプリケーションを単一の DHCP インターフェイスで実行している場合、DHCP クライアントを停止すると、DHCP クライアントのタイマーも無効になります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-147">For DHCP applications running on only a single DHCP interface, stopping the DHCP Client also inactivates the DHCP CLIENT timer.</span></span> <span data-ttu-id="0eda8-148">こうして IP リースの残り時間が監視されなくなります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-148">Thus it is no longer keeping track of the time remaining on the IP lease.</span></span> <span data-ttu-id="0eda8-149">特定のインターフェイスで DHCP クライアントを停止すると、DHCP クライアントのタイマーは無効になりませんが、そのインターフェイスで IP リースの残りの時間のタイマーが停止します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-149">Stopping DHCP Client on a particular interface will not inactivate the DHCP Client timer but will stop timer updates to the time remaining on the IP lease on that interface.</span></span>

<span data-ttu-id="0eda8-150">そのため、ホスト アプリケーションでネットワークの再起動または切り替えが必要な場合を除き、DHCP クライアントを停止することは推奨しません。</span><span class="sxs-lookup"><span data-stu-id="0eda8-150">Therefore, stopping the DHCP Client is not advised unless the host application requires rebooting or switching networks.</span></span>

## <a name="using-the-dhcp-client-with-auto-ip"></a><span data-ttu-id="0eda8-151">Auto IP と共に DHCP クライアントを使用する</span><span class="sxs-lookup"><span data-stu-id="0eda8-151">Using the DHCP Client with Auto IP</span></span>

<span data-ttu-id="0eda8-152">DHCP サーバーが使用可能であること、応答していることが保証されない場合に DHCP と Auto IP によってアドレスの割り当てを保証するアプリケーションでは、NetX DHCP Client を Auto IP プロトコルと共に使用します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-152">The NetX DHCP Client works concurrently with the Auto IP protocol in applications where DHCP and Auto IP guarantee an address where a DHCP Server is not guaranteed to be available or responding.</span></span> <span data-ttu-id="0eda8-153">ただし、ホストがサーバーを検出できず IP アドレスの割り当てを受けることもできない場合は、ローカル IP アドレスの処理を Auto IP プロトコルに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-153">However, If the host is unable to detect a Server or get an IP address assigned, it can switch to the Auto IP protocol for a local IP address.</span></span> <span data-ttu-id="0eda8-154">ただし、そうする前に DHCP クライアントを一時的に停止して、Auto IP が "調査" と "防御" の段階を過ぎるのを待つことを推奨します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-154">However before doing so, it is advisable to stop the DHCP Client temporarily while Auto IP goes through the “probe” and “defense” stages.</span></span> <span data-ttu-id="0eda8-155">自動 IP アドレスがホストに割り当てられたら DHCP クライアントを再起動できます。また、DHCP サーバーが実際に使用できるようになったら、アプリケーション実行中に DHCP サーバーによって提供される IP アドレスを、ホストの IP アドレスとして受け入れることができます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-155">Once an Auto IP address is assigned to the host, the DHCP Client can be restarted and if a DHCP Server does become available, the host IP address can accept the IP address offered by the DHCP Server while the application is running.</span></span>

<span data-ttu-id="0eda8-156">NetX Auto IP には、IP アドレスが変更された場合にホストがそのアドレスの振る舞いを監視するための、アドレス変更通知機能があります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-156">The NetX Auto IP has an address change notification for the host to monitor its activities in the event of an IP address change.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="0eda8-157">システムの簡単な例</span><span class="sxs-lookup"><span data-stu-id="0eda8-157">Small Example System</span></span>

<span data-ttu-id="0eda8-158">NetX の使用例を次の図 1.1 で説明します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-158">An example of how use NetX is described in Figure 1.1 below.</span></span> <span data-ttu-id="0eda8-159">101 行目で *my_thread_entry* により DHCP クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-159">The DHCP Client is created “*my_thread_entry*” at line 101.</span></span> <span data-ttu-id="0eda8-160">作成が完了してから、108 行目で *nx_dhcp_start* を呼び出して DHCP 処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-160">After successful creation, the DHCP process is initiated at the call to *nx_dhcp_start* at line 108.</span></span> <span data-ttu-id="0eda8-161">この時点で DHCP クライアントによって DHCP サーバーへの接続処理が開始されます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-161">At this point the DHCP Client attempts are initiated to contact the DHCP server.</span></span> <span data-ttu-id="0eda8-162">この処理中、アプリケーションのコードは、95 行目から *nx_ip_status_check* サービス (セカンダリ インターフェイスの場合は *nx_ip_interface_status_check*) を使用して、有効な IP アドレスが IP インスタンスに登録されるのを待機します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-162">During this process, the application code waits for a valid IP address to be registered with the IP instance using the *nx_ip_status_check* service (or *nx_ip_interface_status_check* for a secondary interface) starting at line 95.</span></span> <span data-ttu-id="0eda8-163">待機時間を短縮する手段のあるループ処理でこれを行うことが多いです。</span><span class="sxs-lookup"><span data-stu-id="0eda8-163">This is more commonly done in a loop with a shorter wait option.</span></span>

<span data-ttu-id="0eda8-164">127 行目を過ぎた時点で DHCP は有効な IP アドレスを受け取っており、アプリケーションは、必要に応じて NetX の TCP/IP サービスを使用しながら、処理を進めることができます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-164">After line 127, DHCP has received a valid IP address and the application can then proceed, utilizing NetX TCP/IP services as desired.</span></span>

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
      0xFFFFFF00, &my_pool, my_netx_driver, pointer, 
      DEMO_STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


/* Define my thread. */

void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    actual_status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip, NX_IP_LINK_ENABLED, 
                            &actual_status, 100);

  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

<span data-ttu-id="0eda8-165">図 1.1 NetX での DHCP の使用例</span><span class="sxs-lookup"><span data-stu-id="0eda8-165">Figure 1.1 Example of DHCP use with NetX</span></span>

## <a name="multi-server-environments"></a><span data-ttu-id="0eda8-166">マルチサーバー環境</span><span class="sxs-lookup"><span data-stu-id="0eda8-166">Multi-Server Environments</span></span>

<span data-ttu-id="0eda8-167">複数の DHCP サーバーが存在するネットワークでは、DHCP クライアントは最初に受信した DHCP サーバーのオファー メッセージを受け入れて Request 状態に進み、受信した他のオファーをすべて無視します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-167">On networks where there is more than one DHCP Server, the DHCP Client accepts the first received DHCP Server Offer message, advances to the Request state, and ignores any other received offers.</span></span>

## <a name="arp-probes"></a><span data-ttu-id="0eda8-168">ARP プローブ</span><span class="sxs-lookup"><span data-stu-id="0eda8-168">ARP Probes</span></span>

<span data-ttu-id="0eda8-169">DHCP クライアントを構成することで、DHCP サーバーによる IP アドレスの割り当てが済んだ後で、1 つまたは複数の ARP プローブを送信して、その IP アドレスがまだ使用されていないことを確認するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-169">The DHCP Client can be configured to send one or more ARP probes after IP address assignment from the DHCP Server to verify the IP address is not already in use.</span></span> <span data-ttu-id="0eda8-170">RFC 2131 では ARP プローブの使用が推奨されています。これは特に複数の DHCP サーバーが存在する環境で重要です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-170">The ARP probe step is recommended by RFC 2131 and is particularly important in environments with more than one DHCP Server.</span></span> <span data-ttu-id="0eda8-171">ホスト アプリケーションで NX_DHCP_CLIENT_SEND_ARP_PROBE オプションを有効にすると (他の ARP プローブ オプションは、第 2 章の「**構成オプション**」をご覧ください)、DHCP クライアントは "自分宛ての" ARP プローブを送信し、指定された時間応答を待機します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-171">If the host application enables the NX_DHCP_CLIENT_SEND_ARP_PROBE option (see **Configuration Options** in Chapter Two for additional ARP probe options), the DHCP Client will send a ‘self addressed’ ARP probe and wait for the specified time for a response.</span></span> <span data-ttu-id="0eda8-172">何も受信できない場合、DHCP クライアントは Bound 状態に進みます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-172">If none is received, the DHCP Client advances to the Bound state.</span></span> <span data-ttu-id="0eda8-173">応答を受信した場合、DHCP クライアントは、アドレスが既に使用されているものとみなします。</span><span class="sxs-lookup"><span data-stu-id="0eda8-173">If a response is received, the DHCP Client assumes the address is already in use.</span></span> <span data-ttu-id="0eda8-174">すると自動的に DECLINE メッセージがサーバーに送信され、クライアントを再初期化して、INIT 状態から DHCP プローブを再開します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-174">It automatically sends a DECLINE message to the Server, and reinitializes the Client to restart the DHCP probes again from the INIT state.</span></span> <span data-ttu-id="0eda8-175">これにより DHCP ステート マシンが再起動し、クライアントは DISCOVER メッセージをもう 1 度サーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-175">This restarts the DHCP state machine and the Client sends another DISCOVER message to the Server.</span></span>

## <a name="bootp-protocol"></a><span data-ttu-id="0eda8-176">BOOTP プロトコル</span><span class="sxs-lookup"><span data-stu-id="0eda8-176">BOOTP Protocol</span></span>

<span data-ttu-id="0eda8-177">DHCP クライアントは、DHCP プロトコルと共に BOOTP プロトコルもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0eda8-177">The DHCP Client also supports the BOOTP protocol as well the DHCP protocol.</span></span> <span data-ttu-id="0eda8-178">このオプションを有効にして DHCP の代わりに BOOTP を使用するには、ホスト アプリケーションで NX_DHCP_BOOTP_ENABLE 構成オプションを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-178">To enable this option and use BOOTP instead of DHCP, the host application must set the NX_DHCP_BOOTP_ENABLE configuration option.</span></span> <span data-ttu-id="0eda8-179">ホスト アプリケーションは、BOOTP プロトコルでも特定の IP アドレスを要求できます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-179">The host application can still request specific IP addresses in the BOOTP protocol.</span></span> <span data-ttu-id="0eda8-180">なお、BOOTP はホスト オペレーティング システムの読み込みに使用する場合もありますが、DHCP クライアントはこれをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="0eda8-180">However, the DHCP Client does not support loading the host operating system as BOOTP is sometimes used to do.</span></span>

## <a name="dhcp-on-a-secondary-interface"></a><span data-ttu-id="0eda8-181">セカンダリ インターフェイスでの DHCP</span><span class="sxs-lookup"><span data-stu-id="0eda8-181">DHCP on a Secondary Interface</span></span>

<span data-ttu-id="0eda8-182">NetX DHCP Client は、既定のプライマリ インターフェイスの代わりにセカンダリ インターフェイスでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-182">The NetX DHCP Client can run on secondary interfaces rather than the default primary interface.</span></span>

<span data-ttu-id="0eda8-183">セカンダリ ネットワーク インターフェイスで NetX DHCP Client を実行するには、ホスト アプリケーションで *nx_dhcp_set_interface_index* API サービスを使用して、DHCP クライアントのインターフェイス インデックスをセカンダリ インターフェイスに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-183">To run NetX DHCP Client on a secondary network interface, the host application must set the interface index of the DHCP Client to the secondary interface using the *nx_dhcp_set_interface_index* API service.</span></span> <span data-ttu-id="0eda8-184">インターフェイスは、*nx_ip_interface_attach* サービスを使用して、プライマリ ネットワーク インターフェイスに前もってアタッチしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-184">The interface must already be attached to the primary network interface using the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="0eda8-185">セカンダリ インターフェイスのアタッチの詳細は「NetX ユーザー ガイド」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0eda8-185">See the NetX User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="0eda8-186">下の図 1.2 は、ホスト アプリケーションをセカンダリ インターフェイス上の DHCP サーバーに接続するシステムの例です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-186">Below in Figure 1.2 is an example system on which the host application connects to the DHCP server on its secondary interface.</span></span> <span data-ttu-id="0eda8-187">65 行目で、NULL IP アドレスを使用してセカンダリ インターフェイスを IP タスクにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="0eda8-187">On line 65, the secondary interface is attached to the IP task with a null IP address.</span></span> <span data-ttu-id="0eda8-188">104 行目で、DHCP クライアント インスタンスを作成してから、*nx_dhcp_set_interface_index* を呼び出して、DHCP クライアントのインターフェイス インデックスを 1 に設定します (自身のインデックスが 0 であるプライマリ インターフェイスとの差に相当)。</span><span class="sxs-lookup"><span data-stu-id="0eda8-188">On line 104, after the DHCP Client instance is created, the DHCP Client interface index is set to 1 (e.g. the offset from the primary interface which itself is index 0) by calling *nx_dhcp_set_interface_index*.</span></span> <span data-ttu-id="0eda8-189">その後 108 行目で DHCP クライアントが起動できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-189">Then the DHCP Client is ready to be started in line 108.</span></span>

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
       0xFFFFFF00, &my_pool, my_netx_driver, pointer, STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  status = _nx_ip_interface_attach(&ip_0, "port_2", IP_ADDRESS(0, 0, 0,0), 
                            0xFFFFFF00UL, my_netx_driver);
                            
  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,& status,100);
  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Set the DHCP client interface to the secondary interface. 
    status = nx_dhcp_set_interface_index(&my_dhcp, 1);


  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

<span data-ttu-id="0eda8-190">図 1.2 マルチホーム構成をサポートする NetX の DHCP の例</span><span class="sxs-lookup"><span data-stu-id="0eda8-190">Figure 1.2 Example of DHCP for NetX with multihome support</span></span>

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a><span data-ttu-id="0eda8-191">複数のインターフェイスでの DHCP クライアント同時実行</span><span class="sxs-lookup"><span data-stu-id="0eda8-191">DHCP Client on Multiple Interfaces Simultaneously</span></span>

<span data-ttu-id="0eda8-192">DHCP クライアントを複数のインターフェイスで実行するには、*nx_api.h* の NX_MAX_PHYSICAL_INTERFACES を、デバイスに接続している物理インターフェイスの数に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-192">To run DHCP Client on multiple interfaces, NX_MAX_PHYSICAL_INTERFACES in *nx_api.h* must be set to the number of physical interfaces connected to the device.</span></span> <span data-ttu-id="0eda8-193">既定値は 1 です (プライマリ インターフェイスを表しています)。</span><span class="sxs-lookup"><span data-stu-id="0eda8-193">By default, this value is 1 (e.g. the primary interface).</span></span> <span data-ttu-id="0eda8-194">追加のインターフェイスを IP インスタンスに登録するには *nx_ip_interface_attach* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-194">To register an additional interface to the IP instance use the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="0eda8-195">セカンダリ インターフェイスのアタッチの詳細は「NetX ユーザー ガイド」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0eda8-195">See the NetX User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="0eda8-196">次のステップでは、*nx_dhcp.h* の NX_DHCP_CLIENT_MAX_RECORDS を、DHCP を同時に実行する予定のインターフェイスの最大数に設定します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-196">The next step is to set the NX_DHCP_CLIENT_MAX_RECORDS in *nx_dhcp.h* to the maximum number of interfaces expected to run DHCP simultaneously.</span></span> <span data-ttu-id="0eda8-197">NX_DHCP_CLIENT_MAX_RECORDS を NX_MAX_PHYSICAL_INTERFACES と一致させる必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0eda8-197">Note that NX_DHCP_CLIENT_MAX_RECORDS does not have to equal NX_MAX_PHYSICAL_INTERFACES.</span></span> <span data-ttu-id="0eda8-198">たとえば、NX_MAX_PHYSICAL_INTERFACES を 3、NX_DHCP_CLIENT_MAX_RECORDS を 2 に設定できます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-198">For example, NX_MAX_PHYSICAL_INTERFACES can be 3 and NX_DHCP_CLIENT_MAX_RECORDS equal to 2.</span></span> <span data-ttu-id="0eda8-199">この構成だと、DHCP を同時に使用できるのが、3 つの物理インターフェイスのうち 2 つだけということになります (2 つのインターフェイスの組み合わせは、あらゆる時点でどの組み合わせにもなり得ます)。</span><span class="sxs-lookup"><span data-stu-id="0eda8-199">In this configuration, only two interfaces (and they can be any two of the three physical interfaces at any time) of the three physical interfaces can run DHCP at any one time.</span></span> <span data-ttu-id="0eda8-200">DHCP クライアント レコードは、ネットワーク インターフェイスに対し 1 対 1 でマッピングされません。たとえば、クライアント レコード 1 と物理インターフェイス インデックス 1 が自動的に関連付けられることはありません。</span><span class="sxs-lookup"><span data-stu-id="0eda8-200">DHCP Client Records do not have a one to one mapping to network interfaces e.g. Client Record 1 does not automatically correlate to physical interface index 1.</span></span>

<span data-ttu-id="0eda8-201">NX_DHCP_CLIENT_MAX_RECORDS を NX_MAX_PHYSICAL_INTERFACES より大きく設定することもできますが、これは使用しないクライアント レコードを作成することになり、メモリの使用効率が悪くなります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-201">NX_DHCP_CLIENT_MAX_RECORDS can also be set to greater than NX_MAX_PHYSICAL_INTERFACES but this would create unused client records and be an inefficient use of memory.</span></span>

<span data-ttu-id="0eda8-202">どのインターフェイスで DHCP を起動する場合も、前もってアプリケーションで *nx_dhcp_interface_enable* を呼び出し、それらのインターフェイスを有効にしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-202">Before it can start DHCP on any interface, the application must enable those interfaces by calling *nx_dhcp_interface_enable*.</span></span> <span data-ttu-id="0eda8-203">*nx_dhcp_create* の呼び出しで自動的に有効になるプライマリ インターフェイスはこの例外です (後述の *nx_dhcp_interface_disable* サービスを使用すれば無効にできます)。</span><span class="sxs-lookup"><span data-stu-id="0eda8-203">Note that the exception is the primary interface which is automatically enabled in the *nx_dhcp_create* call (and which can be disabled using the *nx_dhcp_interface_disable* service discussed below).</span></span>

<span data-ttu-id="0eda8-204">DHCP を実行している他のインターフェイスとは無関係に、各インターフェイスではいつでも DHCP を無効にすることで、実行中の DHCP を停止することができます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-204">At any time, an interface can be disabled for DHCP or DHCP can be stopped on that interface independently of other interfaces running DHCP.</span></span>

<span data-ttu-id="0eda8-205">前述のとおり特定のインターフェイスで DHCP を有効にするには、*nx_dhcp_interface_enable* サービスを使用し、入力の引数で物理インターフェイスのインデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-205">As mentioned above, to enable a specific interface for DHCP, use the *nx_dhcp_interface_enable* service and specify the physical interface index in the input argument.</span></span> <span data-ttu-id="0eda8-206">インターフェイスは NX_DHCP_CLIENT_MAX_RECORDS で指定された数まで有効にできますが、唯一の制約として、入力の引数で指定するインターフェイス インデックスは NX_MAX_PHYSICAL_INTERFACES 未満でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="0eda8-206">Up to NX_DHCP_CLIENT_MAX_RECORDS interfaces can be enabled with the only limitation that the interface index input argument be less than NX_MAX_PHYSICAL_INTERFACES.</span></span>

<span data-ttu-id="0eda8-207">特定のインターフェイスで DHCP を起動するには *nx_dhcp_interface_start* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-207">To start DHCP on a specific interface, use the *nx_dhcp_interface_start* service.</span></span> <span data-ttu-id="0eda8-208">有効になっているすべてのインターフェイスで DHCP を起動するには *nx_dhcp_start* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-208">To start DHCP on all enabled interfaces, use the *nx_dhcp_start* service.</span></span> <span data-ttu-id="0eda8-209">(既に DHCP を起動しているインターフェイスでは *nx_dhcp_start* の影響はありません。)</span><span class="sxs-lookup"><span data-stu-id="0eda8-209">(Interfaces that have already started DHCP will not be affected by *nx_dhcp_start*.)</span></span>

<span data-ttu-id="0eda8-210">インターフェイスで DHCP を停止するには、*nx_dhcp_interface_stop* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-210">To stop DHCP on an interface, use the *nx_dhcp_interface_stop* service.</span></span> <span data-ttu-id="0eda8-211">DHCP はそのインターフェイスで前もって起動しておく必要があります。起動できていないとエラー ステータスが返されます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-211">DHCP must already have started on that interface or an error status is returned.</span></span> <span data-ttu-id="0eda8-212">有効になっているすべてのインターフェイスで DHCP を停止するには *nx_dhcp_stop* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-212">To stop DHCP on all enabled interfaces, use the *nx_dhcp_stop* service.</span></span> <span data-ttu-id="0eda8-213">DHCP は、他のインターフェイスとは別個に、各インターフェイスでいつでも停止できます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-213">DHCP can be stopped independently of other interfaces at any time.</span></span>

<span data-ttu-id="0eda8-214">既存の DHCP クライアント サービスのほとんどには、"インターフェイス別" に実行するバージョンが存在します。たとえば *nx_dhcp_release* のサービスをインターフェイス別に提供するのが *nx_dhcp_interface_release* です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-214">Most of the existing DHCP Client services have an ‘interface’ equivalent e.g. *nx_dhcp_interface_release* is the interface specific equivalent of *nx_dhcp_release.*</span></span> <span data-ttu-id="0eda8-215">単一のインターフェイスで DHCP クライアントを構成する場合、これらのサービスに違いはありません。</span><span class="sxs-lookup"><span data-stu-id="0eda8-215">If DHCP Client is configured for a single interface, they perform the same action.</span></span>

<span data-ttu-id="0eda8-216">インターフェイス別ではない DHCP クライアント サービスは通常すべてのインターフェイスに適用されますが、そうでない場合もあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0eda8-216">Note that non-interface specific DHCP Client services typically apply to all interfaces but not all.</span></span> <span data-ttu-id="0eda8-217">後者の場合、インターフェイス別ではないサービスは、DHCP が有効になっているインターフェイスのうち、インターフェイス レコードの DHCP クライアント リストを検索して最初に見つかったものに適用されます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-217">In the latter case, the non-interface specific service applies to the first DHCP enabled interface found in searching the DHCP Client list of interface records.</span></span> <span data-ttu-id="0eda8-218">複数のインターフェイスで DHCP を有効にしたときに、インターフェイス別でないサービスがどのように機能するかは、第 3 章の「**サービスの説明**」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0eda8-218">See **Description of Services** in Chapter Three for how a non-interface specific service performs when multiple interfaces are enabled for DHCP.</span></span>

<span data-ttu-id="0eda8-219">下のプロセス進行例では、IP インスタンスに 2 つのネットワーク インターフェイスがあり、セカンダリ インターフェイスで先に DHCP を実行します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-219">In the example sequence below, the IP instance has two network interfaces and first runs DHCP on the secondary interface.</span></span> <span data-ttu-id="0eda8-220">しばらく後で、プライマリ インターフェイスでも DHCP が起動されます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-220">At some time later, it starts DHCP on the primary interface.</span></span> <span data-ttu-id="0eda8-221">それからプライマリ インターフェイスで IP アドレスを解放し、プライマリ インターフェイスで DHCP を再起動します:</span><span class="sxs-lookup"><span data-stu-id="0eda8-221">Then it releases the IP address on the primary interface and restarts DHCP on the primary interface:</span></span>

```C
nx_dhcp_create(&my_dhcp_client);
/* By default this enables primary interface for DHCP. */

nx_dhcp_interface_enable(&my_dhcp_client, 1); 
/* Secondary interface is enabled. */

nx_dhcp_interface_start(&my_dhcp_client, 1); 
/* DHCP is started on secondary interface. */

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is started on primary interface. */

nx_dhcp_interface_release(&my_dhcp_client, 0); 

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is restarted on primary interface. */
```

<span data-ttu-id="0eda8-222">インターフェイス別に実行するすべてのサービスのリストは、第 3 章の「**サービスの説明**」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0eda8-222">For a complete list of interface specific services see **Description of Services** in Chapter Three.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="0eda8-223">構成オプション</span><span class="sxs-lookup"><span data-stu-id="0eda8-223">Configuration Options</span></span>

<span data-ttu-id="0eda8-224">*nx_dhcp.h* にあるユーザーが構成可能な DHCP オプションを使用すると、ホスト アプリケーションで、DHCP クライアントの各要件に関するパラメーターを細かく調整できます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-224">User configurable DHCP options in *nx_dhcp.h* allow the host application to fine tune DHCP Client for its particular requirements.</span></span> <span data-ttu-id="0eda8-225">次のリストにそれらのパラメーターを挙げます:</span><span class="sxs-lookup"><span data-stu-id="0eda8-225">The following is a list of these parameters:</span></span>  
  
- <span data-ttu-id="0eda8-226">**NX_DHCP_ENABLE_BOOTP** このオプションを有効にすると、DHCP の代わりに BOOTP プロトコルが有効になります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-226">**NX_DHCP_ENABLE_BOOTP** Defined, this option enables the BOOTP protocol instead of DHCP.</span></span> <span data-ttu-id="0eda8-227">既定では、このオプションは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="0eda8-227">By default this option is disabled.</span></span>

- <span data-ttu-id="0eda8-228">**NX_DHCP_CLIENT_RESTORE_STATE** このオプションを有効にすると、DHCP クライアントで、リースの残り時間を含む現在の DHCP クランアントのライセンスの "状態"を保存し、DHCP クライアント アプリケーションの再起動間でこの状態を復元できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-228">**NX_DHCP_CLIENT_RESTORE_STATE** If defined, this enables the DHCP Client to save its current DHCP Client license ‘state’ including time remaining on the lease, and restore this state between DHCP Client application reboots.</span></span> <span data-ttu-id="0eda8-229">既定値は、無効です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-229">The default value is disabled.</span></span>

- <span data-ttu-id="0eda8-230">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL** このオプションを有効にすると、DHCP クライアントで専用のパケット プールを作成しなくなります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-230">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL** If set, the DHCP Client will not create its own packet pool.</span></span> <span data-ttu-id="0eda8-231">ホスト アプリケーションで nx_dhcp_packet_pool_set サービスを使用して DHCP クライアントのパケット プールを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-231">The host application must use the nx_dhcp_packet_pool_set service to set the DHCP Client packet pool.</span></span> <span data-ttu-id="0eda8-232">既定値は、無効です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-232">The default value is disabled.</span></span>

- <span data-ttu-id="0eda8-233">**NX_DHCP_CLIENT_SEND_ARP_PROBE** このオプションを有効にすると、IP アドレスを割り当てられた後で DHCP クライアントが ARP プローブを送信し、割り当てられた DHCP アドレスがまだ他のホストに所持されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-233">**NX_DHCP_CLIENT_SEND_ARP_PROBE** Defined, this enables the DHCP Client to send an ARP probe after IP address assignment to verify the assigned DHCP address is not owned by another host.</span></span> <span data-ttu-id="0eda8-234">既定では、このオプションは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="0eda8-234">By default, this option is disabled.</span></span>

- <span data-ttu-id="0eda8-235">**NX_DHCP_ARP_PROBE_WAIT** ARP プローブを送信してから DHCP クライアントが応答を待つ時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-235">**NX_DHCP_ARP_PROBE_WAIT** Defines the length of time the DHCP Client waits for a response after sending an ARP probe.</span></span> <span data-ttu-id="0eda8-236">既定値は 1 秒 (1 x NX_IP_PERIODIC_RATE) です</span><span class="sxs-lookup"><span data-stu-id="0eda8-236">The default value is one second (1 \* NX_IP_PERIODIC_RATE)</span></span>

- <span data-ttu-id="0eda8-237">**NX_DHCP_ARP_PROBE_MIN** ARP プローブを送信する間隔の最小値を指定します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-237">**NX_DHCP_ARP_PROBE_MIN** Defines the minimum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="0eda8-238">既定値は 1 秒です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-238">The value is defaulted to 1 second.</span></span>

- <span data-ttu-id="0eda8-239">**NX_DHCP_ARP_PROBE_MAX** ARP プローブを送信する間隔の最大値を指定します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-239">**NX_DHCP_ARP_PROBE_MAX** Defines the maximum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="0eda8-240">既定値は 2 秒です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-240">The value is defaulted to 2 seconds.</span></span>

- <span data-ttu-id="0eda8-241">**NX_DHCP_ARP_PROBE_NUM** DHCP サーバーによって割り当てられた IP アドレスが既に使用されているかどうかを判断するために ARP プローブを送信する回数を指定します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-241">**NX_DHCP_ARP_PROBE_NUM** Defines the number of ARP probes sent for determining if the IP address assigned by the DHCP server is already in use.</span></span> <span data-ttu-id="0eda8-242">プローブの既定値は 3 回です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-242">The value is defaulted to 3 probes.</span></span>

- <span data-ttu-id="0eda8-243">**NX_DHCP_RESTART_WAIT** DHCP クライアントに割り当てられた IP アドレスが既に使用されている場合に、DHCP クライアントが DHCP を再起動するのを待つ時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-243">**NX_DHCP_RESTART_WAIT** Defines the length of time the DHCP Client waits to restart DHCP if the IP address assigned to the DHCP Client is already in use.</span></span> <span data-ttu-id="0eda8-244">既定値は 10 秒です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-244">The value is defaulted to 10 seconds.</span></span>

- <span data-ttu-id="0eda8-245">**NX_DHCP_CLIENT_MAX_RECORDS** DHCP クライアント インスタンスに保存するインターフェイス レコードの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-245">**NX_DHCP_CLIENT_MAX_RECORDS** Specifies the maximum number of interface records to save to the DHCP Client instance.</span></span> <span data-ttu-id="0eda8-246">DHCP クライアント インターフェイス レコードは、特定のインターフェイスで実行している DHCP クライアントの記録です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-246">A DHCP Client interface record is a record of the DHCP Client running on a specific interface.</span></span> <span data-ttu-id="0eda8-247">既定値は、物理インターフェイス数 (NX_MAX_PHYSICAL_INTERFACES) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="0eda8-247">The default value is set as physical interfaces count(NX_MAX_PHYSICAL_INTERFACES).</span></span>

- <span data-ttu-id="0eda8-248">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION** このオプションを有効にすると、DHCP メッセージ サイズ オプションで指定する最大数まで、DHCP クライアントからメッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-248">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION** Defined, this enables the DHCP Client to send maximum DHCP message size option.</span></span> <span data-ttu-id="0eda8-249">既定では、このオプションは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="0eda8-249">By default, this option is disabled.</span></span>

- <span data-ttu-id="0eda8-250">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK** このオプションを有効にすると、nx_dhcp_create の呼び出しで入力したホスト名の文字と文字数が無効でないかどうかを、DHCP クライアントで確認します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-250">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK** Defined, this enables the DHCP Client to check the input host name in the nx_dhcp_create call for invalid characters or length.</span></span> <span data-ttu-id="0eda8-251">既定では、このオプションは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="0eda8-251">By default, this option is disabled.</span></span>

- <span data-ttu-id="0eda8-252">**NX_DHCP_THREAD_PRIORITY** DHCP スレッドの優先度です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-252">**NX_DHCP_THREAD_PRIORITY** Priority of the DHCP thread.</span></span> <span data-ttu-id="0eda8-253">既定値では、優先度 3 で DHCP スレッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-253">By default, this value specifies that the DHCP thread runs at priority 3.</span></span>

- <span data-ttu-id="0eda8-254">**NX_DHCP_THREAD_STACK_SIZE** DHCP スレッドのスタックのサイズです。</span><span class="sxs-lookup"><span data-stu-id="0eda8-254">**NX_DHCP_THREAD_STACK_SIZE** Size of the DHCP thread stack.</span></span> <span data-ttu-id="0eda8-255">既定のサイズは 2048 バイトです。</span><span class="sxs-lookup"><span data-stu-id="0eda8-255">By default, the size is 2048 bytes.</span></span>

- <span data-ttu-id="0eda8-256">**NX_DHCP_TIME_INTERVAL** DHCP クライアント タイマーの有効期限関数を実行する秒単位の間隔です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-256">**NX_DHCP_TIME_INTERVAL** Interval in seconds when the DHCP Client timer expiration function executes.</span></span> <span data-ttu-id="0eda8-257">この関数を使用すると、DHCP 処理に関与するすべてのタイムアウトの状態が更新されます。たとえば、メッセージの再転送をすべきかや、DHCP クライアントの状態変化などです。</span><span class="sxs-lookup"><span data-stu-id="0eda8-257">This function updates all the timeouts in the DHCP process e.g. if messages should be retransmitted or DHCP Client state changed.</span></span> <span data-ttu-id="0eda8-258">既定値は 1 秒です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-258">By default, this value is 1 second.</span></span>

- <span data-ttu-id="0eda8-259">**NX_DHCP_OPTIONS_BUFFER_SIZE** DHCP のオプションのバッファーのサイズです。</span><span class="sxs-lookup"><span data-stu-id="0eda8-259">**NX_DHCP_OPTIONS_BUFFER_SIZE** Size of DHCP options buffer.</span></span> <span data-ttu-id="0eda8-260">既定値は 312 です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-260">By default, this value is 312.</span></span>

- <span data-ttu-id="0eda8-261">**NX_DHCP_PACKET_PAYLOAD** DHCP クライアントのパケットのペイロードのサイズをバイト単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-261">**NX_DHCP_PACKET_PAYLOAD** Specifies the size in bytes of the DHCP Client packet payload.</span></span> <span data-ttu-id="0eda8-262">既定値は NX_DHCP_MINIMUM_IP_DATAGRAM + 物理ヘッダーのサイズです。</span><span class="sxs-lookup"><span data-stu-id="0eda8-262">The default value is NX_DHCP_MINIMUM_IP_DATAGRAM + physical header size.</span></span> <span data-ttu-id="0eda8-263">有線ネットワークでの物理ヘッダー サイズは、通常イーサネット フレームのサイズです。</span><span class="sxs-lookup"><span data-stu-id="0eda8-263">The physical header size in a wireline network is usually the Ethernet frame size.</span></span>

- <span data-ttu-id="0eda8-264">**NX_DHCP_PACKET_POOL_SIZE** DHCP クライアントのパケット プールのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-264">**NX_DHCP_PACKET_POOL_SIZE** Specifies the size of the DHCP Client packet pool.</span></span> <span data-ttu-id="0eda8-265">既定値は 5 x NX_DHCP_PACKET_PAYLOAD です。これは、パケット 4 個と、内部のパケット プールのオーバーヘッドを処理できるサイズです。</span><span class="sxs-lookup"><span data-stu-id="0eda8-265">The default value is (5 \*NX_DHCP_PACKET_PAYLOAD) which will provide four packets plus room for internal packet pool overhead.</span></span>

- <span data-ttu-id="0eda8-266">**NX_DHCP_MIN_RETRANS_TIMEOUT** クライアントのメッセージに対する DHCP サーバーの応答を待つ最小待機時間を指定します。待機時間を過ぎるとメッセージを再送信します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-266">**NX_DHCP_MIN_RETRANS_TIMEOUT** Specifies the minimum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="0eda8-267">既定値は RFC 2131 で推奨されている 4 秒です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-267">The default value is the RFC 2131 recommended 4 seconds.</span></span>

- <span data-ttu-id="0eda8-268">**NX_DHCP_MAX_RETRANS_TIMEOUT** クライアントのメッセージに対する DHCP サーバーの応答を待つ最大待機時間を指定します。待機時間を過ぎるとメッセージを再送信します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-268">**NX_DHCP_MAX_RETRANS_TIMEOUT** Specifies the maximum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="0eda8-269">既定値は RFC 2131 で推奨されている 64 秒です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-269">The default value is the RFC 2131 recommended 64 seconds.</span></span>

- <span data-ttu-id="0eda8-270">**NX_DHCP_MIN_RENEW_TIMEOUT** DHCP クライアントを IP アドレスにバインドした後、DHCP サーバーのメッセージを受信して更新要求を送信するのを待つ、最小待機時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-270">**NX_DHCP_MIN_RENEW_TIMEOUT** Specifies minimum wait option for receiving a DHCP Server message and sending a renewal request after the DHCP Client is bound to an IP address.</span></span> <span data-ttu-id="0eda8-271">既定値は 60 秒です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-271">The default value is 60 seconds.</span></span> <span data-ttu-id="0eda8-272">ただし、DHCP クライアントは、DHCP サーバーのメッセージで指定される Renew および Rebind の有効期限を最初に使用し、それから更新のタイムアウト時間の既定最小値に戻ります。</span><span class="sxs-lookup"><span data-stu-id="0eda8-272">However, the DHCP Client uses the Renew and Rebind expiration times from the DHCP server message before defaulting to the minimum renew timeout.</span></span>

- <span data-ttu-id="0eda8-273">**NX_DHCP_TYPE_OF_SERVICE** DHCP UDP 要求に必要なサービスの種類です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-273">**NX_DHCP_TYPE_OF_SERVICE** Type of service required for the DHCP UDP requests.</span></span> <span data-ttu-id="0eda8-274">既定値は、通常の IP パケット サービスを表す NX_IP_NORMAL です。</span><span class="sxs-lookup"><span data-stu-id="0eda8-274">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>

- <span data-ttu-id="0eda8-275">**NX_DHCP_FRAGMENT_OPTION** DHCP UDP 要求のフラグメント化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="0eda8-275">**NX_DHCP_FRAGMENT_OPTION** Fragment enable for DHCP UDP requests.</span></span> <span data-ttu-id="0eda8-276">既定値は NX_DONT_FRAGMENT であり DHCP UDP フラグメント化は無効になっています。</span><span class="sxs-lookup"><span data-stu-id="0eda8-276">By default, this value is NX_DONT_FRAGMENT to disable DHCP UDP fragmenting.</span></span>

- <span data-ttu-id="0eda8-277">**NX_DHCP_TIME_TO_LIVE** このパケットが通過できるルーターの数を指定します。この数を超えるとパケットは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="0eda8-277">**NX_DHCP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="0eda8-278">既定値は 0x80 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="0eda8-278">The default value is set to 0x80.</span></span>

- <span data-ttu-id="0eda8-279">**NX_DHCP_QUEUE_DEPTH** 受信キューの深さの最大値を指定します。</span><span class="sxs-lookup"><span data-stu-id="0eda8-279">**NX_DHCP_QUEUE_DEPTH** Specifies the number of maximum depth of receive queue.</span></span> <span data-ttu-id="0eda8-280">既定値は 4 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="0eda8-280">The default value is set to 4.</span></span>
