---
title: 第 2 章 - Azure RTOS TraceX のインストールと使用
description: この章では、Azure RTOS TraceX システム分析ツールのインストール、セットアップ、および使用に関連するさまざまな問題について説明します。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 1a375975ef80cfb7b56466f5d91ed9a0ca00a20a38108e1b81f4fe8e5d85278d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802195"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-tracex"></a>第 2 章 - Azure RTOS TraceX のインストールと使用

この章では、Azure RTOS TraceX システム分析ツールのインストール、セットアップ、および使用に関連するさまざまな問題について説明します。 

## <a name="product-distribution"></a>製品の配布

TraceX アプリを入手するには、[Microsoft App Store](https://microsoft.com/store/apps) で TraceX アプリを検索するか、[TraceX ページ](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab)に直接移動します。 次に、以下を実行します。

1. App Store 内の TraceX ページで、 **[取得]** または **[インストール]** ボタンをクリックして TraceX をインストールします。

1. 次の図に示すように、お使いのブラウザーに、Microsoft Store を開くかどうかを確認するメッセージが表示される場合があります。 表示された場合は、 **[開く]** ボタンをクリックします。
![[開く] を選択して TraceX をインストール。](../guix/media/guix-studio/open-ms-store.png)

1. インストールが完了したら、 **[起動]** ボタンをクリックします。 

## <a name="using-tracex"></a>TraceX の使用

TraceX は、TraceX 内でトレース ファイルを開くのと同じくらい簡単に使用できます。 **[開始]** ボタンを使用して TraceX を実行します。 この時点で、TraceX グラフィカル ユーザー インターフェイス (GUI) が表示されます。 これで、TraceX を使用して、既存のターゲット トレース バッファーをグラフィカルに表示する準備ができました。 これは、*_[ファイル] -> [開く]_* をクリックし、バイナリ トレース ファイルを入力して、簡単に行うことができます。

>[!IMPORTANT]
>*また、拡張子が **trx** のトレース ファイルをダブルクリックすることもできます。これにより、TraceX が自動的に起動します。*

![TraceX GUI のスクリーンショット。](./media/user-guide/screen_shot_8.png)

**図 1**

>[!IMPORTANT]
>*ThreadX を使用してターゲット上でトレース バッファーを生成する手順については、**第 5 章** をご覧ください。*

## <a name="tracex-examples"></a>TraceX の例

TraceX アプリケーションを初めて実行するとき、または TraceX アプリケーションの更新時に、TraceX サンプル トレース ファイルと custom_events.trxc ファイルを、ご自身のローカル コンピューター上のユーザー定義ディレクトリにインストールするように求められます。

このインストール手順が完了すると、ご自身のインストール フォルダーの **TraceFiles** サブディレクトリ内に、拡張子が **trx** のサンプル トレース ファイルが作成されます。 事前作成されたこれらのサンプルは、お使いのアプリケーションで実行されている ThreadX によって生成されたトレース バッファー上での TraceX の操作に慣れるうえで役立ちます。

常に存在するサンプル トレース ファイルの 1 つが ***demo_threadx.trx** _ です。 このサンプル トレース ファイルは、_ThreadX ユーザー ガイド* の第 6 章で説明されているように、標準の ThreadX デモの実行を示しています。

![TraceX 内の [開く] ダイアログのスクリーンショット。](./media/user-guide/screen_shot_9.png)

**図 2**
