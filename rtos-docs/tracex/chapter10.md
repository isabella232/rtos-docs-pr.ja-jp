---
title: 第 10 章 - 顧客ユーザー イベント
description: この章では、ユーザー定義イベント、およびそのようなイベントのカスタム アイコンと情報フィールドを作成する方法について説明します。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 635c2d79922de9d5649bab841ae946cac862056c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812422"
---
# <a name="chapter-10---customer-user-events"></a><span data-ttu-id="89671-103">第 10 章 - 顧客ユーザー イベント</span><span class="sxs-lookup"><span data-stu-id="89671-103">Chapter 10 - Customer user events</span></span>

<span data-ttu-id="89671-104">この章では、ユーザー定義イベント、およびそのようなイベントのカスタム アイコンと情報フィールドを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="89671-104">This chapter contains a description of how to create user-defined events and custom icons and information fields for such events.</span></span> <span data-ttu-id="89671-105">この章は以下のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="89671-105">This chapter includes the following sections:</span></span> 

## <a name="inserting-user-defined-events"></a><span data-ttu-id="89671-106">ユーザー定義イベントの挿入</span><span class="sxs-lookup"><span data-stu-id="89671-106">Inserting User-Defined Events</span></span>

<span data-ttu-id="89671-107">ThreadX では、開発者が独自のユーザー定義イベントをログに記録できるので、さらに有用な情報を提供して TraceX でグラフィカルに表示できます。</span><span class="sxs-lookup"><span data-stu-id="89671-107">ThreadX provides the ability for developers to log their own user-defined events, providing even more useful information that can be viewed graphically by TraceX.</span></span> <span data-ttu-id="89671-108">ユーザー定義イベント番号の範囲は、</span><span class="sxs-lookup"><span data-stu-id="89671-108">User-defined event numbers range from</span></span>

<span data-ttu-id="89671-109">**TX_TRACE_USER_EVENT_START** (4096) から **TX_TRACE_USER_EVENT_END** (65535) までです。</span><span class="sxs-lookup"><span data-stu-id="89671-109">**TX_TRACE_USER_EVENT_START** (4096) through **TX_TRACE_USER_EVENT_END** (65535), inclusive.</span></span> <span data-ttu-id="89671-110">トレース バッファーにイベントを配置するには、第 5 章で定義されている ***tx_trace_user_event_insert*** を使用します。</span><span class="sxs-lookup"><span data-stu-id="89671-110">The placement of the events in the trace buffer is done via the ***tx_trace_user_event_insert***, defined in Chapter 5.</span></span> <span data-ttu-id="89671-111">次の呼び出し例では、2 つのユーザー定義イベント (イベント 4096 とイベント 4098) をターゲットの現在のトレース バッファーに挿入します。</span><span class="sxs-lookup"><span data-stu-id="89671-111">The following example calls insert two user-defined events into the current trace buffer on the target, namely user-defined event 4096 and event 4098:</span></span>

```c
tx_trace_user_event_insert(4096, 1, 2, 3, 4);
tx_trace_user_event_insert(4098,0x100,0x200,0x300,0x400);
```

## <a name="default-display-of-user-defined-events"></a><span data-ttu-id="89671-112">ユーザー定義イベントの既定の表示</span><span class="sxs-lookup"><span data-stu-id="89671-112">Default Display of User-Defined Events</span></span>

![ユーザー定義イベント アイコン](./media/user-guide/tx-events/image0.png)

<span data-ttu-id="89671-114">既定では、TraceX には、第 6 章で説明した既定のユーザー定義イベント アイコンを使用して、すべてのユーザー イベントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="89671-114">By default, TraceX displays all user events with a default user-defined Event icon as described in Chapter 6.</span></span> <span data-ttu-id="89671-115">図 28 は、前の ***tx_trace_user_event_insert*** の例でイベント バッファーに配置された、イベント 452 と 453 の既定のユーザー定義イベント アイコンを示しています。</span><span class="sxs-lookup"><span data-stu-id="89671-115">Figure 28 shows the default user-defined event icon for events 452 and 453, which were placed in the event buffer via the previous ***tx_trace_user_event_insert*** examples.</span></span>

<span data-ttu-id="89671-116">![ユーザー定義イベントの既定の表示のスクリーンショット。](./media/user-guide/10.1.png)
**図 28**</span><span class="sxs-lookup"><span data-stu-id="89671-116">![Screenshot of the default display of user-defined events.](./media/user-guide/10.1.png)
**FIGURE 28**</span></span>

<span data-ttu-id="89671-117">さらに、ユーザー定義イベントの詳細情報も提供されます。</span><span class="sxs-lookup"><span data-stu-id="89671-117">Detailed information is also available for user-defined Events.</span></span> <span data-ttu-id="89671-118">図 29 では、イベント番号が 4096 のイベント 452 の詳細なイベント情報が表示されています。そこには、指定された 4 つの情報フィールドが示されています。</span><span class="sxs-lookup"><span data-stu-id="89671-118">Figure 28 shows the detailed event information for event 452, which has event number 4096 and shows the specified four information fields.</span></span>

<span data-ttu-id="89671-119">![ユーザー定義イベントの詳細表示のスクリーンショット。](./media/user-guide/10.2.png)
**図 29**</span><span class="sxs-lookup"><span data-stu-id="89671-119">![Screenshot of the detailed display of user-defined events.](./media/user-guide/10.2.png)
**FIGURE 29**</span></span>

## <a name="defining-custom-user-defined-event-icons"></a><span data-ttu-id="89671-120">ユーザー定義イベントのカスタム アイコンの定義</span><span class="sxs-lookup"><span data-stu-id="89671-120">Defining Custom User-Defined Event Icons</span></span>

<span data-ttu-id="89671-121">TraceX では、ユーザー定義イベントのカスタム アイコンとカスタム情報フィールド ラベルを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="89671-121">TraceX also provides the user the ability to create custom user-defined event icons and custom information field labels.</span></span> <span data-ttu-id="89671-122">この機能を実現するには、\***tracex_custom trxc** _ 構成ファイルにイベント アイコンの仕様を追加します。</span><span class="sxs-lookup"><span data-stu-id="89671-122">This capability is achieved by adding event icon specifications to the \***tracex_custom.trxc** _ configuration file.</span></span> <span data-ttu-id="89671-123">このファイルは、ユーザー定義の TraceX インストール ディレクトリ (既定では c:\Azure_RTOS\TraceX) の _ *_CustomEvents_*\* サブディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="89671-123">This file is located in the _ *_CustomEvents_*\* subdirectory of your user-defined TraceX installation directory, which defaults to c:\Azure_RTOS\TraceX.</span></span> <span data-ttu-id="89671-124">ディレクトリ パスの例を図 30 に示します。</span><span class="sxs-lookup"><span data-stu-id="89671-124">An example directory path is shown in Figure 30.</span></span>

<span data-ttu-id="89671-125">![ディレクトリ パスの例のスクリーンショット。](./media/user-guide/custom_events_folder.png)
**図 30**</span><span class="sxs-lookup"><span data-stu-id="89671-125">![Screenshot of an example directory path.](./media/user-guide/custom_events_folder.png)
**FIGURE 30**</span></span>

<span data-ttu-id="89671-126">***tracex_custom.trxc*** カスタム イベント構成ファイルは、0 個以上のカスタム イベント定義を含む単純な ASCII テキスト ファイルです。</span><span class="sxs-lookup"><span data-stu-id="89671-126">The ***tracex_custom.trxc*** custom event configuration file is a simple ASCII text file containing zero or more custom event definitions.</span></span> <span data-ttu-id="89671-127">ファイルの形式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="89671-127">The format of the file is as follows:</span></span>

```c
//Comments
**Start **
[custom event definition(s)] **End **
```

<span data-ttu-id="89671-128">Start と End の間の行を使用して、カスタム イベントを定義します (1 行につき 1 つ)。</span><span class="sxs-lookup"><span data-stu-id="89671-128">Each line between Start and End is used to define a single custom event.</span></span> <span data-ttu-id="89671-129">TraceX には、カスタム イベントが定義されていない ("Start" ラベルと "End" ラベルの間に何もない)、このファイルのテンプレート バージョンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="89671-129">TraceX provides a template version of this file with no custom events defined (nothing between the "Start" and "End" labels).</span></span> <span data-ttu-id="89671-130">カスタム イベント定義の形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="89671-130">The format of a custom event definition is as follows:</span></span>

<span data-ttu-id="89671-131">**number, name, abbreviation, top_color, bottom_color, label1, label2, label2, label4**</span><span class="sxs-lookup"><span data-stu-id="89671-131">**number, name, abbreviation, top_color, bottom_color, label1, label2, label2, label4**</span></span>

<span data-ttu-id="89671-132">各値の説明:</span><span class="sxs-lookup"><span data-stu-id="89671-132">where:</span></span>

- <span data-ttu-id="89671-133">number: ユーザー定義イベント番号 (4096 から 65535) を定義します。</span><span class="sxs-lookup"><span data-stu-id="89671-133">number: Defines the user-defined event number, between 4096 and 65535, inclusive.</span></span></th>
- <span data-ttu-id="89671-134">name: ユーザー定義イベントの論理名を定義します。</span><span class="sxs-lookup"><span data-stu-id="89671-134">name: Defines the logical name for the user-defined event.</span></span></td>
- <span data-ttu-id="89671-135">abbreviation: ユーザー定義イベントの略称 (2 文字) を定義します。</span><span class="sxs-lookup"><span data-stu-id="89671-135">abbreviation: Defines the two-letter user-defined event abbreviation.</span></span></td>
- <span data-ttu-id="89671-136">top_color: アイコンの上半分の RGB 値 (かっこ内の 3 桁の数値) を定義します。</span><span class="sxs-lookup"><span data-stu-id="89671-136">top_color: Defines the RGB value for the top-half of the icon, which is a three-digit number in parenthesis.</span></span> <span data-ttu-id="89671-137">一般的な RGB 定義は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="89671-137">Some typical RGB definitions are</span></span>
  - <span data-ttu-id="89671-138">黒 = (0,0,0)</span><span class="sxs-lookup"><span data-stu-id="89671-138">BLACK = (0,0,0)</span></span>       
  - <span data-ttu-id="89671-139">白 = (255,255,255)</span><span class="sxs-lookup"><span data-stu-id="89671-139">WHITE = (255,255,255)</span></span>
  - <span data-ttu-id="89671-140">赤 = (255,0,0)</span><span class="sxs-lookup"><span data-stu-id="89671-140">RED = (255,0,0)</span></span>     
  - <span data-ttu-id="89671-141">緑 = (0,255,0)</span><span class="sxs-lookup"><span data-stu-id="89671-141">GREEN = (0,255,0)</span></span>     
  - <span data-ttu-id="89671-142">青 = (0,0,255)</span><span class="sxs-lookup"><span data-stu-id="89671-142">BLUE = (0,0,255)</span></span>     
  - <span data-ttu-id="89671-143">黄 = (255,255,0)</span><span class="sxs-lookup"><span data-stu-id="89671-143">YELLOW = (255,255,0)</span></span>   
  - <span data-ttu-id="89671-144">シアン = (0,255,255)</span><span class="sxs-lookup"><span data-stu-id="89671-144">CYAN = (0,255,255)</span></span>   
  - <span data-ttu-id="89671-145">マゼンタ = (255,0,255)</span><span class="sxs-lookup"><span data-stu-id="89671-145">MAGENTA = (255,0,255)</span></span>   
  <span data-ttu-id="89671-146">RGB 仕様を使用すると、ユーザーは各ユーザー定義アイコンにさまざまな色を指定できます。</span><span class="sxs-lookup"><span data-stu-id="89671-146">Using the RBG specification gives the user a broad range of colors for each user-defined icon.</span></span> <span data-ttu-id="89671-147">RGB カラー定義の詳細については、 https://en.wikipedia.org/wiki/RGB#Digital_representations をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="89671-147">For more information on RBG color definition, see: https://en.wikipedia.org/wiki/RGB#Digital_representations</span></span>
- <span data-ttu-id="89671-148">botton_color: アイコンの下半分の RGB 値 (かっこ内の 3 桁の数値) を定義します。</span><span class="sxs-lookup"><span data-stu-id="89671-148">botton_color: Defines the RGB value for the bottom half of the icon, which is a three-digit number in parenthesis.</span></span>
- <span data-ttu-id="89671-149">label1: _ *_tx_trace_user_event_insert_*\* 呼び出しで指定された \***info_field_1** _ のラベル。</span><span class="sxs-lookup"><span data-stu-id="89671-149">label1: Label for ***info_field_1** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="89671-150">label2: _ *_tx_trace_user_event_insert_*\* 呼び出しで指定された \***info_field_2** _ のラベル。</span><span class="sxs-lookup"><span data-stu-id="89671-150">label2: Label for ***info_field_2** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="89671-151">label3: _ *_tx_trace_user_event_insert_*\* 呼び出しで指定された \***info_field_3** _ のラベル。</span><span class="sxs-lookup"><span data-stu-id="89671-151">label3: Label for ***info_field_3** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="89671-152">label4: _ *_tx_trace_user_event_insert_*\* 呼び出しで指定された \***info_field_4** _ のラベル。</span><span class="sxs-lookup"><span data-stu-id="89671-152">label4: Label for ***info_field_4** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>

<span data-ttu-id="89671-153">この章で使用する 2 つのユーザー定義イベントの定義例を図 31 に示します。</span><span class="sxs-lookup"><span data-stu-id="89671-153">Example definitions for each of the two user-defined events used in this chapter are shown in Figure 10.4.</span></span> <span data-ttu-id="89671-154">まず、\***tracex_custom. trxc** _ ファイルの 5 行目でイベント 4096 が定義されています。</span><span class="sxs-lookup"><span data-stu-id="89671-154">The first definition is for event 4096 at line 5 of the \***tracex_custom.trxc** _ file.</span></span> <span data-ttu-id="89671-155">この定義では、ユーザー定義イベント 4096 に _*First_User_Event*\* という名前が付けられ、2 文字の略称として **FE** が指定されています。また、アイコンの上部に赤、下部に緑が指定され、情報フィールドに **First_Info1**、**First_Info2**、**First_Info3**、**First_Info4** という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="89671-155">This definition gives user-defined event 4096 the name _\*First_User_Event\*\*, specifies a two-letter abbreviation of **FE**, makes the top portion of the icon red, the bottom portion of the icon green, and names the information fields as **First_Info1**, **First_Info2**, **First_Info3**, and **First_Info4**.</span></span> <span data-ttu-id="89671-156">ユーザー定義イベント 4098 も、**_tracex_custom.trxc_** の 6 行目で同様に定義されています。</span><span class="sxs-lookup"><span data-stu-id="89671-156">User-defined event 4098 is defined similarly at line 6 of **_tracex_custom.trxc_**.</span></span>

<span data-ttu-id="89671-157">![ユーザー定義イベントの定義例のスクリーンショット。](./media/user-guide/10.4.png)
**図 31**</span><span class="sxs-lookup"><span data-stu-id="89671-157">![Screenshot of the example definitions for the user-defined events.](./media/user-guide/10.4.png)
**FIGURE 31**</span></span>

<span data-ttu-id="89671-158">\***tracex_custom.trxc** _ ファイルは初期化中に TraceX によって読み取られるため、カスタム アイコンの定義を有効にするには、TraceX を終了して再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89671-158">Since the \***tracex_custom.trxc** _ file is read by TraceX during initialization, TraceX must be exited and restarted before the custom icon definitions can take effect.</span></span> <span data-ttu-id="89671-159">図 32 では、_*_tracex_custom. trxc_*\* で定義されているカスタム イベント アイコンを使用して、ユーザー定義イベント 452 と 453 が TraceX に表示されています。</span><span class="sxs-lookup"><span data-stu-id="89671-159">Figure 32 shows the TraceX display of user-defined events 452 and 453 with the custom event icons defined in _\*_tracex_custom.trxc_\*\*.</span></span>

<span data-ttu-id="89671-160">![カスタム イベント アイコンを使用したユーザー定義イベントの TraceX での表示のスクリーンショット。](./media/user-guide/10.5.png)
**図 32**</span><span class="sxs-lookup"><span data-stu-id="89671-160">![Screenshot of the TraceX display of user defined events with the custom event icons.](./media/user-guide/10.5.png)
**FIGURE 32**</span></span>

<span data-ttu-id="89671-161">ダブルクリックまたはマウスでのポイントによってイベントを選択するか、現在のイベントのボタンをクリックすると、カスタム イベント定義の追加情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="89671-161">The additional information in the custom event definition is shown when the event you select using a double-click, mouse-over, or clicking the current event button.</span></span> <span data-ttu-id="89671-162">図 33 は、イベント 452 をダブルクリックで選択した状態を示しています。</span><span class="sxs-lookup"><span data-stu-id="89671-162">Figure 33 shows the double-click selection on event 452.</span></span> <span data-ttu-id="89671-163">イベント名と情報フィールドは、***tracex_custom trxc*** に追加された定義例とすべて一致しています。</span><span class="sxs-lookup"><span data-stu-id="89671-163">The event name and information fields all match the sample definition that was added to ***tracex_custom.trxc***.</span></span>

<span data-ttu-id="89671-164">![イベントをダブルクリックで選択した状態を示すスクリーンショット。](./media/user-guide/10.6.png)
**図 33**</span><span class="sxs-lookup"><span data-stu-id="89671-164">![Screenshot of the double-click selection on an event.](./media/user-guide/10.6.png)
**FIGURE 33**</span></span>
