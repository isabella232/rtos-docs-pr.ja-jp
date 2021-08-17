---
title: 第 2 章 - FTP のインストールと使用
description: この章では、NetX Duo FTP サービスのインストール、設定、および使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bef7dcce9354e6653dd92c5a47a29d120268faeb4a30b4d146c9e10d2d69084e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790226"
---
# <a name="chapter-2---installation-and-use-of-ftp"></a>第 2 章 - FTP のインストールと使用

この章では、NetX Duo FTP サービスのインストール、設定、および使用に関連するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品の配布

NetX Duo FTP は、[https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) で入手できます。 このパッケージには、次のような 2 つのソース ファイルと、このドキュメントを含む 1 つの PDF ファイルが含まれています。

- **nxd_tftp_client.h**: NetX Duo FTP クライアント用のヘッダー ファイル
- **nxd_tftp_client.h**: NetX Duo FTP クライアントの C ソース ファイル
- **nxd_tftp_client.h**: NetX Duo FTP サーバー用のヘッダー ファイル
- **nxd_tftp_client.h**: NetX Duo FTP サーバーの C ソース ファイル
- **filex_stub.h**: FileX が存在しない場合のスタブ ファイル
- **nx_ftp.pdf**: NetX Duo 用の FTP に関する PDF 説明書
- **demo_netxduo_ftp.c**: FTP デモンストレーション システム

## <a name="netx-duo-ftp-installation"></a>NetX Duo FTP のインストール

NetX Duo FTP API シリーズを使用するには、前述のディストリビューション全体を、NetX Duo がインストールされているのと同じディレクトリにコピーする必要があります。 たとえば、NetX Duo がディレクトリ " *\threadx\arm7\green*" にインストールされている場合、FTP クライアント アプリケーション用のディレクトリに *nxd_ftp_client.h* と *nxd_ftp_client.c* をコピーする必要があります。また、FTP サーバー アプリケーション用のディレクトリに *nxd_ftp_server.h* ファイルと *nxd_ftp_server.c* ファイルをコピーする必要があります。

## <a name="using-netx-duo-ftp"></a>NetX Duo FTP の使用

NetX Duo FTP API は簡単に使用できます。 基本的には、アプリケーション コードに ThreadX、FileX、および NetX Duo を使用するための *tx_api.h、fx_api.h* および *nx_api.h* をインクルードしてから、FTP クライアント アプリケーション用の *nxd_ftp_client.h* または FTP サーバー アプリケーション用の *nxd_ftp_server* のいずれかをインクルードする必要があります。 ビルド プロジェクトに、FTP ソース コードとホスト アプリケーション ファイルを含める必要があります。ThreadX および NetX ライブラリ ファイルを含めることは言うまでもありません。 NetX Duo FTP を使用するために必要なものは、これですべてです。

FTP では NetX Duo TCP サービスを利用するため、FTP を使用する前に、*nx_tcp_enable* を呼び出して TCP を有効にする必要があります。

NetX Duo ライブラリは IPv6 に対して有効にすることができ、IPv4 ネットワークは引き続きサポートされることに注意してください。 ただし、NetX Duo では、有効にしない限り、IPv6 はサポートできません。 NetX Duo で IPv6 処理を無効にするには、**NX_DISABLE_IPV6** を *nx_user.h* ファイルに定義する必要があります。また、**NX_INCLUDE_USER_DEFINE_FILE** を *nx_port.h* ファイルに定義することで、そのファイルを NetX Duo ライブラリのビルドに含める必要があります。 既定では、**NX_DISABLE_IPV6** は定義されません (IPv6 は有効です)。 これは、IP タスクで IPv6 プロトコルとサービスを設定する *nxd_ipv6_enable* サービスとは異なっており、**NX_DISABLE_IPV6** を定義する必要はありません。

## <a name="small-example-system-of-netx-duo-ftp"></a>NetX Duo FTP の小規模のシステム例

NetX Duo FTP の使用がいかに簡単であるかを示す例を、下の図 1.1 に示します。 この例では、FTP サーバーと FTP クライアントの両方が作成されます。 そのため、行 10 と行 11 で、両方の FTP インクルード ファイル (*nxd_ftp_client.h と nxd_ftp_server.h*) が取り込まれます。 次に、行 99 の "*tx_application_define*" で、FTP サーバーが作成されます。 FTP サーバーとクライアントのコントロール ブロックは、行 26 でグローバル変数として既に定義されていることに注意してください。

このデモでは、NetX Duo FTP と従来の IPv4 制限付き FTP サービスで利用可能な Duo 関数を使用する方法を示します。 このデモでは、IPv6 機能を使用するために、行 16 で USE_IPV6 を定義します。

行 162 で、IPv4 と IPv6 の両方をサポートする USE_IPV6 がホスト アプリケーションによって定義されている場合、***nxd_ftp_server_create** _ を使用して FTP サーバーが作成されます。 そうでない場合、行 166 で、FTP サーバーは、IPv4 限定サービスを使用して、_ *_nx_ftp_server_create_** によって作成されます。 'Duo' 関数では、IPv4 サービスとは異なるログインおよびログアウト関数の引数が使用されます。どちらも、ファイルの末尾の 行 534 から 行568 で定義されています。

その後、FTP サーバーは、行 466 から始まる FTP サーバー スレッド エントリ関数で、NetX Duo により IPv6 アドレス (グローバルおよびリンク ローカル) を確立する必要があります。 その後、行 518 で FTP サーバーが起動され、FTP クライアント要求に対応できるようになります。

行 316 で FTP クライアントが作成され、FTP サーバーと同じプロセスを経由して FTP クライアント IP タスク IPv6 が有効になり、その IPv6 アドレスが行 263 から 行 313 で検証されます。

次に、USE_IPV6 が定義されている場合は行 334 で ***nxd_ftp_client_connect** _ を使用して、IPv4 限定サービスが使用されている場合は行 340 で _*_nx_ftp_client_connect_** を使用して、クライアントが FTP サーバーに接続されます。 FTP クライアント スレッド関数の途中で、FTP サーバーにファイルが書き込まれ、切断前に読み取られます。

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

**図 1.1 NetX Duo FTP の例**

## <a name="configuration-options"></a>構成オプション

NetX FTP と NetX Duo FTP を構築するためのさまざまな構成オプションがあります。 既定値が示されていますが、各定義は、

指定された NetX Duo FTP ヘッダー ファイルをインクルードする前にアプリケーションによって設定できます。 ヘッダー ファイルが指定されていない場合、オプションは *nxd_ftp_client.h と nxd_ftp_server.h* の両方で使用できます。 次の一覧で、それぞれについて詳しく説明します。

- **NX_FTP_SERVER_PRIORITY**: FTP サーバー スレッドの優先順位。 既定では、この値は優先順位 16 を示す 16 に定義されます。
- **NX_FTP_MAX_CLIENTS**: サーバーで一度に処理できるクライアントの最大数。 既定では、この値は、一度に 4 台のクライアントをサポートする 4 に設定されます。
- **NX_FTP_SERVER_MIN_PACKET_PAYLOAD**: TCP、IP、ネットワーク フレーム ヘッダー、および HTTP データを含む、サーバーのパケット プール ペイロードの最小サイズ (バイト単位)。 既定値は、256 (FileX でのファイル名の最大長) + 12 バイト (ファイル情報用)、および NX_PHYSICAL_TRAILER です。
- **NX_FTP_SERVER_TIMEOUT**: 内部サービスが中断される ThreadX ティック数を指定します。 既定値は 1 秒 (1 * NX_IP_PERIODIC_RATE) に設定されます。
- **NX_FTP_ACTIVITY_TIMEOUT**: アクティビティがない場合にクライアント接続を維持する秒数を指定します。 既定値は 240 に設定されます。
- **NX_FTP_TIMEOUT_PERIOD**: サーバーがクライアント アクティビティをチェックする間隔を秒単位で指定します。 既定値は 60 に設定されます。
- **NX_FTP_SERVER_RETRY_SECONDS**: サーバーの応答を再送するまでの初期タイムアウトを秒単位で指定します。 既定値は 2 です。
- **NX_FTP_SERVER_TRANSMIT_QUEUE_DEPTH**: サーバー ソケットでキューに置かれた送信パケットの最大の深さを指定します。 既定値は 20 です。
- **NX_FTP_SERVER_RETRY_MAX**: パケットあたりの最大再試行回数を指定します。 既定値は 10 です。
- **NX_FTP_SERVER_RETRY_SHIFT**: 再試行タイムアウトを設定するときにシフトするビット数を指定します。 既定値は 2 です。たとえば、すべての再試行タイムアウトは、前の再試行の 2 倍の長さになります。
- **NX_FTP_NO_FILEX**: このオプションを定義すると、FileX の依存関係のスタブが提供されます。 このオプションを定義した場合、変更なしで FTP クライアントが機能します。 FTP サーバーを適切に機能させるためには、変更するか、ユーザーがいくつかの FileX サービスを作成する必要があります。
- **NX_FTP_CONTROL_TOS**: FTP 制御要求に必要なサービスの種類。 既定では、この値は、通常の IP パケット サービスを示す NX_IP_NORMAL に定義されます。
- **NX_FTP_DATA_TOS**: FTP データ要求に必要なサービスの種類。 既定では、この値は、通常の IP パケット サービスを示す NX_IP_NORMAL に定義されます。
- **NX_FTP_FRAGMENT_OPTION**: FTP 要求のフラグメントを有効にします。 この値の既定値は NX_DONT_FRAGMENT であり、FTP TCP のフラグメント化が無効になります。
- **NX_FTP_CONTROL_WINDOW_SIZE**: TCP 制御ソケット ウィンドウのサイズ。 既定では、この値は 400 バイトです。
- **NX_FTP_DATA_WINDOW_SIZE**: TCP データ ソケット ウィンドウのサイズ。 既定では、この値は 2,048 バイトです。
- **NX_FTP_TIME_TO_LIVE**: 破棄されるまでにこのパケットが通過できるルーターの数を指定します。 既定値は 0x80 に設定されます。
- **NX_FTP_USERNAME_SIZE**: クライアントによって提供される *username* に許容されるバイト数を指定します。 既定値は 20 に設定されます *。*
- **NX_FTP_PASSWORD_SIZE**: クライアントによって提供される *password* に許容されるバイト数を指定します。 既定値は 20 に設定されます。
