---
title: チャプター 3 - Azure RTOS NetX Duo SNTP クライアントのサービスの説明
description: この章では、NetX Duo SNTP クライアントのすべてのサービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 75b2b878cd084ca1c1cdd1eed4333d303fe32ad6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810562"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-sntp-client-services"></a><span data-ttu-id="0df6d-103">チャプター 3 - Azure RTOS NetX Duo SNTP クライアントのサービスの説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-103">Chapter 3 - Description of Azure RTOS NetX Duo SNTP Client Services</span></span>

<span data-ttu-id="0df6d-104">この章では、Azure RTOS NetX Duo SNTP クライアントのすべてのサービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-104">This chapter contains a description of all Azure RTOS NetX Duo SNTP Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="0df6d-105">次の API の説明の「戻り値」セクションで、**太字** の値は、API のエラー チェックを有効にするための **NX_DISABLE_ERROR_CHECKING** を有効にしてもその影響を受けないことを表します。太字でない値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="0df6d-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="0df6d-106">**nx_sntp_client_create**: *SNTP クライアントを作成します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-106">**nx_sntp_client_create**: *Create the SNTP Client*</span></span>
- <span data-ttu-id="0df6d-107">**nx_sntp_client_delete**: *SNTP クライアントを削除します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-107">**nx_sntp_client_delete**: *Delete the SNTP Client*</span></span>
- <span data-ttu-id="0df6d-108">**nx_sntp_client_get_local_time**: *SNTP クライアントのローカル時刻を取得します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-108">**nx_sntp_client_get_local_time**: *Get SNTP Client local time*</span></span>
- <span data-ttu-id="0df6d-109">**nx_sntp_client_get_local_time_extended**: *SNTP クライアントのローカル時刻を取得します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-109">**nx_sntp_client_get_local_time_extended**: *Get SNTP Client local time*</span></span>
- <span data-ttu-id="0df6d-110">**nx_sntp_client_initialize_broadcast**: *IPv4 ブロードキャスト使用のためにクライアントを初期化します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-110">**nx_sntp_client_initialize_broadcast**: *Initialize Client for IPv4 broadcast operation*</span></span>
- <span data-ttu-id="0df6d-111">**nxd_sntp_client_initialize_broadcast**: *IPv6 または IPv4 ブロードキャスト使用のためにクライアントを初期化します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-111">**nxd_sntp_client_initialize_broadcast**: *Initialize Client for IPv6 or IPv4 broadcast operation*</span></span>
- <span data-ttu-id="0df6d-112">**nx_sntp_client_initialize_unicast**: *IPv4 ユニキャスト使用のためにクライアントを初期化します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-112">**nx_sntp_client_initialize_unicast**: *Initialize Client for IPv4 unicast operation*</span></span>
- <span data-ttu-id="0df6d-113">**nxd_sntp_client_initialize_unicast**: *IPv4 または IPv6 ユニキャスト使用のためにクライアントを初期化します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-113">**nxd_sntp_client_initialize_unicast**: *Initialize Client for IPv4 or IPv6 unicast operation*</span></span>
- <span data-ttu-id="0df6d-114">**nx_sntp_client_receiving_udpates**: *クライアントで有効な SNTP 更新を受信中です*</span><span class="sxs-lookup"><span data-stu-id="0df6d-114">**nx_sntp_client_receiving_udpates**: *Client is currently receiving valid SNTP updates*</span></span>
- <span data-ttu-id="0df6d-115">**nx_sntp_client_request_unicast_time**: *ユニキャスト要求を直接 NTP サーバーに送信します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-115">**nx_sntp_client_request_unicast_time**: *Send a unicast request directly to the NTP Server*</span></span>
- <span data-ttu-id="0df6d-116">**nx_sntp_client_run_broadcast**: *クライアントをブロードキャスト モードで実行します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-116">**nx_sntp_client_run_broadcast**: *Run the Client in broadcast mode*</span></span>
- <span data-ttu-id="0df6d-117">**nx_sntp_client_run_unicast**: *クライアントをユニキャスト モードで実行します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-117">**nx_sntp_client_run_unicast**: *Run the Client in unicast mode*</span></span>
- <span data-ttu-id="0df6d-118">**nx_sntp_client_set_local_time**: *SNTP クライアントの最初のローカル時刻を設定します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-118">**nx_sntp_client_set_local_time**: *Set SNTP Client initial local time*</span></span>
- <span data-ttu-id="0df6d-119">**nx_sntp_client_set_time_update_notify**: *SNTP 更新コールバックを設定します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-119">**nx_sntp_client_set_time_update_notify**: *Set the SNTP update callback*</span></span>
- <span data-ttu-id="0df6d-120">**nx_sntp_client_stop**: *SNTP クライアント スレッドを停止します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-120">**nx_sntp_client_stop**: *Stop the SNTP Client thread*</span></span>
- <span data-ttu-id="0df6d-121">**nx_sntp_client_utility_display_date_and_time**: *NTP 時刻を秒単位で表示します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-121">**nx_sntp_client_utility_display_date_and_time**: *Display NTP time in seconds*</span></span>
- <span data-ttu-id="0df6d-122">**nx_sntp_client_utility_msecs_to_fraction**: *ミリ秒を NPT 時刻の小数部に変換します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-122">**nx_sntp_client_utility_msecs_to_fraction**: *Convert milliseconds to an NTP fraction component*</span></span>
- <span data-ttu-id="0df6d-123">**nx_sntp_client_utility_usecs_to_fraction**: *マイクロ秒を NTP 時刻の小数部に変換します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-123">**nx_sntp_client_utility_usecs_to_fraction**: *Convert microseconds to an NTP fraction component*</span></span>
- <span data-ttu-id="0df6d-124">**nx_sntp_client_utility_fraction_to_usecs**: *NTP 時刻の小数部をミリ秒に変換します*</span><span class="sxs-lookup"><span data-stu-id="0df6d-124">**nx_sntp_client_utility_fraction_to_usecs**: *Convert an NTP fraction component to microseconds*</span></span>


## <a name="nx_sntp_client_create"></a><span data-ttu-id="0df6d-125">nx_sntp_client_create</span><span class="sxs-lookup"><span data-stu-id="0df6d-125">nx_sntp_client_create</span></span>

<span data-ttu-id="0df6d-126">SNTP クライアントを作成します</span><span class="sxs-lookup"><span data-stu-id="0df6d-126">Create an SNTP Client</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-127">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-127">Prototype</span></span>

```C
UINT nx_sntp_client_create(NX_SNTP_CLIENT *client_ptr, NX_IP *ip_ptr,  
                                     UINT iface_index, 
                                     NX_PACKET_POOL *packet_pool_ptr, 
UINT (*leap_second_handler)(NX_SNTP_CLIENT *client_ptr, 
                                        UINT indicator), 
UINT (*kiss_of_death_handler)(NX_SNTP_CLIENT *client_ptr, 
                               NX_SNTP_TIME_MESSAGE *server_time_msg),
VOID (random_number_generator)(struct NX_SNTP_CLIENT_STRUCT 
                                *client_ptr, ULONG *rand));

```

### <a name="description"></a><span data-ttu-id="0df6d-128">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-128">Description</span></span>

<span data-ttu-id="0df6d-129">このサービスでは、SNTP クライアント インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-129">This service creates an SNTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-130">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-130">Input Parameters</span></span>

- <span data-ttu-id="0df6d-131">**client_ptr** SNTP クライアント制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-131">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="0df6d-132">**ip_ptr** クライアントの IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-132">**ip_ptr** Pointer to Client IP instance</span></span>

- <span data-ttu-id="0df6d-133">**iface_index** SNTP ネットワーク インターフェイスのインデックス</span><span class="sxs-lookup"><span data-stu-id="0df6d-133">**iface_index** Index to SNTP network interface</span></span>

- <span data-ttu-id="0df6d-134">**packet_pool_ptr** クライアントのパケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-134">**packet_pool_ptr** Pointer to Client packet pool</span></span>

- <span data-ttu-id="0df6d-135">**leap_second_handler** アプリケーションで間近な閏秒に対応するためのコールバック</span><span class="sxs-lookup"><span data-stu-id="0df6d-135">**leap_second_handler** Callback for application response to impending leap second</span></span>

- <span data-ttu-id="0df6d-136">**kiss_of_death_handler** アプリケーションで受信した Kiss of Death パケットに対応するためのコールバック</span><span class="sxs-lookup"><span data-stu-id="0df6d-136">**kiss_of_death_handler** Callback for application response to receiving Kiss of Death packet</span></span>

- <span data-ttu-id="0df6d-137">**random_number_generator** 乱数生成サービスのコールバック</span><span class="sxs-lookup"><span data-stu-id="0df6d-137">**random_number_generator** Callback to random number generator service</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-138">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-138">Return Values</span></span>

- <span data-ttu-id="0df6d-139">**NX_SUCCESS** (0x00) クライアントの作成に成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-139">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="0df6d-140">**NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0xD2A) ポインターではない無効な値の入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-140">**NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0xD2A) Invalid non pointer input</span></span>

- <span data-ttu-id="0df6d-141">NX_PTR_ERROR (0x07) 無効なポインターの入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-141">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="0df6d-142">NX_INVALID_INTERFACE (0x4C) 無効なネットワーク インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0df6d-142">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df6d-143">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-143">Allowed From</span></span>

<span data-ttu-id="0df6d-144">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="0df6d-144">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-145">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-145">Example</span></span>

```C
/* Create the SNTP Client on the primary interface. */
UINT iface_index = 0;
status =  nx_sntp_client_create(&demo_client, 
                     iface_index, &client_ip, 
&client_packet_pool, leap_second_handler, 
                    kiss_of_death_handler, 
NULL /* no random_number_generator callback */);

/* If status is NX_SUCCESS an SNTP Client instance was successfully
   created.  */

```

## <a name="nx_sntp_client_delete"></a><span data-ttu-id="0df6d-146">nx_sntp_client_delete</span><span class="sxs-lookup"><span data-stu-id="0df6d-146">nx_sntp_client_delete</span></span>

<span data-ttu-id="0df6d-147">SNTP クライアントを削除します</span><span class="sxs-lookup"><span data-stu-id="0df6d-147">Delete an SNTP Client</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-148">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-148">Prototype</span></span>

```C
UINT nx_sntp_client_delete(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="0df6d-149">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-149">Description</span></span>

<span data-ttu-id="0df6d-150">このサービスでは、SNTP クライアント インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-150">This service deletes an SNTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-151">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-151">Input Parameters</span></span>

- <span data-ttu-id="0df6d-152">**client_ptr** SNTP クライアント制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-152">**client_ptr** Pointer to SNTP Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-153">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-153">Return Values</span></span>

- <span data-ttu-id="0df6d-154">**NX_SUCCESS** (0x00) クライアントの作成に成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-154">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="0df6d-155">NX_PTR_ERROR (0x07) 無効なポインターの入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-155">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="0df6d-156">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効</span><span class="sxs-lookup"><span data-stu-id="0df6d-156">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df6d-157">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-157">Allowed From</span></span>

<span data-ttu-id="0df6d-158">Threads</span><span class="sxs-lookup"><span data-stu-id="0df6d-158">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-159">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-159">Example</span></span>

```C
/* Delete the SNTP Client. */
status =  nx_sntp_client_delete(&demo_client);

/* If status is NX_SUCCESS an SNTP Client 
   instance was successfully deleted.  */

```

## <a name="nx_sntp_client_get_local_time"></a><span data-ttu-id="0df6d-160">nx_sntp_client_get_local_time</span><span class="sxs-lookup"><span data-stu-id="0df6d-160">nx_sntp_client_get_local_time</span></span>

<span data-ttu-id="0df6d-161">SNTP クライアントのローカル時刻を取得します</span><span class="sxs-lookup"><span data-stu-id="0df6d-161">Get the SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-162">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-162">Prototype</span></span>

```C
UINT nx_sntp_client_get_local_time(NX_SNTP_CLIENT *client_ptr , 
                                                ULONG *seconds, 
                                                ULONG *fraction, 
                                                CHAR *buffer);

```

### <a name="description"></a><span data-ttu-id="0df6d-163">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-163">Description</span></span>

<span data-ttu-id="0df6d-164">このサービスでは、文字列メッセージ形式でデータを受信するためのオプション バッファーへのポインターの入力により、SNTP クライアントのローカル時刻を取得します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-164">This service gets the SNTP Client local time with an option buffer pointer input to receive the data in string message format.</span></span>

<span data-ttu-id="0df6d-165">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="0df6d-165">This service is deprecated.</span></span> <span data-ttu-id="0df6d-166">開発者は *nx_sntp_client_get_local_time_extended*() に移行することを推奨します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-166">Developers are encouraged to migrate to *nx_sntp_client_get_local_time_extended*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-167">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-167">Input Parameters</span></span>

- <span data-ttu-id="0df6d-168">**client_ptr** SNTP クライアント制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-168">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="0df6d-169">**seconds** ローカル時刻の秒へのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-169">**seconds** Pointer to local time seconds</span></span>

- <span data-ttu-id="0df6d-170">**fraction** ローカル時刻の小数部</span><span class="sxs-lookup"><span data-stu-id="0df6d-170">**fraction** Local time fraction component</span></span>

- <span data-ttu-id="0df6d-171">**buffer** 時刻データを書き込むバッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-171">**buffer** Pointer to buffer to write time data</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-172">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-172">Return Values</span></span>

- <span data-ttu-id="0df6d-173">**NX_SUCCESS** (0x00) クライアントの作成に成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-173">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="0df6d-174">NX_PTR_ERROR (0x07) 無効なポインターの入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-174">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="0df6d-175">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効</span><span class="sxs-lookup"><span data-stu-id="0df6d-175">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df6d-176">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-176">Allowed From</span></span>

<span data-ttu-id="0df6d-177">Threads</span><span class="sxs-lookup"><span data-stu-id="0df6d-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-178">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-178">Example</span></span>

```C
/* Get the SNTP Client local time without the 
   string message option. */

ULONG base_seconds;
ULONG base_fraction;

status =  nx_sntp_client_get_local_time(&demo_client, 
                                       &base_seconds, 
                                       &base_fraction, 
                                       NX_NULL);
/* If status is NX_SUCCESS an SNTP Client time was successfully
   retrieved.  */

```

## <a name="nx_sntp_client_get_local_time_extended"></a><span data-ttu-id="0df6d-179">nx_sntp_client_get_local_time_extended</span><span class="sxs-lookup"><span data-stu-id="0df6d-179">nx_sntp_client_get_local_time_extended</span></span>

<span data-ttu-id="0df6d-180">SNTP クライアントの拡張ローカル時刻を取得します</span><span class="sxs-lookup"><span data-stu-id="0df6d-180">Get the extended SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-181">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-181">Prototype</span></span>

```C
UINT nx_sntp_client_get_local_time_extended(
                 NX_SNTP_CLIENT *client_ptr,
                 ULONG *seconds, 
                 ULONG *fraction, 
                 CHAR *buffer
                 UINT buffer_size);

```

### <a name="description"></a><span data-ttu-id="0df6d-182">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-182">Description</span></span>

<span data-ttu-id="0df6d-183">このサービスでは、文字列メッセージ形式でデータを受信するためのオプション バッファー ポインターの入力により、SNTP クライアントの拡張ローカル時刻を取得します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-183">This service gets the extended SNTP Client local time with an option buffer pointer input to receive the data in string message format.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-184">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-184">Input Parameters</span></span>

- <span data-ttu-id="0df6d-185">**client_ptr** SNTP クライアント制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-185">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="0df6d-186">**seconds** ローカル時刻の秒へのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-186">**seconds** Pointer to local time seconds</span></span>

- <span data-ttu-id="0df6d-187">**fraction** 小数部へのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-187">**fraction** Pointer to fraction component</span></span>

- <span data-ttu-id="0df6d-188">**buffer** 時刻データを書き込むバッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-188">**buffer** Pointer to buffer to write time data</span></span>

- <span data-ttu-id="0df6d-189">**buffer_size** バッファーの長さ</span><span class="sxs-lookup"><span data-stu-id="0df6d-189">**buffer_size** Length of buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-190">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-190">Return Values</span></span>

- <span data-ttu-id="0df6d-191">**NX_SUCCESS** (0x00) クライアントの作成に成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-191">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="0df6d-192">NX_PTR_ERROR (0x07) 無効なポインターの入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-192">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="0df6d-193">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効</span><span class="sxs-lookup"><span data-stu-id="0df6d-193">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

- <span data-ttu-id="0df6d-194">NX_SIZE_ERROR (0x09) バッファーのサイズの確認に失敗</span><span class="sxs-lookup"><span data-stu-id="0df6d-194">NX_SIZE_ERROR (0x09) Check buffer_size fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df6d-195">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-195">Allowed From</span></span>

<span data-ttu-id="0df6d-196">Threads</span><span class="sxs-lookup"><span data-stu-id="0df6d-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-197">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-197">Example</span></span>

```C
/* Get the SNTP Client local time without the 
   string message option. */

#define BUFSIZE 50

ULONG seconds;
ULONG fraction;
CHAR  buffer[BUFSIZE];

status =  nx_sntp_client_get_local_time_extended(&demo_client, 
                                                &seconds, 
                                                &fraction, 
                                                buffer, 
                                                BUFSIZE);

/* If status is NX_SUCCESS an SNTP Client 
   time was successfully retrieved.  */

```

## <a name="nx_sntp_client_initialize_broadcast"></a><span data-ttu-id="0df6d-198">nx_sntp_client_initialize_broadcast</span><span class="sxs-lookup"><span data-stu-id="0df6d-198">nx_sntp_client_initialize_broadcast</span></span>

<span data-ttu-id="0df6d-199">ブロードキャスト使用のためにクライアントを初期化します</span><span class="sxs-lookup"><span data-stu-id="0df6d-199">Initialize the Client for broadcast operation</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-200">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-200">Prototype</span></span>

```C
UINT nx_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                                    ULONG multicast_server_address, 
                                    ULONG broadcast_time_servers);


```

### <a name="description"></a><span data-ttu-id="0df6d-201">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-201">Description</span></span>

<span data-ttu-id="0df6d-202">このサービスでは、SNTP サーバーの IP アドレスを設定し、SNTP 起動パラメーターとタイムアウト時間を初期化することによって、ブロードキャスト使用のためにクライアントを初期化します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-202">This service initializes the Client for broadcast operation by setting the the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="0df6d-203">マルチキャスト アドレスとブロードキャスト アドレスがどちらも NULL でない場合は、マルチキャスト アドレスが選択されます。</span><span class="sxs-lookup"><span data-stu-id="0df6d-203">If both multicast and broadcast addresses are non-null, the multicast address is selected.</span></span> <span data-ttu-id="0df6d-204">どちらのアドレスも NULL である場合はエラーが返ります。</span><span class="sxs-lookup"><span data-stu-id="0df6d-204">If both addresses are null an error is returned.</span></span> <span data-ttu-id="0df6d-205">このサービスは IPv4 のサーバー アドレスのみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0df6d-205">Note this supports IPv4 server addresses only.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-206">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-206">Input Parameters</span></span>

- <span data-ttu-id="0df6d-207">**client_ptr** SNTP クライアント制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-207">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="0df6d-208">**multicast_server_address** SNTP マルチキャスト アドレス</span><span class="sxs-lookup"><span data-stu-id="0df6d-208">**multicast_server_address** SNTP multicast address</span></span>

- <span data-ttu-id="0df6d-209">**broadcast_time_server** SNTP サーバーのブロードキャスト アドレス</span><span class="sxs-lookup"><span data-stu-id="0df6d-209">**broadcast_time_server** SNTP server broadcast address</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-210">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-210">Return Values</span></span>

- <span data-ttu-id="0df6d-211">**NX_SUCCESS** (0x00) クライアントの作成に成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-211">**NX_SUCCESS** (0x00) Successful Client Creation</span></span>

- <span data-ttu-id="0df6d-212">**NX_INVALID_PARAMETERS** (0x4D) ポインターではない無効な値の入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-212">**NX_INVALID_PARAMETERS** (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="0df6d-213">NX_PTR_ERROR (0x07) 無効なポインターの入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-213">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="0df6d-214">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効</span><span class="sxs-lookup"><span data-stu-id="0df6d-214">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df6d-215">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-215">Allowed From</span></span>

<span data-ttu-id="0df6d-216">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="0df6d-216">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-217">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-217">Example</span></span>

```C
/* Initialize the client for broadcast operation.  */
status =  nx_sntp_client_initialize_broadcast(client_ptr,0x0,
                            NX_NULL, IP_ADDRESS(192,2,2,255);

/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nxd_sntp_client_initialize_broadcast"></a><span data-ttu-id="0df6d-218">nxd_sntp_client_initialize_broadcast</span><span class="sxs-lookup"><span data-stu-id="0df6d-218">nxd_sntp_client_initialize_broadcast</span></span>

<span data-ttu-id="0df6d-219">IPv4 または IPv6 ブロードキャスト使用のためにクライアントを初期化します</span><span class="sxs-lookup"><span data-stu-id="0df6d-219">Initialize the Client for IPv4 or IPv6 broadcast operation</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-220">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-220">Prototype</span></span>

```C
UINT nxd_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                            NXD_ADDRESS *multicast_server_address, 
                            NXD_ADDRESS *broadcast_server_address);

```

### <a name="description"></a><span data-ttu-id="0df6d-221">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-221">Description</span></span>

<span data-ttu-id="0df6d-222">このサービスでは、SNTP サーバーの IP アドレスを設定し、SNTP 起動パラメーターとタイムアウト時間を初期化することによって、ブロードキャスト使用のためにクライアントを初期化します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-222">This service initializes the Client for broadcast operation by setting up the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="0df6d-223">ブロードキャスト アドレスとマルチキャスト アドレスへのポインターがどちらも NULL でない場合は、マルチキャストアドレスが選択されます。</span><span class="sxs-lookup"><span data-stu-id="0df6d-223">If both broadcast and multicast address pointers are non null, the multicast address is selected.</span></span> <span data-ttu-id="0df6d-224">どちらのアドレスへのポインターも NULL である場合はエラーが返ります。</span><span class="sxs-lookup"><span data-stu-id="0df6d-224">If both address pointers are null, an error is returned.</span></span> <span data-ttu-id="0df6d-225">このサービスは IPv4 と IPv6 アドレスを両方サポートしています。</span><span class="sxs-lookup"><span data-stu-id="0df6d-225">This supports both IPv4 and IPv6 address types.</span></span> <span data-ttu-id="0df6d-226">IPv6 はブロードキャストをサポートしていないため、ブロードキャスト アドレスへのポインターを IPv6 に設定するとエラーが返ります。</span><span class="sxs-lookup"><span data-stu-id="0df6d-226">Note that IPv6 does not support broadcast, so the broadcast address pointer is set to IPv6, an error is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-227">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-227">Input Parameters</span></span>

- <span data-ttu-id="0df6d-228">**client_ptr** SNTP クライアント制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-228">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="0df6d-229">**multicast_server_address** SNTP サーバーのマルチキャスト アドレス</span><span class="sxs-lookup"><span data-stu-id="0df6d-229">**multicast_server_address** SNTP server multicast address</span></span>

- <span data-ttu-id="0df6d-230">**broadcast_server_address** SNTP サーバーのブロードキャスト アドレス</span><span class="sxs-lookup"><span data-stu-id="0df6d-230">**broadcast_server_address** SNTP server broadcast address</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-231">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-231">Return Values</span></span>

- <span data-ttu-id="0df6d-232">**NX_SUCCESS** (0x00) クライアントの初期化に成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-232">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="0df6d-233">NX_SNTP_PARAM_ERROR (0xD0D) ポインターではない無効な値の入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-233">NX_SNTP_PARAM_ERROR (0xD0D) Invalid non pointer input</span></span>

- <span data-ttu-id="0df6d-234">NX_PTR_ERROR (0x07) 無効なポインターの入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-234">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="0df6d-235">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効</span><span class="sxs-lookup"><span data-stu-id="0df6d-235">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>


### <a name="allowed-from"></a><span data-ttu-id="0df6d-236">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-236">Allowed From</span></span>

<span data-ttu-id="0df6d-237">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="0df6d-237">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-238">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-238">Example</span></span>

```C
/* Initialize the client for broadcast operation.  */
NXD_ADDRESS broadcast_server;

Broadcast_server.nxd_ip_address = NX_IP_VERSION_V6;
Broadcast_server.nxd_ip_address.v6[0] = 0x20010db1;
Broadcast_server.nxd_ip_address.v6[1] = 0x0f101;
Broadcast_server.nxd_ip_address.v6[2] = 0x0;
Broadcast_server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_broadcast(client_ptr,0x0,
                                  NX_NULL, &broadcast_server)


/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nx_sntp_client_initialize_unicast"></a><span data-ttu-id="0df6d-239">nx_sntp_client_initialize_unicast</span><span class="sxs-lookup"><span data-stu-id="0df6d-239">nx_sntp_client_initialize_unicast</span></span>

<span data-ttu-id="0df6d-240">SNTP クライアントをユニキャストで実行するように設定します</span><span class="sxs-lookup"><span data-stu-id="0df6d-240">Set up the SNTP Client to run in unicast</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-241">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-241">Prototype</span></span>

```C
UINT nx_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                        ULONG unicast_time_server);

```
### <a name="description"></a><span data-ttu-id="0df6d-242">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-242">Description</span></span>

<span data-ttu-id="0df6d-243">このサービスでは、SNTP サーバーの IP アドレスを設定し、SNTP の起動パラメーターとタイムアウト時間を初期化することによって、ユニキャスト使用のためにクライアントを初期化します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-243">This service initializes the Client for unicast operation by setting the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="0df6d-244">このサービスは IPv4 のサーバー アドレスのみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0df6d-244">Note this supports IPv4 server addresses only.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-245">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-245">Input Parameters</span></span>

- <span data-ttu-id="0df6d-246">**client_ptr** SNTP クライアント制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-246">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="0df6d-247">**unicast_time_server** SNTP サーバーの IP アドレス</span><span class="sxs-lookup"><span data-stu-id="0df6d-247">**unicast_time_server** SNTP server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-248">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-248">Return Values</span></span>

- <span data-ttu-id="0df6d-249">**NX_SUCCESS** (0x00) クライアントの初期化に成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-249">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="0df6d-250">NX_INVALID_PARAMETERS (0x4D) ポインターではない無効な値の入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-250">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="0df6d-251">NX_PTR_ERROR (0x07) 無効なポインターの入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-251">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="0df6d-252">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効</span><span class="sxs-lookup"><span data-stu-id="0df6d-252">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df6d-253">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-253">Allowed From</span></span>

<span data-ttu-id="0df6d-254">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="0df6d-254">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-255">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-255">Example</span></span>

```C
/* Initialize the Client for unicast operation.  */
status =  nx_sntp_client_initialize_unicast(&client_ptr, 
                                 IP_ADDRESS(192,2,2,1));


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```


## <a name="nxd_sntp_client_initialize_unicast"></a><span data-ttu-id="0df6d-256">nxd_sntp_client_initialize_unicast</span><span class="sxs-lookup"><span data-stu-id="0df6d-256">nxd_sntp_client_initialize_unicast</span></span>

<span data-ttu-id="0df6d-257">SNTP クライアントを IPv4 または IPv6 ユニキャストで実行するように設定します</span><span class="sxs-lookup"><span data-stu-id="0df6d-257">Set up the SNTP Client to run in IPv4 or IPv6 unicast</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-258">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-258">Prototype</span></span>

```C
UINT nxd_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                  NXD_ADDRESS *unicast_time_server);

```

### <a name="description"></a><span data-ttu-id="0df6d-259">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-259">Description</span></span>

<span data-ttu-id="0df6d-260">このサービスでは、SNTP サーバーの IP アドレスを設定し、SNTP の起動パラメーターとタイムアウト時間を初期化することによって、ユニキャスト使用のためにクライアントを初期化します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-260">This service initializes the Client for unicast operation by setting up the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="0df6d-261">このサービスは IPv4 と IPv6 アドレスを両方サポートしています。</span><span class="sxs-lookup"><span data-stu-id="0df6d-261">This supports both IPv4 and IPv6 address types.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-262">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-262">Input Parameters</span></span>

- <span data-ttu-id="0df6d-263">**client_ptr** SNTP クライアント制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-263">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="0df6d-264">**unicast_time_server** SNTP サーバーの IP アドレス</span><span class="sxs-lookup"><span data-stu-id="0df6d-264">**unicast_time_server** SNTP server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-265">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-265">Return Values</span></span>

- <span data-ttu-id="0df6d-266">**NX_SUCCESS** (0x00) クライアントの初期化に成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-266">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="0df6d-267">NX_INVALID_PARAMETERS (0x4D) ポインターではない無効な値の入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-267">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="0df6d-268">NX_PTR_ERROR (0x07) 無効なポインターの入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-268">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="0df6d-269">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効</span><span class="sxs-lookup"><span data-stu-id="0df6d-269">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df6d-270">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-270">Allowed From</span></span>

<span data-ttu-id="0df6d-271">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="0df6d-271">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-272">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-272">Example</span></span>

```C
/* Initialize the Client for unicast operation.  */
NXD_ADDRESS unicast_server;

unicast _server.nxd_ip_address = NX_IP_VERSION_V6;
unicast _server.nxd_ip_address.v6[0] = 0x20010db1;
unicast _server.nxd_ip_address.v6[1] = 0x0f101;
unicast _server.nxd_ip_address.v6[2] = 0x0;
unicast _server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_unicast(&client_ptr, 
                                        *unicast_server); 


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```

## <a name="nx_sntp_client_receiving_updates"></a><span data-ttu-id="0df6d-273">nx_sntp_client_receiving_updates</span><span class="sxs-lookup"><span data-stu-id="0df6d-273">nx_sntp_client_receiving_updates</span></span>

<span data-ttu-id="0df6d-274">クライアントで有効な更新を受信しているかどうかを示します</span><span class="sxs-lookup"><span data-stu-id="0df6d-274">Indicate if Client is receiving valid updates</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-275">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-275">Prototype</span></span>

```C
UINT nx_sntp_client_receiving_updates(NX_SNTP_CLIENT *client_ptr, 
                                           UINT *receive_status);

```

### <a name="description"></a><span data-ttu-id="0df6d-276">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-276">Description</span></span>

<span data-ttu-id="0df6d-277">このサービスでは、クライアントで有効な SNTP 更新を受信しているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-277">This service indicates if the Client is receiving valid SNTP updates.</span></span> <span data-ttu-id="0df6d-278">有効な更新がないまま上限時間が経過するか、連続する無効な更新の受信が上限数を超えた場合、false の受信状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="0df6d-278">If the maximum time lapse without a valid update or limit on consecutive invalid updates is exceeded, the receive status is returned as false.</span></span> <span data-ttu-id="0df6d-279">SNTP クライアントは引き続き稼働します。アプリケーションで、別のユニキャストまたはブロードキャスト/マルチキャスト サーバーを使用するように SNTP クライアントを再起動する必要がある場合、*nx_sntp_client_stop* サービスを使用して SNTP クライアントを停止し、いずれかの初期化サービスを用いて、別のサーバーを使用するようにクライアントを再初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0df6d-279">Note that the SNTP Client is still running and if the application wishes to restart the SNTP Client with another unicast or broadcast/multicast server it must stop the SNTP Client using the *nx_sntp_client_stop* service, reinitialize the Client using one of the initialize services with another server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-280">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-280">Input Parameters</span></span>

- <span data-ttu-id="0df6d-281">**client_ptr** SNTP クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0df6d-281">**client_ptr** Pointer to SNTP Client control block.</span></span>

- <span data-ttu-id="0df6d-282">**receive_status** クライアントが有効な更新を受信しているかどうかを示す情報へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0df6d-282">**receive_status** Pointer to indicator if Client is receiving valid updates.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-283">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-283">Return Values</span></span>

- <span data-ttu-id="0df6d-284">**NX_SUCCESS** (0x00) クライアントで状態の更新の受信に成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-284">**NX_SUCCESS** (0x00) Client successfully received update status</span></span>

- <span data-ttu-id="0df6d-285">NX_PTR_ERROR (0x07) 無効なポインターの入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-285">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df6d-286">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-286">Allowed From</span></span>

<span data-ttu-id="0df6d-287">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="0df6d-287">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-288">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-288">Example</span></span>

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_receiving_updates(client_ptr, 
                                     &receive_status);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is currently receiving valid updates.  */

```

## <a name="nx_sntp_client_request_unicast_time"></a><span data-ttu-id="0df6d-289">nx_sntp_client_request_unicast_time</span><span class="sxs-lookup"><span data-stu-id="0df6d-289">nx_sntp_client_request_unicast_time</span></span>

<span data-ttu-id="0df6d-290">NTP サーバーにユニキャスト要求を直接送信します</span><span class="sxs-lookup"><span data-stu-id="0df6d-290">Send a unicast request directly to the NTP Server</span></span>


### <a name="prototype"></a><span data-ttu-id="0df6d-291">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-291">Prototype</span></span>

```C
UINT nx_sntp_client_request_unicast_time(NX_SNTP_CLIENT *client_ptr, 
                                                  UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="0df6d-292">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-292">Description</span></span>

<span data-ttu-id="0df6d-293">アプリケーションでこのサービスを使用すると、SNTP クライアント スレッドのタスクから非同期で直接 NTP サーバーにユニキャスト要求を送信できます。</span><span class="sxs-lookup"><span data-stu-id="0df6d-293">This service allows the application to directly send a unicast request to the NTP server asynchronously from the SNTP Client thread task.</span></span> <span data-ttu-id="0df6d-294">待機オプションで応答を待つ時間の長さを指定します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-294">The wait option specifies how long to wait for a response.</span></span> <span data-ttu-id="0df6d-295">操作に成功した場合、アプリケーションで、SNTP クライアントの他のサービスを使用して最新の時刻を取得できます。</span><span class="sxs-lookup"><span data-stu-id="0df6d-295">If successful, the application can use other SNTP Client services to obtain the latest time.</span></span> <span data-ttu-id="0df6d-296">詳細は「 **SNTP 非同期ユニキャスト要求** 」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0df6d-296">See section **SNTP Asynchronous Unicast Requests** for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-297">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-297">Input Parameters</span></span>

- <span data-ttu-id="0df6d-298">**client_ptr** SNTP クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0df6d-298">**client_ptr** Pointer to SNTP Client control block.</span></span>

- <span data-ttu-id="0df6d-299">**Wait_option** NTP 応答を待つ、タイマー刻み単位の待機時間。</span><span class="sxs-lookup"><span data-stu-id="0df6d-299">**Wait_option** Wait option for NTP response in timer ticks.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-300">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-300">Return Values</span></span>

- <span data-ttu-id="0df6d-301">**NX_SUCCESS** (0x00) クライアントがユニキャスト更新の送受信に成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-301">**NX_SUCCESS** (0x00) Client successfully sends and receives unicast update</span></span>

- <span data-ttu-id="0df6d-302">**NX_SNTP_CLIENT_NOT_STARTED** (0xD0B) クライアント スレッドを開始していません</span><span class="sxs-lookup"><span data-stu-id="0df6d-302">**NX_SNTP_CLIENT_NOT_STARTED** (0xD0B) Client thread not started</span></span>

- <span data-ttu-id="0df6d-303">NX_PTR_ERROR (0x07) 無効なポインターの入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-303">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="0df6d-304">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効</span><span class="sxs-lookup"><span data-stu-id="0df6d-304">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df6d-305">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-305">Allowed From</span></span>

<span data-ttu-id="0df6d-306">Threads</span><span class="sxs-lookup"><span data-stu-id="0df6d-306">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-307">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-307">Example</span></span>

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_request_unicast_time(client_ptr, 400);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is received a valid response to the unicast request.  */

```

## <a name="nx_sntp_client_run_broadcast"></a><span data-ttu-id="0df6d-308">nx_sntp_client_run_broadcast</span><span class="sxs-lookup"><span data-stu-id="0df6d-308">nx_sntp_client_run_broadcast</span></span>

<span data-ttu-id="0df6d-309">クライアントをブロードキャスト モードで実行します</span><span class="sxs-lookup"><span data-stu-id="0df6d-309">Run the Client in broadcast mode</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-310">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-310">Prototype</span></span>

```C
UINT nx_sntp_client_run_broadcast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="0df6d-311">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-311">Description</span></span>

<span data-ttu-id="0df6d-312">このサービスでは、クライアントをブロードキャスト モードで起動します。このモードでは、クライアントは SNTP サーバーからブロードキャストを受信するのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="0df6d-312">This service starts the Client in broadcast mode where it will wait to receive broadcasts from the SNTP server.</span></span> <span data-ttu-id="0df6d-313">有効なブロードキャスト SNTP メッセージを受信すると、SNTP クライアントで更新を受け取らないまま経過した時間をカウントするタイムアウトのタイマーと、連続して受信した無効メッセージのカウントをリセットします。</span><span class="sxs-lookup"><span data-stu-id="0df6d-313">If a valid broadcast SNTP message is received, the SNTP client timeout for maximum lapse without an update and count of consecutive invalid messages received are reset.</span></span> <span data-ttu-id="0df6d-314">それらいずれかの上限を超えた場合は、SNTP クライアントにおけるサーバーの状態の設定が無効に変更されますが、クライアントは引き続き更新の受信を待ちます。</span><span class="sxs-lookup"><span data-stu-id="0df6d-314">If the either of these limits are exceeded, the SNTP Client sets the server status to invalid although it will still wait to receive updates.</span></span> <span data-ttu-id="0df6d-315">アプリケーションでは、SNTP クライアントのタスクをポーリングしてサーバーの状態を確認し、それが無効であれば、SNTP クライアントを停止し、別の SNTP ブロードキャスト アドレスを使用して再初期化できます。</span><span class="sxs-lookup"><span data-stu-id="0df6d-315">The application can poll the SNTP Client task for server status, and if invalid stop the SNTP Client and reinitialize it with another SNTP broadcast address.</span></span> <span data-ttu-id="0df6d-316">ユニキャスト SNTP サーバーに切り替えることもできます。</span><span class="sxs-lookup"><span data-stu-id="0df6d-316">It can also switch to a unicast SNTP server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-317">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-317">Input Parameters</span></span>

- <span data-ttu-id="0df6d-318">**client_ptr** SNTP クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0df6d-318">**client_ptr** Pointer to SNTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-319">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-319">Return Values</span></span>

- <span data-ttu-id="0df6d-320">**status** -------- 実際の完了ステータス</span><span class="sxs-lookup"><span data-stu-id="0df6d-320">**status** -------- Actual completion status</span></span>

- <span data-ttu-id="0df6d-321">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) クライアントが起動済み</span><span class="sxs-lookup"><span data-stu-id="0df6d-321">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Client already started</span></span>

- <span data-ttu-id="0df6d-322">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) クライアントが初期化されていません</span><span class="sxs-lookup"><span data-stu-id="0df6d-322">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Client not initialized</span></span>

- <span data-ttu-id="0df6d-323">NX_PTR_ERROR (0x07) 無効なポインターの入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-323">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="0df6d-324">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効</span><span class="sxs-lookup"><span data-stu-id="0df6d-324">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df6d-325">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-325">Allowed From</span></span>

<span data-ttu-id="0df6d-326">Threads</span><span class="sxs-lookup"><span data-stu-id="0df6d-326">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-327">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-327">Example</span></span>

```C
/* Start Client running in broadcast mode.  */
status =  nx_sntp_client_run_broadcast(client_ptr);

/* If status is NX_SUCCESS, the client is successfully started.  */

```

## <a name="nx_sntp_client_run_unicast"></a><span data-ttu-id="0df6d-328">nx_sntp_client_run_unicast</span><span class="sxs-lookup"><span data-stu-id="0df6d-328">nx_sntp_client_run_unicast</span></span>

<span data-ttu-id="0df6d-329">クライアントをユニキャスト モードで実行します</span><span class="sxs-lookup"><span data-stu-id="0df6d-329">Run the Client in unicast mode</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-330">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-330">Prototype</span></span>

```C
UINT nx_sntp_client_run_unicast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="0df6d-331">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-331">Description</span></span>

<span data-ttu-id="0df6d-332">このサービスでは、クライアントをユニキャスト モードで起動します。このモードでは、クライアントから SNTP サーバーに定期的にユニキャスト要求を送信して時刻を更新します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-332">This service starts the Client in unicast mode where it periodically sends a unicast request to its SNTP Server for a time update.</span></span> <span data-ttu-id="0df6d-333">有効な SNTP メッセージを受信すると、SNTP クライアントで更新を受け取らないまま経過した時間をカウントするタイムアウトのタイマー、最初のポーリング間隔、連続して受信した無効メッセージのカウントをリセットします。</span><span class="sxs-lookup"><span data-stu-id="0df6d-333">If a valid SNTP message is received, the SNTP client timeout for maximum lapse without an update, initial polling interval and count of consecutive invalid messages received are reset.</span></span> <span data-ttu-id="0df6d-334">それらいずれかの上限を超えた場合は、SNTP クライアントにおけるサーバーの状態の設定が無効に変更されますが、クライアントは引き続きポーリングを行い、更新の受信を待ちます。</span><span class="sxs-lookup"><span data-stu-id="0df6d-334">If the either of these limits are exceeded, the SNTP Client sets the Server status to invalid although it will still poll and wait to receive updates.</span></span> <span data-ttu-id="0df6d-335">アプリケーションでは、SNTP クライアントのタスクをポーリングしてサーバーの状態を確認し、それが無効であれば、SNTP クライアントを停止し、別の SNTP ユニキャスト アドレスを使用して再初期化できます。</span><span class="sxs-lookup"><span data-stu-id="0df6d-335">The application can poll the SNTP Client task for server status, and if invalid stop the SNTP Client and reinitialize it with another SNTP unicast address.</span></span> <span data-ttu-id="0df6d-336">ブロードキャスト SNTP サーバーに切り替えることもできます。</span><span class="sxs-lookup"><span data-stu-id="0df6d-336">It can also switch to a broadcast SNTP server.</span></span>

<span data-ttu-id="0df6d-337">.</span><span class="sxs-lookup"><span data-stu-id="0df6d-337">.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-338">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-338">Input Parameters</span></span>

- <span data-ttu-id="0df6d-339">**client_ptr** SNTP クライアント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0df6d-339">**client_ptr** Pointer to SNTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-340">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-340">Return Values</span></span>

- <span data-ttu-id="0df6d-341">**NX_SUCCESS** (0x00) クライアントをユニキャスト モードで起動することに成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-341">**NX_SUCCESS** (0x00) Successfully started Client in unicast mode</span></span>

- <span data-ttu-id="0df6d-342">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) クライアントが起動済み</span><span class="sxs-lookup"><span data-stu-id="0df6d-342">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Client already started</span></span>

- <span data-ttu-id="0df6d-343">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) クライアントが初期化されていません</span><span class="sxs-lookup"><span data-stu-id="0df6d-343">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Client not initialized</span></span>

- <span data-ttu-id="0df6d-344">NX_PTR_ERROR (0x07) 無効なポインターの入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-344">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="0df6d-345">NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効</span><span class="sxs-lookup"><span data-stu-id="0df6d-345">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>


### <a name="allowed-from"></a><span data-ttu-id="0df6d-346">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-346">Allowed From</span></span>

<span data-ttu-id="0df6d-347">Threads</span><span class="sxs-lookup"><span data-stu-id="0df6d-347">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-348">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-348">Example</span></span>

```C
/* Start the Client in unicast mode. */
status =  nx_sntp_client_run_unicast(client_ptr);

/* If status = NX_SUCCESS, the Client was successfully started.  */

```

## <a name="nx_sntp_client_set_local_time"></a><span data-ttu-id="0df6d-349">nx_sntp_client_set_local_time</span><span class="sxs-lookup"><span data-stu-id="0df6d-349">nx_sntp_client_set_local_time</span></span>

<span data-ttu-id="0df6d-350">SNTP クライアントのローカル時刻を設定します</span><span class="sxs-lookup"><span data-stu-id="0df6d-350">Set the SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-351">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-351">Prototype</span></span>

```C
UINT nx_sntp_client_set_local_time(NX_SNTP_CLIENT *client_ptr , 
                                ULONG seconds, ULONG fraction);

```

### <a name="description"></a><span data-ttu-id="0df6d-352">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-352">Description</span></span>

<span data-ttu-id="0df6d-353">このサービスでは、時刻の入力により SNTP クライアントのローカル時刻を設定します。たとえば、秒と “小数” (1 秒未満の時間を 16 進数で表現する形式) の SNTP 形式で設定します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-353">This service sets the SNTP Client local time with the input time, in SNTP format e.g. seconds and ‘fraction’ which is the format for putting fractions of a second in hexadecimal format.</span></span> <span data-ttu-id="0df6d-354">リアル タイム クロックなどの独立した時計から SNTP クライアントのローカル時刻を更新することを想定しています。</span><span class="sxs-lookup"><span data-stu-id="0df6d-354">It is intended for updating the SNTP Client local time from an independent time keeper, e.g. a real time clock.</span></span> <span data-ttu-id="0df6d-355">SNTP プロトコルでは、SNTP の時刻更新によって、ローカルの時計の時刻がずれるのを防ぐことを意図しています。</span><span class="sxs-lookup"><span data-stu-id="0df6d-355">The SNTP protocol is intended for SNTP time updates to keep local clock time from ‘drifting’.</span></span> <span data-ttu-id="0df6d-356">アプリケーションのデバイスに独立した時計がない場合は、SNTP サーバーによる時刻更新を唯一の入力として SNTP クライアントのローカル時刻を保つこともできますが、これは本来の方法とは異なります。</span><span class="sxs-lookup"><span data-stu-id="0df6d-356">SNTP server time updates can be, but are not intended to be the sole input to the SNTP Client local time if there is no independent time keeper on the application device.</span></span>

<span data-ttu-id="0df6d-357">この API を使用して、SNTP クライアント スレッドの開始前に、SNTP クライアントに基準時間を与えることもできます。</span><span class="sxs-lookup"><span data-stu-id="0df6d-357">This API can also be used to give the SNTP Client a base time before starting the SNTP Client thread.</span></span> <span data-ttu-id="0df6d-358">SNTP クライアントのローカル時刻を受信した更新と比較することで、時刻データの有効性を確保します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-358">The SNTP Client local time is compared to received updates for valid time data.</span></span> <span data-ttu-id="0df6d-359">はじめて更新を受信するときは、とても大きなずれが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="0df6d-359">For the first time update received, there might be a very large discrepancy.</span></span> <span data-ttu-id="0df6d-360">そのため、最初の更新におけるずれを SNTP クライアントで無視するオプションを用意しています。</span><span class="sxs-lookup"><span data-stu-id="0df6d-360">Therefore there is an option for the SNTP Client to ignore the discrepancy on the first update.</span></span> <span data-ttu-id="0df6d-361">そうすることで、SNTP クライアントを基準時間なしで起動できます。</span><span class="sxs-lookup"><span data-stu-id="0df6d-361">In this manner, the SNTP Client can start without a base time.</span></span> <span data-ttu-id="0df6d-362">入力する時刻は、既知のエポック時刻 (通常インターネットで利用可能) から取得でき、(新しい “エポック” が始まる 2036 年までは) 1900 年 1 月 1 日からの秒数として計算されます。</span><span class="sxs-lookup"><span data-stu-id="0df6d-362">Input time can be obtained from known epoch times (usually available on the Internet) and are computed as the number of seconds since January 1, 1900 (until 2036 when a new ‘epoch’ will be started.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-363">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-363">Input Parameters</span></span>

- <span data-ttu-id="0df6d-364">**client_ptr** SNTP クライアント制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-364">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="0df6d-365">**seconds** 入力時刻の整数秒部分</span><span class="sxs-lookup"><span data-stu-id="0df6d-365">**seconds** Seconds component of the time input</span></span>

- <span data-ttu-id="0df6d-366">**fraction** 1 秒未満の部分 (SNTP 時刻の小数部の形式で表現されます)</span><span class="sxs-lookup"><span data-stu-id="0df6d-366">**fraction** Subseconds component in the SNTP fraction format</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-367">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-367">Return Values</span></span>

- <span data-ttu-id="0df6d-368">**NX_SUCCESS** (0x00) ローカル時刻の設定に成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-368">**NX_SUCCESS** (0x00) Successfully set local time</span></span>

- <span data-ttu-id="0df6d-369">NX_PTR_ERROR (0x07) 無効なポインターの入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-369">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df6d-370">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-370">Allowed From</span></span>

<span data-ttu-id="0df6d-371">初期化</span><span class="sxs-lookup"><span data-stu-id="0df6d-371">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-372">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-372">Example</span></span>

```C
/* Set the SNTP Client local time. */
base_seconds =  0xd2c50b71;
base_fraction = 0xa132db1e;

status =  nx_sntp_client_set_local_time(&demo_client, 
                                        base_seconds, 
                                        base_fraction);

/* If status is NX_SUCCESS an SNTP Client time 
   was successfully set.  */

```

## <a name="nx_sntp_client_set_time_update_notify"></a><span data-ttu-id="0df6d-373">nx_sntp_client_set_time_update_notify</span><span class="sxs-lookup"><span data-stu-id="0df6d-373">nx_sntp_client_set_time_update_notify</span></span>

<span data-ttu-id="0df6d-374">SNTP 更新コールバックを設定します</span><span class="sxs-lookup"><span data-stu-id="0df6d-374">Set the SNTP update callback</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-375">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-375">Prototype</span></span>

```C
UINT nx_sntp_client_set_time_update_notify(NX_SNTP_CLIENT *client_ptr, 
                           VOID (time_update_cb)(NX_SNTP_TIME_MESSAGE 
                        *time_update_ptr, NX_SNTP_TIME *local_time)));

```

### <a name="description"></a><span data-ttu-id="0df6d-376">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-376">Description</span></span>

<span data-ttu-id="0df6d-377">このサービスでは、SNTP クライアントが有効な時刻の更新を受信したときにアプリケーションに通知を行うコールバックを設定します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-377">This service sets callback to notify the application when the SNTP Client receives a valid time update.</span></span> <span data-ttu-id="0df6d-378">SNTP メッセージのローカル時刻と SNTP クライアントのローカル時刻 (通常は同じ) を NTP 形式で通知します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-378">It supplies the actual SNTP message and the SNTP Client’s local time (usually the same) in NTP format.</span></span> <span data-ttu-id="0df6d-379">アプリケーションでは、NTP データを直接使用することも、*nx_sntp_client_utility_display_date_time サービス* を呼び出して人間が判読できる形式に時刻を変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="0df6d-379">The application can use the NTP data directly or call the *nx_sntp_client_utility_display_date_time service* to convert the time to human readable format.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-380">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-380">Input Parameters</span></span>

- <span data-ttu-id="0df6d-381">**client_ptr** SNTP クライアント制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-381">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="0df6d-382">**time_update_cb** コールバック関数へのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-382">**time_update_cb** Pointer to callback function</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-383">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-383">Return Values</span></span>

- <span data-ttu-id="0df6d-384">**NX_SUCCESS** (0x00) コールバックの設定に成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-384">**NX_SUCCESS** (0x00) Successfully set callback</span></span>

- <span data-ttu-id="0df6d-385">NX_PTR_ERROR (0x07) 無効なポインターの入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-385">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df6d-386">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-386">Allowed From</span></span>

<span data-ttu-id="0df6d-387">初期化</span><span class="sxs-lookup"><span data-stu-id="0df6d-387">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-388">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-388">Example</span></span>

```C
/* Set the SNTP Client time update callback. */
VOID client_time_update_notify(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                           NX_SNTP_TIME *local time);

NX_SNTP_CLIENT demo_client;


status = nx_sntp_client_set_time_update_notify(&demo_client, 
                                            time_update_cb);

/* If status is NX_SUCCESS an SNTP Client 
   time update callback was successfully set.  */

```

## <a name="nx_sntp_client_stop"></a><span data-ttu-id="0df6d-389">nx_sntp_client_stop</span><span class="sxs-lookup"><span data-stu-id="0df6d-389">nx_sntp_client_stop</span></span>

<span data-ttu-id="0df6d-390">SNTP クライアント スレッドを停止します</span><span class="sxs-lookup"><span data-stu-id="0df6d-390">Stop the SNTP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-391">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-391">Prototype</span></span>

```C
UINT nx_sntp_client_stop(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="0df6d-392">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-392">Description</span></span>

<span data-ttu-id="0df6d-393">このサービスでは、SNTP クライアント スレッドを停止します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-393">This service stops the SNTP Client thread.</span></span> <span data-ttu-id="0df6d-394">SNTP クライアント スレッドのタスク (無限ループで実行されます) ですべての反復処理を一時停止して SNTP クライアントの状態を制御することをやめさせ、アプリケーションが SNTP クライアントで API 呼び出しを実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="0df6d-394">The SNTP Client thread tasks, which runs in an infinite loop, pauses on every iteration to release control of the SNTP Client state and allow applications to make API calls on the SNTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-395">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-395">Input Parameters</span></span>

- <span data-ttu-id="0df6d-396">**client_ptr** SNTP クライアント制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-396">**client_ptr** Pointer to SNTP Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-397">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-397">Return Values</span></span>

- <span data-ttu-id="0df6d-398">**NX_SUCCESS** (0x00) クライアント スレッドの停止に成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-398">**NX_SUCCESS** (0x00) Successful stopped Client thread</span></span>

- <span data-ttu-id="0df6d-399">**NX_SNTP_CLIENT_NOT_STARTED** (0xDB) SNTP クライアント スレッドを開始していません</span><span class="sxs-lookup"><span data-stu-id="0df6d-399">**NX_SNTP_CLIENT_NOT_STARTED** (0xDB) SNTP Client thread not started</span></span>

- <span data-ttu-id="0df6d-400">NX_PTR_ERROR (0x07) 無効なポインターの入力</span><span class="sxs-lookup"><span data-stu-id="0df6d-400">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df6d-401">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-401">Allowed From</span></span>

<span data-ttu-id="0df6d-402">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="0df6d-402">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-403">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-403">Example</span></span>

```C
/* Stop the SNTP Client. */
status =  nx_sntp_client_stop(&demo_client);

/* If status is NX_SUCCESS an SNTP 
   Client instance was successfully stopped.  */

```

## <a name="nx_sntp_client_utility_display_date_time"></a><span data-ttu-id="0df6d-404">nx_sntp_client_utility_display_date_time</span><span class="sxs-lookup"><span data-stu-id="0df6d-404">nx_sntp_client_utility_display_date_time</span></span>

<span data-ttu-id="0df6d-405">NTP 時刻を日付と時刻の文字列に変換します</span><span class="sxs-lookup"><span data-stu-id="0df6d-405">Convert an NTP Time to Date and Time string</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-406">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-406">Prototype</span></span>

```C
UINT nx_sntp_client_utility_display_date_time (NX_SNTP_CLIENT 
                      *client_ptr, CHAR *buffer, UINT length);

```

### <a name="description"></a><span data-ttu-id="0df6d-407">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-407">Description</span></span>

<span data-ttu-id="0df6d-408">このサービスでは、SNTP クライアントのローカル時刻を年月日形式に変換し、その日付を指定されたバッファーに返します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-408">This service converts the SNTP Client local time to a year month date format and returns the date in the supplied buffer.</span></span> <span data-ttu-id="0df6d-409">NX_SNTP_CURRENT_YEAR は、クライアントの現在時刻と同じ年である必要はありませんが、指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0df6d-409">The NX_SNTP_CURRENT_YEAR need not be the same year as the current Client time but it must be defined.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-410">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-410">Input Parameters</span></span>

- <span data-ttu-id="0df6d-411">**client_ptr SNTP クライアントへのポインター**</span><span class="sxs-lookup"><span data-stu-id="0df6d-411">**client_ptr Pointer to SNTP Client**</span></span>

- <span data-ttu-id="0df6d-412">**buffer** 日付を保存するバッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-412">**buffer** Pointer to buffer to store date</span></span>

- <span data-ttu-id="0df6d-413">**length** 入力バッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="0df6d-413">**length** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-414">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-414">Return Values</span></span>

- <span data-ttu-id="0df6d-415">**NX_SUCCESS** (0x00) 変換に成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-415">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="0df6d-416">**NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08) NX_SNTP_CURRENT_YEAR を指定していないか、クライアントのローカル時刻を設定できていません</span><span class="sxs-lookup"><span data-stu-id="0df6d-416">**NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08) NX_SNTP_CURRENT_YEAR not defined or no local client time established</span></span>

- <span data-ttu-id="0df6d-417">**NX_SNTP_INVALID_DATETIME_BUFFER** (0xD07) バッファーの長さが不足</span><span class="sxs-lookup"><span data-stu-id="0df6d-417">**NX_SNTP_INVALID_DATETIME_BUFFER** (0xD07) Insufficient buffer length</span></span>


### <a name="allowed-from"></a><span data-ttu-id="0df6d-418">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-418">Allowed From</span></span>

<span data-ttu-id="0df6d-419">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="0df6d-419">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-420">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-420">Example</span></span>

```C
/* Convert and display the Client’s local time. */

status =  nx_sntp_client_utility_display_date_time(client_ptr , 
                                        buffer, sizeof(buffer));

/* If status is NX_SUCCESS, 
   date was successfully written to buffer.  */

```

## <a name="nx_sntp_client_utility_msecs_to_fraction"></a><span data-ttu-id="0df6d-421">nx_sntp_client_utility_msecs_to_fraction</span><span class="sxs-lookup"><span data-stu-id="0df6d-421">nx_sntp_client_utility_msecs_to_fraction</span></span>

<span data-ttu-id="0df6d-422">ミリ秒を NTP 時刻の小数部に変換します</span><span class="sxs-lookup"><span data-stu-id="0df6d-422">Convert milliseconds to an NTP fraction component</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-423">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-423">Prototype</span></span>

```C
UINT nx_sntp_client_utility_msecs_to_fraction (ULONG milliseconds,   
                                                 ULONG *fraction);

```

### <a name="description"></a><span data-ttu-id="0df6d-424">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-424">Description</span></span>

<span data-ttu-id="0df6d-425">このサービスでは、入力されるミリ秒を NTP 時刻の小数部に変換します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-425">This service converts the input milliseconds to the NTP fraction component.</span></span> <span data-ttu-id="0df6d-426">SNTP クライアント用の開始基準時刻があるものの NTP の “整数秒+小数” 形式になっていないアプリケーションでの使用を意図しています。</span><span class="sxs-lookup"><span data-stu-id="0df6d-426">It is intended for use with applications that have a starting base time for the SNTP Client but not in NTP seconds/fraction format.</span></span> <span data-ttu-id="0df6d-427">有効な小数を作成するには、ミリ秒の数字が 1000 未満である必要があります。</span><span class="sxs-lookup"><span data-stu-id="0df6d-427">The number of milliseconds must be less than 1000 to make a valid fraction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-428">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-428">Input Parameters</span></span>

- <span data-ttu-id="0df6d-429">**milliseconds 変換するミリ秒**</span><span class="sxs-lookup"><span data-stu-id="0df6d-429">**milliseconds Milliseconds to convert**</span></span>

- <span data-ttu-id="0df6d-430">**fraction** 小数に変換するミリ秒へのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-430">**fraction** Pointer to milliseconds converted to fraction</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-431">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-431">Return Values</span></span>

- <span data-ttu-id="0df6d-432">**NX_SUCCESS** (0x00) 変換に成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-432">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="0df6d-433">**NX_SNTP_OVERFLOW_ERROR** (0xD32) 時刻から日付への変換のエラー</span><span class="sxs-lookup"><span data-stu-id="0df6d-433">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Error converting time to a date</span></span>

- <span data-ttu-id="0df6d-434">NX_SNTP_INVALID_TIME (0xD30) 入力された SNTP データが無効</span><span class="sxs-lookup"><span data-stu-id="0df6d-434">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df6d-435">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-435">Allowed From</span></span>

<span data-ttu-id="0df6d-436">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="0df6d-436">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-437">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-437">Example</span></span>

```C
/* Convert the milliseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(milliseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, 
   data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_usecs_to_fraction"></a><span data-ttu-id="0df6d-438">nx_sntp_client_utility_usecs_to_fraction</span><span class="sxs-lookup"><span data-stu-id="0df6d-438">nx_sntp_client_utility_usecs_to_fraction</span></span>

<span data-ttu-id="0df6d-439">マイクロ秒を NTP 時刻の小数部に変換します</span><span class="sxs-lookup"><span data-stu-id="0df6d-439">Convert microseconds to an NTP fraction component</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-440">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-440">Prototype</span></span>

```C
UINT nx_sntp_client_utility_usecs_to_fraction (ULONG microseconds,   
                                                 ULONG *fraction);

```
### <a name="description"></a><span data-ttu-id="0df6d-441">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-441">Description</span></span>

<span data-ttu-id="0df6d-442">このサービスでは、入力されるマイクロ秒を NTP 時刻の小数部に変換します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-442">This service converts the input microseconds to the NTP fraction component.</span></span> <span data-ttu-id="0df6d-443">SNTP クライアント用の開始基準時刻があるものの NTP の “整数秒+小数” 形式になっていないアプリケーションでの使用を意図しています。</span><span class="sxs-lookup"><span data-stu-id="0df6d-443">It is intended for use with applications that have a starting base time for the SNTP Client but not in NTP seconds/fraction format.</span></span> <span data-ttu-id="0df6d-444">有効な小数を作成するには、マイクロ秒の数字が 1000000 未満である必要があります。</span><span class="sxs-lookup"><span data-stu-id="0df6d-444">The number of microseconds must be less than 1000000 to make a valid fraction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-445">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-445">Input Parameters</span></span>

- <span data-ttu-id="0df6d-446">**microseconds** 変換するマイクロ秒</span><span class="sxs-lookup"><span data-stu-id="0df6d-446">**microseconds** Microseconds to convert</span></span>

- <span data-ttu-id="0df6d-447">**fraction** 小数に変換するマイクロ秒へのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-447">**fraction** Pointer to microseconds converted to fraction</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-448">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-448">Return Values</span></span>

- <span data-ttu-id="0df6d-449">**NX_SUCCESS** (0x00) 変換に成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-449">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="0df6d-450">**NX_SNTP_OVERFLOW_ERROR** (0xD32) 時刻から日付への変換のエラー</span><span class="sxs-lookup"><span data-stu-id="0df6d-450">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Error converting time to a date</span></span>

- <span data-ttu-id="0df6d-451">NX_SNTP_INVALID_TIME (0xD30) 入力された SNTP データが無効</span><span class="sxs-lookup"><span data-stu-id="0df6d-451">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df6d-452">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-452">Allowed From</span></span>

<span data-ttu-id="0df6d-453">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="0df6d-453">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-454">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-454">Example</span></span>

```C
/* Convert the microseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(microseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_fraction_to_usecs"></a><span data-ttu-id="0df6d-455">nx_sntp_client_utility_fraction_to_usecs</span><span class="sxs-lookup"><span data-stu-id="0df6d-455">nx_sntp_client_utility_fraction_to_usecs</span></span>

<span data-ttu-id="0df6d-456">NTP 時刻の小数部をマイクロ秒に変換する</span><span class="sxs-lookup"><span data-stu-id="0df6d-456">Convert an NTP fraction component to microseconds</span></span>

### <a name="prototype"></a><span data-ttu-id="0df6d-457">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="0df6d-457">Prototype</span></span>

```C
UINT nx_sntp_client_utility_fraction_to_usecs (ULONG fraction,   
                                         ULONG *microseconds);

```

### <a name="description"></a><span data-ttu-id="0df6d-458">説明</span><span class="sxs-lookup"><span data-stu-id="0df6d-458">Description</span></span>

<span data-ttu-id="0df6d-459">このサービスでは、入力される NTP 時刻小数部をマイクロ秒に変換します。</span><span class="sxs-lookup"><span data-stu-id="0df6d-459">This service converts the input NTP fraction component to microseconds.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0df6d-460">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="0df6d-460">Input Parameters</span></span>

- <span data-ttu-id="0df6d-461">**fraction 変換する小数**</span><span class="sxs-lookup"><span data-stu-id="0df6d-461">**fraction Fraction to convert**</span></span>

- <span data-ttu-id="0df6d-462">**microseconds** マイクロ秒に変換する小数へのポインター</span><span class="sxs-lookup"><span data-stu-id="0df6d-462">**microseconds** Pointer to fraction converted to microseconds</span></span>

### <a name="return-values"></a><span data-ttu-id="0df6d-463">戻り値</span><span class="sxs-lookup"><span data-stu-id="0df6d-463">Return Values</span></span>

- <span data-ttu-id="0df6d-464">**NX_SUCCESS** (0x00) 変換に成功</span><span class="sxs-lookup"><span data-stu-id="0df6d-464">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="0df6d-465">NX_SNTP_INVALID_TIME (0xD30) 入力された SNTP データが無効</span><span class="sxs-lookup"><span data-stu-id="0df6d-465">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0df6d-466">許可元</span><span class="sxs-lookup"><span data-stu-id="0df6d-466">Allowed From</span></span>

<span data-ttu-id="0df6d-467">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="0df6d-467">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="0df6d-468">例</span><span class="sxs-lookup"><span data-stu-id="0df6d-468">Example</span></span>

```C
/* Convert the fraction to microseconds. */


status =  nx_sntp_client_utility_fraction_to_msecs(fraction, 
                                             &microseconds);

/* If status is NX_SUCCESS, data was successfully converted.  */
```