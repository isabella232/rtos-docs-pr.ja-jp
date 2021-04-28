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
# <a name="chapter-2---installation-and-use-of-netx-duo-smtp-client"></a>チャプター 2 - NetX Duo SMTP クライアントのインストールと使用

このチャプターでは、NetX Duo SMTP クライアントのインストール、セットアップ、使用に関するさまざまな問題について説明します。

## <a name="netx-duo-smtp-client-installation"></a>NetX Duo SMTP クライアントのインストール

NetX Duo SMTP クライアントは [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) で入手できます。 パッケージには次のファイルが含まれています:

- **nxd_smtp_client.c** NetX Duo SMTP Client API の C 言語のソース ファイル
- **nxd_smtp_client.h** NetX Duo SMTP Client API の C 言語のヘッダー ファイル
- **demo_netxduo_smtp_client.c** NetX Duo SMTP クライアントのデモ
- **nxd_smtp_client.pdf** NetX Duo SMTP Client API のユーザー ガイド

NetX Duo SMTP Client API を使用するには、NetX Duo がインストールされているのと同じディレクトリに、前述の配布パッケージを丸ごとコピーすることもできます。 たとえば、NetX Duo がディレクトリ c: *\myproject* にインストールされている場合は、*nxd_smtp_client.h および nxd_smtp_client.c* ファイルをこのディレクトリにコピーします。

## <a name="using-netx-duo-smtp-client"></a>NetX Duo SMTP クライアントを使用する

NetX Duo SMTP クライアント アプリケーションを作成するには、まず ThreadX および NetX Duo のライブラリをビルドし、それをビルド プロジェクトに含める必要があります。 次に、tx *_api.h* と *nx_api.h をアプリケーションのソースコードにインクルードする必要があります*。 これで ThreadX および NetX Duo のサービスが有効になります。 SMTP クライアントのサービスを使用するには、*tx_api.h* と *nx_api.h の後で *nxd_smtp_client.c* と *nxd_smtp_client.h* もインクルードする必要があります。*

これらのファイルはアプリケーションの他のファイルと同じ方法でコンパイルし、そのオブジェクト コードをアプリケーションのファイルと共にリンクする必要があります。 NetX Duo SMTP クライアント アプリケーションの作成に必要なものはこれですべてです。

## <a name="small-example-system"></a>簡単なシステムの例

NetX Duo SMTP クライアントの使用例を下の図 1 に示します。 68 行目で nx_packet_pool_create サービスを使用して IP インスタンスのパケット プールを作成します。パケットのペイロードはとても小さいです。 これは、この IP インスタンスから送信するのが、大きなペイロードを必要としない制御パケットだけだからです。 84 行目で 作成する SMTP クライアントのパケット プールは、SMTP クライアントのメッセージをサーバーとメッセージ データに送信するのに使用します。 パケットのペイロード サイズは IP インスタンスの場合よりずっと大きいです。 118 行目で同じパケット プールを使用して IP インスタンスを作成します。 130 行目では、この IP インスタンスで TCP を有効にします。TCP は SMTP プロトコルのために必要です。

アプリケーションのスレッドでは、170 行目で *nxd_smtp_client_create* サービスを使用して SMTP クライアントを作成します。 *nxd_smtp_client_create* サービスは、IPv4 と IPv6 両方で SMTP サーバーの接続をサポートしていますが、この例では IPv4 に限定しています。 次に 184 行目で *nx_smtp_mail_send* サービスを使用して、送信するメール メッセージを SMTP クライアントに渡します。 件名とメール内容のヘッダーは、メッセージ本文とは別に作成されます。 また、メール送信要求では、構文が正しいと考えられる宛先メール アドレスを 1 つだけ指定できます。

それから 200 行目で、アプリケーションにより SMTP クライアントを終了します。 *nx_smtp_client_delete* サービスでは、ソケット接続が閉じられポートがバインド解除されていることを確認します。 それ以上使用しないパケット プールを削除するかどうかは SMTP クライアント アプリケーションに任されています。

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

**図 1. NetX Duo での SMTP クライアントの使用例**

## <a name="client-configuration-options"></a>クライアントの構成オプション

NetX Duo SMTP Client API にはいくつかの構成オプションがあります。 次のリストで、すべてのオプションを詳述します:

- **NX_SMTP_CLIENT_TCP_WINDOW_SIZE** このオプションでは、クライアントの TCP 受信ウィンドウのサイズを設定します。 これは、処理を実行するイーサネット ハードウェアの MTU より小さくし、IP ヘッダーと TCP ヘッダー用の領域を確保する必要があります。 NetX Duo SMTP クライアントの既定の TCP ウィンドウ サイズは 1460 です。
- **NX_SMTP_CLIENT_PACKET_TIMEOUT** このオプションでは、NetX のパケットの割り当てのタイムアウト時間を設定します。 NetX Duo SMTP クライアントのパケットの既定のタイムアウト時間は 2 秒です。
- **NX_SMTP_CLIENT_CONNECTION_TIMEOUT** このオプションでは、クライアントの TCP ソケット接続のタイムアウト時間を設定します。 NetX Duo SMTP クライアントの接続の既定のタイムアウト時間は 10 秒です。
- **NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** このオプションでは、クライアントの TCP ソケットの切断タイムアウト時間を設定します。 NetX Duo SMTP クライアントの既定の切断タイムアウト時間は 5 秒 * です。 SMTP クライアントで接続の切断などの内部エラーが発生すると、直ちにタイムアウトして接続を終了する場合があります。
- **NX_SMTP_GREETING_TIMEOUT** このオプションでは、グリーティング メッセージに対するサーバーの応答をクライアントで受信するのを待つ際のタイムアウト時間を設定します。 NetX Duo SMTP クライアントの既定値は 10 秒です。
- **NX_SMTP_ENVELOPE_TIMEOUT** このオプションでは、クライアント コマンドに対するサーバーの応答をクライアントで受信するのを待つ際のタイムアウト時間を設定します。 NetX Duo SMTP クライアントの既定値は 10 秒です。
- **NX_SMTP_MESSAGE_TIMEOUT** このオプションでは、受信したメール メッセージ データに対するサーバーの応答をクライアントで受信するのを待つ際のタイムアウト時間を設定します。 NetX Duo SMTP クライアントの既定値は 30 秒です。
- **NX_SMTP_CLIENT_SEND_TIMEOUT** このオプションでは、サーバーに対して SMTP 認証を行うときにユーザー パスワードを保存するバッファーの待機オプションを指定します。 既定値は 20 バイトです。
- **NX_SMTP_SERVER_CHALLENGE_MAX_STRING** このオプションでは、SMTP 認証時にサーバーのチャレンジを抽出するバッファーのサイズを指定します。 既定値は 200 バイトです。 LOGIN 認証と PLAIN 認証では、SMTP クライントで使用するバッファーは恐らくこれより小さくても済みます。
- **NX_SMTP_CLIENT_MAX_PASSWORD** このオプションでは、サーバーに対して SMTP 認証を行うときにユーザー パスワードを保存するバッファーのサイズを指定します。 既定値は 20 バイトです。 
- **NX_SMTP_CLIENT_MAX_USERNAME** このオプションでは、サーバーに対して SMTP 認証を行うときにホストのユーザー名を保存するバッファーのサイズを指定します。 既定値は 40 バイトです。 
