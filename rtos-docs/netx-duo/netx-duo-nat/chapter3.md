---
title: 第 3 章 - NAT 構成オプション
description: 次の一覧に、すべてのオプションとその機能について詳しく説明します
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9c10d6f0d2f36d2794ab1229081799f0032cada8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810676"
---
# <a name="chapter-3---nat-configuration-options"></a><span data-ttu-id="b85a9-103">第 3 章 - NAT 構成オプション</span><span class="sxs-lookup"><span data-stu-id="b85a9-103">Chapter 3 - NAT configuration options</span></span>

<span data-ttu-id="b85a9-104">NetX Duo NAT API の構成可能なオプションは *nx_nat.h* に含まれていますが、最初の **NX_DISABLE_ERROR_CHECKING** は例外で *nx_nat.c* に含まれています。</span><span class="sxs-lookup"><span data-stu-id="b85a9-104">Configurable options for the NetX Duo NAT API can be found in *nx_nat.h* with the exception of the first one, **NX_DISABLE_ERROR_CHECKING** which is found in *nx_nat.c*.</span></span> <span data-ttu-id="b85a9-105">次の一覧に、すべてのオプションとその機能について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="b85a9-105">The following list includes all options and their function described in detail:</span></span>

- <span data-ttu-id="b85a9-106">**NX_NAT_DISABLE_ERROR_CHECKING**: このオプションを定義すると、基本的な NAT エラー チェックが削除されます。</span><span class="sxs-lookup"><span data-stu-id="b85a9-106">**NX_NAT_DISABLE_ERROR_CHECKING** This option if defined removes the basic NAT error checking.</span></span> <span data-ttu-id="b85a9-107">通常は、アプリケーションがデバッグされた後に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b85a9-107">It is typically used after the application has been debugged.</span></span> <span data-ttu-id="b85a9-108">既定の NetX Duo NAT の状態が定義されます (有効)。</span><span class="sxs-lookup"><span data-stu-id="b85a9-108">The default NetX Duo NAT status is defined (enabled).</span></span>
- <span data-ttu-id="b85a9-109">**NX_NAT_ENABLE_REPLACEMENT**: このオプションを定義すると、NAT キャッシュがいっぱいになったときに自動置換が有効になります。</span><span class="sxs-lookup"><span data-stu-id="b85a9-109">**NX_NAT_ENABLE_REPLACEMENT** This option if defined enables automatic replacement when NAT cache is full.</span></span>
  > [!NOTE]
  > <span data-ttu-id="b85a9-110">最も古い非 TCP セッションのみを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b85a9-110">Only replace the oldest non-TCP session.</span></span>
- <span data-ttu-id="b85a9-111">**NX_NAT_MIN_ENTRY_COUNT**: このオプションは、変換エントリの最小数を設定します。</span><span class="sxs-lookup"><span data-stu-id="b85a9-111">**NX_NAT_MIN_ENTRY_COUNT** This option sets the minimum count for translation entry.</span></span> <span data-ttu-id="b85a9-112">既定値は 3 です。</span><span class="sxs-lookup"><span data-stu-id="b85a9-112">The default count is 3.</span></span>
- <span data-ttu-id="b85a9-113">**NX_NAT_TCP_SESSION_TIMEOUT**: このオプションは、TCP セッションの変換エントリのタイムアウトを設定します。</span><span class="sxs-lookup"><span data-stu-id="b85a9-113">**NX_NAT_TCP_SESSION_TIMEOUT** This option sets the timeout for translation entry for TCP Sessions.</span></span> <span data-ttu-id="b85a9-114">既定のタイムアウトは 24 時間です。</span><span class="sxs-lookup"><span data-stu-id="b85a9-114">The default timeout is 24 hours.</span></span>
- <span data-ttu-id="b85a9-115">**NX_NAT_NON_TCP_SESSION_TIMEOUT**: このオプションは、非 TCP セッションの変換エントリのタイムアウトを設定します。</span><span class="sxs-lookup"><span data-stu-id="b85a9-115">**NX_NAT_NON_TCP_SESSION_TIMEOUT** This option sets the timeout for translation entry for non-TCP Sessions.</span></span> <span data-ttu-id="b85a9-116">既定のタイムアウトは 240 秒です。</span><span class="sxs-lookup"><span data-stu-id="b85a9-116">The default timeout is 240 seconds.</span></span>
- <span data-ttu-id="b85a9-117">**NX_NAT_START_TCP_PORT**: このオプションは、送信 TCP パケットを割り当てる未使用の TCP ポートを検索する際の開始値を設定します。</span><span class="sxs-lookup"><span data-stu-id="b85a9-117">**NX_NAT_START_TCP_PORT** This option sets the starting value for finding an unused TCP port to assign an outbound TCP packet.</span></span> <span data-ttu-id="b85a9-118">既定値は 20000 です。</span><span class="sxs-lookup"><span data-stu-id="b85a9-118">The default value is 20000.</span></span>
- <span data-ttu-id="b85a9-119">**NX_NAT_END_TCP_PORT**: このオプションは、送信 TCP パケットを割り当てる TCP ポートの上限を設定します。</span><span class="sxs-lookup"><span data-stu-id="b85a9-119">**NX_NAT_END_TCP_PORT** This option sets the upperlimit of TCP port to assign an outbound TCP packet.</span></span> <span data-ttu-id="b85a9-120">既定値は 30,000 です。</span><span class="sxs-lookup"><span data-stu-id="b85a9-120">The default value is 30000.</span></span>
- <span data-ttu-id="b85a9-121">**NX_NAT_START_UDP_PORT**: このオプションは、送信 UDP パケットを割り当てる未使用の UDP ポートを検索する際の開始値を設定します。</span><span class="sxs-lookup"><span data-stu-id="b85a9-121">**NX_NAT_START_UDP_PORT** This option sets the starting value for finding an unused UDP port to assign an outbound UDP packet.</span></span> <span data-ttu-id="b85a9-122">既定値は 20000 です。</span><span class="sxs-lookup"><span data-stu-id="b85a9-122">The default value is 20000.</span></span>
- <span data-ttu-id="b85a9-123">**NX_NAT_END_UDP_PORT**: このオプションは、送信 UDP パケットを割り当てる UDP ポートの上限を設定します。</span><span class="sxs-lookup"><span data-stu-id="b85a9-123">**NX_NAT_END_UDP_PORT** This option sets the upperlimit of UDP port to assign an outbound UDP packet.</span></span> <span data-ttu-id="b85a9-124">既定値は 30,000 です。</span><span class="sxs-lookup"><span data-stu-id="b85a9-124">The default value is 30000.</span></span>
- <span data-ttu-id="b85a9-125">**NX_NAT_START_ICMP_QUERY_ID**: このオプションは、送信 ICMP クエリ パケットを割り当てる未使用のクエリ ID を検索する際の開始値を設定します。</span><span class="sxs-lookup"><span data-stu-id="b85a9-125">**NX_NAT_START_ICMP_QUERY_ID** This option sets the starting value for finding an unused query ID to assign an outbound ICMP query packet.</span></span> <span data-ttu-id="b85a9-126">既定値は 20000 です。</span><span class="sxs-lookup"><span data-stu-id="b85a9-126">The default value is 20000.</span></span>
- <span data-ttu-id="b85a9-127">**NX_NAT_START_ICMP_QUERY_ID**: このオプションは、送信 ICMP クエリ パケットを割り当てる未使用のクエリ ID の上限を設定します。</span><span class="sxs-lookup"><span data-stu-id="b85a9-127">**NX_NAT_END_ICMP_QUERY_ID** This option sets the upperlimit of query IDs to assign an outbound ICMP query packet.</span></span> <span data-ttu-id="b85a9-128">既定値は 30,000 です。</span><span class="sxs-lookup"><span data-stu-id="b85a9-128">The default value is 30000.</span></span>
