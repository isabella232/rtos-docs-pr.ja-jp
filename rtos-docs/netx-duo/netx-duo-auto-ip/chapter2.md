---
title: 第 2 章 - Azure RTOS NetX Duo AutoIP のインストールと使用
description: このチャプターでは、Azure RTOS NetX Duo AutoIP コンポーネントのインストール、セットアップ、使用に関するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 42c58a4cdec34a03eda9f42315438e5fbe2ea594
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810985"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-autoip"></a><span data-ttu-id="3984e-103">第 2 章 - Azure RTOS NetX Duo AutoIP のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="3984e-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo AutoIP</span></span>

<span data-ttu-id="3984e-104">このチャプターでは、Azure RTOS NetX Duo AutoIP コンポーネントのインストール、セットアップ、使用に関するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="3984e-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo AutoIP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="3984e-105">製品の配布</span><span class="sxs-lookup"><span data-stu-id="3984e-105">Product Distribution</span></span>

<span data-ttu-id="3984e-106">Azure RTOS NetX AutoIP は、[https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) のパブリック ソース コード リポジトリから入手できます。</span><span class="sxs-lookup"><span data-stu-id="3984e-106">Azure RTOS NetX AutoIP can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="3984e-107">パッケージの内容は、次に挙げるソース ファイル 3 つ、インクルード ファイル 1 つ、このドキュメントを含む PDF ファイルです。</span><span class="sxs-lookup"><span data-stu-id="3984e-107">The package includes three source files, one include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="3984e-108">**nx_auto_ip.h**: NetX AutoIP のヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="3984e-108">**nx_auto_ip.h**: Header file for NetX AutoIP</span></span>
- <span data-ttu-id="3984e-109">**nx_auto_ip.c**: NetX AutoIP の C 言語のソース ファイル</span><span class="sxs-lookup"><span data-stu-id="3984e-109">**nx_auto_ip.c**: C Source file for NetX AutoIP</span></span>
- <span data-ttu-id="3984e-110">**demo_netx_auto_ip.c**: NetX AutoIP Demo の C 言語のソース ファイル</span><span class="sxs-lookup"><span data-stu-id="3984e-110">**demo_netx_auto_ip.c**: C Source file for NetX AutoIP Demo</span></span>
- <span data-ttu-id="3984e-111">**nx_auto_ip.pdf**: NetX AutoIP の説明書の PDF ファイル</span><span class="sxs-lookup"><span data-stu-id="3984e-111">**nx_auto_ip.pdf**: PDF description of NetX AutoIP</span></span>

## <a name="autoip-installation"></a><span data-ttu-id="3984e-112">AutoIP のインストール</span><span class="sxs-lookup"><span data-stu-id="3984e-112">AutoIP Installation</span></span>

<span data-ttu-id="3984e-113">NetX AutoIP を使用するには、NetX がインストールされているのと同じディレクトリに、前述の配布パッケージを丸ごとコピーします。</span><span class="sxs-lookup"><span data-stu-id="3984e-113">In order to use NetX AutoIP, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="3984e-114">たとえば、NetX がディレクトリ " *\threadx\arm7\green*" にインストールされている場合は、*nx_auto_ip.h*、*nx_auto_ip.c*、*demo_netx_auto_ip.c* の各ファイルをこのディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="3984e-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_auto_ip.h*, *nx_auto_ip.c*, and *demo_netx_auto_ip.c* files should be copied into this directory.</span></span>

## <a name="using-autoip"></a><span data-ttu-id="3984e-115">AutoIP を使用する</span><span class="sxs-lookup"><span data-stu-id="3984e-115">Using AutoIP</span></span>

<span data-ttu-id="3984e-116">NetX AutoIP の使用方法は簡単です。</span><span class="sxs-lookup"><span data-stu-id="3984e-116">Using NetX AutoIP is easy.</span></span> <span data-ttu-id="3984e-117">基本的に、ThreadX と NetX を使用するためには、アプリケーションのコードに *tx_api.h* と *nx_api.h* をインクルードしてから *nx_auto_ip.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3984e-117">Basically, the application code must include *nx_auto_ip.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="3984e-118">*nx_auto_ip* をインクルードすると、このガイドで後述する AutoIP の関数を、アプリケーションのコードで呼び出せるようになります。</span><span class="sxs-lookup"><span data-stu-id="3984e-118">Once *nx_auto_ip.h* is included, the application code is then able to make the AutoIP function calls specified later in this guide.</span></span> <span data-ttu-id="3984e-119">アプリケーションのビルド時に *nx_auto_ip.c* もインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3984e-119">The application must also include *nx_auto_ip.c* in the build process.</span></span> <span data-ttu-id="3984e-120">これらのファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、そのオブジェクト フォームをアプリケーションのファイルと一緒にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3984e-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="3984e-121">NetX AutoIP の使用に必要なものはこれですべてです。</span><span class="sxs-lookup"><span data-stu-id="3984e-121">This is all that is required to use NetX AutoIP.</span></span>

> [!NOTE]
> <span data-ttu-id="3984e-122">AutoIP は NetX ARP サービスを利用するので、AutoIP を使用する前に *nx_arp_enable* を呼び出して ARP を有効にしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="3984e-122">Since AutoIP utilizes NetX ARP services, ARP must be enabled with the *nx_arp_enable* call prior to using AutoIP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="3984e-123">小規模システムの例</span><span class="sxs-lookup"><span data-stu-id="3984e-123">Small Example System</span></span>

<span data-ttu-id="3984e-124">NetX AutoIP の使用がいかに簡単であるかを示す例について、下の図 1.1 で説明しています。</span><span class="sxs-lookup"><span data-stu-id="3984e-124">An example of how easy it is to use NetX AutoIP is described in Figure 1.1, which appears below.</span></span> <span data-ttu-id="3984e-125">この例では、AutoIP のインクルード ファイル *nx_auto_ip.h* を 002 行目に置きます。</span><span class="sxs-lookup"><span data-stu-id="3984e-125">In this example, the AutoIP include file *nx_auto_ip.h* is brought in at line 002.</span></span> <span data-ttu-id="3984e-126">次に、090 行目の "*tx_application_define*" で NetX AutoIP インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3984e-126">Next, the NetX AutoIP instance is created in "*tx_application_define*" at line 090.</span></span> <span data-ttu-id="3984e-127">NetX AutoIP 制御ブロック auto_ip_0 は、015 行目であらかじめグローバル変数として定義してあります。</span><span class="sxs-lookup"><span data-stu-id="3984e-127">Note that the NetX AutoIP control block "auto_ip_0" was defined previously as a global variable at line 015.</span></span> <span data-ttu-id="3984e-128">作成を完了した後、098 行目で NetX AutoIP を開始します。</span><span class="sxs-lookup"><span data-stu-id="3984e-128">After successful creation, an NetX AutoIP is started at line 098.</span></span> <span data-ttu-id="3984e-129">IP アドレス変更コールバック関数の処理を 105 行目で開始します。これは、後に生じる競合や潜在的な DHCP アドレスの解決に使用します。</span><span class="sxs-lookup"><span data-stu-id="3984e-129">The IP address change callback function processing starts at line 105, which is used to handle subsequent conflicts or possible DHCP address resolution.</span></span>

> [!NOTE]
> <span data-ttu-id="3984e-130">下の例では、ホスト デバイスがシングル ホーム デバイスであることを前提にしています。</span><span class="sxs-lookup"><span data-stu-id="3984e-130">The example below assumes the host device is a single-homed device.</span></span> <span data-ttu-id="3984e-131">マルチホーム デバイスの場合、ホスト アプリケーションで NetX AutoIP サービスの *nx_auto_ip_interface_* set を使用して、どのセカンダリ ネットワーク インターフェイスで IP アドレスを調べるかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3984e-131">For a multihomed device, the host application can use the NetX AutoIP service *nx_auto_ip_interface_* set to specify a secondary network interface to probe for an IP address.</span></span> <span data-ttu-id="3984e-132">マルチホーム アプリケーションのセットアップの詳細は『[NetX ユーザー ガイド](https://docs.microsoft.com/azure/rtos/netx/about-this-guide)』をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3984e-132">See the [NetX User Guide](https://docs.microsoft.com/azure/rtos/netx/about-this-guide) for more details on setting up multihomed applications.</span></span> <span data-ttu-id="3984e-133">ホスト アプリケーションでは、NetX API *nx_status_ip_interface_check* を使用し、AutoIP で IP アドレスを取得できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3984e-133">Note further that the host application should use the NetX API *nx_status_ip_interface_check* to verify AutoIP has obtained an IP address.</span></span>

```c
#include "tx_api.h"
#include "nx_api.h"
#include "nx_auto_ip.h"

#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD              thread_0;
NX_PACKET_POOL         pool_0;
NX_IP                  ip_0;

/* Define the AUTO IP structures for the IP instance. */

NX_AUTO_IP             auto_ip_0;

/* Define the counters used in the demo application... */

ULONG                 thread_0_counter;
ULONG                 address_changes;
ULONG                 error_counter;

/* Define thread prototypes. */
void     thread_0_entry(ULONG thread_input);
void     ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

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
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    16, 16, 1, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 128,
                                    pointer, 4096);
    pointer = pointer + 4096;

    if (status)
        error_counter++;

    /* Create an IP instance. */
    status = nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(0, 0, 0, 0),
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 4096, 1);
    pointer = pointer + 4096;

    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
        error_counter++;

    /* Create the AutoIP instance for IP Instance 0. */
    status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);
    pointer = pointer + 4096;

    /* Check AutoIP create status. */
    if (status)
        error_counter++;

    /* Start AutoIP instances. */
    status = **nx_auto_ip_start**(&auto_ip_0, 0 /*IP_ADDRESS(169,254,254,255)*/);

    /* Check AutoIP start status. */
    if (status)
        error_counter++;

    /* Register an IP address change function for IP Instance 0. */
    status = nx_ip_address_change_notify(&ip_0, ip_address_changed,
                                        (void *) &auto_ip_0);

    /* Check IP address change notify status. */
    if (status)
        error_counter++;
}

/* Define the test thread. */

void     thread_0_entry(ULONG thread_input)
{

UINT     status;
ULONG    actual_status;

    /* Wait for IP address to be resolved. */
    do
    {

        /* Call IP status check routine. */
        status = nx_ip_status_check(&ip_0, NX_IP_ADDRESS_RESOLVED,
            &actual_status, 10000);

    } while (status != NX_SUCCESS);

    /* Since the IP address is resolved at this point, the application can now fully utilize NetX! */

    while(1)
    {

        /* Increment thread 0's counter. */
        thread_0_counter++;

        /* Sleep... */
        tx_thread_sleep(10);
    }
}

void          ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address)
{

ULONG         ip_address;
ULONG         network_mask;
NX_AUTO_IP    *auto_ip_ptr;

    /* Setup pointer to auto IP instance. */
    auto_ip_ptr = (NX_AUTO_IP *) auto_ip_address;

    /* Pickup the current IP address. */
    nx_ip_address_get(ip_ptr, &ip_address, &network_mask);

    /* Determine if the IP address has changed back to zero. If so, make sure the AutoIP instance is started. */
    if (ip_address == 0)
    {

        /* Get the last AutoIP address for this node. */
        nx_auto_ip_get_address(auto_ip_ptr, &ip_address);

        /* Start this AutoIP instance. */
        nx_auto_ip_start(auto_ip_ptr, ip_address);
        }

    /* Determine if IP address has transitioned to a non local IP address. */
    else if ((ip_address & 0xFFFF0000UL) != IP_ADDRESS(169, 254, 0, 0))
    {

        /* Stop the AutoIP processing. */
        nx_auto_ip_stop(auto_ip_ptr);
    }

    /* Increment a counter. */
    address_changes++;
}
```

<span data-ttu-id="3984e-134">図 1.1 NetX での AutoIP の使用例</span><span class="sxs-lookup"><span data-stu-id="3984e-134">Figure 1.1 Example of AutoIP use with NetX</span></span>

## <a name="configuration-options"></a><span data-ttu-id="3984e-135">構成オプション</span><span class="sxs-lookup"><span data-stu-id="3984e-135">Configuration Options</span></span>

<span data-ttu-id="3984e-136">NetX AutoIP を構築するための構成オプションはいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="3984e-136">There are several configuration options for building NetX AutoIP.</span></span> <span data-ttu-id="3984e-137">以下に、すべてのオプションの一覧と、それぞれの詳細な説明を示します。</span><span class="sxs-lookup"><span data-stu-id="3984e-137">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="3984e-138">**NX_DISABLE_ERROR_CHECKING**: このオプションを有効にすると、AutoIP の基本的なエラー チェックを行いません。</span><span class="sxs-lookup"><span data-stu-id="3984e-138">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic AutoIP error checking.</span></span> <span data-ttu-id="3984e-139">通常は、アプリケーションがデバッグされた後に使用します。</span><span class="sxs-lookup"><span data-stu-id="3984e-139">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="3984e-140">**NX_AUTO_IP_PROBE_WAIT**: 最初のプローブを送信するまでの秒単位の待機時間。</span><span class="sxs-lookup"><span data-stu-id="3984e-140">**NX_AUTO_IP_PROBE_WAIT**: The number of seconds to wait before sending first probe.</span></span> <span data-ttu-id="3984e-141">既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="3984e-141">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="3984e-142">**NX_AUTO_IP_PROBE_NUM**: 送信する ARP プローブの数。</span><span class="sxs-lookup"><span data-stu-id="3984e-142">**NX_AUTO_IP_PROBE_NUM**: The number of ARP probes to send.</span></span> <span data-ttu-id="3984e-143">既定値は 3 です。</span><span class="sxs-lookup"><span data-stu-id="3984e-143">By default, this value is defined as 3.</span></span>
- <span data-ttu-id="3984e-144">**NX_AUTO_IP_PROBE_MIN**: プローブを送信してから次のプローブを送信するまでの、秒単位の最小待機時間。</span><span class="sxs-lookup"><span data-stu-id="3984e-144">**NX_AUTO_IP_PROBE_MIN**: The minimum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="3984e-145">既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="3984e-145">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="3984e-146">**NX_AUTO_IP_PROBE_MAX**: プローブを送信してから次のプローブを送信するまでの、秒単位の最大待機時間。</span><span class="sxs-lookup"><span data-stu-id="3984e-146">**NX_AUTO_IP_PROBE_MAX**: The maximum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="3984e-147">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="3984e-147">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="3984e-148">**NX_AUTO_IP_MAX_CONFLICTS**: 処理時間を延ばす基準にする AutoIP の競合数。</span><span class="sxs-lookup"><span data-stu-id="3984e-148">**NX_AUTO_IP_MAX_CONFLICTS**: The number of AutoIP conflicts before increasing processing delays.</span></span> <span data-ttu-id="3984e-149">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="3984e-149">By default, this value is defined as 10.</span></span>
- <span data-ttu-id="3984e-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: 合計競合数が基準を超過したときの、秒単位の延長時間。</span><span class="sxs-lookup"><span data-stu-id="3984e-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: The number of seconds to extend the wait period when the total number of conflicts is exceeded.</span></span> <span data-ttu-id="3984e-151">既定値は 60 です。</span><span class="sxs-lookup"><span data-stu-id="3984e-151">By default, this value is defined as 60.</span></span>
- <span data-ttu-id="3984e-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: 通知を送信するまでの、秒単位の待機時間。</span><span class="sxs-lookup"><span data-stu-id="3984e-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: The number of seconds to wait before sending announcement.</span></span> <span data-ttu-id="3984e-153">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="3984e-153">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="3984e-154">**NX_AUTO_IP_ANNOUNCE_NUM**: 送信する ARP 通知の数。</span><span class="sxs-lookup"><span data-stu-id="3984e-154">**NX_AUTO_IP_ANNOUNCE_NUM**: The number of ARP announces to send.</span></span> <span data-ttu-id="3984e-155">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="3984e-155">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="3984e-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: 通知を送信してから次の通知を送信するまでの、秒単位の待機時間。</span><span class="sxs-lookup"><span data-stu-id="3984e-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: The number of seconds to wait between sending announces.</span></span> <span data-ttu-id="3984e-157">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="3984e-157">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="3984e-158">**NX_AUTO_IP_DEFEND_INTERVAL**: 防衛通知を送信してから次の防衛通知を送信するまでの、秒単位の待機時間。</span><span class="sxs-lookup"><span data-stu-id="3984e-158">**NX_AUTO_IP_DEFEND_INTERVAL**: The number of seconds to wait between defense announces.</span></span> <span data-ttu-id="3984e-159">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="3984e-159">By default, this value is defined as 10.</span></span>