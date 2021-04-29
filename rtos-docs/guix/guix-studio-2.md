---
title: GUIX Studio のインストールと使用
description: この章では、GUIX Studio UI システム デザイン ツールのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d7b5f94c26842b408ea1b00aeeb78e111bea3623
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811984"
---
# <a name="chapter-2-installation-and-use-of-guix-studio"></a>第 2 章: GUIX Studio のインストールと使用

この章では、GUIX Studio UI システム デザイン ツールのインストール、セットアップ、使用に関連するさまざまな問題について説明します。 

## <a name="product-distribution"></a>製品の配布

GUIX Studio アプリを [Microsoft App Store](https://microsoft.com/store/apps) から入手するには、GUIX Studio を検索するか、[GUIX Studio ページ](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab)に直接移動します。 次に、以下を実行します。

1. アプリ ストアの GUIX Studio ページで、 **[入手]** または **[インストール]** ボタンをクリックして、GUIX Studio をダウンロードします。

1. 次の図に示すように、お使いのブラウザーに、Microsoft Store を開くかどうかを確認するメッセージが表示される場合があります。 表示された場合は、 **[開く]** ボタンを選択します。
![[開く] を選択して、GUIX Studio をインストールします。](./media/guix-studio/open-ms-store.png)

1. インストールが完了したら、 **[起動]** ボタンをクリックします。

1. GUIX Studio を初めて起動するときに、GUIX リポジトリをローカル コンピューターに複製するかどうかを確認するダイアログ ボックスが表示されます。 リポジトリを複製するか、既にリポジトリが複製されている場所をポイントするか、リポジトリを複製しないこと (この場合、1 つのサンプル プロジェクトがコンピューターにインストールされます) を選択できます。
![リポジトリを複製するか、既に複製されているリポジトリをポイントするか、スキップするかを選択します。](./media/guix-studio/clone-repo.png)

> ![!NOTE]
> このダイアログ ボックスに戻るには、GUIX Stuido のメイン メニューの **[構成]** 、次に **[GUIX Repository]\(GUIX リポジトリ\)** を選択します。

起動プロセスが完了すると、GUIX Studio を使用できるようになります。

## <a name="using-guix-studio"></a>GUIX Studio の使用

GUIX Studio は簡単に使用できます。***[スタート]*** ボタンを使用して GUIX Studio を実行するだけです。 この時点で、GUIX Studio UI が表示されます。 これで、GUIX Studio を使用して、埋め込み UI をグラフィカルに作成する準備ができました。 ここから、新しいプロジェクトを作成するか、GUIX サンプル プロジェクトなどの既存のプロジェクトを開きます。

> [!NOTE]
> "**gxp**" という拡張子を持つ GUIX Studio プロジェクト ファイルをダブルクリックすることもできます。これにより、GUIX Studio が自動的に起動され、参照先のプロジェクトが開きます。

## <a name="guix-studio-project-samples"></a>GUIX Studio プロジェクトのサンプル

"***gxp** _" という拡張子が付いた一連のサンプル GUIX Studio プロジェクト ファイルは、インストール環境の "_ *_Samples_**" サブディレクトリにあります。 これらの構築済みのサンプル プロジェクトは、GUIX Studio の使用に慣れるのに役立ちます。

常に存在するプロジェクト ファイルの一例は、ファイル ***samples/demo_guix_simple/guix_simple.gxp** _ です。 このサンプル プロジェクト ファイルは、このドキュメントの "_ *_第 7 章_**" で説明されているように、単純な GUIX UI の定義を示しています。

![GUIX Studio UI のスクリーンショット。](./media/guix-studio/image_10.png)

**図 1**

## <a name="keyboard-shortcuts"></a>キーボード ショートカット

- **Ctrl + N:** 新しいプロジェクト
- **Ctrl + O:** プロジェクトを開く
- **Ctrl + S:** プロジェクトの保存
- **Ctrl + Shift + S:** プロジェクトに名前を付けて保存
- **Alt + F4:** 終了
