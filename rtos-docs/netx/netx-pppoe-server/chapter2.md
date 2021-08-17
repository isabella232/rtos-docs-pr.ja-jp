---
title: 第 2 章 - Azure RTOS NetX PPPoE サーバーのインストールと使用
description: この章では、Azure RTOS NetX PPPoE サーバー コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5e93d783299448301c4e79a324ccec01473dbcce3fb96d25d7be352384d4fa53
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796329"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pppoe-server"></a>第 2 章 - Azure RTOS NetX PPPoE サーバーのインストールと使用

この章では、Azure RTOS NetX PPPoE サーバー コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品ディストリビューション

NetX 用 PPPoE サーバーは、[https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) で入手できます。 このパッケージには、次のように、2 つのソース ファイルと、このドキュメントを含む PDF ファイルが含まれています。

- **nx_pppoe_server.h**: NetX 用 PPPoE サーバーのヘッダー ファイル
- **nx_pppoe_server.c**: NetX 用 PPPoE サーバーの C ソース ファイル
- **nx_pppoe_server.pdf**: NetX 用 PPPoE サーバーの PDF 説明書
- **demo_netx_pppoe_server.c**: NetX PPPoE サーバーのデモンストレーション

## <a name="pppoe-server-installation"></a>PPPoE サーバーのインストール

NetX 用 PPPoE サーバーを使用するには、前述のディストリビューション全体を、NetX がインストールされているのと同じディレクトリにコピーする必要があります。 たとえば、NetX が " *\threadx\arm7\green*" ディレクトリにインストールされている場合は、*nx_pppoe_server.h* および *nx_pppoe_server.c* ファイルをこのディレクトリにコピーする必要があります。

## <a name="using-pppoe-server"></a>PPPoE サーバーの使用

NetX 用 PPPoE サーバーは簡単に使用できます。 基本的には、ThreadX と NetX を使用するために、アプリケーション コードにそれぞれ *tx_api.h* と *nx_api.h* をインクルードした後に、*nx_pppoe_server.h* をインクルードする必要があります。 *nx_pppoe_server.h* をインクルードすると、アプリケーション コードで、このガイドで後述する PPPoE サーバー関数呼び出しを行えるようになります。 アプリケーションでは、ビルド プロセスで *nx_pppoe_server.c* もインクルードする必要があります。 このファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、そのオブジェクト フォームをアプリケーションのファイルと一緒にリンクする必要があります。 NetX PPPoE サーバーを使用するために必要なことはこれだけです。

## <a name="small-example-system"></a>簡単なシステムの例

NetX PPPoE サーバーの使用方法を示す例を次の図1.1 に示します。 この例では、PPPoE サーバー インクルード ファイル *nx_pppoe_server.h* が 50 行目で取り込まれます。 次に、248 行目の "*thread_0_entry*" で PPPoE サーバーが作成されます。 IP インスタンスを作成してから、PPPoE サーバーを作成する必要があることに注意してください。 IP インスタンスは、165 行目で作成され、初期化されます。 PPPoE サーバー制御ブロック "*pppoe_server*" は、79 行目でグローバル変数として既に定義されています。 257 行目で通知関数が設定されます。 pppoe_session_data_receive 通知関数を設定する必要があることに注意してください。 IP と PPPoE サーバーが正常に作成された後、nx_pppoe_server_enable の呼び出しで PPPoE セッションを確立する PPPoE サーバー プロセスが 272 行目にあります。

一般に、PPPoE モジュールは PPP モジュールと共に使用します。 この例では、PPP サーバー インクルード ファイル *nx_ppp.h* が 49 行目で取り込まれます。 次に、174 行目で PPP サーバーが作成されます。 182 行目で、PPP パケットを送信する関数を設定します。 188 から 200 行目で、IP アドレスを設定し、PAP プロトコルを定義します。 115 から 139 行目で、PAP プロトコルのユーザー名とパスワードを設定します。

PPPoE セッションが確立された後、 281 行目で、アプリケーションは nx_pppoe_server_session_get を呼び出して、セッション情報 (クライアントの MAC アドレスとセッション ID) を取得できます。

アプリケーションは、PPP トラフィックを処理しなくなったら、PppCloseInd または nx_pppoe_server_session_terminate を使用して PPPoE セッションを終了します。

> [!NOTE]
> この例の PPPoE サーバーでは、通常の IP スタックも同時に使用し、1 つのイーサネット ドライバーを共有します。 165 行目の通常の IP インスタンスと 248 行目の PPPoE サーバー インスタンスに同じイーサネット ドライバーを渡します。

> [!NOTE]
> 関数は、定義されている NX_PPPoE_SERVER_SESSION_CONTROL_ENABLE の下でソフトウェアによって呼び出すために、PPPoE 実装によって提供されます。

定義されている場合、PPPoE セッションを制御する機能が有効になります。

アプリケーションが特定の API を呼び出すまで、PPPoE サーバーは要求に自動的には応答しません。定義されていない場合、PPPoE サーバーは自動的に要求に応答します。 これは、nx_pppoe_server.h で既定で有効になります。

物理ヘッダーを入力するための十分な領域を確保するために、**NX_PHYSICAL_HEADER** を 24 に再定義してください。 物理ヘッダー: 14 (イーサネット ヘッダー) + 6 (PPPoE ヘッダー) + 2 (PPP ヘッダー) + 2 (4 バイト アラインメント)。

```c
/**************************************************************************/
/**************************************************************************/
/**                                                                       */
/** NetX PPPoE Server stack Component                                     */
/**                                                                       */
/** This is a small demo of the high-performance NetX PPPoE Server        */
/** stack. This demo includes IP instance, PPPoE Server and PPP Server    */
/** stack. Create one IP instance includes two interfaces to support      */
/** for normal IP stack and PPPoE Server, PPPoE Server can use the        */
/** mutex of IP instance to send PPPoE message when share one Ethernet    */
/** driver. PPPoE Server work with normal IP instance at the same time.   */
/**                                                                       */
/** Note1: Substitute your Ethernet driver instead of                     */
/** _nx_ram_network_driver before run this demo                           */
/**                                                                       */
/** Note2: Prerequisite for using PPPoE.                                  */
/** Redefine NX_PHYSICAL_HEADER to 24 to ensure enough space for filling  */
/** in physical header. Physical header:14(Ethernet header)               */
/** + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment)             */
/**                                                                       */
/**************************************************************************/
/**************************************************************************/


/*****************************************************************/
/*                            NetX Stack                         */
/*****************************************************************/

                                      /***************************/
                                      /* PPP Server              */
                                      /***************************/

                                      /***************************/
                                      /* PPPoE Server            */
                                      /***************************/
/***************************/         /***************************/
/* Normal Ethernet Type    */         /* PPPoE Ethernet Type     */
/***************************/         /***************************/
/***************************/         /***************************/
/* Interface 0             */         /* Interface 1             */
/***************************/         /***************************/

/*****************************************************************/
/*                     Ethernet Dirver                           */
/*****************************************************************/

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nx_ppp.h"
#include     "nx_pppoe_server.h"

/* Defined NX_PPP_PPPOE_ENABLE if use Express Logic's PPP, since PPP module has been modified to match PPPoE moduler under this definition. */
#ifdef NX_PPP_PPPOE_ENABLE

/*   If the driver is not initialized in other module, define */
/*   NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE to initialize the driver in PPPoE module. */
/*   In this demo, the driver has been initialized in IP module. */

#ifdef NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE

/*   NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE: If defined, enables the feature that */
/*   controls the PPPoE session. PPPoE server does not automatically response to the */
/*   request until application call specific API. */

/* Define the block size. */
#define     NX_PACKET_POOL_SIZE     ((1536 + sizeof(NX_PACKET)) * 30)
#define     DEMO_STACK_SIZE         2048
#define     PPPOE_THREAD_SIZE       2048

/* Define the ThreadX and NetX object control blocks... */
TX_THREAD           thread_0;

/* Define the packet pool and IP instance for normal IP instnace. */
NX_PACKET_POOL      pool_0;
NX_IP               ip_0;

/* Define the PPP Server instance. */
NX_PPP              ppp_server;

/* Define the PPPoE Server instance. */
NX_PPPOE_SERVER     pppoe_server;

/* Define the counters. */
CHAR                *pointer;
ULONG               error_counter;

/* Define thread prototypes. */
void     thread_0_entry(ULONG thread_input);

/***** Substitute your PPP driver entry function here *********/
extern void     _nx_ppp_driver(NX_IP_DRIVER *driver_req_ptr);

/***** Substitute your Ethernet driver entry function here *********/
extern void     _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Define the callback functions. */
void     PppDiscoverReq(UINT interfaceHandle);
void     PppOpenReq(UINT interfaceHandle, ULONG length, UCHAR *data);
void     PppCloseRsp(UINT interfaceHandle);
void     PppCloseReq(UINT interfaceHandle);
void     PppTransmitDataReq(UINT interfaceHandle, ULONG length, UCHAR *data, UINT packet_id);
void     PppReceiveDataRsp(UINT interfaceHandle, UCHAR *data);

/* Define the porting layer function for Express Logic's PPP to simulate TTP's PPP. */
/* Functions to be provided by PPP for calling by the PPPoE Stack. */
void     ppp_server_packet_send(NX_PACKET *packet_ptr);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

UINT verify_login(CHAR *name, CHAR *password)
{

    if ((name[0] == 'm') &&
        (name[1] == 'y') &&
        (name[2] == 'n') &&
        (name[3] == 'a') &&
        (name[4] == 'm') &&
        (name[5] == 'e') &&
        (name[6] == (CHAR) 0) &&
        (password[0] == 'm') &&
        (password[1] == 'y') &&
        (password[2] == 'p') &&
        (password[3] == 'a') &&
        (password[4] == 's') &&
        (password[5] == 's') &&
        (password[6] == 'w') &&
        (password[7] == 'o') &&
        (password[8] == 'r') &&
        (password[9] == 'd') &&
        (password[10] == (CHAR) 0))
            return(NX_SUCCESS);
    else
        return(NX_PPP_ERROR);
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{

    UINT status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool for normal IP instance. */
    status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool",
                                    (1536 + sizeof(NX_PACKET)),
                                    pointer, NX_PACKET_POOL_SIZE);
                                    pointer = pointer + NX_PACKET_POOL_SIZE;

    /* Check for error. */
    if (status)
        error_counter++;

    /* Create an normal IP instance. */
    status = nx_ip_create(&ip_0, "NetX IP Instance", IP_ADDRESS(192, 168, 100, 43),
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    /* Check for error. */
    if (status)
        error_counter++;

    /* Create the PPP instance. */
    status = nx_ppp_create(&ppp_server, "PPP Instance", &ip_0, pointer, 2048, 1,
                            &pool_0, NX_NULL, NX_NULL);
    pointer = pointer + 2048;

    /* Check for PPP create error. */
    if (status)
        error_counter++;

    /* Set the PPP packet send function. */
    status = nx_ppp_packet_send_set(&ppp_server, ppp_server_packet_send);

    /* Check for PPP packet send function set error. */
    if (status)
        error_counter++;

    /* Define IP address. This PPP instance is effectively the server since it has both IP addresses. */
    status = nx_ppp_ip_address_assign(&ppp_server, IP_ADDRESS(192, 168, 10, 43),                                         IP_ADDRESS(192, 168, 10, 44));

    /* Check for PPP IP address assign error. */
    if (status)
        error_counter++;

    /* Setup PAP, this PPP instance is effectively the server since it will verify the name and password. */
    status = nx_ppp_pap_enable(&ppp_server, NX_NULL, verify_login);

    /* Check for PPP PAP enable error. */
    if (status)
        error_counter++;

    /* Attach an interface for PPP. */
    status = nx_ip_interface_attach(&ip_0, "Second Interface For PPP", 
                            IP_ADDRESS(0, 0, 0, 0), 0, nx_ppp_driver);

    /* Check for error. */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for Normal IP Instance. */
    status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
        error_counter++;

    /* Enable ICMP */
    status = nx_icmp_enable(&ip_0);
    if(status)
        error_counter++;

    /* Enable UDP traffic. */
    status = nx_udp_enable(&ip_0);
    if (status)
        error_counter++;

    /* Enable TCP traffic. */
    status = nx_tcp_enable(&ip_0);
    if (status)
        error_counter++;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
                    pointer = pointer + DEMO_STACK_SIZE;
}

/* Define the test threads. */

void     thread_0_entry(ULONG thread_input)
{
UINT     status;
ULONG    ip_status;

    /* Create the PPPoE instance. */
    status = nx_pppoe_server_create(&pppoe_server, (UCHAR *)"PPPoE Server", &ip_0, 0,
                    _nx_ram_network_driver, &pool_0, pointer, PPPOE_THREAD_SIZE, 4);
    pointer = pointer + PPPOE_THREAD_SIZE;
    if (status)
    {
        error_counter++;
        return;
    }

    /* Set the callback notify function. */
    status = nx_pppoe_server_callback_notify_set(&pppoe_server, PppDiscoverReq,
        PppOpenReq, PppCloseRsp, PppCloseReq, PppTransmitDataReq, PppReceiveDataRsp);

    if (status)
    {
        error_counter++;
        return;
    }

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call function function to set the default service Name. */
        /* PppInitInd(length, aData); */
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */

    /* Enable PPPoE Server. */
    status = nx_pppoe_server_enable(&pppoe_server);
    if (status)
    {
        error_counter++;
        return;
    }

    /* Get the PPPoE Client physical address and Session ID after establish PPPoE Session. */
    /*
        status = nx_pppoe_server_session_get(&pppoe_server, interfaceHandle, &client_mac_msw, &client_mac_lsw, &session_id);
        if (status)
            error_counter++;
    */

    /* Wait for the link to come up. */
    status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_ADDRESS_RESOLVED,
                                            &ip_status, NX_WAIT_FOREVER);
    if (status)
    {
        error_counter++;
        return;
    }

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to terminate the PPPoE Session. */
        /* PppCloseInd(interfaceHandle, causeCode); */
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */

}

void     PppDiscoverReq(UINT interfaceHandle)
{

    /* Receive the PPPoE Discovery Initiation Message. */
    
    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to define the Service Name field of the PADO packet. */
        PppDiscoverCnf(0, NX_NULL, interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppOpenReq(UINT interfaceHandle, ULONG length, UCHAR *data)
{

    /* Get the notify that receive the PPPoE Discovery Request Message. */

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to accept the PPPoE session. */
        PppOpenCnf(NX_TRUE, interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppCloseRsp(UINT interfaceHandle)
{

    /* Get the notify that receive the PPPoE Discovery Terminate Message. */

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to confirm that the handle has been freed. */
        PppCloseCnf(interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppCloseReq(UINT interfaceHandle)
{

    /* Get the notify that PPPoE Discovery Terminate Message has been sent. */

}

void     PppTransmitDataReq(UINT interfaceHandle, ULONG length, UCHAR *data, UINT packet_id)
{

    NX_PACKET *packet_ptr;

    /* Get the notify that receive the PPPoE Session data. */

    /* Call PPP Server to receive the PPP data fame. */
    packet_ptr = (NX_PACKET *)(packet_id);
    nx_ppp_packet_receive(&ppp_server, packet_ptr);

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to confirm that the data has been processed. */
        PppTransmitDataCnf(interfaceHandle, data, packet_id);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppReceiveDataRsp(UINT interfaceHandle, UCHAR *data)
{

    /* Get the notify that the PPPoE Session data has been sent. */

}

/* PPP Server send function. */
void     ppp_server_packet_send(NX_PACKET *packet_ptr)
{

    /* For Express Logic's PPP test, the session should be the first session, so set interfaceHandle as 0. */
    UINT interfaceHandle = 0;

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        while(packet_ptr)
        {

            /* Call functions to be provided by PPPoE for TTP. */
            PppReceiveDataInd(interfaceHandle, (packet_ptr -> nx_packet_append_ptr -
            packet_ptr -> nx_packet_prepend_ptr), packet_ptr -> nx_packet_prepend_ptr);

            /* Move to the next packet structure. */
            packet_ptr = packet_ptr -> nx_packet_next;
        }
    #else
        /* Directly Call PPPoE send function to send out the data through PPPoE module. */
        nx_pppoe_server_session_packet_send(&pppoe_server, interfaceHandle, packet_ptr);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}
#endif /* NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE */

#endif /* NX_PPP_PPPOE_ENABLE */
```

図 1.1 NetX での PPPoE サーバーの使用例

## <a name="configuration-options"></a>構成オプション

NetX 用 PPPoE サーバーを構築するための構成オプションがいくつかあります。 次の一覧では、それぞれについて詳しく説明しています。

- **NX_DISABLE_ERROR_CHECKING**: このオプションを定義すると、基本的な PPPoE サーバー エラー チェックが削除されます。 通常は、アプリケーションがデバッグされた後に使用されます。

- **NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE**: 定義した場合、PPPoE セッションを制御する機能が有効になります。 アプリケーションが特定の API を呼び出すまで、PPPoE サーバーは要求に自動的には応答しません。

- **NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE**: 定義した場合、PPPoE モジュールでイーサネット ドライバーを初期化する機能が有効になります。 既定では無効になります。

- **NX_PPPOE_SERVER_THREAD_TIME_SLICE**: PPPoE サーバー スレッドのタイムスライス オプション。 この値は既定では TX_NO_TIME_SLICE です。

- **NX_PPPOE_SERVER_MAX_CLIENT_SESSION_NUMBER**: 同時クライアント セッションの最大数を定義します。 この値は既定では 10 です。

- **NX_PPPOE_SERVER_MAX_HOST_UNIQ_SIZE**: Host-Uniq の最大サイズを定義します。 この値は既定では 32 です。

- **NX_PPPOE_SERVER_MAX_RELAY_SESSION_ID_SIZE**: リレー セッション ID の最大サイズを定義します。この値は既定では 12 です。

- **NX_PPPOE_SERVER_MIN_PACKET_PAYLOAD_SIZE**: PPPoE サーバーの最小パケット ペイロード サイズを指定します。 パケット ペイロード サイズがこの値より大きい場合、パケット チェーンを回避できます。 この値は既定では 1520 (イーサネットの最大ペイロード サイズ 1500、イーサネット ヘッダー 14、CRC 2、4 バイト アラインメント 4) です。

- **NX_PPPOE_SERVER_PACKET_TIMEOUT**: パケットを割り当てたり、パケットにデータを追加したりするための待機オプション (タイマー刻み) を定義します。 この値は既定では **NX_IP_PERIODIC_RATE** (100 ティック) です。

- **NX_PPPOE_SERVER_START_SESSION_ID**: PPPoE セッションに割り当てるための開始セッション ID を定義します。 この値は既定では 0X4944 (ID の ASCII 値) です。