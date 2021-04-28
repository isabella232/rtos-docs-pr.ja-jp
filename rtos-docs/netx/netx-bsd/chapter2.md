---
title: 第 2 章 - Azure RTOS NetX BSD のインストールと使用
description: この章では、Azure RTOS NetX BSD コンポーネントのインストール、設定、使用に関連したさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7539565ccd4956c5354be45000efab8318dc606c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811660"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-bsd"></a><span data-ttu-id="69bb9-103">第 2 章 - Azure RTOS NetX BSD のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="69bb9-103">Chapter 2 - Installation and Use of Azure RTOS NetX BSD</span></span>

<span data-ttu-id="69bb9-104">この章では、Azure RTOS NetX BSD コンポーネントのインストール、設定、使用に関連したさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX BSD component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="69bb9-105">製品の配布</span><span class="sxs-lookup"><span data-stu-id="69bb9-105">Product Distribution</span></span>

<span data-ttu-id="69bb9-106">Azure RTOS NetX BSD は、[https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) のパブリック ソース コード リポジトリから入手できます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-106">Azure RTOS NetX BSD can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="69bb9-107">このパッケージには、次のように 2 つのソース ファイルと、このドキュメントを含む PDF ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="69bb9-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="69bb9-108">**nx_bsd.h**: NetX BSD のヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="69bb9-108">**nx_bsd.h**: Header file for NetX BSD</span></span>
- <span data-ttu-id="69bb9-109">**nx_bsd.c**: NetX BSD の C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="69bb9-109">**nx_bsd.c**: C Source file for NetX BSD</span></span>
- <span data-ttu-id="69bb9-110">**nx_bsd.pdf**: NetX BSD のユーザー ガイド</span><span class="sxs-lookup"><span data-stu-id="69bb9-110">**nx_bsd.pdf**: User Guide for NetX BSD</span></span>

<span data-ttu-id="69bb9-111">デモ ファイル:</span><span class="sxs-lookup"><span data-stu-id="69bb9-111">Demo files:</span></span>
- <span data-ttu-id="69bb9-112">**bsd_demo_tcp.c**</span><span class="sxs-lookup"><span data-stu-id="69bb9-112">**bsd_demo_tcp.c**</span></span>
- <span data-ttu-id="69bb9-113">**bsd_demo_udp.c**</span><span class="sxs-lookup"><span data-stu-id="69bb9-113">**bsd_demo_udp.c**</span></span>

## <a name="netx-bsd-installation"></a><span data-ttu-id="69bb9-114">NetX BSD のインストール</span><span class="sxs-lookup"><span data-stu-id="69bb9-114">NetX BSD Installation</span></span>

<span data-ttu-id="69bb9-115">NetX BSD を使用するには、先に説明したディストリビューション全体を NetX がインストールされているのと同じディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-115">In order to use NetX BSD the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="69bb9-116">たとえば、NetX がディレクトリ " *\threadx\arm7\green*" にインストールされている場合は、*nx_bsd.h* および *nx_bsd.c* ファイルをこのディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-116">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_bsd.h* and *nx_bsd.c* files should be copied into this directory.</span></span>

## <a name="building-the-threadx-and-netx-components-of-a-bsd-application"></a><span data-ttu-id="69bb9-117">BSD アプリケーションの ThreadX および NetX コンポーネントの構築</span><span class="sxs-lookup"><span data-stu-id="69bb9-117">Building the ThreadX and NetX components of a BSD Application</span></span>

### <a name="threadx"></a><span data-ttu-id="69bb9-118">ThreadX</span><span class="sxs-lookup"><span data-stu-id="69bb9-118">ThreadX</span></span>

<span data-ttu-id="69bb9-119">ThreadX ライブラリでは、スレッド ローカル ストレージ内に *bsd_errno* を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-119">The ThreadX library must define *bsd_errno* in the thread local storage.</span></span> <span data-ttu-id="69bb9-120">次の手順をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="69bb9-120">We recommend the following procedure:</span></span>

1. <span data-ttu-id="69bb9-121">*tx_port.h* で、次のようにいずれかの TX_THREAD_EXTENSION マクロを設定します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-121">In *tx_port.h*, set one of the TX_THREAD_EXTENSION macros as follows:</span></span>

  ```c
  #define TX_THREAD_EXTENSION_3     int bsd_errno
  ```

2. <span data-ttu-id="69bb9-122">ThreadX ライブラリをリビルドします。</span><span class="sxs-lookup"><span data-stu-id="69bb9-122">Rebuild the ThreadX library.</span></span>

> [!NOTE]
> <span data-ttu-id="69bb9-123">TX_THREAD_EXTENSION_3 が既に使用されている場合、ユーザーは、他の TX_THREAD_EXTENSION マクロのいずれかを自由に使用できます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-123">If TX_THREAD_EXTENSION_3 is already used, the user is free to use one of the other TX_THREAD_EXTENSION macros.</span></span>

### <a name="netx"></a><span data-ttu-id="69bb9-124">NetX</span><span class="sxs-lookup"><span data-stu-id="69bb9-124">NetX</span></span>

<span data-ttu-id="69bb9-125">NetX BSD サービスを使用する前に、NetX ライブラリを NX_ENABLE_EXTENDED_NOTIFY_SUPPORT が (たとえば、*nx_user.h* 内に) 定義された状態で構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-125">Before using NetX BSD Services, the NetX library must be built with NX_ENABLE_EXTENDED_NOTIFY_SUPPORT defined (e.g. in *nx_user.h*).</span></span> <span data-ttu-id="69bb9-126">これは、既定では定義されていません。</span><span class="sxs-lookup"><span data-stu-id="69bb9-126">By default it is not defined.</span></span>

## <a name="using-netx-bsd"></a><span data-ttu-id="69bb9-127">NetX BSD の使用</span><span class="sxs-lookup"><span data-stu-id="69bb9-127">Using NetX BSD</span></span>

<span data-ttu-id="69bb9-128">NetX 用の BSD の使用は簡単です。</span><span class="sxs-lookup"><span data-stu-id="69bb9-128">Using BSD for NetX is easy.</span></span> <span data-ttu-id="69bb9-129">基本的に、ThreadX と NetX を使用するには、アプリケーション コードに、それぞれ *tx_api.h* と *nx_api.h* をインクルードした後に *nx_bsd.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-129">Basically, the application code must include *nx_bsd.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="69bb9-130">*nx_bsd.h* がインクルードされると、アプリケーション コードは、このガイドの後の方で指定されている BSD サービスを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-130">Once *nx_bsd.h* is included, the application code is then able to use the BSD services specified later in this guide.</span></span> <span data-ttu-id="69bb9-131">アプリケーションのビルド プロセスでは *nx_bsd.c* も含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-131">The application must also include *nx_bsd.c* in the build process.</span></span> <span data-ttu-id="69bb9-132">このファイルは、他のアプリケーション ファイルと同様にコンパイルする必要があり、そのオブジェクト形式は、アプリケーションのファイルと一緒にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-132">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="69bb9-133">NetX BSD を使用するために必要なことはこれだけです。</span><span class="sxs-lookup"><span data-stu-id="69bb9-133">This is all that is required to use NetX BSD.</span></span>

<span data-ttu-id="69bb9-134">NetX BSD サービスを利用するには、アプリケーションで IP インスタンスとパケット プールを作成し、*bsd_initialize* を呼び出して BSD サービスを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-134">To utilize NetX BSD services, the application must create an IP instance, a packet pool, and initialize BSD services by calling *bsd_initialize.*</span></span> <span data-ttu-id="69bb9-135">これは、このガイドの後の方の "小さな例" のセクションで示されています。</span><span class="sxs-lookup"><span data-stu-id="69bb9-135">This is demonstrated in the "Small Example" section later in this guide.</span></span> <span data-ttu-id="69bb9-136">このプロトタイプを次に示します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-136">The prototype is shown below:</span></span>

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                  CHAR *free_memory_ptr, ULONG bsd_thread_stack_size,
                  UINT bsd_thread_priority);
```

<span data-ttu-id="69bb9-137">最後の 3 つのパラメーターは、定期的なタスク (TCP イベントのチェックなど) を実行するためのスレッドを作成するために使用され、スレッド スタック領域を定義します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-137">The last three parameters are used for creating a thread for performing periodic tasks such as checking for TCP events and define the thread stack space.</span></span>

> [!NOTE]
> <span data-ttu-id="69bb9-138">ネットワークのバイト順で動作する BSD ソケットとは対照的に、NetX は、ホスト プロセッサのホストのバイト順で動作します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-138">In contrast to BSD sockets, which work in network bye order, NetX works in the host byte order of the host processor.</span></span> <span data-ttu-id="69bb9-139">ソースの互換性の理由から、マクロ htons()、ntohs()、htonl()、ntohl() は定義されていますが、渡された引数を変更することはありません。</span><span class="sxs-lookup"><span data-stu-id="69bb9-139">For source compatibility reasons, the macros htons(), ntohs(), htonl(), ntohl() have been defined, but do not modify the argument passed.</span></span>

## <a name="netx-bsd-limitations"></a><span data-ttu-id="69bb9-140">NetX BSD の制限事項</span><span class="sxs-lookup"><span data-stu-id="69bb9-140">NetX BSD Limitations</span></span>

<span data-ttu-id="69bb9-141">パフォーマンスやアーキテクチャの問題のために、NetX BSD では、BSD 4.3 ソケット機能のすべてはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="69bb9-141">Due to performance and architecture issues, NetX BSD does not support all the BSD 4.3 socket features:</span></span>

<span data-ttu-id="69bb9-142">INT フラグは、*send、recv、sendto*、*recvfrom* の呼び出しではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="69bb9-142">INT flags are not supported for *send, recv, sendto* and *recvfrom* calls.</span></span>

## <a name="netx-bsd-with-dns-support"></a><span data-ttu-id="69bb9-143">NetX BSD での DNS サポート</span><span class="sxs-lookup"><span data-stu-id="69bb9-143">NetX BSD with DNS Support</span></span>

<span data-ttu-id="69bb9-144">NX_BSD_ENABLE_DNS が定義されている場合、NetX BSD では、ホスト名またはホスト IP の情報を取得するために DNS クエリを送信できます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-144">If NX_BSD_ENABLE_DNS is defined, NetX BSD can send DNS queries to obtain hostname or host IP information.</span></span> <span data-ttu-id="69bb9-145">この機能では、*nx_dns_create* サービスを使用して、NetX DNS クライアントを事前に作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-145">This feature requires a NetX DNS Client to be previously created using the *nx_dns_create* service.</span></span> <span data-ttu-id="69bb9-146">1 つ以上の既知の DNS サーバー IP アドレスが、サーバー アドレスを追加するための *nx_dns_server_add* を使用して DNS インスタンスに登録されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-146">One or more known DNS server IP addresses must be registered with the DNS instance using the *nx_dns_server_add* for adding server addresses.</span></span>

<span data-ttu-id="69bb9-147">DNS のサービスとメモリ割り当ては、*getaddrinfo* および *getnameinfo* サービスによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-147">DNS services and memory allocation are used by *getaddrinfo* and *getnameinfo* services:</span></span>

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
              const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
              char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

<span data-ttu-id="69bb9-148">BSD アプリケーションがホスト名を使用して *getaddrinfo* を呼び出すと、NetX BSD では、以下のいずれかのサービスを呼び出して IP アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-148">When the BSD application calls *getaddrinfo* with a hostname, NetX BSD will call any of the below services to obtain the IP address:</span></span>

- <span data-ttu-id="69bb9-149">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="69bb9-149">nx_dns_ipv4_address_by_name_get</span></span>
- <span data-ttu-id="69bb9-150">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="69bb9-150">nx_dns_cname_get</span></span>

<span data-ttu-id="69bb9-151">*nx_dns_ipv4_address_by_name_get* の場合、NetX BSD では ipv4_addr_buffer メモリ領域を使用します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-151">For *nx_dns_ipv4_address_by_name_get*, NetX BSD uses the ipv4_addr_buffer memory areas.</span></span> <span data-ttu-id="69bb9-152">これらのバッファーのサイズは (`NX_BSD_IPV4_ADDR_PER_HOST * 4`) によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-152">The size of these buffers are defined by (`NX_BSD_IPV4_ADDR_PER_HOST * 4`).</span></span>

<span data-ttu-id="69bb9-153">*getaddrinfo* からのアドレス情報を返すために、NetX BSD では、ThreadX ブロック メモリ テーブル *nx_bsd_addrinfo_pool_memory* を使用します。このメモリ領域は、構成可能なオプションの別のセットである *NX_BSD_IPV4_ADDR_MAX_NUM* によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-153">For returning address information from *getaddrinfo*, NetX BSD uses the ThreadX block memory table *nx_bsd_addrinfo_pool_memory*, whose memory area is defined by another set of configurable options, *NX_BSD_IPV4_ADDR_MAX_NUM*.</span></span>

<span data-ttu-id="69bb9-154">上記の構成オプションの詳細については、「**構成オプション**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69bb9-154">See **Configuration Options** for more details on the above configuration options.</span></span>

<span data-ttu-id="69bb9-155">さらに、NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されており、ホスト入力が正規名である場合、NetX BSD では、以前に作成されたブロック プール *_nx_bsd_cname_block_pool* からメモリを動的に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-155">Additionally, if NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, and the host input is a canonical name, NetX BSD will allocate memory dynamically from a previously created block pool *_nx_bsd_cname_block_pool*</span></span>

> [!NOTE]
> <span data-ttu-id="69bb9-156">*getaddrinfo* の呼び出し後、*freeaddrinfo* サービスを使用して、res 引数によって指し示されたメモリを解放してブロック テーブルに戻す処理は、BSD アプリケーションで行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-156">After calling *getaddrinfo* the BSD application is responsible for releasing the memory pointed to by the res argument back to the block table using the *freeaddrinfo* service.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="69bb9-157">構成オプション</span><span class="sxs-lookup"><span data-stu-id="69bb9-157">Configuration Options</span></span>

<span data-ttu-id="69bb9-158">*nx_bsd.h* 内のユーザーが構成可能なオプションを使用すると、アプリケーションでは、その特定の要件に合わせて NetX BSD ソケットを微調整できます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-158">User configurable options in *nx_bsd.h* allow the application to fine tune NetX BSD sockets for its particular requirements.</span></span> <span data-ttu-id="69bb9-159">これらのパラメーターの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-159">The following is a list of these parameters:</span></span>

- <span data-ttu-id="69bb9-160">**NX_BSD_TCP_WINDOW**: TCP ソケットの作成呼び出しで使用されます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-160">**NX_BSD_TCP_WINDOW**: Used in TCP socket create calls.</span></span> <span data-ttu-id="69bb9-161">65535 が 100Mb イーサネットでの標準的なウィンドウ サイズです。</span><span class="sxs-lookup"><span data-stu-id="69bb9-161">65535 is a typical window size for 100Mb Ethernet.</span></span> <span data-ttu-id="69bb9-162">既定値は、65535 です。</span><span class="sxs-lookup"><span data-stu-id="69bb9-162">The default value is 65535.</span></span>
- <span data-ttu-id="69bb9-163">**NX_BSD_SOCKFD_START** これは、BSD ソケットのファイル記述子の開始値に対する論理インデックスです。</span><span class="sxs-lookup"><span data-stu-id="69bb9-163">**NX_BSD_SOCKFD_START** This is the logical index for the BSD socket file descriptor start value.</span></span> <span data-ttu-id="69bb9-164">既定では、このオプションは 32 です。</span><span class="sxs-lookup"><span data-stu-id="69bb9-164">By default this option is 32.</span></span>
- <span data-ttu-id="69bb9-165">**NX_BSD_MAX_SOCKETS** BSD レイヤーで使用可能な合計ソケットの最大数を指定するものであり、32 の倍数である必要があります。この値は、既定で 32 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="69bb9-165">**NX_BSD_MAX_SOCKETS** Specifies the maximum number of total sockets available in the BSD layer and must be a multiple of 32.The value is defaulted to 32.</span></span>
- <span data-ttu-id="69bb9-166">**NX_BSD_SOCKET_QUEUE_MAX** 受信ソケット キューに格納される UDP パケットの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-166">**NX_BSD_SOCKET_QUEUE_MAX** Specifies the maximum number of UDP packets stored on the receive socket queue.</span></span> <span data-ttu-id="69bb9-167">この値は、既定で 5 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="69bb9-167">The value is defaulted to 5.</span></span>
- <span data-ttu-id="69bb9-168">**NX_BSD_MAX_LISTEN_BACKLOG** これは、BSD TCP ソケットのリッスン キュー ('バックログ') のサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-168">**NX_BSD_MAX_LISTEN_BACKLOG** This specifies the size of the listen queue ('backlog') for BSD TCP sockets.</span></span> <span data-ttu-id="69bb9-169">既定値は 5 です。</span><span class="sxs-lookup"><span data-stu-id="69bb9-169">The default value is 5.</span></span>
- <span data-ttu-id="69bb9-170">**NX_MICROSECOND_PER_CPU_TICK** タイマー割り込みあたりのマイクロ秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-170">**NX_MICROSECOND_PER_CPU_TICK** Specifies the number of microseconds per timer interrupt</span></span>
- <span data-ttu-id="69bb9-171">**NX_BSD_TIMEOUT** BSD に必要な NetX の内部呼び出しでのタイマー刻み単位のタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-171">**NX_BSD_TIMEOUT** Specifies the timeout in timer ticks on NetX internal calls required by BSD.</span></span> <span data-ttu-id="69bb9-172">既定値は 20\*NX_IP_PERIODIC_RATE です。</span><span class="sxs-lookup"><span data-stu-id="69bb9-172">The default value is 20\*NX_IP_PERIODIC_RATE.</span></span>
- <span data-ttu-id="69bb9-173">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: NetX の切断呼び出しでのタイマー刻み単位のタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-173">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: Specifies the timeout in timer ticks on NetX disconnect call.</span></span> <span data-ttu-id="69bb9-174">既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="69bb9-174">The default value is 1.</span></span>
- <span data-ttu-id="69bb9-175">**NX_BSD_PRINT_ERRORS** 設定されている場合は、BSD 関数のエラー状態の戻り値によって、エラーが発生した行番号とエラーの種類 (NX_SOC_ERROR など) が返されます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-175">**NX_BSD_PRINT_ERRORS** If set, the error status return of a BSD function returns a line number and type of error e.g. NX_SOC_ERROR where the error occurs.</span></span> <span data-ttu-id="69bb9-176">このためアプリケーション開発者は、デバッグ出力を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-176">This requires the application developer to define the debug output.</span></span> <span data-ttu-id="69bb9-177">既定の設定は無効であり、*nx_bsd.h* でデバッグ出力は指定されていません。</span><span class="sxs-lookup"><span data-stu-id="69bb9-177">The default setting is disabled and no debug output is specified in *nx_bsd.h*</span></span>
- <span data-ttu-id="69bb9-178">**NX_BSD_TIMER_RATE** BSD の定期的なタイマー タスクが実行されるまでの間隔。</span><span class="sxs-lookup"><span data-stu-id="69bb9-178">**NX_BSD_TIMER_RATE** Interval after which BSD periodic timer task runs.</span></span> <span data-ttu-id="69bb9-179">既定値は 1 秒 (1 \* NX_IP_PERIODIC_RATE) です。</span><span class="sxs-lookup"><span data-stu-id="69bb9-179">The default value is 1 second (1 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="69bb9-180">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER** 設定されている場合は、このオプションにより、BSD タイムアウト プロセスをシステム タイマー コンテキストで実行できます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-180">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER** If set, this option allows the BSD timeout process to execute in the system timer context.</span></span> <span data-ttu-id="69bb9-181">既定の動作は無効です。</span><span class="sxs-lookup"><span data-stu-id="69bb9-181">The default behavior is disabled.</span></span> <span data-ttu-id="69bb9-182">この機能は、第 2 章「NetX BSD のインストールと使用」でより詳細に説明されています。</span><span class="sxs-lookup"><span data-stu-id="69bb9-182">This feature is described in more detail in Chapter 2 "Installation and Use of NetX BSD".</span></span>
- <span data-ttu-id="69bb9-183">**NX_BSD_ENABLE_DNS** 有効になっている場合、NetX BSD では、ホスト名またはホスト IP アドレスを取得するために DNS クエリを送信します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-183">**NX_BSD_ENABLE_DNS** If enabled, NetX BSD will send a DNS query for a hostname or host IP address.</span></span> <span data-ttu-id="69bb9-184">DNS クライアント インスタンスが事前に作成され、起動されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-184">Requires a DNS Client instance to be previously created and started.</span></span> <span data-ttu-id="69bb9-185">既定では、有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="69bb9-185">By default it is not enabled.</span></span>
- <span data-ttu-id="69bb9-186">**NX_BSD_IPV4_ADDR_MAX_NUM** *getaddrinfo* によって返される IPv4 アドレスの最大数。</span><span class="sxs-lookup"><span data-stu-id="69bb9-186">**NX_BSD_IPV4_ADDR_MAX_NUM** Maximum number of IPv4 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="69bb9-187">*getaddrinfo* でのアドレス情報の格納にメモリを動的に割り当てるため、これを NX_BSD_IPV4_ADDR_MAX_NUM と一緒に使用して、NetX BSD ブロック プール nx_bsd_addrinfo_block_pool のサイズを定義します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-187">This along with NX_BSD_IPV4_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span> <span data-ttu-id="69bb9-188">既定値は 5 です。</span><span class="sxs-lookup"><span data-stu-id="69bb9-188">The default value is 5.</span></span>
- <span data-ttu-id="69bb9-189">**NX_BSD_IPV4_ADDR_PER_HOST**: DNS クエリごとに格納される IPv4 アドレスの最大数を定義します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-189">**NX_BSD_IPV4_ADDR_PER_HOST**: Defines maximum IPv4 addresses stored per DNS query.</span></span> <span data-ttu-id="69bb9-190">既定値は 5 です。</span><span class="sxs-lookup"><span data-stu-id="69bb9-190">The default value is 5.</span></span>

## <a name="bsd-socket-options"></a><span data-ttu-id="69bb9-191">BSD ソケット オプション</span><span class="sxs-lookup"><span data-stu-id="69bb9-191">BSD Socket Options</span></span>

<span data-ttu-id="69bb9-192">*setsockopt* サービスを使用して、次の NetX BSD ソケット オプションの一覧を実行時にソケットごとに有効 (または無効) にすることができます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-192">The following list of NetX BSD socket options can be enabled (or disabled) at run time on a per socket basis using the *setsockopt* service:</span></span>

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, const
                void *option_value, INT option_length);
```

<span data-ttu-id="69bb9-193">*option_level* には、2 つの異なる設定があります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-193">There are two different settings for *option_level*.</span></span>

<span data-ttu-id="69bb9-194">実行時のソケット オプションの最初の種類は、ソケット レベルのオプションのための SOL_SOCKET です。</span><span class="sxs-lookup"><span data-stu-id="69bb9-194">The first type of run time socket options is SOL_SOCKET for socket level options.</span></span> <span data-ttu-id="69bb9-195">ソケット レベルのオプションを有効にするには、option_level を SOL_SOCKET に設定し、option_name を SO_BROADCAST などの特定のオプションに設定して *setsockopt* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-195">To enable a socket level option, call *setsockopt* with option_level set to SOL_SOCKET and option_name set to the specific option e.g. SO_BROADCAST.</span></span> <span data-ttu-id="69bb9-196">オプション設定を取得するには、option_level を再び SOL_SOCKET に設定して option_name に対する *getsockopt* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-196">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to SOL_SOCKET.</span></span>

<span data-ttu-id="69bb9-197">以下に、実行時のソケット レベルのオプションの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-197">The list of run time socket level options is shown below.</span></span>

- <span data-ttu-id="69bb9-198">**SO_BROADCAST**: 設定されている場合は、これにより、Netx ソケットのブロードキャスト パケットの送受信が可能になります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-198">**SO_BROADCAST**: If set, this enables sending and receiving broadcast packets from Netx sockets.</span></span> <span data-ttu-id="69bb9-199">これは NetX の既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="69bb9-199">This is the default behavior for NetX.</span></span> <span data-ttu-id="69bb9-200">すべてのソケットがこの機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="69bb9-200">All sockets have this capability.</span></span>
- <span data-ttu-id="69bb9-201">**SO_ERROR**: *getsockopt* サービスを使用した、指定されたソケットの以前のソケット操作に関するソケット状態を取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-201">**SO_ERROR**: Used to obtain socket status on the previous socket operation of the specified socket, using the *getsockopt* service.</span></span> <span data-ttu-id="69bb9-202">すべてのソケットがこの機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="69bb9-202">All sockets have this capability.</span></span>
- <span data-ttu-id="69bb9-203">**SO_KEEPALIVE**: 設定されている場合は、これにより、TCP キープ アライブ機能が可能になります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-203">**SO_KEEPALIVE**: If set, this enables the TCP Keep Alive feature.</span></span> <span data-ttu-id="69bb9-204">このためには、*nx_user.h* で NX_TCP_ENABLE_KEEPALIVE を定義して NetX ライブラリを構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-204">This requires the NetX library to be built with NX_TCP_ENABLE_KEEPALIVE defined in *nx_user.h*.</span></span> <span data-ttu-id="69bb9-205">既定では、この機能は無効になります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-205">By default this feature is disabled.</span></span>
- <span data-ttu-id="69bb9-206">**SO_RCVTIMEO**: NetX BSD ソケットでパケットを受信するための待機オプションを秒単位で設定します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-206">**SO_RCVTIMEO**: This sets the wait option in seconds for receiving packets on NetX BSD sockets.</span></span> <span data-ttu-id="69bb9-207">既定値は NX_WAIT_FOREVER (0xFFFFFFFF) です。または、非ブロッキングが有効になっている場合は NX_NO_WAIT (0x0) です。</span><span class="sxs-lookup"><span data-stu-id="69bb9-207">The default value is the NX_WAIT_FOREVER (0xFFFFFFFF) or, if non-blocking is enabled, NX_NO_WAIT (0x0).</span></span>
- <span data-ttu-id="69bb9-208">**SO_RCVBUF**: TCP ソケットのウィンドウ サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-208">**SO_RCVBUF**: This sets the window size of the TCP socket.</span></span> <span data-ttu-id="69bb9-209">既定値の NX_BSD_TCP_WINDOW は、BSD TCP ソケットでは 64k に設定されます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-209">The default value, NX_BSD_TCP_WINDOW, is set to 64k for BSD TCP sockets.</span></span> <span data-ttu-id="69bb9-210">65535 を超えるサイズを設定するには、NX_TCP_ENABLE_WINDOW_SCALING を定義して NetX ライブラリを構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-210">To set the size over 65535 requires the NetX library to be built with the NX_TCP_ENABLE_WINDOW_SCALING be defined.</span></span>
- <span data-ttu-id="69bb9-211">**SO_REUSEADDR**: 設定されている場合は、これにより、1 つのポートに複数のソケットをマップできます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-211">**SO_REUSEADDR**: If set, this enables multiple sockets to be mapped to one port.</span></span> <span data-ttu-id="69bb9-212">典型的な使い方は TCP サーバー ソケット用です。</span><span class="sxs-lookup"><span data-stu-id="69bb9-212">The typical usage is for the TCP Server socket.</span></span> <span data-ttu-id="69bb9-213">これは NetX ソケットの既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="69bb9-213">This is the default behavior of NetX sockets.</span></span>

<span data-ttu-id="69bb9-214">実行時のソケット オプションの 2 番目の種類は、IP オプションのレベルです。</span><span class="sxs-lookup"><span data-stu-id="69bb9-214">The second type of run time socket options is the IP option level.</span></span> <span data-ttu-id="69bb9-215">IP レベルのオプションを有効にするには、option_level を IP_PROTO に設定し、option_name を IP_MULTICAST_TTL などのオプションに設定して *setsockopt* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-215">To enable an IP level option, call *setsockopt* with option_level set to IP_PROTO and option_name set to the option e.g. IP_MULTICAST_TTL.</span></span> <span data-ttu-id="69bb9-216">オプション設定を取得するには、option_level を再び IP_PROTO に設定して option_name に対する *getsockopt* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-216">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to IP_PROTO.</span></span>

<span data-ttu-id="69bb9-217">以下に、実行時の IP レベルのオプションの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-217">The list of run time IP level options is shown below.</span></span>

- <span data-ttu-id="69bb9-218">**IP_MULTICAST_TTL**: UDP ソケットの有効期限を設定します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-218">**IP_MULTICAST_TTL**: This sets the time to live for UDP sockets.</span></span> <span data-ttu-id="69bb9-219">ソケットが作成されるときの既定値は NX_IP_TIME_TO_LIVE (0x80) です。</span><span class="sxs-lookup"><span data-stu-id="69bb9-219">The default value is NX_IP_TIME_TO_LIVE (0x80) when the socket is created.</span></span> <span data-ttu-id="69bb9-220">この値は、このソケット オプションで *setsockopt* を呼び出してオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-220">This value can be overridden by calling *setsockopt* with this socket option.</span></span>
- <span data-ttu-id="69bb9-221">**IP_ADD_MEMBERSHIP**: 設定されている場合は、このオプションにより、BSD ソケット (UDP ソケットにのみ適用されます) は指定された IGMP グループに参加できます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-221">**IP_ADD_MEMBERSHIP**: If set, this options enables the BSD socket (applies only to UDP sockets) to join the specified IGMP group.</span></span>
- <span data-ttu-id="69bb9-222">**IP_DROP_MEMBERSHIP**: 設定されている場合は、このオプションにより、BSD ソケット (UDP ソケットにのみ適用されます) は指定された IGMP グループから離れることができます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-222">**IP_DROP_MEMBERSHIP**: If set, this options enables the BSD socket (applies only to UDP sockets) to leave the specified IGMP group.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="69bb9-223">小規模システムの例</span><span class="sxs-lookup"><span data-stu-id="69bb9-223">Small Example System</span></span>

<span data-ttu-id="69bb9-224">NetX BSD を使用する方法の例を以下の図 1.0 に示します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-224">An example of how to use NetX BSD is shown in Figure 1.0 below.</span></span> <span data-ttu-id="69bb9-225">この例では、インクルード ファイル *nx_bsd.h* が 7 行目で組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="69bb9-225">In this example, the include file *nx_bsd.h* is brought in at line 7.</span></span> <span data-ttu-id="69bb9-226">次に、IP インスタンス *bsd_ip* とパケット プール *bsd_pool* が、20 行目と 21 行目でグローバル変数として作成されています。</span><span class="sxs-lookup"><span data-stu-id="69bb9-226">Next, the IP instance *bsd_ip* and packet pool *bsd_pool* are created as global variables at line 20 and 21.</span></span> <span data-ttu-id="69bb9-227">このデモでは RAM (仮想) ネットワーク ドライバーを使用していることに注意してください (41 行目)。</span><span class="sxs-lookup"><span data-stu-id="69bb9-227">Note that this demo uses a ram (virtual) network driver (line 41).</span></span> <span data-ttu-id="69bb9-228">この例では、クライアントとサーバーが 1 つの IP インスタンス上で同じ IP アドレスを共有します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-228">The client and server will share the same IP address on single IP instance in this example.</span></span>

<span data-ttu-id="69bb9-229">クライアント スレッドとサーバー スレッドは、アプリケーションを設定し、293-361 行目で定義されている *tx_application_define* 内の 303 行目と 309 行目で作成されます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-229">The client and server threads are created on line 303 and 309 in *tx_application_define* which sets up the application and is defined on lines 293-361.</span></span> <span data-ttu-id="69bb9-230">IP インスタンスが 327 行目で正常に作成された後、その IP インスタンスは 350 行目で TCP サービスに対して有効になります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-230">After IP instance successful creation on line 327, the IP instance is enabled for TCP services on line 350.</span></span> <span data-ttu-id="69bb9-231">BSD サービスを使用できるようにする前の最後の要件は、360 行目で *bsd_initialize* を呼び出して、すべてのデータ構造体と NetX のほか、BSD で必要な ThreadX リソースを設定することです。</span><span class="sxs-lookup"><span data-stu-id="69bb9-231">The last requirement before BSD services can be used is to call *bsd_initialize* on line 360 to set up all data structures and NetX, and ThreadX resources needed by BSD.</span></span>

<span data-ttu-id="69bb9-232">381-397 行目で定義されているサーバー スレッドのエントリ関数 *thread_1_entry* では、アプリケーションは、ドライバーがネットワーク パラメーターで NetX を初期化するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-232">In the server thread entry function, *thread_1_entry,* which is defined on lines 381-397, the application waits for the driver to initialize NetX with network parameters.</span></span> <span data-ttu-id="69bb9-233">これが完了すると、この関数は 146-253 行目で定義されている *tcpServer* を呼び出して、TCP サーバー ソケットの設定の詳細を処理します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-233">Once this is done, it calls *tcpServer,* defined on lines 146-253, to handle the details of setting up the TCP server socket.</span></span>

<span data-ttu-id="69bb9-234">*tcpServer* では、159 行目で *socket* サービスを呼び出してマスター ソケットを作成した後、176 行目で *bind* 呼び出しを使用してそれをリスニング ソケットにバインドします。</span><span class="sxs-lookup"><span data-stu-id="69bb9-234">*tcpServer* creates the master socket by calling the *socket* service on line 159 and binds it to the listening socket using the *bind* call on line 176.</span></span> <span data-ttu-id="69bb9-235">これはその後、191 行目で接続要求をリッスンするように構成されます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-235">It is then configured for listening for connection requests on line 191.</span></span> <span data-ttu-id="69bb9-236">マスター ソケットが接続要求を受け付けないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="69bb9-236">Note that the master socket does not accept a connection request.</span></span> <span data-ttu-id="69bb9-237">これは、接続要求を検出するために、毎回 *select* を呼び出す連続したループで実行されます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-237">It runs in a continuous loop which calls *select* each time to detect connection requests.</span></span> <span data-ttu-id="69bb9-238">218 行目で *accept* サービスを呼び出した後、BSD ソケットの配列から選択されたセカンダリ BSD ソケットに接続要求が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-238">A secondary BSD socket chosen from an array of BSD sockets is assigned the connection request after calling the *accept* service on line 218.</span></span>

<span data-ttu-id="69bb9-239">クライアント側では、366-377 行目で定義されているクライアント スレッドのエントリ関数 *thread_0_entry* でも、NetX がドライバーによって初期化されるまで待つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="69bb9-239">On the Client side, the client thread entry function, *thread_0_entry*, defined on lines 366-377, should also wait for NetX to be initialized by the driver.</span></span> <span data-ttu-id="69bb9-240">ここでは、単にサーバー側でそれが行われるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-240">Here we just wait for the server side to do so.</span></span> <span data-ttu-id="69bb9-241">これは次に、54-142 行目で定義されている *tcpClient* を呼び出して、TCP クライアント ソケットの設定と TCP 接続の要求の詳細を処理します。</span><span class="sxs-lookup"><span data-stu-id="69bb9-241">It then calls *tcpClient* defined on line 54-142, to handle the details of setting up the TCP client socket and requesting a TCP connection.</span></span>

<span data-ttu-id="69bb9-242">TCP クライアント ソケットは 68 行目で作成されます。</span><span class="sxs-lookup"><span data-stu-id="69bb9-242">The TCP client socket is created on line 68.</span></span> <span data-ttu-id="69bb9-243">このソケットは、指定された IP アドレスにバインドされ、84 行目で *connect* を呼び出して TCP サーバーに接続しようとします。</span><span class="sxs-lookup"><span data-stu-id="69bb9-243">The socket is bound to the specified IP address and attempts to connect to the TCP server by calling *connect* on line 84.</span></span> <span data-ttu-id="69bb9-244">これで、パケットの送受信を開始する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="69bb9-244">It is now ready to begin sending and receiving packets.</span></span>

```c
1 /*  This is a small demo of BSD Wrapper for the high-performance NetX TCP/IP stack.
2     This demo demonstrate TCP connection, disconnection, sending, and receiving using
3     ARP and a simulated Ethernet driver. */
4
5 #include     "tx_api.h"
6 #include     "nx_api.h"
7 #include     "nx_bsd.h"
8 #include     <string.h>
9 #include     <stdlib.h>
10
11 #define         DEMO_STACK_SIZE         (16*1024)
12
13
14 /* Define the ThreadX and NetX object control blocks... */
15
16 TX_THREAD       thread_0;
17 TX_THREAD       thread_1;
18
19
20 NX_PACKET_POOL  bsd_pool;
21 NX_IP           bsd_ip;
22
23
24 /* Define the counters used in the demo application... */
25
26 ULONG           error_counter;
27
28 /* Define fd_set for select call */
29 fd_set          master_list,read_ready,read_ready1;
30
31
32 /* Define thread prototypes. */
33
34 VOID            thread_0_entry(ULONG thread_input);
35 VOID            thread_1_entry(ULONG thread_input);
36
37 VOID            tcpClient(CHAR *msg0);
38 VOID            tcpServer(VOID);
39 INT             HandleClient(INT sock);
40
41 VOID            _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
42
43
44 /* Define main entry point. */
45
46 int main()
47 {
48
49     /* Enter the ThreadX kernel. */
50     tx_kernel_enter();
51 }
52
53
54 VOID tcpClient(CHAR *msg0)
55 {
56
57 INT     status,status1,send_counter;
58 INT     sock_tcp_1,length,length1;
59 struct  sockaddr_in echoServAddr;       /* Echo server address */
60 struct  sockaddr_in localAddr;          /* Local address */
61 struct  sockaddr_in remoteAddr;         /* Remote address */
62
63 UINT    echoServPort; /* Echo Server Port */
64 CHAR    rcvBuffer1[32]
65
66
67     /* Create BSD TCP Socket */
68     sock_tcp_1 = **socket**( PF_INET, SOCK_STREAM, IPPROTO_TCP);
69     if (sock_tcp_1 == -1)
70     {
71         printf("\nError: BSD TCP Client socket create \n");
72         return;
73     }
74
75     printf("\nBSD TCP Client socket created %lu \n", sock_tcp_1);
76     /* Fill destination port and IP address */
77     echoServPort = 12;
78     memset(&echoServAddr, 0, sizeof(echoServAddr));
79     echoServAddr.sin_family = PF_INET;
80     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
81     echoServAddr.sin_port = echoServPort;
82
83     /* Now connect this client the server */
84     status1 = connect(sock_tcp_1, (struct sockaddr *)&echoServAddr, sizeof(echoServAddr));
85     /* Check for error. */
86     if (status1 != OK)
87     {
88         printf("\nError: BSD TCP Client socket Connect, %d \n",sock_tcp_1);
89         status = soc_close(sock_tcp_1);
90         if (status != ERROR)
91             printf("\nConnect ERROR so BSD Client Socket Closed: %d\n",sock_tcp_1);
92         else
93             printf("\nError: BSD Client Socket close %d\n",sock_tcp_1);
94         return;
95     }
96     /* Get and print source and destination information */
97     printf("\nBSD TCP Client socket: %d connected \n", sock_tcp_1);
98
99     status = getsockname(sock_tcp_1, (struct sockaddr *)&localAddr, &length);
100    printf("Client port = %lu , Client = %lu,", 
            localAddr.sin_port, localAddr.sin_addr.s_addr);
101    status = getpeername( sock_tcp_1, (struct sockaddr *) &remoteAddr, &length1);
102    printf("Remote port = %lu, Remote IP = %lu \n", 
            remoteAddr.sin_port remoteAddr.sin_addr.s_addr);
103
104    send_counter = 1;
105
106    /* Now receive the echoed packet from the server */
107    while(1)
108    {
109        tx_thread_sleep(2);
110
111        printf("\nClient sock: %d Sending packet No: %d to
                server\n",sock_tcp_1,send_counter);
112        status = send(sock_tcp_1,msg0, sizeof(msg0), 0);
113        if (status == ERROR)
114            printf("Error: BSD Client Socket send %d\n",sock_tcp_1);
115        else
116        {
117            printf("\nMessage sent: %s\n",msg0);
118            send_counter++;
119        }
120
121        status = recv(sock_tcp_1, (VOID *)rcvBuffer1, 31,0);
122        if (status == 0)
123            break;
124
125        rcvBuffer1[status] = 0;
126
127        if (status != ERROR)
128            printf("\nBSD Client Socket: %d received %lu bytes: %s ", 
                        sock_tcp_1,(ULONG)status,rcvBuffer1);
129        else
130            printf("\nError: BSD Client Socket receive %d \n",sock_tcp_1);
131
132    }
133
134    /* close this client socket */
135    status = soc_close(sock_tcp_1);
136    if (status != ERROR)
137        printf("\nBSD Client Socket Closed %d\n",sock_tcp_1);
138    else
139        printf("\nError: BSD Client Socket close %d \n",sock_tcp_1);
140
141    /* End */
142 }
143
144
145
146 void tcpServer(void)
147 {
148
149 INT         status,status1,sock,sock_tcp_2,i;
150 struct      sockaddr_in echoServAddr; /* Echo server address */
151 struct      sockaddr_in ClientAddr;
152
153 INT         Clientlen;
154 UINT        echoServPort; /* Echo Server Port */
155
156 INT         maxfd;
157
158 /* Create BSD TCP Server Socket */
159     sock_tcp_2 = socket( PF_INET, SOCK_STREAM, IPPROTO_TCP);
160     if (sock_tcp_2 == -1)
161     {
162         printf("Error: BSD TCP Server socket create\n");
163         return;
164     }
165     else
166         printf("BSD TCP Server socket created \n");
167
168     /* Now fill server side information */
169     echoServPort = 12;
170     memset(&echoServAddr, 0, sizeof(echoServAddr));
171     echoServAddr.sin_family = PF_INET;
172     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
173     echoServAddr.sin_port = echoServPort;
174
175     /* Bind this server socket */
176         status = bind(sock_tcp_2, (struct sockaddr *) &echoServAddr, sizeof(echoServAddr));
177     if (status < 0)
178     {
179         printf("Error: BSD TCP Server Socket Bind \n");
180         return;
181     }
182     else
183         printf("BSD TCP Server Socket bound \n");
184
185     FD_ZERO(&master_list);
186     FD_ZERO(&read_ready);
187     FD_SET(sock_tcp_2,&master_list);
188     maxfd = sock_tcp_2;
189
190     /* Now listen for any client connections for this server socket */
191     status = listen(sock_tcp_2,5);
192     if (status < 0)
193     {
194         printf("Error: BSD TCP Server Socket Listen\n");
195         return;
196     }
197     else
198         printf("BSD TCP Server Socket Listen complete, ");
199
200     /* All set to accept client connections */
201     printf("Now accepting client connections\n");
202
203     /* Loop to create and establish server connections. */
204     while(1)
205     {
206
207         read_ready = master_list;
208         tx_thread_sleep(2); /* Allow some time to other threads too */
209         status = select(maxfd+1,&read_ready,0,0,0);
210         if (status == ERROR)
211         {
212             continue;
213         }
214
215         status = FD_ISSET(sock_tcp_2,&read_ready);
216         if(status)
217         {
218             sock = accept(sock_tcp_2,(struct sockaddr*)&ClientAddr, &Clientlen);
219
220             /* Add this new connection to our master list */
221             FD_SET(sock,&master_list);
222             if ( sock \maxfd)
223             {
224                 maxfd = sock;
225             }
226
227             continue;
228         }
229         for (i = 0; i < (maxfd+1); i++)
230         {
231             if (( i != sock_tcp_2) && (FD_ISSET(i,&master_list)) && 
                    (FD_ISSET(i,&read_ready)))
232             {
233                 status1 = HandleClient(i);
234                 if (status1 == 0)
235                 {
236                     status1 = soc_close(i);
237                     if (status1 == OK)
238                     {
239                         FD_CLR(i,&master_list);
240                         printf("\nBSD Server Socket:%d closed\n",i);
241                     }
242                     else
243                         printf("\nError:BSD Server Socket:%d close\n",i);
244                 }
245
246             }
247         }
248
249         /* Loop back to check any next client connection */
250
251     } /* While(1) ends */
252
253 }
254
255 CHAR     rcvBuffer[128];
256
257 INT     HandleClient(INT sock)
258 {
259
260 INT     status;
261
262
263     status = recv(sock, (VOID *)rcvBuffer, 128,0);
264     if (status == ERROR )
265     {
266         printf("\n BSD Server Socket:%d receive \n",sock);
267         return(ERROR);
268     }
269
270     /* a zero return from a recv() call indicates client is terminated! */
271     if (status == 0)
272     {
273         /* Done with this client , close this secondary server socket */
274         return(status);
275     }
276
277     /* print data received from the client */
278     printf("\nBSD Server Socket:%d received %lu bytes: %s \n", sock, (ULONG)status,rcvBuffer);
279
280     /* And echo the same data to the client */
281     status = send(sock,rcvBuffer, status + 1, 0);
282     if (status == ERROR )
283     {
284         printf("\nError: BSD Server Socket:%d send \n",sock);
285         return(ERROR);
286     }
287     return(status);
288 }
289
290
291 /* Define what the initial system looks like. */
292
293 void     tx_application_define(void *first_unused_memory)
294 {
295
296 CHAR     *pointer;
297 UINT     status;
298
299     /* Setup the working pointer. */
300     pointer = (CHAR *) first_unused_memory;
301
302     /* Create a client thread. */
303     tx_thread_create(&thread_0, "Client1", thread_0_entry, 0,
304         pointer, DEMO_STACK_SIZE, 2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
305
306     pointer = pointer + DEMO_STACK_SIZE;
307
308     /* Create a server thread. */
309     tx_thread_create(&thread_1, "Server", thread_1_entry, 0,
310         pointer, DEMO_STACK_SIZE,1,1, TX_NO_TIME_SLICE, TX_AUTO_START);
311
312     pointer = pointer + DEMO_STACK_SIZE;
313
314     /* Initialize the NetX system. */
315     nx_system_initialize();
316
317     /* Create a BSD packet pool. */
318     status = nx_packet_pool_create(&bsd_pool,"NetX BSD Packet Pool", 128
                                        pointer, 16384);
319     pointer = pointer + 16384;
320     if (status)
321     {
322         error_counter++;
323         printf("Error in creating BSD packet pool\n!");
324     }
325
326     /* Create an IP instance for BSD. */
327     status = nx_ip_create(&bsd_ip, "NetX IP Instance 2", IP_ADDRESS(1, 2, 3, 4),
                              0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                              pointer, 2048, 1);
328
329     pointer = pointer + 2048;
330
331     if (status)
332     {
333         error_counter++;
334         printf("Error creating BSD IP instance\n!");
335     }
336
337     /* Enable ARP and supply ARP cache memory for BSD IP Instance */
338     status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
339     pointer = pointer + 1024;
340
341     /* Check ARP enable status. */
342     if (status)
343     {
344         error_counter++;
345         printf("Error in Enable ARP and supply ARP cache memory to BSD IP instance\n");
346     }
347
348     /* Enable TCP processing for BSD IP instances. */
349
350     status = nx_tcp_enable(&bsd_ip);
351
352     /* Check TCP enable status. */
353     if (status)
354     {
355         error_counter++;
356         printf("Error in Enable TCP \n");
357     }
358
359     /* Now initialize BSD Scoket Wrapper */
360     status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 1);
361 }
362
363
364 /* Define the test threads. */
365
366 void     thread_0_entry)ULONG thread_input)
367 {
368
369 CHAR     *msg0 = "Client 1:
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<> \
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";
370
371     /* Wait till Server side is all set */
372     tx_thread_sleep(2);
373     while (1)
374     {
375         tcpClient(msg0);
376         tx_thread_sleep(1);
377     }
378 }
379
380 /* Define the server thread entry function. */
381 void     thread_1_entry(ULONG thread_input)
382 {
383
384 UINT     status;
385 ULONG    actual_status;
386
387 /* Ensure the IP instance has been initialized. */
388 status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE, &actual_status, 100);
389
390 /* Check status... */
391 if (status != NX_SUCCESS)
392 {
393     error_counter++;
394     return;
395 }
396 /* Start a TCP Server */
397 tcpServer();
398 }
399
```
