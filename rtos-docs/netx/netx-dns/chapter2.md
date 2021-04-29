---
title: 第 2 章 - Azure RTOS NetX DNS クライアントのインストールと使用
description: この章では、Azure RTOS NetX DNS クライアントのインストール、セットアップ、使用に関するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 054b7366eb9a28bc0dc2fb8c4b2479c12532499b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811570"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dns-client"></a><span data-ttu-id="9ee63-103">第 2 章 - Azure RTOS NetX DNS クライアントのインストールと使用</span><span class="sxs-lookup"><span data-stu-id="9ee63-103">Chapter 2 - Installation and Use of Azure RTOS NetX DNS Client</span></span>

<span data-ttu-id="9ee63-104">この章では、Azure RTOS NetX DNS クライアントのインストール、セットアップ、使用に関するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX DNS Client.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="9ee63-105">製品の配布</span><span class="sxs-lookup"><span data-stu-id="9ee63-105">Product Distribution</span></span>

<span data-ttu-id="9ee63-106">NetX DNS クライアントは <https://github.com/azure-rtos/netx> で入手できます。</span><span class="sxs-lookup"><span data-stu-id="9ee63-106">The NetX DNS Client is available at <https://github.com/azure-rtos/netx>.</span></span> <span data-ttu-id="9ee63-107">パッケージには、次のファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9ee63-107">The package includes the following files:</span></span>

- <span data-ttu-id="9ee63-108">**nx_dns.h**: NetX DNS クライアントのヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="9ee63-108">**nx_dns.h**: Header file for NetX DNS Client</span></span>
- <span data-ttu-id="9ee63-109">**nx_dns.c**: NetX DNS クライアントの C 言語のソース ファイル</span><span class="sxs-lookup"><span data-stu-id="9ee63-109">**nx_dns.c**: C Source file for NetX DNS Client</span></span>
- <span data-ttu-id="9ee63-110">**nx_dns.pdf**: NetX DNS クライアントの説明書の PDF ファイル</span><span class="sxs-lookup"><span data-stu-id="9ee63-110">**nx_dns.pdf**: PDF description of NetX DNS Client</span></span>

## <a name="dns-client-installation"></a><span data-ttu-id="9ee63-111">DNS クライアントのインストール</span><span class="sxs-lookup"><span data-stu-id="9ee63-111">DNS Client Installation</span></span>

<span data-ttu-id="9ee63-112">NetX DNS クライアントを使用するには、ソース コード ファイル *nxd_dns.c* と *nxd_dns.h* を NetX がインストールされているのと同じディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="9ee63-112">To use NetX DNS Client, copy the source code files *nx_dns.c* and *nx_dns.h* to the same directory where NetX is installed.</span></span> <span data-ttu-id="9ee63-113">たとえば、NetX がディレクトリ " *\threadx\arm7\green*" にインストールされている場合は、*nx_dns.h* および *nx_dns.c* ファイルをこのディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ee63-113">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_dns.h* and *nx_dns.c* files should be copied into this directory.</span></span>

## <a name="using-the-dns-client"></a><span data-ttu-id="9ee63-114">DNS クライアントの使用</span><span class="sxs-lookup"><span data-stu-id="9ee63-114">Using the DNS Client</span></span>

<span data-ttu-id="9ee63-115">NetX DNS クライアントの使用方法は簡単です。</span><span class="sxs-lookup"><span data-stu-id="9ee63-115">Using NetX DNS Client is easy.</span></span> <span data-ttu-id="9ee63-116">基本的に、ThreadX と NetX を使用するには、アプリケーション コードに、それぞれ *tx_api.h* と *nx_api.h* をインクルードした後に *nx_dns.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ee63-116">Basically, the application code must include *nx_dns.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="9ee63-117">*nx_dns.h* をインクルードすると、このガイドで後述する DNS の関数を、そのアプリケーションのコードで呼び出せるようになります。</span><span class="sxs-lookup"><span data-stu-id="9ee63-117">Once *nx_dns.h* is included, the application code is then able to make the DNS function calls specified later in this guide.</span></span> <span data-ttu-id="9ee63-118">また、アプリケーションのビルドには *nx_dns.c* を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ee63-118">The application must also add *nx_dns.c* to the build process.</span></span> <span data-ttu-id="9ee63-119">このファイルは、他のアプリケーション ファイルと同様にコンパイルする必要があり、そのオブジェクト形式は、アプリケーションのファイルと一緒にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ee63-119">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="9ee63-120">NetX DNS を使用するために必要なことはこれだけです。</span><span class="sxs-lookup"><span data-stu-id="9ee63-120">This is all that is required to use NetX DNS.</span></span>

>[!NOTE]
> <span data-ttu-id="9ee63-121">DNS では NetX UDP のサービスを使用するため、DNS を使用するときは、前もって *nx_udp_enable* を呼び出して UDP を有効にしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ee63-121">Since DNS utilizes NetX UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DNS.</span></span>

## <a name="small-example-system-for-dns-client"></a><span data-ttu-id="9ee63-122">DNS クライアントの小規模なシステム例</span><span class="sxs-lookup"><span data-stu-id="9ee63-122">Small Example System for DNS Client</span></span> 

<span data-ttu-id="9ee63-123">このセクションで示す DNS アプリケーション プログラムの例では、6 行目で *nx_dns.h* をインクルードします。</span><span class="sxs-lookup"><span data-stu-id="9ee63-123">In the example DNS application program provided in this section, *nx_dns.h* is included at line 6.</span></span> <span data-ttu-id="9ee63-124">21 から 23 行目では NX_DNS_CLIENT_USER_CREATE_PACKET_POOL を宣言し、DNS クライアント アプリケーションが DNS クライアントのパケット プールを作成できるようにしています。</span><span class="sxs-lookup"><span data-stu-id="9ee63-124">NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, which allows the DNS Client application to create the packet pool for the DNS Client, is declared on lines 21-23.</span></span> <span data-ttu-id="9ee63-125">このパケット プールは、DNS メッセージの送信に使用するパケットを割り当てるのに使用します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-125">This packet pool is used for allocating packets for sending DNS messages.</span></span> <span data-ttu-id="9ee63-126">NX_DNS_CLIENT_USER_CREATE_PACKET_POOL が定義されている場合、71 から 91 行目でパケット プールを作成します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-126">If NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined, a packet pool is created in lines 71-91.</span></span> <span data-ttu-id="9ee63-127">このオプションが有効でない場合、DNS クライアントは、*nx_dns.h* の構成パラメーターで設定されるパケットのペイロードとパケット プールのサイズに応じて、専用のパケット プールを作成します。パケットのペイロードとパケット プールのサイズの設定については、この章の他の箇所で説明します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-127">If this option is not enabled, the DNS Client creates its own packet pool as per the packet payload and pool size set by configuration parameters in *nx_dns.h* and described elsewhere in this chapter.</span></span>

<span data-ttu-id="9ee63-128">NetX Duo の内部操作に使用するクライアントの IP インスタンスのために、93 から 105 行目でもう 1 つパケット プールを作成します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-128">Another packet pool is created in lines 93-105 for the Client IP instance which is used for internal NetX operations.</span></span> <span data-ttu-id="9ee63-129">次に、107 から 119 行目で *nx_ip_create* を呼び出して IP インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-129">Next the IP instance is created using the *nx_ip_create* call in line 107-119.</span></span> <span data-ttu-id="9ee63-130">IP タスクと DNS クライアントでは同じパケット プールを共有できますが、通常、DNS クライアントから送信されるメッセージの方が IP タスクが送信する制御パケットよりも大きいため、別々のパケット プールを使用する方が効率的にメモリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9ee63-130">It is possible for the IP task and the DNS Client to share the same packet pool, but since the DNS Client typically sends out larger messages than the control packets sent by the IP task, using separate packet pools makes more efficient use of memory.</span></span>

<span data-ttu-id="9ee63-131">122 行目と 134 行目で ARP と UDP (IPv4 ネットワークで使用) をそれぞれ有効にします。</span><span class="sxs-lookup"><span data-stu-id="9ee63-131">ARP and UDP (which is used by IPv4 networks) are enabled in lines 122 and 134 respectively.</span></span>

>[!NOTE]
> <span data-ttu-id="9ee63-132">このデモでは、37 行目で "ram" ドライバーを宣言し、*nx_ip_create* の呼び出しでこれを使用しています。</span><span class="sxs-lookup"><span data-stu-id="9ee63-132">This demo uses the ‘ram’ driver declared on line 37 and used in the *nx_ip_create* call.</span></span> <span data-ttu-id="9ee63-133">この RAM ドライバーは、NetX のソース コードと合わせて配布されています。</span><span class="sxs-lookup"><span data-stu-id="9ee63-133">This ram driver is distributed with the NetX source code.</span></span> <span data-ttu-id="9ee63-134">DNS クライアントを実行するには、実際に使用する物理ネットワーク ドライバーをアプリケーションで指定して、DNS サーバーに対しパケットを送受信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ee63-134">To actually run the DNS Client the application must supply an actual physical network driver to transmit and receive packets from the DNS server.</span></span>

<span data-ttu-id="9ee63-135">クライアント スレッド エントリ関数 *thread_client_entry* を *tx_application_define* 関数の下で定義します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-135">The Client thread entry function *thread_client_entry* is defined below the *tx_application_define* function.</span></span> <span data-ttu-id="9ee63-136">ここでは最初にシステムの制御を放棄し、ネットワーク ドライバーで IP タスク スレッドを初期化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9ee63-136">It initially relinquishes control to the system to allow the IP task thread to be initialized by the network driver.</span></span>

<span data-ttu-id="9ee63-137">次に、176 から 187 行目で DNS クライアントを作成し、189 から 200 行目でキャッシュを初期化し、202 から 217 行目で、先に作成したパケット プールを DNS クライアント インスタンスに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9ee63-137">It then creates the DNS Client on lines 176-187, initializes the cache on lines 189-200, and sets the packet pool previously created to the DNS Client instance on lines 202-217.</span></span> <span data-ttu-id="9ee63-138">次に、220 から 229 行目で IPv4 DNS サーバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-138">It then adds an IPv4 DNS server on lines 220-229.</span></span>

<span data-ttu-id="9ee63-139">サンプル プログラムの残りの部分では、DNS クライアントのサービスを使用して DNS クエリを実行しています。</span><span class="sxs-lookup"><span data-stu-id="9ee63-139">The remainder of the example program uses the DNS Client services to make DNS queries.</span></span> <span data-ttu-id="9ee63-140">240 行目と 262 行目でホストの IP アドレスの検索が実行されます。</span><span class="sxs-lookup"><span data-stu-id="9ee63-140">Host IP address lookups are performed on lines 240 and 262.</span></span> <span data-ttu-id="9ee63-141">これら 2 つのサービス (*nx_dns_host_by_name_get* と *nx_dns_ipv4_address_by_name_get*) の違いは、前者の場合 1 つの IP アドレスのみが保存されるのに対し、後者の場合は DNS サーバーから応答された場合に複数のアドレスが保存されるという点です。</span><span class="sxs-lookup"><span data-stu-id="9ee63-141">The difference between these two services, *nx_dns_host_by_name_get* and *nx_dns_ipv4_address_by_name_get*, is that the former only saves one IP address, while the latter saves multiple addresses if DNS Server replied.</span></span>

<span data-ttu-id="9ee63-142">(IP アドレスからホスト名の) 逆引き参照は、354 行目 (*nx_dns_host_by_address_get* ) で実行されます。</span><span class="sxs-lookup"><span data-stu-id="9ee63-142">Reverse lookups (host name from IP address) are performed on lines 354 (*nx_dns_host_by_address_get*).</span></span>

<span data-ttu-id="9ee63-143">375 行目と 420 行目では、別の 2 つの DNS 検索サービス CNAME と TXT を使用して、入力したドメイン名に対する CNAME と TXT を取得する方法を、それぞれ例示しています。</span><span class="sxs-lookup"><span data-stu-id="9ee63-143">Two more services for DNS lookups, CNAME and TXT, are demonstrated on lines 375 and 420 respectively, to discover CNAME and TXT for the input domain name.</span></span> <span data-ttu-id="9ee63-144">NetX DNS クライアントには、NS、MX、SRV、SOA など他の種類のレコードに対しても同様のサービスが存在します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-144">NetX DNS Client as similar services for other record types, e.g. NS, MX, SRV and SOA.</span></span> <span data-ttu-id="9ee63-145">NetX DNS クライアントで検索できるレコードの種類すべての詳しい説明については、第 3 章を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ee63-145">See Chapter 3 for detailed descriptions of all record type lookups available in NetX DNS Client.</span></span>

<span data-ttu-id="9ee63-146">594 行目で *nx_dns_delete* サービスを使用して DNS クライアントを削除するとき、専用のパケット プールを作成した場合を除き、この DNS クライアントのパケット プールは削除されません。</span><span class="sxs-lookup"><span data-stu-id="9ee63-146">When the DNS Client is deleted on line 594, using the *nx_dns_delete* service, the packet pool for the DNS Client is not deleted unless the DNS Client created its own packet pool.</span></span> <span data-ttu-id="9ee63-147">その他の場合、それ以上使用しないパケット プールを削除するかどうかはアプリケーションに任されています。</span><span class="sxs-lookup"><span data-stu-id="9ee63-147">Otherwise, it is up to the application to delete the packet pool if it has no further use for it.</span></span>

```c
/* This is a small demo of DNS Client for the high-performance NetX TCP/IP stack.*/
#include "tx_api.h"
#include "nx_api.h"
#include "nx_udp.h"
#include "nx_dns.h"

#define     DEMO_STACK_SIZE         4096
#define     NX_PACKET_PAYLOAD       1536
#define     NX_PACKET_POOL_SIZE     30 * NX_PACKET_PAYLOAD
#define     LOCAL_CACHE_SIZE        2048

/* Define the ThreadX and NetX object control blocks... */

NX_DNS             client_dns;
TX_THREAD          client_thread;
NX_IP              client_ip;
NX_PACKET_POOL     main_pool;

#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL
    NX_PACKET_POOL client_pool;
#endif

UCHAR       local_cache[LOCAL_CACHE_SIZE];
UINT        error_counter = 0;
#define     CLIENT_ADDRESS IP_ADDRESS(192,168,0,11)
#define     DNS_SERVER_ADDRESS IP_ADDRESS(192,168,0,1)

/* Define thread prototypes. */
void        thread_client_entry(ULONG thread_input);

/***** Substitute your ethernet driver entry function here *********/
extern     VOID _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Define main entry point. */
int main()
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
    /* Create the main thread. */
    tx_thread_create(&client_thread, "Client thread", 
                     thread_client_entry, 0, pointer, 
                     DEMO_STACK_SIZE, 4, 4, TX_NO_TIME_SLICE, 
                     TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL

    /*Create the packet pool for the DNS Client to send packets. If the DNS Client is configured for letting the host application create the DNS packet pool, 
        (see NX_DNS_CLIENT_USER_CREATE_PACKET_POOL option), see 77 nx_dns_create() for guidelines on packet payload size and pool size. 
        packet traffic for NetX processes.
    */

    status = nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                   NX_DNS_PACKET_PAYLOAD, pointer, 
                                   NX_DNS_PACKET_POOL_SIZE);

    pointer = pointer + NX_DNS_PACKET_POOL_SIZE;
    /* Check for pool creation error. */
    if (status)
    {
        error_counter++;
        return;
    }

#endif
/* Create the packet pool which the IP task will use to send packets. Also available to the host 94 application to send packet. */

    status = nx_packet_pool_create(&main_pool, "Main Packet Pool", 
                                   NX_PACKET_PAYLOAD, pointer, 
                                   NX_PACKET_POOL_SIZE);
    pointer = pointer + NX_PACKET_POOL_SIZE;

/* Check for pool creation error. */
    if (status)
    {
        error_counter++;
        return;
    }

/* Create an IP instance for the DNS Client. */
    status = nx_ip_create(&client_ip, "DNS Client IP Instance", 
                          CLIENT_ADDRESS, 0xFFFFFF00UL, 
                          &main_pool, _nx_ram_network_driver, 
                          pointer, 2048, 1);
    pointer = pointer + 2048;

/* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }
/* Enable ARP and supply ARP cache memory for the DNS Client IP. */
    status = nx_arp_enable(&client_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

/* Check for ARP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }
/* Enable UDP traffic because DNS is a UDP based protocol. */

    status = nx_udp_enable(&client_ip);
/* Check for UDP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

}

#define BUFFER_SIZE 200
#define RECORD_COUNT 10

/* Define the Client thread. */
void thread_client_entry(ULONG thread_input)
{
    UCHAR         record_buffer[200];
    UINT          record_count;
    UINT          status;
    ULONG         host_ip_address;
    UINT          i;
    ULONG         *ipv4_address_ptr[RECORD_COUNT];

#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
    NX_DNS_NS_ENTRY    *nx_dns_ns_entry_ptr[RECORD_COUNT];
    NX_DNS_MX_ENTRY    *nx_dns_mx_entry_ptr[RECORD_COUNT];
    NX_DNS_SRV_ENTRY    *nx_dns_srv_entry_ptr[RECORD_COUNT];
    NX_DNS_SOA_ENTRY    *nx_dns_soa_entry_ptr;
    ULONG                host_address;
    USHORT               host_port;
#endif

    /* Give NetX IP task a chance to get initialized . */
    tx_thread_sleep(100);
    /* Create a DNS instance for the Client. Note this function will create the DNS Client packet pool for creating DNS message packets intended for querying its DNS server. */
    status = nx_dns_create(&client_dns, &client_ip, (UCHAR *)"DNS Client");

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

    /* Yes, use the packet pool created above which has appropriate payload size for DNS messages. */
    status = nx_dns_packet_pool_set(&client_dns, &client_pool);
    /* Check for set DNS packet pool error. */
        
    if (status)
    {
        error_counter++;
        return;
    }
#endif /* NX_DNS_CLIENT_USER_CREATE_PACKET_POOL */

    /* Add an IPv4 server address to the Client list. */
    status = nx_dns_server_add(&client_dns, DNS_SERVER_ADDRESS);
    /* Check for DNS add server error. */
    if (status)
    {
        error_counter++;
        return;
    }
/********************************************************************************/
/* Type A */
/* Send A type DNS Query to its DNS server and get the IPv4 address. */
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
        printf("------------------------------------------------------> n");
        printf("Test A: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }
    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, &record_count, 400);
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
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
/* Type A + CNAME response */
/* Send A type DNS Query to its DNS server and get the IPv4 address. */
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
        printf("------------------------------------------------------> n");
        printf("Test A + CNAME response: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }

    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, 
                                             &record_count, 400);
    
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
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
/* Type PTR */
/* Send PTR type DNS Query to its DNS server and get the host name. */
/********************************************************************************/

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
        printf("------------------------------------------------------> n");
        printf("Test PTR: %s\n", record_buffer);
    }

#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
/********************************************************************************/
/* Type CNAME */
/* Send CNAME type DNS Query to its DNS server and get the canonical name . */
/********************************************************************************/

    /* Send CNAME type to record the canonical name of host in record_buffer. */

    status = nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com", 
                              &record_buffer[0], BUFFER_SIZE, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test CNAME: %s\n", record_buffer);
    }
/********************************************************************************/
/* Type TXT */
/* Send TXT type DNS Query to its DNS server and get descriptive text. */
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
        printf("------------------------------------------------------> n");
        printf("Test TXT: %s\n", record_buffer);
    }

/********************************************************************************/
/* Type NS */
/* Send NS type DNS Query to its DNS server and get the domain name server. */
/********************************************************************************/

    /* Send NS type to record multiple name servers in record_buffer and return the name server count. If the DNS response includes the IPv4 addresses of name server, record it similarly in record_buffer. */

    status = nx_dns_domain_name_server_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                           &record_buffer[0], BUFFER_SIZE, 
                                           &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test NS: ");
        printf("record_count = %d \n", record_count);
    }
    /* Get the name server. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)(record_buffer + i * sizeof(NX_DNS_NS_ENTRY));
        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 24,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 16 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 8 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address & 0xFF);
        
        if(nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr)
            printf("hostname = %s\n", nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

/********************************************************************************/
/* Type MX */
/* Send MX type DNS Query to its DNS server and get the domain mail exchange. */
/********************************************************************************/

    /* Send MX DNS query type to record multiple mail exchanges in record_buffer and return the mail exchange count. If the DNS response includes the IPv4 addresses of mail exchange, record it similarly in record_buffer. */

    status = nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
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
/* Type SRV */
/* Send SRV type DNS Query to its DNS server and get the location of services. */
/********************************************************************************/

    /* Send SRV DNS query type to record the location of services in record_buffer and return count. If the DNS response includes the IPv4 addresses of service name, record it similarly in record_buffer. */

    status = nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                       &record_buffer[0], BUFFER_SIZE, &record_count, 400);
    
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
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
    status = nx_dns_info_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                     &host_address, &host_port, 200);
    /* Check for DNS add server error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test SRV: ");
        printf("IP address: %d.%d.%d.%d\n",
                host_address >> 24,
                host_address >> 16 & 0xFF,
                host_address >> 8 & 0xFF,
                host_address & 0xFF);
        printf("port number = %d\n", host_port);
    }
    
/********************************************************************************/
/* Type SOA */
/* Send SOA type DNS Query to its DNS server and get zone of start of authority.*/
/********************************************************************************/

    /* Send SOA DNS query type to record the zone of start of authority in record_buffer. */

    status = nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    
    /* Get the loc*/
    nx_dns_soa_entry_ptr = (NX_DNS_SOA_ENTRY *) record_buffer;
    printf("------------------------------------------------------> n");
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

## <a name="configuration-options"></a><span data-ttu-id="9ee63-148">構成オプション</span><span class="sxs-lookup"><span data-stu-id="9ee63-148">Configuration Options</span></span>

<span data-ttu-id="9ee63-149">NetX 用に DNS を構築するための構成オプションはいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="9ee63-149">There are several configuration options for building DNS for NetX.</span></span> <span data-ttu-id="9ee63-150">それらのオプションは *nx_dns.h* で再設定できます。</span><span class="sxs-lookup"><span data-stu-id="9ee63-150">These options can be redefined in *nx_dns.h.*</span></span> <span data-ttu-id="9ee63-151">次の一覧で、それぞれについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-151">The following list describes each in detail:</span></span>  

- <span data-ttu-id="9ee63-152">**NX_DNS_TYPE_OF_SERVICE**: DNS UDP 要求に必要なサービスの種類です。</span><span class="sxs-lookup"><span data-stu-id="9ee63-152">**NX_DNS_TYPE_OF_SERVICE**: Type of service required for the DNS UDP requests.</span></span> <span data-ttu-id="9ee63-153">既定値は、通常の IP パケット サービスを表す NX_IP_NORMAL です。</span><span class="sxs-lookup"><span data-stu-id="9ee63-153">By default, this value is defined as NX_IP_NORMAL for normal IP packet service.</span></span>

- <span data-ttu-id="9ee63-154">**NX_DNS_TIME_TO_LIVE**: パケットが通過できるルーターの最大数を指定します。この数を超えるとパケットは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="9ee63-154">**NX_DNS_TIME_TO_LIVE**: Specifies the maximum number of routers a packet can pass before it is discarded.</span></span> <span data-ttu-id="9ee63-155">既定値は 0x80 です。</span><span class="sxs-lookup"><span data-stu-id="9ee63-155">The default value is 0x80</span></span>

- <span data-ttu-id="9ee63-156">**NX_DNS_FRAGMENT_OPTION**: 送信パケットのフラグメント化を許可または拒否するようにソケットのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-156">**NX_DNS_FRAGMENT_OPTION**: Sets the socket property to allow or disallow fragmentation of outgoing packets.</span></span> <span data-ttu-id="9ee63-157">既定値は NX_DONT_FRAGMENT です。</span><span class="sxs-lookup"><span data-stu-id="9ee63-157">The default value is NX_DONT_FRAGMENT.</span></span>

- <span data-ttu-id="9ee63-158">**NX_DNS_QUEUE_DEPTH**: ソケットの受信キューに保持できるパケットの最大数を設定します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-158">**NX_DNS_QUEUE_DEPTH**: Sets the maximum number of packets to store on the socket receive queue.</span></span> <span data-ttu-id="9ee63-159">既定値は 5 です。</span><span class="sxs-lookup"><span data-stu-id="9ee63-159">The default value is 5.</span></span>

- <span data-ttu-id="9ee63-160">**NX_DNS_MAX_SERVERS**: クライアント サーバー リストの DNS サーバーの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-160">**NX_DNS_MAX_SERVERS**: Specifies the maximum number of DNS Servers in the Client server list.</span></span>

- <span data-ttu-id="9ee63-161">**NX_DNS_MESSAGE_MAX**: DNS クエリを送信する DNS メッセージの最大サイズです。</span><span class="sxs-lookup"><span data-stu-id="9ee63-161">**NX_DNS_MESSAGE_MAX**: The maximum DNS message size for sending DNS queries.</span></span> <span data-ttu-id="9ee63-162">既定値は 512 です。これは RFC 1035 セクション 2.3.4 で指定されている最大サイズです。</span><span class="sxs-lookup"><span data-stu-id="9ee63-162">The default value is 512, which is also the maximum size specified in RFC 1035 Section 2.3.4.</span></span>

- <span data-ttu-id="9ee63-163">**NX_DNS_PACKET_PAYLOAD_UNALIGNED**: これを指定しない場合、クライアント パケットのペイロードのサイズに、イーサネット、IP (または IPv6)、UDP ヘッダー、NX_DNS_MESSAGE_MAX で指定された DNS メッセージの最大サイズを含むサイズを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-163">**NX_DNS_PACKET_PAYLOAD_UNALIGNED**: If not defined, the size of the Client packet payload which includes the Ethernet, IP (or IPv6), and UDP headers plus the maximum DNS message size specified by NX_DNS_MESSAGE_MAX.</span></span> <span data-ttu-id="9ee63-164">指定されているかどうかにかかわらず、パケットのペイロードは 4 バイトでアラインされ NX_DNS_PACKET_PAYLOAD に保存されます。</span><span class="sxs-lookup"><span data-stu-id="9ee63-164">Regardless if defined, the packet payload is the 4-byte aligned and stored in NX_DNS_PACKET_PAYLOAD.</span></span>

- <span data-ttu-id="9ee63-165">**NX_DNS_PACKET_POOL_SIZE**: NX_DNS_CLIENT_USER_CREATE_PACKET_POOL が指定されていない場合に、DNS クエリの送信に使用するクライアントのパケット プールのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-165">**NX_DNS_PACKET_POOL_SIZE**: Size of the Client packet pool for sending DNS queries if NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is not defined.</span></span> <span data-ttu-id="9ee63-166">既定値は、NX_DNS_PACKET_PAYLOAD で指定されたサイズのペイロードのパケット 16 個を処理するのに十分な大きさであり、アライメントは 4 バイトです。</span><span class="sxs-lookup"><span data-stu-id="9ee63-166">The default value is large enough for 16 packets of payload size defined by NX_DNS_PACKET_PAYLOAD, and is 4-byte aligned.</span></span>

- <span data-ttu-id="9ee63-167">**NX_DNS_MAX_RETRIES**: DNS クライアントが現在の DNS サーバーにクエリを送信する最大回数です。この回数を超えると他のサーバーを試すか DNS クエリを破棄します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-167">**NX_DNS_MAX_RETRIES**: The maximum number of times the DNS Client will query the current DNS server before trying another server or aborting the DNS query.</span></span>

- <span data-ttu-id="9ee63-168">**NX_DNS_MAX_RETRANS_TIMEOUT**: DNS クエリを特定の DNS サーバーに再送信する際の最長タイムアウト時間です。</span><span class="sxs-lookup"><span data-stu-id="9ee63-168">**NX_DNS_MAX_RETRANS_TIMEOUT**: The maximum retransmission timeout on a DNS query to a specific DNS server.</span></span> <span data-ttu-id="9ee63-169">既定値は 64 秒 (64 \*NX_IP_PERIODIC_RATE) です。</span><span class="sxs-lookup"><span data-stu-id="9ee63-169">The default value is 64 seconds (64 \*NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="9ee63-170">**NX_DNS_IP_GATEWAY_AND_DNS_SERVER**: これが指定され、かつクライアントの IPv4 ゲートウェイのアドレスが 0 以外に設定されている場合、DNS クライアントでその IPv4 ゲートウェイが優先 DNS サーバーに設定されます。</span><span class="sxs-lookup"><span data-stu-id="9ee63-170">**NX_DNS_IP_GATEWAY_AND_DNS_SERVER**: If defined and the Client IPv4 gateway address is non zero, the DNS Client sets the IPv4 gateway as the Client’s primary DNS server.</span></span> <span data-ttu-id="9ee63-171">既定値は、無効です。</span><span class="sxs-lookup"><span data-stu-id="9ee63-171">The default value is disabled.</span></span>

- <span data-ttu-id="9ee63-172">**NX_DNS_PACKET_ALLOCATE_TIMEOUT**: DNS クライアントのパケット プールからパケットを割り当てる際のタイムアウト オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-172">**NX_DNS_PACKET_ALLOCATE_TIMEOUT**: This sets the timeout option for allocating a packet from the DNS client packet pool.</span></span> <span data-ttu-id="9ee63-173">既定値は 1 秒 (1\*NX_IP_PERIODIC_RATE) です。</span><span class="sxs-lookup"><span data-stu-id="9ee63-173">The default value is 1 second (1\*NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="9ee63-174">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL**: DNS クライアントで、アプリケーションによる DNS クライアントのパケット プールの作成と設定を有効にします。</span><span class="sxs-lookup"><span data-stu-id="9ee63-174">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL**: This enables the DNS Client to let the application create and set the DNS Client packet pool.</span></span> <span data-ttu-id="9ee63-175">このオプションは既定で無効になっており、DNS クライアントは *nx_dns_create* で独自のパケット プールを作成します。</span><span class="sxs-lookup"><span data-stu-id="9ee63-175">By default this option is disabled, and the DNS Client creates its own packet pool in *nx_dns_create*.</span></span>

- <span data-ttu-id="9ee63-176">**NX_DNS_CLIENT_CLEAR_QUEUE**: DNS クライアントで、新しいクエリを送信する前に、受信キューの古い DNS メッセージを削除できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9ee63-176">**NX_DNS_CLIENT_CLEAR_QUEUE**: This enables the DNS Client to clear old DNS messages off the receive queue before sending a new query.</span></span> <span data-ttu-id="9ee63-177">DNS クエリの古いパケットを削除すると、DNS クライアントのソケット キューでオーバーフローが起こることと有効なパケットが破棄されることを防止できます。</span><span class="sxs-lookup"><span data-stu-id="9ee63-177">Removing these packets from previous DNS queries prevents the DNS Client socket queue from overflowing and dropping valid packets.</span></span>

- <span data-ttu-id="9ee63-178">**NX_DNS_ENABLE_EXTENDED_RR_TYPES**: DNS クライアントでクエリを実行できるレコードの種類を追加します (CNAME、NS、MX、SOA、SRV、TXT など)。</span><span class="sxs-lookup"><span data-stu-id="9ee63-178">**NX_DNS_ENABLE_EXTENDED_RR_TYPES**: This enables the DNS Client to query on additional DNS record types in (e.g. CNAME, NS, MX, SOA, SRV and TXT).</span></span>

- <span data-ttu-id="9ee63-179">**NX_DNS_CACHE_ENABLE**: DNS クライアントで応答レコードを DNS キャッシュに保存できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9ee63-179">**NX_DNS_CACHE_ENABLE**: This enables the DNS Client to store the answer records into DNS cache.</span></span>
