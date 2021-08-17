---
title: 第 2 章 - Azure RTOS NetX Duo BSD のインストールと使用
description: この章には、Azure RTOS NetX Duo BSD コンポーネントのインストール、設定、使用に関連するさまざまな問題の説明が含まれています。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 560621e528c8ce98013ce505ea1511f466317f4a087aa44cc0e70cb4d4b8ed1e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788509"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-bsd"></a>第 2 章 - Azure RTOS NetX Duo BSD のインストールと使用

この章には、Azure RTOS NetX Duo BSD コンポーネントのインストール、設定、使用に関連するさまざまな問題の説明が含まれています。

## <a name="product-distribution"></a>製品の配布

Azure RTOS NetX Duo BSD は、[https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) のパブリック ソース コード リポジトリから入手できます。 このパッケージには、次のように 2 つのソース ファイルと、このドキュメントを含む PDF ファイルが含まれています。

- **nxd_bsd.h**: NetX Duo BSD のヘッダー ファイル
- **nxd_bsd.c**: NetX Duo BSD の C ソース ファイル
- **nxd_bsd.pdf**: NetX Duo BSD のユーザー ガイド

デモ ファイル:

- **bsd_demo_udp.c**
- **bsd_demo_tcp.c**
- **bsd_demo_raw.c**

## <a name="netx-duo-bsd-installation"></a>NetX Duo BSD のインストール

NetX Duo BSD を使用するためには、前述のディストリビューション全体を、NetX Duo がインストールされているのと同じディレクトリにコピーする必要があります。 たとえば、NetX Duo がディレクトリ " *\threadx\arm7\green*" にインストールされている場合は、このディレクトリに *nxd_bsd.h* および *nxd_bsd.c* ファイルをコピーする必要があります。

## <a name="building-the-threadx-and-netx-duo-components-of-a-bsd-application"></a>BSD アプリケーションの ThreadX および NetX Duo コンポーネントのビルド

### <a name="threadx"></a>ThreadX

ThreadX ライブラリでは、スレッド ローカル ストレージ内に `bsd_errno` を定義する必要があります。 次の手順をお勧めします。

1. *tx_port.h* で、次のようにいずれかの TX_THREAD_EXTENSION マクロを設定します。
   - `#define TX_THREAD_EXTENSION_3     int bsd_errno`

1. ThreadX ライブラリをリビルドします。

> [!NOTE]
> TX_THREAD_EXTENSION_3 が既に使用されている場合、ユーザーは、他の TX_THREAD_EXTENSION マクロのいずれかを自由に使用できます。

### <a name="netx-duo"></a>NetX Duo

NetX Duo BSD サービスを使用する前に、NX_ENABLE_EXTENDED_NOTIFY_SUPPORT を定義して NetX Duo ライブラリをビルドする必要があります。 これは、既定では定義されていません。 BSD RAW ソケットを使用する場合は、NX_ENABLE_IP_RAW_PACKET_FILTER を定義して NetX Duo ライブラリをビルドする必要があります。

## <a name="using-netx-duo-bsd"></a>NetX Duo BSD の使用

NetX Duo BSD アプリケーション プロジェクトでは、このガイドの後半で詳述されている BSD サービスを使用できるように、*tx_api.h* と *nx_api.h* のインクルード後に *nxd_bsd.h* をインクルードする必要があります。 アプリケーションのビルド プロセスでは、*nx_bsd.c* もインクルードする必要があります。 このファイルは、他のアプリケーション ファイルと同様にコンパイルする必要があり、そのオブジェクト形式は、アプリケーションのファイルと一緒にリンクする必要があります。 NetX Duo BSD を使用するために必要なものは、これですべてです。

NetX Duo BSD サービスを利用するには、アプリケーションでの IP インスタンスの作成、パケットを割り当てるための BSD レイヤー用のパケット プールの作成、内部 BSD スレッド スタックのためのメモリ領域の割り当て、内部 BSD スレッドの優先順位の指定を行う必要があります。 BSD レイヤーは、*bsd_initialize* を呼び出してパラメーターを渡すことによって初期化されます。 これについては、このドキュメントの後の方にある "小規模な例" で説明しますが、プロトタイプを下に示します。

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                    *CHAR *bsd_thread_stack_area,
                    *ULONG bsd_thread_stack_size,
                    *UINT bsd_thread_priority*);
```

default_ip は、BSD レイヤーの動作場所の IP インスタンスです。 default_pool は、パケットを割り当てるために、BSD サービスによって使用されます。 2 つのパラメーター bsd_thread_stack_area と bsd_thread_stack_size では内部 BSD スレッドによって使用されるスタック領域を定義し、最後のパラメーター bsd_thread_priority ではスレッドの優先順位を設定します。

## <a name="netx-duo-bsd-raw-socket-support"></a>NetX Duo BSD RAW ソケットのサポート

NetX Duo BSD では、RAW ソケットもサポートされています。 NetX Duo BSD で RAW ソケットを使用するには、NX_ENABLE_IP_RAW_PACKET_FILTER を定義して NetX Duo ライブラリをコンパイルする必要があります。 これは、既定では定義されていません。 次に、アプリケーションで *nx_ip_raw_packet_enable* を呼び出すことによって、以前に作成した IP インスタンスで RAW ソケットの処理を有効にする必要があります。

NetX Duo BSD で RAW ソケットを作成するには、アプリケーションで、ソケット作成サービスの *socket* を使用して、プロトコル ファミリ、ソケットの種類、プロトコルを指定します。

```c
sock_1 = socket(INT protocolFamily, INT socket_type, INT protocol)
```

protocolFamily は、IPv4 ソケットの場合は AF_INET です。または、IP インスタンスで IPv6 が有効になっていると仮定すれば、IPv6 ソケットの場合は AF_INET6 となります。 socket_type は SOCK_RAW に設定する必要があります。 protocol はアプリケーション固有です。

アプリケーションでは、RAW パケットを送受信したり、RAW ソケットを閉じたりするために、通常は UDP の場合と同じ *sendto、recvfrom、select*、*soc_close* などの BSD サービスを使用します。 RAW ソケットでは、BSD サービスの *accept* や *listen* はどちらもサポートされていません。

- 既定では、受信した IPv4 生データには IPv4 ヘッダーが含まれています。  逆に、受信した IPv6 生データには IPv6 ヘッダーが含まれていません。

- 既定では、IPv6 または IPv4 のいずれかの RAW パケットを送信するときには、BSD ラッパー レイヤーによって、データの送信前に IPv6 または IPv4 ヘッダーが追加されます。

NetX Duo BSD では、IP_RAW_RX_NO_HEADER、IP_HDRINCL、IP_RAW_IPV6_HDRINCL などの追加の RAW ソケット オプションがサポートされています。

IP_RAW_RX_NO_HEADER が設定されている場合は、受信したデータに IPv4 ヘッダーが含まれないように IPv4 ヘッダーが削除され、報告されるメッセージ長には IPv4 ヘッダーは含まれません。  IPv6 ソケットの場合、既定では RAW ソケットの受信に IPv6 ヘッダーは含まれません。これは、IP_RAW_RX_NO_HEADER オプションを設定した場合と同じです。 アプリケーションでは、*setsockopt* サービスを使用して IP_RAW_RX_NO_HEADER オプションを解除できます。IP_RAW_RX_NO_HEADER オプションが解除されると、受信した IPv6 生データには IPv6 ヘッダーが含まれるようになり、報告されるメッセージ長には IPv6 ヘッダーが含められます。

このオプションは、IPv4 や IPv6 の転送されるデータには影響を与えません。

IP_HDRINCL が設定されている場合、アプリケーションでは、データ送信時に IPv4 ヘッダーが含められます。  このオプションは、IPv6 転送には影響を与えず、既定では定義されません。 IP_RAW_IPV6_HDRINCL が設定されている場合、アプリケーションでは、データ送信時に IPv6 ヘッダーが含められます。  このオプションは、IPv4 転送には影響を与えず、既定では定義されません。

IP_HDRINCL と IP_RAW_IPV6_HDRINCL は、IPv4 または IPv6 の受信には影響を与えません。

> [!NOTE]
> BSD 4.3 ソケットの仕様では、カーネルによって RAW パケットを各ソケットの受信バッファーにコピーする必要があると規定されています。 ただし NetX Duo BSD では、同じプロトコルを共有するソケットが複数作成された場合は動作が未定義になります。

## <a name="netx-duo-bsd-raw-packet-support"></a>NetX Duo BSD RAW パケットのサポート

PPPoE での RAW パケットのサポートを有効にするには、NX_BSD_RAW_PPPOE_SUPPORT を有効にして、NetX Duo BSD ラッパーをビルドする必要があります。

次のコマンドでは、PPPoE の RAW パケットを処理するための BSD ソケットが作成されます。

```c
Sockfd = socket(AF_PACKET, SOCK_RAW, protocol);
```

現在の BSD 実装では、AF_PACKET ファミリの 2 種類のプロトコルのみがサポートされています

- `ETHERTYPE_PPPOE_DISC`: PPPoE の検出パケット。 MAC データ フレーム内では、検出パケットのイーサネット フレームの種類は 0x8863 です。

- `ETHERTYPE_PPPOE_SESS`: PPP のセッション パケット。 MAC データ フレーム内では、セッション パケットのイーサネット フレームの種類は 0x8864 です。

構造体 `sockaddr_ll` は、PPPoE フレームの送受信時にパラメーターを指定するために使用されます。

`struct sockaddr_ll` は次のように宣言されています。

```c
struct sockaddr_ll
{
    USHORT  sll_family;     /* Must be AF_PACKET */
    USHORT  sll_protocol;   /* LL frame type */
    INT     sll_ifindex;    /* Interface Index. */
    USHORT  sll_hatype;     /* Header type */
    UCHAR   sll_pkttype;    /* Packet type */
    UCHAR   sll_halen;      /* Length of address */
    UCHAR   sll_addr[8];    /* Physical layer address */
};
```

> [!NOTE]
> 構造体のすべてのフィールドが `sendto()` または `recvfrom()` によって使用されるわけではありません。 PPPoE パケットを送受信するために `sockaddr_ll` を設定する方法については、下記の説明を参照してください。

指定されるプロトコルとは無関係に、AF_PACKET ファミリで作成されたソケットを使用して、PPPoE 検出パケットまたは PPP セッション パケットのいずれかを送信できます。 PPPoE パケットの送信時には、MAC ヘッダー (宛先 MAC アドレス、送信元 MAC アドレス、フレームの種類) を含め、適切な形式の PPPoE フレームが含まれるバッファーを、アプリケーションで準備する必要があります。バッファーのサイズには、14 バイトのイーサネット ヘッダーが含まれます。

`sockaddr_ll` 構造体の `sll_ifindex` は、このパケットの送信に使用される物理インターフェイスを指定するために使用されます。 この構造体の残りのフィールドは使用されません。 使用されないフィールドに設定された値は、BSD 内部プロセスによって無視されます。

次のコード ブロックは、PPPoE パケットの送信方法を示しています。

```c
struct sockaddr_ll peer_addr;

/* Transmit a PPPoE frame using the primary network interface. */
peer_addr.sll_ifindex = 0;
n = sendto(sockfd, frame, frame_size, 0, (struct
        sockaddr*)&peer_addr, sizeof(peer_addr));
```

戻り値では、転送されたバイト数が示されます。 PPPoE パケットはメッセージベースであるため、転送が成功すると、送信されたバイト数は (14 バイトのイーサネット ヘッダーを含む) パケットのサイズと一致します。

PPPoE パケットは、`recvfrom()` を使用して受信できます。 受信バッファーは、イーサネットの MTU サイズのメッセージを格納するのに十分な大きさである必要があります。 受信した PPPoE パケットには、14 バイトのイーサネット ヘッダーが含まれています。 PPPoE パケットの受信時には、`ETHERTYPE_PPPOE_DISC` プロトコルを使用して作成されたソケットでのみ、PPPoE 検出パケットを受信できます。 同様に、`ETHERTYPE_PPPOE_SESS` プロトコルを使用して作成されたソケットでのみ、PPP セッション パケットを受信できです。 同じ種類のプロトコルに対して複数のソケットが作成された場合、到着する PPPoE パケットは、最初に作成されたソケットに転送されます。 そのプロトコルに対して作成された最初のソケットが閉じられると、作成順序で次のソケットが、これらのパケットの受信に使用されます。

PPPoE パケットの受信後は、`sockaddr_ll` 構造体の以下のフィールドが有効になります。
- **sll_family**: AF_PACKET になるように BSD 内部で設定されます
- **sll_ifindex**: パケットを受信したインターフェイスを示します
- **sll_protocol**: 受信したパケットの種類に設定されます。`ETHERTYPE_PPPOE_DISC` または `ETHERTYPE_PPPOE_SESS` です

## <a name="eliminating-internal-bsd-thread"></a>内部 BSD スレッドの除去

既定では、BSD では処理の一部を実行するために内部スレッドが利用されます。 メモリの制約が厳しいシステムでは、NX_BSD_TIMEOUT_PROCESS_IN_TIMER を定義して BSD をビルドできます。これにより、内部 BSD スレッドが除去され、その代わりに、同じ処理を実行するために内部タイマーが使用されます。 これで、内部 BSD スレッドの制御ブロックとスタックに必要なメモリがなくなります。 ただし、全体としてのタイマー処理は大幅に増加し、BSD の処理が必要以上に高い優先順位で実行される可能性もあります。

ThreadX タイマーのコンテキストで実行するように BSD ソケットを構成するには、*nxd_bsd.h* で NX_BSD_TIMEOUT_PROCESS_IN_TIMER を定義します。 タイマー コンテキストで BSD タスクを実行するように BSD レイヤーが構成されている場合、*bsd_initialize* の呼び出しでは以下の 3 つのパラメーターは無視されます。これらは NULL に設定する必要があります。

- **bsd_thread_stack_area**
- **bsd_thread_stack_size**
- **bsd_thread_priority**

## <a name="netx-duo-bsd-with-dns-support"></a>DNS のサポートが有効な NetX Duo BSD

NX_BSD_ENABLE_DNS が定義されている場合は、NetX Duo BSD で、ホスト名またはホスト IP の情報を取得する DNS クエリを送信できます。 この機能では、*nx_dns_create* サービスを使用して、NetX DNS クライアントを事前に作成しておく必要があります。 DNS インスタンスには、1 つ以上の既知の DNS サーバーの IP アドレスを登録する必要があります。IPv4 サーバーのアドレスを追加するには *nx_dns_server_add* サービスを使用し、IPv4 または IPv6、いずれかのサーバー アドレスを追加するには *nxd_dns_server_add* サービスを使用します。

DNS のサービスとメモリ割り当ては、*getaddrinfo* および *getnameinfo* サービスによって使用されます。

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
        const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
        char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

BSD アプリケーションがホスト名を使用して *getaddrinfo* を呼び出すと、NetX BSD では、以下のいずれかのサービスを呼び出して IP アドレスを取得します。

- **nx_dns_ipv4_address_by_name_get**
- **nxd_dns_ipv6_address_by_name_get**
- **nx_dns_cname_get**

*nx_dns_ipv4_address_by_name_get* と *nxd_dns_ipv6_address_by_name_get* の場合、NetX BSD では、それぞれ、ipv4_addr_buffer と ipv6_addr_buffer のメモリ領域が使用されます。 これらのバッファーのサイズは、それぞれ、(NX_BSD_IPV4_ADDR_PER_HOST * 4) と (NX_BSD_IPV6_ADDR_PER_HOST * 16) によって定義されます。

*getaddrinfo* からのアドレス情報を返すために、NetX BSD では、ThreadX ブロック メモリ テーブル nx_bsd_addrinfo_pool_memory を使用します。このメモリ領域は、構成可能な別のオプション セットである NX_BSD_IPV4_ADDR_MAX_NUM と NX_BSD_IPV6_ADDR_MAX_NUM によって定義されます。

上の構成オプションの詳細については、「**全般的構成オプション**」を参照してください。

さらに、NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されており、ホスト入力が正規名である場合、NetX BSD では、以前に作成されたブロック プール `_nx_bsd_cname_block_pool からメモリを動的に割り当てます

> [!NOTE]
> *getaddrinfo* の呼び出し後、*freeaddrinfo* サービスを使用して、res 引数によって指し示されたメモリを解放してブロック テーブルに戻す処理は、BSD アプリケーションで行う必要があります。

## <a name="netx-duo-bsd-limitations"></a>NetX Duo BSD の制限事項

パフォーマンスやアーキテクチャの問題のため、NetX Duo BSD では、BSD 4.3 ソケット機能のすべてがサポートされているわけではありません。

INT フラグは、*send、recv、sendto*、*recvfrom* の呼び出しではサポートされていません。

## <a name="general-configuration-options"></a>全般的構成オプション

*nxd_bsd.h* 内で、ユーザーが構成できるオプションを指定することで、特定のアプリケーション要件に合わせて NetX Duo BSD ソケットを微調整することができます。

以下に、コンパイル時に設定される構成可能なオプションの一覧を示します。

- **NX_BSD_TCP_WINDOW**: TCP ソケットの作成呼び出しで使用されます。 64k が 100 MB イーサネットでの標準的なウィンドウ サイズです。 既定値は、65535 です。

- **NX_BSD_SOCKFD_START**: これは、BSD ソケットのファイル記述子の開始値を表す論理インデックスです。 既定では、このオプションは 32 です。

- **NX_BSD_MAX_SOCKETS**: BSD レイヤーで使用できるソケットの合計最大数を指定します。32 の倍数にする必要があります。 この値は、既定で 32 に設定されます。

- **NX_BSD_SOCKET_QUEUE_MAX**: 受信ソケット キューに格納される UDP パケットの最大数を指定します。 この値は、既定で 5 に設定されています。

- **NX_BSD_MAX_LISTEN_BACKLOG**: これで、BSD TCP ソケットのリッスン キュー ("バックログ") のサイズを指定します。 既定値は 5 です。

- **NX_MICROSECOND_PER_CPU_TICK**: スケジューラのタイマー ティックあたりのマイクロ秒数を指定します。

- **NX_BSD_TIMEOUT**: BSD によって求められている、NetX Duo 内部呼び出しでのタイマー ティックのタイムアウトを指定します。 既定値は (20 × NX_IP_PERIODIC_RATE) です。

- **NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: NetX Duo 切断呼び出しでのタイマー ティックのタイムアウトを指定します。 既定値は 1 です。

- **NX_BSD_PRINT_ERRORS**: 設定されている場合、BSD 関数のエラー状態の戻りにおいて、エラーが発生した行番号とエラーの種類 (NX_SOC_ERROR など) が返されます。 このためアプリケーション開発者は、デバッグ出力を定義する必要があります。 既定の設定は無効であり、*nxd_bsd.h* ではデバッグ出力が指定されていません。

- **NX_BSD_TIMER_RATE**: BSD の定期的なタイマー タスクが実行されるまでの間隔。 既定値は 1 秒 (1 * NX_IP_PERIODIC_RATE) です。

- **NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: 設定されている場合、このオプションにより、BSD タイムアウト プロセスをシステム タイマーのコンテキストで実行できます。 既定の動作は無効です。 この機能については、第 2 章「NetX Duo BSD のインストールと使用」で詳細に説明されています。

- **NX_BSD_RAW_PPPOE_SUPPORT**: PPPoE での RAW パケットのサポートを有効にします。 既定では、このオプションは有効になりません。

- **NX_BSD_ENABLE_DNS**: 有効になっている場合、NetX Duo BSD により、ホスト名またはホスト IP アドレスの DNS クエリが送信されます。 DNS クライアント インスタンスが事前に作成され、起動されている必要があります。 既定では、有効になっていません。

- **NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: RAW ソケット テーブルのサイズを定義します。 値は 2 の累乗にする必要があります。 NetX BSD では、RAW パケットを送受信するために、NX_BSD_SOCKETS 型のソケットの配列が作成されます。 NX_ENABLE_IP_RAW_PACKET_FILTER が有効になっている必要があります。 既定では 32 です。

- **NX_BSD_IPV4_ADDR_MAX_NUM**: *getaddrinfo* によって返される IPv4 アドレスの最大数。 *getaddrinfo* でのアドレス情報の格納にメモリを動的に割り当てるため、これを NX_BSD_IPV6_ADDR_MAX_NUM と一緒に使用して、NetX BSD ブロック プール nx_bsd_addrinfo_block_pool のサイズを定義します。 既定値は 5 です。

- **NX_BSD_IPV6_ADDR_MAX_NUM**: *getaddrinfo* によって返される IPv6 アドレスの最大数。 *getaddrinfo* でのアドレス情報の格納にメモリを動的に割り当てるため、これを NX_BSD_IPV4_ADDR_MAX_NUM と一緒に使用して、NetX BSD ブロック プール nx_bsd_addrinfo_block_pool のサイズを定義します。

- **NX_BSD_IPV4_ADDR_PER_HOST**: DNS クエリごとに格納される IPv4 アドレスの最大数を定義します。 既定値は 5 です。

- **NX_BSD_IPV6_ADDR_PER_HOST**: DNS クエリごとに格納される IPv6 アドレスの最大数を定義します。 既定値は 2 です。

## <a name="bsd-socket-options"></a>BSD ソケット オプション

以下の一覧に示した NetX Duo BSD ソケット オプションは、*setsockopt* サービスを使用して、ソケットごとに実行時に有効 (または無効) にすることができます。

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, 
                const void *option_value, INT option_length);
```

option_level には、2 つの異なる設定があります。

実行時のソケット オプションの最初の種類は、ソケット レベルのオプションのための SOL_SOCKET です。 ソケット レベルのオプションを有効にするには、option_level を SOL_SOCKET に設定し、option_name を SO_BROADCAST *などの特定のオプションに設定して *setsockopt* を呼び出します。* オプション設定を取得するには、option_level を再び SOL_SOCKET に設定して option_name に対する *getsockopt* を呼び出します。

以下に、実行時のソケット レベルのオプションの一覧を示します。

- **SO_BROADCAST**: 設定されている場合、NetX ソケットからのブロードキャスト パケットの送受信が可能になります。 これは NetX Duo の既定の動作です。 すべてのソケットがこの機能を備えています。

- **SO_ERROR**: *getsockopt* サービスを使用して、指定したソケットの以前のソケット操作に関するソケット状態を取得するために使用されます。 すべてのソケットがこの機能を備えています。

- **SO_KEEPALIVE**: 設定されている場合、TCP キープ アライブ機能が有効になります。 これを使用するには、*nx_user.h* で NX_TCP_ENABLE_KEEPALIVE を定義して、NetX Duo ライブラリをビルドする必要があります。 既定では、この機能は無効になります。

- **SO_RCVTIMEO**: NetX Duo BSD ソケットでパケットを受信するための待機オプションを秒単位で設定します。 既定値は NX_WAIT_FOREVER (0xFFFFFFFF) です。または、非ブロッキングが有効になっている場合は NX_NO_WAIT (0x0) です。

- **SO_RCVBUF**: TCP ソケットのウィンドウ サイズを設定します。 既定値の NX_BSD_TCP_WINDOW は、BSD TCP ソケットでは 64k に設定されます。 65535 を超えるサイズを設定するには、NX_TCP_ENABLE_WINDOW_SCALING を定義して、NetX ライブラリをビルドする必要があります。

- **SO_REUSEADDR**: 設定されている場合、複数のソケットを 1 つのポートにマップできるようになります。 典型的な使い方は TCP サーバー ソケット用です。 これは NetX Duo ソケットの既定の動作です。

実行時のソケット オプションの 2 番目の種類は、IP オプションのレベルです。 IP レベルのオプションを有効にするには、option_level を IP_PROTO に設定し、option_name を IP_MULTICAST_TTL *などのオプションに設定して、*setsockopt* を呼び出します。* オプション設定を取得するには、option_level を再び IP_PROTO に設定して option_name に対する *getsockopt* を呼び出します。

以下に、実行時の IP レベルのオプションの一覧を示します。

- **IP_MULTICAST_TTL**: UDP ソケットの有効期限を設定します。 ソケットが作成されるときの既定値は NX_IP_TIME_TO_LIVE (0x80) です。 この値は、このソケット オプションで *setsockopt* を呼び出してオーバーライドできます。

- **IP_RAW_IPV6_HDRINCL**: このオプションが設定されている場合は、呼び出し元のアプリケーションで、BSD によって作成された RAW IPv6 ソケットで送信されようとしているデータに、IPv6 ヘッダーとアプリケーション ヘッダー (省略可能) を追加する必要があります。 このオプションを使用するには、その IP タスクで RAW ソケットの処理が有効になっている必要があります。

- **IP_ADD_MEMBERSHIP**: このオプションが設定されている場合、BSD ソケット (UDP ソケットにのみ該当) が、指定された IGMP グループに参加できるようになります。

- **IP_DROP_MEMBERSHIP**: このオプションが設定されている場合、BSD ソケット (UDP ソケットにのみ該当) が、指定された IGMP グループから離脱できるようになります。

- **IP_HDRINCL**: このオプションが設定されている場合は、呼び出し元のアプリケーションで、BSD で作成された RAW IPv4 ソケットで送信されようとしているデータに、IP ヘッダーとアプリケーション ヘッダー (省略可能) を追加する必要があります。 このオプションを使用するには、その IP タスクで RAW ソケットの処理が有効になっている必要があります。

- **IP_RAW_RX_NO_HEADER**: 解除されている場合、BSD で作成された RAW IPv6 ソケットの受信データに、IPv6 ヘッダーが含められます。 BSD の RAW IPv6 ソケット内のIPv6 ヘッダーは既定で削除され、パケット長に IPv6 ヘッダーは含まれません。

設定されている場合、種類が IPv4 である BSD RAW ソケットで受信したデータから、IPv4 ヘッダーが削除されます。 IPv4 ヘッダーは、既定では BSD の RAW IPv4 ソケットに含められ、パケット長に IPv4 ヘッダーが含まれています。

このオプションは、IPv4 や IPv6 のどちらの転送データにも影響を与えません。

## <a name="small-ipv4-example"></a>小規模な IPv4 の例

以下では、IPv4 ネットワークで NetX Duo BSD サービスを使用する方法の例について説明します。 この例では、インクルード ファイル *nxd_bsd.h* が 8 行目で組み込まれています。 次に、IP インスタンス *bsd_ip* とパケット プール *bsd_pool* が、20 行目と 21 行目でグローバル変数として作成されています。 このデモでは、RAM (仮想) ネットワーク ドライバー *_nx_ram_network_driver* を使用していることに注意してください。 この例では、クライアントとサーバーが 1 つの IP インスタンス上で同じ IP アドレスを共有します。

クライアントとサーバーのスレッドは、62 行目と 68 行目で作成されています。 パケット転送用の BSD パケット プールは、78 行目に作成されて、87 行目で IP インスタンスの作成に使用されています。 *nx_ip_create* 呼び出しでは、IP スレッド タスクに優先度 1 が付与されていることに注意してください。 最適な NetX パフォーマンスを得るためには、プログラムで、このスレッドが最も優先度の高いタスクとして定義されている必要があります。

IP インスタンスは、ARP サービスと TCP サービスに対して、それぞれ 88 行目と 110 行目で有効にされています。 BSD サービスが使用可能になる前の最後の要件は、120 行目にある、BSD で必要とされるすべてのデータ構造体と NetX および ThreadX のリソースを設定するための、*bsd_initialize* の呼び出しです。

次に、サーバー スレッドのエントリ関数が定義されています。 BSD TCP ソケットは、149 行目で作成されています。 サーバーの IP アドレスとポートは、160 ～ 163 行目で設定されています。 IP アドレスとポートに適用される、ホスト バイト オーダーからネットワーク バイト オーダーへのマクロ *htonl* および *htons* の使用に注意してください。 これは、マルチ バイト データはネットワーク バイト オーダーで BSD サービスに送信される BSD ソケット仕様に準拠しています。

次に、166 行目では、*bind* サービスを使用して、マスター サーバー ソケットがポートにバインドされています。 これが、180 行目の *listen* サービスを使用した TCP 接続要求のリッスン ソケットです。 ここから、サーバー スレッド関数 *thread_server_entry* は、202 行目の *select* 呼び出しを使用して、受信イベントの確認をループします。 受信イベントが接続要求である場合は (読み取り準備リストの比較によって特定されます)、213 行目で *accept* を呼び出します。 子サーバー ソケットは、接続要求を処理するために割り当てられ、223 行目のクライアントに接続される TCP サーバー ソケットのマスター リストに追加されます。 新しい接続要求がない場合、サーバー スレッドは次に、236 行目から始まる for ループで、現在接続されているすべてのソケットについて、受信イベントがないか確認します。 待機中の受信イベントが検出されると、データが受信されなくなり (逆側で接続が閉じた)、277 行目の *soc_close* サービスを使用してソケットが閉じられるまで、そのソケットで *send* と *recv* が呼び出されます。

サーバー スレッドの設定後、クライアント スレッドのエントリ関数 *thread_client_entry* により、326 行目でのソケットの作成と、337 行目での *connect* 呼び出しを使用した TCP サーバー ソケットとの接続が行われます。 その後は、パケットの送信と受信のループを、それぞれ *send* サービスと *recv* サービスを使用して行います。 それ以上データを受信しないときには、398 行目で、*soc_close* サービスを使用してソケットが閉じられます。 接続の切断後、クライアント スレッドのエントリ関数によって、新しい TCP ソケットが作成され、321 行目で開始される while ループ内で別の接続要求が作成されます。

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection, sending,
and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQR
    STUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */

ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */

VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */
int     main()
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

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool", 128,
                                pointer, 16384);

    pointer = pointer + 16384;
    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                    0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                    pointer, 2048, 1);
                    pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable ARP \n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize (&bsd_ip, &bsd_pool,pointer, 2048, 2);
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT       status, sock, sock_tcp_server;
ULONG     actual_status;
INT       Clientlen;
INT       i;
UINT      is_set = NX_FALSE;
struct    sockaddr_in serverAddr;
struct    sockaddr_in ClientAddr;

    tx_thread_sleep(100);

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
        &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("Error on Server socket %d create \n", sock_tcp_server);
        return;
    }

    printf("Server socket %d created\n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin_family = AF_INET;
    serverAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    serverAddr.sin_port = htons(SERVER_PORT);

    /* Bind this server socket */
    status = bind (sock_tcp_server, (struct sockaddr *) &serverAddr,
                sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error on Server Socket %d Bind \n", sock_tcp_server);
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen (sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error on Server Socket %d Listen\n", sock_tcp_server);
        return;
    }
    else
        printf("Server socket %d listen complete\n", sock_tcp_server);

    /* All set to accept client connections */

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ((status == 0xFFFFFFFF) || (status == 0))
        {

            printf("Error with select. Status 0x%x\n", status);

            continue;
        }

        /* Check for a connection request. */
        is_set = FD_ISSET(sock_tcp_server, &read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,(struct sockaddr*)&ClientAddr,
                        &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i , &master_list)) &&
                (FD_ISSET(i , &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server received no data from Client on
                            socket %d)\n", i);
                        break;
                    }
                    else if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server receiving data from Client on
                            socket %d\n", i);
                        break;
                    }
                    if(status == SERVER_RCV_BUFFER_SIZE) status--;
                    Server_Rcv_Buffer[status] = 0;
                    printf("Server socket %d received %d bytes: %s\n ",
                            i, (ULONG)status, Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                        Client\n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                        Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != NX_SOC_ERROR)
                {
                    printf("Server socket %d closed \n", i);
                }
                else
                {
                    printf("Error on closing Server socket %d \n", i);
                }
            }
        }

    /* Loop back to check any next client connection */
    }
}

CHAR     Client_Rcv_Buffer[100];

VOID     thread_client_entry(ULONG thread_input)
{

INT        status;
INT        sock_tcp_client, length;
struct     sockaddr_in echoServAddr;
struct     sockaddr_in localAddr; /

    /* Let the server side get set up. */
    tx_thread_sleep(200);

    /* Set local port for displaying IP address and port. */
    memset(&localAddr, 0, sizeof(localAddr));
    localAddr.sin_family = AF_INET;
    localAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    localAddr.sin_port = htons(CLIENT_PORT);

    /* Set server port and IP address which we need to connect. */
    memset(&echoServAddr, 0, sizeof(echoServAddr));
    echoServAddr.sin_family = AF_INET;
    echoServAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    echoServAddr.sin_port = htons(SERVER_PORT);

    /* Now make client connections with the server. */
    while (1)
    {

        printf("\n");

        /* Create BSD TCP Socket */
        sock_tcp_client = socket( AF_INET, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n", sock_tcp_client);
            return;
        }

        printf("Client socket %d created\n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr,
                        sizeof(echoServAddr));

        /* Check for error. */
        if (status != OK)
        {
            printf("Error on Client socket %d connect\n", sock_tcp_client);
                    soc_close(sock_tcp_client);
            return;
        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr,
                            &length);

        printf("Client port = %lu , Client = 0x%x,",
            htonl(localAddr.sin_port), htonl(localAddr.sin_addr.s_addr));

        length = sizeof(struct sockaddr_in);

        status = getpeername( sock_tcp_client, (struct sockaddr *)
                            &echoServAddr, &length);

        printf("Remote port = %lu, Remote IP = 0x%x \n",
                htonl(echoServAddr.sin_port),
                htonl(echoServAddr.sin_addr.s_addr));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
            sock_tcp_client);

            status = send(sock_tcp_client, "Hello", (sizeof("Hello")), 0);

            if (status == ERROR)
            {
                printf("Error: Client Socket (%d) send \n", sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,100,0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    380 printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Nothing received by Client on socket %d\n",
                            sock_tcp_client);
                }

                break;
            }
            else
            {
                printf("Client socket %d received %d bytes: %s\n",
                        sock_tcp_client,
                        status, Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = soc_close(sock_tcp_client);

        if (status != ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```

## <a name="small-ipv6-example-system"></a>小規模な IPv6 システムの例

IPv6 ネットワークで NetX Duo BSD サービスを使用する方法の例を、下記のプログラムで説明します。 この例は、前に説明した IPv4 デモ プログラムによく似ていますが、重要な違いがいくつかあります。

クライアントとサーバーのスレッド、BSD パケット プール、IP インスタンス、および BSD の初期化は、IPv4 BSD ソケットの場合と同様に行われます。

サーバー スレッド エントリ関数 *thread_server_entry* では、145 ～ 148 行で *sockaddr_in6* および *NXD_ADDRESS* データ型を使用して一対の IPv6 変数を定義しています。 実際には、NXD_ADDRESS データ型には IPv4 と IPv6 の両方の種類のアドレスを格納できます。

次に、サーバー スレッドにより、IP インスタンスでの IPv6 と ICMPv6 がそれぞれ 161 行目と 169 行目で、*nxd_ipv6_enable* および *nxd_icmpv6_enable* サービスを使用して有効にされています。 次に、その IP インスタンスに、リンク ローカルとグローバルの IP アドレスが登録されます。 これは、180 行目と 195 行目で *nxd_ipv6_address_set* サービスを使用して行われています。 次に、IP スレッドのタスクが重複アドレス検出プロトコルを完了するのに十分な時間スリープ状態になり、201 行目の *tx_thread_sleep* の呼び出しで、これらのアドレスを有効なアドレスとして登録しています。

次に 204 行目で、ソケットの種類の入力引数として AF_INET6 を指定して、TCP サーバー ソケットを作成しています。 ソケットの IPv6 アドレスとポートは 216 ～ 221 行目で設定されています。この場合も、BSD ソケット サービスにはネットワーク バイト オーダーでデータを提供するため、*htonl* マクロと *htons* マクロを使用していることに注目してください。 ここからは、このサーバー スレッド エントリ関数は、IPv4 の例と事実上同じです。

次に、クライアント スレッド エントリ関数 *thread_client_entry* が定義されています。 この例の TCP クライアントは、TCP サーバーと同じ IP インスタンスおよび IPv6 アドレスを共有するため、IP インスタンスでもう一度 IPv6 サービスや ICMPv6 サービスを有効にする必要はありません。 さらに、この IPv6 アドレスも既に、IP インスタンスに登録されています。 そうしないで、クライアント スレッド エントリ関数は単純に、368 行目でサーバーが設定されるのを待機しています。 387 ～ 392 行目でホスト バイト オーダーからネットワーク バイト オーダーへのマクロを使用して、サーバーのアドレスとポートが設定された後、クライアントは 412 行目で、TCP サーバーに接続することができます。 378 ～ 383 行目のローカル IP アドレスのデータ型は、それぞれ 425 行目と 434 行目の *getsockname* サービスと *getpeername* サービスを示すためにのみ使用されていることに注意してください。 データはネットワークから着信するため、378 ～ 383 行目で、ネットワーク バイト オーダーからホスト バイト オーダーへのマクロが使用されています。

次に、クライアント スレッド エントリ関数はループに入り、そこで、それ以上データが受信されなくなるまで TCP ソケットの作成、TCP 接続の作成、TCP サーバーとのデータの送受信を行います。これは事実上、IPv4 の例と同じです。 次に、483 行目でソケットを閉じ、短時間一時停止して別の TCP ソケットを作成し、TCP サーバー接続を要求します。

IPv4 の例との重要な違いの 1 つは、*socket* 呼び出しで、入力引数として AF_INET6 を使用して IPv6 ソケットを指定することです。 もう 1 つの重要な違いは、TCP クライアントの *connect* 呼び出しでは、*sockaddr_in6* データ型と、*sockaddr_in6* データ型のサイズに設定された長さの引数を取ることです。

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection,
disconnection, sending, and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */
ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */
VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

int     main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{
CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool",
    128, pointer, 16384);

    pointer = pointer + 16384;

    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                        0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in enable ARP on BSD IP instance\n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 2);

    /* Check BSD initialize status. */
    if (status)
    {
        error_counter++;
        printf("Error in BSD initialize \n");
    }

    pointer = pointer + 2048;
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT             status, sock, sock_tcp_server;
ULONG           actual_status;
INT             Clientlen;
INT             i;
UINT            is_set = NX_FALSE;
NXD_ADDRESS     ip_address;
struct          sockaddr_in6 serverAddr;
struct          sockaddr_in6 ClientAddr;
UINT            iface_index, address_index;

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
            &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 */
    status = nxd_ipv6_enable(&bsd_ip);
    if((status != NX_SUCCESS) && (status != NX_ALREADY_ENABLED))
    {
        printf("Error with IPv6 enable 0x%x\n", status);
        return;
    }

    /* Enable ICMPv6 */
    status = nxd_icmp_enable(&bsd_ip);

    if(status)
    {
        printf("Error with ECMPv6 enable 0x%x\n", status);
        return;
    }

    /* Set the primary interface for our DNS IPv6 addresses. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, NX_NULL, 10,
                                &address_index);

    if (status)
        return;

    /* Set ip_0 interface address. */
    ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    ip_address.nxd_ip_address.v6[0] = htonl(0x20010db8);
    ip_address.nxd_ip_address.v6[1] = htonl(0x0000f101);
    ip_address.nxd_ip_address.v6[2] = 0;
    ip_address.nxd_ip_address.v6[3] = htonl(0x101);

    /* Set the host global IP address. We are assuming a 64
    bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, &ip_address, 64,
                                &address_index);

    if (status)
        return;

    /* Wait for IPv6 stack to finish DAD process. */
    tx_thread_sleep(400);

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET6, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("\nError: BSD TCP Server socket create \n");
        return;
    }

    printf("\nBSD TCP Server socket created %lu \n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    serverAddr.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    serverAddr.sin6_addr._S6_un._S6_u32[2] = 0x0;
    serverAddr.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    serverAddr.sin6_port = htons(SERVER_PORT);
    serverAddr.sin6_family = AF_INET6;

    /* Bind this server socket */
    status = bind(sock_tcp_server, (struct sockaddr *) &serverAddr,
                    sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error: Server Socket Bind \n");
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen(sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error: Server Socket Listen\n");
        return;
    }
    else
        printf("Server Listen complete\n");

    /* All set to accept client connections */
    printf("Now accepting client connections\n");

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ( (status == 0xFFFFFFFF) || (status == 0) )
        {
            printf("Error with select? Status 0x%x. Try again\n", status);

            continue;
        }

        /* Detected a connection request. */
        is_set = FD_ISSET(sock_tcp_server,&read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,
            (struct sockaddr*)&ClientAddr,
            &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {
                printf("New connection %d\n", sock);

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i, &master_list)) &&
                (FD_ISSET(i, &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server socket %d received no data from
                                Client)\n", i);

                        break;
                    }
                    else if (status == 0xFFFFFFFF)
                    {
                        printf("Error on Server socket %d receiving data from
                                Client\n", i);

                        break;
                    }

                    printf("Server socket %d received from Client %lu bytes:
                            %s\n ", i, (ULONG)status,
                            Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                                Client \n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                                Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != ERROR)
                {
                    printf("Server socket %d closing\n", i);
                }
                else
                {

                    printf("Error on Server socket %d closing\n", i);
                }
            }
        }

        /* Loop back to check any next client connection */
    }
}

#define     CLIENT_BUFFER_SIZE 100
CHAR        Client_Rcv_Buffer[CLIENT_BUFFER_SIZE];

VOID        thread_client_entry(ULONG thread_input)
{

INT         status;
INT         sock_tcp_client, length;
struct      sockaddr_in6 echoServAddr6;
struct      sockaddr_in6 localAddr6; address */

    /* Wait for the server side to get set up, including the DAD process. */
    tx_thread_sleep(500);

    /* ICMPv6 and IPv6 should already be enabled on the IP instance
    by the server thread entry function. */

    /* Further the IPv6 address is already established with the IP instance.
    so no need to wait for DAD completion. */

    /* Set local port and IP address (used only for getsockname call). */
    memset(&localAddr6, 0, sizeof(localAddr6));
    localAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    localAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    localAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    localAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    localAddr6.sin6_port = htons(CLIENT_PORT);
    localAddr6.sin6_family = AF_INET6;

    /* Set Server port and IP address to connect to the TCP server. */
    memset(&echoServAddr6, 0, sizeof(echoServAddr6));
    echoServAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    echoServAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    echoServAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    echoServAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    echoServAddr6.sin6_port = htons(SERVER_PORT);
    echoServAddr6.sin6_family = AF_INET6;

    /* Now make client connections with the server. */
    while (1)
    {
        printf("\n");

        /* Create BSD TCP Socket */

        sock_tcp_client = socket(AF_INET6, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n");
            return;
        }

        printf("Client socket %d created \n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr6,
                sizeof(echoServAddr6));

        /* Check for error. */
        if (status != NX_SOC_OK)
        {
            printf("Error on Client socket %d connect\n");
            soc_close(sock_tcp_client);
            return;

        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr6,
        &length);

        printf("Client port = %lu , Client = 0x%x 0x%x 0x%x 0x%x,",
                ntohs(localAddr6.sin6_port),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[3]));

        length = sizeof(struct sockaddr_in6);

        status = getpeername(sock_tcp_client, (struct sockaddr *)
                            &echoServAddr6, &length);

        printf("Remote port = %lu, Remote IP = 0x%x 0x%x 0x%x 0x%x \n",
                ntohs(echoServAddr6.sin6_port),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[3]));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
                sock_tcp_client);

            status = send(sock_tcp_client, "Hello", sizeof("Hello"), 0);

            if (status == NX_SOC_ERROR)
            {
                printf("Error on Client Socket (%d) send \n",
                        sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message: Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,
                        CLIENT_BUFFER_SIZE, 0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Client received no data on socket %d\n",
                            sock_tcp_client);
                }

            break;
            }
            else
            {
                printf("Client socket %d received %d bytes and this message:
                        %s\n", sock_tcp_client, status,
                        Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = oc_close(sock_tcp_client);

        if (status != NX_SOC_ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```
