---
title: 第 1 章 - Azure RTOS NetX PPPoE クライアントの概要
description: この章では、Azure RTOS NetX PPPoE モジュールの詳細について説明します。
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bbf1e064bb38754bd67b279a0fd60d46d3d6d557
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811459"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pppoe-client"></a><span data-ttu-id="3f423-103">第 1 章 - Azure RTOS NetX PPPoE クライアントの概要</span><span class="sxs-lookup"><span data-stu-id="3f423-103">Chapter 1 - Introduction to Azure RTOS NetX PPPoE Client</span></span>

<span data-ttu-id="3f423-104">ホスト で PPP over Ethernet (PPPoE) を使用することにより、従来の文字ベースのシリアル回線通信ではなく、イーサネット経由で PPP サーバーに接続できます。</span><span class="sxs-lookup"><span data-stu-id="3f423-104">PPP over Ethernet (PPPoE) allows hosts to connect to PPP server via Ethernet instead of the traditional character-based serial line communication.</span></span>  <span data-ttu-id="3f423-105">PPPoE の技術的な詳細については、RFC 2516 の PPP over Ethernet (PPPoE) を送信する方法に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f423-105">The technical details of PPPoE are described in RFC 2516:  A Method for Transmitting PPP over Ethernet (PPPoE).</span></span> <span data-ttu-id="3f423-106">このドキュメントでは、Azure RTOS NetX PPPoE モジュールの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="3f423-106">This document focuses on the details of  Azure RTOS NetX PPPoE module.</span></span>

<span data-ttu-id="3f423-107">イーサネット経由のポイント ツー ポイント接続を提供するには、各 PPP セッションでリモート ピアのイーサネット アドレスを認識し、一意のセッション識別子を確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f423-107">To provide a point-to-point connection over Ethernet, each PPP session must learn the Ethernet address of the remote peer, as well as establish a unique session identifier.</span></span>

<span data-ttu-id="3f423-108">RFC 2516 によれば、PPPoE は、検出ステージと PPPoE セッション ステージという 2 つのステージで構成されます。</span><span class="sxs-lookup"><span data-stu-id="3f423-108">According to RFC 2516, PPPoE consists of two stages: the Discovery stage, and PPPoE Session stage.</span></span> <span data-ttu-id="3f423-109">ホスト (クライアント) で PPP セッションを開始するときは、最初に、検出を実行して PPPoE サーバーを見つける必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f423-109">When a host (client) wishes to start a PPP session, it must first perform Discovery to find PPPoE server.</span></span> <span data-ttu-id="3f423-110">また、このステップにより、サーバーとクライアントは互いのイーサネット MAC アドレスと SESSION_ID を識別できます。これは、PPP セッションの残りの部分で使用されます。</span><span class="sxs-lookup"><span data-stu-id="3f423-110">This step also allows the server and the client to identify each other’s Ethernet MAC address and SESSION_ID, which will be used for the rest of the PPP session.</span></span>

<span data-ttu-id="3f423-111">イーサネット フレームは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3f423-111">An Ethernet frame is as follows:</span></span>

![イーサネット フレーム](media/ethernet-frame.png)

<span data-ttu-id="3f423-113">PPPoE のイーサネット ペイロードは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3f423-113">The Ethernet payload for PPPoE is as follows:</span></span>

![イーサネット ペイロード](media/ethernet-payload.png)

## <a name="pppoe-discovery-stage"></a><span data-ttu-id="3f423-115">PPPoE 検出ステージ</span><span class="sxs-lookup"><span data-stu-id="3f423-115">PPPoE Discovery Stage</span></span>

<span data-ttu-id="3f423-116">PPPoE 検出ステージにより、クライアントは、ネットワーク上の使用可能なすべてのサーバーから 1 つのサーバーを選択し、PPP フレーム交換の前にセッションを効率的に作成できます。</span><span class="sxs-lookup"><span data-stu-id="3f423-116">The PPPoE Discovery stage allows clients to select a server from all available servers on the network, effectively to create a session prior to PPP frames being exchanged.</span></span>  <span data-ttu-id="3f423-117">検出ステージの終了時には、クライアントとサーバーの両方が一意のセッション ID に同意し、両方の側がピアの MAC アドレスを認識している必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f423-117">At the end of the discovery stage, both the client and the server shall agree on a unique session ID, and both sides need to know peer’s MAC address.</span></span>

| <span data-ttu-id="3f423-118">検出メッセージ</span><span class="sxs-lookup"><span data-stu-id="3f423-118">Discovery Message</span></span> | <span data-ttu-id="3f423-119">コード</span><span class="sxs-lookup"><span data-stu-id="3f423-119">Code</span></span> | <span data-ttu-id="3f423-120">Direction</span><span class="sxs-lookup"><span data-stu-id="3f423-120">Direction</span></span> |
| ----------------- | ---- | --------- |
| <span data-ttu-id="3f423-121">PPPoE アクティブ検出開始 (PADI)</span><span class="sxs-lookup"><span data-stu-id="3f423-121">PPPoE Active Discovery Initiation (PADI)</span></span> | <span data-ttu-id="3f423-122">0x09</span><span class="sxs-lookup"><span data-stu-id="3f423-122">0x09</span></span> | <span data-ttu-id="3f423-123">クライアントからブロードキャストへ</span><span class="sxs-lookup"><span data-stu-id="3f423-123">From Client to broadcast</span></span> |
| <span data-ttu-id="3f423-124">PPPoE アクティブ検出提供 (PADO)</span><span class="sxs-lookup"><span data-stu-id="3f423-124">PPPoE Active Discovery Offer (PADO)</span></span> | <span data-ttu-id="3f423-125">0x07</span><span class="sxs-lookup"><span data-stu-id="3f423-125">0x07</span></span> | <span data-ttu-id="3f423-126">サーバーからクライアントへ</span><span class="sxs-lookup"><span data-stu-id="3f423-126">From Server to Client</span></span> |
| <span data-ttu-id="3f423-127">PPPoE アクティブ検出要求 (PADR)</span><span class="sxs-lookup"><span data-stu-id="3f423-127">PPPoE Active Discovery Request (PADR)</span></span> | <span data-ttu-id="3f423-128">0x19</span><span class="sxs-lookup"><span data-stu-id="3f423-128">0x19</span></span> | <span data-ttu-id="3f423-129">クライアントからサーバーへ</span><span class="sxs-lookup"><span data-stu-id="3f423-129">From Client to Server</span></span> |
| <span data-ttu-id="3f423-130">PPPOE アクティブ検出セッション確認 (PADS)</span><span class="sxs-lookup"><span data-stu-id="3f423-130">PPPOE Active Discovery Session-confirmation (PADS)</span></span> | <span data-ttu-id="3f423-131">0x65</span><span class="sxs-lookup"><span data-stu-id="3f423-131">0x65</span></span> | <span data-ttu-id="3f423-132">サーバーからクライアントへ</span><span class="sxs-lookup"><span data-stu-id="3f423-132">From Server to Client</span></span> |
| <span data-ttu-id="3f423-133">PPPoE アクティブ検出終了 (PADT)</span><span class="sxs-lookup"><span data-stu-id="3f423-133">PPPoE Active Discovery Terminate (PADT)</span></span> | <span data-ttu-id="3f423-134">0xa7</span><span class="sxs-lookup"><span data-stu-id="3f423-134">0xa7</span></span> | <span data-ttu-id="3f423-135">サーバーまたはクライアントのどちらからでも開始可能</span><span class="sxs-lookup"><span data-stu-id="3f423-135">Can be initiated from either server or client</span></span> |

<span data-ttu-id="3f423-136">すべての検出イーサネット フレームには、値 0x8863 に設定された ETHER_TYPE フィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="3f423-136">All Discovery Ethernet frames have the ETHER_TYPE field set to the value 0x8863.</span></span>

## <a name="pppoe-session-message"></a><span data-ttu-id="3f423-137">PPPoE セッション メッセージ</span><span class="sxs-lookup"><span data-stu-id="3f423-137">PPPoE Session Message</span></span>

<span data-ttu-id="3f423-138">クライアントとサーバーによってセッションが作成された後、PPPoE セッション メッセージとして PPP フレームを転送できます。</span><span class="sxs-lookup"><span data-stu-id="3f423-138">After the client and the server create a session, PPP frames can be transferred as PPPoE Session messages.</span></span>  <span data-ttu-id="3f423-139">セッションの間に、SESSION_ID が変化してはならず、検出ステージの間にサーバーによって割り当てられた値である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f423-139">During a session, the SESSION_ID must not change and must be the value the server assigned during the Discovery stage.</span></span>

<span data-ttu-id="3f423-140">すべての PPPoE セッション イーサネット フレームには、値 0x8864 に設定された ETHER_TYPE フィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="3f423-140">All PPPoE Session Ethernet frames have the ETHER_TYPE field set to the value 0x8864.</span></span>
