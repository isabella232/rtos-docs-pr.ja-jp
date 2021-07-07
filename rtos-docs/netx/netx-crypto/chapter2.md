---
title: 第 2 章 - Azure RTOS NetX Crypto のインストールと使用
description: この章では、NetX Crypto コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3323af5eaf31ac9c167966522df6477c82e99fdc
ms.sourcegitcommit: c98e5360c9cedbe773af5a44f5163f563c85b570
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2021
ms.locfileid: "110337008"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a><span data-ttu-id="9ce82-103">第 2 章 - Azure RTOS NetX Crypto のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="9ce82-103">Chapter 2 - Installation and use of Azure RTOS NetX Crypto</span></span>

<span data-ttu-id="9ce82-104">このチャプターでは、Azure RTOS NetX コンポーネントのインストール、セットアップ、使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ce82-104">This chapter describes installation, setup, and usage of the Azure RTOS NetX Crypto component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="9ce82-105">製品の配布</span><span class="sxs-lookup"><span data-stu-id="9ce82-105">Product Distribution</span></span>

<span data-ttu-id="9ce82-106">Azure RTOS NetX Crypto は [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="9ce82-106">Azure RTOS NetX Crypto is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="9ce82-107">パッケージに含まれているソース ファイル、インクルード ファイル、このドキュメントを含む PDF ファイルを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="9ce82-107">The package includes source files, include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="9ce82-108">**nx_crypto.h**: NetX Crypto モジュールのパブリック API ヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="9ce82-108">**nx_crypto.h**: Public API header file NetX Crypto module</span></span>
- <span data-ttu-id="9ce82-109">**nx_crypto_\*.c/h**: NetX Crypto の C/H ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="9ce82-109">**nx_crypto_\*.c/h**: C/H Source files for NetX Crypto</span></span>
- <span data-ttu-id="9ce82-110">**nx_crypto_port.h**: 開発ツールおよびターゲットに固有のデータ定義と構造体のすべてが含まれる C ヘッダー ファイル。</span><span class="sxs-lookup"><span data-stu-id="9ce82-110">**nx_crypto_port.h**: C header file containing all development-tool and target specific data definitions and structures.</span></span>
- <span data-ttu-id="9ce82-111">**NetX_Crypto_User_Guide.pdf**: NetX Crypto モジュールについての PDF の説明。</span><span class="sxs-lookup"><span data-stu-id="9ce82-111">**NetX_Crypto_User_Guide.pdf**: PDF description of NetX Crypto Module.</span></span>

## <a name="netx-crypto-installation"></a><span data-ttu-id="9ce82-112">NetX Crypto のインストール</span><span class="sxs-lookup"><span data-stu-id="9ce82-112">NetX Crypto Installation</span></span>

<span data-ttu-id="9ce82-113">前述したディストリビューション全体が、**crypto_libraries** ディレクトリに収録されています。このディレクトリは、NetX Duo リポジトリのルート レベルにあります。</span><span class="sxs-lookup"><span data-stu-id="9ce82-113">The entire distribution mentioned previously is available in **crypto_libraries** directory, present at root level of NetX Duo repository.</span></span>

<span data-ttu-id="9ce82-114">NetX Crypto を使用するためには、前述のディストリビューション全体を、NetX がインストールされているのと同じディレクトリ レベルにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ce82-114">In order to use NetX Crypto, the entire distribution mentioned previously should be copied to the same directory level where NetX is installed.</span></span> <span data-ttu-id="9ce82-115">たとえば、NetX がディレクトリ "\threadx\arm7\NetX" にインストールされている場合は、nx_crypto *.*</span><span class="sxs-lookup"><span data-stu-id="9ce82-115">For example, if NetX is installed in the directory "\threadx\arm7\NetX" then the nx_crypto *.*</span></span> <span data-ttu-id="9ce82-116">ディレクトリを "\threadx\arm7\NetXCrypto" にコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ce82-116">directories should be copied into "\threadx\arm7\NetXCrypto".</span></span>

<span data-ttu-id="9ce82-117">NetX Crypto をスタンドアロン モードで使用するには、前述したディストリビューション全体をアプリケーション プロジェクトにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ce82-117">For NetX Crypto to be used in standalone mode, the entire distribution mentioned previously should be copied to the application project.</span></span> <span data-ttu-id="9ce82-118">たとえば、**crypto_libraries** ディレクトリをアプリケーション プロジェクトにコピーするか、**crypto_libraries** ディレクトリを含むライブラリ プロジェクトを作成して、アプリケーション プロジェクトにリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ce82-118">For example **crypto_libraries** directory should be copied to the application project or a library project with **crypto_libraries** directory should be created and linked to the application project.</span></span> 

## <a name="using-netx-crypto"></a><span data-ttu-id="9ce82-119">NetX Crypto の使用</span><span class="sxs-lookup"><span data-stu-id="9ce82-119">Using NetX Crypto</span></span>

<span data-ttu-id="9ce82-120">アプリケーション コードには *nx_crypto.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ce82-120">The application code must include the *nx_crypto.h*.</span></span>  <span data-ttu-id="9ce82-121">*nx_crypto.h* をインクルードすると、このガイドで後述する NetX Crypto 関数呼び出しを、アプリケーション コードで行えるようになります。</span><span class="sxs-lookup"><span data-stu-id="9ce82-121">Once *nx_crypto.h* is included, the application code is then able to make the NetX Crypto function calls specified later in this guide.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="9ce82-122">構成オプション</span><span class="sxs-lookup"><span data-stu-id="9ce82-122">Configuration Options</span></span>

<span data-ttu-id="9ce82-123">NetX Crypto のビルド時にはいくつかの構成オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="9ce82-123">There are several configuration options for building NetX Crypto.</span></span> <span data-ttu-id="9ce82-124">以下に、すべてのオプションの一覧と、それぞれの詳細な説明を示します。</span><span class="sxs-lookup"><span data-stu-id="9ce82-124">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="9ce82-125">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: このオプションが定義されている場合、予期される最大の RSA モジュラスがビット単位で示されます。</span><span class="sxs-lookup"><span data-stu-id="9ce82-125">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: Defined, this option gives the maximum RSA modulus expected, in bits.</span></span> <span data-ttu-id="9ce82-126">4096 ビット モジュラスの既定値は 4096 です。</span><span class="sxs-lookup"><span data-stu-id="9ce82-126">The default value is 4096 for a 4096-bit modulus.</span></span> <span data-ttu-id="9ce82-127">他に 3072、2048、または 1024 の値を指定できます (推奨されません)。</span><span class="sxs-lookup"><span data-stu-id="9ce82-127">Other values can be 3072, 2048, or 1024 (not recommended).</span></span>
- <span data-ttu-id="9ce82-128">**NX_CRYPTO_SELF_TEST**: 定義されていると場合、NetX Crypto モジュールの自己テストが有効になります。</span><span class="sxs-lookup"><span data-stu-id="9ce82-128">**NX_CRYPTO_SELF_TEST**: Defined, enables self tests for NetX Crypto module.</span></span> <span data-ttu-id="9ce82-129">**NX_CRYPTO_FIPS** シンボルは非推奨となり、名前が **NX_CRYPTO_SELF_TEST** に変更されました。</span><span class="sxs-lookup"><span data-stu-id="9ce82-129">**NX_CRYPTO_FIPS** symbol is now deprecated and renamed to **NX_CRYPTO_SELF_TEST**</span></span>
- <span data-ttu-id="9ce82-130">**NX_CRYPTO_STANDALONE_ENABLE**: 定義されている場合、NetX Crypto をスタンドアロン モード (Azure RTOS なし) で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9ce82-130">**NX_CRYPTO_STANDALONE_ENABLE**: Defined enables NetX Crypto to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="9ce82-131">既定では、このシンボルは定義されません。</span><span class="sxs-lookup"><span data-stu-id="9ce82-131">By default this symbol is not defined.</span></span>
