---
title: 第 1 章 - Azure RTOS NetX Duo PTP クライアントの概要
description: この章では、Azure RTOS NetX Duo PTP クライアントの概要を説明します。
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5beec64bd6d74e3bed06be15255d6bd4a940ba64
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810622"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ptp-client"></a><span data-ttu-id="55e09-103">第 1 章 - Azure RTOS NetX Duo PTP クライアントの概要</span><span class="sxs-lookup"><span data-stu-id="55e09-103">Chapter 1 - Introduction to Azure RTOS NetX Duo PTP Client</span></span>

<span data-ttu-id="55e09-104">Azure RTOS NetX Duo PTP は、Precision Time Protocol (PTP) バージョン 2 (IEEE 1588-2008) のクライアント部分を実装しています。</span><span class="sxs-lookup"><span data-stu-id="55e09-104">The Azure RTOS NetX Duo PTP implements the client part of the Precision Time Protocol (PTP) version 2, IEEE 1588-2008.</span></span> <span data-ttu-id="55e09-105">これは、IPv4 または IPv6 マルチキャスト パケットを介して相互に通信することによって、ローカル ネットワーク上の MCU 間でクロックを同期するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="55e09-105">It is used to synchronize clocks among MCUs on the local network by communicating each other via IPv4 or IPv6 multicast packets.</span></span>

## <a name="netx-duo-ptp-client-setup"></a><span data-ttu-id="55e09-106">NetX Duo PTP クライアントのセットアップ</span><span class="sxs-lookup"><span data-stu-id="55e09-106">NetX Duo PTP Client Setup</span></span>

<span data-ttu-id="55e09-107">PTP クライアント パッケージを正しく機能させるには、NetX Duo IP インスタンスが既に作成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="55e09-107">In order to function properly, the PTP client package requires that a NetX Duo IP instance has already been created.</span></span>

<span data-ttu-id="55e09-108">既定では、PTP クライアントは IPv4 マルチキャスト グループに参加します。</span><span class="sxs-lookup"><span data-stu-id="55e09-108">By default, the PTP client joins IPv4 multicast group.</span></span> <span data-ttu-id="55e09-109">IPv6 ネットワーク上で PTP クライアントを実行するには、NetX Duo ライブラリを構築するときに `NX_ENABLE_IPV6_MULTICAST` を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55e09-109">In order to run the PTP client on an IPv6 network, `NX_ENABLE_IPV6_MULTICAST` must be defined when building NetX Duo library.</span></span>

<span data-ttu-id="55e09-110">PTP クライアントの作成時に、着信および発信パケットのタイムスタンプを処理するコールバック関数をアプリケーションで提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55e09-110">When creating the PTP client, the application must provide a callback function to handle timestamps of incoming and outgoing packets.</span></span> <span data-ttu-id="55e09-111">高解像度を実現するために、アプリケーションで高解像度タイマーを使用してタイムスタンプを生成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="55e09-111">To achieve high resolution, we recommend applications to generate timestamps using a high resolution timer.</span></span> <span data-ttu-id="55e09-112">シミュレーターで PTP を実行するために、ソフトウェアベースの実装である `nx_ptp_client_soft_clock_callback` が用意されています。</span><span class="sxs-lookup"><span data-stu-id="55e09-112">To run the PTP on simulator, a software-based implementation `nx_ptp_client_soft_clock_callback` is provided.</span></span>

<span data-ttu-id="55e09-113">PTP クライアントには、PTP メッセージを送信するためのパケット プールが必要です。</span><span class="sxs-lookup"><span data-stu-id="55e09-113">The PTP client requires a packet pool for transmitting PTP messages.</span></span> <span data-ttu-id="55e09-114">パケット プールのペイロード サイズは、`NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE` (IPv4 の場合は 108 バイト、IPv6 が有効な場合は 128 バイト) 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="55e09-114">The payload size of packet pool must be no less than `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE`, which is 108 bytes for IPv4, and 128 bytes if IPv6 is enabled.</span></span>

<span data-ttu-id="55e09-115">PTP クライアントの作成後、アプリケーションで PTP クライアントを起動できます。</span><span class="sxs-lookup"><span data-stu-id="55e09-115">After creating the PTP Client, the application can start the PTP client.</span></span> <span data-ttu-id="55e09-116">同期は PTP ヘルパー スレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="55e09-116">The synchronization is done in the PTP helper thread.</span></span> <span data-ttu-id="55e09-117">イベント コールバック関数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="55e09-117">An event callback function can be specified.</span></span> <span data-ttu-id="55e09-118">これは、次のいずれかのイベントが発生したときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="55e09-118">It will be invoked when any one of the following events happen.</span></span>
* <span data-ttu-id="55e09-119">マスターの選択。</span><span class="sxs-lookup"><span data-stu-id="55e09-119">A master is selected;</span></span> 
* <span data-ttu-id="55e09-120">時間の調整。</span><span class="sxs-lookup"><span data-stu-id="55e09-120">The time is calibrated.</span></span>
* <span data-ttu-id="55e09-121">マスターのタイムアウト。</span><span class="sxs-lookup"><span data-stu-id="55e09-121">A master times out.</span></span>

## <a name="netx-duo-ptp-client-messages"></a><span data-ttu-id="55e09-122">NetX Duo PTP クライアント メッセージ</span><span class="sxs-lookup"><span data-stu-id="55e09-122">NetX Duo PTP Client Messages</span></span>

<span data-ttu-id="55e09-123">NetX Duo PTP クライアントは、遅延要求 - 応答メカニズムのみを実装しています。</span><span class="sxs-lookup"><span data-stu-id="55e09-123">The NetX Duo PTP client implements the delay request-response mechanism only.</span></span> <span data-ttu-id="55e09-124">PTP クライアントでは 2 つの UDP ポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="55e09-124">The PTP client  opens two UDP ports.</span></span> <span data-ttu-id="55e09-125">**イベント** メッセージ用の *319* と、**一般** メッセージ用の *320* です。</span><span class="sxs-lookup"><span data-stu-id="55e09-125">*319* for **event** message and *320* for **general** message.</span></span> <span data-ttu-id="55e09-126">このメカニズムには、5 種類のメッセージがあります。</span><span class="sxs-lookup"><span data-stu-id="55e09-126">There are five types of message for this mechanism.</span></span>

* <span data-ttu-id="55e09-127">**Announce**:</span><span class="sxs-lookup"><span data-stu-id="55e09-127">**Announce**.</span></span> <span data-ttu-id="55e09-128">これはイベント メッセージです。</span><span class="sxs-lookup"><span data-stu-id="55e09-128">This is an event message.</span></span> <span data-ttu-id="55e09-129">マスター クロックの選択に使用されます。</span><span class="sxs-lookup"><span data-stu-id="55e09-129">It is used for master clock selection.</span></span>
* <span data-ttu-id="55e09-130">**Sync**: これはイベント メッセージです。</span><span class="sxs-lookup"><span data-stu-id="55e09-130">**Sync**. This is an event message.</span></span> <span data-ttu-id="55e09-131">発信元タイムスタンプを送信し、マスターからクライアントへのパス遅延を計算するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="55e09-131">It is used to send origin timestamp and calculate the path delay from master to client.</span></span>
* <span data-ttu-id="55e09-132">**Follow_Up**:</span><span class="sxs-lookup"><span data-stu-id="55e09-132">**Follow_Up**.</span></span> <span data-ttu-id="55e09-133">これは一般メッセージです。</span><span class="sxs-lookup"><span data-stu-id="55e09-133">This is a general message.</span></span> <span data-ttu-id="55e09-134">関連する Sync メッセージの発信元タイムスタンプを修正するために、必要に応じて使用されます。</span><span class="sxs-lookup"><span data-stu-id="55e09-134">It is optional and used to correct the origin timestamp in related Sync message.</span></span> <span data-ttu-id="55e09-135">Sync フラグの 2 ステップ ビットが設定されている場合にのみ送信されます。</span><span class="sxs-lookup"><span data-stu-id="55e09-135">It is sent only when the two step bit in Sync flag is set.</span></span>
* <span data-ttu-id="55e09-136">**Delay_Req**:</span><span class="sxs-lookup"><span data-stu-id="55e09-136">**Delay_Req**.</span></span> <span data-ttu-id="55e09-137">これはイベント メッセージです。</span><span class="sxs-lookup"><span data-stu-id="55e09-137">This is an event message.</span></span> <span data-ttu-id="55e09-138">Delay_Resp の受信時に、クライアントからマスターへのパス遅延を計算するために、PTP クライアントから送信されます。</span><span class="sxs-lookup"><span data-stu-id="55e09-138">It is sent from PTP client to calculate the path delay from client to master, on receiving Delay_Resp.</span></span>
* <span data-ttu-id="55e09-139">**Delay_Resp**:</span><span class="sxs-lookup"><span data-stu-id="55e09-139">**Delay_Resp**.</span></span> <span data-ttu-id="55e09-140">これはイベント メッセージです。</span><span class="sxs-lookup"><span data-stu-id="55e09-140">This is an event message.</span></span> <span data-ttu-id="55e09-141">クライアントからマスターへのパス遅延を計算するために、マスターからクライアントに送信されます。</span><span class="sxs-lookup"><span data-stu-id="55e09-141">It is sent from master to client to calculate the path delay from client to master.</span></span>

<span data-ttu-id="55e09-142">" *"ベスト マスター クロック" アルゴリズムは実装されていないことに注意してください。PTP クライアントがリッスン状態の場合、最初のマスター クロックのみが受け入れられます。* "</span><span class="sxs-lookup"><span data-stu-id="55e09-142">*Note, "best master clock" algorithm is not implemented. Only the first master clock is accepted when the PTP client is in listening state.*</span></span>

## <a name="netx-duo-ptp-client-clock-callback"></a><span data-ttu-id="55e09-143">NetX Duo PTP クライアントのクロック コールバック</span><span class="sxs-lookup"><span data-stu-id="55e09-143">NetX Duo PTP Client Clock Callback</span></span>
<span data-ttu-id="55e09-144">マスターからのクロックを同期するには、PTP クライアントにローカル クロックが必要です。</span><span class="sxs-lookup"><span data-stu-id="55e09-144">To synchronize clock from master, PTP client needs a local clock.</span></span> <span data-ttu-id="55e09-145">クロック コールバック関数は、作成時に PTP クライアントに渡されます。</span><span class="sxs-lookup"><span data-stu-id="55e09-145">A clock callback function is passed into PTP client during creation.</span></span> <span data-ttu-id="55e09-146">クロック コールバック ルーチンの形式は次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="55e09-146">The format of the clock callback routine is  defined below.</span></span>
```C
UINT ptp_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```
<span data-ttu-id="55e09-147">入力パラメーターは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="55e09-147">The input parameters are defined as follows:</span></span>
* <span data-ttu-id="55e09-148">*client_ptr* は、PTP クライアントを指します。</span><span class="sxs-lookup"><span data-stu-id="55e09-148">*client_ptr* points to PTP client.</span></span>
* <span data-ttu-id="55e09-149">*operation* では、コールバック操作を指定します。有効な値は次の一覧のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="55e09-149">*operation* specifies the callback operation, valid values are defined as shown in the list below.</span></span>
  * <span data-ttu-id="55e09-150">**NX_PTP_CLIENT_CLOCK_INIT**: クロックを初期化します。</span><span class="sxs-lookup"><span data-stu-id="55e09-150">**NX_PTP_CLIENT_CLOCK_INIT** Initialize clock.</span></span>
  * <span data-ttu-id="55e09-151">**NX_PTP_CLIENT_CLOCK_SET**: `time_ptr` で指定された現在のタイムスタンプを設定します。</span><span class="sxs-lookup"><span data-stu-id="55e09-151">**NX_PTP_CLIENT_CLOCK_SET** Set current timestamp specified by `time_ptr`.</span></span>
  * <span data-ttu-id="55e09-152">**NX_PTP_CLIENT_CLOCK_GET**: 現在のタイムスタンプを `time_ptr` に返します。</span><span class="sxs-lookup"><span data-stu-id="55e09-152">**NX_PTP_CLIENT_CLOCK_GET** Return current timestamp to `time_ptr`.</span></span>
  * <span data-ttu-id="55e09-153">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT**: `packet_ptr` から `time_ptr` にタイムスタンプを抽出します。</span><span class="sxs-lookup"><span data-stu-id="55e09-153">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extract timestamp from `packet_ptr` to `time_ptr`.</span></span>
  * <span data-ttu-id="55e09-154">**NX_PTP_CLIENT_CLOCK_ADJUST**: 現在のタイムスタンプを *1* 秒未満に調整します。</span><span class="sxs-lookup"><span data-stu-id="55e09-154">**NX_PTP_CLIENT_CLOCK_ADJUST** Adjust current timestamp less than *1* second.</span></span>
  * <span data-ttu-id="55e09-155">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE**: 送信されたタイムスタンプを PTP クライアントに通知する必要がある `packet_ptr` をマークします。</span><span class="sxs-lookup"><span data-stu-id="55e09-155">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Mark the `packet_ptr` which requires to notify PTP client the timestamp when it is transmitted.</span></span>
  * <span data-ttu-id="55e09-156">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE**: ソフト タイマーを更新します。</span><span class="sxs-lookup"><span data-stu-id="55e09-156">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Update soft timer.</span></span> <span data-ttu-id="55e09-157">ハードウェア クロックではこれを無視できます。</span><span class="sxs-lookup"><span data-stu-id="55e09-157">It can be ignored by hardware clock.</span></span>
* <span data-ttu-id="55e09-158">*time_ptr* はタイムスタンプを指します。</span><span class="sxs-lookup"><span data-stu-id="55e09-158">*time_ptr* points to timestamp.</span></span>
* <span data-ttu-id="55e09-159">*packet_ptr* はパケットを指します。</span><span class="sxs-lookup"><span data-stu-id="55e09-159">*packet_ptr* points to packet.</span></span>
* <span data-ttu-id="55e09-160">*callback_data* は、不透明なコールバック データを指します。</span><span class="sxs-lookup"><span data-stu-id="55e09-160">*callback_data* points to opaque callback data.</span></span>

<span data-ttu-id="55e09-161">NX_PTP_TIME データ型は、次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="55e09-161">The NX_PTP_TIME data type is defined as follows.</span></span>
```C
typedef struct NX_PTP_TIME_STRUCT
{
    /* The MSB of the number of seconds */
    LONG  second_high;

    /* The LSB of the number of seconds */
    ULONG second_low;

    /* The number of nanoseconds */
    LONG  nanosecond;
} NX_PTP_TIME;
```

## <a name="netx-duo-ptp-client-event-callback"></a><span data-ttu-id="55e09-162">NetX Duo PTP クライアントのイベント コールバック</span><span class="sxs-lookup"><span data-stu-id="55e09-162">NetX Duo PTP Client Event Callback</span></span>
<span data-ttu-id="55e09-163">PTP クライアントの状態をアプリケーションに通知するために、イベント コールバック関数を設定できます。</span><span class="sxs-lookup"><span data-stu-id="55e09-163">The event callback function can be setup to notify application the state of PTP client.</span></span> <span data-ttu-id="55e09-164">イベント コールバック ルーチンの形式は次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="55e09-164">The format of the event callback routine is defined as shown below.</span></span>
```C
UINT event_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT event, 
    VOID *event_data, 
    VOID *callback_data);
```
<span data-ttu-id="55e09-165">入力パラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="55e09-165">The input parameters are.</span></span>
* <span data-ttu-id="55e09-166">*client_ptr* は、PTP クライアントを指します。</span><span class="sxs-lookup"><span data-stu-id="55e09-166">*client_ptr* points to PTP client.</span></span>
* <span data-ttu-id="55e09-167">*event* では、コールバック イベントを指定します。有効な値は、次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="55e09-167">*event* specifies the callback event, valid values are defined as:</span></span>
  * <span data-ttu-id="55e09-168">**NX_PTP_CLIENT_EVENT_MASTER**: マスター クロックが選択されました。</span><span class="sxs-lookup"><span data-stu-id="55e09-168">**NX_PTP_CLIENT_EVENT_MASTER** A master clock is selected.</span></span>
  * <span data-ttu-id="55e09-169">**NX_PTP_CLIENT_EVENT_SYNC**: PTP クライアントが調整されました。</span><span class="sxs-lookup"><span data-stu-id="55e09-169">**NX_PTP_CLIENT_EVENT_SYNC** PTP client is calibrated.</span></span>
  * <span data-ttu-id="55e09-170">**NX_PTP_CLIENT_EVENT_TIMEOUT**: マスター クロックがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="55e09-170">**NX_PTP_CLIENT_EVENT_TIMEOUT** Master clock is timeout.</span></span>
* <span data-ttu-id="55e09-171">*event_data* では、イベントに関連するデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="55e09-171">*event_data* specifies the data related to event.</span></span> <span data-ttu-id="55e09-172">イベントが **NX_PTP_CLIENT_EVENT_MASTER** の場合、event_data は `NX_PTP_CLIENT_MASTER` インスタンスを参照します。</span><span class="sxs-lookup"><span data-stu-id="55e09-172">When event is **NX_PTP_CLIENT_EVENT_MASTER**, event_data points to `NX_PTP_CLIENT_MASTER` instance.</span></span> <span data-ttu-id="55e09-173">イベントが **NX_PTP_CLIENT_EVENT_SYNC** の場合、event_data は `NX_PTP_CLIENT_SYNC` インスタンスを参照します。</span><span class="sxs-lookup"><span data-stu-id="55e09-173">When event is **NX_PTP_CLIENT_EVENT_SYNC**, event data points to `NX_PTP_CLIENT_SYNC` instance.</span></span>

## <a name="netx-duo-ptp-client-communication"></a><span data-ttu-id="55e09-174">NetX Duo PTP クライアント通信</span><span class="sxs-lookup"><span data-stu-id="55e09-174">NetX Duo PTP Client Communication</span></span>
<span data-ttu-id="55e09-175">前述のように、NetX Duo PTP クライアントでは、遅延要求 - 応答メカニズムのみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="55e09-175">As mentioned previously, NetX Duo PTP client only supports delay request-response mechanism.</span></span> <span data-ttu-id="55e09-176">このメカニズムでは、クライアントとマスター クロック間の平均パス遅延が次のように測定されます。</span><span class="sxs-lookup"><span data-stu-id="55e09-176">This mechanism measures the mean path delay between the client and the master clock as below:</span></span>
1. <span data-ttu-id="55e09-177">クライアントは、マスターから *Announce* メッセージを受信すると、それをベスト マスターとして選択します。</span><span class="sxs-lookup"><span data-stu-id="55e09-177">Client receives *Announce* message from master and select it as best master.</span></span>
1. <span data-ttu-id="55e09-178">クライアントは、マスターから *Sync* メッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="55e09-178">Client receives *Sync* message from master.</span></span> <span data-ttu-id="55e09-179">タイムスタンプ *t1* は、このメッセージの発信元タイムスタンプです。</span><span class="sxs-lookup"><span data-stu-id="55e09-179">The timestamp *t1* is the origin timestamp in this message.</span></span> <span data-ttu-id="55e09-180">このメッセージを受信すると、タイムスタンプ *t2* がローカル クロックから読み取られます。</span><span class="sxs-lookup"><span data-stu-id="55e09-180">The timestamp *t2* is read from local clock when this message is received.</span></span>
1. <span data-ttu-id="55e09-181">クライアントは、マスターから *Follow_Up* メッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="55e09-181">Client receives *Follow_Up* message from master.</span></span> <span data-ttu-id="55e09-182">このメッセージは省略可能であり、*Sync* フラグの 2 ステップが設定されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="55e09-182">This message is optional and valid only when two step in *Sync* flag is set.</span></span> <span data-ttu-id="55e09-183">その後、タイムスタンプ *t1* がこのメッセージの発信元タイムスタンプに更新されます。</span><span class="sxs-lookup"><span data-stu-id="55e09-183">Then the timestamp *t1* is updated to the origin timestamp in this message.</span></span>
1. <span data-ttu-id="55e09-184">クライアントは、*Delay_Req* メッセージをマスターに送信します。</span><span class="sxs-lookup"><span data-stu-id="55e09-184">Client sends *Delay_Req* message to master.</span></span> <span data-ttu-id="55e09-185">メッセージが送信されると、タイムスタンプ *t3* がローカル クロックから読み取られます。</span><span class="sxs-lookup"><span data-stu-id="55e09-185">The timestamp *t3* is read from local clock when the message is transmitted.</span></span>
1. <span data-ttu-id="55e09-186">クライアントは、マスターから *Delay_Resp* メッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="55e09-186">Client receives *Delay_Resp* message from master.</span></span> <span data-ttu-id="55e09-187">タイムスタンプ *t4* は、このメッセージの受信タイムスタンプです。</span><span class="sxs-lookup"><span data-stu-id="55e09-187">The timestamp *t4* is the receive timestamp in this message.</span></span>

<span data-ttu-id="55e09-188">平均パス遅延は、次のように計算されます。</span><span class="sxs-lookup"><span data-stu-id="55e09-188">The mean path delay is computed as shown below.</span></span>
```C
<meanPathDelay>=[(t2-t1)+(t4-t3)]/2
```
<span data-ttu-id="55e09-189">マスターからのオフセットは、次のように計算されます。</span><span class="sxs-lookup"><span data-stu-id="55e09-189">The offset from master is computed as shown below.</span></span>
```C
<offsetFromMaster>=client_clock-master_clock
                  =(t2-t1)-<meanPathDelay>
```

> [!NOTE]
> <span data-ttu-id="55e09-190">"\*\*\*\*correctionField\*\* _ は計算時に無視されます。_"</span><span class="sxs-lookup"><span data-stu-id="55e09-190">\*The \***correctionField** _ is ignored during the calculation._</span></span>