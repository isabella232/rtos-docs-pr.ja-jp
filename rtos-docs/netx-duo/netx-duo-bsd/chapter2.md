---
title: 第 2 章 - Azure RTOS NetX Duo BSD のインストールと使用
description: この章には、Azure RTOS NetX Duo BSD コンポーネントのインストール、設定、使用に関連するさまざまな問題の説明が含まれています。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 582661bc66c51341fc098de9ff7b6fa2a7d746de
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810970"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-bsd"></a><span data-ttu-id="905a5-103">第 2 章 - Azure RTOS NetX Duo BSD のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="905a5-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo BSD</span></span>

<span data-ttu-id="905a5-104">この章には、Azure RTOS NetX Duo BSD コンポーネントのインストール、設定、使用に関連するさまざまな問題の説明が含まれています。</span><span class="sxs-lookup"><span data-stu-id="905a5-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo BSD component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="905a5-105">製品の配布</span><span class="sxs-lookup"><span data-stu-id="905a5-105">Product Distribution</span></span>

<span data-ttu-id="905a5-106">Azure RTOS NetX Duo BSD は、[https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) のパブリック ソース コード リポジトリから入手できます。</span><span class="sxs-lookup"><span data-stu-id="905a5-106">Azure RTOS NetX Duo BSD can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="905a5-107">このパッケージには、次のように 2 つのソース ファイルと、このドキュメントを含む PDF ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="905a5-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="905a5-108">**nxd_bsd.h**: NetX Duo BSD のヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="905a5-108">**nxd_bsd.h**: Header file for NetX Duo BSD</span></span>
- <span data-ttu-id="905a5-109">**nxd_bsd.c**: NetX Duo BSD の C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="905a5-109">**nxd_bsd.c**: C Source file for NetX Duo BSD</span></span>
- <span data-ttu-id="905a5-110">**nxd_bsd.pdf**: NetX Duo BSD のユーザー ガイド</span><span class="sxs-lookup"><span data-stu-id="905a5-110">**nxd_bsd.pdf**: User Guide for NetX Duo BSD</span></span>

<span data-ttu-id="905a5-111">デモ ファイル:</span><span class="sxs-lookup"><span data-stu-id="905a5-111">Demo files:</span></span>

- <span data-ttu-id="905a5-112">**bsd_demo_udp.c**</span><span class="sxs-lookup"><span data-stu-id="905a5-112">**bsd_demo_udp.c**</span></span>
- <span data-ttu-id="905a5-113">**bsd_demo_tcp.c**</span><span class="sxs-lookup"><span data-stu-id="905a5-113">**bsd_demo_tcp.c**</span></span>
- <span data-ttu-id="905a5-114">**bsd_demo_raw.c**</span><span class="sxs-lookup"><span data-stu-id="905a5-114">**bsd_demo_raw.c**</span></span>

## <a name="netx-duo-bsd-installation"></a><span data-ttu-id="905a5-115">NetX Duo BSD のインストール</span><span class="sxs-lookup"><span data-stu-id="905a5-115">NetX Duo BSD Installation</span></span>

<span data-ttu-id="905a5-116">NetX Duo BSD を使用するためには、前述のディストリビューション全体を、NetX Duo がインストールされているのと同じディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-116">In order to use NetX Duo BSD the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="905a5-117">たとえば、NetX Duo がディレクトリ " *\threadx\arm7\green*" にインストールされている場合は、このディレクトリに *nxd_bsd.h* および *nxd_bsd.c* ファイルをコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-117">For example, if NetX Duo is installed in the directory "*\threadx\arm7\green*" then the *nxd_bsd.h* and *nxd_bsd.c* files should be copied into this directory.</span></span>

## <a name="building-the-threadx-and-netx-duo-components-of-a-bsd-application"></a><span data-ttu-id="905a5-118">BSD アプリケーションの ThreadX および NetX Duo コンポーネントのビルド</span><span class="sxs-lookup"><span data-stu-id="905a5-118">Building the ThreadX and NetX Duo components of a BSD Application</span></span>

### <a name="threadx"></a><span data-ttu-id="905a5-119">ThreadX</span><span class="sxs-lookup"><span data-stu-id="905a5-119">ThreadX</span></span>

<span data-ttu-id="905a5-120">ThreadX ライブラリでは、スレッド ローカル ストレージ内に `bsd_errno` を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-120">The ThreadX library must define `bsd_errno` in the thread local storage.</span></span> <span data-ttu-id="905a5-121">次の手順をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="905a5-121">We recommend the following procedure:</span></span>

1. <span data-ttu-id="905a5-122">*tx_port.h* で、次のようにいずれかの TX_THREAD_EXTENSION マクロを設定します。</span><span class="sxs-lookup"><span data-stu-id="905a5-122">In *tx_port.h*, set one of the TX_THREAD_EXTENSION macros as follows:</span></span>
   - `#define TX_THREAD_EXTENSION_3     int bsd_errno`

1. <span data-ttu-id="905a5-123">ThreadX ライブラリをリビルドします。</span><span class="sxs-lookup"><span data-stu-id="905a5-123">Rebuild the ThreadX library.</span></span>

> [!NOTE]
> <span data-ttu-id="905a5-124">TX_THREAD_EXTENSION_3 が既に使用されている場合、ユーザーは、他の TX_THREAD_EXTENSION マクロのいずれかを自由に使用できます。</span><span class="sxs-lookup"><span data-stu-id="905a5-124">If TX_THREAD_EXTENSION_3 is already used, the user is free to use one of the other TX_THREAD_EXTENSION macros.</span></span>

### <a name="netx-duo"></a><span data-ttu-id="905a5-125">NetX Duo</span><span class="sxs-lookup"><span data-stu-id="905a5-125">NetX Duo</span></span>

<span data-ttu-id="905a5-126">NetX Duo BSD サービスを使用する前に、NX_ENABLE_EXTENDED_NOTIFY_SUPPORT を定義して NetX Duo ライブラリをビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-126">Before using NetX Duo BSD Services, the NetX Duo library must be built with NX_ENABLE_EXTENDED_NOTIFY_SUPPORT defined.</span></span> <span data-ttu-id="905a5-127">これは、既定では定義されていません。</span><span class="sxs-lookup"><span data-stu-id="905a5-127">By default it is not defined.</span></span> <span data-ttu-id="905a5-128">BSD RAW ソケットを使用する場合は、NX_ENABLE_IP_RAW_PACKET_FILTER を定義して NetX Duo ライブラリをビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-128">If the BSD raw sockets are to be used, the NetX Duo library must be built with NX_ENABLE_IP_RAW_PACKET_FILTER defined.</span></span>

## <a name="using-netx-duo-bsd"></a><span data-ttu-id="905a5-129">NetX Duo BSD の使用</span><span class="sxs-lookup"><span data-stu-id="905a5-129">Using NetX Duo BSD</span></span>

<span data-ttu-id="905a5-130">NetX Duo BSD アプリケーション プロジェクトでは、このガイドの後半で詳述されている BSD サービスを使用できるように、*tx_api.h* と *nx_api.h* のインクルード後に *nxd_bsd.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-130">A NetX Duo BSD application project must include *nxd_bsd.h* after it includes *tx_api.h* and *nx_api.h* to be able to use BSD services specified later in this guide.</span></span> <span data-ttu-id="905a5-131">アプリケーションのビルド プロセスでは、*nx_bsd.c* もインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-131">The application must also include *nxd_bsd.c* in the build process.</span></span> <span data-ttu-id="905a5-132">このファイルは、他のアプリケーション ファイルと同様にコンパイルする必要があり、そのオブジェクト形式は、アプリケーションのファイルと一緒にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-132">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="905a5-133">NetX Duo BSD を使用するために必要なものは、これですべてです。</span><span class="sxs-lookup"><span data-stu-id="905a5-133">This is all that is required to use NetX Duo BSD.</span></span>

<span data-ttu-id="905a5-134">NetX Duo BSD サービスを利用するには、アプリケーションでの IP インスタンスの作成、パケットを割り当てるための BSD レイヤー用のパケット プールの作成、内部 BSD スレッド スタックのためのメモリ領域の割り当て、内部 BSD スレッドの優先順位の指定を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-134">To utilize NetX Duo BSD services, the application must create an IP instance, create a packet pool for the BSD layer to allocate packets from, allocate memory space for the internal BSD thread stack, and specify the priority of the internal BSD thread.</span></span> <span data-ttu-id="905a5-135">BSD レイヤーは、*bsd_initialize* を呼び出してパラメーターを渡すことによって初期化されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-135">The BSD layer is initialized by calling *bsd_initialize* and passing in the parameters.</span></span> <span data-ttu-id="905a5-136">これについては、このドキュメントの後の方にある "小規模な例" で説明しますが、プロトタイプを下に示します。</span><span class="sxs-lookup"><span data-stu-id="905a5-136">This is demonstrated in the "Small Examples" later in this document but the prototype is shown below:</span></span>

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                    *CHAR *bsd_thread_stack_area,
                    *ULONG bsd_thread_stack_size,
                    *UINT bsd_thread_priority*);
```

<span data-ttu-id="905a5-137">default_ip は、BSD レイヤーの動作場所の IP インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="905a5-137">The default_ip is the IP instance the BSD layer operates on.</span></span> <span data-ttu-id="905a5-138">default_pool は、パケットを割り当てるために、BSD サービスによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-138">The default_pool is used by the BSD services to allocate packets from.</span></span> <span data-ttu-id="905a5-139">2 つのパラメーター bsd_thread_stack_area と bsd_thread_stack_size では内部 BSD スレッドによって使用されるスタック領域を定義し、最後のパラメーター bsd_thread_priority ではスレッドの優先順位を設定します。</span><span class="sxs-lookup"><span data-stu-id="905a5-139">The next two parameters: bsd_thread_stack_area, bsd_thread_stack_size defines the stack area used by the internal BSD thread, and the last parameter, bsd_thread_priority, sets the priority of the thread.</span></span>

## <a name="netx-duo-bsd-raw-socket-support"></a><span data-ttu-id="905a5-140">NetX Duo BSD RAW ソケットのサポート</span><span class="sxs-lookup"><span data-stu-id="905a5-140">NetX Duo BSD Raw Socket Support</span></span>

<span data-ttu-id="905a5-141">NetX Duo BSD では、RAW ソケットもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="905a5-141">NetX Duo BSD also supports raw sockets.</span></span> <span data-ttu-id="905a5-142">NetX Duo BSD で RAW ソケットを使用するには、NX_ENABLE_IP_RAW_PACKET_FILTER を定義して NetX Duo ライブラリをコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-142">To use raw sockets in NetX Duo BSD, the NetX Duo library must be compiled with NX_ENABLE_IP_RAW_PACKET_FILTER defined.</span></span> <span data-ttu-id="905a5-143">これは、既定では定義されていません。</span><span class="sxs-lookup"><span data-stu-id="905a5-143">By default it is not defined.</span></span> <span data-ttu-id="905a5-144">次に、アプリケーションで *nx_ip_raw_packet_enable* を呼び出すことによって、以前に作成した IP インスタンスで RAW ソケットの処理を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-144">The application must then enable raw socket processing for a previously created IP instance by calling *nx_ip_raw_packet_enable.*</span></span>

<span data-ttu-id="905a5-145">NetX Duo BSD で RAW ソケットを作成するには、アプリケーションで、ソケット作成サービスの *socket* を使用して、プロトコル ファミリ、ソケットの種類、プロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="905a5-145">To create a raw socket in NetX Duo BSD, the application uses the socket create service *socket* and specifies the protocol family, socket type and protocol:</span></span>

```c
sock_1 = socket(INT protocolFamily, INT socket_type, INT protocol)
```

<span data-ttu-id="905a5-146">protocolFamily は、IPv4 ソケットの場合は AF_INET です。または、IP インスタンスで IPv6 が有効になっていると仮定すれば、IPv6 ソケットの場合は AF_INET6 となります。</span><span class="sxs-lookup"><span data-stu-id="905a5-146">protocolFamily is AF_INET for IPv4 sockets, or AF_INET6 for IPv6 sockets, assuming IPv6 is enabled on the IP instance.</span></span> <span data-ttu-id="905a5-147">socket_type は SOCK_RAW に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-147">The socket_type must be set to SOCK_RAW.</span></span> <span data-ttu-id="905a5-148">protocol はアプリケーション固有です。</span><span class="sxs-lookup"><span data-stu-id="905a5-148">protocol is application specific.</span></span>

<span data-ttu-id="905a5-149">アプリケーションでは、RAW パケットを送受信したり、RAW ソケットを閉じたりするために、通常は UDP の場合と同じ *sendto、recvfrom、select*、*soc_close* などの BSD サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="905a5-149">To send and receive raw packets as well as close a raw socket, the application typically uses the same BSD services as for UDP e.g. *sendto, recvfrom, select* and *soc_close*.</span></span> <span data-ttu-id="905a5-150">RAW ソケットでは、BSD サービスの *accept* や *listen* はどちらもサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="905a5-150">Raw sockets do not support either *accept* or *listen* BSD services.</span></span>

- <span data-ttu-id="905a5-151">既定では、受信した IPv4 生データには IPv4 ヘッダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="905a5-151">By default, received IPv4 raw data includes the IPv4 header.</span></span>  <span data-ttu-id="905a5-152">逆に、受信した IPv6 生データには IPv6 ヘッダーが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="905a5-152">Conversely, received IPv6 raw data does not include the IPv6 header.</span></span>

- <span data-ttu-id="905a5-153">既定では、IPv6 または IPv4 のいずれかの RAW パケットを送信するときには、BSD ラッパー レイヤーによって、データの送信前に IPv6 または IPv4 ヘッダーが追加されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-153">By default, when sending either raw IPv6 or IPv4 packets, the BSD wrapper layer adds the IPv6 or IPv4 header before sending the data.</span></span>

<span data-ttu-id="905a5-154">NetX Duo BSD では、IP_RAW_RX_NO_HEADER、IP_HDRINCL、IP_RAW_IPV6_HDRINCL などの追加の RAW ソケット オプションがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="905a5-154">NetX Duo BSD supports additional raw socket options, including IP_RAW_RX_NO_HEADER, IP_HDRINCL and IP_RAW_IPV6_HDRINCL.</span></span>

<span data-ttu-id="905a5-155">IP_RAW_RX_NO_HEADER が設定されている場合は、受信したデータに IPv4 ヘッダーが含まれないように IPv4 ヘッダーが削除され、報告されるメッセージ長には IPv4 ヘッダーは含まれません。</span><span class="sxs-lookup"><span data-stu-id="905a5-155">If IP_RAW_RX_NO_HEADER is set, the IPv4 header is removed so that the received data does not contain the IPv4 header, and the reported message length does not include the IPv4 header.</span></span>  <span data-ttu-id="905a5-156">IPv6 ソケットの場合、既定では RAW ソケットの受信に IPv6 ヘッダーは含まれません。これは、IP_RAW_RX_NO_HEADER オプションを設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="905a5-156">For IPv6 sockets, by default the raw socket receive does not include IPv6 header, equivalent to having the IP_RAW_RX_NO_HEADER option set.</span></span> <span data-ttu-id="905a5-157">アプリケーションでは、*setsockopt* サービスを使用して IP_RAW_RX_NO_HEADER オプションを解除できます。IP_RAW_RX_NO_HEADER オプションが解除されると、受信した IPv6 生データには IPv6 ヘッダーが含まれるようになり、報告されるメッセージ長には IPv6 ヘッダーが含められます。</span><span class="sxs-lookup"><span data-stu-id="905a5-157">Application may use the *setsockopt* service to clear the IP_RAW_RX_NO_HEADER option, Once the IP_RAW_RX_NO_HEADER option is cleared, the received IPv6 raw data would include the IPv6 header, and the reported message length includes the IPv6 header.</span></span>

<span data-ttu-id="905a5-158">このオプションは、IPv4 や IPv6 の転送されるデータには影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="905a5-158">This option has no effect on IPv4 or IPv6 transmitted data.</span></span>

<span data-ttu-id="905a5-159">IP_HDRINCL が設定されている場合、アプリケーションでは、データ送信時に IPv4 ヘッダーが含められます。</span><span class="sxs-lookup"><span data-stu-id="905a5-159">If IP_HDRINCL is set, the application includes the IPv4 header when sending data.</span></span>  <span data-ttu-id="905a5-160">このオプションは、IPv6 転送には影響を与えず、既定では定義されません。</span><span class="sxs-lookup"><span data-stu-id="905a5-160">This option has no effect on IPv6 transmission and is not defined by default.</span></span> <span data-ttu-id="905a5-161">IP_RAW_IPV6_HDRINCL が設定されている場合、アプリケーションでは、データ送信時に IPv6 ヘッダーが含められます。</span><span class="sxs-lookup"><span data-stu-id="905a5-161">If IP_RAW_IPV6_HDRINCL is set, the application includes the IPv6 header when sending data.</span></span>  <span data-ttu-id="905a5-162">このオプションは、IPv4 転送には影響を与えず、既定では定義されません。</span><span class="sxs-lookup"><span data-stu-id="905a5-162">This option has no effect on IPv4 transmission and is not defined by default.</span></span>

<span data-ttu-id="905a5-163">IP_HDRINCL と IP_RAW_IPV6_HDRINCL は、IPv4 または IPv6 の受信には影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="905a5-163">IP_HDRINCL and IP_RAW_IPV6_HDRINCL have no effect on IPv4 or IPv6 reception.</span></span>

> [!NOTE]
> <span data-ttu-id="905a5-164">BSD 4.3 ソケットの仕様では、カーネルによって RAW パケットを各ソケットの受信バッファーにコピーする必要があると規定されています。</span><span class="sxs-lookup"><span data-stu-id="905a5-164">The BSD 4.3 Socket specification specifies that the kernel must copy the raw packet to each socket receive buffer.</span></span> <span data-ttu-id="905a5-165">ただし NetX Duo BSD では、同じプロトコルを共有するソケットが複数作成された場合は動作が未定義になります。</span><span class="sxs-lookup"><span data-stu-id="905a5-165">However in NetX Duo BSD, if multiple sockets are created sharing the same protocol, the behavior is undefined.</span></span>

## <a name="netx-duo-bsd-raw-packet-support"></a><span data-ttu-id="905a5-166">NetX Duo BSD RAW パケットのサポート</span><span class="sxs-lookup"><span data-stu-id="905a5-166">NetX Duo BSD Raw Packet Support</span></span>

<span data-ttu-id="905a5-167">PPPoE での RAW パケットのサポートを有効にするには、NX_BSD_RAW_PPPOE_SUPPORT を有効にして、NetX Duo BSD ラッパーをビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-167">To enable the raw packet support for PPPoE, NetX Duo BSD wrapper needs to be built with NX_BSD_RAW_PPPOE_SUPPORT enabled.</span></span>

<span data-ttu-id="905a5-168">次のコマンドでは、PPPoE の RAW パケットを処理するための BSD ソケットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-168">The following command creates a BSD socket to handle PPPoE raw packets:</span></span>

```c
Sockfd = socket(AF_PACKET, SOCK_RAW, protocol);
```

<span data-ttu-id="905a5-169">現在の BSD 実装では、AF_PACKET ファミリの 2 種類のプロトコルのみがサポートされています</span><span class="sxs-lookup"><span data-stu-id="905a5-169">The current BSD implementation only supports two protocol types in AF_PACKET family</span></span>

- <span data-ttu-id="905a5-170">`ETHERTYPE_PPPOE_DISC`: PPPoE の検出パケット。</span><span class="sxs-lookup"><span data-stu-id="905a5-170">`ETHERTYPE_PPPOE_DISC`: PPPoE Discovery packets.</span></span> <span data-ttu-id="905a5-171">MAC データ フレーム内では、検出パケットのイーサネット フレームの種類は 0x8863 です。</span><span class="sxs-lookup"><span data-stu-id="905a5-171">In the MAC data frame, the Discovery packets have the Ethernet frame type 0x8863.</span></span>

- <span data-ttu-id="905a5-172">`ETHERTYPE_PPPOE_SESS`: PPP のセッション パケット。</span><span class="sxs-lookup"><span data-stu-id="905a5-172">`ETHERTYPE_PPPOE_SESS`: PPP Session packets.</span></span> <span data-ttu-id="905a5-173">MAC データ フレーム内では、セッション パケットのイーサネット フレームの種類は 0x8864 です。</span><span class="sxs-lookup"><span data-stu-id="905a5-173">In the MAC data frame, the Session packets have the Ethernet frame type 0x8864.</span></span>

<span data-ttu-id="905a5-174">構造体 `sockaddr_ll` は、PPPoE フレームの送受信時にパラメーターを指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-174">The structure `sockaddr_ll` is used to specify parameters when sending or receiving PPPoE frames.</span></span>

<span data-ttu-id="905a5-175">`struct sockaddr_ll` は次のように宣言されています。</span><span class="sxs-lookup"><span data-stu-id="905a5-175">`struct sockaddr_ll` is declared as:</span></span>

```c
struct sockaddr_ll
{
    USHORT  sll_family;     /* Must be AF_PACKET */
    USHORT  sll_protocol;   /* LL frame type */
    INT     sll_ifindex;    /* Interface Index. */
    USHORT  sll_hatype;     /* Header type */
    UCHAR   sll_pkttype;    /* Packet type */
    UCHAR   sll_halen;      /* Length of address */
    UCHAR   sll_addr[8];    /* Physical layer address */
};
```

> [!NOTE]
> <span data-ttu-id="905a5-176">構造体のすべてのフィールドが `sendto()` または `recvfrom()` によって使用されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="905a5-176">Not every field in the structure is used by `sendto()` or `recvfrom()`.</span></span> <span data-ttu-id="905a5-177">PPPoE パケットを送受信するために `sockaddr_ll` を設定する方法については、下記の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="905a5-177">See the description below on how to set up the `sockaddr_ll` for sending and receiving PPPoE packets.</span></span>

<span data-ttu-id="905a5-178">指定されるプロトコルとは無関係に、AF_PACKET ファミリで作成されたソケットを使用して、PPPoE 検出パケットまたは PPP セッション パケットのいずれかを送信できます。</span><span class="sxs-lookup"><span data-stu-id="905a5-178">Socket created in the AF_PACKET family can be used to send either PPPoE Discovery packets or PPP session packets, regardless of the protocol specified.</span></span> <span data-ttu-id="905a5-179">PPPoE パケットの送信時には、MAC ヘッダー (宛先 MAC アドレス、送信元 MAC アドレス、フレームの種類) を含め、適切な形式の PPPoE フレームが含まれるバッファーを、アプリケーションで準備する必要があります。バッファーのサイズには、14 バイトのイーサネット ヘッダーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="905a5-179">When transmitting a PPPoE packet, application must prepare the buffer that includes properly formatted PPPoE frame, including the MAC headers (Destination MAC address, source MAC address, and frame type.) The size of the buffer includes the 14-byte Ethernet header.</span></span>

<span data-ttu-id="905a5-180">`sockaddr_ll` 構造体の `sll_ifindex` は、このパケットの送信に使用される物理インターフェイスを指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-180">The `sockaddr_ll` struct, the `sll_ifindex` is used to indicate the physical interface to be used for sending this packet.</span></span> <span data-ttu-id="905a5-181">この構造体の残りのフィールドは使用されません。</span><span class="sxs-lookup"><span data-stu-id="905a5-181">The rest of the fields in the structure are not used.</span></span> <span data-ttu-id="905a5-182">使用されないフィールドに設定された値は、BSD 内部プロセスによって無視されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-182">Values set to the unused fields are ignored by the BSD internal process.</span></span>

<span data-ttu-id="905a5-183">次のコード ブロックは、PPPoE パケットの送信方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="905a5-183">The following code block illustrates how to transmit a PPPoE packet:</span></span>

```c
struct sockaddr_ll peer_addr;

/* Transmit a PPPoE frame using the primary network interface. */
peer_addr.sll_ifindex = 0;
n = sendto(sockfd, frame, frame_size, 0, (struct
        sockaddr*)&peer_addr, sizeof(peer_addr));
```

<span data-ttu-id="905a5-184">戻り値では、転送されたバイト数が示されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-184">The return value indicates the number of bytes transmitted.</span></span> <span data-ttu-id="905a5-185">PPPoE パケットはメッセージベースであるため、転送が成功すると、送信されたバイト数は (14 バイトのイーサネット ヘッダーを含む) パケットのサイズと一致します。</span><span class="sxs-lookup"><span data-stu-id="905a5-185">Since PPPoE packets are message-based, on a successful transmission, the number of bytes sent matches the size of the packet, including the 14-byte Ethernet header.</span></span>

<span data-ttu-id="905a5-186">PPPoE パケットは、`recvfrom()` を使用して受信できます。</span><span class="sxs-lookup"><span data-stu-id="905a5-186">PPPoE packets can be received using `recvfrom()`.</span></span> <span data-ttu-id="905a5-187">受信バッファーは、イーサネットの MTU サイズのメッセージを格納するのに十分な大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-187">The receive buffer must be big enough to accommodate message of Ethernet MTU size.</span></span> <span data-ttu-id="905a5-188">受信した PPPoE パケットには、14 バイトのイーサネット ヘッダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="905a5-188">The received PPPoE packet includes 14-byte Ethernet header.</span></span> <span data-ttu-id="905a5-189">PPPoE パケットの受信時には、`ETHERTYPE_PPPOE_DISC` プロトコルを使用して作成されたソケットでのみ、PPPoE 検出パケットを受信できます。</span><span class="sxs-lookup"><span data-stu-id="905a5-189">On receiving PPPoE packets, PPPoE Discovery packets can only be received by socket created with protocol `ETHERTYPE_PPPOE_DISC`.</span></span> <span data-ttu-id="905a5-190">同様に、`ETHERTYPE_PPPOE_SESS` プロトコルを使用して作成されたソケットでのみ、PPP セッション パケットを受信できです。</span><span class="sxs-lookup"><span data-stu-id="905a5-190">Similarly, PPP session packets can only be received by socket created with protocol `ETHERTYPE_PPPOE_SESS`.</span></span> <span data-ttu-id="905a5-191">同じ種類のプロトコルに対して複数のソケットが作成された場合、到着する PPPoE パケットは、最初に作成されたソケットに転送されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-191">If multiple sockets are created for the same protocol type, arriving PPPoE packets are forwarded to the socket created first.</span></span> <span data-ttu-id="905a5-192">そのプロトコルに対して作成された最初のソケットが閉じられると、作成順序で次のソケットが、これらのパケットの受信に使用されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-192">If the first socket created for the protocol is closed, the next socket in the order of creation is used for receiving these packets.</span></span>

<span data-ttu-id="905a5-193">PPPoE パケットの受信後は、`sockaddr_ll` 構造体の以下のフィールドが有効になります。</span><span class="sxs-lookup"><span data-stu-id="905a5-193">After a PPPoE packet is received, the following fields in the `sockaddr_ll` struct are valid:</span></span>
- <span data-ttu-id="905a5-194">**sll_family**: AF_PACKET になるように BSD 内部で設定されます</span><span class="sxs-lookup"><span data-stu-id="905a5-194">**sll_family**: Set by the BSD internal to be AF_PACKET</span></span>
- <span data-ttu-id="905a5-195">**sll_ifindex**: パケットを受信したインターフェイスを示します</span><span class="sxs-lookup"><span data-stu-id="905a5-195">**sll_ifindex**: Indicates the interface from which the packet is received</span></span>
- <span data-ttu-id="905a5-196">**sll_protocol**: 受信したパケットの種類に設定されます。`ETHERTYPE_PPPOE_DISC` または `ETHERTYPE_PPPOE_SESS` です</span><span class="sxs-lookup"><span data-stu-id="905a5-196">**sll_protocol**: Set to the type of packet received: `ETHERTYPE_PPPOE_DISC` or `ETHERTYPE_PPPOE_SESS`</span></span>

## <a name="eliminating-internal-bsd-thread"></a><span data-ttu-id="905a5-197">内部 BSD スレッドの除去</span><span class="sxs-lookup"><span data-stu-id="905a5-197">Eliminating Internal BSD Thread</span></span>

<span data-ttu-id="905a5-198">既定では、BSD では処理の一部を実行するために内部スレッドが利用されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-198">By default, BSD utilizes an internal thread to perform some of its processing.</span></span> <span data-ttu-id="905a5-199">メモリの制約が厳しいシステムでは、NX_BSD_TIMEOUT_PROCESS_IN_TIMER を定義して BSD をビルドできます。これにより、内部 BSD スレッドが除去され、その代わりに、同じ処理を実行するために内部タイマーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-199">In systems with tight memory constraints, BSD can be built with NX_BSD_TIMEOUT_PROCESS_IN_TIMER defined, which eliminates the internal BSD thread and instead uses an internal timer to perform the same processing.</span></span> <span data-ttu-id="905a5-200">これで、内部 BSD スレッドの制御ブロックとスタックに必要なメモリがなくなります。</span><span class="sxs-lookup"><span data-stu-id="905a5-200">This eliminates the memory required for the internal BSD thread control block and stack.</span></span> <span data-ttu-id="905a5-201">ただし、全体としてのタイマー処理は大幅に増加し、BSD の処理が必要以上に高い優先順位で実行される可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="905a5-201">However, overall timer processing is significantly increased and the BSD processing may also execute at a higher priority than needed.</span></span>

<span data-ttu-id="905a5-202">ThreadX タイマーのコンテキストで実行するように BSD ソケットを構成するには、*nxd_bsd.h* で NX_BSD_TIMEOUT_PROCESS_IN_TIMER を定義します。</span><span class="sxs-lookup"><span data-stu-id="905a5-202">To configure BSD sockets to run in the ThreadX timer context, define NX_BSD_TIMEOUT_PROCESS_IN_TIMER in *nxd_bsd.h*.</span></span> <span data-ttu-id="905a5-203">タイマー コンテキストで BSD タスクを実行するように BSD レイヤーが構成されている場合、*bsd_initialize* の呼び出しでは以下の 3 つのパラメーターは無視されます。これらは NULL に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-203">If the BSD layer is configured to execute the BSD tasks in the timer context, in the call to *bsd_initialize*, the following three parameters are ignored, and should be set to NULL:</span></span>

- <span data-ttu-id="905a5-204">**bsd_thread_stack_area**</span><span class="sxs-lookup"><span data-stu-id="905a5-204">**bsd_thread_stack_area**</span></span>
- <span data-ttu-id="905a5-205">**bsd_thread_stack_size**</span><span class="sxs-lookup"><span data-stu-id="905a5-205">**bsd_thread_stack_size**</span></span>
- <span data-ttu-id="905a5-206">**bsd_thread_priority**</span><span class="sxs-lookup"><span data-stu-id="905a5-206">**bsd_thread_priority**</span></span>

## <a name="netx-duo-bsd-with-dns-support"></a><span data-ttu-id="905a5-207">DNS のサポートが有効な NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="905a5-207">NetX Duo BSD with DNS Support</span></span>

<span data-ttu-id="905a5-208">NX_BSD_ENABLE_DNS が定義されている場合は、NetX Duo BSD で、ホスト名またはホスト IP の情報を取得する DNS クエリを送信できます。</span><span class="sxs-lookup"><span data-stu-id="905a5-208">If NX_BSD_ENABLE_DNS is defined, NetX Duo BSD can send DNS queries to obtain hostname or host IP information.</span></span> <span data-ttu-id="905a5-209">この機能では、*nx_dns_create* サービスを使用して、NetX DNS クライアントを事前に作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-209">This feature requires a NetX DNS Client to be previously created using the *nx_dns_create* service.</span></span> <span data-ttu-id="905a5-210">DNS インスタンスには、1 つ以上の既知の DNS サーバーの IP アドレスを登録する必要があります。IPv4 サーバーのアドレスを追加するには *nx_dns_server_add* サービスを使用し、IPv4 または IPv6、いずれかのサーバー アドレスを追加するには *nxd_dns_server_add* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="905a5-210">One or more known DNS server IP addresses must be registered with the DNS instance using the *nx_dns_server_add* service for adding IPv4 server addresses, or using the *nxd_dns_server_add* service for adding either IPv4 or IPv6 server addresses.</span></span>

<span data-ttu-id="905a5-211">DNS のサービスとメモリ割り当ては、*getaddrinfo* および *getnameinfo* サービスによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-211">DNS services and memory allocation are used by *getaddrinfo* and *getnameinfo* services:</span></span>

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
        const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
        char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

<span data-ttu-id="905a5-212">BSD アプリケーションがホスト名を使用して *getaddrinfo* を呼び出すと、NetX BSD では、以下のいずれかのサービスを呼び出して IP アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="905a5-212">When the BSD application calls *getaddrinfo* with a hostname, NetX BSD will call any of the below services to obtain the IP address:</span></span>

- <span data-ttu-id="905a5-213">**nx_dns_ipv4_address_by_name_get**</span><span class="sxs-lookup"><span data-stu-id="905a5-213">**nx_dns_ipv4_address_by_name_get**</span></span>
- <span data-ttu-id="905a5-214">**nxd_dns_ipv6_address_by_name_get**</span><span class="sxs-lookup"><span data-stu-id="905a5-214">**nxd_dns_ipv6_address_by_name_get**</span></span>
- <span data-ttu-id="905a5-215">**nx_dns_cname_get**</span><span class="sxs-lookup"><span data-stu-id="905a5-215">**nx_dns_cname_get**</span></span>

<span data-ttu-id="905a5-216">*nx_dns_ipv4_address_by_name_get* と *nxd_dns_ipv6_address_by_name_get* の場合、NetX BSD では、それぞれ、ipv4_addr_buffer と ipv6_addr_buffer のメモリ領域が使用されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-216">For *nx_dns_ipv4_address_by_name_get* and *nxd_dns_ipv6_address_by_name_get*, NetX BSD uses the ipv4_addr_buffer and ipv6_addr_buffer memory areas respectively.</span></span> <span data-ttu-id="905a5-217">これらのバッファーのサイズは、それぞれ、(NX_BSD_IPV4_ADDR_PER_HOST \* 4) と (NX_BSD_IPV6_ADDR_PER_HOST \* 16) によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-217">The size of these buffers are defined by (NX_BSD_IPV4_ADDR_PER_HOST \* 4) and (NX_BSD_IPV6_ADDR_PER_HOST \* 16) respectively.</span></span>

<span data-ttu-id="905a5-218">*getaddrinfo* からのアドレス情報を返すために、NetX BSD では、ThreadX ブロック メモリ テーブル nx_bsd_addrinfo_pool_memory を使用します。このメモリ領域は、構成可能な別のオプション セットである NX_BSD_IPV4_ADDR_MAX_NUM と NX_BSD_IPV6_ADDR_MAX_NUM によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-218">For returning address information from *getaddrinfo*, NetX BSD uses the ThreadX block memory table nx_bsd_addrinfo_pool_memory, whose memory area is defined by another set of configurable options, NX_BSD_IPV4_ADDR_MAX_NUM and NX_BSD_IPV6_ADDR_MAX_NUM.</span></span>

<span data-ttu-id="905a5-219">上の構成オプションの詳細については、「**全般的構成オプション**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="905a5-219">See **General Configuration Options** for more details on the above configuration options.</span></span>

<span data-ttu-id="905a5-220">さらに、NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されており、ホスト入力が正規名である場合、NetX BSD では、以前に作成されたブロック プール \`_nx_bsd_cname_block_pool からメモリを動的に割り当てます</span><span class="sxs-lookup"><span data-stu-id="905a5-220">Additionally, if NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, and the host input is a canonical name, NetX Duo BSD will allocate memory dynamically from a previously created block pool \`_nx_bsd_cname_block_pool</span></span>

> [!NOTE]
> <span data-ttu-id="905a5-221">*getaddrinfo* の呼び出し後、*freeaddrinfo* サービスを使用して、res 引数によって指し示されたメモリを解放してブロック テーブルに戻す処理は、BSD アプリケーションで行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-221">After calling *getaddrinfo* the BSD application is responsible for releasing the memory pointed to by the res argument back to the block table using the *freeaddrinfo* service.</span></span>

## <a name="netx-duo-bsd-limitations"></a><span data-ttu-id="905a5-222">NetX Duo BSD の制限事項</span><span class="sxs-lookup"><span data-stu-id="905a5-222">NetX Duo BSD Limitations</span></span>

<span data-ttu-id="905a5-223">パフォーマンスやアーキテクチャの問題のため、NetX Duo BSD では、BSD 4.3 ソケット機能のすべてがサポートされているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="905a5-223">Due to performance and architecture issues, NetX Duo BSD does not support all the BSD 4.3 socket features:</span></span>

<span data-ttu-id="905a5-224">INT フラグは、*send、recv、sendto*、*recvfrom* の呼び出しではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="905a5-224">INT flags are not supported for *send, recv, sendto* and *recvfrom* calls.</span></span>

## <a name="general-configuration-options"></a><span data-ttu-id="905a5-225">全般的構成オプション</span><span class="sxs-lookup"><span data-stu-id="905a5-225">General Configuration Options</span></span>

<span data-ttu-id="905a5-226">*nxd_bsd.h* 内で、ユーザーが構成できるオプションを指定することで、特定のアプリケーション要件に合わせて NetX Duo BSD ソケットを微調整することができます。</span><span class="sxs-lookup"><span data-stu-id="905a5-226">User configurable options in *nxd_bsd.h* allow the application to fine tune NetX Duo BSD sockets for its particular application requirements.</span></span>

<span data-ttu-id="905a5-227">以下に、コンパイル時に設定される構成可能なオプションの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="905a5-227">The following is the list of configurable options that are set at compile time:</span></span>

- <span data-ttu-id="905a5-228">**NX_BSD_TCP_WINDOW**: TCP ソケットの作成呼び出しで使用されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-228">**NX_BSD_TCP_WINDOW**: Used in TCP socket create calls.</span></span> <span data-ttu-id="905a5-229">64k が 100 MB イーサネットでの標準的なウィンドウ サイズです。</span><span class="sxs-lookup"><span data-stu-id="905a5-229">64k is typical window size for 100Mb Ethernet.</span></span> <span data-ttu-id="905a5-230">既定値は、65535 です。</span><span class="sxs-lookup"><span data-stu-id="905a5-230">The default value is 65535.</span></span>

- <span data-ttu-id="905a5-231">**NX_BSD_SOCKFD_START**: これは、BSD ソケットのファイル記述子の開始値を表す論理インデックスです。</span><span class="sxs-lookup"><span data-stu-id="905a5-231">**NX_BSD_SOCKFD_START**: This is the logical index for the BSD socket file descriptor start value.</span></span> <span data-ttu-id="905a5-232">既定では、このオプションは 32 です。</span><span class="sxs-lookup"><span data-stu-id="905a5-232">By default this option is 32.</span></span>

- <span data-ttu-id="905a5-233">**NX_BSD_MAX_SOCKETS**: BSD レイヤーで使用できるソケットの合計最大数を指定します。32 の倍数にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-233">**NX_BSD_MAX_SOCKETS**: Specifies the maximum number of total sockets available in the BSD layer and must be a multiple of 32.</span></span> <span data-ttu-id="905a5-234">この値は、既定で 32 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-234">The value is defaulted to 32.</span></span>

- <span data-ttu-id="905a5-235">**NX_BSD_SOCKET_QUEUE_MAX**: 受信ソケット キューに格納される UDP パケットの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="905a5-235">**NX_BSD_SOCKET_QUEUE_MAX**: Specifies the maximum number of UDP packets stored on the receive socket queue.</span></span> <span data-ttu-id="905a5-236">この値は、既定で 5 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="905a5-236">The value is defaulted to 5.</span></span>

- <span data-ttu-id="905a5-237">**NX_BSD_MAX_LISTEN_BACKLOG**: これで、BSD TCP ソケットのリッスン キュー ("バックログ") のサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="905a5-237">**NX_BSD_MAX_LISTEN_BACKLOG**: This specifies the size of the listen queue ('backlog') for BSD TCP sockets.</span></span> <span data-ttu-id="905a5-238">既定値は 5 です。</span><span class="sxs-lookup"><span data-stu-id="905a5-238">The default value is 5.</span></span>

- <span data-ttu-id="905a5-239">**NX_MICROSECOND_PER_CPU_TICK**: スケジューラのタイマー ティックあたりのマイクロ秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="905a5-239">**NX_MICROSECOND_PER_CPU_TICK**: Specifies the number of microseconds per scheduler timer tick.</span></span>

- <span data-ttu-id="905a5-240">**NX_BSD_TIMEOUT**: BSD によって求められている、NetX Duo 内部呼び出しでのタイマー ティックのタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="905a5-240">**NX_BSD_TIMEOUT**: Specifies the timeout in timer ticks on NetX Duo internal calls required by BSD.</span></span> <span data-ttu-id="905a5-241">既定値は (20 × NX_IP_PERIODIC_RATE) です。</span><span class="sxs-lookup"><span data-stu-id="905a5-241">The default value is (20 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="905a5-242">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: NetX Duo 切断呼び出しでのタイマー ティックのタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="905a5-242">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: Specifies the timeout in timer ticks on NetX Duo disconnect call.</span></span> <span data-ttu-id="905a5-243">既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="905a5-243">The default value is 1.</span></span>

- <span data-ttu-id="905a5-244">**NX_BSD_PRINT_ERRORS**: 設定されている場合、BSD 関数のエラー状態の戻りにおいて、エラーが発生した行番号とエラーの種類 (NX_SOC_ERROR など) が返されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-244">**NX_BSD_PRINT_ERRORS**: If set, the error status return of a BSD function returns a line number and type of error e.g. NX_SOC_ERROR where the error occurs.</span></span> <span data-ttu-id="905a5-245">このためアプリケーション開発者は、デバッグ出力を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-245">This requires the application developer to define the debug output.</span></span> <span data-ttu-id="905a5-246">既定の設定は無効であり、*nxd_bsd.h* ではデバッグ出力が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="905a5-246">The default setting is disabled and no debug output is specified in *nxd_bsd.h*.</span></span>

- <span data-ttu-id="905a5-247">**NX_BSD_TIMER_RATE**: BSD の定期的なタイマー タスクが実行されるまでの間隔。</span><span class="sxs-lookup"><span data-stu-id="905a5-247">**NX_BSD_TIMER_RATE**: Interval after which BSD periodic timer task runs.</span></span> <span data-ttu-id="905a5-248">既定値は 1 秒 (1 \* NX_IP_PERIODIC_RATE) です。</span><span class="sxs-lookup"><span data-stu-id="905a5-248">The default value is 1 second (1 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="905a5-249">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: 設定されている場合、このオプションにより、BSD タイムアウト プロセスをシステム タイマーのコンテキストで実行できます。</span><span class="sxs-lookup"><span data-stu-id="905a5-249">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: If set, this option allows the BSD timeout process to execute in the system timer context.</span></span> <span data-ttu-id="905a5-250">既定の動作は無効です。</span><span class="sxs-lookup"><span data-stu-id="905a5-250">The default behavior is disabled.</span></span> <span data-ttu-id="905a5-251">この機能については、第 2 章「NetX Duo BSD のインストールと使用」で詳細に説明されています。</span><span class="sxs-lookup"><span data-stu-id="905a5-251">This feature is described in more detail in Chapter 2 "Installation and Use of NetX Duo BSD".</span></span>

- <span data-ttu-id="905a5-252">**NX_BSD_RAW_PPPOE_SUPPORT**: PPPoE での RAW パケットのサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="905a5-252">**NX_BSD_RAW_PPPOE_SUPPORT**: Enable PPPoE raw packet support.</span></span> <span data-ttu-id="905a5-253">既定では、このオプションは有効になりません。</span><span class="sxs-lookup"><span data-stu-id="905a5-253">By default this option is not enabled.</span></span>

- <span data-ttu-id="905a5-254">**NX_BSD_ENABLE_DNS**: 有効になっている場合、NetX Duo BSD により、ホスト名またはホスト IP アドレスの DNS クエリが送信されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-254">**NX_BSD_ENABLE_DNS**: If enabled, NetX Duo BSD will send a DNS query for a hostname or host IP address.</span></span> <span data-ttu-id="905a5-255">DNS クライアント インスタンスが事前に作成され、起動されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-255">Requires a DNS Client instance to be previously created and started.</span></span> <span data-ttu-id="905a5-256">既定では、有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="905a5-256">By default it is not enabled.</span></span>

- <span data-ttu-id="905a5-257">**NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: RAW ソケット テーブルのサイズを定義します。</span><span class="sxs-lookup"><span data-stu-id="905a5-257">**NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: Defines the size of the raw socket table.</span></span> <span data-ttu-id="905a5-258">値は 2 の累乗にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-258">The value must be a power of two.</span></span> <span data-ttu-id="905a5-259">NetX BSD では、RAW パケットを送受信するために、NX_BSD_SOCKETS 型のソケットの配列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-259">NetX BSD creates an array of sockets of type NX_BSD_SOCKETS for sending and receiving raw packets.</span></span> <span data-ttu-id="905a5-260">NX_ENABLE_IP_RAW_PACKET_FILTER が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-260">NX_ENABLE_IP_RAW_PACKET_FILTER must be enabled.</span></span> <span data-ttu-id="905a5-261">既定では 32 です。</span><span class="sxs-lookup"><span data-stu-id="905a5-261">By default it is 32.</span></span>

- <span data-ttu-id="905a5-262">**NX_BSD_IPV4_ADDR_MAX_NUM**: *getaddrinfo* によって返される IPv4 アドレスの最大数。</span><span class="sxs-lookup"><span data-stu-id="905a5-262">**NX_BSD_IPV4_ADDR_MAX_NUM**: Maximum number of IPv4 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="905a5-263">*getaddrinfo* でのアドレス情報の格納にメモリを動的に割り当てるため、これを NX_BSD_IPV6_ADDR_MAX_NUM と一緒に使用して、NetX BSD ブロック プール nx_bsd_addrinfo_block_pool のサイズを定義します。</span><span class="sxs-lookup"><span data-stu-id="905a5-263">This along with NX_BSD_IPV6_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span> <span data-ttu-id="905a5-264">既定値は 5 です。</span><span class="sxs-lookup"><span data-stu-id="905a5-264">The default value is 5.</span></span>

- <span data-ttu-id="905a5-265">**NX_BSD_IPV6_ADDR_MAX_NUM**: *getaddrinfo* によって返される IPv6 アドレスの最大数。</span><span class="sxs-lookup"><span data-stu-id="905a5-265">**NX_BSD_IPV6_ADDR_MAX_NUM**: Maximum number of IPv6 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="905a5-266">*getaddrinfo* でのアドレス情報の格納にメモリを動的に割り当てるため、これを NX_BSD_IPV4_ADDR_MAX_NUM と一緒に使用して、NetX BSD ブロック プール nx_bsd_addrinfo_block_pool のサイズを定義します。</span><span class="sxs-lookup"><span data-stu-id="905a5-266">This along with NX_BSD_IPV4_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span>

- <span data-ttu-id="905a5-267">**NX_BSD_IPV4_ADDR_PER_HOST**: DNS クエリごとに格納される IPv4 アドレスの最大数を定義します。</span><span class="sxs-lookup"><span data-stu-id="905a5-267">**NX_BSD_IPV4_ADDR_PER_HOST**: Defines maximum IPv4 addresses stored per DNS query.</span></span> <span data-ttu-id="905a5-268">既定値は 5 です。</span><span class="sxs-lookup"><span data-stu-id="905a5-268">The default value is 5.</span></span>

- <span data-ttu-id="905a5-269">**NX_BSD_IPV6_ADDR_PER_HOST**: DNS クエリごとに格納される IPv6 アドレスの最大数を定義します。</span><span class="sxs-lookup"><span data-stu-id="905a5-269">**NX_BSD_IPV6_ADDR_PER_HOST**: Defines maximum IPv6 addresses stored per DNS query.</span></span> <span data-ttu-id="905a5-270">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="905a5-270">The default value is 2.</span></span>

## <a name="bsd-socket-options"></a><span data-ttu-id="905a5-271">BSD ソケット オプション</span><span class="sxs-lookup"><span data-stu-id="905a5-271">BSD Socket Options</span></span>

<span data-ttu-id="905a5-272">以下の一覧に示した NetX Duo BSD ソケット オプションは、*setsockopt* サービスを使用して、ソケットごとに実行時に有効 (または無効) にすることができます。</span><span class="sxs-lookup"><span data-stu-id="905a5-272">The following list of NetX Duo BSD socket options can be enabled (or disabled) at run time on a per socket basis using the *setsockopt* service:</span></span>

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, 
                const void *option_value, INT option_length);
```

<span data-ttu-id="905a5-273">option_level には、2 つの異なる設定があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-273">There are two different settings for option_level.</span></span>

<span data-ttu-id="905a5-274">実行時のソケット オプションの最初の種類は、ソケット レベルのオプションのための SOL_SOCKET です。</span><span class="sxs-lookup"><span data-stu-id="905a5-274">The first type of run time socket options is SOL_SOCKET for socket level options.</span></span> <span data-ttu-id="905a5-275">ソケット レベルのオプションを有効にするには、option_level を SOL_SOCKET に設定し、option_name を SO_BROADCAST *などの特定のオプションに設定して *setsockopt* を呼び出します。*</span><span class="sxs-lookup"><span data-stu-id="905a5-275">To enable a socket level option, call *setsockopt* with option_level set to SOL_SOCKET and option_name set to the specific option e.g. SO_BROADCAST *.*</span></span> <span data-ttu-id="905a5-276">オプション設定を取得するには、option_level を再び SOL_SOCKET に設定して option_name に対する *getsockopt* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="905a5-276">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to SOL_SOCKET.</span></span>

<span data-ttu-id="905a5-277">以下に、実行時のソケット レベルのオプションの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="905a5-277">The list of run time socket level options is shown below.</span></span>

- <span data-ttu-id="905a5-278">**SO_BROADCAST**: 設定されている場合、NetX ソケットからのブロードキャスト パケットの送受信が可能になります。</span><span class="sxs-lookup"><span data-stu-id="905a5-278">**SO_BROADCAST**:  If set, this enables sending and receiving broadcast packets from Netx sockets.</span></span> <span data-ttu-id="905a5-279">これは NetX Duo の既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="905a5-279">This is the default behavior for NetX Duo.</span></span> <span data-ttu-id="905a5-280">すべてのソケットがこの機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="905a5-280">All sockets have this capability.</span></span>

- <span data-ttu-id="905a5-281">**SO_ERROR**: *getsockopt* サービスを使用して、指定したソケットの以前のソケット操作に関するソケット状態を取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-281">**SO_ERROR**:  Used to obtain socket status on the previous socket operation of the specified socket, using the *getsockopt* service.</span></span> <span data-ttu-id="905a5-282">すべてのソケットがこの機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="905a5-282">All sockets have this capability.</span></span>

- <span data-ttu-id="905a5-283">**SO_KEEPALIVE**: 設定されている場合、TCP キープ アライブ機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="905a5-283">**SO_KEEPALIVE**:  If set, this enables the TCP Keep Alive feature.</span></span> <span data-ttu-id="905a5-284">これを使用するには、*nx_user.h* で NX_TCP_ENABLE_KEEPALIVE を定義して、NetX Duo ライブラリをビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-284">This requires the NetX Duo library to be built with NX_TCP_ENABLE_KEEPALIVE defined in *nx_user.h*.</span></span> <span data-ttu-id="905a5-285">既定では、この機能は無効になります。</span><span class="sxs-lookup"><span data-stu-id="905a5-285">By default this feature is disabled.</span></span>

- <span data-ttu-id="905a5-286">**SO_RCVTIMEO**: NetX Duo BSD ソケットでパケットを受信するための待機オプションを秒単位で設定します。</span><span class="sxs-lookup"><span data-stu-id="905a5-286">**SO_RCVTIMEO**:  This sets the wait option in seconds for receiving packets on NetX Duo BSD sockets.</span></span> <span data-ttu-id="905a5-287">既定値は NX_WAIT_FOREVER (0xFFFFFFFF) です。または、非ブロッキングが有効になっている場合は NX_NO_WAIT (0x0) です。</span><span class="sxs-lookup"><span data-stu-id="905a5-287">The default value is the NX_WAIT_FOREVER (0xFFFFFFFF) or, if non-blocking is enabled, NX_NO_WAIT (0x0).</span></span>

- <span data-ttu-id="905a5-288">**SO_RCVBUF**: TCP ソケットのウィンドウ サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="905a5-288">**SO_RCVBUF**:  This sets the window size of the TCP socket.</span></span> <span data-ttu-id="905a5-289">既定値の NX_BSD_TCP_WINDOW は、BSD TCP ソケットでは 64k に設定されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-289">The default value, NX_BSD_TCP_WINDOW, is set to 64k for BSD TCP sockets.</span></span> <span data-ttu-id="905a5-290">65535 を超えるサイズを設定するには、NX_TCP_ENABLE_WINDOW_SCALING を定義して、NetX ライブラリをビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-290">To set the size over 65535 requires the NetX Duo library to be built with the NX_TCP_ENABLE_WINDOW_SCALING be defined.</span></span>

- <span data-ttu-id="905a5-291">**SO_REUSEADDR**: 設定されている場合、複数のソケットを 1 つのポートにマップできるようになります。</span><span class="sxs-lookup"><span data-stu-id="905a5-291">**SO_REUSEADDR**:  If set, this enables multiple sockets to be mapped to one port.</span></span> <span data-ttu-id="905a5-292">典型的な使い方は TCP サーバー ソケット用です。</span><span class="sxs-lookup"><span data-stu-id="905a5-292">The typical usage is for the TCP Server socket.</span></span> <span data-ttu-id="905a5-293">これは NetX Duo ソケットの既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="905a5-293">This is the default behavior of NetX Duo sockets.</span></span>

<span data-ttu-id="905a5-294">実行時のソケット オプションの 2 番目の種類は、IP オプションのレベルです。</span><span class="sxs-lookup"><span data-stu-id="905a5-294">The second type of run time socket options is the IP option level.</span></span> <span data-ttu-id="905a5-295">IP レベルのオプションを有効にするには、option_level を IP_PROTO に設定し、option_name を IP_MULTICAST_TTL *などのオプションに設定して、*setsockopt\* を呼び出します。\*</span><span class="sxs-lookup"><span data-stu-id="905a5-295">To enable an IP level option, call *setsockopt* with option_level set to IP_PROTO and option_name set to the option e.g. IP_MULTICAST_TTL *.*</span></span> <span data-ttu-id="905a5-296">オプション設定を取得するには、option_level を再び IP_PROTO に設定して option_name に対する *getsockopt* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="905a5-296">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to IP_PROTO.</span></span>

<span data-ttu-id="905a5-297">以下に、実行時の IP レベルのオプションの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="905a5-297">The list of run time IP level options is shown below.</span></span>

- <span data-ttu-id="905a5-298">**IP_MULTICAST_TTL**: UDP ソケットの有効期限を設定します。</span><span class="sxs-lookup"><span data-stu-id="905a5-298">**IP_MULTICAST_TTL**:  This sets the time to live for UDP sockets.</span></span> <span data-ttu-id="905a5-299">ソケットが作成されるときの既定値は NX_IP_TIME_TO_LIVE (0x80) です。</span><span class="sxs-lookup"><span data-stu-id="905a5-299">The default value is NX_IP_TIME_TO_LIVE (0x80) when the socket is created.</span></span> <span data-ttu-id="905a5-300">この値は、このソケット オプションで *setsockopt* を呼び出してオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="905a5-300">This value can be overridden by calling *setsockopt* with this socket option.</span></span>

- <span data-ttu-id="905a5-301">**IP_RAW_IPV6_HDRINCL**: このオプションが設定されている場合は、呼び出し元のアプリケーションで、BSD によって作成された RAW IPv6 ソケットで送信されようとしているデータに、IPv6 ヘッダーとアプリケーション ヘッダー (省略可能) を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-301">**IP_RAW_IPV6_HDRINCL**:  If this option is set, the calling application must append an IPv6 header and optionally application headers to data being transmitted on raw IPv6 sockets created by BSD.</span></span> <span data-ttu-id="905a5-302">このオプションを使用するには、その IP タスクで RAW ソケットの処理が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-302">To use this option, raw socket processing must be enabled on the IP task.</span></span>

- <span data-ttu-id="905a5-303">**IP_ADD_MEMBERSHIP**: このオプションが設定されている場合、BSD ソケット (UDP ソケットにのみ該当) が、指定された IGMP グループに参加できるようになります。</span><span class="sxs-lookup"><span data-stu-id="905a5-303">**IP_ADD_MEMBERSHIP**:  If set, this options enables the BSD socket (applies only to UDP sockets) to join the specified IGMP group.</span></span>

- <span data-ttu-id="905a5-304">**IP_DROP_MEMBERSHIP**: このオプションが設定されている場合、BSD ソケット (UDP ソケットにのみ該当) が、指定された IGMP グループから離脱できるようになります。</span><span class="sxs-lookup"><span data-stu-id="905a5-304">**IP_DROP_MEMBERSHIP**:  If set, this options enables the BSD socket (applies only to UDP sockets) to leave the specified IGMP group.</span></span>

- <span data-ttu-id="905a5-305">**IP_HDRINCL**: このオプションが設定されている場合は、呼び出し元のアプリケーションで、BSD で作成された RAW IPv4 ソケットで送信されようとしているデータに、IP ヘッダーとアプリケーション ヘッダー (省略可能) を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-305">**IP_HDRINCL**:  If this option is set, the calling application must append the IP header and optionally application headers to data being transmitted on raw IPv4 sockets created in BSD.</span></span> <span data-ttu-id="905a5-306">このオプションを使用するには、その IP タスクで RAW ソケットの処理が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-306">To use this option, raw socket processing must be enabled on the IP task.</span></span>

- <span data-ttu-id="905a5-307">**IP_RAW_RX_NO_HEADER**: 解除されている場合、BSD で作成された RAW IPv6 ソケットの受信データに、IPv6 ヘッダーが含められます。</span><span class="sxs-lookup"><span data-stu-id="905a5-307">**IP_RAW_RX_NO_HEADER**:  If cleared, the IPv6 header is included with the received data for raw IPv6 sockets created in BSD.</span></span> <span data-ttu-id="905a5-308">BSD の RAW IPv6 ソケット内のIPv6 ヘッダーは既定で削除され、パケット長に IPv6 ヘッダーは含まれません。</span><span class="sxs-lookup"><span data-stu-id="905a5-308">IPv6 headers are removed by default in BSD raw IPv6 sockets, and the packet length does not include the IPv6 header.</span></span>

<span data-ttu-id="905a5-309">設定されている場合、種類が IPv4 である BSD RAW ソケットで受信したデータから、IPv4 ヘッダーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-309">If set, the IPv4 header is removed from received data on BSD raw sockets of type IPv4.</span></span> <span data-ttu-id="905a5-310">IPv4 ヘッダーは、既定では BSD の RAW IPv4 ソケットに含められ、パケット長に IPv4 ヘッダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="905a5-310">IPv4 headers are included by default in BSD raw IPv4 sockets and packet length includes the IPv4 header.</span></span>

<span data-ttu-id="905a5-311">このオプションは、IPv4 や IPv6 のどちらの転送データにも影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="905a5-311">This option has no effect on either IPv4 or IPv6 transmission data.</span></span>

## <a name="small-ipv4-example"></a><span data-ttu-id="905a5-312">小規模な IPv4 の例</span><span class="sxs-lookup"><span data-stu-id="905a5-312">Small IPv4 Example</span></span>

<span data-ttu-id="905a5-313">以下では、IPv4 ネットワークで NetX Duo BSD サービスを使用する方法の例について説明します。</span><span class="sxs-lookup"><span data-stu-id="905a5-313">An example of how to use NetX Duo BSD services for IPv4 networks is described below.</span></span> <span data-ttu-id="905a5-314">この例では、インクルード ファイル *nxd_bsd.h* が 8 行目で組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="905a5-314">In this example, the include file *nxd_bsd.h* is brought in at line 8.</span></span> <span data-ttu-id="905a5-315">次に、IP インスタンス *bsd_ip* とパケット プール *bsd_pool* が、20 行目と 21 行目でグローバル変数として作成されています。</span><span class="sxs-lookup"><span data-stu-id="905a5-315">Next, the IP instance *bsd_ip* and packet pool *bsd_pool* are created as global variables at line 20 and 21.</span></span> <span data-ttu-id="905a5-316">このデモでは、RAM (仮想) ネットワーク ドライバー *_nx_ram_network_driver* を使用していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="905a5-316">Note that this demo uses a ram (virtual) network driver *, _nx_ram_network_driver*.</span></span> <span data-ttu-id="905a5-317">この例では、クライアントとサーバーが 1 つの IP インスタンス上で同じ IP アドレスを共有します。</span><span class="sxs-lookup"><span data-stu-id="905a5-317">The client and server will share the same IP address on single IP instance in this example.</span></span>

<span data-ttu-id="905a5-318">クライアントとサーバーのスレッドは、62 行目と 68 行目で作成されています。</span><span class="sxs-lookup"><span data-stu-id="905a5-318">The client and server threads are created on lines 62 and 68.</span></span> <span data-ttu-id="905a5-319">パケット転送用の BSD パケット プールは、78 行目に作成されて、87 行目で IP インスタンスの作成に使用されています。</span><span class="sxs-lookup"><span data-stu-id="905a5-319">The BSD packet pool for transmitting packets is created on line 78 and used in the IP instance creation on line 87.</span></span> <span data-ttu-id="905a5-320">*nx_ip_create* 呼び出しでは、IP スレッド タスクに優先度 1 が付与されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="905a5-320">Note that the IP thread task is given priority 1 in the *nx_ip_create* call.</span></span> <span data-ttu-id="905a5-321">最適な NetX パフォーマンスを得るためには、プログラムで、このスレッドが最も優先度の高いタスクとして定義されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="905a5-321">This thread should be the highest priority task defined in the program for optimal NetX performance.</span></span>

<span data-ttu-id="905a5-322">IP インスタンスは、ARP サービスと TCP サービスに対して、それぞれ 88 行目と 110 行目で有効にされています。</span><span class="sxs-lookup"><span data-stu-id="905a5-322">The IP instance is enabled for ARP and TCP services on lines 88 and 110 respectively.</span></span> <span data-ttu-id="905a5-323">BSD サービスが使用可能になる前の最後の要件は、120 行目にある、BSD で必要とされるすべてのデータ構造体と NetX および ThreadX のリソースを設定するための、*bsd_initialize* の呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="905a5-323">The last requirement before BSD services can be used is to call *bsd_initialize* on line 120 to set up all data structures and NetX and ThreadX resources needed by BSD.</span></span>

<span data-ttu-id="905a5-324">次に、サーバー スレッドのエントリ関数が定義されています。</span><span class="sxs-lookup"><span data-stu-id="905a5-324">The server thread entry function is defined next.</span></span> <span data-ttu-id="905a5-325">BSD TCP ソケットは、149 行目で作成されています。</span><span class="sxs-lookup"><span data-stu-id="905a5-325">The BSD TCP socket is created on line 149.</span></span> <span data-ttu-id="905a5-326">サーバーの IP アドレスとポートは、160 ～ 163 行目で設定されています。</span><span class="sxs-lookup"><span data-stu-id="905a5-326">The server IP address and port are set on lines 160-163.</span></span> <span data-ttu-id="905a5-327">IP アドレスとポートに適用される、ホスト バイト オーダーからネットワーク バイト オーダーへのマクロ *htonl* および *htons* の使用に注意してください。</span><span class="sxs-lookup"><span data-stu-id="905a5-327">Note the use of host to network byte order macros *htonl* and *htons* applied to the IP address and port.</span></span> <span data-ttu-id="905a5-328">これは、マルチ バイト データはネットワーク バイト オーダーで BSD サービスに送信される BSD ソケット仕様に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="905a5-328">This is in compliance with BSD socket specification that multi byte data is submitted to the BSD services in network byte order.</span></span>

<span data-ttu-id="905a5-329">次に、166 行目では、*bind* サービスを使用して、マスター サーバー ソケットがポートにバインドされています。</span><span class="sxs-lookup"><span data-stu-id="905a5-329">Next, the master server socket is bound to the port using the *bind* service on line 166.</span></span> <span data-ttu-id="905a5-330">これが、180 行目の *listen* サービスを使用した TCP 接続要求のリッスン ソケットです。</span><span class="sxs-lookup"><span data-stu-id="905a5-330">This is the listening socket for TCP connection requests using the *listen* service on line 180.</span></span> <span data-ttu-id="905a5-331">ここから、サーバー スレッド関数 *thread_server_entry* は、202 行目の *select* 呼び出しを使用して、受信イベントの確認をループします。</span><span class="sxs-lookup"><span data-stu-id="905a5-331">From here the server thread function, *thread_server_entry*, loops to check for receive events using the *select* call on line 202.</span></span> <span data-ttu-id="905a5-332">受信イベントが接続要求である場合は (読み取り準備リストの比較によって特定されます)、213 行目で *accept* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="905a5-332">If a receive event is a connection request, which is determined by comparing the read ready list, it calls *accept* on line 213.</span></span> <span data-ttu-id="905a5-333">子サーバー ソケットは、接続要求を処理するために割り当てられ、223 行目のクライアントに接続される TCP サーバー ソケットのマスター リストに追加されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-333">A child server socket is assigned to handle the connection request and added to the master list of TCP server sockets connected to a Client on line 223.</span></span> <span data-ttu-id="905a5-334">新しい接続要求がない場合、サーバー スレッドは次に、236 行目から始まる for ループで、現在接続されているすべてのソケットについて、受信イベントがないか確認します。</span><span class="sxs-lookup"><span data-stu-id="905a5-334">If there are no new connection requests, the server thread then checks all the currently connected sockets for receive events in the for loop starting on line 236.</span></span> <span data-ttu-id="905a5-335">待機中の受信イベントが検出されると、データが受信されなくなり (逆側で接続が閉じた)、277 行目の *soc_close* サービスを使用してソケットが閉じられるまで、そのソケットで *send* と *recv* が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-335">When a receive event waiting is detected, it calls *send* and *recv* on that socket until no data is received (connection closed on the other side) and the socket is closed using the *soc_close* service on line 277.</span></span>

<span data-ttu-id="905a5-336">サーバー スレッドの設定後、クライアント スレッドのエントリ関数 *thread_client_entry* により、326 行目でのソケットの作成と、337 行目での *connect* 呼び出しを使用した TCP サーバー ソケットとの接続が行われます。</span><span class="sxs-lookup"><span data-stu-id="905a5-336">After the server thread sets up, the Client thread entry function, *thread_client_entry,* creates a socket on line 326 and connects with the TCP server socket using the *connect* call on line 337.</span></span> <span data-ttu-id="905a5-337">その後は、パケットの送信と受信のループを、それぞれ *send* サービスと *recv* サービスを使用して行います。</span><span class="sxs-lookup"><span data-stu-id="905a5-337">It then loops to send and receive packets using the *send* and *recv* services respectively.</span></span> <span data-ttu-id="905a5-338">それ以上データを受信しないときには、398 行目で、*soc_close* サービスを使用してソケットが閉じられます。</span><span class="sxs-lookup"><span data-stu-id="905a5-338">When no more data is received, it closes the socket on line 398 using the *soc_close* service.</span></span> <span data-ttu-id="905a5-339">接続の切断後、クライアント スレッドのエントリ関数によって、新しい TCP ソケットが作成され、321 行目で開始される while ループ内で別の接続要求が作成されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-339">After disconnection, the client thread entry function creates a new TCP socket and makes another connection request in the while loop started on line 321.</span></span>

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection, sending,
and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQR
    STUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */

ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */

VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */
int     main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{
CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool", 128,
                                pointer, 16384);

    pointer = pointer + 16384;
    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                    0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                    pointer, 2048, 1);
                    pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable ARP \n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize (&bsd_ip, &bsd_pool,pointer, 2048, 2);
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT       status, sock, sock_tcp_server;
ULONG     actual_status;
INT       Clientlen;
INT       i;
UINT      is_set = NX_FALSE;
struct    sockaddr_in serverAddr;
struct    sockaddr_in ClientAddr;

    tx_thread_sleep(100);

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
        &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("Error on Server socket %d create \n", sock_tcp_server);
        return;
    }

    printf("Server socket %d created\n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin_family = AF_INET;
    serverAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    serverAddr.sin_port = htons(SERVER_PORT);

    /* Bind this server socket */
    status = bind (sock_tcp_server, (struct sockaddr *) &serverAddr,
                sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error on Server Socket %d Bind \n", sock_tcp_server);
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen (sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error on Server Socket %d Listen\n", sock_tcp_server);
        return;
    }
    else
        printf("Server socket %d listen complete\n", sock_tcp_server);

    /* All set to accept client connections */

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ((status == 0xFFFFFFFF) || (status == 0))
        {

            printf("Error with select. Status 0x%x\n", status);

            continue;
        }

        /* Check for a connection request. */
        is_set = FD_ISSET(sock_tcp_server, &read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,(struct sockaddr*)&ClientAddr,
                        &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i , &master_list)) &&
                (FD_ISSET(i , &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server received no data from Client on
                            socket %d)\n", i);
                        break;
                    }
                    else if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server receiving data from Client on
                            socket %d\n", i);
                        break;
                    }
                    if(status == SERVER_RCV_BUFFER_SIZE) status--;
                    Server_Rcv_Buffer[status] = 0;
                    printf("Server socket %d received %d bytes: %s\n ",
                            i, (ULONG)status, Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                        Client\n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                        Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != NX_SOC_ERROR)
                {
                    printf("Server socket %d closed \n", i);
                }
                else
                {
                    printf("Error on closing Server socket %d \n", i);
                }
            }
        }

    /* Loop back to check any next client connection */
    }
}

CHAR     Client_Rcv_Buffer[100];

VOID     thread_client_entry(ULONG thread_input)
{

INT        status;
INT        sock_tcp_client, length;
struct     sockaddr_in echoServAddr;
struct     sockaddr_in localAddr; /

    /* Let the server side get set up. */
    tx_thread_sleep(200);

    /* Set local port for displaying IP address and port. */
    memset(&localAddr, 0, sizeof(localAddr));
    localAddr.sin_family = AF_INET;
    localAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    localAddr.sin_port = htons(CLIENT_PORT);

    /* Set server port and IP address which we need to connect. */
    memset(&echoServAddr, 0, sizeof(echoServAddr));
    echoServAddr.sin_family = AF_INET;
    echoServAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    echoServAddr.sin_port = htons(SERVER_PORT);

    /* Now make client connections with the server. */
    while (1)
    {

        printf("\n");

        /* Create BSD TCP Socket */
        sock_tcp_client = socket( AF_INET, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n", sock_tcp_client);
            return;
        }

        printf("Client socket %d created\n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr,
                        sizeof(echoServAddr));

        /* Check for error. */
        if (status != OK)
        {
            printf("Error on Client socket %d connect\n", sock_tcp_client);
                    soc_close(sock_tcp_client);
            return;
        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr,
                            &length);

        printf("Client port = %lu , Client = 0x%x,",
            htonl(localAddr.sin_port), htonl(localAddr.sin_addr.s_addr));

        length = sizeof(struct sockaddr_in);

        status = getpeername( sock_tcp_client, (struct sockaddr *)
                            &echoServAddr, &length);

        printf("Remote port = %lu, Remote IP = 0x%x \n",
                htonl(echoServAddr.sin_port),
                htonl(echoServAddr.sin_addr.s_addr));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
            sock_tcp_client);

            status = send(sock_tcp_client, "Hello", (sizeof("Hello")), 0);

            if (status == ERROR)
            {
                printf("Error: Client Socket (%d) send \n", sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,100,0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    380 printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Nothing received by Client on socket %d\n",
                            sock_tcp_client);
                }

                break;
            }
            else
            {
                printf("Client socket %d received %d bytes: %s\n",
                        sock_tcp_client,
                        status, Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = soc_close(sock_tcp_client);

        if (status != ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```

## <a name="small-ipv6-example-system"></a><span data-ttu-id="905a5-340">小規模な IPv6 システムの例</span><span class="sxs-lookup"><span data-stu-id="905a5-340">Small IPv6 Example System</span></span>

<span data-ttu-id="905a5-341">IPv6 ネットワークで NetX Duo BSD サービスを使用する方法の例を、下記のプログラムで説明します。</span><span class="sxs-lookup"><span data-stu-id="905a5-341">An example of how to use NetX Duo BSD services for IPv6 networks is described in the program below.</span></span> <span data-ttu-id="905a5-342">この例は、前に説明した IPv4 デモ プログラムによく似ていますが、重要な違いがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="905a5-342">This example is very similar to the IPv4 demo program previously described with a few important differences.</span></span>

<span data-ttu-id="905a5-343">クライアントとサーバーのスレッド、BSD パケット プール、IP インスタンス、および BSD の初期化は、IPv4 BSD ソケットの場合と同様に行われます。</span><span class="sxs-lookup"><span data-stu-id="905a5-343">The client and server threads, BSD packet pool, IP instance and BSD initialization happens as it does for IPv4 BSD sockets.</span></span>

<span data-ttu-id="905a5-344">サーバー スレッド エントリ関数 *thread_server_entry* では、145 ～ 148 行で *sockaddr_in6* および *NXD_ADDRESS* データ型を使用して一対の IPv6 変数を定義しています。</span><span class="sxs-lookup"><span data-stu-id="905a5-344">In the server thread entry function, *thread_server_entry*, defines a couple IPv6 variables using *sockaddr_in6* and *NXD_ADDRESS* data types on lines 145-148.</span></span> <span data-ttu-id="905a5-345">実際には、NXD_ADDRESS データ型には IPv4 と IPv6 の両方の種類のアドレスを格納できます。</span><span class="sxs-lookup"><span data-stu-id="905a5-345">The NXD_ADDRESS data type can actually store both IPv4 and IPv6 address types.</span></span>

<span data-ttu-id="905a5-346">次に、サーバー スレッドにより、IP インスタンスでの IPv6 と ICMPv6 がそれぞれ 161 行目と 169 行目で、*nxd_ipv6_enable* および *nxd_icmpv6_enable* サービスを使用して有効にされています。</span><span class="sxs-lookup"><span data-stu-id="905a5-346">Next, the server thread enables IPv6 and ICMPv6 on the IP instance using the *nxd_ipv6_enable* and *nxd_icmpv6_enable* service respectively on line 161 and 169.</span></span> <span data-ttu-id="905a5-347">次に、その IP インスタンスに、リンク ローカルとグローバルの IP アドレスが登録されます。</span><span class="sxs-lookup"><span data-stu-id="905a5-347">Next, the link local and global IP addresses are registered with the IP instance.</span></span> <span data-ttu-id="905a5-348">これは、180 行目と 195 行目で *nxd_ipv6_address_set* サービスを使用して行われています。</span><span class="sxs-lookup"><span data-stu-id="905a5-348">This is done using the *nxd_ipv6_address_set* service on lines 180 and 195.</span></span> <span data-ttu-id="905a5-349">次に、IP スレッドのタスクが重複アドレス検出プロトコルを完了するのに十分な時間スリープ状態になり、201 行目の *tx_thread_sleep* の呼び出しで、これらのアドレスを有効なアドレスとして登録しています。</span><span class="sxs-lookup"><span data-stu-id="905a5-349">It then sleeps long enough for the IP thread task to complete the Duplicate Address Detection protocol and register these addresses as valid addresses on the *tx_thread_sleep* call on line 201.</span></span>

<span data-ttu-id="905a5-350">次に 204 行目で、ソケットの種類の入力引数として AF_INET6 を指定して、TCP サーバー ソケットを作成しています。</span><span class="sxs-lookup"><span data-stu-id="905a5-350">Next, the TCP server socket is created with the AF_INET6 socket type input argument on line 204.</span></span> <span data-ttu-id="905a5-351">ソケットの IPv6 アドレスとポートは 216 ～ 221 行目で設定されています。この場合も、BSD ソケット サービスにはネットワーク バイト オーダーでデータを提供するため、*htonl* マクロと *htons* マクロを使用していることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="905a5-351">The socket IPv6 address and port are set on lines 216-221, again noting the use of *htonl* and *htons* macros to put data in network byte order for BSD socket services.</span></span> <span data-ttu-id="905a5-352">ここからは、このサーバー スレッド エントリ関数は、IPv4 の例と事実上同じです。</span><span class="sxs-lookup"><span data-stu-id="905a5-352">From here on, the server thread entry function is virtually identical to the IPv4 example.</span></span>

<span data-ttu-id="905a5-353">次に、クライアント スレッド エントリ関数 *thread_client_entry* が定義されています。</span><span class="sxs-lookup"><span data-stu-id="905a5-353">The client thread entry function, *thread_client_entry*, is defined next.</span></span> <span data-ttu-id="905a5-354">この例の TCP クライアントは、TCP サーバーと同じ IP インスタンスおよび IPv6 アドレスを共有するため、IP インスタンスでもう一度 IPv6 サービスや ICMPv6 サービスを有効にする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="905a5-354">Note that because the TCP client in this example shares the same IP instance and IPv6 address as the TCP server, we do not need to enable IPv6 or ICMPv6 services on the IP instance again.</span></span> <span data-ttu-id="905a5-355">さらに、この IPv6 アドレスも既に、IP インスタンスに登録されています。</span><span class="sxs-lookup"><span data-stu-id="905a5-355">Further, the IPv6 address is also already registered with the IP instance.</span></span> <span data-ttu-id="905a5-356">そうしないで、クライアント スレッド エントリ関数は単純に、368 行目でサーバーが設定されるのを待機しています。</span><span class="sxs-lookup"><span data-stu-id="905a5-356">Instead, the client thread entry function simply waits on line 368 for the server to set up.</span></span> <span data-ttu-id="905a5-357">387 ～ 392 行目でホスト バイト オーダーからネットワーク バイト オーダーへのマクロを使用して、サーバーのアドレスとポートが設定された後、クライアントは 412 行目で、TCP サーバーに接続することができます。</span><span class="sxs-lookup"><span data-stu-id="905a5-357">The server address and port are set, using the host to network byte order macros on lines 387-392, and then the Client can connect with the TCP server on line 412.</span></span> <span data-ttu-id="905a5-358">378 ～ 383 行目のローカル IP アドレスのデータ型は、それぞれ 425 行目と 434 行目の *getsockname* サービスと *getpeername* サービスを示すためにのみ使用されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="905a5-358">Note that the local IP address data types in lines 378-383 are used only to demonstrate the *getsockname* and *getpeername* services on lines 425 and 434 respectively.</span></span> <span data-ttu-id="905a5-359">データはネットワークから着信するため、378 ～ 383 行目で、ネットワーク バイト オーダーからホスト バイト オーダーへのマクロが使用されています。</span><span class="sxs-lookup"><span data-stu-id="905a5-359">Because the data is coming from the network, the network to host byte order macros as used in lines 378-383.</span></span>

<span data-ttu-id="905a5-360">次に、クライアント スレッド エントリ関数はループに入り、そこで、それ以上データが受信されなくなるまで TCP ソケットの作成、TCP 接続の作成、TCP サーバーとのデータの送受信を行います。これは事実上、IPv4 の例と同じです。</span><span class="sxs-lookup"><span data-stu-id="905a5-360">Next the client thread entry function enters a loop in which it creates a TCP socket, makes a TCP connection and sends and receives data with the TCP server until no more data is received virtually the same as the IPv4 example.</span></span> <span data-ttu-id="905a5-361">次に、483 行目でソケットを閉じ、短時間一時停止して別の TCP ソケットを作成し、TCP サーバー接続を要求します。</span><span class="sxs-lookup"><span data-stu-id="905a5-361">It then closes the socket on line 483, pauses briefly and creates another TCP socket and requests a TCP server connection.</span></span>

<span data-ttu-id="905a5-362">IPv4 の例との重要な違いの 1 つは、*socket* 呼び出しで、入力引数として AF_INET6 を使用して IPv6 ソケットを指定することです。</span><span class="sxs-lookup"><span data-stu-id="905a5-362">One important difference with the IPv4 example is the *socket* calls specify an IPv6 socket using the AF_INET6 input argument.</span></span> <span data-ttu-id="905a5-363">もう 1 つの重要な違いは、TCP クライアントの *connect* 呼び出しでは、*sockaddr_in6* データ型と、*sockaddr_in6* データ型のサイズに設定された長さの引数を取ることです。</span><span class="sxs-lookup"><span data-stu-id="905a5-363">Another important difference is that the TCP Client *connect* call takes an *sockaddr_in6* data type and a length argument set to the size of the *sockaddr_in6* data type.</span></span>

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection,
disconnection, sending, and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */
ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */
VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

int     main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{
CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool",
    128, pointer, 16384);

    pointer = pointer + 16384;

    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                        0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in enable ARP on BSD IP instance\n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 2);

    /* Check BSD initialize status. */
    if (status)
    {
        error_counter++;
        printf("Error in BSD initialize \n");
    }

    pointer = pointer + 2048;
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT             status, sock, sock_tcp_server;
ULONG           actual_status;
INT             Clientlen;
INT             i;
UINT            is_set = NX_FALSE;
NXD_ADDRESS     ip_address;
struct          sockaddr_in6 serverAddr;
struct          sockaddr_in6 ClientAddr;
UINT            iface_index, address_index;

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
            &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 */
    status = nxd_ipv6_enable(&bsd_ip);
    if((status != NX_SUCCESS) && (status != NX_ALREADY_ENABLED))
    {
        printf("Error with IPv6 enable 0x%x\n", status);
        return;
    }

    /* Enable ICMPv6 */
    status = nxd_icmp_enable(&bsd_ip);

    if(status)
    {
        printf("Error with ECMPv6 enable 0x%x\n", status);
        return;
    }

    /* Set the primary interface for our DNS IPv6 addresses. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, NX_NULL, 10,
                                &address_index);

    if (status)
        return;

    /* Set ip_0 interface address. */
    ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    ip_address.nxd_ip_address.v6[0] = htonl(0x20010db8);
    ip_address.nxd_ip_address.v6[1] = htonl(0x0000f101);
    ip_address.nxd_ip_address.v6[2] = 0;
    ip_address.nxd_ip_address.v6[3] = htonl(0x101);

    /* Set the host global IP address. We are assuming a 64
    bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, &ip_address, 64,
                                &address_index);

    if (status)
        return;

    /* Wait for IPv6 stack to finish DAD process. */
    tx_thread_sleep(400);

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET6, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("\nError: BSD TCP Server socket create \n");
        return;
    }

    printf("\nBSD TCP Server socket created %lu \n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    serverAddr.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    serverAddr.sin6_addr._S6_un._S6_u32[2] = 0x0;
    serverAddr.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    serverAddr.sin6_port = htons(SERVER_PORT);
    serverAddr.sin6_family = AF_INET6;

    /* Bind this server socket */
    status = bind(sock_tcp_server, (struct sockaddr *) &serverAddr,
                    sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error: Server Socket Bind \n");
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen(sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error: Server Socket Listen\n");
        return;
    }
    else
        printf("Server Listen complete\n");

    /* All set to accept client connections */
    printf("Now accepting client connections\n");

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ( (status == 0xFFFFFFFF) || (status == 0) )
        {
            printf("Error with select? Status 0x%x. Try again\n", status);

            continue;
        }

        /* Detected a connection request. */
        is_set = FD_ISSET(sock_tcp_server,&read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,
            (struct sockaddr*)&ClientAddr,
            &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {
                printf("New connection %d\n", sock);

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i, &master_list)) &&
                (FD_ISSET(i, &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server socket %d received no data from
                                Client)\n", i);

                        break;
                    }
                    else if (status == 0xFFFFFFFF)
                    {
                        printf("Error on Server socket %d receiving data from
                                Client\n", i);

                        break;
                    }

                    printf("Server socket %d received from Client %lu bytes:
                            %s\n ", i, (ULONG)status,
                            Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                                Client \n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                                Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != ERROR)
                {
                    printf("Server socket %d closing\n", i);
                }
                else
                {

                    printf("Error on Server socket %d closing\n", i);
                }
            }
        }

        /* Loop back to check any next client connection */
    }
}

#define     CLIENT_BUFFER_SIZE 100
CHAR        Client_Rcv_Buffer[CLIENT_BUFFER_SIZE];

VOID        thread_client_entry(ULONG thread_input)
{

INT         status;
INT         sock_tcp_client, length;
struct      sockaddr_in6 echoServAddr6;
struct      sockaddr_in6 localAddr6; address */

    /* Wait for the server side to get set up, including the DAD process. */
    tx_thread_sleep(500);

    /* ICMPv6 and IPv6 should already be enabled on the IP instance
    by the server thread entry function. */

    /* Further the IPv6 address is already established with the IP instance.
    so no need to wait for DAD completion. */

    /* Set local port and IP address (used only for getsockname call). */
    memset(&localAddr6, 0, sizeof(localAddr6));
    localAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    localAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    localAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    localAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    localAddr6.sin6_port = htons(CLIENT_PORT);
    localAddr6.sin6_family = AF_INET6;

    /* Set Server port and IP address to connect to the TCP server. */
    memset(&echoServAddr6, 0, sizeof(echoServAddr6));
    echoServAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    echoServAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    echoServAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    echoServAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    echoServAddr6.sin6_port = htons(SERVER_PORT);
    echoServAddr6.sin6_family = AF_INET6;

    /* Now make client connections with the server. */
    while (1)
    {
        printf("\n");

        /* Create BSD TCP Socket */

        sock_tcp_client = socket(AF_INET6, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n");
            return;
        }

        printf("Client socket %d created \n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr6,
                sizeof(echoServAddr6));

        /* Check for error. */
        if (status != NX_SOC_OK)
        {
            printf("Error on Client socket %d connect\n");
            soc_close(sock_tcp_client);
            return;

        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr6,
        &length);

        printf("Client port = %lu , Client = 0x%x 0x%x 0x%x 0x%x,",
                ntohs(localAddr6.sin6_port),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[3]));

        length = sizeof(struct sockaddr_in6);

        status = getpeername(sock_tcp_client, (struct sockaddr *)
                            &echoServAddr6, &length);

        printf("Remote port = %lu, Remote IP = 0x%x 0x%x 0x%x 0x%x \n",
                ntohs(echoServAddr6.sin6_port),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[3]));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
                sock_tcp_client);

            status = send(sock_tcp_client, "Hello", sizeof("Hello"), 0);

            if (status == NX_SOC_ERROR)
            {
                printf("Error on Client Socket (%d) send \n",
                        sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message: Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,
                        CLIENT_BUFFER_SIZE, 0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Client received no data on socket %d\n",
                            sock_tcp_client);
                }

            break;
            }
            else
            {
                printf("Client socket %d received %d bytes and this message:
                        %s\n", sock_tcp_client, status,
                        Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = oc_close(sock_tcp_client);

        if (status != NX_SOC_ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```
