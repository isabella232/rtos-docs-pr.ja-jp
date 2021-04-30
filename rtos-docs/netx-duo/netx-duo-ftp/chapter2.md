---
title: 第 2 章 - FTP のインストールと使用
description: この章では、NetX Duo FTP サービスのインストール、設定、および使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ac58658af93f59556d99d340ae38570908d63fc1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810793"
---
# <a name="chapter-2---installation-and-use-of-ftp"></a><span data-ttu-id="c3548-103">第 2 章 - FTP のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="c3548-103">Chapter 2 - Installation and use of FTP</span></span>

<span data-ttu-id="c3548-104">この章では、NetX Duo FTP サービスのインストール、設定、および使用に関連するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="c3548-104">This chapter contains a description of various issues related to installation, set up, and usage of the NetX Duo FTP services.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="c3548-105">製品の配布</span><span class="sxs-lookup"><span data-stu-id="c3548-105">Product Distribution</span></span>

<span data-ttu-id="c3548-106">NetX Duo FTP は、[https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="c3548-106">NetX Duo FTP is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="c3548-107">このパッケージには、次のような 2 つのソース ファイルと、このドキュメントを含む 1 つの PDF ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c3548-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="c3548-108">**nxd_tftp_client.h**: NetX Duo FTP クライアント用のヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="c3548-108">**nxd_ftp_client.h** Header file for NetX Duo FTP Client</span></span>
- <span data-ttu-id="c3548-109">**nxd_tftp_client.h**: NetX Duo FTP クライアントの C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="c3548-109">**nxd_ftp_client.c** C Source file for NetX Duo FTP Client</span></span>
- <span data-ttu-id="c3548-110">**nxd_tftp_client.h**: NetX Duo FTP サーバー用のヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="c3548-110">**nxd_ftp_server.h** Header file for NetX Duo FTP Server</span></span>
- <span data-ttu-id="c3548-111">**nxd_tftp_client.h**: NetX Duo FTP サーバーの C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="c3548-111">**nxd_ftp_server.c** C Source file for NetX Duo FTP Server</span></span>
- <span data-ttu-id="c3548-112">**filex_stub.h**: FileX が存在しない場合のスタブ ファイル</span><span class="sxs-lookup"><span data-stu-id="c3548-112">**filex_stub.h** Stub file if FileX is not present</span></span>
- <span data-ttu-id="c3548-113">**nx_ftp.pdf**: NetX Duo 用の FTP に関する PDF 説明書</span><span class="sxs-lookup"><span data-stu-id="c3548-113">**nxd_ftp.pdf** PDF description of FTP for NetX Duo</span></span>
- <span data-ttu-id="c3548-114">**demo_netxduo_ftp.c**: FTP デモンストレーション システム</span><span class="sxs-lookup"><span data-stu-id="c3548-114">**demo_netxduo_ftp.c** FTP demonstration system</span></span>

## <a name="netx-duo-ftp-installation"></a><span data-ttu-id="c3548-115">NetX Duo FTP のインストール</span><span class="sxs-lookup"><span data-stu-id="c3548-115">NetX Duo FTP Installation</span></span>

<span data-ttu-id="c3548-116">NetX Duo FTP API シリーズを使用するには、前述のディストリビューション全体を、NetX Duo がインストールされているのと同じディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3548-116">In order to use the NetX Duo FTP API, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="c3548-117">たとえば、NetX Duo がディレクトリ " *\threadx\arm7\green*" にインストールされている場合、FTP クライアント アプリケーション用のディレクトリに *nxd_ftp_client.h* と *nxd_ftp_client.c* をコピーする必要があります。また、FTP サーバー アプリケーション用のディレクトリに *nxd_ftp_server.h* ファイルと *nxd_ftp_server.c* ファイルをコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3548-117">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_ftp_client.h* and *nxd_ftp_client.c* should be copied into this directory for FTP Client applications, and *nxd_ftp_server.h* and *nxd_ftp_server.c* files should be copied into this directory for FTP Server applications.</span></span>

## <a name="using-netx-duo-ftp"></a><span data-ttu-id="c3548-118">NetX Duo FTP の使用</span><span class="sxs-lookup"><span data-stu-id="c3548-118">Using NetX Duo FTP</span></span>

<span data-ttu-id="c3548-119">NetX Duo FTP API は簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="c3548-119">Using the NetX Duo FTP API is easy.</span></span> <span data-ttu-id="c3548-120">基本的には、アプリケーション コードに ThreadX、FileX、および NetX Duo を使用するための *tx_api.h、fx_api.h* および *nx_api.h* をインクルードしてから、FTP クライアント アプリケーション用の *nxd_ftp_client.h* または FTP サーバー アプリケーション用の *nxd_ftp_server* のいずれかをインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3548-120">Basically, the application code must include either *nxd_ftp_client.h* for FTP Client applications or *nxd_ftp_server* for FTP Server applications, after it includes *tx_api.h, fx_api.h,* and *nx_api.h*, in order to use ThreadX, FileX, and NetX Duo, respectively.</span></span> <span data-ttu-id="c3548-121">ビルド プロジェクトに、FTP ソース コードとホスト アプリケーション ファイルを含める必要があります。ThreadX および NetX ライブラリ ファイルを含めることは言うまでもありません。</span><span class="sxs-lookup"><span data-stu-id="c3548-121">The build project must include the FTP source code and the host application file, and of course the ThreadX and NetX library files.</span></span> <span data-ttu-id="c3548-122">NetX Duo FTP を使用するために必要なものは、これですべてです。</span><span class="sxs-lookup"><span data-stu-id="c3548-122">This is all that is required to use NetX Duo FTP.</span></span>

<span data-ttu-id="c3548-123">FTP では NetX Duo TCP サービスを利用するため、FTP を使用する前に、*nx_tcp_enable* を呼び出して TCP を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3548-123">Note that since FTP utilizes NetX Duo TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using FTP.</span></span>

<span data-ttu-id="c3548-124">NetX Duo ライブラリは IPv6 に対して有効にすることができ、IPv4 ネットワークは引き続きサポートされることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c3548-124">Note that the NetX Duo library can be enabled for IPv6 and still support IPv4 networks.</span></span> <span data-ttu-id="c3548-125">ただし、NetX Duo では、有効にしない限り、IPv6 はサポートできません。</span><span class="sxs-lookup"><span data-stu-id="c3548-125">However, NetX Duo cannot support IPv6 unless it is enabled.</span></span> <span data-ttu-id="c3548-126">NetX Duo で IPv6 処理を無効にするには、**NX_DISABLE_IPV6** を *nx_user.h* ファイルに定義する必要があります。また、**NX_INCLUDE_USER_DEFINE_FILE** を *nx_port.h* ファイルに定義することで、そのファイルを NetX Duo ライブラリのビルドに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3548-126">To disable IPv6 processing in NetX Duo, the **NX_DISABLE_IPV6** must be defined in the *nx_user.h* file, and that file must be included in the NetX Duo library build by defining **NX_INCLUDE_USER_DEFINE_FILE** in the *nx_port.h* file.</span></span> <span data-ttu-id="c3548-127">既定では、**NX_DISABLE_IPV6** は定義されません (IPv6 は有効です)。</span><span class="sxs-lookup"><span data-stu-id="c3548-127">By default, **NX_DISABLE_IPV6** is not defined (IPv6 is enabled).</span></span> <span data-ttu-id="c3548-128">これは、IP タスクで IPv6 プロトコルとサービスを設定する *nxd_ipv6_enable* サービスとは異なっており、**NX_DISABLE_IPV6** を定義する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c3548-128">This is different from the *nxd_ipv6_enable* service that sets up the IPv6 protocols and services on the IP task, and requires **NX_DISABLE_IPV6** to be not defined.</span></span>

## <a name="small-example-system-of-netx-duo-ftp"></a><span data-ttu-id="c3548-129">NetX Duo FTP の小規模のシステム例</span><span class="sxs-lookup"><span data-stu-id="c3548-129">Small Example System of NetX Duo FTP</span></span>

<span data-ttu-id="c3548-130">NetX Duo FTP の使用がいかに簡単であるかを示す例を、下の図 1.1 に示します。</span><span class="sxs-lookup"><span data-stu-id="c3548-130">An example of how easy it is to use NetX Duo FTP is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="c3548-131">この例では、FTP サーバーと FTP クライアントの両方が作成されます。</span><span class="sxs-lookup"><span data-stu-id="c3548-131">In this example, both an FTP Server and an FTP Client are created.</span></span> <span data-ttu-id="c3548-132">そのため、行 10 と行 11 で、両方の FTP インクルード ファイル (*nxd_ftp_client.h と nxd_ftp_server.h*) が取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="c3548-132">Therefore both FTP include files *nxd_ftp_client.h and nxd_ftp_server.h are* brought in at line 10 and 11.</span></span> <span data-ttu-id="c3548-133">次に、行 99 の "*tx_application_define*" で、FTP サーバーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c3548-133">Next, the FTP Server is created in “*tx_application_define*” at line 99.</span></span> <span data-ttu-id="c3548-134">FTP サーバーとクライアントのコントロール ブロックは、行 26 でグローバル変数として既に定義されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c3548-134">Note that the FTP Server and Client control blocks are defined as global variables at line 26 previously.</span></span>

<span data-ttu-id="c3548-135">このデモでは、NetX Duo FTP と従来の IPv4 制限付き FTP サービスで利用可能な Duo 関数を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c3548-135">This demo shows how to use the duo functions available in NetX Duo FTP as well as the legacy IPv4 limited FTP services.</span></span> <span data-ttu-id="c3548-136">このデモでは、IPv6 機能を使用するために、行 16 で USE_IPV6 を定義します。</span><span class="sxs-lookup"><span data-stu-id="c3548-136">To use the IPv6 functions, the demo defines USE_IPV6 in line 16</span></span>

<span data-ttu-id="c3548-137">行 162 で、IPv4 と IPv6 の両方をサポートする USE_IPV6 がホスト アプリケーションによって定義されている場合、\***nxd_ftp_server_create** _ を使用して FTP サーバーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c3548-137">At line 162 the FTP Server is created with \***nxd_ftp_server_create** _ if the host application defines USE_IPV6 which supports both IPv4 and IPv6.</span></span> <span data-ttu-id="c3548-138">そうでない場合、行 166 で、FTP サーバーは、IPv4 限定サービスを使用して、_ *_nx_ftp_server_create_*\* によって作成されます。</span><span class="sxs-lookup"><span data-stu-id="c3548-138">If it is not, the FTP Server is created with _ *_nx_ftp_server_create_*\* on line 166 with the IPv4 limited service.</span></span> <span data-ttu-id="c3548-139">'Duo' 関数では、IPv4 サービスとは異なるログインおよびログアウト関数の引数が使用されます。どちらも、ファイルの末尾の 行 534 から 行568 で定義されています。</span><span class="sxs-lookup"><span data-stu-id="c3548-139">Note that the ‘duo’ function uses different login and logout function arguments than the IPv4 service, both of which are defined at the bottom of the file on lines 534 -568.</span></span>

<span data-ttu-id="c3548-140">その後、FTP サーバーは、行 466 から始まる FTP サーバー スレッド エントリ関数で、NetX Duo により IPv6 アドレス (グローバルおよびリンク ローカル) を確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3548-140">The FTP server must then establish its IPv6 address (global and link local) with NetX Duo, starting at line 466 in the FTP server thread entry function.</span></span> <span data-ttu-id="c3548-141">その後、行 518 で FTP サーバーが起動され、FTP クライアント要求に対応できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c3548-141">The FTP server is then started on line 518 and is ready for FTP client requests.</span></span>

<span data-ttu-id="c3548-142">行 316 で FTP クライアントが作成され、FTP サーバーと同じプロセスを経由して FTP クライアント IP タスク IPv6 が有効になり、その IPv6 アドレスが行 263 から 行 313 で検証されます。</span><span class="sxs-lookup"><span data-stu-id="c3548-142">The FTP Client is created in line 316 and goes through the same process as the FTP Server to get the FTP Client IP task IPv6 enabled, and its IPv6 addresses validated starting on lines 263-313.</span></span>

<span data-ttu-id="c3548-143">次に、USE_IPV6 が定義されている場合は行 334 で ***nxd_ftp_client_connect** _ を使用して、IPv4 限定サービスが使用されている場合は行 340 で _*_nx_ftp_client_connect_\*\* を使用して、クライアントが FTP サーバーに接続されます。</span><span class="sxs-lookup"><span data-stu-id="c3548-143">Then the Client connects to the FTP Server using ***nxd_ftp_client_connect** _ in line 334 if it has defined USE_IPV6, or line 340 if it is using the IPv4 limited service _*_nx_ftp_client_connect_\*\*.</span></span> <span data-ttu-id="c3548-144">FTP クライアント スレッド関数の途中で、FTP サーバーにファイルが書き込まれ、切断前に読み取られます。</span><span class="sxs-lookup"><span data-stu-id="c3548-144">Over the course of the FTP Client thread function, it writes a file to the FTP server and reads it back before disconnecting.</span></span>

```C
/* This is a small demo of NetX FTP on the high-performance NetX TCP/IP stack.  This demo
   relies on ThreadX, NetX, and FileX to show a simple file transfer from the client
   and then back to the server.  */



#include    "tx_api.h"
#include    "fx_api.h"
#include    "nx_api.h"
#include    "nxd_ftp_client.h"
#include    "nxd_ftp_server.h"

#define     DEMO_STACK_SIZE         4096

#ifdef FEATURE_NX_IPV6
#define USE_IPV6
#endif /* FEATURE_NX_IPV6 */


/* Define the ThreadX, NetX, and FileX object control blocks...  */

TX_THREAD               server_thread;
TX_THREAD               client_thread;
NX_PACKET_POOL          server_pool;
NX_IP                   server_ip;
NX_PACKET_POOL          client_pool;
NX_IP                   client_ip;
FX_MEDIA                ram_disk;


/* Define the NetX FTP object control blocks.  */

NX_FTP_CLIENT           ftp_client;
NX_FTP_SERVER           ftp_server;


/* Define the counters used in the demo application...  */

ULONG                   error_counter = 0;


/* Define the memory area for the FileX RAM disk.  */

UCHAR                   ram_disk_memory[32000];
UCHAR                   ram_disk_sector_cache[512];


#define FTP_SERVER_ADDRESS  IP_ADDRESS(1,2,3,4)
#define FTP_CLIENT_ADDRESS  IP_ADDRESS(1,2,3,5)

extern UINT  _fx_media_format(FX_MEDIA *media_ptr, VOID (*driver)(FX_MEDIA *media),
                        VOID *driver_info_ptr, UCHAR *memory_ptr, UINT memory_size,
                        CHAR *volume_name, UINT number_of_fats, UINT directory_entries,
                        UINT hidden_sectors, ULONG total_sectors, UINT bytes_per_sector,
                        UINT sectors_per_cluster, UINT heads, UINT sectors_per_track);

/* Define the FileX and NetX driver entry functions.  */
VOID    _fx_ram_driver(FX_MEDIA *media_ptr);

/* Replace the 'ram' driver with your own Ethernet driver. */
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);


void    client_thread_entry(ULONG thread_input);
void    thread_server_entry(ULONG thread_input);


#ifdef USE_IPV6
/* Define NetX Duo IP address for the NetX Duo FTP Server and Client. */
NXD_ADDRESS     server_ip_address;
NXD_ADDRESS     client_ip_address;
endif


/* Define server login/logout functions.  These are stubs for functions that would
   validate a client login request.   */

#ifdef USE_IPV6
UINT    server_login6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info);
UINT    server_logout6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info);
#else
UINT    server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
    ULONG client_ip_address, UINT client_port,
    CHAR *name, CHAR *password, CHAR *extra_info);
UINT    server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
    ULONG client_ip_address, UINT client_port,
    CHAR *name, CHAR *password, CHAR *extra_info);
#endif


/* Define main entry point.  */

int main()
{

    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
    return(0);
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{

    UINT    status;
    UCHAR   *pointer;


    /* Setup the working pointer.  */
    pointer =  (UCHAR *) first_unused_memory;

    /* Create a helper thread for the server. */
    tx_thread_create(&server_thread, "FTP Server thread", thread_server_entry, 0,
                     pointer, DEMO_STACK_SIZE,
                     4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize NetX.  */
    nx_system_initialize();

    /* Create the packet pool for the FTP Server.  */
    status = nx_packet_pool_create(&server_pool, "NetX Server Packet Pool", 256, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors.  */
    if (status)
        error_counter++;

    /* Create the IP instance for the FTP Server.  */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance", FTP_SERVER_ADDRESS, 0xFFFFFF00UL,
                                        &server_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Enable ARP and supply ARP cache memory for server IP instance.  */
    nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP.  */
    nx_tcp_enable(&server_ip);

#ifdef USE_IPV6

    /* Next set the NetX Duo FTP Server and Client addresses. */
    server_ip_address.nxd_ip_address.v6[3] = 0x105;
    server_ip_address.nxd_ip_address.v6[2] = 0x0;
    server_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Create the FTP server.  */
    status =  nxd_ftp_server_create(&ftp_server, "FTP Server Instance", &server_ip,
                                    &ram_disk, pointer, DEMO_STACK_SIZE, &server_pool,
                                    server_login6, server_logout6);
#else
    /* Create the FTP server.  */
    status =  nx_ftp_server_create(&ftp_server, "FTP Server Instance", &server_ip,
                                    &ram_disk, pointer, DEMO_STACK_SIZE, &server_pool,
                                    server_login, server_logout);
#endif
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Now set up the FTP Client. */

    /* Create the main FTP client thread.  */
    status = tx_thread_create(&client_thread, "FTP Client thread ", client_thread_entry, 0,
            pointer, DEMO_STACK_SIZE,
            6, 6, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE ;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create a packet pool for the FTP client.  */
    status =  nx_packet_pool_create(&client_pool, "NetX Client Packet Pool", 256, pointer, 8192);
    pointer =  pointer + 8192;

    /* Create an IP instance for the FTP client.  */
    status = nx_ip_create(&client_ip, "NetX Client IP Instance", FTP_CLIENT_ADDRESS, 0xFFFFFF00UL,
                                                &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for the FTP Client IP.  */
    nx_arp_enable(&client_ip, (void *) pointer, 1024);

    pointer = pointer + 1024;

    /* Enable TCP for client IP instance.  */
    nx_tcp_enable(&client_ip);

    return;

}

/* Define the FTP client thread.  */

void    client_thread_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;

#ifdef USE_IPV6
UINT        iface_index, address_index;
#endif


    /* Format the RAM disk - the memory for the RAM disk was defined above.  */
    status = _fx_media_format(&ram_disk,
                            _fx_ram_driver,                  /* Driver entry                */
                            ram_disk_memory,                 /* RAM disk memory pointer     */
                            ram_disk_sector_cache,           /* Media buffer pointer        */
                            sizeof(ram_disk_sector_cache),   /* Media buffer size           */
                            "MY_RAM_DISK",                   /* Volume Name                 */
                            1,                               /* Number of FATs              */
                            32,                              /* Directory Entries           */
                            0,                               /* Hidden sectors              */
                            256,                             /* Total sectors               */
                            128,                             /* Sector size                 */
                            1,                               /* Sectors per cluster         */
                            1,                               /* Heads                       */
                            1);                              /* Sectors per track           */

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Open the RAM disk.  */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory,
        ram_disk_sector_cache, sizeof(ram_disk_sector_cache));

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Let the IP threads and driver initialize the system.    */
    tx_thread_sleep(100);

#ifdef USE_IPV6

    /* Here's where we make the FTP Client IPv6 enabled. */
    status = nxd_ipv6_enable(&client_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    status = nxd_icmp_enable(&client_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Set the Client link local and global addresses. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, &address_index);

    /* Check for link local address set error.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

     /* Set the host global IP address. We are assuming a 64
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, &client_ip_address, 64, &address_index);

    /* Check for global address set error.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    /* Let NetX Duo validate the addresses. */
    tx_thread_sleep(400);

#endif  /* USE_IPV6 */

    /* Create an FTP client.  */
    status =  nx_ftp_client_create(&ftp_client, "FTP Client", &client_ip, 2000, &client_pool);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Created the FTP Client\n");

#ifdef USE_IPV6

    do
    {

        /* Now connect with the NetX Duo FTP (IPv6) server. */
        status =  nxd_ftp_client_connect(&ftp_client, &server_ip_address, "name", "password", 100);
    } while (status != NX_SUCCESS);

#else

    /* Now connect with the NetX FTP (IPv4) server. */
    status =  nx_ftp_client_connect(&ftp_client, FTP_SERVER_ADDRESS, "name", "password", 100);

#endif  /* USE_IPV6 */

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Connected to the FTP Server\n");

    /* Open a FTP file for writing.  */
    status =  nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_WRITE, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Opened the FTP client test.txt file\n");

    /* Allocate a FTP packet.  */
    status =  nx_packet_allocate(&client_pool, &my_packet, NX_TCP_PACKET, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    /* Write ABCs into the packet payload!  */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ  ", 28);

    /* Adjust the write pointer.  */
    my_packet -> nx_packet_length =  28;
    my_packet -> nx_packet_append_ptr =  my_packet -> nx_packet_prepend_ptr + 28;

    /* Write the packet to the file test.txt.  */
    status =  nx_ftp_client_file_write(&ftp_client, my_packet, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
        printf("Wrote to the FTP client test.txt file\n");


    /* Close the file.  */
    status =  nx_ftp_client_file_close(&ftp_client, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Closed the FTP client test.txt file\n");


    /* Now open the same file for reading.  */
    status =  nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_READ, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Reopened the FTP client test.txt file\n");

    /* Read the file.  */
    status =  nx_ftp_client_file_read(&ftp_client, &my_packet, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
    {
            printf("Reread the FTP client test.txt file\n");
            nx_packet_release(my_packet);
    }

    /* Close this file.  */
    status =  nx_ftp_client_file_close(&ftp_client, 100);

    if (status != NX_SUCCESS)
        error_counter++;

    /* Disconnect from the server.  */
    status =  nx_ftp_client_disconnect(&ftp_client, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;


    /* Delete the FTP client.  */
    status =  nx_ftp_client_delete(&ftp_client);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
}


/* Define the helper FTP server thread.  */
void    thread_server_entry(ULONG thread_input)
{

    UINT            status;
#ifdef  USE_IPV6
    UINT            iface_index, address_index;
#endif

    /* Wait till the IP thread and driver have initialized the system. */
    tx_thread_sleep(100);

#ifdef USE_IPV6

    /* Here's where we make the FTP server IPv6 enabled. */
    status = nxd_ipv6_enable(&server_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    status = nxd_icmp_enable(&server_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

     /* Set the link local address with the host MAC address. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&server_ip, iface_index, NX_NULL, 10, &address_index);

    /* Check for link local address set error.  */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Set the host global IP address. We are assuming a 64
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&server_ip, iface_index, &server_ip_address, 64, &address_index);

    /* Check for global address set error.  */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Wait while NetX Duo validates the link local and global address. */
    tx_thread_sleep(500);

#endif /* USE_IPV6 */

    /* OK to start the FTP Server.   */
    status = nx_ftp_server_start(&ftp_server);

    if (status != NX_SUCCESS)
        error_counter++;

    printf("Server started!\n");

    /* FTP server ready to take requests! */

    /* Let the IP threads execute.    */
    tx_thread_relinquish();

    return;
}


#ifdef USE_IPV6
UINT  server_login6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    NXD_ADDRESS *client_ipduo_address, UINT client_port,
                    CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged in6!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}

UINT  server_logout6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
                     UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out6!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}
#else
UINT  server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, ULONG client_ip_address,
                    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{

    printf("Logged in!\n");
    /* Always return success.  */
    return(NX_SUCCESS);
}

UINT  server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, ULONG client_ip_address,
                    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}
#endif  /* USE_IPV6 */
```

<span data-ttu-id="c3548-145">**図 1.1 NetX Duo FTP の例**</span><span class="sxs-lookup"><span data-stu-id="c3548-145">**Figure 1.1 Example of NetX Duo FTP**</span></span>

## <a name="configuration-options"></a><span data-ttu-id="c3548-146">構成オプション</span><span class="sxs-lookup"><span data-stu-id="c3548-146">Configuration Options</span></span>

<span data-ttu-id="c3548-147">NetX FTP と NetX Duo FTP を構築するためのさまざまな構成オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="c3548-147">There are several configuration options for building NetX FTP and NetX Duo FTP.</span></span> <span data-ttu-id="c3548-148">既定値が示されていますが、各定義は、</span><span class="sxs-lookup"><span data-stu-id="c3548-148">The default values are listed, but each define can be set by the</span></span>

<span data-ttu-id="c3548-149">指定された NetX Duo FTP ヘッダー ファイルをインクルードする前にアプリケーションによって設定できます。</span><span class="sxs-lookup"><span data-stu-id="c3548-149">application prior to inclusion of the specified NetX Duo FTP header file.</span></span> <span data-ttu-id="c3548-150">ヘッダー ファイルが指定されていない場合、オプションは *nxd_ftp_client.h と nxd_ftp_server.h* の両方で使用できます。</span><span class="sxs-lookup"><span data-stu-id="c3548-150">If no header file is specified, the option is available in both *nxd_ftp_client.h and nxd_ftp_server.h*.</span></span> <span data-ttu-id="c3548-151">次の一覧で、それぞれについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="c3548-151">The following list describes each in detail:</span></span>

- <span data-ttu-id="c3548-152">**NX_FTP_SERVER_PRIORITY**: FTP サーバー スレッドの優先順位。</span><span class="sxs-lookup"><span data-stu-id="c3548-152">**NX_FTP_SERVER_PRIORITY** The priority of the FTP Server thread.</span></span> <span data-ttu-id="c3548-153">既定では、この値は優先順位 16 を示す 16 に定義されます。</span><span class="sxs-lookup"><span data-stu-id="c3548-153">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="c3548-154">**NX_FTP_MAX_CLIENTS**: サーバーで一度に処理できるクライアントの最大数。</span><span class="sxs-lookup"><span data-stu-id="c3548-154">**NX_FTP_MAX_CLIENTS** The maximum number of Clients the Server can handle at one time.</span></span> <span data-ttu-id="c3548-155">既定では、この値は、一度に 4 台のクライアントをサポートする 4 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c3548-155">By default, this value is 4 to support 4 Clients at once.</span></span>
- <span data-ttu-id="c3548-156">**NX_FTP_SERVER_MIN_PACKET_PAYLOAD**: TCP、IP、ネットワーク フレーム ヘッダー、および HTTP データを含む、サーバーのパケット プール ペイロードの最小サイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="c3548-156">**NX_FTP_SERVER_MIN_PACKET_PAYLOAD** The minimum size of the Server packet pool payload in bytes, including TCP, IP and network frame headers plus HTTP data.</span></span> <span data-ttu-id="c3548-157">既定値は、256 (FileX でのファイル名の最大長) + 12 バイト (ファイル情報用)、および NX_PHYSICAL_TRAILER です。</span><span class="sxs-lookup"><span data-stu-id="c3548-157">The default value is 256 (maximum length of filename in FileX) + 12 bytes for file information, and NX_PHYSICAL_TRAILER.</span></span>
- <span data-ttu-id="c3548-158">**NX_FTP_SERVER_TIMEOUT**: 内部サービスが中断される ThreadX ティック数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3548-158">**NX_FTP_SERVER_TIMEOUT** Specifies the number of ThreadX  ticks that internal services will  suspend for.</span></span> <span data-ttu-id="c3548-159">既定値は 1 秒 (1 \* NX_IP_PERIODIC_RATE) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c3548-159">The default value  is set to 1 second (1 \*  NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="c3548-160">**NX_FTP_ACTIVITY_TIMEOUT**: アクティビティがない場合にクライアント接続を維持する秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3548-160">**NX_FTP_ACTIVITY_TIMEOUT** Specifies the number of seconds  a Client connection is maintained  if there is no activity.</span></span> <span data-ttu-id="c3548-161">既定値は 240 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c3548-161">The default  value is set to 240.</span></span>
- <span data-ttu-id="c3548-162">**NX_FTP_TIMEOUT_PERIOD**: サーバーがクライアント アクティビティをチェックする間隔を秒単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="c3548-162">**NX_FTP_TIMEOUT_PERIOD** Specifies the intervals in seconds  when the Server checks for  Client activity.</span></span> <span data-ttu-id="c3548-163">既定値は 60 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c3548-163">The default value is set to 60.</span></span>
- <span data-ttu-id="c3548-164">**NX_FTP_SERVER_RETRY_SECONDS**: サーバーの応答を再送するまでの初期タイムアウトを秒単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="c3548-164">**NX_FTP_SERVER_RETRY_SECONDS** Specifies the initial timeout in seconds before retransmitting server response.</span></span> <span data-ttu-id="c3548-165">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="c3548-165">The default value is 2.</span></span>
- <span data-ttu-id="c3548-166">**NX_FTP_SERVER_TRANSMIT_QUEUE_DEPTH**: サーバー ソケットでキューに置かれた送信パケットの最大の深さを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3548-166">**NX_FTP_SERVER_TRANSMIT_QUEUE_DEPTH** Specifies the maximum of depth of queued transmit packets on Server socket.</span></span> <span data-ttu-id="c3548-167">既定値は 20 です。</span><span class="sxs-lookup"><span data-stu-id="c3548-167">The default value is 20.</span></span>
- <span data-ttu-id="c3548-168">**NX_FTP_SERVER_RETRY_MAX**: パケットあたりの最大再試行回数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3548-168">**NX_FTP_SERVER_RETRY_MAX** Specifies the maximum retries per packet.</span></span> <span data-ttu-id="c3548-169">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="c3548-169">The default value is 10.</span></span>
- <span data-ttu-id="c3548-170">**NX_FTP_SERVER_RETRY_SHIFT**: 再試行タイムアウトを設定するときにシフトするビット数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3548-170">**NX_FTP_SERVER_RETRY_SHIFT** Specifies the number of bits to shift in setting the retry timeout.</span></span> <span data-ttu-id="c3548-171">既定値は 2 です。たとえば、すべての再試行タイムアウトは、前の再試行の 2 倍の長さになります。</span><span class="sxs-lookup"><span data-stu-id="c3548-171">The default value is 2, e.g. every retry timeout is twice as long as the previous retry.</span></span>
- <span data-ttu-id="c3548-172">**NX_FTP_NO_FILEX**: このオプションを定義すると、FileX の依存関係のスタブが提供されます。</span><span class="sxs-lookup"><span data-stu-id="c3548-172">**NX_FTP_NO_FILEX** Defined, this option provides a  stub for FileX dependencies.</span></span> <span data-ttu-id="c3548-173">このオプションを定義した場合、変更なしで FTP クライアントが機能します。</span><span class="sxs-lookup"><span data-stu-id="c3548-173">The  FTP Client will function without  any change if this option is  defined.</span></span> <span data-ttu-id="c3548-174">FTP サーバーを適切に機能させるためには、変更するか、ユーザーがいくつかの FileX サービスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3548-174">The FTP Server will  need to either be modified or the  user will have to create a handful  of FileX services in order to  function properly.</span></span>
- <span data-ttu-id="c3548-175">**NX_FTP_CONTROL_TOS**: FTP 制御要求に必要なサービスの種類。</span><span class="sxs-lookup"><span data-stu-id="c3548-175">**NX_FTP_CONTROL_TOS** Type of service required for the FTP control requests.</span></span> <span data-ttu-id="c3548-176">既定では、この値は、通常の IP パケット サービスを示す NX_IP_NORMAL に定義されます。</span><span class="sxs-lookup"><span data-stu-id="c3548-176">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="c3548-177">**NX_FTP_DATA_TOS**: FTP データ要求に必要なサービスの種類。</span><span class="sxs-lookup"><span data-stu-id="c3548-177">**NX_FTP_DATA_TOS** Type of service required for the FTP data requests.</span></span> <span data-ttu-id="c3548-178">既定では、この値は、通常の IP パケット サービスを示す NX_IP_NORMAL に定義されます。</span><span class="sxs-lookup"><span data-stu-id="c3548-178">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="c3548-179">**NX_FTP_FRAGMENT_OPTION**: FTP 要求のフラグメントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c3548-179">**NX_FTP_FRAGMENT_OPTION** Fragment enable for FTP requests.</span></span> <span data-ttu-id="c3548-180">この値の既定値は NX_DONT_FRAGMENT であり、FTP TCP のフラグメント化が無効になります。</span><span class="sxs-lookup"><span data-stu-id="c3548-180">By default, this value is NX_DONT_FRAGMENT to disable FTP TCP fragmenting.</span></span>
- <span data-ttu-id="c3548-181">**NX_FTP_CONTROL_WINDOW_SIZE**: TCP 制御ソケット ウィンドウのサイズ。</span><span class="sxs-lookup"><span data-stu-id="c3548-181">**NX_FTP_CONTROL_WINDOW_SIZE** TCP Control socket window size.</span></span> <span data-ttu-id="c3548-182">既定では、この値は 400 バイトです。</span><span class="sxs-lookup"><span data-stu-id="c3548-182">By default, this value is 400 bytes.</span></span>
- <span data-ttu-id="c3548-183">**NX_FTP_DATA_WINDOW_SIZE**: TCP データ ソケット ウィンドウのサイズ。</span><span class="sxs-lookup"><span data-stu-id="c3548-183">**NX_FTP_DATA_WINDOW_SIZE** TCP Data socket window size.</span></span> <span data-ttu-id="c3548-184">既定では、この値は 2,048 バイトです。</span><span class="sxs-lookup"><span data-stu-id="c3548-184">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="c3548-185">**NX_FTP_TIME_TO_LIVE**: 破棄されるまでにこのパケットが通過できるルーターの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3548-185">**NX_FTP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="c3548-186">既定値は 0x80 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c3548-186">The default value is set to 0x80.</span></span>
- <span data-ttu-id="c3548-187">**NX_FTP_USERNAME_SIZE**: クライアントによって提供される *username* に許容されるバイト数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3548-187">**NX_FTP_USERNAME_SIZE** Specifies the number of bytes allowed in a Client supplied *username*.</span></span> <span data-ttu-id="c3548-188">既定値は 20 に設定されます *。*</span><span class="sxs-lookup"><span data-stu-id="c3548-188">The default value is set to 20 *.*</span></span>
- <span data-ttu-id="c3548-189">**NX_FTP_PASSWORD_SIZE**: クライアントによって提供される *password* に許容されるバイト数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3548-189">**NX_FTP_PASSWORD_SIZE** Specifies the number of bytes allowed in a client supplied *password*.</span></span> <span data-ttu-id="c3548-190">既定値は 20 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c3548-190">The default value is set to 20.</span></span>
