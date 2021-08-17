---
title: 第 2 章 - Azure RTOS NetX Duo Telnet のインストールと使用
description: この章では、Azure RTOS NetX Duo Telnet コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4781f45dc37f8c48a9f491d6cb67299432f3ae6743d12d9d92134298474182a5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799355"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-telnet"></a>第 2 章 - Azure RTOS NetX Duo Telnet のインストールと使用

この章では、Azure RTOS NetX Duo Telnet コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品の配布

Azure RTOS NetX Duo Telnet パッケージは <https://github.com/azure-rtos/netxduo> で入手できます。 パッケージには、次のファイルが含まれています。

- **nxd_telnet_client.h**: NetX Duo 用 Telnet クライアントのヘッダー ファイル
- **nxd_telnet_client.c**: NetX Duo 用 Telnet クライアントの C ソース ファイル
- **nxd_telnet_server.h**: NetX Duo 用 Telnet サーバーのヘッダー ファイル
- **nxd_telnet_server.c**: NetX Duo 用 Telnet サーバーの C ソース ファイル
- **nxd_telnet.pdf**: NetX Duo 用 Telnet の PDF での説明
- **demo_netxduo_telnet.c**: NetX Duo Telnet のデモンストレーション

## <a name="telnet-installation"></a>Telnet のインストール

NetX Duo 用 Telnet を使用するには、前述のディストリビューション全体を、NetX Duo がインストールされているものと同じディレクトリにコピーする必要があります。 たとえば、NetX Duo がディレクトリ “ *\threadx\arm7\green*” にインストールされている場合、*nxd_telnet_client.h*、*nxd_telnet_client.c*、*nxd_telnet_server.c、nxd_telnet_server.h* ファイルをこのディレクトリにコピーする必要があります。

## <a name="using-telnet"></a>Telnet の使用

NetX Duo 用 Telnet を使用するのは簡単です。 ThreadX と NetX Duo を使用するには、基本的に、アプリケーション コードに、*tx_api.h* と *nx_api.h* をインクルードした後に Telnet サーバー アプリケーション用の *nxd_telnet_server.h* と Telnet クライアント アプリケーション用の *nxd_telnet_client.h* をインクルードする必要があります。 "*ヘッダー*" をインクルードすると、アプリケーション コードで、このガイドで後述する Telnet 関数呼び出しを行うことができるようになります。 また、アプリケーションでは、ビルド プロセスで *nxd_telnet_client.c* と *nxd_telnet_server.c* もインクルードする必要があります。 これらのファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、そのオブジェクト形式をアプリケーションのファイルと一緒にリンクする必要があります。 NetX Duo Telnet の使用に必要なものはこれですべてです。

Telnet クライアント機能が必要ない場合は、*nxd_telnet_client.c* ファイルを省略できます。

Telnet では NetX Duo TCP サービスを利用するため、Telnet を使用する前に、*nx_tcp_enable* 呼び出しを使用して TCP を有効にする必要があることにも注意してください。

## <a name="small-example-system"></a>小規模のシステム例

NetX Duo Telnet を使用する方法の例を以下の図 1.1 に示します。 この例では、Telnet インクルード ファイルは 7 行目および 8 行目に挿入されて "*います*"。 次に、Telnet サーバーが "*tx_application_define*" の 146 行目に作成されます。 Telnet サーバーとクライアントのコントロール ブロックは、前もって 23 行目から 24 行目にグローバル変数として定義されていることに注意してください。

Telnet サーバーまたはクライアントを起動するには、事前に NetX Duo でそれらの IP アドレスを検証する必要があります。 IPv4 接続の場合、これを行うには、単純に短時間待機することで、NetX ドライバーが 166 行目でシステムを初期化できるようにします。 IPv6 接続の場合は、このために IPv6 と ICMPv6 を有効にする必要があり、171 行目から 172 行目で行います。 クライアントは、181 行目から 186 行目でプライマリ インターフェイスにそのグローバルおよびリンク ローカルの IPv6 アドレスを設定し、バックグラウンドで NetX Duo の検証が完了するのを待機します。 サーバーも、192 行目から 198 行目でプライマリ インターフェイスにそのグローバルおよびリンク ローカルのアドレスを設定します。 2 つのサービス *nxd_ipv6_global_address_set* と *nxd_ipv6_linklocal_address_set* が "*nxd_ipv6_address_set サービス*" に置き換えられていることに注意してください。 以前の 2 つのサービスは引き続きレガシの NetX Duo アプリケーションで使用できますが、最終的には非推奨になります。 開発者には、代わりに *nxd_ipv6_address_set* を使用することが推奨されます。

NetX Duo による IP アドレスの検証が正常に行われると、*nxd_telnet_server_start* サービスを使用して、215 行目で Telnet サーバーが起動されます。 226 行目では、*nx_telnet_client_create* サービスを使用して Telnet クライアントが作成されます。 その後に、IPv4 アプリケーションの場合は 242 行目、IPv6 アプリケーションの場合は 238 行目で、それぞれ *nxd_telnet_client_connect* および *nx_telnet_client_connect* サービスを使用して、Telnet サーバーに接続されます。 検証およびサーバーとの接続が正常に行われた後、切断される前にいくつかのやりとりが行われます。

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

## <a name="configuration-options"></a>構成オプション

NetX Duo 用 Telnet を構築するための構成オプションがいくつかあります。 これらの #define は、*nxd_telnet_server.h* と *nxd_telnet_client.h* をインクルードする前にアプリケーションによって設定できます。

以下に、すべてのオプションの一覧と、それぞれの詳細な説明を示します。  
  
- **NX_DISABLE_ERROR_CHECKING**: このオプションを定義すると、基本的な Telnet エラー チェックが削除されます。 通常は、アプリケーションがデバッグされた後に使用します。
- **NX_TELNET_MAX_CLIENTS**: サーバー スレッドでサポートされる Telnet クライアントの最大数。 既定では、この値は 4 として定義され、一度に最大 4 つのクライアントを指定します。
- **NX_TELNET_SERVER_PRIORITY**: Telnet サーバー スレッドの優先順位。 既定では、この値は 16 に定義され、優先順位 16 を示します。
- **NX_TELNET_TOS**: Telnet TCP 要求に必要なサービスの種類。 既定では、この値は NX_IP_NORMAL として定義され、  
通常の IP パケット サービスを示します。
- **NX_TELNET_FRAGMENT_OPTION**: Telnet TCP 要求でのフラグメントの有効化。 既定では、この値は NX_DONT_FRAGMENT であり、HTTP TCP のフラグメント化が無効になります。
- **NX_TELNET_SERVER_WINDOW_SIZE**: サーバー ソケットのウィンドウ サイズ。 既定では、この値は 2048 バイトです。
- **NX_TELNET_TIME_TO_LIVE**: このパケットが破棄されるまでに通過できるルーターの数を指定します。 既定値は 0x80 に設定されています。
- **NX_TELNET_SERVER_TIMEOUT**: 内部サービスが中断される ThreadX ティックの数を指定します。 既定値は 10 秒に設定されています。
- **NX_TELNET_ACTIVITY_TIMEOUT**: サーバーがクライアント接続を切断するまでに、アクティビティがないまま経過することができる秒数を指定します。 既定値は 600 秒に設定されています。
- **NX_TELNET_TIMEOUT_PERIOD**: クライアント アクティビティのタイムアウトを確認する間隔の秒数を指定します。 既定値は 60 秒に設定されています。
- **NX_TELNET_SERVER_OPTION_DISABLE**: 定義されている場合、Telnet オプションのネゴシエーションは無効になります。 既定では、このオプションは定義されていません。
- **NX_TELNET_SERVER_USER_CREATE_PACKET_POOL**: 定義されている場合、Telnet サーバーのパケット プールを外部に作成する必要があります。 これは、NX_TELNET_SERVER_OPTION_DISABLE が定義されていない場合にのみ有効です。 既定では、このオプションは定義されず、Telnet サーバー スレッドによってそれ自体のパケット プールが作成されます。
- **NX_TELNET_SERVER_PACKET_PAYLOAD**: オプションのネゴシエーションのために Telnet サーバーによって作成されるパケット ペイロードのサイズを定義します。 Telnet サーバーでは、NX_TELNET_SERVER _OPTION_DISABLE が定義されていない (Telnet オプションが有効になっている) 場合にのみこのパケット プールが作成されることに注意してください。 このオプションの既定値は 300 です。
- **NX_TELNET_SERVER_PACKET_POOL_SIZE**: Telnet ネゴシエーションに使用される Telnet サーバー パケット プールのサイズを定義します。 Telnet サーバーでは、NX_TELNET_SERVER _OPTION_DISABLE が定義されていない (Telnet オプションが有効になっている) 場合にのみこのパケット プールが作成されることに注意してください。 このオプションの既定値は 2048 (\~5 から 6 パケット) です。
