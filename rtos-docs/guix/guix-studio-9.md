---
title: GUIX Studio コマンド ライン
description: GUIX Studio によって提供されるコマンド ライン呼び出しは、Studio で生成される出力ファイルを更新するために必要なビルド パイプラインに役立ちます。
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9f9bfc67c524a77b5bf736407bf2ca372ce98308
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811108"
---
# <a name="chapter-9-guix-studio-command-line"></a>第 9 章: GUIX Studio コマンド ライン

GUIX Studio によってサポートされるコマンド ライン呼び出しは、Studio で生成される出力ファイルを更新するために必要なビルド パイプラインに役立ちます。

## <a name="command-line-usage"></a>コマンド ラインの使用

**使用方法:** guix_studio \[OPTION\] \[ARGUMENT\]

*.gxp* プロジェクトを開きます。

Studio プロジェクトを開き、目的の出力ファイルを生成します。


**例:**

`guix_studio demo.gxp`  
"demo.gxp" プロジェクトを開きます


`guix_studio.exe –p demo.gxp`  
"demo.gxp" プロジェクトを開きます


`guix_studio.exe –n –p demo.gxp`  
demo.gxp プロジェクトのすべての出力ファイルを生成します。

`guix_studio.exe –n –r –p demo.gxp`  
demo.gxp プロジェクトのリソース ファイルを生成します


## <a name="command-line-options"></a>コマンドライン オプション

```C
***-n --nogui***  
```

"nogui" オプション。 ウィンドウ形式の UI インターフェイスを開始しないで実行するよう GUIX Studio に指示します。

```C
***-o pathname***  
***--log***  
```

ログ オプション。ログ ファイルを指定します。

```C
***-b***  
***--binary***  
```

バイナリ リソース オプション。 C ファイルではなくバイナリ リソース ファイルを生成します。

```C
***-d display1, display2***  
***--display***  
```

表示名オプション。 このオプションを使用した場合、生成されるリソースまたは仕様ファイルには、指定した表示名だけが含まれます。 このオプションを使用しないと、すべての表示が含まれます。

```C
***-t theme1, theme2***  
***--theme***  
```

テーマ名オプション。 このオプションを使用した場合、生成されるリソースまたは仕様ファイルには、指定したテーマ名だけが含まれます。 このオプションを使用しないと、すべてのテーマが含まれます。

```C
***-l langage1, language2***  
***--language***  
```

言語名オプション。 このオプションを使用した場合、生成されるリソースまたは仕様ファイルには、指定した言語名が含まれます。 それ以外の場合は、すべての言語名が含まれます。

```C
***-r [filename]***  
***--resource***  
```

リソース オプション。前に指定した表示、テーマ、言語のリソース ファイルを生成する必要があることを、Studio に指定します。

```C
***-s [filename]***  
***--specification***  
```

仕様オプション。指定した表示、テーマ、言語の仕様ファイルを生成する必要があることを、Studio に指定します。

```C
***-p project_pathname***  
***--project***  
```

プロジェクト パス名オプション。読み込むプロジェクト例を指定します。

```C
***-i [pathname]***  
***--import***  
```

xliff または csv の形式のファイルから文字列をインポートします。

***--big_endian***  
ビッグエンディアン形式でリソース データを生成します。
