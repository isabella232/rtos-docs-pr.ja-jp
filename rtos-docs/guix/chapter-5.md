---
title: 第 5 章 - GUIX ディスプレイ ドライバー
description: GUIX ディスプレイ ドライバーでは、抽象描画キャンバスと物理ディスプレイ ハードウェアとの間のソフトウェア インターフェイスが定義されます。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 804187ce8562e274205e97448da77d29f99016072c137cb3c4f1f42dac58c432
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788543"
---
# <a name="chapter-5---guix-display-drivers"></a>第 5 章 - GUIX ディスプレイ ドライバー

GUIX ディスプレイ ドライバーでは、抽象描画キャンバスと物理ディスプレイ ハードウェアとの間のソフトウェア インターフェイスが定義されます。 GUIX ディスプレイ ドライバーは、キャンバス メモリ内のピクセル カラー情報を実際に変更する最下位レベルの描画関数を実装し、ダブルバッファリングされたシステムの物理ディスプレイ フレーム バッファーにキャンバス メモリを転送します。

GUIX ディスプレイ ドライバーは、物理ディスプレイ パラメーターと、低レベル ドライバー関数への一連の関数ポインターを含む構造体によって定義されます。 これらの間接的な関数ポインターを使用すると、抽象的なキャンバスとウィジェットの描画関数が、ハードウェアの詳細から完全に独立します。

GUIX には、サポートされている色深度と色形式ごとに、完全に機能する描画関数のセットが用意されています。 特定のハードウェア アクセラレータ機能などハードウェア固有の点を考慮せずにディスプレイ ドライバーを実装する場合は通常、これらの既定の描画関数で最終的なドライバーの実装には十分です。 これらの最も単純なドライバーの場合、ドライバー ソフトウェアに実装する必要があるのは通常、ハードウェア デバイスを構成する機能だけです。 ここでは多くの場合、さまざまなハードウェア レジスタを初期化して、LCD ディスプレイ クロック、ディスプレイ サイズなどを定義する必要があります。他のすべての関数の場合、ドライバーを実装すると、必要な色の深度と形式について、既定の関数実装への GX_DISPLAY 関数ポインターが初期化されるだけです。

カスタムのディスプレイ ドライバーを実装する場合は、最初に、サポートする色深度の既定のソフトウェア実装を使用してディスプレイ ドライバーの描画関数ポインターを初期化し、次に、それらの関数ポインターを置き換えてカスタム関数実装を呼び出すことをお勧めします (存在する場合)。 これを支援するために、サポートされている色の深度と形式ごとに既定のセットアップ機能が用意されています。 たとえば、16 ビット 5:6:5 形式の RGB ディスプレイ ドライバーを作成している場合、カスタム ドライバーは通常まず、次のようにこの色深度の汎用セットアップ ルーチンを呼び出します。

UINT my_custom_565_display_driver(GX_DISPLAY *display)

```c
{
      
      // perform standard function pointer setup
      
      _gx_display_driver_565rgb_setup(display, GX_NULL,
      
             my_buffertoggle);

}
```

上記のパラメーター my_buffer_toggle は、ディスプレイ ドライバーのバッファー トグル関数へのポインターです (ドライバーがシングル バッファーで、ハードウェア フレーム バッファーに直接描画される場合は、GX_NULL の可能性があります)。

カスタムのディスプレイ ドライバーを作成する場合は、カスタム ドライバー ソースに gx_display.h ヘッダー ファイルを含める必要があります。これは、内部で使用され、アプリケーション レベルのソフトウェアでは使用できないヘッダー ファイルです。

GUIX ディスプレイ レベルの描画関数は、**GX_DRAW_CONTEXT** 構造体へのポインターを入力として受け取ります。 **GX_DRAW_CONTEXT** 構造体は、使用されているブラシと色と共に、現在の描画操作のクリッピング座標を定義します。 各描画関数は、関数の要件ごとに固有の追加パラメーターを入力として受け取ります。

**GX_DISPLAY** ドライバーのエントリ ポイントのシグネチャは、次のように定義されます

```c
UINT <device>_graphics_driver_<format>(GX_DISPLAY *diplay)
```

この関数の名前は完全に実装に依存しますが、GUIX で提供されるドライバーの規則では、上記フィールドの<device>フィールドおよび色形式<format>でハードウェア固有のデバイス名を使用することになっています。

この関数は、入力として指定された **GX_DISPLAY** 構造体を初期化し、必要なハードウェアのセットアップを実行する必要があります。 **GX_DISPLAY** 構造体のフィールドは以下のとおりです。

| &nbsp; |
| --- | --- |
| ULONG gx_display_id <br/> これは、特定のドライバーの複数のインスタンスが作成される場合にアプリケーションによって使用されるフィールドです。 |
| CHAR *gx_display_name <br/> ドライバーを識別するために使用される省略可能な名前。 |
| GX_DISPLAY *gx_display_created_next <br/> このフィールドは GUIX によって初期化され、すべての GX_DISPLAY インスタンスの一覧を作成および管理するために使用されます。 |
| GX_DISPLAY *gx_display_created_previous <br/> このフィールドは GUIX によって初期化され、すべての GX_DISPLAY インスタンスの一覧を作成および管理するために使用されます。 |
| GX_VALUE gx_display_color_format <br/> このフィールドには、このドライバーでサポートされているグラフィックス データ形式が反映されている必要があります。 色形式の種類は gx_api.h ヘッダー ファイルで定義されています。 |
| GX_VALUE gx_display_width <br/> このフィールドは、ディスプレイの物理的な幅をピクセル単位で保持するように初期化する必要があります。 |
| GX_VALUE gx_display_height <br/> このフィールドは、ディスプレイの物理的な高さをピクセル単位で保持するように初期化する必要があります。 |
| GX_COLOR *gx_display_color_table <br/> これは、色 Id の値を色形式に固有の色の値に変換するために使用されるテーブルへのポインターです。 |
| GX_PIXELMAP *gx_display_pixelmap_table <br/> これは、このディスプレイのアクティブなピクセル マップ テーブルへのポインターです。 |
| GX_FONT *gx_display_font_table <br/> これは、このディスプレイのアクティブなフォント テーブルへのポインターです。 |
| GX_COLOR *gx_display_palette <br/> パレット モード ドライバーの場合、これはアクティブなカラー パレットへのポインターです。 カラー パレットを使用しないドライバーの場合、このポインターは GX_NULL です。 |
| UINT gx_display_pixelmap_table_size <br/> アクティブなピクセル マップ テーブル内のエントリの数。 |
| UINT gx_display_font_table_size <br/> アクティブなフォント テーブル内のエントリの数。 |
| UINT gx_display_palette_size <br/> カラー パレットのエントリ数 (存在する場合)。 |
| ULONG gx_display_handle <br/> ディスプレイを指定する一意の識別子、すなわち *ハンドル*。
| UINT gx_display_driver_ready <br/> このフィールドは、ドライバーの操作準備が整ったときに GUIX に通知するために使用されます。 場合によっては、ドライバーに複数レベルの初期化と構成が必要になることがあります。その間、GUIX はドライバーを使用しないようにする必要があります。 ドライバーが描画要求を処理できるようになったら、このフラグを 1 に設定する必要があります。 |
| VOID *gx_display_driver_data <br/> このフィールドは、ドライバー実装によって使用されます。 GX_DISPLAY 構造体で使用できない追加情報をドライバーが作成して参照する必要がある場合、ドライバーは、この構造体のフィールドを使用して領域を割り当て、この追加データをポイントする必要があります。 ドライバー固有の追加データの例としては、ドライバーによって使用されている DMA チャンネルや、ディスプレイ フレーム バッファーが接続されている SPI チャンネルなどがあります。 |
| VOID (*gx_display_driver_drawing_initiate)(struct GX_DISPLAY_STRUCT *display, struct GX_CANVAS_STRUCT *canvas) <br/> これは関数ポインターです。 NULL でない場合は、gx_canvas_drawing_initiate 関数によって呼び出されます。 グラフィックス アクセラレータまたはハードウェア グラフィックス ディスプレイのリストを使用するディスプレイ ドライバーの場合、この関数を使用して新しいディスプレイ リストを開始することができます。 この関数ポインターは NULL をとることができます。 |
| VOID (*gx_display_driver_palette_set)(struct GX_DISPLAY_STRUCT *display, GX_COLOR *palette, INT count) <br/> これは、カラー パレットをインストールする関数へのポインターです。 ドライバーがパレット (カラー ルックアップ テーブル、すなわち CLUT とも呼ばれます) モードで動作する場合を除き、この関数は NULL になります。 |
| VOID (*gx_display_driver_simple_line_draw)(GX_DRAW_CONTECT *context, INT x1, INTy1, INT x2, INT y2) <br/> これは、汎用の線描画を実装する関数へのポインターであり、アンチエイリアシングは処理されません。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_simple_wide_line_draw)(GX_DRAW_CONTECT *context, INT x1, INTy1, INT x2, INT y2) <br/> これは、汎用のワイド線描画を実装する関数へのポインターであり、アンチエイリアシングは処理されません。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_anti_aliased_line_draw)(GX_DRAW_CONTECT *context, INT x1, INTy1, INT x2, INT y2) <br/> これは、汎用のアンチエイリアス線描画を実装する関数へのポインターです。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_anti_aliased_wide_line_draw)(GX_DRAW_CONTECT *context, INT x1, INTy1, INT x2, INT y2) <br/> これは、一般的なアンチエイリアス ワイド線描画を実装する関数へのポインターです。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_horizonal_line_draw)(GX_DRAW_CONTECT *context, INT x1, INT x2, INT y) <br/> これは、水平線描画の特殊なケースを実装する関数へのポインターです。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_horizonal_pixelmap_line_draw)(GX_DRAW_CONTECT *context, INT x1, INT x2, INT y, GX_PIXELMAP *map) <br/> これは、ピクセル マップ上の 1 行の描画を実装する関数へのポインターです。 この関数は、内部的にパターン塗りつぶし図形に使用されます。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_vertical_line_draw)(GX_DRAW_CONTECT *context, INT y1, INT y2, INT x) <br/> これは、水平線描画の特殊なケースを実装する関数へのポインターです。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_horizonal_pattern_line_draw)(GX_DRAW_CONTECT *context, INT x1, INT x2, INT y) <br/> これは、水平パターン線描画を実装する関数へのポインターです。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_vertical_pattern_line_draw)(GX_DRAW_CONTECT *context, INT y1, INT y2, INT x) <br/> これは、垂直パターン線描画を実装する関数へのポインターです。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_canvas_copy)(struct GX_CANVAS_STRUCT *source, struct GX_CANVAS_STRUCT *dest) <br/> これは、キャンバス データを 1 つのキャンバスから別のキャンバスにコピーする関数へのポインターです。 コピー領域の定義には、ソース キャンバス無効の四角形が使用されます。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_canvas_blend)(struct GX_CANVAS_STRUCT *source, struct GX_CANVAS_STRUCT *dest) <br/> これは、ソース キャンバスのキャンバス データを変換先キャンバスの既存データとアルファブレンドする関数へのポインターです。 ソース キャンバス無効の四角形は、ブレンド領域の定義に使用されます。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_pixelmap_blend)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp, GX_UBYTE alpha) <br/> これは、描画コンテキストによって定義されているバックグラウンド キャンバス上のピクセル マップをブレンドする関数へのポインターです。 指定されるアルファ値は、ピクセル マップ データに含まれるアルファ チャネルに追加される場合があります。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_pixelmap_draw)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp) <br/> これは、描画コンテキストによって定義されているキャンバスにピクセル マップを描画する関数へのポインターです。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_jpeg_draw)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp) <br/> これは、jpg イメージをデコードしてキャンバスに直接的にレンダリングする関数へのポインターです。 この関数は、GX_SOFTWARE_DECODER_SUPPORT が定義されている場合にのみ提供されます。 この関数ポインターは NULL になります。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_png_draw)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp) <br/> これは、png イメージをデコードしてキャンバスに直接レンダリングする関数へのポインターです。 この関数は、GX_SOFTWARE_DECODER_SUPPORT が定義されている場合にのみ提供されます。 この関数ポインターは NULL になります。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_pixelmap_rotate)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp INT angle, INT rot_cx, INT rot_cy) <br/> これは、ピクセル マップを回転させて、その結果をキャンバスに直接レンダリングする関数へのポインターです。 この関数は、サポートされている各色深度と色形式に対して、この関数の APIDefault 実装の gx_canvas_pixelmap_rotate によって呼び出されます。 |
| VOID *gx_display_driver_pixel_write)(GX_DRAW_CONTEXT *context, INT x, INT y, GX_COLOR color) <br/> これは、キャンバス メモリに 1 ピクセルを書き込む関数へのポインターです。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 <br/>
| VOID *gx_display_driver_block_move)(GX_DRAW_CONTEXT *context,GX_RECTANGLE *block, INT xshift, INT yshift) <br/> これは、キャンバス内の 1 ブロック分のピクセルを移動またはシフトする関数へのポインターです。 この関数は、主にウィンドウの内容をすばやくスクロールするために使用されます。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_pixel_blend)(GX_DRAW_CONTEXT *context, INT x, INT y, GX_COLOR color, GX_UBYTE alpha) <br/> This function is used to alpha-blend the incoming pixel color value with the existing color value in the canvas memory at position x,y. サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| GX_COLOR (*gx_display_driver_native_color_get)(GX_COLOR rawcolor) <br/> この関数は、GUIX で内部的に使用される 32 ビットの A:R:G:B の色形式を、キャンバスとディスプレイのネイティブ色形式に変換します。 ディスプレイ ドライバーが低い色深度で実行されている場合、色情報が失われることがあります。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| USHORT (*gx_display_driver_row_pitch_get)(USHORT width) <br/> 要求されたキャンバス幅を指定して、1 行分のグラフィックス データのバイト数、すなわちストライドを返します。 この関数は、キャンバスの作成に必要なメモリ領域のサイズを計算するために使用されます。 ハードウェア スキャンの行アラインメント制約により、行のピッチと幅が常に同じであるとは限りません。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_buffer_toggle)(struct GX_CANVAS_STRUCT *canvas, GX_RECTANGLE *dirty_area) <br/> これは、ダブルバッファリングされたメモリ システムの動作フレーム バッファーと可視フレーム バッファーを切り替える関数へのポインターです。 この関数は、最初に新しいフレーム バッファーの使用を開始するようハードウェアに指示し、次に、新しい可視バッファーの変更部分をコンパニオン バッファーにコピーして、2 つのバッファーが同期されていることを確認する必要があります。 | 
| VOID (*gx_display_driver_polygon_draw)(GX_DRAW_CONTEXT *context, INT num_points, GX_POINT *vertices <br/> 多角形を描画する関数へのポインター。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_polygon_fill)(GX_DRAW_CONTEXT *context, INT num_points, GX_POINT *vertices <br/> 塗りつぶされた多角形を描画する関数へのポインター。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_circle_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> 円を描画する関数へのポインター。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_anti_aliased_circle_draw) (GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> アンチエイリアシングされた円を描画する関数へのポインター。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_wide_circle_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> 太い輪郭の円を描画する関数へのポインター。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_wide_anti_aliased_circle_draw) (GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> アンチエイリアシングされた太い輪郭の円を描画する関数へのポインター。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_circle_fill)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> 塗りつぶされた円を描画する関数へのポインター。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_arc_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> 円弧を描画する関数へのポインター。サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_anti_aliased_arc_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INTend_angle) <br/> アンチエイリアシングされた円弧を描画する関数へのポインター。サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_wide_arc_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> 太い輪郭の円弧を描画する関数へのポインター。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_anti_aliased_wide_arc_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INTend_angle) <br/> アンチエイリアシングされた円弧を描画する関数へのポインター。サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_arc_fill)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> 塗りつぶされた円弧を描画する関数へのポインター。サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_pie_fill)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> 塗りつぶされた円グラフを描画する関数へのポインター。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_ellipse_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> 楕円を描画する関数へのポインター。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_anti_aliased_ellipse_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> 楕円を描画する関数へのポインター。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_wide_ellipse_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> 太い輪郭の楕円を描画する関数へのポインター。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_anti_aliased_wide_ellipse_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> 太い輪郭の楕円を描画する関数へのポインター。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_ellipse_fill)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> 塗りつぶされた楕円を描画する関数へのポインター。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_8bit_glyph_draw)(GX_DRAW_CONTEXT *context, GX_RECTANGLE *draw_area, GX_POINT *map_offset, constGX_GLYPH *glyph) <br/> 現在の描画コンテキストのブラシを使用して、キャンバスに 8 ビットのエイリアス テキスト グリフを描画する関数へのポインター。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_4bit_glyph_draw)(GX_DRAW_CONTEXT *context, GX_RECTANGLE *draw_area, GX_POINT *map_offset, const GX_GLYPH *glyph) <br/> 現在の描画コンテキストのブラシを使用して、キャンバスに 4 ビットのエイリアス テキスト グリフを描画する関数へのポインター。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |
| VOID (*gx_display_driver_1bit_glyph_draw)(GX_DRAW_CONTEXT *context, GX_RECTANGLE *draw_area, GX_POINT *map_offset, const GX_GLYPH *glyph) <br/> 現在の描画コンテキストのブラシを使用して、キャンバスに 1 ビットのモノクロ テキスト グリフを描画する関数へのポインター。 サポートされている色深度と色形式ごとに、この関数の既定の実装が用意されています。 |


