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
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a>Azure RTOS GUIX および Azure RTOS GUIX Studio の概要

Azure GUIX 埋め込み GUI は、深く埋め込まれたリアルタイム IoT アプリケーション向けに特別に設計された、Microsoft の高度な商用 GUI ソリューションです。 また、Microsoft は、Azure RTOS GUIX Studio という完全な機能を備えた WYSIWYG デスクトップ デザイン ツールも提供しており、開発者が、デスクトップ上で自身の GUI をデザインし、Azure RTOS GUIX 埋め込み GUI コードを生成して、それをターゲットにエクスポートすることができます。 Azure RTOS GUIX は Azure RTOS ThreadX RTOS と完全に統合されており、Azure RTOS ThreadX でサポートされている同じプロセッサの多くで利用できます。 これらすべてを小さな専有領域、高速処理、および優れた操作性と組み合わせることで、Azure RTOS GUIX は、ユーザー インターフェイスを必要とする最も要求の厳しい埋め込み型 IoT アプリケーションに最適な選択肢となります。 

## <a name="azure-rtos-guix-api"></a>Azure RTOS GUIX API

### <a name="powerful-apis"></a>強力な API

* 必要に応じて直接的なキャンバス描画を完全サポート
* Azure RTOS GUIX Studio で生成されたコードの操作が簡単
* 線、四角形、多角形などの API
* 円、弧、弦、楕円などの API
* テキスト描画、配置の API
* アンチエイリアシング、テクスチャで塗りつぶし、純色で塗りつぶし
* スクリーンおよびウィジェットの作成と変更のための API

### <a name="azure-rtos-guix-studio-generated-files"></a>Azure RTOS GUIX Studio で生成されたファイル

* 自動生成された ANSI C ソース ファイル
* アプリケーション ソフトウェアをレイアウトの詳細から分離
* UI デザインに必要なフォントとイメージの挿入
* アプリケーション コードを使用してコンパイルされた生成ファイル
* アプリケーション ロジックに影響を与えずにスクリーン レイアウトを更新可能
* リソース ID により言語とテーマの独立性を確保
* ユーザーが指定したカスタム描画およびイベント処理関数

### <a name="widget-library"></a>ウィジェット ライブラリ

* 事前定義されているがカスタマイズ可能な一連の共通インターフェイス要素
* 非常に小さく、コンパクト、かつ効率的
* ライブラリにボタン、ゲージ、リスト、ウィンドウ、スクロール、スライダー、進行状況バー、プロンプトなどが含まれる
* 完全にカスタマイズ可能な描画と外観
* 完全にカスタマイズ可能な操作とイベント処理
* 使用されるウィジェットのみがアプリケーション ソフトウェアとリンク

### <a name="math-and-utilities"></a>数式とユーティリティ

* 正弦、余弦、逆正弦、逆余弦、正接、平方根の関数
* スクリーン領域を操作するための関数
* システムの構成と起動
* メモリ プールの定義 (省略可能)
* タイマー管理
* アニメーション管理
* ダーティ リストのメンテナンス

### <a name="image-processing"></a>画像処理

* jpeg および png イメージのランタイム デコード用の関数
* ディザリングおよび色空間の変換の適用
* イメージの回転
* イメージのスケーリング
* イメージのブレンド

### <a name="event-processing"></a>イベント処理

* アイドル時に Azure RTOS GUIX スレッドを自動停止
* UI デザインでよく使用されるイベントドリブン プログラミング デル
* 入力ドライバーを Azure RTOS GUIX 描画スレッドから分離
* イベントを送受信するための関数
* すべての Azure RTOS GUIX ウィジェットの種類に対する事前定義済みのイベントの種類
* サポートされているユーザー定義カスタム イベント

### <a name="canvas-processing"></a>キャンバスの処理

* クリッピングと Z オーダーのメンテナンス
* ウィジェット ライブラリをハードウェアの詳細から分離
* アプリケーションをハードウェアの詳細から分離
* ダーティ領域の自動バックグラウンド更新
* レイヤーとブレンドがサポートされている複数のキャンバス
* アプリケーション ソフトウェアによる直接呼び出しが可能

### <a name="input-device-drivers"></a>入力デバイス ドライバー

* ハードウェア固有のサポート、Azure RTOS GUIX およびハードウェアの詳細から切り離されたアプリケーション
* 抵抗膜方式タッチ、静電容量タッチ、およびキーパッドのサポート
* Azure RTOS GUIX イベント キューに渡される入力イベント

### <a name="display-drivers"></a>ディスプレイ ドライバー

* ハードウェア固有のサポート
* すべての色深度と色形式に提供される汎用ドライバー
* 使用可能なグラフィックス アクセラレータを使用するようにカスタマイズ済み

### <a name="target-hardware"></a>ターゲット ハードウェア

* ほぼすべてのグラフィカル出力対応ハードウェアが GUIX に対応
* 複数の物理ディスプレイのサポート
* 最小 RAM とフラッシュの要件

## <a name="create-elegant-user-interfaces"></a>洗練されたユーザー インターフェイスを作成する

Azure RTOS GUIX および Azure RTOS GUIX Studio には、洗練された独自のユーザー インターフェイスの作成に必要な機能すべてが用意されています。 標準の Azure RTOS GUIX パッケージには、医療デバイス参照、スマート ウォッチ参照、ホーム オートメーション参照、工業制御参照、自動車参照、さまざまなスプライトとアニメーションの例など、各種サンプル ユーザー インターフェイスが含まれています。 以下の参照例をクリックしてください。

### <a name="home-automation"></a>ホーム オートメーション

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a>医療

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a>コンシューマー

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a>白物家電

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a>自動車

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a>工業

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

各 Azure RTOS GUIX 参照には、参照デザインのすべてのグラフィカル要素を定義する、対応する Azure RTOS GUIX Studio プロジェクトが含まれています。 参照デザインを変更するのは簡単です。 対応する Azure RTOS GUIX プロジェクトを開き、必要な変更を加え、プロジェクトを保存して、"*プロジェクト*" を選択するだけです。

すべての出力ファイルを生成して、Azure RTOS GUIX 用の C コードを生成します。 そして、ターゲット アプリケーションをリビルドし、変更された参照デザインを確認するだけです。

### <a name="guix-memory-footprint"></a>GUIX のメモリ占有領域

Azure RTOS GUIX の最小メモリ専有領域は非常に小さく、キャンバスに必要なメモリを含まない基本サポートの場合、フラッシュは 13.2 KB、RAM は 4 KB です。

内部で GRAM と自己更新テクノロジが使用されているディスプレイについては、キャンバス メモリは必要ありません。 ただし、描画パフォーマンスを向上させるために、または、ディスプレイに対してローカルな GRAM を使用しないディスプレイ構成の場合は、アプリケーションによってキャンバス メモリ領域が定義されます。

キャンバスのメモリ要件は、キャンバス サイズと色深度の関数であり、次の式で定義されます。

<i>キャンバス RAM (バイト) = (x * y * (bpp/8))</i>

ここで、"x" と "y" はキャンバス (ディスプレイ) のディメンションです。

また、ほとんどのアプリケーションでグラフィカル リソースが使用されていますが、これは主要 Azure RTOS GUIX ライブラリ ストレージ要件に含まれていません。 これらのリソースには、フォント、グラフィカル アイコン (ピクセルマップ)、および静的な文字列が含まれます。 このデータは、const メモリ セクション (フラッシュ) に格納できます。

このメモリ領域のサイズは、使用される一意のフォントの数とサイズ、使用されるグラフィカル アイコンの数とサイズ、出力色形式、各リソースが圧縮データを使用しているかどうかなど、さまざまな要因に依存します。これは、Azure RTOS GUIX が、フォントとピクセルマップの両方のデータの RLE 圧縮をサポートしているためです。 各リソースのストレージ要件は、Azure RTOS GUIX Studio アプリケーション内に表示されます。これにより、ユーザーは、アプリケーション リソースによって消費されるフラッシュ メモリの量を追跡および監視できます。

Azure RTOS ThreadX と同様に、Azure RTOS GUIX のサイズは、アプリケーションで実際に使用されるサービスに基づいて自動的にスケーリングされます。 これにより、複雑な構成やビルド パラメーターが実質的に不要になるため、開発者の作業がより簡単になります。

#### <a name="simple-easy-to-use"></a>シンプルで優れた操作性

Azure RTOS GUIX は非常に簡単に使用できますが、Azure RTOS GUIX Studio は、開発者がデスクトップ上で視覚的にデザインし、実際のターゲット上で動作する C コードを生成できるため、さらに使いやすくなっています。 アプリケーションが独自のカスタム イベント処理や描画関数を追加して、GUI を完成させることができます。

Azure RTOS GUIX API の使い方は簡単です。 Azure RTOS GUIX API は直感的かつ高機能です。 API 名は、他のファイル システム製品でよく見られる略語や大幅に省略された名前ではなく、実際の単語で構成されています。 すべての Azure RTOS GUIX API は、先頭に *gx_* が付き、名詞 - 動詞の名前付け規則に従っています。 さらに、API 全体に機能的な一貫性があります。 たとえば、ウィジェット制御ブロックを初期化するすべての API に、&lt;widget_type&gt;_create という名前が付けられます。また、各ウィジェットの種類の create function パラメーターは常に同じ順序で定義されます。

### <a name="comprehensive-set-of-built-in-widgets"></a>包括的な組み込みウィジェット セット

* Azure RTOS GUIX には、次のような豊富な組み込みウィジェット セットが用意されています。
* アコーディオン メニュー
* Button
* Checkbox
* 円形ゲージ
* ドロップダウン リスト
* 横方向の一覧
* 水平スクロールバー ウィンドウ
* アイコン
* アイコン ボタン
* 折れ線グラフ
* メニュー
* 複数行テキスト ボタン
* 複数行テキスト入力
* 複数行テキスト ビュー
* 数値ピクセルマップ プロンプト
* 数値プロンプト
* 数値スクロール ホイール
* ピクセルマップ ボタン
* ピクセル マップ プロンプト
* ピクセルマップ スライダー
* ピクセルマップ スプライト
* 進行状況バー
* Prompt
* 放射状の進行状況バー
* オプション ボタン
* スクロール ホイール
* 単一行テキスト入力
* スライダー
* 文字列スクロール ホイール
* テキスト ボタン
* ツリー ビュー
* 縦一覧
* 垂直スクロール バー

アプリケーションによって独自の顧客ウィジェットを簡単に作成することもできます。

### <a name="complete-low-level-drawing-api"></a>完全な低レベル描画 API

Azure RTOS GUIX には、堅牢なキャンバス描画 API が用意されています。これにより、アプリケーションは複雑なグラフィカル形状をレンダリングできます。

すべての関数が、高い色深度ターゲット上でのアンチエイリアシングをサポートしており、純色塗り、ピクセルマップ パターン塗りを含め、すべての図形の輪郭を塗りつぶすことができます。 16 bpp 以上の高い色深度で実行する場合は、すべての描画プリミティブによって、ブラシ アルファがサポートされます。 描画関数は次のとおりです。

* 弧描画
* 円描画
* 線描画
* 円描画
* ピクセルマップ Blend
* ピクセルマップ タイル
* 多角形描画
* テキスト描画
* 弦描画
* 楕円描画
* ピクセル描画
* ピクセルマップ描画
* ピクセルマップ回転
* 四角形描画
* テキスト Blend

### <a name="default-free-fonts-and-easy-to-add-more"></a>既定の無料フォントで、さらに簡単に追加

Azure RTOS GUIX には、無料の TrueType フォント セットが用意されています。 開発者は、必要に応じて TrueType フォントを追加できます。

Azure RTOS GUIX フォント形式は、8 bpp アンチエイリアシング、4 bpp アンチエイリアシング、および 1 bpp モノクロ フォントをサポートしています。 リソースに制約があるほとんどのアプリケーションについて、TrueType フォントは、Azure RTOS GUIX によって GUIX Studio デスクトップ ツールを使用して、圧縮されたビットマップ形式に事前にレンダリングされます。

### <a name="custom-jpg-and-png-decoder-implementation"></a>カスタム JPG および PNG デコーダーの実装

カスタム JPG および PNG デコーダーの実装 JPG および PNG ファイル デコーダーの実装。 この実装は、Azure RTOS GUIX 対応ピクセルマップ形式イメージの色空間の変換、ディザリング、およびランタイム作成をサポートしています。

### <a name="extensive-display-and-touchscreen-support"></a>さまざまなディスプレイとタッチスクリーンのサポート

Azure RTOS GUIX には、ほぼすべての色形式 (1 bpp モノクロ、8 bpp パレット、8 bpp 3:3:2 形式、

16 bpp 565 rgb 形式、16 bpp 4:4:4:4 形式、32 bpp x:r:g:b 形式、および 32 bpp:r:g:b 形式など) に対応する汎用ディスプレイ ドライバーが用意されています。 さらに、Azure RTOS GUIX は、最も一般的な多くの LCD コントローラーおよびハードウェア アクセラレータ (ST ChromeArt、Renesas Synergy など) に統合されています。

Azure RTOS GUIX は、タッチスクリーン (ジェスチャ サポートを含む)、ペン、および仮想キーボード入力デバイスを完全にサポートしています。

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a>Azure RTOS GUIX Studio デスクトップ WYSIWYG ツール

Azure RTOS GUIX には、完全な WYSIWYG スクリーン デザイン環境が用意されています。これにより、ユーザーは、GUI スクリーンの作成に使用するグラフィカル要素をドラッグアンドドロップできます。 Azure RTOS GUIX Studio によって、Azure RTOS GUIX ライブラリと互換性がある C コードが自動的に生成されます。これはターゲット上でコンパイルおよび実行できます。 開発者は、統合された Azure RTOS GUIX Studio フォント生成ツールを使用して、アプリケーション内で使用できるレンダリング済みフォントを作成できます。 フォントは、モノクロまたはアンチエイリアス形式で生成でき、ターゲット上の領域を節約するために最適化されています。 フォントには、多言語アプリケーション向け Unicode 文字などの任意の文字セットを含めることができます。

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

Azure RTOS GUIX により、PNG または JPG ファイルからのグラフィックスのインポートが容易になります。また、ターゲット システム上で使用するために、圧縮された Azure RTOS GUIX ピクセルマップに変換されます。 Azure RTOS GUIX ウィジェットの種類の多くが、ユーザー グラフィックスを組み込んで外観をカスタマイズできるように設計されています。 さらに、Azure RTOS GUIX Studio を使用すると、Azure RTOS GUIX ウィジェットで使用される既定の色や描画スタイルをカスタマイズできるため、開発者が Azure RTOS GUIX の外観を非常に簡単に調整することができます。 アプリケーション文字列の生成とメンテナンスも、Azure RTOS GUIX Studio の組み込み機能です。 これにより、開発者がアプリケーションを設計したときに使用した開発言語以外の言語のサポートを、製品リリース後にすばやく簡単に追加することができます。 完全な Azure RTOS GUIX アプリケーションを、Azure RTOS GUIX Studio 環境内の PC デスクトップ上で実行できるため、GUI の概念、スクリーン フローのテスト、およびスクリーン切り替えとアニメーション確認を、迅速かつ簡単に生成し、デモンストレーションを行うことができます。 完成したデザインはターゲット対応 C データ構造としてエクスポートでき、Azure RTOS GUIX ライブラリと Azure RTOS ThreadX ライブラリでコンパイルし、リンクすることができます。

Azure RTOS GUIX と Azure RTOS GUIX Studio は、複数のリソース テーマをサポートしており、実行時、アプリケーションに簡単にスキンを再適用できます。 実行時に 1 つのシンプルな API を使用して、フォント、色、およびピクセルマップを変更できます。

GUIX Studio の詳細をご確認ください

### <a name="complete-win32-simulation"></a>完全な Win32 シミュレーション

Azure RTOS GUIX は、ターゲット ボード上で動作するものとまったく同じ描画ライブラリを使用して、Windows PC 上で実行されます。 Azure RTOS GUIX を使用すると、PC 上で GUI アプリケーションをビルドして実行し、ターゲット上で同じアプリケーション コードを使用して、デバッグ、迅速なプロトタイプ作成、デモンストレーション、WYSIWYG ターゲット操作を行うことができます。

### <a name="advanced-technology"></a>高度なテクノロジ

* Azure RTOS GUIX の高度なテクノロジには、次のものが組み込まれています。
* アルファ ブレンド
* アンチエイリアシング
* 自動スケーリング
* ビットマップ圧縮
* キャンバス ブレンド
* カスタム ウィジェット サポート
* 遅延描画サポート
* ディザリング サポート
* エンディアン ニュートラル プログラミング
* ハードウェア アクセラレータ サポート
* 多言語サポートと UTF-8 エンコード
* 複数ディスプレイとキャンバス サポート
* 最適化されたクリッピング、描画、およびイベント処理
* ランタイム JPEG および PNG デコーダー
* スキニングとテーマ
* モノクロから 32 ビット true-color (アルファ付き) グラフィックス形式までをサポート
* 切り替え、スプライト、およびアニメーションのサポート
* Win32 シミュレーション
* ウィンドウ管理 (ビューポートと Z オーダーのメンテナンスを含む)
