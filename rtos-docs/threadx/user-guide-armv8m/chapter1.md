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
# <a name="chapter-1--overview"></a>第 1 章  概要

ARMv8 のアーキテクチャでは、TrustZone を含む新しいセキュリティ機能が導入されています。この機能により、メモリにセキュアまたは非セキュアというタグを付けることができます。 ARM のガイドラインに従い、ThreadX (およびユーザー アプリケーション) は非セキュア モードで実行されるように設計されています。 ThreadX (およびユーザー アプリケーション) は、セキュア モードでも実行できます。 セキュア モードのソフトウェアとのインターフェイスを構築するには、いくつかの新しい ThreadX API が必要です。 このドキュメントでは、ARMv8-M アーキテクチャ (Cortex-M23、Cortex-M33、Cortex-M35P、Cortex-M55 など) 固有の ThreadX サービスについて説明します。
