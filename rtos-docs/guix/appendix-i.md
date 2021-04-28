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
# <a name="appendix-i---guix-information-structures"></a>別表 I - GUIX 情報構造体 

## <a name="gx_bidi_text_info"></a>GX_BIDI_TEXT_INFO 

### <a name="definition"></a>定義

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```

### <a name="members"></a>メンバー

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_bidi_text_info_text**               | 並べ替えを行うテキスト |
| **gx_bidi_text_info_font**               | テキストの表示に使用するフォント。改行が必要ない場合は GX_NULL に設定します。 |
| **gx_bidi_text_info_display_width**      | 表示に使用できる幅。改行が必要ない場合は -1 に設定します。 |

## <a name="gx_bidi_resolved_text_info"></a>GX_BIDI_RESOLVED_TEXT_INFO 

### <a name="definition"></a>定義

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

### <a name="members"></a>メンバー

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_bidi_resolved_text_info_text**             | 並べ替えた bidi テキストの配列へのポインター |
| **gx_bidi_resolved_text_info_total_lines**      | 処理済み bidi テキストの 1 段落の合計行数 |
| **gx_bidi_resolved_text_info_next**             | 次の段落の処理済み bidi テキストの情報 |

## <a name="gx_circular_gauge_info"></a>GX_CIRCULAR_GAUGE_INFO

### <a name="definition"></a>定義

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
### <a name="members"></a>メンバー

|                                                  |                                              |
| ------------------------------------------------ | -------------------------------------------- |
| **gx_circular_gauge_info_animation_steps**       | 現在の角度から新たに割り当てられる角度まで針が回るときに経る合計ステップ数 |
| **gx_circular_gauge_info_animation_delay**       | アニメーションのステップ間で GUIX の時計の針が動く回数 |
| **gx_circular_gauge_info_needle_xpos**           | ゲージ ウィジェットの左端からゲージの針の回転中心までの距離 |
| **gx_circular_gauge_info_needle_ypos**           | ゲージ ウィジェットの上端からゲージの針の回転中心までの距離 |
| **gx_circular_gauge_info_needle_xcor**           | 針の画像の左端からゲージの針の回転中心までの距離 |
| **gx_circular_gauge_info_needle_ycor**           | 針の画像の上端からゲージの針の回転中心までの距離 |
| **gx_circular_gauge_info_needle_pixelmap**       | ゲージの針の描画に使用するピクセルマップのリソース ID。 この画像は、ゲージ ウィジェットで必要なときに回転し、ゲージの針を必要な位置に表示します |

次の図に xpos、ypos、xcor、ycor の座標を示します:

![針の Y 座標と X 座標の図](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a>GX_LINE_CHART_INFO

### <a name="definition"></a>定義

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

### <a name="members"></a>メンバー

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_line_chart_min_val**          | データの最小値。拡大率の計算に使用します。
| **gx_line_chart_max_val**          | 拡大率の計算に使用されるデータの最大値。 |
| **gx_line_chart_data**             | 整数値の配列へのポインター。 これは、整数値を折れ線グラフ ウィジェットでプロットしたものです |
| **gx_line_<side>_margin**          | グラフ ウィンドウの外側の境界と実際にグラフを描画する領域の間のオフセット。 グラフの軸とデータの線は、常にこの内側の境界の内部にプロットされます。この仕組みによりアプリケーションでは、グラフ ウィンドウの内側でグラフ描画領域の外側に当たる場所に、ラベルなどの情報を描画できます。 |
| **gx_line_chart_max_data_count**   | 表示し得るデータ値の数。 このパラメーターは、データ値をプロットする際の x 軸拡大率または間隔を計算するのに使用します。 |
| **gx_line_active_data_count**      | データの配列の中に実際に存在するデータ値の数。 折れ線グラフは、(たとえば) 最大 100 個の値を描画するように拡大縮小できますが、グラフを更新する際、表示されるデータ値の数がそれよりも少なくなる場合があります。 |
| **gx_line_axis_line_width**        | 水平軸と垂直軸の描画に使用する線の幅 |
| **gx_line_data_line_width**        | プロットされたデータの線の幅 |
| **gx_line_chart_axis_color**       | 軸の線の描画に使用する色のリソース ID |
| **gx_line_chart_line_color**       | グラフのデータ線の描画に使用する色のリソース ID |

## <a name="gx_mouse_cursor_info"></a>GX_MOUSE_CURSOR_INFO 

### <a name="definition"></a>定義

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

### <a name="members"></a>メンバー

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_mouse_cursor_image_id**       | マウス画像のリソース ID |
| **gx_mouse_cursor_hotspot_x**      | マウス画像の左端とマウス画像のホット スポットの間のオフセット |
| **gx_mouse_cursor_hotspot_y**      | マウス画像の上端とマウス画像のホット スポットの間のオフセット |

## <a name="gx_pen_configuration"></a>GX_PEN_CONFIGURATION 

### <a name="definition"></a>定義

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

### <a name="members"></a>メンバー

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| **gx_pen_configuration_min_drag_dist**       | FLICK イベントを発生させる、GUIX タイマー刻みあたりの最小ドラッグ距離。 GX_FIXED_VAL_MAKE を呼び出して固定点データの値を設定します |
| **gx_pen_configuration_max_pen_speed_ticks** | FLICK イベントを発生させる、GUIX タイマー刻み単位の最大ドラッグ速度 | 

## <a name="gx_pixelmap_slider_info"></a>GX_PIXELMAP_SLIDER_INFO 

### <a name="definition"></a>定義

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

### <a name="members"></a>メンバー

|                                                       |                                          |
| ----------------------------------------------------- | ---------------------------------------- |
| **gx_pixelmap_slider_info_lower_background_pixelmap** | 針の手前側の背景を塗りつぶすピクセルマップのリソース ID。 手前側の背景のピクセルマップを設定していない場合は、針の手前側と奥側両方の背景を塗りつぶすのに使用します |
| **gx_pixelmap_slider_info_upper_background_pixelmap** | 針の奥側の背景を塗りつぶすピクセルマップのリソース ID |
| **gx_pixelmap_slider_info_needle_pixelmap**           | 針のピクセルマップのリソース ID |

## <a name="gx_progress_bar_info"></a>GX_PROGRESS_BAR_INFO 

### <a name="definition"></a>**定義**

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

### <a name="members"></a>メンバー

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| **gx_progress_bar_info_min_val**             | 最小報告値 |
| **gx_progress_bar_info_max_val**             | 最大報告値 |
| **gx_progress_bar_info_current_val**         | 現在の値 |
| **gx_progress_bar_info_font_id**             | フォントのリソース ID。テキストの値 (オプション) をプログレス バー ウィジェットに描画する際に使用します。      |
| **gx_progress_bar_normal_text_color**        | 通常の状態のテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します。 |
| **gx_progress_bar_selected_text_color**      | ウィジェットにフォーカスしたときのテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します。 |
| **gx_progress_bar_disabled_text_color**      | GX_STYLE_ENABLED が有効でないときのテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します。 |
| **gx_progress_bar_fill_pixelmap**            | 背景の塗りつぶしに使用するピクセルマップのリソース ID|

## <a name="gx_radial_progress_bar_info"></a>GX_RADIAL_PROGRESS_BAR_INFO

### <a name="definition"></a>定義

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

### <a name="members"></a>メンバー

|                                                   |                                              |
| ------------------------------------------------- | -------------------------------------------- |
| **gx_radial_progress_bar_info_xcenter**           | ウィジェットの x 座標上の位置 |
| **gx_radial_progress_bar_info_ycenter**           | ウィジェットの y 座標上の位置  |
| **gx_radial_progress_bar_info_radius**            | プログレス サークルの半径 |
| **gx_radial_progress_bar_info_current_val**       | 現在の値は、[-360, 360] の範囲で表され、アンカー位置と上半分の円弧の端点の角度差を表します。負の値を指定すると、アンカー位置から時計回りに円弧を描画します。 正の値を指定すると、アンカー位置から反時計回りに円弧を描画します。 アプリケーションは、実際に示されている値に必要な計算を施して得た角度を、プログレス バー ウィジェットに渡す必要があります |
| **gx_radial_progress_bar_anchor_val**             | プログレス サークルの上半分の開始角度。整数で角度を指定します。0° は直角で、真上を指す角度を表します。 |
| **gx_radial_progress_bar_font_id**                | プログレス バー ウィジェットにテキスト (オプション) を描画する際に使用するフォントのリソース ID |
| **gx_radial_progress_bar_normal_text_color**      | 通常の状態のテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します。 |
| **gx_radial_progress_bar_selected_text_color**    |ウィジェットにフォーカスしたときのテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します |
| **gx_radial_progress_bar_disabled_text_color**    | GX_STYLE_ENABLED が有効でないときのテキストの色のリソース ID。プログレス バー ウィジェットに描画するテキスト (オプション) を指定する際に使用します。 |
| **gx_radial_progress_bar_normal_brush_width**     | プログレス サークルの下半分のゲージの幅 |
| **gx_radial_progress_bar_selected_brush_width**   | プログレス サークルの上半分のゲージの幅。上半分を下半分より細くも太くもでき、同じにもできます。 |
| **gx_radial_progress_bar_normal_brush_color**     | プログレス サークルの下半分のゲージを塗りつぶす色のリソース ID |
| **gx_radial_progress_bar_selected_brush_color**   | プログレス サークルの上半分のゲージを塗りつぶす色のリソース ID |

## <a name="gx_radial_slider_info"></a>GX_RADIAL_SLIDER_INFO 

### <a name="definition"></a>定義

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

### <a name="members"></a>メンバー

|                                               |                                                  |
| --------------------------------------------- | ------------------------------------------------ |
**gx_radial_slider_info_xcenter**               | スライダー ウィジェットの左端からスライダーの針の回転中心までの距離 |
| **gx_radial_slider_info_ycenter**             | スライダー ウィジェットの上端からスライダーの針の回転中心までの距離 |
| **gx_radial_slider_info_radius**              | 円形スライダーの半径 |
| **gx_radial_slider_info_track_width**         | 円形スライダーのゲージの幅 |
| **gx_radial_slider_info_current_angle**       | スライダーの現在の角度 |
| **gx_radial_slider_info_min_angle**           | スライダーの最小角度 |
| **gx_radial_slider_info_max_angle**           | スライダーの最大角度 |
| **gx_radial_slider_info_angle_list**          | アンカー角度を指定する、角度の値のリスト。値を指定すると、スライダーは指定したアンカー角度だけを取ります。 |
| **gx_radial_slider_info_list_count**          | アンカー角度の数 |
| **gx_radial_slider_info_background_pixelmap** | 背景のピクセルマップのリソース ID |
| **gx_radial_slider_info_needle_pixelmap**     | 針のピクセルマップのリソース ID |

## <a name="gx_rectangle"></a>GX_RECTANGLE

### <a name="definition"></a>定義

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

### <a name="members"></a>メンバー

|                                  |                         |
| -------------------------------- | ------------------------|
| **gx_rectangle_left**            | 長方形の左端   |  
| **gx_rectangle_top**             | 長方形の上端    | 
| **gx_rectangle_right**           | 長方形の右端  |
| **gx_rectangle_bottom**          | 長方形の下端 |

## <a name="gx_rich_text_fonts"></a>GX_RICH_TEXT_FONTS 

### <a name="definition"></a>定義

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

### <a name="members"></a>メンバー

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_rich_text_fonts_normal_id**   | 通常のフォントのリソース ID |
| **gx_rich_text_fonts_bold_id**     | 太字のフォントのリソース ID |
| **gx_rich_text_fonts_italic_id**   | 斜体のフォントのリソース ID |
| **gx_rich_text_fonts_bold_italic_id** | 太字の斜体のフォントのリソース ID |

## <a name="gx_scroll_info"></a>GX_SCROLL_INFO 
### <a name="definition"></a>**定義**

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

### <a name="members"></a>メンバー

|                         |                               |
| ----------------------- | ----------------------------- |
| **gx_scroll_value**     | 現在のスクロール位置       |
| **gx_scroll_minimum**   | 最小報告位置     |
| **gx_scroll_maximum**   | 最大報告位置     |
| **gx_scroll_visible**   | 親ウィンドウの表示範囲   |
| **gx_scroll_increment** | スクロールバーの最小移動量 |

## <a name="gx_scrollbar_appearance"></a>GX_SCROLLBAR_APPEARANCE 

### <a name="definition"></a>定義

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

### <a name="members"></a>メンバー

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| **gx_scroll_width**                      | スクロールバー ウィジェットの幅 (ピクセル単位) |
| **gx_scroll_thumb_width**                | スクロールバー上をスライドするつまみの幅 (ピクセル単位)。 通常この値は、スクロールバーの全体の幅よりも小さいピクセル数です |
| **gx_scroll_thumb_travel_min**           | スクロールバーの端とつまみの最小移動位置の間のオフセット。 この制限を適用すると、つまみがスクロールバーの本当の端まで移動することを防げます |
| **gx_scroll_thumb_travel_max**           | スクロールバーの端とつまみの最大移動位置の間のオフセット。 この制限を適用すると、つまみがスクロールバーの本当の端まで移動することを防げます |
| **gx_scroll_thumb_border_style**         | つまみの境界のスタイル |
| **gx_scroll_fill_pixelmap**              | ピクセルマップ ID (オプション)。 このピクセルマップ ID がゼロでない場合、そのピクセルマップを使用してスクロールバーの背景を描画します |
| **gx_scroll_thumb_pixelmap**             | ピクセルマップ ID (オプション)。 このピクセルマップ ID がゼロでない場合、そのピクセルマップを使用してスクロールバーのつまみを描画します |
| **gx_scroll_up_pixelmap**                | ピクセルマップ ID (オプション)。 このピクセルマップ ID がゼロでない場合、その ID を使用してスクロールバー左端/上端のボタンを描画します |
| **gx_scroll_down_pixelmap**              | ピクセルマップ ID (オプション)。 このピクセルマップ ID がゼロでない場合、その ID を使用してスクロールバー右端/下端のボタンを描画します |
| **gx_scroll_thumb_color**                | つまみの塗りつぶしに使用する色のリソース ID |
| **gx_scroll_thumb_border_color**         | つまみの境界の描画に使用する色のリソース ID | 
| **gx_scroll_button_color**               | スクロールバーの端のボタンの塗りつぶしに使用する色のリソース ID |

## <a name="gx_slider_info"></a>GX_SLIDER_INFO

### <a name="definition"></a>定義

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

### <a name="members"></a>メンバー

|                                         |                                                        |
| --------------------------------------- | ------------------------------------------------------ |
| **gx_slider_info_min_val**              | 最小報告値 |
| **gx_slider_info_max_val**              | 最大報告値 |
| **gx_slider_info_current_value**        | 現在の値 |
| **gx_slider_info_min_travel**           | 針の移動限度 |
| **gx_slider_info_max_travel**           | 針の移動限度 |
| **gx_slider_info_needle_width**         | 針の幅 (ピクセル単位) |
| **gx_slider_info_needle_height**        | 針の高さ (ピクセル単位) |
|**gx_slider_info_needle_inset**          | 針の描画位置。 GX_STYLE_SLIDER_VERTICAL が有効である場合、これは、針の描画開始位置とスライダー左端の間のオフセットを指定します。 そうでない場合は、針の描画開始位置とスライダー上端の間のオフセットを指定します。 |
| **gx_slider_info_needle_hotspot_offset** | 針の描画開始位置とスライダーのホット スポットの間のオフセットを指定します。 |

## <a name="gx_sprite_frame"></a>GX_SPRITE_FRAME

### <a name="definition"></a>定義

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

### <a name="members"></a>メンバー

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| **gx_sprite_frame_pixelmap**             | このフレームに表示するピクセルマップのリソース ID。 ID には 0 も指定できます。 |
| **gx_sprite_frame_x_offset**             | スプライト ウィジェット左端と表示するピクセルマップの間のオフセット |
| **gx_sprite_frame_y_offset**             | スプライト ウィジェット上端と表示するピクセルマップの間のオフセット |
| **gx_sprite_frame_delay**                | スプライトのフレームを表示する間隔。GUIX タイマー刻み単位。 |
| **gx_sprite_frame_background_operation** | 背景を消去する方法を指定します。 このフィールドで使用できる値:<br />GX_SPRITE_BACKGROUND_NO_ACTION: フレーム間の補完を行いません<br />GX_SPRITE_BACKGROUND_SOLID_FILL: スプライトの背景を再描画します<br />GX_SPRITE_BACKGROUND_RESTORE: 前のピクセルマップを復元します |
| **gx_sprite_frame_alpha**                | 表示するピクセルマップに追加するアルファ値。 値255は、追加のアルファ値を適用しないことを指定します。 ピクセルマップがアルファ チャネルを含む場合、このアルファ チャネルをフレームのアルファ値に追加します。 |
