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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-autoip"></a>第 2 章 - Azure RTOS NetX Duo AutoIP のインストールと使用

このチャプターでは、Azure RTOS NetX Duo AutoIP コンポーネントのインストール、セットアップ、使用に関するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品の配布

Azure RTOS NetX AutoIP は、[https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) のパブリック ソース コード リポジトリから入手できます。 パッケージの内容は、次に挙げるソース ファイル 3 つ、インクルード ファイル 1 つ、このドキュメントを含む PDF ファイルです。

- **nx_auto_ip.h**: NetX AutoIP のヘッダー ファイル
- **nx_auto_ip.c**: NetX AutoIP の C 言語のソース ファイル
- **demo_netx_auto_ip.c**: NetX AutoIP Demo の C 言語のソース ファイル
- **nx_auto_ip.pdf**: NetX AutoIP の説明書の PDF ファイル

## <a name="autoip-installation"></a>AutoIP のインストール

NetX AutoIP を使用するには、NetX がインストールされているのと同じディレクトリに、前述の配布パッケージを丸ごとコピーします。 たとえば、NetX がディレクトリ " *\threadx\arm7\green*" にインストールされている場合は、*nx_auto_ip.h*、*nx_auto_ip.c*、*demo_netx_auto_ip.c* の各ファイルをこのディレクトリにコピーします。

## <a name="using-autoip"></a>AutoIP を使用する

NetX AutoIP の使用方法は簡単です。 基本的に、ThreadX と NetX を使用するためには、アプリケーションのコードに *tx_api.h* と *nx_api.h* をインクルードしてから *nx_auto_ip.h* をインクルードする必要があります。 *nx_auto_ip* をインクルードすると、このガイドで後述する AutoIP の関数を、アプリケーションのコードで呼び出せるようになります。 アプリケーションのビルド時に *nx_auto_ip.c* もインクルードする必要があります。 これらのファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、そのオブジェクト フォームをアプリケーションのファイルと一緒にリンクする必要があります。 NetX AutoIP の使用に必要なものはこれですべてです。

> [!NOTE]
> AutoIP は NetX ARP サービスを利用するので、AutoIP を使用する前に *nx_arp_enable* を呼び出して ARP を有効にしておく必要があります。

## <a name="small-example-system"></a>小規模システムの例

NetX AutoIP の使用がいかに簡単であるかを示す例について、下の図 1.1 で説明しています。 この例では、AutoIP のインクルード ファイル *nx_auto_ip.h* を 002 行目に置きます。 次に、090 行目の "*tx_application_define*" で NetX AutoIP インスタンスを作成します。 NetX AutoIP 制御ブロック auto_ip_0 は、015 行目であらかじめグローバル変数として定義してあります。 作成を完了した後、098 行目で NetX AutoIP を開始します。 IP アドレス変更コールバック関数の処理を 105 行目で開始します。これは、後に生じる競合や潜在的な DHCP アドレスの解決に使用します。

> [!NOTE]
> 下の例では、ホスト デバイスがシングル ホーム デバイスであることを前提にしています。 マルチホーム デバイスの場合、ホスト アプリケーションで NetX AutoIP サービスの *nx_auto_ip_interface_* set を使用して、どのセカンダリ ネットワーク インターフェイスで IP アドレスを調べるかを指定できます。 マルチホーム アプリケーションのセットアップの詳細は『[NetX ユーザー ガイド](https://docs.microsoft.com/azure/rtos/netx/about-this-guide)』をご覧ください。 ホスト アプリケーションでは、NetX API *nx_status_ip_interface_check* を使用し、AutoIP で IP アドレスを取得できたかどうかを確認する必要があります。

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

図 1.1 NetX での AutoIP の使用例

## <a name="configuration-options"></a>構成オプション

NetX AutoIP を構築するための構成オプションはいくつかあります。 以下に、すべてのオプションの一覧と、それぞれの詳細な説明を示します。

- **NX_DISABLE_ERROR_CHECKING**: このオプションを有効にすると、AutoIP の基本的なエラー チェックを行いません。 通常は、アプリケーションがデバッグされた後に使用します。
- **NX_AUTO_IP_PROBE_WAIT**: 最初のプローブを送信するまでの秒単位の待機時間。 既定値は 1 です。
- **NX_AUTO_IP_PROBE_NUM**: 送信する ARP プローブの数。 既定値は 3 です。
- **NX_AUTO_IP_PROBE_MIN**: プローブを送信してから次のプローブを送信するまでの、秒単位の最小待機時間。 既定値は 1 です。
- **NX_AUTO_IP_PROBE_MAX**: プローブを送信してから次のプローブを送信するまでの、秒単位の最大待機時間。 既定値は 2 です。
- **NX_AUTO_IP_MAX_CONFLICTS**: 処理時間を延ばす基準にする AutoIP の競合数。 既定値は 10 です。
- **NX_AUTO_IP_RATE_LIMIT_INTERVAL**: 合計競合数が基準を超過したときの、秒単位の延長時間。 既定値は 60 です。
- **NX_AUTO_IP_ANNOUNCE_WAIT**: 通知を送信するまでの、秒単位の待機時間。 既定値は 2 です。
- **NX_AUTO_IP_ANNOUNCE_NUM**: 送信する ARP 通知の数。 既定値は 2 です。
- **NX_AUTO_IP_ANNOUNCE_INTERVAL**: 通知を送信してから次の通知を送信するまでの、秒単位の待機時間。 既定値は 2 です。
- **NX_AUTO_IP_DEFEND_INTERVAL**: 防衛通知を送信してから次の防衛通知を送信するまでの、秒単位の待機時間。 既定値は 10 です。
