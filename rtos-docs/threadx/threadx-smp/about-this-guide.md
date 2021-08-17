---
title: このガイドについて
description: このガイドでは、Microsoft のハイパフォーマンス組み込みリアルタイム カーネルである Azure RTOS ThreadX SMP に関する包括的な情報を提供します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6a8758bff2f205b06448905634172c05dd7fe189cce9fbe3977f6080c51eb95d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784786"
---
# <a name="about-this-guide"></a>このガイドについて

このガイドでは、Microsoft のハイパフォーマンス組み込みリアルタイム カーネルである Azure RTOS ThreadX SMP に関する包括的な情報を提供します。

これは、組み込みリアルタイム ソフトウェアの開発者を対象としています。 開発者は、標準のリアルタイム オペレーティング システム関数および C プログラミング言語について理解している必要があります。

## <a name="organization"></a>Organization

| 章       | 概要                    |
| ------------- | ---------------------------------------------------------------------------------------------------------- |
| **第 1 章** | ThreadX SMP の基本的な概要と、リアルタイム組み込み開発との関係について説明します。           |
| **第 2 章** | ThreadX SMP をインストールしてアプリケーションで "*すぐに使用する*" ための基本的な手順について説明します。           |
| **第 3 章** | ハイパフォーマンス リアルタイム SMP カーネルである ThreadX SMP の機能動作について詳しく説明します。    |
| **第 4 章** | ThreadX SMP に対するアプリケーションのインターフェイスについて詳しく説明します。                                                        |
| **第 5 章** | ThreadX SMP アプリケーション用の I/O ドライバーの作成について説明します。                                                |
| **第 6 章** | すべての ThreadX SMP プロセッサ サポート パッケージに付属するデモンストレーション アプリケーションについて説明します。 |
| **付録 A:** | ThreadX SMP の API        |
| **付録 B** | ThreadX SMP の定数  |
| **付録 C** | ThreadX SMP のデータ型 |
| **付録 D** | ASCII チャート            |

## <a name="guide-conventions"></a>ガイドの表記規則

- "*斜体*" - "*この書体は、本のタイトルを表し、重要な単語を強調し、変数を示すために使用されています。* "
- **太字** - **この書体は、ファイル名とキーワードを表し、重要な単語や変数をさらに強調するために使用されています。**

> [!IMPORTANT]
> 情報記号は、パフォーマンスや機能に影響を与える可能性がある重要な情報や追加情報を示します。

> [!WARNING]
> 警告記号は、致命的なエラーを引き起こす可能性があるために開発者が回避するように注意する必要がある状況を示します。

## <a name="threadx-smp-data-types"></a>ThreadX SMP のデータ型

カスタム ThreadX SMP 制御構造のデータ型に加えて、ThreadX SMP サービス呼び出しインターフェイスで使用される一連の特殊なデータ型があります。 これらの特殊なデータ型は、基になる C コンパイラのデータ型に直接マップされます。 これは、異なる C コンパイラ間での移植性を確保するために行われます。 正確な実装は、ディストリビューション ディスクに含まれている ***tx_port.h*** ファイルで確認できます。

次に示すのは、ThreadX SMP サービス呼び出しのデータ型とそれに関連付けられている意味の一覧です。

| データ型          | 意味                                                          |
| --------- | --------------------------------------------------------- |
| **UINT**  | 基本的な符号なし整数。 この型は、8 ビットの符号なしデータをサポートする必要があります。ただし、最も便利な符号なしデータ型にマップされます。 |
| **ULONG** | 符号なし long 型。 この型では、32 ビットの符号なしデータをサポートする必要があります。                                                                     |
| **VOID**  | ほとんどの場合、コンパイラの void 型と同等です。                                                                                |
| **CHAR**  | ほとんどの場合、標準の 8 ビット文字型です。                                                                                          |

追加のデータ型は、ThreadX SMP ソース内で使用されます。 これらは、***tx_port.h*** ファイルにもあります。

## <a name="customer-support-center"></a>カスタマー サポート センター

サポート メール アドレス: [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) Web ページ: azure.com/rtos

### <a name="latest-product-information"></a>最新の製品情報

azure.com/rtos Web サイトにアクセスし、[サポート] メニュー オプションを選択して、最新の ThreadX SMP 製品リリースに関する情報など、最新のオンライン サポート情報を検索します。

### <a name="what-we-need-from-you"></a>必要なもの

お客様のサポート リクエストをより効率的に解決できるように、次の情報を電子メールでお知らせください。

1. 問題の詳しい説明。発生頻度や、確実に再現できるかどうかなど。
2. 問題が発生する前にアプリケーションや ThreadX SMP に加えた変更の詳しい説明。
3. ご自身のディストリビューションの _ *_tx_port.h_** ファイル内の * **_tx_version_id** _ 文字列の内容。 この文字列から、実行時環境に関する重要な情報が得られます。
4. ***_tx_build_options*** ULONG 変数の RAM の内容。 この変数から、ThreadX SMP ライブラリの構築方法に関する情報が得られます。

### <a name="where-to-send-comments-about-this-guide"></a>このガイドに関するご意見の送信先

ご意見やご提案は、カスタマー サポート センター ([azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com)) まで電子メールにてお寄せください。その際、件名に "ThreadX SMP ユーザー ガイド" を含めてください。
