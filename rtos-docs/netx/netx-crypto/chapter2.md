---
title: 第 2 章 - Azure RTOS NetX Crypto のインストールと使用
description: この章では、NetX Crypto コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1616667c5efd73229ed69bcd4e5de5f80e5826f9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811633"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a><span data-ttu-id="1539b-103">第 2 章 - Azure RTOS NetX Crypto のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="1539b-103">Chapter 2 - Installation and use of Azure RTOS NetX Crypto</span></span>

<span data-ttu-id="1539b-104">この章では、Azure RTOS NetX Crypto コンポーネントのインストール、設定、使用に関連するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="1539b-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Crypto component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="1539b-105">製品の配布</span><span class="sxs-lookup"><span data-stu-id="1539b-105">Product Distribution</span></span>

<span data-ttu-id="1539b-106">Azure RTOS NetX Crypto は [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="1539b-106">Azure RTOS NetX Crypto is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="1539b-107">パッケージに含まれているソース ファイル、インクルード ファイル、このドキュメントを含む PDF ファイルを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="1539b-107">The package includes source files, include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="1539b-108">**nx_crypto.h**: NetX Crypto モジュールのパブリック API ヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="1539b-108">**nx_crypto.h**: Public API header file NetX Crypto module</span></span>
- <span data-ttu-id="1539b-109">**nx_crypto_\*.c/h**: NetX Crypto の C/H ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="1539b-109">**nx_crypto_\*.c/h**: C/H Source files for NetX Crypto</span></span>
- <span data-ttu-id="1539b-110">**nx_crypto_port.h**: 開発ツールおよびターゲットに固有のデータ定義と構造体のすべてが含まれる C ヘッダー ファイル。</span><span class="sxs-lookup"><span data-stu-id="1539b-110">**nx_crypto_port.h**: C header file containing all development-tool and target specific data definitions and structures.</span></span>
- <span data-ttu-id="1539b-111">**NetX_Crypto_User_Guide.pdf**: NetX Crypto モジュールについての PDF の説明。</span><span class="sxs-lookup"><span data-stu-id="1539b-111">**NetX_Crypto_User_Guide.pdf**: PDF description of NetX Crypto Module.</span></span>

## <a name="netx-crypto-installation"></a><span data-ttu-id="1539b-112">NetX Crypto のインストール</span><span class="sxs-lookup"><span data-stu-id="1539b-112">NetX Crypto Installation</span></span>

<span data-ttu-id="1539b-113">前述したディストリビューション全体が、**crypto_libraries** ディレクトリに収録されています。このディレクトリは、NetX Duo リポジトリのルート レベルにあります。</span><span class="sxs-lookup"><span data-stu-id="1539b-113">The entire distribution mentioned previously is available in **crypto_libraries** directory, present at root level of NetX Duo repository.</span></span>

<span data-ttu-id="1539b-114">NetX Crypto を使用するためには、前述のディストリビューション全体を、NetX がインストールされているのと同じディレクトリ レベルにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1539b-114">In order to use NetX Crypto, the entire distribution mentioned previously should be copied to the same directory level where NetX is installed.</span></span> <span data-ttu-id="1539b-115">たとえば、NetX がディレクトリ "\threadx\arm7\NetX" にインストールされている場合は、nx_crypto *.*</span><span class="sxs-lookup"><span data-stu-id="1539b-115">For example, if NetX is installed in the directory "\threadx\arm7\NetX" then the nx_crypto *.*</span></span> <span data-ttu-id="1539b-116">ディレクトリを "\threadx\arm7\NetXCrypto" にコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1539b-116">directories should be copied into "\threadx\arm7\NetXCrypto".</span></span>

<span data-ttu-id="1539b-117">NetX Crypto をスタンドアロン モードで使用するには、前述したディストリビューション全体をアプリケーション プロジェクトにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1539b-117">For NetX Crypto to be used in standalone mode, the entire distribution mentioned previously should be copied to the application project.</span></span> <span data-ttu-id="1539b-118">たとえば、**crypto_libraries** ディレクトリをアプリケーション プロジェクトにコピーするか、**crypto_libraries** ディレクトリを含むライブラリ プロジェクトを作成して、アプリケーション プロジェクトにリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1539b-118">For example **crypto_libraries** directory should be copied to the application project or a library project with **crypto_libraries** directory should be created and linked to the application project.</span></span> 

## <a name="using-netx-crypto"></a><span data-ttu-id="1539b-119">NetX Crypto の使用</span><span class="sxs-lookup"><span data-stu-id="1539b-119">Using NetX Crypto</span></span>

<span data-ttu-id="1539b-120">NetX Crypto の使用は簡単です。</span><span class="sxs-lookup"><span data-stu-id="1539b-120">Using NetX Crypto is easy.</span></span> <span data-ttu-id="1539b-121">基本的に、アプリケーション コードで *nx_crypto.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1539b-121">Basically, the application code must include the *nx_crypto.h*.</span></span>  <span data-ttu-id="1539b-122">*nx_crypto.h* をインクルードすると、このガイドで後述する NetX Crypto 関数呼び出しを、アプリケーション コードで行えるようになります。</span><span class="sxs-lookup"><span data-stu-id="1539b-122">Once *nx_crypto.h* is included, the application code is then able to make the NetX Crypto function calls specified later in this guide.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="1539b-123">構成オプション</span><span class="sxs-lookup"><span data-stu-id="1539b-123">Configuration Options</span></span>

<span data-ttu-id="1539b-124">NetX Crypto のビルド時にはいくつかの構成オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="1539b-124">There are several configuration options for building NetX Crypto.</span></span> <span data-ttu-id="1539b-125">以下に、すべてのオプションの一覧と、それぞれの詳細な説明を示します。</span><span class="sxs-lookup"><span data-stu-id="1539b-125">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="1539b-126">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: このオプションが定義されている場合、予期される最大の RSA モジュラスがビット単位で示されます。</span><span class="sxs-lookup"><span data-stu-id="1539b-126">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: Defined, this option gives the maximum RSA modulus expected, in bits.</span></span> <span data-ttu-id="1539b-127">4096 ビット モジュラスの既定値は 4096 です。</span><span class="sxs-lookup"><span data-stu-id="1539b-127">The default value is 4096 for a 4096-bit modulus.</span></span> <span data-ttu-id="1539b-128">その他の値として 3072、2048、1024 (非推奨) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1539b-128">Other values can be 3072, 2048, or 1024 (not recommended).</span></span>
- <span data-ttu-id="1539b-129">**NX_CRYPTO_FIPS**: このオプションが定義されている場合、FIPS に準拠した使用のために必要な追加のセキュリティ機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="1539b-129">**NX_CRYPTO_FIPS**: Defined, this option enables extra security features required for FIPS-Compliant usage.</span></span> <span data-ttu-id="1539b-130">このオプションは、FIPS でないビルドに対しては有効になりません。</span><span class="sxs-lookup"><span data-stu-id="1539b-130">This option is not enabled for non-FIPS build.</span></span>
- <span data-ttu-id="1539b-131">**NX_CRYPTO_STANDALONE_ENABLE**: 定義されている場合、NetX Crypto をスタンドアロン モード (Azure RTOS なし) で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1539b-131">**NX_CRYPTO_STANDALONE_ENABLE**: Defined enables NetX Crypto to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="1539b-132">既定では、このシンボルは定義されません。</span><span class="sxs-lookup"><span data-stu-id="1539b-132">By default this symbol is not defined.</span></span>
