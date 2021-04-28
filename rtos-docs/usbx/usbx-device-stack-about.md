---
title: Azure RTOS USBX デバイス スタック ユーザー ガイド
description: このガイドでは、Microsoft のハイ パフォーマンス USB 基盤ソフトウェアである Azure RTOS USBX に関する包括的な情報を提供します
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: c8e9360c8b72adbc41f840a48e333668c489399e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810244"
---
# <a name="azure-rtos-usbx-device-stack-user-guide"></a><span data-ttu-id="b8d0f-103">Azure RTOS USBX デバイス スタック ユーザー ガイド</span><span class="sxs-lookup"><span data-stu-id="b8d0f-103">Azure RTOS USBX Device Stack User Guide</span></span>

<span data-ttu-id="b8d0f-104">このガイドでは、Microsoft のハイ パフォーマンス USB 基盤ソフトウェアである Azure RTOS USBX に関する包括的な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="b8d0f-104">This guide provides comprehensive information about Azure RTOS USBX, the high performance USB foundation software from Microsoft.</span></span>

<span data-ttu-id="b8d0f-105">これは、組み込みリアルタイム ソフトウェアの開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="b8d0f-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="b8d0f-106">開発者は、標準のリアルタイム オペレーティング システム関数、USB 仕様、および C プログラミング言語について理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8d0f-106">The developer should be familiar with standard real-time operating system functions, the USB specification, and the C programming language.</span></span>

<span data-ttu-id="b8d0f-107">USB に関する技術情報については、 https://www.USB.org/developers でダウンロードできる USB 仕様および USB クラス仕様を参照してください</span><span class="sxs-lookup"><span data-stu-id="b8d0f-107">For technical information related to USB, see the USB specification and USB Class specifications that can be downloaded at https://www.USB.org/developers</span></span>

## <a name="organization"></a><span data-ttu-id="b8d0f-108">Organization</span><span class="sxs-lookup"><span data-stu-id="b8d0f-108">Organization</span></span>

- <span data-ttu-id="b8d0f-109">[**第 1 章**](usbx-device-stack-1.md) - Azure RTOS USBX の概要が含まれています</span><span class="sxs-lookup"><span data-stu-id="b8d0f-109">[**Chapter 1**](usbx-device-stack-1.md) - contains an introduction to Azure RTOS USBX</span></span>

- <span data-ttu-id="b8d0f-110">[**第 2 章**](usbx-device-stack-2.md) - Azure RTOS USBX をインストールして ThreadX アプリケーションで使用するための基本的な手順を示します</span><span class="sxs-lookup"><span data-stu-id="b8d0f-110">[**Chapter 2**](usbx-device-stack-2.md) - gives the basic steps to install and use Azure RTOS USBX with your ThreadX application</span></span>

- <span data-ttu-id="b8d0f-111">[**第 3 章**](usbx-device-stack-3.md) - Azure RTOS USBX デバイス スタックの機能コンポーネントについて説明します</span><span class="sxs-lookup"><span data-stu-id="b8d0f-111">[**Chapter 3**](usbx-device-stack-3.md) - describes the functional components of the Azure RTOS USBX device stack</span></span>

- <span data-ttu-id="b8d0f-112">[**第 4 章**](usbx-device-stack-4.md) - Azure RTOS USBX デバイス スタックのサービスについて説明します</span><span class="sxs-lookup"><span data-stu-id="b8d0f-112">[**Chapter 4**](usbx-device-stack-4.md) - describes the Azure RTOS USBX device stack services</span></span>

- <span data-ttu-id="b8d0f-113">[**第 5 章**](usbx-device-stack-5.md) - 各 Azure RTOS USBX デバイス クラスについて、API を含めて説明します</span><span class="sxs-lookup"><span data-stu-id="b8d0f-113">[**Chapter 5**](usbx-device-stack-5.md) - describes each Azure RTOS USBX device class including their APIs</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="b8d0f-114">カスタマー サポート センター</span><span class="sxs-lookup"><span data-stu-id="b8d0f-114">Customer Support Center</span></span>

<span data-ttu-id="b8d0f-115">質問やこちらの手順に関するお問い合わせについては、Azure portal からサポート チケットを送信してください。</span><span class="sxs-lookup"><span data-stu-id="b8d0f-115">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="b8d0f-116">お客様のサポート リクエストをより効率的に解決できるように、次の情報を電子メールでお知らせください。</span><span class="sxs-lookup"><span data-stu-id="b8d0f-116">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="b8d0f-117">問題の詳しい説明。発生頻度や、確実に再現できるかどうかなど。</span><span class="sxs-lookup"><span data-stu-id="b8d0f-117">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="b8d0f-118">問題が発生する前にアプリケーションや Azure RTOS ThreadX に加えた変更の詳しい説明。</span><span class="sxs-lookup"><span data-stu-id="b8d0f-118">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="b8d0f-119">ご自身のディストリビューションの **_tx_port.h_** ファイル内の **_tx_version_id** 文字列の内容。</span><span class="sxs-lookup"><span data-stu-id="b8d0f-119">The contents of the **_tx_version_id** string found in the **_tx_port.h_** file of your distribution.</span></span> <span data-ttu-id="b8d0f-120">この文字列から、実行時環境に関する重要な情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="b8d0f-120">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="b8d0f-121">*_tx_build_options* **ULONG** 変数の RAM の内容。</span><span class="sxs-lookup"><span data-stu-id="b8d0f-121">The contents in RAM of the *_tx_build_options* **ULONG** variable.</span></span> <span data-ttu-id="b8d0f-122">この変数から、Azure RTOS ThreadX ライブラリの構築方法に関する情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="b8d0f-122">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
