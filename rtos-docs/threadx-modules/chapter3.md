---
title: 第 3 章 - モジュール マネージャーの要件
description: この記事では、ThreadX モジュール マネージャーをビルドするために必要な手順について説明します。
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e8ea1a05096b5975de203648fddfb19c1a6105e0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811411"
---
# <a name="chapter-3---module-manager-requirements"></a><span data-ttu-id="9ab2c-103">第 3 章 - モジュール マネージャーの要件</span><span class="sxs-lookup"><span data-stu-id="9ab2c-103">Chapter 3 - Module Manager requirements</span></span>

<span data-ttu-id="9ab2c-104">ThreadX モジュール マネージャーは、ThreadX の RTO と共にアプリケーションの常駐部分に存在します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-104">The ThreadX Module Manager resides in the resident portion of the application along with the ThreadX RTOS.</span></span> <span data-ttu-id="9ab2c-105">これは、モジュールを起動し、ThreadX API サービスのすべてのモジュール要求をフィールディングしてディスパッチする役割を担います。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-105">It is responsible for starting the module as well as fielding and dispatching all module requests for ThreadX API services.</span></span>

> [!NOTE]
> <span data-ttu-id="9ab2c-106">ThreadX モジュール **マネージャー** のソース ファイル (C とアセンブリ) を Threadx ライブラリ プロジェクト "**tx**" に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-106">The ThreadX Module **Manager** source files (C and assembly) should be added to the ThreadX library project "**tx**".</span></span>

<span data-ttu-id="9ab2c-107">ThreadX モジュール マネージャーをビルドするには、以下の手順が必要です (それぞれの手順については、以下で詳しく説明します)。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-107">The following steps are required for building the ThreadX Module Manager (each step is described in greater detail below).</span></span>

1. <span data-ttu-id="9ab2c-108">モジュール情報を含めるには、**TX_THREAD** 制御ブロックを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-108">The **TX_THREAD** control block must be extended to include module information.</span></span> <span data-ttu-id="9ab2c-109">これを実現する最も簡単な方法は、**_tx_port.h_\*ファイル内の **TX_THREAD_EXTENSION_2** の定義を、**_txm_module_port.h_\*\* で見つかった\* TX_THREAD_EXTENSION_2\*\* に置き換えることです。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-109">The easiest way to accomplish this is to replace the definition of **TX_THREAD_EXTENSION_2** in the **_tx_port.h_*_ file with the _\* TX_THREAD_EXTENSION_2*\* found in **_txm_module_port.h_**.</span></span> <span data-ttu-id="9ab2c-110">ポート固有の拡張機能については[付録](appendix.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-110">See [appendix](appendix.md) for port-specific extensions.</span></span>

<span data-ttu-id="9ab2c-111">拡張機能の例:</span><span class="sxs-lookup"><span data-stu-id="9ab2c-111">Example extension:</span></span>

   ```c
   #define TX_THREAD_EXTENSION_2                     \
       VOID      tx_thread_module_instance_ptr;      \
       VOID      tx_thread_module_entry_info_ptr;    \
       ULONG     tx_thread_module_current_user_mode; \
       ULONG     tx_thread_module_user_mode;         \
       VOID     *tx_thread_module_kernel_stack_start;\
       VOID     *tx_thread_module_kernel_stack_end;  \
       ULONG     tx_thread_module_kernel_stack_size; \
       VOID     *tx_thread_module_stack_ptr;         \
       VOID     *tx_thread_module_stack_start;       \
       VOID     *tx_thread_module_stack_end;         \
       ULONG     tx_thread_module_stack_size;        \
       VOID     *tx_thread_module_reserved;
   ```

   <span data-ttu-id="9ab2c-112">次の拡張機能は ***tx_port.h*** で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-112">The following extensions must be defined in ***tx_port.h***.</span></span>

   ```c
   #define TX_EVENT_FLAGS_GROUP_EXTENSION  VOID    *tx_event_flags_group_module_instance; \
        VOID   (*tx_event_flags_group_set_module_notify)(struct TX_EVENT_FLAGS_GROUP_STRUCT *group_ptr);

   #define TX_QUEUE_EXTENSION              VOID    *tx_queue_module_instance; \
        VOID   (*tx_queue_send_module_notify)(struct TX_QUEUE_STRUCT *queue_ptr);

   #define TX_SEMAPHORE_EXTENSION          VOID    *tx_semaphore_module_instance; \
        VOID   (*tx_semaphore_put_module_notify)(struct TX_SEMAPHORE_STRUCT *semaphore_ptr);

   #define TX_TIMER_EXTENSION              VOID    *tx_timer_module_instance; \
        VOID   (*tx_timer_module_expiration_function)(ULONG id);
   ```

2. <span data-ttu-id="9ab2c-113">すべての ***txm_module_manager_\**** C とアセンブリ ファイルを ThreadX ライブラリ プロジェクト **_tx_** に追加します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-113">Add all the ***txm_module_manager_\**** C and assembly files to the ThreadX library project **_tx_**.</span></span>
3. <span data-ttu-id="9ab2c-114">すべてのライブラリと実行可能なプロジェクトをリビルドします。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-114">Rebuild all libraries and executable projects.</span></span> <span data-ttu-id="9ab2c-115">NetX Duo が必要な場合は、**TXM_MODULE_ENABLE_NETX_DUO** を定義して、すべてのモジュールとモジュール マネージャーの C コードをビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-115">If NetX Duo is required, all Module and Module Manager C code should be built with **TXM_MODULE_ENABLE_NETX_DUO** defined.</span></span>

## <a name="module-manager-sources"></a><span data-ttu-id="9ab2c-116">モジュール マネージャーのソース</span><span class="sxs-lookup"><span data-stu-id="9ab2c-116">Module Manager sources</span></span>

<span data-ttu-id="9ab2c-117">ThreadX モジュール マネージャーには、ソース ファイルのセットがあります。これは、常駐する ThreadX コードにリンクされ直接配置されるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-117">The ThreadX Module Manager has a set of source files that are designed to be linked and located directly with the resident ThreadX code.</span></span> <span data-ttu-id="9ab2c-118">これらのファイルには、モジュールを起動し、以降の ThreadX API 要求をそのモジュールからフィールディングする機能があります。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-118">These files provide the ability to launch a module and field subsequent ThreadX API requests from the module.</span></span> <span data-ttu-id="9ab2c-119">モジュール マネージャーのファイルは以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-119">The module manager files are as follows.</span></span>

| <span data-ttu-id="9ab2c-120">**[ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="9ab2c-120">**File Name**</span></span> |  <span data-ttu-id="9ab2c-121">**Contents**</span><span class="sxs-lookup"><span data-stu-id="9ab2c-121">**Contents**</span></span> |
|-------------- | ------------- |
| <span data-ttu-id="9ab2c-122">***txm_module.h***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-122">***txm_module.h***</span></span> | <span data-ttu-id="9ab2c-123">モジュール情報を定義するインクルード ファイル (モジュールのソース コードにも含まれます)。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-123">Include file that defines module information (also included in the module source code).</span></span> |
| <span data-ttu-id="9ab2c-124">***txm_module_manager_dispatch.h***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-124">***txm_module_manager_dispatch.h***</span></span> | <span data-ttu-id="9ab2c-125">ディスパッチ ヘルパー関数を定義するインクルード ファイル。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-125">Include file that defines dispatch helper functions.</span></span>|
| <span data-ttu-id="9ab2c-126">***txm_module_manager_util.h***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-126">***txm_module_manager_util.h***</span></span> | <span data-ttu-id="9ab2c-127">内部的なユーティリティ ヘルパー マクロと関数を定義するインクルード ファイル。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-127">Include file that defines internal utility helper macros & functions.</span></span> |
| <span data-ttu-id="9ab2c-128">***txm_module_port.h***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-128">***txm_module_port.h***</span></span> | <span data-ttu-id="9ab2c-129">ポート固有のモジュール情報を定義するインクルード ファイル (モジュールのソース コードにも含まれます)。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-129">Include file that defines port-specific module information (also included in the module source code).</span></span> |
| <span data-ttu-id="9ab2c-130">\***tx_initialize_low_level.\[s,S,68\]** _</span><span class="sxs-lookup"><span data-stu-id="9ab2c-130">\***tx_initialize_low_level.\[s,S,68\]** _</span></span> | <span data-ttu-id="9ab2c-131">既存の ThreadX ライブラリ ファイルを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-131">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="9ab2c-132">モジュール マネージャーとメモリ例外のために更新されたベクトル テーブルと、追加のベクトル ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-132">Updated vector table and additional vector handlers for module manager and memory exceptions.</span></span> <span data-ttu-id="9ab2c-133">このファイルは、Cortex-A7/ARM、Cortex-M7/ARM、Cortex-R4/ARM、Cortex-R4/IAR、MCF544xx/GHS、RX63/IAR、RX65N/IAR にのみ存在します。\*</span><span class="sxs-lookup"><span data-stu-id="9ab2c-133">_This file is only in Cortex-A7/ARM, Cortex-M7/ARM, Cortex-R4/ARM, Cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR.\*</span></span>|
| <span data-ttu-id="9ab2c-134">\***tx_thread_context_restore.s** _</span><span class="sxs-lookup"><span data-stu-id="9ab2c-134">\***tx_thread_context_restore.s** _</span></span> | <span data-ttu-id="9ab2c-135">既存の ThreadX ライブラリ ファイルを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-135">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="9ab2c-136">割り込み処理後にスレッド コンテキストを復元します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-136">Restore thread context after interrupt processing.</span></span> <span data-ttu-id="9ab2c-137">このファイルは Cortex-A7/ARM、Cortex-R4/ARM、Cortex-R4/IAR にのみ存在します。\*</span><span class="sxs-lookup"><span data-stu-id="9ab2c-137">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="9ab2c-138">***tx_thread_schedule.\[s,S,68\]***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-138">***tx_thread_schedule.\[s,S,68\]***</span></span> | <span data-ttu-id="9ab2c-139">既存の ThreadX ライブラリ ファイルを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-139">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="9ab2c-140">拡張されたスケジューラ コード。この場合は、メモリ管理レジスタを更新するために使用します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-140">Extended scheduler code, which in this case is used to update memory management registers.</span></span> |
| <span data-ttu-id="9ab2c-141">\***tx_thread_stack_build.s** _</span><span class="sxs-lookup"><span data-stu-id="9ab2c-141">\***tx_thread_stack_build.s** _</span></span> | <span data-ttu-id="9ab2c-142">既存の ThreadX ライブラリ ファイルを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-142">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="9ab2c-143">スレッドのスタック フレームをビルドします。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-143">Builds the stack frame of a thread.</span></span> <span data-ttu-id="9ab2c-144">このファイルは Cortex-A7/ARM、Cortex-R4/ARM、Cortex-R4/IAR にのみ存在します。\*</span><span class="sxs-lookup"><span data-stu-id="9ab2c-144">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="9ab2c-145">***txm_module_manager_thread_stack_build.\[s,S,68\]***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-145">***txm_module_manager_thread_stack_build.\[s,S,68\]***</span></span> | <span data-ttu-id="9ab2c-146">すべてのモジュール初期スタックをビルドし、位置に依存しないデータ アクセスのセットアップをインクルードします。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-146">Builds all module initial stacks, includes setup for position-independent data access.</span></span> |
| <span data-ttu-id="9ab2c-147">\***txm_module_manager_user_mode_entry.\[s,S\]** _</span><span class="sxs-lookup"><span data-stu-id="9ab2c-147">\***txm_module_manager_user_mode_entry.\[s,S\]** _</span></span> | <span data-ttu-id="9ab2c-148">モジュールがカーネル モードに入ることを許可します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-148">Allows the module to enter kernel mode.</span></span> <span data-ttu-id="9ab2c-149">このファイルは Cortex-A7/ARM、Cortex-R4/ARM、Cortex-R4/IAR にのみ存在します。\*</span><span class="sxs-lookup"><span data-stu-id="9ab2c-149">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="9ab2c-150">***txm_module_manager_alignment_adjust.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-150">***txm_module_manager_alignment_adjust.c***</span></span> | <span data-ttu-id="9ab2c-151">ポート固有のアラインメント要件を処理します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-151">Handles port-specific alignment requirements.</span></span>|
| <span data-ttu-id="9ab2c-152">***txm_module_manager_application_request.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-152">***txm_module_manager_application_request.c***</span></span> | <span data-ttu-id="9ab2c-153">常駐コードに対するアプリケーション固有の要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-153">Handles the application-specific requests to the resident code.</span></span> |
| <span data-ttu-id="9ab2c-154">***txm_module_manager_callback_request.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-154">***txm_module_manager_callback_request.c***</span></span> | <span data-ttu-id="9ab2c-155">コールバック要求をモジュールに送信します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-155">Sends a callback request to a module.</span></span> |
| <span data-ttu-id="9ab2c-156">***txm_module_manager_event_flags_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-156">***txm_module_manager_event_flags_notify_trampoline.c***</span></span> | <span data-ttu-id="9ab2c-157">ThreadX からのイベント フラグ設定通知呼び出しを処理します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-157">Processes the event flags set notification call from ThreadX.</span></span> |
| <span data-ttu-id="9ab2c-158">***txm_module_manager_external_memory_enable.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-158">***txm_module_manager_external_memory_enable.c***</span></span> | <span data-ttu-id="9ab2c-159">モジュールがアクセスできる共有メモリ空間のエントリを、メモリ管理テーブルに作成します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-159">Creates an entry in the memory management table for a shared memory space the module can access.</span></span> |
| <span data-ttu-id="9ab2c-160">***txm_module_manager_file_load.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-160">***txm_module_manager_file_load.c***</span></span> | <span data-ttu-id="9ab2c-161">バイナリ モジュール ファイルを割り当ててモジュールのメモリ領域に読み込み、実行できるように準備します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-161">Allocates and loads a binary module file into the module memory area and prepares it for execution.</span></span> |
| <span data-ttu-id="9ab2c-162">***txm_module_manager_in_place_load.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-162">***txm_module_manager_in_place_load.c***</span></span> | <span data-ttu-id="9ab2c-163">モジュール データ領域を割り当て、指定されたコード アドレスからのモジュール実行を準備します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-163">Allocates the module data area and prepares for module execution from the supplied code address.</span></span> |
| <span data-ttu-id="9ab2c-164">***txm_module_manager_initialize.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-164">***txm_module_manager_initialize.c***</span></span> | <span data-ttu-id="9ab2c-165">モジュールの読み込みと実行に使用できるモジュール メモリ領域を指定するなど、モジュール マネージャーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-165">Initializes the Module Manager, including specification of the module memory area available for loading and running modules.</span></span> |
| <span data-ttu-id="9ab2c-166">\***txm_module_manager_initialize_mmu.c** _</span><span class="sxs-lookup"><span data-stu-id="9ab2c-166">\***txm_module_manager_initialize_mmu.c** _</span></span> | <span data-ttu-id="9ab2c-167">MMU を初期化します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-167">Initialize MMU.</span></span> <span data-ttu-id="9ab2c-168">ユーザーは、それぞれのメモリ マップに従ってこのファイルを編集できます。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-168">Users can edit this file according to their memory map.</span></span> <span data-ttu-id="9ab2c-169">このファイルは Cortex-A7/ARM にのみ存在します\*</span><span class="sxs-lookup"><span data-stu-id="9ab2c-169">_This file is only in Cortex-A7/ARM\*</span></span> |
| <span data-ttu-id="9ab2c-170">\***txm_module_manager_mm_initialize.c** _</span><span class="sxs-lookup"><span data-stu-id="9ab2c-170">\***txm_module_manager_mm_initialize.c** _</span></span> | <span data-ttu-id="9ab2c-171">MPU/MMU を初期化します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-171">Initialize MPU/MMU.</span></span> <span data-ttu-id="9ab2c-172">ユーザーは、それぞれのメモリ マップに従ってこのファイルを編集できます。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-172">Users can edit this file according to their memory map.</span></span> <span data-ttu-id="9ab2c-173">このファイルは Cortex-A7/ARM にのみ存在します\*</span><span class="sxs-lookup"><span data-stu-id="9ab2c-173">_This file is only in Cortex-A7/ARM\*</span></span> |
| <span data-ttu-id="9ab2c-174">***txm_module_manager_kernel_dispatch.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-174">***txm_module_manager_kernel_dispatch.c***</span></span> | <span data-ttu-id="9ab2c-175">要求 ID に基づいて、モジュールの API 要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-175">Handles the module API requests, based on the request ID.</span></span> |
| <span data-ttu-id="9ab2c-176">***txm_module_manager_maximum_module_priority_set.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-176">***txm_module_manager_maximum_module_priority_set.c***</span></span> | <span data-ttu-id="9ab2c-177">モジュールで許可されるスレッドの最大優先度を設定します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-177">Sets the maximum thread priority allowed in a module.</span></span> |
| <span data-ttu-id="9ab2c-178">***txm_module_manager_memory_fault_handler.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-178">***txm_module_manager_memory_fault_handler.c***</span></span> | <span data-ttu-id="9ab2c-179">実行中のモジュールで検出されたメモリ エラーを処理します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-179">Handles memory faults detected in an executing module.</span></span> |
| <span data-ttu-id="9ab2c-180">***txm_module_manager_memory_fault_notify.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-180">***txm_module_manager_memory_fault_notify.c***</span></span> | <span data-ttu-id="9ab2c-181">メモリ エラーが発生するたびに、アプリケーション通知コールバックを登録します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-181">Registers an application notification callback whenever a memory fault occurs.</span></span> |
| <span data-ttu-id="9ab2c-182">***txm_module_manager_memory_load.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-182">***txm_module_manager_memory_load.c***</span></span> | <span data-ttu-id="9ab2c-183">モジュールのコードとデータを割り当てて読み込み、実行するモジュールを準備します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-183">Allocates and loads a module's code and data and prepares the module for execution.</span></span> |
| <span data-ttu-id="9ab2c-184">***txm_module_manager_mm_register_setup.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-184">***txm_module_manager_mm_register_setup.c***</span></span> | <span data-ttu-id="9ab2c-185">コードとデータが読み込まれる場所に基づいて、モジュールの MPU/MMU レジスタを設定します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-185">Sets up MPU/MMU registers for the module based on where the code and data are loaded.</span></span> |
| <span data-ttu-id="9ab2c-186">***txm_module_manager_object_allocate.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-186">***txm_module_manager_object_allocate.c***</span></span> | <span data-ttu-id="9ab2c-187">モジュール オブジェクトのメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-187">Allocates memory for a module object.</span></span> |
| <span data-ttu-id="9ab2c-188">***txm_module_manager_object_deallocate.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-188">***txm_module_manager_object_deallocate.c***</span></span> | <span data-ttu-id="9ab2c-189">モジュール オブジェクトのメモリの割り当てを解除します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-189">Deallocates memory for a module object.</span></span> |
| <span data-ttu-id="9ab2c-190">***txm_module_manager_object_pointer_get.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-190">***txm_module_manager_object_pointer_get.c***</span></span> | <span data-ttu-id="9ab2c-191">指定されたオブジェクトの種類と名前を検索し、見つかった場合はオブジェクト ポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-191">Searches for the supplied object type and name, and if found, returns the object pointer.</span></span> |
| <span data-ttu-id="9ab2c-192">***txm_module_manager_object_pointer_get_extended.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-192">***txm_module_manager_object_pointer_get_extended.c***</span></span> | <span data-ttu-id="9ab2c-193">指定されたオブジェクトの種類と名前を検索し、見つかった場合はオブジェクト ポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-193">Searches for the supplied object type and name, and if found, returns the object pointer.</span></span> <span data-ttu-id="9ab2c-194">安全のために指定された名前の長さ。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-194">Name length specified for safety.</span></span> |
| <span data-ttu-id="9ab2c-195">***txm_module_manager_object_pool_create.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-195">***txm_module_manager_object_pool_create.c***</span></span>  | <span data-ttu-id="9ab2c-196">モジュール アプリケーションが割り当て元にできる、モジュールのデータ領域の外側に、オブジェクトのプールを作成します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-196">Creates a pool of objects outside the module's data area that module applications can allocate from.</span></span> |
| <span data-ttu-id="9ab2c-197">***txm_module_manager_properties_get.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-197">***txm_module_manager_properties_get.c***</span></span> | <span data-ttu-id="9ab2c-198">指定されたモジュールのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-198">Gets the properties of the specified module.</span></span> |
| <span data-ttu-id="9ab2c-199">***txm_module_manager_queue_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-199">***txm_module_manager_queue_notify_trampoline.c***</span></span> | <span data-ttu-id="9ab2c-200">ThreadX からのキュー通知呼び出しを処理します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-200">Processes the queue notification call from ThreadX.</span></span> |
| <span data-ttu-id="9ab2c-201">***txm_module_manager_semaphore_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-201">***txm_module_manager_semaphore_notify_trampoline.c***</span></span> | <span data-ttu-id="9ab2c-202">ThreadX からのセマフォ put 通知呼び出しを処理します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-202">Processes the semaphore put notification call from ThreadX.</span></span>|
| <span data-ttu-id="9ab2c-203">***txm_module_manager_start.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-203">***txm_module_manager_start.c***</span></span> | <span data-ttu-id="9ab2c-204">モジュールの実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-204">Starts execution of a module.</span></span> |
| <span data-ttu-id="9ab2c-205">***txm_module_manager_stop.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-205">***txm_module_manager_stop.c***</span></span> | <span data-ttu-id="9ab2c-206">モジュールの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-206">Stops execution of a module.</span></span> |
| <span data-ttu-id="9ab2c-207">***txm_module_manager_thread_create.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-207">***txm_module_manager_thread_create.c***</span></span> | <span data-ttu-id="9ab2c-208">すべてのモジュール スレッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-208">Creates all module threads.</span></span> |
| <span data-ttu-id="9ab2c-209">***txm_module_manager_thread_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-209">***txm_module_manager_thread_notify_trampoline.c***</span></span> | <span data-ttu-id="9ab2c-210">ThreadX からのスレッド開始/終了通知呼び出しを処理します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-210">Processes the thread entry/exit notification call from ThreadX.</span></span> |
| <span data-ttu-id="9ab2c-211">***txm_module_manager_thread_reset.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-211">***txm_module_manager_thread_reset.c***</span></span> | <span data-ttu-id="9ab2c-212">モジュール スレッドをリセットします。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-212">Reset a module thread.</span></span> |
| <span data-ttu-id="9ab2c-213">***txm_module_manager_timer_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-213">***txm_module_manager_timer_notify_trampoline.c***</span></span> | <span data-ttu-id="9ab2c-214">ThreadX からのタイマー有効期限を処理します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-214">Processes timer expirations from ThreadX.</span></span> |
| <span data-ttu-id="9ab2c-215">***txm_module_manager_unload.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-215">***txm_module_manager_unload.c***</span></span> | <span data-ttu-id="9ab2c-216">モジュールのメモリ領域からモジュールをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-216">Unloads the module from the module memory area.</span></span> |
| <span data-ttu-id="9ab2c-217">***txm_module_manager_util.c***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-217">***txm_module_manager_util.c***</span></span> | <span data-ttu-id="9ab2c-218">マネージャーの内部ヘルパー関数。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-218">Internal helper functions for manager.</span></span> |

## <a name="module-manager-initialization"></a><span data-ttu-id="9ab2c-219">モジュール マネージャーの初期化</span><span class="sxs-lookup"><span data-stu-id="9ab2c-219">Module Manager initialization</span></span>

<span data-ttu-id="9ab2c-220">アプリケーションの常駐部分は、モジュール マネージャー初期化関数 ***txm_module_manager_initialize*** を呼び出す役割を担います。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-220">The resident portion of the application is responsible for calling the Module Manager initialization function ***txm_module_manager_initialize***.</span></span> <span data-ttu-id="9ab2c-221">この関数は、モジュール メモリの割り当てに使用されるメモリ領域を設定するなど、モジュールの読み込みとアンロードのための内部構造を設定します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-221">This function sets up the internal structures for loading and unloading modules, including setting up the memory area used for allocating module memory.</span></span>

## <a name="module-manager-loading"></a><span data-ttu-id="9ab2c-222">モジュール マネージャーの読み込み</span><span class="sxs-lookup"><span data-stu-id="9ab2c-222">Module Manager loading</span></span>

<span data-ttu-id="9ab2c-223">モジュール マネージャーは、バイナリ モジュール ファイルから、または常駐コード領域に既に存在するモジュール コード セクションから、モジュール メモリにモジュールを動的に読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-223">The Module Manager can load modules dynamically into the module memory from binary module files or from a module code section that is already present in the resident code area.</span></span> <span data-ttu-id="9ab2c-224">また、モジュール マネージャーはコードを適切に実行できます。つまり、モジュール データのみがモジュール メモリに割り当てられ、コードの実行が適切に実行されます。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-224">In addition, the module manager can execute code in place, that is, only the module data is allocated in the module memory and the code execution is done in place.</span></span> <span data-ttu-id="9ab2c-225">次のモジュール マネージャー読み込み API 関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-225">The following Module Manager load API functions are available.</span></span>

* <span data-ttu-id="9ab2c-226">***txm_module_manager_file_load***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-226">***txm_module_manager_file_load***</span></span>

* <span data-ttu-id="9ab2c-227">***txm_module_manager_in_place_load***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-227">***txm_module_manager_in_place_load***</span></span>

* <span data-ttu-id="9ab2c-228">***txm_module_manager_memory_load***</span><span class="sxs-lookup"><span data-stu-id="9ab2c-228">***txm_module_manager_memory_load***</span></span>

<span data-ttu-id="9ab2c-229">メモリ保護されたバージョンのモジュール マネージャーでは、モジュールに適切なアラインメントが読み込まれていることと、メモリ管理レジスタがモジュールごとに適切に設定されていることも確認されます。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-229">The memory protected version of the Module Manager also makes sure that the module is loaded with the proper alignment and the memory management registers are set up properly for each module.</span></span> <span data-ttu-id="9ab2c-230">モジュール プリアンブル オプションを使用してメモリ保護を有効にすると、モジュール メモリ アクセスはモジュール コードとデータ領域に制限されます。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-230">When memory protection is enabled via the module preamble options, module memory access is restricted to the module code and data areas.</span></span>

## <a name="module-manager-starting"></a><span data-ttu-id="9ab2c-231">Module Manager の開始</span><span class="sxs-lookup"><span data-stu-id="9ab2c-231">Module Manager starting</span></span>

<span data-ttu-id="9ab2c-232">モジュール マネージャーは、***txm_module_manager_start*** API 関数を使用して、以前に読み込まれたモジュールの実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-232">The Module Manager initiates execution of a previously-loaded module via the ***txm_module_manager_start*** API function.</span></span> <span data-ttu-id="9ab2c-233">モジュールの実行を開始するために、この関数は、モジュール プリアンブルで指定された開始位置にモジュールに入るスレッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-233">To initiate module execution, this function creates a thread that enters the module at the starting location specified in the module preamble.</span></span> <span data-ttu-id="9ab2c-234">このスレッドの優先度とスタック サイズは、モジュール プリアンブルでも指定されています。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-234">The priority and stack size of this thread is also specified in the module preamble.</span></span>

## <a name="module-manager-stopping"></a><span data-ttu-id="9ab2c-235">モジュール マネージャーの停止</span><span class="sxs-lookup"><span data-stu-id="9ab2c-235">Module Manager stopping</span></span>

<span data-ttu-id="9ab2c-236">モジュール マネージャーは、***txm_module_manager_stop*** 関数を使用して、以前に読み込まれ実行中のモジュールの実行を終了します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-236">The Module Manager terminates execution of a previously-loaded and executing module via the ***txm_module_manager_stop*** function.</span></span> <span data-ttu-id="9ab2c-237">この API 関数は、最初に開始されているスレッドをまず終了して削除します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-237">This API function first terminates and deletes the initial starting thread.</span></span> <span data-ttu-id="9ab2c-238">モジュール プリアンブルに停止スレッドが指定されている場合、このスレッドが作成されて実行されます。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-238">If the module preamble specifies a stop thread, this thread is created and executed.</span></span> <span data-ttu-id="9ab2c-239">モジュール マネージャーは、停止スレッドが完了するまで一定期間待機します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-239">The Module Manager waits for a fixed period of time for the stop thread to complete.</span></span> <span data-ttu-id="9ab2c-240">完了すると、モジュールによって作成されたすべてのシステム リソースが削除され、モジュールは休止状態になります。この状態から、再起動またはアンロードできます。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-240">Once complete, all system resources created by the module are deleted and the module is placed in a dormant state, from which it can be either restarted or unloaded.</span></span>

## <a name="module-manager-unloading"></a><span data-ttu-id="9ab2c-241">モジュール マネージャーのアンロード</span><span class="sxs-lookup"><span data-stu-id="9ab2c-241">Module Manager unloading</span></span>

<span data-ttu-id="9ab2c-242">モジュール マネージャーは、以前に読み込まれたが実行中ではないモジュールを、***txm_module_manager_unload*** 関数を介してアンロードします。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-242">The Module Manager unloads a previously-loaded but not executing module via the ***txm_module_manager_unload*** function.</span></span> <span data-ttu-id="9ab2c-243">この API は、モジュールに関連付けられているすべてのメモリをリリースし、これ以降に別のモジュールで使用できるように解放します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-243">This API releases all memory associated with the module, freeing it for use with another module in the future.</span></span>

## <a name="module-manager-requests"></a><span data-ttu-id="9ab2c-244">モジュール マネージャーの要求</span><span class="sxs-lookup"><span data-stu-id="9ab2c-244">Module Manager requests</span></span>

<span data-ttu-id="9ab2c-245">モジュールによって行われるモジュール マネージャーへの要求は、***txm_module.h*** に含まれるマクロを使用して実行されます。このマクロは ThreadX 呼び出しをマップして、モジュール マネージャーによってモジュールに指定された関数ポインターを介してモジュール マネージャー ディスパッチ関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-245">Requests made by modules to the Module Manager are done via macros in ***txm_module.h*** that map all ThreadX calls to call the Module Manager dispatch function via a function pointer supplied to the module by the Module Manager.</span></span>

<span data-ttu-id="9ab2c-246">***txm_module_application_request*** を呼び出すモジュールを介して実行されるアプリケーション固有の追加サービスは、ThreadX API のために使用されるのと同じマクロの仕組みによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-246">Additional application-specific services made via the module calling ***txm_module_application_request*** are handled by the same macro mechanism used for the ThreadX API.</span></span> <span data-ttu-id="9ab2c-247">既定では、モジュール マネージャーのこの処理関数は空であり、アプリケーション固有の要求を処理するために必要なコードがアプリケーションで追加されるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-247">By default, this handling function in the Module Manager is empty and designed such that the application adds the necessary code to process the application-specific requests.</span></span>

<span data-ttu-id="9ab2c-248">モジュール マネージャーによって要求が実装されない場合は、モジュール マネージャーによって **TX_NOT_AVAILABLE** エラー状態の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-248">If the request is not implemented by the Module Manager, a value of **TX_NOT_AVAILABLE** error status is returned by the Module Manager.</span></span> <span data-ttu-id="9ab2c-249">このエラー コードは、モジュールのアクセス権の範囲外にある操作をモジュールが要求した場合にも返されます。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-249">This error code is also returned if the module requests an operation that is outside the scope of the module's access.</span></span> <span data-ttu-id="9ab2c-250">たとえば、モジュールは、モジュールのコード領域の外部にあるタイマー制御ブロックまたはコールバック アドレスを使用してタイマーを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-250">For example, a module is not allowed to create a timer with the timer control block or callback address outside of the module's code area.</span></span>

## <a name="module-manager-example"></a><span data-ttu-id="9ab2c-251">モジュール マネージャーの例</span><span class="sxs-lookup"><span data-stu-id="9ab2c-251">Module Manager example</span></span>

<span data-ttu-id="9ab2c-252">次に示すのは、前に第 2 章で定義したサンプル モジュールを起動するモジュール マネージャー コードの例です。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-252">The following is an example of Module Manager code that launches the example module previously defined in Chapter 2.</span></span> <span data-ttu-id="9ab2c-253">このモジュールは、たとえばデバッガーによって、ROM アドレス 0x00800000 に既に読み込まれていると仮定しています。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-253">It is assumed that the module is already loaded, presumably by the debugger, at ROM address 0x00800000.</span></span>

```c
#include "tx_api.h"
#include "txm_module.h"

#define DEMO_STACK_SIZE 1024

/* Define the ThreadX object control blocks. */
TX_THREAD   module_manager;

/* Define thread prototype. */
void        module_manager_entry(ULONG thread_input);

/* Define the module object pool area. */
UCHAR       object_memory[8192];

/* Define the module data pool area. */
#define MODULE_DATA_SIZE 65536
UCHAR       module_data_area[MODULE_DATA_SIZE];

/* Define module instances. */
TXM_MODULE_INSTANCE     my_module1;
TXM_MODULE_INSTANCE     my_module2;

/* Define the count of memory faults. */
ULONG memory_faults;

/* Define fault handler. */
VOID module_fault_handler(TX_THREAD *thread, TXM_MODULE_INSTANCE *module)
{
    /* Just increment the fault counter. */
    memory_faults++;
}

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{
    /* Create the module manager thread. */
    tx_thread_create(&module_manager, "Module Manager Thread", module_manager_entry, 0,
                    first_unused_memory, DEMO_STACK_SIZE,
                    1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

/* Define the test threads. */
void module_manager_entry(ULONG thread_input)
{
    /* Initialize the module manager. */
    txm_module_manager_initialize((VOID *) module_data_area, MODULE_DATA_SIZE);

    /* Create a pool for module objects. */
    txm_module_manager_object_pool_create(object_memory, sizeof(object_memory));

    /* Register a fault handler. */
    txm_module_manager_memory_fault_notify(module_fault_handler);

    /* Load the module that is already there,
        in this example it is placed at 0x00800000. */
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Load a second instance of the module. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);

    /* Enable shared memory region for module2. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);

    /* Start the modules. */
    txm_module_manager_start(&my_module1);
    txm_module_manager_start(&my_module2);

    /* Sleep for a while and let the modules run... */
    tx_thread_sleep(300);

    /* Stop the modules. */
    txm_module_manager_stop(&my_module1);
    txm_module_manager_stop(&my_module2);

    /* Unload the modules. */
    txm_module_manager_unload(&my_module1);
    txm_module_manager_unload(&my_module2);

    /* Reload the modules. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Give both modules shared memory. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);
    txm_module_manager_external_memory_enable(&my_module1, (void*)0x20600000, 0x010000, 0x3F);

    /* Set maximum module1 priority to 5. */
    txm_module_manager_maximum_module_priority_set(&my_module1, 5);

    /* Start the modules again. */
    txm_module_manager_start(&my_module2);
    txm_module_manager_start(&my_module1);

    /* Now just spin... */
    while(1)
    {
        tx_thread_sleep(100);

        /* Threads 0 and 5 in module1 are not created because they violate the maximum priority. */
    }
}
```

## <a name="module-manager-building"></a><span data-ttu-id="9ab2c-254">モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="9ab2c-254">Module Manager building</span></span>

<span data-ttu-id="9ab2c-255">***txm_module_manager_\**** ソース ファイルを ThreadX ライブラリに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-255">The ***txm_module_manager_\**** source files must be added to the ThreadX library.</span></span>

<span data-ttu-id="9ab2c-256">ThreadX モジュール マネージャー アプリケーションは、標準の ThreadX アプリケーションと実質的に同じで、これは ThreadX ライブラリ ***tx.a*** を使用してリンクされた 1 つ以上のアプリケーション ファイルです。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-256">A ThreadX Module Manager application is effectively the same as a standard ThreadX application, which is one or more application files linked together with the ThreadX library ***tx.a***.</span></span> <span data-ttu-id="9ab2c-257">モジュール マネージャー アプリケーションのビルドは、使用されているツール チェーンに依存します。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-257">Building a module manager application is dependent on the tool chain being used.</span></span> <span data-ttu-id="9ab2c-258">ポート固有の例については[付録](appendix.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ab2c-258">See [appendix](appendix.md) for port-specific examples.</span></span>
