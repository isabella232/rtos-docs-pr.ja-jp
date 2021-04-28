---
title: チャプター 1 - Azure RTOS NetX BSD の概要
description: Azure RTOS NetX BSD Sockets API Compliancy Wrapper では、基本的な BSD Sockets API の一部を制限付きでサポートしています。その処理には NetX の基本操作を使用しています。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fce781ac97ae75c4148614453eeb35c3064f8849
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810424"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-bsd"></a><span data-ttu-id="1af3a-103">チャプター 1 - Azure RTOS NetX BSD の概要</span><span class="sxs-lookup"><span data-stu-id="1af3a-103">Chapter 1 - Introduction to Azure RTOS NetX BSD</span></span>

<span data-ttu-id="1af3a-104">NetX BSD Sockets API Compliancy Wrapper では、基本的な BSD Sockets API の一部を制限付きでサポートしています。その処理には NetX の基本操作を使用しています。</span><span class="sxs-lookup"><span data-stu-id="1af3a-104">The NetX BSD Sockets API Compliancy Wrapper supports some of the basic BSD Sockets API calls with some limitations and utilizes NetX primitives underneath.</span></span> <span data-ttu-id="1af3a-105">この BSD Sockets API 互換レイヤーでは NetX の基本操作を利用し、NetX の基本的なエラー チェックを無視するため、このラッパーは通常の BSD 実装と同等か、それよりも少し高速です。</span><span class="sxs-lookup"><span data-stu-id="1af3a-105">This BSD Sockets API compatibility layer should perform as fast or slightly faster than typical BSD implementations, since this Wrapper utilizes internal NetX primitives and bypasses basic NetX error checking.</span></span>

## <a name="bsd-sockets-api-compliancy-wrapper-source"></a><span data-ttu-id="1af3a-106">BSD Sockets API Compliancy Wrapper のソース</span><span class="sxs-lookup"><span data-stu-id="1af3a-106">BSD Sockets API Compliancy Wrapper Source</span></span>

<span data-ttu-id="1af3a-107">この BSD ラッパーのソース コードはシンプルさを重視しており、2 つのファイル *nx_bsd.h* と *nx_bsd.c* のみで構成されます。</span><span class="sxs-lookup"><span data-stu-id="1af3a-107">The BSD Wrapper source code is designed for simplicity and is comprised of only two files, *nx_bsd.h* and *nx_bsd.c*.</span></span> <span data-ttu-id="1af3a-108">*nx_bsd.h* ファイルでは、BSD Sockets API Wrapper の必要な定数とサブルーチン プロトタイプをすべて定義しています。*nx_bsd.c* は BSD Sockets API 互換レイヤーのソース コードそのものです。</span><span class="sxs-lookup"><span data-stu-id="1af3a-108">The *nx_bsd.h* file defines all the necessary BSD Sockets API Wrapper constants and subroutine prototypes, while *nx_bsd.c* contains the actual BSD Sockets API compatibility source code.</span></span> <span data-ttu-id="1af3a-109">これらのBSD ラッパーソース ファイルは、すべての NetX サポート パッケージに共通です。</span><span class="sxs-lookup"><span data-stu-id="1af3a-109">These BSD Wrapper source files are common to all NetX support packages.</span></span>

<span data-ttu-id="1af3a-110">パッケージは次のもので構成されます。</span><span class="sxs-lookup"><span data-stu-id="1af3a-110">The package consists of:</span></span>

- <span data-ttu-id="1af3a-111">**nx_bsd.c**: ラッパーのソース コード</span><span class="sxs-lookup"><span data-stu-id="1af3a-111">**nx_bsd.c**: Wrapper source code</span></span>
- <span data-ttu-id="1af3a-112">**nx_bsd.h**: メインのヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="1af3a-112">**nx_bsd.h**: Main header file</span></span>

<span data-ttu-id="1af3a-113">サンプル デモ プログラム:</span><span class="sxs-lookup"><span data-stu-id="1af3a-113">Sample demo programs:</span></span>

- <span data-ttu-id="1af3a-114">**bsd_demo_tcp.c**: *TCP サーバーおよびクライアントを 1 つずつ使用するデモ*</span><span class="sxs-lookup"><span data-stu-id="1af3a-114">**bsd_demo_tcp.c**: *Demo with a single TCP server and client*</span></span>
- <span data-ttu-id="1af3a-115">**bsd_demo_udp.c**: *UDP クライアント 2 つと UDP サーバー 1 つを使用するデモ*</span><span class="sxs-lookup"><span data-stu-id="1af3a-115">**bsd_demo_udp.c**: *Demo with two UDP clients and a UDP server*</span></span>
