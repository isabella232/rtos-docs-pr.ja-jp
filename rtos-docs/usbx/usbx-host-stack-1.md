---
title: 第 1 章 - Azure RTOS USBX ホスト スタックの概要
description: USBX は、深く組み込まれたアプリケーション用のフル機能の USB スタックです。 この章では、USBX の概要と、その応用および利点について説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9ee49903e764e20316438be16b47d2d9208b1363
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813361"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-host-stack"></a>第 1 章 - Azure RTOS USBX ホスト スタックの概要

USBX は、深く組み込まれたアプリケーション用のフル機能の USB スタックです。 この章では、USBX の概要と、その応用および利点について説明します。

## <a name="usbx-features"></a>USBX の機能

USBX では、1.1、2.0、OTG という 3 つの既存の USB 仕様がサポートされています。 スケーラブルになるように設計されており、デバイスが 1 つしか接続されていないシンプルな USB トポロジにも、複数のデバイスとカスケード ハブを使用する複雑なトポロジにも対応できます。 USBX では、USB プロトコルのあらゆるデータ転送の種類 (コントロール、一括、割り込み、アイソクロナス) がサポートされています。

USBX では、ホスト側とデバイス側の両方がサポートされています。 それぞれの側が 3 つのレイヤーで構成されます。

- コントローラー レイヤー
- スタック レイヤー
- クラス レイヤー

USB レイヤー間の関係は次のとおりです。

![各 USB レイヤー](./media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a>製品の主な強化点

- ThreadX プロセッサの完全なサポート
- ロイヤリティなし
- 完全な ANSI C ソース コード
- リアルタイムのパフォーマンス
- すばやく対応するテクニカル サポート
- 複数のホストコントローラーのサポート
- 複数クラス サポート
- 複数クラス インスタンス
- ThreadX、FileX、および NetX とのクラスの統合
- 複数の構成を持つ USB デバイスのサポート
- USB 複合デバイスのサポート
- カスケードハブのサポート
- USB 電源管理のサポート
- USB OTG のサポート
- TraceX のトレース イベントのエクスポート

## <a name="powerful-services-of-usbx"></a>USBX の強力なサービス

### <a name="multiple-host-controller-support"></a>複数のホストコントローラーのサポート

USBX では、同時に実行されている複数の USB ホスト コントローラーをサポートできます。 この機能を使用すると、現在市場にあるほとんどの USB 2.0 ホスト コントローラーに関連付けられている下位互換性スキームを使用して、USBX で USB 2.0 標準をサポートすることができます。

### <a name="usb-software-scheduler"></a>USB ソフトウェア スケジューラ

USBX には、ハードウェア一覧の処理を行わない USB コントローラーをサポートするために必要な、USB ソフトウェア スケジューラが含まれています。 USBX ソフトウェア スケジューラは、正しいサービス頻度と優先度で USB 転送を整理し、各転送の実行を USB コントローラーに指示します。

### <a name="complete-usb-device-framework-support"></a>USB デバイス フレームワークの完全なサポート

USBX では、複数の構成、複数のインターフェイス、複数の代替設定など、最も要求の厳しい USB デバイスをサポートできます。

### <a name="easy-to-use-apis"></a>使いやすい API

USBX では、わかりやすく使いやすい方法で、最良の深く組み込まれた USB スタックが提供されます。 USBX API を使用すると、サービスが直観的かつ一貫したものになります。 提供された USBX クラス API を使用することにより、ユーザー アプリケーションでは複雑な USB プロトコルを理解する必要がなくなります。
