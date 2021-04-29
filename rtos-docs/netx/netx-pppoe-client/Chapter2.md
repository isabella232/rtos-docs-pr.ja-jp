---
title: 第 2 章 - Azure RTOS NetX PPPoE クライアントのインストールと使用
description: この章では、Azure RTOS NetX PPPoE クライアント コンポーネントのインストール、セットアップ、使用に関するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 17d910647db7b207280b3fbd9e90c468293a8e67
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811453"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pppoe-client"></a>第 2 章 - Azure RTOS NetX PPPoE クライアントのインストールと使用

この章では、Azure RTOS NetX PPPoE クライアント コンポーネントのインストール、セットアップ、使用に関するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品の配布

NetX 用の PPPoE クライアントは、[https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) で入手できます。 パッケージには次のファイルが含まれています。

 - **nx_pppoe_client.h** NetX 用 PPPoE クライアントのヘッダー ファイル
 - **nx_pppoe_client.c** NetX 用 PPPoE クライアントの C ソース ファイル
 - **nx_pppoe_client.pdf** NetX 用 PPPoE クライアントの説明 PDF
 - **demo_netx_pppoe_client.c** NetX PPPoE クライアントのデモンストレーション

## <a name="pppoe-client-installation"></a>PPPoE クライアントのインストール

NetX 用 PPPoE クライアントを使用するには、前述のディストリビューション全体を、NetX がインストールされているのと同じディレクトリにコピーする必要があります。 たとえば、NetX が " *\threadx\arm7\green*" ディレクトリにインストールされている場合は、*nx_pppoe_client.h* および *nx_pppoe_client.c* ファイルをこのディレクトリにコピーする必要があります。

## <a name="using-pppoe-client"></a>PPPoE クライアントの使用

NetX 用の PPPoE クライアントは簡単に使用できます。 基本的には、ThreadX と NetX を使用するために、アプリケーション コードにそれぞれ *tx_api.h* と *nx_api.h* をインクルードした後に、*nx_pppoe_client.h* をインクルードする必要があります。 *nx_pppoe_client.h* をインクルードすると、アプリケーション コードで、このガイドで後述する PPPoE クライアント関数呼び出しを行えるようになります。 アプリケーションでは、ビルド プロセスで *nx_pppoe_client.c* もインクルードする必要があります。 このファイルは、他のアプリケーション ファイルと同様にコンパイルする必要があり、そのオブジェクト形式は、アプリケーションのファイルと一緒にリンクする必要があります。 NetX PPPoE クライアントを使用するために必要なことはこれだけです。

## <a name="small-example-system"></a>小さなシステムの例

NetX PPPoE クライアントの使用方法を示す例を次の図 1.1 に示します。 この例では、PPPoE クライアント インクルード ファイル *nx_pppoe_client.h* が 50 行目で取り込まれます。 次に、"*thread_0_entry*" で PPPoE クライアントが作成されます (238 行目)。 IP インスタンスを作成してから、PPPoE クライアントを作成する必要があることに注意してください。 IP インスタンスと PPP インスタンスが作成されて初期化されます (142 - 220 行目)。 PPPoE クライアント制御ブロック "*pppoe_client*" は、グローバル変数として定義されています (75 行目)。 送信および受信関数は 238 行目で設定されます。

一般に、PPPoE モジュールは PPP モジュールと共に使用します。 この例では、PPP クライアント インクルード ファイル *nx_ppp.h* が 49 行目で取り込まれます。 次に、PPP クライアントが作成されます (164 行目)。 PPP パケットを送信するように関数を設定します (172 行目)。 IP アドレスを設定し、PAP プロトコルを定義します (179 - 190 行目)。 PAP プロトコルのユーザー名とパスワードを設定します (104 - 129 行目)。

PPPoE セッションが確立された後。 アプリケーションでは、*nx_pppoe_client_session_get* を呼び出して、セッション情報 (クライアントの MAC アドレスとセッション ID) を取得できます (264 行目)。 PPP またはアプリケーションでは、*nx_pppoe_client_session_packet_send* を呼び出して、PPPoE パケットを送信できます (283 行目)。

アプリケーションで PPP トラフィックを処理しなくなったら、*nx_pppoe_client_session_terminate* を呼び出して PPPoE セッションを終了できます。

この例の PPPoE クライアントでは、通常の IP スタックも同時に使用され、1 つのイーサネット ドライバーが共有されていることに注意してください。 通常の IP インスタンス (155 行目) と PPPoE クライアント インスタンス (298 行目) に、同じイーサネット ドライバーを渡します。

> [!NOTE]
> 物理ヘッダーを入力するための十分な領域を確保するため、**NX_PHYSICAL_HEADER** を 24 に再定義します。 物理ヘッダー: 14 (イーサネット ヘッダー) + 6 (PPPoE ヘッダー) + 2 (PPP ヘッダー) + 2 (4 バイト アラインメント)。

```c
  1 /**************************************************************************/
  2 /**************************************************************************/
  3 /**                                                                       */
  4 /** NetX PPPoE Client stack Component                                     */
  5 /**                                                                       */
  6 /**   This is a small demo of the high-performance NetX PPPoE Client      */
  7 /**   stack. This demo includes IP instance, PPPoE Client and PPP Client  */
  8 /**   stack. Create one IP instance includes two interfaces to support    */
  9 /**   for normal IP stack and PPPoE Client, PPPoE Client can use the      */
 10 /**   mutex of IP instance to send PPPoE message when share one Ethernet  */
 11 /**   driver. PPPoE Client work with normal IP instance at the same time. */
 12 /**                                                                       */
 13 /**   Note1: Substitute your Ethernet driver instead of                   */
 14 /**   _nx_ram_network_driver before run this demo                         */
 15 /**                                                                       */
 16 /**   Note2: Prerequisite for using PPPoE.                                */
 17 /**   Redefine NX_PHYSICAL_HEADER to 24 to ensure enough space for filling*/
 18 /**   in physical header. Physical header:14(Ethernet header)             */
 19 /**    + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment)          */
 20 /**                                                                       */
 21 /**************************************************************************/
 22 /**************************************************************************/
 23
 24
 25       /*****************************************************************/
 26       /*                          NetX Stack                           */
 27       /*****************************************************************/
 28
 29                                             /***************************/
 30                                             /*        PPP Client       */
 31                                             /***************************/
 32
 33                                             /***************************/
 34                                             /*       PPPoE Client      */
 35                                             /***************************/
 36       /***************************/         /***************************/
 37       /*    Normal Ethernet Type */         /*    PPPoE Ethernet Type  */
 38       /***************************/         /***************************/
 39       /***************************/         /***************************/
 40       /*       Interface 0       */         /*       Interface 1       */
 41       /***************************/         /***************************/
 42
 43       /*****************************************************************/
 44       /*                       Ethernet Dirver                         */
 45       /*****************************************************************/
 46
 47 #include   "tx_api.h"
 48 #include   "nx_api.h"
 49 #include   "nx_ppp.h"
 50 #include   "nx_pppoe_client.h"
 51
 52 /* Defined NX_PPP_PPPOE_ENABLE if use Express Logic's PPP, since PPP module has been modified
       to match PPPoE moduler under this definition.  */
 53 #ifdef NX_PPP_PPPOE_ENABLE
 54
 55 /* If the driver is not initialized in other module, define NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE
       to initialize the driver in PPPoE module .
 56    In this demo, the driver has been initialized in IP module.  */
 57 #ifndef NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE
 58
 59 /* Define the block size.  */
 60 #define     NX_PACKET_POOL_SIZE     ((1536 + sizeof(NX_PACKET)) * 30)
 61 #define     DEMO_STACK_SIZE         2048
 62 #define     PPPOE_THREAD_SIZE       2048
 63
 64 /* Define the ThreadX and NetX object control blocks...  */
 65 TX_THREAD               thread_0;
 66
 67 /* Define the packet pool and IP instance for normal IP instnace.  */
 68 NX_PACKET_POOL          pool_0;
 69 NX_IP                   ip_0;
 70
71 /* Define the PPP Client instance.  */
 72 NX_PPP                  ppp_client;
 73
 74 /* Define the PPPoE Client instance.  */
 75 NX_PPPOE_CLIENT         pppoe_client;
 76
 77 /* Define the counters.  */
 78 CHAR                    *pointer;
 79 ULONG                   error_counter;
 80
 81 /* Define thread prototypes.  */
 82 void    thread_0_entry(ULONG thread_input);
 83
 84 /***** Substitute your PPP driver entry function here *********/
 85 extern void    _nx_ppp_driver(NX_IP_DRIVER *driver_req_ptr);
 86
 87 /***** Substitute your Ethernet driver entry function here *********/
 88 extern void    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
 89
 90 /* Define the porting layer function for Express Logic's PPP to simulate TTP's PPP.
 91    Functions to be provided by PPP for calling by the PPPoE Stack.  */
 92 void    ppp_client_packet_send(NX_PACKET *packet_ptr);
 93 void    pppoe_client_packet_receive(NX_PACKET *packet_ptr);
 94
 95 /* Define main entry point.  */
 96
 97 int main()
 98 {
 99
100     /* Enter the ThreadX kernel.  */
101     tx_kernel_enter();
102 }
103
104 UINT generate_login(CHAR *name, CHAR *password)
105 {
106
107     /* Make a name and password, called "myname" and "mypassword".  */
108     name[0] = 'm';
109     name[1] = 'y';
110     name[2] = 'n';
111     name[3] = 'a';
112     name[4] = 'm';
113     name[5] = 'e';
114     name[6] = (CHAR) 0;
115
116     password[0] = 'm';
117     password[1] = 'y';
118     password[2] = 'p';
119     password[3] = 'a';
120     password[4] = 's';
121     password[5] = 's';
122     password[6] = 'w';
123     password[7] = 'o';
124     password[8] = 'r';
125     password[9] = 'd';
126     password[10] = (CHAR) 0;
127
128     return(NX_SUCCESS);
129 }
130
131 /* Define what the initial system looks like.  */
132
133 void    tx_application_define(void *first_unused_memory)
134 {
135
136 UINT    status;
137
138     /* Setup the working pointer.  */
139     pointer =  (CHAR *) first_unused_memory;
140
141     /* Initialize the NetX system.  */
142     nx_system_initialize();
143
144     /* Create a packet pool for normal IP instance.  */
145     status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool",
146                                    (1536 + sizeof(NX_PACKET)),
147                                    pointer, NX_PACKET_POOL_SIZE);
148     pointer = pointer + NX_PACKET_POOL_SIZE;
149
150     /* Check for error.  */
151     if (status)
152         error_counter++;
153
154     /* Create an normal IP instance.  */
155     status = nx_ip_create(&ip_0, "NetX IP Instance", IP_ADDRESS(192, 168, 100, 44), 0xFFFFFF00UL,
156                           &pool_0, _nx_ram_network_driver, pointer, 2048, 1);
157     pointer = pointer + 2048;
158
159     /* Check for error.  */
160     if (status)
161         error_counter++;
162
163     /* Create the PPP instance.  */
164     status = nx_ppp_create(&ppp_client, "PPP Instance", &ip_0, pointer, 2048, 1,
165                            &pool_0, NX_NULL, NX_NULL); pointer = pointer + 2048;
166
167     /* Check for PPP create error.   */
168     if (status)
169         error_counter++;
170
171     /* Set the PPP packet send function.  */
172     status = nx_ppp_packet_send_set(&ppp_client, ppp_client_packet_send);
173
174     /* Check for PPP packet send function set error.   */
175     if (status)
176         error_counter++;
177
178     /* Define IP address. This PPP instance is effectively the client since it doesn't have
           any IP addresses. */
179     status = nx_ppp_ip_address_assign(&ppp_client, IP_ADDRESS(0, 0, 0, 0), IP_ADDRESS(0, 0, 0, 0));
180
181     /* Check for PPP IP address assign error.   */
182     if (status)
183         error_counter++;
184
185     /* Setup PAP, this PPP instance is effectively the since it generates the name and password
           for the peer..  */
186     status = nx_ppp_pap_enable(&ppp_client, generate_login, NX_NULL);
187
188     /* Check for PPP PAP enable error.  */
189     if (status)
190         error_counter++;
191
192     /* Attach an interface for PPP.  */
193     status = nx_ip_interface_attach(&ip_0, "Second Interface For PPP", IP_ADDRESS(0, 0, 0, 0), 0,
                                        nx_ppp_driver);
194
195     /* Check for error.  */
196     if (status)
197         error_counter++;
198
199     /* Enable ARP and supply ARP cache memory for Normal IP Instance.  */
200     status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
201     pointer = pointer + 1024;
202
203     /* Check for ARP enable errors.  */
204     if (status)
205         error_counter++;
206
207     /* Enable ICMP */
208     status = nx_icmp_enable(&ip_0);
209     if(status)
210         error_counter++;
211
212     /* Enable UDP traffic.  */
213     status =  nx_udp_enable(&ip_0);
214     if (status)
215         error_counter++;
216
217     /* Enable TCP traffic.  */
218     status =  nx_tcp_enable(&ip_0);
219     if (status)
220         error_counter++;
221
222     /* Create the main thread.  */
223     tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
224                      pointer, DEMO_STACK_SIZE,
225                      4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
226     pointer =  pointer + DEMO_STACK_SIZE;
227
228 }
229
230 /* Define the test threads.  */
231
232 void    thread_0_entry(ULONG thread_input)
233 {
234 UINT    status;
235 ULONG   ip_status;
236
237     /* Create the PPPoE instance.  */
238     status =  nx_pppoe_client_create(&pppoe_client, (UCHAR *)"PPPoE Client",  &ip_0,  0,
        &pool_0, pointer, PPPOE_THREAD_SIZE, 4, _nx_ram_network_driver, pppoe_client_packet_receive);
239     pointer = pointer + PPPOE_THREAD_SIZE;
240     if (status)
241     {
242         error_counter++;
243         return;
244     }
245
246     /* Establish PPPoE Client sessione.  */
247     status = nx_pppoe_client_session_connect(&pppoe_client, NX_WAIT_FOREVER);
248     if (status)
249     {
250         error_counter++;
251         return;
252     }
253
254     /* Wait for the link to come up.  */
255     status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_ADDRESS_RESOLVED,
                                              &ip_status, NX_WAIT_FOREVER);
256     if (status)
257     {
258         error_counter++;
259         return;
260     }
261
262     /* Get the PPPoE Server physical address and Session ID after establish PPPoE Session.  */
263     /*
264     status = nx_pppoe_client_session_get(&pppoe_client, &server_mac_msw,
                                             &server_mac_lsw, &session_id);
265     if (status)
266         error_counter++;
267     */
268 }
269
270 /* PPPoE Client receive function.  */
271 void    pppoe_client_packet_receive(NX_PACKET *packet_ptr)
272 {
273
274     /* Call PPP Client to receive the PPP data fame.  */
275     nx_ppp_packet_receive(&ppp_client, packet_ptr);
276 }
277
278 /* PPP Client send function.  */
279 void    ppp_client_packet_send(NX_PACKET *packet_ptr)
280 {
281
282     /* Directly Call PPPoE send function to send out the data through PPPoE module.  */
283     nx_pppoe_client_session_packet_send(&pppoe_client, packet_ptr);
284 }
285 #endif /* NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE  */
286
287 #endif /* NX_PPP_PPPOE_ENABLE  */
```

**図 1.1 NetX での PPPoE クライアントの使用例**

## <a name="configuration-options"></a>構成オプション

NetX 用 PPPoE クライアントを構築するための構成オプションがいくつかあります。 次の一覧では、それぞれについて詳しく説明しています。

- **NX_DISABLE_ERROR_CHECKING** このオプションを定義すると、基本的な PPPoE クライアント エラー チェックが削除されます。 通常は、アプリケーションがデバッグされた後に使用されます。
- **NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE** 定義した場合、PPPoE モジュールでイーサネット ドライバーを初期化する機能が有効になります。 既定では無効になります。
- **NX_PPPOE_CLIENT_THREAD_TIME_SLICE** PPPoE クライアント スレッドのタイムスライス オプション。 この値は既定では TX_NO_TIME_SLICE です。
- **NX_PPPOE_CLIENT_PADI_INIT_TIMEOUT** これにより、初期再送 PADI パケットの待機部分が定義されます。 既定値は 1 秒です。
- **NX_PPPOE_CLIENT_PADI_COUNT** これにより、接続が切断されたと見なされるまでに許可される PADI 送信の数が定義されます。 既定値は 4 です。
- **NX_PPPOE_CLIENT_PADR_INIT_TIMEOUT** これにより、初期再送 PADR パケットの待機部分が定義されます。 既定値は 1 秒です。
- **NX_PPPOE_CLIENT_PADR_COUNT** これにより、接続が切断されたと見なされるまでに許可される PADR 送信の数が定義されます。 既定値は 4 です。
- **NX_PPPOE_CLIENT_MAX_AC_NAME_SIZE** これにより、AC 名の最大サイズが定義されます。 この値は既定では 32 です。
- **NX_PPPOE_CLIENT_MAX_AC_COOKIE_SIZE** これにより、AC Cookie の最大サイズが定義されます。 この値は既定では 32 です。
- **NX_PPPOE_CLIENT_MAX_RELAY_SESSION_ID_SIZE** これにより、リレー セッション ID の最大サイズが定義されます。この値は既定では 12 です。
- **NX_PPPOE_CLIENT_MIN_PACKET_PAYLOAD_SIZE** PPPoE クライアントの最小パケット ペイロード サイズを指定します。 パケット ペイロード サイズがこの値より大きい場合、パケット チェーンを回避できます。 この値は既定では 1520 (イーサネットの最大ペイロード サイズ 1500、イーサネット ヘッダー 14、CRC 2、4 バイト アラインメント 4) です。
