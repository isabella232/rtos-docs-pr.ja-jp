---
title: チャプター 2 - NetX Duo SMTP クライアントのインストールと使用
description: このチャプターでは、NetX Duo SMTP クライアントのインストール、セットアップ、使用に関するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 86f324935ba32aab010b81f825be0a6564983a2e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810601"
---
# <a name="chapter-2---installation-and-use-of-netx-duo-smtp-client"></a><span data-ttu-id="bb750-103">チャプター 2 - NetX Duo SMTP クライアントのインストールと使用</span><span class="sxs-lookup"><span data-stu-id="bb750-103">Chapter 2 - Installation and use of NetX Duo SMTP client</span></span>

<span data-ttu-id="bb750-104">このチャプターでは、NetX Duo SMTP クライアントのインストール、セットアップ、使用に関するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb750-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX Duo SMTP Client component.</span></span>

## <a name="netx-duo-smtp-client-installation"></a><span data-ttu-id="bb750-105">NetX Duo SMTP クライアントのインストール</span><span class="sxs-lookup"><span data-stu-id="bb750-105">NetX Duo SMTP Client Installation</span></span>

<span data-ttu-id="bb750-106">NetX Duo SMTP クライアントは [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="bb750-106">The NetX Duo SMTP Client is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="bb750-107">パッケージには次のファイルが含まれています:</span><span class="sxs-lookup"><span data-stu-id="bb750-107">The package includes the following files:</span></span>

- <span data-ttu-id="bb750-108">**nxd_smtp_client.c** NetX Duo SMTP Client API の C 言語のソース ファイル</span><span class="sxs-lookup"><span data-stu-id="bb750-108">**nxd_smtp_client.c** C Source file for NetX Duo SMTP Client API</span></span>
- <span data-ttu-id="bb750-109">**nxd_smtp_client.h** NetX Duo SMTP Client API の C 言語のヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="bb750-109">**nxd_smtp_client.h** C Header file for NetX Duo SMTP Client API</span></span>
- <span data-ttu-id="bb750-110">**demo_netxduo_smtp_client.c** NetX Duo SMTP クライアントのデモ</span><span class="sxs-lookup"><span data-stu-id="bb750-110">**demo_netxduo_smtp_client.c** Demo for NetX Duo SMTP Client</span></span>
- <span data-ttu-id="bb750-111">**nxd_smtp_client.pdf** NetX Duo SMTP Client API のユーザー ガイド</span><span class="sxs-lookup"><span data-stu-id="bb750-111">**nxd_smtp_client.pdf User Guide for** NetX Duo SMTP Client API</span></span>

<span data-ttu-id="bb750-112">NetX Duo SMTP Client API を使用するには、NetX Duo がインストールされているのと同じディレクトリに、前述の配布パッケージを丸ごとコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bb750-112">To use the NetX Duo SMTP Client API, the entire distribution mentioned previously may be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="bb750-113">たとえば、NetX Duo がディレクトリ c: *\myproject* にインストールされている場合は、*nxd_smtp_client.h および nxd_smtp_client.c* ファイルをこのディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="bb750-113">For example, if NetX Duo is installed in the directory “c:*\myproject*” then the *nxd_smtp_client.h, and nxd_smtp_client.c* files should be copied into this directory.</span></span>

## <a name="using-netx-duo-smtp-client"></a><span data-ttu-id="bb750-114">NetX Duo SMTP クライアントを使用する</span><span class="sxs-lookup"><span data-stu-id="bb750-114">Using NetX Duo SMTP Client</span></span>

<span data-ttu-id="bb750-115">NetX Duo SMTP クライアント アプリケーションを作成するには、まず ThreadX および NetX Duo のライブラリをビルドし、それをビルド プロジェクトに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb750-115">To create the NetX Duo SMTP Client application, it must first build the ThreadX and NetX Duo libraries and include them in the build project.</span></span> <span data-ttu-id="bb750-116">次に、tx *_api.h* と *nx_api.h をアプリケーションのソースコードにインクルードする必要があります*。</span><span class="sxs-lookup"><span data-stu-id="bb750-116">The application must then include tx *_api.h* and *nx_api.h in its application source code*.</span></span> <span data-ttu-id="bb750-117">これで ThreadX および NetX Duo のサービスが有効になります。</span><span class="sxs-lookup"><span data-stu-id="bb750-117">This will enable ThreadX and NetX Duo services.</span></span> <span data-ttu-id="bb750-118">SMTP クライアントのサービスを使用するには、*tx_api.h* と *nx_api.h の後で *nxd_smtp_client.c* と *nxd_smtp_client.h* もインクルードする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="bb750-118">It must also include *nxd_smtp_client.c* and *nxd_smtp_client.h* after *tx_api.h* and *nx_api.h to use SMTP Client services.*</span></span>

<span data-ttu-id="bb750-119">これらのファイルはアプリケーションの他のファイルと同じ方法でコンパイルし、そのオブジェクト コードをアプリケーションのファイルと共にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb750-119">These files must be compiled in the same manner as other application files and the object code must be linked along with the files of the application.</span></span> <span data-ttu-id="bb750-120">NetX Duo SMTP クライアント アプリケーションの作成に必要なものはこれですべてです。</span><span class="sxs-lookup"><span data-stu-id="bb750-120">This is all that is required to create a NetX Duo SMTP Client application.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="bb750-121">簡単なシステムの例</span><span class="sxs-lookup"><span data-stu-id="bb750-121">Small Example System</span></span>

<span data-ttu-id="bb750-122">NetX Duo SMTP クライアントの使用例を下の図 1 に示します。</span><span class="sxs-lookup"><span data-stu-id="bb750-122">An example of using the NetX Duo SMTP Client is described in Figure 1 that appears below.</span></span> <span data-ttu-id="bb750-123">68 行目で nx_packet_pool_create サービスを使用して IP インスタンスのパケット プールを作成します。パケットのペイロードはとても小さいです。</span><span class="sxs-lookup"><span data-stu-id="bb750-123">The packet pool for the IP instance is created using the nx_packet_pool_create service, on line 68 and has a very small packet payload.</span></span> <span data-ttu-id="bb750-124">これは、この IP インスタンスから送信するのが、大きなペイロードを必要としない制御パケットだけだからです。</span><span class="sxs-lookup"><span data-stu-id="bb750-124">This is because the IP instance only sends control packets which don’t require much payload.</span></span> <span data-ttu-id="bb750-125">84 行目で 作成する SMTP クライアントのパケット プールは、SMTP クライアントのメッセージをサーバーとメッセージ データに送信するのに使用します。</span><span class="sxs-lookup"><span data-stu-id="bb750-125">The SMTP Client packet pool created on line 84 and is used for transmitting SMTP Client messages to the server and message data.</span></span> <span data-ttu-id="bb750-126">パケットのペイロード サイズは IP インスタンスの場合よりずっと大きいです。</span><span class="sxs-lookup"><span data-stu-id="bb750-126">Its packet payload is much larger.</span></span> <span data-ttu-id="bb750-127">118 行目で同じパケット プールを使用して IP インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="bb750-127">The IP instance is created in line 118 using the same packet pool.</span></span> <span data-ttu-id="bb750-128">130 行目では、この IP インスタンスで TCP を有効にします。TCP は SMTP プロトコルのために必要です。</span><span class="sxs-lookup"><span data-stu-id="bb750-128">TCP, required for the SMTP protocol, is enabled on the IP instance in line 130.</span></span>

<span data-ttu-id="bb750-129">アプリケーションのスレッドでは、170 行目で *nxd_smtp_client_create* サービスを使用して SMTP クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="bb750-129">In the application thread, the SMTP Client is created using the *nxd_smtp_client_create* service, in line 170.</span></span> <span data-ttu-id="bb750-130">*nxd_smtp_client_create* サービスは、IPv4 と IPv6 両方で SMTP サーバーの接続をサポートしていますが、この例では IPv4 に限定しています。</span><span class="sxs-lookup"><span data-stu-id="bb750-130">The *nxd_smtp_client_create* service supports both IPv4 and IPv6 SMTP server connections although this example is limited to IPv4.</span></span> <span data-ttu-id="bb750-131">次に 184 行目で *nx_smtp_mail_send* サービスを使用して、送信するメール メッセージを SMTP クライアントに渡します。</span><span class="sxs-lookup"><span data-stu-id="bb750-131">Then the mail message is submitted to the SMTP Client for transmission on line 184 using the *nx_smtp_mail_send* service.</span></span> <span data-ttu-id="bb750-132">件名とメール内容のヘッダーは、メッセージ本文とは別に作成されます。</span><span class="sxs-lookup"><span data-stu-id="bb750-132">Note that the subject line with the mail content header is created separately from the message body.</span></span> <span data-ttu-id="bb750-133">また、メール送信要求では、構文が正しいと考えられる宛先メール アドレスを 1 つだけ指定できます。</span><span class="sxs-lookup"><span data-stu-id="bb750-133">Also note that the send mail request accepts only one recipient mail address which is assumed to be syntactically correct.</span></span>

<span data-ttu-id="bb750-134">それから 200 行目で、アプリケーションにより SMTP クライアントを終了します。</span><span class="sxs-lookup"><span data-stu-id="bb750-134">Then the application terminates the SMTP Client on line 200.</span></span> <span data-ttu-id="bb750-135">*nx_smtp_client_delete* サービスでは、ソケット接続が閉じられポートがバインド解除されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bb750-135">The *nx_smtp_client_delete* service checks that the socket connection is closed and the port is unbound.</span></span> <span data-ttu-id="bb750-136">それ以上使用しないパケット プールを削除するかどうかは SMTP クライアント アプリケーションに任されています。</span><span class="sxs-lookup"><span data-stu-id="bb750-136">Note that it is up to the SMTP Client application to delete the packet pool if it no longer has use for it.</span></span>

```c
/*
   demo_netxduo_smtp_client.c

   This is a small demo of the NetX Duo SMTP Client on the high-performance NetX
   Duo TCP/IP stack.  This demo relies on Thread, NetX Duo and SMTP Client API to
   perform simple SMTP mail transfers in an SMTP client application to an SMTP mail
   server.   */

#include "nx_api.h"
#include "nx_ip.h"
#include "nxd_smtp_client.h"


/* Define the host user name and mail box parameters */
#define USERNAME               "myusername"
#define PASSWORD               "mypassword"
#define FROM_ADDRESS           "my@mycompany.com"
#define RECIPIENT_ADDRESS      "your@yourcompany.com"
#define LOCAL_DOMAIN           "mycompany.com"

#define SUBJECT_LINE           "NetX Duo SMTP Client Demo"
#define MAIL_BODY              "NetX Duo SMTP client is an SMTP client \r\n" \
                               “implementation for embedded devices to send  \r\n" \
                               "email to SMTP servers. This feature is \r\n" \
                               "intended to allow a device to send simple \r\n " \
                               "status reports using the most universal \r\n " \
                               “Internet application, email.\r\n"

/* See the NetX Duo SMTP Client User Guide for how to set the authentication type.
   The most common authentication type is PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE 3


#define CLIENT_IP_ADDRESS  IP_ADDRESS(1,2,3,5)
#define SERVER_IP_ADDRESS  IP_ADDRESS(1,2,3,4)
#define SERVER_PORT        25


/* Define the NetX Duo and ThreadX structures for the SMTP client appliciation. */
NX_PACKET_POOL                  ip_packet_pool;
NX_PACKET_POOL                  client_packet_pool;
NX_IP                           client_ip;
TX_THREAD                       demo_client_thread;
static NX_SMTP_CLIENT           demo_client;


void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
void    demo_client_thread_entry(ULONG info);

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
    CHAR    *free_memory_pointer;


    /* Setup the pointer to unallocated memory.  */
    free_memory_pointer =  (CHAR *) first_unused_memory;

    /* Create IP default packet pool. */
    status =  nx_packet_pool_create(&ip_packet_pool, "Default IP Packet Pool",
                                    128, free_memory_pointer, 2048);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* Create SMTP Client packet pool. This is only for transmitting packets to the
       server. It need not be a separate packet pool than the IP default packet pool
       but for more efficient resource use, we use two different packet pools
       because the CLient SMTP messages generally require more payload than IP
       control packets.

       Packet payload depends on the SMTP Client application requirements.  Size of
       packet payload must include IP and TCP headers. For IPv6 connections, IP and
       TCP header data is 60 bytes. For IPv4 IP and TCP header data is 40 bytes (not
       including TCP options). */
    status |=  nx_packet_pool_create(&client_packet_pool, "SMTP Client Packet Pool",
                                     800, free_memory_pointer, (10*800));

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + (10*800);

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create the client thread */
    status = tx_thread_create(&demo_client_thread, "client_thread",
                              demo_client_thread_entry, 0, free_memory_pointer,
                              2048, 16, 16,
                              TX_NO_TIME_SLICE, TX_DONT_START);

    if (status != NX_SUCCESS)
    {

        printf("Error creating Client thread. Status 0x%x\r\n", status);
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer =  free_memory_pointer + 4096;


    /* Create Client IP instance. Remember to replace the generic driver
       with a real ethernet driver to actually run this demo! */

    status = nx_ip_create(&client_ip, "SMTP Client IP Instance", CLIENT_IP_ADDRESS,
                          0xFFFFFF00UL, &ip_packet_pool, _nx_ram_network_driver,
                          free_memory_pointer, 2048, 1);


    free_memory_pointer =  free_memory_pointer + 2048;

    /* Enable ARP and supply ARP cache memory. */
    status =  nx_arp_enable(&client_ip, (void **) free_memory_pointer, 1040);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 1040;

    /* Enable TCP for client. */
    status =  nx_tcp_enable(&client_ip);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable ICMP for client. */
    status =  nx_icmp_enable(&client_ip);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Start the client thread. */
    tx_thread_resume(&demo_client_thread);

    return;
}


/* Define the smtp application thread task.   */
void    demo_client_thread_entry(ULONG info)
{

    UINT        status;
    UINT        error_counter = 0;
    NXD_ADDRESS server_ip_address;


    tx_thread_sleep(100);

    /* Set up the server IP address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;

    /* The demo client username and password is the authentication
       data used when the server attempts to authentication the client. */

    status =  nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
                                     USERNAME,
                                     PASSWORD,
                                     FROM_ADDRESS,
                                     LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
                                     &server_ip_address, SERVER_PORT);

    if (status != NX_SUCCESS)
    {
        printf("Error creating the client. Status: 0x%x.\n\r", status);
        return;
    }

    /* Create a mail instance with the above text message and recipient info. */
    status =  nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
                                TP_MAIL_PRIORITY_NORMAL,
                                SUBJECT_LINE, MAIL_BODY, sizeof(MAIL_BODY) - 1);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        /* Mail item was not sent. Note that we need not delete the client. The
           error status may be a failed authentication check or a broken connection.
           We can simply call nx_smtp_mail_send again.  */
        error_counter++;
    }

    /* Release resources used by client. Note that the transmit packet
       pool must be deleted by the application if it no longer has use for it.*/
    status = nx_smtp_client_delete(&demo_client);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    return;
}
```

<span data-ttu-id="bb750-137">**図 1. NetX Duo での SMTP クライアントの使用例**</span><span class="sxs-lookup"><span data-stu-id="bb750-137">**Figure 1. Example of SMTP Client use with NetX Duo**</span></span>

## <a name="client-configuration-options"></a><span data-ttu-id="bb750-138">クライアントの構成オプション</span><span class="sxs-lookup"><span data-stu-id="bb750-138">Client Configuration Options</span></span>

<span data-ttu-id="bb750-139">NetX Duo SMTP Client API にはいくつかの構成オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="bb750-139">There are several configuration options with the NetX Duo SMTP Client API.</span></span> <span data-ttu-id="bb750-140">次のリストで、すべてのオプションを詳述します:</span><span class="sxs-lookup"><span data-stu-id="bb750-140">Following is a list of all options described in detail:</span></span>

- <span data-ttu-id="bb750-141">**NX_SMTP_CLIENT_TCP_WINDOW_SIZE** このオプションでは、クライアントの TCP 受信ウィンドウのサイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="bb750-141">**NX_SMTP_CLIENT_TCP_WINDOW_SIZE** This option sets the size of the Client TCP receive window.</span></span> <span data-ttu-id="bb750-142">これは、処理を実行するイーサネット ハードウェアの MTU より小さくし、IP ヘッダーと TCP ヘッダー用の領域を確保する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb750-142">This should be set to below the MTU size of the underlying Ethernet hardware and allow room for IP and TCP headers.</span></span> <span data-ttu-id="bb750-143">NetX Duo SMTP クライアントの既定の TCP ウィンドウ サイズは 1460 です。</span><span class="sxs-lookup"><span data-stu-id="bb750-143">The default NetX Duo SMTP Client TCP window size is 1460.</span></span>
- <span data-ttu-id="bb750-144">**NX_SMTP_CLIENT_PACKET_TIMEOUT** このオプションでは、NetX のパケットの割り当てのタイムアウト時間を設定します。</span><span class="sxs-lookup"><span data-stu-id="bb750-144">**NX_SMTP_CLIENT_PACKET_TIMEOUT** This option sets the timeout on NetX packet allocation.</span></span> <span data-ttu-id="bb750-145">NetX Duo SMTP クライアントのパケットの既定のタイムアウト時間は 2 秒です。</span><span class="sxs-lookup"><span data-stu-id="bb750-145">The default NetX Duo SMTP Client packet timeout is 2 seconds.</span></span>
- <span data-ttu-id="bb750-146">**NX_SMTP_CLIENT_CONNECTION_TIMEOUT** このオプションでは、クライアントの TCP ソケット接続のタイムアウト時間を設定します。</span><span class="sxs-lookup"><span data-stu-id="bb750-146">**NX_SMTP_CLIENT_CONNECTION_TIMEOUT** This option sets the Client TCP socket connect timeout.</span></span> <span data-ttu-id="bb750-147">NetX Duo SMTP クライアントの接続の既定のタイムアウト時間は 10 秒です。</span><span class="sxs-lookup"><span data-stu-id="bb750-147">The default NetX Duo SMTP Client connect timeout is 10 seconds.</span></span>
- <span data-ttu-id="bb750-148">**NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** このオプションでは、クライアントの TCP ソケットの切断タイムアウト時間を設定します。</span><span class="sxs-lookup"><span data-stu-id="bb750-148">**NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** This option sets the Client TCP socket disconnect timeout.</span></span> <span data-ttu-id="bb750-149">NetX Duo SMTP クライアントの既定の切断タイムアウト時間は 5 秒 \* です。</span><span class="sxs-lookup"><span data-stu-id="bb750-149">The default NetX Duo SMTP Client disconnect timeout is 5 seconds\*.</span></span> <span data-ttu-id="bb750-150">SMTP クライアントで接続の切断などの内部エラーが発生すると、直ちにタイムアウトして接続を終了する場合があります。</span><span class="sxs-lookup"><span data-stu-id="bb750-150">Note that if the SMTP Client encounters an internal error such as a broken connection it may terminate the connection with a zero wait timeout.</span></span>
- <span data-ttu-id="bb750-151">**NX_SMTP_GREETING_TIMEOUT** このオプションでは、グリーティング メッセージに対するサーバーの応答をクライアントで受信するのを待つ際のタイムアウト時間を設定します。</span><span class="sxs-lookup"><span data-stu-id="bb750-151">**NX_SMTP_GREETING_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to its greeting.</span></span> <span data-ttu-id="bb750-152">NetX Duo SMTP クライアントの既定値は 10 秒です。</span><span class="sxs-lookup"><span data-stu-id="bb750-152">The default NetX Duo SMTP Client value is 10 seconds.</span></span>
- <span data-ttu-id="bb750-153">**NX_SMTP_ENVELOPE_TIMEOUT** このオプションでは、クライアント コマンドに対するサーバーの応答をクライアントで受信するのを待つ際のタイムアウト時間を設定します。</span><span class="sxs-lookup"><span data-stu-id="bb750-153">**NX_SMTP_ENVELOPE_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to a Client command.</span></span> <span data-ttu-id="bb750-154">NetX Duo SMTP クライアントの既定値は 10 秒です。</span><span class="sxs-lookup"><span data-stu-id="bb750-154">The default NetX Duo SMTP Client value is 10 seconds.</span></span>
- <span data-ttu-id="bb750-155">**NX_SMTP_MESSAGE_TIMEOUT** このオプションでは、受信したメール メッセージ データに対するサーバーの応答をクライアントで受信するのを待つ際のタイムアウト時間を設定します。</span><span class="sxs-lookup"><span data-stu-id="bb750-155">**NX_SMTP_MESSAGE_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to receiving the mail message data.</span></span> <span data-ttu-id="bb750-156">NetX Duo SMTP クライアントの既定値は 30 秒です。</span><span class="sxs-lookup"><span data-stu-id="bb750-156">The default NetX Duo SMTP Client value is 30 seconds.</span></span>
- <span data-ttu-id="bb750-157">**NX_SMTP_CLIENT_SEND_TIMEOUT** このオプションでは、サーバーに対して SMTP 認証を行うときにユーザー パスワードを保存するバッファーの待機オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="bb750-157">**NX_SMTP_CLIENT_SEND_TIMEOUT** This option defines the wait option of the buffer to store the user password during SMTP authentication with the Server.</span></span> <span data-ttu-id="bb750-158">既定値は 20 バイトです。</span><span class="sxs-lookup"><span data-stu-id="bb750-158">The default value is 20 bytes.</span></span>
- <span data-ttu-id="bb750-159">**NX_SMTP_SERVER_CHALLENGE_MAX_STRING** このオプションでは、SMTP 認証時にサーバーのチャレンジを抽出するバッファーのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="bb750-159">**NX_SMTP_SERVER_CHALLENGE_MAX_STRING** This option defines the size of the buffer for extracting the Server challenge during SMTP authentication.</span></span> <span data-ttu-id="bb750-160">既定値は 200 バイトです。</span><span class="sxs-lookup"><span data-stu-id="bb750-160">The default value is 200 bytes.</span></span> <span data-ttu-id="bb750-161">LOGIN 認証と PLAIN 認証では、SMTP クライントで使用するバッファーは恐らくこれより小さくても済みます。</span><span class="sxs-lookup"><span data-stu-id="bb750-161">For LOGIN and PLAIN authentication, the SMTP Client can probably use a smaller buffer.</span></span>
- <span data-ttu-id="bb750-162">**NX_SMTP_CLIENT_MAX_PASSWORD** このオプションでは、サーバーに対して SMTP 認証を行うときにユーザー パスワードを保存するバッファーのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="bb750-162">**NX_SMTP_CLIENT_MAX_PASSWORD** This option defines the size of the buffer to store the user password during SMTP authentication with the Server.</span></span> <span data-ttu-id="bb750-163">既定値は 20 バイトです。</span><span class="sxs-lookup"><span data-stu-id="bb750-163">The default value is 20 bytes.</span></span> 
- <span data-ttu-id="bb750-164">**NX_SMTP_CLIENT_MAX_USERNAME** このオプションでは、サーバーに対して SMTP 認証を行うときにホストのユーザー名を保存するバッファーのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="bb750-164">**NX_SMTP_CLIENT_MAX_USERNAME** This option defines the size of the buffer to store the host username during SMTP authentication with the Server.</span></span> <span data-ttu-id="bb750-165">既定値は 40 バイトです。</span><span class="sxs-lookup"><span data-stu-id="bb750-165">The default value is 40 bytes.</span></span> 
