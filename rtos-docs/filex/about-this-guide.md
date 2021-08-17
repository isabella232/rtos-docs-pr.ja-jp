---
title: Azure RTOS FileX ユーザー ガイド
description: このガイドには、Microsoft のハイパフォーマンス リアルタイム ファイル システムである Azure RTOS FileX に関する包括的な情報が含まれています。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 48fe70fc3cff6e656328d38b2583116e58a6c98510d5f0554f81a7b728f95457
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782406"
---
# <a name="about-this-filex-user-guide"></a>この FileX ユーザー ガイドについて

このガイドには、Microsoft のハイパフォーマンス リアルタイム組み込みファイル システムである Azure RTOS FileX に関する包括的な情報が含まれています。 このガイドを最大限に活用するには、標準のリアルタイム オペレーティング システム関数、FAT ファイル システムのサービス、および C プログラミング言語について理解している必要があります。

## <a name="organization"></a>Organization

[第 1 章](chapter1.md) - Azure RTOS FileX の概要を示します

[第 2 章](chapter2.md) - Azure RTOS FileX をインストールして Azure RTOS ThreadX アプリケーションで使用するための基本的な手順を示します

[第 3 章](chapter3.md) - Azure RTOS FileX システムの機能の概要と FAT ファイル システム形式に関する基本的な情報を提供します

[第 4 章](chapter4.md) - Azure RTOS FileX に対するアプリケーションのインターフェイスについて詳しく説明します

[第 5 章](chapter5.md) - 提供されている Azure RTOS FileX RAM ドライバーについて説明し、独自のカスタム Azure RTOS FileX ドライバーを作成する方法について説明します

[第 6 章](chapter6.md) - Azure RTOS FileX フォールト トレラント モジュールについて説明します

[付録 A](appendix-a.md) - Azure RTOS FileX のサービス

[付録 B](appendix-b.md) - Azure RTOS FileX の定数

[付録 C](appendix-c.md) - Azure RTOS FileX のデータ型

[付録 D](appendix-d.md) - ASCII チャート

## <a name="guide-conventions"></a>ガイドの表記規則

"*斜体*" - この書体は、本のタイトルを表し、重要な単語を強調し、変数を示すために使用されています。

**太字** - この書体は、ファイル名とキーワードを表し、重要な単語や変数をさらに強調するために使用されます。

> [!NOTE]
> 情報記号は、注意する必要がある、パフォーマンスや機能に影響を与える可能性のある重要な情報や追加情報を示します。

> [!IMPORTANT]
> 警告記号は、致命的なエラーを引き起こす可能性があるため、開発者が回避する必要がある状況を示します。

## <a name="filex-data-types"></a>FileX のデータ型

カスタムの Azure RTOS FileX 制御構造データ型に加えて、Azure RTOS FileX サービス呼び出しインターフェイスで使用される一連の特殊なデータ型があります。 これらの特殊データ型は、基になる C コンパイラのデータ型に直接マップされます。 これは、異なる C コンパイラ間での移植性を確保するために行われます。 正確な実装は Azure RTOS ThreadX から継承されており、Azure RTOS ThreadX ディストリビューションに含まれている tx_port.h ファイルにあります。

Azure RTOS FileX サービス呼び出しのデータ型と、それに関連付けられている意味の一覧を次に示します。

| Type  | 説明  |
|---|---|
| **UINT** | 基本的な符号なし整数。 この型は、8 ビットの符号なしデータをサポートする必要があります。ただし、最も便利な符号なしデータ型にマップされます。 |
| **ULONG** | 符号なし long 型。 この型では、32 ビットの符号なしデータをサポートする必要があります。 |
| **VOID** | ほとんどの場合、コンパイラの void 型と同等です。 |
| **CHAR** | ほとんどの場合、標準の 8 ビット文字型です。 |
| **ULONG64** | 64 ビット符号なし整数データ型。 |

追加のデータ型は、FileX ソース内で使用されます。 これらは ***tx_port.h** または *_fx_port.h_** のいずれかのファイル内にあります。

## <a name="customer-support-center"></a>カスタマー サポート センター

質問やこちらの手順に関するお問い合わせについては、Azure portal からサポート チケットを送信してください。 お客様のサポート リクエストをより効率的に解決できるように、次の情報を電子メールでお知らせください。

1. 問題の詳しい説明。発生頻度や、確実に再現できるかどうかなど。
2. 問題が発生する前にアプリケーションや FileX に加えた変更の詳しい説明。
3. ご自身のディストリビューションの _tx_version_id および _fx_version_id 文字列の内容 (***tx_port.h**_ および _ *_fx_port.h_** ファイル内)。 これらの文字列から、実行時環境に関する重要な情報が得られます。
4. 次の **ULONG** 変数の RAM の内容。 これらの変数から、ThreadX と FileX のライブラリがどのように構築されたかに関する情報が得られます。

    **_tx_build_options**

    **_fx_system_build_options1**

    **_fx_system_build_options2**

    **_fx_system_build_options3**
