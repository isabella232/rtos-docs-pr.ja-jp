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
# <a name="chapter-1---introduction-to-azure-rtos-netx-lwm2m"></a>第 1 章 - Azure RTOS NetX LWM2M の概要

Azure RTOS NetX LWM2M クライアント プロトコルは、マシン プロトコル標準に対してライトウェイト マシンのクライアント部分を実装します。

## <a name="netx-lwm2m-requirements"></a>NetX LWM2M の要件

NetX LWM2M ランタイム ライブラリを正しく機能させるには、NetX IP インスタンスが既に作成されている必要があります。 NetX LWM2M パッケージには、それ以上の要件はありません。

## <a name="netx-lwm2m-rfcs"></a>NetX LWM2M の RFC

NetX LWM2M は、OMA-TS-OMA-TS-LightweightM2M-V1_0-20170208-A と、制約付きアプリケーション プロトコル (CoAP) に関連する次の RFC に準拠しています。

- **RFC 7252**: 制約付きアプリケーション プロトコル (CoAP)

- **RFC 7641**: 制約付きアプリケーション プロトコル (CoAP) でのリソースの監視

- **RFC 6690**: 制約付き RESTful 環境 (CoRE) リンク形式