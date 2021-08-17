---
title: 第 2 章 - Azure RTOS NetX Duo DHCPv6 クライアントのインストールと使用
description: この章では、Azure RTOS NetX Duo DHCPv6 クライアント コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 481e29cc674edfa7e437e8e14253172b89aeae6856114192f4ca5b35717c91e0
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791535"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dhcpv6-client"></a>第 2 章 - Azure RTOS NetX Duo DHCPv6 クライアントのインストールと使用

この章では、Azure RTOS NetX Duo DHCPv6 クライアント コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品の配布

NetX Duo DHCPv6 クライアントは [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) で入手できます。 このパッケージにはソース ファイル 2 つと、このドキュメントを含む PDF ファイル 1 つが含まれています。次のとおりです。

- **nxd_dhcpv6_client.h** NetX Duo DHCPv6 クライアントのヘッダー ファイル

- **nxd_dhcpv6_client.c** NetX Duo DHCPv6 クライアントのソース コード

- **demo_netxduo_dhcpv6_client.c** NetX Duo DHCPv6 クライアントのセットアップをデモンストレーションするサンプル プログラム

- **nxd_dhcpv6_client.pdf** NetX Duo DHCPv6 クライアントの説明 PDF

## <a name="netx-duo-dhcpv6-client-installation"></a>NetX Duo DHCPv6 クライアントのインストール

NetX Duo DHCPv6 クライアント API を使用するには、NetX Duo がインストールされているのと同じディレクトリに前述のディストリビューション全体をコピーします。 たとえば、NetX Duo がディレクトリ "*\threadx\arm7\green*" にインストールされている場合、*nxd_dhcpv6_client.h* と *nxd_dhpcv6_client.c* ファイルをこのディレクトリにコピーできます。

## <a name="using-the-netx-duo-dhcpv6-client"></a>NetX Duo DHCPv6 クライアントの使用

DHCPv6 クライアント、ThreadX、NetX Duo サービスを使用するには、アプリケーション コードで、*tx_api.h* と *nx_api.h* をインクルードした後に、*nxd_dhcpv6_client.h* をインクルードする必要があります。 *nxd_dhcpv6_client.c* をプロジェクトで他のアプリケーション ファイルと同じ方法を使用してコンパイルする必要があり、そのオブジェクト形式をアプリケーションのファイルと共にリンクする必要があります。

### <a name="span-classunderlineclient-dhcp-unique-identifier-duidspan"></a><span class="underline">クライアントの DHCP 一意識別子 (DUID)</span>

クライアントの DUID により、ネットワーク上の各クライアントが一意に定義されます。 アプリケーションで、サーバーに IPv6 アドレスを要求する前に、クライアント DUID を作成する必要があります。 クライアント DUID は、サーバーへのすべてのメッセージに自動的に組み込まれます。 DUID を作成するには、アプリケーションでサービス *nx_dhcpv6_create_client_duid* を呼び出します。
```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT duid_type, 
                                  UINT hardware_type, ULONG time);
```

アプリケーションでこのサービスを呼び出し、DUID の種類 (リンク レイヤーのみ、またはリンク レイヤーと時間) を指定します。 リンク レイヤーと時間の DUID の場合、時間入力が指定されていない場合、このサービスにより時間フィールドが提供されます。

デバイスを再起動した後で、前に割り当てた IPv6 アドレス リースを使用したい場合は、アプリケーションで、IPv6 アドレスを割り当てたときに使用したものと同じクライアント DUID を作成する必要があります。 リンク レイヤー クライアントの DUID を作成するために必要なものは、リンク レイヤー アドレスだけです。 デバイスがリンク レイヤー アドレスにアクセスできる場合、これには以前の不揮発性メモリ記憶域は必要ありません。 時間の種類の DUID の場合は、前の DUID の作成で使用したものと同じ時間データにアプリケーションでアクセスできる必要があり、これには不揮発性メモリが必要です。 安定した記憶域がないクライアントでは、時間の種類の DUID を使用できません。

### <a name="span-classunderlineclient-identity-association-for-non-temporary-addresses-ianaspan"></a><span class="underline">非一時アドレスのクライアント ID 関連付け (IANA)</span>

IPv6 アドレスを要求する前に、IANA と必要に応じて 1 つ以上の IA アドレスを、アプリケーションで作成する必要があります。 これを行うには、アプリケーションで *nx_dhcpv6_create_client_iana* サービスを呼び出します。 IA アドレス オプションを作成するには、アプリケーションで *nx_dhcpv6_add_client_ia* サービスを呼び出し、サーバーへのヒントとして要求する IPv6 アドレスと有効期間の値を指定します。

IANA とその IA で累積的に、クライアントの IPv6 アドレス割り当てパラメーターを定義します。

Dhcpv6 クライアントを開始する前に、DHCPv6 クライアント アプリケーションで *nx_dhcpv6_create_client_iana* サービスを使用して IANA を作成します。

```C
UINT    nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                     UINT IA_ident, ULONG T1, ULONG T2);
```

また、DHCPv6 クライアントを開始する前に、*nx_dhcpv6_create_client_ia* サービスと要求する IPv6 アドレスを使用して、1 つ以上の IA を作成する必要があります。

```C
UINT    nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                                NXD_ADDRESS *ipv6_address, 
                                ULONG preferred_lifetime, 
                                ULONG valid_lifetime);
```

> [!NOTE]
> アプリケーションで作成する IA アドレスの数は、NX_DHCPV6_MAX_IA_ADDRESS パラメーターを超えることはできません (既定値は 1)。

NetX Duo DHCPv6 クライアントでは従来の DHCPv6 クライアント アプリケーション用の *nx_dhcpv6_create_client_ia* がサポートされており、これは *nx_dhcpv6_add_client_ia* と同じですが、開発者には *nx_dhcpv6_add_client_ia* サービスを使用することをお勧めします。

これらのサービスについては、この章の「小さなシステムの例」で説明します。

### <a name="span-classunderlinenon-volatile-memory-considerations-to-reuse-ianas-and-iasspan"></a><span class="underline">IANA と IA の再利用に関する不揮発性メモリの考慮事項</span>

アプリケーションで再起動時に同じアドレスを使用する場合は、IANA のパラメーター T1 と T2 および IANA 識別子を、不揮発性メモリに保存する必要があります。 また、アプリケーションでは、その IPv6 アドレスが含まれる IA も不揮発性メモリに保存する必要があります。

シャットダウンする場合は、割り当てられた IPv6 アドレスのリースにアプリケーションがバインドされてからの経過時間も、不揮発性メモリに格納する必要があります。 これを行うには、DHCPv6 クライアントを停止する前に *nx_dhcpv6_get_time_accrued* サービスを呼び出します。

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, 
                                ULONG *time_accrued);
```

再起動後に DHCPv6 クライアントの停止から再起動までの時間間隔を追跡する独立したクロックがアプリケーションにあるとすると、停止する前に IPv6 リースで発生した時間に、その経過時間を追加します。 次の nv_time 入力のように、IPv6 リースにバインドされた経過時間の合計を使用して、クライアント スレッ ドタスクを開始します。

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr, ULONG nv_time);
```

この時点から、DHCPv6 クライアントのスレッド タスクによって、リースを更新するタイミングを把握するための、IPv6 リースで経過した時間の監視が引き継がれます。

### <a name="span-classunderlinesetting-dhcpv6-option-dataspan"></a><span class="underline">DHCPv6 オプション データの設定</span>

IPv6 リースを要求する前に、DNS サーバーやタイム サーバーなどの他のネットワーク パラメーター データを、アプリケーションで要求できます。 これらのパラメーターの一部には、特定のサービスがあります。 次に例を示します。

```C
UINT  nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT enable)

UINT  nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr, 
                                           UINT enable);
```

### <a name="span-classunderlineinitiating-the-ipv6-address-requestspan"></a><span class="underline">IPv6 アドレス要求の開始</span>

アプリケーションで時間入力として 0 を使用して *nx_dhcpv6_start* サービスを呼び出すことにより、DHCPv6 クライアント スレッドを開始します。 DHCPv6 プロトコルによる IPv6 アドレスの要求を開始するため、アプリケーションで *nx_dhcpv6_request_solicit* を呼び出します。

前に割り当てられた IPv6 リースをアプリケーションで使用する場合は、時間入力を 0 以外にして *nx_dhcpv6_start* を呼び出します。 *nx_dhcpv6_request_solicit* は呼び出さないでください。

その後、アプリケーションで行う必要があることは何もなく、IPv6 アドレスを更新または再バインドするタイミングは、DHCPv6 クライアントによって自動的に監視されます。

## <a name="small-example-system"></a>小さなシステムの例

NetX Duo DHCPv6 クライアントを簡単に使用できることを、DHCPv6 クライアントと仮想 "RAM" ドライバーを使用する次の小さな例で説明します。 このデモのデバイスは、物理ネットワーク インターフェイスを 1 つだけ備えているものとします。

*tx_application_define* によって、DHCPv6 メッセージを送信するための DHCPv6 クライアント用のパケット プールが作成されます。 また、アプリケーション スレッドと IP インスタンスも作成されます。 次に、IP で UDP と ICMP が有効にされます (130 - 148 行目)。 次に、状態変更 (*dhcpv6_state_change_notify*) とサーバー エラー (*dhcpv6_server_error_handler*) のコールバック関数を使用して、DHCPv6 クライアントが作成されます (151 行目)。

クライアント スレッド エントリ関数 *thread_client_entry* において、リンク ローカル アドレスを使用してクライアント IP が設定され、IPv6 および ICMPv6 サービスに対して有効にされます (202 - 217 行目)。 DHCPv6 クライアントを開始する前に、アプリケーションでクライアント DUID、IANA オプション、IA アドレス オプションが作成されます (219 - 303 行目)。 クライアントで IPv6 アドレスと有効な推奨有効期間をサーバーに要求する場合、IA アドレス オプションは省略可能です。 要求した IPv6 アドレスまたはリース時間は、サーバーによって許可される場合と許可されない場合があります。 アプリケーションでは、さらに多くの IA オプションを追加して複数のグローバル アドレスに割り当てることができます (最大 NX_DHCPV6_MAX_IA_ADDRESS)。

最後に、アプリケーションでさまざまなオプションを設定し、DHCPv6 サーバーへのメッセージでネットワーク パラメーターを要求します。 *nx_dhcpv6_start* を呼び出すことによって DHCPv6 クライアント タスクが開始され (306 行目)、*nx_dhcpv6_request_solicit* の呼び出しによって実際の DHCPv6 プロトコルが SOLICIT が状態で開始されます (317 行目)。 その後は、DHCPv6 クライアントにより、アドレスにバインドされるかエラーが発生するまで、DHCPv6 プロトコルによるクライアントの状態の昇格が自動的に処理されます。 この間、アプリケーションは、プロトコルが完了するまで、および IP インスタンスが重複アドレス検出 (DAD) 用に構成されている場合 (既定の構成) は DAD も完了するまで、待機します。

tx_thread_sleep の呼び出しの後、アプリケーションにおいて、状態変更コールバックで設定されたグローバル パラメーターを調べて、DHCPv6 クライアント タスクによる IPv6 リースの割り当てが成功したかどうかを確認し、成功した場合は、DAD による一意性のチェックが成功したかどうかを確認します。 これは、状態変更とサーバー エラーのコールバック関数で設定されたカウンターを使用して行います。 アプリケーションで、アドレスの割り当てが失敗したことを示す address_not_assigned、address_expired、server_errors のゼロ以外のカウントをポーリングします。 bound_addresses のカウントがゼロ以外 (少なくとも 1 つのアドレスが正常に割り当てられている) の場合は、address_failed_dad が DAD チェック失敗を示す 0 以外かどうかを調べます。 状態変更とサーバー エラーのコールバックの説明は次のとおりです。

状態変更コールバック *dhcpv6_state_change_notify* によって、DHCPv6 クライアントの以前と現在の状態が調べられ、クライアントが有効なサーバー応答を受信したかどうかが確認されます。

  - *dhcpv6_state_change_notify* により、SOLICIT から INIT に直接遷移したかどうかが調べられ、そうである場合は、DHCPv6 クライアントがサーバーから応答を受信していないことを示すカウンターが増分されます。

次に、*dhcpv6_state_change_notify* によって、クライアントが 1 つまたは複数の IPv6 アドレスに割り当てられた (バインドされた) かどうかがチェックされます。

  - 新しい状態が BOUND の場合、クライアントにバインドされたアドレスのカウンターが増分されます。
    
また、*dhcpv6_state_change_notify* により、失敗した DAD チェックも確認されます。

  - 状態が DECLINE から INIT に遷移した場合は、DHCPv6 クライアントで、割り当てられたアドレスの 1 つに対する DAD チェックが失敗しており、失敗したアドレス割り当ての数が増分されます。
    
この例での *dhcpv6_state_change_notify* による最後のチェックは、DAD チェックに合格した、正常に割り当てられたアドレスでの、更新または再バインドの失敗に関するものです。

  - 状態が REBIND から INIT に変化している場合、クライアントは RENEW または REBIND 要求に対する応答を取得しておらず、*dhcpv6_state_change_notify* によって有効期限切れのアドレスの数が増分されます。

サーバーからエラー状態を受信したことが DHCPv6 クライアント タスクによって通知された場合、*dhcpv6_server_error_handler* によってサーバー エラーの数が増分されます。

すべてが正常に行われた場合は、アプリケーションによって DHCPv6 クライアントに対してリース時間などのアドレス データの照会が行われます。 *nx_dhcpv6_get_valid_ip_address_count* サービスを呼び出すことによって、有効な (正常に割り当てられた) アドレスの数が取得され、*nx_dhcpv6_get_iana_lease_time* を呼び出すことによって、IANA の更新時間 (割り当てられているすべての IA アドレスに適用されます) が取得されます (372 - 392 行目)。 次に、DHCPv6 クライアントに対し、アドレス インデックスにより IPv6 アドレスとリース時間の各 IA オプションの照会が行われます。

一部の DHCPv6 クライアント サービス (*nx_dhcpv6_get_lease_time_data、nx_dhcpv6_get_IP_address*) は、入力としてアドレス インデックスを必要とせず、プライマリ クライアント グローバル アドレスの DHCPv6 パラメーターを返します。 これは、単一のグローバル IPv6 アドレスを使用するクライアントで *nx_dhcpv6_get_valid_ip_address_lease_time* を呼び出すときに適しています (384 行目)。

DHCPv6 クライアント構成 NX_DHCPV6_CLIENT_RESTORE_STATE を使用すると、システムが再起動された後で、以前に作成されたバインド済み状態の DHCPv6 クライアントを復元できます。 システムが再起動されたときは *nx_dhcpv6_client_get_record* を呼び出して、DHCPv6 クライアント レコードを取得し (434 行目)、システムの電源が入れられた後は *nx_dhcpv6_client_restore_record* を呼び出して、DHCPv6 クライアント レコードを格納します (525 行目)。

その後、アプリケーションにより、*nx_dhcpv6_request_release* サービスを使用して、割り当てられたアドレスが解放されます (552 行目)。 アプリケーションを再起動するには、*nx_dhcpv6_client_stop* サービスを使用して DHCPv6 クライアントを停止し (567 行目)、DHCPv6 クライアントによって構成された IP インスタンスに登録されているすべての IPv6 アドレスをクリアします。 これを行うには、*nx_dhcpv6_reinitialize* を呼び出します (578 行目)。 次に、前と同じように、*nx_dhcpv6_start* および *nx_dhcpv6_request_solicit* サービスを使用して、DHCPv6 クライアント タスクを再起動します。

*nx_dhcpv6_delete* を呼び出すと、DHCPv6 クライアントが削除されます (626 行目)。 DHCPv6 クライアント用に作成されたパケットプールは、IP インスタンスでも使用されているため、削除されないことに注意してください。 そうではなく、それ以上使用されない場合は、NetX Duo の *nx_packet_pool_delete* サービスを使用して、パケット プールを削除する必要があります。

```C
/* This is a small demo of the NetX Duo DHCPv6 Client for the high-performance NetX Duo stack. */

#include    <stdio.h>
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcpv6_client.h"

#ifdef FEATURE_NX_IPV6
#define     DEMO_STACK_SIZE         2048

/* Set the client address, and request these address from DHCPv6 Server. */
/*
#define     NX_DHCPV6_REQUEST_IA_ADDRESS
*/

/* Set the list of DHCPv6 option data (timezone, DNS server, timer server, domain name)to get from the DHCPv6 server. */

#define     NX_DHCPV6_REQUEST_OPTION


/* Add the fully qualified domain name to request whether the DHCPv6 server SHOULD or SHOULD NOT perform the AAAA RR or DNS updates. */

#define     NX_DHCPV6_REQUEST_FQDN_OPTION


/* Define the ThreadX and NetX object control blocks... */

NX_PACKET_POOL          pool_0;
TX_THREAD               thread_client;
NX_IP                   client_ip;

/* Define the Client and Server instances. */

NX_DHCPV6               dhcp_client;

/* Define the error counter used in the demo application... */
ULONG                   error_counter;
CHAR                    *pointer;

/* Define thread prototypes. */
void    thread_client_entry(ULONG thread_input);

/***** Substitute your ethernet driver entry function here *********/
extern VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Declare DHCPv6 Client callbacks */
VOID dhcpv6_state_change_notify(NX_DHCPV6 *dhcpv6_ptr, UINT old_state, UINT new_state);
VOID dhcpv6_server_error_handler(NX_DHCPV6 *dhcpv6_ptr, UINT op_code, UINT status_code, UINT message_type);

/* Set up globals for tracking changes to DHCPv6 Client from callback services. */
UINT state_changes = 0;
UINT address_expired = 0;
UINT address_failed_dad = 0;
UINT bound_addresses = 0;
UINT address_not_assigned = 0;
UINT server_errors = 0;

/* Define some DHCPv6 parameters. */

#define DHCPV6_IANA_ID      0xC0DEDBAD
#define DHCPV6_T1           NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_T2           NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_RENEW_TIME   NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_REBIND_TIME  NX_DHCPV6_INFINITE_LEASE
#define PACKET_PAYLOAD      500
#define PACKET_POOL_SIZE    (5*PACKET_PAYLOAD)

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

UINT    status;

    /* Setup the working pointer. */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the Client thread. */
    status = tx_thread_create(&thread_client, "Client thread", thread_client_entry, 0,
                              pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1024,  pointer, PACKET_POOL_SIZE);

    pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create a Client IP instance. */
    status = nx_ip_create(&client_ip, "Client IP", IP_ADDRESS(0, 0, 0, 0),
                          0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                          pointer, 2048, 1);

    pointer =  pointer + 2048;

    /* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Enable UDP traffic for sending DHCPv6 messages. */
    status =  nx_udp_enable(&client_ip);

    /* Check for UDP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Enable ICMP. */
    status =  nx_icmp_enable(&client_ip);

    /* Check for ICMP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create the DHCPv6 Client. */
    status =  nx_dhcpv6_client_create(&dhcp_client, &client_ip, "DHCPv6 Client",
                                      &pool_0, pointer, 2048, dhcpv6_state_change_notify,
                                      dhcpv6_server_error_handler);

    /* Check for errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Update the stack pointer because we need it again. */
    pointer = pointer + 2048;

    /* Yield control to DHCPv6 threads and ThreadX. */
    return;
}


/* Define the Client host application thread. */

void    thread_client_entry(ULONG thread_input)
{

UINT        status;
ULONG       T1, T2;
UINT        address_count;
UINT        address_index = 0;
NXD_ADDRESS valid_ipv6_address;
ULONG       preferred_lifetime;
ULONG       valid_lifetime;
UINT        ia_count = 1;

#ifdef NX_DHCPV6_REQUEST_IA_ADDRESS
NXD_ADDRESS ipv6_address;
#endif

#ifdef NX_DHCPV6_REQUEST_OPTION
UCHAR       buffer[200];
NXD_ADDRESS dns_server;
#endif

#ifdef NX_DHCPV6_CLIENT_RESTORE_STATE
ULONG       current_time;
ULONG       elapsed_time;
NX_DHCPV6_CLIENT_RECORD dhcpv6_client_record;
#endif


    state_changes = 0;

    /* Establish the link local address for the host. The RAM driver creates
       a virtual MAC address of 0x1122334456. */
    status = nxd_ipv6_address_set(&client_ip, 0, NX_NULL, 10, NULL);

    if (status)
    {
        error_counter++;
        return;
    }

    /* Let NetX Duo get initialized. */
    tx_thread_sleep(50);

    /* Enable the Client IP for IPv6 and ICMPv6 services. */
    nxd_ipv6_enable(&client_ip);
    nxd_icmp_enable(&client_ip);

    /* Create a Link Layer Plus Time DUID for the DHCPv6 Client. Set time ID field
       to NULL; the DHCPv6 Client API will supply one. */
    status = nx_dhcpv6_create_client_duid(&dhcp_client, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                          NX_DHCPV6_HW_TYPE_IEEE_802, 0);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create the DHCPv6 client's Identity Association (IA-NA) now.

       Note that if this host had already been assigned in IPv6 lease, it
       would have to use the assigned T1 and T2 values in loading the DHCPv6
       client with an IANA block.
    */
    status = nx_dhcpv6_create_client_iana(&dhcp_client, DHCPV6_IANA_ID, DHCPV6_T1,  DHCPV6_T2);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

#ifdef NX_DHCPV6_REQUEST_IA_ADDRESS
    memset(&ipv6_address,0x0, sizeof(NXD_ADDRESS));
    ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
    ipv6_address.nxd_ip_address.v6[0] = 0x3ffe0501;
    ipv6_address.nxd_ip_address.v6[1] = 0xffff0100;
    ipv6_address.nxd_ip_address.v6[2] = 0x00000000;
    ipv6_address.nxd_ip_address.v6[3] = 0x0000abcd;

    /* Create an IA address option.
        Note that if this host had already been assigned in IPv6 lease, it
        would have to use the assigned IPv6 address, preferred and valid lifetime
        values in loading the DHCPv6 Client with an IA block.
    */
    status = nx_dhcpv6_add_client_ia(&dhcp_client, &ipv6_address,DHCPV6_RENEW_TIME, DHCPV6_REBIND_TIME);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* If the DHCPv6 Client is configured for a maximum number of IA addresses
       greater than 1, we can add another IA address if the device requires
       multiple global IPv6 addresses. */
    if(NX_DHCPV6_MAX_IA_ADDRESS >= 2)
    {
        memset(&ipv6_address,0x0, sizeof(NXD_ADDRESS));
        ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
        ipv6_address.nxd_ip_address.v6[0] = 0x3ffe0501;
        ipv6_address.nxd_ip_address.v6[1] = 0xffff0100;
        ipv6_address.nxd_ip_address.v6[2] = 0x00000000;
        ipv6_address.nxd_ip_address.v6[3] = 0x00001234;

        /* Add another  IA address option. */
        status = nx_dhcpv6_add_client_ia(&dhcp_client, &ipv6_address, DHCPV6_RENEW_TIME, DHCPV6_REBIND_TIME);

        if (status != NX_SUCCESS)
        {
            error_counter++;
            return;
        }
    }
#endif /* NX_DHCPV6_REQUEST_IA_ADDRESS  */

#ifdef NX_DHCPV6_REQUEST_OPTION
    /* Set the list of DHCPv6 option data to get from the DHCPv6 server if needed. */
    nx_dhcpv6_request_option_timezone(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_DNS_server(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_time_server(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_domain_name(&dhcp_client, NX_TRUE);
#endif /* NX_DHCPV6_REQUEST_OPTION */


#ifdef NX_DHCPV6_REQUEST_FQDN_OPTION
    /* Set the DHCPv6 Client FQDN option.
       operation: NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR         DHCPv6 Client choose to updating the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the client.
                  NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE   DHCPv6 Client choose to updating the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the client to the server.
                  NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE   DHCPv6 Client choose to request that the server perform no DNS updatest on its behalf. */
    nx_dhcpv6_request_option_FQDN(&dhcp_client, "DHCPv6-Client", NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR);
#endif /* NX_DHCPV6_REQUEST_FQDN_OPTION */

    /* Start up the NetX DHCPv6 Client thread task. */
    status =  nx_dhcpv6_start(&dhcp_client);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Start the DHCPv6 by sending a Solicit message out on the network. */
    status = nx_dhcpv6_request_solicit(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Is the DHCPv6 Client request for address assignment successfully started? */
    if (status == NX_SUCCESS)
    {

        /* If Duplicate Address Detection (DAD) is enabled in NetX Duo, e.g. #NXDUO_DISABLE_DAD
           not defined, allow time for NetX Duo to verify the address is unique on our network.
         */
        tx_thread_sleep(500);

        /* Check the bound address. */
        if (bound_addresses != ia_count)
        {

            /* Attempt to find out why DHCPv6 failed, where...*/

            if (server_errors > 0)
            {
                /* Actually you would compare server_error count with number of IA's added
                   to determine if any addresses were assigned. */
                printf("Server error, not all address assigned\n");
            }

            if (address_not_assigned > 0)
            {
                /* Actually you would compare address not assigned count with number of IA's added
                   to determine if any addresses were assigned. */

                printf("No servers responded to some or all of our IAs\n");
            }

        }

        /* Regardless if the DHCPv6 Client achieved a bound state, check for DAD
           failures. */
        if (address_failed_dad > 0)
        {
            /* Actually you would compare failed dad count with number of IA's added
               to determine if any addresses were assigned. */

            printf("Some or all of our IAs failed DAD\n");

        }

        /* Successfully assigned IPv6 addresses! */

        /* Get the count of valid IPv6 address obtained by DHCPv6. */
        status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_client, &address_count);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IPv6 address and related lifetimes by address index. This index is the
           index into the DHCPv6 Client address table. Not to be confused with the IP
           instance address table! */
        status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_client, address_index,
                                                           &valid_ipv6_address, 
                                                               &preferred_lifetime,
                                                           &valid_lifetime);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IANA options for when to start renew/rebind requests. These time
           parameters are the same for all IPv6 addresses assigned in the Client
           e.g. IANA returned from Server. */
        status = nx_dhcpv6_get_iana_lease_time(&dhcp_client, &T1, &T2);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /*****************************************************************************/
        /* These are 'legacy' DHCPv6 services and are for the most part identical to the services
           above except they default to the primary global IPv6 address regardless if the
           Client was assigned more than one global IPv6 address. */

        /* Now check the assigned lease times. */
        status = nx_dhcpv6_get_lease_time_data(&dhcp_client, &T1, &T2,
                                               &preferred_lifetime, &valid_lifetime);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IP address. */
        status = nx_dhcpv6_get_IP_address(&dhcp_client, &valid_ipv6_address);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Bound state. */

#ifdef NX_DHCPV6_CLIENT_RESTORE_STATE

        /* Get the DHCPv6 Client record. */
        nx_dhcpv6_client_get_record(&dhcp_client, &dhcpv6_client_record);

        /* Delete DHCPv6 instance. */
        nx_dhcpv6_client_delete(&dhcp_client);

        /* Delete IP instance. */
        status = nx_ip_delete(&client_ip);

        /* Check for error. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Create a Client IP instance. */
        status = nx_ip_create(&client_ip, "Client IP", IP_ADDRESS(0, 0, 0, 0),
                              0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                              pointer, 2048, 1);

        pointer =  pointer + 2048;

        /* Check for IP create errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable UDP traffic for sending DHCPv6 messages. */
        status =  nx_udp_enable(&client_ip);

        /* Check for UDP enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable ICMP. */
        status =  nx_icmp_enable(&client_ip);

        /* Check for ICMP enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable the Client IP for IPv6 and ICMPv6 services. */
        status = nxd_ipv6_enable(&client_ip);
        status += nxd_icmp_enable(&client_ip);

        /* Check for IPv6 and ICMPv6 enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Establish the link local address for the host. The RAM driver creates
           a virtual MAC address of 0x1122334456. */
        status = nxd_ipv6_address_set(&client_ip, 0, NX_NULL, 10, NULL);

        if (status)
        {
            error_counter++;
            return;
        }

        /* If Duplicate Address Detection (DAD) is enabled in NetX Duo, e.g. #NXDUO_DISABLE_DAD
           not defined, allow time for NetX Duo to verify the address is unique on our network.
         */
        tx_thread_sleep(500);

        /* Create the DHCPv6 Client. */
        status =  nx_dhcpv6_client_create(&dhcp_client, &client_ip, "DHCPv6 Client",
                                          &pool_0, pointer, 2048, dhcpv6_state_change_notify,
                                          dhcpv6_server_error_handler);

        /* Check for errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Update the stack pointer because we need it again. */
        pointer = pointer + 2048;

        /* Restore the DHCPv6 record. */
        nx_dhcpv6_client_restore_record(&dhcp_client, &dhcpv6_client_record, 5);

        /* Resume the DHCPv6 service. */
        nx_dhcpv6_resume(&dhcp_client);
#endif


#ifdef NX_DHCPV6_REQUEST_OPTION

        /* Get the DNS Server address. */
        nx_dhcpv6_get_DNS_server_address(&dhcp_client, 0, &dns_server);

        /* Get the domain name. */
        memset(buffer, 0, sizeof(buffer));

        nx_dhcpv6_get_other_option_data(&dhcp_client, NX_DHCPV6_DOMAIN_NAME_OPTION, buffer, 200); // Try to get DNS info got from DHCPv6 Server

        /* Get the domain name. */
        memset(buffer, 0, sizeof(buffer));

        /* Get the time zone. */
        nx_dhcpv6_get_other_option_data(&dhcp_client, NX_DHCPV6_NEW_POSIX_TIMEZONE_OPTION, buffer, 200); // Try to get DNS info got from DHCPv6 Server
#endif

        /* At some point, we may wish to release the IPv6 address lease e.g. the device
           is leaving the network or powering down. In that case we inform the
           DHCPv6 Server that we are releasing the address lease. */
        status = nx_dhcpv6_request_release(&dhcp_client);

        /* Check status. */
        if (status != NX_SUCCESS)
        {

            error_counter++;
            return;
        }

        /* Send the release message. */
        tx_thread_sleep(100);
    }

    /* Stopping the Client task. */
    status = nx_dhcpv6_stop(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Clear the previously assigned IPv6 addresses from the Client and IP address table. */
    status = nx_dhcpv6_reinitialize(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Start up the Client task again. */
    status = nx_dhcpv6_start(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Begin the request process by sending a Solicit message with the IA created above
       with our preferred IPv6 address. */
    status = nx_dhcpv6_request_solicit(&dhcp_client);
    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Wait a bit before releasing the IP address and terminating the client. */
    tx_thread_sleep(500);

    /* Ok, lets stop the application. Again we DO NOT plan
       to keep the IPv6 address we were assigned and need to release it
       back to the DHCPv6 server. */
    status = nx_dhcpv6_request_release(&dhcp_client);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    /* Now delete the DHCPv6 client and release ThreadX and
       NetX Duo resources back to the system. */
    nx_dhcpv6_client_delete(&dhcp_client);


    return;

}


/* This is the notification from the DHCPv6 Client task that it has changed
   state in the DHCPv6 protocol, for example getting assigned an IPv6 lease and
   achieving the bound state or an IPv6 lease expires and being reset to
   the init state.
*/
VOID dhcpv6_state_change_notify(NX_DHCPV6 *dhcpv6_ptr, UINT old_state, UINT new_state)
{


    /* Increment state change counter. */
    state_changes++;

    /* Check if the Client attempted to request an IPv6 lease but no servers
       responded. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_SOLICIT) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that either DAD failed or IP lease expired. */
        address_not_assigned++;
    }

    /* Check if the Client has been assigned an IPv6 lease. */
    if (new_state == NX_DHCPV6_STATE_BOUND_TO_ADDRESS)
    {
        bound_addresses++;
    }

   /* Check if the Client was bound, but failed the uniqueness check
       (Duplicate Address Detection) and was reset to the INIT state. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_DECLINE) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that DAD failed on Client IA. */
        address_failed_dad++;
    }

    /* Check if the Client was bound, attempted renew the lease but the
       IPv6 address renewal/rebinding failed. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_REBIND) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that the IP lease expired. */
        address_expired++;
    }



    /* Other checks are possible. */

}

/* This is the notification from the DHCPv6 Client task that it received an error
   from the server (status code) in response to the Client's last DHCPv6 message.
*/

VOID dhcpv6_server_error_handler(NX_DHCPV6 *dhcpv6_ptr, UINT op_code, UINT status_code, UINT message_type)
{

    /* Increment the server error count. */
    server_errors++;

    /* This should distinguish between receiving a server error and no server
       available to assign the Client an IPv6 address if the Client fails
       to get assigned an address. */
}

#endif /* FEATURE_NX_IPV6 */
```
