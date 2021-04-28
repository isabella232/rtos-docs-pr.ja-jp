---
title: 第 2 章 - Azure RTOS NetX BSD のインストールと使用
description: この章では、Azure RTOS NetX BSD コンポーネントのインストール、設定、使用に関連したさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7539565ccd4956c5354be45000efab8318dc606c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811660"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-bsd"></a>第 2 章 - Azure RTOS NetX BSD のインストールと使用

この章では、Azure RTOS NetX BSD コンポーネントのインストール、設定、使用に関連したさまざまな問題について説明します。

## <a name="product-distribution"></a>製品の配布

Azure RTOS NetX BSD は、[https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) のパブリック ソース コード リポジトリから入手できます。 このパッケージには、次のように 2 つのソース ファイルと、このドキュメントを含む PDF ファイルが含まれています。

- **nx_bsd.h**: NetX BSD のヘッダー ファイル
- **nx_bsd.c**: NetX BSD の C ソース ファイル
- **nx_bsd.pdf**: NetX BSD のユーザー ガイド

デモ ファイル:
- **bsd_demo_tcp.c**
- **bsd_demo_udp.c**

## <a name="netx-bsd-installation"></a>NetX BSD のインストール

NetX BSD を使用するには、先に説明したディストリビューション全体を NetX がインストールされているのと同じディレクトリにコピーする必要があります。 たとえば、NetX がディレクトリ " *\threadx\arm7\green*" にインストールされている場合は、*nx_bsd.h* および *nx_bsd.c* ファイルをこのディレクトリにコピーする必要があります。

## <a name="building-the-threadx-and-netx-components-of-a-bsd-application"></a>BSD アプリケーションの ThreadX および NetX コンポーネントの構築

### <a name="threadx"></a>ThreadX

ThreadX ライブラリでは、スレッド ローカル ストレージ内に *bsd_errno* を定義する必要があります。 次の手順をお勧めします。

1. *tx_port.h* で、次のようにいずれかの TX_THREAD_EXTENSION マクロを設定します。

  ```c
  #define TX_THREAD_EXTENSION_3     int bsd_errno
  ```

2. ThreadX ライブラリをリビルドします。

> [!NOTE]
> TX_THREAD_EXTENSION_3 が既に使用されている場合、ユーザーは、他の TX_THREAD_EXTENSION マクロのいずれかを自由に使用できます。

### <a name="netx"></a>NetX

NetX BSD サービスを使用する前に、NetX ライブラリを NX_ENABLE_EXTENDED_NOTIFY_SUPPORT が (たとえば、*nx_user.h* 内に) 定義された状態で構築する必要があります。 これは、既定では定義されていません。

## <a name="using-netx-bsd"></a>NetX BSD の使用

NetX 用の BSD の使用は簡単です。 基本的に、ThreadX と NetX を使用するには、アプリケーション コードに、それぞれ *tx_api.h* と *nx_api.h* をインクルードした後に *nx_bsd.h* をインクルードする必要があります。 *nx_bsd.h* がインクルードされると、アプリケーション コードは、このガイドの後の方で指定されている BSD サービスを使用できるようになります。 アプリケーションのビルド プロセスでは *nx_bsd.c* も含める必要があります。 このファイルは、他のアプリケーション ファイルと同様にコンパイルする必要があり、そのオブジェクト形式は、アプリケーションのファイルと一緒にリンクする必要があります。 NetX BSD を使用するために必要なことはこれだけです。

NetX BSD サービスを利用するには、アプリケーションで IP インスタンスとパケット プールを作成し、*bsd_initialize* を呼び出して BSD サービスを初期化する必要があります。 これは、このガイドの後の方の "小さな例" のセクションで示されています。 このプロトタイプを次に示します。

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                  CHAR *free_memory_ptr, ULONG bsd_thread_stack_size,
                  UINT bsd_thread_priority);
```

最後の 3 つのパラメーターは、定期的なタスク (TCP イベントのチェックなど) を実行するためのスレッドを作成するために使用され、スレッド スタック領域を定義します。

> [!NOTE]
> ネットワークのバイト順で動作する BSD ソケットとは対照的に、NetX は、ホスト プロセッサのホストのバイト順で動作します。 ソースの互換性の理由から、マクロ htons()、ntohs()、htonl()、ntohl() は定義されていますが、渡された引数を変更することはありません。

## <a name="netx-bsd-limitations"></a>NetX BSD の制限事項

パフォーマンスやアーキテクチャの問題のために、NetX BSD では、BSD 4.3 ソケット機能のすべてはサポートされていません。

INT フラグは、*send、recv、sendto*、*recvfrom* の呼び出しではサポートされていません。

## <a name="netx-bsd-with-dns-support"></a>NetX BSD での DNS サポート

NX_BSD_ENABLE_DNS が定義されている場合、NetX BSD では、ホスト名またはホスト IP の情報を取得するために DNS クエリを送信できます。 この機能では、*nx_dns_create* サービスを使用して、NetX DNS クライアントを事前に作成しておく必要があります。 1 つ以上の既知の DNS サーバー IP アドレスが、サーバー アドレスを追加するための *nx_dns_server_add* を使用して DNS インスタンスに登録されている必要があります。

DNS のサービスとメモリ割り当ては、*getaddrinfo* および *getnameinfo* サービスによって使用されます。

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
              const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
              char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

BSD アプリケーションがホスト名を使用して *getaddrinfo* を呼び出すと、NetX BSD では、以下のいずれかのサービスを呼び出して IP アドレスを取得します。

- nx_dns_ipv4_address_by_name_get
- nx_dns_cname_get

*nx_dns_ipv4_address_by_name_get* の場合、NetX BSD では ipv4_addr_buffer メモリ領域を使用します。 これらのバッファーのサイズは (`NX_BSD_IPV4_ADDR_PER_HOST * 4`) によって定義されます。

*getaddrinfo* からのアドレス情報を返すために、NetX BSD では、ThreadX ブロック メモリ テーブル *nx_bsd_addrinfo_pool_memory* を使用します。このメモリ領域は、構成可能なオプションの別のセットである *NX_BSD_IPV4_ADDR_MAX_NUM* によって定義されます。

上記の構成オプションの詳細については、「**構成オプション**」を参照してください。

さらに、NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されており、ホスト入力が正規名である場合、NetX BSD では、以前に作成されたブロック プール *_nx_bsd_cname_block_pool* からメモリを動的に割り当てます。

> [!NOTE]
> *getaddrinfo* の呼び出し後、*freeaddrinfo* サービスを使用して、res 引数によって指し示されたメモリを解放してブロック テーブルに戻す処理は、BSD アプリケーションで行う必要があります。

## <a name="configuration-options"></a>構成オプション

*nx_bsd.h* 内のユーザーが構成可能なオプションを使用すると、アプリケーションでは、その特定の要件に合わせて NetX BSD ソケットを微調整できます。 これらのパラメーターの一覧を次に示します。

- **NX_BSD_TCP_WINDOW**: TCP ソケットの作成呼び出しで使用されます。 65535 が 100Mb イーサネットでの標準的なウィンドウ サイズです。 既定値は、65535 です。
- **NX_BSD_SOCKFD_START** これは、BSD ソケットのファイル記述子の開始値に対する論理インデックスです。 既定では、このオプションは 32 です。
- **NX_BSD_MAX_SOCKETS** BSD レイヤーで使用可能な合計ソケットの最大数を指定するものであり、32 の倍数である必要があります。この値は、既定で 32 に設定されています。
- **NX_BSD_SOCKET_QUEUE_MAX** 受信ソケット キューに格納される UDP パケットの最大数を指定します。 この値は、既定で 5 に設定されています。
- **NX_BSD_MAX_LISTEN_BACKLOG** これは、BSD TCP ソケットのリッスン キュー ('バックログ') のサイズを指定します。 既定値は 5 です。
- **NX_MICROSECOND_PER_CPU_TICK** タイマー割り込みあたりのマイクロ秒数を指定します。
- **NX_BSD_TIMEOUT** BSD に必要な NetX の内部呼び出しでのタイマー刻み単位のタイムアウトを指定します。 既定値は 20*NX_IP_PERIODIC_RATE です。
- **NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: NetX の切断呼び出しでのタイマー刻み単位のタイムアウトを指定します。 既定値は 1 です。
- **NX_BSD_PRINT_ERRORS** 設定されている場合は、BSD 関数のエラー状態の戻り値によって、エラーが発生した行番号とエラーの種類 (NX_SOC_ERROR など) が返されます。 このためアプリケーション開発者は、デバッグ出力を定義する必要があります。 既定の設定は無効であり、*nx_bsd.h* でデバッグ出力は指定されていません。
- **NX_BSD_TIMER_RATE** BSD の定期的なタイマー タスクが実行されるまでの間隔。 既定値は 1 秒 (1 * NX_IP_PERIODIC_RATE) です。
- **NX_BSD_TIMEOUT_PROCESS_IN_TIMER** 設定されている場合は、このオプションにより、BSD タイムアウト プロセスをシステム タイマー コンテキストで実行できます。 既定の動作は無効です。 この機能は、第 2 章「NetX BSD のインストールと使用」でより詳細に説明されています。
- **NX_BSD_ENABLE_DNS** 有効になっている場合、NetX BSD では、ホスト名またはホスト IP アドレスを取得するために DNS クエリを送信します。 DNS クライアント インスタンスが事前に作成され、起動されている必要があります。 既定では、有効になっていません。
- **NX_BSD_IPV4_ADDR_MAX_NUM** *getaddrinfo* によって返される IPv4 アドレスの最大数。 *getaddrinfo* でのアドレス情報の格納にメモリを動的に割り当てるため、これを NX_BSD_IPV4_ADDR_MAX_NUM と一緒に使用して、NetX BSD ブロック プール nx_bsd_addrinfo_block_pool のサイズを定義します。 既定値は 5 です。
- **NX_BSD_IPV4_ADDR_PER_HOST**: DNS クエリごとに格納される IPv4 アドレスの最大数を定義します。 既定値は 5 です。

## <a name="bsd-socket-options"></a>BSD ソケット オプション

*setsockopt* サービスを使用して、次の NetX BSD ソケット オプションの一覧を実行時にソケットごとに有効 (または無効) にすることができます。

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, const
                void *option_value, INT option_length);
```

*option_level* には、2 つの異なる設定があります。

実行時のソケット オプションの最初の種類は、ソケット レベルのオプションのための SOL_SOCKET です。 ソケット レベルのオプションを有効にするには、option_level を SOL_SOCKET に設定し、option_name を SO_BROADCAST などの特定のオプションに設定して *setsockopt* を呼び出します。 オプション設定を取得するには、option_level を再び SOL_SOCKET に設定して option_name に対する *getsockopt* を呼び出します。

以下に、実行時のソケット レベルのオプションの一覧を示します。

- **SO_BROADCAST**: 設定されている場合は、これにより、Netx ソケットのブロードキャスト パケットの送受信が可能になります。 これは NetX の既定の動作です。 すべてのソケットがこの機能を備えています。
- **SO_ERROR**: *getsockopt* サービスを使用した、指定されたソケットの以前のソケット操作に関するソケット状態を取得するために使用されます。 すべてのソケットがこの機能を備えています。
- **SO_KEEPALIVE**: 設定されている場合は、これにより、TCP キープ アライブ機能が可能になります。 このためには、*nx_user.h* で NX_TCP_ENABLE_KEEPALIVE を定義して NetX ライブラリを構築する必要があります。 既定では、この機能は無効になります。
- **SO_RCVTIMEO**: NetX BSD ソケットでパケットを受信するための待機オプションを秒単位で設定します。 既定値は NX_WAIT_FOREVER (0xFFFFFFFF) です。または、非ブロッキングが有効になっている場合は NX_NO_WAIT (0x0) です。
- **SO_RCVBUF**: TCP ソケットのウィンドウ サイズを設定します。 既定値の NX_BSD_TCP_WINDOW は、BSD TCP ソケットでは 64k に設定されます。 65535 を超えるサイズを設定するには、NX_TCP_ENABLE_WINDOW_SCALING を定義して NetX ライブラリを構築する必要があります。
- **SO_REUSEADDR**: 設定されている場合は、これにより、1 つのポートに複数のソケットをマップできます。 典型的な使い方は TCP サーバー ソケット用です。 これは NetX ソケットの既定の動作です。

実行時のソケット オプションの 2 番目の種類は、IP オプションのレベルです。 IP レベルのオプションを有効にするには、option_level を IP_PROTO に設定し、option_name を IP_MULTICAST_TTL などのオプションに設定して *setsockopt* を呼び出します。 オプション設定を取得するには、option_level を再び IP_PROTO に設定して option_name に対する *getsockopt* を呼び出します。

以下に、実行時の IP レベルのオプションの一覧を示します。

- **IP_MULTICAST_TTL**: UDP ソケットの有効期限を設定します。 ソケットが作成されるときの既定値は NX_IP_TIME_TO_LIVE (0x80) です。 この値は、このソケット オプションで *setsockopt* を呼び出してオーバーライドできます。
- **IP_ADD_MEMBERSHIP**: 設定されている場合は、このオプションにより、BSD ソケット (UDP ソケットにのみ適用されます) は指定された IGMP グループに参加できます。
- **IP_DROP_MEMBERSHIP**: 設定されている場合は、このオプションにより、BSD ソケット (UDP ソケットにのみ適用されます) は指定された IGMP グループから離れることができます。

## <a name="small-example-system"></a>小規模システムの例

NetX BSD を使用する方法の例を以下の図 1.0 に示します。 この例では、インクルード ファイル *nx_bsd.h* が 7 行目で組み込まれています。 次に、IP インスタンス *bsd_ip* とパケット プール *bsd_pool* が、20 行目と 21 行目でグローバル変数として作成されています。 このデモでは RAM (仮想) ネットワーク ドライバーを使用していることに注意してください (41 行目)。 この例では、クライアントとサーバーが 1 つの IP インスタンス上で同じ IP アドレスを共有します。

クライアント スレッドとサーバー スレッドは、アプリケーションを設定し、293-361 行目で定義されている *tx_application_define* 内の 303 行目と 309 行目で作成されます。 IP インスタンスが 327 行目で正常に作成された後、その IP インスタンスは 350 行目で TCP サービスに対して有効になります。 BSD サービスを使用できるようにする前の最後の要件は、360 行目で *bsd_initialize* を呼び出して、すべてのデータ構造体と NetX のほか、BSD で必要な ThreadX リソースを設定することです。

381-397 行目で定義されているサーバー スレッドのエントリ関数 *thread_1_entry* では、アプリケーションは、ドライバーがネットワーク パラメーターで NetX を初期化するまで待ちます。 これが完了すると、この関数は 146-253 行目で定義されている *tcpServer* を呼び出して、TCP サーバー ソケットの設定の詳細を処理します。

*tcpServer* では、159 行目で *socket* サービスを呼び出してマスター ソケットを作成した後、176 行目で *bind* 呼び出しを使用してそれをリスニング ソケットにバインドします。 これはその後、191 行目で接続要求をリッスンするように構成されます。 マスター ソケットが接続要求を受け付けないことに注意してください。 これは、接続要求を検出するために、毎回 *select* を呼び出す連続したループで実行されます。 218 行目で *accept* サービスを呼び出した後、BSD ソケットの配列から選択されたセカンダリ BSD ソケットに接続要求が割り当てられます。

クライアント側では、366-377 行目で定義されているクライアント スレッドのエントリ関数 *thread_0_entry* でも、NetX がドライバーによって初期化されるまで待つ必要があります。 ここでは、単にサーバー側でそれが行われるまで待ちます。 これは次に、54-142 行目で定義されている *tcpClient* を呼び出して、TCP クライアント ソケットの設定と TCP 接続の要求の詳細を処理します。

TCP クライアント ソケットは 68 行目で作成されます。 このソケットは、指定された IP アドレスにバインドされ、84 行目で *connect* を呼び出して TCP サーバーに接続しようとします。 これで、パケットの送受信を開始する準備ができました。

```c
1 /*  This is a small demo of BSD Wrapper for the high-performance NetX TCP/IP stack.
2     This demo demonstrate TCP connection, disconnection, sending, and receiving using
3     ARP and a simulated Ethernet driver. */
4
5 #include     "tx_api.h"
6 #include     "nx_api.h"
7 #include     "nx_bsd.h"
8 #include     <string.h>
9 #include     <stdlib.h>
10
11 #define         DEMO_STACK_SIZE         (16*1024)
12
13
14 /* Define the ThreadX and NetX object control blocks... */
15
16 TX_THREAD       thread_0;
17 TX_THREAD       thread_1;
18
19
20 NX_PACKET_POOL  bsd_pool;
21 NX_IP           bsd_ip;
22
23
24 /* Define the counters used in the demo application... */
25
26 ULONG           error_counter;
27
28 /* Define fd_set for select call */
29 fd_set          master_list,read_ready,read_ready1;
30
31
32 /* Define thread prototypes. */
33
34 VOID            thread_0_entry(ULONG thread_input);
35 VOID            thread_1_entry(ULONG thread_input);
36
37 VOID            tcpClient(CHAR *msg0);
38 VOID            tcpServer(VOID);
39 INT             HandleClient(INT sock);
40
41 VOID            _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
42
43
44 /* Define main entry point. */
45
46 int main()
47 {
48
49     /* Enter the ThreadX kernel. */
50     tx_kernel_enter();
51 }
52
53
54 VOID tcpClient(CHAR *msg0)
55 {
56
57 INT     status,status1,send_counter;
58 INT     sock_tcp_1,length,length1;
59 struct  sockaddr_in echoServAddr;       /* Echo server address */
60 struct  sockaddr_in localAddr;          /* Local address */
61 struct  sockaddr_in remoteAddr;         /* Remote address */
62
63 UINT    echoServPort; /* Echo Server Port */
64 CHAR    rcvBuffer1[32]
65
66
67     /* Create BSD TCP Socket */
68     sock_tcp_1 = **socket**( PF_INET, SOCK_STREAM, IPPROTO_TCP);
69     if (sock_tcp_1 == -1)
70     {
71         printf("\nError: BSD TCP Client socket create \n");
72         return;
73     }
74
75     printf("\nBSD TCP Client socket created %lu \n", sock_tcp_1);
76     /* Fill destination port and IP address */
77     echoServPort = 12;
78     memset(&echoServAddr, 0, sizeof(echoServAddr));
79     echoServAddr.sin_family = PF_INET;
80     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
81     echoServAddr.sin_port = echoServPort;
82
83     /* Now connect this client the server */
84     status1 = connect(sock_tcp_1, (struct sockaddr *)&echoServAddr, sizeof(echoServAddr));
85     /* Check for error. */
86     if (status1 != OK)
87     {
88         printf("\nError: BSD TCP Client socket Connect, %d \n",sock_tcp_1);
89         status = soc_close(sock_tcp_1);
90         if (status != ERROR)
91             printf("\nConnect ERROR so BSD Client Socket Closed: %d\n",sock_tcp_1);
92         else
93             printf("\nError: BSD Client Socket close %d\n",sock_tcp_1);
94         return;
95     }
96     /* Get and print source and destination information */
97     printf("\nBSD TCP Client socket: %d connected \n", sock_tcp_1);
98
99     status = getsockname(sock_tcp_1, (struct sockaddr *)&localAddr, &length);
100    printf("Client port = %lu , Client = %lu,", 
            localAddr.sin_port, localAddr.sin_addr.s_addr);
101    status = getpeername( sock_tcp_1, (struct sockaddr *) &remoteAddr, &length1);
102    printf("Remote port = %lu, Remote IP = %lu \n", 
            remoteAddr.sin_port remoteAddr.sin_addr.s_addr);
103
104    send_counter = 1;
105
106    /* Now receive the echoed packet from the server */
107    while(1)
108    {
109        tx_thread_sleep(2);
110
111        printf("\nClient sock: %d Sending packet No: %d to
                server\n",sock_tcp_1,send_counter);
112        status = send(sock_tcp_1,msg0, sizeof(msg0), 0);
113        if (status == ERROR)
114            printf("Error: BSD Client Socket send %d\n",sock_tcp_1);
115        else
116        {
117            printf("\nMessage sent: %s\n",msg0);
118            send_counter++;
119        }
120
121        status = recv(sock_tcp_1, (VOID *)rcvBuffer1, 31,0);
122        if (status == 0)
123            break;
124
125        rcvBuffer1[status] = 0;
126
127        if (status != ERROR)
128            printf("\nBSD Client Socket: %d received %lu bytes: %s ", 
                        sock_tcp_1,(ULONG)status,rcvBuffer1);
129        else
130            printf("\nError: BSD Client Socket receive %d \n",sock_tcp_1);
131
132    }
133
134    /* close this client socket */
135    status = soc_close(sock_tcp_1);
136    if (status != ERROR)
137        printf("\nBSD Client Socket Closed %d\n",sock_tcp_1);
138    else
139        printf("\nError: BSD Client Socket close %d \n",sock_tcp_1);
140
141    /* End */
142 }
143
144
145
146 void tcpServer(void)
147 {
148
149 INT         status,status1,sock,sock_tcp_2,i;
150 struct      sockaddr_in echoServAddr; /* Echo server address */
151 struct      sockaddr_in ClientAddr;
152
153 INT         Clientlen;
154 UINT        echoServPort; /* Echo Server Port */
155
156 INT         maxfd;
157
158 /* Create BSD TCP Server Socket */
159     sock_tcp_2 = socket( PF_INET, SOCK_STREAM, IPPROTO_TCP);
160     if (sock_tcp_2 == -1)
161     {
162         printf("Error: BSD TCP Server socket create\n");
163         return;
164     }
165     else
166         printf("BSD TCP Server socket created \n");
167
168     /* Now fill server side information */
169     echoServPort = 12;
170     memset(&echoServAddr, 0, sizeof(echoServAddr));
171     echoServAddr.sin_family = PF_INET;
172     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
173     echoServAddr.sin_port = echoServPort;
174
175     /* Bind this server socket */
176         status = bind(sock_tcp_2, (struct sockaddr *) &echoServAddr, sizeof(echoServAddr));
177     if (status < 0)
178     {
179         printf("Error: BSD TCP Server Socket Bind \n");
180         return;
181     }
182     else
183         printf("BSD TCP Server Socket bound \n");
184
185     FD_ZERO(&master_list);
186     FD_ZERO(&read_ready);
187     FD_SET(sock_tcp_2,&master_list);
188     maxfd = sock_tcp_2;
189
190     /* Now listen for any client connections for this server socket */
191     status = listen(sock_tcp_2,5);
192     if (status < 0)
193     {
194         printf("Error: BSD TCP Server Socket Listen\n");
195         return;
196     }
197     else
198         printf("BSD TCP Server Socket Listen complete, ");
199
200     /* All set to accept client connections */
201     printf("Now accepting client connections\n");
202
203     /* Loop to create and establish server connections. */
204     while(1)
205     {
206
207         read_ready = master_list;
208         tx_thread_sleep(2); /* Allow some time to other threads too */
209         status = select(maxfd+1,&read_ready,0,0,0);
210         if (status == ERROR)
211         {
212             continue;
213         }
214
215         status = FD_ISSET(sock_tcp_2,&read_ready);
216         if(status)
217         {
218             sock = accept(sock_tcp_2,(struct sockaddr*)&ClientAddr, &Clientlen);
219
220             /* Add this new connection to our master list */
221             FD_SET(sock,&master_list);
222             if ( sock \maxfd)
223             {
224                 maxfd = sock;
225             }
226
227             continue;
228         }
229         for (i = 0; i < (maxfd+1); i++)
230         {
231             if (( i != sock_tcp_2) && (FD_ISSET(i,&master_list)) && 
                    (FD_ISSET(i,&read_ready)))
232             {
233                 status1 = HandleClient(i);
234                 if (status1 == 0)
235                 {
236                     status1 = soc_close(i);
237                     if (status1 == OK)
238                     {
239                         FD_CLR(i,&master_list);
240                         printf("\nBSD Server Socket:%d closed\n",i);
241                     }
242                     else
243                         printf("\nError:BSD Server Socket:%d close\n",i);
244                 }
245
246             }
247         }
248
249         /* Loop back to check any next client connection */
250
251     } /* While(1) ends */
252
253 }
254
255 CHAR     rcvBuffer[128];
256
257 INT     HandleClient(INT sock)
258 {
259
260 INT     status;
261
262
263     status = recv(sock, (VOID *)rcvBuffer, 128,0);
264     if (status == ERROR )
265     {
266         printf("\n BSD Server Socket:%d receive \n",sock);
267         return(ERROR);
268     }
269
270     /* a zero return from a recv() call indicates client is terminated! */
271     if (status == 0)
272     {
273         /* Done with this client , close this secondary server socket */
274         return(status);
275     }
276
277     /* print data received from the client */
278     printf("\nBSD Server Socket:%d received %lu bytes: %s \n", sock, (ULONG)status,rcvBuffer);
279
280     /* And echo the same data to the client */
281     status = send(sock,rcvBuffer, status + 1, 0);
282     if (status == ERROR )
283     {
284         printf("\nError: BSD Server Socket:%d send \n",sock);
285         return(ERROR);
286     }
287     return(status);
288 }
289
290
291 /* Define what the initial system looks like. */
292
293 void     tx_application_define(void *first_unused_memory)
294 {
295
296 CHAR     *pointer;
297 UINT     status;
298
299     /* Setup the working pointer. */
300     pointer = (CHAR *) first_unused_memory;
301
302     /* Create a client thread. */
303     tx_thread_create(&thread_0, "Client1", thread_0_entry, 0,
304         pointer, DEMO_STACK_SIZE, 2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
305
306     pointer = pointer + DEMO_STACK_SIZE;
307
308     /* Create a server thread. */
309     tx_thread_create(&thread_1, "Server", thread_1_entry, 0,
310         pointer, DEMO_STACK_SIZE,1,1, TX_NO_TIME_SLICE, TX_AUTO_START);
311
312     pointer = pointer + DEMO_STACK_SIZE;
313
314     /* Initialize the NetX system. */
315     nx_system_initialize();
316
317     /* Create a BSD packet pool. */
318     status = nx_packet_pool_create(&bsd_pool,"NetX BSD Packet Pool", 128
                                        pointer, 16384);
319     pointer = pointer + 16384;
320     if (status)
321     {
322         error_counter++;
323         printf("Error in creating BSD packet pool\n!");
324     }
325
326     /* Create an IP instance for BSD. */
327     status = nx_ip_create(&bsd_ip, "NetX IP Instance 2", IP_ADDRESS(1, 2, 3, 4),
                              0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                              pointer, 2048, 1);
328
329     pointer = pointer + 2048;
330
331     if (status)
332     {
333         error_counter++;
334         printf("Error creating BSD IP instance\n!");
335     }
336
337     /* Enable ARP and supply ARP cache memory for BSD IP Instance */
338     status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
339     pointer = pointer + 1024;
340
341     /* Check ARP enable status. */
342     if (status)
343     {
344         error_counter++;
345         printf("Error in Enable ARP and supply ARP cache memory to BSD IP instance\n");
346     }
347
348     /* Enable TCP processing for BSD IP instances. */
349
350     status = nx_tcp_enable(&bsd_ip);
351
352     /* Check TCP enable status. */
353     if (status)
354     {
355         error_counter++;
356         printf("Error in Enable TCP \n");
357     }
358
359     /* Now initialize BSD Scoket Wrapper */
360     status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 1);
361 }
362
363
364 /* Define the test threads. */
365
366 void     thread_0_entry)ULONG thread_input)
367 {
368
369 CHAR     *msg0 = "Client 1:
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<> \
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";
370
371     /* Wait till Server side is all set */
372     tx_thread_sleep(2);
373     while (1)
374     {
375         tcpClient(msg0);
376         tx_thread_sleep(1);
377     }
378 }
379
380 /* Define the server thread entry function. */
381 void     thread_1_entry(ULONG thread_input)
382 {
383
384 UINT     status;
385 ULONG    actual_status;
386
387 /* Ensure the IP instance has been initialized. */
388 status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE, &actual_status, 100);
389
390 /* Check status... */
391 if (status != NX_SUCCESS)
392 {
393     error_counter++;
394     return;
395 }
396 /* Start a TCP Server */
397 tcpServer();
398 }
399
```
