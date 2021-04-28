---
title: 第 2 章 - モジュールの要件
description: この記事は、ThreadX モジュールをビルドするための要件の説明です。
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 32288d78ceffb74ab088a1d720dbac657f6d3ed4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810310"
---
# <a name="chapter-2---module-requirements"></a><span data-ttu-id="6d9fd-103">第 2 章 - モジュールの要件</span><span class="sxs-lookup"><span data-stu-id="6d9fd-103">Chapter 2 - Module requirements</span></span>

<span data-ttu-id="6d9fd-104">ThreadX モジュールには、モジュールの基本的な特性を定義するプリアンブルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-104">A ThreadX Module contains a preamble, which defines the basic characteristics of the module.</span></span> <span data-ttu-id="6d9fd-105">プリアンブルに続くのは、モジュールの命令領域です。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-105">The preamble is followed by the instruction area of the module.</span></span> <span data-ttu-id="6d9fd-106">モジュールは、インプレースで実行される場合もあれば、実行前にモジュール マネージャーによってモジュール メモリ領域にロードされる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-106">Modules may be executed in place or they may be loaded into the module memory area by the Module Manager prior to execution.</span></span> <span data-ttu-id="6d9fd-107">唯一の要件は、プリアンブルが常にモジュールの最初のアドレスに位置していることです。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-107">The only requirement is that the preamble is always located at the first address of the module.</span></span> <span data-ttu-id="6d9fd-108">図 2 は、基本的なモジュール レイアウトを示しています。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-108">Figure 2 illustrates a basic module layout.</span></span>

| <span data-ttu-id="6d9fd-109">モジュール レイアウト</span><span class="sxs-lookup"><span data-stu-id="6d9fd-109">Module Layout</span></span> |
|:---:|
| <span data-ttu-id="6d9fd-110">\[モジュール プリアンブル\]</span><span class="sxs-lookup"><span data-stu-id="6d9fd-110">\[module preamble\]</span></span>         |
| <span data-ttu-id="6d9fd-111">\[モジュール命令領域\]</span><span class="sxs-lookup"><span data-stu-id="6d9fd-111">\[module instruction area\]</span></span> |
| <span data-ttu-id="6d9fd-112">\[モジュール RAM 領域\]</span><span class="sxs-lookup"><span data-stu-id="6d9fd-112">\[module RAM area\]</span></span>         |

<span data-ttu-id="6d9fd-113">**図 2** - モジュール レイアウト</span><span class="sxs-lookup"><span data-stu-id="6d9fd-113">**Figure 2** - Module Layout</span></span>

> [!NOTE]
> <span data-ttu-id="6d9fd-114">モジュールは、適切な位置独立コードと、データ コンパイラ/リンカー オプションを使用してビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-114">Modules must be built with the appropriate position independent code and data compiler/linker options.</span></span> <span data-ttu-id="6d9fd-115">これにより、どのメモリ領域でもモジュールを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-115">This enables execution of the module in any memory area.</span></span>

<span data-ttu-id="6d9fd-116">モジュール スレッドが作成されると、スレッドがメモリ保護カーネルにあるときに使用する 2 番目のスタック空間が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-116">When a Module thread is created, a second stack space is allocated for use when the thread is in the memory-protected kernel.</span></span> <span data-ttu-id="6d9fd-117">スレッドのカーネル スタック空間のサイズは、**_txm_module_port.h_ *_ で **TXM_MODULE_KERNEL_STACK_SIZE** を使用してユーザーが構成できます。_* _tx_thread_create_** の呼び出し時にユーザーが指定したスタックのみがモジュールで使用されるため、これによって、モジュール スレッドの作成時に使用するスタックのサイズを削減できます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-117">The size of the thread's kernel stack space is user-configurable using **TXM_MODULE_KERNEL_STACK_SIZE** in **_txm_module_port.h_*_. This allows a smaller stack size to be used when creating a Module thread, as the stack specified by the user when calling _*_tx_thread_create_** is only used in the module.</span></span>

> [!NOTE]
> <span data-ttu-id="6d9fd-118">モジュール スレッド スタックの最上位にはスレッド エントリ情報構造体 (**TXM_MODULE_THREAD_ENTRY_INFO**) が含まれているため、利用可能なスタック サイズはこの構造体のサイズの分だけ減少します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-118">The top of a module thread stack contains the thread entry information structure (**TXM_MODULE_THREAD_ENTRY_INFO**), so the available stack size is decreased by the size of this structure.</span></span> <span data-ttu-id="6d9fd-119">モジュールでスレッドを作成するときは、少なくとも、この構造体のサイズの分だけスタック サイズを増やします。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-119">When creating a thread in a module, increase its stack size by at least this the size of this structure.</span></span>

<span data-ttu-id="6d9fd-120">ThreadX モジュールを作成してビルドするには、以下の手順が必要です (それぞれの手順については、以下で詳しく説明します)。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-120">The following steps are required for creating and building a ThreadX Module (each step is described in greater detail below).</span></span>

1. <span data-ttu-id="6d9fd-121">モジュール内のすべての C ファイルでは、**_txm_module.h_** をインクルードする前に **TXM_MODULE** を #define する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-121">All C files in a module must #define **TXM_MODULE** prior to including **_txm_module.h_**.</span></span> <span data-ttu-id="6d9fd-122">これは、コンパイル中のソース ファイルで、またはプロジェクト設定の一部として実行できます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-122">This can be accomplished in the source file being compiled or as part of the project settings.</span></span> <span data-ttu-id="6d9fd-123">これにより、ThreadX API の呼び出しが、モジュール固有バージョンの API に再マップされます。この API により、常駐モジュール マネージャーでディスパッチ関数が呼び出され、実際の API 関数の呼び出しが実行されます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-123">Doing so remaps the ThreadX API calls to the module-specific version of the API that invokes the dispatch function in the resident Module Manager to perform the call to the actual API function.</span></span>
2. <span data-ttu-id="6d9fd-124">各モジュールの最初の命令領域アドレスに、モジュールの特性と必要なリソースを定義するプリアンブルが存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-124">Each module must have a preamble at its first instruction area address which defines the characteristics and the resource needs of the module.</span></span>
3. <span data-ttu-id="6d9fd-125">各モジュールでは、モジュール命令領域の先頭でプリアンブルをリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-125">Each module must link the preamble at the beginning of the module instruction area.</span></span>
4. <span data-ttu-id="6d9fd-126">各モジュールでは、ThreadX との対話に使用されるモジュール固有の関数を含むモジュール ライブラリ (***txm.a***) に対してリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-126">Each module must link against a module library (***txm.a***), which contains module-specific functions used to interact with ThreadX.</span></span>

## <a name="module-sources"></a><span data-ttu-id="6d9fd-127">モジュール ソース</span><span class="sxs-lookup"><span data-stu-id="6d9fd-127">Module sources</span></span>

<span data-ttu-id="6d9fd-128">ThreadX モジュールが独自に備える一連のソース ファイルは、モジュールのソース コードと直接リンクして配置されるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-128">ThreadX Modules have their own set of source files that are designed to be linked and located directly with the module source code.</span></span> <span data-ttu-id="6d9fd-129">これらのファイルは、個別のモジュールと常駐モジュール マネージャーの間のブリッジを提供します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-129">These files provide the bridge between the separate module and resident Module Manager.</span></span> <span data-ttu-id="6d9fd-130">モジュール ファイルには以下のものがあります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-130">The Module files are as follows.</span></span>

| <span data-ttu-id="6d9fd-131">ファイル名</span><span class="sxs-lookup"><span data-stu-id="6d9fd-131">File Name</span></span> | <span data-ttu-id="6d9fd-132">内容</span><span class="sxs-lookup"><span data-stu-id="6d9fd-132">Contents</span></span> |
|---|---|
| <span data-ttu-id="6d9fd-133">**txm_module.h**</span><span class="sxs-lookup"><span data-stu-id="6d9fd-133">**txm_module.h**</span></span> | <span data-ttu-id="6d9fd-134">モジュール情報を定義するインクルード ファイル。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-134">Include file that defines module information.</span></span> |
| <span data-ttu-id="6d9fd-135">**txm_module_port.h**</span><span class="sxs-lookup"><span data-stu-id="6d9fd-135">**txm_module_port.h**</span></span> | <span data-ttu-id="6d9fd-136">ポート固有のモジュール情報を定義するインクルード ファイル。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-136">Include file that defines port-specific module information.</span></span> |
| <span data-ttu-id="6d9fd-137">**txm_module_user.h**</span><span class="sxs-lookup"><span data-stu-id="6d9fd-137">**txm_module_user.h**</span></span> | <span data-ttu-id="6d9fd-138">ユーザーがカスタマイズできる値を定義します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-138">Defines and values the user can customize.</span></span> |
| <span data-ttu-id="6d9fd-139">**txm_module_initialize.s [1][3]**</span><span class="sxs-lookup"><span data-stu-id="6d9fd-139">**txm_module_initialize.s [1][3]**</span></span> | <span data-ttu-id="6d9fd-140">組み込み関数をスタートアップ モジュールに呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-140">Calls intrinsic functions to startup module.</span></span> |
| <span data-ttu-id="6d9fd-141">**txm_module_preamble.\{s/S/68\}**</span><span class="sxs-lookup"><span data-stu-id="6d9fd-141">**txm_module_preamble.\{s/S/68\}**</span></span> | <span data-ttu-id="6d9fd-142">モジュール プリアンブル アセンブリ ファイル。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-142">Module preamble assembly file.</span></span> <span data-ttu-id="6d9fd-143">このファイルは、モジュール固有のさまざまな属性を定義し、モジュール アプリケーション コードとリンクされます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-143">This file defines various module-specific attributes and is linked with the module application code.</span></span> |
| <span data-ttu-id="6d9fd-144">**txm_module_application_request.c [1]**</span><span class="sxs-lookup"><span data-stu-id="6d9fd-144">**txm_module_application_request.c [1]**</span></span> | <span data-ttu-id="6d9fd-145">モジュール アプリケーション要求関数は、アプリケーション固有の要求を常駐コードに送信します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-145">Module application request function sends an application-specific request to the resident code.</span></span> |
| <span data-ttu-id="6d9fd-146">**txm_module_callback_request_thread_entry.c&nbsp;[1]**</span><span class="sxs-lookup"><span data-stu-id="6d9fd-146">**txm_module_callback_request_thread_entry.c&nbsp;[1]**</span></span> | <span data-ttu-id="6d9fd-147">タイマーや通知コールバックなど、モジュールによって要求されたコールバックの処理を担当するモジュール コールバック スレッド。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-147">Module callback thread that is responsible for processing callbacks requested by the module, including timers and notification callbacks.</span></span> |
| <span data-ttu-id="6d9fd-148">**txm_\*.c [1][2]**</span><span class="sxs-lookup"><span data-stu-id="6d9fd-148">**txm_\*.c [1][2]**</span></span> | <span data-ttu-id="6d9fd-149">標準の ThreadX API サービスであり、これらはカーネル ディスパッチャーを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-149">The standard ThreadX API services, these call the kernel dispatcher.</span></span>
| <span data-ttu-id="6d9fd-150">**txm_module_object_allocate.c [1]**</span><span class="sxs-lookup"><span data-stu-id="6d9fd-150">**txm_module_object_allocate.c [1]**</span></span> | <span data-ttu-id="6d9fd-151">マネージャーのメモリ プールに位置するモジュール オブジェクトにメモリを割り当てるためのモジュール関数。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-151">Module function to allocate memory for module objects located in the manager memory pool.</span></span> |
| <span data-ttu-id="6d9fd-152">**txm_module_object_deallocate.c [1]**</span><span class="sxs-lookup"><span data-stu-id="6d9fd-152">**txm_module_object_deallocate.c [1]**</span></span> | <span data-ttu-id="6d9fd-153">マネージャーのメモリ プールに位置するモジュール オブジェクトへのメモリ割り当てを解除するためのモジュール関数。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-153">Module function to deallocate memory for module objects located in the manager memory pool.</span></span> |
| <span data-ttu-id="6d9fd-154">**txm_module_object_pointer_get.c [1]**</span><span class="sxs-lookup"><span data-stu-id="6d9fd-154">**txm_module_object_pointer_get.c [1]**</span></span> | <span data-ttu-id="6d9fd-155">システム オブジェクトへのポインターを取得するためのモジュール関数。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-155">Module function to retrieve a pointer to a system object.</span></span> |
| <span data-ttu-id="6d9fd-156">**txm_module_object_pointer_get_extended.c [1]**</span><span class="sxs-lookup"><span data-stu-id="6d9fd-156">**txm_module_object_pointer_get_extended.c [1]**</span></span> | <span data-ttu-id="6d9fd-157">システム オブジェクトへのポインターを取得するための、名前の長さに関して安全なモジュール関数。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-157">Module function to retrieve a pointer to a system object, name length safety.</span></span> |
| <span data-ttu-id="6d9fd-158">**txm_module_thread_shell_entry.c [1]**</span><span class="sxs-lookup"><span data-stu-id="6d9fd-158">**txm_module_thread_shell_entry.c [1]**</span></span> | <span data-ttu-id="6d9fd-159">モジュール スレッドのエントリ関数。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-159">Module thread entry function.</span></span> |
| <span data-ttu-id="6d9fd-160">**txm_module_thread_system_suspend.c [1]**</span><span class="sxs-lookup"><span data-stu-id="6d9fd-160">**txm_module_thread_system_suspend.c [1]**</span></span> | <span data-ttu-id="6d9fd-161">スレッドを中断するためのモジュール関数。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-161">Module function to suspend a thread.</span></span> |

<span data-ttu-id="6d9fd-162">**[1]** Located in library **_txm.a_**.</span><span class="sxs-lookup"><span data-stu-id="6d9fd-162">**[1]** Located in library **_txm.a_**.</span></span>

<span data-ttu-id="6d9fd-163">**[2]** これらのファイルは ThreadX API ファイルと同じ名前ですが、プレフィックスは **tx_** ではなく **txm_** です。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-163">**[2]** These files have the same name as the ThreadX API files, with **txm_** prefix instead of **tx_** prefix.</span></span>

<span data-ttu-id="6d9fd-164">**[3]** **txm_module_initialize.s** ファイルは、ARM ツールを使用するポート専用です。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-164">**[3]** The **txm_module_initialize.s** file is only for ports using ARM tools.</span></span>

## <a name="module-preamble"></a><span data-ttu-id="6d9fd-165">モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="6d9fd-165">Module preamble</span></span>

<span data-ttu-id="6d9fd-166">モジュール プリアンブルは、モジュールの特性とリソースを定義します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-166">The Module Preamble defines characteristics and resources of the module.</span></span> <span data-ttu-id="6d9fd-167">スレッドに関連付けられる初期スレッド エントリ関数および初期メモリ領域などの情報は、プリアンブルで定義されます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-167">Information such as the initial thread entry function and the initial memory area associated with the thread are defined in the preamble.</span></span> <span data-ttu-id="6d9fd-168">ポート固有のプリアンブルの例は[付録](appendix.md)にあります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-168">Port-specific preamble examples are in the [appendix](appendix.md).</span></span> <span data-ttu-id="6d9fd-169">図 3 は、汎用ターゲット用の ThreadX モジュール プリアンブルの例を示しています (\* で始まる行は、通常であればアプリケーションによって変更される値です)。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-169">Figure 3 shows an example ThreadX module preamble for a generic target (the lines starting with \* are values typically modified by the application):</span></span>

```c
    AREA Init, CODE, READONLY

    /* Define public symbols. */
    EXPORT __txm_module_preamble

    /* Define application-specific start/stop entry points for the module. */
    IMPORT demo_module_start

    /* Define common external refrences. */
    IMPORT _txm_module_thread_shell_entry
    IMPORT _txm_module_callback_request_thread_entry
    IMPORT |Image$$ER_RO$$Length|
    IMPORT |Image$$ER_RW$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                  ; Module ID
    DCD     0x6                                         ; Module Major Version
    DCD     0x1                                         ; Module Minor Version
    DCD     32                                          ; Module Preamble Size in 32-bit words
*   DCD     0x12345678                                  ; Module ID (application defined)
*   DCD     0x01000001                                  ; Module Properties where:
                                                        ; Bits 31-24: Compiler ID
                                                        ;   0 -> IAR
                                                        ;   1 -> ARM
                                                        ;   2 -> GNU
                                                        ;   Bits 23-1: Reserved
                                                        ;   Bit 0: 0 -> Privileged mode execution (no MMU protection)
                                                        ;          1 -> User mode execution (MMU protection)
    DCD     _txm_module_thread_shell_entry - . + .      ; Module Shell Entry Point
*   DCD     demo_module_start - . + .                   ; Module Start Thread Entry Point
    DCD     0                                           ; Module Stop Thread Entry Point
*   DCD     1                                           ; Module Start/Stop Thread Priority
*   DCD     2048                                        ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
    DCD     1                                            ; Module Callback Thread Priority
    DCD     2048                                         ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length|                       ; Module Code Size
    DCD     |Image$$ER_RW$$Length|                       ; Module Data Size
    DCD     0                                            ; Reserved 0
    DCD     0                                            ; Reserved 1
    DCD     0                                            ; Reserved 2
    DCD     0                                            ; Reserved 3
    DCD     0                                            ; Reserved 4
    DCD     0                                            ; Reserved 5
    DCD     0                                            ; Reserved 6
    DCD     0                                            ; Reserved 7
    DCD     0                                            ; Reserved 8
    DCD     0                                            ; Reserved 9
    DCD     0                                            ; Reserved 10
    DCD     0                                            ; Reserved 11
    DCD     0                                            ; Reserved 12
    DCD     0                                            ; Reserved 13
    DCD     0                                            ; Reserved 14
    DCD     0                                            ; Reserved 15
    END
```

<span data-ttu-id="6d9fd-170">**図 3**</span><span class="sxs-lookup"><span data-stu-id="6d9fd-170">**Figure 3**</span></span>

<span data-ttu-id="6d9fd-171">ほとんどの場合、開発者が行う必要があるのは、モジュールの開始スレッド (オフセット 0x1C)、モジュール ID (オフセット 0x10)、開始/停止スレッド優先度 (オフセット 0x24)、開始/停止スレッド スタック サイズ (オフセット 0x28) を定義することだけです。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-171">In most cases, the developer only needs to define the module's starting thread (offset 0x1C), module ID (offset 0x10), start/stop thread priority (offset 0x24), and start/stop thread stack size (offset 0x28).</span></span> <span data-ttu-id="6d9fd-172">上記のデモンストレーションの設定では、モジュールの開始スレッドは ***demo_module_start** _、モジュール ID は _*_0x12345678_*_、開始スレッドの優先度は _*_1_*_、スタック サイズは _ *_2048_** バイトです。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-172">The demonstration above is set up such that the starting thread of the module is ***demo_module_start** _, the module ID is _*_0x12345678_*_, and the starting thread has a priority of _*_1_*_, and a stack size of _ *_2048_** bytes.</span></span>

<span data-ttu-id="6d9fd-173">一部のアプリケーションでは、必要に応じて停止スレッドを定義する場合があります。これは、モジュール マネージャーがモジュールを停止するときに実行されます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-173">Some applications may optionally define a stopping thread, which is executed as the Module Manager stops the module.</span></span> <span data-ttu-id="6d9fd-174">さらに、一部のアプリケーションでは、次のように定義されたモジュール プロパティ フィールドを利用する場合があります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-174">In addition, some applications might utilize the Module Properties field, defined as follows.</span></span>

## <a name="module-properties-bit-map"></a><span data-ttu-id="6d9fd-175">モジュール プロパティのビットマップ</span><span class="sxs-lookup"><span data-stu-id="6d9fd-175">Module properties bit map</span></span>

<span data-ttu-id="6d9fd-176">次の表は、プロパティのビットマップの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-176">The table below shows an example of the properties bit map.</span></span> <span data-ttu-id="6d9fd-177">ポート固有のプロパティ ビットマップは[付録](appendix.md)にあります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-177">Port-specific properties bitmaps are in the [appendix](appendix.md).</span></span>

| <span data-ttu-id="6d9fd-178">ビット</span><span class="sxs-lookup"><span data-stu-id="6d9fd-178">Bit</span></span> | <span data-ttu-id="6d9fd-179">値</span><span class="sxs-lookup"><span data-stu-id="6d9fd-179">Value</span></span> | <span data-ttu-id="6d9fd-180">意味</span><span class="sxs-lookup"><span data-stu-id="6d9fd-180">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="6d9fd-181">0</span><span class="sxs-lookup"><span data-stu-id="6d9fd-181">0</span></span> | <span data-ttu-id="6d9fd-182">0</span><span class="sxs-lookup"><span data-stu-id="6d9fd-182">0</span></span><br /><span data-ttu-id="6d9fd-183">1</span><span class="sxs-lookup"><span data-stu-id="6d9fd-183">1</span></span> | <span data-ttu-id="6d9fd-184">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="6d9fd-184">Privileged mode execution</span></span><br /><span data-ttu-id="6d9fd-185">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="6d9fd-185">User mode execution</span></span> |
| <span data-ttu-id="6d9fd-186">1</span><span class="sxs-lookup"><span data-stu-id="6d9fd-186">1</span></span> | <span data-ttu-id="6d9fd-187">0</span><span class="sxs-lookup"><span data-stu-id="6d9fd-187">0</span></span><br /><span data-ttu-id="6d9fd-188">1</span><span class="sxs-lookup"><span data-stu-id="6d9fd-188">1</span></span> | <span data-ttu-id="6d9fd-189">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="6d9fd-189">No MPU protection</span></span><br /><span data-ttu-id="6d9fd-190">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="6d9fd-190">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="6d9fd-191">2</span><span class="sxs-lookup"><span data-stu-id="6d9fd-191">2</span></span> | <span data-ttu-id="6d9fd-192">0</span><span class="sxs-lookup"><span data-stu-id="6d9fd-192">0</span></span><br /><span data-ttu-id="6d9fd-193">1</span><span class="sxs-lookup"><span data-stu-id="6d9fd-193">1</span></span> | <span data-ttu-id="6d9fd-194">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="6d9fd-194">Disable shared/external memory access</span></span><br /><span data-ttu-id="6d9fd-195">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="6d9fd-195">Enable shared/external memory access</span></span> |
| <span data-ttu-id="6d9fd-196">[23-3]</span><span class="sxs-lookup"><span data-stu-id="6d9fd-196">[23-3]</span></span> | <span data-ttu-id="6d9fd-197">0</span><span class="sxs-lookup"><span data-stu-id="6d9fd-197">0</span></span> | <span data-ttu-id="6d9fd-198">予約済み</span><span class="sxs-lookup"><span data-stu-id="6d9fd-198">Reserved</span></span>
| <span data-ttu-id="6d9fd-199">[31-24]</span><span class="sxs-lookup"><span data-stu-id="6d9fd-199">[31-24]</span></span> | <br /><span data-ttu-id="6d9fd-200">0x01</span><span class="sxs-lookup"><span data-stu-id="6d9fd-200">0x01</span></span><br /><span data-ttu-id="6d9fd-201">0x02</span><span class="sxs-lookup"><span data-stu-id="6d9fd-201">0x02</span></span><br /><span data-ttu-id="6d9fd-202">0x03</span><span class="sxs-lookup"><span data-stu-id="6d9fd-202">0x03</span></span> | <span data-ttu-id="6d9fd-203">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="6d9fd-203">**Compiler ID**</span></span><br /><span data-ttu-id="6d9fd-204">IAR</span><span class="sxs-lookup"><span data-stu-id="6d9fd-204">IAR</span></span><br /><span data-ttu-id="6d9fd-205">ARM</span><span class="sxs-lookup"><span data-stu-id="6d9fd-205">ARM</span></span><br /><span data-ttu-id="6d9fd-206">GNU</span><span class="sxs-lookup"><span data-stu-id="6d9fd-206">GNU</span></span> |


## <a name="module-linker-control-file"></a><span data-ttu-id="6d9fd-207">モジュール リンカー制御ファイル</span><span class="sxs-lookup"><span data-stu-id="6d9fd-207">Module linker control file</span></span>

<span data-ttu-id="6d9fd-208">モジュールをビルドするとき、モジュール プリアンブルは、他のどのコード セクションよりも前に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-208">When building a module, the module preamble must be placed before any other code section.</span></span> <span data-ttu-id="6d9fd-209">モジュールは、位置独立のコードおよびデータ セクションを使用してビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-209">A module must be built with position-independent code and data sections.</span></span> <span data-ttu-id="6d9fd-210">ポート固有のリンカー ファイルの例は[付録](appendix.md)にあります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-210">Port-specific example linker files are in the [appendix](appendix.md).</span></span>

## <a name="module-threadx-library"></a><span data-ttu-id="6d9fd-211">モジュールの ThreadX ライブラリ</span><span class="sxs-lookup"><span data-stu-id="6d9fd-211">Module ThreadX library</span></span>

<span data-ttu-id="6d9fd-212">各モジュールは、特別な、モジュール中心の ThreadX ライブラリに対してリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-212">Each module must link against a special, module-centric ThreadX library.</span></span> <span data-ttu-id="6d9fd-213">このライブラリは、常駐コードで ThreadX サービスへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-213">This library provides access to ThreadX services in the resident code.</span></span> <span data-ttu-id="6d9fd-214">ほとんどのアクセスは ***txm_\*.c*** ファイルを介して行われます。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-214">Most of the access is accomplished via the ***txm_\*.c*** files.</span></span> <span data-ttu-id="6d9fd-215">次に示すのは、( _\*_ \_txm_thread_relinquish.c\*\*\*\* 内の) ThreadX API 関数 \**_tx_thread_relinquish_* _ に対するモジュール アクセス呼び出しの例です。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-215">The following is an example of the module access call for the ThreadX API function **_tx_thread_relinquish_* _ (in _*_\_txm_thread_relinquish.c\*\*\*\*).</span></span>

```c
(_txm_module_kernel_call_dispatcher)(TXM_THREAD_RELINQUISH_CALL, 0, 0, 0);
```

<span data-ttu-id="6d9fd-216">この例では、モジュール マネージャーによって提供された関数ポインターを使用して、***tx_thread_relinquish*** サービスに関連付けられた ID を持つ、モジュール マネージャーのディスパッチ関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-216">In this example, the function pointer supplied by the Module Manager is used to call the Module Manager dispatch function with the ID associated with the ***tx_thread_relinquish*** service.</span></span> <span data-ttu-id="6d9fd-217">このサービスはパラメーターを取りません。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-217">This service takes no parameters.</span></span>

## <a name="module-example"></a><span data-ttu-id="6d9fd-218">モジュールの例</span><span class="sxs-lookup"><span data-stu-id="6d9fd-218">Module example</span></span>

<span data-ttu-id="6d9fd-219">次に示すのは、モジュールの形式である標準 ThreadX デモンストレーションの例です。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-219">The following is an example of the standard ThreadX demonstration in the form of a module.</span></span> <span data-ttu-id="6d9fd-220">標準 ThreadX デモンストレーションとモジュール デモンストレーションの主な違いは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-220">The main differences between the standard ThreadX demonstration and the module demonstration are.</span></span>

1. <span data-ttu-id="6d9fd-221">***tx_api.h** _ を _ *_txm_module.h_** で置き換える</span><span class="sxs-lookup"><span data-stu-id="6d9fd-221">Replacement of ***tx_api.h** _ with _ *_txm_module.h_**</span></span>
2. <span data-ttu-id="6d9fd-222">**_txm_module.h_** の前に **#define TXM_MODULE** を追加する</span><span class="sxs-lookup"><span data-stu-id="6d9fd-222">Addition of **#define TXM_MODULE** prior to **_txm_module.h_**</span></span>
3. <span data-ttu-id="6d9fd-223">***main** _ と _ *tx_application_define** を **_demo_module_start_** で置き換える</span><span class="sxs-lookup"><span data-stu-id="6d9fd-223">Replacement of ***main** _ and _ *tx_application_define** with **_demo_module_start_**</span></span>
4. <span data-ttu-id="6d9fd-224">オブジェクト自体ではなく ThreadX オブジェクトへの *ポインター* を宣言する</span><span class="sxs-lookup"><span data-stu-id="6d9fd-224">Declaring *pointers* to ThreadX objects rather than the objects themselves.</span></span>

```c
/* Specify that this is a module! */
#define TXM_MODULE

/* Include the ThreadX module header. */
#include "txm_module.h"

/* Define constants. */
#define DEMO_STACK_SIZE         1024
#define DEMO_BYTE_POOL_SIZE     9120
#define DEMO_BLOCK_POOL_SIZE    100
#define DEMO_QUEUE_SIZE         100

/* Define the pool space in the bss section of the module. ULONG is used to
   get word alignment. */
   
ULONG                   demo_module_pool_space[DEMO_BYTE_POOL_SIZE / 4];

/* Define the ThreadX object control block pointers. */

TX_THREAD               *thread_0;
TX_THREAD               *thread_1;
TX_THREAD               *thread_2;
TX_THREAD               *thread_3;
TX_THREAD               *thread_4;
TX_THREAD               *thread_5;
TX_THREAD               *thread_6;
TX_THREAD               *thread_7;
TX_QUEUE                *queue_0;
TX_SEMAPHORE            *semaphore_0;
TX_MUTEX                *mutex_0;
TX_EVENT_FLAGS_GROUP    *event_flags_0;
TX_BYTE_POOL            *byte_pool_0;
TX_BLOCK_POOL           *block_pool_0;


/* Define the counters used in the demo application. */
ULONG       thread_0_counter;
ULONG       thread_1_counter;
ULONG       thread_1_messages_sent;
ULONG       thread_2_counter;
ULONG       thread_2_messages_received;
ULONG       thread_3_counter;
ULONG       thread_4_counter;
ULONG       thread_5_counter;
ULONG       thread_6_counter;
ULONG       thread_7_counter;
ULONG       semaphore_0_puts;
ULONG       event_0_sets;
ULONG       queue_0_sends;

/* Define thread prototypes. */

void    thread_0_entry(ULONG thread_input);
void    thread_1_entry(ULONG thread_input);
void    thread_2_entry(ULONG thread_input);
void    thread_3_and_4_entry(ULONG thread_input);
void    thread_5_entry(ULONG thread_input);
void    thread_6_and_7_entry(ULONG thread_input);

/* Define notify functions. */

void semaphore_0_notify(TX_SEMAPHORE *semaphore_ptr)
{
    if (semaphore_ptr == semaphore_0)
        semaphore_0_puts++;
}


void event_0_notify(TX_EVENT_FLAGS_GROUP *event_flag_group_ptr)
{
    if (event_flag_group_ptr == event_flags_0)
        event_0_sets++;
}


void queue_0_notify(TX_QUEUE *queue_ptr)
{
    if (queue_ptr == queue_0)
        queue_0_sends++;
}

/* Define the module start function. */
void demo_module_start(ULONG id)
{
    CHAR *pointer;

    /* Allocate all the objects. In memory protection mode,
        modules cannot allocate control blocks within their
        own memory area so they cannot corrupt the resident
        portion of ThreadX by corrupting the control block(s). */
    txm_module_object_allocate(&thread_0, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_1, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_2, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_3, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_4, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_5, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_6, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_7, sizeof(TX_THREAD));
    txm_module_object_allocate(&queue_0, sizeof(TX_QUEUE));
    txm_module_object_allocate(&semaphore_0, sizeof(TX_SEMAPHORE));
    txm_module_object_allocate(&mutex_0, sizeof(TX_MUTEX));
    txm_module_object_allocate(&event_flags_0, sizeof(TX_EVENT_FLAGS_GROUP));
    txm_module_object_allocate(&byte_pool_0, sizeof(TX_BYTE_POOL));
    txm_module_object_allocate(&block_pool_0, sizeof(TX_BLOCK_POOL));

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(byte_pool_0, "module byte pool 0",
        demo_module_pool_space, DEMO_BYTE_POOL_SIZE);

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 0. */
    tx_thread_create(thread_0, "module thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through
        a ThreadX message queue. It is also interesting to note that
        these threads have a time slice. */
    tx_thread_create(thread_1, "module thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack and create thread 2. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_2, "module thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX
        counting semaphore. An interesting thing here is that both threads
        share the same instruction area. */
    tx_thread_create(thread_3, "module thread 3",
        thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack and create thread 4. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_4, "module thread 4",
        thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag which
        will be set by thread 0. */
    tx_thread_create(thread_5, "module thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(thread_6, "module thread 6",
        thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack and create thread 7. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_7, "module thread 7",
        thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(queue_0, "module queue 0", TX_1_ULONG, pointer,
        DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Register queue send callback. */
    tx_queue_send_notify(queue_0, queue_0_notify);

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(semaphore_0, "module semaphore 0", 1);

    /* Register semaphore put callback. */
    tx_semaphore_put_notify(semaphore_0, semaphore_0_notify);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(event_flags_0, "module event flags 0");

    /* Register event flag set callback. */
    tx_event_flags_set_notify(event_flags_0, event_0_notify);

    /* Create the mutex used by thread 6 and 7 without priority
        inheritance. */
    tx_mutex_create(mutex_0, "module mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool. */
    tx_block_pool_create(block_pool_0, "module block pool 0",
        sizeof(ULONG), pointer, DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block. */
    tx_block_allocate(block_pool_0, (VOID **) &pointer,
        TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);

}

/* Define all the threads. */

void thread_0_entry(ULONG thread_input)
{
    UINT status;

    /* This thread simply sits in while-forever-sleep loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_0_counter++;

        /* Sleep for 10 ticks. */
        tx_thread_sleep(10);

        /* Set event flag 0 to wake up thread 5. */
        status = tx_event_flags_set(event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}

void thread_1_entry(ULONG thread_input)
{
    UINT status;

    /* This thread simply sends messages to a queue shared by
       thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(queue_0, &thread_1_messages_sent,
            TX_WAIT_FOREVER);

        /* Check completion status. */
        if (status != TX_SUCCESS)
            break;

        /* Increment the message sent. */
        thread_1_messages_sent++;
    }
}

void thread_2_entry(ULONG thread_input)
{
    ULONG received_message;
    UINT status;

    /* This thread retrieves messages placed on the queue by thread 1. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_2_counter++;

        /* Retrieve a message from the queue. */
        status = tx_queue_receive(queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what
           we expected. */
        if ((status != TX_SUCCESS) || (received_message != thread_2_messages_received))
            break;

        /* Otherwise, all is okay. Increment the received message count. */
        thread_2_messages_received++;
    }
}

void thread_3_and_4_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 3 and thread 4. As the loop
       below shows, these function compete for ownership of semaphore_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 3)
            thread_3_counter++;
        else
            thread_4_counter++;

        /* Get the semaphore with suspension. */
        status = tx_semaphore_get(semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(semaphore_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}

void thread_5_entry(ULONG thread_input)
{
    UINT status;
    ULONG actual_flags;

    /* This thread simply waits for an event in a forever loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_5_counter++;

        /* Wait for event flag 0. */
        status = tx_event_flags_get(event_flags_0, 0x1, TX_OR_CLEAR,
                                        &actual_flags, TX_WAIT_FOREVER);

        /* Check status. */
        if ((status != TX_SUCCESS) || (actual_flags != 0x1))
            break;
    }
}

void thread_6_and_7_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 6 and thread 7. As the loop
       below shows, these function compete for ownership of mutex_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 6)
            thread_6_counter++;
        else
            thread_7_counter++;

        /* Get the mutex with suspension. */
        status = tx_mutex_get(mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows that an
           owning thread may retrieve the mutex it owns multiple times. */
        status = tx_mutex_get(mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually release ownership
           since it was obtained twice. */
        status = tx_mutex_put(mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```

## <a name="building-modules"></a><span data-ttu-id="6d9fd-225">モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="6d9fd-225">Building Modules</span></span>

<span data-ttu-id="6d9fd-226">モジュールのビルドは、使用しているツール チェーンに依存します。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-226">Building a module is dependent on the tool chain being used.</span></span> <span data-ttu-id="6d9fd-227">ポート固有の例については[付録](appendix.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-227">See [appendix](appendix.md) for port-specific examples.</span></span> <span data-ttu-id="6d9fd-228">すべてのポートに共通のアクティビティには、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-228">Common activities to all ports include the following.</span></span>

- <span data-ttu-id="6d9fd-229">モジュール ライブラリのビルド</span><span class="sxs-lookup"><span data-stu-id="6d9fd-229">Building a module library</span></span>
- <span data-ttu-id="6d9fd-230">モジュール アプリケーションのビルド</span><span class="sxs-lookup"><span data-stu-id="6d9fd-230">Building the module application</span></span>

<span data-ttu-id="6d9fd-231">各モジュールは、(特にそのモジュールのために設定された) **txm_module_preamble** と、モジュール ライブラリ (例: **_txm.a_**) を備えている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9fd-231">Each module is required to have a **txm_module_preamble** (setup specifically for the module) and the module library (for example, **_txm.a_**).</span></span>
