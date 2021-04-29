---
title: Azure RTOS NetX ユーザー ガイドについて
description: このガイドでは、Microsoft の高パフォーマンス ネットワーク スタックである Azure RTOS NetX について包括的に説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8e1c23892c4360ddc8783b04ae8f23e371899f1d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811735"
---
# <a name="about-the-azure-rtos-netx-user-guide"></a>Azure RTOS NetX ユーザー ガイドについて

このガイドでは、Microsoft の高パフォーマンス ネットワーク スタックである Azure RTOS NetX について包括的に説明します。

本書は、基本的なネットワーク概念、Azure RTOS ThreadX、C プログラミング言語を理解している埋め込み型のリアルタイム ソフトウェア開発者を対象としています。

## <a name="organization"></a>Organization

[第 1 章](chapter1.md) - Azure RTOS NetX の概要

[第 2 章](chapter2.md) - Azure RTOS NetX をインストールして ThreadX アプリケーションで使用するための基本的な手順を示します。

[第 3 章](chapter3.md) - Azure RTOS NetX システムの機能の概要と TCP/IP ネットワーク標準に関する基本的な情報を提供します。

[第 4 章](chapter4.md) - Azure RTOS NetX のアプリケーションのインターフェイスについて詳しく説明します。

[第 5 章](chapter5.md) - Azure RTOS NetX のネットワーク ドライバーについて説明します。

[付録 A](appendix-a.md) - Azure RTOS NetX サービス

[付録 B](appendix-b.md) - Azure RTOS NetX の定数

[付録 C](appendix-c.md) - Azure RTOS NetX のデータ型

[付録 D](appendix-d.md) - BSD 互換ソケット API

[付録 E](appendix-e.md) - ASCII チャート

## <a name="azure-rtos-netx-data-types"></a>Azure RTOS NetX のデータ型

カスタムの Azure RTOS NetX 制御構造データ型に加えて、Azure RTOS NetX サービス呼び出しインターフェイスで使用される特殊なデータ型がいくつかあります。 これらの特殊データ型は、基になる C コンパイラのデータ型に直接マップされます。 これは、異なる C コンパイラ間での移植性を確保するために行われます。 正確な実装は ThreadX から継承されており、ThreadX ディストリビューションに含まれている ***tx_port.h*** ファイル内にあります。

Azure RTOS NetX サービス呼び出しのデータ型と、それに関連付けられている意味の一覧を次に示します。

| <!-- -->    | <!-- -->    |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **UINT**  | 基本的な符号なし整数。 この型は、32 ビットの符号なしデータをサポートする必要があります。ただし、これは最も便利な符号なしデータ型にマップされます。 |
| **ULONG** | 符号なし long 型。 この型は、32 ビットの符号なしデータをサポートする必要があります。                                                                      |
| **VOID**  | ほとんどの場合、コンパイラの void 型と同等です。                                                                                 |
| **CHAR**  | ほとんどの場合、標準の 8 ビット文字型です。                                                                                           |

その他のデータ型は Azure RTOS NetX ソース内で使用されます。 これらは ***tx_port.h** または *_nx_port.h_** のいずれかのファイル内にあります。

## <a name="customer-support-center"></a>カスタマー サポート センター

こちらの手順についてご不明な点がある場合、またはサポートが必要な場合は、Azure portal からサポート チケットをお送りください。 お客様のサポート リクエストをより効率的に解決できるように、次の情報をメールでお知らせください。

1. 問題の詳しい説明。発生頻度や、確実に再現できるかどうかなど。

2. 問題が発生する前にアプリケーションや Azure RTOS NetX に行ったすべての変更に関する詳細な説明。

3. ご自身のディストリビューションの **_tx_port.h_ *_ および _* _nx_port.h_** ファイル内の **_tx_version_id** 文字列および **_nx_version_id** 文字列の内容。 これらの文字列から、実行時環境に関する重要な情報が得られます。

4. 次の **ULONG** 変数の RAM 内の内容:

    **_tx_build_options**

    **_nx_system_build_options1**

    **_nx_system_build_options2**

    **_nx_system_build_options3**

    **_nx_system_build_options4**

    **_nx_system_build_options5**

    これらの変数から、Azure RTOS ThreadX と Azure RTOS NetX のライブラリがどのように構築されたかに関する情報が得られます。

5. 問題が検出された直後にキャプチャされたトレース バッファー。 これを行うには、Azure RTOS ThreadX と Azure RTOS NetX のライブラリを **TX_ENABLE_EVENT_TRACE** を使用して構築し、トレース バッファー情報を使用して **tx_trace_enable** を呼び出します。 詳細については、Azure RTOS TraceX ユーザー ガイドをご覧ください。
