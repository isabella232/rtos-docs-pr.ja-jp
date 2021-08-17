---
title: 第 1 章 - ARMv8-M 用 Azure RTOS ThreadX の概要。
description: この章は、ARMv8-M 用 Azure RTOS ThreadX の補足資料の導入部分です。
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1f0d87ec562c7fcfa6af5d2240655ef526f6e0611d509fe60c745436371413d7
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798250"
---
# <a name="chapter-1--overview"></a>第 1 章  概要

ARMv8 のアーキテクチャでは、TrustZone を含む新しいセキュリティ機能が導入されています。この機能により、メモリにセキュアまたは非セキュアというタグを付けることができます。 ARM のガイドラインに従い、ThreadX (およびユーザー アプリケーション) は非セキュア モードで実行されるように設計されています。 ThreadX (およびユーザー アプリケーション) は、セキュア モードでも実行できます。 セキュア モードのソフトウェアとのインターフェイスを構築するには、いくつかの新しい ThreadX API が必要です。 このドキュメントでは、ARMv8-M アーキテクチャ (Cortex-M23、Cortex-M33、Cortex-M35P、Cortex-M55 など) 固有の ThreadX サービスについて説明します。
