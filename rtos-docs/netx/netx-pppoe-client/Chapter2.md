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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pppoe-client"></a><span data-ttu-id="3e167-103">第 2 章 - Azure RTOS NetX PPPoE クライアントのインストールと使用</span><span class="sxs-lookup"><span data-stu-id="3e167-103">Chapter 2 - Installation and Use of Azure RTOS NetX PPPoE Client</span></span>

<span data-ttu-id="3e167-104">この章では、Azure RTOS NetX PPPoE クライアント コンポーネントのインストール、セットアップ、使用に関するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e167-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX PPPoE Client component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="3e167-105">製品の配布</span><span class="sxs-lookup"><span data-stu-id="3e167-105">Product Distribution</span></span>

<span data-ttu-id="3e167-106">NetX 用の PPPoE クライアントは、[https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="3e167-106">The PPPoE Client for NetX is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="3e167-107">パッケージには次のファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3e167-107">The package includes the following files:</span></span>

 - <span data-ttu-id="3e167-108">**nx_pppoe_client.h** NetX 用 PPPoE クライアントのヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="3e167-108">**nx_pppoe_client.h** Header file for PPPoE Client for NetX</span></span>
 - <span data-ttu-id="3e167-109">**nx_pppoe_client.c** NetX 用 PPPoE クライアントの C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="3e167-109">**nx_pppoe_client.c** C Source file for PPPoE Client for NetX</span></span>
 - <span data-ttu-id="3e167-110">**nx_pppoe_client.pdf** NetX 用 PPPoE クライアントの説明 PDF</span><span class="sxs-lookup"><span data-stu-id="3e167-110">**nx_pppoe_client.pdf** PDF description of PPPoE Client for NetX</span></span>
 - <span data-ttu-id="3e167-111">**demo_netx_pppoe_client.c** NetX PPPoE クライアントのデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="3e167-111">**demo_netx_pppoe_client.c** NetX PPPoE Client demonstration</span></span>

## <a name="pppoe-client-installation"></a><span data-ttu-id="3e167-112">PPPoE クライアントのインストール</span><span class="sxs-lookup"><span data-stu-id="3e167-112">PPPoE Client Installation</span></span>

<span data-ttu-id="3e167-113">NetX 用 PPPoE クライアントを使用するには、前述のディストリビューション全体を、NetX がインストールされているのと同じディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e167-113">In order to use PPPoE Client for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="3e167-114">たとえば、NetX が " *\threadx\arm7\green*" ディレクトリにインストールされている場合は、*nx_pppoe_client.h* および *nx_pppoe_client.c* ファイルをこのディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e167-114">For example, if NetX is installed in the directory *“\threadx\arm7\green”* then the *nx_pppoe_client.h* and *nx_pppoe_client.c* files should be copied into this directory.</span></span>

## <a name="using-pppoe-client"></a><span data-ttu-id="3e167-115">PPPoE クライアントの使用</span><span class="sxs-lookup"><span data-stu-id="3e167-115">Using PPPoE Client</span></span>

<span data-ttu-id="3e167-116">NetX 用の PPPoE クライアントは簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="3e167-116">Using PPPoE Client for NetX is easy.</span></span> <span data-ttu-id="3e167-117">基本的には、ThreadX と NetX を使用するために、アプリケーション コードにそれぞれ *tx_api.h* と *nx_api.h* をインクルードした後に、*nx_pppoe_client.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e167-117">Basically, the application code must include *nx_pppoe_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="3e167-118">*nx_pppoe_client.h* をインクルードすると、アプリケーション コードで、このガイドで後述する PPPoE クライアント関数呼び出しを行えるようになります。</span><span class="sxs-lookup"><span data-stu-id="3e167-118">Once *nx_pppoe_client.h* is included, the application code is then able to make the PPPoE Client function calls specified later in this guide.</span></span> <span data-ttu-id="3e167-119">アプリケーションでは、ビルド プロセスで *nx_pppoe_client.c* もインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e167-119">The application must also include *nx_pppoe_client.c* in the build process.</span></span> <span data-ttu-id="3e167-120">このファイルは、他のアプリケーション ファイルと同様にコンパイルする必要があり、そのオブジェクト形式は、アプリケーションのファイルと一緒にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e167-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="3e167-121">NetX PPPoE クライアントを使用するために必要なことはこれだけです。</span><span class="sxs-lookup"><span data-stu-id="3e167-121">This is all that is required to use NetX PPPoE Client.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="3e167-122">小さなシステムの例</span><span class="sxs-lookup"><span data-stu-id="3e167-122">Small Example System</span></span>

<span data-ttu-id="3e167-123">NetX PPPoE クライアントの使用方法を示す例を次の図 1.1 に示します。</span><span class="sxs-lookup"><span data-stu-id="3e167-123">The following is an example that illustrates how to use NetX PPPoE Client is described in Figure 1.1.</span></span> <span data-ttu-id="3e167-124">この例では、PPPoE クライアント インクルード ファイル *nx_pppoe_client.h* が 50 行目で取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="3e167-124">In this example, the PPPoE Client include file *nx_pppoe_client.h* is brought in at line 50.</span></span> <span data-ttu-id="3e167-125">次に、"*thread_0_entry*" で PPPoE クライアントが作成されます (238 行目)。</span><span class="sxs-lookup"><span data-stu-id="3e167-125">Next, PPPoE Client is created in *”thread_0_entry”* at line 238.</span></span> <span data-ttu-id="3e167-126">IP インスタンスを作成してから、PPPoE クライアントを作成する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3e167-126">Note that PPPoE Client should be created after create the IP instance.</span></span> <span data-ttu-id="3e167-127">IP インスタンスと PPP インスタンスが作成されて初期化されます (142 - 220 行目)。</span><span class="sxs-lookup"><span data-stu-id="3e167-127">The IP instance and PPP instance are created and initialized line142-220.</span></span> <span data-ttu-id="3e167-128">PPPoE クライアント制御ブロック "*pppoe_client*" は、グローバル変数として定義されています (75 行目)。</span><span class="sxs-lookup"><span data-stu-id="3e167-128">The PPPoE Client control block *“pppoe_client”* was defined as a global variable at line 75 previously.</span></span> <span data-ttu-id="3e167-129">送信および受信関数は 238 行目で設定されます。</span><span class="sxs-lookup"><span data-stu-id="3e167-129">The send and receive functions are set at line 238.</span></span>

<span data-ttu-id="3e167-130">一般に、PPPoE モジュールは PPP モジュールと共に使用します。</span><span class="sxs-lookup"><span data-stu-id="3e167-130">In general, PPPoE module should be used with PPP module.</span></span> <span data-ttu-id="3e167-131">この例では、PPP クライアント インクルード ファイル *nx_ppp.h* が 49 行目で取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="3e167-131">In this example, the PPP Client include file *nx_ppp.h* is brought in at line 49.</span></span> <span data-ttu-id="3e167-132">次に、PPP クライアントが作成されます (164 行目)。</span><span class="sxs-lookup"><span data-stu-id="3e167-132">Next, PPP Client is created at line 164.</span></span> <span data-ttu-id="3e167-133">PPP パケットを送信するように関数を設定します (172 行目)。</span><span class="sxs-lookup"><span data-stu-id="3e167-133">Line 172 setup the function to send PPP packet.</span></span> <span data-ttu-id="3e167-134">IP アドレスを設定し、PAP プロトコルを定義します (179 - 190 行目)。</span><span class="sxs-lookup"><span data-stu-id="3e167-134">Line 179-190 setup the IP addresses and define the pap protocol.</span></span> <span data-ttu-id="3e167-135">PAP プロトコルのユーザー名とパスワードを設定します (104 - 129 行目)。</span><span class="sxs-lookup"><span data-stu-id="3e167-135">Line 104-129 setup the user name and password for pap protocol.</span></span>

<span data-ttu-id="3e167-136">PPPoE セッションが確立された後。</span><span class="sxs-lookup"><span data-stu-id="3e167-136">After the PPPoE session established.</span></span> <span data-ttu-id="3e167-137">アプリケーションでは、*nx_pppoe_client_session_get* を呼び出して、セッション情報 (クライアントの MAC アドレスとセッション ID) を取得できます (264 行目)。</span><span class="sxs-lookup"><span data-stu-id="3e167-137">The application can call *nx_pppoe_client_session_get* to get the session information (server MAC address and session id) at line 264.</span></span> <span data-ttu-id="3e167-138">PPP またはアプリケーションでは、*nx_pppoe_client_session_packet_send* を呼び出して、PPPoE パケットを送信できます (283 行目)。</span><span class="sxs-lookup"><span data-stu-id="3e167-138">PPP or Application can call *nx_pppoe_client_session_packet_send* to send PPPoE packet at line 283.</span></span>

<span data-ttu-id="3e167-139">アプリケーションで PPP トラフィックを処理しなくなったら、*nx_pppoe_client_session_terminate* を呼び出して PPPoE セッションを終了できます。</span><span class="sxs-lookup"><span data-stu-id="3e167-139">When the application no longer process PPP traffic, the application can call *nx_pppoe_client_session_terminate* to terminate the PPPoE session.</span></span>

<span data-ttu-id="3e167-140">この例の PPPoE クライアントでは、通常の IP スタックも同時に使用され、1 つのイーサネット ドライバーが共有されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3e167-140">Note, in this example, PPPoE Client work with normal IP stack at the same time, and share one Ethernet driver.</span></span> <span data-ttu-id="3e167-141">通常の IP インスタンス (155 行目) と PPPoE クライアント インスタンス (298 行目) に、同じイーサネット ドライバーを渡します。</span><span class="sxs-lookup"><span data-stu-id="3e167-141">Pass the same Ethernet driver for normal IP instance at line 155 and PPPoE Client instance at line 298.</span></span>

> [!NOTE]
> <span data-ttu-id="3e167-142">物理ヘッダーを入力するための十分な領域を確保するため、**NX_PHYSICAL_HEADER** を 24 に再定義します。</span><span class="sxs-lookup"><span data-stu-id="3e167-142">Redefine **NX_PHYSICAL_HEADER** to 24 to ensure enough space for filling in physical header.</span></span> <span data-ttu-id="3e167-143">物理ヘッダー: 14 (イーサネット ヘッダー) + 6 (PPPoE ヘッダー) + 2 (PPP ヘッダー) + 2 (4 バイト アラインメント)。</span><span class="sxs-lookup"><span data-stu-id="3e167-143">Physical header:14(Ethernet header) + 6(PPPoE header) + 2(PPP header) + 2(four-byte alignment).</span></span>

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

<span data-ttu-id="3e167-144">**図 1.1 NetX での PPPoE クライアントの使用例**</span><span class="sxs-lookup"><span data-stu-id="3e167-144">**Figure 1.1 Example of PPPoE Client use with NetX**</span></span>

## <a name="configuration-options"></a><span data-ttu-id="3e167-145">構成オプション</span><span class="sxs-lookup"><span data-stu-id="3e167-145">Configuration Options</span></span>

<span data-ttu-id="3e167-146">NetX 用 PPPoE クライアントを構築するための構成オプションがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="3e167-146">There are several configuration options for building PPPoE Client for NetX.</span></span> <span data-ttu-id="3e167-147">次の一覧では、それぞれについて詳しく説明しています。</span><span class="sxs-lookup"><span data-stu-id="3e167-147">The following list describes each in detail:</span></span>

- <span data-ttu-id="3e167-148">**NX_DISABLE_ERROR_CHECKING** このオプションを定義すると、基本的な PPPoE クライアント エラー チェックが削除されます。</span><span class="sxs-lookup"><span data-stu-id="3e167-148">**NX_DISABLE_ERROR_CHECKING** Defined, this option removes the basic PPPoE Client error checking.</span></span> <span data-ttu-id="3e167-149">通常は、アプリケーションがデバッグされた後に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3e167-149">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="3e167-150">**NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE** 定義した場合、PPPoE モジュールでイーサネット ドライバーを初期化する機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="3e167-150">**NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE** If defined, enables the feature to initialize the Ethernet driver in PPPoE module.</span></span> <span data-ttu-id="3e167-151">既定では無効になります。</span><span class="sxs-lookup"><span data-stu-id="3e167-151">It disables by default.</span></span>
- <span data-ttu-id="3e167-152">**NX_PPPOE_CLIENT_THREAD_TIME_SLICE** PPPoE クライアント スレッドのタイムスライス オプション。</span><span class="sxs-lookup"><span data-stu-id="3e167-152">**NX_PPPOE_CLIENT_THREAD_TIME_SLICE** Time-slice option for PPPoE Client thread.</span></span> <span data-ttu-id="3e167-153">この値は既定では TX_NO_TIME_SLICE です。</span><span class="sxs-lookup"><span data-stu-id="3e167-153">By default, this value is TX_NO_TIME_SLICE.</span></span>
- <span data-ttu-id="3e167-154">**NX_PPPOE_CLIENT_PADI_INIT_TIMEOUT** これにより、初期再送 PADI パケットの待機部分が定義されます。</span><span class="sxs-lookup"><span data-stu-id="3e167-154">**NX_PPPOE_CLIENT_PADI_INIT_TIMEOUT** This defines the wait potion for initial retransmitting PADI packets.</span></span> <span data-ttu-id="3e167-155">既定値は 1 秒です。</span><span class="sxs-lookup"><span data-stu-id="3e167-155">By default, this value is 1 second.</span></span>
- <span data-ttu-id="3e167-156">**NX_PPPOE_CLIENT_PADI_COUNT** これにより、接続が切断されたと見なされるまでに許可される PADI 送信の数が定義されます。</span><span class="sxs-lookup"><span data-stu-id="3e167-156">**NX_PPPOE_CLIENT_PADI_COUNT** This defines how many PADI transmit retires are allowed before the connection is deemed broken.</span></span> <span data-ttu-id="3e167-157">既定値は 4 です。</span><span class="sxs-lookup"><span data-stu-id="3e167-157">By default, this value is 4.</span></span>
- <span data-ttu-id="3e167-158">**NX_PPPOE_CLIENT_PADR_INIT_TIMEOUT** これにより、初期再送 PADR パケットの待機部分が定義されます。</span><span class="sxs-lookup"><span data-stu-id="3e167-158">**NX_PPPOE_CLIENT_PADR_INIT_TIMEOUT** This defines the wait potion for initial retransmitting PADR packets.</span></span> <span data-ttu-id="3e167-159">既定値は 1 秒です。</span><span class="sxs-lookup"><span data-stu-id="3e167-159">By default, this value is 1 second.</span></span>
- <span data-ttu-id="3e167-160">**NX_PPPOE_CLIENT_PADR_COUNT** これにより、接続が切断されたと見なされるまでに許可される PADR 送信の数が定義されます。</span><span class="sxs-lookup"><span data-stu-id="3e167-160">**NX_PPPOE_CLIENT_PADR_COUNT** This defines how many PADR transmit retires are allowed before the connection is deemed broken.</span></span> <span data-ttu-id="3e167-161">既定値は 4 です。</span><span class="sxs-lookup"><span data-stu-id="3e167-161">By default, this value is 4.</span></span>
- <span data-ttu-id="3e167-162">**NX_PPPOE_CLIENT_MAX_AC_NAME_SIZE** これにより、AC 名の最大サイズが定義されます。</span><span class="sxs-lookup"><span data-stu-id="3e167-162">**NX_PPPOE_CLIENT_MAX_AC_NAME_SIZE** This defines the max size of AC-Name.</span></span> <span data-ttu-id="3e167-163">この値は既定では 32 です。</span><span class="sxs-lookup"><span data-stu-id="3e167-163">By default, this value is 32.</span></span>
- <span data-ttu-id="3e167-164">**NX_PPPOE_CLIENT_MAX_AC_COOKIE_SIZE** これにより、AC Cookie の最大サイズが定義されます。</span><span class="sxs-lookup"><span data-stu-id="3e167-164">**NX_PPPOE_CLIENT_MAX_AC_COOKIE_SIZE** This defines the max size of AC-Cookie.</span></span> <span data-ttu-id="3e167-165">この値は既定では 32 です。</span><span class="sxs-lookup"><span data-stu-id="3e167-165">By default, this value is 32.</span></span>
- <span data-ttu-id="3e167-166">**NX_PPPOE_CLIENT_MAX_RELAY_SESSION_ID_SIZE** これにより、リレー セッション ID の最大サイズが定義されます。この値は既定では 12 です。</span><span class="sxs-lookup"><span data-stu-id="3e167-166">**NX_PPPOE_CLIENT_MAX_RELAY_SESSION_ID_SIZE** This defines the max size of Relay-Session-Id. By default, this value is 12.</span></span>
- <span data-ttu-id="3e167-167">**NX_PPPOE_CLIENT_MIN_PACKET_PAYLOAD_SIZE** PPPoE クライアントの最小パケット ペイロード サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="3e167-167">**NX_PPPOE_CLIENT_MIN_PACKET_PAYLOAD_SIZE** Specifies the Minimum packet payload size for PPPoE Client.</span></span> <span data-ttu-id="3e167-168">パケット ペイロード サイズがこの値より大きい場合、パケット チェーンを回避できます。</span><span class="sxs-lookup"><span data-stu-id="3e167-168">If the packet payload size is greater than this value, can avoid packet chained.</span></span> <span data-ttu-id="3e167-169">この値は既定では 1520 (イーサネットの最大ペイロード サイズ 1500、イーサネット ヘッダー 14、CRC 2、4 バイト アラインメント 4) です。</span><span class="sxs-lookup"><span data-stu-id="3e167-169">By default, this value is 1520 (Maximum Payload Size of Ethernet 1500, Ethernet Header 14, CRC 2 and Four-byte alignment 4).</span></span>
