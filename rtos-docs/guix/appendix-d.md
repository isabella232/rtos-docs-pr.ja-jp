---
title: 別表 D - GUIX のブラシ、キャンバス、グラデーションの属性
description: GUIX のブラシ、キャンバス、グラデーションの属性について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 19c0687a54be244ae395124664b4b6da0f4e90b6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812092"
---
# <a name="appendix-d---guix-brush-canvas-and-gradient-attributes"></a><span data-ttu-id="38204-103">別表 D - GUIX のブラシ、キャンバス、グラデーションの属性</span><span class="sxs-lookup"><span data-stu-id="38204-103">Appendix D - GUIX Brush, Canvas and Gradient Attributes</span></span>

<span data-ttu-id="38204-104">__**ブラシ スタイル:**__</span><span class="sxs-lookup"><span data-stu-id="38204-104">__**Brush Styles:**__</span></span>

<span data-ttu-id="38204-105">**GX_BRUSH_OUTLINE**</span><span class="sxs-lookup"><span data-stu-id="38204-105">**GX_BRUSH_OUTLINE**</span></span>
- <span data-ttu-id="38204-106">値: 0x0000</span><span class="sxs-lookup"><span data-stu-id="38204-106">Value: 0x0000</span></span>
- <span data-ttu-id="38204-107">説明: このブラシ スタイルは、gx_canvas_rectangle_draw や gx_canvas_polygon_draw などの図形描画の関数に適用されます。</span><span class="sxs-lookup"><span data-stu-id="38204-107">Description: This brush style applies to shape drawing functions such as gx_canvas_rectangle_draw or gx_canvas_polygon_draw.</span></span> <span data-ttu-id="38204-108">このスタイルでは図形の輪郭が描画され、必要ならば塗りつぶすこともできます。</span><span class="sxs-lookup"><span data-stu-id="38204-108">This style indicateds the shape should be outlined, in addition to optionally being fill.</span></span> <span data-ttu-id="38204-109">GX_BRUSH_OUTLINE スタイルを設定して GX_BRSUH_SOLID_FILL を設定しない場合、図形の輪郭だけが描画されます。</span><span class="sxs-lookup"><span data-stu-id="38204-109">If the GX_BRUSH_OUTLINE style is set and the GX_BRSUH_SOLID_FILL is cleared, the shape is only outlined.</span></span>

<span data-ttu-id="38204-110">**GX_BRUSH_SOLID_FILL**</span><span class="sxs-lookup"><span data-stu-id="38204-110">**GX_BRUSH_SOLID_FILL**</span></span>
- <span data-ttu-id="38204-111">値: 0x0001</span><span class="sxs-lookup"><span data-stu-id="38204-111">Value: 0x0001</span></span>
- <span data-ttu-id="38204-112">説明: このブラシ スタイルは図形描画の関数に適用され、現在のブラシ塗りつぶしの色で、要求された図形を塗りつぶすことを示します。</span><span class="sxs-lookup"><span data-stu-id="38204-112">Description: This brush style applies to shape drawing functions, and indicates that the requested shape should be filled with a solid color using the current brush fill color.</span></span>

<span data-ttu-id="38204-113">**GX_BRUSH_PIXELMAP_FILL**</span><span class="sxs-lookup"><span data-stu-id="38204-113">**GX_BRUSH_PIXELMAP_FILL**</span></span>
- <span data-ttu-id="38204-114">値: 0x0002</span><span class="sxs-lookup"><span data-stu-id="38204-114">Value: 0x0002</span></span>
- <span data-ttu-id="38204-115">説明: このブラシ スタイルは図形描画の関数に適用され、現在のブラシ pixelmap (ピクセルマップ) のパターンで、要求された図形を塗りつぶすことを示します。</span><span class="sxs-lookup"><span data-stu-id="38204-115">Description: This brush style applies to shape drawing functions, and indicates that the requested shape should be pattern filled with the current brush pixelmap.</span></span>

<span data-ttu-id="38204-116">**GX_BRUSH_ALIAS**</span><span class="sxs-lookup"><span data-stu-id="38204-116">**GX_BRUSH_ALIAS**</span></span>
- <span data-ttu-id="38204-117">値: 0x0004</span><span class="sxs-lookup"><span data-stu-id="38204-117">Value: 0x0004</span></span>
- <span data-ttu-id="38204-118">説明: このブラシ スタイルは、すべての線描と図形の輪郭に適用されます。</span><span class="sxs-lookup"><span data-stu-id="38204-118">Description: This brush style applies to all line drawing and shape outlines.</span></span> <span data-ttu-id="38204-119">このフラグを設定するとアンチエイリアス描画アルゴリズムが適用され、描画が正確になる代わりにかかる時間が長くなります。</span><span class="sxs-lookup"><span data-stu-id="38204-119">If this flag is set, lines and outlines are drawing with the more accurate but also more time consuming anti-aliased drawing algorithms.</span></span> <span data-ttu-id="38204-120">このスタイル フラグは 16 bpp 以上の色深度でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="38204-120">This style flag is only used for 16-bpp color depths and higher.</span></span>

<span data-ttu-id="38204-121">**GX_BRUSH_UNDERLINE**</span><span class="sxs-lookup"><span data-stu-id="38204-121">**GX_BRUSH_UNDERLINE**</span></span>
- <span data-ttu-id="38204-122">値: 0x0008</span><span class="sxs-lookup"><span data-stu-id="38204-122">Value: 0x0008</span></span>
- <span data-ttu-id="38204-123">説明: このフラグはテキストの描画に適用され、フラグ設定後に描画するテキストに下線を付けることを示します。</span><span class="sxs-lookup"><span data-stu-id="38204-123">Description: This flag applies to text drawing, and indicates that subsequent text drawn should be underlined.</span></span>

<span data-ttu-id="38204-124">**GX_BRUSH_ROUND**</span><span class="sxs-lookup"><span data-stu-id="38204-124">**GX_BRUSH_ROUND**</span></span>
- <span data-ttu-id="38204-125">値: 0x0010</span><span class="sxs-lookup"><span data-stu-id="38204-125">Value: 0x0010</span></span>
- <span data-ttu-id="38204-126">説明: このフラグは線描に適用され、線の端が既定の角ばった形状ではなく円い形状を示します。</span><span class="sxs-lookup"><span data-stu-id="38204-126">Description: This flag applies to line drawing, and indicates that line ends are drawn with a round or circular shape, rather than the default square shape.</span></span>

<span data-ttu-id="38204-127">__**キャンバスのフラグ:**__</span><span class="sxs-lookup"><span data-stu-id="38204-127">__**Canvas Flags:**__</span></span>

<span data-ttu-id="38204-128">**GX_CANVAS_SIMPLE**</span><span class="sxs-lookup"><span data-stu-id="38204-128">**GX_CANVAS_SIMPLE**</span></span>
- <span data-ttu-id="38204-129">値: 0x01</span><span class="sxs-lookup"><span data-stu-id="38204-129">Value: 0x01</span></span>
- <span data-ttu-id="38204-130">説明: 画面に表示されない描画に使用されるメモリ キャンバスです。</span><span class="sxs-lookup"><span data-stu-id="38204-130">Description: A memory canvas which is used to off-screen drawing.</span></span>

<span data-ttu-id="38204-131">**GX_CANVAS_MANAGED**</span><span class="sxs-lookup"><span data-stu-id="38204-131">**GX_CANVAS_MANAGED**</span></span>
- <span data-ttu-id="38204-132">値: 0x02</span><span class="sxs-lookup"><span data-stu-id="38204-132">Value: 0x02</span></span>
- <span data-ttu-id="38204-133">説明: 合成作成プロセスの一環として、または単一キャンバス アーキテクチャのバッファー切り替え操作の一環として、アクティブな画面に自動的にフラッシュされるキャンバス。</span><span class="sxs-lookup"><span data-stu-id="38204-133">Description: A canvas which automatically flushed to the active display, either as part of the composite building process or as part of the buffer toggle operation for single-canvas architectures.</span></span>

<span data-ttu-id="38204-134">**GX_CANVAS_VISIBLE**</span><span class="sxs-lookup"><span data-stu-id="38204-134">**GX_CANVAS_VISIBLE**</span></span>
- <span data-ttu-id="38204-135">値: 0x04</span><span class="sxs-lookup"><span data-stu-id="38204-135">Value: 0x04</span></span>
- <span data-ttu-id="38204-136">説明: このフラグを使用すれば、キャンバスの描画内容を失わずにキャンバスをオンまたはオフできます。</span><span class="sxs-lookup"><span data-stu-id="38204-136">Description: This flag can be used to turn on and off a canvas, without losing the canvas drawing contents.</span></span>

<span data-ttu-id="38204-137">**GX_CANVAS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="38204-137">**GX_CANVAS_MODIFIED**</span></span>
- <span data-ttu-id="38204-138">値: 0x08</span><span class="sxs-lookup"><span data-stu-id="38204-138">Value: 0x08</span></span>
- <span data-ttu-id="38204-139">説明: 将来使用するために確保されています。</span><span class="sxs-lookup"><span data-stu-id="38204-139">Description: Reserved for future use.</span></span>

<span data-ttu-id="38204-140">**GX_CANVAS_COMPOSITE**</span><span class="sxs-lookup"><span data-stu-id="38204-140">**GX_CANVAS_COMPOSITE**</span></span>
- <span data-ttu-id="38204-141">値: 0x20</span><span class="sxs-lookup"><span data-stu-id="38204-141">Value: 0x20</span></span>
- <span data-ttu-id="38204-142">説明: アプリケーションはこのフラグを使用して、管理している複数のキャンバスを合成キャンバス上に合成する複数キャンバス システムを構成し、合成したものをハードウェアのフレーム バッファーに送ります。</span><span class="sxs-lookup"><span data-stu-id="38204-142">Description: This flag is used by the application when configuring a multiple-canvas system which will composite multiple managed canvases into the composite canvas, and the composite is the driven to the hardware frame buffer.</span></span>

<span data-ttu-id="38204-143">__**グラデーションの種類:**__</span><span class="sxs-lookup"><span data-stu-id="38204-143">__**Gradient Types:**__</span></span>

<span data-ttu-id="38204-144">**GX_GRADIENT_TYPE_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="38204-144">**GX_GRADIENT_TYPE_VERTICAL**</span></span>
- <span data-ttu-id="38204-145">値: 0x01</span><span class="sxs-lookup"><span data-stu-id="38204-145">Value: 0x01</span></span>
- <span data-ttu-id="38204-146">説明: アルファマップの垂直方向のグラデーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="38204-146">Description: Creates a vertical alphamap gradient.</span></span>

<span data-ttu-id="38204-147">**GX_GRADIENT_TYPE_ALPHA**</span><span class="sxs-lookup"><span data-stu-id="38204-147">**GX_GRADIENT_TYPE_ALPHA**</span></span>
- <span data-ttu-id="38204-148">値: 0x02</span><span class="sxs-lookup"><span data-stu-id="38204-148">Value: 0x02</span></span>
- <span data-ttu-id="38204-149">説明: アルファマップ スタイルのグラデーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="38204-149">Description: Creats an alpha-map style gradient.</span></span> <span data-ttu-id="38204-150">これは、現在サポートされている唯一のグラデーション スタイルです。</span><span class="sxs-lookup"><span data-stu-id="38204-150">This is currently the only gradient style supported.</span></span>

<span data-ttu-id="38204-151">**GX_GRADIENT_TYPE_MIRROR**</span><span class="sxs-lookup"><span data-stu-id="38204-151">**GX_GRADIENT_TYPE_MIRROR**</span></span>
- <span data-ttu-id="38204-152">値: 0x04</span><span class="sxs-lookup"><span data-stu-id="38204-152">Value: 0x04</span></span>
- <span data-ttu-id="38204-153">説明: このフラグは、幅や高さの範囲の中央でグラデーションが最大になり、右端や下端に達すると最初の値に戻ることを示します。</span><span class="sxs-lookup"><span data-stu-id="38204-153">Description: This flag indicates that the gradient should peak at the center of the width/height range, and return to the starting value as it reaches the right/bottom edge.</span></span> <span data-ttu-id="38204-154">このスタイル フラグを設定しない場合、GX_GRADIENT_TYPE_VERTICAL フラグに応じて、グラデーションは上から下、または左から右の線形グラデーションになります。</span><span class="sxs-lookup"><span data-stu-id="38204-154">Without this style flag, the gradient will be a linear gradient from top-to-bottom or left-to-right, depending on the GX_GRADIENT_TYPE_VERTICAL flag.</span></span>