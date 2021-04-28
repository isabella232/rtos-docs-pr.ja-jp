---
title: 第 2 章 - Azure RTOS NetX Duo Telnet のインストールと使用
description: この章では、Azure RTOS NetX Duo Telnet コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5b24690db6ccbc582387dd9dba5b0471e6f278d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810541"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-telnet"></a><span data-ttu-id="d5182-103">第 2 章 - Azure RTOS NetX Duo Telnet のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="d5182-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo Telnet</span></span>

<span data-ttu-id="d5182-104">この章では、Azure RTOS NetX Duo Telnet コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="d5182-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo Telnet component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="d5182-105">製品の配布</span><span class="sxs-lookup"><span data-stu-id="d5182-105">Product Distribution</span></span>

<span data-ttu-id="d5182-106">Azure RTOS NetX Duo Telnet パッケージは <https://github.com/azure-rtos/netxduo> で入手できます。</span><span class="sxs-lookup"><span data-stu-id="d5182-106">The Azure RTOS NetX Duo Telnet package is available at <https://github.com/azure-rtos/netxduo>.</span></span> <span data-ttu-id="d5182-107">パッケージには、次のファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d5182-107">The package includes the following files:</span></span>

- <span data-ttu-id="d5182-108">**nxd_telnet_client.h**: NetX Duo 用 Telnet クライアントのヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="d5182-108">**nxd_telnet_client.h**: Header file for Telnet Client for NetX Duo</span></span>
- <span data-ttu-id="d5182-109">**nxd_telnet_client.c**: NetX Duo 用 Telnet クライアントの C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="d5182-109">**nxd_telnet_client.c**: C Source file for Telnet Client for NetX Duo</span></span>
- <span data-ttu-id="d5182-110">**nxd_telnet_server.h**: NetX Duo 用 Telnet サーバーのヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="d5182-110">**nxd_telnet_server.h**: Header file for Telnet Server for NetX Duo</span></span>
- <span data-ttu-id="d5182-111">**nxd_telnet_server.c**: NetX Duo 用 Telnet サーバーの C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="d5182-111">**nxd_telnet_server.c**: C Source file for Telnet Server for NetX Duo</span></span>
- <span data-ttu-id="d5182-112">**nxd_telnet.pdf**: NetX Duo 用 Telnet の PDF での説明</span><span class="sxs-lookup"><span data-stu-id="d5182-112">**nxd_telnet.pdf**: PDF description of Telnet for NetX Duo</span></span>
- <span data-ttu-id="d5182-113">**demo_netxduo_telnet.c**: NetX Duo Telnet のデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="d5182-113">**demo_netxduo_telnet.c**: NetX Duo Telnet demonstration</span></span>

## <a name="telnet-installation"></a><span data-ttu-id="d5182-114">Telnet のインストール</span><span class="sxs-lookup"><span data-stu-id="d5182-114">Telnet Installation</span></span>

<span data-ttu-id="d5182-115">NetX Duo 用 Telnet を使用するには、前述のディストリビューション全体を、NetX Duo がインストールされているものと同じディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5182-115">In order to use Telnet for NetX Duo, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="d5182-116">たとえば、NetX Duo がディレクトリ “ *\threadx\arm7\green*” にインストールされている場合、*nxd_telnet_client.h*、*nxd_telnet_client.c*、*nxd_telnet_server.c、nxd_telnet_server.h* ファイルをこのディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5182-116">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_telnet_client.h*, *nxd_telnet_client.c*, *nxd_telnet_server.c and nxd_telnet_server.h* files should be copied into this directory.</span></span>

## <a name="using-telnet"></a><span data-ttu-id="d5182-117">Telnet の使用</span><span class="sxs-lookup"><span data-stu-id="d5182-117">Using Telnet</span></span>

<span data-ttu-id="d5182-118">NetX Duo 用 Telnet を使用するのは簡単です。</span><span class="sxs-lookup"><span data-stu-id="d5182-118">Using Telnet for NetX Duo is easy.</span></span> <span data-ttu-id="d5182-119">ThreadX と NetX Duo を使用するには、基本的に、アプリケーション コードに、*tx_api.h* と *nx_api.h* をインクルードした後に Telnet サーバー アプリケーション用の *nxd_telnet_server.h* と Telnet クライアント アプリケーション用の *nxd_telnet_client.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5182-119">Basically, the application code must include *nxd_telnet_server.h* for Telnet Server applications and *nxd_telnet_client.h* for Telnet Client applications after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX Duo.</span></span> <span data-ttu-id="d5182-120">"*ヘッダー*" をインクルードすると、アプリケーション コードで、このガイドで後述する Telnet 関数呼び出しを行うことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="d5182-120">Once *the header* is included, the application code is then able to make the Telnet function calls specified later in this guide.</span></span> <span data-ttu-id="d5182-121">また、アプリケーションでは、ビルド プロセスで *nxd_telnet_client.c* と *nxd_telnet_server.c* もインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5182-121">The application must also include *nxd_telnet_client.c* and *nxd_telnet_server.c* in the build process.</span></span> <span data-ttu-id="d5182-122">これらのファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、そのオブジェクト形式をアプリケーションのファイルと一緒にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5182-122">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="d5182-123">NetX Duo Telnet の使用に必要なものはこれですべてです。</span><span class="sxs-lookup"><span data-stu-id="d5182-123">This is all that is required to use NetX Duo Telnet.</span></span>

<span data-ttu-id="d5182-124">Telnet クライアント機能が必要ない場合は、*nxd_telnet_client.c* ファイルを省略できます。</span><span class="sxs-lookup"><span data-stu-id="d5182-124">If no Telnet Client capabilities are required, the *nxd_telnet_client.c* file may be omitted.</span></span>

<span data-ttu-id="d5182-125">Telnet では NetX Duo TCP サービスを利用するため、Telnet を使用する前に、*nx_tcp_enable* 呼び出しを使用して TCP を有効にする必要があることにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="d5182-125">Note also that because Telnet utilizes NetX Duo TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using Telnet.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="d5182-126">小規模のシステム例</span><span class="sxs-lookup"><span data-stu-id="d5182-126">Small Example System</span></span>

<span data-ttu-id="d5182-127">NetX Duo Telnet を使用する方法の例を以下の図 1.1 に示します。</span><span class="sxs-lookup"><span data-stu-id="d5182-127">An example of how to use NetX Duo Telnet is shown in Figure 1.1 below.</span></span> <span data-ttu-id="d5182-128">この例では、Telnet インクルード ファイルは 7 行目および 8 行目に挿入されて "*います*"。</span><span class="sxs-lookup"><span data-stu-id="d5182-128">In this example, the Telnet include files *are* brought in at line 7 and 8.</span></span> <span data-ttu-id="d5182-129">次に、Telnet サーバーが "*tx_application_define*" の 146 行目に作成されます。</span><span class="sxs-lookup"><span data-stu-id="d5182-129">Next, the Telnet Server is created in “*tx_application_define*” at line 146.</span></span> <span data-ttu-id="d5182-130">Telnet サーバーとクライアントのコントロール ブロックは、前もって 23 行目から 24 行目にグローバル変数として定義されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d5182-130">Note that the Telnet Server and Client control blocks are defined as global variables at line 23-24 previously.</span></span>

<span data-ttu-id="d5182-131">Telnet サーバーまたはクライアントを起動するには、事前に NetX Duo でそれらの IP アドレスを検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5182-131">Before the Telnet Server or Client can be started they must validate their IP address with NetX Duo.</span></span> <span data-ttu-id="d5182-132">IPv4 接続の場合、これを行うには、単純に短時間待機することで、NetX ドライバーが 166 行目でシステムを初期化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d5182-132">For IPv4 connections this is accomplished by simply waiting briefly to let the NetX driver initialize the system on line 166.</span></span> <span data-ttu-id="d5182-133">IPv6 接続の場合は、このために IPv6 と ICMPv6 を有効にする必要があり、171 行目から 172 行目で行います。</span><span class="sxs-lookup"><span data-stu-id="d5182-133">For IPv6 connections, this requires enabling IPv6 and ICMPv6 which it does in lines 171-172.</span></span> <span data-ttu-id="d5182-134">クライアントは、181 行目から 186 行目でプライマリ インターフェイスにそのグローバルおよびリンク ローカルの IPv6 アドレスを設定し、バックグラウンドで NetX Duo の検証が完了するのを待機します。</span><span class="sxs-lookup"><span data-stu-id="d5182-134">The Client sets its global and link local IPv6 addresses on the primary interface on lines 181-186 and waits for NetX Duo validation to complete in the background.</span></span> <span data-ttu-id="d5182-135">サーバーも、192 行目から 198 行目でプライマリ インターフェイスにそのグローバルおよびリンク ローカルのアドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="d5182-135">The Server also sets its global and link local addresses on its primary interface in lines 192 – 198.</span></span> <span data-ttu-id="d5182-136">2 つのサービス *nxd_ipv6_global_address_set* と *nxd_ipv6_linklocal_address_set* が "*nxd_ipv6_address_set サービス*" に置き換えられていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d5182-136">Note that the two services, *nxd_ipv6_global_address_set* and *nxd_ipv6_linklocal_address_set* are replaced with *nxd_ipv6_address_set service*.</span></span> <span data-ttu-id="d5182-137">以前の 2 つのサービスは引き続きレガシの NetX Duo アプリケーションで使用できますが、最終的には非推奨になります。</span><span class="sxs-lookup"><span data-stu-id="d5182-137">The former two services are still available for legacy NetX Duo applications but are eventually deprecated.</span></span> <span data-ttu-id="d5182-138">開発者には、代わりに *nxd_ipv6_address_set* を使用することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="d5182-138">Developers are encouraged to use *nxd_ipv6_address_set* instead.</span></span>

<span data-ttu-id="d5182-139">NetX Duo による IP アドレスの検証が正常に行われると、*nxd_telnet_server_start* サービスを使用して、215 行目で Telnet サーバーが起動されます。</span><span class="sxs-lookup"><span data-stu-id="d5182-139">After successful IP address validation with NetX Duo, the Telnet Server is started at line 215 using the *nxd_telnet_server_start* service.</span></span> <span data-ttu-id="d5182-140">226 行目では、*nx_telnet_client_create* サービスを使用して Telnet クライアントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d5182-140">At line 226 the Telnet Client is created using the *nx_telnet_client_create* service.</span></span> <span data-ttu-id="d5182-141">その後に、IPv4 アプリケーションの場合は 242 行目、IPv6 アプリケーションの場合は 238 行目で、それぞれ *nxd_telnet_client_connect* および *nx_telnet_client_connect* サービスを使用して、Telnet サーバーに接続されます。</span><span class="sxs-lookup"><span data-stu-id="d5182-141">It then connects with the Telnet Server on line 242 for IPv4 applications and line 238 for IPv6 applications using the *nxd_telnet_client_connect* and *nx_telnet_client_connect* services respectively.</span></span> <span data-ttu-id="d5182-142">検証およびサーバーとの接続が正常に行われた後、切断される前にいくつかのやりとりが行われます。</span><span class="sxs-lookup"><span data-stu-id="d5182-142">After successful validation and connection with the server, it makes a few exchanges before disconnecting.</span></span>

```c
/* This is a small demo of TELNET on the high-performance NetX Duo TCP/IP stack.  
       This demo relies on ThreadX and NetX Duo to show a simple TELNET connection,
       send, server echo, and then disconnection from the TELNET server.  */
    
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nxd_telnet_client.h"
#include  "nxd_telnet_server.h"
#define     DEMO_STACK_SIZE         4096    
   
/* Define the ThreadX and NetX object control blocks...  */
TX_THREAD               test_thread;
NX_PACKET_POOL          pool_server;
NX_PACKET_POOL          pool_client;
NX_IP                   ip_server;
NX_IP                   ip_client;
   
/* Define TELNET objects.  */

NX_TELNET_SERVER        my_server;
NX_TELNET_CLIENT        my_client;


#ifdef FEATURE_NX_IPV6

/* Define NetX Duo IP address for the NetX Duo Telnet Server and Client. */

NXD_ADDRESS     server_ip_address;
NXD_ADDRESS     client_ip_address;

#endif

#define         SERVER_ADDRESS          IP_ADDRESS(1,2,3,4)
#define         CLIENT_ADDRESS          IP_ADDRESS(1,2,3,5)

/* Define the counters used in the demo application...  */
ULONG                   error_counter;

/* Define timeout in ticks for connecting and sending/receiving data. */

#define                 TELNET_TIMEOUT  200

/* Define function prototypes.  */

void    thread_test_entry(ULONG thread_input);
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);


/* Define the application's TELNET Server callback routines.  */

void    telnet_new_connection(NX_TELNET_SERVER *server_ptr, UINT 
                              logical_connection); 
void    telnet_receive_data(NX_TELNET_SERVER *server_ptr, UINT logical_connection, 
                            NX_PACKET *packet_ptr);
void    telnet_connection_end(NX_TELNET_SERVER *server_ptr, UINT 
                              logical_connection);

/* Define main entry point.  */

int main()
{

    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

UINT    status;
CHAR    *pointer;
UINT    iface_index, address_index;
    
    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;
    
    /* Create the main thread.  */
    tx_thread_create(&test_thread, "test thread", thread_test_entry, 0,  
                     pointer, DEMO_STACK_SIZE, 
                     2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;
    
    /* Initialize the NetX system.  */
    nx_system_initialize();
    
    /* Create packet pool.  */
    nx_packet_pool_create(&pool_server, "Server NetX Packet Pool", 600, pointer, 8192);
    pointer = pointer + 8192;
    
    /* Create an IP instance.  */
    nx_ip_create(&ip_server, "Server NetX IP Instance", SERVER_ADDRESS, 
                 0xFFFFFF00UL, &pool_server, _nx_ram_network_driver,
                 pointer, 4096, 1);
    
    pointer =  pointer + 4096;
    
    /* Create another packet pool. */
    nx_packet_pool_create(&pool_client, "Client NetX Packet Pool", 600, 
                          pointer, 8192);
    pointer = pointer + 8192;
    
    /* Create another IP instance.  */
    nx_ip_create(&ip_client, "Client NetX IP Instance", CLIENT_ADDRESS, 
                 0xFFFFFF00UL, &pool_client, _nx_ram_network_driver, 
                 pointer, 4096, 1);
    
    pointer = pointer + 4096;
    
    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    nx_arp_enable(&ip_server, (void *) pointer, 1024);
    pointer = pointer + 1024;
    
    /* Enable ARP and supply ARP cache memory for IP Instance 1.  */
    nx_arp_enable(&ip_client, (void *) pointer, 1024);
    pointer = pointer + 1024;
    
    /* Enable TCP processing for both IP instances.  */
    nx_tcp_enable(&ip_server);
    nx_tcp_enable(&ip_client);

#ifdef FEATURE_NX_IPV6

    /* Next set the NetX Duo Telnet Server and Client addresses. */
    server_ip_address.nxd_ip_address.v6[3] = 0x105;
    server_ip_address.nxd_ip_address.v6[2] = 0x0;
    server_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

#endif

    /* Create the NetX Duo TELNET Server.  */
    status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_server, 
                                      pointer, 2048, telnet_new_connection, telnet_receive_data, 
                                      telnet_connection_end);
    
    /* Check for errors.  */
    if (status)
        error_counter++;
    
    return;
}

/* Define the test thread.  */
void    thread_test_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;
    
    /* Allow other threads (e.g. IP thread task) to run first. */
    tx_thread_sleep(100);
    
    #ifdef FEATURE_NX_IPV6
    /* Here's where we make the Telnet Client IPv6 enabled. */
    nxd_ipv6_enable(&ip_client);
    nxd_icmp_enable(&ip_client);     
    
    /* Wait till the IP task thread initializes the system. */
    tx_thread_sleep(100);
        
    /* Set up the Client addresses on the Client IP for the primary interface. */
    if_index = 0;
    
    status = nxd_ipv6_address_set(&ip_ client, iface_index, NX_NULL, 10, 
                                  &address_index);
    status = nxd_ipv6_address_set(&ip_ client, iface_index, & client _ip_address, 
                                   64, &address_index);
        
    /* Allow NetX Duo time to validate addresses. */
    tx_thread_sleep(400);
    
    /* Set up the Server addresses on the Client IP. */
    iface_index = 0;
    status = nxd_ipv6_address_set (&ip_server, iface_index, NX_NULL, 10, 
                                   &address_index);
    
    status = nxd_ ipv6_address _set(&ip_server, iface_index, & server _ip_address, 
                                     64, &address_index);
        
    /* Allow NetX Duo time to validate addresses. */     
    tx_thread_sleep(400);
    
    #endif
    
    /* Start the TELNET Server.  */
    status =  nx_telnet_server_start(&my_server);
    
    /* Check for errors.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Create a TELENT client instance.  */
    status =  nx_telnet_client_create(&my_client, "My TELNET Client", 
                                      &ip_client, 600);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    #ifdef FEATURE_NX_IPV6
    
        /* Connect the TELNET client to the TELNET Server at port 23.  */
        status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 
                                             TELNET_TIMEOUT);
    
    #else
        /* Connect the TELNET client to the TELNET Server at port 23.  */
        status =  nx_telnet_client_connect(&my_client, SERVER_ADDRESS, 23,
                                            TELNET_TIMEOUT);
    #endif
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Allocate a packet.  */
    status =  nx_packet_allocate(&pool_client, &my_packet, NX_TCP_PACKET, 
                                  NX_WAIT_FOREVER);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Build a simple 1-byte message.  */
    nx_packet_data_append(my_packet, "a", 1, &pool_client, NX_WAIT_FOREVER);
    
    /* Send the packet to the TELNET Server.  */
    status =  nx_telnet_client_packet_send(&my_client, my_packet, TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Pickup the Server header.  */
    status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 
                                               TELNET_TIMEOUT);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* At this point the packet should contain the Server's banner
        message sent by the Server callback function below.  Just
        release it for this demo.  */
    nx_packet_release(my_packet);
    
    /* Pickup the Server echo of the character.  */
    status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 
                                               TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* At this point the packet should contain the character 'a' that
        we sent earlier.  Just release the packet for now.  */
    nx_packet_release(my_packet);
    
    /* Now disconnect form the TELNET Server.  */
    status =  nx_telnet_client_disconnect(&my_client, TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Delete the TELNET Client.  */
    status =  nx_telnet_client_delete(&my_client);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
}

/* This routine is called by the NetX Telnet Server whenever a new Telnet client 
    connection is established.  */
void  telnet_new_connection(NX_TELNET_SERVER *server_ptr, UINT logical_connection)
{

UINT        status;
NX_PACKET   *packet_ptr;

    /* Allocate a packet for client greeting. */
    status =  nx_packet_allocate(&pool_server, &packet_ptr, NX_TCP_PACKET, 
                                  NX_NO_WAIT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Build a banner message and a prompt.  */
    nx_packet_data_append(packet_ptr,"**** Welcome to NetX TELNET Server ****\r\n\r\n\r\n", 45,                            
                         &pool_server, NX_NO_WAIT);

    nx_packet_data_append(packet_ptr, "NETX> ", 6, &pool_server, NX_NO_WAIT);
    
    /* Send the packet to the client.  */
    status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                           packet_ptr, TELNET_TIMEOUT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        nx_packet_release(packet_ptr);
    }
    return;
}

/* This routine is called by the NetX Telnet Server whenever data is present on a 
    Telnet client connection.  */          
void  telnet_receive_data(NX_TELNET_SERVER *server_ptr, UINT logical_connection,
                          NX_PACKET *packet_ptr)
{

UINT    status;
UCHAR   alpha;

    /* This demo echoes the character back; on <cr,lf> sends a new prompt back to 
        the client.  A real system would likely buffer the character(s) received in a 
        buffer associated with the supplied logical connection and process it.  */

    /* Just throw away carriage returns.  */
    if ((packet_ptr -> nx_packet_prepend_ptr[0] == '\r') && (packet_ptr -> nx_packet_length == 1))
    {
        printf("telnet server received just a CRLF\n");

        nx_packet_release(packet_ptr);
        return;
    }

    /* Setup new line on line feed.  */
    if ((packet_ptr -> nx_packet_prepend_ptr[0] == '\n') || (packet_ptr -> nx_packet_prepend_ptr[1] == '\n'))
    {
        /* Clean up the packet.  */
        packet_ptr -> nx_packet_length =  0;
        packet_ptr -> nx_packet_prepend_ptr =  packet_ptr -> nx_packet_data_start + NX_TCP_PACKET;
        packet_ptr -> nx_packet_append_ptr =   packet_ptr -> nx_packet_data_start + NX_TCP_PACKET;

        /* Build the next prompt.  */
        nx_packet_data_append(packet_ptr, "\r\nNETX> ", 8, &pool_server, 
                              NX_NO_WAIT);

        /* Send the packet to the client.  */
        status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                               packet_ptr, TELNET_TIMEOUT);

        if (status != NX_SUCCESS)
        {
            error_counter++;
            nx_packet_release(packet_ptr);
        }
        return;
    }

    /* Pickup first character (usually only one from client).  */
    alpha =  packet_ptr -> nx_packet_prepend_ptr[0];

    /* Echo character.  */
    status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                           packet_ptr, TELNET_TIMEOUT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        nx_packet_release(packet_ptr);
    }

    /* Check for a disconnection.  */
    if (alpha == 'q')
    {
        /* Initiate server disconnection.  */
        nx_telnet_server_disconnect(server_ptr, logical_connection);
    }
}


/* This routine is called by the NetX Telnet Server when the client disconnects.  */
void  telnet_connection_end(NX_TELNET_SERVER *server_ptr, UINT logical_connection)
{
    /* Cleanup any application specific connection or buffer information.  */
    return;
}
```

## <a name="configuration-options"></a><span data-ttu-id="d5182-143">構成オプション</span><span class="sxs-lookup"><span data-stu-id="d5182-143">Configuration Options</span></span>

<span data-ttu-id="d5182-144">NetX Duo 用 Telnet を構築するための構成オプションがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="d5182-144">There are several configuration options for building Telnet for NetX Duo.</span></span> <span data-ttu-id="d5182-145">これらの #define は、*nxd_telnet_server.h* と *nxd_telnet_client.h* をインクルードする前にアプリケーションによって設定できます。</span><span class="sxs-lookup"><span data-stu-id="d5182-145">These #defines can be set by the application prior to inclusion of *nxd_telnet_server.h*.and *nxd_telnet_client.h.*</span></span>

<span data-ttu-id="d5182-146">以下に、すべてのオプションの一覧と、それぞれの詳細な説明を示します。</span><span class="sxs-lookup"><span data-stu-id="d5182-146">Following is a list of all options, where each is described in detail:</span></span>  
  
- <span data-ttu-id="d5182-147">**NX_DISABLE_ERROR_CHECKING**: このオプションを定義すると、基本的な Telnet エラー チェックが削除されます。</span><span class="sxs-lookup"><span data-stu-id="d5182-147">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic Telnet error checking.</span></span> <span data-ttu-id="d5182-148">通常は、アプリケーションがデバッグされた後に使用します。</span><span class="sxs-lookup"><span data-stu-id="d5182-148">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="d5182-149">**NX_TELNET_MAX_CLIENTS**: サーバー スレッドでサポートされる Telnet クライアントの最大数。</span><span class="sxs-lookup"><span data-stu-id="d5182-149">**NX_TELNET_MAX_CLIENTS**: The maximum number of Telnet Clients supported by the Server thread.</span></span> <span data-ttu-id="d5182-150">既定では、この値は 4 として定義され、一度に最大 4 つのクライアントを指定します。</span><span class="sxs-lookup"><span data-stu-id="d5182-150">By default, this value is defined as 4 to specify a maximum of 4 clients at a time.</span></span>
- <span data-ttu-id="d5182-151">**NX_TELNET_SERVER_PRIORITY**: Telnet サーバー スレッドの優先順位。</span><span class="sxs-lookup"><span data-stu-id="d5182-151">**NX_TELNET_SERVER_PRIORITY**: The priority of the Telnet Server thread.</span></span> <span data-ttu-id="d5182-152">既定では、この値は 16 に定義され、優先順位 16 を示します。</span><span class="sxs-lookup"><span data-stu-id="d5182-152">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="d5182-153">**NX_TELNET_TOS**: Telnet TCP 要求に必要なサービスの種類。</span><span class="sxs-lookup"><span data-stu-id="d5182-153">**NX_TELNET_TOS**: Type of service required for the Telnet TCP requests.</span></span> <span data-ttu-id="d5182-154">既定では、この値は NX_IP_NORMAL として定義され、</span><span class="sxs-lookup"><span data-stu-id="d5182-154">By default, this value is defined as NX_IP_NORMAL to indicate</span></span>  
<span data-ttu-id="d5182-155">通常の IP パケット サービスを示します。</span><span class="sxs-lookup"><span data-stu-id="d5182-155">normal IP packet service.</span></span>
- <span data-ttu-id="d5182-156">**NX_TELNET_FRAGMENT_OPTION**: Telnet TCP 要求でのフラグメントの有効化。</span><span class="sxs-lookup"><span data-stu-id="d5182-156">**NX_TELNET_FRAGMENT_OPTION**: Fragment enable for Telnet TCP requests.</span></span> <span data-ttu-id="d5182-157">既定では、この値は NX_DONT_FRAGMENT であり、HTTP TCP のフラグメント化が無効になります。</span><span class="sxs-lookup"><span data-stu-id="d5182-157">By default, this value is NX_DONT_FRAGMENT to disable Telnet TCP fragmenting.</span></span>
- <span data-ttu-id="d5182-158">**NX_TELNET_SERVER_WINDOW_SIZE**: サーバー ソケットのウィンドウ サイズ。</span><span class="sxs-lookup"><span data-stu-id="d5182-158">**NX_TELNET_SERVER_WINDOW_SIZE**: Server socket window size.</span></span> <span data-ttu-id="d5182-159">既定では、この値は 2048 バイトです。</span><span class="sxs-lookup"><span data-stu-id="d5182-159">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="d5182-160">**NX_TELNET_TIME_TO_LIVE**: このパケットが破棄されるまでに通過できるルーターの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d5182-160">**NX_TELNET_TIME_TO_LIVE**: Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="d5182-161">既定値は 0x80 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="d5182-161">The default value is set to 0x80.</span></span>
- <span data-ttu-id="d5182-162">**NX_TELNET_SERVER_TIMEOUT**: 内部サービスが中断される ThreadX ティックの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d5182-162">**NX_TELNET_SERVER_TIMEOUT**: Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="d5182-163">既定値は 10 秒に設定されています。</span><span class="sxs-lookup"><span data-stu-id="d5182-163">The default value is set to 10 seconds.</span></span>
- <span data-ttu-id="d5182-164">**NX_TELNET_ACTIVITY_TIMEOUT**: サーバーがクライアント接続を切断するまでに、アクティビティがないまま経過することができる秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d5182-164">**NX_TELNET_ACTIVITY_TIMEOUT**: Specifies the number of seconds that can elapse without any activity before the Server disconnects the Client connection.</span></span> <span data-ttu-id="d5182-165">既定値は 600 秒に設定されています。</span><span class="sxs-lookup"><span data-stu-id="d5182-165">The default value is set to 600 seconds.</span></span>
- <span data-ttu-id="d5182-166">**NX_TELNET_TIMEOUT_PERIOD**: クライアント アクティビティのタイムアウトを確認する間隔の秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d5182-166">**NX_TELNET_TIMEOUT_PERIOD**: Specifies the number of seconds between checking for Client activity timeouts.</span></span> <span data-ttu-id="d5182-167">既定値は 60 秒に設定されています。</span><span class="sxs-lookup"><span data-stu-id="d5182-167">The default value is set to 60 seconds.</span></span>
- <span data-ttu-id="d5182-168">**NX_TELNET_SERVER_OPTION_DISABLE**: 定義されている場合、Telnet オプションのネゴシエーションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="d5182-168">**NX_TELNET_SERVER_OPTION_DISABLE**: Defined, Telnet option negotiation is disabled.</span></span> <span data-ttu-id="d5182-169">既定では、このオプションは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="d5182-169">By default this option is not defined.</span></span>
- <span data-ttu-id="d5182-170">**NX_TELNET_SERVER_USER_CREATE_PACKET_POOL**: 定義されている場合、Telnet サーバーのパケット プールを外部に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5182-170">**NX_TELNET_SERVER_USER_CREATE_PACKET_POOL**: If defined, the Telnet Server packet pool must be created externally.</span></span> <span data-ttu-id="d5182-171">これは、NX_TELNET_SERVER_OPTION_DISABLE が定義されていない場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="d5182-171">This is only meaningful if NX_TELNET_SERVER_OPTION_DISABLE is not defined.</span></span> <span data-ttu-id="d5182-172">既定では、このオプションは定義されず、Telnet サーバー スレッドによってそれ自体のパケット プールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d5182-172">By default this option is not defined and the Telnet Server thread creates its own packet pool.</span></span>
- <span data-ttu-id="d5182-173">**NX_TELNET_SERVER_PACKET_PAYLOAD**: オプションのネゴシエーションのために Telnet サーバーによって作成されるパケット ペイロードのサイズを定義します。</span><span class="sxs-lookup"><span data-stu-id="d5182-173">**NX_TELNET_SERVER_PACKET_PAYLOAD**: Defines the size of the packet payload created by the Telnet Server for option negotiation.</span></span> <span data-ttu-id="d5182-174">Telnet サーバーでは、NX_TELNET_SERVER _OPTION_DISABLE が定義されていない (Telnet オプションが有効になっている) 場合にのみこのパケット プールが作成されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d5182-174">Note that the Telnet Server only creates this packet pool if NX_TELNET_SERVER _OPTION_DISABLE is not defined (Telnet options are enabled).</span></span> <span data-ttu-id="d5182-175">このオプションの既定値は 300 です。</span><span class="sxs-lookup"><span data-stu-id="d5182-175">The default value of this option is 300.</span></span>
- <span data-ttu-id="d5182-176">**NX_TELNET_SERVER_PACKET_POOL_SIZE**: Telnet ネゴシエーションに使用される Telnet サーバー パケット プールのサイズを定義します。</span><span class="sxs-lookup"><span data-stu-id="d5182-176">**NX_TELNET_SERVER_PACKET_POOL_SIZE**: Defines the size of the Telnet Server packet pool used for Telnet negotiations.</span></span> <span data-ttu-id="d5182-177">Telnet サーバーでは、NX_TELNET_SERVER _OPTION_DISABLE が定義されていない (Telnet オプションが有効になっている) 場合にのみこのパケット プールが作成されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d5182-177">Note that the Telnet Server only creates this packet pool if NX_TELNET_SERVER _OPTION_DISABLE is not defined (Telnet options are enabled).</span></span> <span data-ttu-id="d5182-178">このオプションの既定値は 2048 (\~5 から 6 パケット) です。</span><span class="sxs-lookup"><span data-stu-id="d5182-178">The default value of this option is 2048 (\~5-6 packets).</span></span>
