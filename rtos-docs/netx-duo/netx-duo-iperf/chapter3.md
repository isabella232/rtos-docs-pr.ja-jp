---
title: 第 3 章 - UDP 送信テストの実行
description: この章では、Iperf サンプルを実行する手順について説明します。
author: v-condav
ms.author: v-condav
ms.date: 08/16/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2a68ba3ddb71adc424002c815fd023f50b552997
ms.sourcegitcommit: 4842f4cfe9e31b3ac59059f43e598eb70faebc8f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2021
ms.locfileid: "122609799"
---
# <a name="chapter-3-running-the-demonstration"></a>第 3 章 - デモンストレーションの実行

この章では、前に示したように NetX Duo Iperf デモンストレーションの Web ページがホスト ブラウザーに表示されていて、Jperf がホストで実行されていることを前提に、各 Iperf テストを実行する方法について説明します。

## <a name="running-the-udp-transmit-test"></a>UDP 送信テストの実行

UDP 送信テストでは、ホストへの NetX Duo UDP 送信のパフォーマンスが確認されます。 このテストでは、NetX Duo ターゲットはクライアントで、Jperf ホストはサーバーです。 まず、Jperf IDE で **[Server]\(サーバー\)** と **[UDP]** を選択します。 次に、 **[Run IPerf!]\(IPerf を実行\)** を選択し、 下に示すように Iperf サーバーを開始します。

![UDP 送信テストを実行しています。](media/picture3.jpg)

ここで、NetX Duo Iperf デモンストレーションの Web ページから **[Start UDP Transmit Test]\(UDP 送信テストを開始\)** ボタンを選択して、テストを開始します。 下に示すように、Jperf IDE のパフォーマンス統計と更新された NetX Duo の Web ページが表示されるようになったはずです。

![UDP 送信テストの統計。](media/picture4.jpg)

NetX Duo Iperf デモンストレーションの Web ページにあるリンク、 **[here]\(こちら\)** を選択して、テストを完了します。 これで、テストのパフォーマンス結果が表示されます。 この例では、下に示すように、NetX Duo ターゲットでの Iperf ホストへの UDP 送信パフォーマンスは 94 Mbps でした。

![UDP 送信テストの結果。](media/picture5.jpg)

## <a name="running-the-udp-receive-test"></a>UDP 受信テストの実行

UDP 受信テストでは、NetX Duo ターゲットでの NetX Duo UDP 受信のパフォーマンスが確認されます。 このテストでは、NetX Duo ターゲットはサーバーで、Jperf ホストはクライアントです。 まず、Jperf IDE で **[Client]\(クライアント\)** と **[UDP]** を選択します。 次に、次の図に示すように、NetX Duo Iperf デモンストレーションの Web ページで **[Start UDP Receive Test]\(UDP 受信テストを開始\)** を選択します。

![UDP 受信テストを実行しています。](media/picture6.jpg)

次に、 **[Run IPerf!]\(IPerf を実行\)** を Jperf IDE から選択し、下に示すように Jperf IDE で統計を確認します。

![UDP 受信テストの統計。](media/picture7.jpg)

NetX Duo Iperf デモンストレーションの Web ページにあるリンク、 **[here]\(こちら\)** を選択して、テストを完了します。 これで、テストのパフォーマンス結果が表示されます。 この例では、下に示すように、NetX Duo ターゲットでの UDP 受信パフォーマンスは 95 Mbps でした。

![UDP 受信テストの結果](media/picture8.jpg)

## <a name="running-the-tcp-transmit-test"></a>TCP 送信テストの実行

TCP 送信テストでは、ホストへの NetX Duo TCP 送信のパフォーマンスが確認されます。 このテストでは、NetX Duo ターゲットはクライアントで、Jperf ホストはサーバーです。 まず、Jperf IDE で **[Server]\(サーバー\)** と **[TCP]** を選択します。 次に、 **[Run IPerf!]\(IPerf を実行\)** を選択し、 下に示すように Iperf サーバーを開始します。

![TCP 送信テストを実行しています。](media/picture9.jpg)

ここで、NetX Duo Iperf デモンストレーションの Web ページから **[Start TCP Transmit Test]\(TCP 送信テストを開始\)** ボタンを選択して、テストを開始します。 下に示すように、Jperf IDE のパフォーマンス統計と更新された NetX Duo Iperf デモンストレーションの Web ページが表示されるようになったはずです。

![TCP 送信テストの統計。](media/picture10.jpg)

NetX Duo Iperf デモンストレーションの Web ページにあるリンク、***[here]\(こちら\)*** を選択して、テストを完了します。 これで、テストのパフォーマンス結果が表示されます。 この例では、下に示すように、NetX Duo ターゲットでの TCP 送信パフォーマンスは 91 Mbps でした。

![TCP 送信テストの結果。](media/picture11.jpg)

## <a name="running-the-tcp-receive-test"></a>TCP 受信テストの実行

TCP 受信テストでは、NetX Duo ターゲットでの NetX Duo TCP 受信のパフォーマンスが確認されます。 このテストでは、NetX Duo ターゲットはサーバーで、Jperf ホストはクライアントです。 まず、Jperf IDE で **[Client]\(クライアント\)** と **[TCP]** を選択します。 次に、次に示すように、NetX Duo の Web ページで **[Start TCP Receive Test]\(TCP 受信テストを開始\)** を選択します。

![TCP 受信テストの実行](media/picture12.jpg)

次に、 **[Run IPerf!]\(IPerf を実行\)** を Jperf IDE から選択し、下に示すように Jperf IDE で統計を確認します。

![TCP 受信テストの統計。](media/picture13.jpg)

NetX Duo Iperf デモンストレーションの Web ページにあるリンク、***[here]\(こちら\)*** を選択して、テストを完了します。 これで、テストのパフォーマンス結果が表示されます。 この例では、下に示すように、NetX Duo ターゲットでの TCP 受信パフォーマンスは 71 Mbps でした。

![TCP 受信テストの結果。](media/picture14.jpg)
