---
title: 第 2 章 - Azure RTOS TraceX のインストールと使用
description: この章では、Azure RTOS TraceX システム分析ツールのインストール、セットアップ、および使用に関連するさまざまな問題について説明します。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 05d7fe3df38c7e8a3480c8ea0d4922a109de9ede
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812389"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-tracex"></a><span data-ttu-id="3159c-103">第 2 章 - Azure RTOS TraceX のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="3159c-103">Chapter 2 - Installation and use of Azure RTOS TraceX</span></span>

<span data-ttu-id="3159c-104">この章では、Azure RTOS TraceX システム分析ツールのインストール、セットアップ、および使用に関連するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="3159c-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS TraceX system analysis tool.</span></span> 

## <a name="product-distribution"></a><span data-ttu-id="3159c-105">製品の配布</span><span class="sxs-lookup"><span data-stu-id="3159c-105">Product Distribution</span></span>

<span data-ttu-id="3159c-106">TraceX アプリを入手するには、[Microsoft App Store](https://microsoft.com/store/apps) で TraceX アプリを検索するか、[TraceX ページ](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab)に直接移動します。</span><span class="sxs-lookup"><span data-stu-id="3159c-106">You can obtain the TraceX app from the [Microsoft App Store](https://microsoft.com/store/apps) by searching for TraceX, or by going directly to [the TraceX page](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab).</span></span> <span data-ttu-id="3159c-107">次に、以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="3159c-107">Then do the following.</span></span>

1. <span data-ttu-id="3159c-108">App Store 内の TraceX ページで、 **[取得]** または **[インストール]** ボタンをクリックして TraceX をインストールします。</span><span class="sxs-lookup"><span data-stu-id="3159c-108">From the TraceX page in the App Store, click the **Get** or **Install** button to install TraceX.</span></span>

1. <span data-ttu-id="3159c-109">次の図に示すように、お使いのブラウザーに、Microsoft Store を開くかどうかを確認するメッセージが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="3159c-109">Your browser may display a message asking if you want to open the Microsoft Store, as shown in the figure below.</span></span> <span data-ttu-id="3159c-110">表示された場合は、 **[開く]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3159c-110">If it does, choose the **Open** button.</span></span>
<span data-ttu-id="3159c-111">![[開く] を選択して TraceX をインストール。](../guix/media/guix-studio/open-ms-store.png)</span><span class="sxs-lookup"><span data-stu-id="3159c-111">![Choose Open to install TraceX.](../guix/media/guix-studio/open-ms-store.png)</span></span>

1. <span data-ttu-id="3159c-112">インストールが完了したら、 **[起動]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3159c-112">When the install finishes, choose the **Launch** button.</span></span> 

## <a name="using-tracex"></a><span data-ttu-id="3159c-113">TraceX の使用</span><span class="sxs-lookup"><span data-stu-id="3159c-113">Using TraceX</span></span>

<span data-ttu-id="3159c-114">TraceX は、TraceX 内でトレース ファイルを開くのと同じくらい簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="3159c-114">Using TraceX is as easy as opening a trace file inside TraceX!</span></span> <span data-ttu-id="3159c-115">**[開始]** ボタンを使用して TraceX を実行します。</span><span class="sxs-lookup"><span data-stu-id="3159c-115">Run TraceX via the \***Start** _ button.</span></span> <span data-ttu-id="3159c-116">この時点で、TraceX グラフィカル ユーザー インターフェイス (GUI) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3159c-116">At this point you will observe the TraceX graphic user interface (GUI).</span></span> <span data-ttu-id="3159c-117">これで、TraceX を使用して、既存のターゲット トレース バッファーをグラフィカルに表示する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="3159c-117">You are now ready to use TraceX to graphically view an existing target trace buffer.</span></span> <span data-ttu-id="3159c-118">これは、*_[ファイル] -> [開く]_* をクリックし、バイナリ トレース ファイルを入力して、簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3159c-118">This is easily done by clicking _ *_File -> Open,_*\* then entering the binary trace file.</span></span>

>[!IMPORTANT]
><span data-ttu-id="3159c-119">*また、拡張子が **trx** のトレース ファイルをダブルクリックすることもできます。これにより、TraceX が自動的に起動します。*</span><span class="sxs-lookup"><span data-stu-id="3159c-119">*You can also double-click on any trace file with an extension of **trx,** which will automatically launch TraceX.*</span></span>

![TraceX GUI のスクリーンショット。](./media/user-guide/screen_shot_8.png)

<span data-ttu-id="3159c-121">**図 1**</span><span class="sxs-lookup"><span data-stu-id="3159c-121">**FIGURE 1**</span></span>

>[!IMPORTANT]
><span data-ttu-id="3159c-122">*ThreadX を使用してターゲット上でトレース バッファーを生成する手順については、\*\*第 5 章*\* をご覧ください。\*</span><span class="sxs-lookup"><span data-stu-id="3159c-122">*Refer to **Chapter 5** for instructions on how to generate trace buffers on the target using ThreadX.*</span></span>

## <a name="tracex-examples"></a><span data-ttu-id="3159c-123">TraceX の例</span><span class="sxs-lookup"><span data-stu-id="3159c-123">TraceX Examples</span></span>

<span data-ttu-id="3159c-124">TraceX アプリケーションを初めて実行するとき、または TraceX アプリケーションの更新時に、TraceX サンプル トレース ファイルと custom_events.trxc ファイルを、ご自身のローカル コンピューター上のユーザー定義ディレクトリにインストールするように求められます。</span><span class="sxs-lookup"><span data-stu-id="3159c-124">The first time you run the TraceX application, or when the TraceX application is updated, you will be prompted to install the TraceX example trace files and the custom_events.trxc file to a user-defined directory on your local machine.</span></span>

<span data-ttu-id="3159c-125">このインストール手順が完了すると、ご自身のインストール フォルダーの **TraceFiles** サブディレクトリ内に、拡張子が **trx** のサンプル トレース ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3159c-125">After this installation step in completed, the example trace files with the extension **trx** are found in the **TraceFiles** subdirectory of your installation folder.</span></span> <span data-ttu-id="3159c-126">事前作成されたこれらのサンプルは、お使いのアプリケーションで実行されている ThreadX によって生成されたトレース バッファー上での TraceX の操作に慣れるうえで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3159c-126">These pre-built examples will help you get comfortable with using TraceX on the trace buffers generated by ThreadX running with your application.</span></span>

<span data-ttu-id="3159c-127">常に存在するサンプル トレース ファイルの 1 つが \***demo_threadx.trx** _ です。</span><span class="sxs-lookup"><span data-stu-id="3159c-127">One example trace file always present is the file \***demo_threadx.trx** _.</span></span> <span data-ttu-id="3159c-128">このサンプル トレース ファイルは、_ThreadX ユーザー ガイド\* の第 6 章で説明されているように、標準の ThreadX デモの実行を示しています。</span><span class="sxs-lookup"><span data-stu-id="3159c-128">This example trace file shows the execution of the standard ThreadX demo, as described in Chapter 6 of the _ThreadX User Guide\*.</span></span>

![TraceX 内の [開く] ダイアログのスクリーンショット。](./media/user-guide/screen_shot_9.png)

<span data-ttu-id="3159c-130">**図 2**</span><span class="sxs-lookup"><span data-stu-id="3159c-130">**FIGURE 2**</span></span>
