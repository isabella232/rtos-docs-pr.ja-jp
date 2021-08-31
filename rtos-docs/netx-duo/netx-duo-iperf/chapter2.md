---
title: 第 2 章 - Azure RTOS NetX Duo Iperf のインストールと使用
description: この章では、Iperf サンプルをインストールして使用する手順について説明します。
author: v-condav
ms.author: v-condav
ms.date: 08/16/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7e80d89a334ceec3467b23574ab5c231a15f68a1
ms.sourcegitcommit: 4842f4cfe9e31b3ac59059f43e598eb70faebc8f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2021
ms.locfileid: "122609798"
---
# <a name="chapter-2-installation-and-use"></a>第 2 章 - インストールと使用

この章では、NetX Duo Iperf デモンストレーションのインストール、セットアップ、使用に関連するさまざまな問題について説明します。

## <a name="installing-the-demonstration"></a>デモンストレーションのインストール

配布時に提供されているプラットフォーム固有のインストール手順に従ってください。

## <a name="installing-iperf"></a>Iperf のインストール

さまざまな Iperf プログラムを使用できます。 ただし、このドキュメントの例は、インターネット上の複数のソースから入手できる Java ベースの ***Jperf 2.0.2*** に基づいています。

> [注] "*Jperf は、ホスト コンピューターに Java がインストールされている必要があります。* "

## <a name="setting-the-ip-address"></a>IP アドレスの設定

既定では、NetX Duo Iperf デモンストレーションの IP アドレスは **192.2.2.149** に設定されています。 これは、ファイル **_demo_netx_duo_iperf.c_ *_ に、_* _nx_ip_create_** への呼び出しのパラメーターとして設定されます。

## <a name="network-assumptions"></a>ネットワークの前提条件

このデモンストレーションでは、NetX Duo Iperf デモンストレーションを実行している Iperf ホスト コンピューターとターゲット ボードが、100 Mbps の全二重イーサネット スイッチに接続されていることを前提としています。 最高のパフォーマンスを実現するには、テスト ネットワークに他のトラフィックが存在しないようにする必要があります。

また、クロスオーバーのイーサネット ケーブルを使用して、Iperf ホストと NetX Duo ターゲット ボードをバックツーバックで接続することもできます。

## <a name="running-the-demonstration"></a>デモンストレーションの実行

デモンストレーションの実行は簡単です。NetX Duo Iperf デモンストレーション プロジェクト (通常、***demo_netx_duo_iperf*** という名前) を読み込んでビルドし、実行するだけです。

## <a name="browse-to-the-demonstration"></a>デモンストレーションの参照

Iperf ホスト プラットフォームのブラウザーを使用してターゲット ボードを参照します。 ターゲット ボードの IP アドレス **192.2.2.149** を前提として、NetX Duo Iperf デモンストレーションの最初の Web ページの例を次に示します。

![Iperf の最初の Ｗeb ページの例](media/Picture1.jpg)

## <a name="running-jperf"></a>Jperf の実行

Jperf の実行は簡単で、Windows バッチ ファイル ***jperf.bat** _ をダブルクリックするだけです。 これにより、下に示すように Jperf IDE が起動します。 Jperf IDE が表示されたら、NetX Duo Iperf デモンストレーションのターゲット ボードの IP アドレスを _ *[Server Address]* * フィールドに設定する必要があります。 この例では、NetX Duo ターゲット ボードの IP アドレスは **192.2.2.149** です。 また、 **[UDP Bandwidth]\(UDP 帯域幅\)** と **[UDP Packet Size]\(UDP パケット サイズ\)** の各フィールドにも注目してください。 これらには、下に示すように、最適な UDP 受信パフォーマンスを設定する必要があります。

![UDP パフォーマンスの最適化。](media/Picture2.jpg)
