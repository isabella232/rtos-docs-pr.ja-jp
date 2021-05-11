---
title: Azure RTOS GUIX ユーザー ガイド
description: このガイドには、Microsoft のハイパフォーマンス GUI 製品である Azure RTOS GUIX に関する包括的な情報が含まれています。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: b7af0fba59b599c9c8db3ab80a3271eacfd11992
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812107"
---
# <a name="about-guix-user-guide"></a>GUIX ユーザー ガイドについて

このガイドには、Microsoft のハイパフォーマンス GUI 製品である Azure RTOS GUIX に関する包括的な情報が含まれています。 基本的な GUI の概念、Azure RTOS ThreadX、C プログラミング言語を理解している埋め込み型のリアルタイム ソフトウェア開発者を対象としています。

## <a name="organization"></a>Organization

[第 1 章 - Azure RTOS GUIX の概要](chapter-1.md)

[第 2 章 - Azure RTOS GUIX のインストールと使用](chapter-2.md)

[第 3 章 - Azure RTOS GUIX の機能の概要](chapter-3.md)

[第 4 章 - Azure RTOS GUIX サービスの説明](chapter-4.md)

[第 5 章 - Azure RTOS GUIX ディスプレイ ドライバー](chapter-5.md)  

[Azure RTOS GUIX の例](guix-example.md)

[付録 A - Azure RTOS GUIX の色の定義](appendix-a.md)

[付録 B - Azure RTOS GUIX の色の形式](appendix-b.md)

[付録 C - Azure RTOS GUIX ウィジェットのスタイル](appendix-c.md)

[付録 D - Azure RTOS GUIX のブラシ、キャンバス、グラデーションの属性](appendix-d.md)

[付録 E - Azure RTOS GUIX イベントの説明](appendix-e.md)

[付録 F - Azure RTOS GUIX RTOS バインド サービス](appendix-f.md)

[付録 G - Azure RTOS GUIX フォント構造体](appendix-g.md)

[付録 H - Azure RTOS GUIX のビルド時の構成フラグ](appendix-h.md)

[付録 I - Azure RTOS GUIX 情報構造](appendix-i.md)

## <a name="guide-conventions"></a>ガイドの表記規則

"*斜体*" - この書体は、本のタイトルを表し、重要な単語を強調し、変数を示すために使用されています。

**太字** - この書体は、ファイル名とキーワードを表し、重要な単語や変数をさらに強調するために使用されます。

> [!IMPORTANT]
> 情報記号は、注意する必要がある、パフォーマンスや機能に影響を与える可能性のある重要な情報や追加情報を示します。

## <a name="azure-rtos-guix-data-types"></a>Azure RTOS GUIX データ型

カスタムの Azure RTOS GUIX 制御構造データ型に加えて、Azure RTOS GUIX サービス呼び出しインターフェイスで使用される特殊なデータ型がいくつかあります。 これらの特殊データ型は、基になる C コンパイラのデータ型に直接マップされます。 これは、異なる C コンパイラ間での移植性を確保するために行われます。 正確な実装は ThreadX から継承されており、ThreadX ディストリビューションに含まれている ***tx_port.h*** ファイル内にあります。

Azure RTOS GUIX サービス呼び出しのデータ型と、それに関連付けられている意味の一覧を次に示します。

| <!-- --> | <!-- --> |
| --------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **UINT**             | 基本的な符号なし整数。 この型は、最も便利な符号なしデータ型にマップされます。                                |
| **INT**              | 基本的な符号付き整数。 この型は、最も便利な符号付きデータ型にマップされます。                                    |
| **ULONG**            | 符号なし long 型。 この型では、32 ビットの符号なしデータをサポートする必要があります。                                                      |
| **VOID**             | ほとんどの場合、コンパイラの void 型と同等です。                                                                 |
| **GX_CHAR**         | 多くの場合、コンパイラによって定義された char 型として型定義されています。                                                               |
| **GX_BYTE**          | 8 ビットの符号付きの型。                                                                                                    |
| **GX_UBYTE**         | 8 ビットの符号なしの型。                                                                                                  |
| **GX_VALUE**        | 16 または 32 ビットの符号付きの型。 ターゲット システム上で最適なパフォーマンスを得るために必要に応じて定義されます。                                |
| **GX_FIXED_VAL**   | 固定小数点数値データ型。                                                                                        |
| **GX_RESOURCE_ID** | 符号なし long 型。                                                                                                   |
| **GX_COLOR**        | 符号なし long 型。                                                                                                   |
| **GX_STRING**       | GX_CHAR \*gx_string_ptr および UINT gx_string_length を含む構造体。                                          |
| **GX_POINT**        | gx_point_x と gx_point_y を含む構造体。                                                                   |
| **GX_RECTANGLE**    | gx_rectangle_left、gx_rectangle_top、gx_rectangle_right、gx_rectangle_bottom の各フィールドを含む構造体。 |
| **GX_GLYPH**        | グリフ メトリックを含む構造体。                                                                                   |
| **GX_FONT**         | フォント メトリックを含む構造体。                                                                                    |
| **GX_BRUSH**        | ブラシ メトリックを含む構造体。                                                                               |
**GX_PIXELMAP**       | ピクセルマップ メトリックを含む構造体。

その他のデータ型は Azure RTOS GUIX ソース内で使用されます。 それらは ***tx_port.h** _ または _ *_gx_port.h_** のいずれかのファイル内にあります。

## <a name="customer-support-center"></a>カスタマー サポート センター

ご質問がある場合、サポートが必要な場合は、次の手順で Azure Portal からサポート チケットを提出します。 お客様のサポート リクエストをより効率的に解決できるように、以下の情報をメール メッセージに記載してください。

1. 問題の詳しい説明。発生頻度や、確実に再現できるかどうかなど。

2. 問題が発生する前にアプリケーションや Azure RTOS GUIX に行ったすべての変更に関する詳細な説明。

3. ご自身のディストリビューションの _tx_version_id および _fx_version_id 文字列の内容 (***tx_port.h**_ および _ *_fx_port.h_** ファイル内)。 これらの文字列から、実行時環境に関する重要な情報が得られます。

4. 次の ULONG 変数の RAM の内容。

    **_tx_build_options** **_gx_system_build_options**

    これらの変数から、Azure RTOS ThreadX と Azure RTOS GUIX のライブラリがどのように構築されたかに関する情報が得られます。

5. 次の ULONG 変数の RAM の内容。

    **_gx_system_last_error** **_gx_system_error_count**

    これらの変数により、Azure RTOS GUIX の内部システム エラーが追跡されます。 _gx_system_error_count が 1 より大きい場合は、_gx_system_error_process 関数の戻り値にブレークポイントを設定し、この時点での _gx_system_last_error の値をお知らせください。 これにより、最初の内部 Azure RTOS GUIX システム エラーが生成されます。

6. 問題が検出された直後にキャプチャされたトレース バッファー。 これを行うには、TX_ENABLE_EVENT_TRACE を使用して Azure RTOS ThreadX と Azure RTOS GUIX のライブラリを構築し、トレース バッファー情報を使用して tx_trace_enable を呼び出します。

7. 使用している Azure RTOS GUIX Studio プロジェクト (該当する場合)、または少なくとも報告している欠陥を示すのに十分な小さなプロジェクト。
