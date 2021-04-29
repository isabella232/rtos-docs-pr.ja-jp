---
title: 付録 G - GUIX フォント構造体
description: GUIX フォント構造体について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b5f0232e6c21851014b85cfe7b07795062fd1e8d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812083"
---
# <a name="appendix-g---guix-font-structure"></a><span data-ttu-id="a0ae0-103">付録 G - GUIX フォント構造体</span><span class="sxs-lookup"><span data-stu-id="a0ae0-103">Appendix G - GUIX Font Structure</span></span>

<span data-ttu-id="a0ae0-104">GUIX フォントは通常、GUIX Studio アプリケーションによって生成され、フォント グリフは GUIX ディスプレイ ドライバーによってレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-104">GUIX fonts are normally produced by the GUIX Studio application, and font glyphs are rendered by the GUIX display driver.</span></span> <span data-ttu-id="a0ae0-105">アプリケーション ソフトウェアで指定する必要があるのは、各テキスト表示ウィジェットで使用する必要があるフォントと色だけです。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-105">The application software need only specify the font and colors that each text display widget should use.</span></span> <span data-ttu-id="a0ae0-106">完全を期すため、また、開発者が他のフォントの作成や GUIX フォント形式への変換を行う独自のメソッドを作成できるように、GUIX フォント データ構造体をここに記載します。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-106">The GUIX font data structures are documented here for completeness, and to enable developers to create their own methods for generating or converting other fonts into the GUIX font format.</span></span>

<span data-ttu-id="a0ae0-107">各 GUIX フォントは GX_FONT 構造体で始まります。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-107">Each GUIX font starts with a GX_FONT structure.</span></span> <span data-ttu-id="a0ae0-108">GX_FONT 構造体により、フォント内に含まれる文字やフォントの行の高さなど、グローバル フォント パラメーターが定義されます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-108">The GX_FONT structure defines global font parameters, such as the character included within the font and the line height of the font.</span></span> <span data-ttu-id="a0ae0-109">GX_FONT 構造体は、GX_GLYPH 構造体の配列を指します。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-109">The GX_FONT structure points at an array of GX_GLYPH structures.</span></span> <span data-ttu-id="a0ae0-110">各 GX_GLYPH 構造体により、1 つの特定の文字グリフの幅、高さ、およびベースラインのオフセットが定義されます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-110">Each GX_GLYPH structure defines the width, height, and baseline offset of one specific character glyph.</span></span> <span data-ttu-id="a0ae0-111">GX_GLYPH 構造体は、実際のグリフ ビットマップ データ (空白文字の場合は NULL) も指します。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-111">The GX_GLYPH structure also points to the actual glyph bitmap data (which may be NULL for whitespace characters).</span></span>

<span data-ttu-id="a0ae0-112">gx_api.h に含まれる GX_FONT 構造体は、次のように宣言されます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-112">The GX_FONT structure, contained in gx_api.h, is declared as follows:</span></span>

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

<span data-ttu-id="a0ae0-113">gx_font_format フィールドにより、gx_api.h ヘッダー ファイルで定義されているように、フォントのピクセルあたりのビット数とその他のフラグが定義されます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-113">The gx_font_format field defines the font bits-per-pixel and other flags, as defined in the gx_api.h header file.</span></span>

<span data-ttu-id="a0ae0-114">gx_font_prespace により、複数行テキスト表示でスキップする各テキスト行の上のピクセル間隔が定義されます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-114">The gx_font_prespace defines the pixel space to skip above each line of text in a multi-line text display.</span></span>

<span data-ttu-id="a0ae0-115">gx_font_postspace フィールドにより、複数行テキスト表示でスキップする各テキスト行の下のピクセル間隔が定義されます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-115">The gx_font_postspace field defines the pixel space to skip below each line of text in a multi-line text display.</span></span>

<span data-ttu-id="a0ae0-116">gx_font_line_height フィールドにより、フォント内の最も高いグリフの高さが定義されます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-116">The gx_font_line_height field defines the height of the tallest glyph in the font.</span></span>

<span data-ttu-id="a0ae0-117">gx_font_baseline フィールドにより、グリフ ピクセルの一番上の行からフォント ベースラインまでの距離がピクセル単位で定義されます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-117">The gx_font_baseline field defines the distance, in pixels, from the top row of glyph pixels to the font baseline.</span></span>

<span data-ttu-id="a0ae0-118">gx_font_first_glyph フィールドにより、このフォント ページに含まれる最初の Unicode 文字エンコードが定義されます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-118">The gx_font_first_glyph field defines the first Unicode character encoding included in this font page.</span></span>

<span data-ttu-id="a0ae0-119">gx_font_last_glyph フィールドにより、このフォント ページに含まれる最後の Unicode 文字エンコードが定義されます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-119">The gx_font_last_glyph field defines the last Unicode character encoding included in this font page.</span></span>

<span data-ttu-id="a0ae0-120">gx_font_glyphs ポインターは GX_GLYPH 構造体の配列を指します。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-120">The gx_font_glyphs pointer points to an array of GX_GLYPH structures.</span></span> <span data-ttu-id="a0ae0-121">この配列のサイズは、このフォント ページに含まれる文字数と同じでなければなりません。つまり</span><span class="sxs-lookup"><span data-stu-id="a0ae0-121">This array must be equal in size to the number of characters contained on this font page, i.e</span></span> <span data-ttu-id="a0ae0-122">(gx_font_last_glyph – gx_font_first_glyph) + 1 です。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-122">(gx_font_last_glyph – gx_font_first_glyph) + 1.</span></span>

<span data-ttu-id="a0ae0-123">gx_font_next_page メンバーは、複数ページ フォントに使用されます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-123">The gx_font_next_page member is used for multiple page fonts.</span></span> <span data-ttu-id="a0ae0-124">複数ページ フォントは、拡張文字セットに対して、また GX_GLYPH 構造体配列のサイズを最適化するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-124">Multiple page fonts are used for extended character sets and to optimize the size of the GX_GLYPH structure arrays.</span></span> <span data-ttu-id="a0ae0-125">フォントのすべての文字が 1 つのフォント ページ内に含まれている場合、またはこれが対象のフォントの最後のページである場合は、gx_font_next_page メンバーが GX_NULL に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-125">If all of the characters of the font are contained within one font page, or if this is the last page of the font in question, the gx_font_next_page member is set to GX_NULL.</span></span>

<span data-ttu-id="a0ae0-126">前述のように、上記の GX_FONT 構造体には、GX_GLYPHS 構造体の配列へのポインターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-126">As noted above, the GX_FONT structure above contains a pointer to an array of GX_GLYPHS structures.</span></span> <span data-ttu-id="a0ae0-127">フォント ページ上の文字ごとに 1 つの GX_GLYPH 構造体が必要です。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-127">There must be one GX_GLYPH structure for each character on the font page.</span></span> <span data-ttu-id="a0ae0-128">GX_GLYPH 構造体は次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-128">The GX_GLYPH structure is defined as:</span></span>

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

<span data-ttu-id="a0ae0-129">gx_glyph_map ポインターは、グリフ ビットマップを指します。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-129">The gx_glyph_map pointer points to the glyph bitmap.</span></span> <span data-ttu-id="a0ae0-130">このポインターは、空白文字に対しては GX_NULL になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-130">This pointer may be GX_NULL for whitespace characters.</span></span> <span data-ttu-id="a0ae0-131">ビットマップ データは、1 bpp、2 bpp、4 bpp、または 8 bpp アルファ値としてエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-131">The bitmap data is encoded as 1 bpp, 2 bpp, 4 bpp, or 8 bpp alpha values.</span></span> <span data-ttu-id="a0ae0-132">1 ビット データの場合、値 1 はピクセルが前景色で書き込まれることを示し、値 0 はピクセルが透明であることを示します。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-132">For 1 bit data, a value of 1 indicates that the pixel should be written in the foreground color, and a value of 0 indicates that the pixel is transparent.</span></span> <span data-ttu-id="a0ae0-133">8 ビット データの場合、値の範囲は 0 (完全に透明) から 255 (完全不透明) です。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-133">For 8 bit data, the values range from 0 (fully transparent) to 255 (fully opague).</span></span> <span data-ttu-id="a0ae0-134">すべての中間値は、アンチエイリアス フォントのブレンド値を表します。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-134">All intermediate value represent a blending value for anti-aliased fonts.</span></span> <span data-ttu-id="a0ae0-135">グリフ ビットマップ データは、常に 8 bpp 未満のデータ値を使用して、形式のフル バイト アラインメントに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-135">The glyph bitmap data is always padded to full byte alignment for formats using less than 8bpp data values.</span></span>

<span data-ttu-id="a0ae0-136">gx_glyph_ascent と gx_glyph_descent の値は、フォントのベースラインに対してグリフを垂直方向に配置します。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-136">The gx_glyph_ascent and gx_glyph_descent values position the glyph vertically with respect to the font baseline.</span></span>

<span data-ttu-id="a0ae0-137">gx_glyph_width と gx_glyph_height の値により、グリフ ビットマップ データのサイズが指定されます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-137">The gx_glyph_width and gx_glyph_height values specify the size of the glyph bitmap data.</span></span>

<span data-ttu-id="a0ae0-138">gx_glyph_advance 値により、グリフを描画した後に描画位置を進めるピクセル幅が指定されます (これはグリフの幅と等しくない可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-138">The gx_glyph_advance value specifies the pixel width to advance the drawing position after drawing the glyph (this may not be equal to the glyph width).</span></span>

<span data-ttu-id="a0ae0-139">gx_glyph_leading 値により、グリフを描画する前に x 方向に進めるピクセルが指定されます。</span><span class="sxs-lookup"><span data-stu-id="a0ae0-139">The gx_glyph_leading value specifies the pixels to advance in the x-direction prior to rendering the glyph.</span></span>