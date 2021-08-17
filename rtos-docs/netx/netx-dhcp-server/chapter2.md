---
title: 第 2 章 - Azure RTOS NetX DHCP サーバーのインストールと使用
description: この章では、Azure RTOS NetX DHCP のサーバー コンポーネントのインストール、セットアップ、使用に関するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 04cbf4c9529538c3b5db6f8045a28bbcad5861c6ce846a898fa3ba1c7d97b19f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799576"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-dhcp-server"></a>第 2 章 - Azure RTOS NetX DHCP サーバーのインストールと使用

この章では、Azure RTOS NetX DHCP のコンポーネントのインストール、セットアップ、使用に関するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品の配布パッケージ

Azure RTOS NetX DHCP サーバーは公開ソース コード リポジトリ ([https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/)) から入手できます。 このパッケージには、下に挙げるとおり、ソース ファイル 2 つと、このドキュメントを含む PDF ファイル 1 つが含まれています:

- **nx_dhcp_server.h**: NetX DHCP サーバーのヘッダー ファイル
- **nx_dhcp_server.c**: NetX DHCP サーバーの C 言語のソース ファイル
- **nx_dhcp_server.pdf**: NetX DHCP サーバーの説明書の PDF ファイル
- **demo_netx_dhcp_server.c**: NetX DHCP サーバーのデモ

## <a name="dhcp-installation"></a>DHCP のインストール

NetX DHCP サーバーを使用するには、NetX がインストールされているのと同じディレクトリに、前述の配布パッケージを丸ごとコピーします。 たとえば、NetX が " *\threadx\arm7\green*" ディレクトリにインストールされている場合は、*nx_dhcp_server.h* と *nx_dhpc_server.c* ファイルをこのディレクトリにコピーします。

## <a name="using-netx-dhcp-server"></a>NetX DHCP サーバーの使用

NetX DHCP サーバーの使用方法は簡単です。 基本的に、ThreadX と NetX を使用するためには、アプリケーションのコードにそれぞれ *tx_api.h* と *nx_api.h* をインクルードしてから *nx_dhcp_server.h* をインクルードする必要があります。 *nx_dhcp_server* をインクルードすると、このガイドで後述する DHCP 関数を、そのアプリケーションのコードで呼び出せるようになります。 また、アプリケーションをビルドするときに *nx_dhcp_server.c* をインクルードする必要があります。 このファイルは、他のアプリケーション ファイルと同様にコンパイルし、オブジェクトとしてアプリケーションのファイルと共にリンクする必要があります。 NetX DHCP サーバーの使用方法の詳細は、後述の「[NetX DHCP サーバーの要件](#requirements-of-the-netx-dhcp-server)」および「[NetX DHCP サーバーの制約](#constraints-of-the-netx-dhcp-server)」のセクションをご覧ください。

> [!NOTE]
> DHCP では NetX UDP サービスが使用されているので、DHCP を使用する前に *nx_udp_enable* を呼び出して UDP を有効にしておく必要があります。

## <a name="requirements-of-the-netx-dhcp-server"></a>NetX DHCP サーバーの要件

NetX DHCP サーバーを使用するには、UDP ソケットのポートをウェルノウン ポートの DHCP ポート 67 に割り当てる必要があります。 DHCP サーバーを作成するには、少なくとも 548 バイトのペイロードと IP、UDP、イーサネット ヘッダー (4 バイトのアライメントで合計 44 バイト) を含むパケットのプールを作成する必要があります。

サーバーとクライアントがどちらもイーサネット ハードウェア アドレスを使用することを前提にしています:

- **ハードウェアの種類**: 1
- **ハードウェア アドレス長**: 6
- **ホップ数**: 0

### <a name="multiple-client-sessions"></a>複数のクライアント セッション

NetX DHCP サーバーでは、アクティブな DHCP クライアントとその "状態" をテーブルで管理することにより、複数のクライアント セッションを処理することができます (DHCP の状態の例: INIT、BOOT、SELECTING、REQUESTING、RENEWING)。次のクライアント メッセージを受け取る前にセッションがタイムアウトした場合、クライアントが IP アドレスのリースにバインドされている場合を除いて、サーバーはクライアント セッションのデータを削除し、割り当てられていた IP アドレスを使用可能なアドレスのプールに戻します。 クライアントから複数の DISCOVER メッセージを受信した場合、サーバーはセッションの経過時間をリセットし、その IP アドレスを予約して、クライアントが後の REQUEST メッセージでそれを受け入れられるようにします。

NetX DHCP サーバーは、クライアントによる単一の状態の DHCP 要求も受け入れます。たとえば、クライアントが REQUEST メッセージしか送信しない場合が考えられます。 これは、クライアントに既に DHCP サーバーから IP アドレスのリースを割り当てられていることを前提にしています。

### <a name="setting-interface-specific-network-parameters-server-responses"></a>ネットワーク パラメーター サーバー応答をインターフェイスごとに設定する

アプリケーションでは、*nx_dhcp_set_interface_network_parameters* サービスを使用して、DHCP クライアント要求を処理するインターフェイスごとに、ルーター、サブネット マスク、DNS サーバーのパラメーターを設定できます。 設定を行わない場合、これらのパラメーターではそれぞれ、サーバーのプライマリ インターフェイスの IP ゲートウェイ、DHCP ネットワークのサブネット、DHCP サーバーの IP アドレスを既定値として使用します。

DHCP サーバーから DHCP クライアントに送信する DHCP メッセージのオプション データには、これらのパラメーターが含まれています。

### <a name="assigning-ip-addresses-to-the-client"></a>クライアントに IP アドレスを割り当てる

クライアントの DISCOVER メッセージに IP アドレスを指定する要求がない場合、DHCP サーバーは自身のプールにあるアドレスを 1 つ使用できます。 使用できる IP アドレスがサーバーにない場合は、クライアントに NACK メッセージが送信されます。

当該の IP アドレスが使用可能であり、サーバーの IP アドレスのデータベースに存在する場合、NetX DHCP サーバーによって、クライアントの REQUEST メッセージで指定された IP アドレスが割り当てられます。 アプリケーションでは、*nx_dhcp_create_server_ip_address_list* サービスを使用して、DHCP クライアントに割り当てることができるサーバーの IP アドレスのリストが作成されます。 要求された IP アドレスがサーバーに存在しないか別のホストに割り当てられている場合は、クライアントに NACK メッセージが送信されます。

クライアント要求を受信すると、DHCP サーバーは、DHCP メッセージのクライアント MAC アドレス フィールドにあるクライアントの MAC アドレス使用して、クライアントを一意に識別します。 クライアントが MAC アドレスを変更するか別のサブネットに移動した場合、そのクライアントはサーバーに RELEASE メッセージを送信し、使用可能なアドレスのプールに IP アドレスを戻し、INIT 状態の新たな IP アドレスを要求する必要があります。

詳しくは「**システムの簡単な例**」セクションの図 1.1 をご覧ください。 DHCP サーバー インスタンスに保存される IP アドレスの数は、DHCP サーバー制御ブロックにあるサーバー アドレスの配列で指定された数に限定され、構成可能なオプション NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE によって指定されます。

### <a name="ip-address-lease-times"></a>IP アドレスのリース時間

要求されたクライアントのリース時間が、構成可能なオプション NX_DHCP_DEFAULT_LEASE_TIME で指定されているサーバーの既定のリース時間より短い場合も、そのリース時間の要求は DHCP サーバーによって受け入れられます。 リース時間が無期限 (0xFFFFFFFF) である場合を除き、クライアントに割り当てられる更新時間と再バインド時間はそれぞれリース時間の 50% と 85% です。リース時間が無期限である場合は、更新時間と再バインド時間も無期限に設定されます。

### <a name="dhcp-server-timeouts"></a>DHCP サーバーのタイムアウト

DHCP サーバーには、セッションが終了していない場合に次の DHCP クライアントメッセージを待つための、ユーザーが構成可能なセッション タイムアウトのオプション NX_DHCP_CLIENT_SESSION_TIMEOUT があります。 サーバーがクライアントから次のメッセージを受け取ると、それが以前送信されたメッセージと同じかどうかにかかわらず、タイムアウトのタイマーがリセットされます。

### <a name="internal-error-handling"></a>内部エラーの処理

DHCP サーバーは *nx_dhcp_listen_for_messages* 関数で DHCP クライアント パケットを受信して処理します。 パケットが無効である場合、または DHCP サーバーで内部エラーが発生した場合、この *nx_dhcp_listen_for_messages* 関数は現在の DHCP クライアント パケットの処理を中止してエラー ステータスを返します。 DHCP サーバー スレッドは、ThreadX スケジューラの制御を一時的に放棄し、その後でこの関数を呼び出して次の DHCP クライアント メッセージを受信します。 現在のリリースは *nx_dhcp_listen_for_messages* がエラー ステータスを返した場合のログをサポートしていません。

### <a name="option-55-parameter-request-list"></a>オプション 55: パラメーター要求リスト

NetX DHCP サーバーは、クライアントに返送する OFFER および DHCPACK メッセージのパラメーター要求オプション (55) のリストに読み込むオプションを含めるように構成する必要があります。 クライアント ネットワークに不可欠な構成データをこれらのオプションに含める必要があります。既定のオプションはルーターの IP アドレス、サブネット マスク、DNS サーバーです。 オプションのリストは、スペース区切り形式で、ユーザーが構成可能な NX_DHCP_DEFAULT_SERVER_OPTION_LIST に指定されます。 このリストに指定するオプションの数は、同じくユーザーが指定する NX_DHCP_DEFAULT_OPTION_LIST_SIZE と一致する必要があります。

## <a name="constraints-of-the-netx-dhcp-server"></a>NetX DHCP サーバーの制約

### <a name="dhcp-messages"></a>DHCP メッセージ

NetX DHCP サーバーは、IP アドレスをクライアントに割り当てる際、その IP アドレスがネットワーク上の他の場所に割り当てられていないことを確認しません。 複数の DHCP サーバーがある場合も同様です。 *RFC 2131 によると、IP アドレスがネットワーク上で一意であることを確認するのはクライアントです* (たとえばアドレスに ping を打つ)。 そうしない場合、サーバーは、サーバーのデータベースを更新するための IP アドレスを含む DECLINE メッセージをクライアントから受信するべきです。

NetX DHCP サーバーは FORCE_RENEW メッセージを発行しません。 IP アドレスのリースを更新するかどうかは DHCP クライアントに任されています。 ただし、DHCP サーバーは、自身のデータベースにあるすべての割り当て済み IP アドレスの残り時間を監視します。 IP アドレスのリース期限が切れると、その IP アドレスは使用可能な IP アドレスのプールに戻されます。 そのため、IP アドレスのリースを能動的に更新または再バインドするかどうかはクライアントに任されています。

クライアントに IP アドレスのリースが割り当てられる ("バインド" される) と (または既存のリースが更新されると)、セッションのデータはすぐに削除されます。 クライアントのパケットが偽りである場合、または応答間にクライアントがタイムアウトした場合、セッションのデータは削除されます。

### <a name="saving-data-between-reboots"></a>再起動間にデータを保存する

NetX DHCP サーバーは、DHCP 要求パラメーターなどのクライアントのデータをクライアント レコード テーブルに保存します。 このテーブルは不揮発性メモリには保存されないため、DHCP サーバー ホストを再起動する必要がある場合、そうした情報は再起動間で保存されません。

NetX DHCP サーバーは IP アドレスのリースのデータを IP アドレス テーブルに保存します。 このテーブルは不揮発性メモリには保存されないため、DHCP サーバー ホストを再起動する必要がある場合、そうした情報は再起動間で保存されません。

### <a name="relay-agents"></a>リレー エージェント

ネットワーク外の DHCP 要求をサポートしていないため、NetX DHCP サーバーの "リレー エージェント" フィールドは、すべて 0 の IP アドレスになっています。

## <a name="small-example-system"></a>システムの簡単な例

NetX DHCP サーバーを簡単に使用する例を下の図 1.1 で説明しています。 この例では、DHCP のインクルード ファイル *nx_dhcp_server.h* が 5 行目に来ています。 DHCP サーバー スレッド、IP スレッド、およびテスト スレッドのスタック サイズは 7 から 13 行ですべて指定します。

最初に 57 行目の *test_thread_entry* 関数で、DHCP サーバーの停止、再起動、その後の削除を行うための、テスト スレッドのオプションのタスクを作成します。 DHCP サーバー制御ブロック "*dhcp_server*" は、20 行目でグローバル変数として定義されています。 サーバーのパケット プールは、ペイロードが少なくとも標準の DHCP メッセージと同じ大きさ (548 バイト + IP と UDP ヘッダー) のパケットで作成されることに注意してください。 DHCP サーバー用の IP インスタンスが正常に作成された後、アプリケーションによって DHCP サーバーが作成されます (96 行目)。 次に、アプリケーションによって、そのサーバーの IP インスタンスで UDP が有効にされます。 DHCP サーバーを起動する前に、*nx_dhcp_create_server_ip_address_list* サービスを使用して、使用可能な IP アドレスのリストが作成されます (137 行目)。 *nx_dhcp_set_interface_network_parameters* サービスを使用してネットワーク構成パラメーターが設定され (138 行目)、アプリケーションによって *nx_dhcp_server_start* が呼び出されると DHCP サーバーのサービスが使用可能になります (141 行目)。 テスト スレッドのタスクでは、DHCP サーバーの停止と再起動を例示しています。

```c
/* This is a small demo of NetX DHCP Server for the high-performance NetX TCP/IP stack. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nx_dhcp_server.h"

#define     DEMO_TEST_STACK_SIZE       2048
#define     DEMO_SERVER_STACK_SIZE     2048
#define     SERVER_IP_ADDRESS_LIST     "192.168.2.10 192.168.2.11 192.168.2.12"
#define     PACKET_PAYLOAD             1000
#define     PACKET_POOL_SIZE           (PACKET_PAYLOAD * 10)
#define     SERVER_IP_THREAD_STACK     2048

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD          test_thread;
NX_PACKET_POOL     server_pool;
NX_IP              server_ip;
NX_DHCP_SERVER     dhcp_server;

/* Define the counters used in the demo application... */

ULONG             state_changes;

/* Define thread prototypes. */

void     test_thread_entry(ULONG thread_input);
void     nx_etherDriver_mcf5485(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
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

    /* Create the test thread. */
    status = tx_thread_create(&test_thread, "test thread", test_thread_entry, 0,
                pointer, TEST_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_DONT_START);

    if (status)
    {
        printf("Error with DHCP test thread create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create the DHCP Server packet pool. */
    status = nx_packet_pool_create(&server_pool, "NetX Main Packet Pool",
                                PACKET_PAYLOAD, pointer, PACKET_POOL_SIZE);
                                pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {
        printf("Error with DHCP server packet pool create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server IP instance. */
    status = nx_ip_create(&server_ip, "NetX DHCP Server IP", NX_DHCP_SERVER_IP_ADDRESS,
                        0xFFFFFF00UL, &server_pool, nx_etherDriver_mcf5485, pointer,
                        SERVER_IP_THREAD_STACK, 1);

    pointer = pointer + DEMO_IP_THREAD_STACK;

    /* Check for IP create errors. */
    if (status)
    {
        printf("Error with DHCP server IP task create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server instance. */
    status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE,"DHCP Server", &server_pool);

    if (status)
    {
        printf("Error with DHCP server create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_SERVER_STACK_SIZE;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status = nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
    {
        printf("Error with ARP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable UDP traffic. */
    status = nx_udp_enable(&server_ip);

    /* Check for UDP enable errors. */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable ICMP to enable the ping utility. */
    status = nx_icmp_enable(&server_ip);

    /* Check for errors. */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
    }

    status = nx_dhcp_create_server_ip_address_list(&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);
    status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                        NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                        IP_ADDRESS(10,0,0,1));

    /* Start the DHCP Server. */
    status = nx_dhcp_server_start(&dhcp_server);

    tx_thread_resume(&test_thread);
}

/* Define the test thread. */
void     test_thread_entry(ULONG thread_input)
{

UINT     status;
UINT     keep_spinning;

    /* Just let the test thread be idle till we're ready to shut things down. */
    keep_spinning = 1;
    while(keep_spinning)
    {
        tx_thread_sleep(300);
    }

    printf("Stopping the server...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(500);

    printf("Starting the server...\n");
    status = nx_dhcp_server_start(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server start. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(600);

    printf("Stopping the server for good...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(200);

    printf("Deleting the server...\n");
    status = nx_dhcp_server_delete(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server delete. Status 0x%x\r\n", status);
        return;
    }
}
```

図 1.1 NetX DHCP サーバー アプリケーションの例

## <a name="configuration-options"></a>構成オプション

NetX DHCP サーバーを構築するための構成オプションはいくつかあります。 次のリストでは各オプションを詳しく説明しています:  
  
- **NX_DISABLE_ERROR_CHECKING**: このオプションを使用すると、DHCP エラーの基本的な確認作業が停止されます。 通常、アプリケーションのデバッグ後に使用します。  
- **NX_DHCP_SERVER_THREAD_PRIORITY**: このオプションを使用すると、DHCP サーバー スレッドの優先度が指定されます。 既定では、この値により DHCP スレッドは優先順位 2 で実行するように指定されます。
- **NX_DHCP_TYPE_OF_SERVICE**: このオプションを使用すると、DHCP UDP 要求に必要なサービスの種類が指定されます。 既定では、この値は通常の IP パケット サービスを示す NX_IP_NORMAL に定義されています。
- **NX_DHCP_FRAGMENT_OPTION**: DHCP UDP 要求の断片化を有効にします。 既定値は、UDP 断片化を無効にする NX_DONT_FRAGMENT です。
- **NX_DHCP_TIME_TO_LIVE**: パケットが通過できるルーターの数を指定します。この数を超えるとパケットは破棄されます。 既定値は 0x80 です。
- **NX_DHCP_QUEUE_DEPTH**: DHCP サーバーのソケットに保持できるパケットの数を指定します。この数を超えるとキューをフラッシュします。 既定値は 5 です。
- **NX_DHCP_PACKET_ALLOCATE_TIMEOUT**: 自身のパケット プールからパケットが割り当てられるのを待機する NetX DHCP サーバーのタイムアウト時間をタイマー ティック単位で指定します。 既定値は NX_IP_PERIODIC_RATE に設定されています。
- **NX_DHCP_SUBNET_MASK**: DHCP クライアントの構成で使用するサブネット マスクです。 既定値は 0xFFFFFF00 に設定されています。
- **NX_DHCP_FAST_PERIODIC_TIME_INTERVAL**: DHCP サーバーの高速タイマーがセッションの残り時間を確認し、タイムアウトしたセッションを処理するためのタイムアウト時間です。タイマー ティック単位です。
- **NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL**: DHCP サーバーの低速タイマーが IP アドレスのリースの残り時間を確認し、タイムアウトしたリースを処理するためのタイムアウト時間です。タイマー ティック単位です。
- **NX_DHCP_CLIENT_SESSION_TIMEOUT**: DHCP サーバーが次の DHCP クライアント メッセージの受信を待つ際のタイムアウト時間です。タイマー ティック単位です。
- **NX_DHCP_DEFAULT_LEASE_TIME**: DHCP クライアントに割り当てる IP アドレスの秒単位のリース時間です。クライアントに割り当てる更新時間と再バインド時間を計算する際の基準でもあります。 既定値は 0xFFFFFFFF (無期限) です。
- **NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE**: クライアントに割り当てることができる IP アドレスを保持する DHCP サーバーの配列のサイズです。 既定値は 20 です。
- **NX_DHCP_CLIENT_RECORD_TABLE_SIZE**: クライアントのレコードを保持する DHCP サーバーの配列のサイズです。 既定値は 50 です。
- **NX_DHCP_CLIENT_OPTIONS_MAX**: パラメーター要求リストにあるすべてのオプションを現在のセッションに保持するための DHCP クライアント インスタンス上の配列のサイズです。 既定値は 12 です。
- **NX_DHCP_OPTIONAL_SERVER_OPTION_LIST**: 現在の DHCP クライアントに渡す DHCP サーバーの既定のオプションのリストをパラメーター要求リストに保持するバッファーです。 既定値は "1 3 6" です。
- **NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE**: DHCP サーバーの既定のオプションのリストを保持する配列のサイズです。 既定値は、3 です。
- **NX_DHCP_SERVER_HOSTNAME_MAX**: サーバーのホスト名を保持するバッファーのサイズです。 既定値は 32 です。
- **NX_DHCP_CLIENT_HOSTNAME_MAX**: DHCP サーバーの現在のクライアント セッションにクライアント ホスト名を保持するバッファーのサイズです。 既定値は 32 です。
