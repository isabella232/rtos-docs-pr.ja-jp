---
title: Azure RTOS NetX ユーザー ガイドについて
description: このガイドでは、Microsoft の高パフォーマンス ネットワーク スタックである Azure RTOS NetX について包括的に説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 01077e3315e87b918cdfd47423d8e0c1b6bbdbbd
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550271"
---
# <a name="about-the-azure-rtos-netx-user-guide"></a><span data-ttu-id="6cb99-103">Azure RTOS NetX ユーザー ガイドについて</span><span class="sxs-lookup"><span data-stu-id="6cb99-103">About The Azure RTOS NetX User Guide</span></span>

<span data-ttu-id="6cb99-104">このガイドでは、Microsoft の高パフォーマンス ネットワーク スタックである Azure RTOS NetX について包括的に説明します。</span><span class="sxs-lookup"><span data-stu-id="6cb99-104">This guide contains comprehensive information about Azure RTOS NetX, the Microsoft high-performance network stack.</span></span>

<span data-ttu-id="6cb99-105">本書は、基本的なネットワーク概念、Azure RTOS ThreadX、C プログラミング言語を理解している埋め込み型のリアルタイム ソフトウェア開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="6cb99-105">It is intended for embedded real-time software developers familiar with basic networking concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="6cb99-106">Organization</span><span class="sxs-lookup"><span data-stu-id="6cb99-106">Organization</span></span>

<span data-ttu-id="6cb99-107">[第 1 章](chapter1.md) - Azure RTOS NetX の概要</span><span class="sxs-lookup"><span data-stu-id="6cb99-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS NetX</span></span>

<span data-ttu-id="6cb99-108">[第 2 章](chapter2.md) - Azure RTOS NetX をインストールして ThreadX アプリケーションで使用するための基本的な手順を示します。</span><span class="sxs-lookup"><span data-stu-id="6cb99-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS NetX with your ThreadX application.</span></span>

<span data-ttu-id="6cb99-109">[第 3 章](chapter3.md) - Azure RTOS NetX システムの機能の概要と TCP/IP ネットワーク標準に関する基本的な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="6cb99-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS NetX system and basic information about the TCP/IP networking standards.</span></span>

<span data-ttu-id="6cb99-110">[第 4 章](chapter4.md) - Azure RTOS NetX のアプリケーションのインターフェイスについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="6cb99-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS NetX.</span></span>

<span data-ttu-id="6cb99-111">[第 5 章](chapter5.md) - Azure RTOS NetX のネットワーク ドライバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6cb99-111">[Chapter 5](chapter5.md) - Describes network drivers for Azure RTOS NetX.</span></span>

<span data-ttu-id="6cb99-112">[付録 A](appendix-a.md) - Azure RTOS NetX サービス</span><span class="sxs-lookup"><span data-stu-id="6cb99-112">[Appendix A](appendix-a.md) - Azure RTOS NetX Services</span></span>

<span data-ttu-id="6cb99-113">[付録 B](appendix-b.md) - Azure RTOS NetX の定数</span><span class="sxs-lookup"><span data-stu-id="6cb99-113">[Appendix B](appendix-b.md) - Azure RTOS NetX Constants</span></span>

<span data-ttu-id="6cb99-114">[付録 C](appendix-c.md) - Azure RTOS NetX のデータ型</span><span class="sxs-lookup"><span data-stu-id="6cb99-114">[Appendix C](appendix-c.md) - Azure RTOS NetX Data Types</span></span>

<span data-ttu-id="6cb99-115">[付録 D](appendix-d.md) - BSD 互換ソケット API</span><span class="sxs-lookup"><span data-stu-id="6cb99-115">[Appendix D](appendix-d.md) - BSD-Compatible Socket API</span></span>

<span data-ttu-id="6cb99-116">[付録 E](appendix-e.md) - ASCII チャート</span><span class="sxs-lookup"><span data-stu-id="6cb99-116">[Appendix E](appendix-e.md) - ASCII Chart</span></span>

## <a name="azure-rtos-netx-data-types"></a><span data-ttu-id="6cb99-117">Azure RTOS NetX のデータ型</span><span class="sxs-lookup"><span data-stu-id="6cb99-117">Azure RTOS NetX Data Types</span></span>

<span data-ttu-id="6cb99-118">カスタムの Azure RTOS NetX 制御構造データ型に加えて、Azure RTOS NetX サービス呼び出しインターフェイスで使用される特殊なデータ型がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="6cb99-118">In addition to the custom Azure RTOS NetX control structure data types, there are several special data types that are used in Azure RTOS NetX service call interfaces.</span></span> <span data-ttu-id="6cb99-119">これらの特殊データ型は、基になる C コンパイラのデータ型に直接マップされます。</span><span class="sxs-lookup"><span data-stu-id="6cb99-119">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="6cb99-120">これは、異なる C コンパイラ間での移植性を確保するために行われます。</span><span class="sxs-lookup"><span data-stu-id="6cb99-120">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="6cb99-121">正確な実装は ThreadX から継承されており、ThreadX ディストリビューションに含まれている ***tx_port.h*** ファイル内にあります。</span><span class="sxs-lookup"><span data-stu-id="6cb99-121">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="6cb99-122">Azure RTOS NetX サービス呼び出しのデータ型と、それに関連付けられている意味の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6cb99-122">The following is a list of Azure RTOS NetX service call data types and their associated meanings:</span></span>

| <span data-ttu-id="6cb99-123">データ型</span><span class="sxs-lookup"><span data-stu-id="6cb99-123">Data Types</span></span> | <span data-ttu-id="6cb99-124">説明</span><span class="sxs-lookup"><span data-stu-id="6cb99-124">Description</span></span>  |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="6cb99-125">**UINT**</span><span class="sxs-lookup"><span data-stu-id="6cb99-125">**UINT**</span></span>  | <span data-ttu-id="6cb99-126">基本的な符号なし整数。</span><span class="sxs-lookup"><span data-stu-id="6cb99-126">Basic unsigned integer.</span></span> <span data-ttu-id="6cb99-127">この型は、32 ビットの符号なしデータをサポートする必要があります。ただし、これは最も便利な符号なしデータ型にマップされます。</span><span class="sxs-lookup"><span data-stu-id="6cb99-127">This type must support 32-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="6cb99-128">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="6cb99-128">**ULONG**</span></span> | <span data-ttu-id="6cb99-129">符号なし long 型。</span><span class="sxs-lookup"><span data-stu-id="6cb99-129">Unsigned long type.</span></span> <span data-ttu-id="6cb99-130">この型では、32 ビットの符号なしデータをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6cb99-130">This type must support 32-bit unsigned data.</span></span>                                                                      |
| <span data-ttu-id="6cb99-131">**VOID**</span><span class="sxs-lookup"><span data-stu-id="6cb99-131">**VOID**</span></span>  | <span data-ttu-id="6cb99-132">ほとんどの場合、コンパイラの void 型と同等です。</span><span class="sxs-lookup"><span data-stu-id="6cb99-132">Almost always equivalent to the compiler's void type.</span></span>                                                                                 |
| <span data-ttu-id="6cb99-133">**CHAR**</span><span class="sxs-lookup"><span data-stu-id="6cb99-133">**CHAR**</span></span>  | <span data-ttu-id="6cb99-134">ほとんどの場合、標準の 8 ビット文字型です。</span><span class="sxs-lookup"><span data-stu-id="6cb99-134">Most often a standard 8-bit character type.</span></span>                                                                                           |

<span data-ttu-id="6cb99-135">その他のデータ型は Azure RTOS NetX ソース内で使用されます。</span><span class="sxs-lookup"><span data-stu-id="6cb99-135">Additional data types are used within the Azure RTOS NetX source.</span></span> <span data-ttu-id="6cb99-136">これらは ***tx_port.h** または *_nx_port.h_** のいずれかのファイル内にあります。</span><span class="sxs-lookup"><span data-stu-id="6cb99-136">They are located in either the ***tx_port.h** _ or _ *_nx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="6cb99-137">カスタマー サポート センター</span><span class="sxs-lookup"><span data-stu-id="6cb99-137">Customer Support Center</span></span>

<span data-ttu-id="6cb99-138">ご質問がある場合、サポートが必要な場合は、次の手順で Azure Portal からサポート チケットを提出します。</span><span class="sxs-lookup"><span data-stu-id="6cb99-138">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="6cb99-139">お客様のサポート リクエストをより効率的に解決できるように、以下の情報をメール メッセージに記載してください。</span><span class="sxs-lookup"><span data-stu-id="6cb99-139">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="6cb99-140">問題の詳しい説明。発生頻度や、確実に再現できるかどうかなど。</span><span class="sxs-lookup"><span data-stu-id="6cb99-140">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>

2. <span data-ttu-id="6cb99-141">問題が発生する前にアプリケーションや Azure RTOS NetX に行ったすべての変更に関する詳細な説明。</span><span class="sxs-lookup"><span data-stu-id="6cb99-141">A detailed description of any changes to the application and/or Azure RTOS NetX that preceded the problem.</span></span>

3. <span data-ttu-id="6cb99-142">ご自身のディストリビューションの **_tx_port.h_ *_ および _* _nx_port.h_** ファイル内の **_tx_version_id** 文字列および **_nx_version_id** 文字列の内容。</span><span class="sxs-lookup"><span data-stu-id="6cb99-142">The contents of the **_tx_version_id** and **_nx_version_id** strings found in the **_tx_port.h_*_ and _*_nx_port.h_** files of your distribution.</span></span> <span data-ttu-id="6cb99-143">これらの文字列から、実行時環境に関する重要な情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="6cb99-143">These strings will provide us valuable information regarding your run-time environment.</span></span>

4. <span data-ttu-id="6cb99-144">次の **ULONG** 変数の RAM 内の内容:</span><span class="sxs-lookup"><span data-stu-id="6cb99-144">The contents in RAM of the following **ULONG** variables:</span></span>

    <span data-ttu-id="6cb99-145">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="6cb99-145">**_tx_build_options**</span></span>

    <span data-ttu-id="6cb99-146">**_nx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="6cb99-146">**_nx_system_build_options1**</span></span>

    <span data-ttu-id="6cb99-147">**_nx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="6cb99-147">**_nx_system_build_options2**</span></span>

    <span data-ttu-id="6cb99-148">**_nx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="6cb99-148">**_nx_system_build_options3**</span></span>

    <span data-ttu-id="6cb99-149">**_nx_system_build_options4**</span><span class="sxs-lookup"><span data-stu-id="6cb99-149">**_nx_system_build_options4**</span></span>

    <span data-ttu-id="6cb99-150">**_nx_system_build_options5**</span><span class="sxs-lookup"><span data-stu-id="6cb99-150">**_nx_system_build_options5**</span></span>

    <span data-ttu-id="6cb99-151">これらの変数から、Azure RTOS ThreadX と Azure RTOS NetX のライブラリがどのように構築されたかに関する情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="6cb99-151">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS NetX libraries were built.</span></span>

5. <span data-ttu-id="6cb99-152">問題が検出された直後にキャプチャされたトレース バッファー。</span><span class="sxs-lookup"><span data-stu-id="6cb99-152">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="6cb99-153">これを行うには、Azure RTOS ThreadX と Azure RTOS NetX のライブラリを **TX_ENABLE_EVENT_TRACE** を使用して構築し、トレース バッファー情報を使用して **tx_trace_enable** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6cb99-153">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS NetX libraries with **TX_ENABLE_EVENT_TRACE** and calling **tx_trace_enable** with the trace buffer information.</span></span> <span data-ttu-id="6cb99-154">詳細については、Azure RTOS TraceX ユーザー ガイドをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6cb99-154">Refer to the Azure RTOS TraceX User Guide for details.</span></span>
