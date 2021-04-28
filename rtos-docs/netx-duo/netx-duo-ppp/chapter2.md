---
title: 第 2 章 - Azure RTOS NetX Duo Point-to-Point プロトコル (PPP) のインストールと使用
description: この章では、Azure RTOS NetX Duo Point-to-Point プロトコル (PPP) コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2270a2668884dbecc8368d4ee130e419afa92491
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810643"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-point-to-point-protocol-ppp"></a>第 2 章 - Azure RTOS NetX Duo Point-to-Point プロトコル (PPP) のインストールと使用

この章では、Azure RTOS NetX Duo Point-to-Point プロトコル (PPP) コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品ディストリビューション

Azure RTOS NetX Duo Point-to-Point プロトコル (PPP) パッケージは、<https://github.com/azure-rtos/netxduo> で入手できます。 パッケージには、次のファイルが含まれています。

- **nx_ppp.h**: NetX 用 PPP のヘッダー ファイル
- **nx_ppp.c**: NetX 用 PPP の C ソース ファイル
- **nx_ppp.pdf**: NetX 用 PPP の PDF 説明書
- **demo_netx_ppp.c**: NetX PPP のデモンストレーション

## <a name="ppp-installation"></a>PPP のインストール

NetX 用 PPP を使用するには、前述のディストリビューション全体を、NetX がインストールされているのと同じディレクトリにコピーする必要があります。 たとえば、NetX が " *\threadx\arm7\green*" ディレクトリにインストールされている場合は、*nx_ppp.h* および *nx_ppp.c* ファイルをこのディレクトリにコピーする必要があります。

## <a name="using-ppp"></a>PPP の使用

NetX 用 PPP は簡単に使用できます。 基本的には、ThreadX と NetX を使用するために、アプリケーション コードにそれぞれ *tx_api.h* と *nx_api.h* をインクルードした後に、*nx_ppp.h* をインクルードする必要があります。 *nx_ppp.h* をインクルードすると、アプリケーション コードで、このガイドで後述する PPP 関数呼び出しを行えるようになります。 アプリケーションでは、ビルド プロセスで *nx_ppp.c* もインクルードする必要があります。 このファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、そのオブジェクト フォームをアプリケーションのファイルと一緒にリンクする必要があります。 NetX PPP を使用するために必要なことはこれだけです。

## <a name="using-modems"></a>モデムの使用

インターネットへの接続にモデムが必要な場合、NetX PPP 製品を使用するには、特別な考慮事項が必要となります。 基本的に、モデムを使用すると、初期化ロジックと通信喪失のロジックが追加されます。 さらに、追加のモデム ロジックのほとんどは、NetX PPP のコンテキストの外部で実行されます。 モデムで NetX PPP を使用する際の基本的な流れはこのようになります。

1. モデムを初期化する

1. インターネット サービス プロバイダー (ISP) にダイヤルする

1. 接続を待機する

1. ユーザー ID プロンプトを待機する

1. NetX PPP を起動する [動作中の PPP]

1. 通信が失われる

1. NetX PPP を停止する (または nx_ppp_restart によって再起動する)

### <a name="initialize-modem"></a>モデムを初期化する

アプリケーションの低レベルのシリアル出力ルーチンを使用して、一連の ASCII 文字コマンドでモデムを初期化します (詳細については、モデムのドキュメントをご覧ください)。

### <a name="dial-internet-service-provider"></a>インターネット サービス プロバイダーにダイヤルする

アプリケーションの低レベルのシリアル出力ルーチンを使用して、ISP にダイヤルするようモデムに指示します。 たとえば、123-4567 の番号で ISP にダイヤルする場合、通常、次の ASCII 文字列が使用されます。

"ATDT123456\r"

### <a name="wait-for-connection"></a>接続を待機する

この時点で、アプリケーションは、接続が確立されたことを示す通知をモデムから受信するのを待ちます。 これは、アプリケーションの低レベルのシリアル入力ルーチンからの文字を探すことで実現されます。 通常、接続が確立されると、モデムから ASCII 文字列 "CONNECT" が返されます。

### <a name="wait-for-user-id-prompt"></a>ユーザー ID プロンプトを待機する

接続が確立されたら、アプリケーションは ISP からの最初のログイン要求を待つ必要があります。 通常、これは "Login?" のような ASCII 文字列の形式になります。

### <a name="start-netx-ppp"></a>NetX PPP を起動する

この時点で、NetX PPP を起動できます。 これは、*nx_ppp_create* サービスを呼び出した後、*nx_ip_create* サービスを呼び出すことで実現されます。 PAP を有効にしたり、PPP IP アドレスを設定したりするための追加のサービスも必要になる場合があります。 詳細については、このガイドの以降のセクションをご覧ください。

### <a name="loss-of-communication"></a>通信が失われる

PPP が開始されると、PPP 以外の情報は、アプリケーションで *nx_ppp_create* サービスに指定した "無効なパケット処理" ルーチンに渡されます。 通常、ISP との通信が失われると、モデムは "NO CARRIER" などの ASCII 文字列を送信します。 アプリケーションは、このような情報を含む PPP 以外のパケットを受信すると、NetX PPP インスタンスを停止するか、*nx_ppp_restart* API を介して PPP ステート マシンを再起動する必要があります。

### <a name="stop-netx-ppp"></a>NetX PPP を停止する

NetX PPP の停止は非常に簡単です。 基本的に、作成されたすべてのソケットをバインド解除して削除する必要があります。 次に、*nx_ip_delete* サービスを使用して IP インスタンスを削除します。 IP インスタンスが削除されたら、*nx_ppp_delete* サービスを呼び出して、PPP を停止するプロセスを終了する必要があります。 この時点で、アプリケーションは ISP との通信の再確立を試行できるようになります。

## <a name="small-example-system"></a>簡単なシステムの例

NetX PPP の使用がいかに簡単であるかを示す例を下の図 1.1 に示します。 この例では、PPP インクルード ファイル *nx_ppp.h* が 3 行目で取り込まれます。 次に、56 行目の "*tx_application_define*" で PPP が作成されます。 PPP 制御ブロック "*my_ppp*" は、9 行目でグローバル変数として既に定義されています。 

>[!NOTE]
>IP インスタンスを作成する前に、PPP を作成する必要があります。 PPP と IP が正常に作成されると、スレッド "*my_thread*" は、98 行目で PPP リンクが有効になるのを待ちます。 104 行目で、PPP と NetX の両方が完全に動作しています。

この例に示されていない 1 つの項目は、アプリケーションのシリアル バイト受信 ISR です。 "*my_ppp*" と受信したバイトを入力パラメーターとして指定して、*nx_ppp_byte_receive* を呼び出す必要があります。

```c
0001 #include   "tx_api.h"
0002 #include   "nx_api.h"
0003 #include   "nx_ppp.h"
0004
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
## <a name="configuration-options"></a>構成オプション

NetX 用 PPP を構築するための構成オプションがいくつかあります。 次の一覧では、それぞれについて詳しく説明しています。

- **NX_DISABLE_ERROR_CHECKING**: このオプションを定義すると、基本的な PPP エラー チェックが削除されます。 通常は、アプリケーションがデバッグされた後に使用されます。
- **NX_PPP_PPPOE_ENABLE**: 定義した場合、PPP はイーサネット経由でパケットを送信できます
- **NX_PPP_BASE_TIMEOUT**: PPP イベントをチェックするために PPP スレッド タスクを起動する期間レート (タイマー刻み) を定義します。 既定値は、1*NX_IP_PERIODIC_RATE (100 ティック) です。
- **NX_PPP_DISABLE_INFO**: 定義した場合、内部 PPP 情報の収集が無効になります。
- **NX_PPP_DEBUG_LOG_ENABLE**: 定義した場合、内部 PPP デバッグ ログが有効になります。
- **NX_PPP_DEBUG_LOG_PRINT_ENABLE**: 定義した場合、内部 PPP デバッグ ログの *stdio* への *printf* が有効になります。 これは、デバッグ ログも有効になっている場合にのみ有効です。
- **NX_PPP_DEBUG_LOG_SIZE**: デバッグ ログのサイズ (デバッグ ログのエントリ数)。 最後のエントリに到達すると、デバッグ キャプチャは最初のエントリにラップされ、以前にキャプチャされたデータが上書きされます。 既定値は 50 です。
- **NX_PPP_DEBUG_FRAME_SIZE**: 受信したパケット ペイロードからキャプチャされ、デバッグ出力に保存されるデータの最大量。 既定値は 50 です。
- **NX_PPP_DISABLE_CHAP**: 定義した場合、MD5 ダイジェスト ロジックなど、内部 PPP CHAP ロジックが削除されます。
- **NX_PPP_DISABLE_PAP**: 定義した場合、内部 PPP PAP ロジックが削除されます。
- **NX_PPP_DNS_OPTION_DISABLE**: 定義した場合、IPCP 応答でプライマリ DNS サーバー オプションが無効になります。 既定では、このオプションは定義されません。
- **NX_PPP_DNS_ADDRESS_MAX_RETRIES**: PPP ホストが IPCP 状態のピアに DNS サーバー アドレスを要求する回数を指定します。 NX_PPP_DNS_OPTION_DISABLE が定義されている場合、これは無効になります。 既定値は 2 です。
- **NX_PPP_HASHED_VALUE_SIZE**: CHAP 認証で使用される "ハッシュ値" 文字列のサイズを指定します。 既定値は 16 バイトに設定されていますが、*nx_ppp.h* をインクルードする前に再定義できます。
- **NX_PPP_MAX_LCP_PROTOCOL_RETRIES**: 別の LCP 構成要求メッセージを送信する前に PPP がタイムアウトした場合の最大再試行回数を定義します。 この数に達すると、PPP ハンドシェイクが中止され、リンクの状態がダウンになります。 既定値は 20 です。
- **NX_PPP_MAX_PAP_PROTOCOL_RETRIES**: 別の PAP 認証要求メッセージを送信する前に PPP がタイムアウトした場合の最大再試行回数を定義します。 この数に達すると、PPP ハンドシェイクが中止され、リンクの状態がダウンになります。 既定値は 20 です。
- **NX_PPP_MAX_CHAP_PROTOCOL_RETRIES**: 別の CHAP チャレンジ メッセージを送信する前に PPP がタイムアウトした場合の最大再試行回数を定義します。 この数に達すると、PPP ハンドシェイクが中止され、リンクの状態がダウンになります。 既定値は 20 です。
- **NX_PPP_MAX_IPCP_PROTOCOL_RETRIES**: 別の IPCP 構成要求メッセージを送信する前に PPP がタイムアウトした場合の最大再試行回数を定義します。 この数に達すると、PPP ハンドシェイクが中止され、リンクの状態がダウンになります。 既定値は 20 です。
- **NX_PPP_MRU**: PPP の Maximum Receive Unit (MRU) を指定します。 この値は既定では 1,500 バイト (最小値) です。 この定義は、*nx_ppp.h* をインクルードする前にアプリケーションで設定できます。
- **NX_PPP_MINIMUM_MRU**: LCP 構成要求メッセージで受信する最小の MRU を指定します。 この値は既定では 1,500 バイト (最小値) です。 この定義は、*nx_ppp.h* をインクルードする前にアプリケーションで設定できます。
- **NX_PPP_NAME_SIZE**: 認証で使用される "名前" 文字列のサイズを指定します。 既定値は 32 バイトに設定されていますが、*nx_ppp.h をインクルードする前に再定義できます。
- **NX_PPP_PASSWORD_SIZE**: 認証で使用される "パスワード" 文字列のサイズを指定します。 既定値は 32 バイトに設定されていますが、*nx_ppp.h* をインクルードする前に再定義できます。
- **NX_PPP_PROTOCOL_TIMEOUT**: PPP タスクが PPP プロトコル要求メッセージへの応答を受信するための待機オプション (秒単位) を定義します。 既定値は 4 秒です。
- **NX_PPP_RECEIVE_TIMEOUTS**: PPP スレッド タスクが、PPP メッセージ ストリーム内の次の文字の受信を待機してタイムアウトする回数を定義します。 その後、PPP はパケットを解放し、次の PPP メッセージの受信待機を開始します。 既定値は 4 ですが、
- **NX_PPP_SERIAL_BUFFER_SIZE**: 受信文字のシリアル バッファーのサイズを指定します。 この値は既定では 3,000 バイトです。 この定義は、*nx_ppp.h* をインクルードする前にアプリケーションで設定できます。
- **NX_PPP_TIMEOUT**: データを送信するためのパケットを割り当て、IP 層に送信するために PPP シリアル データをパケットにバッファーするときの待機オプション (タイマー刻み) を定義します。 既定値は、4*NX_IP_PERIODIC_RATE (400 ティック) です。
- **NX_PPP_THREAD_TIME_SLICE**: PPP スレッドのタイムスライス オプション。 この値は既定では TX_NO_TIME_SLICE です。 この定義は、*nx_ppp.h* をインクルードする前にアプリケーションで設定できます。
- **NX_PPP_VALUE_SIZE**: CHAP 認証で使用される "値" 文字列のサイズを指定します。 既定値は 32 バイトに設定されていますが、nx_ppp.h をインクルードする前に再定義できます。