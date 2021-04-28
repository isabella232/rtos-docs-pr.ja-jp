---
title: Azure RTOS USBX デバイス スタック ユーザー ガイド
description: このガイドでは、Microsoft のハイ パフォーマンス USB 基盤ソフトウェアである Azure RTOS USBX に関する包括的な情報を提供します
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: c8e9360c8b72adbc41f840a48e333668c489399e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810244"
---
# <a name="azure-rtos-usbx-device-stack-user-guide"></a>Azure RTOS USBX デバイス スタック ユーザー ガイド

このガイドでは、Microsoft のハイ パフォーマンス USB 基盤ソフトウェアである Azure RTOS USBX に関する包括的な情報を提供します。

これは、組み込みリアルタイム ソフトウェアの開発者を対象としています。 開発者は、標準のリアルタイム オペレーティング システム関数、USB 仕様、および C プログラミング言語について理解している必要があります。

USB に関する技術情報については、 https://www.USB.org/developers でダウンロードできる USB 仕様および USB クラス仕様を参照してください

## <a name="organization"></a>Organization

- [**第 1 章**](usbx-device-stack-1.md) - Azure RTOS USBX の概要が含まれています

- [**第 2 章**](usbx-device-stack-2.md) - Azure RTOS USBX をインストールして ThreadX アプリケーションで使用するための基本的な手順を示します

- [**第 3 章**](usbx-device-stack-3.md) - Azure RTOS USBX デバイス スタックの機能コンポーネントについて説明します

- [**第 4 章**](usbx-device-stack-4.md) - Azure RTOS USBX デバイス スタックのサービスについて説明します

- [**第 5 章**](usbx-device-stack-5.md) - 各 Azure RTOS USBX デバイス クラスについて、API を含めて説明します

## <a name="customer-support-center"></a>カスタマー サポート センター

質問やこちらの手順に関するお問い合わせについては、Azure portal からサポート チケットを送信してください。 お客様のサポート リクエストをより効率的に解決できるように、次の情報を電子メールでお知らせください。

1. 問題の詳しい説明。発生頻度や、確実に再現できるかどうかなど。
2. 問題が発生する前にアプリケーションや Azure RTOS ThreadX に加えた変更の詳しい説明。
3. ご自身のディストリビューションの **_tx_port.h_** ファイル内の **_tx_version_id** 文字列の内容。 この文字列から、実行時環境に関する重要な情報が得られます。
4. *_tx_build_options* **ULONG** 変数の RAM の内容。 この変数から、Azure RTOS ThreadX ライブラリの構築方法に関する情報が得られます。
