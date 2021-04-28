---
title: 第 2 章 - Azure RTOS NetX POP3 クライアントのインストールと使用
description: NetX POP3 クライアントには、1 つのソース ファイル、1 つのヘッダー ファイル、および 1 つのデモ ファイルが含まれています。 MD5 ダイジェスト サービス用の 2 つの追加ファイルがあります。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24de396c69d458866f9423fd995bcb8d905f29c8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811480"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pop3-client"></a><span data-ttu-id="d997f-104">第 2 章 - Azure RTOS NetX POP3 クライアントのインストールと使用</span><span class="sxs-lookup"><span data-stu-id="d997f-104">Chapter 2 - Installation and use of Azure RTOS NetX POP3 Client</span></span>

<span data-ttu-id="d997f-105">NetX POP3 クライアントには、1 つのソース ファイル、1 つのヘッダー ファイル、および 1 つのデモ ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d997f-105">NetX POP3 Client includes one source file, one header file, and a demo file.</span></span> <span data-ttu-id="d997f-106">MD5 ダイジェスト サービス用の 2 つの追加ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="d997f-106">There are two additional files for MD5 digest services.</span></span> <span data-ttu-id="d997f-107">また、ユーザー ガイド PDF ファイル (このドキュメント) もあります。</span><span class="sxs-lookup"><span data-stu-id="d997f-107">There is also a User Guide PDF file (this document).</span></span>

- <span data-ttu-id="d997f-108">**nx_pop3_client.c**: NetX POP3 クライアント API 用の C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="d997f-108">**nx_pop3_client.c**: C Source file for NetX POP3 Client API</span></span>
- <span data-ttu-id="d997f-109">**nx_pop3_client.h**: NetX POP3 クライアント API 用の C ヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="d997f-109">**nx_pop3_client.h**: C Header file for NetX POP3 Client API</span></span>
- <span data-ttu-id="d997f-110">**demo_netxduo_pop3_client.c**: POP3 クライアントの作成とセッション開始のデモ ファイル</span><span class="sxs-lookup"><span data-stu-id="d997f-110">**demo_netxduo_pop3_client.c**: Demo file for POP3 Client creation and session initiation</span></span>
- <span data-ttu-id="d997f-111">**nx_md5.c**: MD5 ダイジェスト サービスを定義する C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="d997f-111">**nx_md5.c**: C Source file defining MD5 digest services</span></span>
- <span data-ttu-id="d997f-112">**nx_md5.h**: MD5 ダイジェスト サービスを定義する C ヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="d997f-112">**nx_md5.h**: C Header file defining MD5 digest services</span></span>
- <span data-ttu-id="d997f-113">**nx_pop3_client.pdf** NetX POP3 クライアントのユーザー ガイド</span><span class="sxs-lookup"><span data-stu-id="d997f-113">**nx_pop3_client.pdf**: NetX POP3 Client User Guide</span></span>

<span data-ttu-id="d997f-114">NetX POP3 クライアントを使用する場合は、NetX がインストールされているのと同じディレクトリに前述のディストリビューション全体をコピーします。</span><span class="sxs-lookup"><span data-stu-id="d997f-114">To use NetX POP3 Client, the entire distribution mentioned previously can be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="d997f-115">たとえば、NetX が " *\threadx\mcf5272\green*" ディレクトリにインストールされている場合は、*nx_md5.h*、*nx_md5.c*、*nx_pop3_client.h、nx_pop3_client.c* の各ファイルをこのディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d997f-115">For example, if NetX is installed in the directory "*\threadx\mcf5272\green*" then the *nx_md5.h*, *nx_md5.c,* *nx_pop3_client.h, and nx_pop3_client.c* files should be copied into this directory.</span></span>

## <a name="using-netx-pop3-client"></a><span data-ttu-id="d997f-116">NetX POP3 クライアントの使用</span><span class="sxs-lookup"><span data-stu-id="d997f-116">Using NetX POP3 Client</span></span>

<span data-ttu-id="d997f-117">NetX POP3 クライアント サービスを使用するには、そのビルド プロジェクトに *nx_pop3_client.c* を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d997f-117">To use the NetX POP3 Client service, the application must add *nx_pop3_client.c* to its build project.</span></span> <span data-ttu-id="d997f-118">ThreadX と NetX を使用するために、アプリケーション コードに *tx_api.h* と *nx_api.h* を、その後に *nx_md5.h、nx_pop3.h、nx_pop3_client.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d997f-118">The application code must include *nx_md5.h, nx_pop3.h and nx_pop3_client.h* after *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span>

<span data-ttu-id="d997f-119">これらのファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、オブジェクト コードをアプリケーションのファイルと一緒にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d997f-119">These files must be compiled in the same manner as other application files and the object code must be linked along with the files of the application.</span></span> <span data-ttu-id="d997f-120">これが NetX POP3 クライアントを使用するために必要なすべてです。</span><span class="sxs-lookup"><span data-stu-id="d997f-120">This is all that is required to use the NetX POP3 Client.</span></span>

## <a name="small-example-of-the-netx-pop3-client"></a><span data-ttu-id="d997f-121">NetX POP3 クライアントの小規模な例</span><span class="sxs-lookup"><span data-stu-id="d997f-121">Small Example of the NetX POP3 Client</span></span>

<span data-ttu-id="d997f-122">NetX POP3 クライアント サービスの使用方法の例を下の図 1 に示します。</span><span class="sxs-lookup"><span data-stu-id="d997f-122">An example of how to use NetX POP3 Client services is described in Figure 1 that appears below.</span></span> <span data-ttu-id="d997f-123">このデモでは、37 と 38 行目でメールのダウンロードとセッションの完了を通知する 2 つのコールバックが設定されます。</span><span class="sxs-lookup"><span data-stu-id="d997f-123">This demo sets up the two callbacks for notification of mail download and session completion on lines 37 and 38.</span></span> <span data-ttu-id="d997f-124">76 行目で POP3 クライアントのパケット プールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d997f-124">The POP3 Client packet pool is created on line 76.</span></span> <span data-ttu-id="d997f-125">88 行目で IP スレッド タスクが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d997f-125">The IP thread task is created on line 88.</span></span> <span data-ttu-id="d997f-126">このパケット プールも POP3 クライアントのパケット プールに使用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d997f-126">Note that this packet pool is also used for the POP3 Client packet pool.</span></span> <span data-ttu-id="d997f-127">107 行目で IP タスクに対して TCP が有効になります。</span><span class="sxs-lookup"><span data-stu-id="d997f-127">TCP is enabled on the IP task in line 107.</span></span>

<span data-ttu-id="d997f-128">133 行目の、アプリケーション スレッド エントリ関数 *demo_thread_entry* 内で POP3 クライアントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d997f-128">The POP3 Client is created on line 133 inside the application thread entry function, *demo_thread_entry*.</span></span> <span data-ttu-id="d997f-129">これは、*nx_pop3_client_create* サービスも POP3 サーバーとの TCP 接続を試行するためです。</span><span class="sxs-lookup"><span data-stu-id="d997f-129">This is because the *nx_pop3_client_create* service also attempts to make a TCP connection with the POP3 server.</span></span> <span data-ttu-id="d997f-130">成功した場合、アプリケーションは 149 行目で *nx_pop3_client_mail_items_get* サービスを使用して、そのメールドロップ内のアイテムの数を POP3 サーバーに照会します。</span><span class="sxs-lookup"><span data-stu-id="d997f-130">If successful, the application queries the POP3 server for the number of items in its maildrop on line 149 using the *nx_pop3_client_mail_items_get* service.</span></span>

<span data-ttu-id="d997f-131">アイテムが 1 つ以上ある場合、アプリケーションは while ループを反復処理して各メール アイテムのメール メッセージをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="d997f-131">If there are one or more items, the application iterates through the while loop for each mail item to download the mail message.</span></span> <span data-ttu-id="d997f-132">149 行目の *nx_pop3_client_mail_item_get* 呼び出しで RETR 要求が行われます。</span><span class="sxs-lookup"><span data-stu-id="d997f-132">The RETR request is made on line 149 in the *nx_pop3_client_mail_item_get* call.</span></span> <span data-ttu-id="d997f-133">成功した場合、アプリケーションは 196 行目でメッセージの最後のパケットを受信したことを検出するまで、177 行目で *nx_pop3_client_mail_item_message_get* サービスを使用して、パケットをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="d997f-133">If successful, the application downloads packets using the *nx_pop3_client_mail_item_message_get* service on line 177 till it detects the last packet in the message has been received on line 196.</span></span> <span data-ttu-id="d997f-134">最後に、アプリケーションは 199 行目の *nx_pop3_client_mail_item_delete* 呼び出しで、ダウンロードが正常に実行されたと見なして、メール アイテムを削除します。</span><span class="sxs-lookup"><span data-stu-id="d997f-134">Lastly, the application deletes the mail item, assuming a successful download has occurred on line 199 in *the nx_pop3_client_mail_item_delete* call.</span></span> <span data-ttu-id="d997f-135">RFC 1939 では、クライアントのメールドロップにメールが蓄積されないように、ダウンロードしたメール アイテムを削除するよう POP3 クライアントからサーバーに指示することを推奨しています。</span><span class="sxs-lookup"><span data-stu-id="d997f-135">The RFC 1939 recommends that POP3 Clients instruct the Server to delete downloaded mail items to prevent mail accumulating in the Client's maildrop.</span></span> <span data-ttu-id="d997f-136">ただし、サーバーが自動的にそうする場合があります。</span><span class="sxs-lookup"><span data-stu-id="d997f-136">The Server may automatically do so anyway.</span></span>

<span data-ttu-id="d997f-137">すべてのメール アイテムがダウンロードされた場合、または POP3 クライアントのサービス呼び出しが失敗した場合、アプリケーションはループを終了し、217 行目で *nx_pop3_client_delete* サービスを使用して、POP3 クライアントを削除します。</span><span class="sxs-lookup"><span data-stu-id="d997f-137">Once all the mail items are downloaded, or if a POP3 Client service call fails, the application exits of the loop and deletes the POP3 Client on line 217 using the *nx_pop3_client_delete* service.</span></span>

```c
/*
    demo_netxduo_pop3.c

    This is a small demo of POP3 Client on the NetX TCP/IP stack.
    This demo relies on Thread, NetX and POP3 Client API to conduct
    a POP3 mail session.
*/

#include "tx_api.h"
#include "nx_api.h"
#include "nx_pop3_client.h"

#define DEMO_STACK_SIZE        4096
#define CLIENT_ADDRESS         IP_ADDRESS(192,2,2,61)
#define SERVER_ADDRESS         IP_ADDRESS(192,2,2,89)
#define SERVER_PORT            110

/* Replace the 'ram' driver with your own Ethernet driver. */
void _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Set up the POP3 Client. */

TX_THREAD          demo_client_thread;
NX_POP3_CLIENT     demo_client;
NX_PACKET_POOL     client_packet_pool;
NX_IP              client_ip;

#define PAYLOAD_SIZE 500

/* Set up Client thread entry point. */
void     demo_thread_entry(ULONG info);

/* Shared secret is the same as password. */

#define LOCALHOST              "recipient@domain.com"
#define LOCALHOST_PASSWORD     "testpwd"

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{

UINT      status;
UCHAR     *free_memory_pointer;

    /* Setup the working pointer. */
    free_memory_pointer = first_unused_memory;

    /* Create a client thread. */
    tx_thread_create(&demo_client_thread, "Client", demo_thread_entry, 0,
                    free_memory_pointer, DEMO_STACK_SIZE, 1, 1,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    free_memory_pointer = free_memory_pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* The demo client username and password is the authentication
    data used when the server attempts to authentication the client. */

    /* Create Client packet pool. */
    status = nx_packet_pool_create(&client_packet_pool,"POP3 Client Packet Pool",
                        PAYLOAD_SIZE, free_memory_pointer, (PAYLOAD_SIZE * 10));
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + (PAYLOAD_SIZE * 10);

    /* Create IP instance for demo Client */
    status = nx_ip_create(&client_ip, "POP3 Client IP Instance",
                            CLIENT_ADDRESS, 0xFFFFFF00UL, &client_packet_pool,
                            _nx_ram_network_driver, free_memory_pointer,
                            2048, 1);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* Enable ARP and supply ARP cache memory. */
    nx_arp_enable(&client_ip, (void **) free_memory_pointer, 1024);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 1024;

    /* Enable TCP and ICMP for Client IP. */
    nx_tcp_enable(&client_ip);
    nx_icmp_enable(&client_ip);

    return;
}

/* Define the application thread entry function. */

void demo_thread_entry(ULONG info)
{

UINT          status;
UINT          mail_item, number_mail_items;
UINT          bytes_downloaded = 0;
UINT          final_packet = NX_FALSE;
ULONG         total_size, mail_item_size, bytes_retrieved;
NX_PACKET     *packet_ptr;

    /* Let the IP instance get initialized with driver parameters. */
    tx_thread_sleep(40);

    /* Create a NetX POP3 Client instance with no byte or block memory pools.
    Note that it uses its password for its APOP shared secret. */
    status = nx_pop3_client_create(&demo_client,
                        NX_TRUE,
                        &client_ip, &client_packet_pool, SERVER_ADDRESS,
                        SERVER_PORT, LOCALHOST, LOCALHOST_PASSWORD);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        status = nx_pop3_client_delete(&demo_client);

        /* Abort. */
        return;
    }

    /* Find out how many items are in our mailbox. */
    status = nx_pop3_client_mail_items_get(&demo_client, &number_mail_items, &total_size);

    printf("Got %d mail items, total size%d \n", number_mail_items, total_size);

    /* If nothing in the mailbox, disconnect. */
    if (number_mail_items == 0)
    {
        nx_pop3_client_delete(&demo_client);

        return;
    }

    /* Download all mail items. */
    mail_item = 1;

    while (mail_item <= number_mail_items)
    {

        /* This submits a RETR request and gets the mail message size. */
        status = nx_pop3_client_mail_item_get(&demo_client, mail_item, &mail_item_size);

        /* Loop to get all mail message packets until the mail item is completely downloaded. */

        while((final_packet == NX_FALSE) && (status == NX_SUCCESS))
        {
            status = nx_pop3_client_mail_item_message_get(&demo_client, &packet_ptr,
                                                        &bytes_retrieved,
                                                        &final_packet);

            if (status != NX_SUCCESS)
            {
                break;
            }

            if (bytes_retrieved != 0)
            {

            printf("Received %d bytes of data for item %d: %s\n",
                    packet_ptr -> nx_packet_length,
                    mail_item, packet_ptr -> nx_packet_prepend_ptr);
            }

            nx_packet_release(packet_ptr);

            /* Determine if this is the last data packet. */
            if (final_packet)
            {
                /* It is. Let the server know it can delete this mail item. */
                status = nx_pop3_client_mail_item_delete(&demo_client, mail_item);
            }

            /* Keep track of how much mail message data is left. */
            bytes_downloaded += bytes_retrieved;
        }

        /* Get the next mail item. */
        mail_item++;

        tx_thread_sleep(100);
    }

    /* Disconnect from the POP3 server. */
    status = nx_pop3_client_quit(&demo_client);

    /* Delete the POP3 Client. This will not delete the Client packet pool. */
    status = nx_pop3_client_delete(&demo_client);

}
```

<span data-ttu-id="d997f-138">図 1.</span><span class="sxs-lookup"><span data-stu-id="d997f-138">Figure 1.</span></span> <span data-ttu-id="d997f-139">NetX POP3 クライアント アプリケーションの例</span><span class="sxs-lookup"><span data-stu-id="d997f-139">Example of a NetX POP3 Client application</span></span>

## <a name="pop3-client-configuration-options"></a><span data-ttu-id="d997f-140">POP3 クライアントの構成オプション</span><span class="sxs-lookup"><span data-stu-id="d997f-140">POP3 Client Configuration Options</span></span>

<span data-ttu-id="d997f-141">NetX POP3 クライアントには、いくつかの構成オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="d997f-141">There are several configuration options with the NetX POP3 Client.</span></span> <span data-ttu-id="d997f-142">以下はすべてのオプションの一覧で、詳細に説明されています。</span><span class="sxs-lookup"><span data-stu-id="d997f-142">Following is a list of all options described in detail:</span></span>

- <span data-ttu-id="d997f-143">**NX_POP3_CLIENT_PACKET_TIMEOUT**: これは、POP3 クライアントがパケットを割り当てる際の待機オプションを秒単位で定義します。</span><span class="sxs-lookup"><span data-stu-id="d997f-143">**NX_POP3_CLIENT_PACKET_TIMEOUT**: This defines the wait option in seconds for the POP3 Client to allocate a packet.</span></span> <span data-ttu-id="d997f-144">既定値は 1 秒です。</span><span class="sxs-lookup"><span data-stu-id="d997f-144">The default value is 1 second.</span></span>

- <span data-ttu-id="d997f-145">**NX_POP3_CLIENT_CONNECTION_TIMEOUT**: これは、POP3 クライアントが POP3 サーバーと接続する際の待機オプションを秒単位で定義します。</span><span class="sxs-lookup"><span data-stu-id="d997f-145">**NX_POP3_CLIENT_CONNECTION_TIMEOUT**: This defines the wait option in seconds for the POP3 Client to connect with the POP3 Server.</span></span> <span data-ttu-id="d997f-146">既定値は 30 秒です。</span><span class="sxs-lookup"><span data-stu-id="d997f-146">The default value is 30 seconds.</span></span>

- <span data-ttu-id="d997f-147">**NX_POP3_CLIENT_DISCONNECT_TIMEOUT**: これは、POP3 クライアントが POP3 サーバーから切断する際の待機オプションを秒単位で定義します。</span><span class="sxs-lookup"><span data-stu-id="d997f-147">**NX_POP3_CLIENT_DISCONNECT_TIMEOUT**: This defines the wait option in seconds for the POP3 Client to disconnect from the POP3 Server.</span></span> <span data-ttu-id="d997f-148">既定値は 2 秒です。</span><span class="sxs-lookup"><span data-stu-id="d997f-148">The default value is 2 seconds.</span></span>

- <span data-ttu-id="d997f-149">**NX_POP3_TCP_SOCKET_SEND_WAIT**: このオプションでは、*nx_tcp_socket_send* サービスの呼び出しの待機オプションを秒単位で設定します。</span><span class="sxs-lookup"><span data-stu-id="d997f-149">**NX_POP3_TCP_SOCKET_SEND_WAIT**: This option sets the wait option in seconds in *nx_tcp_socket_send* service calls.</span></span> <span data-ttu-id="d997f-150">既定値は 2 秒です。</span><span class="sxs-lookup"><span data-stu-id="d997f-150">The default value is 2 seconds.</span></span>

- <span data-ttu-id="d997f-151">**NX_POP3_SERVER_REPLY_TIMEOUT**: このオプションでは、*nx_tcp_socket_receive* サービスの呼び出しにおけるクライアント要求に対するサーバー応答の待機オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="d997f-151">**NX_POP3_SERVER_REPLY_TIMEOUT**: This option sets the wait option in *nx_tcp_socket_receive* service calls for the Server reply to a Client request.</span></span> <span data-ttu-id="d997f-152">既定値は 10 秒です。</span><span class="sxs-lookup"><span data-stu-id="d997f-152">The default value is 10 seconds.</span></span>

- <span data-ttu-id="d997f-153">**NX_POP3_CLIENT_TCP_WINDOW_SIZE**: このオプションでは、クライアントの TCP 受信ウィンドウのサイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="d997f-153">**NX_POP3_CLIENT_TCP_WINDOW_SIZE**: This option sets the size of the Client TCP receive window.</span></span> <span data-ttu-id="d997f-154">これは、IP インスタンスの MTU サイズから IP と TCP のヘッダーを引いた値に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d997f-154">This should be set to the IP instance MTU size minus the IP and TCP header.</span></span> <span data-ttu-id="d997f-155">既定値は 1,460 です。</span><span class="sxs-lookup"><span data-stu-id="d997f-155">The default value is 1460.</span></span>

- <span data-ttu-id="d997f-156">**NX_POP3_MAX_USERNAME**: このオプションでは、POP3 クライアントのユーザー名のバッファー サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="d997f-156">**NX_POP3_MAX_USERNAME**: This option sets the size of the buffer of the POP3 Client user name.</span></span> <span data-ttu-id="d997f-157">既定値は 40 バイトです。</span><span class="sxs-lookup"><span data-stu-id="d997f-157">The default value is 40 bytes.</span></span>

- <span data-ttu-id="d997f-158">**NX_POP3_MAX_PASSWORD**: このオプションでは、POP3 クライアントのパスワードのバッファー サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="d997f-158">**NX_POP3_MAX_PASSWORD**: This option sets the size of the buffer of the POP3 Client password.</span></span> <span data-ttu-id="d997f-159">既定値は 20 バイトです。</span><span class="sxs-lookup"><span data-stu-id="d997f-159">The default value is 20 bytes.</span></span>