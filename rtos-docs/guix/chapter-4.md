---
title: 第 4 章 - GUIX サービスの説明
description: この章では、すべての GUIX サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7c89014c571b2b59279487cd24d5ec9e36019ed4c3ec2b6470b80e150214ebf3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116786825"
---
# <a name="chapter-4---description-of-guix-services"></a>第 4 章 - GUIX サービスの説明

この章では、すべての GUIX サービス (以下に記載) をアルファベット順に説明します。  

次の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にする際に使用される **GX_DISABLE_ERROR_CHECKING** 定義の影響を受けません。一方、太字以外の値は完全に無効になっています。 

| **GUIX サービス**                      | **説明**                                                                             |
| -------------------------------------- | -------------------------------------------------------------------------------------------- |
| gx_accordion_menu_create            | アコーディオン メニューを作成します                                                                        |
| gx_accordion_menu_draw              | アコーディオン メニューを描画します                                                                          |
| gx_accordion_menu_event_process    | アコーディオン メニュー イベントを処理します                                                                 |
| gx_accordion_menu_position          | メニュー項目を配置します                                                                          |
| gx_animation_canvas_define          | 後続のアニメーションに使用されるキャンバスのアニメーション コントローラーにメモリを提供します。 |
| gx_animation_create                  | アニメーション コントローラーを作成します                                                               |
| gx_animation_delete                  | 1 つ以上のアニメーション コントローラーを削除します |
| gx_animation_drag_disable           | 画面のドラッグ アニメーションのフックを無効にします                                                           |
| gx_animation_drag_enable            | 画面のドラッグ アニメーションのフックを有効にします                                                            |
| gx_animation_landing_speed_set     | 画面のドラッグ アニメーションのランディング速度を設定します                                                  |
| gx_animation_start                   | アニメーション シーケンスを開始します                                                               |
| gx_animation_stop                    | アニメーション シーケンスを停止します                                                                |
| gx_binres_language_count_get      |  バイナリ リソース ファイルから言語の数を取得します                                          |
| gx_binres_language_info_load      |  バイナリ リソース ファイルから言語の名前とサイズの情報を読み取ります。                           |
| gx_binres_language_table_load      | (非推奨) バイナリ リソース データ バッファーから言語テーブルを読み込みます                          |
| gx_binres_language_table_load_ext | バイナリ リソース データ バッファーから言語テーブルを読み込みます                                       |
| gx_binres_theme_load                | バイナリ リソース データ バッファーからテーマを読み込みます                                                |
| gx_brush_default                     | 現在のブラシを既定値に初期化します                                                         |
| gx_brush_define                      | ブラシを定義します                                                                                 |
| gx_button_background_draw           | ボタンの背景を描画します                                                                       |
| gx_button_create                     | [作成] ボタン                                                                                |
| gx_button_deselect                   | ボタンを選択解除します                                                                              |
| gx_button_draw                       | ボタンを描画します                                                                                  |
| gx_button_event_process            | ボタン イベントを処理します                              |
| gx_button_select                    | [選択] ボタン                                     |
| gx_canvas_alpha_set                | キャンバスのアルファブレンド値を設定します                  |
| gx_canvas_arc_draw                 | 円弧を描画します                                   |
| gx_canvas_block_move               | ブロックを移動します                                        |
| gx_canvas_circle_draw              | 円を描画します                                       |
| gx_canvas_create                    | キャンバスを作成します                                   |
| gx_canvas_delete                    | キャンバスを削除します                                   |
| gx_canvas_drawing_complete         | キャンバスの描画を完了します                           |
| gx_canvas_drawing_initiate         | キャンバスで描画を開始します                        |
| gx_canvas_ellipse_draw             | 楕円を描画します                                   |
| gx_canvas_hardware_layer_bind     | キャンバスをグラフィックス レイヤーにバインドします                     |
| gx_canvas_hide                      | キャンバスを非表示にします                           |
| gx_canvas_line_draw                | 線を描画します                                         |
| gx_canvas_memory_define            | キャンバス メモリ アドレスを割り当てます                      |
| gx_canvas_offset_set               | キャンバスの X、Y 表示オフセットを割り当てます                  |
| gx_canvas_pie_draw                 | 円 (くさび形) の形を描画します                          |
| gx_canvas_pixel_draw               | 1 ピクセルを描画します                               |
| gx_canvas_pixelmap_blend           | ピクセルマップを背景とブレンドします                  |
| gx_canvas_pixelmap_get             | キャンバス データをポイントするピクセルマップを取得します            |
| gx_canvas_pixelmap_draw            | ピクセルマップを描画します                                     |
| gx_canvas_pixelmap_rotate          | ピクセルマップを回転します                                   |
| gx_canvas_pixelmap_tile            | ピクセルマップをタイル表示します                                     |
| gx_canvas_polygon_draw             | 多角形を描画します                                      |
| gx_canvas_rectangle_draw           | 四角形を描画します                                    |
| gx_canvas_rotated_text_draw       | (非推奨) 中心点の周りを回転するテキストを描画します |
| gx_canvas_rotated_text_draw_ext  | 中心点の周りを回転するテキストを描画します              |
| gx_canvas_shift                     | X、Y でキャンバスをシフトします                               |
| gx_canvas_show                      | キャンバスを表示します                             |
| gx_canvas_text_draw                | (非推奨) テキストを描画します                            |
| gx_canvas_text_draw_ext           | テキストを描画します                                         |
| gx_checkbox_create                  | チェック ボックスの作成                                 |
| gx_checkbox_draw                    | チェックボックスを描画します                                   |
| gx_checkbox_event_process          | チェックボックス イベント処理関数                   |
| gx_checkbox_pixelmap_set           | チェックボックスのピクセルマップを割り当てます                          |
| gx_checkbox_select                  | チェックボックスを選択します                                   |
| gx_circular_gauge_angle_get       | ゲージ ウィジェットの針の角度を取得します                |
| gx_circular_gauge_angle_set       | ゲージ ウィジェットの針の角度を割り当てます                  |
| gx_circular_gauge_animation_set   | 円形ゲージ アニメーションを定義します                   |
| gx_circular_gauge_background_draw | 円形ゲージの背景を描画します                    |
| gx_circular_gauge_create           | 円形ゲージ ウィジェットを作成します                    |
| gx_circular_gauge_draw             | 円形ゲージ ウィジェットを描画します                      |
| gx_circular_gauge_event_process   | 円形ゲージ イベントを処理します                      |
| gx_context_brush_default            | 現在のコンテキストのブラシを設定します                                      |
| gx_context_brush_define             | 現在のコンテキストのブラシを定義します                                       |
| gx_context_brush_get                | 現在のコンテキストのブラシを取得します                                          |
| gx_context_brush_pattern_set       | 現在のコンテキストのブラシのパターンを設定します                           |
| gx_context_brush_set                | 現在のコンテキストのブラシを設定します                                          |
| gx_context_brush_style_set         | 現在のコンテキストのブラシのスタイルを設定します                                    |
| gx_context_brush_width_set         | 現在のコンテキストのブラシの幅を設定します                                     |
| gx_context_color_get                | 色 ID を色の値に解決します                                     |
| gx_context_fill_color_set          | 現在のコンテキストの塗りつぶしの色を設定します                                     |
| gx_context_font_get                 | フォント ID をフォント ポインターの値に解決します                               |
| gx_context_font_set                 | 現在のコンテキストのフォントを設定します                                           |
| gx_context_line_color_set          | 現在のコンテキストの線の色を設定します                                     |
| gx_context_pixelmap_get             | ピクセルマップ ID をピクセルマップ ポインターの値に解決します                       |
| gx_context_pixelmap_set             | 領域の塗りつぶしに使用するブラシのピクセルマップを割り当てます                            |
| gx_context_raw_brush_define        | 現在のコンテキストの生のブラシを定義します                                   |
| gx_context_raw_fill_color_set     | 現在のコンテキストの生の塗りつぶしの色を設定します                                 |
| gx_context_raw_line_color_set     | 現在のコンテキストの生の線の色を設定します                                 |
| gx_context_string_get               | 現在の描画コンテキストに関連付けられている文字列を取得します (非推奨)。 |
| gx_context_string_get_ext          | 現在の描画コンテキストに関連付けられている文字列を取得します (非推奨)。 |
| gx_display_active_language_set     | アクティブな言語を割り当てます                                                |
| gx_display_color_set                | 表示色テーブルの 1 つの色の値を置き換えます。                       |
| gx_display_color_table_set         | 画面で使用される色テーブルを割り当てます                              |
| gx_display_create                    | 画面を作成します                                                        |
| gx_display_delete                    | 画面を削除します                                                        |
| gx_display_font_table_set          | 画面で使用されるフォント テーブルを割り当てます                               |
| gx_display_language_table_get      | 画面に関連付けられている言語テーブルを取得します (非推奨)    |
| gx_display_language_table_get_ext | 画面に関連付けられている言語テーブルを取得します                 |
| gx_display_language_table_set      | 示された画面に言語テーブルを割り当てます (非推奨)           |
| gx_display_language_table_set_ext | 示された画面に言語テーブルを割り当てます。                       |
| gx_display_pixelmap_table_set      | 画面で使用されるピクセルマップ テーブルを割り当てます                           |
| gx_display_string_get               | 文字列 ID に関連付けられた文字列を取得します (非推奨)                |
| gx_display_string_get_ext          | 文字列 ID に関連付けられた文字列を取得します                             |
| gx_display_string_table_get             | 示された画面に関連付けられた文字列テーブルを取得します (非推奨)。 |
| gx_display_string_table_get_ext        | 示された画面に関連付けられた文字列テーブルを取得します               |
| gx_display_theme_install                 | 指定された画面にテーマをインストールします                               |
| gx_drop_list_close                       | ドロップダウン リストを閉じます                                                       |
| gx_drop_list_create                      | ドロップダウン・リストを作成します                                                      |
| gx_drop_list_event_process               | ドロップダウン リストのイベント処理                                            |
| gx_drop_list_open                        | ドロップダウン リストを開きます                                                        |
| gx_drop_list_pixelmap_set               | ピクセルマップをドロップダウン リストに設定します                                             |
| gx_drop_list_popup_set                  | ポップアップをドロップダウン リストに設定します                                                |
| gx_generic_scroll_wheel_children_position | 汎用スクロール ホイールに子を配置します |
| gx_generic_scroll_wheel_create| 汎用スクロール ホイール ウィジェットを作成します |
| gx_generic_scroll_wheel_draw | 汎用スクロール ホイール ウィジェットを描画します |
| gx_generic_scroll_wheel_event_process| 汎用スクロール ホイールのイベントを処理します|
| gx_generic_scroll_wheel_row_height_set| 汎用スクロール ホイールの行の高さを設定します|
| gx_generic_scroll_wheel_total_rows_set| 汎用スクロール ホイールの合計行数を設定します |
| gx_horizontal_list_children_position    | 子ウィジェットを横方向の一覧に配置します                          |
| gx_horizontal_list_create                | 横方向の一覧を作成します                                                |
| gx_horizontal_list_event_process        | 横方向の一覧にあるイベントを処理します                                      |
| gx_horizontal_list_page_index_set      | 横方向の一覧ページのインデックスを割り当てます                                     |
| gx_horizontal_list_selected_index_get  | 選択された項目のインデックスを取得します                                           |
| gx_horizontal_list_selected_widget_get | 選択された項目のウイジェットを取得します                                          |
| gx_horizontal_list_selected_set         | 選択された項目を設定します                                                 |
| gx_horizontal_list_total_columns_set   | 作成後に一覧の列の数を変更します                          |
| gx_horizontal_scrollbar_create           | 水平スクロール バーを作成します                                           |
| gx_icon_button_create                    | アイコン ボタンを作成します                                                    |
| gx_icon_button_draw                      | アイコン ボタンを描画します                                                   |
| gx_icon_button_pixelmap_set             | アイコン ボタンにピクセルマップを設定します                                           |
| gx_icon_background_draw                  | アイコンの背景を描画します                                                  |
| gx_icon_create                            | [作成] アイコン                                                           |
| gx_icon_draw                              | アイコンを描画します                                                             |
| gx_icon_event_process                    | アイコン イベント処理関数                                        |
| gx_icon_pixelmap_set                     | アイコンにピクセルマップを設定します                                                 |
| gx_image_reader_create                   | イメージ リーダー モジュール インスタンスを作成します                                   |
| gx_image_reader_palette_set             | イメージ リーダー パレットを定義します                                           |
| gx_image_reader_start                    | 圧縮解除と変換のプロセスを開始します                           |
| gx_line_chart_axis_draw                 | 折れ線グラフの X、Y 軸を描画します                                              |
| gx_line_chart_create                     | GX_LINE_CHART インスタンスを作成します                                       |
| gx_line_chart_data_draw                 | 折れ線グラフのデータ線を描画します                                             |
| gx_line_chart_draw                       | 既定の折れ線グラフの描画                                            |
| gx_line_chart_update                     | 折れ線グラフ データを強制的に更新します                                       |
| gx_line_chart_y_scale_calculate        | ピクセル座標に対する Y 軸のデータ値のスケールを計算します。           |
| gx_menu_create                            | メニューを作成します                                                           |
| gx_menu_draw                              | メニューを描画します                                                             |
| gx_menu_event_process                     | メニュー イベントを処理します                                                    |
| gx_menu_insert                                | 新しい項目を挿入します                                                               |
| gx_menu_remove                                | 項目を削除します                                                                  |
| gx_menu_text_draw                            | メニュー テキストを描画します                                                                  |
| gx_menu_text_offset_set                     | メニュー テキストの描画オフセットを設定します                                                       |
| gx_multi_line_text_button_create           | 複数行テキスト ボタンを作成します                                                   |
| gx_multi_line_text_button_draw             | 複数行テキスト ボタンを描画します                                                     |
| gx_multi_line_text_button_event_process   | 複数行テキスト ボタンのフォントを設定します                                             |
| gx_multi_line_text_button_text_draw       | 描画のテキスト描画部分                                                 |
| gx_multi_line_text_button_text_id_set    | システム文字列をテキスト ボタンに設定します                                                |
| gx_multi_line_text_button_text_set        | ユーザー定義の文字列をテキスト ボタンに割り当てます (非推奨)                          |
| gx_multi_line_text_button_text_set_ext   | ユーザー定義の文字列をテキスト ボタンに割り当てます                                       |
| gx_multi_line_text_input_backspace         | 複数行テキスト入力のカーソル位置の前にある文字を削除します               |
| gx_multi_line_text_input_buffer_get       | テキスト入力ウィジェットのバッファー情報を取得します                               |
| gx_multi_line_text_input_buffer_clear     | テキスト入力バッファーからすべての文字を削除します                               |
| gx_multi_line_text_input_char_insert      | 複数行テキスト入力のカーソル位置に UTF8 形式の文字列を挿入します (非推奨) |
| gx_multi_line_text_input_char_insert_ext | 複数行テキスト入力のカーソル位置に UTF8 形式の文字列を挿入します              |
| gx_multi_line_text_input_create            | 複数行テキスト入力を作成します                                                    |
| gx_multi_line_text_input_cursor_pos_get  | 複数行テキスト入力のカーソル位置を取得します                                  |
| gx_multi_line_text_input_delete            | 複数行テキスト入力のカーソル位置の後にある文字を削除します                 |
| gx_multi_line_text_input_down_arrow       | 複数行テキスト入力のカーソルを次の行に移動します                              |
| gx_multi_line_text_input_end               | 複数行テキスト入力のカーソルを現在の行の末尾に移動します                |
| gx_multi_line_text_input_event_process    | 複数行テキスト入力のテキストを処理します                                              |
| gx_multi_line_text_input_fill_color_set  | 複数行テキスト入力の塗りつぶしの色を設定します                                       |
| gx_multi_line_text_input_home              | 複数行テキスト入力のカーソルを現在の行の先頭に移動します              |
| gx_multi_line_text_input_left_arrow       | 複数行テキスト入力のカーソルを 1 文字分だけ左に移動します                         |
| gx_multi_line_text_input_right_arrow      | 複数行テキスト入力のカーソルを 1 文字分だけ右に移動します                        |
| gx_multi_line_text_input_style_add        | 複数行テキストのスタイル フラグを追加します                                                 |
| gx_multi_line_text_input_style_remove     | 複数行テキストのスタイル フラグを削除します                                              |
| gx_multi_line_text_input_style_set        | 複数行テキストのスタイル フラグを割り当てます                                              |
| gx_multi_line_text_input_text_color_set  | 複数行テキスト入力のテキストの色を割り当てます                                    |
| gx_multi_line_text_input_text_select      | 複数行テキスト入力のテキストを選択します                                               |
| gx_multi_line_text_input_text_set         | 複数行テキスト入力にテキストを割り当てます (非推奨)                               |
| gx_multi_line_text_input_text_set_ext          | 複数行テキスト入力にテキストを割り当てます                         |
| gx_multi_line_text_input_up_arrow               | 複数行テキスト入力のカーソルを前の行に移動します       |
| gx_multi_line_text_view_create                   | 複数行テキスト ビューを作成します                                  |
| gx_multi_line_text_view_event_process           | 複数行テキスト ビュー イベントを処理します                           |
| gx_multi_line_text_view_font_set                | 複数行テキスト ビューで使用されるフォントを設定します                        |
| gx_multi_line_text_view_line_space_set         | 複数行テキスト ビューの行スペースを設定します                          |
| gx_multi_line_text_view_scroll_info_get        | 複数行テキスト ビューのスクロール情報を取得します                         |
| gx_multi_line_text_view_text_color_set         | 複数行テキスト ビューのテキストの色を設定します                       |
| gx_multi_line_text_view_text_id_set            | 複数行テキスト ビューのシステム テキスト文字列を設定します               |
| gx_multi_line_text_view_text_set                | 複数行テキスト ビューにユーザー定義の文字列を設定します (非推奨) |
| gx_multi_line_text_view_text_set_ext           | 複数行テキスト ビューにユーザー定義の文字列を設定します              |
| gx_multi_line_text_view_whitespace_set          | 複数行テキスト ビューの空白を設定します                          |
| gx_numeric_pixelmap_prompt_create                 | 数値ピクセルマップ プロンプトを作成します                               |
| gx_numeric_pixelmap_prompt_format_ function_set | 数値ピクセルマップ プロンプトの形式関数をオーバーライドします          |
| gx_numeric_pixelmap_prompt_value_set             | 数値プロンプトの値を設定します                                     |
| gx_numeric_prompt_create                           | 数値プロンプトを作成します                                        |
| gx_numeric_prompt_format_function_set            | 数値プロンプトの形式関数をオーバーライドします                   |
| gx_numeric_prompt_value_set                       | 数値プロンプトの値を設定します                                     |
| gx_numeric_scroll_wheel_create                    | 数値スクロール ホイール ウィジェットを作成します                           |
| gx_numeric_scroll_wheel_range_set                | スクロール ホイールの値の範囲を割り当てます                              |
| gx_pixelmap_button_create                          | ピクセルマップ ボタンを作成します                                       |
| gx_pixelmap_button_draw                            | ピクセルマップ ボタンを描画します                                         |
| gx_pixelmap_button_event_process                  | ピクセルマップ ボタンのイベント処理                             |
| gx_pixelmap_button_pixelmap_set                   | ピクセルマップ ボタンでピクセルマップを設定します                              |
| gx_pixelmap_prompt_create                          | ピクセル マップ プロンプトを作成します                                       |
| gx_pixelmap_prompt_draw                            | ピクセル マップ プロンプトを描画します                                         |
| gx_pixelmap_prompt_pixelmap_set                   | ピクセルマップ プロンプトでピクセルマップを設定します                              |
| gx_pixelmap_slider_create                          | ピクセルマップ スライダーを作成します                                       |
| gx_pixelmap_slider_draw                            | ピクセルマップ スライダーを描画します                                         |
| gx_pixelmap_slider_event_process        | ピクセルマップ スライダーのイベント処理       |
| gx_pixelmap_slider_pixelmap_set         | ピクセルマップ スライダーでピクセルマップを設定します        |
| gx_progress_bar_background_draw         | 進行状況バーの背景を描画します           |
| gx_progress_bar_create                   | 進行状況バーを作成します                  |
| gx_progress_bar_draw                     | 進行状況バーを描画します                    |
| gx_progress_bar_event_process           | 進行状況バーのイベントを処理します           |
| gx_progress_bar_font_set                | 進行状況バーのテキストのフォントを設定します          |
| gx_progress_bar_info_set                | 進行状況バーの情報の構造を設定します |
| gx_progress_bar_pixelmap_set            | 進行状況バーの描画に使用されるピクセルマップを設定します |
| gx_progress_bar_range_set               | 進行状況バーの値の範囲を設定します        |
| gx_progress_bar_text_color_set         | 進行状況バーのテキストの色を設定します            |
| gx_progress_bar_text_draw               | 進行状況バーのテキストを描画します                 |
| gx_progress_bar_value_set               | 進行状況バーの値を設定します                 |
| gx_prompt_create                          | プロンプトを作成します                          |
| gx_prompt_draw                            | プロンプトを描画します                            |
| gx_prompt_event_process                   | プロンプトのイベントを処理します                   |
| gx_prompt_font_set                       | プロンプトのフォントを設定します                        |
| gx_prompt_text_color_set                | プロンプトのテキストの色を設定します                  |
| gx_prompt_text_draw                      | プロンプトの描画のテキスト描画部分    |
| gx_prompt_text_get                       | プロンプトのテキストを取得します (非推奨)           |
| gx_prompt_text_get_ext                  | プロンプトのテキストを取得します                        |
| gx_prompt_text_id_set                   | システム テキスト文字列を使用してプロンプトを設定します     |
| gx_prompt_text_set                       | プロンプトのテキストを設定します (非推奨)           |
| gx_prompt_text_set_ext                  | プロンプトのテキストを設定します                        |
| gx_radial_progress_bar_anchor_set      | 開始角度を設定します                     |
| gx_radial_progress_bar_background_draw | 放射状の進行状況バーの背景を描画します    |
| gx_radial_progress_bar_create           | 放射状の進行状況バーを作成します           |
| gx_radial_progress_bar_draw             | 放射状の進行状況バーを描画します             |
| gx_radial_progress_bar_event_process   | 放射状の進行状況バーのイベントを処理します      |
| gx_radial_progress_bar_font_set        | 放射状の進行状況バーのフォントを設定します           |
| gx_radial_progress_bar_info_set        | 放射状の進行状況バーの情報を設定します    |
| gx_radial_progress_bar_text_color_set | 放射状の進行状況バーのテキストの色を設定します     |
| gx_radial_progress_bar_text_draw       | 放射状の進行状況バーのテキストを描画します          |
| gx_radial_progress_bar_value_set       | 放射状の進行状況バーの値を設定します          |
| gx_radio_button_create                   | オプション ボタンを作成します                    |
| gx_radio_button_draw                     | オプション ボタンを描画します                      |
| gx_radio_button_pixelmap_set            | オプション ボタンにピクセルマップを設定します           |
| gx_radial_slider_anchor_angles_set     | 放射状スライダーのアンカーの角度の一覧を設定します    |
| gx_radial_slider_angle_set              | 放射状スライダーの角度を設定します                |
| gx_radial_slider_animation_set          | 放射状スライダーのアニメーション情報を設定します       |
| gx_radial_slider_animation_start               | アニメーションを使用して放射状スライダーの角度を設定します                      |
| gx_radial_slider_create                         | 放射状スライダーを作成します                                      |
| gx_radial_slider_draw                           | 放射状スライダーを描画します                                        |
| gx_radial_slider_event_process                 | 放射状スライダーのイベントを処理します                               |
| gx_radial_slider_info_get                      | 放射状スライダーの情報ポインターを取得します                  |
| gx_radial_slider_info_set                      | 放射状スライダーの情報を設定します                               |
| gx_radial_slider_pixelmap_set                  | 放射状スライダーのピクセルマップを設定します                                 |
| gx_rich_text_view_create                       | リッチ テキスト ビューを作成します                                     |
| gx_rich_text_view_draw                         | リッチ テキスト ビューを描画します                                         |
| gx_rich_text_view_set_fonts                    | リッチ テキスト ビューのフォントを設定します                                    |
| gx_rich_text_view_text_draw                    | リッチ テキスト ビューのテキストを描画します                                    |
| gx_screen_stack_create                          | GUIX 画面スタック コントロール ブロックとメモリ領域を作成します。 |
| gx_screen_stack_pop                             | 画面スタックから一番上の画面をポップします。                   |
| gx_screen_stack_push                            | 現在の画面を画面スタックにプッシュします。                |
| gx_screen_stack_reset                           | 画面スタックをリセットします                                      |
| gx_scroll_wheel_create                          | 基本のスクロール ホイール ウィジェットを作成します                             |
| gx_scroll_wheel_event_process                  | スクロール ホイールのイベント処理                               |
| gx_scroll_wheel_gradient_alpha_set            | スクロール ホイールのオーバーレイのグラデーションを変更します                        |
| gx_scroll_wheel_row_height_set                | スクロール ホイールの行の高さを割り当てます                              |
| gx_scroll_wheel_selected_background_set       | 選択された行の背景画像を割り当てます                    |
| gx_scroll_wheel_selected_get                   | 選択された行のインデックスを取得します                                 |
| gx_scroll_wheel_selected_set                   | 選択された行のインデックスを割り当てます                                   |
| gx_scroll_wheel_speed_set                      | スクロール速度を割り当てます                                      |
| gx_scroll_wheel_total_rows_set                | 使用可能な行の合計数を割り当てます                       |
| gx_scrollbar_draw                                | スクロール バーを描画します                                              |
| gx_scrollbar_event_process                      | スクロール バーのイベントを処理します                                     |
| gx_scrollbar_limit_check                        | スクロール バーの制限を確認します                                       |
| gx_scrollbar_reset                               | スクロール バーをリセットします                                             |
| gx_scrollbar_value_set                          | スクロール バーの値を割り当てます                                      |
| gx_single_line_text_input_backspace           | バックスペース文字を処理します                                  |
| gx_single_line_text_input_buffer_clear       | 文字バッファーをクリアします                                  |
| gx_single_line_text_input_buffer_get         | バッファー ポインターを取得します                                     |
| gx_single_line_text_input_character_delete   | 文字を削除します                                            |
| gx_single_line_text_input_character_insert   | 文字を挿入します                                            |
| gx_single_line_text_input_create              | 単一行のテキスト入力を作成します                               |
| gx_single_line_text_input_draw                | 単一行のテキスト入力ウィジェットを描画します                          |
| gx_single_line_text_input_draw_position_get | テキスト描画の開始位置を取得します                           |
| gx_single_line_text_input_end                 | カーソルを末尾に移動します                                          |
| gx_single_line_text_input_event_process      | テキスト入力のイベント処理                                 |
| gx_single_line_text_input_fill_color_set    | 単一行テキスト入力の塗りつぶしの色を設定します                  |
| gx_single_line_text_input_home                | カーソルをホームに移動します                                         |
| gx_single_line_text_input_left_arrow         | 左方向キーを処理します                                       |
| gx_single_line_text_input_position_get       | カーソル位置を取得します                                         |
| gx_single_line_text_input_right_arrow        | 右方向キーを処理します                                      |
| gx_single_line_text_input_style_add          | スタイル フラグを追加します                                             |
| gx_single_line_text_input_style_remove       | スタイル フラグを削除します                                          |
| gx_single_line_text_input_style_set          | スタイル フラグを割り当てます                                          |
| gx_single_line_text_input_text_color_set  | 単一行テキスト入力のテキストの色を設定します                      |
| gx_single_line_text_input_text_select     | 単一行テキスト入力のテキストを選択します                              |
| gx_single_line_text_input_text_set        | 単一行テキスト入力のテキストを設定します (非推奨)                    |
| gx_single_line_text_input_text_set_ext    | 単一行テキスト入力のテキストを設定します                                 |
| gx_slider_create                          | スライダーを作成します                                                   |
| gx_slider_draw                            | スライダーを描画します                                                     |
| gx_slider_event_process                   | スライダーのイベントを処理します                                            |
| gx_slider_info_set                        | スライダー情報ブロックを設定します                                    |
| gx_slider_needle_draw                     | スライダーの針を描画します                                              |
| gx_slider_needle_position_get             | スライダーの針の位置を取得します                                      |
| gx_slider_tickmarks_draw                  | スライダーの目盛りを描画します                                           |
| gx_slider_travel_get                      | スライダーの移動を取得します                                               |
| gx_slider_value_calculate                 | スライダーの値を計算します                                          |
| gx_slider_value_set                       | スライダーの値を設定します                                                |
| gx_sprite_create                          | GX_SPRITE ウィジェットを作成します                                         |
| gx_sprite_current_frame_set               | スプライト ウィジェットに現在の表示フレームを割り当てます                  |
| gx_sprite_frame_list_set                  | スプライト フレームの一覧を割り当てまたは変更します                            |
| gx_sprite_start                           | スプライト シーケンスを開始します                                         |
| gx_sprite_stop                            | スプライト シーケンスを停止します                                          |
| gx_string_scroll_wheel_create             | `GX_STRING_SCROLL_WHEEL` ウィジェットを作成します                          |
| gx_string_scroll_wheel_event_process      | 文字列スクロール ホイールのイベントを処理します                               |
| gx_string_scroll_wheel_string_id_list_set | 文字列 ID の配列を割り当てます                                      |
| gx_string_scroll_wheel_string_list_set    | 表示された文字列の配列を変更します                                   |
| gx_string_scroll_wheel_text_get           | スクロール ホイールの行のテキストを取得します                              |
| gx_studio_widget_create                   | Studio 内で定義されたウィジェットを作成します                             |
| gx_studio_named_widget_create             | Studio 内で定義された画面を作成します                             |
| gx_studio_display_configure               | `GX_DISPLAY`、`GX_CANVAS`、`GX_WINDOW_ROOT` を作成して初期化します |
| gx_system_active_language_set             | アクティブな言語 ID を割り当てます                                       |
| gx_system_canvas_refresh                  | ダーティ キャンバスの更新 (描画) を強制します                       |
| gx_system_dirty_mark                      | 領域をダーティとしてマークします                                                 |
| gx_system_dirty_partial_add               | 一部の領域をダーティとしてマークします                                         |
| gx_system_draw_context_get                | 描画コンテキストを取得します                                             |
| gx_system_event_fold                      | イベントを折りたたみます                                                       |
| gx_system_event_send                      | イベントを送信します                                                      |
| gx_system_focus_claim                     | フォーカスを要求します                                                     |
| gx_system_initialize                      | GUIX を初期化します                                                 |
| gx_system_language_table_get              | 言語テーブルを取得します                                         |
| gx_system_language_table_set              | 言語テーブルを割り当てます                                           |
| gx_system_memory_allocator_set            | メモリ アロケーター/デアロケーターを割り当てます                            |
| gx_system_pen_configure                  | ペンの構成を設定します                                  |
| gx_system_screen_stack_create           | 画面スタック コントロールを作成します                            |
| gx_system_screen_stack_get              | 画面スタック ポインターを取得します                         |
| gx_system_screen_stack_pop              | 画面スタックから一番上の画面をポップします                       |
| gx_system_screen_stack_push             | 示された画面を画面スタックにプッシュします              |
| gx_system_screen_stack_reset            | 画面スタックをリセットします                                 |
| gx_system_scroll_appearance_get         | スクロールの外観を取得します                                  |
| gx_system_scroll_appearance_set         | スクロールの外観を設定します                                  |
| gx_system_start                           | GUIX を開始します                                             |
| gx_system_string_get                     | 文字列を取得します                                             |
| gx_system_string_table_get              | 文字列テーブルを取得します                                       |
| gx_system_string_table_set              | 文字列テーブルを設定します                                       |
| gx_system_string_width_get              | 文字列の幅を取得します (非推奨)                          |
| gx_system_string_width_get_ext         | 文字列の幅を取得します                                       |
| gx_system_theme_install                  | フォント、色、ピクセルマップのテーブルをインストールします                     |
| gx_system_timer_start                    | タイマーを開始します                                            |
| gx_system_timer_stop                     | タイマーを停止します                                             |
| gx_system_version_string_get            | GUIX ライブラリのバージョン文字列を取得します (非推奨)      |
| gx_system_version_string_get_ext       | GUIX ライブラリのバージョン文字列を取得します                   |
| gx_system_widget_find                    | ウイジェットを見つけます                                            |
| gx_text_button_create                    | テキスト ボタンを作成します                                     |
| gx_text_button_draw                      | テキスト ボタンを描画します                                       |
| gx_text_button_event_process             | テキスト ボタンのイベントを処理します                              |
| gx_text_button_font_set                 | テキスト ボタンのフォントを設定します                               |
| gx_text_button_text_color_set          | テキスト ボタンの色を設定します                                  |
| gx_text_button_text_draw                | ボタンの描画のテキスト描画部分                 |
| gx_text_button_text_get                 | テキスト ボタンに使用されるテキストを取得します (非推奨)              |
| gx_text_button_text_get_ext            | テキスト ボタンに使用されるテキストを取得します                           |
| gx_text_button_text_id_set             | システム文字列をテキスト ボタンに割り当てます                    |
| gx_text_button_text_set                 | ユーザー定義の文字列をテキスト ボタンに割り当てます (非推奨) |
| gx_text_button_text_set_ext            | ユーザー定義の文字列をテキスト ボタンに割り当てます              |
| gx_text_scroll_wheel_callback_set      | 文字列取得のコールバックを割り当てます (非推奨)          |
| gx_text_scroll_wheel_callback_set_ext | 文字列取得のコールバックを割り当てます                       |
| gx_text_scroll_wheel_create             | 基本のテキスト スクロール ホイールを作成します                          |
| gx_text_scroll_wheel_draw               | テキスト スクロール ホイールの描画関数                  |
| gx_text_scroll_wheel_event_process      | テキスト スクロール ホイールのイベントを処理します                        |
| gx_text_scroll_wheel_font_set          | テキスト スクロール ホイールのフォントを割り当てます                         |
| gx_text_scroll_wheel_text_color_set   | テキスト スクロール ホイールのテキストの色を割り当てます                   |
| gx_tree_view_create                    | ツリー ビューの作成                          |
| gx_tree_view_draw                      | ツリー ビューを描画します                              |
| gx_tree_view_event_process            | ツリー ビューのイベントを処理します                     |
| gx_tree-view_indentation_set           | ツリー ビューのインデントを設定します                   |
| gx_tree_view_position                  | ツリー ビューの項目を配置します                    |
| gx_tree_view_root_line_color_set    | ツリー ビューのルート線の色を設定します               |
| gx_tree_view_root_pixelmap_set       | ツリー ビューのルート ピクセルマップを設定します                |
| gx_tree_view_selected_get             | 選択された項目を取得します                      |
| gx_tree_view_selected_set             | 選択された項目を設定します                           |
| gx_utility_canvas_to_bmp              | キャンバス メモリをビットマップ形式に変換します      |
| gx_utility_circle_point_get           | 円上のポイントを計算します               |
| gx_utility_gradient_create             | グラデーションのピクセルマップを作成します                  |
| gx_utility_gradient_delete              | グラデーションのピクセルマップを削除します                  |
| gx_utility_ltoa                         | 長整数を ASCII に変換します               |
| gx_utility_math_acos                   | アーク コサインを計算します                          |
| gx_utility_math_asin                   | アーク サインを計算します                             |
| gx_utility_math_cos                    | コサインを計算します                              |
| gx_utility_math_sin                    | サインを計算します                                |
| gx_utility_math_sqrt                   | 平方根を計算します                         |
| gx_utility_bidi_paragraph_reorder         | BiDi テキストを表示順に並べ替えます|
| gx_utility_bidi_resolved_text_info_delete | 並べ替えられた BiDi テキストを削除します               |
| gx_utility_pixelmap_resize             | ピクセルマップをサイズ変更します                             |
| gx_utility_pixelmap_rotate             | 任意の角度でピクセルマップを回転します          |
| gx_utility_pixelmap_simple_rotate      | ピクセルマップを 90、180、270 度回転します     |
| gx_utility_rectangle_center            | 別の四角形の中で四角形を中央に配置します   |
| gx_utility_rectangle_center_find      | 四角形の中央を探します                    |
| gx_utility_rectangle_combine           | 2 つの四角形を最初のものに結合します           |
| gx_utility_rectangle_compare           | 2 つの四角形を比較します                      |
| gx_utility_rectangle_define            | 四角形を定義します                            |
| gx_utility_rectangle_resize            | 四角形をサイズ変更します                            |
| gx_utility_rectangle_overlap_detect   | 四角形の重なりを検出します                |
| gx_utility_rectangle_point_detect     | ポイントが四角形内に存在するかどうかを検出します        |
| gx_utility_rectangle_shift             | 四角形をシフトします                             |
| gx_utility_string_to_alphamap         | テキスト文字列を alphamap にレンダリングします (非推奨) |
| gx_utility_string_to_alphamap_ext    | テキスト文字列を alphamap にレンダリングします              |
| gx_vertical_list_children_position    | 縦の一覧に子を配置します          |
| gx_vertical_list_create                | 縦の一覧を作成します                        |
| gx_vertical_list_event_process        | 縦の一覧のイベントを処理します                 |
| gx_vertical_list_selected_index_get  | 選択された項目のインデックスを取得します                     |
| gx_vertical_list_selected_widget_get | 選択されたウイジェットを取得します                         |
| gx_vertical_list_selected_set         | エントリを縦の一覧に設定します                  |
| gx_vertical_list_total_rows_set      | 作成後に一覧の行の数を変更します   |
| gx_vertical_scrollbar_create           | 垂直スクロール バーを作成します                   |
| gx_widget_allocate                      | ウィジェットを動的に割り当てます               |
| gx_widget_attach                        | ウィジェットを親にアタッチします                     |
| gx_widget_background_draw              | ウィジェットの背景を描画します                      |
| gx_widget_back_attach                  | ウィジェットを背面にアタッチします                       |
| gx_widget_back_move                    | ウイジェットを背面に移動します                         |
| gx_widget_block_move                   | ピクセルのブロックを移動します                        |
| gx_widget_border_draw                  | ウィジェットの枠線を描画します                          |
| gx_widget_border_style_set            | ウィジェットの枠線のスタイルを設定します                     |
| gx_widget_border_width_get            | ウィジェットの枠線の幅を設定します                     |
| gx_widget_canvas_get               | ウィジェット キャンバスを取得します                                                         |
| gx_widget_child_detect             | ウィジェットの子を検出します                                                       |
| gx_widget_children_draw            | ウィジェットの子を描画します                                                      |
| gx_widget_client_get               | ウィジェットのクライアント領域を取得します                                                    |
| gx_widget_color_get                | 表示されているウィジェットで色 ID を色の値に解決します                      |
| gx_widget_create                    | ウィジェットを作成します                                                             |
| gx_widget_created_test             | ウィジェットが作成されたかどうかをテストします                                                    |
| gx_widget_delete                    | ウィジェットを削除します                                                             |
| gx_widget_detach                    | 親からウイジェットをデタッチします                                                 |
| gx_widget_draw                      | ウィジェットを描画します                                                               |
| gx_widget_draw_set                 | ウィジェットの描画関数を設定します                                               |
| gx_widget_event_generate           | ウイジェットのイベントを生成します                                                     |
| gx_widget_event_process            | ウィジェットのイベントを処理します                                                      |
| gx_widget_event_process_set       | ウィジェットのイベント処理関数を設定します                                   |
| gx_widget_event_to_parent         | ウィジェットの親にイベントを送信します                                             |
| gx_widget_fill_color_set          | ウィジェットの塗りつぶしの色を割り当てます                                                  |
| gx_widget_find                      | ウイジェットを見つけます                                                               |
| gx_widget_first_child_get         | 最初の子へのポインターを返します                                             |
| gx_widget_focus_next               | 入力フォーカスを次のウィジェットに移動します                                           |
| gx_widget_focus_previous           | 入力フォーカスを前のウィジェットに移動します                                       |
| gx_widget_font_get                 | 表示されているウィジェットでフォント ID をフォント ポインターに解決します                    |
| gx_widget_free                      | ウィジェット コントロール ブロックのメモリを解放します                                          |
| gx_widget_front_move               | ウィジェットを前面に移動します                                                      |
| gx_widget_height_get               | ウイジェットの高さを取得します                                                         |
| gx_widget_hide                      | ウイジェットを非表示にします                                                               |
| gx_widget_last_child_get          | 最後の子へのポインターを返します                                              |
| gx_widget_next_sibling_get        | 次の兄弟へのポインターを返します                                            |
| gx_widget_parent_get               | 親ウィジェットへのポインターを返します                                           |
| gx_widget_pixelmap_get             | 表示されているウイジェットでピクセルマップ ID をピクセルマップ ポインターに解決します            |
| gx_widget_previous_sibling_get    | 前の兄弟へのポインターを返します                                        |
| gx_widget_resize                    | ウイジェットをサイズ変更します                                                             |
| gx_widget_shift                     | ウイジェットをシフトします                                                              |
| gx_widget_show                      | ウィジェットを表示します                                                               |
| gx_widget_status_add               | ウィジェットの状態を追加する                                                         |
| gx_widget_status_get               | ウィジェットの状態フラグを取得します                                              |
| gx_widget_status_remove            | ウィジェットの状態を削除します                                                      |
| gx_widget_string_get               | 表示されているウィジェットの文字列 ID に関連付けられた文字列を取得します (非推奨) |
| gx_widget_string_get_ext          | 表示されているウィジェットの文字列 ID に関連付けられた文字列を取得します。             |
| gx_widget_status_test              | ウィジェットの状態をテストします                                                        |
| gx_widget_style_add                | ウィジェットのスタイルを追加します                                                          |
| gx_widget_style_get                | ウィジェットのスタイル フラグを取得します                                               |
| gx_widget_style_remove             | ウィジェットのスタイルを削除します                                                       |
| gx_widget_style_set                | ウィジェットのスタイルを設定します                                                          |
| gx_widget_text_blend               | ブレンドしたテキストをウィジェット上にレンダリングします (非推奨)                              |
| gx_widget_text_blend_ext          | ブレンドしたテキストをウィジェット上にレンダリングします                                           |
| gx_widget_text_draw                | テキストをウィジェット上にレンダリングします (非推奨)                                      |
| gx_widget_text_draw_ext           | テキストをウィジェット上にレンダリングします                                            |
| gx_widget_text_id_draw            | 文字列 ID で識別されたテキストをウィジェット上にレンダリングします                           |
| gx_widget_top_visible_child_find | Z オーダーの最上部に描画された、表示されている子へのポインターを返します   |
| gx_widget_type_find                | ウィジェットの種類を見つけます                                                          |
| gx_widget_width_get                | ウィジェットの幅を取得します                                                          |
| gx_window_canvas_set               | ウィンドウ キャンバスを設定します                                                         |
| gx_window_client_height_get       | ウィンドウ クライアントの高さを取得します                                                  |
| gx_window_client_scroll            | ウィンドウ クライアントをスクロールします                                                     |
| gx_window_client_width_get        | ウィンドウ クライアントの幅を取得します                                                   |
| gx_window_close                     | モーダル ウィンドウの実行を終了します                                          |
| gx_window_create                    | ウィンドウを作成します                                                             |
| gx_window_draw                      | ウィンドウを描画します                                                               |
| gx_window_event_process            | ウィンドウ イベントを処理します                                                      |
| gx_window_execute                   | モーダル ウィンドウの実行                                                    |
| gx_window_root_create              | ルート ウィンドウを作成します                                                        |
| gx_window_root_delete              | ルート ウィンドウを破棄します                                                       |
| gx_window_root_event_process      | ルート ウィンドウのイベントを処理します                                             |
| gx_window_root_find                | ルート ウィンドウを見つけます                                                          |
| gx_window_scroll_info_get         | ウィンドウのスクロール情報を取得します                                                    |
| gx_window_scrollbar_find           | ウィンドウのスクロール バーを見つけます                                                     |
| gx_window_wallpaper_get            | ウィンドウの壁紙を取得します                                                      |
| gx_window_wallpaper_set            | ウィンドウの壁紙を設定します                                                      |

## <a name="gx_accordion_menu_create"></a>gx_accordion_menu_create

アコーディオン メニューを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_accordion_menu_create(
    GX_ACCORDION_MENU *accordion,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    ULONG style ,
    USHORT accordion_menu_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスでは、指定どおりのアコーディオン メニューが作成され、指定された親ウィジェットにそのアコーディオン メニューがアタッチされます。 アコーディオン メニューは、展開したり折りたたんだりするメニュー表示ウィジェットです。 これは、すべての種類のウィジェットをその子メニュー項目として受け入れます。 アコーディオン メニューは入れ子にすることができます。つまり、複数のレベルの深さを持つメニューを作成できます。

子項目をメニュー項目ウィジェットに挿入するには、親メニュー項目として GX_MENU 型のウィジェットを使用することをお勧めします。

単一レベルのアコーディオン メニューを作成する場合のヒント:

1.  アコーディオン メニューを作成します。

2.  GX_MENU 型ウィジェットをアコーディオン メニューにアタッチします。

3.  子ウィジェットを GX_MENU 型の親にアタッチします。 子項目の種類は、任意の GUIX ウィジェットの種類にすることができます。

複数レベルのアコーディオン メニューを作成する場合のヒント:

1.  アコーディオン メニューを作成します。

2.  GX_MENU 型ウィジェットをアコーディオン メニューにアタッチします。

3.  GX_ACCORDION_MENU 型ウィジェットを GX_MENU 型の親にアタッチします。

4.  単一レベルのアコーディオン メニューの作成で説明されているように、メニュー項目を GX_ACCORDION_MENU 型の親にアタッチします。

### <a name="parameters"></a>パラメーター

- **accordion** アコーディオン メニュー コントロール ブロックへのポインター
- **name** アコーディオン メニューの名前
- **parent** 親ウィジェットへのポインター
- **style** ウィジェットのスタイル。 **付録 D** には、ウィジェット固有のスタイルだけでなく、すべてのウィジェット用に事前に定義されている一般的なスタイルが記載されています。
- **accordion_menu_id** アコーディオン メニューのアプリケーション定義の ID
- **size** アコーディオン メニューのサイズ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) アコーディオン メニューの作成が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_ACCORDION_MENU my_accordion;
GX_MENU menu_1;
GX_MENU item_1;
GX_RECTANGLE size;

gx_utility_rectangle_define(&size, 100, 100, 300, 150);

status = gx_accordion_menu_create(&my_accordion, “my_accordion”,
                                  parent, GX_STYLE_ENABLED,
                                  MY_ACCORDION_ID, &size);

gx_menu_create(&menu_1, “menu_1”, &my_accordion,
               GX_STRING_ID_MENU_1, GX_ID_NONE,
               GX_STYLE_ENABLED | GX_TYLE_BORDER_THIN, 0, &size);

gx_menu_create(&item_1, “item_1”, &my_accordion,
               GX_STRING_ID_ITEM_1, GX_ID_NONE,
               GX_STYLE_ENABLED | GX_STYLE_BORDER_THIN, 0, &size);

gx_text_offset_set(&item_1, 30, 0);

gx_menu_insert(&menu_1, &item_1);

/* If status is GX_SUCCESS the accordion menu was successfully created. */

```

GUIX Studio のインストールの一部として提供されているデモ アプリケーション demo_guix_widget_types には、アコーディオン メニュー ウィジェットの使用の完全な例が用意されています。

### <a name="see-also"></a>参照

- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_accordion_menu_draw"></a>gx_accordion_menu_draw

アコーディオン メニューを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_accordion_menu_draw(GX_ACCORDION_MENU *accordion);
```

### <a name="description"></a>説明

このサービスでは、指定されたアコーディオン メニューが描画されます。 通常、このサービスは GUIX キャンバスの更新機構によって内部で呼び出されますが、カスタム アコーディオン メニュー ウイジェットのカスタム描画関数の実装を支援するためにアプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **accordion** アコーディオン メニュー コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Define a custom accordion menu draw function */

VOID my_accordion_menu_draw(GX_ACCORDION_MENU *accordion)
{
    /* Call default accordion menu draw. */
    gx_accordion_menu_draw(accordion);

    /* Add custom drawing here. */
}

```

### <a name="see-also"></a>参照

- gx_accordion_menu_create
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_accordion_menu_event_process"></a>gx_accordion_menu_event_process

アコーディオン メニュー イベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_accordion_menu_event_process(
    GX_ACCORDION_MENU *accordion, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>説明

このサービスでは、指定されたアコーディオン メニューのイベントが処理されます。 このサービスは、カスタム アコーディオン メニュー イベント処理関数によって既定のイベント ハンドラーとして呼び出される必要があります。

このサービスにより、GX_EVENT_PEN_DOWN と GX_EVENT_PEN_UP イベントが処理され、メニュー項目が展開されたり折りたたまれたりします。

### <a name="parameters"></a>パラメーター

- **accordion** アコーディオン メニュー コントロール ブロックへのポインター
- **event_ptr** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) アコーディオン メニュー イベントの処理が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Call generic accordion menu event processing as part of custom event processing function. */

UINT custom_accordion_event_process( 
    GX_ACCORDION_MENU *accordion,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default accordion menu
            event processing */
        status =
        gx_accordion_menu_event_process(accordion, event);
        break;
    }
    return status;
}

```

### <a name="see-also"></a>参照

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_accordion_menu_position"></a>gx_accordion_menu_position

メニュー項目を配置します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_accordion_menu_position(GX_ACCORDION_MENU *accordion);
```

### <a name="description"></a>説明

このサービスでは、アコーディオン メニューのメニュー項目が配置されます。 この関数は通常、アコーディオン メニューが表示されるようになるときに内部で呼び出されます。 アコーディオン メニューで項目を挿入/削除する場合や、子項目の展開スタイルを変更する場合は、この関数を呼び出して子項目の位置を変更する必要があります。

### <a name="parameters"></a>パラメーター

- **accordion** アコーディオン メニュー コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) アコーディオン メニューの配置が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Position menu items in the accordion menu “my_accordion” */
status = gx_accordion_menu_position (&my_accordion);

/* If status is GX_SUCCESS the children in the accordion menu
“my_accordion” are positioned. */

```

### <a name="see-also"></a>参照

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_animation_canvas_define"></a>gx_animation_canvas_define

アニメーション コントローラーにキャンバス メモリを提供します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_animation_canvas_define(
    GX_ANIMATION *animation, 
    GX_CANVAS *canvas);
```

### <a name="description"></a>説明

このサービスでは、アニメーション シーケンスの実装に使用されるアニメーション コントローラーにメモリ キャンバスが提供されます。 この提供されるキャンバスは、アニメーションのターゲット ウィジェットを保持するのに十分な大きさでなければなりません。

アニメーション キャンバスが定義されるときに、このアニメーション キャンバスにターゲット ウィジェットが 1 回描画されます。また、キャンバスのオフセットかキャンバスのアルファ値 (またはこの両方) を変更することで、画面のスライドまたはフェード効果が実現されます。 複数のグラフィックス レイヤーに対するハードウェア サポートが提供されている場合、ハードウェアのグラフィックス オーバーレイ レイヤーにバインドされているアニメーション キャンバスを定義すると、スライドとフェードのアニメーションのパフォーマンスが "***大幅***" に向上する可能性があります。

アニメーション マネージャーでは、16 bpp 未満の色深度で実行されている場合に、フェードインとフェードアウトのアニメーションの種類を実行するためにアニメーション キャンバスが必要です。

### <a name="parameters"></a>パラメーター

- **animation** アニメーション コントロール ブロックへのポインター
- **canvas** 平行移動アニメーションの実装に使用されるメモリ キャンバス。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) アニメーション キャンバスの定義が成功しました
- **GX_INVALID_STATUS** (0x10) アニメーションの状態が無効です
- **GX_INVALID_MEMORY_SIZE** (0x29) 提供されたメモリ ブロックの大きさがキャンバスを作成するのに十分ではありません
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_ANIMATION animation;
GX_CANVAS animation_canvas;
GX_ROOT_WINDOW animation_root;
/* Create animation canvas. */
status = gx_canvas_create(
        &animation_canvas, /* Canvas control block. */
        “animation_canvas”, /* Name of canvas. */
        display, /* Display control block. */
        GX_ANIMATION_MANAGED, /* Type of canvas. */
        width, /* Width of canvas. */
        height, /* Height of canvas. */
        memory_area, /* Memory area of canvas. */
        memory_size /* Size of canvas memory. */
        );
if (status == GX_SUCCESS)
{
    /* Create the root window for the canvas. */
    status = gx_window_root_create(
        &animation_root, /* Root window control block. */
        “animation_root”, /* Name of root window. */
        &animation_canvas, /* Canvas of the root window. */ GX_STYLE_NONE, /* Style of the window. */
        GX_ID_NONE, /* Root window ID. */
        &root_size /* Window size. */
        );
}
if (status == GX_SUCCESS)
{
    /* Define canvas for the animation. */
    status = gx_animation_canvas_define(&animation,
                &animation_canvas);
}
/* If status is GX_SUCCESS the new canvas was successfully set to the animation manager. */

```

### <a name="see-also"></a>参照

- gx_animation_create
- gx_animation_delete
- gx_animation_drag_disable
- gx_animation_drag_enable
- gx_animation_landing_speed_set
- gx_animation_start
- gx_animation_stop

## <a name="gx_animation_create"></a>gx_animation_create

アニメーション コントローラーを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_animation_create(GX_ANIMATION *animation);
```

### <a name="description"></a>説明

このサービスでは、アニメーション コントローラーが作成されます。 コントローラーはアイドル状態に初期化されます。 アニメーションは、アイドル状態でない場合は開始できません。 GX_ANIMATION コントロール ブロック ポインターは、gx_system_animation_get() を使用して取得できます。または、静的に定義されたコントロール ブロックである場合もあります。

### <a name="parameters"></a>パラメーター

- **animation** アニメーション コントロール ブロックへのポインター


### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) アニメーション コントローラーの作成が成功しました
- **GX_ALREADY_CREATED** (0x13) コントロール ブロックは既に初期化されています
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_ANIMATION *animation;

/* Allocate an animaton control from system pool */
gx_system_animation_get(&animation);

/* Initialize the control block */

if (animation)
{
    status = gx_animation_create(animation);
}

/* If status is GX_SUCCESS the new animation controller was successfully created and initialized. */

```

### <a name="see-also"></a>参照

- gx_animation_canvas_define
- gx_animation_delete
- gx_animation_drag_disable
- gx_animation_drag_enable
- gx_animation_start
- gx_animation_landing_speed_set
- gx_animation_stop
- gx_system_animation_get
- gx_system_animation_free

## <a name="gx_animation_delete"></a>gx_animation_delete

1 つ以上のアニメーション コントローラーを削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_animation_delete(GX_ANIMATION *animation, GX_WIDGET *parent);
```

### <a name="description"></a>説明

このサービスでは、入力アニメーション ポインターが設定されている場合、アニメーション シーケンスが削除されます。それ以外の場合は、指定した親ウィジェットに属しているすべてのアニメーションが削除されます。

### <a name="parameters"></a>パラメーター

- **animation** アニメーション コントロール ブロックへのポインター
- **parent** 親ウィジェットへのポインター


### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) アニメーション コントローラーの削除が成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

- 1 つのアニメーションを削除する

```C
GX_ANIMATION *animation;

/* Allocate an animaton control from system pool */
gx_system_animation_get(&animation);

if (animation)
{
    /* Create an animation.  */
    gx_animation_create(animation);

    /* Delete an animation.  */
    status = gx_animation_delete(animation, GX_NULL);
}

/* If status is GX_SUCCESS the animation controller was successfully deleted and returned back to system animation pool. */

```

- 複数のアニメーションを削除する
```C

status = gx_animation_delete(GX_NULL, parent);

/* If status is GX_SUCCESS all the animations belong to the parent were successfully deleted. */

```

### <a name="see-also"></a>参照

- gx_animation_canvas_define、
- gx_animation_create
- gx_animation_drag_disable、
- gx_animation_drag_enable
- gx_animation_start
- gx_animation_landing_speed_set、
- gx_animation_stop
- gx_system_animation_get
- gx_system_animation_free

## <a name="gx_animation_drag_disable"></a>gx_animation_drag_disable

画面のドラッグ アニメーションのフックを無効にします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_animation_drag_disable(
    GX_ANIMATION *animation, 
    GX_WIDGET *widget);
```

### <a name="description"></a>説明

このサービスでは、ウィジェットの既定のイベント処理関数から画面のドラッグ アニメーションのフック プロシージャが削除され、アニメーション シーケンスが停止されます。 画面のドラッグ アニメーションのフック プロシージャによって、画面のドラッグ アニメーションのイベントが処理されます。

### <a name="parameters"></a>パラメーター

- **animation** アニメーション コントロール ブロックへのポインター
- **widget** ウィジェット コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_ANIMATION animation;
GX_WIDGET *animation_parent;

/* Disable screen drag animation of “animation_parent”. */
status = gx_animation_drag_disable(&animation, animation_parent);

/* If status is GX_SUCCESS the screen drag hook has been removed
    from the event process of “animation_parent”. */

```

### <a name="see-also"></a>参照

- gx_animation_canvas_define
- gx_animation_create
- gx_animation_delete
- gx_animation_drag_enable
- gx_animation_landing_speed_set
- gx_animation_start
- gx_animation_stop
- gx_system_animation_get
- gx_system_animation_free

## <a name="gx_animation_drag_enable"></a>gx_animation_drag_enable

画面のドラッグ アニメーションのフックを有効にします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_animation_drag_enable(
    GX_ANIMATION *animation,
    GX_WIDGET *widget, 
    GX_ANIMATION_INFO *info);
```

### <a name="description"></a>説明

このサービスでは、内部で定義された画面のドラッグ アニメーションのイベント処理関数が、ウィジェットの既定のイベント処理関数のフック プロシージャとして設定されます。 画面のドラッグ アニメーションのイベント処理関数によって、画面のドラッグ アニメーションのイベントが処理されます。

画面のドラッグ フック プロシージャが、ターゲット ウィジェットに送信されるペン入力イベントの既定のハンドラーになります。 元のウィジェット イベント処理関数は、画面のドラッグ入力イベントの種類を確認した後に、デイジー チェーン方式で呼び出されます。

### <a name="parameters"></a>パラメーター

- **animation** アニメーション コントロール ブロックへのポインター
- **widget** ウィジェット コントロール ブロックへのポインター
- **info** アニメーション情報

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 成功しました
- **GX_INVALID_STATUS** (0x26) アニメーションの状態が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_VALUE** (0x22) 値が無効です
- **GX_INVALID_WIDGET** (0x12) スライド画面の一覧が指定されていません

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_ANIMATION animation;
GX_ANIMATION_INFO info;
GX_WIDGET *animation_parent;
GX_WIDGET *screen_list[] = {
    screen_1,
    screen_2,
    screen_3,
    GX_NULL
}

memset(&info, 0, sizeof(GX_ANIMATION_INFO);
info.gx_animation_parent = animation_parent;

/* If GX_STYLE_ANIMATION_WRAP is set, the screen list will wrap itself. */
info.gx_animation_style = GX_ANIMATION_SCREEN_DRAG |
                          GX_ANIMATION_HORIZONTAL |
                          GX_STYLE_ANIMATION_WRAP;
info.gx_animation_frame_interval = 1;
info.gx_animation_slide_screen_list = screen_list;

status = gx_animation_drag_enable(&animation, animation_parent,
                                  info);

/* If status is GX_SUCCESS the screen slide animinatin event
    process function has been set as a hook procedure of
    “animation_parent”. */
```

### <a name="see-also"></a>参照

- gx_animation_canvas_define
- gx_animation_create
- gx_animation_delete
- gx_animation_drag_disable
- gx_animation_landing_speed_set
- gx_animation_start
- gx_animation_stop
- gx_system_animation_get
- gx_system_animation_free

## <a name="gx_animation_landing_speed_set"></a>gx_animation_landing_speed_set

画面のドラッグ アニメーションのランディング速度を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_animation_landing_speed_set(
    GX_ANIMATION *animation, 
    USHORT shift_per_step);
```

### <a name="description"></a>説明

このサービスでは、画面のドラッグ アニメーションのランディング速度が設定されます。

### <a name="parameters"></a>パラメーター

- **animation** アニメーション コントロール ブロックへのポインター
- **shift_per_step** 各ステップのシフト距離

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 成功しました
- **GX_INVALID_VALUE** (0x22) パラメーターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set landing speed of “my_animation” to 20. */
status = gx_animation_landing_peed_set(&my_animation, 20);

/* If status is GX_SUCCESS the landing speed is successfully set to 20. */
```

### <a name="see-also"></a>参照

- gx_animation_canvas_define
- gx_animation_create
- gx_animation_delete
- gx_animation_slide_disable
- gx_animation_slide_enable
- gx_animation_start
- gx_animation_stop
- gx_system_animation_get
- gx_system_animation_free

## <a name="gx_animation_start"></a>gx_animation_start

タイマー駆動型アニメーションを開始します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_animation_start(
    GX_ANIMATION *animation, 
    GX_ANIMATION_INFO *params);
```

### <a name="description"></a>説明

このサービスでは、以前に作成されたアニメーション インスタンスと新しい一連のアニメーション パラメーターを使用して、アニメーション シーケンスが開始されます。 この関数によってパラメーターのローカル コピーが作成されます。つまり、パラメーター構造を静的に定義する必要はありません。

GX_ANIMATION 制御構造はアプリケーションによって静的に定義することも、gx_system_animation_get() API を使用して取得することもできます。

GX_ANIMATION_INFO 構造体では、実行されるアニメーションのパラメーターが定義されます。 この構造体と各フィールドの意味の詳細な説明については、このマニュアルの第 3 章にある GUIX アニメーション コンポーネントに関するセクションを参照してください。

### <a name="parameters"></a>パラメーター

- **animation** アニメーション コントロール ブロックへのポインター
- **params** パラメーター構造へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 成功しました
- **GX_INVALID_VALUE** (0x22) パラメーターが無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) アニメーションのターゲットが無効です
- **GX_INVALID_STATUS** (0x26) アニメーションの状態が無効です
- **GX_INVALID_CANVAS** (0x20) アニメーションのキャンバスが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_ANIMATION_INFO params;
GX_ANIMATION *animation;

/* obtain an animation control block pointer */
gx_system_animation_get(&animation);
if (animation)
{
    /* define a slide down and to the right */
    params.gx_animation_start_position.gx_point_x = 0;
    params.gx_animation_start_position.gx_point_y = 0;
    params.gx_animation_end_position.gx_point_x = 100;
    params.gx_animation_end_position.gx_point_y = 200;
    params.gx_animation_style= GX_ANIMATION_TRANSLATE;
    params.gx_animation_target = &my_window;
    params.gx_animation_parent = root_window;
    params.gx_animation_start_alpha = 255;
    params.gx_animation_end_alpha = 255;

    params.gx_animation_delay_before = 0;
    params.gx_animation_steps = 10;
    params.gx_animation_tick_rate = 2;

    status = gx_animation_start(&animation, &params);
}

/* If status is GX_SUCCESS the animation is initiated. */
```

### <a name="see-also"></a>参照

- gx_animation_canvas_define、
- gx__animation_create
- gx_animation_slide_disable、
- gx__animation_slide_enable
- gx_animation_landing_speed_set、
- gx__animation_stop
- gx_system_animation_get、
- gx__system_animation_free

## <a name="gx_animation_stop"></a>gx_animation_stop

アクティブなタイマー駆動型アニメーションを停止します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_animation_stop(GX_ANIMATION *animation);
```

### <a name="description"></a>説明

以前に開始されたアニメーションを停止します。 アニメーション コントロール ブロックのポインターが gx_system_animation_get を使用して割り当てられている場合、アプリケーションでは、コントロール ブロックを再利用することも、gx_system_animation_free() を使用してそれをシステム プールに返すこともできます。

### <a name="parameters"></a>パラメーター

- **animation** アニメーション コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 成功しました GX_PTR_ERROR (0x07) ポインターが無効です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_STATUS** (0x26) コントローラーの状態が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_ANIMATION animation;

status = gx_animation_stop(&animation);

/* If status is GX_SUCCESS the animation is stopped */

```

### <a name="see-also"></a>参照

- gx_animation_canvas_define
- gx_animation_create
- gx_animation_delete
- gx_animation_drag_disable
- gx_animation_drag_enable
- gx_animation_start
- gx_system_animation_get
- gx_system_animation_free

## <a name="gx_binres_language_count_get"></a>gx_binres_language_count_get

バイナリ リソース データに存在する言語の数を返します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_binres_language_count_get(
    GX_UBYTE *root_address, 
    GX_VALUE *returned_count);
```

### <a name="description"></a>説明

このサービスでは、バイナリ リソース データのヘッダーが解析され、バイナリ データに含まれる言語の数が返されます。 これは、ユーザーが複数の言語の選択肢から選択できるように、ユーザーに選択リストを表示する必要があるアプリケーションに役立ちます。

### <a name="parameters"></a>パラメーター

- **root_address** メモリ内のバイナリ リソース データのアドレス
- **return_count** 返された言語の数を格納する場所

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 成功しました
- **GX_INVALID_FORMAT** (0x24) バイナリ リソースが無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_VALUE language_count = 0;

/* Specify address that binary resource data is located. */
GX_UBYTE    *root_address = 0x60000000;

status = gx_binres_language_count_get(root_address,
    &language_count);

/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>参照

- gx_binres_language_info_load

## <a name="gx_binres_language_info_load"></a>gx_binres_language_info_load

言語テーブルの情報を読み込みます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_binres_language_info_load(
    GX_UBYTE *root_address, 
    GX_LANGUAGE_HEDAER *put_info);
```

### <a name="description"></a>説明

このサービスでは、バイナリ リソース データ BLOB の解析によって GX_LANGUAGE_HEADER 構造体の配列が設定され、バイナリ データに含まれる各言語の言語名と文字列テーブルのサイズがアプリケーションに通知されます。 アプリケーションでは、まず gx_binres_language_count_get() が呼び出され、バイナリ データ内の言語の数が特定され、この関数に渡された put_info ポインターが language_count GX_LANGUAGE_HEADER 構造体の配列を指していることが確認されます。

このサービスは、バイナリ リソース データ チャンクの内容を実行時に特定するためにアプリケーションによって使用されます。

GX_LANGUAGE_HEADER 構造体は次のように定義されます。

```c
typedef struct GX_LANGUAGE_HEADER_STRUCT{
    USHORT gx_language_header_magic_number;
    USHORT gx_language_header_index;
    UCHAR gx_language_header_name[GX_LANGUAGE_HEADER_NAME_SIZE];
    ULONG  gx_language_header_data_size;
} GX_LANGUAGE_HEADER;
```

- *magic_number* フィールドは、バイナリ リソース データ形式の内部検証に使用されます。
- *header_index* フィールドは、バイナリ データ内で言語が定義されている順序を示します。
- *header_name* フィールドには言語名が含まれています。
- *header_data_size* フィールドには、言語文字列テーブルのデータ サイズが含まれています。

### <a name="parameters"></a>パラメーター

- **root_address** メモリ内のバイナリ リソース データのアドレス
- **put_info** GX_LANGUAGE_HEADER 構造体の配列へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 成功しました
- **GX_INVALID_FORMAT** (0x24) バイナリ リソースが無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_LANGUAGE_HEADER language_info[4];

/* Specify address that binary resource data is located. */
GX_UBYTE    *root_address = 0x60000000;

status = gx_binres_language_info_load(root_address,
    language_info);
/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>参照

- gx_binres_language_count_get

## <a name="gx_binres_language_table_load"></a>gx_binres_language_table_load

言語テーブル リソースを読み込みます (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_binres_language_table_load(
    GX_UBYTE *root_address, 
    GX_UBYTE **returned_language_table);
```

### <a name="description"></a>説明

この非推奨の API を使用すると、アプリケーションで古い (リリース 5.6 より前の) バイナリ リソース データ ファイルから文字列テーブルデータを読み込むことができます。

新しいアプリケーションでは gx_binres_language_table_load_ext() を使用する必要があります。

このサービスでは、テーブル リソースへのポインターを含む言語テーブル構造体が構築されます。生成されたデータ構造体は "イン プレースで" リソース データを指しますが、リソース データはコピーしません。 リソース データは一般的なアクセス メモリの場所に配置する必要があり、このメモリの場所のベース アドレスがこの API に渡されます。

このサービスでは、言語テーブル構造体を保持するのに十分なサイズの実行時割り当てメモリ ブロックが必要です。そのため、このサービスを要求する前に、gx_system_memory_allocator_set API を 1 回呼び出す必要があります。

返される言語テーブルでは、1 つまたは複数の文字列テーブルが定義されます。各文字列テーブルには、リソース データ メモリ内の文字列リソースへのポインターが含まれます。

### <a name="parameters"></a>パラメーター

- **root_address** メモリ内のバイナリ リソース データのアドレス
- **returned _language_table** 読み込まれた言語テーブルへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 成功しました
- **GX_INVALID_FORMAT** (0x24) バイナリ リソースが無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_SYSTEM_MEMPRY_ERROR** (0x30) メモリ アロケーターまたは free 関数が定義されていません

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_UBYTE ***language_table = GX_NULL;

/* Specify address that binary resource data is located. */
GX_UBYTE *root_address = 0x60000000;

status = gx_binres_language_table_load(root_address,
                                        &language_table);

/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>参照

- gx_binres_language_table_load_ext

## <a name="gx_binres_language_table_load_ext"></a>gx_binres_language_table_load_ext

言語テーブル リソースを読み込みます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_binres_language_table_load_ext(
    GX_UBYTE *root_address, 
    GX_STRING **returned_language_table);
```

### <a name="description"></a>説明

このサービスでは、テーブル リソースへのポインターを含む言語テーブル構造体が構築されます。生成されたデータ構造体は "イン プレースで" リソース データを指しますが、リソース データはコピーしません。 リソース データは一般的なアクセス メモリの場所に配置する必要があり、このメモリの場所のベース アドレスがこの API に渡されます。

このサービスでは、言語テーブル構造体を保持するのに十分なサイズの実行時割り当てメモリ ブロックが必要です。そのため、このサービスを要求する前に、gx_system_memory_allocator_set API を 1 回呼び出す必要があります。

返される言語テーブルでは、1 つまたは複数の文字列テーブルが定義されます。各文字列テーブルには、リソース データ メモリ内の文字列リソースへのポインターが含まれます。

### <a name="parameters"></a>パラメーター

- **root_address** メモリ内のバイナリ リソース データのアドレス
- **returned _language_table** 読み込まれた言語テーブルへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 成功しました
- **GX_INVALID_FORMAT** (0x24) バイナリ リソースが無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_SYSTEM_MEMPRY_ERROR** (0x30) メモリ アロケーターまたは free 関数が定義されていません

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_STRING **language_table = GX_NULL;

/* Specify address that binary resource data is located. */
GX_UBYTE *root_address = 0x60000000;

status = gx_binres_language_table_load_ext(root_address,
                                            &language_table);

/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>参照

- gx_binres_theme_load

## <a name="gx_binres_theme_load"></a>gx_binres_theme_load

テーマ リソースを読み込みます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_binres_theme_load(
    GX_UBYTE *root_address, 
    INT theme_id, GX_THEME **returned_theme);
```

### <a name="description"></a>説明

このサービスでは、要求されたテーマのリソース テーブルへのポインターを含む GX_THEME 構造体が構築されます。 生成されたデータ構造体は "イン プレースで" リソース データを指しますが、リソース データはコピーしません。 そのため、リソース データは一般的なアクセス メモリの場所に配置する必要があり、このメモリの場所のベース アドレスがこの API に渡されます。

このサービスでは、テーマ テーブル構造体を保持するのに十分なサイズの実行時割り当てメモリ ブロックが必要です。そのため、このサービスを要求する前に、gx_system_memory_allocator_set API を 1 回呼び出す必要があります。

### <a name="parameters"></a>パラメーター

- **root_address** メモリ内のバイナリ リソース データのアドレス
- **theme_id** テーマの識別子
- **returned_theme** 読み込まれたテーマへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 成功しました
- **GX_INVALID_FORMAT** (0x24) バイナリ リソースが無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_VALUE** (0x22) テーマ ID が無効です
- **GX_SYSTEM_MEMORY_ERROR** (0x30) メモリ アロケーターまたは free 関数が定義されていません

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_CHAR *theme = GX_NULL;
GX_UBYTE *root_address = 0x60000000;
INT theme_id = 0;

status = gx_binres_theme_load(root_address, theme_id, &theme);

/* If status is GX_SUCCESS, the theme was successfully loaded. */
```

### <a name="see-also"></a>参照

- gx_binres_language_table_read

## <a name="gx_brush_default"></a>gx_brush_default
既定のブラシを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_brush_default(GX_BRUSH *brush);
```

### <a name="description"></a>説明

このサービスでは、現在のコンテキストのブラシがシステムの既定値に設定されます。

### <a name="parameters"></a>パラメーター
- **brush** ブラシ コントロール ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ブラシの定義が成功しました
- **GX_PTR_ERROR** (0x07) ブラシのポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/*Reset the brush to its default value. */
status = gx_brush_default(&my_brush);

/* If status is GX_SUCCESS the brush was successfully reset to its default value. */

```

### <a name="see-also"></a>参照

- gx_brush_define


## <a name="gx_brush_define"></a>gx_brush_define
ブラシを定義します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_brush_define(
    GX_BRUSH *brush, 
    GX_COLOR line_color, 
    GX_COLOR fill_color, 
    UINT style);
```

### <a name="description"></a>説明

このサービスでは、指定された線の色、塗りつぶしの色、スタイルを持つブラシが定義されます。

### <a name="parameters"></a>パラメーター

- **brush** ブラシ コントロール ブロックへのポインター
- **line_color** ブラシの線の色。 **付録 A** には事前定義済みの色が含まれています。 アプリケーションでは、カスタムの色も追加できることに注意してください。
- **fill_color** ブラシの塗りつぶしの色。 **付録 A** には事前定義済みの色が含まれています。 アプリケーションでは、カスタムの色も追加できることに注意してください。
- **style** ブラシのスタイル。 **付録 D** では、サポートされているブラシのスタイルが説明されています。 ブラシのスタイルは、ビットごとの OR 演算を使用して 1 つの変数に結合できます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ブラシの定義が成功しました
- **GX_PTR_ERROR** (0x07) ブラシのポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Define a brush. */
status = gx_brush_define(&my_brush, GX_COLOR_BLACK, GX_COLOR_BLACK,
                         GX_STYLE_BORDER_NONE);

/* If status is GX_SUCCESS the brush was successfully created. */
```

### <a name="see-also"></a>参照

- gx_brush_default

## <a name="gx_button_background_draw"></a>gx_button_background_draw

 ボタンの背景を描画します

###<a name="prototype"></a>プロトタイプ

```C
VOID gx_button_background_draw(GX_BUTTON *button);
```

### <a name="description"></a>説明

このサービスにより、ボタンの背景が描画されます。 この関数は通常、gx_button_draw 関数によって内部で呼び出されますが、カスタムの描画関数の記述を支援するためにアプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **button** ボタン コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
VOID custom_button_draw(GX_BUTTON *button)
{
    /* Draw button background. */
    gx_button_background_draw(button);

    /* Add custom drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)button);
}
```

### <a name="see-also"></a>参照

- gx_button_create、
- gx__button_deselect、
- gx__button_draw
- gx_button_event_process、
- gx__button_select
- gx_icon_button_create、
- gx__pixelmap_button_create
- gx_pixelmap_button_draw、
- gx__radio_button_create
- gx_radio_button_draw、
- gx__text_button_create
- gx_text_button_color_set、
- gx__text_button_draw

## <a name="gx_button_create"></a>gx_button_create

[作成] ボタン

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_button_create(
    GX_BUTTON *button, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    ULONG style, 
    USHORT button_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスでは、指定どおりのボタンが作成され、指定された親ウィジェットにそのボタンが関連付けられます。

### <a name="parameters"></a>パラメーター

- **button** ボタン コントロール ブロックへのポインター
- **name** ボタンの論理名
- **parent** ボタンの親ウィジェットへのポインター
- **style** ボタンのスタイル。 **付録 D** には、ウィジェット固有のスタイルだけでなく、すべてのウィジェット用に事前に定義されている一般的なスタイルが記載されています。
- **button_id** アプリケーションで定義された、ボタンの ID
- **size** ボタンのサイズ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ボタンの作成が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_BUTTON my_top_button;

/* Create a stop button. */
status = gx_button_create(&my_stop_button, "my stop button",
                            &my_parent_window,
                            GX_STYLE_BUTTON_TOGGLE,
                            MY_STOP_BUTTON_ID, &size);

/* If status is GX_SUCCESS the stop button was successfully created. */
```

### <a name="see-also"></a>参照

- gx_button_background_draw、
- gx_button_deselect、
- gx_button_draw
- gx_button_event_process、
- gx_button_select
- gx_radio_button_create、
- gx_radio_button_draw
- gx_icon_button_create、
- gx_pixelmap_button_create
- gx_pixelmap_button_draw、
- gx_text_button_create
- gx_text_button_color_set、
- gx_text_button_draw

## <a name="gx_button_deselect"></a>gx_button_deselect


ボタンを選択解除します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_button_deselect(
    GX_BUTTON *button, 
    GX_BOOL gen_event);
```

### <a name="description"></a>説明

このサービスでは、指定されたボタンの選択が解除され、ボタンのスタイルに応じてシグナル イベントが生成されます。


| ボタンのスタイル              | Signal                     |
|---------------------------|----------------------------|
| なし                      | GX_EVENT_CLICKED         |
| GX_STYLE_BUTTON_RADIO  | GX_EVENT_RADIO_DESELECT |
| GX_STYLE_BUTTON_TOGGLE | GX_EVENT_TOGGLE_OFF     |



### <a name="parameters"></a>パラメーター

- **button** ボタン コントロール ブロックへのポインター
- **gen_event** GX_TRUE の場合、ボタンのスタイルに応じて、ボタンによって GX_EVENT_CLICKED、GX_EVENT_DESELECT、または GX_EVENT_TOGGLE_OFFSET イベントが生成されます。 GX_FALSE の場合、通常行われている場合でも、ボタンによって上位レベルのイベントは生成されません。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ボタンの選択解除が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Deselect button. */
status = gx_button_deselect(&my_stop_button, GX_TRUE);

/* If status is GX_SUCCESS the stop button was successfully deselected. */
```

### <a name="see-also"></a>参照

- gx_button_background_draw、
- gx_button_create、
- gx_button_draw
- gx_button_event_process、
- gx_button_select
- gx_radio_button_create、
- gx_radio_button_draw
- gx_icon_button_create、
- gx_pixelmap_button_create
- gx_pixelmap_button_draw、
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_button_draw"></a>gx_button_draw

ボタンを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_button_draw(GX_BUTTON *button);
```

### <a name="description"></a>説明

このサービスでは、指定されたボタンが描画されます。 通常、この関数は GUIX キャンバスの更新メカニズムによって内部で呼び出されますが、カスタム ボタン ウイジェットのカスタム描画関数の実装を支援するためにアプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **button** ボタン コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom button draw function. */
VOID custom_button_draw(GX_BUTTON *button)
{
    /* Call default button draw. */
    gx_button_draw(button);

    /* Add custom drawing here. */
}

```

### <a name="see-also"></a>参照

- gx_button_background_draw、
- gx_button_create
- gx_button_deselect、
- gx_button_event_process、
- gx_button_select
- gx_radio_button_create、
- gx_radio_button_draw
- gx_icon_button_create、
- gx_pixelmap_button_create
- gx_pixelmap_button_draw、
- gx_text_button_create
- gx_text_button_color_set、
- gx_text_button_draw

## <a name="gx_button_event_process"></a>gx_button_event_process


ボタン イベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_button_event_process(
    GX_BUTTON *button, 
    GX_EVENT *event);
```

### <a name="description"></a>説明

このサービスでは、指定されたボタンのイベントが処理されます。

### <a name="parameters"></a>パラメーター

- **button** ボタン コントロール ブロックへのポインター
- **event_ptr** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ボタンのイベント処理が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Call generic button event processing as part of custom event processing function. */

UINT custom_button_event_process(GX_BUTTON *button,
                                 GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default button
            event processing */
        status = gx_button_event_process(button, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>参照

- gx_button_background_draw、
- gx_button_create
- gx_button_deselect、
- gx_button_draw、
- gx_button_select
- gx_radio_button_create、
- gx_radio_button_draw
- gx_icon_button_create、
- gx_pixelmap_button_create
- gx_pixelmap_button_draw、
- gx_text_button_create
- gx_text_button_color_set、
- gx_text_button_draw

## <a name="gx_button_select"></a>gx_button_select

[選択] ボタン

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_button_select(GX_BUTTON *button);
```

### <a name="description"></a>説明

このサービスでは、指定されたボタンが選択され、ボタンのスタイルに応じてシグナル イベントが生成されます。

オプション ボタン グループの兄弟を選択解除します。

| ボタンのスタイル                       | Signal                   |
|------------------------------------|--------------------------|
| GX_STYLE_BUTTON_RADIO           | GX_EVENT_RADIO_SELECT |
| GX_STYLE_BUTTON_EVENT_ON_PUSH | GX_EVENT_CLICKED       |
| GX_STYLE_BUTTON_TOGGLE          | GX_EVENT_TOGGLE_ON    |


### <a name="parameters"></a>パラメーター

- **button** ボタン コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ボタンの選択が成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Select button. */
status = gx_button_select(&my_stop_button);

/* If status is GX_SUCCESS the stop button was successfully selected. */
```

### <a name="see-also"></a>参照

- gx_button_background_draw、
- gx_button_create
- gx_button_deselect、
- gx_button_draw、
- gx_button_event_process
- gx_radio_button_create、
- gx_radio_button_draw
- gx_icon_button_create、
- gx_pixelmap_button_create
- gx_pixelmap_button_draw、
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_canvas_alpha_set"></a>gx_canvas_alpha_set

キャンバスのアルファブレンド値を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_alpha_set(
    GX_CANVAS *canvas, 
    GX_UBYTE alpha);
```

### <a name="description"></a>説明

このサービスでは、指定されたキャンバスのアルファブレンド値が設定されます。 キャンバスのアルファ値は 0 (透明) から 255 (完全に不透明) までの範囲にすることができます。

オーバーレイ キャンバスをブレンドするには、ハードウェアのグラフィックス レイヤーのサポート、または合成キャンバスを作成することによるソフトウェア サポートが必要です。

キャンバス ブレンドに対するハードウェア サポートは、キャンバスのアルファ値を設定する前に gx_canvas_hardware_layer_bind() API を呼び出して有効にします。 キャンバスがハードウェアのグラフィックス レイヤーにバインドされている場合、gx_canvas_alpha_set() API を呼び出すと、ハードウェアのグラフィックス レイヤーのブレンド サービスが直接起動されます。

キャンバスのブレンドに対するソフトウェア サポートを利用するには、アプリケーションで GX_CANVAS_COMPOSITE スタイルのキャンバスを作成する必要があります。その中で、最終的な表示の前に他のすべての管理対象キャンバスが合成されます。 キャンバスのブレンドに対するソフトウェア サポートは、16 bpp 以上の色深度のディスプレイ ドライバーを使用して実行している場合にのみ提供されます。

### <a name="parameters"></a>パラメーター

- **canvas** キャンバス コントロール ブロックへのポインター
- **alpha** 0 (透明) から 255 (不透明) までの範囲のアルファブレンド値。

### <a name="return--values"></a>戻り値

- **GX_SUCCESS** (0x00) アルファブレンド値の設定が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_ERROR** (0x20) キャンバスが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the alpha-blend value of “my_canvas”. */
status = gx_canvas_alpha_set(&my_canvas, GX_ALPHA_VALUE_OPAQUE);

/* If status is GX_SUCCESS the alpha-blend value was successfully set. */
```

### <a name="see-also"></a>参照

- gx_canvas_create、
- gx_canvas_drawing_complete
- gx_canvas_drawing_initiate、
- gx_canvas_offset_set
- gx_canvas_shift、
- gx_canvas_hardware_layer_bind、
- gx_canvas_show
- gx_canvas_hide

## <a name="gx_canvas_arc_draw"></a>gx_canvas_arc_draw

円弧を描画します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_arc_draw(
    INT xcenter, 
    INT ycenter, 
    UINT r,
    INT start_angle, 
    INT end_angle);
```

### <a name="description"></a>説明

このサービスでは、現在のブラシを使用して、キャンバスに円弧が描画されます。 この円弧はキャンバスの無効な領域にクリップされます。 このサービスでは GX_ARC_DRAWING_SUPPORT を定義する必要があります。

### <a name="parameters"></a>パラメーター

- **xcenter** 円弧の中心の X 位置
- **ycenter** 円弧の中心の Y 位置
- **r** 円弧の半径
- **start_angle** 円弧の開始角度
- **end_angle** 円弧の終了角度

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 円弧の描画が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_VALUE** (0x22) 値が無効です
- **GX_INVALID_CONTEXT** (0x06) 開いている描画コンテキストがありません

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Draw a circle arc from 0 degree to 90 degree in clockwise. */
status = gx_canvas_arc_draw(100, 100, 50, 0, 90);

/* If status is GX_SUCCESS the arc has been drawn on “my_canvas”. */
```

### <a name="see-also"></a>参照

- gx_canvas_block_move、
- gx_canvas_circle_draw
- gx_display_create、
- gx_canvas_ellipse_draw
- gx_canvas_line_draw、
- gx_canvas_pie_draw
- gx_canvas_pixelmap_draw、
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw、
- gx_canvas_text_draw

## <a name="gx_canvas_block_move"></a>gx_canvas_block_move

キャンバス ピクセルのブロックを移動します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_block_move(GX_RECTANGLE *block,
    GX_VALUE x_shift, GX_VALUE y_shift, GX_RECTANGLE *dirty);
```

### <a name="description"></a>説明

このサービスにより、キャンバスのピクセル データのブロックが、指定された方向に移動されます。 このサービスは、高速スクロールを実行するために GUIX によって内部で使用されますが、アプリケーション ソフトウェアでも使用される場合があります。

### <a name="parameters"></a>パラメーター

- **block** 移動する領域の座標
- **x_shift** X 軸でシフトするピクセル数
- **y_shift** Y 軸でシフトするピクセル数
- **dirty** ブロックの移動が成功した場合、この関数では、まだダーティである移動元の四角形の部分がこのパラメーターの呼び出し元に返されます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ブロックの移動が成功しました
- **GX_FAILURE** (0x10) ブロックの移動が失敗しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
GX_RECTANGLE invalid;
GX_RECTANGLE move;

/* define 100 x 100 pixel rectangle */
gx_utility_rectangle_define(&move, 0, 0, 99, 99);

/* Move this rectangle 10 pixels to the right”. */
status = gx_canvas_block_move(&move, 10, 0, &invalid);

/* If status is GX_SUCCESS, then ‘invalid’ marks the area that needs to be redrawn after the block move. */

```

### <a name="see-also"></a>参照

- gx_canvas_arc_draw
- gx_canvas_circle_draw、
- gx_display_create
- gx_canvas_ellipse_draw、
- gx_canvas_line_draw
- gx_canvas_pie_draw、
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile、
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw、
- gx_canvas_text_draw

## <a name="gx_canvas_circle_draw"></a>gx_canvas_circle_draw

円を描画します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_circle_draw(
    INT xcenter, 
    INT ycenter, 
    UINT r);
```

### <a name="description"></a>説明

このサービスでは、現在のブラシを使用して、キャンバスに円が描画されます。 この円はキャンバスの無効な領域にクリップされます。 このサービスでは GX_ARC_DRAWING_SUPPORT を定義する必要があります。

### <a name="parameters"></a>パラメーター

- **xcenter** 円の中心の X 座標
- **ycenter** 円の中心の Y 座標
- **r** 円の半径

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 円の描画が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_VALUE** (0x22) 円の半径が無効です
- **GX_INVALID_CONTEXT** (0x06) 開いている描画コンテキストがありません

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C

/* Draw a circle of radius 10 centered at (100, 100). */
status = gx_canvas_circle_draw(100, 100, 50);

/* If status is GX_SUCCESS the circle has been drawn on “my_canvas”. */

```

### <a name="see-also"></a>参照

- gx_canvas_arc_draw
- gx_canvas_block_move、
- gx_display_create
- gx_canvas_ellipse_draw、
- gx_canvas_line_darw
- gx_canvas_pie_draw、
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile、
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw、
- gx_canvas_text_draw


## <a name="gx_canvas_create"></a>gx_canvas_create

キャンバスを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_create(
    GX_CANVAS *canvas, 
    GX_CONST GX_CHAR *name,
    GX_DISPLAY *display, 
    UINT type, 
    UINT width, 
    UINT height,
    GX_COLOR *memory_area, 
    ULONG memory_size);
```

### <a name="description"></a>説明

このサービスでは、指定されたプロパティと関連付けられたメモリを使用してキャンバスが作成されます。

### <a name="parameters"></a>パラメーター

- **canvas** キャンバス コントロール ブロックへのポインター
- **name** キャンバスの論理名
- **display** 以前に作成された画面へのポインター
- **type** キャンバスの種類。キャンバスの種類には以下が含まれます。
- **GX_CANVAS_SIMPLE:** オフスクリーンの描画に使用されるメモリ キャンバス。
- **GX_CANVAS_MANAGED:** 合成作成プロセスの一環として、または単一キャンバス アーキテクチャのバッファー切り替え操作の一環として、アクティブな画面に自動的にフラッシュされるキャンバス。
- **GX_CANVAS_VISIBLE:** このフラグを使用すると、キャンバスの描画内容を失わずにキャンバスをオンにしたりオフにしたりすることができます。
- **GX_CANVAS_MODIFIED:** 将来使用するために予約されています。
- **GX_CANVAS_COMPOSITE:** このフラグは、複数の管理対象キャンバスを合成して合成キャンバスにする、マルチキャンバス システムを構成するときにアプリケーションによって使用されます。その合成は、ハードウェア フレーム バッファーに送られます。
- **width** ピクセル単位での幅
- **height** ピクセル単位での高さ
- **memory_area** キャンバスのメモリ領域。 この値は
- キャンバスの作成時に **GX_NULL** の場合があり、
- **また**、後で gx_canvas_memory_define を使用して初期化されます
- **memory_size** メモリ領域のサイズ (バイト単位)。または、キャンバスの作成後にキャンバス メモリが定義される場合は 0。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) キャンバスの作成が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_CANVAS_SIZE** (0x1c) キャンバス コントロール ブロックのサイズが無効です
- **GX_INVALID_TYPE** (0x1B) キャンバスの種類が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Define global canvas memory area. */
GX_COLOR my_canvas_memory[272*480];

…

/* Create “my_canvas”. */
status = gx_canvas_create(&my_canvas, "my canvas", &my_display,
                    (GX_CANVAS_MANAGED | GX_CANVAS_VISIBLE),
                    272, 480,
                    my_canvas_memory,
                    sizeof(default_canvas_memory));

/* If status is GX_SUCCESS the 272 x 480 canvas was successfully created. */
```

### <a name="see-also"></a>参照

- gx_canvas_delete、
- gx_canvas_hardware_layer_bind
- gx_canvas_memory_define

## <a name="gx_canvas_delete"></a>gx_canvas_delete

キャンバスを削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_delete(GX_CANVAS *canvas);
```

### <a name="description"></a>説明

このサービスにより、キャンバスが削除されます。 キャンバスは、GUIX によって管理されているキャンバスの内部リンク リストから削除されます。

### <a name="parameters"></a>パラメーター

- **canvas** キャンバス コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) キャンバスの作成が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_CANVAS** (0x20) キャンバスが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Delete “my_canvas”. */
status = gx_canvas_delete (&my_canvas);

/* If status is GX_SUCCESS my_canvas was deleted. */
```

### <a name="see-also"></a>参照

- gx_canvas_alpha_set、
- gx_canvas_drawing_complete
- gx_canvas_create、
- gx_canvas_drawing_initiate
- gx_canvas_offset_set、
- gx_canvas_shift

## <a name="gx_canvas_drawing_complete"></a>gx_canvas_drawing_complete

キャンバスの描画を完了します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_drawing_complete(
    GX_CANVAS *canvas, 
    GX_BOOL flush);
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたキャンバスでアプリケーションの描画が完了したことを GUIX に知らせることができます。

アプリケーションでは、このサービスを使用してキャンバスへの即時描画を強制することができます。 これにより、システム メモリのアーキテクチャに応じて、表示されているフレーム バッファーにキャンバスがフラッシュされたり、バーガー トグル操作がトリガーされたりします。

このサービスは、gx_canvas_drawing_initiate() で始まった描画シーケンスを終了する場合にのみアプリケーションによって呼び出される必要があります。

### <a name="parameters"></a>パラメーター

- **canvas** キャンバス コントロール ブロックへのポインター
- **flush** **_GX_TRUE_** の場合、キャンバスの変更が画面にフラッシュされます

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 描画が正常に完了しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Complete drawing on “my_canvas” and flush to display. */
status = gx_canvas_drawing_complete(&my_canvas, GX_TRUE);

/* If status is GX_SUCCESS the canvas drawing was successfully completed. */
```


### <a name="see-also"></a>参照

- gx_canvas_alpha_set、
- gx_canvas_create
- gx_canvas_drawing_initiate、
- gx_canvas_offset_set
- gx_canvas_shift

## <a name="gx_canvas_drawing_initiate"></a>gx_canvas_drawing_initiate

キャンバスの描画を開始します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_drawing_initiate(
    GX_CANVAS *canvas,
    GX_WIDGET *who, 
    GX_RECTANGLE *dirty_area);
```

### <a name="description"></a>説明

このサービスでは、指定されたキャンバスへの描画が開始されます。 このサービスは、キャンバスを更新する必要があるときに、GUIX によって自動的に実行される遅延描画操作の一部として、内部で呼び出されます。 ただし、アプリケーションでは、最初に gx_canvas_drawing_inititate を呼び出し、次に目的の描画関数を呼び出し、その後に gx_canvas_drawing_complete() を呼び出すことによって、GUIX 遅延描画アルゴリズムをバイパスして、キャンバスへの即時および直接的な描画を実行できます。

### <a name="parameters"></a>パラメーター

- **canvas** キャンバス コントロール ブロックへのポインター
- **who** 呼び出し元のウィジェット コントロール ブロックへのポインター。 このパラメーターを使用して、描画クリッピングを初期化し、後続の描画操作のためのパラメーターを表示します。
- **dirty_area** 描画する領域。 このパラメーターは呼び出し元によって渡され、呼び出し元がすべての描画操作をクリップしたい領域を示します。 通常これは、以前にはダーティとしてマークされていた領域ですが、呼び出し元はクリッピング領域を自由に拡張または縮小できます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 描画が正常に開始しました
- **GX_DRAW_NESTING_EXCEEDED** (0x05) 入れ子の最大数を超えています
- **GX_NO_VIEW** (0x03) 呼び出し元のビューポートがありません
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_CANVAS** (0x20) キャンバスが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Initiate drawing on “my_canvas”, my_widget.gx_widget_size
specify the area the application wants GUIX to redraw. */
status = gx_canvas_drawing_initiate(&my_canvas, &my_widget,
    &my_widget.gx_widget_size);

/* If status is GX_SUCCESS the canvas drawing was successfully initiated. */
```

### <a name="see-also"></a>参照

- gx_canvas_alpha_set、
- gx_canvas_create
- gx_canvas_drawing_complete、
- gx_canvas_offset_set
- gx_canvas_shift


## <a name="gx_canvas_ellipse_draw"></a>gx_canvas_ellipse_draw

楕円を描画します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_ellipse_draw(
    INT xcenter, 
    INT ycenter, 
    INT a, 
    dINT b);
```

### <a name="description"></a>説明

このサービスでは、現在のブラシを使用して、キャンバスに楕円が描画されます。 この楕円はキャンバスの無効な領域にクリップされます。 このサービスでは GX_ARC_DRAWING_SUPPORT を定義する必要があります。

### <a name="parameters"></a>パラメーター

- **xcenter** 楕円の中心の X 座標
- **ycenter** 楕円の中心の Y 座標
- **a** 軌道長半径の長さ
- **b** 軌道短半径の長さ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 円の描画が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_VALUE** (0x22) 値が無効です
- **GX_INVALID_CONTEXT** (0x06) 開いている描画コンテキストがありません

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Draw an ellipse of semi-major radius 100, semi-minor radius 50
    and centered at (200, 200). */
status = gx_canvas_ellipse_draw(200, 200, 100, 50);

/* If status is GX_SUCCESS the ellipse has been drawn on
    “my_canvas”. */
```

### <a name="see-also"></a>参照

- gx_canvas_arc_draw、
- gx_canvas_block_move
- gx_canvas_circle_draw、
- gx_display_create、
- gx_canvas_line_darw
- gx_canvas_pie_draw、
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile、
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw、
- gx_canvas_text_draw

## <a name="gx_canvas_hardware_layer_bind"></a>gx_canvas_hardware_layer_bind

キャンバスをハードウェアのグラフィックス レイヤーにバインドします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_hardware_layer_bind(
    GX_CANVAS *canvas, 
    INT layer);
```

### <a name="description"></a>説明

このサービスでは、GUIX 描画キャンバスがハードウェアのグラフィックス レイヤーにバインドされます。 このサービスは、ハードウェアのグラフィックス レイヤーを複数サポートするハードウェア デバイスでのみ必要です。

キャンバスをハードウェアのグラフィックス レイヤーにバインドすると、gx_canvas_show()、gx_canvas_hide()、gx_canvas_alpha_set()、gx_canvas_offset_set() の 各 API がハードウェアのディスプレイ ドライバー サービスによって直接実装されます。

ハードウェアのディスプレイ ドライバーで複数のグラフィックス レイヤーがサポートされていない場合、このサービスは失敗し、GX_INVALID_DISPLAY が返されます。

### <a name="parameters"></a>パラメーター

- **canvas** ハードウェアに実装されるキャンバス
- **layer** ハードウェアのグラフィックス レイヤー

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) バインドが成功しました
- **GX_INVALID_DISPLAY** (0x1D) ディスプレイ レイヤー サービスが定義されていません
- **GX_PTR_ERROR** (0x17) ポインターが無効です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_CANVAS** (0x20) キャンバスが無効です
- **GX_NOT_SUPPORTED** (0x28) サポートされていません

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Binds the canvas to the hardware graphics layer 1. */
status = gx_canvas_hardware_layer_bind(&my_canvas, 1);

/* If status is GX_SUCCESS, the drawing canvas is bound to the
    hardware graphics. */
```

### <a name="see-also"></a>参照

- gx_canvas_create、
- gx_canvas_memory_define

## <a name="gx_canvas_hide"></a>gx_canvas_hide

キャンバスを隠して非表示にします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_hide(GX_CANVAS *canvas);
```

### <a name="description"></a>説明

このサービスにより、GUIX キャンバスが非表示になります。 キャンバスが gx_canvas_hardware_layer_bind() を使用してハードウェアのグラフィックス レイヤーにバインドされている場合、このサービスはハードウェア サポートを使用して実装されます。

### <a name="parameters"></a>パラメーター

- **canvas** 非表示にするキャンバス

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 非表示が成功しました
- **GX_INVALID_CANVAS** (0x20) キャンバスが無効です
- **GX_PTR_ERROR** (0x17) ポインターが無効です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Make my_canvas invisible. */
status = gx_canvas_hide(&my_canvas);

/* If status is GX_SUCCESS, the canvas has been hidden. */

```

### <a name="see-also"></a>参照

- gx_canvas_create、
- gx_canvas_drawing_complete
- gx_canvas_drawing_initiate、
- gx_canvas_offset_set
- gx_canvas_shift、
- gx_canvas_hardware_layer_bind、
- gx_canvas_show
- gx_canvas_hide

## <a name="gx_canvas_line_draw"></a>gx_canvas_line_draw

線を描画します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_line_draw(
    GX_VALUE x_start, 
    GX_VALUE y_start,
    GX_VALUE x_end, 
    GX_VALUE y_end);
```

### <a name="description"></a>説明

このサービスでは、現在のブラシを使用して、キャンバスに線が描画されます。 この線はキャンバスの無効な領域にクリップされます。

### <a name="parameters"></a>パラメーター

- **x_start** 線の開始の X 位置
- **y_end** 線の開始の Y 位置
- **x_start** 線の終了の X 位置
- **y_end** 線の終了の Y 位置

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 線の描画が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_CONTEXT** (0x06) 開いている描画コンテキストがありません
- **GX_INVALID_WIDTH** (0x1E) ブラシの幅が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Draw line on canvas. */
status = gx_canvas_line_draw(0, 1, 320, 480);

/* If status is GX_SUCCESS, the line has been drawn to canvas. */
```

### <a name="see-also"></a>参照

- gx_canvas_arc_draw、
- gx_canvas_block_move
- gx_canvas_circle_draw、
- gx_display_create
- gx_canvas_ellipse_draw、
- gx_canvas_pie_draw
- gx_canvas_pixelmap_draw、
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw、
- gx_canvas_rectangle_draw
- gx_canvas_text_draw

## <a name="gx_canvas_memory_define"></a>gx_canvas_memory_define

キャンバス メモリを定義します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_memory_define(
    GX_CANVAS *canvas, 
    GX_COLOR *memory,
    ULONG memsize);
```

### <a name="description"></a>説明

このサービスを使用して、キャンバスの作成後にキャンバス メモリ アドレスを割り当てることができます。

### <a name="parameters"></a>パラメーター

- **canvas** 以前に作成したキャンバスへのポインター
- **memory** キャンバス メモリ アドレス
- **memsize** キャンバス メモリ ブロックのサイズ (バイト単位)

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 割り当てが成功しました
- **GX_INVALID_CANVAS** (0x20) コントロール ブロックが無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Assign canvas memory block. */
status = gx_canvas_memory_define(canvas,
    (GX_COLOR *) DRAM_MEMORY,
    (640 * 480 * 2));

/* If status is GX_SUCCESS, the canvas memory pointer has be
reassigned. */

```

### <a name="see-also"></a>参照

- gx_canvas_create、
- gx_canvas_hardware_layer_bind

## <a name="gx_canvas_mouse_define"></a>gx_canvas_mouse_define

マウス カーソルの画像を定義します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_mouse_define(GX_CANVAS *canvas,
    GX_MOUSE_CURSOR_INFO *info);
```

### <a name="description"></a>説明

このサービスは、指定されたキャンバスのマウス情報を定義します。 このサービスでは GX_MOUSE_SUPPORT を定義する必要があります。

### <a name="parameters"></a>パラメーター

- **canvas** キャンバス コントロール ブロックへのポインター
- **info** マウス カーソル情報へのポインター。 **付録 I** には GX_MOUSE_CURSOR_INFO 構造体の定義が含まれています。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) マウス情報の設定が成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set mouse cursor info. */
GX_MOUSE_CURSOR_INFO mouse_cursor;
mouse_cursor.gx_mouse_cursor_image_id = GX_PIXELMAP_ID_MOUSE;
mouse_cursor.gx_mouse_cursor_hotspot_x = 0;
mouse_cursor.gx_mouse_cursor_hotspot_y = 0;

status = gx_canvas_mouse_define(&my_canvas, &mouse_cursor);

/* If status is GX_SUCCESS the mouse info of “my_canvas” has been
set successfully. */

```

### <a name="see-also"></a>参照

- gx_canvas_mouse_show、
- gx_canvas_mouse_hide

## <a name="gx_canvas_mouse_hide"></a>gx_canvas_mouse_hide


マウス カーソルをオフにします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_mouse_hide(GX_CANVAS *canvas);
```

### <a name="description"></a>説明

このサービスは、指定されたキャンバスでマウス カーソルを非表示にします。 このサービスでは GX_MOUSE_SUPPORT を定義する必要があります。

### <a name="parameters"></a>パラメーター

- **canvas** キャンバス コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) マウス カーソルの非表示が成功しました
- **GX_FAILURE** (0x10) マウス カーソルの非表示が失敗しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です


### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Hide the mouse cursor. */
status = gx_canvas_mouse_hide(&my_canvas);

/* If status is GX_SUCCESS the mouse cursor of “my_canvas” has been
hidden successfully. */

```

### <a name="see-also"></a>参照

- gx_canvas_mouse_show、
- gx_canvas_mouse_define

## <a name="gx_canvas_mouse_show"></a>gx_canvas_mouse_show


マウス カーソルをオンにします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_mouse_show(GX_CANVAS *canvas);
```

### <a name="description"></a>説明

このサービスは、指定されたキャンバスでマウス カーソルを表示します。 このサービスでは GX_MOUSE_SUPPORT を定義する必要があります。 このサービスが要求される前に、gx_canvas_mouse_define API を呼び出して、マウス カーソルの画像を定義する必要があります。

### <a name="parameters"></a>パラメーター

- **canvas** キャンバス コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) マウス情報の設定が成功しました
- **GX_FAILURE** (0x10) マウス カーソルの表示が失敗しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Make mouse cursor hidden ”. */
status = gx_canvas_mouse_show(&my_canvas);

/* If status is GX_SUCCESS the mouse of “my_canvas” has been
hidden successfully. */
```

### <a name="see-also"></a>参照

- gx_canvas_mouse_show、
- gx_canvas_mouse_define

## <a name="gx_canvas_offset_set"></a>gx_canvas_offset_set


キャンバスの X、Y 表示オフセットを割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_offset_set(
    GX_CANVAS *canvas,
    GX_VALUE x, 
    GX_VALUE y);
```

### <a name="description"></a>説明

このサービスは、指定されたキャンバスに X、Y 表示オフセットを割り当てます。 これは、表示されているフレーム バッファーにキャンバスが合成される位置を制御し、多くの場合、キャンバスが物理的な画面より小さい場合に使用されます。

キャンバスが gx_canvas_hardware_layer_bind() API を使用してハードウェアのグラフィックス レイヤーにバインドされている場合、gx_canvas_offset_set サービスがハードウェア サポートを使用して直接実装されます。

### <a name="parameters"></a>パラメーター

- **canvas** キャンバス コントロール ブロックへのポインター
- **x** オフセットの X 座標
- **y** オフセットの Y 座標

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) オフセットの割り当てが成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_CANVAS** (0x20) キャンバスが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set display offset for “my_canvas”. */
status = gx_canvas_offset_set(&my_canvas, 20, 30);

/* If status is GX_SUCCESS the canvas drawing is now offset from
position 20,30. */
```

### <a name="see-also"></a>参照

- gx_canvas_alpha_set、
- gx_canvas_create
- gx_canvas_drawing_complete、
- gx_canvas_initiate、
- gx_canvas_shift
- gx_canvas_show、
- gx_canvas_hide、
- gx_canvas_hardware_layer_bind

## <a name="gx_canvas_pie_draw"></a>gx_canvas_pie_draw


円を描画します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_pie_draw(
    INT xcenter, 
    INT ycenter,
    UINT r, 
    INT start_angle, 
    INT end_angle);
```

### <a name="description"></a>説明

このサービスは、現在の描画コンテキスト ブラシを使用してキャンバスに円を描画します。 この円はキャンバスの無効な領域にクリップされます。 このサービスでは、構成オプション GX_ARC_DRAWING_SUPPORT を定義する必要があります。

### <a name="parameters"></a>パラメーター

- **xcenter** 円の中心の X 位置
- **ycenter** 円の中心の Y 位置
- **r** 円の半径
- **start_angle** 円の開始角度
- **end_angle** 円の終了角度

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 円弧の描画が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_VALUE** (0x22) 値が無効です
- **GX_INVALID_CONTEXT** (0x06) 開いている描画コンテキストがありません

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Draw a pie from 0 degree to 90 degree in clockwise. */
status = gx_canvas_pie_draw(100, 100, 50, 0, 90);

/* If status is GX_SUCCESS the pie has been drawn to canvas. */
```

### <a name="see-also"></a>参照

- gx_canvas_arc_draw、
- gx_canvas_block_move
- gx_canvas_circle_draw、
- gx_display_create
- gx_canvas_ellipse_draw、
- gx_canvas_line_draw
- gx_canvas_pixelmap_draw、
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw、
- gx_canvas_rectangle_draw
- gx_canvas_text_draw

## <a name="gx_canvas_pixel_draw"></a>gx_canvas_pixel_draw


ピクセルを描画します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_pixel_draw(GX_POINT position);
```

### <a name="description"></a>説明

このサービスは、現在の描画コンテキスト ブラシの線の色を使用してキャンバスにピクセルを描画します。 構成オプション GX_BRUSH_ALPHA_SUPPORT が定義されている場合は、ピクセルをブレンドします。それ以外の場合は、完全に不透明になるようにピクセルを描画します。

- **point** 描画するピクセルの X、Y 位置

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ピクセルマップの描画が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_CONTEXT** (0x06) 開いている描画コンテキストがありません

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_POINT point; /* the x,y position you want to draw to */
GX_RECTANGLE drawto; /* the rectangle bounding your drawing */
GX_CANVAS *mycanvas; /* the canvas you want to draw to */

/* calculate 1x1 pixel drawing area: */
gx_utility_rectangle_define(&drawto,
    point.gx_point_x, point.gx_point_y,
    point.gx_point_x, point.gx_point_y);

/* get my canvas: */
gx_widget_canvas_get(win, &mycanvas);

/* open my canvas for drawing: */
gx_canvas_drawing_initiate(mycanvas, win, &drawto);

/* setup my brush colors. Use any color ID in your resources: */
gx_context_line_color_set(GX_COLOR_ID_WINDOW_BORDER);

/* draw a pixel: */
status = gx_canvas_pixel_draw(point);

/* close the canvas: */
gx_canvas_drawing_complete(mycanvas, GX_TRUE);

/* If status is GX_SUCCESS, the pixel was successfully drawn to mycanvas. */
```

### <a name="see-also"></a>参照

- gx_canvas_block_move、
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_blend

## <a name="gx_canvas_pixelmap_blend"></a>gx_canvas_pixelmap_blend

ピクセルマップをブレンドします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_pixelmap_blend(
    GX_VALUE x_position,
    GX_VALUE y_position, 
    GX_PIXELMAP *pixelmap, 
    GX_UBYTE alpha);
```

### <a name="description"></a>説明

このサービスは、ピクセルマップをキャンバスの背景とブレンドします。 ブレンド比率は、呼び出し元によって指定されます。 アルファ値は 0 (完全に透明) から 255 (完全に不透明) までの範囲にすることができます。 ピクセルマップには、内部アルファ チャネルを含めることもできます。これは、入力されたブレンド値と結合されます。 このサービスは、16 bpp 以上の色深度で実行されているディスプレイ ドライバーでのみサポートされます。

### <a name="parameters"></a>パラメーター

- **x_start** ピクセルマップの開始の X 位置
- **y_end** ピクセルマップの開始の Y 位置
- **pixelmap** ピクセルマップへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ピクセルマップの描画が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_NOT_SUPPORTED** (0x28) サポートされていません
- **GX_INVALID_CONTEXT** (0x06) 開いている描画コンテキストがありません

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Draw pixelmap on active canvas */

GX_PIXELMAP *map;
gx_system_pixelmap_get(ID_MY_PIXELMAP, &map);

status = gx_canvas_pixelmap_blend(10, 20, map, 128);

/* If status is GX_SUCCESS the pixelmap has been blended onto the current canvas. */
```

### <a name="see-also"></a>参照

- gx_canvas_block_move、
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_draw

## <a name="gx_canvas_pixelmap_draw"></a>gx_canvas_pixelmap_draw

ピクセルマップを描画します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_pixelmap_draw(
    GX_VALUE x_position, 
    GX_VALUE y_position,
    GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>説明

このサービスは、キャンバスにピクセルマップを描画します。

### <a name="parameters"></a>パラメーター

- **x_start** ピクセルマップの開始の X 位置
- **y_end** ピクセルマップの開始の Y 位置
- **pixelmap** ピクセルマップへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ピクセルマップの描画が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_CONTEXT** (0x06) 開いている描画コンテキストがありません

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Draw pixelmap on canvas. */
status = gx_canvas_pixelmap_draw(10, 20, &my_pixelmap);

/* If status is GX_SUCCESS the pixelmap “my_pixelmap” has been drawn. */
```

### <a name="see-also"></a>参照

- gx_canvas_block_move、
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_blend

## <a name="gx_canvas_pixelmap_get"></a>gx_canvas_pixelmap_get

キャンバスのピクセルマップを取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_pixelmap_get(GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>説明

このサービスは、キャンバス データを指す GX_PIXELMAP 構造体を返します。 ピクセルマップ形式は、現在の表示色の形式に設定されます。

### <a name="parameters"></a>パラメーター

- **pixelmap** 返されたピクセルマップ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ピクセルマップの取得が成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Draw pixelmap on active canvas */

GX_PIXELMAP *map;

status = gx_canvas_pixelmap_get(map);

/* If status is GX_SUCCESS the pixelmap has been retrieved. */
```

### <a name="see-also"></a>参照

- gx_canvas_pixelmap_blend、
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_draw

## <a name="gx_canvas_pixelmap_rotate"></a>gx_canvas_pixelmap_rotate


回転したピクセルマップを描画します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_pixelmap_rotate(
    GX_VALUE x_position, 
    GX_VALUE y_position,
    GX_PIXELMAP *pixelmap, 
    INT angle,
    INT rot_cx, 
    INT rot_cy);
```

### <a name="description"></a>説明

このサービスは、指定された角度でピクセルマップを回転し、回転が行われるときに、ピクセルマップをキャンバスに直接レンダリングします。 このサービスは、回転の出力がキャンバス メモリに直接レンダリングされ、回転したピクセルマップが呼び出し元に返されないという点で gx_utility_pixelmap_rotate とは異なります。

このサービスが gx_utility_pixelmap_rotate より優れている点は、回転したピクセルマップを保持するために追加のメモリが必要ないことです。 欠点は、ピクセルマップを描画するたびに回転コードを実行しなければならないことです。

クリッピングとビューポートの検証は、回転したピクセルマップのレンダリング中に実施されます。

### <a name="parameters"></a>パラメーター

- **x_position** ピクセルマップの開始 X 位置
- **y_position** ピクセルマップの開始 Y 位置
- **pixelmap** ピクセルマップへのポインター
- **angle** 回転する角度
- **rot_cx** 回転の中心の X 座標。 この値が -1 に設定されている場合、画像の中心が回転の中心として使用されます。
- **rot_cy** 回転の中心の Y 座標。 この値が -1 に設定されている場合、画像の中心が回転の中心として使用されます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ピクセルマップの描画が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_CONTEXT** (0x06) 開いている描画コンテキストがありません

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* rotate “src_pixelmap” by 30 degree in clockwise direction and draw in on canvas. */
status = gx_canvas_pixelmap_rotate(10, 20, &my_pixelmap, 30,
    -1, -1);

/* If status is GX_SUCCESS the rotated pixelmap “my_pixelmap” has been drawn. */
```

### <a name="see-also"></a>参照

- gx_canvas_block_move、
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_tile、
- gx_canvas_pixelmap_blend

## <a name="gx_canvas_pixelmap_tile"></a>gx_canvas_pixelmap_tile

ピクセルマップをタイル表示します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_pixelmap_tile(
    GX_RECTANGLE *fill,
    GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>説明

このサービスは、要求されたピクセルマップを使用して、キャンバス内の四角形を塗りつぶします。

### <a name="parameters"></a>パラメーター

- **fill** ピクセルマップを使用してタイル表示する領域
- **pixelmap** ピクセルマップへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ピクセルのタイル表示が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_CONTEXT** (0x06) 開いている描画コンテキストがありません
- **GX_INVALID_VALUE** (0x22) 塗りつぶしのサイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Tile pixelmap on canvas */
status = gx_canvas_pixelmap_tile(&tile_area, &my_pixelmap);

/* If status is GX_SUCCESS the pixelmap “my_pixelmap” has been tiled on canvas */
```

### <a name="see-also"></a>参照

- gx_canvas_block_move、
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_blend、
- gx_canvas_pixelmap_draw

## <a name="gx_canvas_polygon_draw"></a>gx_canvas_polygon_draw


多角形を描画します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_polygon_draw(
    GX_POINT *point_array,
    INT number_of_points);
```

### <a name="description"></a>説明

このサービスは、現在の描画コンテキスト ブラシを使用してキャンバスに多角形を描画します。

### <a name="parameters"></a>パラメーター

- **point_array** 多角形の点の配列
- **number_of_points** 多角形の点の数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 多角形の描画が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_CONTEXT** (0x06) 開いている描画コンテキストがありません

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_POINT my_polygon[4] =
{
    { 208, 63 },
    { 274, 63 },
    { 274, 163 },
    { 208, 163 }
};

/* Draw polygon “my_polygon” on canvas. */
status = gx_canvas_polygon_draw(&my_polygon, 4);

/* If status is GX_SUCCESS the polygon “my_polygon” has been drawn. */
```

### <a name="see-also"></a>参照

- gx_canvas_arc_draw、
- gx_canvas_block_move
- gx_canvas_circle_draw、
- gx_display_create
- gx_canvas_ellipse_draw、
- gx_canvas_line_draw
- gx_canvas_pie_draw、
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile、
- gx_canvas_rectangle_draw
- gx_canvas_text_draw

## <a name="gx_canvas_rectangle_draw"></a>gx_canvas_rectangle_draw


四角形を描画します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_rectangle_draw(GX_RECTANGLE *rectangle);
```

### <a name="description"></a>説明

このサービスは、キャンバスに四角形を描画します。

### <a name="parameters"></a>パラメーター

- **rectangle** 描画する四角形

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 四角形の描画が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_CONTEXT** (0x06) 開いている描画コンテキストがありません

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Draw rectangle “my_rectangle” on canvas. */
status = gx_canvas_rectangle_draw(&my_rectangle);

/* If status is GX_SUCCESS the rectangle “my_rectangle” has been drawn. */
```

### <a name="see-also"></a>参照

- gx_canvas_arc_draw、
- gx_canvas_block_move
- gx_canvas_circle_draw、
- gx_display_create
- gx_canvas_ellipse_draw、
- gx_canvas_line_draw
- gx_canvas_pie_draw、
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile、
- gx_canvas_polygon_draw
- gx_canvas_text_draw

## <a name="gx_canvas_rotated_text_draw"></a>gx_canvas_rotated_text_draw


中心点の周りを回転するテキストを描画します (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_rotated_text_draw(
    const GX_CHAR *text,
    GX_VALUE xCenter, 
    GX_VALUE yCenter, 
    INT angle);
```

### <a name="description"></a>説明

この API は非推奨になっていて、gx_canvas_rotated_text_draw_ext() の使用が推奨されています。 引き続きサポートされますが、新しいアプリケーションではこの API を使用せず、代わりに gx_canvas_rotated_text_draw_ext() を使用する必要があります。

このサービスは、テキストをキャンバスに描画します。 テキストは、要求された中心点の周りを回転するように描画されます。 テキストのレンダリングには、現在の描画コンテキストのフォントと描画コンテキストの線の色が使用されます。

このサービスは、関数 gx_utility_string_to_alphamap を使用して、アルファ値のみを含む一時的な 8bpp ピクセルマップにテキスト文字列をレンダリングします。 その後このサービスは、関数 gx_utility_pixelmap_rotate 使用して alphamap を回転させます。 最終的な alphamap がキャンバスにレンダリングされると、このサービスは一時的な alphamap と関連付けられているメモリを解放します。

回転するテキストをレンダリングするには一時的な alphamap が必要であるため、アプリケーションでは、回転するテキストの描画を試みる前に、gx_system_memory_allocator_set() API を呼び出して gx_system_memory_allocator を構成する必要があります。

このサービスは、回転するテキストを "1 回だけ" レンダリングする場合にのみ使用してください。 同じテキスト文字列を異なる場所または異なる回転角度で複数回描画する場合は、ユーティリティ関数 gx_utility_string_to_alphamap() を使用してテキスト alphamap を 1 回作成してから、gx_utility_pixelmap_rotate を複数回使用して、結果の alphamap を繰り返し回転させることで、効率が高まります。

### <a name="parameters"></a>パラメーター

- **text** 描画されるテキスト文字列
- **xCenter** 回転するテキストの中心となる位置。
- **yCenter** 回転するテキストの中心となる位置。
- **angle** 目的のテキストの回転角度 (度単位)。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) テキストのレンダリングが成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_SYSTEM_MEMORY_ERROR** (0x30) 使用できるメモリが不十分であるか、gx_system_memory_allocator が割り当てられていません
- **GX_INVALID_STRING_LENGTH** (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
void my_window_draw(GX_WINDOW *window)
{

    GX_VALUE xpos = 100;
    GX_VALUE ypos = 100;
    INT dynamic_count = 1234567;
    GX_CHAR dynamic_text[10];

    /* Call default window draw routine. */
    gx_window_draw(window);

    /* Set font. */
    gx_context_font_set(GX_FONT_ID_SMALL_BOLD);

    /* Convert int value to string. */
    gx_utility_ltoa(dynamic_count, dynamic_text, 20);

    /* Draw rotate text. */
    gx_canvas_rotated_text_draw(dynamic_text, xpos, ypos, 45);
}
```

### <a name="see-also"></a>参照

- gx_canvas_alpha_set、
- gx_canvas_drawing_complete
- gx_canvas_create、
- gx_canvas_drawing_initiate
- gx_canvas_offset_set、
- gx_canvas_shift

## <a name="gx_canvas_rotated_text_draw_ext"></a>gx_canvas_rotated_text_draw_ext


中心点の周りを回転するテキストを描画します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_rotated_text_draw_ext(
    GX_CONST GX_STRING *text,
    GX_VALUE xCenter, 
    GX_VALUE yCenter, 
    INT angle);
```

### <a name="description"></a>説明

このサービスは、テキストをキャンバスに描画します。 テキストは、要求された中心点の周りを回転するように描画されます。 テキストのレンダリングには、現在の描画コンテキストのフォントと描画コンテキストの線の色が使用されます。

このサービスは、関数 gx_utility_string_to_alphamap を使用して、アルファ値のみを含む一時的な 8bpp ピクセルマップにテキスト文字列をレンダリングします。 その後このサービスは、関数 gx_utility_pixelmap_rotate 使用して alphamap を回転させます。 最終的な alphamap がキャンバスにレンダリングされると、このサービスは一時的な alphamap と関連付けられているメモリを解放します。

回転するテキストをレンダリングするには一時的な alphamap が必要であるため、アプリケーションでは、回転するテキストの描画を試みる前に、***gx_system_memory_allocator_set()*** API を呼び出して gx_system_memory_allocator を構成する必要があります。

このサービスは、回転するテキストを "1 回だけ" レンダリングする場合にのみ使用してください。 同じテキスト文字列を異なる場所または異なる回転角度で複数回描画する場合は、ユーティリティ関数 gx_utility_string_to_alphamap() を使用してテキスト alphamap を 1 回作成してから、gx_utility_pixelmap_rotate を複数回使用して、結果の alphamap を繰り返し回転させることで、効率が高まります。

### <a name="parameters"></a>パラメーター

- **text** 描画されるテキスト文字列
- **xCenter** 回転するテキストの中心となる位置。
- **yCenter** 回転するテキストの中心となる位置。
- **angle** 目的のテキストの回転角度 (度単位)。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) テキストのレンダリングが成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_CONTEXT** (0x06) 描画コンテキストが無効です
- **GX_SYSTEM_MEMORY_ERROR** (0x30) 使用できるメモリが不十分であるか、gx_system_memory_allocator が割り当てられていません。
- **GX_INVALID_STRING_LENGTH** (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
void my_window_draw(GX_WINDOW *window)
{

    GX_VALUE xpos = 100;
    GX_VALUE ypos = 100;
    INT dynamic_count = 1234567;
    GX_CHAR dynamic_text[10];
    GX_STRING string;

    /* Call default window draw routine. */
    gx_window_draw(window);

    /* Set font. */
    gx_context_font_set(GX_FONT_ID_SMALL_BOLD);

    /* Convert int value to string. */
    gx_utility_ltoa(dynamic_count, dynamic_text, 20);

    string.gx_string_ptr = dynamic_text;
    string.gx_string_length = strlen(dynamic_text);

    /* Draw rotate text. */
    gx_canvas_rotated_text_draw_ext(&string, xpos, ypos, 45);
}
```

### <a name="see-also"></a>参照

- gx_canvas_alpha_set、
- gx_canvas_drawing_complete
- gx_canvas_create、
- gx_canvas_drawing_initiate
- gx_canvas_offset_set、
- gx_canvas_shift

## <a name="gx_canvas_shift"></a>gx_canvas_shift


X、Y でキャンバスをシフトします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_shift(
    GX_CANVAS *canvas, 
    GX_VALUE x, GX_VALUE y);
```

### <a name="description"></a>説明

このサービスは、指定されたキャンバス オフセットを指定された量だけシフトします。 これは、表示されているフレーム バッファー内のキャンバスがレンダリングされる位置に影響します。

### <a name="parameters"></a>パラメーター

- **canvas** キャンバス コントロール ブロックへのポインター
- **x** X 軸上でシフトするピクセル
- **y** Y 軸上でシフトするピクセル

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) キャンバスのシフトが成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_CANVAS** (0x20) キャンバスが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Shift canvas “my_canvas”. */
status = gx_canvas_shift(&my_canvas, 10, 15);

/* If status is GX_SUCCESS the canvas has been shifted by 10 pixels
    on the X axis and 15 on the Y axis. */
```

### <a name="see-also"></a>参照

- gx_canvas_drawing_complete、
- gx_canvas_initiate
- gx_canvas_alpha_set、
- gx_canvas_create
- gx_canvas_offset_set

## <a name="gx_canvas_show"></a>gx_canvas_show


キャンバスを表示します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_show(GX_CANVAS *canvas);
```

### <a name="description"></a>説明

このサービスは、キャンバスを表示します。 キャンバスが事前に gx_canvas_hardware_layer_bind() API を使用してハードウェアのグラフィックス レイヤーにバインドされている場合、gx_canvas_show() サービスがハードウェア サポートを使用して直接実装されます。

### <a name="parameters"></a>パラメーター

- **canvas** キャンバス コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) オフセットの割り当てが成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_CANVAS** (0x20) キャンバスが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Make this canvas visible. */
status = gx_canvas_show(&my_canvas);

/* If status is GX_SUCCESS the canvas drawing is now visible */
```

### <a name="see-also"></a>参照

- gx_canvas_alpha_set、
- gx_canvas_create
- gx_canvas_drawing_complete、
- gx_canvas_initiate、
- gx_canvas_shift、
- gx_canvas_hide、
- gx_canvas_hardware_layer_bind

## <a name="gx_canvas_text_draw"></a>gx_canvas_text_draw

テキストを描画します (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_text_draw(
    GX_VALUE x_start, 
    GX_VALUE y_start,
    GX_CONST GX_CHAR *string, 
    INT length);
```

### <a name="description"></a>説明

このサービスは、テキストをキャンバスに描画します。 この API は引き続きサポートされますが、非推奨であり、新しいアプリケーションでは、代わりに gx_canvas_text_draw_ext() を使用する必要があります。

### <a name="parameters"></a>パラメーター

- **x_start** テキストの開始の X 座標
- **y_start** テキストの開始の Y 座標
- **string** 描画する文字列へのポインター
- **length** length >= 0 である場合は、描画する文字数を length に制限します。 length < 0 である場合、NULL ターミネータが描画されるまでの文字列全体です。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) テキストの描画が成功しました
- **GX_FAILURE** (0x1E) テキストの描画が失敗しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_CONTEXT** (0x06) 開いている描画コンテキストがありません
- **GX_INVALID_STRING_LENGTH** (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Draw text “example” on current canvas”. */
status = gx_canvas_text_draw(10, 20, “example”, 7);

/* Draw all of a string of unknown length on the current canvas */
status = gx_canvas_text_draw(10, 40, string_ptr, -1);

/* If status is GX_SUCCESS the text “example” has been drawn. */
```

### <a name="see-also"></a>参照

- gx_canvas_arc_draw、
- gx_canvas_block_move
- gx_canvas_circle_draw、
- gx_display_create
- gx_canvas_ellipse_draw、
- gx_canvas_line_draw
- gx_canvas_pie_draw、
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw、
- gx_canvas_rectangle_draw

## <a name="gx_canvas_text_draw_ext"></a>gx_canvas_text_draw_ext


テキストを描画します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_canvas_text_draw_ext(
    GX_VALUE x_start, 
    GX_VALUE y_start,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>説明

このサービスは、テキストをキャンバスに描画します。

### <a name="parameters"></a>パラメーター

- **x_start** テキストの開始の X 座標
- **y_start** テキストの開始の Y 座標
- **string** 描画する文字列へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) テキストの描画が成功しました
- **GX_FAILURE** (0x1E) テキストの描画が失敗しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_CONTEXT** (0x06) 開いている描画コンテキストがありません
- **GX_INVALID_STRING_LENGTH** (0x34) 文字列の長さが無効です
- **GX_INVALID_FONT** (0x16) フォントが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_STRING string;
string.gx_string_ptr = “example”;
string.gx_string_length = 7;

/* Draw text “example” on current canvas”. */
status = gx_canvas_text_draw_ext(10, 20, &string);

/* If status is GX_SUCCESS the text “example” has been drawn. */
```

### <a name="see-also"></a>参照

- gx_canvas_arc_draw、
- gx_canvas_block_move
- gx_canvas_circle_draw、
- gx_display_create
- gx_canvas_ellipse_draw、
- gx_canvas_line_draw
- gx_canvas_pie_draw、
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw、
- gx_canvas_rectangle_draw

## <a name="gx_checkbox_create"></a>gx_checkbox_create


チェックボックスを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_checkbox_create(
    GX_CHECKBOX *checkbox, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    GX_RESOURCE_ID text_id,
    ULONG style, 
    USHORT checkbox_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスは、指定されたプロパティを使用してチェックボックス ウィジェットを作成します。 GX_CHECKBOX は GX_TEXT_BUTTON から派生し、GX_CHECKBOX ウィジェットではすべての gx_text_button サービスを使用できます。

### <a name="parameters"></a>パラメーター

- **checkbox** チェックボックス コントロール ブロックへのポインター。name: チェックボックス ウイジェットの論理名
- **parent** 親ウィジェットへのポインター
- **text_id** チェックボックスのテキストのリソース ID
- **style** チェックボックスのスタイル。 **付録 D** には、ウィジェット固有のスタイルだけでなく、すべてのウィジェット用に事前に定義されている一般的なスタイルが記載されています。
- **checkbox_id** アプリケーションで定義されたチェックボックスの ID
- **size** チェックボックスの大きさ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) チェックボックスの作成が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Create “my_checkbox”. */
status = gx_checkbox_create(&my_checkbox, “my_checkbox”,
    &my_parent,
    MY_CHECKBOX_TEXT_RESOURCE_ID, GX_STYLE_BORDER_RAISED,
    MY_CHECKBOX_ID,
    &size);

/* If status is GX_SUCCESS the checkbox “my_checkbox” has been created. */
```
### <a name="see-also"></a>参照

- gx_checkbox_draw、
- gx_checkbox_event_process、
- gx_checkbox_select

## <a name="gx_checkbox_draw"></a>gx_checkbox_draw

チェックボックスを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_checkbox_draw(GX_CHECKBOX *checkbox);
```

### <a name="description"></a>説明

このサービスは、指定されたチェックボックスを描画します。 通常、この関数は GUIX キャンバスの更新メカニズムによって内部で呼び出されますが、カスタム チェックボックス ウイジェットのカスタム描画関数の実装を支援するためにアプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **checkbox** チェックボックス コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom checkbox draw function. */
VOID custom_checkbox_draw(GX_CHECKBOX *checkbox)
{
    /* Call default checkbox draw. */
    gx_checkbox_draw(checkbox);

    /* Add custom drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_checkbox_create、
- gx_checkbox_event_process、
- gx_checkbox_select

## <a name="gx_checkbox_event_process"></a>gx_checkbox_event_process


チェックボックスのイベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_checkbox_event_process(
    GX_CHECKBOX *checkbox, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>説明

このサービスは、指定されたチェックボックスのイベントを処理します。 このサービスは、カスタム チェックボックスのイベント処理関数によって既定のイベント ハンドラーとして呼び出される必要があります。

### <a name="parameters"></a>パラメーター

- **checkbox** チェックボックス コントロール ブロックへのポインター
- **event_ptr** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) チェックボックスのイベント処理が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Call generic checkbox event processing as part of custom event processing function. */

UINT custom_checkbox_event_process(GX_CHECKBOX *checkbox,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default checkbox
            event processing */
        status = gx_checkbox_event_process(checkbox, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>参照

- gx_checkbox_create、
- gx_checkbox_draw、
- gx_checkbox_select

## <a name="gx_checkbox_pixelmap_set"></a>gx_checkbox_pixelmap_set


チェックボックスのピクセルマップを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_checkbox_pixelmap_set(
    GX_CHECKBOX *checkbox,
    GX_RESOURCE_ID unchecked_id, 
    GX_RESOURCE_ID checked_id,
    GX_RESOURCE_ID unchecked_disabled_id, 
    GX_RESOURCE_ID checked_disabled_id);
```

### <a name="description"></a>説明

このサービスは、チェックボックスの状態ごとに、指定されたチェックボックスによって表示されるピクセルマップを割り当てます。 リソース ID は重複してかまいません。

### <a name="parameters"></a>パラメーター

- **checkbox** チェックボックス コントロール ブロックへのポインター
- **unchecked_id** オフの状態の場合に使用されるピクセルマップ
- **checked_id** オンの状態の場合に使用されるピクセルマップ
- **unchecked_disabled_id** 無効かつオフになっているチェックボックスに使用されるピクセルマップ
- **unchecked_disabled_id** 無効かつオンになているチェックボックスに使用されるピクセルマップ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) チェックボックスをオンにすることが成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Select “my_checkbox”. */
status = gx_checkbox_pixelmap_set(&my_checkbox,
    PIXELMAP_UNCHECKED_ID,
    PIXELMAP_CHECKED_ID, PIXELMAP_UNCHECKED_DISABLED_ID,
    PIXELMAP_CHECKED_SIABLED_ID));

/* If status is GX_SUCCESS the pixelmaps are assigned to the checkbox “my_checkbox” */
```

### <a name="see-also"></a>参照

- gx_checkbox_create、
- gx_checkbox_draw、
- gx_checkbox_event_process

## <a name="gx_checkbox_select"></a>gx_checkbox_select


チェックボックスをオンにします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_checkbox_select(GX_CHECKBOX *checkbox);
```

### <a name="description"></a>説明

このサービスは、チェックボックスを強制的にオンの状態にします。

### <a name="parameters"></a>パラメーター

- **checkbox** チェックボックス コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) チェックボックスをオンにすることが成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Select “my_checkbox”. */
status = gx_checkbox_select(&my_checkbox);

/* If status is GX_SUCCESS the checkbox “my_checkbox” has been toggled. */
```

### <a name="see-also"></a>参照

- gx_checkbox_create、
- gx_checkbox_draw、
- gx_checkbox_event_process

## <a name="gx_circular_gauge_angle_get"></a>gx_circular_gauge_angle_get


現在の角度を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_circular_gauge_angle_get(
    GX_CIRCULAR_GAUGE *gauge, 
    INT *angle);
```

### <a name="description"></a>説明

このサービスは、円形ゲージ ウィジェットの現在の針の角度を取得します。

### <a name="parameters"></a>パラメーター

- **gauge** 円形ゲージ コントロール ブロックへのポインター
- **angle** 取得する現在の針の角度

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 円形ゲージの角度の取得が成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
INT current_angle;

/* Retrieve the current needle angle of “my_gauge”. */
status = gx_circular_gauge_angle_get(&my_gauge, &current_angle);

/* If status is GX_SUCCESS the current needle angle of “my_gauge” has been retrieved. */
```

### <a name="see-also"></a>参照

- gx_circular_gauge_angle_set、
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw、
- gx_circular_gauge_create
- gx_circular_gauge_draw、
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_angle_set"></a>gx_circular_gauge_angle_set


目標角度を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_circular_gauge_angle_set(
    GX_CIRCULAR_GAUGE *gauge,
    INT angle);
```

### <a name="description"></a>説明

このサービスは、円形ゲージ ウィジェットの目標角度を設定します。

### <a name="parameters"></a>パラメーター

- **gauge** 円形ゲージ コントロール ブロックへのポインター
- **angle** 針の目標角度

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 角度の設定が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set target angle of “my_gauge” to 180. */
status = gx_circular_gauge_angle_set(&my_gauge, 180);

/* If status is GX_SUCCESS the circular gauge of “my_gauge” has been set. */
```

### <a name="see-also"></a>参照

- gx_circular_gauge_angle_get、
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw、
- gx_circular_gauge_create
- gx_circular_gauge_draw、
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_animation_set"></a>gx_circular_gauge_animation_set


アニメーションのパラメーターを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_circular_gauge_animation_set(
    GX_CIRCULAR_GAUGE *gauge,
    INT steps, 
    INT delay);
```

### <a name="description"></a>説明

このサービスは、円形ゲージ ウィジェットのアニメーション ステップと遅延時間を設定します。

### <a name="parameters"></a>パラメーター

- **gauge** 円形ゲージ コントロール ブロックへのポインター
- **steps** 1 回の回転の合計ステップ
- **delay** すべてのステップの遅延時間

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) チェックボックスをオンにすることが成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_VALUE** (0x22) 値が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set animation steps and delay time of circular gauge “my_gauge”
    to 30 and 1, the needle of “my_gauge” will rotate from
    current angle to target angle by 30 steps with 1 tick delay between every step. */
status = gx_circular_gauge_animation_set(&my_gauge, 30, 1);

/* If status is GX_SUCCESS the steps and delay time of “my_gauge” has been set. */
```

### <a name="see-also"></a>参照

- gx_circular_gauge_angle_get、
- gx_circular_gauge_angle_set
- gx_circular_gauge_background_draw、
- gx_circular_gauge_create
- gx_circular_gauge_draw、
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_background_draw"></a>gx_circular_gauge_background_draw


円形ゲージの背景を描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_circular_gauge_background_draw(GX_CIRCULAR_GAUGE *gauge);
```

### <a name="description"></a>説明

このサービスは、指定された円形ゲージの背景を描画します。 このサービスは通常、gx_circular_gauge_draw 関数によって内部で呼び出されますが、カスタムの描画関数の記述を支援するためにアプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **gauge** 円形ゲージ コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Draw circular gauge background. */
gx_circular_gauge_background_draw(&my_circular_gauge);
```

### <a name="see-also"></a>参照

- gx_circular_gauge_angle_get、
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set、
- gx_circular_gauge_create
- gx_circular_gauge_draw、
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_create"></a>gx_circular_gauge_create


円形ゲージを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_circular_gauge_create(
    GX_CIRCULAR_GAUGE *gauge,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_CIRCULAR_GAUGE_INFO *info,
    GX_RESOURCE_ID background_id,
    ULONG style,
    USHORT circular_gauge_id,
    GX_VALUE xpos,
    GX_VALUE ypos);
```

### <a name="description"></a>説明

このサービスは、指定されたプロパティを使用して円形ゲージ ウィジェットを作成します。

### <a name="parameters"></a>パラメーター

- **gauge** 円形ゲージ コントロール ブロックへのポインター
- **name** 円形ゲージ ウィジェットの論理名
- **parent** 親ウイジェットへのポインター
- **info** ゲージ情報構造体へのポインター。 **付録 I** には、GX_CIRCULAR_GAUGE_INFO 構造体の定義が含まれています
- **background_id** 円形ゲージの背景のピクセルマップのリソース ID
- **style** 円形ゲージのスタイル。 **付録 D** には、ウィジェット固有のスタイルだけでなく、すべてのウィジェット用に事前に定義されている一般的なスタイルが記載されています。
- **circular_gauge_id** 円形ゲージのアプリケーション定義の ID
- **xpos** ゲージの X 座標の位置
- **ypos** ゲージの Y 座標の位置

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) チェックボックスをオンにすることが成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_SIZE**: (0x19) コントロール ブロック サイズが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_CIRCULAR_GAUGE gauge_info;

gauge_info.gx_circular_gauge_info_animation_steps = 30;
gauge_info.gx_circular_gauge_info_animation_delay = 1;
gauge_info.gx_circular_gauge_info_needle_xpos = 140;
gauge_info.gx_circular_gauge_info_needle_ypos = 140;
gauge_info.gx_circular_gauge_info_neelde_xcor = 20;
gauge_info.gx_circular_gauge_info_neelde_ycor = 88;
gauge_info.gx_circular_gauge_info_needle_pixelmap = GX_PIXELMAP_ID_NEEDLE;

/* Create “my_gauge”. */
status = gx_circular_gauge_create(&my_gauge, “my_gauge”,
            &my_parent,
            &gauge_info, MY_PIXELMAP_RESOURCE_ID, GX_NULL,
            MY_ICON_ID, 5, 30);

/* If status is GX_SUCCESS the circular gauge “my_gauge” has been created. */
```

### <a name="see-also"></a>参照

- gx_circular_gauge_angle_get、
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw、
- gx_circular_gauge_draw
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_draw"></a>gx_circular_gauge_draw

円形ゲージを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_circular_gauge_draw(GX_CIRCULAR_GAUGE *gauge);
```

### <a name="description"></a>説明

このサービスは、指定された円形ゲージを描画します。 通常、この関数は GUIX キャンバスの更新メカニズムによって内部で呼び出されますが、カスタム ゲージ ウイジェットのカスタム描画関数の実装を支援するためにアプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **gauge** 円形ゲージ コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom circular gauge draw function. */
VOID custom_gauge_draw(GX_CIRCULAR_GAUGE *gauge)
{
    /* Call default circular gauge draw. */
    gx_circular_gauge_draw(gauge);

    /* Add custom drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_circular_gauge_angle_get、
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw
- gx_circular_gauge_create、
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_event_process"></a>gx_circular_gauge_event_process


円形ゲージ イベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_circular_gauge_event_process(
    GX_CIRCULAR_GAUGE *gauge,
    GX_EVENT *event);
```

### <a name="description"></a>説明

このサービスは、指定された円形ゲージのイベントを処理します。

### <a name="parameters"></a>パラメーター

- **gauge** ゲージ コントロール ブロックへのポインター
- **event_ptr** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ゲージのイベント処理が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Call generic circular gauge event processing as part of custom event processing function. */
UINT custom_gauge_event_process(GX_CIRCULAR_GAUGE *gauge,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default circular gauge
             event processing */
        status = gx_circular_gauge_event_process(gauge, event);
        break;
}
return status;
```

### <a name="see-also"></a>参照

- gx_circular_gauge_angle_get、
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw、
- gx_circular_gauge_create
- gx_circular_gauge_draw

## <a name="gx_context_brush_default"></a>gx_context_brush_default


現在の描画コンテキストのブラシを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_brush_default(GX_DRAW_CONTEXT *context);
```

### <a name="description"></a>説明

このサービスは、指定された描画コンテキストのブラシを既定値に設定します。

### <a name="parameters"></a>パラメーター

- **context** コンテキスト コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 作成が成功しました
- **GX_PTR_ERROR** (0x07) コンテキスト ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the brush of “my_context” to default. */
status = gx_context_brush_default(&my_context);

/* If status is GX_SUCCESS the brush of “my_context” has been set to default. */

```

### <a name="see-also"></a>参照

- gx_context_brush_define、
- gx_context_brush_get
- gx_context_brush_set、
- gx_context_brush_style_set
- gx_context_brush_pattern_set、
- gx_context_brush_width_set
- gx_context_fill_color_set、
- gx_context_font_set
- gx_context_line_color_set、
- gx_context_pixelmap_set
- gx_context_raw_brush_define、
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_define"></a>gx_context_brush_define


現在の描画コンテキストのブラシを定義します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_brush_define(
    GX_RESOURCE_ID line_color_id,
    GX_RESOURCE_ID fill_color_id, 
    UINT style);
```

### <a name="description"></a>説明

このサービスは、現在の描画コンテキストのブラシを定義します。

### <a name="parameters"></a>パラメーター

- **line_color_id** 線の色のリソース ID。 **付録 B** には、定義済みの色リソース ID が含まれています。 アプリケーションでは、カスタムの色リソース ID も追加できることに注意してください。
- **fill_color_id** 塗りつぶしの色のリソース ID。 **付録 B** には、定義済みの色リソース ID が含まれています。 アプリケーションでは、カスタムの色リソース ID も追加できることに注意してください。
- **style** ブラシのスタイル。 **付録 D** では、サポートされているブラシのスタイルが説明されています。 ブラシのスタイルは、ビットごとの OR 演算を使用して 1 つの変数に結合できます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) コンテキスト ブラシの定義が成功しました
- **GX_INVALID_RESOURCE_ID** (0x33) リソース ID が無効です
- **GX_INVALID_CONTEXT** (0x06) アクティブな描画コンテキストの定義がありません
- **GX_INVALID_RESOURCE_ID** (0x33) リソース ID が無効です
- **GX_INVALID_CONTEXT** (0x06) アクティブな描画コンテキストがありません

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Define the brush of the current context. */
status = gx_context_brush_define(GX_COLOR_BLACK_ID,
    GX_COLOR_BLACK_ID,
    GX_STYLE_BORDER_NONE);

/* If status is GX_SUCCESS the brush of the current context has been defined. */
```

### <a name="see-also"></a>参照

- gx_context_brush_default、
- gx_context_brush_get
- gx_context_brush_set、
- gx_context_brush_pattern_set
- gx_context_brush_style_set、
- gx_context_brush_width_set
- gx_context_fill_color_set、
- gx_context_font_set
- gx_context_line_color_set、
- gx_context_pixelmap_set
- gx_context_raw_brush_define、
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_get"></a>gx_context_brush_get


現在の描画コンテキストのブラシを取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_brush_get(GX_BRUSH **return_brush);
```

### <a name="description"></a>説明

このサービスは、現在の描画コンテキストのアクティブなブラシへのポインターを返します。 アクティブな描画コンテキストがない場合、このサービスは失敗し、NULL ポインターを返します。

### <a name="parameters"></a>パラメーター

- **return_brush** ブラシの宛先へのポインター。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) コンテキストのブラシの取得に成功しました
- **GX_INVALID_CONTEXT** (0x06) アクティブな描画コンテキストがありません
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_BRUSH *my_brush;

/* Get the brush of the current context. */
status = gx_context_brush_get(&my_brush);

/* If status is GX_SUCCESS the brush of the current context has been retrieved. */
```

### <a name="see-also"></a>参照

- gx_context_brush_set、
- gx_context_brush_style_set
- gx_context_brush_default、
- gx_context_brush_define
- gx_context_brush_pattern_set、
- gx_context_brush_width_set
- gx_context_fill_color_set、
- gx_context_font_set
- gx_context_line_color_set、
- gx_context_pixelmap_set
- gx_context_raw_brush_define、
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_pattern_set"></a>gx_context_brush_pattern_set


現在の描画コンテキストのブラシ パターンを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_brush_pattern_set(ULONG pattern);
```

### <a name="description"></a>説明

このサービスは、現在の描画コンテキストのブラシ パターンを設定します。

ブラシ パターンは、水平方向の破線と垂直方向の破線の描画に使用されます。 gx_canvas_line_draw() が呼び出され、線が水平方向または垂直方向であり、brush.gx_brush_line_pattern フィールドが 0 以外の場合、パターンの線が描画されます。

現在、ブラシ パターンのマスクは、水平方向と垂直方向の線でのみサポートされています。

### <a name="parameters"></a>パラメーター

- **pattern** ブラシに使用されるパターン。 これは、パターンの線の描画に使用される単純な 16 進数のオン/オフ パターンです。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) コンテキスト ブラシの設定が成功しました
- **GX_INVALID_CONTEXT** (0x06) 描画コンテキストが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the brush pattern for the current contex. */
status = gx_context_brush_pattern_set(0x80808080);

/* If status is GX_SUCCESS the brush pattern of the current context
has been set to the specified pattern. */
```

### <a name="see-also"></a>参照

- gx_context_brush_default、
- gx_context_brush_define
- gx_context_brush_get、
- gx_context_brush_style_set
- gx_context_brush_width_set、
- gx_context_fill_color_set
- gx_context_font_set、
- gx_context_line_color_set
- gx_context_pixelmap_set、
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set、
- gx_context_raw_line_color_set

## <a name="gx_context_brush_set"></a>gx_context_brush_set


現在の描画コンテキストのブラシを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_brush_set(GX_BRUSH *brush);
```

### <a name="description"></a>説明

このサービスは、現在の描画コンテキストのブラシを設定します。

### <a name="parameters"></a>パラメーター

- **brush** 現在のコンテキストで使用するブラシへのポインター。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) コンテキスト ブラシの設定が成功しました
- **GX_INVALID_CONTEXT** (0x06) アクティブな描画コンテキストがありません
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_BRSUH my_brush;
GX_FONT *font;
GX_COLOR fill_color;
GX_COLOR line_color;

/* Retrieve the font that associated with the specified font ID. */
gx_context_font_get(MY_FONT_ID, &font);

/* Retrieve the color that associated with the specified color ID. */
gx_context_color_get(MY_FILL_COLOR_ID, &fill_color);
gx_context_color_get(MY_LINE_COLOR, &line_color);

my_brush.gx_brush_pixelmap = MY_PIXELMAP_ID;
my_brush.gx_brush_font = font;
my_brush.gx_brush_line_pattern = 0x80808080;
my_brush.gx_brush_pattern_mask = 0x80000000;
my_brush.gx_brush_fill_color = fill_color;
my_brush.gx_brush_line_color = line_color;
my_brush.gx_brush_style = GX_BRSUH_SOLID_FILL | GX_BRUSH_ALIAS |
                          GX_BRUSH_PIXELMAP_FILL | GX_BRUSH_ROUND
my_brush.gx_brush_width = 2;
my_brush.gx_brush_alpha = 255;

/* Set the brush of the current context. */
status = gx_context_brush_set(my_brush);

/* If status is GX_SUCCESS the brush of the current context has been set. */
```

### <a name="see-also"></a>参照

- gx_context_brush_default、
- gx_context_brush_define
- gx_context_brush_get、
- gx_context_brush_pattern_set
- gx_context_brush_style_set、
- gx_context_brush_width_set
- gx_context_fill_color_set、
- gx_context_font_set
- gx_context_line_color_set、
- gx_context_pixelmap_set
- gx_context_raw_brush_define、
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_style_set"></a>gx_context_brush_style_set


現在の描画コンテキストのブラシのスタイルを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_brush_style_set(UINT style);
```

### <a name="description"></a>説明

このサービスは、現在の描画コンテキストのブラシのスタイルを設定します。

### <a name="parameters"></a>パラメーター

- **style** 現在のコンテキストのブラシのスタイル。 **付録 D** には、ウィジェット固有のスタイルだけでなく、すべてのウィジェット用に事前に定義された一般的なスタイルが含まれています。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) コンテキスト ブラシのスタイルの設定が成功しました
- **GX_INVALID_CONTEXT** (0x06) アクティブな描画コンテキストがありません

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the brush style of the current context. */
status = gx_context_brush_style_set(GX_BRUSH_ALIAS);

/* If status is GX_SUCCESS the brush style of the current context has been set. */
```

### <a name="see-also"></a>参照

- gx_context_brush_default、
- gx_context_brush_define
- gx_context_brush_get、
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_width_set、
- gx_context_fill_color_set
- gx_context_font_set、
- gx_context_line_color_set
- gx_context_pixelmap_set、
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set、
- gx_context_raw_line_color_set

## <a name="gx_context_brush_width_set"></a>gx_context_brush_width_set


現在の描画コンテキストのブラシの幅を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_brush_width_set(UINT width);
```

### <a name="description"></a>説明

このサービスは、現在の描画コンテキストのアクティブなブラシの幅を設定します。

### <a name="parameters"></a>パラメーター

**width** 現在のコンテキストのブラシの幅 (ピクセル単位)

### <a name="return-values"></a>戻り値

**GX_SUCCESS** (0x00) コンテキスト ブラシの幅の設定が成功しました

**GX_INVALID_CONTEXT** (0x06) アクティブな描画コンテキストがありません

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the brush width of the current context to 10 pixels. */
status = gx_context_brush_width_set(10); /*

If status is GX_SUCCESS the brush width of the current context has been set to 10. */
```

### <a name="see-also"></a>参照

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_color_get"></a>gx_context_color_get


現在の描画コンテキストの色 ID に関連付けられている色の値を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_color_get(
    GX_RESOURCE_ID color_id,
    GX_COLOR *return_color);
```

### <a name="description"></a>説明

このサービスは、示された色 ID に関連付けられている色の値を取得します。 色の値は、アクティブなコンテキスト表示の色の形式で返されます。 このサービスは、アクティブな描画操作内からのみ呼び出してください。

### <a name="parameters"></a>パラメーター

**color_id** 要求された色のリソース ID。

**return_color** 返された色の値を保持する変数のアドレス。

### <a name="return-values"></a>戻り値

**GX_SUCCESS** (0x00) 色の値の取得に成功しました

**GX_INVALID_RESOURCE_ID** (0x33) リソース ID が無効です

**GX_INVALID_CONTEXT** (0x06) アクティブな描画コンテキストがありません

**GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_COLOR color_value;

/* Get the color vaue. */
status = gx_context_color_get(MY_BLACK_COLOR_ID, &color_value);
```

### <a name="see-also"></a>参照

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_fill_color_set"></a>gx_context_fill_color_set

現在の描画コンテキストの塗りつぶしの色を設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_fill_color_set(GX_RESOURCE_ID fill_color_id);
```

### <a name="description"></a>説明

このサービスは、現在の描画コンテキストでアクティブなブラシの塗りつぶしの色を設定します。

### <a name="parameters"></a>パラメーター

- **fill_color_id** 現在のコンテキストの塗りつぶしの色のリソース ID。 **付録 B** に、定義済みの色のリソース ID が記載されています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) コンテキストの塗りつぶしの色の設定が成功しました
- **GX_INVALID_RESOURCE_ID** (0x33) リソース ID が無効です
- **GX_INVALID_CONTEXT** (0x06) アクティブな描画コンテキストがありません

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the fill color of the current context to black. */
status = gx_context_fill_color_set(MY_BLACK_COLOR_ID);

/* If status is GX_SUCCESS the fill color of the current context has been set to black. */
```

### <a name="see-also"></a>参照

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_font_get"></a>gx_context_font_get

現在の描画コンテキストでフォント ID に関連付けられているフォントを取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_font_get(
    GX_RESOURCE_ID font_id,
    GX_FONT **return_font);
```

### <a name="description"></a>説明

このサービスは、指定されたフォント ID に関連付けられているフォント ポインターを取得します。 このサービスは、アクティブな描画操作内からのみ呼び出してください。

### <a name="parameters"></a>パラメーター

- **font_id** 要求対象のフォントのリソース ID。
- **return_font** 返されるフォント ポインターを格納する変数のアドレス。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) フォントの取得に成功しました
- **GX_INVALID_RESOURCE_ID** (0x33) リソース ID が無効です
- **GX_INVALID_CONTEXT** (0x06) アクティブな描画コンテキストがありません
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_FONT *my_font;

/* Get the font pointer. */
status = gx_context_font_get(MY_MIDSIZE_FONT, &my_font);

/* If status is GX_SUCCESS, the font that indicated with MY_MIDSIZE_FONT has been successfully retrieved. */
```

### <a name="see-also"></a>参照

- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_font_set"></a>gx_context_font_set

現在の描画コンテキストのフォントを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_font_set(GX_RESOURCE_ID font_id);
```

### <a name="description"></a>説明

このサービスは、現在の描画コンテキストのアクティブなブラシのフォントを設定します。

### <a name="parameters"></a>パラメーター

- **font_id** 現在のコンテキストのフォント リソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) コンテキストのフォントの設定が成功しました
- **GX_INVALID_RESOURCE_ID** (0x33) リソース ID が無効です
- **GX_INVALID_CONTEXT** (0x06) アクティブな描画コンテキストがありません

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the font of the current context to MY_FONT_ID. */
status = gx_context_font_set(MY_FONT_ID);

/* If status is GX_SUCCESS the font of the current context has been set. */
```

### <a name="see-also"></a>参照

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_line_color_set"></a>gx_context_line_color_set

現在の描画コンテキストの線の色を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_line_color_set(GX_RESOURCE_ID line_color_id);
```

### <a name="description"></a>説明

このサービスは、現在の描画コンテキストでアクティブなブラシの線の色を設定します。

### <a name="parameters"></a>パラメーター

- **line_color_id** 現在のコンテキストの線の色。 **付録 B** に、定義済みの色のリソース ID が記載されています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) コンテキストの線の色の設定が成功しました
- **GX_INVALID_RESOURCE_ID** (0x33) リソース ID が無効です
- **GX_INVALID_CONTEXT** (0x06) アクティブな描画コンテキストがありません

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the line color of the current context to black. */
status = gx_context_line_color_set(GX_COLOR_BLACK_ID);

/* If status is GX_SUCCESS the line color of the current context has been set to black. */
```

### <a name="see-also"></a>参照

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_pixelmap_get"></a>gx_context_pixelmap_get

現在の描画コンテキストでピクセルマップ ID に関連付けられているピクセルマップを取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_pixelmap_get(
    GX_RESOURCE_ID pixelmap_id,
    GX_PIXELMAP **return_map);
```

### <a name="description"></a>説明

このサービスは、指定されたピクセルマップ ID に関連付けられているピクセルマップ ポインターを取得します。

### <a name="parameters"></a>パラメーター

- **pixelmap_id** 要求対象のピクセルマップのリソース ID。
- **return_map** 返されたピクセルマップのアドレスを格納する変数のアドレス。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ピクセルマップの取得に成功しました
- **GX_INVALID_RESOURCE_ID** (0x33) リソース ID が無効です
- **GX_INVALID_CONTEXT** (0x06) アクティブな描画コンテキストがありません
- **GX_PTR_ERROR** (0x07) ピクセルマップのポインターが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_PIXELMAP *map;

/* Get the pixelmap pointer. */
status = gx_context_pixelmap_get(MY_PIXELMAP_ID, &map);

/* If status is GX_SUCCESS, the pixelmap was successfully retrieved. */
```

### <a name="see-also"></a>参照

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_pixelmap_set"></a>gx_context_pixelmap_set

現在の描画コンテキストのピクセルマップを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_pixelmap_set(GX_RESOURCE_ID pixelmap_id);
```

### <a name="description"></a>説明

このサービスは、現在の描画コンテキストでアクティブなブラシのピクセルマップを割り当てます。

### <a name="parameters"></a>パラメーター

- **pixelmap_id** 現在のコンテキストに使用するピクセルマップのリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) コンテキストのピクセルマップの設定が成功しました
- **GX_INVALID_RESOURCE_ID** (0x33) リソース ID が無効です
- **GX_INVLAID_CONTEXT** (0x06) コンテキストが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Set pixelmap of the current context to MY_PIXELMAP_ID. */
status = gx_context_pixelmap_set(MY_PIXELMAP_ID);

/* If status is GX_SUCCESS the pixelmap of the current context has been set. */
```

### <a name="see-also"></a>参照

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_raw_brush_define"></a>gx_context_raw_brush_define

現在の描画コンテキストの未加工ブラシを定義します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_raw_brush_define(
    GX_COLOR line_color,
    GX_COLOR fill_color, 
    UINT style);
```

### <a name="description"></a>説明

このサービスは、現在の画面コンテキストの未加工ブラシを定義します。 32 ビットの ARGB カラー値をカラー ID ではなくブラシに渡す場合、未加工の定義が使用されます。 未加工のカラー定義は、目的の色が現在のシステム カラー テーブルに存在しない場合、または RGB カラー値が実行時に計算される場合に便利です。

### <a name="parameters"></a>パラメーター

- **line_color** 32 ビットの未加工 ARGB カラー形式の線の色。 **付録 A** に、事前定義済みの色が記載されています。 なお、アプリケーションでカスタムの色を追加することもできます。
- **line_color** 32 ビットの未加工 ARGB カラー形式の塗りつぶしの色。 **付録 A** に、事前定義済みの色が記載されています。 なお、アプリケーションでカスタムの色を追加することもできます。
- **style** ブラシのスタイル。 **付録 D** には、すべてのウィジェット用に事前に定義されている一般的なスタイルおよびウィジェット固有のスタイルが記載されています。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) コンテキストの未加工ブラシの定義が成功しました
- **GX_INVALID_CONTEXT** (0x06) アクティブな描画コンテキストがありません

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Define the raw brush of the current context. */
status = gx_context_raw_brush_define(GX_COLOR_BLACK,
    GX_COLOR_BLACK, GX_STYLE_BORDER_NONE);

/* If status is GX_SUCCESS the raw brush of the current context has been defined. */
```

### <a name="see-also"></a>参照

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_raw_fill_color_set"></a>gx_context_raw_fill_color_set

現在の描画コンテキストの未加工の塗りつぶし色を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_raw_fill_color_set(GX_COLOR line_color);
```

### <a name="description"></a>説明

このサービスは、現在の画面コンテキストの未加工の塗りつぶし色を設定します。 line_color パラメーターは、カラー ID 値ではなく、32 ビットの ARGB 形式の未加工のカラー値です。 未加工のカラー定義は、目的の色が現在のシステム カラー テーブルに存在しない場合、または RGB カラー値が実行時に計算される場合に便利です。

### <a name="parameters"></a>パラメーター

- **line_color** 線の色。 **付録 A** に、事前定義済みの色が記載されています。 なお、アプリケーションでカスタムの色を追加することもできます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) コンテキストの未加工の塗りつぶし色の設定が成功しました
- **GX_INVALID_CONTEXT** (0x06) アクティブな描画コンテキストがありません

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the raw fill color of the current context. */
status = gx_context_raw_fill_color_set(GX_COLOR_BLACK);

/* If status is GX_SUCCESS the raw fill color of the current context has been set. */
```

### <a name="see-also"></a>参照

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_line_color_set

## <a name="gx_context_raw_line_color_set"></a>gx_context_raw_line_color_set

現在の描画コンテキストの未加工の線の色を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_raw_line_color_set(GX_COLOR line_color);
```

### <a name="description"></a>説明

このサービスは、現在の描画コンテキストでアクティブなブラシの線の色を設定します。 line_color パラメーターは、カラー ID 値ではなく、32 ビットの ARGB 形式の未加工のカラー値です。 未加工のカラー定義は、目的の色が現在のシステム カラー テーブルに存在しない場合、または RGB カラー値が実行時に計算される場合に便利です。

### <a name="parameters"></a>パラメーター

- **line_color** 線の色の値。 **付録 A** に、事前定義済みの色が記載されています。 なお、アプリケーションでカスタムの色を追加することもできます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) コンテキストの未加工の線の色の設定が成功しました
- **GX_INVALID_CONTEXT** (0X06) アクティブな描画コンテキストがありません

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

```C
/* Set the raw line color of the current context. */
status = gx_context_raw_line_color_set(GX_COLOR_BLACK);

/* If status is GX_SUCCESS the raw line color of the current context has been set. */
```

### <a name="see-also"></a>参照

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set

## <a name="gx_context_string_get"></a>gx_context_string_get

文字列 ID に関連付けられた文字列を取得します (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_string_get(GX_RESOURCE_ID string_id,
    GX_CONST GX_CHAR **return_string);
```

### <a name="description"></a>説明

この非推奨の API は、指定された文字列 ID に関連付けられている文字列を返します。 新しいアプリケーションでは gx_context_string_get_ext() を使用してください。

### <a name="parameters"></a>パラメーター

- **string_id** GUIX Studio アプリケーションによって生成される文字列 ID。
- **return_string** 文字列ポインターを返す変数のアドレス。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) コンテキストの未加工の線の色の設定が成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_CONTEXT** (0X06) アクティブな描画コンテキストがありません

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_CHAR *text;

status = gx_context_string_get(GX_ID_ERROR, &text);

/* If status is GX_SUCCESS the string pointer has been returned. */
```

### <a name="see-also"></a>参照

- gx_context_string_get_ext

## <a name="gx_context_string_get_ext"></a>gx_context_string_get_ext

指定された文字列 ID に関連付けられている文字列を取得します。

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_context_string_get_ext(
    GX_RESOURCE_ID string_id, 
    GX_STRING *return_string);
```

### <a name="description"></a>説明

このサービスは、指定された文字列 ID に関連付けられている文字列を返します。 このサービスは、アクティブな描画コンテキストがある場合、つまり、ウィジェットの描画関数内からのみ呼び出すことができます。 このサービスは、アクティブなキャンバスとディスプレイを識別し、検出されたディスプレイ インスタンスから文字列を取得します。

### <a name="parameters"></a>パラメーター

- **string_id** アプリケーション リソース ヘッダー ファイル内の GUIX Studio によって生成される文字列を識別するために使用される文字列 ID。
- **return_string** 文字列ポインターと文字列長が返される GX_STRING 変数のアドレス。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) コンテキストの未加工の線の色の設定が成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_CONTEXT** (0X06) アクティブな描画コンテキストがありません

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例


```C
GX_STRING string;

/* Set the raw line color of the current context. */
status = gx_context_string_get_ext(ID_ERROR, &string);

/* If status is GX_SUCCESS the string.gx_string_ptr and
string.gx_string_length values have been returned. */
```

### <a name="see-also"></a>参照

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set

## <a name="gx_display_active_language_set"></a>gx_display_active_language_set

ディスプレイにアクティブな言語を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_display_active_language_set(
    GX_DISPLAY *display, 
    GX_UBYTE language);
```

### <a name="description"></a>説明

このサービスは、指定されたディスプレイに現在アクティブな言語を割り当てます。 言語インデックスは、ディスプレイの言語テーブルで定義されている言語に対応し、ANSI 言語識別子ではありません。

マルチディスプレイ システムでは、異なるディスプレイで、それぞれ異なるアクティブな言語を実行できます。 この API を使用する前に、ディスプレイの言語テーブルを割り当てる必要があります。 gx_studio_display_configure を使用してディスプレイを初期化すると、言語テーブルが自動的にインストールされ、アプリケーションはアクティブな言語インデックスを渡します。

### <a name="parameters"></a>パラメーター

- **display** ディスプレイ コントロール ブロックへのポインター
- **language** アクティブな言語インデックス

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 言語の割り当てが成功しました
- **GX_PTR_ERROR** (0x07) ディスプレイのポインターが無効です
- **GX_INVALID_VALUE** (0x22) 言語インデックスが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Change value of color MY_COLOR_ID. */
status = gx_display_active_language_set(&my_display,
    LANGUAGE_ENGLISH);

/* If status is GX_SUCCESS the active language has been assigned. */
```

### <a name="see-also"></a>参照

- gx_display_language_table_set
- gx_studio_display_configure

## <a name="gx_display_color_set"></a>gx_display_color_set

1 つのカラー値を再割り当てします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_display_color_set(
    GX_DISPLAY *display,
    GX_RESOURCE_ID color_id, 
    GX_COLOR new_color);
```

### <a name="description"></a>説明

このサービスは、指定されたカラー ID に関連付けられているカラー値を再割り当てします。 これを使用すると、まったく新しいカラー テーブルを指定しなくても、ディスプレイのカラー テーブルを変更できます。 指定するカラー値は、ディスプレイでサポートされているネイティブ形式である必要があります。

### <a name="parameters"></a>パラメーター

- **display** ディスプレイ コントロール ブロックへのポインター
- **color_id** 再割り当てするカラー ID
- **new_color** この color_id スロットに割り当てるカラー値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 色の再割り当てが成功しました
- **GX_INVALID_RESOURCE_ID** (0x33) カラー ID が無効です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_DISPLAY** (0x1D) ディスプレイが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Change value of color MY_COLOR_ID. */
status = gx_display_color_set(&my_display, MY_COLOR_ID, 0x5454);

/* If status is GX_SUCCESS the color has been reassigned. */
```

### <a name="see-also"></a>参照

- gx_display_color_table_set

## <a name="gx_display_color_table_set"></a>gx_display_color_table_set

ディスプレイにカラー テーブルを割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_display_color_table_set(
    GX_DISPLAY *display,
    GX_COLOR *color_table, 
    INT color_count);
```

### <a name="description"></a>説明

このサービスは、ディスプレイで使用するカラー テーブルを再割り当てします。 通常、このサービスは GUIX Studio で生成されたディスプレイの構成関数によって呼び出されますが、アプリケーション ソフトウェアから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **display** ディスプレイ コントロール ブロックへのポインター
- **color_table** ディスプレイのネイティブ形式のカラー値の配列。
- **color_count** カラー テーブル内のエントリの数を示します

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) カラー テーブルの設定が成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_DISPLAY** (0x1D) ディスプレイが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_COLOR default_table[32] = { … };

/* Change the color table */
status = gx_display_color_table_set(&my_display, default_table, 32);

/* If status is GX_SUCCESS the color table has been reassigned. */
```

### <a name="see-also"></a>参照

- gx_display_color_set

## <a name="gx_display_create"></a>gx_display_create

ディスプレイを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_display_create(
    GX_DISPLAY *display, 
    GX_CONST CHAR *name,
    UINT (*display_driver_setup)(GX_DISPLAY *),
    GX_VALUE width, 
    GX_VALUE height);
```

### <a name="description"></a>説明

このサービスは、ディスプレイを作成し、ディスプレイ ドライバー設定関数を呼び出します。 GUIX はこのディスプレイを取得し、ディスプレイの内部リストに追加します。

### <a name="parameters"></a>パラメーター

- **display** ディスプレイ コントロール ブロックへのポインター
- **name** ディスプレイの名前
- **display_driver_setup** ディスプレイ ドライバー設定関数へのポインター
- **optional_driver_info** オプションのドライバー情報へのポインター
- **color_format** **付録 C** で定義されているカラー形式
- **width** X 軸のピクセル数
- **height** Y 軸のピクセル数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ディスプレイの作成が成功しました
- **GX_SYSTEM_ERROR** (0xFE) ディスプレイの設定が失敗しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_SIZE** (0x23) ディスプレイ コントロール ブロックのサイズが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_DISPLAY my_display;

UINT my_driver_setup_callback(GX_DISPLAY *display)
{
    …
}

/* Create screen “my_display”. */
status = gx_display_create(&my_display, “my display”,
    my_driver_setup_callback, 320, 480);

/* If status is GX_SUCCESS, the screen “my_display” has been created. */
```

### <a name="see-also"></a>参照

- gx_display_delete

## <a name="gx_display_delete"></a>gx_display_delete


ディスプレイを破棄します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_display_delete(
    GX_DISPLAY *display,
    VOID (*display_driver_cleanup)(GX_DISPLAY *));
```

### <a name="description"></a>説明

このサービスは、ディスプレイをシャットダウンし、割り当てられたリソースをクリーンアップします。

### <a name="parameters"></a>パラメーター

- **display** ディスプレイ コントロール ブロックへのポインター
- **display_driver_cleanup** ディスプレイ ドライバーのクリーンアップ関数へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ディスプレイの削除が成功しました
- **GX_FAILURE** (0x10) 作成されたディスプレイ リストが NULL です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
VOID driver_cleanup_callback(GX_DISPLAY *display)
{
    …
}

/* Delete a display “my_display”. */
status = gx_display_delete(&my_display, driver_cleanup_callback);

/* If status is GX_SUCCESS the screen “my_display” has been destroyed. */
```

### <a name="see-also"></a>参照

- gx_canvas_block_move
- gx_canvas_line_draw
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw
- gx_canvas_text_draw
- gx_display_create

## <a name="gx_display_font_table_set"></a>gx_display_font_table_set

ディスプレイのフォント テーブルを割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_display_font_table_set(
    GX_DISPLAY *display,
    GX_FONT **font_table, 
    INT table_size);
```

### <a name="description"></a>説明

このサービスは、ディスプレイで使用するフォント テーブルを再割り当てします。 通常、このサービスは GUIX Studio で生成されたディスプレイの構成関数によって呼び出されますが、アプリケーション ソフトウェアから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **display** ディスプレイ コントロール ブロックへのポインター
- **font_table** GX_FONT ポインターの配列。
- **table_size** テーブル内のフォント数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) フォント テーブルの設定が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_FONT *font_table[32] = { … };

/* Assign font table */
status = gx_display_font_table_set(&my_display, font_table, 32);

/* If status is GX_SUCCESS, the font table has been reassigned. */
```

### <a name="see-also"></a>参照

- gx_display_color_set
- gx_display_color_table_set
- gx_display_pixelmap_table_set

## <a name="gx_display_language_table_get"></a>gx_display_language_table_get

ディスプレイの言語テーブルを取得します (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_display_language_table_get(
    GX_DISPLAY *display,
    GX_CHAR **table, 
    GX_UBYTE *language_count,
    UINT *string_table_size);
```

### <a name="description"></a>説明

このサービスは、指定されたディスプレイから言語テーブルを取得します。 アプリケーションで実行時にこのサービスを使用すると、動的に定義された文字列を使用して、ディスプレイの言語テーブルを変更できます。

この API は、非推奨であり、古いスタイルの言語テーブル (つまり、バージョン 5.6 より前のライブラリ バージョン用に生成された Studio 生成のリソース ファイル) を使用するアプリケーションに対してのみサポートされます。 新しいアプリケーションでは gx_display_language_table_get_ext() を使用してください。

### <a name="parameters"></a>パラメーター

- **display** ディスプレイ コントロール ブロックへのポインター
- **table** テーブル ポインターを受け取るアドレス
- **language_count** 言語数を受け取るアドレス
- **string_table_size** 文字列テーブルのサイズを受け取るアドレス

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) フォント テーブルの設定が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_CHAR **language_table;
GX_UBYTE language_count;
UINT string_count;

/* Retrieve language table */
status = gx_display_language_table_get(&my_display,
        &language_table, &language_count, &string_count);

/* If status is GX_SUCCESS, the language table has been retrieved.
```

### <a name="see-also"></a>参照

- gx_display_language_table_set
- gx_display_active_langauge_set
- gx_display_string_get
- gx_display_language_table_get_ext

## <a name="gx_display_language_table_get_ext"></a>gx_display_language_table_get_ext

ディスプレイの言語テーブルを取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_display_language_table_get_ext(
    GX_DISPLAY *display,
    GX_STRING **table, 
    GX_UBYTE *language_count, 
    UINT *string_table_size);
```

### <a name="description"></a>説明

このサービスは、指定されたディスプレイから言語テーブルを取得します。 アプリケーションで実行時にこのサービスを使用すると、動的に定義された文字列を使用して、ディスプレイの言語テーブルを変更できます。

### <a name="parameters"></a>パラメーター

- **display** ディスプレイ コントロール ブロックへのポインター
- **table** テーブル ポインターを受け取るアドレス
- **language_count** 言語数を受け取るアドレス
- **string_table_size** 文字列テーブルのサイズを受け取るアドレス

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) フォント テーブルの設定が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_STRING **language_table;
GX_UBYTE language_count;
UINT string_count;

/* Retrieve language table */
status = gx_display_language_table_get_ext(&my_display,
    &language_table, &language_count, &string_count);

/* If status is GX_SUCCESS, the language table has been retrieved. */
```

### <a name="see-also"></a>参照

- gx_display_language_table_set_ext
- gx_display_active_langauge_set
- gx_display_string_get_ext

## <a name="gx_display_language_table_set"></a>gx_display_language_table_set

ディスプレイの言語テーブルを割り当てます (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_display_language_table_set(
    GX_DISPLAY *display,
    GX_CHAR **table, 
    GX_UBYTE number_of_languages, 
    UINT number_of_strings);
```

### <a name="description"></a>説明

このサービスは非推奨です。新しいアプリケーションでは gx_display_language_table_set_ext() を使用してください。 このサービスは、バージョン 5.6 より前のライブラリ バージョンをターゲットとする、Studio で生成されたリソース ファイルとの互換性のためにのみサポートされています。

このサービスは、ディスプレイで使用する言語テーブルを再割り当てします。 通常、このサービスは GUIX Studio で生成された関数 gx_studio_display_configure によって呼び出されますが、アプリケーション ソフトウェアから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **display** ディスプレイ コントロール ブロックへのポインター
- **table** 言語テーブル
- **number_of_languages** 指定したテーブル内の列の数
- **number_of_strings** 各テーブル列内の文字列の数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) フォント テーブルの設定が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_CHAR ***language_table= my_app_language_table;

/* Assign language table */
status = gx_display_language_table_set(&my_display, language_table,
5, 232);

/* If status is GX_SUCCESS, the language table has been reassigned. */
```

### <a name="see-also"></a>参照

- gx_display_active_language_set
- gx_display_string_get

## <a name="gx_display_language_table_set_ext"></a>gx_display_language_table_set_ext

ディスプレイの言語テーブルを割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_display_language_table_set_ext(
    GX_DISPLAY *display,
    GX_STRING **table, 
    GX_UBYTE number_of_languages,
    UINT number_of_strings);
```

### <a name="description"></a>説明

このサービスは、ディスプレイで使用する言語テーブルを再割り当てします。 通常、このサービスは GUIX Studio で生成された関数 gx_studio_display_configure によって呼び出されますが、アプリケーション ソフトウェアから呼び出すこともできます。

ランタイム言語テーブルの割り当ては、通常、gx_binres_language_table_load() を使用してバイナリ リソース ファイルから言語が読み込まれる場合に実行されます。

### <a name="parameters"></a>パラメーター

- **display** ディスプレイ コントロール ブロックへのポインター
- **table** 言語テーブル
- **number_of_languages** 指定したテーブル内の列の数
- **number_of_strings** 各テーブル列内の文字列の数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) フォント テーブルの設定が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_STRING_LENGTH** (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_STRING **language_table = my_app_language_table;

/* Assign the language table */
status = gx_display_language_table_set_ext(&my_display,
    language_table, 5, 132);

/* If status is GX_SUCCESS, the language table has been reassigned. */
```

### <a name="see-also"></a>参照

- gx_display_active_language_set
- gx_display_string_get

## <a name="gx_display_pixelmap_table_set"></a>gx_display_pixelmap_table_set

ディスプレイのフォント テーブルを割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_display_pixelmap_table_set(
    GX_DISPLAY *display,
    GX_PIXELMAP **pixelmap_table, 
    INT table_size);
```

### <a name="description"></a>説明

このサービスは、ディスプレイで使用するピクセルマップ テーブルを再割り当てします。 通常、このサービスは Studio で生成されたディスプレイの構成関数によって呼び出されますが、アプリケーション ソフトウェアから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **display** ディスプレイ コントロール ブロックへのポインター
- **pixelmap_table** GX_PIXELMAP ポインターの配列。
- **table_size** テーブル内のピクセルマップの数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ピクセルマップ テーブルの設定が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_PIXELMAP *pixelmap_table[32] = { … };

/* Assign pixelmap table */
status = gx_display_pixelmap_table_set(&my_display, pixelmap_table, 32);

/* If status is GX_SUCCESS the pixelmap table has been reassigned. */
```

### <a name="see-also"></a>参照

- gx_display_color_set
- gx_display_color_table_set
- gx_display_font_table_set

## <a name="gx_display_string_get"></a>gx_display_string_get

アクティブな文字列テーブルから文字列を取得します (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_display_string_get(
    GX_DISPLAY *display,
    GX_RESOURCE_ID string_id, 
    GX_CONST GX_CHAR **string);
```

### <a name="description"></a>説明

このサービスは非推奨です。gx_display_string_get_ext() を使用してください。

このサービスは、指定されたディスプレイのアクティブな文字列テーブルから文字列を取得します。 アクティブな言語を使用して、ディスプレイに割り当てられている言語テーブルから文字列が選択されます。

文字列 ID は GUIX Studio によって生成され、application resources.h ヘッダー ファイル内にあります。

### <a name="parameters"></a>パラメーター

- **display** ディスプレイ コントロール ブロックへのポインター
- **string_id** GUIX Studio によって生成される文字列 ID。
- **string** 文字列ポインター変数のアドレス

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 文字列の取得に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_RESOURCE_ID** (0X33) 文字列 ID が無効です
- **GX_PTR_ERROR** (0x07) ディスプレイのポインターが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_CHAR *string;

/* Retrieve string value */
status = gx_display_string_get(&my_display,
    GX_STRING_ID_MONDAY, &string);

/* If status is GX_SUCCESS, the string has been retrieved. */
```


### <a name="see-also"></a>参照

- gx_display_active_language_set
- gx_display_language_table_set

## <a name="gx_display_string_get_ext"></a>gx_display_string_get_ext

アクティブな文字列テーブルから文字列を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_display_string_get_ext(
    GX_DISPLAY *display,
    GX_RESOURCE_ID string_id,
    GX_STRING *string);
```

### <a name="description"></a>説明

このサービスは、指定されたディスプレイのアクティブな文字列テーブルから文字列を取得します。 アクティブな言語を使用して、ディスプレイに割り当てられている言語テーブルから文字列が選択されます。

文字列 ID は GUIX Studio によって生成され、application resources.h ヘッダー ファイル内にあります。

### <a name="parameters"></a>パラメーター

- **display** ディスプレイ コントロール ブロックへのポインター
- **string_id** GUIX Studio によって生成される文字列 ID。
- **string** GX_STRING 変数のアドレス。
- **string.gx_string_ptr** と
- **string.gx_string_length** が返されます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 文字列の取得に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_RESOURCE_ID** (0X33) 文字列 ID が無効です
- **GX_PTR_ERROR** (0x07) ディスプレイのポインターが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_STRING string;

/* Retrieve string value */
status = gx_display_string_get_ext(&my_display,
    GX_STRING_ID_MONDAY, &string);

/* If status is GX_SUCCESS, the string has been retrieved. */
```

### <a name="see-also"></a>参照

- gx_display_active_language_set
- gx_display_language_table_set


## <a name="gx_display_string_table_get"></a>gx_display_string_table_get


アクティブな文字列テーブルを取得します (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_display_string_table_get(
    GX_DISPLAY *display,
    GX_UBYTE language, 
    GX_CHAR ***table,
    UINT *table_size);
```

### <a name="description"></a>説明

このサービスは非推奨になり、gx_display_string_table_get_ext() に置き換えられています。

このサービスは、アクティブな言語に関連付けられている文字列テーブルを取得します。 このサービスは頻繁には使用されませんが、文字列テーブルに対して実行時の変更を加える必要があるアプリケーションの補完のために用意されています。

### <a name="parameters"></a>パラメーター

- **display** ディスプレイ コントロール ブロックへのポインター
- **language** 取得するテーブル列。
- **table** ポインターを返す変数のアドレス。
- **table_size** テーブル サイズを返す変数のアドレス

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) フォント テーブルの設定が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_NOT_FOUND** (0x09) 言語インデックスが無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_CHAR **string_table;
UINT table_size;

/* Retrieve string table */
status = gx_display_string_table_get(&my_display, LANGUAGE_ENGLISH,
    &string_table, &table_size);

/* If status is GX_SUCCESS, the string table has been retrieved. */
```

### <a name="see-also"></a>参照

- gx_display_color_set
- gx_display_color_table_set
- gx_display_pixelmap_table_set

## <a name="gx_display_string_table_get_ext"></a>gx_display_string_table_get_ext


アクティブな文字列テーブルを取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_display_string_table_get(
    GX_DISPLAY *display,
    GX_UBYTE language, 
    GX_STRING **table, 
    UINT *table_size);
```

### <a name="description"></a>説明

このサービスは、アクティブな言語に関連付けられている文字列テーブルを取得します。 このサービスは頻繁には使用されませんが、文字列テーブルに対して実行時の変更を加える必要があるアプリケーションの補完のために用意されています。

### <a name="parameters"></a>パラメーター

- **display** ディスプレイ コントロール ブロックへのポインター
- **language** 取得するテーブル列。
- **table** ポインターを返す変数のアドレス。
- **table_size** テーブル サイズを返す変数のアドレス

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) フォント テーブルの設定が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_NOT_FOUND** (0x09) 言語インデックスが無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_STRING *string_table;
UINT table_size;

/* Retrieve string table */
status = gx_display_string_table_get_ext(&my_display,
    LANGUAGE_ENGLISH, &string_table, &table_size);

/* If status is GX_SUCCESS, the string table has been retrieved. */
```

### <a name="see-also"></a>参照

- gx_display_color_set
- gx_display_color_table_set
- gx_display_pixelmap_table_set

## <a name="gx_display_theme_install"></a>gx_display_theme_install


指定されたディスプレイにテーマをインストールします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_display_theme_install(
    GX_DISPLAY *display, 
    GX_THEME *theme_table);
```

### <a name="description"></a>説明

このサービスは、指定されたディスプレイにテーマをインストールします。 通常、このサービスは Studio で生成されたディスプレイの構成関数によって呼び出されますが、アプリケーション ソフトウェアから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **display** ディスプレイ コントロール ブロックへのポインター
- **theme_table** インストールするテーマ テーブル

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) テーマ テーブルが正常にインストールされました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) テーマ テーブル ポインターが無効です
- **GX_INVALID_DISPLAY** (0x1D) ディスプレイが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_THEME theme_1;

&theme_table[1] = {
    &theme_1,
    …
}

/* Define resource tables. */
GX_COLOR color_table[32] = {…};
GX_FONT *font_table[32] = {…};
GX_PIXELMAP *pixelmap_table[32] = { … };

/* Define scroll appearance. */
GX_SCROLLBAR_APPEARANCE scroll_appearance;

memset(&scroll_appearance, 0, sizeof(GX_SCROLLBAR_APPEARANCE));

scroll_appearance.gx_scroll_width = 20;
scroll_appearance.gx_scroll_thumb_width = 18;
scroll_appearance.gx_scroll_thumb_color =
    GX_COLOR_ID_SCROLL_BUTTON;
scroll_appearance.gx_scroll_thumb_border_color =
    GX_COLOR_ID_SCROLL_BUTTON;
scroll_appearance.gx_scroll_button_color =
    GX_COLOR_ID_SCROLL_BUTTON;
scroll_appearance.gx_scroll_thumb_travel_min = 20;
scroll_appearance.gx_scroll_thumb_travel_max = 20;
scroll appearance.gx_scroll_thumb_border_style =
    GX_STYLE_BORDER_THIN;

theme_1.theme_color_table = color_table;
theme_1.theme_font_table = font_table;
theme_1.theme_pixlemap_table = pixelmap_table;
theme_1.theme_palette = GX_NULL;
theme_1.theme_vertical_scrollbar_appearance = scroll_appearance;
theme_1.theme_horizontal_scrollbar_appearance = scroll_appearance;
theme_1.theme_vertical_scroll_style = GX_SCROLLBAR_RELATIVE_THUMB;
theme_1.theme_horizontal_scroll_style =
    GX_SCROLLBAR_RELATIVE_THUMB;
theme_1.theme_color_table_size = 32;
theme_1.theme_font_table_size = 32;
theme_1.theme_pixelmap_table_size = 32;
theme_1.theme_palette_size = 0;

/* Install theme table. */
status = gx_display_theme_install(&my_display, theme_table);

/* If status is GX_SUCCESS the theme table has been installed. */
```

### <a name="see-also"></a>参照

- gx_display_color_set
- gx_display_color_table_set
- gx_display_font_table_set

## <a name="gx_drop_list_close"></a>gx_drop_list_close


ドロップダウン リストを閉じます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_drop_list_close(GX_DROP_LIST *drop_list);
```

### <a name="description"></a>説明

このサービスは、指定されたドロップダウン リストのポップアップ リストを閉じます。

### <a name="parameters"></a>パラメーター

- **drop_list** ドロップダウン リストのコントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ドロップダウン リストが正常に閉じられました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Close a drop list. */
status = gx_drop_list_close(&drop_list);

/* If status is GX_SUCCESS, the drop list is closed. */
```

### <a name="see-also"></a>参照

- gx_drop_list_create
- gx_drop_list_event_process
- gx_drop_list_open

gx_drop_list_pixelmap_set, gx_drop_list_popup_get

## <a name="gx_drop_list_create"></a>gx_drop_list_create


ドロップダウン リストを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_drop_list_create(
    GX_DROP_LIST *drop_list, 
    GX_CONST
    GX_CHAR *name, 
    GX_WIDGET *parent,
    INT total_rows, 
    INT open_height,
    VOID (*callback)(GX_VERTICAL_LIST *, 
    GX_WIDGET *, INT),
    ULONG style, 
    USHORT drop_list_id,
    GX_CONST GX_RECTANGLE *size)
```

### <a name="description"></a>説明

このサービスは、ドロップダウン リストを作成します。 ドロップダウン リストは、ドロップダウン リスト ウィジェットと、ドロップダウン リストが開いたときに表示されるポップアップの縦方向のリストを組み合わせたものです。 ポップアップの縦方向のリストはドロップダウン リスト ウィジェットが作成されると自動的に作成され、ドロップリスト ウィジェットが開いたり閉じたりすると、それに応じて表示または非表示になります。

ドロップダウン リスト ウィジェットでは、2 つの関連するピクセルマップがサポートされています。 1 つ目は、Studio のプロパティ ビューの "リスト壁紙" といいます。これは、ドロップダウン リスト ウィジェットを開いたときに表示される縦方向のリストの背景として表示される、オプションの壁紙ピクセルマップです。 2 つ目のピクセルマップは、Studio のプロパティ ビューの "背景画像" といいます。これは、ドロップダウン リスト自体の背景として表示されるオプションの画像です。

ドロップダウン リスト ウィジェットでは、ドロップダウン リストを開いたり閉じたりするために使用される子ウィジェットを持つことができます (ただし、必須ではありません)。 これは通常、アイコンまたはボタンのウィジェットですが、親のドロップダウン リストを開くか閉じるかの切り替えにカスタム ウィジェットを使用することもできます。 この子ウィジェットでドロップダウン リストを操作できるようにするためのキー設定では、この子ウィジェットに、定義済みウィジェット ID ID_DROP_LIST_BUTTON が必要です。

ドロップダウン リストを開いたり閉じたりする子ウィジェットを定義するには、最初に子ウィジェットをドロップダウン リストに追加し、この子ウィジェットをドロップダウン リスト内で必要な位置に配置します。

![ドロップダウン リストのスクリーンショット。](./media/guix/image6.jpg)

次に、Studio のプロパティ ビューを使用して、この子ウィジェットに ID 値 ID_DROP_LIST_BUTTON を割り当てます。これは、親のドロップダウン リストによって認識される、内部的に定義された ID 値です。

![Studio のプロパティ ビューのスクリーンショット。](./media/guix/image7.jpg)

### <a name="parameters"></a>パラメーター
- **drop_list** ドロップダウン リストのコントロール ブロックへのポインター
- **name** ドロップダウン リストの名前
- **parent** 親ウィジェットへのポインター
- **total_rows** ドロップダウン リストの合計行数
- **open_height** ドロップダウン リストを開いたときに表示される縦方向のリストの高さ。
- **callback** リストがスクロールされたときに縦方向のリストによって呼び出される関数。 詳細については、GX_VERTICAL_LIST のドキュメントを参照してください。
- **style** ドロップダウン リストの枠線のスタイル。
- **drop_list_id** アプリケーションで定義されたドロップダウン リストの ID
- **size** ドロップダウン リストの大きさ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ドロップダウン リストの作成が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットは既に作成されています

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_DROP_LIST my_drop_list;
VOID list_row_create(GX_VERTICAL_LIST *list,
                     GX_WIDGET *row, INT index);
{
    …
}

GX_RECTANGLE size;

gx_utility_rectangle_define(&size, 10, 10, 80, 40);

status = gx_drop_list_create(&my_drop_list,
    "my drop list", GX_NULL,
    10, 100, list_row_create,
    GX_STYLE_BORDER_RECESSED | GX_STYLE_ENABLED,
    ID_DROP_LIST, &size)

/* Is status is GX_SUCCESS, the drop list was successfully created. */
```

### <a name="see-also"></a>参照:

- gx_drop_list_close
- gx_drop_list_event_process
- gx_drop_list_open
- gx_drop_list_pixelmap_set
- gx_drop_list_popup_get

## <a name="gx_drop_list_event_process"></a>gx_drop_list_event_process


ドロップダウン リストのイベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_drop_list_event_process(
    GX_DROP_LIST *list, 
    GX_EVENT *event);
```

### <a name="description"></a>説明

このサービスは、ドロップダウン リストのイベントを処理します。

### <a name="parameters"></a>パラメーター

- **drop_list** ドロップダウン リスト ウィジェットのコントロール ブロック
- **event** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ドロップダウン リストのイベント処理に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Call generic drop list event processing as part of custom event processing function. */

UINT custom_drop_list_event_process(GX_DROP_LIST *drop_list,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default drop list
            event processing */
        status = gx_drop_list_event_process(drop_list, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>参照

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_open
- gx_drop_list_pixelmap_set
- gx_drop_list_popup_get

## <a name="gx_drop_list_open"></a>gx_drop_list_open


ドロップダウン リストを開きます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_drop_list_open(GX_DROP_LIST *drop_list);
```

### <a name="description"></a>説明

このサービスは、以前に作成されたドロップダウン リストを開きます。

### <a name="parameters"></a>パラメーター

- **drop_list** ドロップダウン リストのコントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ドロップダウン リストの作成が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_DROP_LIST mylist;

/* Open the popup list of “mylist”. */
status = gx_drop_list_open(&mylist);

/* If status == GX_SUCCESS, the popup list of “mylist” has been displayed. */
```

### <a name="see-also"></a>参照

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_event_process
- gx_drop_list_pixelmap_set
- gx_drop_list_popup_get

## <a name="gx_drop_list_pixelmap_set"></a>gx_drop_list_pixelmap_set


ドロップダウン リストに背景画像を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_drop_list_pixelmap_set(
    GX_DROP_LIST *drop_list,
    GX_RESOURCE_ID id);
```

### <a name="description"></a>説明

ドロップダウン リストに背景画像を割り当てます。 このピクセルマップは、ドロップダウン リスト ウィジェットそのものの背景として使用されます。リストを開いたときに表示されるポップアップの縦方向のリストのためのものではありません。 ピクセルマップをドロップダウン リストのポップアップに割り当てるには、最初に gx_drop_list_popup_get を呼び出してポップアップ リストへのポインターを取得し、次に gx_window_wallpaper_set () を使用して、このポップアップ リストにピクセルマップを割り当てる必要があります。

### <a name="parameters"></a>パラメーター

- **drop_list** ドロップダウン リストのコントロール ブロックへのポインター
- **id** ピクセルマップのリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ドロップダウン リストのピクセルマップが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_RESOURCE_ID** (0x33) ピクセルマップ ID が無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_DROP_LIST mylist;

/* create the drop list here */

/* Assign a pixelmap id, which will turn on the list button */
status = gx_drop_list_pixelmap_set(&mylist,
    GX_PIXELMAP_ID_DROP_LIST_BACKGROND);

/* If status is GX_SUCCESS, the pixelmap was successfully set. */
```

### <a name="see-also"></a>参照:

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_event_process
- gx_drop_list_open
- gx_drop_list_popup_get

## <a name="gx_drop_list_popup_get"></a>gx_drop_list_popup_get


ポップアップの縦方向のリストへのポインターを取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_drop_list_popup_get(
    GX_DROP_LIST *drop_list,
    GX_VERTICAL_LIST **return_list);
```

### <a name="description"></a>説明

ドロップダウン リスト ウィジェットは、ドロップダウン リスト ウィジェット自体と、ドロップダウン リスト ウィジェットが開いたときに表示されるポップアップの縦方向のリストで構成されます。 このサービスは、ドロップダウン リストの縦方向のリスト コンポーネントへのポインターを取得しするため、この縦方向のリスト上の API サービスをアプリケー00ションから直接呼び出すことができます。

### <a name="parameters"></a>パラメーター

- **drop_list** ドロップダウン リストのコントロール ブロックへのポインター
- **return_list** ドロップダウン リストに格納されている縦方向のリストへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 縦のポップアップ リストの取得に成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_DROP_LIST drop_list;
GX_VERTICAL_LIST *vertical_list;

/* Retrieve the popup list of “drop_list”. */
status = gx_drop_list_popup_get(&drop_list, &vertical_list)

/* If status is GX_SUCCESS, the popup list was successfully retrieved. */
```

### <a name="see-also"></a>参照:

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_open
- gx_drop_list_pixelmap_set

## <a name="gx_generic_scroll_wheel_children_position"></a>gx_generic_scroll_wheel_children_position
### <a name="position-children-for-the-generic-scroll-wheel"></a>汎用スクロール ホイールに子を配置します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_generic_scroll_wheel_children_position(
    GX_GENERIC_SCROLL_WHEEL *wheel)
```

### <a name="description"></a>説明

この関数では、汎用スクロール ホイールの行の高さに従って、汎用スクロール ホイールの子が配置されます。 この関数は、汎用スクロール ホイールが表示されている場合に既定で呼び出されます。

### <a name="parameters"></a>パラメーター

- **wheel** 汎用スクロール ホイール コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 汎用スクロール ホイールの子を正常に配置しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Position children in the generic scroll wheel. */
status = gx_generic_scroll_wheel_children_position (&wheel);

/* If status is GX_SUCCESS the children in the generic scroll wheel are positioned. */
```

### <a name="see-also"></a>参照

- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_generic_scroll_wheel_create
- gx_generic_scroll_wheel_draw
- gx_generic_scroll_wheel_event_process
- gx_generic_scroll_wheel_row_height_set
- gx_generic_scroll_wheel_total_rows_set

## <a name="gx_generic_scroll_wheel_create"></a>gx_generic_scroll_wheel_create


汎用スクロール ホイール を作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_generic_scroll_wheel_create(
    GX_GENERIC_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    INT total_rows,
    VOID (*callback)(GX_GENERIC_SCROLL_WHEEL *, GX_WIDGET *, INT),
    ULONG style,
    USHORT id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスにより、汎用スクロール ホイール ウィジェットが作成されます。

汎用スクロール ホイールは、子ウィジェットで構成されるスクロール ホイール ウィジェットの一種です。 その他の種類のスクロール ホイール ウィジェットも使用できます。 スクロール ホイール ウィジェットの階層、ウィジェットの種類、およびウィジェットの派生の詳細については、gx_scroll_wheel_create() API を参照してください。

GX_GENERIC_SCROLL_WHEEL は GX_SCROLL_WHEEL から派生し、すべての gx_scroll_wheel サービスをサポートしています。

スクロール ホイールをスクロールすると、すべてのスクロール ホイールの種類によって GX_EVENT_LIST_SELECT イベントがその親に対して生成されます。

### <a name="parameters"></a>パラメーター

- **wheel** 汎用スクロール ホイール コントロール ブロックへのポインター
- **name** 汎用スクロール ホイール ウィジェットの論理名
- **parent** 親ウィジェットへのポインター
- **total_rows** スクロール ホイールの合計行数。
- **callback** ウィジェットの行を作成するコールバック関数。 合計行数が子の数と一致する場合は、GX_NULL とすることができます。 子の数が合計行数よりも少ない場合、または GX_STYLE_WRAP スタイルが設定されている場合は、ウィジェットを再利用するためにこれを指定する必要があります。 その場合は、表示される行の数よりも子の数が 1 つ多いことを確認します。
- **style** 汎用スクロール ホイールのスタイル。 **付録 D** には、ウィジェット固有のスタイルと、すべてのウィジェット用に事前に定義されている一般的なスタイルが含まれています。
- **id** 汎用スクロール ホイールのアプリケーション定義 ID
- **size** 汎用スクロール ホイール ウィジェットのディメンション

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 汎用スクロール ホイールが正常に作成されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です
- **GX_INVALID_VALUE** (0x22) 行数が無効です
- **GX_INVALID_WIDGET** (0x12) 親ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C

/* Define visible rows.  */
#define VISIBLE_ROWS 5

/* Define row memory.  */
GX_NUMERIC_PROMPT row_memory[VISIBLE_ROWS + 1];

/* Define callback function.  */
VOID row_create(GX_GENERIC_SCROLL_WHEEL *wheel, GX_WIDGET *widget, INT index)
{
GX_NUMERIC_PROMPT *row = (GX_PROMPT *)widget;
GX_BOOL result;
GX_RECTANGLE size;

    gx_widget_created_test(widget, &result);

    if(!result)
    {
        gx_numeric_prompt_create(row, "", wheel, 0, GX_STYLE_ENABLED, 0, &size);
    }

    gx_numeric_prompt_value_set(row, index);
}

/* Create "generic_wheel” with 20 rows.  */
status = gx_generic_scroll_wheel_create(&generic_wheel, “generic_wheel”, &parent, 20, row_create,
                                       GX_STYLE_ENABLED, WHEEL_ID, &size);

/* If status is GX_SUCCESS the generic scroll wheel "generic_wheel”" has been created. */

/* Create children for generic scroll wheel.  */
for(index = 0; index <= VISIBLE_ROWS; index++)
{
    row_create(generic_wheel, (GX_WIDGET *)&row_memory[index], index);
}
```

### <a name="see-also"></a>参照

- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_generic_scroll_wheel_children_position
- gx_generic_scroll_wheel_draw
- gx_generic_scroll_wheel_event_process
- gx_generic_scroll_wheel_row_height_set
- gx_generic_scroll_wheel_total_rows_set

## <a name="gx_generic_scroll_wheel_draw"></a>gx_generic_scroll_wheel_draw
### <a name="draw-window"></a>ウィンドウを描画する

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_generic_scroll_wheel_draw(GX_GENERIC_SCROLL_WHEEL *wheel);
```

### <a name="description"></a>説明

このサービスにより、汎用スクロール ホイールが描画されます。 このサービスは通常、キャンバスの更新中に内部的に呼び出されますが、カスタムの汎用スクロール ホイール描画関数から呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **wheel** 汎用スクロール ホイール コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom generic scroll wheel draw function. */

VOID my_custom_generic_scroll_wheel_draw(GX_GENERIC_SCROLL_WHEEL *wheel)
{
    /* Call default generic scroll wheel draw. */
    gx_generic_scroll_wheel_draw(wheel);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_generic_scroll_wheel_children_position
- gx_generic_scroll_wheel_create
- gx_generic_scroll_wheel_event_process
- gx_generic_scroll_wheel_row_height_set
- gx_generic_scroll_wheel_total_rows_set

## <a name="gx_generic_scroll_wheel_event_process"></a>gx_generic_scroll_wheel_event_process
### <a name="process-generic-scroll-wheel-event"></a>汎用スクロール ホイールのイベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_generic_scroll_wheel_event_process(
    GX_GENERIC_SCROLL_WHEEL *wheel, 
    GX_EVENT *event);
```

### <a name="description"></a>説明

このサービスにより、このウィンドウのイベントが処理されます。

### <a name="parameters"></a>パラメーター

- **wheel** 汎用スクロール ホイール コントロール ブロックへのポインター
- **event** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 汎用スクロール ホイールのイベント処理が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Call generic generic scroll wheel event processing as part of custom event processing function. */

UINT custom_generic_scroll_wheel_event_process(GX_GENERIC_SCROLL_WHEEL *wheel,
                                               GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
        case xyz:

            /* Insert custom event handling here */
            break;

        default:

            /* Pass all other events to the default generic scroll wheel
            event processing */
            status = gx_generic_scroll_wheel_event_process(wheel, event);
            break;
        }
        return status;
}
```

### <a name="see-also"></a>参照

- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_generic_scroll_wheel_children_position
- gx_generic_scroll_wheel_create
- gx_generic_scroll_wheel_draw
- gx_generic_scroll_wheel_row_height_set
- gx_generic_scroll_wheel_total_rows_set

## <a name="gx_generic_scroll_wheel_row_height_set"></a>gx_generic_scroll_wheel_row_height_set


各ホイール行に行の高さを割り当てる

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_generic_scroll_wheel_row_height_set(
    GX_GENERIC_SCROLL_WHEEL *wheel,
    GX_VALUE row_height);
```

### <a name="description"></a>説明

このサービスでは、スクロール ホイールの各行に行の高さが割り当てられます。

### <a name="parameters"></a>パラメーター

- **wheel** 汎用スクロール ホイール コントロール ブロックへのポインター
- **row_height** 行の高さの値 (ピクセル単位)。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) スクロール ホイールの高さが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE** (0x22) 行の高さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
status = gx_generic_scroll_wheel_row_height_set(&wheel, 40);

/* if status == GX_SUCCESS the wheel row height has been set to 40
pixels. */
```

### <a name="see-also"></a>参照

- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_generic_scroll_wheel_children_position
- gx_generic_scroll_wheel_create
- gx_generic_scroll_wheel_draw
- gx_generic_scroll_wheel_event_process
- gx_generic_scroll_wheel_total_rows_set

## <a name="gx_generic_scroll_wheel_total_rows_set"></a>gx_generic_scroll_wheel_total_rows_set


使用可能な合計スクロール ホイール行数を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_generic_scroll_wheel_total_rows_set(
    GX_GENERIC_SCROLL_WHEEL *wheel,
    INT total_rows);
```

### <a name="description"></a>説明

このサービスにより、汎用スクロール ホイールの合計行数の割り当てまたは変更が行われます。

### <a name="parameters"></a>パラメーター

- **wheel** 汎用スクロール ホイール コントロール ブロックへのポインター
- **total_rows** ユーザーに表示されるホイール行の合計数。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 汎用スクロール ホイールの合計行が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE** (0x22) 合計行数が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
status = gx_generic_scroll_wheel_total_rows_set(&wheel, 20);

/* if status == GX_SUCCESS the scroll wheel has been changed to
display 20 total rows */
```
### <a name="see-also"></a>参照

- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_generic_scroll_wheel_children_position
- gx_generic_scroll_wheel_create
- gx_generic_scroll_wheel_draw
- gx_generic_scroll_wheel_event_process
- gx_generic_scroll_wheel_row_height_set

## <a name="gx_horizontal_list_children_position"></a>gx_horizontal_list_children_position


横方向のリストの子を配置します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_horizontal_list_children_position(GX_HORIZONTAL_LIST *horizontal_list);
```

### <a name="description"></a>説明

この関数は、横方向のリストの子を配置します。 この関数は、一覧で GX_EVENT_SHOW イベントが受信されたときに自動的に呼び出されますが、一覧が参照可能になった後に変更された場合は直接呼び出す必要があります。

### <a name="parameters"></a>パラメーター

- **horizontal_list** 横方向のリストのコントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 横方向のリストの子が正常に配置されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Position children in the horizontal list */
status = gx_horizontal_list_children_position (&horizontal_list);

/* If status is GX_SUCCESS the children in the horizontal list are positioned. */
```

### <a name="see-also"></a>参照

- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_create"></a>gx_horizontal_list_create


横方向のリストを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_horizontal_list_create(
    GX_HORIZONTAL_LIST *horizontal_list,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    INT total_columns,
    VOID (*callback)(GX_HORIZONTAL_LIST *, 
    GX_WIDGET *, INT),
    ULONG style, 
    USHORT horizontal_list_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスは、横方向のリストを作成します。

### <a name="parameters"></a>パラメーター

- **horizontal_list** 横方向のリストのウィジェット コントロール ブロック
- **name** 横方向のリストの名前
- **parent** 親ウィジェットへのポインター
- **total_columns** 横方向のリストの合計列数
- **callback** アプリケーションによって提供されるコールバック関数へのポインターです。 このコールバック関数は、横方向のリストがスクロールされたときに、新しく表示されるリスト項目を作成するために呼び出されます。 このように、横方向のリストでは、ユーザー定義のあらゆるウィジェットの種類をリスト項目として表示できます。
- **style** スクロール バー ウィジェットのスタイル。 **付録 D** には、すべてのウィジェット用に事前に定義されている一般的なスタイルおよびウィジェット固有のスタイルが記載されています。
- **horizontal_list_id** アプリケーションで定義された横方向のリストの ID
- **size** 横方向のリストの大きさ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 横方向のリストの作成に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です
- **GX_INVALID_VALUE** (0x22) 列数が無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Create horizontal list “my_list” with 5 columns. */
status = gx_horizontal_list_create(&my_list, “my_list”, &my_parent,
    5, callback, GX_STYLE_WRAP, MY_LIST_ID, &size);

/* If status is GX_SUCCESS the horizontal list “my_list” has been created. */
```

### <a name="see-also"></a>参照

- gx_horizontal_list_children_position
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_event_process"></a>gx_horizontal_list_event_process


横方向のリストのイベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_horizontal_list_event_process(
    GX_HORIZONTAL_LIST *list,
    GX_EVENT *event);
```

### <a name="description"></a>説明

このサービスは、横方向のリストのイベントを処理します。

### <a name="parameters"></a>パラメーター

- **list** 横方向のリストのウィジェット コントロール ブロック
- **event** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 横方向のリストのイベント処理に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Call generic horizontal list event processing as part of custom event processing function. */

UINT custom_list_event_process(
    GX_HORIZONTAL_LIST *list,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default horizontal
        list event processing */
        status =
        gx_horizontal_list_event_process(list, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>参照

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_page_index_set"></a>gx_horizontal_list_page_index_set


開始ページのインデックスを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_horizontal_list_page_index_set(
    GX_HORIZONTAL_LIST *list,
    INT *index);
```

### <a name="description"></a>説明

このサービスは、横方向のリストの開始インデックスを設定します。

### <a name="parameters"></a>パラメーター

- **list** 横方向のリストのウィジェット コントロール ブロック
- **index** 新しい上位インデックス

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 横方向のリストの開始ページ インデックスの設定に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_VALUE** (0x22) 値が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Sets the starting page index of horizontal list “my_list” as 1. */
status = gx_horizontal_list_page_index_set(&my_list, 1);

/* If status is GX_SUCCESS the starting page index of “my_list” has been set. */
```

### <a name="see-also"></a>参照

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_selected_index_get"></a>gx_horizontal_list_selected_index_get


選択したエントリのインデックスを横方向のリストから取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_horizontal_list_selected_index_get(
    GX_horizobntal_LIST *horizontal_list,
    INT *return_index);
```

### <a name="description"></a>説明

このサービスは、横方向のリストで選択したリスト エントリのインデックスを返します。

### <a name="parameters"></a>パラメーター

- **horizontal_list** 横方向のリストのウィジェット コントロール ブロック
- **return_index** 返されたリスト インデックスの宛先

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 横方向のリスト エントリの取得に成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
INT current_index_entry;

/* Get the list entry at the current index of horizontal list “my_list”. */
status = gx_horizontal_list_selected_index_get(&my_list,
    &current_index_entry);

/* If status is GX_SUCCESS, “current_index_entry” contains the current list selection index. */
```

### <a name="see-also"></a>参照

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_selected_set"></a>gx_horizontal_list_selected_set


選択したエントリを横方向のリストに割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_horizontal_list_selected_set(
    GX_HORIZONATAL_LIST *horizontal_list,
    INT index);
```

### <a name="description"></a>説明

このサービスは、選択したエントリを横方向のリストに割り当てます。 必要に応じて、選択したエントリが表示されるように、横方向のリストがスクロールします。

### <a name="parameters"></a>パラメーター

- **horizontal_list** 横方向のリストのウィジェット コントロール ブロック
- **index** 新しいリスト エントリのインデックスに基づく位置

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 横方向のリスト エントリの設定に成功しました
- **GX_FAILURE** (0x10) インデックスが無効な範囲にありません
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the list entry of “my_list” to the child in line 12. */
status = gx_horizontal_list_selected_set(&my_list, 12);

/* If status is GX_SUCCESS, the list entry of “my_list” has been successfully set to 12. */
```

### <a name="see-also"></a>参照

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_selected_widget_get"></a>gx_horizontal_list_selected_widget_get


選択したエントリを横方向のリストから取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_horizontal_list_selected_widget_get(
    GX_horizobntal_LIST *horizontal_list,
    GX_WIDGET **return_list_entry);
```

### <a name="description"></a>説明

このサービスは、横方向のリストで選択したリスト エントリを返します。 横方向のリストに子ウィジェットよりも多くの行があり、選択したエントリがビューからスクロールされている場合、GX_NULL が返されます。これは、リストの内容がスクロールされると、子ウィジェットが再利用されるためです。 gx_horizontal_list_selected_index_get 関数では、選択された項目がビューからスクロールされた場合でも、その項目のインデックスが確実に返されます。

### <a name="parameters"></a>パラメーター

- **horizontal_list** 横方向のリストのウィジェット コントロール ブロック
- **return_list_entry** 返されるリスト エントリ ウィジェットの宛先

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 横方向のリスト エントリの取得に成功しました
- **GX_FAILURE** (0x10) 選択されたウィジェットが、クライアントの子よりも行数の多いリストを持つリストのビューからスクロールされました。
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Get the list entry at the current index of horizontal list “my_list”. */
status = gx_horizontal_list_selected_widget_get(&my_list, &current_list_entry);

/* If status is GX_SUCCESS, “current_list_entry” contains a pointer to the currently selected widget. */

    
```

### <a name="see-also"></a>参照

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_total_columns_set"></a>gx_horizontal_list_total_columns_set


リストの合計列数を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_horizontal_list_total_columns_set(
    GX_HORIZONTAL_LIST *horizontal_list,
    INT count);
```

### <a name="description"></a>説明

このサービスは、横方向のリストに表示される列の合計数を割り当てます。

### <a name="parameters"></a>パラメーター

- **horizontal_list** 横方向のリストのウィジェット コントロール ブロック
- **count** 表示する列数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 列数が正常に割り当てられました
- **GX_CALLER_ERROR** (0x10) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_VALUE** (0x22) count 値が無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Tell my list to display 20 total columns. */
status = gx_horizontal_list_total_columns_set(&my_list, 20);

/* If status is GX_SUCCESS, the total colums of “my_list” was successfully set to 20. */
```

### <a name="see-also"></a>参照

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set

## <a name="gx_horizontal_scrollbar_create"></a>gx_horizontal_scrollbar_create


水平スクロール バーを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_horizontal_scrollbar_create(
    GX_SCROLLBAR *scrollbar,
    GX_CONST GX_CHAR *name,
    GX_WINDOW *parent,
    GX_SCROLLBAR_APPEARANCE *appearance ULONG style);
```

### <a name="description"></a>説明

このサービスは、水平スクロール バーを作成します。 水平スクロール バーの ID は事前に定義されています (ウィンドウでイベントをキャッチする方法がわかっている必要があるため)。また、サイズは自動になります (親ウィンドウのクライアントの幅に合わせる必要があるため)。 クライアント領域のスクロール バーを許可する場合は、id と size のパラメーターを指定して別の create 関数を追加する必要があります。

### <a name="parameters"></a>パラメーター

- **scrollbar** スクロール バーのウィジェット コントロール ブロック
- **name** スクロール バーの名前
- **parent** 親ウィジェットへのポインター
- **appearance** 外観構造によって、スクロール バーの外観が定義されます。 この値が GX_NULL 場合、gx_system_scroll_appearance_get で定義されている既定のスクロール バーの外観が使用されます。 GX_SCROLLBAR_APPEARANCE 構造の定義については、**付録 I** を参照してください。
- **Style** スクロール バー ウィジェットのスタイル。 **付録 D** には、すべてのウィジェット用に事前に定義されている一般的なスタイルおよびウィジェット固有のスタイルが記載されています。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 水平スクロール バーの作成に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Create horizontal scrollbar “my_scrollbar”. */
status = gx_horizontal_scrollbar_create(&my_scrollbar,
    “my_horizontal_scrollbar”, &my_parent, GX_NULL,
    GX_STYLE_SCROLLBAR_END_BUTTONS);

/* If status is GX_SUCCESS the horizontal scrollbar “my_scrollbar” has been created. */
```

### <a name="see-also"></a>参照

- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_icon_button_create"></a>gx_icon_button_create


アイコン ボタンを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_icon_button_create(
    GX_ICON_BUTTON *button,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    GX_RESOURCE_ID icon_id,
    ULONG style,
    USHORT icon_button_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスは、指定されたアイコン ボタン ウィジェットを作成します。

GX_ICON_BUTTON は GX_BUTTON からの派生であり、すべての gx_button API サービスをサポートします。

### <a name="parameters"></a>パラメーター

- **button** アイコン ボタン コントロール ブロックへのポインター
- **name** アイコン ボタン ウィジェットの論理名
- **parent** 親ウィジェットへのポインター
- **icon_id** アイコンのリソース ID
- **style** アイコンのスタイル。 **付録 D** には、すべてのウィジェット用に事前に定義されている一般的なスタイルおよびウィジェット固有のスタイルが記載されています。
- **icon_button_id** アプリケーションで定義されたアイコン ボタンの ID
- **size** アイコン ボタンの大きさ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) アイコン ボタンの作成に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Create “my_icon_button”. */
status = gx_icon_button_create(&my_icon_button, “my_icon_button”,
    &my_parent,
    MY_ICON_RESOURCE_ID, GX_STYLE_BORDER_RAISED, MY_ICON_BUTTON_ID,
    &size);

/* If status is GX_SUCCESS the icon button “my_icon_button” has been created. */
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_create
- gx_icon_draw
- gx_icon_pixelmap_set
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_radio_button_create
- gx_radio_button_draw gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_icon_button_draw"></a>gx_icon_button_draw


アイコン ボタンを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_icon_button_draw(GX_ICON_BUTTON *button);
```

### <a name="description"></a>説明

このサービスでは、アイコン ボタンを描画します。 通常、この関数は、キャンバスの更新操作の一部として GUIX によって内部的に呼び出されますが、カスタム描画関数を提供し、カスタム描画ベースとして既定のアイコン ボタン描画を呼び出す必要があるアプリケーションにも公開されます。

### <a name="parameters"></a>パラメーター

- **button**: アイコン ボタン コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom icon draw function. */
void MyIconButtonDraw(GX_ICON_BUTTON *button)
{
    /* Do the normal drawing first */
    gx_icon_button_draw(button);

    /* Add custom drawing here */
}
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_create
- gx_icon_draw
- gx_icon_pixelmap_set
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_radio_button_create
- gx_radio_button_draw gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_icon_button_pixelmap_set"></a>gx_icon_button_pixelmap_set


アイコン ボタン ウィジェットにピクセルマップを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_icon_button_pixelmap_set(
    GX_ICON_BUTTON *button,
    GX_RESOURCE_ID icon_id);
```

### <a name="description"></a>説明

このサービスでは、新しいピクセルマップをアイコン ボタン ウィジェットに割り当てます。

### <a name="parameters"></a>パラメーター

- **button**: アイコン ボタン コントロール ブロックへのポインター
- **icon_id**: ピクセルマップのリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) アイコン ボタンのピクセルマップが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set pixelmap for “my_icon_button”. */
status = gx_icon_button_pixelmap_set(&my_icon_button,
    GX_PIXELMAP_ID_ICON);

/* If status is GX_SUCCESS, the pixelmap of the icon button “my_icon_button” has been set. */
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_create
- gx_icon_draw
- gx_icon_pixelmap_set
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_radio_button_create
- gx_radio_button_draw gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_icon_background_draw"></a>gx_icon_background_draw


アイコンの背景を描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_icon_background_draw(GX_ICON *icon);
```

### <a name="description"></a>説明

このサービスでは、指定されたアイコン ウィジェットの背景を描画します。 このサービスは、通常、gx_icon_button_draw 関数によって内部的に呼び出されますが、カスタムの描画関数の作成を支援するためにアプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **icon**: アイコン ウィジェット コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Write a custom icon draw function. */
void MyIconButtonDraw(GX_ICON *icon)
{
    /* Call icon background draw. */
    gx_icon_background_draw(icon);

    /* Add custom drawing here */

    /* Draw child widgets. */
    gx_widget_children_draw(icon);
}
```

### <a name="see-also"></a>参照

- gx_icon_create
- gx_icon_draw
- gx_icon_event_process
- gx_icon_pixelmap_set

## <a name="gx_icon_create"></a>gx_icon_create


[作成] アイコン

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_icon_create(
    GX_ICON *icon, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID pixelmap_id, 
    ULONG style,
    USHORT icon_id, 
    GX_VALUE x, 
    GX_VALUE y);
```

### <a name="description"></a>説明

このサービスでは、指定されたアイコン ウィジェットを作成します。

### <a name="parameters"></a>パラメーター

- **icon**: アイコン コントロール ブロックへのポインター
- **name**: アイコン ウィジェットの論理名
- **parent**: 親ウイジェットへのポインター
- **pixelmap_id**: ピクセルマップのリソース ID
- **style**: アイコンのスタイル
- **icon_id**: アイコンのアプリケーション定義 ID
- **x**: x 座標の開始位置
- **y**: y 座標の開始位置

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) アイコンの作成に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Create “my_icon”. */
status = gx_icon_create(&my_icon, “my_icon”, &my_parent,
    MY_PIXELMAP_RESOURCE_ID, GX_STYLE_BORDER_RAISED, MY_ICON_ID,
    5, 30);

/* If status is GX_SUCCESS the icon “my_icon” has been created. */
```

### <a name="see-also"></a>参照

- gx_icon_button_create
- gx_icon_draw
- gx_icon_pixelmap_set

## <a name="gx_icon_draw"></a>gx_icon_draw


アイコンを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_icon_draw(GX_ICON *icon);
```

### <a name="description"></a>説明

このサービスでは、指定されたアイコン ウィジェットを描画します。 通常、このサービスは、キャンバスの更新操作の一部として GUIX によって内部的に呼び出されますが、カスタム描画関数を提供し、カスタム描画ベースとして既定のアイコン描画を呼び出す必要があるアプリケーションにも公開されます。

### <a name="parameters"></a>パラメーター

- **icon**: アイコン ウィジェット コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom icon drawing function. */

VOID my_icon_draw(GX_MENU *menu)
{
    /* Call default icon draw. */
    gx_icon_draw(menu);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_icon_button_create
- gx_icon_create
- gx_icon_pixelmap_set

## <a name="gx_icon_event_process"></a>gx_icon_event_process

アイコン ウィジェット イベントの処理

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_icon_event_process(
    GX_ICON *icon, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>説明

このサービスでは、GX_ICON ウィジェットに送信されるイベントを処理します。

### <a name="parameters"></a>パラメーター

- **icon**: アイコン ウィジェット コントロール ブロックへのポインター
- **event_ptr**: GX_EVENT 構造体へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) アイコン イベントが正常に処理されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
switch(event_ptr->gx_event_type)
{
case GX_EVENT_SHOW:
    /* Do default handling. */
    status = gx_icon_event_process(icon, event_ptr);

    /* add your own handling here */
    break;
}
```

### <a name="see-also"></a>参照

- gx_icon_button_create
- gx_icon_create
- gx_icon_pixelmap_set

## <a name="gx_icon_pixelmap_set"></a>gx_icon_pixelmap_set


アイコンのピクセルマップを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_icon_pixelmap_set(
    GX_ICON *icon, 
    GX_RESOURCE_ID normal_id,
    GX_RESOURCE_ID selected_id);
```

### <a name="description"></a>説明

このサービスでは、指定されたアイコン ウィジェットのピクセルマップを設定します。

### <a name="parameters"></a>パラメーター

- **icon**: アイコン ウィジェット コントロール ブロックへのポインター
- **normal_id**: 通常状態のリソース ID
- **selected_id**: 選択状態のリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) アイコンのピクセルマップが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set pixelmap for “my_icon”. */
status = gx_icon_pixelmap_set(&my_icon,
    MY_NOT_SELECTED_RESOURCE_ID,
    MY_SELECTED_ID);

/* If status is GX_SUCCESS, the icon “my_icon” has a pixelmap set. */
```

### <a name="see-also"></a>参照

- gx_icon_button_create
- gx_icon_create
- gx_icon_draw

## <a name="gx_image_reader_create"></a>gx_image_reader_create


イメージ リーダー モジュール インスタンスを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_image_reader_create(
    GX_IMAGE_READER *image_reader,
    GX_CONST GX_UBYTE *data, 
    INT data_size,
    GX_UBYTE color_format, 
    GX_UBYTE mode);
```

### <a name="description"></a>説明

この関数では、ランタイムの未加工イメージ リーダーまたはデコーダーを作成します。 現在、未加工イメージの種類として jpeg と png のみがサポートされています。 このサービスでは、GX_SOFTWARE_DECODER_SUPPORT が定義されている必要があります。

### <a name="parameters"></a>パラメーター

- **image_reader**: イメージ リーダー コントロール ブロック
- **data**: 未加工入力データへのポインター。
- **data_size**: 未加工入力データのサイズ。
- **color_format**: 要求された出力の色形式。
- **mode**: 圧縮、ディザー、およびアルファのモード フラグ。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) イメージ　リーダーが正常に作成されました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_VALUE** (0x22) データ サイズが無効です

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
GX_IMAGE_READER my_image_reader;

“color format” could be set to:
    GX_COLOR_FORMAT_32ARGB
    GX_COLOR_FORMAT_24RGB
    GX_COLOR_FORMAT_565RGB
    GX_COLOR_FORMAT_8BIT_PALETTE

/* Create image reader “my_image_reader”. */
status = gx_image_reader_create(&my_image_reader, decoder_data,
    decoder_data_size,
    GX_COLOR_FORMAT_32ARGB,
    GX_IMAGE_READER_MODE_COMPRESS)

/* If status is GX_SUCCESS, “my_image_reader” has been successfully created. */
```

### <a name="see-also"></a>参照

- gx_image_reader_start
- gx_image_reader_palette_set

## <a name="gx_image_reader_palette_set"></a>gx_image_reader_palette_set


イメージ リーダー パレットを定義します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_image_reader_palette_set(
    GX_IMAGE_READER *image_reader,
    GX_COLOR *pal,
    UINT palsize);
```

### <a name="description"></a>説明

このサービスでは、イメージ リーダー コントロール ブロックのパレットを設定します。 このサービスでは、GX_SOFTWARE_DECODER_SUPPORT が定義されている必要があります。

### <a name="parameters"></a>パラメーター

- **image_reader**: イメージ リーダー コントロール ブロック
- **pal**: パレットへのポインター
- **palsize**: パレットのサイズ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) イメージ　リーダー パレットの設定が成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_VALUE** (0x22) パレットのサイズが無効です

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Set “my_palette” as the palette of “my_image_reader”. */
status = gx_image_reader_palette_set(&my_image_reader, my_palette,
    my_palette_size);

/* If status is GX_SUCCESS the palette of “my_image_reader” has been set to “my_palette”. */
```

### <a name="see-also"></a>参照

- gx_image_reader_create
- gx_image_reader_start

## <a name="gx_image_reader_start"></a>gx_image_reader_start

圧縮解除と変換のプロセスを開始します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_image_reader_start(
    GX_IMAGE_READER *image_reader, 
    GX_PIXELMAP *outmap);
```

### <a name="description"></a>説明

このサービスでは、未加工のイメージを指定された色形式にデコードします。 現在、未加工のイメージの種類として jpeg と png のみがサポートされています。 これには、GX_SOFTWARE_DECODER_SUPPORT が定義されている必要があります。

### <a name="parameters"></a>パラメーター

- **image_reader**: イメージ リーダー コントロール ブロック
- **pixelmap**: 出力ピクセルマップ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) イメージのデコードに成功しました
- **GX_SYSTEM_MEMORY_ERROR** (0x30) メモリ アロケーターが定義されていないか、メモリの割り当てに失敗しました
- **GX_NOT_SUPPORTED** (0X28) 入力のイメージの種類または出力の色形式がサポートされていません
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
GX_IMAGE_READER my_image_reader;
GX_PIXELMAP output_map;

/* Create my_image_reader here. */

/* Decoding a raw image according to the settings of “my_image_reader”. */
status = gx_image_reader_start(&my_image_reader, output_map)

/* If status is GX_SUCCESS “output_map” have been loaded with the requested pixelmap. */
```

### <a name="see-also"></a>参照

- gx_image_reader_create
- gx_image_reader_palette_set

## <a name="gx_line_chart_axis_draw"></a>gx_line_chart_axis_draw


折れ線グラフの x、y 軸を描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_line_chart_axis_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>説明

このサービスでは、折れ線グラフの x、y 軸を描画します。 軸の色と線の幅のパラメーターは、折れ線グラフ情報の構造体から取得されます。

このサービスは、通常、gx_line_chart_draw 関数によって内部的に呼び出されますが、カスタムの描画関数の作成を支援するためにアプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **chart**: 折れ線グラフ コントロール ブロック。

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom chart drawing function. */

VOID my_chart_draw(GX_LINE_CHART *chart)
{
    /* Call default window draw. */
    gx_window_draw((GX_WINDOW *)chart);

    /* Draw the line chart axis. */
    gx_line_chart_axis_draw(&chart->gx_line_chart_info);

    /* Draw the data line */
    gx_line_chart_data_draw(&chart->gx_line_chart_info);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_create"></a>gx_line_chart_create


GX_LINE_CHART ウィジェットを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_line_chart_create(
    GX_LINE_CHART *chart,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_LINE_CHART_INFO *info,
    ULONG style,
    USHORT chart_id, GX_RECTANGLE *size)
```

### <a name="description"></a>説明

このサービスでは、折れ線グラフ ウィンドウを作成します。 グラフ描画パラメーターとグラフ データは、GX_LINE_CHART_INFO 構造体で渡されます。

GX_LINE_CHART は GX_WINDOW に基づいており、すべての GX_WINDOW API がサポートされています。

### <a name="parameters"></a>パラメーター

- **chart**: GX_LINE_CHART コントロール ブロックへのポインター。
- **name**: 省略可能な折れ線グラフ名
- **parent**: 親ウィジェット、または GX_NULL
- **info**: 折れ線グラフ描画パラメーターを定義する構造体。 **付録 I** には GX_LINE_CHART_INFO 構造体の定義が含まれています。
- **style**: ウィジェットのスタイル フラグ
- **chart_id**: グラフの論理 ID 値
- **size**: グラフ ウィンドウの境界ボックス

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 折れ線グラフの作成に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットは既に作成されています

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Create a line chart */
GX_LINE_CHART chart;
GX_RECTANGLE chart_size;
GX_LINE_CHART_INFO gx_chart_info;
GX_WINDOW_ROOT *root_window;

chart_size = root_window->gx_widget_size;

/* Initialize params for the GUIX base chart. */
gx_chart_info.gx_line_chart_min_val = DATA_MIN_VAL;
gx_chart_info.gx_line_chart_max_val = DATA_MAX_VAL;
gx_chart_info.gx_line_chart_max_data_count = MAX_DATA_COUNT;
gx_chart_info.gx_line_chart_active_data_count = 0;
gx_chart_info.gx_line_chart_axis_line_width = AXIS_LINE_WIDTH;
gx_chart_info.gx_line_chart_data_line_width = DATA_LINE_WIDTH;
gx_chart_info.gx_line_chart_data = chart_data;
gx_chart_info.gx_line_chart_line_color = GX_COLOR_ID_DATA_LINE;
gx_chart_info.gx_line_chart_axis_color = GX_COLOR_ID_AXIS_LINE;

/* Leave room for labels on bottom and right. */
gx_chart_info.gx_line_chart_left_margin = 0;
gx_chart_info.gx_line_chart_top_margin = 0;
gx_chart_info.gx_line_chart_right_margin = 80;
gx_chart_info.gx_line_chart_bottom_margin = 32;

status = gx_line_chart_create(&chart, “Line Chart”, root_window,
    &gx_chart_info, GX_STYLE_NONE, &chart_size);

/* If status is GX_SUCCESS, the “chart” has been successfully created. */
```

### <a name="see-also"></a>参照

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_data_draw"></a>gx_line_chart_data_draw


折れ線グラフのデータ線を描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_line_chart_data_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>説明

このサービスでは、折れ線グラフのデータ線を描画します。 線の色と線の幅のパラメーターは、折れ線グラフ情報の構造体から取得されます。

このサービスは、通常、gx_line_chart_draw 関数によって内部的に呼び出されますが、カスタムの描画関数の作成を支援するためにアプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **chart**: 折れ線グラフ コントロール ブロック

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom chart drawing function. */

VOID my_chart_draw(GX_LINE_CHART *chart)
{
    /* Call default window draw. */
    gx_window_draw((GX_WINDOW *)chart);

    /* Draw the line chart axis. */
    gx_line_chart_axis_draw(chart);

    /* Draw the data line. */
    gx_line_chart_data_draw(chart);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_line_chart_create
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_draw"></a>gx_line_chart_draw


折れ線グラフを描画します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_line_chart_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>説明

これは、グラフの軸とデータ線を描画する既定の折れ線グラフ描画関数です。 アプリケーションには通常、基本の折れ線グラフ ウィジェットによって描画されたグラフ軸やデータ線に、目盛り、スケール、またはその他の情報などを追加するための既定の描画を置き換えるカスタム描画関数が用意されています。

### <a name="parameters"></a>パラメーター

- **chart**: 折れ線グラフ コントロール ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom chart drawing function. */

VOID my_chart_draw(GX_LINE_CHART *chart)
{
    /* Call default line chart draw. */
    gx_line_chart_draw(chart);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_line_chart_create
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_update"></a>gx_line_chart_update


折れ線グラフのデータ線を更新します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_line_chart_update(
    GX_LINE_CHART *chart, 
    INT *data,
    INT data_count)
```

### <a name="description"></a>説明

このサービスでは、折れ線グラフ ウィンドウによってプロットされたデータ配列を更新し、強制的にウィンドウを再描画します。

### <a name="parameters"></a>パラメーター

- **chart**: 折れ線グラフ コントロール ブロック
- **data**: プロットされるデータ配列
- **data_count**: データ配列のサイズ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) テキスト ボタンの作成に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
INT chart_data[100];
GX_LINE_CHART chart;

/* Update the data array associated with “chart”. */
status = gx_line_chart_update(&chart, chart_data, 100);

/* If status is GX_SUCCESS, the line chart data has been updated. */
```

### <a name="see-also"></a>参照

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_y_scale_calculate"></a>gx_line_chart_y_scale_calculate


y 軸の固定小数点スケーリング値を計算します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_line_chart_y_scale_calculate(
    GX_LINE_CHART *chart,
    INT *return_val);
```

### <a name="description"></a>説明

このサービスでは、グラフの Y 軸にデータ値をプロットするために使用される固定小数点スケーリング値を計算します。 このスケーリング値を計算するために、chart_info パラメーターとグラフの境界ボックスが使用されます。

### <a name="parameters"></a>パラメーター

- **chart**: 折れ線グラフ コントロール ブロック
- **return_val**: 固定小数点の戻り値を保持する値のアドレス。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) y スケール値の計算に成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_LINE_CHART chart;
INT y_scale;

/* Caluclate y scale value of “chart”. */
status = gx_line_chart_y_scale_calculate(&chart, &y_scale);

/* If status is GX_SUCCESS, y scale value of “chart” has been calculated. */
```

### <a name="see-also"></a>参照

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_update

## <a name="gx_menu_create"></a>gx_menu_create


メニューを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_menu_create(
    GX_MENU *menu,GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    GX_RESOURCE_ID text_id,
    GX_RESOURCE_ID fill_id, 
    ULONG style, 
    USHORT menu_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスでは、指定されたとおりにメニューを作成し、そのメニューを指定された親ウィジェットに関連付けます。 これは、すべての種類のウィジェットを子メニュー項目として受け入れます。 ウィジェットを子メニュー項目として挿入するには、**gx_menu_insert** を呼び出します。

GX_MENU は GX_PIXELMAP_PROMPT から派生しており、すべての gx_pixelmap_prompt API サービスがサポートされます。

### <a name="parameters"></a>パラメーター

- **menu**: メニュー コントロール ブロックへのポインター
- **name**: メニューの名前
- **parent**: 親ウィジェットへのポインター
- **text_id**: テキストのリソース ID
- **fill_id**: 塗りつぶしのリソース ID
- **style**: ウィジェットのスタイル。 **付録 D** には、ウィジェット固有のスタイルだけでなく、すべてのウィジェット用に事前に定義されている一般的なスタイルが記載されています。
- **menu_id**: メニューのアプリケーション定義 ID
- **size**: メニューのサイズ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) メニューの作成に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_MENU my_menu;

/* Create “my_menu”. */
status = gx_menu_create(&my_menu, “my_menu”, parent, MY_TEXT_ID,
    MY_FILL_ID, GX_STYLE_ENABLED, MY_MENU_ID,
    &size);

/* If status is GX_SUCCESS, the menu was successfully created. */
```

### <a name="see-also"></a>参照

- gx_accordion_meu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_draw"></a>gx_menu_draw


メニューを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_menu_draw(GX_MENU *menu);
```

### <a name="description"></a>説明

このサービスでは、指定されたメニューを描画します。 通常、この関数は GUIX キャンバスの更新メカニズムによって内部的に呼び出されますが、カスタム メニュー ウイジェットのカスタム描画関数の実装を支援するためにアプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **menu**: メニュー コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom menu drawing function. */

VOID my_menu_draw(GX_MENU *menu)
{
    /* Call default menu draw. */
    gx_menu_draw(menu);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_event_process"></a>gx_menu_event_process

メニュー イベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_menu_event_process(GX_MENU *menu, GX_EVENT *event_ptr);
```

### <a name="description"></a>説明

このサービスでは、指定されたメニューのイベントを処理します。 このサービスは、カスタム メニューのイベント処理関数によって既定のイベント ハンドラーとして呼び出される必要があります。

### <a name="parameters"></a>パラメーター

- **menu**: メニュー コントロール ブロックへのポインター
- **event_ptr**: 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) メニューのイベント処理が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x23) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Call generic menu event processing as part of custom event processing function. */

UINT custom_menu_event_process(GX_MENU *menu, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */

        /* Call default event process if this is a system event such as GX_EVENT_SHOW. */
        status = gx_menu_event_process(menu, event);
        break;

    default:
        /* Pass all other events to the default menu
           event processing */
        status = gx_menu_event_process(menu, event);
        break;
    }
    return status;
}

```

### <a name="see-also"></a>参照

- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_insert"></a>gx_menu_insert


新しい項目を挿入します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_menu_insert(
    GX_MENU *menu, 
    GX_WIDGET *insert);
```

### <a name="description"></a>説明

このサービスでは、メニューに新しい項目を挿入します。

### <a name="parameters"></a>パラメーター

- **menu**: メニュー コントロール ブロックへのポインター
- **widget**: 挿入するウィジェットへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) メニューに新しい項目を正常に挿入しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Insert new item “my_widget” to the menu “my_menu”. */
status = gx_menu_insert(&my_menu, &my_widget);

/* If status is GX_SUCCESS the new item “my_widget” has been inserted to the menu “my_menu”. */
```

### <a name="see-also"></a>参照

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_remove"></a>gx_menu_remove


項目を削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_menu_remvoe(
    GX_MENU *menu, 
    GX_WIDGET *widget);
```

### <a name="description"></a>説明

このサービスでは、メニューから項目を削除します。

### <a name="parameters"></a>パラメーター

- **menu**: メニュー コントロール ブロックへのポインター
- **widget**: 削除するウィジェットへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) メニュー項目を正常に削除しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Remove item “my_widget” from menu “my_menu” */
status = gx_menu_remove(&my_menu, &my_widget);

/* If status is GX_SUCCESS the item “my_widget” has been removed from menu “my_menu”. */
```

### <a name="see-also"></a>参照

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_text_draw"></a>gx_menu_text_draw


メニュー テキストを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_menu_text_draw(GX_MENU *menu);
```

### <a name="description"></a>説明

このサービスでは、メニューのテキストを描画します。 通常、この関数は GUIX キャンバスの更新メカニズムによって内部的に呼び出されますが、カスタム メニュー ウイジェットのカスタム描画関数の実装を支援するためにアプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **menu**: メニュー コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom menu drawing function. */

VOID my_menu_draw(GX_MENU *menu)
{
    /* Call default menu background draw. */
    gx_pixelmap_prompt_background_draw(
                            (GX_PIXELMAP_PROMPT *)menu);

    /* Draw menu text. */
    gx_menu_text_draw(menu);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_offset_set

## <a name="gx_menu_text_offset_set"></a>gx_menu_text_offset_set


メニュー テキスト描画オフセットを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_menu_text_offset_set(
    GX_MENU *menu, 
    GX_VALUE x_offset,
    GX_VALUE y_offset);
```

### <a name="description"></a>説明

このサービスでは、メニュー テキストに対して x、y 表示オフセットを設定します。

### <a name="parameters"></a>パラメーター

- **menu**: メニュー コントロール ブロックへのポインター
- **x_offset**: オフセットの X 座標
- **y_offset**: オフセットの Y 座標

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) メニュー テキスト描画オフセットが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set text draw offset of menu “my_menu” to (20, 10). */
status = gx_menu_text_offset_set(&my_menu, 20, 10);

/* If status is GX_SUCCESS the text draw offset of menu “my_menu” has been set to (20, 10). */
```

### <a name="see-also"></a>参照

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw

## <a name="gx_multi_line_text_button_create"></a>gx_multi_line_text_button_create


複数行テキスト ボタンを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_button_create(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    ULONG style,
    USHORT text_button_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスでは、複数行テキスト ボタン ウィジェットを作成します。 複数行テキスト ボタンでは、ボタンのテキストが 1 - n 行に表示されます。 最大行数は、定数 GX_MULTI_LINE_TEXT_BUTTON_MAX_LINES によって定義されます。既定値は 4 です。 改行は、複数行テキスト ボタンに割り当てられたテキスト文字列内で復帰や、復帰と改行の組み合わせによって設定されます。

GX_MULTI_LINE_TEXT_BUTTON は GX_TEXT_BUTTON から派生しており、すべての gx_text_button API サービスがサポートされます。

### <a name="parameters"></a>パラメーター

- **text_button**: テキスト ボタン コントロール ブロックへのポインター
- **name**: テキスト ボタンの論理名
- **parent**: ボタンの親ウィジェットへのポインター
- **text_id**: テキストのリソース ID
- **style**: テキスト ボタンのスタイル。 **付録 D** には、ウィジェット固有のスタイルに加えて、すべてのウィジェット用に事前に定義された一般的なスタイルも含まれています。
- **text_button_id**: テキスト ボタンのアプリケーション定義 ID
- **size**: ボタンのサイズ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行テキスト ボタンの作成に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Create multi-line text button “my_text_button”. */
status = gx_multi_line_text_button_create(&my_text_button, "my text button",
    &my_parent_window, MY_TEXT_RESOURCE_ID,
    GX_STYLE_BUTTON_TOGGLE, MY_TEXT_BUTTON_ID,
    &size);

/* If status is GX_SUCCESS, the multi-line text button “my_text_button” was created. */
```

### <a name="see-also"></a>参照

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_draw"></a>gx_multi_line_text_button_draw


複数行テキスト ボタンを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_multi_line_text_button_draw(GX_MULTI_LINE_TEXT_BUTTON *button);
```

### <a name="description"></a>説明

このサービスでは、複数行テキスト ボタンを描画します。 通常、この関数は、キャンバスの更新操作の一部として GUIX によって内部的に呼び出されますが、カスタム描画関数を提供し、カスタム描画ベースとして既定の複数行テキスト ボタン描画を呼び出す必要があるアプリケーションにも公開されます。

### <a name="parameters"></a>パラメーター

- **button**: テキスト ボタン コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Draw the text button “my_text_button”. */
void MyButtonDraw(GX_MULTI_LINE_TEXT_BUTTON *button)
{
    /* Do the normal drawing first */
    gx_multi_line_text_button_draw(&my_text_button);

    /* Add custom drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_event_process"></a>gx_multi_line_text_button_event_process


複数行テキスト ボタンに対する既定のイベント処理

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_button_event_process(
    GX_MULTI_LINE_TEXT_BUTTON *button,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>説明

このサービスは、複数行テキスト ボタン ウィジェットの既定のイベント処理関数です。 この関数には、テキスト ボタン ウィジェットに対してカスタム イベント処理を提供するアプリケーションからアクセスできるようになります。

### <a name="parameters"></a>パラメーター

- **button**: テキスト ボタン コントロール ブロックへのポインター
- **event_ptr**: 処理されるイベント

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) イベントが正常に処理されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
UINT MyEventHandler(GX_MULTI_LINE_TEXT_BUTTON *button,
    GX_EVENT *event_ptr)
{
    switch(event->gx_event_type)
    {
    case GX_EVENT_SHOW:
        gx_multi_line_text_button_event_process(button, event_ptr);
        /* add custom actions here */
        break;
    default:
        gx_multi_line_text_button_event_process(button, event_ptr);
        break;
    }
    return GX_SUCCESS;
}
```

### <a name="see-also"></a>参照

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_text_draw"></a>gx_multi_line_text_button_text_draw


描画サポート関数

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_multi_line_text_button_text_draw(GX_MULTI_LINE_TEXT_BUTTON *text_button);
```

### <a name="description"></a>説明

このサポート関数では、複数行テキスト ボタンのテキスト部分を描画します。 この関数は gx_multi_line_text_button_draw() によって内部的に呼び出され、カスタムの複数行テキスト ボタンの描画関数を定義するアプリケーションの利便性向上のために、独立した API として提供されます。 ボタンの背景描画をカスタマイズする必要があるアプリケーションは、カスタム描画関数を提供し、背景上にボタン テキストを描画するカスタム描画の一部として multi_line_text_button_text_draw サービスを呼び出すことができます。

### <a name="parameters"></a>パラメーター

- **text_button**: テキスト ボタン コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Define a custom drawing function */
VOID my_button_draw(GX_MULTI_LINE_TEXT_BUTTON *button)
{
    /* insert code here to draw button background */

    /* call support function to do text drawing */
    gx_multi_line_text_button_text_draw();

    /* draw child widgets */
    gx_widget_children_draw((GX_WIDGET *) button);
}
```

### <a name="see-also"></a>参照

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set


## <a name="gx_multi_line_text_button_text_id_set"></a>gx_multi_line_text_button_text_id_set


テキスト リソース ID をテキスト ボタンに設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_button_text_id_set(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    RESOURCE_ID string_id)
```

### <a name="description"></a>説明

このサービスでは、指定された文字列リソース ID をテキスト ボタンに設定します。 文字列には、ボタン領域内の複数行にテキストを表示する改行文字を含めることができます。

### <a name="parameters"></a>パラメーター

- **text_button**: テキスト ボタン コントロール ブロックへのポインター
- **string_id**: 文字列のリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 文字列リソース ID をテキスト ボタンに正常に設定しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the string ID ”MY_STRING_ID” to the text button “my_text_button”. */
status = gx_multi_line_text_button_text_id_set(
    &my_text_button, MY_STRING_ID);

/* If status is GX_SUCCESS, the string ID MY_STRING_ID was set to “my_text_button”. */
```

### <a name="see-also"></a>参照

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_text_set"></a>gx_multi_line_text_button_text_set


テキストをテキスト ボタンに割り当てます (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_mult_line_text_button_text_set(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    GX_CHAR *text);
```

### <a name="description"></a>説明

このサービスは非推奨となり、gx_multi_line_text_button_text_set_ext() に置き換えられます。

このサービスでは、指定された文字列をテキスト ボタンに割り当てます。 text_button ウィジェットがスタイル GX_STYLE_TEXT_COPY で作成された場合は、ウィジェットによって、割り当てられたテキスト文字列のプライベート コピーが作成されます。そのため、このサービスを要求する前に gx_system_memmory_allocate_set API が 1 回呼び出される必要があります。 GX_STYLE_TEXT_COPY がアクティブでない場合、ウィジェットでは受信文字列のプライベート コピーが作成されないため、文字列は静的またはグローバルに割り当てられる必要があります (つまり、自動または一時変数であってはなりません)。

### <a name="parameters"></a>パラメーター

- **text_button**: テキスト ボタン コントロール ブロックへのポインター
- **text**: NULL で終わる文字列へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ボタンにテキストが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_MEMORY_ERROR** (0X30) メモリ アロケーターが定義されていません
- **GX_INVALID_STRING_LENGTH** (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
static GX_CHAR text[] = “myrstring”;

/* Set text to the text button “my_text_button”. */
status = gx_multi_line_text_button_text_set(&my_text_button, text);

/* If status is GX_SUCCESS, the text of “my_text_button” was set. */
```

### <a name="see-also"></a>参照

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_text_set_ext"></a>gx_multi_line_text_button_text_set_ext


テキスト ボタンにテキストを割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_mult_line_text_button_text_set_ext(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    GX_STRING *string)
```

### <a name="description"></a>説明

このサービスでは、指定された文字列をテキスト ボタンに割り当てます。 text_button ウィジェットがスタイル GX_STYLE_TEXT_COPY で作成された場合は、ウィジェットによって、割り当てられたテキスト文字列のプライベート コピーが作成されます。そのため、このサービスを要求する前に gx_system_memmory_allocate_set API が 1 回呼び出される必要があります。 GX_STYLE_TEXT_COPY がアクティブでない場合、ウィジェットでは受信文字列のプライベート コピーが作成されないため、文字列は静的またはグローバルに割り当てられる必要があります (つまり、自動または一時変数であってはなりません)。

### <a name="parameters"></a>パラメーター

- **text_button**: テキスト ボタン コントロール ブロックへのポインター
- **string**: GX_STRING 変数へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ボタンにテキストが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_MEMORY_ERROR** (0X30) メモリ アロケーターが定義されていません
- **GX_INVALID_STRING_LENGTH** (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
static GX_CHAR text[] = “myrstring”;
GX_STRING string;

string.gx_string_ptr = text;
string.gx_string_length = strlen(text);

/* Set text to the text button “my_text_button”. */
status = gx_multi_line_text_button_text_set_ext(&my_text_button, string);

/* If status is GX_SUCCESS, the text of “my_text_button” was set. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_input_backspace"></a>gx_multi_line_text_input_backspace


複数行テキスト入力のカーソル位置の前にある文字を削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_backspace(
    GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>説明

このサービスでは、複数行テキスト入力のカーソル位置の前にある文字を削除します。 このサービスは、Backspace キーを押すイベントを受信したときに内部的に呼び出されますが、アプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input** 複数行テキスト入力ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行テキスト入力の Backspace に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_FAILURE** (0X10) 無効なフォント

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Delete a character before the cursor of “my_text_input”. */
status = gx_multi_line_text_input_backspace(&my_text_input);

/* If status is GX_SUCCESS the character before the cursor has been deleted. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_buffer_clear"></a>gx_multi_line_text_input_buffer_clear


テキスト入力バッファーからすべての文字を削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_buffer_clear(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>説明

このサービスは、テキスト入力バッファーからすべての文字を削除します。

### <a name="parameters"></a>パラメーター

- **text_input** 複数行テキスト入力ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行テキスト入力バッファーのクリアに成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* clear input buffer of “my_text_input”. */
status = gx_multi_line_text_input_clear(&my_text_input);

/* If status is GX_SUCCESS the text input widget has emptied its input buffer. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_buffer_get"></a>gx_multi_line_text_input_buffer_get


テキスト入力ウィジェットのバッファー情報を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_buffer_get(
    GX_MULTI_LINE_TEXT_INPUT *text_input, 
    GX_CHAR **buffer_address,
    UINT *content_size, 
    UINT *buffer_size);
```

### <a name="description"></a>説明

このサービスでは、複数行テキスト入力ウィジェットのバッファー情報を取得します。

### <a name="parameters"></a>パラメーター

- **text_input**: 複数行テキスト入力ウィジェット コントロール ブロック
- **buffer_address**: 入力バッファーのアドレス
- **content_size** 入力データのバイト数
- **buffer_size** 入力バッファーのサイズ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行テキストの取得に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_CHAR *buffer_address;
UINT context_size;
UINT buffer_size;

/* Retrieves buffer information of “my_text_input” widget. */
status = gx_multi_line_text_input_buffer_get(&my_text_input,
    &buffer_address, &string_size,
    &buffer_size);

/* If status is GX_SUCCESS the value of buffer_address, string_size and buffer_size has been retrieved. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_char_insert"></a>gx_multi_line_text_input_char_insert


複数行テキスト入力の現在のカーソル位置に文字列を挿入します (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_char_insert(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_UBYTE *insert_str,
    UINT insert_size);
```

### <a name="description"></a>説明

この API は非推奨となり、gx_multi_line_text_input_char_insert_ext () に置き換えられました。

このサービスでは、複数行テキスト入力文字列バッファーの現在の入力位置に文字列を挿入します。 このサービスは、特定のキーを押すイベントを受信したときに内部的に呼び出されますが、アプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input**: 複数行テキスト入力ウィジェット コントロール ブロック
- **insert_str**: 挿入される UTF-8 形式の文字列
- **insert_size**: 挿入されるバイト数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 文字列を正常に挿入しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE**: (0x22) 文字列のサイズが無効です
- **GX_FAILURE** (0x10) フォントが無効であるか、バッファー サイズが不足しています

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Insert characters at current cursor position. */
GX_CHAR insert_text[10] = “insert”;
status = gx_multi_line_text_input_char_insert(&my_text_input,
    insert_text,
    GX_STRLEN(insert_text));

/* If status is GX_SUCCESS the multi line text input widget has successfully insert the string. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_char_insert_ext

## <a name="gx_multi_line_text_input_char_insert_ext"></a>gx_multi_line_text_input_char_insert_ext


複数行テキスト入力の現在のカーソル位置に文字列を挿入します (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_char_insert_ext(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>説明

このサービスでは、複数行テキスト入力文字列バッファーの現在の入力位置に文字列を挿入します。 このサービスは、特定のキーを押すイベントを受信したときに内部的に呼び出されますが、アプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input**: 複数行テキスト入力ウィジェット コントロール ブロック
- **string**: 挿入される UTF-8 でエンコードされた文字列

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 文字列を正常に挿入しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE**: (0x22) 文字列のサイズが無効です
- **GX_FAILURE** (0x10) フォントが無効であるか、バッファー サイズが不足しています
- **GX_INVALID_STRING_LENGTH** (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Insert characters at current cursor position. */
GX_CHAR insert_text[10] = “insert”;
GX_STRING string;

string.gx_string_ptr = insert_text;
string.gx_string_length = strlen(insert_text);

status = gx_multi_line_text_input_char_insert_ext(&my_text_input, &string);

/* If status is GX_SUCCESS the multi line text input widget has successfully inserted the string. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_create"></a>gx_multi_line_text_input_create


複数行テキスト入力を作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_create(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *name, GX_WINDOW *parent,
    GX_CHAR *input_buffer, UINT buffer_size,
    ULONG style, USHORT text_input_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスでは、複数行テキスト入力ウィジェットを作成します。

GX_MULTI_LINE_TEXT_INPUT は GX_MULTI_LINE_TEXT_VIEW から派生しており、すべての gx_multi_line_text_view サービスがサポートされます。

### <a name="parameters"></a>パラメーター

- **text_input**: 複数行テキスト入力ウィジェット コントロール ブロック
- **name**: テキスト入力ウィジェットの名前
- **parent**: 親ウィジェットへのポインター
- **input_buffer**: テキスト入力バッファーへのポインター
- **buffer_size**: テキスト入力バッファーのサイズ (バイト単位)
- **style**: テキスト入力ウィジェットのスタイル。 **付録 D** には、ウィジェット固有のスタイルに加えて、すべてのウィジェット用に事前に定義された一般的なスタイルも含まれています。
- **text_input_id**: テキスト入力のアプリケーション定義 ID
- **size**: テキスト入力ウィジェットのディメンション

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行テキスト入力の作成が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_WIDGET** (0x12) 親ウィジェットが無効です
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_MULTI_LINE_TEXT_INPUT my_text_input;
GX_CHAR my_buffer[100];
GX_RECTANGLE size;

/* Define widget size. */
gx_utility_rectangle_define(&size, 10, 10, 100, 200);

/* Create multi-line text input widget “my_text_input”. */
status = gx_multi_line_text_input_create(&my_text_input,
    “my_text_input”, &my_parent,
    my_buffer, 100, GX_STYLE_BORDER_RAISED,
    MY_TEXT_INPUT_ID, &size);

/* If status is GX_SUCCESS, the text input “my_text_input” has been created. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_cursor_pos_get"></a>gx_multi_line_text_input_cursor_pos_get


複数行テキスト入力のカーソル位置を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_cursor_pos_get(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_POINT cursor_pos);
```

### <a name="description"></a>説明

このサービスでは、複数行テキスト入力のカーソル位置を取得します。

### <a name="parameters"></a>パラメーター

- **text_input**: 複数行テキスト入力ウィジェット コントロール ブロック
- **cursor_pos**: 取得したカーソル位置

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00)カーソル位置の取得に成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Retrieve the cursor position of “my_text_input”. */
GX_POINT cursor_pos;
status = gx_multi_line_text_input_cursor_pos_get(&my_text_input,
    &cursor_pos);

/* If status is GX_SUCCESS the cursor position has been retrieved. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_delete"></a>gx_multi_line_text_input_delete


複数行テキスト入力のカーソル位置にある文字を削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_delete(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>説明

このサービスでは、複数行テキスト入力のカーソル位置の後にある文字を削除します。 このサービスは、Delete キーを押すイベントを受信したときに内部的に呼び出されますが、アプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input** 複数行テキスト入力ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) カーソルの後の文字を正常に削除しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_FAILURE** (0X10) フォントが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Delete the character after the cursor of “my_text_input”. */
status = gx_multi_line_text_input_delete(&my_text_input);

/* If status is GX_SUCCESS the character after the cursor has been deleted. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_down_arrow"></a>gx_multi_line_text_input_down_arrow


複数行テキスト入力のカーソルを次の行に移動します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_down_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>説明

このサービスでは、複数行テキスト入力ウィジェットのカーソルを次の行に配置します。 このサービスは、下矢印キーを押すイベントを受信したときに内部的に呼び出されますが、アプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input** 複数行テキスト入力ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) テキスト入力カーソルを次の行に正常に移動しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_FAILURE** (0x10) フォントまたは行の高さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Move input cursor to the next line. */
status = gx_multi_line_text_input_down_arrow(&my_text_input);

/* If status is GX_SUCCESS, text text input cursor has been moved to the next line. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_end"></a>gx_multi_line_text_input_end


複数行テキスト入力のカーソルを現在の行の末尾に移動します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_end(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>説明

このサービスでは、複数行テキスト入力ウィジェットのカーソルを現在の文字列行の末尾に配置します。 このサービスは、End キーを押すイベントを受信したときに内部的に呼び出されますが、アプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input** 複数行テキスト入力ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) テキスト入力カーソルを現在の行の末尾に正常に移動しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Move input cursor to the end of current line. */
status = gx_multi_line_text_input_end(&my_text_input);

/* If status is GX_SUCCESS, the multi line text input cursor has been moved to the end of the current line. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_event_process"></a>gx_multi_line_text_input_event_process


複数行テキスト入力の既定のイベント処理

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_event_process(
    GX_MULTI_LINE_TEXT_INPUT *input,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>説明

このサービスは、複数行テキスト入力ウィジェットの既定のイベント処理関数です。 この関数は、複数行テキスト入力ウィジェットに対してカスタム イベント処理を提供するアプリケーションからアクセスできるようになります。

### <a name="parameters"></a>パラメーター

- **button**: 複数行テキスト入力コントロール ブロックへのポインター
- **event_ptr**: 処理されるイベント

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) イベントが正常に処理されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) 親ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
UINT MyEventHandler(GX_MULTI_LINE_TEXT_INPUT *input,
    GX_EVENT *event_ptr)
{
    switch(event->gx_event_type)
    {
    case xyz:
        /* insert custom event handling here */
        break;
    default:
        /* pass all other events to the generic multi line text
            input event processing */
        gx_multi_line_text_input_event_process(input, event_ptr);
        break;
    }
    return GX_SUCCESS;
}
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_fill_color_set"></a>gx_multi_line_text_input_fill_color_set


複数行テキスト入力の背景色を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_fill_color_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_fill_color_id,
    GX_RESOURCE_ID selected_fill_color_id,
    GX_RESOURCE_ID disabled_fill_color_id,
    GX_RESOURCE_ID readonly_fill_color_id);
```

### <a name="description"></a>説明

このサービスにより、複数行テキスト入力ウィジェットの塗りつぶしの色が割り当てられます。

### <a name="parameters"></a>パラメーター

- **text_input** 複数行テキスト入力ウィジェット コントロール ブロック
- **normal_fill_color_id** 通常の状態で使用される通常の塗りつぶしの色のリソース ID
- **selected_fill_color_id** ウィジェットがフォーカスを得たときに使用される、選択した塗りつぶしの色のリソース ID
- **disabled_fill_color_id** GX_STYLE_ENABLED がアクティブではないときに使用される、無効な塗りつぶしの色のリソース ID
- **readonly_fill_color_id** GX_STYLE_ENABLED と GX_STYLE_INPUT_READONLY の両方がアクティブな場合に使用される、読み取り専用の塗りつぶしの色のリソース ID。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行テキスト入力の色が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set fill colors for the multi-line text input widget “my_text_input”. */

status = gx_multi_line_text_input_fill_color_set(&my_text_input,
    GX_COLOR_ID_NORMAL_FILL,
    GX_COLOR_ID_SELECTED_FILL,
    GX_COLOR_ID_DISABLED_FILL,
    GX_COLOR_ID_READONLY_FILL);

/* If status is GX_SUCCESS, the fill color of “my_text_input” has been successfully set. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_home"></a>gx_multi_line_text_input_home


テキスト入力のカーソルを現在の行の先頭に移動します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_home(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>説明

このサービスにより、テキスト入力のカーソルの位置が現在の行の先頭に移動されます。 このサービスは、Home キーを押すイベントを受信したときに内部的に呼び出されますが、アプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input** 複数行テキスト入力ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 現在の行の先頭にカーソルが正常に移動されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Move cursor to the start of the current line. */
status = gx_multi_line_text_input_home(&my_text_input);

/* If status is GX_SUCCESS the cursor has been moved to the start of the current line. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_left_arrow"></a>gx_multi_line_text_input_left_arrow


複数行テキスト入力のカーソルを 1 文字分だけ左に移動します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_left_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>説明

このサービスにより、複数行テキスト入力のカーソルが 1 文字分だけ左に移動されます。 このサービスは、左矢印キーを押すイベントを受信したときに内部的に呼び出されますが、アプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) カーソルが左へ正常に移動されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_FAILURE** (0X10) フォントが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Move the cursor one character to the left. */
status = gx_multi_line_text_input_left_arrow(&my_text_input);

/* If status is GX_SUCCESS the multi line text input cursor has been moved one character to the left. */

```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_right_arrow"></a>gx_multi_line_text_input_right_arrow


複数行テキスト入力のカーソルを 1 文字分だけ右に移動します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_right_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>説明

このサービスにより、複数行テキスト入力のカーソルが 1 文字分だけ右に移動されます。 このサービスは、右矢印キーを押すイベントを受信したときに内部的に呼び出されますが、アプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input** 複数行テキスト入力ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) カーソルが右に正常に移動されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Move cursor one character to the right. */
status = gx_multi_line_text_input_right_arrow(&my_text_input);

/* If status is GX_SUCCESS the text input cursor has been moved one character to the right. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_style_add"></a>gx_multi_line_text_input_style_add


複数行入力のスタイルを追加します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_style_add(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    ULONG style);
```

### <a name="description"></a>説明

このサービスにより、複数行テキスト入力ウィジェットにスタイルが追加されます。

### <a name="parameters"></a>パラメーター

- **text_input** 複数行テキスト入力ウィジェット コントロール ブロック
- **style** 追加するスタイル。 **付録 D** には、すべてのウィジェットの定義済みの一般的なスタイルが含まれています

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行テキスト入力のスタイルの追加が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Add style GX_STYTLE_CURSOR_ALWAYS to multi-line text input widget “my_text_input”. */
status = gx_multi_line_text_input_style_add(&my_text_input,
    GX_STYLE_CURSOR_ALWAYS);

/* If status is GX_SUCCESS the style GX_STYLE_CURSOR_ALWAYS has been successfully added. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_style_remove"></a>gx_multi_line_text_input_style_remove


スタイルを削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_remove(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    ULONG style);
```

### <a name="description"></a>説明

このサービスにより、複数行テキスト入力ウィジェットから指定されたスタイルが削除されます。

### <a name="parameters"></a>パラメーター

- **text_input** 複数行テキスト入力ウィジェット コントロール ブロック
- **style** 削除するスタイル。 **付録 D** には、すべてのウィジェットの定義済みの一般的なスタイルが含まれています

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行テキスト入力の作成が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Remove style GX_STYLE_CURSOR_ALWAYS from text input widget “my_text_input”. */
status = gx_multi_line_text_input_style_remove(&my_text_input,
    GX_STYLE_CURSOR_ALWAYS);

/* If status is GX_SUCCESS, the style GX_STYLE_CURSOR_ALWAYS has been successfully removed. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_style_set"></a>gx_multi_line_text_input_style_set

複数行入力のスタイルを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_style_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>説明

このサービスにより、複数行テキスト入力ウィジェットのスタイルが設定されます。

### <a name="parameters"></a>パラメーター

- **text_input** 複数行テキスト入力ウィジェット コントロール ブロック
- **style** 設定するスタイル。 **付録 D** には、すべてのウィジェットの定義済みの一般的なスタイルが含まれています

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行テキスト入力スタイルの設定が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set style GX_STYLE_CURSOR_ALWAYS for text input widget “my_text_input”. */
status = gx_multi_line_text_input_style_set(&my_text_input,
    GX_STYLE_CURSOR_ALWAYS);

/* If status is GX_SUCCESS the text input style has been set */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_text_color_set"></a>gx_multi_line_text_input_text_color_set


複数行テキスト入力のテキストの色を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_text_color_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id,
    GX_RESOURCE_ID readonly_text_color_id);
```

### <a name="description"></a>説明

このサービスにより、複数行テキスト入力ウィジェットのテキストの色が割り当てられます。

### <a name="parameters"></a>パラメーター

- **text_input** 複数行テキスト入力ウィジェット コントロール ブロック
- **normal_fill_color_id** 通常の状態で使用される、通常のテキストの色のリソース ID
- **selected_text_color_id** ウィジェットがフォーカスを得たときに使用される、選択したテキストの色のリソース ID
- **disabled_text_color_id** GX_STYLE_ENABLED がアクティブではないときに使用される、無効なテキストの色のリソース ID
- **readonly_text_color_id** GX_STYLE_ENABLED と GX_STYLE_TEXT_INPUT_READONLY の両方がアクティブな場合に使用される、読み取り専用のテキストの色のリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行テキスト入力の色が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set text colors for the multi-line text input widget “my_text_input”. */
status = gx_multi_line_text_input_text_color_set(&my_text_input,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT,
    GX_COLOR_ID_READONLY_TEXT);

/* If status is GX_SUCCESS, the fill colors of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_text_select"></a>gx_multi_line_text_input_text_select


テキストを選択します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_text_select(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    UINT start_index, UINT end_index);
```

### <a name="description"></a>説明

このサービスでは、指定された開始マークと終了マーク インデックスを使用して複数行テキスト入力のテキストを選択し、選択された塗りつぶしとテキストの色を使用して、選択されたテキストを強調表示します。

### <a name="parameters"></a>パラメーター

- **text_input** 複数行テキスト入力コントロール ブロックへのポインター
- **start_index** 最初に選択された文字のインデックス
- **end_index** 最後に選択された文字のインデックス

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行テキスト入力のテキストの選択が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE** (0x22) インデックスの値が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Select text between index [0, 9]. */
status = gx_multi_line_text_input_text_select(&my_text_input,
    0,9);

/* If status is GX_SUCCESS, the text between 
    index [0, 9] “my_text_input” was selected. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_text_set"></a>gx_multi_line_text_input_text_set


テキストをテキスト入力に割り当てます (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_mult_line_text_input_text_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CHAR *text);
```

### <a name="description"></a>説明

この API は非推奨となり、gx_multi_line_text_input_text_set_ext() に置き換えられました。

このサービスでは、指定された文字列が複数行テキスト入力に割り当てられます。 multi_line_text_input ウィジェットの入力バッファー サイズが文字列の長さよりも小さい場合、文字列は切り詰められます。

### <a name="parameters"></a>パラメーター

- **text_input** 複数行テキスト入力コントロール ブロックへのポインター
- **text** NULL で終わる文字列へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行のテキスト入力のテキストを正常に設定しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_STRING_LENGTH** (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the string “my string” to the text button “my_text_input”. */
status = gx_multi_line_text_input_text_set(&my_text_input,
    “myrstring”);

/* If status is GX_SUCCESS, the content of “my_text_input” bas been reset. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_text_set_ext

## <a name="gx_multi_line_text_input_text_set_ext"></a>gx_multi_line_text_input_text_set_ext


テキストをテキスト入力に割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_mult_line_text_input_text_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>説明

このサービスでは、指定された文字列が複数行テキスト入力に割り当てられます。 multi_line_text_input ウィジェットの入力バッファー サイズが文字列の長さよりも小さい場合、文字列は切り詰められます。

### <a name="parameters"></a>パラメーター

- **text_input** 複数行テキスト入力コントロール ブロックへのポインター
- **string** 割り当てる GX_STRING へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行のテキスト入力のテキストを正常に設定しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_STRING_LENGTH** (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the string “my string” to the text button “my_text_input”. */
GX_STRING string;
string.gx_string_ptr = “myrstring”;
string.gx_string_length = strlen(string.gx_string_ptr);

status = gx_multi_line_text_input_text_set_ext(&my_text_input,
    &string);

/* If status is GX_SUCCESS, the content of “my_text_input” bas been reset. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_up_arrow"></a>gx_multi_line_text_input_up_arrow


複数行テキスト入力のカーソルを前の行に移動します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_input_up_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>説明

このサービスにより、複数行テキスト入力のカーソルがテキストの前の行に移動されます。 このサービスは、上矢印キーを押すイベントを受信したときに内部的に呼び出されますが、アプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) カーソルが前の行に正常に移動されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Move the cursor to the previous line. */
status = gx_multi_line_text_input_up_arrow(&my_text_input);

/* If status is GX_SUCCESS the multi line text input cursor has been moved to the previous line. */

```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_create"></a>gx_multi_line_text_view_create


複数行テキスト ビューを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_view_create(
    GX_MULTI_LINE_TEXT_VIEW *text_view,
    GX_CONST GX_CHAR *name, 
    GX_WINDOW *parent, 
    GX_RESOURCE_ID text_id,
    ULONG style, 
    USHORT text_view_id, 
    GX_CONST GX_RECTANGLE *size);

```

### <a name="description"></a>説明

このサービスにより、GX_MULTI_LINE_TEXT_VIEW ウィジェットが作成されます。 このウィジェットの種類は GX_WINDOW から派生したものであるため、このウィジェットの種類では、すべての gx_window API サービスを使用することもできます。

### <a name="parameters"></a>パラメーター

- **text_view** 複数行テキスト ビュー ウィジェット コントロール ブロック
- **name** テキスト ビュー ウィジェットの名前
- **parent** 親ウィジェットへのポインター
- **text_id** テキスト文字列のリソース ID
- **style** テキスト ビュー ウィジェットのスタイル。 **付録 D** には、すべてのウィジェット用に事前に定義されている一般的なスタイルおよびウィジェット固有のスタイルが含まれています。
- **text_view_id** テキスト ビューのアプリケーション定義 ID
- **size** テキスト ビュー ウィジェットのディメンション

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) 複数行テキスト ビュー ウィジェットが正常に作成されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Create multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_create(&my_text_view,
    “my_text_view”, &my_parent,
    TEXT_STRING_ID, GX_STYLE_BORDER_RAISED,
    MY_TEXT_VIEW_ID, &size);

/* If status is GX_SUCCESS the text view “my_text_view” has been successfully created. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_draw"></a>gx_multi_line_text_view_draw


複数行テキスト ビュー ウィジェットを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_multi_line_text_view_draw(GX_MULTI_LINE_TEXT_VIEW * text_view);
```

### <a name="description"></a>説明

このサービスにより、複数行テキスト ビュー ウィジェットが描画されます。 このサービスは、通常、キャンバスの更新中に内部的に呼び出されますが、カスタムの複数行テキスト ビュー描画関数から呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_view** 複数行テキスト ビュー ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Write a custom multi line text view drawing function. */

VOID my_multi_line_text_view_draw(GX_MULTI_LINE_TEXT_VIEW *view)
{
    /* Call default multi line text view draw. */
    gx_multi_line_text_view_draw(view);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_event_process"></a>gx_multi_line_text_view_event_process


複数行テキスト ビュー イベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_view_event_process(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_EVENT *event);
```

### <a name="description"></a>説明

このサービスによって、複数行テキスト ビュー ウィジェットのイベントが処理されます。

### <a name="parameters"></a>パラメーター

- **text_view** 複数行テキスト ビュー ウィジェット コントロール ブロック
- **event** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) 複数行テキスト ビューのイベント処理が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom event handler. */
UINT my_event_handler(GX_MULTI_LINE_TEXT_VIEW *view, GX_EVENT *event_ptr)
{
    switch(event->gx_event_type)
    {
    case GX_EVENT_SHOW:
        gx_multi_line_text_view_event_process(view, event_ptr);
        /* Add custom actions here. */
        break;
    default:
        gx_multi_line_text_view_event_process (view, event_ptr);
        break;
    }
    return GX_SUCCESS;
}
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_font_set"></a>gx_multi_line_text_view_font_set


複数行テキスト ビューで使用されるフォントを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_view_text_id_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>説明

このサービスによって、複数行テキスト ビュー ウィジェットのフォントが設定されます。

### <a name="parameters"></a>パラメーター

- **text_view** 複数行テキスト ビュー ウィジェット コントロール ブロック
- **font_id** フォントのリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行テキスト ビューのフォントが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set font ID FONT_ID to the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_font_set(&my_text_view, FONT_ID);

/* If status is GX_SUCCESS, the text view “my_text_view” will use the specified font to display its text. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_line_space_set"></a>gx_multi_line_text_view_line_space_set


複数行テキスト ビューの行スペースを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_view_line_space_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_BYTE line_space);
```

### <a name="description"></a>説明

このサービスにより、複数行テキスト ビュー ウィジェットのテキスト行の間隔が設定されます。

### <a name="parameters"></a>パラメーター

- **view** 複数行テキスト ビュー ウィジェット コントロール ブロック
- **line_space** 設定する値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行テキスト ビューの行スペース値が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

```C
/* Set line space of “my_text_view” to 2. */
status = gx_multi_line_text_view_line_space_set(&my_text_view, 2);

/* If status is GX_SUCCESS, the line space of “my_text_view” has been successfully set to 2. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_scroll_info_get"></a>gx_multi_line_text_view_scroll_info_get

複数行テキスト ビューのスクロール情報を取得します


### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_view_scroll_info_get(
    GX_MULTI_LINE_TEXT_VIEW *text_view, ULONG style,
    GX_SCROLL_INFO *info);
```

### <a name="description"></a>説明

このサービスにより、複数行テキスト ビューのスクロール情報が取得されます。

### <a name="parameters"></a>パラメーター

- **text_view** 複数行テキスト ビュー ウィジェット コントロール ブロック
- **Style** GX_SCROLLBAR_HORIZONTAL または GX_SCROLLBAR_VERTICAL
- **Info** スクロール情報の宛先へのポインター。 **付録 I** には GX_LINE_CHART_INFO 構造体の定義が含まれています。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) テキスト ビューのスクロール情報が正常に取得されました
- **GX_FAILURE** (0X10) ウィジェットが表示されていないか、テキス トビューのフォント ID が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_SCROLL_INFO scroll_info;

/* Get scroll information for multi-line text view “my_text_view”. */
status = gx_multi_line_text_view_scroll_info_get(&my_text_view,
    &scroll_info);

/* If status is GX_SUCCESS the “scroll_info” contains the scroll information for multi-line text view “my_text_view”. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_text_color_set"></a>gx_multi_line_text_view_text_color_set


複数行テキスト ビューのテキストの色を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_view_text_color_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCe_ID disabled_text_color_id);
```

### <a name="description"></a>説明

このサービスにより、複数行テキスト ビュー ウィジェットにテキストの色が割り当てられます。

### <a name="parameters"></a>パラメーター

- **text_view** 複数行テキスト ビュー ウィジェット コントロール ブロック
- **normal_text_color_id** 通常の状態で使用される、通常のテキストの色のリソース ID
- **selected_text_color_id** ウィジェットがフォーカスを得たときに使用される、選択したテキストの色のリソース ID
- **disabled_text_color_id** GX_STYLE_ENABLED がアクティブではないときに使用される、無効なテキストの色のリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行テキスト ビューの色が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set text colors for the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_text_color_set(&my_text_view,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS the text color of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_text_id_set"></a>gx_multi_line_text_view_text_id_set


複数行テキスト ビューでシステム テキスト文字列を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_view_text_id_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_RESOURCE_ID text_id);
```

### <a name="description"></a>説明

このサービスにより、複数行のテキスト ビュー ウィジェットに文字列のリソース ID が設定されます。

### <a name="parameters"></a>パラメーター

- **text_view** 複数行テキスト ビュー ウィジェット コントロール ブロック
- **text_id** テキスト文字列のリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行のテキスト ビューの文字列 ID が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_RESOURCE_ID** (0x33) リソース ID が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set string ID STRING_ID to the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_text_id_set(&my_text_view, STRING_ID);

/* If status is GX_SUCCESS the text id of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_text_set"></a>gx_multi_line_text_view_text_set


複数行テキスト ビューにユーザー定義の文字列を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_view_text_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_CONST GX_CHAR *text);
```

### <a name="description"></a>説明

このサービスにより、複数行のテキスト ビュー ウィジェットにテキスト文字列が割り当てられます。 text_view ウィジェットがスタイル GX_STYLE_TEXT_COPY で作成された場合は、ウィジェットによって、割り当てられたテキスト文字列のプライベート コピーが作成されます。そのため、このサービスを要求する前に gx_system_memmory_allocate_set API が 1 回呼び出される必要があります。 GX_STYLE_TEXT_COPY がアクティブでない場合、ウィジェットでは受信文字列のプライベート コピーが作成されないため、割り当てられた文字列は静的またはグローバルに割り当てられる必要があります (つまり、自動または一時変数であってはなりません)。

### <a name="parameters"></a>パラメーター

- **text_view** 複数行テキスト ビュー ウィジェット コントロール ブロック
- **text** NULL で終わるテキスト文字列

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行テキスト ビューの文字列が正常に設定されました
- **GX_SYSTEM_MEMORY_ERROR** (0x30) メモリ アロケーターが定義されていないか、メモリの割り当てに失敗しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set string “my string” to the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_text_set(&my_text_view, “my string”);

/* If status is GX_SUCCESS the text of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_whitespace_set"></a>gx_multi_line_text_view_whitespace_set


複数行テキスト ビューの空白を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_multi_line_text_view_whitespace_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_UBYTE whitespace);
```

### <a name="description"></a>説明

このサービスにより、複数行テキスト ビュー ウィジェットのアウトラインとクライアント領域の間隔が設定されます。

### <a name="parameters"></a>パラメーター

- **text_view** 複数行テキスト ビュー ウィジェット コントロール ブロック
- **whitespace** text_view ウィジェットと表示されるテキストの間の余白の幅 (ピクセル単位)。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 複数行テキスト ビューの空白が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set whitespace of “my_text_view” to 2. */
status = gx_multi_line_text_view_whitespace_set(&my_text_view, 2);

/* If status is GX_SUCCESS the whitespace of “my_text_view” has been successfully set to 2. */
```

### <a name="see-also"></a>参照

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set

## <a name="gx_numeric_pixelmap_prompt_create"></a>gx_numeric_pixelmap_prompt_create


数値ピクセルマップ プロンプトを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_numeric_pixelmap_prompt_create(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    GX_CONST GX_CHAR name, GX_WIDGET *parent,
    GX_RESOURCE_ID text_id, GX_RESOURCE_ID fill_id,
    ULONG style, USHORT pixelmap_prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスにより、数値ピクセルマップ プロンプト ウィジェットが作成されます。 numeric_pixelmap_prompt は、単に独自のバッファーを保持し、gx_numeric_pixelmap_prompt_value_set(INT) API を提供する pixelmap_prompt です。バッファー サイズは定数の GX_NUMERIC_PROMPT_BUFFER_SIZE によって定義されます。この既定値は 16 です。

GX_NUMERIC_PIXELMAP_PROMPT は、GX_PIXELMAP_PROMPT から派生し、すべての gx_pixelmap_prompt API サービスをサポートします。

### <a name="parameters"></a>パラメーター

- **prompt** 数値ピクセルマップ プロンプト コントロール ブロック
- **name** プロンプトの名前
- **parent** 親ウィジェット コントロール ブロック
- **text_id** リソース文字列 ID
- **fill_id** 塗りつぶし領域のピクセルマップ ID
- **style** 数値ピクセルマップ プロンプトのスタイル。**付録 D** には、すべてのウィジェット用に事前に定義されている一般的なスタイルおよびウィジェット固有のスタイルが含まれています。
- **pixelmap_prompt_id** アプリケーションで定義された、プロンプトの ID
- **size** 数値のピクセルマップ プロンプトのディメンション

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) 数値ピクセルマップ プロンプトが正常に作成されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Create “my_numeric_pix_prompt”. */
status = gx_numeric_pixelmap_prompt_create(&my_numeric_pix_prompt,
    “my_numeric_pix_prompt”, &my_parent,
    MY_TEXT_RESOURCE_ID, MY_FEEL_RESOURCE_ID,
    GX_STYLE_BORDER_RAISED, MY_NUMERIC_PIXELMAP_PROMPT_ID,
    &size);

/* If status is GX_SUCCESS the numeric pixelmap prompt “my_numeric_pix_prompt” has been created. */
```

### <a name="see-also"></a>参照

- gx_numeric_pixelmap_format_function_set
- gx_numeric_pixelmap_prompt_value_set

## <a name="gx_numeric_pixelmap_prompt_format_function_set"></a>gx_numeric_pixelmap_prompt_format_function_set


数値ピクセルマップ プロンプトの書式設定関数をオーバーライドします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_numeric_pixelmap_format_function_set(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    OID (*format_func)(GX_NUMERIC_PIXELMAP_PROMPT *, INT));
```

### <a name="description"></a>説明

このサービスにより、数値ピクセルマップ プロンプト ウィジェットの既定の書式設定関数がオーバーライドされます。 既定の書式設定関数は、数値ピクセルマップ プロンプト値を文字列に変換し、それをウィジェットのプライベート バッファーに格納します。 このサービスを使用すると、アプリケーションで独自の書式設定関数を定義して、数値のピクセルマップ プロンプト値を書式設定し、ウィジェットのプライベート バッファーに格納できます。

### <a name="parameters"></a>パラメーター

- **prompt** 数値ピクセルマップ プロンプト コントロール ブロック
- **format_func** 設定する書式設定関数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 数値ピクセルマップ プロンプトの書式設定関数が正常に設定されました
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Define my numeric pixelmap format function. */
VOID my_format_function(GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    INT value)
{
    /* If the value is “1234”, the new format will be “12.34”. */

    INT length;
    gx_utility_ltoa(value / 100,
        prompt->gx_numeric_pixelmap_prompt_buffer,
        GX_NUMERIC_PROMPT_ BUFFER_SIZE);
    Length = GX_STRLEN(prompt->gx_numeric_pixelmap_prompt_buffer);
    prompt->gx_numeric_pixelmap_prompt_buffer[length++] = ‘.’;
    gx_utility_ltoa(value % 100,
        prompt->gx_numeric_pixelmap_prompt_buffer + length,
        GX_NUMERIC_PROMPT_BUFFER_SIZE - length);
}

/* Override default format function of “my_numeric_pix_prompt”. */
status = gx_numeric_pixelmap_prompt_format_function_set(
    &my_numeric_pix_prompt,
    my_format_function);

/* If status is GX_SUCCESS the format function of “my_numeric_pix_prompt” has been override. */
```

### <a name="see-also"></a>参照

- gx_numeric_pixelmap_prompt_create
- gx_numeric_pixelmap_prompt_value_set

## <a name="gx_numeric_pixelmap_prompt_value_set"></a>gx_numeric_pixelmap_prompt_value_set


数値のピクセルマップ プロンプト値を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_numeric_pixelmap_prompt_value_set(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    INT value);
```

### <a name="description"></a>説明

このサービスにより、数値ピクセルマップ プロンプトに整数値が設定されます。

### <a name="parameters"></a>パラメーター

- **prompt** 数値のピクセルマップ プロンプト コントロール ブロック
- **value** 設定する整数値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 数値のピクセルマップ プロンプト値が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set a value to “my_numeric_pix_prompt”. */
status = gx_numeric_pixelmap_prompt_value_set(&my_numeric_pix_prompt, 1000);

/* If status is GX_SUCCESS the value of the numeric pixelmap prompt “my_numeric_pix_prompt” has been set. */
```

### <a name="see-also"></a>参照

- gx_numeric_pixelmap_prompt_create
- gx_numeric_pixelmap_format_function_set

## <a name="gx_numeric_prompt_create"></a>gx_numeric_prompt_create


数値プロンプトを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_numeric_prompt_create( 
    GX_NUMERIC_PROMPT *prompt,
    GX_CONST GX_CHAR name, GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    ULONG style, USHORT prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスにより、数値プロンプト ウィジェットが作成されます。 numeric_prompt は、単に独自のバッファーを保持し、gx_numeric_prompt_value_set (INT) API を提供するプロンプトです。バッファー サイズは定数の GX_NUMERIC_PROMPT_BUFFER_SIZE によって定義されます。この既定値は 16 です。

GX_NUMERIC_PROMPT は GX_PROMPT から派生し、すべての gx_prompt API サービスをサポートします。

### <a name="parameters"></a>パラメーター

- **prompt** 数値のプロンプト コントロール ブロック
- **name** プロンプトの名前
- **parent** 親ウィジェット コントロール ブロック
- **text_id** リソース文字列 ID
- **style** 数値プロンプトのスタイル。**付録 D** には、すべてのウィジェット用に事前に定義されている一般的なスタイルおよびウィジェット固有のスタイルが含まれています。
- **prompt_id** アプリケーションで定義された、プロンプトの ID
- **size** 数値プロンプトのディメンション

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 数値プロンプトが正常に作成されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Create “my_numeric _prompt”. */
status = gx_numeric_prompt_create(&my_numeric_prompt,
    “my_numeric_prompt”, &my_parent,
    MY_TEXT_RESOURCE_ID, GX_STYLE_BORDER_RAISED, MY_NUMERIC_PROMPT_ID,
    &size);

/* If status is GX_SUCCESS the numeric prompt “my_numeric_prompt” has been created. */
```

### <a name="see-also"></a>参照

- gx_numeric_format_function_set
- gx_numeric_prompt_value_set

## <a name="gx_numeric_prompt_format_function_set"></a>gx_numeric_prompt_format_function_set


数値プロンプトの書式設定関数をオーバーライドします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_numeric_format_function_set(
    GX_NUMERIC_PROMPT *prompt,
    VOID (*format_func)(GX_NUMERIC_PROMPT *, INT));
```

### <a name="description"></a>説明

このサービスにより、数値プロンプト ウィジェットの既定の書式設定関数がオーバーライドされます。 既定の書式設定関数は、数値のプロンプト値を文字列に変換し、それをウィジェットのプライベート バッファーに格納します。 このサービスを使用すると、アプリケーションで独自の書式設定関数を定義して、数値のプロンプト値を書式設定し、ウィジェットのプライベート バッファーに格納できます。

### <a name="parameters"></a>パラメーター

- **prompt** 数値のプロンプト コントロール ブロック
- **format_func** 設定する書式設定関数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 数値プロンプトの書式設定関数が正常に設定されました
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Define my numeric format function. */
VOID my_format_function(GX_NUMERIC_PROMPT *prompt, INT value)
{
    /* If the value is “1234”, the new format will be “12.34”. */

    INT length;
    gx_utility_ltoa(value / 100, prompt->gx_numeric_prompt_buffer,
        GX_NUMERIC_PROMPT_ BUFFER_SIZE);
    Length = GX_STRLEN(prompt->gx_numeric_prompt_buffer);
    prompt->gx_numeric_prompt_buffer[length++] = ‘.’;
    gx_utility_ltoa(value % 100,
        prompt->gx_numeric_prompt_buffer + length,
        GX_NUMERIC_PROMPT_BUFFER_SIZE - length);
}

/* Override the default format function of “my_numeric_prompt”. */
status = gx_numeric_prompt_format_function_set(&my_numeric_prompt,
    my_format_function);

/* If status is GX_SUCCESS, the format function of “my_numeric_prompt” has been override. */
```

### <a name="see-also"></a>参照

- gx_numeric_prompt_create
- gx_numeric_prompt_value_set

## <a name="gx_numeric_prompt_value_set"></a>gx_numeric_prompt_value_set


数値のプロンプト値を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_numeric_prompt_value_set(
    GX_NUMERIC_PROMPT *prompt, 
    INT value);
```

### <a name="description"></a>説明

このサービスにより、数値プロンプトに整数値が設定されます。

### <a name="parameters"></a>パラメーター

- **prompt** 数値のプロンプト コントロール ブロック
- **value** 設定する整数値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 数値のプロンプト値が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set a value to “my_numeric_prompt”. */
status = gx_numeric_prompt_value_set(&my_numeric_prompt, 1000);

/* If status is GX_SUCCESS the value of the numeric prompt “my_numeric_prompt” has been set. */
```

### <a name="see-also"></a>参照

- gx_numeric_prompt_create
- gx_numeric_format_function_set

## <a name="gx_numeric_scroll_wheel_create"></a>gx_numeric_scroll_wheel_create


数値スクロール ホイールを作成します

### <a name="prototype"></a>プロトタイプ


UINT gx_numeric_scroll_wheel_create( GX_NUMERIC_SCROLL_WHEEL *wheel, GX_CONST GX_CHAR *name, GX_WIDGET *parent, INT start_val, INT end_val, ULONG style, USHORT wheel_id, GX_CONST GX_RECTANGLE *size);

### <a name="description"></a>説明

このサービスにより、数値スクロール ホイール ウィジェットが作成されます。

数値スクロール ホイールは、数値の範囲を表示するために特に使用されるスクロール ホイール ウィジェットの一種です。 その他の種類のスクロール ホイール ウィジェットも使用できます。 スクロール ホイール ウィジェットの階層、ウィジェットの種類、およびウィジェットの派生の詳細については、gx_scroll_wheel_create() API を参照してください。

GX_NUMERIC_SCROLL_WHEEL は GX_TEXT_SCROLL_WHEEL から派生し、すべての gx_text_scroll_wheel および gx_scroll_wheel サービスをサポートしています。

スクロール ホイールをスクロールすると、すべてのスクロール ホイールの種類によって GX_EVENT_LIST_SELECT イベントがその親に対して生成されます。

数値スクロール ホイールは、デフォルトで abs(end_val – start_val) + 1 の行数を持ちます。 つまり、スクロール ホイールによって、start_val と end_val の間のすべての値が表示され、各行で 1 増加または減少します。 アプリケーションで範囲をどのように表示するかに応じて、start_val は end_val より大きくも小さくもできます。

アプリケーションで行の増減を変更する場合は、数値スクロール ホイールを作成した後に gx_scroll_wheel_total_rows_set() を呼び出すことによってこれを行うことができます。 たとえば、1980 から 2020 年の値を 5 ずつ増加させて表示するスクロール ホイールを作成するアプリケーションでは、次のようにします。

```C
gx_numeric_scroll_wheel_create(&wheel, GX_NULL, parent, 1980,
    2020, style, id, &size);

/* the years 1980 through 2020, inclusive, incrementing by 5 years,
yields 9 total rows */

gx_scroll_wheel_total_rows_set(&wheel, 9);
```

### <a name="parameters"></a>パラメーター

- **wheel** 数値スクロール ホイール コントロール ブロックへのポインター
- **name** ピクセルマップ ボタン ウィジェットの論理名
- **parent** 親ウイジェットへのポインター
- **start_val** 開始数値
- **end_val** 終了数値
- **style** チェックボックスのスタイル。 **付録 D** には、すべてのウィジェット用に事前に定義されている一般的なスタイルおよびウィジェット固有のスタイルが含まれています。
- **wheel_id** スクロール ホイールのアプリケーション定義 ID
- **size** スクロール ホイール ウィジェットのディメンション

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 数値スクロール ホイールが正常に作成されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Create “year_wheel”. */
status = gx_numeric_scroll_wheel_create(&year_wheel,
    “year_selector””, &parent,
    1980, 2040,
    GX_STYLE_ENABLED | GX_STYLE_TEXT_CENTER |
    GX_STYLE_TRANSPARENT | GX_STYLE_WRAP |
    GX_STYLE_TEXT_SCROLL_WHEEL_ROUND,
    YEAR_WHEEL_ID,
    &size);

/* If status is GX_SUCCESS the scroll wheel “year_wheel” has been created. */
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_text_get

## <a name="gx_numeric_scroll_wheel_range_set"></a>gx_numeric_scroll_wheel_range_set


数値スクロール ホイールの値の範囲を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT
gx_numeric_scroll_wheel_range_set(
    GX_NUMERIC_SCROLL_WHEEL *wheel,
    INT start_val, INT end_val);
```

### <a name="description"></a>説明

このサービスにより、数値スクロール ホイール ウィジェットで許可および表示される値の範囲が変更されます。

数値スクロール ホイールは、数値の範囲を表示するために特に使用されるスクロール ホイール ウィジェットの一種です。 その他の種類のスクロール ホイール ウィジェットも使用できます。 スクロール ホイール ウィジェットの階層、ウィジェットの種類、およびウィジェットの派生の詳細については、gx_scroll_wheel_create() API を参照してください。

この API を呼び出すと、スクロール ホイールの合計行数が abs(end_val – start_val) + 1 にリセットされます。これは、行ごとにスクロール ホイールが 1 ずつ増加することを意味します。 これを変更するには、アプリケーションで gx_scroll_wheel_total_rows_set() を呼び出し、行の合計数を変更し、行間の値の増分を効果的に変更します。

### <a name="parameters"></a>パラメーター

- **wheel** 数値スクロール ホイール コントロール ブロックへのポインター
- **start_val** 開始数値 
- **end_val** 終了数値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 数値スクロール ホイール範囲が正常に設定されました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド 

### <a name="example"></a>例

```C
/* Change range of “rate” scroll wheel. */

status = gx_numeric_scroll_wheel_range_set(&year_wheel, 0, 200);

/* If status is GX_SUCCESS the scroll wheel range has been modified. */
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_pixelmap_button_create"></a>gx_pixelmap_button_create


ピクセルマップ ボタンを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_pixelmap_button_create(
    GX_PIXELMAP_BUTTON *button,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID normal_id,
    GX_RESOURCE_ID selected_id,
    GX_RESOURCE_ID disabled_id,
    ULONG style,
    USHORT pixelmap_button_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスにより、ピクセルマップ ボタン ウィジェットが作成されます。

GX_PIXELMAP_BUTTON は GX_BUTTON から派生し、すべての gx_button サービスをサポートします。

### <a name="parameters"></a>パラメーター

- **button** ピクセルマップ ボタン コントロール ブロックへのポインター
- **name** ピクセルマップ ボタン ウィジェットの論理名
- **parent** 親ウイジェットへのポインター
- **normal_id** 通常状態のリソース ID
- **selected_id** 選択状態のリソース ID
- **disabled_id** 無効状態のリソース ID
- **style** チェックボックスのスタイル。 **付録 D** には、すべてのウィジェット用に事前に定義されている一般的なスタイルおよびウィジェット固有のスタイルが含まれています。
- **pixelmap_button_id** アプリケーションで定義された、ピクセルマップ ボタンの ID
- **size** ピクセルマップ ボタンのディメンション

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ピクセルマップ ボタンが正常に作成されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Create “my_pixelmap_button”. */
status = gx_pixelmap_button_create(&my_pixelmap_button,
    “my_pixelmap_button”, &my_parent,
    MY_NORMAL_RESOURCE_ID, MY_SELECTED_RESOURCE_ID,
    MY_DESELECTED_RESOURCE_ID, GX_STYLE_BORDER_RAISED,
    MY_PIXELMAP_BUTTON_ID,
    &size);

/* If status is GX_SUCCESS the pixelmap button “my_pixelmap_button” has been created. */
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_draw
- gx_pixelmap_button_pxielmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_button_draw"></a>gx_pixelmap_button_draw


ピクセルマップ ボタンを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_pixelmap_button_draw(GX_PIXELMAP_BUTTON *button);
```

### <a name="description"></a>説明

このサービスにより、ピクセルマップ ボタン ウィジェットが描画されます。 通常、この関数は GUIX キャンバスの更新メカニズムによって内部的に呼び出されますが、カスタム ピクセルマップ ボタン ウイジェットのカスタム描画関数の実装を支援するためにアプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **button** ピクセルマップ ボタン コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom pixelmap button drawing function. */

VOID my_pixelmap_button_draw(GX_PIXELMAP_BUTTON *button)
{
    /* Call default pixelmap button draw. */
    gx_pixelmap_button_draw(button);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_pxielmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_button_event_process"></a>gx_pixelmap_button_event_process


ピクセルマップ ボタンのイベント処理

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_pixelmap_button_event_process(
    GX_PIXELMAP_BUTTON *button,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>説明

このサービスにより、ピクセルマップ ボタン ウィジェットの種類の既定のイベント処理が提供されます。

### <a name="parameters"></a>パラメーター

- **button** ピクセルマップ ボタン コントロール ブロックへのポインター
- **event_ptr** GX_EVENT 構造体へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ピクセルマップ ボタンの描画が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
switch(event_ptr->gx_event_type)
{
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_pixelmap_button_event_process(icon, event_ptr);
    
        /* add my own handling here */
        break;
}
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_pxielmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_button_pixelmap_set"></a>gx_pixelmap_button_pixelmap_set


ピクセルマップをボタンに割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_pixelmap_button_pixelmap_set(
    GX_PIXELMAP_BUTTON *button, 
    GX_RESOURCE_ID normal_id,
    GX_RESOURCE_ID selected_id, 
    GX_RESOURCE_ID disabled_id);
```

### <a name="description"></a>説明

このサービスにより、ピクセルマップがピクセルマップ ボタンに設定されます。

### <a name="parameters"></a>パラメーター

- **button** ピクセルマップ ボタン コントロール ブロックへのポインター
- **normal_id** 通常の状態として使用されるピクセルマップのリソース ID
- **selected_id** ボタンが選択されたときに使用されるピクセルマップのリソース ID
- **disabled_id** ボタンが選択解除されたときに使用されるピクセルマップのリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) ピクセルマップがボタンに正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Draw “my_pixelmap_button”. */
status = gx_pixelmap_button_pixelmap_set (&my_pixelmap_button,
    NORMAL_ID, SELECTED_ID,
    DISABLED_ID);

/* If status is GX_SUCCESS the pixelmap button is properly configured with the specified pixelmaps. */
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_prompt_create"></a>gx_pixelmap_prompt_create


ピクセルマップ プロンプトを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_pixelmap_prompt_create(
    GX_PIXELMAP_PROMPT *prompt,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    GX_RESOURCE_ID fill_pixelmap_id,
    ULONG style,
    USHORT pixelmap_prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスにより、ピクセルマップ プロンプト ウィジェットが作成されます。 ピクセルマップ プロンプトは、ピクセルマップを使用してプロンプトの背景を描画するという点で、標準の GX_PROMPT とは異なります。 作成関数は、1 つのピクセルマップ (通常の状態の塗りつぶしピクセルマップ) の ID を受け取ります。 ピクセルマップ プロンプトには、最大 6 つのピクセルマップを割り当てることができます。

### <a name="parameters"></a>パラメーター

- **prompt** ピクセルマップ プロンプト コントロール ブロックへのポインター
- **name** ピクセルマップ プロンプト ウィジェットの論理名
- **parent** 親ウイジェットへのポインター
- **text_id** テキストのリソース ID
- **fill_id** 塗りつぶしのリソース ID
- **style** チェックボックスのスタイル。 **付録 D** には、すべてのウィジェット用に事前に定義されている一般的なスタイルおよびウィジェット固有のスタイルが含まれています。
- **pixelmap_prompt_id** アプリケーションで定義された、ピクセル プロンプトの ID
- **size** ピクセルマップ プロンプトのディメンション

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ピクセルマップ プロンプトの作成が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットは既に作成されています

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Create “my_pixelmap_prompt”. */
status = gx_pixelmap_prompt_create(&my_pixelmap_prompt,
    “my_pixelmap_prompt”, &my_parent,
    MY_TEXT_RESOURCE_ID, MY_LEFT_RESOURCE_ID,
    MY_FILL_RESOURCE_ID, MY_RIGHT_RESOURCE_ID,
    GX_STYLE_BORDER_RAISED, MY_PIXELMAP_PROMPT_ID,
    &size);

/* If status is GX_SUCCESS the pixelmap prompt “my_pixelmap_prompt” has been created. */
```

### <a name="see-also"></a>参照

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_set

## <a name="gx_pixelmap_prompt_draw"></a>gx_pixelmap_prompt_draw


ピクセルマップ プロンプトを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_pixelmap_prompt_draw(GX_PIXELMAP_PROMPT *prompt);
```

### <a name="description"></a>説明

このサービスにより、ピクセルマップ プロンプト ウィジェットが描画されます。 通常、この関数は GUIX キャンバスの更新メカニズムによって内部的に呼び出されますが、カスタム ピクセルマップ プロンプト ウイジェットのカスタム描画関数の実装を支援するためにアプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **prompt** ピクセルマップ プロンプト コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Write a custom pixelmap prompt drawing function. */

VOID my_pixelmap_button_draw(GX_PIXELMAP_PROMPT *prompt)
{
    /* Call default pixelmap prompt draw. */
    gx_pixelmap_prompt_draw(prompt);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_set

## <a name="gx_pixelmap_prompt_pixelmap_set"></a>gx_pixelmap_prompt_pixelmap_set


ピクセルマップをプロンプトに割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_pixelmap_prompt_pixelmap_set(
    GX_PIXELMAP_PROMPT *prompt,
    GX_RESOURCE_ID normal_left_pixelmap,
    GX_RESOURCE_ID normal_fill_pixelmap,
    GX_RESOURCE_ID normal_right_pixelmap,
    GX_RESOURCE_ID selected_left_pixelmap,
    GX_RESOURCE_ID selected_fill_pixelmap,
    GX_RESOURCE_ID selected_right_pixelmap);
```

### <a name="description"></a>説明

このサービスにより、ピクセルマップ プロンプトにピクセルマップ ID が割り当てられます。 左、塗りつぶし、および右のピクセルマップ ID は、幅がさまざまで高さが共通であるプロンプトに対して、アプリケーションで 1 つのセットのピクセルマップを使用してストレージ要件を節約するために使用されます。 左と右の ID が使用されていない場合は、0 に設定する必要があります。 入力フォーカスが得られたときにプロンプトの描画を変える必要がある場合は、選択したピクセルマップ ID がその目的のために使用されます。 選択した ID が使用されていない場合、または通常の ID と同じである場合は、0 に設定します。

### <a name="parameters"></a>パラメーター

- **prompt** ピクセルマップ プロンプト コントロール ブロックへのポインター
- **normal_left_id** 通常の状態で、左側で使用されるピクセルマップのリソース ID
- **normal_fill_id** 通常の状態でタイル状の塗りつぶしとして使用されるピクセルマップのリソース ID
- **normal_right_id** 通常の状態で、右側で使用されるピクセルマップのリソース ID
- **selected_left_id** 選択された状態で、左側で使用されるピクセルマップのリソース ID
- **selected_fill_id** 選択された状態で、タイル状の塗りつぶしとして使用されるピクセルマップのリソース ID
- **selected_right_id** 選択された状態で、右側で使用されるピクセルマップのリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) ピクセルマップがプロンプトに正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_RESOURCE_ID** (0x33) リソース ID が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Assign pixelmap IDs to “my_prompt”. Only the normal state pixelmaps are used in this case */
status = gx_pixelmap_prompt_pixelmap_set (&my_prompt,
    normal_left_id, normal_fill_id,
    normal_right_id, 0, 0, 0);

/* If status is GX_SUCCESS the pixelmap prompt is properly configured with pixelmaps. */
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_slider_create"></a>gx_pixelmap_slider_create


ピクセルマップ スライダーを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_pixelmap_slider_create(
    GX_PIXELMAP_SLIDER *slider,
    GX_CONST GX_CHAR *name, GX_WIDGET *parent,
    GX_SLIDER_INFO *info,
    GX_PIXELMAP_SLIDER_INFO *pixelmap_info, ULONG style,
    USHORT pixelmap_slider_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスにより、ピクセルマップ スライダー ウィジェットが作成されます。

### <a name="parameters"></a>パラメーター

- **slider** ピクセルマップ スライダー コントロール ブロックへのポインター
- **name** ピクセルマップ スライダー ウィジェットの論理名
- **parent** 親ウイジェットへのポインター
- **info** スライダーの最小値、最大値、現在の値、および針の制限を定義する値を格納する GX_SLIDER_INFO 構造体へのポインター。 **付録 I** には GX_PIXELMAP_SLIDER_INFO 構造体の定義が含まれています。
- **pixelmap_info** スライダーの背景と針を描画するために使用されるピクセルマップを定義する GX_PIXELMAP_SLIDER_INFO 構造体へのポインター。 **付録 I** には GX_PIXELMAP_SLIDER_INFO 構造体の定義が含まれています。 スライダーの背景には、1 つまたは 2 つのピクセルマップを使用できます。 1 つの場合には、針の移動につれて背景が変化しません。 2 つの背景が定義されている場合には、針の前の背景には最初の背景ピクセルマップが使用され、針の後の背景には 2 番目の背景ピクセルマップが使用されます。
- **style** スライダーのスタイル。 **付録 D** には、すべてのウィジェット用に事前に定義されている一般的なスタイルおよびウィジェット固有のスタイルが含まれています。
- **pixelmap_slider_id** ピクセルマップ スライダーのアプリケーション定義 ID
- **size** ピクセルマップ プロンプトのディメンション

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ピクセルマップ スライダーが正常に作成されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_SLIDER_INFO info;
GX_PIXELMAP_SLIDER_INFO pixelmap_info;

/* Initiate slider information structure. */
info.gx_slider_info_min_val = 0;
info.gx_slider_info_max_val = 100;
info.gx_slider_info_current_val = 50;
info.gx_slider_info_min_travel = 10;
info.gx_slider_info_max_tralvel = 10;
info.gx_slider_info_needle_width = 5;
info.gx_slider_info_needle_height = 10;
info.gx_slider_info_needle_inset = 5;
info.gx_slider_info_needle_hotspot_offset;

/* Initiate pixelmap slider information structure. */
pixelmap_info.gx_pixelmap_slider_info_lower_background_pixelmap =
                                        GX_PIXELMAP_ID_ORANGE;
pixelmap_info.gx_pixelmap_slider_info_upper_background_pixelmap =
                                        GX_PIXELMAP_ID_EMPTY;
pixelmap_info.gx_pixelmap_slider_info_needle_pixelmap =
                                        GX_PIXELMAP_ID_NEEDLE;

/* Create “my_pixelmap_slider”. */
status = gx_pixelmap_slider_create(&my_pixelmap_slider,
                            “my_pixelmap_slider”, &my_parent,
                            &info, &pixelmap_info,
                            GX_STYLE_BORDER_RAISED,
                            MY_PIXELMAP_SLIDER_ID, &size);

/* If status is GX_SUCCESS the pixelmap slider “my_pixelmap_slider” has been created. */
```

### <a name="see-also"></a>参照

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_pixelmap_slider_draw"></a>gx_pixelmap_slider_draw


ピクセルマップ スライダーを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_pixelmap_slider_draw(GX_PIXELMAP_SLIDER *slider);
```

### <a name="description"></a>説明

このサービスにより、ピクセルマップ スライダー ウィジェットが描画されます。 通常、この関数は GUIX キャンバスの更新メカニズムによって内部的に呼び出されますが、カスタム ピクセルマップ スライダー ウイジェットのカスタム描画関数の実装を支援するためにアプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **slider** ピクセルマップ スライダー コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom pixelmap slider drawing function. */

VOID my_pixelmap_slider_draw(GX_PIXELMAP_SLIDER *pixelmap_slider)
{
    /* Call default pixelmap slider draw. */
    gx_pixelmap_slider_draw(pixelmap_slider);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_pixelmap_slider_event_process"></a>gx_pixelmap_slider_event_process


ピクセルマップのスライダー イベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_pixelmap_slider_event_process(
    GX_PIXELMAP_SLIDER *slider,
    GX_EVENT *event);
```

### <a name="description"></a>説明

このサービスにより、指定されたピクセルマップ スライダー ウィジェットのイベントが処理されます。

### <a name="parameters"></a>パラメーター

- **slider** ピクセルマップへのポインター
- **slider** 処理するイベントへのコントロール ブロック イベント ポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) ピクセルマップ スライダーのイベント処理に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Write a custom event processing function. */
UINT my_event_hanlder(GX_PIXELMAP_SLIDER *pixelmap_slider, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_pixelmap_slider_event_process(pixelmap_slider,
                                                    event_ptr);

        /* add my own handling here */
        break;
    default:
        status = gx_pixelmap_slider_event_process(pixelmap_slider,
                                                  event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>参照

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_pixelmap_slider_pixelmap_set"></a>gx_pixelmap_slider_pixelmap_set


ピクセルマップをスライダーに割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_pixelmap_slider_pixelmap_set(
    GX_PIXELMAP_SLIDER *slider,
    GX_PIXELMAP_SLIDER_INFO *pixinfo);
```

### <a name="description"></a>説明

このサービスにより、ピクセルマップがピクセルマップ スライダーに設定されます。

### <a name="parameters"></a>パラメーター

- **slider** ピクセルマップ スライダー コントロール ブロックへのポインター
- **pixinfo** スライダーの背景と針を描画するために使用されるピクセルマップを定義する、GX_PIXELMAP_SLIDER_INFO 構造体へのポインター。 **付録 I** には GX_PIXELMAP_SLIDER_INFO 構造体の定義が含まれています。 スライダーの背景には、1 つまたは 2 つのピクセルマップを使用できます。 1 つの場合には、針の移動につれて背景が変化しません。 2 つの背景が定義されている場合には、針の前の背景には最初の背景ピクセルマップが使用され、針の後の背景には 2 番目の背景ピクセルマップが使用されます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) ピクセルマップがスライダーに正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_PIXELMAP_SLIDER_INFO pixelmap_info;

/* Initiate pixelmap slider information structure. */
pixelmap_info.gx_pixelmap_slider_info_lower_background_pixelmap =
                                        GX_PIXELMAP_ID_ORANGE;
pixelmap_info.gx_pixelmap_slider_info_upper_background_pixelmap =
                                        GX_PIXELMAP_ID_EMPTY;
pixelmap_info.gx_pixelmap_slider_info_needle_pixelmap =
                                        GX_PIXELMAP_ID_NEEDLE;

/* Draw “my_pixelmap_button”. */
status = gx_pixelmap_slider _pixelmap_set (&my_pixelmap_slider,
                                &pixelmap_info);

/* If status is GX_SUCCESS the pixelmap slider is properly configured with “pixelmap_info”. */
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_progress_bar_background_draw"></a>gx_progress_bar_background_draw


進行状況バーの背景を描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_progress_bar_background_draw(GX_PROGRESS_BAR *progress_bar)
```

### <a name="description"></a>説明

このサービスにより、指定された進行状況バーの背景が描画されます。 この関数は gx_progress_bar_draw() の一部として内部的に呼び出されますが、アプリケーションがカスタムの進行状況バー描画関数を定義する場合をサポートするために、アプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **progress bar** 進行状況バー コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom progress bar drawing function. */

VOID my_progress_bar_draw(GX_PROGRESS_BAR *progress_bar)
{
    /* Call default progress bar background draw. */
    gx_progress_bar_background_draw(progress_bar);

    /* Call default progress bar text draw. */
    gx_progress_bar_text_draw(progress_bar);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_value_set

## <a name="gx_progress_bar_create"></a>gx_progress_bar_create


進行状況バーを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_progress_bar_create(
    GX_PROGRESS_BAR *progress_bar,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_PROGRESS_BAR_INFO *progress_bar_info,
    ULONG style, 
    USHORT progress_bar_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスにより、進行状況バー ウィジェットが作成されます。

### <a name="parameters"></a>パラメーター

- **progress_bar** 進行状況バー コントロール ブロック
- **name** 論理名
- **parent** 親ウィジェットへのポインター
- **progress_bar_info** GX_PROGRESS_BAR_INFO 構造体へのポインター。 **付録 I** には GX_PROGRESS_BAR_INFO 構造体の定義が含まれています。
- **style** 進行状況バーのスタイル。 **付録 D** には、すべてのウィジェット用に事前に定義されている一般的なスタイルおよびウィジェット固有のスタイルが含まれています。
- **progress_bar_id** アプリケーション定義の進行状況バーの ID
- **size**: 進行状況バーの大きさ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 進行状況バーの作成に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE**: (0x19) ウィジェット コントロール ブロック サイズが無効です
- **GX_INVALID_WIDGET** (0x12) 親ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_PROGRESS_BAR_INFO info;
GX_RECTANGLE size;

info.gx_progress_bar_info_min_val = 0;
info.gx_progress_bar_info_max_val = 100;
info.gx_progress_bar_info_current_val = 0;
info.gx_progress_bar_font_id = GX_FONT_ID_SYSTEM_FONT;
info.gx_progress_bar_normal_text_color = GX_COLOR_ID_WHITE;
info.gx_progress_bar_selected_text_color = GX_COLOR_ID_BLUE;
info.gx_progress_bar_fill_pixelmap = 0;

size.gx_rectangle_left = 10;
size.gx_rectangle_top = 10;
size.gx_rectangle_right = 110;
size.gx_rectangle_bottom = 140;

/* Create a progress bar with the specified information. */
status = gx_progress_bar_create(&my_progress_bar, GX_NULL, GX_NULL,
                        &info, GX_STYLE_BORDER_THIN,
                        0, &size);

/* If status is GX_SUCSESS the progress bar “my_progress_bar” has been successfully created. */
```

### <a name="see-also"></a>参照

- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_draw"></a>gx_progress_bar_draw


進行状況バーを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_progress_bar_draw(GX_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>説明

このサービスにより、進行状況バー ウィジェットが描画されます。 通常、この関数は GUIX キャンバスの更新メカニズムによって内部的に呼び出されますが、カスタム進行状況バー ウイジェットのカスタム描画関数の実装を支援するためにアプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **progress_bar** 進行状況バー コントロール ブロック

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom progress bar drawing function. */

VOID my_progress_bar_draw(GX_PROGRESS_BAR *progress_bar)
{
    /* Call default progress bar draw. */
    gx_progress_bar_draw(progress_bar);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_progress_bar_create
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_event_process"></a>gx_progress_bar_event_process


進行状況バーのイベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_progress_bar_event_process(
    GX_PROGRESS_BAR *progress_bar,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>説明

このサービスでは、進行状況バーのイベントが処理されます。

### <a name="parameters"></a>パラメーター

- **progress_bar** 進行状況バー コントロール ブロック
- **event_ptr** GX_EVENT 構造体へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) プロンプトの作成に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Write a custom event processing function. */

UINT my_event_process (GX_PROGRESS_BAR *progress_bar, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_progress_bar_event_process(progress_bar,
                                                event_ptr);
        /* add my own handling here */
        break;
    default:
        status = gx_progress_bar_event_process(progress_bar,
                                                event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>参照

- gx_progress_bar_create
- gx_progress_bar_event_draw
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_font_set"></a>gx_progress_bar_font_set


進行状況バーのテキストのフォントを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_progress_bar_font_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>説明

このサービスにより、進行状況バー ウィジェットのフォントが設定されます。

### <a name="parameters"></a>パラメーター

- **progress_bar** 進行状況バー コントロール ブロック
- **font_id** フォントのリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 進行状況バーのフォントの設定に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
UINT status = gx_progress_bar_font_set(&progress_bar,
                                        GX_FONT_ID_MEDIUM);

/* if status is GX_SUCCESS, the font was successfully assigned. */
```

### <a name="see-also"></a>参照

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_info_set"></a>gx_progress_bar_info_set


進行状況バーの情報の構造を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_progress_bar_info_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_PROGRESS_BAR_INFO *info);
```

### <a name="description"></a>説明

このサービスでは、進行状況バー ウィジェットの情報の構造がリセットされます。

### <a name="parameters"></a>パラメーター

- **progress_bar** 進行状況バー コントロール ブロック
- **info** GX_PROGRESS_BAR_INFO 構造体へのポインター。 **付録 I** には GX_PROGRESS_BAR_INFO 構造体の定義が含まれています。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 進行状況バーの情報が正常にリセットされました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_PROGRESS_BAR_INFO info;

info.gx_progress_bar_info_min_val = 0;
info.gx_progress_bar_info_max_val = 100;
info.gx_progress_bar_info_current_val = 0;
info.gx_progress_bar_font_id = GX_FONT_ID_SYSTEM_FONT;
info.gx_progress_bar_normal_text_color = GX_COLOR_ID_WHITE;
info.gx_progress_bar_selected_text_color = GX_COLOR_ID_BLUE;
info.gx_progress_bar_fill_pixelmap = 0;

status = gx_progress_bar_info_set(&progress_bar, &info);

/* if status == GX_SUCCESS the progress bar info was re-assigned. */
```

### <a name="see-also"></a>参照

- gx_progress_bar_info_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_pixelmap_set"></a>gx_progress_bar_pixelmap_set


進行状況バーの描画に使用されるピクセルマップを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_progress_bar_pixelmap_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID pixelmap_id);
```

### <a name="description"></a>説明

このサービスでは、進行状況バーの背景を塗りつぶすのに使用されるピクセルマップが設定されます。

### <a name="parameters"></a>パラメーター

- **progress_bar** 進行状況バー コントロール ブロック
- **pixelmap_id** ピクセルマップのリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 進行状況バーのピクセルマップの設定に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
UINT status = gx_progress_bar_pixelmap_set(&progress_bar,
                                GX_PIXELMAP_ID_PROGRESS_FILL);

/* if status is GX_SUCCESS, the pixelmap was successfully assigned. */
```

### <a name="see-also"></a>参照

- gx_progress_bar_pielmap_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_range_set"></a>gx_progress_bar_range_set


進行状況バーの値の範囲を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_progress_bar_range_set(
    GX_PROGRESS_BAR *progress_bar,
    INT min_value, 
    INT max_value);
```

### <a name="description"></a>説明

このサービスでは、進行状況バーの値の範囲が設定されます。

### <a name="parameters"></a>パラメーター

- **progress_bar** 進行状況バー コントロール ブロック
- **min_value** 進行状況バーの最小値
- **max_value** 進行状況バーの最大値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 進行状況バーの範囲の設定に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
UINT status = gx_progress_bar_range_set(progress_bar, 0, 100);

/* if status is GX_SUCCESS, the progress bar range was successfully assigned. */
```

### <a name="see-also"></a>参照

- gx_progress_bar_range_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_text_color_set"></a>gx_progress_bar_text_color_set


進行状況バーのテキストの色を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_progress_bar_text_color_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCE_ID disabled_text_color);
```

### <a name="description"></a>説明

このサービスにより、進行状況バー ウィジェットのテキストの色が設定されます。

### <a name="parameters"></a>パラメーター

- **progress_bar** 進行状況バー コントロール ブロック
- **normal_text_color** 通常の状態で使用される通常のテキストの色のリソース ID
- **selected_text_color** ウィジェットがフォーカスを得たときに使用される、選択したテキストの色のリソース ID
- **disabled_text_color** GX_STYLE_ENABLED がアクティブではないときに使用される、無効なテキストの色のリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 進行状況バーのテキストの色の設定に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set text colors for the progress bar “my_progress_bar”*/
UINT status = gx_progress_bar_text_color_set(&my_progress_bar,
                        GX_COLOR_ID_NORMAL_TEXT,
                        GX_COLOR_ID_SELECTED_TEXT,
                        GX_COLOR_ID_DISABLED_TEXT);

/* if status is GX_SUCCESS, the progress bar text colors were successfully assigned. */
```

### <a name="see-also"></a>参照

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_text_draw"></a>gx_progress_bar_text_draw


進行状況バーのテキストを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_progress_bar_text_draw(GX_PROGRESS_BAR *progress_bar)
```

### <a name="description"></a>説明

このサービスでは、指定された進行状況バーのテキストが描画されます。 この関数は gx_progress_bar_draw() の一部として内部的に呼び出されますが、アプリケーションがカスタムの進行状況バー描画関数を定義する場合をサポートするために、アプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **progress bar** 進行状況バー コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom progress bar drawing function. */

VOID my_progress_bar_draw(GX_PROGRESS_BAR *progress_bar)
{
    /* Call default progress bar background draw. */
    gx_progress_bar_background_draw(progress_bar);

    /* Call default progress bar text draw. */
    gx_progress_bar_text_draw(progress_bar);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_value_set

## <a name="gx_progress_bar_value_set"></a>gx_progress_bar_value_set


進行状況バーの現在の値を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_progress_bar_value_set(
    GX_PROGRESS_BAR *progress_bar,
    INT value);
```

### <a name="description"></a>説明

このサービスでは、進行状況バーの現在の値が割り当てられます。 進行状況バー ウィジェットは、進行状況バーの値が変更されると自動的に無効になり、それ自体が再描画されます。

### <a name="parameters"></a>パラメーター

- **progress_bar** 進行状況バー コントロール ブロック
- **value** 進行状況バーの現在の値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 進行状況バーの値が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
UINT status = gx_progress_bar_value_set(progress_bar, 50);

/* if status == GX_SUCCESS the progress bar value was successfully assigned. */
```

### <a name="see-also"></a>参照

- gx_progress_bar_value_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw

## <a name="gx_prompt_create"></a>gx_prompt_create


プロンプトを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_prompt_create(
    GX_PROMPT *prompt, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    GX_RESOURCE_ID text_id,
    ULONG style, 
    USHORT prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスでは、プロンプト ウィジェットが作成されます。

GX_PROMPT は GX_WIDGET から派生しており、すべての gx_widget API サービスがサポートされます。

### <a name="parameters"></a>パラメーター

- **pointer** 親ウィジェットを指します
- **text_id** プロンプト テキストのリソース ID
- **style** プロンプトのスタイル。 **付録 D** には、すべてのウィジェット用に事前に定義されている一般的なスタイルおよびウィジェット固有のスタイルが含まれています。
- **prompt_id** アプリケーション定義のプロンプト ID
- **size**: プロンプトの大きさ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) プロンプトの作成に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Create “my_prompt”. */
status = gx_prompt_create(&my_prompt, “my_promPt”, &my_parent,
                    MY_PROMPT_TEXT_RESOURCE_ID,
                    GX_STYLE_BORDER_RAISED, MY_PROPMT_ID, &size);

/* If status is GX_SUCCESS the prompt “my_prompt” has been created. */
```

### <a name="see-also"></a>参照

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_draw"></a>gx_prompt_draw


プロンプトを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_prompt_draw(GX_PROMPT *prompt);
```

### <a name="description"></a>説明

このサービスでは、プロンプト ウィジェットが描画されます。 このサービスは、キャンバスの更新中に GUIX によって内部的に呼び出されますが、カスタム描画関数によって呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **prompt** プロンプト ウィジェット コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom prompt drawing function. */

VOID my_prompt_draw(GX_PROMPT *prompt)
{
    /* Call default prompt draw. */
    gx_prompt_draw(prompt);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_event_process"></a>gx_prompt_event_process


プロンプトのイベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_prompt_event_process(GX_PROMPT *prompt, GX_EVENT *event_ptr);
```

### <a name="description"></a>説明

このサービスでは、指定されたプロンプトのイベントが処理されます。 このサービスは、カスタム プロンプトのイベント処理関数によって既定のイベント ハンドラーとして呼び出される必要があります。

### <a name="parameters"></a>パラメーター

- **prompt** プロンプト コントロール ブロックへのポインター
- **event_ptr** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) プロンプトのイベント処理に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Call generic prompt event processing as part of custom event processing function. */

UINT custom_prompt_event_process(GX_PROMPT *prompt, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default prompt event processing */
        status = gx_prompt_event_process(prompt, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>参照

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_font_set"></a>gx_prompt_font_set


プロンプトのフォントを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_prompt_font_set(
    GX_PROMPT *prompt, 
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>説明

このサービスでは、プロンプト ウィジェットのフォントが設定されます。

### <a name="parameters"></a>パラメーター

- **prompt** プロンプト ウィジェット コントロール ブロックへのポインター
- **font_id** フォントのリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) プロンプトのフォントの設定に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the font of “my_prompt”. */
status = gx_prompt_font_set(&my_prompt, MY_PROMPT_FONT_ID);

/* If status is GX_SUCCESS the font for prompt “my_prompt” has been set. */
```

### <a name="see-also"></a>参照

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_color_set"></a>gx_prompt_text_color_set


プロンプトのテキストの色を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_prompt_text_color_set(
    GX_PROMPT *prompt,
    GX_RESOURCE_ID normal_color,
    GX_RESOURCE_ID selected_color,
    GX_RESOURCE_ID disabled_color);
```

### <a name="description"></a>説明

このサービスでは、プロンプト ウィジェットのテキストの色を設定します。

### <a name="parameters"></a>パラメーター

- **prompt** プロンプト ウィジェット コントロール ブロックへのポインター
- **normal_color** 通常テキストの色のリソース ID。 **付録 A** には、事前定義された色のリソース ID が含まれています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。
- **selected_color** ウィジェットがフォーカスされたときに使用される、選択されているテキストの色のリソース ID。 **付録 A** には、事前定義された色のリソース ID が含まれています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。
- **disabled_color** GX_STYLE_ENABLED がアクティブではないときに使用される、無効なテキストの色のリソース ID。 **付録 A** には、事前定義された色のリソース ID が含まれています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) プロンプト テキストの色が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET_SIZE** (0X14) ウィジェットのサイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the text color of “my_prompt”. */
status = gx_prompt_text_color_set(&my_prompt,
                    GX_COLOR_ID_BLACK,
                    GX_COLOR_ID_LIGHTGRAY,
                    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS the text color for prompt “my_prompt” has been set. */
```

### <a name="see-also"></a>参照

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_draw"></a>gx_prompt_text_draw


描画サポート関数

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_prompt_text_draw(GX_PROMPT *prompt);
```

### <a name="description"></a>説明

このサポート関数では、プロンプトのテキスト部分を描画します。 この関数は gx_prompt_draw() によって内部的に呼び出され、カスタム プロンプトの描画関数を定義するアプリケーションの利便性向上のために、独立した API として提供されます。 プロンプトの背景描画をカスタマイズする必要があるアプリケーションでは、カスタムの描画関数を提供し、プロンプト テキストを背景に重ねて描画するためのカスタム描画の一部として gx_prompt_text_draw service サービスを呼び出すことができます。

### <a name="parameters"></a>パラメーター

- **prompt** プロンプト コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Define a custom drawing function */
VOID my_prompt_draw(GX_PROMPT *prompt)
{
    /* insert code here to draw prompt background */

    /* call support function to do text drawing */
    gx_prompt_text_draw();

    /* draw child widgets */
    gx_widget_children_draw((GX_WIDGET *) prompt);
}
```

### <a name="see-also"></a>参照

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_get"></a>gx_prompt_text_get


プロンプトのテキストを取得します (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_prompt_text_get(
    GX_PROMPT *prompt, 
    GX_CHAR **return_text);
```

### <a name="description"></a>説明

このサービスは非推奨です。gx_prompt_text_get_ext() を使用してください。

このサービスでは、プロンプト ウィジェットのテキストを取得します。

### <a name="parameters"></a>パラメーター

- **prompt** プロンプト ウィジェット コントロール ブロックへのポインター
- **return_text** テキストの宛先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) プロンプトのテキストが正常に取得されました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_PROMPT my_prompt;
GX_CHAR *my_prompt_text;

/* Get the text of “my_prompt”. */
status = gx_prompt_text_get(&my_prompt, &my_prompt_text);

/* If status is GX_SUCCESS the pointer “my_prompt_text” points to the text displayed by “my_prompt”. */
```

### <a name="see-also"></a>参照

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_get_ext"></a>gx_prompt_text_get_ext


プロンプトのテキストを取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_prompt_text_get(
    GX_PROMPT *prompt, 
    GX_STRING *return_string);
```

### <a name="description"></a>説明

このサービスでは、プロンプト ウィジェットの文字列を取得します。

### <a name="parameters"></a>パラメーター

- **prompt** プロンプト ウィジェット コントロール ブロックへのポインター
- **return_string** 文字列の宛先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) プロンプトのテキストが正常に取得されました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_PROMPT my_prompt;
GX_STRING my_prompt_string;

/* Get the text of “my_prompt”. */
status = gx_prompt_text_get_ext(&my_prompt, &my_prompt_string);

/* If status is GX_SUCCESS then my_prompt_string has been initialize to hold a copy of the prompt string. */
```

### <a name="see-also"></a>参照

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_id_set"></a>gx_prompt_text_id_set


プロンプト テキストID を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_prompt_text_id_set(
    GX_PROMPT *prompt, 
    GX_RESOURCE_ID string_id);
```

### <a name="description"></a>説明

このサービスでは、テキスト プロンプト ウィジェットの文字列 ID を設定します。

### <a name="parameters"></a>パラメーター

- **prompt** プロンプト ウィジェット コントロール ブロックへのポインター
- **string_id**: 文字列のリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) プロンプト テキスト ID が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_RESOURCE_ID** (0x33) リソース ID が無効です
- **GX_SYSTEM_MEMPRY_ERROR** (0x30) メモリ解放関数が定義されていません

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the string ID of “my_prompt”. */
status = gx_prompt_text_id_set(&my_prompt, MY_STRING_ID);

/* If status is GX_SUCCESS the text ID for prompt “my_prompt” has been set. */
```

### <a name="see-also"></a>参照

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_get
- gx_prompt_text_set

## <a name="gx_prompt_text_set"></a>gx_prompt_text_set


プロンプト テキストを設定します (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_prompt_text_set(
    GX_PROMPT *prompt, 
    GX_CHAR *text);
```

### <a name="description"></a>説明

このサービスは非推奨となりました。gx_prompt_text_set_ext() を使用してください。

このサービスでは、プロンプト ウィジェットのテキストを設定します。 プロンプト ウィジェットがスタイル GX_STYLE_TEXT_COPY で作成されたものである場合は、割り当てられたテキスト文字列のプライベート コピーがウィジェットによって作成されます。 GX_STYLE_TEXT_COPY がアクティブでない場合、ウィジェットでは受信文字列のプライベート コピーが作成されないため、文字列は静的またはグローバルに割り当てられる必要があります (つまり、自動または一時変数であってはなりません)。

GX_PROMPT は GX_WIDGET から派生しているため、すべての gx_widget API サービスを GX_PROMPT で使用できます。

### <a name="parameters"></a>パラメーター

- **prompt** プロンプト ウィジェット コントロール ブロックへのポインター
- **text** テキストへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) プロンプト テキストが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_SYSTEM_MEMORY_ERROR** (0x30) メモリ割り当て関数が定義されていません
- **GX_INVALID_STRING_LENGTH** (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the text of “my_prompt” to “my_text”. */
status = gx_prompt_text_set(&my_prompt, “my_text”);

/* If status is GX_SUCCESS the text for “my_prompt” has been set. */
```

### <a name="see-also"></a>参照

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_get

## <a name="gx_prompt_text_set_ext"></a>gx_prompt_text_set_ext

プロンプト テキストを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_prompt_text_set_ext(
    GX_PROMPT *prompt,
    GX_STRING *string);
```

### <a name="description"></a>説明

このサービスでは、プロンプト ウィジェットのテキストを設定します。 プロンプト ウィジェットがスタイル GX_STYLE_TEXT_COPY で作成されたものである場合は、割り当てられたテキスト文字列のプライベート コピーがウィジェットによって作成されます。 GX_STYLE_TEXT_COPY がアクティブでない場合、ウィジェットでは受信文字列のプライベート コピーが作成されないため、文字列は静的またはグローバルに割り当てられる必要があります (つまり、自動または一時変数であってはなりません)。

GX_PROMPT は GX_WIDGET から派生しているため、すべての gx_widget API サービスを GX_PROMPT で使用できます。

### <a name="parameters"></a>パラメーター

- **prompt** プロンプト ウィジェット コントロール ブロックへのポインター
- **text** テキストへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) プロンプト テキストが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_SYSTEM_MEMORY_ERROR** (0x30) メモリ割り当て関数が定義されていません
- **GX_INVALID_STRING_LENGTH** (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_STRING new_string;
new_string.gx_string_ptr = “my_text”;
new_string.gx_string_length = strlen(new_string.gx_string_ptr);

/* Set the text of “my_prompt” to “new_string”. */
status = gx_prompt_text_set(&my_prompt, &new_string);

/* If status is GX_SUCCESS the text for “my_prompt” has been set. */
```

### <a name="see-also"></a>参照

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_get

## <a name="gx_radial_progress_bar_anchor_set"></a>gx_radial_progress_bar_anchor_set


開始角度を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radial_progress_bar_anchor_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar, 
    GX_VALUE angle);
```

### <a name="description"></a>説明

このサービスでは、放射状進行状況バーの開始角度を設定します。

### <a name="parameters"></a>パラメーター

- **progress** bar 放射状進行状況バー コントロール ブロックへのポインター
- **angle** 円弧の開始角度

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) 放射状進行状況バーのアンカーが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_VALUE start_angle = 90;

/* Set the start angle of “my_progress_bar” to 90 degree. */
status = gx_radial_progress_bar_anchor_set(&my_progress_bar, start_angle);

/* If status is GX_SUCCESS the anchor value of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>参照

- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_background_draw"></a>gx_radial_progress_bar_background_draw


背景を描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_radial_progress_bar_background_draw(GX_RADIAL_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>説明

このサービスでは、放射状進行状況バーの背景を描画します。 このサービスは gx_radial_progress_bar_draw 関数によって内部的に参照されますが、アプリケーションによってカスタムの放射状進行状況バーの描画関数が定義される場合は、アプリケーションで使用するために公開されます。

### <a name="parameters"></a>パラメーター

- **progress bar** 放射状進行状況バー コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom radial progress bar drawing function. */

VOID my_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *radial_progress)
{
    /* Call default radial progress bar background draw. */
    gx_radial_progress_bar_background_draw(radial_progress);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radial_progress);
}
```
### <a name="see-also"></a>参照

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_create"></a>gx_radial_progress_bar_create


放射状進行状況バーを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radial_progress_bar_create(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RADIAL_PROGRESS_BAR_INFO *info,
    ULONG style
    USHORT id);
```

### <a name="description"></a>説明

このサービスでは、放射状進行状況バーを作成します。

ウィジェット スタイル GX_STYLE_ENABLED が進行状況バーに適用されている場合、進行状況バーでは pen_down、pen_drag、pen_up の各入力を受け取って、進行状況バーの現在値を変更します。

ウィジェット スタイル GX_STYLE_PROGRESS_TEXT_DRAW を使用すると、進行状況バー領域内にテキストとして進行状況バーの値を描画できます。 このスタイルがスタイル GX_STYLE_PROGRESS_PERCENT と組み合わせて使用されると、進行状況バーの値はパーセンテージとして表示されます。 それ以外の場合、進行状況バーの値は、現在の角度値として表示されます。

### <a name="parameters"></a>パラメーター

- **progress bar** 放射状進行状況バー コントロールへのポインター
- **progress** bar 放射状進行状況バー コントロール ブロックへのポインター
- **name** 放射状進行状況バーの名前
- **parent** 親ウィジェットへのポインター
- **info** GX_RADIAL_PROGRESS_BAR 構造体へのポインター。 **付録 I** には GX_RADIAL_PROGRESS_BAR 構造体の定義が含まれています。
- **style** 放射状進行状況バーのスタイル
- **id** 進行状況バーのアプリケーション定義 ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) 放射状進行状況バーが正常に作成されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットは既に作成されています
- **GX_INVALID_WIDGET** (0x12) 親ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_RAIDAL_PROGRESS_BAR_INFO info;

info.gx_radial_progress_bar_info_xcenter = 200;
info.gx_radial_progress_bar_info_ycenter = 200;
info.gx_radial_progress_bar_info_radius = 100;
info.gx_radial_progress_bar_info_current_angle = 180;
info.gx_radial_progress_bar_info_anchor_val = -180;
info.gx_radial_progress_bar_info_font_id = GX_FONT_ID_SYSTEM;
info.gx_raidal_progress_bar_info_normal_text_color =
                                        GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_selected_text_color =
                                        GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_disabled_text_color =
                                        GX_COLOR_ID_DISABLED_TEXT;
info.gx_radial_progress_bar_info_normal_brush_width = 20;
info.gx_raidal_progress_bar_info_selected_brush_width = 16;
info.gx_radial_progress_bar_info_normal_brush_color =
                                        GX_COLOR_ID_WIDGET_FILL;
info.gx_radial_progress_bar_info_selected_brush_color =
                                        GX_COLOR_ID_SELECTED_FILL;

/* Create a radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_create(&my_progress_bar,
                    “my_progress_bar”, parent, &info,
                    GX_STYLE_ENABLED | GX_STYLE_TRANSPARENT |
                    GX_STYLE_PROGRESS_TEXT_DRAW,
                    ID_MY_RADIAL_PROGRESS);

/* If status is GX_SUCCESS the radial progress bar “my_progress_bar” has been created. */
```

### <a name="see-also"></a>参照

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_draw"></a>gx_radial_progress_bar_draw


放射状進行状況バーを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>説明

このサービスでは、放射状進行状況バーを描画します。 このサービスは gx_radial_progress_bar_create 関数によって内部的に参照されますが、アプリケーションによってカスタムの放射状進行状況バーの描画関数が定義される場合は、アプリケーションで使用するために公開されます。

### <a name="parameters"></a>パラメーター

- **progress bar** 放射状進行状況バー コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom radial progress bar drawing function. */

VOID my_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *radial_progress)
{
    /* Call default radial progress bar draw. */
    gx_radial_progress_bar_draw(radial_progress);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radial_progress);
}
```

### <a name="see-also"></a>参照

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_size_calculate
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_event_process"></a>gx_radial_progress_bar_event_process


放射状進行状況バーのイベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radial_progress_bar_event_process(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>説明

このサービスでは、放射状進行状況バーのイベントを処理します。 この関数は gx_radial_progress_bar_create 関数によって内部的に参照されますが、アプリケーションによってカスタムの放射状進行状況イベント処理関数が定義される場合にアプリケーションで使用するために公開されます。

### <a name="parameters"></a>パラメーター

- **progress** bar 放射状進行状況バー コントロール ブロックへのポインター
- **event_ptr** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) 放射状進行状況バーのイベントが正常に処理されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Write a custom event processing function. */

UINT my_event_process (GX_RADIAL_PROGRESS_BAR *radial_progress, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
        case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_radial_progress_bar_event_process(
                            radial_progress, event_ptr);
        /* add my own handling here */
        break;
    default:
        status = gx_radial_progress_bar_event_process(
                            radial_progress, event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>参照

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_font_set"></a>gx_radial_progress_bar_font_set


放射状進行状況バーのフォントを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radial_progress_bar_font_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>説明

このサービスでは、放射状進行状況バー ウィジェットのフォントを設定します。 ウィジェット スタイル GX_STYLE_PROGRESS_TEXT_DRAW が設定されていない場合、このパラメーターは無効です。

### <a name="parameters"></a>パラメーター

- **progress** bar 放射状進行状況バー コントロール ブロックへのポインター
- **font_id** フォントのリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) 放射状進行状況バーのフォントが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set font for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_font_set(&my_progress_bar, font);

/* If status is GX_SUCCESS the font of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>参照

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_info_set"></a>gx_radial_progress_bar_info_set


放射状進行状況バーの情報を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radial_progress_bar_info_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RADIAL_PROGRESS_BAR_INFO *info);
```

### <a name="description"></a>説明

このサービスでは、放射状進行状況バーに割り当てられた情報パラメーターをリセットします。

### <a name="parameters"></a>パラメーター

- **progress** bar 放射状進行状況バー コントロール ブロックへのポインター
- **info** 放射状進行状況バーの情報構造体へのポインター。 **付録 I** には GX_RADIAL_PROGRESS_BAR_INFO 構造体の定義が含まれています。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) 放射状進行状況バーの情報が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_RAIDAL_PROGRESS_BAR_INFO info;

info.gx_radial_progress_bar_info_xcenter = 200;
info.gx_radial_progress_bar_info_ycenter = 200;
info.gx_radial_progress_bar_info_radius = 100;
info.gx_radial_progress_bar_info_current_angle = 180;
info.gx_radial_progress_bar_info_anchor_val = -180;
info.gx_radial_progress_bar_info_font_id = GX_FONT_ID_SYSTEM;
info.gx_raidal_progress_bar_info_normal_text_color =
                                GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_selected_text_color =
                                GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_disabled_text_color =
                                GX_COLOR_ID_DISABLED_TEXT;
info.gx_radial_progress_bar_info_normal_brush_width = 20;
info.gx_raidal_progress_bar_info_selected_brush_width = 16;
info.gx_radial_progress_bar_info_normal_brush_color =
                                GX_COLOR_ID_WIDGET_FILL;
info.gx_radial_progress_bar_info_selected_brush_color =
                                GX_COLOR_ID_SELECTED_FILL;

/* Set appearance information for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_info_set(&my_progress_bar, &info);

/* If status is GX_SUCCESS the appearance information of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>参照

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_text_color_set"></a>gx_radial_progress_bar_text_color_set


放射状進行状況バーのテキストの色を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radial_progress_bar_text_color_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCE_ID disabled_text_color);
```

### <a name="description"></a>説明

このサービスでは、進行状況バーのテキストの色を設定します。 この値は、スタイル GX_STYLE_PROGRESS_TEXT_DRAW が設定されている場合にのみ使用されます。

### <a name="parameters"></a>パラメーター

- **progress** bar 放射状進行状況バー コントロール ブロックへのポインター
- **normal_color** 通常状態のテキストの色のリソース ID。 **付録 A** には、事前定義された色のリソース ID が含まれています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。
- **selected_color_id** ウィジェットがフォーカスされたときのテキストの色のリソース ID。 **付録 A** には、事前定義された色のリソース ID が含まれています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。
- **disabled_color** スタイル GX_STYLE_ENABLED が設定されていない場合の、テキストの色のリソース ID。 **付録 A** には、事前定義された色のリソース ID が含まれています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 放射状進行状況バーのテキストの色が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェット チェックが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set text color for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_text_color_set(&my_progress_bar,
                            GX_COLOR_ID_NORMAL_TEXT,
                            GX_COLOR_ID_SELECTED_TEXT,
                            GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS the text color of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>参照

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_text_draw"></a>gx_radial_progress_bar_text_draw


放射状進行状況バーのテキストを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_radial_progress_bar_text_draw(GX_RADIAL_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>説明

このサービスでは、指定された放射状進行状況バーのテキストを描画します。 この関数は gx_radial_progress_bar_draw() の一部として内部的に呼び出されますが、アプリケーションによってカスタムの進行状況バー描画関数が定義されるケースをサポートするために、アプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **progress bar** 放射状進行状況バー コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Draw text for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_text_draw (&my_progress_bar);

/* If status is GX_SUCCESS the text of “my_progress_bar” has been drawn. */

/* Write a custom radial progress bar drawing function. */
VOID my_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *radial_progress)
{
    /* Add your own background draw here. */

    /* Call default radial progress bar text draw. */
    gx_radial_progress_bar_text_draw(radial_progress);

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radial_progress);
}
```

### <a name="see-also"></a>参照

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_value_set"></a>gx_radial_progress_bar_value_set


放射状進行状況バーの値を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radial_progress_bar_value_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar, 
    GX_VALUE value);
```

### <a name="description"></a>説明

このサービスでは、放射状進行状況バーの値を設定します。 割り当てられる値は、[-360, 360] の範囲に制限され、進行状況バーの現在の場所で可能な角度値の範囲を定義します。 アプリケーションでは、示されている実際の値をスケーリングして、進行状況バー ウィジェットに角度値を割り当てる必要があります。

進行状況バーは、現在値がアンカー位置と上部円弧の端点間の角度差を示すように描画されます。負の値を指定すると、アンカー位置から時計回りの方向に円弧が描画されます。 正の現在値を指定すると、アンカー位置から反時計回りに円弧が描画されます。

たとえば、円弧の最上部 (12 時の位置) から開始し、右 (3 時の位置) で終わる円弧を描画するには、アンカー値 90 度と、現在値 -90 度を割り当てます。

### <a name="parameters"></a>パラメーター

- **progress** bar 放射状進行状況バー コントロール ブロックへのポインター
- **value** 新しい進行状況バーの値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) 放射状進行状況バーの値が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **NX_PTR_ERROR** (0x07) ポインターが無効です。
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_VALUE new_value = 180;

/* Set value for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_value_set(&my_progress_bar,
                                        new_value);

/* If status is GX_SUCCESS the value of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>参照

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw

## <a name="gx_radio_button_create"></a>gx_radio_button_create


ラジオ ボタンを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radio_button_create(
    GX_RADIO_BUTTON *button,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id, ULONG style,
    USHORT radio_button_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスでは、ラジオ ボタン ウィジェットを作成します。 GX_RADIO_BUTTON は GX_TEXT_BUTTON から派生しているため、すべての gx_text_button サービスもこのウィジェットの種類でサポートされます。

### <a name="parameters"></a>パラメーター

- **button** ラジオ ボタン コントロール ブロックへのポインター
- **name** ラジオ ボタン ウィジェットの論理名
- **parent** 親ウィジェットへのポインター
- **text_id** ラジオ ボタンのリソース ID
- **style** ラジオ ボタンのスタイル。 **付録 D** には、すべてのウィジェット用に事前に定義されている一般的なスタイルと、ウィジェット固有のスタイルが含まれています。
- **radio_button_id** ラジオ ボタンのアプリケーション定義 ID
- **size** ラジオ ボタンの大きさ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ラジオ ボタンが正常に作成されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットは既に作成されています
- **GX_INVALID_** SIZE (0x19) ウィジェット コントロール ブロックのサイズが無効です
- **GX_INVALID_RESOURCE_ID** (0x33) リソース ID が無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Create “my_radio_button”. */
status = gx_radio_button_create(&my_radio_button, “my_radio_button”, &my_parent,
                    MY_RADIO_BUTTON_TEXT_RESOURCE_ID,
                    GX_STYLE_BORDER_RAISED, MY_RADIO_BUTTON_ID, &size);

/* If status is GX_SUCCESS the radio button “my_radio_button” has been created. */
```
### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw
- gx_radio_button_draw

## <a name="gx_radio_button_draw"></a>gx_radio_button_draw


ラジオ ボタンを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_radio_button_draw(GX_RADIO_BUTTON *button);
```

### <a name="description"></a>説明

このサービスでは、ラジオ ボタン ウィジェットを描画します。 このサービスは、GUIX キャンバスの更新によって内部的に呼び出されますが、オーバーライドされた描画関数によって呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **button** ラジオ ボタン ウィジェット コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom radio button drawing function. */

VOID my_radio_button_draw(GX_RADIO_BUTTON *radio_button)
{
    /* Call default radio button draw. */
    gx_radio_button_draw(radio_button);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radio_button);
}
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw
- gx_radio_button_create

## <a name="gx_radio_button_pixelmap_set"></a>gx_radio_button_pixelmap_set


ラジオ ボタンのピクセルマップを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radio_button_pixelmap_set(
    GX_RADIO_BUTTON *button,
    GX_RESOURCE_ID off_id,
    GX_RESOURCE_ID on_id,
    GX_RESOURCE_ID off_disabled_id,
    GX_RESOURCE_ID on_disabled_id);
```

### <a name="description"></a>説明

このサービスでは、ボタンの状態ごとに、指定されたラジオ ボタンによって表示されるピクセルマップを割り当てます。 リソース ID は重複してかまいません。

### <a name="parameters"></a>パラメーター

- **off_id** ラジオ ボタンのオフ状態に使用されるピクセルマップ
- **off_id** ラジオ ボタンのオン状態に使用されるピクセルマップ
- **off_disabled_id** 無効またはオフの状態のラジオ ボタンに使用されるピクセルマップ
- **off_disabled_id** 無効またはオンの状態のラジオ ボタンに使用されるピクセルマップ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ラジオ ボタンが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set pixelmap for “my_radio_button”. */
status = gx_radio_button_pixelmap_set(&my_radio_button,
                                MY_OFF_PIXELMAP,
                                MY_ON_PIXELMAP,
                                MY_OFF_DISABLED_PIXELMAP,
                                MY_ON_DISABLED_PIXELMAP);

/* If status is GX_SUCCESS the pixelmaps for radio button “my_radio_button” has been set. */
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw
- gx_radio_button_create

## <a name="gx_radial_slider_anchor_angles_set"></a>gx_radial_slider_anchor_angles_set


放射状スライダーのアンカー一覧を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radial_slider_anchor_angles_set(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE *anchor_angles, 
    USHORT anchor_count);
```

### <a name="description"></a>説明

このサービスでは、放射状スライダーのアンカー角度を設定します。 アンカー角度一覧が設定されている場合、放射状スライダーの角度は、定義済みアンカー角度のいずれかになります。

### <a name="parameters"></a>パラメーター

- **slider** 放射状スライダー コントロール ブロック
- **anchor_angles** 設定する角度一覧
- **anchor_count** アンカー角度の数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) アンカー角度が正常に設定されました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE** (0x22) アンカー一覧が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_VALUE anchor_angles[]={0, 30, 60, 90, 120, 150, 180};
USHORT anchor_count = 7;

/* Set anchor angles for radial slider. */
status = gx_radial_slider_anchor_angles_set(&my_radial_slider,
                                anchor_angles, anchor_count);

/* If status is GX_SUCCESS the anchor angles have been set for “my_radial_slider”. */

/* Set anchor angles for radial slider. */
status = gx_radial_slider_anchor_angles_set(&my_radial_slider,
                                GX_NULL, 0);

/* If status is GX_SUCCESS the anchor angles have been removed from “my_radial_slider”. */
```

### <a name="see-also"></a>参照

- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_angle_set"></a>gx_radial_slider_angle_set

放射状スライダーの角度を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radial_slider_angle_set(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE new_angle);
```

### <a name="description"></a>説明

このサービスでは、放射状スライダーの新しい角度値を設定します。

### <a name="parameters"></a>パラメーター

- **slider** 放射状スライダー コントロール ブロックへのポインター
- **new_angle** 設定する新しい角度値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) 放射状スライダーの角度が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set “my_radial_slider” angle to 0 degree(3 o’clock position). */
status = gx_radial_slider_angle_set(&my_radial_slider, 0);

/* If status is GX_SUCCESS the value of “my_radial_slider” has been set to 0 degree. */
```

### <a name="see-also"></a>参照

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_animation_set"></a>gx_radial_slider_animation_set


放射状スライダーのアニメーション情報を作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radial_slider_animation_set(
    GX_RADIAL_SLIDER *slider,
    USHORT steps, USHORT delay, 
    USHORT animation_style,
    VOID (*animation_update_callback)(GX_RADIAL_SLIDER *slider));
```

### <a name="description"></a>説明

このサービスでは、放射状スライダーの針のアニメーションについて、アニメーションのステップ、遅延時間、およびアニメーション スタイルを設定します。

### <a name="parameters"></a>パラメーター

- **slider** 放射状スライダー コントロール ブロックへのポインター
- **steps** 1 つのアニメーションの合計ステップ
- **delay** 各アニメーション ステップの遅延時間
- **animation_style** イージング関数の種類。次のものが含まれます。
  - GX_ANIMATION_BACK_EASE_IN
  - GX_ANIMATION_BACK_EASE_OUT
  - GX_ANIMATION_BACK_EASE_IN_OUT
  - GX_ANIMATION_BOUNCE_EASE_IN
  - GX_ANIMATION_BOUNCE_EASE_OUT
  - GX_ANIMATION_BOUNCE_EASE_IN_OUT
  - GX_ANIMATION_CIRC_EASE_IN
  - GX_ANIMATION_CIRC_EASE_OUT
  - GX_ANIMATION_CIRC_EASE_IN_OUT
  - GX_ANIMATION_CUBIC_EASE_IN
  - GX_ANIMATION_CUBIC_EASE_OUT
  - GX_ANIMATION_CUBIC_EASE_IN_OUT
  - GX_ANIMATION_ELASTIC_EASE_IN
  - GX_ANIMATION_ELASTIC_EASE_OUT
  - GX_ANIMATION_ELASTIC_EASE_IN_OUT
  - GX_ANIMATION_EXPO_EASE_IN
  - GX_ANIMATION_EXPO_EASE_OUT
  - GX_ANIMATION_EXPO_EASE_IN_OUT
  - GX_ANIMATION_QUAD_EASE_IN
  - GX_ANIMATION_QUAD_EASE_OUT
  - GX_ANIMATION_QUAD_EASE_IN_OUT
  - GX_ANIMATION_QUART_EASE_IN
  - GX_ANIMATION_QUART_EASE_OUT
  - GX_ANIMATION_QUART_EASE_IN_OUT
  - GX_ANIMATION_QUINT_EASE_IN
  - GX_ANIMATION_QUINT_EASE_OUT
  - GX_ANIMATION_QUINT_EASE_IN_OUT
  - GX_ANIMATION_SINE_EASE_IN
  - GX_ANIMATION_SINE_EASE_OUT
  - GX_ANIMATION_SINE_EASE_IN_OUT
- **animation_update_callback** 各アニメーション ステップの後に呼び出されるユーザー定義のコールバック関数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) 放射状スライダーのアニメーションが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
VOID animation_callback(GX_RADIAL_SLIDER *slider)
{
    /* This function will be called after each animation step,
    add custom code here. */
}

/* Set animation info for “my_radial_slider”. */
status = gx_radial_slider_animation_set(&my_radial_slider, 15, 2,
                                GX_ANIMATION_CIRC_EASE_IN_OUT,
                                animation_callback);

/* If status is GX_SUCCESS the radial slider needle will move with specified animation. */

/* Disable animation for “my_radial_slider”. */
status = gx_radial_slider_animation_set(&my_radial_slider, 0, 0,
                                        0, 0);

/* If status is GX_SUCCESS the radial slider needle will move without animation. */
```

### <a name="see-also"></a>参照

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_animation_start"></a>gx_radial_slider_animation_start


新しい放射状スライダー値をアニメーションを使用して設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radial_slider_animation_start(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE target_angle);
```

### <a name="description"></a>説明

このサービスでは、スライダーの針を現在の位置から指定した位置に動かすアニメーションを開始します。

### <a name="parameters"></a>パラメーター

- **slider** 放射状スライダー コントロール ブロックへのポインター
- **target_angle** 目標角度の値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 放射状スライダーのアニメーションが正常に開始されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Start an animation to move radial slider needle from
current position to 90 degree position. */
status = gx_radial_slider_animation_start(&my_radial_slider, 90);

/* If status is GX_SUCCESS the radial slider needle animation has been started. */
```

### <a name="see-also"></a>参照

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_create"></a>gx_radial_slider_create


放射状スライダーの作成

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radial_slider_create(
    GX_RADIAL_SLIDER *slider,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RADIAL_SLIDER_INFO *info,
    ULONG style,
    USHORT slider_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスにより、放射状スライダー ウィジェットが作成されます。

### <a name="parameters"></a>パラメーター

- **slider** 放射状スライダー コントロール ブロックへのポインター
- **name** 放射状スライダー ウィジェットの論理名
- **parent** 親ウィジェットへのポインター
- **info** 放射状スライダーの外観の定義。**付録 I** には GX_RADIAL_SLIDER_INFO の定義が含まれています。
- **style** ラジオ ボタンのスタイル。 **付録 D** には、すべてのウィジェット用に事前に定義されている一般的なスタイルおよびウィジェット固有のスタイルが含まれています。
- **radio_button_id** 放射状スライダーのアプリケーション定義 ID
- **size** 放射状スライダーの大きさ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 放射状スライダーが正常に作成されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットは既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です
- **GX_INVALID_WIDGET** (0x12) 親ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_RADIAL_SLIDER_INFO info;
GX_RECTANGLE size;

/* Distance from left side of widget to rotating center. */
info.gx_radial_slider_info_xcenter = 100;

/* Distance from top size of widget to rotating center. */
info.gx_radial_slider_info_ycenter = 100;

/* Radius of rotating circle. */
info.gx_radial_slider_info_radius = 100;

/* Widget of rotating track. */
info.gx_radial_slider_info_track_width = 40;

/* Current angle value. */
info.gx_radial_slider_info_current_angle = 0;

/* Minimum angle value. */
info.gx_radial_slider_min_anlge = -60;

/* Maximum angle value. */
info.gx_radial_slider_max_angle = 240;

/* Anchor value list. */
info.gx_radial_slider_angle_list = GX_NULL;

/* Anchor value count. */
info.gx_radial_slider_list_count = 0;

/* Resource ID of background pixelmap. */
info.gx_radial_slider_background_pixelmap = GX_PIXELMAP_ID_BKGRD;

/* Resource ID of needle pixelmap. */
info.gx_radial_slider_needle_pixelmap = GX_PIXELMAP_ID_NEEDLE;

/* Define widget size. */
gx_utility_rectangle_define(&size, 0, 0, 200, 200);

/* Create “my_radial_slider”. */
status = gx_radial_slider_create(&my_radial_slider,
                                “my_radial_slider”, &my_parent,
                                &info, GX_STYLE_ENABLED,
                                MY_RADIAL_SLIDER_ID, &size);

/* If status is GX_SUCCESS the radial slider “my_radial_slider” has been created. */
```

### <a name="see-also"></a>参照

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_draw"></a>gx_radial_slider_draw


放射状スライダーの描画

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_radial_slider_draw(GX_RADIAL_SLIDER *slider);
```

### <a name="description"></a>説明

このサービスは放射状スライダーを描画します。 このサービスは、GUIX キャンバスの更新によって内部的に呼び出されますが、オーバーライドされた描画関数によって呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **slider** 放射状スライダー コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom radio button drawing function. */

VOID my_radial_slider_draw(GX_RADIAL_SLIDER *radial_slider)
{
    /* Call default radial slider draw. */
    gx_radio_slider_draw(radial_slider);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_event_process"></a>gx_radial_slider_event_process


放射状スライダー イベントの処理

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radial_slider_event_process(
    GX_RADIAL_SLIDER *slider,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>説明

このサービスにより、放射状スライダー イベントが処理されます。 このサービスは、カスタム放射状スライダーのイベント処理関数によって既定のイベント ハンドラーとして呼び出される必要があります。

### <a name="parameters"></a>パラメーター

- **slider** 放射状スライダー コントロール ブロックへのポインター
- **event_ptr** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 放射状スライダーのイベントが正常に処理されしました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Write a custom event processing function. */

UINT my_event_process(GX_RADIAL_SLIDER *slider,
                    GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_radial_slider_event_process(slider, event_ptr);

        /* add my own handling here */
        break;
    default:
        status = gx_radial_slider_event_process(slider, event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>参照

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_info_get"></a>gx_radial_slider_info_get


放射状スライダー情報の取得

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radial_slider_info_get(
    GX_RADIAL_SLIDER *slider,
    GX_RADIAL_SLIDER_INFO **info);
```

### <a name="description"></a>説明

このサービスは、放射状スライダー情報のポインターを取得します。

### <a name="parameters"></a>パラメーター

- **slider** 放射状スライダー コントロール ブロックへのポインター
- **info** 取得した放射状スライダー情報のポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 放射状スライダー情報が正常に取得されました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_RADIAL_SLIDER_INFO *info;

/* Retrive radial slider information structure. */
status = gx_radial_slider_info_get(&my_radial_slider,
                                    “my_radial_slider”, &info);

/* If status is GX_SUCCESS the radial slider information pointer of “my_radial_slider” has been retrieved. */
```

### <a name="see-also"></a>参照

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_info_set"></a>gx_radial_slider_info_set


放射状スライダー情報の設定

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radial_slider_info_set(
    GX_RADIAL_SLIDER *slider,
    GX_RADIAL_SLIDER_INFO *info);
```

### <a name="description"></a>説明

このサービスは、放射状スライダーの情報を設定します。

### <a name="parameters"></a>パラメーター

- **slider** 放射状スライダー コントロール ブロックへのポインター
- **info** 設定する放射状スライダー情報

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 放射状スライダー情報が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_RADIAL_SLIDER_INFO info;

/* Distance from left side of widget to rotating center. */
info.gx_radial_slider_info_xcenter = 100;

/* Distance from top size of widget to rotating center. */
info.gx_radial_slider_info_ycenter = 100;

/* Radius of rotating circle. */
info.gx_radial_slider_info_radius = 100;

/* Widget of rotating track. */
info.gx_radial_slider_info_track_width = 40;

/* Current angle value. */
info.gx_radial_slider_info_current_angle = 0;

/* Minimum angle value. */
info.gx_radial_slider_min_anlge = -60;

/* Maximum angle value. */
info.gx_radial_slider_max_angle = 240;

/* Anchor value list. */
info.gx_radial_slider_angle_list = GX_NULL;

/* Anchor value count. */
info.gx_radial_slider_list_count = 0;

/* Resource ID of background pixelmap. */
info.gx_radial_slider_background_pixelmap = GX_PIXELMAP_ID_BKGRD;

/* Resource ID of needle pixelmap. */
info.gx_radial_slider_needle_pixelmap = GX_PIXELMAP_ID_NEEDLE;

/* Reset radial slider info for “my_radial_slider”. */
status = gx_radial_slider_info_set(&my_radial_slider, &info);

/* If status is GX_SUCCESS the radial slider info of “my_radial_slider” has been reset. */
```

### <a name="see-also"></a>参照

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_pixelmap_set"></a>gx_radial_slider_pixelmap_set


放射状スライダーのピクセルマップを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_radial_slider_pixelmap_set(
    GX_RADIAL_SLIDER *slider,
    GX_RESOURCE_ID background_pixemap,
    GX_REOUSRCE_ID needle_pixelmap);
```

### <a name="description"></a>説明

このサービスは、放射状スライダーの背景と針のピクセルマップを設定します。

### <a name="parameters"></a>パラメーター

- **slider** 放射状スライダー コントロール ブロックへのポインター
- **background_pixelmap** バックグラウンド ピクセルマップのリソース ID
- **needle_pixelmap** ニードル ピクセルマップのリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 放射状スライダー ピクセルマップが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Create “my_radio_button”. */
status = gx_radial_slider_pixelmap_set(&my_radial_slider, GX_PIXELMAP_ID_BG, GX_PIXELMAP_ID_NEEDLE);

/* If status is GX_SUCCESS the background and needle pixelmap of “my_radial_slider” has been reset. */
```

### <a name="see-also"></a>参照

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set

## <a name="gx_rich_text_view_create"></a>gx_rich_text_view_create

リッチ テキスト ビューを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_rich_text_view_create(
    GX_RICH_TEXT_VIEW *text_view,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    GX_RICH_TEXT_FONTS *fonts,
    USHORT id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスは、指定に従ってリッチ テキスト ビューを作成します。


**書式設定タグは、特殊な種類のテキストを表示するために使用されます。**

- **\<b>\</b>** ユーザー指定の太字フォント ID を使用してテキストを設定します
- **\<i>\</i>** ユーザー指定の斜体フォント ID を使用してテキストを設定します
- **\<u>\</u>** テキストの下線を有効にします
- **\<f GX_FONT_ID>\</f>** 指定されたフォント ID でテキスト フォントを設定します
- **\<c GX_COLOR_ID>\</c>** 指定された色 ID でテキスト フォントを設定します
- **\<hc GX_COLOR_ID>\</hc>** 指定された色 ID でテキストの強調表示の色を設定します
- **\<align left/right/center>\</align>** テキストトの配置を設定します

**書式設定タグの使用例:**

- \<b>これは太字テキストストです<\b>
- \<i>これは斜体テキストストです<\i>
- \<u>これは下線が引かれたテキストです<\u>
- \<f 0>このテキスト フォント ID は、0 に設定されています<\f>
- \<c 1>このテキストの色 ID は、1 に設定されています<\c>
- \<hc 2>このテキスト強調表示の色 ID は、2 に設定されています<\hc>
- \<align left>このテキストは左揃えになっています<\align>

### <a name="parameters"></a>パラメーター

- **text_view** リッチ テキスト ビュー コントロール ブロックへのポインター
- **name** リッチ テキスト ビューの名前
- **parent** 親ウィジェットへのポインター
- **text_id** テキスト文字列のリソース ID
- **fonts** リッチ テキスト ビューのフォント情報へのポインター。 **Apendix I** に GX_RICH_TEXT_FONTS 構造体についての定義が含まれています。
- **style** ウィジェットのスタイル。 **付録 D** には、ウィジェット固有のスタイルだけでなく、すべてのウィジェット用に事前に定義されている一般的なスタイルが含まれています。
- **id** リッチ テキスト ビューのアプリケーション定義 ID
- **size** リッチ テキスト ビューのサイズ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) リッチ テキスト ビューが正常に作成されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_RICH_TEXT_VIEW rich_view;
GX_RCIH_TEXT_FONTS fonts;
GX_RECTANGLE size;

/* Defined widget size. */
gx_utility_rectangle_define(&size, 100, 100, 300, 150);

/* Define font information. */
fonts.gx_rich_text_fonts_normal_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_italic_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_italic_id = GX_FONT_ID_SYSTEM;

/* Create rich text view widget. */
status = gx_rich_text_view_create(&rich_view, “my_rich_view”,
                                  parent, GX_STRING_ID_TEST_STRING,
                                  &fonts,
                                  GX_STYLE_ENABLED,
                                  MY_RICH_VIEW_ID, &size);

/* If status is GX_SUCCESS the rich text view was successfully created. */

```

GUIX Studio のインストールの一部として提供されているデモ アプリケーション demo_guix_widget_types には、リッチ テキスト ビュー ウィジェットの使用の完全な例が用意されています。

### <a name="see-also"></a>参照

- gx_rich_text_view_draw
- gx_rich_text_view_fonts_set
- gx_rich_text_view_text_draw

## <a name="gx_rich_text_view_draw"></a>gx_rich_text_view_draw


リッチ テキスト ビューを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_rich_text_view_draw(GX_RICH_TEXT_VIEW *text_view);
```

### <a name="description"></a>説明

このサービスは、指定されたリッチ テキスト ビュー ウィジェットを描画します。 このサービスは通常、キャンバスの更新操作の一部として GUIX によって内部的に呼び出されますが、カスタム描画関数を提供し、カスタム描画ベースとして既定のリッチ テキスト ビュー描画を呼び出す必要があるアプリケーションにも公開されます。

### <a name="parameters"></a>パラメーター

- **text_view** リッチ テキスト ビュー ウィジェット コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom rich text view drawing function. */

VOID my_rich_text_view_draw(GX_RICH_TEXT_VIEW *text_view)
{
    /* Call default rich text view draw. */
    gx_rich_text_view_draw(text_view);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_rich_text_view_create
- gx_rich_text_view_fonts_set
- gx_rich_text_view_text_draw

## <a name="gx_rich_text_view_fonts_set"></a>gx_rich_text_view_fonts_set

リッチ テキスト ビューのフォントを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_rich_text_view_fonts_set(GX_RICH_TEXT_VIEW *text_view, GX_RICH_TEXT_FONTS *fonts);
```

### <a name="description"></a>説明

このサービスは、リッチ テキスト ビュー ウィジェットのフォントを設定します。

### <a name="parameters"></a>パラメーター

- **text_view** リッチ テキスト ビュー ウィジェット コントロール ブロックへのポインター
- **fonts** リッチ テキスト ビューのフォント情報へのポインター。 **Apendix I** に GX_RICH_TEXT_FONTS 構造体構造体についての定義が含まれています。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) リッチ テキスト ビューのフォントが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_RICH_TEXT_FONTS fonts;

/* Replace the font ids as needed. */
fonts.gx_rich_text_fonts_normal_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_italic_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_italic_id = GX_FONT_ID_SYSTEM;

/* Set the font of “my_rich_view”. */
status = gx_rich_text_view_fonts_set(&my_rich_view, &fonts);

/* If status is GX_SUCCESS the font for rich text view “my_rich_view” has been set. */
```

### <a name="see-also"></a>参照

- gx_rich_text_view_create
- gx_rich_text_view_draw
- gx_rich_text_view_text_draw

## <a name="gx_rich_text_view_text_draw"></a>gx_rich_text_view_text_draw


リッチ テキスト ビューのテキストを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_rich_text_view_text_draw(GX_RICH_TEXT_VIEW *text_view);
```

### <a name="description"></a>説明

このサポート関数は、リッチ テキスト ビューのテキスト部分を描画します。 この関数は gx_rich_text_view_draw() によって内部的に呼び出され、カスタム リッチ テキスト ビュー描画関数を定義するアプリケーションの利便性向上のために、独立した API として提供されます。 リッチ テキスト ビューの背景描画をカスタマイズする必要があるアプリケーションは、そのカスタム描画関数を提供し、リッチ テキスト ビュー テキストを背景に重ねて描画するためのカスタム描画の一部として gx_rich_text_view_text_draw サービスを呼び出すことができます。

### <a name="parameters"></a>パラメーター

- **text_view** リッチ テキスト ビュー ウィジェット コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom rich text view drawing function. */

VOID my_rich_text_view_draw(GX_RICH_TEXT_VIEW *text_view)
{
    /* Insert code here to draw rich text view background. */

    /* Call support function to do text drawing. */
    gx_rich_text_view_text_draw();

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *) rich_text_view);
}
```

### <a name="see-also"></a>参照

- gx_rich_text_view_create
- gx_rich_text_view_draw
- gx_rich_text_view_fonts_set

## <a name="gx_screen_stack_create"></a>gx_screen_stack_create


スクリーン スタックを初期化します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_screen_stack_create(
    GX_SCREEN_STACK_CONTROL *control,
    GX_WIDGET **memory_buffer, 
    INT buffer_size);
```

### <a name="description"></a>説明

このサービスは、スクリーン スタックを初期化します。 アプリケーションでは、スクリーン スタック機能を実装するために使用されるメモリ ブロックとバッファー サイズを定義する必要があります。

> [!NOTE]
> "*この API は古くなっており、gx_system_screen_stack_create () に置き換えられています。このバージョンは、以前のライブラリ リリースとの下位互換性の確保のためにのみ提供されています。* "

### <a name="parameters"></a>パラメーター

- **control** スクリーン スタック コントロール ブロック
- **memory_buffer** スクリーン スタックとして使用されるメモリ バッファーへのポインター
- **buffer_size** メモリ サイズ (バイト単位)

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) スクリーン スタックが正常に作成されました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_VALUE** (0x22) バッファー サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
#define SCREEN_STACK_SIZE 10

GX_SCREEN_STACK_CONTROL my_stack_control;
GX_WIDGET *screen_stack[SCREEN_STACK_SIZE];

/* Initialize “my_stack_control”. */
status = gx_screen_stack_create(&my_stack_control, screen_stack,
                        SCREEN_STACK_SIZE * sizeof(GX_WIDGET *));

/* If status is GX_SUCCESS the screen control block “my_stack control” has been initialized. */
```

### <a name="see-also"></a>参照

- gx_screen_stack_push
- gx_screen_stack_pop
- gx_screen_stack_reset

## <a name="gx_screen_stack_pop"></a>gx_screen_stack_pop


スクリーン スタックから最上位のエントリを削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_screen_stack_pop(GX_SCREEN_STACK_CONTROL *control);
```

### <a name="description"></a>説明

このサービスは、スクリーン スタックから最上位のエントリを削除し、ポップしたスクリーンを前の親にアタッチします。 また、この API は、親から既存の子をすべてデタッチします。

> [!NOTE]
> *この API は古くなっており、gx_system_screen_stack_pop() に置き換えられています。このバージョンは、以前のライブラリ リリースとの下位互換性の確保のためにのみ提供されています。*

### <a name="parameters"></a>パラメーター

- **control** スクリーン スタック コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) スクリーン スタックが正常にポップされました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Remove the topmost entry from the screen stack. */
status = gx_screen_stack_pop(&my_stack_control);

/* If status is GX_SUCCESS the topmost entry has been removed from the screen stack, 
    and the popped screen has been attached to its parent. */
```

### <a name="see-also"></a>参照

- gx_screen_stack_create
- gx_screen_stack_push
- gx_screen_stack_reset

## <a name="gx_screen_stack_push"></a>gx_screen_stack_push


スクリーンとその親をスタックにプッシュします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_screen_stack_push(
    GX_SCREEN_STACK_CONTROL *control,
    GX_WIDGET *screen,
    GX_WIDGET *new_screen);
```

### <a name="description"></a>説明

このサービスは、スクリーンを親から切り離し、スクリーン ポインターと親ポインターをスクリーン スタックにプッシュします。 新しいスクリーン ポインターがその後が親にアタッチされます。


> [!NOTE]
> *この API は古くなっており、gx_system_screen_stack_pop() に置き換えられています。このバージョンは、以前のライブラリ リリースとの下位互換性の確保のためにのみ提供されています。*

### <a name="parameters"></a>パラメーター

- **control** スクリーン スタック コントロール ブロック
- **screen** プッシュするスクリーン ポインター
- **new_screen** 新しいスクリーンへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) スクリーン スタックが正常にプッシュされました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Push “screen” and its parent to screen stack, Dettach “screen” from its parent, and attach “new screen” to the parent. */
status = gx_screen_stack_push(&my_stack_control,
                                screen, new_screen);

/* If status is GX_SUCCESS the widget “screen” and its parent have been pushed to screen stack, “screen” has been detached from its parent, “new_screen” has been attached to the parent. */
```

### <a name="see-also"></a>参照

- gx_screen_stack_create
- gx_screen_stack_push
- gx_screen_stack_reset

## <a name="gx_screen_stack_reset"></a>gx_screen_stack_reset


スクリーン スタックからすべてのエントリを削除します。

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_screen_stack_reset(GX_SCREEN_STACK_CONTROL *control);
```

### <a name="description"></a>説明

このサービスは、スクリーン スタックからすべてのエントリを削除します。

> [!NOTE]
> *この API は古くなっており、gx_system_screen_stack_pop() に置き換えられています。このバージョンは、以前のライブラリ リリースとの下位互換性の確保のためにのみ提供されています。*

### <a name="parameters"></a>パラメーター

- **control** スクリーン スタック コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) スクロールつまみが正常に作成されました
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Remove all enteries from the screen stack. */
status = gx_screen_stack_reset(&my_stack_control);

/* If status is GX_SUCCESS all entries of screen stack has been removed. */
```

### <a name="see-also"></a>参照

- gx_screen_stack_create
- gx_screen_stack_push
- gx_screen_stack_pop

## <a name="gx_scroll_thumb_create"></a>gx_scroll_thumb_create


スクロールつまみを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_scroll_thumb_create(
    GX_SCROLL_THUMB *scroll_thumb,
    GX_SCROLLBAR *parent, ULONG style);
```

### <a name="description"></a>説明

このサービスは、スクロール サムホイールを作成します。 このサービスは、通常、GX_SCROLLBAR が作成されるときに内部的に呼び出されますが、カスタム スクロールバーの実装を可能にするために公開されています。

### <a name="parameters"></a>パラメーター

- **scroll_thumb** スクロールつまみウィジェットのコントロール ブロック
- **parent** 親スクロールバーへのポインター
- **style** スクロール バー ウィジェットのスタイル。 **付録 D** には、すべてのウィジェット用に事前に定義されている一般的なスタイルと、ウィジェット固有のスタイルが含まれています。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) スクロールつまみが正常に作成されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE**: (0x19) ウィジェット コントロール ブロック サイズが無効です
- **GX_INVALID_WIDGET** (0x12) 親ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_SCROLL_THUMB my_scroll_thumb;

/* Create scroll thumb “my_scroll_thumb”. */
status = gx_scroll_thumb_create(&my_scroll_thumb, &my_scrollbar,
                                GX_STYLE_NONE);

/* If status is GX_SUCCESS the scroll thumb “my_scroll_thumb” has been created. */
```

### <a name="see-also"></a>参照

- gx_scroll_thumb_draw
- gx_scroll_thumb_event_process

## <a name="gx_scroll_thumb_draw"></a>gx_scroll_thumb_draw


スクロールつまみの描画

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_scroll_thumb_draw(GX_SCROLL_THUMB *scroll_thumb);
```

### <a name="description"></a>説明

このサービスは、スクロール サムホイールを描画します。 このサービスは、GUIX キャンバスの更新によって内部的に呼び出されますが、オーバーライドされた描画関数によって呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **scroll_thumb** スクロールつまみウィジェットのコントロール ブロック

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom scroll thumb drawing function. */

VOID my_scroll_thumb_draw(GX_SCROLL_THUMB *thumb)
{
    /* Call default scroll thumb draw. */
    gx_scroll_thumb_draw(thumb);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_scroll_thumb_create
- gx_scroll_thumb_event_process

## <a name="gx_scroll_thumb_event_process"></a>gx_scroll_thumb_event_process


スクロールつまみイベントの処理

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_scroll_thumb_event_process(
    GX_SCROLL_THUMB *scroll_thumb,
    GX_EVENT *event);
```

### <a name="description"></a>説明

このサービスは、スクロールバーのサムホイールに送信されるイベントを処理します。 このサービスは通常 GUIX によって内部的に使用されますが、カスタム スクロールバーの動作の実装を支援するために公開されています。

### <a name="parameters"></a>パラメーター

- **scroll_thumb** スクロールつまみウィジェットのコントロール ブロック
- **event** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) スクロールつまみのイベントが正常に処理されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Write a custom event processing function. */

UINT my_event_process (GX_SCROLL_THUMB *thumb, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_scroll_thumb_event_process(thumb, event_ptr);

        /* add my own handling here */
        break;
    default:
        status = gx_scroll_thumb_event_process(thumb, event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>参照

- gx_scroll_thumb_create
- gx_scroll_thumb_draw

## <a name="gx_scroll_wheel_create"></a>gx_scroll_wheel_create


基本のスクロール ホイール ウィジェットを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_scroll_wheel_create( 
    GX_SCROLL_WHEEL *wheel, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    INT total_rows, 
    ULONG style,
    USHORT id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスにより、基本のスクロール ホイール ウィジェットが作成されます。

基本のスクロール ホイールは、すべてのスクロール ホイール ウィジェットの種類の基本ウィジェットで、**gx_numeric_scroll_wheel** と **gx_string_ scroll_wheel** ウィジェットのベースである **gx_generic_scroll_wheel** と **gx_text_scroll_wheel** を含みます。 基本スクロール ホイール ウィジェットは、すべてのスクロール ホイール ウィジェットの種類について、イベント処理、スクロール アニメーション、および選択された行の計算を提供します。

通常、アプリケーションでは、汎用スクロール ホイール ウィジェットのインスタンスは作成しません。このウィジェットの種類では描画関数が提供されないためです。 ただし、カスタム スクロール ホイール ウィジェットの種類を作成する必要があるアプリケーションを支援するために、この API へのアクセスが用意されています。

GX_SCROLL_WHEEL は GX_WINDOW に基づいているため、GX_SCROLL_WHEEL および GX_SCROLL_WHEEL から派生したウィジェットでは、すべての GX_WINDOW API を使用できます。

### <a name="parameters"></a>パラメーター

- **wheel** 汎用スクロール ホイール コントロール ブロックへのポインター
- **name** アプリケーションで割り当てられたウィジェット名
- **parent** 親ウィジェット、または GX_NULL
- **total_rows** 使用可能な合計行数
- **style** ウィジェットのスタイル フラグ
- **id** アプリケーションで割り当てられたウィジェット ID
- **size** ウィジェットの初期サイズを定義する四角形

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) スクロール ホイールが正常に作成されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_SIZE**: (0x19) コントロール ブロック サイズが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが作成されました
- **GX_INVALID_WIDGET** (0x12) 親ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Call generic create function during custom widget createl. */

UINT custom_scroll_wheel_create(CUSTOM_SCROLL_WHEEL *wheel,
                    GX_CONST GX_CHAR *name,
                    GX_WIDGET *parent,
                    INT total_rows, ULONG style,
                    USHORT id,
                    GX_CONST GX_RECTANGLE *size)
{
    /* create base widget as part of custom create */
    status = gx_scroll_wheel_create(wheel, name, parent,
                            total_rows, style, id, size);

    /* If status is GX_SUCCESS the base scroll wheel has been created. */
}
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_event_process"></a>gx_scroll_wheel_event_process


汎用スクロール ホイール ウィジェットのイベント処理関数

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_scroll_wheel_event_process(
    GX_SCROLL_WHEEL *wheel,
    GX_EVENT *event);
```

### <a name="description"></a>説明

このサービスは、すべてのスクロール ホイール ウィジェットの種類に対する基本的な入力イベント処理を提供します。

この関数は、カスタムのスクロール ホイール ウィジェットの種類を作成する必要があるアプリケーションを支援するために、アプリケーション ソフトウェアに公開されています。 多くの場合、アプリケーションは独自のイベント処理関数を提供しますが、カスタマイズする必要がないイベントについては、ホイール ウィジェットの汎用イベント処理を呼び出します。

### <a name="parameters"></a>パラメーター

- **wheel** 汎用スクロール ホイール コントロール ブロックへのポインター
- **event** GX_EVENT ポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) スクロール ホイールのイベント処理が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Call generic scroll wheel event processing 
    as part of custom event processing function. */

UINT custom_scroll_wheel_event_process(CUSTOM_SCROLL_WHEEL *wheel,
                    GX_EVENT *event)
{
    switch(event->gx_event_type)
    {
    case xyz:
        /* insert custom event handling here */
        break;

    default:
        /* pass all other events to the generic scroll wheel
            event processing */
        gx_scroll_wheel_event_process(wheel, event);
        break;
    }
}
```


### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_gradient_alpha_set"></a>gx_scroll_wheel_gradient_alpha_set


オプションのオーバーレイ グラデーションにグラデーションのアルファ値を割り当てる

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_scroll_wheel_gradient_alpha_set(
    GX_SCROLL_WHEEL *wheel,
    GX_UBYTE start_alpha,
    GX_UBYTE end_alpha);
```

### <a name="description"></a>説明

このサービスは、スクロール ホイール ウィジェットのオプションのグラデーション オーバーレイの開始と終了のアルファ値を定義します。

すべてのスクロール ホイール ウィジェットは、スクロール ホイール ウィジェットの上端と下端付近の行でスクロール ホイール行の "フェード" 効果をサポートしています。 このフェード効果は、スクロール ホイールの行の上にグラデーション ピクセルマップを描画することによって達成されます。これにより、スクロール ホイール ウィジェットの上部および下部付近に行が描画されると、行がフェードアウトします。

この API サービスを使用すると、アプリケーションでフェード効果の強度を変更したり、開始と終了のアルファ値を 0 に設定することによって、この効果を完全に無効にしたるすることができます。

グラデーションのピクセルマップは、スクロール ホイールが最初に表示されるときに実行時に作成されます。 これには、_gx_system_memory_allocator_set() を使用してランタイム メモリ割り当てサービスが定義されている必要があります。 メモリ アロケーター関数が定義されていない場合、グラデーション イメージは作成されず、フェード効果は使用できません。

### <a name="parameters"></a>パラメーター

- **wheel** 汎用スクロール ホイール コントロール ブロックへのポインター
- **start_alpha** オーバーレイ グラデーションの開始アルファ値。
- **end_alpha** オーバーレイ グラデーションの終了アルファ値。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) スクロール ホイールのグラデーション アルファを正常に設定しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
status = gx_scroll_wheel_gradient_alpha_set(&wheel, 240, 0);
/* if status == GX_SUCCESS the wheel gradient alpha values were
Successfully assigned. */
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_row_height_set"></a>gx_scroll_wheel_row_height_set


各ホイール行に行の高さを割り当てる

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_scroll_wheel_row_height_set(
    GX_SCROLL_WHEEL *wheel,
    GX_VALUE row_height);
```

### <a name="description"></a>説明

このサービスでは、スクロール ホイールの各行に行の高さが割り当てられます。 スクロール ホイールのスタイルが GX_STYLE_TEXT_SCROLL_WHEEL_ROUND の場合、行の高さは変換を通過するため、行がホイールの上端または下端に近づくにつれて行の高さが実質的に縮小されることに注意してください。

### <a name="parameters"></a>パラメーター

- **wheel** 汎用スクロール ホイール コントロール ブロックへのポインター
- **row_height** 行の高さの値 (ピクセル単位)。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) スクロール ホイールの高さが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
status = gx_scroll_wheel_row_height_set(&wheel, 40);

/* if status == GX_SUCCESS the wheel row height has been set to 40
pixels. */
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_gradient_alpha_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_selected_background_set"></a>gx_scroll_wheel_selected_background_set


ホイールで選択された行の背景画像を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_scroll_wheel_selected_background_set(
    GX_SCROLL_WHEEL*wheel, 
    GX_RESOURCE_ID image_id);
```

### <a name="description"></a>説明

このサービスは、スクロール ホイールの選択された行の背後に描画されるオプションのピクセルマップ ID を割り当てます。 これを使用すると、選択された行を強調表示して、ユーザーがスクロール ホイールのどの行を選択しているかを簡単に区別できるようになります。

### <a name="parameters"></a>パラメーター

- **wheel** 汎用スクロール ホイール コントロール ブロックへのポインター
- **image_id** 選択された行の背景画像として使用するピクセルマップの ID。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) スクロール ホイールの背景が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
status = gx_scroll_wheel_selected_background_set(&wheel,
GX_PIXELMAP_ID_SELECTED_ROW);

/* if status == GX_SUCCESS the background image has been
assigned. */
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_selected_get"></a>gx_scroll_wheel_selected_get


現在選択されているホイール行を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_scroll_wheel_selected_get(
    GX_SCROLL_WHEEL *wheel,
    INT *row);
```

### <a name="description"></a>説明

このサービスは、スクロール ホイールに対してクエリを実行し、現在選択されている行を取得します。 呼び出し元は、選択された行インデックスを返す場所を、この関数の 2 番目のパラメーターとして渡す必要があります。

### <a name="parameters"></a>パラメーター

- **wheel** 汎用スクロール ホイール コントロール ブロックへのポインター
- **row** 選択された行の値が返される場所。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 選択されているホイール行が正常に取得されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x19) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
INT row;
status = gx_scroll_wheel_selected_get(&wheel, &row);

/* if status == GX_SUCCESS the selected row has been returned in
the row variable. */
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_selected_set"></a>gx_scroll_wheel_selected_set


選択したスクロール ホイール行の割り当て

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_scroll_wheel_selected_set(
    GX_SCROLL_WHEEL *wheel,
    INT row);
```

### <a name="description"></a>説明

このサービスは、現在選択されているスクロール ホイールの行を割り当てます。

### <a name="parameters"></a>パラメーター

- **wheel** 汎用スクロール ホイール コントロール ブロックへのポインター
- **row** 選択するスクロール ホイールの行。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 選択されているホイール行が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
status = gx_scroll_wheel_selected_set(&wheel, 20);

/* if status == GX_SUCCESS the scroll wheel has been set to select
row 20 */
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_speed_set"></a>gx_scroll_wheel_speed_set


スクロール速度を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_scroll_wheel_speed_set(
    GX_SCROLL_WHEEL *wheel,
    GX_FIXED_VAL start_speed_rate,
    GX_FIXED_VAL end_speed_rate,
    GX_VALUE max_steps,
    GX_VALUE delay);
```

### <a name="description"></a>説明

このサービスは、スクロール ホイール ウィジェットにスクロール速度を割り当てます。

### <a name="parameters"></a>パラメーター

- **wheel** 汎用スクロール ホイール コントロール ブロックへのポインター
- **start_speed_rate** フリック速度に対するスクロールの開始速度。
- **start_speed_rate** フリック速度に対するスクロールの終了速度
- **max_steps** スクロールの最大ステップ数。
- **delay** 各ステップの遅延時間。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ホイール速度が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE** (0x22) 値が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
status = gx_scroll_wheel_speed_set(&wheel, GX_FIXED_VAL_MAKE(2),
                                GX_FIXED_VAL_MAKE(1) / 2, 10, 2);

/* if status == GX_SUCCESS the scroll wheel speed has been
successfully set. */
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_total_rows_set"></a>gx_scroll_wheel_total_rows_set


使用可能な合計スクロール ホイール行数を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_scroll_wheel_total_rows_set(
    GX_SCROLL_WHEEL *wheel,
    INT total_rows);
```

### <a name="description"></a>説明

このサービスは、指定されたスクロール ホイールで使用可能な行数を割り当てます。 スクロール ホイール ウィジェットは通常、文字列の配列またはユーザーが指定した文字列データの形式で、アプリケーションから行の内容を受け取ります。 この API により、ユーザーに表示される行の合計数がスクロール ホイールに通知されます。

### <a name="parameters"></a>パラメーター

- **wheel** 汎用スクロール ホイール コントロール ブロックへのポインター
- **total_rows** ユーザーに表示されるホイール行の合計数。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) スクロール ホイールの合計行が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE** (0x22) 値が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
status = gx_scroll_wheel_total_rows_set(&wheel, 100);

/* if status == GX_SUCCESS the scroll wheel has been changed to
display 100 total rows */
```
### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scrollbar_draw"></a>gx_scrollbar_draw


スクロール バーを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_scrollbar_draw(GX_SCROLLBAR *scrollbar);
```

### <a name="description"></a>説明

このサービスにより、スクロール バーが描画されます。 共通の描画関数が、垂直と水平の両方のスクロール バー ウィジェットに使用されます。 このサービスは、GUIX キャンバスの更新によって内部的に呼び出されますが、カスタム描画関数によって呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **scrollbar** 描画するスクロール バー ウィジェット

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom scrollbar drawing function. */

VOID my_scrollbar_draw(GX_SCROLLBAR *scrollbar)
{
    /* Call default scrollbar draw. */
    gx_scrollbar_draw(thumb);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_ horizontal_scrollbar_create
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_event_process"></a>gx_scrollbar_event_process


スクロール バーのイベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_scrollbar_event_process(
    GX_SCROLLBAR *scrollbar,
    GX_EVENT *event);
```

### <a name="description"></a>説明

このサービスは、スクロール バー イベントを処理します。 共通のイベント処理関数が、垂直と水平の両方のスクロール バー ウィジェットに使用されます。

### <a name="parameters"></a>パラメーター

- **scrollbar** スクロール バーのウィジェット コントロール ブロック
- **event** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) スクロール バーのイベントが正常に処理されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
Call generic scrollbar event processing as part of custom event processing function. */

UINT custom_scrollbar_event_process(GX_SCROLLBAR *scrollbar,
                                    GX_EVENT *event)
{
    switch(event->gx_event_type)
    {
    case xyz:
        /* insert custom event handling here */
        break;
    default:
        /* pass all other events to the generic scrollbar
            event processing */
        gx_scrollbar_event_process(scrollbar, event);
        break;
    }
}
```

### <a name="see-also"></a>参照

- gx_ horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_limit_check"></a>gx_scrollbar_limit_check


スクロール バーの制限を確認します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_scrollbar_limit_check(GX_SCROLLBAR *scrollbar);
```

### <a name="description"></a>説明

このサービスは、スクロール バーの制限を確認し、事前定義された制限を超えてスクロールバーのサムホイールが移動しないようにします。

### <a name="parameters"></a>パラメーター

- **scrollbar** スクロール バーのウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) スクロール バーの制限が正常に確認されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Check scrollbar limit of “my_scrollbar”. */
status = gx_scrollbar_limit_check(&my_scrollbar);

/* If status is GX_SUCCESS the limit of scrollbar “my_scrollbar” has been checked. */
```

### <a name="see-also"></a>参照

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_reset"></a>gx_scrollbar_reset


スクロール バーをリセットします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_scrollbar_reset(
    GX_SCROLLBAR *scrollbar,
    GX_SCROLL_INFO *info);
```

### <a name="description"></a>説明

このサービスは、スクロール バーをリセットします。

### <a name="parameters"></a>パラメーター

- **scrollbar** スクロール バーのウィジェット コントロール ブロック
- **info** スクロール バーの制限、現在の値、およびステップまたは増分を定義する GX_SCROLL_INFO 構造体へのポインター。 **付録 I** には GX_LINE_CHART_INFO 構造体についての定義が含まれています。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) スクロール バーが正常にリセットされました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE** (0x22) スクロール情報が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Reset scrollbar “my_scrollbar”. */

GX_SCROLL_INFO my_info;

my_info.gx_scroll_value = 0;
my_info.gx_scroll_minimum = 0;
my_info.gx_scroll_maximum = 100;
my_info.gx_scroll_visible = 10;
my_info.gx_scroll_increment = 1;

status = gx_scrollbar_reset(&my_scrollbar, &my_info);

/* If status is GX_SUCCESS the scrollbar “my_scrollbar” has been reset. */
```

### <a name="see-also"></a>参照

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_value_set"></a>gx_scrollbar_value_set


スクロール バーの値を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_scrollbar_value_set(
    GX_SCROLLBAR *scrollbar,
    INT value);
```

### <a name="description"></a>説明

このサービスは、現在のスクロール バー値を割り当てます。 GX_EVENT_VERTICAL_SCROLL または GX_EVENT_HORIZONTAL_SCROLL イベントが親ウィンドウに生成されます。

### <a name="parameters"></a>パラメーター

- **scrollbar** スクロール バーのウィジェット コントロール ブロック
- **value** 新しいスクロール バー値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0X00) スクロール バーのイベントが正常に処理されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE** (0x22) スクロール値が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Assign new value for scrollbar “my_scrollbar”. */

status = gx_scrollbar_value_set(&my_scrollbar, 0);

/* If status is GX_SUCCESS the current position of scrollbar “my_scrollbar” has been set. */

```

### <a name="see-also"></a>参照

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_single_line_text_input_backspace"></a>gx_single_line_text_input_backspace


テキスト入力ウィジェット内のバックスペース文字を処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_backspace(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>説明

このサービスは、テキスト入力のカーソル位置の前にある文字を削除します。 このサービスは、Backspace キーを押すイベントを受信したときに内部的に呼び出されますが、アプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 単一行テキスト入力が正常に作成されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x23) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Delete a character before the cursor of “my_text_input”. */
status = gx_single_line_text_input_backspace(&my_text_input);

/* If status is GX_SUCCESS the character before the cursor has been deleted. */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_buffer_clear"></a>gx_single_line_text_input_buffer_clear


テキスト入力バッファーからすべての文字を削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_buffer_clear(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>説明

このサービスは、テキスト入力バッファーからすべての文字を削除します。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 単一行テキスト入力バッファーが正常にクリアされました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* clear input buffer of “my_text_input”. */
status = gx_single_line_text_input_clear(&my_text_input);

/* If status is GX_SUCCESS the text input widget has emptied its input buffer. */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_buffer_backspace
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_buffer_get"></a>gx_single_line_text_input_buffer_get


テキスト入力ウィジェットのバッファー情報を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_buffer_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CHAR **buffer_address, 
    UINT *content_size, 
    UINT *buffer_size);
```

### <a name="description"></a>説明

このサービスは、テキスト入力ウィジェットのバッファー情報を取得します。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック
- **buffer_address** 入力バッファーのアドレス
- **content_size** 入力データのバイト数
- **buffer_size** 入力バッファーのサイズ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) バッファー情報が正常に取得されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_CHAR *buffer_address;
UINT buffer_size;
UINT content_size;

/* Retrieve buffer information of “my_text_input” widget. */
status = gx_single_line_text_input_buffer_get(&my_text_input,
                    &buffer_address, &string_size, &buffer_size);

/* If status is GX_SUCCESS the value of buffer_address, string_size and buffer_size has been retrieved. */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_character_delete"></a>gx_single_line_text_input_character_delete


現在のカーソル位置にある文字を削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_character_delete(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>説明

このサービスでは、テキスト入力のカーソル位置の後にある文字を削除します。 このサービスは、Delete キーを押すイベントを受信したときに内部的に呼び出されますが、アプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) カーソルの後の文字を正常に削除しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Delete the character after the cursor of “my_text_input”. */
status = gx_single_line_text_input_character_delete(&my_text_input);

/* If status is GX_SUCCESS the character after the cursor has been deleted. */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_multi_line_text_input_create
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_character_insert"></a>gx_single_line_text_input_character_insert


現在のカーソル位置に文字列を挿入します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_character_insert(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_UBYTE *insert_str,
    UINT insert_size);
```

### <a name="description"></a>説明

このサービスでは、テキスト入力文字列バッファーの現在のカーソル位置に文字列を挿入します。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック
- **insert_str** 挿入される文字列
- **insert_size** 挿入されるバイト数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 文字が正常に挿入されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Insert characters at current cursor position. */

GX_CHAR insert_text[10] = “insert”;
status = gx_single_line_text_input_character_insert(&my_text_input,
                                            insert_text,
                                            GX_STRLEN(insert_text));

/* If status is GX_SUCCESS the text input widget has successfully insert the string. */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_create"></a>gx_single_line_text_input_create


テキスト入力ウィジェットを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_create(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *name, GX_WIDGET *parent,
    GX_CHAR *input_buffer, UINT buffer_size,
    UINT style, USHORT text_input_id, GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスは、テキスト入力ウィジェットを作成します。 呼び出し元は、入力文字列の記憶域を提供し、文字列の最大長を示す必要があります。

GX_SINGLE_LINE_TEXT_INPUT は GX_PROMPT から派生しているため、すべての gx_prompt サービスを GX_SINGLE_LINE_TEXT_INPUT ウィジェットで使用できます。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック
- **namae** 省略可能なウィジェット論理名
- **parent** 省略可能な親ウィジェット
- **input_buffer** 入力文字列の記憶域
- **buffer_size** 入力文字列の記憶域のサイズ (バイト単位)。
- **style** テキスト入力のスタイル フラグ
- **text_input_id** 入力ウィジェットの省略可能な ID
- **size** ウィジェットの初期サイズを定義する四角形

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 単一行テキスト入力が正常に作成されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_SINGLE_LINE_TEXT_INPUT my_text_input;
static GX_CHAR           text_input_buffer[100];
GX_RECTANGLE             size;

/* Define widget size. */
gx_utility_rectangle_define(&size, 10, 10, 110, 40);

/* Create single-line text input widget “my_text_input”. */
status = gx_single_line_text_input_create(&my_text_input,
                        “text_input”, GX_NULL, text_input_buffer, 100,
                        GX_STYLE_ENABLED, 0, &size);

/* If status is GX_SUCCESS, the text input widget has been created. */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_draw"></a>gx_single_line_text_input_draw


テキスト入力ウィジェットを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_single_line_text_input_draw(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>説明

このサービスは、テキスト入力ウィジェットを描画します。 このサービスは通常、キャンバスの更新中に内部的に呼び出されますが、カスタムのテキスト入力描画関数から呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom single line text input draw function. */

VOID my_sl_text_input_draw(GX_SINGLE_LINE_TEXT_INPUT *input)
{
    /* Call default single line text input draw. */
    gx_single_line_text_input_draw(input);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_draw_position_get"></a>gx_single_line_text_input_draw_position_get


テキスト描画の開始位置を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_draw_position_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_VALUE *xpos, GX_VALUE *ypos);
```

### <a name="description"></a>説明

このサービスは、テキスト入力テキストの描画開始位置を取得します。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック
- **xpos** 取得された x 座標の描画開始位置
- **ypos** 取得された y 座標の描画開始位置

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) テキスト入力カーソルを末尾に正常に移動しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Write a custom single line text input draw function. */

VOID my_sl_text_input_draw(GX_SINGLE_LINE_TEXT_INPUT *input)
{
GX_VALUE xpos;
GX_VALUE ypos;

    /* Draw background. */
    gx_widget_border_draw(input, border_color, upper_fill_color,
                          lower_fill_color, GX_TRUE);

    /* Retrieve text draw start position. */
    gx_single_line_text_input_draw_position_get(input, xpos,
                                                ypos);

    /* Add your text drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_end"></a>gx_single_line_text_input_end


テキスト入力カーソルを文字列の末尾に移動します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_end(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>説明

このサービスでは、入力文字列の末尾にテキスト入力ウィジェット カーソルを配置します。 このサービスは、End キーを押すイベントを受信したときに内部的に呼び出されますが、アプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) テキスト入力カーソルを末尾に正常に移動しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Move input cursor to end. */
status = gx_single_line_text_input_end(&my_text_input);

/* If status is GX_SUCCESS, text text input cursor has been moved to end. */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_event_process"></a>gx_single_line_text_input_event_process


テキスト入力ウィジェットのイベント処理関数

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_event_process(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>説明

このサービスは、単一行テキスト入力イベントを処理します。 この関数は gx_single_line_text_input_create 関数によって内部的に参照されますが、アプリケーションでカスタムの単一行テキスト入力イベント処理関数を定義する場合には、アプリケーションで使用するために公開されます。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック
- **event_ptr** GX_EVENT 構造体へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) テキスト入力イベントが正常に処理されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Call generic single line text input event processing as part of custom event processing function. */

UINT custom_sl_text_input_event_process(
                                GX_SINGLE_LINE_TEXT_INPUT *input,
                                GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default single line
            text input event processing */
        status =
        gx_single_line_text_input_event_process(input, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_fill_color_set"></a>gx_single_line_text_input_fill_color_set


単一行テキスト入力の背景色を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_fill_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_fill_color_id,
    GX_RESOURCE_ID selected_fill_color_id,
    GX_RESOURCE_ID disabled_fill_color_id,
    GX_RESOURCE_ID readonly_fill_color_id);
```

### <a name="description"></a>説明

このサービスは、単一行テキスト入力の塗りつぶしの色を設定します。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力コントロール ブロックへのポインター
- **normal_fill_color_id** 通常状態のウィジェット塗りつぶしの色のリソース ID。 **付録 A** には、事前定義された色のリソース ID が含まれています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。
- **selected_fill_color_id** ウィジェットがフォーカスされたときのウィジェット塗りつぶしの色のリソース ID。 **付録 A** には、事前定義された色のリソース ID が含まれています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。
- **disabled_fill_color_id** スタイル GX_STYLE_ENABLED が設定されていない場合のウィジェット塗りつぶしの色のリソース ID。 **付録 A** には、事前定義された色のリソース ID が含まれています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。
- **readonly_fill_color_id** スタイル GX_STYLE_ENABLED と GX_STYLE_TEXT_INPUT_READYONLY の両方が設定されている場合のウィジェット塗りつぶしの色のリソース ID。 **付録 A** には、事前定義された色のリソース ID が含まれています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 単一行テキスト入力の塗りつぶしの色が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set fill colors for single line text input “my_text_input”. */
status = gx_single_line_text_input_fill_color_set(&my_text_input,
                    GX_COLOR_ID_NORMAL_FILL,
                    GX_COLOR_ID_SELECTED_FILL,
                    GX_COLOR_ID_DISABLED_FILL,
                    GX_COLOR_ID_READONLY_FILL);

/* If status is GX_SUCCESS, the fill color of “my_text_input” was
set. */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_home"></a>gx_single_line_text_input_home


テキスト入力カーソルをホーム位置に移動します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_home(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>説明

このサービスにより、テキスト入力カーソルの位置が入力文字列の先頭に移動されます。 このサービスは、Home キーを押すイベントを受信したときに内部的に呼び出されますが、アプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) カーソルがホーム位置に正常に移動されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Move cursor to the start of the input text. */
status = gx_single_line_text_input_home(&my_text_input);

/* If status is GX_SUCCESS the cursor has been moved to the home position */
```

### <a name="see-also"></a>参照
- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_left_arrow"></a>gx_single_line_text_input_left_arrow


入力のカーソルを 1 文字分左に移動します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_left_arrow(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>説明

このサービスは、テキスト入力のカーソルを 1 文字分左に移動します。 このサービスは、左矢印キーを押すイベントを受信したときに内部的に呼び出されますが、アプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) カーソルが左へ正常に移動されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Move the cursor one character to the left. */
status = gx_single_line_text_input_left_arrow(&my_text_input);

/* If status is GX_SUCCESS the text input cursor has been moved one character to the left. */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_position_get"></a>gx_single_line_text_input_position_get

カーソルをピクセル位置に移動します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_position_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    INT pixel_position);
```

### <a name="description"></a>説明

このサービスでは、要求されたピクセル位置に基づいてテキスト入力カーソルを配置します。 テキスト入力カーソルのインデックスは、ピクセル位置の x 値に基づいて計算されます。 このサービスは、ペン ダウン イベントを受信したときに内部的に呼び出されますが、アプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック
- **pixel_position** ピクセル位置の X 値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 要求された位置にカーソルが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set cursor to requested position. */
status = gx_single_line_text_input_position_get(&my_text_input,
                                                100);

/* If status is GX_SUCCESS the text input widget cursor has been positioned */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_right_arrow"></a>gx_single_line_text_input_right_arrow


入力のカーソルを 1 文字分右に移動します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_right_arrow(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>説明

このサービスは、テキスト入力のカーソルを 1 文字分右に移動します。 このサービスは、右矢印キーを押すイベントを受信したときに内部的に呼び出されますが、アプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) カーソルが右に正常に移動されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Move cursor one character to the right. */
status = gx_single_line_text_input_right_arrow(&my_text_input);

/* If status is GX_SUCCESS the text input cursor has been moved one character to the right. */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_style_add"></a>gx_single_line_text_input_style_add


スタイルを追加します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_style_add(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>説明

このサービスは、指定したスタイルを単一行テキスト入力ウィジェットに追加します。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック
- **style** 追加する新しいスタイル。 **付録 D** には、すべてのウィジェットの事前定義された一般的なスタイルが含まれています

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットにスタイルが正常に追加されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Add a new style to “my_text_input”. */
status = gx_single_line_text_input_style_add(&my_text_input,
GX_STYLE_CURSOR_AWAYS);

/* If status is GX_SUCCESS the GX_STYLE_CUSROSR_SHOR have been successfully added. */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gax_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_style_remove"></a>gx_single_line_text_input_style_remove

スタイルを削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_style_remove(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>説明

このサービスは、指定したスタイルが単一行テキスト入力ウィジェットから削除します。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック
- **style** 削除するスタイル。 **付録 D** には、すべてのウィジェットの事前定義された一般的なスタイルが含まれています

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットからスタイルが正常に削除されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Remove cursor blink style from “my_text_input”. */
status = gx_single_line_text_input_style_remove(&my_text_input,
GX_STYLE_CURSOR_BLINK);

/* If status is GX_SUCCESS the GX_STYLE_CURSOR_BLINK style has been successfully removed. */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_style_set"></a>gx_single_line_text_input_style_set


テキスト入力のスタイルを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_style_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>説明

このサービスは、指定したスタイルを単一行テキスト入力ウィジェットに設定します。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力ウィジェット コントロール ブロック
- **style** 割り当てるスタイル フラグ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) テキスト入力スタイルが正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set style for “my_text_input”. */
status = gx_single_line_text_input_style_set(&my_text_input,
                    GX_STYLE_ENABLED | GX_STYLE_CURSOR_BLINK);

/* If status is GX_SUCCESS the text input style has been successfully set to the specified styles. */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_signle_line_text_input_event_process
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_text_color_set"></a>gx_single_line_text_input_text_color_set


単一行テキスト入力のテキストの色を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_text_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id,
    GX_RESOURCE_ID readonly_text_color_id);
```

### <a name="description"></a>説明

このサービスは、単一行テキスト入力のテキストの色を設定します。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力コントロール ブロックへのポインター
- **normal_text_color_id** 通常状態のテキストの色のリソース ID。 **付録 A** には、事前定義された色のリソース ID が含まれています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。
- **selected_text_color_id** ウィジェットがフォーカスされたときのテキストの色のリソース ID。 **付録 A** には、事前定義された色のリソース ID が含まれています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。
- **disabled_text_color_id** スタイル GX_STYLE_ENABLED が設定されていない場合のテキストの色のリソース ID。 **付録 A** には、事前定義された色のリソース ID が含まれています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。
- **readonly_text_color_id** スタイル GX_STYLE_ENABLED と GX_STYLE_TEXT_INPUT_READONLY の両方が設定されている場合のテキストの色のリソース ID。 **付録 A** には、事前定義された色のリソース ID が含まれています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 単一行テキスト入力のテキストの色が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set text colors for single line text input “my_text_input”. */
status = gx_single_line_text_input_text_color_set(&my_text_input,
                                        GX_COLOR_ID_NORMAL_TEXT,
                                        GX_COLOR_ID_SELECTED_TEXT,
                                        GX_COLOR_ID_DISABLED_TEXT,
                                        GX_COLOR_ID_READONLY_TEXT);

/* If status is GX_SUCCESS, the text color “my_text_input” was set. */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_text_select"></a>gx_single_line_text_input_text_select

テキストを選択します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_text_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    UINT start_index, UINT end_index);
```

### <a name="description"></a>説明

このサービスでは、指定された開始マークと終了マークのインデックスを使用してテキストを選択し、選択された塗りつぶしとテキストの色を使用して、選択されたテキストを強調表示します。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力コントロール ブロックへのポインター
- **start_index** 最初に選択された文字のインデックス
- **end_index** 最後に選択された文字のインデックス

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 単一行テキスト入力のテキストが正常に選択されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE** (0x22) インデックスの値が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Select text between index [0, 9]. */
status = gx_single_line_text_input_text_select(&my_text_input,
                                                0,9);

/* If status is GX_SUCCESS, the text between index [0, 9] “my_text_input” was selected. */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_text_set"></a>gx_single_line_text_input_text_set


単一行テキスト入力のテキストを設定します (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_text_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *text);
```

### <a name="description"></a>説明

このサービスは非推奨となりました。gx_single_line_text_input_text_set_ext() を使用してください

このサービスは、単一行テキスト入力のテキストを設定します。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力コントロール ブロックへのポインター
- **text** null 値で終わるテキスト文字列

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 単一行テキスト入力のテキストの色が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_STRING_LENGTH**: (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_CONST GX_CHAR new_text = “Set Single Line Text Input Text”;

/* Set text for single line text input “my_text_input”. */
status = gx_single_line_text_input_text_set(&my_text_input,
                                        new_text);

/* If status is GX_SUCCESS, the text of “my_text_input” was set. */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_text_set_ext

## <a name="gx_single_line_text_input_text_set_ext"></a>gx_single_line_text_input_text_set_ext


単一行テキスト入力のテキストを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_single_line_text_input_text_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>説明

このサービスは、単一行テキスト入力のテキストを設定します。

### <a name="parameters"></a>パラメーター

- **text_input** 単一行テキスト入力コントロール ブロックへのポインター
- **string** GX_STRING 変数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 単一行テキスト入力のテキストの色が正常に設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_STRING_LENGTH**: (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_STRING new_string;
new_string.gx_string_ptr = “Set Single Line Text Input Text”;
new_string.gx_string_length = strlen(new_string.gx_string_ptr);

/* Set text for single line text input “my_text_input”. */
status = gx_single_line_text_input_text_set_ext(&my_text_input,
                                        &new_string);

/* If status is GX_SUCCESS, the string has been assigned to my_text_input. */
```

### <a name="see-also"></a>参照

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_set_ext


## <a name="gx_slider_create"></a>gx_slider_create

スライダーを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_slider_create(
    GX_SLIDER *slider, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, INT tick_count,
    GX_SLIDER_INFO *slider_info,
    ULONG style, USHORT slider_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスにより、スライダー ウィジェットが作成されます。

GX_SLIDER は GX_WIDGET から派生しているため、すべての gx_widget API サービスを GX_SLIDER 型のウィジェットで使用できます。

### <a name="parameters"></a>パラメーター

- **slider**: スライダー ウィジェット コントロール ブロック
- **name**: スライダーの名前
- **parent**: 親ウィジェットへのポインター
- **tick_count**: スライダーの目盛りの数
- **slider_info**: スライダーの値の制限、スライダーの針のサイズと位置、およびその他のスライダー パラメーターを渡すために使用される構造体であるスライダー情報へのポインター。 **付録 I** に GX_SLIDER_INFO 構造体についての定義が含まれています。
- **style**: スライダーのスタイル。 **付録 D** には、すべてのウィジェット用に事前定義されている一般的なスタイルと、ウィジェット固有のスタイルが含まれています。
- **slider_id**: スライダーのアプリケーション定義 ID
- **size**: スライダーの大きさ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) スライダーが正常に作成されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_ALREADY_CREATED**: (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE**: (0x19) ウィジェット コントロール ブロック サイズが無効です
- **GX_INVALID_WIDGET**: (0x12) 親ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Create slider “my_slider”. */

GX_SLIDER my_slider;
GX_SLIDER_INFO info;

info.gx_slider_info_min_val = 0;
info.gx_slider_info_max_val = 100;
info.gx_slider_info_current_val = 50;
info.gx_slider_info_increment = 1;
info.gx_slider_info_min_travel = 20;
info.gx_slider_info_max_travel = 20;
info.gx_slider_info_needle_width = 10;
info.gx_slider_info_needle_height = 10;
info.gx_slider_info_needle_inset = 5;
info.gx_slider_info_needle_hotspot_offset = 5;

status = gx_slider_create(&my_slider, “my_slider”,
    &my_parent, 10, info, GX_STYLE_ENABLED, ID_MY_SLIDER, &size);

/* If status is GX_SUCCESS the slider “my_slider” has been created. */
```

### <a name="see-also"></a>参照

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_draw"></a>gx_slider_draw

スライダーを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_slider_draw(GX_SLIDER *slider);
```

### <a name="description"></a>説明

このサービスにより、スライダーが描画されます。 このサービスは gx_slider_create 関数によって内部的に使用されますが、カスタムのスライダー描画関数が定義されている場合に、それらのインスタンスのアプリケーションで使用するために公開もされています。

### <a name="parameters"></a>パラメーター

- **slider**: スライダー ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom slider draw function. */
VOID my_slider_draw(GX_SLIDER *slider)
{
    /* Call default slider draw. */
    gx_slider_draw(slider);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_event_process"></a>gx_slider_event_process

スライダーのイベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_slider_event_process(
    GX_SLIDER *slider, 
    GX_EVENT *event);
```

### <a name="description"></a>説明

このサービスでは、スライダー イベントが処理されます。 この関数は gx_slider_creat 関数によって内部的に参照されますが、アプリケーションでカスタムのスライダー イベント処理関数を定義する場合は、アプリケーションで使用するために公開されます。

### <a name="parameters"></a>パラメーター

- **slider**: スライダー ウィジェット コントロール ブロック
- **event**: 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0X00) スライダーのイベントが正常に処理されしました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Call generic slider event processing as part of custom event processing function. */

UINT custom_slider_event_process(GX_SLIDER *slider,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;
    switch(event->gx_event_type)
    {
        case xyz:
            /* Insert custom event handling here */
            break;
        default:
            /* Pass all other events to the default slider event processing */
            status = gx_slider_event_process(slider, event);
            break;
    }
    return status;
}
```

### <a name="see-also"></a>参照

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_info_set"></a>gx_slider_info_set

スライダー情報ブロックを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_slider_info_set(
    GX_SLIDER *slider, 
    GX_SLIDER_INFO *info);
```

### <a name="description"></a>説明

このサービスは、スライダーの最小値、スライダーの最大値、スライダーの現在の値などの指定されたスライダー情報を、指示されたスライダーに割り当てます。 スライダーは、新しいスライダー情報に基づいて針の位置を更新し、再描画します。

### <a name="parameters"></a>パラメーター

- **slider**: スライダー ウィジェット コントロール ブロック
- **info**: スライダー情報構造体へのポインター。 **付録 I** に GX_SLIDER_INFO 構造体についての定義が含まれています。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) スライダー情報が正常に設定されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_SLIDER_INFO my_slider_info;
my_slider_info.gx_slider_info_min_val = 0;
my_slider_info.gx_slider_info_max_val = 100;
my_slider_info.gx_slider_info_current_val = 50;
my_slider_info.gx_slider_info_increment = 1;
my_slider_info.gx_slider_info_min_travel = 20;
my_slider_info.gx_slider_info_max_travel = 20;
my_slider_info.gx_slider_info_needle_width = 10;
my_slider_info.gx_slider_info_needle_height = 10;
my_slider_info.gx_slider_info_needle_inset = 5;

my_slider_info.gx_slider_info_needle_hotspot_offset = 5;

/* Set slider information for slider “my_slider”. */
status = gx_slider_info_set (&my_slider, &my_slider_info);

/* If status is GX_SUCCESS the “my_slider” is configured with my_slider_info. */
```

### <a name="see-also"></a>参照

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_needle_draw"></a>gx_slider_needle_draw

スライダーの針を描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_slider_needle_draw(GX_SLIDER *slider);
```

### <a name="description"></a>説明

このサービスは、スライダーの針を描画します。 このサービスは、gx_slider_draw 関数によって自動的に呼び出されますが、カスタマイズされたスライダー描画関数の一部としてアプリケーションによって呼び出されることもあります。

### <a name="parameters"></a>パラメーター

- **slider**: スライダー ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom slider draw function. */
VOID my_slider_draw(GX_SLIDER *slider)
{
    /* Add your own background draw here. */

    /* Call default tickmarks draw. */
    gx_slider_tickmarks_draw(slider);

    /* Call default slider needle draw. */
    gx_slider_needle_draw(slider);
}
```

### <a name="see-also"></a>参照

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_needle_position_get"></a>gx_slider_needle_position_get

スライダーの針の位置を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_slider_needle_position_get(
    GX_SLIDER *slider,
    GX_SLIDER_INFO *slider_info,
    GX_RECTANGLE *return_position);
```

### <a name="description"></a>説明

このサービスにより、現在のスライダー値に基づいてスライダーの針の位置が計算されます。

### <a name="parameters"></a>パラメーター

- **slider**: スライダー ウィジェット コントロール ブロック
- **slider_info**: スライダーの制限、針のサイズとオフセット、およびその他のスライダー パラメーターを定義するスライダー情報構造体へのポインター。 **付録 I** に GX_SLIDER_INFO 構造体についての定義が含まれています。
- **return_position**: 針の位置の設定先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0X00) スライダーの針の位置が正常に取得されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE**: (0x22) スライダー情報が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_RECTANGLE needle_position;

/* Get the needle position for slider “my_slider”. */
status = gx_slider_needle_posistion_get(&my_slider, &slider_info,
    &needle_position);

/* If status is GX_SUCCESS the needle position for slider “my_slider” has been retrieved. */
```

### <a name="see-also"></a>参照

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_tickmarks_draw"></a>gx_slider_tickmarks_draw

スライダーの目盛りを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_slider_tickmarks_draw(GX_SLIDER *slider);
```

### <a name="description"></a>説明

このサービスでは、スライダーの目盛りが描画されます。 この関数は gx_slider_draw 関数によって内部的に呼び出されますが、カスタム スライダー描画関数を実装する可能性のあるアプリケーションで使用するために公開されています。

### <a name="parameters"></a>パラメーター

- **slider**: スライダー ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom slider draw function. */
VOID my_slider_draw(GX_SLIDER *slider)
{
    /* Add your own background draw here. */

    /* Call default tickmarks draw. */
    gx_slider_tickmarks_draw(slider);

    /* Call default slider needle draw. */
    gx_slider_needle_draw(slider);
}
```

### <a name="see-also"></a>参照

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_travel_get"></a>gx_slider_travel_get

スライダーの移動を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_slider_travel_get(
    GX_SLIDER *widget,
    GX_SLIDER_INFO *info,
    INT *return_min_travel, 
    INT *return_max_travel);
```

### <a name="description"></a>説明

このサービスにより、スライダーの移動が取得されます。

### <a name="parameters"></a>パラメーター

- **slider**: スライダー ウィジェット コントロール ブロック
- **info**: スライダー情報の構造体へのポインター。 **付録 I** には GX_SLIDER_INFO 構造体の定義が含まれています。
- **return_min_travel**: 最小移動値の宛先へのポインター</td>
- **return_max_travell**: 最大移動値の宛先へのポインター</td>

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) スライダーの移動の取得に成功しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE**: (0x22) スライダー情報が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Get travel information for for slider “my_slider”. */
status = gx_slider_travel_get(&my_slider, &info,
    &my_min_travel, &my_max_travel);

/* If status is GX_SUCCESS the travel max/min values for slider “my_slider” have been retrieved. */
```

### <a name="see-also"></a>参照

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_value_calculate"></a>gx_slider_value_calculate

スライダーの値を計算します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_slider_value_calculate(
    GX_SLIDER *slider, 
    GX_SLIDER_INFO *info,
    INT new_position);
```

### <a name="description"></a>説明

このサービスでは、スライダーの針の位置に基づいてスライダーの値が計算されます。 この関数は、ユーザーがスライダーの針を動かしたときに GUIX によって内部的に呼び出されますが、カスタム スライダー ウィジェットを実装するときにアプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **slider**: スライダー ウィジェット コントロール ブロック
- **info**: スライダー情報へのポインター。 **付録 I** には GX_SLIDER_INFO 構造体の定義が含まれています。
- **new_position**: スライダーの新しい位置

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) スライダーの値の計算に成功しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE**: (0x22) スライダー情報が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Calculate new value for slider “my_slider”. */
status = gx_slider_value_calculate(&my_slider,
    &my_slider.gx_slider_info, new_slider_position);

/* If status is GX_SUCCESS the slider value of “my_slider” has been calculated. */

```

### <a name="see-also"></a>参照

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_set

## <a name="gx_slider_value_set"></a>gx_slider_value_set

スライダーの値を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_slider_value_set(
    GX_SLIDER *slider,
    GX_SLIDER_INFO *info, 
    INT new_value);
```

### <a name="description"></a>説明

このサービスでは、スライダーの値が設定されます。 この API をアプリケーションから呼び出すと、プログラムによる制御の下でスライダーの針を移動できます。これにより、ユーザー入力でスライダーの針をドラッグする必要がなくなります。

### <a name="parameters"></a>パラメーター

- **slider**: スライダー ウィジェット コントロール ブロック
- **info**: スライダー情報の構造体へのポインター。 **付録 I** には GX_SLIDER_INFO 構造体の定義が含まれています
- **new_value**: スライダーの新しい値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) スライダーの値の設定に成功しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set new value for slider “my_slider”. */
status = gx_slider_value_set(&my_slider,
    &my_slider.gx_slider_info, new_value);

/* If status is GX_SUCCESS the new value has been set for slider “my_slider”. */
```

### <a name="see-also"></a>参照

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate

##  <a name="gx_sprite_create"></a>gx_sprite_create

スプライト ウィジェットを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_sprite_create(
    GX_SPRITE *sprite, GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_SPRITE_FRAME *frame_list,
    USHORT frame_count,
    ULONG style, USHORT sprite_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスでは、GX_SPRITE ウィジェットが作成されます。 スプライトは、アニメーションのようにピクセルマップのシーケンスを表示するために使用されます。また、マルチ状態のピクセルマップ表示ウィジェットとしても使用できます。

GX_SPRITE は GX_WIDGET から派生しており、すべての gx_widget API サービスがサポートされます。

GX_SPRITE ウィジェットでは、スプライト アニメーションを定義するために GX_SPRITE_FRAME 構造体の配列が必要です。 **付録 I** には GX_PRITE_FRAME 構造体の定義が含まれています

### <a name="parameters"></a>パラメーター

- **sprite**: スプライト ウィジェット コントロール ブロック
- **name**: 省略可能なスプライト名
- **parent**: 親ウィジェットへのポインター
- **frame_list**: GX_SPRITE_FRAME 構造体の配列
- **frame_count**: フレーム リスト配列内のエントリの数を指定します
- **style** スプライトのスタイル。 **付録 D** には、すべてのウィジェット用に事前に定義されている一般的なスタイルおよびウィジェット固有のスタイルが含まれています。
- **sprite_id**: スプライトのアプリケーション定義 ID
- **size**: スプライトの大きさ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) スプライトの作成に成功しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_ALREADY_CREATED**: (0x13) ウィジェットは既に作成されています
- **GX_INVALID_WIDGET**: (0x12) 親ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Create sprite “my_sprite”. */

status = gx_sprite_create(&my_sprite, “my_sprite”,
    &my_parent,
    sprite_frame_list, frame_count,
    GX_STYLE_SPRITE_AUTO|GX_STYLE_SPRITE_LOOP,
    ID_MY_SPRITE, &size);

/* If status is GX_SUCCESS the sprite “my_sprite” has been created. */
```

### <a name="see-also"></a>参照

- gx_sprite_start
- gx_sprite_stop
- gx_sprite_current_frame_set
- gx_sprite_frame_list_set

## <a name="gx_sprite_current_frame_set"></a>gx_sprite_current_frame_set

スプライト フレームを割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_sprite_current_frame_set(
    GX_SPRITE *sprite, 
    USHORT frame);
```

### <a name="description"></a>説明

このサービスにより、現在のスプライト フレームが割り当てられます。 GX_SPRITE ウィジェットが自動実行されていない場合は、それをプログラムによって制御された状態ライトとして使用できます。この場合、指定されたフレームのピクセルマップが表示されます。

### <a name="parameters"></a>パラメーター

- **sprite**: スプライト ウィジェット コントロール ブロック
- **frame**: 表示するスプライト フレーム

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 成功しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Assign frame number 3 as the current sprite frame */
status = gx_sprite_current_frame_set(&my_sprite, 3);

/* If status is GX_SUCCESS the sprite “my_sprite” will display frame index 3. */
```

### <a name="see-also"></a>参照

- gx_sprite_start
- gx_sprite_stop
- gx_sprite_create
- gx_sprite_frame_list_set

## <a name="gx_sprite_frame_list_set"></a>gx_sprite_frame_list_set

スプライト フレーム リストを割り当てまたは変更します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_sprite_frame_list_set(
    GX_SPRITE *sprite,
    GX_SPRITE_FRAME *frame_list,
    USHORT frame_count);
```

### <a name="description"></a>説明

このサービスを使用して、スプライト ウィジェットが作成された後にスプライト ウィジェットで使用されるフレーム リストを割り当てたり、再割り当てしたりすることができます。 スプライト フレーム リストの内容の詳細については、gx_sprite_create API のドキュメントを参照してください。

### <a name="parameters"></a>パラメーター

- **sprite**: スプライト ウィジェット コントロール ブロック
- **frame_list**: GX_SPRITE_FRAME 構造体の配列または GX_NULL (フレーム リストがない場合)。
- **frame_count**: フレーム リスト配列内のフレーム数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) スプライトのフレーム リストの設定に成功しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Assign framelist_1, which has 10 frames, to my_sprite */
status = gx_sprite_frame_list_set(&my_sprite, framelist_1, 10);

/* If status is GX_SUCCESS the new frame list is now associated with this sprite */
```

### <a name="see-also"></a>参照

- gx_sprite_current_frame_set
- gx_sprite_stop
- gx_sprite_create
- gx_sprite_create

## <a name="gx_sprite_start"></a>gx_sprite_start

スプライトの実行シーケンスを開始します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_sprite_start(
    GX_SPRITE *sprite, 
    USHORT frame);
```

### <a name="description"></a>説明

このサービスでは、スプライトの自動実行シーケンスが開始されます。 スプライト ウィジェットでは、最後のフレームに到達するまでスプライト フレームを順番に処理するか、または GX_SPRITE_LOOP スタイルが設定されている場合は継続的に実行します。

### <a name="parameters"></a>パラメーター

- **sprite**: スプライト ウィジェット コントロール ブロック
- **frame**: 最初に表示されるスプライト フレーム (通常はフレーム 0)

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) スプライトの実行が正常に開始されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Start the sprite “my_sprite” */
status = gx_sprite_start(&my_sprite, 0);

/* If status is GX_SUCCESS the sprite “my_sprite” will start running */
```

### <a name="see-also"></a>参照

- gx_sprite_current_frame_set
- gx_sprite_stop
- gx_sprite_create
- gx_sprite_frame_list_set

## <a name="gx_sprite_stop"></a>gx_sprite_stop

スプライトの実行シーケンスを停止します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_sprite_stop(GX_SPRITE *sprite);
```

### <a name="description"></a>説明

このサービスでは、スプライトの自動実行シーケンスを停止します。

### <a name="parameters"></a>パラメーター

- **sprite**: スプライト ウィジェット コントロール ブロック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) スプライトの実行が正常に停止されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Stop the sprite sequence */
status = gx_sprite_stop(&my_sprite);

/* If status is GX_SUCCESS the sprite “my_sprite” is stopped. */
```

### <a name="see-also"></a>参照

- gx_sprite_current_frame_set
- gx_sprite_start
- gx_sprite_create
- gx_sprite_frame_list_set

## <a name="gx_string_scroll_wheel_create"></a>gx_string_scroll_wheel_create

文字列型のスクロール ホイールを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_string_scroll_wheel_create(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent, 
    INT total_rows,
    GX_CONST GX_CHAR **string_list, 
    ULONG style,
    USHORT Id, 
    GX_CONST GX_RECTANGLE *size)
```

### <a name="description"></a>説明

このサービスにより、文字列型のスクロール ホイールが作成されます。

GX_STRING_SCROLL_WHEEL は GX_TEXT_SCROLL_WHEEL から派生しています。そのため、すべての gx_text_scroll_wheel API 関数は GX_STRING_SCROLL_WHEEL ウィジェットで使用される可能性があります。

アプリケーションでは、スクロール ホイールによって表示される文字列を定義する create 関数に、単純な文字列配列を渡すことができます。または、アプリケーションでは、string_list パラメーターとして GX_NULL を渡し、`gx_string_scroll_wheel_string_id_list_set()` API を呼び出して文字列 ID の配列を提供できます。 後者の方法を使用すると、アクティブなアプリケーションの言語が変更された場合、文字列スクロール ホイールでは、表示される文字列が自動的に切り替わります。

また、スクロール ホイールが作成された時点で、表示される文字列が静的に定義されていないか、認識されていない場合には、アプリケーションでは string list パラメーターとして GX_NULL を渡し、API 関数 gx_text_scroll_wheel_callback_set() を呼び出して、必要に応じてリアルタイムで表示される文字列を提供するコールバック関数を定義できます。

### <a name="parameters"></a>パラメーター

- **wheel**: 文字列スクロール ホイール コントロール ブロックのアドレス
- **name**: アプリケーション定義のウィジェット名
- **parent**: ホイールの親または GX_NULL
- **total_rows**: ユーザーに表示される合計行数
- **string_list**: 静的に定義された文字列配列または GX_NULL
- **style**: 必要なスタイル フラグ
- **Id**: アプリケーション定義のホイール スタイル フラグ
- **size**: 最初のスクロール ホイール サイズ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 文字列スクロール ホイールが正常に作成されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR (0x07)** : ポインターが無効です
- **GX_ALREADY_CREATED**: (0x13) ウィジェットは既に作成されています
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_CONST GX_CHAR *days[] = {
    “Sunday”,
    “Monday”,
    “Tuesday”,
    “Wednesday”,
    “Thursday”,
    “Friday”,
    “Saturday”
};

GX_STRING_SCROLL_WHEEL wheel;

/* Create the string scroll wheel. */

status = gx_string_scroll_wheel_create(&wheel, “Day Wheel”,
    root, 7, days,
    GX_STYLE_ENABLED|GX_STYLE_TEXT_CENTER|GX_STYLE_TRANSPARENT|
    GX_STYLE_WRAP|GX_STYLE_TEXT_SCROLL_WHEEL_ROUND,
    ID_SCROLL_WHEEL_DAY, &size);

/* If status is GX_SUCCESS the string scroll wheel has been created. */
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_id_list_set
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_string_scroll_wheel_event_process"></a>gx_string_scroll_wheel_event_process


文字列スクロール ホイールのイベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_string_scroll_wheel_string_id_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_RESOURCE_ID *string_id_list, 
    INT id_count);
```

### <a name="description"></a>説明

このサービスでは、指定された文字列スクロール ホイールのイベントが処理されます。 このサービスは、カスタム文字列スクロール ホイールのイベント処理関数によって既定のイベント ハンドラーとして呼び出されます。

### <a name="parameters"></a>パラメーター

- **wheel** 文字列スクロール ホイール制御ブロックへのポインター
- **event_ptr** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 文字列スクロール ホイールのイベント処理が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Call generic string scroll wheel event processing as part of custom event processing function. */

UINT custom_string_scroll_wheel_event_process(GX_STRING_SCROLL_WHEEL *wheel, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default string scroll wheel event processing */
        status = gx_string_scroll_wheel_event_process(wheel, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_id_list_set
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_string_scroll_wheel_string_id_list_set"></a>gx_string_scroll_wheel_string_id_list_set

文字列 ID の配列を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_string_scroll_wheel_string_id_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_RESOURCE_ID *string_id_list, INT id_count);
```

### <a name="description"></a>説明

このサービスは、文字列 ID の配列を文字列スクロール ホイール ウィジェットに割り当てます。 文字列が静的に定義され、ウィジェットが複数の言語で動作する必要がある場合は、文字列を文字列スクロール ホイールに割り当てるこの方法をお勧めします。 この API を使用する場合は、まず GX_NULL 文字列リストを使用してスクロール ホイール ウィジェットを作成する必要があります。

### <a name="parameters"></a>パラメーター

- **wheel**: 文字列スクロール ホイール制御ブロックのアドレス
- **string_id_list**: 文字列 ID の配列
- **id_count**: ID リストのサイズ。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 文字列 ID の配列が正常に設定されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE**: (0x22) ID リストのサイズが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_CONST RESOURCE_ID wheel_ids[] = {
    GX_STRING_ID_SUNDAY,
    GX_STRING_ID_MONDAY,
    GX_STRING_ID_TUESDAY,
    GX_STRING_ID_WEDNESDAY,
    GX_STRING_ID_THURSDAY,
    GX_STRING_ID_FRIDAY,
    GX_STRING_ID_SATURDAY
};

GX_STRING_SCROLL_WHEEL wheel;

/* Stop the sprite sequence */

status = gx_string_scroll_wheel_string_id_list_set(&wheel, wheel_ids, 7);

/* If status is GX_SUCCESS the ID list has been assigned. */
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_string_scroll_wheel_string_list_set"></a>gx_string_scroll_wheel_string_list_set

文字列の配列を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_string_scroll_wheel_string_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *string_list, 
    INT string_count);
```

### <a name="description"></a>説明

文字列の配列を文字列スクロール ホイール ウィジェットに割り当てます。 ウィジェットが最初に作成された後に表示される文字列を変更するために使用できます。

string_scroll_wheel では GX_STYLE_TEXT_COPY がサポートされていないため、この関数に渡される文字列の配列は、アプリケーションによって静的に定義される必要があることに注意してください。

### <a name="parameters"></a>パラメーター

- **wheel**: 文字列スクロール ホイール制御ブロックのアドレス
- **string_list**: 文字列ポインターの配列
- **string_count**: 文字列配列のサイズ。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) スクロール ホイールの文字列が正常に変更されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE**: (0x22) 文字列リストのサイズが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_CONST GX_CHAR *days[] = {
    “Sunday”,
    “Monday”,
    “Tuesday”,
    “Wednesday”,
    “Thursday”,
    “Friday”,
    “Saturday”
};

GX_STRING_SCROLL_WHEEL wheel;

/* Set the array of strings to the scroll wheel. */

status = gx_string_scroll_wheel_string_list_set(&wheel, days, 7);

/* If status is GX_SUCCESS the string array has been assigned. */
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_studio_widget_create"></a>gx_studio_widget_create

Studio で生成された specifications ファイルで定義されたウィジェットを作成します

### <a name="prototype"></a>プロトタイプ

```C
GX_WIDGET *gx_studio_widget_create(
    GX_BYTE *control,
    GX_CONST GX_STUDIO_WIDGET *definition, 
    GX_WIDGET *parent);
```

### <a name="description"></a>説明

このサービスは、GUIX Studio で生成された specifications ファイル内で定義されているウィジェット仕様を使用して、ウィジェットとそのウィジェットの子を作成します。 この関数では、同様の関数 `gx_studio_named_widget_create()` の "名前による" 検索が回避されます。

GX_STUDIO_WIDGET 構造体は、GUIX Studio によって生成されるアプリケーション仕様ヘッダー ファイルで定義されています。

静的に割り当てられているウィジェットの場合、ウィジェット制御ブロックは、生成された specifications.c ファイルで定義され、GUIX Studio 内で定義されたウィジェット名が付けられます。 動的に割り当てられるウィジェットの場合、アプリケーションから GX_NULL をウィジェット制御ブロック アドレスとして渡す必要があり、この関数によって、`gx_system_memory_allocate()` 関数 (これもアプリケーションによって定義および提供されます) を使用したウィジェット制御ブロックの動的な割り当てが試行されます。

生成された specifications ファイル内の GUIX Studio ウィジェット定義をアプリケーションで直接参照するには、GUI Studio コード ジェネレーターで使用されている名前付け規則に従う必要があります。 specifications.c ファイル内に生成される GX_STUDIO_WIDGET 構造体は、必ず <widget_name>_define という規則に従って名前が付けられます。ここで <widget_name> フィールドは、ウィジェットが子ウィジェットの子である場合、複数回繰り返されます。

### <a name="parameters"></a>パラメーター

- **control** ウィジェット制御ブロックへのポインター、または動的に割り当てられる場合は GX_NULL。
- **definition** Studio で生成されたウィジェット定義の構造体
- **parent** ウィジェットの親へのポインター (存在する場合)

### <a name="return-values"></a>戻り値

作成されたウィジェット制御ブロックへのポインター。作成に失敗した場合は GX_NULL。

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Create the widget “playlist_screen”, which is statically allocated. */

widget = gx_studio_widget_create(&playlist_screen,
    &playlist_screen_define,
    root_window);

/* If widget != GX_NULL the widget was created. */

/* create the widget “songs_screen”, which is dynamically allocated */

widget = gx_studio_widget_create(GX_NULL,
    &songs_screen_define, root_window);
```

### <a name="see-also"></a>参照

- gx_studio_named_widget_create

## <a name="gx_studio_named_widget_create"></a>gx_studio_named_widget_create

Studio で生成された specifications ファイルで定義されたウィジェットを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT *gx_studio_named_widget_create(
    char *name, 
    GX_WIDGET *parent,
    GX_WIDGET **new_widget);
```

### <a name="description"></a>説明

このサービスは、GUIX Studio で生成された specifications ファイル内で定義されているウィジェット仕様を使用して、ウィジェットとそのウィジェットの子を作成します。

この API 関数を使用して、GUIX Studio アプリケーション内で指定されたスクリーン名をウィジェット定義識別子として使用するトップレベルのスクリーンを作成します。

### <a name="parameters"></a>パラメーター

- **name**: GUIX Studio アプリケーション内で定義されているスクリーン名。
- **parent**: ウィジェットの親へのポインター (存在する場合)
- **new_widget**: 作成されたウィジェット ポインターを返す場所

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 成功しました
- **GX_FAILURE**: (0x11) 指定されたウィジェットは見つかりませんでした

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Create the widget named “child_popup”,
   which is a child of the top-level screen “main_screen”. */

GX_WIDGET *menu_screen;

status = gx_studio_named_widget_create(“main_menu”,
    &root_window, &menu_screen);

/* If status == GX_SUCCESS the screen was created
   and linked to the root window. */
```

### <a name="see-also"></a>参照

- gx_studio_widget_create

## <a name="gx_studio_display_configure"></a>gx_studio_display_configure

GUIX Studio プロジェクトで定義されているディスプレイを構成します

### <a name="prototype"></a>プロトタイプ

```C
UINT *gx_studio_display_configure(
    USHORT display,
    UINT (*driver)(GX_DISPLAY *),
    USHORT language, 
    USHORT theme,
    GX_WINDOW_ROOT **return_root);
```

### <a name="description"></a>説明

このサービスは、すぐ使用できるように GX_DISPLAY を初期化します。 この関数は、GX_DISPLAY 制御ブロックの初期化、ディスプレイに合わせたキャンバスの作成、キャンバスのルート ウィンドウの作成を行う各関数を統合したものです。 この関数は、ディスプレイが初期化された後に要求される、言語とリソースのテーマのインストールも行います。

この関数には、ディスプレイを使用できるように準備するために通常必要なプログラミング作業が統合されています。 この関数により、gx_display_create ()、gx_display_color_table_set、gx_display_font_table_set、gx_display_pixelmap_table_set、gx_system_language_table_set、gx_system_active_language_set、gx_system_scroll_appearance_set、gx_canvas_create、gx_window_root_create の各関数が呼び出されます。これらのすべてまたは一部がアプリケーション プログラムで必要になります。

### <a name="parameters"></a>パラメーター

- **display**: ディスプレイ テーブルにインデックスを付けます。これは、Studio プロジェクト ファイル内のディスプレイ定義に対応します。
- **driver**: ドライバー初期化関数を表示するポインター。 この関数は、GX_DISPLAY 制御ブロックの間接的な関数ポインターの初期化、および必要なハードウェアのセットアップ実行のために呼び出されます。
- **language**: 初期の言語テーブルのインデックス
- **language**: 初期のテーマのインデックス
- **root**: ルート ウィンドウ アドレスを返す変数へのポインター、または GX_NULL。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 成功しました
- **GX_FAILURE**: (0x11) ディスプレイを初期化できませんでした

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Create the widget named “child_popup”, which is a child of the
   top-level screen “main_screen”. */

GX_WIDGET *menu_screen;

status = gx_studio_display_configure(MAIN_DISPLAY,
    my_driver_setup, LANGUAGE_ENGLISH, DEFAULT_THEME, GX_NULL);

/* If status == GX_SUCCESS the display was initialized, a canvas was
created for the display, a root window was created for the canvas, and
the requested language and theme have been installed.
*/
```

### <a name="see-also"></a>参照

- gx_display_create
- gx_display_color_table_set
- gx_display_font_table_set
- gx_display_pixelmap_table_set
- gx_system_language_table_set
- gx_system_active_language_set
- gx_system_scroll_appearance_set
- gx_canvas_create
- gx_window_root_create

## <a name="gx_system_active_language_set"></a>gx_system_active_language_set

アクティブな言語を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_active_language_set(GX_UBYTE language);
```

### <a name="description"></a>説明

このサービスは、現在の言語を設定します。 言語インデックスは、アプリケーション文字列テーブルの列数よりも少なくする必要があります。 gx_display_string_table_get が採用されたため、この関数は非推奨となりました。 すべての新しいアプリケーションで gx_display_active_langauge_set を使用してください。

### <a name="parameters"></a>パラメーター

- **language**: リソース ヘッダー ファイルで定義されている言語インデックス。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) アクティブな言語が正常に設定されました
- **GX_CALLER_ERROR**: ** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: ** (0x07) ポインターが無効です
- **GX_INVALID_VALUE**: ** (0x22) 言語インデックスが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Set active language and mark widget canvas as dirty. */
status = gx_system_active_language_set(ID_LANGUAGE_ENGLISH);

/* If status is GX_SUCCESS the active language has been assigned. */
```

### <a name="see-also"></a>参照

- gx_display_language_table_set
- gx_display_active_langauge_set
- gx_display_string_get

## <a name="gx_system_animation_get"></a>gx_system_animation_get

システム プールからアニメーション制御ブロックを取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_animation_get(GX_ANIMATION **animation);
```

### <a name="description"></a>説明

このサービスを使用すると、アニメーション制御ブロックを、gx_system コンポーネントによって管理されている当該の制御ブロックのプールから取得できます。 アニメーション制御ブロック プールおよび関連する API サービスは、定数 GX_ANIMATION_POOL_SIZE が値 0 で定義されている場合にのみ提供されます。 この値の既定の設定は 6 です。つまり、システム アニメーション制御ブロック プールには、その数の GX_ANIMATION 制御ブロックが含まれます。

この API を使用して割り当てられたアニメーション制御ブロックは、アニメーションが最後まで実行された場合、空きプールに自動的に返されます。 アニメーションが gx_animation_stop を使用して停止された場合、または何らかの返されたエラーが原因で開始できなかった場合は、gx_system_animation_free を使用して、アニメーション制御ブロックをアニメーションから空きプールに返す必要があります。

### <a name="parameters"></a>パラメーター

- **animation**: GX_ANIMATION ポインターを受け取るポインターのアドレス。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) アニメーション制御ブロックが正常に取得されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) アニメーション ポインターが無効です
- **GX_OUT_OF_ANIMATIONS**: (0x31) システム アニメーション プールを使い果たしました

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_ANIMATION *animation;

UINT status = gx_system_animation_get(&animation);

if (status == GX_SUCCESS)
{
    gx_animation_start(animation, animation_info);
}
```

### <a name="see-also"></a>参照

- gx_animation_create
- gx_animation_start
- gx_animation_stop
- gx_system_animation_free

## <a name="gx_system_animation_free"></a>gx_system_animation_free

アニメーション制御ブロックをシステム プールに返します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_animation_free(GX_ANIMATION *animation);
```

### <a name="description"></a>説明

このサービスを使用して、アニメーション制御ブロックをシステム プールに返すことができます。 アニメーション制御ブロック プールおよび関連する API サービスは、定数 GX_ANIMATION_POOL_SIZE が値 0 で定義されている場合にのみ提供されます。 この値の既定の設定は 6 です。つまり、システム アニメーション制御ブロック プールには、その数の GX_ANIMATION 制御ブロックが含まれます。

gx_system_animation_get() を使用して割り当てられたアニメーション制御ブロックは、アニメーションが最後まで実行された場合、空きプールに自動的に返されます。 空きプールに既に返されているアニメーション制御ブロックを空きープールに返そうとしても、影響はありません。

アニメーションが gx_animation_stop を使用して停止されたか、何らかの返されたエラーが原因で開始できなかった場合、gx_system_animation_get() を使用して取得されたアニメーション制御ブロックは、gx_system_animation_free() を使用して、アプリケーションから空きプールに返す必要があります。

アニメーションが空きプールに返されるには、IDLE 状態になっている必要があります。 アニメーションは、開始されていない場合、停止されている場合、または最後まで実行された場合、IDLE 状態になります。

### <a name="parameters"></a>パラメーター

- **animation**: GX_ANIMATION 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) アニメーション ブロックが正常に解放されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) アニメーション ポインターが無効です
- **GX_INVALID_ANIMATION**: (0x32) アニメーションが IDLE でないか、システム プールから割り当てられていません

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_ANIMATION *animation;

UINT status = gx_system_animation_get(&animation);

if (status == GX_SUCCESS)
{
    status = gx_animation_start(animation, animation_info);

    if (status != GX_SUCCESS)
    {
        /* animation did not start, return it to the free pool */
        gx_system_animation_free(animation);
    }
}
```

### <a name="see-also"></a>参照

- gx_animation_create
- gx_animation_start
- gx_animation_stop
- gx_system_animation_get

## <a name="gx_system_bidi_text_disable"></a>gx_system_bidi_text_disable

動的な双方向のテキストのサポートを無効にします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_bidi_text_disable(VOID);
```

### <a name="description"></a>説明

このサービスは、動的な双方向のテキストのサポートを無効にします。 GUIX ライブラリを構築するときに、GX_DYNAMIC_BIDI_TEXT_SUPPORT を定義する必要があります。また、これが必要になるのは、BiDi 文字列データの実行時の並べ替えが必要な場合のみです。 ほとんどのアプリケーションは、GUIX Studio を使用して、正しく並べ替えられた BiDi テキスト文字列を生成します。

### <a name="parameters"></a>パラメーター

**なし**

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) bidi テキストのサポートが正常に無効になりました

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* GX_DYNAMIC_BIDI_TEXT_SUPPORT is defined. */

/* Diable bidi text support. */
status = gx_system_bidi_text_disable();

/* If status is GX_SUCCESS, bidi text support was disabled. */
```

### <a name="see-also"></a>参照

- gx_system_bidi_text_enable

## <a name="gx_system_bidi_text_enable"></a>gx_system_bidi_text_enable

動的な bidi テキストのサポートを有効にします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_bidi_text_enable(VOID);
```

### <a name="description"></a>説明

このサービスは、動的な双方向のテキストのサポートを有効にします。 GUIX ライブラリを構築するときに、GX_DYNAMIC_BIDI_TEXT_SUPPORT を定義する必要があります。また、これが必要になるのは、BiDi 文字列データの実行時の並べ替えが必要な場合のみです。 ほとんどのアプリケーションは、GUIX Studio を使用して、正しく並べ替えられた BiDi テキスト文字列を生成します。

### <a name="parameters"></a>パラメーター

**なし**

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) bidi テキストのサポートが正常に有効になりました

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* GX_DYNAMIC_BIDI_TEXT_SUPPORT is defined. */

/* Enable bidi text support. */
status = gx_system_bidi_text_enable();

/* If status is GX_SUCCESS, bidi text support was enabled. */
```

### <a name="see-also"></a>参照

- gx_system_bidi_text_disable

## <a name="gx_system_canvas_refresh"></a>gx_system_canvas_refresh

ダーティ キャンバスをすべて更新します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_canvas_refresh(VOID);
```

### <a name="description"></a>説明

このサービスは、すべてのダーティ ウィジェットおよびキャンバスの即時再描画を強制的に実行します。 このサービスは通常、GUIX システム コンポーネントによって内部的に呼び出されますが、システムの即時再描画操作を強制的に実行するためにアプリケーションから呼び出すことができます。

### <a name="parameters"></a>パラメーター

**なし**

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) アニメーション ブロックが正常に解放されました
- **GX_INVALID_CANVAS**: (0x20) キャンバスが作成されていません
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Force immediate redraw operation. */
status = gx_system_canvas_refresh();

/* If status is GX_SUCCESS, canvas has been redraw. */
```

### <a name="see-also"></a>参照

- gx_system_active_language_set
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_dirty_mark"></a>gx_system_dirty_mark

領域をダーティとしてマークします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_dirty_mark(GX_WIDGET *widget);
```

### <a name="description"></a>説明

このサービスは、このウィジェットの領域をダーティとしてマークします。 これにより、システム イベントの処理が完了したときに再描画するためにウィジェットが効果的にキューに登録されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェット制御ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ウィジェットがダーティと正常にマークされました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Mark widget “my_widget” as dirty. */
status = gx_system_dirty_mark(&my_widget);

/* If status is GX_SUCCESS the area associated
   with “my_widget” has been marked as dirty. */
```

### <a name="see-also"></a>参照

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_dirty_partial_add"></a>gx_system_dirty_partial_add

一部の領域をダーティとしてマークします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_dirty_partial_add(
    GX_WIDGET *widget,
    GX_RECTANGLE *dirty_area);
```

### <a name="description"></a>説明

このサービスは、このウィジェットの部分的な領域をダーティとしてマークします。 これにより、システム イベントの処理が完了したときに GUIX キャンバスの更新操作によって再描画するためにウィジェットがキューに登録されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェット制御ブロックへのポインター
- **dirty_area**: ダーティとしてマークするウィジェットのダーティ領域

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 部分的なダーティ領域のマーク付けが成功しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です
- **GX_INVALID_SIZE**: (0x19) ダーティ領域のサイズが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Mark widget “my_widget” partial area as dirty. */

status = gx_system_dirty_partial_add(&my_widget,
    &partial_area);

/* If status is GX_SUCCESS the partial area “partial_area”
associated with “my_widget” has been marked as dirty. */
```

### <a name="see-also"></a>参照

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_draw_context_get"></a>gx_system_draw_context_get

描画コンテキストを取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_draw_context_get(GX_DRAW_CONTEXT **current_context);
```

### <a name="description"></a>説明

このサービスは、現在の描画コンテキストへのポインターを返します。

### <a name="parameters"></a>パラメーター

- **current_context**: 現在の描画コンテキスト ポインターの宛先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 現在のコンテキストの取得に成功しました
- **GX_PTR_ERROR**: (0x07) ポインターが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_DRAW_CONTEXT *current_context;

/* Get current drawing context. */

status = gx_system_draw_context_get(&current_context);

/* If status is GX_SUCCESS the current drawing context
   is contained in “current_context”. */
```

### <a name="see-also"></a>参照

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_event_fold"></a>gx_system_event_fold

イベントを送信します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_event_fold(GX_EVENT *event);
```

### <a name="description"></a>説明

このサービスは、GUIX イベント キューで同じ種類のイベントを探します。 同じ種類のイベントが存在する場合、イベント ペイロードが新しいイベントに合わせて更新されます。 一致するイベントが見つからない場合は、イベント キューの最後に新しいイベントを追加するために、gx_system_event_send 関数が呼び出されます。

この関数は、イベント キューが複数の PEN_DRAG イベントでいっぱいにならないようにするために、高速タッチ入力ドライバーでよく使用されます。 同じ種類の複数のイベントが GUIX イベント キューに追加されないようにするために、この関数をアプリケーションから呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **event**: イベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) イベントの送信が成功しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_EVENT my_event;

memset(&my_event, 0, sizeof(GX_EVENT));

my_event.gx_event_type = GX_EVENT_PEN_DOWN;

my_event.gx_event_payload.gx_event_pointdata.gx_point_x = 100;
my_event.gx_event_payload.gx_event_pointdata.gx_point_y = 200;

/* Send “my_event” for processing. */
status = gx_system_event_fold(&my_event);

/* If status is GX_SUCCESS the event has been sent for processing. */
```

### <a name="see-also"></a>参照

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_event_send"></a>gx_system_event_send

イベントを送信します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_event_send(GX_EVENT *event);
```

### <a name="description"></a>説明

このサービスは、指定されたイベントを GUIX システム イベント キューに送信します。 新しいイベントは、キューの最後に配置されます。

### <a name="parameters"></a>パラメーター

- **event**: イベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) イベントの送信が成功しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Send “new_event” for processing. */

GX_EVENT new_event;

new_event.gx_event_target = widget ->gx_widget_parent;
new_event.gx_event_type = MY_EVENT_TYPE;

/* Set optional param. */
new_event.gx_event_payload.xxxx = yyyy
new_event.gx_event_sender = widget->gx_widget_id;

/* Push the event to event pool. */
status = gx_system_event_send(&new_event);

/* If status is GX_SUCCESS the event has been sent for processing. */
```

### <a name="see-also"></a>参照

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_focus_claim"></a>gx_system_focus_claim

フォーカスを要求します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_focus_claim(GX_WIDGET *widget);
```

### <a name="description"></a>説明

このサービスは、指定されたウィジェットのフォーカスを要求します。 ウィジェットは、以前にフォーカスされていなかった場合、GX_EVENT_FOCUS_GAINED イベントを受信します。

### <a name="parameters"></a>パラメーター

- **widget**: フォーカスを要求するウィジェット制御ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) フォーカスの要求に成功しました
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_NO_CHANGE**: (0x08) ウィジェットは既にフォーカスされています
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Claim focus for widget “my_widget”. */
status = gx_system_claim_focus(&my_widget);

/* If status is GX_SUCCESS the focus has been claimed for
   “my_widget”. */
```

### <a name="see-also"></a>参照

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_initialize"></a>gx_system_initialize

GUIX を初期化します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_initialize(VOID);
```

### <a name="description"></a>説明

このサービスは、GUIX を初期化します。 このサービスは、他の GUIX API サービスの前に呼び出す必要があり、システムの起動時に 1 回だけ呼び出す必要があります。

### <a name="parameters"></a>パラメーター

- **なし**

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) システムが正常に初期化されました
- **GX_SYSTEM_ERROR**: (0xFE) GX_EVENT 制御ブロック サイズが無効であるか、キューまたはミューテックスまたはスレッドの作成のイベントが失敗しました。
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Initialize GUIX. */
status = gx_system_initialize();

/* If status is GX_SUCCESS, GUIX has been initialized. */
```

### <a name="see-also"></a>参照

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_language_table_get"></a>gx_system_language_table_get

アクティブな言語テーブルを取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_language_table_get( 
    GX_CHAR ****language_table,
    GX_UBYTE *languages_count, 
    UINT *string_count);
```

### <a name="description"></a>説明

このサービスは、アクティブな言語テーブルを取得します。 gx_display_language_table_get が採用されたため、この関数は非推奨となりました。 すべての新しいアプリケーションで gx_display_language_table_get を使用してください。

### <a name="parameters"></a>パラメーター

- **language_table**: 言語テーブルを返すポインターのアドレス。
- **languages_count**: テーブルの列数を返す変数のアドレス。
- **string_count**: テーブルの行数を返すポインターのアドレス。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) アクティブな言語テーブルを正常に取得しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_CHAR ***language_table;

GX_UBYTE language_count;

UINT string_count;

/* Retrieve the language table */

status = gx_system_language_table_get(&language_table,
    &language_count, &string_count);
```

### <a name="see-also"></a>参照

- gx_display_language_table_get
- gx_display_language_table_set

## <a name="gx_system_language_table_set"></a>gx_system_language_table_set

アクティブな言語テーブルを割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_language_table_set(
    GX_CHAR ***language_table,
    GX_UBYTE languages_count, 
    UINT string_count);
```

### <a name="description"></a>説明

このサービスは、アクティブな言語テーブルをインストールします。 gx_display_language_table_set が採用されたため、この関数は非推奨となりました。 すべての新しいアプリケーションでは gx_display_language_table_set を使用してください。

### <a name="parameters"></a>パラメーター

- **language_table**: 言語テーブルへのポインター。
- **languages_count**: テーブル内の言語の数。
- **string_count**: 文字列テーブルの行数。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 言語テーブルが正常に設定されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Retrieve the language table */

status = gx_system_language_table_set(language_table,
    language_count, string_count);
```

### <a name="see-also"></a>参照

- gx_display_language_table_set
- gx_display_language_table_get
- gx_display_active_language_set

## <a name="gx_system_memory_allocator_set"></a>gx_system_memory_allocator_set

メモリの割り当て、割り当て解除のために関数を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_memory_allocator_set(VOID *(allocate)(ULONG size),
    VOID(*release)(VOID *));
```

### <a name="description"></a>説明

このサービスは、動的なメモリ割り当てと割り当て解除のために、アプリケーションが提供するコールバック関数を割り当てます。

動的メモリ割り当てを使用する GUIX サービスがアプリケーションで必要ない場合は、このサービスを呼び出す必要はありません。

このサービスを使用する場合は、GUIX サービス ポインターをクリアする gx_system_initialize() の後、動的なメモリ割り当てを使用する必要がある GUIX サービスの前に呼び出す必要があります。

実行時のメモリ割り当ておよび割り当て解除サービスを必要とする GUIX サービスには、次のものがあります。

- 外部ストレージから GUIX ランタイム環境へのバイナリ リソースの読み込み。
- ソフトウェア ランタイム jpeg 画像デコーダー。
- ソフトウェア ランタイム png 画像デコーダー。
- GX_STYLE_TEXT_COPY でのテキスト ウィジェットの使用。
- 実行時のピクセルマップのサイズ変更および回転の各ユーティリティ関数。
- 実行時のスクリーンおよびウィジェットの制御ブロックの割り当て。

### <a name="parameters"></a>パラメーター

- **allocator**: メモリ アロケーター関数
- **release**: メモリ解放関数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) メモリ割り当て関数が正常に割り当てられました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

次の例では、ThreadX バイト プールを使用して、スレッドセーフな動的メモリ割り当てとメモリ割り当て解除サービスを実装しています。

```C
TX_BYTE_POOL memory_pool;

#define SCRATCHPAD_SIZE (1024 * 4)

ULONG scratchpad[SCRATCHPAD_SIZE];

/* define memory allocation service */

VOID *memory_allocate(ULONG size)
{
    VOID *memptr;

    if (tx_byte_allocate(&memory_pool, &memptr, size, TX_NO_WAIT) == TX_SUCCESS)
    {
        return memptr;
    }
    return NULL;
}

/* define memory de-allocation service */
void memory_free(VOID *mem)
{
    tx_byte_release(mem);
}

/* create byte pool and install our dynamic memory services with GUIX
*/

VOID tx_application_define(void *first_unused_memory)
{
    /* create byte pool for GUIX to use */
    tx_byte_pool_create(&memory_pool, "scratchpad", scratchpad,
        SCRATCHPAD_SIZE * sizeof(ULONG));

    guix_setup();

    /* install our memory allocator and de-allocator */
    gx_system_memory_allocator_set(memory_allocate, memory_free);
}
```

### <a name="see-also"></a>参照

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_pen_configure"></a>gx_system_pen_configure

ペンの構成を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_pen_configure(GX_PEN_CONFIGURATION *pen_configuration);
```

### <a name="description"></a>説明

このサービスは、ペンの構成を設定して、ペンの速度と距離のパラメーターを制御します (これらはGX_EVENT_FLICK イベントの種類の生成をトリガーするために使用されます)。

GX_PEN_CONFIGURATION の gx_pen_configuration_min_drag_dist メンバーは固定小数点データ型であるため、GX_FIXED_VAL_MAKE(値) を使用して INT から GX_FIXED_VAL に変換する必要があります。 たとえば、最小ドラッグ距離をティックあたり 0.5 ピクセルに設定する場合は、gx_pen_configuration_min_drag_dist を `GX_FIXED_VAL_MAKE(1) / 2` に設定する必要があります。

GUIX リリース 5.4.0 以前では、GX_PEN_CONFIGURATION の gx_pen_configuration_min_drag_dist メンバーは GX_FIXED_VAL 型ではなく (INT << 8) 型でした。 5\.4.0 バージョン GUIX ライブラリを使用しているプロジェクトでこの API を使用している場合は、GUIX ライブラリをビルドするときに、min_drag_dist パラメーターを変更するか、#define GUIX_5_4_0_COMPATIBILITY を指定する必要があります。

### <a name="parameters"></a>パラメーター

- **pen_configuration** ペンの構成の構造へのポインター。 **付録 I** には GX_PEN_CONFIGURATION 構造の定義が含まれています

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ペンの構成が正常に設定されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Define pen configuration, set minimum drag distance to 0.5 pixel
per tick, maximum pen speed to 10 ticks. That means GUIX will trigger
a vertical or horizontal flick event if the drag time is smaller than
10 ticks and the drag distance is bigger than 0.5 * drag_ticks. */

GX_PEN_CONFIGURATION pen_configuration;

#if defined(GUIX_5_4_0_COMPATIBILITY)
Pen_configuration.gx_pen_configuration_min_drag_dist = (1 << 8)/ 2;
#else
pen_configuration.gx_pen_configuration_min_drag_dist = GX_FIXED_VAL_MAKE(1) / 2;
#endif

pen_configuration.gx_pen_configuration_max_pen_speed_ticks = 10;

/* Set the pen configuration. */
status = gx_system_pen_configure(&pen_configuration);

/* If status is GX_SUCCESS the touch configure has been set. */
```

## <a name="gx_system_screen_stack_create"></a>gx_system_screen_stack_create

システム画面スタックを作成して初期化します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_screen_stack_create(
    GX_WIDGET **memory, 
    INT size);
```

### <a name="description"></a>説明

このサービスは、システム画面スタックに使用されるメモリ プールを定義します。 システム画面スタックは、アプリケーションでアプリケーション画面フローの外観を管理するために使用できるオプションの関数です。

アプリケーションで画面スタック サービスを使用する場合は、まず、画面スタック メモリ領域を設定するために gx_system_screen_stack_create 関数を呼び出す必要があります。

### <a name="parameters"></a>パラメーター

- **memory**: 予約されたメモリ ブロックへのポインター。
- **size**: 予約されたメモリ ブロックのサイズ (バイト単位)。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 正常に作成しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
#define SCREEN_STACK_DEPTH 8
GX_WIDGET *screen_stack[SCREEN_STACK_DEPTH * 2];

UINT status;

/* Get the scrollbar appearance. */

status = gx_system_screen_stack_create(screen_stack,
    sizeof(GX_WIDGET *) * SCREEN_STACK_DEPTH * 2);

/* If status is GX_SUCCESS the system screen stack is initialized
and ready for use. */
```

### <a name="see-also"></a>参照

- gx_system_screen_stack_get
- gx_system_screen_stack_pop
- gx_system_screen_stack_push
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_get"></a>gx_system_screen_stack_get

最上位の画面スタック ポインターをポップします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_screen_stack_get(
    GX_WIDGET **popped_parent,
    GX_WIDGET **popped_screen);
```

### <a name="description"></a>説明

この関数は、最上位の画面スタック ポインターをポップし、それらのポインターを呼び出し元に返します。 この関数は gx_system_screen_stack_pop() とは異なり、ポップされた画面は前の親に自動的に再アタッチされません。 代わりに、ポインターがスタックからポップされ、呼び出し元に返されます。これにより、呼び出し元は、返された画面を必要に応じてをアタッチしたり破棄したりできます。

### <a name="parameters"></a>パラメーター

- **popped_parent**: 親ウィジェットのポインターを格納する場所。
- **popped_screen**: ポップされた画面ポインターを格納する場所。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 画面スタック ポインターを正常に取得しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_FAILURE**: (0x10) 無効または空の画面スタック

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
UINT status;

GX_WIDGET *parent_screen;

GX_WIDGET *popped_screen;

/* Pop a screen stack entry. */
status = gx_system_screen_stack_get(&parent_screen, &popped_screen);

/* If status is GX_SUCCESS, parent_screen and
popped_screen hold the topmost screen stack pointers. */
```

### <a name="see-also"></a>参照

- gx_system_screen_stack_create
- gx_system_screen_stack_pop
- gx_system_screen_stack_push
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_pop"></a>gx_system_screen_stack_pop

システム画面スタックから最上位のエントリをポップします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_screen_stack_pop();
```

### <a name="description"></a>説明

この関数は、画面スタックの最上位のエントリをポップし、ポップされた画面をポップされた親ウィジェットに自動的にアタッチします。

### <a name="parameters"></a>パラメーター

"**なし**"

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 画面スタック ポインターを正常に取得しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_FAILURE**: (0x10) 無効または空の画面スタック

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
UINT status;

/* Pop a screen stack entry. */
status = gx_system_screen_stack_pop();

/* If status is GX_SUCCESS, the topmost screen stack entry has been
popped from the stack and re-attached to the previous parent. */
```

### <a name="see-also"></a>参照

- gx_system_screen_stack_get
- gx_system_screen_stack_create
- gx_system_screen_stack_push
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_push"></a>gx_system_screen_stack_push

ウィジェットと親ポインターを画面スタックにプッシュする

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_screen_stack_push(GX_WIDGET *screen)
```

### <a name="description"></a>説明

このサービスは、(通常はトップレベル画面である) 指定されたウィジェットへのポインターを画面スタックに配置します。 ウィジェットに親がある場合、親からデタッチされます。 親ウィジェットのポインターも画面スタックにプッシュされます。 親ウィジェットは NULL でもかまいません。つまり、表示されていないか親にアタッチされていない画面は、画面スタックにプッシュされる可能性があります。 親を持たないウィジェットが画面スタックにプッシュされた場合は、ポップされたウィジェットを前の親に再アタッチしようとする screen_stack_pop() API を使用するのではなく、screen_stack_get() API を使用してプッシュ画面ポインターを取得する必要があります。

### <a name="parameters"></a>パラメーター

- **screen**: 画面スタックにプッシュされるウィジェットへのポインター。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) スクロールバーの外観を正常に取得しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Get the scrollbar appearance. */
status = gx_system_screen_stack_push(window);

/* If status is GX_SUCCESS, the widget pointed to by “window” has
been pushed to the screen stack, along with the widget’s parent
ponter. */
```

### <a name="see-also"></a>参照

- gx_system_screen_stack_get
- gx_system_screen_stack_pop
- gx_system_screen_stack_create
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_reset"></a>gx_system_screen_stack_reset

システム画面スタックをリセットします

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_screen_stack_reset();
```

### <a name="description"></a>説明

この関数は、システム画面スタックからすべてのエントリを削除します。 スタックからポップされた画面に、GUIX Studio によってコントロール ブロックが動的に割り当てられている場合は、それらのコントロール ブロックのメモリが解放されます。

### <a name="parameters"></a>パラメーター

"**なし**"

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) スクロールバーの外観を正常に取得しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Get the scrollbar appearance. */
status = gx_system_screen_stack_reset();

/* If status is GX_SUCCESS the system screen stack has been cleared
of entries. */
```

### <a name="see-also"></a>参照

- gx_system_screen_stack_get
- gx_system_screen_stack_pop
- gx_system_screen_stack_push
- gx_system_screen_stack_create

## <a name="gx_system_scroll_appearance_get"></a>gx_system_scroll_appearance_get

スクロールの外観を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_scroll_appearance_get(
    ULONG style,
    GX_SCROLLBAR_APPEARANCE *return_appearance);
```

### <a name="description"></a>説明

このサービスは、スクロールバーの外観を取得します。

### <a name="parameters"></a>パラメーター

- **style**: スクロールバーのスタイル: `GX_SCROLLBAR_HORIZONTAL` または `GX_SCROLLBAR_VERTICAL`
- **return_appearance**:外観の宛先へのポインター。 **付録 I** には GX_SCROLLBAR_APPERANCE の定義が含まれています

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) スクロールバーの外観を正常に取得しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_SCROLLBAR_APPEARANCE my_appearance;

/* Get the scrollbar appearance. */

status = gx_system_scroll_appearance_get(style, &my_appearance);

/* If status is GX_SUCCESS “my_appearance” now contains the scroll
appearance. */
```

### <a name="see-also"></a>参照

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_set
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_scroll_appearance_set"></a>gx_system_scroll_appearance_set

スクロールの外観を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_scroll_appearance_set(
    ULONG style,
    GX_SCROLLBAR_APPEARANCE *appearance);
```

### <a name="description"></a>説明

このサービスは、既定のスクロールの外観を設定します。 スクロールを作成するとき、アプリケーションでカスタム バージョンが指定されない限り、この外観構造が使用されます。

### <a name="parameters"></a>パラメーター

- **style**: スクロールスタイル `GX_SCROLLBAR_HORIZONTAL` または `GX_SCROLLBAR_VERTICAL`
- **appearance**: さまざまなスクロールバーの外観属性で初期化された外観構造へのポインター。 GX_SCROLLBAR_APPEARANCE 構造の定義については、**付録 I** を参照してください。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) スクロールの外観セットが正常に設定されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_SCROLLBAR_APPEARANCE my_appearance;

memset(&my_appearance, 0, sizeof(GX_SCROLLBAR_APPEARANCE));

my_appearance.gx_scroll_width = 20;
my_appearance.gx_scroll_thumb_width = 18;

my_appearance.gx_scroll_thumb_color = GX_COLOR_ID_SCROLL_BUTTON;
my_appearance.gx_scroll_thumb_border_color = GX_COLOR_ID_SCROLL_BUTTON;
my_appearance.gx_scroll_button_color = GX_COLOR_ID_SCROLL_BUTTON;
my_appearance.gx_scroll_thumb_travel_min = 20;
my_appearance.gx_scroll_thumb_travel_max = 20;
my_appearance.gx_scroll_thumb_border_style = GX_STYLE_BORDER_THIN;

/* Set the scroll appearance. */

status = gx_system_scroll_appearance_set(GX_SCROLLBAR_VERTICAL, &my_appearance);

/* If status is GX_SUCCESS the scroll appearance has been set. */
```

### <a name="see-also"></a>参照

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_start"></a>gx_system_start

GUIX を開始します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_start(VOID);
```

### <a name="description"></a>説明

このサービスは、GUIX 処理を開始します。 通常の状況では、この関数は処理を返しませんが、代わりに GUIX イベント キューの処理を開始します。 GUIX イベント キューが空の場合、このサービスは、新しいイベントが GUIX イベント キューに到達するまで呼び出し元のスレッドを中断します。

### <a name="parameters"></a>パラメーター

- **なし**

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) システムが正常に開始しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Start GUIX. */
status = gx_system_start();

/* If status is GX_SUCCESS . GUIX has been started. */
```

### <a name="see-also"></a>参照

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_string_get"></a>gx_system_string_get

文字列を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_string_get(
    GX_RESOURCE_ID string_id,
    GX_CHAR **return_string);
```

### <a name="description"></a>説明

このサービスは、最初に定義された表示と現在アクティブな言語を使用して、指定されたリソース ID の文字列を取得します。 gx_display_string_get を優先して、この関数は非推奨となりました。 すべての新しいアプリケーションで gx_display_string_get を使用する必要があります。

### <a name="parameters"></a>パラメーター

- **string_id**: 文字列のリソース ID
- **return_string**: 文字列宛先ポインターへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 文字列の取得に成功しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR (0x07)** : ポインターが無効です
- **GX_INVALID_RESOURCE_ID**: (0x33) リソース ID が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Get the string associated with MY_STRING_ID. */

status = gx_system_string_get(MY_STRING_RESOURCE_ID, &my_string);

/* If status is GX_SUCCESS the string is contained in “my_string”.
*/
```

### <a name="see-also"></a>参照

- gx_display_string_get
- gx_display_string_table_get
- gx_display_language_table_set

## <a name="gx_system_string_table_get"></a>gx_system_string_table_get

文字列テーブルを取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_string_table_get(
    GX_UBYTE language,
    GX_CHAR ***string_table,
    UINT *get_size);
```

### <a name="description"></a>説明

このサービスは、最初の表示から、要求された言語の文字列テーブルを取得します。 gx_display_string_table_get を優先して、この関数は非推奨となりました。 すべての新しいアプリケーションで gx_display_string_table_get を使用する必要があります。

### <a name="parameters"></a>パラメーター

- **language**: 言語インデックス
- **string_table**: 文字列テーブル ポインターのストレージ領域へのポインター。呼び出し元が文字列テーブルへのポインターを取得する必要がない場合は NULL。
- **get_size**: 文字列テーブル内の文字列の数に対するストレージへのポインター。呼び出し元が文字列テーブル内の文字列の数を取得する必要がない場合は NULL。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 文字列テーブルの取得に成功しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Get the string table. */

CHAR **my_string_table; UINT table_size;

status = gx_system_string_table_get(LANGUAGE_ID_ENGLISH,
    &my_string_table, &table_size);

/* If status is GX_SUCCESS . the pointer to the string table has
been obtained. */
```

### <a name="see-also"></a>参照

- gx_display_string_table_get
- gx_display_string_get
- gx_display_active_language_set
- gx_display_language_table_set

## <a name="gx_system_string_width_get"></a>gx_system_string_width_get

文字列の幅を取得します (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_string_width_get(
    GX_FONT *font, GX_CHAR *string,
    INT string_length,
    GX_VALUE *return_width);
```

### <a name="description"></a>説明

gx_system_string_width_get_ext() を優先して、このサービスは非推奨となりました。

このサービスは、指定されたフォントを使用して、指定された文字列の表示幅をピクセル単位で計算します。 string_length パラメーターが 0 以上の場合、計算には文字の要求数だけが含まれます。 string_length パラメーターが -1 の場合、計算では、NULL 終端文字までの文字列全体が使用されます。

### <a name="parameters"></a>パラメーター

- **font**: 文字列のフォントへのポインター
- **string**: 文字列へのポインター
- **string_length**: 文字列の長さ
- **return_width**: 文字列の幅の宛先

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 文字列の幅の取得に成功しました
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_FONT**: (0x16) フォントが無効です
- **GX_INVALID_STRING_LENGTH**: (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Get the string width of “my_string”. */

status = gx_system_string_width_get(&my_font, &my_string,
    strlen(my_string), &my_width);

/* If status is GX_SUCCESS . “my_width” contains the string width.
*/
```

### <a name="see-also"></a>参照

- gx_system_string_width_get_ext

## <a name="gx_system_string_width_get_ext"></a>gx_system_string_width_get_ext

文字列の幅を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_string_width_get_ext(
    GX_FONT *font,
    GX_STRING *string,
    GX_VALUE *return_width);
```

### <a name="description"></a>説明

このサービスは、指定されたフォントを使用して、指定された文字列の表示幅をピクセル単位で計算します。

### <a name="parameters"></a>パラメーター

- **font**: 文字列のフォントへのポインター
- **string**: 文字列へのポインター
- **return_width**: 文字列の幅の宛先

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 文字列の幅の取得に成功しました
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_FONT**: (0x16) フォントが無効です
- **GX_INVALID_STRING_LENGTH**: (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_STRING my_string; my_string.gx_string_ptr = “Monday”;

my_string.gx_string_length = strlen(my_string.gx_string_ptr);

/* Get the string width of “my_string”. */

status = gx_system_string_width_get_ext(&my_font,
    &my_string, &my_width);

/* If status is GX_SUCCESS . “my_width” contains the string width.
*/
```

### <a name="see-also"></a>参照

- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_timer_start"></a>gx_system_timer_start

タイマーを開始します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_timer_start(
    GX_WIDGET *owner, 
    UINT timer_id,
    UINT initial_ticks,
    UINT reschedule_ticks);
```

### <a name="description"></a>説明

このサービスは、指定されたウィジェットのタイマーを開始します。 定数 GX_MAX_ACTIVE_TIMERS では、サポートされるアクティブなタイマーの最大数が定義されています。 この値の既定の設定は 32 です。

### <a name="parameters"></a>パラメーター

- **owner**: ウィジェット コントロール ブロックへのポインター
- **timer_id**: タイマーの ID
- **initial_ticks**: 初期の有効期限のティック
- **reschedule_ticks**: 定期的な有効期限のティック

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) タイマーの開始に成功しました
- **GX_OUT_OF_TIMERS**: (0x04) タイマーはこれ以上ありません
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE** (0x22) タイマー値が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Start a periodic timer for the widget “my_widget”. */
status = gx_system_timer_start(&my_widget, MY_TIMER_ID, 10, 20);

/* If status is GX_SUCCESS . the timer for “my_widget” has been
started. */
```

### <a name="see-also"></a>参照

- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_timer_stop"></a>gx_system_timer_stop

タイマーを停止します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_timer_stop(
    GW_WIDGET *owner, 
    UINT timer_id);
```

### <a name="description"></a>説明

このサービスは、呼び出し元のウィジェットに関連付けられている指定された timer_id のタイマーを停止します。 特定のウィジェットにリンクされているすべてのタイマーを停止するために、アプリケーションで timer_id の値として 0 を渡すことができます。

### <a name="parameters"></a>パラメーター

- **owner**: ウィジェット コントロール ブロックへのポインター
- **timer_id**: タイマーの ID。すべてのタイマーの場合は 0

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) タイマーの停止に成功しました
- **GX_NOT_FOUND**: (0x09) タイマー ID が見つかりません
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Stop the periodic timer for the widget “my_widget”. */
status = gx_system_timer_stop(&my_widget, MY_TIMER_ID);

/* If status is GX_SUCCESS . the timer for “my_widget” has been
stopped. */
```

### <a name="see-also"></a>参照

- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_version_string_get"></a>gx_system_version_string_get

GUIX ライブラリのバージョン文字列を取得します (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_version_string_get(GX_CHAR **version);
```

### <a name="description"></a>説明

gx_system_version_string_get_ext() を優先して、このサービスは非推奨となりました。

このサービスは、GUIX ライブラリのバージョン文字列を取得します。

### <a name="parameters"></a>パラメーター

- **version**: 返される文字列値へのポインター。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) バージョン文字列の取得に成功しました
- **GX_PTR_ERROR**: (0x07) ポインターが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_CHAR *version;

/* get the library version string. */

status = gx_system_verrsion_string_get(&version);
```

### <a name="see-also"></a>参照

- gx_system_version_string_get_ext()

## <a name="gx_system_version_string_get_ext"></a>gx_system_version_string_get_ext

GUIX ライブラリのバージョン文字列を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_version_string_get(GX_STRING *version);
```

### <a name="description"></a>説明

このサービスは、GUIX ライブラリのバージョン文字列を取得します。

### <a name="parameters"></a>パラメーター

- **version**: 返される文字列値へのポインター。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) バージョン文字列の取得に成功しました
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_STRING_LENGTH**: (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_STRING version;

/* get the library version string. */

status = gx_system_version_string_get_ext(&version);
```

### <a name="see-also"></a>参照

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_widget_find

## <a name="gx_system_widget_find"></a>gx_system_widget_find

ウイジェットを見つけます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_system_widget_find(
    USHORT widget_id,
    INT search_level, 
    GX_WIDGET **return_search_result);
```

### <a name="description"></a>説明

このサービスは、指定されたウィジェット ID を検索します。 gx_widget_find() とは異なり、この関数は、システムで定義されているすべてのルート ウィンドウの子を検索します。これは、表示されているすべてのウィジェットを網羅的に検索することを意味します。 検索するウィジェットの親がわかっている場合は、代わりに gx_widget_find() を使用します。

### <a name="parameters"></a>パラメーター

- **widget_id**: 検索するウィジェット ID
- **search_level**: 子ウィジェットを検索する際の再帰的な入れ子レベルを定義します。 この値が 0 の場合は、各ルート ウィンドウの直接の子だけが検索されます。 この値が GX_SEARCH_DEPTH_INFINITE の場合、関数は、すべての子まで入れ子を掘り下げて、要求されたウィジェット ID を検索します。 0 より大きいその他の値の場合、検索レベルによって、この関数が要求されたウィジェット ID を検索する入れ子の深さが定義されます。
- **return_search_result**: 見つかったウィジェットの宛先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ウィジェットの検索に成功しました
- **GX_NOT_FOUND**: (0x09) ウィジェット ID が見つかりませんでした
- **GX_PTR_ERROR**: (0x07) ポインターが無効です

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
/* Search recursively from the top level widget for the widget with
ID of MY_WIDGET_ID. */

status = gx_system_widget_find(MY_WIDGET_ID,
    GX_SEARCH_DEPTH_INFINITE,
    &my_widget);

/* If status is GX_SUCCESS . the search was successful and
“my_widget” contains the pointer to the widget. */
```

### <a name="see-also"></a>参照

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get

## <a name="gx_text_button_create"></a>gx_text_button_create

テキスト ボタンを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_button_create(
    GX_TEXT_BUTTON *text_button,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id, 
    ULONG style,
    USHORT text_button_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスは、テキスト ボタン ウィジェットを作成します。

GX_TEXT_BUTTON は GX_BUTTON から派生し、すべての gx_button API サービスをサポートします。

### <a name="parameters"></a>パラメーター

- **text_button**: テキスト ボタン コントロール ブロックへのポインター
- **name**: テキスト ボタンの論理名
- **parent**: ボタンの親ウィジェットへのポインター
- **text_id**: テキストのリソース ID
- **style**: テキスト ボタンのスタイル。 **付録 D** には、ウィジェット固有のスタイルだけでなく、すべてのウィジェット用に事前に定義された一般的なスタイルが含まれています。
- **text_button_id**: テキスト ボタンのアプリケーション定義の ID
- **size**: ボタンのサイズ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) テキスト ボタンの作成に成功しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_ALREADY_CREATED**: (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE**: (0x19) ウィジェット コントロール ブロック サイズが無効です
- **GX_INVALID_WIDGET**: (0x12) 親ウィジェットが無効です


### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_TEXT_BUTTON my_text_button;

GX_RECTANGLE size;

/* Define widget size. */

gx_utility_rectangle_define(&size, 0, 0, 100, 100);

/* Create text button “my_text_button”. */

status = gx_text_button_create(&my_text_button, "my text button",
    &my_parent_window, MY_TEXT_RESOURCE_ID,
    GX_STYLE_BUTTON_TOGGLE, MY_TEXT_BUTTON_ID, &size);

/* If status is GX_SUCCESS, the text button “my_text_button” was
created. */
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_color_set
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_draw"></a>gx_text_button_draw

テキスト ボタンを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_text_button_draw(GX_TEXT_BUTTON *button);
```

### <a name="description"></a>説明

このサービスは、テキスト ボタンを描画します。 このサービスは、通常、キャンバスの更新中に内部的に呼び出されますが、カスタムのテキスト ボタン描画関数から呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **button**: テキスト ボタン コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom text button draw function. */

VOID my_text_button_draw(GX_TEXT_BUTTON *text_button)
{
    /* Call default text button draw. */
    gx_text_button_draw(text_button);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_event_process
- gx_text_button_color_set
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_event_process"></a>gx_text_button_event_process


テキスト ボタンのイベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_button_event_process(GX_TEXT_BUTTON *text_button, GX_EVENT *event_ptr);
```

### <a name="description"></a>説明

このサービスは、指定されたテキスト ボタンのイベントを処理します。 このサービスは、カスタム テキスト ボタンのイベント処理関数によって既定のイベント ハンドラーとして呼び出される必要があります。

### <a name="parameters"></a>パラメーター

- **text_button** テキスト ボタン コントロール ブロックへのポインター
- **event_ptr** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) テキスト ボタンのイベント処理が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Call generic text button event processing as part of custom event processing function. */

UINT custom_text_button_event_process(GX_TEXT_BUTTON *text_button, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default text button event processing */
        status = gx_text_button_event_process(wheel, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_color_set
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_font_set"></a>gx_text_button_font_set

テキスト ボタンにフォントを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_button_font_set(
    GX_TEXT_BUTTON *button,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>説明

このサービスは、指定されたボタンにフォントを割り当てます。

### <a name="parameters"></a>パラメーター

- **button**: テキスト ボタン コントロール ブロックへのポインター
- **font_id**: フォントのリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) フォントが正常に設定されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the text button with the font ID MY_FONT. */
status = gx_text_button_font_set(&my_text_button, MY_FONT);

/* If status is GX_SUCCESS, the font of the text button
“my_text_button” was set to MY_FONT. */
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_color_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_color_set"></a>gx_text_button_text_color_set

テキスト ボタンの色を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_button_text_color_set(
    GX_TEXT_BUTTON *text_button,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id);
```

### <a name="description"></a>説明

このサービスは、テキスト ボタンの色を設定します。

### <a name="parameters"></a>パラメーター

- **text_button**: テキスト ボタン コントロール ブロックへのポインター
- **normal_text_color_id**: 通常のテキストのリソース ID。 **付録 A** には、事前定義済みの色リソース ID が含まれています。 アプリケーションでは、カスタムの色リソース ID も追加できることに注意してください。
- **selected_text_color_id**: 選択されたテキストのリソース ID。 **付録 A** には、事前定義済みの色リソース ID が含まれています。 アプリケーションでは、カスタムの色リソース ID も追加できることに注意してください。
- **disabled_text_color_id**: 無効なテキストの色のリソース ID。 **付録 A** には、事前定義済みの色リソース ID が含まれています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) テキスト ボタンの色の設定に成功しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the color of the text button “my_text_button”. */
status = gx_text_button_text_color_set(&my_text_button,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS, the text color of “my_text_button” was
set. */
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_draw"></a>gx_text_button_text_draw

ボタンのテキストを描画するためのサポート関数

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_text_button_text_draw(GX_TEXT_BUTTON *text_button);
```

### <a name="description"></a>説明

このサポート関数は、テキスト ボタンのテキスト部分を描画します。 この関数は gx_text_button_draw によって内部的に呼び出され、カスタム ボタンの描画関数を定義するアプリケーションの利便性向上のために、独立した API として提供されます。 ボタンの背景描画をカスタマイズする必要があるアプリケーションは、そのカスタム描画関数を提供し、ボタン テキストを背景に重ねて描画するためのカスタム描画の一部として gx_text_button_text_draw サービスを呼び出すことができます。

### <a name="parameters"></a>パラメーター

- **text_button**: テキスト ボタン コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Define a custom drawing function */

VOID my_button_draw(GX_TEXT_BUTTON *button)
{
    /* Insert code here to draw button background */

    /* Call support function to do text drawing */
    gx_text_button_text_draw(button);

    /* Draw child widgets */
    gx_widget_children_draw((GX_WIDGET *) button);
}
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_get"></a>gx_text_button_text_get

テキスト ボタンからテキストを取得します (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_button_text_get(
    GX_TEXT_BUTTON *text_button,
    GX_CHAR **return_text);
```

### <a name="description"></a>説明

gx_text_button_text_get_ext() を優先して、このサービスは非推奨となりました。

このサービスは、テキスト ボタンから指定された文字列を取得します。

### <a name="parameters"></a>パラメーター

- **text_button**: テキスト ボタン コントロール ブロックへのポインター
- **return_text**: テキスト ボタンから取得した文字列へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ボタンからテキストを正常に取得しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_CHAR *string;

/* Get the string from the text button “my_text_button”. */
status = gx_text_button_text_get(&my_text_button, &string);

/* If status is GX_SUCCESS, the string pointer from
“my_text_button” is retrieved and stored in string. */
```

### <a name="see-also"></a>参照

- gx_text_button_text_get_ext

## <a name="gx_text_button_text_get_ext"></a>gx_text_button_text_get_ext

テキスト ボタンからテキストを取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_button_text_get_ext(
    GX_TEXT_BUTTON *text_button,
    GX_STRING *return_string);
```

### <a name="description"></a>説明

このサービスは、テキスト ボタンから指定された文字列を取得します。

### <a name="parameters"></a>パラメーター

- **text_button**: テキスト ボタン コントロール ブロックへのポインター
- **return_string**: テキスト ボタンから取得した文字列へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ボタンからテキストを正常に取得しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_STRING string;

/* Get the string from the text button “my_text_button”. */
status = gx_text_button_text_get_ext(&my_text_button, &string);

/* If status is GX_SUCCESS, the string pointer and length from
“my_text_button” is retrieved and stored in string. */
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_id_set"></a>gx_text_button_text_id_set

テキスト リソース ID をテキスト ボタンに設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_button_text_id_set(
    GX_TEXT_BUTTON *text_button,
    RESOURCE_ID string_id);
```

### <a name="description"></a>説明

このサービスは、指定された文字列リソース ID をテキスト ボタンに設定します。

### <a name="parameters"></a>パラメーター

- **text_button**: テキスト ボタン コントロール ブロックへのポインター
- **string_id**: 文字列のリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 文字列リソース ID をテキスト ボタンに正常に設定しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です
- **GX_INVALID_RESOURCE_ID**: (0x33) 文字列 ID が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the string ID ”MY_STRING_ID” to the text button
“my_text_button”. */

status = gx_text_button_text_id_set(&my_text_button,
    MY_STRING_ID);

/* If status is GX_SUCCESS, the string ID MY_STRING_ID was set to
“my_text_button”. */
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_get

## <a name="gx_text_button_text_set"></a>gx_text_button_text_set

テキストをテキスト ボタンに割り当てます (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_button_text_set(
    GX_TEXT_BUTTON *text_button,
    GX_CHAR *text);
```

### <a name="description"></a>説明

gx_text_button_text_set_ext() を優先して、このサービスは非推奨となりました。

このサービスは、指定された文字列をテキスト ボタンに割り当てます。 text_button ウィジェットがスタイル GX_STYLE_TEXT_COPY で作成されたものである場合は、割り当てられたテキスト文字列のプライベート コピーがウィジェットによって作成されます。 GX_STYLE_TEXT_COPY がアクティブでない場合、ウィジェットでは受信文字列のプライベート コピーが作成されないため、文字列は静的またはグローバルに割り当てられる必要があります (つまり、自動的または一時的な変数であってはなりません)。

### <a name="parameters"></a>パラメーター

- **text_button**: テキスト ボタン コントロール ブロックへのポインター
- **text**: NULL で終わる文字列へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ボタンにテキストが正常に設定されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) メモリ アロケーターが定義されていないか、メモリの割り当てに失敗しました
- **GX_INVALID_STRING_LENGTH**: (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the string “my string” to the text button “my_text_button”.
*/

status = gx_text_button_text_set(&my_text_button, “my string”);

/* If status is GX_SUCCESS, the string “my_text_button” was set.
*/
```

### <a name="see-also"></a>参照

- gx_text_button_event_process
- gx_text_button_text_set_ext
- gx_text_button_text_id_set

## <a name="gx_text_button_text_set_ext"></a>gx_text_button_text_set_ext

テキスト ボタンにテキストを割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_button_text_set_ext(
    GX_TEXT_BUTTON *text_button,
    GX_STRING *string);
```

### <a name="description"></a>説明

このサービスは、指定された文字列をテキスト ボタンに割り当てます。 text_button ウィジェットがスタイル GX_STYLE_TEXT_COPY で作成されたものである場合は、割り当てられたテキスト文字列のプライベート コピーがウィジェットによって作成されます。 GX_STYLE_TEXT_COPY がアクティブでない場合、ウィジェットでは受信文字列のプライベート コピーが作成されないため、文字列は静的またはグローバルに割り当てられる必要があります (つまり、自動的または一時的な変数であってはなりません)。

### <a name="parameters"></a>パラメーター

- **text_button**: テキスト ボタン コントロール ブロックへのポインター
- **string**: GX_STRING 変数へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ボタンにテキストが正常に設定されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) メモリ アロケーターが定義されていないか、メモリの割り当てに失敗しました
- **GX_INVALID_STRING_LENGTH**: (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_STRING new_string; new_string.gx_string_ptr = “Monday”;

new_string.gx_string_length = strlen(new_string.gx_string_ptr);

/* Assign the string “new_string” to the text button
“my_text_button”. */

status = gx_text_button_text_set_ext(&my_text_button, &new_string);

/* If status is GX_SUCCESS, the string “my_text_button” was set.
*/
```

### <a name="see-also"></a>参照

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_get
- gx_text_button_text_id_set

## <a name="gx_text_input_cursor_blink_interval_set"></a>gx_text_input_cursor_blink_interval_set

カーソルの点滅間隔を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_input_cursor_blink_interval_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE blink_interval);
```

### <a name="description"></a>説明

このサービスは、カーソルの点滅間隔の値を設定します。

### <a name="parameters"></a>パラメーター

- **cursor_input** カーソル コントロール ブロック
- **blink_interval** 設定する値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) カーソルの点滅間隔が正常に設定されました
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_VALUE**: (0x22) 点滅間隔の値が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_TEXT_INPUT_CURSOR *input_cursor;

/* Pointer the input cursor to the cursor instance of single/multi
line text input widget. */

input_cursor = &sl_input.gx_single_line_text_input_cursor_instance;

/* Set the blink interval value of “input_cursor” to 2. */
status = gx_text_input_cursor_blink_interval_set(input_cursor, 2);

/* If status is GX_SUCCESS, the blink interval value of
“input_cursor” has been successfully set to 2. */
```

### <a name="see-also"></a>参照

- gx_text_input_cursor_height_set
- gx_text_input_cursor_width_set

## <a name="gx_text_input_cursor_height_set"></a>gx_text_input_cursor_height_set

カーソルの高さを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_input_cursor_height_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE height);
```

### <a name="description"></a>説明

このサービスは、カーソルの高さを設定します。

### <a name="parameters"></a>パラメーター

- **cursor_input**: カーソル コントロール ブロック
- **height** 設定する値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) カーソルの高さが正常に設定されました
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_VALUE**: (0x22) 高さの値が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_TEXT_INPUT_CURSOR *input_cursor;

/* Pointer the input cursor to the cursor instance of single/multi
line text input widget. */

input_cursor = &sl_input.gx_single_line_text_input_cursor_instance;

/* Set height value of “input_cursor”. */
status = gx_text_input_cursor_height_set(&input_cursor, 15);

/* If status is GX_SUCCESS, the height value of “input_curosr” has
been successfully set to 15. */
```

### <a name="see-also"></a>参照

- gx_text_input_cursor_blink_interval_set
- gx_text_input_cursor_width_set

## <a name="gx_text_input_cursor_width_set"></a>gx_text_input_cursor_width_set

カーソルの幅を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_input_cursor_blink_width_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE *width);
```

### <a name="description"></a>説明

このサービスは、カーソルの幅を設定します。

### <a name="parameters"></a>パラメーター

- **cursor_input**: カーソル コントロール ブロック
- **width**: 設定する値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) カーソルの幅が正常に設定されました
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_VALUE**: (0x22) 幅の値が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_TEXT_INPUT_CURSOR *input_cursor;

/* Pointer the input cursor to the cursor instance of single/multi
line text input widget. */

input_cursor = &sl_input.gx_single_line_text_input_cursor_instance;

/* Set width of “input_curosr” to 2. */

status = gx_text_input_cursor_blink_width_set(&input_cursor, 2);

/* If status is GX_SUCCESS, the width of “input_cursor” has been
successfully set to 2. */
```

### <a name="see-also"></a>参照

- gx_text_input_cursor_blink_interval_set
- gx_text_input_cursor_height_set

## <a name="gx_text_scroll_wheel_callback_set"></a>gx_text_scroll_wheel_callback_set

テキスト型のスクロール ホイールのコールバック関数を割り当てます (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_scroll_wheel_callback_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *(*callback)(GX_TEXT_SCROLL_WHEEL *, int));
```

### <a name="description"></a>説明

gx_text_scroll_wheel_callback_set_ext() を優先して、このサービスは非推奨となりました。

このサービスは、スクロール ホイールの各行に表示されるテキスト文字列を決定するために、テキスト型のスクロール ホイールが呼び出すコールバック関数を割り当てます。

GX_NUMERIC_SCROLL_WHEEL と GX_STRING_SCROLL_WHEEL では、既定のコールバック関数が指定されるため、アプリケーションではこれらの既定の実装を使用するために変更を行う必要はありません。

この API は、スクロール ホイール ウィジェットの各行に表示される文字列の書式設定やその他のパラメーターをアプリケーションでカスタマイズできるようにするために用意されています。

コールバック関数は、スクロール ホイール コントロール ブロックへのポインターと、表示される行番号を入力として受け取ります。 この関数は、テキスト文字列へのポインターを返します。

### <a name="parameters"></a>パラメーター

- **wheel** 文字列スクロール ホイール コントロール ブロックのアドレス
- **callback** コールバック関数へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) コールバックが正常に設定されました
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_TEXT_SCROLL_WHEEL wheel;

GX_CHAR string_buffer[20];

GX_CHAR *my_wheel_callback(GX_TEXT_SCROLL_WHEEL *wheel, int row)
{
    /* Just for an example, return row number as string for rows
    >= 0, and return text “Invalid” otherwise */
    if (row >= 0)
    {
        gx_utility_ltoa(row, string_buffer, 20);
    }
    else
    {
        return(“Invalid”);
    }
}

gx_text_scroll_wheel_create(&wheel, “my wheel”, root, 10,
    GX_STYLE_ENABLED|GX_STYLE_TEXT_CENTER|GX_STYLE_TRANSPARENT|
    GX_STYLE_WRAP|ID_MY_WHEEL, &size);

status = gx_text_scroll_wheel_callback_set(&wheel,
    my_wheel_callback);

/* If status is GX_SUCCESS, the scroll whell callback function has
been set. */
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_callback_set_ext"></a>gx_text_scroll_wheel_callback_set_ext

テキスト型のスクロール ホイールのコールバック関数を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_scroll_wheel_callback_set_ext(
    GX_TEXT_SCROLL_WHEEL *wheel,
    UINT *(*callback)(GX_TEXT_SCROLL_WHEEL *, int, GX_STRING *));
```

### <a name="description"></a>説明

このサービスは、スクロール ホイールの各行に表示されるテキスト文字列を決定するために、テキスト型のスクロール ホイールが呼び出すコールバック関数を割り当てます。

GX_NUMERIC_SCROLL_WHEEL と GX_STRING_SCROLL_WHEEL では、既定のコールバック関数が指定されるため、アプリケーションではこれらの既定の実装を使用するために変更を行う必要はありません。

この API は、スクロール ホイール ウィジェットの各行に表示される文字列の書式設定やその他のパラメーターをアプリケーションでカスタマイズできるようにするために用意されています。

コールバック関数は、スクロール ホイール コントロール ブロックへのポインターと、表示される行番号を入力として受け取ります。 この関数は、テキスト文字列へのポインターを返します。

### <a name="parameters"></a>パラメーター

- **wheel** 文字列スクロール ホイール コントロール ブロックのアドレス
- **callback** コールバック関数へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) コールバックが正常に設定されました
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_TEXT_SCROLL_WHEEL wheel;

GX_CHAR string_buffer[20];

UINT *my_wheel_callback(GX_TEXT_SCROLL_WHEEL *wheel, int row,
    GX_STRING *return_string)
{
    /* Just for an example, return row number as string for rows
    >= 0, and return text “Invalid” otherwise */
    if (row >= 0)
    {
        gx_utility_ltoa(row, string_buffer, 20);
        return_string->gx_string_ptr = string_buffer;
        return_string->gx_string_length = strlen(string_buffer);
    }
    else
    {
        return_string->gx_string_ptr = “Invalid”;
        return_string->gx_string_length = strlen(“Invalid”);
    }

    return GX_SUCCESS;
}

gx_text_scroll_wheel_create(&wheel, “my wheel”, root, 10,
    GX_STYLE_ENABLED|GX_STYLE_TEXT_CENTER|GX_STYLE_TRANSPARENT|
    GX_STYLE_WRAP|ID_MY_WHEEL, &size);

status = gx_text_scroll_wheel_callback_set_ext(&wheel,
    my_wheel_callback);

/* If status is GX_SUCCESS, the scroll whell callback function has
been set. */
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_create"></a>gx_text_scroll_wheel_create

テキスト スクロール ホイールを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_scroll_wheel_create(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent, 
    INT total_rows,
    ULONG style, 
    USHORT Id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスは、テキスト スクロール ホイールを作成します。 テキスト スクロール ホイールは、GX_STRING_SCROLL_WHEEL および GX_NUMERIC_SCROLL_WHEEL 型ウィジェットの基本ウィジェットです。 この関数は gx_string_scroll_wheel_create と gx_numeric_scroll_wheel_create によって内部的に呼び出され、カスタムのスクロール ホイール ウィジェットを定義するアプリケーションの利便性向上のために、独立した API として提供されます。

### <a name="parameters"></a>パラメーター

- **wheel**: テキスト スクロール ホイール コントロール ブロックのアドレス
- **name**: アプリケーション定義のウィジェット名
- **parent**: ホイールの親または GX_NULL
- **total_rows**: ユーザーに提示される合計行数
- **style**: 必要なスタイル フラグ
- **Id**: アプリケーション定義のホイール スタイル フラグ
- **size**: 最初のスクロール ホイール サイズ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) テキスト スクロール ホイールの作成に成功しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_ALREADY_CREATED**: (0x13) ウィジェットは既に作成されています
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です


### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Define a custom scroll wheel widget. */
typedef MY_SCROLL_WHEEL_STRUCT
{
    GX_TEXT_SCROLL_WHEEL text_scroll_wheel;

    /* Add custom members here. */

} MY_SCROLL_WHEEL;

MY_SCROLL_WHEEL my_scroll_wheel;

UINT my_scroll_wheel_create(MY_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *name, GX_WIDGET *parent,
    INT total_rows, ULONG style, USHORT Id,
    GX_CONST GX_RECTANGLE *size)
{
    /* Call base creation. */
    status = gx_text_scroll_wheel_create(
        &wheel.text_scroll_wheel,
        ”my_text_scroll_wheel”, GX_NULL, 7,
        GX_STYLE_ENABLED, ID_MY_SCROLL_WHEEL, &size);

    if (status == GX_SUCCESS)
    {
        /* Add custom initialization here. */
        if(parent)
        {
            gx_widget_link(parent, (GX_WIDGET *)wheel);
        }
    }
}
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_string_id_list_set
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_draw"></a>gx_text_scroll_wheel_draw

テキスト スクロール ホイールを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_text_scroll_wheel_draw(GX_TEXT_SCROLL_WHEEL *wheel);
```

### <a name="description"></a>説明

これは、GX_TEXT_SCROLL_WHEEL に基づくすべての種類のホイールの既定の描画関数です。 この関数は、テキスト スクロール ホイールの描画の外観をカスタマイズする必要があるアプリケーションによってオーバーライドできます。

GX_STRING_SCROLL_WHEEL と GX_NUMERIC_SCROLL_WHEEL は、どちらも GX_TEXT_SCROLL_WHEEL に基づいているか、それから派生しています。

### <a name="parameters"></a>パラメーター

- **wheel**: 文字列スクロール ホイール コントロール ブロックのアドレス

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Write a custom wheel draw function. */
UINT my_wheel_draw(GX_TEXT_SCROLL_WHEEL *wheel)
{
    /* Perform default drawing */
    gx_text_scroll_wheel_draw(wheel);

    /* Add custom drawing here */
}
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_event_process"></a>gx_text_scroll_wheel_event_process


テキスト スクロール ホイールのイベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_scroll_wheel_event_process(GX_TEXT_SCROLL_WHEEL *wheel, GX_EVENT *event_ptr);
```

### <a name="description"></a>説明

このサービスは、指定されたテキスト スクロール ホイールのイベントを処理します。 このサービスは、カスタム テキスト スクロール ホイールのイベント処理関数によって既定のイベント ハンドラーとして呼び出される必要があります。

### <a name="parameters"></a>パラメーター

- **wheel** テキスト スクロール ホイール コントロール ブロックへのポインター
- **event_ptr** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) テキスト スクロール ホイールのイベント処理が成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Call generic text scroll wheel event processing as part of custom event processing function. */

UINT custom_text_scroll_wheel_event_process(GX_TEXT_SCROLL_WHEEL *wheel, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default text scroll wheel event processing */
        status = gx_text_scroll_wheel_event_process(wheel, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_font_set"></a>gx_text_scroll_wheel_font_set

スクロール ホイールの行を描画するために使用するフォントを割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_scroll_font_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_RESOURCE_ID normal_font, 
    GX_RESOURCE_ID selected_font);
```

### <a name="description"></a>説明

テキスト スクロール ホイールベースのウィジェットのテキストを描画するために使用されるフォントを割り当てます。

### <a name="parameters"></a>パラメーター

- **wheel**: 文字列スクロール ホイール コントロール ブロックのアドレス

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ホイールのフォントが正常に割り当てられました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_NUMERIC_SCROLL_WHEEL wheel;

status = gx_text_scroll_wheel_font_set(&wheel,
    GX_FONT_ID_WHEEL_NORMAL,
    GX_FONT_ID_WHEEL_SELECTED);

/* If status is GX_SUCCESS, the scroll wheel fonts have been assigned. */
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_text_color_set"></a>gx_text_scroll_wheel_text_color_set

スクロール ホイールの行を描画するために使用する色を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_text_scroll_wheel_text_color_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCe_ID disabled_text_color);
```

### <a name="description"></a>説明

この関数は、テキストベースのスクロール ホイールの行を描画するために使用するテキストの色を割り当てます。

### <a name="parameters"></a>パラメーター

- **wheel**: 文字列スクロール ホイール コントロール ブロックのアドレス
- **normal_text_color**: 選択されていない行の描画に使用される色
- **selected_text_color**: 選択された行の描画に使用される色。
- **disabled_text_color**: 無効なウィジェットのテキストの描画に使用される色。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) スクロール ホイールのテキストの色が正常に割り当てられました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_STRING_SCROLL_WHEEL wheel;

UINT status = gx_text_scroll_wheel_text_color_set(&wheel,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS, the colors used to draw the wheel text have been assigned. */
```

### <a name="see-also"></a>参照

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set

## <a name="gx_tree_view_create"></a>gx_tree_view_create

ツリー ビューの作成

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_tree_view_create(
    GX_TREE_VIEW *tree,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    ULONG style, 
    USHORT tree_view_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスは、指定どおりにツリー ビューを作成し、そのツリー ビューを指定の親ウィジェットに関連付けます。 これは、すべての種類のウィジェットを子メニュー項目として受け入れます。 子メニュー項目として GX_MENU 型ウィジェットを使用することをお勧めします。

GX_TREE_VIEW は GX_WINDOW から派生し、すべての gx_window API サービスをサポートします。

### <a name="parameters"></a>パラメーター

- **tree**: ツリー ビュー コントロール ブロックへのポインター
- **name**: ツリー ビューの名前
- **parent**: 親ウィジェットへのポインター
- **style**: ウィジェットのスタイル。 **付録 D** には、ウィジェット固有のスタイルだけでなく、すべてのウィジェット用に事前に定義されている一般的なスタイルが記載されています。
- **menu_id**: ツリー ビューのアプリケーション定義 ID
- **size**: ツリー ビューのサイズ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ツリー ビューの作成に成功しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_ALREADY_CREATED**: (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE**: (0x19) ウィジェット コントロール ブロック サイズが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
status = gx_tree_view_create(&my_tree_view,
    “my_tree_view”, parent,
    GX_STYLE_ENABLED, MY_TREE_VIEW_ID,
    &size);

/* If status is GX_SUCCESS the tree view was successfully created. */
```

### <a name="see-also"></a>参照

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_draw"></a>gx_tree_view_draw

ツリー ビューを描画します

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_tree_view_draw(GX_TREE_VIEW *tree);
```

### <a name="description"></a>説明

このサービスは、指定されたツリー ビューを描画します。 通常、この関数は GUIX キャンバスの更新メカニズムによって内部で呼び出されますが、カスタム ツリー ビュー ウィジェットのカスタム描画関数の実装を支援するためにアプリケーションに公開されます。

### <a name="parameters"></a>パラメーター

- **tree**: ツリー ビュー コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom tree view draw function. */
UINT my_tree_view_draw(GX_TREE_VIEW *tree_view)
{
    /* Perform default drawing */
    gx_tree_view_draw(tree_view);

    /* Add custom drawing here */
}
```

### <a name="see-also"></a>参照

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_event_process"></a>gx_tree_view_event_process

ツリー ビューのイベントを処理します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_tree_view_event_process(
    GX_TREE_VIEW *tree, 
    GX_EVENT event_ptr);
```

### <a name="description"></a>説明

このサービスでは、指定されたツリー ビューのイベントが処理されます。 このサービスは、カスタム ツリー ビューのイベント処理関数によって既定のイベント ハンドラーとして呼び出される必要があります。

### <a name="parameters"></a>パラメーター

- **tree**: ツリー ビュー コントロール ブロックへのポインター
- **event_ptr**: 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ツリー ビューのイベントが正常に処理されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Call generic tree view event processing as part of custom event
    processing function. */

UINT custom_tree_view_event_process(GX_TREE_VIEW *tree_view,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
        case xyz:
            /* Insert custom event handling here */
            break;
        default:
            /* Pass all other events to the default tree view
                event processing */
            status = gx_tree_view_event_process(tree_view, event);
            break;
    }
}
return status;
```

### <a name="see-also"></a>参照

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_indentation_set"></a>gx_tree_view_indentation_set

ツリー ビューのインデントを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_tree_view_indentation_set(
    GX_TREE_VIEW *tree,
    GX_VALUE indentation);
```

### <a name="description"></a>説明

このサービスでは、ツリー ビューのインデントが設定されます。

### <a name="parameters"></a>パラメーター

- **tree**: ツリー ビュー コントロール ブロックへのポインター
- **indentation**: 設定するインデント

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ツリー ビューのインデントが正常に設定されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set tree view “my_tree” indentation to 10. */
status = gx_tree_view_indentation_set(&my_tree, 10);

/* If status is GX_SUCCESS the indentation of tree view “my_tree”
has been set to 10. */
```

### <a name="see-also"></a>参照

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixemlap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_position"></a>gx_tree_view_position

ツリー ビューの項目を配置します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_tree_view_position(GX_TREE_VIEW *tree);
```

### <a name="description"></a>説明

このサービスは、ツリー ビューの項目を配置します。

### <a name="parameters"></a>パラメーター

- **tree**: ツリー ビュー コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ツリー ビューの項目が正常に配置されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Position tree view “my_tree” items. */
status = gx_tree_view_position(&my_tree);

/* If status is GX_SUCCESS the items of tree view “my_tree” has
been positioned. */
```

### <a name="see-also"></a>参照

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_root_line_color_set"></a>gx_tree_view_root_line_color_set

ツリー ビューのルート線の色を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_tree_view_root_line_color_set(
    GX_TREE_VIEW *tree,
    GX_RESOURCE_ID color_id);
```

### <a name="description"></a>説明

このサービスは、ツリー ビューのルート線の色を割り当てます。

### <a name="parameters"></a>パラメーター

- **tree**: ツリー ビュー コントロール ブロックへのポインター
- **color_id**: ルート線の色のリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ルート線の色が正常に設定されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set root line color for tree view “my_tree”. */

status = gx_tree_view_root_line_color_set(&my_tree,
    MY_ROOT LINE_COLOR_ID);

/* If status is GX_SUCCESS the root line color of the tree view
“my_tree” has been set. */
```

### <a name="see-also"></a>参照

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_root_pixelmap_set"></a>gx_tree_view_root_pixelmap_set

ツリー ビューのルート ピクセルマップを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_tree_view_root_pixelmap_set(
    GX_TREE_VIEW *tree,
    GX_RESOURCE_ID expand_map_id,
    GX_RESOURCE_ID collapse_map_id);
```

### <a name="description"></a>説明

このサービスは、ツリー ビューの展開と折りたたみのピクセルマップを割り当てます。

### <a name="parameters"></a>パラメーター

- **tree**: ツリー ビュー コントロール ブロックへのポインター
- **expand_map_id**: 展開ピクセルマップのリソース ID
- **collapse_map_id**: 折りたたみピクセルマップのリソース ID

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ルート ピクセルマップが正常に設定されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set root pixelmaps for tree view “my_tree”. */

status = gx_tree_view_root_pixelmap_set(&my_tree,
    MY_EXPAND_MAP_ID,
    MY_COLLAPSE_MAP_ID);

/* If status is GX_SUCCESS the root pixelmaps of tree view
“my_tree” has been set. */
```

### <a name="see-also"></a>参照

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_selected_get"></a>gx_tree_view_selected_get

選択された項目を取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_tree_view_selected_get(
    GX_TREE_VIEW *tree,
    GX_WIDGET **selected);
```

### <a name="description"></a>説明

このサービスは、ツリー ビューの現在選択されている項目を取得します。

### <a name="parameters"></a>パラメーター

- **tree**: ツリー ビュー コントロール ブロックへのポインター
- **selected**: 選択されたウィジェット ポインターへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 選択されている項目が正常に取得されました
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Retrieve selected item of tree view “my_tree”. */

GX_WIDGET *selected;

status = gx_tree_view_selected_get(&my_tree, &selected);

/* If status is GX_SUCCESS the selected item of tree view “my_tree”
has been retrieved. */
```

### <a name="see-also"></a>参照

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_set

## <a name="gx_tree_view_selected_set"></a>gx_tree_view_selected_set

選択した項目を設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_tree_view_selected_set(
    GX_TREE_VIEW *tree,
    GX_WIDGET *selected);
```

### <a name="description"></a>説明

このサービスにより、ツリー ビューの選択された項目が設定されます。

### <a name="parameters"></a>パラメーター

- **tree**: ツリー ビュー コントロール ブロックへのポインター
- **selected**: 新しい選択項目へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) メニューの描画が成功しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) ポインターが無効です
- **GX_INVALID_WIDGET**: (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set selected item of tree view “my_tree” to “tree_view_item’. */
status = gx_tree_view_selected_set(&my_tree, &tree_view_item);

/* If status is GX_SUCCESS selected item of tree view “my_menu” has
been set to “tree_view_item”. */
```

### <a name="see-also"></a>参照

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get

## <a name="gx_utility_canvas_to_bmp"></a>gx_utility_canvas_to_bmp

キャンバス メモリをビットマップに変換する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_utility_canvas_to_bmp(
    GX_CANVAS *canvas, 
    GX_RECTANGLE *rect,
    UINT (*write_data)(GX_UBYTE *byte_data, UINT data_count));
```

### <a name="description"></a>説明

このサービスにより、キャンバス メモリがビットマップ ファイルに変換されます。

### <a name="parameters"></a>パラメーター

- **canvas**: キャンバス コントロール ブロック ポインター
- **rect**: 変換する四角形
- **write_data**: データを書き込むコールバック関数ポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 整数の文字列への変換に成功しました
- **GX_PTR_ERROR**: (0x07) リターン バッファー ポインターが無効です
- **GX_INVALID_SIZE**: (0x19) リターン バッファー サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
FILE *fp = GX_NULL;

/* define call back function of how to write the data read from
canvas memory. */

UINT write_data_callback(GX_UBYTE *byte_data, UINT data_count)
{
    if (fp)
    {
        fwrite(byte_data, 1, data_count, fp);
    }
    return GX_SUCCESS;
}

VOID scroll_wheel_screen_draw(GX_WINDOW *window)
{
    UINT status;

    GX_RECTANGLE size = {31,31,610,450};
    gx_window_draw(window);
    if (screenshot)
    {
        fp = fopen("../screenshot.bmp", "wb");
        /* Convert canvas memory to bitmap format.
           Status GX_SUCCESS means operation succeed. */
        status = gx_utility_canvas_to_bmp(root->gx_window_root_canvas,
            &size, write_data_callback);

        fclose(fp);
    }
}
```

### <a name="see-also"></a>参照

- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_circle_point_get"></a>gx_utility_circle_point_get

円上のポイントを計算する

### <a name="prototype"></a>プロトタイプ

```C
INT gx_utility_circle_point_get(
    INT xCenter, 
    INT yCenter,
    UINT radius, 
    INT angle, 
    GX_POINT *point);
```

### <a name="description"></a>説明

このサービスにより、円の中心、半径、および角度を指定して、円上のポイントが計算されます。

### <a name="parameters"></a>パラメーター

- **xCenter**: 円の中心の x 座標
- **yCenter**: 円の中心の y 座標
- **radius**: 円の半径
- **angle**: 円の外周ポイントを計算する角度 (度単位)
- **point**: 計算された x、y 座標を格納する GX_POINT 変数のアドレス
- **end_alpha**: 終了アルファ値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) グラデーションが作成されました
- **GX_PTR_ERROR**: (0x07) リターン ポイント アドレスが無効です
- **GX_INVALID_VALUE**: (0x22) 半径のパラメーターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_POINT point;
    UINT status;

        status = gx_utility_circle_point_get(100, 100,
20, 45,
&point);

/* If status is GX_SUCCESS the value of point is the x,y coordinate of a point on the circle perimeter at an angle of 45 degrees, where the circle is centered at (100, 100), has a radius of 20 pixels */

```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_gradient_create"></a>gx_utility_gradient_create

グラデーションのピクセルマップを作成する

### <a name="prototype"></a>プロトタイプ

```C
INT gx_utility_gradient_create(
    GX_GRADIENT *gradient,
    GX_VALUE width, 
    GX_VALUE height,
    UCHAR type, 
    GX_UBYTE start_alpha, 
    GX_UBYTE end_alpha);
```

### <a name="description"></a>説明

このサービスでは、ランタイムにグラデーションのピクセルマップが作成されます。 グラデーション画像を使用して、フェード効果やその他の興味深いビジュアルの変更を実行できます。

要求するグラデーションの幅と高さは、2x2 ピクセル以上にしてください。

GUIX では、作成されたグラデーションのリストが内部に保持されます。この関数では、最初にグラデーション リストで一致するグラデーションのピクセルマップが検索され、その後に新しいピクセルマップが作成されます。 言い換えると、同じグラデーション ピクセルマップが複数回必要になる場合、1 つのピクセルマップのみが実際に作成され、このピクセルマップを必要とする各グラデーションによってその作成されたピクセルマップが共有されます。

この API では、ランタイム メモリの割り当てを可能にするために gx_system_memory_allocator 関数が定義されている必要があります。

グラデーションの型のフラグには、GX_GRADIENT_TYPE_ALPHA と GX_GRADIENT_TYPE_MIRROR が含まれます。 現在サポートされているのは GX_GRADIENT_TYPE_ALPHA の型のグラデーションのみです (つまり、この型のフラグを設定する必要があります)。 GX_GRADIENT_TYPE_MORROR フラグは省略可能です。これを設定すると、start_alpha から end_alpha に変化し、そしてまた start_alpha に戻るグラデーションを作成するように、グラデーション作成ロジックに指示します。 それ以外の場合は、線形グラデーションが作成されます。

### <a name="parameters"></a>パラメーター

- **gradient**: グラデーション コントロール ブロックの構造体へのポインター
- **width**: 要求されたピクセルマップの幅
- **height**: 要求されたピクセルマップの高さ
- **type**: 要求されたグラデーションの型
- **start_alpha**: 開始アルファ値
- **end_alpha**: 終了アルファ値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) グラデーションが作成されました
- **GX_INVALID_SIZE**: (0x19) グラデーションが 2x2 ピクセル以上ではありません
- **GX_NOT_SUPPORTED**: (0x28) グラデーションが GX_GRADIENT_TYPE_ALPHA 型ではありません
- **GX_FAILURE**: (0x10) メモリ アロケーターが定義されていないか、メモリ割り当てが失敗しました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) グラデーション ポインターが無効です
- **GX_INVALID_VALUE**: (0x22) 幅と高さの値が無効です
- **GX_INVALID_TYPE**: (0x1B) グラデーションの型が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_GRADIENT gradient;

UINT status;

status = gx_utiity_gradient_create(&gradient, 3, 40,
    GX_GRADIENT_TYPE_ALPHA, 240, 0);

/* If status == GX_SUCCESS the gradient pixelmap has been created */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_gradient_delete"></a>gx_utility_gradient_delete

以前に作成したグラデーションを削除する

### <a name="prototype"></a>プロトタイプ

```C
INT gx_utility_gradient_delete(GX_GRADIENT *gradient);
```

### <a name="description"></a>説明

このサービスでは、以前に作成されたグラデーションが削除されます。 このグラデーションに関連付けられているピクセルマップが他のグラデーションで使用されていない場合は、ピクセルマップ データも削除されます。

### <a name="parameters"></a>パラメーター

- **gradient**: グラデーション コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) グラデーションが削除されました
- **GX_CALLER_ERROR**: (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR**: (0x07) グラデーション ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_GRADIENT gradient;

UINT status;

/* Delete previously created gradient. */
status = gx_utility_gradient_delete(&gradient);

/* If status == GX_SUCCESS, the gradient has been deleted. */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_ltoa"></a>gx_utility_ltoa

長整数を ASCII に変換する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_utility_itoa(
    LONG value, 
    GX_CHAR *return_buffer,
    UINT seturn_buffer_size);
```

### <a name="description"></a>説明

このサービスでは、長整数値が ASCII 文字列に変換されます。

### <a name="parameters"></a>パラメーター

- **value**: 変換する長整数値
- **return_buffer**: ASCII 文字列の変換先バッファー
- **return_buffer_size**: 変換先バッファーのサイズ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 整数の文字列への変換に成功しました
- **GX_PTR_ERROR**: (0x07) リターン バッファー ポインターが無効です
- **GX_INVALID_SIZE**: (0x19) リターン バッファー サイズが無効です

### <a name="allowed-from"></a>許可元

すべて

### <a name="example"></a>例

```C
INT my_value = 200;

GX_CHAR string_buffer[10];

UINT status;

/* Convert “my_value” into an ASCII string. */
status = gx_utility_ltoa(my_value, string_buffer, 10);

/* If status is GX_SUCCESS, “string_buffer” contains the ASCII
representation of “my_value”. */
```

### <a name="see-also"></a>参照

- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_acos"></a>gx_utility_math_acos

アーク コサインを計算する

### <a name="prototype"></a>プロトタイプ

```C
INT gx_utility_math_acos(GX_FIXED_VAL x);
```

### <a name="description"></a>説明

このサービスにより、アーク コサイン x の角度値が計算されます。

入力値は固定ポイント データ型であり、GX_FIXED_VAL_MAKE を呼び出して INT から GX_FIXED_VAL 型に変換します。 たとえば、0.5 のアーク コサインを計算する場合は、入力を GX_FIXED_VAL_MAKE(1) / 2 とします。

5\.4.0 またはそれ以下のバージョンの GUIX では、この関数の入力値の型は INT で、値は [-256, 256] の範囲に制限されます。 アプリケーションは、このサービスを呼び出す前に、範囲 [-1, 1] から範囲 [-256, 256] に値をスケーリングする必要があります。 GUIX バージョンが 5.4.0 またはそれ以下のプロジェクトで、この API への参照があり、最新の guix ライブラリを使用してプロジェクトをアップグレードするとします。 この場合、2 つの選択肢があります。

1. GX_FIXED_VAL データ型の値を使用するように、この API 呼び出しの入力値を修正します。
1. GUIX_5_4_0_COMPATIBILITY を定義します。

### <a name="parameters"></a>パラメーター

- **x**: アーク コサインが計算される値

### <a name="return-values"></a>戻り値

- **angle**: アーク コサイン x の角度値

### <a name="allowed-from"></a>許可元

すべて

### <a name="example"></a>例

```C
/* Compute the angle value of arc cosine of “0.5”. */

#if defined(GUIX_5_4_0_COMPATIBILITY)
    x = 256 / 2;
#else
    x = GX_FIXED_VAL_MAKE(1) / 2;
#endif

angle = gx_utility_math_acos(x);

/* “angle” contains the angle value of arc cosine “x”. */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_asin"></a>gx_utility_math_asin

アーク サインを計算する

### <a name="prototype"></a>プロトタイプ

```C
INT gx_utility_math_asin(GX_FIXED_VAL x);
```

### <a name="description"></a>説明

このサービスにより、アーク サイン x の角度値が計算されます。

入力値は固定ポイント データ型であり、GX_FIXED_VAL_MAKE を呼び出して INT から GX_FIXED_VAL 型に変換します。 たとえば、0.5 のアーク サインを計算する場合は、入力を GX_FIXED_VAL_MAKE(1) / 2 とします。

5\.4.0 またはそれ以下のバージョンの GUIX では、この関数の入力値の型は INT で、値は [-256, 256] の範囲に制限されます。 アプリケーションは、このサービスを呼び出す前に、範囲 [-1, 1] から範囲 [-256, 256] に値をスケーリングする必要があります。 GUIX バージョンが 5.4.0 またはそれ以下のプロジェクトで、最新の guix ライブラリを使用してプロジェクトをアップグレードするとします。 この場合、2 つの選択肢があります。

1. GX_FIXED_VAL データ型の値を使用するように、この API 呼び出しの入力値を修正します。
1. GUIX_5_4_0_COMPATIBILITY を定義します。

### <a name="parameters"></a>パラメーター

- **x**: アーク サインが計算される値

### <a name="return-values"></a>戻り値

- **angle**: アーク サイン x の角度値

### <a name="allowed-from"></a>許可元

すべて

### <a name="example"></a>例

```C
/* Compute the angle value of arc sine of “x”. */

#if defined GUIX_5_4_0_COMPATIBILITY
    x = 256 / 2;
#else
    X = GX_FIXED_VAL_MAKE(1) / 2;
#endif

angle = gx_utility_math_asin(x);

/* “angle” contains the angle value of arc sine “x”. */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_acos
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_cos"></a>gx_utility_math_cos

コサインを計算する

### <a name="prototype"></a>プロトタイプ

```C
GX_FIXED_VAL gx_utility_math_cos(GX_FIXED_VAL angle);
```

### <a name="description"></a>説明

このサービスにより、指定された角度のコサインが計算されます。

入力値は固定ポイント データ型であり、GX_FIXED_VAL_MAKE を呼び出して INT から GX_FIXED_VAL に変換します。 たとえば、90 度のコサインを計算する場合は、入力を GX_FIXED_VAL_MAKE(90) とします。

戻り値は固定ポイント データ型であり、GX_FIXED_VAL_TO_INT を呼び出して GX_FIXED_VAL から INT に変換します。

5\.4.0 またはそれ以前の GUIX バージョンでは、このサービスの入力値と戻り値の型は INT で、入力値と戻り値には 256 が掛けられ増大します。 したがって、このサービスを呼び出す前に、アプリケーションで角度の値を 256 でスケーリングする必要があります。 GUIX バージョンが 5.4.0 以下のプロジェクトで、最新の guix ライブラリを使用してプロジェクトをアップグレードする場合は、2 つのオプションがあります。

1. この API 呼び出しの入力値と戻り値の処理を、GX_FIXED_VAL データ型の値を使用するように修正します。
1. GUIX_5_4_0_COMPATIBILITY を定義します。

### <a name="parameters"></a>パラメーター

- **angle**: コサインを計算する角度

### <a name="return-values"></a>戻り値

- **cosine**: 指定された角度のコサイン

### <a name="allowed-from"></a>許可元

すべて

### <a name="example"></a>例

```C
/* Compute cosine of 90 degree. */

INT angle = 90;

#if defined (GUIX_5_4_0_COMPATIBILITY)
    INT scaled_angle = angle << 8;
#else
    GX_FIXED_VAL scaled_angle = GX_FIXED_VAL_MAKE(angle);
#endif

my_angle_cosine = gx_utility_math_cos(scaled_angle);

/* “my_angle_cosine” contains the cosine of “my_angle”. */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_acos
- gx_utility_math_asin
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_sin"></a>gx_utility_math_sin

サイン (正弦) を計算する

### <a name="prototype"></a>プロトタイプ

```C
GX_FIXED_VAL gx_utility_math_sin(GX_FIXED_VAL angle);
```

### <a name="description"></a>説明

このサービスにより、指定された角度のサインが計算されます。

入力値は固定ポイント データ型であり、GX_FIXED_VAL_MAKE を呼び出して INT から GX_FIXED_VAL に変換します。 たとえば、90 度のサインを計算する場合は、入力を GX_FIXED_VAL_MAKE (90) とします。 

戻り値は固定ポイント データ型であり、GX_FIXED_VAL_TO_INT を呼び出して GX_FIXED_VAL から INT に変換します。

5\.4.0 またはそれ以下の GUIX バージョンでは、入力値と戻り値の型は INT で、入力値と戻り値は 256 で拡大されます。 したがって、このサービスを呼び出す前に、アプリケーションで角度の値を 256 でスケーリングする必要があります。 GUIX バージョンが 5.4.0 以下のプロジェクトで、最新の guix ライブラリを使用してプロジェクトをアップグレードする場合は、2 つのオプションがあります。

1. この API 呼び出しの入力値と戻り値の処理を、GX_FIXED_VAL データ型の値を使用するように修正します。
1. GUIX_5_4_0_COMPATIBILITY を定義します。

### <a name="parameters"></a>パラメーター

- **angle**: サインを計算する角度

### <a name="return-values"></a>戻り値

- **sine**: 指定された角度のサイン

### <a name="allowed-from"></a>許可元

すべて

### <a name="example"></a>例

```C
INT my_angle = 80;

/* Compute sine of “my_angle”. */

#if defined(GUIX_5_4_0_COMPATIBILITY)
    INT scaled_angle = my_angle << 8;
#else
    GX_FIXED_VAL = GX_FIXED_VAL_MAKE(my_angle);
#endif

my_angle_sine = gx_utility_math_sin(scaled_angle);

/* “my_angle_sine” contains the sine of “my_angle”. */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_acos
- gx_utility_asin
- gx_utility_math_cos
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_sqrt"></a>gx_utility_math_sqrt

平方根を計算する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_utility_math_sqrt(UINT value);
```

### <a name="description"></a>説明

このサービスにより、指定された値の平方根が計算されます。

### <a name="parameters"></a>パラメーター

- **value**: 平方根を計算する値

### <a name="return-values"></a>戻り値

- **square root**: 指定された値の平方根

### <a name="allowed-from"></a>許可元

すべて

### <a name="example"></a>例

```C
/* Compute square root of “my_value”. */
my_square_root = gx_utility_math_sqrt(my_value);

/* “my_square_root” contains the square root of “my_value”. */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_bidi_paragraph_reorder"></a>gx_utility_bidi_paragraph_reorder

BiDi テキストを表示順に並べ替える

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_utility_bidi_paragraph_reorder(GX_BIDI_TEXT_INFO *input_info, 
                                       GX_BIDI_RESOLVED_TEXT_INFO **resolved_info_head)
```

### <a name="description"></a>説明

このサービスは、BiDi テキストを表示順に並べ替えます。 テキスト描画のフォントと表示幅が指定されている場合は、最初に改行が適用され、各行に基づいて並べ替え処理が適用されます。 指定したテキストに複数の段落が含まれている場合、サービスはテキストを段落に分割し、各段落の改行と並べ替えの結果がリストとしてリンクされます。

### <a name="parameters"></a>パラメーター

- **input_info**: 改行とテキストの並べ替えに関する情報へのポインター
- **resolved_info_head**: 指定されたテキストの各段落の改行と並べ替えの結果を含むリンク リストへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) bidi テキストの並べ替えが成功しました
- **GX_PTR_ERROR**: (0x07) 入力ポインターが無効です
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) メモリ アロケーターが定義されていないか、メモリの割り当てに失敗しました

### <a name="allowed-from"></a>許可元

すべて

### <a name="example"></a>例
#### <a name="draw-single-line-bidi-text-to-canvas"></a>単一行の bidi テキストをキャンバスに描画する
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_CHAR bidi_text[] = "Single Line String";
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = GX_NULL;
    input_info.gx_bidi_text_info_display_width = -1;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        /* Draw reordered bidi text to canvas. */
        gx_canvas_text_draw_ext(widget->gx_widget_size.gx_rectangle_left,
                                widget->gx_widget_size.gx_rectangle_top,
                                resolved_info.gx_bidi_resolved_text_info_text);

        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```
#### <a name="draw-multi-line-bidi-text-to-canvas"></a>複数行の bidi テキストをキャンバスに描画する
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_CHAR bidi_text[] = "Multi Line BiDi Text Display Example";
    GX_FONT *font;
    GX_RECTANGLE client;
    GX_VALUE display_width;
    INT index;
    GX_VALUE xpos;
    GX_VALUE ypos;
    
    /* Pickup the font. */
    gx_context_font_get(font_id, &font);
    gx_widget_client_get(widget, 2, &client);
    
    display_width = (GX_VALUE)(client.gx_rectangle_right - client.gx_rectangle_left + 1);
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = font;
    input_info.gx_bidi_text_info_display_width = display_width;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        xpos = client.gx_rectangle_left;
        ypos = client.gx_rectangle_top;
        
        /* Draw reordered bidi text to canvas. */
        for(index = 0; index < resolved_info.gx_bidi_resolved_text_info_total_lines; index++)
        {
            gx_canvas_text_draw_ext(xpos, ypos, &resolved_info.gx_bidi_resolved_text_info_text[index]);
        
            ypos += font->gx_font_line_height;
        }
        
        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```

#### <a name="draw-multi-paragraph-bidi-text-to-canvas"></a>複数段落の bidi テキストをキャンバスに描画する
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_BIDI_RESOLVED_TEXT_INFO *next;
    GX_CHAR bidi_text[] = "Multi Paragraph\r BiDi Text Display Example";
    GX_FONT *font;
    GX_RECTANGLE client;
    GX_VALUE display_width;
    INT index;
    GX_VALUE xpos;
    GX_VALUE ypos;
    
    /* Pickup the font. */
    gx_context_font_get(font_id, &font);
    gx_widget_client_get(widget, 2, &client);
    
    display_width = (GX_VALUE)(client.gx_rectangle_right - client.gx_rectangle_left + 1);
    
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = font;
    input_info.gx_bidi_text_info_display_width = display_width;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        xpos = client.gx_rectangle_left;
        ypos = client.gx_rectangle_top;
        
        next = resolved_info;
        
        /* Draw reordered bidi text to canvas. */
        while(next)
        {
            for(index = 0; index < next.gx_bidi_resolved_text_info_total_lines; index++)
            {
                gx_canvas_text_draw_ext(xpos, ypos, &next.gx_bidi_resolved_text_info_text[index]);
            
                ypos += font->gx_font_line_height;
            }
            
            next = next->gx_bidi_resolved_text_info_next;
        }
        
        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```

### <a name="see-also"></a>参照

- gx_utility_bidi_resolved_text_info_delete

## <a name="gx_utility_bidi_resolved_text_info_delete"></a>gx_utility_bidi_resolved_text_info_delete

解決された BiDi テキスト情報リストを削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_utility_bidi_resolved_text_info_delete(GX_BIDI_RESOLVED_TEXT_INFO **resolved_info_head)
```

### <a name="description"></a>説明

このサービスは、gx_utility_bidi_paragraph_reorder によって返された解決済み情報リストを削除します。

### <a name="parameters"></a>パラメーター

- **resolved_info_head**: 解決された BiDi テキスト情報リストへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 解決されたテキストの削除が成功しました
- **GX_PTR_ERROR**: (0x07) 入力ポインターが無効です
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) メモリ アロケーターが定義されていないか、メモリの割り当てに失敗しました

### <a name="allowed-from"></a>許可元

すべて

### <a name="example"></a>例
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_CHAR bidi_text[] = "Single Line String";
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = GX_NULL;
    input_info.gx_bidi_text_info_display_width = -1;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        /* Draw reordered bidi text to canvas. */
        gx_canvas_text_draw_ext(widget->gx_widget_size.gx_rectangle_left,
                                widget->gx_widget_size.gx_rectangle_top,
                                resolved_info.gx_bidi_resolved_text_info_text);

        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```

### <a name="see-also"></a>参照

- gx_utility_bidi_paragraph_reorder

## <a name="gx_utility_pixelmap_resize"></a>gx_utility_pixelmap_resize

ピクセルマップをサイズ変更する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_utility_pixelmap_resize(
    GX_PIXELMAP *src,
    GX_PIXELMAP *destination, 
    INT width, 
    INT height);
```

### <a name="description"></a>説明

このサービスは、ピクセルマップのサイズを変更し、サイズ変更後の新しいピクセルマップへのポインターを返します。

このサービスでは、サイズ変更されたピクセルマップ データを保持するためのメモリ割り当てを可能にするために、事前に gx_system_memory_allocator_set を使用する必要があります。

### <a name="parameters"></a>パラメーター

- **src**: サイズ変更するピクセルマップへのポインター
- **destination**: 結果のピクセルマップの保存先バッファー
- **width**: 結果のピクセルマップの幅 (ピクセル単位)
- **height**: 結果のピクセルマップの高さ (ピクセル単位)

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ピクセルマップのサイズ変更が成功しました
- **GX_PTR_ERROR**: (0x07) ソースまたはターゲットのピクセルマップ ポインターが無効です
- **GX_INVALID_VALUE**: (0x22) 幅または高さの値が無効です
- **GX_NOT_SUPPORTED**: (0x28) ソース ピクセルマップは圧縮形式です
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) メモリ アロケーターが定義されていないか、メモリの割り当てに失敗しました

### <a name="allowed-from"></a>許可元

すべて

### <a name="example"></a>例

```C
GX_PIXLEMAP *des_pixelmap;

/* Resize “src_pixelmap” with specifiy width and height. */
status = gx_utility_pixelmap_resize(src_pixelmap,
    &des_pixelmap, 100, 200);

/* If status is GX_SUCCESS. “des_pixelmap” successfully load the
resulting pixelmap of resize. */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift
- gx_canvas_pixelmap_rotate

## <a name="gx_utility_pixelmap_rotate"></a>gx_utility_pixelmap_rotate

ピクセルマップを回転する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_utility_pixelmap_rotate(
    GX_PIXELMAP *src, INT angle,
    GX_PIXELMAP *destination,
    UINT *rot_cx, 
    UINT *rot_cy);
```

### <a name="description"></a>説明

このサービスは、ピクセルマップを回転し、回転後の新しいピクセルマップへのポインターを返します。 ピクセルマップをキャンバスで直接回転させるには、gx_canvas_pixelmap_rotate() を使用します。

このサービスでは、回転したピクセルマップ データを保持するためのメモリ割り当てを可能にするために、事前に gx_system_memory_allocator_set を使用する必要があります。

### <a name="parameters"></a>パラメーター

- **src**: 回転するピクセルマップ
- **angle**: 回転角度
- **destination**: 結果のピクセルマップの宛先バッファー
- **rot_cx**: 宛先のピクセルマップに対する、取得された回転中心の x 座標。 ソースのピクセルマップに対する、回転中心の x 座標を使用して開始する必要があります。 rot_cx が GX_NULL の場合、値は取得されません。
- **rot_cy**: 宛先のピクセルマップに対する、取得された回転中心の y 座標。 ソースのピクセルマップに対する、回転中心の y 座標を使用して開始する必要があります。 rot_cy が GX_NULL の場合、値は取得されません。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ピクセルマップの回転が成功しました
- **GX_PTR_ERROR**: (0x07) ソースまたはターゲットのピクセルマップ ポインターが無効です
- **GX_INVALID_VALUE**: (0x22) 角度の値が 0 です
- **GX_INVALID_FORMAT**: (0x28) ソースのピクセルマップが圧縮形式です。これはサポートされていません
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) メモリ アロケーターが定義されていないか、メモリの割り当てに失敗しました

### <a name="allowed-from"></a>許可元

すべて

### <a name="example"></a>例

```C
rot_cx = source_rotate_center_x;
rot_cy = source_rotate_center_y;

/* rotate “src_pixelmap” by 30 degree in clockwise direction. */
status = gx_utility_pixelmap_rotate(src_pixelmap, 30,
    &des_pixelmap, &rot_cx, &rot_cy);

/* If status is GX_SUCCESS. “des_pixelmap” successfully load the
resulting pixelmap of rotation. */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift
- gx_canvas_pixelmap_rotate

## <a name="gx_utility_pixelmap_simple_rotate"></a>gx_utility_pixelmap_simple_rotate

ピクセルマップを回転する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_utility_pixelmap_simple_rotate(
    GX_PIXELMAP *src,
    INT angle,
    GX_PIXELMAP *destination,
    UINT *rot_cx,
    UINT *rot_cy);
```

### <a name="description"></a>説明

このサービスにより、ピクセルマップが 90 度、180 度、または 270 度回転されます。

### <a name="parameters"></a>パラメーター

- **src**: 回転するピクセルマップ
- **angle**: 回転角度
- **destination**: 結果のピクセルマップの宛先バッファー
- **rot_cx**: 宛先のピクセルマップに対する、取得された回転中心の x 座標。 ソースのピクセルマップに対する、回転中心の x 座標を使用して開始する必要があります。 rot_cx が GX_NULL の場合、値は取得されません。
**rot_cy**: 宛先のピクセルマップに対する、取得された回転中心の y 座標。 ソースのピクセルマップに対する、回転中心の y 座標を使用して開始する必要があります。 rot_cy が GX_NULL の場合、値は取得されません。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) ピクセルマップの回転が成功しました
- **GX_PTR_ERROR**: (0x07) ピクセルマップ ポインターのソースまたは宛先が無効です
- **GX_INVALID_VALUE**: (0x22) 角度値が 0 であるか、または90、180、270 のような単純な角度ではありません
- **GX_INVALID_FORMAT**: (0x28) ソースのピクセルマップが圧縮形式です。これはサポートされていません
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) メモリ アロケーターが定義されていないか、メモリの割り当てに失敗しました

### <a name="allowed-from"></a>許可元

すべて

### <a name="example"></a>例

```C
rot_cx = source_rotate_center_x;
rot_cy = source_rotate_center_y;

/* rotate “src_pixelmap” by 90 degree in clockwise direction. */
status = gx_utility_pixelmap_simple_rotate(src_pixelmap, 90,
    &des_pixelmap,
    &rot_cx, &rot_cy);

/* If status is GX_SUCCESS. “des_pixelmap” successfully load the
resulting pixelmap of rotation. */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_center"></a>gx_utility_rectangle_center

四角形内で別の四角形を中央に配置する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_utility_rectangle_center(
    GX_RECTANGLE *rectangle,
    GX_RECTANGLE *within_rectangle);
```

### <a name="description"></a>説明

このサービスにより、四角形の内側の中央に別の四角形が配置されます。

### <a name="parameters"></a>パラメーター

- **rectangle**: 中央に配置する四角形
- **within_rectangle**: 内側で中央に配置する四角形

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) が四角形が正しく中央に配置されました
- **GX_PTR_ERROR**: (0x07) 入力四角形ポインターが無効です
- **GX_INVALID_SIZE**: (0x19) 四角形のサイズが無効です

### <a name="allowed-from"></a>許可元

すべて

### <a name="example"></a>例

```C
UINT status;

/* Center “my_inner_rectangle” inside of “my_outer_rectangle”.*/
status = gx_utility_rectangle_center(&my_inner_rectangle,
    &my_outer_rectangle);

/* Is status is GX_SUCCESS, “my_inner_rectangle” is centered
within “my_other_rectangle”. */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_center_find"></a>gx_utility_rectangle_center_find

四角形の中央を検出する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_utility_rectangle_center_find(
    GX_RECTANGLE *rectangle,
    GX_POINT *return_center);
```

### <a name="description"></a>説明

このサービスにより、四角形の中心が検出されます。

### <a name="parameters"></a>パラメーター

- **rectangle**: 四角形
- **return_center**: 中心点へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 四角形の中心の検出に成功しました
- **GX_PTR_ERROR** (0x07) 入力ポインターが無効です
- **GX_INVALID_SIZE**: (0x19) 四角形のサイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
UINT status;

GX_RECTANGLE my_rectangle;

GX_POINT my_center_point;

gx_utility_define(&my_rectangle, 0, 0, 100, 100);

/* Find center of “my_rectangle””. */

status = gx_utility_rectangle_center_find(&my_rectangle,
    &my_center_point);

/* If status is GX_SUCCESS, “my_center_point” is the center point
of “my_rectangle” (50, 50). */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_combine"></a>gx_utility_rectangle_combine

2 つの四角形を最初のものに結合する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_utility_rectangle_combine(
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle);
```

### <a name="description"></a>説明

このサービスにより、1 番目と 2 番目の四角形が 1 つ目の四角形に結合されます。 最初の四角形は、2 番目を含むように拡張されます。

### <a name="parameters"></a>パラメーター

- **first_rectangle**: 最初の四角形と結合された四角形
- **second_rectangle**: 2 番目の四角形

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 2 つの四角形の結合に成功しました
- **GX_PTR_ERROR** (0x07) 入力ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
UINT status;

GX_RECTANGLE rect_a;

GX_RECTANGLE rect_b;

gx_utility_rectangle_define(&rect_a, 0, 0, 100, 100);
gx_utility_rectangle_define(&rect_b, 50, 50, 200, 200);

/* Combine “my_rectangle_a” to “my_rectangle_b”. */
status = gx_utility_rectangle_combine(&rect_a, &rect_b);

/* If status is GX_SUCCESS, “rect_a” is (0, 0, 200, 200) the merger
of the original “rect_a” and “rect_b”. */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_compare"></a>gx_utility_rectangle_compare

2 つの四角形を比較する

### <a name="prototype"></a>プロトタイプ

```C
GX_BOOL gx_utility_rectangle_compare( 
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle);
```

### <a name="description"></a>説明

このサービスにより、1 番目と 2 番目の四角形が比較されます。 等しい場合は、GX_TRUE の値が返されます。

### <a name="parameters"></a>パラメーター

- **first_rectangle**: 最初の四角形
- **second_rectangle**: 2 番目の四角形

### <a name="return-values"></a>戻り値

- **result**: 四角形が等しい場合は GX_TRUE、それ以外の場合は GX_FALSE が返されます。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Compare “my_rectangle_a” to “my_rectangle_b”. */
result = gx_utility_rectangle_compare(&my_rectangle_a,
    &my_rectangle_b);

/* If result is GX_TRUE, the two rectangles are equal. */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_define"></a>gx_utility_rectangle_define

四角形を定義する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_utility_rectangle_define(
    GX_RECTANGLE *rectangle,
    GX_VALUE left,
    GX_VALUE top, 
    GX_VALUE right, 
    GX_VALUE bottom);
```

### <a name="description"></a>説明

このサービスにより、指定されたように四角形が定義されます。

### <a name="parameters"></a>パラメーター

- **rectangle**: 四角形のコントロール ブロック
- **left**: 左端の座標
- **top**: 上端の座標
- **right**: 右端の座標
- **bottom**: 下端の座標

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) が四角形の定義に成功しました
- **GX_PTR_ERROR**: (0x07) 四角形ポインターが無効です

### <a name="allowed-from"></a>許可元

すべて

### <a name="example"></a>例

```C
UINT status;

GX_RECTANGLE my_rect;

/* Define “my_rect”. */

status = gx_utility_rectangle_define(&my_rect, 10, 5, 200, 100);

/* If status is GX_SUCCESS, “my_rect” is defined. */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_overlap_detect"></a>gx_utility_rectangle_overlap_detect

四角形の重複を検出する

### <a name="prototype"></a>プロトタイプ

```C
GX_BOOL gx_utility_rectangle_overlap_detect(
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle,
    GX_RECTANGLE *return_overlap_area);
```

### <a name="description"></a>説明

このサービスにより、指定された四角形の重複が検出されます。 重複が見つかった場合、サービスは GX_TRUE と、重複した四角形を返します。

### <a name="parameters"></a>パラメーター

- **first_rectangle**: 最初の四角形
- **second_rectangle**: 2 番目の四角形
- **return_overlap_area**: 重複する四角形の領域

### <a name="return-values"></a>戻り値

- **result**: 四角形が重複している場合は GX_TRUE、それ以外の場合は GX_FALSE。

### <a name="allowed-from"></a>許可元

すべて

### <a name="example"></a>例

```C
/* Detect overlap of “my_rectangle_a” and “my_rectangle_b”. */
result = gx_utility_rectangle_overlap_detect(&my_rectangle_a,
    &my_rectangle_b,
    &my_overlap_area);

/* If result is GX_TRUE, “my_overlap_area” specifies the area the
rectangles overlap. */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_point_detect"></a>gx_utility_rectangle_point_detect

ポイントが四角形内に存在するかを検出する

### <a name="prototype"></a>プロトタイプ

```C
GX_BOOL gx_utility_rectangle_point_detect(
    GX_RECTANGLE *rectangle,
    GX_POINT point);
```

### <a name="description"></a>説明

このサービスにより、指定されたポイントが四角形内に存在するかどうかが検出されます。 ポイントが四角形内に存在する場合、サービスは GX_TRUE を返します。

### <a name="parameters"></a>パラメーター

- **rectangle**: 四角形
- **point**: ポイント

### <a name="return-values"></a>戻り値

- **result**: ポイントが四角形内に存在する場合は GX_TRUE、それ以外の場合は GX_FALSE

### <a name="allowed-from"></a>許可元

すべて

### <a name="example"></a>例

```c
GX_RECTANGLE my_rectangle;

GX_POINT my_point;

gx_utility_rectangle_define(&my_rectangle, 0, 0, 100, 100);

my_point.gx_point_x = 20; my_point.gx_point_y = 20;

/* Detect if point “my_point” is within “my_rectangle””. */
result = gx_utility_rectangle_point_detect(&my_rectangle,
    &my_point);

/* If result is GX_TRUE, “my_point” resides in the rectangle. */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_resize"></a>gx_utility_rectangle_resize

四角形を拡張する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_utility_rectangle_resize(
    GX_RECTANGLE *rectangle,
    GX_VALUE adjust);
```

### <a name="description"></a>説明

このサービスにより、四角形のサイズが指定どおりに拡張されます。

### <a name="parameters"></a>パラメーター

- **rectangle**: 四角形へのポインター
- **adjust**: 四角形を調整する量

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 四角形のサイズ変更に成功しました
- **GX_PTR_ERROR**: (0x07) 入力四角形ポインターが無効です

### <a name="allowed-from"></a>許可元

すべて

### <a name="example"></a>例

```C
UINT status;

/* Adjust “my_rectangle” by increasing 20 pixels on four sides */
status = gx_utility_rectangle_resize(&my_rectangle, 20);

/* If status is GX_SUCCESS, “my_rectangle” is 20 pixels larger. */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_shift"></a>gx_utility_rectangle_shift

四角形をシフトする

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_utility_rectangle_shift(
    GX_RECTANGLE *rectangle,
    GX_VALUE x_shift,
    GX_VALUE y_shift);
```

### <a name="description"></a>説明

このサービスにより、指定された値で四角形がシフトされます。

### <a name="parameters"></a>パラメーター

- **rectangle**: シフトする四角形
- **x_shift** X 軸でシフトするピクセル数
- **y_shift** Y 軸でシフトするピクセル数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) 四角形のシフトに成功しました
- **GX_PTR_ERROR**: (0x07) 入力四角形ポインターが無効です

### <a name="allowed-from"></a>許可元

すべて

### <a name="example"></a>例

```C
UINT status;

/* Shift “my_rectangle”. */

status = gx_utility_rectangle_shift(&my_rectangle, 10, 20);

/* If status is GX_SUCCESS, “my_rectangle” has been shifted. */
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect

## <a name="gx_utility_string_to_alphamap"></a>gx_utility_string_to_alphamap

文字列を 8bpp alphamap 型のピクセルマップにレンダリングする (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_utility_string_to_alphamap(
    const GX_CHAR *text, const
    GX_FONT *font, 
    GX_PIXELMAP *return_map);
```

### <a name="description"></a>説明

gx_utility_string_to_alphamap_ext() を優先して、このサービスは非推奨になりました。

このサービスは、テキスト文字列を alphamap にレンダリングします。これは、アルファ値のみを含む特殊な形式の 8bpp ピクセルマップです。 通常、このサービスは gx_utility_pixelmap_rotate および gx_canvas_pixelmap_draw と共に使用して、回転したテキストをキャンバスに描画します。

このサービスは、結果として得られる alphamap に必要なメモリ サイズを計算し、アプリケーションによって定義された gx_system_memory_allocator() 関数を呼び出してメモリを動的に割り当てます。 アプリケーションは、このサービスを使用する前に、通常はプログラムの起動時に gx_system_memory_allocator_set() を呼び出す必要があります。

テキスト文字列を回転してキャンバスに一度だけ描画する場合は、代替としてサービス gx_canvas_rotated_text_draw() が提供されています。 gx_canvas_rotated_text_draw() は、gx_utility_string_to_alphamap()、gx_utility_pixelmap_rotate()、および gx_canvas_pixelmap_draw() を呼び出して、1 回の操作で回転したテキストをレンダリングします。 ただし、同じテキストがさまざまな角度で回転されて複数回描画される場合は、gx_utility_string_to_alphmap API を使用して alphamap を 1 回作成した後、必要に応じて結果の alphamap を複数回回転する方が効率的です。

### <a name="parameters"></a>パラメーター

- **text**: alphamap にレンダリングするテキスト文字列
- **font**: テキストをレンダリングするためのフォント
- **return_map**: 呼び出し元に返される GX_PIXELMAP へのポインター。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) テキスト文字列を alphamap に正常にレンダリングしました
- **GX_PTR_ERROR** (0x07) 入力ポインターが無効です
- **GX_SYSTEM_MEMORY_ERROR** (0x30) メモリ割り当て/free 関数が定義されていません
- **GX_INVALID_STRING_LENGTH**: (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_PIXELMAP alphamap;

GX_PIXELMAP rotated_text;

INT xpos;

INT ypos;

gx_widget_font_get(widget, GX_FONT_ID_SCREEN_LABEL, &font);

/* render string to alphamap once */

gx_utility_string_to_alphamap("Hello World", font, &alphamap);

/* rotate and render the alphmap at multiple angles */

gx_utility_pixelmap_rotate(&alphamap, 45, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(10, 10, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 135, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(100, 100, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 300, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(200, 200, &rotated_text);
```

### <a name="see-also"></a>参照

- gx_utility_string_to_alphamap_ext

## <a name="gx_utility_string_to_alphamap_ext"></a>gx_utility_string_to_alphamap_ext

文字列を 8bpp alphamap 型のピクセルマップにレンダリングする

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_utility_string_to_alphamap_ext(
    GX_CONST GX_STRING *string,
    GX_CONST GX_FONT *font, 
    GX_PIXELMAP *return_map);
```

### <a name="description"></a>説明

このサービスは、テキスト文字列を alphamap にレンダリングします。これは、アルファ値のみを含む特殊な形式の 8bpp ピクセルマップです。 通常、このサービスは gx_utility_pixelmap_rotate および gx_canvas_pixelmap_draw と共に使用して、回転したテキストをキャンバスに描画します。

このサービスは、結果として得られる alphamap に必要なメモリ サイズを計算し、アプリケーションによって定義された gx_system_memory_allocator() 関数を呼び出してメモリを動的に割り当てます。 アプリケーションは、このサービスを使用する前に、通常はプログラムの起動時に gx_system_memory_allocator_set() を呼び出す必要があります。

テキスト文字列を回転してキャンバスに一度だけ描画する場合は、代替としてサービス gx_canvas_rotated_text_draw() が提供されています。 gx_canvas_rotated_text_draw() は、gx_utility_string_to_alphamap()、gx_utility_pixelmap_rotate()、および gx_canvas_pixelmap_draw() を呼び出して、1 回の操作で回転したテキストをレンダリングします。 ただし、同じテキストがさまざまな角度で回転されて複数回描画される場合は、gx_utility_string_to_alphmap API を使用して alphamap を 1 回作成した後、必要に応じて結果の alphamap を複数回回転する方が効率的です。

### <a name="parameters"></a>パラメーター

- **string**: alphamap にレンダリングするテキスト文字列
- **font**: テキストをレンダリングするためのフォント
- **return_map**: 呼び出し元に返される GX_PIXELMAP へのポインター。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS**: (0x00) テキスト文字列を alphamap に正常にレンダリングしました
- **GX_PTR_ERROR** (0x07) 入力ポインターが無効です
- **GX_SYSTEM_MEMORY_ERROR** (0x30) メモリ割り当て/free 関数が定義されていません
- **GX_INVALID_STRING_LENGTH**: (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_STRING string;

GX_PIXELMAP alphamap;

GX_PIXELMAP rotated_text;

INT xpos;

INT ypos;

gx_widget_font_get(widget, GX_FONT_ID_SCREEN_LABEL, &font);

string.gx_string_ptr = “Hello World”;

string.gx_string_length = strlen(string.gx_string_ptr);

/* render string to alphamap once */
gx_utility_string_to_alphamap_ext(&string, font, &alphamap);

/* rotate and render the alphmap at multiple angles */
gx_utility_pixelmap_rotate(&alphamap, 45, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(10, 10, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 135, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(100, 100, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 300, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(200, 200, &rotated_text);
```

### <a name="see-also"></a>参照

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect

## <a name="gx_vertical_list_children_position"></a>gx_vertical_list_children_position
### <a name="position-children-for-the-vertical-list"></a>縦のリストに子を配置する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_vertical_list_children_position(
    GX_VERTICAL_LIST *vertical_list)
```

### <a name="description"></a>説明

この関数は、縦のリストの子を配置します。

### <a name="parameters"></a>パラメーター

- **vertical_list** 縦のリストのコントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 縦のリストの子を正常に配置しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Position children in the vertical list */
status = gx_vertical_list_children_position (&vertical_list);

/* If status is GX_SUCCESS the children in the vertical list are positioned.. */
```

### <a name="see-also"></a>参照

- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selecgted_widget_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_create"></a>gx_vertical_list_create
### <a name="create-vertical-list"></a>縦のリストを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_vertical_list_create(
    GX_VERTICAL_LIST *vertical_list,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent, 
    INT total_rows,
    VOID (*callback)(GX_VERTICAL_LIST *, GX_WIDGET *, INT),
    ULONG style, USHORT vertical_list_id,
    GX_CONST GX_RECTANGLE *size);
```
### <a name="description"></a>説明

このサービスにより、縦のリストが作成されます。

GX_VERTICAL_LIST は GX_WINDOW から派生し、すべての gx_window API サービスをサポートします。

### <a name="parameters"></a>パラメーター

- **vertical_list** 縦のリストのウィジェット コントロール ブロック
- **name** 縦のリストの名前
- **parent** 親ウィジェットへのポインター
- **total_rows** 縦のリストの合計行数
- **callback** リストがスクロールされるときに縦のリストによって呼び出される関数。 呼び出し元により、最初に、表示されるリスト行を埋めるために十分な GX_WIDGET ベースの子を作成する必要があります。 リストがスクロールされると、この関数が呼び出され、指定されたリスト インデックスに対応する子リストが再作成されます。
- **style** スクロール バー ウィジェットのスタイル。 **Appendix D** には、ウィジェット固有のスタイルだけでなく、すべてのウィジェット用に事前に定義された一般的なスタイルが含まれています。
- **vertical_list_id** アプリケーションで定義された、縦のリストの ID
- **size** 縦のリストのディメンション

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 縦のリストの作成に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です
- **GX_INVALID_VALUE** (0x22) 行数が無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Create vertical list “my_list” with 20 rows. */
status = gx_vertical_list_create(&my_list, “my_list”, &my_parent,
                    20, callback, GX_STYLE_WRAP, MY_LIST_ID,
                    &size);

/* If status is GX_SUCCESS the vertical list “my_list” has been created. */
```

### <a name="see-also"></a>参照

- gx_vertical_list_children_position
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_event_process"></a>gx_vertical_list_event_process
### <a name="process-vertical-list-event"></a>縦のリストのイベントを処理する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_vertical_list_event_process(GX_VERTICAL_LIST *list,
                                                      GX_EVENT *event);
```

### <a name="description"></a>説明

このサービスにより、縦のリストのイベントが処理されます。

### <a name="parameters"></a>パラメーター

- **list** 縦のリストのウィジェット コントロール ブロック
- **event** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 縦のリストのイベント処理に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Process “my_event” for vertical list “my_list”. */
status = gx_vertical_list_event_process(&my_list, &my_event);

/* If status is GX_SUCCESS the event for vertical list “my_list” has been processed. */
```

### <a name="see-also"></a>参照

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_selected_set

## <a name="gx_vertical_list_page_index_set"></a>gx_vertical_list_page_index_set
### <a name="set-starting-page-index"></a>開始ページのインデックスを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_vertical_list_page_index_set(
    GX_VERTICAL_LIST *list,
    INT index);
```
### <a name="description"></a>説明

このサービスにより、縦のリストの開始インデックスが設定されます。

### <a name="parameters"></a>パラメーター

- **list** 縦のリストのウィジェット コントロール ブロック
- **index** 新しい上位インデックス

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 縦のリストの開始ページ インデックスの設定に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ウィジェット ポインターが無効です
- **GX_INVALID_VALUE** (0x22) インデックス値が無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the starting page index of vertical list “my_list” to 4. */
status = gx_vertical_list_page_index_set(&my_list, 4);

/* If status is GX_SUCCESS the starting page index of “my_list” has
been set to 4. */
```
### <a name="see-also"></a>参照

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_selected_index_get"></a>gx_vertical_list_selected_index_get
### <a name="get-selected-index-from-vertical-list"></a>選択したインデックスを縦のリストから取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_vertical_list_selected_index_get(
    GX_VERTICAL_LIST *vertical_list,
    INT *return_index);
```
### <a name="description"></a>説明

このサービスにより、縦のリストの選択されたインデックスが返されます

### <a name="parameters"></a>パラメーター

- **vertical_list** 縦のリストのウィジェット コントロール ブロック
- **return_index** 選択されたインデックスを返す宛先

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 垂直リスト エントリの取得に成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
INT current_selected_index;

/* Get the list entry at the current index of vertical list “my_list”. */
status = gx_vertical_list_selected_index_get(&my_list, &current_selected_index);

/* If status is GX_SUCCESS, “current_list_index” contains the index of the selected list item. */
```
### <a name="see-also"></a>参照

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_selected_set"></a>gx_vertical_list_selected_set
### <a name="assign-the-selected-entry-in-a-vertical-list"></a>選択したエントリを縦のリストに割り当てる

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_vertical_list_selected_set(
    GX_VERTICAL_LIST *vertical_list,
    INT index);
```

### <a name="description"></a>説明

このサービスでは、縦のリストに選択したエントリが割り当てられます。 必要に応じて、選択したエントリが表示されるように縦のリストがスクロールします。

### <a name="parameters"></a>パラメーター

- **vertical_list** 縦のリストのウィジェット コントロール ブロック
- **index** 新しいリスト エントリのインデックスに基づく位置

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 縦のリスト エントリの設定に成功しました
- **GX_FAILURE** (0x10) 入力されたインデックスがリストに見つかりません
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) 縦のリストまたはリスト エントリ ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the list entry of “my_list” to the child in line 12. */
status = gx_vertical_list_selected_set(&my_list, 12);

/* If status is GX_SUCCESS, the list entry of “my_list” has been successfully set to 12. */
```
### <a name="see-also"></a>参照

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_get
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_selected_widget_get"></a>gx_vertical_list_selected_widget_get
### <a name="get-selected-widget-from-vertical-list"></a>縦のリストから選択したウィジェットを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_vertical_list_selected_widget_get(
    GX_VERTICAL_LIST *vertical_list,
    GX_WIDGET **return_list_entry);
```
### <a name="description"></a>説明

このサービスは、縦のリストの選択したウィジェットを返します。 リストに子ウィジェットよりも多い行が含まれており、選択した子ウィジェットがビューからスクロールされている場合、この関数は GX_WIDGET ポインターとして GX_NULL を返します。これは、新しいリスト エントリを表示するためにウィジェットが再利用されたためです。

### <a name="parameters"></a>パラメーター

- **vertical_list** 縦のリストのウィジェット コントロール ブロック
- **return_list_entry** 返されたリスト エントリ ウィジェットの宛先

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 垂直リスト エントリの取得に成功しました
- **GX_FAILURE** (0x10) 選択したウィジェットがビューからスクロールされました。
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_WIDGET *current_selected_widget;

/* Get the list entry at the current index of vertical list “my_list”. */
status = gx_vertical_list_selected_widget_get(&my_list, &current_selected_widget);

/* If status is GX_SUCCESS, “current_list_entry” contains a pointer to the currently selected widget. */
```

### <a name="see-also"></a>参照

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_total_rows_set"></a>gx_vertical_list_total_rows_set
### <a name="set-total-number-of-vertical-list-rows"></a>縦リストの合計行数を設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_vertical_list_total_rows_set(
    GX_VERTICAL_LIST *vertical_list,
    INT count);
```
### <a name="description"></a>説明

このサービスは、リスト行の合計数を割り当てまたは変更します。

### <a name="parameters"></a>パラメーター

- **vertical_list** 縦のリストのウィジェット コントロール ブロック
- **count** 新しいリストの行数

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 縦リストの行数の設定に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE** (0x22) 行数値が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set the list row count to 20 items. */
status = gx_vertical_list_total_rows_set(&my_list, 20);

/* If status is GX_SUCCESS, the total rows of “my_list” has been set to 20. */
```
### <a name="see-also"></a>参照

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set

## <a name="gx_vertical_scrollbar_create"></a>gx_vertical_scrollbar_create
### <a name="create-vertical-scrollbar"></a>垂直スクロール バーを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_vertical_scrollbar_create(
    GX_SCROLLBAR *scrollbar,
    GX_CONST GX_CHAR *name, 
    GX_WINDOW *parent,
    GX_SCROLLBAR_APPEARANCE *appearance,
    ULONG style);
```
### <a name="description"></a>説明

このサービスでは、垂直スクロールバーが作成されます。

### <a name="parameters"></a>パラメーター

- **scrollbar** スクロール バーのウィジェット コントロール ブロック
- **name** スクロール バーの名前
- **parent** 親ウィジェットへのポインター
- **appearance** 垂直スクロールバー ウィジェットの外観。
- **style** スクロールバーのスタイル。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 垂直スクロール バーの作成に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE**: (0x19) ウィジェット コントロール ブロック サイズが無効です
- **GX_INVALID_WIDGET** (0x12) 親ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Create vertical scrollbar “my_scrollbar”. */
status = gx_vertical_scrollbar_create(&my_scrollbar,
                          “my_vertical_scrollbar”,
                          &my_parent, &scrollbar_appearance,
                          GX_STYLE_ENABLED);

/* If status is GX_SUCCESS the vertical scrollbar “my_scrollbar” has been created. */
```
### <a name="see-also"></a>参照

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_scrollbar_reset

## <a name="gx_widget_allocate"></a>gx_widget_allocate
### <a name="allocate-a-widget-control-block"></a>ウィジェット コントロール ブロックを割り当てる

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_allocate(
    GX_WIDGET **control_block,
    ULONG memsize);
```
### <a name="description"></a>説明

このサービスは、アプリケーション定義のメモリ割り当て関数を呼び出すことによって、ウィジェット コントロール ブロックを動的に割り当てます。 このサービスは主に GUIX Studio によって生成される関数によって使用され、GUIX Studio のプロパティ ビューで [動的割り当て] プロパティが選択されている場合に、コントロール ブロックを動的に割り当てます。

### <a name="parameters"></a>パラメーター

- **control_block** 返されたコントロール ブロック ポインターへのポインター
- **memsize** コントロール ブロック サイズ (バイト単位)

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの割り当てに成功しました
- **GX_SYSTEM_MEMORY_ERROR** (0x30) メモリ アロケーターが定義されていないか、メモリの割り当てに失敗しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_MEMORY_SIZE** (0x29) メモリ サイズが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_TEXT_BUTTON *button;

/* Attach “my_widget” to “my_parent”. */
status = gx_widget_allocate(&button, sizeof(GX_TEXT_BUTTON));

/* If status is GX_SUCCESS the button widget control block is allocated. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_attach"></a>gx_widget_attach
### <a name="attach-widget-to-its-parent"></a>ウィジェットを親にアタッチする

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_attach(
    GX_WIDGET *parent, 
    GX_WIDGET *widget);
```
### <a name="description"></a>説明

このサービスにより、ウィジェットが、指定された親にアタッチされます。 ウィジェットが既に別の親にアタッチされている場合は、まずデタッチされます。 ウィジェットが既に同じ親にアタッチされている場合、この関数は何も行いません。

ウィジェットは、z 順序付けの観点から親の最上位の子になります。 兄弟ウィジェットが重なる場合、このウィジェットは兄弟の上に描画されます。 新しいウィジェットを z 順序の背面に配置するには、gx_widget_back_attach または gx_widget_back_move を使用します。

### <a name="parameters"></a>パラメーター

- **parent** 親ウィジェットへのポインター
- **widget** 子ウィジェットへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットのアタッチに成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) 親またはウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Attach “my_widget” to “my_parent”. */
status = gx_widget_attach(&my_parent, &my_widget);

/* If status is GX_SUCCESS the widget “my_widget” is attached to “my_parent”. */
```

### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_background_draw"></a>gx_widget_background_draw
### <a name="draw-a-widget-background"></a>ウィジェットの背景を描画する

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_widget_background_draw(GX_WIDGET *widget);
```
### <a name="description"></a>説明

このサービスにより、ウィジェットの背景が単色で塗りつぶされます。 このサービスは、gx_widget_draw 関数によって自動的に呼び出されますが、カスタマイズされたウィジェット描画関数の一部としてアプリケーションによって呼び出されることもあります。

### <a name="parameters"></a>パラメーター

- **widget** 描画するウィジェットへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom widget draw function. */

VOID my_widget_draw(GX_WIDGET * widget)
{
    /* Call default widget background draw. */
    gx_widget_background_draw(widget);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw(widget);
}
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_back_attach"></a>gx_widget_back_attach
### <a name="attach-widget-to-its-parent"></a>ウィジェットを親にアタッチする

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_back_attach(
    GX_WIDGET *parent, 
    GX_WIDGET *widget);
```
### <a name="description"></a>説明

このサービスにより、ウィジェットが、指定された親にアタッチされます。 ウィジェットが既に別の親にアタッチされている場合は、まずデタッチされます。 ウィジェットが既に同じ親にアタッチされている場合は、この関数は何も行いません。

ウィジェットは、z 順序付けの観点から、親の最下位の子になります。 兄弟ウィジェットが重なる場合、このウィジェットはそれらの兄弟の背後に描画されます。 新しいウィジェットを z 順序の前に配置するには、gx_widget_back_attach または gx_widget_back_move を使用します。

### <a name="parameters"></a>パラメーター

- **parent** 親ウィジェットへのポインター
- **widget** 子ウィジェットへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットのアタッチに成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) 親またはウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Attach “my_widget” to “my_parent”. */
status = gx_widget_back_attach(&my_parent, &my_widget);

/* If status is GX_SUCCESS the widget “my_widget” is attached to “my_parent”. */
```
### <a name="see-also"></a>参照

- gx_widget_back_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_back_move"></a>gx_widget_back_move
### <a name="move-widget-to-back"></a>ウィジェットを背面へ移動する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_back_move(
    GX_WIDGET *widget,
    GX_BOOL *return_widget_moved);
```
### <a name="description"></a>説明

このサービスにより、ウィジェットが、子ウィジェットの親の Z 順序の後ろに移動されます。

### <a name="parameters"></a>パラメーター

- **parent** 親ウィジェットへのポインター
- **return_widget_moved** ウィジェットが移動されたことを示すフラグの宛先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの背面への移動に成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_NO_CHANGE** (0x08) 変更は適用されません
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Move “my_widget” to the back. */
status = gx_widget_back_move(&my_widget, &moved_flag);

/* If status is GX_SUCCESS and “moved_flag” is GX_TRUE, the widget “my_widget” was moved to the back. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_block_move"></a>gx_widget_block_move
### <a name="move-a-rectangular-block-of-pixels"></a>四角形のピクセル ブロックを移動する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_block_move(
    GX_WIDGET *widget,
    GX_RECTANGLE *block,
    INT xshift, INT yshift);
```

### <a name="description"></a>説明

このサービスにより、ピクセルの四角形のブロックが移動されます。 このサービスは、高速スクロールを実装するために頻繁に使用されます。

### <a name="parameters"></a>パラメーター

- **widget** ブロック移動を要求するウィジェットへのポインター
- **block** 境界線で囲まれた移動するブロック
- **xshift** X のシフト量 (ピクセル単位)
- **yshift** Y のシフト量 (ピクセル単位)

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの背面への移動に成功しました
- **GX_INVALID_CANVAS** (0x20) ウィジェット キャンバスが見つかりません
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Move a block of pixels 20 pixels to the right. */
status = gx_widget_block_move(&my_widget, &size, 20, 0);

/* If status is GX_SUCCESS the block of pixels was moved. */
```

### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_border_draw"></a>gx_widget_border_draw
### <a name="draw-widget-border"></a>ウィジェットの枠線の描画

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_widget_border_draw(
    GX_WIDGET *widget,
    GX_COLOR border_color,
    GX_COLOR upper_fill, 
    GX_COLOR lower_fill, 
    GX_BOOL fill);
```

### <a name="description"></a>説明

このサービスにより、ウィジェットの枠線が描画されます。 通常このサービスは、ウィジェットの描画関数の一部として呼び出されます。 このサービスにより、ウィジェットの枠線スタイルのフラグが解釈され、枠線なし、または、細い枠線、浮き出た枠線、くぼんだ枠線、太い枠線が描画されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **border_color** 枠線の色。 **付録 A** には事前定義済みの色が含まれています。 アプリケーションでは、カスタムの色も追加できることに注意してください。
- **upper_fill** 上の塗りつぶしの色。 **付録 A** には事前定義済みの色が含まれています。 アプリケーションでは、カスタムの色も追加できることに注意してください。
- **lower_fill** 下の塗りつぶしの色。 **付録 A** には事前定義済みの色が含まれています。 アプリケーションでは、カスタムの色も追加できることに注意してください。
- **fill** このブール型のフラグは、ウィジェット領域を、指定された塗りつぶしの色で塗りつぶすかどうかを示します。 この値が GX_FALSE 場合は、ウィジェットの枠線だけが描画されます。

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom widget draw function. */

VOID my_widget_draw(GX_WIDGET * widget)
{
      /* Call widget border draw. */
      gx_widget_border_draw(widget, GX_COLOR_BLACK,
                            GX_COLOR_GREEN, GX_COLOR_BLUE,
                            GX_TRUE);

      /* Add your own drawing here. */

      /* Draw child widgets. */
      Gx_widget_children_draw(widget);
}
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_border_style_set"></a>gx_widget_border_style_set
### <a name="set-widget-border-style"></a>ウィジェットの枠線のスタイルを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_border_style_set(
    GX_WIDGET *widget, 
    ULONG style);
```

### <a name="description"></a>説明

このサービスにより、ウィジェットの枠線のスタイルが設定されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **style** 枠線のスタイル。 **付録 D** には、ウィジェット固有のスタイルだけでなく、すべてのウィジェット用に事前に定義された一般的なスタイルが含まれています。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの枠線のスタイル設定に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set border style of “my_widget”. */
status = gx_widget_border_style_set(&my_widget,
                                    GX_STYLE_BORDER_RAISED);

/* If status is GX_SUCCESS the widget “my_widget” border style has been set. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_border_width_get"></a>gx_widget_border_width_get
### <a name="get-widget-border-width"></a>ウィジェットの枠線の幅を取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_border_width_get(
    GX_WIDGET *widget,
    GX_VALUE *return_width);
```

### <a name="description"></a>説明

このサービスにより、ウィジェットの枠線の幅が取得されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **return_width** ウィジェットの枠線の幅の宛先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 枠線の幅の取得に成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_VALUE my_width;

/* Get border width of “my_widget”. */
status = gx_widget_border_width_get(&my_widget, &my_width);

/* If status is GX_SUCCESS, “my_width” contains the border width of the widget “my_widget”. */
```

### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_canvas_get"></a>gx_widget_canvas_get
### <a name="get-widget-canvas"></a>ウィジェット キャンバスを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_canvas_get(
    GX_WIDGET *widget,
    GX_CANVAS **return_canvas)
```
### <a name="description"></a>説明

このサービスにより、このウィジェットがレンダリングされるキャンバスへのポインターが返されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **return_canvas** ウィジェットのキャンバスの宛先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットのキャンバス取得に成功しました
- **GX_FAILURE** (0x10) ウィジェットのキャンバスが見つかりません
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Get canvas associated with “my_widget”. */
status = gx_widget_canvas_get(&my_widget, &my_canvas);

/* If status is GX_SUCCESS, “my_canvas” contains the canvas of the widget “my_widget”. */
```

### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_child_detect"></a>gx_widget_child_detect
### <a name="detect-widget-child"></a>ウィジェットの子を検出する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_child_detect(
    GX_WIDGET *parent, 
    GX_WIDGET *child,
    GX_BOOL *return_detect);
```

### <a name="description"></a>説明

このサービスにより、ウィジェットが親ウィジェットの子であるかどうかが検出されます。 このサービスは、子の子を検索するために入れ子にし、親ウィジェットが子ウィジェットの任意レベルの先祖である場合に TRUE を返します。

### <a name="parameters"></a>パラメーター

- **parent** 親ウィジェットへのポインター
- **child** 子ウィジェットへのポインター
- **return_detect** 検出の宛先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの子の検出に成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) 親または子ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_BOOL detected;

/* Determine if “my_child” is a child of “my_widget”. */
status = gx_widget_child_detect(&my_widget, &my_child, &detected);

/* If status is GX_SUCCESS and “detected” is GX_TRUE, “my_child” is a child of widget “my_widget”. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_children_draw"></a>gx_widget_children_draw
### <a name="draw-widget-children"></a>ウィジェットの子を描画する

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_widget_children_draw(GX_WIDGET *widget);
```

### <a name="description"></a>説明

このサービスにより、親ウィジェットのすべての子が描画されます。 このサービスは通常、すべての標準ウィジェット描画関数によって呼び出され、既存の子ウィジェットを描画します。また、子ウィジェットをカスタムの親ウィジェットの種類にアタッチできるようにするためには、カスタム描画関数から呼び出す必要があります。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom widget draw function. */

VOID my_widget_draw(GX_WIDGET * widget)
{
        /* Call default widget background draw. */
        gx_widget_background_draw(widget);

        /* Add your own drawing here. */

        /* Draw child widgets. */
        gx_widget_children_draw(widget);
}
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_client_get"></a>gx_widget_client_get
### <a name="get-widget-client-area"></a>ウィジェット クライアント領域を取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_client_get(
    GX_WIDGET *widget,
    GX_VALUE border_width,
    GX_RECTANGLE *return_client_area);
```
### <a name="description"></a>説明

このサービスにより、ウィジェットのサイズ全体からウィジェットの枠線の幅が引かれ、ウィジェットのクライアント領域が計算されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **border_width** ウィジェットの枠線の幅
- **return_client_area** クライアント領域を返す宛先

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェット クライアント領域の取得に成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE** (0x22) ウィジェットの枠線が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_RECTANGLE client_area
/* Get client area of widget “my_widget”. */
status = gx_widget_client_get(&my_widget, my_widget_width,
                              &client_area);

/* If status is GX_SUCCESS, the “client_area” is the client area of “my_widget”. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_color_get"></a>gx_widget_color_get
### <a name="get-color"></a>色を取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_color_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID resource_id,
    GX_COLOR *return_color);
```

### <a name="description"></a>説明

このサービスにより、指定されたリソース ID に関連付けられている色が取得されます。 このサービスは、表示可能なウィジェットでのみ呼び出します。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェット コントロール ブロックへのポインター
- **resource_id** 色のリソース ID。 **付録 B** には、定義済みの色リソース ID が含まれています。 アプリケーションでは、カスタムの色リソース ID も追加できることに注意してください。
- **return_color** 色の宛先へのポインター。 **付録 A** には定義済みの色が含まれています。 なお、アプリケーションでカスタムの色を追加することもできます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 色の取得に成功しました
- **GX_INVALID_RESOURCE_ID** (0x33) 無効なリソース ID
- **GX_INVALID_CANVAS** (0x20) ウィジェット キャンバスが無効であるか、ウィジェットが非表示です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_COLOR actual_color;

/* Get color for resource ID MY_FIRST_COLOR_ID. */
status = gx_widget_color_get(my_widget, MY_FIRST_COLOR_RESOURCE_ID,
                            &actual_color);

/* If status is GX_SUCCESS the actual color is contained in “actual_color”. */
```
### <a name="see-also"></a>参照

- gx_widget_font_get
- gx_widget_pixelmap_get

## <a name="gx_widget_create"></a>gx_widget_create
### <a name="create-widget"></a>ウィジェットを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_create(
    GX_WIDGET *widget, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    ULONG style, 
    USHORT widget_id,
    GX_CONST GX_RECTANGLE *size);
```
### <a name="description"></a>説明

このサービスによりウィジェットが作成されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **name** ウィジェットの論理名
- **parent** 親ウィジェットへのポインター
- **style** スタイル。 **付録 D** には、ウィジェット固有のスタイルだけでなく、すべてのウィジェット用に事前に定義された一般的なスタイルが含まれています。
- **widget_id** アプリケーションで定義された、ウィジェットの ID
- **size** ウィジェットのサイズ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの作成に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE**: (0x19) ウィジェット コントロール ブロック サイズが無効です
- **GX_INVALID_WIDGET** (0x12) 親ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_WIDGET my_widget;
GX_RECTANGLE size;

gx_utility_rectangle_define(&size, 0, 0, 100, 100);

/* Get client area of widget “my_widget”. */
status = gx_widget_create(&my_widget, "my widget",
                          &my_parent_window, GX_STYLE_BORDER_RAISED, MY_WIDGET_ID, &size);

/* If status is GX_SUCCESS, the widget “my_widget” has been created. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_created_test"></a>gx_widget_created_test
### <a name="test-if-widget-created"></a>ウィジェットが作成されたことをテストする

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_created_test(
    GX_WIDGET *widget,
    GX_BOOL *return_test);
```
### <a name="description"></a>説明

このサービスにより、ウィジェットが以前に作成されているかどうかがテストされます。 エラーが発生しなかった場合、ウィジェットが作成されているかどうかに関係なく、この関数により GX_SUCCESS が返されます。 テストの結果は return_test ポインターにあります。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **return_test** テスト結果の出力先

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) テストが正常に完了しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_BOOL was_created;

/* Test to see if widget “my_widget” is created. */
status = gx_widget_created_test(&my_widget, &was_created);

/* If status is GX_SUCCESS, no error occurred. If “was_created” is
GX_TRUE, the widget “my_widget” has been created. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_delete"></a>gx_widget_delete
### <a name="delete-widget"></a>ウィジェットを削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_delete(GX_WIDGET *widget);
```

### <a name="description"></a>説明

このサービスにより、ウィジェットが削除されます。 ウィジェット コントロール ブロックが動的に割り当てられている場合は、動的に割り当てられたストレージを解放するために、gx_system_memory_free サービスが呼び出されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの削除に成功しました GX_CALLER_ERROR (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_SYSTEM_MEMPRY_ERROR** (0x30) メモリ解放関数が定義されていません

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Delete widget “my_widget”. */
status = gx_widget_delete(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” has been deleted. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_detach"></a>gx_widget_detach
### <a name="detach-widget-from-parent"></a>親からウィジェットをデタッチする

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_detach(GX_WIDGET *widget);
```

### <a name="description"></a>説明

このサービスにより、ウィジェットが親からデタッチされます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットのデタッチに成功しました GX_CALLER_ERROR (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Detach widget “my_widget” from its parent. */
status = gx_widget_detach(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” has been detached. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_draw"></a>gx_widget_draw
### <a name="draw-widget"></a>ウィジェットを描画する

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_widget_draw(GX_WIDGET *widget);
```

### <a name="description"></a>説明

このサービスによりウィジェットが描画されます。 通常、この関数は GUIX キャンバスの更新機構によって内部的に呼び出されますが、カスタム描画関数の実装を支援するためにアプリケーションに公開されています。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom widget draw function. */

VOID my_custom_widget_draw(GX_WIDGET *widget)
{
      /* Call default widget draw. */
      gx_widget_draw(widget);

      /* Add your own drawing here. */
}
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_draw_set"></a>gx_widget_draw_set
### <a name="assign-the-widget-drawing-function"></a>ウィジェット描画関数を割り当てる

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_draw_set(
    GX_WIDGET *widget,
    VOID (*drawing_function) (GX_WIDGET *));
```

### <a name="description"></a>説明

このサービスにより、ウィジェットのデフォルトの描画関数がオーバーライドされます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **drawing_function** 描画関数へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェット描画関数のオーバーライドに成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Define a custom drawing function. */
VOID my_drawing_function(GX_WIDGET *widget)
{
      /* Add your own drawing here. */
}

/* Set the drawing function of widget “my_widget” to “my_drawing_function”. */
status = gx_widget_draw_set(&my_widget, my_drawing_function);

/* If status is GX_SUCCESS the widget “my_widget” has the drawning function “my_drawing_function”. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_event_generate"></a>gx_widget_event_generate
### <a name="generate-widget-event"></a>ウィジェット イベントを生成する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_event_generate(
    GX_WIDGET *widget, 
    USHORT event_type, LONG value);
```

### <a name="description"></a>説明

このサービスにより、GX_EVENT の特定の型またはクラスである GX_SIGNAL 型のイベントが生成されます。 gx_widget_event_generate() は、16 ビット ウィジェット ID を、渡された event_type と共に 1 つの 32 ビット GX_EVENT.gx_event_type 値にエンコードします。 値パラメーターは、生成された gx_event. gx_event_payload.gx_event_longdata フィールドにエンコードされます。

生成された event.gx_event_target フィールドは、常に呼び出し元のウィジェットの親と共に読み込まれます。つまり、生成されたイベントは常に、生成元のウィジェットの親に対して最初に送信されます。

gx_widget_event_generate は、GX_SIGNAL 範囲のイベントの種類を送信する場合にのみ使用することに注意してください。 ユーザー定義のイベントの種類など、他のすべてのイベントの種類では、gx_system_event_send() API を使用します。これにより、GUIX イベント キューにプッシュされるイベントのすべてのフィールドに対するフル コントロールが許可されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **event_type** イベントの種類。 **付録 E** には、事前定義済みの GUIX イベントが含まれています。 アプリケーションによって追加のイベントが追加される場合があります。
- **value** 追加のイベント情報

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェット イベントの生成に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Generate a redraw event for widget “my_widget”. */
status = gx_widget_event_generate(&my_widget, GX_EVENT_REDRAW, 0);

/* If status is GX_SUCCESS the redraw event for widget “my_widget” has been generated. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get
- gx_system_event_send

## <a name="gx_widget_event_process"></a>gx_widget_event_process
### <a name="process-widget-event"></a>ウィジェット イベントを処理する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_event_process(
    GX_WIDGET *widget, 
    GX_EVENT *event);
```

### <a name="description"></a>説明

これは、すべてのウィジェットのデフォルトのイベント処理関数です。 カスタム イベント処理関数が記述されている場合、任意のイベントの種類のデフォルト アクションは、常にウィジェットの基になるウィジェットの種類にイベントを渡すことです。 最も基本的な GX_WIDGET の種類のパスに基づいたウィジェットは、デフォルトのイベント処理関数として gx_widget_event_process を使用します。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **event** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェット イベントの処理に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Process event “my_event” for widget “my_widget”. */
status = gx_widget_event_process(&my_widget, &my_event);

/* If status is GX_SUCCESS the event “my_event” for widget “my_widget” has been processed. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_event_process_set"></a>gx_widget_event_process_set
### <a name="set-event-processing-function-of-widget"></a>ウィジェットのイベント処理関数を設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_event_process_set(
    GX_WIDGET *widget,
    UINT (*event_processing) (GX_WIDGET *, GX_EVENT *));
```

### <a name="description"></a>説明

このサービスにより、ウィジェットのイベント処理関数がオーバーライドされます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **event_processing** 新しいイベント処理関数へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェット イベント処理のオーバーライドに成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
UINT my_event_process(GX_TREE_VIEW *tree_view,
                      GX_EVENT *event)
{
      UINT status = GX_SUCCESS;

      switch(event->gx_event_type)
      {
      case xyz:
            /* Insert custom event handling here */
            break;

      default:
            /* Pass all other events to the default tree view
               event processing */
            status = gx_tree_view_event_process(tree_view, event);
            break;
      }
      return status;
}

/* Use “my_event_process” to process events for widget “my_tree_view”. */
status = gx_widget_event_process_set((GX_WIDGET *)&my_tree_view,
                    (VOID (*)(GX_WIDGET *))my_event_process);

/* If status is GX_SUCCESS all event processing for widget “my_tree_view” is handled by “my_event_process”. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_event_to_parent"></a>gx_widget_event_to_parent
### <a name="send-event-to-widgets-parent"></a>ウィジェットの親にイベントを送信する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_event_to_parent(
    GX_WIDGET *widget,
    GX_EVENT *event);
```
### <a name="description"></a>説明

このサービスにより、ウィジェットの親にイベントが送信されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **event** イベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの親にイベントが送信されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Send my_event to the widget’s parent */
status = gx_widget_event_to_parent(&my_widget, my_event);

/* If status is GX_SUCCESS the event has been delivered to the parent of my_widget. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_fill_color_set"></a>gx_widget_fill_color_set
### <a name="set-widget-background-color"></a>ウィジェットの背景色を設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_fill_color_set(
    GX_WIDGET *widget,
    GX_RESOURCE_ID normal_color_id,
    GX_RESOURCE_ID selected_color_id,
    GX_RESOURCE_ID disabled_color_id);
```
### <a name="description"></a>説明

このサービスにより、ウィジェットの背景色が設定されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **normal_color_id** 通常状態の塗りつぶしの色のリソース ID。 **付録 A** には、事前定義済みの色リソース ID が含まれています。 アプリケーションでは、カスタムの色リソース ID も追加できることに注意してください。
- **selected_color_id** ウィジェットがフォーカスを得るときの塗りつぶしの色のリソース ID。 **付録 A** には、事前定義済みの色リソース ID が含まれています。 アプリケーションでは、カスタムの色リソース ID も追加できることに注意してください。
- **disabled_color_id** スタイル GX_STYLE_ENABLED が設定されていない場合の塗りつぶしの色のリソース ID。 **付録 A** には、事前定義済みの色リソース ID が含まれています。 なお、アプリケーションでカスタムの色のリソース ID を追加することもできます。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの塗りつぶしの色が設定されました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set background of “my_widget”. */
status = gx_widget_fill_color_set(&my_widget,
                    GX_COLOR_ID_NORMAL_FILL,
                    GX_COLOR_ID_SELECTED_FILL,
                    GX_COLOR_ID_DISABLED_FILL);

/* If status is GX_SUCCESS the widget “my_widget” background has been set. */
```

### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_find"></a>gx_widget_find
### <a name="find-child-widget-of-parent-widget"></a>親ウィジェットの子ウィジェットを検索する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_find(
    GX_WIDGET *parent, 
    USHORT widget_id,
    INT search_depth, 
    GX_WIDGET **return_widget);
```
### <a name="description"></a>説明

このサービスにより、指定された親の子の中から、要求された ID 値を持つウィジェットが検索されます。

### <a name="parameters"></a>パラメーター

- **parent** 検索を開始する親ウィジェットへのポインター
- **widget_id** 検索するウィジェット ID
- **search_depth** 関数が子ウィジェットを検索する再帰的な入れ子レベルを定義します。 この値が 0 以下の場合は、親ウィジェットのすぐ下の子だけが検索されます。 この値が GX_SEARCH_DEPTH_INFINITE 場合は、すべての子ウィジェットのすべての子が徹底的に検索されます。 0 を超えるその他の値の場合には、この値によって、この関数が要求されたウィジェット ID を探し、入れ子になった子ウィジェットを検索するレベルが制限されます。
- **return_widget** 見つかったウィジェットの宛先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの検索に成功しました
- **GX_NOT_FOUND** (0x09) ウィジェットが見つかりませんでした
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_WIDGET *widget_found;

/* Find widget “my_widget”. */
status = gx_widget_find(&my_widget, GX_SEARCH_DEPTH_INFINITE
                        MY_WIDGET_ID, &widget_found);

/* If status is GX_SUCCESS, the pointer “widget_found” contains the pointer to the widget found. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_first_child_get"></a>gx_widget_first_child_get
### <a name="return-pointer-to-first-child-widget"></a>最初の子ウィジェットへのポインターを返す

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_first_child_get(
    GX_WIDGET *parent,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>説明

GUIX により、親と子のウィジェットのツリー構造リストが保持されます。 このサービスにより、親の最初の子ウィジェットへのポインターが返されます。

### <a name="parameters"></a>パラメーター

- **parent** 親ウィジェットへのポインター
- **widget_return** リターン ウィジェット ポインターへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ポインターが返されました
- **GX_PTR_ERROR** (0x07) ウィジェット ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Retrieve child widget pointer. */

GX_WIDGET *get_child_widget(GX_WIDGET *parent)
{
      GX_WIDGET *child;
      UINT status;

      status = gx_widget_first_child_get(parent, &child);
      if (status == GX_SUCCESS)
      {
            return child;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>参照

- gx_widget_last_child_get
- gx_widget_next_sibling_get
- gx_widget_parent_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_focus_next"></a>gx_widget_focus_next
### <a name="move-focus-to-next-widget-in-navigation-order"></a>ナビゲーション順で次のウィジェットにフォーカスを移動する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_focus_next(GX_WIDGET *widget);
```

### <a name="description"></a>説明

このサービスにより、フォーカスを受け入れるウィジェットのリンク リスト内の次の兄弟ウィジェットにフォーカスが移動されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェット コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) フォーカスが移動されました
- **GX_FAILURE** (0x00) フォーカスが移動されませんでした
- **GX_PTR_ERROR** (0x07) ウィジェット ポインターが無効です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Move focus to next widget in navigation order. */ status =
gx_widget_focus_next(&my_widget);

/* If status is GX_SUCCESS the focus has been moved to the next
widget in the navigation order */
```
### <a name="see-also"></a>参照

- gx_widget_focus_previous

## <a name="gx_widget_focus_previous"></a>gx_widget_focus_previous
### <a name="move-focus-to-previous-widget-in-navigation-order"></a>ナビゲーション順で前のウィジェットにフォーカスを移動する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_focus_previous(GX_WIDGET *widget);
```

### <a name="description"></a>説明

このサービスにより、ナビゲーション順で前のウィジェットにフォーカスが移動されます。

### <a name="parameters"></a>パラメーター

- **widget** 現在の入力フォーカスがあるウィジェットへのポインター。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) フォーカスが移動されました
- **GX_FAILURE** (0x00) フォーカスが移動されませんでした

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Move focus to previuos widget in navigation order. */ status =
gx_widget_focus_previous(&my_widget);

/* If status is GX_SUCCESS the input focus has been moved to the
previous widget. */
```
### <a name="see-also"></a>参照

- gx_widget_focus_next

## <a name="gx_widget_font_get"></a>gx_widget_font_get
### <a name="get-font-for-specified-resource-id"></a>指定されたリソース ID のフォントを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_font_get(
    GX_WIDGETG *widget,
    GX_RESOURCE_ID resource_id,
    GX_FONT **return_font);
```
### <a name="description"></a>説明

このサービスにより、このウィジェットが表示されている表示のフォント テーブルから、指定されたリソース ID に関連付けられているフォントが取得されます。 この関数は、表示可能なウィジェットによってのみ呼び出してください。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェット コントロール ブロックへのポインター
- **resource_id** フォントのリソース ID
- **return_font** フォント ポインターの宛先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) フォントの取得に成功しました
- **GX_INVALID_RESOURCE_ID** (0x33) リソース ID が無効です
- **GX_INVALID_CANVAS** (0x20) ウィジェット キャンバスが無効であるか、ウィジェットが非表示です
- **GX_PTR_ERROR** (0x07) ウィジェット ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_FONT *my_font;
/* Get font for MY_FONT_ID. */
status = gx_widget_font_get(widget, MY_FONT_RESOURCE_ID, &my_font);
/* If status is GX_SUCCESS the font pointer has been retrieved in “my_font”. */
```
### <a name="see-also"></a>参照

- gx_widget_color_get
- gx_widget_pixelmap_get

## <a name="gx_widget_free"></a>gx_widget_free
### <a name="release-memory-associated-with-a-widget"></a>ウィジェットに関連付けられているメモリを解放する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_free(GX_WIDGETG *widget);
```

### <a name="description"></a>説明

このサービスによって、ウィジェット コントロール ブロックに関連付けられているメモリが解放されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェット コントロール ブロックへのポインター
- **resource_id** フォントのリソース ID
- **return_font** フォント ポインターの宛先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの解放に成功しました
- **GX_SYSTEM_MEMPRY_ERROR** (0x30) メモリ解放関数が定義されていません
- **GX_PTR_ERROR** (0x07) ウィジェット ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_WIDGET widget;
UINT status;

status = gx_widget_allocate(&widget, sizeof(GX_WIDGET))

/* Free a runtime allocated widget. */
if (status == GX_SUCCESS)
{
      status = gx_widget_free(widget);
}

/* If status is GX_SUCCESS the memory that allocated to the widget has been released. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_front_move"></a>gx_widget_front_move
### <a name="move-widget-to-front"></a>ウィジェットを前面へ移動する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_front_move(
    GX_WIDGET *widget, 
    GX_BOOL *return_moved);
```

### <a name="description"></a>説明

このサービスにより、ウィジェットが、子ウィジェットの親 Z 順序リストの先頭に移動されます。

### <a name="parameters"></a>パラメーター

- **widget** 移動するウィジェットへのポインター
- **return_moved** 指示ウィジェットの移動先へのポインターが移動されました

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの前面への移動に成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_NO_CHANGE** (0x08) ウィジェットが既に前面にあります
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_BOOL widget_moved;

/* Move widget “my_widget” to the front. */
status = gx_widget_front_move(&my_widget, &widget_moved);

/* If status is GX_SUCCESS and “widget_moved” is GX_TRUE, the
widget “my_widget” was moved to the front . */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_height_get"></a>gx_widget_height_get
### <a name="get-widget-height"></a>ウィジェットの高さを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_height_get(
    GX_WIDGET *widget,
    UINT *return_height);
```

### <a name="description"></a>説明

このサービスにより、ウィジェットの高さが取得されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **return_height** ウィジェットの高さの描画先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの高さの取得に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_VALUE widget_height;

/* Get height for widget “my_widget”. */
status = gx_widget_height_get(&my_widget, &widget_height);

/* If status is GX_SUCCESS the height of the widget is contained in
“widget_height” . */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_hide"></a>gx_widget_hide
### <a name="hide-widget"></a>ウィジェットを非表示にする

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_hide(GX_WIDGET *widget);
```

### <a name="description"></a>説明

このサービスにより、ウィジェットが非表示になります。 このウィジェットは親にアタッチされたままですが、キャンバス上に描画することはできません。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの非表示に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```c
/* Hide widget “my_widget”. */
status = gx_widget_hide(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” is hidden. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_style_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_last_child_get"></a>gx_widget_last_child_get
### <a name="return-pointer-to-last-child-widget"></a>最後の子ウィジェットへのポインターを返す

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_last_child_get(
    GX_WIDGET *parent,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>説明

GUIX は、親と子のウィジェットのツリー構造のリストを保持します。 このサービスにより、親の最後の子ウィジェットへのポインターが返されます。

### <a name="parameters"></a>パラメーター

- **parent** 親ウィジェットへのポインター
- **widget_return** リターン ウィジェット ポインターへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ポインターが返されました
- **GX_PTR_ERROR** (0x07) ウィジェット ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Retrieve child widget pointer. */

GX_WIDGET *get_last_child_widget(GX_WIDGET *parent)
{

      GX_WIDGET *child;
      UINT status;

      status = gx_widget_last_child_get(parent, &child);
      if (status == GX_SUCCESS)
      {
              return child;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>参照

- gx_widget_first_child_get
- gx_widget_next_sibling_get
- gx_widget_parent_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_next_sibling_get"></a>gx_widget_next_sibling_get
### <a name="return-pointer-to-next-sibling-of-current-widget"></a>現在のウィジェットの次の兄弟へのポインターを返す

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_next_sibling_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>説明

GUIX により、親と子のウィジェットのツリー構造リストが保持されます。 このサービスにより、現在のウィジェットの次の兄弟へのポインターが返されます。

### <a name="parameters"></a>パラメーター

- **current** 現在のウィジェットへのポインター
- **widget_return** リターン ウィジェット ポインターへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ポインターが返されました
- **GX_PTR_ERROR** (0x07) ウィジェット ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Retrieve next sibling widget pointer. */

GX_WIDGET *get_next(GX_WIDGET *current)
{
      GX_WIDGET *sibling;
      UINT status;

      status = gx_widget_next_sibling_get(current, &sibling);
      if (status == GX_SUCCESS)
      {
            return sibling;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>参照

- gx_widget_first_child_get
- gx_widget_last_child_get
- gx_widget_parent_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_parent_get"></a>gx_widget_parent_get
### <a name="return-pointer-to-parent-of-current-widget"></a>現在のウィジェットの親へのポインターを返す

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_parent_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>説明

GUIX により、親と子のウィジェットのツリー構造リストが保持されます。 このサービスにより、現在のウィジェットの親へのポインターが返されます。

### <a name="parameters"></a>パラメーター

- **current** 現在のウィジェットへのポインター
- **widget_return** リターン ウィジェット ポインターへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ポインターが返されました
- **GX_PTR_ERROR** (0x07) ウィジェット ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Retrieve parent widget */

GX_WIDGET *get_parent(GX_WIDGET *current)
{
      GX_WIDGET *parent;
      UINT status;

      status = gx_widget_parent_get(current, &parent);
      if (status == GX_SUCCESS)
      {
            return parent;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>参照

- gx_widget_first_child_get
- gx_widget_last_child_get
- gx_widget_next_sibling_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_pixelmap_get"></a>gx_widget_pixelmap_get
### <a name="get-pixelmap"></a>ピクセルマップを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_pixelmap_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID resource_id,
    GX_PIXELMAP **return_pixelmap);
```

### <a name="description"></a>説明

このサービスにより、指定されたリソース ID に関連付けられているピクセルマップが取得されます。 このサービスは、表示可能なウィジェットでのみ呼び出します。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェット コントロール ブロックへのポインター
- **pixelmap_id** ピクセルマップのリソース ID
- **return_pixelmap** ピクセルマップの宛先ポインターへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ピクセルマップの取得に成功しました
- **GX_INVALID_RESOURCE_ID** (0x33) リソース ID が無効です
- **GX_INVALID_CANVAS** (0x20) ウィジェット キャンバスが無効であるか、ウィジェットが非表示です
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```c
GX_PIXELMAP *my_pixelmap;

/* Get the pixelmap associated with MY_PIXELMAP_ID. */
status = gx_widget_pixelmap_get(widget, MY_PIXELMAP_RESOURCE_ID,
                                &my_pixelmap);

/* If status is GX_SUCCESS, “my_pixelmap” contains the pixemap pointer. */
```
### <a name="see-also"></a>参照

- gx_widget_color_get
- gx_widget_font_get

## <a name="gx_widget_previous_sibling_get"></a>gx_widget_previous_sibling_get
### <a name="return-pointer-to-previous-sibling-of-the-current-widget"></a>現在のウィジェットの前の兄弟へのポインターを返す

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_previous_sibling_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```

### <a name="description"></a>説明

GUIX により、親と子のウィジェットのツリー構造リストが保持されます。 このサービスにより、現在のウィジェットの前の兄弟へのポインターが返されます。

### <a name="parameters"></a>パラメーター

- **current** 現在のウィジェットへのポインター
- **widget_return** リターン ウィジェット ポインターへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ポインターが返されました
- **GX_PTR_ERROR** (0x07) ウィジェット ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Retrieve previous sibling widget */

GX_WIDGET *get_previous(GX_WIDGET *current)
{
      GX_WIDGET *sibling;
      UINT status;

      status = gx_widget_previous_sibling_get(current, &sibling);
      if (status == GX_SUCCESS)
      {
          return sibling;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>参照

- gx_widget_first_child_get
- gx_widget_last_child_get
- gx_widget_next_sibling_get
- gx_widget_parent_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_resize"></a>gx_widget_resize
### <a name="resize-widget"></a>ウィジェットのサイズを変更する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_resize(
    GX_WIDGET *widget, 
    GX_RECTANGLE *new_size);
```
### <a name="description"></a>説明

このサービスにより、ウィジェットのサイズが変更されます。 ウィジェットが表示されている場合は、自動的に無効になり、再描画のためにキューに入れられます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **new_size** 新しいウィジェットのサイズ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットのサイズ変更に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_RECTANGLE new_size;

gx_utility_rectangle_define(&new_size, 0, 0, 100, 100);

/* Resize widget “my_widget”. */
status = gx_widget_resize(&my_widget, &new_size);

/* If status is GX_SUCCESS the widget “my_widget” has been resized. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_shift"></a>gx_widget_shift
### <a name="shift-widget"></a>ウィジェットをシフトする

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_shift(
    GX_WIDGET *widget, 
    GX_VALUE x_shift,
    GX_VALUE y_shift, 
    GX_BOOL mark_dirty);
```

### <a name="description"></a>説明

このサービスによりウィジェットがシフトされ、必要に応じてダーティとしてマークされます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **x_shift** X 軸でシフトするピクセル数
- **y_shift** Y 軸でシフトするピクセル数
- **mark_dirty** ダーティとして示す場合には GX_TRUE、それ以外の場合は GX_FALSE

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットのシフトに成功しました GX_CALLER_ERROR (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Shift widget “my_widget”. */
status = gx_widget_shift(&my_widget, 10, 20, GX_FALSE);

/* If status is GX_SUCCESS the widget “my_widget” has been shifted. */
```

### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_show"></a>gx_widget_show
### <a name="show-widget"></a>ウィジェットを表示する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_show(GX_WIDGET *widget);
```

### <a name="description"></a>説明

このサービスによりウィジェットが表示されます。 ウィジェットは親にアタッチされていて、親ウィジェットも表示される場合にのみ表示されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの表示に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Show widget “my_widget”. */
status = gx_widget_show(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” has been shown. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_add"></a>gx_widget_status_add
### <a name="add-widget-status"></a>ウィジェットの状態を追加する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_status_add(
    GX_WIDGET *widget, 
    ULONG status)
```

### <a name="description"></a>説明

このサービスにより、指定されたウィジェットに状態フラグの任意の組み合わせが追加されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **status** 追加する状態

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの状態の追加に成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Add status to widget “my_widget”. */
status = gx_widget_status_add(&my_widget, status_to_add);

/* If status is GX_SUCCESS the widget “my_widget” status was. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_get"></a>gx_widget_status_get
### <a name="get-widget-status"></a>ウィジェットの状態を取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_status_get(
    GX_WIDGET *widget,
    ULONG *return_status)
```

### <a name="description"></a>説明

このサービスにより、ウィジェットから状態フラグが取得されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **return_status** 返される状態へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの状態の取得に成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
ULONT get_status;

/* Retrieve status flag from widget “my_widget”. */ status =
gx_widget_status_get(&my_widget, &get_status);

/* If status is GX_SUCCESS the status from widget “my_widget” is
saved to “get_status”. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_remove"></a>gx_widget_status_remove
### <a name="remove-widget-status"></a>ウィジェットの状態を削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_status_remove(
    GX_WIDGET *widget, 
    ULONG status)
```

### <a name="description"></a>説明

このサービスにより、ウィジェットの内部状態変数から、指定された状態フラグが削除されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **status** 削除する状態

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの状態の削除に成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Remove status of widget “my_widget”. */
status = gx_widget_status_remove(&my_widget, status_to_remove);

/* If status is GX_SUCCESS, the status flags are removed from the
widget “my_widget”. */
```
### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_test"></a>gx_widget_status_test
### <a name="test-widget-status"></a>ウィジェットの状態をテストする

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_status_test(
    GX_WIDGET *widget, 
    ULONG status,
    GX_BOOL *return_test);
```
### <a name="description"></a>説明

このサービスにより、指定されたウィジェットの状態フラグがテストされ、結果が「return_test」で示されるメモリに格納されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **status** テストする状態
- **return_status** テスト結果の格納先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの状態テストに成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_BOOL test_result;

/* Test status of widget “my_widget”. */
status = gx_widget_status_test(&my_widget, status_to_test,
                              &test_result);

/* If status is GX_SUCCESS the widget “my_widget” status was tested
and the result in “test_result”. */
```
### <a name="see-also"></a>参照

- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set

## <a name="gx_widget_string_get"></a>gx_widget_string_get
### <a name="retrieve-string-associated-with-a-visible-widget-and-string-id-deprecated"></a>表示されているウィジェットと文字列 ID に関連付けられた文字列を取得する (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_string_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID string_id,
    GX_CONST GX_CHAR **string);
```

### <a name="description"></a>説明

このサービスは非推奨です。gx_widget_string_get_ext() を使用してください。

このサービスにより、指定された文字列 ID 値に対応する文字列テーブルのエントリが返されます。 このサービスは gx_display_string_get に似ていますが、アクティブな表示が呼び出し元によって渡されるのではなく、自動的に決定される点が異なります。 このサービスは、表示されているウィジェットに対してのみ使用できます (このウィジェットに関連付けられている表示がわかっている)。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **string_id** リソース ヘッダーからの文字列 ID 値
- **string** 文字列を返す変数のアドレス

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの状態テストに成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_CONST GX_CHAR *string;

/* Test status of widget “my_widget”. */
status = gx_widget_string_get(&my_widget, GX_STRING_ID_SHUTDOWN,
      &string);

/* If status is GX_SUCCESS the string has been retrieved */
```
### <a name="see-also"></a>参照

- gx_display_string_get
- gx_display_active_langauge_set

## <a name="gx_widget_string_get_ext"></a>gx_widget_string_get_ext
### <a name="retrieve-string-associated-with-a-visible-widget-and-string-id"></a>表示されているウィジェットと文字列 ID に関連付けられた文字列を取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_string_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID string_id,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>説明

このサービスにより、指定された文字列 ID 値に対応する文字列テーブルのエントリが返されます。 このサービスは gx_display_string_get に似ていますが、アクティブな表示が呼び出し元によって渡されるのではなく、自動的に決定される点が異なります。 このサービスは、表示されているウィジェットに対してのみ使用できます (このウィジェットに関連付けられている表示がわかっている)。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **string_id** リソース ヘッダーからの文字列 ID 値
- **string** 文字列を返す変数のアドレス

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェットの状態テストに成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_STRING string;

/* Test status of widget “my_widget”. */

status = gx_widget_string_get_ext(&my_widget,
                          GX_STRING_ID_SHUTDOWN, &string);

/* If status is GX_SUCCESS the string has been retrieved */
```

### <a name="see-also"></a>参照

- gx_display_string_get
- gx_display_active_langauge_set

## <a name="gx_widget_style_add"></a>gx_widget_style_add
### <a name="add-widget-style"></a>ウィジェットのスタイルを追加する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_style_add(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>説明

このサービスにより、ウィジェットにスタイルが追加されます。 さらに、次のアクションが実行されます。

追加されたスタイルが GX_STYLE_TRANSPARENT の場合は、状態 GX_STATUS_TRANSPARENT が追加されます。

追加されたスタイルが GX_STYLE_ENABLED の場合は、状態 GX_STATUS_SELECTABLE が追加されます。

ウィジェットが表示されている場合は、自動的に無効になり、再描画のためにキューに入れられます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **style** 追加する新しいスタイル。 **付録 D** には、ウィジェット固有のスタイルだけでなく、すべてのウィジェット用に事前に定義された一般的なスタイルが含まれています。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェット スタイルの追加に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Add style to widget “my_widget”. */
status = gx_widget_style_add(&my_widget, GX_STYLE_BORDER_RAISED);

/* If status is GX_SUCCESS, the style was successfully applied to the widget “my_widget”. */
```

### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_style_get"></a>gx_widget_style_get
### <a name="get-widget-style"></a>ウイジェットのスタイルを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_style_get(
    GX_WIDGET *widget, 
    ULONG *return_style)
```

### <a name="description"></a>説明

このサービスにより、ウィジェットからスタイル フラグが取得されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **return_style** 返されるスタイルへのポインター。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェット スタイルの取得に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド


### <a name="example"></a>例

```C
/* Retrieve style from widget into “style”. */
status = gx_widget_style_get(&my_widget, &style);

/* If status is GX_SUCCESS the style flag from widget is saved in “style”. */
```

### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_remove
- gx_widget_style_add
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_style_remove"></a>gx_widget_style_remove
### <a name="remove-widget-style"></a>ウィジェットのスタイルを削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_style_remove(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>説明

このサービスにより、ウィジェットからスタイルが削除されます。 さらに、次のアクションが実行されます。

削除されたスタイルが GX_STYLE_TRANSPARENT の場合は、状態 GX_STATUS_TRANSPARENT が削除されます。

削除されたスタイルが GX_STYLE_ENABLED の場合は、状態 GX_STATUS_SELECTABLE が削除されます。

ウィジェットが表示されている場合は、自動的に無効になり、再描画のためにキューに入れられます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **style** 削除するスタイル。 **付録 D** には、ウィジェット固有のスタイルだけでなく、すべてのウィジェット用に事前に定義された一般的なスタイルが含まれています。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェット スタイルの削除に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Remove style from widget “my_widget”. */
status = gx_widget_style_remove(&my_widget,
                                GX_STYLE_BORDER_RAISED);

/* If status is GX_SUCCESS the GX_STYLE_BORDER_RAISED style was removed from the widget “my_widget”.*/
```

### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_style_set"></a>gx_widget_style_set
### <a name="set-widget-style"></a>ウイジェットのスタイルを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_style_set(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>説明

このサービスにより、ウィジェットにスタイルが設定されます。

設定されたスタイルに GX_STYLE_TRANSPARENT が含まれている場合は、状態 GX_STATUS_TRANSPARENT が追加されます。それ以外の場合は、状態が削除されます。

設定されたスタイルに GX_STYLE_ENABLED が含まれている場合は、状態 GX_STATUS_SELECTABLE が追加されます。それ以外の場合は、状態が削除されます。

ウィジェットが表示されている場合は、自動的に無効になり、再描画のためにキューに入れられます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **style** 設定するスタイル。 **付録 D** には、ウィジェット固有のスタイルだけでなく、すべてのウィジェット用に事前に定義された一般的なスタイルが含まれています。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェット スタイルの設定に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set style GX_STYLE_TRANSPARENT to the widget “my_widget”. */
status = gx_widget_style_set(&my_widget, GX_STYLE_TRANSPARENT);

/* If status is GX_SUCCESS the widget “my_widget” style is set to GX_STYLE_TRANSPARENT. */
```

### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_text_blend"></a>gx_widget_text_blend
### <a name="blend-text-assigned-to-widget-deprecated"></a>割り当てられたテキストをウィジェットに合成する (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_text_blend(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    GX_CHAR *string,
    INT x_offset, 
    INT y_offset, 
    UCHAR alpha)
```

### <a name="description"></a>説明

このサービスは非推奨です。gx_widget_text_blend_ext() を使用してください。

このサービスにより、現在のブラシとテキストの配置が使用され、ウィジェット上に指定されたテキストが合成されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **tColor** テキストの色
- **font_id** フォント ID
- **string** 描画文字列
- **x_offset** 描画位置の調整
- **x_offset** 描画位置の調整
- **alpha** 0 から 255 のブレンド値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェット幅の取得に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_STRING_LENGTH**: (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Blend “my_string” over “my_widget” given alpha value 120. */
status = gx_widget_text_blend(&my_widget, my_text_color, my_font_id,
                              &my_string, xoffset, yoffset, 120);

/* If status is GX_SUCCESS “my_string” has been blend to “my_widget”. */
```

### <a name="see-also"></a>参照

- gx_widget_text_blend_ext

## <a name="gx_widget_text_blend_ext"></a>gx_widget_text_blend_ext
### <a name="blend-text-assigned-to-widget"></a>割り当てられたテキストをウィジェットに合成する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_text_blend(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    GX_CONST GX_STRING *string,
    INT x_offset, 
    INT y_offset, 
    UCHAR alpha)
```

### <a name="description"></a>説明

このサービスは非推奨です。gx_widget_text_blend_ext() を使用してください。

このサービスにより、現在のブラシとテキストの配置、指定された色、フォント、および x、y オフセットを使用して、指定されたウィジェット上に文字列が表示されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **tColor** テキストの色
- **font_id** フォント ID
- **string** 描画文字列
- **x_offset** 描画位置の調整
- **x_offset** 描画位置の調整
- **alpha** 0 から 255 のブレンド値

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェット幅の取得に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_STRING_LENGTH**: (0x34) 文字列の長さが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
gx_string render_string;
render_string.gx_string_ptr = “Hello”;
render_string.gx_string_length =
    strlen(render_string.gx_string_ptr);

/* Blend “my_string” over “my_widget” given alpha value 120. */
status = gx_widget_text_blend_ext(&my_widget,
        my_text_color,
        my_font_id,
        &render_string, xoffset, yoffset, 120);

/* If status is GX_SUCCESS “my_string” has been blend to “my_widget”. */
```

### <a name="see-also"></a>参照

- gx_widget_text_draw_ext

## <a name="gx_widget_text_draw"></a>gx_widget_text_draw
### <a name="draw-text-assigned-to-widget-deprecated"></a>割り当てられたテキストをウィジェットに描画する (非推奨)

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_widget_text_draw(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    GX_CHAR *string,
    INT x_offset, 
    INT y_offset)
```

### <a name="description"></a>説明

このサービスは非推奨です。gx_widget_text_draw_ext() を使用してください。

このサービスにより、現在のブラシとテキストの配置が使用され、ウィジェット上に指定されたテキストが描画されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **tColor** テキストの色
- **font_id** フォント ID
- **string** 描画文字列
- **x_offset** 描画位置の調整
- **x_offset** 描画位置の調整

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom widget draw function. */

VOID my_custom_widget_draw(GX_WIDGET *widget)
{
    /* Add your own background raw here. */

    /* Call widget text draw. */
    gx_widget_text_draw(widget, my_text_color, my_font_id
                        &my_string, xoffset, yoffset);
}
```

### <a name="see-also"></a>参照

- gx_widget_text_blend
- gx_widget_text_id_draw

## <a name="gx_widget_text_draw_ext"></a>gx_widget_text_draw_ext
### <a name="draw-text-assigned-to-widget"></a>割り当てられたテキストをウィジェットに描画する

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_widget_text_draw(
    GX_WIDGET *widget,
    UINT *tColor,
    UINT font_id, 
    GX_CONST GX_STRING *string,
    INT x_offset,
    INT y_offset)
```

### <a name="description"></a>説明

このサービスにより、現在のブラシとテキストの配置が使用され、ウィジェット上に指定されたテキストが描画されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **tColor** テキストの色
- **font_id** フォント ID
- **text_id** テキスト ID
- **x_offset** 描画位置の調整
- **x_offset** 描画位置の調整

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
gx_string render_string;
render_string.gx_string_ptr = “Hello”;
render_string.gx_string_length =
    strlen(render_string.gx_string_ptr);

/* Write a custom widget draw function. */
VOID my_custom_widget_draw(GX_WIDGET *widget)
{
    /* Add your own background draw here. */

    /* Call widget text draw. */
    gx_widget_text_draw_ext(widget, my_text_color, my_font_id
                        &render_string, xoffset, yoffset);
}
```

### <a name="see-also"></a>参照

- gx_widget_text_blend
- gx_widget_text_id_draw

## <a name="gx_widget_text_id_draw"></a>gx_widget_text_id_draw
### <a name="draw-text-assigned-to-widget"></a>割り当てられたテキストをウィジェットに描画する

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_widget_text_id_draw(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    UINT text_id,
    INT x_offset, 
    INT y_offse)
```

### <a name="description"></a>説明

このサービスにより、ウィジェットの上に指定されたテキスト ID のテキストが描画されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **tColor** テキストの色
- **font_id** フォント ID
- **text_id** テキスト ID
- **x_offset** 描画位置の調整
- **x_offset** 描画位置の調整

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Write a custom widget draw function. */

VOID my_custom_widget_draw(GX_WIDGET *widget)
{
    /* Add your own background raw here. */

    /* Call widget text id draw. */
    gx_widget_text_id_draw(widget, my_text_color, my_font_id
                            &my_string_id, xoffset, yoffset);
}
```

### <a name="see-also"></a>参照

- gx_widget_text_blend
- gx_widget_text_draw

## <a name="gx_widget_top_visible_child_find"></a>gx_widget_top_visible_child_find
### <a name="return-pointer-to-visible-child-that-is-top-of-z-order"></a>Z 順序の最上位にある表示された子へのポインターを返す

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_top_visible_child_find(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```

### <a name="description"></a>説明

GUIX は、親と子のウィジェットのツリー構造のリストを保持します。
このサービスにより、現在のウィジェットの最上位の表示された子へのポインターが返されます。

### <a name="parameters"></a>パラメーター

- **current** 現在のウィジェットへのポインター
- **widget_return** リターン ウィジェット ポインターへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ポインターが返されました
- **GX_PTR_ERROR** (0x07) ウィジェット ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Retrieve topmost visible widget on the display */

GX_WIDGET *get_top_window(GX_WINDOW_ROOT *root)
{
    GX_WIDGET *top_window;
    UINT status;

    status = gx_widget_top_visible_child_find(root, &top_window);
    if (status == GX_SUCCESS)
    {
        return top_window;
    }
    return GX_NULL;
}
```

### <a name="see-also"></a>参照

- gx_widget_first_child_get、
- gx_widget_last_child_get、
- gx_widget_next_sibling_get、
- gx_widget_parent_get、
- gx_widget_previous_sibling_get

## <a name="gx_widget_type_find"></a>gx_widget_type_find
### <a name="search-for-a-widget-of-the-requested-type"></a>要求された種類のウィジェットを検索する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_type_find(
    GX_WIDGET *parent, 
    USHORT widget_id,
    GX_WIDGET **return_widget)
```

### <a name="description"></a>説明

このサービスにより、要求された種類のウィジェットが検索されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **return_width** ウィジェット幅の描画先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェット幅の取得に成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_WIDGET *retrieved_widget;

/* Find horizontal scrollbar under “parent_widget”. */
status = gx_widget_type_find(&parent_widget,
                GX_TYPE_HORIZONTAL_SCROLL_BAR, &retrieved_widget);

/* If status is GX_SUCCESS, the horizontal scrollbar widget is retrieved. */
```

### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set

## <a name="gx_widget_width_get"></a>gx_widget_width_get
### <a name="get-widget-width"></a>ウィジェットの幅を取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_widget_width_get(
    GX_WIDGET *widget,
    GX_VALUE *return_width)
```

### <a name="description"></a>説明

このサービスにより、ウィジェットの幅が取得されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェットへのポインター
- **return_width** ウィジェット幅の描画先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィジェット幅の取得に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_VALUE my_widget_width;

/* Get width of widget “my_widget”. */
status = gx_widget_width_get(&my_widget, &my_widget_width);

/* If status is GX_SUCCESS the width of widget “my_widget” is in “my_widget_width”. */
```

### <a name="see-also"></a>参照

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set

## <a name="gx_window_client_height_get"></a>gx_window_client_height_get
### <a name="get-window-client-height"></a>ウィンドウ クライアントの高さを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_window_client_height_get(
    GX_WINDOW *window,
    GX_VALUE *return_height);
```

### <a name="description"></a>説明

このサービスにより、ウィンドウのクライアントの高さが取得されます。

### <a name="parameters"></a>パラメーター

- **window** ウィンドウへのポインター
- **return_height** クライアントの高さの宛先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィンドウ クライアントの高さ取得に成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_RECTANGLE my_client_height;

/* Get client height of “my_window”. */
status = gx_window_client_height_get(&my_window,
                                     &my_client_height);

/* If status is GX_SUCCESS the window “my_window” client height is contained in “my_client_height”. */
```

### <a name="see-also"></a>参照

- gx_window_canvas_set
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- x_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_client_scroll"></a>gx_window_client_scroll
### <a name="scroll-window-clients"></a>ウィンドウ クライアントをスクロールする

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_window_client_scroll(
    GX_WINDOW *window, 
    GX_VALUE x_scroll,
    GX_VALUE y_scroll);
```

### <a name="description"></a>説明

このサービスにより、指定された量だけウィンドウ クライアントをスクロールします。

### <a name="parameters"></a>パラメーター

- **window** ウィンドウへのポインター
- **x_scroll** X 軸でスクロールする量
- **x_scroll** X 軸でスクロールする量

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィンドウ クライアントのスクロールに成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_VALUE** (0x22) スクロール値が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Scroll clients of “my_window”. */
status = gx_window_client_scroll(&my_window, 10, 0);

/* If status is GX_SUCCESS the clients of window “my_window” have been scrolled. */
```

### <a name="see-also"></a>参照

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_client_width_get"></a>gx_window_client_width_get
### <a name="get-window-client-width"></a>ウィンドウ クライアントの幅を取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_window_client_width_get(
    GX_WINDOW *window,
    GX_VALUE *return_width);
```

### <a name="description"></a>説明

このサービスでは、指定されたウィンドウ クライアントの幅が取得されます。

### <a name="parameters"></a>パラメーター

- **window** ウィンドウへのポインター
- **return_height** クライアントの幅の宛先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィンドウ クライアントの幅の取得に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_VALUE my_client_widthl

/* Get client width of “my_window”. */
status = gx_window_client_width_get(&my_window, &my_client_width);

/* If status is GX_SUCCESS “my_client_width” contains the client width of window “my_window”. */
```

### <a name="see-also"></a>参照

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_close"></a>gx_window_close
### <a name="close-modal-window"></a>モーダル ウィンドウを閉じる

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_window_close(GX_WINDOW *window);
```

### <a name="description"></a>説明

このサービスにより、モーダル ウィンドウが強制的に親からデタッチされ、モーダル実行ループから戻されます。

### <a name="parameters"></a>パラメーター

- **window** ウィンドウ コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィンドウが閉じられました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Close window “my_window”. */
status = gx_window_close(&my_window);

/* If status is GX_SUCCESS window “my_window” has been closed. */
```

### <a name="see-also"></a>参照

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_create"></a>gx_window_create
### <a name="create-window"></a>ウィンドウを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_window_create(
    GX_WINDOW *window, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    ULONG style,
    USHORT window_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>説明

このサービスによりウィンドウが作成されます。

GX_WINDOW は GX_WIDGET から派生し、すべての gx_widget API サービスをサポートします。

### <a name="parameters"></a>パラメーター

- **window** ウィンドウ コントロール ブロックへのポインター
- **name** ウィンドウの論理名
- **parent** 親ウィジェットへのポインター
- **style** ウィンドウのスタイル。 **付録 D** には、ウィジェット固有のスタイルだけでなく、すべてのウィジェット用に事前に定義された一般的なスタイルが含まれています。
- **widget_id** アプリケーションで定義された、ウィンドウの ID
- **size** ウィンドウのサイズ

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィンドウの作成に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットが既に作成されています
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_WINDOW my_window;

/* Create window “my_window”. */
status = gx_window_create(&my_window, "my window",
                          &my_parent_window, GX_STYLE_BORDER_RAISED,
                          MY_WINDOW_ID, &size);

/* If status is GX_SUCCESS window “my_window” has been created. */
```

### <a name="see-also"></a>参照

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_draw"></a>gx_window_draw
### <a name="draw-window"></a>ウィンドウを描画する

### <a name="prototype"></a>プロトタイプ

```C
VOID gx_window_draw(GX_WINDOW *window);
```

### <a name="description"></a>説明

このサービスにより、ウィンドウが描画されます。 このサービスは、通常、キャンバスの更新中に内部的に呼び出されますが、カスタムのウィンドウ描画関数から呼び出すこともできます。

### <a name="parameters"></a>パラメーター

- **window** ウィンドウ コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **なし**

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a custom window draw function. */

VOID my_custom_window_draw(GX_WINDOW *window)
{
    /* Call default window draw. */
    gx_window_draw(window);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>参照

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_event_process"></a>gx_window_event_process
### <a name="process-window-event"></a>ウィンドウ イベントを処理する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_window_event_process(
    GX_WINDOW *window, 
    GX_EVENT *event);
```

### <a name="description"></a>説明

このサービスにより、このウィンドウのイベントが処理されます。

### <a name="parameters"></a>パラメーター

- **window** ウィンドウ コントロール ブロックへのポインター
- **event** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィンドウ イベントの処理に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Call generic window event processing as part of custom event processing function. */

UINT custom_window_event_process(GX_WINDOW *window,
                                 GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
        case xyz:
            /* Insert custom event handling here */
            break;
        default:
            /* Pass all other events to the default window
            event processing */
            status = gx_window_event_process(window, event);
            break;
        }
        return status;
}
```

### <a name="see-also"></a>参照

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_execute"></a>gx_window_execute
### <a name="modally-execute-a-window"></a>ウィンドウをモーダルで実行する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_window_execute(
    GX_WINDOW *window,
    ULONG *return_ptr)
```

### <a name="description"></a>説明

このサービスにより、モーダルでウィンドウが実行されます。 ウィンドウ クライアント領域外のユーザー入力 (ペン イベントなど) は無視されます。 この関数は、連続的なブロッキング実行ループに入り、モデルの実行が終了するまで呼び出し元に戻らないことに注意してください。

モーダル実行は、受信したイベントのイベント処理によって 0 以外の状態値が返された場合、または gx_window_close API 関数が呼び出された場合に終了します。 0 以外のイベント処理リターンコードは、この API に渡された return_ptr を通じて呼び出し元に返されます

### <a name="parameters"></a>パラメーター

- **window** ウィンドウ コントロール ブロックへのポインター
- **return_ptr** モーダル実行の終了状態を保存する場所。 GX_NULL の可能性があります。

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) 実行が成功しました
- **GX_SYSTEM_EVENT_RECEIVE_ERROR** (0x05) イベント キューからのピックアップ イベントに失敗しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Execute a modal window. */
status = gx_window_execute(&my_window, &return_code);

/* If status is GX_SUCCESS the window was executed, and return_code holds the execution return code. */
```

### <a name="see-also"></a>参照

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_root_create"></a>gx_window_root_create
### <a name="create-a-root-window"></a>ルート ウィンドウを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_window_root_create(
    GX_WINDOW_ROOT *root_window,
    GX_CONST GX_CHAR *name,
    GX_CANVAS *canvas, 
    ULONG style,
    USHORT id,
    GX_CONST GX_RECTANGLE *size)
```

### <a name="description"></a>説明

このサービスは、ルート ウィンドウを作成します。

### <a name="parameters"></a>パラメーター

- **root_window** ルート ウィンドウ コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ルート ウィンドウの作成に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_SIZE** (0x19) ウィジェット コントロール ブロック サイズが無効です
- **GX_ALREADY_CREATED** (0x13) ウィジェットは既に作成されています

### <a name="allowed-from"></a>使用可能な場所

初期化とスレッド

### <a name="example"></a>例

```C
GX_ROOT_WINDOW root_window;
GX_CANVAS canvas;

/* Create canvas here. */

/* Create a root window */
status = gx_window_root_create(&root_window, “root”, &canvas,
GX_STYLE_BORDER_NONE, GX_NULL, &size);

/* If status is GX_SUCCESS, the “root_window” is successfully created. */
```

### <a name="see-also"></a>参照

- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find

## <a name="gx_window_root_delete"></a>gx_window_root_delete
### <a name="destroy-a-root-window"></a>ルート ウィンドウを破棄する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_window_root_delete(GX_WINDOW_ROOT *root_window)
```

### <a name="description"></a>説明

このサービスにより、ルート ウィンドウが削除されます。

### <a name="parameters"></a>パラメーター

- **root_window** ルート ウィンドウ コントロール ブロックへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ルート ウィンドウの削除に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_SYSTEM_MEMPRY_ERROR** (0x30) メモリ解放関数が定義されていません

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Delete a root window */
status = gx_window_root_delete(&root_window);

/* If status is GX_SUCCESS the “root_window” is destroyed. */
```

### <a name="see-also"></a>参照

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_root_event_process"></a>gx_window_root_event_process
### <a name="process-event-for-the-root-window"></a>ルート ウィンドウのイベントを処理する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_window_root_create(
    GX_WINDOW_ROOT *root_window,
    GX_EVENT *event)
```

### <a name="description"></a>説明

このサービスにより、指定されたルート ウィンドウのイベントが処理されます。

### <a name="parameters"></a>パラメーター

- **root_window** ルート ウィンドウ コントロール ブロックへのポインター
- **event** 処理するイベントへのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ルート ウィンドウ イベントの処理に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Call generic root window event processing as part of custom event processing function. */

UINT custom_root_window_event_process(GX_ROOT_WINDOW *root,
                                      GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default root window
            event processing */
        status = gx_window_root_event_process(root, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>参照

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_root_find"></a>gx_window_root_find
### <a name="find-root-window"></a>ルート ウィンドウを探す

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_window_root_find(
    GX_WIDGET *widget,
    GX_WINDOW_ROOT **return_root_window);
```

### <a name="description"></a>説明

このサービスにより、指定されたウィジェットのルート ウィンドウが探されます。

### <a name="parameters"></a>パラメーター

- **widget** ウィジェット コントロール ブロックへのポインター
- **return_root_window** 見つかったルート ウィンドウの宛先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ルート ウィンドウが見つかりました
- **GX_FAILURE** (0x00) ルート ウィンドウが存在しません
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Find root window associated with window “my_window”. */
status = gx_window_root_find(&my_window, &root_window);

/* If status is GX_SUCCESS the “root_window” contains the root window for window “my_window”. */
```

### <a name="see-also"></a>参照

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_scroll_info_get"></a>gx_window_scroll_info_get
### <a name="get-window-scroll-info"></a>ウィンドウのスクロール情報を取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_window_scroll_info_get(
    GX_WINDOW *window, 
    ULONG style,
    GX_SCROLL_INFO *return_scroll_info);
```

### <a name="description"></a>説明

このサービスにより、ウィンドウのスクロール情報が取得されます。

### <a name="parameters"></a>パラメーター

- **window** ウィンドウへのポインター
- **style** GX_SCROLLBAR_HORIZONTAL または GX_SCROLLBAR_VERTICAL
- **return_scroll_info** スクロール情報の宛先へのポインター。 親ウィンドウは、この構造体を初期化して、親ウィンドウの合計サイズ、表示可能領域、スクロールの増分と制限をスクロールバーに通知します。 デフォルトの実装では、表示可能領域として Windows クライアント領域が使用され、ピクセル単位でスクロールされますが、カスタマイズされたウィンドウの実装ではスクロール パラメーターを使用できます。 **付録 I** には GX_SCROLL_INFO 構造の定義が含まれています

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィンドウ スクロール情報の取得に成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_TYPE** (0x1B) 種類が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_SCROLL_INFO scroll_info;

/* Get scroll information for window “my_window”. */
status = gx_window_scroll_info_get(&my_window,
                    GX_SCROLLBAR_HORIZONTAL, &scroll_info);

/* If status is GX_SUCCESS the “scroll_info” contains the scroll information for window “my_window”. */
```
### <a name="see-also"></a>参照

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_scrollbar_find"></a>gx_window_scrollbar_find
### <a name="find-window-scrollbar"></a>ウィンドウのスクロールバーを探す

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_window_scrollbar_find(
    GX_WINDOW *window, 
    USHORT type,
    GX_SCROLLBAR **return_scrollbar);
```

### <a name="description"></a>説明

このサービスにより、指定されたウィンドウのスクロールバーが探されます。

### <a name="parameters"></a>パラメーター

- **window** ウィンドウへのポインター
- **type** GX_TYPE_VERTICAL_SCROLL または GX_TYPE_HORIZONTAL_SCROLL
- **return_scrollbar** スクロールバーの宛先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィンドウのスクロールバーが見つかりました
- **GX_NOT_FOUND** (0x09)スクロールバーが見つかりません
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です
- **GX_INVALID_TYPE** (0x1B) 種類が無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Find horizontal scrollbar for window “my_window”. */
status = gx_window_scrollbar_find(&my_window,
                 GX_SCROLLBAR_HORIZONTAL, &my_scrollbar);

/* If status is GX_SUCCESS the “my_scrollbar” contains the horizontal scrollbar for window “my_window”. */
```

### <a name="see-also"></a>参照

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_wallpaper_get"></a>gx_window_wallpaper_get
### <a name="get-window-wallpaper"></a>ウィンドウの壁紙を取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_window_wallpaper_get(
    GX_WINDOW *window,
    GX_RESOURCE_ID *return_wallpaper_id);
```

### <a name="description"></a>説明

このサービスにより、指定されたウィンドウの壁紙が取得されます。

### <a name="parameters"></a>パラメーター

- **window** ウィンドウへのポインター
- **return_wallpaper_id** 壁紙のリソース ID の宛先へのポインター

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィンドウの壁紙の取得に成功しました
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
GX_RESOURCE_ID my_window_wallpaper;

/* Get wallpaper for window “my_window”. */
status = gx_window_wallpaper_get(&my_window, &my_window_wallpaper);

/* If status is GX_SUCCESS the “my_window_wallpaper” contains the wallpaper resource ID for window “my_window”. */
```

### <a name="see-also"></a>参照

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_set

## <a name="gx_window_wallpaper_set"></a>gx_window_wallpaper_set
### <a name="set-window-wallpaper"></a>ウィンドウの壁紙を設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT gx_window_wallpaper_set(
    GX_WINDOW *window,
    GX_RESOURCE_ID wallpaper_id,
    GX_BOOL tile);
```

### <a name="description"></a>説明

このサービスにより、指定されたウィンドウの壁紙が設定されます。

### <a name="parameters"></a>パラメーター

- **window** ウィンドウへのポインター
- **wallpaper_id** 使用する壁紙のリソース ID
- **tile** GX_TRUE の場合には壁紙は並べて表示され、そうでない場合には並べて表示されません

### <a name="return-values"></a>戻り値

- **GX_SUCCESS** (0x00) ウィンドウの壁紙の設定に成功しました
- **GX_CALLER_ERROR** (0x11) この関数の呼び出し元が無効です
- **GX_PTR_ERROR** (0x07) ポインターが無効です
- **GX_INVALID_WIDGET** (0x12) ウィジェットが無効です

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="example"></a>例

```C
/* Set wallpaper for window “my_window”. */
status = gx_window_wallpaper_set(&my_window,
                                 MY_WALLPAPER_RESOURCE_ID,
                                 GX_TRUE);

/* If status is GX_SUCCESS the wallpaper for window “my_window” is set. */
```

### <a name="see-also"></a>参照

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
-  gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
