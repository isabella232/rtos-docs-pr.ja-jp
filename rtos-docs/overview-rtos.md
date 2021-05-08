---
title: Microsoft Azure RTOS とは
description: Azure RTOS は、マイクロコントローラー ユニット (MCU) を搭載した IoT デバイスとエッジ デバイスのためのリアル タイム オペレーティング システム (RTOS) です。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: c902289b487c439da4ef5138319fe09d74a2347f
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171277"
---
# <a name="what-is-microsoft-azure-rtos"></a><span data-ttu-id="bd272-103">Microsoft Azure RTOS とは</span><span class="sxs-lookup"><span data-stu-id="bd272-103">What is Microsoft Azure RTOS?</span></span>

<span data-ttu-id="bd272-104">Azure RTOS は、マイクロコントローラー ユニット (MCU) を搭載したモノのインターネット (IoT) およびエッジ デバイスのためのリアル タイム オペレーティング システム (RTOS) です。</span><span class="sxs-lookup"><span data-stu-id="bd272-104">Azure RTOS is a real time operating system (RTOS) for Internet of Things (IoT) and edge devices powered by microcontroller units (MCUs).</span></span> <span data-ttu-id="bd272-105">Azure RTOS は、非常に制約の厳しいデバイス (バッテリ駆動で、フラッシュ メモリが 64 KB 未満) をサポートするように設計されています。</span><span class="sxs-lookup"><span data-stu-id="bd272-105">Azure RTOS is designed to support most highly constrained devices (battery powered and having less than 64 KB of flash memory).</span></span>

<span data-ttu-id="bd272-106">Azure RTOS は、さまざまな安全性標準に対する認定をあらかじめ受けています。</span><span class="sxs-lookup"><span data-stu-id="bd272-106">Azure RTOS is pre-certified for a variety of safety standards.</span></span> <span data-ttu-id="bd272-107">これには、IEC 61508 SIL 4、IEC 62304 Class C、ISO 26262 ASIL D の各認定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bd272-107">These include the IEC 61508 SIL 4, IEC 62304 Class C, and ISO 26262 ASIL D certifications.</span></span> <span data-ttu-id="bd272-108">Azure RTOS ThreadX は、DO-178 の認定も受けています。</span><span class="sxs-lookup"><span data-stu-id="bd272-108">Azure RTOS ThreadX is also DO-178 certified.</span></span>

<span data-ttu-id="bd272-109">Azure RTOS により、IPsec による完全な IP 層セキュリティおよび TLS と DTLS によるソケット層セキュリティを含む、EAL4+ の情報セキュリティ国際評価基準認定環境が提供されます。</span><span class="sxs-lookup"><span data-stu-id="bd272-109">Azure RTOS provides an EAL4+ Common Criteria security certified environment, including full IP layer security via IPsec and socket layer security via TLS and DTLS.</span></span> <span data-ttu-id="bd272-110">Microsoft のソフトウェア暗号化ライブラリは、FIPS 140-2 の認定を受けています。</span><span class="sxs-lookup"><span data-stu-id="bd272-110">Our software crypto library has achieved FIPS 140-2 certification.</span></span> <span data-ttu-id="bd272-111">また、ハードウェア暗号化機能、ThreadX MODULES によるメモリ保護、ARM の TrustZone ARMv8-M セキュリティ機能のサポートも利用しています。</span><span class="sxs-lookup"><span data-stu-id="bd272-111">We also leverage hardware cryptographic capabilities, memory protection via ThreadX MODULES, and support for ARM's TrustZone ARMv8-M security features.</span></span>

## <a name="components-of-azure-rtos"></a><span data-ttu-id="bd272-112">Azure RTOS のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="bd272-112">Components of Azure RTOS</span></span>

<span data-ttu-id="bd272-113">Azure RTOS プラットフォームは、Azure RTOS ThreadX、Azure RTOS FileX、Azure RTOS GUIX、Azure RTOS NetX、Azure RTOS NetX Duo、Azure RTOS USBX などの実行時ソリューションのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="bd272-113">The Azure RTOS platform is the collection of run-time solutions including Azure RTOS ThreadX, Azure RTOS FileX, Azure RTOS GUIX, Azure RTOS NetX, Azure RTOS NetX Duo, and Azure RTOS USBX.</span></span>

### <a name="azure-rtos-threadx"></a><span data-ttu-id="bd272-114">Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="bd272-114">Azure RTOS ThreadX</span></span>

<span data-ttu-id="bd272-115">Azure RTOS ThreadX は、特に深く組み込まれたアプリケーション向けに設計された高度なリアルタイム オペレーティング システム (RTOS) です。</span><span class="sxs-lookup"><span data-stu-id="bd272-115">Azure RTOS ThreadX is an advanced Real-Time Operating System (RTOS) designed specifically for deeply embedded applications.</span></span> <span data-ttu-id="bd272-116">Azure RTOS ThreadX によって提供されるさまざまな利点としては、高度なスケジュール機能、メッセージ パッシング、割り込み管理、メッセージング サービスなどがあります。</span><span class="sxs-lookup"><span data-stu-id="bd272-116">Among the multiple benefits Azure RTOS ThreadX provides are advanced scheduling facilities, message passing, interrupt management, and messaging services.</span></span> <span data-ttu-id="bd272-117">Azure RTOS ThreadX には、ピコカーネル アーキテクチャ、優先しきい値のスケジュール設定、イベント チェーン、豊富なシステム サービスのセットなど、高度な機能が多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="bd272-117">Azure RTOS ThreadX has many advanced features, including its picokernel architecture, preemption-threshold scheduling, event-chaining, and a rich set of system services.</span></span>

### <a name="azure-rtos-filex"></a><span data-ttu-id="bd272-118">Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="bd272-118">Azure RTOS FileX</span></span>

<span data-ttu-id="bd272-119">Azure RTOS FileX は、高パフォーマンスの FAT 互換ファイル システムです。</span><span class="sxs-lookup"><span data-stu-id="bd272-119">Azure RTOS FileX is a high-performance FAT-compatible file system.</span></span> <span data-ttu-id="bd272-120">Azure RTOS ThreadX と完全に統合されており、サポートされているすべてのプロセッサで利用できます。</span><span class="sxs-lookup"><span data-stu-id="bd272-120">It is fully integrated with Azure RTOS ThreadX and is available for all supported processors.</span></span> <span data-ttu-id="bd272-121">Azure RTOS ThreadX と同様に、Azure RTOS FileX は、小さい専有領域でハイ パフォーマンスを実現するように設計されているため、ファイル操作を必要とする昨今の深い埋め込み型のアプリケーションに最適です。</span><span class="sxs-lookup"><span data-stu-id="bd272-121">Like Azure RTOS ThreadX, Azure RTOS FileX is designed to have a small footprint and high performance, making it ideal for today's deeply embedded applications that require file operations.</span></span> <span data-ttu-id="bd272-122">Azure RTOS FileX により、RAM ディスク、USBX、SD カード、および Azure RTOS LevelX 経由の NAND と NOR フラッシュ メモリなど、ほとんどの物理メディアがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bd272-122">Azure RTOS FileX supports most physical media, including RAM disk, USBX, SD CARD, and NAND/NOR flash memories via Azure RTOS LevelX.</span></span>

### <a name="azure-rtos-guix"></a><span data-ttu-id="bd272-123">Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="bd272-123">Azure RTOS GUIX</span></span>

<span data-ttu-id="bd272-124">Azure RTOS GUIX は、埋め込みシステム開発者のニーズに対応するために作成された、プロフェッショナル品質のグラフィカル ユーザー インターフェイス パッケージです。</span><span class="sxs-lookup"><span data-stu-id="bd272-124">Azure RTOS GUIX is a professional quality graphical user interface package, created to meet the needs of embedded systems developers.</span></span> <span data-ttu-id="bd272-125">代替製品とは異なり、Azure RTOS GUIX は小さく高速で、グラフィカル出力をサポートできる事実上すべてのハードウェア構成に簡単に移植できます。</span><span class="sxs-lookup"><span data-stu-id="bd272-125">Unlike the alternatives, Azure RTOS GUIX is small, fast, and easily ported to virtually any hardware configuration capable of supporting graphical output.</span></span> <span data-ttu-id="bd272-126">また、Azure RTOS GUIX には、魅力的な外観と、アプリケーション レベルのユーザー インターフェイス開発用の直感的で強力な API も用意されています。</span><span class="sxs-lookup"><span data-stu-id="bd272-126">Azure RTOS GUIX also delivers exceptional visual appeal and an intuitive and powerful API for application-level user interface development.</span></span>

### <a name="azure-rtos-netx"></a><span data-ttu-id="bd272-127">Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="bd272-127">Azure RTOS NetX</span></span>

<span data-ttu-id="bd272-128">Azure RTOS NetX は、TCP/IP プロトコル標準の高パフォーマンスの実装です。</span><span class="sxs-lookup"><span data-stu-id="bd272-128">Azure RTOS NetX is a high-performance implementation of TCP/IP protocol standards.</span></span> <span data-ttu-id="bd272-129">Azure RTOS ThreadX と完全に統合されており、サポートされているすべてのプロセッサで利用できます。</span><span class="sxs-lookup"><span data-stu-id="bd272-129">It is fully integrated with Azure RTOS ThreadX, and is available for all supported processors.</span></span> <span data-ttu-id="bd272-130">Azure RTOS NetX は、独自の Piconet アーキテクチャを備えています。</span><span class="sxs-lookup"><span data-stu-id="bd272-130">Azure RTOS NetX has a unique Piconet architecture.</span></span> <span data-ttu-id="bd272-131">ゼロコピー API と組み合わせることで、ネットワーク接続を必要とする今日の深く組み込まれたアプリケーションに最適なものになります。</span><span class="sxs-lookup"><span data-stu-id="bd272-131">Combined with a zero-copy API, it makes it a perfect fit for today's deeply embedded applications that require network connectivity.</span></span>

### <a name="azure-rtos-netx-duo"></a><span data-ttu-id="bd272-132">Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bd272-132">Azure RTOS NetX Duo</span></span>

<span data-ttu-id="bd272-133">Azure RTOS NetX Duo は、特に深く組み込まれたリアルタイムの IoT アプリケーション用に設計された、高度な商用 TCP/IP ネットワーク スタックです。</span><span class="sxs-lookup"><span data-stu-id="bd272-133">Azure RTOS NetX Duo is an advanced, Industrial Grade TCP/IP network stacks designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="bd272-134">Azure RTOS NetX Duo が IPv4 と IPv6 のデュアル ネットワーク スタックであるのに対し、NetX は元の IPv4 ネットワーク スタックで、実質的には Azure RTOS NetX Duo のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="bd272-134">Azure RTOS NetX Duo is a dual IPv4 and IPv6 network stack, while NetX is the original IPv4 network stack, essentially a subset of Azure RTOS NetX Duo.</span></span>

### <a name="azure-rtos-usbx"></a><span data-ttu-id="bd272-135">Azure RTOS USBX</span><span class="sxs-lookup"><span data-stu-id="bd272-135">Azure RTOS USBX</span></span>

<span data-ttu-id="bd272-136">Azure RTOS USBXは、ハイ パフォーマンスの USB ホスト、デバイス、On-The-Go (OTG) の埋め込みスタックです。</span><span class="sxs-lookup"><span data-stu-id="bd272-136">Azure RTOS USBX is a high-performance USB host, device, and On-The-Go (OTG) embedded stack.</span></span> <span data-ttu-id="bd272-137">ThreadX と完全に統合されており、Azure RTOS ThreadX でサポートされているすべてのプロセッサで利用できます。</span><span class="sxs-lookup"><span data-stu-id="bd272-137">It is fully integrated with ThreadX and is available for all Azure RTOS ThreadX supported processors.</span></span> <span data-ttu-id="bd272-138">Azure RTOS ThreadX と同様に、Azure RTOS USBX は、小さいフットプリントでハイパフォーマンスを実現するように設計されているため、USB デバイスとのインターフェイスを必要とする深く組み込まれたアプリケーションに最適です。</span><span class="sxs-lookup"><span data-stu-id="bd272-138">Like Azure RTOS ThreadX, Azure RTOS USBX is designed to have a small footprint and high performance, making it ideal for deeply embedded applications that require an interface with USB devices.</span></span>

### <a name="windows-tools"></a><span data-ttu-id="bd272-139">Windows ツール</span><span class="sxs-lookup"><span data-stu-id="bd272-139">Windows tools</span></span>

<span data-ttu-id="bd272-140">Azure RTOS GUIX には完全な GUI アプリケーション デザイン環境が用意されており、アプリケーションの GUI のすべてのグラフィカル要素を容易に作成および保守できます。</span><span class="sxs-lookup"><span data-stu-id="bd272-140">Azure RTOS GUIX Studio provides a complete GUI application design environment, facilitating the creation and maintenance of all graphical elements in the application's GUI.</span></span> <span data-ttu-id="bd272-141">Azure RTOS GUIX Studio によって、Azure RTOS GUIX ライブラリと互換性がある C コードが自動的に生成されます。これはターゲット上でコンパイルおよび実行できます。</span><span class="sxs-lookup"><span data-stu-id="bd272-141">Azure RTOS GUIX Studio automatically generates C code compatible with the Azure RTOS GUIX library, ready to be compiled and run on the target.</span></span>

<span data-ttu-id="bd272-142">Azure RTOS TraceX は、開発者がリアルタイム システムのイベントをグラフィカルに表示し、リアルタイム システムの動作への理解を深めることができる、ホストベースの分析ツールです。</span><span class="sxs-lookup"><span data-stu-id="bd272-142">Azure RTOS TraceX is a host-based analysis tool that provides developers with a graphical view of real-time system events and enables them to visualize and better understand the behavior of their real-time systems.</span></span>

## <a name="the-azure-rtos-advantage"></a><span data-ttu-id="bd272-143">Azure RTOS の利点</span><span class="sxs-lookup"><span data-stu-id="bd272-143">The Azure RTOS Advantage</span></span>
<span data-ttu-id="bd272-144">Azure RTOS には、他のリアルタイム オペレーティング システムに比べて次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="bd272-144">Azure RTOS provides the following advantages over other real-time operating systems.</span></span>

### <a name="intuitive-and-consistent-api-design"></a><span data-ttu-id="bd272-145">直感的で一貫性のある API のデザイン</span><span class="sxs-lookup"><span data-stu-id="bd272-145">Intuitive and consistent API design</span></span>

* <span data-ttu-id="bd272-146">直感的で一貫性のある API。</span><span class="sxs-lookup"><span data-stu-id="bd272-146">Intuitive and consistent API.</span></span>
* <span data-ttu-id="bd272-147">名詞 - 動詞の名前付け規則。</span><span class="sxs-lookup"><span data-stu-id="bd272-147">Noun-verb naming convention.</span></span>
* <span data-ttu-id="bd272-148">すべての API には、ThreadX の *tx_* や FileX の *nx_* など、先頭にプレフィックスが付けられており、それらが所属する Azure RTOS コンポーネントを簡単に識別可能。</span><span class="sxs-lookup"><span data-stu-id="bd272-148">All APIs have leading prefix, such as *tx_* for ThreadX and *nx_* for FileX, to easily identify the Azure RTOS component they belong to.</span></span>
* <span data-ttu-id="bd272-149">ブロックしている API にオプションのスレッド タイムアウトがある</span><span class="sxs-lookup"><span data-stu-id="bd272-149">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="bd272-150">多数の API をアプリケーション ISR から直接利用可能。</span><span class="sxs-lookup"><span data-stu-id="bd272-150">Many APIs are directly available from application ISRs.</span></span>
- <span data-ttu-id="bd272-151">メディアとファイルを操作するための省略可能なユーザー通知コールバック。</span><span class="sxs-lookup"><span data-stu-id="bd272-151">Optional user-notification callbacks for media and file operations.</span></span>
* <span data-ttu-id="bd272-152">イベントドリブン プログラミング モデル (API)。</span><span class="sxs-lookup"><span data-stu-id="bd272-152">Event-driven programming model (API).</span></span>

### <a name="high-efficiency"></a><span data-ttu-id="bd272-153">高効率</span><span class="sxs-lookup"><span data-stu-id="bd272-153">High efficiency</span></span>

- <span data-ttu-id="bd272-154">小さいコード フットプリント。</span><span class="sxs-lookup"><span data-stu-id="bd272-154">Small code footprint.</span></span>
- <span data-ttu-id="bd272-155">使用されるサービスに基づいたスケーラブルなコード フットプリント。</span><span class="sxs-lookup"><span data-stu-id="bd272-155">Scalable code footprint based on the services used.</span></span>
- <span data-ttu-id="bd272-156">TUV および UL による IEC 61508 SIL 4、IEC 62304 クラス C、ISO 26262 ASIL D、および EN 50128 SW-SIL4 に対する事前認定。</span><span class="sxs-lookup"><span data-stu-id="bd272-156">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4.</span></span>
- <span data-ttu-id="bd272-157">高速実行。</span><span class="sxs-lookup"><span data-stu-id="bd272-157">Fast execution.</span></span>

### <a name="fastest-time-to-market"></a><span data-ttu-id="bd272-158">市場投入までの時間を最短化</span><span class="sxs-lookup"><span data-stu-id="bd272-158">Fastest time-to-market</span></span>

<span data-ttu-id="bd272-159">Azure RTOS は、インストール、習得、使用、デバッグ、検証、認定、保守が簡単です。</span><span class="sxs-lookup"><span data-stu-id="bd272-159">Azure RTOS is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="bd272-160">その結果、Azure RTOS は、Broadcom や Gainspan などが提供する多くの SoC を含む、組み込み型 IoT デバイス向けの最も一般的なリアルタイム オペレーティング システムの 1 つとなっています。</span><span class="sxs-lookup"><span data-stu-id="bd272-160">As a result, Azure RTOS is one of the most popular real time operating systems for embedded IoT devices, including many SoCs from Broadcom, Gainspan, and so forth.</span></span> <span data-ttu-id="bd272-161">一貫した市場投入までの時間の優位性は、次の要素を基に構築されています。</span><span class="sxs-lookup"><span data-stu-id="bd272-161">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="bd272-162">完全なソース コードを提供。</span><span class="sxs-lookup"><span data-stu-id="bd272-162">Complete source code availability.</span></span>
* <span data-ttu-id="bd272-163">使いやすい API。</span><span class="sxs-lookup"><span data-stu-id="bd272-163">Easy-to-use API.</span></span>
* <span data-ttu-id="bd272-164">包括的かつ高度な機能セット。</span><span class="sxs-lookup"><span data-stu-id="bd272-164">Comprehensive and advanced feature set.</span></span>

### <a name="one-simple-license"></a><span data-ttu-id="bd272-165">シンプルな 1 つのライセンス</span><span class="sxs-lookup"><span data-stu-id="bd272-165">One Simple License</span></span>

<span data-ttu-id="bd272-166">ソース コードの使用とテストにコストはかかりません。事前にライセンスされたデバイスに展開する場合は、運用環境ライセンスのコストもかかりません。他のすべてのデバイスには、シンプルな年間ライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="bd272-166">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

### <a name="full-highest-quality-source-code"></a><span data-ttu-id="bd272-167">最高品質の完全なソース コード</span><span class="sxs-lookup"><span data-stu-id="bd272-167">Full, highest-quality source code</span></span>

<span data-ttu-id="bd272-168">長年にわたり、Azure RTOS のソース コードは、品質とわかりやすさに一定の基準を設けてきました。</span><span class="sxs-lookup"><span data-stu-id="bd272-168">Throughout the years, Azure RTOS source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="bd272-169">また、ファイルごとに 1 つの関数を使用するという規則により、簡単なソース ナビゲーションが実現されます。</span><span class="sxs-lookup"><span data-stu-id="bd272-169">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

### <a name="pre-certified-by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="bd272-170">TUV と UL による多くの安全性標準による事前認定</span><span class="sxs-lookup"><span data-stu-id="bd272-170">Pre-certified by TUV and UL to many safety standards</span></span>

<span data-ttu-id="bd272-171">Azure RTOS は、IEC-61508 SIL 4、IEC-62304 SW セーフティ クラス C、ISO 26262 ASIL D、および EN 50128 に従って、安全性が重要なシステムでの使用が SGS-TUV Saar によって認定されています。</span><span class="sxs-lookup"><span data-stu-id="bd272-171">Azure RTOS has been certified by SGS-TUV  Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="bd272-172">この認定により、「電気、電子、プログラマブル電子安全関連系の機能安全」に関する IEC-61508、IEC-62304、ISO 26262、および EN 50128 の最高の安全性整合性レベルに対応する安全性関連ソフトウェアの開発で Azure RTOS を使用できることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="bd272-172">The certification confirms that Azure RTOS can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="bd272-173">ドイツの SGS-Group と TUV Saarland の共同事業を通じて結成された SGS-TUV Saar は、世界中の安全関連システムのための組み込みソフトウェアのテスト、監査、検証、認定を行う、世界有数の公認された独立系企業になりました。</span><span class="sxs-lookup"><span data-stu-id="bd272-173">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying, and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="bd272-174">工業安全規格の IEC 61508 と、それから派生したすべての標準 (IEC-62304、ISO 26262 および EN 50128 を含む) は、電気・電子・プログラマブル電子安全関連の医療デバイス、プロセス制御システム、工業機械、自動車および鉄道制御システムの機能安全を保証するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd272-174">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

:::image type="content" source="media/partener-logo-sgs-tuv-saar.png" alt-text="SGS-TUV 認定":::

<span data-ttu-id="bd272-176">Azure RTOS は、プログラム可能なコンポーネント内のソフトウェアに対する UL 60730-1 付属文書 H、CSA E60730-1 付属文書 H、IEC 60730-1 付属文書 H、UL 60335-1 付属文書 R、IEC 60335-1 付属文書 R、UL 1998 の各安全標準に準拠しているものとして UL によって承認されています。</span><span class="sxs-lookup"><span data-stu-id="bd272-176">Azure RTOS has been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="bd272-177">UL は、独立した安全科学のグローバル企業であり、電気の公的な選定からサステナビリティ、再生可能エネルギー、およびナノテクノロジーにおける革新まで、さまざまな安全性ソリューションの革新を 1 世紀以上にわたって専門としてきました。</span><span class="sxs-lookup"><span data-stu-id="bd272-177">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

:::image type="content" source="media/cru-logo-certification.png" alt-text="CRU UL 認定":::

<span data-ttu-id="bd272-179">TUV および UL 認定に関連付けられている成果物 (証明書、安全性マニュアル、テスト レポートなど) は、販売されています。</span><span class="sxs-lookup"><span data-stu-id="bd272-179">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

<span data-ttu-id="bd272-180">アプリケーションで追加の認定が必要な場合は、Microsoft を通じて認定サービスを利用し、実際のハードウェア プラットフォームを使用してさまざまな標準にターンキー認定を提供したり、アプリケーション コードをカバーしたりできます。</span><span class="sxs-lookup"><span data-stu-id="bd272-180">In cases where the application needs additional certification, a certification service is available through Microsoft for providing turn-key certification to various standards using the actual hardware platform and even covering the application code.</span></span> <span data-ttu-id="bd272-181">認定サービスの詳細については、お問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="bd272-181">Contact us for more details on our certification service.</span></span>

### <a name="eal4-common-criteria-security-certification"></a><span data-ttu-id="bd272-182">EAL4+ コモン クライテリア セキュリティ認定</span><span class="sxs-lookup"><span data-stu-id="bd272-182">EAL4+ Common Criteria security certification</span></span>

<span data-ttu-id="bd272-183">Azure RTOS は、EAL4+ のコモン クライテリア セキュリティ認定を達成しました。</span><span class="sxs-lookup"><span data-stu-id="bd272-183">Azure RTOS has achieved EAL4+ Common Criteria security certification.</span></span> <span data-ttu-id="bd272-184">評価対象 (TOE) は、Azure RTOS ThreadX、Azure RTOS NetX-Duo、Azure RTOS NetX Secure TLS、および Azure RTOS NetX MQTT です。</span><span class="sxs-lookup"><span data-stu-id="bd272-184">The Target of Evaluation (TOE) covers Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS, and Azure RTOS NetX MQTT.</span></span> <span data-ttu-id="bd272-185">これは、深い埋め込み型センサー、デバイス、エッジ ルーター、およびゲートウェイに必要な最も一般的な IoT プロトコルを表します。</span><span class="sxs-lookup"><span data-stu-id="bd272-185">This represents the most typical IoT protocols required by deeply embedded sensors, devices, edge routers, and gateways.</span></span>

:::image type="content" source="media/eal-logo-certification.png" alt-text="EAL 認定":::

<span data-ttu-id="bd272-187">Microsoft Azure RTOS SC セキュリティ認定に使用される IT セキュリティ評価機関は Brightsight BV で、証明機関は SERTIT です。</span><span class="sxs-lookup"><span data-stu-id="bd272-187">The IT Security Evaluation Facility used for the Microsoft Azure RTOS SC security certification is Brightsight BV and the Certification Authority is SERTIT.</span></span>

### <a name="fips-140-2-validated"></a><span data-ttu-id="bd272-188">FIPS 140-2 の検証</span><span class="sxs-lookup"><span data-stu-id="bd272-188">FIPS 140-2 Validated</span></span>

<span data-ttu-id="bd272-189">Azure RTOS Crypto ライブラリは、暗号化モジュールの要件を指定する、Federal Information Processing Standards 140-2 (FIPS 140-2) のソフトウェアの認定を受けています。</span><span class="sxs-lookup"><span data-stu-id="bd272-189">Azure RTOS Crypto libraries have achieved Federal Information Processing Standardization 140-2 (FIPS 140-2) Certification for software, which specifies requirements for cryptography modules.</span></span> <span data-ttu-id="bd272-190">FIPS 140-2 では、暗号化ベースのセキュリティを使用するすべての連邦政府機関および部門が、暗号化の強度と機能に関連する特定の標準を満たすことが求められています。</span><span class="sxs-lookup"><span data-stu-id="bd272-190">FIPS 140-2 requires all federal government agencies and departments that use cryptographic-based security to meet specific standards related to encryption strength and capabilities.</span></span> <span data-ttu-id="bd272-191">これらの暗号化ベースのセキュリティ標準は、カナダと欧州連合でも承認されています。</span><span class="sxs-lookup"><span data-stu-id="bd272-191">These cryptographic-based security standards are also recognized in Canada and the European Union.</span></span>

<span data-ttu-id="bd272-192">Azure RTOS Crypt ライブラリに使用される情報セキュリティ評価ラボは atsec でした。証明機関は[米国国立標準技術研究所 (NIST)](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394) です。</span><span class="sxs-lookup"><span data-stu-id="bd272-192">The Information Security evaluation lab used for Azure RTOS Crypto libraries was atsec and the certification authority is [The National Institute of Standards and Technology (NIST)](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394).</span></span>

### <a name="supports-most-popular-architectures"></a><span data-ttu-id="bd272-193">最も一般的なアーキテクチャをサポート</span><span class="sxs-lookup"><span data-stu-id="bd272-193">Supports most popular architectures</span></span>

<span data-ttu-id="bd272-194">Azure RTOS は、完全にテストされ、サポートされている、すぐに使える最も一般的な 32 および 64 ビット マイクロプロセッサで動作します。これには、次の高度なアーキテクチャが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bd272-194">Azure RTOS on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following advanced architectures:</span></span>

<span data-ttu-id="bd272-195">**Analog Devices**: SHARC、Blackfin、CM4xx</span><span class="sxs-lookup"><span data-stu-id="bd272-195">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="bd272-196">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="bd272-196">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="bd272-197">**Ambiqmicro**: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="bd272-197">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="bd272-198">**ARM**: ARM7、ARM9、ARM11、Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64 ビット/A7x 64 ビット/R4/R5、TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="bd272-198">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="bd272-199">**Cadence**: Xtensa、Diamond</span><span class="sxs-lookup"><span data-stu-id="bd272-199">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="bd272-200">**CEVA**: PSoC、PSoC 4、PSoC 5、PSoC 6、FM0+、FM3、MF4、WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="bd272-200">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="bd272-201">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="bd272-201">**Cypress**: RISC-V</span></span>

<span data-ttu-id="bd272-202">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="bd272-202">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="bd272-203">**Infineon**: XMC1000、XMC4000、TriCore</span><span class="sxs-lookup"><span data-stu-id="bd272-203">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="bd272-204">**Intel および Intel FPGA**: x36/Pentium、XScale、NIOS II、Cyclone、Arria 10</span><span class="sxs-lookup"><span data-stu-id="bd272-204">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="bd272-205">**Microchip**: AVR32、ARM7、ARM9、Cortex-M3/M4/M7、SAM3/4/7/9/A/C/D/E/G/L/SV、PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="bd272-205">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="bd272-206">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="bd272-206">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="bd272-207">**NXP**: LPC、ARM7、ARM9、PowerPC、68 K、i.MX、ColdFire、Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="bd272-207">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="bd272-208">**Renesas**: SH、HS、V850、RX、RZ、Synergy</span><span class="sxs-lookup"><span data-stu-id="bd272-208">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="bd272-209">**Silicon Labs**: EFM32</span><span class="sxs-lookup"><span data-stu-id="bd272-209">**Silicon Labs**: EFM32</span></span>

<span data-ttu-id="bd272-210">**Synopsys**: ARC 600、700、ARC EM、ARC HS</span><span class="sxs-lookup"><span data-stu-id="bd272-210">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="bd272-211">**ST**: STM32、ARM7、ARM9、Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="bd272-211">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="bd272-212">**Tl**: C5xxx、C6xxx、Stellaris、Sitara、Tiva-C</span><span class="sxs-lookup"><span data-stu-id="bd272-212">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="bd272-213">**Wave Computing**: MIPS32 4K、24 K、34 K、1004 K、MIPS64 5K、microAptiv、interAptiv、proAptiv、M-Class</span><span class="sxs-lookup"><span data-stu-id="bd272-213">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="bd272-214">**Xilinx**: MicroBlaze、PowerPC 405、ZYNQ、ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="bd272-214">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="bd272-215">*記載されているタイミングとサイズの数値はすべて推定値であり、開発プラットフォームによって異なる場合があります。*</span><span class="sxs-lookup"><span data-stu-id="bd272-215">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>

## <a name="in-the-context-of-azure-iot"></a><span data-ttu-id="bd272-216">Azure IoT のコンテキストで</span><span class="sxs-lookup"><span data-stu-id="bd272-216">In the context of Azure IoT</span></span>

<span data-ttu-id="bd272-217">Azure IoT に直接接続したり、Azure IoT Edge 経由で間接的に接続したりするだけでなく、Azure Sphere デバイスでも Azure RTOS を利用できます。</span><span class="sxs-lookup"><span data-stu-id="bd272-217">In addition to directly connecting to Azure IoT or indirectly connecting through Azure IoT Edge, Azure RTOS is also available on Azure Sphere devices.</span></span> <span data-ttu-id="bd272-218">Azure RTOS と Azure Sphere を組み合わせることにより、クラス最高のリアルタイム処理とセキュリティを 1 つのデバイスでまとめて実現できます。</span><span class="sxs-lookup"><span data-stu-id="bd272-218">The combination of Azure RTOS and Azure Sphere bring best-of-class real-time processing and security together in one device.</span></span>
