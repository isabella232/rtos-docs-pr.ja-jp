---
title: 第 1 章 - Azure RTOS NetX LWM2M の概要
description: Azure RTOS NetX LWM2M クライアント プロトコルは、マシン プロトコル標準に対してライトウェイト マシンのクライアント部分を実装します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c29af430975266eed684bd1de38d9e5d7e2586a6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811525"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-lwm2m"></a><span data-ttu-id="bf096-103">第 1 章 - Azure RTOS NetX LWM2M の概要</span><span class="sxs-lookup"><span data-stu-id="bf096-103">Chapter 1 - Introduction to Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="bf096-104">Azure RTOS NetX LWM2M クライアント プロトコルは、マシン プロトコル標準に対してライトウェイト マシンのクライアント部分を実装します。</span><span class="sxs-lookup"><span data-stu-id="bf096-104">The Azure RTOS NetX LWM2M Protocol implements the client part of the Lightweight Machine to Machine protocol standard.</span></span>

## <a name="netx-lwm2m-requirements"></a><span data-ttu-id="bf096-105">NetX LWM2M の要件</span><span class="sxs-lookup"><span data-stu-id="bf096-105">NetX LWM2M Requirements</span></span>

<span data-ttu-id="bf096-106">NetX LWM2M ランタイム ライブラリを正しく機能させるには、NetX IP インスタンスが既に作成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf096-106">In order to function properly, the NetX LWM2M run-time library requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="bf096-107">NetX LWM2M パッケージには、それ以上の要件はありません。</span><span class="sxs-lookup"><span data-stu-id="bf096-107">The NetX LWM2M package has no further requirements.</span></span>

## <a name="netx-lwm2m-rfcs"></a><span data-ttu-id="bf096-108">NetX LWM2M の RFC</span><span class="sxs-lookup"><span data-stu-id="bf096-108">NetX LWM2M RFCs</span></span>

<span data-ttu-id="bf096-109">NetX LWM2M は、OMA-TS-OMA-TS-LightweightM2M-V1_0-20170208-A と、制約付きアプリケーション プロトコル (CoAP) に関連する次の RFC に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="bf096-109">NetX LWM2M is compliant with OMA-TS-LightweightM2M-V1_0-20170208-A and the following RFCs related to the Constrained Application Protocol (CoAP):</span></span>

- <span data-ttu-id="bf096-110">**RFC 7252**: 制約付きアプリケーション プロトコル (CoAP)</span><span class="sxs-lookup"><span data-stu-id="bf096-110">**RFC 7252**: The Constrained Application Protocol (CoAP)</span></span>

- <span data-ttu-id="bf096-111">**RFC 7641**: 制約付きアプリケーション プロトコル (CoAP) でのリソースの監視</span><span class="sxs-lookup"><span data-stu-id="bf096-111">**RFC 7641**: Observing Resources in the Constrained Application Protocol (CoAP)</span></span>

- <span data-ttu-id="bf096-112">**RFC 6690**: 制約付き RESTful 環境 (CoRE) リンク形式</span><span class="sxs-lookup"><span data-stu-id="bf096-112">**RFC 6690**: Constrained RESTful Environments (CoRE) Link Format</span></span>