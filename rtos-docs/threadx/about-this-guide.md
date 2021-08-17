---
title: Azure RTOS ThreadX に関するガイド
description: このガイドでは、Microsoft のハイパフォーマンス リアルタイム カーネルである Azure RTOS ThreadX に関する包括的な情報を提供します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 28f088409fdd5e2c075cbf90b21d3d260c811806066e74bffc395207cde0239c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802126"
---
# <a name="about-the-azure-rtos-threadx-guide"></a>Azure RTOS ThreadX に関するガイド

このガイドでは、Microsoft のハイパフォーマンス リアルタイム カーネルである Azure RTOS ThreadX に関する包括的な情報を提供します。 

これは、組み込みリアルタイム ソフトウェアの開発者を対象としています。 開発者は、標準のリアルタイム オペレーティング システム関数および C プログラミング言語について理解している必要があります。

## <a name="organization"></a>Organization

[第 1 章](chapter1.md) - Azure RTOS ThreadX の基本的な概要と、リアルタイム組み込み開発との関係について説明します

[第 2 章](chapter2.md) - Azure RTOS ThreadX をインストールしてアプリケーションで "*すぐに使用する*" ための基本的な手順について説明します

[第 3 章](chapter3.md) - ハイパフォーマンス リアルタイム カーネルである Azure RTOS ThreadX の機能動作について詳しく説明します

[第 4 章](chapter4.md) - Azure RTOS ThreadX に対するアプリケーションのインターフェイスについて詳しく説明します

[第 5 章](chapter5.md) - Azure RTOS ThreadX アプリケーション用の I/O ドライバーの作成について説明します

[第 6 章](chapter6.md) - すべての Azure RTOS ThreadX プロセッサ サポート パッケージに付属するデモンストレーション アプリケーションについて説明します

[付録 A](appendix-a.md) - Azure RTOS ThreadX API

[付録 B](appendix-b.md) - Azure RTOS ThreadX の定数

[付録 C](appendix-c.md) - Azure RTOS ThreadX のデータ型

[付録 D](appendix-d.md) - ASCII チャート

## <a name="guide-conventions"></a>ガイドの表記規則

"*斜体*" - この書体は、本のタイトルを表し、重要な単語を強調し、パラメーターを示すために使用されています。

**太字** - この書体は、キーワード、定数、型名、ユーザー インターフェイス要素、変数名を表し、重要な単語をさらに強調するために使用されています。

***斜体かつ太字*** - この書体は、ファイル名と関数名を表すために使用されています。

> [!IMPORTANT]
> 情報記号は、パフォーマンスや機能に影響を与える可能性がある重要な情報や追加情報を示します。

> [!WARNING]
> 警告記号は、致命的なエラーを引き起こす可能性があるために開発者が回避するように注意する必要がある状況を示します。

## <a name="azure-rtos-threadx-data-types"></a>Azure RTOS ThreadX のデータ型

カスタムの Azure RTOS ThreadX 制御構造データ型に加えて、Azure RTOS ThreadX サービス呼び出しインターフェイスで使用される一連の特殊なデータ型があります。 これらの特殊データ型は、基になる C コンパイラのデータ型に直接マップされます。 これは、異なる C コンパイラ間での移植性を確保するために行われます。 正確な実装は、ソースに含まれている ***tx_port.h*** ファイルで確認できます。

Azure RTOS ThreadX サービス呼び出しのデータ型と、それらに関連付けられている意味の一覧を次に示します。

| データ型  | 説明 |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **UINT** | 基本的な符号なし整数。 この型は、8 ビットの符号なしデータをサポートする必要があります。ただし、最も便利な符号なしデータ型にマップされます。 |
| **ULONG** | 符号なし long 型。 この型では、32 ビットの符号なしデータをサポートする必要があります。 |
| **VOID** | ほとんどの場合、コンパイラの void 型と同等です。 |
| **CHAR** | ほとんどの場合、標準の 8 ビット文字型です。 |
|  |  |

その他のデータ型は Azure RTOS ThreadX ソース内で使用されます。 これらは、***tx_port.h*** ファイルにもあります。

## <a name="customer-support-center"></a>カスタマー サポート センター

質問やこちらの手順に関するお問い合わせについては、Azure portal からサポート チケットを送信してください。 お客様のサポート リクエストをより効率的に解決できるように、以下の情報をメール メッセージに記載してください。

1. 問題の詳しい説明。発生頻度や、確実に再現できるかどうかなど。
2. 問題が発生する前にアプリケーションや Azure RTOS ThreadX に加えた変更の詳しい説明。
3. ご自身のディストリビューションの *tx_port.h* ファイル内の *_tx_version_id* 文字列の内容。 この文字列から、実行時環境に関する重要な情報が得られます。
4. **_tx_build_options** **ULONG** 変数の RAM の内容。 この変数から、Azure RTOS ThreadX ライブラリの構築方法に関する情報が得られます。
