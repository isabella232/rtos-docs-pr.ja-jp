---
title: 第 5 章 - Azure RTOS ThreadX のデバイス ドライバー
description: この章では、Azure RTOS ThreadX のデバイス ドライバーについて説明します。
author: philmea
ms.author: philmea
ms.date: 05/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2432b291f2b3fa7d6d798b8b4c187dd20b97db6b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812173"
---
# <a name="chapter-5---device-drivers-for-azure-rtos-threadx"></a><span data-ttu-id="bd046-103">第 5 章 - Azure RTOS ThreadX のデバイス ドライバー</span><span class="sxs-lookup"><span data-stu-id="bd046-103">Chapter 5 - Device Drivers for Azure RTOS ThreadX</span></span>

<span data-ttu-id="bd046-104">この章では、Azure RTOS ThreadX のデバイス ドライバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bd046-104">This chapter contains a description of device drivers for Azure RTOS ThreadX.</span></span> <span data-ttu-id="bd046-105">この章に記載されている情報は、アプリケーション固有のドライバーを作成する開発者を支援することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="bd046-105">The information presented in this chapter is designed to help developers write application-specific drivers.</span></span>

## <a name="device-driver-introduction"></a><span data-ttu-id="bd046-106">デバイス ドライバーの概要</span><span class="sxs-lookup"><span data-stu-id="bd046-106">Device Driver Introduction</span></span>

<span data-ttu-id="bd046-107">外部環境との通信は、ほとんどの組み込みアプリケーションの重要な構成要素です。</span><span class="sxs-lookup"><span data-stu-id="bd046-107">Communication with the external environment is an important component of most embedded applications.</span></span> <span data-ttu-id="bd046-108">この通信は、組み込みアプリケーション ソフトウェアがアクセス可能なハードウェア デバイスを介して行われます。</span><span class="sxs-lookup"><span data-stu-id="bd046-108">This communication is accomplished through hardware devices that are accessible to the embedded application software.</span></span> <span data-ttu-id="bd046-109">このようなデバイスを管理する役割を担うソフトウェア コンポーネントは、一般に "*デバイス ドライバー*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="bd046-109">The software components responsible for managing such devices are commonly called *device drivers*.</span></span>

<span data-ttu-id="bd046-110">組み込みのリアルタイム システムのデバイス ドライバーは、本質的にアプリケーションに依存しています。</span><span class="sxs-lookup"><span data-stu-id="bd046-110">Device drivers in embedded, real-time systems are inherently application dependent.</span></span> <span data-ttu-id="bd046-111">これには 2 つの主な理由があります。それは、ターゲット ハードウェアが多種多様であることと、リアルタイム アプリケーションに課せられるパフォーマンス要件も同様に広範であることです。</span><span class="sxs-lookup"><span data-stu-id="bd046-111">This is true for two principal reasons: the vast diversity of target hardware and the equally vast performance requirements imposed on real-time applications.</span></span> <span data-ttu-id="bd046-112">そのため、すべてのアプリケーションの要件を満たすことができる共通のドライバー セットを提供するのは実質的に不可能です。</span><span class="sxs-lookup"><span data-stu-id="bd046-112">Because of this, it is virtually impossible to provide a common set of drivers that will meet the requirements of every application.</span></span> <span data-ttu-id="bd046-113">これらの理由から、この章の情報は、ユーザーが "*既製*" の ThreadX デバイス ドライバーをカスタマイズし、独自のドライバーを作成できるよう支援することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="bd046-113">For these reasons, the information in this chapter is designed to help users customize *off-the-shelf* ThreadX device drivers and write their own specific drivers.</span></span>

## <a name="driver-functions"></a><span data-ttu-id="bd046-114">ドライバーの機能</span><span class="sxs-lookup"><span data-stu-id="bd046-114">Driver Functions</span></span>

<span data-ttu-id="bd046-115">ThreadX デバイス ドライバーは、次の 8 つの基本的な機能領域で構成されています。</span><span class="sxs-lookup"><span data-stu-id="bd046-115">ThreadX device drivers are composed of eight basic functional areas, as follows.</span></span>

- <span data-ttu-id="bd046-116">**ドライバーの初期化**</span><span class="sxs-lookup"><span data-stu-id="bd046-116">**Driver Initialization**</span></span>
- <span data-ttu-id="bd046-117">**ドライバー制御**</span><span class="sxs-lookup"><span data-stu-id="bd046-117">**Driver Control**</span></span>
- <span data-ttu-id="bd046-118">**ドライバー アクセス**</span><span class="sxs-lookup"><span data-stu-id="bd046-118">**Driver Access**</span></span>
- <span data-ttu-id="bd046-119">**ドライバーの入力**</span><span class="sxs-lookup"><span data-stu-id="bd046-119">**Driver Input**</span></span>
- <span data-ttu-id="bd046-120">**ドライバーの出力**</span><span class="sxs-lookup"><span data-stu-id="bd046-120">**Driver Output**</span></span>
- <span data-ttu-id="bd046-121">**ドライバーの割り込み**</span><span class="sxs-lookup"><span data-stu-id="bd046-121">**Driver Interrupts**</span></span>
- <span data-ttu-id="bd046-122">**ドライバーの状態**</span><span class="sxs-lookup"><span data-stu-id="bd046-122">**Driver Status**</span></span>
- <span data-ttu-id="bd046-123">**ドライバーの終了**</span><span class="sxs-lookup"><span data-stu-id="bd046-123">**Driver Termination**</span></span>

<span data-ttu-id="bd046-124">初期化を除き、ドライバーの各機能領域は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="bd046-124">With the exception of initialization, each driver functional area is optional.</span></span> <span data-ttu-id="bd046-125">さらに、各領域での正確な処理はデバイス ドライバーに固有です。</span><span class="sxs-lookup"><span data-stu-id="bd046-125">Furthermore, the exact processing in each area is specific to the device driver.</span></span>

### <a name="driver-initialization"></a><span data-ttu-id="bd046-126">ドライバーの初期化</span><span class="sxs-lookup"><span data-stu-id="bd046-126">Driver Initialization</span></span>
<span data-ttu-id="bd046-127">この機能領域は、実際のハードウェア デバイスとドライバーの内部データ構造の初期化を担当します。</span><span class="sxs-lookup"><span data-stu-id="bd046-127">This functional area is responsible for initialization of the actual hardware device and the internal data structures of the driver.</span></span> <span data-ttu-id="bd046-128">初期化が完了するまで、他のドライバー サービスを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="bd046-128">Calling other driver services is not allowed until initialization is complete.</span></span>

> [!NOTE]
> <span data-ttu-id="bd046-129">"*ドライバーの初期化関数コンポーネントは、通常、\*\*\*tx_application_define*\* _ 関数または初期化スレッドから呼び出されます。_"</span><span class="sxs-lookup"><span data-stu-id="bd046-129">\*The driver's initialization function component is typically called from the \***tx_application_define** _ function or from an initialization thread._</span></span>

### <a name="driver-control"></a><span data-ttu-id="bd046-130">ドライバー制御</span><span class="sxs-lookup"><span data-stu-id="bd046-130">Driver Control</span></span>

<span data-ttu-id="bd046-131">ドライバーが初期化され、操作の準備が整うと、この機能領域が実行時の制御を担当します。</span><span class="sxs-lookup"><span data-stu-id="bd046-131">After the driver is initialized and ready for operation, this functional area is responsible for run-time control.</span></span> <span data-ttu-id="bd046-132">通常、実行時の制御は、基になるハードウェア デバイスの変更で構成されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-132">Typically, run-time control consists of making changes to the underlying hardware device.</span></span> <span data-ttu-id="bd046-133">例として、シリアル デバイスのボー レートの変更や、ディスク上の新しいセクターのシークが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="bd046-133">Examples include changing the baud rate of a serial device or seeking a new sector on a disk.</span></span>

### <a name="driver-access"></a><span data-ttu-id="bd046-134">ドライバー アクセス</span><span class="sxs-lookup"><span data-stu-id="bd046-134">Driver Access</span></span>

<span data-ttu-id="bd046-135">一部のデバイス ドライバーは、1 つのアプリケーション スレッドからのみ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-135">Some device drivers are called only from a single application thread.</span></span> <span data-ttu-id="bd046-136">このような場合、この機能領域は不要です。</span><span class="sxs-lookup"><span data-stu-id="bd046-136">In such cases, this functional area is not needed.</span></span> <span data-ttu-id="bd046-137">ただし、複数のスレッドがドライバーに同時にアクセスする必要があるアプリケーションでは、デバイス ドライバーに割り当て/解放機能を追加して、対話を制御する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd046-137">However, in applications where multiple threads need simultaneous driver access, their interaction must be controlled by adding assign/ release facilities in the device driver.</span></span> <span data-ttu-id="bd046-138">代わりに、アプリケーションでセマフォを使用してドライバー アクセスを制御し、ドライバー内の余分なオーバーヘッドや複雑さを回避することもできます。</span><span class="sxs-lookup"><span data-stu-id="bd046-138">Alternatively, the application may use a semaphore to control driver access and avoid extra overhead and complication inside the driver.</span></span>

### <a name="driver-input"></a><span data-ttu-id="bd046-139">ドライバーの入力</span><span class="sxs-lookup"><span data-stu-id="bd046-139">Driver Input</span></span>

<span data-ttu-id="bd046-140">この機能領域は、すべてのデバイス入力を担当します。</span><span class="sxs-lookup"><span data-stu-id="bd046-140">This functional area is responsible for all device input.</span></span> <span data-ttu-id="bd046-141">ドライバーの入力に関連する主な問題には、通常、入力をバッファーする方法と、スレッドがその入力を待機する方法が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bd046-141">The principal issues associated with driver input usually involve how the input is buffered and how threads wait for such input.</span></span>

### <a name="driver-output"></a><span data-ttu-id="bd046-142">ドライバーの出力</span><span class="sxs-lookup"><span data-stu-id="bd046-142">Driver Output</span></span>

<span data-ttu-id="bd046-143">この機能領域は、すべてのデバイス出力を担当します。</span><span class="sxs-lookup"><span data-stu-id="bd046-143">This functional area is responsible for all device output.</span></span> <span data-ttu-id="bd046-144">ドライバーの出力に関連する主な問題には、通常、出力をバッファーする方法と、スレッドが出力の実行を待機する方法が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bd046-144">The principal issues associated with driver output usually involve how the output is buffered and how threads wait to perform output.</span></span>

### <a name="driver-interrupts"></a><span data-ttu-id="bd046-145">ドライバーの割り込み</span><span class="sxs-lookup"><span data-stu-id="bd046-145">Driver Interrupts</span></span>

<span data-ttu-id="bd046-146">ほとんどのリアルタイム システムでは、デバイスの入力、出力、制御、エラーの各イベントをドライバーに通知するために、ハードウェア割り込みを利用します。</span><span class="sxs-lookup"><span data-stu-id="bd046-146">Most real-time systems rely on hardware interrupts to notify the driver of device input, output, control, and error events.</span></span> <span data-ttu-id="bd046-147">割り込みにより、このような外部イベントに対する応答時間が保証されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-147">Interrupts provide a guaranteed response time to such external events.</span></span> <span data-ttu-id="bd046-148">割り込みの代わりに、ドライバー ソフトウェアで外部ハードウェアを定期的にチェックして、このようなイベントの有無を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="bd046-148">Instead of interrupts, the driver software may periodically check the external hardware for such events.</span></span> <span data-ttu-id="bd046-149">この手法は "*ポーリング*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="bd046-149">This technique is called *polling*.</span></span> <span data-ttu-id="bd046-150">割り込みに比べてリアルタイム性は劣りますが、リアルタイム性の低いアプリケーションではポーリングが効果的である場合もあります。</span><span class="sxs-lookup"><span data-stu-id="bd046-150">It is less real-time than interrupts, but polling may make sense for some less real-time applications.</span></span>

### <a name="driver-status"></a><span data-ttu-id="bd046-151">ドライバーの状態</span><span class="sxs-lookup"><span data-stu-id="bd046-151">Driver Status</span></span>

<span data-ttu-id="bd046-152">この機能領域は、ドライバー操作に関連する実行時の状態と統計情報を提供する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="bd046-152">This function area is responsible for providing run-time status and statistics associated with the driver operation.</span></span> <span data-ttu-id="bd046-153">この機能領域によって管理される情報には、通常、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bd046-153">Information managed by this function area typically includes the following.</span></span>

- <span data-ttu-id="bd046-154">デバイスの現在の状態</span><span class="sxs-lookup"><span data-stu-id="bd046-154">Current device status</span></span>
- <span data-ttu-id="bd046-155">入力バイト数</span><span class="sxs-lookup"><span data-stu-id="bd046-155">Input bytes</span></span>
- <span data-ttu-id="bd046-156">出力バイト数</span><span class="sxs-lookup"><span data-stu-id="bd046-156">Output bytes</span></span>
- <span data-ttu-id="bd046-157">デバイスのエラー数</span><span class="sxs-lookup"><span data-stu-id="bd046-157">Device error counts</span></span>

### <a name="driver-termination"></a><span data-ttu-id="bd046-158">ドライバーの終了</span><span class="sxs-lookup"><span data-stu-id="bd046-158">Driver Termination</span></span>

<span data-ttu-id="bd046-159">この機能領域は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="bd046-159">This functional area is optional.</span></span> <span data-ttu-id="bd046-160">ドライバーや物理ハードウェア デバイスをシャットダウンする必要がある場合にのみ必要となります。</span><span class="sxs-lookup"><span data-stu-id="bd046-160">It is only required if the driver and/or the physical hardware device need to be shut down.</span></span> <span data-ttu-id="bd046-161">終了後は、再初期化されるまでドライバーを再度呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="bd046-161">After being terminated, the driver must not be called again until it is reinitialized.</span></span>

## <a name="simple-driver-example"></a><span data-ttu-id="bd046-162">簡易ドライバーの例</span><span class="sxs-lookup"><span data-stu-id="bd046-162">Simple Driver Example</span></span>

<span data-ttu-id="bd046-163">デバイス ドライバーを記述するための最良の方法は例を使うことです。</span><span class="sxs-lookup"><span data-stu-id="bd046-163">An example is the best way to describe a device driver.</span></span> <span data-ttu-id="bd046-164">この例では、構成レジスタ、入力レジスタ、出力レジスタを備えた単純なシリアル ハードウェア デバイスがドライバーによって想定されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-164">In this example, the driver assumes a simple serial hardware device with a configuration register, an input register, and an output register.</span></span> <span data-ttu-id="bd046-165">この簡易ドライバーの例では、初期化、入力、出力、割り込みの各機能領域を示します。</span><span class="sxs-lookup"><span data-stu-id="bd046-165">This simple driver example illustrates the initialization, input, output, and interrupt functional areas.</span></span>

### <a name="simple-driver-initialization"></a><span data-ttu-id="bd046-166">簡易ドライバーの初期化</span><span class="sxs-lookup"><span data-stu-id="bd046-166">Simple Driver Initialization</span></span>

<span data-ttu-id="bd046-167">簡易ドライバーの ***tx_sdriver_initialize*** 関数により、ドライバーの入出力操作の管理に使用される 2 つのカウント セマフォが作成されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-167">The ***tx_sdriver_initialize*** function of the simple driver creates two counting semaphores that are used to manage the driver's input and output operation.</span></span> <span data-ttu-id="bd046-168">入力セマフォは、シリアル ハードウェア デバイスが文字を受信したときに入力 ISR によって設定されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-168">The input semaphore is set by the input ISR when a character is received by the serial hardware device.</span></span> <span data-ttu-id="bd046-169">そのため、入力セマフォは初期カウントが 0 で作成されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-169">Because of this, the input semaphore is created with an initial count of zero.</span></span>

<span data-ttu-id="bd046-170">一方、出力セマフォは、シリアル ハードウェアの送信レジスタの可用性を示します。</span><span class="sxs-lookup"><span data-stu-id="bd046-170">Conversely, the output semaphore indicates the availability of the serial hardware transmit register.</span></span> <span data-ttu-id="bd046-171">送信レジスタが最初に使用可能であることを示すために値 1 で作成されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-171">It is created with a value of one to indicate the transmit register is initially available.</span></span>

<span data-ttu-id="bd046-172">初期化関数は、入力および出力通知用の低レベルの割り込みベクター ハンドラーをインストールする役割も担います。</span><span class="sxs-lookup"><span data-stu-id="bd046-172">The initialization function is also responsible for installing the low-level interrupt vector handlers for input and output notifications.</span></span> <span data-ttu-id="bd046-173">他の ThreadX 割り込みサービス ルーチンと同様に、低レベル ハンドラーでは、簡易ドライバーの ISR を呼び出す前に、\* **_tx_thread_context_save** _ を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd046-173">Like other ThreadX interrupt service routines, the low-level handler must call \***_tx_thread_context_save** _ before calling the simple driver ISR.</span></span> <span data-ttu-id="bd046-174">ドライバーの ISR に制御が戻ったら、低レベル ハンドラーで _\*_ _tx_thread_context_restore_\*\* を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd046-174">After the driver ISR returns, the low-level handler must call _\*_ _tx_thread_context_restore_\*\*.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd046-175">\*初期化は、他のドライバー関数の前に呼び出すことが重要です。</span><span class="sxs-lookup"><span data-stu-id="bd046-175">\*It is important that initialization is called before any of the other driver functions.</span></span> <span data-ttu-id="bd046-176">通常、ドライバーの初期化は ***tx_application_define*** から呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-176">Typically, driver initialization is called from ***tx_application_define***.</span></span>

```c
VOID tx_sdriver_initialize(VOID)
{
    /* Initialize the two counting semaphores used to control
    the simple driver I/O. */
    tx_semaphore_create(&tx_sdriver_input_semaphore,
                        "simple driver input semaphore", 0);
    tx_semaphore_create(&tx_sdriver_output_semaphore,
                        "simple driver output semaphore", 1);

    /* Setup interrupt vectors for input and output ISRs.
    The initial vector handling should call the ISRs
    defined in this file. */

    /* Configure serial device hardware for RX/TX interrupt
    generation, baud rate, stop bits, etc. */
}
```
<span data-ttu-id="bd046-177">**図 9. 簡易ドライバーの初期化**</span><span class="sxs-lookup"><span data-stu-id="bd046-177">**FIGURE 9. Simple Driver Initialization**</span></span>

### <a name="simple-driver-input"></a><span data-ttu-id="bd046-178">簡易ドライバーの入力</span><span class="sxs-lookup"><span data-stu-id="bd046-178">Simple Driver Input</span></span>

<span data-ttu-id="bd046-179">簡易ドライバーの入力は、入力セマフォを中心としています。</span><span class="sxs-lookup"><span data-stu-id="bd046-179">Input for the simple driver centers around the input semaphore.</span></span> <span data-ttu-id="bd046-180">シリアル デバイスの入力割り込みを受信すると、入力セマフォが設定されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-180">When a serial device input interrupt is received, the input semaphore is set.</span></span> <span data-ttu-id="bd046-181">1 つ以上のスレッドがドライバーからの文字を待機している場合、待機時間が最も長いスレッドが再開されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-181">If one or more threads are waiting for a character from the driver, the thread waiting the longest is resumed.</span></span> <span data-ttu-id="bd046-182">待機しているスレッドがない場合は、スレッドがドライバー入力関数を呼び出すまで、セマフォは単に設定されたままになります。</span><span class="sxs-lookup"><span data-stu-id="bd046-182">If no threads are waiting, the semaphore simply remains set until a thread calls the drive input function.</span></span>

<span data-ttu-id="bd046-183">簡易ドライバーの入力処理にはいくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="bd046-183">There are several limitations to the simple driver input handling.</span></span> <span data-ttu-id="bd046-184">最も重要なのは、入力文字が破棄される可能性があることです。</span><span class="sxs-lookup"><span data-stu-id="bd046-184">The most significant is the potential for dropping input characters.</span></span> <span data-ttu-id="bd046-185">この可能性があるのは、前の文字が処理される前に到着した入力文字をバッファーする機能がないためです。</span><span class="sxs-lookup"><span data-stu-id="bd046-185">This is possible because there is no ability to buffer input characters that arrive before the previous character is processed.</span></span> <span data-ttu-id="bd046-186">これは、入力文字バッファーを追加することで簡単に処理できます。</span><span class="sxs-lookup"><span data-stu-id="bd046-186">This is easily handled by adding an input character buffer.</span></span>

> [!NOTE]
> <span data-ttu-id="bd046-187">" ***tx_sdriver_input** _ _ 関数を呼び出すことができるのはスレッドだけです。*"</span><span class="sxs-lookup"><span data-stu-id="bd046-187">*Only threads are allowed to call the* ***tx_sdriver_input** _ _function.*</span></span>

<span data-ttu-id="bd046-188">図 10 は、簡易ドライバーの入力に関連するソース コードを示しています。</span><span class="sxs-lookup"><span data-stu-id="bd046-188">Figure 10 shows the source code associated with simple driver input.</span></span>

```c
UCHAR tx_sdriver_input(VOID)
{
  /* Determine if there is a character waiting. If not,
  suspend. */
  tx_semaphore_get(&tx_sdriver_input_semaphore,
  TX_WAIT_FOREVER;

  /* Return character from serial RX hardware register. */
  return(*serial_hardware_input_ptr);
}
  VOID tx_sdriver_input_ISR(VOID)
{
  /* See if an input character notification is pending. */
  if (!tx_sdriver_input_semaphore.tx_semaphore_count)
  {
    /* If not, notify thread of an input character. */
    tx_semaphore_put(&tx_sdriver_input_semaphore);
  }
}
```
<span data-ttu-id="bd046-189">**図 10. 簡易ドライバーの入力**</span><span class="sxs-lookup"><span data-stu-id="bd046-189">**FIGURE 10. Simple Driver Input**</span></span>

### <a name="simple-driver-output"></a><span data-ttu-id="bd046-190">簡易ドライバーの出力</span><span class="sxs-lookup"><span data-stu-id="bd046-190">Simple Driver Output</span></span>

<span data-ttu-id="bd046-191">出力処理では、出力セマフォを利用して、シリアル デバイスの送信レジスタが解放されたことを通知します。</span><span class="sxs-lookup"><span data-stu-id="bd046-191">Output processing utilizes the output semaphore to signal when the serial device's transmit register is free.</span></span> <span data-ttu-id="bd046-192">出力文字が実際にデバイスに書き込まれる前に、出力セマフォが取得されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-192">Before an output character is actually written to the device, the output semaphore is obtained.</span></span> <span data-ttu-id="bd046-193">これが使用できない場合は、前の送信がまだ完了していません。</span><span class="sxs-lookup"><span data-stu-id="bd046-193">If it is not available, the previous transmit is not yet complete.</span></span>

<span data-ttu-id="bd046-194">出力 ISR は、送信完了割り込みを処理する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="bd046-194">The output ISR is responsible for handling the transmit complete interrupt.</span></span> <span data-ttu-id="bd046-195">出力 ISR の処理では、出力セマフォを設定することによって別の文字の出力を可能にします。</span><span class="sxs-lookup"><span data-stu-id="bd046-195">Processing of the output ISR amounts to setting the output semaphore, thereby allowing output of another character.</span></span>

> [!NOTE]
> <span data-ttu-id="bd046-196">" ***tx_sdriver_output** _ _ 関数を呼び出すことができるのはスレッドだけです。*"</span><span class="sxs-lookup"><span data-stu-id="bd046-196">*Only threads are allowed to call the* ***tx_sdriver_output** _ _function.*</span></span>

<span data-ttu-id="bd046-197">図 11 は、簡易ドライバーの出力に関連するソース コードを示しています。</span><span class="sxs-lookup"><span data-stu-id="bd046-197">Figure 11 shows the source code associated with simple driver output.</span></span>

```c
VOID tx_sdriver_output(UCHAR alpha)
{
  /* Determine if the hardware is ready to transmit a
  character. If not, suspend until the previous output
  completes. */
  tx_semaphore_get(&tx_sdriver_output_semaphore,
                                          TX_WAIT_FOREVER);

  /* Send the character through the hardware. */
  *serial_hardware_output_ptr = alpha;
}
  
VOID tx_sdriver_output_ISR(VOID)
{
  /* Notify thread last character transmit is
  complete. */
  tx_semaphore_put(&tx_sdriver_output_semaphore);
}
```
<span data-ttu-id="bd046-198">**図 11. 簡易ドライバーの出力**</span><span class="sxs-lookup"><span data-stu-id="bd046-198">**FIGURE 11. Simple Driver Output**</span></span>

### <a name="simple-driver-shortcomings"></a><span data-ttu-id="bd046-199">簡易ドライバーの欠点</span><span class="sxs-lookup"><span data-stu-id="bd046-199">Simple Driver Shortcomings</span></span>

<span data-ttu-id="bd046-200">この簡易デバイス ドライバーの例は、ThreadX デバイス ドライバーの基本概念を示しています。</span><span class="sxs-lookup"><span data-stu-id="bd046-200">This simple device driver example illustrates the basic idea of a ThreadX device driver.</span></span> <span data-ttu-id="bd046-201">ただし、簡易デバイス ドライバーは、データ バッファリングやオーバーヘッドの問題に対処していないため、実際の ThreadX ドライバーを完全に表しているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="bd046-201">However, because the simple device driver does not address data buffering or any overhead issues, it does not fully represent real-world ThreadX drivers.</span></span> <span data-ttu-id="bd046-202">次のセクションでは、デバイス ドライバーに関連するより高度な問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="bd046-202">The following section describes some of the more advanced issues associated with device drivers.</span></span>

## <a name="advanced-driver-issues"></a><span data-ttu-id="bd046-203">ドライバーの高度な問題</span><span class="sxs-lookup"><span data-stu-id="bd046-203">Advanced Driver Issues</span></span>

<span data-ttu-id="bd046-204">前述のように、デバイス ドライバーには、アプリケーションに固有の要件があります。</span><span class="sxs-lookup"><span data-stu-id="bd046-204">As mentioned previously, device drivers have requirements as unique as their applications.</span></span> <span data-ttu-id="bd046-205">大量のデータ バッファリングを必要とするアプリケーションもあれば、デバイスの割り込みが高頻度で発生するため、最適化されたドライバー ISR を必要とするアプリケーションもあります。</span><span class="sxs-lookup"><span data-stu-id="bd046-205">Some applications may require an enormous amount of data buffering while another application may require optimized driver ISRs because of high-frequency device interrupts.</span></span>

### <a name="io-buffering"></a><span data-ttu-id="bd046-206">I/O バッファリング</span><span class="sxs-lookup"><span data-stu-id="bd046-206">I/O Buffering</span></span>

<span data-ttu-id="bd046-207">リアルタイム組み込みアプリケーションでのデータ バッファリングには、かなりの計画が必要です。</span><span class="sxs-lookup"><span data-stu-id="bd046-207">Data buffering in real-time embedded applications requires considerable planning.</span></span> <span data-ttu-id="bd046-208">設計の一部は、基になるハードウェア デバイスによって決まります。</span><span class="sxs-lookup"><span data-stu-id="bd046-208">Some of the design is dictated by the underlying hardware device.</span></span> <span data-ttu-id="bd046-209">デバイスで基本的なバイト I/O が提供される場合は、単純な循環バッファーが適していると考えられます。</span><span class="sxs-lookup"><span data-stu-id="bd046-209">If the device provides basic byte I/O, a simple circular buffer is probably in order.</span></span> <span data-ttu-id="bd046-210">ただし、デバイスでブロック、DMA、またはパケット I/O が提供される場合は、バッファー管理スキームが必要になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bd046-210">However, if the device provides block, DMA, or packet I/O, a buffer management scheme is probably warranted.</span></span>

### <a name="circular-byte-buffers"></a><span data-ttu-id="bd046-211">循環バイト バッファー</span><span class="sxs-lookup"><span data-stu-id="bd046-211">Circular Byte Buffers</span></span>

<span data-ttu-id="bd046-212">通常、循環バイト バッファーは、UART のような単純なシリアル ハードウェア デバイスを管理するドライバーで使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-212">Circular byte buffers are typically used in drivers that manage a simple serial hardware device like a UART.</span></span> <span data-ttu-id="bd046-213">このような場合、2 つの循環バッファー (1 つは入力用、もう 1 つは出力用) が最もよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-213">Two circular buffers are most often used in such situations—one for input and one for output.</span></span>

<span data-ttu-id="bd046-214">各循環バイト バッファーは、バイト メモリ領域 (通常は **UCHAR** の配列)、読み取りポインター、書き込みポインターで構成されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-214">Each circular byte buffer is comprised of a byte memory area (typically an array of **UCHAR** s), a read pointer, and a write pointer.</span></span> <span data-ttu-id="bd046-215">読み取りポインターと書き込みポインターがバッファー内の同じメモリ位置を参照している場合、バッファーは空と見なされます。</span><span class="sxs-lookup"><span data-stu-id="bd046-215">A buffer is considered empty when the read pointer and the write pointers reference the same memory location in the buffer.</span></span> <span data-ttu-id="bd046-216">ドライバーの初期化により、読み取りと書き込み両方のバッファーのポインターがバッファーの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-216">Driver initialization sets both the read and write buffer pointers to the beginning address of the buffer.</span></span>

### <a name="circular-buffer-input"></a><span data-ttu-id="bd046-217">循環バッファー入力</span><span class="sxs-lookup"><span data-stu-id="bd046-217">Circular Buffer Input</span></span>

<span data-ttu-id="bd046-218">入力バッファーは、アプリケーションの準備が整う前に到着した文字を保持するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-218">The input buffer is used to hold characters that arrive before the application is ready for them.</span></span> <span data-ttu-id="bd046-219">(通常は割り込みサービス ルーチンで) 入力文字を受信すると、その新しい文字がハードウェア デバイスから取得され、書き込みポインターが指す位置の入力バッファーに配置されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-219">When an input character is received (usually in an interrupt service routine), the new character is retrieved from the hardware device and placed into the input buffer at the location pointed to by the write pointer.</span></span> <span data-ttu-id="bd046-220">その後、書き込みポインターはバッファー内の次の位置に進められます。</span><span class="sxs-lookup"><span data-stu-id="bd046-220">The write pointer is then advanced to the next position in the buffer.</span></span> <span data-ttu-id="bd046-221">次の位置がバッファーの末尾を越える場合、書き込みポインターはバッファーの先頭に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-221">If the next position is past the end of the buffer, the write pointer is set to the beginning of the buffer.</span></span> <span data-ttu-id="bd046-222">新しい書き込みポインターが読み取りポインターと同じである場合、書き込みポインターの前進をキャンセルすることによって、キューの満杯状態が処理されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-222">The queue full condition is handled by canceling the write pointer advancement if the new write pointer is the same as the read pointer.</span></span>

<span data-ttu-id="bd046-223">ドライバーに対するアプリケーションの入力バイト要求では、まず、入力バッファーの読み取りおよび書き込みポインターが調べられます。</span><span class="sxs-lookup"><span data-stu-id="bd046-223">Application input byte requests to the driver first examine the read and write pointers of the input buffer.</span></span> <span data-ttu-id="bd046-224">読み取りと書き込みのポインターが同一の場合、バッファーは空です。</span><span class="sxs-lookup"><span data-stu-id="bd046-224">If the read and write pointers are identical, the buffer is empty.</span></span> <span data-ttu-id="bd046-225">読み取りポインターが同じでない場合は、読み取りポインターが指すバイトが入力バッファーからコピーされ、読み取りポインターが次のバッファー位置に進められます。</span><span class="sxs-lookup"><span data-stu-id="bd046-225">Otherwise, if the read pointer is not the same, the byte pointed to by the read pointer is copied from the input buffer and the read pointer is advanced to the next buffer location.</span></span> <span data-ttu-id="bd046-226">新しい読み取りポインターがバッファーの末尾を越える場合は、先頭にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="bd046-226">If the new read pointer is past the end of the buffer, it is reset to the beginning.</span></span> <span data-ttu-id="bd046-227">図 12 は、循環入力バッファーのロジックを示しています。</span><span class="sxs-lookup"><span data-stu-id="bd046-227">Figure 12 shows the logic for the circular input buffer.</span></span>

```c
UCHAR   tx_input_buffer[MAX_SIZE];
UCHAR   tx_input_write_ptr;
UCHAR   tx_input_read_ptr;

/* Initialization. */
tx_input_write_ptr =    &tx_input_buffer[0];
tx_input_read_ptr =     &tx_input_buffer[0];

/* Input byte ISR... UCHAR alpha has character from device. */
save_ptr = tx_input_write_ptr;
*tx_input_write_ptr++ = alpha;
if (tx_input_write_ptr > &tx_input_buffer[MAX_SIZE-1])
    tx_input_write_ptr = &tx_input_buffer[0]; /* Wrap */
if (tx_input_write_ptr == tx_input_read_ptr)
    tx_input_write_ptr = save_ptr; /* Buffer full */

/* Retrieve input byte from buffer... */
if (tx_input_read_ptr != tx_input_write_ptr)
{
  alpha = *tx_input_read_ptr++;
  if (tx_input_read_ptr > &tx_input_buffer[MAX_SIZE-1])
      tx_input_read_ptr = &tx_input_buffer[0];
}
```
<span data-ttu-id="bd046-228">**図 12. 循環入力バッファーのロジック**</span><span class="sxs-lookup"><span data-stu-id="bd046-228">**FIGURE 12. Logic for Circular Input Buffer**</span></span>

> [!NOTE]
> <span data-ttu-id="bd046-229">\*信頼性の高い動作を実現するために、入力と出力の両方の循環バッファーの読み取りおよび書き込みポインターを操作するときに、割り込みをロックアウトすることが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="bd046-229">\*For reliable operation, it may be necessary to lockout interrupts when manipulating the read and write pointers of both the input and output circular buffers.</span></span> *

### <a name="circular-output-buffer"></a><span data-ttu-id="bd046-230">循環出力バッファー</span><span class="sxs-lookup"><span data-stu-id="bd046-230">Circular Output Buffer</span></span>

<span data-ttu-id="bd046-231">出力バッファーは、ハードウェア デバイスが前のバイトの送信を終了する前に、出力用に到着した文字を保持するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-231">The output buffer is used to hold characters that have arrived for output before the hardware device finished sending the previous byte.</span></span> <span data-ttu-id="bd046-232">出力バッファー処理は入力バッファー処理と似ていますが、送信完了割り込み処理によって出力読み取りポインターが操作され、アプリケーションの出力要求で出力書き込みポインターが利用される点が異なります。</span><span class="sxs-lookup"><span data-stu-id="bd046-232">Output buffer processing is similar to input buffer processing, except the transmit complete interrupt processing manipulates the output read pointer, while the application output request utilizes the output write pointer.</span></span>
<span data-ttu-id="bd046-233">それ以外の点では、出力バッファー処理は同じです。</span><span class="sxs-lookup"><span data-stu-id="bd046-233">Otherwise, the output buffer processing is the same.</span></span> <span data-ttu-id="bd046-234">図 13 は、循環出力バッファーのロジックを示しています。</span><span class="sxs-lookup"><span data-stu-id="bd046-234">Figure 13 shows the logic for the circular output buffer.</span></span>

```c
UCHAR   tx_output_buffer[MAX_SIZE];
UCHAR   tx_output_write_ptr;
UCHAR   tx_output_read_ptr;

/* Initialization. */
tx_output_write_ptr = &tx_output_buffer[0];
tx_output_read_ptr = &tx_output_buffer[0];

/* Transmit complete ISR... Device ready to send. */
if (tx_output_read_ptr != tx_output_write_ptr)
{
  *device_reg = *tx_output_read_ptr++;
  if (tx_output_read_reg > &tx_output_buffer[MAX_SIZE-1])
      tx_output_read_ptr = &tx_output_buffer[0];
}

/* Output byte driver service. If device busy, buffer! */
save_ptr = tx_output_write_ptr;
*tx_output_write_ptr++ = alpha;
if (tx_output_write_ptr > &tx_output_buffer[MAX_SIZE-1])
    tx_output_write_ptr = &tx_output_buffer[0]; /* Wrap */
if (tx_output_write_ptr == tx_output_read_ptr)
    tx_output_write_ptr = save_ptr; /* Buffer full! */
```
<span data-ttu-id="bd046-235">**図 13. 循環出力バッファーのロジック**</span><span class="sxs-lookup"><span data-stu-id="bd046-235">**FIGURE 13. Logic for Circular Output Buffer**</span></span>

### <a name="buffer-io-management"></a><span data-ttu-id="bd046-236">バッファー I/O の管理</span><span class="sxs-lookup"><span data-stu-id="bd046-236">Buffer I/O Management</span></span>

<span data-ttu-id="bd046-237">組み込みマイクロプロセッサのパフォーマンスを向上させるために、多くの周辺機器では、ソフトウェアによって提供されるバッファーを使用してデータが送受信されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-237">To improve the performance of embedded microprocessors, many peripheral device devices transmit and receive data with buffers supplied by software.</span></span> <span data-ttu-id="bd046-238">実装によっては、データの個々のパケットを送受信するために複数のバッファーが使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="bd046-238">In some implementations, multiple buffers may be used to transmit or receive individual packets of data.</span></span>

<span data-ttu-id="bd046-239">I/O バッファーのサイズと場所は、アプリケーションやドライバー ソフトウェアによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-239">The size and location of I/O buffers is determined by the application and/or driver software.</span></span> <span data-ttu-id="bd046-240">通常、バッファーはサイズが固定されており、ThreadX ブロック メモリ プール内で管理されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-240">Typically, buffers are fixed in size and managed within a ThreadX block memory pool.</span></span> <span data-ttu-id="bd046-241">図 14 は、一般的な I/O バッファーと、それらの割り当てを管理する ThreadX ブロック メモリ プールを示しています。</span><span class="sxs-lookup"><span data-stu-id="bd046-241">Figure 14 describes a typical I/O buffer and a ThreadX block memory pool that manages their allocation.</span></span>

```c
typedef struct TX_IO_BUFFER_STRUCT
{
      struct TX_IO_BUFFER_STRUCT *tx_next_packet;
      struct TX_IO_BUFFER_STRUCT *tx_next_buffer;
      UCHAR tx_buffer_area[TX_MAX_BUFFER_SIZE];
} TX_IO_BUFFER;

TX_BLOCK_POOL tx_io_block_pool;

/* Create a pool of I/O buffers. Assume that the pointer
"free_memory_ptr"points to an available memory area that
is 64 KBytes in size. */
tx_block_pool_create(&tx_io_block_pool,
                  "Sample IO Driver Buffer Pool",
                  free_memory_ptr, 0x10000,
                  sizeof(TX_IO_BUFFER));
```

<span data-ttu-id="bd046-242">**図 14. I/O バッファー**</span><span class="sxs-lookup"><span data-stu-id="bd046-242">**FIGURE 14. I/O Buffer**</span></span>

### <a name="tx_io_buffer"></a><span data-ttu-id="bd046-243">TX_IO_BUFFER</span><span class="sxs-lookup"><span data-stu-id="bd046-243">TX_IO_BUFFER</span></span>

<span data-ttu-id="bd046-244">typedef TX_IO_BUFFER は、2 つのポインターで構成されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-244">The typedef TX_IO_BUFFER consists of two pointers.</span></span> <span data-ttu-id="bd046-245">**tx_next_packet** ポインターは、入力または出力リストで複数のパケットをリンクするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-245">The **tx_next_packet** pointer is used to link multiple packets on either the input or output list.</span></span> <span data-ttu-id="bd046-246">**tx_next_buffer** ポインターは、デバイスからのデータの個々のパケットを構成するバッファーを一緒にリンクするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-246">The **tx_next_buffer** pointer is used to link together buffers that make up an individual packet of data from the device.</span></span> <span data-ttu-id="bd046-247">バッファーがプールから割り当てられるときに、これらのポインターはどちらも NULL に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-247">Both of these pointers are set to NULL when the buffer is allocated from the pool.</span></span> <span data-ttu-id="bd046-248">さらに、一部のデバイスでは、実際にデータを格納するバッファー領域の量を示す別のフィールドが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bd046-248">In addition, some devices may require another field to indicate how much of the buffer area actually contains data.</span></span>

### <a name="buffered-io-advantage"></a><span data-ttu-id="bd046-249">バッファー I/O の利点</span><span class="sxs-lookup"><span data-stu-id="bd046-249">Buffered I/O Advantage</span></span>

<span data-ttu-id="bd046-250">バッファー I/O スキームの利点は何でしょうか。</span><span class="sxs-lookup"><span data-stu-id="bd046-250">What are the advantages of a buffer I/O scheme?</span></span> <span data-ttu-id="bd046-251">最大の利点は、デバイスのレジスタとアプリケーションのメモリの間でデータがコピーされないことです。</span><span class="sxs-lookup"><span data-stu-id="bd046-251">The biggest advantage is that data is not copied between the device registers and the application's memory.</span></span> <span data-ttu-id="bd046-252">代わりに、ドライバーによって一連のバッファー ポインターがデバイスに提供されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-252">Instead, the driver provides the device with a series of buffer pointers.</span></span> <span data-ttu-id="bd046-253">物理デバイス I/O では、指定されたバッファー メモリを直接利用します。</span><span class="sxs-lookup"><span data-stu-id="bd046-253">Physical device I/O utilizes the supplied buffer memory directly.</span></span>

<span data-ttu-id="bd046-254">プロセッサを使用して情報の入力または出力パケットをコピーすることは非常にコストがかかるので、高スループットの I/O 状況では避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd046-254">Using the processor to copy input or output packets of information is extremely costly and should be avoided in any high throughput I/O situation.</span></span>

<span data-ttu-id="bd046-255">バッファー I/O アプローチのもう 1 つの利点は、入力と出力のリストに満杯状態がないことです。</span><span class="sxs-lookup"><span data-stu-id="bd046-255">Another advantage to the buffered I/O approach is that the input and output lists do not have full conditions.</span></span> <span data-ttu-id="bd046-256">どちらのリストにも、使用可能なすべてのバッファーをいつでも配置できます。</span><span class="sxs-lookup"><span data-stu-id="bd046-256">All of the available buffers can be on either list at any one time.</span></span> <span data-ttu-id="bd046-257">これは、この章で前述した単純なバイト循環バッファーとは対照的です。</span><span class="sxs-lookup"><span data-stu-id="bd046-257">This contrasts with the simple byte circular buffers presented earlier in the chapter.</span></span> <span data-ttu-id="bd046-258">それぞれ、コンパイル時に決定されたサイズに固定されていました。</span><span class="sxs-lookup"><span data-stu-id="bd046-258">Each had a fixed size determined at compilation.</span></span>

### <a name="buffered-driver-responsibilities"></a><span data-ttu-id="bd046-259">バッファー型ドライバーの役割</span><span class="sxs-lookup"><span data-stu-id="bd046-259">Buffered Driver Responsibilities</span></span>

<span data-ttu-id="bd046-260">バッファー型デバイス ドライバーは、I/O バッファーのリンク リストの管理にのみ関与します。</span><span class="sxs-lookup"><span data-stu-id="bd046-260">Buffered device drivers are only concerned with managing linked lists of I/O buffers.</span></span> <span data-ttu-id="bd046-261">入力バッファー リストは、アプリケーション ソフトウェアの準備が整う前に受信したパケット用に保持されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-261">An input buffer list is maintained for packets that are received before the application software is ready.</span></span> <span data-ttu-id="bd046-262">一方、出力バッファー リストは、ハードウェア デバイスが処理できるようになる前に送られてくるパケット用に保持されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-262">Conversely, an output buffer list is maintained for packets being sent faster than the hardware device can handle them.</span></span> <span data-ttu-id="bd046-263">図 15 は、データ パケットと各パケットを構成するバッファーの単純な入力および出力リンク リストを示しています。</span><span class="sxs-lookup"><span data-stu-id="bd046-263">Figure 15 shows simple input and output linked lists of data packets and the buffer(s) that make up each packet.</span></span>

<span data-ttu-id="bd046-264">**入力リスト**</span><span class="sxs-lookup"><span data-stu-id="bd046-264">**Input List**</span></span>

![入力リスト](./media/user-guide/input-list.png)

<span data-ttu-id="bd046-266">**出力リスト**</span><span class="sxs-lookup"><span data-stu-id="bd046-266">**Output List**</span></span>

![出力リスト](./media/user-guide/output-list.png)

<span data-ttu-id="bd046-268">**図 15. 入力と出力のリスト**</span><span class="sxs-lookup"><span data-stu-id="bd046-268">**FIGURE 15. Input-Output Lists**</span></span>

<span data-ttu-id="bd046-269">アプリケーションは、同じ I/O バッファーを使用するバッファー型ドライバーとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="bd046-269">Applications interface with buffered drivers with the same I/O buffers.</span></span> <span data-ttu-id="bd046-270">送信時に、アプリケーション ソフトウェアは、送信する 1 つ以上のバッファーをドライバーに提供します。</span><span class="sxs-lookup"><span data-stu-id="bd046-270">On transmit, application software provides the driver with one or more buffers to transmit.</span></span> <span data-ttu-id="bd046-271">アプリケーション ソフトウェアが入力を要求すると、ドライバーは I/O バッファーに入力データを返します。</span><span class="sxs-lookup"><span data-stu-id="bd046-271">When the application software requests input, the driver returns the input data in I/O buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="bd046-272">"*一部のアプリケーションでは、空きバッファーをドライバーからの入力バッファーと交換することをアプリケーションに要求する、ドライバー入力インターフェイスを構築すると役立つ場合があります。これにより、ドライバーの内部でのバッファー割り当て処理が軽減される可能性があります。* "</span><span class="sxs-lookup"><span data-stu-id="bd046-272">*In some applications, it may be useful to build a driver input interface that requires the application to exchange a free buffer for an input buffer from the driver. This might alleviate some buffer allocation processing inside of the driver.*</span></span>

### <a name="interrupt-management"></a><span data-ttu-id="bd046-273">割り込み管理</span><span class="sxs-lookup"><span data-stu-id="bd046-273">Interrupt Management</span></span>

<span data-ttu-id="bd046-274">一部のアプリケーションでは、デバイスの割り込み頻度により、ISR を C で記述したり、各割り込みで ThreadX と対話したりすることが妨げられる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bd046-274">In some applications, the device interrupt frequency may prohibit writing the ISR in C or to interact with ThreadX on each interrupt.</span></span> <span data-ttu-id="bd046-275">たとえば、中断されたコンテキストの保存と復元に 25 マイクロ秒かかる場合、割り込み頻度が 50 マイクロ秒であるとすると、コンテキストの完全な保存を実行することはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="bd046-275">For example, if it takes 25us to save and restore the interrupted context, it would not be advisable to perform a full context save if the interrupt frequency was 50us.</span></span> <span data-ttu-id="bd046-276">このような場合は、アセンブリ言語の小さな ISR を使用して、デバイスの割り込みの大半を処理します。</span><span class="sxs-lookup"><span data-stu-id="bd046-276">In such cases, a small assembly language ISR is used to handle most of the device interrupts.</span></span> <span data-ttu-id="bd046-277">この低オーバーヘッドの ISR は、必要な場合にのみ ThreadX と対話します。</span><span class="sxs-lookup"><span data-stu-id="bd046-277">This low-overhead ISR would only interact with ThreadX when necessary.</span></span>

<span data-ttu-id="bd046-278">第 3 章の最後にある割り込み管理の説明にも同様の説明があります。</span><span class="sxs-lookup"><span data-stu-id="bd046-278">A similar discussion can be found in the interrupt management discussion at the end of Chapter 3.</span></span>

### <a name="thread-suspension"></a><span data-ttu-id="bd046-279">スレッドの中断</span><span class="sxs-lookup"><span data-stu-id="bd046-279">Thread Suspension</span></span>

<span data-ttu-id="bd046-280">この章で前述した簡易ドライバーの例では、文字が使用できない場合に、入力サービスの呼び出し元が一時停止されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-280">In the simple driver example presented earlier in this chapter, the caller of the input service suspends if a character is not available.</span></span> <span data-ttu-id="bd046-281">アプリケーションによっては、これを許容できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="bd046-281">In some applications, this might not be acceptable.</span></span>

<span data-ttu-id="bd046-282">たとえば、ドライバーからの入力を処理する役割を担うスレッドにほかの役割もある場合、ドライバーの入力だけで一時停止しても、うまく機能しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bd046-282">For example, if the thread responsible for processing input from a driver also has other duties, suspending on just the driver input is probably not going to work.</span></span> <span data-ttu-id="bd046-283">代わりに、スレッドに対する他の処理要求と同様に処理を要求するように、ドライバーをカスタマイズする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd046-283">Instead, the driver needs to be customized to request processing similar to the way other processing requests are made to the thread.</span></span>

<span data-ttu-id="bd046-284">ほとんどの場合、入力バッファーはリンク リストに配置され、入力イベント メッセージがスレッドの入力キューに送信されます。</span><span class="sxs-lookup"><span data-stu-id="bd046-284">In most cases, the input buffer is placed on a linked list and an input event message is sent to the thread's input queue.</span></span>
