---
title: 第 3 章 - Azure RTOS NetX Duo PTP クライアント サービスの説明
description: この章では、すべての NetX Duo PTP クライアント サービスをアルファベット順に説明します。
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b4cdeca81c157934e35a219cd5535ec38f2c0746
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810619"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-ptp-client-services"></a><span data-ttu-id="8afb3-103">第 3 章 - Azure RTOS NetX Duo PTP クライアント サービスの説明</span><span class="sxs-lookup"><span data-stu-id="8afb3-103">Chapter 3 - Description of Azure RTOS NetX Duo PTP Client Services</span></span>

<span data-ttu-id="8afb3-104">この章では、すべての NetX Duo PTP クライアント サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-104">This chapter contains a description of all NetX Duo PTP client services (listed below) in alphabetical order.</span></span>

[!NOTE]
> <span data-ttu-id="8afb3-105">"*以下の API 関数の説明の「**戻り値**」セクションでは、\*\*太字*\* の値は API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。\* "</span><span class="sxs-lookup"><span data-stu-id="8afb3-105">*In the **Return Values** section in the following API function descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.*</span></span>

## <a name="nx_ptp_client_create"></a><span data-ttu-id="8afb3-106">nx_ptp_client_create</span><span class="sxs-lookup"><span data-stu-id="8afb3-106">nx_ptp_client_create</span></span>

<span data-ttu-id="8afb3-107">PTP クライアント インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-107">Create a PTP client instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="8afb3-108">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8afb3-108">Prototype</span></span>

```C
UINT nx_ptp_client_create(
    NX_PTP_CLIENT *client_ptr, NX_IP *ip_ptr, 
    UINT interface_index,
    NX_PACKET_POOL *packet_pool_ptr, 
    UINT thread_priority, 
    UCHAR *thread_stack, 
    UINT stack_size,
    NX_PTP_CLIENT_CLOCK_CALLBACK clock_callback, 
    VOID *clock_callback_data);
```

### <a name="description"></a><span data-ttu-id="8afb3-109">説明</span><span class="sxs-lookup"><span data-stu-id="8afb3-109">Description</span></span>

<span data-ttu-id="8afb3-110">このサービスでは、PTP クライアントのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-110">This service creates an instance of the PTP client.</span></span>

<span data-ttu-id="8afb3-111">アプリケーションでは、PTP クライアントがパケットを送信するための IP インスタンスとパケット プールを最初に作成する必要がある点に注意します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-111">Note that the  application must first create an IP instance and a packet pool for the PTP client to transmit packets.</span></span> <span data-ttu-id="8afb3-112">パケット プールについては、アプリケーションは IP インスタンスで同じパケット プールを使用することも、PTP クライアント専用のパケット プールを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="8afb3-112">For the packet pool, application may use the same packet pool in the IP instance; or it can create a dedicated packet pool for PTP client.</span></span>  <span data-ttu-id="8afb3-113">専用パケット プールのアプローチには、小さいパケット (IPv6 が使用されている場合は 128 バイト、IPv4 のみの場合は 108 バイト) の使用という利点があります。</span><span class="sxs-lookup"><span data-stu-id="8afb3-113">The dedicated packet pool approach has the advantage of using small packets (128 bytes packets if IPv6 is used, or 108 bytes for IPv4-only).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8afb3-114">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8afb3-114">Input Parameters</span></span>
* <span data-ttu-id="8afb3-115">**client_ptr**: 作成する PTP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-115">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="8afb3-116">**ip_ptr**: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-116">**ip_ptr** Pointer to IP instance</span></span>
* <span data-ttu-id="8afb3-117">**interface_index**: PTP ネットワーク インターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="8afb3-117">**interface_index** Index of PTP network interface</span></span>
* <span data-ttu-id="8afb3-118">**packet_pool_ptr**: クライアントのパケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-118">**packet_pool_ptr** Pointer to client packet pool</span></span>
* <span data-ttu-id="8afb3-119">**thread_priority**: PTP スレッドの優先順位</span><span class="sxs-lookup"><span data-stu-id="8afb3-119">**thread_priority**  Priority of PTP thread</span></span>
* <span data-ttu-id="8afb3-120">**thread_stack**: スレッド スタックへのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-120">**thread_stack** Pointer to thread stack</span></span>
* <span data-ttu-id="8afb3-121">**stack_size**: スレッド スタックのサイズ</span><span class="sxs-lookup"><span data-stu-id="8afb3-121">**stack_size** Size of thread stack</span></span>
* <span data-ttu-id="8afb3-122">**clock_callback**: PTP クロック コールバック</span><span class="sxs-lookup"><span data-stu-id="8afb3-122">**clock_callback** PTP clock callback</span></span>
* <span data-ttu-id="8afb3-123">**clock_callback_data**: クロック コールバックのデータ</span><span class="sxs-lookup"><span data-stu-id="8afb3-123">**clock_callback_data** Data for the clock callback</span></span>

### <a name="return-values"></a><span data-ttu-id="8afb3-124">戻り値</span><span class="sxs-lookup"><span data-stu-id="8afb3-124">Return Values</span></span>
* <span data-ttu-id="8afb3-125">**NX_SUCCESS**: (0x00) クライアントが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="8afb3-125">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="8afb3-126">**NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD**: (0xD04) パケット ペイロードが小さすぎます</span><span class="sxs-lookup"><span data-stu-id="8afb3-126">**NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) Packet payload too small</span></span>
* <span data-ttu-id="8afb3-127">**NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE**: (0xD05) クロック コールバックに失敗しました</span><span class="sxs-lookup"><span data-stu-id="8afb3-127">**NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) Failure on clock callback</span></span>
* <span data-ttu-id="8afb3-128">**status**: NetX Duo および ThreadX サービス呼び出しの完了状態</span><span class="sxs-lookup"><span data-stu-id="8afb3-128">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
* <span data-ttu-id="8afb3-129">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="8afb3-129">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
* <span data-ttu-id="8afb3-130">NX_INVALID_INTERFACE: (0x4C) インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="8afb3-130">NX_INVALID_INTERFACE (0x4C) Invalid interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8afb3-131">許可元</span><span class="sxs-lookup"><span data-stu-id="8afb3-131">Allowed From</span></span>
<span data-ttu-id="8afb3-132">Threads</span><span class="sxs-lookup"><span data-stu-id="8afb3-132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8afb3-133">例</span><span class="sxs-lookup"><span data-stu-id="8afb3-133">Example</span></span>
```C
/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_delete"></a><span data-ttu-id="8afb3-134">nx_ptp_client_delete</span><span class="sxs-lookup"><span data-stu-id="8afb3-134">nx_ptp_client_delete</span></span>

<span data-ttu-id="8afb3-135">PTP クライアント インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-135">Deletes a PTP client instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="8afb3-136">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8afb3-136">Prototype</span></span>

```C
UINT nx_ptp_client_delete(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="8afb3-137">説明</span><span class="sxs-lookup"><span data-stu-id="8afb3-137">Description</span></span>

<span data-ttu-id="8afb3-138">このサービスでは、PTP クライアントのインスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-138">This service deletes an instance of the PTP client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8afb3-139">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8afb3-139">Input Parameters</span></span>
* <span data-ttu-id="8afb3-140">**client_ptr**: 削除する PTP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-140">**client_ptr** Pointer to PTP client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="8afb3-141">戻り値</span><span class="sxs-lookup"><span data-stu-id="8afb3-141">Return Values</span></span>
* <span data-ttu-id="8afb3-142">**NX_SUCCESS**: (0x00) クライアントが正常に削除されました</span><span class="sxs-lookup"><span data-stu-id="8afb3-142">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
* <span data-ttu-id="8afb3-143">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="8afb3-143">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8afb3-144">許可元</span><span class="sxs-lookup"><span data-stu-id="8afb3-144">Allowed From</span></span>
<span data-ttu-id="8afb3-145">Threads</span><span class="sxs-lookup"><span data-stu-id="8afb3-145">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8afb3-146">例</span><span class="sxs-lookup"><span data-stu-id="8afb3-146">Example</span></span>
```C
/* Delete the PTP client instance */
status = nx_ptp_client_delete(&ptp_client);

/* If the client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_master_info_get"></a><span data-ttu-id="8afb3-147">nx_ptp_client_master_info_get</span><span class="sxs-lookup"><span data-stu-id="8afb3-147">nx_ptp_client_master_info_get</span></span>

<span data-ttu-id="8afb3-148">マスター クロック情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-148">Get master clock information.</span></span>

### <a name="prototype"></a><span data-ttu-id="8afb3-149">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8afb3-149">Prototype</span></span>

```C
UINT nx_ptp_client_master_info_get(
    NX_PTP_CLIENT_MASTER *master_ptr, 
    NXD_ADDRESS *address, 
    UCHAR **port_identity, 
    UINT *port_identity_length, 
    UCHAR *priority1, 
    UCHAR *priority2, 
    UCHAR *clock_class, UCHAR *clock_accuracy, 
    USHORT *clock_variance, 
    UCHAR **grandmaster_identity,
    UINT *grandmaster_identity_length, 
    USHORT *steps_removed, 
    UCHAR *time_source);
```

### <a name="description"></a><span data-ttu-id="8afb3-150">説明</span><span class="sxs-lookup"><span data-stu-id="8afb3-150">Description</span></span>
<span data-ttu-id="8afb3-151">このサービスは、マスター クロックの情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-151">This service gets information of master clock.</span></span> <span data-ttu-id="8afb3-152">マスター制御ブロックは、イベント コールバック関数を介してユーザー アプリケーションに渡されます。</span><span class="sxs-lookup"><span data-stu-id="8afb3-152">The master control block is passed to user application through event callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8afb3-153">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8afb3-153">Input Parameters</span></span>
* <span data-ttu-id="8afb3-154">**master_ptr**: PTP マスター クロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-154">**master_ptr** Pointer to PTP master clock</span></span>
* <span data-ttu-id="8afb3-155">**address**: マスター クロックのアドレス</span><span class="sxs-lookup"><span data-stu-id="8afb3-155">**address** Address of master clock</span></span>
* <span data-ttu-id="8afb3-156">**port_identity**: PTP マスター ポートと ID</span><span class="sxs-lookup"><span data-stu-id="8afb3-156">**port_identity** PTP master port and identity</span></span>
* <span data-ttu-id="8afb3-157">**port_identity_length**: PTP マスター ポートと ID の長さ</span><span class="sxs-lookup"><span data-stu-id="8afb3-157">**port_identity_length** Length of PTP master port and identity</span></span>
* <span data-ttu-id="8afb3-158">**priority1**: PTP マスター クロックの Priority1</span><span class="sxs-lookup"><span data-stu-id="8afb3-158">**priority1** Priority1 of PTP master clock</span></span>
* <span data-ttu-id="8afb3-159">**priority2**: PTP マスター クロックの Priority2</span><span class="sxs-lookup"><span data-stu-id="8afb3-159">**priority2** Priority2 of PTP master clock</span></span>
* <span data-ttu-id="8afb3-160">**clock_class**: PTP マスター クロックのクラス</span><span class="sxs-lookup"><span data-stu-id="8afb3-160">**clock_class** Class of PTP master clock</span></span>
* <span data-ttu-id="8afb3-161">**clock_accuracy**: PTP マスター クロックの精度</span><span class="sxs-lookup"><span data-stu-id="8afb3-161">**clock_accuracy** Accuracy of PTP master clock</span></span>
* <span data-ttu-id="8afb3-162">**clock_variance**: PTP マスター クロックの差異</span><span class="sxs-lookup"><span data-stu-id="8afb3-162">**clock_variance** Variance of PTP master clock</span></span>
* <span data-ttu-id="8afb3-163">**grandmaster_identity**: グランドマスター クロックの ID</span><span class="sxs-lookup"><span data-stu-id="8afb3-163">**grandmaster_identity** Identity of grandmaster clock</span></span>
* <span data-ttu-id="8afb3-164">**grandmaster_identity_length**: グランドマスター ID の長さ</span><span class="sxs-lookup"><span data-stu-id="8afb3-164">**grandmaster_identity_length** Length of grandmaster Identity</span></span>
* <span data-ttu-id="8afb3-165">**steps_removed**: PTP ヘッダーから削除されたステップ</span><span class="sxs-lookup"><span data-stu-id="8afb3-165">**steps_removed** Steps removed from PTP header</span></span>
* <span data-ttu-id="8afb3-166">**time_source**: グランドマスター クロックによって使用されるタイマーのソース</span><span class="sxs-lookup"><span data-stu-id="8afb3-166">**time_source** The source of timer used by grandmaster clock</span></span>

### <a name="return-values"></a><span data-ttu-id="8afb3-167">戻り値</span><span class="sxs-lookup"><span data-stu-id="8afb3-167">Return Values</span></span>
* <span data-ttu-id="8afb3-168">**NX_SUCCESS**: (0x00) マスター クロック情報が正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="8afb3-168">**NX_SUCCESS** (0x00) Get master clock information successfully</span></span>
* <span data-ttu-id="8afb3-169">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="8afb3-169">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8afb3-170">許可元</span><span class="sxs-lookup"><span data-stu-id="8afb3-170">Allowed From</span></span>
<span data-ttu-id="8afb3-171">Threads</span><span class="sxs-lookup"><span data-stu-id="8afb3-171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8afb3-172">例</span><span class="sxs-lookup"><span data-stu-id="8afb3-172">Example</span></span>
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
NXD_ADDRESS address;
UCHAR *port_identity;
UINT port_identity_length;
UCHAR priority1, priority2;
UCHAR clock_class, clock_accuracy;
USHORT clock_variance;
UCHAR *grandmaster_identity;
UINT grandmaster_identity_length;
USHORT steps_removed;
UCHAR time_source;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_MASTER:
        {
            status = nx_ptp_client_master_info_get((NX_PTP_CLIENT_MASTER *)event_data, 
                                                   &address, &port_identity,
                                                   &port_identity_length, &priority1, 
                                                   &priority2, &clock_class,
                                                   &clock_accuracy, &clock_variance, 
                                                   &grandmaster_identity,
                                                   &grandmaster_identity_length, 
                                                   &steps_removed, &time_source);

            /* If the master clock information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_packet_timestamp_notify"></a><span data-ttu-id="8afb3-173">nx_ptp_client_packet_timestamp_notify</span><span class="sxs-lookup"><span data-stu-id="8afb3-173">nx_ptp_client_packet_timestamp_notify</span></span>

<span data-ttu-id="8afb3-174">パケットのタイムスタンプを PTP クライアントに通知します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-174">Notify PTP client the timestamp of the packet.</span></span>

### <a name="prototype"></a><span data-ttu-id="8afb3-175">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8afb3-175">Prototype</span></span>

```C
VOID nx_ptp_client_packet_timestamp_notify(
    NX_PTP_CLIENT *client_ptr, 
    NX_PACKET *packet_ptr, 
    NX_PTP_TIME *timestamp_ptr);
```

### <a name="description"></a><span data-ttu-id="8afb3-176">説明</span><span class="sxs-lookup"><span data-stu-id="8afb3-176">Description</span></span>
<span data-ttu-id="8afb3-177">このサービスは、パケットがタイムスタンプ付きで送信されたことを PTP クライアントに通知します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-177">This service notifies the PTP client that packet is transmitted with timestamp.</span></span> <span data-ttu-id="8afb3-178">このサービスはネットワーク ドライバー用に設計されており、パケットが送信されるときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8afb3-178">This service is designed for network driver and invoked when the packet is transmitted.</span></span> <span data-ttu-id="8afb3-179">通常、タイムスタンプはハードウェアによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="8afb3-179">The timestamp is usually generated by hardware.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8afb3-180">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8afb3-180">Input Parameters</span></span>
* <span data-ttu-id="8afb3-181">**client_ptr**: 作成する PTP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-181">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="8afb3-182">**packet_ptr**: 送信される PTP パケットへのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-182">**packet_ptr** Pointer to PTP packet that is transmitted</span></span>
* <span data-ttu-id="8afb3-183">**timestamp_ptr**: PTP パケットのタイムスタンプへのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-183">**timestamp_ptr** Pointer to timestamp of PTP packet</span></span>

### <a name="return-values"></a><span data-ttu-id="8afb3-184">戻り値</span><span class="sxs-lookup"><span data-stu-id="8afb3-184">Return Values</span></span>
<span data-ttu-id="8afb3-185">None</span><span class="sxs-lookup"><span data-stu-id="8afb3-185">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8afb3-186">許可元</span><span class="sxs-lookup"><span data-stu-id="8afb3-186">Allowed From</span></span>
<span data-ttu-id="8afb3-187">Threads</span><span class="sxs-lookup"><span data-stu-id="8afb3-187">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8afb3-188">例</span><span class="sxs-lookup"><span data-stu-id="8afb3-188">Example</span></span>
```C
/* Call notification callback */
nx_ptp_client_packet_timestamp_notify(client_ptr, packet_ptr, &ts);
```

## <a name="nx_ptp_client_soft_clock_callback"></a><span data-ttu-id="8afb3-189">nx_ptp_client_soft_clock_callback</span><span class="sxs-lookup"><span data-stu-id="8afb3-189">nx_ptp_client_soft_clock_callback</span></span>

<span data-ttu-id="8afb3-190">PTP クロックのソフトウェア実装。</span><span class="sxs-lookup"><span data-stu-id="8afb3-190">Software implementation of a PTP clock.</span></span>

### <a name="prototype"></a><span data-ttu-id="8afb3-191">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8afb3-191">Prototype</span></span>

```C
UINT nx_ptp_client_soft_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```

### <a name="description"></a><span data-ttu-id="8afb3-192">説明</span><span class="sxs-lookup"><span data-stu-id="8afb3-192">Description</span></span>
<span data-ttu-id="8afb3-193">このコールバック関数は、PTP のシミュレートされた低解像度クロック ソースとして機能します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-193">This callback function serves as a simulated low resolution clock source for PTP.</span></span> <span data-ttu-id="8afb3-194">このルーチンは参照用として提供されており、運用環境では使用できません。</span><span class="sxs-lookup"><span data-stu-id="8afb3-194">This routine is provided as a reference and cannot be used for production.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8afb3-195">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8afb3-195">Input Parameters</span></span>
* <span data-ttu-id="8afb3-196">**client_ptr**: 作成する PTP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-196">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="8afb3-197">**operation**: コールバック操作。有効な値は次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="8afb3-197">**operation** Callback operation, valid values are defined as:</span></span>
  * <span data-ttu-id="8afb3-198">**NX_PTP_CLIENT_CLOCK_INIT**: クロックを初期化します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-198">**NX_PTP_CLIENT_CLOCK_INIT** Initialize clock.</span></span>
  * <span data-ttu-id="8afb3-199">**NX_PTP_CLIENT_CLOCK_SET**: `time_ptr` で指定された現在のタイムスタンプを設定します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-199">**NX_PTP_CLIENT_CLOCK_SET** Set current timestamp specified by `time_ptr`.</span></span>
  * <span data-ttu-id="8afb3-200">**NX_PTP_CLIENT_CLOCK_GET**: 現在のタイムスタンプを `time_ptr` に返します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-200">**NX_PTP_CLIENT_CLOCK_GET** Return current timestamp to `time_ptr`.</span></span>
  * <span data-ttu-id="8afb3-201">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT**: `packet_ptr` から `time_ptr` にタイムスタンプを抽出します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-201">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extract timestamp from `packet_ptr` to `time_ptr`.</span></span>
  * <span data-ttu-id="8afb3-202">**NX_PTP_CLIENT_CLOCK_ADJUST**: 現在のタイムスタンプを *1* 秒未満に調整します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-202">**NX_PTP_CLIENT_CLOCK_ADJUST** Adjust current timestamp less than *1* second.</span></span>
  * <span data-ttu-id="8afb3-203">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE**: 送信されたタイムスタンプを PTP クライアントに通知する必要がある `packet_ptr` をマークします。</span><span class="sxs-lookup"><span data-stu-id="8afb3-203">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Mark the `packet_ptr` which requires to notify PTP client the timestamp when it is transmitted.</span></span>
  * <span data-ttu-id="8afb3-204">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE**: ソフト タイマーを更新します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-204">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Update soft timer.</span></span> <span data-ttu-id="8afb3-205">ハードウェア クロックではこれを無視できます。</span><span class="sxs-lookup"><span data-stu-id="8afb3-205">It can be ignored by hardware clock.</span></span>
* <span data-ttu-id="8afb3-206">**time_ptr**: タイムスタンプへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8afb3-206">**time_ptr** Pointer to timestamp.</span></span>
* <span data-ttu-id="8afb3-207">**packet_ptr**: パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8afb3-207">**packet_ptr** Pointer to packet.</span></span>
* <span data-ttu-id="8afb3-208">**callback_data**: 不透明なコールバック データへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8afb3-208">**callback_data** Pointer to opaque callback data.</span></span>

### <a name="return-values"></a><span data-ttu-id="8afb3-209">戻り値</span><span class="sxs-lookup"><span data-stu-id="8afb3-209">Return Values</span></span>
* <span data-ttu-id="8afb3-210">**NX_SUCCESS**: (0x00) 操作が正常に完了しました</span><span class="sxs-lookup"><span data-stu-id="8afb3-210">**NX_SUCCESS** (0x00) Operation successfully</span></span>
* <span data-ttu-id="8afb3-211">**NX_PTP_PARAM_ERROR**: (0xD03) パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="8afb3-211">**NX_PTP_PARAM_ERROR** (0xD03) Invalid parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8afb3-212">許可元</span><span class="sxs-lookup"><span data-stu-id="8afb3-212">Allowed From</span></span>
<span data-ttu-id="8afb3-213">PTP 内部</span><span class="sxs-lookup"><span data-stu-id="8afb3-213">PTP internal</span></span>

### <a name="example"></a><span data-ttu-id="8afb3-214">例</span><span class="sxs-lookup"><span data-stu-id="8afb3-214">Example</span></span>
```C/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              nx_ptp_client_soft_clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_start"></a><span data-ttu-id="8afb3-215">nx_ptp_client_start</span><span class="sxs-lookup"><span data-stu-id="8afb3-215">nx_ptp_client_start</span></span>

<span data-ttu-id="8afb3-216">PTP クライアントを起動します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-216">Start PTP client.</span></span>

### <a name="prototype"></a><span data-ttu-id="8afb3-217">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8afb3-217">Prototype</span></span>

```C
UINT nx_ptp_client_start(
    NX_PTP_CLIENT *client_ptr, 
    UCHAR *client_port_identity_ptr, 
    UINT client_port_identity_length,
    UINT domain, 
    UINT transport_specific, 
    NX_PTP_CLIENT_EVENT_CALLBACK event_callback,
    VOID *event_callback_data)
```

### <a name="description"></a><span data-ttu-id="8afb3-218">説明</span><span class="sxs-lookup"><span data-stu-id="8afb3-218">Description</span></span>
<span data-ttu-id="8afb3-219">このサービスは、以前に作成された PTP クライアント インスタンスを起動します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-219">This service starts a previously created PTP client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8afb3-220">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8afb3-220">Input Parameters</span></span>
* <span data-ttu-id="8afb3-221">**client_ptr**: 作成する PTP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-221">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="8afb3-222">**client_port_identity_ptr**: クライアント ポートと ID へのポインター。NULL にすることもできます</span><span class="sxs-lookup"><span data-stu-id="8afb3-222">**client_port_identity_ptr** Pointer to client port and identity, it can be NULL</span></span>
* <span data-ttu-id="8afb3-223">**client_port_identity_length**: クライアント ポートと ID の長さ。</span><span class="sxs-lookup"><span data-stu-id="8afb3-223">**client_port_identity_length** Length of client port and identity.</span></span> <span data-ttu-id="8afb3-224">client_port_identity_ptr が NULL または NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10) の場合は、0 である必要があります</span><span class="sxs-lookup"><span data-stu-id="8afb3-224">It must be 0 if client_port_identity_ptr is NULL or NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)</span></span>
* <span data-ttu-id="8afb3-225">**domain**: PTP クロック ドメイン</span><span class="sxs-lookup"><span data-stu-id="8afb3-225">**domain** PTP clock domain</span></span>
* <span data-ttu-id="8afb3-226">**transport_specific**: 4 ビットの転送固有</span><span class="sxs-lookup"><span data-stu-id="8afb3-226">**transport_specific** 4 bits of transport specific</span></span>
* <span data-ttu-id="8afb3-227">**event_callback**: イベントで呼び出されるコールバック関数</span><span class="sxs-lookup"><span data-stu-id="8afb3-227">**event_callback** Callback function invoked on event</span></span>
* <span data-ttu-id="8afb3-228">**event_callback_data**: イベント コールバックのデータ</span><span class="sxs-lookup"><span data-stu-id="8afb3-228">**event_callback_data** Data for the event callback</span></span>

### <a name="return-values"></a><span data-ttu-id="8afb3-229">戻り値</span><span class="sxs-lookup"><span data-stu-id="8afb3-229">Return Values</span></span>
* <span data-ttu-id="8afb3-230">**NX_SUCCESS**: (0x00) クライアントが正常に起動されました</span><span class="sxs-lookup"><span data-stu-id="8afb3-230">**NX_SUCCESS** (0x00) Client successfully started</span></span>
* <span data-ttu-id="8afb3-231">**NX_PTP_CLIENT_ALREADY_STARTED**: (0xD02) PTP クライアントは既に起動されています</span><span class="sxs-lookup"><span data-stu-id="8afb3-231">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP client already started</span></span>
* <span data-ttu-id="8afb3-232">**status**: NetX Duo および ThreadX サービス呼び出しの完了状態</span><span class="sxs-lookup"><span data-stu-id="8afb3-232">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
* <span data-ttu-id="8afb3-233">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="8afb3-233">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8afb3-234">許可元</span><span class="sxs-lookup"><span data-stu-id="8afb3-234">Allowed From</span></span>
<span data-ttu-id="8afb3-235">Threads</span><span class="sxs-lookup"><span data-stu-id="8afb3-235">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8afb3-236">例</span><span class="sxs-lookup"><span data-stu-id="8afb3-236">Example</span></span>
```C
status = nx_ptp_client_start(&ptp_client, NX_NULL, 0, 0, 0, ptp_event_callback, NX_NULL);

/* If the client was successfully started, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_stop"></a><span data-ttu-id="8afb3-237">nx_ptp_client_stop</span><span class="sxs-lookup"><span data-stu-id="8afb3-237">nx_ptp_client_stop</span></span>

<span data-ttu-id="8afb3-238">PTP クライアントを停止します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-238">Stop PTP client.</span></span>  <span data-ttu-id="8afb3-239">PTP クライアントを停止した後は、PTP パケットの処理も送信も行われなくなります。</span><span class="sxs-lookup"><span data-stu-id="8afb3-239">After the PTP client is stopped, it does not process PTP packets, nor does it transmit PTP packets.</span></span>

### <a name="prototype"></a><span data-ttu-id="8afb3-240">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8afb3-240">Prototype</span></span>

```C
UINT nx_ptp_client_stop(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="8afb3-241">説明</span><span class="sxs-lookup"><span data-stu-id="8afb3-241">Description</span></span>
<span data-ttu-id="8afb3-242">このサービスは、以前に作成され、起動された PTP クライアント インスタンスを停止します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-242">This service stops a previously created and started PTP client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8afb3-243">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8afb3-243">Input Parameters</span></span>
* <span data-ttu-id="8afb3-244">**client_ptr**: 停止する PTP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-244">**client_ptr** Pointer to PTP client to stop</span></span>

### <a name="return-values"></a><span data-ttu-id="8afb3-245">戻り値</span><span class="sxs-lookup"><span data-stu-id="8afb3-245">Return Values</span></span>
* <span data-ttu-id="8afb3-246">**NX_SUCCESS**: (0x00) クライアントが正常に停止されました</span><span class="sxs-lookup"><span data-stu-id="8afb3-246">**NX_SUCCESS** (0x00) Client successfully stopped</span></span>
* <span data-ttu-id="8afb3-247">**NX_PTP_CLIENT_NOT_STARTED**: (0xD01) クライアントが起動していません</span><span class="sxs-lookup"><span data-stu-id="8afb3-247">**NX_PTP_CLIENT_NOT_STARTED** (0xD01) Client not started</span></span>
* <span data-ttu-id="8afb3-248">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="8afb3-248">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8afb3-249">許可元</span><span class="sxs-lookup"><span data-stu-id="8afb3-249">Allowed From</span></span>
<span data-ttu-id="8afb3-250">Threads</span><span class="sxs-lookup"><span data-stu-id="8afb3-250">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8afb3-251">例</span><span class="sxs-lookup"><span data-stu-id="8afb3-251">Example</span></span>
```C
status = nx_ptp_client_stop(&ptp_client);

/* If the client was successfully stopped, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_sync_info_get"></a><span data-ttu-id="8afb3-252">nx_ptp_client_sync_info_get</span><span class="sxs-lookup"><span data-stu-id="8afb3-252">nx_ptp_client_sync_info_get</span></span>

<span data-ttu-id="8afb3-253">同期情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-253">Get Sync information.</span></span>

### <a name="prototype"></a><span data-ttu-id="8afb3-254">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8afb3-254">Prototype</span></span>

```C
UINT nx_ptp_client_sync_info_get(
    NX_PTP_CLIENT_SYNC *sync_ptr, 
    USHORT *flags, 
    SHORT *utc_offset);
```

### <a name="description"></a><span data-ttu-id="8afb3-255">説明</span><span class="sxs-lookup"><span data-stu-id="8afb3-255">Description</span></span>
<span data-ttu-id="8afb3-256">このサービスは、Sync メッセージの情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-256">This service gets information of Sync message.</span></span> <span data-ttu-id="8afb3-257">Sync 制御ブロックは、イベント コールバック関数を介してユーザー アプリケーションに渡されます。</span><span class="sxs-lookup"><span data-stu-id="8afb3-257">The Sync control block is passed to user application through event callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8afb3-258">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8afb3-258">Input Parameters</span></span>
* <span data-ttu-id="8afb3-259">**client_ptr**: 作成する PTP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-259">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="8afb3-260">**flags**: Sync メッセージのフラグ</span><span class="sxs-lookup"><span data-stu-id="8afb3-260">**flags** Flags in Sync message</span></span>
* <span data-ttu-id="8afb3-261">**utc_offset**: TAI と UTC の間のオフセット</span><span class="sxs-lookup"><span data-stu-id="8afb3-261">**utc_offset** Offset between TAI and UTC</span></span>

### <a name="return-values"></a><span data-ttu-id="8afb3-262">戻り値</span><span class="sxs-lookup"><span data-stu-id="8afb3-262">Return Values</span></span>
* <span data-ttu-id="8afb3-263">**NX_SUCCESS**: (0x00) 同期情報が正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="8afb3-263">**NX_SUCCESS** (0x00) Get Sync information successfully</span></span>
* <span data-ttu-id="8afb3-264">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="8afb3-264">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8afb3-265">許可元</span><span class="sxs-lookup"><span data-stu-id="8afb3-265">Allowed From</span></span>
<span data-ttu-id="8afb3-266">Threads</span><span class="sxs-lookup"><span data-stu-id="8afb3-266">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8afb3-267">例</span><span class="sxs-lookup"><span data-stu-id="8afb3-267">Example</span></span>
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
USHORT utc_offset;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_SYNC:
        {
            nx_ptp_client_sync_info_get((NX_PTP_CLIENT_SYNC *)event_data, NX_NULL, &utc_offset);

            /* If the Sync information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_time_get"></a><span data-ttu-id="8afb3-268">nx_ptp_client_time_get</span><span class="sxs-lookup"><span data-stu-id="8afb3-268">nx_ptp_client_time_get</span></span>

<span data-ttu-id="8afb3-269">現在の時刻を取得します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-269">Get current time.</span></span>

### <a name="prototype"></a><span data-ttu-id="8afb3-270">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8afb3-270">Prototype</span></span>

```C
UINT nx_ptp_client_time_get(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a><span data-ttu-id="8afb3-271">説明</span><span class="sxs-lookup"><span data-stu-id="8afb3-271">Description</span></span>
<span data-ttu-id="8afb3-272">このサービスは、PTP クロックの現在の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-272">This service gets the current value of the PTP clock.</span></span> <span data-ttu-id="8afb3-273">PTP クライアントがマスター クロックと同期されているかどうかに関係なく使用できます。</span><span class="sxs-lookup"><span data-stu-id="8afb3-273">It is available no matter PTP client is synchronized with master clock or not.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8afb3-274">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8afb3-274">Input Parameters</span></span>
* <span data-ttu-id="8afb3-275">**client_ptr**: 作成する PTP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-275">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="8afb3-276">**time_ptr**: PTP 時刻へのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-276">**time_ptr** Pointer to PTP time</span></span>

### <a name="return-values"></a><span data-ttu-id="8afb3-277">戻り値</span><span class="sxs-lookup"><span data-stu-id="8afb3-277">Return Values</span></span>
* <span data-ttu-id="8afb3-278">**NX_SUCCESS**: (0x00) クライアントが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="8afb3-278">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="8afb3-279">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="8afb3-279">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8afb3-280">許可元</span><span class="sxs-lookup"><span data-stu-id="8afb3-280">Allowed From</span></span>
<span data-ttu-id="8afb3-281">Threads</span><span class="sxs-lookup"><span data-stu-id="8afb3-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8afb3-282">例</span><span class="sxs-lookup"><span data-stu-id="8afb3-282">Example</span></span>
```C
/* Get the PTP clock */
nx_ptp_client_time_get(&ptp_client, &tm);
```

## <a name="nx_ptp_client_time_set"></a><span data-ttu-id="8afb3-283">nx_ptp_client_time_set</span><span class="sxs-lookup"><span data-stu-id="8afb3-283">nx_ptp_client_time_set</span></span>

<span data-ttu-id="8afb3-284">現在の時刻を設定します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-284">Set current time.</span></span>

### <a name="prototype"></a><span data-ttu-id="8afb3-285">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8afb3-285">Prototype</span></span>

```C
UINT nx_ptp_client_time_set(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a><span data-ttu-id="8afb3-286">説明</span><span class="sxs-lookup"><span data-stu-id="8afb3-286">Description</span></span>
<span data-ttu-id="8afb3-287">このサービスは、PTP クロックの現在の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-287">This service sets the current value of the PTP clock.</span></span> <span data-ttu-id="8afb3-288">PTP クライアントが起動する前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8afb3-288">It must be invoked before PTP client starts.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8afb3-289">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8afb3-289">Input Parameters</span></span>
* <span data-ttu-id="8afb3-290">**client_ptr**: 作成する PTP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-290">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="8afb3-291">**time_ptr**: PTP 時刻へのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-291">**time_ptr** Pointer to PTP time</span></span>

### <a name="return-values"></a><span data-ttu-id="8afb3-292">戻り値</span><span class="sxs-lookup"><span data-stu-id="8afb3-292">Return Values</span></span>
* <span data-ttu-id="8afb3-293">**NX_SUCCESS**: (0x00) クライアントが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="8afb3-293">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="8afb3-294">**NX_PTP_CLIENT_ALREADY_STARTED**: (0xD02) PTP クライアントは既に起動されています</span><span class="sxs-lookup"><span data-stu-id="8afb3-294">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP client already started</span></span>
* <span data-ttu-id="8afb3-295">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="8afb3-295">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8afb3-296">許可元</span><span class="sxs-lookup"><span data-stu-id="8afb3-296">Allowed From</span></span>
<span data-ttu-id="8afb3-297">Threads</span><span class="sxs-lookup"><span data-stu-id="8afb3-297">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8afb3-298">例</span><span class="sxs-lookup"><span data-stu-id="8afb3-298">Example</span></span>
```C
/* Set current time before PTP client started.  */
status = nx_ptp_client_time_set(&ptp_client, &tm);
```

## <a name="nx_ptp_client_utility_convert_time_to_date"></a><span data-ttu-id="8afb3-299">nx_ptp_client_utility_convert_time_to_date</span><span class="sxs-lookup"><span data-stu-id="8afb3-299">nx_ptp_client_utility_convert_time_to_date</span></span>

<span data-ttu-id="8afb3-300">PTP 時刻を UTC の日付と時刻に変換します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-300">Convert PTP time to a UTC date and time.</span></span>

### <a name="prototype"></a><span data-ttu-id="8afb3-301">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8afb3-301">Prototype</span></span>

```C
UINT nx_ptp_client_utility_convert_time_to_date(
    NX_PTP_TIME *time_ptr, 
    LONG offset, 
    NX_PTP_DATE_TIME *date_time_ptr);
```

### <a name="description"></a><span data-ttu-id="8afb3-302">説明</span><span class="sxs-lookup"><span data-stu-id="8afb3-302">Description</span></span>
<span data-ttu-id="8afb3-303">このサービスは、PTP 時刻を UTC の日付と時刻に変換します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-303">This service converts PTP time to a UTC date and time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8afb3-304">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8afb3-304">Input Parameters</span></span>
* <span data-ttu-id="8afb3-305">**time_ptr**: PTP 時刻へのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-305">**time_ptr** Pointer to PTP time</span></span>
* <span data-ttu-id="8afb3-306">**offset**: PTP 時刻を追加するための符号付き秒オフセット</span><span class="sxs-lookup"><span data-stu-id="8afb3-306">**offset** Signed second offset to add the PTP time</span></span>
* <span data-ttu-id="8afb3-307">**date_time_ptr**: 変換後の日付へのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-307">**date_time_ptr** Pointer to resulting date</span></span>

### <a name="return-values"></a><span data-ttu-id="8afb3-308">戻り値</span><span class="sxs-lookup"><span data-stu-id="8afb3-308">Return Values</span></span>
* <span data-ttu-id="8afb3-309">**NX_SUCCESS**: (0x00) クライアントが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="8afb3-309">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="8afb3-310">**変換後の日付へのポインター**: (0xD03) 入力パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="8afb3-310">**Pointer to resulting date** (0xD03) Invalid input parameter</span></span>
* <span data-ttu-id="8afb3-311">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="8afb3-311">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8afb3-312">許可元</span><span class="sxs-lookup"><span data-stu-id="8afb3-312">Allowed From</span></span>
<span data-ttu-id="8afb3-313">Threads</span><span class="sxs-lookup"><span data-stu-id="8afb3-313">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8afb3-314">例</span><span class="sxs-lookup"><span data-stu-id="8afb3-314">Example</span></span>
```C
/* convert PTP time to UTC date and time */
status = nx_ptp_client_utility_convert_time_to_date(&tm, -ptp_utc_offset, &date);

/* If the time was successfully converted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_utility_time_diff"></a><span data-ttu-id="8afb3-315">nx_ptp_client_utility_time_diff</span><span class="sxs-lookup"><span data-stu-id="8afb3-315">nx_ptp_client_utility_time_diff</span></span>

<span data-ttu-id="8afb3-316">2 つの PTP 時刻の差を計算します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-316">Diff two PTP times.</span></span>

### <a name="prototype"></a><span data-ttu-id="8afb3-317">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8afb3-317">Prototype</span></span>

```C
UINT nx_ptp_client_utility_time_diff(
    NX_PTP_TIME *time1_ptr, 
    NX_PTP_TIME *time2_ptr, 
    NX_PTP_TIME *result_ptr);
```

### <a name="description"></a><span data-ttu-id="8afb3-318">説明</span><span class="sxs-lookup"><span data-stu-id="8afb3-318">Description</span></span>
<span data-ttu-id="8afb3-319">このサービスは、2 つの PTP 時刻の差を計算します。</span><span class="sxs-lookup"><span data-stu-id="8afb3-319">This service computes the difference between two PTP times.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8afb3-320">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8afb3-320">Input Parameters</span></span>
* <span data-ttu-id="8afb3-321">**time1_ptr**: 最初の PTP 時刻へのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-321">**time1_ptr** Pointer to first PTP time</span></span>
* <span data-ttu-id="8afb3-322">**time2_ptr**: 2 番目の PTP 時刻へのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-322">**time2_ptr** Pointer to second PTP time</span></span>
* <span data-ttu-id="8afb3-323">**result_ptr**: 結果 time1-time2 へのポインター</span><span class="sxs-lookup"><span data-stu-id="8afb3-323">**result_ptr** Pointer to result time1-time2</span></span>

### <a name="return-values"></a><span data-ttu-id="8afb3-324">戻り値</span><span class="sxs-lookup"><span data-stu-id="8afb3-324">Return Values</span></span>
* <span data-ttu-id="8afb3-325">**NX_SUCCESS**: (0x00) クライアントが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="8afb3-325">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="8afb3-326">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="8afb3-326">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8afb3-327">許可元</span><span class="sxs-lookup"><span data-stu-id="8afb3-327">Allowed From</span></span>
<span data-ttu-id="8afb3-328">Threads</span><span class="sxs-lookup"><span data-stu-id="8afb3-328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8afb3-329">例</span><span class="sxs-lookup"><span data-stu-id="8afb3-329">Example</span></span>
```C
/* Diff time.  */
status = nx_ptp_client_utility_time_diff(&time1, &time2, &result);

/* If the calculation was successfully, status = NX_SUCCESS. */
```