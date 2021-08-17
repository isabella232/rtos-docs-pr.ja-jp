---
title: 付録 G - GUIX フォント構造体
description: GUIX フォント構造体について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4c7cedb49268f97f8e1fc4cd28329b0b61e697d57562865896f0502bdd1d45f1
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784191"
---
# <a name="appendix-g---guix-font-structure"></a>付録 G - GUIX フォント構造体

GUIX フォントは通常、GUIX Studio アプリケーションによって生成され、フォント グリフは GUIX ディスプレイ ドライバーによってレンダリングされます。 アプリケーション ソフトウェアで指定する必要があるのは、各テキスト表示ウィジェットで使用する必要があるフォントと色だけです。 完全を期すため、また、開発者が他のフォントの作成や GUIX フォント形式への変換を行う独自のメソッドを作成できるように、GUIX フォント データ構造体をここに記載します。

各 GUIX フォントは GX_FONT 構造体で始まります。 GX_FONT 構造体により、フォント内に含まれる文字やフォントの行の高さなど、グローバル フォント パラメーターが定義されます。 GX_FONT 構造体は、GX_GLYPH 構造体の配列を指します。 各 GX_GLYPH 構造体により、1 つの特定の文字グリフの幅、高さ、およびベースラインのオフセットが定義されます。 GX_GLYPH 構造体は、実際のグリフ ビットマップ データ (空白文字の場合は NULL) も指します。

gx_api.h に含まれる GX_FONT 構造体は、次のように宣言されます。

```c
typedef struct GX_FONT_STRUCT
{
    GX_UBYTE                     gx_font_format
    GX_UBYTE                     gx_font_prespace
    GX_UBYTE                     gx_font_postspace
    GX_UBYTE                     gx_font_line_height 
    GX_UBYTE                     gx_font_baseline
    USHORT                       gx_font_first_glyph
    USHORT                       gx_font_last_glyph 
    GX_CONST GX_GLYPH           *gx_font_glyphs
    const struct GX_FONT_STRUCT *gx_font_next_page
} GX_FONT;
```

gx_font_format フィールドにより、gx_api.h ヘッダー ファイルで定義されているように、フォントのピクセルあたりのビット数とその他のフラグが定義されます。

gx_font_prespace により、複数行テキスト表示でスキップする各テキスト行の上のピクセル間隔が定義されます。

gx_font_postspace フィールドにより、複数行テキスト表示でスキップする各テキスト行の下のピクセル間隔が定義されます。

gx_font_line_height フィールドにより、フォント内の最も高いグリフの高さが定義されます。

gx_font_baseline フィールドにより、グリフ ピクセルの一番上の行からフォント ベースラインまでの距離がピクセル単位で定義されます。

gx_font_first_glyph フィールドにより、このフォント ページに含まれる最初の Unicode 文字エンコードが定義されます。

gx_font_last_glyph フィールドにより、このフォント ページに含まれる最後の Unicode 文字エンコードが定義されます。

gx_font_glyphs ポインターは GX_GLYPH 構造体の配列を指します。 この配列のサイズは、このフォント ページに含まれる文字数と同じでなければなりません。つまり (gx_font_last_glyph – gx_font_first_glyph) + 1 です。

gx_font_next_page メンバーは、複数ページ フォントに使用されます。 複数ページ フォントは、拡張文字セットに対して、また GX_GLYPH 構造体配列のサイズを最適化するために使用されます。 フォントのすべての文字が 1 つのフォント ページ内に含まれている場合、またはこれが対象のフォントの最後のページである場合は、gx_font_next_page メンバーが GX_NULL に設定されます。

前述のように、上記の GX_FONT 構造体には、GX_GLYPHS 構造体の配列へのポインターが含まれています。 フォント ページ上の文字ごとに 1 つの GX_GLYPH 構造体が必要です。 GX_GLYPH 構造体は次のように定義されます。

```c
typedef struct GX_GLYPH_STRUCT
{
    GX_CONST GX_UBYTE *gx_glyph_map;
    GX_BYTE            gx_glyph_ascent;
    GX_BYTE            gx_glyph_descent;
    GX_BYTE            gx_glyph_advance;
    GX_BYTE            gx_glyph_leading;
    GX_UBYTE           gx_glyph_width;
    GX_UBYTE           gx_glyph_height;
} GX_GLYPH;
```

gx_glyph_map ポインターは、グリフ ビットマップを指します。 このポインターは、空白文字に対しては GX_NULL になる可能性があります。 ビットマップ データは、1 bpp、2 bpp、4 bpp、または 8 bpp アルファ値としてエンコードされます。 1 ビット データの場合、値 1 はピクセルが前景色で書き込まれることを示し、値 0 はピクセルが透明であることを示します。 8 ビット データの場合、値の範囲は 0 (完全に透明) から 255 (完全不透明) です。 すべての中間値は、アンチエイリアス フォントのブレンド値を表します。 グリフ ビットマップ データは、常に 8 bpp 未満のデータ値を使用して、形式のフル バイト アラインメントに埋め込まれます。

gx_glyph_ascent と gx_glyph_descent の値は、フォントのベースラインに対してグリフを垂直方向に配置します。

gx_glyph_width と gx_glyph_height の値により、グリフ ビットマップ データのサイズが指定されます。

gx_glyph_advance 値により、グリフを描画した後に描画位置を進めるピクセル幅が指定されます (これはグリフの幅と等しくない可能性があります)。

gx_glyph_leading 値により、グリフを描画する前に x 方向に進めるピクセルが指定されます。