---
title: 第 1 章 - Azure RTOS NetX Duo LWM2M クライアントの概要
description: この章では、マシン プロトコル クライアントに対する Azure RTOS NetX Duo ライトウェイト マシンの概要について説明します。
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 12f13c154668b3cadfae0924e59b55631dc27424
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810772"
---
# <a name="chapter-1--introduction-to-lwm2m-client"></a><span data-ttu-id="a0723-103">第 1 章 - LWM2M クライアントの概要</span><span class="sxs-lookup"><span data-stu-id="a0723-103">Chapter 1  Introduction to LWM2M Client</span></span>

<span data-ttu-id="a0723-104">Azure RTOS NetX Duo LWM2M クライアント プロトコルは、マシン プロトコル標準に対してライトウェイト マシンのクライアント部分を実装します。</span><span class="sxs-lookup"><span data-stu-id="a0723-104">The Azure RTOS NetX Duo LWM2M Client Protocol implements the client part of the Lightweight Machine to Machine protocol standard.</span></span> <span data-ttu-id="a0723-105">(LWM2M 1.0-20170208A)</span><span class="sxs-lookup"><span data-stu-id="a0723-105">(LWM2M 1.0-20170208A)</span></span>

## <a name="netx-lwm2m-client-requirements"></a><span data-ttu-id="a0723-106">NetX LWM2M クライアントの要件</span><span class="sxs-lookup"><span data-stu-id="a0723-106">NetX LWM2M Client Requirements</span></span>

<span data-ttu-id="a0723-107">LWM2M クライアント ランタイム ライブラリを正しく機能させるには、NetX IP インスタンスが既に作成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0723-107">In order to function properly, the LWM2M Client run-time library requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="a0723-108">NetX LWM2M クライアント パッケージには、それ以上の要件はありません。</span><span class="sxs-lookup"><span data-stu-id="a0723-108">The NetX LWM2M Client package has no further requirements.</span></span>

## <a name="netx-lwm2m-client-rfcs"></a><span data-ttu-id="a0723-109">NetX LWM2M クライアントの RFC</span><span class="sxs-lookup"><span data-stu-id="a0723-109">NetX LWM2M Client RFCs</span></span>

<span data-ttu-id="a0723-110">LWM2M クライアントは、OMA-TS-LightweightM2M-V1\_0-20170208-A と、制約付きアプリケーション プロトコル (CoAP) に関連する次の RFC に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="a0723-110">LWM2M Client is compliant with OMA-TS-LightweightM2M-V1\_0-20170208-A and the following RFCs related to the Constrained Application Protocol (CoAP).</span></span>

* <span data-ttu-id="a0723-111">RFC 7252 制約付きアプリケーション プロトコル (CoAP)</span><span class="sxs-lookup"><span data-stu-id="a0723-111">RFC 7252 The Constrained Application Protocol (CoAP)</span></span>

* <span data-ttu-id="a0723-112">RFC 7641 制約付きアプリケーション プロトコル (CoAP) でのリソースの監視</span><span class="sxs-lookup"><span data-stu-id="a0723-112">RFC 7641 Observing Resources in the Constrained Application Protocol (CoAP)</span></span>

* <span data-ttu-id="a0723-113">RFC 6690 制約付き RESTful 環境 (CoRE) リンク形式</span><span class="sxs-lookup"><span data-stu-id="a0723-113">RFC 6690 Constrained RESTful Environments (CoRE) Link Format</span></span>

<span data-ttu-id="a0723-114">詳細については、「[OMA-TS-LightweightM2M-V1\_0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0723-114">For more information, please see [OMA-TS-LightweightM2M-V1\_0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf).</span></span>