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
# <a name="about-guix-user-guide"></a><span data-ttu-id="e2859-103">GUIX ユーザー ガイドについて</span><span class="sxs-lookup"><span data-stu-id="e2859-103">About GUIX User Guide</span></span>

<span data-ttu-id="e2859-104">このガイドには、Microsoft のハイパフォーマンス GUI 製品である Azure RTOS GUIX に関する包括的な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e2859-104">This guide contains comprehensive information about Azure RTOS GUIX, the high-performance GUI product from Microsoft.</span></span> <span data-ttu-id="e2859-105">基本的な GUI の概念、Azure RTOS ThreadX、C プログラミング言語を理解している埋め込み型のリアルタイム ソフトウェア開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="e2859-105">It is intended for embedded real-time software developers familiar with basic GUI concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="e2859-106">Organization</span><span class="sxs-lookup"><span data-stu-id="e2859-106">Organization</span></span>

[<span data-ttu-id="e2859-107">第 1 章 - Azure RTOS GUIX の概要</span><span class="sxs-lookup"><span data-stu-id="e2859-107">Chapter 1 - Introduction to Azure RTOS GUIX</span></span>](chapter-1.md)

[<span data-ttu-id="e2859-108">第 2 章 - Azure RTOS GUIX のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="e2859-108">Chapter 2 - Installation and use of Azure RTOS GUIX</span></span>](chapter-2.md)

[<span data-ttu-id="e2859-109">第 3 章 - Azure RTOS GUIX の機能の概要</span><span class="sxs-lookup"><span data-stu-id="e2859-109">Chapter 3 - Functional Overview of Azure RTOS GUIX</span></span>](chapter-3.md)

[<span data-ttu-id="e2859-110">第 4 章 - Azure RTOS GUIX サービスの説明</span><span class="sxs-lookup"><span data-stu-id="e2859-110">Chapter 4 - Description of Azure RTOS GUIX Services</span></span>](chapter-4.md)

[<span data-ttu-id="e2859-111">第 5 章 - Azure RTOS GUIX ディスプレイ ドライバー</span><span class="sxs-lookup"><span data-stu-id="e2859-111">Chapter 5 - Azure RTOS GUIX Display Drivers</span></span>](chapter-5.md)  

[<span data-ttu-id="e2859-112">Azure RTOS GUIX の例</span><span class="sxs-lookup"><span data-stu-id="e2859-112">Azure RTOS GUIX Example</span></span>](guix-example.md)

[<span data-ttu-id="e2859-113">付録 A - Azure RTOS GUIX の色の定義</span><span class="sxs-lookup"><span data-stu-id="e2859-113">Appendix A - Azure RTOS GUIX Color Definitions</span></span>](appendix-a.md)

[<span data-ttu-id="e2859-114">付録 B - Azure RTOS GUIX の色の形式</span><span class="sxs-lookup"><span data-stu-id="e2859-114">Appendix B - Azure RTOS GUIX Color Formats</span></span>](appendix-b.md)

[<span data-ttu-id="e2859-115">付録 C - Azure RTOS GUIX ウィジェットのスタイル</span><span class="sxs-lookup"><span data-stu-id="e2859-115">Appendix C - Azure RTOS GUIX Widget Styles</span></span>](appendix-c.md)

[<span data-ttu-id="e2859-116">付録 D - Azure RTOS GUIX のブラシ、キャンバス、グラデーションの属性</span><span class="sxs-lookup"><span data-stu-id="e2859-116">Appendix D - Azure RTOS GUIX Brush, Canvas and Gradient Attributes</span></span>](appendix-d.md)

[<span data-ttu-id="e2859-117">付録 E - Azure RTOS GUIX イベントの説明</span><span class="sxs-lookup"><span data-stu-id="e2859-117">Appendix E - Azure RTOS GUIX Event Description</span></span>](appendix-e.md)

[<span data-ttu-id="e2859-118">付録 F - Azure RTOS GUIX RTOS バインド サービス</span><span class="sxs-lookup"><span data-stu-id="e2859-118">Appendix F - Azure RTOS GUIX RTOS Binding Services</span></span>](appendix-f.md)

[<span data-ttu-id="e2859-119">付録 G - Azure RTOS GUIX フォント構造体</span><span class="sxs-lookup"><span data-stu-id="e2859-119">Appendix G - Azure RTOS GUIX Font Structure</span></span>](appendix-g.md)

[<span data-ttu-id="e2859-120">付録 H - Azure RTOS GUIX のビルド時の構成フラグ</span><span class="sxs-lookup"><span data-stu-id="e2859-120">Appendix H - Azure RTOS GUIX Build-Time Configuration flags</span></span>](appendix-h.md)

[<span data-ttu-id="e2859-121">付録 I - Azure RTOS GUIX 情報構造</span><span class="sxs-lookup"><span data-stu-id="e2859-121">Appendix I - Azure RTOS GUIX Information Structures</span></span>](appendix-i.md)

## <a name="guide-conventions"></a><span data-ttu-id="e2859-122">ガイドの表記規則</span><span class="sxs-lookup"><span data-stu-id="e2859-122">Guide Conventions</span></span>

<span data-ttu-id="e2859-123">"*斜体*" - この書体は、本のタイトルを表し、重要な単語を強調し、変数を示すために使用されています。</span><span class="sxs-lookup"><span data-stu-id="e2859-123">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="e2859-124">**太字** - この書体は、ファイル名とキーワードを表し、重要な単語や変数をさらに強調するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e2859-124">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e2859-125">情報記号は、注意する必要がある、パフォーマンスや機能に影響を与える可能性のある重要な情報や追加情報を示します。</span><span class="sxs-lookup"><span data-stu-id="e2859-125">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

## <a name="azure-rtos-guix-data-types"></a><span data-ttu-id="e2859-126">Azure RTOS GUIX データ型</span><span class="sxs-lookup"><span data-stu-id="e2859-126">Azure RTOS GUIX Data Types</span></span>

<span data-ttu-id="e2859-127">カスタムの Azure RTOS GUIX 制御構造データ型に加えて、Azure RTOS GUIX サービス呼び出しインターフェイスで使用される特殊なデータ型がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="e2859-127">In addition to the custom Azure RTOS GUIX control structure data types, there are several special data types that are used in Azure RTOS GUIX service call interfaces.</span></span> <span data-ttu-id="e2859-128">これらの特殊データ型は、基になる C コンパイラのデータ型に直接マップされます。</span><span class="sxs-lookup"><span data-stu-id="e2859-128">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="e2859-129">これは、異なる C コンパイラ間での移植性を確保するために行われます。</span><span class="sxs-lookup"><span data-stu-id="e2859-129">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="e2859-130">正確な実装は ThreadX から継承されており、ThreadX ディストリビューションに含まれている ***tx_port.h*** ファイル内にあります。</span><span class="sxs-lookup"><span data-stu-id="e2859-130">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="e2859-131">Azure RTOS GUIX サービス呼び出しのデータ型と、それに関連付けられている意味の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e2859-131">The following is a list of Azure RTOS GUIX service call data types and their associated meanings:</span></span>

| <!-- --> | <!-- --> |
| --------------------- | --------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e2859-132">**UINT**</span><span class="sxs-lookup"><span data-stu-id="e2859-132">**UINT**</span></span>             | <span data-ttu-id="e2859-133">基本的な符号なし整数。</span><span class="sxs-lookup"><span data-stu-id="e2859-133">Basic unsigned integer.</span></span> <span data-ttu-id="e2859-134">この型は、最も便利な符号なしデータ型にマップされます。</span><span class="sxs-lookup"><span data-stu-id="e2859-134">This type is mapped to the most convenient unsigned data type.</span></span>                                |
| <span data-ttu-id="e2859-135">**INT**</span><span class="sxs-lookup"><span data-stu-id="e2859-135">**INT**</span></span>              | <span data-ttu-id="e2859-136">基本的な符号付き整数。</span><span class="sxs-lookup"><span data-stu-id="e2859-136">Basic signed integer.</span></span> <span data-ttu-id="e2859-137">この型は、最も便利な符号付きデータ型にマップされます。</span><span class="sxs-lookup"><span data-stu-id="e2859-137">This type is mapped to the most convenient signed data type.</span></span>                                    |
| <span data-ttu-id="e2859-138">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="e2859-138">**ULONG**</span></span>            | <span data-ttu-id="e2859-139">符号なし long 型。</span><span class="sxs-lookup"><span data-stu-id="e2859-139">Unsigned long type.</span></span> <span data-ttu-id="e2859-140">この型では、32 ビットの符号なしデータをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2859-140">This type must support 32-bit unsigned data.</span></span>                                                      |
| <span data-ttu-id="e2859-141">**VOID**</span><span class="sxs-lookup"><span data-stu-id="e2859-141">**VOID**</span></span>             | <span data-ttu-id="e2859-142">ほとんどの場合、コンパイラの void 型と同等です。</span><span class="sxs-lookup"><span data-stu-id="e2859-142">Almost always equivalent to the compiler’s void type.</span></span>                                                                 |
| <span data-ttu-id="e2859-143">**GX_CHAR**</span><span class="sxs-lookup"><span data-stu-id="e2859-143">**GX_CHAR**</span></span>         | <span data-ttu-id="e2859-144">多くの場合、コンパイラによって定義された char 型として型定義されています。</span><span class="sxs-lookup"><span data-stu-id="e2859-144">Most often typedefed as the compiler defined char type.</span></span>                                                               |
| <span data-ttu-id="e2859-145">**GX_BYTE**</span><span class="sxs-lookup"><span data-stu-id="e2859-145">**GX_BYTE**</span></span>          | <span data-ttu-id="e2859-146">8 ビットの符号付きの型。</span><span class="sxs-lookup"><span data-stu-id="e2859-146">8-bit signed type.</span></span>                                                                                                    |
| <span data-ttu-id="e2859-147">**GX_UBYTE**</span><span class="sxs-lookup"><span data-stu-id="e2859-147">**GX_UBYTE**</span></span>         | <span data-ttu-id="e2859-148">8 ビットの符号なしの型。</span><span class="sxs-lookup"><span data-stu-id="e2859-148">8-bit unsigned type.</span></span>                                                                                                  |
| <span data-ttu-id="e2859-149">**GX_VALUE**</span><span class="sxs-lookup"><span data-stu-id="e2859-149">**GX_VALUE**</span></span>        | <span data-ttu-id="e2859-150">16 または 32 ビットの符号付きの型。</span><span class="sxs-lookup"><span data-stu-id="e2859-150">16 or 32 bit signed type.</span></span> <span data-ttu-id="e2859-151">ターゲット システム上で最適なパフォーマンスを得るために必要に応じて定義されます。</span><span class="sxs-lookup"><span data-stu-id="e2859-151">Defined as needed for best performance on the target system.</span></span>                                |
| <span data-ttu-id="e2859-152">**GX_FIXED_VAL**</span><span class="sxs-lookup"><span data-stu-id="e2859-152">**GX_FIXED_VAL**</span></span>   | <span data-ttu-id="e2859-153">固定小数点数値データ型。</span><span class="sxs-lookup"><span data-stu-id="e2859-153">Fixed point numeric data type.</span></span>                                                                                        |
| <span data-ttu-id="e2859-154">**GX_RESOURCE_ID**</span><span class="sxs-lookup"><span data-stu-id="e2859-154">**GX_RESOURCE_ID**</span></span> | <span data-ttu-id="e2859-155">符号なし long 型。</span><span class="sxs-lookup"><span data-stu-id="e2859-155">Unsigned long type.</span></span>                                                                                                   |
| <span data-ttu-id="e2859-156">**GX_COLOR**</span><span class="sxs-lookup"><span data-stu-id="e2859-156">**GX_COLOR**</span></span>        | <span data-ttu-id="e2859-157">符号なし long 型。</span><span class="sxs-lookup"><span data-stu-id="e2859-157">Unsigned long type.</span></span>                                                                                                   |
| <span data-ttu-id="e2859-158">**GX_STRING**</span><span class="sxs-lookup"><span data-stu-id="e2859-158">**GX_STRING**</span></span>       | <span data-ttu-id="e2859-159">GX_CHAR \*gx_string_ptr および UINT gx_string_length を含む構造体。</span><span class="sxs-lookup"><span data-stu-id="e2859-159">Structure containing GX_CHAR \*gx_string_ptr and UINT gx_string_length.</span></span>                                          |
| <span data-ttu-id="e2859-160">**GX_POINT**</span><span class="sxs-lookup"><span data-stu-id="e2859-160">**GX_POINT**</span></span>        | <span data-ttu-id="e2859-161">gx_point_x と gx_point_y を含む構造体。</span><span class="sxs-lookup"><span data-stu-id="e2859-161">Structure containing gx_point_x and gx_point_y.</span></span>                                                                   |
| <span data-ttu-id="e2859-162">**GX_RECTANGLE**</span><span class="sxs-lookup"><span data-stu-id="e2859-162">**GX_RECTANGLE**</span></span>    | <span data-ttu-id="e2859-163">gx_rectangle_left、gx_rectangle_top、gx_rectangle_right、gx_rectangle_bottom の各フィールドを含む構造体。</span><span class="sxs-lookup"><span data-stu-id="e2859-163">Structure containing gx_rectangle_left, gx_rectangle_top, gx_rectangle_right, and gx_rectangle_bottom fields.</span></span> |
| <span data-ttu-id="e2859-164">**GX_GLYPH**</span><span class="sxs-lookup"><span data-stu-id="e2859-164">**GX_GLYPH**</span></span>        | <span data-ttu-id="e2859-165">グリフ メトリックを含む構造体。</span><span class="sxs-lookup"><span data-stu-id="e2859-165">Structure containing glyph metrics.</span></span>                                                                                   |
| <span data-ttu-id="e2859-166">**GX_FONT**</span><span class="sxs-lookup"><span data-stu-id="e2859-166">**GX_FONT**</span></span>         | <span data-ttu-id="e2859-167">フォント メトリックを含む構造体。</span><span class="sxs-lookup"><span data-stu-id="e2859-167">Structure containing font metrics.</span></span>                                                                                    |
| <span data-ttu-id="e2859-168">**GX_BRUSH**</span><span class="sxs-lookup"><span data-stu-id="e2859-168">**GX_BRUSH**</span></span>        | <span data-ttu-id="e2859-169">ブラシ メトリックを含む構造体。</span><span class="sxs-lookup"><span data-stu-id="e2859-169">Structure containing brush metrics.</span></span>                                                                               |
<span data-ttu-id="e2859-170">**GX_PIXELMAP**</span><span class="sxs-lookup"><span data-stu-id="e2859-170">**GX_PIXELMAP**</span></span>       | <span data-ttu-id="e2859-171">ピクセルマップ メトリックを含む構造体。</span><span class="sxs-lookup"><span data-stu-id="e2859-171">Structure containing pixelmap metrics.</span></span>

<span data-ttu-id="e2859-172">その他のデータ型は Azure RTOS GUIX ソース内で使用されます。</span><span class="sxs-lookup"><span data-stu-id="e2859-172">Additional data types are used within the Azure RTOS GUIX source.</span></span> <span data-ttu-id="e2859-173">それらは ***tx_port.h** _ または _ *_gx_port.h_** のいずれかのファイル内にあります。</span><span class="sxs-lookup"><span data-stu-id="e2859-173">They are located in either the ***tx_port.h** _ or _ *_gx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="e2859-174">カスタマー サポート センター</span><span class="sxs-lookup"><span data-stu-id="e2859-174">Customer Support Center</span></span>

<span data-ttu-id="e2859-175">ご質問がある場合、サポートが必要な場合は、次の手順で Azure Portal からサポート チケットを提出します。</span><span class="sxs-lookup"><span data-stu-id="e2859-175">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="e2859-176">お客様のサポート リクエストをより効率的に解決できるように、以下の情報をメール メッセージに記載してください。</span><span class="sxs-lookup"><span data-stu-id="e2859-176">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="e2859-177">問題の詳しい説明。発生頻度や、確実に再現できるかどうかなど。</span><span class="sxs-lookup"><span data-stu-id="e2859-177">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>

2. <span data-ttu-id="e2859-178">問題が発生する前にアプリケーションや Azure RTOS GUIX に行ったすべての変更に関する詳細な説明。</span><span class="sxs-lookup"><span data-stu-id="e2859-178">A detailed description of any changes to the application and/or Azure RTOS GUIX that preceded the problem.</span></span>

3. <span data-ttu-id="e2859-179">ご自身のディストリビューションの _tx_version_id および _fx_version_id 文字列の内容 (\***tx_port.h**_ および _ *_fx_port.h_*\* ファイル内)。</span><span class="sxs-lookup"><span data-stu-id="e2859-179">The contents of the _tx_version_id and _gx_version_id strings found in the \***tx_port.h**_ and _ *_gx_port.h_*\* files of your distribution.</span></span> <span data-ttu-id="e2859-180">これらの文字列から、実行時環境に関する重要な情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="e2859-180">These strings will provide us valuable Information regarding your run-time environment.</span></span>

4. <span data-ttu-id="e2859-181">次の ULONG 変数の RAM の内容。</span><span class="sxs-lookup"><span data-stu-id="e2859-181">The contents in RAM of the following ULONG variables:</span></span>

    <span data-ttu-id="e2859-182">**_tx_build_options** **_gx_system_build_options**</span><span class="sxs-lookup"><span data-stu-id="e2859-182">**_tx_build_options** **_gx_system_build_options**</span></span>

    <span data-ttu-id="e2859-183">これらの変数から、Azure RTOS ThreadX と Azure RTOS GUIX のライブラリがどのように構築されたかに関する情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="e2859-183">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS GUIX libraries were built.</span></span>

5. <span data-ttu-id="e2859-184">次の ULONG 変数の RAM の内容。</span><span class="sxs-lookup"><span data-stu-id="e2859-184">The contents in RAM of the following ULONG variables:</span></span>

    <span data-ttu-id="e2859-185">**_gx_system_last_error** **_gx_system_error_count**</span><span class="sxs-lookup"><span data-stu-id="e2859-185">**_gx_system_last_error** **_gx_system_error_count**</span></span>

    <span data-ttu-id="e2859-186">これらの変数により、Azure RTOS GUIX の内部システム エラーが追跡されます。</span><span class="sxs-lookup"><span data-stu-id="e2859-186">These variables keep track of internal system errors in Azure RTOS GUIX.</span></span> <span data-ttu-id="e2859-187">_gx_system_error_count が 1 より大きい場合は、_gx_system_error_process 関数の戻り値にブレークポイントを設定し、この時点での _gx_system_last_error の値をお知らせください。</span><span class="sxs-lookup"><span data-stu-id="e2859-187">If the _gx_system_error_count is greater than one, please set a breakpoint on the function return in the _gx_system_error_process function and provide the value of _gx_system_last_error at this point.</span></span> <span data-ttu-id="e2859-188">これにより、最初の内部 Azure RTOS GUIX システム エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="e2859-188">This will yield the first internal Azure RTOS GUIX system error.</span></span>

6. <span data-ttu-id="e2859-189">問題が検出された直後にキャプチャされたトレース バッファー。</span><span class="sxs-lookup"><span data-stu-id="e2859-189">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="e2859-190">これを行うには、TX_ENABLE_EVENT_TRACE を使用して Azure RTOS ThreadX と Azure RTOS GUIX のライブラリを構築し、トレース バッファー情報を使用して tx_trace_enable を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e2859-190">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS GUIX libraries with TX_ENABLE_EVENT_TRACE and calling tx_trace_enable with the trace buffer information.</span></span>

7. <span data-ttu-id="e2859-191">使用している Azure RTOS GUIX Studio プロジェクト (該当する場合)、または少なくとも報告している欠陥を示すのに十分な小さなプロジェクト。</span><span class="sxs-lookup"><span data-stu-id="e2859-191">The Azure RTOS GUIX Studio project you are using, if applicable, or at a minimum a small project sufficient to demonstrate the deficiency you are reporting.</span></span>
