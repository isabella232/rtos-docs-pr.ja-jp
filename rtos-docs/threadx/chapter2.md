---
title: 第 2 章 - Azure RTOS ThreadX のインストールと使用
description: この章では、Azure RTOS ThreadX の高パフォーマンス カーネルのインストール、設定、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e1bf85d363b07c81f226d494107eae9ba18114a7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810271"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-threadx"></a><span data-ttu-id="997dd-103">第 2 章 - Azure RTOS ThreadX のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="997dd-103">Chapter 2 - Installation and Use of Azure RTOS ThreadX</span></span>

<span data-ttu-id="997dd-104">この章では、Azure RTOS ThreadX の高パフォーマンス カーネルのインストール、設定、使用に関連するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="997dd-104">This chapter contains a description of various issues related to installation, setup, and usage of the high-performance Azure RTOS ThreadX kernel.</span></span>

## <a name="host-considerations"></a><span data-ttu-id="997dd-105">ホストに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="997dd-105">Host Considerations</span></span>

<span data-ttu-id="997dd-106">埋め込みソフトウェアは、通常は Windows または Linux (Unix) ホスト コンピューターで開発されています。</span><span class="sxs-lookup"><span data-stu-id="997dd-106">Embedded software is usually developed on Windows or Linux (Unix) host computers.</span></span> <span data-ttu-id="997dd-107">アプリケーションは、ホスト上でコンパイル、リンク、および配置された後、実行のためにターゲット ハードウェアにダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="997dd-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

<span data-ttu-id="997dd-108">通常、ターゲットへのダウンロードは、開発ツールのデバッガー内から実行されます。</span><span class="sxs-lookup"><span data-stu-id="997dd-108">Usually the target download is done from within the development tool debugger.</span></span> <span data-ttu-id="997dd-109">ダウンロードの完了後、デバッガーは、メモリおよびプロセッサ レジスタへのアクセスだけでなく、ターゲットの実行制御 (移動、停止、ブレークポイントなど) を提供します。</span><span class="sxs-lookup"><span data-stu-id="997dd-109">After the download has completed, the debugger is responsible for providing target execution control (go, halt, breakpoint, etc.) as well as access to memory and processor registers.</span></span>

<span data-ttu-id="997dd-110">開発ツール デバッガーのほとんどが、JTAG (IEEE 1149.1) やバックグラウンド デバッグ モード (BDM) などのオンチップ デバッグ (OCD) 接続を介してターゲット ハードウェアと通信します。</span><span class="sxs-lookup"><span data-stu-id="997dd-110">Most development tool debuggers communicate with the target hardware via on-chip debug (OCD) connections such as JTAG (IEEE 1149.1) and Background Debug Mode (BDM).</span></span> <span data-ttu-id="997dd-111">また、デバッガーは、インサーキット エミュレーション (ICE) 接続を使用してターゲット ハードウェアと通信することもあります。</span><span class="sxs-lookup"><span data-stu-id="997dd-111">Debuggers also communicate with target hardware through In-Circuit Emulation (ICE) connections.</span></span> <span data-ttu-id="997dd-112">OCD 接続と ICE 接続はどちらも、ターゲットの常駐ソフトウェアへの侵入を最小限に抑えた堅牢なソリューションを提供します。</span><span class="sxs-lookup"><span data-stu-id="997dd-112">Both OCD and ICE connections provide robust solutions with minimal intrusion on the target resident software.</span></span>

<span data-ttu-id="997dd-113">ホスト上で使用されるリソースについては、ThreadX のソース コードは ASCII 形式で提供され、ホスト コンピューターのハード ディスク上に約 1 MB の空き領域が必要です。</span><span class="sxs-lookup"><span data-stu-id="997dd-113">As for resources used on the host, the source code for ThreadX is delivered in ASCII format and requires approximately 1 MByte of space on the host computer's hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="997dd-114">ターゲットに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="997dd-114">Target Considerations</span></span>

<span data-ttu-id="997dd-115">ThreadX は、ターゲット上に 2 KB から 20 KB の読み取り専用メモリ (ROM) を必要とします。</span><span class="sxs-lookup"><span data-stu-id="997dd-115">ThreadX requires between 2 KBytes and 20 KBytes of Read Only Memory (ROM) on the target.</span></span> <span data-ttu-id="997dd-116">また、ThreadX システム スタックおよびその他のグローバル データ構造用に、ターゲットのランダム アクセス メモリ (RAM) がさらに 1 KB から 2 KB 必要です。</span><span class="sxs-lookup"><span data-stu-id="997dd-116">It also requires another 1 to 2 KBytes of the target's Random Access Memory (RAM) for the ThreadX system stack and other global data structures.</span></span>

<span data-ttu-id="997dd-117">サービス呼び出しタイムアウト、タイムスライス、アプリケーション タイマーなどのタイマー関連関数が機能するためには、基になるターゲット ハードウェアは定期的な割り込みソースを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="997dd-117">For timer-related functions like service call time-outs, time-slicing, and application timers to function, the underlying target hardware must provide a periodic interrupt source.</span></span> <span data-ttu-id="997dd-118">プロセッサがこの機能を備えている場合は、ThreadX によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="997dd-118">If the processor has this capability, it is utilized by ThreadX.</span></span> <span data-ttu-id="997dd-119">あるいは、ターゲット プロセッサに定期的な割り込みを生成する機能がない場合は、ユーザーのハードウェアがそれを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="997dd-119">Otherwise, if the target processor does not have the ability to generate a periodic interrupt, the user's hardware must provide it.</span></span> <span data-ttu-id="997dd-120">タイマー割り込みの設定と構成は、通常は ThreadX ディストリビューションの ***tx_initialize_low_level*** アセンブリ ファイルにあります。</span><span class="sxs-lookup"><span data-stu-id="997dd-120">Setup and configuration of the timer interrupt is typically located in the ***tx_initialize_low_level*** assembly file in the ThreadX distribution.</span></span>

> [!NOTE]
> <span data-ttu-id="997dd-121">*定期的なタイマー割り込みソースを使用できない場合でも、ThreadX は機能します。ただし、タイマー関連サービスはいずれも機能しません。*</span><span class="sxs-lookup"><span data-stu-id="997dd-121">*ThreadX is still functional even if no periodic timer interrupt source is available. However, none of the timer-related services are functional.*</span></span>

## <a name="product-distribution"></a><span data-ttu-id="997dd-122">製品の配布</span><span class="sxs-lookup"><span data-stu-id="997dd-122">Product Distribution</span></span>

<span data-ttu-id="997dd-123">Azure RTOS ThreadX は、<https://github.com/azure-rtos/threadx/> のパブリック ソース コード リポジトリから入手できます。</span><span class="sxs-lookup"><span data-stu-id="997dd-123">Azure RTOS ThreadX can be obtained from our public source code repository at <https://github.com/azure-rtos/threadx/>.</span></span>

<span data-ttu-id="997dd-124">以下は、リポジトリ内のいくつかの重要なファイルの一覧です。</span><span class="sxs-lookup"><span data-stu-id="997dd-124">The following is a list of several important files in the repository.</span></span>

| <span data-ttu-id="997dd-125">ファイル名</span><span class="sxs-lookup"><span data-stu-id="997dd-125">Filename</span></span> | <span data-ttu-id="997dd-126">説明</span><span class="sxs-lookup"><span data-stu-id="997dd-126">Description</span></span> |
|------------------- | ----------- |
| <span data-ttu-id="997dd-127">**tx_api.h**</span><span class="sxs-lookup"><span data-stu-id="997dd-127">**tx_api.h**</span></span>                      | <span data-ttu-id="997dd-128">すべてのシステム等価物、データ構造、およびサービス プロトタイプが含まれる C ヘッダーファイル。</span><span class="sxs-lookup"><span data-stu-id="997dd-128">C header file containing all system equates, data structures, and service prototypes.</span></span>                                                             |
| <span data-ttu-id="997dd-129">**tx_port.h**</span><span class="sxs-lookup"><span data-stu-id="997dd-129">**tx_port.h**</span></span>                     | <span data-ttu-id="997dd-130">すべての開発ツール、およびターゲット固有のデータの定義と構造が含まれる C ヘッダー ファイル。</span><span class="sxs-lookup"><span data-stu-id="997dd-130">C header file containing all development-tool and targetspecific data definitions and structures.</span></span>                                                 |
| <span data-ttu-id="997dd-131">**demo_threadx.c**</span><span class="sxs-lookup"><span data-stu-id="997dd-131">**demo_threadx.c**</span></span>                | <span data-ttu-id="997dd-132">小規模なデモ アプリケーションが含まれる C ファイル。</span><span class="sxs-lookup"><span data-stu-id="997dd-132">C file containing a small demo application.</span></span>                                                                                                       |
| <span data-ttu-id="997dd-133">**tx.a (または tx.lib)**</span><span class="sxs-lookup"><span data-stu-id="997dd-133">**tx.a (or tx.lib)**</span></span>              | <span data-ttu-id="997dd-134">"*標準*" パッケージと共に配布される ThreadX C ライブラリのバイナリ バージョン。</span><span class="sxs-lookup"><span data-stu-id="997dd-134">Binary version of the ThreadX C library that is distributed with the *standard* package.</span></span>                                                          |
|                                   |                                                                                                                                                   |

>[!NOTE]
><span data-ttu-id="997dd-135">*ファイル名はすべて小文字で表記します。この名前付け規則を使用することで、コマンドを Linux (Unix) 開発プラットフォームに簡単に変換できます。*</span><span class="sxs-lookup"><span data-stu-id="997dd-135">*All file names are in lower-case. This naming convention makes it easier to convert the commands to Linux (Unix) development platforms.*</span></span>

## <a name="threadx-installation"></a><span data-ttu-id="997dd-136">ThreadX のインストール</span><span class="sxs-lookup"><span data-stu-id="997dd-136">ThreadX Installation</span></span>

<span data-ttu-id="997dd-137">ThreadX は、GitHub リポジトリをローカル コンピューターに複製することによってインストールされます。</span><span class="sxs-lookup"><span data-stu-id="997dd-137">ThreadX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="997dd-138">お使いの PC 上に ThreadX リポジトリの複製を作成するための一般的な構文を次に示します。</span><span class="sxs-lookup"><span data-stu-id="997dd-138">The following is typical syntax for creating a clone of the ThreadX repository on your PC.</span></span>

```c
    git clone https://github.com/azure-rtos/threadx
```

<span data-ttu-id="997dd-139">GitHub メイン ページ上のダウンロード ボタンを使用して、リポジトリのコピーをダウンロードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="997dd-139">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="997dd-140">また、オンライン リポジトリのフロント ページ上で ThreadX ライブラリを構築する手順も紹介します。</span><span class="sxs-lookup"><span data-stu-id="997dd-140">You will also find instructions for building the ThreadX library on the front page of the online repository.</span></span>

> [!NOTE]
> <span data-ttu-id="997dd-141">*アプリケーション ソフトウェアが ThreadX SMP ライブラリ ファイル (通常は **tx.a** または **tx.lib**) と、C インクルード ファイル **_tx_api.h_* _ および _*_tx_port.h_*_ にアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="997dd-141">*Application software needs access to the ThreadX library file (usually **tx.a** or **tx.lib**) and the C include files **_tx_api.h_* _ and _*_tx_port.h_*_.</span></span> <span data-ttu-id="997dd-142">そのためには、開発ツールで適切なパスを設定するか、アプリケーション開発を行う領域にこれらのファイルをコピーします。_</span><span class="sxs-lookup"><span data-stu-id="997dd-142">This is accomplished either by setting the appropriate path for the development tools or by copying these files into the application development area._</span></span>

## <a name="using-threadx"></a><span data-ttu-id="997dd-143">ThreadX を使用する</span><span class="sxs-lookup"><span data-stu-id="997dd-143">Using ThreadX</span></span>

<span data-ttu-id="997dd-144">ThreadX を使用するには、アプリケーション コードには ***tx_api.h** _ をコンパイル中に含めて、ThreadX SMP ランタイム ライブラリ _*_tx.a_*_ (または _*_tx.lib)_ \*\* とリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="997dd-144">To use ThreadX, the application code must include ***tx_api.h** _ during compilation and link with the ThreadX run-time library _*_tx.a_*_ (or _*_tx.lib_\*\*).</span></span>

<span data-ttu-id="997dd-145">ThreadX アプリケーションをビルドするには、次の 4 つの手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="997dd-145">There are four steps required to build a ThreadX application.</span></span>

1. <span data-ttu-id="997dd-146">***tx_api.h*** ファイルを、ThreadX のサービスまたはデータ構造を使用するすべてのアプリケーション ファイル内に追加します。</span><span class="sxs-lookup"><span data-stu-id="997dd-146">Include the ***tx_api.h*** file in all application files that use ThreadX services or data structures.</span></span>

1. <span data-ttu-id="997dd-147">標準の C \***main** _ 関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="997dd-147">Create the standard C \***main** _ function.</span></span> <span data-ttu-id="997dd-148">この関数が最終的に _ *_tx_kernel_enter_*\* を呼び出して THREADX を開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="997dd-148">This function must eventually call _ *_tx_kernel_enter_*\* to start ThreadX.</span></span> <span data-ttu-id="997dd-149">ThreadX に関係しないアプリケーション固有の初期化が、カーネルに入る前に追加される場合があります。</span><span class="sxs-lookup"><span data-stu-id="997dd-149">Application-specific initialization that does not involve ThreadX may be added prior to entering the kernel.</span></span>

      > [!IMPORTANT]
      > <span data-ttu-id="997dd-150">\*ThreadX のエントリ関数 \***tx_kernel_enter** _ は戻りません。</span><span class="sxs-lookup"><span data-stu-id="997dd-150">\*The ThreadX entry function \***tx_kernel_enter** _ does not return.</span></span> <span data-ttu-id="997dd-151">したがって、その後で一切の処理または関数の呼び出しを行わないようにしてください。_</span><span class="sxs-lookup"><span data-stu-id="997dd-151">So be sure not to place any processing or function calls after it._</span></span>

1. <span data-ttu-id="997dd-152">***tx_application_define*** 関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="997dd-152">Create the ***tx_application_define*** function.</span></span> <span data-ttu-id="997dd-153">ここに、最初のシステム リソースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="997dd-153">This is where the initial system resources are created.</span></span> <span data-ttu-id="997dd-154">システム リソースの例としては、スレッド、キュー、メモリ プール、イベント フラグ グループ、ミューテックス、セマフォなどがあります。</span><span class="sxs-lookup"><span data-stu-id="997dd-154">Examples of system resources include threads, queues, memory pools, event flags groups, mutexes, and semaphores.</span></span>

1. <span data-ttu-id="997dd-155">アプリケーション ソースをコンパイルして、ThreadX ランタイム ライブラリ ***tx.lib*** にリンクします。</span><span class="sxs-lookup"><span data-stu-id="997dd-155">Compile application source and link with the ThreadX run-time library ***tx.lib***.</span></span> <span data-ttu-id="997dd-156">結果のイメージはターゲットにダウンロードして、実行できます。</span><span class="sxs-lookup"><span data-stu-id="997dd-156">The resulting image can be downloaded to the target and executed!</span></span>

## <a name="small-example-system"></a><span data-ttu-id="997dd-157">小規模のシステム例</span><span class="sxs-lookup"><span data-stu-id="997dd-157">Small Example System</span></span>

<span data-ttu-id="997dd-158">図 1 の小規模のシステム例は、優先度が 3 のシングル スレッドの作成を示しています。</span><span class="sxs-lookup"><span data-stu-id="997dd-158">The small example system in Figure 1 shows the creation of a single thread with a priority of 3.</span></span> <span data-ttu-id="997dd-159">スレッドは実行されて、カウンターが増え、時計の 1 目盛り分の間スリープ状態になります。</span><span class="sxs-lookup"><span data-stu-id="997dd-159">The thread executes, increments a counter, then sleeps for one clock tick.</span></span>
<span data-ttu-id="997dd-160">このプロセスは永久に続きます。</span><span class="sxs-lookup"><span data-stu-id="997dd-160">This process continues forever.</span></span>

```c
#include "tx_api.h"
unsigned long my_thread_counter = 0;
TX_THREAD my_thread;
main( )
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter( );
}
void tx_application_define(void *first_unused_memory)
{
    /* Create my_thread! */
    tx_thread_create(&my_thread, "My Thread",
    my_thread_entry, 0x1234, first_unused_memory, 1024,
    3, 3, TX_NO_TIME_SLICE, TX_AUTO_START);
}
void my_thread_entry(ULONG thread_input)
{
    /* Enter into a forever loop. */
    while(1)
    {
        /* Increment thread counter. */
        my_thread_counter++;
        /* Sleep for 1 tick. */
        tx_thread_sleep(1);
    }
}
```

<span data-ttu-id="997dd-161">**図 1. アプリケーション開発のためのテンプレート**</span><span class="sxs-lookup"><span data-stu-id="997dd-161">**FIGURE 1. Template for Application Development**</span></span>

<span data-ttu-id="997dd-162">これは簡単な例ですが、実際のアプリケーション開発に適したテンプレートとなります。</span><span class="sxs-lookup"><span data-stu-id="997dd-162">Although this is a simple example, it provides a good template for real application development.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="997dd-163">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="997dd-163">Troubleshooting</span></span>

<span data-ttu-id="997dd-164">各 ThreadX ポートには、デモンストレーション アプリケーションが付属しています。</span><span class="sxs-lookup"><span data-stu-id="997dd-164">Each ThreadX port is delivered with a demonstration application.</span></span> <span data-ttu-id="997dd-165">実際のターゲット ハードウェアまたはシミュレートされた環境で、最初にデモンストレーション システムを稼働させることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="997dd-165">It is always a good idea to first get the demonstration system running—either on actual target hardware or simulated environment.</span></span>

<span data-ttu-id="997dd-166">デモンストレーション システムが正常に実行されない場合のトラブルシューティングのヒントを、以下に示します。</span><span class="sxs-lookup"><span data-stu-id="997dd-166">If the demonstration system does not execute properly, the following are some troubleshooting tips.</span></span>

1. <span data-ttu-id="997dd-167">実行中のデモンストレーションの量を確認します。</span><span class="sxs-lookup"><span data-stu-id="997dd-167">Determine how much of the demonstration is running.</span></span>
1. <span data-ttu-id="997dd-168">スタック サイズを増やします (これは、デモンストレーションよりも実際のアプリケーション コードでより重要です)。</span><span class="sxs-lookup"><span data-stu-id="997dd-168">Increase stack sizes (this is more important in actual application code than it is for the demonstration).</span></span>
1. <span data-ttu-id="997dd-169">TX_ENABLE_STACK_CHECKING を定義して ThreadX ライブラリをリビルドします。</span><span class="sxs-lookup"><span data-stu-id="997dd-169">Rebuild the ThreadX library with TX_ENABLE_STACK_CHECKING defined.</span></span> <span data-ttu-id="997dd-170">これにより、組み込みの ThreadX スタック チェックが有効になります。</span><span class="sxs-lookup"><span data-stu-id="997dd-170">This enables the built-in ThreadX stack checking.</span></span>
1. <span data-ttu-id="997dd-171">最近の変更を一時的にバイパスして、問題が解消または変更するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="997dd-171">Temporarily bypass any recent changes to see if the problem disappears or changes.</span></span> <span data-ttu-id="997dd-172">このような情報は、サポート エンジニアにとって有益です。</span><span class="sxs-lookup"><span data-stu-id="997dd-172">Such information should prove useful to support engineers.</span></span>

<span data-ttu-id="997dd-173">「[カスタマー サポート センター](about-this-guide.md#customer-support-center)」に記載されている手順に従って、トラブルシューティング手順で収集した情報を送信します。</span><span class="sxs-lookup"><span data-stu-id="997dd-173">Follow the procedures outlined in "[Customer Support Center](about-this-guide.md#customer-support-center)" to send the information gathered from the troubleshooting steps.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="997dd-174">構成オプション</span><span class="sxs-lookup"><span data-stu-id="997dd-174">Configuration Options</span></span>

<span data-ttu-id="997dd-175">ThreadX を使用して ThreadX ライブラリとアプリケーションをビルドする場合、構成オプションがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="997dd-175">There are several configuration options when building the ThreadX library and the application using ThreadX.</span></span> <span data-ttu-id="997dd-176">以下のオプションは、アプリケーション ソース内、コマンド ライン上、または ***tx_user.h*** インクルード ファイル内で定義できます。</span><span class="sxs-lookup"><span data-stu-id="997dd-176">The options below can be defined in the application source, on the command line, or within the ***tx_user.h*** include file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="997dd-177">\*\*\*\*tx_user.h\*\* _ 内で定義されているオプションは、アプリケーションと ThreadX ライブラリが、_ *TX_INCLUDE_USER_DEFINE_FILE*\* を定義してビルドされている場合にのみ適用されます。\*</span><span class="sxs-lookup"><span data-stu-id="997dd-177">*Options defined in ***tx_user.h** _ are applied only if the application and ThreadX library are built with _ *TX_INCLUDE_USER_DEFINE_FILE** defined.*</span></span>

### <a name="smallest-configuration"></a><span data-ttu-id="997dd-178">最小の構成</span><span class="sxs-lookup"><span data-stu-id="997dd-178">Smallest Configuration</span></span>

<span data-ttu-id="997dd-179">コード サイズを最小にするには、次の ThreadX 構成オプションを考慮する必要があります (他のすべてのオプションが存在しない場合)。</span><span class="sxs-lookup"><span data-stu-id="997dd-179">For the smallest code size, the following ThreadX configuration options should be considered (in absence of all other options).</span></span>

```c
TX_DISABLE_ERROR_CHECKING
TX_DISABLE_PREEMPTION_THRESHOLD
TX_DISABLE_NOTIFY_CALLBACKS
TX_DISABLE_REDUNDANT_CLEARING
TX_DISABLE_STACK_FILLING
TX_NOT_INTERRUPTABLE
TX_TIMER_PROCESS_IN_ISR
```

### <a name="fastest-configuration"></a><span data-ttu-id="997dd-180">最も速い構成</span><span class="sxs-lookup"><span data-stu-id="997dd-180">Fastest Configuration</span></span>

<span data-ttu-id="997dd-181">実行速度を最速にするには、以前の最小の構成で使用したものと同じ構成オプションを使用します。ただし、これらのオプションも考慮します。</span><span class="sxs-lookup"><span data-stu-id="997dd-181">For the fastest execution, the same configuration options used for the Smallest Configuration previously, but with these options also considered.</span></span>

```c
TX_REACTIVATE_INLINE
TX_INLINE_THREAD_RESUME_SUSPEND
```

<span data-ttu-id="997dd-182">[詳細な構成オプション](#detailed-configuration-options)が説明されています。</span><span class="sxs-lookup"><span data-stu-id="997dd-182">[Detailed configuration options](#detailed-configuration-options) are described.</span></span>

### <a name="global-time-source"></a><span data-ttu-id="997dd-183">グローバル タイム ソース</span><span class="sxs-lookup"><span data-stu-id="997dd-183">Global Time Source</span></span>

<span data-ttu-id="997dd-184">他の Microsoft Azure RTOS 製品 (FileX、NetX、GUIX、USBX など) では、ThreadX で 1 秒を表す ThreadX タイマー刻みの数が定義されています。</span><span class="sxs-lookup"><span data-stu-id="997dd-184">For other Microsoft Azure RTOS products (FileX, NetX, GUIX, USBX, etc.), ThreadX defines the number of ThreadX timer ticks that represents one second.</span></span> <span data-ttu-id="997dd-185">この定数に基づいて各種の時間要件が導き出されます。</span><span class="sxs-lookup"><span data-stu-id="997dd-185">Others derive their time requirements based on this constant.</span></span> <span data-ttu-id="997dd-186">既定では、この値は 100 で、10 ミリ秒の定期的割り込みを想定しています。</span><span class="sxs-lookup"><span data-stu-id="997dd-186">By default, the value is 100, assuming a 10ms periodic interrupt.</span></span> <span data-ttu-id="997dd-187">この値をユーザーがオーバーライドするには、***tx_port.h*** または IDE あるいはコマンド ライン内で TX_TIMER_TICKS_PER_SECOND を必要な値で定義します。</span><span class="sxs-lookup"><span data-stu-id="997dd-187">The user may override this value by defining TX_TIMER_TICKS_PER_SECOND with the desired value in ***tx_port.h*** or within the IDE or command line.</span></span>

### <a name="detailed-configuration-options"></a><span data-ttu-id="997dd-188">詳細な構成オプション</span><span class="sxs-lookup"><span data-stu-id="997dd-188">Detailed Configuration Options</span></span>

<span data-ttu-id="997dd-189">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="997dd-189">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="997dd-190">このオプションを定義すると、バイト プールのパフォーマンス情報の収集が有効になります。</span><span class="sxs-lookup"><span data-stu-id="997dd-190">When defined, this option enables the gathering of performance information on byte pools.</span></span> <span data-ttu-id="997dd-191">既定では、このオプションは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="997dd-191">By default, this option is not defined.</span></span>

<span data-ttu-id="997dd-192">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="997dd-192">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="997dd-193">このオプションを定義すると、バイト プールのパフォーマンス情報の収集が有効になります。</span><span class="sxs-lookup"><span data-stu-id="997dd-193">When defined, this option enables the gathering of performance information on byte pools.</span></span> <span data-ttu-id="997dd-194">既定では、このオプションは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="997dd-194">By default, this option is not defined.</span></span>

<span data-ttu-id="997dd-195">**TX_DISABLE_ERROR_CHECKING**</span><span class="sxs-lookup"><span data-stu-id="997dd-195">**TX_DISABLE_ERROR_CHECKING**</span></span>

<span data-ttu-id="997dd-196">基本的なサービス呼び出しエラー チェックをバイパスします。</span><span class="sxs-lookup"><span data-stu-id="997dd-196">Bypasses basic service call error checking.</span></span> <span data-ttu-id="997dd-197">アプリケーション ソースで定義されていると、すべての基本パラメーター エラー チェックが無効になります。</span><span class="sxs-lookup"><span data-stu-id="997dd-197">When defined in the application source, all basic parameter error checking is disabled.</span></span> <span data-ttu-id="997dd-198">これによりパフォーマンスが最大 30% 向上する場合があり、イメージ サイズも小さくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="997dd-198">This may improve performance by as much as 30% and may also reduce the image size.</span></span>

> [!NOTE]
> <span data-ttu-id="997dd-199">*エラー チェックを無効にしても安全なのは、アプリケーションですべての入力パラメーターが、外部入力から派生した入力パラメーターも含めて、すべての状況で常に有効であると保証される場合だけです。無効な入力が API に提供され、エラー チェックが無効になっている場合、その結果の動作は定義されていないため、メモリが破損したりシステムがクラッシュする可能性があります。*</span><span class="sxs-lookup"><span data-stu-id="997dd-199">*It is only safe to disable error checking if the application can absolutely guarantee all input parameters are always valid under all circumstances, including input parameters derived from external input. If invalid input is supplied to the API with error checking disabled, the resulting behavior is undefined and could result in memory corruption or system crash.*</span></span>

> [!NOTE]
> <span data-ttu-id="997dd-200">*エラー チェックを無効にすることの影響がない ThreadX API の戻り値を、第 4 章の各 API の説明の「戻り値」セクションに太字で示しています。太字でない戻り値は、TX_DISABLE_ERROR_CHECKING オプションを使用してエラー チェックを無効にしている場合は void になります。*</span><span class="sxs-lookup"><span data-stu-id="997dd-200">*ThreadX API return values not affected by disabling error checking are listed in bold in the “Return Values” section of each API description in Chapter 4. The nonbold return values are void if error checking is disabled by using the TX_DISABLE_ERROR_CHECKING option.*</span></span>

<span data-ttu-id="997dd-201">**TX_DISABLE_NOTIFY_CALLBACKS**</span><span class="sxs-lookup"><span data-stu-id="997dd-201">**TX_DISABLE_NOTIFY_CALLBACKS**</span></span>

<span data-ttu-id="997dd-202">定義されている場合、さまざまな ThreadX オブジェクトの通知コールバックが無効になります。</span><span class="sxs-lookup"><span data-stu-id="997dd-202">When defined, disables the notify callbacks for various ThreadX objects.</span></span> <span data-ttu-id="997dd-203">このオプションを使用するとコード サイズが若干減り、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="997dd-203">Using this option slightly reduces code size and improves performance.</span></span> <span data-ttu-id="997dd-204">既定では、このオプションは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="997dd-204">By default, this option is not defined.</span></span>

<span data-ttu-id="997dd-205">**TX_DISABLE_PREEMPTION_THRESHOLD**</span><span class="sxs-lookup"><span data-stu-id="997dd-205">**TX_DISABLE_PREEMPTION_THRESHOLD**</span></span>

<span data-ttu-id="997dd-206">定義されている場合、プリエンプションしきい値機能が無効になり、コード サイズが若干減って、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="997dd-206">When defined, disables the preemption-threshold feature and slightly reduces code size and improves performance.</span></span> <span data-ttu-id="997dd-207">もちろん、プリエンプションしきい値機能は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="997dd-207">Of course, the preemption-threshold capabilities are no longer available.</span></span> <span data-ttu-id="997dd-208">既定では、このオプションは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="997dd-208">By default, this option is not defined.</span></span>

<span data-ttu-id="997dd-209">**TX_DISABLE_REDUNDANT_CLEARING**</span><span class="sxs-lookup"><span data-stu-id="997dd-209">**TX_DISABLE_REDUNDANT_CLEARING**</span></span>

<span data-ttu-id="997dd-210">定義されている場合、ThreadX のグローバル C データ構造をゼロに初期化するためのロジックが削除されます。</span><span class="sxs-lookup"><span data-stu-id="997dd-210">When defined, removes the logic for initializing ThreadX global C data structures to zero.</span></span> <span data-ttu-id="997dd-211">コンパイラの初期化コードが初期化されていないすべての C グローバル データをゼロに設定する場合のみに使用してください。</span><span class="sxs-lookup"><span data-stu-id="997dd-211">This should only be used if the compiler's initialization code sets all un-initialized C global data to zero.</span></span> <span data-ttu-id="997dd-212">このオプションを使用するとコード サイズが若干減り、初期化中のパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="997dd-212">Using this option slightly reduces code size and improves performance during initialization.</span></span> <span data-ttu-id="997dd-213">既定では、このオプションは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="997dd-213">By default, this option is not defined.</span></span>

<span data-ttu-id="997dd-214">**TX_DISABLE_STACK_FILLING**</span><span class="sxs-lookup"><span data-stu-id="997dd-214">**TX_DISABLE_STACK_FILLING**</span></span>

<span data-ttu-id="997dd-215">定義されている場合、各スレッドのスタックの作成時に各バイトへの 0xEF 値の配置が無効になります。</span><span class="sxs-lookup"><span data-stu-id="997dd-215">When defined, disables placing the 0xEF value in each byte of each thread's stack when created.</span></span> <span data-ttu-id="997dd-216">既定では、このオプションは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="997dd-216">By default, this option is not defined.</span></span>

<span data-ttu-id="997dd-217">**TX_ENABLE_EVENT_TRACE**</span><span class="sxs-lookup"><span data-stu-id="997dd-217">**TX_ENABLE_EVENT_TRACE**</span></span>

<span data-ttu-id="997dd-218">定義されている場合、ThreadX で TraceX トレース バッファーを作成するためのイベント収集コードが有効になります。</span><span class="sxs-lookup"><span data-stu-id="997dd-218">When defined, ThreadX enables the event gathering code for creating a TraceX trace buffer.</span></span>

<span data-ttu-id="997dd-219">**TX_ENABLE_STACK_CHECKING**</span><span class="sxs-lookup"><span data-stu-id="997dd-219">**TX_ENABLE_STACK_CHECKING**</span></span>

<span data-ttu-id="997dd-220">定義されている場合、ThreadX ランタイム スタック チェックが有効になります。これには、スタック使用量の解析と、スタック領域の前後のデータ パターン "フェンス"の検査が含まれます。</span><span class="sxs-lookup"><span data-stu-id="997dd-220">When defined, enables ThreadX run-time stack checking, which includes analysis of how much stack has been used and examination of data pattern "fences" before and after the stack area.</span></span> <span data-ttu-id="997dd-221">スタック エラーが検出されると、登録されているアプリケーション スタック エラー ハンドラーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="997dd-221">If a stack error is detected, the registered application stack error handler is called.</span></span> <span data-ttu-id="997dd-222">このオプションにより、オーバーヘッドとコード サイズが若干増加します。</span><span class="sxs-lookup"><span data-stu-id="997dd-222">This option does result in slightly increased overhead and code size.</span></span> <span data-ttu-id="997dd-223">詳細については、***tx_thread_stack_error_notify*** API 関数を参照してください。</span><span class="sxs-lookup"><span data-stu-id="997dd-223">Review the ***tx_thread_stack_error_notify*** API function for more information.</span></span> <span data-ttu-id="997dd-224">既定では、このオプションは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="997dd-224">By default, this option is not defined.</span></span>

<span data-ttu-id="997dd-225">**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="997dd-225">**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="997dd-226">定義されている場合、イベント フラグ グループに関するパフォーマンス情報の収集が有効になります。</span><span class="sxs-lookup"><span data-stu-id="997dd-226">When defined, enables the gathering of performance information on event flags groups.</span></span> <span data-ttu-id="997dd-227">既定では、このオプションは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="997dd-227">By default, this option is not defined.</span></span>

<span data-ttu-id="997dd-228">**TX_INLINE_THREAD_RESUME_SUSPEND**</span><span class="sxs-lookup"><span data-stu-id="997dd-228">**TX_INLINE_THREAD_RESUME_SUSPEND**</span></span>

<span data-ttu-id="997dd-229">定義されている場合、ThreadX でインライン コードを介した ***tx_thread_resume** _ および _ *_tx_thread_suspend_** の API 呼び出しが向上します。</span><span class="sxs-lookup"><span data-stu-id="997dd-229">When defined, ThreadX improves the ***tx_thread_resume** _ and _ *_tx_thread_suspend_** API calls via in-line code.</span></span> <span data-ttu-id="997dd-230">これによりコード サイズが増えますが、これら 2 つの API 呼び出しのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="997dd-230">This increases code size but enhances performance of these two API calls.</span></span>

<span data-ttu-id="997dd-231">**TX_MAX_PRIORITIES**</span><span class="sxs-lookup"><span data-stu-id="997dd-231">**TX_MAX_PRIORITIES**</span></span>

<span data-ttu-id="997dd-232">ThreadX の優先度レベルを定義します。</span><span class="sxs-lookup"><span data-stu-id="997dd-232">Defines the priority levels for ThreadX.</span></span> <span data-ttu-id="997dd-233">有効な値は 32 から 1024 の範囲 (両端を含む) で、32 で均等に割り切れ "*なければなりません*"。</span><span class="sxs-lookup"><span data-stu-id="997dd-233">Legal values range from 32 through 1024 (inclusive) and *must* be evenly divisible by 32.</span></span> <span data-ttu-id="997dd-234">サポートされている優先度レベルの数を増やすと、優先度 を 32 上げるごとに RAM 使用量が 128 バイト増えます。</span><span class="sxs-lookup"><span data-stu-id="997dd-234">Increasing the number of priority levels supported increases the RAM usage by 128 bytes for every group of 32 priorities.</span></span> <span data-ttu-id="997dd-235">ただし、パフォーマンスへの影響はごくわずかです。</span><span class="sxs-lookup"><span data-stu-id="997dd-235">However, there is only a negligible effect on performance.</span></span> <span data-ttu-id="997dd-236">既定では、この値は 32 の優先度レベルに設定されます。</span><span class="sxs-lookup"><span data-stu-id="997dd-236">By default, this value is set to 32 priority levels.</span></span>

<span data-ttu-id="997dd-237">**TX_MINIMUM_STACK**</span><span class="sxs-lookup"><span data-stu-id="997dd-237">**TX_MINIMUM_STACK**</span></span>

<span data-ttu-id="997dd-238">最小スタック サイズ (バイト単位) を定義します。</span><span class="sxs-lookup"><span data-stu-id="997dd-238">Defines the minimum stack size (in bytes).</span></span> <span data-ttu-id="997dd-239">これは、スレッドが作成されるときのエラー チェックに使用されます。</span><span class="sxs-lookup"><span data-stu-id="997dd-239">It is used for error checking when threads are created.</span></span> <span data-ttu-id="997dd-240">既定値はポート固有であり、***tx_port.h*** にあります。</span><span class="sxs-lookup"><span data-stu-id="997dd-240">The default value is port-specific and is found in ***tx_port.h***.</span></span>

<span data-ttu-id="997dd-241">**TX_MISRA_ENABLE**</span><span class="sxs-lookup"><span data-stu-id="997dd-241">**TX_MISRA_ENABLE**</span></span>

<span data-ttu-id="997dd-242">定義されている場合、ThreadX が MISRA C 準拠規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="997dd-242">When defined, ThreadX utilizes MISRA C compliant conventions.</span></span> <span data-ttu-id="997dd-243">詳細については、***ThreadX_MISRA_Compliance.pdf*** を参照してください。</span><span class="sxs-lookup"><span data-stu-id="997dd-243">Refer to  ***ThreadX_MISRA_Compliance.pdf*** for details.</span></span>

<span data-ttu-id="997dd-244">**TX_MUTEX_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="997dd-244">**TX_MUTEX_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="997dd-245">定義されている場合、ミューテックスに関するパフォーマンス情報の収集が有効になります。</span><span class="sxs-lookup"><span data-stu-id="997dd-245">When defined, enables the gathering of performance information on mutexes.</span></span> <span data-ttu-id="997dd-246">既定では、このオプションは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="997dd-246">By default, this option is not defined.</span></span>

<span data-ttu-id="997dd-247">**TX_NO_TIMER**</span><span class="sxs-lookup"><span data-stu-id="997dd-247">**TX_NO_TIMER**</span></span>

<span data-ttu-id="997dd-248">定義されている場合、ThreadX タイマー ロジックが完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="997dd-248">When defined, the ThreadX timer logic is completely disabled.</span></span> <span data-ttu-id="997dd-249">これは、ThreadX のタイマー機能 (スレッド スリープ、API タイムアウト、タイムスライス、アプリケーション タイマー) を使用しない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="997dd-249">This is useful in cases where the ThreadX timer features (thread sleep, API timeouts, time-slicing, and application timers) are not utilized.</span></span> <span data-ttu-id="997dd-250">**TX_NO_TIMER** が指定されている場合は、オプション **TX_TIMER_PROCESS_IN_ISR** も定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="997dd-250">If **TX_NO_TIMER** is specified, the option **TX_TIMER_PROCESS_IN_ISR** must also be defined.</span></span>

<span data-ttu-id="997dd-251">**TX_NOT_INTERRUPTABLE**</span><span class="sxs-lookup"><span data-stu-id="997dd-251">**TX_NOT_INTERRUPTABLE**</span></span>

<span data-ttu-id="997dd-252">定義されている場合、ThreadX は割り込みロックアウト時間を最小に抑えようとしません。</span><span class="sxs-lookup"><span data-stu-id="997dd-252">When defined, ThreadX does not attempt to minimize interrupt lockout time.</span></span> <span data-ttu-id="997dd-253">この結果、実行速度が速くなりますが、割り込みロックアウト時間が若干長くなります。</span><span class="sxs-lookup"><span data-stu-id="997dd-253">This results in faster execution but does slightly increase interrupt lockout time.</span></span>

<span data-ttu-id="997dd-254">**TX_QUEUE_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="997dd-254">**TX_QUEUE_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="997dd-255">定義されている場合、キューに関するパフォーマンス情報の収集が有効になります。</span><span class="sxs-lookup"><span data-stu-id="997dd-255">When defined, enables the gathering of performance information on queues.</span></span> <span data-ttu-id="997dd-256">既定では、このオプションは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="997dd-256">By default, this option is not defined.</span></span>

<span data-ttu-id="997dd-257">**TX_REACTIVATE_INLINE**</span><span class="sxs-lookup"><span data-stu-id="997dd-257">**TX_REACTIVATE_INLINE**</span></span>

<span data-ttu-id="997dd-258">定義されている場合、関数呼び出しを使用する代わりに、ThreadX タイマーの再アクティブ化がインラインで実行されます。</span><span class="sxs-lookup"><span data-stu-id="997dd-258">When defined, performs reactivation of ThreadX timers inline instead of using a function call.</span></span> <span data-ttu-id="997dd-259">これによりパフォーマンスが向上しますが、コード サイズが若干増えます。</span><span class="sxs-lookup"><span data-stu-id="997dd-259">This improves performance but slightly increases code size.</span></span> <span data-ttu-id="997dd-260">既定では、このオプションは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="997dd-260">By default, this option is not defined.</span></span>

<span data-ttu-id="997dd-261">**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="997dd-261">**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="997dd-262">定義されている場合、セマフォに関するパフォーマンス情報の収集が有効になります。</span><span class="sxs-lookup"><span data-stu-id="997dd-262">When defined, enables the gathering of performance information on semaphores.</span></span> <span data-ttu-id="997dd-263">既定では、このオプションは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="997dd-263">By default, this option is not defined.</span></span>

<span data-ttu-id="997dd-264">**TX_THREAD_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="997dd-264">**TX_THREAD_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="997dd-265">定義されている場合、スレッドに関するパフォーマンス情報の収集が有効になります。</span><span class="sxs-lookup"><span data-stu-id="997dd-265">When defined, enables the gathering of performance information on threads.</span></span> <span data-ttu-id="997dd-266">既定では、このオプションは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="997dd-266">By default, this option is not defined.</span></span>

<span data-ttu-id="997dd-267">**TX_TIMER_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="997dd-267">**TX_TIMER_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="997dd-268">定義されている場合、タイマーに関するパフォーマンス情報の収集が有効になります。</span><span class="sxs-lookup"><span data-stu-id="997dd-268">When defined, enables the gathering of performance information on timers.</span></span> <span data-ttu-id="997dd-269">既定では、このオプションは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="997dd-269">By default, this option is not defined.</span></span>

<span data-ttu-id="997dd-270">**TX_TIMER_PROCESS_IN_ISR**</span><span class="sxs-lookup"><span data-stu-id="997dd-270">**TX_TIMER_PROCESS_IN_ISR**</span></span>

<span data-ttu-id="997dd-271">定義されている場合、ThreadX の内部システム タイマー スレッドは除去されます。</span><span class="sxs-lookup"><span data-stu-id="997dd-271">When defined, eliminates the internal system timer thread for ThreadX.</span></span> <span data-ttu-id="997dd-272">この結果、タイマー スタックと制御ブロックが不要になるため、タイマー イベントのパフォーマンスが向上し、RAM の要件が小さくなります。</span><span class="sxs-lookup"><span data-stu-id="997dd-272">This results in improved performance on timer events and smaller RAM requirements because the timer stack and control block are no longer needed.</span></span> <span data-ttu-id="997dd-273">ただし、このオプションを使用すると、タイマー期限切れ処理がすべてタイマー ISR レベルに移動します。</span><span class="sxs-lookup"><span data-stu-id="997dd-273">However, using this option moves all the timer expiration processing to the timer ISR level.</span></span> <span data-ttu-id="997dd-274">既定では、このオプションは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="997dd-274">By default, this option is not defined.</span></span>

> [!NOTE]
> <span data-ttu-id="997dd-275">*タイマーから許可されているサービスは ISR から許可されない可能性があるため、このオプションを使用していると許可されない場合があります。*</span><span class="sxs-lookup"><span data-stu-id="997dd-275">*Services allowed from timers may not be allowed from ISRs and thus might not be allowed when using this option.*</span></span>

<span data-ttu-id="997dd-276">**TX_TIMER_THREAD_PRIORITY**</span><span class="sxs-lookup"><span data-stu-id="997dd-276">**TX_TIMER_THREAD_PRIORITY**</span></span>

<span data-ttu-id="997dd-277">ThreadX の内部システム タイマー スレッドの優先度を定義します。</span><span class="sxs-lookup"><span data-stu-id="997dd-277">Defines the priority of the internal ThreadX system timer thread.</span></span> <span data-ttu-id="997dd-278">既定値は優先度 0 で、ThreadX で最も高い優先度です。</span><span class="sxs-lookup"><span data-stu-id="997dd-278">The default value is priority 0—the highest priority in ThreadX.</span></span> <span data-ttu-id="997dd-279">既定値は ***tx_port.h*** で定義されています。</span><span class="sxs-lookup"><span data-stu-id="997dd-279">The default value is defined in ***tx_port.h***.</span></span>

<span data-ttu-id="997dd-280">**TX_TIMER_THREAD_STACK_SIZE**</span><span class="sxs-lookup"><span data-stu-id="997dd-280">**TX_TIMER_THREAD_STACK_SIZE**</span></span>

<span data-ttu-id="997dd-281">ThreadX の内部システム タイマー スレッドのスタック サイズ (バイト単位) を定義します。</span><span class="sxs-lookup"><span data-stu-id="997dd-281">Defines the stack size (in bytes) of the internal ThreadX system timer thread.</span></span> <span data-ttu-id="997dd-282">このスレッドは、すべてのスレッド スリープ要求だけでなく、すべてのサービス呼び出しタイムアウトも処理します。</span><span class="sxs-lookup"><span data-stu-id="997dd-282">This thread processes all thread sleep requests as well as all service call timeouts.</span></span> <span data-ttu-id="997dd-283">さらに、すべてのアプリケーション タイマー コールバック ルーチンはこのコンテキストから呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="997dd-283">In addition, all application timer callback routines are invoked from this context.</span></span> <span data-ttu-id="997dd-284">既定値はポート固有であり、***tx_port.h*** にあります。</span><span class="sxs-lookup"><span data-stu-id="997dd-284">The default value is port-specific and is found in ***tx_port.h***.</span></span>

## <a name="threadx-version-id"></a><span data-ttu-id="997dd-285">ThreadX のバージョン ID</span><span class="sxs-lookup"><span data-stu-id="997dd-285">ThreadX Version ID</span></span>

<span data-ttu-id="997dd-286">プログラマーは \***tx_port.h** _ ファイルを調べることで ThreadX のバージョンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="997dd-286">The programmer can obtain the ThreadX version from examination of the \***tx_port.h** _ file.</span></span> <span data-ttu-id="997dd-287">加えて、このファイルには、対応するポートのバージョン履歴も含まれています。</span><span class="sxs-lookup"><span data-stu-id="997dd-287">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="997dd-288">アプリケーション ソフトウェアは、グローバル文字列 _*_tx_version_id*\* を調べることで ThreadX のバージョンを取得できます。</span><span class="sxs-lookup"><span data-stu-id="997dd-288">Application software can obtain the ThreadX version by examining the global string _\*_tx_version_id\*\*.</span></span>
