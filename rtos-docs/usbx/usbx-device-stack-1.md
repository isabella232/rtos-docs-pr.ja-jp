---
title: 第 1 章 - Azure RTOS USBX デバイス スタックの概要
description: USBX は、深く組み込まれたアプリケーション用のフル機能の USB スタックです。 この章では、USBX の概要と、その利点および応用について説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 8b1e08130d4531fd82629378761cd5b1752f0a07
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550288"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-device-stack"></a>第 1 章 - Azure RTOS USBX デバイス スタックの概要

USBX は、深く組み込まれたアプリケーション用のフル機能の USB スタックです。 この章では、USBX の概要と、その応用および利点について説明します 

## <a name="usbx-features"></a>USBX の機能

USBX では、1.1、2.0、OTG という 3 つの既存の USB 仕様がサポートされています。 スケーラブルになるように設計されており、デバイスが 1 つしか接続されていないシンプルな USB トポロジにも、複数のデバイスとカスケード ハブを使用する複雑なトポロジにも対応できます。 USBX では、USB プロトコルのあらゆるデータ転送の種類 (コントロール、一括、割り込み、アイソクロナス) がサポートされています。

USBX では、ホスト側とデバイス側の両方がサポートされています。 それぞれの側が 3 つのレイヤーで構成されます。

- コントローラー レイヤー
- スタック レイヤー
- クラス レイヤー

USB レイヤー間の関係は次のとおりです。

![各 USB レイヤー](media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a>製品の特徴

- ThreadX プロセッサの完全なサポート
- ロイヤリティなし
- 完全な ANSI C ソース コード
- リアルタイムのパフォーマンス
- すばやく対応するテクニカル サポート
- 複数クラス サポート
- 複数クラス インスタンス
- ThreadX、FileX、および NetX とのクラスの統合
- 複数の構成を持つ USB デバイスのサポート
- USB 複合デバイスのサポート
- USB 電源管理のサポート
- USB OTG のサポート
- TraceX のトレース イベントのエクスポート

## <a name="powerful-services-of-usbx"></a>USBX の強力なサービス

### <a name="complete-usb-device-framework-support"></a>USB デバイス フレームワークの完全なサポート

USBX では、複数の構成、複数のインターフェイス、複数の代替設定など、最も要求の厳しい USB デバイスをサポートできます。

### <a name="easy-to-use-apis"></a>使いやすい API

USBX では、わかりやすく使いやすい方法で、最良の深く組み込まれた USB スタックが提供されます。 USBX API を使用すると、サービスが直観的かつ一貫したものになります。 提供された USBX クラス API を使用することにより、ユーザー アプリケーションでは複雑な USB プロトコルを理解する必要がなくなります。
