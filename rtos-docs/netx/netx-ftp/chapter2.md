---
title: 第 2 章 - Azure RTOS NetX FTP のインストールと使用
description: この章では、Azure RTOS NetX FTP コンポーネントのインストール、設定、使用に関連したさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 812422566b9761baac5f9c2477dba1f0fcc0a778
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811540"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-ftp"></a><span data-ttu-id="6c4a1-103">第 2 章 - Azure RTOS NetX FTP のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="6c4a1-103">Chapter 2 - Installation and use of Azure RTOS NetX FTP</span></span>

<span data-ttu-id="6c4a1-104">この章では、Azure RTOS NetX FTP コンポーネントのインストール、設定、使用に関連したさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX FTP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="6c4a1-105">製品の配布</span><span class="sxs-lookup"><span data-stu-id="6c4a1-105">Product Distribution</span></span>

<span data-ttu-id="6c4a1-106">Azure RTOS NetX は、[https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/]) のパブリック ソース コード リポジトリから入手できます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-106">Azure RTOS NetX can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/]).</span></span> <span data-ttu-id="6c4a1-107">このパッケージにはソース ファイル 2 つと、このドキュメントを含む PDF ファイル 1 つが含まれています。次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="6c4a1-108">**nx_ftp.h**: NetX 用 FTP のヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="6c4a1-108">**nx_ftp.h**: Header file for FTP for NetX</span></span>
- <span data-ttu-id="6c4a1-109">**nx_ftp_client.c**: NetX 用 FTP クライアントの C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="6c4a1-109">**nx_ftp_client.c**: C Source file for FTP Client for NetX</span></span>
- <span data-ttu-id="6c4a1-110">**nx_ftp_server.c**: NetX 用 FTP サーバーの C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="6c4a1-110">**nx_ftp_server.c**: C Source file for FTP Server for NetX</span></span>
- <span data-ttu-id="6c4a1-111">**filex_stub.h**: FileX が存在しない場合のスタブ ファイル</span><span class="sxs-lookup"><span data-stu-id="6c4a1-111">**filex_stub.h**: Stub file if FileX is not present</span></span>
- <span data-ttu-id="6c4a1-112">**nx_ftp.pdf**: NetX 用 FTP の PDF の説明</span><span class="sxs-lookup"><span data-stu-id="6c4a1-112">**nx_ftp.pdf**: PDF description of FTP for NetX</span></span>
- <span data-ttu-id="6c4a1-113">**demo_netx_ftp.c**: FTP デモンストレーション システム</span><span class="sxs-lookup"><span data-stu-id="6c4a1-113">**demo_netx_ftp.c**: FTP demonstration system</span></span>

## <a name="ftp-installation"></a><span data-ttu-id="6c4a1-114">FTP のインストール</span><span class="sxs-lookup"><span data-stu-id="6c4a1-114">FTP Installation</span></span>

<span data-ttu-id="6c4a1-115">NetX 用 FTP を使用するには、前述のディストリビューション全体を、NetX がインストールされているのと同じディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-115">In order to use FTP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="6c4a1-116">たとえば、NetX が " *\threadx\arm7\green*" ディレクトリにインストールされている場合は、*nx_ftp.h*、*nx_ftp_client.c*、および *nx_ftp_server.c* ファイルをこのディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-116">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_ftp.h*, *nx_ftp_client.c*, and *nx_ftp_server.c* files should be copied into this directory.</span></span>

## <a name="using-ftp"></a><span data-ttu-id="6c4a1-117">FTP を使用する</span><span class="sxs-lookup"><span data-stu-id="6c4a1-117">Using FTP</span></span>

<span data-ttu-id="6c4a1-118">NetX 用 FTP は簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-118">Using FTP for NetX is easy.</span></span> <span data-ttu-id="6c4a1-119">ThreadX、FileX、および NetX を使用するためには、基本的に、アプリケーションのコードでそれぞれ *tx_api.h、fx_api.h、* および *nx_api.h* をインクルードしてから *nx_ftp.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-119">Basically, the application code must include *nx_ftp.h* after it includes *tx_api.h, fx_api.h,* and *nx_api.h*, in order to use ThreadX, FileX, and NetX, respectively.</span></span> <span data-ttu-id="6c4a1-120">*nx_ftp.h* をインクルードすると、アプリケーション コードで、このガイドで後述する FTP 関数呼び出しを行うことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-120">Once *nx_ftp.h* is included, the application code is then able to make the FTP function calls specified later in this guide.</span></span> <span data-ttu-id="6c4a1-121">また、アプリケーションでは、ビルド プロセスに *nx_ftp_client.c* と *nx_ftp_server.c* もインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-121">The application must also include *nx_ftp_client.c* and *nx_ftp_server.c* in the build process.</span></span> <span data-ttu-id="6c4a1-122">これらのファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、そのオブジェクト形式をアプリケーションのファイルと一緒にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-122">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="6c4a1-123">NetX FTP を使用するために必要なことはこれだけです。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-123">This is all that is required to use NetX FTP.</span></span>

> [!NOTE]
> <span data-ttu-id="6c4a1-124">FTP では NetX TCP サービスを利用するため、FTP を使用する前に、*nx_tcp_enable* を呼び出して TCP を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-124">Since FTP utilizes NetX TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using FTP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="6c4a1-125">小規模のシステム例</span><span class="sxs-lookup"><span data-stu-id="6c4a1-125">Small Example System</span></span>

<span data-ttu-id="6c4a1-126">NetX FTP の使用がいかに簡単であるかを示す例を、下の図 1.1 に示します。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-126">An example of how easy it is to use NetX FTP is described in Figure 1.1 that appears below.</span></span>

> [!NOTE]
> <span data-ttu-id="6c4a1-127">これは、1 つのネットワーク インターフェイスを持つホスト デバイス用です。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-127">This is for a host device with a single network interface.</span></span>

<span data-ttu-id="6c4a1-128">この例では、FTP インクルード ファイル *nx_ftp_client.h* と *nx_ftp_server.h* が 10 行目と 11 行目で取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-128">In this example, the FTP include file *nx_ftp_client.h* and *nx_ftp_server.h* are brought at line 10 and 11.</span></span> <span data-ttu-id="6c4a1-129">次に、FTP サーバーが "*tx_application_define*" の 134 行目に作成されます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-129">Next, the FTP Server is created in "*tx_application_define*" at line 134.</span></span> <span data-ttu-id="6c4a1-130">FTP サーバー制御ブロック "*Server*" は、31 行目でグローバル変数として既に定義されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-130">Note that the FTP Server control block "*Server*" was defined as a global variable at line 31 previously.</span></span> <span data-ttu-id="6c4a1-131">正常に作成されると、363 行目で FTP サーバーが起動されます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-131">After successful creation, an FTP Server is started at line 363.</span></span> <span data-ttu-id="6c4a1-132">183 行目では、FTP クライアントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-132">At line 183 the FTP Client is created.</span></span> <span data-ttu-id="6c4a1-133">最後に、クライアントによって 229 行目でファイルが書き込まれ、318 行目でファイルが読み取られます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-133">And finally, the Client writes the file at line 229 and reads the file back at line 318.</span></span>

```c
/* This is a small demo of NetX FTP on the high-performance NetX TCP/IP stack. This demo
relies on ThreadX, NetX, and FileX to show a simple file transfer from the client
and then back to the server. */

#include     "tx_api.h"
#include     "fx_api.h"
#include     "nx_api.h"
#include     "nx_ftp_client.h"
#include     "nx_ftp_server.h"

#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX, NetX, and FileX object control blocks... */

TX_THREAD          server_thread;
TX_THREAD          client_thread;
NX_PACKET_POOL     server_pool;
NX_IP              server_ip;
NX_PACKET_POOL     client_pool;
NX_IP              client_ip;
FX_MEDIA           ram_disk;

/* Define the NetX FTP object control blocks. */

NX_FTP_CLIENT     ftp_client;
NX_FTP_SERVER     ftp_server;

/* Define the counters used in the demo application... */

ULONG     error_counter = 0;

/* Define the memory area for the FileX RAM disk. */

UCHAR     ram_disk_memory[32000];
UCHAR     ram_disk_sector_cache[512];

#define FTP_SERVER_ADDRESS IP_ADDRESS(1,2,3,4)
#define FTP_CLIENT_ADDRESS IP_ADDRESS(1,2,3,5)

extern UINT _fx_media_format(FX_MEDIA *media_ptr, VOID (*driver)(FX_MEDIA *media),
                    VOID *driver_info_ptr, UCHAR *memory_ptr, UINT memory_size,
                    CHAR *volume_name, UINT number_of_fats, UINT directory_entries,
                    UINT hidden_sectors, ULONG total_sectors, UINT bytes_per_sector,
                    UINT sectors_per_cluster, UINT heads, UINT sectors_per_track);

/* Define the FileX and NetX driver entry functions. */
VOID     _fx_ram_driver(FX_MEDIA *media_ptr);

/* Replace the 'ram' driver with your own Ethernet driver. */
VOID     _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

void     client_thread_entry(ULONG thread_input);
void     thread_server_entry(ULONG thread_input);

/* Define server login/logout functions. These are stubs for functions that would
validate a client login request. */

UINT     server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                ULONG client_ip_address, UINT client_port, CHAR *name,
                CHAR *password, CHAR *extra_info);

UINT     server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    ULONG client_ip_address, UINT client_port, CHAR *name,
                    CHAR *password, CHAR *extra_info);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
    return(0);
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{

UINT      status;
UCHAR     *pointer;

    /* Setup the working pointer. */
    pointer = (UCHAR *) first_unused_memory;

    /* Create a helper thread for the server. */
    tx_thread_create(&server_thread, "FTP Server thread", thread_server_entry,
                    0, pointer, DEMO_STACK_SIZE,
                    4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize NetX. */
    nx_system_initialize();

    /* Create the packet pool for the FTP Server. */
    status = nx_packet_pool_create(&server_pool, "NetX Server Packet Pool",
                                    256, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Create the IP instance for the FTP Server. */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance",
                        FTP_SERVER_ADDRESS, 0xFFFFFF00UL, &server_pool,
                        _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Enable ARP and supply ARP cache memory for server IP instance. */
    nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP. */
    nx_tcp_enable(&server_ip);

    /* Create the FTP server. */
    status = nx_ftp_server_create(&ftp_server, "FTP Server Instance",
                    &server_ip, &ram_disk, pointer, DEMO_STACK_SIZE,
                    &server_pool, server_login, server_logout);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Now set up the FTP Client. */

    /* Create the main FTP client thread. */
    status = tx_thread_create(&client_thread, "FTP Client thread ",
                            client_thread_entry, 0,
                            pointer, DEMO_STACK_SIZE,
                            6, 6, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create a packet pool for the FTP client. */
    status = nx_packet_pool_create(&client_pool, "NetX Client Packet Pool",
                                    256, pointer, 8192);
    pointer = pointer + 8192;

    /* Create an IP instance for the FTP client. */
    status = nx_ip_create(&client_ip, "NetX Client IP Instance", FTP_CLIENT_ADDRESS,
            0xFFFFFF00UL, &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for the FTP Client IP. */
    nx_arp_enable(&client_ip, (void *) pointer, 1024);

    pointer = pointer + 1024;

    /* Enable TCP for client IP instance. */
    nx_tcp_enable(&client_ip);

    return;
}

/* Define the FTP client thread. */
void     client_thread_entry(ULONG thread_input)
{

NX_PACKET     *my_packet;
UINT          status;

    /* Format the RAM disk - the memory for the RAM disk was defined above. */
    status = _fx_media_format(&ram_disk,
            _fx_ram_driver, /* Driver entry */
            ram_disk_memory, /* RAM disk memory pointer */
            ram_disk_sector_cache, /* Media buffer pointer */
            sizeof(ram_disk_sector_cache), /* Media buffer size */
            "MY_RAM_DISK", /* Volume Name */
            1, /* Number of FATs */
            32, /* Directory Entries */
            0, /* Hidden sectors */
            256, /* Total sectors */
            128, /* Sector size */
            1, /* Sectors per cluster */
            1, /* Heads */
            1); /* Sectors per track */

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Open the RAM disk. */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory,
                            ram_disk_sector_cache, sizeof(ram_disk_sector_cache));

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

     /* Let the IP threads and driver initialize the system. */
    tx_thread_sleep(100);

    /* Create an FTP client. */
    status = nx_ftp_client_create(&ftp_client, "FTP Client", &client_ip, 2000, &client_pool);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Created the FTP Client\n");

    /* Now connect with the NetX FTP (IPv4) server. */
    status = nx_ftp_client_connect(&ftp_client, FTP_SERVER_ADDRESS,
                                    "name", "password", 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Connected to the FTP Server\n");

    /* Open a FTP file for writing. */
    status = nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_WRITE, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Opened the FTP client test.txt file\n");

    /* Allocate a FTP packet. */
    status = nx_packet_allocate(&client_pool, &my_packet, NX_TCP_PACKET, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Write ABCs into the packet payload! */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ ", 28);

    /* Adjust the write pointer. */
    my_packet -> nx_packet_length = 28;
    my_packet -> nx_packet_append_ptr = my_packet -> nx_packet_prepend_ptr + 28;

    /* Write the packet to the file test.txt. */
    status = nx_ftp_client_file_write(&ftp_client, my_packet, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
        printf("Wrote to the FTP client test.txt file\n");

    /* Close the file. */
    status = nx_ftp_client_file_close(&ftp_client, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Closed the FTP client test.txt file\n");

    /* Now open the same file for reading. */
    status = nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_READ, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;

    else
        printf("Reopened the FTP client test.txt file\n");

    /* Read the file. */
    status = nx_ftp_client_file_read(&ftp_client, &my_packet, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
    else
    {
        printf("Reread the FTP client test.txt file\n");
        nx_packet_release(my_packet);
    }

    /* Close this file. */
    status = nx_ftp_client_file_close(&ftp_client, 100);

    if (status != NX_SUCCESS)
        error_counter++;

    /* Disconnect from the server. */
    status = nx_ftp_client_disconnect(&ftp_client, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;

    /* Delete the FTP client. */
    status = nx_ftp_client_delete(&ftp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
}

/* Define the helper FTP server thread. */
void     thread_server_entry(ULONG thread_input)
{

UINT     status;

    /* Wait till the IP thread and driver have initialized the system. */
    tx_thread_sleep(100);

    /* OK to start the FTP Server. */
    status = nx_ftp_server_start(&ftp_server);

    if (status != NX_SUCCESS)
        error_counter++;

    printf("Server started!\n");

    /* FTP server ready to take requests! */

    /* Let the IP threads execute. */
    tx_thread_relinquish();

    return;
}

UINT     server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                ULONG client_ip_address, UINT client_port,
                CHAR *name, CHAR *password, CHAR *extra_info)
{

    printf("Logged in!\n");
    /* Always return success. */
    return(NX_SUCCESS);
}

UINT     server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    ULONG client_ip_address, UINT client_port,
                    CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out!\n");

    /* Always return success. */
    return(NX_SUCCESS);
}
```

<span data-ttu-id="6c4a1-134">図 1.1 NetX を使用した FTP クライアントとサーバーの例 (単一ネットワーク インターフェイス ホスト)</span><span class="sxs-lookup"><span data-stu-id="6c4a1-134">Figure 1.1 Example of FTP Client and Server with NetX (Single network interface host)</span></span>

## <a name="configuration-options"></a><span data-ttu-id="6c4a1-135">構成オプション</span><span class="sxs-lookup"><span data-stu-id="6c4a1-135">Configuration Options</span></span>

<span data-ttu-id="6c4a1-136">NetX 用 FTP を構築するための構成オプションがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-136">There are several configuration options for building FTP for NetX.</span></span> <span data-ttu-id="6c4a1-137">次の一覧で、それぞれについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-137">The following list describes each in detail:</span></span>  

- <span data-ttu-id="6c4a1-138">**NX_FTP_SERVER_PRIORITY**: FTP サーバーのスレッドの優先順位。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-138">**NX_FTP_SERVER_PRIORITY**: The priority of the FTP Server thread.</span></span> <span data-ttu-id="6c4a1-139">既定では、この値は 16 に定義され、優先順位 16 を示します。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-139">By default, this value is defined as 16 to specify priority 16.</span></span>

- <span data-ttu-id="6c4a1-140">**NX_FTP_MAX_CLIENTS**: サーバーで一度に処理できるクライアントの最大数。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-140">**NX_FTP_MAX_CLIENTS**: The maximum number of Clients the Server can handle at one time.</span></span> <span data-ttu-id="6c4a1-141">既定では、一度に 4 個のクライアントをサポートするために、この値は 4 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-141">By default, this value is 4 to support 4 Clients at once.</span></span>

- <span data-ttu-id="6c4a1-142">**NX_FTP_SERVER_MIN_PACKET_PAYLOAD**: TCP、IP、ネットワーク フレーム ヘッダーと HTTP データを含む、サーバーのパケット プール ペイロードの最小サイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-142">**NX_FTP_SERVER_MIN_PACKET_PAYLOAD**: The minimum size of the Server packet pool payload in bytes, including TCP, IP and network frame headers plus HTTP data.</span></span> <span data-ttu-id="6c4a1-143">既定値は、256 (FileX でのファイル名の最大長) + 12 バイト (ファイル情報用)、および NX_PHYSICAL_TRAILER です。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-143">The default value is 256 (maximum length of filename in FileX) + 12 bytes for file information, and NX_PHYSICAL_TRAILER.</span></span>

- <span data-ttu-id="6c4a1-144">**NX_FTP_NO_FILEX**: このオプションを定義すると、FileX の依存関係のスタブが提供されます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-144">**NX_FTP_NO_FILEX**: Defined, this option provides a stub for FileX dependencies.</span></span> <span data-ttu-id="6c4a1-145">このオプションを定義しても、FTP クライアントは変更なしで機能します。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-145">The FTP Client will function without any change if this option is defined.</span></span> <span data-ttu-id="6c4a1-146">FTP サーバーが適切に機能するためには、変更するか、ユーザーがいくつかの FileX サービスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-146">The FTP Server will need to either be modified or the user will have to create a handful of FileX services in order to function properly.</span></span>

- <span data-ttu-id="6c4a1-147">**NX_FTP_CONTROL_TOS**: FTP TCP 制御要求に必要なサービスの種類。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-147">**NX_FTP_CONTROL_TOS**: Type of service required for the FTP TCP control requests.</span></span> <span data-ttu-id="6c4a1-148">既定では、この値は通常の IP パケット サービスを示す NX_IP_NORMAL として定義されています。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-148">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span> <span data-ttu-id="6c4a1-149">この定義は、*nx_ftp.h* をインクルードする前にアプリケーションで設定できます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-149">This define can be set by the application prior to inclusion of *nx_ftp.h*.</span></span>

- <span data-ttu-id="6c4a1-150">**NX_FTP_DATA_TOS**: FTP TCP データ要求に必要なサービスの種類。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-150">**NX_FTP_DATA_TOS**: Type of service required for the FTP TCP data requests.</span></span> <span data-ttu-id="6c4a1-151">既定では、この値は通常の IP パケット サービスを示す NX_IP_NORMAL として定義されています。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-151">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span> <span data-ttu-id="6c4a1-152">この定義は、*nx_ftp.h* をインクルードする前にアプリケーションで設定できます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-152">This define can be set by the application prior to inclusion of *nx_ftp.h*.</span></span>

- <span data-ttu-id="6c4a1-153">**NX_FTP_FRAGMENT_OPTION**: FTP TCP 要求のフラグメントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-153">**NX_FTP_FRAGMENT_OPTION**: Fragment enable for FTP TCP requests.</span></span> <span data-ttu-id="6c4a1-154">この値の既定値は NX_DONT_FRAGMENT であり、FTP TCP のフラグメント化が無効になります。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-154">By default, this value is NX_DONT_FRAGMENT to disable FTP TCP fragmenting.</span></span> <span data-ttu-id="6c4a1-155">この定義は、*nx_ftp.h* をインクルードする前にアプリケーションで設定できます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-155">This define can be set by the application prior to inclusion of *nx_ftp.h*.</span></span>

- <span data-ttu-id="6c4a1-156">**NX_FTP_CONTROL_WINDOW_SIZE**: 制御ソケット ウィンドウのサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-156">**NX_FTP_CONTROL_WINDOW_SIZE**: Control socket window size.</span></span> <span data-ttu-id="6c4a1-157">既定では、この値は 400 バイトです。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-157">By default, this value is 400 bytes.</span></span> <span data-ttu-id="6c4a1-158">この定義は、*nx_ftp.h* をインクルードする前にアプリケーションで設定できます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-158">This define can be set by the application prior to inclusion of *nx_ftp.h*.</span></span>

- <span data-ttu-id="6c4a1-159">**NX_FTP_DATA_WINDOW_SIZE**: データ ソケット ウィンドウのサイズ。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-159">**NX_FTP_DATA_WINDOW_SIZE**: Data socket window size.</span></span> <span data-ttu-id="6c4a1-160">既定では、この値は 2,048 バイトです。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-160">By default, this value is 2048 bytes.</span></span> <span data-ttu-id="6c4a1-161">この定義は、*nx_ftp.h* をインクルードする前にアプリケーションで設定できます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-161">This define can be set by the application prior to inclusion of *nx_ftp.h*.</span></span>

- <span data-ttu-id="6c4a1-162">**NX_FTP_TIME_TO_LIVE**: このパケットが破棄されるまでに通過できるルーターの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-162">**NX_FTP_TIME_TO_LIVE**: Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="6c4a1-163">既定値は 0x80 に設定されていますが、*nx_ftp.h* をインクルードする前に再定義できます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-163">The default value is set to 0x80, but can be redefined prior to inclusion of *nx_ftp.h.*</span></span>

- <span data-ttu-id="6c4a1-164">**NX_FTP_SERVER_TIMEOUT**: 内部サービスが中断される ThreadX ティックの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-164">**NX_FTP_SERVER_TIMEOUT**: Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="6c4a1-165">既定値は 100 に設定されていますが、*nx_ftp.h* をインクルードする前に再定義できます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-165">The default value is set to 100, but can be redefined prior to inclusion of *nx_ftp.h.*</span></span>

- <span data-ttu-id="6c4a1-166">**NX_FTP_USERNAME_SIZE**: クライアントによって指定される "*ユーザー名*" に許容されるバイト数を指定します。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-166">**NX_FTP_USERNAME_SIZE**: Specifies the number of bytes allowed in a client supplied *username*.</span></span> <span data-ttu-id="6c4a1-167">既定値は 20 に設定されていますが、*nx_ftp.h* をインクルードする前に再定義できます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-167">The default value is set to 20, but can be redefined prior to inclusion of *nx_ftp.h.*</span></span>

- <span data-ttu-id="6c4a1-168">**NX_FTP_PASSWORD_SIZE**: クライアントによって指定される "*パスワード*" に許容されるバイト数を指定します。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-168">**NX_FTP_PASSWORD_SIZE**: Specifies the number of bytes allowed in a client supplied *password*.</span></span> <span data-ttu-id="6c4a1-169">既定値は 20 に設定されていますが、*nx_ftp.h* をインクルードする前に再定義できます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-169">The default value is set to 20, but can be redefined prior to inclusion of *nx_ftp.h.*</span></span>

- <span data-ttu-id="6c4a1-170">**NX_FTP_ACTIVITY_TIMEOUT**: アクティビティがない場合にクライアント接続を維持する秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-170">**NX_FTP_ACTIVITY_TIMEOUT**: Specifies the number of seconds a client connection is maintained if there is no activity.</span></span> <span data-ttu-id="6c4a1-171">既定値は 240 に設定されていますが、*nx_ftp.h* をインクルードする前に再定義できます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-171">The default value is set to 240, but can be redefined prior to inclusion of *nx_ftp.h.*</span></span>

- <span data-ttu-id="6c4a1-172">**NX_FTP_TIMEOUT_PERIOD**: サーバーによってクライアントの非アクティブ状態がチェックされる間隔を秒数で指定します。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-172">**NX_FTP_TIMEOUT_PERIOD**: Specifies the number of seconds between the Server checking for client inactivity.</span></span> <span data-ttu-id="6c4a1-173">既定値は 60 に設定されていますが、*nx_ftp.h* をインクルードする前に再定義できます。</span><span class="sxs-lookup"><span data-stu-id="6c4a1-173">The default value is set to 60, but can be redefined prior to inclusion of *nx_ftp.h.*</span></span>
