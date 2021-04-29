---
title: 第 1 章 - Azure RTOS NetX Duo mDNS/DNS-SD の概要
description: Azure RTOS NetX Duo mDNS/DNS-SD は、従来の DNS サービスを強化します。
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b46539ee4d502fa4c90fb3392e25cd3bee40dc5b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810742"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mdnsdns-sd"></a><span data-ttu-id="37e92-103">第 1 章 - Azure RTOS NetX Duo mDNS/DNS-SD の概要</span><span class="sxs-lookup"><span data-stu-id="37e92-103">Chapter 1 - Introduction to Azure RTOS NetX Duo mDNS/DNS-SD</span></span>

<span data-ttu-id="37e92-104">mDNS と DNS-SD は、従来の DNS サービスを強化するように設計されたプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="37e92-104">The mDNS and DNS-SD are protocols designed to augment the traditional DNS service.</span></span> <span data-ttu-id="37e92-105">mDNS は、ホスト名とサービス検索をローカル ネットワーク上のノードに提供します。</span><span class="sxs-lookup"><span data-stu-id="37e92-105">mDNS provides host name and service lookup to the nodes on the local network.</span></span> <span data-ttu-id="37e92-106">各ノードでは、提供するサービスを IPv4 または IPv6 マルチキャスト チャネルを使用してその近隣ノードにアナウンスし、近隣からのクエリに応答し、アプリケーションに代わってクエリを送信します。</span><span class="sxs-lookup"><span data-stu-id="37e92-106">Each node uses IPv4 or IPv6 multicast channel to announce services it offers to its neighbors, responds to queries from its neighbors, and sends queries on behave of its applications.</span></span> <span data-ttu-id="37e92-107">設計上、mDNS は分散環境で動作するため、集中管理されたサービスが排除されます。</span><span class="sxs-lookup"><span data-stu-id="37e92-107">By design, mDNS operates in a distributed environment, thus eliminates a centralized serve.</span></span>

<span data-ttu-id="37e92-108">DNS-SD は、mDNS の上位に構築されます。</span><span class="sxs-lookup"><span data-stu-id="37e92-108">DNS-SD is built on top of mDNS.</span></span> <span data-ttu-id="37e92-109">DNS-SD を使用すると、ノードが提供するサービスをローカル ネットワークにアナウンスしたり、ローカル ネット ワーク上の他のノードによって提供されるサービスを探索したりできます。</span><span class="sxs-lookup"><span data-stu-id="37e92-109">DNS-SD allows nodes to announce services they provide to the local network or to discover services offered by other nodes on the local network.</span></span> <span data-ttu-id="37e92-110">このドキュメント全体で、*mDNS* という用語は、mDNS 仕様と DNS-SD 仕様の両方をカバーするサービスを指します。</span><span class="sxs-lookup"><span data-stu-id="37e92-110">Throughout the document, the term *mDNS* refers to the services that cover both the mDNS specification and the DNS-SD specification.</span></span>

## <a name="mdns-standard"></a><span data-ttu-id="37e92-111">mDNS 標準</span><span class="sxs-lookup"><span data-stu-id="37e92-111">mDNS Standard</span></span>

<span data-ttu-id="37e92-112">NetX Duo mDNS/DNS-SD の実装は、次の RFC に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="37e92-112">NetX Duo mDNS/DNS-SD implementation conforms to the following RFCs:</span></span>

- <span data-ttu-id="37e92-113">RFC 6762: mDNS 仕様</span><span class="sxs-lookup"><span data-stu-id="37e92-113">RFC 6762: mDNS Specification</span></span>
- <span data-ttu-id="37e92-114">RFC 6763: DNS-SD 仕様</span><span class="sxs-lookup"><span data-stu-id="37e92-114">RFC 6763: DNS-SD Specification</span></span>