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
# <a name="chapter-9-guix-studio-command-line"></a><span data-ttu-id="cac8b-103">第 9 章: GUIX Studio コマンド ライン</span><span class="sxs-lookup"><span data-stu-id="cac8b-103">Chapter 9: GUIX Studio Command Line</span></span>

<span data-ttu-id="cac8b-104">GUIX Studio によってサポートされるコマンド ライン呼び出しは、Studio で生成される出力ファイルを更新するために必要なビルド パイプラインに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="cac8b-104">GUIX Studio supports command-line invocation,  which is useful for build pipelines that are required to update of the Studio-generated output files.</span></span>

## <a name="command-line-usage"></a><span data-ttu-id="cac8b-105">コマンド ラインの使用</span><span class="sxs-lookup"><span data-stu-id="cac8b-105">Command-Line Usage</span></span>

<span data-ttu-id="cac8b-106">**使用方法:** guix_studio \[OPTION\] \[ARGUMENT\]</span><span class="sxs-lookup"><span data-stu-id="cac8b-106">**Usage:** guix_studio \[OPTION\] \[ARGUMENT\]</span></span>

<span data-ttu-id="cac8b-107">*.gxp* プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="cac8b-107">Open the *.gxp* project.</span></span>

<span data-ttu-id="cac8b-108">Studio プロジェクトを開き、目的の出力ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="cac8b-108">Open the Studio project and generate desired output files.</span></span>


<span data-ttu-id="cac8b-109">**例:**</span><span class="sxs-lookup"><span data-stu-id="cac8b-109">**Examples:**</span></span>

`guix_studio demo.gxp`  
<span data-ttu-id="cac8b-110">"demo.gxp" プロジェクトを開きます</span><span class="sxs-lookup"><span data-stu-id="cac8b-110">Open "demo.gxp" project</span></span>


`guix_studio.exe –p demo.gxp`  
<span data-ttu-id="cac8b-111">"demo.gxp" プロジェクトを開きます</span><span class="sxs-lookup"><span data-stu-id="cac8b-111">Open "demo.gxp" project</span></span>


`guix_studio.exe –n –p demo.gxp`  
<span data-ttu-id="cac8b-112">demo.gxp プロジェクトのすべての出力ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="cac8b-112">Generate all output files of demo.gxp project.</span></span>

`guix_studio.exe –n –r –p demo.gxp`  
<span data-ttu-id="cac8b-113">demo.gxp プロジェクトのリソース ファイルを生成します</span><span class="sxs-lookup"><span data-stu-id="cac8b-113">Generate resource files of demo.gxp project</span></span>


## <a name="command-line-options"></a><span data-ttu-id="cac8b-114">コマンドライン オプション</span><span class="sxs-lookup"><span data-stu-id="cac8b-114">Command-Line Options</span></span>

```C
***-n --nogui***  
```

<span data-ttu-id="cac8b-115">"nogui" オプション。</span><span class="sxs-lookup"><span data-stu-id="cac8b-115">The "nogui" option.</span></span> <span data-ttu-id="cac8b-116">ウィンドウ形式の UI インターフェイスを開始しないで実行するよう GUIX Studio に指示します。</span><span class="sxs-lookup"><span data-stu-id="cac8b-116">Tell GUIX Studio to run without starting the windowing UI interface.</span></span>

```C
***-o pathname***  
***--log***  
```

<span data-ttu-id="cac8b-117">ログ オプション。ログ ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="cac8b-117">Log option, specify a log file.</span></span>

```C
***-b***  
***--binary***  
```

<span data-ttu-id="cac8b-118">バイナリ リソース オプション。</span><span class="sxs-lookup"><span data-stu-id="cac8b-118">Binary resource option.</span></span> <span data-ttu-id="cac8b-119">C ファイルではなくバイナリ リソース ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="cac8b-119">Produces a binary resource file rather than a C file.</span></span>

```C
***-d display1, display2***  
***--display***  
```

<span data-ttu-id="cac8b-120">表示名オプション。</span><span class="sxs-lookup"><span data-stu-id="cac8b-120">Display names option.</span></span> <span data-ttu-id="cac8b-121">このオプションを使用した場合、生成されるリソースまたは仕様ファイルには、指定した表示名だけが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cac8b-121">If this option is used, then only the specified display names are included in any generated resource or specification files.</span></span> <span data-ttu-id="cac8b-122">このオプションを使用しないと、すべての表示が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cac8b-122">If this option is not used,  all displays are included.</span></span>

```C
***-t theme1, theme2***  
***--theme***  
```

<span data-ttu-id="cac8b-123">テーマ名オプション。</span><span class="sxs-lookup"><span data-stu-id="cac8b-123">Theme name(s) option.</span></span> <span data-ttu-id="cac8b-124">このオプションを使用した場合、生成されるリソースまたは仕様ファイルには、指定したテーマ名だけが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cac8b-124">If this option is used, then only the specified theme names are included in any generated resource or specification files.</span></span> <span data-ttu-id="cac8b-125">このオプションを使用しないと、すべてのテーマが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cac8b-125">If this option is not used, all themes are included.</span></span>

```C
***-l langage1, language2***  
***--language***  
```

<span data-ttu-id="cac8b-126">言語名オプション。</span><span class="sxs-lookup"><span data-stu-id="cac8b-126">Language name(s) option.</span></span> <span data-ttu-id="cac8b-127">このオプションを使用した場合、生成されるリソースまたは仕様ファイルには、指定した言語名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cac8b-127">If this option is used,  the specified language names are included in the generated resource or specification files.</span></span> <span data-ttu-id="cac8b-128">それ以外の場合は、すべての言語名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cac8b-128">Otherwise all language names are included.</span></span>

```C
***-r [filename]***  
***--resource***  
```

<span data-ttu-id="cac8b-129">リソース オプション。前に指定した表示、テーマ、言語のリソース ファイルを生成する必要があることを、Studio に指定します。</span><span class="sxs-lookup"><span data-stu-id="cac8b-129">The resource option, specifies that Studio should produce a resource file for previously designated display(s), theme(s), and language(s).</span></span>

```C
***-s [filename]***  
***--specification***  
```

<span data-ttu-id="cac8b-130">仕様オプション。指定した表示、テーマ、言語の仕様ファイルを生成する必要があることを、Studio に指定します。</span><span class="sxs-lookup"><span data-stu-id="cac8b-130">The specification option, specify that studio should produce a specification file for designated display(s), theme(s), and language(s).</span></span>

```C
***-p project_pathname***  
***--project***  
```

<span data-ttu-id="cac8b-131">プロジェクト パス名オプション。読み込むプロジェクト例を指定します。</span><span class="sxs-lookup"><span data-stu-id="cac8b-131">Project pathname option, specify the example project to be loaded.</span></span>

```C
***-i [pathname]***  
***--import***  
```

<span data-ttu-id="cac8b-132">xliff または csv の形式のファイルから文字列をインポートします。</span><span class="sxs-lookup"><span data-stu-id="cac8b-132">Import string from xliff or csv format file.</span></span>

<span data-ttu-id="cac8b-133">***--big_endian***</span><span class="sxs-lookup"><span data-stu-id="cac8b-133">***--big_endian***</span></span>  
<span data-ttu-id="cac8b-134">ビッグエンディアン形式でリソース データを生成します。</span><span class="sxs-lookup"><span data-stu-id="cac8b-134">Generate resource data in big-endian format.</span></span>
