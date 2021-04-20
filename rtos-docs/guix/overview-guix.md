---
title: Azure RTOS GUIX および Azure RTOS GUIX Studio について
description: Azure RTOS GUIX は、埋め込みシステム開発者のニーズに対応するために作成された、プロフェッショナル品質のパッケージです。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0d0ff37784673f851ab918e20b255d19ddf98b0f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811909"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a><span data-ttu-id="78f41-103">Azure RTOS GUIX および Azure RTOS GUIX Studio の概要</span><span class="sxs-lookup"><span data-stu-id="78f41-103">Overview of Azure RTOS GUIX and Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="78f41-104">Azure GUIX 埋め込み GUI は、深く埋め込まれたリアルタイム IoT アプリケーション向けに特別に設計された、Microsoft の高度な商用 GUI ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="78f41-104">Azure GUIX embedded GUI is Microsoft’s advanced, industrial grade GUI solution designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="78f41-105">また、Microsoft は、Azure RTOS GUIX Studio という完全な機能を備えた WYSIWYG デスクトップ デザイン ツールも提供しており、開発者が、デスクトップ上で自身の GUI をデザインし、Azure RTOS GUIX 埋め込み GUI コードを生成して、それをターゲットにエクスポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="78f41-105">Microsoft also provides a full-featured WYSIWYG desktop design tool named Azure RTOS GUIX Studio, which allows developers to design their GUI on the desktop and generate Azure RTOS GUIX embedded GUI code that can then be exported to the target.</span></span> <span data-ttu-id="78f41-106">Azure RTOS GUIX は Azure RTOS ThreadX RTOS と完全に統合されており、Azure RTOS ThreadX でサポートされている同じプロセッサの多くで利用できます。</span><span class="sxs-lookup"><span data-stu-id="78f41-106">Azure RTOS GUIX is fully integrated with Azure RTOS ThreadX RTOS and is available for many of the same processors supported by Azure RTOS ThreadX.</span></span> <span data-ttu-id="78f41-107">これらすべてを小さな専有領域、高速処理、および優れた操作性と組み合わせることで、Azure RTOS GUIX は、ユーザー インターフェイスを必要とする最も要求の厳しい埋め込み型 IoT アプリケーションに最適な選択肢となります。</span><span class="sxs-lookup"><span data-stu-id="78f41-107">All of this combined with an extremely small footprint, fast execution, and superior ease-of-use, make Azure RTOS GUIX the ideal choice for the most demanding embedded IoT applications requiring a user interface.</span></span> 

## <a name="azure-rtos-guix-api"></a><span data-ttu-id="78f41-108">Azure RTOS GUIX API</span><span class="sxs-lookup"><span data-stu-id="78f41-108">Azure RTOS GUIX API</span></span>

### <a name="intuitive-and-consistent-api"></a><span data-ttu-id="78f41-109">直感的で一貫性のある API</span><span class="sxs-lookup"><span data-stu-id="78f41-109">Intuitive and consistent API</span></span>

* <span data-ttu-id="78f41-110">名詞 - 動詞の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="78f41-110">Noun-verb naming convention</span></span>

* <span data-ttu-id="78f41-111">すべての API の先頭を *gx_* にして、Azure RTOS GUIX として簡単に識別</span><span class="sxs-lookup"><span data-stu-id="78f41-111">All APIs have leading *gx_* to easily identify as Azure RTOS GUIX</span></span>

* <span data-ttu-id="78f41-112">イベントドリブン プログラミング モデル (API)</span><span class="sxs-lookup"><span data-stu-id="78f41-112">Event-driven programming model (API)</span></span>

* <span data-ttu-id="78f41-113">必要に応じて直接的なキャンバス描画を完全サポート</span><span class="sxs-lookup"><span data-stu-id="78f41-113">Full support for direct canvas drawing when needed</span></span>

* <span data-ttu-id="78f41-114">Azure RTOS GUIX Studio で生成されたコードの操作が簡単</span><span class="sxs-lookup"><span data-stu-id="78f41-114">Simple to interact with Azure RTOS GUIX Studio generated code</span></span>

* <span data-ttu-id="78f41-115">線、四角形、多角形などの API</span><span class="sxs-lookup"><span data-stu-id="78f41-115">APIs for line, rectangle, polygon, etc.</span></span>

* <span data-ttu-id="78f41-116">円、弧、弦、楕円などの API</span><span class="sxs-lookup"><span data-stu-id="78f41-116">APIs for circle, arc, pie, chord, ellipse, etc.</span></span>

* <span data-ttu-id="78f41-117">テキスト描画、配置の API</span><span class="sxs-lookup"><span data-stu-id="78f41-117">APIs for text drawing and positioning</span></span>

* <span data-ttu-id="78f41-118">アンチエイリアシング、テクスチャで塗りつぶし、純色で塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="78f41-118">Anti-aliasing, texture fills, and solid fills</span></span>

* <span data-ttu-id="78f41-119">スクリーンおよびウィジェットの作成と変更のための API</span><span class="sxs-lookup"><span data-stu-id="78f41-119">APIs for creating and modifing screens and widgets</span></span>

### <a name="azure-rtos-guix-studio-generated-files"></a><span data-ttu-id="78f41-120">Azure RTOS GUIX Studio で生成されたファイル</span><span class="sxs-lookup"><span data-stu-id="78f41-120">Azure RTOS GUIX Studio Generated Files</span></span>

* <span data-ttu-id="78f41-121">自動生成された ANSI C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="78f41-121">Automatically generated ANSI C source files</span></span>

* <span data-ttu-id="78f41-122">アプリケーション ソフトウェアをレイアウトの詳細から分離</span><span class="sxs-lookup"><span data-stu-id="78f41-122">Insulates application software from layout details</span></span>

* <span data-ttu-id="78f41-123">UI デザインに必要なフォントとイメージの挿入</span><span class="sxs-lookup"><span data-stu-id="78f41-123">Includes fonts and images required by UI design</span></span>

* <span data-ttu-id="78f41-124">アプリケーション コードを使用してコンパイルされた生成ファイル</span><span class="sxs-lookup"><span data-stu-id="78f41-124">Generated files compiled with application code</span></span>

* <span data-ttu-id="78f41-125">アプリケーション ロジックに影響を与えずにスクリーン レイアウトを更新可能</span><span class="sxs-lookup"><span data-stu-id="78f41-125">Screen layout can be updated without affecting application logic</span></span>

* <span data-ttu-id="78f41-126">リソース ID により言語とテーマの独立性を確保</span><span class="sxs-lookup"><span data-stu-id="78f41-126">Resource IDs create language and theme independence</span></span>

* <span data-ttu-id="78f41-127">ユーザーが指定したカスタム描画およびイベント処理関数</span><span class="sxs-lookup"><span data-stu-id="78f41-127">User-supplied custom drawing and event processing functions</span></span>

### <a name="widget-library"></a><span data-ttu-id="78f41-128">ウィジェット ライブラリ</span><span class="sxs-lookup"><span data-stu-id="78f41-128">Widget library</span></span>

* <span data-ttu-id="78f41-129">事前定義されているがカスタマイズ可能な一連の共通インターフェイス要素</span><span class="sxs-lookup"><span data-stu-id="78f41-129">Pre-defined but customizable set of common interface elements</span></span>

* <span data-ttu-id="78f41-130">非常に小さく、コンパクト、かつ効率的</span><span class="sxs-lookup"><span data-stu-id="78f41-130">Extremely small, compact, and efficient</span></span>

* <span data-ttu-id="78f41-131">ライブラリにボタン、ゲージ、リスト、ウィンドウ、スクロール、スライダー、進行状況バー、プロンプトなどが含まれる</span><span class="sxs-lookup"><span data-stu-id="78f41-131">Library includes button, gauge, list, window, scroll, slider, progress bar, prompt and many more</span></span>

* <span data-ttu-id="78f41-132">完全にカスタマイズ可能な描画と外観</span><span class="sxs-lookup"><span data-stu-id="78f41-132">Fully customizable drawing and appearance</span></span>

* <span data-ttu-id="78f41-133">完全にカスタマイズ可能な操作とイベント処理</span><span class="sxs-lookup"><span data-stu-id="78f41-133">Fully customizable operation and event handling</span></span>

* <span data-ttu-id="78f41-134">使用されるウィジェットのみがアプリケーション ソフトウェアとリンク</span><span class="sxs-lookup"><span data-stu-id="78f41-134">Only the widgets used are linked with application software</span></span>

### <a name="math-and-utilities"></a><span data-ttu-id="78f41-135">数式とユーティリティ</span><span class="sxs-lookup"><span data-stu-id="78f41-135">Math and utilities</span></span>

* <span data-ttu-id="78f41-136">正弦、余弦、逆正弦、逆余弦、正接、平方根の関数</span><span class="sxs-lookup"><span data-stu-id="78f41-136">Functions for sin, cos, arcsin, arccos, tangent, square root</span></span>

* <span data-ttu-id="78f41-137">スクリーン領域を操作するための関数</span><span class="sxs-lookup"><span data-stu-id="78f41-137">Functions for manipulating screen regions</span></span>

* <span data-ttu-id="78f41-138">システムの構成と起動</span><span class="sxs-lookup"><span data-stu-id="78f41-138">System configuration and startup</span></span>

* <span data-ttu-id="78f41-139">メモリ プールの定義 (省略可能)</span><span class="sxs-lookup"><span data-stu-id="78f41-139">Memory pool definition (optional)</span></span>

* <span data-ttu-id="78f41-140">タイマー管理</span><span class="sxs-lookup"><span data-stu-id="78f41-140">Timer Management</span></span>

* <span data-ttu-id="78f41-141">アニメーション管理</span><span class="sxs-lookup"><span data-stu-id="78f41-141">Animation Management</span></span>

* <span data-ttu-id="78f41-142">ダーティ リストのメンテナンス</span><span class="sxs-lookup"><span data-stu-id="78f41-142">Dirty list maintenance</span></span>

### <a name="image-processing"></a><span data-ttu-id="78f41-143">画像処理</span><span class="sxs-lookup"><span data-stu-id="78f41-143">Image processing</span></span>

* <span data-ttu-id="78f41-144">jpeg および png イメージのランタイム デコード用の関数</span><span class="sxs-lookup"><span data-stu-id="78f41-144">Functions for runtime decode of jpeg and png images</span></span>

* <span data-ttu-id="78f41-145">ディザリングおよび色空間の変換の適用</span><span class="sxs-lookup"><span data-stu-id="78f41-145">Apply dithering and color space conversion</span></span>

* <span data-ttu-id="78f41-146">イメージの回転</span><span class="sxs-lookup"><span data-stu-id="78f41-146">Image rotation</span></span>

* <span data-ttu-id="78f41-147">イメージのスケーリング</span><span class="sxs-lookup"><span data-stu-id="78f41-147">Image scaling</span></span>

* <span data-ttu-id="78f41-148">イメージのブレンド</span><span class="sxs-lookup"><span data-stu-id="78f41-148">Image blending</span></span>

### <a name="event-processing"></a><span data-ttu-id="78f41-149">イベント処理</span><span class="sxs-lookup"><span data-stu-id="78f41-149">Event processing</span></span>

* <span data-ttu-id="78f41-150">アイドル時に Azure RTOS GUIX スレッドを自動停止</span><span class="sxs-lookup"><span data-stu-id="78f41-150">Automatically suspends Azure RTOS GUIX thread when idle</span></span>

* <span data-ttu-id="78f41-151">UI デザインでよく使用されるイベントドリブン プログラミング デル</span><span class="sxs-lookup"><span data-stu-id="78f41-151">Event-driven programming model popular in UI design</span></span>

* <span data-ttu-id="78f41-152">入力ドライバーを Azure RTOS GUIX 描画スレッドから分離</span><span class="sxs-lookup"><span data-stu-id="78f41-152">Insulates input drivers from Azure RTOS GUIX drawing thread</span></span>

* <span data-ttu-id="78f41-153">イベントを送受信するための関数</span><span class="sxs-lookup"><span data-stu-id="78f41-153">Functions for sending and receiving events</span></span>

* <span data-ttu-id="78f41-154">すべての Azure RTOS GUIX ウィジェットの種類に対する事前定義済みのイベントの種類</span><span class="sxs-lookup"><span data-stu-id="78f41-154">Pre-defined event types for all Azure RTOS GUIX widget types</span></span>

* <span data-ttu-id="78f41-155">サポートされているユーザー定義カスタム イベント</span><span class="sxs-lookup"><span data-stu-id="78f41-155">User-defined custom events supported</span></span>

### <a name="canvas-processing"></a><span data-ttu-id="78f41-156">キャンバスの処理</span><span class="sxs-lookup"><span data-stu-id="78f41-156">Canvas processing</span></span>

* <span data-ttu-id="78f41-157">クリッピングと Z オーダーのメンテナンス</span><span class="sxs-lookup"><span data-stu-id="78f41-157">Clipping and Z-Order maintenance</span></span>

* <span data-ttu-id="78f41-158">ウィジェット ライブラリをハードウェアの詳細から分離</span><span class="sxs-lookup"><span data-stu-id="78f41-158">Insulates widget library from hardware details</span></span>

* <span data-ttu-id="78f41-159">アプリケーションをハードウェアの詳細から分離</span><span class="sxs-lookup"><span data-stu-id="78f41-159">Insulates application from hardware details</span></span>

* <span data-ttu-id="78f41-160">ダーティ領域の自動バックグラウンド更新</span><span class="sxs-lookup"><span data-stu-id="78f41-160">Automatic background refresh of dirty areas</span></span>

* <span data-ttu-id="78f41-161">レイヤーとブレンドがサポートされている複数のキャンバス</span><span class="sxs-lookup"><span data-stu-id="78f41-161">Multiple canvases with layering and blending supported</span></span>

* <span data-ttu-id="78f41-162">アプリケーション ソフトウェアによる直接呼び出しが可能</span><span class="sxs-lookup"><span data-stu-id="78f41-162">Can be invoked directly by the application software</span></span>

### <a name="input-device-drivers"></a><span data-ttu-id="78f41-163">入力デバイス ドライバー</span><span class="sxs-lookup"><span data-stu-id="78f41-163">Input device driver(s)</span></span>

* <span data-ttu-id="78f41-164">ハードウェア固有のサポート、Azure RTOS GUIX およびハードウェアの詳細から切り離されたアプリケーション</span><span class="sxs-lookup"><span data-stu-id="78f41-164">Hardware-specific support, Azure RTOS GUIX and application insulated from hardware details</span></span>

* <span data-ttu-id="78f41-165">抵抗膜方式タッチ、静電容量タッチ、およびキーパッドのサポート</span><span class="sxs-lookup"><span data-stu-id="78f41-165">Resistive Touch, Cap Touch, and keypad supported</span></span>

* <span data-ttu-id="78f41-166">Azure RTOS GUIX イベント キューに渡される入力イベント</span><span class="sxs-lookup"><span data-stu-id="78f41-166">Input events passed to Azure RTOS GUIX event queue</span></span>

### <a name="display-drivers"></a><span data-ttu-id="78f41-167">ディスプレイ ドライバー</span><span class="sxs-lookup"><span data-stu-id="78f41-167">Display drivers</span></span>

* <span data-ttu-id="78f41-168">ハードウェア固有のサポート</span><span class="sxs-lookup"><span data-stu-id="78f41-168">Hardware-specific support</span></span>

* <span data-ttu-id="78f41-169">すべての色深度と色形式に提供される汎用ドライバー</span><span class="sxs-lookup"><span data-stu-id="78f41-169">Generic drivers provided for all color depth and formats</span></span>

* <span data-ttu-id="78f41-170">使用可能なグラフィックス アクセラレータを使用するようにカスタマイズ済み</span><span class="sxs-lookup"><span data-stu-id="78f41-170">Customized to utilize available graphics accelerators</span></span>

### <a name="target-hardware"></a><span data-ttu-id="78f41-171">ターゲット ハードウェア</span><span class="sxs-lookup"><span data-stu-id="78f41-171">Target hardware</span></span>

* <span data-ttu-id="78f41-172">ほぼすべてのグラフィカル出力対応ハードウェアが GUIX に対応</span><span class="sxs-lookup"><span data-stu-id="78f41-172">Nearly any hardware capable of graphical output Is compatible with GUIX</span></span>

* <span data-ttu-id="78f41-173">複数の物理ディスプレイのサポート</span><span class="sxs-lookup"><span data-stu-id="78f41-173">Multiple physical displays supported</span></span>

* <span data-ttu-id="78f41-174">最小 RAM とフラッシュの要件</span><span class="sxs-lookup"><span data-stu-id="78f41-174">Minimal RAM and Flash requirements</span></span>

## <a name="create-elegant-user-interfaces"></a><span data-ttu-id="78f41-175">洗練されたユーザー インターフェイスを作成する</span><span class="sxs-lookup"><span data-stu-id="78f41-175">Create Elegant User Interfaces</span></span>

<span data-ttu-id="78f41-176">Azure RTOS GUIX および Azure RTOS GUIX Studio には、洗練された独自のユーザー インターフェイスの作成に必要な機能すべてが用意されています。</span><span class="sxs-lookup"><span data-stu-id="78f41-176">Azure RTOS GUIX and Azure RTOS GUIX Studio provide all the features necessary to create uniquely elegant user interfaces.</span></span> <span data-ttu-id="78f41-177">標準の Azure RTOS GUIX パッケージには、医療デバイス参照、スマート ウォッチ参照、ホーム オートメーション参照、工業制御参照、自動車参照、さまざまなスプライトとアニメーションの例など、各種サンプル ユーザー インターフェイスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="78f41-177">The standard Azure RTOS GUIX package includes various sample user interfaces, including a medical device reference, a smart watch reference, a home automation reference, an industrial control reference, an automotive reference, and various sprite and animation examples.</span></span> <span data-ttu-id="78f41-178">以下の参照例をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="78f41-178">Please click on the reference examples shown below.</span></span>

### <a name="home-automation"></a><span data-ttu-id="78f41-179">ホーム オートメーション</span><span class="sxs-lookup"><span data-stu-id="78f41-179">Home Automation</span></span>

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a><span data-ttu-id="78f41-180">医療</span><span class="sxs-lookup"><span data-stu-id="78f41-180">Medical</span></span>

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a><span data-ttu-id="78f41-181">コンシューマー</span><span class="sxs-lookup"><span data-stu-id="78f41-181">Consumer</span></span>

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a><span data-ttu-id="78f41-182">白物家電</span><span class="sxs-lookup"><span data-stu-id="78f41-182">White Goods</span></span>

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a><span data-ttu-id="78f41-183">自動車</span><span class="sxs-lookup"><span data-stu-id="78f41-183">Automotive</span></span>

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a><span data-ttu-id="78f41-184">工業</span><span class="sxs-lookup"><span data-stu-id="78f41-184">Industrial</span></span>

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

<span data-ttu-id="78f41-185">各 Azure RTOS GUIX 参照には、参照デザインのすべてのグラフィカル要素を定義する、対応する Azure RTOS GUIX Studio プロジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="78f41-185">Each Azure RTOS GUIX reference has a corresponding Azure RTOS GUIX Studio project that defines all the graphical elements of the reference design.</span></span> <span data-ttu-id="78f41-186">参照デザインを変更するのは簡単です。</span><span class="sxs-lookup"><span data-stu-id="78f41-186">Changing a reference design is easy.</span></span> <span data-ttu-id="78f41-187">対応する Azure RTOS GUIX プロジェクトを開き、必要な変更を加え、プロジェクトを保存して、"*プロジェクト*" を選択するだけです。</span><span class="sxs-lookup"><span data-stu-id="78f41-187">Simply open the corresponding Azure RTOS GUIX project, make the desired changes, save the project, and then select *Project*.</span></span>

<span data-ttu-id="78f41-188">すべての出力ファイルを生成して、Azure RTOS GUIX 用の C コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="78f41-188">Generate All Output Files to generate the C code for Azure RTOS GUIX.</span></span> <span data-ttu-id="78f41-189">そして、ターゲット アプリケーションをリビルドし、変更された参照デザインを確認するだけです。</span><span class="sxs-lookup"><span data-stu-id="78f41-189">Then simply rebuild the target application and run to observe the modified reference design.</span></span>

### <a name="small-footprint"></a><span data-ttu-id="78f41-190">小さなメモリ専有領域</span><span class="sxs-lookup"><span data-stu-id="78f41-190">Small-footprint</span></span>

<span data-ttu-id="78f41-191">Azure RTOS GUIX の最小メモリ専有領域は非常に小さく、キャンバスに必要なメモリを含まない基本サポートの場合、フラッシュは 13.2 KB、RAM は 4 KB です。</span><span class="sxs-lookup"><span data-stu-id="78f41-191">Azure RTOS GUIX has a remarkably small minimal footprint of 13.2KB of FLASH and 4KB RAM for basic support, not including the memory required for a canvas.</span></span>

<span data-ttu-id="78f41-192">内部で GRAM と自己更新テクノロジが使用されているディスプレイについては、キャンバス メモリは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="78f41-192">For a display with internal GRAM and self-refresh technology, no canvas memory is required.</span></span> <span data-ttu-id="78f41-193">ただし、描画パフォーマンスを向上させるために、または、ディスプレイに対してローカルな GRAM を使用しないディスプレイ構成の場合は、アプリケーションによってキャンバス メモリ領域が定義されます。</span><span class="sxs-lookup"><span data-stu-id="78f41-193">However, to improve drawing performance, or for a display configuration that does not utilize GRAM local to the display, a canvas memory area is defined by the application.</span></span>

<span data-ttu-id="78f41-194">キャンバスのメモリ要件は、キャンバス サイズと色深度の関数であり、次の式で定義されます。</span><span class="sxs-lookup"><span data-stu-id="78f41-194">Canvas memory requirements are a function of the canvas size as well as the color depth, and are defined by the formula:</span></span>

<span data-ttu-id="78f41-195"><i>キャンバス RAM (バイト) = (x \* y \* (bpp/8))</i></span><span class="sxs-lookup"><span data-stu-id="78f41-195"><i>Canvas RAM (bytes) = (x \* y \* (bpp/8))</i></span></span>

<span data-ttu-id="78f41-196">ここで、"x" と "y" はキャンバス (ディスプレイ) のディメンションです。</span><span class="sxs-lookup"><span data-stu-id="78f41-196">Where “x” and “y” are the dimensions of the canvas (display).</span></span>

<span data-ttu-id="78f41-197">また、ほとんどのアプリケーションでグラフィカル リソースが使用されていますが、これは主要 Azure RTOS GUIX ライブラリ ストレージ要件に含まれていません。</span><span class="sxs-lookup"><span data-stu-id="78f41-197">Most applications also utilize graphical resources, which are not included in the core Azure RTOS GUIX library storage requirements.</span></span> <span data-ttu-id="78f41-198">これらのリソースには、フォント、グラフィカル アイコン (ピクセルマップ)、および静的な文字列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="78f41-198">These resources include fonts, graphical icons (pixelmaps), and static strings.</span></span> <span data-ttu-id="78f41-199">このデータは、const メモリ セクション (フラッシュ) に格納できます。</span><span class="sxs-lookup"><span data-stu-id="78f41-199">This data can be stored in the const memory section (i.e. FLASH).</span></span>

<span data-ttu-id="78f41-200">このメモリ領域のサイズは、使用される一意のフォントの数とサイズ、使用されるグラフィカル アイコンの数とサイズ、出力色形式、各リソースが圧縮データを使用しているかどうかなど、さまざまな要因に依存します。これは、Azure RTOS GUIX が、フォントとピクセルマップの両方のデータの RLE 圧縮をサポートしているためです。</span><span class="sxs-lookup"><span data-stu-id="78f41-200">The size of this memory area is dependent on a number of factors, including the number and size of unique fonts used, the number and size of the graphical icons used, the output color format, and whether or not each resource is using compressed data, since Azure RTOS GUIX supports RLE compression of both font and pixelmap data.</span></span> <span data-ttu-id="78f41-201">各リソースのストレージ要件は、Azure RTOS GUIX Studio アプリケーション内に表示されます。これにより、ユーザーは、アプリケーション リソースによって消費されるフラッシュ メモリの量を追跡および監視できます。</span><span class="sxs-lookup"><span data-stu-id="78f41-201">The storage requirements for each resource are displayed within the Azure RTOS GUIX Studio application, allowing the user to track and monitor the amount of flash memory that will be consumed by the application resources.</span></span>

<span data-ttu-id="78f41-202">Azure RTOS ThreadX と同様に、Azure RTOS GUIX のサイズは、アプリケーションで実際に使用されるサービスに基づいて自動的にスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="78f41-202">Like Azure RTOS ThreadX, the size of Azure RTOS GUIX automatically scales based on the services actually used by the application.</span></span> <span data-ttu-id="78f41-203">これにより、複雑な構成やビルド パラメーターが実質的に不要になるため、開発者の作業がより簡単になります。</span><span class="sxs-lookup"><span data-stu-id="78f41-203">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

### <a name="fast-execution"></a><span data-ttu-id="78f41-204">高速実行</span><span class="sxs-lookup"><span data-stu-id="78f41-204">Fast execution</span></span>

<span data-ttu-id="78f41-205">Azure RTOS GUIX は C で排他的に記述されており、速度を重視して設計されています。</span><span class="sxs-lookup"><span data-stu-id="78f41-205">Azure RTOS GUIX is written exclusively in C and is designed for speed.</span></span> <span data-ttu-id="78f41-206">Azure RTOS GUIX には、最小限の内部関数呼び出しのレイヤーを備えています。</span><span class="sxs-lookup"><span data-stu-id="78f41-206">Azure RTOS GUIX has minimal internal function call layering.</span></span>

<span data-ttu-id="78f41-207">また、Azure RTOS GUIX は、最適化されたクリッピング、描画、およびイベント処理を提供します。</span><span class="sxs-lookup"><span data-stu-id="78f41-207">In addition, Azure RTOS GUIX provides optimized clipping, drawing, and event handling.</span></span> <span data-ttu-id="78f41-208">このすべてと、一般的なパフォーマンス指向の設計理念が、Azure RTOS GUIX が最高のパフォーマンスを実現するうえで役立っています。</span><span class="sxs-lookup"><span data-stu-id="78f41-208">All of this and a general performance-oriented design philosophy help Azure RTOS GUIX achieve the fastest possible performance.</span></span>

### <a name="pre-certified--by-tuv-to-many-safety-standards"></a><span data-ttu-id="78f41-209">TUV による多くの安全標準に対する事前認定</span><span class="sxs-lookup"><span data-stu-id="78f41-209">Pre-certified  by TUV to many safety standards</span></span>

<span data-ttu-id="78f41-210">Azure RTOS GUIX は、IEC-61508 SIL 4、IEC-62304 SW セーフティ クラス C、ISO 26262 ASIL D、および EN 50128 に従って、安全性が重要なシステムでの使用が SGS-TUV Saar によって認定されています。</span><span class="sxs-lookup"><span data-stu-id="78f41-210">Azure RTOS GUIX has been certified by SGS-TUV  Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304  SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="78f41-211">この認定により、「電気、電子、プログラマブル電子安全関連系の機能安全」に関する IEC-61508、IEC-62304、ISO 26262、および EN 50128 の最高の安全性整合性レベルに対応する安全性関連ソフトウェアの開発で Azure RTOS GUIX を使用できることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="78f41-211">The certification confirms that Azure RTOS GUIX can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="78f41-212">ドイツの SGS-Group と TUV Saarland の共同事業を通じて結成された SGS-TUV Saar は、世界中の安全関連システムのための組み込みソフトウェアのテスト、監査、検証、認定を行う、世界有数の公認された独立系企業になりました。</span><span class="sxs-lookup"><span data-stu-id="78f41-212">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="78f41-213">工業安全規格の IEC 61508 と、それから派生したすべての標準 (IEC-62304、ISO 26262 および EN 50128 を含む) は、電気・電子・プログラマブル電子安全関連の医療デバイス、プロセス制御システム、工業機械、自動車および鉄道制御システムの機能安全を保証するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="78f41-213">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

<img alt="SGS-TUV Saar" class="img-responsive" src="https://rtos.com/wp-content/uploads/2017/10/partener-logo-sgs-tuv-saar-2.png"/>

#### <a name="simple-easy-to-use"></a><span data-ttu-id="78f41-214">シンプルで優れた操作性</span><span class="sxs-lookup"><span data-stu-id="78f41-214">Simple, easy-to-use</span></span>

<span data-ttu-id="78f41-215">Azure RTOS GUIX は非常に簡単に使用できますが、Azure RTOS GUIX Studio は、開発者がデスクトップ上で視覚的にデザインし、実際のターゲット上で動作する C コードを生成できるため、さらに使いやすくなっています。</span><span class="sxs-lookup"><span data-stu-id="78f41-215">Azure RTOS GUIX is very simple to use and Azure RTOS GUIX Studio makes it even easier by allowing developers to visually design on the desktop and generate C code that runs on the actual target.</span></span> <span data-ttu-id="78f41-216">アプリケーションが独自のカスタム イベント処理や描画関数を追加して、GUI を完成させることができます。</span><span class="sxs-lookup"><span data-stu-id="78f41-216">Applications can then add their own custom event handling and drawing functions to complete their GUI.</span></span>

<span data-ttu-id="78f41-217">Azure RTOS GUIX API の使い方は簡単です。</span><span class="sxs-lookup"><span data-stu-id="78f41-217">Using the Azure RTOS GUIX API is straightforward.</span></span> <span data-ttu-id="78f41-218">Azure RTOS GUIX API は直感的かつ高機能です。</span><span class="sxs-lookup"><span data-stu-id="78f41-218">The Azure RTOS GUIX API is both intuitive and highly functional.</span></span> <span data-ttu-id="78f41-219">API 名は、他のファイル システム製品でよく見られる略語や大幅に省略された名前ではなく、実際の単語で構成されています。</span><span class="sxs-lookup"><span data-stu-id="78f41-219">The API names are made of real words and not the “alphabet soup” and/or the highly abbreviated names that are so common in other file system products.</span></span> <span data-ttu-id="78f41-220">すべての Azure RTOS GUIX API は、先頭に *gx_* が付き、名詞 - 動詞の名前付け規則に従っています。</span><span class="sxs-lookup"><span data-stu-id="78f41-220">All Azure RTOS GUIX APIs have a leading *gx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="78f41-221">さらに、API 全体に機能的な一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="78f41-221">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="78f41-222">たとえば、ウィジェット制御ブロックを初期化するすべての API に、&lt;widget_type&gt;_create という名前が付けられます。また、各ウィジェットの種類の create function パラメーターは常に同じ順序で定義されます。</span><span class="sxs-lookup"><span data-stu-id="78f41-222">For example, all APIs that initialize a widget control block are named &lt; widget_type&gt;_create, and the create function parameters for each widget type are always defined in the same order.</span></span>

### <a name="comprehensive-set-of-built-in-widgets"></a><span data-ttu-id="78f41-223">包括的な組み込みウィジェット セット</span><span class="sxs-lookup"><span data-stu-id="78f41-223">Comprehensive set of built-in widgets</span></span>

* <span data-ttu-id="78f41-224">Azure RTOS GUIX には、次のような豊富な組み込みウィジェット セットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="78f41-224">Azure RTOS GUIX provides a rich set of built-in widgets, including:</span></span>

* <span data-ttu-id="78f41-225">アコーディオン メニュー</span><span class="sxs-lookup"><span data-stu-id="78f41-225">Accordion Menu</span></span>

* <span data-ttu-id="78f41-226">Button</span><span class="sxs-lookup"><span data-stu-id="78f41-226">Button</span></span>

* <span data-ttu-id="78f41-227">Checkbox</span><span class="sxs-lookup"><span data-stu-id="78f41-227">Checkbox</span></span>

* <span data-ttu-id="78f41-228">円形ゲージ</span><span class="sxs-lookup"><span data-stu-id="78f41-228">Circular Gauge</span></span>

* <span data-ttu-id="78f41-229">ドロップダウン リスト</span><span class="sxs-lookup"><span data-stu-id="78f41-229">Drop Down List</span></span>

* <span data-ttu-id="78f41-230">横方向の一覧</span><span class="sxs-lookup"><span data-stu-id="78f41-230">Horizontal List</span></span>

* <span data-ttu-id="78f41-231">水平スクロールバー ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="78f41-231">Horizontal Scrollbar Window</span></span>

* <span data-ttu-id="78f41-232">アイコン</span><span class="sxs-lookup"><span data-stu-id="78f41-232">Icon</span></span>

* <span data-ttu-id="78f41-233">アイコン ボタン</span><span class="sxs-lookup"><span data-stu-id="78f41-233">Icon Button</span></span>

* <span data-ttu-id="78f41-234">折れ線グラフ</span><span class="sxs-lookup"><span data-stu-id="78f41-234">Line Chart</span></span>

* <span data-ttu-id="78f41-235">メニュー</span><span class="sxs-lookup"><span data-stu-id="78f41-235">Menu</span></span>

* <span data-ttu-id="78f41-236">複数行テキスト ボタン</span><span class="sxs-lookup"><span data-stu-id="78f41-236">Multi Line Text Button</span></span>

* <span data-ttu-id="78f41-237">複数行テキスト入力</span><span class="sxs-lookup"><span data-stu-id="78f41-237">Multi Line Text Input</span></span>

* <span data-ttu-id="78f41-238">複数行テキスト ビュー</span><span class="sxs-lookup"><span data-stu-id="78f41-238">Multi Line Text View</span></span>

* <span data-ttu-id="78f41-239">数値ピクセルマップ プロンプト</span><span class="sxs-lookup"><span data-stu-id="78f41-239">Numeric Pixelmap Prompt</span></span>

* <span data-ttu-id="78f41-240">数値プロンプト</span><span class="sxs-lookup"><span data-stu-id="78f41-240">Numeric Prompt</span></span>

* <span data-ttu-id="78f41-241">数値スクロール ホイール</span><span class="sxs-lookup"><span data-stu-id="78f41-241">Numeric Scroll Wheel</span></span>

* <span data-ttu-id="78f41-242">ピクセルマップ ボタン</span><span class="sxs-lookup"><span data-stu-id="78f41-242">Pixelmap Button</span></span>

* <span data-ttu-id="78f41-243">ピクセル マップ プロンプト</span><span class="sxs-lookup"><span data-stu-id="78f41-243">Pixelmap Prompt</span></span>

* <span data-ttu-id="78f41-244">ピクセルマップ スライダー</span><span class="sxs-lookup"><span data-stu-id="78f41-244">Pixelmap Slider</span></span>

* <span data-ttu-id="78f41-245">ピクセルマップ スプライト</span><span class="sxs-lookup"><span data-stu-id="78f41-245">Pixelmap Sprite</span></span>

* <span data-ttu-id="78f41-246">進行状況バー</span><span class="sxs-lookup"><span data-stu-id="78f41-246">Progress Bar</span></span>

* <span data-ttu-id="78f41-247">Prompt</span><span class="sxs-lookup"><span data-stu-id="78f41-247">Prompt</span></span>

* <span data-ttu-id="78f41-248">放射状の進行状況バー</span><span class="sxs-lookup"><span data-stu-id="78f41-248">Radial Progress Bar</span></span>

* <span data-ttu-id="78f41-249">オプション ボタン</span><span class="sxs-lookup"><span data-stu-id="78f41-249">Radio Button</span></span>

* <span data-ttu-id="78f41-250">スクロール ホイール</span><span class="sxs-lookup"><span data-stu-id="78f41-250">Scroll Wheel</span></span>

* <span data-ttu-id="78f41-251">単一行テキスト入力</span><span class="sxs-lookup"><span data-stu-id="78f41-251">Single Line Text Input</span></span>

* <span data-ttu-id="78f41-252">スライダー</span><span class="sxs-lookup"><span data-stu-id="78f41-252">Slider</span></span>

* <span data-ttu-id="78f41-253">文字列スクロール ホイール</span><span class="sxs-lookup"><span data-stu-id="78f41-253">String Scroll Wheel</span></span>

* <span data-ttu-id="78f41-254">テキスト ボタン</span><span class="sxs-lookup"><span data-stu-id="78f41-254">Text Button</span></span>

* <span data-ttu-id="78f41-255">ツリー ビュー</span><span class="sxs-lookup"><span data-stu-id="78f41-255">Tree View</span></span>

* <span data-ttu-id="78f41-256">縦一覧</span><span class="sxs-lookup"><span data-stu-id="78f41-256">Vertical List</span></span>

* <span data-ttu-id="78f41-257">垂直スクロール バー</span><span class="sxs-lookup"><span data-stu-id="78f41-257">Vertical Scrollbar</span></span>

<span data-ttu-id="78f41-258">アプリケーションによって独自の顧客ウィジェットを簡単に作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="78f41-258">It’s easy for the application to create its own customer widgets as well.</span></span>

### <a name="complete-low-level-drawing-api"></a><span data-ttu-id="78f41-259">完全な低レベル描画 API</span><span class="sxs-lookup"><span data-stu-id="78f41-259">Complete low-level drawing API</span></span>

<span data-ttu-id="78f41-260">Azure RTOS GUIX には、堅牢なキャンバス描画 API が用意されています。これにより、アプリケーションは複雑なグラフィカル形状をレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="78f41-260">Azure RTOS GUIX provides a robust canvas drawing API, allowing the application to render complex graphical shapes.</span></span>

<span data-ttu-id="78f41-261">すべての関数が、高い色深度ターゲット上でのアンチエイリアシングをサポートしており、純色塗り、ピクセルマップ パターン塗りを含め、すべての図形の輪郭を塗りつぶすことができます。</span><span class="sxs-lookup"><span data-stu-id="78f41-261">All functions support anti-aliasing on high color depth targets, and all shapes can be filled our outlined, including solid and pixelmap pattern fills.</span></span> <span data-ttu-id="78f41-262">16 bpp 以上の高い色深度で実行する場合は、すべての描画プリミティブによって、ブラシ アルファがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="78f41-262">All drawing primitives support brush alpha when running at 16 bpp and higher color depth.</span></span> <span data-ttu-id="78f41-263">描画関数は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="78f41-263">Drawing functions include:</span></span>

* <span data-ttu-id="78f41-264">弧描画</span><span class="sxs-lookup"><span data-stu-id="78f41-264">Arc Draw</span></span>

* <span data-ttu-id="78f41-265">円描画</span><span class="sxs-lookup"><span data-stu-id="78f41-265">Circle Draw</span></span>

* <span data-ttu-id="78f41-266">線描画</span><span class="sxs-lookup"><span data-stu-id="78f41-266">Line Draw</span></span>

* <span data-ttu-id="78f41-267">円描画</span><span class="sxs-lookup"><span data-stu-id="78f41-267">Pie Draw</span></span>

* <span data-ttu-id="78f41-268">ピクセルマップ Blend</span><span class="sxs-lookup"><span data-stu-id="78f41-268">Pixelmap Blend</span></span>

* <span data-ttu-id="78f41-269">ピクセルマップ タイル</span><span class="sxs-lookup"><span data-stu-id="78f41-269">Pixelmap Tile</span></span>

* <span data-ttu-id="78f41-270">多角形描画</span><span class="sxs-lookup"><span data-stu-id="78f41-270">Polygon Draw</span></span>

* <span data-ttu-id="78f41-271">テキスト描画</span><span class="sxs-lookup"><span data-stu-id="78f41-271">Text Draw</span></span>

* <span data-ttu-id="78f41-272">弦描画</span><span class="sxs-lookup"><span data-stu-id="78f41-272">Chord Draw</span></span>

* <span data-ttu-id="78f41-273">楕円描画</span><span class="sxs-lookup"><span data-stu-id="78f41-273">Ellipse Draw</span></span>

* <span data-ttu-id="78f41-274">ピクセル描画</span><span class="sxs-lookup"><span data-stu-id="78f41-274">Pixel Draw</span></span>

* <span data-ttu-id="78f41-275">ピクセルマップ描画</span><span class="sxs-lookup"><span data-stu-id="78f41-275">Pixelmap Draw</span></span>

* <span data-ttu-id="78f41-276">ピクセルマップ回転</span><span class="sxs-lookup"><span data-stu-id="78f41-276">Pixelmap Rotate</span></span>

* <span data-ttu-id="78f41-277">四角形描画</span><span class="sxs-lookup"><span data-stu-id="78f41-277">Rectangle Draw</span></span>

* <span data-ttu-id="78f41-278">テキスト Blend</span><span class="sxs-lookup"><span data-stu-id="78f41-278">Text Blend</span></span>

### <a name="default-free-fonts-and-easy-to-add-more"></a><span data-ttu-id="78f41-279">既定の無料フォントで、さらに簡単に追加</span><span class="sxs-lookup"><span data-stu-id="78f41-279">Default free fonts and easy to add more</span></span>

<span data-ttu-id="78f41-280">Azure RTOS GUIX には、無料の TrueType フォント セットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="78f41-280">Azure RTOS GUIX provides a free set of TrueType fonts.</span></span> <span data-ttu-id="78f41-281">開発者は、必要に応じて TrueType フォントを追加できます。</span><span class="sxs-lookup"><span data-stu-id="78f41-281">Developers can add additional TrueType fonts as desired.</span></span>

<span data-ttu-id="78f41-282">Azure RTOS GUIX フォント形式は、8 bpp アンチエイリアシング、4 bpp アンチエイリアシング、および 1 bpp モノクロ フォントをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="78f41-282">The Azure RTOS GUIX font format supports 8bpp anti-aliasing, 4bpp anti-aliasing, and 1bpp monochrome fonts.</span></span> <span data-ttu-id="78f41-283">リソースに制約があるほとんどのアプリケーションについて、TrueType フォントは、Azure RTOS GUIX によって GUIX Studio デスクトップ ツールを使用して、圧縮されたビットマップ形式に事前にレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="78f41-283">For the most resource-constrained applications, Azure RTOS GUIX pre-renders the TrueType fonts to a compressed bitmap format using our GUIX Studio desktop tool.</span></span>

### <a name="custom-jpg-and-png-decoder-implementation"></a><span data-ttu-id="78f41-284">カスタム JPG および PNG デコーダーの実装</span><span class="sxs-lookup"><span data-stu-id="78f41-284">Custom JPG and PNG decoder implementation</span></span>

<span data-ttu-id="78f41-285">カスタム JPG および PNG デコーダーの実装 JPG および PNG ファイル デコーダーの実装。</span><span class="sxs-lookup"><span data-stu-id="78f41-285">Custom JPG and PNG decoder implementation JPG and PNG file decoder implementation.</span></span> <span data-ttu-id="78f41-286">この実装は、Azure RTOS GUIX 対応ピクセルマップ形式イメージの色空間の変換、ディザリング、およびランタイム作成をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="78f41-286">This implementation supports color space conversion, dithering, and runtime creation of Azure RTOS GUIX-compatible pixelmap format images.</span></span>

### <a name="extensive-display-and-touchscreen-support"></a><span data-ttu-id="78f41-287">さまざまなディスプレイとタッチスクリーンのサポート</span><span class="sxs-lookup"><span data-stu-id="78f41-287">Extensive display and touchscreen support</span></span>

<span data-ttu-id="78f41-288">Azure RTOS GUIX には、ほぼすべての色形式 (1 bpp モノクロ、8 bpp パレット、8 bpp 3:3:2 形式、</span><span class="sxs-lookup"><span data-stu-id="78f41-288">Azure RTOS GUIX provides generic display drivers for nearly all color formats, including 1bpp monochrome, 8 bpp palette, 8 bpp 3:3:2 format,</span></span>

<span data-ttu-id="78f41-289">16 bpp 565 rgb 形式、16 bpp 4:4:4:4 形式、32 bpp x:r:g:b 形式、および 32 bpp:r:g:b 形式など) に対応する汎用ディスプレイ ドライバーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="78f41-289">16 bpp 565 rgb format, 16 bpp 4:4:4:4 format, 32 bpp x:r:g:b format, and 32 bpp a:r:g:b format.</span></span> <span data-ttu-id="78f41-290">さらに、Azure RTOS GUIX は、最も一般的な多くの LCD コントローラーおよびハードウェア アクセラレータ (ST ChromeArt、Renesas Synergy など) に統合されています。</span><span class="sxs-lookup"><span data-stu-id="78f41-290">In addition, Azure RTOS GUIX is integrated with many of the most popular LCD controllers and hardware accelerators (ST ChromeArt, Renesas Synergy, etc.).</span></span>

<span data-ttu-id="78f41-291">Azure RTOS GUIX は、タッチスクリーン (ジェスチャ サポートを含む)、ペン、および仮想キーボード入力デバイスを完全にサポートしています。</span><span class="sxs-lookup"><span data-stu-id="78f41-291">Azure RTOS GUIX fully supports touchscreen (including gesture support), pen, and virtual keyboard input devices.</span></span>

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a><span data-ttu-id="78f41-292">Azure RTOS GUIX Studio デスクトップ WYSIWYG ツール</span><span class="sxs-lookup"><span data-stu-id="78f41-292">Azure RTOS GUIX Studio desktop WYSIWYG tool</span></span>

<span data-ttu-id="78f41-293">Azure RTOS GUIX には、完全な WYSIWYG スクリーン デザイン環境が用意されています。これにより、ユーザーは、GUI スクリーンの作成に使用するグラフィカル要素をドラッグアンドドロップできます。</span><span class="sxs-lookup"><span data-stu-id="78f41-293">Azure RTOS GUIX Studio provides a complete WYSIWYG screen design environment which allows the user to drag-and-drop graphical elements used to build the GUI screens.</span></span> <span data-ttu-id="78f41-294">Azure RTOS GUIX Studio によって、Azure RTOS GUIX ライブラリと互換性がある C コードが自動的に生成されます。これはターゲット上でコンパイルおよび実行できます。</span><span class="sxs-lookup"><span data-stu-id="78f41-294">Azure RTOS GUIX Studio automatically generates C code compatible with the Azure RTOS GUIX library, ready to be compiled and run on the target.</span></span> <span data-ttu-id="78f41-295">開発者は、統合された Azure RTOS GUIX Studio フォント生成ツールを使用して、アプリケーション内で使用できるレンダリング済みフォントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="78f41-295">Developers can produce pre-rendered fonts for use within an application using the integrated Azure RTOS GUIX Studio font generation tool.</span></span> <span data-ttu-id="78f41-296">フォントは、モノクロまたはアンチエイリアス形式で生成でき、ターゲット上の領域を節約するために最適化されています。</span><span class="sxs-lookup"><span data-stu-id="78f41-296">Fonts can be generated in monochrome or anti-aliased formats, and are optimized to save space on the target.</span></span> <span data-ttu-id="78f41-297">フォントには、多言語アプリケーション向け Unicode 文字などの任意の文字セットを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="78f41-297">Fonts can include any set of characters, including Unicode characters for multi-lingual applications.</span></span>

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

<span data-ttu-id="78f41-298">Azure RTOS GUIX により、PNG または JPG ファイルからのグラフィックスのインポートが容易になります。また、ターゲット システム上で使用するために、圧縮された Azure RTOS GUIX ピクセルマップに変換されます。</span><span class="sxs-lookup"><span data-stu-id="78f41-298">Azure RTOS GUIX Studio facilitates the import of graphics from PNG or JPG files with conversion to compressed Azure RTOS GUIX Pixelmaps for use on the target system.</span></span> <span data-ttu-id="78f41-299">Azure RTOS GUIX ウィジェットの種類の多くが、ユーザー グラフィックスを組み込んで外観をカスタマイズできるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="78f41-299">Many of the Azure RTOS GUIX widget types are designed to incorporate user graphics for a custom look and feel.</span></span> <span data-ttu-id="78f41-300">さらに、Azure RTOS GUIX Studio を使用すると、Azure RTOS GUIX ウィジェットで使用される既定の色や描画スタイルをカスタマイズできるため、開発者が Azure RTOS GUIX の外観を非常に簡単に調整することができます。</span><span class="sxs-lookup"><span data-stu-id="78f41-300">In addition, Azure RTOS GUIX Studio allows customization of the default colors and drawing styles used by the Azure RTOS GUIX widgets, allowing developers to tune the appearance of Azure RTOS GUIX very easily.</span></span> <span data-ttu-id="78f41-301">アプリケーション文字列の生成とメンテナンスも、Azure RTOS GUIX Studio の組み込み機能です。</span><span class="sxs-lookup"><span data-stu-id="78f41-301">Generation and maintenance of application strings is another built-in facility of Azure RTOS GUIX Studio.</span></span> <span data-ttu-id="78f41-302">これにより、開発者がアプリケーションを設計したときに使用した開発言語以外の言語のサポートを、製品リリース後にすばやく簡単に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="78f41-302">This enables developers to design an application using one language for developing, and quickly and easily add support for additional languages after the product is released.</span></span> <span data-ttu-id="78f41-303">完全な Azure RTOS GUIX アプリケーションを、Azure RTOS GUIX Studio 環境内の PC デスクトップ上で実行できるため、GUI の概念、スクリーン フローのテスト、およびスクリーン切り替えとアニメーション確認を、迅速かつ簡単に生成し、デモンストレーションを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="78f41-303">A complete Azure RTOS GUIX application can be executed on a PC desktop within the Azure RTOS GUIX Studio environment, allowing a quick and easy generation and demonstration of GUI concepts, testing of screen flows, and observation of screen transitions and animations.</span></span> <span data-ttu-id="78f41-304">完成したデザインはターゲット対応 C データ構造としてエクスポートでき、Azure RTOS GUIX ライブラリと Azure RTOS ThreadX ライブラリでコンパイルし、リンクすることができます。</span><span class="sxs-lookup"><span data-stu-id="78f41-304">When completed, a design can be exported as target-ready C data structures, ready to be compiled and linked with the Azure RTOS GUIX and Azure RTOS ThreadX libraries.</span></span>

<span data-ttu-id="78f41-305">Azure RTOS GUIX と Azure RTOS GUIX Studio は、複数のリソース テーマをサポートしており、実行時、アプリケーションに簡単にスキンを再適用できます。</span><span class="sxs-lookup"><span data-stu-id="78f41-305">Azure RTOS GUIX and Azure RTOS GUIX Studio support multiple resource themes, allowing an application to be easily reskinned at run-time.</span></span> <span data-ttu-id="78f41-306">実行時に 1 つのシンプルな API を使用して、フォント、色、およびピクセルマップを変更できます。</span><span class="sxs-lookup"><span data-stu-id="78f41-306">Fonts, colors, and pixelmaps can be changed at run-time with one simple API.</span></span>

<span data-ttu-id="78f41-307">GUIX Studio の詳細をご確認ください</span><span class="sxs-lookup"><span data-stu-id="78f41-307">Learn more about GUIX Studio</span></span>

### <a name="complete-win32-simulation"></a><span data-ttu-id="78f41-308">完全な Win32 シミュレーション</span><span class="sxs-lookup"><span data-stu-id="78f41-308">Complete Win32 simulation</span></span>

<span data-ttu-id="78f41-309">Azure RTOS GUIX は、ターゲット ボード上で動作するものとまったく同じ描画ライブラリを使用して、Windows PC 上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="78f41-309">Azure RTOS GUIX runs on a Windows PC, using exactly the same drawing library that runs on the target board.</span></span> <span data-ttu-id="78f41-310">Azure RTOS GUIX を使用すると、PC 上で GUI アプリケーションをビルドして実行し、ターゲット上で同じアプリケーション コードを使用して、デバッグ、迅速なプロトタイプ作成、デモンストレーション、WYSIWYG ターゲット操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="78f41-310">With Azure RTOS GUIX, you can build and run a GUI application on the PC, and use the same application code on your target for debugging, rapid prototyping, demonstration, and WYSIWYG target operation.</span></span>

### <a name="advanced-technology"></a><span data-ttu-id="78f41-311">高度なテクノロジ</span><span class="sxs-lookup"><span data-stu-id="78f41-311">Advanced technology</span></span>

* <span data-ttu-id="78f41-312">Azure RTOS GUIX の高度なテクノロジには、次のものが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="78f41-312">Azure RTOS GUIX's advanced technology incorporates:</span></span>

* <span data-ttu-id="78f41-313">アルファ ブレンド</span><span class="sxs-lookup"><span data-stu-id="78f41-313">Alpha blending</span></span>

* <span data-ttu-id="78f41-314">アンチエイリアシング</span><span class="sxs-lookup"><span data-stu-id="78f41-314">Anti-Aliasing</span></span>

* <span data-ttu-id="78f41-315">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="78f41-315">Automatic scaling</span></span>

* <span data-ttu-id="78f41-316">ビットマップ圧縮</span><span class="sxs-lookup"><span data-stu-id="78f41-316">Bitmap compression</span></span>

* <span data-ttu-id="78f41-317">キャンバス ブレンド</span><span class="sxs-lookup"><span data-stu-id="78f41-317">Canvas blending</span></span>

* <span data-ttu-id="78f41-318">カスタム ウィジェット サポート</span><span class="sxs-lookup"><span data-stu-id="78f41-318">Custom widget support</span></span>

* <span data-ttu-id="78f41-319">遅延描画サポート</span><span class="sxs-lookup"><span data-stu-id="78f41-319">Deferred drawing support</span></span>

* <span data-ttu-id="78f41-320">ディザリング サポート</span><span class="sxs-lookup"><span data-stu-id="78f41-320">Dithering support</span></span>

* <span data-ttu-id="78f41-321">エンディアン ニュートラル プログラミング</span><span class="sxs-lookup"><span data-stu-id="78f41-321">Endian neutral programming</span></span>

* <span data-ttu-id="78f41-322">ハードウェア アクセラレータ サポート</span><span class="sxs-lookup"><span data-stu-id="78f41-322">Hardware accelerator support</span></span>

* <span data-ttu-id="78f41-323">多言語サポートと UTF-8 エンコード</span><span class="sxs-lookup"><span data-stu-id="78f41-323">Multilingual support and UTF-8 encoding</span></span>

* <span data-ttu-id="78f41-324">複数ディスプレイとキャンバス サポート</span><span class="sxs-lookup"><span data-stu-id="78f41-324">Multiple display and canvas support</span></span>

* <span data-ttu-id="78f41-325">最適化されたクリッピング、描画、およびイベント処理</span><span class="sxs-lookup"><span data-stu-id="78f41-325">Optimized clipping, drawing, and event handling</span></span>

* <span data-ttu-id="78f41-326">ランタイム JPEG および PNG デコーダー</span><span class="sxs-lookup"><span data-stu-id="78f41-326">Runtime JPEG and PNG decoder</span></span>

* <span data-ttu-id="78f41-327">スキニングとテーマ</span><span class="sxs-lookup"><span data-stu-id="78f41-327">Skinning and Themes</span></span>

* <span data-ttu-id="78f41-328">モノクロから 32 ビット true-color (アルファ付き) グラフィックス形式までをサポート</span><span class="sxs-lookup"><span data-stu-id="78f41-328">Supports monochrome through 32-bit true-color with alpha graphics formats</span></span>

* <span data-ttu-id="78f41-329">切り替え、スプライト、およびアニメーションのサポート</span><span class="sxs-lookup"><span data-stu-id="78f41-329">Transitions, Sprites, and Animation support</span></span>

* <span data-ttu-id="78f41-330">Win32 シミュレーション</span><span class="sxs-lookup"><span data-stu-id="78f41-330">Win32 simulation</span></span>

* <span data-ttu-id="78f41-331">ウィンドウ管理 (ビューポートと Z オーダーのメンテナンスを含む)</span><span class="sxs-lookup"><span data-stu-id="78f41-331">Window management including Viewports and Z-order maintenance</span></span>

### <a name="fastest-time-to-market"></a><span data-ttu-id="78f41-332">市場投入までの時間を短縮</span><span class="sxs-lookup"><span data-stu-id="78f41-332">Fastest time-to-market</span></span>

<span data-ttu-id="78f41-333">Azure RTOS GUIX は、インストール、習得、使用、デバッグ、検証、認定、保守が簡単です。</span><span class="sxs-lookup"><span data-stu-id="78f41-333">Azure RTOS GUIX is easy to install, learn, use, debug, verify, certify and maintain.</span></span> <span data-ttu-id="78f41-334">また、Azure RTOS GUIX Studio により、埋め込み GUI のデザインと実装が容易になります。</span><span class="sxs-lookup"><span data-stu-id="78f41-334">Azure RTOS GUIX Studio also helps making embedded GUI design and implementation easier.</span></span> <span data-ttu-id="78f41-335">その結果、Azure RTOS GUIX は、埋め込み IoT デバイス向けの最も普及している GUI ソリューションの 1 つになっています。</span><span class="sxs-lookup"><span data-stu-id="78f41-335">As a result, Azure RTOS GUIX is one of the most popular GUI solutions for embedded IoT devices.</span></span> <span data-ttu-id="78f41-336">一貫した市場投入までの時間の優位性は、次の要素を基に構築されています。</span><span class="sxs-lookup"><span data-stu-id="78f41-336">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="78f41-337">質の高いドキュメント - [Azure RTOS GUIX ユーザー ガイド](about-guix.md)をご覧になり、ご自身でお確かめください</span><span class="sxs-lookup"><span data-stu-id="78f41-337">Quality Documentation – please review our [Azure RTOS GUIX User Guide](about-guix.md) and see for yourself!</span></span>

* <span data-ttu-id="78f41-338">完全なソース コードを提供</span><span class="sxs-lookup"><span data-stu-id="78f41-338">Complete Source Code Availability</span></span>

* <span data-ttu-id="78f41-339">使いやすい API</span><span class="sxs-lookup"><span data-stu-id="78f41-339">Easy-to-use API</span></span>

* <span data-ttu-id="78f41-340">包括的かつ高度な機能セット</span><span class="sxs-lookup"><span data-stu-id="78f41-340">Comprehensive and Advanced Feature Set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="78f41-341">シンプルな 1 つのライセンス</span><span class="sxs-lookup"><span data-stu-id="78f41-341">One Simple License</span></span>

<span data-ttu-id="78f41-342">ソース コードの使用とテストに費用はかからず、事前にライセンスされたデバイスに展開する場合は、運用環境ライセンスにはコストがかかりません。その他のすべてのデバイスには、シンプルな年間ライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="78f41-342">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="78f41-343">完全な最高品質のソース コード</span><span class="sxs-lookup"><span data-stu-id="78f41-343">Full, highest-quality source code</span></span>

<span data-ttu-id="78f41-344">長年にわたり、Azure RTOS NetX のソース コードは、品質とわかりやすさに一定の基準を設けてきました。</span><span class="sxs-lookup"><span data-stu-id="78f41-344">Throughout the years, Azure RTOS NetX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="78f41-345">また、ファイルごとに 1 つの関数を使用するという規則により、簡単にソースを移動できます。</span><span class="sxs-lookup"><span data-stu-id="78f41-345">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="78f41-346">最も一般的なアーキテクチャをサポート</span><span class="sxs-lookup"><span data-stu-id="78f41-346">Supports most popular architectures</span></span>

<span data-ttu-id="78f41-347">Azure RTOS GUIX は、すぐに利用可能で完全なテストとサポートが実現されている、最も一般的な 32/64 ビットのマイクロプロセッサで動作します。</span><span class="sxs-lookup"><span data-stu-id="78f41-347">Azure RTOS GUIX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

<span data-ttu-id="78f41-348">高度なアーキテクチャ:</span><span class="sxs-lookup"><span data-stu-id="78f41-348">Advanced Architectures:</span></span>

<span data-ttu-id="78f41-349">**Analog Devices**: SHARC、Blackfin、CM4xx</span><span class="sxs-lookup"><span data-stu-id="78f41-349">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="78f41-350">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="78f41-350">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="78f41-351">**Ambiqmicro**: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="78f41-351">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="78f41-352">**ARM**: ARM7、ARM9、ARM11、Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64 ビット/A7x 64 ビット/R4/R5、TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="78f41-352">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="78f41-353">**Cadence**: Xtensa、Diamond</span><span class="sxs-lookup"><span data-stu-id="78f41-353">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="78f41-354">**CEVA**: PSoC、PSoC 4、PSoC 5、PSoC 6、FM0+、FM3、MF4、WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="78f41-354">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="78f41-355">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="78f41-355">**Cypress**: RISC-V</span></span>

<span data-ttu-id="78f41-356">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="78f41-356">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="78f41-357">**Infineon**: XMC1000、XMC4000、TriCore</span><span class="sxs-lookup"><span data-stu-id="78f41-357">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="78f41-358">**Intel および Intel FPGA**: x36/Pentium、XScale、NIOS II、Cyclone、Arria 10</span><span class="sxs-lookup"><span data-stu-id="78f41-358">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="78f41-359">**Microchip**: AVR32、ARM7、ARM9、Cortex-M3/M4/M7、SAM3/4/7/9/A/C/D/E/G/L/SV、PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="78f41-359">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="78f41-360">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="78f41-360">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="78f41-361">**NXP**: LPC、ARM7、ARM9、PowerPC、68K、i.MX、ColdFire、Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="78f41-361">**NXP**: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="78f41-362">**Renesas**: SH、HS、V850、RX、RZ、Synergy</span><span class="sxs-lookup"><span data-stu-id="78f41-362">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="78f41-363">**Silicon Labs**: EFM32</span><span class="sxs-lookup"><span data-stu-id="78f41-363">**Silicon Labs**: EFM32</span></span>

<span data-ttu-id="78f41-364">**Synopsys**: ARC 600、700、ARC EM、ARC HS</span><span class="sxs-lookup"><span data-stu-id="78f41-364">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="78f41-365">**ST**: STM32、ARM7、ARM9、Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="78f41-365">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="78f41-366">**Tl**: C5xxx、C6xxx、Stellaris、Sitara、Tiva-C</span><span class="sxs-lookup"><span data-stu-id="78f41-366">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="78f41-367">**Wave Computing**: MIPS32 4K、24K、34K、1004K、MIPS64 5K、microAptiv、interAptiv、proAptiv、M-Class</span><span class="sxs-lookup"><span data-stu-id="78f41-367">**Wave Computing**: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="78f41-368">**Xilinx**: MicroBlaze、PowerPC 405、ZYNQ、ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="78f41-368">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>
