---
title: 第 2 章 - Azure RTOS NetX Duo SNTP クライアントのインストールと使用
description: この章では、NetX Duo SNTP クライアントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cd917e7e70ce21dbff6c8081c2ff115c0acad8a8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810565"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-sntp-client"></a>第 2 章 - Azure RTOS NetX Duo SNTP クライアントのインストールと使用

この章では、Azure RTOS NetX Duo SNTP クライアントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品ディストリビューション

NetX Duo 用 SNTP は [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) で入手できます。 このパッケージにはソース ファイル 2 つと、このドキュメントを含む PDF ファイル 1 つが含まれています。次のとおりです。

- **nxd_sntp_client.c** SNTP クライアント C ソース ファイル  
- **nxd_sntp_client.h** SNTP クライアント ヘッダー ファイル  
- **demo_netxduo_sntp_client.c** デモンストレーション SNTP クライアント アプリケーション  
- **nxd_sntp_client.pdf** NetX Duo SNTP クライアント ユーザー ガイド  

## <a name="netx-duo-sntp-client-installation"></a>NetX Duo SNTP クライアントのインストール

NetX Duo 用 SNTP を使用するには、前述のディストリビューション全体を、NetX Duo がインストールされているのと同じディレクトリにコピーする必要があります。 たとえば、NetX Duo が " *\threadx\arm7\green*" ディレクトリにインストールされている場合は、NetX Duo SNTP クライアント ファイル *nxd_sntp_client.c* と *nxd_sntp_client.h* (NetX では *nx_sntp_client.c* と *nx_sntp_client.h*) をこのディレクトリにコピーする必要があります。

## <a name="using-netx-duo-sntp-client"></a>NetX Duo SNTP クライアントの使用

NetX Duo SNTP クライアントは簡単に使用できます。 基本的に言って、アプリケーション コードでは、*tx_api.h、fx_api.h*、*nx_api.h* をインクルードして ThreadX と NetX Duo をそれぞれ使用できるようにした後、*nxd_sntp_client.h* をインクルードする必要があります。 *nxd_sntp_client.h* をインクルードすると、このガイドで後述する SNTP 関数呼び出しを、そのアプリケーション コードで実行できるようになります。 アプリケーションでは、ビルド プロセスで *nxd_sntp_client.c* をインクルードする必要もあります。 これらのファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、そのオブジェクト形式をアプリケーションのファイルと一緒にリンクする必要があります。 NetX Duo SNTP クライアントを使用するために必要なことはこれだけです。

> [!NOTE]
> NetX Duo SNTP クライアントは NetX Duo UDP サービスを利用するため、SNTP サービスを使用する前に、*nx_udp_enable* 呼び出しで UDP を有効にする必要があります。

## <a name="small-example-system"></a>小規模のシステム例

NetX Duo SNTP の使用方法の例を以下に示します。 この例は、お使いのシステムでそのままの状態で動作することは保証されて **いない** ことにご注意ください。 お使いの特定のシステムおよびハードウェアに合わせて調整することが必要な場合があります。 たとえば、NetX ram ドライバーを実際のドライバー関数に置き換える必要があります。 この例は、あくまでもデモンストレーションを目的としたものです。

この例では、SNTP ヘッダー ファイル *nxd_sntp_client.h* がインクルードされています。 SNTP クライアントは、"*tx_application_define*" で作成されます。 Kiss of Death およびうるう秒ハンドラー関数は、SNTP クライアントを作成する場合は省略可能であることにご注意ください。

このデモは、IPv6 または IPv4 で使用できます。 IPv6 経由で SNTP クライアントを実行するには、USE_IPV6 を定義します。 IPv6 は NetX Duo でも有効にする必要があります。 この SNTP クライアント ホストは、NetX Duo の IPv6 アドレス検証と ICMPv6 および IPv6 サービス用に設定されています。 NetX Duo での IPv6 サポートの詳細については、『NetX Duo ユーザー ガイド』を参照してください。

次に、ユニキャスト モードまたはブロードキャスト モードで、SNTP クライアントを初期化する必要があります。

最初、SNTP クライアントはその独自のデータ構造にサーバー時刻の更新を書き込みます。 これは、デバイスのローカル時刻と同じではありません。 デバイスのローカル時刻は、SNTP クライアント スレッドを開始する前に、SNTP クライアントのベースライン時刻として設定できます。 これは、SNTP クライアントが、最初のサーバー更新を NX_SNTP_CLIENT_MAX_ADJUSTMENT (既定値は 180 ミリ秒) と比較するように構成されている (NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP が NX_FALSE に設定されている) 場合に役立ちます。 それ以外の場合、SNTP クライアントは、サーバーから最初の更新を取得したときに、初期ローカル時刻を直接設定します。

ベースライン時刻は、*nx_sntp_client_set_local_time* サービスを使用して SNTP クライアントに適用されます。

SNTP クライアントがユニキャスト モードとブロードキャスト モードでそれぞれ開始されます。 アプリケーションは、一定の間隔 (ユニキャスト ポーリング間隔より若干短い) で、*nx_sntp_client_set_local_time* を使用して "リアルタイム クロック" (現在の時刻の秒とミリ秒を単純にインクリメントすることによってシミュレートしたもの) から SNTP クライアントのローカル時刻を更新します。 間隔が経過するたびに、アプリケーションは、SNTP サーバーからの更新を定期的にチェックします。 *nx_sntp_client_receiving _updates* サービスは、SNTP クライアントが有効な更新を現在受信していることを確認します。 受信している場合、*nx_sntp_client_get_local_time_extended* サービスを使用して、最新の更新時刻が取得されます。

SNTP クライアントが有効な更新をもはや受信していないことが検出された場合など、いつでも *nx_sntp_client_stop* サービスを使用して、SNTP クライアントを停止できます。 クライアントを再起動するには、アプリケーションでユニキャストまたはブロードキャストの初期化サービスを呼び出してから、ユニキャストまたはブロードキャストの実行サービスを呼び出す必要があります。 SNTP クライアントのスレッド タスクが停止している間、その SNTP クライアントでは、必要に応じて SNTP サーバーとモード (ユニキャストまたはブロードキャスト) を切り替えることができます。たとえば、前の SNTP サーバーがダウンしているように思われる場合などです。

```c
/* 
   This is a small demo of the NetX SNTP Client on the high-performance NetX
   TCP/IP stack. This demo relies on Thread, NetX and NetX SNTP Client API to
   execute the Simple Network Time Protocol in unicast and broadcast modes.  
 */

#include <stdio.h>
#include "nx_api.h"
#include "nx_ip.h"
#include "nxd_sntp_client.h"
                
/* Define SNTP packet size. */
#define NX_SNTP_CLIENT_PACKET_SIZE      (NX_UDP_PACKET + 100)

/* Define SNTP packet pool size. */
#define NX_SNTP_CLIENT_PACKET_POOL_SIZE      (4 * (NX_SNTP_CLIENT_PACKET_SIZE + 
                                                            sizeof(NX_PACKET)))

/* Define how often the demo checks for SNTP updates. */
#define DEMO_PERIODIC_CHECK_INTERVAL      (1 * NX_IP_PERIODIC_RATE) 

/* Define how often we check on SNTP server status. 
   We expect updates from the SNTP server about every hour using 
   the SNTP Client defaults. For testing
   make this (much) shorter. */
#define CHECK_SNTP_UPDATES_TIMEOUT       (180 * NX_IP_PERIODIC_RATE) 

/* Set up generic network driver for demo program. */
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Application defined services of the NetX SNTP Client. */

UINT leap_second_handler(NX_SNTP_CLIENT *client_ptr, 
                                UINT leap_indicator);
UINT kiss_of_death_handler(NX_SNTP_CLIENT *client_ptr, 
                                        UINT KOD_code);
VOID time_update_callback(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                       NX_SNTP_TIME *local_time);


/* Set up client thread and network resources. */

NX_PACKET_POOL      client_packet_pool;
NX_IP               client_ip;
TX_THREAD           demo_client_thread;
NX_SNTP_CLIENT      demo_sntp_client;
TX_EVENT_FLAGS_GROUP sntp_flags;

#define DEMO_SNTP_UPDATE_EVENT  1

/* Configure the SNTP Client to use IPv6. If not enabled, the 
   Client will use IPv4.  Note: IPv6 must be enabled in NetX Duo
   for the Client to communicate over IPv6.    */
#ifdef FEATURE_NX_IPV6
/* #define USE_IPV6 */
#endif /* FEATURE_NX_IPV6 */


/* Configure the SNTP Client to use unicast SNTP. */
#define USE_UNICAST


#define CLIENT_IP_ADDRESS       IP_ADDRESS(192,2,2,66)
#define SERVER_IP_ADDRESS       IP_ADDRESS(192,2,2,92)
#define SERVER_IP_ADDRESS_2     SERVER_IP_ADDRESS

/* Set up the SNTP network and address index; */
UINT     iface_index =0;
UINT     prefix = 64;   
UINT     address_index;

/* Set up client thread entry point. */
void    demo_client_thread_entry(ULONG info);

/* Define main entry point.  */
int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
    return 0;
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

UINT     status;
UCHAR    *free_memory_pointer;


    free_memory_pointer = (UCHAR *)first_unused_memory;

    /* Create client packet pool. */
    status =  nx_packet_pool_create(&client_packet_pool, 
                                "SNTP Client Packet Pool",
                                NX_SNTP_CLIENT_PACKET_SIZE, 
                                free_memory_pointer, 
                                NX_SNTP_CLIENT_PACKET_POOL_SIZE);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        return;
    }

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer =  free_memory_pointer + NX_SNTP_CLIENT_PACKET_POOL_SIZE;

    /* Create Client IP instances */
    status = nx_ip_create(&client_ip, "SNTP IP Instance", 
                                        CLIENT_IP_ADDRESS, 
                                        0xFFFFFF00UL, 
                                        &client_packet_pool, 
                                       _nx_ram_network_driver, 
                                       free_memory_pointer, 2048, 1);
    
    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }

    free_memory_pointer =  free_memory_pointer + 2048;

#ifndef NX_DISABLE_IPV4
    /* Enable ARP and supply ARP cache memory. */
    status =  nx_arp_enable(&client_ip, (void **) free_memory_pointer, 2048);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }
#endif /* NX_DISABLE_IPV4  */

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;
    
    /* Enable UDP for client. */
    status =  nx_udp_enable(&client_ip);
    
    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }

#ifndef NX_DISABLE_IPV4
    status = nx_icmp_enable(&client_ip);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }
#endif /* NX_DISABLE_IPV4  */

    /* Create the client thread */
    status = tx_thread_create(&demo_client_thread, "SNTP Client Thread", 
                                                demo_client_thread_entry, 
                                              (ULONG)(&demo_sntp_client), 
                                                free_memory_pointer, 2048, 
                                                  4, 4, TX_NO_TIME_SLICE, 
                                                        TX_DONT_START);

    /* Check for errors */
    if (status != TX_SUCCESS)
    {

        return;
    }

    /* Create the event flags. */
    status = tx_event_flags_create(&sntp_flags, "SNTP event flags");

    /* Check for errors */
    if (status != TX_SUCCESS)
    {

        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* set the SNTP network interface to the primary interface. */
    iface_index = 0;

    /* Create the SNTP Client to run in broadcast mode.. */
status =  nx_sntp_client_create(&demo_sntp_client, &client_ip,
                           iface_index, &client_packet_pool,  
                               leap_second_handler, 
                               kiss_of_death_handler, 
                               NULL /* no random_number_generator callback */);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        /* Bail out!*/
        return;
    }

    tx_thread_resume(&demo_client_thread);

    return;
}

/* Define size of buffer to display client's local time. */
#define BUFSIZE 50

/* Define the client thread.  */
void    demo_client_thread_entry(ULONG info)
{

UINT   status;
UINT   spin;
UINT   server_status;
ULONG  base_seconds;
ULONG  base_fraction;
ULONG  seconds, milliseconds, microseconds, fraction;
UINT   wait = 0;
UINT   error_counter = 0;
ULONG  events = 0;
#ifdef USE_IPV6
NXD_ADDRESS sntp_server_address;
NXD_ADDRESS client_ip_address;
#endif

    NX_PARAMETER_NOT_USED(info);

    /* Give other threads (IP instance) initialize first. */
    tx_thread_sleep(NX_IP_PERIODIC_RATE); 

#ifdef USE_IPV6
    /* Set up IPv6 services. */
    status = nxd_ipv6_enable(&client_ip);

    status += nxd_icmp_enable(&client_ip);

    if (status  != NX_SUCCESS)
        return;

    client_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Set the IPv6 server address. */
    sntp_server_address.nxd_ip_address.v6[0] = 0x20010db8;  
    sntp_server_address.nxd_ip_address.v6[1] = 0x0000f101;
    sntp_server_address.nxd_ip_address.v6[2] = 0x0;
    sntp_server_address.nxd_ip_address.v6[3] = 0x00000106;
    sntp_server_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Establish the link local address for the host. The RAM driver creates
       a virtual MAC address. */
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, NULL);

    /* Check for link local address set error.  */
    if (status != NX_SUCCESS) 
    {
        return;
    }

     /* Set the host global IP address. We are assuming a 64 
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, 
                                        &client_ip_address, 
                                    prefix, &address_index);

    /* Check for global address set error.  */
    if (status != NX_SUCCESS) 
    {
        return;
    }

    /* Wait while NetX Duo validates the global and link local addresses. */
    tx_thread_sleep(5 * NX_IP_PERIODIC_RATE);

#endif

    /* Setup time update callback function. */
    nx_sntp_client_set_time_update_notify(&demo_sntp_client, 
                                        time_update_callback);

    /* Set up client time updates depending on mode. */
#ifdef USE_UNICAST

    /* Initialize the Client for unicast mode to 
       poll the SNTP server once an hour. */
#ifdef USE_IPV6
/* Use the duo service to set up the Client and set the IPv6 SNTP server.
   Note: this can take either an IPv4 or IPv6 address. */
    status = nxd_sntp_client_initialize_unicast(&demo_sntp_client, 
                                            &sntp_server_address);
#else
    /* Use the IPv4 service to set up the Client and set the IPv4 SNTP server. */
    status = nx_sntp_client_initialize_unicast(&demo_sntp_client, 
                                                SERVER_IP_ADDRESS);
#endif  /* USE_IPV6 */


#else   /* Broadcast mode */

/* Initialize the Client for broadcast mode, no roundtrip calculation
   required and a broadcast SNTP service. */
#ifdef USE_IPV6
    /* Use the duo service to initialize the Client 
       and set IPv6 SNTP all hosts multicast address. 
       (Note: This can take either an IPv4 or IPv6 address.)*/
    status = nxd_sntp_client_initialize_broadcast(&demo_sntp_client, 
                                                &sntp_server_address, 
                                                            NX_NULL);
#else

    /* Use the IPv4 service to initialize the Client and set 
       IPv4 SNTP broadcast address. */
    status = nx_sntp_client_initialize_broadcast(&demo_sntp_client,  
                                                NX_NULL, 
                                                SERVER_IP_ADDRESS);
#endif  /* USE_IPV6 */
#endif  /* USE_UNICAST */

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Set the base time which is approximately the number of seconds since
       the turn of the last century. If this is not available in SNTP format,
       the nx_sntp_client_utility_add_msecs_to_ntp_time service can convert
       milliseconds to fraction.  For how to compute NTP seconds from real
   time, read the NetX SNTP User Guide. Otherwise set the base time to 
   zero and set NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP to NX_TRUE for
       the SNTP CLient to accept the first time update without applying a
       minimum or maximum adjustment parameters
      (NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT and
       NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT). */

    base_seconds =  0xd2c96b90;  /* Jan 24, 2012 UTC */
    base_fraction = 0xa132db1e;

    /* Apply to the SNTP Client local time.  */
status = nx_sntp_client_set_local_time(&demo_sntp_client, base_seconds,
                                base_fraction);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Run whichever service the client is configured for. */
#ifdef USE_UNICAST
    status = nx_sntp_client_run_unicast(&demo_sntp_client);
#else
    status = nx_sntp_client_run_broadcast(&demo_sntp_client);
#endif  /* USE_UNICAST */

    if (status != NX_SUCCESS)
    {
        return;
    }

    spin = NX_TRUE;

    /* Now check periodically for time changes. */
    while(spin)
    {
        /* Wait for a server update event. */
        tx_event_flags_get(&sntp_flags, DEMO_SNTP_UPDATE_EVENT, 
                                          TX_OR_CLEAR, &events, 
                                 DEMO_PERIODIC_CHECK_INTERVAL);

        if (events == DEMO_SNTP_UPDATE_EVENT)
        {

            /* Check for valid SNTP server status. */
            status = nx_sntp_client_receiving_updates(&demo_sntp_client,
                                               &server_status);

            if ((status != NX_SUCCESS) || (server_status == NX_FALSE))
            {

                /* We do not have a valid update. Skip processing any time
                   data. If this happens repeatedly, consider stopping the
                   SNTP Client thread, picking another SNTP server and
                   resuming the SNTP Client thread task (more details about
                   that in the comments at the end of this function).
                 
                   If SNTP Client configurable parameters are too restrictive,
                   such as Max Adjustment, that may also cause valid server
                   updates to be rejected. Configurable parameters, however,
                   cannot be changed at run time.
                 */
                 
                continue;
            }

            /* We have a valid update.  Get the SNTP Client time.  */
            status = nx_sntp_client_get_local_time_extended(&demo_sntp_client, 
                                                    &seconds, &fraction,  
                                                    NX_NULL, 0); 

            /* Convert fraction to microseconds. */
            nx_sntp_client_utility_fraction_to_usecs(fraction, &microseconds);

            milliseconds = ((microseconds + 500) / 1000);

            if (status != NX_SUCCESS)
            {
                printf("Internal error with getting local time 0x%x\n", 
                       status);
                error_counter++;
            }
            else
            {
                printf("\nSNTP updated\n");
                printf("Time: %lu.%03lu sec.\r\n", seconds, milliseconds);
            }

            /* Clear all events in our event flag. */
            events = 0;
        }
        else
        {

            /* No SNTP update event.             
               In the meantime, if we have an RTC we might want to check
               its notion of time. In this demo, we simulate the passage of 
               time on our 'RTC' really just the CPU counter, assuming that 
               seconds and milliseconds have previously been set to a base 
              (starting) time (as was the SNTP Client before running it) 
             */

            seconds += 1;
            milliseconds += 1;

            /* Update our timer. */
            wait += DEMO_PERIODIC_CHECK_INTERVAL;

            /* Check if it is time to display the local 'RTC' time. */
            if (wait >= CHECK_SNTP_UPDATES_TIMEOUT)
            {
                /* It is. Reset the timeout and print local time. */
                wait = 0;

                printf("Time: %lu.%03lu sec.\r\n", seconds, milliseconds);
            }           
        }
    }

/* We can stop the SNTP service if for example we think the SNTP server 
   has stopped sending updates.
     
       To restart the SNTP Client, simply call the
       nx_sntp_client_initialize_unicast or
       nx_sntp_client_initialize_broadcast using another SNTP server IP
       address as input, and resume the SNTP Client by calling
       nx_sntp_client_run_unicast or
       nx_sntp_client_run_braodcast. */
    status = nx_sntp_client_stop(&demo_sntp_client);

    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    /* When done with the SNTP Client, we delete it */
    status = nx_sntp_client_delete(&demo_sntp_client);

    return;
}


/* This application defined handler for handling an 
   impending leap second is not required by 
   the SNTP Client. The default handler below only logs the
   event for every time stamp received with the 
   leap indicator set.  */

UINT leap_second_handler(NX_SNTP_CLIENT *client_ptr, 
                                UINT leap_indicator)
{
    NX_PARAMETER_NOT_USED(client_ptr);
    NX_PARAMETER_NOT_USED(leap_indicator);

    /* Handle the leap second handler... */

    return NX_SUCCESS;
}

/* This application defined handler for handling 
   a Kiss of Death packet is not required by the SNTP Client. 
   A KOD handler should determine if the Client task should continue vs. 
   abort sending/receiving time data from its current time server, 
   and if aborting if it should remove
   the server from its active server list. 

   Note that the KOD list of codes is subject to change. The list
   below is current at the time of this software release. */

UINT kiss_of_death_handler(NX_SNTP_CLIENT *client_ptr, UINT KOD_code)
{

UINT    remove_server_from_list = NX_FALSE;
UINT    status = NX_SUCCESS;

    NX_PARAMETER_NOT_USED(client_ptr);

    /* Handle kiss of death by code group. */
    switch (KOD_code)
    {

        case NX_SNTP_KOD_RATE:
        case NX_SNTP_KOD_NOT_INIT:
        case NX_SNTP_KOD_STEP:

            /* Find another server while this one 
               is temporarily out of service.  */
            status =  NX_SNTP_KOD_SERVER_NOT_AVAILABLE;

        break;

        case NX_SNTP_KOD_AUTH_FAIL:
        case NX_SNTP_KOD_NO_KEY:
        case NX_SNTP_KOD_CRYP_FAIL:

            /* These indicate the server will not 
               service client with time updates
               without successful authentication. */


            remove_server_from_list =  NX_TRUE;

        break;


        default:

            /* All other codes. Remove server 
               before resuming time updates. */

            remove_server_from_list =  NX_TRUE;
        break;
    }

    /* Removing the server from the active server list? */
    if (remove_server_from_list)
    {

        /* Let the caller know it has to bail on 
           this server before resuming service. */
        status = NX_SNTP_KOD_REMOVE_SERVER;
    }

    return status;
}


/* This application defined handler for notifying SNTP time update event.  */

VOID time_update_callback(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                       NX_SNTP_TIME *local_time)
{
    tx_event_flags_set(&sntp_flags, DEMO_SNTP_UPDATE_EVENT, TX_OR);
}

```

図 1 NetX Duo で SNTP クライアントを使用する例

## <a name="configuration-options"></a>構成オプション

NetX Duo SNTP クライアントを定義するための構成オプションがいくつか用意されています。 次の一覧で、それぞれについて詳しく説明します。  
  

**NX_SNTP_CLIENT_THREAD_STACK_SIZE**  
このオプションでは、クライアント スレッド スタックのサイズを設定します。 既定の NetX Duo SNTP クライアント サイズは、2048 です。

**NX_SNTP_CLIENT_THREAD_TIME_SLICE**  
このオプションでは、クライアント スレッドの実行に許可されるスケジューラのタイム スライスを設定します。 既定の NetX Duo SNTP クライアント サイズは、TX_NO_TIME_SLICE です。

**NX_SNTP_CLIENT_ THREAD_PRIORITY**  
このオプションでは、クライアント スレッドの優先順位を設定します。 NetX Duo SNTP クライアントの既定値は、2 です。

**NX_SNTP_CLIENT_PREEMPTION_THRESHOLD**  
このオプションでは、クライアント スレッドがプリエンプションを許可する優先順位のレベルを設定します。 既定の NetX Duo SNTP クライアント値は、`NX_SNTP_CLIENT_ THREAD_PRIORITY` に設定されています。

**NX_SNTP_CLIENT_UDP_SOCKET_NAME**  
このオプションでは、UDP ソケット名を設定します。 NetX Duo SNTP クライアントの UDP ソケット名の既定値は、"SNTP クライアント ソケット" です。

**NX_SNTP_CLIENT_UDP_PORT**  
これによって、クライアント ソケットのバインド先ポートを設定します。 既定の NetX Duo SNTP クライアント ポートは、123 です。

**NX_SNTP_SERVER_UDP_PORT**  
これは、クライアントから SNTP サーバーに SNTP メッセージを送信するポートです。 既定の NetX SNTP サーバー ポートは、123 です。

**NX_SNTP_CLIENT_TIME_TO_LIVE**  
クライアント パケットが通過できるルーターの数を指定します。この数を超えるとパケットは破棄されます。 既定の NetX Duo SNTP クライアントは、0x80 に設定されています *。*

**NX_SNTP_CLIENT_MAX_QUEUE_DEPTH**  
NetX Duo SNTP クライアント ソケットでキューに入れることができる UDP パケット (データグラム) の最大数。 これを超えるパケットを受信した場合、最も古いパケットが解放されます。 既定の NetX Duo SNTP クライアントは、5 に設定されています。

**NX_SNTP_CLIENT_PACKET_TIMEOUT**  
NetX Duo パケット割り当てのタイムアウト。 既定の NetX Duo SNTP クライアント パケット タイムアウトは、1 秒です。

**NX_SNTP_CLIENT_NTP_VERSION**  
クライアントによって使用される SNTP バージョン。NetX Duo SNTP クライアント API は、バージョン 4 に基づいていました。 既定値は、3 です。

**NX_SNTP_CLIENT_MIN_NTP_VERSION**  
クライアントが連携できる最も古い SNTP バージョン。 NetX Duo SNTP クライアントの既定値は、バージョン 3 です。

**NX_SNTP_CLIENT_MIN_SERVER_STRATUM**  
クライアントが受け入れる最下位レベル (数値が最も高い階層レベル) の SNTP サーバー階層。 NetX Duo SNTP クライアントの既定値は、2 です。

**NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT**  
クライアントでローカル クロック時間に対して行われる最小の時間調整 (ミリ秒単位)。 この値未満の時間調整は無視されます。 NetX Duo SNTP クライアントの既定値は、10 です。

**NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT**  
クライアントでローカル クロック時間に対して行われる最大の時間調整 (ミリ秒単位)。 この数値を超える時間調整の場合、ローカル クロックの調整は最大の時間調整に制限されます。 NetX Duo SNTP クライアントの既定値は、180000 (3 分) です。

**NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP**  
これを使用すると、クライアントがタイム サーバーから最初の更新を受信するとき、最大の時間調整が免除されます。 それ以降は、最大の時間調整が適用されます。 その目的は、クライアントができるだけ早くサーバー クロックと同期されるようにすることです。 NetX Duo SNTP クライアントの既定値は、NX_TRUE です。

**NX_SNTP_CLIENT_MAX_TIME_LAPSE**  
SNTP クライアントが有効な時間更新を受信しないで経過することが許可される最大時間 (秒)。 SNTP クライアントは動作し続けますが、SNTP サーバーの状態は NX_FALSE に設定されます。 既定値は、7200 です。


**NX_SNTP_UPDATE_TIMEOUT_INTERVAL**  
最後の有効な更新を受信してからの残り SNTP クライアント時間が SNTP クライアント タイマーによって更新される、および次に SNTP 更新要求を送信するまでの残りポーリング間隔時間がユニキャスト クライアントによって更新される間隔 (秒数)。 既定値は 1 です。

**NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL**  
クライアントがその SNTP サーバーにユニキャスト要求を送信するポーリング開始間隔 (秒)。 NetX Duo SNTP クライアントの既定値は、3600 です。

**NX_SNTP_CLIENT_EXP_BACKOFF_RATE**  
現在のクライアント ユニキャスト ポーリング間隔を増やす際の係数。 クライアントがサーバー時刻の更新を受信できない場合、または時刻更新サービスが一時的に使用できなくなっている (まだ同期されていないなど) ことをサーバーから受信した場合は、現在のポーリング間隔がこの指定値分だけ増えます。ただし、最大でも NX_SNTP_CLIENT_MAX_TIME_LAPSE までで、これを超すことはありません。 既定値は 2 です。

**NX_SNTP_CLIENT_RTT_REQUIRED**  
このオプションが有効になっている場合、サーバー更新をローカル クロックに適用するときに、SNTP クライアントは SNTP メッセージのラウンド トリップ時間を計算することが必要になります。 既定値は、NX_FALSE (無効) です。

**NX_SNTP_CLIENT_MAX_ROOT_DISPERSION**  
サーバー クロックの最大分散 (マイクロ秒)。これは、クライアントが受け入れるサーバー クロックの精度のメジャーです。 この要件を無効にするには、ルートの最大分散を 0x0 に設定します。 NetX Duo SNTP クライアントの既定値は、50000 に設定されています。

**NX_SNTP_CLIENT_INVALID_UPDATE_LIMIT**  
ブロードキャストまたはユニキャスト モードでクライアント サーバーから連続して受信できる無効な更新の数の制限。 この制限に達すると、クライアントでは現在の SNTP サーバーの状態を無効 (NX_FALSE) に設定しますが、サーバーからの更新の受信を試行し続けます。 NetX Duo SNTP クライアントの既定値は、3 です。

**NX_SNTP_CLIENT_RANDOMIZE_ON_STARTUP**  
これにより、ユニキャスト モードの SNTP クライアントで、ランダムな待機期間の後に、現在の SNTP サーバーに最初の SNTP 要求を送信するかどうかが決定されます。 これは、多数の SNTP クライアントが同時に起動する場合に、SNTP サーバー上のトラフィックの輻輳を制限するために使用します。 既定値は、NX_FALSE です。

**NX_SNTP_CLIENT_SLEEP_INTERVAL**  
SNTP クライアントのタスクがスリープ状態になる時間間隔。 これを使用すると、アプリケーション API 呼び出しを SNTP クライアントで実行できるようになります。 既定値は、1 タイマー ティックです。

**NX_SNTP_CURRENT_YEAR**  
日付を "年/月/日" の形式で表示するには、この値を現在の年と同じかそれより小さい値に設定します (NTP 時刻の評価の場合のように同じ年に設定する必要はありません)。 既定値は、2015 です。

**NTP_SECONDS_AT_01011999**  
これは、マスター NTP クロックにおける最初の NTP エポックからの秒数です。 これは、0xBA368E80 として定義されています。 NTP 秒の日付と時刻での表示を無効にするには、ゼロに設定します。
