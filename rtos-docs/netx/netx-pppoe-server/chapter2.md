---
title: 第 2 章 - Azure RTOS NetX PPPoE サーバーのインストールと使用
description: この章では、Azure RTOS NetX PPPoE サーバー コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5b52164911676b68c67da01d698e41c02730e45a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810403"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pppoe-server"></a><span data-ttu-id="63aea-103">第 2 章 - Azure RTOS NetX PPPoE サーバーのインストールと使用</span><span class="sxs-lookup"><span data-stu-id="63aea-103">Chapter 2 - Installation and use of Azure RTOS NetX PPPoE Server</span></span>

<span data-ttu-id="63aea-104">この章では、Azure RTOS NetX PPPoE サーバー コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="63aea-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX PPPoE Server component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="63aea-105">製品ディストリビューション</span><span class="sxs-lookup"><span data-stu-id="63aea-105">Product Distribution</span></span>

<span data-ttu-id="63aea-106">NetX 用 PPPoE サーバーは、[https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="63aea-106">PPPoE Server for NetX is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="63aea-107">このパッケージには、次のように、2 つのソース ファイルと、このドキュメントを含む PDF ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="63aea-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="63aea-108">**nx_pppoe_server.h**: NetX 用 PPPoE サーバーのヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="63aea-108">**nx_pppoe_server.h**: Header file for PPPoE Server for NetX</span></span>
- <span data-ttu-id="63aea-109">**nx_pppoe_server.c**: NetX 用 PPPoE サーバーの C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="63aea-109">**nx_pppoe_server.c**: C Source file for PPPoE Server for NetX</span></span>
- <span data-ttu-id="63aea-110">**nx_pppoe_server.pdf**: NetX 用 PPPoE サーバーの PDF 説明書</span><span class="sxs-lookup"><span data-stu-id="63aea-110">**nx_pppoe_server.pdf**: PDF description of PPPoE Server for NetX</span></span>
- <span data-ttu-id="63aea-111">**demo_netx_pppoe_server.c**: NetX PPPoE サーバーのデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="63aea-111">**demo_netx_pppoe_server.c**: NetX PPPoE Server demonstration</span></span>

## <a name="pppoe-server-installation"></a><span data-ttu-id="63aea-112">PPPoE サーバーのインストール</span><span class="sxs-lookup"><span data-stu-id="63aea-112">PPPoE Server Installation</span></span>

<span data-ttu-id="63aea-113">NetX 用 PPPoE サーバーを使用するには、前述のディストリビューション全体を、NetX がインストールされているのと同じディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="63aea-113">In order to use PPPoE Server for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="63aea-114">たとえば、NetX が " *\threadx\arm7\green*" ディレクトリにインストールされている場合は、*nx_pppoe_server.h* および *nx_pppoe_server.c* ファイルをこのディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="63aea-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_pppoe_server.h* and *nx_pppoe_server.c* files should be copied into this directory.</span></span>

## <a name="using-pppoe-server"></a><span data-ttu-id="63aea-115">PPPoE サーバーの使用</span><span class="sxs-lookup"><span data-stu-id="63aea-115">Using PPPoE Server</span></span>

<span data-ttu-id="63aea-116">NetX 用 PPPoE サーバーは簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="63aea-116">Using PPPoE Server for NetX is easy.</span></span> <span data-ttu-id="63aea-117">基本的には、ThreadX と NetX を使用するために、アプリケーション コードにそれぞれ *tx_api.h* と *nx_api.h* をインクルードした後に、*nx_pppoe_server.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="63aea-117">Basically, the application code must include *nx_pppoe_server.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="63aea-118">*nx_pppoe_server.h* をインクルードすると、アプリケーション コードで、このガイドで後述する PPPoE サーバー関数呼び出しを行えるようになります。</span><span class="sxs-lookup"><span data-stu-id="63aea-118">Once *nx_pppoe_server.h* is included, the application code is then able to make the PPPoE Server function calls specified later in this guide.</span></span> <span data-ttu-id="63aea-119">アプリケーションでは、ビルド プロセスで *nx_pppoe_server.c* もインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="63aea-119">The application must also include *nx_pppoe_server.c* in the build process.</span></span> <span data-ttu-id="63aea-120">このファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、そのオブジェクト フォームをアプリケーションのファイルと一緒にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="63aea-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="63aea-121">NetX PPPoE サーバーを使用するために必要なことはこれだけです。</span><span class="sxs-lookup"><span data-stu-id="63aea-121">This is all that is required to use NetX PPPoE Server.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="63aea-122">簡単なシステムの例</span><span class="sxs-lookup"><span data-stu-id="63aea-122">Small Example System</span></span>

<span data-ttu-id="63aea-123">NetX PPPoE サーバーの使用方法を示す例を次の図1.1 に示します。</span><span class="sxs-lookup"><span data-stu-id="63aea-123">The following is an example that illustrates how to use NetX PPPoE Server is described in Figure 1.1.</span></span> <span data-ttu-id="63aea-124">この例では、PPPoE サーバー インクルード ファイル *nx_pppoe_server.h* が 50 行目で取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="63aea-124">In this example, the PPPoE Server include file *nx_pppoe_server.h* is brought in at line 50.</span></span> <span data-ttu-id="63aea-125">次に、248 行目の "*thread_0_entry*" で PPPoE サーバーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="63aea-125">Next, PPPoE Server is created in *"thread_0_entry*" at line 248.</span></span> <span data-ttu-id="63aea-126">IP インスタンスを作成してから、PPPoE サーバーを作成する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="63aea-126">Note that PPPoE Server should be created after create the IP instance.</span></span> <span data-ttu-id="63aea-127">IP インスタンスは、165 行目で作成され、初期化されます。</span><span class="sxs-lookup"><span data-stu-id="63aea-127">The IP instance is created and initialized line165.</span></span> <span data-ttu-id="63aea-128">PPPoE サーバー制御ブロック "*pppoe_server*" は、79 行目でグローバル変数として既に定義されています。</span><span class="sxs-lookup"><span data-stu-id="63aea-128">The PPPoE Server control block "*pppoe_server*" was defined as a global variable at line 79 previously.</span></span> <span data-ttu-id="63aea-129">257 行目で通知関数が設定されます。</span><span class="sxs-lookup"><span data-stu-id="63aea-129">The notify functions are set at line 257.</span></span> <span data-ttu-id="63aea-130">pppoe_session_data_receive 通知関数を設定する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="63aea-130">Note that pppoe_session_data_receive notify function must be set.</span></span> <span data-ttu-id="63aea-131">IP と PPPoE サーバーが正常に作成された後、nx_pppoe_server_enable の呼び出しで PPPoE セッションを確立する PPPoE サーバー プロセスが 272 行目にあります。</span><span class="sxs-lookup"><span data-stu-id="63aea-131">After successful creation of IP and PPPoE Server, the PPPoE Server process of establishing a PPPoE session at the call to nx_pppoe_server_enable at line 272.</span></span>

<span data-ttu-id="63aea-132">一般に、PPPoE モジュールは PPP モジュールと共に使用します。</span><span class="sxs-lookup"><span data-stu-id="63aea-132">In general, PPPoE module should be used with PPP module.</span></span> <span data-ttu-id="63aea-133">この例では、PPP サーバー インクルード ファイル *nx_ppp.h* が 49 行目で取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="63aea-133">In this example, the PPP Server include file *nx_ppp.h* is brought in at line 49.</span></span> <span data-ttu-id="63aea-134">次に、174 行目で PPP サーバーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="63aea-134">Next, PPP Server is created at line 174.</span></span> <span data-ttu-id="63aea-135">182 行目で、PPP パケットを送信する関数を設定します。</span><span class="sxs-lookup"><span data-stu-id="63aea-135">Line 182 setup the function to send PPP packet.</span></span> <span data-ttu-id="63aea-136">188 から 200 行目で、IP アドレスを設定し、PAP プロトコルを定義します。</span><span class="sxs-lookup"><span data-stu-id="63aea-136">Line 188-200 setup the IP addresses and define the pap protocol.</span></span> <span data-ttu-id="63aea-137">115 から 139 行目で、PAP プロトコルのユーザー名とパスワードを設定します。</span><span class="sxs-lookup"><span data-stu-id="63aea-137">Line 115-139 setup the user name and password for pap protocol.</span></span>

<span data-ttu-id="63aea-138">PPPoE セッションが確立された後、</span><span class="sxs-lookup"><span data-stu-id="63aea-138">After the PPPoE session established.</span></span> <span data-ttu-id="63aea-139">281 行目で、アプリケーションは nx_pppoe_server_session_get を呼び出して、セッション情報 (クライアントの MAC アドレスとセッション ID) を取得できます。</span><span class="sxs-lookup"><span data-stu-id="63aea-139">The application can call nx_pppoe_server_session_get to get the session information (client MAC address and session id) at line 281.</span></span>

<span data-ttu-id="63aea-140">アプリケーションは、PPP トラフィックを処理しなくなったら、PppCloseInd または nx_pppoe_server_session_terminate を使用して PPPoE セッションを終了します。</span><span class="sxs-lookup"><span data-stu-id="63aea-140">When the application no longer process PPP traffic, the application PppCloseInd or nx_pppoe_server_session_terminate to terminate the PPPoE session.</span></span>

> [!NOTE]
> <span data-ttu-id="63aea-141">この例の PPPoE サーバーでは、通常の IP スタックも同時に使用し、1 つのイーサネット ドライバーを共有します。</span><span class="sxs-lookup"><span data-stu-id="63aea-141">In this example, PPPoE Server work with normal IP stack at the same time, and share one Ethernet driver.</span></span> <span data-ttu-id="63aea-142">165 行目の通常の IP インスタンスと 248 行目の PPPoE サーバー インスタンスに同じイーサネット ドライバーを渡します。</span><span class="sxs-lookup"><span data-stu-id="63aea-142">Pass the same Ethernet driver for normal IP instance at line 165 and PPPoE Server instance at line 248.</span></span>

> [!NOTE]
> <span data-ttu-id="63aea-143">関数は、定義されている NX_PPPoE_SERVER_SESSION_CONTROL_ENABLE の下でソフトウェアによって呼び出すために、PPPoE 実装によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="63aea-143">The functions are provided by the PPPoE implementation for calling by the software under defined NX_PPPoE_SERVER_SESSION_CONTROL_ENABELE.</span></span>

<span data-ttu-id="63aea-144">定義されている場合、PPPoE セッションを制御する機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="63aea-144">If defined, enables the feature that controls the PPPoE session.</span></span>

<span data-ttu-id="63aea-145">アプリケーションが特定の API を呼び出すまで、PPPoE サーバーは要求に自動的には応答しません。定義されていない場合、PPPoE サーバーは自動的に要求に応答します。</span><span class="sxs-lookup"><span data-stu-id="63aea-145">PPPoE server does not automatically response to the request until application call specific API, if not defined, PPPoE Server automatically responses to the request.</span></span> <span data-ttu-id="63aea-146">これは、nx_pppoe_server.h で既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="63aea-146">It enables by default in nx_pppoe_server.h.</span></span>

<span data-ttu-id="63aea-147">物理ヘッダーを入力するための十分な領域を確保するために、**NX_PHYSICAL_HEADER** を 24 に再定義してください。</span><span class="sxs-lookup"><span data-stu-id="63aea-147">Note, redefine **NX_PHYSICAL_HEADER** to 24 to ensure enough space for filling in physical header.</span></span> <span data-ttu-id="63aea-148">物理ヘッダー: 14 (イーサネット ヘッダー) + 6 (PPPoE ヘッダー) + 2 (PPP ヘッダー) + 2 (4 バイト アラインメント)。</span><span class="sxs-lookup"><span data-stu-id="63aea-148">Physical header:14(Ethernet header) + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment).</span></span>

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

<span data-ttu-id="63aea-149">図 1.1 NetX での PPPoE サーバーの使用例</span><span class="sxs-lookup"><span data-stu-id="63aea-149">Figure 1.1 Example of PPPoE Server use with NetX</span></span>

## <a name="configuration-options"></a><span data-ttu-id="63aea-150">構成オプション</span><span class="sxs-lookup"><span data-stu-id="63aea-150">Configuration Options</span></span>

<span data-ttu-id="63aea-151">NetX 用 PPPoE サーバーを構築するための構成オプションがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="63aea-151">There are several configuration options for building PPPoE Server for NetX.</span></span> <span data-ttu-id="63aea-152">次の一覧では、それぞれについて詳しく説明しています。</span><span class="sxs-lookup"><span data-stu-id="63aea-152">The following list describes each in detail:</span></span>

- <span data-ttu-id="63aea-153">**NX_DISABLE_ERROR_CHECKING**: このオプションを定義すると、基本的な PPPoE サーバー エラー チェックが削除されます。</span><span class="sxs-lookup"><span data-stu-id="63aea-153">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic PPPoE Server error checking.</span></span> <span data-ttu-id="63aea-154">通常は、アプリケーションがデバッグされた後に使用されます。</span><span class="sxs-lookup"><span data-stu-id="63aea-154">It is typically used after the application has been debugged.</span></span>

- <span data-ttu-id="63aea-155">**NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE**: 定義した場合、PPPoE セッションを制御する機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="63aea-155">**NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE**: If defined, enables the feature that controls the PPPoE session.</span></span> <span data-ttu-id="63aea-156">アプリケーションが特定の API を呼び出すまで、PPPoE サーバーは要求に自動的には応答しません。</span><span class="sxs-lookup"><span data-stu-id="63aea-156">PPPoE server does not automatically response to the request until application call specific API.</span></span>

- <span data-ttu-id="63aea-157">**NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE**: 定義した場合、PPPoE モジュールでイーサネット ドライバーを初期化する機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="63aea-157">**NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE**: If defined, enables the feature to initialize the Ethernet driver in PPPoE module.</span></span> <span data-ttu-id="63aea-158">既定では無効になります。</span><span class="sxs-lookup"><span data-stu-id="63aea-158">It disables by default.</span></span>

- <span data-ttu-id="63aea-159">**NX_PPPOE_SERVER_THREAD_TIME_SLICE**: PPPoE サーバー スレッドのタイムスライス オプション。</span><span class="sxs-lookup"><span data-stu-id="63aea-159">**NX_PPPOE_SERVER_THREAD_TIME_SLICE**: Time-slice option for PPPoE Server thread.</span></span> <span data-ttu-id="63aea-160">この値は既定では TX_NO_TIME_SLICE です。</span><span class="sxs-lookup"><span data-stu-id="63aea-160">By default, this value is TX_NO_TIME_SLICE.</span></span>

- <span data-ttu-id="63aea-161">**NX_PPPOE_SERVER_MAX_CLIENT_SESSION_NUMBER**: 同時クライアント セッションの最大数を定義します。</span><span class="sxs-lookup"><span data-stu-id="63aea-161">**NX_PPPOE_SERVER_MAX_CLIENT_SESSION_NUMBER**: This defines the max number of concurrent client sessions.</span></span> <span data-ttu-id="63aea-162">この値は既定では 10 です。</span><span class="sxs-lookup"><span data-stu-id="63aea-162">By default, this value is 10.</span></span>

- <span data-ttu-id="63aea-163">**NX_PPPOE_SERVER_MAX_HOST_UNIQ_SIZE**: Host-Uniq の最大サイズを定義します。</span><span class="sxs-lookup"><span data-stu-id="63aea-163">**NX_PPPOE_SERVER_MAX_HOST_UNIQ_SIZE**: This defines the max size of Host-Uniq.</span></span> <span data-ttu-id="63aea-164">この値は既定では 32 です。</span><span class="sxs-lookup"><span data-stu-id="63aea-164">By default, this value is 32.</span></span>

- <span data-ttu-id="63aea-165">**NX_PPPOE_SERVER_MAX_RELAY_SESSION_ID_SIZE**: リレー セッション ID の最大サイズを定義します。この値は既定では 12 です。</span><span class="sxs-lookup"><span data-stu-id="63aea-165">**NX_PPPOE_SERVER_MAX_RELAY_SESSION_ID_SIZE**: This defines the max size of Relay-Session-Id. By default, this value is 12.</span></span>

- <span data-ttu-id="63aea-166">**NX_PPPOE_SERVER_MIN_PACKET_PAYLOAD_SIZE**: PPPoE サーバーの最小パケット ペイロード サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="63aea-166">**NX_PPPOE_SERVER_MIN_PACKET_PAYLOAD_SIZE**: Specifies the Minimum packet payload size for PPPoE Server.</span></span> <span data-ttu-id="63aea-167">パケット ペイロード サイズがこの値より大きい場合、パケット チェーンを回避できます。</span><span class="sxs-lookup"><span data-stu-id="63aea-167">If the packet payload size is greater than this value, can avoid packet chained.</span></span> <span data-ttu-id="63aea-168">この値は既定では 1520 (イーサネットの最大ペイロード サイズ 1500、イーサネット ヘッダー 14、CRC 2、4 バイト アラインメント 4) です。</span><span class="sxs-lookup"><span data-stu-id="63aea-168">By default, this value is 1520 (Maximum Payload Size of Ethernet 1500, Ethernet Header 14, CRC 2 and Four-byte alignment 4).</span></span>

- <span data-ttu-id="63aea-169">**NX_PPPOE_SERVER_PACKET_TIMEOUT**: パケットを割り当てたり、パケットにデータを追加したりするための待機オプション (タイマー刻み) を定義します。</span><span class="sxs-lookup"><span data-stu-id="63aea-169">**NX_PPPOE_SERVER_PACKET_TIMEOUT**: This defines the wait potion(in timer ticks) for allocating packets or appending data into packets.</span></span> <span data-ttu-id="63aea-170">この値は既定では **NX_IP_PERIODIC_RATE** (100 ティック) です。</span><span class="sxs-lookup"><span data-stu-id="63aea-170">By default, this value is **NX_IP_PERIODIC_RATE** (100 ticks).</span></span>

- <span data-ttu-id="63aea-171">**NX_PPPOE_SERVER_START_SESSION_ID**: PPPoE セッションに割り当てるための開始セッション ID を定義します。</span><span class="sxs-lookup"><span data-stu-id="63aea-171">**NX_PPPOE_SERVER_START_SESSION_ID**: This defines the start Session ID for assigning to the PPPoE Session.</span></span> <span data-ttu-id="63aea-172">この値は既定では 0X4944 (ID の ASCII 値) です。</span><span class="sxs-lookup"><span data-stu-id="63aea-172">By default, this value is 0X4944(ASCII value for ID).</span></span>