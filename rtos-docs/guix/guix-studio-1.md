---
title: GUIX Studio ユーザー ガイド
description: このガイドでは GUIX Studio に関する総合的な情報を提供します。これは、Microsoft の GUIX ランタイム ライブラリ用に設計された、Microsoft Windows ベースの高速 UI 開発環境です。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6a5d628581d4c6b44ff093bac45790d6e2755349
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811987"
---
# <a name="chapter-1-introduction-to-azure-rtos-guix-studio"></a><span data-ttu-id="68faa-103">第 1 章: Azure RTOS GUIX Studio の概要</span><span class="sxs-lookup"><span data-stu-id="68faa-103">Chapter 1: Introduction to Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="68faa-104">Azure RTOS GUIX Studio は、Microsoft の GUIX ランタイム ライブラリ専用に設計された、Microsoft Windows ベースの高速 UI 開発環境です。</span><span class="sxs-lookup"><span data-stu-id="68faa-104">Azure RTOS GUIX Studio is a Microsoft Windows-based rapid UI development environment specifically designed for the GUIX runtime library from Microsoft.</span></span>

<span data-ttu-id="68faa-105">埋め込み UI の開発者は、GUIX Studio WYSIWYG 画面デザイナーを利用し、GUIX ランタイム環境を使用して埋め込み UI をすばやく作成および更新できます。</span><span class="sxs-lookup"><span data-stu-id="68faa-105">Embedded UI Developers can utilize the GUIX Studio WYSIWYG screen designer to quickly create and update their embedded UI using the GUIX run-time environment.</span></span> <span data-ttu-id="68faa-106">GUIX Studio のデザインは、拡張子が .gxp の GUIX Studio プロジェクト ファイルに保存され、メンテナンスされます。</span><span class="sxs-lookup"><span data-stu-id="68faa-106">GUIX Studio designs are saved and maintained in a GUIX Studio project file, which has the extension .gxp.</span></span> <span data-ttu-id="68faa-107">ターゲット上でデザインを実行する準備が整うと、GUIX Studio によって、必要なすべての UI 情報とコードを含む C コードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="68faa-107">When your design is ready for execution on the target, GUIX Studio generates C code that contains all the necessary UI information and code.</span></span>

## <a name="guix-studio-requirements"></a><span data-ttu-id="68faa-108">GUIX Studio の要件</span><span class="sxs-lookup"><span data-stu-id="68faa-108">GUIX Studio Requirements</span></span>

<span data-ttu-id="68faa-109">Microsoft の GUIX Studio が正常に機能するためには、*Windows XP* (またはそれ以降) が必要です。</span><span class="sxs-lookup"><span data-stu-id="68faa-109">In order to function properly, Microsoft's GUIX Studio requires *Windows XP* (or above).</span></span> <span data-ttu-id="68faa-110">システムには、最低 200 MB の RAM、2 GB のハードディスク空き領域、および 256 色で 1024x768 の最小表示が必要です。</span><span class="sxs-lookup"><span data-stu-id="68faa-110">The system should have a minimum of 200MB of RAM, 2GB of available hard-disk space, and a minimum display of 1024x768 with 256 colors.</span></span> <span data-ttu-id="68faa-111">また、埋め込みアプリケーションは、*ThreadX/GUIX V6.0* 以降で実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="68faa-111">In addition, the embedded application must be running on *ThreadX/GUIX V6.0* or later.</span></span>

<span data-ttu-id="68faa-112">埋め込み UI アプリケーションをスタンドアロンの Microsoft Windows 実行可能ファイルとしてビルドして実行できるようにする場合は、Microsoft Windows の実行可能ファイルを生成するために C ソース コードをコンパイルできるコンパイラまたはビルド環境も必要になります。</span><span class="sxs-lookup"><span data-stu-id="68faa-112">If you would like to be able to build and run the embedded UI application as a stand-alone Microsoft Windows executable, you will also need a compiler or build environment capable of compiling C source code to produce a Microsoft Windows executable.</span></span> <span data-ttu-id="68faa-113">GUIX Studio に含まれる評価パッケージには、Visual Studio 2019 と互換性のあるプロジェクト ファイルと、提供されている各サンプル アプリケーションのソリューションも含まれています。</span><span class="sxs-lookup"><span data-stu-id="68faa-113">The evaluation package included with GUIX Studio also includes Visual Studio 2019 compatible project files and solutions for each of the provided example applications.</span></span> <span data-ttu-id="68faa-114">別のコンパイラを使用している場合は、独自のプロジェクト ファイルを作成するか、サンプル アプリケーションをビルドするためにファイルを作成するか、 https://aka.ms/azrtos-support でサポートにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="68faa-114">If you are using a different compiler, you will need to create your own project files or make files for the purposes of building your example applications, or contact support at https://aka.ms/azrtos-support.</span></span>

## <a name="guix-studio-constraints"></a><span data-ttu-id="68faa-115">GUIX Studio の制約</span><span class="sxs-lookup"><span data-stu-id="68faa-115">GUIX Studio Constraints</span></span>

<span data-ttu-id="68faa-116">GUIX Studio UI デザイン ツールには、次のようないくつかの制約があります。</span><span class="sxs-lookup"><span data-stu-id="68faa-116">The GUIX Studio UI design tool has several constraints, as follows:</span></span>

- <span data-ttu-id="68faa-117">プロジェクトあたり最大 4 つの表示。</span><span class="sxs-lookup"><span data-stu-id="68faa-117">A maximum of 4 displays per project.</span></span>
- <span data-ttu-id="68faa-118">GUIX Studio プロジェクトあたり最大 10 万のウィジェット。</span><span class="sxs-lookup"><span data-stu-id="68faa-118">A maximum of 100,000 widgets per GUIX Studio project.</span></span>
- <span data-ttu-id="68faa-119">最大 10 万の異なるリソース (色、フォント、ピクセルマップ、文字列など)。</span><span class="sxs-lookup"><span data-stu-id="68faa-119">A maximum of 100,000 distinct resources, e.g., colors, fonts, pixelmaps, strings, etc.</span></span>