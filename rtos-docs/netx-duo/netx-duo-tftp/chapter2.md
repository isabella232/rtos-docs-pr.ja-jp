---
title: 第 2 章 - Azure RTOS NetX Duo TFTP のインストールと使用
description: この章では、Azure RTOS NetX Duo TFTP コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ffb0c433bf1a5665e07da3cc6c240f1d0d8c87d9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811813"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-tftp"></a>第 2 章 - Azure RTOS NetX Duo TFTP のインストールと使用

この章では、Azure RTOS NetX Duo TFTP コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品の配布

Azure RTOS NetX Duo は、 https://github.com/azure-rtos/netxduo/ のパブリック ソース コード リポジトリから入手できます。 パッケージには、次のファイルが含まれています。


- **nxd_tftp_client.h** NetX Duo TFTP クライアントのヘッダー ファイル

- **nxd_tftp_client.c** NetX Duo TFTP クライアントの C ソース ファイル

- **nxd_tftp_server.h** NetX Duo TFTP サーバーのヘッダー ファイル

- **nxd_tftp_server.c** NetX Duo TFTP サーバーの C ソース ファイル

- **filex_stub.h** FileX が存在しない場合のスタブ ファイル

- **nxd_tftp.pdf** NetX Duo TFTP の PDF の説明

- **demo_netxduo_tftp.c** NetX Duo TFTP のデモンストレーション

## <a name="tftp-installation"></a>TFTP のインストール

NetX Duo TFTP を使用する場合は、NetX Duo がインストールされているのと同じディレクトリに前述のディストリビューション全体をコピーします。 たとえば、NetX Duo がディレクトリ *\threadx\arm7\green* にインストールされている場合、*nxd_tftp_client.h*、*nxd_tftp_client.c*、*nxd_tftp_server.h*、および *nxd_tftp_server.c* の各ファイルをこのディレクトリにコピーできます。

## <a name="using-tftp"></a>TFTP の使用

TFTP アプリケーションを実行するには、ThreadX、FileX、NetX Duo を使用するために、アプリケーション コードにそれぞれ *tx_api.h、fx_api.h*、および *nx_api.h* をインクルードした後に、*nxd_tftp_client.h* または nxd_tftp_serverin.h、あるいはこの両方をインクルードする必要があります。 また、アプリケーション プロジェクトには、ビルド プロセスで *nxd_tftp_client.c* または *nxd_tftp_server.c*、あるいはこの両方をインクルードする必要があります。 これらのファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、そのオブジェクト フォームをアプリケーションのファイルと一緒にリンクする必要があります。 NetX Duo TFTP の使用に必要なものはこれですべてです。 "*ヘッダー ファイル*"がインクルードされると、アプリケーション コードで TFTP サービスを使用できるようになります。

> [!NOTE]
> TFTP では NetX Duo UDP のサービスを使用するため、TFTP を使用するときは、前もって *nx_tftp_enable* を呼び出して UDP を有効にしておく必要があります。

## <a name="small-example-system"></a>小規模システムの例

NetX Duo TFTP の使用がいかに簡単であるかを示す例を、下の図 1.1 に示します。 この例では、TFTP インクルード ファイル *nxd_tftp_client.h* と *nxd_tftp_server.h* が 19 行目と 20 行目で取り込まれています。 次に、TFTP サーバーが "*tx_application_define*" の 179 行目に作成されます。 

> [!NOTE]
> TFTP サーバー制御ブロック "*server*" は、45 行目でグローバル変数として既に定義されています。 このデモでは、14 行目の TFTP 通信に IPv4 を使用することを選択します。 正常に作成されると、TFTP サーバーは 304 行目で開始されます。 411 行目では、TFTP クライアントが作成されます。 最後に、クライアントでは 450 行目にファイルを書き込み、485 行目でファイルを読み取ります。

TFTP サーバー スレッド タスクが停止し、324 行目で TFTP サーバーが削除されます。 アプリケーションでは fx_media_close (331 行目) を呼び出してすべてのファイルを閉じ、ファイルとディレクトリのデータを USB メディアに更新する必要があります。

> [!NOTE]
> この例では、TFTP クライアント ファイル要求を受信およびダウンロードするための TFTP サーバー処理に FileX を使用します。 ただし、NX_TFTP_NO_FILEX が定義されている場合、アプリケーションには fx_api.h ではなく file_stub.h を含めることができます。
>
> また、既存の NetX TFTP クライアントおよびサーバー アプリケーションが NetX Duo TFTP で動作することにも注意してください。 ただし、アプリケーション開発者は NetX TFTP アプリケーションを NetX Duo に移植することをお勧めします。 同等の NetX TFTP サービスは次のとおりです。

- *nxd_tftp_server_start*

- *nxd_tftp_server_stop*

- *nxd_tftp_client_file_read*

- *nxd_tftp_client_file_write*

- *nxd_tftp_client_file_open*

```C
/* This is a small demo of TFTP on the high-performance NetX TCP/IP stack. This demo
   relies on ThreadX and NetX Duo, to show a simple file transfer from the client
   and then back to the server. */



/* Indicate if using IPv6. */
#define USE_DUO

/* If the host application is using NetX Duo, determine which IP version to use.
   Make sure IPv6 in NetX Duo is enabled if planning to use TFTP over IPv6 */
#ifdef USE_DUO
#define     IP_TYPE     6
#endif /* USE_DUO        */

#include    "tx_api.h"
#include    "nx_api.h"
#include    "nxd_tftp_client.h"
#include    "nxd_tftp_server.h"
#ifndef     NX_TFTP_NO_FILEX
#include    "fx_api.h"
#endif


#define     DEMO_STACK_SIZE         4096

/* To use another file storage utility define this symbol:
#define NX_TFTP_NO_FILEX
*/

/* Define the ThreadX, NetX, and FileX object control blocks... */

TX_THREAD               server_thread;
TX_THREAD               client_thread;
NX_PACKET_POOL          server_pool;
NX_IP                   server_ip;
NX_PACKET_POOL          client_pool;
NX_IP                   client_ip;
FX_MEDIA                ram_disk;

/* Define the NetX TFTP object control blocks. */

NX_TFTP_CLIENT          client;
NX_TFTP_SERVER          server;

/* Define the application global variables */

#define                 CLIENT_ADDRESS  IP_ADDRESS(1, 2, 3, 5)
#define                 SERVER_ADDRESS  IP_ADDRESS(1, 2, 3, 4)

NXD_ADDRESS             server_ip_address;
NXD_ADDRESS             client_ip_address;

UINT                    error_counter = 0;

/* Define buffer used in the demo application. */
UCHAR                   buffer[255];
ULONG                   data_length;


/* Define the memory area for the FileX RAM disk. */
#ifndef NX_TFTP_NO_FILEX
UCHAR                   ram_disk_memory[32000];
UCHAR                   ram_disk_sector_cache[512];
#endif


/* Define function prototypes. */

VOID    _fx_ram_driver(FX_MEDIA *media_ptr);
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
void    client_thread_entry(ULONG thread_input);
void    server_thread_entry(ULONG thread_input);


/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

UINT    status;
UCHAR   *pointer;


    /* Setup the working pointer. */
    pointer =  (UCHAR *) first_unused_memory;


    /* Create the main TFTP server thread. */
    status = tx_thread_create(&server_thread, "TFTP Server Thread", server_thread_entry, 0,
                              pointer, DEMO_STACK_SIZE,
                              4,4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer += DEMO_STACK_SIZE ;

    /* Check for errors. */
    if (status)
        error_counter++;


    /* Create the main TFTP client thread at a slightly lower priority. */
    status = tx_thread_create(&client_thread, "TFTP Client Thread", client_thread_entry, 0,
                              pointer, DEMO_STACK_SIZE,
                              5, 5, TX_NO_TIME_SLICE, TX_DONT_START);

    pointer += DEMO_STACK_SIZE ;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Note: The data portion of a packet is exactly 512 bytes, but the packet payload size must
       be at least 580 bytes. The remaining bytes are used for the UDP, IP, and Ethernet
       headers and byte alignment requirements. */

    status =  nx_packet_pool_create(&server_pool, "TFTP Server Packet Pool", NX_TFTP_PACKET_SIZE, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Create the IP instance for the TFTP Server. */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance", SERVER_ADDRESS, 0xFFFFFF00UL,
                                        &server_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status =  nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Enable UDP. */
    status =  nx_udp_enable(&server_ip);

    /* Check for errors. */
    if (status)
        error_counter++;


    /* Create the TFTP server. */
#ifdef USE_DUO
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
    /* Specify the tftp server global address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x102;
#endif
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_ADDRESS;

#endif

    status =  nxd_tftp_server_create(&server, "TFTP Server Instance", &server_ip, &ram_disk,
                                      pointer, DEMO_STACK_SIZE, &server_pool);
#else
    status =  nx_tftp_server_create(&server, "TFTP Server Instance", &server_ip, &ram_disk,
                                      pointer, DEMO_STACK_SIZE, &server_pool);
#endif

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for errors for the server. */
    if (status)
        error_counter++;

    /* Create a packet pool for the TFTP client. */

    /* Note: The data portion of a packet is exactly 512 bytes, but the packet payload size must
       be at least 580 bytes. The remaining bytes are used for the UDP, IP, and Ethernet
       headers and byte alignment requirements. */

    status =  nx_packet_pool_create(&client_pool, "TFTP Client Packet Pool", NX_TFTP_PACKET_SIZE, pointer, 8192);
    pointer =  pointer + 8192;

    /* Create an IP instance for the TFTP client. */
    status = nx_ip_create(&client_ip, "TFTP Client IP Instance", CLIENT_ADDRESS, 0xFFFFFF00UL,
                                                &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for IP Instance 1. */
    status =  nx_arp_enable(&client_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable UDP for client IP instance. */
    status |=  nx_udp_enable(&client_ip);
    status |= nx_icmp_enable(&client_ip);

    tx_thread_resume(&client_thread);
}

void server_thread_entry(ULONG thread_input)
{

UINT        status, running;
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
UINT        address_index;
UINT        iface_index;
#endif
#endif


    /* Allow time for the network driver and NetX to get initialized. */
    tx_thread_sleep(100);

#ifndef  NX_TFTP_NO_FILEX

    /* Format the RAM disk - the memory for the RAM disk was defined above. */
    status = fx_media_format(&ram_disk,
                            _fx_ram_driver,                  /* Driver entry             */
                            ram_disk_memory,                 /* RAM disk memory pointer  */
                            ram_disk_sector_cache,           /* Media buffer pointer     */
                            sizeof(ram_disk_sector_cache),   /* Media buffer size        */
                            "MY_RAM_DISK",                   /* Volume Name              */
                            1,                               /* Number of FATs           */
                            32,                              /* Directory Entries        */
                            0,                               /* Hidden sectors           */
                            256,                            /* Total sectors            */
                            128,                             /* Sector size              */
                            1,                               /* Sectors per cluster      */
                            1,                               /* Heads                    */
                            1);                              /* Sectors per track        */

    /* Check for errors. */
    if (status != FX_SUCCESS)
    {
        return;
    }

    /* Open the RAM disk. */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory, ram_disk_sector_cache,
                               sizeof(ram_disk_sector_cache));

    /* Check for errors. */
    if (status != FX_SUCCESS)
    {
        return;
    }

#endif /*  NX_TFTP_NO_FILEX */

#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6

    /* Enable ICMPv6 services. */
    status |= nxd_icmp_enable(&server_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 services for the server. */
    status = nxd_ipv6_enable(&server_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* This assumes the primary interface. See the NetX Duo
       User Guide for more information on address configuration. */
    iface_index = 0;
    status = nxd_ipv6_address_set(&server_ip, iface_index, NX_NULL, 10, &address_index);
    status += nxd_ipv6_address_set(&server_ip, iface_index, &server_ip_address, 64, &address_index);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Wait for DAD to validate the address. */
    tx_thread_sleep(500);
#endif

#endif /* IP_TYPE == 6 */

    /* Start the NetX TFTP server. */
#ifdef USE_DUO
    status =  nxd_tftp_server_start(&server);
#else
    status =  nx_tftp_server_start(&server);
#endif

    /* Check for errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Run for a while */
    running = NX_TRUE;
    while(running)
        tx_thread_sleep(200);


    /* Stop and delete the TFTP server. */
#ifdef USE_DUO
    nxd_tftp_server_delete(&server);
#else
    nx_tftp_server_delete(&server);
#endif

    /* Close all open files and ensure directory information is also written out to the media.
    This will also flush the file data to USB media*/
    status = fx_media_close(&ram_disk);

    if (status)
    {
        error_counter++;
    }

    return;

}


/* Define the TFTP client thread. */

void    client_thread_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;
UINT        all_done = NX_FALSE;
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
UINT        address_index;
UINT        iface_index;
#endif
#endif


    /* Allow time for the network driver and NetX to get initialized. */
    tx_thread_sleep(100);

#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6

    /* Enable ECMPv6 services for the client. */
    status = nxd_icmp_enable(&client_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 services for the client. */
    status = nxd_ipv6_enable(&client_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Set the Client IPv6 address */
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    client_ip_address.nxd_ip_address.v6[1] = 0xf101;
    client_ip_address.nxd_ip_address.v6[2] = 0;
    client_ip_address.nxd_ip_address.v6[3] = 0x101;

    /* This assumes the primary interface. See the NetX Duo
       User Guide for more information on address configuration. */
    iface_index = 0;
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, &address_index);
    status += nxd_ipv6_address_set(&client_ip, iface_index, &client_ip_address, 64, &address_index);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Wait for the link local and global addresses to be validated. */
    tx_thread_sleep(500);
#endif
#endif /*(IP_TYPE == 6) */


    /* The TFTP services used below include the NetX equivalent service which will work with
       NetX Duo TFTP. However, it is recommended for developers to port their applications
       to the newer services that take the NXD_ADDRESS type and support both IPv4 and IPv6
       communication.
    */

    /* Create a TFTP client. */
#ifdef USE_DUO
    status =  nxd_tftp_client_create(&client, "TFTP Client", &client_ip, &client_pool, IP_TYPE);
#else
    status =  nx_tftp_client_create(&client, "TFTP Client", &client_ip, &client_pool);
#endif

    /* Check status. */
    if (status)
        return;

    /* Open a TFTP file for writing. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_open(&client, "test.txt", &server_ip_address, NX_TFTP_OPEN_FOR_WRITE, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_open(&client, "test.txt", SERVER_ADDRESS, NX_TFTP_OPEN_FOR_WRITE, 100);
#endif

    /* Check status. */
    if (status)
        return;

    /* Allocate a TFTP packet. */
#ifdef USE_DUO
    status =  nxd_tftp_client_packet_allocate(&client_pool, &my_packet, 100, IP_TYPE);
#else
    status =  nx_tftp_client_packet_allocate(&client_pool, &my_packet, 100);
#endif
    /* Check status. */
    if (status)
        error_counter++;

    /* Write ABCs into the packet payload!  */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ  ", 28);

    /* Adjust the write pointer. */
    my_packet -> nx_packet_length =  28;
    my_packet -> nx_packet_append_ptr =  my_packet -> nx_packet_prepend_ptr + 28;

    /* Write this packet to the file via TFTP. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_write(&client, my_packet, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_write(&client, my_packet, 100);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Close this file. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_close(&client, IP_TYPE);
#else
    status =  nx_tftp_client_file_close(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Open the same file for reading. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_open(&client, "test.txt", &server_ip_address, NX_TFTP_OPEN_FOR_READ, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_open(&client, "test.txt", SERVER_ADDRESS, NX_TFTP_OPEN_FOR_READ, 100);
#endif

    /* Check status. */
    if (status)
        error_counter++;
    do
    {

    /* Read the file back. */
#ifdef USE_DUO
        status =  nxd_tftp_client_file_read(&client, &my_packet, 100, IP_TYPE);
#else
        status =  nx_tftp_client_file_read(&client, &my_packet, 100);
#endif
        /* Check for retranmission/dropped packet error. Benign. Try again... */
        if (status == NX_TFTP_INVALID_BLOCK_NUMBER)
        {

            continue;
        }
        else if (status == NX_TFTP_END_OF_FILE)
        {

            /* All done. */
            all_done = NX_TRUE;
        }
        else if (status != NX_SUCCESS)
        {

            /* Internal error, invalid packet or error on read. */
            break;
        }


        /* Do something with the packet data and release when done. */
        nx_packet_data_retrieve(my_packet, buffer, &data_length);
        buffer[data_length] = 0;
        printf("Receive data: %s\n", buffer);

        printf("release packet in demo.\n");

        nx_packet_release(my_packet);

    } while (all_done == NX_FALSE);

    /* Close the file again. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_close(&client, IP_TYPE);
#else
    status =  nx_tftp_client_file_close(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Delete the client. */
#ifdef USE_DUO
    status =  nxd_tftp_client_delete(&client);
#else
    status =  nx_tftp_client_delete(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    return;
}
```

図 1.1 NetX Duo での TFTP の使用例

## <a name="configuration-options"></a>構成オプション

NetX Duo TFTP を構築するためのいくつかの構成オプションがあります。 次の一覧で、それぞれについて詳しく説明します。 特に指定がない限り、これらのオプションは *nxd_tftp_client.h* と *nxd_tftp_server.h* にあります。


- **NX_DISABLE_ERROR_CHECKING** このオプションを定義すると、基本的な TFTP エラー チェックが削除されます。 通常は、アプリケーションがデバッグされた後に使用します。

- **NX_TFTP_SERVER_PRIORITY** TFTP サーバーのスレッドの優先順位。 既定では、この値は 16 番目の優先順位を示す 16 に定義されています。

- **NX_TFTP_SERVER_TIME_SLICE** 同じ優先順位の他のスレッドに起動する前に、TFTP サーバーを実行するタイム スライス。 既定値は 2 です。

- **NX_TFTP_MAX_CLIENTS** サーバーが一度に処理できるクライアントの最大数。 既定では、10 個のクライアントを一度にサポートするために、この値は 10 に設定されています。

- **NX_TFTP_ERROR_STRING_MAX** エラー文字列内の最大文字数。 既定値は 64 です。

- **NX_TFTP_NO_FILEX** このオプションを定義すると、FileX の依存関係のスタブが提供されます。 このオプションを定義しても、TFTP クライアントは変更なしで機能します。 TFTP サーバーが適切に機能するためには、変更するか、ユーザーがいくつかの FileX サービスを作成する必要があります。

- **NX_TFTP_TYPE_OF_SERVICE** TFTP UDP 要求に必要なサービスの種類です。 既定では、この値は通常の IP パケット サービスを示す NX_IP_NORMAL に定義されています。

- **NX_TFTP_FRAGMENT_OPTION** TFTP UDP 要求の断片化を有効にします。 既定では、この値は NX_DONT_FRAGMENT であり TFTP UDP 断片化は無効になっています。

- **NX_TFTP_TIME_TO_LIVE** このパケットが破棄されるまでに通過できるルーターの数を指定します。 既定値は 0x80 に設定されます。

- **NX_TFTP_SOURCE_PORT** このオプションを使用すると、TFTP クライアント アプリケーションで TFTP クライアントの UDP ソケット ポートを指定できます。 既定値は NX_ANY_PORT です。

- ***NX_TFTP_SERVER_RETRANSMIT_ENABLE*** TFTP サーバーのタイマーが、各 TFTP クライアント セッションで最近のアクティビティ (ACK またはデータ パケット) を確認できるようにします。 セッション タイムアウトが最大回数を過ぎると、接続が失われたと見なされます。 サーバーではクライアント要求をクリアし、開いているファイルを閉じて、次のクライアントが接続要求を使用できるようにします。 既定の設定は無効です。

- **NX_TFTP_SERVER_TIMEOUT_PERIOD** TFTP サーバー タイマー入力関数がクライアント接続でパケットを受信するかどうかを確認する間隔を指定します。 既定値は、20 タイマー ティックです。

- **NX_TFTP_SERVER_RETRANSMIT_TIMEOUT** これは、クライアントから有効な ACK またはデータ パケットを受信するためのタイムアウトです。 既定値は、200 タイマー ティックです *。*

- **NX_TFTP_SERVER_MAX_RETRIES** クライアント セッションの再転送タイムアウトが更新される最大回数を指定します。 この回数を過ぎると、セッションはサーバーによって閉じられます。

- **NX_TFTP_MAX_CLIENT_RETRANSMITS** サーバーが、クライアントにエラー メッセージを送信してセッションを閉じることなく、クライアントから (ドロップされる) 重複する ACK またはデータ パケットを受信する最大回数を指定します。 NX_TFTP_SERVER_RETRANSMIT_ENABLE が定義されている場合は効果がありません。
