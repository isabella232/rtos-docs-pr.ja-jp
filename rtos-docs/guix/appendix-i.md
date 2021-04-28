---
title: 別表 I - GUIX 情報構造体
description: GUIX 情報構造体について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dc7775cdde8f1aa89ca650561713f54ac6c069eb
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550220"
---
# <a name="appendix-i---guix-information-structures"></a><span data-ttu-id="b88a6-103">別表 I - GUIX 情報構造体</span><span class="sxs-lookup"><span data-stu-id="b88a6-103">Appendix I - GUIX Information Structures</span></span> 

## <a name="gx_bidi_text_info"></a><span data-ttu-id="b88a6-104">GX_BIDI_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="b88a6-104">GX_BIDI_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b88a6-105">定義</span><span class="sxs-lookup"><span data-stu-id="b88a6-105">Definition</span></span>

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```
| <span data-ttu-id="b88a6-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b88a6-106">Members</span></span> | <span data-ttu-id="b88a6-107">説明</span><span class="sxs-lookup"><span data-stu-id="b88a6-107">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b88a6-108">**gx_bidi_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="b88a6-108">**gx_bidi_text_info_text**</span></span>               | <span data-ttu-id="b88a6-109">並べ替えを行うテキスト</span><span class="sxs-lookup"><span data-stu-id="b88a6-109">Text for reordering</span></span> |
| <span data-ttu-id="b88a6-110">**gx_bidi_text_info_font**</span><span class="sxs-lookup"><span data-stu-id="b88a6-110">**gx_bidi_text_info_font**</span></span>               | <span data-ttu-id="b88a6-111">テキストの表示に使用するフォント。改行が必要ない場合は GX_NULL に設定します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-111">Font used to display text, set it to GX_NULL if line breaking is not needed</span></span> |
| <span data-ttu-id="b88a6-112">**gx_bidi_text_info_display_width**</span><span class="sxs-lookup"><span data-stu-id="b88a6-112">**gx_bidi_text_info_display_width**</span></span>      | <span data-ttu-id="b88a6-113">表示に使用できる幅。改行が必要ない場合は -1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-113">Available width for displaying, set it to -1 if line breaking is not needed</span></span> |

## <a name="gx_bidi_resolved_text_info"></a><span data-ttu-id="b88a6-114">GX_BIDI_RESOLVED_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="b88a6-114">GX_BIDI_RESOLVED_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b88a6-115">定義</span><span class="sxs-lookup"><span data-stu-id="b88a6-115">Definition</span></span>

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

| <span data-ttu-id="b88a6-116">メンバー</span><span class="sxs-lookup"><span data-stu-id="b88a6-116">Members</span></span> | <span data-ttu-id="b88a6-117">説明</span><span class="sxs-lookup"><span data-stu-id="b88a6-117">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b88a6-118">**gx_bidi_resolved_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="b88a6-118">**gx_bidi_resolved_text_info_text**</span></span>             | <span data-ttu-id="b88a6-119">並べ替えた bidi テキストの配列へのポインター</span><span class="sxs-lookup"><span data-stu-id="b88a6-119">Pointer to the array of reordered bidi text</span></span> |
| <span data-ttu-id="b88a6-120">**gx_bidi_resolved_text_info_total_lines**</span><span class="sxs-lookup"><span data-stu-id="b88a6-120">**gx_bidi_resolved_text_info_total_lines**</span></span>      | <span data-ttu-id="b88a6-121">処理済み bidi テキストの 1 段落の合計行数</span><span class="sxs-lookup"><span data-stu-id="b88a6-121">Total lines of resolved bidi text for one paragraph</span></span> |
| <span data-ttu-id="b88a6-122">**gx_bidi_resolved_text_info_next**</span><span class="sxs-lookup"><span data-stu-id="b88a6-122">**gx_bidi_resolved_text_info_next**</span></span>             | <span data-ttu-id="b88a6-123">次の段落の処理済み bidi テキストの情報</span><span class="sxs-lookup"><span data-stu-id="b88a6-123">Resolved bidi text information for the next paragraph</span></span> |

## <a name="gx_circular_gauge_info"></a><span data-ttu-id="b88a6-124">GX_CIRCULAR_GAUGE_INFO</span><span class="sxs-lookup"><span data-stu-id="b88a6-124">GX_CIRCULAR_GAUGE_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="b88a6-125">定義</span><span class="sxs-lookup"><span data-stu-id="b88a6-125">Definition</span></span>

```c
typedef struct GX_CIRCULAR_GAUGE_INFO_STRUCT
{
    INT             gx_circular_gauge_info_animation_steps;
    INT             gx_circular_gauge_info_animation_delay;
    GX_VALUE        gx_circular_gauge_info_needle_xpos;
    GX_VALUE        gx_circular_gauge_info_needle_ypos;
    GX_VALUE        gx_circular_gauge_info_needle_xcor;
    GX_VALUE        gx_circular_gauge_info_needle_ycor;
    GX_RESOURCE_ID  gx_circular_gauge_info_needle_pixelmap;
} GX_CIRCULAR_GAUGE_INFO;
```

| <span data-ttu-id="b88a6-126">メンバー</span><span class="sxs-lookup"><span data-stu-id="b88a6-126">Members</span></span> | <span data-ttu-id="b88a6-127">説明</span><span class="sxs-lookup"><span data-stu-id="b88a6-127">Description</span></span> |
| ------------------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="b88a6-128">**gx_circular_gauge_info_animation_steps**</span><span class="sxs-lookup"><span data-stu-id="b88a6-128">**gx_circular_gauge_info_animation_steps**</span></span>       | <span data-ttu-id="b88a6-129">現在の角度から新たに割り当てられる角度まで針が回るときに経る合計ステップ数</span><span class="sxs-lookup"><span data-stu-id="b88a6-129">Total steps the needle will travel through when moving from the current needle angle to a newly assigned needle angle</span></span> |
| <span data-ttu-id="b88a6-130">**gx_circular_gauge_info_animation_delay**</span><span class="sxs-lookup"><span data-stu-id="b88a6-130">**gx_circular_gauge_info_animation_delay**</span></span>       | <span data-ttu-id="b88a6-131">アニメーションのステップ間で GUIX の時計の針が動く回数</span><span class="sxs-lookup"><span data-stu-id="b88a6-131">The number of GUIX clock ticks to delay between animation steps</span></span> |
| <span data-ttu-id="b88a6-132">**gx_circular_gauge_info_needle_xpos**</span><span class="sxs-lookup"><span data-stu-id="b88a6-132">**gx_circular_gauge_info_needle_xpos**</span></span>           | <span data-ttu-id="b88a6-133">ゲージ ウィジェットの左端からゲージの針の回転中心までの距離</span><span class="sxs-lookup"><span data-stu-id="b88a6-133">The distance from the left of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="b88a6-134">**gx_circular_gauge_info_needle_ypos**</span><span class="sxs-lookup"><span data-stu-id="b88a6-134">**gx_circular_gauge_info_needle_ypos**</span></span>           | <span data-ttu-id="b88a6-135">ゲージ ウィジェットの上端からゲージの針の回転中心までの距離</span><span class="sxs-lookup"><span data-stu-id="b88a6-135">The distance from the top of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="b88a6-136">**gx_circular_gauge_info_needle_xcor**</span><span class="sxs-lookup"><span data-stu-id="b88a6-136">**gx_circular_gauge_info_needle_xcor**</span></span>           | <span data-ttu-id="b88a6-137">針の画像の左端からゲージの針の回転中心までの距離</span><span class="sxs-lookup"><span data-stu-id="b88a6-137">The distance from the left of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="b88a6-138">**gx_circular_gauge_info_needle_ycor**</span><span class="sxs-lookup"><span data-stu-id="b88a6-138">**gx_circular_gauge_info_needle_ycor**</span></span>           | <span data-ttu-id="b88a6-139">針の画像の上端からゲージの針の回転中心までの距離</span><span class="sxs-lookup"><span data-stu-id="b88a6-139">The distance from the top of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="b88a6-140">**gx_circular_gauge_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b88a6-140">**gx_circular_gauge_info_needle_pixelmap**</span></span>       | <span data-ttu-id="b88a6-141">ゲージの針の描画に使用するピクセルマップのリソース ID。</span><span class="sxs-lookup"><span data-stu-id="b88a6-141">Resource ID of the pixelmap which will be used to draw the gauge needle.</span></span> <span data-ttu-id="b88a6-142">この画像は、ゲージ ウィジェットで必要なときに回転し、ゲージの針を必要な位置に表示します</span><span class="sxs-lookup"><span data-stu-id="b88a6-142">This image will be rotated as needed by the gauge widget to display the gauge needle in any position</span></span> |

<span data-ttu-id="b88a6-143">次の図に xpos、ypos、xcor、ycor の座標を示します:</span><span class="sxs-lookup"><span data-stu-id="b88a6-143">The diagram below illustrates the xpos, ypos, and xcor, ycor coordinates:</span></span>

![針の Y 座標と X 座標の図](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a><span data-ttu-id="b88a6-145">GX_LINE_CHART_INFO</span><span class="sxs-lookup"><span data-stu-id="b88a6-145">GX_LINE_CHART_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="b88a6-146">定義</span><span class="sxs-lookup"><span data-stu-id="b88a6-146">Definition</span></span>

```c
typedef struct GX_LINE_CHART_INFO_STRUCT
{
    INT            gx_line_chart_min_val;
    INT            gx_line_chart_max_val;
    INT           *gx_line_chart_data;
    GX_VALUE       gx_line_left_margin;
    GX_VALUE       gx_line_top_margin;
    GX_VALUE       gx_line_right_margin;
    GX_VALUE       gx_line_bottom_margin;
    GX_VALUE       gx_line_chart_max_data_count;
    GX_VALUE       gx_line_chart_active_data_count;
    GX_VALUE       gx_line_chart_axis_line_width;
    GX_VALUE       gx_line_chart_data_line_width;
    GX_RESOURCE_ID gx_line_chart_axis_color;
    GX_RESOURCE_ID gx_line_chart_line_color;
} GX_LINE_CHART_INFO;
```

| <span data-ttu-id="b88a6-147">メンバー</span><span class="sxs-lookup"><span data-stu-id="b88a6-147">Members</span></span> | <span data-ttu-id="b88a6-148">説明</span><span class="sxs-lookup"><span data-stu-id="b88a6-148">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b88a6-149">**gx_line_chart_min_val**</span><span class="sxs-lookup"><span data-stu-id="b88a6-149">**gx_line_chart_min_val**</span></span>          | <span data-ttu-id="b88a6-150">データの最小値。拡大率の計算に使用します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-150">The minimum data value, which is used to calculate scaling</span></span>
| <span data-ttu-id="b88a6-151">**gx_line_chart_max_val**</span><span class="sxs-lookup"><span data-stu-id="b88a6-151">**gx_line_chart_max_val**</span></span>          | <span data-ttu-id="b88a6-152">拡大率の計算に使用されるデータの最大値。</span><span class="sxs-lookup"><span data-stu-id="b88a6-152">The maximum data value, which is used to calculate scaling</span></span> |
| <span data-ttu-id="b88a6-153">**gx_line_chart_data**</span><span class="sxs-lookup"><span data-stu-id="b88a6-153">**gx_line_chart_data**</span></span>             | <span data-ttu-id="b88a6-154">整数値の配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b88a6-154">Pointer to an array of integer values.</span></span> <span data-ttu-id="b88a6-155">これは、整数値を折れ線グラフ ウィジェットでプロットしたものです</span><span class="sxs-lookup"><span data-stu-id="b88a6-155">These are the integer values plotted by the line chart widget</span></span> |
| <span data-ttu-id="b88a6-156">**gx_line_<side>_margin**</span><span class="sxs-lookup"><span data-stu-id="b88a6-156">**gx_line_<side>_margin**</span></span>          | <span data-ttu-id="b88a6-157">グラフ ウィンドウの外側の境界と実際にグラフを描画する領域の間のオフセット。</span><span class="sxs-lookup"><span data-stu-id="b88a6-157">The offset from the chart window outer bound to the actual chart rendering area.</span></span> <span data-ttu-id="b88a6-158">グラフの軸とデータの線は、常にこの内側の境界の内部にプロットされます。この仕組みによりアプリケーションでは、グラフ ウィンドウの内側でグラフ描画領域の外側に当たる場所に、ラベルなどの情報を描画できます。</span><span class="sxs-lookup"><span data-stu-id="b88a6-158">The chart axis and data line are always plotted within this inner boundary, which allows the application to draw labels and other information inside the chart window but outside the char graphing area</span></span> |
| <span data-ttu-id="b88a6-159">**gx_line_chart_max_data_count**</span><span class="sxs-lookup"><span data-stu-id="b88a6-159">**gx_line_chart_max_data_count**</span></span>   | <span data-ttu-id="b88a6-160">表示し得るデータ値の数。</span><span class="sxs-lookup"><span data-stu-id="b88a6-160">The number of data values which may be present.</span></span> <span data-ttu-id="b88a6-161">このパラメーターは、データ値をプロットする際の x 軸拡大率または間隔を計算するのに使用します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-161">This parameter is used for calculating the x-axis scaling or interval for plotting data points.</span></span> |
| <span data-ttu-id="b88a6-162">**gx_line_active_data_count**</span><span class="sxs-lookup"><span data-stu-id="b88a6-162">**gx_line_active_data_count**</span></span>      | <span data-ttu-id="b88a6-163">データの配列の中に実際に存在するデータ値の数。</span><span class="sxs-lookup"><span data-stu-id="b88a6-163">The number of data values that actually present in the data array.</span></span> <span data-ttu-id="b88a6-164">折れ線グラフは、(たとえば) 最大 100 個の値を描画するように拡大縮小できますが、グラフを更新する際、表示されるデータ値の数がそれよりも少なくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b88a6-164">A line chart may be scaled to draw a maximum of 100 values (for example), but on any particular update a smaller number of data values may actually be present.</span></span> |
| <span data-ttu-id="b88a6-165">**gx_line_axis_line_width**</span><span class="sxs-lookup"><span data-stu-id="b88a6-165">**gx_line_axis_line_width**</span></span>        | <span data-ttu-id="b88a6-166">水平軸と垂直軸の描画に使用する線の幅</span><span class="sxs-lookup"><span data-stu-id="b88a6-166">Width of the line used to draw the horizontal and vertical axis</span></span> |
| <span data-ttu-id="b88a6-167">**gx_line_data_line_width**</span><span class="sxs-lookup"><span data-stu-id="b88a6-167">**gx_line_data_line_width**</span></span>        | <span data-ttu-id="b88a6-168">プロットされたデータの線の幅</span><span class="sxs-lookup"><span data-stu-id="b88a6-168">Width of the plotted data line</span></span> |
| <span data-ttu-id="b88a6-169">**gx_line_chart_axis_color**</span><span class="sxs-lookup"><span data-stu-id="b88a6-169">**gx_line_chart_axis_color**</span></span>       | <span data-ttu-id="b88a6-170">軸の線の描画に使用する色のリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-170">Resource ID of the color used to draw the axis lines</span></span> |
| <span data-ttu-id="b88a6-171">**gx_line_chart_line_color**</span><span class="sxs-lookup"><span data-stu-id="b88a6-171">**gx_line_chart_line_color**</span></span>       | <span data-ttu-id="b88a6-172">グラフのデータ線の描画に使用する色のリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-172">Resource ID of the color used to draw the chart data line</span></span> |

## <a name="gx_mouse_cursor_info"></a><span data-ttu-id="b88a6-173">GX_MOUSE_CURSOR_INFO</span><span class="sxs-lookup"><span data-stu-id="b88a6-173">GX_MOUSE_CURSOR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b88a6-174">定義</span><span class="sxs-lookup"><span data-stu-id="b88a6-174">Definition</span></span>

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

| <span data-ttu-id="b88a6-175">メンバー</span><span class="sxs-lookup"><span data-stu-id="b88a6-175">Members</span></span> | <span data-ttu-id="b88a6-176">説明</span><span class="sxs-lookup"><span data-stu-id="b88a6-176">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b88a6-177">**gx_mouse_cursor_image_id**</span><span class="sxs-lookup"><span data-stu-id="b88a6-177">**gx_mouse_cursor_image_id**</span></span>       | <span data-ttu-id="b88a6-178">マウス画像のリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-178">Resource ID of the mouse image</span></span> |
| <span data-ttu-id="b88a6-179">**gx_mouse_cursor_hotspot_x**</span><span class="sxs-lookup"><span data-stu-id="b88a6-179">**gx_mouse_cursor_hotspot_x**</span></span>      | <span data-ttu-id="b88a6-180">マウス画像の左端とマウス画像のホット スポットの間のオフセット</span><span class="sxs-lookup"><span data-stu-id="b88a6-180">The offset from the left of the mouse image to the mouse image hotspot</span></span> |
| <span data-ttu-id="b88a6-181">**gx_mouse_cursor_hotspot_y**</span><span class="sxs-lookup"><span data-stu-id="b88a6-181">**gx_mouse_cursor_hotspot_y**</span></span>      | <span data-ttu-id="b88a6-182">マウス画像の上端とマウス画像のホット スポットの間のオフセット</span><span class="sxs-lookup"><span data-stu-id="b88a6-182">The offset from the top of the mouse image to the mouse image hotspot</span></span> |

## <a name="gx_pen_configuration"></a><span data-ttu-id="b88a6-183">GX_PEN_CONFIGURATION</span><span class="sxs-lookup"><span data-stu-id="b88a6-183">GX_PEN_CONFIGURATION</span></span> 

### <a name="definition"></a><span data-ttu-id="b88a6-184">定義</span><span class="sxs-lookup"><span data-stu-id="b88a6-184">Definition</span></span>

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

| <span data-ttu-id="b88a6-185">メンバー</span><span class="sxs-lookup"><span data-stu-id="b88a6-185">Members</span></span> | <span data-ttu-id="b88a6-186">説明</span><span class="sxs-lookup"><span data-stu-id="b88a6-186">Description</span></span> |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="b88a6-187">**gx_pen_configuration_min_drag_dist**</span><span class="sxs-lookup"><span data-stu-id="b88a6-187">**gx_pen_configuration_min_drag_dist**</span></span>       | <span data-ttu-id="b88a6-188">FLICK イベントを発生させる、GUIX タイマー刻みあたりの最小ドラッグ距離。</span><span class="sxs-lookup"><span data-stu-id="b88a6-188">The minimum drag distance per GUIX timer tick to trigger an FLICK event.</span></span> <span data-ttu-id="b88a6-189">GX_FIXED_VAL_MAKE を呼び出して固定点データの値を設定します</span><span class="sxs-lookup"><span data-stu-id="b88a6-189">Call GX_FIXED_VAL_MAKE to make a fixed point data type value</span></span> |
| <span data-ttu-id="b88a6-190">**gx_pen_configuration_max_pen_speed_ticks**</span><span class="sxs-lookup"><span data-stu-id="b88a6-190">**gx_pen_configuration_max_pen_speed_ticks**</span></span> | <span data-ttu-id="b88a6-191">FLICK イベントを発生させる、GUIX タイマー刻み単位の最大ドラッグ速度</span><span class="sxs-lookup"><span data-stu-id="b88a6-191">The maximum drag speed in GUIX timer ticks to trigger an FLICK event</span></span> | 

## <a name="gx_pixelmap_slider_info"></a><span data-ttu-id="b88a6-192">GX_PIXELMAP_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="b88a6-192">GX_PIXELMAP_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b88a6-193">定義</span><span class="sxs-lookup"><span data-stu-id="b88a6-193">Definition</span></span>

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

| <span data-ttu-id="b88a6-194">メンバー</span><span class="sxs-lookup"><span data-stu-id="b88a6-194">Members</span></span> | <span data-ttu-id="b88a6-195">説明</span><span class="sxs-lookup"><span data-stu-id="b88a6-195">Description</span></span> |
| ----------------------------------------------------- | ---------------------------------------- |
| <span data-ttu-id="b88a6-196">**gx_pixelmap_slider_info_lower_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b88a6-196">**gx_pixelmap_slider_info_lower_background_pixelmap**</span></span> | <span data-ttu-id="b88a6-197">針の手前側の背景を塗りつぶすピクセルマップのリソース ID。</span><span class="sxs-lookup"><span data-stu-id="b88a6-197">Resource ID of the pixelmap for filling the background before the needle.</span></span> <span data-ttu-id="b88a6-198">手前側の背景のピクセルマップを設定していない場合は、針の手前側と奥側両方の背景を塗りつぶすのに使用します</span><span class="sxs-lookup"><span data-stu-id="b88a6-198">If upper background pixelmap is not set, it’s used for filling background both before and after the needle</span></span> |
| <span data-ttu-id="b88a6-199">**gx_pixelmap_slider_info_upper_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b88a6-199">**gx_pixelmap_slider_info_upper_background_pixelmap**</span></span> | <span data-ttu-id="b88a6-200">針の奥側の背景を塗りつぶすピクセルマップのリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-200">Resource ID of the pixelmap for filling background after the needle</span></span> |
| <span data-ttu-id="b88a6-201">**gx_pixelmap_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b88a6-201">**gx_pixelmap_slider_info_needle_pixelmap**</span></span>           | <span data-ttu-id="b88a6-202">針のピクセルマップのリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-202">Resource ID of the needle pixelmap</span></span> |

## <a name="gx_progress_bar_info"></a><span data-ttu-id="b88a6-203">GX_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="b88a6-203">GX_PROGRESS_BAR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b88a6-204">**定義**</span><span class="sxs-lookup"><span data-stu-id="b88a6-204">**Definition**</span></span>

```c
typedef struct GX_PROGRESS_BAR_INFO_STRUCT
{
    INT gx_progress_bar_info_min_val;
    INT gx_progress_bar_info_max_val;
    INT gx_progress_bar_info_current_val;
    GX_RESOURCE_ID gx_progress_bar_font_id;
    GX_RESOURCE_ID gx_progress_bar_normal_text_color;
    GX_RESOURCE_ID gx_progress_bar_selected_text_color;
    GX_RESOURCE_ID gx_progress_bar_disabled_text_color;
    GX_RESOURCE_ID gx_progress_bar_fill_pixelmap;
} GX_PROGRESS_BAR_INFO;
```

| <span data-ttu-id="b88a6-205">メンバー</span><span class="sxs-lookup"><span data-stu-id="b88a6-205">Members</span></span> | <span data-ttu-id="b88a6-206">説明</span><span class="sxs-lookup"><span data-stu-id="b88a6-206">Description</span></span> |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="b88a6-207">**gx_progress_bar_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="b88a6-207">**gx_progress_bar_info_min_val**</span></span>             | <span data-ttu-id="b88a6-208">最小報告値</span><span class="sxs-lookup"><span data-stu-id="b88a6-208">Minimum reported value</span></span> |
| <span data-ttu-id="b88a6-209">**gx_progress_bar_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="b88a6-209">**gx_progress_bar_info_max_val**</span></span>             | <span data-ttu-id="b88a6-210">最大報告値</span><span class="sxs-lookup"><span data-stu-id="b88a6-210">Maximum reported value</span></span> |
| <span data-ttu-id="b88a6-211">**gx_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="b88a6-211">**gx_progress_bar_info_current_val**</span></span>         | <span data-ttu-id="b88a6-212">現在の値</span><span class="sxs-lookup"><span data-stu-id="b88a6-212">Current value</span></span> |
| <span data-ttu-id="b88a6-213">**gx_progress_bar_info_font_id**</span><span class="sxs-lookup"><span data-stu-id="b88a6-213">**gx_progress_bar_info_font_id**</span></span>             | <span data-ttu-id="b88a6-214">フォントのリソース ID。テキストの値 (オプション) をプログレス バー ウィジェットに描画する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-214">Resource ID of the font, used to draw the optional text value within the progress bar widget</span></span>      |
| <span data-ttu-id="b88a6-215">**gx_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="b88a6-215">**gx_progress_bar_normal_text_color**</span></span>        | <span data-ttu-id="b88a6-216">通常の状態のテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-216">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b88a6-217">**gx_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="b88a6-217">**gx_progress_bar_selected_text_color**</span></span>      | <span data-ttu-id="b88a6-218">ウィジェットにフォーカスしたときのテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-218">Resource ID of the text color when the widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b88a6-219">**gx_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="b88a6-219">**gx_progress_bar_disabled_text_color**</span></span>      | <span data-ttu-id="b88a6-220">GX_STYLE_ENABLED が有効でないときのテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-220">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b88a6-221">**gx_progress_bar_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b88a6-221">**gx_progress_bar_fill_pixelmap**</span></span>            | <span data-ttu-id="b88a6-222">背景の塗りつぶしに使用するピクセルマップのリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-222">Resource ID of the pixelmap for background filling</span></span>|

## <a name="gx_radial_progress_bar_info"></a><span data-ttu-id="b88a6-223">GX_RADIAL_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="b88a6-223">GX_RADIAL_PROGRESS_BAR_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="b88a6-224">定義</span><span class="sxs-lookup"><span data-stu-id="b88a6-224">Definition</span></span>

```c
typedef struct GX_RADIAL_PROGRESS_BAR_INFO_STRUCT
{
    GX_VALUE       gx_radial_progress_bar_info_xcenter;
    GX_VALUE       gx_radial_progress_bar_info_ycenter;
    GX_VALUE       gx_radial_progress_bar_info_radius;
    GX_VALUE       gx_radial_progress_bar_info_current_val;
    GX_VALUE       gx_radial_progress_bar_info_anchor_val;
    GX_RESOURCE_ID gx_radial_progress_bar_info_font_id;
    GX_RESOURCE_ID gx_radial_progress_bar_info_normal_text_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_selected_text_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_disabled_text_color;
    GX_VALUE       gx_radial_progress_bar_info_normal_brush_width;
    GX_VALUE       gx_radial_progress_bar_info_selected_brush_width;
    GX_RESOURCE_ID gx_radial_progress_bar_info_normal_brush_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_selected_brush_color;
} GX_RADIAL_PROGRESS_BAR_INFO;
```

| <span data-ttu-id="b88a6-225">メンバー</span><span class="sxs-lookup"><span data-stu-id="b88a6-225">Members</span></span> | <span data-ttu-id="b88a6-226">説明</span><span class="sxs-lookup"><span data-stu-id="b88a6-226">Description</span></span> |
| ------------------------------------------------- | -------------------------------------------- |
| <span data-ttu-id="b88a6-227">**gx_radial_progress_bar_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="b88a6-227">**gx_radial_progress_bar_info_xcenter**</span></span>           | <span data-ttu-id="b88a6-228">ウィジェットの x 座標上の位置</span><span class="sxs-lookup"><span data-stu-id="b88a6-228">Widget position in x coordinate</span></span> |
| <span data-ttu-id="b88a6-229">**gx_radial_progress_bar_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="b88a6-229">**gx_radial_progress_bar_info_ycenter**</span></span>           | <span data-ttu-id="b88a6-230">ウィジェットの y 座標上の位置</span><span class="sxs-lookup"><span data-stu-id="b88a6-230">Widget position in y coordinate</span></span>  |
| <span data-ttu-id="b88a6-231">**gx_radial_progress_bar_info_radius**</span><span class="sxs-lookup"><span data-stu-id="b88a6-231">**gx_radial_progress_bar_info_radius**</span></span>            | <span data-ttu-id="b88a6-232">プログレス サークルの半径</span><span class="sxs-lookup"><span data-stu-id="b88a6-232">Radius of the progress circle</span></span> |
| <span data-ttu-id="b88a6-233">**gx_radial_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="b88a6-233">**gx_radial_progress_bar_info_current_val**</span></span>       | <span data-ttu-id="b88a6-234">現在の値は、[-360, 360] の範囲で表され、アンカー位置と上半分の円弧の端点の角度差を表します。負の値を指定すると、アンカー位置から時計回りに円弧を描画します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-234">Current value, limited to the range [-360, 360], indicates the angular delta between the anchor position and the end point of the upper arc. Negative value causes the arc to be drawn in a clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="b88a6-235">正の値を指定すると、アンカー位置から反時計回りに円弧を描画します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-235">Positive value causes the arc to be drawn in a counter-clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="b88a6-236">アプリケーションは、実際に示されている値に必要な計算を施して得た角度を、プログレス バー ウィジェットに渡す必要があります</span><span class="sxs-lookup"><span data-stu-id="b88a6-236">The application must scale the real-word value being indicated to assign an angular value to the progress bar widget</span></span> |
| <span data-ttu-id="b88a6-237">**gx_radial_progress_bar_anchor_val**</span><span class="sxs-lookup"><span data-stu-id="b88a6-237">**gx_radial_progress_bar_anchor_val**</span></span>             | <span data-ttu-id="b88a6-238">プログレス サークルの上半分の開始角度。整数で角度を指定します。0° は直角で、真上を指す角度を表します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-238">Starting angle of the upper progress arc. The value is defined in terms of integer degree with 0 degree pointing to the right and 90 degree indicating straight up position.</span></span> |
| <span data-ttu-id="b88a6-239">**gx_radial_progress_bar_font_id**</span><span class="sxs-lookup"><span data-stu-id="b88a6-239">**gx_radial_progress_bar_font_id**</span></span>                | <span data-ttu-id="b88a6-240">プログレス バー ウィジェットにテキスト (オプション) を描画する際に使用するフォントのリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-240">Resource ID of the font used to draw the optional text value within the progress bar widget</span></span> |
| <span data-ttu-id="b88a6-241">**gx_radial_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="b88a6-241">**gx_radial_progress_bar_normal_text_color**</span></span>      | <span data-ttu-id="b88a6-242">通常の状態のテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-242">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b88a6-243">**gx_radial_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="b88a6-243">**gx_radial_progress_bar_selected_text_color**</span></span>    |<span data-ttu-id="b88a6-244">ウィジェットにフォーカスしたときのテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します</span><span class="sxs-lookup"><span data-stu-id="b88a6-244">Resource ID of the text color when widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b88a6-245">**gx_radial_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="b88a6-245">**gx_radial_progress_bar_disabled_text_color**</span></span>    | <span data-ttu-id="b88a6-246">GX_STYLE_ENABLED が有効でないときのテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-246">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b88a6-247">**gx_radial_progress_bar_normal_brush_width**</span><span class="sxs-lookup"><span data-stu-id="b88a6-247">**gx_radial_progress_bar_normal_brush_width**</span></span>     | <span data-ttu-id="b88a6-248">プログレス サークルの下半分のゲージの幅</span><span class="sxs-lookup"><span data-stu-id="b88a6-248">Width of the lower progress circle</span></span> |
| <span data-ttu-id="b88a6-249">**gx_radial_progress_bar_selected_brush_width**</span><span class="sxs-lookup"><span data-stu-id="b88a6-249">**gx_radial_progress_bar_selected_brush_width**</span></span>   | <span data-ttu-id="b88a6-250">プログレス サークルの上半分のゲージの幅。上半分を下半分より細くも太くもでき、同じにもできます。</span><span class="sxs-lookup"><span data-stu-id="b88a6-250">Width of the upper progress arc, the upper arc may be narrower, the same as, or wider than the lower circle</span></span> |
| <span data-ttu-id="b88a6-251">**gx_radial_progress_bar_normal_brush_color**</span><span class="sxs-lookup"><span data-stu-id="b88a6-251">**gx_radial_progress_bar_normal_brush_color**</span></span>     | <span data-ttu-id="b88a6-252">プログレス サークルの下半分のゲージを塗りつぶす色のリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-252">Resource ID of the color to fill lower progress circle</span></span> |
| <span data-ttu-id="b88a6-253">**gx_radial_progress_bar_selected_brush_color**</span><span class="sxs-lookup"><span data-stu-id="b88a6-253">**gx_radial_progress_bar_selected_brush_color**</span></span>   | <span data-ttu-id="b88a6-254">プログレス サークルの上半分のゲージを塗りつぶす色のリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-254">Resource ID of the color to fill upper progress arc</span></span> |

## <a name="gx_radial_slider_info"></a><span data-ttu-id="b88a6-255">GX_RADIAL_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="b88a6-255">GX_RADIAL_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b88a6-256">定義</span><span class="sxs-lookup"><span data-stu-id="b88a6-256">Definition</span></span>

```c
typedef struct GX_RADIAL_SLIDER_INFO_STRUCT
{
    GX_VALUE       gx_radial_slider_info_xcenter;
    GX_VALUE       gx_radial_slider_info_ycenter;
    USHORT         gx_radial_slider_info_radius;
    USHORT         gx_radial_slider_info_track_width;
    GX_VALUE       gx_radial_slider_info_current_angle;
    GX_VALUE       gx_radial_slider_info_min_angle;
    GX_VALUE       gx_radial_slider_info_max_angle;
    GX_VALUE      *gx_radial_slider_info_angle_list;
    USHORT         gx_radial_slider_info_list_cont;
    GX_RESOURCE_ID gx_radial_slider_info_background_pixelmap;
    GX_RESOURCE_ID gx_radial_slider_info_needle_pixelmap;
} GX_RADIAL_SLIDER_INFO;
```

| <span data-ttu-id="b88a6-257">メンバー</span><span class="sxs-lookup"><span data-stu-id="b88a6-257">Members</span></span> | <span data-ttu-id="b88a6-258">説明</span><span class="sxs-lookup"><span data-stu-id="b88a6-258">Description</span></span> |
| --------------------------------------------- | ------------------------------------------------ |
<span data-ttu-id="b88a6-259">**gx_radial_slider_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="b88a6-259">**gx_radial_slider_info_xcenter**</span></span>               | <span data-ttu-id="b88a6-260">スライダー ウィジェットの左端からスライダーの針の回転中心までの距離</span><span class="sxs-lookup"><span data-stu-id="b88a6-260">Distance from the left of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="b88a6-261">**gx_radial_slider_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="b88a6-261">**gx_radial_slider_info_ycenter**</span></span>             | <span data-ttu-id="b88a6-262">スライダー ウィジェットの上端からスライダーの針の回転中心までの距離</span><span class="sxs-lookup"><span data-stu-id="b88a6-262">Distance from the top of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="b88a6-263">**gx_radial_slider_info_radius**</span><span class="sxs-lookup"><span data-stu-id="b88a6-263">**gx_radial_slider_info_radius**</span></span>              | <span data-ttu-id="b88a6-264">円形スライダーの半径</span><span class="sxs-lookup"><span data-stu-id="b88a6-264">Radius of the radial slider circle</span></span> |
| <span data-ttu-id="b88a6-265">**gx_radial_slider_info_track_width**</span><span class="sxs-lookup"><span data-stu-id="b88a6-265">**gx_radial_slider_info_track_width**</span></span>         | <span data-ttu-id="b88a6-266">円形スライダーのゲージの幅</span><span class="sxs-lookup"><span data-stu-id="b88a6-266">Width of radial slider track</span></span> |
| <span data-ttu-id="b88a6-267">**gx_radial_slider_info_current_angle**</span><span class="sxs-lookup"><span data-stu-id="b88a6-267">**gx_radial_slider_info_current_angle**</span></span>       | <span data-ttu-id="b88a6-268">スライダーの現在の角度</span><span class="sxs-lookup"><span data-stu-id="b88a6-268">Current slider angle</span></span> |
| <span data-ttu-id="b88a6-269">**gx_radial_slider_info_min_angle**</span><span class="sxs-lookup"><span data-stu-id="b88a6-269">**gx_radial_slider_info_min_angle**</span></span>           | <span data-ttu-id="b88a6-270">スライダーの最小角度</span><span class="sxs-lookup"><span data-stu-id="b88a6-270">Minimum slider angle</span></span> |
| <span data-ttu-id="b88a6-271">**gx_radial_slider_info_max_angle**</span><span class="sxs-lookup"><span data-stu-id="b88a6-271">**gx_radial_slider_info_max_angle**</span></span>           | <span data-ttu-id="b88a6-272">スライダーの最大角度</span><span class="sxs-lookup"><span data-stu-id="b88a6-272">Maximum slider angle</span></span> |
| <span data-ttu-id="b88a6-273">**gx_radial_slider_info_angle_list**</span><span class="sxs-lookup"><span data-stu-id="b88a6-273">**gx_radial_slider_info_angle_list**</span></span>          | <span data-ttu-id="b88a6-274">アンカー角度を指定する、角度の値のリスト。値を指定すると、スライダーは指定したアンカー角度だけを取ります。</span><span class="sxs-lookup"><span data-stu-id="b88a6-274">Angle value list, defines anchor angles, if set, slider angle can only be one of the defined anchor angles</span></span> |
| <span data-ttu-id="b88a6-275">**gx_radial_slider_info_list_count**</span><span class="sxs-lookup"><span data-stu-id="b88a6-275">**gx_radial_slider_info_list_count**</span></span>          | <span data-ttu-id="b88a6-276">アンカー角度の数</span><span class="sxs-lookup"><span data-stu-id="b88a6-276">Number of anchor angles</span></span> |
| <span data-ttu-id="b88a6-277">**gx_radial_slider_info_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b88a6-277">**gx_radial_slider_info_background_pixelmap**</span></span> | <span data-ttu-id="b88a6-278">背景のピクセルマップのリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-278">Resource ID of background pixelmap</span></span> |
| <span data-ttu-id="b88a6-279">**gx_radial_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b88a6-279">**gx_radial_slider_info_needle_pixelmap**</span></span>     | <span data-ttu-id="b88a6-280">針のピクセルマップのリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-280">Resource ID of needle pixelmap</span></span> |

## <a name="gx_rectangle"></a><span data-ttu-id="b88a6-281">GX_RECTANGLE</span><span class="sxs-lookup"><span data-stu-id="b88a6-281">GX_RECTANGLE</span></span>

### <a name="definition"></a><span data-ttu-id="b88a6-282">定義</span><span class="sxs-lookup"><span data-stu-id="b88a6-282">Definition</span></span>

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

| <span data-ttu-id="b88a6-283">メンバー</span><span class="sxs-lookup"><span data-stu-id="b88a6-283">Members</span></span> | <span data-ttu-id="b88a6-284">説明</span><span class="sxs-lookup"><span data-stu-id="b88a6-284">Description</span></span> |
| -------------------------------- | ------------------------|
| <span data-ttu-id="b88a6-285">**gx_rectangle_left**</span><span class="sxs-lookup"><span data-stu-id="b88a6-285">**gx_rectangle_left**</span></span>            | <span data-ttu-id="b88a6-286">長方形の左端</span><span class="sxs-lookup"><span data-stu-id="b88a6-286">Left of the rectangle</span></span>   |  
| <span data-ttu-id="b88a6-287">**gx_rectangle_top**</span><span class="sxs-lookup"><span data-stu-id="b88a6-287">**gx_rectangle_top**</span></span>             | <span data-ttu-id="b88a6-288">長方形の上端</span><span class="sxs-lookup"><span data-stu-id="b88a6-288">Top of the rectangle</span></span>    | 
| <span data-ttu-id="b88a6-289">**gx_rectangle_right**</span><span class="sxs-lookup"><span data-stu-id="b88a6-289">**gx_rectangle_right**</span></span>           | <span data-ttu-id="b88a6-290">長方形の右端</span><span class="sxs-lookup"><span data-stu-id="b88a6-290">Right of the rectangle</span></span>  |
| <span data-ttu-id="b88a6-291">**gx_rectangle_bottom**</span><span class="sxs-lookup"><span data-stu-id="b88a6-291">**gx_rectangle_bottom**</span></span>          | <span data-ttu-id="b88a6-292">長方形の下端</span><span class="sxs-lookup"><span data-stu-id="b88a6-292">Bottom of the rectangle</span></span> |

## <a name="gx_rich_text_fonts"></a><span data-ttu-id="b88a6-293">GX_RICH_TEXT_FONTS</span><span class="sxs-lookup"><span data-stu-id="b88a6-293">GX_RICH_TEXT_FONTS</span></span> 

### <a name="definition"></a><span data-ttu-id="b88a6-294">定義</span><span class="sxs-lookup"><span data-stu-id="b88a6-294">Definition</span></span>

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

| <span data-ttu-id="b88a6-295">メンバー</span><span class="sxs-lookup"><span data-stu-id="b88a6-295">Members</span></span> | <span data-ttu-id="b88a6-296">説明</span><span class="sxs-lookup"><span data-stu-id="b88a6-296">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b88a6-297">**gx_rich_text_fonts_normal_id**</span><span class="sxs-lookup"><span data-stu-id="b88a6-297">**gx_rich_text_fonts_normal_id**</span></span>   | <span data-ttu-id="b88a6-298">通常のフォントのリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-298">Resource ID of normal text font</span></span> |
| <span data-ttu-id="b88a6-299">**gx_rich_text_fonts_bold_id**</span><span class="sxs-lookup"><span data-stu-id="b88a6-299">**gx_rich_text_fonts_bold_id**</span></span>     | <span data-ttu-id="b88a6-300">太字のフォントのリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-300">Resource ID of bold text font</span></span> |
| <span data-ttu-id="b88a6-301">**gx_rich_text_fonts_italic_id**</span><span class="sxs-lookup"><span data-stu-id="b88a6-301">**gx_rich_text_fonts_italic_id**</span></span>   | <span data-ttu-id="b88a6-302">斜体のフォントのリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-302">Resource ID of italic text font</span></span> |
| <span data-ttu-id="b88a6-303">**gx_rich_text_fonts_bold_italic_id**</span><span class="sxs-lookup"><span data-stu-id="b88a6-303">**gx_rich_text_fonts_bold_italic_id**</span></span> | <span data-ttu-id="b88a6-304">太字の斜体のフォントのリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-304">Resource ID of bold italic text font</span></span> |

## <a name="gx_scroll_info"></a><span data-ttu-id="b88a6-305">GX_SCROLL_INFO</span><span class="sxs-lookup"><span data-stu-id="b88a6-305">GX_SCROLL_INFO</span></span> 
### <a name="definition"></a><span data-ttu-id="b88a6-306">**定義**</span><span class="sxs-lookup"><span data-stu-id="b88a6-306">**Definition**</span></span>

```c
typedef struct GX_SCROLL_INFO_STRUCT
{
    INT      gx_scroll_value;
    INT      gx_scroll_minimum;
    INT      gx_scroll_maximum;
    GX_VALUE gx_scroll_visible;
    GX_VALUE gx_scroll_increment;
} GX_SCROLL_INFO;
```

| <span data-ttu-id="b88a6-307">メンバー</span><span class="sxs-lookup"><span data-stu-id="b88a6-307">Members</span></span> | <span data-ttu-id="b88a6-308">説明</span><span class="sxs-lookup"><span data-stu-id="b88a6-308">Description</span></span> |
| ----------------------- | ----------------------------- |
| <span data-ttu-id="b88a6-309">**gx_scroll_value**</span><span class="sxs-lookup"><span data-stu-id="b88a6-309">**gx_scroll_value**</span></span>     | <span data-ttu-id="b88a6-310">現在のスクロール位置</span><span class="sxs-lookup"><span data-stu-id="b88a6-310">Current scroll position</span></span>       |
| <span data-ttu-id="b88a6-311">**gx_scroll_minimum**</span><span class="sxs-lookup"><span data-stu-id="b88a6-311">**gx_scroll_minimum**</span></span>   | <span data-ttu-id="b88a6-312">最小報告位置</span><span class="sxs-lookup"><span data-stu-id="b88a6-312">Minimum reported position</span></span>     |
| <span data-ttu-id="b88a6-313">**gx_scroll_maximum**</span><span class="sxs-lookup"><span data-stu-id="b88a6-313">**gx_scroll_maximum**</span></span>   | <span data-ttu-id="b88a6-314">最大報告位置</span><span class="sxs-lookup"><span data-stu-id="b88a6-314">Maximum reported position</span></span>     |
| <span data-ttu-id="b88a6-315">**gx_scroll_visible**</span><span class="sxs-lookup"><span data-stu-id="b88a6-315">**gx_scroll_visible**</span></span>   | <span data-ttu-id="b88a6-316">親ウィンドウの表示範囲</span><span class="sxs-lookup"><span data-stu-id="b88a6-316">Parent window visible range</span></span>   |
| <span data-ttu-id="b88a6-317">**gx_scroll_increment**</span><span class="sxs-lookup"><span data-stu-id="b88a6-317">**gx_scroll_increment**</span></span> | <span data-ttu-id="b88a6-318">スクロールバーの最小移動量</span><span class="sxs-lookup"><span data-stu-id="b88a6-318">Scrollbar minimum delta value</span></span> |

## <a name="gx_scrollbar_appearance"></a><span data-ttu-id="b88a6-319">GX_SCROLLBAR_APPEARANCE</span><span class="sxs-lookup"><span data-stu-id="b88a6-319">GX_SCROLLBAR_APPEARANCE</span></span> 

### <a name="definition"></a><span data-ttu-id="b88a6-320">定義</span><span class="sxs-lookup"><span data-stu-id="b88a6-320">Definition</span></span>

```c
typedef struct GX_SCROLLBAR_APPEARANCE_STRUCT
{
    GX_VALUE       gx_scroll_width;
    GX_VALUE       gx_scroll_thumb_width;
    GX_VALUE       gx_scroll_thumb_travel_min;
    GX_VALUE       gx_scroll_thumb_travel_max;
    GX_UBYTE       gx_scroll_thumb_border_style;
    GX_RESOURCE_ID gx_scroll_fill_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_pixelmap;
    GX_RESOURCE_ID gx_scroll_up_pixelmap;
    GX_RESOURCE_ID gx_scroll_down_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_color;
    GX_RESOURCE_ID gx_scroll_thumb_border_color;
    GX_RESOURCE_ID gx_scroll_button_color;
} GX_SCROLLBAR_APPEARANCE;
```

| <span data-ttu-id="b88a6-321">メンバー</span><span class="sxs-lookup"><span data-stu-id="b88a6-321">Members</span></span> | <span data-ttu-id="b88a6-322">説明</span><span class="sxs-lookup"><span data-stu-id="b88a6-322">Description</span></span> |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="b88a6-323">**gx_scroll_width**</span><span class="sxs-lookup"><span data-stu-id="b88a6-323">**gx_scroll_width**</span></span>                      | <span data-ttu-id="b88a6-324">スクロールバー ウィジェットの幅 (ピクセル単位)</span><span class="sxs-lookup"><span data-stu-id="b88a6-324">Width of the scrollbar widget, in pixels</span></span> |
| <span data-ttu-id="b88a6-325">**gx_scroll_thumb_width**</span><span class="sxs-lookup"><span data-stu-id="b88a6-325">**gx_scroll_thumb_width**</span></span>                | <span data-ttu-id="b88a6-326">スクロールバー上をスライドするつまみの幅 (ピクセル単位)。</span><span class="sxs-lookup"><span data-stu-id="b88a6-326">Width of the thumb button which slides on the scrollbar, in pixels.</span></span> <span data-ttu-id="b88a6-327">通常この値は、スクロールバーの全体の幅よりも小さいピクセル数です</span><span class="sxs-lookup"><span data-stu-id="b88a6-327">This value is usually some number of pixels less than the total scrollbar width</span></span> |
| <span data-ttu-id="b88a6-328">**gx_scroll_thumb_travel_min**</span><span class="sxs-lookup"><span data-stu-id="b88a6-328">**gx_scroll_thumb_travel_min**</span></span>           | <span data-ttu-id="b88a6-329">スクロールバーの端とつまみの最小移動位置の間のオフセット。</span><span class="sxs-lookup"><span data-stu-id="b88a6-329">Offset from the end of scrollbar to minimum thumb button travel point.</span></span> <span data-ttu-id="b88a6-330">この制限を適用すると、つまみがスクロールバーの本当の端まで移動することを防げます</span><span class="sxs-lookup"><span data-stu-id="b88a6-330">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="b88a6-331">**gx_scroll_thumb_travel_max**</span><span class="sxs-lookup"><span data-stu-id="b88a6-331">**gx_scroll_thumb_travel_max**</span></span>           | <span data-ttu-id="b88a6-332">スクロールバーの端とつまみの最大移動位置の間のオフセット。</span><span class="sxs-lookup"><span data-stu-id="b88a6-332">Offset from the end of scrollbar to maximum thumb button travel point.</span></span> <span data-ttu-id="b88a6-333">この制限を適用すると、つまみがスクロールバーの本当の端まで移動することを防げます</span><span class="sxs-lookup"><span data-stu-id="b88a6-333">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="b88a6-334">**gx_scroll_thumb_border_style**</span><span class="sxs-lookup"><span data-stu-id="b88a6-334">**gx_scroll_thumb_border_style**</span></span>         | <span data-ttu-id="b88a6-335">つまみの境界のスタイル</span><span class="sxs-lookup"><span data-stu-id="b88a6-335">Border styles of thumb button</span></span> |
| <span data-ttu-id="b88a6-336">**gx_scroll_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b88a6-336">**gx_scroll_fill_pixelmap**</span></span>              | <span data-ttu-id="b88a6-337">ピクセルマップ ID (オプション)。</span><span class="sxs-lookup"><span data-stu-id="b88a6-337">Optional pixelmap ID.</span></span> <span data-ttu-id="b88a6-338">このピクセルマップ ID がゼロでない場合、そのピクセルマップを使用してスクロールバーの背景を描画します</span><span class="sxs-lookup"><span data-stu-id="b88a6-338">If this pixelmap ID is not zero, the scrollbar uses this pixelmap to draw the scrollbar background</span></span> |
| <span data-ttu-id="b88a6-339">**gx_scroll_thumb_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b88a6-339">**gx_scroll_thumb_pixelmap**</span></span>             | <span data-ttu-id="b88a6-340">ピクセルマップ ID (オプション)。</span><span class="sxs-lookup"><span data-stu-id="b88a6-340">Optional pixelmap ID.</span></span> <span data-ttu-id="b88a6-341">このピクセルマップ ID がゼロでない場合、そのピクセルマップを使用してスクロールバーのつまみを描画します</span><span class="sxs-lookup"><span data-stu-id="b88a6-341">If this pixelmap ID is not zero, the scrollbar thumb button uses this pixelmap to draw itself</span></span> |
| <span data-ttu-id="b88a6-342">**gx_scroll_up_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b88a6-342">**gx_scroll_up_pixelmap**</span></span>                | <span data-ttu-id="b88a6-343">ピクセルマップ ID (オプション)。</span><span class="sxs-lookup"><span data-stu-id="b88a6-343">Optional pixelmap ID.</span></span> <span data-ttu-id="b88a6-344">このピクセルマップ ID がゼロでない場合、その ID を使用してスクロールバー左端/上端のボタンを描画します</span><span class="sxs-lookup"><span data-stu-id="b88a6-344">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar left/up end button</span></span> |
| <span data-ttu-id="b88a6-345">**gx_scroll_down_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b88a6-345">**gx_scroll_down_pixelmap**</span></span>              | <span data-ttu-id="b88a6-346">ピクセルマップ ID (オプション)。</span><span class="sxs-lookup"><span data-stu-id="b88a6-346">Optional pixelmap ID.</span></span> <span data-ttu-id="b88a6-347">このピクセルマップ ID がゼロでない場合、その ID を使用してスクロールバー右端/下端のボタンを描画します</span><span class="sxs-lookup"><span data-stu-id="b88a6-347">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar right/down end button</span></span> |
| <span data-ttu-id="b88a6-348">**gx_scroll_thumb_color**</span><span class="sxs-lookup"><span data-stu-id="b88a6-348">**gx_scroll_thumb_color**</span></span>                | <span data-ttu-id="b88a6-349">つまみの塗りつぶしに使用する色のリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-349">Resource ID of color used to fill thumb button</span></span> |
| <span data-ttu-id="b88a6-350">**gx_scroll_thumb_border_color**</span><span class="sxs-lookup"><span data-stu-id="b88a6-350">**gx_scroll_thumb_border_color**</span></span>         | <span data-ttu-id="b88a6-351">つまみの境界の描画に使用する色のリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-351">Resource ID of color used to draw the border of thumb button</span></span> | 
| <span data-ttu-id="b88a6-352">**gx_scroll_button_color**</span><span class="sxs-lookup"><span data-stu-id="b88a6-352">**gx_scroll_button_color**</span></span>               | <span data-ttu-id="b88a6-353">スクロールバーの端のボタンの塗りつぶしに使用する色のリソース ID</span><span class="sxs-lookup"><span data-stu-id="b88a6-353">Resource ID of color used to fill scrollbar end buttons</span></span> |

## <a name="gx_slider_info"></a><span data-ttu-id="b88a6-354">GX_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="b88a6-354">GX_SLIDER_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="b88a6-355">定義</span><span class="sxs-lookup"><span data-stu-id="b88a6-355">Definition</span></span>

```c
typedef struct GX_SLIDER_INFO_STRUCT
{
    INT      gx_slider_info_min_val;
    INT      gx_slider_info_max_val;
    INT      gx_slider_info_current_val;
    INT      gx_slider_info_increment;
    GX_VALUE gx_slider_info_min_travel;
    GX_VALUE gx_slider_info_max_travel;
    GX_VALUE gx_slider_info_needle_width;
    GX_VALUE gx_slider_info_needle_height;
    GX_VALUE gx_slider_info_needle_inset;
    GX_VALUE gx_slider_info_needle_hotspot_offset;
} GX_SLIDER_INFO;
```

| <span data-ttu-id="b88a6-356">メンバー</span><span class="sxs-lookup"><span data-stu-id="b88a6-356">Members</span></span> | <span data-ttu-id="b88a6-357">説明</span><span class="sxs-lookup"><span data-stu-id="b88a6-357">Description</span></span> |
| --------------------------------------- | ------------------------------------------------------ |
| <span data-ttu-id="b88a6-358">**gx_slider_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="b88a6-358">**gx_slider_info_min_val**</span></span>              | <span data-ttu-id="b88a6-359">最小報告値</span><span class="sxs-lookup"><span data-stu-id="b88a6-359">Minimum reported value</span></span> |
| <span data-ttu-id="b88a6-360">**gx_slider_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="b88a6-360">**gx_slider_info_max_val**</span></span>              | <span data-ttu-id="b88a6-361">最大報告値</span><span class="sxs-lookup"><span data-stu-id="b88a6-361">Maximum reported value</span></span> |
| <span data-ttu-id="b88a6-362">**gx_slider_info_current_value**</span><span class="sxs-lookup"><span data-stu-id="b88a6-362">**gx_slider_info_current_value**</span></span>        | <span data-ttu-id="b88a6-363">現在の値</span><span class="sxs-lookup"><span data-stu-id="b88a6-363">Current value</span></span> |
| <span data-ttu-id="b88a6-364">**gx_slider_info_min_travel**</span><span class="sxs-lookup"><span data-stu-id="b88a6-364">**gx_slider_info_min_travel**</span></span>           | <span data-ttu-id="b88a6-365">針の移動限度</span><span class="sxs-lookup"><span data-stu-id="b88a6-365">Needle travel limit</span></span> |
| <span data-ttu-id="b88a6-366">**gx_slider_info_max_travel**</span><span class="sxs-lookup"><span data-stu-id="b88a6-366">**gx_slider_info_max_travel**</span></span>           | <span data-ttu-id="b88a6-367">針の移動限度</span><span class="sxs-lookup"><span data-stu-id="b88a6-367">Needle travel limit</span></span> |
| <span data-ttu-id="b88a6-368">**gx_slider_info_needle_width**</span><span class="sxs-lookup"><span data-stu-id="b88a6-368">**gx_slider_info_needle_width**</span></span>         | <span data-ttu-id="b88a6-369">針の幅 (ピクセル単位)</span><span class="sxs-lookup"><span data-stu-id="b88a6-369">Needle width in pixel</span></span> |
| <span data-ttu-id="b88a6-370">**gx_slider_info_needle_height**</span><span class="sxs-lookup"><span data-stu-id="b88a6-370">**gx_slider_info_needle_height**</span></span>        | <span data-ttu-id="b88a6-371">針の高さ (ピクセル単位)</span><span class="sxs-lookup"><span data-stu-id="b88a6-371">Needle height in pixel</span></span> |
|<span data-ttu-id="b88a6-372">**gx_slider_info_needle_inset**</span><span class="sxs-lookup"><span data-stu-id="b88a6-372">**gx_slider_info_needle_inset**</span></span>          | <span data-ttu-id="b88a6-373">針の描画位置。</span><span class="sxs-lookup"><span data-stu-id="b88a6-373">Needle draw position.</span></span> <span data-ttu-id="b88a6-374">GX_STYLE_SLIDER_VERTICAL が有効である場合、これは、針の描画開始位置とスライダー左端の間のオフセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-374">If GX_STYLE_SLIDER_VERTICAL is set, used to specify the offset from the needle draw start position to the slider left.</span></span> <span data-ttu-id="b88a6-375">そうでない場合は、針の描画開始位置とスライダー上端の間のオフセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-375">Else, used to specify the offset from the needle draw start position to the slider top.</span></span> |
| <span data-ttu-id="b88a6-376">**gx_slider_info_needle_hotspot_offset**</span><span class="sxs-lookup"><span data-stu-id="b88a6-376">**gx_slider_info_needle_hotspot_offset**</span></span> | <span data-ttu-id="b88a6-377">針の描画開始位置とスライダーのホット スポットの間のオフセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-377">Needle hotpot_offset, used to specify the offset from the needle draw start position to the slider hotspot.</span></span> |

## <a name="gx_sprite_frame"></a><span data-ttu-id="b88a6-378">GX_SPRITE_FRAME</span><span class="sxs-lookup"><span data-stu-id="b88a6-378">GX_SPRITE_FRAME</span></span>

### <a name="definition"></a><span data-ttu-id="b88a6-379">定義</span><span class="sxs-lookup"><span data-stu-id="b88a6-379">Definition</span></span>

```c
typedef struct GX_SPRITE_FRAME_STRUCT
{
    GX_RESOURCE_ID gx_sprite_frame_pixelmap;
    GX_VALUE gx_sprite_frame_x_offset;
    GX_VALUE gx_sprite_frame_y_offset;
    UINT gx_sprite_frame_delay;
    UINT gx_sprite_frame_background_operation;
    UCHAR gx_sprite_frame_alpha;
} GX_SPRITE_FRAME;
```

| <span data-ttu-id="b88a6-380">メンバー</span><span class="sxs-lookup"><span data-stu-id="b88a6-380">Members</span></span> | <span data-ttu-id="b88a6-381">説明</span><span class="sxs-lookup"><span data-stu-id="b88a6-381">Description</span></span> |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="b88a6-382">**gx_sprite_frame_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b88a6-382">**gx_sprite_frame_pixelmap**</span></span>             | <span data-ttu-id="b88a6-383">このフレームに表示するピクセルマップのリソース ID。</span><span class="sxs-lookup"><span data-stu-id="b88a6-383">Resource ID of the pixelmap to be displayed for this frame.</span></span> <span data-ttu-id="b88a6-384">ID には 0 も指定できます。</span><span class="sxs-lookup"><span data-stu-id="b88a6-384">The ID can be 0.</span></span> |
| <span data-ttu-id="b88a6-385">**gx_sprite_frame_x_offset**</span><span class="sxs-lookup"><span data-stu-id="b88a6-385">**gx_sprite_frame_x_offset**</span></span>             | <span data-ttu-id="b88a6-386">スプライト ウィジェット左端と表示するピクセルマップの間のオフセット</span><span class="sxs-lookup"><span data-stu-id="b88a6-386">Offset from the sprite widget left to display the pixelmap</span></span> |
| <span data-ttu-id="b88a6-387">**gx_sprite_frame_y_offset**</span><span class="sxs-lookup"><span data-stu-id="b88a6-387">**gx_sprite_frame_y_offset**</span></span>             | <span data-ttu-id="b88a6-388">スプライト ウィジェット上端と表示するピクセルマップの間のオフセット</span><span class="sxs-lookup"><span data-stu-id="b88a6-388">Offset from the sprite widget top to display the pixelmap</span></span> |
| <span data-ttu-id="b88a6-389">**gx_sprite_frame_delay**</span><span class="sxs-lookup"><span data-stu-id="b88a6-389">**gx_sprite_frame_delay**</span></span>                | <span data-ttu-id="b88a6-390">スプライトのフレームを表示する間隔。GUIX タイマー刻み単位。</span><span class="sxs-lookup"><span data-stu-id="b88a6-390">Delay value, in GUIX timer ticks, after displaying this frame before advancing to the next sprite frame</span></span> |
| <span data-ttu-id="b88a6-391">**gx_sprite_frame_background_operation**</span><span class="sxs-lookup"><span data-stu-id="b88a6-391">**gx_sprite_frame_background_operation**</span></span> | <span data-ttu-id="b88a6-392">背景を消去する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-392">Define how the background should be erased.</span></span> <span data-ttu-id="b88a6-393">このフィールドで使用できる値:</span><span class="sxs-lookup"><span data-stu-id="b88a6-393">Possible values for this field are:</span></span><br /><span data-ttu-id="b88a6-394">GX_SPRITE_BACKGROUND_NO_ACTION: フレーム間の補完を行いません</span><span class="sxs-lookup"><span data-stu-id="b88a6-394">GX_SPRITE_BACKGROUND_NO_ACTION: No fill between frames</span></span><br /><span data-ttu-id="b88a6-395">GX_SPRITE_BACKGROUND_SOLID_FILL: スプライトの背景を再描画します</span><span class="sxs-lookup"><span data-stu-id="b88a6-395">GX_SPRITE_BACKGROUND_SOLID_FILL: Redraw sprite background</span></span><br /><span data-ttu-id="b88a6-396">GX_SPRITE_BACKGROUND_RESTORE: 前のピクセルマップを復元します</span><span class="sxs-lookup"><span data-stu-id="b88a6-396">GX_SPRITE_BACKGROUND_RESTORE: Restore previous pixelmap</span></span> |
| <span data-ttu-id="b88a6-397">**gx_sprite_frame_alpha**</span><span class="sxs-lookup"><span data-stu-id="b88a6-397">**gx_sprite_frame_alpha**</span></span>                | <span data-ttu-id="b88a6-398">表示するピクセルマップに追加するアルファ値。</span><span class="sxs-lookup"><span data-stu-id="b88a6-398">Alpha value to be added to the displayed pixelmap.</span></span> <span data-ttu-id="b88a6-399">値255は、追加のアルファ値を適用しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-399">The value 255 specifies that no extra alpha value should be imposed.</span></span> <span data-ttu-id="b88a6-400">ピクセルマップがアルファ チャネルを含む場合、このアルファ チャネルをフレームのアルファ値に追加します。</span><span class="sxs-lookup"><span data-stu-id="b88a6-400">If the pixelmap includes an alpha channel, this alpha channel will be added to the frame alpha value.</span></span> |
