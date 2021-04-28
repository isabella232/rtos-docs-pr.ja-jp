---
title: 第 2 章 - Azure RTOS NetX Duo DNS Client のインストールと使用
description: この章では、Azure RTOS NetX Duo DNS Client のインストール、セットアップ、使用に関するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 75b85829f80462015d66e1623b880d5139349ce0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811816"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dns-client"></a><span data-ttu-id="b0797-103">第 2 章 - Azure RTOS NetX Duo DNS Client のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="b0797-103">Chapter 2 - Installation and Use of Azure RTOS NetX Duo DNS Client</span></span>

<span data-ttu-id="b0797-104">この章では、Azure RTOS NetX Duo DNS Client のインストール、セットアップ、使用に関するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="b0797-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo DNS Client.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="b0797-105">製品の配布パッケージ</span><span class="sxs-lookup"><span data-stu-id="b0797-105">Product Distribution</span></span>

<span data-ttu-id="b0797-106">NetX Duo DNS Client は [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="b0797-106">NetX Duo DNS Client is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="b0797-107">このパッケージには、下に挙げるとおり、ソース ファイル 2 つと、このドキュメントを含む PDF ファイル 1 つが含まれています:</span><span class="sxs-lookup"><span data-stu-id="b0797-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="b0797-108">**nxd_dns.h** NetX Duo DNS Client のヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="b0797-108">**nxd_dns.h** Header file for NetX Duo DNS Client</span></span>
- <span data-ttu-id="b0797-109">**nxd_dns.c** NetX Duo DNS Client の C 言語のソース ファイル</span><span class="sxs-lookup"><span data-stu-id="b0797-109">**nxd_dns.c** C Source file for NetX Duo DNS Client</span></span>
- <span data-ttu-id="b0797-110">**nxd_dns.pdf** NetX Duo DNS Client の説明書の PDF ファイル</span><span class="sxs-lookup"><span data-stu-id="b0797-110">**nxd_dns.pdf** PDF description of NetX Duo DNS Client</span></span>

## <a name="dns-client-installation"></a><span data-ttu-id="b0797-111">DNS クライアントのインストール</span><span class="sxs-lookup"><span data-stu-id="b0797-111">DNS Client Installation</span></span>

<span data-ttu-id="b0797-112">NetX Duo DNS Client を使用するには、ソース コード ファイル *nxd_dns.c* と *nxd_dns.h* を NetX Duo がインストールされているのと同じディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b0797-112">To use NetX Duo DNS Client, copy the source code files *nxd_dns.c* and *nxd_dns.h* to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="b0797-113">たとえば、NetX Duo がディレクトリ " *\threadx\arm7\green*" にインストールされている場合、*nxd_dns.h* ファイルと *nxd_dns.c* ファイルをこのディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b0797-113">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_dns.h* and *nxd_dns.c* files should be copied into this directory.</span></span>

## <a name="using-the-dns-client"></a><span data-ttu-id="b0797-114">DNS クライアントを使用する</span><span class="sxs-lookup"><span data-stu-id="b0797-114">Using the DNS Client</span></span>

<span data-ttu-id="b0797-115">NetX Duo DNS Client の使用方法は簡単です。</span><span class="sxs-lookup"><span data-stu-id="b0797-115">Using NetX Duo DNS Client is easy.</span></span> <span data-ttu-id="b0797-116">基本的には、ThreadX と NetX Duo を使用するために、アプリケーション コードにそれぞれ *tx_api.h* と *nx_api.h* をインクルードした後に、*nxd_dns.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0797-116">Basically, the application code must include *nxd_dns.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX Duo, respectively.</span></span> <span data-ttu-id="b0797-117">*nxd_dns.h* をインクルードすると、このガイドで後述する DNS の関数を、そのアプリケーションのコードで呼び出せるようになります。</span><span class="sxs-lookup"><span data-stu-id="b0797-117">Once *nxd_dns.h* is included, the application code is then able to make the DNS function calls specified later in this guide.</span></span> <span data-ttu-id="b0797-118">また、アプリケーションのビルドには *nxd_dns.c* を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0797-118">The application must also add *nxd_dns.c* to the build process.</span></span> <span data-ttu-id="b0797-119">このファイルは、他のアプリケーション ファイルと同様にコンパイルし、オブジェクトとしてアプリケーションのファイルと共にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0797-119">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="b0797-120">NetX Duo DNS の使用に必要なものはこれですべてです。</span><span class="sxs-lookup"><span data-stu-id="b0797-120">This is all that is required to use NetX Duo DNS.</span></span>

> [!NOTE]
> <span data-ttu-id="b0797-121">DNS では NetX Duo UDP のサービスを使用するため、DNS を使用するときは、前もって *nx_udp_enable* を呼び出して UDP を有効にしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0797-121">Since DNS utilizes NetX Duo UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DNS.</span></span>

## <a name="small-example-system-for-netx-duo-dns-client"></a><span data-ttu-id="b0797-122">NetX Duo DNS Client のシステムの簡単な例</span><span class="sxs-lookup"><span data-stu-id="b0797-122">Small Example System for NetX Duo DNS Client</span></span> 

<span data-ttu-id="b0797-123">NetX Duo DNS Cilent は、既存の NetX DNS アプリケーションと互換性があります。</span><span class="sxs-lookup"><span data-stu-id="b0797-123">NetX Duo DNS Client is compatible with existing NetX DNS applications.</span></span> <span data-ttu-id="b0797-124">古いサービスと、それに対応する NetX Duo のサービスのリストを次に示します:</span><span class="sxs-lookup"><span data-stu-id="b0797-124">The list of legacy services and their NetX Duo equivalent is shown below:</span></span>

| <span data-ttu-id="b0797-125">NetX DNS API サービス (IPv4 のみ)</span><span class="sxs-lookup"><span data-stu-id="b0797-125">NetX DNS API service (IPv4 only)</span></span> | <span data-ttu-id="b0797-126">NetX Duo DNS API サービス (IPv4 と IPv6 をサポート)</span><span class="sxs-lookup"><span data-stu-id="b0797-126">NetX Duo DNS API service (IPv4 and IPv6 supported)</span></span> |
|----------------------------------|----------------------------------------------------|
| <span data-ttu-id="b0797-127">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="b0797-127">nx_dns_host_by_name_get</span></span>          | <span data-ttu-id="b0797-128">nxd_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="b0797-128">nxd_dns_host_by_name_get</span></span>                           |
| <span data-ttu-id="b0797-129">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="b0797-129">nx_dns_host_by_address_get</span></span>       | <span data-ttu-id="b0797-130">nxd_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="b0797-130">nxd_dns_host_by_address_get</span></span>                        |
| <span data-ttu-id="b0797-131">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="b0797-131">nx_dns_server_get</span></span>                | <span data-ttu-id="b0797-132">nxd_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="b0797-132">nxd_dns_server_get</span></span>                                 |
| <span data-ttu-id="b0797-133">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="b0797-133">nx_dns_server_add</span></span>                | <span data-ttu-id="b0797-134">nxd_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="b0797-134">nxd_dns_server_add</span></span>                                 |
| <span data-ttu-id="b0797-135">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="b0797-135">nx_dns_server_remove</span></span>             | <span data-ttu-id="b0797-136">nxd_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="b0797-136">nxd_dns_server_remove</span></span>                              |

<span data-ttu-id="b0797-137">詳細は、第 3 章の「NetX Duo DNS Client API サービスの説明」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b0797-137">See the description of NetX Duo DNS Client API services in Chapter 3 for more details.</span></span>

<span data-ttu-id="b0797-138">このセクションで示す DNS アプリケーション プログラムの例では、6 行目で *nxd_dns.h* をインクルードします。</span><span class="sxs-lookup"><span data-stu-id="b0797-138">In the example DNS application program provided in this section, *nxd_dns.h* is included at line 6.</span></span> <span data-ttu-id="b0797-139">24 ～ 26 行目では NX_DNS_CLIENT_USER_CREATE_PACKET_POOL を宣言し、DNS クライアント アプリケーションが DNS クライアントのパケット プールを作成できるようにしています。</span><span class="sxs-lookup"><span data-stu-id="b0797-139">NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, which allows the DNS Client application to create the packet pool for the DNS Client, is declared on lines 24-26.</span></span> <span data-ttu-id="b0797-140">このパケット プールは、DNS メッセージの送信に使用するパケットを割り当てるのに使用します。</span><span class="sxs-lookup"><span data-stu-id="b0797-140">This packet pool is used for allocating packets for sending DNS messages.</span></span> <span data-ttu-id="b0797-141">NX_DNS_CLIENT_USER_CREATE_PACKET_POOL が定義されている場合、78 ～ 98 行目でパケット プールを作成します。</span><span class="sxs-lookup"><span data-stu-id="b0797-141">If NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined, a packet pool is created in lines 78-98.</span></span> <span data-ttu-id="b0797-142">このオプションが有効でない場合、DNS クライアントは、*nxd_dns.h* の構成パラメーターで設定されるパケットのペイロードとパケット プールのサイズに応じて、専用のパケット プールを作成します。パケットのペイロードとパケット プールのサイズの設定については、この章の他の箇所で説明します。</span><span class="sxs-lookup"><span data-stu-id="b0797-142">If this option is not enabled, the DNS Client creates its own packet pool as per the packet payload and pool size set by configuration parameters in *nxd_dns.h* and described elsewhere in this chapter.</span></span>

<span data-ttu-id="b0797-143">NetX Duo の内部操作に使用するクライアントの IP インスタンスのために、100 ～ 112 行目でもう 1 つパケット プールを作成します。</span><span class="sxs-lookup"><span data-stu-id="b0797-143">Another packet pool is created in lines 100-112 for the Client IP instance which is used for internal NetX Duo operations.</span></span> <span data-ttu-id="b0797-144">次に、115 行目で *nx_ip_create* を呼び出して IP インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b0797-144">Next the IP instance is created using the *nx_ip_create* call in line 115.</span></span> <span data-ttu-id="b0797-145">IP タスクと DNS クライアントでは同じパケット プールを共有できますが、通常、DNS クライアントから送信されるメッセージの方が IP タスクが送信する制御パケットよりも大きいため、別々のパケット プールを使用する方が効率的にメモリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b0797-145">It is possible for the IP task and the DNS Client to share the same packet pool, but since the DNS Client typically sends out larger messages than the control packets sent by the IP task, using separate packet pools makes more efficient use of memory.</span></span>

<span data-ttu-id="b0797-146">129 行目と 141 行目で ARP と UDP (IPv4 ネットワークで使用) をそれぞれ有効にします。</span><span class="sxs-lookup"><span data-stu-id="b0797-146">ARP and UDP (which is used by IPv4 networks) are enabled in lines 129 and 141 respectively.</span></span>

>[!NOTE]
> <span data-ttu-id="b0797-147">このデモでは、44 行目で "ram" ドライバーを宣言し、*nx_ip_create* の呼び出しでこれを使用しています。</span><span class="sxs-lookup"><span data-stu-id="b0797-147">This demo uses the ‘ram’ driver declared on line 44 and used in the *nx_ip_create* call.</span></span> <span data-ttu-id="b0797-148">この RAM ドライバーは、NetX Duo のソース コードと合わせて配布されています。</span><span class="sxs-lookup"><span data-stu-id="b0797-148">This ram driver is distributed with the NetX Duo source code.</span></span> <span data-ttu-id="b0797-149">DNS クライアントを実行するには、実際に使用する物理ネットワーク ドライバーをアプリケーションで指定して、DNS サーバーに対しパケットを送受信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0797-149">To actually run the DNS Client the application must supply an actual physical network driver to transmit and receive packets from the DNS server.</span></span>

<span data-ttu-id="b0797-150">クライアント スレッド エントリ関数 *thread_client_entry* を *tx_application_define* 関数の下で定義します。</span><span class="sxs-lookup"><span data-stu-id="b0797-150">The Client thread entry function *thread_client_entry* is defined below the *tx_application_define* function.</span></span> <span data-ttu-id="b0797-151">ここでは最初にシステムの制御を放棄し、ネットワーク ドライバーで IP タスク スレッドを初期化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b0797-151">It initially relinquishes control to the system to allow the IP task thread to be initialized by the network driver.</span></span>

<span data-ttu-id="b0797-152">次に、257 行目で DNS クライアントを作成し、267 ～ 278 行目で DNS キャッシュを初期化し、281 ～ 295 行目で、先に作成したパケット プールを DNS クライアント インスタンスに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b0797-152">It then creates the DNS Client in line 257, initializes the DNS cache on lines 267- 278, and sets the packet pool previously created to the DNS Client instance on lines 281-295.</span></span> <span data-ttu-id="b0797-153">次に、297 ～ 341 行目で DNS サーバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="b0797-153">It then adds DNS server on lines 297-341.</span></span>

<span data-ttu-id="b0797-154">サンプル プログラムの残りの部分では、DNS クライアントのサービスを使用して DNS クエリを実行しています。</span><span class="sxs-lookup"><span data-stu-id="b0797-154">The remainder of the example program uses the DNS Client services to make DNS queries.</span></span> <span data-ttu-id="b0797-155">193 行目と 207 行目でホストの IP アドレスの検索が実行されます。</span><span class="sxs-lookup"><span data-stu-id="b0797-155">Host IP address lookups are performed on lines 193 and 207.</span></span> <span data-ttu-id="b0797-156">これら 2 つのサービス *nxd_dns_host_by_name_get* と *nx_dns_host_by_name_get* の違いは、前者がアドレスのデータを NXD_ADDRESS のデータ型で保存するのに対し、後者は ULONG のデータ型で保存することです。</span><span class="sxs-lookup"><span data-stu-id="b0797-156">The difference between these two services, *nxd_dns_host_by_name_get* and *nx_dns_host_by_name_get*, is that the former saves the address data in an NXD_ADDRESS data type, while the latter saves the data in a ULONG data type.</span></span> <span data-ttu-id="b0797-157">さらに、後者は IPv4 ネットワークでしか使用できないのに対し、前者は IPv6 と IPv4 ネットワークで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b0797-157">Further the latter is limited to IPv4 networks, while the former can be used with IPv6 or IPv4 networks.</span></span> <span data-ttu-id="b0797-158">これができるのは、IP インスタンスで IPv6 が有効になっている場合です。</span><span class="sxs-lookup"><span data-stu-id="b0797-158">This is only possible if the IP instance is enabled for IPv6.</span></span> <span data-ttu-id="b0797-159">IP インスタンスで IPv6 ネットワークを有効にする詳しい方法は「NetX Duo ユーザー ガイド」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b0797-159">See the NetX Duo User Guide for more details on enabling the IP instance for IPv6 networking.</span></span>

<span data-ttu-id="b0797-160">464 行目では、別のサービス *nx_dns_ipv4_address_by_name_get* を使用してホストの IP アドレスを検索します。</span><span class="sxs-lookup"><span data-stu-id="b0797-160">Another service for host IP address lookups is shown on line 464, *nx_dns_ipv4_address_by_name_get*.</span></span> <span data-ttu-id="b0797-161">このサービスは *nx_dns_host_by_name_get* と異なり、DNS サーバーの応答で最初に挙げられたアドレスだけでなく、ドメイン名に対して検出されたすべての IPv4 アドレス (または用意されたバッファーに書き込めるできる限り多くのアドレス) を返します。</span><span class="sxs-lookup"><span data-stu-id="b0797-161">This service differs from *nx_dns_host_by_name_get* in that it returns all (or as many will fit in the supplied buffer) of the IPv4 addresses discovered for the domain name, not just the first address received in the DNS Server reply.</span></span>

<span data-ttu-id="b0797-162">同様に、380 行目で呼び出す *nxd_dns_ipv6_address_by_name_get* サービスは、最初のアドレスだけでなく、DNS クライアントにより検出されたすべての IPv6 アドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="b0797-162">Similarly, the *nxd_dns_ipv6_address_by_name_get* service, called on line 380, returns all the IPv6 addresses discovered by the DNS Client, not just the first one.</span></span>

<span data-ttu-id="b0797-163">606 行目 (*nx_dns_host_by_address_get*) と、564 行目および 588 行目 (*nxd_dns_host_by_address_get*) では逆引きを実行します (IP アドレスからホスト名を取得)。</span><span class="sxs-lookup"><span data-stu-id="b0797-163">Reverse lookups (host name from IP address) are performed on lines 606 (*nx_dns_host_by_address_get*) and again on line 564 and 588 (*nxd_dns_host_by_address_get*).</span></span> <span data-ttu-id="b0797-164">*nx_dns_host_by_address_get* は IPv4 ネットワークでしか使用できませんが、*nxd_dns_host_by_address_get* は IPv4 と IPv6 ネットワークのどちらでも使用できます (たとえば、IPv6 と IPv4 ネットワークが有効になっている IP インスタンスで使用)。</span><span class="sxs-lookup"><span data-stu-id="b0797-164">*nx_dns_host_by_address_get* will only work on IPv4 networks, while *nxd_dns_host_by_address_get* will work on either IPv4 or IPv6 networks (e.g. the IP instance is enabled for IPv6 as well as IPv4 networks).</span></span>

<span data-ttu-id="b0797-165">627 行目と 649 行目では、別の 2 つの DNS 検索サービス CNAME と TXT を使用して、入力したドメイン名に対する CNAME とドメイン名データを取得する方法を、それぞれ例示しています。</span><span class="sxs-lookup"><span data-stu-id="b0797-165">Two more services for DNS lookups, CNAME and TXT, are demonstrated on lines 627 and 649 respectively, to discover CNAME and domain name data for the input domain name.</span></span> <span data-ttu-id="b0797-166">NetX Duo DNS Client には、MX、NS、SRV、SOA など他の種類のレコードに対しても同様のサービスが存在します。</span><span class="sxs-lookup"><span data-stu-id="b0797-166">NetX Duo DNS Client as similar services for other record types, e.g. MX, NS, SRV and SOA.</span></span> <span data-ttu-id="b0797-167">NetX Duo DNS Client で検索できるレコードの種類すべての詳しい説明は、第 3 章をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b0797-167">See Chapter 3 for detailed descriptions of all record type lookups available in NetX Duo DNS Client.</span></span>

<span data-ttu-id="b0797-168">846 行目で *nx_dns_delete* サービスを使用して DNS クライアントを削除するとき、専用のパケット プールを作成した場合を除き、この DNS クライアントのパケット プールは削除されません。</span><span class="sxs-lookup"><span data-stu-id="b0797-168">When the DNS Client is deleted on line 846, using the *nx_dns_delete* service, the packet pool for the DNS Client is not deleted unless the DNS Client created its own packet pool.</span></span> <span data-ttu-id="b0797-169">その他の場合、それ以上使用しないパケット プールを削除するかどうかはアプリケーションに任されています。</span><span class="sxs-lookup"><span data-stu-id="b0797-169">Otherwise, it is up to the application to delete the packet pool if it has no further use for it.</span></span>

```C
/* This is a small demo of DNS Client for the high-performance NetX TCP/IP stack. */

#include   "tx_api.h"
#include   "nx_api.h"
#include   "nx_udp.h"
#include   "nxd_dns.h"

#ifdef FEATURE_NX_IPV6
#include   "nx_ipv6.h"
#endif

#define     DEMO_STACK_SIZE         4096

#define     NX_PACKET_PAYLOAD       1536
#define     NX_PACKET_POOL_SIZE     30 * NX_PACKET_PAYLOAD
#define     LOCAL_CACHE_SIZE        2048

/* Define the ThreadX and NetX object control blocks... */

NX_DNS                  client_dns;
TX_THREAD               client_thread;
NX_IP                   client_ip;
NX_PACKET_POOL          main_pool;
#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL
NX_PACKET_POOL          client_pool;
#endif
UCHAR                   local_cache[LOCAL_CACHE_SIZE];

UINT                    error_counter = 0;

#ifdef FEATURE_NX_IPV6
/* If IPv6 is enabled in NetX Duo, allow DNS Client to try using IPv6 */
//#define USE_IPV6
#endif

#define CLIENT_ADDRESS      IP_ADDRESS(192,168,0,11)
#define DNS_SERVER_ADDRESS  IP_ADDRESS(192,168,0,1)

/* Define thread prototypes. */

void    thread_client_entry(ULONG thread_input);

/***** Substitute your ethernet driver entry function here *********/
extern  VOID _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

    /* Setup the working pointer. */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&client_thread, "Client thread", thread_client_entry, 0,
            pointer, DEMO_STACK_SIZE, 4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL

    /* Create the packet pool for the DNS Client to send packets.

        If the DNS Client is configured for letting the host application create
        the DNS packet pool, (see NX_DNS_CLIENT_USER_CREATE_PACKET_POOL option), see
       nx_dns_create() for guidelines on packet payload size and pool size.
       packet traffic for NetX processes.
    */
    status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", NX_DNS_PACKET_PAYLOAD, pointer, NX_DNS_PACKET_POOL_SIZE);

    pointer = pointer + NX_DNS_PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {

        error_counter++;
        return;
     }
#endif
     /* Create the packet pool which the IP task will use to send packets. Also available to the host
       application to send packet. */
    status =  nx_packet_pool_create(&main_pool, "Main Packet Pool", NX_PACKET_PAYLOAD, pointer, NX_PACKET_POOL_SIZE);

    pointer = pointer + NX_PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Create an IP instance for the DNS Client. */
    status = nx_ip_create(&client_ip, "DNS Client IP Instance", CLIENT_ADDRESS, 0xFFFFFF00UL,
                          &main_pool, _nx_ram_network_driver, pointer, 2048, 1);

    pointer =  pointer + 2048;

    /* Check for IP create errors. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Enable ARP and supply ARP cache memory for the DNS Client IP. */
    status =  nx_arp_enable(&client_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Enable UDP traffic because DNS is a UDP based protocol. */
    status =  nx_udp_enable(&client_ip);

    /* Check for UDP enable errors. */
    if (status)
    {

        error_counter++;
        return;
     }
}

#define BUFFER_SIZE     200
#define RECORD_COUNT    10

/* Define the Client thread. */

void    thread_client_entry(ULONG thread_input)
{

UCHAR           record_buffer[200];
UINT            record_count;
UINT            status;
ULONG           host_ip_address;
#ifdef FEATURE_NX_IPV6
NXD_ADDRESS     host_ipduo_address;
NXD_ADDRESS     test_ipduo_server_address;
#ifdef USE_IPV6
NXD_ADDRESS     client_ipv6_address;
NXD_ADDRESS     dns_ipv6_server_address;
UINT            iface_index, address_index;
#endif
#endif
UINT            i;
ULONG           *ipv4_address_ptr[RECORD_COUNT];
NX_DNS_IPV6_ADDRESS
                *ipv6_address_ptr[RECORD_COUNT];
#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
NX_DNS_NS_ENTRY
                *nx_dns_ns_entry_ptr[RECORD_COUNT];
NX_DNS_MX_ENTRY
                *nx_dns_mx_entry_ptr[RECORD_COUNT];
NX_DNS_SRV_ENTRY
                *nx_dns_srv_entry_ptr[RECORD_COUNT];
NX_DNS_SOA_ENTRY
                *nx_dns_soa_entry_ptr;
ULONG           host_address;
USHORT          host_port;
#endif

    /* Give NetX IP task a chance to get initialized . */
    tx_thread_sleep(100);

#ifdef FEATURE_NX_IPV6
#ifdef USE_IPV6

    /* Make the DNS Client IPv6 enabled. */
    status = nxd_ipv6_enable(&client_ip);

    /* Check for enable errors. */
    if (status)
    {

        error_counter++;
        return;
     }
    status = nxd_icmp_enable(&client_ip);

    /* Check for enable errors. */
    if (status)
    {

        error_counter++;
        return;
    }

    client_ipv6_address.nxd_ip_address.v6[3] = 0x101;
    client_ipv6_address.nxd_ip_address.v6[2] = 0x0;
    client_ipv6_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ipv6_address.nxd_ip_address.v6[0] = 0x20010db8;
    client_ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;


     /* Set the link local address with the host MAC address. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, &address_index);

    /* Check for link local address set error. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Set the host global IP address. We are assuming a 64
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, &client_ipv6_address, 64, &address_index);

    /* Check for global address set error. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Wait while NetX Duo validates the link local and global address. */
    tx_thread_sleep(500);
#endif
#endif

    /* Create a DNS instance for the Client. Note this function will create
       the DNS Client packet pool for creating DNS message packets intended
       for querying its DNS server. */
    status =  nx_dns_create(&client_dns, &client_ip, (UCHAR *)"DNS Client");

    /* Check for DNS create error. */
    if (status)
    {

        error_counter++;
        return;
     }

#ifdef NX_DNS_CACHE_ENABLE
    /* Initialize the cache. */
    status = nx_dns_cache_initialize(&client_dns, local_cache, LOCAL_CACHE_SIZE);

    /* Check for DNS cache error. */
    if (status)
    {

        error_counter++;
        return;
     }
#endif

    /* Is the DNS client configured for the host application to create the pecket pool? */
#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL

    /* Yes, use the packet pool created above which has appropriate payload size
       for DNS messages. */
     status = nx_dns_packet_pool_set(&client_dns, &client_pool);

     /* Check for set DNS packet pool error. */
     if (status)
     {

         error_counter++;
         return;
      }

#endif /* NX_DNS_CLIENT_USER_CREATE_PACKET_POOL */

#ifdef FEATURE_NX_IPV6
#ifdef USE_IPV6

    /* Add an IPv6 DNS server to the DNS client. */
    dns_ipv6_server_address.nxd_ip_address.v6[3] = 0x106;
    dns_ipv6_server_address.nxd_ip_address.v6[2] = 0x0;
    dns_ipv6_server_address.nxd_ip_address.v6[1] = 0x0000f101;
    dns_ipv6_server_address.nxd_ip_address.v6[0] = 0x20010db8;
    dns_ipv6_server_address.nxd_ip_version = NX_IP_VERSION_V6;

    status = nxd_dns_server_add(&client_dns, &dns_ipv6_server_address);

    /* Check for DNS add server error. */
    if (status)
    {

        error_counter++;
        return;
     }
#else

    /* Add an IPv4 server address to the Client list. */
    status = nx_dns_server_add(&client_dns, DNS_SERVER_ADDRESS);

    /* Check for DNS add server error. */
    if (status)
    {

        error_counter++;
        return;
     }
#endif
#else

    /* Add an IPv4 server address to the Client list. */
    status = nx_dns_server_add(&client_dns, DNS_SERVER_ADDRESS);

    /* Check for DNS add server error. */
    if (status)
    {

        error_counter++;
        return;
     }
#endif


/********************************************************************************/
/*                                  Type AAAA                                   */
/*     Send AAAA type DNS Query to its DNS server and get the IPv6 address. */
/********************************************************************************/
#ifdef FEATURE_NX_IPV6

    /* Send a DNS Client name query. Indicate the Client expects an IPv6 address (containing an AAAA record). The DNS
       Client will send AAAA type query to its DNS server. */
    status = nxd_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ipduo_address, 400, NX_IP_VERSION_V6);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test AAAA: \n");

        printf("IP address: %x:%x:%x:%x:%x:%x:%x:%x\n",
            (UINT)host_ipduo_address.nxd_ip_address.v6[0]  >>16 & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[0]  & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[1]  >>16 & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[1]  & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[2]  >>16 & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[2]  & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[3]  >>16 & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[3]  & 0xFFFF);
    }

#endif

    /* Look up IPv6 addresses(AAAA TYPE) to record multiple IPv6 addresses in record_buffer and return the IPv6 address count. */
    status = nxd_dns_ipv6_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

    /* Check for DNS add server error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test AAAA: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the IPv6 addresses of host. */
    for(i =0; i< record_count; i++)
    {
        ipv6_address_ptr[i] = (NX_DNS_IPV6_ADDRESS *)(record_buffer + i * sizeof(NX_DNS_IPV6_ADDRESS));

        printf("record %d: IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", i,
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[0]  >>16 & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[0]  & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[1]  >>16 & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[1]  & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[2]  >>16 & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[2]  & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[3]  >>16 & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[3]  & 0xFFFF));
    }


/********************************************************************************/
/*                                  Type A                                      */
/*       Send A type DNS Query to its DNS server and get the IPv4 address. */
/********************************************************************************/
#ifdef FEATURE_NX_IPV6
    /* Send a DNS Client name query. Indicate the Client expects an IPv4 address (containing an A record). If the DNS client
       is using an IPv6 DNS server it will send this query over IPv6; otherwise it will be sent over IPv4. */
    status = nxd_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ipduo_address, 400, NX_IP_VERSION_V4);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {

        printf("------------------------------------------------------\n");
        printf("Test A: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
              host_ipduo_address.nxd_ip_address.v4 >> 24,
              host_ipduo_address.nxd_ip_address.v4 >> 16 & 0xFF,
              host_ipduo_address.nxd_ip_address.v4 >> 8 & 0xFF,
              host_ipduo_address.nxd_ip_address.v4 & 0xFF);
    }

#endif

    /* Look up an IPv4 address over IPv4. */
    status = nx_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ip_address, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test A: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }


    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test A: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the IPv4 addresses of host. */
    for(i =0; i< record_count; i++)
    {
        ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG));
        printf("record %d: IP address: %lu.%lu.%lu.%lu\n", i,
                *ipv4_address_ptr[i] >> 24,
                *ipv4_address_ptr[i] >> 16 & 0xFF,
                *ipv4_address_ptr[i] >> 8 & 0xFF,
                *ipv4_address_ptr[i] & 0xFF);
    }


/********************************************************************************/
/*                                  Type A + CNAME response                     */
/*       Send A type DNS Query to its DNS server and get the IPv4 address. */
/********************************************************************************/
    /* Look up an IPv4 address over IPv4. */
    status = nx_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ip_address, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test A + CNAME response: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }


    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test Test A + CNAME response: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the IPv4 addresses of host. */
    for(i =0; i< record_count; i++)
    {
        ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG));
        printf("record %d: IP address: %lu.%lu.%lu.%lu\n", i,
                *ipv4_address_ptr[i] >> 24,
                *ipv4_address_ptr[i] >> 16 & 0xFF,
                *ipv4_address_ptr[i] >> 8 & 0xFF,
                *ipv4_address_ptr[i] & 0xFF);
    }


/********************************************************************************/
/*                                  Type PTR                                    */
/*       Send PTR type DNS Query to its DNS server and get the host name. */
/********************************************************************************/

#ifdef FEATURE_NX_IPV6

    /* Look up a host name from an IPv6 address (reverse lookup). */

    /* Create an IPv6 address for a reverse lookup. */
    test_ipduo_server_address.nxd_ip_version = NX_IP_VERSION_V6;
    test_ipduo_server_address.nxd_ip_address.v6[0] = 0x24046800;
    test_ipduo_server_address.nxd_ip_address.v6[1] = 0x40050c00;
    test_ipduo_server_address.nxd_ip_address.v6[2] = 0x00000000;
    test_ipduo_server_address.nxd_ip_address.v6[3] = 0x00000065;

    /* This will be sent over IPv6 to the DNS server who should return a PTR record if it can find the information. */
    status = nxd_dns_host_by_address_get(&client_dns, &test_ipduo_server_address, &record_buffer[0], BUFFER_SIZE, 450);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test PTR: %s\n", record_buffer);
    }
#endif

#ifdef FEATURE_NX_IPV6

    /* Create an IPv4 address for the reverse lookup. If the DNS client is IPv6 enabled, it will send this over
       IPv6 to the DNS server; otherwise it will send it over IPv4. In either case the respective server will
       return a PTR record if it has the information. */
    test_ipduo_server_address.nxd_ip_version = NX_IP_VERSION_V4;
    test_ipduo_server_address.nxd_ip_address.v4 = IP_ADDRESS(74, 125, 71, 106);

    status = nxd_dns_host_by_address_get(&client_dns, &test_ipduo_server_address, &record_buffer[0], BUFFER_SIZE, 450);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test PTR: %s\n", record_buffer);
    }
#endif

     /* Look up host name over IPv4. */
     host_ip_address = IP_ADDRESS(74, 125, 71, 106);
     status = nx_dns_host_by_address_get(&client_dns, host_ip_address, &record_buffer[0], BUFFER_SIZE, 450);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {
        printf("------------------------------------------------------\n");
        printf("Test PTR: %s\n", record_buffer);
    }

#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
/********************************************************************************/
/*                                  Type CNAME                                  */
/*   Send CNAME type DNS Query to its DNS server and get the canonical name . */
/********************************************************************************/

     /* Send CNAME type to record the canonical name of host in record_buffer. */
     status = nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test CNAME: %s\n", record_buffer);
    }


/********************************************************************************/
/*                                  Type TXT                                    */
/*      Send TXT type DNS Query to its DNS server and get descriptive text. */
/********************************************************************************/

     /* Send TXT type to record the descriptive test of host in record_buffer. */
     status = nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test TXT: %s\n", record_buffer);
    }


/********************************************************************************/
/*                                  Type NS                                     */
/*   Send NS type DNS Query to its DNS server and get the domain name server. */
/********************************************************************************/

     /* Send NS type to record multiple name servers in record_buffer and return the name server count.
        If the DNS response includes the IPv4 addresses of name server, record it similarly in record_buffer. */
     status = nx_dns_domain_name_server_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test NS: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the name server. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)(record_buffer + i * sizeof(NX_DNS_NS_ENTRY));

        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address  >> 24,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 16 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 8 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address & 0xFF);
        if(nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr)
            printf("hostname = %s\n", nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

/********************************************************************************/
/*                                  Type MX                                     */
/*   Send MX type DNS Query to its DNS server and get the domain mail exchange. */
/********************************************************************************/

     /* Send MX DNS query type to record multiple mail exchanges in record_buffer and return the mail exchange count.
        If the DNS response includes the IPv4 addresses of mail exchange, record it similarly in record_buffer. */
     status = nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test MX: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the mail exchange. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)(record_buffer + i * sizeof(NX_DNS_MX_ENTRY));

        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);
        printf("preference = %d \n ", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);
        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

/********************************************************************************/
/*                                  Type SRV                                    */
/*  Send SRV type DNS Query to its DNS server and get the location of services. */
/********************************************************************************/

     /* Send SRV DNS query type to record the location of services in record_buffer and return count.
        If the DNS response includes the IPv4 addresses of service name, record it similarly in record_buffer. */
     status = nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test SRV: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the location of services. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)(record_buffer + i * sizeof(NX_DNS_SRV_ENTRY));

        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 24,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 16 & 0xFF,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 8 & 0xFF,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address & 0xFF);
        printf("port number = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_port_number );
        printf("priority = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_priority );
        printf("weight = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_weight );
        if(nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr)
            printf("hostname = %s\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

    /* Get the service info, NetX old API.*/
    status = nx_dns_info_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_address, &host_port, 200);

    /* Check for DNS add server error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test SRV: ");
        printf("IP address: %d.%d.%d.%d\n",
                host_address >> 24,
                host_address >> 16 & 0xFF,
                host_address >> 8 & 0xFF,
                host_address & 0xFF);
        printf("port number = %d\n", host_port);
    }

/********************************************************************************/
/*                                  Type SOA                                    */
/* Send SOA type DNS Query to its DNS server and get zone of start of authority.*/
/********************************************************************************/

     /* Send SOA DNS query type to record the zone of start of authority in record_buffer. */
     status = nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

     /* Get the loc*/
     nx_dns_soa_entry_ptr = (NX_DNS_SOA_ENTRY *) record_buffer;
     printf("------------------------------------------------------\n");
     printf("Test SOA: \n");
     printf("serial = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_serial );
     printf("refresh = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_refresh );
     printf("retry = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_retry );
     printf("expire = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_expire );
     printf("minmum = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_minmum );
     if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr)
         printf("host mname = %s\n", nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr);
     else
         printf("host mame is not set\n");
     if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr)
         printf("host rname = %s\n", nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr);
     else
         printf("host rname is not set\n");


#endif

    /* Shutting down...*/

    /* Terminate the DNS Client thread. */
    status = nx_dns_delete(&client_dns);

    return;
}
```
## <a name="configuration-options"></a><span data-ttu-id="b0797-170">構成オプション</span><span class="sxs-lookup"><span data-stu-id="b0797-170">Configuration Options</span></span>

<span data-ttu-id="b0797-171">NetX 用に DNS を構築するための構成オプションはいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="b0797-171">There are several configuration options for building DNS for NetX.</span></span> <span data-ttu-id="b0797-172">それらのオプションは *nxd_dns.h* で再設定できます。</span><span class="sxs-lookup"><span data-stu-id="b0797-172">These options can be redefined in *nxd_dns.h.*</span></span> <span data-ttu-id="b0797-173">次のリストでは各オプションを詳しく説明しています:</span><span class="sxs-lookup"><span data-stu-id="b0797-173">The following list describes each in detail:</span></span>  

- <span data-ttu-id="b0797-174">**NX_DNS_TYPE_OF_SERVICE** DNS UDP 要求に必要なサービスの種類です。</span><span class="sxs-lookup"><span data-stu-id="b0797-174">**NX_DNS_TYPE_OF_SERVICE** Type of service required for the DNS UDP requests.</span></span> <span data-ttu-id="b0797-175">既定値は、通常の IP パケット サービスの NX_IP_NORMAL です。</span><span class="sxs-lookup"><span data-stu-id="b0797-175">By default, this value is defined as NX_IP_NORMAL for normal IP packet service.</span></span>

- <span data-ttu-id="b0797-176">**NX_DNS_TIME_TO_LIVE** パケットが通過できるルーターの最大数を指定します。この数を超えるとパケットは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="b0797-176">**NX_DNS_TIME_TO_LIVE** Specifies the maximum number of routers a packet can pass before it is discarded.</span></span> <span data-ttu-id="b0797-177">既定値は 0x80 です。</span><span class="sxs-lookup"><span data-stu-id="b0797-177">The default value is 0x80.</span></span>

- <span data-ttu-id="b0797-178">**NX_DNS_FRAGMENT_OPTION** 送信パケットのフラグメント化を許可または拒否するようにソケットのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="b0797-178">**NX_DNS_FRAGMENT_OPTION** Sets the socket property to allow or disallow fragmentation of outgoing packets.</span></span> <span data-ttu-id="b0797-179">既定値は NX_DONT_FRAGMENT です。</span><span class="sxs-lookup"><span data-stu-id="b0797-179">The default value is NX_DONT_FRAGMENT.</span></span>

- <span data-ttu-id="b0797-180">**NX_DNS_QUEUE_DEPTH** ソケットの受信キューに保持できるパケットの最大数を設定します。</span><span class="sxs-lookup"><span data-stu-id="b0797-180">**NX_DNS_QUEUE_DEPTH** Sets the maximum number of packets to store on the socket receive queue.</span></span> <span data-ttu-id="b0797-181">既定値は 5 です。</span><span class="sxs-lookup"><span data-stu-id="b0797-181">The default value is 5.</span></span>

- <span data-ttu-id="b0797-182">**NX_DNS_MAX_SERVERS** クライアント サーバー リストの DNS サーバーの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="b0797-182">**NX_DNS_MAX_SERVERS** Specifies the maximum number of DNS Servers in the Client server list.</span></span> <span data-ttu-id="b0797-183">既定値は 5 です。</span><span class="sxs-lookup"><span data-stu-id="b0797-183">The default value is 5.</span></span>

- <span data-ttu-id="b0797-184">**NX_DNS_MESSAGE_MAX** DNS クエリを送信する DNS メッセージの最大サイズです。</span><span class="sxs-lookup"><span data-stu-id="b0797-184">**NX_DNS_MESSAGE_MAX** The maximum DNS message size for sending DNS queries.</span></span> <span data-ttu-id="b0797-185">既定値は 512 です。これは RFC 1035 セクション 2.3.4 で指定されている最大サイズです。</span><span class="sxs-lookup"><span data-stu-id="b0797-185">The default value is 512, which is also the maximum size specified in RFC 1035 Section 2.3.4.</span></span>

- <span data-ttu-id="b0797-186">**NX_DNS_PACKET_PAYLOAD_UNALIGNED** これを指定しない場合、クライアント パケットのペイロードのサイズに、イーサネット、IP (または IPv6)、UDP ヘッダー、NX_DNS_MESSAGE_MAX で指定された DNS メッセージの最大サイズを含むサイズを使用します。</span><span class="sxs-lookup"><span data-stu-id="b0797-186">**NX_DNS_PACKET_PAYLOAD_UNALIGNED** If not defined, the size of the Client packet payload which includes the Ethernet, IP (or IPv6), and UDP headers plus the maximum DNS message size specified by NX_DNS_MESSAGE_MAX.</span></span> <span data-ttu-id="b0797-187">指定されているかどうかにかかわらず、パケットのペイロードは 4 バイトでアラインされ NX_DNS_PACKET_PAYLOAD に保存されます。</span><span class="sxs-lookup"><span data-stu-id="b0797-187">Regardless if defined, the packet payload is the 4-byte aligned and stored in NX_DNS_PACKET_PAYLOAD.</span></span>

- <span data-ttu-id="b0797-188">**NX_DNS_PACKET_POOL_SIZE** NX_DNS_CLIENT_USER_CREATE_PACKET_POOL が指定されていない場合に、DNS クエリの送信に使用するクライアントのパケット プールのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="b0797-188">**NX_DNS_PACKET_POOL_SIZE** Size of the Client packet pool for sending DNS queries if NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is not defined.</span></span> <span data-ttu-id="b0797-189">既定値は、NX_DNS_PACKET_PAYLOAD で指定されたサイズのペイロードのパケット 16 個を処理するのに十分な大きさであり、アライメントは 4 バイトです。</span><span class="sxs-lookup"><span data-stu-id="b0797-189">The default value is large enough for 16 packets of payload size defined by NX_DNS_PACKET_PAYLOAD, and is 4-byte aligned.</span></span>

- <span data-ttu-id="b0797-190">**NX_DNS_MAX_RETRIES** DNS クライアントが現在の DNS サーバーにクエリを送信する最大回数です。この回数を超えると他のサーバーを試すか DNS クエリを破棄します。</span><span class="sxs-lookup"><span data-stu-id="b0797-190">**NX_DNS_MAX_RETRIES** The maximum number of times the DNS Client will query the current DNS server before trying another server or aborting the DNS query.</span></span> <span data-ttu-id="b0797-191">既定値は、3 です。</span><span class="sxs-lookup"><span data-stu-id="b0797-191">The default value is 3.</span></span>

- <span data-ttu-id="b0797-192">**NX_DNS_MAX_RETRANS_TIMEOUT** DNS クエリを特定の DNS サーバーに再送信する際の最長タイムアウト時間です。</span><span class="sxs-lookup"><span data-stu-id="b0797-192">**NX_DNS_MAX_RETRANS_TIMEOUT** The maximum retransmission timeout on a DNS query to a specific DNS server.</span></span> <span data-ttu-id="b0797-193">既定値は 64 秒 (64 x NX_IP_PERIODIC_RATE) です。</span><span class="sxs-lookup"><span data-stu-id="b0797-193">The default value is 64 seconds (64 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="b0797-194">**NX_DNS_IP_GATEWAY_AND_DNS_SERVER** これが指定され、かつクライアントの IPv4 ゲートウェイのアドレスが 0 以外に設定されている場合、DNS クライアントでその IPv4 ゲートウェイが優先 DNS サーバーに設定されます。</span><span class="sxs-lookup"><span data-stu-id="b0797-194">**NX_DNS_IP_GATEWAY_AND_DNS_SERVER** If defined and the Client IPv4 gateway address is non zero, the DNS Client sets the IPv4 gateway as the Client’s primary DNS server.</span></span> <span data-ttu-id="b0797-195">既定値は、無効です。</span><span class="sxs-lookup"><span data-stu-id="b0797-195">The default value is disabled.</span></span>

- <span data-ttu-id="b0797-196">**NX_DNS_PACKET_ALLOCATE_TIMEOUT** DNS クライアントのパケット プールからパケットを割り当てる際のタイムアウト オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="b0797-196">**NX_DNS_PACKET_ALLOCATE_TIMEOUT** This sets the timeout option for allocating a packet from the DNS client packet pool.</span></span> <span data-ttu-id="b0797-197">既定値は 1 秒 (1 x NX_IP_PERIODIC_RATE) です。</span><span class="sxs-lookup"><span data-stu-id="b0797-197">The default value is 1 second (1\*NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="b0797-198">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** DNS クライアントで、アプリケーションによる DNS クライアントのパケット プールの作成と設定を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b0797-198">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** This enables the DNS Client to let the application create and set the DNS Client packet pool.</span></span> <span data-ttu-id="b0797-199">このオプションは既定で無効になっており、DNS クライアントは *nx_dns_create* で独自のパケット プールを作成します。</span><span class="sxs-lookup"><span data-stu-id="b0797-199">By default this option is disabled, and the DNS Client creates its own packet pool in *nx_dns_create*.</span></span>

- <span data-ttu-id="b0797-200">**NX_DNS_CLIENT_CLEAR_QUEUE** DNS クライアントで、新しいクエリを送信する前に、受信キューの古い DNS メッセージを削除できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b0797-200">**NX_DNS_CLIENT_CLEAR_QUEUE** This enables the DNS Client to clear old DNS messages off the receive queue before sending a new query.</span></span> <span data-ttu-id="b0797-201">DNS クエリの古いパケットを削除すると、DNS クライアントのソケット キューでオーバーフローが起こることと有効なパケットが破棄されることを防止できます。</span><span class="sxs-lookup"><span data-stu-id="b0797-201">Removing these packets from previous DNS queries prevents the DNS Client socket queue from overflowing and dropping valid packets.</span></span>

- <span data-ttu-id="b0797-202">**NX_DNS_ENABLE_EXTENDED_RR_TYPES** DNS クライアントでクエリを実行できるレコードの種類を追加します (CNAME、NS、MX、SOA、SRV、TXT など)。</span><span class="sxs-lookup"><span data-stu-id="b0797-202">**NX_DNS_ENABLE_EXTENDED_RR_TYPES** This enables the DNS Client to query on additional DNS record types in (e.g. CNAME, NS, MX, SOA, SRV and TXT).</span></span>

- <span data-ttu-id="b0797-203">**NX_DNS_CACHE_ENABLE** DNS クライアントで応答レコードを DNS キャッシュに保存できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b0797-203">**NX_DNS_CACHE_ENABLE** This enables the DNS Client to store the answer records into DNS cache.</span></span>