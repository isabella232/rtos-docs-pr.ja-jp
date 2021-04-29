---
title: 付録 D - ダンプとトレース バッファー
description: Azure RTOS ThreadX によって作成されたトレース バッファーをホスト コンピューター上のファイルにダンプするには、使用している特定の開発ツールによって提供されるコマンドやユーティリティを使用します。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 30f6b5e329feeb2dca37dda391fd738aba587c9a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812539"
---
# <a name="appendix-d---dumping-and-trace-buffer"></a>付録 D - ダンプとトレース バッファー

Azure RTOS ThreadX によって作成されたトレース バッファーをホスト コンピューター上のファイルにダンプするには、使用している特定の開発ツールによって提供されるコマンドやユーティリティを使用します。 この付録では、ThreadX と共に使用されるいくつかの一般的な開発ツールで、ホスト ファイルにトレース バッファーをダンプする例を示します。 

## <a name="benchx-tools"></a>BenchX ツール

トレース バッファーは、BenchX ツールを使用すると簡単にホスト ファイルにダンプできます。それには、次に示すように、_* _[Memory]\(メモリ\) ビュー_* 内の * **[Store Memory To File]\(メモリをファイルに保存する\)** _ ボタンを選択します。

![BenchX ツールの [Memory]\(メモリ\) ビューのスクリーンショット。](./media/user-guide/image642.jpg)

この時点で、トレース バッファーのアドレス、サイズ、出力先のファイル名 (パスを含む) を指定し、次に示すように ***[Save]\(保存\)*** ボタンを選択します。 これにより、TraceX 内で表示するバイナリ トレース ファイルが作成されます。

![BenchX ツールの保存ダイアログのスクリーンショット。](./media/user-guide/image643.jpg)

## <a name="realview-tools"></a>RealView ツール

トレース バッファーは、ARM RealView ツールを使用して簡単にホスト ファイルにダンプできます。それには、RealView のコマンド ライン プロンプトで次のコマンドを入力します。

```c 
> WRITEFILE,raw trace_file.trx=0x6860..0xE560
```

完了すると、ファイル ***trace_file.trx*** にトレース バッファーが格納され、アドレス 0x6860 からアドレス 0xE560 までに配置されます。 このファイルはすぐに TraceX で表示することができます。

## <a name="iar-tools"></a>IAR ツール

トレース バッファーは、IAR ツールを使用して簡単にホスト ファイルにダンプできます。それには、メモリ ビュー内で右クリックして、***[Memory Save…]\(メモリの保存…\)*** オプションを次に示すように選択するだけです。

![IAR ツールの [Memory Save]\(メモリの保存\) オプションのスクリーンショット。](./media/user-guide/image0_311.jpg)

そうすると、* **[Memory Save]\(メモリの保存\)** _ ダイアログが表示されます。 開始アドレスと終了アドレス、およびトレース ファイル名を入力し、_*_[Save]\(保存\)_*_ ボタンを選択します。 以下の例では、IAR ツールによって、指定したトレース バッファーが Intel HEX レコードとしてファイル _*_trace_file.hex_** に保存されます。

![IAR ツールの [Memory Save]\(メモリの保存\) ダイアログのスクリーンショット。](./media/user-guide/image648.jpg)

この時点で、トレース バッファーはホスト上の ***trace_file.hex*** ファイルに保存され、すぐに TraceX を使って表示できます。

## <a name="codewarrior-tools"></a>CodeWarrior ツール

トレース バッファーは、CodeWarrior ツールを使用して簡単にホスト ファイルにダンプできます。それには、コマンド ウィンドウに ***save** _ コマンドを入力します。 次の例の _ *_save_** コマンドでは、トレース バッファーが 0x102200 で始まり 0x109F00 で終わることが想定されています。

```c
> save –b p:0x102200..0x109F00 trace_file.trx -a 32bit
```

これを実行すると、トレース バッファーはホスト上のファイル ***trace_file.trx*** に保存されます。

## <a name="mplab-tools"></a>MPLAB ツール

MPLAB では、[Export Table]\(テーブルのエクスポート\) ユーティリティを使用して TraceX と互換性のあるトレース ファイルを作成できます。これにより、任意の範囲のメモリをホスト ファイルにエクスポートすることが可能になります。 このユーティリティを使用して TraceX 用のトレース ファイルを作成するには、次の手順を実行します。

**手順 1** [View]\(表示\) -> [Memory]\(メモリ\) の順に選択してメモリ ウィンドウを開きます。

![[View]\(表示\) メニューの [Memory]\(メモリ\) を選択するスクリーンショット。](./media/user-guide/image0_316.jpg)

**手順 2** **[Memory]\(メモリ\) ビュー** 内で右クリックすると、オプションの一覧が表示されます。 **[Display Format]\(表示形式\) -[1 Byte]\(1 バイト\)** を指定して、バイト表示を選択します。

![[Display Format]\(表示形式\) オプションが選択されている [Memory]\(メモリ\) ビューのスクリーンショット。](./media/user-guide/image650.png)

![[Go To] ダイアログのスクリーンショット。](./media/user-guide/image651.jpg)

**手順 3** **[Memory]\(メモリ\) ビュー** ウィンドウ内でもう一度右クリックし、 **[Go To]** を選択します。開かれるダイアログ ボックスで、イベント バッファーのアドレスを指定できます。 この例では、表示されている **_event_buffer_** が示されいます。

![[Go To] オプションが選択されている [Memory]\(メモリ\) ビューのスクリーンショット。](./media/user-guide/image0_312.jpg)

![表示されている event_buffer を示す例のスクリーンショット。](./media/user-guide/image653.png)

**手順 4** これにより、トレース バッファーの最初の場所の内容が強調表示されます。これは常に文字列 BTXT…. になります。

![トレース バッファーの最初の場所のスクリーンショット。](./media/user-guide/image0_313.jpg)

**手順 5** ここで、もう一度右クリックしてオプション メニューを表示し、 **[Export Table]\(テーブルのエクスポート\)** を選択します。

![[Export Table]\(テーブルのエクスポート\) オプションが選択されている [Memory]\(メモリ\) ビューのスクリーンショット。](./media/user-guide/image0_314.jpg)

**手順 6** これにより、次のように **[Export Table]\(テーブルのエクスポート\)** ダイアログが表示されます。 エクスポートするアドレスの範囲を指定します。 この例のケースのように、8K のトレース バッファーの場合は、0xA00006AC から 0xA00026AC の範囲を指定し、作成するホスト ファイルの名前 (この例では demo_threadx.trx) を入力します。

![[Export As]\(形式を指定してエクスポート\) ダイアログのスクリーンショット。](./media/user-guide/image656.jpg)

**手順 7** ホスト上に **demo_threadx.trx** という名前のファイルが作成されます。このファイルを TraceX で開くことができます。

## <a name="ghs-tools"></a>GHS ツール

トレース バッファーは、GHS ツールを使用して簡単にホスト ファイルにダンプできます。それには、デバッグ コマンド ウィンドウのコマンド ライン プロンプトで次のコマンドを入力します。

```c
memdump raw c:releasethreadxdemo_threadx.trx event_buffer 32768
```

完了すると、ファイル **demo_threadx.trx** にトレース バッファーが格納されます。それは 32,768 バイトのサイズで event_buffer に配置され、すぐに TraceX で表示できます。

## <a name="renesas-hew"></a>Renesas HEW

トレース バッファーは、Renasas HEW ツールを使用して簡単にホスト ファイルにダンプできます。それには、次の 3 つの手順 (およびサブ手順) に従います。

**手順 1** メモリ ウィンドウを開きます。

![[メモリ ウィンドウのスクリーンショット。](./media/user-guide/image657.jpg)

**手順 2** メモリ ウィンドウ内にカーソルを置き、右クリックします。

![[Save]\(保存\) オプションが選択されているメモリ ウィンドウのスクリーンショット。](./media/user-guide/image0_315.jpg)

**手順 3** [Save]\(保存\) を選択した後、[Save Memory As]\(形式を指定してメモリを保存する\) ウィンドウで次の操作を行います。

- [File format]\(ファイル形式\) を選択します: [Binary]\(バイナリ\)。
- [Filename]\(ファイル名\) を指定します: 任意
- [Start address]\(開始アドレス\) を指定します: trace_buffer
- [End address]\(終了アドレス\) を指定します: (trace_buffer+サイズ)
- [Access size]\(アクセス サイズ\) を指定します: 1
- [保存] をクリックします。

![[Save Memory As]\(形式を指定してメモリを保存する\) ダイアログのスクリーンショット。](./media/user-guide/image659.jpg)