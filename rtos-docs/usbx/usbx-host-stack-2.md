---
title: 第 2 章 - Azure RTOS USBX ホスト スタックのインストール
description: USBX ホスト スタックをインストールする方法について説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 4c33f95b8ac268c557fd947a1303ec3af315a37e
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377086"
---
# <a name="chapter-2---azure-rtos-usbx-host-stack-installation"></a><span data-ttu-id="be6da-103">第 2 章 - Azure RTOS USBX ホスト スタックのインストール</span><span class="sxs-lookup"><span data-stu-id="be6da-103">Chapter 2 - Azure RTOS USBX Host Stack Installation</span></span>

## <a name="host-considerations"></a><span data-ttu-id="be6da-104">ホストに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="be6da-104">Host Considerations</span></span>

### <a name="computer-type"></a><span data-ttu-id="be6da-105">コンピューターの種類</span><span class="sxs-lookup"><span data-stu-id="be6da-105">Computer Type</span></span>

<span data-ttu-id="be6da-106">埋め込み開発は、通常、Windows PC または Unix ホスト コンピューター上で行われます。</span><span class="sxs-lookup"><span data-stu-id="be6da-106">Embedded development is usually performed on Windows PC or Unix host computers.</span></span> <span data-ttu-id="be6da-107">アプリケーションは、ホスト上でコンパイル、リンク、および配置された後、実行のためにターゲット ハードウェアにダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="be6da-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

### <a name="download-interfaces"></a><span data-ttu-id="be6da-108">ダウンロードのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="be6da-108">Download Interfaces</span></span>

<span data-ttu-id="be6da-109">通常、ターゲットのダウンロードは RS-232 のシリアル インターフェイスで行われますが、パラレル インターフェイス、USB、およびイーサネットも普及してきています。</span><span class="sxs-lookup"><span data-stu-id="be6da-109">Usually, the target download is done over an RS-232 serial interface, although parallel interfaces, USB, and Ethernet are becoming more popular.</span></span> <span data-ttu-id="be6da-110">使用可能なオプションについては、開発ツールのドキュメントをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="be6da-110">See the development tool documentation for available options.</span></span>

### <a name="debugging-tools"></a><span data-ttu-id="be6da-111">デバッグ ツール</span><span class="sxs-lookup"><span data-stu-id="be6da-111">Debugging Tools</span></span>

<span data-ttu-id="be6da-112">デバッグは、通常、プログラム イメージのダウンロードと同じリンクを使って行われます。</span><span class="sxs-lookup"><span data-stu-id="be6da-112">Debugging is done typically over the same link as the program image download.</span></span> <span data-ttu-id="be6da-113">デバッガーには、ターゲット上で動作する小さなモニター プログラムから、バックグラウンド デバッグ モニター (BDM) ツールやインサーキット エミュレーター (ICE) ツールまで、さまざまなものがあります。</span><span class="sxs-lookup"><span data-stu-id="be6da-113">A variety of debuggers exist, ranging from small monitor programs running on the target through Background Debug Monitor (BDM) and In-Circuit Emulator (ICE) tools.</span></span> <span data-ttu-id="be6da-114">ICE ツールには、実際のターゲット ハードウェアの最も堅牢なデバッグ機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="be6da-114">The ICE tool provides the most robust debugging of actual target hardware.</span></span>

### <a name="required-hard-disk-space"></a><span data-ttu-id="be6da-115">必要なハード ディスク容量</span><span class="sxs-lookup"><span data-stu-id="be6da-115">Required Hard Disk Space</span></span>

<span data-ttu-id="be6da-116">USBX のソース コードは ASCII 形式で提供され、ホスト コンピューターのハード ディスク上に約 500 KB の空き領域が必要です。</span><span class="sxs-lookup"><span data-stu-id="be6da-116">The source code for USBX is delivered in ASCII format and requires approximately 500 KBytes of space on the host computer's hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="be6da-117">ターゲットに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="be6da-117">Target Considerations</span></span>

<span data-ttu-id="be6da-118">USBX は、ホスト モードでターゲット上に 24 KB から 64 KB の読み取り専用メモリ (ROM) を必要とします。</span><span class="sxs-lookup"><span data-stu-id="be6da-118">USBX requires between 24 KBytes and 64 KBytes of Read Only Memory (ROM) on the target in host mode.</span></span> <span data-ttu-id="be6da-119">必要なメモリ容量は、使用するコントローラーの種類と、USBX にリンクされている USB クラスによって異なります。</span><span class="sxs-lookup"><span data-stu-id="be6da-119">The amount of memory required is dependent on the type of controller used and the USB classes linked to USBX.</span></span> <span data-ttu-id="be6da-120">また、USBX グローバル データ構造およびメモリ プール用に、ターゲットのランダム アクセス メモリ (RAM) がさらに 32 KB 必要です。</span><span class="sxs-lookup"><span data-stu-id="be6da-120">Another 32 KBytes of the target's Random Access Memory (RAM) are required for USBX global data structures and memory pool.</span></span> <span data-ttu-id="be6da-121">このメモリ プールは、USB 上の予期されたデバイス数と USB コントローラーの種類に応じて調整することもできます。</span><span class="sxs-lookup"><span data-stu-id="be6da-121">This memory pool can also be adjusted depending on the expected number of devices on the USB and the type of USB controller.</span></span> <span data-ttu-id="be6da-122">USBX デバイス側には、デバイス コントローラーの種類に応じて、約 10K から 12K の ROM が必要です。</span><span class="sxs-lookup"><span data-stu-id="be6da-122">The USBX device side requires roughly 10-12 K of ROM depending on the type of device controller.</span></span> <span data-ttu-id="be6da-123">RAM メモリの使用量は、デバイスによってエミュレートされるクラスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="be6da-123">The RAM memory usage depends on the type of class emulated by the device.</span></span>

<span data-ttu-id="be6da-124">また、USBX は、複数スレッド保護のために、ThreadX セマフォ、ミューテックス、およびスレッドを利用しているほか、USB バス トポロジを監視するために I/O 中断および定期的な処理を行っています。</span><span class="sxs-lookup"><span data-stu-id="be6da-124">USBX also relies on ThreadX semaphores, mutexes, and threads for multiple thread protection, and I/O suspension and periodic processing for monitoring the USB bus topology.</span></span>

### <a name="product-distribution"></a><span data-ttu-id="be6da-125">製品の配布</span><span class="sxs-lookup"><span data-stu-id="be6da-125">Product Distribution</span></span>

<span data-ttu-id="be6da-126">Azure RTOS USBX は、<https://github.com/azure-rtos/usbx/> のパブリック ソース コード リポジトリから入手できます。</span><span class="sxs-lookup"><span data-stu-id="be6da-126">Azure RTOS USBX can be obtained from our public source code repository at <https://github.com/azure-rtos/usbx/>.</span></span>

<span data-ttu-id="be6da-127">以下は、リポジトリ内のいくつかの重要なファイルの一覧です。</span><span class="sxs-lookup"><span data-stu-id="be6da-127">The following is a list of several important files in the repository:</span></span>

- <span data-ttu-id="be6da-128">***ux_api.h***: この C ヘッダー ファイルには、すべてのシステム等価物、データ構造、およびサービス プロトタイプが含まれています。</span><span class="sxs-lookup"><span data-stu-id="be6da-128">***ux_api.h***: This C header file contains all system equates, data structures, and service prototypes.</span></span>
- <span data-ttu-id="be6da-129">***ux_port.h***: この C ヘッダー ファイルには、開発ツール固有のすべてのデータ定義とデータ構造が含まれています。</span><span class="sxs-lookup"><span data-stu-id="be6da-129">***ux_port.h***: This C header file contains all development-tool-specific data definitions and structures.</span></span>
- <span data-ttu-id="be6da-130">***ux.lib***: これは、USBX C ライブラリのバイナリ バージョンです。</span><span class="sxs-lookup"><span data-stu-id="be6da-130">***ux.lib***: This is the binary version of the USBX C library.</span></span> <span data-ttu-id="be6da-131">これは標準パッケージと共に配布されます。</span><span class="sxs-lookup"><span data-stu-id="be6da-131">It is distributed with the standard package.</span></span>
- <span data-ttu-id="be6da-132">***demo_usbx c***: シンプルな USBX デモが含まれる C ファイル</span><span class="sxs-lookup"><span data-stu-id="be6da-132">***demo_usbx.c***: The C file containing a simple USBX demo</span></span>

<span data-ttu-id="be6da-133">すべてのファイル名が小文字で表記されます。</span><span class="sxs-lookup"><span data-stu-id="be6da-133">All filenames are in lower-case.</span></span> <span data-ttu-id="be6da-134">この名前付け規則によって、コマンドを Unix 開発プラットフォームにより簡単に変換できます。</span><span class="sxs-lookup"><span data-stu-id="be6da-134">This naming convention makes it easier to convert the commands to Unix development platforms.</span></span>

## <a name="usbx-installation"></a><span data-ttu-id="be6da-135">USBX のインストール</span><span class="sxs-lookup"><span data-stu-id="be6da-135">USBX Installation</span></span>

<span data-ttu-id="be6da-136">USBX は、GitHub リポジトリをローカル コンピューターに複製することによってインストールされます。</span><span class="sxs-lookup"><span data-stu-id="be6da-136">USBX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="be6da-137">お使いの PC 上に USBX リポジトリの複製を作成するための一般的な構文を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be6da-137">The following is typical syntax for creating a clone of the USBX repository on your PC:</span></span>

```powershell
    git clone https://github.com/azure-rtos/usbx
```

<span data-ttu-id="be6da-138">GitHub メイン ページ上のダウンロード ボタンを使用して、リポジトリのコピーをダウンロードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="be6da-138">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="be6da-139">また、オンライン リポジトリのフロント ページ上で USBX ライブラリを構築する手順も紹介します。</span><span class="sxs-lookup"><span data-stu-id="be6da-139">You will also find instructions for building the USBX library on the front page of the online repository.</span></span>

<span data-ttu-id="be6da-140">次の一般的な手順は、事実上すべてのインストールに適用されます。</span><span class="sxs-lookup"><span data-stu-id="be6da-140">The following general instructions apply to virtually any installation:</span></span>

1. <span data-ttu-id="be6da-141">ホストのハード ドライブ上で以前 ThreadX をインストールした先と同じディレクトリを使用します。</span><span class="sxs-lookup"><span data-stu-id="be6da-141">Use the same directory in which you previously installed ThreadX on the host hard drive.</span></span> <span data-ttu-id="be6da-142">すべての USBX 名が一意で、以前の USBX インストールと競合することはありません。</span><span class="sxs-lookup"><span data-stu-id="be6da-142">All USBX names are unique and will not interfere with the previous USBX installation.</span></span>
2. <span data-ttu-id="be6da-143">_ *_tx_application_define_*\* の先頭または先頭付近に \***ux_system_initialize** _ への呼び出しを追加します。これは USBX リソースが初期化される場所です。</span><span class="sxs-lookup"><span data-stu-id="be6da-143">Add a call to ***ux_system_initialize** _ at or near the beginning of _ *_tx_application_define_.** This is where the USBX resources are initialized.</span></span>
3. <span data-ttu-id="be6da-144">***ux_host_stack_initialize*** への呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="be6da-144">Add a call to \***ux_host_stack_initialize\*.**</span></span>
4. <span data-ttu-id="be6da-145">必要な USBX を初期化するための呼び出しを 1 つ以上追加します。</span><span class="sxs-lookup"><span data-stu-id="be6da-145">Add one or more calls to initialize the required USBX.</span></span>
5. <span data-ttu-id="be6da-146">システム内で使用可能なホスト コントローラーを初期化するための呼び出しを 1 つ以上追加します。</span><span class="sxs-lookup"><span data-stu-id="be6da-146">Add one or more calls to initialize the host controllers available in the system.</span></span>
6. <span data-ttu-id="be6da-147">低レベルのハードウェア初期化および割り込みベクター ルーティングを追加するために、tx_low_level_initialize.c ファイルの変更が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="be6da-147">It may be required to modify the tx_low_level_initialize.c file to add low-level hardware initialization and interrupt vector routing.</span></span> <span data-ttu-id="be6da-148">これはハードウェア プラットフォームに固有であるため、ここでは説明しません。</span><span class="sxs-lookup"><span data-stu-id="be6da-148">This is specific to the hardware platform and will not be discussed here.</span></span>
7. <span data-ttu-id="be6da-149">アプリケーション ソース コードをコンパイルし、USBX および ThreadX ランタイム ライブラリ (USB ストレージ クラスや USB ネットワーク クラスをコンパイルする場合は、FileX や Netx も必要になる場合があります)、ux. a (または ux.lib)、および tx.a (または tx.lib) とリンクします。</span><span class="sxs-lookup"><span data-stu-id="be6da-149">Compile application source code and link with the USBX and ThreadX run time libraries (FileX and/or Netx may also be required if the USB storage class and/or USB network classes are to be compiled in), ux.a (or ux.lib) and tx.a (or tx.lib).</span></span> <span data-ttu-id="be6da-150">結果はターゲットにダウンロードして、実行できます。</span><span class="sxs-lookup"><span data-stu-id="be6da-150">The resulting can be downloaded to the target and executed.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="be6da-151">構成オプション</span><span class="sxs-lookup"><span data-stu-id="be6da-151">Configuration Options</span></span>

<span data-ttu-id="be6da-152">USBX ライブラリを構築するための構成オプションはいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="be6da-152">There are several configuration options for building the USBX library.</span></span> <span data-ttu-id="be6da-153">オプションはすべて ***ux_user.h*** にあります。</span><span class="sxs-lookup"><span data-stu-id="be6da-153">All options are located in the ***ux_user.h***.</span></span>

<span data-ttu-id="be6da-154">各構成オプションの詳細を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="be6da-154">The list below details each configuration option.</span></span>


- <span data-ttu-id="be6da-155">**UX_PERIODIC_RATE**: この値は、特定のハードウェア プラットフォームの 1 秒あたりのティック数を表します。</span><span class="sxs-lookup"><span data-stu-id="be6da-155">**UX_PERIODIC_RATE**: This value represents how many ticks per seconds for a specific hardware platform.</span></span> <span data-ttu-id="be6da-156">既定値は 1000 で、ミリ秒あたり 1 ティックを示します。</span><span class="sxs-lookup"><span data-stu-id="be6da-156">The default is 1000 indicating one tick per millisecond.</span></span>
- <span data-ttu-id="be6da-157">**UX_MAX_CLASS_DRIVER**: この値は、USBX によって読み込むことができるクラスの最大数です。</span><span class="sxs-lookup"><span data-stu-id="be6da-157">**UX_MAX_CLASS_DRIVER**: This value is the maximum number of classes that can be loaded by USBX.</span></span> <span data-ttu-id="be6da-158">この値はクラス コンテナーを表します。クラスのインスタンス数ではありません。</span><span class="sxs-lookup"><span data-stu-id="be6da-158">This value represents the class container and not the number of instances of a class.</span></span> <span data-ttu-id="be6da-159">たとえば、USBX の特定の実装にハブ クラス、プリンター クラス、およびストレージ クラスが必要な場合、これらのクラスに属するデバイスの数に関係なく、UX_MAX_CLASS_DRIVER 値は 3 に設定できます。</span><span class="sxs-lookup"><span data-stu-id="be6da-159">For instance, if a particular implementation of USBX needs the hub class, the printer class, and the storage class, then the UX_MAX_CLASS_DRIVER value can be set to 3 regardless of the number of devices that belong to these classes.</span></span>
- <span data-ttu-id="be6da-160">**UX_MAX_HCD**: この値は、システム内で使用できるさまざまなホスト コントローラーの数を表します。</span><span class="sxs-lookup"><span data-stu-id="be6da-160">**UX_MAX_HCD**: This value represents the number of different host controllers that are available in the system.</span></span> <span data-ttu-id="be6da-161">USB 1.1 サポートの場合、この値はほとんどが 1 になります。</span><span class="sxs-lookup"><span data-stu-id="be6da-161">For USB 1.1 support, this value will mostly be 1.</span></span> <span data-ttu-id="be6da-162">USB 2.0 サポートの場合、この値には 1 より大きい値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="be6da-162">For USB 2.0 support this value can be more than 1.</span></span> <span data-ttu-id="be6da-163">この値は、同時に実行されているホスト コントローラーの数を表します。</span><span class="sxs-lookup"><span data-stu-id="be6da-163">This value represents the number of concurrent host controllers running at the same time.</span></span> <span data-ttu-id="be6da-164">たとえば、OHCI のインスタンスが 2 つ実行されている場合、または EHCI コントローラーと OHCI コントローラーが 1 つずつ実行されている場合、UX_MAX_HCD は 2 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="be6da-164">If for instance, there are two instances of OHCI running or one EHCI and one OHCI controllers running, the UX_MAX_HCD should be set to 2.</span></span> 
- <span data-ttu-id="be6da-165">**UX_MAX_DEVICES**: この値は、USB にアタッチできるデバイスの最大数を表します。</span><span class="sxs-lookup"><span data-stu-id="be6da-165">**UX_MAX_DEVICES**: This value represents the maximum number of devices that can be attached to the USB.</span></span> <span data-ttu-id="be6da-166">通常、単一 USB 上の理論上の最大数は 127 デバイスです。</span><span class="sxs-lookup"><span data-stu-id="be6da-166">Normally, the theoretical maximum number on a single USB is 127 devices.</span></span> <span data-ttu-id="be6da-167">この値は、メモリを節約するためにスケールダウンできます。</span><span class="sxs-lookup"><span data-stu-id="be6da-167">This value can be scaled down to conserve memory.</span></span> <span data-ttu-id="be6da-168">この値は、システム内の USB バスの数に関係なく、デバイスの合計数を表すことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="be6da-168">It should be noted that this value represents the total number of devices regardless of the number of USB buses in the system.</span></span>
- <span data-ttu-id="be6da-169">**UX_MAX_ED**: この値は、コントローラー プール内の ED の最大数を表します。</span><span class="sxs-lookup"><span data-stu-id="be6da-169">**UX_MAX_ED**: This value represents the maximum number of EDs in the controller pool.</span></span> <span data-ttu-id="be6da-170">この数は 1 つのコントローラーにのみ割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="be6da-170">This number is assigned to one controller only.</span></span> <span data-ttu-id="be6da-171">コントローラーのインスタンスが複数存在する場合、この値は、個別のコントローラーごとに使用されます。</span><span class="sxs-lookup"><span data-stu-id="be6da-171">If multiple instances of controllers are present, this value is used by each individual controller.</span></span>
- <span data-ttu-id="be6da-172">**UX_MAX_TD と UX_MAX_ISO_TD**: この値は、コントローラー プール内の標準 TD およびアイソクロナス TD の最大数を表します。</span><span class="sxs-lookup"><span data-stu-id="be6da-172">**UX_MAX_TD and UX_MAX_ISO_TD**: This value represents the maximum number of regular and isochronous TDs in the controller pool.</span></span> <span data-ttu-id="be6da-173">この数は 1 つのコントローラーにのみ割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="be6da-173">This number is assigned to one controller only.</span></span> <span data-ttu-id="be6da-174">コントローラーのインスタンスが複数存在する場合、この値は、個別のコントローラーごとに使用されます。</span><span class="sxs-lookup"><span data-stu-id="be6da-174">If multiple instances of controllers are present, this value is used by each individual controller.</span></span>
- <span data-ttu-id="be6da-175">**UX_THREAD_STACK_SIZE**: この値は、USBX スレッド用のスタックのサイズ (バイト単位) です。</span><span class="sxs-lookup"><span data-stu-id="be6da-175">**UX_THREAD_STACK_SIZE**: This value is the size of the stack in bytes for the USBX threads.</span></span> <span data-ttu-id="be6da-176">これは、通常、使用されるプロセッサとホスト コントローラーに応じて、1024 バイトまたは 2048 バイトになります。</span><span class="sxs-lookup"><span data-stu-id="be6da-176">It can be typically 1024 bytes or 2048 bytes depending on the processor used and the host controller.</span></span>
- <span data-ttu-id="be6da-177">**UX_HOST_ENUM_THREAD_STACK_SIZE**: この値は、USB ホスト列挙スレッドのスタック サイズです。</span><span class="sxs-lookup"><span data-stu-id="be6da-177">**UX_HOST_ENUM_THREAD_STACK_SIZE**: This value is the stack size of the USB host enumeration thread.</span></span> <span data-ttu-id="be6da-178">このシンボルが設定されていない場合、USBX ホスト列挙スレッドのスタック サイズは **UX_THREAD_STACK_SIZE** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="be6da-178">If this symbol I not set, the USBX host enumeration thread stack size is set to **UX_THREAD_STACK_SIZE**.</span></span> 
- <span data-ttu-id="be6da-179">**UX_HOST_HCD_THREAD_STACK_SIZE**: この値は、USB ホスト HCD スレッドのスタック サイズです。</span><span class="sxs-lookup"><span data-stu-id="be6da-179">**UX_HOST_HCD_THREAD_STACK_SIZE**: This value is the stack size of the USB host HCD thread.</span></span> <span data-ttu-id="be6da-180">このシンボルが設定されていない場合、USBX ホスト HCD スレッドのスタック サイズは **UX_THREAD_STACK_SIZE** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="be6da-180">If this symbol I not set, the USBX host HCD thread stack size is set to **UX_THREAD_STACK_SIZE**.</span></span>
- <span data-ttu-id="be6da-181">**UX_THREAD_PRIORITY_ENUM**: これは、バス トポロジを監視する USBX 列挙スレッドの ThreadX 優先度の値です。</span><span class="sxs-lookup"><span data-stu-id="be6da-181">**UX_THREAD_PRIORITY_ENUM**: This is the ThreadX priority value for the USBX enumeration threads that monitors the bus topology.</span></span>
- <span data-ttu-id="be6da-182">**UX_THREAD_PRIORITY_CLASS**: これは、標準 USBX スレッドの ThreadX 優先度の値です。</span><span class="sxs-lookup"><span data-stu-id="be6da-182">**UX_THREAD_PRIORITY_CLASS**: This is the ThreadX priority value for the standard USBX threads.</span></span>
- <span data-ttu-id="be6da-183">**UX_THREAD_PRIORITY_KEYBOARD**: これは、USBX HID キーボード クラスの ThreadX 優先度の値です。</span><span class="sxs-lookup"><span data-stu-id="be6da-183">**UX_THREAD_PRIORITY_KEYBOARD**: This is the ThreadX priority value for the USBX HID keyboard class.</span></span>
- <span data-ttu-id="be6da-184">**UX_THREAD_PRIORITY_HCD**: これは、ホスト コントローラー スレッドの ThreadX 優先度の値です。</span><span class="sxs-lookup"><span data-stu-id="be6da-184">**UX_THREAD_PRIORITY_HCD**: This is the ThreadX priority value for the host controller thread.</span></span>
- <span data-ttu-id="be6da-185">**UX_NO_TIME_SLICE**: この値は、スレッドに使用されるタイム スライスを実際に定義します。</span><span class="sxs-lookup"><span data-stu-id="be6da-185">**UX_NO_TIME_SLICE**: This value actually defines the time slice that will be used for threads.</span></span> <span data-ttu-id="be6da-186">たとえば、0 に定義されている場合、ThreadX ターゲット ポートはタイム スライスを使用しません。</span><span class="sxs-lookup"><span data-stu-id="be6da-186">For example, if defined to 0, the ThreadX target port does not use time slices.</span></span>
- <span data-ttu-id="be6da-187">**UX_MAX_HOST_LUN**: この値は、ホスト ストレージ クラス ドライバー内で表される SCSI 論理ユニットの最大数を表します。</span><span class="sxs-lookup"><span data-stu-id="be6da-187">**UX_MAX_HOST_LUN**: This value represents the maximum number of SCSI logical units represented in the host storage class driver.</span></span>
- <span data-ttu-id="be6da-188">**UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: 定義されている場合、この値には、CB または CBI プロトコル (フロッピー ディスクなど) を使用するストレージ デバイスを処理するコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="be6da-188">**UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: If defined, this value includes code to handle storage devices that use the CB or CBI protocol (such as floppy disks).</span></span> <span data-ttu-id="be6da-189">これらのプロトコルは古い形式で、事実上すべての最新ストレージ デバイスで使用されてい BOT (Bulk Only Transport) プロトコルで置き換えられています。このため、これは既定ではオフになっています。</span><span class="sxs-lookup"><span data-stu-id="be6da-189">It is off by default because these protocols are obsolete, being superseded by the Bulk Only Transport (BOT protocol, which virtually all modern storage devices use.</span></span>
- <span data-ttu-id="be6da-190">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: この値が定義されている場合、ux_host_class_hid_keyboard_key_get は、キーの変更、つまりキー押下とキー リリースのみを報告します。</span><span class="sxs-lookup"><span data-stu-id="be6da-190">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: If defined, this value causes ux_host_class_hid_keyboard_key_get to only report key changes that is, key presses and key releases.</span></span> <span data-ttu-id="be6da-191">既定では、キーが押されたときのみ報告します。</span><span class="sxs-lookup"><span data-stu-id="be6da-191">By default, it only reports when a key is down.</span></span>
- <span data-ttu-id="be6da-192">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** が定義されている場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="be6da-192">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="be6da-193">定義されている場合、ux_host_class_hid_keyboard_key_get は、キー押下/ダウンの変更のみを報告します。キー リリース/アップの変更は報告されません。</span><span class="sxs-lookup"><span data-stu-id="be6da-193">If defined, causes ux_host_class_hid_keyboard_key_get to only report key pressed/down changes; key released/up changes are not reported.</span></span>
- <span data-ttu-id="be6da-194">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS**: **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** が定義されている場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="be6da-194">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="be6da-195">定義されている場合、ux_host_class_hid_keyboard_key_get は、キー ロック (CapsLock/NumLock/ScrollLock) の変更を報告します。</span><span class="sxs-lookup"><span data-stu-id="be6da-195">If defined, causes ux_host_class_hid_keyboard_key_get to report lock key (CapsLock/NumLock/ScrollLock) changes.</span></span>
- <span data-ttu-id="be6da-196">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** が定義されている場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="be6da-196">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="be6da-197">定義されている場合、ux_host_class_hid_keyboard_key_get は、修飾キー (Ctrl/Alt/Shift/GUI) の変更を報告します。</span><span class="sxs-lookup"><span data-stu-id="be6da-197">If defined, causes ux_host_class_hid_keyboard_key_get to report modifier key (Ctrl/Alt/Shift/GUI) changes.</span></span>
- <span data-ttu-id="be6da-198">**UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: 定義されている場合、この値は CDC-ECM ホスト クラス内のパケット数を表します。</span><span class="sxs-lookup"><span data-stu-id="be6da-198">**UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: If defined, this value represents the number of packets in the CDC-ECM host class.</span></span> <span data-ttu-id="be6da-199">既定値は 16 です。</span><span class="sxs-lookup"><span data-stu-id="be6da-199">The default is 16.</span></span>

## <a name="source-code-tree"></a><span data-ttu-id="be6da-200">ソース コード ツリー</span><span class="sxs-lookup"><span data-stu-id="be6da-200">Source Code Tree</span></span>

<span data-ttu-id="be6da-201">USBX ファイルは、複数のディレクトリ内に用意されています。</span><span class="sxs-lookup"><span data-stu-id="be6da-201">The USBX files are provided in several directories.</span></span>

![ソース コード ツリー](media/usbx-host-stack/source-code-tree.png)

<span data-ttu-id="be6da-203">ファイル名によってファイルを認識できるようにするために、次の規則が採用されています。</span><span class="sxs-lookup"><span data-stu-id="be6da-203">In order to make the files recognizable by their names, the following convention has been adopted:</span></span>

| <span data-ttu-id="be6da-204">ファイルのサフィックス名</span><span class="sxs-lookup"><span data-stu-id="be6da-204">File Suffix Name</span></span> | <span data-ttu-id="be6da-205">ファイルの説明</span><span class="sxs-lookup"><span data-stu-id="be6da-205">File description</span></span>                          |
| ---------------- | ----------------------------------------- |
| <span data-ttu-id="be6da-206">ux_host_stack</span><span class="sxs-lookup"><span data-stu-id="be6da-206">ux_host_stack</span></span>    | <span data-ttu-id="be6da-207">USBX ホスト スタック コア ファイル</span><span class="sxs-lookup"><span data-stu-id="be6da-207">usbx host stack core files</span></span>                |
| <span data-ttu-id="be6da-208">ux_host_class</span><span class="sxs-lookup"><span data-stu-id="be6da-208">ux_host_class</span></span>    | <span data-ttu-id="be6da-209">USBX ホスト スタック クラス ファイル</span><span class="sxs-lookup"><span data-stu-id="be6da-209">usbx host stack classes files</span></span>             |
| <span data-ttu-id="be6da-210">ux_hcd</span><span class="sxs-lookup"><span data-stu-id="be6da-210">ux_hcd</span></span>           | <span data-ttu-id="be6da-211">USBX ホスト スタック コントローラー ドライバー ファイル</span><span class="sxs-lookup"><span data-stu-id="be6da-211">usbx host stack controller driver files</span></span>   |
| <span data-ttu-id="be6da-212">ux_device_stack</span><span class="sxs-lookup"><span data-stu-id="be6da-212">ux_device_stack</span></span>  | <span data-ttu-id="be6da-213">USBX デバイス スタック コア ファイル</span><span class="sxs-lookup"><span data-stu-id="be6da-213">usbx device stack core files</span></span>              |
| <span data-ttu-id="be6da-214">ux_device_class</span><span class="sxs-lookup"><span data-stu-id="be6da-214">ux_device_class</span></span>  | <span data-ttu-id="be6da-215">USBX デバイス スタック クラス ファイル</span><span class="sxs-lookup"><span data-stu-id="be6da-215">usbx device stack classes files</span></span>           |
| <span data-ttu-id="be6da-216">ux_dcd</span><span class="sxs-lookup"><span data-stu-id="be6da-216">ux_dcd</span></span>           | <span data-ttu-id="be6da-217">USBX デバイス スタック コントローラー ドライバー ファイル</span><span class="sxs-lookup"><span data-stu-id="be6da-217">usbx device stack controller driver files</span></span> |
| <span data-ttu-id="be6da-218">ux_otg</span><span class="sxs-lookup"><span data-stu-id="be6da-218">ux_otg</span></span>           | <span data-ttu-id="be6da-219">USBX OTG コントローラー ドライバー関連ファイル</span><span class="sxs-lookup"><span data-stu-id="be6da-219">usbx otg controller driver related files</span></span>  |
| <span data-ttu-id="be6da-220">ux_pictbridge</span><span class="sxs-lookup"><span data-stu-id="be6da-220">ux_pictbridge</span></span>    | <span data-ttu-id="be6da-221">USBX Pictbridge ファイル</span><span class="sxs-lookup"><span data-stu-id="be6da-221">usbx pictbridge files</span></span>                     |
| <span data-ttu-id="be6da-222">ux_utility</span><span class="sxs-lookup"><span data-stu-id="be6da-222">ux_utility</span></span>       | <span data-ttu-id="be6da-223">USBXユーティリティ関数</span><span class="sxs-lookup"><span data-stu-id="be6da-223">usbx utility functions</span></span>                    |
| <span data-ttu-id="be6da-224">demo_usbx</span><span class="sxs-lookup"><span data-stu-id="be6da-224">demo_usbx</span></span>        | <span data-ttu-id="be6da-225">USBX のデモンストレーション ファイル</span><span class="sxs-lookup"><span data-stu-id="be6da-225">demonstration files for USBX</span></span>              |

## <a name="initialization-of-usbx-resources"></a><span data-ttu-id="be6da-226">USBX リソースの初期化</span><span class="sxs-lookup"><span data-stu-id="be6da-226">Initialization of USBX resources</span></span>

<span data-ttu-id="be6da-227">USBX には、独自のメモリ マネージャーがあります。</span><span class="sxs-lookup"><span data-stu-id="be6da-227">USBX has its own memory manager.</span></span> <span data-ttu-id="be6da-228">メモリは、USBX のホスト側またはデバイス側が初期化される前に、USBX に割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="be6da-228">The memory needs to be allocated to USBX before the host or device side of USBX is initialized.</span></span> <span data-ttu-id="be6da-229">USBX メモリ マネージャーは、メモリをキャッシュできるシステムに対応できます。</span><span class="sxs-lookup"><span data-stu-id="be6da-229">USBX memory manager can accommodate systems where memory can be cached.</span></span>

<span data-ttu-id="be6da-230">次の関数は、USBX メモリ リソースを通常の 128K メモリで初期化します。キャッシュ セーフ メモリ用の個別のプールはありません。</span><span class="sxs-lookup"><span data-stu-id="be6da-230">The following function initializes USBX memory resources with 128K of regular memory and no separate pool for cache safe memory:</span></span>

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

<span data-ttu-id="be6da-231">ux_system_initialize のプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="be6da-231">The prototype for the ux_system_initialize is as follows.</span></span>

```c
UINT ux_system_initialize( 
    VOID *regular_memory_pool_start,
    ULONG regular_memory_size,
    VOID *cache_safe_memory_pool_start,
    ULONG cache_safe_memory_size);
```

### <a name="input-parameters"></a><span data-ttu-id="be6da-232">入力パラメーター:</span><span class="sxs-lookup"><span data-stu-id="be6da-232">Input parameters:</span></span>

- <span data-ttu-id="be6da-233">**regular_memory_pool_start** 通常のメモリ プールの開始。</span><span class="sxs-lookup"><span data-stu-id="be6da-233">**regular_memory_pool_start** Beginning of the regular memory pool.</span></span>
- <span data-ttu-id="be6da-234">**regular_memory_size** 通常のメモリ プールのサイズ。</span><span class="sxs-lookup"><span data-stu-id="be6da-234">**regular_memory_size** Size of the regular memory pool.</span></span>
- <span data-ttu-id="be6da-235">**cache_safe_memory_pool_start** キャッシュ セーフ メモリ プールの開始。</span><span class="sxs-lookup"><span data-stu-id="be6da-235">**cache_safe_memory_pool_start** Beginning of the cache safe memory pool.</span></span>
- <span data-ttu-id="be6da-236">**cache_safe_memory_size** キャッシュ セーフ メモリ プールのサイズ。</span><span class="sxs-lookup"><span data-stu-id="be6da-236">**cache_safe_memory_size** Size of the cache safe memory pool.</span></span>    |

<span data-ttu-id="be6da-237">キャッシュ セーフ メモリの定義を必要としないシステムもあります。</span><span class="sxs-lookup"><span data-stu-id="be6da-237">Not all systems require the definition of cache safe memory.</span></span> <span data-ttu-id="be6da-238">このようなシステムでは、メモリ ポインターの初期化中に渡された値は UX_NULL に、プールのサイズは 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="be6da-238">In such a system, the values passed during the initialization for the memory pointer will be set to UX_NULL and the size of the pool to 0.</span></span> <span data-ttu-id="be6da-239">その後、USBX はキャッシュ セーフ プールの代わりに通常のメモリ プールを使用します。</span><span class="sxs-lookup"><span data-stu-id="be6da-239">USBX will then use the regular memory pool in lieu of the cache safe pool.</span></span>

<span data-ttu-id="be6da-240">通常のメモリがキャッシュ セーフではなく、コントローラーが DMA メモリ (OHCI、EHCI コントローラーなど) を実行する必要があるシステムでは、キャッシュ セーフ ゾーン内でメモリ プールを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="be6da-240">In a system where the regular memory is not cache safe and a controller requires to perform DMA memory (like OHCI, EHCI controllers amongst others) it is necessary to define a memory pool in a cache safe zone.</span></span>

## <a name="uninitialization-of-usbx-resources"></a><span data-ttu-id="be6da-241">USBX リソースを初期化前の状態に戻す</span><span class="sxs-lookup"><span data-stu-id="be6da-241">Uninitialization of USBX resources</span></span>

<span data-ttu-id="be6da-242">USBX を終了するには、そのリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="be6da-242">USBX can be terminated by releasing its resources.</span></span> <span data-ttu-id="be6da-243">USBX を終了する前に、すべてのクラスとコントローラー リソースを適切に終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="be6da-243">Prior to terminating usbx, all classes and controller resources need to be terminated properly.</span></span> <span data-ttu-id="be6da-244">次の関数は、USBX メモリ リソースを初期化前の状態に戻します。</span><span class="sxs-lookup"><span data-stu-id="be6da-244">The following function uninitializes USBX memory resources :</span></span>

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

<span data-ttu-id="be6da-245">ux_system_initialize のプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="be6da-245">The prototype for the ux_system_initialize is as follows.</span></span>

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-host-controllers"></a><span data-ttu-id="be6da-246">USB ホスト コントローラーの定義</span><span class="sxs-lookup"><span data-stu-id="be6da-246">Definition of USB Host Controllers</span></span>

<span data-ttu-id="be6da-247">USBX をホスト モードで動作させるには、USB ホスト コントローラーを少なくとも 1 つ定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="be6da-247">It is required to define at least one USB host controller for USBX to operate in host mode.</span></span> <span data-ttu-id="be6da-248">アプリケーション初期化ファイルには、この定義が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="be6da-248">The application initialization file should contain this definition.</span></span> <span data-ttu-id="be6da-249">次の行は、汎用ホスト コントローラーの定義を実行します。</span><span class="sxs-lookup"><span data-stu-id="be6da-249">The following line performs the definition of a generic host controller.</span></span>

```c
ux_host_stack_hcd_register("ux_hcd_controller",
        ux_hcd_controller_initialize, 0xd0000, 0x0a);
```

<span data-ttu-id="be6da-250">ux_host_stack_hcd_register には、次のプロトタイプが含まれます。</span><span class="sxs-lookup"><span data-stu-id="be6da-250">The ux_host_stack_hcd_register has the following prototype.</span></span>

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_initialize_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

<span data-ttu-id="be6da-251">ux_host_stack_hcd_register 関数には、次のパラメーターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="be6da-251">The ux_host_stack_hcd_register function has the following parameters.</span></span>

- <span data-ttu-id="be6da-252">**hcd_name**: コントローラー名の文字列</span><span class="sxs-lookup"><span data-stu-id="be6da-252">**hcd_name**: string of the controller name</span></span>
- <span data-ttu-id="be6da-253">**hcd_initialize_function**: コントローラーの初期化関数</span><span class="sxs-lookup"><span data-stu-id="be6da-253">**hcd_initialize_function**: initialization function of the controller</span></span>
- <span data-ttu-id="be6da-254">**hcd_param1**: 通常、コントローラーによって使用される IO 値またはメモリ</span><span class="sxs-lookup"><span data-stu-id="be6da-254">**hcd_param1**: usually the IO value or Memory used by the controller</span></span>
- <span data-ttu-id="be6da-255">**hcd_param2**: 通常、コントローラーによって使用される IRQ</span><span class="sxs-lookup"><span data-stu-id="be6da-255">**hcd_param2**: usually the IRQ used by the controller</span></span>

<span data-ttu-id="be6da-256">前の例の項目はそれぞれ以下を表します。</span><span class="sxs-lookup"><span data-stu-id="be6da-256">In our previous example:</span></span>

- <span data-ttu-id="be6da-257">"ux_hcd_controller" はコントローラーの名前です</span><span class="sxs-lookup"><span data-stu-id="be6da-257">"ux_hcd_controller" is the name of the controller</span></span>
- <span data-ttu-id="be6da-258">"ux_hcd_controller_initialize" は、ホスト コントローラーの初期化ルーチンです</span><span class="sxs-lookup"><span data-stu-id="be6da-258">"ux_hcd_controller_initialize" is the initialization routine for the host controller</span></span>
- <span data-ttu-id="be6da-259">0xd0000 は、メモリ内でホスト コントローラー レジスタを表示できるアドレスです</span><span class="sxs-lookup"><span data-stu-id="be6da-259">0xd0000 is the address at which the host controller registers are visible in memory</span></span>
- <span data-ttu-id="be6da-260">0x0a は、ホスト コントローラーによって使用される IRQ です。</span><span class="sxs-lookup"><span data-stu-id="be6da-260">and 0x0a is the IRQ used by the host controller.</span></span>

<span data-ttu-id="be6da-261">1 つのホスト コントローラーと複数のクラスを持つ、ホスト モードでの USBX の初期化の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be6da-261">Following is an example of the initialization of USBX in host mode with one host controller and several classes.</span></span>

```c
UINT status;

/* Initialize USBX. */
ux_system_initialize(memory_ptr, (128*1024),0,0);

/* The code below is required for installing the USBX host stack. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, host stack has been initialized. */

/* Register all the host classes for this USBX implementation. */
status = ux_host_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_storage", ux_host_class_storage_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_printer", ux_host_class_printer_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_audio", ux_host_class_audio_entry);

/* If status equals UX_SUCCESS, host class has been registered. */

/* Register all the USB host controllers available in this system. */ 
status = ux_host_stack_hcd_register("ux_hcd_controller", ux_hcd_controller_initialize, 0x300000, 0x0a);

/* If status equals UX_SUCCESS, USB host controllers have been registered. */
```

## <a name="definition-of-host-classes"></a><span data-ttu-id="be6da-262">Host クラスの定義</span><span class="sxs-lookup"><span data-stu-id="be6da-262">Definition of Host Classes</span></span>

<span data-ttu-id="be6da-263">USBX を使用して 1 つ以上のホスト クラスを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="be6da-263">It is required to define one or more host classes with USBX.</span></span> <span data-ttu-id="be6da-264">USB スタックが USB デバイスを構成した後、その USB デバイスを動作させるには USB クラスが必要です。</span><span class="sxs-lookup"><span data-stu-id="be6da-264">A USB class is required to drive a USB device after the USB stack has configured the USB device.</span></span> <span data-ttu-id="be6da-265">USB クラスは、デバイスに固有です。</span><span class="sxs-lookup"><span data-stu-id="be6da-265">A USB class is specific to the device.</span></span> <span data-ttu-id="be6da-266">USB デバイス記述子に含まれるインターフェイスの数によっては、USB デバイスを動作させるために 1 つ以上のクラスが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="be6da-266">One or more classes may be required to drive a USB device depending on the number of interfaces contained in the USB device descriptors.</span></span>

<span data-ttu-id="be6da-267">HUB クラスの登録の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be6da-267">This is an example of the registration of the HUB class.</span></span>

```c
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);
```

<span data-ttu-id="be6da-268">関数 ux_host_class_register には、次のプロトタイプが含まれます。</span><span class="sxs-lookup"><span data-stu-id="be6da-268">The function ux_host_class_register has the following prototype.</span></span>

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name, 
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

- <span data-ttu-id="be6da-269">**class_name** はクラスの名前です</span><span class="sxs-lookup"><span data-stu-id="be6da-269">**class_name** is the name of the class</span></span>
- <span data-ttu-id="be6da-270">**class_entry_address** はクラスのエントリ ポイントです</span><span class="sxs-lookup"><span data-stu-id="be6da-270">**class_entry_address** is the entry point of the class</span></span>

<span data-ttu-id="be6da-271">HUB クラスの初期化の例の項目はそれぞれ以下を表します。</span><span class="sxs-lookup"><span data-stu-id="be6da-271">In the example of the HUB class initialization:</span></span>

- <span data-ttu-id="be6da-272">"ux_host_class_hub" は HUB クラスの名前です</span><span class="sxs-lookup"><span data-stu-id="be6da-272">"ux_host_class_hub" is the name of the hub class</span></span>
- <span data-ttu-id="be6da-273">ux_host_class_hub_entry は HUB クラスのエントリ ポイントです。</span><span class="sxs-lookup"><span data-stu-id="be6da-273">ux_host_class_hub_entry is the entry point of the HUB class.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="be6da-274">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="be6da-274">Troubleshooting</span></span>

<span data-ttu-id="be6da-275">USBX には、デモンストレーション ファイルとシミュレーション環境が付属しています。</span><span class="sxs-lookup"><span data-stu-id="be6da-275">USBX is delivered with a demonstration file and a simulation environment.</span></span> <span data-ttu-id="be6da-276">まずは、ターゲット ハードウェアまたは特定のデモンストレーション プラットフォームのいずれかで、デモンストレーション プラットフォームを稼働させることを常にお勧めします。</span><span class="sxs-lookup"><span data-stu-id="be6da-276">It is always a good idea to get the demonstration platform running first—either on the target hardware or a specific demonstration platform.</span></span>

<span data-ttu-id="be6da-277">デモンストレーション システムが動作しない場合は、次のことを試して問題を絞り込んでください。</span><span class="sxs-lookup"><span data-stu-id="be6da-277">If the demonstration system does not work, try the following things to narrow the problem.</span></span>

## <a name="usbx-version-id"></a><span data-ttu-id="be6da-278">USBX のバージョン ID</span><span class="sxs-lookup"><span data-stu-id="be6da-278">USBX Version ID</span></span>

<span data-ttu-id="be6da-279">現在使用している USBX のバージョンは、実行時にユーザーとアプリケーション ソフトウェアのどちらからでも確認できます。</span><span class="sxs-lookup"><span data-stu-id="be6da-279">The current version of USBX is available both to the user and the application software during run-time.</span></span> <span data-ttu-id="be6da-280">プログラマーは \***ux_port.h** _ ファイルを調べることで USBX のバージョンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="be6da-280">The programmer can obtain the USBX version from examination of the \***ux_port.h** _ file.</span></span> <span data-ttu-id="be6da-281">加えて、このファイルには、対応するポートのバージョン履歴も含まれています。</span><span class="sxs-lookup"><span data-stu-id="be6da-281">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="be6da-282">アプリケーション ソフトウェアは、_*_ux_port.h_*\* 内で定義されているグローバル文字列 _ \*_ _ux_version_id_\* _ を調べることで USBX バージョンを取得できます。</span><span class="sxs-lookup"><span data-stu-id="be6da-282">Application software can obtain the USBX version by examining the global string _ *_ _ux_version_id_* _, which is defined in _\*_ux_port.h_\*\*.</span></span>
