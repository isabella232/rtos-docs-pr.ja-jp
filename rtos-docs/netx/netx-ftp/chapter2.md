---
title: 第 2 章 - Azure RTOS NetX FTP のインストールと使用
description: この章では、Azure RTOS NetX FTP コンポーネントのインストール、設定、使用に関連したさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9da2761ed9483a920ab6f735b8a3a6bd82936c867ece8047b622788d5fb99804
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799491"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-ftp"></a>第 2 章 - Azure RTOS NetX FTP のインストールと使用

この章では、Azure RTOS NetX FTP コンポーネントのインストール、設定、使用に関連したさまざまな問題について説明します。

## <a name="product-distribution"></a>製品の配布

Azure RTOS NetX は、[https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/]) のパブリック ソース コード リポジトリから入手できます。 このパッケージにはソース ファイル 2 つと、このドキュメントを含む PDF ファイル 1 つが含まれています。次のとおりです。

- **nx_ftp.h**: NetX 用 FTP のヘッダー ファイル
- **nx_ftp_client.c**: NetX 用 FTP クライアントの C ソース ファイル
- **nx_ftp_server.c**: NetX 用 FTP サーバーの C ソース ファイル
- **filex_stub.h**: FileX が存在しない場合のスタブ ファイル
- **nx_ftp.pdf**: NetX 用 FTP の PDF の説明
- **demo_netx_ftp.c**: FTP デモンストレーション システム

## <a name="ftp-installation"></a>FTP のインストール

NetX 用 FTP を使用するには、前述のディストリビューション全体を、NetX がインストールされているのと同じディレクトリにコピーする必要があります。 たとえば、NetX が " *\threadx\arm7\green*" ディレクトリにインストールされている場合は、*nx_ftp.h*、*nx_ftp_client.c*、および *nx_ftp_server.c* ファイルをこのディレクトリにコピーする必要があります。

## <a name="using-ftp"></a>FTP を使用する

NetX 用 FTP は簡単に使用できます。 ThreadX、FileX、および NetX を使用するためには、基本的に、アプリケーションのコードでそれぞれ *tx_api.h、fx_api.h、* および *nx_api.h* をインクルードしてから *nx_ftp.h* をインクルードする必要があります。 *nx_ftp.h* をインクルードすると、アプリケーション コードで、このガイドで後述する FTP 関数呼び出しを行うことができるようになります。 また、アプリケーションでは、ビルド プロセスに *nx_ftp_client.c* と *nx_ftp_server.c* もインクルードする必要があります。 これらのファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、そのオブジェクト形式をアプリケーションのファイルと一緒にリンクする必要があります。 NetX FTP を使用するために必要なことはこれだけです。

> [!NOTE]
> FTP では NetX TCP サービスを利用するため、FTP を使用する前に、*nx_tcp_enable* を呼び出して TCP を有効にする必要があります。

## <a name="small-example-system"></a>小規模のシステム例

NetX FTP の使用がいかに簡単であるかを示す例を、下の図 1.1 に示します。

> [!NOTE]
> これは、1 つのネットワーク インターフェイスを持つホスト デバイス用です。

この例では、FTP インクルード ファイル *nx_ftp_client.h* と *nx_ftp_server.h* が 10 行目と 11 行目で取り込まれます。 次に、FTP サーバーが "*tx_application_define*" の 134 行目に作成されます。 FTP サーバー制御ブロック "*Server*" は、31 行目でグローバル変数として既に定義されていることに注意してください。 正常に作成されると、363 行目で FTP サーバーが起動されます。 183 行目では、FTP クライアントが作成されます。 最後に、クライアントによって 229 行目でファイルが書き込まれ、318 行目でファイルが読み取られます。

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

図 1.1 NetX を使用した FTP クライアントとサーバーの例 (単一ネットワーク インターフェイス ホスト)

## <a name="configuration-options"></a>構成オプション

NetX 用 FTP を構築するための構成オプションがいくつかあります。 次の一覧で、それぞれについて詳しく説明します。  

- **NX_FTP_SERVER_PRIORITY**: FTP サーバーのスレッドの優先順位。 既定では、この値は 16 に定義され、優先順位 16 を示します。

- **NX_FTP_MAX_CLIENTS**: サーバーで一度に処理できるクライアントの最大数。 既定では、一度に 4 個のクライアントをサポートするために、この値は 4 に設定されています。

- **NX_FTP_SERVER_MIN_PACKET_PAYLOAD**: TCP、IP、ネットワーク フレーム ヘッダーと HTTP データを含む、サーバーのパケット プール ペイロードの最小サイズ (バイト単位)。 既定値は、256 (FileX でのファイル名の最大長) + 12 バイト (ファイル情報用)、および NX_PHYSICAL_TRAILER です。

- **NX_FTP_NO_FILEX**: このオプションを定義すると、FileX の依存関係のスタブが提供されます。 このオプションを定義しても、FTP クライアントは変更なしで機能します。 FTP サーバーが適切に機能するためには、変更するか、ユーザーがいくつかの FileX サービスを作成する必要があります。

- **NX_FTP_CONTROL_TOS**: FTP TCP 制御要求に必要なサービスの種類。 既定では、この値は通常の IP パケット サービスを示す NX_IP_NORMAL として定義されています。 この定義は、*nx_ftp.h* をインクルードする前にアプリケーションで設定できます。

- **NX_FTP_DATA_TOS**: FTP TCP データ要求に必要なサービスの種類。 既定では、この値は通常の IP パケット サービスを示す NX_IP_NORMAL として定義されています。 この定義は、*nx_ftp.h* をインクルードする前にアプリケーションで設定できます。

- **NX_FTP_FRAGMENT_OPTION**: FTP TCP 要求のフラグメントを有効にします。 この値の既定値は NX_DONT_FRAGMENT であり、FTP TCP のフラグメント化が無効になります。 この定義は、*nx_ftp.h* をインクルードする前にアプリケーションで設定できます。

- **NX_FTP_CONTROL_WINDOW_SIZE**: 制御ソケット ウィンドウのサイズ。 既定では、この値は 400 バイトです。 この定義は、*nx_ftp.h* をインクルードする前にアプリケーションで設定できます。

- **NX_FTP_DATA_WINDOW_SIZE**: データ ソケット ウィンドウのサイズ。 既定では、この値は 2,048 バイトです。 この定義は、*nx_ftp.h* をインクルードする前にアプリケーションで設定できます。

- **NX_FTP_TIME_TO_LIVE**: このパケットが破棄されるまでに通過できるルーターの数を指定します。 既定値は 0x80 に設定されていますが、*nx_ftp.h* をインクルードする前に再定義できます。

- **NX_FTP_SERVER_TIMEOUT**: 内部サービスが中断される ThreadX ティックの数を指定します。 既定値は 100 に設定されていますが、*nx_ftp.h* をインクルードする前に再定義できます。

- **NX_FTP_USERNAME_SIZE**: クライアントによって指定される "*ユーザー名*" に許容されるバイト数を指定します。 既定値は 20 に設定されていますが、*nx_ftp.h* をインクルードする前に再定義できます。

- **NX_FTP_PASSWORD_SIZE**: クライアントによって指定される "*パスワード*" に許容されるバイト数を指定します。 既定値は 20 に設定されていますが、*nx_ftp.h* をインクルードする前に再定義できます。

- **NX_FTP_ACTIVITY_TIMEOUT**: アクティビティがない場合にクライアント接続を維持する秒数を指定します。 既定値は 240 に設定されていますが、*nx_ftp.h* をインクルードする前に再定義できます。

- **NX_FTP_TIMEOUT_PERIOD**: サーバーによってクライアントの非アクティブ状態がチェックされる間隔を秒数で指定します。 既定値は 60 に設定されていますが、*nx_ftp.h* をインクルードする前に再定義できます。
