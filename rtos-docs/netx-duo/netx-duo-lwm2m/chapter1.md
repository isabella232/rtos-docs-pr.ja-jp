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
# <a name="chapter-1--introduction-to-lwm2m-client"></a>第 1 章 - LWM2M クライアントの概要

Azure RTOS NetX Duo LWM2M クライアント プロトコルは、マシン プロトコル標準に対してライトウェイト マシンのクライアント部分を実装します。 (LWM2M 1.0-20170208A)

## <a name="netx-lwm2m-client-requirements"></a>NetX LWM2M クライアントの要件

LWM2M クライアント ランタイム ライブラリを正しく機能させるには、NetX IP インスタンスが既に作成されている必要があります。 NetX LWM2M クライアント パッケージには、それ以上の要件はありません。

## <a name="netx-lwm2m-client-rfcs"></a>NetX LWM2M クライアントの RFC

LWM2M クライアントは、OMA-TS-LightweightM2M-V1\_0-20170208-A と、制約付きアプリケーション プロトコル (CoAP) に関連する次の RFC に準拠しています。

* RFC 7252 制約付きアプリケーション プロトコル (CoAP)

* RFC 7641 制約付きアプリケーション プロトコル (CoAP) でのリソースの監視

* RFC 6690 制約付き RESTful 環境 (CoRE) リンク形式

詳細については、「[OMA-TS-LightweightM2M-V1\_0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf)」を参照してください。