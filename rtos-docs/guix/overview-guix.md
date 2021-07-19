---
title: Azure RTOS GUIX および Azure RTOS GUIX Studio について
description: Azure RTOS GUIX は、埋め込みシステム開発者のニーズに対応するために作成された、プロフェッショナル品質のパッケージです。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0a6ac2c7a76893d516b9beae9b893c9764de60ba
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754932"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a><span data-ttu-id="1c584-103">Azure RTOS GUIX および Azure RTOS GUIX Studio の概要</span><span class="sxs-lookup"><span data-stu-id="1c584-103">Overview of Azure RTOS GUIX and Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="1c584-104">Azure GUIX 埋め込み GUI は、深く埋め込まれたリアルタイム IoT アプリケーション向けに特別に設計された、Microsoft の高度な商用 GUI ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="1c584-104">Azure GUIX embedded GUI is Microsoft’s advanced, industrial grade GUI solution designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="1c584-105">また、Microsoft は、Azure RTOS GUIX Studio という完全な機能を備えた WYSIWYG デスクトップ デザイン ツールも提供しており、開発者が、デスクトップ上で自身の GUI をデザインし、Azure RTOS GUIX 埋め込み GUI コードを生成して、それをターゲットにエクスポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="1c584-105">Microsoft also provides a full-featured WYSIWYG desktop design tool named Azure RTOS GUIX Studio, which allows developers to design their GUI on the desktop and generate Azure RTOS GUIX embedded GUI code that can then be exported to the target.</span></span> <span data-ttu-id="1c584-106">Azure RTOS GUIX は Azure RTOS ThreadX RTOS と完全に統合されており、Azure RTOS ThreadX でサポートされている同じプロセッサの多くで利用できます。</span><span class="sxs-lookup"><span data-stu-id="1c584-106">Azure RTOS GUIX is fully integrated with Azure RTOS ThreadX RTOS and is available for many of the same processors supported by Azure RTOS ThreadX.</span></span> <span data-ttu-id="1c584-107">これらすべてを小さな専有領域、高速処理、および優れた操作性と組み合わせることで、Azure RTOS GUIX は、ユーザー インターフェイスを必要とする最も要求の厳しい埋め込み型 IoT アプリケーションに最適な選択肢となります。</span><span class="sxs-lookup"><span data-stu-id="1c584-107">All of this combined with an extremely small footprint, fast execution, and superior ease-of-use, make Azure RTOS GUIX the ideal choice for the most demanding embedded IoT applications requiring a user interface.</span></span> 

## <a name="azure-rtos-guix-api"></a><span data-ttu-id="1c584-108">Azure RTOS GUIX API</span><span class="sxs-lookup"><span data-stu-id="1c584-108">Azure RTOS GUIX API</span></span>

### <a name="powerful-apis"></a><span data-ttu-id="1c584-109">強力な API</span><span class="sxs-lookup"><span data-stu-id="1c584-109">Powerful APIs</span></span>

* <span data-ttu-id="1c584-110">必要に応じて直接的なキャンバス描画を完全サポート</span><span class="sxs-lookup"><span data-stu-id="1c584-110">Full support for direct canvas drawing when needed</span></span>
* <span data-ttu-id="1c584-111">Azure RTOS GUIX Studio で生成されたコードの操作が簡単</span><span class="sxs-lookup"><span data-stu-id="1c584-111">Simple to interact with Azure RTOS GUIX Studio generated code</span></span>
* <span data-ttu-id="1c584-112">線、四角形、多角形などの API</span><span class="sxs-lookup"><span data-stu-id="1c584-112">APIs for line, rectangle, polygon, etc.</span></span>
* <span data-ttu-id="1c584-113">円、弧、弦、楕円などの API</span><span class="sxs-lookup"><span data-stu-id="1c584-113">APIs for circle, arc, pie, chord, ellipse, etc.</span></span>
* <span data-ttu-id="1c584-114">テキスト描画、配置の API</span><span class="sxs-lookup"><span data-stu-id="1c584-114">APIs for text drawing and positioning</span></span>
* <span data-ttu-id="1c584-115">アンチエイリアシング、テクスチャで塗りつぶし、純色で塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="1c584-115">Anti-aliasing, texture fills, and solid fills</span></span>
* <span data-ttu-id="1c584-116">スクリーンおよびウィジェットの作成と変更のための API</span><span class="sxs-lookup"><span data-stu-id="1c584-116">APIs for creating and modifing screens and widgets</span></span>

### <a name="azure-rtos-guix-studio-generated-files"></a><span data-ttu-id="1c584-117">Azure RTOS GUIX Studio で生成されたファイル</span><span class="sxs-lookup"><span data-stu-id="1c584-117">Azure RTOS GUIX Studio Generated Files</span></span>

* <span data-ttu-id="1c584-118">自動生成された ANSI C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="1c584-118">Automatically generated ANSI C source files</span></span>
* <span data-ttu-id="1c584-119">アプリケーション ソフトウェアをレイアウトの詳細から分離</span><span class="sxs-lookup"><span data-stu-id="1c584-119">Insulates application software from layout details</span></span>
* <span data-ttu-id="1c584-120">UI デザインに必要なフォントとイメージの挿入</span><span class="sxs-lookup"><span data-stu-id="1c584-120">Includes fonts and images required by UI design</span></span>
* <span data-ttu-id="1c584-121">アプリケーション コードを使用してコンパイルされた生成ファイル</span><span class="sxs-lookup"><span data-stu-id="1c584-121">Generated files compiled with application code</span></span>
* <span data-ttu-id="1c584-122">アプリケーション ロジックに影響を与えずにスクリーン レイアウトを更新可能</span><span class="sxs-lookup"><span data-stu-id="1c584-122">Screen layout can be updated without affecting application logic</span></span>
* <span data-ttu-id="1c584-123">リソース ID により言語とテーマの独立性を確保</span><span class="sxs-lookup"><span data-stu-id="1c584-123">Resource IDs create language and theme independence</span></span>
* <span data-ttu-id="1c584-124">ユーザーが指定したカスタム描画およびイベント処理関数</span><span class="sxs-lookup"><span data-stu-id="1c584-124">User-supplied custom drawing and event processing functions</span></span>

### <a name="widget-library"></a><span data-ttu-id="1c584-125">ウィジェット ライブラリ</span><span class="sxs-lookup"><span data-stu-id="1c584-125">Widget library</span></span>

* <span data-ttu-id="1c584-126">事前定義されているがカスタマイズ可能な一連の共通インターフェイス要素</span><span class="sxs-lookup"><span data-stu-id="1c584-126">Pre-defined but customizable set of common interface elements</span></span>
* <span data-ttu-id="1c584-127">非常に小さく、コンパクト、かつ効率的</span><span class="sxs-lookup"><span data-stu-id="1c584-127">Extremely small, compact, and efficient</span></span>
* <span data-ttu-id="1c584-128">ライブラリにボタン、ゲージ、リスト、ウィンドウ、スクロール、スライダー、進行状況バー、プロンプトなどが含まれる</span><span class="sxs-lookup"><span data-stu-id="1c584-128">Library includes button, gauge, list, window, scroll, slider, progress bar, prompt and many more</span></span>
* <span data-ttu-id="1c584-129">完全にカスタマイズ可能な描画と外観</span><span class="sxs-lookup"><span data-stu-id="1c584-129">Fully customizable drawing and appearance</span></span>
* <span data-ttu-id="1c584-130">完全にカスタマイズ可能な操作とイベント処理</span><span class="sxs-lookup"><span data-stu-id="1c584-130">Fully customizable operation and event handling</span></span>
* <span data-ttu-id="1c584-131">使用されるウィジェットのみがアプリケーション ソフトウェアとリンク</span><span class="sxs-lookup"><span data-stu-id="1c584-131">Only the widgets used are linked with application software</span></span>

### <a name="math-and-utilities"></a><span data-ttu-id="1c584-132">数式とユーティリティ</span><span class="sxs-lookup"><span data-stu-id="1c584-132">Math and utilities</span></span>

* <span data-ttu-id="1c584-133">正弦、余弦、逆正弦、逆余弦、正接、平方根の関数</span><span class="sxs-lookup"><span data-stu-id="1c584-133">Functions for sin, cos, arcsin, arccos, tangent, square root</span></span>
* <span data-ttu-id="1c584-134">スクリーン領域を操作するための関数</span><span class="sxs-lookup"><span data-stu-id="1c584-134">Functions for manipulating screen regions</span></span>
* <span data-ttu-id="1c584-135">システムの構成と起動</span><span class="sxs-lookup"><span data-stu-id="1c584-135">System configuration and startup</span></span>
* <span data-ttu-id="1c584-136">メモリ プールの定義 (省略可能)</span><span class="sxs-lookup"><span data-stu-id="1c584-136">Memory pool definition (optional)</span></span>
* <span data-ttu-id="1c584-137">タイマー管理</span><span class="sxs-lookup"><span data-stu-id="1c584-137">Timer Management</span></span>
* <span data-ttu-id="1c584-138">アニメーション管理</span><span class="sxs-lookup"><span data-stu-id="1c584-138">Animation Management</span></span>
* <span data-ttu-id="1c584-139">ダーティ リストのメンテナンス</span><span class="sxs-lookup"><span data-stu-id="1c584-139">Dirty list maintenance</span></span>

### <a name="image-processing"></a><span data-ttu-id="1c584-140">画像処理</span><span class="sxs-lookup"><span data-stu-id="1c584-140">Image processing</span></span>

* <span data-ttu-id="1c584-141">jpeg および png イメージのランタイム デコード用の関数</span><span class="sxs-lookup"><span data-stu-id="1c584-141">Functions for runtime decode of jpeg and png images</span></span>
* <span data-ttu-id="1c584-142">ディザリングおよび色空間の変換の適用</span><span class="sxs-lookup"><span data-stu-id="1c584-142">Apply dithering and color space conversion</span></span>
* <span data-ttu-id="1c584-143">イメージの回転</span><span class="sxs-lookup"><span data-stu-id="1c584-143">Image rotation</span></span>
* <span data-ttu-id="1c584-144">イメージのスケーリング</span><span class="sxs-lookup"><span data-stu-id="1c584-144">Image scaling</span></span>
* <span data-ttu-id="1c584-145">イメージのブレンド</span><span class="sxs-lookup"><span data-stu-id="1c584-145">Image blending</span></span>

### <a name="event-processing"></a><span data-ttu-id="1c584-146">イベント処理</span><span class="sxs-lookup"><span data-stu-id="1c584-146">Event processing</span></span>

* <span data-ttu-id="1c584-147">アイドル時に Azure RTOS GUIX スレッドを自動停止</span><span class="sxs-lookup"><span data-stu-id="1c584-147">Automatically suspends Azure RTOS GUIX thread when idle</span></span>
* <span data-ttu-id="1c584-148">UI デザインでよく使用されるイベントドリブン プログラミング デル</span><span class="sxs-lookup"><span data-stu-id="1c584-148">Event-driven programming model popular in UI design</span></span>
* <span data-ttu-id="1c584-149">入力ドライバーを Azure RTOS GUIX 描画スレッドから分離</span><span class="sxs-lookup"><span data-stu-id="1c584-149">Insulates input drivers from Azure RTOS GUIX drawing thread</span></span>
* <span data-ttu-id="1c584-150">イベントを送受信するための関数</span><span class="sxs-lookup"><span data-stu-id="1c584-150">Functions for sending and receiving events</span></span>
* <span data-ttu-id="1c584-151">すべての Azure RTOS GUIX ウィジェットの種類に対する事前定義済みのイベントの種類</span><span class="sxs-lookup"><span data-stu-id="1c584-151">Pre-defined event types for all Azure RTOS GUIX widget types</span></span>
* <span data-ttu-id="1c584-152">サポートされているユーザー定義カスタム イベント</span><span class="sxs-lookup"><span data-stu-id="1c584-152">User-defined custom events supported</span></span>

### <a name="canvas-processing"></a><span data-ttu-id="1c584-153">キャンバスの処理</span><span class="sxs-lookup"><span data-stu-id="1c584-153">Canvas processing</span></span>

* <span data-ttu-id="1c584-154">クリッピングと Z オーダーのメンテナンス</span><span class="sxs-lookup"><span data-stu-id="1c584-154">Clipping and Z-Order maintenance</span></span>
* <span data-ttu-id="1c584-155">ウィジェット ライブラリをハードウェアの詳細から分離</span><span class="sxs-lookup"><span data-stu-id="1c584-155">Insulates widget library from hardware details</span></span>
* <span data-ttu-id="1c584-156">アプリケーションをハードウェアの詳細から分離</span><span class="sxs-lookup"><span data-stu-id="1c584-156">Insulates application from hardware details</span></span>
* <span data-ttu-id="1c584-157">ダーティ領域の自動バックグラウンド更新</span><span class="sxs-lookup"><span data-stu-id="1c584-157">Automatic background refresh of dirty areas</span></span>
* <span data-ttu-id="1c584-158">レイヤーとブレンドがサポートされている複数のキャンバス</span><span class="sxs-lookup"><span data-stu-id="1c584-158">Multiple canvases with layering and blending supported</span></span>
* <span data-ttu-id="1c584-159">アプリケーション ソフトウェアによる直接呼び出しが可能</span><span class="sxs-lookup"><span data-stu-id="1c584-159">Can be invoked directly by the application software</span></span>

### <a name="input-device-drivers"></a><span data-ttu-id="1c584-160">入力デバイス ドライバー</span><span class="sxs-lookup"><span data-stu-id="1c584-160">Input device driver(s)</span></span>

* <span data-ttu-id="1c584-161">ハードウェア固有のサポート、Azure RTOS GUIX およびハードウェアの詳細から切り離されたアプリケーション</span><span class="sxs-lookup"><span data-stu-id="1c584-161">Hardware-specific support, Azure RTOS GUIX and application insulated from hardware details</span></span>
* <span data-ttu-id="1c584-162">抵抗膜方式タッチ、静電容量タッチ、およびキーパッドのサポート</span><span class="sxs-lookup"><span data-stu-id="1c584-162">Resistive Touch, Cap Touch, and keypad supported</span></span>
* <span data-ttu-id="1c584-163">Azure RTOS GUIX イベント キューに渡される入力イベント</span><span class="sxs-lookup"><span data-stu-id="1c584-163">Input events passed to Azure RTOS GUIX event queue</span></span>

### <a name="display-drivers"></a><span data-ttu-id="1c584-164">ディスプレイ ドライバー</span><span class="sxs-lookup"><span data-stu-id="1c584-164">Display drivers</span></span>

* <span data-ttu-id="1c584-165">ハードウェア固有のサポート</span><span class="sxs-lookup"><span data-stu-id="1c584-165">Hardware-specific support</span></span>
* <span data-ttu-id="1c584-166">すべての色深度と色形式に提供される汎用ドライバー</span><span class="sxs-lookup"><span data-stu-id="1c584-166">Generic drivers provided for all color depth and formats</span></span>
* <span data-ttu-id="1c584-167">使用可能なグラフィックス アクセラレータを使用するようにカスタマイズ済み</span><span class="sxs-lookup"><span data-stu-id="1c584-167">Customized to utilize available graphics accelerators</span></span>

### <a name="target-hardware"></a><span data-ttu-id="1c584-168">ターゲット ハードウェア</span><span class="sxs-lookup"><span data-stu-id="1c584-168">Target hardware</span></span>

* <span data-ttu-id="1c584-169">ほぼすべてのグラフィカル出力対応ハードウェアが GUIX に対応</span><span class="sxs-lookup"><span data-stu-id="1c584-169">Nearly any hardware capable of graphical output Is compatible with GUIX</span></span>
* <span data-ttu-id="1c584-170">複数の物理ディスプレイのサポート</span><span class="sxs-lookup"><span data-stu-id="1c584-170">Multiple physical displays supported</span></span>
* <span data-ttu-id="1c584-171">最小 RAM とフラッシュの要件</span><span class="sxs-lookup"><span data-stu-id="1c584-171">Minimal RAM and Flash requirements</span></span>

## <a name="create-elegant-user-interfaces"></a><span data-ttu-id="1c584-172">洗練されたユーザー インターフェイスを作成する</span><span class="sxs-lookup"><span data-stu-id="1c584-172">Create Elegant User Interfaces</span></span>

<span data-ttu-id="1c584-173">Azure RTOS GUIX および Azure RTOS GUIX Studio には、洗練された独自のユーザー インターフェイスの作成に必要な機能すべてが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1c584-173">Azure RTOS GUIX and Azure RTOS GUIX Studio provide all the features necessary to create uniquely elegant user interfaces.</span></span> <span data-ttu-id="1c584-174">標準の Azure RTOS GUIX パッケージには、医療デバイス参照、スマート ウォッチ参照、ホーム オートメーション参照、工業制御参照、自動車参照、さまざまなスプライトとアニメーションの例など、各種サンプル ユーザー インターフェイスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1c584-174">The standard Azure RTOS GUIX package includes various sample user interfaces, including a medical device reference, a smart watch reference, a home automation reference, an industrial control reference, an automotive reference, and various sprite and animation examples.</span></span> <span data-ttu-id="1c584-175">以下の参照例をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="1c584-175">Please click on the reference examples shown below.</span></span>

### <a name="home-automation"></a><span data-ttu-id="1c584-176">ホーム オートメーション</span><span class="sxs-lookup"><span data-stu-id="1c584-176">Home Automation</span></span>

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a><span data-ttu-id="1c584-177">医療</span><span class="sxs-lookup"><span data-stu-id="1c584-177">Medical</span></span>

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a><span data-ttu-id="1c584-178">コンシューマー</span><span class="sxs-lookup"><span data-stu-id="1c584-178">Consumer</span></span>

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a><span data-ttu-id="1c584-179">白物家電</span><span class="sxs-lookup"><span data-stu-id="1c584-179">White Goods</span></span>

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a><span data-ttu-id="1c584-180">自動車</span><span class="sxs-lookup"><span data-stu-id="1c584-180">Automotive</span></span>

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a><span data-ttu-id="1c584-181">工業</span><span class="sxs-lookup"><span data-stu-id="1c584-181">Industrial</span></span>

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

<span data-ttu-id="1c584-182">各 Azure RTOS GUIX 参照には、参照デザインのすべてのグラフィカル要素を定義する、対応する Azure RTOS GUIX Studio プロジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1c584-182">Each Azure RTOS GUIX reference has a corresponding Azure RTOS GUIX Studio project that defines all the graphical elements of the reference design.</span></span> <span data-ttu-id="1c584-183">参照デザインを変更するのは簡単です。</span><span class="sxs-lookup"><span data-stu-id="1c584-183">Changing a reference design is easy.</span></span> <span data-ttu-id="1c584-184">対応する Azure RTOS GUIX プロジェクトを開き、必要な変更を加え、プロジェクトを保存して、"*プロジェクト*" を選択するだけです。</span><span class="sxs-lookup"><span data-stu-id="1c584-184">Simply open the corresponding Azure RTOS GUIX project, make the desired changes, save the project, and then select *Project*.</span></span>

<span data-ttu-id="1c584-185">すべての出力ファイルを生成して、Azure RTOS GUIX 用の C コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="1c584-185">Generate All Output Files to generate the C code for Azure RTOS GUIX.</span></span> <span data-ttu-id="1c584-186">そして、ターゲット アプリケーションをリビルドし、変更された参照デザインを確認するだけです。</span><span class="sxs-lookup"><span data-stu-id="1c584-186">Then simply rebuild the target application and run to observe the modified reference design.</span></span>

### <a name="guix-memory-footprint"></a><span data-ttu-id="1c584-187">GUIX のメモリ占有領域</span><span class="sxs-lookup"><span data-stu-id="1c584-187">GUIX Memory footprint</span></span>

<span data-ttu-id="1c584-188">Azure RTOS GUIX の最小メモリ専有領域は非常に小さく、キャンバスに必要なメモリを含まない基本サポートの場合、フラッシュは 13.2 KB、RAM は 4 KB です。</span><span class="sxs-lookup"><span data-stu-id="1c584-188">Azure RTOS GUIX has a remarkably small minimal footprint of 13.2KB of FLASH and 4KB RAM for basic support, not including the memory required for a canvas.</span></span>

<span data-ttu-id="1c584-189">内部で GRAM と自己更新テクノロジが使用されているディスプレイについては、キャンバス メモリは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="1c584-189">For a display with internal GRAM and self-refresh technology, no canvas memory is required.</span></span> <span data-ttu-id="1c584-190">ただし、描画パフォーマンスを向上させるために、または、ディスプレイに対してローカルな GRAM を使用しないディスプレイ構成の場合は、アプリケーションによってキャンバス メモリ領域が定義されます。</span><span class="sxs-lookup"><span data-stu-id="1c584-190">However, to improve drawing performance, or for a display configuration that does not utilize GRAM local to the display, a canvas memory area is defined by the application.</span></span>

<span data-ttu-id="1c584-191">キャンバスのメモリ要件は、キャンバス サイズと色深度の関数であり、次の式で定義されます。</span><span class="sxs-lookup"><span data-stu-id="1c584-191">Canvas memory requirements are a function of the canvas size as well as the color depth, and are defined by the formula:</span></span>

<span data-ttu-id="1c584-192"><i>キャンバス RAM (バイト) = (x \* y \* (bpp/8))</i></span><span class="sxs-lookup"><span data-stu-id="1c584-192"><i>Canvas RAM (bytes) = (x \* y \* (bpp/8))</i></span></span>

<span data-ttu-id="1c584-193">ここで、"x" と "y" はキャンバス (ディスプレイ) のディメンションです。</span><span class="sxs-lookup"><span data-stu-id="1c584-193">Where “x” and “y” are the dimensions of the canvas (display).</span></span>

<span data-ttu-id="1c584-194">また、ほとんどのアプリケーションでグラフィカル リソースが使用されていますが、これは主要 Azure RTOS GUIX ライブラリ ストレージ要件に含まれていません。</span><span class="sxs-lookup"><span data-stu-id="1c584-194">Most applications also utilize graphical resources, which are not included in the core Azure RTOS GUIX library storage requirements.</span></span> <span data-ttu-id="1c584-195">これらのリソースには、フォント、グラフィカル アイコン (ピクセルマップ)、および静的な文字列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1c584-195">These resources include fonts, graphical icons (pixelmaps), and static strings.</span></span> <span data-ttu-id="1c584-196">このデータは、const メモリ セクション (フラッシュ) に格納できます。</span><span class="sxs-lookup"><span data-stu-id="1c584-196">This data can be stored in the const memory section (i.e. FLASH).</span></span>

<span data-ttu-id="1c584-197">このメモリ領域のサイズは、使用される一意のフォントの数とサイズ、使用されるグラフィカル アイコンの数とサイズ、出力色形式、各リソースが圧縮データを使用しているかどうかなど、さまざまな要因に依存します。これは、Azure RTOS GUIX が、フォントとピクセルマップの両方のデータの RLE 圧縮をサポートしているためです。</span><span class="sxs-lookup"><span data-stu-id="1c584-197">The size of this memory area is dependent on a number of factors, including the number and size of unique fonts used, the number and size of the graphical icons used, the output color format, and whether or not each resource is using compressed data, since Azure RTOS GUIX supports RLE compression of both font and pixelmap data.</span></span> <span data-ttu-id="1c584-198">各リソースのストレージ要件は、Azure RTOS GUIX Studio アプリケーション内に表示されます。これにより、ユーザーは、アプリケーション リソースによって消費されるフラッシュ メモリの量を追跡および監視できます。</span><span class="sxs-lookup"><span data-stu-id="1c584-198">The storage requirements for each resource are displayed within the Azure RTOS GUIX Studio application, allowing the user to track and monitor the amount of flash memory that will be consumed by the application resources.</span></span>

<span data-ttu-id="1c584-199">Azure RTOS ThreadX と同様に、Azure RTOS GUIX のサイズは、アプリケーションで実際に使用されるサービスに基づいて自動的にスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="1c584-199">Like Azure RTOS ThreadX, the size of Azure RTOS GUIX automatically scales based on the services actually used by the application.</span></span> <span data-ttu-id="1c584-200">これにより、複雑な構成やビルド パラメーターが実質的に不要になるため、開発者の作業がより簡単になります。</span><span class="sxs-lookup"><span data-stu-id="1c584-200">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

#### <a name="simple-easy-to-use"></a><span data-ttu-id="1c584-201">シンプルで優れた操作性</span><span class="sxs-lookup"><span data-stu-id="1c584-201">Simple, easy-to-use</span></span>

<span data-ttu-id="1c584-202">Azure RTOS GUIX は非常に簡単に使用できますが、Azure RTOS GUIX Studio は、開発者がデスクトップ上で視覚的にデザインし、実際のターゲット上で動作する C コードを生成できるため、さらに使いやすくなっています。</span><span class="sxs-lookup"><span data-stu-id="1c584-202">Azure RTOS GUIX is very simple to use and Azure RTOS GUIX Studio makes it even easier by allowing developers to visually design on the desktop and generate C code that runs on the actual target.</span></span> <span data-ttu-id="1c584-203">アプリケーションが独自のカスタム イベント処理や描画関数を追加して、GUI を完成させることができます。</span><span class="sxs-lookup"><span data-stu-id="1c584-203">Applications can then add their own custom event handling and drawing functions to complete their GUI.</span></span>

<span data-ttu-id="1c584-204">Azure RTOS GUIX API の使い方は簡単です。</span><span class="sxs-lookup"><span data-stu-id="1c584-204">Using the Azure RTOS GUIX API is straightforward.</span></span> <span data-ttu-id="1c584-205">Azure RTOS GUIX API は直感的かつ高機能です。</span><span class="sxs-lookup"><span data-stu-id="1c584-205">The Azure RTOS GUIX API is both intuitive and highly functional.</span></span> <span data-ttu-id="1c584-206">API 名は、他のファイル システム製品でよく見られる略語や大幅に省略された名前ではなく、実際の単語で構成されています。</span><span class="sxs-lookup"><span data-stu-id="1c584-206">The API names are made of real words and not the “alphabet soup” and/or the highly abbreviated names that are so common in other file system products.</span></span> <span data-ttu-id="1c584-207">すべての Azure RTOS GUIX API は、先頭に *gx_* が付き、名詞 - 動詞の名前付け規則に従っています。</span><span class="sxs-lookup"><span data-stu-id="1c584-207">All Azure RTOS GUIX APIs have a leading *gx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="1c584-208">さらに、API 全体に機能的な一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="1c584-208">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="1c584-209">たとえば、ウィジェット制御ブロックを初期化するすべての API に、&lt;widget_type&gt;_create という名前が付けられます。また、各ウィジェットの種類の create function パラメーターは常に同じ順序で定義されます。</span><span class="sxs-lookup"><span data-stu-id="1c584-209">For example, all APIs that initialize a widget control block are named &lt; widget_type&gt;_create, and the create function parameters for each widget type are always defined in the same order.</span></span>

### <a name="comprehensive-set-of-built-in-widgets"></a><span data-ttu-id="1c584-210">包括的な組み込みウィジェット セット</span><span class="sxs-lookup"><span data-stu-id="1c584-210">Comprehensive set of built-in widgets</span></span>

* <span data-ttu-id="1c584-211">Azure RTOS GUIX には、次のような豊富な組み込みウィジェット セットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1c584-211">Azure RTOS GUIX provides a rich set of built-in widgets, including:</span></span>
* <span data-ttu-id="1c584-212">アコーディオン メニュー</span><span class="sxs-lookup"><span data-stu-id="1c584-212">Accordion Menu</span></span>
* <span data-ttu-id="1c584-213">Button</span><span class="sxs-lookup"><span data-stu-id="1c584-213">Button</span></span>
* <span data-ttu-id="1c584-214">Checkbox</span><span class="sxs-lookup"><span data-stu-id="1c584-214">Checkbox</span></span>
* <span data-ttu-id="1c584-215">円形ゲージ</span><span class="sxs-lookup"><span data-stu-id="1c584-215">Circular Gauge</span></span>
* <span data-ttu-id="1c584-216">ドロップダウン リスト</span><span class="sxs-lookup"><span data-stu-id="1c584-216">Drop Down List</span></span>
* <span data-ttu-id="1c584-217">横方向の一覧</span><span class="sxs-lookup"><span data-stu-id="1c584-217">Horizontal List</span></span>
* <span data-ttu-id="1c584-218">水平スクロールバー ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="1c584-218">Horizontal Scrollbar Window</span></span>
* <span data-ttu-id="1c584-219">アイコン</span><span class="sxs-lookup"><span data-stu-id="1c584-219">Icon</span></span>
* <span data-ttu-id="1c584-220">アイコン ボタン</span><span class="sxs-lookup"><span data-stu-id="1c584-220">Icon Button</span></span>
* <span data-ttu-id="1c584-221">折れ線グラフ</span><span class="sxs-lookup"><span data-stu-id="1c584-221">Line Chart</span></span>
* <span data-ttu-id="1c584-222">メニュー</span><span class="sxs-lookup"><span data-stu-id="1c584-222">Menu</span></span>
* <span data-ttu-id="1c584-223">複数行テキスト ボタン</span><span class="sxs-lookup"><span data-stu-id="1c584-223">Multi Line Text Button</span></span>
* <span data-ttu-id="1c584-224">複数行テキスト入力</span><span class="sxs-lookup"><span data-stu-id="1c584-224">Multi Line Text Input</span></span>
* <span data-ttu-id="1c584-225">複数行テキスト ビュー</span><span class="sxs-lookup"><span data-stu-id="1c584-225">Multi Line Text View</span></span>
* <span data-ttu-id="1c584-226">数値ピクセルマップ プロンプト</span><span class="sxs-lookup"><span data-stu-id="1c584-226">Numeric Pixelmap Prompt</span></span>
* <span data-ttu-id="1c584-227">数値プロンプト</span><span class="sxs-lookup"><span data-stu-id="1c584-227">Numeric Prompt</span></span>
* <span data-ttu-id="1c584-228">数値スクロール ホイール</span><span class="sxs-lookup"><span data-stu-id="1c584-228">Numeric Scroll Wheel</span></span>
* <span data-ttu-id="1c584-229">ピクセルマップ ボタン</span><span class="sxs-lookup"><span data-stu-id="1c584-229">Pixelmap Button</span></span>
* <span data-ttu-id="1c584-230">ピクセル マップ プロンプト</span><span class="sxs-lookup"><span data-stu-id="1c584-230">Pixelmap Prompt</span></span>
* <span data-ttu-id="1c584-231">ピクセルマップ スライダー</span><span class="sxs-lookup"><span data-stu-id="1c584-231">Pixelmap Slider</span></span>
* <span data-ttu-id="1c584-232">ピクセルマップ スプライト</span><span class="sxs-lookup"><span data-stu-id="1c584-232">Pixelmap Sprite</span></span>
* <span data-ttu-id="1c584-233">進行状況バー</span><span class="sxs-lookup"><span data-stu-id="1c584-233">Progress Bar</span></span>
* <span data-ttu-id="1c584-234">Prompt</span><span class="sxs-lookup"><span data-stu-id="1c584-234">Prompt</span></span>
* <span data-ttu-id="1c584-235">放射状の進行状況バー</span><span class="sxs-lookup"><span data-stu-id="1c584-235">Radial Progress Bar</span></span>
* <span data-ttu-id="1c584-236">オプション ボタン</span><span class="sxs-lookup"><span data-stu-id="1c584-236">Radio Button</span></span>
* <span data-ttu-id="1c584-237">スクロール ホイール</span><span class="sxs-lookup"><span data-stu-id="1c584-237">Scroll Wheel</span></span>
* <span data-ttu-id="1c584-238">単一行テキスト入力</span><span class="sxs-lookup"><span data-stu-id="1c584-238">Single Line Text Input</span></span>
* <span data-ttu-id="1c584-239">スライダー</span><span class="sxs-lookup"><span data-stu-id="1c584-239">Slider</span></span>
* <span data-ttu-id="1c584-240">文字列スクロール ホイール</span><span class="sxs-lookup"><span data-stu-id="1c584-240">String Scroll Wheel</span></span>
* <span data-ttu-id="1c584-241">テキスト ボタン</span><span class="sxs-lookup"><span data-stu-id="1c584-241">Text Button</span></span>
* <span data-ttu-id="1c584-242">ツリー ビュー</span><span class="sxs-lookup"><span data-stu-id="1c584-242">Tree View</span></span>
* <span data-ttu-id="1c584-243">縦一覧</span><span class="sxs-lookup"><span data-stu-id="1c584-243">Vertical List</span></span>
* <span data-ttu-id="1c584-244">垂直スクロール バー</span><span class="sxs-lookup"><span data-stu-id="1c584-244">Vertical Scrollbar</span></span>

<span data-ttu-id="1c584-245">アプリケーションによって独自の顧客ウィジェットを簡単に作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="1c584-245">It’s easy for the application to create its own customer widgets as well.</span></span>

### <a name="complete-low-level-drawing-api"></a><span data-ttu-id="1c584-246">完全な低レベル描画 API</span><span class="sxs-lookup"><span data-stu-id="1c584-246">Complete low-level drawing API</span></span>

<span data-ttu-id="1c584-247">Azure RTOS GUIX には、堅牢なキャンバス描画 API が用意されています。これにより、アプリケーションは複雑なグラフィカル形状をレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="1c584-247">Azure RTOS GUIX provides a robust canvas drawing API, allowing the application to render complex graphical shapes.</span></span>

<span data-ttu-id="1c584-248">すべての関数が、高い色深度ターゲット上でのアンチエイリアシングをサポートしており、純色塗り、ピクセルマップ パターン塗りを含め、すべての図形の輪郭を塗りつぶすことができます。</span><span class="sxs-lookup"><span data-stu-id="1c584-248">All functions support anti-aliasing on high color depth targets, and all shapes can be filled our outlined, including solid and pixelmap pattern fills.</span></span> <span data-ttu-id="1c584-249">16 bpp 以上の高い色深度で実行する場合は、すべての描画プリミティブによって、ブラシ アルファがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="1c584-249">All drawing primitives support brush alpha when running at 16 bpp and higher color depth.</span></span> <span data-ttu-id="1c584-250">描画関数は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1c584-250">Drawing functions include:</span></span>

* <span data-ttu-id="1c584-251">弧描画</span><span class="sxs-lookup"><span data-stu-id="1c584-251">Arc Draw</span></span>
* <span data-ttu-id="1c584-252">円描画</span><span class="sxs-lookup"><span data-stu-id="1c584-252">Circle Draw</span></span>
* <span data-ttu-id="1c584-253">線描画</span><span class="sxs-lookup"><span data-stu-id="1c584-253">Line Draw</span></span>
* <span data-ttu-id="1c584-254">円描画</span><span class="sxs-lookup"><span data-stu-id="1c584-254">Pie Draw</span></span>
* <span data-ttu-id="1c584-255">ピクセルマップ Blend</span><span class="sxs-lookup"><span data-stu-id="1c584-255">Pixelmap Blend</span></span>
* <span data-ttu-id="1c584-256">ピクセルマップ タイル</span><span class="sxs-lookup"><span data-stu-id="1c584-256">Pixelmap Tile</span></span>
* <span data-ttu-id="1c584-257">多角形描画</span><span class="sxs-lookup"><span data-stu-id="1c584-257">Polygon Draw</span></span>
* <span data-ttu-id="1c584-258">テキスト描画</span><span class="sxs-lookup"><span data-stu-id="1c584-258">Text Draw</span></span>
* <span data-ttu-id="1c584-259">弦描画</span><span class="sxs-lookup"><span data-stu-id="1c584-259">Chord Draw</span></span>
* <span data-ttu-id="1c584-260">楕円描画</span><span class="sxs-lookup"><span data-stu-id="1c584-260">Ellipse Draw</span></span>
* <span data-ttu-id="1c584-261">ピクセル描画</span><span class="sxs-lookup"><span data-stu-id="1c584-261">Pixel Draw</span></span>
* <span data-ttu-id="1c584-262">ピクセルマップ描画</span><span class="sxs-lookup"><span data-stu-id="1c584-262">Pixelmap Draw</span></span>
* <span data-ttu-id="1c584-263">ピクセルマップ回転</span><span class="sxs-lookup"><span data-stu-id="1c584-263">Pixelmap Rotate</span></span>
* <span data-ttu-id="1c584-264">四角形描画</span><span class="sxs-lookup"><span data-stu-id="1c584-264">Rectangle Draw</span></span>
* <span data-ttu-id="1c584-265">テキスト Blend</span><span class="sxs-lookup"><span data-stu-id="1c584-265">Text Blend</span></span>

### <a name="default-free-fonts-and-easy-to-add-more"></a><span data-ttu-id="1c584-266">既定の無料フォントで、さらに簡単に追加</span><span class="sxs-lookup"><span data-stu-id="1c584-266">Default free fonts and easy to add more</span></span>

<span data-ttu-id="1c584-267">Azure RTOS GUIX には、無料の TrueType フォント セットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1c584-267">Azure RTOS GUIX provides a free set of TrueType fonts.</span></span> <span data-ttu-id="1c584-268">開発者は、必要に応じて TrueType フォントを追加できます。</span><span class="sxs-lookup"><span data-stu-id="1c584-268">Developers can add additional TrueType fonts as desired.</span></span>

<span data-ttu-id="1c584-269">Azure RTOS GUIX フォント形式は、8 bpp アンチエイリアシング、4 bpp アンチエイリアシング、および 1 bpp モノクロ フォントをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="1c584-269">The Azure RTOS GUIX font format supports 8bpp anti-aliasing, 4bpp anti-aliasing, and 1bpp monochrome fonts.</span></span> <span data-ttu-id="1c584-270">リソースに制約があるほとんどのアプリケーションについて、TrueType フォントは、Azure RTOS GUIX によって GUIX Studio デスクトップ ツールを使用して、圧縮されたビットマップ形式に事前にレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="1c584-270">For the most resource-constrained applications, Azure RTOS GUIX pre-renders the TrueType fonts to a compressed bitmap format using our GUIX Studio desktop tool.</span></span>

### <a name="custom-jpg-and-png-decoder-implementation"></a><span data-ttu-id="1c584-271">カスタム JPG および PNG デコーダーの実装</span><span class="sxs-lookup"><span data-stu-id="1c584-271">Custom JPG and PNG decoder implementation</span></span>

<span data-ttu-id="1c584-272">カスタム JPG および PNG デコーダーの実装 JPG および PNG ファイル デコーダーの実装。</span><span class="sxs-lookup"><span data-stu-id="1c584-272">Custom JPG and PNG decoder implementation JPG and PNG file decoder implementation.</span></span> <span data-ttu-id="1c584-273">この実装は、Azure RTOS GUIX 対応ピクセルマップ形式イメージの色空間の変換、ディザリング、およびランタイム作成をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="1c584-273">This implementation supports color space conversion, dithering, and runtime creation of Azure RTOS GUIX-compatible pixelmap format images.</span></span>

### <a name="extensive-display-and-touchscreen-support"></a><span data-ttu-id="1c584-274">さまざまなディスプレイとタッチスクリーンのサポート</span><span class="sxs-lookup"><span data-stu-id="1c584-274">Extensive display and touchscreen support</span></span>

<span data-ttu-id="1c584-275">Azure RTOS GUIX には、ほぼすべての色形式 (1 bpp モノクロ、8 bpp パレット、8 bpp 3:3:2 形式、</span><span class="sxs-lookup"><span data-stu-id="1c584-275">Azure RTOS GUIX provides generic display drivers for nearly all color formats, including 1bpp monochrome, 8 bpp palette, 8 bpp 3:3:2 format,</span></span>

<span data-ttu-id="1c584-276">16 bpp 565 rgb 形式、16 bpp 4:4:4:4 形式、32 bpp x:r:g:b 形式、および 32 bpp:r:g:b 形式など) に対応する汎用ディスプレイ ドライバーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1c584-276">16 bpp 565 rgb format, 16 bpp 4:4:4:4 format, 32 bpp x:r:g:b format, and 32 bpp a:r:g:b format.</span></span> <span data-ttu-id="1c584-277">さらに、Azure RTOS GUIX は、最も一般的な多くの LCD コントローラーおよびハードウェア アクセラレータ (ST ChromeArt、Renesas Synergy など) に統合されています。</span><span class="sxs-lookup"><span data-stu-id="1c584-277">In addition, Azure RTOS GUIX is integrated with many of the most popular LCD controllers and hardware accelerators (ST ChromeArt, Renesas Synergy, etc.).</span></span>

<span data-ttu-id="1c584-278">Azure RTOS GUIX は、タッチスクリーン (ジェスチャ サポートを含む)、ペン、および仮想キーボード入力デバイスを完全にサポートしています。</span><span class="sxs-lookup"><span data-stu-id="1c584-278">Azure RTOS GUIX fully supports touchscreen (including gesture support), pen, and virtual keyboard input devices.</span></span>

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a><span data-ttu-id="1c584-279">Azure RTOS GUIX Studio デスクトップ WYSIWYG ツール</span><span class="sxs-lookup"><span data-stu-id="1c584-279">Azure RTOS GUIX Studio desktop WYSIWYG tool</span></span>

<span data-ttu-id="1c584-280">Azure RTOS GUIX には、完全な WYSIWYG スクリーン デザイン環境が用意されています。これにより、ユーザーは、GUI スクリーンの作成に使用するグラフィカル要素をドラッグアンドドロップできます。</span><span class="sxs-lookup"><span data-stu-id="1c584-280">Azure RTOS GUIX Studio provides a complete WYSIWYG screen design environment which allows the user to drag-and-drop graphical elements used to build the GUI screens.</span></span> <span data-ttu-id="1c584-281">Azure RTOS GUIX Studio によって、Azure RTOS GUIX ライブラリと互換性がある C コードが自動的に生成されます。これはターゲット上でコンパイルおよび実行できます。</span><span class="sxs-lookup"><span data-stu-id="1c584-281">Azure RTOS GUIX Studio automatically generates C code compatible with the Azure RTOS GUIX library, ready to be compiled and run on the target.</span></span> <span data-ttu-id="1c584-282">開発者は、統合された Azure RTOS GUIX Studio フォント生成ツールを使用して、アプリケーション内で使用できるレンダリング済みフォントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1c584-282">Developers can produce pre-rendered fonts for use within an application using the integrated Azure RTOS GUIX Studio font generation tool.</span></span> <span data-ttu-id="1c584-283">フォントは、モノクロまたはアンチエイリアス形式で生成でき、ターゲット上の領域を節約するために最適化されています。</span><span class="sxs-lookup"><span data-stu-id="1c584-283">Fonts can be generated in monochrome or anti-aliased formats, and are optimized to save space on the target.</span></span> <span data-ttu-id="1c584-284">フォントには、多言語アプリケーション向け Unicode 文字などの任意の文字セットを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="1c584-284">Fonts can include any set of characters, including Unicode characters for multi-lingual applications.</span></span>

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

<span data-ttu-id="1c584-285">Azure RTOS GUIX により、PNG または JPG ファイルからのグラフィックスのインポートが容易になります。また、ターゲット システム上で使用するために、圧縮された Azure RTOS GUIX ピクセルマップに変換されます。</span><span class="sxs-lookup"><span data-stu-id="1c584-285">Azure RTOS GUIX Studio facilitates the import of graphics from PNG or JPG files with conversion to compressed Azure RTOS GUIX Pixelmaps for use on the target system.</span></span> <span data-ttu-id="1c584-286">Azure RTOS GUIX ウィジェットの種類の多くが、ユーザー グラフィックスを組み込んで外観をカスタマイズできるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="1c584-286">Many of the Azure RTOS GUIX widget types are designed to incorporate user graphics for a custom look and feel.</span></span> <span data-ttu-id="1c584-287">さらに、Azure RTOS GUIX Studio を使用すると、Azure RTOS GUIX ウィジェットで使用される既定の色や描画スタイルをカスタマイズできるため、開発者が Azure RTOS GUIX の外観を非常に簡単に調整することができます。</span><span class="sxs-lookup"><span data-stu-id="1c584-287">In addition, Azure RTOS GUIX Studio allows customization of the default colors and drawing styles used by the Azure RTOS GUIX widgets, allowing developers to tune the appearance of Azure RTOS GUIX very easily.</span></span> <span data-ttu-id="1c584-288">アプリケーション文字列の生成とメンテナンスも、Azure RTOS GUIX Studio の組み込み機能です。</span><span class="sxs-lookup"><span data-stu-id="1c584-288">Generation and maintenance of application strings is another built-in facility of Azure RTOS GUIX Studio.</span></span> <span data-ttu-id="1c584-289">これにより、開発者がアプリケーションを設計したときに使用した開発言語以外の言語のサポートを、製品リリース後にすばやく簡単に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="1c584-289">This enables developers to design an application using one language for developing, and quickly and easily add support for additional languages after the product is released.</span></span> <span data-ttu-id="1c584-290">完全な Azure RTOS GUIX アプリケーションを、Azure RTOS GUIX Studio 環境内の PC デスクトップ上で実行できるため、GUI の概念、スクリーン フローのテスト、およびスクリーン切り替えとアニメーション確認を、迅速かつ簡単に生成し、デモンストレーションを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1c584-290">A complete Azure RTOS GUIX application can be executed on a PC desktop within the Azure RTOS GUIX Studio environment, allowing a quick and easy generation and demonstration of GUI concepts, testing of screen flows, and observation of screen transitions and animations.</span></span> <span data-ttu-id="1c584-291">完成したデザインはターゲット対応 C データ構造としてエクスポートでき、Azure RTOS GUIX ライブラリと Azure RTOS ThreadX ライブラリでコンパイルし、リンクすることができます。</span><span class="sxs-lookup"><span data-stu-id="1c584-291">When completed, a design can be exported as target-ready C data structures, ready to be compiled and linked with the Azure RTOS GUIX and Azure RTOS ThreadX libraries.</span></span>

<span data-ttu-id="1c584-292">Azure RTOS GUIX と Azure RTOS GUIX Studio は、複数のリソース テーマをサポートしており、実行時、アプリケーションに簡単にスキンを再適用できます。</span><span class="sxs-lookup"><span data-stu-id="1c584-292">Azure RTOS GUIX and Azure RTOS GUIX Studio support multiple resource themes, allowing an application to be easily reskinned at run-time.</span></span> <span data-ttu-id="1c584-293">実行時に 1 つのシンプルな API を使用して、フォント、色、およびピクセルマップを変更できます。</span><span class="sxs-lookup"><span data-stu-id="1c584-293">Fonts, colors, and pixelmaps can be changed at run-time with one simple API.</span></span>

<span data-ttu-id="1c584-294">GUIX Studio の詳細をご確認ください</span><span class="sxs-lookup"><span data-stu-id="1c584-294">Learn more about GUIX Studio</span></span>

### <a name="complete-win32-simulation"></a><span data-ttu-id="1c584-295">完全な Win32 シミュレーション</span><span class="sxs-lookup"><span data-stu-id="1c584-295">Complete Win32 simulation</span></span>

<span data-ttu-id="1c584-296">Azure RTOS GUIX は、ターゲット ボード上で動作するものとまったく同じ描画ライブラリを使用して、Windows PC 上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="1c584-296">Azure RTOS GUIX runs on a Windows PC, using exactly the same drawing library that runs on the target board.</span></span> <span data-ttu-id="1c584-297">Azure RTOS GUIX を使用すると、PC 上で GUI アプリケーションをビルドして実行し、ターゲット上で同じアプリケーション コードを使用して、デバッグ、迅速なプロトタイプ作成、デモンストレーション、WYSIWYG ターゲット操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1c584-297">With Azure RTOS GUIX, you can build and run a GUI application on the PC, and use the same application code on your target for debugging, rapid prototyping, demonstration, and WYSIWYG target operation.</span></span>

### <a name="advanced-technology"></a><span data-ttu-id="1c584-298">高度なテクノロジ</span><span class="sxs-lookup"><span data-stu-id="1c584-298">Advanced technology</span></span>

* <span data-ttu-id="1c584-299">Azure RTOS GUIX の高度なテクノロジには、次のものが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="1c584-299">Azure RTOS GUIX's advanced technology incorporates:</span></span>
* <span data-ttu-id="1c584-300">アルファ ブレンド</span><span class="sxs-lookup"><span data-stu-id="1c584-300">Alpha blending</span></span>
* <span data-ttu-id="1c584-301">アンチエイリアシング</span><span class="sxs-lookup"><span data-stu-id="1c584-301">Anti-Aliasing</span></span>
* <span data-ttu-id="1c584-302">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="1c584-302">Automatic scaling</span></span>
* <span data-ttu-id="1c584-303">ビットマップ圧縮</span><span class="sxs-lookup"><span data-stu-id="1c584-303">Bitmap compression</span></span>
* <span data-ttu-id="1c584-304">キャンバス ブレンド</span><span class="sxs-lookup"><span data-stu-id="1c584-304">Canvas blending</span></span>
* <span data-ttu-id="1c584-305">カスタム ウィジェット サポート</span><span class="sxs-lookup"><span data-stu-id="1c584-305">Custom widget support</span></span>
* <span data-ttu-id="1c584-306">遅延描画サポート</span><span class="sxs-lookup"><span data-stu-id="1c584-306">Deferred drawing support</span></span>
* <span data-ttu-id="1c584-307">ディザリング サポート</span><span class="sxs-lookup"><span data-stu-id="1c584-307">Dithering support</span></span>
* <span data-ttu-id="1c584-308">エンディアン ニュートラル プログラミング</span><span class="sxs-lookup"><span data-stu-id="1c584-308">Endian neutral programming</span></span>
* <span data-ttu-id="1c584-309">ハードウェア アクセラレータ サポート</span><span class="sxs-lookup"><span data-stu-id="1c584-309">Hardware accelerator support</span></span>
* <span data-ttu-id="1c584-310">多言語サポートと UTF-8 エンコード</span><span class="sxs-lookup"><span data-stu-id="1c584-310">Multilingual support and UTF-8 encoding</span></span>
* <span data-ttu-id="1c584-311">複数ディスプレイとキャンバス サポート</span><span class="sxs-lookup"><span data-stu-id="1c584-311">Multiple display and canvas support</span></span>
* <span data-ttu-id="1c584-312">最適化されたクリッピング、描画、およびイベント処理</span><span class="sxs-lookup"><span data-stu-id="1c584-312">Optimized clipping, drawing, and event handling</span></span>
* <span data-ttu-id="1c584-313">ランタイム JPEG および PNG デコーダー</span><span class="sxs-lookup"><span data-stu-id="1c584-313">Runtime JPEG and PNG decoder</span></span>
* <span data-ttu-id="1c584-314">スキニングとテーマ</span><span class="sxs-lookup"><span data-stu-id="1c584-314">Skinning and Themes</span></span>
* <span data-ttu-id="1c584-315">モノクロから 32 ビット true-color (アルファ付き) グラフィックス形式までをサポート</span><span class="sxs-lookup"><span data-stu-id="1c584-315">Supports monochrome through 32-bit true-color with alpha graphics formats</span></span>
* <span data-ttu-id="1c584-316">切り替え、スプライト、およびアニメーションのサポート</span><span class="sxs-lookup"><span data-stu-id="1c584-316">Transitions, Sprites, and Animation support</span></span>
* <span data-ttu-id="1c584-317">Win32 シミュレーション</span><span class="sxs-lookup"><span data-stu-id="1c584-317">Win32 simulation</span></span>
* <span data-ttu-id="1c584-318">ウィンドウ管理 (ビューポートと Z オーダーのメンテナンスを含む)</span><span class="sxs-lookup"><span data-stu-id="1c584-318">Window management including Viewports and Z-order maintenance</span></span>
