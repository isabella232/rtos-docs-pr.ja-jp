---
title: このガイドについて
description: このガイドでは、Microsoft のハイパフォーマンス組み込みリアルタイム カーネルである Azure RTOS ThreadX SMP に関する包括的な情報を提供します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2399666b5b4d7c34db50d539e200c90f06f7235f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810262"
---
# <a name="about-this-guide"></a><span data-ttu-id="bbb75-103">このガイドについて</span><span class="sxs-lookup"><span data-stu-id="bbb75-103">About This Guide</span></span>

<span data-ttu-id="bbb75-104">このガイドでは、Microsoft のハイパフォーマンス組み込みリアルタイム カーネルである Azure RTOS ThreadX SMP に関する包括的な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="bbb75-104">This guide provides comprehensive information about Azure RTOS ThreadX SMP, the Microsoft high-performance embedded real-time kernel.</span></span>

<span data-ttu-id="bbb75-105">これは、組み込みリアルタイム ソフトウェアの開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="bbb75-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="bbb75-106">開発者は、標準のリアルタイム オペレーティング システム関数および C プログラミング言語について理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbb75-106">The developer should be familiar with standard real-time operating system functions and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="bbb75-107">Organization</span><span class="sxs-lookup"><span data-stu-id="bbb75-107">Organization</span></span>

| <span data-ttu-id="bbb75-108">章</span><span class="sxs-lookup"><span data-stu-id="bbb75-108">Chapter</span></span>       | <span data-ttu-id="bbb75-109">概要</span><span class="sxs-lookup"><span data-stu-id="bbb75-109">Overview</span></span>                    |
| ------------- | ---------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="bbb75-110">**第 1 章**</span><span class="sxs-lookup"><span data-stu-id="bbb75-110">**Chapter 1**</span></span> | <span data-ttu-id="bbb75-111">ThreadX SMP の基本的な概要と、リアルタイム組み込み開発との関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="bbb75-111">Provides a basic overview of ThreadX SMP and its relationship to real-time embedded development.</span></span>           |
| <span data-ttu-id="bbb75-112">**第 2 章**</span><span class="sxs-lookup"><span data-stu-id="bbb75-112">**Chapter 2**</span></span> | <span data-ttu-id="bbb75-113">ThreadX SMP をインストールしてアプリケーションで "*すぐに使用する*" ための基本的な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="bbb75-113">Gives the basic steps to install and use ThreadX SMP in your application right *out of the box*.</span></span>           |
| <span data-ttu-id="bbb75-114">**第 3 章**</span><span class="sxs-lookup"><span data-stu-id="bbb75-114">**Chapter 3**</span></span> | <span data-ttu-id="bbb75-115">ハイパフォーマンス リアルタイム SMP カーネルである ThreadX SMP の機能動作について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="bbb75-115">Describes in detail the functional operation of ThreadX SMP, the high-performance real-time SMP kernel.</span></span>    |
| <span data-ttu-id="bbb75-116">**第 4 章**</span><span class="sxs-lookup"><span data-stu-id="bbb75-116">**Chapter 4**</span></span> | <span data-ttu-id="bbb75-117">ThreadX SMP に対するアプリケーションのインターフェイスについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="bbb75-117">Details the application’s interface to ThreadX SMP.</span></span>                                                        |
| <span data-ttu-id="bbb75-118">**第 5 章**</span><span class="sxs-lookup"><span data-stu-id="bbb75-118">**Chapter 5**</span></span> | <span data-ttu-id="bbb75-119">ThreadX SMP アプリケーション用の I/O ドライバーの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="bbb75-119">Describes writing I/O drivers for ThreadX SMP applications.</span></span>                                                |
| <span data-ttu-id="bbb75-120">**第 6 章**</span><span class="sxs-lookup"><span data-stu-id="bbb75-120">**Chapter 6**</span></span> | <span data-ttu-id="bbb75-121">すべての ThreadX SMP プロセッサ サポート パッケージに付属するデモンストレーション アプリケーションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bbb75-121">Describes the demonstration application that is supplied with every ThreadX SMP processor support package.</span></span> |
| <span data-ttu-id="bbb75-122">**付録 A:**</span><span class="sxs-lookup"><span data-stu-id="bbb75-122">**Appendix A**</span></span> | <span data-ttu-id="bbb75-123">ThreadX SMP の API</span><span class="sxs-lookup"><span data-stu-id="bbb75-123">ThreadX SMP API</span></span>        |
| <span data-ttu-id="bbb75-124">**付録 B**</span><span class="sxs-lookup"><span data-stu-id="bbb75-124">**Appendix B**</span></span> | <span data-ttu-id="bbb75-125">ThreadX SMP の定数</span><span class="sxs-lookup"><span data-stu-id="bbb75-125">ThreadX SMP constants</span></span>  |
| <span data-ttu-id="bbb75-126">**付録 C**</span><span class="sxs-lookup"><span data-stu-id="bbb75-126">**Appendix C**</span></span> | <span data-ttu-id="bbb75-127">ThreadX SMP のデータ型</span><span class="sxs-lookup"><span data-stu-id="bbb75-127">ThreadX SMP data types</span></span> |
| <span data-ttu-id="bbb75-128">**付録 D**</span><span class="sxs-lookup"><span data-stu-id="bbb75-128">**Appendix D**</span></span> | <span data-ttu-id="bbb75-129">ASCII チャート</span><span class="sxs-lookup"><span data-stu-id="bbb75-129">ASCII chart</span></span>            |

## <a name="guide-conventions"></a><span data-ttu-id="bbb75-130">ガイドの表記規則</span><span class="sxs-lookup"><span data-stu-id="bbb75-130">Guide Conventions</span></span>

- <span data-ttu-id="bbb75-131">"*斜体*" - "*この書体は、本のタイトルを表し、重要な単語を強調し、変数を示すために使用されています。* "</span><span class="sxs-lookup"><span data-stu-id="bbb75-131">*Italics* - *typeface denotes book titles, emphasizes important words, and indicates variables.*</span></span>
- <span data-ttu-id="bbb75-132">**太字** - **この書体は、ファイル名とキーワードを表し、重要な単語や変数をさらに強調するために使用されています。**</span><span class="sxs-lookup"><span data-stu-id="bbb75-132">**Boldface** - **typeface denotes file names, key words, and further emphasizes important words and variables.**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bbb75-133">情報記号は、パフォーマンスや機能に影響を与える可能性がある重要な情報や追加情報を示します。</span><span class="sxs-lookup"><span data-stu-id="bbb75-133">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

> [!WARNING]
> <span data-ttu-id="bbb75-134">警告記号は、致命的なエラーを引き起こす可能性があるために開発者が回避するように注意する必要がある状況を示します。</span><span class="sxs-lookup"><span data-stu-id="bbb75-134">Warning symbols draw attention to situations in which developers should take care to avoid because they could cause fatal errors.</span></span>

## <a name="threadx-smp-data-types"></a><span data-ttu-id="bbb75-135">ThreadX SMP のデータ型</span><span class="sxs-lookup"><span data-stu-id="bbb75-135">ThreadX SMP Data Types</span></span>

<span data-ttu-id="bbb75-136">カスタム ThreadX SMP 制御構造のデータ型に加えて、ThreadX SMP サービス呼び出しインターフェイスで使用される一連の特殊なデータ型があります。</span><span class="sxs-lookup"><span data-stu-id="bbb75-136">In addition to the custom ThreadX SMP control structure data types, there are a series of special data types that are used in ThreadX SMP service call interfaces.</span></span> <span data-ttu-id="bbb75-137">これらの特殊なデータ型は、基になる C コンパイラのデータ型に直接マップされます。</span><span class="sxs-lookup"><span data-stu-id="bbb75-137">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="bbb75-138">これは、異なる C コンパイラ間での移植性を確保するために行われます。</span><span class="sxs-lookup"><span data-stu-id="bbb75-138">This is done to insure portability between different C compilers.</span></span> <span data-ttu-id="bbb75-139">正確な実装は、ディストリビューション ディスクに含まれている ***tx_port.h*** ファイルで確認できます。</span><span class="sxs-lookup"><span data-stu-id="bbb75-139">The exact implementation can be found in the ***tx_port.h*** file included on the distribution disk.</span></span>

<span data-ttu-id="bbb75-140">次に示すのは、ThreadX SMP サービス呼び出しのデータ型とそれに関連付けられている意味の一覧です。</span><span class="sxs-lookup"><span data-stu-id="bbb75-140">The following is a list of ThreadX SMP service call data types and their associated meanings:</span></span>

| <span data-ttu-id="bbb75-141">データ型</span><span class="sxs-lookup"><span data-stu-id="bbb75-141">Data Type</span></span>          | <span data-ttu-id="bbb75-142">意味</span><span class="sxs-lookup"><span data-stu-id="bbb75-142">Meaning</span></span>                                                          |
| --------- | --------------------------------------------------------- |
| <span data-ttu-id="bbb75-143">**UINT**</span><span class="sxs-lookup"><span data-stu-id="bbb75-143">**UINT**</span></span>  | <span data-ttu-id="bbb75-144">基本的な符号なし整数。</span><span class="sxs-lookup"><span data-stu-id="bbb75-144">Basic unsigned integer.</span></span> <span data-ttu-id="bbb75-145">この型は、8 ビットの符号なしデータをサポートする必要があります。ただし、最も便利な符号なしデータ型にマップされます。</span><span class="sxs-lookup"><span data-stu-id="bbb75-145">This type must support 8-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="bbb75-146">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="bbb75-146">**ULONG**</span></span> | <span data-ttu-id="bbb75-147">符号なし long 型。</span><span class="sxs-lookup"><span data-stu-id="bbb75-147">Unsigned long type.</span></span> <span data-ttu-id="bbb75-148">この型は、32 ビットの符号なしデータをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbb75-148">This type must support 32-bit unsigned data.</span></span>                                                                     |
| <span data-ttu-id="bbb75-149">**VOID**</span><span class="sxs-lookup"><span data-stu-id="bbb75-149">**VOID**</span></span>  | <span data-ttu-id="bbb75-150">ほとんどの場合、コンパイラの void 型と同等です。</span><span class="sxs-lookup"><span data-stu-id="bbb75-150">Almost always equivalent to the compiler’s void type.</span></span>                                                                                |
| <span data-ttu-id="bbb75-151">**CHAR**</span><span class="sxs-lookup"><span data-stu-id="bbb75-151">**CHAR**</span></span>  | <span data-ttu-id="bbb75-152">ほとんどの場合、標準の 8 ビット文字型です。</span><span class="sxs-lookup"><span data-stu-id="bbb75-152">Most often a standard 8-bit character type.</span></span>                                                                                          |

<span data-ttu-id="bbb75-153">追加のデータ型は、ThreadX SMP ソース内で使用されます。</span><span class="sxs-lookup"><span data-stu-id="bbb75-153">Additional data types are used within the ThreadX SMP source.</span></span> <span data-ttu-id="bbb75-154">これらは、***tx_port.h*** ファイルにもあります。</span><span class="sxs-lookup"><span data-stu-id="bbb75-154">They are also located in the ***tx_port.h*** file.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="bbb75-155">カスタマー サポート センター</span><span class="sxs-lookup"><span data-stu-id="bbb75-155">Customer Support Center</span></span>

<span data-ttu-id="bbb75-156">サポート メール アドレス: [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) Web ページ: azure.com/rtos</span><span class="sxs-lookup"><span data-stu-id="bbb75-156">Support email: [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) Web page: azure.com/rtos</span></span>

### <a name="latest-product-information"></a><span data-ttu-id="bbb75-157">最新の製品情報</span><span class="sxs-lookup"><span data-stu-id="bbb75-157">Latest Product Information</span></span>

<span data-ttu-id="bbb75-158">azure.com/rtos Web サイトにアクセスし、[サポート] メニュー オプションを選択して、最新の ThreadX SMP 製品リリースに関する情報など、最新のオンライン サポート情報を検索します。</span><span class="sxs-lookup"><span data-stu-id="bbb75-158">Visit the azure.com/rtos web site and select the “Support” menu option to find the latest online support information, including information about the latest ThreadX SMP product releases.</span></span>

### <a name="what-we-need-from-you"></a><span data-ttu-id="bbb75-159">必要なもの</span><span class="sxs-lookup"><span data-stu-id="bbb75-159">What We Need From You</span></span>

<span data-ttu-id="bbb75-160">お客様のサポート リクエストをより効率的に解決できるように、次の情報を電子メールでお知らせください。</span><span class="sxs-lookup"><span data-stu-id="bbb75-160">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="bbb75-161">問題の詳しい説明。発生頻度や、確実に再現できるかどうかなど。</span><span class="sxs-lookup"><span data-stu-id="bbb75-161">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="bbb75-162">問題が発生する前にアプリケーションや ThreadX SMP に加えた変更の詳しい説明。</span><span class="sxs-lookup"><span data-stu-id="bbb75-162">A detailed description of any changes to the application and/or ThreadX SMP that preceded the problem.</span></span>
3. <span data-ttu-id="bbb75-163">ご自身のディストリビューションの _ *_tx_port.h_*\* ファイル内の \* **_tx_version_id** _ 文字列の内容。</span><span class="sxs-lookup"><span data-stu-id="bbb75-163">The contents of the ***_tx_version_id** _ string found in the _ *_tx_port.h_** file of your distribution.</span></span> <span data-ttu-id="bbb75-164">この文字列から、実行時環境に関する重要な情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="bbb75-164">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="bbb75-165">***_tx_build_options*** ULONG 変数の RAM の内容。</span><span class="sxs-lookup"><span data-stu-id="bbb75-165">The contents in RAM of the ***_tx_build_options*** ULONG variable.</span></span> <span data-ttu-id="bbb75-166">この変数から、ThreadX SMP ライブラリの構築方法に関する情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="bbb75-166">This variable will give us information on how your ThreadX SMP library was built.</span></span>

### <a name="where-to-send-comments-about-this-guide"></a><span data-ttu-id="bbb75-167">このガイドに関するご意見の送信先</span><span class="sxs-lookup"><span data-stu-id="bbb75-167">Where to Send Comments About This Guide</span></span>

<span data-ttu-id="bbb75-168">ご意見やご提案は、カスタマー サポート センター ([azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com)) まで電子メールにてお寄せください。その際、件名に "ThreadX SMP ユーザー ガイド" を含めてください。</span><span class="sxs-lookup"><span data-stu-id="bbb75-168">Email any comments and suggestions to the Customer Support Center at [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) Enter “ThreadX SMP User Guide” in the subject line.</span></span>
