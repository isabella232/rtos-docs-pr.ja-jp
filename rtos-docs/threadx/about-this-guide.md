---
title: Azure RTOS ThreadX に関するガイド
description: このガイドでは、Microsoft のハイパフォーマンス リアルタイム カーネルである Azure RTOS ThreadX に関する包括的な情報を提供します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ad9f782942bcdbb2dc49a9c841d865d97bcb1d4e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811408"
---
# <a name="about-the-azure-rtos-threadx-guide"></a><span data-ttu-id="0630d-103">Azure RTOS ThreadX に関するガイド</span><span class="sxs-lookup"><span data-stu-id="0630d-103">About the Azure RTOS ThreadX Guide</span></span>

<span data-ttu-id="0630d-104">このガイドでは、Microsoft のハイパフォーマンス リアルタイム カーネルである Azure RTOS ThreadX に関する包括的な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="0630d-104">This guide provides comprehensive information about Azure RTOS ThreadX, the Microsoft high-performance real-time kernel.</span></span> 

<span data-ttu-id="0630d-105">これは、組み込みリアルタイム ソフトウェアの開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="0630d-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="0630d-106">開発者は、標準のリアルタイム オペレーティング システム関数および C プログラミング言語について理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="0630d-106">The developer should be familiar with standard real-time operating system functions and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="0630d-107">Organization</span><span class="sxs-lookup"><span data-stu-id="0630d-107">Organization</span></span>

<span data-ttu-id="0630d-108">[第 1 章](chapter1.md) - Azure RTOS ThreadX の基本的な概要と、リアルタイム組み込み開発との関係について説明します</span><span class="sxs-lookup"><span data-stu-id="0630d-108">[Chapter 1](chapter1.md) - Provides a basic overview of Azure RTOS ThreadX and its relationship to real-time embedded development</span></span>

<span data-ttu-id="0630d-109">[第 2 章](chapter2.md) - Azure RTOS ThreadX をインストールしてアプリケーションで "*すぐに使用する*" ための基本的な手順について説明します</span><span class="sxs-lookup"><span data-stu-id="0630d-109">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS ThreadX in your application right *out of the box*</span></span>

<span data-ttu-id="0630d-110">[第 3 章](chapter3.md) - ハイパフォーマンス リアルタイム カーネルである Azure RTOS ThreadX の機能動作について詳しく説明します</span><span class="sxs-lookup"><span data-stu-id="0630d-110">[Chapter 3](chapter3.md) - Describes in detail the functional operation of Azure RTOS ThreadX, the high performance real-time kernel</span></span>

<span data-ttu-id="0630d-111">[第 4 章](chapter4.md) - Azure RTOS ThreadX に対するアプリケーションのインターフェイスについて詳しく説明します</span><span class="sxs-lookup"><span data-stu-id="0630d-111">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS ThreadX</span></span>

<span data-ttu-id="0630d-112">[第 5 章](chapter5.md) - Azure RTOS ThreadX アプリケーション用の I/O ドライバーの作成について説明します</span><span class="sxs-lookup"><span data-stu-id="0630d-112">[Chapter 5](chapter5.md) - Describes writing I/O drivers for Azure RTOS ThreadX applications</span></span>

<span data-ttu-id="0630d-113">[第 6 章](chapter6.md) - すべての Azure RTOS ThreadX プロセッサ サポート パッケージに付属するデモンストレーション アプリケーションについて説明します</span><span class="sxs-lookup"><span data-stu-id="0630d-113">[Chapter 6](chapter6.md) - Describes the demonstration application that is supplied with every Azure RTOS ThreadX processor support package</span></span>

<span data-ttu-id="0630d-114">[付録 A](appendix-a.md) - Azure RTOS ThreadX API</span><span class="sxs-lookup"><span data-stu-id="0630d-114">[Appendix A](appendix-a.md) - Azure RTOS ThreadX API</span></span>

<span data-ttu-id="0630d-115">[付録 B](appendix-b.md) - Azure RTOS ThreadX の定数</span><span class="sxs-lookup"><span data-stu-id="0630d-115">[Appendix B](appendix-b.md) - Azure RTOS ThreadX constants</span></span>

<span data-ttu-id="0630d-116">[付録 C](appendix-c.md) - Azure RTOS ThreadX のデータ型</span><span class="sxs-lookup"><span data-stu-id="0630d-116">[Appendix C](appendix-c.md) - Azure RTOS ThreadX data types</span></span>

<span data-ttu-id="0630d-117">[付録 D](appendix-d.md) - ASCII チャート</span><span class="sxs-lookup"><span data-stu-id="0630d-117">[Appendix D](appendix-d.md) - ASCII chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="0630d-118">ガイドの表記規則</span><span class="sxs-lookup"><span data-stu-id="0630d-118">Guide Conventions</span></span>

<span data-ttu-id="0630d-119">"*斜体*" - この書体は、本のタイトルを表し、重要な単語を強調し、パラメーターを示すために使用されています。</span><span class="sxs-lookup"><span data-stu-id="0630d-119">*Italics* - typeface denotes book titles, emphasizes important words, and indicates parameters.</span></span>

<span data-ttu-id="0630d-120">**太字** - この書体は、キーワード、定数、型名、ユーザー インターフェイス要素、変数名を表し、重要な単語をさらに強調するために使用されています。</span><span class="sxs-lookup"><span data-stu-id="0630d-120">**Boldface** - typeface denotes key words, constants, type names, user interface elements, variable names, and further emphasizes important words.</span></span>

<span data-ttu-id="0630d-121">***斜体かつ太字*** - この書体は、ファイル名と関数名を表すために使用されています。</span><span class="sxs-lookup"><span data-stu-id="0630d-121">***Italics and Boldface*** - typeface denotes file names and function names.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0630d-122">情報記号は、パフォーマンスや機能に影響を与える可能性がある重要な情報や追加情報を示します。</span><span class="sxs-lookup"><span data-stu-id="0630d-122">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

> [!WARNING]
> <span data-ttu-id="0630d-123">警告記号は、致命的なエラーを引き起こす可能性があるために開発者が回避するように注意する必要がある状況を示します。</span><span class="sxs-lookup"><span data-stu-id="0630d-123">Warning symbols draw attention to situations in which developers should take care to avoid because they could cause fatal errors.</span></span>

## <a name="azure-rtos-threadx-data-types"></a><span data-ttu-id="0630d-124">Azure RTOS ThreadX のデータ型</span><span class="sxs-lookup"><span data-stu-id="0630d-124">Azure RTOS ThreadX Data Types</span></span>

<span data-ttu-id="0630d-125">カスタムの Azure RTOS ThreadX 制御構造データ型に加えて、Azure RTOS ThreadX サービス呼び出しインターフェイスで使用される一連の特殊なデータ型があります。</span><span class="sxs-lookup"><span data-stu-id="0630d-125">In addition to the custom Azure RTOS ThreadX control structure data types, there are a series of special data types that are used in Azure RTOS ThreadX service call interfaces.</span></span> <span data-ttu-id="0630d-126">これらの特殊データ型は、基になる C コンパイラのデータ型に直接マップされます。</span><span class="sxs-lookup"><span data-stu-id="0630d-126">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="0630d-127">これは、異なる C コンパイラ間での移植性を確保するために行われます。</span><span class="sxs-lookup"><span data-stu-id="0630d-127">This is done to insure portability between different C compilers.</span></span> <span data-ttu-id="0630d-128">正確な実装は、ソースに含まれている ***tx_port.h*** ファイルで確認できます。</span><span class="sxs-lookup"><span data-stu-id="0630d-128">The exact implementation can be found in the ***tx_port.h*** file included with the source.</span></span>

<span data-ttu-id="0630d-129">Azure RTOS ThreadX サービス呼び出しのデータ型と、それらに関連付けられている意味の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0630d-129">The following is a list of Azure RTOS ThreadX service call data types and their associated meanings:</span></span>

| <span data-ttu-id="0630d-130">データ型</span><span class="sxs-lookup"><span data-stu-id="0630d-130">Data type</span></span>  | <span data-ttu-id="0630d-131">説明</span><span class="sxs-lookup"><span data-stu-id="0630d-131">Description</span></span> |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="0630d-132">**UINT**</span><span class="sxs-lookup"><span data-stu-id="0630d-132">**UINT**</span></span> | <span data-ttu-id="0630d-133">基本的な符号なし整数。</span><span class="sxs-lookup"><span data-stu-id="0630d-133">Basic unsigned integer.</span></span> <span data-ttu-id="0630d-134">この型は、8 ビットの符号なしデータをサポートする必要があります。ただし、最も便利な符号なしデータ型にマップされます。</span><span class="sxs-lookup"><span data-stu-id="0630d-134">This type must support 8-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="0630d-135">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="0630d-135">**ULONG**</span></span> | <span data-ttu-id="0630d-136">符号なし long 型。</span><span class="sxs-lookup"><span data-stu-id="0630d-136">Unsigned long type.</span></span> <span data-ttu-id="0630d-137">この型は、32 ビットの符号なしデータをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0630d-137">This type must support 32-bit unsigned data.</span></span> |
| <span data-ttu-id="0630d-138">**VOID**</span><span class="sxs-lookup"><span data-stu-id="0630d-138">**VOID**</span></span> | <span data-ttu-id="0630d-139">ほとんどの場合、コンパイラの void 型と同等です。</span><span class="sxs-lookup"><span data-stu-id="0630d-139">Almost always equivalent to the compiler's void type.</span></span> |
| <span data-ttu-id="0630d-140">**CHAR**</span><span class="sxs-lookup"><span data-stu-id="0630d-140">**CHAR**</span></span> | <span data-ttu-id="0630d-141">ほとんどの場合、標準の 8 ビット文字型です。</span><span class="sxs-lookup"><span data-stu-id="0630d-141">Most often a standard 8-bit character type.</span></span> |
|  |  |

<span data-ttu-id="0630d-142">その他のデータ型は Azure RTOS ThreadX ソース内で使用されます。</span><span class="sxs-lookup"><span data-stu-id="0630d-142">Additional data types are used within the Azure RTOS ThreadX source.</span></span> <span data-ttu-id="0630d-143">これらは、***tx_port.h*** ファイルにもあります。</span><span class="sxs-lookup"><span data-stu-id="0630d-143">They are also located in the ***tx_port.h*** file.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="0630d-144">カスタマー サポート センター</span><span class="sxs-lookup"><span data-stu-id="0630d-144">Customer Support Center</span></span>

<span data-ttu-id="0630d-145">ご質問がある場合、サポートが必要な場合は、次の手順で Azure Portal からサポートチケットを提出します。</span><span class="sxs-lookup"><span data-stu-id="0630d-145">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="0630d-146">お客様のサポート リクエストをより効率的に解決できるように、次の情報を電子メールでお知らせください。</span><span class="sxs-lookup"><span data-stu-id="0630d-146">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="0630d-147">問題の詳しい説明。発生頻度や、確実に再現できるかどうかなど。</span><span class="sxs-lookup"><span data-stu-id="0630d-147">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="0630d-148">問題が発生する前にアプリケーションや Azure RTOS ThreadX に加えた変更の詳しい説明。</span><span class="sxs-lookup"><span data-stu-id="0630d-148">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="0630d-149">ご自身のディストリビューションの *tx_port.h* ファイル内の *_tx_version_id* 文字列の内容。</span><span class="sxs-lookup"><span data-stu-id="0630d-149">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="0630d-150">この文字列から、実行時環境に関する重要な情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="0630d-150">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="0630d-151">**_tx_build_options** **ULONG** 変数の RAM の内容。</span><span class="sxs-lookup"><span data-stu-id="0630d-151">The contents in RAM of the **_tx_build_options** **ULONG** variable.</span></span> <span data-ttu-id="0630d-152">この変数から、Azure RTOS ThreadX ライブラリの構築方法に関する情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="0630d-152">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
