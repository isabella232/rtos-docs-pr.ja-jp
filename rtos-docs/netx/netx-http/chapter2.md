---
title: 第 2 章 - NetX HTTP のインストールと使用
description: この章では、NetX HTTP コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5d4913c01de5cc7c41d44bda473bbaca06dd474a26570b056bfde3cd48acc4e4
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799406"
---
# <a name="chapter-2---installation-and-use-of-netx-http"></a>第 2 章 - NetX HTTP のインストールと使用

この章では、NetX HTTP コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品ディストリビューション

Azure RTOS NetX は、[https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) のパブリック ソース コード リポジトリから入手できます。

- **nx_http_client.h**: NetX 用 HTTP クライアントのヘッダー ファイル
- **nx_http_server.h**: NetX 用 HTTP サーバーのヘッダー ファイル
- **nx_http_client.c**: NetX 用 HTTP クライアントの C ソース ファイル
- **nx_http_server.c**: NetX 用 HTTP サーバーの C ソース ファイル
- **nx_md5.c**: MD5 ダイジェスト アルゴリズム
- **filex_stub.h**: FileX が存在しない場合のスタブ ファイル
- **nx_http.pdf**: NetX 用 HTTP の説明
- **demo_netx_http.c**: NetX HTTP のデモンストレーション

## <a name="http-installation"></a>HTTP のインストール

NetX 用 HTTP を使用するには、前述のディストリビューション全体を、NetX がインストールされているのと同じディレクトリにコピーする必要があります。 たとえば、NetX が " *\threadx\arm7\green*" ディレクトリにインストールされている場合は、NetX HTTP クライアント アプリケーションの *nx_http_client.h* と *nx_http_client.c*、NetX HTTP サーバー アプリケーションの *nx_http_server.h* と *nx_http_server.c*、および *nx_md5.c* をこのディレクトリにコピーする必要があります。 デモの "ram driver" アプリケーションの場合、NetX HTTP クライアントとサーバーのファイルを同じディレクトリにコピーする必要があります。

## <a name="using-http"></a>HTTP の使用

NetX 用 HTTP は簡単に使用できます。 基本的には、ThreadX、FileX、NetX を使用するために、アプリケーション コードにそれぞれ *tx_api.h、fx_api.h*、*nx_api.h* をインクルードした後に、*nx_http_client.h* または *nx_http_server.h*、あるいはこの両方をインクルードする必要があります。 HTTP ヘッダー ファイルをインクルードすると、アプリケーション コードで、このガイドで後述する HTTP 関数呼び出しを行えるようになります。 アプリケーションでは、ビルド プロセスで *nx_http_client.c*、*nx_http_server.c*、*md5.c* もインクルードする必要があります。 これらのファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、そのオブジェクト フォームをアプリケーションのファイルと一緒にリンクする必要があります。 NetX HTTP を使用するために必要なことはこれだけです。

>[!NOTE] 
> ビルド プロセスで NX_HTTP_DIGEST_ENABLE が指定されていない場合は、アプリケーションに *md5.c* ファイルを追加する必要はありません。 同様に、HTTP クライアント機能が不要な場合は、*nx_http_client.c* ファイルを省略できます。

>[!NOTE] 
> HTTP では NetX TCP サービスを利用するため、HTTP を使用する前に、*nx_tcp_enable* を呼び出して TCP を有効にする必要があります。

## <a name="small-example-system"></a>簡単なシステムの例

NetX HTTP の使用がいかに簡単であるかを示す例を、下の図 1.1 に示します。 この例では、HTTP インクルード ファイル "*nx_http_client.h と nx_http_server.h*" が 8 行目で取り込まれます。 次に、131 行目の "*tx_application_define*" で HTTP サーバーが作成されます。

>[!NOTE] 
> HTTP サーバー制御ブロック "*Server*" は、25 行目でグローバル変数として既に定義されています。

正常に作成されると、136 行目で HTTP サーバーが起動されます。 149 行目で、HTTP クライアントが作成されます。 最後に、クライアントは、157 行目でファイルを書き込み、195 行目でファイルを読み取ります。

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

図 1.1 NetX での HTTP の使用例

## <a name="configuration-options"></a>構成オプション

NetX 用 HTTP を構築するための構成オプションがいくつかあります。 すべてのオプションとそれぞれの詳細を以下に示します。 既定値が示されていますが、"*nx_http_client.h と nx_http_server.h*" をインクルードする前に再定義できます。

- **NX_DISABLE_ERROR_CHECKING**: このオプションを定義すると、基本的な HTTP エラー チェックが削除されます。 通常は、アプリケーションがデバッグされた後に使用されます。
- **NX_HTTP_SERVER_PRIORITY**: HTTP サーバーのスレッドの優先順位。 既定では、この値は 16 番目の優先順位を示す 16 に定義されています。
- **NX_HTTP_NO_FILEX**: このオプションを定義すると、FileX の依存関係のスタブが提供されます。 このオプションを定義しても、HTTP クライアントは変更なしで機能します。 HTTP サーバーを適切に機能させるには、変更を行うか、ユーザーがいくつかの FileX サービスを作成する必要があります。
- **NX_HTTP_TYPE_OF_SERVICE**: HTTP TCP 要求に必要なサービスの種類。 既定では、この値は通常の IP パケット サービスを示す NX_IP_NORMAL に定義されています。
- **NX_HTTP_SERVER_THREAD_TIME_SLICE**: 同じ優先順位のスレッドに譲る前に、サーバー スレッドが実行を許可されるタイマー刻みの数。 既定値は 2 です。
- **NX_HTTP_FRAGMENT_OPTION**: HTTP TCP 要求のフラグメントを有効にします。 この値は既定では NX_DONT_FRAGMENT であり、HTTP TCP のフラグメント化が無効になります。
- **NX_HTTP_SERVER_WINDOW_SIZE**: サーバー ソケットのウィンドウ サイズ。 既定値は 2048 バイトです。
- **NX_HTTP_TIME_TO_LIVE**: このパケットが破棄されるまでに通過できるルーターの数を指定します。 既定値は 0x80 に設定されています。
- **NX_HTTP_SERVER_TIMEOUT**: 内部サービスが中断される ThreadX ティックの数を指定します。 既定値は 10 秒 (10 * NX_IP_PERIODIC_RATE) に設定されています。
- **NX_HTTP_SERVER_TIMEOUT_ACCEPT**: 内部 *nx_tcp_server_socket_accept* 呼び出しで内部サービスが中断される ThreadX ティックの数を指定します。 既定値は (10 * NX_IP_PERIODIC_RATE) に設定されています。
- **NX_HTTP_SERVER_TIMEOUT_DISCONNECT**: 内部 *nx_tcp_socket_disconnect* 呼び出しで内部サービスが中断される ThreadX ティックの数を指定します。 既定値は 10 秒 (10 * NX_IP_PERIODIC_RATE) に設定されています。
- **NX_HTTP_SERVER_TIMEOUT_RECEIVE**: 内部 *nx_tcp_socket_receive* 呼び出しで内部サービスが中断される ThreadX ティックの数を指定します。 既定値は 10 秒 (10 * NX_IP_PERIODIC_RATE) に設定されています。
- **NX_HTTP_SERVER_TIMEOUT_SEND**: 内部 *nx_tcp_socket_send* 呼び出しで内部サービスが中断される ThreadX ティックの数を指定します。 既定値は 10 秒 (10 * NX_IP_PERIODIC_RATE) に設定されています。
- **NX_HTTP_MAX_HEADER_FIELD**: HTTP ヘッダー フィールドの最大サイズを指定します。 既定値は 256 です。
- **NX_HTTP_MULTIPART_ENABLE**: 定義した場合、HTTP サーバーでマルチパート HTTP 要求をサポートできるようになります。
- **NX_HTTP_SERVER_MAX_PENDING**: HTTP サーバーのキューに登録できる接続の数を指定します。 既定値は 5 に設定されています。
- **NX_HTTP_MAX_RESOURCE**: クライアントで指定される "*リソース名*" に許容されるバイト数を指定します。 既定値は 40 に設定されています。
- **NX_HTTP_MAX_NAME**: クライアントで指定される "*ユーザー名*" に許容されるバイト数を指定します。 既定値は 20 に設定されています。
- **NX_HTTP_MAX_PASSWORD**: クライアントで指定される "*パスワード*" に許容されるバイト数を指定します。 既定値は 20 に設定されています。
- **NX_HTTP_SERVER_MIN_PACKET_SIZE**: サーバーの作成時に指定されたプール内のパケットの最小サイズを指定します。 最小サイズは、完全な HTTP ヘッダーを 1 つのパケットに含めることができるようにするために必要です。 既定値は 600 に設定されています。
- **NX_HTTP_CLIENT_MIN_PACKET_SIZE**: クライアントの作成時に指定されたプール内のパケットの最小サイズを指定します。 最小サイズは、完全な HTTP ヘッダーを 1 つのパケットに含めることができるようにするために必要です。 既定値は 300 に設定されています。
- **NX_HTTP_SERVER_RETRY_SECONDS**: "*サーバー ソケットの再送信タイムアウトを秒単位で設定します。* " 既定値は 2 に設定されています。
- **NX_HTTP_SERVER_RETRY_MAX**: サーバー ソケットの最大再送信回数を設定します。 既定値は 10 に設定されています。
- **NX_HTTP_SERVER_RETRY_SHIFT**: この値は、次の再送信タイムアウトを設定するために使用されます。 現在のタイムアウトにこれまでの再送信回数が乗算され、ソケット タイムアウト シフトの値でシフトされます。 既定値は 1 に設定されており、タイムアウトが 2 倍になります。
- **NX_HTTP_SERVER_TRANSMIT_QUEUE_DEPTH**: サーバー ソケット再送信キューにエンキューできるパケットの最大数を指定します。 エンキューされたパケットの数がこの数に達した場合、エンキューされた 1 つ以上のパケットが解放されるまで、これ以上パケットを送信することはできません。 既定値は 20 に設定されています。