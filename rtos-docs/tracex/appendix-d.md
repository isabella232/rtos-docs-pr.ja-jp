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
# <a name="appendix-d---dumping-and-trace-buffer"></a><span data-ttu-id="0de71-103">付録 D - ダンプとトレース バッファー</span><span class="sxs-lookup"><span data-stu-id="0de71-103">Appendix D - Dumping and trace buffer</span></span>

<span data-ttu-id="0de71-104">Azure RTOS ThreadX によって作成されたトレース バッファーをホスト コンピューター上のファイルにダンプするには、使用している特定の開発ツールによって提供されるコマンドやユーティリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="0de71-104">Dumping the trace buffer created by Azure RTOS ThreadX to a file on the host computer is done via commands and/or utilities provided by the specific development tool being used.</span></span> <span data-ttu-id="0de71-105">この付録では、ThreadX と共に使用されるいくつかの一般的な開発ツールで、ホスト ファイルにトレース バッファーをダンプする例を示します。</span><span class="sxs-lookup"><span data-stu-id="0de71-105">This appendix contains examples of dumping a trace buffer to a host file in some of the more popular development tools used with ThreadX.</span></span> 

## <a name="benchx-tools"></a><span data-ttu-id="0de71-106">BenchX ツール</span><span class="sxs-lookup"><span data-stu-id="0de71-106">BenchX Tools</span></span>

<span data-ttu-id="0de71-107">トレース バッファーは、BenchX ツールを使用すると簡単にホスト ファイルにダンプできます。それには、次に示すように、_\* _[Memory]\(メモリ\) ビュー_\* 内の \* **[Store Memory To File]\(メモリをファイルに保存する\)** _ ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="0de71-107">The trace buffer can be dumped to a host file easily with the BenchX tools by selecting the ***Store Memory To File** _ button within the _*_Memory View_\*\*, as shown below:</span></span>

![BenchX ツールの [Memory]\(メモリ\) ビューのスクリーンショット。](./media/user-guide/image642.jpg)

<span data-ttu-id="0de71-109">この時点で、トレース バッファーのアドレス、サイズ、出力先のファイル名 (パスを含む) を指定し、次に示すように ***[Save]\(保存\)*** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="0de71-109">At this point, specify the trace buffer address, size, destination file name (including path), and select the ***Save*** button as shown below.</span></span> <span data-ttu-id="0de71-110">これにより、TraceX 内で表示するバイナリ トレース ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0de71-110">This will create the binary trace file for viewing within TraceX.</span></span>

![BenchX ツールの保存ダイアログのスクリーンショット。](./media/user-guide/image643.jpg)

## <a name="realview-tools"></a><span data-ttu-id="0de71-112">RealView ツール</span><span class="sxs-lookup"><span data-stu-id="0de71-112">RealView Tools</span></span>

<span data-ttu-id="0de71-113">トレース バッファーは、ARM RealView ツールを使用して簡単にホスト ファイルにダンプできます。それには、RealView のコマンド ライン プロンプトで次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="0de71-113">The trace buffer can be dumped to a host file easily with the ARM RealView tools by entering the following command at the command-line prompt in RealView:</span></span>

```c 
> WRITEFILE,raw trace_file.trx=0x6860..0xE560
```

<span data-ttu-id="0de71-114">完了すると、ファイル ***trace_file.trx*** にトレース バッファーが格納され、アドレス 0x6860 からアドレス 0xE560 までに配置されます。</span><span class="sxs-lookup"><span data-stu-id="0de71-114">Upon completion, the file ***trace_file.trx*** will contain the trace buffer that is located starting at the address 0x6860 and goes up to address 0xE560.</span></span> <span data-ttu-id="0de71-115">このファイルはすぐに TraceX で表示することができます。</span><span class="sxs-lookup"><span data-stu-id="0de71-115">This file is ready for viewing by TraceX.</span></span>

## <a name="iar-tools"></a><span data-ttu-id="0de71-116">IAR ツール</span><span class="sxs-lookup"><span data-stu-id="0de71-116">IAR Tools</span></span>

<span data-ttu-id="0de71-117">トレース バッファーは、IAR ツールを使用して簡単にホスト ファイルにダンプできます。それには、メモリ ビュー内で右クリックして、***[Memory Save…]\(メモリの保存…\)***</span><span class="sxs-lookup"><span data-stu-id="0de71-117">The trace buffer can be dumped to a host file easily with the IAR tools by simply right-clicking in the memory view and selecting the ***Memory Save…***</span></span> <span data-ttu-id="0de71-118">オプションを次に示すように選択するだけです。</span><span class="sxs-lookup"><span data-stu-id="0de71-118">option, as shown below.</span></span>

![IAR ツールの [Memory Save]\(メモリの保存\) オプションのスクリーンショット。](./media/user-guide/image0_311.jpg)

<span data-ttu-id="0de71-120">そうすると、\* **[Memory Save]\(メモリの保存\)** _ ダイアログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0de71-120">This results in the \***Memory Save** _ dialog to be displayed.</span></span> <span data-ttu-id="0de71-121">開始アドレスと終了アドレス、およびトレース ファイル名を入力し、_\*_[Save]\(保存\)_\*_ ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="0de71-121">Enter the starting and ending address and the trace file name, then select the _*_Save_*_ button.</span></span> <span data-ttu-id="0de71-122">以下の例では、IAR ツールによって、指定したトレース バッファーが Intel HEX レコードとしてファイル _*_trace_file.hex_*\* に保存されます。</span><span class="sxs-lookup"><span data-stu-id="0de71-122">In the example shown below, the IAR tools save the specified trace buffer into Intel HEX records in the file _\*_trace_file.hex_\*\*.</span></span>

![IAR ツールの [Memory Save]\(メモリの保存\) ダイアログのスクリーンショット。](./media/user-guide/image648.jpg)

<span data-ttu-id="0de71-124">この時点で、トレース バッファーはホスト上の ***trace_file.hex*** ファイルに保存され、すぐに TraceX を使って表示できます。</span><span class="sxs-lookup"><span data-stu-id="0de71-124">At this point, we have the trace buffer saved in the ***trace_file.hex*** file on the host and is ready for viewing with TraceX.</span></span>

## <a name="codewarrior-tools"></a><span data-ttu-id="0de71-125">CodeWarrior ツール</span><span class="sxs-lookup"><span data-stu-id="0de71-125">CodeWarrior Tools</span></span>

<span data-ttu-id="0de71-126">トレース バッファーは、CodeWarrior ツールを使用して簡単にホスト ファイルにダンプできます。それには、コマンド ウィンドウに \***save** _ コマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="0de71-126">The trace buffer can be dumped to a host file easily with the CodeWarrior tools by entering the \***save** _ command in the Command Window.</span></span> <span data-ttu-id="0de71-127">次の例の _ *_save_*\* コマンドでは、トレース バッファーが 0x102200 で始まり 0x109F00 で終わることが想定されています。</span><span class="sxs-lookup"><span data-stu-id="0de71-127">The following example _ *_save_*\* command assumes the trace buffer starts at 0x102200 and ends at 0x109F00:</span></span>

```c
> save –b p:0x102200..0x109F00 trace_file.trx -a 32bit
```

<span data-ttu-id="0de71-128">これを実行すると、トレース バッファーはホスト上のファイル ***trace_file.trx*** に保存されます。</span><span class="sxs-lookup"><span data-stu-id="0de71-128">This results in the trace buffer being saved in the file ***trace_file.trx*** on the host.</span></span>

## <a name="mplab-tools"></a><span data-ttu-id="0de71-129">MPLAB ツール</span><span class="sxs-lookup"><span data-stu-id="0de71-129">MPLAB Tools</span></span>

<span data-ttu-id="0de71-130">MPLAB では、[Export Table]\(テーブルのエクスポート\) ユーティリティを使用して TraceX と互換性のあるトレース ファイルを作成できます。これにより、任意の範囲のメモリをホスト ファイルにエクスポートすることが可能になります。</span><span class="sxs-lookup"><span data-stu-id="0de71-130">MPLAB can create a TraceX-compatible trace file through its Export Table utility, which allows the export of any range of memory to a host file.</span></span> <span data-ttu-id="0de71-131">このユーティリティを使用して TraceX 用のトレース ファイルを作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0de71-131">To use this utility to create a trace file for TraceX, proceed as follows:</span></span>

<span data-ttu-id="0de71-132">**手順 1** [View]\(表示\) -> [Memory]\(メモリ\) の順に選択してメモリ ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="0de71-132">**Step 1** Open a memory window by selecting View -> Memory.</span></span>

![[View]\(表示\) メニューの [Memory]\(メモリ\) を選択するスクリーンショット。](./media/user-guide/image0_316.jpg)

<span data-ttu-id="0de71-134">**手順 2** **[Memory]\(メモリ\) ビュー** 内で右クリックすると、オプションの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0de71-134">**Step 2** Right-click within the **Memory View** to display a list of options.</span></span> <span data-ttu-id="0de71-135">**[Display Format]\(表示形式\) -[1 Byte]\(1 バイト\)** を指定して、バイト表示を選択します。</span><span class="sxs-lookup"><span data-stu-id="0de71-135">Specify **Display Format -1 Byte** to select byte display..</span></span>

![[Display Format]\(表示形式\) オプションが選択されている [Memory]\(メモリ\) ビューのスクリーンショット。](./media/user-guide/image650.png)

![[Go To] ダイアログのスクリーンショット。](./media/user-guide/image651.jpg)

<span data-ttu-id="0de71-138">**手順 3** **[Memory]\(メモリ\) ビュー** ウィンドウ内でもう一度右クリックし、 **[Go To]** を選択します。開かれるダイアログ ボックスで、イベント バッファーのアドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="0de71-138">**Step 3** Right-click again within the **Memory View** Window and select **Go To**, which opens a dialog box that enables you to specify the address of the event buffer.</span></span> <span data-ttu-id="0de71-139">この例では、表示されている **_event_buffer_** が示されいます。</span><span class="sxs-lookup"><span data-stu-id="0de71-139">This example shows **_event_buffer_** being displayed.</span></span>

![[Go To] オプションが選択されている [Memory]\(メモリ\) ビューのスクリーンショット。](./media/user-guide/image0_312.jpg)

![表示されている event_buffer を示す例のスクリーンショット。](./media/user-guide/image653.png)

<span data-ttu-id="0de71-142">**手順 4** これにより、トレース バッファーの最初の場所の内容が強調表示されます。これは常に文字列 BTXT…. になります。</span><span class="sxs-lookup"><span data-stu-id="0de71-142">**Step 4** This highlights the contents of the first location of the trace buffer, which is always the string BTXT….</span></span>

![トレース バッファーの最初の場所のスクリーンショット。](./media/user-guide/image0_313.jpg)

<span data-ttu-id="0de71-144">**手順 5** ここで、もう一度右クリックしてオプション メニューを表示し、 **[Export Table]\(テーブルのエクスポート\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0de71-144">**Step 5** Now, right-click again to bring up the options menu, and select **Export Table**.</span></span>

![[Export Table]\(テーブルのエクスポート\) オプションが選択されている [Memory]\(メモリ\) ビューのスクリーンショット。](./media/user-guide/image0_314.jpg)

<span data-ttu-id="0de71-146">**手順 6** これにより、次のように **[Export Table]\(テーブルのエクスポート\)** ダイアログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0de71-146">**Step 6** This brings up the **Export Table** dialog, as shown.</span></span> <span data-ttu-id="0de71-147">エクスポートするアドレスの範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="0de71-147">Specify the range of addresses to export.</span></span> <span data-ttu-id="0de71-148">この例のケースのように、8K のトレース バッファーの場合は、0xA00006AC から 0xA00026AC の範囲を指定し、作成するホスト ファイルの名前 (この例では demo_threadx.trx) を入力します。</span><span class="sxs-lookup"><span data-stu-id="0de71-148">For an 8K trace buffer, as is the case in this example, specify the range 0xA00006AC to 0xA00026AC, and enter a name for the host file to be created (demo_threadx.trx in this example).</span></span>

<span data-ttu-id="0de71-149">![[Export As]\(形式を指定してエクスポート\) ダイアログのスクリーンショット。](./media/user-guide/image656.jpg)</span><span class="sxs-lookup"><span data-stu-id="0de71-149">![[Screenshot of the Export As dialog.](./media/user-guide/image656.jpg)</span></span>

<span data-ttu-id="0de71-150">**手順 7** ホスト上に **demo_threadx.trx** という名前のファイルが作成されます。このファイルを TraceX で開くことができます。</span><span class="sxs-lookup"><span data-stu-id="0de71-150">**Step 7** A file named **demo_threadx.trx** will be created on the host, and this file can be opened by TraceX.</span></span>

## <a name="ghs-tools"></a><span data-ttu-id="0de71-151">GHS ツール</span><span class="sxs-lookup"><span data-stu-id="0de71-151">GHS Tools</span></span>

<span data-ttu-id="0de71-152">トレース バッファーは、GHS ツールを使用して簡単にホスト ファイルにダンプできます。それには、デバッグ コマンド ウィンドウのコマンド ライン プロンプトで次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="0de71-152">The trace buffer can be dumped to a host file easily with the GHS tools by entering the following command at the command-line prompt in the debug command window:</span></span>

```c
memdump raw c:releasethreadxdemo_threadx.trx event_buffer 32768
```

<span data-ttu-id="0de71-153">完了すると、ファイル **demo_threadx.trx** にトレース バッファーが格納されます。それは 32,768 バイトのサイズで event_buffer に配置され、すぐに TraceX で表示できます。</span><span class="sxs-lookup"><span data-stu-id="0de71-153">Upon completion, the file **demo_threadx.trx** will contain the trace buffer that is located in the event_buffer with a size of 32,768 bytes and is ready for viewing by TraceX.</span></span>

## <a name="renesas-hew"></a><span data-ttu-id="0de71-154">Renesas HEW</span><span class="sxs-lookup"><span data-stu-id="0de71-154">Renesas HEW</span></span>

<span data-ttu-id="0de71-155">トレース バッファーは、Renasas HEW ツールを使用して簡単にホスト ファイルにダンプできます。それには、次の 3 つの手順 (およびサブ手順) に従います。</span><span class="sxs-lookup"><span data-stu-id="0de71-155">The trace buffer can be dumped to a host file easily with the Renasas HEW tools by following the three steps (and substeps) below:</span></span>

<span data-ttu-id="0de71-156">**手順 1** メモリ ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="0de71-156">**Step 1** Open Memory Window.</span></span>

<span data-ttu-id="0de71-157">![[メモリ ウィンドウのスクリーンショット。](./media/user-guide/image657.jpg)</span><span class="sxs-lookup"><span data-stu-id="0de71-157">![[Screenshot of the Memory Window.](./media/user-guide/image657.jpg)</span></span>

<span data-ttu-id="0de71-158">**手順 2** メモリ ウィンドウ内にカーソルを置き、右クリックします。</span><span class="sxs-lookup"><span data-stu-id="0de71-158">**Step 2** Place cursor within memory window and right click.</span></span>

![[Save]\(保存\) オプションが選択されているメモリ ウィンドウのスクリーンショット。](./media/user-guide/image0_315.jpg)

<span data-ttu-id="0de71-160">**手順 3** [Save]\(保存\) を選択した後、[Save Memory As]\(形式を指定してメモリを保存する\) ウィンドウで次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="0de71-160">**Step 3** Select Save, then in the Save Memory As window do the following:</span></span>

- <span data-ttu-id="0de71-161">[File format]\(ファイル形式\) を選択します: [Binary]\(バイナリ\)。</span><span class="sxs-lookup"><span data-stu-id="0de71-161">Select File format: Binary.</span></span>
- <span data-ttu-id="0de71-162">[Filename]\(ファイル名\) を指定します: 任意</span><span class="sxs-lookup"><span data-stu-id="0de71-162">Specify Filename: As Desired</span></span>
- <span data-ttu-id="0de71-163">[Start address]\(開始アドレス\) を指定します: trace_buffer</span><span class="sxs-lookup"><span data-stu-id="0de71-163">Specify Start address: trace_buffer</span></span>
- <span data-ttu-id="0de71-164">[End address]\(終了アドレス\) を指定します: (trace_buffer+サイズ)</span><span class="sxs-lookup"><span data-stu-id="0de71-164">Specify End address: (trace_buffer+size)</span></span>
- <span data-ttu-id="0de71-165">[Access size]\(アクセス サイズ\) を指定します: 1</span><span class="sxs-lookup"><span data-stu-id="0de71-165">Specify Access size: 1</span></span>
- <span data-ttu-id="0de71-166">[保存] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0de71-166">Click Save</span></span>

![[Save Memory As]\(形式を指定してメモリを保存する\) ダイアログのスクリーンショット。](./media/user-guide/image659.jpg)