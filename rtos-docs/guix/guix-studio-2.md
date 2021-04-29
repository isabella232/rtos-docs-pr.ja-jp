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
# <a name="chapter-2-installation-and-use-of-guix-studio"></a><span data-ttu-id="603db-103">第 2 章: GUIX Studio のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="603db-103">Chapter 2: Installation and Use of GUIX Studio</span></span>

<span data-ttu-id="603db-104">この章では、GUIX Studio UI システム デザイン ツールのインストール、セットアップ、使用に関連するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="603db-104">This chapter contains a description of various issues related to installation, setup, and usage of the GUIX Studio UI system design tool.</span></span> 

## <a name="product-distribution"></a><span data-ttu-id="603db-105">製品の配布</span><span class="sxs-lookup"><span data-stu-id="603db-105">Product Distribution</span></span>

<span data-ttu-id="603db-106">GUIX Studio アプリを [Microsoft App Store](https://microsoft.com/store/apps) から入手するには、GUIX Studio を検索するか、[GUIX Studio ページ](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab)に直接移動します。</span><span class="sxs-lookup"><span data-stu-id="603db-106">You can obtain the GUIX Studio app from the [Microsoft App Store](https://microsoft.com/store/apps) by searching for GUIX Studio, or by going directly to [the GUIX Studio page](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab).</span></span> <span data-ttu-id="603db-107">次に、以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="603db-107">Then do the following.</span></span>

1. <span data-ttu-id="603db-108">アプリ ストアの GUIX Studio ページで、 **[入手]** または **[インストール]** ボタンをクリックして、GUIX Studio をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="603db-108">From the GUIX Studio page in the App Store, click the **Get** or **Install** button to download GUIX Studio.</span></span>

1. <span data-ttu-id="603db-109">次の図に示すように、お使いのブラウザーに、Microsoft Store を開くかどうかを確認するメッセージが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="603db-109">Your browser may display a message asking if you want to open the Microsoft Store, as shown in the figure below.</span></span> <span data-ttu-id="603db-110">表示された場合は、 **[開く]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="603db-110">If it does, choose the **Open** button.</span></span>
<span data-ttu-id="603db-111">![[開く] を選択して、GUIX Studio をインストールします。](./media/guix-studio/open-ms-store.png)</span><span class="sxs-lookup"><span data-stu-id="603db-111">![Choose Open to install GUIX Studio.](./media/guix-studio/open-ms-store.png)</span></span>

1. <span data-ttu-id="603db-112">インストールが完了したら、 **[起動]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="603db-112">When the install finishes, choose the **Launch** button.</span></span>

1. <span data-ttu-id="603db-113">GUIX Studio を初めて起動するときに、GUIX リポジトリをローカル コンピューターに複製するかどうかを確認するダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="603db-113">The first time that GUIX Studio launches, it displays a dialog box asking if you want to clone the GUIX repo to your local computer.</span></span> <span data-ttu-id="603db-114">リポジトリを複製するか、既にリポジトリが複製されている場所をポイントするか、リポジトリを複製しないこと (この場合、1 つのサンプル プロジェクトがコンピューターにインストールされます) を選択できます。</span><span class="sxs-lookup"><span data-stu-id="603db-114">You can either choose to clone the repository, point to where you have already cloned the repo, or choose not to clone the repo at all (in which case, one example project is installed on your computer).</span></span>
<span data-ttu-id="603db-115">![リポジトリを複製するか、既に複製されているリポジトリをポイントするか、スキップするかを選択します。](./media/guix-studio/clone-repo.png)</span><span class="sxs-lookup"><span data-stu-id="603db-115">![Choose to clone the repo, point to an already-cloned repo, or skip.](./media/guix-studio/clone-repo.png)</span></span>

> <span data-ttu-id="603db-116">!</span><span class="sxs-lookup"><span data-stu-id="603db-116">!</span></span>[!NOTE]
> <span data-ttu-id="603db-117">このダイアログ ボックスに戻るには、GUIX Stuido のメイン メニューの **[構成]** 、次に **[GUIX Repository]\(GUIX リポジトリ\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="603db-117">You can return to this dialog box at any time by choosing **Configure** from the main menu of GUIX Stuido, followed by **GUIX Repository**.</span></span>

<span data-ttu-id="603db-118">起動プロセスが完了すると、GUIX Studio を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="603db-118">After the startup process is finished, you will be ready to use GUIX Studio.</span></span>

## <a name="using-guix-studio"></a><span data-ttu-id="603db-119">GUIX Studio の使用</span><span class="sxs-lookup"><span data-stu-id="603db-119">Using GUIX Studio</span></span>

<span data-ttu-id="603db-120">GUIX Studio は簡単に使用できます。***[スタート]*** ボタンを使用して GUIX Studio を実行するだけです。</span><span class="sxs-lookup"><span data-stu-id="603db-120">Using GUIX Studio is easy - simply run GUIX Studio via the "***Start***" button.</span></span> <span data-ttu-id="603db-121">この時点で、GUIX Studio UI が表示されます。</span><span class="sxs-lookup"><span data-stu-id="603db-121">At this point you will observe the GUIX Studio UI.</span></span> <span data-ttu-id="603db-122">これで、GUIX Studio を使用して、埋め込み UI をグラフィカルに作成する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="603db-122">You are now ready to use GUIX Studio to graphically create your embedded UI.</span></span> <span data-ttu-id="603db-123">ここから、新しいプロジェクトを作成するか、GUIX サンプル プロジェクトなどの既存のプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="603db-123">From here you create a new project or open an existing project, including the GUIX example projects.</span></span>

> [!NOTE]
> <span data-ttu-id="603db-124">"**gxp**" という拡張子を持つ GUIX Studio プロジェクト ファイルをダブルクリックすることもできます。これにより、GUIX Studio が自動的に起動され、参照先のプロジェクトが開きます。</span><span class="sxs-lookup"><span data-stu-id="603db-124">You can also double-click on any GUIX Studio project file with an extension of "**gxp,**" which will automatically launch GUIX Studio and open the referenced project.</span></span>

## <a name="guix-studio-project-samples"></a><span data-ttu-id="603db-125">GUIX Studio プロジェクトのサンプル</span><span class="sxs-lookup"><span data-stu-id="603db-125">GUIX Studio Project Samples</span></span>

<span data-ttu-id="603db-126">"\***gxp** _" という拡張子が付いた一連のサンプル GUIX Studio プロジェクト ファイルは、インストール環境の "_ \*_Samples_\*\*" サブディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="603db-126">A series of example GUIX Studio project files with the extension "\***gxp**_" are found in the "_\*_Samples_\*\*" sub-directory of your installation.</span></span> <span data-ttu-id="603db-127">これらの構築済みのサンプル プロジェクトは、GUIX Studio の使用に慣れるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="603db-127">These pre-built example projects will help you get comfortable with using GUIX Studio.</span></span>

<span data-ttu-id="603db-128">常に存在するプロジェクト ファイルの一例は、ファイル \***samples/demo_guix_simple/guix_simple.gxp** _ です。</span><span class="sxs-lookup"><span data-stu-id="603db-128">One example project file that is always present is the file \***samples/demo_guix_simple/guix_simple.gxp** _.</span></span> <span data-ttu-id="603db-129">このサンプル プロジェクト ファイルは、このドキュメントの "_ \*_第 7 章_\*\*" で説明されているように、単純な GUIX UI の定義を示しています。</span><span class="sxs-lookup"><span data-stu-id="603db-129">This example project file shows the definition of a simple GUIX UI, as described in _ *_Chapter 7_*\* of this document.</span></span>

![GUIX Studio UI のスクリーンショット。](./media/guix-studio/image_10.png)

<span data-ttu-id="603db-131">**図 1**</span><span class="sxs-lookup"><span data-stu-id="603db-131">**Figure 1**</span></span>

## <a name="keyboard-shortcuts"></a><span data-ttu-id="603db-132">キーボード ショートカット</span><span class="sxs-lookup"><span data-stu-id="603db-132">Keyboard Shortcuts</span></span>

- <span data-ttu-id="603db-133">**Ctrl + N:** 新しいプロジェクト</span><span class="sxs-lookup"><span data-stu-id="603db-133">**Ctrl + N:** New Project</span></span>
- <span data-ttu-id="603db-134">**Ctrl + O:** プロジェクトを開く</span><span class="sxs-lookup"><span data-stu-id="603db-134">**Ctrl + O:** Open Project</span></span>
- <span data-ttu-id="603db-135">**Ctrl + S:** プロジェクトの保存</span><span class="sxs-lookup"><span data-stu-id="603db-135">**Ctrl + S:** Save Project</span></span>
- <span data-ttu-id="603db-136">**Ctrl + Shift + S:** プロジェクトに名前を付けて保存</span><span class="sxs-lookup"><span data-stu-id="603db-136">**Ctrl + Shift + S:** Save Project As</span></span>
- <span data-ttu-id="603db-137">**Alt + F4:** 終了</span><span class="sxs-lookup"><span data-stu-id="603db-137">**Alt + F4:** Exit</span></span>
