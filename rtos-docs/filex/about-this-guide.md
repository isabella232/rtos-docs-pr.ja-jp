---
title: Azure RTOS FileX ユーザー ガイド
description: このガイドには、Microsoft のハイパフォーマンス リアルタイム ファイル システムである Azure RTOS FileX に関する包括的な情報が含まれています。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 640d9ed4c8037d3af6c5f45158c9496ad1258a3c
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550101"
---
# <a name="about-this-filex-user-guide"></a><span data-ttu-id="3b7ac-103">この FileX ユーザー ガイドについて</span><span class="sxs-lookup"><span data-stu-id="3b7ac-103">About This FileX User Guide</span></span>

<span data-ttu-id="3b7ac-104">このガイドには、Microsoft のハイパフォーマンス リアルタイム組み込みファイル システムである Azure RTOS FileX に関する包括的な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-104">This guide contains comprehensive information about Azure RTOS FileX, the high-performance, real-time embedded file system from Microsoft.</span></span> <span data-ttu-id="3b7ac-105">このガイドを最大限に活用するには、標準のリアルタイム オペレーティング システム関数、FAT ファイル システムのサービス、および C プログラミング言語について理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-105">To gain the most from this guide, you should be familiar with standard real-time operating system functions, FAT file system services, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="3b7ac-106">Organization</span><span class="sxs-lookup"><span data-stu-id="3b7ac-106">Organization</span></span>

<span data-ttu-id="3b7ac-107">[第 1 章](chapter1.md) - Azure RTOS FileX の概要を示します</span><span class="sxs-lookup"><span data-stu-id="3b7ac-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS FileX</span></span>

<span data-ttu-id="3b7ac-108">[第 2 章](chapter2.md) - Azure RTOS FileX をインストールして Azure RTOS ThreadX アプリケーションで使用するための基本的な手順を示します</span><span class="sxs-lookup"><span data-stu-id="3b7ac-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS FileX with your Azure RTOS ThreadX application</span></span>

<span data-ttu-id="3b7ac-109">[第 3 章](chapter3.md) - Azure RTOS FileX システムの機能の概要と FAT ファイル システム形式に関する基本的な情報を提供します</span><span class="sxs-lookup"><span data-stu-id="3b7ac-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS FileX system and basic information about FAT file system formats</span></span>

<span data-ttu-id="3b7ac-110">[第 4 章](chapter4.md) - Azure RTOS FileX に対するアプリケーションのインターフェイスについて詳しく説明します</span><span class="sxs-lookup"><span data-stu-id="3b7ac-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS FileX</span></span>

<span data-ttu-id="3b7ac-111">[第 5 章](chapter5.md) - 提供されている Azure RTOS FileX RAM ドライバーについて説明し、独自のカスタム Azure RTOS FileX ドライバーを作成する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="3b7ac-111">[Chapter 5](chapter5.md) - Describes the supplied Azure RTOS FileX RAM driver and how to write your own custom Azure RTOS FileX drivers</span></span>

<span data-ttu-id="3b7ac-112">[第 6 章](chapter6.md) - Azure RTOS FileX フォールト トレラント モジュールについて説明します</span><span class="sxs-lookup"><span data-stu-id="3b7ac-112">[Chapter 6](chapter6.md) - Describes the Azure RTOS FileX Fault Tolerant Module</span></span>

<span data-ttu-id="3b7ac-113">[付録 A](appendix-a.md) - Azure RTOS FileX のサービス</span><span class="sxs-lookup"><span data-stu-id="3b7ac-113">[Appendix A](appendix-a.md) - Azure RTOS FileX Services</span></span>

<span data-ttu-id="3b7ac-114">[付録 B](appendix-b.md) - Azure RTOS FileX の定数</span><span class="sxs-lookup"><span data-stu-id="3b7ac-114">[Appendix B](appendix-b.md) - Azure RTOS FileX Constants</span></span>

<span data-ttu-id="3b7ac-115">[付録 C](appendix-c.md) - Azure RTOS FileX のデータ型</span><span class="sxs-lookup"><span data-stu-id="3b7ac-115">[Appendix C](appendix-c.md) - Azure RTOS FileX Data Types</span></span>

<span data-ttu-id="3b7ac-116">[付録 D](appendix-d.md) - ASCII チャート</span><span class="sxs-lookup"><span data-stu-id="3b7ac-116">[Appendix D](appendix-d.md) - ASCII Chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="3b7ac-117">ガイドの表記規則</span><span class="sxs-lookup"><span data-stu-id="3b7ac-117">Guide Conventions</span></span>

<span data-ttu-id="3b7ac-118">"*斜体*" - この書体は、本のタイトルを表し、重要な単語を強調し、変数を示すために使用されています。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-118">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="3b7ac-119">**太字** - この書体は、ファイル名とキーワードを表し、重要な単語や変数をさらに強調するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-119">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!NOTE]
> <span data-ttu-id="3b7ac-120">情報記号は、注意する必要がある、パフォーマンスや機能に影響を与える可能性のある重要な情報や追加情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-120">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3b7ac-121">警告記号は、致命的なエラーを引き起こす可能性があるため、開発者が回避する必要がある状況を示します。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-121">Warning symbols draw attention to situations that developers should avoid because they could cause fatal errors.</span></span>

## <a name="filex-data-types"></a><span data-ttu-id="3b7ac-122">FileX のデータ型</span><span class="sxs-lookup"><span data-stu-id="3b7ac-122">FileX Data Types</span></span>

<span data-ttu-id="3b7ac-123">カスタムの Azure RTOS FileX 制御構造データ型に加えて、Azure RTOS FileX サービス呼び出しインターフェイスで使用される一連の特殊なデータ型があります。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-123">In addition to the custom Azure RTOS FileX control structure data types, there is a series of special data types that are used in Azure RTOS FileX service call interfaces.</span></span> <span data-ttu-id="3b7ac-124">これらの特殊データ型は、基になる C コンパイラのデータ型に直接マップされます。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-124">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="3b7ac-125">これは、異なる C コンパイラ間での移植性を確保するために行われます。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-125">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="3b7ac-126">正確な実装は Azure RTOS ThreadX から継承されており、Azure RTOS ThreadX ディストリビューションに含まれている tx_port.h ファイルにあります。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-126">The exact implementation is inherited from Azure RTOS ThreadX and can be found in the tx_port.h file included in the Azure RTOS ThreadX distribution.</span></span>

<span data-ttu-id="3b7ac-127">Azure RTOS FileX サービス呼び出しのデータ型と、それに関連付けられている意味の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-127">The following is a list of Azure RTOS FileX service call data types and their associated meanings.</span></span>

| <span data-ttu-id="3b7ac-128">Type</span><span class="sxs-lookup"><span data-stu-id="3b7ac-128">Type</span></span>  | <span data-ttu-id="3b7ac-129">説明</span><span class="sxs-lookup"><span data-stu-id="3b7ac-129">Description</span></span>  |
|---|---|
| <span data-ttu-id="3b7ac-130">**UINT**</span><span class="sxs-lookup"><span data-stu-id="3b7ac-130">**UINT**</span></span> | <span data-ttu-id="3b7ac-131">基本的な符号なし整数。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-131">Basic unsigned integer.</span></span> <span data-ttu-id="3b7ac-132">この型は、8 ビットの符号なしデータをサポートする必要があります。ただし、最も便利な符号なしデータ型にマップされます。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-132">This type must support 8-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="3b7ac-133">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="3b7ac-133">**ULONG**</span></span> | <span data-ttu-id="3b7ac-134">符号なし long 型。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-134">Unsigned long type.</span></span> <span data-ttu-id="3b7ac-135">この型では、32 ビットの符号なしデータをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-135">This type must support 32-bit unsigned data.</span></span> |
| <span data-ttu-id="3b7ac-136">**VOID**</span><span class="sxs-lookup"><span data-stu-id="3b7ac-136">**VOID**</span></span> | <span data-ttu-id="3b7ac-137">ほとんどの場合、コンパイラの void 型と同等です。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-137">Almost always equivalent to the compiler’s void type.</span></span> |
| <span data-ttu-id="3b7ac-138">**CHAR**</span><span class="sxs-lookup"><span data-stu-id="3b7ac-138">**CHAR**</span></span> | <span data-ttu-id="3b7ac-139">ほとんどの場合、標準の 8 ビット文字型です。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-139">Most often a standard 8-bit character type.</span></span> |
| <span data-ttu-id="3b7ac-140">**ULONG64**</span><span class="sxs-lookup"><span data-stu-id="3b7ac-140">**ULONG64**</span></span> | <span data-ttu-id="3b7ac-141">64 ビット符号なし整数データ型。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-141">64-bit unsigned integer data type.</span></span> |

<span data-ttu-id="3b7ac-142">追加のデータ型は、FileX ソース内で使用されます。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-142">Additional data types are used within the FileX source.</span></span> <span data-ttu-id="3b7ac-143">これらは ***tx_port.h** または *_fx_port.h_** のいずれかのファイル内にあります。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-143">They are located in either the ***tx_port.h** _ or _ *_fx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="3b7ac-144">カスタマー サポート センター</span><span class="sxs-lookup"><span data-stu-id="3b7ac-144">Customer Support Center</span></span>

<span data-ttu-id="3b7ac-145">質問やこちらの手順に関するお問い合わせについては、Azure portal からサポート チケットを送信してください。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-145">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="3b7ac-146">お客様のサポート リクエストをより効率的に解決できるように、次の情報を電子メールでお知らせください。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-146">Please supply us with the following information in an email message so we can more efficiently resolve your support request.</span></span>

1. <span data-ttu-id="3b7ac-147">問題の詳しい説明。発生頻度や、確実に再現できるかどうかなど。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-147">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="3b7ac-148">問題が発生する前にアプリケーションや FileX に加えた変更の詳しい説明。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-148">A detailed description of any changes to the application and/or FileX that preceded the problem.</span></span>
3. <span data-ttu-id="3b7ac-149">ご自身のディストリビューションの _tx_version_id および _fx_version_id 文字列の内容 (\***tx_port.h**_ および _ *_fx_port.h_*\* ファイル内)。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-149">The contents of the _tx_version_id and _fx_version_id strings found in the \***tx_port.h**_ and _ *_fx_port.h_*\* files of your distribution.</span></span> <span data-ttu-id="3b7ac-150">これらの文字列から、実行時環境に関する重要な情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-150">These strings will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="3b7ac-151">次の **ULONG** 変数の RAM の内容。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-151">The contents in RAM of the following **ULONG** variables.</span></span> <span data-ttu-id="3b7ac-152">これらの変数から、ThreadX と FileX のライブラリがどのように構築されたかに関する情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="3b7ac-152">These variables will give us information on how your ThreadX and FileX libraries were built:</span></span>

    <span data-ttu-id="3b7ac-153">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="3b7ac-153">**_tx_build_options**</span></span>

    <span data-ttu-id="3b7ac-154">**_fx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="3b7ac-154">**_fx_system_build_options1**</span></span>

    <span data-ttu-id="3b7ac-155">**_fx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="3b7ac-155">**_fx_system_build_options2**</span></span>

    <span data-ttu-id="3b7ac-156">**_fx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="3b7ac-156">**_fx_system_build_options3**</span></span>
