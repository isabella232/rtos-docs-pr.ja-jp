---
title: Azure RTOS TraceX ユーザー ガイド
description: このガイドには、Microsoft 提供の Microsoft Windows ベースのシステム分析ツールである Azure RTOS TraceX に関する包括的な情報が含まれています。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 89a39112d6fc6d231408179ebb3867c21f927326930a1610529b142aa71a1027
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784072"
---
# <a name="about-this-guide"></a>このガイドについて

このガイドには、Microsoft Azure RTOS 用の Microsoft Windows ベースのシステム分析ツールである Azure RTOS TraceX に関する包括的な情報が含まれています。

Azure RTOS ThreadX リアルタイム オペレーティング システム (RTOS) およびアドオン コンポーネントを使用する組み込みリアルタイム ソフトウェア開発者を対象としています。 開発者には、Azure RTOS ThreadX、Azure RTOS FileX、および Azure RTOS NetX の標準的な概念に関する知識が必要です。

## <a name="organization"></a>Organization

- [第 1 章](chapter1.md) - Azure RTOS TraceX の基本的な概要、およびリアルタイム開発との関係について説明します。
- [第 2 章](chapter2.md) - Azure RTOS TraceX をインストールして使用し、すぐにアプリケーションの分析を始めるための基本的な手順について説明します。
- [第 3 章](chapter3.md) - Azure RTOS TraceX の主な機能について説明します。
- [第 4 章](chapter4.md) - Azure RTOS TraceX のパフォーマンス分析機能について詳しく説明します。
- [第 5 章](chapter5.md) - Azure RTOS TraceX で表示できるトレース バッファーを生成するために、Azure RTOS ThreadX、Azure RTOS FileX、および Azure RTOS NetX を設定する方法について説明します。
- [第 6 章](chapter6.md) - Azure RTOS TraceX イベントの詳細について説明します。
- [第 7 章](chapter7.md) - Azure RTOS FileX イベントの詳細について説明します。
- [第 8 章](chapter8.md) - Azure RTOS NetX イベントの詳細について説明します。
- [第 9 章](chapter9.md) - Azure RTOS USBX イベントの詳細について説明します。
- [第 10 章](chapter10.md) - カスタム ユーザー イベントの作成について詳しく説明します。
- [第 11 章](chapter11.md) - 内部トレース バッファーについて詳しく説明します。
- [付録 A](appendix-a.md) - Azure RTOS ThreadX のポート固有のファイルと、トレース イベントを収集するためのタイムスタンプ ソース。
- [付録 B](appendix-b.md) - イベント トレース バッファーに関する実装の詳細を示す Azure RTOS ThreadX の *tx_trace.h* ファイル。
- [付録 C](appendix-c.md) - さまざまなファイル形式を適切な Azure RTOS TraceX バイナリ ファイルに変換するためのコマンド ライン ユーティリティの概要を示します。
- [付録 D](appendix-d.md) - さまざまな開発ツールからトレース ファイルをダンプする例。

## <a name="guide-conventions"></a>ガイドの表記規則

"*斜体*" - この書体は、本のタイトルを表し、重要な単語を強調し、変数を示すために使用されています。

**太字** - この書体は、ファイル名とキーワードを表し、重要な単語や変数をさらに強調するために使用されます。

> [!NOTE]
> 注意事項を示します。

## <a name="customer-support-center"></a>カスタマー サポート センター

質問やこちらの手順に関するお問い合わせについては、Azure portal からサポート チケットを送信してください。 お客様のサポート リクエストをより効率的に解決できるように、以下の情報をメール メッセージに記載してください。

1. 問題の詳しい説明。発生頻度や、確実に再現できるかどうかなど。
2. 問題が発生する前にアプリケーションや Azure RTOS ThreadX に加えた変更の詳しい説明。
3. ご自身のディストリビューションの *tx_port.h* ファイル内の *_tx_version_id* 文字列の内容。 この文字列から、実行時環境に関する重要な情報が得られます。
4. *_tx_build_options* ULONG 変数の RAM の内容。 この変数から、Azure RTOS ThreadX ライブラリの構築方法に関する情報が得られます。
