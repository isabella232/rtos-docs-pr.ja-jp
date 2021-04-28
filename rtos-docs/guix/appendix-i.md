---
title: 別表 I - GUIX 情報構造体
description: GUIX 情報構造体について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 03a10aeb65017befaf5e7b440046dbff9f9252ef
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812026"
---
# <a name="appendix-i---guix-information-structures"></a><span data-ttu-id="7a73b-103">別表 I - GUIX 情報構造体</span><span class="sxs-lookup"><span data-stu-id="7a73b-103">Appendix I - GUIX Information Structures</span></span> 

## <a name="gx_bidi_text_info"></a><span data-ttu-id="7a73b-104">GX_BIDI_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="7a73b-104">GX_BIDI_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="7a73b-105">定義</span><span class="sxs-lookup"><span data-stu-id="7a73b-105">Definition</span></span>

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```

### <a name="members"></a><span data-ttu-id="7a73b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a73b-106">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="7a73b-107">**gx_bidi_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="7a73b-107">**gx_bidi_text_info_text**</span></span>               | <span data-ttu-id="7a73b-108">並べ替えを行うテキスト</span><span class="sxs-lookup"><span data-stu-id="7a73b-108">Text for reordering</span></span> |
| <span data-ttu-id="7a73b-109">**gx_bidi_text_info_font**</span><span class="sxs-lookup"><span data-stu-id="7a73b-109">**gx_bidi_text_info_font**</span></span>               | <span data-ttu-id="7a73b-110">テキストの表示に使用するフォント。改行が必要ない場合は GX_NULL に設定します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-110">Font used to display text, set it to GX_NULL if line breaking is not needed</span></span> |
| <span data-ttu-id="7a73b-111">**gx_bidi_text_info_display_width**</span><span class="sxs-lookup"><span data-stu-id="7a73b-111">**gx_bidi_text_info_display_width**</span></span>      | <span data-ttu-id="7a73b-112">表示に使用できる幅。改行が必要ない場合は -1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-112">Available width for displaying, set it to -1 if line breaking is not needed</span></span> |

## <a name="gx_bidi_resolved_text_info"></a><span data-ttu-id="7a73b-113">GX_BIDI_RESOLVED_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="7a73b-113">GX_BIDI_RESOLVED_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="7a73b-114">定義</span><span class="sxs-lookup"><span data-stu-id="7a73b-114">Definition</span></span>

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

### <a name="members"></a><span data-ttu-id="7a73b-115">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a73b-115">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="7a73b-116">**gx_bidi_resolved_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="7a73b-116">**gx_bidi_resolved_text_info_text**</span></span>             | <span data-ttu-id="7a73b-117">並べ替えた bidi テキストの配列へのポインター</span><span class="sxs-lookup"><span data-stu-id="7a73b-117">Pointer to the array of reordered bidi text</span></span> |
| <span data-ttu-id="7a73b-118">**gx_bidi_resolved_text_info_total_lines**</span><span class="sxs-lookup"><span data-stu-id="7a73b-118">**gx_bidi_resolved_text_info_total_lines**</span></span>      | <span data-ttu-id="7a73b-119">処理済み bidi テキストの 1 段落の合計行数</span><span class="sxs-lookup"><span data-stu-id="7a73b-119">Total lines of resolved bidi text for one paragraph</span></span> |
| <span data-ttu-id="7a73b-120">**gx_bidi_resolved_text_info_next**</span><span class="sxs-lookup"><span data-stu-id="7a73b-120">**gx_bidi_resolved_text_info_next**</span></span>             | <span data-ttu-id="7a73b-121">次の段落の処理済み bidi テキストの情報</span><span class="sxs-lookup"><span data-stu-id="7a73b-121">Resolved bidi text information for the next paragraph</span></span> |

## <a name="gx_circular_gauge_info"></a><span data-ttu-id="7a73b-122">GX_CIRCULAR_GAUGE_INFO</span><span class="sxs-lookup"><span data-stu-id="7a73b-122">GX_CIRCULAR_GAUGE_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="7a73b-123">定義</span><span class="sxs-lookup"><span data-stu-id="7a73b-123">Definition</span></span>

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
### <a name="members"></a><span data-ttu-id="7a73b-124">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a73b-124">Members</span></span>

|                                                  |                                              |
| ------------------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="7a73b-125">**gx_circular_gauge_info_animation_steps**</span><span class="sxs-lookup"><span data-stu-id="7a73b-125">**gx_circular_gauge_info_animation_steps**</span></span>       | <span data-ttu-id="7a73b-126">現在の角度から新たに割り当てられる角度まで針が回るときに経る合計ステップ数</span><span class="sxs-lookup"><span data-stu-id="7a73b-126">Total steps the needle will travel through when moving from the current needle angle to a newly assigned needle angle</span></span> |
| <span data-ttu-id="7a73b-127">**gx_circular_gauge_info_animation_delay**</span><span class="sxs-lookup"><span data-stu-id="7a73b-127">**gx_circular_gauge_info_animation_delay**</span></span>       | <span data-ttu-id="7a73b-128">アニメーションのステップ間で GUIX の時計の針が動く回数</span><span class="sxs-lookup"><span data-stu-id="7a73b-128">The number of GUIX clock ticks to delay between animation steps</span></span> |
| <span data-ttu-id="7a73b-129">**gx_circular_gauge_info_needle_xpos**</span><span class="sxs-lookup"><span data-stu-id="7a73b-129">**gx_circular_gauge_info_needle_xpos**</span></span>           | <span data-ttu-id="7a73b-130">ゲージ ウィジェットの左端からゲージの針の回転中心までの距離</span><span class="sxs-lookup"><span data-stu-id="7a73b-130">The distance from the left of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="7a73b-131">**gx_circular_gauge_info_needle_ypos**</span><span class="sxs-lookup"><span data-stu-id="7a73b-131">**gx_circular_gauge_info_needle_ypos**</span></span>           | <span data-ttu-id="7a73b-132">ゲージ ウィジェットの上端からゲージの針の回転中心までの距離</span><span class="sxs-lookup"><span data-stu-id="7a73b-132">The distance from the top of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="7a73b-133">**gx_circular_gauge_info_needle_xcor**</span><span class="sxs-lookup"><span data-stu-id="7a73b-133">**gx_circular_gauge_info_needle_xcor**</span></span>           | <span data-ttu-id="7a73b-134">針の画像の左端からゲージの針の回転中心までの距離</span><span class="sxs-lookup"><span data-stu-id="7a73b-134">The distance from the left of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="7a73b-135">**gx_circular_gauge_info_needle_ycor**</span><span class="sxs-lookup"><span data-stu-id="7a73b-135">**gx_circular_gauge_info_needle_ycor**</span></span>           | <span data-ttu-id="7a73b-136">針の画像の上端からゲージの針の回転中心までの距離</span><span class="sxs-lookup"><span data-stu-id="7a73b-136">The distance from the top of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="7a73b-137">**gx_circular_gauge_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="7a73b-137">**gx_circular_gauge_info_needle_pixelmap**</span></span>       | <span data-ttu-id="7a73b-138">ゲージの針の描画に使用するピクセルマップのリソース ID。</span><span class="sxs-lookup"><span data-stu-id="7a73b-138">Resource ID of the pixelmap which will be used to draw the gauge needle.</span></span> <span data-ttu-id="7a73b-139">この画像は、ゲージ ウィジェットで必要なときに回転し、ゲージの針を必要な位置に表示します</span><span class="sxs-lookup"><span data-stu-id="7a73b-139">This image will be rotated as needed by the gauge widget to display the gauge needle in any position</span></span> |

<span data-ttu-id="7a73b-140">次の図に xpos、ypos、xcor、ycor の座標を示します:</span><span class="sxs-lookup"><span data-stu-id="7a73b-140">The diagram below illustrates the xpos, ypos, and xcor, ycor coordinates:</span></span>

![針の Y 座標と X 座標の図](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a><span data-ttu-id="7a73b-142">GX_LINE_CHART_INFO</span><span class="sxs-lookup"><span data-stu-id="7a73b-142">GX_LINE_CHART_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="7a73b-143">定義</span><span class="sxs-lookup"><span data-stu-id="7a73b-143">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="7a73b-144">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a73b-144">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="7a73b-145">**gx_line_chart_min_val**</span><span class="sxs-lookup"><span data-stu-id="7a73b-145">**gx_line_chart_min_val**</span></span>          | <span data-ttu-id="7a73b-146">データの最小値。拡大率の計算に使用します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-146">The minimum data value, which is used to calculate scaling</span></span>
| <span data-ttu-id="7a73b-147">**gx_line_chart_max_val**</span><span class="sxs-lookup"><span data-stu-id="7a73b-147">**gx_line_chart_max_val**</span></span>          | <span data-ttu-id="7a73b-148">拡大率の計算に使用されるデータの最大値。</span><span class="sxs-lookup"><span data-stu-id="7a73b-148">The maximum data value, which is used to calculate scaling</span></span> |
| <span data-ttu-id="7a73b-149">**gx_line_chart_data**</span><span class="sxs-lookup"><span data-stu-id="7a73b-149">**gx_line_chart_data**</span></span>             | <span data-ttu-id="7a73b-150">整数値の配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7a73b-150">Pointer to an array of integer values.</span></span> <span data-ttu-id="7a73b-151">これは、整数値を折れ線グラフ ウィジェットでプロットしたものです</span><span class="sxs-lookup"><span data-stu-id="7a73b-151">These are the integer values plotted by the line chart widget</span></span> |
| <span data-ttu-id="7a73b-152">**gx_line_<side>_margin**</span><span class="sxs-lookup"><span data-stu-id="7a73b-152">**gx_line_<side>_margin**</span></span>          | <span data-ttu-id="7a73b-153">グラフ ウィンドウの外側の境界と実際にグラフを描画する領域の間のオフセット。</span><span class="sxs-lookup"><span data-stu-id="7a73b-153">The offset from the chart window outer bound to the actual chart rendering area.</span></span> <span data-ttu-id="7a73b-154">グラフの軸とデータの線は、常にこの内側の境界の内部にプロットされます。この仕組みによりアプリケーションでは、グラフ ウィンドウの内側でグラフ描画領域の外側に当たる場所に、ラベルなどの情報を描画できます。</span><span class="sxs-lookup"><span data-stu-id="7a73b-154">The chart axis and data line are always plotted within this inner boundary, which allows the application to draw labels and other information inside the chart window but outside the char graphing area</span></span> |
| <span data-ttu-id="7a73b-155">**gx_line_chart_max_data_count**</span><span class="sxs-lookup"><span data-stu-id="7a73b-155">**gx_line_chart_max_data_count**</span></span>   | <span data-ttu-id="7a73b-156">表示し得るデータ値の数。</span><span class="sxs-lookup"><span data-stu-id="7a73b-156">The number of data values which may be present.</span></span> <span data-ttu-id="7a73b-157">このパラメーターは、データ値をプロットする際の x 軸拡大率または間隔を計算するのに使用します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-157">This parameter is used for calculating the x-axis scaling or interval for plotting data points.</span></span> |
| <span data-ttu-id="7a73b-158">**gx_line_active_data_count**</span><span class="sxs-lookup"><span data-stu-id="7a73b-158">**gx_line_active_data_count**</span></span>      | <span data-ttu-id="7a73b-159">データの配列の中に実際に存在するデータ値の数。</span><span class="sxs-lookup"><span data-stu-id="7a73b-159">The number of data values that actually present in the data array.</span></span> <span data-ttu-id="7a73b-160">折れ線グラフは、(たとえば) 最大 100 個の値を描画するように拡大縮小できますが、グラフを更新する際、表示されるデータ値の数がそれよりも少なくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7a73b-160">A line chart may be scaled to draw a maximum of 100 values (for example), but on any particular update a smaller number of data values may actually be present.</span></span> |
| <span data-ttu-id="7a73b-161">**gx_line_axis_line_width**</span><span class="sxs-lookup"><span data-stu-id="7a73b-161">**gx_line_axis_line_width**</span></span>        | <span data-ttu-id="7a73b-162">水平軸と垂直軸の描画に使用する線の幅</span><span class="sxs-lookup"><span data-stu-id="7a73b-162">Width of the line used to draw the horizontal and vertical axis</span></span> |
| <span data-ttu-id="7a73b-163">**gx_line_data_line_width**</span><span class="sxs-lookup"><span data-stu-id="7a73b-163">**gx_line_data_line_width**</span></span>        | <span data-ttu-id="7a73b-164">プロットされたデータの線の幅</span><span class="sxs-lookup"><span data-stu-id="7a73b-164">Width of the plotted data line</span></span> |
| <span data-ttu-id="7a73b-165">**gx_line_chart_axis_color**</span><span class="sxs-lookup"><span data-stu-id="7a73b-165">**gx_line_chart_axis_color**</span></span>       | <span data-ttu-id="7a73b-166">軸の線の描画に使用する色のリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-166">Resource ID of the color used to draw the axis lines</span></span> |
| <span data-ttu-id="7a73b-167">**gx_line_chart_line_color**</span><span class="sxs-lookup"><span data-stu-id="7a73b-167">**gx_line_chart_line_color**</span></span>       | <span data-ttu-id="7a73b-168">グラフのデータ線の描画に使用する色のリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-168">Resource ID of the color used to draw the chart data line</span></span> |

## <a name="gx_mouse_cursor_info"></a><span data-ttu-id="7a73b-169">GX_MOUSE_CURSOR_INFO</span><span class="sxs-lookup"><span data-stu-id="7a73b-169">GX_MOUSE_CURSOR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="7a73b-170">定義</span><span class="sxs-lookup"><span data-stu-id="7a73b-170">Definition</span></span>

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

### <a name="members"></a><span data-ttu-id="7a73b-171">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a73b-171">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="7a73b-172">**gx_mouse_cursor_image_id**</span><span class="sxs-lookup"><span data-stu-id="7a73b-172">**gx_mouse_cursor_image_id**</span></span>       | <span data-ttu-id="7a73b-173">マウス画像のリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-173">Resource ID of the mouse image</span></span> |
| <span data-ttu-id="7a73b-174">**gx_mouse_cursor_hotspot_x**</span><span class="sxs-lookup"><span data-stu-id="7a73b-174">**gx_mouse_cursor_hotspot_x**</span></span>      | <span data-ttu-id="7a73b-175">マウス画像の左端とマウス画像のホット スポットの間のオフセット</span><span class="sxs-lookup"><span data-stu-id="7a73b-175">The offset from the left of the mouse image to the mouse image hotspot</span></span> |
| <span data-ttu-id="7a73b-176">**gx_mouse_cursor_hotspot_y**</span><span class="sxs-lookup"><span data-stu-id="7a73b-176">**gx_mouse_cursor_hotspot_y**</span></span>      | <span data-ttu-id="7a73b-177">マウス画像の上端とマウス画像のホット スポットの間のオフセット</span><span class="sxs-lookup"><span data-stu-id="7a73b-177">The offset from the top of the mouse image to the mouse image hotspot</span></span> |

## <a name="gx_pen_configuration"></a><span data-ttu-id="7a73b-178">GX_PEN_CONFIGURATION</span><span class="sxs-lookup"><span data-stu-id="7a73b-178">GX_PEN_CONFIGURATION</span></span> 

### <a name="definition"></a><span data-ttu-id="7a73b-179">定義</span><span class="sxs-lookup"><span data-stu-id="7a73b-179">Definition</span></span>

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

### <a name="members"></a><span data-ttu-id="7a73b-180">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a73b-180">Members</span></span>

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="7a73b-181">**gx_pen_configuration_min_drag_dist**</span><span class="sxs-lookup"><span data-stu-id="7a73b-181">**gx_pen_configuration_min_drag_dist**</span></span>       | <span data-ttu-id="7a73b-182">FLICK イベントを発生させる、GUIX タイマー刻みあたりの最小ドラッグ距離。</span><span class="sxs-lookup"><span data-stu-id="7a73b-182">The minimum drag distance per GUIX timer tick to trigger an FLICK event.</span></span> <span data-ttu-id="7a73b-183">GX_FIXED_VAL_MAKE を呼び出して固定点データの値を設定します</span><span class="sxs-lookup"><span data-stu-id="7a73b-183">Call GX_FIXED_VAL_MAKE to make a fixed point data type value</span></span> |
| <span data-ttu-id="7a73b-184">**gx_pen_configuration_max_pen_speed_ticks**</span><span class="sxs-lookup"><span data-stu-id="7a73b-184">**gx_pen_configuration_max_pen_speed_ticks**</span></span> | <span data-ttu-id="7a73b-185">FLICK イベントを発生させる、GUIX タイマー刻み単位の最大ドラッグ速度</span><span class="sxs-lookup"><span data-stu-id="7a73b-185">The maximum drag speed in GUIX timer ticks to trigger an FLICK event</span></span> | 

## <a name="gx_pixelmap_slider_info"></a><span data-ttu-id="7a73b-186">GX_PIXELMAP_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="7a73b-186">GX_PIXELMAP_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="7a73b-187">定義</span><span class="sxs-lookup"><span data-stu-id="7a73b-187">Definition</span></span>

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

### <a name="members"></a><span data-ttu-id="7a73b-188">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a73b-188">Members</span></span>

|                                                       |                                          |
| ----------------------------------------------------- | ---------------------------------------- |
| <span data-ttu-id="7a73b-189">**gx_pixelmap_slider_info_lower_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="7a73b-189">**gx_pixelmap_slider_info_lower_background_pixelmap**</span></span> | <span data-ttu-id="7a73b-190">針の手前側の背景を塗りつぶすピクセルマップのリソース ID。</span><span class="sxs-lookup"><span data-stu-id="7a73b-190">Resource ID of the pixelmap for filling the background before the needle.</span></span> <span data-ttu-id="7a73b-191">手前側の背景のピクセルマップを設定していない場合は、針の手前側と奥側両方の背景を塗りつぶすのに使用します</span><span class="sxs-lookup"><span data-stu-id="7a73b-191">If upper background pixelmap is not set, it’s used for filling background both before and after the needle</span></span> |
| <span data-ttu-id="7a73b-192">**gx_pixelmap_slider_info_upper_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="7a73b-192">**gx_pixelmap_slider_info_upper_background_pixelmap**</span></span> | <span data-ttu-id="7a73b-193">針の奥側の背景を塗りつぶすピクセルマップのリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-193">Resource ID of the pixelmap for filling background after the needle</span></span> |
| <span data-ttu-id="7a73b-194">**gx_pixelmap_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="7a73b-194">**gx_pixelmap_slider_info_needle_pixelmap**</span></span>           | <span data-ttu-id="7a73b-195">針のピクセルマップのリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-195">Resource ID of the needle pixelmap</span></span> |

## <a name="gx_progress_bar_info"></a><span data-ttu-id="7a73b-196">GX_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="7a73b-196">GX_PROGRESS_BAR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="7a73b-197">**定義**</span><span class="sxs-lookup"><span data-stu-id="7a73b-197">**Definition**</span></span>

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

### <a name="members"></a><span data-ttu-id="7a73b-198">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a73b-198">Members</span></span>

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="7a73b-199">**gx_progress_bar_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="7a73b-199">**gx_progress_bar_info_min_val**</span></span>             | <span data-ttu-id="7a73b-200">最小報告値</span><span class="sxs-lookup"><span data-stu-id="7a73b-200">Minimum reported value</span></span> |
| <span data-ttu-id="7a73b-201">**gx_progress_bar_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="7a73b-201">**gx_progress_bar_info_max_val**</span></span>             | <span data-ttu-id="7a73b-202">最大報告値</span><span class="sxs-lookup"><span data-stu-id="7a73b-202">Maximum reported value</span></span> |
| <span data-ttu-id="7a73b-203">**gx_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="7a73b-203">**gx_progress_bar_info_current_val**</span></span>         | <span data-ttu-id="7a73b-204">現在の値</span><span class="sxs-lookup"><span data-stu-id="7a73b-204">Current value</span></span> |
| <span data-ttu-id="7a73b-205">**gx_progress_bar_info_font_id**</span><span class="sxs-lookup"><span data-stu-id="7a73b-205">**gx_progress_bar_info_font_id**</span></span>             | <span data-ttu-id="7a73b-206">フォントのリソース ID。テキストの値 (オプション) をプログレス バー ウィジェットに描画する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-206">Resource ID of the font, used to draw the optional text value within the progress bar widget</span></span>      |
| <span data-ttu-id="7a73b-207">**gx_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="7a73b-207">**gx_progress_bar_normal_text_color**</span></span>        | <span data-ttu-id="7a73b-208">通常の状態のテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-208">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="7a73b-209">**gx_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="7a73b-209">**gx_progress_bar_selected_text_color**</span></span>      | <span data-ttu-id="7a73b-210">ウィジェットにフォーカスしたときのテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-210">Resource ID of the text color when the widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="7a73b-211">**gx_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="7a73b-211">**gx_progress_bar_disabled_text_color**</span></span>      | <span data-ttu-id="7a73b-212">GX_STYLE_ENABLED が有効でないときのテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-212">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="7a73b-213">**gx_progress_bar_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="7a73b-213">**gx_progress_bar_fill_pixelmap**</span></span>            | <span data-ttu-id="7a73b-214">背景の塗りつぶしに使用するピクセルマップのリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-214">Resource ID of the pixelmap for background filling</span></span>|

## <a name="gx_radial_progress_bar_info"></a><span data-ttu-id="7a73b-215">GX_RADIAL_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="7a73b-215">GX_RADIAL_PROGRESS_BAR_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="7a73b-216">定義</span><span class="sxs-lookup"><span data-stu-id="7a73b-216">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="7a73b-217">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a73b-217">Members</span></span>

|                                                   |                                              |
| ------------------------------------------------- | -------------------------------------------- |
| <span data-ttu-id="7a73b-218">**gx_radial_progress_bar_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="7a73b-218">**gx_radial_progress_bar_info_xcenter**</span></span>           | <span data-ttu-id="7a73b-219">ウィジェットの x 座標上の位置</span><span class="sxs-lookup"><span data-stu-id="7a73b-219">Widget position in x coordinate</span></span> |
| <span data-ttu-id="7a73b-220">**gx_radial_progress_bar_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="7a73b-220">**gx_radial_progress_bar_info_ycenter**</span></span>           | <span data-ttu-id="7a73b-221">ウィジェットの y 座標上の位置</span><span class="sxs-lookup"><span data-stu-id="7a73b-221">Widget position in y coordinate</span></span>  |
| <span data-ttu-id="7a73b-222">**gx_radial_progress_bar_info_radius**</span><span class="sxs-lookup"><span data-stu-id="7a73b-222">**gx_radial_progress_bar_info_radius**</span></span>            | <span data-ttu-id="7a73b-223">プログレス サークルの半径</span><span class="sxs-lookup"><span data-stu-id="7a73b-223">Radius of the progress circle</span></span> |
| <span data-ttu-id="7a73b-224">**gx_radial_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="7a73b-224">**gx_radial_progress_bar_info_current_val**</span></span>       | <span data-ttu-id="7a73b-225">現在の値は、[-360, 360] の範囲で表され、アンカー位置と上半分の円弧の端点の角度差を表します。負の値を指定すると、アンカー位置から時計回りに円弧を描画します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-225">Current value, limited to the range [-360, 360], indicates the angular delta between the anchor position and the end point of the upper arc. Negative value causes the arc to be drawn in a clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="7a73b-226">正の値を指定すると、アンカー位置から反時計回りに円弧を描画します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-226">Positive value causes the arc to be drawn in a counter-clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="7a73b-227">アプリケーションは、実際に示されている値に必要な計算を施して得た角度を、プログレス バー ウィジェットに渡す必要があります</span><span class="sxs-lookup"><span data-stu-id="7a73b-227">The application must scale the real-word value being indicated to assign an angular value to the progress bar widget</span></span> |
| <span data-ttu-id="7a73b-228">**gx_radial_progress_bar_anchor_val**</span><span class="sxs-lookup"><span data-stu-id="7a73b-228">**gx_radial_progress_bar_anchor_val**</span></span>             | <span data-ttu-id="7a73b-229">プログレス サークルの上半分の開始角度。整数で角度を指定します。0° は直角で、真上を指す角度を表します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-229">Starting angle of the upper progress arc. The value is defined in terms of integer degree with 0 degree pointing to the right and 90 degree indicating straight up position.</span></span> |
| <span data-ttu-id="7a73b-230">**gx_radial_progress_bar_font_id**</span><span class="sxs-lookup"><span data-stu-id="7a73b-230">**gx_radial_progress_bar_font_id**</span></span>                | <span data-ttu-id="7a73b-231">プログレス バー ウィジェットにテキスト (オプション) を描画する際に使用するフォントのリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-231">Resource ID of the font used to draw the optional text value within the progress bar widget</span></span> |
| <span data-ttu-id="7a73b-232">**gx_radial_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="7a73b-232">**gx_radial_progress_bar_normal_text_color**</span></span>      | <span data-ttu-id="7a73b-233">通常の状態のテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-233">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="7a73b-234">**gx_radial_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="7a73b-234">**gx_radial_progress_bar_selected_text_color**</span></span>    |<span data-ttu-id="7a73b-235">ウィジェットにフォーカスしたときのテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します</span><span class="sxs-lookup"><span data-stu-id="7a73b-235">Resource ID of the text color when widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="7a73b-236">**gx_radial_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="7a73b-236">**gx_radial_progress_bar_disabled_text_color**</span></span>    | <span data-ttu-id="7a73b-237">GX_STYLE_ENABLED が有効でないときのテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-237">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="7a73b-238">**gx_radial_progress_bar_normal_brush_width**</span><span class="sxs-lookup"><span data-stu-id="7a73b-238">**gx_radial_progress_bar_normal_brush_width**</span></span>     | <span data-ttu-id="7a73b-239">プログレス サークルの下半分のゲージの幅</span><span class="sxs-lookup"><span data-stu-id="7a73b-239">Width of the lower progress circle</span></span> |
| <span data-ttu-id="7a73b-240">**gx_radial_progress_bar_selected_brush_width**</span><span class="sxs-lookup"><span data-stu-id="7a73b-240">**gx_radial_progress_bar_selected_brush_width**</span></span>   | <span data-ttu-id="7a73b-241">プログレス サークルの上半分のゲージの幅。上半分を下半分より細くも太くもでき、同じにもできます。</span><span class="sxs-lookup"><span data-stu-id="7a73b-241">Width of the upper progress arc, the upper arc may be narrower, the same as, or wider than the lower circle</span></span> |
| <span data-ttu-id="7a73b-242">**gx_radial_progress_bar_normal_brush_color**</span><span class="sxs-lookup"><span data-stu-id="7a73b-242">**gx_radial_progress_bar_normal_brush_color**</span></span>     | <span data-ttu-id="7a73b-243">プログレス サークルの下半分のゲージを塗りつぶす色のリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-243">Resource ID of the color to fill lower progress circle</span></span> |
| <span data-ttu-id="7a73b-244">**gx_radial_progress_bar_selected_brush_color**</span><span class="sxs-lookup"><span data-stu-id="7a73b-244">**gx_radial_progress_bar_selected_brush_color**</span></span>   | <span data-ttu-id="7a73b-245">プログレス サークルの上半分のゲージを塗りつぶす色のリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-245">Resource ID of the color to fill upper progress arc</span></span> |

## <a name="gx_radial_slider_info"></a><span data-ttu-id="7a73b-246">GX_RADIAL_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="7a73b-246">GX_RADIAL_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="7a73b-247">定義</span><span class="sxs-lookup"><span data-stu-id="7a73b-247">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="7a73b-248">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a73b-248">Members</span></span>

|                                               |                                                  |
| --------------------------------------------- | ------------------------------------------------ |
<span data-ttu-id="7a73b-249">**gx_radial_slider_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="7a73b-249">**gx_radial_slider_info_xcenter**</span></span>               | <span data-ttu-id="7a73b-250">スライダー ウィジェットの左端からスライダーの針の回転中心までの距離</span><span class="sxs-lookup"><span data-stu-id="7a73b-250">Distance from the left of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="7a73b-251">**gx_radial_slider_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="7a73b-251">**gx_radial_slider_info_ycenter**</span></span>             | <span data-ttu-id="7a73b-252">スライダー ウィジェットの上端からスライダーの針の回転中心までの距離</span><span class="sxs-lookup"><span data-stu-id="7a73b-252">Distance from the top of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="7a73b-253">**gx_radial_slider_info_radius**</span><span class="sxs-lookup"><span data-stu-id="7a73b-253">**gx_radial_slider_info_radius**</span></span>              | <span data-ttu-id="7a73b-254">円形スライダーの半径</span><span class="sxs-lookup"><span data-stu-id="7a73b-254">Radius of the radial slider circle</span></span> |
| <span data-ttu-id="7a73b-255">**gx_radial_slider_info_track_width**</span><span class="sxs-lookup"><span data-stu-id="7a73b-255">**gx_radial_slider_info_track_width**</span></span>         | <span data-ttu-id="7a73b-256">円形スライダーのゲージの幅</span><span class="sxs-lookup"><span data-stu-id="7a73b-256">Width of radial slider track</span></span> |
| <span data-ttu-id="7a73b-257">**gx_radial_slider_info_current_angle**</span><span class="sxs-lookup"><span data-stu-id="7a73b-257">**gx_radial_slider_info_current_angle**</span></span>       | <span data-ttu-id="7a73b-258">スライダーの現在の角度</span><span class="sxs-lookup"><span data-stu-id="7a73b-258">Current slider angle</span></span> |
| <span data-ttu-id="7a73b-259">**gx_radial_slider_info_min_angle**</span><span class="sxs-lookup"><span data-stu-id="7a73b-259">**gx_radial_slider_info_min_angle**</span></span>           | <span data-ttu-id="7a73b-260">スライダーの最小角度</span><span class="sxs-lookup"><span data-stu-id="7a73b-260">Minimum slider angle</span></span> |
| <span data-ttu-id="7a73b-261">**gx_radial_slider_info_max_angle**</span><span class="sxs-lookup"><span data-stu-id="7a73b-261">**gx_radial_slider_info_max_angle**</span></span>           | <span data-ttu-id="7a73b-262">スライダーの最大角度</span><span class="sxs-lookup"><span data-stu-id="7a73b-262">Maximum slider angle</span></span> |
| <span data-ttu-id="7a73b-263">**gx_radial_slider_info_angle_list**</span><span class="sxs-lookup"><span data-stu-id="7a73b-263">**gx_radial_slider_info_angle_list**</span></span>          | <span data-ttu-id="7a73b-264">アンカー角度を指定する、角度の値のリスト。値を指定すると、スライダーは指定したアンカー角度だけを取ります。</span><span class="sxs-lookup"><span data-stu-id="7a73b-264">Angle value list, defines anchor angles, if set, slider angle can only be one of the defined anchor angles</span></span> |
| <span data-ttu-id="7a73b-265">**gx_radial_slider_info_list_count**</span><span class="sxs-lookup"><span data-stu-id="7a73b-265">**gx_radial_slider_info_list_count**</span></span>          | <span data-ttu-id="7a73b-266">アンカー角度の数</span><span class="sxs-lookup"><span data-stu-id="7a73b-266">Number of anchor angles</span></span> |
| <span data-ttu-id="7a73b-267">**gx_radial_slider_info_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="7a73b-267">**gx_radial_slider_info_background_pixelmap**</span></span> | <span data-ttu-id="7a73b-268">背景のピクセルマップのリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-268">Resource ID of background pixelmap</span></span> |
| <span data-ttu-id="7a73b-269">**gx_radial_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="7a73b-269">**gx_radial_slider_info_needle_pixelmap**</span></span>     | <span data-ttu-id="7a73b-270">針のピクセルマップのリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-270">Resource ID of needle pixelmap</span></span> |

## <a name="gx_rectangle"></a><span data-ttu-id="7a73b-271">GX_RECTANGLE</span><span class="sxs-lookup"><span data-stu-id="7a73b-271">GX_RECTANGLE</span></span>

### <a name="definition"></a><span data-ttu-id="7a73b-272">定義</span><span class="sxs-lookup"><span data-stu-id="7a73b-272">Definition</span></span>

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

### <a name="members"></a><span data-ttu-id="7a73b-273">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a73b-273">Members</span></span>

|                                  |                         |
| -------------------------------- | ------------------------|
| <span data-ttu-id="7a73b-274">**gx_rectangle_left**</span><span class="sxs-lookup"><span data-stu-id="7a73b-274">**gx_rectangle_left**</span></span>            | <span data-ttu-id="7a73b-275">長方形の左端</span><span class="sxs-lookup"><span data-stu-id="7a73b-275">Left of the rectangle</span></span>   |  
| <span data-ttu-id="7a73b-276">**gx_rectangle_top**</span><span class="sxs-lookup"><span data-stu-id="7a73b-276">**gx_rectangle_top**</span></span>             | <span data-ttu-id="7a73b-277">長方形の上端</span><span class="sxs-lookup"><span data-stu-id="7a73b-277">Top of the rectangle</span></span>    | 
| <span data-ttu-id="7a73b-278">**gx_rectangle_right**</span><span class="sxs-lookup"><span data-stu-id="7a73b-278">**gx_rectangle_right**</span></span>           | <span data-ttu-id="7a73b-279">長方形の右端</span><span class="sxs-lookup"><span data-stu-id="7a73b-279">Right of the rectangle</span></span>  |
| <span data-ttu-id="7a73b-280">**gx_rectangle_bottom**</span><span class="sxs-lookup"><span data-stu-id="7a73b-280">**gx_rectangle_bottom**</span></span>          | <span data-ttu-id="7a73b-281">長方形の下端</span><span class="sxs-lookup"><span data-stu-id="7a73b-281">Bottom of the rectangle</span></span> |

## <a name="gx_rich_text_fonts"></a><span data-ttu-id="7a73b-282">GX_RICH_TEXT_FONTS</span><span class="sxs-lookup"><span data-stu-id="7a73b-282">GX_RICH_TEXT_FONTS</span></span> 

### <a name="definition"></a><span data-ttu-id="7a73b-283">定義</span><span class="sxs-lookup"><span data-stu-id="7a73b-283">Definition</span></span>

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

### <a name="members"></a><span data-ttu-id="7a73b-284">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a73b-284">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="7a73b-285">**gx_rich_text_fonts_normal_id**</span><span class="sxs-lookup"><span data-stu-id="7a73b-285">**gx_rich_text_fonts_normal_id**</span></span>   | <span data-ttu-id="7a73b-286">通常のフォントのリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-286">Resource ID of normal text font</span></span> |
| <span data-ttu-id="7a73b-287">**gx_rich_text_fonts_bold_id**</span><span class="sxs-lookup"><span data-stu-id="7a73b-287">**gx_rich_text_fonts_bold_id**</span></span>     | <span data-ttu-id="7a73b-288">太字のフォントのリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-288">Resource ID of bold text font</span></span> |
| <span data-ttu-id="7a73b-289">**gx_rich_text_fonts_italic_id**</span><span class="sxs-lookup"><span data-stu-id="7a73b-289">**gx_rich_text_fonts_italic_id**</span></span>   | <span data-ttu-id="7a73b-290">斜体のフォントのリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-290">Resource ID of italic text font</span></span> |
| <span data-ttu-id="7a73b-291">**gx_rich_text_fonts_bold_italic_id**</span><span class="sxs-lookup"><span data-stu-id="7a73b-291">**gx_rich_text_fonts_bold_italic_id**</span></span> | <span data-ttu-id="7a73b-292">太字の斜体のフォントのリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-292">Resource ID of bold italic text font</span></span> |

## <a name="gx_scroll_info"></a><span data-ttu-id="7a73b-293">GX_SCROLL_INFO</span><span class="sxs-lookup"><span data-stu-id="7a73b-293">GX_SCROLL_INFO</span></span> 
### <a name="definition"></a><span data-ttu-id="7a73b-294">**定義**</span><span class="sxs-lookup"><span data-stu-id="7a73b-294">**Definition**</span></span>

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

### <a name="members"></a><span data-ttu-id="7a73b-295">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a73b-295">Members</span></span>

|                         |                               |
| ----------------------- | ----------------------------- |
| <span data-ttu-id="7a73b-296">**gx_scroll_value**</span><span class="sxs-lookup"><span data-stu-id="7a73b-296">**gx_scroll_value**</span></span>     | <span data-ttu-id="7a73b-297">現在のスクロール位置</span><span class="sxs-lookup"><span data-stu-id="7a73b-297">Current scroll position</span></span>       |
| <span data-ttu-id="7a73b-298">**gx_scroll_minimum**</span><span class="sxs-lookup"><span data-stu-id="7a73b-298">**gx_scroll_minimum**</span></span>   | <span data-ttu-id="7a73b-299">最小報告位置</span><span class="sxs-lookup"><span data-stu-id="7a73b-299">Minimum reported position</span></span>     |
| <span data-ttu-id="7a73b-300">**gx_scroll_maximum**</span><span class="sxs-lookup"><span data-stu-id="7a73b-300">**gx_scroll_maximum**</span></span>   | <span data-ttu-id="7a73b-301">最大報告位置</span><span class="sxs-lookup"><span data-stu-id="7a73b-301">Maximum reported position</span></span>     |
| <span data-ttu-id="7a73b-302">**gx_scroll_visible**</span><span class="sxs-lookup"><span data-stu-id="7a73b-302">**gx_scroll_visible**</span></span>   | <span data-ttu-id="7a73b-303">親ウィンドウの表示範囲</span><span class="sxs-lookup"><span data-stu-id="7a73b-303">Parent window visible range</span></span>   |
| <span data-ttu-id="7a73b-304">**gx_scroll_increment**</span><span class="sxs-lookup"><span data-stu-id="7a73b-304">**gx_scroll_increment**</span></span> | <span data-ttu-id="7a73b-305">スクロールバーの最小移動量</span><span class="sxs-lookup"><span data-stu-id="7a73b-305">Scrollbar minimum delta value</span></span> |

## <a name="gx_scrollbar_appearance"></a><span data-ttu-id="7a73b-306">GX_SCROLLBAR_APPEARANCE</span><span class="sxs-lookup"><span data-stu-id="7a73b-306">GX_SCROLLBAR_APPEARANCE</span></span> 

### <a name="definition"></a><span data-ttu-id="7a73b-307">定義</span><span class="sxs-lookup"><span data-stu-id="7a73b-307">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="7a73b-308">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a73b-308">Members</span></span>

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="7a73b-309">**gx_scroll_width**</span><span class="sxs-lookup"><span data-stu-id="7a73b-309">**gx_scroll_width**</span></span>                      | <span data-ttu-id="7a73b-310">スクロールバー ウィジェットの幅 (ピクセル単位)</span><span class="sxs-lookup"><span data-stu-id="7a73b-310">Width of the scrollbar widget, in pixels</span></span> |
| <span data-ttu-id="7a73b-311">**gx_scroll_thumb_width**</span><span class="sxs-lookup"><span data-stu-id="7a73b-311">**gx_scroll_thumb_width**</span></span>                | <span data-ttu-id="7a73b-312">スクロールバー上をスライドするつまみの幅 (ピクセル単位)。</span><span class="sxs-lookup"><span data-stu-id="7a73b-312">Width of the thumb button which slides on the scrollbar, in pixels.</span></span> <span data-ttu-id="7a73b-313">通常この値は、スクロールバーの全体の幅よりも小さいピクセル数です</span><span class="sxs-lookup"><span data-stu-id="7a73b-313">This value is usually some number of pixels less than the total scrollbar width</span></span> |
| <span data-ttu-id="7a73b-314">**gx_scroll_thumb_travel_min**</span><span class="sxs-lookup"><span data-stu-id="7a73b-314">**gx_scroll_thumb_travel_min**</span></span>           | <span data-ttu-id="7a73b-315">スクロールバーの端とつまみの最小移動位置の間のオフセット。</span><span class="sxs-lookup"><span data-stu-id="7a73b-315">Offset from the end of scrollbar to minimum thumb button travel point.</span></span> <span data-ttu-id="7a73b-316">この制限を適用すると、つまみがスクロールバーの本当の端まで移動することを防げます</span><span class="sxs-lookup"><span data-stu-id="7a73b-316">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="7a73b-317">**gx_scroll_thumb_travel_max**</span><span class="sxs-lookup"><span data-stu-id="7a73b-317">**gx_scroll_thumb_travel_max**</span></span>           | <span data-ttu-id="7a73b-318">スクロールバーの端とつまみの最大移動位置の間のオフセット。</span><span class="sxs-lookup"><span data-stu-id="7a73b-318">Offset from the end of scrollbar to maximum thumb button travel point.</span></span> <span data-ttu-id="7a73b-319">この制限を適用すると、つまみがスクロールバーの本当の端まで移動することを防げます</span><span class="sxs-lookup"><span data-stu-id="7a73b-319">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="7a73b-320">**gx_scroll_thumb_border_style**</span><span class="sxs-lookup"><span data-stu-id="7a73b-320">**gx_scroll_thumb_border_style**</span></span>         | <span data-ttu-id="7a73b-321">つまみの境界のスタイル</span><span class="sxs-lookup"><span data-stu-id="7a73b-321">Border styles of thumb button</span></span> |
| <span data-ttu-id="7a73b-322">**gx_scroll_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="7a73b-322">**gx_scroll_fill_pixelmap**</span></span>              | <span data-ttu-id="7a73b-323">ピクセルマップ ID (オプション)。</span><span class="sxs-lookup"><span data-stu-id="7a73b-323">Optional pixelmap ID.</span></span> <span data-ttu-id="7a73b-324">このピクセルマップ ID がゼロでない場合、そのピクセルマップを使用してスクロールバーの背景を描画します</span><span class="sxs-lookup"><span data-stu-id="7a73b-324">If this pixelmap ID is not zero, the scrollbar uses this pixelmap to draw the scrollbar background</span></span> |
| <span data-ttu-id="7a73b-325">**gx_scroll_thumb_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="7a73b-325">**gx_scroll_thumb_pixelmap**</span></span>             | <span data-ttu-id="7a73b-326">ピクセルマップ ID (オプション)。</span><span class="sxs-lookup"><span data-stu-id="7a73b-326">Optional pixelmap ID.</span></span> <span data-ttu-id="7a73b-327">このピクセルマップ ID がゼロでない場合、そのピクセルマップを使用してスクロールバーのつまみを描画します</span><span class="sxs-lookup"><span data-stu-id="7a73b-327">If this pixelmap ID is not zero, the scrollbar thumb button uses this pixelmap to draw itself</span></span> |
| <span data-ttu-id="7a73b-328">**gx_scroll_up_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="7a73b-328">**gx_scroll_up_pixelmap**</span></span>                | <span data-ttu-id="7a73b-329">ピクセルマップ ID (オプション)。</span><span class="sxs-lookup"><span data-stu-id="7a73b-329">Optional pixelmap ID.</span></span> <span data-ttu-id="7a73b-330">このピクセルマップ ID がゼロでない場合、その ID を使用してスクロールバー左端/上端のボタンを描画します</span><span class="sxs-lookup"><span data-stu-id="7a73b-330">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar left/up end button</span></span> |
| <span data-ttu-id="7a73b-331">**gx_scroll_down_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="7a73b-331">**gx_scroll_down_pixelmap**</span></span>              | <span data-ttu-id="7a73b-332">ピクセルマップ ID (オプション)。</span><span class="sxs-lookup"><span data-stu-id="7a73b-332">Optional pixelmap ID.</span></span> <span data-ttu-id="7a73b-333">このピクセルマップ ID がゼロでない場合、その ID を使用してスクロールバー右端/下端のボタンを描画します</span><span class="sxs-lookup"><span data-stu-id="7a73b-333">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar right/down end button</span></span> |
| <span data-ttu-id="7a73b-334">**gx_scroll_thumb_color**</span><span class="sxs-lookup"><span data-stu-id="7a73b-334">**gx_scroll_thumb_color**</span></span>                | <span data-ttu-id="7a73b-335">つまみの塗りつぶしに使用する色のリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-335">Resource ID of color used to fill thumb button</span></span> |
| <span data-ttu-id="7a73b-336">**gx_scroll_thumb_border_color**</span><span class="sxs-lookup"><span data-stu-id="7a73b-336">**gx_scroll_thumb_border_color**</span></span>         | <span data-ttu-id="7a73b-337">つまみの境界の描画に使用する色のリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-337">Resource ID of color used to draw the border of thumb button</span></span> | 
| <span data-ttu-id="7a73b-338">**gx_scroll_button_color**</span><span class="sxs-lookup"><span data-stu-id="7a73b-338">**gx_scroll_button_color**</span></span>               | <span data-ttu-id="7a73b-339">スクロールバーの端のボタンの塗りつぶしに使用する色のリソース ID</span><span class="sxs-lookup"><span data-stu-id="7a73b-339">Resource ID of color used to fill scrollbar end buttons</span></span> |

## <a name="gx_slider_info"></a><span data-ttu-id="7a73b-340">GX_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="7a73b-340">GX_SLIDER_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="7a73b-341">定義</span><span class="sxs-lookup"><span data-stu-id="7a73b-341">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="7a73b-342">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a73b-342">Members</span></span>

|                                         |                                                        |
| --------------------------------------- | ------------------------------------------------------ |
| <span data-ttu-id="7a73b-343">**gx_slider_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="7a73b-343">**gx_slider_info_min_val**</span></span>              | <span data-ttu-id="7a73b-344">最小報告値</span><span class="sxs-lookup"><span data-stu-id="7a73b-344">Minimum reported value</span></span> |
| <span data-ttu-id="7a73b-345">**gx_slider_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="7a73b-345">**gx_slider_info_max_val**</span></span>              | <span data-ttu-id="7a73b-346">最大報告値</span><span class="sxs-lookup"><span data-stu-id="7a73b-346">Maximum reported value</span></span> |
| <span data-ttu-id="7a73b-347">**gx_slider_info_current_value**</span><span class="sxs-lookup"><span data-stu-id="7a73b-347">**gx_slider_info_current_value**</span></span>        | <span data-ttu-id="7a73b-348">現在の値</span><span class="sxs-lookup"><span data-stu-id="7a73b-348">Current value</span></span> |
| <span data-ttu-id="7a73b-349">**gx_slider_info_min_travel**</span><span class="sxs-lookup"><span data-stu-id="7a73b-349">**gx_slider_info_min_travel**</span></span>           | <span data-ttu-id="7a73b-350">針の移動限度</span><span class="sxs-lookup"><span data-stu-id="7a73b-350">Needle travel limit</span></span> |
| <span data-ttu-id="7a73b-351">**gx_slider_info_max_travel**</span><span class="sxs-lookup"><span data-stu-id="7a73b-351">**gx_slider_info_max_travel**</span></span>           | <span data-ttu-id="7a73b-352">針の移動限度</span><span class="sxs-lookup"><span data-stu-id="7a73b-352">Needle travel limit</span></span> |
| <span data-ttu-id="7a73b-353">**gx_slider_info_needle_width**</span><span class="sxs-lookup"><span data-stu-id="7a73b-353">**gx_slider_info_needle_width**</span></span>         | <span data-ttu-id="7a73b-354">針の幅 (ピクセル単位)</span><span class="sxs-lookup"><span data-stu-id="7a73b-354">Needle width in pixel</span></span> |
| <span data-ttu-id="7a73b-355">**gx_slider_info_needle_height**</span><span class="sxs-lookup"><span data-stu-id="7a73b-355">**gx_slider_info_needle_height**</span></span>        | <span data-ttu-id="7a73b-356">針の高さ (ピクセル単位)</span><span class="sxs-lookup"><span data-stu-id="7a73b-356">Needle height in pixel</span></span> |
|<span data-ttu-id="7a73b-357">**gx_slider_info_needle_inset**</span><span class="sxs-lookup"><span data-stu-id="7a73b-357">**gx_slider_info_needle_inset**</span></span>          | <span data-ttu-id="7a73b-358">針の描画位置。</span><span class="sxs-lookup"><span data-stu-id="7a73b-358">Needle draw position.</span></span> <span data-ttu-id="7a73b-359">GX_STYLE_SLIDER_VERTICAL が有効である場合、これは、針の描画開始位置とスライダー左端の間のオフセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-359">If GX_STYLE_SLIDER_VERTICAL is set, used to specify the offset from the needle draw start position to the slider left.</span></span> <span data-ttu-id="7a73b-360">そうでない場合は、針の描画開始位置とスライダー上端の間のオフセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-360">Else, used to specify the offset from the needle draw start position to the slider top.</span></span> |
| <span data-ttu-id="7a73b-361">**gx_slider_info_needle_hotspot_offset**</span><span class="sxs-lookup"><span data-stu-id="7a73b-361">**gx_slider_info_needle_hotspot_offset**</span></span> | <span data-ttu-id="7a73b-362">針の描画開始位置とスライダーのホット スポットの間のオフセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-362">Needle hotpot_offset, used to specify the offset from the needle draw start position to the slider hotspot.</span></span> |

## <a name="gx_sprite_frame"></a><span data-ttu-id="7a73b-363">GX_SPRITE_FRAME</span><span class="sxs-lookup"><span data-stu-id="7a73b-363">GX_SPRITE_FRAME</span></span>

### <a name="definition"></a><span data-ttu-id="7a73b-364">定義</span><span class="sxs-lookup"><span data-stu-id="7a73b-364">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="7a73b-365">メンバー</span><span class="sxs-lookup"><span data-stu-id="7a73b-365">Members</span></span>

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="7a73b-366">**gx_sprite_frame_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="7a73b-366">**gx_sprite_frame_pixelmap**</span></span>             | <span data-ttu-id="7a73b-367">このフレームに表示するピクセルマップのリソース ID。</span><span class="sxs-lookup"><span data-stu-id="7a73b-367">Resource ID of the pixelmap to be displayed for this frame.</span></span> <span data-ttu-id="7a73b-368">ID には 0 も指定できます。</span><span class="sxs-lookup"><span data-stu-id="7a73b-368">The ID can be 0.</span></span> |
| <span data-ttu-id="7a73b-369">**gx_sprite_frame_x_offset**</span><span class="sxs-lookup"><span data-stu-id="7a73b-369">**gx_sprite_frame_x_offset**</span></span>             | <span data-ttu-id="7a73b-370">スプライト ウィジェット左端と表示するピクセルマップの間のオフセット</span><span class="sxs-lookup"><span data-stu-id="7a73b-370">Offset from the sprite widget left to display the pixelmap</span></span> |
| <span data-ttu-id="7a73b-371">**gx_sprite_frame_y_offset**</span><span class="sxs-lookup"><span data-stu-id="7a73b-371">**gx_sprite_frame_y_offset**</span></span>             | <span data-ttu-id="7a73b-372">スプライト ウィジェット上端と表示するピクセルマップの間のオフセット</span><span class="sxs-lookup"><span data-stu-id="7a73b-372">Offset from the sprite widget top to display the pixelmap</span></span> |
| <span data-ttu-id="7a73b-373">**gx_sprite_frame_delay**</span><span class="sxs-lookup"><span data-stu-id="7a73b-373">**gx_sprite_frame_delay**</span></span>                | <span data-ttu-id="7a73b-374">スプライトのフレームを表示する間隔。GUIX タイマー刻み単位。</span><span class="sxs-lookup"><span data-stu-id="7a73b-374">Delay value, in GUIX timer ticks, after displaying this frame before advancing to the next sprite frame</span></span> |
| <span data-ttu-id="7a73b-375">**gx_sprite_frame_background_operation**</span><span class="sxs-lookup"><span data-stu-id="7a73b-375">**gx_sprite_frame_background_operation**</span></span> | <span data-ttu-id="7a73b-376">背景を消去する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-376">Define how the background should be erased.</span></span> <span data-ttu-id="7a73b-377">このフィールドで使用できる値:</span><span class="sxs-lookup"><span data-stu-id="7a73b-377">Possible values for this field are:</span></span><br /><span data-ttu-id="7a73b-378">GX_SPRITE_BACKGROUND_NO_ACTION: フレーム間の補完を行いません</span><span class="sxs-lookup"><span data-stu-id="7a73b-378">GX_SPRITE_BACKGROUND_NO_ACTION: No fill between frames</span></span><br /><span data-ttu-id="7a73b-379">GX_SPRITE_BACKGROUND_SOLID_FILL: スプライトの背景を再描画します</span><span class="sxs-lookup"><span data-stu-id="7a73b-379">GX_SPRITE_BACKGROUND_SOLID_FILL: Redraw sprite background</span></span><br /><span data-ttu-id="7a73b-380">GX_SPRITE_BACKGROUND_RESTORE: 前のピクセルマップを復元します</span><span class="sxs-lookup"><span data-stu-id="7a73b-380">GX_SPRITE_BACKGROUND_RESTORE: Restore previous pixelmap</span></span> |
| <span data-ttu-id="7a73b-381">**gx_sprite_frame_alpha**</span><span class="sxs-lookup"><span data-stu-id="7a73b-381">**gx_sprite_frame_alpha**</span></span>                | <span data-ttu-id="7a73b-382">表示するピクセルマップに追加するアルファ値。</span><span class="sxs-lookup"><span data-stu-id="7a73b-382">Alpha value to be added to the displayed pixelmap.</span></span> <span data-ttu-id="7a73b-383">値255は、追加のアルファ値を適用しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-383">The value 255 specifies that no extra alpha value should be imposed.</span></span> <span data-ttu-id="7a73b-384">ピクセルマップがアルファ チャネルを含む場合、このアルファ チャネルをフレームのアルファ値に追加します。</span><span class="sxs-lookup"><span data-stu-id="7a73b-384">If the pixelmap includes an alpha channel, this alpha channel will be added to the frame alpha value.</span></span> |
