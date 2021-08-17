---
title: 第 2 章 - Azure RTOS NetX Duo HTTP のインストールと使用
description: この章では、Azure RTOS NetX Duo HTTP コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8739603d4a387ff3f3f42c979bd00fcebe4f08efaab42ecade462adf1fb4906a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783494"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-http"></a>第 2 章 - Azure RTOS NetX Duo HTTP のインストールと使用

この章では、Azure RTOS NetX Duo HTTP コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品ディストリビューション

Azure RTOS NetX Duo は、[https://github.com/azure-rtos/netxduo/](https://github.com/azure-rtos/netxduo/) のパブリック ソース コード リポジトリから入手できます。

 - **nxd_http_client.h**: NetX Duo 用 HTTP クライアントのヘッダー ファイル
 - **nxd_http_server.h**: NetX Duo 用 HTTP サーバーのヘッダー ファイル
 - **nxd_http_client.c**: NetX Duo 用 HTTP クライアントの C ソース ファイル
 - **nxd_http_server.c**: NetX Duo 用 HTTP サーバーの C ソース ファイル
 - **nx_md5.c**: MD5 ダイジェスト アルゴリズム
 - **filex_stub.h**: FileX が存在しない場合のスタブ ファイル
 - **nxd_http.pdf**: NetX Duo 用 HTTP の説明
 - **demo_netxduo_http.c**: NetX Duo HTTP のデモンストレーション

## <a name="http-installation"></a>HTTP のインストール

NetX Duo 用 HTTP を使用するには、前述のディストリビューション全体を、NetX Duo がインストールされているのと同じディレクトリにコピーする必要があります。 たとえば、NetX Duo が " *\threadx\arm7\green*" ディレクトリにインストールされている場合は、NetX Duo HTTP クライアント アプリケーションの *nxd_http_client.h* と *nxd_http_client.c*、NetX Duo HTTP サーバー アプリケーションの *nxd_http_server.h* と *nxd_http_server.c*、および *nx_md5.c* をこのディレクトリにコピーする必要があります。 *nx_md5.c* をこのディレクトリにコピーする必要があります。 デモの "ram driver" アプリケーションの場合、NetX Duo HTTP クライアントとサーバーのファイルを同じディレクトリにコピーする必要があります。

## <a name="using-http"></a>HTTP の使用

NetX Duo 用 HTTP は簡単に使用できます。 基本的には、ThreadX、FileX、NetX Duo を使用するために、アプリケーション コードにそれぞれ *tx_api.h*、*fx_api.h*、*nx_api.h* をインクルードした後に、*nxd_http_client.h* または *nxd_http_server.h*、あるいはその両方をインクルードする必要があります。 HTTP ヘッダー ファイルをインクルードすると、アプリケーション コードで、このガイドで後述する HTTP 関数呼び出しを行えるようになります。 アプリケーションでは、ビルド プロセスで *nxd_http_client.c*、*nxd_http_server.c*、*md5.c* もインクルードする必要があります。 これらのファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、そのオブジェクト フォームをアプリケーションのファイルと一緒にリンクする必要があります。 NetX Duo HTTP を使用するために必要なことはこれだけです。

> [!NOTE]
> ビルド プロセスで NX_HTTP_DIGEST_ENABLE が指定されていない場合は、アプリケーションに md5.c ファイルを追加する必要はありません。 同様に、HTTP クライアント機能が不要な場合は、*nxd_http_client.c* ファイルを省略できます。

> [!NOTE]
> HTTP では NetX Duo TCP サービスを利用するため、HTTP を使用する前に、*nx_tcp_enable* を呼び出して TCP を有効にする必要があります。

## <a name="small-example-system"></a>簡単なシステムの例

NetX Duo HTTP の使用がいかに簡単であるかを示す例を、下の図 1.1 に示します。 この例では、23 行目に #define USE_DUO を配置して、NetX Duo HTTP で使用できる "duo" サービスを使用します。 それ以外の場合は、従来の NetX HTTP の同等のサービス (IPv4 のみに限定) を使用します。 開発者は、NetX Duo HTTP サービスを使用するように既存のアプリケーションを移行することをお勧めします。

IPv6 通信を指定するために、このアプリケーションでは 24 行目で IPTYPE を IPv6 に定義しています。

この例では、HTTP インクルード ファイル *nxd_http_client.h* と *nxd_http_server.h* が 8 行目と 9 行目で取り込まれます。 次に、HTTP サーバーのヘルパー スレッド、パケット プール、IP インスタンスが 89 から 112 行目で作成されます。 137 行目に示すように、HTTP サーバーの IP インスタンスで TCP を有効にする必要があります。 HTTP サーバー自体は 159 行目で作成されます。

次に、HTTP クライアントが作成されます。 まず、172 行目でクライアント スレッドが作成された後、HTTP サーバーと同様に、パケット プールと IP インスタンスが 186 から 200 行目で作成されます。 この場合も、HTTP クライアントの IP インスタンスで TCP を有効にする必要があります (217 行目)。

HTTP サーバー スレッドが実行され、その最初のタスクとして、NetX Duo によって IP アドレスが検証されます (423 から 450 行目)。 これで、HTTP サーバーは要求を受け取る準備ができました。

HTTP クライアント スレッドの最初のタスクは、FileX メディアの作成とフォーマットです (236 および 260 行目)。 メディアが初期化された後、271 行目で HTTP クライアントが作成されます。 HTTP サーバーが HTTP 要求を処理できるようにするには、これを完了しておく必要があります。 その後、NetX Duo を使用して IP アドレスを検証する必要があります (282 から 316 行目)。 HTTP クライアントは、client_test.html ファイルを作成して HTTP サーバーに送信し、しばらく待ってから、HTTP サーバーからのファイルの読み取りを試みます。

> [!NOTE]
> IPv6 が有効になっていない場合は、HTTP クライアント API で別のサービスが使用されます (343 行目の *nx_http_client_put_start* と、399 行目の *nx_http_client_get_start*)。 これにより、NetX Duo で既存の NetX HTTP クライアント アプリケーションをサポートできるようになります。

> [!NOTE]
> HTTP クライアント API 呼び出しは、比較的短いタイムアウトで行われます。 HTTP クライアントが低速のプロセッサでビジー状態のサーバーやリモート サーバーと通信している場合は、これらのタイムアウトを延長することが必要な場合があります。

```c
1    /* This is a small demo of the NetX Duo HTTP Client Server API running on a
2       high-performance NetX Duo TCP/IP stack. This demo is applicable for
3       either IPv4 or IPv6 enabled applications. */
4    
5    #include   "tx_api.h"
6    #include   "fx_api.h"
7    #include   "nx_api.h"
8    #include   "nxd_http_client.h"
9    #include   "nxd_http_server.h"
10   
11   #define     DEMO_STACK_SIZE         2048  
12   
13   /* Set up FileX and file memory resources. */
14   CHAR            *ram_disk_memory;
15   FX_MEDIA        ram_disk;
16   unsigned char   media_memory[512];
17      
18   /* Define device drivers. */
19   extern void _fx_ram_driver(FX_MEDIA *media_ptr);
20   VOID        _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
22   
23   #define USE_DUO        /* Use the duo service (not legacy netx) */
24   #define IPTYPE   6       /* Send packets over IPv6 */
25
26   /* Set up the HTTP client. */
27   TX_THREAD       client_thread;
28   NX_PACKET_POOL  client_pool;
29   NX_HTTP_CLIENT  my_client;
30   NX_IP           client_ip;
31   #define         CLIENT_PACKET_SIZE  (NX_HTTP_SERVER_MIN_PACKET_SIZE * 2)
32   void            thread_client_entry(ULONG thread_input);
33   
34   #define HTTP_SERVER_ADDRESS  IP_ADDRESS(1,2,3,4)
35   #define HTTP_CLIENT_ADDRESS  IP_ADDRESS(1,2,3,5)
36   
37   /* Set up the HTTP server */
38   
39   NX_HTTP_SERVER  my_server;
40   NX_PACKET_POOL  server_pool;
41   TX_THREAD       server_thread;
42   NX_IP           server_ip;
43   #define         SERVER_PACKET_SIZE  (NX_HTTP_SERVER_MIN_PACKET_SIZE * 2)
44   
45   void            thread_server_entry(ULONG thread_input);
46   #ifdef FEATURE_NX_IPV6
47   NXD_ADDRESS     server_ip_address;
48   #endif
49   
50   
51   /* Define the application's authentication check. This is called by
52      the HTTP server whenever a new request is received. */
53   UINT  authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
54               CHAR *resource, CHAR **name, CHAR **password, CHAR **realm)
55   {
56   
57       /* Just use a simple name, password, and realm for all
58          requests and resources. */
59       *name =     "name";
60       *password = "password";
61       *realm =    "NetX Duo HTTP demo";
62   
63       /* Request basic authentication. */
64       return(NX_HTTP_BASIC_AUTHENTICATE);
65   }
66   
67   /* Define main entry point. */
68   
69   int main()
70   {
71   
72       /* Enter the ThreadX kernel. */
73       tx_kernel_enter();
74   }
75   
76   
77   /* Define what the initial system looks like. */
78   void    tx_application_define(void *first_unused_memory)
79   {
80   
81   CHAR    *pointer;
82   UINT    status;
83   
84       
85       /* Setup the working pointer. */
86       pointer =  (CHAR *) first_unused_memory;
87   
88       /* Create a helper thread for the server. */
89       tx_thread_create(&server_thread, "HTTP Server thread", thread_server_entry, 0,  
90                        pointer, DEMO_STACK_SIZE,
91                        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
92   
93       pointer =  pointer + DEMO_STACK_SIZE;
94   
95       /* Initialize the NetX system. */
96       nx_system_initialize();
97   
98       /* Create the server packet pool. */
99       status =  nx_packet_pool_create(&server_pool, "HTTP Server Packet Pool",
        SERVER_PACKET_SIZE, pointer, SERVER_PACKET_SIZE*4);
100
101  
102      pointer = pointer + SERVER_PACKET_SIZE * 4;
103  
104      /* Check for pool creation error. */
105      if (status)
106      {
107  
108          return;
109      }
110  
111      /* Create an IP instance. */
112      status = nx_ip_create(&server_ip, "HTTP Server IP", HTTP_SERVER_ADDRESS,
113                            0xFFFFFF00UL, &server_pool, _nx_ram_network_driver,
114                            pointer, 4096, 1);
115  
116      pointer =  pointer + 4096;
117  
118      /* Check for IP create errors. */
119      if (status)
120      {
121          printf("nx_ip_create failed. Status 0x%x\n", status);
122          return;
123      }
124  
125      /* Enable ARP and supply ARP cache memory for the server IP instance. */
126      status = nx_arp_enable(&server_ip, (void *) pointer, 1024);
127  
128      /* Check for ARP enable errors. */
129      if (status)
130      {
131          return;
132      }
133  
134      pointer = pointer + 1024;
135  
136       /* Enable TCP traffic. */
137      status = nx_tcp_enable(&server_ip);
138  
139      if (status)
140      {
141          return;
142      }
143  
144  #if (IP_TYPE==6)
145  
146      /* Set up HTTPv6 server, but we have to wait till its address has been
147         validated before we can start the thread_server_entry thread. */
148  
149      /* Set up the server's IPv6 address here. */
150      server_ip_address.nxd_ip_address.v6[3] = 0x105;
151      server_ip_address.nxd_ip_address.v6[2] = 0x0;
152      server_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
153      server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
154      server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
155  
156  #endif
157  
158      /* Create the NetX HTTP Server. */
159      status = nx_http_server_create(&my_server, "My HTTP Server", &server_ip,
            &ram_disk, pointer, 2048, &server_pool, authentication_check,
            NX_NULL);
160
161      if (status)
162      {
163          return;
164      }
165  
166      pointer =  pointer + 2048;
167  
168      /* Save the memory pointer for the RAM disk. */
169      ram_disk_memory =  pointer;
170  
171      /* Create the HTTP client thread. */
172      status = tx_thread_create(&client_thread, "HTTP Client", thread_client_entry, 0,  
173                       pointer, DEMO_STACK_SIZE,
174                       2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
175  
176      pointer =  pointer + DEMO_STACK_SIZE;
177  
178      /* Check for thread create error. */
179      if (status)
180      {
181  
182          return;
183      }
184  
185      /* Create the Client packet pool. */
186      status =  nx_packet_pool_create(&client_pool, "HTTP Client Packet Pool",
 SERVER_PACKET_SIZE, pointer, SERVER_PACKET_SIZE*4);

187
188  
189      pointer = pointer + SERVER_PACKET_SIZE * 4;
190  
191      /* Check for pool creation error. */
192      if (status)
193      {
194  
195          return;
196      }
197  
198  
199      /* Create an IP instance. */
200      status = nx_ip_create(&client_ip, "HTTP Client IP", HTTP_CLIENT_ADDRESS,
201                            0xFFFFFF00UL, &client_pool, _nx_ram_network_driver,
202                            pointer, 2048, 1);
203  
204      pointer =  pointer + 2048;
205  
206      /* Check for IP create errors. */
207      if (status)
208      {
209          return;
210      }
211  
212      nx_arp_enable(&client_ip, (void *) pointer, 1024);
213  
214      pointer =  pointer + 2048;
215  
216       /* Enable TCP traffic. */
217      nx_tcp_enable(&client_ip);
218  
219      return;
220  }
221  
222  
223  VOID thread_client_entry(ULONG thread_input)
224  {
225  
226  UINT            status;
227  NX_PACKET       *my_packet;
228  #ifdef FEATURE_NX_IPV6
229  NXD_ADDRESS     client_ip_address;
230  UINT            address_index;
230  #endif
231  
232  
233      /* Format the RAM disk - the memory for the RAM disk was setup in
234        tx_application_define above. This must be set up before the client(s) start
235        sending requests. */
236      status = fx_media_format(&ram_disk,
237                              _fx_ram_driver,         // Driver entry
238                              ram_disk_memory,        // RAM disk memory pointer
239                              media_memory,           // Media buffer pointer
240                              sizeof(media_memory),   // Media buffer size
241                              "MY_RAM_DISK",          // Volume Name
242                              1,                      // Number of FATs
243                              32,                     // Directory Entries
244                              0,                      // Hidden sectors
245                              256,                    // Total sectors
246                              128,                    // Sector size   
247                              1,                      // Sectors per cluster
248                              1,                      // Heads
249                              1);                     // Sectors per track
250  
251      /* Check the media format status. */
252      if (status != FX_SUCCESS)
253      {
254  
255          /* Error, bail out. */
256          return ;
257      }
258  
259      /* Open the RAM disk. */
260      status =  fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory,
                media_memory, sizeof(media_memory));
261  
262      /* Check the media open status. */
263      if (status != FX_SUCCESS)
264      {
265  
266          /* Error, bail out. */
267          return ;
268      }
269  
270      /* Create an HTTP client instance. */
271      status = nx_http_client_create(&my_client, "HTTP Client", &client_ip,
                    &client_pool, 600);
272  
273      /* Check status. */
274      if (status != NX_SUCCESS)
275      {
276          return;
277      }
278  
279      /* Attempt to upload a file to the HTTP server. */
280  
281  
282  #if (IPTYPE== 6)
283  
284      /* Relinquish control so the HTTP server can get set up...*/
285      tx_thread_relinquish();
286  
287      /* Set up the client's IPv6 address here. */
288      client_ip_address.nxd_ip_address.v6[3] = 0x101;
289      client_ip_address.nxd_ip_address.v6[2] = 0x0;
290      client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
291      client_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
292      client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
293                 
294      /* Here's where we make the HTTP Client IPv6 enabled. */
295  
296      nxd_ipv6_enable(&client_ip);
298      nxd_icmp_enable(&client_ip);     
299      
300      /* Wait till the IP task thread has set the device MAC address. */
302      tx_thread_sleep(100);
303  
305      /* Now update NetX Duo the Client's link local and global IPv6 address. */
306      nxd_ipv6_address_set(&server_ip, 0, NX_NULL, 10, &address_index)
307      nxd_ipv6_ address_set(&server_ip, 0, &client_ip_address, 64, &address_index);
311
313      /* Then make sure NetX Duo has had time to validate the addresses. */
314      
316      tx_thread_sleep(400);
317  
321      /* Now upload an HTML file to the HTTPv6 server. */
322      status =  nxd_http_client_put_start(&my_client, &server_ip_address,
323         "/client_test.htm", "name", "password", 103, 500);
324
325
326      /* Check status. */
327      if (status != NX_SUCCESS)
328      {
329
330          return;
331      }
332      
333
334  #else
335  
336      /* Relinquish control so the HTTP server can get set up...*/
337      tx_thread_relinquish();
338  
339      do
340      {
341      
342          /* Attempt to upload to the HTTP IPv4 server. */
343          status =  nx_http_client_put_start(&my_client, HTTP_SERVER_ADDRESS,
            "/client_test.htm", "name", "password", 103, 500);
344
345  
346          /* Check status. */
347          if (status != NX_SUCCESS)
348          {
349              tx_thread_sleep(100);
350          }
351  
352      } while (status != NX_SUCCESS);
353  
354  
355  #endif  /* (IPTYPE== 6) */
356  
357  
358      /* Allocate a packet. */
359      status =  nx_packet_allocate(&client_pool, &my_packet, NX_TCP_PACKET,
                        NX_WAIT_FOREVER);
360  
361      /* Check status. */
362      if (status != NX_SUCCESS)
363      {
364          return;
365      }
366  
367      /* Build a simple 103-byte HTML page. */
368      nx_packet_data_append(my_packet, "<HTML>\r\n", 8,
369                          &client_pool, NX_WAIT_FOREVER);
370      nx_packet_data_append(my_packet,
371                   "<HEAD><TITLE>NetX HTTP Test</TITLE></HEAD>\r\n", 44,
372                          &client_pool, NX_WAIT_FOREVER);
373      nx_packet_data_append(my_packet, "<BODY>\r\n", 8,
374                          &client_pool, NX_WAIT_FOREVER);
375      nx_packet_data_append(my_packet, "<H1>Another NetX Test Page!</H1>\r\n", 25,
376                          &client_pool, NX_WAIT_FOREVER);
377      nx_packet_data_append(my_packet, "</BODY>\r\n", 9,
378                          &client_pool, NX_WAIT_FOREVER);
379      nx_packet_data_append(my_packet, "</HTML>\r\n", 9,
380                          &client_pool, NX_WAIT_FOREVER);
381  
382      /* Complete the PUT by writing the total length. */
383      status =  nx_http_client_put_packet(&my_client, my_packet, 50);
384  
385      /* Check status. */
386      if (status != NX_SUCCESS)
387      {
388          return;
389      }
390  
391      /* Now GET the test file  */
392  
393  #ifdef USE_DUO
394  
395      status =  nxd_http_client_get_start(&my_client, &server_ip_address,
396                     "/client_test.htm", NX_NULL, 0, "name", "password", 50);
397  #else
398  
399      status =  nx_http_client_get_start(&my_client, HTTP_SERVER_ADDRESS,
                 "/client_test.htm",  NX_NULL, 0, "name", "password", 50);
400
401  #endif
402  
403      /* Check status. */
404      if (status != NX_SUCCESS)
405      {
406          return;
407      }
408  
409      status = nx_http_client_delete(&my_client);
410  
411      return;
413  }
414  
416  /* Define the helper HTTP server thread. */
417  void    thread_server_entry(ULONG thread_input)
418  {
419  
420  UINT            status;
421  #if (IPTYPE == 6)
422  UINT            address_index
423  NXD_ADDRESS     ip_address
424  
425      /* Allow time for the IP task to initialize the driver. */
426      tx_thread_sleep(100);
427
428    ip_address.nxd_ip_version = NX_IP_VERSION_V6;
429    ip_address.nxd_ip_address.v6[0] = 0x20010000;
430    ip_address.nxd_ip_address.v6[1] = 0;
431    ip_address.nxd_ip_address.v6[2] = 0;
432    ip_address.nxd_ip_address.v6[3] = 4;
433  
434      /* Here's where we make the HTTP server IPv6 enabled. */
435      nxd_ipv6_enable(&server_ip);
436      nxd_icmp_enable(&server_ip);
437  
438      /* Wait till the IP task thread has set the device MAC address. */
439      while (server_ip.nx_ip_arp_physical_address_msw == 0 ||
440             server_ip.nx_ip_arp_physical_address_lsw == 0)
441      {
442          tx_thread_sleep(30);
443      }
444  
445      nxd_ipv6_address_set(&server_ip, 0, NX_NULL, 10, &address_index)
446      nxd_ipv6_ address_set(&server_ip, 0, &ip_address, 64, &address_index);
447  
448      /* Wait for NetX Duo to validate server address. */
449      tx_thread_sleep(400);
450  
451  #endif  /* (IPTYPE == 6) */
452  
453      /* OK to start the HTTPv6 Server. */
454      status = nx_http_server_start(&my_server);
455  
456      if (status != NX_SUCCESS)
457      {
458          return;
459      }
460  
461      /* HTTP server ready to take requests! */
462  
463      /* Let the IP threads execute. */
464      tx_thread_relinquish();
465  
466      return;
467  }
```

**図 1.1 NetX Duo での HTTP の使用例**

## <a name="configuration-options"></a>構成オプション

NetX Duo 用 HTTP を構築するための構成オプションがいくつかあります。 すべてのオプションとそれぞれの詳細を以下に示します。 既定値が示されていますが、*nxd_http_client.h* および *nxd_http_server.h* をインクルードする前に再定義できます。

 - **NX_DISABLE_ERROR_CHECKING**: このオプションを定義すると、基本的な HTTP エラー チェックが削除されます。 通常は、アプリケーションがデバッグされた後に使用されます。
 - **NX_HTTP_SERVER_PRIORITY**: HTTP サーバーのスレッドの優先順位。 既定では、この値は 16 番目の優先順位を示す 16 に定義されています。
 - **NX_HTTP_NO_FILEX**: このオプションを定義すると、FileX の依存関係のスタブが提供されます。 このオプションを定義しても、HTTP クライアントは変更なしで機能します。 HTTP サーバーを適切に機能させるには、変更を行うか、ユーザーがいくつかの FileX サービスを作成する必要があります。
 - **NX_HTTP_TYPE_OF_SERVICE**: HTTP TCP 要求に必要なサービスの種類。 既定では、この値は通常の IP パケット サービスを示す NX_IP_NORMAL に定義されています。
  - **NX_HTTP_SERVER_THREAD_TIME_SLICE**: 同じ優先順位のスレッドに譲る前に、サーバー スレッドが実行を許可されるタイマー刻みの数。 既定値は 2 です。
 - **NX_HTTP_FRAGMENT_OPTION**: HTTP TCP 要求のフラグメントを有効にします。 この値は既定では NX_DONT_FRAGMENT であり、HTTP TCP のフラグメント化が無効になります。
 - **NX_HTTP_SERVER_WINDOW_SIZE**: サーバー ソケットのウィンドウ サイズ。 この値は既定では 2,048 バイトです。
 - **NX_HTTP_TIME_TO_LIVE**: このパケットが破棄されるまでに通過できるルーターの数を指定します。 既定値は 0x80 に設定されています。
 - **NX_HTTP_SERVER_TIMEOUT**: 内部サービスが中断される ThreadX ティックの数を指定します。 既定値は 10 秒 (10 * NX_IP_PERIODIC_RATE) に設定されています。
 - **NX_HTTP_SERVER_TIMEOUT_ACCEPT**: 内部 *nx_tcp_server_socket_accept* 呼び出しで内部サービスが中断される ThreadX ティックの数を指定します。 既定値は (10 * NX_IP_PERIODIC_RATE) に設定されています。
 - **NX_HTTP_SERVER_TIMEOUT_DISCONNECT**: 内部 *nx_tcp_socket_disconnect* 呼び出しで内部サービスが中断される ThreadX ティックの数を指定します。 既定値は 10 秒 (10 * NX_IP_PERIODIC_RATE) に設定されています。
 - **NX_HTTP_SERVER_TIMEOUT_RECEIVE**: 内部 *nx_tcp_socket_receive* 呼び出しで内部サービスが中断される ThreadX ティックの数を指定します。 既定値は 10 秒 (10 * NX_IP_PERIODIC_RATE) に設定されています。
 - **NX_HTTP_SERVER_TIMEOUT_SEND**: 内部 *nx_tcp_socket_send* 呼び出しで内部サービスが中断される ThreadX ティックの数を指定します。 既定値は 10 秒 (10 * NX_IP_PERIODIC_RATE) に設定されています。
 - **NX_HTTP_MAX_HEADER_FIELD**: HTTP ヘッダー フィールドの最大サイズを指定します。 既定値は 256 です。
 - **NX_HTTP_MULTIPART_ENABLE**: 定義した場合、HTTP サーバーでマルチパート HTTP 要求をサポートできるようになります。
 - **NX_HTTP_SERVER_MAX_PENDING**: HTTP サーバーのキューに登録できる接続の数を指定します。 既定値は 5 に設定されています。
 - **NX_HTTP_MAX_RESOURCE**: クライアントで指定される "*リソース名*" に許容されるバイト数を指定します。 既定値は 40 に設定されています。
 - **NX_HTTP_MAX_NAME**: クライアントで指定される "*ユーザー名*" に許容されるバイト数を指定します。 既定値は 20 に設定されています。
 - **NX_HTTP_MAX_PASSWORD**: クライアントで指定される "*パスワード*" に許容されるバイト数を指定します。 既定値は 20 に設定されています。
 - **NX_HTTP_SERVER_MIN_PACKET_SIZE**: サーバーの作成時に指定されたプール内のパケットの最小サイズを指定します。 最小サイズは、完全な HTTP ヘッダーを 1 つのパケットに含めることができるようにするために必要です。 既定値は 600 に設定されています。
 - **NX_HTTP_CLIENT_MIN_PACKET_SIZE**: クライアントの作成時に指定されたプール内のパケットの最小サイズを指定します。 最小サイズは、完全な HTTP ヘッダーを 1 つのパケットに含めることができるようにするために必要です。 既定値は 300 に設定されています。
 - **NX_HTTP_SERVER_RETRY_SECONDS**: サーバー ソケットの再送信タイムアウトを秒単位で設定します。 既定値は 2 に設定されています。
 - **NX_HTTP_SERVER_RETRY_MAX**: サーバー ソケットの最大再送信回数を設定します。 既定値は 10 に設定されています。
 - **NX_HTTP_SERVER_RETRY_SHIFT**: この値は、次の再送信タイムアウトを設定するために使用されます。 現在のタイムアウトにこれまでの再送信回数が乗算され、ソケット タイムアウト シフトの値でシフトされます。 既定値は 1 に設定されており、タイムアウトが 2 倍になります。
 - **NX_HTTP_SERVER_TRANSMIT_QUEUE_DEPTH**: サーバー ソケット再送信キューにエンキューできるパケットの最大数を指定します。 エンキューされたパケットの数がこの数に達した場合、エンキューされた 1 つ以上のパケットが解放されるまで、これ以上パケットを送信することはできません。 既定値は 20 に設定されています。
