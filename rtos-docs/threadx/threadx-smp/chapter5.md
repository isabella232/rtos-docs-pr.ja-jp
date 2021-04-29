---
title: 第 5 章 - Azure RTOS ThreadX SMP のデバイス ドライバー
description: この章では、Azure RTOS ThreadX SMP のデバイス ドライバーについて説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: acfb54a25cc8bc27b7d0aaeff48956529d90c9e1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812833"
---
# <a name="chapter-5---device-drivers-for-azure-rtos-threadx-smp"></a><span data-ttu-id="9ece4-103">第 5 章 - Azure RTOS ThreadX SMP のデバイス ドライバー</span><span class="sxs-lookup"><span data-stu-id="9ece4-103">Chapter 5 - Device Drivers for Azure RTOS ThreadX SMP</span></span>

<span data-ttu-id="9ece4-104">この章では、Azure RTOS ThreadX SMP のデバイス ドライバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9ece4-104">This chapter contains a description of device drivers for Azure RTOS ThreadX SMP.</span></span> <span data-ttu-id="9ece4-105">この章に記載されている情報は、アプリケーション固有のドライバーを作成する開発者を支援することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="9ece4-105">The information presented in this chapter is designed to help developers write application specific drivers.</span></span> 

## <a name="device-driver-introduction"></a><span data-ttu-id="9ece4-106">デバイス ドライバーの概要</span><span class="sxs-lookup"><span data-stu-id="9ece4-106">Device Driver Introduction</span></span>

<span data-ttu-id="9ece4-107">外部環境との通信は、ほとんどの組み込みアプリケーションの重要な構成要素です。</span><span class="sxs-lookup"><span data-stu-id="9ece4-107">Communication with the external environment is an important component of most embedded applications.</span></span> <span data-ttu-id="9ece4-108">この通信は、組み込みアプリケーション ソフトウェアがアクセス可能なハードウェア デバイスを介して行われます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-108">This communication is accomplished through hardware devices that are accessible to the embedded application software.</span></span> <span data-ttu-id="9ece4-109">このようなデバイスを管理する役割を担うソフトウェア コンポーネントは、一般に "*デバイス ドライバー*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-109">The software components responsible for managing such devices are commonly called *Device Drivers*.</span></span>

<span data-ttu-id="9ece4-110">組み込みのリアルタイム システムのデバイス ドライバーは、本質的にアプリケーションに依存しています。</span><span class="sxs-lookup"><span data-stu-id="9ece4-110">Device drivers in embedded, real-time systems are inherently application dependent.</span></span> <span data-ttu-id="9ece4-111">これには 2 つの主な理由があります。ターゲット ハードウェアが多種多様であることと、リアルタイム アプリケーションに課せられるパフォーマンス要件も同様に広範であることです。</span><span class="sxs-lookup"><span data-stu-id="9ece4-111">This is true for two principal reasons: the vast diversity of target hardware and the equally vast performance requirements imposed on real-time applications.</span></span> <span data-ttu-id="9ece4-112">そのため、すべてのアプリケーションの要件を満たすことができる共通のドライバー セットを提供するのは実質的に不可能です。</span><span class="sxs-lookup"><span data-stu-id="9ece4-112">Because of this, it is virtually impossible to provide a common set of drivers that will meet the requirements of every application.</span></span> <span data-ttu-id="9ece4-113">これらの理由から、この章の情報は、ユーザーが "*既製*" の ThreadX SMP デバイス ドライバーをカスタマイズし、独自のドライバーを作成できるよう支援することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="9ece4-113">For these reasons, the information in this chapter is designed to help users customize *off-the-shelf* ThreadX SMP device drivers and write their own specific drivers.</span></span>

## <a name="driver-functions"></a><span data-ttu-id="9ece4-114">ドライバーの機能</span><span class="sxs-lookup"><span data-stu-id="9ece4-114">Driver Functions</span></span>

<span data-ttu-id="9ece4-115">ThreadX SMP デバイス ドライバーは、次の 8 つの基本的な機能領域で構成されています。</span><span class="sxs-lookup"><span data-stu-id="9ece4-115">ThreadX SMP device drivers are composed of eight basic functional areas, as follows:</span></span>

- <span data-ttu-id="9ece4-116">**ドライバーの初期化**</span><span class="sxs-lookup"><span data-stu-id="9ece4-116">**Driver Initialization**</span></span>
- <span data-ttu-id="9ece4-117">**ドライバー制御**</span><span class="sxs-lookup"><span data-stu-id="9ece4-117">**Driver Control**</span></span>
- <span data-ttu-id="9ece4-118">**ドライバー アクセス**</span><span class="sxs-lookup"><span data-stu-id="9ece4-118">**Driver Access**</span></span>
- <span data-ttu-id="9ece4-119">**ドライバーの入力**</span><span class="sxs-lookup"><span data-stu-id="9ece4-119">**Driver Input**</span></span>
- <span data-ttu-id="9ece4-120">**ドライバーの出力**</span><span class="sxs-lookup"><span data-stu-id="9ece4-120">**Driver Output**</span></span>
- <span data-ttu-id="9ece4-121">**ドライバーの割り込み**</span><span class="sxs-lookup"><span data-stu-id="9ece4-121">**Driver Interrupts**</span></span>
- <span data-ttu-id="9ece4-122">**ドライバーの状態**</span><span class="sxs-lookup"><span data-stu-id="9ece4-122">**Driver Status**</span></span>
- <span data-ttu-id="9ece4-123">**ドライバーの終了**</span><span class="sxs-lookup"><span data-stu-id="9ece4-123">**Driver Termination**</span></span>

<span data-ttu-id="9ece4-124">初期化を除き、ドライバーの各機能領域は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9ece4-124">With the exception of initialization, each driver functional area is optional.</span></span> <span data-ttu-id="9ece4-125">さらに、各領域での正確な処理はデバイス ドライバーに固有です。</span><span class="sxs-lookup"><span data-stu-id="9ece4-125">Furthermore, the exact processing in each area is specific to the device driver.</span></span>

### <a name="driver-initialization"></a><span data-ttu-id="9ece4-126">ドライバーの初期化</span><span class="sxs-lookup"><span data-stu-id="9ece4-126">Driver Initialization</span></span> 
<span data-ttu-id="9ece4-127">この機能領域は、実際のハードウェア デバイスとドライバーの内部データ構造の初期化を担当します。</span><span class="sxs-lookup"><span data-stu-id="9ece4-127">This functional area is responsible for initialization of the actual hardware device and the internal data structures of the driver.</span></span> <span data-ttu-id="9ece4-128">初期化が完了するまで、他のドライバー サービスを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="9ece4-128">Calling other driver services is not allowed until initialization is complete.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ece4-129">ドライバーの初期化関数コンポーネントは、通常、**tx_application_define** 関数または初期化スレッドから呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-129">The driver’s initialization function component is typically called from the **tx_application_define** function or from an initialization thread.</span></span>

### <a name="driver-control"></a><span data-ttu-id="9ece4-130">ドライバー制御</span><span class="sxs-lookup"><span data-stu-id="9ece4-130">Driver Control</span></span> 
<span data-ttu-id="9ece4-131">ドライバーが初期化され、操作の準備が整うと、この機能領域が実行時の制御を担当します。</span><span class="sxs-lookup"><span data-stu-id="9ece4-131">After the driver is initialized and ready for operation, this functional area is responsible for run-time control.</span></span> <span data-ttu-id="9ece4-132">通常、実行時の制御は、基になるハードウェア デバイスの変更で構成されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-132">Typically, run-time control consists of making changes to the underlying hardware device.</span></span> <span data-ttu-id="9ece4-133">例として、シリアル デバイスのボー レートの変更や、ディスク上の新しいセクターのシークが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-133">Examples include changing the baud rate of a serial device or seeking a new sector on a disk.</span></span>

### <a name="driver-access"></a><span data-ttu-id="9ece4-134">ドライバー アクセス</span><span class="sxs-lookup"><span data-stu-id="9ece4-134">Driver Access</span></span> 
<span data-ttu-id="9ece4-135">一部のデバイス ドライバーは、1 つのアプリケーション スレッドからのみ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-135">Some device drivers are called only from a single application thread.</span></span> <span data-ttu-id="9ece4-136">このような場合、この機能領域は不要です。</span><span class="sxs-lookup"><span data-stu-id="9ece4-136">In such cases, this functional area is not needed.</span></span> <span data-ttu-id="9ece4-137">ただし、複数のスレッドがドライバーに同時にアクセスする必要があるアプリケーションでは、デバイス ドライバーに割り当ておよび解放機能を追加して、それらの相互作用を制御する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-137">However, in applications where multiple threads need simultaneous driver access, their interaction must be controlled by adding assign/ release facilities in the device driver.</span></span> <span data-ttu-id="9ece4-138">代わりに、アプリケーションでセマフォを使用してドライバー アクセスを制御し、ドライバー内の余分なオーバーヘッドや複雑さを回避することもできます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-138">Alternatively, the application may use a semaphore to control driver access and avoid extra overhead and complication inside the driver.</span></span> 

### <a name="driver-input"></a><span data-ttu-id="9ece4-139">ドライバーの入力</span><span class="sxs-lookup"><span data-stu-id="9ece4-139">Driver Input</span></span> 
<span data-ttu-id="9ece4-140">この機能領域は、すべてのデバイス入力を担当します。</span><span class="sxs-lookup"><span data-stu-id="9ece4-140">This functional area is responsible for all device input.</span></span> <span data-ttu-id="9ece4-141">ドライバーの入力に関連する主な問題には、通常、入力をバッファーする方法と、スレッドがその入力を待機する方法が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-141">The principal issues associated with driver input usually involve how the input is buffered and how threads wait for such input.</span></span> 

### <a name="driver-output"></a><span data-ttu-id="9ece4-142">ドライバーの出力</span><span class="sxs-lookup"><span data-stu-id="9ece4-142">Driver Output</span></span> 
<span data-ttu-id="9ece4-143">この機能領域は、すべてのデバイス出力を担当します。</span><span class="sxs-lookup"><span data-stu-id="9ece4-143">This functional area is responsible for all device output.</span></span> <span data-ttu-id="9ece4-144">ドライバーの出力に関連する主な問題には、通常、出力をバッファーする方法と、スレッドが出力の実行を待機する方法が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-144">The principal issues associated with driver output usually involve how the output is buffered and how threads wait to perform output.</span></span> 

### <a name="driver-interrupts"></a><span data-ttu-id="9ece4-145">ドライバーの割り込み</span><span class="sxs-lookup"><span data-stu-id="9ece4-145">Driver Interrupts</span></span> 
<span data-ttu-id="9ece4-146">ほとんどのリアルタイム システムでは、デバイスの入力、出力、制御、エラーの各イベントをドライバーに通知するために、ハードウェア割り込みを利用します。</span><span class="sxs-lookup"><span data-stu-id="9ece4-146">Most real-time systems rely on hardware interrupts to notify the driver of device input, output, control, and error events.</span></span> <span data-ttu-id="9ece4-147">割り込みにより、このような外部イベントに対する応答時間が保証されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-147">Interrupts provide a guaranteed response time to such external events.</span></span> <span data-ttu-id="9ece4-148">割り込みの代わりに、ドライバー ソフトウェアで外部ハードウェアを定期的にチェックして、このようなイベントの有無を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-148">Instead of interrupts, the driver software may periodically check the external hardware for such events.</span></span> <span data-ttu-id="9ece4-149">この手法は "*ポーリング*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-149">This technique is called *polling*.</span></span> <span data-ttu-id="9ece4-150">割り込みに比べてリアルタイム性は劣りますが、リアルタイム性の低いアプリケーションではポーリングが効果的である場合もあります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-150">It is less real-time than interrupts, but polling may make sense for some less real-time applications.</span></span> 

### <a name="driver-status"></a><span data-ttu-id="9ece4-151">ドライバーの状態</span><span class="sxs-lookup"><span data-stu-id="9ece4-151">Driver Status</span></span> 
<span data-ttu-id="9ece4-152">この機能領域は、ドライバー操作に関連する実行時の状態と統計情報を提供する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="9ece4-152">This function area is responsible for providing runtime status and statistics associated with the driver operation.</span></span> <span data-ttu-id="9ece4-153">この機能領域によって管理される情報には、通常、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-153">Information managed by this function area typically includes the following:</span></span> 
- <span data-ttu-id="9ece4-154">デバイスの現在の状態</span><span class="sxs-lookup"><span data-stu-id="9ece4-154">Current device status</span></span>
- <span data-ttu-id="9ece4-155">入力バイト数</span><span class="sxs-lookup"><span data-stu-id="9ece4-155">Input bytes</span></span>
- <span data-ttu-id="9ece4-156">出力バイト数</span><span class="sxs-lookup"><span data-stu-id="9ece4-156">Output bytes</span></span>
- <span data-ttu-id="9ece4-157">デバイスのエラー数</span><span class="sxs-lookup"><span data-stu-id="9ece4-157">Device error counts</span></span>

### <a name="driver-termination"></a><span data-ttu-id="9ece4-158">ドライバーの終了</span><span class="sxs-lookup"><span data-stu-id="9ece4-158">Driver Termination</span></span> 
<span data-ttu-id="9ece4-159">この機能領域は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9ece4-159">This functional area is optional.</span></span> <span data-ttu-id="9ece4-160">ドライバーや物理ハードウェア デバイスをシャットダウンする必要がある場合にのみ必要となります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-160">It is only required if the driver and/or the physical hardware device need to be shut down.</span></span> <span data-ttu-id="9ece4-161">終了後は、再初期化されるまでドライバーを再度呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="9ece4-161">After being terminated, the driver must not be called again until it is re-initialized.</span></span> 

## <a name="simple-driver-example"></a><span data-ttu-id="9ece4-162">簡易ドライバーの例</span><span class="sxs-lookup"><span data-stu-id="9ece4-162">Simple Driver Example</span></span>

<span data-ttu-id="9ece4-163">デバイス ドライバーを記述するための最良の方法は例を使うことです。</span><span class="sxs-lookup"><span data-stu-id="9ece4-163">An example is the best way to describe a device driver.</span></span> <span data-ttu-id="9ece4-164">この例では、構成レジスタ、入力レジスタ、出力レジスタを備えた単純なシリアル ハードウェア デバイスがドライバーによって想定されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-164">In this example, the driver assumes a simple serial hardware device with a configuration register, an input register, and an output register.</span></span> <span data-ttu-id="9ece4-165">この簡易ドライバーの例では、初期化、入力、出力、割り込みの各機能領域が説明されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-165">This simple driver example illustrates the initialization, input, output, and interrupt functional areas.</span></span>

### <a name="simple-driver-initialization"></a><span data-ttu-id="9ece4-166">簡易ドライバーの初期化</span><span class="sxs-lookup"><span data-stu-id="9ece4-166">Simple Driver Initialization</span></span> 
<span data-ttu-id="9ece4-167">簡易ドライバーの ***tx_sdriver_initialize*** 関数により、ドライバーの入出力操作の管理に使用される 2 つのカウント セマフォが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-167">The ***tx_sdriver_initialize*** function of the simple driver creates two counting semaphores that are used to manage the driver’s input and output operation.</span></span> <span data-ttu-id="9ece4-168">入力セマフォは、シリアル ハードウェア デバイスが文字を受信したときに入力 ISR によって設定されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-168">The input semaphore is set by the input ISR when a character is received by the serial hardware device.</span></span> <span data-ttu-id="9ece4-169">そのため、入力セマフォは初期カウントが 0 で作成されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-169">Because of this, the input semaphore is created with an initial count of zero.</span></span>

<span data-ttu-id="9ece4-170">一方、出力セマフォは、シリアル ハードウェアの送信レジスタの可用性を示します。</span><span class="sxs-lookup"><span data-stu-id="9ece4-170">Conversely, the output semaphore indicates the availability of the serial hardware transmit register.</span></span> <span data-ttu-id="9ece4-171">送信レジスタが最初に使用可能であることを示すために値 1 で作成されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-171">It is created with a value of one to indicate the transmit register is initially available.</span></span>

<span data-ttu-id="9ece4-172">初期化関数は、入力および出力通知用の低レベルの割り込みベクター ハンドラーをインストールする役割も担います。</span><span class="sxs-lookup"><span data-stu-id="9ece4-172">The initialization function is also responsible for installing the low-level interrupt vector handlers for input and output notifications.</span></span> <span data-ttu-id="9ece4-173">他の ThreadX SMP 割り込みサービス ルーチンと同様に、低レベル ハンドラーでは、簡易ドライバーの ISR を呼び出す前に、\* **_tx_thread_context_save** _ を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-173">Like other ThreadX SMP interrupt service routines, the low-level handler must call \***_tx_thread_context_save** _ before calling the simple driver ISR.</span></span> <span data-ttu-id="9ece4-174">ドライバーの ISR に制御が戻ったら、低レベル ハンドラーで _\*_ _tx_thread_context_restore_\*\* を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-174">After the driver ISR returns, the low-level handler must call _\*_ _tx_thread_context_restore_\*\*.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ece4-175">初期化は、他のドライバー関数の前に呼び出すことが重要です。</span><span class="sxs-lookup"><span data-stu-id="9ece4-175">It is important that initialization is called before any of the other driver functions.</span></span> <span data-ttu-id="9ece4-176">通常、ドライバーの初期化は **tx_application_define** から呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-176">Typically, driver initialization is called from **tx_application_define**.</span></span>

<span data-ttu-id="9ece4-177">簡易ドライバーの初期化ソース コードについては、306 ページの図 9 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ece4-177">See Figure 9 on page 306 for the initialization source code of the simple driver.</span></span>

```C
VOID     tx_sdriver_initialize(VOID)
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
<span data-ttu-id="9ece4-178">**図 9. 簡易ドライバーの初期化**</span><span class="sxs-lookup"><span data-stu-id="9ece4-178">**FIGURE 9. Simple Driver Initialization**</span></span>

### <a name="simple-driver-input"></a><span data-ttu-id="9ece4-179">簡易ドライバーの入力</span><span class="sxs-lookup"><span data-stu-id="9ece4-179">Simple Driver Input</span></span> 
<span data-ttu-id="9ece4-180">簡易ドライバーの入力は、入力セマフォを中心としています。</span><span class="sxs-lookup"><span data-stu-id="9ece4-180">Input for the simple driver centers around the input semaphore.</span></span> <span data-ttu-id="9ece4-181">シリアル デバイスの入力割り込みを受信すると、入力セマフォが設定されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-181">When a serial device input interrupt is received, the input semaphore is set.</span></span> <span data-ttu-id="9ece4-182">1 つ以上のスレッドがドライバーからの文字を待機している場合、待機時間が最も長いスレッドが再開されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-182">If one or more threads are waiting for a character from the driver, the thread waiting the longest is resumed.</span></span> <span data-ttu-id="9ece4-183">待機しているスレッドがない場合は、スレッドがドライバー入力関数を呼び出すまで、セマフォは単に設定されたままになります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-183">If no threads are waiting, the semaphore simply remains set until a thread calls the drive input function.</span></span>

<span data-ttu-id="9ece4-184">簡易ドライバーの入力処理にはいくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-184">There are several limitations to the simple driver input handling.</span></span> <span data-ttu-id="9ece4-185">最も重要なのは、入力文字が破棄される可能性があることです。</span><span class="sxs-lookup"><span data-stu-id="9ece4-185">The most significant is the potential for dropping input characters.</span></span> <span data-ttu-id="9ece4-186">この可能性があるのは、前の文字が処理される前に到着した入力文字をバッファーする機能がないためです。</span><span class="sxs-lookup"><span data-stu-id="9ece4-186">This is possible because there is no ability to buffer input characters that arrive before the previous character is processed.</span></span> <span data-ttu-id="9ece4-187">これは、入力文字バッファーを追加することで簡単に処理できます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-187">This is easily handled by adding an input character buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ece4-188">**tx_sdriver_input** 関数を呼び出すことができるのはスレッドだけです。</span><span class="sxs-lookup"><span data-stu-id="9ece4-188">Only threads are allowed to call the **tx_sdriver_input** function.</span></span>

<span data-ttu-id="9ece4-189">図 10 は、簡易ドライバーの入力に関連するソース コードを示しています。</span><span class="sxs-lookup"><span data-stu-id="9ece4-189">Figure 10 shows the source code associated with simple driver input.</span></span>

```C
UCHAR     tx_sdriver_input(VOID)
{

    /* Determine if there is a character waiting. If not,
        suspend. */
    tx_semaphore_get(&tx_sdriver_input_semaphore,
                                             TX_WAIT_FOREVER;
    /* Return character from serial RX hardware register. */
    return(*serial_hardware_input_ptr);
}

VOID     tx_sdriver_input_ISR(VOID)
{
    /* See if an input character notification is pending. */
    if (!tx_sdriver_input_semaphore.tx_semaphore_count)
    {
        /* If not, notify thread of an input character. */
        tx_semaphore_put(&tx_sdriver_input_semaphore);
    }
}
```
<span data-ttu-id="9ece4-190">**図 10. 簡易ドライバーの入力**</span><span class="sxs-lookup"><span data-stu-id="9ece4-190">**FIGURE 10. Simple Driver Input**</span></span>

### <a name="simple-driver-output"></a><span data-ttu-id="9ece4-191">簡易ドライバーの出力</span><span class="sxs-lookup"><span data-stu-id="9ece4-191">Simple Driver Output</span></span> 
<span data-ttu-id="9ece4-192">出力処理では、出力セマフォを利用して、シリアル デバイスの送信レジスタが解放されたことを通知します。</span><span class="sxs-lookup"><span data-stu-id="9ece4-192">Output processing utilizes the output semaphore to signal when the serial device’s transmit register is free.</span></span> <span data-ttu-id="9ece4-193">出力文字が実際にデバイスに書き込まれる前に、出力セマフォが取得されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-193">Before an output character is actually written to the device, the output semaphore is obtained.</span></span> <span data-ttu-id="9ece4-194">これが使用できない場合は、前の送信がまだ完了していません。</span><span class="sxs-lookup"><span data-stu-id="9ece4-194">If it is not available, the previous transmit is not yet complete.</span></span>

<span data-ttu-id="9ece4-195">出力 ISR は、送信完了割り込みを処理する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="9ece4-195">The output ISR is responsible for handling the transmit complete interrupt.</span></span> <span data-ttu-id="9ece4-196">出力 ISR の処理によって出力セマフォが設定され、それによって別の文字の出力が可能になります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-196">Processing of the output ISR amounts to setting the output semaphore, thereby allowing output of another character.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ece4-197">**tx_sdriver_output** 関数を呼び出すことができるのはスレッドだけです。</span><span class="sxs-lookup"><span data-stu-id="9ece4-197">Only threads are allowed to call the **tx_sdriver_output** function.</span></span>

<span data-ttu-id="9ece4-198">図 11 は、簡易ドライバーの出力に関連するソース コードを示しています。</span><span class="sxs-lookup"><span data-stu-id="9ece4-198">Figure 11 shows the source code associated with simple driver output.</span></span>

```C
VOID     tx_sdriver_output(UCHAR alpha)
{

    /* Determine if the hardware is ready to transmit a
       character. If not, suspend until the previous output
        completes. */
    tx_semaphore_get(&tx_sdriver_output_semaphore,
                                            TX_WAIT_FOREVER);
    /* Send the character through the hardware. */
    *serial_hardware_output_ptr = alpha;
}

VOID     tx_sdriver_output_ISR(VOID)
{
    /* Notify thread last character transmit is
        complete. */
    tx_semaphore_put(&tx_sdriver_output_semaphore);
}
```
<span data-ttu-id="9ece4-199">**図 11. 簡易ドライバーの出力**</span><span class="sxs-lookup"><span data-stu-id="9ece4-199">**FIGURE 11. Simple Driver Output**</span></span>

### <a name="simple-driver-shortcomings"></a><span data-ttu-id="9ece4-200">簡易ドライバーの欠点</span><span class="sxs-lookup"><span data-stu-id="9ece4-200">Simple Driver Shortcomings</span></span> 
<span data-ttu-id="9ece4-201">この簡易デバイス ドライバーの例は、ThreadX SMP デバイス ドライバーの基本概念を示しています。</span><span class="sxs-lookup"><span data-stu-id="9ece4-201">This simple device driver example illustrates the basic idea of a ThreadX SMP device driver.</span></span> <span data-ttu-id="9ece4-202">しかし、簡易デバイス ドライバーではデータ バッファリングやオーバーヘッドの問題に対処していないため、実際の ThreadX SMP ドライバーを完全に表しているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="9ece4-202">However, because the simple device driver does not address data buffering or any overhead issues, it does not fully represent real-world ThreadX SMP drivers.</span></span> <span data-ttu-id="9ece4-203">次のセクションでは、デバイス ドライバーに関連するより高度な問題の一部について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ece4-203">The following section describes some of the more advanced issues associated with device drivers.</span></span>

## <a name="advanced-driver-issues"></a><span data-ttu-id="9ece4-204">ドライバーの高度な問題</span><span class="sxs-lookup"><span data-stu-id="9ece4-204">Advanced Driver Issues</span></span>

<span data-ttu-id="9ece4-205">前述のように、デバイス ドライバーには、アプリケーションに固有の要件があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-205">As mentioned previously, device drivers have requirements as unique as their applications.</span></span> <span data-ttu-id="9ece4-206">大量のデータ バッファリングを必要とするアプリケーションもあれば、デバイスの割り込みが高頻度で発生するため、最適化されたドライバー ISR を必要とするアプリケーションもあります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-206">Some applications may require an enormous amount of data buffering while another application may require optimized driver ISRs because of high-frequency device interrupts.</span></span>

### <a name="io-buffering"></a><span data-ttu-id="9ece4-207">I/O バッファリング</span><span class="sxs-lookup"><span data-stu-id="9ece4-207">I/O Buffering</span></span> 
<span data-ttu-id="9ece4-208">リアルタイム組み込みアプリケーションでのデータ バッファリングには、かなりの計画が必要です。</span><span class="sxs-lookup"><span data-stu-id="9ece4-208">Data buffering in real-time embedded applications requires considerable planning.</span></span> <span data-ttu-id="9ece4-209">設計の一部は、基になるハードウェア デバイスによって決まります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-209">Some of the design is dictated by the underlying hardware device.</span></span> <span data-ttu-id="9ece4-210">デバイスで基本的なバイト I/O が提供される場合は、単純な循環バッファーが適していると考えられます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-210">If the device provides basic byte I/O, a simple circular buffer is probably in order.</span></span> <span data-ttu-id="9ece4-211">ただし、デバイスでブロック、DMA、またはパケット I/O が提供される場合は、バッファー管理スキームが必要になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-211">However, if the device provides block, DMA, or packet I/O, a buffer management scheme is probably warranted.</span></span> 

### <a name="circular-byte-buffers"></a><span data-ttu-id="9ece4-212">循環バイト バッファー</span><span class="sxs-lookup"><span data-stu-id="9ece4-212">Circular Byte Buffers</span></span> 
<span data-ttu-id="9ece4-213">通常、循環バイト バッファーは、UART のような単純なシリアル ハードウェア デバイスを管理するドライバーで使用されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-213">Circular byte buffers are typically used in drivers that manage a simple serial hardware device like a UART.</span></span> <span data-ttu-id="9ece4-214">このような場合、2 つの循環バッファー (1 つは入力用、もう 1 つは出力用) が最もよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-214">Two circular buffers are most often used in such situations—one for input and one for output.</span></span>

<span data-ttu-id="9ece4-215">各循環バイト バッファーは、バイト メモリ領域 (通常は UCHAR の配列)、読み取りポインター、書き込みポインターで構成されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-215">Each circular byte buffer is comprised of a byte memory area (typically an array of UCHARs), a read pointer, and a write pointer.</span></span> <span data-ttu-id="9ece4-216">読み取りポインターと書き込みポインターがバッファー内の同じメモリ位置を参照している場合、バッファーは空と見なされます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-216">A buffer is considered empty when the read pointer and the write pointers reference the same memory location in the buffer.</span></span> <span data-ttu-id="9ece4-217">ドライバーの初期化により、読み取りと書き込み両方のバッファーのポインターがバッファーの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-217">Driver initialization sets both the read and write buffer pointers to the beginning address of the buffer.</span></span>

### <a name="circular-buffer-input"></a><span data-ttu-id="9ece4-218">循環バッファー入力</span><span class="sxs-lookup"><span data-stu-id="9ece4-218">Circular Buffer Input</span></span> 
<span data-ttu-id="9ece4-219">入力バッファーは、アプリケーションの準備が整う前に到着した文字を保持するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-219">The input buffer is used to hold characters that arrive before the application is ready for them.</span></span> <span data-ttu-id="9ece4-220">(通常は割り込みサービス ルーチンで) 入力文字を受信すると、その新しい文字がハードウェア デバイスから取得され、書き込みポインターが指す位置の入力バッファーに配置されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-220">When an input character is received (usually in an interrupt service routine), the new character is retrieved from the hardware device and placed into the input buffer at the location pointed to by the write pointer.</span></span> <span data-ttu-id="9ece4-221">その後、書き込みポインターはバッファー内の次の位置に進められます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-221">The write pointer is then advanced to the next position in the buffer.</span></span> <span data-ttu-id="9ece4-222">次の位置がバッファーの末尾を越える場合、書き込みポインターはバッファーの先頭に設定されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-222">If the next position is past the end of the buffer, the write pointer is set to the beginning of the buffer.</span></span> <span data-ttu-id="9ece4-223">新しい書き込みポインターが読み取りポインターと同じである場合、書き込みポインターの前進をキャンセルすることによって、キューの満杯状態が処理されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-223">The queue full condition is handled by canceling the write pointer advancement if the new write pointer is the same as the read pointer.</span></span>

<span data-ttu-id="9ece4-224">ドライバーに対するアプリケーションの入力バイト要求では、まず、入力バッファーの読み取りおよび書き込みポインターが調べられます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-224">Application input byte requests to the driver first examine the read and write pointers of the input buffer.</span></span> <span data-ttu-id="9ece4-225">読み取りと書き込みのポインターが同一の場合、バッファーは空です。</span><span class="sxs-lookup"><span data-stu-id="9ece4-225">If the read and write pointers are identical, the buffer is empty.</span></span> <span data-ttu-id="9ece4-226">読み取りポインターが同じでない場合は、読み取りポインターが指すバイトが入力バッファーからコピーされ、読み取りポインターが次のバッファー位置に進められます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-226">Otherwise, if the read pointer is not the same, the byte pointed to by the read pointer is copied from the input buffer and the read pointer is advanced to the next buffer location.</span></span> <span data-ttu-id="9ece4-227">新しい読み取りポインターがバッファーの末尾を越える場合は、先頭にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-227">If the new read pointer is past the end of the buffer, it is reset to the beginning.</span></span> <span data-ttu-id="9ece4-228">図 12 は、循環入力バッファーのロジックを示しています。</span><span class="sxs-lookup"><span data-stu-id="9ece4-228">Figure 12 shows the logic for the circular input buffer.</span></span>

```C
UCHAR     tx_input_buffer[MAX_SIZE];
UCHAR     tx_input_write_ptr;
UCHAR     tx_input_read_ptr;

/* Initialization.  */
tx_input_write_ptr =  &tx_input_buffer[0];
tx_input_read_ptr =    &tx_input_buffer[0];

/* Input byte ISR... UCHAR alpha has character from device. */
save_ptr =  tx_input_write_ptr;
*tx_input_write_ptr++ =  alpha;
if (tx_input_write_ptr > &tx_input_buffer[MAX_SIZE-1])
    tx_input_write_ptr =  &tx_input_buffer[0];  /* Wrap */
if (tx_input_write_ptr == tx_input_read_ptr)
    tx_input_write_ptr =  save_ptr;  /* Buffer full */

/* Retrieve input byte from buffer... */
if (tx_input_read_ptr != tx_input_write_ptr)
{
    alpha =  *tx_input_read_ptr++;
    if (tx_input_read_ptr > &tx_input_buffer[MAX_SIZE-1])
        tx_input_read_ptr =  &tx_input_buffer[0];
}
```
<span data-ttu-id="9ece4-229">**図 12. 循環入力バッファーのロジック**</span><span class="sxs-lookup"><span data-stu-id="9ece4-229">**FIGURE 12. Logic for Circular Input Buffer**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ece4-230">信頼性の高い動作を実現するために、入力と出力の両方の循環バッファーの読み取りおよび書き込みポインターを操作するときに、割り込みをロックアウトすることが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-230">For reliable operation, it may be necessary to lockout interrupts when manipulating the read and write pointers of both the input and output circular buffers.</span></span>

### <a name="circular-output-buffer"></a><span data-ttu-id="9ece4-231">循環出力バッファー</span><span class="sxs-lookup"><span data-stu-id="9ece4-231">Circular Output Buffer</span></span> 
<span data-ttu-id="9ece4-232">出力バッファーは、ハードウェア デバイスが前のバイトの送信を終了する前に、出力用に到着した文字を保持するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-232">The output buffer is used to hold characters that have arrived for output before the hardware device finished sending the previous byte.</span></span> <span data-ttu-id="9ece4-233">出力バッファー処理は入力バッファー処理と似ていますが、送信完了割り込み処理によって出力読み取りポインターが操作され、アプリケーションの出力要求で出力書き込みポインターが利用される点が異なります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-233">Output buffer processing is similar to input buffer processing, except the transmit complete interrupt processing manipulates the output read pointer, while the application output request utilizes the output write pointer.</span></span> <span data-ttu-id="9ece4-234">それ以外の点では、出力バッファー処理は同じです。</span><span class="sxs-lookup"><span data-stu-id="9ece4-234">Otherwise, the output buffer processing is the same.</span></span> <span data-ttu-id="9ece4-235">図 13 は、循環出力バッファーのロジックを示しています。</span><span class="sxs-lookup"><span data-stu-id="9ece4-235">Figure 13shows the logic for the circular output buffer.</span></span>

```C
UCHAR     tx_output_buffer[MAX_SIZE];
UCHAR     tx_output_write_ptr;
UCHAR     tx_output_read_ptr;

/* Initialization.  */
tx_output_write_ptr =  &tx_output_buffer[0];
tx_output_read_ptr =   &tx_output_buffer[0];

/* Transmit complete ISR... Device ready to send. */
if (tx_output_read_ptr != tx_output_write_ptr)
{
    *device_reg =  *tx_output_read_ptr++;
    if (tx_output_read_reg > &tx_output_buffer[MAX_SIZE-1])
    tx_output_read_ptr =  &tx_output_buffer[0];
}

/* Output byte driver service. If device busy, buffer! */
save_ptr =  tx_output_write_ptr;
*tx_output_write_ptr++ =  alpha;
if (tx_output_write_ptr > &tx_output_buffer[MAX_SIZE-1])
    tx_output_write_ptr =  &tx_output_buffer[0];  /* Wrap */
if (tx_output_write_ptr == tx_output_read_ptr)
    tx_output_write_ptr =  save_ptr;  /* Buffer full!  */
```
<span data-ttu-id="9ece4-236">**図 13. 循環出力バッファーのロジック**</span><span class="sxs-lookup"><span data-stu-id="9ece4-236">**FIGURE 13. Logic for Circular Output Buffer**</span></span>

### <a name="buffer-io-management"></a><span data-ttu-id="9ece4-237">バッファー I/O の管理</span><span class="sxs-lookup"><span data-stu-id="9ece4-237">Buffer I/O Management</span></span> 
<span data-ttu-id="9ece4-238">組み込みマイクロプロセッサのパフォーマンスを向上させるために、多くの周辺機器では、ソフトウェアによって提供されるバッファーを使用してデータが送受信されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-238">To improve the performance of embedded microprocessors, many peripheral device devices transmit and receive data with buffers supplied by software.</span></span> <span data-ttu-id="9ece4-239">実装によっては、データの個々のパケットを送受信するために複数のバッファーが使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-239">In some implementations, multiple buffers may be used to transmit or receive individual packets of data.</span></span> 

<span data-ttu-id="9ece4-240">I/O バッファーのサイズと場所は、アプリケーションやドライバー ソフトウェアによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-240">The size and location of I/O buffers is determined by the application and/or driver software.</span></span> <span data-ttu-id="9ece4-241">通常、バッファーはサイズが固定されており、ThreadX SMP ブロック メモリ プール内で管理されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-241">Typically, buffers are fixed in size and managed within a ThreadX SMP block memory pool.</span></span> <span data-ttu-id="9ece4-242">図 14 は、一般的な I/O バッファーと、それらの割り当てを管理する ThreadX SMP ブロック メモリ プールを示しています。</span><span class="sxs-lookup"><span data-stu-id="9ece4-242">Figure 14describes a typical I/O buffer and a ThreadX SMP block memory pool that manages their allocation.</span></span>

```C
typedef struct TX_IO_BUFFER_STRUCT
{

      struct TX_IO_BUFFER_STRUCT *tx_next_packet;
    struct TX_IO_BUFFER_STRUCT *tx_next_buffer;
      UCHAR  tx_buffer_area[TX_MAX_BUFFER_SIZE];
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
<span data-ttu-id="9ece4-243">**図 14. I/O バッファー**</span><span class="sxs-lookup"><span data-stu-id="9ece4-243">**FIGURE 14. I/O Buffer**</span></span>

### <a name="tx_io_buffer"></a><span data-ttu-id="9ece4-244">TX_IO_BUFFER</span><span class="sxs-lookup"><span data-stu-id="9ece4-244">TX_IO_BUFFER</span></span> 
<span data-ttu-id="9ece4-245">typedef TX_IO_BUFFER は、2 つのポインターで構成されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-245">The typedef TX_IO_BUFFER consists of two pointers.</span></span> <span data-ttu-id="9ece4-246">\***tx_next_packet** _ ポインターは、入力または出力リストで複数のパケットをリンクするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-246">The \***tx_next_packet** _ pointer is used to link multiple packets on either the input or output list.</span></span> <span data-ttu-id="9ece4-247">_ *_tx_next_buffer_*\* ポインターは、デバイスからのデータの個々のパケットを構成するバッファーを一緒にリンクするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-247">The _ *_tx_next_buffer_*\* pointer is used to link together buffers that make up an individual packet of data from the device.</span></span> <span data-ttu-id="9ece4-248">バッファーがプールから割り当てられるときに、これらのポインターはどちらも NULL に設定されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-248">Both of these pointers are set to NULL when the buffer is allocated from the pool.</span></span> <span data-ttu-id="9ece4-249">さらに、一部のデバイスでは、実際にデータを格納するバッファー領域の量を示す別のフィールドが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-249">In addition, some devices may require another field to indicate how much of the buffer area actually contains data.</span></span>

### <a name="buffered-io-advantage"></a><span data-ttu-id="9ece4-250">バッファー I/O の利点</span><span class="sxs-lookup"><span data-stu-id="9ece4-250">Buffered I/O Advantage</span></span> 
<span data-ttu-id="9ece4-251">バッファー I/O スキームの利点は何でしょうか。</span><span class="sxs-lookup"><span data-stu-id="9ece4-251">What are the advantages of a buffer I/O scheme?</span></span> <span data-ttu-id="9ece4-252">最大の利点は、デバイスのレジスタとアプリケーションのメモリの間でデータがコピーされないことです。</span><span class="sxs-lookup"><span data-stu-id="9ece4-252">The biggest advantage is that data is not copied between the device registers and the application’s memory.</span></span> <span data-ttu-id="9ece4-253">代わりに、ドライバーによって一連のバッファー ポインターがデバイスに提供されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-253">Instead, the driver provides the device with a series of buffer pointers.</span></span> <span data-ttu-id="9ece4-254">物理デバイス I/O では、指定されたバッファー メモリを直接利用します。</span><span class="sxs-lookup"><span data-stu-id="9ece4-254">Physical device I/O utilizes the supplied buffer memory directly.</span></span>

<span data-ttu-id="9ece4-255">プロセッサを使用して情報の入力または出力パケットをコピーすることは非常にコストがかかるので、高スループットの I/O 状況では避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-255">Using the processor to copy input or output packets of information is extremely costly and should be avoided in any high throughput I/O situation.</span></span>

<span data-ttu-id="9ece4-256">バッファー I/O アプローチのもう 1 つの利点は、入力と出力のリストに満杯状態がないことです。</span><span class="sxs-lookup"><span data-stu-id="9ece4-256">Another advantage to the buffered I/O approach is that the input and output lists do not have full conditions.</span></span> <span data-ttu-id="9ece4-257">どちらのリストにも、使用可能なすべてのバッファーをいつでも配置できます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-257">All of the available buffers can be on either list at any one time.</span></span> <span data-ttu-id="9ece4-258">これは、この章で前述した単純なバイト循環バッファーとは対照的です。</span><span class="sxs-lookup"><span data-stu-id="9ece4-258">This contrasts with the simple byte circular buffers presented earlier in the chapter.</span></span> <span data-ttu-id="9ece4-259">それぞれ、コンパイル時に決定されたサイズに固定されていました。</span><span class="sxs-lookup"><span data-stu-id="9ece4-259">Each had a fixed size determined at compilation.</span></span>

### <a name="buffered-driver-responsibilities"></a><span data-ttu-id="9ece4-260">バッファー型ドライバーの役割</span><span class="sxs-lookup"><span data-stu-id="9ece4-260">Buffered Driver Responsibilities</span></span> 
<span data-ttu-id="9ece4-261">バッファー型デバイス ドライバーは、I/O バッファーのリンク リストの管理にのみ関与します。</span><span class="sxs-lookup"><span data-stu-id="9ece4-261">Buffered device drivers are only concerned with managing linked lists of I/O buffers.</span></span> <span data-ttu-id="9ece4-262">入力バッファー リストは、アプリケーション ソフトウェアの準備が整う前に受信したパケット用に保持されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-262">An input buffer list is maintained for packets that are received before the application software is ready.</span></span> <span data-ttu-id="9ece4-263">一方、出力バッファー リストは、ハードウェア デバイスが処理できるようになる前に送られてくるパケット用に保持されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-263">Conversely, an output buffer list is maintained for packets being sent faster than the hardware device can handle them.</span></span> <span data-ttu-id="9ece4-264">314 ページの図 15 は、データ パケットのシンプルな入力および出力リンク リストと、各パケットを構成するバッファーを示しています。</span><span class="sxs-lookup"><span data-stu-id="9ece4-264">Figure 15 on page 314 shows simple input and output linked lists of data packets and the buffer(s) that make up each packet.</span></span>

![バッファー型ドライバーの役割](media/image11.png)

<span data-ttu-id="9ece4-266">**図 15. 入力と出力のリスト**</span><span class="sxs-lookup"><span data-stu-id="9ece4-266">**FIGURE 15. Input-Output Lists**</span></span>

<span data-ttu-id="9ece4-267">アプリケーションは、同じ I/O バッファーを使用するバッファー型ドライバーとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="9ece4-267">Applications interface with buffered drivers with the same I/O buffers.</span></span> <span data-ttu-id="9ece4-268">送信時に、アプリケーション ソフトウェアによって、送信する 1 つ以上のバッファーがドライバーに提供されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-268">On transmit, application software provides the driver with one or more buffers to transmit.</span></span> <span data-ttu-id="9ece4-269">アプリケーション ソフトウェアが入力を要求すると、ドライバーは I/O バッファーに入力データを返します。</span><span class="sxs-lookup"><span data-stu-id="9ece4-269">When the application software requests input, the driver returns the input data in I/O buffers.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ece4-270">一部のアプリケーションでは、空きバッファーをドライバーからの入力バッファーと交換することをアプリケーションに要求する、ドライバー入力インターフェイスを構築すると役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-270">In some applications, it may be useful to build a driver input interface that requires the application to exchange a free buffer for an input buffer from the driver.</span></span> <span data-ttu-id="9ece4-271">これにより、ドライバーの内部でのバッファー割り当て処理が軽減される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-271">This might alleviate some buffer allocation processing inside of the driver.</span></span>

### <a name="interrupt-management"></a><span data-ttu-id="9ece4-272">割り込み管理</span><span class="sxs-lookup"><span data-stu-id="9ece4-272">Interrupt Management</span></span> 
<span data-ttu-id="9ece4-273">一部のアプリケーションでは、デバイスの割り込み頻度により、ISR を C で記述したり、各割り込みで ThreadX SMP と対話したりすることが妨げられる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-273">In some applications, the device interrupt frequency may prohibit writing the ISR in C or to interact with ThreadX SMP on each interrupt.</span></span> <span data-ttu-id="9ece4-274">たとえば、中断されたコンテキストの保存と復元に 25 マイクロ秒かかる場合、割り込み頻度が 50 マイクロ秒であるとすると、コンテキストの完全な保存を実行することはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="9ece4-274">For example, if it takes 25us to save and restore the interrupted context, it would not be advisable to perform a full context save if the interrupt frequency was 50us.</span></span> <span data-ttu-id="9ece4-275">このような場合は、アセンブリ言語の小さな ISR を使用して、デバイスの割り込みの大半を処理します。</span><span class="sxs-lookup"><span data-stu-id="9ece4-275">In such cases, a small assembly language ISR is used to handle most of the device interrupts.</span></span> <span data-ttu-id="9ece4-276">この低オーバーヘッドの ISR は、必要な場合にのみ ThreadX SMP と対話します。</span><span class="sxs-lookup"><span data-stu-id="9ece4-276">This lowoverhead ISR would only interact with ThreadX SMP when necessary.</span></span>

<span data-ttu-id="9ece4-277">第 3 章の最後にある割り込み管理の説明にも同様の説明があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-277">A similar discussion can be found in the interrupt management discussion at the end of Chapter 3.</span></span>

> [!NOTE]
> <span data-ttu-id="9ece4-278">ドライバーの ISR コードからドライバー コードの重要なセクションを保護するために割り込みロックアウトが使用される場合、スレッド レベルのドライバー コードは、ISR が処理されるのと同じコアで常に実行される必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-278">If interrupt lockout is to be used to protect critical sections of driver code from driver ISR code, the thread level driver code must always execute on the same core that the ISR is processed on.</span></span> <span data-ttu-id="9ece4-279">それ以外の場合は、やはりコア間の保護が組み込まれている TX_DISABLE や TX_RESTORE などの内部 ThreadX SMP プリミティブを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-279">Otherwise, internal ThreadX SMP primitives like TX_DISABLE and TX_RESTORE should be used that also have inter-core protection built-in.</span></span>

### <a name="thread-suspension"></a><span data-ttu-id="9ece4-280">スレッドの中断</span><span class="sxs-lookup"><span data-stu-id="9ece4-280">Thread Suspension</span></span> 
<span data-ttu-id="9ece4-281">この章で前述した簡易ドライバーの例では、文字が使用できない場合に、入力サービスの呼び出し元が一時停止されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-281">In the simple driver example presented earlier in this chapter, the caller of the input service suspends if a character is not available.</span></span> <span data-ttu-id="9ece4-282">アプリケーションによっては、これを許容できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-282">In some applications, this might not be acceptable.</span></span>

<span data-ttu-id="9ece4-283">たとえば、ドライバーからの入力を処理する役割を担うスレッドにほかの役割もある場合、ドライバーの入力だけで一時停止しても、うまく機能しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-283">For example, if the thread responsible for processing input from a driver also has other duties, suspending on just the driver input is probably not going to work.</span></span> <span data-ttu-id="9ece4-284">代わりに、スレッドに対する他の処理要求と同様に処理を要求するように、ドライバーをカスタマイズする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ece4-284">Instead, the driver needs to be customized to request processing similar to the way other processing requests are made to the thread.</span></span>

<span data-ttu-id="9ece4-285">ほとんどの場合、入力バッファーはリンク リストに配置され、入力イベント メッセージがスレッドの入力キューに送信されます。</span><span class="sxs-lookup"><span data-stu-id="9ece4-285">In most cases, the input buffer is placed on a linked list and an input event message is sent to the thread’s input queue.</span></span>