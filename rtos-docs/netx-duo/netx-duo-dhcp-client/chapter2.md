---
title: 第 2 章 - Azure RTOS NetX Duo DHCP クライアントのインストールと使用
description: この章では、Azure RTOS NetX Duo DHCP クライアント コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 08f88f4501a7b44272111cbe5c14ee09474827b72a1239b334fb9d40e8093c51
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788492"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dhcp-client"></a>第 2 章 - Azure RTOS NetX Duo DHCP クライアントのインストールと使用

この章では、Azure RTOS NetX Duo DHCP クライアント コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品の配布

Azure RTOS NetX Duo は、<https://github.com/azure-rtos/netxduo> のパブリック ソース コード リポジトリから入手できます。 パッケージには、次のファイルが含まれています。

- **nxd_dhcp_client.h**: NetX Duo DHCP のヘッダー ファイル
- **nxd_dhcp_client.c**: DHCP NetX Duo の C ソース ファイル
- **nxd_dhcp_client.pdf**: NetX Duo DHCP のユーザー ガイド 
    - **demo_netxduo_dhcp.c**: NetX Duo DHCP クライアントのデモンストレーション
    - **demo_netxduo_multihome_dhcp_client.c**: 複数のインターフェイスで DHCP を使用する NetX Duo DHCP クライアントのデモ

## <a name="dhcp-installation"></a>DHCP のインストール

NetX Duo DHCP クライアントを使用するためには、前述の配布全体を、NetX Duo がインストールされているのと同じディレクトリにコピーする必要があります。 たとえば、NetX Duo がディレクトリ " *\threadx\arm7\green*" にインストールされている場合、*nxd_dhcp_client.h* ファイルと *nxd_dhcp_client.c* ファイルをこのディレクトリにコピーします。

## <a name="using-dhcp"></a>DHCP の使用

NetX Duo 用 DHCP は簡単に使用できます。 基本的には、ThreadX と NetX Duo を使用するために、アプリケーション コードにそれぞれ *tx_api.h* と *nx_api.h* をインクルードした後に、*nxd_dhcp_client.h* をインクルードする必要があります。 *nxd_dhcp_client.h* をインクルードすると、このガイドで後述する DHCP 関数呼び出しを、そのアプリケーション コードで実行できるようになります。 このアプリケーションには、ビルド プロセスで *nxd_dhcp_client.c* もインクルードする必要があります。 このファイルは、他のアプリケーション ファイルと同様にコンパイルし、オブジェクトとしてアプリケーションのファイルと共にリンクする必要があります。 NetX DHCP の使用に必要なものはこれですべてです。

DHCP では NetX Duo UDP サービスを利用するため、DHCP を使用するときは、前もって *nx_udp_enable* を呼び出して UDP を有効にしておく必要があることに注意してください。

割り当て済みの IP アドレスを取得するために、DHCP クライアントでは、要求メッセージおよびオプション 50 "要求された IP アドレス" を DHCP サーバーに送信することで DHCP 処理を開始できます。 DHCP サーバーは、クライアントに IP アドレスを割り当てる場合は ACK メッセージで応答し、拒否する場合は NACK で応答します。 後者の場合、DHCP クライアントから Discover メッセージが送信され、要求された IP アドレスを与えずに、DHCP 処理を Init の状態からやり直します。 ホスト アプリケーションは最初に DHCP クライアントを作成し、次に *nx_dhcp_request_client_ip* API サービスを呼び出して要求する IP アドレスを設定し、その後で *nx_dhcp_start* により DHCP 処理を開始します。 詳細は、このドキュメントの他の箇所に挙げる DHCP アプリケーションの例をご覧ください。

## <a name="in-the-bound-state"></a>バインド状態

DHCP クライアントがバインド状態である間、DHCP クライアント スレッドはクライアントの状態を一定間隔で (NX_DHCP_TIME_INTERVAL で指定された間隔で) 処理し、クライアントに割り当てられた IP アドレスのリースの残り時間を減らします。 更新時間が経過すると、DHCP クライアントの状態は RENEW 状態に更新され、クライアントは DHCP サーバーによる更新を要求します。

## <a name="sending-dhcp-messages-to-the-server"></a>DHCP メッセージをサーバーに送信する

DHCP クライアントには、ホスト アプリケーションが DHCP サーバーにメッセージを送信するための API サービスが用意されています。 これらのサービスは、ホスト アプリケーションで DHCP クライアント プロトコルを手動で実行するためのものではありません。

  - *nx_dhcp_release*: ホスト アプリケーションがネットワークを離れるとき、または IP アドレスを手放す必要があるときに、RELEASE メッセージをサーバーに送信します。
  - *nx_dhcp_decline*: ホスト アプリケーションが、DHCP クライアントの判断とは無関係に、自身の IP アドレスが既に使用されていると判断した場合に、DECLINE メッセージをサーバーに送信します。
  - *nx_dhcp_forcerenew*: サーバーに FORCERENEW メッセージを送信します
  - *nx_dhcp_send_request*: *nx_dhcp_client.h* に指定された DHCP メッセージの種類を引数に取ってサーバーにメッセージを送信します。 DHCP INFORM メッセージを送信することが主な目的です。

これらのサービスの詳細については、[DHCP サービスの説明](chapter3.md)に関するページを参照してください 

## <a name="starting-and-stopping-the-dhcp-client"></a>DHCP クライアントの起動と停止

DHCP クライアントを停止するには、バインド状態になっているかどうかにかかわらず、ホスト アプリケーションで *nx_dhcp_stop* を呼び出します。

DHCP クライアントを再起動するには、最初に、ホスト アプリケーションで前述の *nx_dhcp_stop* サービスを使用して DHCP クライアントを停止する必要があります。 それから、ホストで *nx_dhcp_start* を呼び出して DHCP クライアントを再開できます。 古い DHCP クライアント プロファイル、たとえば他のネットワーク上にあった以前の DHCP サーバーから取得したものの削除をホスト アプリケーションが求める場合、そのホスト アプリケーションで *nx_dhcp_reinitialize* を呼び出してこのタスクを内部的に実行し、その後で *nx_dhcp_start* を呼び出します。

典型的なシーケンスは、次のようになります。

```c
nx_dhcp_stop(&my_dhcp);
nx_dhcp_reinitialize(&my_dhcp);
nx_dhcp_start(&my_dhcp);
```

DHCP アプリケーションを単一の DHCP インターフェイスで実行している場合、DHCP クライアントを停止すると、DHCP クライアントのタイマーも無効になります。 こうして IP リース時間の残り時間が監視されなくなります。 特定のインターフェイスで DHCP クライアントを停止すると、DHCP クライアントのタイマーは無効になりませんが、そのインターフェイスで IP リース時間の残り時間のタイマーが停止します

そのため、ホスト アプリケーションでネットワークの再起動または切り替えが必要な場合を除き、DHCP クライアントを停止することは推奨しません。

## <a name="using-the-dhcp-client-with-auto-ip"></a>Auto IP と共に DHCP クライアントを使用

DHCP サーバーが使用可能であること、または応答していることが保証されない場合に DHCP と Auto IP による IP アドレスの割り当てが保証されるアプリケーションでは、NetX Duo DHCP クライアントを Auto IP プロトコルと共に使用します。 ただし、ホストがサーバーを検出できない、または IP アドレスの割り当てを受けることができない場合は、ローカル IP アドレスの処理を Auto IP プロトコルに切り替えることができます。 ただし、そうする前に DHCP クライアントを一時的に停止して、Auto IP が "調査" と "防御" の段階を過ぎるのを待つことを推奨します。 Auto IP アドレスがホストに割り当てられたら DHCP クライアントを再起動できます。また、DHCP サーバーが実際に使用できるようになったら、アプリケーション実行中に DHCP サーバーによって提供される IP アドレスを、ホストの IP アドレスとして受け入れることができます。

NetX Duo Auto IP には、IP アドレスが変更された場合にホストがそのアドレスの振る舞いを監視するための、アドレス変更通知があります。

## <a name="packet-chaining"></a>パケット チェーン

パケット プールとメモリ リソースをより効率的に使用するために、DHCP クライアントでは、イーサネット ドライバーからチェーン化された受信パケット (ドライバーの MTU を超えるデータグラム) を処理できます。 ドライバーがこの機能を備えている場合、アプリケーションではパケットを受信するためのパケット プールを、必須の NX_DHCP_PACKET_PAYLOAD バイト以下に設定できます。 NX_DHCP_PACKET_PAYLOAD では、物理ネットワーク (通常はイーサネット) フレームと、548 バイトの DHCP メッセージ データ (IP と UDP) に対応する必要があります。

なお、アプリケーションでは、パケット ペイロードに加え、DHCP クライアントの一部であり、かつ DHCP メッセージを送信するために使用されるパケット プール内のパケットの数を最適化できます。予想される使用量と DHCP クライアント メッセージのサイズに基づいて、サイズが最適化されます。

## <a name="small-example-system"></a>簡単なシステムの例

NetX Duo を使用する方法の例を以下の図 1.1 に示します。 アプリケーション スレッド エントリ関数 *my_thread_entry* は 101 行目に作成されます。 正常に作成されると、108 行目の *nx_dhcp_start* 呼び出しを使用して DHCP 処理が開始されます。 この時点で、DHCP クライアント スレッド タスクは、個別に DHCP サーバーへの接続を試みます。 この処理中、アプリケーションのコードは、95 行目の *nx_ip_status_check* サービス (セカンダリ インターフェイスの場合は *nx_ip_interface_status_check*) を使用して、有効な IP アドレスが IP インスタンスに登録されるのを待ちます。 これは、待機時間を短縮するオプションのあるループではより一般的です。

127 行目を過ぎた時点で DHCP では有効な IP アドレスを受け取っており、アプリケーションでは必要に応じて NetX Duo の TCP/IP サービスを使用しながら、処理を進めることができます。

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_client.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_DHCP                 my_dhcp;

/* Define function prototypes.  */

void    my_thread_entry(ULONG thread_input);
void    my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point.  */
intmain()
{
  /* Enter the ThreadX kernel.  */
  tx_kernel_enter();
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;
    
    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create “my_thread”.  */
      tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                        pointer, DEMO_STACK_SIZE, 2, 2, 
                        TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duo system.  */
    nx_system_initialize();

    /* Create a packet pool.  */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                     1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error.  */
    if (status)
        error_counter++;

    /* Create an IP instance without an IP address. */
    status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
                          0xFFFFFF00, &my_pool, my_netx_driver, pointer, 
                          DEMO_STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors.  */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for my IP Instance.  */
    status =  nx_arp_enable(&my_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
        error_counter++;

    /* Enable UDP.  */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
 }


 /* Define my thread.  */

 void    my_thread_entry(ULONG thread_input)
 {

 UINT        status;
 ULONG       actual_status;
 NX_PACKET   *my_packet;

    /* Wait for the link to come up.  */
    do
    {
    /* Get the link status.  */
        status =  nx_ip_status_check(&my_ip, NX_IP_LINK_ENABLED, 
                                     &actual_status, 100);
    } while (status != NX_SUCCESS);

    /* Create a DHCP instance.  */
    status =  nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

    /* Check for DHCP create error.  */
    if (status)
        error_counter++;

    /* Start DHCP.  */
    nx_dhcp_start(&my_dhcp);

    /* Check for DHCP start error.  */
    if (status)
        error_counter++;

    /* Wait for IP address to be resolved through DHCP.  */
    nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                       (ULONG *) &status, 100000);

    /* Check to see if we have a valid IP address.  */
    if (status)
    {
      error_counter++;
      return;
    }
    else
    {

  /* Yes, a valid IP address is now on lease…  All NetX Duo
        services are available.
    }
 }

```
## <a name="multi-server-environments"></a>マルチサーバー環境

複数の DHCP サーバーが存在するネットワークでは、DHCP クライアントは最初に受信した DHCP サーバーのオファー メッセージを受け入れて Request 状態に進み、受信した他のオファーをすべて無視します。

## <a name="arp-probes"></a>ARP プローブ

DHCP クライアントを構成することで、DHCP サーバーによる IP アドレスの割り当てが済んだ後で、1 つまたは複数の ARP プローブを送信して、その IP アドレスがまだ使用されていないことを確認するように設定できます。 RFC 2131 では ARP プローブの使用が推奨されています。これは特に複数の DHCP サーバーが存在する環境で重要です。 ホスト アプリケーションで NX_DHCP_CLIENT_SEND_ARP_PROBE オプションを有効にすると (他の ARP プローブ オプションは、第 2 章の「**構成オプション**」をご覧ください)、DHCP クライアントは "自分宛ての" ARP プローブを送信し、指定された時間応答を待機します。 何も受信できない場合、DHCP クライアントは Bound 状態に進みます。 応答を受信した場合、DHCP クライアントは、アドレスが既に使用されているものとみなします。 すると自動的に DECLINE メッセージがサーバーに送信され、クライアントを再初期化して、INIT 状態から DHCP プローブを再開します。 これにより DHCP ステート マシンが再起動し、クライアントは DISCOVER メッセージをもう 1 度サーバーに送信します。

## <a name="bootp-protocol"></a>BOOTP プロトコル

DHCP クライアントは、DHCP プロトコルと共に BOOTP プロトコルもサポートしています。 このオプションを有効にして DHCP の代わりに BOOTP を使用するには、ホスト アプリケーションで NX_DHCP_BOOTP_ENABLE 構成オプションを設定する必要があります。 ホスト アプリケーションは、BOOTP プロトコルでも特定の IP アドレスを要求できます。 なお、BOOTP はホスト オペレーティング システムの読み込みに使用する場合もありますが、DHCP クライアントはこれをサポートしていません。

## <a name="dhcp-on-a-secondary-interface"></a>セカンダリ インターフェイスでの DHCP

NetX Duo DHCP クライアントは、既定のプライマリ インターフェイスの代わりにセカンダリ インターフェイスでも実行できます。

セカンダリ ネットワーク インターフェイスで NetX Duo DHCP クライアントを実行するには、ホスト アプリケーションで、*nx_dhcp_set_interface_index* API サービスを使用して、DHCP クライアントのインターフェイス インデックスをセカンダリ インターフェイスに設定する必要があります。 インターフェイスは、*nx_ip_interface_attach* サービスを使用して、プライマリ ネットワーク インターフェイスに前もってアタッチしておく必要があります。 セカンダリ インターフェイスのアタッチの詳細については、NetX Duo ユーザー ガイドを参照してください。

次に示すのは (図 1.2)、ホスト アプリケーションをセカンダリ インターフェイス上の DHCP サーバーに接続するシステムの例です。 65 行目で、null 値の IP アドレスを使用してセカンダリ インターフェイスを IP タスクにアタッチします。 104 行目で、DHCP クライアント インスタンスを作成してから、*nx_dhcp_set_interface_index* を呼び出して、DHCP クライアントのインターフェイス インデックスを 1 に設定します (自身のインデックスが 0 であるプライマリ インターフェイスとの差に相当)。 その後 108 行目で DHCP クライアントが起動できる状態になります。

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_client.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_DHCP                 my_dhcp;

/* Define function prototypes.  */

void    my_thread_entry(ULONG thread_input);
void    my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point.  */

intmain()
{
  /* Enter the ThreadX kernel.  */
  tx_kernel_enter();
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create “my_thread”.  */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                      pointer, DEMO_STACK_SIZE, 
                      2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duo system.  */
    nx_system_initialize();

  /* Create a packet pool.  */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                     1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error.  */
    if (status)
        error_counter++;

    /* Create an IP instance without an IP address. */
    status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
                           0xFFFFFF00, &my_pool, my_netx_driver, pointer, STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors.  */
    if (status)
        error_counter++;

    status =  _nx_ip_interface_attach(&ip_0, "port_2", IP_ADDRESS(0, 0, 0,0), 
                                       0xFFFFFF00UL, my_netx_driver);

    /* Enable ARP and supply ARP cache memory for my IP Instance.  */
    status =  nx_arp_enable(&my_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
        error_counter++;

    /* Enable UDP.  */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
}


void    my_thread_entry(ULONG thread_input)
{

UINT        status;
ULONG       status;
NX_PACKET   *my_packet;

    /* Wait for the link to come up.  */
    do
    {
      /* Get the link status.  */
        status =  nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,& status,100);
    } while (status != NX_SUCCESS);

    /* Create a DHCP instance.  */
    status =  nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

    /* Check for DHCP create error.  */
    if (status)
        error_counter++;

    /* Set the DHCP client interface to the secondary interface. */
    status = nx_dhcp_set_interface_index(&my_dhcp, 1);


    /* Start DHCP.  */
    nx_dhcp_start(&my_dhcp);

    /* Check for DHCP start error.  */
    if (status)
        error_counter++;

    /* Wait for IP address to be resolved through DHCP.  */
    nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                       (ULONG *) &status, 100000);

    /* Check to see if we have a valid IP address.  */
    if (status)
    {
        error_counter++;
        return;
    }
    else
    {
    /* Yes, a valid IP address is now on lease…  All NetX Duo
        services are available.*/
    }
}
```

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a>複数のインターフェイスでの DHCP クライアントの同時実行

DHCP クライアントを複数のインターフェイスで実行するには、*nx_api.h* の NX_MAX_PHYSICAL_INTERFACES を、デバイスに接続している物理インターフェイスの数に設定する必要があります。 既定値は 1 です (プライマリ インターフェイスを表しています)。 追加のインターフェイスを IP インスタンスに登録するには *nx_ip_interface_attach* サービスを使用します。 セカンダリ インターフェイスのアタッチの詳細については、NetX Duo ユーザー ガイドを参照してください。

次のステップでは、*nxd_dhcp_client.h* の NX_DHCP_CLIENT_MAX_RECORDS を、DHCP を同時に実行する予定のインターフェイスの最大数に設定します。 NX_DHCP_CLIENT_MAX_RECORDS を NX_MAX_PHYSICAL_INTERFACES と一致させる必要はありません。 たとえば、NX_MAX_PHYSICAL_INTERFACES を 3、NX_DHCP_CLIENT_MAX_RECORDS を 2 に設定できます。 この構成だと、DHCP を同時に使用できるのが、3 つの物理インターフェイスのうち 2 つだけということになります (2 つのインターフェイスの組み合わせは、あらゆる時点でどの組み合わせにもなり得ます)。 DHCP クライアント レコードは、ネットワーク インターフェイスに対し 1 対 1 でマッピングされません。たとえば、クライアント レコード 1 と物理インターフェイス インデックス 1 が自動的に関連付けられることはありません。

NX_DHCP_CLIENT_MAX_RECORDS を NX_MAX_PHYSICAL_INTERFACES より大きく設定することもできますが、これは使用しないクライアント レコードを作成することになり、メモリの使用効率が悪くなります。

どのインターフェイスで DHCP を起動する場合も、前もってアプリケーションで *nx_dhcp_interface_enable* を呼び出し、それらのインターフェイスを有効にしておく必要があります。 *nx_dhcp_create* の呼び出しで自動的に有効になるプライマリ インターフェイスはこの例外です (後述の *nx_dhcp_interface_disable* サービスを使用すれば無効にできます)。

DHCP を実行している他のインターフェイスとは無関係に、各インターフェイスではいつでも DHCP を無効にすることで、実行中の DHCP を停止することができます。

前述のとおり特定のインターフェイスで DHCP を有効にするには、*nx_dhcp_interface_enable* サービスを使用し、入力の引数で物理インターフェイスのインデックスを指定します。 インターフェイスは NX_DHCP_CLIENT_MAX_RECORDS で指定された数まで有効にできますが、唯一の制約として、入力の引数で指定するインターフェイス インデックスは NX_MAX_PHYSICAL_INTERFACES 未満でなければなりません。

特定のインターフェイスで DHCP を起動するには *nx_dhcp_interface_start* サービスを使用します。 有効になっているすべてのインターフェイスで DHCP を起動するには *nx_dhcp_start* サービスを使用します。 (既に DHCP を起動しているインターフェイスでは *nx_dhcp_start* の影響はありません。)

インターフェイスで DHCP を停止するには、*nx_dhcp_interface_stop* サービスを使用します。 DHCP はそのインターフェイスで前もって起動しておく必要があります。起動できていないとエラー ステータスが返されます。 有効になっているすべてのインターフェイスで DHCP を停止するには *nx_dhcp_stop* サービスを使用します。 DHCP は、他のインターフェイスとは別個に、各インターフェイスでいつでも停止できます。

既存の DHCP クライアント サービスのほとんどには、"インターフェイス別" に実行するバージョンが存在します。たとえば *nx_dhcp_release* のサービスをインターフェイス別に提供するのが *nx_dhcp_interface_release* です。 単一のインターフェイスで DHCP クライアントを構成する場合、これらのサービスに違いはありません。

インターフェイス別ではない DHCP クライアント サービスは通常すべてのインターフェイスに適用されますが、そうでない場合もあることに注意してください。 後者の場合、インターフェイス別ではないサービスは、DHCP が有効になっているインターフェイスのうち、インターフェイス レコードの DHCP クライアント リストを検索して最初に見つかったものに適用されます。 複数のインターフェイスで DHCP を有効にしたときに、インターフェイス別でないサービスがどのように機能するかは、第 3 章の「**サービスの説明**」をご覧ください。

下のプロセス進行例では、IP インスタンスに 2 つのネットワーク インターフェイスがあり、セカンダリ インターフェイスで先に DHCP を実行します。 しばらく後で、プライマリ インターフェイスでも DHCP が起動されます。 それからプライマリ インターフェイスで IP アドレスを解放し、プライマリ インターフェイスで DHCP を再起動します:

```c
nx_dhcp_create(&my_dhcp_client); /* By default this enables primary interface for DHCP. */

nx_dhcp_interface_enable(&my_dhcp_client, 1); /* Secondary interface is enabled. */

nx_dhcp_interface_start(&my_dhcp_client, 1); /* DHCP is started on secondary interface. */

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); /* DHCP is started on primary interface. */

nx_dhcp_interface_release(&my_dhcp_client, 0); /* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); /* DHCP is restarted on primary interface. */
```

インターフェイス別に実行するすべてのサービスのリストは、第 3 章の「**サービスの説明**」をご覧ください。

## <a name="configuration-options"></a>構成オプション

*nxd_dhcp_client.h* にあるユーザーが構成可能な DHCP オプションを使用すると、ホスト アプリケーションで、DHCP クライアントの特定の要件を細かく調整できます。 次のリストにそれらのパラメーターを挙げます。  
  
- **NX_DHCP_ENABLE_BOOTP**: このオプションを有効にすると、DHCP の代わりに BOOTP プロトコルが有効になります。 既定では、このオプションは無効になっています。
- **NX_DHCP_CLIENT_RESTORE_STATE**: 定義されていると、DHCP クライアントで、リース時間の残り時間を含む現在の DHCP クランアントのライセンスの "状態" を保存し、DHCP クライアント アプリケーションを再起動してもこの状態を復元できるようになります。 既定値は、無効です。
- **NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL**: 設定されている場合、DHCP クライアントで専用のパケット プールを作成しなくなります。 ホスト アプリケーションで *nx_dhcp_packet_pool_set* サービスを使用して DHCP クライアントのパケット プールを設定する必要があります。 既定値は、無効です。
- **NX_DHCP_CLIENT_SEND_ARP_PROBE**: 定義されている場合、IP アドレスを割り当てられた後で DHCP クライアントが ARP プローブを送信し、割り当てられた DHCP アドレスがまだ他のホストに所持されていないことを確認できるようになります。 既定では、このオプションは無効になっています。
- **NX_DHCP_ARP_PROBE_WAIT**: ARP プローブを送信してから DHCP クライアントが応答を待つ時間を定義します。 既定値は 1 秒 (1 x NX_IP_PERIODIC_RATE) です
- **NX_DHCP_ARP_PROBE_MIN**: ARP プローブを送信する間隔の最小値を定義します。 既定値は 1 秒です。
- **NX_DHCP_ARP_PROBE_MAX**: ARP プローブを送信する間隔の最大値を定義します。 既定値は 2 秒です。
- **NX_DHCP_ARP_PROBE_NUM**: DHCP サーバーが割り当てた IP アドレスが既に使用されているかどうかを判断するために ARP プローブを送信する回数を定義します。 既定値は 3 回です。
- **NX_DHCP_RESTART_WAIT**: DHCP クライアントに割り当てた IP アドレスが既に使用されている場合に、DHCP クライアントが DHCP の再起動を待つ時間を定義します。 既定値は 10 秒です。
- **NX_DHCP_CLIENT_MAX_RECORDS**: DHCP クライアント インスタンスに保存するインターフェイス レコードの最大数を指定します。 DHCP クライアント インターフェイス レコードは、特定のインターフェイスで実行している DHCP クライアントのレコードです。 既定値は、物理インターフェイス数 (NX_MAX_PHYSICAL_INTERFACES) に設定されています。
- **NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION**: 定義されていると、DHCP メッセージ サイズ オプションの最大数まで、DHCP クライアントからメッセージを送信できます。 既定では、このオプションは無効になっています。
- **NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK**: 定義されていると、nx_dhcp_create の呼び出しで入力したホスト名の文字と長さが無効でないかどうかを、DHCP クライアントで確認できるようになります。 既定では、このオプションは無効になっています。
- **NX_DHCP_THREAD_PRIORITY**: DHCP スレッドの優先度です。 既定では、この値によって DHCP スレッドが優先度 3 で 実行されるように指定されます。
- **NX_DHCP_THREAD_STACK_SIZE**: DHCP スレッドのスタックのサイズです。 既定のサイズは 2048 バイトです。
- **NX_DHCP_TIME_INTERVAL**: DHCP クライアント タイマーの有効期限関数を実行する秒単位の間隔です。 この関数では、DHCP 処理のすべてのタイムアウトが更新されます。たとえば、メッセージを再送する必要がある場合や、DHCP クライアントの状態が変更された場合などです。 既定値は 1 秒です。
- **NX_DHCP_OPTIONS_BUFFER_SIZE**: DHCP のオプションのバッファーのサイズです。 既定値は 312 バイトです。
- **NX_DHCP_PACKET_PAYLOAD**: DHCP クライアントのパケットのペイロードのサイズをバイト単位で指定します。 既定値は NX_DHCP_MINIMUM_IP_DATAGRAM + 物理ヘッダーのサイズです。 有線ネットワークでの物理ヘッダー サイズは、通常イーサネット フレームのサイズです。
- **NX_DHCP_PACKET_POOL_SIZE**: DHCP クライアントのパケット プールのサイズを指定します。 既定値は 5 x NX_DHCP_PACKET_PAYLOAD です。これは、パケット 4 個に、内部のパケット プールのオーバーヘッドを処理できるサイズを加えたものです。
- **NX_DHCP_MIN_RETRANS_TIMEOUT**: クライアントのメッセージに対する DHCP サーバーの応答を受け取ってからメッセージが再送されるまでの最小待機時間を指定します。 既定値は RFC 2131 で推奨されている 4 秒です。
- **NX_DHCP_MAX_RETRANS_TIMEOUT**: クライアントのメッセージに対する DHCP サーバーの応答を受け取ってからメッセージが再送されるまでの最大待機時間を指定します。 既定値は 64 秒です。
- **NX_DHCP_MIN_RENEW_TIMEOUT**: DHCP クライアントを IP アドレスにバインドした後、DHCP サーバーのメッセージを受信してから更新要求を送信するまでの、最小待機時間を指定します。 既定値は 60 秒です。 ただし、DHCP クライアントでは、DHCP サーバーのメッセージで指定される Renew および Rebind の有効期限を使用してから、更新のタイムアウト時間の既定最小値に戻ります。
- **NX_DHCP_TYPE_OF_SERVICE**: DHCP UDP 要求に必要なサービスの種類です。 既定では、この値は通常の IP パケット サービスを示す NX_IP_NORMAL に定義されています。
- **NX_DHCP_FRAGMENT_OPTION**: DHCP UDP 要求の断片化を有効にします。 既定値は NX_DONT_FRAGMENT であり DHCP UDP の断片化は無効になっています。
- **NX_DHCP_TIME_TO_LIVE**: このパケットが通過できるルーターの数を指定します。この数を超えるとパケットは破棄されます。 既定値は 0x80 に設定されています。
- **NX_DHCP_QUEUE_DEPTH**: 受信キューの深さの最大値を指定します。 既定値は 4 です。