---
title: 第 1 章 - Azure RTOS NetX Duo BSD の概要
description: BSD Socket API の Compliancy Wrapper では、基本的な BSD Socket API 呼び出しの一部を一定の制限付きでサポートしており、その基盤では Azure RTOS NetX Duo のプリミティブが利用されています。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e89018dffd2f9f9065efab2ecabdf4364c4f89a3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810976"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-bsd"></a><span data-ttu-id="c8217-103">第 1 章 - Azure RTOS NetX Duo BSD の概要</span><span class="sxs-lookup"><span data-stu-id="c8217-103">Chapter 1 - Introduction to Azure RTOS NetX Duo BSD</span></span>

<span data-ttu-id="c8217-104">BSD Socket API の Compliancy Wrapper では、基本的な BSD Socket API 呼び出しの一部を一定の制限付きでサポートしており、その基盤では Azure RTOS NetX Duo のプリミティブが利用されています。</span><span class="sxs-lookup"><span data-stu-id="c8217-104">The BSD Socket API Compliancy Wrapper supports some of the basic BSD Socket API calls, with some limitations and utilizes Azure RTOS NetX Duo primitives underneath.</span></span>

## <a name="bsd-socket-api-compliancy-wrapper-source"></a><span data-ttu-id="c8217-105">BSD Socket API の Compliancy Wrapper のソース</span><span class="sxs-lookup"><span data-stu-id="c8217-105">BSD Socket API Compliancy Wrapper Source</span></span>

<span data-ttu-id="c8217-106">このラッパーのソース コードは単純さのために設計されており、2 つのファイルで構成されています。つまり、*nxd_bsd.h* と *nxd_bsd.c* です。</span><span class="sxs-lookup"><span data-stu-id="c8217-106">The Wrapper source code is designed for simplicity and is comprised of two files, namely *nxd_bsd.h* and *nxd_bsd.c*.</span></span> <span data-ttu-id="c8217-107">*nxd_bsd.h* ファイルでは、BSD Socket API Wrapper の必要な定数とサブルーチン プロトタイプがすべて定義されています。一方 *nxd_bsd.c* には、BSD Socket API と互換性がある実際のソース コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c8217-107">The *nxd_bsd.h* file defines all the necessary BSD Socket API wrapper constants and subroutine prototypes, while *nxd_bsd.c* contains the actual BSD Socket API compatibility source code.</span></span> <span data-ttu-id="c8217-108">ラッパーのこれらのソース ファイルは、すべての NetX Duo サポート パッケージに共通です。</span><span class="sxs-lookup"><span data-stu-id="c8217-108">These Wrapper source files are common to all NetX Duo support packages.</span></span>

<span data-ttu-id="c8217-109">パッケージは次のもので構成されます。</span><span class="sxs-lookup"><span data-stu-id="c8217-109">The package consists of:</span></span>

- <span data-ttu-id="c8217-110">**nxd_bsd.c**: ラッパーのソース コード</span><span class="sxs-lookup"><span data-stu-id="c8217-110">**nxd_bsd.c**: Wrapper source code</span></span>
- <span data-ttu-id="c8217-111">**nxd_bsd.h**: メインのヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="c8217-111">**nxd_bsd.h**: Main header file</span></span>

<span data-ttu-id="c8217-112">サンプル デモ プログラム:</span><span class="sxs-lookup"><span data-stu-id="c8217-112">Sample demo programs:</span></span>

- <span data-ttu-id="c8217-113">**bsd_demo_udp.c**: *2 つの UDP ピアを使用したデモ (IPv4 のみ)*</span><span class="sxs-lookup"><span data-stu-id="c8217-113">**bsd_demo_udp.c**: *Demo with two UDP peers (IPv4 only)*</span></span>
- <span data-ttu-id="c8217-114">**bsd_demo_tcp.c**: *1 つの TCP サーバーとクライアントを使用したデモ*</span><span class="sxs-lookup"><span data-stu-id="c8217-114">**bsd_demo_tcp.c**: *Demo with a single TCP server and client*</span></span>
- <span data-ttu-id="c8217-115">**bsd_demo_raw.c**: *2 つの RAW ピアを使用したデモ*</span><span class="sxs-lookup"><span data-stu-id="c8217-115">**bsd_demo_raw.c**: *Demo with two RAW peers*</span></span>