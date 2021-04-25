---
title: 第 1 章 - ARMv8-M 用 Azure RTOS ThreadX の概要。
description: この章は、ARMv8-M 用 Azure RTOS ThreadX の補足資料の導入部分です。
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 486466f41e64adb9e32ebbd21a22629221ffa9c1
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377507"
---
# <a name="chapter-1--overview"></a><span data-ttu-id="5624e-103">第 1 章  概要</span><span class="sxs-lookup"><span data-stu-id="5624e-103">Chapter 1  Overview</span></span>

<span data-ttu-id="5624e-104">ARMv8 のアーキテクチャでは、TrustZone を含む新しいセキュリティ機能が導入されています。この機能により、メモリにセキュアまたは非セキュアというタグを付けることができます。</span><span class="sxs-lookup"><span data-stu-id="5624e-104">The ARMv8-M architecture introduces new security features, including TrustZone, which allows memory to be tagged as secure or non-secure.</span></span> <span data-ttu-id="5624e-105">ARM のガイドラインに従い、ThreadX (およびユーザー アプリケーション) は非セキュア モードで実行されるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="5624e-105">Following ARM's guidelines, ThreadX (and the user application) is designed to be run in non-secure mode.</span></span> <span data-ttu-id="5624e-106">ThreadX (およびユーザー アプリケーション) は、セキュア モードでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="5624e-106">ThreadX (and the user application) can also be run in secure mode.</span></span> <span data-ttu-id="5624e-107">セキュア モードのソフトウェアとのインターフェイスを構築するには、いくつかの新しい ThreadX API が必要です。</span><span class="sxs-lookup"><span data-stu-id="5624e-107">In order to interface with secure mode software, some new ThreadX APIs are necessary.</span></span> <span data-ttu-id="5624e-108">このドキュメントでは、ARMv8-M アーキテクチャ (Cortex-M23、Cortex-M33、Cortex-M35P、Cortex-M55 など) 固有の ThreadX サービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5624e-108">This document describes these ThreadX services that are specific to the ARMv8-M architecture, including the Cortex-M23, Cortex-M33, Cortex-M35P, and Cortex-M55.</span></span>
