---
title: 第 2 章 - Azure RTOS NetX Point-to-Point Protocol (PPP) のインストールと使用
description: この章では、Azure RTOS NetX Point-to-Point Protocol (PPP) コンポーネントのインストール、セットアップ、および使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 40f09da31f5541208c3b2cc0eeb54850b3d71f7c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811471"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-point-to-point-protocol-ppp"></a><span data-ttu-id="7e22c-103">第 2 章 - Azure RTOS NetX Point-to-Point Protocol (PPP) のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="7e22c-103">Chapter 2 - Installation and use of Azure RTOS NetX Point-to-Point Protocol (PPP)</span></span>

<span data-ttu-id="7e22c-104">この章では、Azure RTOS NetX Point-to-Point Protocol (PPP) コンポーネントのインストール、セットアップ、および使用に関連するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Point-to-Point Protocol (PPP) component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="7e22c-105">製品の配布</span><span class="sxs-lookup"><span data-stu-id="7e22c-105">Product Distribution</span></span>

<span data-ttu-id="7e22c-106">Azure RTOS NetX Point-to-Point Protocol (PPP) パッケージは、<https://github.com/azure-rtos/netx> で入手できます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-106">The Azure RTOS NetX Point-to-Point Protocol (PPP) package is available at <https://github.com/azure-rtos/netx>.</span></span> <span data-ttu-id="7e22c-107">このパッケージには、次のファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7e22c-107">The package includes the following files:</span></span>

- <span data-ttu-id="7e22c-108">**nx_ppp.h**: NetX PPP のヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="7e22c-108">**nx_ppp.h**: Header file for PPP for NetX</span></span>
- <span data-ttu-id="7e22c-109">**nx_ppp.c**: NetX PPP の C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="7e22c-109">**nx_ppp.c**: C Source file for PPP for NetX</span></span>
- <span data-ttu-id="7e22c-110">**nx_ppp.pdf**: NetX PPP の PDF 説明書</span><span class="sxs-lookup"><span data-stu-id="7e22c-110">**nx_ppp.pdf**: PDF description of PPP for NetX</span></span>
- <span data-ttu-id="7e22c-111">**demo_netx_ppp.c**: NetX PPP のデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="7e22c-111">**demo_netx_ppp.c**: NetX PPP demonstration</span></span>

## <a name="ppp-installation"></a><span data-ttu-id="7e22c-112">PPP のインストール</span><span class="sxs-lookup"><span data-stu-id="7e22c-112">PPP Installation</span></span>

<span data-ttu-id="7e22c-113">NetX PPP を使用するには、前述のディストリビューション全体を、NetX がインストールされているのと同じディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-113">In order to use PPP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="7e22c-114">たとえば、NetX が " *\threadx\arm7\green*" ディレクトリにインストールされている場合は、*nx_ppp.h* ファイルと *nx_ppp.c* ファイルをこのディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-114">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_ppp.h* and *nx_ppp.c* files should be copied into this directory.</span></span>

## <a name="using-ppp"></a><span data-ttu-id="7e22c-115">PPP の使用</span><span class="sxs-lookup"><span data-stu-id="7e22c-115">Using PPP</span></span>

<span data-ttu-id="7e22c-116">NetX PPP は簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-116">Using PPP for NetX is easy.</span></span> <span data-ttu-id="7e22c-117">基本的には、アプリケーション コードに ThreadX と NetX を使用するための *tx_api.h* と *nx_api.h* をインクルードした後、*nx_ppp.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-117">Basically, the application code must include *nx_ppp.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="7e22c-118">*nx_ppp.h* をインクルードすると、アプリケーション コードで、このガイドで後述する PPP 関数呼び出しを行えるようになります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-118">Once *nx_ppp.h* is included, the application code is then able to make the PPP function calls specified later in this guide.</span></span> <span data-ttu-id="7e22c-119">アプリケーションのビルド プロセスで、*nx_ppp.c* もインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-119">The application must also include *nx_ppp.c* in the build process.</span></span> <span data-ttu-id="7e22c-120">このファイルは、他のアプリケーション ファイルと同様にコンパイルする必要があり、そのオブジェクト形式は、アプリケーションのファイルと一緒にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="7e22c-121">NetX PPP を使用するために必要なことはこれだけです。</span><span class="sxs-lookup"><span data-stu-id="7e22c-121">This is all that is required to use NetX PPP.</span></span>

## <a name="using-modems"></a><span data-ttu-id="7e22c-122">モデムの使用</span><span class="sxs-lookup"><span data-stu-id="7e22c-122">Using Modems</span></span>

<span data-ttu-id="7e22c-123">インターネットへの接続にモデムが必要な場合、NetX PPP 製品を使用するには、特別な考慮事項が必要となります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-123">If a modem is required for connection to the internet, some special considerations are required in order to use the NetX PPP product.</span></span> <span data-ttu-id="7e22c-124">基本的に、モデムを使用すると、初期化ロジックと通信喪失のロジックが追加されます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-124">Basically, using a modem introduces additional initialization logic and logic for loss of communication.</span></span> <span data-ttu-id="7e22c-125">さらに、追加のモデム ロジックのほとんどは、NetX PPP のコンテキストの外部で実行されます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-125">In addition, most of the additional modem logic is done outside the context of NetX PPP.</span></span> <span data-ttu-id="7e22c-126">モデムで NetX PPP を使用する際の基本的な流れは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-126">The basic flow of using the NetX PPP with a modem goes something like this:</span></span>

1. <span data-ttu-id="7e22c-127">モデムを初期化する</span><span class="sxs-lookup"><span data-stu-id="7e22c-127">Initialize Modem</span></span>

1. <span data-ttu-id="7e22c-128">インターネット サービス プロバイダー (ISP) にダイヤルする</span><span class="sxs-lookup"><span data-stu-id="7e22c-128">Dial Internet Service Provider (ISP)</span></span>

1. <span data-ttu-id="7e22c-129">接続を待機する</span><span class="sxs-lookup"><span data-stu-id="7e22c-129">Wait for Connection</span></span>

1. <span data-ttu-id="7e22c-130">ユーザー ID プロンプトを待機する</span><span class="sxs-lookup"><span data-stu-id="7e22c-130">Wait for UserID Prompt</span></span>

1. <span data-ttu-id="7e22c-131">NetX PPP を開始する [動作中の PPP]</span><span class="sxs-lookup"><span data-stu-id="7e22c-131">Start NetX PPP [PPP in operation]</span></span>

1. <span data-ttu-id="7e22c-132">通信の損失</span><span class="sxs-lookup"><span data-stu-id="7e22c-132">Loss of Communication</span></span>

1. <span data-ttu-id="7e22c-133">NetX PPP を停止する (または nx_ppp_restart によって再開する)</span><span class="sxs-lookup"><span data-stu-id="7e22c-133">Stop NetX PPP (or restart via nx_ppp_restart)</span></span>

### <a name="initialize-modem"></a><span data-ttu-id="7e22c-134">モデムを初期化する</span><span class="sxs-lookup"><span data-stu-id="7e22c-134">Initialize Modem</span></span>

<span data-ttu-id="7e22c-135">アプリケーションの低レベルのシリアル出力ルーチンを使用して、一連の ASCII 文字コマンドでモデムを初期化します (詳細については、モデムのドキュメントをご覧ください)。</span><span class="sxs-lookup"><span data-stu-id="7e22c-135">Using the application’s low-level serial output routine, the modem is initialized via a series of ASCII character commands (see modem’s documentation for more details).</span></span>

### <a name="dial-internet-service-provider"></a><span data-ttu-id="7e22c-136">インターネット サービス プロバイダーにダイヤルする</span><span class="sxs-lookup"><span data-stu-id="7e22c-136">Dial Internet Service Provider</span></span>

<span data-ttu-id="7e22c-137">アプリケーションの低レベルのシリアル出力ルーチンを使用して、ISP にダイヤルするようモデムに指示します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-137">Using the application’s low-level serial output routine, the modem is instructed to dial the ISP.</span></span> <span data-ttu-id="7e22c-138">たとえば、123-4567 の番号で ISP にダイヤルする場合、通常、次の ASCII 文字列が使用されます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-138">For example, the following is typical of an ASCII string used to dial an ISP at the number 123-4567:</span></span>

<span data-ttu-id="7e22c-139">"ATDT123456\r"</span><span class="sxs-lookup"><span data-stu-id="7e22c-139">“ATDT123456\r”</span></span>

### <a name="wait-for-connection"></a><span data-ttu-id="7e22c-140">接続を待機する</span><span class="sxs-lookup"><span data-stu-id="7e22c-140">Wait for Connection</span></span>

<span data-ttu-id="7e22c-141">この時点で、アプリケーションは、接続が確立されたことを示す通知をモデムから受信するために待機します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-141">At this point, the application waits to receive indication from the modem that a connection has been established.</span></span> <span data-ttu-id="7e22c-142">これは、アプリケーションの低レベルのシリアル入力ルーチンからの文字を探すことで実現されます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-142">This is accomplished by looking for characters from the application’s low-level serial input routine.</span></span> <span data-ttu-id="7e22c-143">通常、接続が確立されると、モデムから ASCII 文字列 "CONNECT" が返されます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-143">Typically, modems return an ASCII string “CONNECT” when a connection has been established.</span></span>

### <a name="wait-for-user-id-prompt"></a><span data-ttu-id="7e22c-144">ユーザー ID プロンプトを待機する</span><span class="sxs-lookup"><span data-stu-id="7e22c-144">Wait for User ID Prompt</span></span>

<span data-ttu-id="7e22c-145">接続が確立されたら、アプリケーションは ISP からの最初のログイン要求を待つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-145">Once the connection has been established, the application must now wait for an initial login request from the ISP.</span></span> <span data-ttu-id="7e22c-146">通常、これは "Login?" のような ASCII 文字列の形式になります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-146">This typically takes the form of an ASCII string like “Login?”</span></span>

### <a name="start-netx-ppp"></a><span data-ttu-id="7e22c-147">NetX PPP を開始する</span><span class="sxs-lookup"><span data-stu-id="7e22c-147">Start NetX PPP</span></span>

<span data-ttu-id="7e22c-148">この時点で、NetX PPP を開始できます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-148">At this point, the NetX PPP can be started.</span></span> <span data-ttu-id="7e22c-149">これは、*nx_ppp_create* サービスを呼び出した後、*nx_ip_create* サービスを呼び出すことで実現されます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-149">This is accomplished by calling the *nx_ppp_create* service followed by the *nx_ip_create* service.</span></span> <span data-ttu-id="7e22c-150">PAP を有効にしたり、PPP IP アドレスを設定したりするための追加のサービスも必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-150">Additional services to enable PAP and to setup the PPP IP addresses might also be required.</span></span> <span data-ttu-id="7e22c-151">詳細については、このガイドの以降のセクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7e22c-151">Please review the following sections of this guide for more information.</span></span>

### <a name="loss-of-communication"></a><span data-ttu-id="7e22c-152">通信の損失</span><span class="sxs-lookup"><span data-stu-id="7e22c-152">Loss of Communication</span></span>

<span data-ttu-id="7e22c-153">PPP が開始されると、PPP 以外の情報は、アプリケーションで *nx_ppp_create* サービスに指定した "無効なパケット処理" ルーチンに渡されます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-153">Once PPP is started, any non-PPP information is passed to the “invalid packet handling” routine the application specified to the *nx_ppp_create* service.</span></span> <span data-ttu-id="7e22c-154">通常、ISP との通信が失われると、モデムから "NO CARRIER" などの ASCII 文字列が送信されます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-154">Typically, modems send an ASCII string such as “NO CARRIER” when communication is lost with the ISP.</span></span> <span data-ttu-id="7e22c-155">アプリケーションでこのような情報を含む PPP 以外のパケットを受信した場合は、NetX PPP インスタンスを停止するか、*nx_ppp_restart* API を介して PPP ステート マシンを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-155">When the application receives a non-PPP packet with such information, it should proceed to either stop the NetX PPP instance or to restart the PPP state machine via the *nx_ppp_restart* API.</span></span>

### <a name="stop-netx-ppp"></a><span data-ttu-id="7e22c-156">NetX PPP を停止する</span><span class="sxs-lookup"><span data-stu-id="7e22c-156">Stop NetX PPP</span></span>

<span data-ttu-id="7e22c-157">NetX PPP の停止は非常に簡単です。</span><span class="sxs-lookup"><span data-stu-id="7e22c-157">Stopping the NetX PPP is fairly straightforward.</span></span> <span data-ttu-id="7e22c-158">基本的に、作成されたすべてのソケットをバインド解除して削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-158">Basically, all created sockets must be unbound and deleted.</span></span> <span data-ttu-id="7e22c-159">次に、*nx_ip_delete* サービスを使用して IP インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-159">Next, delete the IP instance via the *nx_ip_delete* service.</span></span> <span data-ttu-id="7e22c-160">IP インスタンスが削除されたら、*nx_ppp_delete* サービスを呼び出して、PPP を停止するプロセスを終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-160">Once the IP instance is deleted, the *nx_ppp_delete* service should be called to finish the process of stopping PPP.</span></span> <span data-ttu-id="7e22c-161">この時点で、アプリケーションは ISP との通信の再確立を試行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-161">At this point, the application is now able to attempt to reestablish communication with the ISP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="7e22c-162">小規模のシステム例</span><span class="sxs-lookup"><span data-stu-id="7e22c-162">Small Example System</span></span>

<span data-ttu-id="7e22c-163">NetX PPP の使用がいかに簡単であるかを示す例を下の図 1.1 に示します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-163">An example that illustrates how easy it is to use NetX PPP is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="7e22c-164">この例では、行 3 で PPP インクルード ファイル *nx_ppp.h* が取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-164">In this example, the PPP include file *nx_ppp.h* is brought in at line 3.</span></span> <span data-ttu-id="7e22c-165">次に、行 56 の "*tx_application_define*" で PPP が作成されます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-165">Next, PPP is created in *”tx_application_define*” at line 56.</span></span> <span data-ttu-id="7e22c-166">PPP 制御ブロック "*my_ppp*" は、行 9 でグローバル変数として既に定義されています。</span><span class="sxs-lookup"><span data-stu-id="7e22c-166">The PPP control block “*my_ppp*” was defined as a global variable at line 9 previously.</span></span> 

>[!NOTE]
><span data-ttu-id="7e22c-167">IP インスタンスを作成する前に、PPP を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-167">PPP should be created prior to creating the IP instance.</span></span> <span data-ttu-id="7e22c-168">PPP と IP が正常に作成されると、スレッド "*my_thread*" は、行 98 で PPP リンクが有効になるのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-168">After successful creation of PPP and IP, the thread “*my_thread*” waits for the PPP link to come alive at line 98.</span></span> <span data-ttu-id="7e22c-169">行 104 で、PPP と NetX の両方が完全に動作します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-169">At line 104, both PPP and NetX are fully operational.</span></span>

<span data-ttu-id="7e22c-170">この例に示されていない 1 つの項目は、アプリケーションのシリアル バイト受信 ISR です。</span><span class="sxs-lookup"><span data-stu-id="7e22c-170">The one item not shown in this example is the application’s serial byte receive ISR.</span></span> <span data-ttu-id="7e22c-171">"*my_ppp*" と受信したバイトを入力パラメーターとして指定して、*nx_ppp_byte_receive* を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-171">It will need to call *nx_ppp_byte_receive* with “*my_ppp*” and the byte received as input parameters.</span></span>

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nx_ppp.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_PPP                  my_ppp;

/* Define function prototypes. */

void    my_thread_entry(ULONG thread_input);
void    my_serial_driver_byte_output(UCHAR byte);
void    my_invalid_packet_handler(NX_PACKET *packet_ptr);
 
/* Define main entry point. */
intmain()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
 }


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

/* Setup the working pointer. */
pointer =  (CHAR *) first_unused_memory;

/* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                  pointer, DEMO_STACK_SIZE, 
                  2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                    1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error. */
    if (status)
        error_counter++;

    /* Create a PPP instance. */
    status = nx_ppp_create(&my_ppp, “My PPP”, &my_ip, pointer, 1024, 2, 
                           &my_pool, my_invalid_packet_handler, my_serial_driver_byte_output);
    pointer =  pointer + 1024;
    /* Check for PPP creation pool. */
    if (status)
        error_counter++;

    /* Create an IP instance with the PPP driver. */
    status = nx_ip_create(&my_ip,"My NetX IP Instance", 
                           IP_ADDRESS(216,2,3,1), 0xFFFFFF00, &my_pool, 
                           nx_ppp_driver, pointer, DEMO_STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors. */
    if (status)
        error_counter++;

    /* Enable ICMP for my IP Instance. */
    status =  nx_icmp_enable(&my_ip);

    /* Check for ICMP enable errors. */
    if (status)
        error_counter++;

    /* Enable UDP. */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
}

/* Define my thread. */
void    my_thread_entry(ULONG thread_input)
{

UINT        status;
ULONG       ip_status;
NX_PACKET   *my_packet;

/* Wait for the PPP link in my_ip to become enabled. */
    status =  nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,&ip_status,3000);

    /* Check for IP status error. */
    if (status) 
        return;

    /* Link is fully up and operational. All NetX activities 
    are now available. */

}
```
## <a name="configuration-options"></a><span data-ttu-id="7e22c-172">構成オプション</span><span class="sxs-lookup"><span data-stu-id="7e22c-172">Configuration Options</span></span>

<span data-ttu-id="7e22c-173">NetX PPP を構築するための構成オプションがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-173">There are several configuration options for building PPP for NetX.</span></span> <span data-ttu-id="7e22c-174">次の一覧で、それぞれについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-174">The following list describes each in detail:</span></span>

- <span data-ttu-id="7e22c-175">**NX_DISABLE_ERROR_CHECKING**: このオプションを定義すると、基本的な PPP エラー チェックが削除されます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-175">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic PPP error checking.</span></span> <span data-ttu-id="7e22c-176">通常は、アプリケーションがデバッグされた後に使用します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-176">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="7e22c-177">**NX_PPP_PPPOE_ENABLE**: 定義した場合、PPP はイーサネット経由でパケットを送信できます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-177">**NX_PPP_PPPOE_ENABLE**: If defined, PPP can transmit packet over Ethernet</span></span>
- <span data-ttu-id="7e22c-178">**NX_PPP_BASE_TIMEOUT**: PPP イベントをチェックするために PPP スレッド タスクを起動する期間レート (タイマー刻み) を定義します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-178">**NX_PPP_BASE_TIMEOUT**: This defines the period rate (in timer ticks) that the PPP thread task is woken to check for PPP events.</span></span> <span data-ttu-id="7e22c-179">既定値は、1\*NX_IP_PERIODIC_RATE (100 ティック) です。</span><span class="sxs-lookup"><span data-stu-id="7e22c-179">The default value is 1\*NX_IP_PERIODIC_RATE (100 ticks).</span></span>
- <span data-ttu-id="7e22c-180">**NX_PPP_DISABLE_INFO**: 定義した場合、内部 PPP 情報の収集が無効になります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-180">**NX_PPP_DISABLE_INFO**: If defined, internal PPP information gathering is disabled.</span></span>
- <span data-ttu-id="7e22c-181">**NX_PPP_DEBUG_LOG_ENABLE**: 定義した場合、内部 PPP デバッグ ログが有効になります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-181">**NX_PPP_DEBUG_LOG_ENABLE**: If defined, internal PPP debug log is enabled.</span></span>
- <span data-ttu-id="7e22c-182">**NX_PPP_DEBUG_LOG_PRINT_ENABLE**: 定義した場合、内部 PPP デバッグ ログの *stdio* への *printf* が有効になります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-182">**NX_PPP_DEBUG_LOG_PRINT_ENABLE**:If defined, internal PPP debug log *printf* to *stdio* is enabled.</span></span> <span data-ttu-id="7e22c-183">これは、デバッグ ログも有効になっている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="7e22c-183">This is only valid if the debug log is also enabled.</span></span>
- <span data-ttu-id="7e22c-184">**NX_PPP_DEBUG_LOG_SIZE**: デバッグ ログのサイズ (デバッグ ログのエントリ数)。</span><span class="sxs-lookup"><span data-stu-id="7e22c-184">**NX_PPP_DEBUG_LOG_SIZE**: Size of debug log (number of entries in the debug log).</span></span> <span data-ttu-id="7e22c-185">最後のエントリに到達すると、デバッグ キャプチャは最初のエントリにラップされ、以前にキャプチャされたデータが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-185">On reaching the last entry, the debug capture wraps to the first entry and overwrites any data previously captured.</span></span> <span data-ttu-id="7e22c-186">既定値は 50 です。</span><span class="sxs-lookup"><span data-stu-id="7e22c-186">The default value is 50.</span></span>
- <span data-ttu-id="7e22c-187">**NX_PPP_DEBUG_FRAME_SIZE**: 受信したパケット ペイロードからキャプチャされ、デバッグ出力に保存されるデータの最大量。</span><span class="sxs-lookup"><span data-stu-id="7e22c-187">**NX_PPP_DEBUG_FRAME_SIZE**: Maximum amount of data captured from a received packet payload and saved to debug output.</span></span> <span data-ttu-id="7e22c-188">既定値は 50 です。</span><span class="sxs-lookup"><span data-stu-id="7e22c-188">The default value is 50.</span></span>
- <span data-ttu-id="7e22c-189">**NX_PPP_DISABLE_CHAP**: 定義した場合、MD5 ダイジェスト ロジックなど、内部 PPP CHAP ロジックが削除されます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-189">**NX_PPP_DISABLE_CHAP**: If defined, internal PPP CHAP logic is removed, including the MD5 digest logic.</span></span>
- <span data-ttu-id="7e22c-190">**NX_PPP_DISABLE_PAP**: 定義した場合、内部 PPP PAP ロジックが削除されます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-190">**NX_PPP_DISABLE_PAP**: If defined, internal PPP PAP logic is removed.</span></span>
- <span data-ttu-id="7e22c-191">**NX_PPP_DNS_OPTION_DISABLE**: 定義した場合、IPCP 応答で DNS オプションが無効になります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-191">**NX_PPP_DNS_OPTION_DISABLE**: If defined, DNS Option is disabled in the IPCP response.</span></span>  <span data-ttu-id="7e22c-192">既定では、このオプションは定義されません (DNS オプションが設定されます)。</span><span class="sxs-lookup"><span data-stu-id="7e22c-192">By default this option is not defined (DNS option is set).</span></span>
- <span data-ttu-id="7e22c-193">**NX_PPP_DNS_ADDRESS_MAX_RETRIES**: PPP ホストが IPCP 状態のピアに DNS サーバー アドレスを要求する回数を指定します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-193">**NX_PPP_DNS_ADDRESS_MAX_RETRIES**: This specifies how many times the PPP host will request a DNS Server address from the peer in the IPCP state.</span></span> <span data-ttu-id="7e22c-194">NX_PPP_DNS_OPTION_DISABLE が定義されている場合、これは機能しません。</span><span class="sxs-lookup"><span data-stu-id="7e22c-194">This has no effect if NX_PPP_DNS_OPTION_DISABLE is defined.</span></span> <span data-ttu-id="7e22c-195">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="7e22c-195">The default value is 2.</span></span>
- <span data-ttu-id="7e22c-196">**NX_PPP_HASHED_VALUE_SIZE**: CHAP 認証で使用される "ハッシュ値" 文字列のサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-196">**NX_PPP_HASHED_VALUE_SIZE**: Specifies the size of “hashed value” strings used in CHAP authentication.</span></span> <span data-ttu-id="7e22c-197">既定値は 16 バイトに設定されますが、*nx_ppp.h* をインクルードする前に再定義できます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-197">The default value is set to 16 bytes, but can be redefined prior to inclusion of *nx_ppp.h.*</span></span>
- <span data-ttu-id="7e22c-198">**NX_PPP_MAX_LCP_PROTOCOL_RETRIES**: 別の LCP 構成要求メッセージを送信する前に PPP がタイムアウトした場合の最大再試行回数を定義します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-198">**NX_PPP_MAX_LCP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another LCP configure request message.</span></span> <span data-ttu-id="7e22c-199">この数に達すると、PPP ハンドシェイクが中止され、リンクの状態がダウンになります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-199">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="7e22c-200">既定値は 20 です。</span><span class="sxs-lookup"><span data-stu-id="7e22c-200">The default value is 20.</span></span>
- <span data-ttu-id="7e22c-201">**NX_PPP_MAX_PAP_PROTOCOL_RETRIES**: 別の PAP 認証要求メッセージを送信する前に PPP がタイムアウトした場合の最大再試行回数を定義します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-201">**NX_PPP_MAX_PAP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another PAP authentication request message.</span></span> <span data-ttu-id="7e22c-202">この数に達すると、PPP ハンドシェイクが中止され、リンクの状態がダウンになります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-202">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="7e22c-203">既定値は 20 です。</span><span class="sxs-lookup"><span data-stu-id="7e22c-203">The default value is 20.</span></span>
- <span data-ttu-id="7e22c-204">**NX_PPP_MAX_CHAP_PROTOCOL_RETRIES**: 別の CHAP チャレンジ メッセージを送信する前に PPP がタイムアウトした場合の最大再試行回数を定義します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-204">**NX_PPP_MAX_CHAP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another CHAP challenge message.</span></span> <span data-ttu-id="7e22c-205">この数に達すると、PPP ハンドシェイクが中止され、リンクの状態がダウンになります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-205">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="7e22c-206">既定値は 20 です。</span><span class="sxs-lookup"><span data-stu-id="7e22c-206">The default value is 20.</span></span>
- <span data-ttu-id="7e22c-207">**NX_PPP_MAX_IPCP_PROTOCOL_RETRIES**: 別の IPCP 構成要求メッセージを送信する前に PPP がタイムアウトした場合の最大再試行回数を定義します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-207">**NX_PPP_MAX_IPCP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another IPCP configure request message.</span></span> <span data-ttu-id="7e22c-208">この数に達すると、PPP ハンドシェイクが中止され、リンクの状態がダウンになります。</span><span class="sxs-lookup"><span data-stu-id="7e22c-208">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="7e22c-209">既定値は 20 です。</span><span class="sxs-lookup"><span data-stu-id="7e22c-209">The default value is 20.</span></span>
- <span data-ttu-id="7e22c-210">**NX_PPP_MRU**: PPP の最大受信ユニット (MRU) を指定します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-210">**NX_PPP_MRU**: Specifies the Maximum Receive Unit (MRU) for PPP.</span></span> <span data-ttu-id="7e22c-211">この値は、既定では 1,500 バイト (最小値) です。</span><span class="sxs-lookup"><span data-stu-id="7e22c-211">By default, this value is 1,500 bytes (the minimum value).</span></span> <span data-ttu-id="7e22c-212">*nx_ppp.h* をインクルードする前に、アプリケーションによってこの定義を設定できます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-212">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="7e22c-213">**NX_PPP_MINIMUM_MRU**: LCP 構成要求メッセージで受信する最小 MRU を指定します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-213">**NX_PPP_MINIMUM_MRU**: Specifies the minimum MRU received in an LCP configure request message.</span></span> <span data-ttu-id="7e22c-214">この値は、既定では 1,500 バイト (最小値) です。</span><span class="sxs-lookup"><span data-stu-id="7e22c-214">By default, this value is 1,500 bytes (the minimum value).</span></span> <span data-ttu-id="7e22c-215">*nx_ppp.h* をインクルードする前に、アプリケーションによってこの定義を設定できます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-215">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="7e22c-216">**NX_PPP_NAME_SIZE**: 認証で使用される "name" 文字列のサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-216">**NX_PPP_NAME_SIZE**: Specifies the size of “name” strings used in authentication.</span></span> <span data-ttu-id="7e22c-217">既定値は 32 バイトに設定されていますが、\*nx_ppp.h をインクルードする前に再定義できます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-217">The default value is set to 32bytes, but can be redefined prior to inclusion of \*nx_ppp.h.</span></span>
- <span data-ttu-id="7e22c-218">**NX_PPP_PASSWORD_SIZE**: 認証で使用される "password" 文字列のサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-218">**NX_PPP_PASSWORD_SIZE**: Specifies the size of “password” strings used in authentication.</span></span> <span data-ttu-id="7e22c-219">既定値は 32 バイトに設定されていますが、*nx_ppp.h* をインクルードする前に再定義できます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-219">The default value is set to 32bytes, but can be redefined prior to inclusion of *nx_ppp.h.*</span></span>
- <span data-ttu-id="7e22c-220">**NX_PPP_PROTOCOL_TIMEOUT**: PPP タスクが PPP プロトコル要求メッセージへの応答を受信するための待機オプション (秒単位) を定義します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-220">**NX_PPP_PROTOCOL_TIMEOUT**: This defines the wait option (in seconds) for the PPP task to receive a response to a PPP protocol request message.</span></span> <span data-ttu-id="7e22c-221">既定値は 4 秒です。</span><span class="sxs-lookup"><span data-stu-id="7e22c-221">The default value is 4 seconds.</span></span>
- <span data-ttu-id="7e22c-222">**NX_PPP_RECEIVE_TIMEOUTS**: PPP スレッド タスクが、PPP メッセージ ストリーム内の次の文字の受信を待機してタイムアウトする回数を定義します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-222">**NX_PPP_RECEIVE_TIMEOUTS**: This defines the number of times the PPP thread task times out waiting to receive the next character in a PPP message stream.</span></span> <span data-ttu-id="7e22c-223">その後、PPP はパケットを解放し、次の PPP メッセージの受信待機を開始します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-223">Thereafter, PPP releases the packet and begins waiting to receive the next PPP message.</span></span> <span data-ttu-id="7e22c-224">既定値は 4 です。</span><span class="sxs-lookup"><span data-stu-id="7e22c-224">The default value is 4.</span></span>
- <span data-ttu-id="7e22c-225">**NX_PPP_SERIAL_BUFFER_SIZE**: 受信文字のシリアル バッファーのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-225">**NX_PPP_SERIAL_BUFFER_SIZE**: Specifies the size of the receive character serial buffer.</span></span> <span data-ttu-id="7e22c-226">この値は、既定では 3,000 バイトです。</span><span class="sxs-lookup"><span data-stu-id="7e22c-226">By default, this value is 3,000 bytes.</span></span> <span data-ttu-id="7e22c-227">*nx_ppp.h* をインクルードする前に、アプリケーションによってこの定義を設定できます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-227">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="7e22c-228">**NX_PPP_TIMEOUT**: データを送信するためのパケットを割り当て、IP 層に送信するために PPP シリアル データをパケットにバッファーするときの待機オプション (タイマー ティック単位) を定義します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-228">**NX_PPP_TIMEOUT**: This defines the wait option (in timer ticks) for allocating packets to transmit data as well as buffer PPP serial data into packets to send to the IP layer.</span></span> <span data-ttu-id="7e22c-229">既定値は、4\*NX_IP_PERIODIC_RATE (400 ティック) です。</span><span class="sxs-lookup"><span data-stu-id="7e22c-229">The default value is 4\*NX_IP_PERIODIC_RATE (400 ticks).</span></span>
- <span data-ttu-id="7e22c-230">**NX_PPP_THREAD_TIME_SLICE**: PPP スレッドのタイムスライス オプション。</span><span class="sxs-lookup"><span data-stu-id="7e22c-230">**NX_PPP_THREAD_TIME_SLICE**: Time-slice option for PPP threads.</span></span> <span data-ttu-id="7e22c-231">この値は、既定では TX_NO_TIME_SLICE です。</span><span class="sxs-lookup"><span data-stu-id="7e22c-231">By default, this value is TX_NO_TIME_SLICE.</span></span> <span data-ttu-id="7e22c-232">*nx_ppp.h* をインクルードする前に、アプリケーションによってこの定義を設定できます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-232">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="7e22c-233">**NX_PPP_VALUE_SIZE**: CHAP 認証で使用される "value" 文字列のサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="7e22c-233">**NX_PPP_VALUE_SIZE**: Specifies the size of “value” strings used in CHAP authentication.</span></span> <span data-ttu-id="7e22c-234">既定値は 32 バイトに設定されていますが、nx_ppp.h をインクルードする前に再定義できます。</span><span class="sxs-lookup"><span data-stu-id="7e22c-234">The default value is set to 32bytes, but can be redefined prior to inclusion of nx_ppp.h.</span></span>
