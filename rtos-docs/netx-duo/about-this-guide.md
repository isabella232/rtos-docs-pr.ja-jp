---
title: Azure RTOS NetX Duo ユーザー ガイドについて
description: このガイドでは、Microsoft の高パフォーマンス IPv4/IPv6 デュアル ネットワーク スタックである Azure RTOS NetX Duo について包括的に説明しています。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b1eef5bfa28f13d7a6b627792f96039b252f2355
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811054"
---
# <a name="about-the-azure-rtos-netx-duo-user-guide"></a><span data-ttu-id="4b31a-103">Azure RTOS NetX Duo ユーザー ガイドについて</span><span class="sxs-lookup"><span data-stu-id="4b31a-103">About The Azure RTOS NetX Duo User Guide</span></span>

<span data-ttu-id="4b31a-104">このガイドでは、Microsoft の高パフォーマンス IPv4/IPv6 デュアル ネットワーク スタックである Azure RTOS NetX Duo について包括的に説明しています。</span><span class="sxs-lookup"><span data-stu-id="4b31a-104">This guide contains comprehensive information about Azure RTOS NetX Duo, the Microsoft high-performance IPv4/IPv6 dual network stack.</span></span> 

<span data-ttu-id="4b31a-105">本書は、基本的なネットワーク概念、Azure RTOS ThreadX、C プログラミング言語を理解している埋め込みリアルタイム ソフトウェアの開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="4b31a-105">It is intended for embedded real-time software developers familiar with basic networking concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="4b31a-106">Organization</span><span class="sxs-lookup"><span data-stu-id="4b31a-106">Organization</span></span>

<span data-ttu-id="4b31a-107">[第 1 章](chapter1.md) - Azure RTOS NetX Duo の概要</span><span class="sxs-lookup"><span data-stu-id="4b31a-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS NetX Duo</span></span>

<span data-ttu-id="4b31a-108">[第 2 章](chapter2.md) - Azure RTOS NetX Duo をインストールして ThreadX アプリケーションで使用するための基本的な手順を示します</span><span class="sxs-lookup"><span data-stu-id="4b31a-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS NetX Duo with your ThreadX application</span></span>

<span data-ttu-id="4b31a-109">[第 3 章](chapter3.md) - Azure RTOS NetX Duo システムの機能の概要と TCP/IP ネットワーク標準の基本情報について説明します</span><span class="sxs-lookup"><span data-stu-id="4b31a-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS NetX Duo system and basic information about the TCP/IP networking standards</span></span>

<span data-ttu-id="4b31a-110">[第 4 章](chapter4.md) - Azure RTOS NetX Duo に対するアプリケーションのインターフェイスの詳細です</span><span class="sxs-lookup"><span data-stu-id="4b31a-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS NetX Duo</span></span>

<span data-ttu-id="4b31a-111">[第 5 章](chapter5.md) - Azure RTOS NetX Duo のネットワーク ドライバーについて説明します</span><span class="sxs-lookup"><span data-stu-id="4b31a-111">[Chapter 5](chapter5.md) - Describes network drivers for Azure RTOS NetX Duo</span></span>

<span data-ttu-id="4b31a-112">[付録 A](appendix-a.md) - Azure RTOS NetX Duo のサービス</span><span class="sxs-lookup"><span data-stu-id="4b31a-112">[Appendix A](appendix-a.md) - Azure RTOS NetX Duo Services</span></span>

<span data-ttu-id="4b31a-113">[付録 B](appendix-b.md) - Azure RTOS NetX Duo の定数</span><span class="sxs-lookup"><span data-stu-id="4b31a-113">[Appendix B](appendix-b.md) - Azure RTOS NetX Duo Constants</span></span>

<span data-ttu-id="4b31a-114">[付録 C](appendix-c.md) - Azure RTOS NetX Duo のデータ型</span><span class="sxs-lookup"><span data-stu-id="4b31a-114">[Appendix C](appendix-c.md) - Azure RTOS NetX Duo Data Types</span></span>

<span data-ttu-id="4b31a-115">[付録 D](appendix-d.md) - BSD 互換ソケット API</span><span class="sxs-lookup"><span data-stu-id="4b31a-115">[Appendix D](appendix-d.md) - BSD-Compatible Socket API</span></span>

<span data-ttu-id="4b31a-116">[付録 E](appendix-e.md) - ASCII チャート</span><span class="sxs-lookup"><span data-stu-id="4b31a-116">[Appendix E](appendix-e.md) - ASCII Chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="4b31a-117">ガイドの表記規則</span><span class="sxs-lookup"><span data-stu-id="4b31a-117">Guide Conventions</span></span>

<span data-ttu-id="4b31a-118">斜体 - この書体は、本のタイトルを表し、重要な単語を強調し、変数を示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b31a-118">Italics - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="4b31a-119">**太字** - この書体は、ファイル名とキーワードを表し、重要な単語や変数をさらに強調するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b31a-119">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4b31a-120">情報記号は、注意する必要がある、パフォーマンスや機能に影響を与える可能性のある重要な情報や追加情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4b31a-120">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>
 
> [!WARNING]
> <span data-ttu-id="4b31a-121">警告記号は、致命的なエラーを引き起こす可能性があるため、開発者が回避する必要がある状況を示します。</span><span class="sxs-lookup"><span data-stu-id="4b31a-121">Warning symbols draw attention to situations that developers should avoid because they could cause fatal errors.</span></span>

## <a name="azure-rtos-netx-duo-data-types"></a><span data-ttu-id="4b31a-122">Azure RTOS NetX Duo のデータ型</span><span class="sxs-lookup"><span data-stu-id="4b31a-122">Azure RTOS NetX Duo Data Types</span></span>

<span data-ttu-id="4b31a-123">Azure RTOS NetX Duo のカスタムの制御構造データ型に加えて、Azure RTOS NetX Duo サービス呼び出しインターフェイスで使用される特殊なデータ型がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="4b31a-123">In addition to the custom Azure RTOS NetX Duo control structure data types, there are several special data types that are used in Azure RTOS NetX Duo service call interfaces.</span></span> <span data-ttu-id="4b31a-124">これらの特殊データ型は、基になる C コンパイラのデータ型に直接マップされます。</span><span class="sxs-lookup"><span data-stu-id="4b31a-124">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="4b31a-125">これは、異なる C コンパイラ間での移植性を確保するために行われます。</span><span class="sxs-lookup"><span data-stu-id="4b31a-125">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="4b31a-126">正確な実装は ThreadX から継承されており、ThreadX ディストリビューションに含まれている ***tx_port.h*** ファイルにあります。</span><span class="sxs-lookup"><span data-stu-id="4b31a-126">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="4b31a-127">次に示すのは、Azure RTOS NetX Duo サービス呼び出しのデータ型とそれに関連付けられている意味の一覧です。</span><span class="sxs-lookup"><span data-stu-id="4b31a-127">The following is a list of Azure RTOS NetX Duo service call data types and their associated meanings:</span></span>

<span data-ttu-id="4b31a-128">**UINT**: 基本的な符号なし整数。</span><span class="sxs-lookup"><span data-stu-id="4b31a-128">**UINT**: Basic unsigned integer.</span></span> <span data-ttu-id="4b31a-129">この型は、32 ビットの符号なしデータをサポートする必要があります。ただし、最も便利な符号なしデータ型にマップされます。</span><span class="sxs-lookup"><span data-stu-id="4b31a-129">This type must support 32-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span>  
<span data-ttu-id="4b31a-130">**ULONG**: 符号なし long 型。</span><span class="sxs-lookup"><span data-stu-id="4b31a-130">**ULONG**: Unsigned long type.</span></span> <span data-ttu-id="4b31a-131">この型は、32 ビットの符号なしデータをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b31a-131">This type must support 32-bit unsigned  data.</span></span>
<span data-ttu-id="4b31a-132">**VOID**: ほとんどの場合、コンパイラの void 型と同等です。</span><span class="sxs-lookup"><span data-stu-id="4b31a-132">**VOID**: Almost always equivalent to the compiler's void type.</span></span>  
<span data-ttu-id="4b31a-133">**CHAR**: ほとんどの場合、標準の 8 ビット文字型です。</span><span class="sxs-lookup"><span data-stu-id="4b31a-133">**CHAR**: Most often a standard 8-bit character type.</span></span>  

<span data-ttu-id="4b31a-134">その他のデータ型が Azure RTOS NetX Duo ソース内で使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b31a-134">Additional data types are used within the Azure RTOS NetX Duo source.</span></span> <span data-ttu-id="4b31a-135">それらは ***tx_port.h** _ と _ *_nx_port.h_** のいずれかのファイルにあります。</span><span class="sxs-lookup"><span data-stu-id="4b31a-135">They are located in either the ***tx_port.h** _ or _ *_nx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="4b31a-136">カスタマー サポート センター</span><span class="sxs-lookup"><span data-stu-id="4b31a-136">Customer Support Center</span></span>

<span data-ttu-id="4b31a-137">こちらの手順に関する質問やサポートについては、Azure portal からサポート チケットを送信してください。</span><span class="sxs-lookup"><span data-stu-id="4b31a-137">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="4b31a-138">お客さまのサポート リクエストをより効率的に解決できるように、電子メール メッセージで次の情報をお知らせください。</span><span class="sxs-lookup"><span data-stu-id="4b31a-138">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="4b31a-139">問題の詳しい説明。発生頻度や、確実に再現できるかどうかなど。</span><span class="sxs-lookup"><span data-stu-id="4b31a-139">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="4b31a-140">問題が発生する前にアプリケーションや Azure RTOS NetX Duo に加えた変更の詳しい説明。</span><span class="sxs-lookup"><span data-stu-id="4b31a-140">A detailed description of any changes to the application and/or Azure RTOS NetX Duo that preceded the problem.</span></span>
3. <span data-ttu-id="4b31a-141">ディストリビューションの tx_port.h および nx_port.h のファイルの中にある _tx_version_id および _nx_version_id の文字列の内容。</span><span class="sxs-lookup"><span data-stu-id="4b31a-141">The contents of the _tx_version_id and _nx_version_id strings found in the tx_port.h and nx_port.h files of your distribution.</span></span> <span data-ttu-id="4b31a-142">これらの文字列から、実行時環境に関する重要な情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="4b31a-142">These strings will provide us valuable information regarding your run- time environment.</span></span>
4. <span data-ttu-id="4b31a-143">次の ULONG 変数の RAM の内容。</span><span class="sxs-lookup"><span data-stu-id="4b31a-143">The contents in RAM of the following ULONG variables:</span></span>

    <span data-ttu-id="4b31a-144">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="4b31a-144">**_tx_build_options**</span></span>

    <span data-ttu-id="4b31a-145">**_nx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="4b31a-145">**_nx_system_build_options1**</span></span>

    <span data-ttu-id="4b31a-146">**_nx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="4b31a-146">**_nx_system_build_options2**</span></span>

    <span data-ttu-id="4b31a-147">**_nx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="4b31a-147">**_nx_system_build_options3**</span></span>

    <span data-ttu-id="4b31a-148">**_nx_system_build_options4**</span><span class="sxs-lookup"><span data-stu-id="4b31a-148">**_nx_system_build_options4**</span></span>

    <span data-ttu-id="4b31a-149">**_nx_system_build_options5**</span><span class="sxs-lookup"><span data-stu-id="4b31a-149">**_nx_system_build_options5**</span></span>

    <span data-ttu-id="4b31a-150">これらの変数から、Azure RTOS ThreadX と Azure RTOS NetX Duo のライブラリがどのようにビルドされたかについての情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="4b31a-150">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS NetX Duo libraries were built.</span></span>

5. <span data-ttu-id="4b31a-151">問題が検出された直後にキャプチャされたトレース バッファー。</span><span class="sxs-lookup"><span data-stu-id="4b31a-151">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="4b31a-152">これを行なうには、Azure RTOS ThreadX と Azure RTOS NetX Duo のライブラリを TX_ENABLE_EVENT_TRACE を使用してビルドし、トレース バッファー情報を使用して tx_trace_enable を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4b31a-152">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS NetX Duo libraries with TX_ENABLE_EVENT_TRACE and calling tx_trace_enable with the trace buffer information.</span></span>
