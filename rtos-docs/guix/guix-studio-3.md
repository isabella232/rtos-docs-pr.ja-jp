---
title: GUIX Studio の説明
description: この章では、GUIX Studio システム分析ツールについて説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 89bbcd51c22dddef6e420750e8c8805a66344335
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811186"
---
# <a name="chapter-3-description-of-guix-studio"></a><span data-ttu-id="6d47c-103">第 3 章 - GUIX Studio の説明</span><span class="sxs-lookup"><span data-stu-id="6d47c-103">Chapter 3: Description of GUIX Studio</span></span>

<span data-ttu-id="6d47c-104">この章では、GUIX Studio システム分析ツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6d47c-104">This chapter contains a description of the GUIX Studio system analysis tool.</span></span> <span data-ttu-id="6d47c-105">GUI の全体的な機能の説明については、この章をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6d47c-105">A description of the overall functionality of the GUI is found in this chapter.</span></span> 

## <a name="guix-studio-views"></a><span data-ttu-id="6d47c-106">GUIX Studio ビュー</span><span class="sxs-lookup"><span data-stu-id="6d47c-106">GUIX Studio Views</span></span>

<span data-ttu-id="6d47c-107">GUIX Studio UI には、**Toolbar**、_\*_プロジェクト ビュー_\*_、_\*_プロパティ ビュー_\*_、_\*_ターゲット ビュー_\*_、_\*_リソース ビュー_\*_ の 5 つの主な領域があります。</span><span class="sxs-lookup"><span data-stu-id="6d47c-107">There are five principal areas of the GUIX Studio UI, namely the ***Toolbar** _, _*_Project View_*_, _*_Properties View_*_, _*_Target View_*_, and _*_Resource View_\*_.</span></span> <span data-ttu-id="6d47c-108">*_図 2_* は、基本的な GUIX Studio UI を示しています。</span><span class="sxs-lookup"><span data-stu-id="6d47c-108">_ *_Figure 2_*\* shows the basic GUIX Studio UI.</span></span> <span data-ttu-id="6d47c-109">以下のサブセクションでは、各ビューについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="6d47c-109">Each of the views is further discussed in the following sub-sections.</span></span>

![基本的な GUIX Studio UI のスクリーンショット。](./media/guix-studio/image_10.png)

<span data-ttu-id="6d47c-111">**図 2**</span><span class="sxs-lookup"><span data-stu-id="6d47c-111">**Figure 2**</span></span>

### <a name="title"></a><span data-ttu-id="6d47c-112">タイトル</span><span class="sxs-lookup"><span data-stu-id="6d47c-112">Title</span></span>

- <span data-ttu-id="6d47c-113">GUIX Studio 18: 前の *_図 2_* の上部に示されているように、**タイトル** には、GUIX Studio のバージョンと現在開いているプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-113">GUIX Studio 18: The ***Title** _ displays the GUIX Studio version as well as the currently open project, as shown at the top of _ *_Figure 2_** previously.</span></span>

### <a name="toolbar"></a><span data-ttu-id="6d47c-114">ツール バー</span><span class="sxs-lookup"><span data-stu-id="6d47c-114">Toolbar</span></span>

<span data-ttu-id="6d47c-115">*_図 3_* に示されているように、**ツール バー** には、GUIX Studio 開発者が使用できるボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-115">The ***Toolbar** _ shows the buttons available to the GUIX Studio developer, as shown in _*_Figure 3_\*\*.</span></span>

![GUIX Studio ツール バーのスクリーンショット。](./media/guix-studio/image11.jpg)

<span data-ttu-id="6d47c-117">**図 3**</span><span class="sxs-lookup"><span data-stu-id="6d47c-117">**Figure 3**</span></span>

<span data-ttu-id="6d47c-118">ツール バーのボタンは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-118">The toolbar buttons are defined as follows:</span></span>

![[新規] ボタン](./media/guix-studio/new-button.png) <span data-ttu-id="6d47c-120">新しい GUIX Studio プロジェクトを作成します</span><span class="sxs-lookup"><span data-stu-id="6d47c-120">Creates a new GUIX Studio project</span></span>

![開くボタン](./media/guix-studio/open-button.png) <span data-ttu-id="6d47c-122">既存の GUIX Studio プロジェクトを開きます</span><span class="sxs-lookup"><span data-stu-id="6d47c-122">Opens an existing GUIX Studio project</span></span>

![[保存] ボタン](./media/guix-studio/save-button.png) <span data-ttu-id="6d47c-124">プロジェクトを保存します</span><span class="sxs-lookup"><span data-stu-id="6d47c-124">Saves the project</span></span>

![切り取りボタン](./media/guix-studio/cut-button.png) <span data-ttu-id="6d47c-126">選択したウィジェットを切り取ります (子を含む)</span><span class="sxs-lookup"><span data-stu-id="6d47c-126">Cut widget selected, including children</span></span>

![コピー ボタン](./media/guix-studio/copy-button.png) <span data-ttu-id="6d47c-128">選択したウィジェットをコピーします (子を含む)</span><span class="sxs-lookup"><span data-stu-id="6d47c-128">Copy selected widget, including children</span></span>

![貼り付けボタン](./media/guix-studio/paste-button.png) <span data-ttu-id="6d47c-130">ウィジェットと子を貼り付けます</span><span class="sxs-lookup"><span data-stu-id="6d47c-130">Paste widget and children</span></span>

![左揃えボタン](./media/guix-studio/left-align-button.png) <span data-ttu-id="6d47c-132">選択したウィジェットを左揃えにします</span><span class="sxs-lookup"><span data-stu-id="6d47c-132">Left-align selected widgets</span></span>

![右揃えボタン](./media/guix-studio/right-align-button.png) <span data-ttu-id="6d47c-134">選択したウィジェットを右揃えにします</span><span class="sxs-lookup"><span data-stu-id="6d47c-134">Right-align selected widgets</span></span>

![上揃えボタン](./media/guix-studio/top-align-button.png) <span data-ttu-id="6d47c-136">選択したウィジェットを上揃えにします</span><span class="sxs-lookup"><span data-stu-id="6d47c-136">Top-align selected widgets</span></span>

![下揃えボタン](./media/guix-studio/bottom-align-button.png) <span data-ttu-id="6d47c-138">選択したウィジェットを下揃えにします</span><span class="sxs-lookup"><span data-stu-id="6d47c-138">Bottom-align selected widgets</span></span>

![縦方向の間隔ボタン](./media/guix-studio/space-vertically-button.png) <span data-ttu-id="6d47c-140">選択したウィジェットの縦方向の間隔を均等にします</span><span class="sxs-lookup"><span data-stu-id="6d47c-140">Equally space selected widgets vertically</span></span>

![横方向の間隔ボタン](./media/guix-studio/space-horizontally-button.png) <span data-ttu-id="6d47c-142">選択したウィジェットの横方向の間隔を均等にします</span><span class="sxs-lookup"><span data-stu-id="6d47c-142">Equally space selected widgets horizontally</span></span>

![幅揃えボタン](./media/guix-studio/equal-width-button.png) <span data-ttu-id="6d47c-144">選択したウィジェットの幅を均等にします</span><span class="sxs-lookup"><span data-stu-id="6d47c-144">Make selected widgets equal width</span></span>

![高さ揃えボタン](./media/guix-studio/equal-height-button.png) <span data-ttu-id="6d47c-146">選択したウィジェットの高さを均等にします</span><span class="sxs-lookup"><span data-stu-id="6d47c-146">Make selected widgets equal height</span></span>

![前面へ移動ボタン](./media/guix-studio/move-front-button.png) <span data-ttu-id="6d47c-148">選択したウィジェットを前面に移動します</span><span class="sxs-lookup"><span data-stu-id="6d47c-148">Move selected widgets to front</span></span>

![背面へ移動ボタン](./media/guix-studio/move-back-button.png) <span data-ttu-id="6d47c-150">選択したウィジェットを背面に移動します</span><span class="sxs-lookup"><span data-stu-id="6d47c-150">Move selected widgets to back</span></span>

![サイズ設定ボタン](./media/guix-studio/size-button.png) <span data-ttu-id="6d47c-152">選択したウィジェットのサイズをコンテンツに合わせます</span><span class="sxs-lookup"><span data-stu-id="6d47c-152">Size selected widget to content Zoom out target screen</span></span>

![縮小ボタン](./media/guix-studio/zoom-out-button.png) <span data-ttu-id="6d47c-154">ターゲット スクリーンを縮小します</span><span class="sxs-lookup"><span data-stu-id="6d47c-154">Zoom out target screen</span></span>

![拡大ボタン](./media/guix-studio/zoom-in-button.png) <span data-ttu-id="6d47c-156">ターゲット スクリーンを拡大します</span><span class="sxs-lookup"><span data-stu-id="6d47c-156">Zoom in target screen</span></span>

![[録画] ボタン](./media/guix-studio/record-button.png) <span data-ttu-id="6d47c-158">マクロを記録します</span><span class="sxs-lookup"><span data-stu-id="6d47c-158">Record Macro</span></span>

![再生ボタン](./media/guix-studio/playback-button.png) <span data-ttu-id="6d47c-160">マクロを再生します</span><span class="sxs-lookup"><span data-stu-id="6d47c-160">Playback Macro</span></span>

![[実行] ボタン](./media/guix-studio/run-button.png) <span data-ttu-id="6d47c-162">アプリケーションを実行します</span><span class="sxs-lookup"><span data-stu-id="6d47c-162">Run Application</span></span>

![バージョン情報ボタン](./media/guix-studio/about-button.png) <span data-ttu-id="6d47c-164">GUIX Studio について</span><span class="sxs-lookup"><span data-stu-id="6d47c-164">About GUIX Studio</span></span>

### <a name="project-view"></a><span data-ttu-id="6d47c-165">[Project View (プロジェクト ビュー)]</span><span class="sxs-lookup"><span data-stu-id="6d47c-165">Project View</span></span>

<span data-ttu-id="6d47c-166">**プロジェクト ビュー** には、埋め込み UI を構成する階層リスト GUIX オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-166">The \***Project View** _ shows the hierarchical list GUIX objects that comprise the embedded UI.</span></span> <span data-ttu-id="6d47c-167">新しい GUIX オブジェクトを追加するには、親オブジェクトをクリックし、_\*_[挿入]_\*_ メニューからオブジェクトを選択します (または、オブジェクトを右クリックして右クリック メニューから選択します)。</span><span class="sxs-lookup"><span data-stu-id="6d47c-167">New GUIX objects can be added by clicking on the parent object and then selecting an object from the _*_Insert_*_ menu (or by right-clicking on the object and selecting from the right-click menu).</span></span> <span data-ttu-id="6d47c-168">以下の _\*_図 4_*_ は、GUIX Studio の*_プロジェクト ビュー_\*を示しています。</span><span class="sxs-lookup"><span data-stu-id="6d47c-168">_*_Figure 4_*_ below shows the GUIX Studio _\*_Project View_\*\*.</span></span>

![GUIX Studio プロジェクト ビューのスクリーンショット。](./media/guix-studio/image_35.png)

<span data-ttu-id="6d47c-170">**図 4**</span><span class="sxs-lookup"><span data-stu-id="6d47c-170">**Figure 4**</span></span>

### <a name="properties-view"></a><span data-ttu-id="6d47c-171">プロパティ ビュー</span><span class="sxs-lookup"><span data-stu-id="6d47c-171">Properties View</span></span>

<span data-ttu-id="6d47c-172">**プロパティ ビュー** には、現在選択されている GUIX オブジェクトの詳細なプロパティ情報が表示されます。これを選択するには、_\*_プロジェクト ビュー_\*_ を使用するか、_\*_ターゲット ビュー_\*_ 内でオブジェクトを直接クリックします。</span><span class="sxs-lookup"><span data-stu-id="6d47c-172">The ***Properties View** _ shows detailed property information of the currently selected GUIX object, which can be selected via the _*_Project View_*_ or by clicking directly on the object in the _*_Target View_\*_.</span></span> <span data-ttu-id="6d47c-173">以下の _\*_図 5_*_ は、GUIX Studio の*_プロパティ ビュー_\*を示しています。</span><span class="sxs-lookup"><span data-stu-id="6d47c-173">_*_Figure 5_*_ below shows the GUIX Studio _\*_Properties View_\*\*.</span></span>

![GUIX Studio のプロパティ ビューのスクリーンショット。](./media/guix-studio/image36.jpg)

<span data-ttu-id="6d47c-175">**図 5**</span><span class="sxs-lookup"><span data-stu-id="6d47c-175">**Figure 5**</span></span>

### <a name="target-view"></a><span data-ttu-id="6d47c-176">ターゲット ビュー</span><span class="sxs-lookup"><span data-stu-id="6d47c-176">Target View</span></span>

<span data-ttu-id="6d47c-177">**ターゲット ビュー** は、WYSIWYG スクリーンのデザインおよびレイアウト領域です。</span><span class="sxs-lookup"><span data-stu-id="6d47c-177">The \***Target View** _ is the WYSIWYG screen design and layout area.</span></span> <span data-ttu-id="6d47c-178">このビューの目的は、ターゲット ハードウェア上で使用可能な物理ディスプレイを表すことです。</span><span class="sxs-lookup"><span data-stu-id="6d47c-178">This view is meant to represent the physical display or displays available on your target hardware.</span></span> <span data-ttu-id="6d47c-179">簡単なマウス操作で、オブジェクトの選択、移動、サイズ変更などを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-179">Objects can be selected, moved, resized, etc. via simple mouse operations.</span></span> <span data-ttu-id="6d47c-180">また、配置ボタンと Z オーダー ボタンの操作は、ターゲット ビュー内の選択したオブジェクト上で利用できます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-180">In addition, alignment and Z-order button operations are available on selected objects in the Target View.</span></span> <span data-ttu-id="6d47c-181">_\*_ターゲット ビュー_\*_ でオブジェクトを選択すると、そのオブジェクトのプロパティが _\*_プロパティ ビュー_\*_ に表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-181">Selecting an object in the _*_Target View_*_ will also result in the properties for that object to be displayed in the _*_Properties View_*_.</span></span> <span data-ttu-id="6d47c-182">以下の _\*_図 6_*_ は、GUIX Studio の*_ターゲット ビュー_\*を示しています。</span><span class="sxs-lookup"><span data-stu-id="6d47c-182">_*_Figure 6_*_ below shows the GUIX Studio _\*_Target View_\*\*.</span></span>

![GUIX Studio ターゲット ビューのスクリーンショット。](./media/guix-studio/image_37.png)

<span data-ttu-id="6d47c-184">**図 6**</span><span class="sxs-lookup"><span data-stu-id="6d47c-184">**Figure 6**</span></span>

### <a name="resource-view"></a><span data-ttu-id="6d47c-185">リソース ビュー</span><span class="sxs-lookup"><span data-stu-id="6d47c-185">Resource View</span></span>

<span data-ttu-id="6d47c-186">**リソース ビュー** は、各ディスプレイに対して定義されているアプリケーション スクリーンで使用できるリソース (色、フォント、ピクセルマップ、および文字列) の管理に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-186">The \***Resource View** _ is used to manage the resources (colors, fonts, pixelmaps, and strings) available to applications screens defined for each display.</span></span> <span data-ttu-id="6d47c-187">リソース ビュー グループのヘッダーをクリックすると、各グループを展開し、グループのコンテンツを確認できます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-187">You can click on the resource view group headers to expand each group and examine the group contents.</span></span> <span data-ttu-id="6d47c-188">以下の _\*_図 7_*_ は、GUIX Studio の*_リソース ビュー_\*を示しています。</span><span class="sxs-lookup"><span data-stu-id="6d47c-188">_*_Figure 7_*_ below shows the GUIX Studio _\*_Resource View_\*\*.</span></span>

![GUIX Studio リソース ビューのスクリーンショット。](./media/guix-studio/image38.jpg)

<span data-ttu-id="6d47c-190">**図 7**</span><span class="sxs-lookup"><span data-stu-id="6d47c-190">**Figure 7**</span></span>

<span data-ttu-id="6d47c-191">リソース グループのタイトルは、現在のテーマの名前を示します。</span><span class="sxs-lookup"><span data-stu-id="6d47c-191">The title of the resource groups indicates current theme name.</span></span> <span data-ttu-id="6d47c-192">複数のテーマを使用できる場合は、上矢印または下矢印をクリックすると、テーマを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-192">If multi themes available, you are able to switch between themes by clicking on the up and down arrow.</span></span>

<span data-ttu-id="6d47c-193">上のビューの各リソース グループを展開するか折りたたむには、そのグループのヘッダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d47c-193">Each resource group in the view above can be expanded or collapsed by clicking on the group header.</span></span> <span data-ttu-id="6d47c-194">各リソース グループの詳細については、次の章をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6d47c-194">A more detailed description of each resource groups follows in the next chapter.</span></span>

## <a name="the-guix-studio-project"></a><span data-ttu-id="6d47c-195">GUIX Studio プロジェクト</span><span class="sxs-lookup"><span data-stu-id="6d47c-195">The GUIX Studio Project</span></span>

<span data-ttu-id="6d47c-196">GUIX Studio プロジェクトには、お使いの UI スクリーンのデザインおよび UI リソースに関する情報が保持されます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-196">A GUIX Studio project maintains information about your UI screen design and UI resources.</span></span> <span data-ttu-id="6d47c-197">プロジェクト データは、拡張子が ".***gxp***" の XML 形式ファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-197">The project data is saved to an XML format file with the extension ".***gxp***".</span></span> <span data-ttu-id="6d47c-198">プロジェクト ファイルは XML スキーマ ファイルであるため、バージョン コントロールが可能で、他のソース ファイルと同じように共有できます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-198">Since the project file is an XML schema file, it can be versioned controlled and shared similar to any other source file.</span></span>

<span data-ttu-id="6d47c-199">最初に GUIX Studio の使用を開始するときに、配布物と共に提供されるサンプル プロジェクトのいずれかを開くか、新しいプロジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d47c-199">When you first start using GUIX Studio, you will need to either open one of the example projects provided with the distribution or create a new project.</span></span> <span data-ttu-id="6d47c-200">すべての作業がプロジェクト データ ファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-200">All of your work is saved to the project data file.</span></span>

<span data-ttu-id="6d47c-201">GUIX Studio によって、ANSI C ソース ファイルも生成されます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-201">GUIX Studio also produces ANSI C source files.</span></span> <span data-ttu-id="6d47c-202">これらのソース ファイルには、アプリケーション リソース、またはデザインされたご自身のスクリーンを記述するデータ構造が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6d47c-202">These source files contain either your application resources or data structures describing your designed screens.</span></span> <span data-ttu-id="6d47c-203">また、GUIX Studio は、これらの生成されたソース ファイルに API 関数も書き込みます。これは、生成されたデータ構造を使用して、アプリケーション スクリーンを動的に作成することがわかっています。</span><span class="sxs-lookup"><span data-stu-id="6d47c-203">GUIX Studio also writes to these generated source files API functions that know to utilize the generated data structures to dynamically create your application screens.</span></span> <span data-ttu-id="6d47c-204">お使いのアプリケーション ソフトウェアは、提供された API 関数を呼び出すだけで、GUIX Studio 内でデザインしたスクリーンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-204">Your application software will simply invoke the provided API functions to create the screens you have designed within GUIX Studio.</span></span>

<span data-ttu-id="6d47c-205">ご自身のユーザー インターフェイスをデザインしているときは、GUIX Studio を定期的に使用して、デザインしたインターフェイスをビルドして実行できる GUIX 互換出力ファイルを生成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6d47c-205">As you progress in designing your user interface, you will periodically want to use GUIX Studio to generate the GUIX compatible output files that will allow you to build and run the interface you have designed.</span></span> <span data-ttu-id="6d47c-206">生成したソース ファイルは、ご自身のターゲット ハードウェアに対して、または ThreadX と GUIX をシミュレートする Windows デスクトップ上でコンパイルし、実行できます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-206">You can compile and run the generated source files for either your target hardware or on your Windows desktop that simulates ThreadX and GUIX.</span></span>

## <a name="guix-studio-project-organization"></a><span data-ttu-id="6d47c-207">GUIX Studio プロジェクトの編成</span><span class="sxs-lookup"><span data-stu-id="6d47c-207">GUIX Studio Project Organization</span></span>

<span data-ttu-id="6d47c-208">GUIX Studio を効果的に使用する方法と、GUIX Studio IDE のプロジェクト ビュー内に表示される情報を理解するには、GUIX Studio プロジェクトの基本的な編成に関する知識があると役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-208">It is helpful to have some knowledge of the basic organization of a GUIX Studio project to understand how to use GUIX Studio effectively and to understand the information presented in the Project View of the GUIX Studio IDE.</span></span> <span data-ttu-id="6d47c-209">プロジェクト ビューは、ご自身のプロジェクト内に含まれているすべての情報の概要を視覚的に表したものです。</span><span class="sxs-lookup"><span data-stu-id="6d47c-209">The Project View is a summary visual representation of all of the information contained in your project.</span></span>

<span data-ttu-id="6d47c-210">プロジェクトについて説明する前に、いくつかの用語を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d47c-210">Before describing the project, it is necessary to define few terms.</span></span> <span data-ttu-id="6d47c-211">まずは **ディスプレイ** という用語です。これは物理ディスプレイ デバイスを表します。</span><span class="sxs-lookup"><span data-stu-id="6d47c-211">First, we use the term **Display** to mean a physical display device.</span></span> <span data-ttu-id="6d47c-212">ほとんどの場合、LCD ディスプレイ デバイスですが、他のテクノロジを使用している可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="6d47c-212">This is most often an LCD display device but it could be using other technology.</span></span> <span data-ttu-id="6d47c-213">次の用語は **スクリーン** です。これはトップレベルの GUIX オブジェクトで、通常は GUIX ウィンドウと、関連付けられているすべての子要素を意味します。</span><span class="sxs-lookup"><span data-stu-id="6d47c-213">The next term is **Screen**, which mean a top-level GUIX object, usually a GUIX Window, and all of its associated child elements.</span></span> <span data-ttu-id="6d47c-214">スクリーンは、実行時に定義および変更できるソフトウェア コンストラクトです。</span><span class="sxs-lookup"><span data-stu-id="6d47c-214">A Screen is a software construct that can be defined and modified at runtime.</span></span> <span data-ttu-id="6d47c-215">最後の **テーマ** はリソースのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="6d47c-215">Finally, a **Theme** is a collection of resources.</span></span> <span data-ttu-id="6d47c-216">テーマには、色の定義、フォント定義、およびピクセルマップ定義の表が含まれており、これらは連携してエンド ユーザーに一貫した外観を提供するよう設計されています。</span><span class="sxs-lookup"><span data-stu-id="6d47c-216">A theme includes a table of color definitions, font definitions, and pixelmap definitions that are designed to work well together and present your end user with a consistent look and feel.</span></span>

<span data-ttu-id="6d47c-217">最初のプロジェクトには、プロジェクト名、サポートされているディスプレイ数、各ディスプレイの解像度と色形式、サポートされる言語の数、サポートされている各言語の名前など、一連のグローバル情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6d47c-217">The project first includes a set of global information such as the project name, number of displays supported, the resolution and color format of each display, the number of languages supported, the name of each supported language.</span></span> <span data-ttu-id="6d47c-218">プロジェクト名は、プロジェクト ビュー内に表示される最初のノードです。</span><span class="sxs-lookup"><span data-stu-id="6d47c-218">The project name is the first node displayed in the Project View.</span></span>

<span data-ttu-id="6d47c-219">次のプロジェクトには、最大 4 つの物理ディスプレイに必要なすべての情報と、各ディスプレイで使用できるスクリーンとリソースが整理されています。</span><span class="sxs-lookup"><span data-stu-id="6d47c-219">The project next organizes all of the information required for up to 4 physical displays and the screens and resources available to each display.</span></span> <span data-ttu-id="6d47c-220">ディスプレイ名は、プロジェクト ビュー ツリー内の次のレベルのノードです。</span><span class="sxs-lookup"><span data-stu-id="6d47c-220">The display names are the next level nodes in the Project View tree.</span></span>

<span data-ttu-id="6d47c-221">GUIX Studio アプリケーションの固有の機能には複数の物理ディスプレイに対するサポートが組み込まれており、それぞれ独自の x/y 解像度、色の形式、スクリーン、およびリソースがあります。</span><span class="sxs-lookup"><span data-stu-id="6d47c-221">A unique feature of the GUIX Studio application is built-in support for multiple physical displays, each with its own x,y resolution, color format, screens, and resources.</span></span> <span data-ttu-id="6d47c-222">大部分の GUIX アプリケーションが 1 つの物理ディスプレイしか利用できませんが、複数の同時物理ディスプレイをサポートする必要がある製品を作成する場合は、この機能が重要です。</span><span class="sxs-lookup"><span data-stu-id="6d47c-222">While the vast majority of GUIX applications utilize only one physical display, this capability is important for those making a product that must support multiple simultaneous physical displays.</span></span>

<span data-ttu-id="6d47c-223">各ディスプレイ定義の下に、そのディスプレイに対して定義されているトップレベルのウィンドウまたはスクリーンがあります。</span><span class="sxs-lookup"><span data-stu-id="6d47c-223">Beneath each display definition are the top-level windows or screens defined for that display.</span></span> <span data-ttu-id="6d47c-224">スクリーン定義は、各スクリーン上の子ウィジェットの数と入れ子に応じて、任意のレベルまで入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-224">The screen definitions can be nested to any level depending on the number and nesting of child widgets on each screen.</span></span>

<span data-ttu-id="6d47c-225">このスクリーンと子ウィジェットの編成は、プロジェクト ビュー内にグラフィカルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-225">This screen and child widget organization is displayed in a graphical manner in the Project View.</span></span>

<span data-ttu-id="6d47c-226">各ディスプレイに関連付けられているテーマは、各テーマを構成するディスプレイおよびリソースのコンテンツによってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-226">Also associated with each display are the Themes supported by the display and the resource content composing each Theme.</span></span> <span data-ttu-id="6d47c-227">ご自身のプロジェクトに複数のディスプレイが含まれている場合、1 つのディスプレイを選択してから別のディスプレイを選択すると、リソース ビューのコンテンツが変更されることがわかります。</span><span class="sxs-lookup"><span data-stu-id="6d47c-227">If your project includes multiple displays, you will notice that the Resource View changes its content when you select one display and then another.</span></span> <span data-ttu-id="6d47c-228">これは、リソースのコンテンツが各ディスプレイにリンクされているためです。</span><span class="sxs-lookup"><span data-stu-id="6d47c-228">This is because the resource content is linked to each display.</span></span> <span data-ttu-id="6d47c-229">色形式だけでなく、使用するように選択したピクセルマップ、色、およびフォントも、物理ディスプレイによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6d47c-229">Not only the color format may be different, but the pixelmaps, colors, and fonts you choose to use may vary from one physical display to another.</span></span>

<span data-ttu-id="6d47c-230">プロジェクトによって管理される最後のコンポーネントは、各ディスプレイに関連付けられている文字列テーブル データです。</span><span class="sxs-lookup"><span data-stu-id="6d47c-230">The final component maintained by the project is the string table data associated with each display.</span></span> <span data-ttu-id="6d47c-231">ディスプレイの x/y 解像度は大きく異なるため、文字列データは、プロジェクト内で定義されているディスプレイごとに個別に保持されます。</span><span class="sxs-lookup"><span data-stu-id="6d47c-231">Since displays can be of very different x,y resolutions, the string data is maintained independently for each display defined in the project.</span></span>
