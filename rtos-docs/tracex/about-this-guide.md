---
title: Azure RTOS TraceX ユーザー ガイド
description: このガイドには、Microsoft 提供の Microsoft Windows ベースのシステム分析ツールである Azure RTOS TraceX に関する包括的な情報が含まれています。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 92d886b19a0c67292cd4f6a5f8bd7f9d3106374b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812686"
---
# <a name="about-this-guide"></a><span data-ttu-id="7afbc-103">このガイドについて</span><span class="sxs-lookup"><span data-stu-id="7afbc-103">About this guide</span></span>

<span data-ttu-id="7afbc-104">このガイドには、Microsoft Azure RTOS 用の Microsoft Windows ベースのシステム分析ツールである Azure RTOS TraceX に関する包括的な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7afbc-104">This guide contains comprehensive information about Azure RTOS TraceX, the Microsoft Windows-based system analysis tool for Microsoft Azure RTOS.</span></span>

<span data-ttu-id="7afbc-105">Azure RTOS ThreadX リアルタイム オペレーティング システム (RTOS) およびアドオン コンポーネントを使用する組み込みリアルタイム ソフトウェア開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="7afbc-105">It is intended for the embedded real-time software developer using Azure RTOS ThreadX Real-Time Operating System (RTOS) and add-on components.</span></span> <span data-ttu-id="7afbc-106">開発者には、Azure RTOS ThreadX、Azure RTOS FileX、および Azure RTOS NetX の標準的な概念に関する知識が必要です。</span><span class="sxs-lookup"><span data-stu-id="7afbc-106">The developer should be familiar with standard Azure RTOS ThreadX Azure RTOS FileX, and Azure RTOS NetX concepts.</span></span>

## <a name="organization"></a><span data-ttu-id="7afbc-107">Organization</span><span class="sxs-lookup"><span data-stu-id="7afbc-107">Organization</span></span>

- <span data-ttu-id="7afbc-108">[第 1 章](chapter1.md) - Azure RTOS TraceX の基本的な概要、およびリアルタイム開発との関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="7afbc-108">[Chapter 1](chapter1.md) - contains an basic overview of Azure RTOS TraceX and describes its relationship to real-time development.</span></span>
- <span data-ttu-id="7afbc-109">[第 2 章](chapter2.md) - Azure RTOS TraceX をインストールして使用し、すぐにアプリケーションの分析を始めるための基本的な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="7afbc-109">[Chapter 2](chapter2.md) - gives the basic steps to install and use Azure RTOS TraceX to analyze your application right out of the box.</span></span>
- <span data-ttu-id="7afbc-110">[第 3 章](chapter3.md) - Azure RTOS TraceX の主な機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="7afbc-110">[Chapter 3](chapter3.md) - describes the main features of Azure RTOS TraceX.</span></span>
- <span data-ttu-id="7afbc-111">[第 4 章](chapter4.md) - Azure RTOS TraceX のパフォーマンス分析機能について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="7afbc-111">[Chapter 4](chapter4.md) - details performance analysis features of Azure RTOS TraceX.</span></span>
- <span data-ttu-id="7afbc-112">[第 5 章](chapter5.md) - Azure RTOS TraceX で表示できるトレース バッファーを生成するために、Azure RTOS ThreadX、Azure RTOS FileX、および Azure RTOS NetX を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7afbc-112">[Chapter 5](chapter5.md) - describes how to set up Azure RTOS ThreadX, Azure RTOS FileX, and Azure RTOS NetX in order to generate a trace buffer that is viewable by Azure RTOS TraceX.</span></span>
- <span data-ttu-id="7afbc-113">[第 6 章](chapter6.md) - Azure RTOS TraceX イベントの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="7afbc-113">[Chapter 6](chapter6.md) - describes Azure RTOS TraceX events in detail.</span></span>
- <span data-ttu-id="7afbc-114">[第 7 章](chapter7.md) - Azure RTOS FileX イベントの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="7afbc-114">[Chapter 7](chapter7.md) - describes Azure RTOS FileX events in detail.</span></span>
- <span data-ttu-id="7afbc-115">[第 8 章](chapter8.md) - Azure RTOS NetX イベントの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="7afbc-115">[Chapter 8](chapter8.md) - describes Azure RTOS NetX events in detail.</span></span>
- <span data-ttu-id="7afbc-116">[第 9 章](chapter9.md) - Azure RTOS USBX イベントの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="7afbc-116">[Chapter 9](chapter9.md) - describes Azure RTOS USBX events in detail.</span></span>
- <span data-ttu-id="7afbc-117">[第 10 章](chapter10.md) - カスタム ユーザー イベントの作成について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="7afbc-117">[Chapter 10](chapter10.md) - describes creating custom user events in detail.</span></span>
- <span data-ttu-id="7afbc-118">[第 11 章](chapter11.md) - 内部トレース バッファーについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="7afbc-118">[Chapter 11](chapter11.md) - describes the internal trace buffer in detail.</span></span>
- <span data-ttu-id="7afbc-119">[付録 A](appendix-a.md) - Azure RTOS ThreadX のポート固有のファイルと、トレース イベントを収集するためのタイムスタンプ ソース。</span><span class="sxs-lookup"><span data-stu-id="7afbc-119">[Appendix A](appendix-a.md) - Azure RTOS ThreadX port-specific file with its time-stamp source for gathering trace events.</span></span>
- <span data-ttu-id="7afbc-120">[付録 B](appendix-b.md) - イベント トレース バッファーに関する実装の詳細を示す Azure RTOS ThreadX の *tx_trace.h* ファイル。</span><span class="sxs-lookup"><span data-stu-id="7afbc-120">[Appendix B](appendix-b.md) - Azure RTOS ThreadX *tx_trace.h* file that shows implementation details regarding the event trace buffer.</span></span>
- <span data-ttu-id="7afbc-121">[付録 C](appendix-c.md) - さまざまなファイル形式を適切な Azure RTOS TraceX バイナリ ファイルに変換するためのコマンド ライン ユーティリティの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="7afbc-121">[Appendix C](appendix-c.md) - Summarizes command line utilities for converting various file formats into proper Azure RTOS TraceX binary files.</span></span>
- <span data-ttu-id="7afbc-122">[付録 D](appendix-d.md) - さまざまな開発ツールからトレース ファイルをダンプする例。</span><span class="sxs-lookup"><span data-stu-id="7afbc-122">[Appendix D](appendix-d.md) - Examples of dumping trace files from various development tools.</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="7afbc-123">ガイドの表記規則</span><span class="sxs-lookup"><span data-stu-id="7afbc-123">Guide Conventions</span></span>

<span data-ttu-id="7afbc-124">"*斜体*" - この書体は、本のタイトルを表し、重要な単語を強調し、変数を示すために使用されています。</span><span class="sxs-lookup"><span data-stu-id="7afbc-124">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="7afbc-125">**太字** - この書体は、ファイル名とキーワードを表し、重要な単語や変数をさらに強調するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="7afbc-125">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!NOTE]
> <span data-ttu-id="7afbc-126">注意事項を示します。</span><span class="sxs-lookup"><span data-stu-id="7afbc-126">Indicates information of note.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="7afbc-127">カスタマー サポート センター</span><span class="sxs-lookup"><span data-stu-id="7afbc-127">Customer Support Center</span></span>

<span data-ttu-id="7afbc-128">こちらの手順に関する質問やサポートについては、Azure Portal からサポート チケットを送信してください。</span><span class="sxs-lookup"><span data-stu-id="7afbc-128">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="7afbc-129">お客様のサポート リクエストをより効率的に解決できるように、以下の情報をメール メッセージに記載してください。</span><span class="sxs-lookup"><span data-stu-id="7afbc-129">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="7afbc-130">問題の詳しい説明。発生頻度や、確実に再現できるかどうかなど。</span><span class="sxs-lookup"><span data-stu-id="7afbc-130">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="7afbc-131">問題が発生する前にアプリケーションや Azure RTOS ThreadX に加えた変更の詳しい説明。</span><span class="sxs-lookup"><span data-stu-id="7afbc-131">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="7afbc-132">ご自身のディストリビューションの *tx_port.h* ファイル内の *_tx_version_id* 文字列の内容。</span><span class="sxs-lookup"><span data-stu-id="7afbc-132">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="7afbc-133">この文字列から、実行時環境に関する重要な情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="7afbc-133">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="7afbc-134">*_tx_build_options* ULONG 変数の RAM の内容。</span><span class="sxs-lookup"><span data-stu-id="7afbc-134">The contents in RAM of the *_tx_build_options* ULONG variable.</span></span> <span data-ttu-id="7afbc-135">この変数から、Azure RTOS ThreadX ライブラリの構築方法に関する情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="7afbc-135">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
