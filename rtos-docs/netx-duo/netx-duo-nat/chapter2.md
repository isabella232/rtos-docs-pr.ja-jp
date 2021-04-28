---
title: 第 2 章 - NAT のインストールと使用
description: この章では、NetX Duo NAT サービスのインストール、設定、および使用法について説明します。
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 47816c8a62aed9e2b096b121d1676c66178ad825
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810679"
---
# <a name="chapter-2---installation-and-use-of-nat"></a><span data-ttu-id="cf918-103">第 2 章 - NAT のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="cf918-103">Chapter 2 - Installation and use of NAT</span></span>

<span data-ttu-id="cf918-104">この章では、NetX Duo NAT サービスのインストール、設定、および使用法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf918-104">This chapter contains a description how to install, set up, and use the NetX Duo NAT services.</span></span>

## <a name="netx-duo-nat-installation"></a><span data-ttu-id="cf918-105">NetX Duo NAT のインストール</span><span class="sxs-lookup"><span data-stu-id="cf918-105">NetX Duo NAT Installation</span></span>

<span data-ttu-id="cf918-106">NetX Duo NAT は [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="cf918-106">NetX Duo NAT is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="cf918-107">NetX Duo NAT パッケージには、以下に示すように、1 つのソース ファイル、1 つのヘッダー ファイル、デモンストレーション アプリケーション ファイル、およびこのドキュメントの PDF ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cf918-107">The NetX Duo NAT package includes one source file and one header file, a demonstration application file, and a PDF file for this document, as follows:</span></span>

- <span data-ttu-id="cf918-108">**nx_nat.c**: NetX Duo NAT の C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="cf918-108">**nx_nat.c** C Source file for NetX Duo NAT</span></span>
- <span data-ttu-id="cf918-109">**nx_nat.h**: NetX Duo NAT の C ヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="cf918-109">**nx_nat.h** C Header file for NetX Duo NAT</span></span>
- <span data-ttu-id="cf918-110">**demo_netx_nat.c**: サンプルのホスト NetX Duo C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="cf918-110">**demo_netx_nat.c** Example host NetX Duo C source file</span></span>
- <span data-ttu-id="cf918-111">**nx_nat.docx**: NetX Duo NAT ユーザー ガイドの説明 (このドキュメント)</span><span class="sxs-lookup"><span data-stu-id="cf918-111">**nx_nat.docx** Description of the NetX Duo NAT User Guide (this document)</span></span>

<span data-ttu-id="cf918-112">NetX Duo NAT ソース コード ファイルを、NetX Duo と ThreadX がインストールされているのと同じディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="cf918-112">Copy the NetX Duo NAT source code files to the same directory where NetX Duo and ThreadX are installed.</span></span> <span data-ttu-id="cf918-113">たとえば、NetX Duo と ThreadX が " *\threadx\mcf5485\green*" ディレクトリにインストールされている場合は、"*nx_nat.c*、*nx_nat.h、および変更した NetX Duo ファイル*" をこのディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf918-113">For example, if NetX Duo and ThreadX are installed in the directory “*\threadx\mcf5485\green*” then *nx_nat.c*, *nx_nat.h and the modified NetX Duo files* should be copied into this directory.</span></span> <span data-ttu-id="cf918-114">変更した NetX Duo ファイルを既存の NetX Duo ファイルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="cf918-114">Copy the modified NetX Duo files over the existing NetX Duo files.</span></span> <span data-ttu-id="cf918-115">同様に、イーサネット コントローラー ドライバー ファイルをこのディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="cf918-115">Copy the Ethernet controller driver files into this directory as well.</span></span>

<span data-ttu-id="cf918-116">NetX Duo NAT アプリケーションを構築するには:</span><span class="sxs-lookup"><span data-stu-id="cf918-116">To build a NetX Duo NAT application:</span></span>

- <span data-ttu-id="cf918-117">NetX Duo ライブラリ *nxduo.a* は、NX_NAT_ENABLED を定義して構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf918-117">The NetX Duo library *nxduo.a* must be built with NX_NAT_ENABLED defined.</span></span> <span data-ttu-id="cf918-118">これは *nx_user.h* 内で行います (*nx_user.h* の構成オプションがビルドに含まれるように NX_INCLUDE_USER_DEFINE_FILE も定義されていることを確認してください)。</span><span class="sxs-lookup"><span data-stu-id="cf918-118">This can be done in *nx_user.h*, (make sure NX_INCLUDE_USER_DEFINE_FILE is also defined to ensure that configuration options in *nx_user.h* are included in the build.</span></span>
- <span data-ttu-id="cf918-119">アプリケーション プロジェクトでは、*nx_nat.h* を、*tx_api.h* と *nx_api.h* の後にインクルードする必要があります。ThreadX および NetX Duo サービスを使用するには、後者の 2 つのヘッダー ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="cf918-119">The application project must include *nx_nat.h* after *tx_api.h* and *nx_api.h. The latter two header files are necessary* to use ThreadX and NetX Duo services.</span></span>
- <span data-ttu-id="cf918-120">次に、アプリケーションは、*nx_nat_enable* サービスを使用して、以前に作成された IP インスタンスで NAT を有効にします。</span><span class="sxs-lookup"><span data-stu-id="cf918-120">The application then enables NAT on a previously created IP instance using the *nx_nat_enable* service.</span></span>
- <span data-ttu-id="cf918-121">アプリケーション コードでは、*nx_nat_enable* および *nx_nat_disable* サービスを呼び出すことによって、NAT を動的に有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="cf918-121">The application code can dynamically enable/disable NAT by calling the *nx_nat_enable* and *nx_nat_disable* service.</span></span>
- <span data-ttu-id="cf918-122">アプリケーション プロジェクト コードは、実行可能ファイルを作成するために、コンパイルされ、NAT が有効になっている NetX Duo ライブラリとリンクされます。</span><span class="sxs-lookup"><span data-stu-id="cf918-122">The application project code is compiled and linked with the NAT enabled NetX Duo library to create the executable.</span></span>
- <span data-ttu-id="cf918-123">TCP、UDP、または ICMP プロトコルを使用した NAT 接続をサポートするには、そのプロトコルをサポートするために NetX Duo を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf918-123">To support NAT connections using TCP, UDP or ICMP protocols, NetX Duo must be enabled to support that protocol.</span></span> <span data-ttu-id="cf918-124">これを行うには、前に作成した IP インスタンスに対して "*nx_tcp_enable、x_udp_enable*"、および *nx_icmp_enable* をそれぞれ呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cf918-124">This is done by calling *nx_tcp_enable, nx_udp_enable* and *nx_icmp_enable* for the previously created IP instance respectively.</span></span>

## <a name="small-example-demo-nat-setup"></a><span data-ttu-id="cf918-125">小さなデモンストレーション NAT 設定の例</span><span class="sxs-lookup"><span data-stu-id="cf918-125">Small Example Demo NAT Setup</span></span>

<span data-ttu-id="cf918-126">アプリケーションが NetX Duo NAT を設定する方法の例を、次の図 4 の *tx_application_define* 関数に示します。</span><span class="sxs-lookup"><span data-stu-id="cf918-126">An example of how an application sets up NetX Duo NAT is shown in the *tx_application_define* function in Figure 4 below.</span></span> <span data-ttu-id="cf918-127">インストール CD で配布されるほとんどの NetX Duo デモンストレーション ファイルとは異なり、このデモンストレーションは、仮想ネットワーク ドライバー *_nx_ram_network_driver*() が使用された Windows PC ではなく、2 つのイーサネット コントローラーを備えた実際のプロセッサ ボード上で動作します。</span><span class="sxs-lookup"><span data-stu-id="cf918-127">Unlike most NetX Duo demo files distributed on the installation CD, this demo runs on an actual processor board with two Ethernet controllers, instead of a Windows PC using the virtual network driver *_nx_ram_network_driver*().</span></span> <span data-ttu-id="cf918-128">NAT デバイスは、ローカル インターフェイスのローカル スイッチを介してローカル ドメインに接続され、外部インターフェイスの 2 番目のスイッチを介して外部ネットワークに接続されます。</span><span class="sxs-lookup"><span data-stu-id="cf918-128">The NAT device is connected to the local domain through a local switch on its local interface, and to the external network through second switch on its external interface.</span></span>

<span data-ttu-id="cf918-129">NetX Duo の基本構成は demo_netx_nat.c に示されています。</span><span class="sxs-lookup"><span data-stu-id="cf918-129">NetXDuo basic configuration is shown in demo_netx_nat.c.</span></span> <span data-ttu-id="cf918-130">プライベート ネットワークは、192.168.2.xx として定義され、2 つのローカル ホスト ノードを含みます。</span><span class="sxs-lookup"><span data-stu-id="cf918-130">The private network is defined as 192.168.2.xx and has two local host nodes.</span></span> <span data-ttu-id="cf918-131">グローバル ネットワークは、192.168.0.xx として定義され、ネットワーク外パケットのゲートウェイを 192.168.0.1 として定義します。</span><span class="sxs-lookup"><span data-stu-id="cf918-131">The global network is defined as 192.168.0.xx and defines its gateway for out of network packets as 192.168.0.1.</span></span> <span data-ttu-id="cf918-132">NetX Duo IP インスタンスは、118 から 171 行目で作成され、"RAM" ドライバーを呼び出します。2 つのインターフェイスが接続された nat_ip インスタンスは NAT ルーターとして機能し、1 つのインターフェイスが接続された local_ip インスタンスはローカル ホストとして機能します。1 つのインターフェイスが接続された external_ip インスタンスは、外部ホストとして機能します。</span><span class="sxs-lookup"><span data-stu-id="cf918-132">The NetX Duo IP instances are created on lines 118-171 and invoke the ‘ram’ driver; nat_ip instance attached two interfaces act as an NAT router, local_ip instance attached on interface act as local host; external_ip instance attached one interface act as external host.</span></span>

<span data-ttu-id="cf918-133">252 行目で NAT が作成され、動的変換エントリを格納するためのキャッシュが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="cf918-133">The NAT is created in line 252 and invokes the cache to store dynamic translation entries.</span></span> <span data-ttu-id="cf918-134">319 行目で NAT 機能が有効にされます。362 行目で静的変換エントリ (受信エントリ) が作成され、外部ホストがローカル ホストにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="cf918-134">Enable the NAT feature in line319, static translation entrie (inbound entry) is created in lines 362 to allow external host to access to local host.</span></span>

```C
/*
   demo_netx_nat.c

   This is a small demo of NAT (Network Address Translation) on the high-performance
   NetX TCP/IP stack.  This demo relies on ThreadX, NetX and NAT APIs to perform network
   address translation for IP packets traveling between private and external networks.
   this demo concentrates on the ICMP ping operation.
*/

#include   "tx_api.h"
#include   "nx_api.h"
#include   "nx_nat.h"

extern void    test_control_return(UINT status);
#if defined NX_NAT_ENABLE && defined __PRODUCT_NETXDUO__ && (NX_MAX_PHYSICAL_INTERFACES >= 2)

#define     DEMO_STACK_SIZE         2048

/* Define the ThreadX and NetX object control blocks...  */

static TX_THREAD                    ntest_0;

/* Set up the NAT components. */

/* Create a NAT instance, packet pool and translation table. */

NX_NAT_DEVICE                       nat_server;
NX_IP                               nat_ip;
NX_IP                               local_ip;
NX_IP                               external_ip;
NX_PACKET_POOL                      nat_packet_pool;
UINT                                error_counter = 0;


/* Configure the NAT network parameters. */

/* Set NetX IP packet pool packet size. This should be less than the Maximum Transmit Unit (MTU) of
   the driver (allow enough room for the Ethernet header plus padding bytes for frame alignment).  */
#define NX_NAT_PACKET_SIZE                          1536


/* Set the size of the NAT IP packet pool.  */
#define NX_NAT_PACKET_POOL_SIZE                     (NX_NAT_PACKET_SIZE * 10)

/* Set NetX IP helper thread stack size. */
#define NX_NAT_IP_THREAD_STACK_SIZE                 2048

/* Set the server IP thread priority */
#define NX_NAT_IP_THREAD_PRIORITY                   2

/* Set ARP cache size of a NAT ip instance. */
#define NX_NAT_ARP_CACHE_SIZE                       1024

/* Set NAT entries memory size. */
#define NX_NAT_ENTRY_CACHE_SIZE                     1024

/* Define NAT IP addresses, local host private IP addresses and external host IP address. */
#define NX_NAT_LOCAL_IPADR              (IP_ADDRESS(192, 168, 2, 1))
#define NX_NAT_LOCAL_HOST1              (IP_ADDRESS(192, 168, 2, 3))
#define NX_NAT_LOCAL_HOST2              (IP_ADDRESS(192, 168, 2, 10))
#define NX_NAT_LOCAL_GATEWAY            (IP_ADDRESS(192, 168, 2, 1))
#define NX_NAT_LOCAL_NETMASK            (IP_ADDRESS(255, 255, 255, 0))
#define NX_NAT_EXTERNAL_IPADR           (IP_ADDRESS(192, 168, 0, 10))
#define NX_NAT_EXTERNAL_HOST            (IP_ADDRESS(192, 168, 0, 100))
#define NX_NAT_EXTERNAL_GATEWAY         (IP_ADDRESS(192, 168, 0, 1))
#define NX_NAT_EXTERNAL_NETMASK         (IP_ADDRESS(255, 255, 255, 0))

/* Create NAT structures for creating NAT tables with static
   entries for local server hosts. */
NX_NAT_TRANSLATION_ENTRY            server_inbound_entry_icmp;

/* Define thread prototypes.  */
static void     ntest_0_entry(ULONG thread_input);
extern void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point.  */

int main()
{

    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{

    UINT     status;
    UCHAR    *pointer;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Setup the pointer to unallocated memory.  */
    pointer =  (UCHAR *) first_unused_memory;

    /* Create the main thread.  */
    tx_thread_create(&ntest_0, "thread 0", ntest_0_entry, 0,
                     pointer, DEMO_STACK_SIZE,
                     4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Create NAT packet pool. */
    status =  nx_packet_pool_create(&nat_packet_pool, "NAT Packet Pool",
                                    NX_NAT_PACKET_SIZE, pointer,
                                    NX_NAT_PACKET_POOL_SIZE);

    /* Update pointer to unallocated (free) memory. */
    pointer = pointer + NX_NAT_PACKET_POOL_SIZE;

    /* Check status.  */
    if (status)
        return;

    /* Create IP instances for NAT server (global network) */
    status = nx_ip_create(&nat_ip, "NAT IP Instance", NX_NAT_EXTERNAL_IPADR, NX_NAT_EXTERNAL_NETMASK,
                          &nat_packet_pool, _nx_ram_network_driver, pointer,
                          NX_NAT_IP_THREAD_STACK_SIZE, NX_NAT_IP_THREAD_PRIORITY);

    /* Update pointer to unallocated (free) memory. */
    pointer =  pointer + NX_NAT_IP_THREAD_STACK_SIZE;

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Set the private interface(private network).  */
    status += nx_ip_interface_attach(&nat_ip, "Private Interface", NX_NAT_LOCAL_IPADR,
        NX_NAT_LOCAL_NETMASK, _nx_ram_network_driver);

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create IP instances for Local network IP instance */
    status = nx_ip_create(&local_ip, "Local IP Instance", NX_NAT_LOCAL_HOST1, NX_NAT_LOCAL_NETMASK,
                          &nat_packet_pool, _nx_ram_network_driver, pointer,
                          NX_NAT_IP_THREAD_STACK_SIZE, NX_NAT_IP_THREAD_PRIORITY);

    /* Update pointer to unallocated (free) memory. */
    pointer =  pointer + NX_NAT_IP_THREAD_STACK_SIZE;

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create IP instances for external network IP instance */
    status = nx_ip_create(&external_ip, "External IP Instance", NX_NAT_EXTERNAL_HOST,
                        NX_NAT_EXTERNAL_NETMASK,
                        &nat_packet_pool, _nx_ram_network_driver, pointer,
                        NX_NAT_IP_THREAD_STACK_SIZE, NX_NAT_IP_THREAD_PRIORITY);

    /* Update pointer to unallocated (free) memory. */
    pointer =  pointer + NX_NAT_IP_THREAD_STACK_SIZE;

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Set the global network gateway for NAT IP instance.  */
    status = nx_ip_gateway_address_set(&nat_ip, NX_NAT_EXTERNAL_GATEWAY);

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Set the global network gateway for Local IP instance.  */
    status = nx_ip_gateway_address_set(&local_ip, NX_NAT_LOCAL_GATEWAY);

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Set the global network gateway for External IP instance.  */
    status = nx_ip_gateway_address_set(&external_ip, NX_NAT_EXTERNAL_GATEWAY);

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }


    /* Enable ARP and supply ARP cache memory for NAT IP isntance. */
    status =  nx_arp_enable(&nat_ip, (void **) pointer,
                            NX_NAT_ARP_CACHE_SIZE);

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    pointer = pointer + NX_NAT_ARP_CACHE_SIZE;

    /* Enable ARP and supply ARP cache memory for Local IP isntance. */
    status =  nx_arp_enable(&local_ip, (void **) pointer,
                            NX_NAT_ARP_CACHE_SIZE);

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    pointer = pointer + NX_NAT_ARP_CACHE_SIZE;

    /* Enable ARP and supply ARP cache memory for External IP isntance. */
    status =  nx_arp_enable(&external_ip, (void **) pointer,
                            NX_NAT_ARP_CACHE_SIZE);

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    pointer = pointer + NX_NAT_ARP_CACHE_SIZE;

    /* Enable ICMP. */
    nx_icmp_enable(&nat_ip);
    nx_icmp_enable(&local_ip);
    nx_icmp_enable(&external_ip);

    /* Create a NetX NAT server and cache with a global interface index.  */
    status =  nx_nat_create(&nat_server, &nat_ip, 0, pointer, NX_NAT_ENTRY_CACHE_SIZE);

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    pointer = pointer + NX_NAT_ENTRY_CACHE_SIZE;
}

/* Define the test threads.  */

static void    ntest_0_entry(ULONG thread_input)
{

UINT        status;
NX_PACKET   *my_packet;

    /***********************************/
    /*       Disable NAT feature       */
    /***********************************/
    /* Local Host ping External Host address.  */
    status =  nx_icmp_ping(&local_ip, NX_NAT_EXTERNAL_HOST,
        "ABCDEFGHIJKLMNOPQRSTUVWXYZ", 28, &my_packet, 100);

    /* Check status.  */
    if (status == NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Check the NAT forwarded count.  */
#ifndef NX_DISABLE_NAT_INFO
    if ((nat_server.forwarded_packets_received != 0) ||
        (nat_server.forwarded_packets_sent != 0) ||
        (nat_server.arded_packets_dropped != 0))
    {
        error_counter++;
        return;
    }
#endif

    /* External Host ping NAT External address, NAT IP instance will response the requet.  */
    status = nx_icmp_ping(&external_ip, NX_NAT_EXTERNAL_IPADR,
        "ABCDEFGHIJKLMNOPQRSTUVWXYZ", 28, &my_packet, 100);

    /* Check status.  */
    if ((status != NX_SUCCESS) || (my_packet == NX_NULL) || (my_packet -> nx_packet_length != 28))
    {
        error_counter++;
        return;

    /* Check the NAT forwarded count.  */
#ifndef NX_DISABLE_NAT_INFO
    if ((nat_server.forwarded_packets_received != 0) ||
        (nat_server.forwarded_packets_sent != 0) ||
        (nat_server.arded_packets_dropped != 0))
    {
        error_counter++;
        return;
    }
#endif
    }

    /***********************************/
    /*       Enable NAT feature        */
    /***********************************/

    /* Enable the NAT service.  */
    nx_nat_enable(&nat_server);

    /* Local Host ping External Host address.  */
    status =  nx_icmp_ping(&local_ip, NX_NAT_EXTERNAL_HOST,
        "ABCDEFGHIJKLMNOPQRSTUVWXYZ", 28, &my_packet, 100);

    if ((status != NX_SUCCESS) || (my_packet == NX_NULL) || (my_packet -> nx_packet_length != 28))
    {
        error_counter++;
        return;
    }

    /* Check the NAT forwarded count.  */
#ifndef NX_DISABLE_NAT_INFO
    if ((nat_server.forwarded_packets_received != 2) ||
        (nat_server.forwarded_packets_sent != 2) ||
        (nat_server.arded_packets_dropped != 0))
    {
        error_counter++;
        return;
    }
#endif

    /* External Host ping NAT External address, NAT IP instance will response the requet.  */
    status =  nx_icmp_ping(&external_ip, NX_NAT_EXTERNAL_IPADR,
        "ABCDEFGHIJKLMNOPQRSTUVWXYZ", 28, &my_packet, 100);

    if ((status != NX_SUCCESS) || (my_packet == NX_NULL) || (my_packet -> nx_packet_length != 28))
    {
        error_counter++;
        return;
    }

    /* Check the NAT forwarded count.  NAT receive the ping request,
        but can not forward this packet to local network.  discard it.  
#ifndef NX_DISABLE_NAT_INFO
    if ((nat_server.forwarded_packets_received != 3) ||
        (nat_server.forwarded_packets_sent != 2) ||
        (nat_server.arded_packets_dropped != 1))
    {
        error_counter++;
        return;
    }
#endif

    /**********************************************/
    /*       Create an inbound entry for ICMP     */
    /**********************************************/

    /* Calling NAT API to create a inbound entry.  */
    status = nx_nat_inbound_entry_create(&nat_server, &server_inbound_entry_icmp,
        NX_NAT_LOCAL_HOST1, 0, 0, NX_PROTOCOL_ICMP);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* External Host ping NAT External address, LOCAL HOST1 will
        response all inbound icmp request from external network.  */
    status =  nx_icmp_ping(&external_ip, NX_NAT_EXTERNAL_IPADR,
        "ABCDEFGHIJKLMNOPQRSTUVWXYZ", 28, &my_packet, 100);

    if ((status != NX_SUCCESS) || (my_packet == NX_NULL) || (my_packet -> nx_packet_length != 28))
    {
        error_counter++;
        return;
    }

    /* Check the NAT forwarded count.  */
#ifndef NX_DISABLE_NAT_INFO
    if ((nat_server.forwarded_packets_received != 5) ||
        (nat_server.forwarded_packets_sent != 4) ||
        (nat_server.arded_packets_dropped != 1))
    {
        error_counter++;
        return;
    }
#endif
}
#endif
```

<span data-ttu-id="cf918-135">**図 5 - NetX Duo NAT の設定**</span><span class="sxs-lookup"><span data-stu-id="cf918-135">**Figure 5 - Setting up NetX Duo NAT**</span></span>
