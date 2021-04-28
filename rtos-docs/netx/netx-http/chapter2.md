---
title: 第 2 章 - NetX HTTP のインストールと使用
description: この章では、NetX HTTP コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: db621e38e9d2324ca3ce2398aee9f729b05886ee
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811531"
---
# <a name="chapter-2---installation-and-use-of-netx-http"></a><span data-ttu-id="5e7e5-103">第 2 章 - NetX HTTP のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="5e7e5-103">Chapter 2 - Installation and use of NetX HTTP</span></span>

<span data-ttu-id="5e7e5-104">この章では、NetX HTTP コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX HTTP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="5e7e5-105">製品ディストリビューション</span><span class="sxs-lookup"><span data-stu-id="5e7e5-105">Product Distribution</span></span>

<span data-ttu-id="5e7e5-106">Azure RTOS NetX は、[https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) のパブリック ソース コード リポジトリから入手できます。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-106">Azure RTOS NetX can be obtained from our public source code repository at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span>

- <span data-ttu-id="5e7e5-107">**nx_http_client.h**: NetX 用 HTTP クライアントのヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="5e7e5-107">**nx_http_client.h** Header file for HTTP Client for NetX</span></span>
- <span data-ttu-id="5e7e5-108">**nx_http_server.h**: NetX 用 HTTP サーバーのヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="5e7e5-108">**nx_http_server.h** Header file for HTTP Server for NetX</span></span>
- <span data-ttu-id="5e7e5-109">**nx_http_client.c**: NetX 用 HTTP クライアントの C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="5e7e5-109">**nx_http_client.c** C Source file for HTTP Client for NetX</span></span>
- <span data-ttu-id="5e7e5-110">**nx_http_server.c**: NetX 用 HTTP サーバーの C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="5e7e5-110">**nx_http_server.c** C Source file for HTTP Server for NetX</span></span>
- <span data-ttu-id="5e7e5-111">**nx_md5.c**: MD5 ダイジェスト アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="5e7e5-111">**nx_md5.c** MD5 digest algorithms</span></span>
- <span data-ttu-id="5e7e5-112">**filex_stub.h**: FileX が存在しない場合のスタブ ファイル</span><span class="sxs-lookup"><span data-stu-id="5e7e5-112">**filex_stub.h** Stub file if FileX is not present</span></span>
- <span data-ttu-id="5e7e5-113">**nx_http.pdf**: NetX 用 HTTP の説明</span><span class="sxs-lookup"><span data-stu-id="5e7e5-113">**nx_http.pdf** Description of HTTP for NetX</span></span>
- <span data-ttu-id="5e7e5-114">**demo_netx_http.c**: NetX HTTP のデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="5e7e5-114">**demo_netx_http.c** NetX HTTP demonstration</span></span>

## <a name="http-installation"></a><span data-ttu-id="5e7e5-115">HTTP のインストール</span><span class="sxs-lookup"><span data-stu-id="5e7e5-115">HTTP Installation</span></span>

<span data-ttu-id="5e7e5-116">NetX 用 HTTP を使用するには、前述のディストリビューション全体を、NetX がインストールされているのと同じディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-116">In order to use HTTP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="5e7e5-117">たとえば、NetX が " *\threadx\arm7\green*" ディレクトリにインストールされている場合は、NetX HTTP クライアント アプリケーションの *nx_http_client.h* と *nx_http_client.c*、NetX HTTP サーバー アプリケーションの *nx_http_server.h* と *nx_http_server.c*、および</span><span class="sxs-lookup"><span data-stu-id="5e7e5-117">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_http_client.h* and *nx_http_client.c* for NetX HTTP Client applications, and *nx_http_server.h* and *nx_http_server.c* for NetX HTTP Server applications.</span></span> <span data-ttu-id="5e7e5-118">*nx_md5.c* をこのディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-118">*nx_md5.c* should be copied into this directory.</span></span> <span data-ttu-id="5e7e5-119">デモの "ram driver" アプリケーションの場合、NetX HTTP クライアントとサーバーのファイルを同じディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-119">For the demo ‘ram driver’ application NetX HTTP Client and Server files should be copied into the same directory.</span></span>

## <a name="using-http"></a><span data-ttu-id="5e7e5-120">HTTP の使用</span><span class="sxs-lookup"><span data-stu-id="5e7e5-120">Using HTTP</span></span>

<span data-ttu-id="5e7e5-121">NetX 用 HTTP は簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-121">Using HTTP for NetX is easy.</span></span> <span data-ttu-id="5e7e5-122">基本的には、ThreadX、FileX、NetX を使用するために、アプリケーション コードにそれぞれ *tx_api.h、fx_api.h*、*nx_api.h* をインクルードした後に、*nx_http_client.h* または *nx_http_server.h*、あるいはこの両方をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-122">Basically, the application code must include *nx_http_client.h* and/or *nx_http_server.h* after it includes *tx_api.h, fx_api.h,* and *nx_api.h*, in order to use ThreadX, FileX, and NetX, respectively.</span></span> <span data-ttu-id="5e7e5-123">HTTP ヘッダー ファイルをインクルードすると、アプリケーション コードで、このガイドで後述する HTTP 関数呼び出しを行えるようになります。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-123">Once the HTTP header files are included, the application code is then able to make the HTTP function calls specified later in this guide.</span></span> <span data-ttu-id="5e7e5-124">アプリケーションでは、ビルド プロセスで *nx_http_client.c*、*nx_http_server.c*、*md5.c* もインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-124">The application must also include *nx_http_client.c*, *nx_http_server.c*, and *md5.c* in the build process.</span></span> <span data-ttu-id="5e7e5-125">これらのファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、そのオブジェクト フォームをアプリケーションのファイルと一緒にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-125">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="5e7e5-126">NetX HTTP を使用するために必要なことはこれだけです。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-126">This is all that is required to use NetX HTTP.</span></span>

>[!NOTE] 
> <span data-ttu-id="5e7e5-127">ビルド プロセスで NX_HTTP_DIGEST_ENABLE が指定されていない場合は、アプリケーションに *md5.c* ファイルを追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-127">If NX_HTTP_DIGEST_ENABLE is not specified in the build process, the *md5.c* file does not need to be added to the application.</span></span> <span data-ttu-id="5e7e5-128">同様に、HTTP クライアント機能が不要な場合は、*nx_http_client.c* ファイルを省略できます。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-128">Similarly, if no HTTP Client capabilities are required, the *nx_http_client.c* file may be omitted.</span></span>

>[!NOTE] 
> <span data-ttu-id="5e7e5-129">HTTP では NetX TCP サービスを利用するため、HTTP を使用する前に、*nx_tcp_enable* を呼び出して TCP を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-129">Since HTTP utilizes NetX TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using HTTP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="5e7e5-130">簡単なシステムの例</span><span class="sxs-lookup"><span data-stu-id="5e7e5-130">Small Example System</span></span>

<span data-ttu-id="5e7e5-131">NetX HTTP の使用がいかに簡単であるかを示す例を、下の図 1.1 に示します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-131">An example of how easy it is to use NetX HTTP is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="5e7e5-132">この例では、HTTP インクルード ファイル "*nx_http_client.h と nx_http_server.h*" が 8 行目で取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-132">In this example, the HTTP include file *nx_http_client.h and nx_http_server.h are* brought in at line 8.</span></span> <span data-ttu-id="5e7e5-133">次に、131 行目の "*tx_application_define*" で HTTP サーバーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-133">Next, the HTTP Server is created in “*tx_application_define*” at line 131.</span></span>

>[!NOTE] 
> <span data-ttu-id="5e7e5-134">HTTP サーバー制御ブロック "*Server*" は、25 行目でグローバル変数として既に定義されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-134">The HTTP Server control block “*Server*” was defined as a global variable at line 25 previously.</span></span>

<span data-ttu-id="5e7e5-135">正常に作成されると、136 行目で HTTP サーバーが起動されます。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-135">After successful creation, an HTTP Server is started at line 136.</span></span> <span data-ttu-id="5e7e5-136">149 行目で、HTTP クライアントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-136">At line 149 the HTTP Client is created.</span></span> <span data-ttu-id="5e7e5-137">最後に、クライアントは、157 行目でファイルを書き込み、195 行目でファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-137">And finally, the Client writes the file at line 157 and reads the file back at line 195.</span></span>

```c
/* This is a small demo of HTTP on the high-performance NetX TCP/IP stack.
This demo relies on ThreadX, NetX, and FileX to show a simple HTML
transfer from the client and then back from the server. */

#include "tx_api.h"
#include "fx_api.h"
#include "nx_api.h"
#include "nx_http_client.h"
#include "nx_http_server.h"
#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_0;
TX_THREAD         thread_1;
NX_PACKET_POOL    pool_0;
NX_PACKET_POOL    pool_1;
NX_IP             ip_0;
NX_IP             ip_1;
FX_MEDIA          ram_disk;

/* Define HTTP objects. */

NX_HTTP_SERVER    my_server;
NX_HTTP_CLIENT    my_client;

/* Define the counters used in the demo application... */

ULONG             error_counter;

/* Define the RAM disk memory. */

UCHAR             ram_disk_memory[32000];

/* Define function prototypes. */

void     thread_0_entry(ULONG thread_input);
VOID     _fx_ram_driver(FX_MEDIA *media_ptr) ;
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
UINT     authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, CHAR **name, CHAR **password, 
                              CHAR **realm);

/* Define the application's authentication check. This is called by
the HTTP server whenever a new request is received. */
UINT authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
                         CHAR *resource, CHAR **name, CHAR **password, 
                         CHAR **realm);
{

    /* Just use a simple name, password, and realm for all
    requests and resources. */
    *name = "name";
    *password = "password";
    *realm = "NetX HTTP demo";

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void     tx_application_define(void *first_unused_memory)
{

CHAR     *pointer;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
                    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create packet pool. */
    nx_packet_pool_create(&pool_0, "NetX Packet Pool 0",
                         600, pointer, 8192);
                         pointer = pointer + 8192;

    /* Create an IP instance. */
    nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(1, 2, 3, 4),
                0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                pointer, 4096, 1);
                pointer = pointer + 4096;

    /* Create another packet pool. */
    nx_packet_pool_create(&pool_1, "NetX Packet Pool 1", 600, pointer, 8192);
                         pointer = pointer + 8192;

    /* Create another IP instance. */
    nx_ip_create(&ip_1, "NetX IP Instance 1", IP_ADDRESS(1, 2, 3, 5),
                0xFFFFFF00UL, &pool_1, _nx_ram_network_driver,
                pointer, 4096, 1);
                pointer = pointer + 4096;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    nx_arp_enable(&ip_0, (void *) pointer, 1024);
                 pointer = pointer + 1024;

    /* Enable ARP and supply ARP cache memory for IP Instance 1. */
    nx_arp_enable(&ip_1, (void *) pointer, 1024);
                 pointer = pointer + 1024;

    /* Enable TCP processing for both IP instances. */
    nx_tcp_enable(&ip_0);
    nx_tcp_enable(&ip_1);

    /* Open the RAM disk. */
                 _fx_ram_driver, ram_disk_memory, pointer, 4096) ;
                 pointer += 4096;

    /* Create the NetX HTTP Server. */
    nx_http_server_create(&my_server, "My HTTP Server", &ip_1, &ram_disk,
                         pointer, 4096, &pool_1, authentication_check, NX_NULL);
                         pointer = pointer + 4096;

    /* Start the HTTP Server. */
    nx_http_server_start(&my_server);
}

/* Define the test thread. */
void     thread_0_entry(ULONG thread_input)
{

NX_PACKET     *my_packet;
UINT          status;

    /* Create an HTTP client instance. */
    status = nx_http_client_create(&my_client, "My Client", &ip_0,
                                  &pool_0, 600);

    /* Check status. */
    if (status)
        error_counter++;

    /* Prepare to send the simple 103-byte HTML file to the Server. */
    status = nx_http_client_put_start(&my_client, IP_ADDRESS(1,2,3,5),
                                      "/test.htm", "name", "password", 103, 50);
    /* Check status. */
    if (status)
        error_counter++;

    /* Allocate a packet. */
    status = nx_packet_allocate(&pool_0, &my_packet, NX_TCP_PACKET,
                               NX_WAIT_FOREVER);
    /* Check status. */
    if (status != NX_SUCCESS)
        return;

    /* Build a simple 103-byte HTML page. */
    nx_packet_data_append(my_packet, "<HTML>\r\n", 8,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet,
                         "<HEAD><TITLE>NetX HTTP Test</TITLE></HEAD>\r\n", 44,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<BODY>\r\n", 8,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<H1>NetX Test Page</H1>\r\n", 25,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</BODY>\r\n", 9,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</HTML>\r\n", 9,
                         &pool_0, NX_WAIT_FOREVER);

    /* Complete the PUT by writing the total length. */
    status = **nx_http_client_put_packet**(&my_client, my_packet, 50);

    /* Check status. */
    if (status)
        error_counter++;

    /* Now GET the file back! */
    status = nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
                                     "/test.htm", NX_NULL, 0, "name", 
                                     "password", 50);

    /* Check status. */
    if (status)
        error_counter++;

    /* Get a packet. */
    status = nx_http_client_get_packet(&my_client, &my_packet, 20);

    /* Check for an error. */
    if ((status) || (my_packet -> nx_packet_length != 103))
        error_counter++;

    /* Check to see if we have a packet. */
    if (status == NX_SUCCESS)
    {

        /* Yes, release it! */
        nx_packet_release(my_packet);
    }

    /* Flush the media. */
     fx_media_flush(&ram_disk);
 }
```

<span data-ttu-id="5e7e5-138">図 1.1 NetX での HTTP の使用例</span><span class="sxs-lookup"><span data-stu-id="5e7e5-138">Figure 1.1 Example of HTTP use with NetX</span></span>

## <a name="configuration-options"></a><span data-ttu-id="5e7e5-139">構成オプション</span><span class="sxs-lookup"><span data-stu-id="5e7e5-139">Configuration Options</span></span>

<span data-ttu-id="5e7e5-140">NetX 用 HTTP を構築するための構成オプションがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-140">There are several configuration options for building HTTP for NetX.</span></span> <span data-ttu-id="5e7e5-141">すべてのオプションとそれぞれの詳細を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-141">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="5e7e5-142">既定値が示されていますが、"*nx_http_client.h と nx_http_server.h*" をインクルードする前に再定義できます。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-142">The default values are listed, but can be redefined prior to inclusion of *nx_http_client.h and nx_http_server.h*:</span></span>

- <span data-ttu-id="5e7e5-143">**NX_DISABLE_ERROR_CHECKING**: このオプションを定義すると、基本的な HTTP エラー チェックが削除されます。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-143">**NX_DISABLE_ERROR_CHECKING** Defined, this option removes the basic HTTP error checking.</span></span> <span data-ttu-id="5e7e5-144">通常は、アプリケーションがデバッグされた後に使用されます。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-144">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="5e7e5-145">**NX_HTTP_SERVER_PRIORITY**: HTTP サーバーのスレッドの優先順位。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-145">**NX_HTTP_SERVER_PRIORITY** The priority of the HTTP Server thread.</span></span> <span data-ttu-id="5e7e5-146">既定では、この値は 16 番目の優先順位を示す 16 に定義されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-146">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="5e7e5-147">**NX_HTTP_NO_FILEX**: このオプションを定義すると、FileX の依存関係のスタブが提供されます。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-147">**NX_HTTP_NO_FILEX** Defined, this option provides a stub for FileX dependencies.</span></span> <span data-ttu-id="5e7e5-148">このオプションを定義しても、HTTP クライアントは変更なしで機能します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-148">The HTTP Client will function without any change if this option is defined.</span></span> <span data-ttu-id="5e7e5-149">HTTP サーバーを適切に機能させるには、変更を行うか、ユーザーがいくつかの FileX サービスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-149">The HTTP Server will need to either be modified or the user will have to create a handful of FileX services in order to function properly.</span></span>
- <span data-ttu-id="5e7e5-150">**NX_HTTP_TYPE_OF_SERVICE**: HTTP TCP 要求に必要なサービスの種類。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-150">**NX_HTTP_TYPE_OF_SERVICE** Type of service required for the HTTP TCP requests.</span></span> <span data-ttu-id="5e7e5-151">既定では、この値は通常の IP パケット サービスを示す NX_IP_NORMAL に定義されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-151">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="5e7e5-152">**NX_HTTP_SERVER_THREAD_TIME_SLICE**: 同じ優先順位のスレッドに譲る前に、サーバー スレッドが実行を許可されるタイマー刻みの数。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-152">**NX_HTTP_SERVER_THREAD_TIME_SLICE** The number of timer ticks the Server thread is allowed to run before yielding to threads of the same priority.</span></span> <span data-ttu-id="5e7e5-153">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-153">The default value is 2.</span></span>
- <span data-ttu-id="5e7e5-154">**NX_HTTP_FRAGMENT_OPTION**: HTTP TCP 要求のフラグメントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-154">**NX_HTTP_FRAGMENT_OPTION** Fragment enable for HTTP TCP requests.</span></span> <span data-ttu-id="5e7e5-155">この値は既定では NX_DONT_FRAGMENT であり、HTTP TCP のフラグメント化が無効になります。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-155">By default, this value is NX_DONT_FRAGMENT to disable HTTP TCP fragmenting.</span></span>
- <span data-ttu-id="5e7e5-156">**NX_HTTP_SERVER_WINDOW_SIZE**: サーバー ソケットのウィンドウ サイズ。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-156">**NX_HTTP_SERVER_WINDOW_SIZE** Server socket window size.</span></span> <span data-ttu-id="5e7e5-157">既定値は 2048 バイトです。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-157">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="5e7e5-158">**NX_HTTP_TIME_TO_LIVE**: このパケットが破棄されるまでに通過できるルーターの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-158">**NX_HTTP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="5e7e5-159">既定値は 0x80 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-159">The default value is set to 0x80.</span></span>
- <span data-ttu-id="5e7e5-160">**NX_HTTP_SERVER_TIMEOUT**: 内部サービスが中断される ThreadX ティックの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-160">**NX_HTTP_SERVER_TIMEOUT** Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="5e7e5-161">既定値は 10 秒 (10 \* NX_IP_PERIODIC_RATE) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-161">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="5e7e5-162">**NX_HTTP_SERVER_TIMEOUT_ACCEPT**: 内部 *nx_tcp_server_socket_accept* 呼び出しで内部サービスが中断される ThreadX ティックの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-162">**NX_HTTP_SERVER_TIMEOUT_ACCEPT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_server_socket_accept* calls.</span></span> <span data-ttu-id="5e7e5-163">既定値は (10 \* NX_IP_PERIODIC_RATE) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-163">The default value is set to (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="5e7e5-164">**NX_HTTP_SERVER_TIMEOUT_DISCONNECT**: 内部 *nx_tcp_socket_disconnect* 呼び出しで内部サービスが中断される ThreadX ティックの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-164">**NX_HTTP_SERVER_TIMEOUT_DISCONNECT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_disconnect* calls.</span></span> <span data-ttu-id="5e7e5-165">既定値は 10 秒 (10 \* NX_IP_PERIODIC_RATE) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-165">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="5e7e5-166">**NX_HTTP_SERVER_TIMEOUT_RECEIVE**: 内部 *nx_tcp_socket_receive* 呼び出しで内部サービスが中断される ThreadX ティックの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-166">**NX_HTTP_SERVER_TIMEOUT_RECEIVE** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_receive* calls.</span></span> <span data-ttu-id="5e7e5-167">既定値は 10 秒 (10 \* NX_IP_PERIODIC_RATE) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-167">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="5e7e5-168">**NX_HTTP_SERVER_TIMEOUT_SEND**: 内部 *nx_tcp_socket_send* 呼び出しで内部サービスが中断される ThreadX ティックの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-168">**NX_HTTP_SERVER_TIMEOUT_SEND** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_send* calls.</span></span> <span data-ttu-id="5e7e5-169">既定値は 10 秒 (10 \* NX_IP_PERIODIC_RATE) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-169">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="5e7e5-170">**NX_HTTP_MAX_HEADER_FIELD**: HTTP ヘッダー フィールドの最大サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-170">**NX_HTTP_MAX_HEADER_FIELD** Specifies the maximum size of the HTTP header field.</span></span> <span data-ttu-id="5e7e5-171">既定値は 256 です。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-171">The default value is 256.</span></span>
- <span data-ttu-id="5e7e5-172">**NX_HTTP_MULTIPART_ENABLE**: 定義した場合、HTTP サーバーでマルチパート HTTP 要求をサポートできるようになります。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-172">**NX_HTTP_MULTIPART_ENABLE** If defined, enables HTTP Server to support multipart HTTP requests.</span></span>
- <span data-ttu-id="5e7e5-173">**NX_HTTP_SERVER_MAX_PENDING**: HTTP サーバーのキューに登録できる接続の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-173">**NX_HTTP_SERVER_MAX_PENDING** Specifies the number of connections that can be queued for the HTTP Server.</span></span> <span data-ttu-id="5e7e5-174">既定値は 5 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-174">The default value is set to 5.</span></span>
- <span data-ttu-id="5e7e5-175">**NX_HTTP_MAX_RESOURCE**: クライアントで指定される "*リソース名*" に許容されるバイト数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-175">**NX_HTTP_MAX_RESOURCE** Specifies the number of bytes allowed in a client supplied *resource name*.</span></span> <span data-ttu-id="5e7e5-176">既定値は 40 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-176">The default value is set to 40.</span></span>
- <span data-ttu-id="5e7e5-177">**NX_HTTP_MAX_NAME**: クライアントで指定される "*ユーザー名*" に許容されるバイト数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-177">**NX_HTTP_MAX_NAME** Specifies the number of bytes allowed in a client supplied *username*.</span></span> <span data-ttu-id="5e7e5-178">既定値は 20 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-178">The default value is set to 20.</span></span>
- <span data-ttu-id="5e7e5-179">**NX_HTTP_MAX_PASSWORD**: クライアントで指定される "*パスワード*" に許容されるバイト数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-179">**NX_HTTP_MAX_PASSWORD** Specifies the number of bytes allowed in a client supplied *password*.</span></span> <span data-ttu-id="5e7e5-180">既定値は 20 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-180">The default value is set to 20.</span></span>
- <span data-ttu-id="5e7e5-181">**NX_HTTP_SERVER_MIN_PACKET_SIZE**: サーバーの作成時に指定されたプール内のパケットの最小サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-181">**NX_HTTP_SERVER_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Server creation.</span></span> <span data-ttu-id="5e7e5-182">最小サイズは、完全な HTTP ヘッダーを 1 つのパケットに含めることができるようにするために必要です。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-182">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="5e7e5-183">既定値は 600 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-183">The default value is set to 600.</span></span>
- <span data-ttu-id="5e7e5-184">**NX_HTTP_CLIENT_MIN_PACKET_SIZE**: クライアントの作成時に指定されたプール内のパケットの最小サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-184">**NX_HTTP_CLIENT_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Client creation.</span></span> <span data-ttu-id="5e7e5-185">最小サイズは、完全な HTTP ヘッダーを 1 つのパケットに含めることができるようにするために必要です。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-185">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="5e7e5-186">既定値は 300 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-186">The default value is set to 300.</span></span>
- <span data-ttu-id="5e7e5-187">**NX_HTTP_SERVER_RETRY_SECONDS**: "*サーバー ソケットの再送信タイムアウトを秒単位で設定します。* " 既定値は 2 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-187">**NX_HTTP_SERVER_RETRY_SECONDS** *Set the Server socket retransmission timeout in seconds. The* default value is set to 2.</span></span>
- <span data-ttu-id="5e7e5-188">**NX_HTTP_SERVER_RETRY_MAX**: サーバー ソケットの最大再送信回数を設定します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-188">**NX_HTTP_SERVER_RETRY_MAX** This sets the maximum number of retransmissions on Server socket.</span></span> <span data-ttu-id="5e7e5-189">既定値は 10 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-189">The default value is set to 10.</span></span>
- <span data-ttu-id="5e7e5-190">**NX_HTTP_SERVER_RETRY_SHIFT**: この値は、次の再送信タイムアウトを設定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-190">**NX_HTTP_SERVER_RETRY_SHIFT** This value is used to set the next retransmission timeout.</span></span> <span data-ttu-id="5e7e5-191">現在のタイムアウトにこれまでの再送信回数が乗算され、ソケット タイムアウト シフトの値でシフトされます。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-191">The current timeout is multiplied by the number of retransmissions thus far, shifted by the value of the socket timeout shift.</span></span> <span data-ttu-id="5e7e5-192">既定値は 1 に設定されており、タイムアウトが 2 倍になります。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-192">The default value is set to 1 for doubling the timeout.</span></span>
- <span data-ttu-id="5e7e5-193">**NX_HTTP_SERVER_TRANSMIT_QUEUE_DEPTH**: サーバー ソケット再送信キューにエンキューできるパケットの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-193">**NX_HTTP_ SERVER_TRANSMIT_QUEUE_DEPTH** This specifies the maximum number of packets that can be enqueued on the Server socket retransmission queue.</span></span> <span data-ttu-id="5e7e5-194">エンキューされたパケットの数がこの数に達した場合、エンキューされた 1 つ以上のパケットが解放されるまで、これ以上パケットを送信することはできません。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-194">If the number of packets enqueued reaches this number, no more packets can be sent until one or more enqueued packets are released.</span></span> <span data-ttu-id="5e7e5-195">既定値は 20 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="5e7e5-195">The default value is set to 20.</span></span>