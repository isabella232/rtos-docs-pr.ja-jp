---
title: 第 2 章 - GUIX のインストールと使用
description: この章では、高パフォーマンス ユーザー インターフェイス製品 GUIX のインストール、設定、および使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6527227062fc667b3f527a798d6621914c374c5c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811207"
---
# <a name="chapter-2---installation-and-use-of-guix"></a><span data-ttu-id="e624f-103">第 2 章 - GUIX のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="e624f-103">Chapter 2 - Installation and Use of GUIX</span></span>

<span data-ttu-id="e624f-104">この章では、高パフォーマンス ユーザー インターフェイス製品 GUIX のインストール、設定、および使用に関連するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="e624f-104">This chapter contains a description of various issues related to installation, setup, and use of the highperformance user interface product GUIX.</span></span>  

## <a name="host-considerations"></a><span data-ttu-id="e624f-105">ホストに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="e624f-105">Host Considerations</span></span>

<span data-ttu-id="e624f-106">埋め込み開発は、通常、Windows または Linux (Unix) ホスト コンピューターで行われます。</span><span class="sxs-lookup"><span data-stu-id="e624f-106">Embedded development is usually performed on Windows or Linux (Unix) host computers.</span></span> <span data-ttu-id="e624f-107">アプリケーションはコンパイルおよびリンクされた後、ホスト上に実行可能ファイルが生成され、実行のためにターゲット ハードウェアにダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="e624f-107">After the application is compiled, linked, and the executable is generated on the host, it is downloaded to the target hardware for execution.</span></span>

<span data-ttu-id="e624f-108">通常、ターゲットのダウンロードは、開発ツールのデバッガー内から実行されます。</span><span class="sxs-lookup"><span data-stu-id="e624f-108">Usually the target download is done from within the development tool's debugger.</span></span> <span data-ttu-id="e624f-109">ダウンロード後、デバッガーは、メモリおよびプロセッサ レジスタへのアクセスだけでなく、ターゲットの実行制御 (移動、停止、ブレークポイントなど) を提供します。</span><span class="sxs-lookup"><span data-stu-id="e624f-109">After download, the debugger is responsible for providing target execution control (go, halt, breakpoint, etc.) as well as access to memory and processor registers.</span></span>

<span data-ttu-id="e624f-110">開発ツール デバッガーのほとんどが、JTAG (IEEE 1149.1) やバックグラウンド デバッグ モード (BDM) などのオンチップ デバッグ (OCD) 接続を介してターゲット ハードウェアと通信します。</span><span class="sxs-lookup"><span data-stu-id="e624f-110">Most development tool debuggers communicate with the target hardware via on-chip debug (OCD) connections such as JTAG (IEEE 1149.1) and Background Debug Mode (BDM).</span></span> <span data-ttu-id="e624f-111">また、デバッガーは、インサーキット エミュレーション (ICE) 接続を使用してターゲット ハードウェアと通信することもあります。</span><span class="sxs-lookup"><span data-stu-id="e624f-111">Debuggers also communicate with target hardware through In-Circuit Emulation (ICE) connections.</span></span> <span data-ttu-id="e624f-112">OCD 接続と ICE 接続はどちらも、ターゲットの常駐ソフトウェアへの侵入を最小限に抑えた堅牢なソリューションを提供します。</span><span class="sxs-lookup"><span data-stu-id="e624f-112">Both OCD and ICE connections provide robust solutions with minimal intrusion on the target resident software.</span></span>

<span data-ttu-id="e624f-113">ホスト上で使用されるリソースについては、GUIX のソースコードは ASCII 形式で提供され、ホスト コンピューターのハード ディスク上に約 30 MB の空き領域が必要です。</span><span class="sxs-lookup"><span data-stu-id="e624f-113">As for resources used on the host, the source code for GUXI is delivered in ASCII format and requires approximately 30 Mbytes of space on the host computer’s hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="e624f-114">ターゲットに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="e624f-114">Target Considerations</span></span>

<span data-ttu-id="e624f-115">GUIX は、ターゲット上に 5 KB から 80 KB の読み取り専用メモリ (ROM) を必要とします。</span><span class="sxs-lookup"><span data-stu-id="e624f-115">GUIX requires between 5 KBytes and 80 Kbytes of Read-Only Memory (ROM) on the target.</span></span> <span data-ttu-id="e624f-116">また、GUIX スレッド スタックおよびその他のグローバル データ構造用に、ターゲットのランダム アクセス メモリ (RAM) がさらに 5 KB から 10 KB 必要です。</span><span class="sxs-lookup"><span data-stu-id="e624f-116">Another 5 to 10KBytes of the target’s Random Access Memory (RAM) are required for the GUIX thread stack and other global data structures.</span></span>

<span data-ttu-id="e624f-117">さらに、GUIX では、ThreadX タイマーと ThreadX ミューテックス オブジェクトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e624f-117">In addition, GUIX requires the use of a ThreadX timer and a ThreadX mutex object.</span></span> <span data-ttu-id="e624f-118">これらの機能は、GUIX 内の定期的な処理のニーズとスレッド保護に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e624f-118">These facilities are used for periodic processing needs and thread protection inside GUIX.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="e624f-119">製品の配布</span><span class="sxs-lookup"><span data-stu-id="e624f-119">Product Distribution</span></span>

<span data-ttu-id="e624f-120">Azure RTOS GUIX は、<https://github.com/azure-rtos/guix/> のパブリック ソース コード リポジトリから入手できます。</span><span class="sxs-lookup"><span data-stu-id="e624f-120">Azure RTOS GUIX can be obtained from our public source code repository at <https://github.com/azure-rtos/guix/>.</span></span>

<span data-ttu-id="e624f-121">ほとんどの製品配布に共通する重要ファイルの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e624f-121">The following is a list of the important files common to most product distributions:</span></span>

| <span data-ttu-id="e624f-122">ファイル名&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="e624f-122">Filename&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></span>| <span data-ttu-id="e624f-123">説明</span><span class="sxs-lookup"><span data-stu-id="e624f-123">Description</span></span>   |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="e624f-124">gx_api.h</span><span class="sxs-lookup"><span data-stu-id="e624f-124">gx_api.h</span></span>        | <span data-ttu-id="e624f-125">この C ヘッダー ファイルには、すべてのシステム等価物、データ構造、およびサービス プロトタイプが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e624f-125">This C header file contains all system equates, data structures, and service prototypes.</span></span> |
| <span data-ttu-id="e624f-126">gx_port.h</span><span class="sxs-lookup"><span data-stu-id="e624f-126">gx_port.h</span></span>       | <span data-ttu-id="e624f-127">この C ヘッダー ファイルには、ターゲット固有および開発ツール固有のすべてのデータ定義とデータ構造が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e624f-127">This C header file contains all target-specific and development tool-specific data definitions and structures.</span></span>                                                                                                                                         |
| <span data-ttu-id="e624f-128">gx.a (または gx.lib)</span><span class="sxs-lookup"><span data-stu-id="e624f-128">gx.a (or gx.lib)</span></span> | <span data-ttu-id="e624f-129">これは、GUIX C ライブラリのバイナリ バージョンです。</span><span class="sxs-lookup"><span data-stu-id="e624f-129">This is the binary version of the GUIX C library.</span></span> <span data-ttu-id="e624f-130">これは、通常、提供されている GUIX ライブラリのソース ファイルをコンパイルおよびアーカイブすることで構築されます。ただし、お使いのハードウェア ターゲットおよびライセンスの種類によっては、このライブラリは、事前構築済みフォームで提供される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e624f-130">This is normally built by compiling and archiving the provided GUIX library source files, however this library may be provided in pre-built form depending on your hardware target and license type.</span></span> |
|

> [!IMPORTANT]
> <span data-ttu-id="e624f-131">*すべてのファイルが小文字であるため、コマンドは容易に Linux (Unix) 開発プラットフォームに簡単に変換できます。*</span><span class="sxs-lookup"><span data-stu-id="e624f-131">*All files are in lower-case, making it easy to convert the commands to Linux (Unix) development platforms.*</span></span>

## <a name="guix-installation"></a><span data-ttu-id="e624f-132">GUIX のインストール</span><span class="sxs-lookup"><span data-stu-id="e624f-132">GUIX Installation</span></span>

<span data-ttu-id="e624f-133">GUIX は、GitHub リポジトリをローカル コンピューターに複製することによってインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e624f-133">GUIX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="e624f-134">お使いの PC 上に GUIX リポジトリの複製を作成するための一般的な構文を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e624f-134">The following is typical syntax for creating a clone of the GUIX repository on your PC:</span></span>

```c
    git clone https://github.com/azure-rtos/guix
```

<span data-ttu-id="e624f-135">GitHub メイン ページ上のダウンロード ボタンを使用して、リポジトリのコピーをダウンロードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="e624f-135">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="e624f-136">また、オンライン リポジトリのフロント ページ上で GUIX ライブラリを構築する手順も紹介します。</span><span class="sxs-lookup"><span data-stu-id="e624f-136">You will also find instructions for building the GUIX library on the front page of the online repository.</span></span>

>[!NOTE]  
> <span data-ttu-id="e624f-137">*アプリケーション ソフトウェアは、通常 **gx.a** (または **gx.lib**) と呼ばれる GUIX ライブラリ ファイルと、C インクルード ファイル **gx_api.h** および **gx_port.h** にアクセスする必要があります。これを行うには、開発ツールの適切なパスを設定するか、これらのファイルをアプリケーション開発領域にコピーします。*</span><span class="sxs-lookup"><span data-stu-id="e624f-137">*Application software needs access to the GUIX library file, usually called **gx.a** (or **gx.lib**), and the C include files **gx_api.h** and **gx_port.h**. This is accomplished either by setting the appropriate path for the development tools or by copying these files into the application development area.*</span></span>

## <a name="using-guix"></a><span data-ttu-id="e624f-138">GUIX の使用</span><span class="sxs-lookup"><span data-stu-id="e624f-138">Using GUIX</span></span>

<span data-ttu-id="e624f-139">GUIX の使い方は簡単です。</span><span class="sxs-lookup"><span data-stu-id="e624f-139">Using GUIX is easy.</span></span> <span data-ttu-id="e624f-140">基本的に、コンパイル中にアプリケーション コードに ***gx_api.h** を追加し、GUIX ライブラリ _*_gx.a_\*_ (または _ \*_gx.lib_\*\*) とリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e624f-140">Basically, the application code must include ***gx_api.h** _ during compilation and link with the GUIX library _*_gx.a_*_ (or _ *_gx.lib_*)*.</span></span>

<span data-ttu-id="e624f-141">GUIX アプリケーションをビルドするには、次の 4 つの簡単な手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="e624f-141">There are four easy steps required to build a GUIX application:</span></span>

| <span data-ttu-id="e624f-142">手順</span><span class="sxs-lookup"><span data-stu-id="e624f-142">Steps</span></span>   | <span data-ttu-id="e624f-143">説明</span><span class="sxs-lookup"><span data-stu-id="e624f-143">Description</span></span>    |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="e624f-144">手順&nbsp;1:</span><span class="sxs-lookup"><span data-stu-id="e624f-144">Step&nbsp;1:</span></span> | <span data-ttu-id="e624f-145">***gx_api.h*** ファイルを、GUIX サービスまたはデータ構造を使用するすべてのアプリケーション ファイル内に追加します。</span><span class="sxs-lookup"><span data-stu-id="e624f-145">Include the ***gx_api.h*** file in all application files that use GUIX services or data structures.</span></span>                                                               |
| <span data-ttu-id="e624f-146">手順&nbsp;2:</span><span class="sxs-lookup"><span data-stu-id="e624f-146">Step&nbsp;2:</span></span> | <span data-ttu-id="e624f-147">_ *_tx_application_define_*\* 関数またはアプリケーション スレッドから \***gx_system_initialize** _ を呼び出して、GUIX システムを初期化します。</span><span class="sxs-lookup"><span data-stu-id="e624f-147">Initialize the GUIX system by calling ***gx_system_initialize** _ from the _ *_tx_application_define_** function or an application thread.</span></span>                       |
| <span data-ttu-id="e624f-148">手順&nbsp;3:</span><span class="sxs-lookup"><span data-stu-id="e624f-148">Step&nbsp;3:</span></span> | <span data-ttu-id="e624f-149">表示インスタンスを作成し、ディスプレイのキャンバスを作成して、ルート ウィンドウおよびその他の必要なウィンドウまたはウィジェットを作成します。</span><span class="sxs-lookup"><span data-stu-id="e624f-149">Create a display instance, create a canvas for the display, and create the root window and any other windows or widgets necessary.</span></span>                                 |
| <span data-ttu-id="e624f-150">手順&nbsp;4:</span><span class="sxs-lookup"><span data-stu-id="e624f-150">Step&nbsp;4:</span></span> | <span data-ttu-id="e624f-151">アプリケーション ソースをコンパイルし、GUIX ランタイム ライブラリ ***gx. a** _ (または _*_gx.lib_\*\*) とリンクします。</span><span class="sxs-lookup"><span data-stu-id="e624f-151">Compile application source and link with the GUIX runtime library ***gx.a** _ (or _*_gx.lib_\*\*).</span></span> <span data-ttu-id="e624f-152">結果のイメージはターゲットにダウンロードして、実行できます。</span><span class="sxs-lookup"><span data-stu-id="e624f-152">The resulting image can be downloaded to the target and executed!</span></span> |

## <a name="troubleshooting"></a><span data-ttu-id="e624f-153">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e624f-153">Troubleshooting</span></span>

<span data-ttu-id="e624f-154">各 GUIX ポートには、特定のディスプレイ ハードウェア上で実行されるデモンストレーション アプリケーションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e624f-154">Each GUIX port is delivered with a demonstration application that executes on specific display hardware.</span></span> <span data-ttu-id="e624f-155">どのバージョンの GUIX でも、用意されている基本デモンストレーションは同じです。</span><span class="sxs-lookup"><span data-stu-id="e624f-155">The same basic demonstration is delivered with all versions of GUIX.</span></span> <span data-ttu-id="e624f-156">最初にデモンストレーション システムを実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e624f-156">It is always a good idea to get the demonstration system running first.</span></span>

<span data-ttu-id="e624f-157">デモンストレーション システムが正常に実行されない場合は、次の操作を行って、問題を絞り込んでください。</span><span class="sxs-lookup"><span data-stu-id="e624f-157">If the demonstration system does not run properly, perform the following operations to narrow the problem:</span></span>

1. <span data-ttu-id="e624f-158">実行中のデモンストレーションの量を確認します。</span><span class="sxs-lookup"><span data-stu-id="e624f-158">Determine how much of the demonstration is running.</span></span>

2. <span data-ttu-id="e624f-159">コンパイル時の定数 **GX_THREAD_STACK_SIZE** を変更し、GUIX ライブラリを再コンパイルして、GUIX スレッドのスタック サイズを増やします</span><span class="sxs-lookup"><span data-stu-id="e624f-159">Increase the stack size of the GUIX thread by changing the  compile-time constant **GX_THREAD_STACK_SIZE** and recompiling  the GUIX library</span></span>

3. <span data-ttu-id="e624f-160">[構成オプション] セクションに一覧表示されている適切なデバッグ オプションを使用して、GUIX ライブラリを再コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="e624f-160">Recompile the GUIX library with the appropriate debug options listed  in the configuration option section.</span></span>

4. <span data-ttu-id="e624f-161">すべての API 呼び出しからリターン状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="e624f-161">Examine the return status from all API calls.</span></span>

5. <span data-ttu-id="e624f-162">関数 ***_gx_system_error_process*** にブレークポイントを設定して、内部システム エラーが発生していないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="e624f-162">Determine if there is an internal system error by setting a breakpoint at the function ***_gx_system_error_process***.</span></span> <span data-ttu-id="e624f-163">エラー コードと呼び出し元に、問題の原因に関する手掛かりがあるはずです。</span><span class="sxs-lookup"><span data-stu-id="e624f-163">There error code and caller should give clues as to what might be going wrong.</span></span>

6. <span data-ttu-id="e624f-164">最近の変更を一時的にバイパスして、問題が解消または変更するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="e624f-164">Temporarily bypass any recent changes to see if the problem disappears or changes.</span></span> <span data-ttu-id="e624f-165">このような情報は、Microsoft サポート エンジニアにとって有益です。</span><span class="sxs-lookup"><span data-stu-id="e624f-165">Such information should prove useful to Microsoft support engineers.</span></span>

<span data-ttu-id="e624f-166">トラブルシューティング手順で収集した情報を送信するには、「必要なもの」セクションに記載されている手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="e624f-166">Follow the procedures outlined in the section titled “What We Need From You” to send the information gathered from the troubleshooting steps.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="e624f-167">構成オプション</span><span class="sxs-lookup"><span data-stu-id="e624f-167">Configuration Options</span></span>

<span data-ttu-id="e624f-168">GUIX を使用して GUIX ライブラリとアプリケーションを構築する場合、構成オプションがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="e624f-168">There are several configuration options when building the GUIX library and the application using GUIX.</span></span> <span data-ttu-id="e624f-169">これらのオプションは、ご自身のアプリケーション要件に合わせてライブラリ サイズと機能セットを調整するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e624f-169">These options are used to tune the library size and feature set to best fit your application requirements.</span></span> <span data-ttu-id="e624f-170">たとえば、ご自身のアプリケーションの 1 つのスレッドのみが GUIX API サービスを利用する場合、構成フラグ **GX_DISABLE_MULTITHREAD_SUPPORT** は、複数のスレッドによるプリエンプションからの重要なコード セクション保護に伴うオーバーヘッドを排除するよう定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e624f-170">For example, if your application will have only one thread utilizing the GUIX API services, the configuration flag **GX_DISABLE_MULTITHREAD_SUPPORT** should be defined to eliminate the overhead associated with protecting critical code sections from pre-emption by multiple threads.</span></span> <span data-ttu-id="e624f-171">さまざまな構成フラグを、アプリケーション ソース内、コマンド ライン上、または **_gx_user.h_** インクルード ファイル内で定義できます。</span><span class="sxs-lookup"><span data-stu-id="e624f-171">The various configuration flags can be defined in the application source, on the command line, or within the **_gx_user.h_** include file.</span></span>

<span data-ttu-id="e624f-172">GUIX ライブラリ構成フラグが変更された場合は必ず、GUIX ライブラリとお使いのアプリケーション モジュールの両方をリビルドして、構成の変更を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e624f-172">Whenever the GUIX library configuration flags are modified, it is required to rebuild both the GUIX library and your application modules for the configuration changes to take effect.</span></span>

<span data-ttu-id="e624f-173">構成フラグの完全な一覧については、「付録 H: GUIX のビルド時の構成フラグ」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e624f-173">The complete list of configuration flags is documented in Appendix H: GUIX Build-Time Configuration Flags.</span></span>

## <a name="guix-version-id"></a><span data-ttu-id="e624f-174">GUIX バージョン ID</span><span class="sxs-lookup"><span data-stu-id="e624f-174">GUIX Version ID</span></span>

<span data-ttu-id="e624f-175">現在使用している GUIX のバージョンは、実行時にユーザーとアプリケーション ソフトウェアのどちらからでも確認できます。</span><span class="sxs-lookup"><span data-stu-id="e624f-175">The current version of GUIX is available to both the user and the application software during runtime.</span></span> <span data-ttu-id="e624f-176">プログラマーは \***gx_port.h** _ ファイルを調べることで GUIX のバージョンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e624f-176">The programmer can obtain the GUIX version from examination of the \***gx_port.h** _ file.</span></span> <span data-ttu-id="e624f-177">さらに、このファイルには、対応するポートのバージョン履歴も含まれています。アプリケーション ソフトウェアで GUIX バージョンを取得するには、_*_gx_port.h_*\* 内のグローバル文字列 _ \*_ _gx_version_id_\* _ を確認します。</span><span class="sxs-lookup"><span data-stu-id="e624f-177">In addition, this file also contains a version history of the corresponding port Application software can obtain the GUIX version by examining the global string _ *_ _gx_version_id_* _ in _\*_gx_port.h_\*\*.</span></span>

<span data-ttu-id="e624f-178">また、***gx_api.h*** 内で定義されている以下に示す定数から、アプリケーション ソフトウェアによってリリース情報を取得することもできます。これらの定数は、現在の製品リリースを、名前と製品のメジャー バージョンとマイナー バージョンによって特定します。</span><span class="sxs-lookup"><span data-stu-id="e624f-178">Application software can also obtain release information from the constants shown below defined in \***gx_api.h**.\* These constants identify the current product release by name and the product major and minor version.</span></span>

```C
#define __PRODUCT_GUIX__

#define __GUIX_MAJOR_VERSION__

#define __GUIX_MINOR_VERSION__
```
