---
title: 第 1 章 - GUIX の概要
description: GUIX は、Azure RTOS ThreadX ベースの埋め込みアプリケーション専用に設計された、(GUI) の高パフォーマンスのリアルタイム実装です。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b90da988a03d59b1bca3f5584164d641bef96454
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812020"
---
# <a name="chapter-1---introduction-to-azure-rtos-guix"></a><span data-ttu-id="3c91f-103">第 1 章 - Azure RTOS GUIX の概要</span><span class="sxs-lookup"><span data-stu-id="3c91f-103">Chapter 1 - Introduction to Azure RTOS GUIX</span></span>

<span data-ttu-id="3c91f-104">Azure RTOS GUIX (GUIX) は、ThreadX ベースの埋め込みアプリケーション専用に設計された、グラフィカル インターフェイス フレームワークの高パフォーマンスのリアルタイム実装です。</span><span class="sxs-lookup"><span data-stu-id="3c91f-104">Azure RTOS GUIX (GUIX) is a high-performance real-time implementation of a graphical interface framework designed exclusively for embedded ThreadX-based applications.</span></span> <span data-ttu-id="3c91f-105">この章では、GUIX の概要と、そのアプリケーションおよび利点について説明します。</span><span class="sxs-lookup"><span data-stu-id="3c91f-105">This chapter contains an introduction to GUIX and a description of its applications and benefits.</span></span>

## <a name="guix-feature-overview"></a><span data-ttu-id="3c91f-106">GUIX の機能の概要</span><span class="sxs-lookup"><span data-stu-id="3c91f-106">GUIX Feature Overview</span></span>

<span data-ttu-id="3c91f-107">他の多くの GUI 実装とは異なり、GUIX は汎用性を考慮して、つまり、マイクロコントローラー ベースの小規模なアプリケーションから、強力な RISC および DSP プロセッサを使用するアプリケーションまで容易にスケーリングするように設計されています。</span><span class="sxs-lookup"><span data-stu-id="3c91f-107">Unlike many other GUI implementations, GUIX is designed to be versatile—easily scaling from small micro-controller-based applications to those that use powerful RISC and DSP processors.</span></span> <span data-ttu-id="3c91f-108">これは、当初はワークステーション環境を対象にしていたが、その後で無理に埋め込み設計に詰め込まれたパブリック ドメインまたはその他の商用実装とは大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="3c91f-108">This is in sharp contrast to public domain or other commercial implementations originally intended for workstation environments but then squeezed into embedded designs.</span></span> <span data-ttu-id="3c91f-109">GUIX の機能の概要を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3c91f-109">An overview of GUIX features follows:</span></span>

- <span data-ttu-id="3c91f-110">ホスト ベースのデザイン ツール GUIX Studio による使いやすさ</span><span class="sxs-lookup"><span data-stu-id="3c91f-110">Easy to use with host-based design tool GUIX Studio</span></span>

- <span data-ttu-id="3c91f-111">完全なホストされたプロトタイプ作成のための Win32 GUIX ランタイム環境</span><span class="sxs-lookup"><span data-stu-id="3c91f-111">Win32 GUIX run-time environment for complete hosted prototyping</span></span>

- <span data-ttu-id="3c91f-112">ThreadX でサポートされるほとんどのプロセッサをサポート</span><span class="sxs-lookup"><span data-stu-id="3c91f-112">Supports most processors supported by ThreadX</span></span>

- <span data-ttu-id="3c91f-113">ANSI C のみによる記述</span><span class="sxs-lookup"><span data-stu-id="3c91f-113">Written exclusively in ANSI C</span></span>

- <span data-ttu-id="3c91f-114">エンディアン ニュートラル</span><span class="sxs-lookup"><span data-stu-id="3c91f-114">Endian neutral</span></span>

- <span data-ttu-id="3c91f-115">最小で、かつ最速の埋め込み GUI</span><span class="sxs-lookup"><span data-stu-id="3c91f-115">Smallest, Fasted Embedded GUI</span></span>

- <span data-ttu-id="3c91f-116">実行時に構成可能 (オブジェクト数、画面サイズなど)</span><span class="sxs-lookup"><span data-stu-id="3c91f-116">Run-time configurable, number of objects, screen size, etc.</span></span>

- <span data-ttu-id="3c91f-117">ディスプレイ ドライバー インターフェイスの記述が容易</span><span class="sxs-lookup"><span data-stu-id="3c91f-117">Easy to write display driver interface</span></span>

- <span data-ttu-id="3c91f-118">カラー (最大 32 bpp の色深度)、モノクロ、グレースケールのサポート</span><span class="sxs-lookup"><span data-stu-id="3c91f-118">Color (up to 32-bpp color depth), monochrome, and grayscale support</span></span>

- <span data-ttu-id="3c91f-119">UTF8 文字列エンコードと文字列リソースによる多言語のサポート</span><span class="sxs-lookup"><span data-stu-id="3c91f-119">Multilingual support via UTF8 string encoding and string resources</span></span>

- <span data-ttu-id="3c91f-120">既定の無料フォント、新しいフォントの追加が容易</span><span class="sxs-lookup"><span data-stu-id="3c91f-120">Default free fonts and easy to add new fonts</span></span>

- <span data-ttu-id="3c91f-121">さまざまなサイズの複数の描画キャンバスのサポート</span><span class="sxs-lookup"><span data-stu-id="3c91f-121">Multiple drawing Canvases supported, of various sizes</span></span>

- <span data-ttu-id="3c91f-122">さまざまなサイズと色深度の複数のディスプレイのサポート</span><span class="sxs-lookup"><span data-stu-id="3c91f-122">Multiple displays of different sizes and color depths supported</span></span>

- <span data-ttu-id="3c91f-123">画面の切り替えのサポート (フェード イン、フェード アウト、スワイプなど)</span><span class="sxs-lookup"><span data-stu-id="3c91f-123">Screen Transition support (fade in, fade out, swipe, etc.)</span></span>

- <span data-ttu-id="3c91f-124">タッチ スクリーン、ジェスチャ、仮想キーボードのサポート</span><span class="sxs-lookup"><span data-stu-id="3c91f-124">Touch Screen, Gesture, and Virtual Keyboard Support</span></span>

- <span data-ttu-id="3c91f-125">ビットマップ圧縮</span><span class="sxs-lookup"><span data-stu-id="3c91f-125">Bitmap compression</span></span>

- <span data-ttu-id="3c91f-126">アルファ ブレンドのサポート</span><span class="sxs-lookup"><span data-stu-id="3c91f-126">Alpha Blending Support</span></span>

- <span data-ttu-id="3c91f-127">ディザーのサポート</span><span class="sxs-lookup"><span data-stu-id="3c91f-127">Dither Support</span></span>

- <span data-ttu-id="3c91f-128">アンチエイリアシングのサポート</span><span class="sxs-lookup"><span data-stu-id="3c91f-128">Anti-Aliasing Support</span></span>

- <span data-ttu-id="3c91f-129">スキニングとテーマ</span><span class="sxs-lookup"><span data-stu-id="3c91f-129">Skinning and Themes</span></span>

- <span data-ttu-id="3c91f-130">キャンバス ブレンド</span><span class="sxs-lookup"><span data-stu-id="3c91f-130">Canvas Blending</span></span>

- <span data-ttu-id="3c91f-131">完全なウィンドウ管理</span><span class="sxs-lookup"><span data-stu-id="3c91f-131">Complete Window Management</span></span>

  - <span data-ttu-id="3c91f-132">親/子の関係</span><span class="sxs-lookup"><span data-stu-id="3c91f-132">Parent/Child Relationship</span></span>

  - <span data-ttu-id="3c91f-133">動的な作成、削除、サイズ変更、移動</span><span class="sxs-lookup"><span data-stu-id="3c91f-133">Dynamic creation, deletion, resizing, moving</span></span>
  - <span data-ttu-id="3c91f-134">イベント処理と描画の分離</span><span class="sxs-lookup"><span data-stu-id="3c91f-134">Separate event handling and drawing</span></span> 
  - <span data-ttu-id="3c91f-135">Z オーダー</span><span class="sxs-lookup"><span data-stu-id="3c91f-135">Z-order</span></span>
  - <span data-ttu-id="3c91f-136">クリッピングとビュー</span><span class="sxs-lookup"><span data-stu-id="3c91f-136">Clipping and views</span></span>

- <span data-ttu-id="3c91f-137">豊富な一連のウィジェット</span><span class="sxs-lookup"><span data-stu-id="3c91f-137">Extensive Set of Widgets</span></span>

  - <span data-ttu-id="3c91f-138">さまざまなボタンの種類、スライダー、ダイヤル</span><span class="sxs-lookup"><span data-stu-id="3c91f-138">Various button types, sliders, and dials</span></span>

  - <span data-ttu-id="3c91f-139">ドロップダウン リスト</span><span class="sxs-lookup"><span data-stu-id="3c91f-139">Drop Down List</span></span>
  
  - <span data-ttu-id="3c91f-140">Prompt</span><span class="sxs-lookup"><span data-stu-id="3c91f-140">Prompt</span></span>

  - <span data-ttu-id="3c91f-141">複数行テキスト ビュー</span><span class="sxs-lookup"><span data-stu-id="3c91f-141">Multi-Line text view</span></span>
  
  - <span data-ttu-id="3c91f-142">単一行および複数行テキスト入力</span><span class="sxs-lookup"><span data-stu-id="3c91f-142">Single and Multi-Line text input</span></span>
  
  - <span data-ttu-id="3c91f-143">数値およびテキスト スクロール ホイール</span><span class="sxs-lookup"><span data-stu-id="3c91f-143">Numeric and Textual Scroll Wheels</span></span>
  
  - <span data-ttu-id="3c91f-144">ウィンドウとスクロール バー</span><span class="sxs-lookup"><span data-stu-id="3c91f-144">Windows and Scroll Bars</span></span>
  
  - <span data-ttu-id="3c91f-145">放射状の進行状況バー</span><span class="sxs-lookup"><span data-stu-id="3c91f-145">Radial Progress Bar</span></span>
  
  - <span data-ttu-id="3c91f-146">スプライト</span><span class="sxs-lookup"><span data-stu-id="3c91f-146">Sprite</span></span>

### <a name="ansi-c-source-code"></a><span data-ttu-id="3c91f-147">ANSI C ソース コード</span><span class="sxs-lookup"><span data-stu-id="3c91f-147">ANSI C Source Code</span></span>

<span data-ttu-id="3c91f-148">GUIX は完全に ANSI C で記述されているため、ANSI C コンパイラと ThreadX がサポートされているほぼすべてのプロセッサ アーキテクチャにすぐに移植できます。</span><span class="sxs-lookup"><span data-stu-id="3c91f-148">GUIX is written completely in ANSI C and is portable immediately to virtually any processor architecture that has an ANSI C compiler and ThreadX support.</span></span> <span data-ttu-id="3c91f-149">ANSI C で記述されていますが、GUIX ではオブジェクト指向モデルと継承を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c91f-149">Although written in ANSI C, GUIX uses an object oriented model and inheritance.</span></span>

### <a name="not-a-black-box"></a><span data-ttu-id="3c91f-150">ブラック ボックスではない</span><span class="sxs-lookup"><span data-stu-id="3c91f-150">Not A Black Box</span></span>

<span data-ttu-id="3c91f-151">GUIX のほとんどのディストリビューションには、完全な C ソース コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3c91f-151">Most distributions of GUIX include the complete C source code.</span></span> <span data-ttu-id="3c91f-152">これにより、多くの商用 GUI 実装で発生する "ブラック ボックス" の問題が解消されます。</span><span class="sxs-lookup"><span data-stu-id="3c91f-152">This eliminates the “black-box” problems that occur with many commercial GUI implementations.</span></span> <span data-ttu-id="3c91f-153">GUIX を使用すると、アプリケーション開発者は GUI が何を行っているかを正確に確認することができ、秘密は存在しません。</span><span class="sxs-lookup"><span data-stu-id="3c91f-153">By using GUIX, applications developers can see exactly what the GUI is doing—there are no mysteries!</span></span>

<span data-ttu-id="3c91f-154">また、ソース コードが存在すると、アプリケーション固有の変更も可能になります。</span><span class="sxs-lookup"><span data-stu-id="3c91f-154">Having the source code also allows for application specific modifications.</span></span> <span data-ttu-id="3c91f-155">お勧めはできませんが、必要になった場合は GUI を変更できると間違いなく役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3c91f-155">Although not recommended, it is certainly beneficial to have the ability to modify the GUI if it is required.</span></span> <span data-ttu-id="3c91f-156">これらの機能は、社内製品またはパブリック ドメイン製品の操作に慣れている開発者には特に有効です。</span><span class="sxs-lookup"><span data-stu-id="3c91f-156">These features are especially comforting to developers accustomed to working with in-house or public domain products.</span></span> <span data-ttu-id="3c91f-157">これらの開発者は、ソース コードが存在することと、それを変更できることを期待しています。</span><span class="sxs-lookup"><span data-stu-id="3c91f-157">They expect to have source code and the ability to modify it.</span></span> <span data-ttu-id="3c91f-158">GUIX は、このような開発者のための究極の GUI ソフトウェアです。</span><span class="sxs-lookup"><span data-stu-id="3c91f-158">GUIX is the ultimate GUI software for such developers.</span></span>

## <a name="embedded-gui-applications"></a><span data-ttu-id="3c91f-159">埋め込み GUI アプリケーション</span><span class="sxs-lookup"><span data-stu-id="3c91f-159">Embedded GUI Applications</span></span>

<span data-ttu-id="3c91f-160">埋め込み GUI アプリケーションは、ユーザー インターフェイスの要件があり、かつ携帯電話、通信機器、自動車エンジン、レーザー プリンター、医療機器などの製品の内部に隠されたマイクロプロセッサ上で実行されるアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="3c91f-160">Embedded GUI applications are applications that have a user interface requirement and execute on microprocessors hidden inside products such as cellular phones, communication equipment, automotive engines, laser printers, medical devices, and so forth.</span></span> <span data-ttu-id="3c91f-161">このようなアプリケーションでは、ほぼ常にメモリとパフォーマンスに何らかの制約があります。</span><span class="sxs-lookup"><span data-stu-id="3c91f-161">Such applications almost always have some memory and performance constraints.</span></span> <span data-ttu-id="3c91f-162">埋め込み GUI のもう 1 つの特徴は、そのソフトウェアとハードウェアが専用であることです。</span><span class="sxs-lookup"><span data-stu-id="3c91f-162">Another distinction of embedded GUI is that their software and hardware have a dedicated purpose.</span></span>

### <a name="real-time-gui-software"></a><span data-ttu-id="3c91f-163">リアルタイム GUI ソフトウェア</span><span class="sxs-lookup"><span data-stu-id="3c91f-163">Real-time GUI Software</span></span>

<span data-ttu-id="3c91f-164">基本的に、ある正確な期間内に処理を実行する必要がある GUI ソフトウェアは "*リアルタイム GUI*" ソフトウェアと呼ばれ、時間の制約が GUI アプリケーションに課される場合、そのアプリケーションはリアルタイム アプリケーションとして分類されます。</span><span class="sxs-lookup"><span data-stu-id="3c91f-164">Basically, GUI software that must perform its processing within an exact period of time is called *real-time GUI* software, and when time constraints are imposed on GUI applications, they are classified as realtime applications.</span></span> <span data-ttu-id="3c91f-165">埋め込み GUI アプリケーションは、外部の環境とのやり取りがその本来の処理であるため、ほぼ常にリアルタイムです。</span><span class="sxs-lookup"><span data-stu-id="3c91f-165">Embedded GUI applications are almost always real-time because of their inherent interaction with the external world.</span></span>

## <a name="guix-benefits"></a><span data-ttu-id="3c91f-166">GUIX の利点</span><span class="sxs-lookup"><span data-stu-id="3c91f-166">GUIX Benefits</span></span>

<span data-ttu-id="3c91f-167">埋め込みアプリケーションで GUIX を使用する主な利点は、高パフォーマンス、豊富な機能、そして非常に小さなメモリ要件です。</span><span class="sxs-lookup"><span data-stu-id="3c91f-167">The primary benefits of using GUIX for embedded applications are high-performance, feature rich, and very small memory requirements.</span></span> <span data-ttu-id="3c91f-168">GUIX はまた、高パフォーマンスのマルチタスキング Azure RTOS ThreadX リアルタイム オペレーティング システムとも完全に統合されています。</span><span class="sxs-lookup"><span data-stu-id="3c91f-168">GUIX is also completely integrated with the high-performance, multitasking Azure RTOS ThreadX real-time operating system.</span></span>

### <a name="improved-responsiveness"></a><span data-ttu-id="3c91f-169">応答性の向上</span><span class="sxs-lookup"><span data-stu-id="3c91f-169">Improved Responsiveness</span></span>

<span data-ttu-id="3c91f-170">高パフォーマンスの GUIX 製品を使用すると、アプリケーションは、これまでにない速さで応答できます。</span><span class="sxs-lookup"><span data-stu-id="3c91f-170">The high-performance GUIX product enables applications to respond faster than ever before.</span></span> <span data-ttu-id="3c91f-171">これは、膨大な量のビジュアル情報があるか、またはこのような情報の表示に対する厳密なタイミング要件がある埋め込みアプリケーションにとって特に重要です。</span><span class="sxs-lookup"><span data-stu-id="3c91f-171">This is especially important for embedded applications that either have a significant volume of visual information or strict timing requirements on displaying such information.</span></span>

### <a name="software-maintenance"></a><span data-ttu-id="3c91f-172">ソフトウェアのメンテナンス</span><span class="sxs-lookup"><span data-stu-id="3c91f-172">Software Maintenance</span></span>

<span data-ttu-id="3c91f-173">GUIX を使用すると、開発者は、その埋め込みアプリケーションの GUI の側面を容易にパーティション分割できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3c91f-173">Using GUIX allows developers to easily partition the GUI aspects of their embedded application.</span></span> <span data-ttu-id="3c91f-174">このパーティション分割により、開発プロセス全体が容易になり、将来のソフトウェアのメンテナンスが大幅に強化されます。</span><span class="sxs-lookup"><span data-stu-id="3c91f-174">This partitioning makes the entire development process easy and significantly enhances future software maintenance.</span></span>

### <a name="increased-throughput"></a><span data-ttu-id="3c91f-175">スループットの向上</span><span class="sxs-lookup"><span data-stu-id="3c91f-175">Increased Throughput</span></span>

<span data-ttu-id="3c91f-176">GUIX は、埋め込みアプリケーションに直接転送する、使用可能な最高のパフォーマンスの GUI を提供します。</span><span class="sxs-lookup"><span data-stu-id="3c91f-176">GUIX provides the highest-performance GUI available, which directly transfers to the embedded application.</span></span> <span data-ttu-id="3c91f-177">GUIX アプリケーションは、ユーザー インターフェイス情報を GUIX 以外のアプリケーションより高速に処理できます。</span><span class="sxs-lookup"><span data-stu-id="3c91f-177">GUIX applications are able to process user interface information faster than non-GUIX applications!</span></span>

### <a name="processor-isolation"></a><span data-ttu-id="3c91f-178">プロセッサの分離</span><span class="sxs-lookup"><span data-stu-id="3c91f-178">Processor Isolation</span></span>

<span data-ttu-id="3c91f-179">GUIX は、アプリケーションと基になるプロセッサおよびディスプレイ ハードウェアとの間の、プロセッサに依存しない堅牢なインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="3c91f-179">GUIX provides a robust, processor-independent interface between the application and the underlying processor and display hardware.</span></span> <span data-ttu-id="3c91f-180">これにより、開発者はディスプレイ ハードウェアの問題への対処に余分な時間を費やすのではなく、ユーザー インターフェイスの高レベルの側面に集中できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3c91f-180">This allows developers to concentrate on the high-level aspects of the user interface rather than spending extra time dealing with display hardware issues.</span></span>

### <a name="ease-of-use"></a><span data-ttu-id="3c91f-181">使いやすさ</span><span class="sxs-lookup"><span data-stu-id="3c91f-181">Ease of Use</span></span>

<span data-ttu-id="3c91f-182">GUIX は、アプリケーション開発者を念頭に置いて設計されています。</span><span class="sxs-lookup"><span data-stu-id="3c91f-182">GUIX is designed with the application developer in mind.</span></span> <span data-ttu-id="3c91f-183">GUIX のアーキテクチャやサービス呼び出しインターフェイスは容易に理解できます。</span><span class="sxs-lookup"><span data-stu-id="3c91f-183">The GUIX architecture and service call interface are easy to understand.</span></span> <span data-ttu-id="3c91f-184">その結果、GUIX 開発者は、その高度な機能をすばやく使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c91f-184">As a result, GUIX developers can quickly use its advanced features.</span></span>

### <a name="improve-time-to-market"></a><span data-ttu-id="3c91f-185">市場投入までの時間の短縮</span><span class="sxs-lookup"><span data-stu-id="3c91f-185">Improve Time to Market</span></span>

<span data-ttu-id="3c91f-186">GUIX の強力な機能は、ソフトウェア開発プロセスを加速します。</span><span class="sxs-lookup"><span data-stu-id="3c91f-186">The powerful features of GUIX accelerate the software development process.</span></span> <span data-ttu-id="3c91f-187">GUIX では、プロセッサやディスプレイ ハードウェアのほとんどの問題を抽象化することにより、これらの問題をアプリケーション ユーザー インターフェイス実装の大部分から排除しています。</span><span class="sxs-lookup"><span data-stu-id="3c91f-187">GUIX abstracts most processor and display hardware issues, thereby removing these concerns from a majority of application user interface implementation.</span></span> <span data-ttu-id="3c91f-188">この機能と、使いやすさや高度な機能セットとが相まって、市場投入までの時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="3c91f-188">This feature, coupled with the ease-of-use and advanced feature set, results in a faster time to market!</span></span>

### <a name="protecting-the-software-investment"></a><span data-ttu-id="3c91f-189">ソフトウェア投資の保護</span><span class="sxs-lookup"><span data-stu-id="3c91f-189">Protecting the Software Investment</span></span>

<span data-ttu-id="3c91f-190">GUIX は ANSI C のみで記述され、Azure RTOS ThreadX リアルタイム オペレーティング システムと完全に統合されています。</span><span class="sxs-lookup"><span data-stu-id="3c91f-190">GUIX is written exclusively in ANSI C and is fully integrated with the Azure RTOS ThreadX real-time operating system.</span></span> <span data-ttu-id="3c91f-191">つまり、GUIX アプリケーションは、ThreadX でサポートされているすべてのプロセッサにすぐに移植できます。</span><span class="sxs-lookup"><span data-stu-id="3c91f-191">This means GUIX applications are instantly portable to all ThreadX supported processors.</span></span> <span data-ttu-id="3c91f-192">さらに良いことに、まったく新しいプロセッサ アーキテクチャを数週間のうちに ThreadX でサポートできます。</span><span class="sxs-lookup"><span data-stu-id="3c91f-192">Better yet, a completely new processor architecture can be supported with ThreadX in a matter of weeks.</span></span> <span data-ttu-id="3c91f-193">その結果、GUIX の使用によってアプリケーションの移行パスが保証され、当初の開発投資が保護されます。</span><span class="sxs-lookup"><span data-stu-id="3c91f-193">As a result, using GUIX ensures the application’s migration path and protects the original development investment.</span></span>
