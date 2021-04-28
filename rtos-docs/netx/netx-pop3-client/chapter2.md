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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pop3-client"></a>第 2 章 - Azure RTOS NetX POP3 クライアントのインストールと使用

NetX POP3 クライアントには、1 つのソース ファイル、1 つのヘッダー ファイル、および 1 つのデモ ファイルが含まれています。 MD5 ダイジェスト サービス用の 2 つの追加ファイルがあります。 また、ユーザー ガイド PDF ファイル (このドキュメント) もあります。

- **nx_pop3_client.c**: NetX POP3 クライアント API 用の C ソース ファイル
- **nx_pop3_client.h**: NetX POP3 クライアント API 用の C ヘッダー ファイル
- **demo_netxduo_pop3_client.c**: POP3 クライアントの作成とセッション開始のデモ ファイル
- **nx_md5.c**: MD5 ダイジェスト サービスを定義する C ソース ファイル
- **nx_md5.h**: MD5 ダイジェスト サービスを定義する C ヘッダー ファイル
- **nx_pop3_client.pdf** NetX POP3 クライアントのユーザー ガイド

NetX POP3 クライアントを使用する場合は、NetX がインストールされているのと同じディレクトリに前述のディストリビューション全体をコピーします。 たとえば、NetX が " *\threadx\mcf5272\green*" ディレクトリにインストールされている場合は、*nx_md5.h*、*nx_md5.c*、*nx_pop3_client.h、nx_pop3_client.c* の各ファイルをこのディレクトリにコピーする必要があります。

## <a name="using-netx-pop3-client"></a>NetX POP3 クライアントの使用

NetX POP3 クライアント サービスを使用するには、そのビルド プロジェクトに *nx_pop3_client.c* を追加する必要があります。 ThreadX と NetX を使用するために、アプリケーション コードに *tx_api.h* と *nx_api.h* を、その後に *nx_md5.h、nx_pop3.h、nx_pop3_client.h* をインクルードする必要があります。

これらのファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、オブジェクト コードをアプリケーションのファイルと一緒にリンクする必要があります。 これが NetX POP3 クライアントを使用するために必要なすべてです。

## <a name="small-example-of-the-netx-pop3-client"></a>NetX POP3 クライアントの小規模な例

NetX POP3 クライアント サービスの使用方法の例を下の図 1 に示します。 このデモでは、37 と 38 行目でメールのダウンロードとセッションの完了を通知する 2 つのコールバックが設定されます。 76 行目で POP3 クライアントのパケット プールが作成されます。 88 行目で IP スレッド タスクが作成されます。 このパケット プールも POP3 クライアントのパケット プールに使用されることに注意してください。 107 行目で IP タスクに対して TCP が有効になります。

133 行目の、アプリケーション スレッド エントリ関数 *demo_thread_entry* 内で POP3 クライアントが作成されます。 これは、*nx_pop3_client_create* サービスも POP3 サーバーとの TCP 接続を試行するためです。 成功した場合、アプリケーションは 149 行目で *nx_pop3_client_mail_items_get* サービスを使用して、そのメールドロップ内のアイテムの数を POP3 サーバーに照会します。

アイテムが 1 つ以上ある場合、アプリケーションは while ループを反復処理して各メール アイテムのメール メッセージをダウンロードします。 149 行目の *nx_pop3_client_mail_item_get* 呼び出しで RETR 要求が行われます。 成功した場合、アプリケーションは 196 行目でメッセージの最後のパケットを受信したことを検出するまで、177 行目で *nx_pop3_client_mail_item_message_get* サービスを使用して、パケットをダウンロードします。 最後に、アプリケーションは 199 行目の *nx_pop3_client_mail_item_delete* 呼び出しで、ダウンロードが正常に実行されたと見なして、メール アイテムを削除します。 RFC 1939 では、クライアントのメールドロップにメールが蓄積されないように、ダウンロードしたメール アイテムを削除するよう POP3 クライアントからサーバーに指示することを推奨しています。 ただし、サーバーが自動的にそうする場合があります。

すべてのメール アイテムがダウンロードされた場合、または POP3 クライアントのサービス呼び出しが失敗した場合、アプリケーションはループを終了し、217 行目で *nx_pop3_client_delete* サービスを使用して、POP3 クライアントを削除します。

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

図 1. NetX POP3 クライアント アプリケーションの例

## <a name="pop3-client-configuration-options"></a>POP3 クライアントの構成オプション

NetX POP3 クライアントには、いくつかの構成オプションがあります。 以下はすべてのオプションの一覧で、詳細に説明されています。

- **NX_POP3_CLIENT_PACKET_TIMEOUT**: これは、POP3 クライアントがパケットを割り当てる際の待機オプションを秒単位で定義します。 既定値は 1 秒です。

- **NX_POP3_CLIENT_CONNECTION_TIMEOUT**: これは、POP3 クライアントが POP3 サーバーと接続する際の待機オプションを秒単位で定義します。 既定値は 30 秒です。

- **NX_POP3_CLIENT_DISCONNECT_TIMEOUT**: これは、POP3 クライアントが POP3 サーバーから切断する際の待機オプションを秒単位で定義します。 既定値は 2 秒です。

- **NX_POP3_TCP_SOCKET_SEND_WAIT**: このオプションでは、*nx_tcp_socket_send* サービスの呼び出しの待機オプションを秒単位で設定します。 既定値は 2 秒です。

- **NX_POP3_SERVER_REPLY_TIMEOUT**: このオプションでは、*nx_tcp_socket_receive* サービスの呼び出しにおけるクライアント要求に対するサーバー応答の待機オプションを設定します。 既定値は 10 秒です。

- **NX_POP3_CLIENT_TCP_WINDOW_SIZE**: このオプションでは、クライアントの TCP 受信ウィンドウのサイズを設定します。 これは、IP インスタンスの MTU サイズから IP と TCP のヘッダーを引いた値に設定する必要があります。 既定値は 1,460 です。

- **NX_POP3_MAX_USERNAME**: このオプションでは、POP3 クライアントのユーザー名のバッファー サイズを設定します。 既定値は 40 バイトです。

- **NX_POP3_MAX_PASSWORD**: このオプションでは、POP3 クライアントのパスワードのバッファー サイズを設定します。 既定値は 20 バイトです。