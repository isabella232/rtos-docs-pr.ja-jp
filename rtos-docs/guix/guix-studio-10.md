---
title: 単純なプロジェクト例
description: この章では、プロジェクト例を GUIX Studio で作成して、この例を GUIX で実行する方法について説明します。
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 8981bed62d2929703e4233d6a3ee31b692226c26d046875a235bf3aca32a7573
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116786567"
---
# <a name="chapter-10-example-project"></a>第 10 章: プロジェクト例

この章では、プロジェクト例を GUIX Studio で作成して、この例を GUIX で実行する方法について説明します。

## <a name="create-new-project"></a>新しいプロジェクトの作成

最初の手順では、新しいプロジェクトを作成して、プロジェクトでサポートされる表示と言語を構成します。 GUIX Studio を最初に起動すると、***[最近使ったプロジェクト]*** 画面が表示されます。

![GUIX Studio の [最近使ったプロジェクト] ダイアログのスクリーンショット。](./media/guix-studio/recent_projects.png)

**図 10.1**

* **[新しいプロジェクトの作成]** _ ボタンをクリックして、新しいプロジェクトを開始します。 こちらに示すような、_ *_[New GUIX Project]\(新しい GUIX プロジェクト\)_** ダイアログが表示されます。

![GUIX Studio の [新しいプロジェクトの作成] ダイアログのスクリーンショット。](./media/guix-studio/create_new_project.png)

**図 10.2**

プロジェクト名として「***new_example***」という名前を入力します。 プロジェクト名には、標準の C 変数名前付けルールを使用する必要があります (特殊および予約文字は不可)。 プロジェクトを保存する場所へのパスを入力します。 パスは有効なファイル システム ディレクトリでなければなりません。存在しない場合、ディレクトリは作成されません。 [OK] をクリックしてプロジェクトを作成します。

次に表示される画面は、こちらに示す [プロジェクト構成] 画面です。

![GUIX Studio の [プロジェクト構成] ダイアログのスクリーンショット。](./media/guix-studio/config_new_project.png)

**図 10.3**

このダイアログでは、プロジェクトでサポートするディスプレイ数を指定して、各ディスプレイに名前を付けます。 各ディスプレイでサポートされるカラー フォーマットを指定し、必要に応じてStudio によって各ディスプレイ用に生成される出力ファイルのパス名を入力します。 出力ファイルの既定のディレクトリは "***.\\***" です。これは、C 出力ファイルがプロジェクト自体と同じディレクトリに書き込まれることを意味します。

この例では、* **[Number of Displays]\(ディスプレイ数\)** _ を "1" のままにして、表示名 フィールドに「_*_main_display_*_」という名前を入力し、_*_[allocate canvas memory]\(キャンバス メモリの割り当て\)_*_ オンにします。 解像度、カラー フォーマット、ディレクトリの各フィールドを既定値のままにし、_* _[OK]_ ** をクリックします。

これにより、図10.4 に示すように、プロジェクトが Studio IDE で開いて表示されます。

![Studio IDE で開いているプロジェクトのスクリーンショット。](./media/guix-studio/initial_screen.png)

**図 10.4**

新しいプロジェクトを作成すると、プロジェクトの開始点として既定のウィンドウが自動的に作成されます。 この灰色のボックスは自動的に作成された既定のウィンドウで、"*ターゲット ビュー*" の中央にあります。

このウィンドウが選択されていない場合は、ウィンドウをクリックすると、ウィンドウの周囲に破線の選択ボックスが描画されます。 * **[Properties View]\(プロパティ ビュー\)** _ で、_*_[Widget Name]\(ウィジェット名\)_*_、_*_[Widget Id]\(ウィジェット ID\)_*_、_*_[左]_*_、_*_[上]_*_ 、_*_[幅]_*_ 、_*_[高さ]_*_ 、および _ *_[Border]\(境界線\)_* * を下に示す設定に合わせて変更します。 これらの変更を行うと、変更内容がすぐにターゲット ビュー内に反映されて表示されます。

![[Properties View]\(プロパティ ビュー\) ダイアログのスクリーンショット。](./media/guix-studio/initial_window_properties.png)

**図 10.5**

次に、***GX_ICON** _ ウィジェット内で使用されるピクセルマップ リソースを追加します。 GUIX Studio ディストリビューションには複数のアイコンが用意されており、それらをこの例で使用します。 _*_[Pixelmaps]\(ピクセルマップ\)_*_ リソース ビューを展開して、_ *_[Add New Pixelmap]\(新しいピクセルマップの追加\)_** ボタンをクリックします。

![[Add New Pixelmap]\(新しいピクセルマップの追加\) ボタンのスクリーンショット。](./media/guix-studio/image74.jpg)

GUIX Studio のインストール フォルダーを参照し、* **./graphics/icons** _ フォルダー内で _*_i_history_lg.png_*_ という名前のファイルを選択します。 _*_[開く]_*_ をクリックしてこのリソースをプロジェクトに追加します。 これで、_ *_[Pixelmaps]\(ピクセルマップ\)_** リソース ビューに、新しく追加したアイコン イメージのプレビューが表示されるようになりました。

![[Pixelmaps]\(ピクセルマップ\) リソース ビューのスクリーンショット。](./media/guix-studio/example_add_pixelmap.png)

**図 10.6**

この新しいイメージ リソースは、後で UI デザインの一部として使用します。

ピクセルマップ リソースを追加するのと同様に、新しいフォント リソースをツールボックスに追加して、このフォントを後でデザインで使用できるようにします。 * **[フォント]** _ リソース ビューを展開して、_*_[Add New Font]\(新しいフォントの追加\)_*_ ボタンをクリックします。 この操作により、_*_[Add font]\(フォントの追加\) または [Edit font]\(フォントの編集\)_*_ ダイアログが呼び出されます。 次に、GUIX Studio のインストール フォルダーで、指定されている GUIX フォント _*_ .\\fonts\\verasans_ *_ を参照し、_* _VeraIt.ttf_ *_という名前の TrueType フォント ファイルを選択します。フォント名フィールドにフォント名「_*_MEDIUM_ITALIC_*_」を入力して、高さフィールドに「_*_30_**」を入力します。 ダイアログはこちらのようになります。

![[Edit Font]\(フォントの編集\)ダイアログのスクリーンショット。](./media/guix-studio/example_add_font.png)

**図 10.7**

***[OK]*** をクリックして、このフォントをプロジェクトに追加します。 リソース ビューにフォントが表示されます。

![リソース ビューのフォントのスクリーンショット。](./media/guix-studio/example_font_added.png)

**図 10.8**

この新しいフォントは、後で UI デザインで使用します。

いくつかの新しいリソースを利用できるようになったので、いくつかの子ウィジェットを画面に追加してこれらのリソースを利用できるようにする必要があります。 ターゲット ビューで右クリックして、前に作成した "***hello_world** _" という名前のウィンドウを選択します。 表示されたポップアップ メニューで、メニュー コマンド _*_[Insert]\(挿入\)、[Text]\(テキスト\)、[Prompt]\(プロンプト\)_*_ を選択して、新しい _ *_GX_PROMPT_** ウィジェットを挿入し、このウィジェットを背景ウィンドウにアタッチします。 ウィンドウはこちらのようになります。

![[Prompt]\(プロンプト\) が選択されたポップアップ メニューのスクリーンショット](./media/guix-studio/image78.jpg)

**図 10.9**

"***MEDIUM_ITALIC** _" という名前のフォントを _ *_[フォント]_** リソース ビューでクリックして、プロンプト ウィジェットにドラッグ アンド ドロップします。 次に、プロンプトのプロパティを図 10.10 に示すように編集してプロンプトのサイズを変更し、プロンプトの透明度を設定し、プロンプトのテキストとスタイルを変更します。

![プロンプトの [Properties View]\(プロパティ ビュー\) のスクリーンショット。](./media/guix-studio/image79.jpg)

**図 10.10**

画面の解像度によっては、[Properties View]\(プロパティ ビュー\) を縦にスクロールしてこれらの設定をそれぞれ表示する必要があります。 これらの変更を行った後、ターゲット ビューはこちらのようになります。

![Hello World が選択されたポップアップ メニューのスクリーンショット。](./media/guix-studio/image80.jpg)

**図 10.11**

次に、アイコン ボタンのスタイル ウィジェットを画面に置きます。 背景ウィンドウをクリックして選択し、最上位メニューまたは右クリック ポップアップ メニューを使用して、* **[Insert]\(挿入\)、[Button]\(ボタン\)、[Icon Button]\(アイコン ボタン\)** _ を選択して新しい _*_GX_ICON_BUTTON_*_ をウィンドウに追加します。 先ほど追加した _ *_I_HISTORY_LG_** という名前のアイコンをクリックして、アイコン ボタンにドラッグします。 [Properties View]\(プロパティ ビュー\) を使用して、アイコンの位置とサイズを下に示すように調整します。

![アイコン ボタン スタイル ウィジェットの [Properties View]\(プロパティ ビュー\) のスクリーンショット。](./media/guix-studio/image81.jpg)

**図 10.12**

画面はこちらのようになるはずです。

![Hello World とクリップボード アイコンが表示されたポップアップ メニューのスクリーンショット。](./media/guix-studio/image82.jpg)

**図 10.13**

これで、単純な画面デザインの例は完成です。 実際のアプリケーション画面はずっと高度なものになるでしょうが、GUIX Studio を使用して独自のアプリケーション画面を作成する方法を紹介するにはこれで十分です。

## <a name="generate-resource-and-application-code"></a>リソースとアプリケーション コードの生成

次の手順では、埋め込み GUIX ランタイム UI を定義するリソース ファイルと仕様ファイルを生成します。 出力ファイルを生成するには、プロジェクト ビューで ***main_display** _ ノードを右クリックして _ *_[Generate Resource Files]\(リソース ファイルの生成\)_** コマンドを選択する必要があります。 表示される情報ウィンドウにリソース ファイルが生成されたことが示されます (図 10.14 を参照)。

![通知ダイアログのスクリーンショット。](./media/guix-studio/image83.jpg)

**図 10.14**

* **[OK]** _ をクリックしてこの通知を無視して、同じ手順を使用して _*_main_display_*_ ノードを右クリックして _ *_[Generate Specification Files]\(仕様ファイルの生成\)_** コマンドを選択します。 同様の通知ウィンドウが表示されます。 これで、単純な UI アプリケーション ファイルが生成されました。

## <a name="create-user-supplied-code"></a>ユーザー指定コードの作成

次の手順では、GUIX Studio で生成された画面デザインを呼び出す独自のアプリケーション ファイルを作成します。 好きなエディターを使用して、***new_example.c*** という名前のソース ファイルを作成して、このファイルに次のソース コードを入力します。

```C

/* This is an example of the GUIX graphics framework in Win32. */
/* Include system files. */

#include <stdio.h>
#include "tx_api.h"
#include "gx_api.h"

/* Include GUIX resource and specification files for example. */

#include "new_example_resources.h"
#include "new_example_specifications.h"

/* Define the new example thread control block and stack. */

TX_THREAD new_example_thread;
UCHAR new_example_thread_stack[4096];

/* Define the root window pointer. */

GX_WINDOW_ROOT *root_window;

/* Define function prototypes. */

VOID new_example_thread_entry(ULONG thread_input);
UINT win32_graphics_driver_setup_24bpp(GX_DISPLAY *display);

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
    return(0);
}

VOID tx_application_define(void *first_unused_memory)
{
    /* Create the new example thread. */
    tx_thread_create(&new_example_thread, "GUIX New Example Thread", 
                      new_example_thread_entry, 0, 
                      new_example_thread_stack, sizeof(new_example_thread_stack),
                      1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

VOID new_example_thread_entry(ULONG thread_input)
{

    /* Initialize the GUIX library */
    gx_system_initialize();

    /* Configure the main display. */
    gx_studio_display_configure(MAIN_DISPLAY,                      /* Display to configure*/
                                win32_graphics_driver_setup_24bpp, /* Driver to use */
                                LANGUAGE_ENGLISH,                  /* Language to install */
                                MAIN_DISPLAY_DEFAULT_THEME,        /* Theme to install */
                                &root_window);                     /* Root window pointer */

    /* Create the screen - attached to root window. */

    gx_studio_named_widget_create("hello_world", (GX_WIDGET *) root_window, GX_NULL);

    /* Show the root window to make it visible. */
    gx_widget_show(root_window);

    /* Let GUIX run. */
    gx_system_start();

}
```

上のソース コードによって `GUIX New Example Thread` という名前の典型的な ThreadX スレッドが、4K バイトのスタック サイズで作成されます。 ***new_example_thread_entry*** という名前の関数で始まる動作に注目してください。 この関数から、GUIX 特有スレッドの実行が開始します。

最初の呼び出しは、***gx_system_initialize*** という名前の関数に対して行なわれます。 この呼び出しは、他の GUIX API を呼び出して GUIX ライブラリを初めて使用するための準備をする前に、かならず必要です。

次に、この例では ***gx_studio_display_configure*** 関数を呼び出します。 この関数は GUIX 表示インスタンスを作成し、要求された言語のアプリケーション文字列テーブルをインストールし、要求されたテーマを表示リソースからインストールし、この表示用に作成されたルート ウィンドウへのポインターを返します。 ルート ウィンドウは、このアプリケーションで表示されるすべての最上位の画面の親として使用されます。

次に、この例では ***gx_studio_named_widget_create** _ を呼び出して _ *_hello_world_** 画面のインスタンスを作成します。 この関数は、GUIX Studio によって作成されるデータ構造とリソースを使用して、画面のインスタンスをここで定義したとおりに作成します。 ルート ウィンドウのポインターを 2 番目のパラメーターとしてこの関数呼び出しに渡します。つまり、画面をすぐにルート ウィンドウにアタッチします。 最後のパラメーターは、作成された画面へのポインターを保持する場合に使用できるオプションの戻りポインターです。

次に ***gx_widget_show** _ を呼び出します。これにより、ルート ウィンドウとそのすべての子 (_ *_hello_world_** 画面を含む) が表示されます。

最後に、この例では ***gx_system_start*** を呼び出します。 この関数は、GUIX システム イベント処理ループの実行を開始します。

## <a name="build-and-run-the-example"></a>例のビルドと実行

例のビルドと実行は、お使いのビルド ツールと環境に固有です。 しかし、一般的なプロセスを次のように定義できます。

1. 新しいディレクトリとアプリケーション プロジェクトを作成します
1. プロジェクトにこちらのファイルを追加します

    **new_example_resources.c**

    **new_example_specification.c**

    **new_example.c**

1. GUIX Studio インストール パス ***./win32_runtime*** の Win32 ランタイム サポート ファイルを追加します。 この中には、ThreadX および GUIX Win32 ヘッダーおよびランタイム ライブラリ ファイルが含まれます。
1. GUIX Win32 ライブラリ (***gx.lib***) をプロジェクトに追加します。
1. ThreadX Win32 ライブラリ (***tx.lib***) をプロジェクトに追加します。
1. アプリケーションのコンパイル、リンク、実行を行います。
