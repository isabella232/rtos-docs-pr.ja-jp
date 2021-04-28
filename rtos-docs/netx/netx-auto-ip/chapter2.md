---
title: チャプター 2 - Azure RTOS NetX AutoIP のインストールと使用
description: このチャプターでは、Azure RTOS NetX AutoIP コンポーネントのインストール、セットアップ、使用に関するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 269a3b4e9754fdc19e2cf1482d483fad2b841de9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810427"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-autoip"></a>チャプター 2 - Azure RTOS NetX AutoIP のインストールと使用

このチャプターでは、Azure RTOS NetX AutoIP コンポーネントのインストール、セットアップ、使用に関するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品の配布パッケージ

NetX の AutoIP は [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) で入手できます。 パッケージの内容は、次に挙げるソースファイル 3 つ、インクルード ファイル 1 つ、このドキュメントを含む PDF ファイルです:

- **nx_auto_ip.h**: NetX AutoIP のヘッダー ファイル
- **nx_auto_ip.c**: NetX AutoIP の C 言語のソース ファイル
- **demo_netx_auto_ip.c**: NetX AutoIP Demo の C 言語のソース ファイル
- **nx_auto_ip.pdf**: NetX AutoIP の説明書の PDF ファイル

## <a name="autoip-installation"></a>AutoIP のインストール

NetX AutoIP を使用するには、NetX がインストールされているのと同じディレクトリに、前述の配布パッケージを丸ごとコピーします。 たとえば、NetX がディレクトリ *\threadx\arm7\green* にインストールされている場合は、 *nx_auto_ip.h*、*nx_auto_ip.c*、*demo_netx_auto_ip.c* ファイルをこのディレクトリにコピーします。

## <a name="using-autoip"></a>AutoIP を使用する

NetX AutoIP の使用方法は簡単です。 基本的に、ThreadX と NetX を使用するためには、アプリケーションのコードに *tx_api.h* と *nx_api.h* をインクルードしてから *nx_auto_ip.h* をインクルードする必要があります。 *nx_auto_ip* をインクルードすると、このガイドで後述する AutoIP の関数を、アプリケーションのコードで呼び出せるようになります。 アプリケーションのビルド時に *nx_auto_ip.c* もインクルードする必要があります。 これらのファイルは、アプリケーションの他のファイルと同様にコンパイルし、オブジェクトとしてアプリケーションのファイルと共にリンクする必要があります。 NetX AutoIP の使用に必要なものはこれですべてです。

> [!NOTE]
> AutoIP は NetX ARP サービスを利用するので、AutoIP を使用する前に *nx_arp_enable* を呼び出して ARP を有効にしておく必要があります。

## <a name="small-example-system"></a>簡単なシステムの例

NetX AutoIP の簡単な使用方法の例を、下の図 1.1 に示します。 この例では、AutoIP のインクルード ファイル *nx_auto_ip.h* を 002 行目に置きます。 次に、090 行目の *tx_application_define* で NetX AutoIP インスタンスを作成します。 NetX AutoIP 制御ブロック auto_ip_0 は、015 行目であらかじめグローバル変数として定義してあります。 作成を完了した後、098 行目で NetX AutoIP を開始します。 IP アドレス変更コールバック関数の処理を 105 行目で開始します。これは、後に生じる競合や潜在的な DHCP アドレスの解決に使用します。

> [!NOTE]
> 下の例では、ホスト デバイスがシングル　ホーム デバイスであることを前提にしています。 マルチホーム デバイスの場合、ホスト アプリケーションで NetX AutoIP サービスの *nx_auto_ip_interface_* set を使用して、どのセカンダリ ネットワーク インターフェイスで IP アドレスを調べるかを指定できます。 マルチホーム アプリケーションのセットアップの詳細は『**NetX ユーザー ガイド**』をご覧ください。 ホスト アプリケーションでは、NetX API *nx_status_ip_interface_check* を使用し、AutoIP で IP アドレスを取得できたかどうかを確認する必要があります。

## <a name="example-of-autoip-use-with-netx"></a>NetX での AutoIP の使用例

```c
000 #include "tx_api.h"
001 #include "nx_api.h"
002 #include "nx_auto_ip.h"
003
004 #define         DEMO_STACK_SIZE         4096
005
006 /* Define the ThreadX and NetX object control blocks... */
007
008 TX_THREAD         thread_0;
009 NX_PACKET_POOL    pool_0;
010 NX_IP             ip_0;
011
012
013 /* Define the AUTO IP structures for the IP instance. */
014
015 NX_AUTO_IP         auto_ip_0;
016
017
018 /* Define the counters used in the demo application... */
019
020 ULONG             thread_0_counter;
021 ULONG             address_changes;
022 ULONG             error_counter;
023
024
025 /* Define thread prototypes. */
026
027 void     thread_0_entry(ULONG thread_input);
028 void     ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address);
029 void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
030
031
032 /* Define main entry point. */
033
034 int main()
035 {
036
037     /* Enter the ThreadX kernel. */
038     tx_kernel_enter();
039 }
040
041
042 /* Define what the initial system looks like. */
043
044 void     tx_application_define(void *first_unused_memory)
045 {
046
047 CHAR     *pointer;
048 UINT     status;
049
050
051     /* Setup the working pointer. */
052     pointer = (CHAR *) first_unused_memory;
053
054     /* Create the main thread. */
055     tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
056                     pointer, DEMO_STACK_SIZE,
057                     16, 16, 1, TX_AUTO_START);
058
059     pointer = pointer + DEMO_STACK_SIZE;
060
061     /* Initialize the NetX system. */
062     nx_system_initialize();
063
064     /* Create a packet pool. */
065     status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 128,
066                                     pointer, 4096);
067                                     pointer = pointer + 4096;
068
069     if (status)
070         error_counter++;
071
072     /* Create an IP instance. */
073     status = nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(0, 0, 0, 0),
074                             0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
075                             pointer, 4096, 1);
076                             pointer = pointer + 4096;
077
078     if (status)
079         error_counter++;
080
081     /* Enable ARP and supply ARP cache memory for IP Instance 0. */
082     status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
083     pointer = pointer + 1024;
084
085     /* Check ARP enable status. */
086     if (status)
087         error_counter++;
088
089     /* Create the AutoIP instance for IP Instance 0. */
090     status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);
091     pointer = pointer + 4096;
092
093     /* Check AutoIP create status. */
094     if (status)
095         error_counter++;
096
097     /* Start AutoIP instances. */
098     status = nx_auto_ip_start(&auto_ip_0, 0 /*IP_ADDRESS(169,254,254,255)*/);
099
100     /* Check AutoIP start status. */
101     if (status)
102         error_counter++;
103
104     /* Register an IP address change function for IP Instance 0. */
105     status = nx_ip_address_change_notify(&ip_0, ip_address_changed,
106                                         (void *) &auto_ip_0);
107
108     /* Check IP address change notify status. */
109     if (status)
110         error_counter++;
111     }
112
113
114     /* Define the test thread. */
115
116     void thread_0_entry(ULONG thread_input)
117     {
118
119     UINT      status;
120     ULONG     actual_status;
121
122
123          /* Wait for IP address to be resolved. */
124         do
125         {
126
127             /* Call IP status check routine. */
128             status = nx_ip_status_check(&ip_0, NX_IP_ADDRESS_RESOLVED,
129                                         &actual_status, 10000);
130
131         } while (status != NX_SUCCESS);
132
133         /* Since the IP address is resolved at this point, the application
134         can now fully utilize NetX! */
135
136         while(1)
137         {
138
139
140
141             /* Increment thread 0's counter. */
142             thread_0_counter++;
143
144             /* Sleep... */
145             tx_thread_sleep(10);
146         }
147     }
148
149
150     void ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address)
151     {
152
153     ULONG         ip_address;
154     ULONG         network_mask;
155     NX_AUTO_IP    *auto_ip_ptr;
156
157
158     /* Setup pointer to auto IP instance. */
159     auto_ip_ptr = (NX_AUTO_IP *) auto_ip_address;
160
161     /* Pickup the current IP address. */
162     nx_ip_address_get(ip_ptr, &ip_address, &network_mask);
163
164     /* Determine if the IP address has changed back to zero. If so,
165     make sure the AutoIP instance is started. */
166     if (ip_address == 0)
167     {
168
169         /* Get the last AutoIP address for this node. */
170         nx_auto_ip_get_address(auto_ip_ptr, &ip_address);
171
172         /* Start this AutoIP instance. */
173         nx_auto_ip_start(auto_ip_ptr, ip_address);
174     }
175
176     /* Determine if IP address has transitioned to a non local IP address. */
177     else if ((ip_address & 0xFFFF0000UL) != IP_ADDRESS(169, 254, 0, 0))
178     {
179
180         /* Stop the AutoIP processing. */
181         nx_auto_ip_stop(auto_ip_ptr);
182     }
183
184     /* Increment a counter. */
185     address_changes++;
186 }
```

## <a name="configuration-options"></a>構成オプション

NetX AutoIP を構築するための構成オプションはいくつかあります。 次のリストですべてのオプションを 1 つずつ詳述します:

- **NX_DISABLE_ERROR_CHECKING**: このオプションを有効にすると、AutoIP の基本的なエラー チェックを行いません。 通常、アプリケーションのデバッグ後に使用します。
- **NX_AUTO_IP_PROBE_WAIT**: 最初のプローブを送信するまでの秒単位の待機時間。 既定値は 1 です。
- **NX_AUTO_IP_PROBE_NUM**: 送信する ARP プローブの数。 既定値は 3 です。
- **NX_AUTO_IP_PROBE_MIN**: プローブを送信してから次のプローブを送信するまでの、秒単位の最小待機時間。 既定値は 1 です。
- **NX_AUTO_IP_PROBE_MAX**: プローブを送信してから次のプローブを送信するまでの、秒単位の最大待機時間。 既定値は 2 です。
- **NX_AUTO_IP_MAX_CONFLICTS**: 処理時間を伸ばす基準にする AutoIP の競合数。 既定値は 10 です。
- **NX_AUTO_IP_RATE_LIMIT_INTERVAL**: 合計競合数が基準を超過したときの、秒単位の延長時間。 既定値は 60 です。
- **NX_AUTO_IP_ANNOUNCE_WAIT**: 通知を送信するまでの、秒単位の待機時間。 既定値は 2 です。
- **NX_AUTO_IP_ANNOUNCE_NUM**: 送信する ARP 通知の数。 既定値は 2 です。
- **NX_AUTO_IP_ANNOUNCE_INTERVAL**: 通知を送信してから次の通知を送信するまでの、秒単位の待機時間。 既定値は 2 です。
- **NX_AUTO_IP_DEFEND_INTERVAL**: 防衛通知を送信してから次の防衛通知を送信するまでの、秒単位の待機時間。 既定値は 10 です。