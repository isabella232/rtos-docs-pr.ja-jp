---
title: Azure RTOS NetX Duo ユーザー ガイドについて
description: このガイドでは、Microsoft の高パフォーマンス IPv4/IPv6 デュアル ネットワーク スタックである Azure RTOS NetX Duo について包括的に説明しています。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b1eef5bfa28f13d7a6b627792f96039b252f2355
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811054"
---
# <a name="about-the-azure-rtos-netx-duo-user-guide"></a>Azure RTOS NetX Duo ユーザー ガイドについて

このガイドでは、Microsoft の高パフォーマンス IPv4/IPv6 デュアル ネットワーク スタックである Azure RTOS NetX Duo について包括的に説明しています。 

本書は、基本的なネットワーク概念、Azure RTOS ThreadX、C プログラミング言語を理解している埋め込みリアルタイム ソフトウェアの開発者を対象としています。

## <a name="organization"></a>Organization

[第 1 章](chapter1.md) - Azure RTOS NetX Duo の概要

[第 2 章](chapter2.md) - Azure RTOS NetX Duo をインストールして ThreadX アプリケーションで使用するための基本的な手順を示します

[第 3 章](chapter3.md) - Azure RTOS NetX Duo システムの機能の概要と TCP/IP ネットワーク標準の基本情報について説明します

[第 4 章](chapter4.md) - Azure RTOS NetX Duo に対するアプリケーションのインターフェイスの詳細です

[第 5 章](chapter5.md) - Azure RTOS NetX Duo のネットワーク ドライバーについて説明します

[付録 A](appendix-a.md) - Azure RTOS NetX Duo のサービス

[付録 B](appendix-b.md) - Azure RTOS NetX Duo の定数

[付録 C](appendix-c.md) - Azure RTOS NetX Duo のデータ型

[付録 D](appendix-d.md) - BSD 互換ソケット API

[付録 E](appendix-e.md) - ASCII チャート

## <a name="guide-conventions"></a>ガイドの表記規則

斜体 - この書体は、本のタイトルを表し、重要な単語を強調し、変数を示すために使用されます。

**太字** - この書体は、ファイル名とキーワードを表し、重要な単語や変数をさらに強調するために使用されます。

> [!IMPORTANT]
> 情報記号は、注意する必要がある、パフォーマンスや機能に影響を与える可能性のある重要な情報や追加情報を示します。
 
> [!WARNING]
> 警告記号は、致命的なエラーを引き起こす可能性があるため、開発者が回避する必要がある状況を示します。

## <a name="azure-rtos-netx-duo-data-types"></a>Azure RTOS NetX Duo のデータ型

Azure RTOS NetX Duo のカスタムの制御構造データ型に加えて、Azure RTOS NetX Duo サービス呼び出しインターフェイスで使用される特殊なデータ型がいくつかあります。 これらの特殊データ型は、基になる C コンパイラのデータ型に直接マップされます。 これは、異なる C コンパイラ間での移植性を確保するために行われます。 正確な実装は ThreadX から継承されており、ThreadX ディストリビューションに含まれている ***tx_port.h*** ファイルにあります。

次に示すのは、Azure RTOS NetX Duo サービス呼び出しのデータ型とそれに関連付けられている意味の一覧です。

**UINT**: 基本的な符号なし整数。 この型は、32 ビットの符号なしデータをサポートする必要があります。ただし、最も便利な符号なしデータ型にマップされます。  
**ULONG**: 符号なし long 型。 この型は、32 ビットの符号なしデータをサポートする必要があります。
**VOID**: ほとんどの場合、コンパイラの void 型と同等です。  
**CHAR**: ほとんどの場合、標準の 8 ビット文字型です。  

その他のデータ型が Azure RTOS NetX Duo ソース内で使用されます。 それらは ***tx_port.h** _ と _ *_nx_port.h_** のいずれかのファイルにあります。

## <a name="customer-support-center"></a>カスタマー サポート センター

こちらの手順に関する質問やサポートについては、Azure portal からサポート チケットを送信してください。 お客さまのサポート リクエストをより効率的に解決できるように、電子メール メッセージで次の情報をお知らせください。

1. 問題の詳しい説明。発生頻度や、確実に再現できるかどうかなど。
2. 問題が発生する前にアプリケーションや Azure RTOS NetX Duo に加えた変更の詳しい説明。
3. ディストリビューションの tx_port.h および nx_port.h のファイルの中にある _tx_version_id および _nx_version_id の文字列の内容。 これらの文字列から、実行時環境に関する重要な情報が得られます。
4. 次の ULONG 変数の RAM の内容。

    **_tx_build_options**

    **_nx_system_build_options1**

    **_nx_system_build_options2**

    **_nx_system_build_options3**

    **_nx_system_build_options4**

    **_nx_system_build_options5**

    これらの変数から、Azure RTOS ThreadX と Azure RTOS NetX Duo のライブラリがどのようにビルドされたかについての情報が得られます。

5. 問題が検出された直後にキャプチャされたトレース バッファー。 これを行なうには、Azure RTOS ThreadX と Azure RTOS NetX Duo のライブラリを TX_ENABLE_EVENT_TRACE を使用してビルドし、トレース バッファー情報を使用して tx_trace_enable を呼び出します。
