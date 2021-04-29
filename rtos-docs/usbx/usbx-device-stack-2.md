---
title: 第 2 章 - Azure RTOS USBX デバイス スタックのインストール
description: USBX のインストール方法について説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 097fdd3c6f09c666ec3ad6eda9e5ba3fa159cb4d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813265"
---
# <a name="chapter-2---azure-rtos-usbx-device-stack-installation"></a><span data-ttu-id="539a1-103">第 2 章 - Azure RTOS USBX デバイス スタックのインストール</span><span class="sxs-lookup"><span data-stu-id="539a1-103">Chapter 2 - Azure RTOS USBX Device Stack Installation</span></span>

## <a name="host-considerations"></a><span data-ttu-id="539a1-104">ホストに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="539a1-104">Host Considerations</span></span>

### <a name="computer-type"></a><span data-ttu-id="539a1-105">コンピューターの種類</span><span class="sxs-lookup"><span data-stu-id="539a1-105">Computer Type</span></span>

<span data-ttu-id="539a1-106">埋め込み開発は、通常、Windows PC または Unix ホスト コンピューター上で行われます。</span><span class="sxs-lookup"><span data-stu-id="539a1-106">Embedded development is usually performed on Windows PC or Unix host computers.</span></span> <span data-ttu-id="539a1-107">アプリケーションは、ホスト上でコンパイル、リンク、および配置された後、実行のためにターゲット ハードウェアにダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="539a1-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

### <a name="download-interfaces"></a><span data-ttu-id="539a1-108">ダウンロードのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="539a1-108">Download Interfaces</span></span>

<span data-ttu-id="539a1-109">通常、ターゲットのダウンロードは RS-232 のシリアル インターフェイスで行われますが、パラレル インターフェイス、USB、およびイーサネットも普及してきています。</span><span class="sxs-lookup"><span data-stu-id="539a1-109">Usually the target download is done over an RS-232 serial interface, although parallel interfaces, USB, and Ethernet are becoming more popular.</span></span> <span data-ttu-id="539a1-110">使用可能なオプションについては、開発ツールのドキュメントをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="539a1-110">See the development tool documentation for available options.</span></span>

### <a name="debugging-tools"></a><span data-ttu-id="539a1-111">デバッグ ツール</span><span class="sxs-lookup"><span data-stu-id="539a1-111">Debugging Tools</span></span>

<span data-ttu-id="539a1-112">デバッグは、通常、プログラム イメージのダウンロードと同じリンクを使って行われます。</span><span class="sxs-lookup"><span data-stu-id="539a1-112">Debugging is done typically over the same link as the program image download.</span></span> <span data-ttu-id="539a1-113">デバッガーには、ターゲット上で動作する小さなモニター プログラムから、バックグラウンド デバッグ モニター (BDM) ツールやインサーキット エミュレーター (ICE) ツールまで、さまざまなものがあります。</span><span class="sxs-lookup"><span data-stu-id="539a1-113">A variety of debuggers exist, ranging from small monitor programs running on the target through Background Debug Monitor (BDM) and In-Circuit Emulator (ICE) tools.</span></span> <span data-ttu-id="539a1-114">ICE ツールには、実際のターゲット ハードウェアの最も堅牢なデバッグ機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="539a1-114">The ICE tool provides the most robust debugging of actual target hardware.</span></span>

### <a name="required-hard-disk-space"></a><span data-ttu-id="539a1-115">必要なハード ディスク容量</span><span class="sxs-lookup"><span data-stu-id="539a1-115">Required Hard Disk Space</span></span>

<span data-ttu-id="539a1-116">USBX のソース コードは ASCII 形式で提供され、ホスト コンピューターのハード ディスク上に約 500 KB の空き領域が必要です。</span><span class="sxs-lookup"><span data-stu-id="539a1-116">The source code for USBX is delivered in ASCII format and requires approximately 500 KBytes of space on the host computer's hard disk.</span></span>

### <a name="target-considerations"></a><span data-ttu-id="539a1-117">ターゲットに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="539a1-117">Target Considerations</span></span>

<span data-ttu-id="539a1-118">USBX は、ホスト モードでターゲット上に 24 KB から 64 KB の読み取り専用メモリ (ROM) を必要とします。</span><span class="sxs-lookup"><span data-stu-id="539a1-118">USBX requires between 24 KBytes and 64 KBytes of Read Only Memory (ROM) on the target in host mode.</span></span> <span data-ttu-id="539a1-119">必要なメモリ容量は、使用するコントローラーの種類と、USBX にリンクされている USB クラスによって異なります。</span><span class="sxs-lookup"><span data-stu-id="539a1-119">The amount of memory required is dependent on the type of controller used and the USB classes linked to USBX.</span></span> <span data-ttu-id="539a1-120">また、USBX グローバル データ構造およびメモリ プール用に、ターゲットのランダム アクセス メモリ (RAM) がさらに 32 KB 必要です。</span><span class="sxs-lookup"><span data-stu-id="539a1-120">Another 32 KBytes of the target's Random Access Memory (RAM) are required for USBX global data structures and memory pool.</span></span> <span data-ttu-id="539a1-121">このメモリ プールは、USB 上の予期されたデバイス数と USB コントローラーの種類に応じて調整することもできます。</span><span class="sxs-lookup"><span data-stu-id="539a1-121">This memory pool can also be adjusted depending on the expected number of devices on the USB and the type of USB controller.</span></span> <span data-ttu-id="539a1-122">USBX デバイス側には、デバイス コントローラーの種類に応じて、約 10K から 12K の ROM が必要です。</span><span class="sxs-lookup"><span data-stu-id="539a1-122">The USBX device side requires roughly 10-12 K of ROM depending on the type of device controller.</span></span> <span data-ttu-id="539a1-123">RAM メモリの使用量は、デバイスによってエミュレートされるクラスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="539a1-123">The RAM memory usage depends on the type of class emulated by the device.</span></span>

<span data-ttu-id="539a1-124">また、USBX は、複数スレッド保護のために、ThreadX セマフォ、ミューテックス、およびスレッドを利用しているほか、USB バス トポロジを監視するために I/O 中断および定期的な処理を行っています。</span><span class="sxs-lookup"><span data-stu-id="539a1-124">USBX also relies on ThreadX semaphores, mutexes, and threads for multiple thread protection, and I/O suspension and periodic processing for monitoring the USB bus topology.</span></span>

### <a name="product-distribution"></a><span data-ttu-id="539a1-125">製品の配布</span><span class="sxs-lookup"><span data-stu-id="539a1-125">Product Distribution</span></span>

<span data-ttu-id="539a1-126">Azure RTOS USBX は、<https://github.com/azure-rtos/usbx/> のパブリック ソース コード リポジトリから入手できます。</span><span class="sxs-lookup"><span data-stu-id="539a1-126">Azure RTOS USBX can be obtained from our public source code repository at <https://github.com/azure-rtos/usbx/>.</span></span>

<span data-ttu-id="539a1-127">以下は、リポジトリ内のいくつかの重要なファイルの一覧です。</span><span class="sxs-lookup"><span data-stu-id="539a1-127">The following is a list of several important files in the repository.</span></span>

* <span data-ttu-id="539a1-128">***ux_api.h***: この C ヘッダー ファイルには、すべてのシステム等価物、データ構造、およびサービス プロトタイプが含まれています。</span><span class="sxs-lookup"><span data-stu-id="539a1-128">***ux_api.h***: This C header file contains all system equates, data structures, and service prototypes.</span></span>
* <span data-ttu-id="539a1-129">***ux_port.h***: この C ヘッダー ファイルには、開発ツール固有のすべてのデータ定義とデータ構造が含まれています。</span><span class="sxs-lookup"><span data-stu-id="539a1-129">***ux_port.h***: This C header file contains all development-tool-specific data definitions and structures.</span></span>
* <span data-ttu-id="539a1-130">***ux.lib***: これは、USBX C ライブラリのバイナリ バージョンです。</span><span class="sxs-lookup"><span data-stu-id="539a1-130">***ux.lib***:  This is the binary version of the USBX C library.</span></span> <span data-ttu-id="539a1-131">これは標準パッケージと共に配布されます。</span><span class="sxs-lookup"><span data-stu-id="539a1-131">It is distributed with the standard package.</span></span>
* <span data-ttu-id="539a1-132">***demo_usbx c***: シンプルな USBX デモが含まれる C ファイル</span><span class="sxs-lookup"><span data-stu-id="539a1-132">***demo_usbx.c***: The C file containing a simple USBX demo</span></span>

<span data-ttu-id="539a1-133">すべてのファイル名が小文字で表記されます。</span><span class="sxs-lookup"><span data-stu-id="539a1-133">All filenames are in lower-case.</span></span> <span data-ttu-id="539a1-134">この名前付け規則によって、コマンドを Unix 開発プラットフォームにより簡単に変換できます。</span><span class="sxs-lookup"><span data-stu-id="539a1-134">This naming convention makes it easier to convert the commands to Unix development platforms.</span></span>

## <a name="usbx-installation"></a><span data-ttu-id="539a1-135">USBX のインストール</span><span class="sxs-lookup"><span data-stu-id="539a1-135">USBX Installation</span></span>

<span data-ttu-id="539a1-136">USBX は、GitHub リポジトリをローカル コンピューターに複製することによってインストールされます。</span><span class="sxs-lookup"><span data-stu-id="539a1-136">USBX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="539a1-137">お使いの PC 上に USBX リポジトリの複製を作成するための一般的な構文を次に示します。</span><span class="sxs-lookup"><span data-stu-id="539a1-137">The following is typical syntax for creating a clone of the USBX repository on your PC:</span></span>

```c
    git clone https://github.com/azure-rtos/usbx
```

<span data-ttu-id="539a1-138">GitHub メイン ページ上のダウンロード ボタンを使用して、リポジトリのコピーをダウンロードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="539a1-138">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="539a1-139">また、オンライン リポジトリのフロント ページ上で USBX ライブラリを構築する手順も紹介します。</span><span class="sxs-lookup"><span data-stu-id="539a1-139">You will also find instructions for building the USBX library on the front page of the online repository.</span></span>

<span data-ttu-id="539a1-140">次の一般的な手順は、事実上すべてのインストールに適用されます。</span><span class="sxs-lookup"><span data-stu-id="539a1-140">The following general instructions apply to virtually any installation:</span></span>

1. <span data-ttu-id="539a1-141">ホストのハード ドライブ上で以前 ThreadX をインストールした先と同じディレクトリを使用します。</span><span class="sxs-lookup"><span data-stu-id="539a1-141">Use the same directory in which you previously installed ThreadX on the host hard drive.</span></span> <span data-ttu-id="539a1-142">すべての USBX 名が一意で、以前の USBX インストールと競合することはありません。</span><span class="sxs-lookup"><span data-stu-id="539a1-142">All USBX names are unique and will not interfere with the previous USBX installation.</span></span>
1. <span data-ttu-id="539a1-143">_*_tx_application_define_*\* の先頭または先頭付近に \***ux_system_initialize** _ への呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="539a1-143">Add a call to ***ux_system_initialize** _ at or near the beginning of _*_tx_application_define_\*\*.</span></span> <span data-ttu-id="539a1-144">これは USBX リソースが初期化される場所です。</span><span class="sxs-lookup"><span data-stu-id="539a1-144">This is where the USBX resources are initialized.</span></span>
1. <span data-ttu-id="539a1-145">***ux_device_stack_initialize*** への呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="539a1-145">Add a call to \***ux_device_stack_initialize\*.**</span></span>
1. <span data-ttu-id="539a1-146">必要な USBX クラス (ホストまたはデバイス クラス) を初期化するための呼び出しを 1 つ以上追加します</span><span class="sxs-lookup"><span data-stu-id="539a1-146">Add one or more calls to initialize the required USBX classes (either host and/or devices classes)</span></span>
1. <span data-ttu-id="539a1-147">システム内で使用可能なデバイス コントローラーを初期化するための呼び出しを 1 つ以上追加します。</span><span class="sxs-lookup"><span data-stu-id="539a1-147">Add one or more calls to initialize the device controller available in the system.</span></span>
1. <span data-ttu-id="539a1-148">低レベルのハードウェア初期化および割り込みベクター ルーティングを追加するために、tx_low_level_initialize.c ファイルの変更が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="539a1-148">It may be required to modify the tx_low_level_initialize.c file to add low-level hardware initialization and interrupt vector routing.</span></span> <span data-ttu-id="539a1-149">これはハードウェア プラットフォームに固有であるため、ここでは説明しません。</span><span class="sxs-lookup"><span data-stu-id="539a1-149">This is specific to the hardware platform and will not be discussed here.|</span></span>
1. <span data-ttu-id="539a1-150">アプリケーション ソース コードをコンパイルし、USBX および ThreadX ランタイム ライブラリ (USB ストレージ クラスや USB ネットワーク クラスをコンパイルする場合は、FileX や Netx も必要になる場合があります)、ux. a (または ux.lib)、および tx.a (または tx.lib) とリンクします。</span><span class="sxs-lookup"><span data-stu-id="539a1-150">Compile application source code and link with the USBX and ThreadX run time libraries (FileX and/or Netx may also be required if the USB storage class and/or USB network classes are to be compiled in), ux.a (or ux.lib) and tx.a (or tx.lib).</span></span> <span data-ttu-id="539a1-151">結果はターゲットにダウンロードして、実行できます。</span><span class="sxs-lookup"><span data-stu-id="539a1-151">The resulting can be downloaded to the target and executed!</span></span>

## <a name="configuration-options"></a><span data-ttu-id="539a1-152">構成オプション</span><span class="sxs-lookup"><span data-stu-id="539a1-152">Configuration Options</span></span>

<span data-ttu-id="539a1-153">USBX ライブラリを構築するための構成オプションはいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="539a1-153">There are several configuration options for building the USBX library.</span></span> <span data-ttu-id="539a1-154">オプションはすべて ***ux_user.h*** にあります。</span><span class="sxs-lookup"><span data-stu-id="539a1-154">All options are located in the ***ux_user.h***.</span></span>

<span data-ttu-id="539a1-155">各構成オプションの詳細を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="539a1-155">The list below details each configuration option.</span></span>

| <span data-ttu-id="539a1-156">構成&nbsp;オプション</span><span class="sxs-lookup"><span data-stu-id="539a1-156">Configuration&nbsp;Option</span></span> | <span data-ttu-id="539a1-157">説明</span><span class="sxs-lookup"><span data-stu-id="539a1-157">Description</span></span> |
| --- | --- |
| <span data-ttu-id="539a1-158">**UX_PERIODIC_RATE**</span><span class="sxs-lookup"><span data-stu-id="539a1-158">**UX_PERIODIC_RATE**</span></span> | <span data-ttu-id="539a1-159">この値は、特定のハードウェア プラットフォームの 1 秒あたりのティック数を表します。</span><span class="sxs-lookup"><span data-stu-id="539a1-159">This value represents how many ticks per seconds for a specific hardware platform.</span></span> <span data-ttu-id="539a1-160">既定値は 1000 で、ミリ秒あたり 1 ティックを示します。</span><span class="sxs-lookup"><span data-stu-id="539a1-160">The default is 1000 indicating 1 tick per millisecond.</span></span> |
| <span data-ttu-id="539a1-161">**UX_THREAD_STACK_SIZE**</span><span class="sxs-lookup"><span data-stu-id="539a1-161">**UX_THREAD_STACK_SIZE**</span></span> | <span data-ttu-id="539a1-162">この値は、USBX スレッド用のスタックのサイズ (バイト単位) です。</span><span class="sxs-lookup"><span data-stu-id="539a1-162">This value is the size of the stack in bytes for the USBX threads.</span></span> <span data-ttu-id="539a1-163">これは、通常、使用されるプロセッサとホスト コントローラーに応じて、1024 バイトまたは 2048 バイトになります。</span><span class="sxs-lookup"><span data-stu-id="539a1-163">It can be typically 1024 bytes or 2048 bytes depending on the processor used and the host controller.</span></span> |
| <span data-ttu-id="539a1-164">**UX_THREAD_PRIORITY_ENUM**</span><span class="sxs-lookup"><span data-stu-id="539a1-164">**UX_THREAD_PRIORITY_ENUM**</span></span> | <span data-ttu-id="539a1-165">これは、バス トポロジを監視する USBX 列挙スレッドの ThreadX 優先度の値です。</span><span class="sxs-lookup"><span data-stu-id="539a1-165">This is the ThreadX priority value for the USBX enumeration threads that monitors the bus topology.</span></span> |
| <span data-ttu-id="539a1-166">**UX_THREAD_PRIORITY_CLASS**</span><span class="sxs-lookup"><span data-stu-id="539a1-166">**UX_THREAD_PRIORITY_CLASS**</span></span> | <span data-ttu-id="539a1-167">これは、標準 USBX スレッドの ThreadX 優先度の値です。</span><span class="sxs-lookup"><span data-stu-id="539a1-167">This is the ThreadX priority value for the standard USBX threads.</span></span> |
| <span data-ttu-id="539a1-168">**UX_THREAD_PRIORITY_KEYBOARD**</span><span class="sxs-lookup"><span data-stu-id="539a1-168">**UX_THREAD_PRIORITY_KEYBOARD**</span></span> | <span data-ttu-id="539a1-169">これは、USBX HID キーボード クラスの ThreadX 優先度の値です。</span><span class="sxs-lookup"><span data-stu-id="539a1-169">This is the ThreadX priority value for the USBX HID keyboard class.</span></span> |
| <span data-ttu-id="539a1-170">**UX_THREAD_PRIORITY_DCD**</span><span class="sxs-lookup"><span data-stu-id="539a1-170">**UX_THREAD_PRIORITY_DCD**</span></span> | <span data-ttu-id="539a1-171">これは、デバイス コントローラー スレッドの ThreadX 優先度の値です。</span><span class="sxs-lookup"><span data-stu-id="539a1-171">This is the ThreadX priority value for the device controller thread.</span></span> |
| <span data-ttu-id="539a1-172">**UX_NO_TIME_SLICE**</span><span class="sxs-lookup"><span data-stu-id="539a1-172">**UX_NO_TIME_SLICE**</span></span> | <span data-ttu-id="539a1-173">この値は、スレッドに使用されるタイム スライスを実際に定義します。</span><span class="sxs-lookup"><span data-stu-id="539a1-173">This value actually defines the time slice that will be used for threads.</span></span> <span data-ttu-id="539a1-174">たとえば、0 に定義されている場合、ThreadX ターゲット ポートはタイム スライスを使用しません。</span><span class="sxs-lookup"><span data-stu-id="539a1-174">For example, if defined to 0, the ThreadX target port does not use time slices.</span></span> |
| <span data-ttu-id="539a1-175">**UX_MAX_SLAVE_CLASS_DRIVER**</span><span class="sxs-lookup"><span data-stu-id="539a1-175">**UX_MAX_SLAVE_CLASS_DRIVER**</span></span> | <span data-ttu-id="539a1-176">これは、ux_device_stack_class_register 経由で登録できる USBX クラスの最大数です。</span><span class="sxs-lookup"><span data-stu-id="539a1-176">This is the maximum number of USBX classes that can be registered via ux_device_stack_class_register.</span></span> |
| <span data-ttu-id="539a1-177">**UX_MAX_SLAVE_LUN**</span><span class="sxs-lookup"><span data-stu-id="539a1-177">**UX_MAX_SLAVE_LUN**</span></span> | <span data-ttu-id="539a1-178">この値は、デバイス ストレージ クラス ドライバー内で表される SCSI 論理ユニットの現在の数を表します。</span><span class="sxs-lookup"><span data-stu-id="539a1-178">This value represents the current number of SCSI logical units represented in the device storage class driver.</span></span> |
| <span data-ttu-id="539a1-179">**UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC**</span><span class="sxs-lookup"><span data-stu-id="539a1-179">**UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC**</span></span> | <span data-ttu-id="539a1-180">定義されている場合、ストレージ クラスではマルチメディア コマンド (MMC)、つまり DVD-ROM が処理されます。</span><span class="sxs-lookup"><span data-stu-id="539a1-180">If defined, the storage class will handle Multi-Media Commands (MMC) that is, DVD-ROM.</span></span> |
| <span data-ttu-id="539a1-181">**UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**</span><span class="sxs-lookup"><span data-stu-id="539a1-181">**UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**</span></span> | <span data-ttu-id="539a1-182">この値は、CDC-ECM クラスのパケット プール内にある NetX パケットの数を表します。</span><span class="sxs-lookup"><span data-stu-id="539a1-182">This value represents the number of NetX packets in the CDC-ECM class' packet pool.</span></span> <span data-ttu-id="539a1-183">既定値は 16 です。</span><span class="sxs-lookup"><span data-stu-id="539a1-183">The default is 16.</span></span> |
| <span data-ttu-id="539a1-184">**UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="539a1-184">**UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH**</span></span> | <span data-ttu-id="539a1-185">この値は、デバイス スタック内のコントロール エンドポイントで受信される最大バイト数を表します。</span><span class="sxs-lookup"><span data-stu-id="539a1-185">This value represents the maximum number of bytes received on a control endpoint in the device stack.</span></span> <span data-ttu-id="539a1-186">既定値は 256 バイトですが、メモリ制約環境では減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="539a1-186">The default is 256 bytes but can be reduced in memory constraint environments.</span></span> |
| <span data-ttu-id="539a1-187">**UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="539a1-187">**UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH**</span></span> | <span data-ttu-id="539a1-188">この値は、HID レポートの最大長 (バイト単位) を表します。</span><span class="sxs-lookup"><span data-stu-id="539a1-188">This value represents the maximum length in bytes of a HID report.</span></span> |
| <span data-ttu-id="539a1-189">**UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE**</span><span class="sxs-lookup"><span data-stu-id="539a1-189">**UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE**</span></span> | <span data-ttu-id="539a1-190">この値は、一度にキューに入れることができる HID レポートの最大数を表します。</span><span class="sxs-lookup"><span data-stu-id="539a1-190">This value represents the maximum number of HID reports that can be queued at once.</span></span> |
| <span data-ttu-id="539a1-191">**UX_SLAVE_REQUEST_DATA_MAX_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="539a1-191">**UX_SLAVE_REQUEST_DATA_MAX_LENGTH**</span></span> | <span data-ttu-id="539a1-192">この値は、デバイス スタック内の一括エンドポイントで受信される最大バイト数を表します。</span><span class="sxs-lookup"><span data-stu-id="539a1-192">This value represents the maximum number of bytes received on a bulk endpoint in the device stack.</span></span> <span data-ttu-id="539a1-193">既定値は 4096 バイトですが、メモリ制約環境では減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="539a1-193">The default is 4096 bytes but can be reduced in memory constraint environments.</span></span> |

## <a name="source-code-tree"></a><span data-ttu-id="539a1-194">ソース コード ツリー</span><span class="sxs-lookup"><span data-stu-id="539a1-194">Source Code Tree</span></span>

<span data-ttu-id="539a1-195">USBX ファイルは、複数のディレクトリ内に用意されています。</span><span class="sxs-lookup"><span data-stu-id="539a1-195">The USBX files are provided in several directories.</span></span>

![ソース コード ツリー](media/usbx-device-stack/source-code-tree.png)

<span data-ttu-id="539a1-197">ファイル名によってファイルを認識できるようにするために、次の規則が採用されています。</span><span class="sxs-lookup"><span data-stu-id="539a1-197">In order to make the files recognizable by their names, the following convention has been adopted:</span></span>

| <span data-ttu-id="539a1-198">ファイルのサフィックス名</span><span class="sxs-lookup"><span data-stu-id="539a1-198">File Suffix Name</span></span>  | <span data-ttu-id="539a1-199">ファイルの説明</span><span class="sxs-lookup"><span data-stu-id="539a1-199">File description</span></span>                          |
| ----------------- | ----------------------------------------- |
| <span data-ttu-id="539a1-200">ux_host_stack</span><span class="sxs-lookup"><span data-stu-id="539a1-200">ux_host_stack</span></span>   | <span data-ttu-id="539a1-201">USBX ホスト スタック コア ファイル</span><span class="sxs-lookup"><span data-stu-id="539a1-201">usbx host stack core files</span></span>                |
| <span data-ttu-id="539a1-202">ux_host_class</span><span class="sxs-lookup"><span data-stu-id="539a1-202">ux_host_class</span></span>   | <span data-ttu-id="539a1-203">USBX ホスト スタック クラス ファイル</span><span class="sxs-lookup"><span data-stu-id="539a1-203">usbx host stack classes files</span></span>             |
| <span data-ttu-id="539a1-204">ux_hcd</span><span class="sxs-lookup"><span data-stu-id="539a1-204">ux_hcd</span></span>           | <span data-ttu-id="539a1-205">USBX ホスト スタック コントローラー ドライバー ファイル</span><span class="sxs-lookup"><span data-stu-id="539a1-205">usbx host stack controller driver files</span></span>   |
| <span data-ttu-id="539a1-206">ux_device_stack</span><span class="sxs-lookup"><span data-stu-id="539a1-206">ux_device_stack</span></span> | <span data-ttu-id="539a1-207">USBX デバイス スタック コア ファイル</span><span class="sxs-lookup"><span data-stu-id="539a1-207">usbx device stack core files</span></span>              |
| <span data-ttu-id="539a1-208">ux_device_class</span><span class="sxs-lookup"><span data-stu-id="539a1-208">ux_device_class</span></span> | <span data-ttu-id="539a1-209">USBX デバイス スタック クラス ファイル</span><span class="sxs-lookup"><span data-stu-id="539a1-209">usbx device stack classes files</span></span>           |
| <span data-ttu-id="539a1-210">ux_dcd</span><span class="sxs-lookup"><span data-stu-id="539a1-210">ux_dcd</span></span>           | <span data-ttu-id="539a1-211">USBX デバイス スタック コントローラー ドライバー ファイル</span><span class="sxs-lookup"><span data-stu-id="539a1-211">usbx device stack controller driver files</span></span> |
| <span data-ttu-id="539a1-212">ux_otg</span><span class="sxs-lookup"><span data-stu-id="539a1-212">ux_otg</span></span>           | <span data-ttu-id="539a1-213">USBX OTG コントローラー ドライバー関連ファイル</span><span class="sxs-lookup"><span data-stu-id="539a1-213">usbx otg controller driver related files</span></span>  |
| <span data-ttu-id="539a1-214">ux_pictbridge</span><span class="sxs-lookup"><span data-stu-id="539a1-214">ux_pictbridge</span></span>    | <span data-ttu-id="539a1-215">USBX Pictbridge ファイル</span><span class="sxs-lookup"><span data-stu-id="539a1-215">usbx pictbridge files</span></span>                     |
| <span data-ttu-id="539a1-216">ux_utility</span><span class="sxs-lookup"><span data-stu-id="539a1-216">ux_utility</span></span>       | <span data-ttu-id="539a1-217">USBX ユーティリティ関数</span><span class="sxs-lookup"><span data-stu-id="539a1-217">usbx utility functions</span></span>                    |
| <span data-ttu-id="539a1-218">demo_usbx</span><span class="sxs-lookup"><span data-stu-id="539a1-218">demo_usbx</span></span>        | <span data-ttu-id="539a1-219">USBX のデモンストレーション ファイル</span><span class="sxs-lookup"><span data-stu-id="539a1-219">demonstration files for USBX</span></span>              |

## <a name="initialization-of-usbx-resources"></a><span data-ttu-id="539a1-220">USBX リソースの初期化</span><span class="sxs-lookup"><span data-stu-id="539a1-220">Initialization of USBX resources</span></span>

<span data-ttu-id="539a1-221">USBX には、独自のメモリ マネージャーがあります。</span><span class="sxs-lookup"><span data-stu-id="539a1-221">USBX has its own memory manager.</span></span> <span data-ttu-id="539a1-222">メモリは、USBX のホスト側またはデバイス側が初期化される前に、USBX に割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="539a1-222">The memory needs to be allocated to USBX before the host or device side of USBX is initialized.</span></span> <span data-ttu-id="539a1-223">USBX メモリ マネージャーは、メモリをキャッシュできるシステムに対応できます。</span><span class="sxs-lookup"><span data-stu-id="539a1-223">USBX memory manager can accommodate systems where memory can be cached.</span></span>

<span data-ttu-id="539a1-224">次の関数は、USBX メモリ リソースを通常の 128 K メモリで初期化します。キャッシュ セーフ メモリ用の個別のプールはありません。</span><span class="sxs-lookup"><span data-stu-id="539a1-224">The following function initializes USBX memory resources with 128 K of regular memory and no separate pool for cache safe memory:</span></span>

```c
/* Initialize USBX Memory */
ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

<span data-ttu-id="539a1-225">ux_system_initialize のプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="539a1-225">The prototype for the ux_system_initialize is as follows:</span></span>

```c
UINT ux_system_initialize(VOID *regular_memory_pool_start,
        ULONG regular_memory_size,
        VOID *cache_safe_memory_pool_start,
        ULONG cache_safe_memory_size);
```

<span data-ttu-id="539a1-226">入力パラメーター:</span><span class="sxs-lookup"><span data-stu-id="539a1-226">Input parameters:</span></span>

| <span data-ttu-id="539a1-227">パラメーター</span><span class="sxs-lookup"><span data-stu-id="539a1-227">Parameter</span></span>                          | <span data-ttu-id="539a1-228">説明</span><span class="sxs-lookup"><span data-stu-id="539a1-228">Description</span></span>                             |
| ---------------------------------- | --------------------------------------- |
| <span data-ttu-id="539a1-229">VOID \*regular_memory_pool_start</span><span class="sxs-lookup"><span data-stu-id="539a1-229">VOID \*regular_memory_pool_start</span></span>    | <span data-ttu-id="539a1-230">通常のメモリ プールの開始</span><span class="sxs-lookup"><span data-stu-id="539a1-230">Beginning of the regular memory pool</span></span>    |
| <span data-ttu-id="539a1-231">ULONG regular_memory_size</span><span class="sxs-lookup"><span data-stu-id="539a1-231">ULONG regular_memory_size</span></span>          | <span data-ttu-id="539a1-232">通常のメモリ プールのサイズ</span><span class="sxs-lookup"><span data-stu-id="539a1-232">Size of the regular memory pool</span></span>         |
| <span data-ttu-id="539a1-233">VOID \*cache_safe_memory_pool_start</span><span class="sxs-lookup"><span data-stu-id="539a1-233">VOID \*cache_safe_memory_pool_start</span></span> | <span data-ttu-id="539a1-234">キャッシュ セーフ メモリ プールの開始</span><span class="sxs-lookup"><span data-stu-id="539a1-234">Beginning of the cache safe memory pool</span></span> |
| <span data-ttu-id="539a1-235">ULONG cache_safe_memory_size</span><span class="sxs-lookup"><span data-stu-id="539a1-235">ULONG cache_safe_memory_size</span></span>       | <span data-ttu-id="539a1-236">キャッシュ セーフ メモリ プールのサイズ</span><span class="sxs-lookup"><span data-stu-id="539a1-236">Size of the cache safe memory pool</span></span>      |

<span data-ttu-id="539a1-237">キャッシュ セーフ メモリの定義を必要としないシステムもあります。</span><span class="sxs-lookup"><span data-stu-id="539a1-237">Not all systems require the definition of cache safe memory.</span></span> <span data-ttu-id="539a1-238">このようなシステムでは、メモリ ポインターの初期化中に渡された値は UX_NULL に、プールのサイズは 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="539a1-238">In such a system, the values passed during the initialization for the memory pointer will be set to UX_NULL and the size of the pool to 0.</span></span> <span data-ttu-id="539a1-239">その後、USBX はキャッシュ セーフ プールの代わりに通常のメモリ プールを使用します。</span><span class="sxs-lookup"><span data-stu-id="539a1-239">USBX will then use the regular memory pool in lieu of the cache safe pool.</span></span>

<span data-ttu-id="539a1-240">通常のメモリがキャッシュ セーフではなく、コントローラーが DMA メモリを実行する必要があるシステムでは、キャッシュ セーフ ゾーン内でメモリ プールを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="539a1-240">In a system where the regular memory is not cache safe and a controller requires to perform DMA memory it is necessary to define a memory pool in a cache safe zone.</span></span>

## <a name="uninitialization-of-usbx-resources"></a><span data-ttu-id="539a1-241">USBX リソースを初期化前の状態に戻す</span><span class="sxs-lookup"><span data-stu-id="539a1-241">Uninitialization of USBX resources</span></span>

<span data-ttu-id="539a1-242">USBX を終了するには、そのリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="539a1-242">USBX can be terminated by releasing its resources.</span></span> <span data-ttu-id="539a1-243">USBX を終了する前に、すべてのクラスとコントローラー リソースを適切に終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="539a1-243">Prior to terminating usbx, all classes and controller resources need to be terminated properly.</span></span> <span data-ttu-id="539a1-244">次の関数は、USBX メモリ リソースを初期化前の状態に戻します。</span><span class="sxs-lookup"><span data-stu-id="539a1-244">The following function uninitializes USBX memory resources:</span></span>

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

<span data-ttu-id="539a1-245">ux_system_initialize のプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="539a1-245">The prototype for the ux_system_initialize is as follows:</span></span>

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-device-controller"></a><span data-ttu-id="539a1-246">USB デバイス コントローラーの定義</span><span class="sxs-lookup"><span data-stu-id="539a1-246">Definition of USB Device Controller</span></span>

<span data-ttu-id="539a1-247">デバイス モードで動作する場合は、一度に 1 つの USB デバイス コントローラーだけを定義できます。</span><span class="sxs-lookup"><span data-stu-id="539a1-247">Only one USB device controller can be defined at any time to operate in device mode.</span></span> <span data-ttu-id="539a1-248">アプリケーション初期化ファイルには、この定義が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="539a1-248">The application initialization file should contain this definition.</span></span> <span data-ttu-id="539a1-249">次の行は、汎用 USB コントローラーの定義を実行します。</span><span class="sxs-lookup"><span data-stu-id="539a1-249">The following line performs the definition of a generic usb controller:</span></span>

```c
ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);
```

<span data-ttu-id="539a1-250">USB デバイスの初期化には、次のプロトタイプがあります。</span><span class="sxs-lookup"><span data-stu-id="539a1-250">The USB device initialization has the following prototype:</span></span>

```c
UINT ux_dcd_controller_initialize(ULONG dcd_io,
    ULONG dcd_irq, ULONG dcd_vbus_address);
```

<span data-ttu-id="539a1-251">次のパラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="539a1-251">with the following parameters:</span></span>

| <span data-ttu-id="539a1-252">パラメーター</span><span class="sxs-lookup"><span data-stu-id="539a1-252">Pararmeter</span></span>               | <span data-ttu-id="539a1-253">説明</span><span class="sxs-lookup"><span data-stu-id="539a1-253">Description</span></span>                      |
| ------------------------ | -------------------------------- |
| <span data-ttu-id="539a1-254">ULONG dcd_io</span><span class="sxs-lookup"><span data-stu-id="539a1-254">ULONG dcd_io</span></span>            | <span data-ttu-id="539a1-255">コントローラー IO のアドレス</span><span class="sxs-lookup"><span data-stu-id="539a1-255">Address of the controller IO</span></span>     |
| <span data-ttu-id="539a1-256">ULONG dcd_irq</span><span class="sxs-lookup"><span data-stu-id="539a1-256">ULONG dcd_irq</span></span>           | <span data-ttu-id="539a1-257">コントローラーによって使用される割り込み</span><span class="sxs-lookup"><span data-stu-id="539a1-257">Interrupt used by the controller</span></span> |
| <span data-ttu-id="539a1-258">ULONG dcd_vbus_address</span><span class="sxs-lookup"><span data-stu-id="539a1-258">ULONG dcd_vbus_address</span></span> | <span data-ttu-id="539a1-259">VBUS GPIO のアドレス</span><span class="sxs-lookup"><span data-stu-id="539a1-259">Address of the VBUS GPIO</span></span>         |

<span data-ttu-id="539a1-260">次の例は、ストレージ デバイス クラスと汎用コントローラーを使って USBX をデバイス モードで初期化する方法を示したものです。</span><span class="sxs-lookup"><span data-stu-id="539a1-260">The following example is the initialization of USBX in device mode with the storage device class and a generic controller:</span></span>

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024), 0, 0);

/* The code below is required for installing the device portion of USBX */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, installation was successful. */

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(ux_system_slave_class_storage_name ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *)&storage_parameter);

/* Register the device controllers available in this system */
status = ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);

/* If status equals UX_SUCCESS, registration was successful. */
```

## <a name="troubleshooting"></a><span data-ttu-id="539a1-261">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="539a1-261">Troubleshooting</span></span>

<span data-ttu-id="539a1-262">USBX には、デモンストレーション ファイルとシミュレーション環境が付属しています。</span><span class="sxs-lookup"><span data-stu-id="539a1-262">USBX is delivered with a demonstration file and a simulation environment.</span></span> <span data-ttu-id="539a1-263">まずは、ターゲット ハードウェアまたは特定のデモンストレーション プラットフォームのいずれかで、デモンストレーション プラットフォームを稼働させることを常にお勧めします。</span><span class="sxs-lookup"><span data-stu-id="539a1-263">It is always a good idea to get the demonstration platform running first—either on the target hardware or a specific demonstration platform.</span></span>

## <a name="usbx-version-id"></a><span data-ttu-id="539a1-264">USBX のバージョン ID</span><span class="sxs-lookup"><span data-stu-id="539a1-264">USBX Version ID</span></span>

<span data-ttu-id="539a1-265">現在使用している USBX のバージョンは、実行時にユーザーとアプリケーション ソフトウェアのどちらからでも確認できます。</span><span class="sxs-lookup"><span data-stu-id="539a1-265">The current version of USBX is available both to the user and the application software during run-time.</span></span> <span data-ttu-id="539a1-266">プログラマーは \***ux_port.h** _ ファイルを調べることで USBX のバージョンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="539a1-266">The programmer can obtain the USBX version from examination of the \***ux_port.h** _ file.</span></span> <span data-ttu-id="539a1-267">加えて、このファイルには、対応するポートのバージョン履歴も含まれています。</span><span class="sxs-lookup"><span data-stu-id="539a1-267">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="539a1-268">アプリケーション ソフトウェアは、_*_ux_port.h_*\* 内で定義されているグローバル文字列 _ \*_ _ux_version_id_\* _ を調べることで USBX バージョンを取得できます。</span><span class="sxs-lookup"><span data-stu-id="539a1-268">Application software can obtain the USBX version by examining the global string _ *_ _ux_version_id_* _, which is defined in _\*_ux_port.h_\*\*.</span></span>
