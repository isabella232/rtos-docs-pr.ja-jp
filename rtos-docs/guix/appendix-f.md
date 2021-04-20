---
title: 付録 F - GUIX RTOS バインド サービス
description: GUIX RTOS バインド サービスの詳細について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d94dbb9d7d53ec3e1900188142974cc981dfea9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812086"
---
# <a name="appendix-f---guix-rtos-binding-services"></a><span data-ttu-id="df9b1-103">付録 F - GUIX RTOS バインド サービス</span><span class="sxs-lookup"><span data-stu-id="df9b1-103">Appendix F - GUIX RTOS Binding Services</span></span>

<span data-ttu-id="df9b1-104">GUIX には、基になる RTOS が提供するスレッドまたはタスク サービス、ミューテックス、イベント キュー、およびタイミング サービスが必要です。</span><span class="sxs-lookup"><span data-stu-id="df9b1-104">GUIX requires thread or tasking services, mutex, event queue, and timing services providing by the underlying RTOS.</span></span> <span data-ttu-id="df9b1-105">既定では、GUIX は、ThreadX リアルタイム オペレーティング システムを使用してこれらのサービスを提供するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="df9b1-105">By default GUIX is configured to utilize the ThreadX real time operating system to provide these services.</span></span> <span data-ttu-id="df9b1-106">別のオペレーティング システムに GUIX を移植するには、開発者は、プリプロセッサ ディレクティブ GX_DISABLE_THREADX_BINDING を定義し、GUIX ライブラリをリビルドして、ThreadX 依存関係を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df9b1-106">To port GUIX to another operating system, the developer should # define the pre-processor directive GX_DISABLE_THREADX_BINDING and rebuild the GUIX library to remove the ThreadX dependencies.</span></span> <span data-ttu-id="df9b1-107">さらに、開発者は、次のマクロ定義とサポート関数を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df9b1-107">In addition, the developer will need to provide the following macro definitions and supporting functions.</span></span> <span data-ttu-id="df9b1-108">これらのマクロ定義およびサポート関数の例は、gx_system_rtos_bind.h ファイルと gx_system_rtos_bind.c ファイルにあります。これらのファイルには、一般的な RTOS 統合の例が用意されています。</span><span class="sxs-lookup"><span data-stu-id="df9b1-108">Examples of these macro definitions and supporting functions can be found in the files gx_system_rtos_bind.h and gx_system_rtos_bind.c, which provide an example generic rtos integration.</span></span>

<span data-ttu-id="df9b1-109">システム統合マクロ:</span><span class="sxs-lookup"><span data-stu-id="df9b1-109">System Integration macros:</span></span>

<span data-ttu-id="df9b1-110">**GX_RTOS_BINDING_INITIALIZE**</span><span class="sxs-lookup"><span data-stu-id="df9b1-110">**GX_RTOS_BINDING_INITIALIZE**</span></span>

<span data-ttu-id="df9b1-111">このマクロは、システムの初期化中に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="df9b1-111">This macro is invoked during system initialization.</span></span> <span data-ttu-id="df9b1-112">このマクロは、RTOS システム サービスまたは RTOS リソースの使用前の準備に必要な任意の関数を呼び出すように定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df9b1-112">The macro should be defined to call any function needed to prepare your rtos system services or rtos resources prior to use.</span></span> <span data-ttu-id="df9b1-113">これは、GUIX が使用する RTOS リソースを準備するためのバインドの機会です。</span><span class="sxs-lookup"><span data-stu-id="df9b1-113">This is the binding’s opportunity to prepare the rtos resources that GUIX will use.</span></span>

<span data-ttu-id="df9b1-114">**GX_SYSTEM_THREAD_START**</span><span class="sxs-lookup"><span data-stu-id="df9b1-114">**GX_SYSTEM_THREAD_START**</span></span>

<span data-ttu-id="df9b1-115">このマクロは、GUIX タスクまたはスレッドを実行し始める必要があるときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="df9b1-115">This macro is invoked when the GUIX task or thread should start executing.</span></span> <span data-ttu-id="df9b1-116">このマクロは、GUIX スレッドの実行を開始する関数を呼び出すように定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df9b1-116">This macro should be defined to call a function which will start the GUIX thread running.</span></span> <span data-ttu-id="df9b1-117">呼び出された関数には、GUIX スレッドへのエントリ ポイントが渡されます。</span><span class="sxs-lookup"><span data-stu-id="df9b1-117">The entry point to the GUIX thread is passed to the called function.</span></span> <span data-ttu-id="df9b1-118">呼び出された関数のシグネチャは、次のようにする必要があります</span><span class="sxs-lookup"><span data-stu-id="df9b1-118">The signature of the called function must be</span></span>

<span data-ttu-id="df9b1-119">**UINT *function_name*(VOID (thread_entry_point)(VOID));**</span><span class="sxs-lookup"><span data-stu-id="df9b1-119">**UINT *function_name*(VOID (thread_entry_point)(VOID));**</span></span>

<span data-ttu-id="df9b1-120">この関数は、スレッドが正常に開始された場合は GX_SUCCESS を返し、それ以外の場合は GX_FAILURE を返します。</span><span class="sxs-lookup"><span data-stu-id="df9b1-120">This function should return GX_SUCCESS if the thread is successfully started, or GX_FAILURE.</span></span>

<span data-ttu-id="df9b1-121">**GX_EVENT_PUSH**</span><span class="sxs-lookup"><span data-stu-id="df9b1-121">**GX_EVENT_PUSH**</span></span>

<span data-ttu-id="df9b1-122">このマクロは、使用される FIFO イベント キューにイベントをプッシュするために、GUIX によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="df9b1-122">This macro is invoked to push an event into the FIFO event queue used by GUIX.</span></span> <span data-ttu-id="df9b1-123">新しい RTOS に移植する場合は、スレッドセーフな方法でこのイベント キューを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df9b1-123">When porting to a new rtos, it is your responsibility to implement this event queue in a thread-safe manner.</span></span> <span data-ttu-id="df9b1-124">GX_EVENT 構造体は、このキューにコピーし、このキューからコピーする必要があります。つまり、GX_EVENT ポインターのキューは動作しません。これは、GUIX イベントは、イベント プロデューサーから見ると、自動変数になる可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="df9b1-124">GX_EVENT structures must be copied into this queue and copied out of this queue, i.e. a queue of GX_EVENT pointers will not work, since GUIX events can be automatic variables from the view of the event producer.</span></span> <span data-ttu-id="df9b1-125">このマクロによって呼び出される関数のシグネチャは、次のようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="df9b1-125">The signature of the function called by this macro must be:</span></span>

<span data-ttu-id="df9b1-126">\**UINT *function_name* (GX_EVENT *event_ptr);**</span><span class="sxs-lookup"><span data-stu-id="df9b1-126">\**UINT *function_name* (GX_EVENT *event_ptr);**</span></span>

<span data-ttu-id="df9b1-127">この関数は、イベントがイベント キューにプッシュされた場合は GX_SUCCESS を返し、それ以外の場合は GX_FAILURE を返します。</span><span class="sxs-lookup"><span data-stu-id="df9b1-127">This function should return GX_SUCCESS if the event is pushed into the event queue, otherwise it should return GX_FAILURE.</span></span>

<span data-ttu-id="df9b1-128">**GX_EVENT_POP**</span><span class="sxs-lookup"><span data-stu-id="df9b1-128">**GX_EVENT_POP**</span></span>

<span data-ttu-id="df9b1-129">このマクロは、GUIX イベント キューから先頭の (一番古い) イベントを削除し、要求された場所にコピーするために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="df9b1-129">This macro is invoked to remove the head (oldest) event from the GUIX event queue and copy it into the requested location.</span></span> <span data-ttu-id="df9b1-130">この関数は、現在イベント キューにイベントがない場合に、必要に応じてイベントをブロックまたは待機できなければなりません。</span><span class="sxs-lookup"><span data-stu-id="df9b1-130">This function must be able to optionally block or wait for an event if no events are currently in the event queue.</span></span> <span data-ttu-id="df9b1-131">このマクロによって呼び出される関数のシグネチャは、次のようにする必要があります</span><span class="sxs-lookup"><span data-stu-id="df9b1-131">The signature of the function invoked by this macro must be</span></span>

<span data-ttu-id="df9b1-132">UINT function_name(GX_EVENT \*put_event, GX_BOOL wait)</span><span class="sxs-lookup"><span data-stu-id="df9b1-132">UINT function_name(GX_EVENT \*put_event, GX_BOOL wait)</span></span>

<span data-ttu-id="df9b1-133">wait パラメーター が GX_TRUE の場合、イベントが提供されるまで、関数から制御が戻されません。</span><span class="sxs-lookup"><span data-stu-id="df9b1-133">If the wait parameter == GX_TRUE, the function should not return until an event is provided.</span></span> <span data-ttu-id="df9b1-134">wait パラメーターが GX_FALSE の場合は、イベントの有無に関係なく、関数からすぐに制御が戻されます。</span><span class="sxs-lookup"><span data-stu-id="df9b1-134">If the wait parameter is GX_FALSE, the function should return immediately with or without an event.</span></span>

<span data-ttu-id="df9b1-135">キューからイベントが取得された場合、そのイベントは put_event の場所にコピーされ、リターン状態は GX_SUCCESS になります。</span><span class="sxs-lookup"><span data-stu-id="df9b1-135">If an event is retrieved from the queue, it should copied into the put_event location and the return status is GX_SUCCESS.</span></span> <span data-ttu-id="df9b1-136">それ以外の場合、リターン状態は GX_FAILURE です。</span><span class="sxs-lookup"><span data-stu-id="df9b1-136">Otherwise the return status should be GX_FAILURE.</span></span>

<span data-ttu-id="df9b1-137">**GX_EVENT_FOLD**</span><span class="sxs-lookup"><span data-stu-id="df9b1-137">**GX_EVENT_FOLD**</span></span>

<span data-ttu-id="df9b1-138">このマクロは、FIFO イベント キューにイベントを折りたたむために、GUIX によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="df9b1-138">This macro is invoked by GUIX to fold an event into the FIFO event queue.</span></span> <span data-ttu-id="df9b1-139">イベントの折りたたみとは、同じ種類のイベントが既にキュー内に存在する場合に、新しいイベントのペイロードを含むようにそのエントリが更新されることです。</span><span class="sxs-lookup"><span data-stu-id="df9b1-139">Folding an event means that if an event of the same type already exists in the queue, that entry is update to contain the payload of the new event.</span></span> <span data-ttu-id="df9b1-140">同じ種類の既存のイベントがキュー内に見つからない場合は、新しいイベントがキューにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="df9b1-140">If an existing event of the same type is not found in the queue, a new event is pushed into the queue.</span></span> 

<span data-ttu-id="df9b1-141">イベント折りたたみ機能を実装できないバインディングの場合は、単に GX_EVENT_PUSH を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="df9b1-141">For bindings that cannot implement the event fold feature, it is acceptable to simply invoke the GX_EVENT_PUSH.</span></span>

<span data-ttu-id="df9b1-142">**GX_TIMER_START**</span><span class="sxs-lookup"><span data-stu-id="df9b1-142">**GX_TIMER_START**</span></span>

<span data-ttu-id="df9b1-143">このマクロは、GUIX が定期的なタイマー入力を受け取る必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="df9b1-143">This macro is invoked when GUIX needs to receive periodic timer input.</span></span> <span data-ttu-id="df9b1-144">このマクロは、低レベル RTOS の定期的なタイマー サービスを開始するサービスを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="df9b1-144">This macro should invoke a service that starts the low-level RTOS periodic timer service.</span></span> <span data-ttu-id="df9b1-145">RTOS タイマー サービスを簡単に停止および開始できない場合、このサービスを常時実行させておいても構いませんが、効率的ではありません。</span><span class="sxs-lookup"><span data-stu-id="df9b1-145">If the RTOS timer service cannot be easily stopped and started, it is acceptable but less efficient to leave this service running at all times.</span></span>

<span data-ttu-id="df9b1-146">低レベル RTOS タイマー サービスが定期的に期限切れになる場合、バインドは GUIX システム関数 _gx_system_timer_expiration (0) を呼び出す必要があります。この関数を定期的に呼び出すことで、高レベル GUIX タイマー ウィジェットのタイマー サービスが動作します。</span><span class="sxs-lookup"><span data-stu-id="df9b1-146">When the low-level RTOS timer service periodically expires, the binding must call the GUIX system function _gx_system_timer_expiration(0); Calling this function periodically is what drives the high-level GUIX timer widget timer services.</span></span>

<span data-ttu-id="df9b1-147">**GX_TIMER_STOP**</span><span class="sxs-lookup"><span data-stu-id="df9b1-147">**GX_TIMER_STOP**</span></span>

<span data-ttu-id="df9b1-148">このマクロは、GUIX に定期的なタイマーが不要になった場合 (つまり、アクティブな GUIX タイマーが実行されていない場合) に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="df9b1-148">This macro is invoked when GUIX no longer needs a periodic timer (i.e. there are no active GUIX timers running).</span></span> <span data-ttu-id="df9b1-149">RTOS タイマー サービスを簡単に停止および開始できない場合、このサービスを常時実行させて何も行わないようにこのマクロを定義しても構いませんが、効率的ではありません。</span><span class="sxs-lookup"><span data-stu-id="df9b1-149">If the RTOS timer service cannot be easily stopped and started, it is acceptable but less efficient to leave this service running at all times and define this macro to do nothing.</span></span>

<span data-ttu-id="df9b1-150">**GX_SYSTEM_MUTEX_LOCK**</span><span class="sxs-lookup"><span data-stu-id="df9b1-150">**GX_SYSTEM_MUTEX_LOCK**</span></span>

<span data-ttu-id="df9b1-151">このマクロは、重要なコード セクション中、別のタスクが一般的なデータ構造に優先して実行され、そのデータ構造を変更し、破損を引き起こす可能性を防ぐために、GUIX によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="df9b1-151">This macro is invoked by GUIX during critical code sections to prevent another task from  pre-empting and modifying common data structures, potentially causing corruption.</span></span> <span data-ttu-id="df9b1-152">このマクロは、適切な RTOS リソース ロック サービスを実装する関数を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="df9b1-152">This macro should call a function that implements the suitable RTOS resource locking service.</span></span>

<span data-ttu-id="df9b1-153">GUIX API サービスを GUIX スレッド外で使用しない場合は、何も実行しないようにこのマクロを定義できます。</span><span class="sxs-lookup"><span data-stu-id="df9b1-153">If you never utilize any GUIX API services outside of the GUIX thread, you can define this macro to do nothing.</span></span>

<span data-ttu-id="df9b1-154">**GX_SYSTEM_MUTEX_UNLOCK**</span><span class="sxs-lookup"><span data-stu-id="df9b1-154">**GX_SYSTEM_MUTEX_UNLOCK**</span></span>

<span data-ttu-id="df9b1-155">このマクロは、重要なコード セクションの最後に呼び出され、基になる適切な RTOS サービスを使用して GUIX リソースのロックを解除します。</span><span class="sxs-lookup"><span data-stu-id="df9b1-155">This macro is invoked at the end of critical code sections, and should unlock the GUIX resource using the suitable underlying RTOS service.</span></span> <span data-ttu-id="df9b1-156">GUIX API サービスを GUIX スレッド外で使用しない場合は、何も実行しないようにこのマクロを定義できます。</span><span class="sxs-lookup"><span data-stu-id="df9b1-156">If you never utilize any GUIX API services outside of the GUIX thread, you can define this macro to do nothing.</span></span>

<span data-ttu-id="df9b1-157">**GX_SYSTEM_TIME_GET**</span><span class="sxs-lookup"><span data-stu-id="df9b1-157">**GX_SYSTEM_TIME_GET**</span></span>

<span data-ttu-id="df9b1-158">このマクロは、現在のシステム時刻を "システム ティック数" で返す関数を呼び出す必要があります。システム ティック数は、通常、システムの起動後に発生した低レベルのタイマー割り込みの数です。</span><span class="sxs-lookup"><span data-stu-id="df9b1-158">This macro should call a function that returns the current system time is “system ticks”, which is usually the number of low-level timer interrupts that have occurred since system startup.</span></span> <span data-ttu-id="df9b1-159">このサービスは、タッチ入力ジェスチャに対するタッチ イベントのペン速度を計算するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="df9b1-159">This service is used to calculate touch event pen speed for touch input gestures.</span></span> <span data-ttu-id="df9b1-160">このマクロによって呼び出される関数のシグネチャは、次のようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="df9b1-160">The signature of the function invoked by this macro must be:</span></span>

<span data-ttu-id="df9b1-161">**ULONG *function_name*(VOID);**</span><span class="sxs-lookup"><span data-stu-id="df9b1-161">**ULONG *function_name*(VOID);**</span></span>

<span data-ttu-id="df9b1-162">**GX_CURRENT_THREAD**</span><span class="sxs-lookup"><span data-stu-id="df9b1-162">**GX_CURRENT_THREAD**</span></span>

<span data-ttu-id="df9b1-163">このマクロは、現在実行中のスレッドを識別するために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="df9b1-163">This macro is invoked to identify the currently executing thread.</span></span> <span data-ttu-id="df9b1-164">このマクロによって呼び出されるサービスは、void \* を返す必要があります。つまり、現在の実行スレッドを識別するために、お使いのオペレーティング システムによって使用されるデータ型を GUIX に返すには、void \* にキャストしなければなりません。</span><span class="sxs-lookup"><span data-stu-id="df9b1-164">The service called by this macro must return a void \*, meaning that the data type used by your operating system to identify the current execution thread must be cast to a void \* to be returned to GUX.</span></span>

<span data-ttu-id="df9b1-165">一般的な RTOS バインドの完全な例は、登録済み gx_system_rtos_bind.h および gx_system_rtos_bind.c フィールド内に実装されています</span><span class="sxs-lookup"><span data-stu-id="df9b1-165">A complete example of a generic RTOS binding is implemented in the filed gx_system_rtos_bind.h and gx_system_rtos_bind.c</span></span>