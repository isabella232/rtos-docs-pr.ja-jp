---
title: 付録 C - GUIX ウィジェットのスタイル
description: GUIX ウィジェットのスタイルについて説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 83d5c5167739e91b7af8fce6b04213f610984fc6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812095"
---
# <a name="appendix-c---guix-widget-styles"></a><span data-ttu-id="e8223-103">付録 C - GUIX ウィジェットのスタイル</span><span class="sxs-lookup"><span data-stu-id="e8223-103">Appendix C - GUIX Widget Styles</span></span>

<span data-ttu-id="e8223-104">__"***全般的なスタイル (ほとんどのウィジェットの種類で使用されます):***"__</span><span class="sxs-lookup"><span data-stu-id="e8223-104">__***General Styles (Used with most widget types):***__</span></span>

<span data-ttu-id="e8223-105">**GX_STYLE_BORDER_NONE**</span><span class="sxs-lookup"><span data-stu-id="e8223-105">**GX_STYLE_BORDER_NONE**</span></span>
  - <span data-ttu-id="e8223-106">値: 0x00000000</span><span class="sxs-lookup"><span data-stu-id="e8223-106">Value: 0x00000000</span></span>
  - <span data-ttu-id="e8223-107">説明: このスタイルを使用すると、枠線なしでウィジェットを描画します。</span><span class="sxs-lookup"><span data-stu-id="e8223-107">Description: Use this style to draw a widget with no border.</span></span>

<span data-ttu-id="e8223-108">**GX_STYLE_BORDER_RAISED**</span><span class="sxs-lookup"><span data-stu-id="e8223-108">**GX_STYLE_BORDER_RAISED**</span></span>
  - <span data-ttu-id="e8223-109">値: 0x00000001</span><span class="sxs-lookup"><span data-stu-id="e8223-109">Value: 0x00000001</span></span>
  - <span data-ttu-id="e8223-110">説明: 浮き出した枠線でウィジェットを描画します。</span><span class="sxs-lookup"><span data-stu-id="e8223-110">Description: Draw widget with a raised border.</span></span>

<span data-ttu-id="e8223-111">**GX_STYLE_BORDER_RECESSED**</span><span class="sxs-lookup"><span data-stu-id="e8223-111">**GX_STYLE_BORDER_RECESSED**</span></span>
  - <span data-ttu-id="e8223-112">値: 0x00000002</span><span class="sxs-lookup"><span data-stu-id="e8223-112">Value: 0x00000002</span></span>
  - <span data-ttu-id="e8223-113">説明: くぼんだ枠線でウィジェットを描画します。</span><span class="sxs-lookup"><span data-stu-id="e8223-113">Description: Draw widget with a recessed border.</span></span>

<span data-ttu-id="e8223-114">**GX_STYLE_BORDER_THIN**</span><span class="sxs-lookup"><span data-stu-id="e8223-114">**GX_STYLE_BORDER_THIN**</span></span>
  - <span data-ttu-id="e8223-115">値: 0x00000004</span><span class="sxs-lookup"><span data-stu-id="e8223-115">Value: 0x00000004</span></span>
  - <span data-ttu-id="e8223-116">説明: 1 ピクセル幅の枠線を描画します。</span><span class="sxs-lookup"><span data-stu-id="e8223-116">Description: Draw a one-pixel width border.</span></span>

<span data-ttu-id="e8223-117">**GX_STYLE_BORDER_THICK**</span><span class="sxs-lookup"><span data-stu-id="e8223-117">**GX_STYLE_BORDER_THICK**</span></span> 
  - <span data-ttu-id="e8223-118">値: 0x00000008</span><span class="sxs-lookup"><span data-stu-id="e8223-118">Value: 0x00000008</span></span>
  - <span data-ttu-id="e8223-119">説明: 太い枠線でウィジェットを描画します。</span><span class="sxs-lookup"><span data-stu-id="e8223-119">Description: Draw widget with a thick border.</span></span>

<span data-ttu-id="e8223-120">**GX_STYLE_BORDER_MASK**</span><span class="sxs-lookup"><span data-stu-id="e8223-120">**GX_STYLE_BORDER_MASK**</span></span>
  - <span data-ttu-id="e8223-121">値: 0x0000000f</span><span class="sxs-lookup"><span data-stu-id="e8223-121">Value: 0x0000000f</span></span>
  - <span data-ttu-id="e8223-122">説明: ウィジェット スタイルのメンバーのスタイル フィールドのみをテストするために使用するマスク値です。</span><span class="sxs-lookup"><span data-stu-id="e8223-122">Description: Mask value used to test only the style fields of the widget style member.</span></span>

<span data-ttu-id="e8223-123">**GX_STYLE_TRANSPARENT**</span><span class="sxs-lookup"><span data-stu-id="e8223-123">**GX_STYLE_TRANSPARENT**</span></span>
  - <span data-ttu-id="e8223-124">値: 0x10000000</span><span class="sxs-lookup"><span data-stu-id="e8223-124">Value: 0x10000000</span></span>
  - <span data-ttu-id="e8223-125">説明: 少なくとも部分的に透明なウィジェットを作成します。</span><span class="sxs-lookup"><span data-stu-id="e8223-125">Description: Create a widget that is at least partially transparent.</span></span> <span data-ttu-id="e8223-126">このスタイルは、ウィジェット自体が完全に不透明には描画されない場合に使用します。これには、ウィジェットの背景として半透明なピクセルマップを描画するウィジェットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e8223-126">This style should be used when a widget does not draw itself fully opaque, including widgets that draw a semi-transparent pixelmap as the widget background.</span></span> <span data-ttu-id="e8223-127">このスタイル フラグを使用すると、ウィジェットの背景領域を更新するためにウィジェットの親を描画する必要があることが GUIX に伝えられます。</span><span class="sxs-lookup"><span data-stu-id="e8223-127">This style flag informs GUIX that the widget parent must be drawn to refresh the widget background area.</span></span>

<span data-ttu-id="e8223-128">**GX_STYLE_DRAW_SELECTED**</span><span class="sxs-lookup"><span data-stu-id="e8223-128">**GX_STYLE_DRAW_SELECTED**</span></span>
  - <span data-ttu-id="e8223-129">値: 0x20000000</span><span class="sxs-lookup"><span data-stu-id="e8223-129">Value: 0x20000000</span></span>
  - <span data-ttu-id="e8223-130">説明: 選択した状態の色とフォントを使用してウィジェットを描画するように指定します。</span><span class="sxs-lookup"><span data-stu-id="e8223-130">Description: Specify that the widget should be drawn using selected state colors and fonts.</span></span> <span data-ttu-id="e8223-131">異なるウィジェットの種類では、異なる方法で DRAW_SELECTED を使用して、ウィジェットが現在選択されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="e8223-131">Different widget types use the DRAW_SELECTED style in different ways to indicate the widget is currently selected.</span></span>

<span data-ttu-id="e8223-132">**GX_STYLE_ENABLED**</span><span class="sxs-lookup"><span data-stu-id="e8223-132">**GX_STYLE_ENABLED**</span></span>
  - <span data-ttu-id="e8223-133">値: 0x40000000</span><span class="sxs-lookup"><span data-stu-id="e8223-133">Value: 0x40000000</span></span>
  - <span data-ttu-id="e8223-134">説明: ウィジェットを有効としてマークします。これにより、ウィジェットによるユーザー入力イベントの受け入れと出力シグナルの生成が可能になります。</span><span class="sxs-lookup"><span data-stu-id="e8223-134">Description: Mark the widget as enabled, which allows the widget to accept user input events and generate output signals.</span></span>
  
<span data-ttu-id="e8223-135">**GX_STYLE_DYNAMICALLY_ALLOCATED**</span><span class="sxs-lookup"><span data-stu-id="e8223-135">**GX_STYLE_DYNAMICALLY_ALLOCATED**</span></span>
  - <span data-ttu-id="e8223-136">値: 0x80000000</span><span class="sxs-lookup"><span data-stu-id="e8223-136">Value: 0x80000000</span></span>
  - <span data-ttu-id="e8223-137">説明: ウィジェットの作成時に、gx_system_memory_allocator サービスを使用して、ウィジェット コントロール ブロック メモリを動的に割り当てることを示します。ウィジェットが破棄されるとコントロール ブロック メモリは解放されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-137">Description: Indicates the widget control block memory is dynamically allocated using the gx_system_memory_allocator service when the widget is created, and the control block memory is freed if the widget is destroyed.</span></span>

<span data-ttu-id="e8223-138">**GX_STYLE_USE_LOCAL_ALPHA**</span><span class="sxs-lookup"><span data-stu-id="e8223-138">**GX_STYLE_USE_LOCAL_ALPHA**</span></span>
  - <span data-ttu-id="e8223-139">値: 0x01000000</span><span class="sxs-lookup"><span data-stu-id="e8223-139">Value: 0x01000000</span></span>
  - <span data-ttu-id="e8223-140">説明: ウィジェットを描画するときにローカルのウィジェット アルファ値を使用するように、GUIX の描画関数に指示します。</span><span class="sxs-lookup"><span data-stu-id="e8223-140">Description: Instructs GUIX drawing functions to use the local widget alpha value when drawing the widget.</span></span> <span data-ttu-id="e8223-141">通常、このフラグは、ウィジェットのフェード アニメーションを実装するために GUIX の内部ロジックによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-141">This flag is normally used by the internal GUIX logic to implement widget fading animations.</span></span>


<span data-ttu-id="e8223-142">__"***テキストの配置スタイル (テキストを描画するすべてのウィジェットに適用されるスタイル):***"__</span><span class="sxs-lookup"><span data-stu-id="e8223-142">__***Text Alignment Styles (styles applied to all widgets that draw text):***__</span></span>

<span data-ttu-id="e8223-143">**GX_STYLE_TEXT_LEFT**</span><span class="sxs-lookup"><span data-stu-id="e8223-143">**GX_STYLE_TEXT_LEFT**</span></span>
  - <span data-ttu-id="e8223-144">値: 0x00001000</span><span class="sxs-lookup"><span data-stu-id="e8223-144">Value: 0x00001000</span></span>
  - <span data-ttu-id="e8223-145">説明: テキストが、ウィジェットのクライアント領域内に、左揃えで描画されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-145">Description: Text is drawn left-aligned within the widget client area.</span></span>

<span data-ttu-id="e8223-146">**GX_STYLE_TEXT_RIGHT**</span><span class="sxs-lookup"><span data-stu-id="e8223-146">**GX_STYLE_TEXT_RIGHT**</span></span> 
  - <span data-ttu-id="e8223-147">値: 0x00002000</span><span class="sxs-lookup"><span data-stu-id="e8223-147">Value: 0x00002000</span></span>
  - <span data-ttu-id="e8223-148">説明: テキストが右揃えで、ウィジェットのクライアント領域に描画されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-148">Description: Text is drawn right-aligned within the widget client area.</span></span>

<span data-ttu-id="e8223-149">**GX_STYLE_TEXT_CENTER**</span><span class="sxs-lookup"><span data-stu-id="e8223-149">**GX_STYLE_TEXT_CENTER**</span></span>
  - <span data-ttu-id="e8223-150">値: 0x00004000</span><span class="sxs-lookup"><span data-stu-id="e8223-150">Value: 0x00004000</span></span>
  - <span data-ttu-id="e8223-151">説明: テキストが中央揃えで、ウィジェットのクライアント領域に描画されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-151">Description: Text is drawn center-aligned within the widget client area.</span></span>

<span data-ttu-id="e8223-152">**GX_STYLE_TEXT_COPY**</span><span class="sxs-lookup"><span data-stu-id="e8223-152">**GX_STYLE_TEXT_COPY**</span></span>
  - <span data-ttu-id="e8223-153">値: 0x00008000</span><span class="sxs-lookup"><span data-stu-id="e8223-153">Value: 0x00008000</span></span>
  - <span data-ttu-id="e8223-154">説明: 既定では、テキストを描画するウィジェットには、アプリケーションによって渡されたテキストへのポインターのみが保持されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-154">Description: By default, widgets that draw text keep only a pointer to the text which is passed in by the application.</span></span> <span data-ttu-id="e8223-155">文字列テーブル内で定義されている静的に定義されたテキストの場合、ウィジェットでは、割り当てられたテキストのプライベート コピーを作成する理由はありません。</span><span class="sxs-lookup"><span data-stu-id="e8223-155">For statically defined text that is defined within the string table, there is no reason for the widget to make a private copy of the text assigned.</span></span> <span data-ttu-id="e8223-156">ただし、ウィジェットに割り当てられるテキストが、sprint() や gx_utility_ltoa などの関数を使用して動的に作成される場合は、割り当てられたテキストの独自のプライベート コピーを保持するようにウィジェットに指示すると便利なことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="e8223-156">However, if the text assigned to a widget is created dynamically using functions like sprint() or gx_utility_ltoa, then it is often convenient to tell the widget to keep it’s own private copy of any text assigned.</span></span> <span data-ttu-id="e8223-157">これにより、アプリケーションでは、テキスト文字列を定義するときに自動変数または一時変数を使用できます。そうでない場合、アプリケーションでは、動的に定義されたテキストを使用するテキスト ウィジェットごとに、静的に定義された文字配列を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8223-157">This allows the application to use automatic or temporary variables when defining the text string, when the application would otherwise be required to define statically defined character arrays for each text widget that is using dynamically defined text.</span></span> <span data-ttu-id="e8223-158">このスタイル フラグが設定されている場合、ウィジェットでは gx_system_memory_allocator 関数を使用して、割り当てられた文字列のプライベート コピーを保持するために必要なメモリ ブロックが動的に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="e8223-158">When this style flag is set, the widget will use the gx_system_memory_allocator function to dynamically allocate the memory block needed to hold a private copy of the assigned string.</span></span> <span data-ttu-id="e8223-159">したがって、このスタイル フラグの使用は、memory_allocator および memory_deallocator 関数を定義するアプリケーションを前提としています。</span><span class="sxs-lookup"><span data-stu-id="e8223-159">Therefore using this style flag is predicated on the application defining memory_allocator and memory_deallocator functions.</span></span> <span data-ttu-id="e8223-160">GX_STYLE_TEXT_COPY を設定した後は、クリアしないでください。クリアすると予期しない結果が発生します。</span><span class="sxs-lookup"><span data-stu-id="e8223-160">GX_STYLE_TEXT_COPY should not be cleared after it has been set, and doing so will cause unpredictable results.</span></span>

<span data-ttu-id="e8223-161">__"***ボタン スタイル (GUIX のボタン ウィジェットの種類にのみ適用されます):***"__</span><span class="sxs-lookup"><span data-stu-id="e8223-161">__***Button Styles (apply only to GUIX button widget types):***__</span></span>

<span data-ttu-id="e8223-162">**GX_STYLE_BUTTON_PUSHED**</span><span class="sxs-lookup"><span data-stu-id="e8223-162">**GX_STYLE_BUTTON_PUSHED**</span></span>
  - <span data-ttu-id="e8223-163">値 0x00000010</span><span class="sxs-lookup"><span data-stu-id="e8223-163">Value 0x00000010</span></span>
  - <span data-ttu-id="e8223-164">説明: ボタンが押された状態、または選択された状態であることを示します。</span><span class="sxs-lookup"><span data-stu-id="e8223-164">Description: Indicates the button is in the pushed or selected state.</span></span>

<span data-ttu-id="e8223-165">**GX_STYLE_BUTTON_TOGGLE**</span><span class="sxs-lookup"><span data-stu-id="e8223-165">**GX_STYLE_BUTTON_TOGGLE**</span></span>
  - <span data-ttu-id="e8223-166">値 0x00000020</span><span class="sxs-lookup"><span data-stu-id="e8223-166">Value 0x00000020</span></span>
  - <span data-ttu-id="e8223-167">説明: クリック イベントが発生するたびに、ボタンの状態が押された状態と押されていない状態で切り替わります。</span><span class="sxs-lookup"><span data-stu-id="e8223-167">Description: Button will switch status between pushed and unpushed on every click event.</span></span> <span data-ttu-id="e8223-168">通常、このスタイルは "チェックボックス" スタイルのボタンと共に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-168">This style is commonly used with “checkbox” style buttons.</span></span>

<span data-ttu-id="e8223-169">**GX_STYLE_BUTTON_RADIO**</span><span class="sxs-lookup"><span data-stu-id="e8223-169">**GX_STYLE_BUTTON_RADIO**</span></span>
  - <span data-ttu-id="e8223-170">値 0x00000040</span><span class="sxs-lookup"><span data-stu-id="e8223-170">Value 0x00000040</span></span>
  - <span data-ttu-id="e8223-171">説明: このスタイルは、ボタンが排他的になり、選択されるとすべての兄弟ボタンが選択解除されることを示します。</span><span class="sxs-lookup"><span data-stu-id="e8223-171">Description: This style indicates the button will be exclusive, and deselect any button siblings when selected.</span></span> <span data-ttu-id="e8223-172">通常、このスタイルは "ラジオ ボタン" スタイルのボタンと共に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-172">This style is commonly used with “radio button” style buttons.</span></span>

<span data-ttu-id="e8223-173">**GX_STYLE_BUTTON_EVENT_ON_PUSH**</span><span class="sxs-lookup"><span data-stu-id="e8223-173">**GX_STYLE_BUTTON_EVENT_ON_PUSH**</span></span>
  - <span data-ttu-id="e8223-174">値: 0x00000080</span><span class="sxs-lookup"><span data-stu-id="e8223-174">Value: 0x00000080</span></span>
  - <span data-ttu-id="e8223-175">説明: 最初に押されたときに、ボタンによってクリック イベントが生成されることを示します。</span><span class="sxs-lookup"><span data-stu-id="e8223-175">Description: Indicates the button generates a click event when initially pushed.</span></span> <span data-ttu-id="e8223-176">既定の操作では、ボタンが離されたときにクリック イベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-176">The default operation is to generate a click event when the button is released.</span></span>

<span data-ttu-id="e8223-177">**GX_STYLE_BUTTON_REPEAT**</span><span class="sxs-lookup"><span data-stu-id="e8223-177">**GX_STYLE_BUTTON_REPEAT**</span></span>
  - <span data-ttu-id="e8223-178">値 0x00000100</span><span class="sxs-lookup"><span data-stu-id="e8223-178">Value 0x00000100</span></span>
  - <span data-ttu-id="e8223-179">説明: ボタンが押された状態のままであるときに、ボタンからボタンの親に繰り返しクリック イベントを送信する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="e8223-179">Description: Indicates the button should send repeated click events to the button parent when the button is held in the pushed state.</span></span>

<span data-ttu-id="e8223-180">__"***リスト スタイル (GUIX のリスト ウィジェットの種類にのみ適用されます):***"__</span><span class="sxs-lookup"><span data-stu-id="e8223-180">__***List Styles (apply only to GUIX list widget types):***__</span></span>

<span data-ttu-id="e8223-181">**GX_STYLE_CENTER_SELECTED**</span><span class="sxs-lookup"><span data-stu-id="e8223-181">**GX_STYLE_CENTER_SELECTED**</span></span> 
  - <span data-ttu-id="e8223-182">値: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="e8223-182">Value: 0x00000010</span></span>
  - <span data-ttu-id="e8223-183">説明: 予約済み</span><span class="sxs-lookup"><span data-stu-id="e8223-183">Description: Reserved</span></span>

<span data-ttu-id="e8223-184">**GX_STYLE_WRAP**</span><span class="sxs-lookup"><span data-stu-id="e8223-184">**GX_STYLE_WRAP**</span></span>
  - <span data-ttu-id="e8223-185">値 0x00000020</span><span class="sxs-lookup"><span data-stu-id="e8223-185">Value 0x00000020</span></span>
  - <span data-ttu-id="e8223-186">説明: リストが、先頭または末尾のリスト インデックスを超えてドラッグまたはスクロールされると、リストの子が先頭から末尾に折り返されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-186">Description: The list children wrap from start to end when the list is dragged or scrolled past the starting or ending list index.</span></span>

<span data-ttu-id="e8223-187">**GX_STYLE_FLICKABLE**</span><span class="sxs-lookup"><span data-stu-id="e8223-187">**GX_STYLE_FLICKABLE**</span></span>
  - <span data-ttu-id="e8223-188">値: 0x00000040</span><span class="sxs-lookup"><span data-stu-id="e8223-188">Value: 0x00000040</span></span>
  - <span data-ttu-id="e8223-189">説明: 予約済み</span><span class="sxs-lookup"><span data-stu-id="e8223-189">Description: Reserved</span></span>

<span data-ttu-id="e8223-190">__"***ピクセルマップ ボタンとアイコン ボタンのスタイル:***"__</span><span class="sxs-lookup"><span data-stu-id="e8223-190">__***Pixelmap Button and Icon Button Styles:***__</span></span>

<span data-ttu-id="e8223-191">**GX_STYLE_HALIGN_CENTER**</span><span class="sxs-lookup"><span data-stu-id="e8223-191">**GX_STYLE_HALIGN_CENTER**</span></span>
  - <span data-ttu-id="e8223-192">値: 0x00010000</span><span class="sxs-lookup"><span data-stu-id="e8223-192">Value: 0x00010000</span></span>
  - <span data-ttu-id="e8223-193">説明: ボタンのピクセルマップは、ボタンの境界内で、水平軸上で中央揃えになります。</span><span class="sxs-lookup"><span data-stu-id="e8223-193">Description: The button pixelmap should be center aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="e8223-194">**GX_STYLE_HALIGN_LEFT**</span><span class="sxs-lookup"><span data-stu-id="e8223-194">**GX_STYLE_HALIGN_LEFT**</span></span>
  - <span data-ttu-id="e8223-195">値: 0x00020000</span><span class="sxs-lookup"><span data-stu-id="e8223-195">Value: 0x00020000</span></span>
  - <span data-ttu-id="e8223-196">説明: ボタンのピクセルマップは、ボタンの境界内で、水平軸上で左揃えになります。</span><span class="sxs-lookup"><span data-stu-id="e8223-196">Description: The button pixelmap should be left aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="e8223-197">**GX_STYLE_HALIGN_RIGHT**</span><span class="sxs-lookup"><span data-stu-id="e8223-197">**GX_STYLE_HALIGN_RIGHT**</span></span>
  - <span data-ttu-id="e8223-198">値 0x00040000</span><span class="sxs-lookup"><span data-stu-id="e8223-198">Value 0x00040000</span></span>
  - <span data-ttu-id="e8223-199">説明: ボタンのピクセルマップは、ボタンの境界内で、水平軸上で右揃えになります。</span><span class="sxs-lookup"><span data-stu-id="e8223-199">Description: The button pixelmap should be right aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="e8223-200">**GX_STYLE_VALIGN_CENTER**</span><span class="sxs-lookup"><span data-stu-id="e8223-200">**GX_STYLE_VALIGN_CENTER**</span></span>
  - <span data-ttu-id="e8223-201">値 0x00080000</span><span class="sxs-lookup"><span data-stu-id="e8223-201">Value 0x00080000</span></span>
  - <span data-ttu-id="e8223-202">説明: ボタンのピクセルマップは、ボタンの境界内で、垂直軸上で中央揃えになります。</span><span class="sxs-lookup"><span data-stu-id="e8223-202">Description: The button pixelmap should be center aligned within the button boundary on the vertical axis.</span></span>

<span data-ttu-id="e8223-203">**GX_STYLE_VALIGN_TOP**</span><span class="sxs-lookup"><span data-stu-id="e8223-203">**GX_STYLE_VALIGN_TOP**</span></span>
  - <span data-ttu-id="e8223-204">値: 0x00100000</span><span class="sxs-lookup"><span data-stu-id="e8223-204">Value: 0x00100000</span></span>
  - <span data-ttu-id="e8223-205">説明: ボタンのピクセルマップは、ボタンの境界内で、垂直軸上で上端揃えになります。</span><span class="sxs-lookup"><span data-stu-id="e8223-205">Description: The button pixelmap should be top aligned within the button boundary on the vertical axis.</span></span>

<span data-ttu-id="e8223-206">**GX_STYLE_VALIGN_BOTTOM**</span><span class="sxs-lookup"><span data-stu-id="e8223-206">**GX_STYLE_VALIGN_BOTTOM**</span></span>
  - <span data-ttu-id="e8223-207">値: 0x00200000</span><span class="sxs-lookup"><span data-stu-id="e8223-207">Value: 0x00200000</span></span>
  - <span data-ttu-id="e8223-208">説明: ボタンのピクセルマップは、ボタンの境界内で、垂直水平軸上で下端揃えになります。</span><span class="sxs-lookup"><span data-stu-id="e8223-208">Description: The button pixelmap should be bottom aligned within the button boundary on the vertical horizontal axis.</span></span>

<span data-ttu-id="e8223-209">__"***スライダー スタイル (GX_SLIDER と派生ウィジェットの種類にのみ適用されます):***"__</span><span class="sxs-lookup"><span data-stu-id="e8223-209">__***Slider Styles (Appy only to GX_SLIDER and derived widget types):***__</span></span>

<span data-ttu-id="e8223-210">**GX_STYLE_SHOW_NEEDLE**</span><span class="sxs-lookup"><span data-stu-id="e8223-210">**GX_STYLE_SHOW_NEEDLE**</span></span>
  - <span data-ttu-id="e8223-211">値: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="e8223-211">Value: 0x00000200</span></span>
  - <span data-ttu-id="e8223-212">説明: スライダーで針インジケーターを描画するには、このスタイルを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8223-212">Description: This style must be included for the slider to draw the needle indicator.</span></span> <span data-ttu-id="e8223-213">アプリケーションでスライダーの針を無効にしたり、カスタムの針インジケーターを描画したりする場合は、このスタイルを無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="e8223-213">This style can be disabled if the application wants to disable the slider needle or draw a custom needle indicator.</span></span>

<span data-ttu-id="e8223-214">**GX_STYLE_SHOW_TICKMARKS**</span><span class="sxs-lookup"><span data-stu-id="e8223-214">**GX_STYLE_SHOW_TICKMARKS**</span></span>
  - <span data-ttu-id="e8223-215">値: 0x00000400</span><span class="sxs-lookup"><span data-stu-id="e8223-215">Value: 0x00000400</span></span>
  - <span data-ttu-id="e8223-216">説明: このスタイルが有効になっている場合、スライダー ウィジェットでは目盛りの破線がソフトウェアによって描画されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-216">Description: The slider widget will do software drawing of dashed tickmark lines when this style is enabled.</span></span>

<span data-ttu-id="e8223-217">**GX_STYLE_SLIDER_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="e8223-217">**GX_STYLE_SLIDER_VERTICAL**</span></span>
  - <span data-ttu-id="e8223-218">値 0x00000800</span><span class="sxs-lookup"><span data-stu-id="e8223-218">Value 0x00000800</span></span>
  - <span data-ttu-id="e8223-219">説明: このスタイル フラグを設定すると垂直スライダーを作成し、このスタイル フラグをクリアすると水平スライダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e8223-219">Description: Set this style flag to create a vertical slider, and clear this style flag to create a horizontal slider.</span></span>

<span data-ttu-id="e8223-220">__"***スプライト スタイル (GX_SPRITE のウィジェットの種類にのみ適用されます):***"__</span><span class="sxs-lookup"><span data-stu-id="e8223-220">__***Sprite Styles (Applies only to GX_SPRITE widget types):***__</span></span>

<span data-ttu-id="e8223-221">**GX_STYLE_SPRITE_AUTO**</span><span class="sxs-lookup"><span data-stu-id="e8223-221">**GX_STYLE_SPRITE_AUTO**</span></span>
  - <span data-ttu-id="e8223-222">値: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="e8223-222">Value: 0x00000010</span></span>
  - <span data-ttu-id="e8223-223">説明: スプライト ウィジェットが GX_EVENT_SHOW イベントを受信したときに、スプライト アニメーションが自動的に実行されることを示します。</span><span class="sxs-lookup"><span data-stu-id="e8223-223">Description: Indicates the sprite animation will run automatically when the sprite widget received the GX_EVENT_SHOW event.</span></span>

<span data-ttu-id="e8223-224">**GX_STYLE_SPRITE_LOOP**</span><span class="sxs-lookup"><span data-stu-id="e8223-224">**GX_STYLE_SPRITE_LOOP**</span></span>
  - <span data-ttu-id="e8223-225">値: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="e8223-225">Value: 0x00000020</span></span>
  - <span data-ttu-id="e8223-226">説明: このスタイルを使用する場合、スプライト ウィジェットでは、アプリケーションによってスプライトが停止されるまで、スプライト アニメーション フレームが連続してループします。</span><span class="sxs-lookup"><span data-stu-id="e8223-226">Description: With this style, the sprite widget will continuously loop through sprite animation frames until the sprite is stopped by the application.</span></span>

<span data-ttu-id="e8223-227">__"***ピクセルマップ スライダー スタイル:***"__</span><span class="sxs-lookup"><span data-stu-id="e8223-227">__***Pixelmap Slider Styles:***__</span></span>

<span data-ttu-id="e8223-228">**GX_STYLE_TILE_BACKGROUND**</span><span class="sxs-lookup"><span data-stu-id="e8223-228">**GX_STYLE_TILE_BACKGROUND**</span></span>
  - <span data-ttu-id="e8223-229">値 0x00001000</span><span class="sxs-lookup"><span data-stu-id="e8223-229">Value 0x00001000</span></span>
  - <span data-ttu-id="e8223-230">説明: スライダーの背景画像を、スプライトの四角形領域全体に並べて表示します。</span><span class="sxs-lookup"><span data-stu-id="e8223-230">Description: The slider background image is tiled to fill the sprite bounding rectangle.</span></span> <span data-ttu-id="e8223-231">これにより、小さな縦または横のストライプ画像を使用して、スライダーの背景を埋めることができます。</span><span class="sxs-lookup"><span data-stu-id="e8223-231">This allows a small vertical or horizontal stripe image to be used to fill the slider background.</span></span>

<span data-ttu-id="e8223-232">__"***追加の進行状況バー スタイル:***"__</span><span class="sxs-lookup"><span data-stu-id="e8223-232">__***Additional Progress Bar Styles:***__</span></span>

<span data-ttu-id="e8223-233">**GX_STYLE_PROGRESS_PERCENT**</span><span class="sxs-lookup"><span data-stu-id="e8223-233">**GX_STYLE_PROGRESS_PERCENT**</span></span>
  - <span data-ttu-id="e8223-234">値: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="e8223-234">Value: 0x00000010</span></span>
  - <span data-ttu-id="e8223-235">説明: このスタイルを設定すると、進行状況バーのバーの値が、生の値ではなくパーセンテージとして描画されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-235">Description: When this style is set, the progress bar will draw  bar value as a percentage rather than a raw value.</span></span> <span data-ttu-id="e8223-236">テキストは、進行状況バーの四角形領域内の中央に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-236">The text is centered in the progress bar bounding rectangle.</span></span>

<span data-ttu-id="e8223-237">**GX_STYLE_PROGRESS_TEXT_DRAW**</span><span class="sxs-lookup"><span data-stu-id="e8223-237">**GX_STYLE_PROGRESS_TEXT_DRAW**</span></span>
  - <span data-ttu-id="e8223-238">値: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="e8223-238">Value: 0x00000020</span></span>
  - <span data-ttu-id="e8223-239">説明: 現在の進行状況バーの値を、進行状況バー内の中央に表示される 10 進数のテキストとして描画します。</span><span class="sxs-lookup"><span data-stu-id="e8223-239">Description: Draw the current progress bar value as decimal text centered within the progress bar.</span></span>

<span data-ttu-id="e8223-240">**GX_STYLE_PROGRESS_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="e8223-240">**GX_STYLE_PROGRESS_VERTICAL**</span></span>
  - <span data-ttu-id="e8223-241">値: 0x0000040</span><span class="sxs-lookup"><span data-stu-id="e8223-241">Value: 0x0000040</span></span>
  - <span data-ttu-id="e8223-242">説明: 進行状況が垂直方向になることを示します。</span><span class="sxs-lookup"><span data-stu-id="e8223-242">Description: Indicate the progress is vertically oriented.</span></span> <span data-ttu-id="e8223-243">既定値は水平方向です。</span><span class="sxs-lookup"><span data-stu-id="e8223-243">The default is horizontal orientation.</span></span>

<span data-ttu-id="e8223-244">**GX_STYLE_PROGRESS_SEGMENT_FILL**:</span><span class="sxs-lookup"><span data-stu-id="e8223-244">**GX_STYLE_PROGRESS_SEGMENT_FILL**:</span></span>
  - <span data-ttu-id="e8223-245">**値**: 0x00000100</span><span class="sxs-lookup"><span data-stu-id="e8223-245">**Value**: 0x00000100</span></span>
  - <span data-ttu-id="e8223-246">説明: 進行状況バーの値は、純色の塗りつぶしではなく、セグメント化された塗りつぶし四角形で示されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-246">Description: The progress bar value is indicated with segmented filled rectangles, rather than a solid fill.</span></span>

<span data-ttu-id="e8223-247">__"***追加の放射状進行状況バー スタイル:***"__</span><span class="sxs-lookup"><span data-stu-id="e8223-247">__***Additional Radial Progress Bar Styles:***__</span></span>

<span data-ttu-id="e8223-248">**GX_STYLE_RADIAL_PROGRESS_ALIAS**</span><span class="sxs-lookup"><span data-stu-id="e8223-248">**GX_STYLE_RADIAL_PROGRESS_ALIAS**</span></span>
  - <span data-ttu-id="e8223-249">値: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="e8223-249">Value: 0x00000200</span></span>
  - <span data-ttu-id="e8223-250">説明: アンチエイリアス ブラシ スタイルを使用して放射状の進行状況バーを描画します。</span><span class="sxs-lookup"><span data-stu-id="e8223-250">Description: Draw the radial progress bar using anti-aliased brush styles.</span></span> <span data-ttu-id="e8223-251">これにはより多くの CPU 帯域幅が必要になりますが、見栄えもよくなります。</span><span class="sxs-lookup"><span data-stu-id="e8223-251">This requires more CPU bandwidth but also produces a nicer appearance.</span></span> <span data-ttu-id="e8223-252">パフォーマンスの低い CPU ターゲットの場合は、このスタイル フラグをクリアすると描画速度が速くなります。</span><span class="sxs-lookup"><span data-stu-id="e8223-252">For lower performance CPU targets, clearing this style flag will result in faster drawing speed.</span></span>

<span data-ttu-id="e8223-253">**GX_STYLE_RADIAL_PROGRESS_ROUND**</span><span class="sxs-lookup"><span data-stu-id="e8223-253">**GX_STYLE_RADIAL_PROGRESS_ROUND**</span></span>
  - <span data-ttu-id="e8223-254">値: 0x00000400</span><span class="sxs-lookup"><span data-stu-id="e8223-254">Value: 0x00000400</span></span>
  - <span data-ttu-id="e8223-255">説明: 放射状進行状況バーの円弧を描画するときに、線の先端が丸いブラシ スタイルを使用します。既定値では線の先端が四角くなります。</span><span class="sxs-lookup"><span data-stu-id="e8223-255">Description: Use a round line end brush style when drawing the radial progress bar arc. The default is a square line end.</span></span>

<span data-ttu-id="e8223-256">__"***追加のテキスト入力スタイル:***"__</span><span class="sxs-lookup"><span data-stu-id="e8223-256">__***Additional Text Input Styles:***__</span></span>

<span data-ttu-id="e8223-257">**GX_STYLE_ CURSOR_BLINK**</span><span class="sxs-lookup"><span data-stu-id="e8223-257">**GX_STYLE_ CURSOR_BLINK**</span></span>
  - <span data-ttu-id="e8223-258">値: 0x00000040</span><span class="sxs-lookup"><span data-stu-id="e8223-258">Value: 0x00000040</span></span>
  - <span data-ttu-id="e8223-259">説明: テキスト入力ウィジェットのカーソルは、固定されるのではなく点滅します。</span><span class="sxs-lookup"><span data-stu-id="e8223-259">Description: The text input widget cursor will flash on and off rather than being steady.</span></span>

<span data-ttu-id="e8223-260">**GX_STYLE_ CURSOR_ALWAYS**</span><span class="sxs-lookup"><span data-stu-id="e8223-260">**GX_STYLE_ CURSOR_ALWAYS**</span></span>
  - <span data-ttu-id="e8223-261">値: 0x00000080</span><span class="sxs-lookup"><span data-stu-id="e8223-261">Value: 0x00000080</span></span>
  - <span data-ttu-id="e8223-262">説明</span><span class="sxs-lookup"><span data-stu-id="e8223-262">Description.</span></span> <span data-ttu-id="e8223-263">通常、テキスト入力ウィジェットのカーソルは、そのウィジェットに入力フォーカスがある場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-263">The text input widget cursor is normally only displayed when the widget owns input focus.</span></span> <span data-ttu-id="e8223-264">このスタイル フラグを使用すると、入力フォーカスに関係なく、カーソルが常に表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="e8223-264">This style flag will make the cursor always visible regardless of input focus.</span></span>

<span data-ttu-id="e8223-265">**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**</span><span class="sxs-lookup"><span data-stu-id="e8223-265">**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**</span></span>
  - <span data-ttu-id="e8223-266">値: 0x00000100</span><span class="sxs-lookup"><span data-stu-id="e8223-266">Value: 0x00000100</span></span>
  - <span data-ttu-id="e8223-267">説明: このスタイル フラグを使用すると、テキスト入力ウィジェットがキーを押すイベントを受信するたびに、GX_EVENT_TEXT_EDITED イベントが設定されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-267">Description: With this style flag set the GX_EVENT_TEXT_EDITED event every time key down event is received by the text input widget.</span></span>

<span data-ttu-id="e8223-268">__"***追加のウィンドウ スタイル:***"__</span><span class="sxs-lookup"><span data-stu-id="e8223-268">__***Additional Window Styles:***__</span></span>

<span data-ttu-id="e8223-269">**GX_STYLE_TILE_WALLPAPER**</span><span class="sxs-lookup"><span data-stu-id="e8223-269">**GX_STYLE_TILE_WALLPAPER**</span></span>
  - <span data-ttu-id="e8223-270">値: 0x00040000</span><span class="sxs-lookup"><span data-stu-id="e8223-270">Value: 0x00040000</span></span>
  - <span data-ttu-id="e8223-271">説明: ウィンドウでは、割り当てられた壁紙画像を、ウィンドウ クライアントの四角形全体に並べて表示します。</span><span class="sxs-lookup"><span data-stu-id="e8223-271">Description: The window will tile any assigned wallpaper image to fill the window client rectangle.</span></span>

<span data-ttu-id="e8223-272">**GX_STYLE_AUTO_HSCROLL**</span><span class="sxs-lookup"><span data-stu-id="e8223-272">**GX_STYLE_AUTO_HSCROLL**</span></span>
  - <span data-ttu-id="e8223-273">値: 0x00100000</span><span class="sxs-lookup"><span data-stu-id="e8223-273">Value: 0x00100000</span></span>
  - <span data-ttu-id="e8223-274">説明: 今後の使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="e8223-274">Description: Reserved for future use.</span></span>

<span data-ttu-id="e8223-275">**GX_STYLE_AUTO_VSCROLL**</span><span class="sxs-lookup"><span data-stu-id="e8223-275">**GX_STYLE_AUTO_VSCROLL**</span></span>
  - <span data-ttu-id="e8223-276">値: 0x00200000</span><span class="sxs-lookup"><span data-stu-id="e8223-276">Value: 0x00200000</span></span>
  - <span data-ttu-id="e8223-277">説明: 今後の使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="e8223-277">Description: Reserved for future use.</span></span>

<span data-ttu-id="e8223-278">__"***追加のメニュー スタイル:***"__</span><span class="sxs-lookup"><span data-stu-id="e8223-278">__***Additional Menu Styles:***__</span></span>

<span data-ttu-id="e8223-279">**GX_STYLE_MENU_EXPANDED**</span><span class="sxs-lookup"><span data-stu-id="e8223-279">**GX_STYLE_MENU_EXPANDED**</span></span>
  - <span data-ttu-id="e8223-280">値: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="e8223-280">Value: 0x00000010</span></span>
  - <span data-ttu-id="e8223-281">説明: アコーディオン メニュー ウィジェットが、最初に展開された状態になります。</span><span class="sxs-lookup"><span data-stu-id="e8223-281">Description: Accordion menu widget is initially in expanded state.</span></span>

<span data-ttu-id="e8223-282">__"***追加のツリー ビュー スタイル:***"__</span><span class="sxs-lookup"><span data-stu-id="e8223-282">__***Additional Tree View Styles:***__</span></span>

<span data-ttu-id="e8223-283">**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**</span><span class="sxs-lookup"><span data-stu-id="e8223-283">**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**</span></span>
  - <span data-ttu-id="e8223-284">値: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="e8223-284">Value: 0x00000010</span></span>
  - <span data-ttu-id="e8223-285">説明: ツリー ビュー ウィジェットでは、ノード アイコンからルート ツリーノードに線が描画されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-285">Description: Tree view widget should draw lines from node icon to root tree node.</span></span>

<span data-ttu-id="e8223-286">__"***追加のスクロール バー スタイル:***"__</span><span class="sxs-lookup"><span data-stu-id="e8223-286">__***Additional Scrollbar Styles:***__</span></span>

<span data-ttu-id="e8223-287">**GX_SCROLLBAR_BACKGROUND_TILE**</span><span class="sxs-lookup"><span data-stu-id="e8223-287">**GX_SCROLLBAR_BACKGROUND_TILE**</span></span>
  - <span data-ttu-id="e8223-288">値: 0x00010000</span><span class="sxs-lookup"><span data-stu-id="e8223-288">Value: 0x00010000</span></span>
  - <span data-ttu-id="e8223-289">説明: 今後の使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="e8223-289">Description: Reserved for future use.</span></span>

<span data-ttu-id="e8223-290">**GX_SCROLLBAR_RELATIVE_THUMB**</span><span class="sxs-lookup"><span data-stu-id="e8223-290">**GX_SCROLLBAR_RELATIVE_THUMB**</span></span>
  - <span data-ttu-id="e8223-291">値: 0x00020000</span><span class="sxs-lookup"><span data-stu-id="e8223-291">Value: 0x00020000</span></span>
  - <span data-ttu-id="e8223-292">説明: スクロール バーのつまみの幅 (水平スクロール バーの場合) または高さ (垂直スクロール バーの場合) は、スクロール バーの最小および最大範囲に対する親ウィンドウの可視領域の割合に基づいて計算されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-292">Description: The scrollbar thumb width (for a horizontal scroll bar) or height (for a vertical scroll bar) are calculated based on the ratio of the visible area of the parent window to the min and max scrollbar range.</span></span>

<span data-ttu-id="e8223-293">**GX_SCROLLBAR_END_BUTTONS**</span><span class="sxs-lookup"><span data-stu-id="e8223-293">**GX_SCROLLBAR_END_BUTTONS**</span></span>
  - <span data-ttu-id="e8223-294">値: 0x00040000</span><span class="sxs-lookup"><span data-stu-id="e8223-294">Value: 0x00040000</span></span>
  - <span data-ttu-id="e8223-295">説明: スクロール バーでは、スクロール バー領域の各端に、ボタンが自動的に作成されて追加されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-295">Description: The scrollbar automatically creates and attaches buttons at each end of the scrollbar region.</span></span>

<span data-ttu-id="e8223-296">**GX_SCROLLBAR_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="e8223-296">**GX_SCROLLBAR_VERTICAL**</span></span> 
  - <span data-ttu-id="e8223-297">値: 0x01000000</span><span class="sxs-lookup"><span data-stu-id="e8223-297">Value: 0x01000000</span></span>
  - <span data-ttu-id="e8223-298">説明: スクロール バーは垂直方向になります。</span><span class="sxs-lookup"><span data-stu-id="e8223-298">Description: The scrollbar is vertically oriented.</span></span>

<span data-ttu-id="e8223-299">**GX_SCROLLBAR_HORIZONTAL**</span><span class="sxs-lookup"><span data-stu-id="e8223-299">**GX_SCROLLBAR_HORIZONTAL**</span></span>
  - <span data-ttu-id="e8223-300">値: 0x02000000</span><span class="sxs-lookup"><span data-stu-id="e8223-300">Value: 0x02000000</span></span>
  - <span data-ttu-id="e8223-301">説明: スクロール バーは水平方向になります。</span><span class="sxs-lookup"><span data-stu-id="e8223-301">Description: The scrollbar is horizontally oriented.</span></span>

<span data-ttu-id="e8223-302">__"***テキストのスクロール ホイール スタイル:***"__</span><span class="sxs-lookup"><span data-stu-id="e8223-302">__***Text Scroll Wheel Styles:***__</span></span>

<span data-ttu-id="e8223-303">**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**</span><span class="sxs-lookup"><span data-stu-id="e8223-303">**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**</span></span>
  - <span data-ttu-id="e8223-304">値: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="e8223-304">Value: 0x00000200</span></span>
  - <span data-ttu-id="e8223-305">説明: スクロール ホイールでは、正弦波アルゴリズムを使用して、スクロール ホイールが丸みのある形で表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="e8223-305">Description: The scroll wheel uses a Sinusoidal algorithm to make the scroll wheel appear to have a rounded shape.</span></span> <span data-ttu-id="e8223-306">このスタイル フラグを使用すると、スクロール ホイール ウィジェットのパフォーマンスに大きなオーバーヘッドが生じる可能性がありますが、ホイールの外観を 3D のリアルなものにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="e8223-306">This style flag can add significant overhead to the performance of the scroll wheel widget, but can also give the wheel a 3D realistic appearance.</span></span>