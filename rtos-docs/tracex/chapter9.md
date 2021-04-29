---
title: チャプター 9 - Azure RTOS USBX トレース イベント
description: このチャプターでは、TraceX により表示される Azure RTOS USBX イベントについて説明します。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 98561fe1d131e1d1b0893b7d89eb720881a82ac8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813166"
---
# <a name="chapter-9---azure-rtos-usbx-trace-events"></a><span data-ttu-id="26363-103">チャプター 9 - Azure RTOS USBX トレース イベント</span><span class="sxs-lookup"><span data-stu-id="26363-103">Chapter 9 - Azure RTOS USBX trace events</span></span>

<span data-ttu-id="26363-104">このチャプターでは、TraceX により表示される Azure RTOS USBX イベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="26363-104">This chapter contains a description of the Azure RTOS USBX events displayed by TraceX.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="26363-105">イベントとアイコンのリスト</span><span class="sxs-lookup"><span data-stu-id="26363-105">List of Events and Icons</span></span>

<span data-ttu-id="26363-106">次のリストに、TraceX により表示される USBX イベントを挙げます。</span><span class="sxs-lookup"><span data-stu-id="26363-106">The following is a list of USBX events displayed by TraceX.</span></span>

| <span data-ttu-id="26363-107">アイコン</span><span class="sxs-lookup"><span data-stu-id="26363-107">Icon</span></span>                             | <span data-ttu-id="26363-108">意味</span><span class="sxs-lookup"><span data-stu-id="26363-108">Meaning</span></span>                               |
| -------------------------------- | ------------------------------------- |
| ![デバイス クラス CDC アクティブ化アイコン](./media/user-guide/usbx-events/image1.png)    | <span data-ttu-id="26363-110">**デバイス クラス CDC アクティブ化** *(ux_device_class_cdc_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-110">**Device Class Cdc Activate** *(ux_device_class_cdc_activate)*</span></span> |
| ![デバイス クラス CDC 非アクティブ化アイコン](./media/user-guide/usbx-events/image2.png)    | <span data-ttu-id="26363-112">**デバイス クラス CDC 非アクティブ化** *(ux_device_class_cdc_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-112">**Device Class Cdc Deactivate** *(ux_device_class_cdc_deactivate)*</span></span> |
| ![デバイス クラス CDC 読み取りアイコン](./media/user-guide/usbx-events/image3.png)    | <span data-ttu-id="26363-114">**デバイス クラス CDC 読み取り** *(ux_device_class_cdc_read)*</span><span class="sxs-lookup"><span data-stu-id="26363-114">**Device Class Cdc Read** *(ux_device_class_cdc_read)*</span></span> |
| ![デバイス クラス CDC 書き込みアイコン](./media/user-guide/usbx-events/image4.png)    | <span data-ttu-id="26363-116">**デバイス クラス CDC 書き込み** *(ux_device_class_cdc_write)*</span><span class="sxs-lookup"><span data-stu-id="26363-116">**Device Class Cdc Write** *(ux_device_class_cdc_write)*</span></span> |
| ![デバイス クラス DPUMP アクティブ化アイコン](./media/user-guide/usbx-events/image5.png)    | <span data-ttu-id="26363-118">**デバイス クラス DPUMP アクティブ化** *(ux_device_class_dpump_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-118">**Device Class Dpump Activate** *(ux_device_class_dpump_activate)*</span></span> |
| ![デバイス クラス DPUMP 非アクティブ化アイコン](./media/user-guide/usbx-events/image6.png)    | <span data-ttu-id="26363-120">**デバイス クラス DPUMP 非アクティブ化** *(ux_device_class_dpump_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-120">**Device Class Dpump Deactivate** *(ux_device_class_dpump_deactivate)*</span></span> |
| ![デバイス クラス DPUMP 読み取りアイコン](./media/user-guide/usbx-events/image7.png)    | <span data-ttu-id="26363-122">**デバイス クラス DPUMP 読み取り** *(ux_device_class_dpump_read)*</span><span class="sxs-lookup"><span data-stu-id="26363-122">**Device Class Dpump Read** *(ux_device_class_dpump_read)*</span></span> |
| ![デバイス クラス DPUMP 書き込みアイコン](./media/user-guide/usbx-events/image8.png)    | <span data-ttu-id="26363-124">**デバイス クラス DPUMP 書き込み** *(ux_device_class_dpump_write)*</span><span class="sxs-lookup"><span data-stu-id="26363-124">**Device Class Dpump Write** *(ux_device_class_dpump_write)*</span></span> |
| ![デバイス クラス HID アクティブ化アイコン](./media/user-guide/usbx-events/image9.png)    | <span data-ttu-id="26363-126">**デバイス クラス HID アクティブ化** *(ux_device_class_hid_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-126">**Device Class Hid Activate** *(ux_device_class_hid_activate)*</span></span> |
| ![デバイス クラス HID 非アクティブ化アイコン](./media/user-guide/usbx-events/image10.png)    | <span data-ttu-id="26363-128">**デバイス クラス HID 非アクティブ化** *(ux_device_class_hid_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-128">**Device Class Hid Deactivate** *(ux_device_class_hid_deactivate)*</span></span> |
| ![デバイス クラス HID 記述子送信アイコン](./media/user-guide/usbx-events/image11.png)    | <span data-ttu-id="26363-130">**デバイス クラス HID 記述子送信** *(ux_device_class_hid_descriptor_send)*</span><span class="sxs-lookup"><span data-stu-id="26363-130">**Device Class Hid Descriptor Send** *(ux_device_class_hid_descriptor_send)*</span></span> |
| ![デバイス クラス HID イベント取得アイコン](./media/user-guide/usbx-events/image12.png)    | <span data-ttu-id="26363-132">**デバイス クラス HID イベント取得** *(ux_device_class_hid_event_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-132">**Device Class Hid Event Get** *(ux_device_class_hid_event_get)*</span></span> |
| ![デバイス クラス HID イベント設定アイコン](./media/user-guide/usbx-events/image13.png)    | <span data-ttu-id="26363-134">**デバイス クラス HID イベント設定** *(ux_device_class_hid_event_set)*</span><span class="sxs-lookup"><span data-stu-id="26363-134">**Device Class Hid Event Set** *(ux_device_class_hid_event_set)*</span></span> |
| ![デバイス クラス HID レポート取得アイコン](./media/user-guide/usbx-events/image14.png)    | <span data-ttu-id="26363-136">**デバイス クラス HID レポート取得** *(ux_device_class_hid_report_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-136">**Device Class Hid Report Get** *(ux_device_class_hid_report_get)*</span></span> |
| ![デバイス クラス HID レポート設定アイコン](./media/user-guide/usbx-events/image15.png)    | <span data-ttu-id="26363-138">**デバイス クラス HID レポート設定** *(ux_device_class_hid_report_set)*</span><span class="sxs-lookup"><span data-stu-id="26363-138">**Device Class Hid Report Set** *(ux_device_class_hid_report_set)*</span></span> |
| ![デバイス クラス PIMA アクティブ化アイコン](./media/user-guide/usbx-events/image16.png)    | <span data-ttu-id="26363-140">**デバイス クラス PIMA アクティブ化** *(ux_device_class_pima_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-140">**Device Class Pima Activate** *(ux_device_class_pima_activate)*</span></span> |
| ![デバイス クラス PIMA 非アクティブ化アイコン](./media/user-guide/usbx-events/image17.png)    | <span data-ttu-id="26363-142">**デバイス クラス PIMA 非アクティブ化** *(ux_device_class_pima_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-142">**Device Class Pima Deactivate** *(ux_device_class_pima_deactivate)*</span></span> |
| ![デバイス クラス PIMA デバイス情報送信アイコン](./media/user-guide/usbx-events/image18.png)    | <span data-ttu-id="26363-144">**デバイス クラス PIMA デバイス情報送信** *(ux_device_class_pima_device_info_send)*</span><span class="sxs-lookup"><span data-stu-id="26363-144">**Device Class Pima Device Info Send** *(ux_device_class_pima_device_info_send)*</span></span> |
| ![デバイス クラス PIMA イベント取得アイコン](./media/user-guide/usbx-events/image19.png)    | <span data-ttu-id="26363-146">**デバイス クラス PIMA イベント取得** *(ux_device_class_pima_event_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-146">**Device Class Pima Event Get** *(ux_device_class_pima_event_get)*</span></span> |
| ![デバイス クラス PIMA イベント設定アイコン](./media/user-guide/usbx-events/image20.png)    | <span data-ttu-id="26363-148">**デバイス クラス PIMA イベント設定** *(ux_device_class_pima_event_set)*</span><span class="sxs-lookup"><span data-stu-id="26363-148">**Device Class Pima Event Set** *(ux_device_class_pima_event_set)*</span></span> |
| ![デバイス クラス PIMA オブジェクト追加アイコン](./media/user-guide/usbx-events/image21.png)    | <span data-ttu-id="26363-150">**デバイス クラス PIMA オブジェクト追加** *(ux_device_class_pima_object_add)*</span><span class="sxs-lookup"><span data-stu-id="26363-150">**Device Class Pima Object Add** *(ux_device_class_pima_object_add)*</span></span> |
| ![デバイス クラス PIMA オブジェクト データ取得アイコン](./media/user-guide/usbx-events/image22.png)    | <span data-ttu-id="26363-152">**デバイス クラス PIMA オブジェクト データ取得** *(ux_device_class_pima_object_data_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-152">**Device Class Pima Object Data Get** *(ux_device_class_pima_object_data_get)*</span></span> |
| ![デバイス クラス PIMA オブジェクト データ送信アイコン](./media/user-guide/usbx-events/image23.png)    | <span data-ttu-id="26363-154">**デバイス クラス PIMA オブジェクト データ送信** *(ux_device_class_pima_object_data_send)*</span><span class="sxs-lookup"><span data-stu-id="26363-154">**Device Class Pima Object Data Send** *(ux_device_class_pima_object_data_send)*</span></span> |
| ![デバイス クラス PIMA オブジェクト削除アイコン](./media/user-guide/usbx-events/image24.png)    | <span data-ttu-id="26363-156">**デバイス クラス PIMA オブジェクト削除** *(ux_device_class_pima_object_delete)*</span><span class="sxs-lookup"><span data-stu-id="26363-156">**Device Class Pima Object Delete** *(ux_device_class_pima_object_delete)*</span></span> |
| ![デバイス クラス PIMA オブジェクト ハンドル送信アイコン](./media/user-guide/usbx-events/image25.png)    | <span data-ttu-id="26363-158">**デバイス クラス PIMA オブジェクト ハンドル送信** *(ux_device_class_pima_object_handles_send)*</span><span class="sxs-lookup"><span data-stu-id="26363-158">**Device Class Pima Object Handles Send** *(ux_device_class_pima_object_handles_send)*</span></span> |
| ![デバイス クラス PIMA オブジェクト情報取得アイコン](./media/user-guide/usbx-events/image26.png)    | <span data-ttu-id="26363-160">**デバイス クラス PIMA オブジェクト情報取得** *(ux_device_class_pima_object_info_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-160">**Device Class Pima Object Info Get** *(ux_device_class_pima_object_info_get)*</span></span> |
| ![デバイス クラス PIMA オブジェクト情報送信アイコン](./media/user-guide/usbx-events/image27.png)    | <span data-ttu-id="26363-162">**デバイス クラス PIMA オブジェクト情報送信** *(ux_device_class_pima_object_info_send)*</span><span class="sxs-lookup"><span data-stu-id="26363-162">**Device Class Pima Object Info Send** *(ux_device_class_pima_object_info_send)*</span></span> |
| ![デバイス クラス PIMA オブジェクト数送信アイコン](./media/user-guide/usbx-events/image28.png)    | <span data-ttu-id="26363-164">**デバイス クラス PIMA オブジェクト数送信** *(ux_device_class_pima_objects_number_send)*</span><span class="sxs-lookup"><span data-stu-id="26363-164">**Device Class Pima Objects Number Send** *(ux_device_class_pima_objects_number_send)*</span></span> |
| ![デバイス クラス PIMA オブジェクト データ一部取得アイコン](./media/user-guide/usbx-events/image29.png)    | <span data-ttu-id="26363-166">**デバイス クラス PIMA オブジェクトデータ一部取得** *(ux_device_class_pima_partial_object_data_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-166">**Device Class Pima Partial Object Data Get** *(ux_device_class_pima_partial_object_data_get)*</span></span> |
| ![デバイス クラス PIMA 応答送信アイコン](./media/user-guide/usbx-events/image30.png)    | <span data-ttu-id="26363-168">**デバイス クラス PIMA 応答送信** *(ux_device_class_pima_response_send)*</span><span class="sxs-lookup"><span data-stu-id="26363-168">**Device Class Pima Response Send** *(ux_device_class_pima_response_send)*</span></span>|
| ![デバイス クラス PIMA ストレージ ID 送信アイコン](./media/user-guide/usbx-events/image31.png)    | <span data-ttu-id="26363-170">**デバイス クラス PIMA ストレージ ID 送信** *(ux_device_class_pima_storage_id_send)*</span><span class="sxs-lookup"><span data-stu-id="26363-170">**Device Class Pima Storage Id Send** *(ux_device_class_pima_storage_id_send)*</span></span> |
| ![デバイス クラス PIMA ストレージ情報送信アイコン](./media/user-guide/usbx-events/image32.png)    | <span data-ttu-id="26363-172">**デバイス クラス PIMA ストレージ情報送信** *(ux_device_class_pima_storage_info_send)*</span><span class="sxs-lookup"><span data-stu-id="26363-172">**Device Class Pima Storage Info Send** *(ux_device_class_pima_storage_info_send)*</span></span> |
| ![デバイス クラス RNDIS アクティブ化アイコン](./media/user-guide/usbx-events/image33.png)    | <span data-ttu-id="26363-174">**デバイス クラス RNDIS アクティブ化** *(ux_device_class_rndis_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-174">**Device Class Rndis Activate** *(ux_device_class_rndis_activate)*</span></span> |
| ![デバイス クラス RNDIS 非アクティブ化アイコン](./media/user-guide/usbx-events/image34.png)    | <span data-ttu-id="26363-176">**デバイス クラス RNDIS 非アクティブ化** *(ux_device_class_rndis_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-176">**Device Class Rndis Deactivate** *(ux_device_class_rndis_deactivate)*</span></span> |
| ![デバイス クラス RNDIS キープ アライブ メッセージ送信アイコン](./media/user-guide/usbx-events/image35.png)    | <span data-ttu-id="26363-178">**デバイス クラス RNDIS キープ アライブ メッセージ送信** *(ux_device_class_rndis_msg_keep_alive)*</span><span class="sxs-lookup"><span data-stu-id="26363-178">**Device Class Rndis Message Keep Alive** *(ux_device_class_rndis_msg_keep_alive)*</span></span> |
| ![デバイス クラス RNDIS クエリ メッセージ送信アイコン](./media/user-guide/usbx-events/image36.png)    | <span data-ttu-id="26363-180">**デバイス クラス RNDIS クエリ メッセージ送信** *(ux_device_class_rndis_msg_query)*</span><span class="sxs-lookup"><span data-stu-id="26363-180">**Device Class Rndis Message Query** *(ux_device_class_rndis_msg_query)*</span></span> |
| ![デバイス クラス RNDIS リセット メッセージ送信アイコン](./media/user-guide/usbx-events/image37.png)    | <span data-ttu-id="26363-182">**デバイス クラス RNDIS リセット メッセージ送信** *(ux_device_class_rndis_msg_reset)*</span><span class="sxs-lookup"><span data-stu-id="26363-182">**Device Class Rndis Message Reset** *(ux_device_class_rndis_msg_reset)*</span></span> |
| ![デバイス クラス RNDIS 設定メッセージ送信アイコン](./media/user-guide/usbx-events/image38.png)    | <span data-ttu-id="26363-184">**デバイス クラス RNDIS 設定メッセージ送信** *(ux_device_class_rndis_msg_set)*</span><span class="sxs-lookup"><span data-stu-id="26363-184">**Device Class Rndis Message Set** *(ux_device_class_rndis_msg_set)*</span></span> |
| ![デバイス クラス RNDIS パケット受信アイコン](./media/user-guide/usbx-events/image39.png)    | <span data-ttu-id="26363-186">**デバイス クラス RNDIS パケット受信** *(ux_device_class_rndis_packet_receive)*</span><span class="sxs-lookup"><span data-stu-id="26363-186">**Device Class Rndis Packet Receive** *(ux_device_class_rndis_packet_receive)*</span></span> |
| ![デバイス クラス RNDIS パケット送信アイコン](./media/user-guide/usbx-events/image40.png)    | <span data-ttu-id="26363-188">**デバイス クラス RNDIS パケット送信** *(ux_device_class_rndis_packet_transmit)*</span><span class="sxs-lookup"><span data-stu-id="26363-188">**Device Class Rndis Packet Transmit** *(ux_device_class_rndis_packet_transmit)*</span></span> |
| ![デバイス クラス Storage アクティブ化アイコン](./media/user-guide/usbx-events/image41.png)    | <span data-ttu-id="26363-190">**デバイス クラス Storage アクティブ化** *(ux_device_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-190">**Device Class Storage Activate** *(ux_device_class_storage_activate)*</span></span> |
| ![デバイス クラス Storage 非アクティブ化アイコン](./media/user-guide/usbx-events/image42.png)    | <span data-ttu-id="26363-192">**デバイス クラス Storage 非アクティブ化** *(ux_device_class_storage_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-192">**Device Class Storage Deactivate** *(ux_device_class_storage_deactivate)*</span></span> |
| ![デバイス クラス Storage フォーマット アイコン](./media/user-guide/usbx-events/image43.png)    | <span data-ttu-id="26363-194">**デバイス クラス Storage フォーマット** *(ux_device_class_storage_format)*</span><span class="sxs-lookup"><span data-stu-id="26363-194">**Device Class Storage Format** *(ux_device_class_storage_format)*</span></span> |
| ![デバイス クラス Storage 照会アイコン](./media/user-guide/usbx-events/image44.png)    | <span data-ttu-id="26363-196">**デバイス クラス Storage 照会** *(ux_device_class_storage_inquiry)*</span><span class="sxs-lookup"><span data-stu-id="26363-196">**Device Class Storage Inquiry** *(ux_device_class_storage_inquiry)*</span></span> |
| ![デバイス クラス Storage モード選択アイコン](./media/user-guide/usbx-events/image45.png)    | <span data-ttu-id="26363-198">**デバイス クラス Storage モード選択** *(ux_device_class_storage_mode_select)*</span><span class="sxs-lookup"><span data-stu-id="26363-198">**Device Class Storage Mode Select** *(ux_device_class_storage_mode_select)*</span></span> |
| ![デバイス クラス Storage モード センス アイコン](./media/user-guide/usbx-events/image46.png)    | <span data-ttu-id="26363-200">**デバイス クラス Storage モード センス** *(ux_device_class_storage_mode_sense)*</span><span class="sxs-lookup"><span data-stu-id="26363-200">**Device Class Storage Mode Sense** *(ux_device_class_storage_mode_sense)*</span></span> |
| ![デバイス クラス Storage メディア取り外し禁止/許可アイコン](./media/user-guide/usbx-events/image47.png)    | <span data-ttu-id="26363-202">**デバイス クラス Storage メディア取り外し禁止/許可** *(ux_device_class_storage_prevent_allow_media_removal)*</span><span class="sxs-lookup"><span data-stu-id="26363-202">**Device Class Storage Prevent Allow Media Removal** *(ux_device_class_storage_prevent_allow_media_removal)*</span></span> |
| ![デバイス クラス Storage 読み取りアイコン](./media/user-guide/usbx-events/image48.png)    | <span data-ttu-id="26363-204">**デバイス クラス Storage 読み取り** *(ux_device_class_storage_read)*</span><span class="sxs-lookup"><span data-stu-id="26363-204">**Device Class Storage Read** *(ux_device_class_storage_read)*</span></span> |
| ![デバイス クラス Storage 容量読み取りアイコン](./media/user-guide/usbx-events/image49.png)    | <span data-ttu-id="26363-206">**デバイス クラス Storage 容量読み取り** *(ux_device_class_storage_read_capacity)*</span><span class="sxs-lookup"><span data-stu-id="26363-206">**Device Class Storage Read Capacity** *(ux_device_class_storage_read_capacity)*</span></span> |
| ![デバイス クラス Storage フォーマット容量読み取りアイコン](./media/user-guide/usbx-events/image50.png)    | <span data-ttu-id="26363-208">**デバイス クラス Storage フォーマット容量読み取り** *(ux_device_class_storage_read_format_capacity)*</span><span class="sxs-lookup"><span data-stu-id="26363-208">**Device Class Storage Read Format Capacity** *(ux_device_class_storage_read_format_capacity)*</span></span> |
| ![デバイス クラス Storage TOC 読み取りアイコン](./media/user-guide/usbx-events/image51.png)    | <span data-ttu-id="26363-210">**デバイス クラス Storage TOC 読み取り** *(ux_device_class_storage_read_toc)*</span><span class="sxs-lookup"><span data-stu-id="26363-210">**Device Class Storage Read TOC** *(ux_device_class_storage_read_toc)*</span></span> |
| ![デバイス クラス Storage センス データ要求アイコン](./media/user-guide/usbx-events/image52.png)    | <span data-ttu-id="26363-212">**デバイス クラス Storage センス データ要求** *(ux_device_class_storage_request_sense)*</span><span class="sxs-lookup"><span data-stu-id="26363-212">**Device Class Storage Request Sense** *(ux_device_class_storage_request_sense)*</span></span> |
| ![デバイス クラス Storage 開始/停止アイコン](./media/user-guide/usbx-events/image53.png)    | <span data-ttu-id="26363-214">**デバイス クラス Storage 開始/停止** *(ux_device_class_storage_start_stop)*</span><span class="sxs-lookup"><span data-stu-id="26363-214">**Device Class Storage Start Stop** *(ux_device_class_storage_start_stop)*</span></span> |
| ![デバイス クラス Storage 準備状態テスト アイコン](./media/user-guide/usbx-events/image54.png)    | <span data-ttu-id="26363-216">**デバイス クラス Storage 準備状態テスト** *(ux_device_class_storage_test_ready)*</span><span class="sxs-lookup"><span data-stu-id="26363-216">**Device Class Storage Test Ready** *(ux_device_class_storage_test_ready)*</span></span> |
| ![デバイス クラス Storage 検証アイコン](./media/user-guide/usbx-events/image55.png)    | <span data-ttu-id="26363-218">**デバイス クラス Storage 検証** *(ux_device_class_storage_verify)*</span><span class="sxs-lookup"><span data-stu-id="26363-218">**Device Class Storage Verify** *(ux_device_class_storage_verify)*</span></span> |
| ![デバイス クラス Storage 書き込みアイコン](./media/user-guide/usbx-events/image56.png)    | <span data-ttu-id="26363-220">**デバイス クラス Storage 書き込み** *(ux_device_class_storage_write)*</span><span class="sxs-lookup"><span data-stu-id="26363-220">**Device Class Storage Write** *(ux_device_class_storage_write)*</span></span> |
| ![デバイス スタック設定選択肢取得アイコン](./media/user-guide/usbx-events/image57.png)    | <span data-ttu-id="26363-222">**デバイス スタック設定選択肢取得** *(ux_device_stack_alternate_setting_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-222">**Device Stack Alternate Setting Get** *(ux_device_stack_alternate_setting_get)*</span></span> |
| ![デバイス スタック設定選択肢設定アイコン](./media/user-guide/usbx-events/image58.png)    | <span data-ttu-id="26363-224">**デバイス スタック設定選択肢設定** *(ux_device_stack_alternate_setting_set)*</span><span class="sxs-lookup"><span data-stu-id="26363-224">**Device Stack Alternate Setting Set** *(ux_device_stack_alternate_setting_set)*</span></span> |
| ![デバイス スタック クラス登録アイコン](./media/user-guide/usbx-events/image59.png)    | <span data-ttu-id="26363-226">**デバイス スタック クラス登録** *(ux_device_stack_class_register)*</span><span class="sxs-lookup"><span data-stu-id="26363-226">**Device Stack Class Register** *(ux_device_stack_class_register)*</span></span> |
| ![デバイス スタック機能消去アイコン](./media/user-guide/usbx-events/image60.png)    | <span data-ttu-id="26363-228">**デバイス スタック機能消去** *(ux_device_stack_clear_feature)*</span><span class="sxs-lookup"><span data-stu-id="26363-228">**Device Stack Clear Feature** *(ux_device_stack_clear_feature)*</span></span> |
| ![デバイス スタック構成取得アイコン](./media/user-guide/usbx-events/image61.png)    | <span data-ttu-id="26363-230">**デバイス スタック構成取得** *(ux_device_stack_configuration_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-230">**Device Stack Configuration Get** *(ux_device_stack_configuration_get)*</span></span> |
| ![デバイス スタック構成設定アイコン](./media/user-guide/usbx-events/image62.png)    | <span data-ttu-id="26363-232">**デバイス スタック構成設定** *(ux_device_stack_configuration_set)*</span><span class="sxs-lookup"><span data-stu-id="26363-232">**Device Stack Configuration Set** *(ux_device_stack_configuration_set)*</span></span> |
| ![デバイス スタック接続アイコン](./media/user-guide/usbx-events/image63.png)    | <span data-ttu-id="26363-234">**デバイス スタック接続** *(ux_device_stack_connect)*</span><span class="sxs-lookup"><span data-stu-id="26363-234">**Device Stack Connect** *(ux_device_stack_connect)*</span></span> |
| ![デバイス スタック記述子送信アイコン](./media/user-guide/usbx-events/image64.png)    | <span data-ttu-id="26363-236">**デバイス スタック記述子送信** *(ux_device_stack_descriptor_send)*</span><span class="sxs-lookup"><span data-stu-id="26363-236">**Device Stack Descriptor Send** *(ux_device_stack_descriptor_send)*</span></span> |
| ![デバイス スタック切断アイコン](./media/user-guide/usbx-events/image65.png)    | <span data-ttu-id="26363-238">**デバイス スタック切断** *(ux_device_stack_disconnect)*</span><span class="sxs-lookup"><span data-stu-id="26363-238">**Device Stack Disconnect** *(ux_device_stack_disconnect)*</span></span> |
| ![デバイス スタック エンドポイント停止アイコン](./media/user-guide/usbx-events/image66.png)    | <span data-ttu-id="26363-240">**デバイス スタック エンドポイント停止** *(ux_device_stack_endpoint_stall)*</span><span class="sxs-lookup"><span data-stu-id="26363-240">**Device Stack Endpoint Stall** *(ux_device_stack_endpoint_stall)*</span></span> |
| ![デバイス スタック状態取得アイコン](./media/user-guide/usbx-events/image67.png)    | <span data-ttu-id="26363-242">**デバイス スタック状態取得** *(ux_device_stack_get_status)*</span><span class="sxs-lookup"><span data-stu-id="26363-242">**Device Stack Get Status** *(ux_device_stack_get_status)*</span></span> |
| ![デバイス スタック ホスト スリープ解除アイコン](./media/user-guide/usbx-events/image68.png)    | <span data-ttu-id="26363-244">**デバイス スタック ホスト スリープ解除** *(ux_device_stack_host_wakeup)*</span><span class="sxs-lookup"><span data-stu-id="26363-244">**Device Stack Host Wakeup** *(ux_device_stack_host_wakeup)*</span></span> |
| ![デバイス スタック初期化アイコン](./media/user-guide/usbx-events/image69.png)    | <span data-ttu-id="26363-246">**デバイス スタック初期化** *(ux_device_stack_initialize)*</span><span class="sxs-lookup"><span data-stu-id="26363-246">**Device Stack Initialize** *(ux_device_stack_initialize)*</span></span> |
| ![デバイス スタック インターフェイス削除アイコン](./media/user-guide/usbx-events/image70.png)    | <span data-ttu-id="26363-248">**デバイス スタック インターフェイス削除** *(ux_device_stack_interface_delete)*</span><span class="sxs-lookup"><span data-stu-id="26363-248">**Device Stack Interface Delete** *(ux_device_stack_interface_delete)*</span></span> |
| ![デバイス スタック インターフェイス取得アイコン](./media/user-guide/usbx-events/image71.png)    | <span data-ttu-id="26363-250">**デバイス スタック インターフェイス取得** *(ux_device_stack_interface_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-250">**Device Stack Interface Get** *(ux_device_stack_interface_get)*</span></span> |
| ![デバイス スタック インターフェイス設定アイコン](./media/user-guide/usbx-events/image72.png)    | <span data-ttu-id="26363-252">**デバイス スタック インターフェイス設定** *(ux_device_stack_interface_set)*</span><span class="sxs-lookup"><span data-stu-id="26363-252">**Device Stack Interface Set** *(ux_device_stack_interface_set)*</span></span> |
| ![デバイス スタック機能設定アイコン](./media/user-guide/usbx-events/image73.png)    | <span data-ttu-id="26363-254">**デバイス スタック機能設定** *(ux_device_stack_set_feature)*</span><span class="sxs-lookup"><span data-stu-id="26363-254">**Device Stack Set Feature** *(ux_device_stack_set_feature)*</span></span> |
| ![デバイス スタック転送アボート アイコン](./media/user-guide/usbx-events/image74.png)    | <span data-ttu-id="26363-256">**デバイス スタック転送アボート** *(ux_device_stack_transfer_abort)*</span><span class="sxs-lookup"><span data-stu-id="26363-256">**Device Stack Transfer Abort** *(ux_device_stack_transfer_abort)*</span></span> |
| ![\* デバイス スタック全転送要求アボート アイコン](./media/user-guide/usbx-events/image75.png)    | <span data-ttu-id="26363-258">**デバイス スタック全転送要求アボート** *(ux_device_stack_transfer_all_request_abort)*</span><span class="sxs-lookup"><span data-stu-id="26363-258">**Device Stack Transfer All Request Abort** *(ux_device_stack_transfer_all_request_abort)*</span></span> |
| ![デバイス スタック転送要求アイコン](./media/user-guide/usbx-events/image76.png)    | <span data-ttu-id="26363-260">**デバイス スタック転送要求** *(ux_device_stack_transfer_request)*</span><span class="sxs-lookup"><span data-stu-id="26363-260">**Device Stack Transfer Request** *(ux_device_stack_transfer_request)*</span></span> |
| ![ホスト クラス ASIX アクティブ化アイコン](./media/user-guide/usbx-events/image77.png)    | <span data-ttu-id="26363-262">**ホスト クラス ASIX アクティブ化** *(ux_host_class_asix_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-262">**Host Class Asix Activate** *(ux_host_class_asix_activate)*</span></span> |
| ![ホスト クラス ASIX 非アクティブ化アイコン](./media/user-guide/usbx-events/image78.png)    | <span data-ttu-id="26363-264">**ホスト クラス ASIX 非アクティブ化** *(ux_host_class_asix_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-264">**Host Class Asix Deactivate** *(ux_host_class_asix_deactivate)*</span></span> |
| ![ホスト クラス ASIX 割り込み通知アイコン](./media/user-guide/usbx-events/image79.png)    | <span data-ttu-id="26363-266">**ホスト クラス ASIX 割り込み通知** *(ux_host_class_asix_interrupt_notification)*</span><span class="sxs-lookup"><span data-stu-id="26363-266">**Host Class Asix Interrupt Notification** *(ux_host_class_asix_interrupt_notification)*</span></span> |
| ![ホスト クラス ASIX 読み取りアイコン](./media/user-guide/usbx-events/image80.png)    | <span data-ttu-id="26363-268">**ホスト クラス ASIX 読み取り** *(ux_host_class_asix_read)*</span><span class="sxs-lookup"><span data-stu-id="26363-268">**Host Class Asix Read** *(ux_host_class_asix_read)*</span></span> |
| ![ホスト クラス ASIX 書き込みアイコン](./media/user-guide/usbx-events/image81.png)    | <span data-ttu-id="26363-270">**ホスト クラス ASIX 書き込み** *(ux_host_class_asix_write)*</span><span class="sxs-lookup"><span data-stu-id="26363-270">**Host Class Asix Write** *(ux_host_class_asix_write)*</span></span> |
| ![ホスト クラス Audio アクティブ化アイコン](./media/user-guide/usbx-events/image82.png)    | <span data-ttu-id="26363-272">**ホスト クラス Audio アクティブ化** *(ux_host_class_audio_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-272">**Host Class Audio Activate** *(ux_host_class_audio_activate)*</span></span> |
| ![ホスト クラス Audio コントロール値取得アイコン](./media/user-guide/usbx-events/image83.png)    | <span data-ttu-id="26363-274">**ホスト クラス Audio コントロール値取得** *(ux_host_class_audio_control_value_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-274">**Host Class Audio Control Value Get** *(ux_host_class_audio_control_value_get)*</span></span> |
| ![ホスト クラス Audio コントロール値設定アイコン](./media/user-guide/usbx-events/image84.png)    | <span data-ttu-id="26363-276">**ホスト クラス Audio コントロール値設定** *(ux_host_class_audio_control_value_set)*</span><span class="sxs-lookup"><span data-stu-id="26363-276">**Host Class Audio Control Value Set** *(ux_host_class_audio_control_value_set)*</span></span> |
| ![ホスト クラス Audio 非アクティブ化アイコン](./media/user-guide/usbx-events/image85.png)    | <span data-ttu-id="26363-278">**ホスト クラス Audio 非アクティブ化** *(ux_host_class_audio_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-278">**Host Class Audio Deactivate** *(ux_host_class_audio_deactivate)*</span></span> |
| ![ホスト クラス Audio 読み取りアイコン](./media/user-guide/usbx-events/image86.png)    | <span data-ttu-id="26363-280">**ホスト クラス Audio 読み取り** *(ux_host_class_audio_read)*</span><span class="sxs-lookup"><span data-stu-id="26363-280">**Host Class Audio Read** *(ux_host_class_audio_read)*</span></span> |
| ![ホスト クラス Audio ストリーミング サンプリング取得アイコン](./media/user-guide/usbx-events/image87.png)    | <span data-ttu-id="26363-282">**ホスト クラス Audio ストリーミング サンプリング取得** *(ux_host_class_audio_streaming_sampling_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-282">**Host Class Audio Streaming Sampling Get** *(ux_host_class_audio_streaming_sampling_get)*</span></span> |
| ![ホスト クラス Audio ストリーミング サンプリング設定アイコン](./media/user-guide/usbx-events/image88.png)    | <span data-ttu-id="26363-284">**ホスト クラス Audio ストリーミング サンプリング設定** *(ux_host_class_audio_streaming_sampling_set)*</span><span class="sxs-lookup"><span data-stu-id="26363-284">**Host Class Audio Streaming Sampling Set** *(ux_host_class_audio_streaming_sampling_set)*</span></span> |
| ![ホスト クラス Audio 書き込みアイコン](./media/user-guide/usbx-events/image89.png)    | <span data-ttu-id="26363-286">**ホスト クラス Audio 書き込み** *(ux_host_class_audio_write)*</span><span class="sxs-lookup"><span data-stu-id="26363-286">**Host Class Audio Write** *(ux_host_class_audio_write)*</span></span> |
| ![ホスト クラス CDC ACM アクティブ化アイコン](./media/user-guide/usbx-events/image90.png)    | <span data-ttu-id="26363-288">**ホスト クラス CDC ACM アクティブ化** *(ux_host_class_cdc_acm_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-288">**Host Class Cdc Acm Activate** *(ux_host_class_cdc_acm_activate)*</span></span> |
| ![ホスト クラス CDC ACM 非アクティブ化アイコン](./media/user-guide/usbx-events/image91.png)    | <span data-ttu-id="26363-290">**ホスト クラス CDC ACM 非アクティブ化** *(ux_host_class_cdc_acm_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-290">**Host Class Cdc Acm Deactivate** *(ux_host_class_cdc_acm_deactivate)*</span></span> |
| ![ホスト クラス CDC ACM IOCTL 入力パイプ アイコン](./media/user-guide/usbx-events/image92.png)    | <span data-ttu-id="26363-292">**ホスト クラス CDC ACM IOCTL 入力パイプ アボート** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)*</span><span class="sxs-lookup"><span data-stu-id="26363-292">**Host Class Cdc Acm Ioctl Abort In Pipe** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)*</span></span> |
| ![ホスト クラス CDC ACM IOCTL 出力パイプ アボート アイコン](./media/user-guide/usbx-events/image93.png)    | <span data-ttu-id="26363-294">**ホスト クラス CDC ACM IOCTL 出力パイプ アボート** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)*</span><span class="sxs-lookup"><span data-stu-id="26363-294">**Host Class Cdc Acm Ioctl Abort Out Pipe** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)*</span></span> |
| ![ホスト クラス CDC ACM IOCTL デバイス状態取得アイコン](./media/user-guide/usbx-events/image94.png)    | <span data-ttu-id="26363-296">**ホスト クラス CDC ACM IOCTL デバイス状態取得** *(ux_host_class_cdc_acm_ioctl_get_device_status)*</span><span class="sxs-lookup"><span data-stu-id="26363-296">**Host Class Cdc Acm Ioctl Get Device Status** *(ux_host_class_cdc_acm_ioctl_get_device_status)*</span></span> |
| ![ホスト クラス CDC ACM IOCTL 伝送路符号化取得アイコン](./media/user-guide/usbx-events/image95.png)    | <span data-ttu-id="26363-298">**ホスト クラス CDC ACM IOCTL 伝送路符号化取得** *(ux_host_class_cdc_acm_ioctl_get_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="26363-298">**Host Class Cdc Acm Ioctl Get Line Coding** *(ux_host_class_cdc_acm_ioctl_get_line_coding)*</span></span> |
| ![ホスト クラス CDC ACM IOCTL 通知コールバック アイコン](./media/user-guide/usbx-events/image96.png)    | <span data-ttu-id="26363-300">**ホスト クラス CDC ACM IOCTL 通知コールバック** *(ux_host_class_cdc_acm_ioctl_notification_callback)*</span><span class="sxs-lookup"><span data-stu-id="26363-300">**Host Class Cdc Acm Ioctl Notification Callback** *(ux_host_class_cdc_acm_ioctl_notification_callback)*</span></span> |
| ![ホスト クラス CDC ACM IOCTL ブレーク送信アイコン](./media/user-guide/usbx-events/image97.png)    | <span data-ttu-id="26363-302">**ホスト クラス CDC ACM IOCTL ブレーク送信** *(ux_host_class_cdc_acm_ioctl_send_break)*</span><span class="sxs-lookup"><span data-stu-id="26363-302">**Host Class Cdc Acm Ioctl Send Break** *(ux_host_class_cdc_acm_ioctl_send_break)*</span></span> |
| ![ホスト クラス CDC ACM IOCTL 伝送路符号化設定アイコン](./media/user-guide/usbx-events/image98.png)    | <span data-ttu-id="26363-304">**ホスト クラス CDC ACM IOCTL 伝送路符号化設定** *(ux_host_class_cdc_acm_ioctl_set_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="26363-304">**Host Class Cdc Acm Ioctl Set Line Coding** *(ux_host_class_cdc_acm_ioctl_set_line_coding)*</span></span> |
| ![ホスト クラス CDC ACM IOCTL 伝送路状態設定アイコン](./media/user-guide/usbx-events/image99.png)    | <span data-ttu-id="26363-306">**ホスト クラス CDC ACM IOCTL 伝送路状態設定** *(ux_host_class_cdc_acm_ioctl_set_line_state)*</span><span class="sxs-lookup"><span data-stu-id="26363-306">**Host Class Cdc Acm Ioctl Set Line State** *(ux_host_class_cdc_acm_ioctl_set_line_state)*</span></span> |
| ![ホスト クラス CDC ACM 読み取りアイコン](./media/user-guide/usbx-events/image100.png)    | <span data-ttu-id="26363-308">**ホスト クラス CDC ACM 読み取り** *(ux_host_class_cdc_acm_read)*</span><span class="sxs-lookup"><span data-stu-id="26363-308">**Host Class Cdc Acm Read** *(ux_host_class_cdc_acm_read)*</span></span> |
| ![ホスト クラス CDC ACM 受信開始アイコン](./media/user-guide/usbx-events/image101.png)    | <span data-ttu-id="26363-310">**ホスト クラス CDC ACM 受信開始** *(ux_host_class_cdc_acm_reception_start)*</span><span class="sxs-lookup"><span data-stu-id="26363-310">**Host Class Cdc Acm Reception Start** *(ux_host_class_cdc_acm_reception_start)*</span></span> |
| ![ホスト クラス CDC ACM 受信停止アイコン](./media/user-guide/usbx-events/image102.png)    | <span data-ttu-id="26363-312">**ホスト クラス CDC ACM 受信停止** *(ux_host_class_cdc_acm_reception_stop)*</span><span class="sxs-lookup"><span data-stu-id="26363-312">**Host Class Cdc Acm Reception Stop** *(ux_host_class_cdc_acm_reception_stop)*</span></span> |
| ![ホスト クラス CDC ACM 書き込みアイコン](./media/user-guide/usbx-events/image103.png)    | <span data-ttu-id="26363-314">**ホスト クラス CDC ACM 書き込み** *(ux_host_class_cdc_acm_write)*</span><span class="sxs-lookup"><span data-stu-id="26363-314">**Host Class Cdc Acm Write** *(ux_host_class_cdc_acm_write)*</span></span> |
| ![ホスト クラス DPUMP アクティブ化アイコン](./media/user-guide/usbx-events/image104.png)    | <span data-ttu-id="26363-316">**ホスト クラス DPUMP アクティブ化** *(ux_host_class_dpump_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-316">**Host Class Dpump Activate** *(ux_host_class_dpump_activate)*</span></span> |
| ![ホスト クラス DPUMP 非アクティブ化アイコン](./media/user-guide/usbx-events/image105.png)    | <span data-ttu-id="26363-318">**ホスト クラス DPUMP 非アクティブ化** *(ux_host_class_dpump_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-318">**Host Class Dpump Deactivate** *(ux_host_class_dpump_deactivate)*</span></span> |
| ![ホスト クラス DPUMP 読み取りアイコン](./media/user-guide/usbx-events/image106.png)    | <span data-ttu-id="26363-320">**ホスト クラス DPUMP 読み取り** *(ux_host_class_dpump_read)*</span><span class="sxs-lookup"><span data-stu-id="26363-320">**Host Class Dpump Read** *(ux_host_class_dpump_read)*</span></span> |
| ![ホスト クラス DPUMP 書き込みアイコン](./media/user-guide/usbx-events/image107.png)    | <span data-ttu-id="26363-322">**ホスト クラス DPUMP 書き込み** *(ux_host_class_dpump_write)*</span><span class="sxs-lookup"><span data-stu-id="26363-322">**Host Class Dpump Write** *(ux_host_class_dpump_write)*</span></span> |
| ![ホスト クラス HID アクティブ化アイコン](./media/user-guide/usbx-events/image108.png)    | <span data-ttu-id="26363-324">**ホスト クラス HID アクティブ化** *(ux_host_class_hid_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-324">**Host Class Hid Activate** *(ux_host_class_hid_activate)*</span></span> |
| ![ホスト クラス HID クライアント登録アイコン](./media/user-guide/usbx-events/image109.png)    | <span data-ttu-id="26363-326">**ホスト クラス HID クライアント登録** *(ux_host_class_hid_client_register)*</span><span class="sxs-lookup"><span data-stu-id="26363-326">**Host Class Hid Client Register** *(ux_host_class_hid_client_register)*</span></span> |
| ![ホスト クラス HID 非アクティブ化アイコン](./media/user-guide/usbx-events/image110.png)    | <span data-ttu-id="26363-328">**ホスト クラス HID 非アクティブ化** *(ux_host_class_hid_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-328">**Host Class Hid Deactivate** *(ux_host_class_hid_deactivate)*</span></span> |
| ![ホスト クラス HID アイドル取得アイコン](./media/user-guide/usbx-events/image111.png)    | <span data-ttu-id="26363-330">**ホスト クラス HID アイドル取得** *(ux_host_class_hid_idle_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-330">**Host Class Hid Idle Get** *(ux_host_class_hid_idle_get)*</span></span> |
| ![ホスト クラス HID アイドル設定アイコン](./media/user-guide/usbx-events/image112.png)    | <span data-ttu-id="26363-332">**ホスト クラス HID アイドル設定** *(ux_host_class_hid_idle_set)*</span><span class="sxs-lookup"><span data-stu-id="26363-332">**Host Class Hid Idle Set** *(ux_host_class_hid_idle_set)*</span></span> |
| ![ホスト クラス HID キーボード アクティブ化アイコン](./media/user-guide/usbx-events/image113.png)    | <span data-ttu-id="26363-334">**ホスト クラス HID キーボード アクティブ化** *(ux_host_class_hid_keyboard_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-334">**Host Class Hid Keyboard Activate** *(ux_host_class_hid_keyboard_activate)*</span></span> |
| ![ホスト クラス HID キーボード非アクティブ化アイコン](./media/user-guide/usbx-events/image114.png)    | <span data-ttu-id="26363-336">**ホスト クラス HID キーボード非アクティブ化** *(ux_host_class_hid_keyboard_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-336">**Host Class Hid Keyboard Deactivate** *(ux_host_class_hid_keyboard_deactivate)*</span></span> |
| ![ホスト クラス HID マウス アクティブ化アイコン](./media/user-guide/usbx-events/image115.png)    | <span data-ttu-id="26363-338">**ホスト クラス HID マウス アクティブ化** *(ux_host_class_hid_mouse_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-338">**Host Class Hid Mouse Activate** *(ux_host_class_hid_mouse_activate)*</span></span> |
| ![ホスト クラス HID マウス非アクティブ化アイコン](./media/user-guide/usbx-events/image116.png)    | <span data-ttu-id="26363-340">**ホスト クラス HID マウス非アクティブ化** *(ux_host_class_hid_mouse_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-340">**Host Class Hid Mouse Deactivate** *(ux_host_class_hid_mouse_deactivate)*</span></span> |
| ![ホスト クラス HID リモート制御アクティブ化アイコン](./media/user-guide/usbx-events/image117.png)    | <span data-ttu-id="26363-342">**ホスト クラス HID リモート制御アクティブ化** *(ux_host_class_hid_remote_control_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-342">**Host Class Hid Remote Control Activate** *(ux_host_class_hid_remote_control_activate)*</span></span> |
| ![ホスト クラス HID リモート制御非アクティブ化アイコン](./media/user-guide/usbx-events/image118.png)    | <span data-ttu-id="26363-344">**ホスト クラス HID リモート制御非アクティブ化** *(ux_host_class_hid_remote_control_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-344">**Host Class Hid Remote Control Deactivate** *(ux_host_class_hid_remote_control_deactivate)*</span></span> |
| ![ホスト クラス HID レポート取得アイコン](./media/user-guide/usbx-events/image119.png)    | <span data-ttu-id="26363-346">**ホスト クラス HID レポート取得** *(ux_host_class_hid_report_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-346">**Host Class Hid Report Get** *(ux_host_class_hid_report_get)*</span></span> |
| ![ホスト クラス HID レポート設定アイコン](./media/user-guide/usbx-events/image120.png)    | <span data-ttu-id="26363-348">**ホスト クラス HID レポート設定** *(ux_host_class_hid_report_set)*</span><span class="sxs-lookup"><span data-stu-id="26363-348">**Host Class Hid Report Set** *(ux_host_class_hid_report_set)*</span></span> |
| ![ホスト クラス Hub アクティブ化アイコン](./media/user-guide/usbx-events/image121.png)    | <span data-ttu-id="26363-350">**ホスト クラス Hub アクティブ化** *(ux_host_class_hub_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-350">**Host Class Hub Activate** *(ux_host_class_hub_activate)*</span></span> |
| ![ホスト クラス Hub 変更検出アイコン](./media/user-guide/usbx-events/image122.png)    | <span data-ttu-id="26363-352">**ホスト クラス Hub 変更検出** *(ux_host_class_hub_change_detect)*</span><span class="sxs-lookup"><span data-stu-id="26363-352">**Host Class Hub Change Detect** *(ux_host_class_hub_change_detect)*</span></span> |
| ![\* ホストクラス Hub 非アクティブ化アイコン](./media/user-guide/usbx-events/image123.png)    | <span data-ttu-id="26363-354">**ホスト クラス Hub 非アクティブ化** *(ux_host_class_hub_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-354">**Host Class Hub Deactivate** *(ux_host_class_hub_deactivate)*</span></span> |
| ![ホスト クラス Hub ポート変更接続処理アイコン](./media/user-guide/usbx-events/image124.png)    | <span data-ttu-id="26363-356">**ホスト クラス Hub ポート変更接続処理** *(ux_host_class_hub_port_change_connection_process)*</span><span class="sxs-lookup"><span data-stu-id="26363-356">**Host Class Hub Port Change Connection Process** *(ux_host_class_hub_port_change_connection_process)*</span></span> |
| ![ホスト クラス Hub ポート変更有効化処理アイコン](./media/user-guide/usbx-events/image125.png)    | <span data-ttu-id="26363-358">**ホスト クラス Hub ポート変更有効化処理** *(ux_host_class_hub_port_change_enable_process)*</span><span class="sxs-lookup"><span data-stu-id="26363-358">**Host Class Hub Port Change Enable Process** *(ux_host_class_hub_port_change_enable_process)*</span></span> |
| ![ホスト クラス Hub ポート変更過電流処理アイコン](./media/user-guide/usbx-events/image126.png)    | <span data-ttu-id="26363-360">**ホスト クラス Hub ポート変更過電流処理** *(ux_host_class_hub_port_change_over_current_process)*</span><span class="sxs-lookup"><span data-stu-id="26363-360">**Host Class Hub Port Change Over Current Process** *(ux_host_class_hub_port_change_over_current_process)*</span></span> |
| ![ホスト クラス Hub ポート変更リセット処理アイコン](./media/user-guide/usbx-events/image127.png)    | <span data-ttu-id="26363-362">**ホスト クラス Hub ポート変更リセット処理** *(ux_host_class_hub_port_change_reset_process)*</span><span class="sxs-lookup"><span data-stu-id="26363-362">**Host Class Hub Port Change Reset Process** *(ux_host_class_hub_port_change_reset_process)*</span></span> |
| ![ホスト クラス Hub ポート変更中断処理アイコン](./media/user-guide/usbx-events/image128.png)    | <span data-ttu-id="26363-364">**ホスト クラス Hub ポート変更中断処理** *(ux_host_class_hub_port_change_suspend_process)*</span><span class="sxs-lookup"><span data-stu-id="26363-364">**Host Class Hub Port Change Suspend Process** *(ux_host_class_hub_port_change_suspend_process)*</span></span> |
| ![ホスト クラス PIMA アクティブ化アイコン](./media/user-guide/usbx-events/image129.png)    | <span data-ttu-id="26363-366">**ホスト クラス PIMA アクティブ化** *(ux_host_class_prima_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-366">**Host Class Pima Activate** *(ux_host_class_prima_activate)*</span></span> |
| ![ホスト クラス PIMA 非アクティブ化アイコン](./media/user-guide/usbx-events/image130.png)    | <span data-ttu-id="26363-368">**ホスト クラス PIMA 非アクティブ化** *(ux_host_class_pima_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-368">**Host Class Pima Deactivate** *(ux_host_class_pima_deactivate)*</span></span> |
| ![ホスト クラス PIMA デバイス情報取得アイコン](./media/user-guide/usbx-events/image131.png)    | <span data-ttu-id="26363-370">**ホスト クラス PIMA デバイス情報取得** *(ux_host_class_pima_device_info_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-370">**Host Class Pima Device Info Get** *(ux_host_class_pima_device_info_get)*</span></span> |
| ![ホスト クラス PIMA デバイス リセット アイコン](./media/user-guide/usbx-events/image132.png)    | <span data-ttu-id="26363-372">**ホスト クラス PIMA デバイス リセット** *(ux_host_class_pima_device_reset)*</span><span class="sxs-lookup"><span data-stu-id="26363-372">**Host Class Pima Device Reset** *(ux_host_class_pima_device_reset)*</span></span> |
| ![ホスト クラス PIMA 通知アイコン](./media/user-guide/usbx-events/image133.png)    | <span data-ttu-id="26363-374">**ホスト クラス PIMA 通知** *(ux_host_class_pima_notification)*</span><span class="sxs-lookup"><span data-stu-id="26363-374">**Host Class Pima Notification** *(ux_host_class_pima_notification)*</span></span> |
| ![ホスト クラス PIMA オブジェクト数取得アイコン](./media/user-guide/usbx-events/image134.png)    | <span data-ttu-id="26363-376">**ホスト クラス PIMA オブジェクト数取得** *(ux_host_class_pima_num_objects_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-376">**Host Class Pima Number Objects Get** *(ux_host_class_pima_num_objects_get)*</span></span> |
| ![ホスト クラス PIMA オブジェクト クローズ アイコン](./media/user-guide/usbx-events/image135.png)    | <span data-ttu-id="26363-378">**ホスト クラス PIMA オブジェクト クローズ** *(ux_host_class_pima_object_close)*</span><span class="sxs-lookup"><span data-stu-id="26363-378">**Host Class Pima Object Close** *(ux_host_class_pima_object_close)*</span></span> |
| ![ホスト クラス PIMA オブジェクト コピー アイコン](./media/user-guide/usbx-events/image136.png)    | <span data-ttu-id="26363-380">**ホスト クラス PIMA オブジェクト コピー** *(ux_host_class_pima_object_copy)*</span><span class="sxs-lookup"><span data-stu-id="26363-380">**Host Class Pima Object Copy** *(ux_host_class_pima_object_copy)*</span></span> |
| ![ホスト クラス PIMA オブジェクト削除アイコン](./media/user-guide/usbx-events/image137.png)    | <span data-ttu-id="26363-382">**ホスト クラス PIMA オブジェクト削除** *(ux_host_class_pima_object_delete)*</span><span class="sxs-lookup"><span data-stu-id="26363-382">**Host Class Pima Object Delete** *(ux_host_class_pima_object_delete)*</span></span> |
| ![ホスト クラス PIMA オブジェクト取得アイコン](./media/user-guide/usbx-events/image138.png)    | <span data-ttu-id="26363-384">**ホスト クラス PIMA オブジェクト取得** *(ux_host_class_pima_object_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-384">**Host Class Pima Object Get** *(ux_host_class_pima_object_get)*</span></span> |
| ![ホスト クラス PIMA オブジェクト情報取得アイコン](./media/user-guide/usbx-events/image139.png)    | <span data-ttu-id="26363-386">**ホスト クラス PIMA オブジェクト情報取得** *(ux_host_class_pima_object_info_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-386">**Host Class Pima Object Info Get** *(ux_host_class_pima_object_info_get)*</span></span> |
| ![ホスト クラス PIMA オブジェクト情報送信アイコン](./media/user-guide/usbx-events/image140.png)    | <span data-ttu-id="26363-388">**ホスト クラス PIMA オブジェクト情報送信** *(ux_host_class_pima_object_info_send)*</span><span class="sxs-lookup"><span data-stu-id="26363-388">**Host Class Pima Object Info Send** *(ux_host_class_pima_object_info_send)*</span></span> |
| ![ホスト クラス PIMA オブジェクト移動アイコン](./media/user-guide/usbx-events/image141.png)    | <span data-ttu-id="26363-390">**ホスト クラス PIMA オブジェクト移動** *(ux_host_class_pima_object_move)*</span><span class="sxs-lookup"><span data-stu-id="26363-390">**Host Class Pima Object Move** *(ux_host_class_pima_object_move)*</span></span> |
| ![ホスト クラス PIMA オブジェクト送信アイコン](./media/user-guide/usbx-events/image142.png)    | <span data-ttu-id="26363-392">**ホスト クラス PIMA オブジェクト送信** *(ux_host_class_pima_object_send)*</span><span class="sxs-lookup"><span data-stu-id="26363-392">**Host Class Pima Object Send** *(ux_host_class_pima_object_send)*</span></span> |
| ![ホスト クラス PIMA オブジェクト転送アボート アイコン](./media/user-guide/usbx-events/image143.png)    | <span data-ttu-id="26363-394">**ホスト クラス PIMA オブジェクト転送アボード** *(ux_host_class_object_transfer_abort)*</span><span class="sxs-lookup"><span data-stu-id="26363-394">**Host Class Pima Object Transfer Abort** *(ux_host_class_object_transfer_abort)*</span></span> |
| ![ホスト クラス PIMA 読み取りアイコン](./media/user-guide/usbx-events/image144.png)    | <span data-ttu-id="26363-396">**ホスト クラス PIMA 読み取り** *(ux_host_class_pima_read)*</span><span class="sxs-lookup"><span data-stu-id="26363-396">**Host Class Pima Read** *(ux_host_class_pima_read)*</span></span> |
| ![ホスト クラス PIMA 要求取り消しアイコン](./media/user-guide/usbx-events/image145.png)    | <span data-ttu-id="26363-398">**ホスト クラス PIMA 要求取り消し** *(ux_host_class_pima_request_cancel)*</span><span class="sxs-lookup"><span data-stu-id="26363-398">**Host Class Pima Request Cancel** *(ux_host_class_pima_request_cancel)*</span></span> |
| ![ホスト クラス PIMA セッション終了アイコン](./media/user-guide/usbx-events/image146.png)    | <span data-ttu-id="26363-400">**ホスト クラス PIMA セッション終了** *(ux_host_class_pima_session_close)*</span><span class="sxs-lookup"><span data-stu-id="26363-400">**Host Class Pima Session Close** *(ux_host_class_pima_session_close)*</span></span> |
| ![ホスト クラス PIMA セッション開始アイコン](./media/user-guide/usbx-events/image147.png)    | <span data-ttu-id="26363-402">**ホスト クラス PIMA セッション開始** *(ux_host_class_pima_session_open)*</span><span class="sxs-lookup"><span data-stu-id="26363-402">**Host Class Pima Session Open** *(ux_host_class_pima_session_open)*</span></span> |
| ![ホスト クラス PIMA ストレージ ID 取得アイコン](./media/user-guide/usbx-events/image148.png)    | <span data-ttu-id="26363-404">**ホスト クラス PIMA ストレージ ID 取得** *(ux_host_class_pima_storage_ids_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-404">**Host Class Pima Storage Ids Get** *(ux_host_class_pima_storage_ids_get)*</span></span> |
| ![ホスト クラス PIMA ストレージ情報取得アイコン](./media/user-guide/usbx-events/image149.png)    | <span data-ttu-id="26363-406">**ホスト クラス PIMA ストレージ情報取得** *(ux_host_class_pima_storage_info_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-406">**Host Class Pima Storage Info Get** *(ux_host_class_pima_storage_info_get)*</span></span> |
| ![ホスト クラス PIMA Thumb 取得アイコン](./media/user-guide/usbx-events/image150.png)    | <span data-ttu-id="26363-408">**ホスト クラス PIMA Thumb 取得** *(ux_host_class_pima_thumb_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-408">**Host Class Pima Thumb Get** *(ux_host_class_pima_thumb_get)*</span></span> |
| ![ホスト クラス PIMA 書き込みアイコン](./media/user-guide/usbx-events/image151.png)    | <span data-ttu-id="26363-410">**ホスト クラス PIMA 書き込み** *(ux_host_class_pima_write)*</span><span class="sxs-lookup"><span data-stu-id="26363-410">**Host Class Pima Write** *(ux_host_class_pima_write)*</span></span> |
| ![ホスト クラス Printer アクティブ化アイコン](./media/user-guide/usbx-events/image152.png)    | <span data-ttu-id="26363-412">**ホスト クラス Printer アクティブ化** *(ux_host_class_printer_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-412">**Host Class Printer Activate** *(ux_host_class_printer_activate)*</span></span> |
| ![ホスト クラス Printer 非アクティブ化アイコン](./media/user-guide/usbx-events/image153.png)    | <span data-ttu-id="26363-414">**ホスト クラス Printer 非アクティブ化** *(ux_host_class_printer_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-414">**Host Class Printer Deactivate** *(ux_host_class_printer_deactivate)*</span></span> |
| ![ホスト クラス Printer 名前取得アイコン](./media/user-guide/usbx-events/image154.png)    | <span data-ttu-id="26363-416">**ホスト クラス Printer 名前取得** *(ux_host_class_printer_name_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-416">**Host Class Printer Name Get** *(ux_host_class_printer_name_get)*</span></span> |
| ![ホスト クラス Printer 読み取りアイコン](./media/user-guide/usbx-events/image155.png)    |  <span data-ttu-id="26363-418">**ホスト クラス Printer 読み取り** *(ux_host_class_printer_read)*</span><span class="sxs-lookup"><span data-stu-id="26363-418">**Host Class Printer Read** *(ux_host_class_printer_read)*</span></span> |
| ![ホスト クラス Printer ソフト リセット アイコン](./media/user-guide/usbx-events/image156.png)    | <span data-ttu-id="26363-420">**ホスト クラス Printer ソフト リセット** *(ux_host_class_printer_soft_reset)*</span><span class="sxs-lookup"><span data-stu-id="26363-420">**Host Class Printer Soft Reset** *(ux_host_class_printer_soft_reset)*</span></span> |
| ![ホスト クラス Printer 状態取得アイコン](./media/user-guide/usbx-events/image157.png)    | <span data-ttu-id="26363-422">**ホスト クラス Printer 状態取得** *(ux_host_class_printer_status_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-422">**Host Class Printer Status Get** *(ux_host_class_printer_status_get)*</span></span> |
| ![ホスト クラス Printer 書き込みアイコン](./media/user-guide/usbx-events/image158.png)    | <span data-ttu-id="26363-424">**ホスト クラス Printer 書き込み** *(ux_host_class_printer_write)*</span><span class="sxs-lookup"><span data-stu-id="26363-424">**Host Class Printer Write** *(ux_host_class_printer_write)*</span></span> |
| ![ホスト クラス Prolific アクティブ化アイコン](./media/user-guide/usbx-events/image159.png)    | <span data-ttu-id="26363-426">**ホスト クラス Prolific アクティブ化** *(ux_host_class_prolific_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-426">**Host Class Prolific Activate** *(ux_host_class_prolific_activate)*</span></span> |
| ![ホスト クラス Prolific 非アクティブ化アイコン](./media/user-guide/usbx-events/image160.png)    | <span data-ttu-id="26363-428">**ホスト クラス Prolific 非アクティブ化** *(ux_host_class_prolific_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-428">**Host Class Prolific Deactivate** *(ux_host_class_prolific_deactivate)*</span></span> |
| ![ホスト クラス Prolific IOCTL 入力パイプ アボート アイコン](./media/user-guide/usbx-events/image161.png)    | <span data-ttu-id="26363-430">**ホスト クラス Prolific IOCTL 入力パイプ アボート** *(ux_host_class_prolific_ioctl_abort_in_pipe)*</span><span class="sxs-lookup"><span data-stu-id="26363-430">**Host Class Prolific Ioctl Abort In Pipe** *(ux_host_class_prolific_ioctl_abort_in_pipe)*</span></span> |
| ![ホスト クラス Prolific IOCTL 出力パイプ アボート アイコン](./media/user-guide/usbx-events/image162.png)    | <span data-ttu-id="26363-432">**ホスト クラス Prolific IOCTL 出力パイプ アボート** *(ux_host_class_prolific_ioctl_abort_out_pipe)*</span><span class="sxs-lookup"><span data-stu-id="26363-432">**Host Class Prolific Ioctl Abort Out Pipe** *(ux_host_class_prolific_ioctl_abort_out_pipe)*</span></span> |
| ![ホスト クラス Prolific IOCTL デバイス情報取得アイコン](./media/user-guide/usbx-events/image163.png)    | <span data-ttu-id="26363-434">**ホスト クラス Prolific IOCTL デバイス情報取得** *(ux_host_class_prolific_ioctl_get_device_status)*</span><span class="sxs-lookup"><span data-stu-id="26363-434">**Host Class Prolific Ioctl Get Device Status** *(ux_host_class_prolific_ioctl_get_device_status)*</span></span> |
| ![ホスト クラス Prolific IOCTL 伝送路符号化取得アイコン](./media/user-guide/usbx-events/image164.png)    | <span data-ttu-id="26363-436">**ホスト クラス Prolific IOCTL 伝送路符号化取得** *(ux_host_class_prolific_ioctl_get_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="26363-436">**Host Class Prolific Ioctl Get Line Coding** *(ux_host_class_prolific_ioctl_get_line_coding)*</span></span> |
| ![ホスト クラス Prolific IOCTL パージ アイコン](./media/user-guide/usbx-events/image165.png)    | <span data-ttu-id="26363-438">**ホスト クラス Prolific IOCTL パージ** *(ux_host_class_prolific_ioctl_purge)*</span><span class="sxs-lookup"><span data-stu-id="26363-438">**Host Class Prolific Ioctl Purge** *(ux_host_class_prolific_ioctl_purge)*</span></span> |
| ![ホスト クラス Prolific IOCTL デバイス状態変更報告アイコン](./media/user-guide/usbx-events/image166.png)    | <span data-ttu-id="26363-440">**ホスト クラス Prolific IOCTL デバイス状態変更報告** *(ux_host_class_prolific_ioctl_report_device_status_change)*</span><span class="sxs-lookup"><span data-stu-id="26363-440">**Host Class Prolific Ioctl Report Device Status Change** *(ux_host_class_prolific_ioctl_report_device_status_change)*</span></span> |
| ![ホスト クラス Prolific IOCTL ブレーク送信アイコン](./media/user-guide/usbx-events/image167.png)    | <span data-ttu-id="26363-442">**ホスト クラス Prolific IOCTL ブレーク送信** *(ux_host_class_prolific_ioctl_send_break)*</span><span class="sxs-lookup"><span data-stu-id="26363-442">**Host Class Prolific Ioctl Send Break** *(ux_host_class_prolific_ioctl_send_break)*</span></span> |
| ![ホスト クラス Prolific IOCTL 伝送路符号化設定アイコン](./media/user-guide/usbx-events/image168.png)    | <span data-ttu-id="26363-444">**ホスト クラス Prolific IOCTL 伝送路符号化設定** *(ux_host_class_prolific_ioctl_set_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="26363-444">**Host Class Prolific Ioctl Set Line Coding** *(ux_host_class_prolific_ioctl_set_line_coding)*</span></span> |
| ![ホスト クラス Prolific IOCTL 伝送路状態設定アイコン](./media/user-guide/usbx-events/image169.png)    | <span data-ttu-id="26363-446">**ホスト クラス Prolific IOCTL 伝送路状態設定** *(ux_host_class_prolific_ioctl_set_line_state)*</span><span class="sxs-lookup"><span data-stu-id="26363-446">**Host Class Prolific Ioctl Set Line State** *(ux_host_class_prolific_ioctl_set_line_state)*</span></span> |
| ![ホスト クラス Prolific 読み取りアイコン](./media/user-guide/usbx-events/image170.png)    | <span data-ttu-id="26363-448">**ホスト クラス Prolific 読み取り** *(ux_host_class_prolific_read)*</span><span class="sxs-lookup"><span data-stu-id="26363-448">**Host Class Prolific Read** *(ux_host_class_prolific_read)*</span></span> |
| ![ホスト クラス Prolific 受信開始アイコン](./media/user-guide/usbx-events/image171.png)    | <span data-ttu-id="26363-450">**ホスト クラス Prolific 受信開始** *(ux_host_class_prolific_reception_start)*</span><span class="sxs-lookup"><span data-stu-id="26363-450">**Host Class Prolific Reception Start** *(ux_host_class_prolific_reception_start)*</span></span> |
| ![ホスト クラス Prolific 受信停止アイコン](./media/user-guide/usbx-events/image172.png)    | <span data-ttu-id="26363-452">**ホスト クラス Prolific 受信停止** *(ux_host_class_prolific_reception_stop)*</span><span class="sxs-lookup"><span data-stu-id="26363-452">**Host Class Prolific Reception Stop** *(ux_host_class_prolific_reception_stop)*</span></span> |
| ![ホスト クラス Prolific 書き込みアイコン](./media/user-guide/usbx-events/image173.png)    | <span data-ttu-id="26363-454">**ホスト クラス Prolific 書き込み** *(ux_host_class_prolific_write)*</span><span class="sxs-lookup"><span data-stu-id="26363-454">**Host Class Prolific Write** *(ux_host_class_prolific_write)*</span></span> |
| ![ホスト クラス Storage アクティブ化アイコン](./media/user-guide/usbx-events/image174.png)    | <span data-ttu-id="26363-456">**ホスト クラス Storage アクティブ化** *(ux_host_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-456">**Host Class Storage Activate** *(ux_host_class_storage_activate)*</span></span> |
| ![ホスト クラス Storage 非アクティブ化アイコン](./media/user-guide/usbx-events/image175.png)    | <span data-ttu-id="26363-458">**ホスト クラス Storage 非アクティブ化** (*ux_host_class_storage_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="26363-458">**Host Class Storage Deactivate** (*ux_host_class_storage_deactivate)*</span></span> |
| ![ホスト クラス Storage メディア容量取得アイコン](./media/user-guide/usbx-events/image176.png)    | <span data-ttu-id="26363-460">**ホスト クラス Storage メディア容量取得** *(ux_host_class_storage_media_capacity_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-460">**Host Class Storage Media Capacity Get** *(ux_host_class_storage_media_capacity_get)*</span></span> |
| ![ホスト クラス Storage メディア フォーマット容量取得アイコン](./media/user-guide/usbx-events/image177.png)    | <span data-ttu-id="26363-462">**ホスト クラス Storage メディア フォーマット容量取得** *(ux_host_class_storage_media_format_capacity_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-462">**Host Class Storage Media Format Capacity Get** *(ux_host_class_storage_media_format_capacity_get)*</span></span> |
| ![ホスト クラス Storage メディア マウント アイコン](./media/user-guide/usbx-events/image178.png)    | <span data-ttu-id="26363-464">**ホスト クラス Storage メディア マウント** (ux_host_class_storage_media_mount)\*</span><span class="sxs-lookup"><span data-stu-id="26363-464">**Host Class Storage Media Mount** (ux_host_class_storage_media_mount)\*</span></span> |
| ![ホスト クラス Storage メディア オープン アイコン](./media/user-guide/usbx-events/image179.png)    | <span data-ttu-id="26363-466">**ホスト クラス Storage メディア オープン** *(ux_host_class_storage_media_open)*</span><span class="sxs-lookup"><span data-stu-id="26363-466">**Host Class Storage Media Open** *(ux_host_class_storage_media_open)*</span></span> |
| ![ホスト クラス Storage メディア読み取りアイコン](./media/user-guide/usbx-events/image180.png)    | <span data-ttu-id="26363-468">**ホスト クラス Storage メディア読み取り** *(ux_host_class_storage_media_read)*</span><span class="sxs-lookup"><span data-stu-id="26363-468">**Host Class Storage Media Read** *(ux_host_class_storage_media_read)*</span></span> |
| ![ホスト クラス Storage メディア書き込みアイコン](./media/user-guide/usbx-events/image181.png)    | <span data-ttu-id="26363-470">**ホスト クラス Storage メディア書き込み** *(ux_host_class_storage_media_write)*</span><span class="sxs-lookup"><span data-stu-id="26363-470">**Host Class Storage Media Write** *(ux_host_class_storage_media_write)*</span></span> |
| ![ホスト クラス Storage センス データ要求アイコン](./media/user-guide/usbx-events/image182.png)    | <span data-ttu-id="26363-472">**ホスト クラス Storage センス データ要求** *(ux_host_class_storage_request_sense)*</span><span class="sxs-lookup"><span data-stu-id="26363-472">**Host Class Storage Request Sense** *(ux_host_class_storage_request_sense)*</span></span> |
| ![ホスト クラス Storage 開始/停止アイコン](./media/user-guide/usbx-events/image183.png)    | <span data-ttu-id="26363-474">**ホスト クラス Storage 開始/停止** *(ux_host_class_storage_start_stop)*</span><span class="sxs-lookup"><span data-stu-id="26363-474">**Host Class Storage Start Stop** *(ux_host_class_storage_start_stop)*</span></span> |
| ![ホスト クラス Storage ユニット準備状態テスト アイコン](./media/user-guide/usbx-events/image184.png)    | <span data-ttu-id="26363-476">**ホスト クラス Storage ユニット準備状態テスト** *(ux_host_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="26363-476">**Host Class Storage Unit Ready Test** *(ux_host_class_storage_activate)*</span></span> |
| ![ホスト スタック クラス インスタンス作成アイコン](./media/user-guide/usbx-events/image185.png)    | <span data-ttu-id="26363-478">**ホスト スタック クラス インスタンス作成** *(ux_host_stack_class_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="26363-478">**Host Stack Class Instance Create** *(ux_host_stack_class_instance_create)*</span></span> |
| ![ホスト スタック クラス インスタンス破棄アイコン](./media/user-guide/usbx-events/image186.png)    | <span data-ttu-id="26363-480">**ホスト スタック クラス インスタンス破棄** *(ux_host_stack_class_instance_destroy)*</span><span class="sxs-lookup"><span data-stu-id="26363-480">**Host Stack Class Instance Destroy** *(ux_host_stack_class_instance_destroy)*</span></span> |
| ![ホスト スタック構成削除アイコン](./media/user-guide/usbx-events/image187.png)    | <span data-ttu-id="26363-482">**ホスト スタック構成削除** *(ux_host_stack_configuration_delete)*</span><span class="sxs-lookup"><span data-stu-id="26363-482">**Host Stack Configuration Delete** *(ux_host_stack_configuration_delete)*</span></span> |
| ![ホスト スタック構成エニュメレーション アイコン](./media/user-guide/usbx-events/image188.png)    | <span data-ttu-id="26363-484">**ホスト スタック構成エニュメレーション** *(ux_host_stack_configuration_enumerate)*</span><span class="sxs-lookup"><span data-stu-id="26363-484">**Host Stack Configuration Enumerate** *(ux_host_stack_configuration_enumerate)*</span></span> |
| ![ホスト スタック構成インスタンス作成アイコン](./media/user-guide/usbx-events/image189.png)    | <span data-ttu-id="26363-486">**ホスト スタック構成インスタンス作成** *(ux_host_stack_configuration_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="26363-486">**Host Stack Configuration Instance Create** *(ux_host_stack_configuration_instance_create)*</span></span> |
| ![ホスト スタック構成インスタンス削除アイコン](./media/user-guide/usbx-events/image190.png)    | <span data-ttu-id="26363-488">**ホスト スタック構成インスタンス削除** *(ux_host_stack_configuration_instance_delete)*</span><span class="sxs-lookup"><span data-stu-id="26363-488">**Host Stack Configuration Instance Delete** *(ux_host_stack_configuration_instance_delete)*</span></span> |
| ![ホスト スタック構成設定アイコン](./media/user-guide/usbx-events/image191.png)    | <span data-ttu-id="26363-490">**ホスト スタック構成設定** *(ux_host_stack_configuration_set)*</span><span class="sxs-lookup"><span data-stu-id="26363-490">**Host Stack Configuration Set** *(ux_host_stack_configuration_set)*</span></span> |
| ![ホスト スタック デバイス アドレス設定アイコン](./media/user-guide/usbx-events/image192.png)    | <span data-ttu-id="26363-492">**ホスト スタック デバイス アドレス設定** *(ux_host_stack_device_set)*</span><span class="sxs-lookup"><span data-stu-id="26363-492">**Host Stack Device Address Set** *(ux_host_stack_device_set)*</span></span> |
| ![ホスト スタック デバイス構成取得アイコン](./media/user-guide/usbx-events/image193.png)    | <span data-ttu-id="26363-494">**ホスト スタック デバイス構成取得** *(ux_host_stack_device_configuration_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-494">**Host Stack Device Configuration Get** *(ux_host_stack_device_configuration_get)*</span></span> |
| ![ホスト スタック デバイス構成選択アイコン](./media/user-guide/usbx-events/image194.png)    | <span data-ttu-id="26363-496">**ホスト スタック デバイス構成選択** *(ux_host_stack_device_configuration_select)*</span><span class="sxs-lookup"><span data-stu-id="26363-496">**Host Stack Device Configuration Select** *(ux_host_stack_device_configuration_select)*</span></span> |
| ![ホスト スタック デバイス記述子読み取りアイコン](./media/user-guide/usbx-events/image195.png)    | <span data-ttu-id="26363-498">**ホスト スタック デバイス記述子読み取り** *(ux_host_stack_device_descriptor_read)*</span><span class="sxs-lookup"><span data-stu-id="26363-498">**Host Stack Device Descriptor Read** *(ux_host_stack_device_descriptor_read)*</span></span> |
| ![ホスト スタック デバイス取得アイコン](./media/user-guide/usbx-events/image196.png)    | <span data-ttu-id="26363-500">**ホスト スタック デバイス取得** (ux_host_stack_device_get)</span><span class="sxs-lookup"><span data-stu-id="26363-500">**Host Stack Device Get** (ux_host_stack_device_get)</span></span> |
| ![ホスト スタック デバイス取り外しアイコン](./media/user-guide/usbx-events/image197.png)    | <span data-ttu-id="26363-502">**ホスト スタック デバイス取り外し** (ux_host_stack_device_get)</span><span class="sxs-lookup"><span data-stu-id="26363-502">**Host Stack Device Remove** (ux_host_stack_device_get)</span></span> |
| ![ホスト スタック デバイス リソース解放アイコン](./media/user-guide/usbx-events/image198.png)    | <span data-ttu-id="26363-504">**ホスト スタック デバイス リソース解放** (ux_host_stack_device_resource_free)</span><span class="sxs-lookup"><span data-stu-id="26363-504">**Host Stack Device Resource Free** (ux_host_stack_device_resource_free)</span></span> |
| ![ホスト スタック エンドポイント インスタンス作成アイコン](./media/user-guide/usbx-events/image199.png)    | <span data-ttu-id="26363-506">**ホスト スタック エンドポイント インスタンス作成** (ux_host_stack_endpoint_instance_create)</span><span class="sxs-lookup"><span data-stu-id="26363-506">**Host Stack Endpoint Instance Create** (ux_host_stack_endpoint_instance_create)</span></span> |
| ![ホスト スタック エンドポイント インスタンス削除アイコン](./media/user-guide/usbx-events/image200.png)    | <span data-ttu-id="26363-508">**ホスト スタック エンドポイント インスタンス削除** (ux_host_stack_endpoint_instance_delete)</span><span class="sxs-lookup"><span data-stu-id="26363-508">**Host Stack Endpoint Instance Delete** (ux_host_stack_endpoint_instance_delete)</span></span> |
| ![ホスト スタック エンドポイント リセット アイコン](./media/user-guide/usbx-events/image201.png)    | <span data-ttu-id="26363-510">**ホスト スタック エンドポイント リセット** (ux_host_stack_endpoint_reset)</span><span class="sxs-lookup"><span data-stu-id="26363-510">**Host Stack Endpoint Reset** (ux_host_stack_endpoint_reset)</span></span> |
| ![ホスト スタック エンドポイント転送アボート アイコン](./media/user-guide/usbx-events/image202.png)    | <span data-ttu-id="26363-512">**ホスト スタック エンドポイント転送アボート** (ux_host_stack_endpoint_transfer_abort)</span><span class="sxs-lookup"><span data-stu-id="26363-512">**Host Stack Endpoint Transfer Abort** (ux_host_stack_endpoint_transfer_abort)</span></span> |
| ![ホスト スタック ホスト コントローラー登録アイコン](./media/user-guide/usbx-events/image203.png)    | <span data-ttu-id="26363-514">**ホスト スタック ホスト コントローラー登録** *(ux_host_stack_hcd_register)*</span><span class="sxs-lookup"><span data-stu-id="26363-514">**Host Stack Host Controller Register** *(ux_host_stack_hcd_register)*</span></span> |
| ![ホスト スタック初期化アイコン](./media/user-guide/usbx-events/image204.png)    | <span data-ttu-id="26363-516">**ホスト スタック初期化** *(ux_host_stack_initialize)*</span><span class="sxs-lookup"><span data-stu-id="26363-516">**Host Stack Initialize** *(ux_host_stack_initialize)*</span></span> |
| ![ホスト スタック インターフェイス エンドポイント取得アイコン](./media/user-guide/usbx-events/image205.png)    | <span data-ttu-id="26363-518">**ホスト スタック インターフェイス エンドポイント取得** *(ux_host_stack_interface_endpoint_get)*</span><span class="sxs-lookup"><span data-stu-id="26363-518">**Host Stack Interface Endpoint Get** *(ux_host_stack_interface_endpoint_get)*</span></span> |
| ![ホスト スタック インターフェイス インスタンス作成アイコン](./media/user-guide/usbx-events/image206.png)    | <span data-ttu-id="26363-520">**ホスト スタック インターフェイス インスタンス作成** *(ux_host_stack_interface_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="26363-520">**Host Stack Interface Instance Create** *(ux_host_stack_interface_instance_create)*</span></span> |
| ![ホスト スタック インターフェイス インスタンス削除アイコン](./media/user-guide/usbx-events/image207.png)    | <span data-ttu-id="26363-522">**ホスト スタック インターフェイス インスタンス削除** *(ux_host_stack_interface_instance_delete)*</span><span class="sxs-lookup"><span data-stu-id="26363-522">**Host Stack Interface Instance Delete** *(ux_host_stack_interface_instance_delete)*</span></span> |
| ![ホスト スタック インターフェイス設定アイコン](./media/user-guide/usbx-events/image208.png)    | <span data-ttu-id="26363-524">**ホスト スタック インターフェイス設定** *(ux_host_stack_interface_set)*</span><span class="sxs-lookup"><span data-stu-id="26363-524">**Host Stack Interface Set** *(ux_host_stack_interface_set)*</span></span> |
| ![ホスト スタック インターフェイス設定選択アイコン](./media/user-guide/usbx-events/image209.png)    | <span data-ttu-id="26363-526">**ホスト スタック インターフェイス設定選択** *(ux_host_stack_interface_setting_select)*</span><span class="sxs-lookup"><span data-stu-id="26363-526">**Host Stack Interface Setting Select** *(ux_host_stack_interface_setting_select)*</span></span> |
| ![ホスト スタック新規構成作成アイコン](./media/user-guide/usbx-events/image210.png)    | <span data-ttu-id="26363-528">**ホスト スタック新規構成作成** *(ux_host_stack_new_configuration_create)*</span><span class="sxs-lookup"><span data-stu-id="26363-528">**Host Stack New Configuration Create** *(ux_host_stack_new_configuration_create)*</span></span> |
| ![ホスト スタック新規デバイス作成アイコン](./media/user-guide/usbx-events/image211.png)    | <span data-ttu-id="26363-530">**ホスト スタック新規デバイス作成** *(ux_host_stack_new_device_create)*</span><span class="sxs-lookup"><span data-stu-id="26363-530">**Host Stack New Device Create** *(ux_host_stack_new_device_create)*</span></span> |
| ![ホスト スタック新規エンドポイント作成アイコン](./media/user-guide/usbx-events/image212.png)    | <span data-ttu-id="26363-532">**ホスト スタック新規エンドポイント作成** *(ux_host_stack_new_endpoint_create)*</span><span class="sxs-lookup"><span data-stu-id="26363-532">**Host Stack New Endpoint Create** *(ux_host_stack_new_endpoint_create)*</span></span> |
| ![ホスト スタック ルート ハブ変更処理アイコン](./media/user-guide/usbx-events/image213.png)    | <span data-ttu-id="26363-534">**ホスト スタック ルート ハブ変更処理** *(ux_host_stack_rh_change_process)*</span><span class="sxs-lookup"><span data-stu-id="26363-534">**Host Stack Root Hub Change Process** *(ux_host_stack_rh_change_process)*</span></span> |
| ![ホスト スタック ルート ハブ デバイス抽出アイコン](./media/user-guide/usbx-events/image214.png)    | <span data-ttu-id="26363-536">**ホスト スタック ルート ハブ デバイス抽出** *(ux_host_stack_rh_device_extraction)*</span><span class="sxs-lookup"><span data-stu-id="26363-536">**Host Stack Root Hub Device Extraction** *(ux_host_stack_rh_device_extraction)*</span></span> |
| ![ホスト スタック ルート ハブ デバイス挿入アイコン](./media/user-guide/usbx-events/image215.png)    | <span data-ttu-id="26363-538">**ホスト スタック ルート ハブ デバイス挿入** *(ux_host_stack_rh_device_insertion)*</span><span class="sxs-lookup"><span data-stu-id="26363-538">**Host Stack Root Hub Device Insertion** *(ux_host_stack_rh_device_insertion)*</span></span> |
| ![ホスト スタック転送要求アイコン](./media/user-guide/usbx-events/image216.png)    | <span data-ttu-id="26363-540">**ホスト スタック転送要求** *(ux_host_stack_transfer_request)*</span><span class="sxs-lookup"><span data-stu-id="26363-540">**Host Stack Transfer Request** *(ux_host_stack_transfer_request)*</span></span> |
| ![ホスト スタック転送要求アボート アイコン](./media/user-guide/usbx-events/image217.png)    | <span data-ttu-id="26363-542">**ホスト スタック転送要求アボート** *(ux_host_stack_transfer_request_abort)*</span><span class="sxs-lookup"><span data-stu-id="26363-542">**Host Stack Transfer Request Abort** *(ux_host_stack_transfer_request_abort)*</span></span> |
| ![USBX エラー アイコン](./media/user-guide/usbx-events/image218.png)    | <span data-ttu-id="26363-544">**USBX エラー** *(ux_error)*</span><span class="sxs-lookup"><span data-stu-id="26363-544">**USBX Error** *(ux_error)*</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="26363-545">イベントの説明</span><span class="sxs-lookup"><span data-stu-id="26363-545">Event Descriptions</span></span>

<span data-ttu-id="26363-546">以下のページでは USBX トレース イベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="26363-546">The following pages describe the USBX Trace Events.</span></span>

### <a name="device-class-cdc-activate"></a><span data-ttu-id="26363-547">デバイス クラス CDC アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-547">Device Class Cdc Activate</span></span> 

#### <a name="ux_device_class_cdc_activate"></a><span data-ttu-id="26363-548">ux_device_class_cdc_activate</span><span class="sxs-lookup"><span data-stu-id="26363-548">ux_device_class_cdc_activate</span></span>

<span data-ttu-id="26363-549">**アイコン** ![デバイス クラス CDC アクティブ化アイコン](./media/user-guide/usbx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="26363-549">**Icon** ![Device Class C D C Activate icon](./media/user-guide/usbx-events/image1.png)</span></span>

<span data-ttu-id="26363-550">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-550">**Description**</span></span>

<span data-ttu-id="26363-551">USBX デバイス クラス CDC アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-551">This event represents a USBX Device Class Cdc Activate Event.</span></span>

<span data-ttu-id="26363-552">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-552">**Information Fields**</span></span> 

- <span data-ttu-id="26363-553">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-553">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-554">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-554">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-555">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-555">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-556">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-556">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-deactivate"></a><span data-ttu-id="26363-557">デバイス クラス CDC 非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-557">Device Class Cdc Deactivate</span></span> 

#### <a name="ux_device_class_cdc_deactivate"></a><span data-ttu-id="26363-558">ux_device_class_cdc_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-558">ux_device_class_cdc_deactivate</span></span>

<span data-ttu-id="26363-559">**アイコン** ![デバイス クラス CDC 非アクティブ化アイコン](./media/user-guide/usbx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="26363-559">**Icon** ![Device Class C D C Deactivate icon](./media/user-guide/usbx-events/image2.png)</span></span>

<span data-ttu-id="26363-560">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-560">**Description**</span></span>

<span data-ttu-id="26363-561">USBX デバイス クラス CDC 非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-561">This event represents a USBX Device Class Cdc Deactivate.</span></span>

<span data-ttu-id="26363-562">情報フィールド</span><span class="sxs-lookup"><span data-stu-id="26363-562">Information Fields</span></span> 

- <span data-ttu-id="26363-563">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-563">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-564">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-564">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-565">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-565">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-566">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-566">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-read"></a><span data-ttu-id="26363-567">デバイス クラス CDC 読み取り</span><span class="sxs-lookup"><span data-stu-id="26363-567">Device Class Cdc Read</span></span> 

#### <a name="ux_device_class_cdc_read"></a><span data-ttu-id="26363-568">ux_device_class_cdc_read</span><span class="sxs-lookup"><span data-stu-id="26363-568">ux_device_class_cdc_read</span></span>

<span data-ttu-id="26363-569">**アイコン** ![デバイス クラス CDC 読み取りアイコン](./media/user-guide/usbx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="26363-569">**Icon** ![Device Class C D C Read icon](./media/user-guide/usbx-events/image3.png)</span></span>

<span data-ttu-id="26363-570">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-570">**Description**</span></span>

<span data-ttu-id="26363-571">USBX デバイス クラス CDC 読み取りイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-571">This event represents a USBX Device Class Cdc Read Event.</span></span>

<span data-ttu-id="26363-572">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-572">**Information Fields**</span></span>

- <span data-ttu-id="26363-573">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-573">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-574">情報フィールド 2: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-574">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="26363-575">情報フィールド 3: 要求された長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-575">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="26363-576">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-576">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-write"></a><span data-ttu-id="26363-577">デバイス クラス CDC 書き込み</span><span class="sxs-lookup"><span data-stu-id="26363-577">Device Class Cdc Write</span></span> 

#### <a name="ux_device_class_cdc_write"></a><span data-ttu-id="26363-578">ux_device_class_cdc_write</span><span class="sxs-lookup"><span data-stu-id="26363-578">ux_device_class_cdc_write</span></span>

<span data-ttu-id="26363-579">**アイコン** ![デバイス クラス CDC 書き込みアイコン](./media/user-guide/usbx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="26363-579">**Icon** ![Device Class C D C Write icon](./media/user-guide/usbx-events/image4.png)</span></span>

<span data-ttu-id="26363-580">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-580">**Description**</span></span>

<span data-ttu-id="26363-581">USBX デバイス クラス CDC 書き込みイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-581">This event represents a USBX Device Class Cdc Write Event.</span></span>

<span data-ttu-id="26363-582">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-582">**Information Fields**</span></span>

- <span data-ttu-id="26363-583">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-583">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-584">情報フィールド 2: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-584">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="26363-585">情報フィールド 3: 要求された長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-585">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="26363-586">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-586">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-activate"></a><span data-ttu-id="26363-587">デバイス クラス DPUMP アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-587">Device Class Dpump Activate</span></span> 

#### <a name="ux_device_class_dpump_activate"></a><span data-ttu-id="26363-588">ux_device_class_dpump_activate</span><span class="sxs-lookup"><span data-stu-id="26363-588">ux_device_class_dpump_activate</span></span>

<span data-ttu-id="26363-589">**アイコン** ![デバイス クラス DPUMP アクティブ化アイコン](./media/user-guide/usbx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="26363-589">**Icon** ![Device Class Dpump Activate icon](./media/user-guide/usbx-events/image5.png)</span></span>

<span data-ttu-id="26363-590">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-590">**Description**</span></span>

<span data-ttu-id="26363-591">USBX デバイス クラス DPUMP アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-591">This event represents a USBX Device Class Dpump Activate Event.</span></span>

<span data-ttu-id="26363-592">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-592">**Information Fields**</span></span>

- <span data-ttu-id="26363-593">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-593">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-594">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-594">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-595">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-595">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-596">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-596">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-deactivate"></a><span data-ttu-id="26363-597">デバイス クラス DPUMP 非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-597">Device Class Dpump Deactivate</span></span> 

#### <a name="ux_device_class_dpump_deactivate"></a><span data-ttu-id="26363-598">ux_device_class_dpump_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-598">ux_device_class_dpump_deactivate</span></span>

<span data-ttu-id="26363-599">**アイコン** ![デバイス クラス DPUMP 非アクティブ化アイコン](./media/user-guide/usbx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="26363-599">**Icon** ![Device Class Dpump Deactivate icon](./media/user-guide/usbx-events/image6.png)</span></span>

<span data-ttu-id="26363-600">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-600">**Description**</span></span>

<span data-ttu-id="26363-601">USBX デバイス クラス DPUMP 非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-601">This event represents a USBX Device Class Dpump Deactivate Event.</span></span>

<span data-ttu-id="26363-602">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-602">**Information Fields**</span></span> 

- <span data-ttu-id="26363-603">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-603">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-604">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-604">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-605">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-605">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-606">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-606">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-read"></a><span data-ttu-id="26363-607">デバイス クラス DPUMP 読み取り</span><span class="sxs-lookup"><span data-stu-id="26363-607">Device Class Dpump Read</span></span> 

#### <a name="ux_device_class_dpump_read"></a><span data-ttu-id="26363-608">ux_device_class_dpump_read</span><span class="sxs-lookup"><span data-stu-id="26363-608">ux_device_class_dpump_read</span></span>

<span data-ttu-id="26363-609">**アイコン** ![デバイス クラス DPUMP 読み取りアイコン](./media/user-guide/usbx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="26363-609">**Icon** ![Device Class Dpump Read icon](./media/user-guide/usbx-events/image7.png)</span></span>

<span data-ttu-id="26363-610">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-610">**Description**</span></span>

<span data-ttu-id="26363-611">USBX デバイス クラス DPUMP 読み取りイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-611">This event represents a USBX Device Class Dpump Read Event.</span></span>

<span data-ttu-id="26363-612">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-612">**Information Fields**</span></span>

- <span data-ttu-id="26363-613">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-613">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-614">情報フィールド 2: バッファー。</span><span class="sxs-lookup"><span data-stu-id="26363-614">Info Field 2: Buffer.</span></span>
- <span data-ttu-id="26363-615">情報フィールド 3: 要求された長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-615">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="26363-616">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-616">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-write"></a><span data-ttu-id="26363-617">デバイス クラス DPUMP 書き込み</span><span class="sxs-lookup"><span data-stu-id="26363-617">Device Class Dpump Write</span></span> 

#### <a name="ux_device_class_dpump_write"></a><span data-ttu-id="26363-618">ux_device_class_dpump_write</span><span class="sxs-lookup"><span data-stu-id="26363-618">ux_device_class_dpump_write</span></span>

<span data-ttu-id="26363-619">**アイコン** ![デバイス クラス DPUMP 書き込みアイコン](./media/user-guide/usbx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="26363-619">**Icon** ![Device Class Dpump Write icon](./media/user-guide/usbx-events/image8.png)</span></span>

<span data-ttu-id="26363-620">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-620">**Description**</span></span>

<span data-ttu-id="26363-621">USBX デバイス クラス DPUMP 書き込みイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-621">This event represents a USBX Device Class Dpump Write Event.</span></span>

<span data-ttu-id="26363-622">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-622">**Information Fields**</span></span>

- <span data-ttu-id="26363-623">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-623">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-624">情報フィールド 2: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-624">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="26363-625">情報フィールド 3: 要求された長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-625">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="26363-626">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-626">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-activate"></a><span data-ttu-id="26363-627">デバイス クラス HID アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-627">Device Class Hid Activate</span></span> 

#### <a name="ux_device_class_hid_activate"></a><span data-ttu-id="26363-628">ux_device_class_hid_activate</span><span class="sxs-lookup"><span data-stu-id="26363-628">ux_device_class_hid_activate</span></span>

<span data-ttu-id="26363-629">**アイコン** ![デバイス クラス HID アクティブ化アイコン](./media/user-guide/usbx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="26363-629">**Icon** ![Device Class Hid Activate icon](./media/user-guide/usbx-events/image9.png)</span></span>

<span data-ttu-id="26363-630">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-630">**Description**</span></span>

<span data-ttu-id="26363-631">USBX デバイス クラス HID アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-631">This event represents a USBX Device Class Hid Activate Event.</span></span>

<span data-ttu-id="26363-632">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-632">**Information Fields**</span></span>

- <span data-ttu-id="26363-633">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-633">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-634">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-634">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-635">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-635">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-636">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-636">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-deactivate"></a><span data-ttu-id="26363-637">デバイス クラス HID 非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-637">Device Class Hid Deactivate</span></span> 

#### <a name="ux_device_class_hid_deactivate"></a><span data-ttu-id="26363-638">ux_device_class_hid_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-638">ux_device_class_hid_deactivate</span></span>

<span data-ttu-id="26363-639">**アイコン** ![デバイス クラス HID 非アクティブ化アイコン](./media/user-guide/usbx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="26363-639">**Icon** ![Device Class Hid Deactivate icon](./media/user-guide/usbx-events/image10.png)</span></span>

<span data-ttu-id="26363-640">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-640">**Description**</span></span>

<span data-ttu-id="26363-641">USBX デバイス クラス HID 非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-641">This event represents a USBX Device Class Hid Deactivate Event.</span></span>

<span data-ttu-id="26363-642">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-642">**Information Fields**</span></span> 

- <span data-ttu-id="26363-643">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-643">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-644">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-644">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-645">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-645">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-646">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-646">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-descriptor-send"></a><span data-ttu-id="26363-647">デバイス クラス HID 記述子送信</span><span class="sxs-lookup"><span data-stu-id="26363-647">Device Class Hid Descriptor Send</span></span> 

#### <a name="ux_device_class_hid_descritpor_send"></a><span data-ttu-id="26363-648">ux_device_class_hid_descritpor_send</span><span class="sxs-lookup"><span data-stu-id="26363-648">ux_device_class_hid_descritpor_send</span></span>

<span data-ttu-id="26363-649">**アイコン** ![デバイス クラス HID 記述子送信アイコン](./media/user-guide/usbx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="26363-649">**Icon** ![Device Class Hid Descriptor Send icon](./media/user-guide/usbx-events/image11.png)</span></span>

<span data-ttu-id="26363-650">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-650">**Description**</span></span>

<span data-ttu-id="26363-651">USBX デバイス クラス HID 記述子送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-651">This event represents a USBX Device Class Hid Descriptor Send Event.</span></span>

<span data-ttu-id="26363-652">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-652">**Information Fields**</span></span> 

- <span data-ttu-id="26363-653">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-653">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-654">情報フィールド 2: 記述子の種類。</span><span class="sxs-lookup"><span data-stu-id="26363-654">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="26363-655">情報フィールド 3: 要求のインデックス。</span><span class="sxs-lookup"><span data-stu-id="26363-655">Info Field 3: Request index.</span></span>
- <span data-ttu-id="26363-656">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-656">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-event-get"></a><span data-ttu-id="26363-657">デバイス クラス HID イベント取得</span><span class="sxs-lookup"><span data-stu-id="26363-657">Device Class Hid Event Get</span></span> 

#### <a name="ux_device_class_hid_event_get"></a><span data-ttu-id="26363-658">ux_device_class_hid_event_get</span><span class="sxs-lookup"><span data-stu-id="26363-658">ux_device_class_hid_event_get</span></span>

<span data-ttu-id="26363-659">**アイコン** ![デバイス クラス HID イベント取得アイコン](./media/user-guide/usbx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="26363-659">**Icon** ![Device Class Hid Event Get icon](./media/user-guide/usbx-events/image12.png)</span></span>

<span data-ttu-id="26363-660">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-660">**Description**</span></span>

<span data-ttu-id="26363-661">USBX デバイス クラス HID イベント取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-661">This event represents a USBX Device Class Hid Event Get Event.</span></span>

<span data-ttu-id="26363-662">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-662">**Information Fields**</span></span> 

- <span data-ttu-id="26363-663">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-663">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-664">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-664">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-665">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-665">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-666">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-666">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-event-set"></a><span data-ttu-id="26363-667">デバイス クラス HID イベント設定</span><span class="sxs-lookup"><span data-stu-id="26363-667">Device Class Hid Event Set</span></span> 

#### <a name="ux_device_class_hid_event_set"></a><span data-ttu-id="26363-668">ux_device_class_hid_event_set</span><span class="sxs-lookup"><span data-stu-id="26363-668">ux_device_class_hid_event_set</span></span>

<span data-ttu-id="26363-669">**アイコン** ![デバイス クラス HID イベント設定アイコン](./media/user-guide/usbx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="26363-669">**Icon** ![Device Class Hid Event Set icon](./media/user-guide/usbx-events/image13.png)</span></span>

<span data-ttu-id="26363-670">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-670">**Description**</span></span>

<span data-ttu-id="26363-671">USBX デバイス クラス HID イベント設定イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-671">This event represents a USBX Device Class Hid Event Set.</span></span>

<span data-ttu-id="26363-672">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-672">**Information Fields**</span></span> 

- <span data-ttu-id="26363-673">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-673">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-674">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-674">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-675">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-675">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-676">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-676">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-report-get"></a><span data-ttu-id="26363-677">デバイス クラス HID レポート取得</span><span class="sxs-lookup"><span data-stu-id="26363-677">Device Class Hid Report Get</span></span> 

#### <a name="ux_device_class_hid_report_get"></a><span data-ttu-id="26363-678">ux_device_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="26363-678">ux_device_class_hid_report_get</span></span>

<span data-ttu-id="26363-679">**アイコン** ![デバイス クラス HID レポート取得アイコン](./media/user-guide/usbx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="26363-679">**Icon** ![Device Class Hid Report Get icon](./media/user-guide/usbx-events/image14.png)</span></span>

<span data-ttu-id="26363-680">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-680">**Description**</span></span>

<span data-ttu-id="26363-681">USBX デバイス クラス HID レポート取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-681">This event represents a USBX Device Class Hid Report Get Event.</span></span>

<span data-ttu-id="26363-682">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-682">**Information Fields**</span></span>

- <span data-ttu-id="26363-683">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-683">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-684">情報フィールド 2: 記述子の種類。</span><span class="sxs-lookup"><span data-stu-id="26363-684">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="26363-685">情報フィールド 3: 要求のインデックス。</span><span class="sxs-lookup"><span data-stu-id="26363-685">Info Field 3: Request index.</span></span>
- <span data-ttu-id="26363-686">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-686">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-report-set"></a><span data-ttu-id="26363-687">デバイス クラス HID レポート設定</span><span class="sxs-lookup"><span data-stu-id="26363-687">Device Class Hid Report Set</span></span> 

#### <a name="ux_device_class_hid_report_set"></a><span data-ttu-id="26363-688">ux_device_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="26363-688">ux_device_class_hid_report_set</span></span>

<span data-ttu-id="26363-689">**アイコン** ![デバイス クラス HID レポート設定アイコン](./media/user-guide/usbx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="26363-689">**Icon** ![Device Class Hid Report Set icon](./media/user-guide/usbx-events/image15.png)</span></span>

<span data-ttu-id="26363-690">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-690">**Description**</span></span>

<span data-ttu-id="26363-691">USBX デバイス クラス HID レポート設定イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-691">This event represents a USBX Device Class Hid Report Set Event.</span></span>

<span data-ttu-id="26363-692">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-692">**Information Fields**</span></span> 

- <span data-ttu-id="26363-693">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-693">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-694">情報フィールド 2: 記述子の種類。</span><span class="sxs-lookup"><span data-stu-id="26363-694">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="26363-695">情報フィールド 3: 要求のインデックス。</span><span class="sxs-lookup"><span data-stu-id="26363-695">Info Field 3: Request index.</span></span>
- <span data-ttu-id="26363-696">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-696">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-activate"></a><span data-ttu-id="26363-697">デバイス クラス PIMA アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-697">Device Class Pima Activate</span></span>

#### <a name="ux_device_class_pima_activate"></a><span data-ttu-id="26363-698">ux_device_class_pima_activate</span><span class="sxs-lookup"><span data-stu-id="26363-698">ux_device_class_pima_activate</span></span>

<span data-ttu-id="26363-699">**アイコン** ![デバイス クラス PIMA アクティブ化アイコン](./media/user-guide/usbx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="26363-699">**Icon** ![Device Class Pima Activate icon](./media/user-guide/usbx-events/image16.png)</span></span>

<span data-ttu-id="26363-700">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-700">**Description**</span></span>

<span data-ttu-id="26363-701">USBX デバイス クラス PIMA アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-701">This event represents a USBX Device Class Pima Activate Event.</span></span>

<span data-ttu-id="26363-702">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-702">**Information Fields**</span></span>

- <span data-ttu-id="26363-703">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-703">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-704">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-704">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-705">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-705">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-706">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-706">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-deactivate"></a><span data-ttu-id="26363-707">デバイス クラス PIMA 非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-707">Device Class Pima Deactivate</span></span> 

#### <a name="ux_device_class_pima_deactivate"></a><span data-ttu-id="26363-708">ux_device_class_pima_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-708">ux_device_class_pima_deactivate</span></span>

<span data-ttu-id="26363-709">**アイコン** ![デバイス クラス PIMA 非アクティブ化アイコン](./media/user-guide/usbx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="26363-709">**Icon** ![Device Class Pima Deactivate icon](./media/user-guide/usbx-events/image17.png)</span></span>

<span data-ttu-id="26363-710">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-710">**Description**</span></span>

<span data-ttu-id="26363-711">USBX デバイス クラス PIMA 非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-711">This event represents a USBX Device Class Pima Deactivate Event.</span></span>

<span data-ttu-id="26363-712">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-712">**Information Fields**</span></span>

- <span data-ttu-id="26363-713">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-713">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-714">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-714">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-715">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-715">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-716">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-716">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-device-info-send"></a><span data-ttu-id="26363-717">デバイス クラス PIMA デバイス情報送信</span><span class="sxs-lookup"><span data-stu-id="26363-717">Device Class Pima Device Info Send</span></span> 

#### <a name="ux_device_class_pima_device_info_send"></a><span data-ttu-id="26363-718">ux_device_class_pima_device_info_send</span><span class="sxs-lookup"><span data-stu-id="26363-718">ux_device_class_pima_device_info_send</span></span>

<span data-ttu-id="26363-719">**アイコン** ![デバイス クラス PIMA デバイス情報送信アイコン](./media/user-guide/usbx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="26363-719">**Icon** ![Device Class Pima Device Info Send icon](./media/user-guide/usbx-events/image18.png)</span></span>

<span data-ttu-id="26363-720">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-720">**Description**</span></span>

<span data-ttu-id="26363-721">USBX デバイス クラス PIMA デバイス情報送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-721">This event represents a USBX Device Class Pima Device Info Send Event.</span></span>

<span data-ttu-id="26363-722">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-722">**Information Fields**</span></span>

- <span data-ttu-id="26363-723">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-723">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-724">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-724">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-725">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-725">Info Field 3: Not used.</span></span>

### <a name="device-class-pima-event-get"></a><span data-ttu-id="26363-726">デバイス クラス PIMA イベント取得</span><span class="sxs-lookup"><span data-stu-id="26363-726">Device Class Pima Event Get</span></span> 

#### <a name="ux_device_class_pima_event_get"></a><span data-ttu-id="26363-727">ux_device_class_pima_event_get</span><span class="sxs-lookup"><span data-stu-id="26363-727">ux_device_class_pima_event_get</span></span>

<span data-ttu-id="26363-728">**アイコン** ![デバイス クラス PIMA イベント取得アイコン](./media/user-guide/usbx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="26363-728">**Icon** ![Device Class Pima Event Get icon](./media/user-guide/usbx-events/image19.png)</span></span>

<span data-ttu-id="26363-729">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-729">**Description**</span></span>

<span data-ttu-id="26363-730">USBX デバイス クラス PIMA イベント取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-730">This event represents a USBX Device Class Pima Event Get Event.</span></span>

<span data-ttu-id="26363-731">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-731">**Information Fields**</span></span>

- <span data-ttu-id="26363-732">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-732">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-733">情報フィールド 2: PIMA イベント。</span><span class="sxs-lookup"><span data-stu-id="26363-733">Info Field 2: Pima event.</span></span>
- <span data-ttu-id="26363-734">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-734">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-735">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-735">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-event-set"></a><span data-ttu-id="26363-736">デバイス クラス PIMA イベント設定</span><span class="sxs-lookup"><span data-stu-id="26363-736">Device Class Pima Event Set</span></span> 

#### <a name="ux_device_class_pima_event_set"></a><span data-ttu-id="26363-737">ux_device_class_pima_event_set</span><span class="sxs-lookup"><span data-stu-id="26363-737">ux_device_class_pima_event_set</span></span>

<span data-ttu-id="26363-738">**アイコン** ![デバイス クラス PIMA イベント設定アイコン](./media/user-guide/usbx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="26363-738">**Icon** ![Device Class Pima Event Set icon](./media/user-guide/usbx-events/image20.png)</span></span>

<span data-ttu-id="26363-739">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-739">**Description**</span></span>

<span data-ttu-id="26363-740">USBX デバイス クラス PIMA イベント設定イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-740">This event represents a USBX Device Class Pima Event Set Event.</span></span>

<span data-ttu-id="26363-741">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-741">**Information Fields**</span></span>

- <span data-ttu-id="26363-742">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-742">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-743">情報フィールド 2: PIMA イベント。</span><span class="sxs-lookup"><span data-stu-id="26363-743">Info Field 2: Pima event.</span></span>
- <span data-ttu-id="26363-744">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-744">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-745">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-745">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-add"></a><span data-ttu-id="26363-746">デバイス クラス PIMA オブジェクト追加</span><span class="sxs-lookup"><span data-stu-id="26363-746">Device Class Pima Object Add</span></span> 

#### <a name="ux_device_class_pima_object_add"></a><span data-ttu-id="26363-747">ux_device_class_pima_object_add</span><span class="sxs-lookup"><span data-stu-id="26363-747">ux_device_class_pima_object_add</span></span>

<span data-ttu-id="26363-748">**アイコン** ![デバイス クラス PIMA オブジェクト追加アイコン](./media/user-guide/usbx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="26363-748">**Icon** ![Device Class Pima Object Add icon](./media/user-guide/usbx-events/image21.png)</span></span>

<span data-ttu-id="26363-749">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-749">**Description**</span></span>

<span data-ttu-id="26363-750">USBX デバイス クラス PIMA オブジェクト追加イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-750">This event represents a USBX Device Class Pima Object Add Event.</span></span>

<span data-ttu-id="26363-751">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-751">**Information Fields**</span></span> 

- <span data-ttu-id="26363-752">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-752">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-753">情報フィールド 2: オブジェクトのハンドル。</span><span class="sxs-lookup"><span data-stu-id="26363-753">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="26363-754">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-754">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-755">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-755">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-data-get"></a><span data-ttu-id="26363-756">デバイス クラス PIMA オブジェクト データ取得</span><span class="sxs-lookup"><span data-stu-id="26363-756">Device Class Pima Object Data Get</span></span> 

#### <a name="ux_device_class_pima_object_data_get"></a><span data-ttu-id="26363-757">ux_device_class_pima_object_data_get</span><span class="sxs-lookup"><span data-stu-id="26363-757">ux_device_class_pima_object_data_get</span></span>

<span data-ttu-id="26363-758">**アイコン** ![デバイス クラス PIMA オブジェクト データ取得アイコン](./media/user-guide/usbx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="26363-758">**Icon** ![Device Class Pima Object Data Get icon](./media/user-guide/usbx-events/image22.png)</span></span>

<span data-ttu-id="26363-759">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-759">**Description**</span></span>

<span data-ttu-id="26363-760">USBX デバイス クラス PIMA オブジェクト データ取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-760">This event represents a USBX Device Class Pima Object Data Get Event.</span></span>

<span data-ttu-id="26363-761">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-761">**Information Fields**</span></span> 

- <span data-ttu-id="26363-762">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-762">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-763">情報フィールド 2: オブジェクトのハンドル。</span><span class="sxs-lookup"><span data-stu-id="26363-763">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="26363-764">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-764">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-765">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-765">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-data-send"></a><span data-ttu-id="26363-766">デバイス クラス PIMA オブジェクト データ送信</span><span class="sxs-lookup"><span data-stu-id="26363-766">Device Class Pima Object Data Send</span></span> 

#### <a name="ux_device_class_pima_object_data_send"></a><span data-ttu-id="26363-767">ux_device_class_pima_object_data_send</span><span class="sxs-lookup"><span data-stu-id="26363-767">ux_device_class_pima_object_data_send</span></span>

<span data-ttu-id="26363-768">**アイコン** ![デバイス クラス PIMA オブジェクト データ送信アイコン](./media/user-guide/usbx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="26363-768">**Icon** ![Device Class Pima Object Data Send icon](./media/user-guide/usbx-events/image23.png)</span></span>

<span data-ttu-id="26363-769">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-769">**Description**</span></span>

<span data-ttu-id="26363-770">USBX デバイス クラス PIMA オブジェクト データ送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-770">This event represents a USBX Device Class Pima Object Data Send Event.</span></span>

<span data-ttu-id="26363-771">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-771">**Information Fields**</span></span> 

- <span data-ttu-id="26363-772">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-772">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-773">情報フィールド 2: オブジェクトのハンドル。</span><span class="sxs-lookup"><span data-stu-id="26363-773">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="26363-774">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-774">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-775">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-775">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-delete"></a><span data-ttu-id="26363-776">デバイス クラス PIMA オブジェクト削除</span><span class="sxs-lookup"><span data-stu-id="26363-776">Device Class Pima Object Delete</span></span> 

#### <a name="ux_device_class_pima_object_delete"></a><span data-ttu-id="26363-777">ux_device_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="26363-777">ux_device_class_pima_object_delete</span></span>

<span data-ttu-id="26363-778">**アイコン** ![デバイス クラス PIMA オブジェクト削除アイコン](./media/user-guide/usbx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="26363-778">**Icon** ![Device Class Pima Object Delete icon](./media/user-guide/usbx-events/image24.png)</span></span>

<span data-ttu-id="26363-779">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-779">**Description**</span></span>

<span data-ttu-id="26363-780">USBX デバイス クラス PIMA オブジェクト データ削除イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-780">This event represents a USBX Device Class Pima Object Delete Event.</span></span>

<span data-ttu-id="26363-781">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-781">**Information Fields**</span></span> 

- <span data-ttu-id="26363-782">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-782">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-783">情報フィールド 2: オブジェクトのハンドル。</span><span class="sxs-lookup"><span data-stu-id="26363-783">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="26363-784">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-784">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-785">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-785">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-handles-send"></a><span data-ttu-id="26363-786">デバイス クラス PIMA オブジェクト ハンドル送信</span><span class="sxs-lookup"><span data-stu-id="26363-786">Device Class Pima Object Handles Send</span></span> 

#### <a name="ux_device_class_pima_object_handles_send"></a><span data-ttu-id="26363-787">ux_device_class_pima_object_handles_send</span><span class="sxs-lookup"><span data-stu-id="26363-787">ux_device_class_pima_object_handles_send</span></span>

<span data-ttu-id="26363-788">**アイコン** ![デバイス クラス PIMA オブジェクト ハンドル送信アイコン](./media/user-guide/usbx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="26363-788">**Icon** ![Device Class Pima Object Handles Send icon](./media/user-guide/usbx-events/image25.png)</span></span>

<span data-ttu-id="26363-789">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-789">**Description**</span></span>

<span data-ttu-id="26363-790">USBX デバイス クラス PIMA オブジェクト ハンドル送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-790">This event represents a USBX Device Class Pima Object Handles Send Event.</span></span>

<span data-ttu-id="26363-791">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-791">**Information Fields**</span></span>

- <span data-ttu-id="26363-792">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-792">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-793">情報フィールド 2: ストレージ ID。</span><span class="sxs-lookup"><span data-stu-id="26363-793">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="26363-794">情報フィールド 3: オブジェクトのフォーマットのコード。</span><span class="sxs-lookup"><span data-stu-id="26363-794">Info Field 3: Object format code.</span></span>
- <span data-ttu-id="26363-795">情報フィールド 4: オブジェクトの関連付け。</span><span class="sxs-lookup"><span data-stu-id="26363-795">Info Field 4: Object association.</span></span>

### <a name="device-class-pima-object-info-get"></a><span data-ttu-id="26363-796">デバイス クラス PIMA オブジェクト情報取得</span><span class="sxs-lookup"><span data-stu-id="26363-796">Device Class Pima Object Info Get</span></span> 

#### <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="26363-797">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="26363-797">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="26363-798">**アイコン** ![デバイス クラス PIMA オブジェクト情報取得アイコン](./media/user-guide/usbx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="26363-798">**Icon** ![Device Class Pima Object Info Get icon](./media/user-guide/usbx-events/image26.png)</span></span>

<span data-ttu-id="26363-799">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-799">**Description**</span></span>

<span data-ttu-id="26363-800">USBX デバイス クラス PIMA オブジェクト情報取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-800">This event represents a USBX Device Class Pima Object Info Get Event.</span></span>

<span data-ttu-id="26363-801">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-801">**Information Fields**</span></span>

- <span data-ttu-id="26363-802">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-802">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-803">情報フィールド 2: オブジェクトのハンドル。</span><span class="sxs-lookup"><span data-stu-id="26363-803">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="26363-804">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-804">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-805">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-805">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-info-send"></a><span data-ttu-id="26363-806">デバイス クラス PIMA オブジェクト情報送信</span><span class="sxs-lookup"><span data-stu-id="26363-806">Device Class Pima Object Info Send</span></span> 

#### <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="26363-807">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="26363-807">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="26363-808">**アイコン** ![デバイス クラス PIMA オブジェクト情報送信アイコン](./media/user-guide/usbx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="26363-808">**Icon** ![Device Class Pima Object Info Send icon](./media/user-guide/usbx-events/image27.png)</span></span>

<span data-ttu-id="26363-809">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-809">**Description**</span></span>

<span data-ttu-id="26363-810">USBX デバイス クラス PIMA オブジェクト情報送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-810">This event represents a USBX Device Class Pima Object Info Send Event.</span></span>

<span data-ttu-id="26363-811">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-811">**Information Fields**</span></span>

- <span data-ttu-id="26363-812">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-812">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-813">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-813">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-814">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-814">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-815">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-815">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-objects-number-send"></a><span data-ttu-id="26363-816">デバイス クラス PIMA オブジェクト数送信</span><span class="sxs-lookup"><span data-stu-id="26363-816">Device Class Pima Objects Number Send</span></span> 

#### <a name="ux_device_class_pima_object_number_send"></a><span data-ttu-id="26363-817">ux_device_class_pima_object_number_send</span><span class="sxs-lookup"><span data-stu-id="26363-817">ux_device_class_pima_object_number_send</span></span>

<span data-ttu-id="26363-818">**アイコン** ![デバイス クラス PIMA オブジェクト数送信アイコン](./media/user-guide/usbx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="26363-818">**Icon** ![Device Class Pima Objects Number Send icon](./media/user-guide/usbx-events/image28.png)</span></span>

<span data-ttu-id="26363-819">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-819">**Description**</span></span>

<span data-ttu-id="26363-820">USBX デバイス クラス PIMA オブジェクト数送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-820">This event represents a USBX Device Class Pima Object Number Send event.</span></span>

<span data-ttu-id="26363-821">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-821">**Information Fields**</span></span>

- <span data-ttu-id="26363-822">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-822">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-823">情報フィールド 2: ストレージ ID。</span><span class="sxs-lookup"><span data-stu-id="26363-823">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="26363-824">情報フィールド 3: オブジェクトのフォーマットのコード。</span><span class="sxs-lookup"><span data-stu-id="26363-824">Info Field 3: Object format code.</span></span>
- <span data-ttu-id="26363-825">情報フィールド 4: オブジェクトの関連付け。</span><span class="sxs-lookup"><span data-stu-id="26363-825">Info Field 4: Object associate.</span></span>

### <a name="device-class-pima-partial-object-data-get"></a><span data-ttu-id="26363-826">デバイス クラス PIMA オブジェクト データ一部取得</span><span class="sxs-lookup"><span data-stu-id="26363-826">Device Class Pima Partial Object Data Get</span></span>

#### <a name="ux_device_class_pima_partial_object_data_get"></a><span data-ttu-id="26363-827">ux_device_class_pima_partial_object_data_get</span><span class="sxs-lookup"><span data-stu-id="26363-827">ux_device_class_pima_partial_object_data_get</span></span>

<span data-ttu-id="26363-828">**アイコン** ![デバイス クラス PIMA オブジェクト データ一部取得アイコン](./media/user-guide/usbx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="26363-828">**Icon** ![Device Class Pima Partial Object Data Get icon](./media/user-guide/usbx-events/image29.png)</span></span>

<span data-ttu-id="26363-829">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-829">**Description**</span></span>

<span data-ttu-id="26363-830">USBX デバイス クラス PIMA オブジェクト データ一部取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-830">This event represents a USBX Device Class Pima Partial Object Data Get Event.</span></span>

<span data-ttu-id="26363-831">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-831">**Information Fields**</span></span>

- <span data-ttu-id="26363-832">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-832">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-833">情報フィールド 2: オブジェクトのハンドル。</span><span class="sxs-lookup"><span data-stu-id="26363-833">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="26363-834">情報フィールド 3: 要求されたオフセット。</span><span class="sxs-lookup"><span data-stu-id="26363-834">Info Field 3: Offset requested.</span></span>
- <span data-ttu-id="26363-835">情報フィールド 4: 要求された長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-835">Info Field 4: Length requested.</span></span>

### <a name="device-class-pima-response-send"></a><span data-ttu-id="26363-836">デバイス クラス PIMA 応答送信</span><span class="sxs-lookup"><span data-stu-id="26363-836">Device Class Pima Response Send</span></span> 

#### <a name="ux_device_class_pima_response_send"></a><span data-ttu-id="26363-837">ux_device_class_pima_response_send</span><span class="sxs-lookup"><span data-stu-id="26363-837">ux_device_class_pima_response_send</span></span>

<span data-ttu-id="26363-838">**アイコン** ![デバイス クラス PIMA 応答送信アイコン](./media/user-guide/usbx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="26363-838">**Icon** ![Device Class Pima Response Send icon](./media/user-guide/usbx-events/image30.png)</span></span>

<span data-ttu-id="26363-839">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-839">**Description**</span></span>

<span data-ttu-id="26363-840">USBX デバイス クラス PIMA 応答送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-840">This event represents a USBX Device Class Pima Response Send Event.</span></span>

<span data-ttu-id="26363-841">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-841">**Information Fields**</span></span>

- <span data-ttu-id="26363-842">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-842">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-843">情報フィールド 2: 応答コード。</span><span class="sxs-lookup"><span data-stu-id="26363-843">Info Field 2: Response code.</span></span>
- <span data-ttu-id="26363-844">情報フィールド 3: 番号パラメーター。</span><span class="sxs-lookup"><span data-stu-id="26363-844">Info Field 3: Number parameter.</span></span>
- <span data-ttu-id="26363-845">情報フィールド 4: PIMA パラメーター 1。</span><span class="sxs-lookup"><span data-stu-id="26363-845">Info Field 4: Pima parameter 1.</span></span>

### <a name="device-class-pima-storage-id-send"></a><span data-ttu-id="26363-846">デバイス クラス PIMA ストレージ ID 送信</span><span class="sxs-lookup"><span data-stu-id="26363-846">Device Class Pima Storage Id Send</span></span> 

#### <a name="ux_device_class_pima_storage_id_send"></a><span data-ttu-id="26363-847">ux_device_class_pima_storage_id_send</span><span class="sxs-lookup"><span data-stu-id="26363-847">ux_device_class_pima_storage_id_send</span></span>

<span data-ttu-id="26363-848">**アイコン** ![デバイス クラス PIMA ストレージ ID 送信アイコン](./media/user-guide/usbx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="26363-848">**Icon** ![Device Class Pima Storage Id Send icon](./media/user-guide/usbx-events/image31.png)</span></span>

<span data-ttu-id="26363-849">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-849">**Description**</span></span>

<span data-ttu-id="26363-850">USBX デバイス クラス PIMA ストレージ ID 送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-850">This event represents a USBX Device Class Pima Storage Id Send Event.</span></span>

<span data-ttu-id="26363-851">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-851">**Information Fields**</span></span> 

- <span data-ttu-id="26363-852">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-852">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-853">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-853">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-854">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-854">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-855">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-855">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-storage-info-send"></a><span data-ttu-id="26363-856">デバイス クラス PIMA ストレージ情報送信</span><span class="sxs-lookup"><span data-stu-id="26363-856">Device Class Pima Storage Info Send</span></span> 

#### <a name="ux_device_class_pima_storage_info_send"></a><span data-ttu-id="26363-857">ux_device_class_pima_storage_info_send</span><span class="sxs-lookup"><span data-stu-id="26363-857">ux_device_class_pima_storage_info_send</span></span>

<span data-ttu-id="26363-858">**アイコン** ![デバイス クラス PIMA ストレージ情報送信アイコン](./media/user-guide/usbx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="26363-858">**Icon** ![Device Class Pima Storage Info Send icon](./media/user-guide/usbx-events/image32.png)</span></span>

<span data-ttu-id="26363-859">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-859">**Description**</span></span>

<span data-ttu-id="26363-860">USBX デバイス クラス PIMA ストレージ情報送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-860">This event represents a USBX Device Class Pima Storage Info Send Event.</span></span>

<span data-ttu-id="26363-861">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-861">**Information Fields**</span></span> 

- <span data-ttu-id="26363-862">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-862">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-863">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-863">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-864">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-864">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-865">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-865">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-activate"></a><span data-ttu-id="26363-866">デバイス クラス RNDIS アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-866">Device Class Rndis Activate</span></span> 

#### <a name="ux_device_class_rndis_activate"></a><span data-ttu-id="26363-867">ux_device_class_rndis_activate</span><span class="sxs-lookup"><span data-stu-id="26363-867">ux_device_class_rndis_activate</span></span>

<span data-ttu-id="26363-868">**アイコン** ![デバイス クラス RNDIS アクティブ化アイコン](./media/user-guide/usbx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="26363-868">**Icon** ![Device Class Rndis Activate icon](./media/user-guide/usbx-events/image33.png)</span></span>

<span data-ttu-id="26363-869">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-869">**Description**</span></span>

<span data-ttu-id="26363-870">USBX デバイス クラス RNDIS アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-870">This event represents a USBX Device Class Rndis Activate Event.</span></span>

<span data-ttu-id="26363-871">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-871">**Information Fields**</span></span> 

- <span data-ttu-id="26363-872">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-872">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-873">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-873">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-874">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-874">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-875">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-875">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-deactivate"></a><span data-ttu-id="26363-876">デバイス クラス RNDIS 非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-876">Device Class Rndis Deactivate</span></span> 

#### <a name="ux_device_class_rndis_deactivate"></a><span data-ttu-id="26363-877">ux_device_class_rndis_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-877">ux_device_class_rndis_deactivate</span></span>

<span data-ttu-id="26363-878">**アイコン** ![デバイス クラス RNDIS 非アクティブ化アイコン](./media/user-guide/usbx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="26363-878">**Icon** ![Device Class Rndis Deactivate icon](./media/user-guide/usbx-events/image34.png)</span></span>

<span data-ttu-id="26363-879">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-879">**Description**</span></span>

<span data-ttu-id="26363-880">USBX デバイス クラス RNDIS 非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-880">This event represents a USBX Device Class Rndis Deactivate Event.</span></span>

<span data-ttu-id="26363-881">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-881">**Information Fields**</span></span> 

- <span data-ttu-id="26363-882">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-882">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-883">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-883">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-884">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-884">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-885">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-885">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-keep-alive"></a><span data-ttu-id="26363-886">デバイス クラス RNDIS キープ アライブ メッセージ送信</span><span class="sxs-lookup"><span data-stu-id="26363-886">Device Class Rndis Message Keep Alive</span></span> 

#### <a name="ux_device_class_rndis_msg_keep_alive"></a><span data-ttu-id="26363-887">ux_device_class_rndis_msg_keep_alive</span><span class="sxs-lookup"><span data-stu-id="26363-887">ux_device_class_rndis_msg_keep_alive</span></span>

<span data-ttu-id="26363-888">**アイコン** ![デバイス クラス RNDIS キープ アライブ メッセージ送信アイコン](./media/user-guide/usbx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="26363-888">**Icon** ![Device Class Rndis Message Keep Alive icon](./media/user-guide/usbx-events/image35.png)</span></span>

<span data-ttu-id="26363-889">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-889">**Description**</span></span>

<span data-ttu-id="26363-890">USBX デバイス クラス RNDIS キープ アライブ メッセージ送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-890">This event represents a USBX Device Class Rndis Message Keep Alive Event.</span></span>

<span data-ttu-id="26363-891">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-891">**Information Fields**</span></span> 

- <span data-ttu-id="26363-892">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-892">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-893">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-893">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-894">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-894">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-895">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-895">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-query"></a><span data-ttu-id="26363-896">デバイス クラス RNDIS クエリ メッセージ送信</span><span class="sxs-lookup"><span data-stu-id="26363-896">Device Class Rndis Message Query</span></span> 

#### <a name="ux_device_class_rndis_msg_keep_query"></a><span data-ttu-id="26363-897">ux_device_class_rndis_msg_keep_query</span><span class="sxs-lookup"><span data-stu-id="26363-897">ux_device_class_rndis_msg_keep_query</span></span>

<span data-ttu-id="26363-898">**アイコン** ![デバイス クラス RNDIS クエリ メッセージ送信アイコン](./media/user-guide/usbx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="26363-898">**Icon** ![Device Class Rndis Message Query icon](./media/user-guide/usbx-events/image36.png)</span></span>

<span data-ttu-id="26363-899">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-899">**Description**</span></span>

<span data-ttu-id="26363-900">USBX デバイス クラス RNDIS クエリ メッセージ送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-900">This event represents a USBX Device Class Rndis Message Query Event.</span></span>

<span data-ttu-id="26363-901">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-901">**Information Fields**</span></span> 

- <span data-ttu-id="26363-902">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-902">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-903">情報フィールド 2: RNDIS OID。</span><span class="sxs-lookup"><span data-stu-id="26363-903">Info Field 2: Rndis OID.</span></span>
- <span data-ttu-id="26363-904">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-904">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-905">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-905">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-reset"></a><span data-ttu-id="26363-906">デバイス クラス RNDIS リセット メッセージ送信</span><span class="sxs-lookup"><span data-stu-id="26363-906">Device Class Rndis Message Reset</span></span> 

#### <a name="ux_device_class_rndis_msg_reset"></a><span data-ttu-id="26363-907">ux_device_class_rndis_msg_reset</span><span class="sxs-lookup"><span data-stu-id="26363-907">ux_device_class_rndis_msg_reset</span></span>

<span data-ttu-id="26363-908">**アイコン** ![デバイス クラス RNDIS リセット メッセージ送信アイコン](./media/user-guide/usbx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="26363-908">**Icon** ![Device Class Rndis Message Reset icon](./media/user-guide/usbx-events/image37.png)</span></span>

<span data-ttu-id="26363-909">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-909">**Description**</span></span>

<span data-ttu-id="26363-910">USBX デバイス クラス RNDIS リセット メッセージ送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-910">This event represents a USBX Device Class Rndis Message Reset Event.</span></span>

<span data-ttu-id="26363-911">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-911">**Information Fields**</span></span> 

- <span data-ttu-id="26363-912">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-912">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-913">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-913">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-914">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-914">Info Field 3: Not used.</span></span>

### <a name="device-class-rndis-message-set"></a><span data-ttu-id="26363-915">デバイス クラス RNDIS 設定メッセージ送信</span><span class="sxs-lookup"><span data-stu-id="26363-915">Device Class Rndis Message Set</span></span> 

#### <a name="ux_device_class_rndis_msg_set"></a><span data-ttu-id="26363-916">ux_device_class_rndis_msg_set</span><span class="sxs-lookup"><span data-stu-id="26363-916">ux_device_class_rndis_msg_set</span></span>

<span data-ttu-id="26363-917">**アイコン** ![デバイス クラス RNDIS 設定メッセージ送信アイコン](./media/user-guide/usbx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="26363-917">**Icon** ![Device Class Rndis Message Set icon](./media/user-guide/usbx-events/image38.png)</span></span>

<span data-ttu-id="26363-918">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-918">**Description**</span></span>

<span data-ttu-id="26363-919">USBX デバイス クラス RNDIS 設定メッセージ送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-919">This event represents a USBX Device Class Rndis Message Set Event.</span></span>

<span data-ttu-id="26363-920">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-920">**Information Fields**</span></span>

- <span data-ttu-id="26363-921">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-921">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-922">情報フィールド 2: RNDIS OID。</span><span class="sxs-lookup"><span data-stu-id="26363-922">Info Field 2: Rndis OID.</span></span>
- <span data-ttu-id="26363-923">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-923">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-924">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-924">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-packet-receive"></a><span data-ttu-id="26363-925">デバイス クラス RNDIS パケット受信</span><span class="sxs-lookup"><span data-stu-id="26363-925">Device Class Rndis Packet Receive</span></span> 

#### <a name="ux_device_class_rndis_packet_receive"></a><span data-ttu-id="26363-926">ux_device_class_rndis_packet_receive</span><span class="sxs-lookup"><span data-stu-id="26363-926">ux_device_class_rndis_packet_receive</span></span>

<span data-ttu-id="26363-927">**アイコン** ![デバイス クラス RNDIS パケット受信アイコン](./media/user-guide/usbx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="26363-927">**Icon** ![Device Class Rndis Packet Receive icon](./media/user-guide/usbx-events/image39.png)</span></span>

<span data-ttu-id="26363-928">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-928">**Description**</span></span>

<span data-ttu-id="26363-929">USBX デバイス クラス RNDIS パケット受信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-929">This event represents a USBX Device Class Rndis Packet Receive Event.</span></span>

<span data-ttu-id="26363-930">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-930">**Information Fields**</span></span>

- <span data-ttu-id="26363-931">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-931">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-932">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-932">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-933">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-933">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-934">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-934">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-packet-transmit"></a><span data-ttu-id="26363-935">デバイス クラス RNDIS パケット送信</span><span class="sxs-lookup"><span data-stu-id="26363-935">Device Class Rndis Packet Transmit</span></span> 

#### <a name="ux_device_class_rndis_packet_transmit"></a><span data-ttu-id="26363-936">ux_device_class_rndis_packet_transmit</span><span class="sxs-lookup"><span data-stu-id="26363-936">ux_device_class_rndis_packet_transmit</span></span>

<span data-ttu-id="26363-937">**アイコン** ![デバイス クラス RNDIS パケット送信アイコン](./media/user-guide/usbx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="26363-937">**Icon** ![Device Class Rndis Packet Transmit icon](./media/user-guide/usbx-events/image40.png)</span></span>

<span data-ttu-id="26363-938">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-938">**Description**</span></span>

<span data-ttu-id="26363-939">USBX デバイス クラス RNDIS パケット送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-939">This event represents a USBX Device Class Rndis Packet Transmit Event.</span></span>

<span data-ttu-id="26363-940">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-940">**Information Fields**</span></span> 

- <span data-ttu-id="26363-941">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-941">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-942">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-942">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-943">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-943">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-944">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-944">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-activate"></a><span data-ttu-id="26363-945">デバイス クラス Storage アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-945">Device Class Storage Activate</span></span> 

#### <a name="ux_device_class_storage_activate"></a><span data-ttu-id="26363-946">ux_device_class_storage_activate</span><span class="sxs-lookup"><span data-stu-id="26363-946">ux_device_class_storage_activate</span></span>

<span data-ttu-id="26363-947">**アイコン** ![デバイス クラス Storage アクティブ化アイコン](./media/user-guide/usbx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="26363-947">**Icon** ![Device Class Storage Activate icon](./media/user-guide/usbx-events/image41.png)</span></span>

<span data-ttu-id="26363-948">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-948">**Description**</span></span>

<span data-ttu-id="26363-949">USBX デバイス クラス Storage アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-949">This event represents a USBX Device Class Storage Activate Event.</span></span>

<span data-ttu-id="26363-950">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-950">**Information Fields**</span></span>

- <span data-ttu-id="26363-951">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-951">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-952">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-952">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-953">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-953">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-954">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-954">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-deactivate"></a><span data-ttu-id="26363-955">デバイス クラス Storage 非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-955">Device Class Storage Deactivate</span></span> 

#### <a name="ux_device_class_storage_deactivate"></a><span data-ttu-id="26363-956">ux_device_class_storage_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-956">ux_device_class_storage_deactivate</span></span>

<span data-ttu-id="26363-957">**アイコン** ![デバイス クラス Storage 非アクティブ化アイコン](./media/user-guide/usbx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="26363-957">**Icon** ![Device Class Storage Deactivate icon](./media/user-guide/usbx-events/image42.png)</span></span>

<span data-ttu-id="26363-958">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-958">**Description**</span></span>

<span data-ttu-id="26363-959">USBX デバイス クラス Storage 非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-959">This event represents a USBX Device Class Storage Deactivate Event.</span></span>

<span data-ttu-id="26363-960">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-960">**Information Fields**</span></span>

- <span data-ttu-id="26363-961">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-961">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-962">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-962">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-963">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-963">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-964">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-964">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-format"></a><span data-ttu-id="26363-965">デバイス クラス Storage フォーマット</span><span class="sxs-lookup"><span data-stu-id="26363-965">Device Class Storage Format</span></span> 

#### <a name="ux_device_class_storage_format"></a><span data-ttu-id="26363-966">ux_device_class_storage_format</span><span class="sxs-lookup"><span data-stu-id="26363-966">ux_device_class_storage_format</span></span>

<span data-ttu-id="26363-967">**アイコン** ![デバイス クラス Storage フォーマット アイコン](./media/user-guide/usbx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="26363-967">**Icon** ![Device Class Storage Format icon](./media/user-guide/usbx-events/image43.png)</span></span>

<span data-ttu-id="26363-968">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-968">**Description**</span></span>

<span data-ttu-id="26363-969">USBX デバイス クラス Storage フォーマット イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-969">This event represents a USBX Device Class Storage Format Event.</span></span>

<span data-ttu-id="26363-970">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-970">**Information Fields**</span></span> 

- <span data-ttu-id="26363-971">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-971">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-972">情報フィールド 2: Lun。</span><span class="sxs-lookup"><span data-stu-id="26363-972">Info Field 2: Lun.</span></span>
- <span data-ttu-id="26363-973">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-973">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-974">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-974">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-inquiry"></a><span data-ttu-id="26363-975">デバイス クラス Storage 照会</span><span class="sxs-lookup"><span data-stu-id="26363-975">Device Class Storage Inquiry</span></span> 

#### <a name="ux_device_class_storage_inquiry"></a><span data-ttu-id="26363-976">ux_device_class_storage_inquiry</span><span class="sxs-lookup"><span data-stu-id="26363-976">ux_device_class_storage_inquiry</span></span>

<span data-ttu-id="26363-977">**アイコン** ![デバイス クラス Storage 照会アイコン](./media/user-guide/usbx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="26363-977">**Icon** ![Device Class Storage Inquiry icon](./media/user-guide/usbx-events/image44.png)</span></span>

<span data-ttu-id="26363-978">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-978">**Description**</span></span>

<span data-ttu-id="26363-979">USBX デバイス クラス Storage 照会イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-979">This event represents a USBX Device Class Storage Inquiry Event.</span></span>

<span data-ttu-id="26363-980">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-980">**Information Fields**</span></span>

- <span data-ttu-id="26363-981">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-981">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-982">情報フィールド 2: Lun。</span><span class="sxs-lookup"><span data-stu-id="26363-982">Info Field 2: Lun.</span></span>
- <span data-ttu-id="26363-983">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-983">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-984">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-984">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-mode-select"></a><span data-ttu-id="26363-985">デバイス クラス Storage モード選択</span><span class="sxs-lookup"><span data-stu-id="26363-985">Device Class Storage Mode Select</span></span>

#### <a name="ux_device_class_storage_mode_select"></a><span data-ttu-id="26363-986">ux_device_class_storage_mode_select</span><span class="sxs-lookup"><span data-stu-id="26363-986">ux_device_class_storage_mode_select</span></span>

<span data-ttu-id="26363-987">**アイコン** ![デバイス クラス Storage モード選択アイコン](./media/user-guide/usbx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="26363-987">**Icon** ![Device Class Storage Mode Select icon](./media/user-guide/usbx-events/image45.png)</span></span>

<span data-ttu-id="26363-988">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-988">**Description**</span></span>

<span data-ttu-id="26363-989">USBX デバイス クラス Storage モード選択イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-989">This event represents a USBX Device Class Storage Mode Select Event.</span></span>

<span data-ttu-id="26363-990">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-990">**Information Fields**</span></span> 

- <span data-ttu-id="26363-991">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-991">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-992">情報フィールド 2: Lun。</span><span class="sxs-lookup"><span data-stu-id="26363-992">Info Field 2: Lun.</span></span>
- <span data-ttu-id="26363-993">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-993">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-994">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-994">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-mode-sense"></a><span data-ttu-id="26363-995">デバイス クラス Storage モード センス</span><span class="sxs-lookup"><span data-stu-id="26363-995">Device Class Storage Mode Sense</span></span> 

#### <a name="ux_device_class_storage_mode_sense"></a><span data-ttu-id="26363-996">ux_device_class_storage_mode_sense</span><span class="sxs-lookup"><span data-stu-id="26363-996">ux_device_class_storage_mode_sense</span></span>

<span data-ttu-id="26363-997">**アイコン](./media/user-guide/usbx-events/image46.png)** デバイス クラス Storage モード センス アイコン![</span><span class="sxs-lookup"><span data-stu-id="26363-997">**Icon** ![Device Class Storage Mode Sense icon](./media/user-guide/usbx-events/image46.png)</span></span>

<span data-ttu-id="26363-998">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-998">**Description**</span></span>

<span data-ttu-id="26363-999">USBX デバイス クラス Storage モード センス イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-999">This event represents a USBX Device Class Storage Mode Sense Event.</span></span>

<span data-ttu-id="26363-1000">情報フィールド</span><span class="sxs-lookup"><span data-stu-id="26363-1000">Information Fields</span></span> 

- <span data-ttu-id="26363-1001">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1001">nfo Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-1002">情報フィールド 2: Lun。</span><span class="sxs-lookup"><span data-stu-id="26363-1002">Info Field 2: Lun.</span></span>
- <span data-ttu-id="26363-1003">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1003">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1004">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1004">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-prevent-allow-media-removal"></a><span data-ttu-id="26363-1005">デバイス クラス Storage メディア取り外し禁止/許可</span><span class="sxs-lookup"><span data-stu-id="26363-1005">Device Class Storage Prevent Allow Media Removal</span></span> 

#### <a name="ux_device_class_storage_prevent_allow_media_removal"></a><span data-ttu-id="26363-1006">ux_device_class_storage_prevent_allow_media_removal</span><span class="sxs-lookup"><span data-stu-id="26363-1006">ux_device_class_storage_prevent_allow_media_removal</span></span>

<span data-ttu-id="26363-1007">**アイコン** ![デバイス クラス Storage メディア取り外し禁止/許可アイコン](./media/user-guide/usbx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1007">**Icon** ![Device Class Storage Prevent Allow Media Removal icon](./media/user-guide/usbx-events/image47.png)</span></span>

<span data-ttu-id="26363-1008">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1008">**Description**</span></span>

<span data-ttu-id="26363-1009">USBX デバイス クラス Storage メディア取り外し禁止/許可イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1009">This event represents a USBX Device Class Storage Prevent Allow Media Removal Event.</span></span>

<span data-ttu-id="26363-1010">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1010">**Information Fields**</span></span>

- <span data-ttu-id="26363-1011">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1011">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-1012">情報フィールド 2: Lun。</span><span class="sxs-lookup"><span data-stu-id="26363-1012">Info Field 2: Lun.</span></span>
- <span data-ttu-id="26363-1013">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1013">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1014">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1014">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read"></a><span data-ttu-id="26363-1015">デバイス クラス Storage 読み取り</span><span class="sxs-lookup"><span data-stu-id="26363-1015">Device Class Storage Read</span></span> 

#### <a name="ux_device_class_storage_read"></a><span data-ttu-id="26363-1016">ux_device_class_storage_read</span><span class="sxs-lookup"><span data-stu-id="26363-1016">ux_device_class_storage_read</span></span>

<span data-ttu-id="26363-1017">**アイコン** ![デバイス クラス Storage 読み取りアイコン](./media/user-guide/usbx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1017">**Icon** ![Device Class Storage Read icon](./media/user-guide/usbx-events/image48.png)</span></span>

<span data-ttu-id="26363-1018">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1018">**Description**</span></span>

<span data-ttu-id="26363-1019">USBX デバイス クラス Storage 読み取りイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1019">This event represents a USBX Device Class Storage Read Event.</span></span>

<span data-ttu-id="26363-1020">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1020">**Information Fields**</span></span>

- <span data-ttu-id="26363-1021">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1021">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-1022">情報フィールド 2: Lun。</span><span class="sxs-lookup"><span data-stu-id="26363-1022">Info Field 2: Lun.</span></span>
- <span data-ttu-id="26363-1023">情報フィールド 3: セクター。</span><span class="sxs-lookup"><span data-stu-id="26363-1023">Info Field 3: Sector.</span></span>
- <span data-ttu-id="26363-1024">情報フィールド 4: セクター数。</span><span class="sxs-lookup"><span data-stu-id="26363-1024">Info Field 4: Number sectors.</span></span>

### <a name="device-class-storage-read-capacity"></a><span data-ttu-id="26363-1025">デバイス クラス Storage 容量読み取り</span><span class="sxs-lookup"><span data-stu-id="26363-1025">Device Class Storage Read Capacity</span></span> 

#### <a name="ux_device_class_storage_read_capacity"></a><span data-ttu-id="26363-1026">ux_device_class_storage_read_capacity</span><span class="sxs-lookup"><span data-stu-id="26363-1026">ux_device_class_storage_read_capacity</span></span>

<span data-ttu-id="26363-1027">**アイコン** ![デバイス クラス Storage 容量読み取りアイコン](./media/user-guide/usbx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1027">**Icon** ![Device Class Storage Read Capacity icon](./media/user-guide/usbx-events/image49.png)</span></span>

<span data-ttu-id="26363-1028">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1028">**Description**</span></span>

<span data-ttu-id="26363-1029">USBX デバイス クラス Storage 容量読み取りイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1029">This event represents a USBX Device Class Storage Read Capacity Event.</span></span>

<span data-ttu-id="26363-1030">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1030">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1031">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1031">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-1032">情報フィールド 2: Lun。</span><span class="sxs-lookup"><span data-stu-id="26363-1032">Info Field 2: Lun.</span></span>
- <span data-ttu-id="26363-1033">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1033">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1034">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1034">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read-format-capacity"></a><span data-ttu-id="26363-1035">デバイス クラス Storage フォーマット容量読み取り</span><span class="sxs-lookup"><span data-stu-id="26363-1035">Device Class Storage Read Format Capacity</span></span> 

#### <a name="ux_device_class_storage_read_format_capacity"></a><span data-ttu-id="26363-1036">ux_device_class_storage_read_format_capacity</span><span class="sxs-lookup"><span data-stu-id="26363-1036">ux_device_class_storage_read_format_capacity</span></span>

<span data-ttu-id="26363-1037">**アイコン** ![デバイス クラス Storage フォーマット容量読み取りアイコン](./media/user-guide/usbx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1037">**Icon** ![Device Class Storage Read Format Capacity icon](./media/user-guide/usbx-events/image50.png)</span></span>

<span data-ttu-id="26363-1038">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1038">**Description**</span></span>

<span data-ttu-id="26363-1039">USBX デバイス クラス Storage フォーマット容量読み取りイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1039">This event represents a USBX Device Class Storage Read Format Capacity Event.</span></span>

<span data-ttu-id="26363-1040">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1040">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1041">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1041">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-1042">情報フィールド 2: Lun。</span><span class="sxs-lookup"><span data-stu-id="26363-1042">Info Field 2: Lun.</span></span>
- <span data-ttu-id="26363-1043">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1043">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1044">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1044">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read-toc"></a><span data-ttu-id="26363-1045">デバイス クラス Storage TOC 読み取り</span><span class="sxs-lookup"><span data-stu-id="26363-1045">Device Class Storage Read TOC</span></span> 

#### <a name="ux_device_class_storage_read_toc"></a><span data-ttu-id="26363-1046">ux_device_class_storage_read_toc</span><span class="sxs-lookup"><span data-stu-id="26363-1046">ux_device_class_storage_read_toc</span></span>

<span data-ttu-id="26363-1047">**アイコン** ![デバイス クラス Storage TOC 読み取りアイコン](./media/user-guide/usbx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1047">**Icon** ![Device Class Storage Read TOC icon](./media/user-guide/usbx-events/image51.png)</span></span>

<span data-ttu-id="26363-1048">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1048">**Description**</span></span>

<span data-ttu-id="26363-1049">USBX デバイス クラス Storage TOC 読み取りイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1049">This event represents a USBX Device Class Storage Read TOC Event.</span></span>

<span data-ttu-id="26363-1050">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1050">**Information Fields**</span></span>

- <span data-ttu-id="26363-1051">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1051">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-1052">情報フィールド 2: Lun。</span><span class="sxs-lookup"><span data-stu-id="26363-1052">Info Field 2: Lun.</span></span>
- <span data-ttu-id="26363-1053">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1053">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1054">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1054">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-request-sense"></a><span data-ttu-id="26363-1055">デバイス クラス Storage センス データ要求</span><span class="sxs-lookup"><span data-stu-id="26363-1055">Device Class Storage Request Sense</span></span> 

#### <a name="ux_device_class_storage_request_sense"></a><span data-ttu-id="26363-1056">ux_device_class_storage_request_sense</span><span class="sxs-lookup"><span data-stu-id="26363-1056">ux_device_class_storage_request_sense</span></span>

<span data-ttu-id="26363-1057">**アイコン** ![デバイス クラス Storage センス データ要求アイコン](./media/user-guide/usbx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1057">**Icon** ![Device Class Storage Request Sense icon](./media/user-guide/usbx-events/image52.png)</span></span>

<span data-ttu-id="26363-1058">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1058">**Description**</span></span>

<span data-ttu-id="26363-1059">USBX デバイス クラス Storage センス データ要求イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1059">This event represents a USBX Device Class Storage Request Sense Event.</span></span>

<span data-ttu-id="26363-1060">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1060">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1061">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1061">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-1062">情報フィールド 2: Lun。</span><span class="sxs-lookup"><span data-stu-id="26363-1062">Info Field 2: Lun.</span></span>
- <span data-ttu-id="26363-1063">情報フィールド 3: センス キー。</span><span class="sxs-lookup"><span data-stu-id="26363-1063">Info Field 3: Sense key.</span></span>
- <span data-ttu-id="26363-1064">情報フィールド 4: コード。</span><span class="sxs-lookup"><span data-stu-id="26363-1064">Info Field 4: Code.</span></span>

### <a name="device-class-storage-start-stop"></a><span data-ttu-id="26363-1065">デバイス クラス Storage 開始/停止</span><span class="sxs-lookup"><span data-stu-id="26363-1065">Device Class Storage Start Stop</span></span> 

#### <a name="ux_device_class_storage_start_stop"></a><span data-ttu-id="26363-1066">ux_device_class_storage_start_stop</span><span class="sxs-lookup"><span data-stu-id="26363-1066">ux_device_class_storage_start_stop</span></span>

<span data-ttu-id="26363-1067">**アイコン** ![デバイス クラス Storage 開始/停止アイコン](./media/user-guide/usbx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1067">**Icon** ![Device Class Storage Start Stop icon](./media/user-guide/usbx-events/image53.png)</span></span>

<span data-ttu-id="26363-1068">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1068">**Description**</span></span>

<span data-ttu-id="26363-1069">USBX デバイス クラス Storage 開始/停止イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1069">This event represents a USBX Device Class Storage Start Stop Event.</span></span>

<span data-ttu-id="26363-1070">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1070">**Information Fields**</span></span>

- <span data-ttu-id="26363-1071">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1071">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-1072">情報フィールド 2: Lun。</span><span class="sxs-lookup"><span data-stu-id="26363-1072">Info Field 2: Lun.</span></span>
- <span data-ttu-id="26363-1073">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1073">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1074">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1074">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-test-ready"></a><span data-ttu-id="26363-1075">デバイス クラス Storage 準備状態テスト</span><span class="sxs-lookup"><span data-stu-id="26363-1075">Device Class Storage Test Ready</span></span> 

#### <a name="ux_device_class_storage_test_ready"></a><span data-ttu-id="26363-1076">ux_device_class_storage_test_ready</span><span class="sxs-lookup"><span data-stu-id="26363-1076">ux_device_class_storage_test_ready</span></span>

<span data-ttu-id="26363-1077">**アイコン** ![デバイス クラス Storage 準備状態テスト アイコン](./media/user-guide/usbx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1077">**Icon** ![Device Class Storage Test Ready icon](./media/user-guide/usbx-events/image54.png)</span></span>

<span data-ttu-id="26363-1078">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1078">**Description**</span></span>

<span data-ttu-id="26363-1079">USBX デバイス クラス Storage 準備状態テスト イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1079">This event represents a USBX Device Class Storage Test Ready Event.</span></span>

<span data-ttu-id="26363-1080">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1080">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1081">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1081">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-1082">情報フィールド 2: Lun。</span><span class="sxs-lookup"><span data-stu-id="26363-1082">Info Field 2: Lun.</span></span>
- <span data-ttu-id="26363-1083">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1083">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1084">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1084">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-verify"></a><span data-ttu-id="26363-1085">デバイス クラス Storage 検証</span><span class="sxs-lookup"><span data-stu-id="26363-1085">Device Class Storage Verify</span></span> 

#### <a name="ux_device_class_storage_verify"></a><span data-ttu-id="26363-1086">ux_device_class_storage_verify</span><span class="sxs-lookup"><span data-stu-id="26363-1086">ux_device_class_storage_verify</span></span>

<span data-ttu-id="26363-1087">**アイコン** ![デバイス クラス Storage 検証アイコン](./media/user-guide/usbx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1087">**Icon** ![Device Class Storage Verify icon](./media/user-guide/usbx-events/image55.png)</span></span>

<span data-ttu-id="26363-1088">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1088">**Description**</span></span>

<span data-ttu-id="26363-1089">USBX デバイス クラス Storage 検証イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1089">This event represents a USBX Device Class Storage Verify Event.</span></span>

<span data-ttu-id="26363-1090">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1090">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1091">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1091">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-1092">情報フィールド 2: Lun。</span><span class="sxs-lookup"><span data-stu-id="26363-1092">Info Field 2: Lun.</span></span>
- <span data-ttu-id="26363-1093">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1093">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1094">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1094">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-write"></a><span data-ttu-id="26363-1095">デバイス クラス Storage 書き込み</span><span class="sxs-lookup"><span data-stu-id="26363-1095">Device Class Storage Write</span></span> 

#### <a name="ux_device_class_storage_write"></a><span data-ttu-id="26363-1096">ux_device_class_storage_write</span><span class="sxs-lookup"><span data-stu-id="26363-1096">ux_device_class_storage_write</span></span>

<span data-ttu-id="26363-1097">**アイコン** ![デバイス クラス Storage 書き込みアイコン](./media/user-guide/usbx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1097">**Icon** ![Device Class Storage Write icon](./media/user-guide/usbx-events/image56.png)</span></span>

<span data-ttu-id="26363-1098">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1098">**Description**</span></span>

<span data-ttu-id="26363-1099">USBX デバイス クラス Storage 書き込みイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1099">This event represents a USBX Device Class Storage Write Event.</span></span>

<span data-ttu-id="26363-1100">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1100">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1101">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1101">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-1102">情報フィールド 2: Lun。</span><span class="sxs-lookup"><span data-stu-id="26363-1102">Info Field 2: Lun.</span></span>
- <span data-ttu-id="26363-1103">情報フィールド 3: セクター。</span><span class="sxs-lookup"><span data-stu-id="26363-1103">Info Field 3: Sector.</span></span>
- <span data-ttu-id="26363-1104">情報フィールド 4: セクター数。</span><span class="sxs-lookup"><span data-stu-id="26363-1104">Info Field 4: Number sectors.</span></span>

### <a name="device-stack-alternate-setting-get"></a><span data-ttu-id="26363-1105">デバイス スタック設定選択肢取得</span><span class="sxs-lookup"><span data-stu-id="26363-1105">Device Stack Alternate Setting Get</span></span> 

#### <a name="ux_device_class_alternate_setting_get"></a><span data-ttu-id="26363-1106">ux_device_class_alternate_setting_get</span><span class="sxs-lookup"><span data-stu-id="26363-1106">ux_device_class_alternate_setting_get</span></span>

<span data-ttu-id="26363-1107">**アイコン** ![デバイス スタック設定選択肢取得アイコン](./media/user-guide/usbx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1107">**Icon** ![Device Stack Alternate Setting Get icon](./media/user-guide/usbx-events/image57.png)</span></span>

<span data-ttu-id="26363-1108">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1108">**Description**</span></span>

<span data-ttu-id="26363-1109">USBX デバイス スタック設定選択肢取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1109">This event represents a USBX Device Stack Alternate Setting Get Event.</span></span>

<span data-ttu-id="26363-1110">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1110">**Information Fields**</span></span>

- <span data-ttu-id="26363-1111">情報フィールド 1: インターフェイスの値。</span><span class="sxs-lookup"><span data-stu-id="26363-1111">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="26363-1112">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1112">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1113">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1113">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1114">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1114">Info Field 4: Not used.</span></span>

### <a name="device-stack-alternate-setting-set"></a><span data-ttu-id="26363-1115">デバイス スタック設定選択肢設定</span><span class="sxs-lookup"><span data-stu-id="26363-1115">Device Stack Alternate Setting Set</span></span> 

#### <a name="ux_device_class_alternate_setting_set"></a><span data-ttu-id="26363-1116">ux_device_class_alternate_setting_set</span><span class="sxs-lookup"><span data-stu-id="26363-1116">ux_device_class_alternate_setting_set</span></span>

<span data-ttu-id="26363-1117">**アイコン** ![デバイス スタック設定選択肢設定アイコン](./media/user-guide/usbx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1117">**Icon** ![Device Stack Alternate Setting Set icon](./media/user-guide/usbx-events/image58.png)</span></span>

<span data-ttu-id="26363-1118">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1118">**Description**</span></span>

<span data-ttu-id="26363-1119">USBX デバイス スタック設定選択肢設定イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1119">This event represents a USBX Device Stack Alternate Setting Set Event.</span></span>

<span data-ttu-id="26363-1120">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1120">**Information Fields**</span></span>
- <span data-ttu-id="26363-1121">情報フィールド 1: インターフェイスの値。</span><span class="sxs-lookup"><span data-stu-id="26363-1121">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="26363-1122">情報フィールド 2: 選択可能な設定の値。</span><span class="sxs-lookup"><span data-stu-id="26363-1122">Info Field 2: Alternate setting value.</span></span>
- <span data-ttu-id="26363-1123">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1123">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1124">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1124">Info Field 4: Not used.</span></span>

### <a name="device-stack-class-register"></a><span data-ttu-id="26363-1125">デバイス スタック クラス登録</span><span class="sxs-lookup"><span data-stu-id="26363-1125">Device Stack Class Register</span></span> 

#### <a name="ux_device_stack_class_register"></a><span data-ttu-id="26363-1126">ux_device_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="26363-1126">ux_device_stack_class_register</span></span>

<span data-ttu-id="26363-1127">**アイコン** ![デバイス スタック クラス登録アイコン](./media/user-guide/usbx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1127">**Icon** ![Device Stack Class Register icon](./media/user-guide/usbx-events/image59.png)</span></span>

<span data-ttu-id="26363-1128">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1128">**Description**</span></span>

<span data-ttu-id="26363-1129">USBX デバイス スタック クラス登録イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1129">This event represents a USBX Device Stack Class Register Event.</span></span>

<span data-ttu-id="26363-1130">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1130">**Information Fields**</span></span>

- <span data-ttu-id="26363-1131">情報フィールド 1: クラス名。</span><span class="sxs-lookup"><span data-stu-id="26363-1131">Info Field 1: Class name.</span></span>
- <span data-ttu-id="26363-1132">情報フィールド 2: インターフェイス番号。</span><span class="sxs-lookup"><span data-stu-id="26363-1132">Info Field 2: Interface number.</span></span>
- <span data-ttu-id="26363-1133">情報フィールド 3: パラメーター。</span><span class="sxs-lookup"><span data-stu-id="26363-1133">Info Field 3: Parameter.</span></span>
- <span data-ttu-id="26363-1134">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1134">Info Field 4: Not used.</span></span>

### <a name="device-stack-clear-feature"></a><span data-ttu-id="26363-1135">デバイス スタック機能消去</span><span class="sxs-lookup"><span data-stu-id="26363-1135">Device Stack Clear Feature</span></span> 

#### <a name="ux_device_stack_clear_feature"></a><span data-ttu-id="26363-1136">ux_device_stack_clear_feature</span><span class="sxs-lookup"><span data-stu-id="26363-1136">ux_device_stack_clear_feature</span></span>

<span data-ttu-id="26363-1137">**アイコン** ![デバイス スタック機能消去アイコン](./media/user-guide/usbx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1137">**Icon** ![Device Stack Clear Feature icon](./media/user-guide/usbx-events/image60.png)</span></span>

<span data-ttu-id="26363-1138">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1138">**Description**</span></span>

<span data-ttu-id="26363-1139">USBX デバイス スタック機能消去イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1139">This event represents a USBX Device Stack Clear Feature Event.</span></span>

<span data-ttu-id="26363-1140">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1140">**Information Fields**</span></span>

- <span data-ttu-id="26363-1141">情報フィールド 1: 要求の種類。</span><span class="sxs-lookup"><span data-stu-id="26363-1141">Info Field 1: Request type.</span></span>
- <span data-ttu-id="26363-1142">情報フィールド 2: 要求の値。</span><span class="sxs-lookup"><span data-stu-id="26363-1142">Info Field 2: Request value.</span></span> <span data-ttu-id="26363-1143">情報フィールド 3: 要求のインデックス。</span><span class="sxs-lookup"><span data-stu-id="26363-1143">Info Field 3: Request index.</span></span>
- <span data-ttu-id="26363-1144">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1144">Info Field 4: Not used.</span></span>

### <a name="device-stack-configuration-get"></a><span data-ttu-id="26363-1145">デバイス スタック構成取得</span><span class="sxs-lookup"><span data-stu-id="26363-1145">Device Stack Configuration Get</span></span> 

#### <a name="ux_device_stack_configuration_get-t"></a><span data-ttu-id="26363-1146">ux_device_stack_configuration_get t</span><span class="sxs-lookup"><span data-stu-id="26363-1146">ux_device_stack_configuration_get t</span></span>

<span data-ttu-id="26363-1147">**アイコン** ![デバイス スタック構成取得アイコン](./media/user-guide/usbx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1147">**Icon** ![Device Stack Configuration Get icon](./media/user-guide/usbx-events/image61.png)</span></span>

<span data-ttu-id="26363-1148">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1148">**Description**</span></span>

<span data-ttu-id="26363-1149">USBX デバイス スタック構成取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1149">This event represents a USBX Device Stack Configuration Get Event.</span></span>

<span data-ttu-id="26363-1150">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1150">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1151">情報フィールド 1: 構成値。</span><span class="sxs-lookup"><span data-stu-id="26363-1151">Info Field 1: Configuration value.</span></span>
- <span data-ttu-id="26363-1152">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1152">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1153">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1153">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1154">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1154">Info Field 4: Not used.</span></span>

### <a name="device-stack-configuration-set"></a><span data-ttu-id="26363-1155">デバイス スタック構成設定</span><span class="sxs-lookup"><span data-stu-id="26363-1155">Device Stack Configuration Set</span></span> 

#### <a name="ux_device_stack_configuration_set"></a><span data-ttu-id="26363-1156">ux_device_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="26363-1156">ux_device_stack_configuration_set</span></span>

<span data-ttu-id="26363-1157">**アイコン** ![デバイス スタック構成設定アイコン](./media/user-guide/usbx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1157">**Icon** ![Device Stack Configuration Set icon](./media/user-guide/usbx-events/image62.png)</span></span>

<span data-ttu-id="26363-1158">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1158">**Description**</span></span>

<span data-ttu-id="26363-1159">USBX デバイス スタック構成設定イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1159">This event represents a USBX Device Stack Configuration Set Event.</span></span>

<span data-ttu-id="26363-1160">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1160">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1161">情報フィールド 1: 構成値。</span><span class="sxs-lookup"><span data-stu-id="26363-1161">Info Field 1: Configuration value.</span></span>
- <span data-ttu-id="26363-1162">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1162">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1163">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1163">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1164">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1164">Info Field 4: Not used.</span></span>

### <a name="device-stack-connect"></a><span data-ttu-id="26363-1165">デバイス スタック接続</span><span class="sxs-lookup"><span data-stu-id="26363-1165">Device Stack Connect</span></span> 

#### <a name="ux_device_stack_connect"></a><span data-ttu-id="26363-1166">ux_device_stack_connect</span><span class="sxs-lookup"><span data-stu-id="26363-1166">ux_device_stack_connect</span></span>

<span data-ttu-id="26363-1167">**アイコン** ![デバイス スタック接続アイコン](./media/user-guide/usbx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1167">**Icon** ![Device Stack Connect icon](./media/user-guide/usbx-events/image63.png)</span></span>

<span data-ttu-id="26363-1168">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1168">**Description**</span></span>

<span data-ttu-id="26363-1169">USBX デバイス スタック記述子送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1169">This event represents a USBX Device Stack Descriptor Send Event.</span></span>

<span data-ttu-id="26363-1170">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1170">**Information Fields**</span></span>

- <span data-ttu-id="26363-1171">情報フィールド 1: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1171">Info Field 1: Not used.</span></span>
- <span data-ttu-id="26363-1172">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1172">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1173">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1173">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1174">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1174">Info Field 4: Not used.</span></span>

### <a name="device-stack-descriptor-send"></a><span data-ttu-id="26363-1175">デバイス スタック記述子送信</span><span class="sxs-lookup"><span data-stu-id="26363-1175">Device Stack Descriptor Send</span></span> 

#### <a name="ux_device_stack_descriptor_send"></a><span data-ttu-id="26363-1176">ux_device_stack_descriptor_send</span><span class="sxs-lookup"><span data-stu-id="26363-1176">ux_device_stack_descriptor_send</span></span>

<span data-ttu-id="26363-1177">**アイコン** ![デバイス スタック記述子送信アイコン](./media/user-guide/usbx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1177">**Icon** ![Device Stack Descriptor Send icon](./media/user-guide/usbx-events/image64.png)</span></span>

<span data-ttu-id="26363-1178">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1178">**Description**</span></span>

<span data-ttu-id="26363-1179">USBX デバイス スタック記述子送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1179">This event represents a USBX Device Stack Descriptor Send Event.</span></span>

<span data-ttu-id="26363-1180">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1180">**Information Fields**</span></span>

- <span data-ttu-id="26363-1181">情報フィールド 1: 記述子の種類。</span><span class="sxs-lookup"><span data-stu-id="26363-1181">Info Field 1: Descriptor type.</span></span>
- <span data-ttu-id="26363-1182">情報フィールド 2: 要求のインデックス。</span><span class="sxs-lookup"><span data-stu-id="26363-1182">Info Field 2: Request index.</span></span>
- <span data-ttu-id="26363-1183">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1183">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1184">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1184">Info Field 4: Not used.</span></span>

### <a name="device-stack-disconnect"></a><span data-ttu-id="26363-1185">デバイス スタック切断</span><span class="sxs-lookup"><span data-stu-id="26363-1185">Device Stack Disconnect</span></span> 

#### <a name="ux_device_stack_disconnect"></a><span data-ttu-id="26363-1186">ux_device_stack_disconnect</span><span class="sxs-lookup"><span data-stu-id="26363-1186">ux_device_stack_disconnect</span></span>

<span data-ttu-id="26363-1187">**アイコン** ![デバイス スタック切断アイコン](./media/user-guide/usbx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1187">**Icon** ![Device Stack Disconnect icon](./media/user-guide/usbx-events/image65.png)</span></span>

<span data-ttu-id="26363-1188">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1188">**Description**</span></span>

<span data-ttu-id="26363-1189">USBX デバイス スタック切断イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1189">This event represents a USBX Device Stack Disconnect Event.</span></span>

<span data-ttu-id="26363-1190">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1190">**Information Fields**</span></span>

- <span data-ttu-id="26363-1191">情報フィールド 1: デバイス。</span><span class="sxs-lookup"><span data-stu-id="26363-1191">Info Field 1: Device.</span></span>
- <span data-ttu-id="26363-1192">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1192">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1193">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1193">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1194">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1194">Info Field 4: Not used.</span></span>

### <a name="device-stack-endpoint-stall"></a><span data-ttu-id="26363-1195">デバイス スタック エンドポイント停止</span><span class="sxs-lookup"><span data-stu-id="26363-1195">Device Stack Endpoint Stall</span></span> 

#### <a name="ux_device_stack_endpoint_stall"></a><span data-ttu-id="26363-1196">ux_device_stack_endpoint_stall</span><span class="sxs-lookup"><span data-stu-id="26363-1196">ux_device_stack_endpoint_stall</span></span>

<span data-ttu-id="26363-1197">**アイコン** ![デバイス スタック エンドポイント停止アイコン](./media/user-guide/usbx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1197">**Icon** ![Device Stack Endpoint Stall icon](./media/user-guide/usbx-events/image66.png)</span></span>

<span data-ttu-id="26363-1198">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1198">**Description**</span></span>

<span data-ttu-id="26363-1199">USBX デバイス スタック エンドポイント停止イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1199">This event represents a USBX Device Stack Endpoint Stall Event.</span></span>

<span data-ttu-id="26363-1200">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1200">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1201">情報フィールド 1: エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="26363-1201">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="26363-1202">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1202">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1203">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1203">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1204">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1204">Info Field 4: Not used.</span></span>

### <a name="device-stack-get-status"></a><span data-ttu-id="26363-1205">デバイス スタック状態取得</span><span class="sxs-lookup"><span data-stu-id="26363-1205">Device Stack Get Status</span></span> 

#### <a name="ux_device_stack_get_status"></a><span data-ttu-id="26363-1206">ux_device_stack_get_status</span><span class="sxs-lookup"><span data-stu-id="26363-1206">ux_device_stack_get_status</span></span>

<span data-ttu-id="26363-1207">**アイコン** ![デバイス スタック状態取得アイコン](./media/user-guide/usbx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1207">**Icon** ![Device Stack Get Status icon](./media/user-guide/usbx-events/image67.png)</span></span>

<span data-ttu-id="26363-1208">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1208">**Description**</span></span>

<span data-ttu-id="26363-1209">USBX デバイス スタック状態取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1209">This event represents a USBX Device Stack Get Status Event.</span></span>

<span data-ttu-id="26363-1210">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1210">**Information Fields**</span></span>

- <span data-ttu-id="26363-1211">情報フィールド 1: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1211">Info Field 1: Not used.</span></span>
- <span data-ttu-id="26363-1212">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1212">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1213">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1213">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1214">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1214">Info Field 4: Not used.</span></span>

### <a name="device-stack-host-wakeup"></a><span data-ttu-id="26363-1215">デバイス スタック ホスト スリープ解除</span><span class="sxs-lookup"><span data-stu-id="26363-1215">Device Stack Host Wakeup</span></span> 

#### <a name="ux_device_stack_host_wakeup"></a><span data-ttu-id="26363-1216">ux_device_stack_host_wakeup</span><span class="sxs-lookup"><span data-stu-id="26363-1216">ux_device_stack_host_wakeup</span></span>

<span data-ttu-id="26363-1217">**アイコン** ![デバイス スタック ホスト スリープ解除アイコン](./media/user-guide/usbx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1217">**Icon** ![Device Stack Host Wakeup icon](./media/user-guide/usbx-events/image68.png)</span></span>

<span data-ttu-id="26363-1218">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1218">**Description**</span></span>

<span data-ttu-id="26363-1219">USBX デバイス スタック ホスト スリープ解除イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1219">This event represents a USBX Device Stack Host Wakeup Event.</span></span>

<span data-ttu-id="26363-1220">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1220">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1221">情報フィールド 1: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1221">Info Field 1: Not used.</span></span>
- <span data-ttu-id="26363-1222">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1222">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1223">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1223">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1224">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1224">Info Field 4: Not used.</span></span>

### <a name="device-stack-initialize"></a><span data-ttu-id="26363-1225">デバイス スタック初期化</span><span class="sxs-lookup"><span data-stu-id="26363-1225">Device Stack Initialize</span></span> 

#### <a name="ux_device_stack_initialize"></a><span data-ttu-id="26363-1226">ux_device_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="26363-1226">ux_device_stack_initialize</span></span>

<span data-ttu-id="26363-1227">**アイコン** ![デバイス スタック初期化アイコン](./media/user-guide/usbx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1227">**Icon** ![Device Stack Initialize icon](./media/user-guide/usbx-events/image69.png)</span></span>

<span data-ttu-id="26363-1228">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1228">**Description**</span></span>

<span data-ttu-id="26363-1229">USBX デバイス スタック初期化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1229">This event represents a USBX Device Stack Initialize Event.</span></span>

<span data-ttu-id="26363-1230">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1230">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1231">情報フィールド 1: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1231">Info Field 1: Not used.</span></span>
- <span data-ttu-id="26363-1232">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1232">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1233">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1233">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1234">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1234">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-delete"></a><span data-ttu-id="26363-1235">デバイス スタック インターフェイス削除</span><span class="sxs-lookup"><span data-stu-id="26363-1235">Device Stack Interface Delete</span></span> 

#### <a name="ux_device_stack_interface_delete"></a><span data-ttu-id="26363-1236">ux_device_stack_interface_delete</span><span class="sxs-lookup"><span data-stu-id="26363-1236">ux_device_stack_interface_delete</span></span>

<span data-ttu-id="26363-1237">**アイコン** ![デバイス スタック インターフェイス削除アイコン](./media/user-guide/usbx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1237">**Icon** ![Device Stack Interface Delete icon](./media/user-guide/usbx-events/image70.png)</span></span>

<span data-ttu-id="26363-1238">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1238">**Description**</span></span>

<span data-ttu-id="26363-1239">USBX デバイス スタック インターフェイス削除イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1239">This event represents a USBX Device Stack Interface Delete Event.</span></span>

<span data-ttu-id="26363-1240">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1240">**Information Fields**</span></span>

- <span data-ttu-id="26363-1241">情報フィールド 1: インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="26363-1241">Info Field 1: Interface.</span></span>
- <span data-ttu-id="26363-1242">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1242">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1243">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1243">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1244">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1244">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-get"></a><span data-ttu-id="26363-1245">デバイス スタック インターフェイス取得</span><span class="sxs-lookup"><span data-stu-id="26363-1245">Device Stack Interface Get</span></span> 

#### <a name="ux_device_stack_interface_get"></a><span data-ttu-id="26363-1246">ux_device_stack_interface_get</span><span class="sxs-lookup"><span data-stu-id="26363-1246">ux_device_stack_interface_get</span></span>

<span data-ttu-id="26363-1247">**アイコン** ![デバイス スタック インターフェイス取得アイコン](./media/user-guide/usbx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1247">**Icon** ![Device Stack Interface Get icon](./media/user-guide/usbx-events/image71.png)</span></span>

<span data-ttu-id="26363-1248">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1248">**Description**</span></span>

<span data-ttu-id="26363-1249">USBX デバイス スタック インターフェイス取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1249">This event represents a USBX Device Stack Interface Get Event.</span></span>

<span data-ttu-id="26363-1250">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1250">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1251">情報フィールド 1: インターフェイスの値。</span><span class="sxs-lookup"><span data-stu-id="26363-1251">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="26363-1252">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1252">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1253">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1253">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1254">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1254">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-set"></a><span data-ttu-id="26363-1255">デバイス スタック インターフェイス設定</span><span class="sxs-lookup"><span data-stu-id="26363-1255">Device Stack Interface Set</span></span> 

#### <a name="ux_device_stack_interface_set"></a><span data-ttu-id="26363-1256">ux_device_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="26363-1256">ux_device_stack_interface_set</span></span>

<span data-ttu-id="26363-1257">**アイコン** ![デバイス スタック インターフェイス設定アイコン](./media/user-guide/usbx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1257">**Icon** ![Device Stack Interface Set icon](./media/user-guide/usbx-events/image72.png)</span></span>

<span data-ttu-id="26363-1258">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1258">**Description**</span></span>

<span data-ttu-id="26363-1259">USBX デバイス スタック インターフェイス設定イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1259">This event represents a USBX Device Stack Interface Set Event.</span></span>

<span data-ttu-id="26363-1260">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1260">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1261">情報フィールド 1: 要求の値。</span><span class="sxs-lookup"><span data-stu-id="26363-1261">Info Field 1: Request value.</span></span> <span data-ttu-id="26363-1262">情報フィールド 2: 要求のインデックス。</span><span class="sxs-lookup"><span data-stu-id="26363-1262">Info Field 2: Request index.</span></span>
- <span data-ttu-id="26363-1263">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1263">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1264">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1264">Info Field 4: Not used.</span></span>

### <a name="device-stack-set-feature"></a><span data-ttu-id="26363-1265">デバイス スタック機能設定</span><span class="sxs-lookup"><span data-stu-id="26363-1265">Device Stack Set Feature</span></span> 

#### <a name="ux_device_stack_set_feature"></a><span data-ttu-id="26363-1266">ux_device_stack_set_feature</span><span class="sxs-lookup"><span data-stu-id="26363-1266">ux_device_stack_set_feature</span></span>

<span data-ttu-id="26363-1267">**アイコン** ![デバイス スタック機能設定アイコン](./media/user-guide/usbx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1267">**Icon** ![Device Stack Set Feature icon](./media/user-guide/usbx-events/image73.png)</span></span>

<span data-ttu-id="26363-1268">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1268">**Description**</span></span>

<span data-ttu-id="26363-1269">USBX デバイス スタック機能設定イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1269">This event represents a USBX Device Stack Set Feature Event.</span></span>

<span data-ttu-id="26363-1270">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1270">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1271">情報フィールド 1: 要求の値。</span><span class="sxs-lookup"><span data-stu-id="26363-1271">Info Field 1: Request value.</span></span> <span data-ttu-id="26363-1272">情報フィールド 2: 要求のインデックス。</span><span class="sxs-lookup"><span data-stu-id="26363-1272">Info Field 2: Request index.</span></span>
- <span data-ttu-id="26363-1273">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1273">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1274">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1274">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-abort"></a><span data-ttu-id="26363-1275">デバイス スタック転送アボート</span><span class="sxs-lookup"><span data-stu-id="26363-1275">Device Stack Transfer Abort</span></span> 

#### <a name="ux_device_stack_transfer_abort"></a><span data-ttu-id="26363-1276">ux_device_stack_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="26363-1276">ux_device_stack_transfer_abort</span></span>

<span data-ttu-id="26363-1277">**アイコン** ![デバイス スタック転送アボート アイコン](./media/user-guide/usbx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1277">**Icon** ![Device Stack Transfer Abort icon](./media/user-guide/usbx-events/image74.png)</span></span>

<span data-ttu-id="26363-1278">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1278">**Description**</span></span>

<span data-ttu-id="26363-1279">USBX デバイス スタック転送アボート イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1279">This event represents a USBX Device Stack Transfer Abort Event.</span></span>

<span data-ttu-id="26363-1280">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1280">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1281">情報フィールド 1: 転送要求。</span><span class="sxs-lookup"><span data-stu-id="26363-1281">Info Field 1: Transfer request.</span></span>
- <span data-ttu-id="26363-1282">情報フィールド 2: 完了コード。</span><span class="sxs-lookup"><span data-stu-id="26363-1282">Info Field 2: Completion code.</span></span>
- <span data-ttu-id="26363-1283">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1283">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1284">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1284">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-all-request-abort"></a><span data-ttu-id="26363-1285">デバイス スタック全転送要求アボート</span><span class="sxs-lookup"><span data-stu-id="26363-1285">Device Stack Transfer All Request Abort</span></span> 

#### <a name="ux_device_stack_transfer_all_request_abort"></a><span data-ttu-id="26363-1286">ux_device_stack_transfer_all_request_abort</span><span class="sxs-lookup"><span data-stu-id="26363-1286">ux_device_stack_transfer_all_request_abort</span></span>

<span data-ttu-id="26363-1287">**アイコン** ![デバイス スタック全転送要求アボート アイコン](./media/user-guide/usbx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1287">**Icon** ![Device Stack Transfer All Request Abort icon](./media/user-guide/usbx-events/image75.png)</span></span>

<span data-ttu-id="26363-1288">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1288">**Description**</span></span>

<span data-ttu-id="26363-1289">USBX デバイス スタック全転送要求アボート イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1289">This event represents a USBX Device Stack Transfer All Request Abort Event.</span></span>

<span data-ttu-id="26363-1290">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1290">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1291">情報フィールド 1: エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="26363-1291">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="26363-1292">情報フィールド 2: 完了コード。</span><span class="sxs-lookup"><span data-stu-id="26363-1292">Info Field 2: Completion code.</span></span>
- <span data-ttu-id="26363-1293">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1293">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1294">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1294">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-request"></a><span data-ttu-id="26363-1295">デバイス スタック転送要求</span><span class="sxs-lookup"><span data-stu-id="26363-1295">Device Stack Transfer Request</span></span> 

#### <a name="ux_device_stack_transfer_request"></a><span data-ttu-id="26363-1296">ux_device_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="26363-1296">ux_device_stack_transfer_request</span></span>

<span data-ttu-id="26363-1297">**アイコン** ![デバイス スタック転送要求アイコン](./media/user-guide/usbx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1297">**Icon** ![Device Stack Transfer Request icon](./media/user-guide/usbx-events/image76.png)</span></span>

<span data-ttu-id="26363-1298">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1298">**Description**</span></span>

<span data-ttu-id="26363-1299">USBX デバイス スタック転送要求イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1299">This event represents a USBX Device Stack Transfer Request Event.</span></span>

<span data-ttu-id="26363-1300">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1300">**Information Fields**</span></span>

- <span data-ttu-id="26363-1301">情報フィールド 1: 転送要求。</span><span class="sxs-lookup"><span data-stu-id="26363-1301">Info Field 1: Transfer request.</span></span>
- <span data-ttu-id="26363-1302">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1302">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1303">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1303">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1304">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1304">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-activate"></a><span data-ttu-id="26363-1305">ホスト クラス ASIX アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1305">Host Class Asix Activate</span></span> 

#### <a name="ux_host_class_asix_activate"></a><span data-ttu-id="26363-1306">ux_host_class_asix_activate</span><span class="sxs-lookup"><span data-stu-id="26363-1306">ux_host_class_asix_activate</span></span>

<span data-ttu-id="26363-1307">**アイコン** ![ホスト クラス ASIX アクティブ化アイコン](./media/user-guide/usbx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1307">**Icon** ![Host Class Asix Activate icon](./media/user-guide/usbx-events/image77.png)</span></span>

<span data-ttu-id="26363-1308">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1308">**Description**</span></span>

<span data-ttu-id="26363-1309">USBX ホスト クラス ASIX アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1309">This event represents a USBX Host Class Asix Activate.</span></span>

<span data-ttu-id="26363-1310">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1310">**Information Fields**</span></span>

- <span data-ttu-id="26363-1311">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1311">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-1312">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1312">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1313">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1313">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1314">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1314">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-deactivate"></a><span data-ttu-id="26363-1315">ホスト クラス ASIX 非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1315">Host Class Asix Deactivate</span></span> 

#### <a name="ux_host_class_asix_deactivate"></a><span data-ttu-id="26363-1316">ux_host_class_asix_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-1316">ux_host_class_asix_deactivate</span></span>

<span data-ttu-id="26363-1317">**アイコン** ![ホスト クラス ASIX 非アクティブ化アイコン](./media/user-guide/usbx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1317">**Icon** ![Host Class Asix Deactivate icon](./media/user-guide/usbx-events/image78.png)</span></span>

<span data-ttu-id="26363-1318">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1318">**Description**</span></span>

<span data-ttu-id="26363-1319">USBX ホスト クラス ASIX 非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1319">This event represents a USBX Host Class Asix Deactivate Event.</span></span>

<span data-ttu-id="26363-1320">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1320">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1321">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1321">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-1322">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1322">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1323">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1323">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1324">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1324">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-interrupt-notification"></a><span data-ttu-id="26363-1325">ホスト クラス ASIX 割り込み通知</span><span class="sxs-lookup"><span data-stu-id="26363-1325">Host Class Asix Interrupt Notification</span></span> 

#### <a name="ux_host_class_asix_interrupt_notification"></a><span data-ttu-id="26363-1326">ux_host_class_asix_interrupt_notification</span><span class="sxs-lookup"><span data-stu-id="26363-1326">ux_host_class_asix_interrupt_notification</span></span>

<span data-ttu-id="26363-1327">**アイコン** ![ホスト クラス ASIX 割り込み通知アイコン](./media/user-guide/usbx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1327">**Icon** ![Host Class Asix Interrupt Notification icon](./media/user-guide/usbx-events/image79.png)</span></span>

<span data-ttu-id="26363-1328">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1328">**Description**</span></span>

<span data-ttu-id="26363-1329">USBX ホスト クラス ASIX 割り込み通知イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1329">This event represents a USBX Host Class Asix Interrupt Notification Event.</span></span>

<span data-ttu-id="26363-1330">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1330">**Information Fields**</span></span>

- <span data-ttu-id="26363-1331">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1331">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-1332">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1332">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1333">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1333">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1334">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1334">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-read"></a><span data-ttu-id="26363-1335">ホスト クラス ASIX 読み取り</span><span class="sxs-lookup"><span data-stu-id="26363-1335">Host Class Asix Read</span></span> 

#### <a name="ux_host_class_asix_read"></a><span data-ttu-id="26363-1336">ux_host_class_asix_read</span><span class="sxs-lookup"><span data-stu-id="26363-1336">ux_host_class_asix_read</span></span>

<span data-ttu-id="26363-1337">**アイコン** ![ホスト クラス ASIX 読み取りアイコン](./media/user-guide/usbx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1337">**Icon** ![Host Class Asix Read icon](./media/user-guide/usbx-events/image80.png)</span></span>

<span data-ttu-id="26363-1338">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1338">**Description**</span></span>

<span data-ttu-id="26363-1339">USBX ホスト クラス ASIX 読み取りイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1339">This event represents a USBX Host Class Asix Read Event.</span></span>

<span data-ttu-id="26363-1340">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1340">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1341">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1341">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1342">情報フィールド 2: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-1342">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="26363-1343">情報フィールド 3: 要求された長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-1343">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="26363-1344">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1344">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-write"></a><span data-ttu-id="26363-1345">ホスト クラス ASIX 書き込み</span><span class="sxs-lookup"><span data-stu-id="26363-1345">Host Class Asix Write</span></span> 

#### <a name="ux_host_class_asix_write"></a><span data-ttu-id="26363-1346">ux_host_class_asix_write</span><span class="sxs-lookup"><span data-stu-id="26363-1346">ux_host_class_asix_write</span></span>

<span data-ttu-id="26363-1347">**アイコン** ![ホスト クラス ASIX 書き込みアイコン](./media/user-guide/usbx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1347">**Icon** ![Host Class Asix Write icon](./media/user-guide/usbx-events/image81.png)</span></span>

<span data-ttu-id="26363-1348">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1348">**Description**</span></span>

<span data-ttu-id="26363-1349">USBX ホスト クラス ASIX 書き込みイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1349">This event represents a USBX Host Class Asix Write Event.</span></span>

<span data-ttu-id="26363-1350">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1350">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1351">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1351">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1352">情報フィールド 2: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-1352">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="26363-1353">情報フィールド 3: 要求された長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-1353">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="26363-1354">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1354">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-activate"></a><span data-ttu-id="26363-1355">ホスト クラス Audio アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1355">Host Class Audio Activate</span></span> 

#### <a name="ux_host_class_audio_activate"></a><span data-ttu-id="26363-1356">ux_host_class_audio_activate</span><span class="sxs-lookup"><span data-stu-id="26363-1356">ux_host_class_audio_activate</span></span>

<span data-ttu-id="26363-1357">**アイコン** ![ホスト クラス Audio アクティブ化アイコン](./media/user-guide/usbx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1357">**Icon** ![Host Class Audio Activate icon](./media/user-guide/usbx-events/image82.png)</span></span>

<span data-ttu-id="26363-1358">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1358">**Description**</span></span>

<span data-ttu-id="26363-1359">USBX ホスト クラス Audio アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1359">This event represents a USBX Host Class Audio Activate Event.</span></span>

<span data-ttu-id="26363-1360">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1360">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1361">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1361">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1362">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1362">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1363">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1363">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1364">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1364">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-control-value-get"></a><span data-ttu-id="26363-1365">ホスト クラス Audio コントロール値取得</span><span class="sxs-lookup"><span data-stu-id="26363-1365">Host Class Audio Control Value Get</span></span> 

#### <a name="ux_host_class_audio_control_value_get"></a><span data-ttu-id="26363-1366">ux_host_class_audio_control_value_get</span><span class="sxs-lookup"><span data-stu-id="26363-1366">ux_host_class_audio_control_value_get</span></span>

<span data-ttu-id="26363-1367">**アイコン** ![ホスト クラス Audio コントロール値取得アイコン](./media/user-guide/usbx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1367">**Icon** ![Host Class Audio Control Value Get icon](./media/user-guide/usbx-events/image83.png)</span></span>

<span data-ttu-id="26363-1368">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1368">**Description**</span></span>

<span data-ttu-id="26363-1369">USBX ホスト クラス Audio コントロール値取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1369">This event represents a USBX Host Class Audio Control Value Get Event.</span></span>

<span data-ttu-id="26363-1370">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1370">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1371">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1371">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1372">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1372">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1373">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1373">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1374">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1374">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-control-value-set"></a><span data-ttu-id="26363-1375">ホスト クラス Audio コントロール値設定</span><span class="sxs-lookup"><span data-stu-id="26363-1375">Host Class Audio Control Value Set</span></span> 

#### <a name="ux_host_class_audio_control_value_set"></a><span data-ttu-id="26363-1376">ux_host_class_audio_control_value_set</span><span class="sxs-lookup"><span data-stu-id="26363-1376">ux_host_class_audio_control_value_set</span></span>

<span data-ttu-id="26363-1377">**アイコン** ![ホスト クラス Audio コントロール値設定アイコン](./media/user-guide/usbx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1377">**Icon** ![Host Class Audio Control Value Set icon](./media/user-guide/usbx-events/image84.png)</span></span>

<span data-ttu-id="26363-1378">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1378">**Description**</span></span>

<span data-ttu-id="26363-1379">NetX の I/O ドライバーの遅延処理イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1379">This event represents an internal NetX I/O driver deferred processing event.</span></span>

<span data-ttu-id="26363-1380">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1380">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1381">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1381">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1382">情報フィールド 2: オーディオ コントロール。</span><span class="sxs-lookup"><span data-stu-id="26363-1382">Info Field 2: Audio control.</span></span>
- <span data-ttu-id="26363-1383">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1383">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1384">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1384">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-deactivate"></a><span data-ttu-id="26363-1385">ホスト クラス Audio 非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1385">Host Class Audio Deactivate</span></span> 

#### <a name="ux_host_class_audio_deactivate"></a><span data-ttu-id="26363-1386">ux_host_class_audio_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-1386">ux_host_class_audio_deactivate</span></span>

<span data-ttu-id="26363-1387">**アイコン** ![ホスト クラス Audio 非アクティブ化アイコン](./media/user-guide/usbx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1387">**Icon** ![Host Class Audio Deactivate icon](./media/user-guide/usbx-events/image85.png)</span></span>

<span data-ttu-id="26363-1388">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1388">**Description**</span></span>

<span data-ttu-id="26363-1389">USBX ホスト クラス Audio 非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1389">This event represents a USBX Host Class Audio Deactivate Event.</span></span>

<span data-ttu-id="26363-1390">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1390">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1391">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1391">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1392">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1392">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1393">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1393">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1394">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1394">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-read"></a><span data-ttu-id="26363-1395">ホスト クラス Audio 読み取り</span><span class="sxs-lookup"><span data-stu-id="26363-1395">Host Class Audio Read</span></span> 

#### <a name="ux_host_class_audio_read"></a><span data-ttu-id="26363-1396">ux_host_class_audio_read</span><span class="sxs-lookup"><span data-stu-id="26363-1396">ux_host_class_audio_read</span></span>

<span data-ttu-id="26363-1397">**アイコン** ![ホスト クラス Audio 読み取りアイコン](./media/user-guide/usbx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1397">**Icon** ![Host Class Audio Read icon](./media/user-guide/usbx-events/image86.png)</span></span>

<span data-ttu-id="26363-1398">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1398">**Description**</span></span>

<span data-ttu-id="26363-1399">USBX ホスト クラス Audio 読み取りイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1399">This event represents a USBX Host Class Audio Read Event.</span></span>

- <span data-ttu-id="26363-1400">情報フィールド</span><span class="sxs-lookup"><span data-stu-id="26363-1400">Information Fields</span></span> 
- <span data-ttu-id="26363-1401">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1401">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1402">情報フィールド 2: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-1402">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="26363-1403">情報フィールド 3: 要求された長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-1403">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="26363-1404">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1404">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-streaming-sampling-get"></a><span data-ttu-id="26363-1405">ホスト クラス Audio ストリーミング サンプリング取得</span><span class="sxs-lookup"><span data-stu-id="26363-1405">Host Class Audio Streaming Sampling Get</span></span> 

#### <a name="ux_host_class_audio_streaming_sampling_get"></a><span data-ttu-id="26363-1406">ux_host_class_audio_streaming_sampling_get</span><span class="sxs-lookup"><span data-stu-id="26363-1406">ux_host_class_audio_streaming_sampling_get</span></span>

<span data-ttu-id="26363-1407">**アイコン** ![ホスト クラス Audio ストリーミング サンプリング取得アイコン](./media/user-guide/usbx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1407">**Icon** ![Host Class Audio Streaming Sampling Get icon](./media/user-guide/usbx-events/image87.png)</span></span>

<span data-ttu-id="26363-1408">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1408">**Description**</span></span>

<span data-ttu-id="26363-1409">USBX ホスト クラス Audio ストリーミング サンプリング取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1409">This event represents a USBX Host Class Audio Streaming Sampling Get Event.</span></span>

<span data-ttu-id="26363-1410">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1410">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1411">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1411">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1412">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1412">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1413">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1413">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1414">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1414">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-streaming-sampling-set"></a><span data-ttu-id="26363-1415">ホスト クラス Audio ストリーミング サンプリング設定</span><span class="sxs-lookup"><span data-stu-id="26363-1415">Host Class Audio Streaming Sampling Set</span></span> 

#### <a name="ux_host_class_audio_streaming_sampling_set"></a><span data-ttu-id="26363-1416">ux_host_class_audio_streaming_sampling_set</span><span class="sxs-lookup"><span data-stu-id="26363-1416">ux_host_class_audio_streaming_sampling_set</span></span>

<span data-ttu-id="26363-1417">**アイコン** ![ホスト クラス Audio ストリーミング サンプリング設定アイコン](./media/user-guide/usbx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1417">**Icon** ![Host Class Audio Streaming Sampling Set icon](./media/user-guide/usbx-events/image88.png)</span></span>

<span data-ttu-id="26363-1418">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1418">**Description**</span></span>

<span data-ttu-id="26363-1419">USBX ホスト クラス Audio ストリーミング サンプリング設定イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1419">This event represents a USBX Host Class Audio Streaming Sampling Set Event.</span></span>

<span data-ttu-id="26363-1420">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1420">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1421">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1421">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1422">情報フィールド 2: オーディオ サンプリング。</span><span class="sxs-lookup"><span data-stu-id="26363-1422">Info Field 2: Audio Sampling.</span></span>
- <span data-ttu-id="26363-1423">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1423">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1424">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1424">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-write"></a><span data-ttu-id="26363-1425">ホスト クラス Audio 書き込み</span><span class="sxs-lookup"><span data-stu-id="26363-1425">Host Class Audio Write</span></span> 

#### <a name="ux_host_class_audio_write"></a><span data-ttu-id="26363-1426">ux_host_class_audio_write</span><span class="sxs-lookup"><span data-stu-id="26363-1426">ux_host_class_audio_write</span></span>

<span data-ttu-id="26363-1427">**アイコン** ![ホスト クラス Audio 書き込みアイコン](./media/user-guide/usbx-events/image89.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1427">**Icon** ![Host Class Audio Write icon](./media/user-guide/usbx-events/image89.png)</span></span>

<span data-ttu-id="26363-1428">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1428">**Description**</span></span>

<span data-ttu-id="26363-1429">USBX ホスト クラス Audio 書き込みイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1429">This event represents a USBX Host Class Audio Write Event.</span></span>

<span data-ttu-id="26363-1430">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1430">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1431">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1431">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1432">情報フィールド 2: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-1432">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="26363-1433">情報フィールド 3: 要求された長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-1433">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="26363-1434">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1434">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-activate"></a><span data-ttu-id="26363-1435">ホスト クラス CDC ACM アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1435">Host Class Cdc Acm Activate</span></span> 

#### <a name="ux_host_class_cdc_acm_activate"></a><span data-ttu-id="26363-1436">ux_host_class_cdc_acm_activate</span><span class="sxs-lookup"><span data-stu-id="26363-1436">ux_host_class_cdc_acm_activate</span></span>

<span data-ttu-id="26363-1437">**アイコン** ![ホスト クラス CDC ACM アクティブ化アイコン](./media/user-guide/usbx-events/image90.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1437">**Icon** ![Host Class C D C A C M Activate icon](./media/user-guide/usbx-events/image90.png)</span></span>

<span data-ttu-id="26363-1438">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1438">**Description**</span></span>

<span data-ttu-id="26363-1439">USBX ホスト クラス CDC ACM アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1439">This event represents a USBX Host Class Cdc Acm Activate Event.</span></span>

<span data-ttu-id="26363-1440">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1440">**Information Fields**</span></span>

- <span data-ttu-id="26363-1441">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1441">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1442">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1442">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1443">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1443">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1444">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1444">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-deactivate"></a><span data-ttu-id="26363-1445">ホスト クラス CDC ACM 非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1445">Host Class Cdc Acm Deactivate</span></span> 

#### <a name="ux_host_class_cdc_acm_deactivate"></a><span data-ttu-id="26363-1446">ux_host_class_cdc_acm_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-1446">ux_host_class_cdc_acm_deactivate</span></span>

<span data-ttu-id="26363-1447">**アイコン** ![ホスト クラス CDC ACM 非アクティブ化アイコン](./media/user-guide/usbx-events/image91.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1447">**Icon** ![Host Class C D C A C M Deactivate icon](./media/user-guide/usbx-events/image91.png)</span></span>

<span data-ttu-id="26363-1448">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1448">**Description**</span></span>

<span data-ttu-id="26363-1449">USBX ホスト クラス CDC ACM 非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1449">This event represents a USBX Host Class Cdc Acm Deactivate Event.</span></span>

<span data-ttu-id="26363-1450">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1450">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1451">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1451">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1452">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1452">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1453">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1453">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1454">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1454">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-abort-in-pipe"></a><span data-ttu-id="26363-1455">ホスト クラス CDC ACM IOCTL 入力パイプ アボート</span><span class="sxs-lookup"><span data-stu-id="26363-1455">Host Class Cdc Acm Ioctl Abort In Pipe</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_abort_in_pipe"></a><span data-ttu-id="26363-1456">ux_host_class_cdc_acm_ioctl_abort_in_pipe</span><span class="sxs-lookup"><span data-stu-id="26363-1456">ux_host_class_cdc_acm_ioctl_abort_in_pipe</span></span>

<span data-ttu-id="26363-1457">**アイコン** ![ホスト クラス CDC ACM IOCTL 入力パイプ アボート アイコン](./media/user-guide/usbx-events/image92.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1457">**Icon** ![Host Class C D C A C M I O C T L Abort In Pipe icon](./media/user-guide/usbx-events/image92.png)</span></span>

<span data-ttu-id="26363-1458">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1458">**Description**</span></span>

<span data-ttu-id="26363-1459">USBX ホスト クラス CDC ACM IOCTL 入力パイプ アボート イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1459">This event represents a USBX Host Class Cdc Acm Ioctl Abort In Pipe Event.</span></span>

<span data-ttu-id="26363-1460">情報フィールド</span><span class="sxs-lookup"><span data-stu-id="26363-1460">Information Fields</span></span> 

- <span data-ttu-id="26363-1461">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1461">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1462">情報フィールド 2: エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="26363-1462">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="26363-1463">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1463">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1464">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1464">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-abort-out-pipe"></a><span data-ttu-id="26363-1465">ホスト クラス CDC ACM IOCTL 出力パイプ アボート</span><span class="sxs-lookup"><span data-stu-id="26363-1465">Host Class Cdc Acm Ioctl Abort Out Pipe</span></span> 

#### <a name="ux_host_class_cdc_acm_ioct_abort_out_pipe"></a><span data-ttu-id="26363-1466">ux_host_class_cdc_acm_ioct_abort_out_pipe</span><span class="sxs-lookup"><span data-stu-id="26363-1466">ux_host_class_cdc_acm_ioct_abort_out_pipe</span></span>

<span data-ttu-id="26363-1467">**アイコン** ![[ホスト クラス CDC ACM IOCTL 出力パイプ アボート アイコン](./media/user-guide/usbx-events/image93.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1467">**Icon** ![[Host Class C D C A C M I O C T L Abort Out Pipe icon](./media/user-guide/usbx-events/image93.png)</span></span>

<span data-ttu-id="26363-1468">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1468">**Description**</span></span>

<span data-ttu-id="26363-1469">USBX ホスト クラス CDC ACM IOCTL 出力パイプ アボート イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1469">This event represents a USBX Host Class Cdc Acm Ioctl Abort Out Pipe Event.</span></span>

<span data-ttu-id="26363-1470">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1470">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1471">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1471">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1472">情報フィールド 2: エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="26363-1472">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="26363-1473">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1473">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1474">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1474">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-get-device-status"></a><span data-ttu-id="26363-1475">ホスト クラス CDC ACM IOCTL デバイス状態取得</span><span class="sxs-lookup"><span data-stu-id="26363-1475">Host Class Cdc Acm Ioctl Get Device Status</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_get_device_status"></a><span data-ttu-id="26363-1476">ux_host_class_cdc_acm_ioctl_get_device_status</span><span class="sxs-lookup"><span data-stu-id="26363-1476">ux_host_class_cdc_acm_ioctl_get_device_status</span></span>

<span data-ttu-id="26363-1477">**アイコン** ![ホスト クラス CDC ACM IOCTL デバイス状態取得アイコン](./media/user-guide/usbx-events/image94.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1477">**Icon** ![Host Class C D C A C M I O C T L Get Device Status icon](./media/user-guide/usbx-events/image94.png)</span></span>

<span data-ttu-id="26363-1478">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1478">**Description**</span></span>

<span data-ttu-id="26363-1479">USBX ホスト クラス CDC ACM IOCTL デバイス状態取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1479">This event represents a USBX Host Class Cdc Acm Ioctl Get Device Status Event.</span></span>

<span data-ttu-id="26363-1480">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1480">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1481">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1481">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1482">情報フィールド 2: デバイスの状態。</span><span class="sxs-lookup"><span data-stu-id="26363-1482">Info Field 2: Device status.</span></span>
- <span data-ttu-id="26363-1483">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1483">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1484">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1484">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-get-line-coding"></a><span data-ttu-id="26363-1485">ホスト クラス CDC ACM IOCTL 伝送路符号化取得</span><span class="sxs-lookup"><span data-stu-id="26363-1485">Host Class Cdc Acm Ioctl Get Line Coding</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_get_line_coding"></a><span data-ttu-id="26363-1486">ux_host_class_cdc_acm_ioctl_get_line_coding</span><span class="sxs-lookup"><span data-stu-id="26363-1486">ux_host_class_cdc_acm_ioctl_get_line_coding</span></span>

<span data-ttu-id="26363-1487">**アイコン** ![ホスト クラス CDC ACM IOCTL 伝送路符号化取得アイコン](./media/user-guide/usbx-events/image95.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1487">**Icon** ![Host Class C D C A C M I O C T L Get Line Coding icon](./media/user-guide/usbx-events/image95.png)</span></span>

<span data-ttu-id="26363-1488">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1488">**Description**</span></span>

<span data-ttu-id="26363-1489">USBX ホスト クラス CDC ACM IOCTL 伝送路符号化取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1489">This event represents a USBX Host Class Cdc Acm Ioctl Get Line Coding Event.</span></span>

<span data-ttu-id="26363-1490">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1490">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1491">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1491">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1492">情報フィールド 2: パラメーター。</span><span class="sxs-lookup"><span data-stu-id="26363-1492">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="26363-1493">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1493">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1494">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1494">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-notification-callback"></a><span data-ttu-id="26363-1495">ホスト クラス CDC ACM IOCTL 通知コールバック</span><span class="sxs-lookup"><span data-stu-id="26363-1495">Host Class Cdc Acm Ioctl Notification Callback</span></span>

#### <a name="ux_host_class_cdc_acm_ioctl_notification_callback"></a><span data-ttu-id="26363-1496">ux_host_class_cdc_acm_ioctl_notification_callback</span><span class="sxs-lookup"><span data-stu-id="26363-1496">ux_host_class_cdc_acm_ioctl_notification_callback</span></span>

<span data-ttu-id="26363-1497">**アイコン** ![ホスト クラス CDC ACM IOCTL 通知コールバック アイコン](./media/user-guide/usbx-events/image96.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1497">**Icon** ![Host Class C D C A C M I O C T L Notification Callback icon](./media/user-guide/usbx-events/image96.png)</span></span>

<span data-ttu-id="26363-1498">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1498">**Description**</span></span>

<span data-ttu-id="26363-1499">USBX ホスト クラス CDC ACM IOCTL 通知コールバック イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1499">This event represents a USBX Host Class Cdc Acm Ioctl Notification Callback Event.</span></span>

<span data-ttu-id="26363-1500">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1500">**Information Fields**</span></span>

- <span data-ttu-id="26363-1501">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1501">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1502">情報フィールド 2: パラメーター。</span><span class="sxs-lookup"><span data-stu-id="26363-1502">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="26363-1503">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1503">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1504">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1504">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-send-break"></a><span data-ttu-id="26363-1505">ホスト クラス CDC ACM IOCTL ブレーク送信</span><span class="sxs-lookup"><span data-stu-id="26363-1505">Host Class Cdc Acm Ioctl Send Break</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_send_break"></a><span data-ttu-id="26363-1506">ux_host_class_cdc_acm_ioctl_send_break</span><span class="sxs-lookup"><span data-stu-id="26363-1506">ux_host_class_cdc_acm_ioctl_send_break</span></span>

<span data-ttu-id="26363-1507">**アイコン** ![ホスト クラス CDC ACM IOCTL ブレーク送信アイコン](./media/user-guide/usbx-events/image97.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1507">**Icon** ![Host Class C D C A C M I O C T L Send Break icon](./media/user-guide/usbx-events/image97.png)</span></span>

<span data-ttu-id="26363-1508">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1508">**Description**</span></span>

<span data-ttu-id="26363-1509">USBX ホスト クラス CDC ACM IOCTL ブレーク送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1509">This event represents a USBX Host Class Cdc Acm Ioctl Send Break Event.</span></span>

<span data-ttu-id="26363-1510">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1510">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1511">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1511">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1512">情報フィールド 2: パラメーター。</span><span class="sxs-lookup"><span data-stu-id="26363-1512">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="26363-1513">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1513">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1514">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1514">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-set-line-coding"></a><span data-ttu-id="26363-1515">ホスト クラス CDC ACM IOCTL 伝送路符号化設定</span><span class="sxs-lookup"><span data-stu-id="26363-1515">Host Class Cdc Acm Ioctl Set Line Coding</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_coding"></a><span data-ttu-id="26363-1516">ux_host_class_cdc_acm_ioctl_set_line_coding</span><span class="sxs-lookup"><span data-stu-id="26363-1516">ux_host_class_cdc_acm_ioctl_set_line_coding</span></span>

<span data-ttu-id="26363-1517">**アイコン** ![ホスト クラス CDC ACM IOCTL 伝送路符号化設定アイコン](./media/user-guide/usbx-events/image97.png) icon](./media/user-guide/usbx-events/image98.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1517">**Icon** ![The Host Class C D C A C M I O C T L Set Line Coding icon](./media/user-guide/usbx-events/image97.png) icon](./media/user-guide/usbx-events/image98.png)</span></span>

<span data-ttu-id="26363-1518">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1518">**Description**</span></span>

<span data-ttu-id="26363-1519">USBX ホスト クラス CDC ACM IOCTL 伝送路符号化設定イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1519">This event represents a USBX Host Class Cdc Acm Ioctl Set Line Coding Event.</span></span>

<span data-ttu-id="26363-1520">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1520">**Information Fields**</span></span>

- <span data-ttu-id="26363-1521">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1521">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1522">情報フィールド 2: パラメーター。</span><span class="sxs-lookup"><span data-stu-id="26363-1522">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="26363-1523">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1523">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1524">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1524">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-set-line-state"></a><span data-ttu-id="26363-1525">ホスト クラス CDC ACM IOCTL 伝送路状態設定</span><span class="sxs-lookup"><span data-stu-id="26363-1525">Host Class Cdc Acm Ioctl Set Line State</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_state"></a><span data-ttu-id="26363-1526">ux_host_class_cdc_acm_ioctl_set_line_state</span><span class="sxs-lookup"><span data-stu-id="26363-1526">ux_host_class_cdc_acm_ioctl_set_line_state</span></span>

<span data-ttu-id="26363-1527">**アイコン** ![ホスト クラス CDC ACM IOCTL 伝送路状態設定アイコン](./media/user-guide/usbx-events/image99.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1527">**Icon** ![Host Class C D C A C M I O C T L Set Line State icon](./media/user-guide/usbx-events/image99.png)</span></span>

<span data-ttu-id="26363-1528">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1528">**Description**</span></span>

<span data-ttu-id="26363-1529">USBX ホスト クラス CDC ACM IOCTL 伝送路状態設定イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1529">This event represents a USBX Host Class Cdc Acm Ioctl Set Line State Event.</span></span>

<span data-ttu-id="26363-1530">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1530">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1531">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1531">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1532">情報フィールド 2: パラメーター。</span><span class="sxs-lookup"><span data-stu-id="26363-1532">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="26363-1533">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1533">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1534">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1534">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-read"></a><span data-ttu-id="26363-1535">ホスト クラス CDC ACM 読み取り</span><span class="sxs-lookup"><span data-stu-id="26363-1535">Host Class Cdc Acm Read</span></span> 

#### <a name="ux_host_class_cdc_acm_read"></a><span data-ttu-id="26363-1536">ux_host_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="26363-1536">ux_host_class_cdc_acm_read</span></span>

<span data-ttu-id="26363-1537">**アイコン** ![ホスト クラス CDC ACM 読み取りアイコン](./media/user-guide/usbx-events/image100.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1537">**Icon** ![Host Class C D C A C M Read icon](./media/user-guide/usbx-events/image100.png)</span></span>

<span data-ttu-id="26363-1538">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1538">**Description**</span></span>

<span data-ttu-id="26363-1539">USBX ホスト クラス CDC ACM 読み取りイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1539">This event represents a USBX Host Class Cdc Acm Read Event.</span></span>

<span data-ttu-id="26363-1540">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1540">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1541">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1541">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1542">情報フィールド 2: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-1542">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="26363-1543">情報フィールド 3: 要求された長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-1543">Info Field 3: Requested Length.</span></span>
- <span data-ttu-id="26363-1544">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1544">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-reception-start"></a><span data-ttu-id="26363-1545">ホスト クラス CDC ACM 受信開始</span><span class="sxs-lookup"><span data-stu-id="26363-1545">Host Class Cdc Acm Reception Start</span></span> 

#### <a name="ux_host_class_cdc_acm_reception_start"></a><span data-ttu-id="26363-1546">ux_host_class_cdc_acm_reception_start</span><span class="sxs-lookup"><span data-stu-id="26363-1546">ux_host_class_cdc_acm_reception_start</span></span>

<span data-ttu-id="26363-1547">**アイコン** ![ホスト クラス CDC ACM 受信開始アイコン](./media/user-guide/usbx-events/image101.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1547">**Icon** ![Host Class C D C A C M Reception Start icon](./media/user-guide/usbx-events/image101.png)</span></span>

<span data-ttu-id="26363-1548">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1548">**Description**</span></span>

<span data-ttu-id="26363-1549">USBX ホスト クラス CDC ACM 受信開始イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1549">This event represents a USBX Host Class Cdc Acm Reception Start Event.</span></span>

<span data-ttu-id="26363-1550">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1550">**Information Fields**</span></span>

- <span data-ttu-id="26363-1551">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1551">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1552">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1552">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1553">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1553">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1554">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1554">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-reception-stop"></a><span data-ttu-id="26363-1555">ホスト クラス CDC ACM 受信停止</span><span class="sxs-lookup"><span data-stu-id="26363-1555">Host Class Cdc Acm Reception Stop</span></span> 

#### <a name="ux_host_class_cdc_acm_reception_stop"></a><span data-ttu-id="26363-1556">ux_host_class_cdc_acm_reception_stop</span><span class="sxs-lookup"><span data-stu-id="26363-1556">ux_host_class_cdc_acm_reception_stop</span></span>

<span data-ttu-id="26363-1557">**アイコン** ![ホスト クラス CDC ACM 受信停止アイコン](./media/user-guide/usbx-events/image102.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1557">**Icon** ![Host Class C D C A C M Reception Stop icon](./media/user-guide/usbx-events/image102.png)</span></span>

<span data-ttu-id="26363-1558">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1558">**Description**</span></span>

<span data-ttu-id="26363-1559">USBX ホスト クラス CDC ACM 受信停止イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1559">This event represents a USBX Host Class Cdc Acm Reception Stop Event.</span></span>

<span data-ttu-id="26363-1560">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1560">**Information Fields**</span></span>

- <span data-ttu-id="26363-1561">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1561">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1562">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1562">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1563">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1563">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-write"></a><span data-ttu-id="26363-1564">ホスト クラス CDC ACM 書き込み</span><span class="sxs-lookup"><span data-stu-id="26363-1564">Host Class Cdc Acm Write</span></span> 

#### <a name="ux_host_class_acm_write"></a><span data-ttu-id="26363-1565">ux_host_class_acm_write</span><span class="sxs-lookup"><span data-stu-id="26363-1565">ux_host_class_acm_write</span></span>

<span data-ttu-id="26363-1566">**アイコン** ![ホスト クラス CDC ACM 書き込みアイコン](./media/user-guide/usbx-events/image103.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1566">**Icon** ![Host Class C D C A C M Write icon](./media/user-guide/usbx-events/image103.png)</span></span>

<span data-ttu-id="26363-1567">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1567">**Description**</span></span>

<span data-ttu-id="26363-1568">USBX ホスト クラス CDC ACM 書き込みイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1568">This event represents a USBX Host Class Cdc Acm Write Event.</span></span>

<span data-ttu-id="26363-1569">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1569">**Information Fields**</span></span>

- <span data-ttu-id="26363-1570">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1570">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1571">情報フィールド 2: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-1571">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="26363-1572">情報フィールド 3: 要求された長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-1572">Info Field 3: Requested Length.</span></span>
- <span data-ttu-id="26363-1573">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1573">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-activate"></a><span data-ttu-id="26363-1574">ホスト クラス DPUMP アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1574">Host Class Dpump Activate</span></span> 

#### <a name="ux_host_class_dpump_activate"></a><span data-ttu-id="26363-1575">ux_host_class_dpump_activate</span><span class="sxs-lookup"><span data-stu-id="26363-1575">ux_host_class_dpump_activate</span></span>

<span data-ttu-id="26363-1576">**アイコン** ![ホスト クラス DPUMP アクティブ化アイコン](./media/user-guide/usbx-events/image104.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1576">**Icon** ![Host Class Dpump Activate icon](./media/user-guide/usbx-events/image104.png)</span></span>

<span data-ttu-id="26363-1577">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1577">**Description**</span></span>

<span data-ttu-id="26363-1578">USBX ホスト クラス DPUMP アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1578">This event represents a USBX Host Class Dpump Activate Event.</span></span>

<span data-ttu-id="26363-1579">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1579">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1580">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1580">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1581">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1581">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1582">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1582">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1583">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1583">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-deactivate"></a><span data-ttu-id="26363-1584">ホスト クラス DPUMP 非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1584">Host Class Dpump Deactivate</span></span> 

#### <a name="ux_host_class_dpump_deactivate"></a><span data-ttu-id="26363-1585">ux_host_class_dpump_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-1585">ux_host_class_dpump_deactivate</span></span>

<span data-ttu-id="26363-1586">**アイコン** ![ホスト クラス DPUMP 非アクティブ化アイコン](./media/user-guide/usbx-events/image105.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1586">**Icon** ![Host Class Dpump Deactivate icon](./media/user-guide/usbx-events/image105.png)</span></span>

<span data-ttu-id="26363-1587">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1587">**Description**</span></span>

<span data-ttu-id="26363-1588">USBX ホスト クラス DPUMP 非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1588">This event represents a USBX Host Class Dpump Deactivate Event.</span></span>

<span data-ttu-id="26363-1589">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1589">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1590">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1590">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1591">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1591">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1592">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1592">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1593">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1593">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-read"></a><span data-ttu-id="26363-1594">ホスト クラス DPUMP 読み取り</span><span class="sxs-lookup"><span data-stu-id="26363-1594">Host Class Dpump Read</span></span> 

#### <a name="ux_host_class_dpump_read"></a><span data-ttu-id="26363-1595">ux_host_class_dpump_read</span><span class="sxs-lookup"><span data-stu-id="26363-1595">ux_host_class_dpump_read</span></span>

<span data-ttu-id="26363-1596">**アイコン** ![ホスト クラス DPUMP 読み取りアイコン](./media/user-guide/usbx-events/image106.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1596">**Icon** ![Host Class Dpump Read icon](./media/user-guide/usbx-events/image106.png)</span></span>

<span data-ttu-id="26363-1597">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1597">**Description**</span></span>

<span data-ttu-id="26363-1598">USBX ホスト クラス DPUMP 読み取りイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1598">This event represents a USBX Host Class Dpump Read Event.</span></span>

<span data-ttu-id="26363-1599">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1599">**Information Fields**</span></span>

- <span data-ttu-id="26363-1600">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1600">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1601">情報フィールド 2: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-1601">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="26363-1602">情報フィールド 3: 要求された長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-1602">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="26363-1603">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1603">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-write"></a><span data-ttu-id="26363-1604">ホスト クラス DPUMP 書き込み</span><span class="sxs-lookup"><span data-stu-id="26363-1604">Host Class Dpump Write</span></span> 

#### <a name="ux_host_class_dpump_write"></a><span data-ttu-id="26363-1605">ux_host_class_dpump_write</span><span class="sxs-lookup"><span data-stu-id="26363-1605">ux_host_class_dpump_write</span></span>

<span data-ttu-id="26363-1606">**アイコン** ![ホスト クラス DPUMP 書き込みアイコン](./media/user-guide/usbx-events/image107.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1606">**Icon** ![Host Class Dpump Write icon](./media/user-guide/usbx-events/image107.png)</span></span>

<span data-ttu-id="26363-1607">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1607">**Description**</span></span>

<span data-ttu-id="26363-1608">USBX ホスト クラス DPUMP 書き込みイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1608">This event represents a USBX Host Class Dpump Write Event.</span></span>

<span data-ttu-id="26363-1609">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1609">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1610">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1610">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1611">情報フィールド 2: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-1611">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="26363-1612">情報フィールド 3: 要求された長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-1612">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="26363-1613">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1613">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-activate"></a><span data-ttu-id="26363-1614">ホスト クラス HID アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1614">Host Class Hid Activate</span></span> 

#### <a name="ux_host_class_hid_activate"></a><span data-ttu-id="26363-1615">ux_host_class_hid_activate</span><span class="sxs-lookup"><span data-stu-id="26363-1615">ux_host_class_hid_activate</span></span>

<span data-ttu-id="26363-1616">**アイコン** ![ホスト クラス HID アクティブ化アイコン](./media/user-guide/usbx-events/image108.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1616">**Icon** ![Host Class Hid Activate icon](./media/user-guide/usbx-events/image108.png)</span></span>

<span data-ttu-id="26363-1617">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1617">**Description**</span></span>

<span data-ttu-id="26363-1618">USBX ホスト クラス HID アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1618">This event represents a USBX Host Class Hid Activate Event.</span></span>

<span data-ttu-id="26363-1619">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1619">**Information Fields**</span></span>

- <span data-ttu-id="26363-1620">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1620">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1621">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1621">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1622">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1622">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1623">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1623">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-client-register"></a><span data-ttu-id="26363-1624">ホスト クラス HID クライアント登録</span><span class="sxs-lookup"><span data-stu-id="26363-1624">Host Class Hid Client Register</span></span> 

#### <a name="ux_host_class_hid_client_register"></a><span data-ttu-id="26363-1625">ux_host_class_hid_client_register</span><span class="sxs-lookup"><span data-stu-id="26363-1625">ux_host_class_hid_client_register</span></span>

<span data-ttu-id="26363-1626">**アイコン** ![ホスト クラス HID クライアント登録アイコン](./media/user-guide/usbx-events/image109.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1626">**Icon** ![Host Class Hid Client Register icon](./media/user-guide/usbx-events/image109.png)</span></span>

<span data-ttu-id="26363-1627">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1627">**Description**</span></span>

<span data-ttu-id="26363-1628">USBX ホスト クラス HID クライアント登録イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1628">This event represents a USBX Host Class Hid Client Register Event.</span></span>

<span data-ttu-id="26363-1629">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1629">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1630">情報フィールド 1: HID クライアント名。</span><span class="sxs-lookup"><span data-stu-id="26363-1630">Info Field 1: Hid client name.</span></span>
- <span data-ttu-id="26363-1631">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1631">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1632">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1632">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1633">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1633">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-deactivate"></a><span data-ttu-id="26363-1634">ホスト クラス HID 非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1634">Host Class Hid Deactivate</span></span> 

#### <a name="ux_host_class_hid_deactivate"></a><span data-ttu-id="26363-1635">ux_host_class_hid_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-1635">ux_host_class_hid_deactivate</span></span>

<span data-ttu-id="26363-1636">**アイコン** ![ホスト クラス HID 非アクティブ化アイコン](./media/user-guide/usbx-events/image110.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1636">**Icon** ![Host Class Hid Deactivate icon](./media/user-guide/usbx-events/image110.png)</span></span>

<span data-ttu-id="26363-1637">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1637">**Description**</span></span>

<span data-ttu-id="26363-1638">USBX ホスト クラス HID 非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1638">This event represents a USBX Host Class Hid Deactivate Event.</span></span>

<span data-ttu-id="26363-1639">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1639">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1640">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1640">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1641">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1641">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1642">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1642">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1643">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1643">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-idle-get"></a><span data-ttu-id="26363-1644">ホスト クラス HID アイドル取得</span><span class="sxs-lookup"><span data-stu-id="26363-1644">Host Class Hid Idle Get</span></span> 

#### <a name="ux_host_class_hid_idle_get"></a><span data-ttu-id="26363-1645">ux_host_class_hid_idle_get</span><span class="sxs-lookup"><span data-stu-id="26363-1645">ux_host_class_hid_idle_get</span></span>

<span data-ttu-id="26363-1646">**アイコン** ![ホスト クラス HID アイドル取得アイコン](./media/user-guide/usbx-events/image111.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1646">**Icon** ![Host Class Hid Idle Get icon](./media/user-guide/usbx-events/image111.png)</span></span>

<span data-ttu-id="26363-1647">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1647">**Description**</span></span>

<span data-ttu-id="26363-1648">USBX ホスト クラス HID アイドル取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1648">This event represents a USBX Host Class Hid Idle Get Event.</span></span>

<span data-ttu-id="26363-1649">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1649">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1650">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1650">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1651">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1651">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1652">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1652">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1653">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1653">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-idle-set"></a><span data-ttu-id="26363-1654">ホスト クラス HID アイドル設定</span><span class="sxs-lookup"><span data-stu-id="26363-1654">Host Class Hid Idle Set</span></span> 

#### <a name="ux_host_class_hid_idle_set"></a><span data-ttu-id="26363-1655">ux_host_class_hid_idle_set</span><span class="sxs-lookup"><span data-stu-id="26363-1655">ux_host_class_hid_idle_set</span></span>

<span data-ttu-id="26363-1656">**アイコン** ![ホスト クラス HID アイドル設定アイコン](./media/user-guide/usbx-events/image112.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1656">**Icon** ![Host Class Hid Idle Set icon](./media/user-guide/usbx-events/image112.png)</span></span>

<span data-ttu-id="26363-1657">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1657">**Description**</span></span>

<span data-ttu-id="26363-1658">USBX ホスト クラス HID アイドル設定イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1658">This event represents a USBX Host Class Hid Idle Set Event.</span></span>

<span data-ttu-id="26363-1659">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1659">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1660">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1660">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1661">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1661">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1662">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1662">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1663">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1663">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-keyboard-activate"></a><span data-ttu-id="26363-1664">ホスト クラス HID キーボード アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1664">Host Class Hid Keyboard Activate</span></span> 

#### <a name="ux_host_class_hid_keyboard_activate"></a><span data-ttu-id="26363-1665">ux_host_class_hid_keyboard_activate</span><span class="sxs-lookup"><span data-stu-id="26363-1665">ux_host_class_hid_keyboard_activate</span></span>

<span data-ttu-id="26363-1666">**アイコン** ![ホスト クラス HID キーボード アクティブ化アイコン](./media/user-guide/usbx-events/image113.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1666">**Icon** ![Host Class Hid Keyboard Activate icon](./media/user-guide/usbx-events/image113.png)</span></span>

<span data-ttu-id="26363-1667">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1667">**Description**</span></span>

<span data-ttu-id="26363-1668">USBX ホスト クラス HID キーボード アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1668">This event represents a USBX Host Class Hid Keyboard Activate Event.</span></span>

<span data-ttu-id="26363-1669">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1669">**Information Fields**</span></span>
<p><span data-ttu-id="26363-1670">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1670">Info Field 1: Class instance.</span></span>
<p><span data-ttu-id="26363-1671">情報フィールド 2: HID クライアント インスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1671">Info Field 2: Hid client instance.</span></span>
<p><span data-ttu-id="26363-1672">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1672">Info Field 3: Not used.</span></span>
<p><span data-ttu-id="26363-1673">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1673">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-keyboard-deactivate"></a><span data-ttu-id="26363-1674">ホスト クラス HID キーボード非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1674">Host Class Hid Keyboard Deactivate</span></span> 

#### <a name="ux_host_class_hid_keyboard_deactivate"></a><span data-ttu-id="26363-1675">ux_host_class_hid_keyboard_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-1675">ux_host_class_hid_keyboard_deactivate</span></span>

<span data-ttu-id="26363-1676">**アイコン** ![ホスト クラス HID キーボード非アクティブ化アイコン](./media/user-guide/usbx-events/image114.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1676">**Icon** ![Host Class Hid Keyboard Deactivate icon](./media/user-guide/usbx-events/image114.png)</span></span>

<span data-ttu-id="26363-1677">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1677">**Description**</span></span>

<span data-ttu-id="26363-1678">USBX ホスト クラス HID キーボード非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1678">This event represents a USBX Host Class Hid Keyboard Deactivate Event.</span></span>

<span data-ttu-id="26363-1679">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1679">**Information Fields**</span></span>

- <span data-ttu-id="26363-1680">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1680">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1681">情報フィールド 2: HID クライアント インスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1681">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="26363-1682">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1682">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1683">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1683">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-mouse-activate"></a><span data-ttu-id="26363-1684">ホスト クラス HID マウス アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1684">Host Class Hid Mouse Activate</span></span> 

#### <a name="ux_host_class_hid_mouse_activate"></a><span data-ttu-id="26363-1685">ux_host_class_hid_mouse_activate</span><span class="sxs-lookup"><span data-stu-id="26363-1685">ux_host_class_hid_mouse_activate</span></span>

<span data-ttu-id="26363-1686">**アイコン** ![ホスト クラス HID マウス アクティブ化アイコン](./media/user-guide/usbx-events/image115.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1686">**Icon** ![Host Class Hid Mouse Activate icon](./media/user-guide/usbx-events/image115.png)</span></span>

<span data-ttu-id="26363-1687">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1687">**Description**</span></span>

<span data-ttu-id="26363-1688">USBX ホスト クラス HID マウス アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1688">This event represents a USBX Host Class Hid Mouse Activate Event.</span></span>

<span data-ttu-id="26363-1689">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1689">**Information Fields**</span></span>

- <span data-ttu-id="26363-1690">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1690">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1691">情報フィールド 2: HID クライアント インスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1691">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="26363-1692">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1692">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1693">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1693">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-mouse-deactivate"></a><span data-ttu-id="26363-1694">ホストクラス HID マウス非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1694">Host Class Hid Mouse Deactivate</span></span> 

#### <a name="ux_host_class_hid_mouse_deactivate"></a><span data-ttu-id="26363-1695">ux_host_class_hid_mouse_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-1695">ux_host_class_hid_mouse_deactivate</span></span>

<span data-ttu-id="26363-1696">**アイコン** ![ホスト クラス HID マウス非アクティブ化アイコン](./media/user-guide/usbx-events/image116.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1696">**Icon** ![Host Class Hid Mouse Deactivate icon](./media/user-guide/usbx-events/image116.png)</span></span>

<span data-ttu-id="26363-1697">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1697">**Description**</span></span>

- <span data-ttu-id="26363-1698">USBX ホスト クラス HID マウス非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1698">This event represents a USBX Host Class Hid Mouse Deactivate Event.</span></span>

<span data-ttu-id="26363-1699">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1699">**Information Fields**</span></span>

- <span data-ttu-id="26363-1700">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1700">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1701">情報フィールド 2: HID クライアント インスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1701">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="26363-1702">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1702">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1703">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1703">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-remote-control-activate"></a><span data-ttu-id="26363-1704">ホスト クラス HID リモート制御アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1704">Host Class Hid Remote Control Activate</span></span> 

#### <a name="ux_host_class_hid_remote_control_activate"></a><span data-ttu-id="26363-1705">ux_host_class_hid_remote_control_activate</span><span class="sxs-lookup"><span data-stu-id="26363-1705">ux_host_class_hid_remote_control_activate</span></span>

<span data-ttu-id="26363-1706">**アイコン** ![ホスト クラス HID リモート制御アクティブ化アイコン](./media/user-guide/usbx-events/image117.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1706">**Icon** ![Host Class Hid Remote Control Activate icon](./media/user-guide/usbx-events/image117.png)</span></span>

<span data-ttu-id="26363-1707">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1707">**Description**</span></span>

<span data-ttu-id="26363-1708">USBX ホスト クラス HID リモート制御アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1708">This event represents a USBX Host Class Hid Remote Control Activate Event.</span></span>

<span data-ttu-id="26363-1709">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1709">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1710">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1710">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1711">情報フィールド 2: HID クライアント インスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1711">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="26363-1712">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1712">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1713">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1713">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-remote-control-deactivate"></a><span data-ttu-id="26363-1714">ホスト クラス HID リモート制御非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1714">Host Class Hid Remote Control Deactivate</span></span> 

#### <a name="ux_host_class_hid_remote_control_deactivate"></a><span data-ttu-id="26363-1715">ux_host_class_hid_remote_control_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-1715">ux_host_class_hid_remote_control_deactivate</span></span>

<span data-ttu-id="26363-1716">**アイコン** ![ホスト クラス HID リモート制御非アクティブ化アイコン](./media/user-guide/usbx-events/image118.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1716">**Icon** ![Host Class Hid Remote Control Deactivate icon](./media/user-guide/usbx-events/image118.png)</span></span>

<span data-ttu-id="26363-1717">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1717">**Description**</span></span>

<span data-ttu-id="26363-1718">USBX ホスト クラス HID リモート制御非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1718">This event represents a USBX Host Class Hid Remote Control Deactivate Event.</span></span>

<span data-ttu-id="26363-1719">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1719">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1720">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1720">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1721">情報フィールド 2: HID クライアント インスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1721">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="26363-1722">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1722">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1723">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1723">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-report-get"></a><span data-ttu-id="26363-1724">ホスト クラス HID レポート取得</span><span class="sxs-lookup"><span data-stu-id="26363-1724">Host Class Hid Report Get</span></span> 

#### <a name="ux_host_class_hid_report_get"></a><span data-ttu-id="26363-1725">ux_host_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="26363-1725">ux_host_class_hid_report_get</span></span>

<span data-ttu-id="26363-1726">**アイコン** ![ホスト クラス HID レポート取得アイコン](./media/user-guide/usbx-events/image119.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1726">**Icon** ![Host Class Hid Report Get icon](./media/user-guide/usbx-events/image119.png)</span></span>

<span data-ttu-id="26363-1727">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1727">**Description**</span></span>

<span data-ttu-id="26363-1728">USBX ホスト クラス HID レポート取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1728">This event represents a USBX Host Class Hid Report Get.</span></span>

<span data-ttu-id="26363-1729">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1729">**Information Fields**</span></span>

- <span data-ttu-id="26363-1730">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1730">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1731">情報フィールド 2: クライアントのレポート。</span><span class="sxs-lookup"><span data-stu-id="26363-1731">Info Field 2: Client report.</span></span>
- <span data-ttu-id="26363-1732">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1732">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1733">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1733">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-report-set"></a><span data-ttu-id="26363-1734">ホスト クラス HID レポート設定</span><span class="sxs-lookup"><span data-stu-id="26363-1734">Host Class Hid Report Set</span></span> 

#### <a name="ux_host_class_hid_report_set"></a><span data-ttu-id="26363-1735">ux_host_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="26363-1735">ux_host_class_hid_report_set</span></span>

<span data-ttu-id="26363-1736">**アイコン** ![ホスト クラス HID レポート設定アイコン](./media/user-guide/usbx-events/image120.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1736">**Icon** ![Host Class Hid Report Set icon](./media/user-guide/usbx-events/image120.png)</span></span>

<span data-ttu-id="26363-1737">**説明** USBX ホスト クラス HID レポート設定イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1737">**Description** This event represents a USBX Host Class Hid Report Set.</span></span>

<span data-ttu-id="26363-1738">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1738">**Information Fields**</span></span>

- <span data-ttu-id="26363-1739">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1739">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1740">情報フィールド 2: クライアントのレポート。</span><span class="sxs-lookup"><span data-stu-id="26363-1740">Info Field 2: Client report.</span></span>
- <span data-ttu-id="26363-1741">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1741">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1742">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1742">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-activate"></a><span data-ttu-id="26363-1743">ホスト クラス Hub アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1743">Host Class Hub Activate</span></span> 

#### <a name="ux_host_class_hub_activate"></a><span data-ttu-id="26363-1744">ux_host_class_hub_activate</span><span class="sxs-lookup"><span data-stu-id="26363-1744">ux_host_class_hub_activate</span></span>

<span data-ttu-id="26363-1745">**アイコン** ![ホスト クラス Hub アクティブ化アイコン](./media/user-guide/usbx-events/image121.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1745">**Icon** ![Host Class Hub Activate icon](./media/user-guide/usbx-events/image121.png)</span></span>

<span data-ttu-id="26363-1746">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1746">**Description**</span></span>

<span data-ttu-id="26363-1747">USBX ホスト クラス Hub アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1747">This event represents a USBX Host Class Hub Activate Event.</span></span>

<span data-ttu-id="26363-1748">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1748">**Information Fields**</span></span> 

- <span data-ttu-id="26363-1749">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1749">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1750">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1750">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1751">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1751">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1752">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1752">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-change-detect"></a><span data-ttu-id="26363-1753">ホスト クラス Hub 変更検出</span><span class="sxs-lookup"><span data-stu-id="26363-1753">Host Class Hub Change Detect</span></span> 

#### <a name="ux_host_class_hub_change_detect"></a><span data-ttu-id="26363-1754">ux_host_class_hub_change_detect</span><span class="sxs-lookup"><span data-stu-id="26363-1754">ux_host_class_hub_change_detect</span></span>

<span data-ttu-id="26363-1755">**アイコン** ![ホスト クラス Hub 変更検出アイコン](./media/user-guide/usbx-events/image122.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1755">**Icon** ![Host Class Hub Change Detect icon](./media/user-guide/usbx-events/image122.png)</span></span>

<span data-ttu-id="26363-1756">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1756">**Description**</span></span>

<span data-ttu-id="26363-1757">USBX ホスト クラス Hub 変更検出イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1757">This event represents a USBX Host Class Hub Change Detect Event.</span></span>

<span data-ttu-id="26363-1758">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1758">**Information Fields**</span></span>

- <span data-ttu-id="26363-1759">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1759">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1760">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1760">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1761">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1761">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1762">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1762">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-deactivate"></a><span data-ttu-id="26363-1763">ホスト クラス Hub 非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1763">Host Class Hub Deactivate</span></span> 

#### <a name="ux_host_class_hub_deactivate"></a><span data-ttu-id="26363-1764">ux_host_class_hub_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-1764">ux_host_class_hub_deactivate</span></span>

<span data-ttu-id="26363-1765">**アイコン** ![ホスト クラス Hub 非アクティブ化アイコン](./media/user-guide/usbx-events/image123.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1765">**Icon** ![Host Class Hub Deactivate icon](./media/user-guide/usbx-events/image123.png)</span></span>

<span data-ttu-id="26363-1766">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1766">**Description**</span></span>

<span data-ttu-id="26363-1767">USBX ホスト クラス Hub 非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1767">This event represents a USBX Host Class Hub Deactivate Event.</span></span>

<span data-ttu-id="26363-1768">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1768">**Information Fields**</span></span>

- <span data-ttu-id="26363-1769">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1769">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1770">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1770">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1771">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1771">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1772">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1772">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-connection-process"></a><span data-ttu-id="26363-1773">ホスト クラス Hub ポート変更接続処理</span><span class="sxs-lookup"><span data-stu-id="26363-1773">Host Class Hub Port Change Connection Process</span></span> 

#### <a name="ux_host_class_hub_change_connection_process"></a><span data-ttu-id="26363-1774">ux_host_class_hub_change_connection_process</span><span class="sxs-lookup"><span data-stu-id="26363-1774">ux_host_class_hub_change_connection_process</span></span>

<span data-ttu-id="26363-1775">**アイコン** ![ホスト クラス Hub ポート変更接続処理アイコン](./media/user-guide/usbx-events/image124.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1775">**Icon** ![Host Class Hub Port Change Connection Process icon](./media/user-guide/usbx-events/image124.png)</span></span>

<span data-ttu-id="26363-1776">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1776">**Description**</span></span>

<span data-ttu-id="26363-1777">USBX ホスト クラス Hub ポート変更接続処理イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1777">This event represents a USBX Host Class Hub Port Change Connection Process Event.</span></span>

<span data-ttu-id="26363-1778">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1778">**Information Fields**</span></span>

- <span data-ttu-id="26363-1779">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1779">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1780">情報フィールド 2: ポート。</span><span class="sxs-lookup"><span data-stu-id="26363-1780">Info Field 2: Port.</span></span>
- <span data-ttu-id="26363-1781">情報フィールド 3: ポートの状態。</span><span class="sxs-lookup"><span data-stu-id="26363-1781">Info Field 3: Port status.</span></span>
- <span data-ttu-id="26363-1782">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1782">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-enable-process"></a><span data-ttu-id="26363-1783">ホスト クラス Hub ポート変更有効化処理</span><span class="sxs-lookup"><span data-stu-id="26363-1783">Host Class Hub Port Change Enable Process</span></span> 

#### <a name="ux_host_class_hub_port_change_enable_process"></a><span data-ttu-id="26363-1784">ux_host_class_hub_port_change_enable_process</span><span class="sxs-lookup"><span data-stu-id="26363-1784">ux_host_class_hub_port_change_enable_process</span></span>

<span data-ttu-id="26363-1785">**アイコン** ![ホスト クラス Hub ポート変更有効化処理アイコン](./media/user-guide/usbx-events/image125.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1785">**Icon** ![Host Class Hub Port Change Enable Process icon](./media/user-guide/usbx-events/image125.png)</span></span>

<span data-ttu-id="26363-1786">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1786">**Description**</span></span>

<span data-ttu-id="26363-1787">USBX ホスト クラス Hub ポート変更有効化処理イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1787">This event represents a USBX Host Class Hub Port Change Enable Process Event.</span></span>

<span data-ttu-id="26363-1788">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1788">**Information Fields**</span></span>

- <span data-ttu-id="26363-1789">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1789">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1790">情報フィールド 2: ポート。</span><span class="sxs-lookup"><span data-stu-id="26363-1790">Info Field 2: Port.</span></span>
- <span data-ttu-id="26363-1791">情報フィールド 3: ポートの状態。</span><span class="sxs-lookup"><span data-stu-id="26363-1791">Info Field 3: Port status.</span></span>
- <span data-ttu-id="26363-1792">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1792">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-over-current-process"></a><span data-ttu-id="26363-1793">ホスト クラス Hub ポート変更過電流処理</span><span class="sxs-lookup"><span data-stu-id="26363-1793">Host Class Hub Port Change Over Current Process</span></span> 

#### <a name="ux_host_class_hub_port_change_over_current_process"></a><span data-ttu-id="26363-1794">ux_host_class_hub_port_change_over_current_process</span><span class="sxs-lookup"><span data-stu-id="26363-1794">ux_host_class_hub_port_change_over_current_process</span></span>

<span data-ttu-id="26363-1795">**アイコン** ![ホスト クラス Hub ポート変更過電流処理アイコン](./media/user-guide/usbx-events/image126.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1795">**Icon** ![Host Class Hub Port Change Over Current Process icon](./media/user-guide/usbx-events/image126.png)</span></span>

<span data-ttu-id="26363-1796">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1796">**Description**</span></span>

<span data-ttu-id="26363-1797">nx_packet_allocate でパケットを割り当てるイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1797">This event represents allocating a packet via nx_packet_allocate.</span></span>

<span data-ttu-id="26363-1798">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1798">**Information Fields**</span></span>

- <span data-ttu-id="26363-1799">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1799">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1800">情報フィールド 2: ポート。</span><span class="sxs-lookup"><span data-stu-id="26363-1800">Info Field 2: Port.</span></span>
- <span data-ttu-id="26363-1801">情報フィールド 3: ポートの状態。</span><span class="sxs-lookup"><span data-stu-id="26363-1801">Info Field 3: Port status.</span></span>
- <span data-ttu-id="26363-1802">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1802">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-reset-process"></a><span data-ttu-id="26363-1803">ホスト クラス Hub ポート変更リセット処理</span><span class="sxs-lookup"><span data-stu-id="26363-1803">Host Class Hub Port Change Reset Process</span></span> 

#### <a name="ux_host_class_hub_port_change_reset_process"></a><span data-ttu-id="26363-1804">ux_host_class_hub_port_change_reset_process</span><span class="sxs-lookup"><span data-stu-id="26363-1804">ux_host_class_hub_port_change_reset_process</span></span>

<span data-ttu-id="26363-1805">**アイコン** ![ホスト クラス Hub ポート変更リセット処理アイコン](./media/user-guide/usbx-events/image127.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1805">**Icon** ![Host Class Hub Port Change Reset Process icon](./media/user-guide/usbx-events/image127.png)</span></span>

<span data-ttu-id="26363-1806">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1806">**Description**</span></span>

<span data-ttu-id="26363-1807">USBX ホスト クラス Hub ポート変更リセット処理イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1807">This event represents a USBX Host Class Hub Port Change Reset Process Event.</span></span>

<span data-ttu-id="26363-1808">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1808">**Information Fields**</span></span>

- <span data-ttu-id="26363-1809">情報フィールド 1: ハブ。</span><span class="sxs-lookup"><span data-stu-id="26363-1809">Info Field 1: Hub.</span></span> <span data-ttu-id="26363-1810">情報フィールド 2: ポート。</span><span class="sxs-lookup"><span data-stu-id="26363-1810">Info Field 2: Port.</span></span>
- <span data-ttu-id="26363-1811">情報フィールド 3: ポートの状態。</span><span class="sxs-lookup"><span data-stu-id="26363-1811">Info Field 3: Port status.</span></span>
- <span data-ttu-id="26363-1812">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1812">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-suspend-process"></a><span data-ttu-id="26363-1813">ホスト クラス Hub ポート変更中断処理</span><span class="sxs-lookup"><span data-stu-id="26363-1813">Host Class Hub Port Change Suspend Process</span></span> 

#### <a name="ux_host_class_hub_port_change_suspend_process"></a><span data-ttu-id="26363-1814">ux_host_class_hub_port_change_suspend_process</span><span class="sxs-lookup"><span data-stu-id="26363-1814">ux_host_class_hub_port_change_suspend_process</span></span>

<span data-ttu-id="26363-1815">**アイコン** ![ホスト クラス Hub ポート変更中断処理アイコン](./media/user-guide/usbx-events/image128.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1815">**Icon** ![Host Class Hub Port Change Suspend Process icon](./media/user-guide/usbx-events/image128.png)</span></span>

<span data-ttu-id="26363-1816">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1816">**Description**</span></span>

<span data-ttu-id="26363-1817">USBX ホスト クラス Hub ポート変更中断処理イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1817">This event represents a USBX Host Class Hub Port Change Suspend Process Event.</span></span>

<span data-ttu-id="26363-1818">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1818">**Information Fields**</span></span>

- <span data-ttu-id="26363-1819">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1819">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1820">情報フィールド 2: ポート。</span><span class="sxs-lookup"><span data-stu-id="26363-1820">Info Field 2: Port.</span></span>
- <span data-ttu-id="26363-1821">情報フィールド 3: ポートの状態。</span><span class="sxs-lookup"><span data-stu-id="26363-1821">Info Field 3: Port status.</span></span>
- <span data-ttu-id="26363-1822">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1822">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-activate"></a><span data-ttu-id="26363-1823">ホスト クラス PIMA アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1823">Host Class Pima Activate</span></span> 

#### <a name="ux_host_class_pima_activate"></a><span data-ttu-id="26363-1824">ux_host_class_pima_activate</span><span class="sxs-lookup"><span data-stu-id="26363-1824">ux_host_class_pima_activate</span></span>

<span data-ttu-id="26363-1825">**アイコン** ![ホスト クラス PIMA アクティブ化アイコン](./media/user-guide/usbx-events/image129.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1825">**Icon** ![Host Class Pima Activate icon](./media/user-guide/usbx-events/image129.png)</span></span>

<span data-ttu-id="26363-1826">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1826">**Description**</span></span>

<span data-ttu-id="26363-1827">USBX ホスト クラス PIMA アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1827">This event represents a USBX Host Class Pima Activate Event.</span></span>

<span data-ttu-id="26363-1828">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1828">**Information Fields**</span></span>

- <span data-ttu-id="26363-1829">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1829">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1830">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1830">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1831">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1831">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1832">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1832">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-deactivate"></a><span data-ttu-id="26363-1833">ホスト クラス PIMA 非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-1833">Host Class Pima Deactivate</span></span> 

#### <a name="ux_host_class_pima_deactivate"></a><span data-ttu-id="26363-1834">ux_host_class_pima_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-1834">ux_host_class_pima_deactivate</span></span>

<span data-ttu-id="26363-1835">**アイコン** ![ホスト クラス PIMA 非アクティブ化アイコン](./media/user-guide/usbx-events/image130.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1835">**Icon** ![Host Class Pima Deactivate icon](./media/user-guide/usbx-events/image130.png)</span></span>

<span data-ttu-id="26363-1836">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1836">**Description**</span></span>

<span data-ttu-id="26363-1837">USBX ホスト クラス PIMA 非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1837">This event represents a USBX Host Class Pima Deactivate Event.</span></span>

<span data-ttu-id="26363-1838">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1838">**Information Fields**</span></span>

- <span data-ttu-id="26363-1839">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1839">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1840">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1840">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1841">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1841">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1842">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1842">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-device-info-get"></a><span data-ttu-id="26363-1843">ホスト クラス PIMA デバイス情報取得</span><span class="sxs-lookup"><span data-stu-id="26363-1843">Host Class Pima Device Info Get</span></span> 

#### <a name="ux_host_class_pima_device_info_get"></a><span data-ttu-id="26363-1844">ux_host_class_pima_device_info_get</span><span class="sxs-lookup"><span data-stu-id="26363-1844">ux_host_class_pima_device_info_get</span></span>

<span data-ttu-id="26363-1845">**アイコン** ![ホスト クラス PIMA デバイス情報取得アイコン](./media/user-guide/usbx-events/image131.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1845">**Icon** ![Host Class Pima Device Info Get icon](./media/user-guide/usbx-events/image131.png)</span></span>

<span data-ttu-id="26363-1846">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1846">**Description**</span></span>

<span data-ttu-id="26363-1847">USBX ホスト クラス PIMA デバイス情報取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1847">This event represents a USBX Host Class Pima Device Info Get Event.</span></span>

<span data-ttu-id="26363-1848">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1848">**Information Fields**</span></span>

- <span data-ttu-id="26363-1849">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1849">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1850">情報フィールド 2: PIMA デバイス。</span><span class="sxs-lookup"><span data-stu-id="26363-1850">Info Field 2: Pima device.</span></span>
- <span data-ttu-id="26363-1851">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1851">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1852">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1852">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-device-reset"></a><span data-ttu-id="26363-1853">ホスト クラス PIMA デバイス リセット</span><span class="sxs-lookup"><span data-stu-id="26363-1853">Host Class Pima Device Reset</span></span> 

#### <a name="ux_host_class_pima_device_reset"></a><span data-ttu-id="26363-1854">ux_host_class_pima_device_reset</span><span class="sxs-lookup"><span data-stu-id="26363-1854">ux_host_class_pima_device_reset</span></span>

<span data-ttu-id="26363-1855">**アイコン** ![ホスト クラス PIMA デバイス リセット アイコン](./media/user-guide/usbx-events/image132.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1855">**Icon** ![Host Class Pima Device Reset icon](./media/user-guide/usbx-events/image132.png)</span></span>

<span data-ttu-id="26363-1856">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1856">**Description**</span></span>

<span data-ttu-id="26363-1857">USBX ホスト クラス PIMA デバイス リセット イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1857">This event represents a USBX Host Class Pima Device Reset Event.</span></span>

<span data-ttu-id="26363-1858">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1858">**Information Fields**</span></span>

- <span data-ttu-id="26363-1859">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1859">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1860">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1860">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1861">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1861">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1862">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1862">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-notification"></a><span data-ttu-id="26363-1863">ホスト クラス PIMA 通知</span><span class="sxs-lookup"><span data-stu-id="26363-1863">Host Class Pima Notification</span></span> 

#### <a name="ux_host_class_pima_notification"></a><span data-ttu-id="26363-1864">ux_host_class_pima_notification</span><span class="sxs-lookup"><span data-stu-id="26363-1864">ux_host_class_pima_notification</span></span>

<span data-ttu-id="26363-1865">**アイコン** ![ホスト クラス PIMA 通知アイコン](./media/user-guide/usbx-events/image133.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1865">**Icon** ![Host Class Pima Notification icon](./media/user-guide/usbx-events/image133.png)</span></span>

<span data-ttu-id="26363-1866">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1866">**Description**</span></span>

<span data-ttu-id="26363-1867">USBX ホスト クラス PIMA 通知イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1867">This event represents a USBX Host Class Pima Notification Event.</span></span>

<span data-ttu-id="26363-1868">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1868">**Information Fields**</span></span>

- <span data-ttu-id="26363-1869">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1869">Info Field 1: Class instance.</span></span> <span data-ttu-id="26363-1870">情報フィールド 2: イベント コード。</span><span class="sxs-lookup"><span data-stu-id="26363-1870">Info Field 2: Event code.</span></span>
- <span data-ttu-id="26363-1871">情報フィールド 3: トランザクション ID。</span><span class="sxs-lookup"><span data-stu-id="26363-1871">Info Field 3: Transaction ID.</span></span>
- <span data-ttu-id="26363-1872">情報フィールド 4: パラメーター 1。</span><span class="sxs-lookup"><span data-stu-id="26363-1872">Info Field 4: Parameter1.</span></span>

### <a name="host-class-pima-number-objects-get"></a><span data-ttu-id="26363-1873">ホスト クラス PIMA オブジェクト数取得</span><span class="sxs-lookup"><span data-stu-id="26363-1873">Host Class Pima Number Objects Get</span></span> 

#### <a name="ux_host_class_pima_number_objects_get"></a><span data-ttu-id="26363-1874">ux_host_class_pima_number_objects_get</span><span class="sxs-lookup"><span data-stu-id="26363-1874">ux_host_class_pima_number_objects_get</span></span>

<span data-ttu-id="26363-1875">**アイコン** ![ホスト クラス PIMA オブジェクト数取得アイコン](./media/user-guide/usbx-events/image134.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1875">**Icon** ![Host Class Pima Number Objects Get icon](./media/user-guide/usbx-events/image134.png)</span></span>

<span data-ttu-id="26363-1876">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1876">**Description**</span></span>

<span data-ttu-id="26363-1877">USBX ホスト クラス PIMA オブジェクト数取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1877">This event represents a USBX Host Class Pima Number Objects Get Event.</span></span>

<span data-ttu-id="26363-1878">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1878">**Information Fields**</span></span>

- <span data-ttu-id="26363-1879">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1879">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1880">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1880">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1881">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1881">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1882">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1882">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-close"></a><span data-ttu-id="26363-1883">ホスト クラス PIMA オブジェクト クローズ</span><span class="sxs-lookup"><span data-stu-id="26363-1883">Host Class Pima Object Close</span></span> 

#### <a name="ux_host_class_pima_object_close"></a><span data-ttu-id="26363-1884">ux_host_class_pima_object_close</span><span class="sxs-lookup"><span data-stu-id="26363-1884">ux_host_class_pima_object_close</span></span>

<span data-ttu-id="26363-1885">**アイコン** ![ホスト クラス PIMA オブジェクト クローズ アイコン](./media/user-guide/usbx-events/image135.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1885">**Icon** ![Host Class Pima Object Close icon](./media/user-guide/usbx-events/image135.png)</span></span>

<span data-ttu-id="26363-1886">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1886">**Description**</span></span>

<span data-ttu-id="26363-1887">USBX ホスト クラス PIMA オブジェクト クローズ イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1887">This event represents a USBX Host Class Pima Object Close Event.</span></span>

<span data-ttu-id="26363-1888">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1888">**Information Fields**</span></span>

- <span data-ttu-id="26363-1889">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1889">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1890">情報フィールド 2: オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="26363-1890">Info Field 2: Object.</span></span>
- <span data-ttu-id="26363-1891">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1891">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1892">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1892">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-copy"></a><span data-ttu-id="26363-1893">ホスト クラス PIMA オブジェクト コピー</span><span class="sxs-lookup"><span data-stu-id="26363-1893">Host Class Pima Object Copy</span></span> 

#### <a name="ux_host_class_pima_object_copy"></a><span data-ttu-id="26363-1894">ux_host_class_pima_object_copy</span><span class="sxs-lookup"><span data-stu-id="26363-1894">ux_host_class_pima_object_copy</span></span>

<span data-ttu-id="26363-1895">**アイコン** ![ホスト クラス PIMA オブジェクト コピー アイコン](./media/user-guide/usbx-events/image136.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1895">**Icon** ![Host Class Pima Object Copy icon](./media/user-guide/usbx-events/image136.png)</span></span>

<span data-ttu-id="26363-1896">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1896">**Description**</span></span>

<span data-ttu-id="26363-1897">USBX ホスト クラス PIMA オブジェクト コピー イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1897">This event represents a USBX Host Class Pima Object Copy Event.</span></span>

<span data-ttu-id="26363-1898">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1898">**Information Fields**</span></span>

- <span data-ttu-id="26363-1899">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1899">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1900">情報フィールド 2: オブジェクトのハンドル。</span><span class="sxs-lookup"><span data-stu-id="26363-1900">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="26363-1901">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1901">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1902">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1902">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-delete"></a><span data-ttu-id="26363-1903">ホスト クラス PIMA オブジェクト削除</span><span class="sxs-lookup"><span data-stu-id="26363-1903">Host Class Pima Object Delete</span></span> 

#### <a name="ux_host_class_pima_object_delete"></a><span data-ttu-id="26363-1904">ux_host_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="26363-1904">ux_host_class_pima_object_delete</span></span>

<span data-ttu-id="26363-1905">**アイコン** ![ホスト クラス PIMA オブジェクト削除アイコン](./media/user-guide/usbx-events/image137.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1905">**Icon** ![Host Class Pima Object Delete icon](./media/user-guide/usbx-events/image137.png)</span></span>

<span data-ttu-id="26363-1906">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1906">**Description**</span></span>

<span data-ttu-id="26363-1907">USBX ホスト クラス PIMA オブジェクト削除イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1907">This event represents a USBX Host Class Pima Object Delete Event.</span></span>

<span data-ttu-id="26363-1908">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1908">**Information Fields**</span></span>

- <span data-ttu-id="26363-1909">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1909">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1910">情報フィールド 2: オブジェクトのハンドル。</span><span class="sxs-lookup"><span data-stu-id="26363-1910">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="26363-1911">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1911">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1912">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1912">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-get"></a><span data-ttu-id="26363-1913">ホスト クラス PIMA オブジェクト取得</span><span class="sxs-lookup"><span data-stu-id="26363-1913">Host Class Pima Object Get</span></span> 

#### <a name="ux_host_class_pima_object_get"></a><span data-ttu-id="26363-1914">ux_host_class_pima_object_get</span><span class="sxs-lookup"><span data-stu-id="26363-1914">ux_host_class_pima_object_get</span></span>

<span data-ttu-id="26363-1915">**アイコン** ![ホスト クラス PIMA オブジェクト取得アイコン](./media/user-guide/usbx-events/image138.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1915">**Icon** ![Host Class Pima Object Get icon](./media/user-guide/usbx-events/image138.png)</span></span>

<span data-ttu-id="26363-1916">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1916">**Description**</span></span>

<span data-ttu-id="26363-1917">nx_rarp_info_get で RARP 情報を取得するイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1917">This event represents getting RARP information via nx_rarp_info_get.</span></span>

<span data-ttu-id="26363-1918">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1918">**Information Fields**</span></span>

- <span data-ttu-id="26363-1919">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1919">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1920">情報フィールド 2: オブジェクトのハンドル。</span><span class="sxs-lookup"><span data-stu-id="26363-1920">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="26363-1921">情報フィールド 3: オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="26363-1921">Info Field 3: Object.</span></span>
- <span data-ttu-id="26363-1922">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1922">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-info-get"></a><span data-ttu-id="26363-1923">ホスト クラス PIMA オブジェクト情報取得</span><span class="sxs-lookup"><span data-stu-id="26363-1923">Host Class Pima Object Info Get</span></span> 

#### <a name="ux_host_class_pima_object_info_get"></a><span data-ttu-id="26363-1924">ux_host_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="26363-1924">ux_host_class_pima_object_info_get</span></span>

<span data-ttu-id="26363-1925">**アイコン** ![ホスト クラス PIMA オブジェクト情報取得アイコン](./media/user-guide/usbx-events/image139.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1925">**Icon** ![Host Class Pima Object Info Get icon](./media/user-guide/usbx-events/image139.png)</span></span>

<span data-ttu-id="26363-1926">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1926">**Description**</span></span>

<span data-ttu-id="26363-1927">USBX ホスト クラス PIMA オブジェクト情報取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1927">This event represents a USBX Host Class Pima Object Info Get Event.</span></span>

<span data-ttu-id="26363-1928">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1928">**Information Fields**</span></span>

- <span data-ttu-id="26363-1929">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1929">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1930">情報フィールド 2: オブジェクトのハンドル。</span><span class="sxs-lookup"><span data-stu-id="26363-1930">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="26363-1931">情報フィールド 3: オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="26363-1931">Info Field 3: Object.</span></span>
- <span data-ttu-id="26363-1932">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1932">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-info-send"></a><span data-ttu-id="26363-1933">ホスト クラス PIMA オブジェクト情報送信</span><span class="sxs-lookup"><span data-stu-id="26363-1933">Host Class Pima Object Info Send</span></span> 

#### <a name="ux_host_class_pima_object_info_send"></a><span data-ttu-id="26363-1934">ux_host_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="26363-1934">ux_host_class_pima_object_info_send</span></span>

<span data-ttu-id="26363-1935">**アイコン** ![ホスト クラス PIMA オブジェクト情報送信アイコン](./media/user-guide/usbx-events/image140.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1935">**Icon** ![Host Class Pima Object Info Send icon](./media/user-guide/usbx-events/image140.png)</span></span>

<span data-ttu-id="26363-1936">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1936">**Description**</span></span>

<span data-ttu-id="26363-1937">USBX ホスト クラス PIMA オブジェクト情報送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1937">This event represents a USBX Host Class Pima Object Info Send Event.</span></span>

<span data-ttu-id="26363-1938">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1938">**Information Fields**</span></span>

- <span data-ttu-id="26363-1939">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1939">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1940">情報フィールド 2: オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="26363-1940">Info Field 2: Object.</span></span>
- <span data-ttu-id="26363-1941">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1941">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1942">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1942">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-move"></a><span data-ttu-id="26363-1943">ホスト クラス PIMA オブジェクト移動</span><span class="sxs-lookup"><span data-stu-id="26363-1943">Host Class Pima Object Move</span></span> 

#### <a name="ux_host_class_pima_object_move"></a><span data-ttu-id="26363-1944">ux_host_class_pima_object_move</span><span class="sxs-lookup"><span data-stu-id="26363-1944">ux_host_class_pima_object_move</span></span>

<span data-ttu-id="26363-1945">**アイコン** ![ホスト クラス PIMA オブジェクト移動アイコン](./media/user-guide/usbx-events/image141.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1945">**Icon** ![Host Class Pima Object Move icon](./media/user-guide/usbx-events/image141.png)</span></span>

<span data-ttu-id="26363-1946">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1946">**Description**</span></span>

<span data-ttu-id="26363-1947">USBX ホスト クラス PIMA オブジェクト移動イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1947">This event reprThis event represents a USBX Host Class Pima Object Move Event.</span></span>

<span data-ttu-id="26363-1948">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1948">**Information Fields**</span></span>

- <span data-ttu-id="26363-1949">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1949">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1950">情報フィールド 2: オブジェクトのハンドル。</span><span class="sxs-lookup"><span data-stu-id="26363-1950">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="26363-1951">情報フィールド 3: オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="26363-1951">Info Field 3: Object.</span></span>
- <span data-ttu-id="26363-1952">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1952">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-send"></a><span data-ttu-id="26363-1953">ホスト クラス PIMA オブジェクト送信</span><span class="sxs-lookup"><span data-stu-id="26363-1953">Host Class Pima Object Send</span></span> 

#### <a name="ux_host_class_pima_object_move"></a><span data-ttu-id="26363-1954">ux_host_class_pima_object_move</span><span class="sxs-lookup"><span data-stu-id="26363-1954">ux_host_class_pima_object_move</span></span>

<span data-ttu-id="26363-1955">**アイコン** ![ホスト クラス PIMA オブジェクト送信アイコン](./media/user-guide/usbx-events/image142.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1955">**Icon** ![Host Class Pima Object Send icon](./media/user-guide/usbx-events/image142.png)</span></span>

<span data-ttu-id="26363-1956">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1956">**Description**</span></span>

<span data-ttu-id="26363-1957">USBX ホスト クラス PIMA オブジェクト送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1957">This event represents a USBX Host Class Pima Object Send Event.</span></span>

<span data-ttu-id="26363-1958">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1958">**Information Fields**</span></span>

- <span data-ttu-id="26363-1959">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1959">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1960">情報フィールド 2: オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="26363-1960">Info Field 2: Object.</span></span>
- <span data-ttu-id="26363-1961">情報フィールド 3: オブジェクトのバッファー。</span><span class="sxs-lookup"><span data-stu-id="26363-1961">Info Field 3: Object buffer.</span></span>
- <span data-ttu-id="26363-1962">情報フィールド 4: オブジェクトの長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-1962">Info Field 4: Object length.</span></span>

### <a name="host-class-pima-object-transfer-abort"></a><span data-ttu-id="26363-1963">ホスト クラス PIMA オブジェクト転送アボート</span><span class="sxs-lookup"><span data-stu-id="26363-1963">Host Class Pima Object Transfer Abort</span></span> 

#### <a name="ux_host_class_pima_object_transfer_abort"></a><span data-ttu-id="26363-1964">ux_host_class_pima_object_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="26363-1964">ux_host_class_pima_object_transfer_abort</span></span>

<span data-ttu-id="26363-1965">**アイコン** ![ホスト クラス PIMA オブジェクト転送アボート アイコン](./media/user-guide/usbx-events/image143.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1965">**Icon** ![Host Class Pima Object Transfer Abort icon](./media/user-guide/usbx-events/image143.png)</span></span>

<span data-ttu-id="26363-1966">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1966">**Description**</span></span>

<span data-ttu-id="26363-1967">USBX ホスト クラス PIMA オブジェクト転送アボート イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1967">This event represents a USBX Host Class Pima Object Transfer Abort Event.</span></span>

<span data-ttu-id="26363-1968">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1968">**Information Fields**</span></span>

- <span data-ttu-id="26363-1969">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1969">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1970">情報フィールド 2: オブジェクトのハンドル。</span><span class="sxs-lookup"><span data-stu-id="26363-1970">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="26363-1971">情報フィールド 3: オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="26363-1971">Info Field 3: Object.</span></span>
- <span data-ttu-id="26363-1972">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1972">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-read"></a><span data-ttu-id="26363-1973">ホスト クラス PIMA 読み取り</span><span class="sxs-lookup"><span data-stu-id="26363-1973">Host Class Pima Read</span></span> 

#### <a name="ux_host_class_pima_read"></a><span data-ttu-id="26363-1974">ux_host_class_pima_read</span><span class="sxs-lookup"><span data-stu-id="26363-1974">ux_host_class_pima_read</span></span>

<span data-ttu-id="26363-1975">**アイコン** ![ホスト クラス PIMA 読み取りアイコン](./media/user-guide/usbx-events/image144.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1975">**Icon** ![Host Class Pima Read icon](./media/user-guide/usbx-events/image144.png)</span></span>

<span data-ttu-id="26363-1976">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1976">**Description**</span></span>

<span data-ttu-id="26363-1977">USBX ホスト クラス PIMA 読み取りイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1977">This event represents a USBX Host Class Pima Read Event.</span></span>

<span data-ttu-id="26363-1978">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1978">**Information Fields**</span></span>

- <span data-ttu-id="26363-1979">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1979">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1980">情報フィールド 2: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-1980">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="26363-1981">情報フィールド 3: データの長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-1981">Info Field 3: Data length.</span></span>
- <span data-ttu-id="26363-1982">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1982">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-request-cancel"></a><span data-ttu-id="26363-1983">ホスト クラス PIMA 要求取り消し</span><span class="sxs-lookup"><span data-stu-id="26363-1983">Host Class Pima Request Cancel</span></span> 

#### <a name="ux_host_class_pima_request_cancel"></a><span data-ttu-id="26363-1984">ux_host_class_pima_request_cancel</span><span class="sxs-lookup"><span data-stu-id="26363-1984">ux_host_class_pima_request_cancel</span></span>

<span data-ttu-id="26363-1985">**アイコン** ![ホスト クラス PIMA 要求取り消しアイコン](./media/user-guide/usbx-events/image145.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1985">**Icon** ![Host Class Pima Request Cancel icon](./media/user-guide/usbx-events/image145.png)</span></span>

<span data-ttu-id="26363-1986">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1986">**Description**</span></span>

<span data-ttu-id="26363-1987">USBX ホスト クラス PIMA 要求取り消しイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1987">This event represents a USBX Host Class Pima Request Cancel Event.</span></span>

<span data-ttu-id="26363-1988">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1988">**Information Fields**</span></span>

- <span data-ttu-id="26363-1989">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1989">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-1990">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1990">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-1991">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1991">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-1992">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-1992">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-session-close"></a><span data-ttu-id="26363-1993">ホスト クラス PIMA セッション終了</span><span class="sxs-lookup"><span data-stu-id="26363-1993">Host Class Pima Session Close</span></span> 

#### <a name="ux_host_class_pima_session_close"></a><span data-ttu-id="26363-1994">ux_host_class_pima_session_close</span><span class="sxs-lookup"><span data-stu-id="26363-1994">ux_host_class_pima_session_close</span></span>

<span data-ttu-id="26363-1995">**アイコン** ![ホスト クラス PIMA セッション終了アイコン](./media/user-guide/usbx-events/image146.png)</span><span class="sxs-lookup"><span data-stu-id="26363-1995">**Icon** ![Host Class Pima Session Close icon](./media/user-guide/usbx-events/image146.png)</span></span>

<span data-ttu-id="26363-1996">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-1996">**Description**</span></span>

<span data-ttu-id="26363-1997">USBX ホスト クラス PIMA セッション終了イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-1997">This event represents a USBX Host Class Pima Session Close Event.</span></span>

<span data-ttu-id="26363-1998">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-1998">**Information Fields**</span></span>

- <span data-ttu-id="26363-1999">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-1999">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2000">情報フィールド 2: PIMA セッション。</span><span class="sxs-lookup"><span data-stu-id="26363-2000">Info Field 2: Pima session.</span></span>
- <span data-ttu-id="26363-2001">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2001">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2002">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2002">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-session-open"></a><span data-ttu-id="26363-2003">ホスト クラス PIMA セッション開始</span><span class="sxs-lookup"><span data-stu-id="26363-2003">Host Class Pima Session Open</span></span> 

#### <a name="ux_host_class_pima_session_open"></a><span data-ttu-id="26363-2004">ux_host_class_pima_session_open</span><span class="sxs-lookup"><span data-stu-id="26363-2004">ux_host_class_pima_session_open</span></span>

<span data-ttu-id="26363-2005">**アイコン** ![ホスト クラス PIMA セッション開始アイコン](./media/user-guide/usbx-events/image147.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2005">**Icon** ![Host Class Pima Session Open icon](./media/user-guide/usbx-events/image147.png)</span></span>

<span data-ttu-id="26363-2006">**説明** USBX ホスト クラス PIMA セッション開始イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2006">**Description** This event represents a USBX Host Class Pima Session Open Event.</span></span>

<span data-ttu-id="26363-2007">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2007">**Information Fields**</span></span>

- <span data-ttu-id="26363-2008">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2008">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2009">情報フィールド 2: PIMA セッション。</span><span class="sxs-lookup"><span data-stu-id="26363-2009">Info Field 2: Pima session.</span></span>
- <span data-ttu-id="26363-2010">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2010">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2011">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2011">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-storage-ids-get"></a><span data-ttu-id="26363-2012">ホスト クラス PIMA ストレージ ID 取得</span><span class="sxs-lookup"><span data-stu-id="26363-2012">Host Class Pima Storage Ids Get</span></span> 

#### <a name="ux_host_class_pima_session_ids_get"></a><span data-ttu-id="26363-2013">ux_host_class_pima_session_ids_get</span><span class="sxs-lookup"><span data-stu-id="26363-2013">ux_host_class_pima_session_ids_get</span></span>

<span data-ttu-id="26363-2014">**アイコン** ![ホスト クラス PIMA ストレージ ID 取得アイコン](./media/user-guide/usbx-events/image148.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2014">**Icon** ![Host Class Pima Storage Ids Get icon](./media/user-guide/usbx-events/image148.png)</span></span>

<span data-ttu-id="26363-2015">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2015">**Description**</span></span>

<span data-ttu-id="26363-2016">USBX ホスト クラス PIMA ストレージ ID 取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2016">This event represents a USBX Host Class Pima Storage Ids Get Event.</span></span>

<span data-ttu-id="26363-2017">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2017">**Information Fields**</span></span>

- <span data-ttu-id="26363-2018">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2018">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2019">情報フィールド 2: ストレージ ID の配列。</span><span class="sxs-lookup"><span data-stu-id="26363-2019">nfo Field 2: Storage ID array.</span></span>
- <span data-ttu-id="26363-2020">情報フィールド 3: ストレージ ID の長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-2020">Info Field 3: Storage ID length.</span></span>
<span data-ttu-id="26363-2021">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2021">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-storage-info-get"></a><span data-ttu-id="26363-2022">ホスト クラス PIMA ストレージ情報取得</span><span class="sxs-lookup"><span data-stu-id="26363-2022">Host Class Pima Storage Info Get</span></span> 

#### <a name="ux_host_class_pima_storage_info_get"></a><span data-ttu-id="26363-2023">ux_host_class_pima_storage_info_get</span><span class="sxs-lookup"><span data-stu-id="26363-2023">ux_host_class_pima_storage_info_get</span></span>

<span data-ttu-id="26363-2024">**アイコン** ![ホスト クラス PIMA ストレージ情報取得アイコン](./media/user-guide/usbx-events/image149.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2024">**Icon** ![Host Class Pima Storage Info Get icon](./media/user-guide/usbx-events/image149.png)</span></span>

<span data-ttu-id="26363-2025">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2025">**Description**</span></span>

<span data-ttu-id="26363-2026">USBX ホスト クラス PIMA ストレージ情報取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2026">This event represents a USBX Host Class Pima Storage Info Get Event.</span></span>

<span data-ttu-id="26363-2027">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2027">**Information Fields**</span></span>

- <span data-ttu-id="26363-2028">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2028">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2029">情報フィールド 2: ストレージ ID。</span><span class="sxs-lookup"><span data-stu-id="26363-2029">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="26363-2030">情報フィールド 3: ストレージ。</span><span class="sxs-lookup"><span data-stu-id="26363-2030">Info Field 3: Storage.</span></span>
- <span data-ttu-id="26363-2031">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2031">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-thumb-get"></a><span data-ttu-id="26363-2032">ホスト クラス PIMA Thumb 取得</span><span class="sxs-lookup"><span data-stu-id="26363-2032">Host Class Pima Thumb Get</span></span> 

#### <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="26363-2033">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="26363-2033">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="26363-2034">**アイコン** ![ホスト クラス PIMA Thumb 取得アイコン](./media/user-guide/usbx-events/image150.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2034">**Icon** ![Host Class Pima Thumb Get icon](./media/user-guide/usbx-events/image150.png)</span></span>

<span data-ttu-id="26363-2035">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2035">**Description**</span></span>

<span data-ttu-id="26363-2036">nx_tcp_server_socket_unaccept で TCP サーバーの接続を拒否するイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2036">This event represents unaccepting a TCP server connection via nx_tcp_server_socket_unaccept.</span></span>

<span data-ttu-id="26363-2037">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2037">**Information Fields**</span></span> 

- <span data-ttu-id="26363-2038">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2038">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2039">情報フィールド 2: オブジェクトのハンドル。</span><span class="sxs-lookup"><span data-stu-id="26363-2039">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="26363-2040">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2040">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2041">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2041">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-write"></a><span data-ttu-id="26363-2042">ホスト クラス PIMA 書き込み</span><span class="sxs-lookup"><span data-stu-id="26363-2042">Host Class Pima Write</span></span> 

#### <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="26363-2043">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="26363-2043">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="26363-2044">**アイコン** ![ホスト クラス PIMA 書き込みアイコン](./media/user-guide/usbx-events/image151.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2044">**Icon** ![Host Class Pima Write icon](./media/user-guide/usbx-events/image151.png)</span></span>

<span data-ttu-id="26363-2045">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2045">**Description**</span></span>

<span data-ttu-id="26363-2046">USBX ホスト クラス PIMA 書き込みイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2046">This event represents a USBX Host Class Pima Write.</span></span>

<span data-ttu-id="26363-2047">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2047">**Information Fields**</span></span>

- <span data-ttu-id="26363-2048">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2048">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="26363-2049">情報フィールド 2: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-2049">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="26363-2050">情報フィールド 3: データの長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-2050">Info Field 3: Data length.</span></span>
- <span data-ttu-id="26363-2051">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2051">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-activate"></a><span data-ttu-id="26363-2052">ホスト クラス Printer アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-2052">Host Class Printer Activate</span></span> 

#### <a name="ux_host_class_printer_activate"></a><span data-ttu-id="26363-2053">ux_host_class_printer_activate</span><span class="sxs-lookup"><span data-stu-id="26363-2053">ux_host_class_printer_activate</span></span>

<span data-ttu-id="26363-2054">**アイコン** ![ホスト クラス Printer アクティブ化アイコン](./media/user-guide/usbx-events/image152.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2054">**Icon** ![Host Class Printer Activate icon](./media/user-guide/usbx-events/image152.png)</span></span>

<span data-ttu-id="26363-2055">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2055">**Description**</span></span>

<span data-ttu-id="26363-2056">USBX ホスト クラス Printer アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2056">This event represents a USBX Host Class Printer Activate Event.</span></span>

<span data-ttu-id="26363-2057">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2057">**Information Fields**</span></span>

- <span data-ttu-id="26363-2058">情報フィールド 1: IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-2058">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="26363-2059">情報フィールド 2: ソケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-2059">Info Field 2: Pointer to socket.</span></span>
- <span data-ttu-id="26363-2060">情報フィールド 3: サービスの種類。</span><span class="sxs-lookup"><span data-stu-id="26363-2060">Info Field 3: Type of service.</span></span>
- <span data-ttu-id="26363-2061">情報フィールド 4: 受信ウィンドウのサイズ。</span><span class="sxs-lookup"><span data-stu-id="26363-2061">Info Field 4: Receive window size.</span></span>

### <a name="host-class-printer-deactivate"></a><span data-ttu-id="26363-2062">ホスト クラス Printer 非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-2062">Host Class Printer Deactivate</span></span> 

#### <a name="ux_host_class_printer_deactivate"></a><span data-ttu-id="26363-2063">ux_host_class_printer_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-2063">ux_host_class_printer_deactivate</span></span>

<span data-ttu-id="26363-2064">**アイコン** ![ホスト クラス Printer 非アクティブ化アイコン](./media/user-guide/usbx-events/image153.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2064">**Icon** ![Host Class Printer Deactivate icon](./media/user-guide/usbx-events/image153.png)</span></span>

<span data-ttu-id="26363-2065">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2065">**Description**</span></span>

<span data-ttu-id="26363-2066">USBX ホスト クラス Printer 非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2066">This event represents a USBX Host Class Printer Deactivate Event.</span></span>

<span data-ttu-id="26363-2067">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2067">**Information Fields**</span></span>

- <span data-ttu-id="26363-2068">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2068">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2069">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2069">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2070">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2070">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2071">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2071">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-name-get"></a><span data-ttu-id="26363-2072">ホスト クラス Printer 名前取得</span><span class="sxs-lookup"><span data-stu-id="26363-2072">Host Class Printer Name Get</span></span> 

#### <a name="ux_host_class_printer_name_get"></a><span data-ttu-id="26363-2073">ux_host_class_printer_name_get</span><span class="sxs-lookup"><span data-stu-id="26363-2073">ux_host_class_printer_name_get</span></span>

<span data-ttu-id="26363-2074">**アイコン** ![ホスト クラス Printer 名前取得アイコン](./media/user-guide/usbx-events/image154.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2074">**Icon** ![Host Class Printer Name Get icon](./media/user-guide/usbx-events/image154.png)</span></span>

<span data-ttu-id="26363-2075">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2075">**Description**</span></span>

<span data-ttu-id="26363-2076">USBX ホスト クラス Printer 名前取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2076">This event represents a USBX Host Class Printer Name Get Event.</span></span>

<span data-ttu-id="26363-2077">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2077">**Information Fields**</span></span> 

- <span data-ttu-id="26363-2078">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2078">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2079">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2079">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2080">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2080">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2081">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2081">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-read"></a><span data-ttu-id="26363-2082">ホスト クラス Printer 読み取り</span><span class="sxs-lookup"><span data-stu-id="26363-2082">Host Class Printer Read</span></span> 

#### <a name="ux_host_class_printer_read"></a><span data-ttu-id="26363-2083">ux_host_class_printer_read</span><span class="sxs-lookup"><span data-stu-id="26363-2083">ux_host_class_printer_read</span></span>

<span data-ttu-id="26363-2084">**アイコン** ![ホスト クラス Printer 読み取りアイコン](./media/user-guide/usbx-events/image155.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2084">**Icon** ![Host Class Printer Read icon](./media/user-guide/usbx-events/image155.png)</span></span>

<span data-ttu-id="26363-2085">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2085">**Description**</span></span>

<span data-ttu-id="26363-2086">USBX ホスト クラス Printer 読み取りイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2086">This event represents a USBX Host Class Printer Read Event.</span></span>

<span data-ttu-id="26363-2087">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2087">**Information Fields**</span></span>

- <span data-ttu-id="26363-2088">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2088">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2089">情報フィールド 2: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-2089">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="26363-2090">情報フィールド 3: 要求された長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-2090">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="26363-2091">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2091">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-soft-reset"></a><span data-ttu-id="26363-2092">ホスト クラス Printer ソフト リセット</span><span class="sxs-lookup"><span data-stu-id="26363-2092">Host Class Printer Soft Reset</span></span> 

#### <a name="ux_host_class_printer_soft_reset"></a><span data-ttu-id="26363-2093">ux_host_class_printer_soft_reset</span><span class="sxs-lookup"><span data-stu-id="26363-2093">ux_host_class_printer_soft_reset</span></span>

<span data-ttu-id="26363-2094">**アイコン** ![ホスト クラス Printer ソフト リセット アイコン](./media/user-guide/usbx-events/image156.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2094">**Icon** ![Host Class Printer Soft Reset icon](./media/user-guide/usbx-events/image156.png)</span></span>

<span data-ttu-id="26363-2095">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2095">**Description**</span></span>

<span data-ttu-id="26363-2096">USBX ホスト クラス Printer ソフト リセット イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2096">This event represents a USBX Host Class Printer Soft Reset Event.</span></span>

<span data-ttu-id="26363-2097">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2097">**Information Fields**</span></span>

- <span data-ttu-id="26363-2098">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2098">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2099">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2099">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2100">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2100">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2101">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2101">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-status-get"></a><span data-ttu-id="26363-2102">ホスト クラス Printer 状態取得</span><span class="sxs-lookup"><span data-stu-id="26363-2102">Host Class Printer Status Get</span></span> 

#### <a name="ux_host_class_printer_status_get"></a><span data-ttu-id="26363-2103">ux_host_class_printer_status_get</span><span class="sxs-lookup"><span data-stu-id="26363-2103">ux_host_class_printer_status_get</span></span>

<span data-ttu-id="26363-2104">**アイコン** ![ホスト クラス Printer 状態取得アイコン](./media/user-guide/usbx-events/image157.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2104">**Icon** ![Host Class Printer Status Get icon](./media/user-guide/usbx-events/image157.png)</span></span>

<span data-ttu-id="26363-2105">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2105">**Description**</span></span>

<span data-ttu-id="26363-2106">USBX ホスト クラス Printer 状態取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2106">This event represents a USBX Host Class Printer Status Get Event.</span></span>

<span data-ttu-id="26363-2107">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2107">**Information Fields**</span></span>

- <span data-ttu-id="26363-2108">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2108">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2109">情報フィールド 2: プリンターの状態。</span><span class="sxs-lookup"><span data-stu-id="26363-2109">Info Field 2: Printer status.</span></span>
- <span data-ttu-id="26363-2110">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2110">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2111">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2111">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-write"></a><span data-ttu-id="26363-2112">ホスト クラス Printer 書き込み</span><span class="sxs-lookup"><span data-stu-id="26363-2112">Host Class Printer Write</span></span> 

#### <a name="ux_host_class_printer_write"></a><span data-ttu-id="26363-2113">ux_host_class_printer_write</span><span class="sxs-lookup"><span data-stu-id="26363-2113">ux_host_class_printer_write</span></span>

<span data-ttu-id="26363-2114">**アイコン** ![ホスト クラス Printer 書き込みアイコン](./media/user-guide/usbx-events/image158.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2114">**Icon** ![Host Class Printer Write icon](./media/user-guide/usbx-events/image158.png)</span></span>

<span data-ttu-id="26363-2115">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2115">**Description**</span></span>

<span data-ttu-id="26363-2116">USBX ホスト クラス Printer 書き込みイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2116">This event represents a USBX Host Class Printer Write.</span></span>

<span data-ttu-id="26363-2117">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2117">**Information Fields**</span></span> 

- <span data-ttu-id="26363-2118">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2118">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2119">情報フィールド 2: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-2119">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="26363-2120">情報フィールド 3: 要求された長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-2120">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="26363-2121">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2121">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-activate"></a><span data-ttu-id="26363-2122">ホスト クラス Prolific アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-2122">Host Class Prolific Activate</span></span> 

#### <a name="ux_host_class_prolific_activate"></a><span data-ttu-id="26363-2123">ux_host_class_prolific_activate</span><span class="sxs-lookup"><span data-stu-id="26363-2123">ux_host_class_prolific_activate</span></span> 

<span data-ttu-id="26363-2124">**アイコン** ![ホスト クラス Prolific アクティブ化アイコン](./media/user-guide/usbx-events/image159.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2124">**Icon** ![Host Class Prolific Activate icon](./media/user-guide/usbx-events/image159.png)</span></span>

<span data-ttu-id="26363-2125">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2125">**Description**</span></span>

<span data-ttu-id="26363-2126">USBX ホスト クラス Prolific アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2126">This event represents a USBX Host Class Prolific Activate Event.</span></span>

<span data-ttu-id="26363-2127">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2127">**Information Fields**</span></span> 

- <span data-ttu-id="26363-2128">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2128">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2129">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2129">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2130">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2130">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2131">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2131">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-deactivate"></a><span data-ttu-id="26363-2132">ホスト クラス Prolific 非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-2132">Host Class Prolific Deactivate</span></span> 

#### <a name="ux_host_class_prolific_deactivate"></a><span data-ttu-id="26363-2133">ux_host_class_prolific_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-2133">ux_host_class_prolific_deactivate</span></span> 

<span data-ttu-id="26363-2134">**アイコン** ![ホスト クラス Prolific 非アクティブ化アイコン](./media/user-guide/usbx-events/image160.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2134">**Icon** ![Host Class Prolific Deactivate icon](./media/user-guide/usbx-events/image160.png)</span></span>

<span data-ttu-id="26363-2135">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2135">**Description**</span></span>

<span data-ttu-id="26363-2136">USBX ホスト クラス Prolific 非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2136">This event represents a USBX Host Class Prolific Deactivate Event.</span></span>

<span data-ttu-id="26363-2137">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2137">**Information Fields**</span></span>

- <span data-ttu-id="26363-2138">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2138">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2139">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2139">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2140">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2140">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2141">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2141">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-abort-in-pipe"></a><span data-ttu-id="26363-2142">ホスト クラス Prolific IOCTL 入力パイプ アボート</span><span class="sxs-lookup"><span data-stu-id="26363-2142">Host Class Prolific Ioctl Abort In Pipe</span></span> 

#### <a name="ux_host_class_prolific_ioctl_abort_in_pipe"></a><span data-ttu-id="26363-2143">ux_host_class_prolific_ioctl_abort_in_pipe</span><span class="sxs-lookup"><span data-stu-id="26363-2143">ux_host_class_prolific_ioctl_abort_in_pipe</span></span>

<span data-ttu-id="26363-2144">**アイコン** ![ホスト クラス Prolific IOCTL 入力パイプ アボート アイコン](./media/user-guide/usbx-events/image161.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2144">**Icon** ![Host Class Prolific I O C T L Abort In Pipe icon](./media/user-guide/usbx-events/image161.png)</span></span>

<span data-ttu-id="26363-2145">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2145">**Description**</span></span>

<span data-ttu-id="26363-2146">USBX ホスト クラス Prolific IOCTL 入力パイプ アボート イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2146">This event represents a USBX Host Class Prolific Ioctl Abort In Pipe Event.</span></span>

<span data-ttu-id="26363-2147">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2147">**Information Fields**</span></span>

- <span data-ttu-id="26363-2148">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2148">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2149">情報フィールド 2: エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="26363-2149">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="26363-2150">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2150">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2151">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2151">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-abort-out-pipe"></a><span data-ttu-id="26363-2152">ホスト クラス Prolific IOCTL 出力パイプ アボート</span><span class="sxs-lookup"><span data-stu-id="26363-2152">Host Class Prolific Ioctl Abort Out Pipe</span></span> 

#### <a name="ux_host_class_prolific_ioctl_abort_out_pipe"></a><span data-ttu-id="26363-2153">ux_host_class_prolific_ioctl_abort_out_pipe</span><span class="sxs-lookup"><span data-stu-id="26363-2153">ux_host_class_prolific_ioctl_abort_out_pipe</span></span>

<span data-ttu-id="26363-2154">**アイコン** ![ホスト クラス Prolific IOCTL 出力パイプ アボート アイコン](./media/user-guide/usbx-events/image162.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2154">**Icon** ![Host Class Prolific I O C T L Abort Out Pipe icon](./media/user-guide/usbx-events/image162.png)</span></span>

<span data-ttu-id="26363-2155">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2155">**Description**</span></span>

<span data-ttu-id="26363-2156">USBX ホスト クラス Prolific IOCTL 出力パイプ アボート イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2156">This event represents a USBX Host Class Prolific Ioctl Abort Out Pipe Event.</span></span>

<span data-ttu-id="26363-2157">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2157">**Information Fields**</span></span>

- <span data-ttu-id="26363-2158">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2158">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2159">情報フィールド 2: エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="26363-2159">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="26363-2160">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2160">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2161">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2161">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-get-device-status"></a><span data-ttu-id="26363-2162">ホスト クラス Prolific IOCTL デバイス状態取得</span><span class="sxs-lookup"><span data-stu-id="26363-2162">Host Class Prolific Ioctl Get Device Status</span></span> 

#### <a name="ux_host_class_prolific_ioctl_get_device_status"></a><span data-ttu-id="26363-2163">ux_host_class_prolific_ioctl_get_device_status</span><span class="sxs-lookup"><span data-stu-id="26363-2163">ux_host_class_prolific_ioctl_get_device_status</span></span>

<span data-ttu-id="26363-2164">**アイコン** ![ホスト クラス Prolific IOCTL デバイス状態取得アイコン](./media/user-guide/usbx-events/image163.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2164">**Icon** ![Host Class Prolific I O C T L Get Device Status icon](./media/user-guide/usbx-events/image163.png)</span></span>

<span data-ttu-id="26363-2165">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2165">**Description**</span></span>

<span data-ttu-id="26363-2166">USBX ホスト クラス Prolific IOCTL デバイス状態取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2166">This event represents a USBX Host Class Prolific Ioctl Get Device Status Event.</span></span>

<span data-ttu-id="26363-2167">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2167">**Information Fields**</span></span>

- <span data-ttu-id="26363-2168">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2168">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2169">情報フィールド 2: デバイスの状態。</span><span class="sxs-lookup"><span data-stu-id="26363-2169">Info Field 2: Device status.</span></span>
- <span data-ttu-id="26363-2170">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2170">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2171">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2171">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-get-line-coding"></a><span data-ttu-id="26363-2172">ホスト クラス Prolific IOCTL 伝送路符号化取得</span><span class="sxs-lookup"><span data-stu-id="26363-2172">Host Class Prolific Ioctl Get Line Coding</span></span> 

#### <a name="ux_host_class_prolific_ioctl_get_line_coding"></a><span data-ttu-id="26363-2173">ux_host_class_prolific_ioctl_get_line_coding</span><span class="sxs-lookup"><span data-stu-id="26363-2173">ux_host_class_prolific_ioctl_get_line_coding</span></span>

<span data-ttu-id="26363-2174">**アイコン** ![ホスト クラス Prolific IOCTL 伝送路符号化取得アイコン](./media/user-guide/usbx-events/image164.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2174">**Icon** ![Host Class Prolific I O C T L Get Line Coding icon](./media/user-guide/usbx-events/image164.png)</span></span>

<span data-ttu-id="26363-2175">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2175">**Description**</span></span>

<span data-ttu-id="26363-2176">USBX ホスト クラス Prolific IOCTL 伝送路符号化取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2176">This event represents a USBX Host Class Prolific Ioctl Get Line Coding Event.</span></span>

<span data-ttu-id="26363-2177">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2177">**Information Fields**</span></span>

- <span data-ttu-id="26363-2178">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2178">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2179">情報フィールド 2: パラメーター。</span><span class="sxs-lookup"><span data-stu-id="26363-2179">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="26363-2180">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2180">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2181">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2181">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-purge"></a><span data-ttu-id="26363-2182">ホスト クラス Prolific IOCTL パージ</span><span class="sxs-lookup"><span data-stu-id="26363-2182">Host Class Prolific Ioctl Purge</span></span> 

#### <a name="ux_host_class_prolific_ioctl_purge"></a><span data-ttu-id="26363-2183">ux_host_class_prolific_ioctl_purge</span><span class="sxs-lookup"><span data-stu-id="26363-2183">ux_host_class_prolific_ioctl_purge</span></span>

<span data-ttu-id="26363-2184">**アイコン** ![ホスト クラス Prolific IOCTL パージ アイコン](./media/user-guide/usbx-events/image165.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2184">**Icon** ![Host Class Prolific Ioctl Purge icon](./media/user-guide/usbx-events/image165.png)</span></span>

<span data-ttu-id="26363-2185">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2185">**Description**</span></span>

<span data-ttu-id="26363-2186">USBX ホスト クラス Prolific IOCTL パージ イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2186">This event represents a USBX Host Class Prolific Ioctl Purge Event.</span></span>

<span data-ttu-id="26363-2187">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2187">**Information Fields**</span></span>

- <span data-ttu-id="26363-2188">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2188">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2189">情報フィールド 2: パラメーター。</span><span class="sxs-lookup"><span data-stu-id="26363-2189">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="26363-2190">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2190">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2191">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2191">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-report-device"></a><span data-ttu-id="26363-2192">ホスト クラス Prolific IOCTL デバイス報告</span><span class="sxs-lookup"><span data-stu-id="26363-2192">Host Class Prolific Ioctl Report Device</span></span> 

#### <a name="ux_host_class_prolific_ioctl_report_device"></a><span data-ttu-id="26363-2193">ux_host_class_prolific_ioctl_report_device</span><span class="sxs-lookup"><span data-stu-id="26363-2193">ux_host_class_prolific_ioctl_report_device</span></span>

<span data-ttu-id="26363-2194">**アイコン** ![ホスト クラス Prolific IOCTL デバイス報告アイコン](./media/user-guide/usbx-events/image166.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2194">**Icon** ![Host Class Prolific I O C T L Report Device icon](./media/user-guide/usbx-events/image166.png)</span></span>

<span data-ttu-id="26363-2195">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2195">**Description**</span></span>

<span data-ttu-id="26363-2196">USBX ホスト クラス Prolific IOCTL デバイス状態変更報告イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2196">This event represents a USBX Host Class Prolific Ioctl Report Device Status Change Event.</span></span>

<span data-ttu-id="26363-2197">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2197">**Information Fields**</span></span>

- <span data-ttu-id="26363-2198">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2198">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2199">情報フィールド 2: パラメーター。</span><span class="sxs-lookup"><span data-stu-id="26363-2199">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="26363-2200">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2200">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2201">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2201">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-send-break"></a><span data-ttu-id="26363-2202">ホスト クラス Prolific IOCTL ブレーク送信</span><span class="sxs-lookup"><span data-stu-id="26363-2202">Host Class Prolific Ioctl Send Break</span></span> 

#### <a name="ux_host_class_prolific_ioctl_send_break"></a><span data-ttu-id="26363-2203">ux_host_class_prolific_ioctl_send_break</span><span class="sxs-lookup"><span data-stu-id="26363-2203">ux_host_class_prolific_ioctl_send_break</span></span>

<span data-ttu-id="26363-2204">**アイコン** ![ホスト クラス Prolific IOCTL ブレーク送信アイコン](./media/user-guide/usbx-events/image167.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2204">**Icon** ![Host Class Prolific I O C T L Send Break icon](./media/user-guide/usbx-events/image167.png)</span></span>

<span data-ttu-id="26363-2205">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2205">**Description**</span></span>

<span data-ttu-id="26363-2206">USBX ホスト クラス Prolific IOCTL ブレーク送信イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2206">This event represents a USBX Host Class Prolific Ioctl Send Break Event.</span></span>

<span data-ttu-id="26363-2207">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2207">**Information Fields**</span></span>

- <span data-ttu-id="26363-2208">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2208">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2209">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2209">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2210">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2210">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2211">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2211">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-set-line-coding"></a><span data-ttu-id="26363-2212">ホスト クラス Prolific IOCTL 伝送路符号化設定</span><span class="sxs-lookup"><span data-stu-id="26363-2212">Host Class Prolific Ioctl Set Line Coding</span></span> 

#### <a name="ux_host_class_prolific_ioctl_set_line_coding"></a><span data-ttu-id="26363-2213">ux_host_class_prolific_ioctl_set_line_coding</span><span class="sxs-lookup"><span data-stu-id="26363-2213">ux_host_class_prolific_ioctl_set_line_coding</span></span>

<span data-ttu-id="26363-2214">**アイコン** ![ホスト クラス Prolific IOCTL 伝送路符号化設定アイコン](./media/user-guide/usbx-events/image168.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2214">**Icon** ![Host Class Prolific I O C T L Set Line Coding icon](./media/user-guide/usbx-events/image168.png)</span></span>

<span data-ttu-id="26363-2215">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2215">**Description**</span></span>

<span data-ttu-id="26363-2216">USBX ホスト クラス Prolific IOCTL 伝送路符号化設定イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2216">This event represents a USBX Host Class Prolific Ioctl Set Line Coding Event.</span></span>

<span data-ttu-id="26363-2217">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2217">**Information Fields**</span></span>

- <span data-ttu-id="26363-2218">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2218">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2219">情報フィールド 2: パラメーター。</span><span class="sxs-lookup"><span data-stu-id="26363-2219">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="26363-2220">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2220">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2221">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2221">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-set-line-state"></a><span data-ttu-id="26363-2222">ホスト クラス Prolific IOCTL 伝送路状態設定</span><span class="sxs-lookup"><span data-stu-id="26363-2222">Host Class Prolific Ioctl Set Line State</span></span> 

#### <a name="ux_host_class_prolific_ioctl_set_line_state"></a><span data-ttu-id="26363-2223">ux_host_class_prolific_ioctl_set_line_state</span><span class="sxs-lookup"><span data-stu-id="26363-2223">ux_host_class_prolific_ioctl_set_line_state</span></span>

<span data-ttu-id="26363-2224">**アイコン** ![ホスト クラス Prolific IOCTL 伝送路状態設定アイコン](./media/user-guide/usbx-events/image169.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2224">**Icon** ![Host Class Prolific I O C T L Set Line State icon](./media/user-guide/usbx-events/image169.png)</span></span>

<span data-ttu-id="26363-2225">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2225">**Description**</span></span>

<span data-ttu-id="26363-2226">USBX ホスト クラス Prolific IOCTL 伝送路状態設定イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2226">This event represents a USBX Host Class Prolific Ioctl Set Line State Event.</span></span>

<span data-ttu-id="26363-2227">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2227">**Information Fields**</span></span>

- <span data-ttu-id="26363-2228">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2228">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2229">情報フィールド 2: パラメーター。</span><span class="sxs-lookup"><span data-stu-id="26363-2229">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="26363-2230">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2230">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2231">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2231">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-read"></a><span data-ttu-id="26363-2232">ホスト クラス Prolific 読み取り</span><span class="sxs-lookup"><span data-stu-id="26363-2232">Host Class Prolific Read</span></span> 

#### <a name="ux_host_class_prolific_read"></a><span data-ttu-id="26363-2233">ux_host_class_prolific_read</span><span class="sxs-lookup"><span data-stu-id="26363-2233">ux_host_class_prolific_read</span></span>

<span data-ttu-id="26363-2234">**アイコン** ![ホスト クラス Prolific 読み取りアイコン](./media/user-guide/usbx-events/image170.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2234">**Icon** ![Host Class Prolific Read icon](./media/user-guide/usbx-events/image170.png)</span></span>

<span data-ttu-id="26363-2235">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2235">**Description**</span></span>

<span data-ttu-id="26363-2236">USBX ホスト クラス Prolific 読み取りイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2236">This event represents a USBX Host Class Prolific Read Event.</span></span>

<span data-ttu-id="26363-2237">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2237">**Information Fields**</span></span>

- <span data-ttu-id="26363-2238">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2238">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2239">情報フィールド 2: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-2239">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="26363-2240">情報フィールド 3: 要求された長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-2240">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="26363-2241">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2241">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-reception-start"></a><span data-ttu-id="26363-2242">ホスト クラス Prolific 受信開始</span><span class="sxs-lookup"><span data-stu-id="26363-2242">Host Class Prolific Reception Start</span></span> 

#### <a name="ux_host_class_prolific_reception_start"></a><span data-ttu-id="26363-2243">ux_host_class_prolific_reception_start</span><span class="sxs-lookup"><span data-stu-id="26363-2243">ux_host_class_prolific_reception_start</span></span>

<span data-ttu-id="26363-2244">**アイコン** ![ホスト クラス Prolific 受信開始アイコン](./media/user-guide/usbx-events/image171.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2244">**Icon** ![Host Class Prolific Reception Start icon](./media/user-guide/usbx-events/image171.png)</span></span>

<span data-ttu-id="26363-2245">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2245">**Description**</span></span>

<span data-ttu-id="26363-2246">USBX ホスト クラス Prolific 受信開始イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2246">This event represents a USBX Host Class Prolific Reception Start Event.</span></span>

<span data-ttu-id="26363-2247">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2247">**Information Fields**</span></span>

- <span data-ttu-id="26363-2248">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2248">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2249">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2249">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2250">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2250">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2251">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2251">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-reception-stop"></a><span data-ttu-id="26363-2252">ホスト クラス Prolific 受信停止</span><span class="sxs-lookup"><span data-stu-id="26363-2252">Host Class Prolific Reception Stop</span></span> 

#### <a name="ux_host_class_prolific_reception_stop"></a><span data-ttu-id="26363-2253">ux_host_class_prolific_reception_stop</span><span class="sxs-lookup"><span data-stu-id="26363-2253">ux_host_class_prolific_reception_stop</span></span>

<span data-ttu-id="26363-2254">**アイコン** ![ホスト クラス Prolific 受信停止アイコン](./media/user-guide/usbx-events/image172.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2254">**Icon** ![Host Class Prolific Reception Stop icon](./media/user-guide/usbx-events/image172.png)</span></span>

<span data-ttu-id="26363-2255">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2255">**Description**</span></span>

<span data-ttu-id="26363-2256">USBX ホスト クラス Prolific 受信停止イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2256">This event represents a USBX Host Class Prolific Reception Stop Event.</span></span>

<span data-ttu-id="26363-2257">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2257">**Information Fields**</span></span>

- <span data-ttu-id="26363-2258">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2258">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2259">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2259">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2260">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2260">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2261">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2261">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-write"></a><span data-ttu-id="26363-2262">ホスト クラス Prolific 書き込み</span><span class="sxs-lookup"><span data-stu-id="26363-2262">Host Class Prolific Write</span></span> 

#### <a name="ux_host_class_prolific_write"></a><span data-ttu-id="26363-2263">ux_host_class_prolific_write</span><span class="sxs-lookup"><span data-stu-id="26363-2263">ux_host_class_prolific_write</span></span>

<span data-ttu-id="26363-2264">**アイコン** ![ホスト クラス Prolific 書き込みアイコン](./media/user-guide/usbx-events/image173.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2264">**Icon** ![Host Class Prolific Write icon](./media/user-guide/usbx-events/image173.png)</span></span>

<span data-ttu-id="26363-2265">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2265">**Description**</span></span>

<span data-ttu-id="26363-2266">USBX ホスト クラス Prolific 書き込みイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2266">This event represents a USBX Host Class Prolific Write Event.</span></span>

<span data-ttu-id="26363-2267">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2267">**Information Fields**</span></span>

- <span data-ttu-id="26363-2268">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2268">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2269">情報フィールド 2: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-2269">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="26363-2270">情報フィールド 3: 要求された長さ。</span><span class="sxs-lookup"><span data-stu-id="26363-2270">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="26363-2271">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2271">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-activate"></a><span data-ttu-id="26363-2272">ホスト クラス Storage アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-2272">Host Class Storage Activate</span></span> 

#### <a name="ux_host_class_storage_activate"></a><span data-ttu-id="26363-2273">ux_host_class_storage_activate</span><span class="sxs-lookup"><span data-stu-id="26363-2273">ux_host_class_storage_activate</span></span>

<span data-ttu-id="26363-2274">**アイコン** ![ホスト クラス Storage アクティブ化アイコン](./media/user-guide/usbx-events/image174.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2274">**Icon** ![Host Class Storage Activate icon](./media/user-guide/usbx-events/image174.png)</span></span>

<span data-ttu-id="26363-2275">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2275">**Description**</span></span>

<span data-ttu-id="26363-2276">USBX ホスト クラス Storage アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2276">This event represents a USBX Host Class Storage Activate Event.</span></span>

<span data-ttu-id="26363-2277">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2277">**Information Fields**</span></span>

- <span data-ttu-id="26363-2278">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2278">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2279">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2279">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2280">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2280">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2281">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2281">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-deactivate"></a><span data-ttu-id="26363-2282">ホスト クラス Storage 非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="26363-2282">Host Class Storage Deactivate</span></span> 

#### <a name="ux_host_class_storage_deactivate"></a><span data-ttu-id="26363-2283">ux_host_class_storage_deactivate</span><span class="sxs-lookup"><span data-stu-id="26363-2283">ux_host_class_storage_deactivate</span></span>

<span data-ttu-id="26363-2284">**アイコン** ![ホスト クラス Storage 非アクティブ化アイコン](./media/user-guide/usbx-events/image175.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2284">**Icon** ![Host Class Storage Deactivate icon](./media/user-guide/usbx-events/image175.png)</span></span>

<span data-ttu-id="26363-2285">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2285">**Description**</span></span>

<span data-ttu-id="26363-2286">USBX ホスト クラス Storage 非アクティブ化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2286">This event represents a USBX Host Class Storage Deactivate Event.</span></span>

<span data-ttu-id="26363-2287">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2287">**Information Fields**</span></span>

- <span data-ttu-id="26363-2288">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2288">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2289">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2289">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2290">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2290">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2291">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2291">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-capacity-get"></a><span data-ttu-id="26363-2292">ホスト クラス Storage メディア容量取得</span><span class="sxs-lookup"><span data-stu-id="26363-2292">Host Class Storage Media Capacity Get</span></span> 

#### <a name="ux_host_class_storage_media_capacity_get"></a><span data-ttu-id="26363-2293">ux_host_class_storage_media_capacity_get</span><span class="sxs-lookup"><span data-stu-id="26363-2293">ux_host_class_storage_media_capacity_get</span></span>

<span data-ttu-id="26363-2294">**アイコン** ![ホスト クラス Storage メディア容量取得アイコン](./media/user-guide/usbx-events/image176.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2294">**Icon** ![Host Class Storage Media Capacity Get icon](./media/user-guide/usbx-events/image176.png)</span></span>

<span data-ttu-id="26363-2295">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2295">**Description**</span></span>

<span data-ttu-id="26363-2296">USBX ホスト クラス Storage メディア容量取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2296">This event represents a USBX Host Class Storage Media Capacity Get Event.</span></span>

<span data-ttu-id="26363-2297">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2297">**Information Fields**</span></span>

- <span data-ttu-id="26363-2298">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2298">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2299">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2299">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2300">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2300">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2301">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2301">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-format-capacity-get"></a><span data-ttu-id="26363-2302">ホスト クラス Storage メディア フォーマット容量取得</span><span class="sxs-lookup"><span data-stu-id="26363-2302">Host Class Storage Media Format Capacity Get</span></span>

#### <a name="ux_host_class_storage_media_format_capacity_get"></a><span data-ttu-id="26363-2303">ux_host_class_storage_media_format_capacity_get</span><span class="sxs-lookup"><span data-stu-id="26363-2303">ux_host_class_storage_media_format_capacity_get</span></span>

<span data-ttu-id="26363-2304">**アイコン** ![ホスト クラス Storage メディア フォーマット容量取得アイコン](./media/user-guide/usbx-events/image177.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2304">**Icon** ![Host Class Storage Media Format Capacity Get icon](./media/user-guide/usbx-events/image177.png)</span></span>

<span data-ttu-id="26363-2305">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2305">**Description**</span></span>

<span data-ttu-id="26363-2306">USBX ホスト クラス Storage メディア フォーマット容量取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2306">This event represents a USBX Host Class Storage Media Format Capacity Get Event.</span></span>

<span data-ttu-id="26363-2307">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2307">**Information Fields**</span></span>

- <span data-ttu-id="26363-2308">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2308">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2309">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2309">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2310">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2310">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2311">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2311">Info Field 4: Not used.</span></span>

#### <a name="host-class-storage-media-mount"></a><span data-ttu-id="26363-2312">ホスト クラス Storage メディア マウント</span><span class="sxs-lookup"><span data-stu-id="26363-2312">Host Class Storage Media Mount</span></span> 

#### <a name="ux_host_class_storage_media_mount"></a><span data-ttu-id="26363-2313">ux_host_class_storage_media_mount</span><span class="sxs-lookup"><span data-stu-id="26363-2313">ux_host_class_storage_media_mount</span></span>

<span data-ttu-id="26363-2314">**アイコン** ![ホスト クラス Storage メディア マウント アイコン](./media/user-guide/usbx-events/image178.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2314">**Icon** ![Host Class Storage Media Mount icon](./media/user-guide/usbx-events/image178.png)</span></span>

<span data-ttu-id="26363-2315">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2315">**Description**</span></span>

<span data-ttu-id="26363-2316">USBX ホスト クラス Storage メディア マウント イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2316">This event represents a USBX Host Class Storage Media Mount Event.</span></span>

<span data-ttu-id="26363-2317">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2317">**Information Fields**</span></span>

- <span data-ttu-id="26363-2318">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2318">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2319">情報フィールド 2: セクター。</span><span class="sxs-lookup"><span data-stu-id="26363-2319">Info Field 2: Sector.</span></span>
- <span data-ttu-id="26363-2320">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2320">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2321">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2321">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-open"></a><span data-ttu-id="26363-2322">ホスト クラス Storage メディア オープン</span><span class="sxs-lookup"><span data-stu-id="26363-2322">Host Class Storage Media Open</span></span> 

#### <a name="ux_host_class_storage_media_open"></a><span data-ttu-id="26363-2323">ux_host_class_storage_media_open</span><span class="sxs-lookup"><span data-stu-id="26363-2323">ux_host_class_storage_media_open</span></span>

<span data-ttu-id="26363-2324">**アイコン** ![ホスト クラス Storage メディア オープン アイコン](./media/user-guide/usbx-events/image179.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2324">**Icon** ![Host Class Storage Media Open icon](./media/user-guide/usbx-events/image179.png)</span></span>

<span data-ttu-id="26363-2325">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2325">**Description**</span></span>

<span data-ttu-id="26363-2326">USBX ホスト クラス Storage メディア オープン イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2326">This event represents a USBX Host Class Storage Media Open Event.</span></span>

<span data-ttu-id="26363-2327">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2327">**Information Fields**</span></span>

- <span data-ttu-id="26363-2328">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2328">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2329">情報フィールド 2: メディア。</span><span class="sxs-lookup"><span data-stu-id="26363-2329">Info Field 2: Media.</span></span>
- <span data-ttu-id="26363-2330">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2330">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2331">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2331">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-read"></a><span data-ttu-id="26363-2332">ホスト クラス Storage メディア読み取り</span><span class="sxs-lookup"><span data-stu-id="26363-2332">Host Class Storage Media Read</span></span> 

#### <a name="ux_host_class_storage_media_read"></a><span data-ttu-id="26363-2333">ux_host_class_storage_media_read</span><span class="sxs-lookup"><span data-stu-id="26363-2333">ux_host_class_storage_media_read</span></span>

<span data-ttu-id="26363-2334">**アイコン** ![ホスト クラス Storage メディア読み取りアイコン](./media/user-guide/usbx-events/image180.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2334">**Icon** ![Host Class Storage Media Read icon](./media/user-guide/usbx-events/image180.png)</span></span>

<span data-ttu-id="26363-2335">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2335">**Description**</span></span>

<span data-ttu-id="26363-2336">USBX ホスト クラス Storage メディア読み取りイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2336">This event represents a USBX Host Class Storage Media Read Event.</span></span>

<span data-ttu-id="26363-2337">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2337">**Information Fields**</span></span>

- <span data-ttu-id="26363-2338">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2338">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2339">情報フィールド 2: セクターの開始位置。</span><span class="sxs-lookup"><span data-stu-id="26363-2339">Info Field 2: Sector start.</span></span>
- <span data-ttu-id="26363-2340">情報フィールド 3: セクター数。</span><span class="sxs-lookup"><span data-stu-id="26363-2340">Info Field 3: Sector count.</span></span>
- <span data-ttu-id="26363-2341">情報フィールド 4: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-2341">Info Field 4: Data pointer.</span></span>

### <a name="host-class-storage-media-write"></a><span data-ttu-id="26363-2342">ホスト クラス Storage メディア書き込み</span><span class="sxs-lookup"><span data-stu-id="26363-2342">Host Class Storage Media Write</span></span> 

#### <a name="ux_host_class_storage_media_write"></a><span data-ttu-id="26363-2343">ux_host_class_storage_media_write</span><span class="sxs-lookup"><span data-stu-id="26363-2343">ux_host_class_storage_media_write</span></span>

<span data-ttu-id="26363-2344">**アイコン** ![ホスト クラス Storage メディア書き込みアイコン](./media/user-guide/usbx-events/image181.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2344">**Icon** ![Host Class Storage Media Write icon](./media/user-guide/usbx-events/image181.png)</span></span>

<span data-ttu-id="26363-2345">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2345">**Description**</span></span>

<span data-ttu-id="26363-2346">USBX ホスト クラス Storage メディア書き込みイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2346">This event represents a USBX Host Class Storage Media Write Event.</span></span>

<span data-ttu-id="26363-2347">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2347">**Information Fields**</span></span>

- <span data-ttu-id="26363-2348">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2348">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2349">情報フィールド 2: セクターの開始位置。</span><span class="sxs-lookup"><span data-stu-id="26363-2349">Info Field 2: Sector start.</span></span>
- <span data-ttu-id="26363-2350">情報フィールド 3: セクター数。</span><span class="sxs-lookup"><span data-stu-id="26363-2350">Info Field 3: Sector count.</span></span>
- <span data-ttu-id="26363-2351">情報フィールド 4: データ ポインター。</span><span class="sxs-lookup"><span data-stu-id="26363-2351">Info Field 4: Data pointer.</span></span>

### <a name="host-class-storage-request-sense"></a><span data-ttu-id="26363-2352">ホスト クラス Storage センス データ要求</span><span class="sxs-lookup"><span data-stu-id="26363-2352">Host Class Storage Request Sense</span></span> 

#### <a name="ux_host_class_storage_request_sense"></a><span data-ttu-id="26363-2353">ux_host_class_storage_request_sense</span><span class="sxs-lookup"><span data-stu-id="26363-2353">ux_host_class_storage_request_sense</span></span>

<span data-ttu-id="26363-2354">**アイコン** ![ホスト クラス Storage センス データ要求アイコン](./media/user-guide/usbx-events/image182.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2354">**Icon** ![Host Class Storage Request Sense icon](./media/user-guide/usbx-events/image182.png)</span></span>

<span data-ttu-id="26363-2355">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2355">**Description**</span></span>

<span data-ttu-id="26363-2356">USBX ホスト クラス Storage センス データ要求イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2356">This event represents a USBX Host Class Storage Request Sense Event.</span></span>

<span data-ttu-id="26363-2357">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2357">**Information Fields**</span></span>

- <span data-ttu-id="26363-2358">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2358">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2359">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2359">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2360">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2360">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2361">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2361">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-start-stop"></a><span data-ttu-id="26363-2362">ホスト クラス Storage 開始/停止</span><span class="sxs-lookup"><span data-stu-id="26363-2362">Host Class Storage Start Stop</span></span> 

#### <a name="ux_host_class_storage_start_stop"></a><span data-ttu-id="26363-2363">ux_host_class_storage_start_stop</span><span class="sxs-lookup"><span data-stu-id="26363-2363">ux_host_class_storage_start_stop</span></span>

<span data-ttu-id="26363-2364">**アイコン** ![ホスト クラス Storage 開始/停止アイコン](./media/user-guide/usbx-events/image183.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2364">**Icon** ![Host Class Storage Start Stop icon](./media/user-guide/usbx-events/image183.png)</span></span>

<span data-ttu-id="26363-2365">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2365">**Description**</span></span>

<span data-ttu-id="26363-2366">USBX ホスト クラス Storage 開始/停止イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2366">This event represents a USBX Host Class Storage Start Stop Event.</span></span>

<span data-ttu-id="26363-2367">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2367">**Information Fields**</span></span>

- <span data-ttu-id="26363-2368">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2368">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2369">情報フィールド 2: 開始/停止信号。</span><span class="sxs-lookup"><span data-stu-id="26363-2369">Info Field 2: Start stop signal.</span></span>
- <span data-ttu-id="26363-2370">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2370">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2371">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2371">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-unit-ready-test"></a><span data-ttu-id="26363-2372">ホスト クラス Storage ユニット準備状態テスト</span><span class="sxs-lookup"><span data-stu-id="26363-2372">Host Class Storage Unit Ready Test</span></span> 

#### <a name="ux_host_class_storage_unit_ready_test"></a><span data-ttu-id="26363-2373">ux_host_class_storage_unit_ready_test</span><span class="sxs-lookup"><span data-stu-id="26363-2373">ux_host_class_storage_unit_ready_test</span></span>

<span data-ttu-id="26363-2374">**アイコン** ![ホスト クラス Storage ユニット準備状態テスト アイコン](./media/user-guide/usbx-events/image184.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2374">**Icon** ![Host Class Storage Unit Ready Test icon](./media/user-guide/usbx-events/image184.png)</span></span>

<span data-ttu-id="26363-2375">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2375">**Description**</span></span>

<span data-ttu-id="26363-2376">USBX ホスト クラス Storage ユニット準備状態テスト イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2376">This event represents a USBX Host Class Storage Unit Ready Test Event.</span></span>

<span data-ttu-id="26363-2377">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2377">**Information Fields**</span></span>

- <span data-ttu-id="26363-2378">情報フィールド 1: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2378">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="26363-2379">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2379">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2380">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2380">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2381">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2381">Info Field 4: Not used.</span></span>

### <a name="host-stack-class-instance-create"></a><span data-ttu-id="26363-2382">ホスト スタック クラス インスタンス作成</span><span class="sxs-lookup"><span data-stu-id="26363-2382">Host Stack Class Instance Create</span></span> 

#### <a name="ux_host_class_instance_create"></a><span data-ttu-id="26363-2383">ux_host_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="26363-2383">ux_host_class_instance_create</span></span>

<span data-ttu-id="26363-2384">**アイコン** ![ホスト スタック クラス インスタンス作成アイコン](./media/user-guide/usbx-events/image185.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2384">**Icon** ![Host Stack Class Instance Create icon](./media/user-guide/usbx-events/image185.png)</span></span>

<span data-ttu-id="26363-2385">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2385">**Description**</span></span>

<span data-ttu-id="26363-2386">USBX ホスト スタック クラス インスタンス作成イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2386">This event represents a USBX Host Stack Class Instance Create Event.</span></span>

<span data-ttu-id="26363-2387">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2387">**Information Fields**</span></span>

- <span data-ttu-id="26363-2388">情報フィールド 1: クラス。</span><span class="sxs-lookup"><span data-stu-id="26363-2388">Info Field 1: Class.</span></span>
- <span data-ttu-id="26363-2389">情報フィールド 2: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2389">Info Field 2: Class Instance.</span></span>
- <span data-ttu-id="26363-2390">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2390">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2391">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2391">Info Field 4: Not used.</span></span>

### <a name="host-stack-class-instance-destroy"></a><span data-ttu-id="26363-2392">ホスト スタック クラス インスタンス破棄</span><span class="sxs-lookup"><span data-stu-id="26363-2392">Host Stack Class Instance Destroy</span></span> 

#### <a name="ux_host_class_instance_create"></a><span data-ttu-id="26363-2393">ux_host_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="26363-2393">ux_host_class_instance_create</span></span>

<span data-ttu-id="26363-2394">**アイコン** ![ホスト スタック クラス インスタンス破棄アイコン](./media/user-guide/usbx-events/image186.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2394">**Icon** ![Host Stack Class Instance Destroy icon](./media/user-guide/usbx-events/image186.png)</span></span>

<span data-ttu-id="26363-2395">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2395">**Description**</span></span>

<span data-ttu-id="26363-2396">USBX ホスト スタック クラス インスタンス破棄イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2396">This event represents a USBX Host Stack Class Instance Destroy Event.</span></span>

<span data-ttu-id="26363-2397">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2397">**Information Fields**</span></span>

- <span data-ttu-id="26363-2398">情報フィールド 1: クラス。</span><span class="sxs-lookup"><span data-stu-id="26363-2398">Info Field 1: Class.</span></span>
- <span data-ttu-id="26363-2399">情報フィールド 2: クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="26363-2399">Info Field 2: Class Instance.</span></span>
- <span data-ttu-id="26363-2400">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2400">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2401">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2401">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-delete"></a><span data-ttu-id="26363-2402">ホスト スタック構成削除</span><span class="sxs-lookup"><span data-stu-id="26363-2402">Host Stack Configuration Delete</span></span> 

#### <a name="ux_host_class_configuration_delete"></a><span data-ttu-id="26363-2403">ux_host_class_configuration_delete</span><span class="sxs-lookup"><span data-stu-id="26363-2403">ux_host_class_configuration_delete</span></span>

<span data-ttu-id="26363-2404">**アイコン** ![ホスト スタック構成削除アイコン](./media/user-guide/usbx-events/image187.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2404">**Icon** ![Host Stack Configuration Delete icon](./media/user-guide/usbx-events/image187.png)</span></span>

<span data-ttu-id="26363-2405">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2405">**Description**</span></span>

<span data-ttu-id="26363-2406">USBX ホスト スタック構成削除イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2406">This event represents a USBX Host Stack Configuration Delete Event.</span></span>

<span data-ttu-id="26363-2407">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2407">**Information Fields**</span></span>

- <span data-ttu-id="26363-2408">情報フィールド 1: 構成。</span><span class="sxs-lookup"><span data-stu-id="26363-2408">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="26363-2409">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2409">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2410">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2410">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2411">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2411">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-enumerate"></a><span data-ttu-id="26363-2412">ホスト スタック構成エニュメレーション</span><span class="sxs-lookup"><span data-stu-id="26363-2412">Host Stack Configuration Enumerate</span></span> 

#### <a name="ux_host_stack_configuration_enumerate"></a><span data-ttu-id="26363-2413">ux_host_stack_configuration_enumerate</span><span class="sxs-lookup"><span data-stu-id="26363-2413">ux_host_stack_configuration_enumerate</span></span>

<span data-ttu-id="26363-2414">**アイコン** ![ホスト スタック構成エニュメレーション アイコン](./media/user-guide/usbx-events/image188.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2414">**Icon** ![Host Stack Configuration Enumerate icon](./media/user-guide/usbx-events/image188.png)</span></span>

<span data-ttu-id="26363-2415">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2415">**Description**</span></span>

<span data-ttu-id="26363-2416">USBX ホスト スタック構成エニュメレーション イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2416">This event represents a USBX Host Stack Configuration Enumerate Event.</span></span>

<span data-ttu-id="26363-2417">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2417">**Information Fields**</span></span>

- <span data-ttu-id="26363-2418">情報フィールド 1: デバイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2418">Info Field 1: Device.</span></span>
- <span data-ttu-id="26363-2419">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2419">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2420">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2420">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2421">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2421">Info Field 4: Not used.</span></span>

### <a name="stack-configuration-instance-create"></a><span data-ttu-id="26363-2422">スタック構成インスタンス作成</span><span class="sxs-lookup"><span data-stu-id="26363-2422">Stack Configuration Instance Create</span></span> 

#### <a name="ux_host_stack_configuration_instance_create"></a><span data-ttu-id="26363-2423">ux_host_stack_configuration_instance_create</span><span class="sxs-lookup"><span data-stu-id="26363-2423">ux_host_stack_configuration_instance_create</span></span>

<span data-ttu-id="26363-2424">**アイコン** ![スタック構成インスタンス作成アイコン](./media/user-guide/usbx-events/image189.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2424">**Icon** ![Stack Configuration Instance Create icon](./media/user-guide/usbx-events/image189.png)</span></span>

<span data-ttu-id="26363-2425">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2425">**Description**</span></span>

<span data-ttu-id="26363-2426">USBX ホスト スタック構成インスタンス作成イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2426">This event represents a USBX Host Stack Configuration Instance Create Event.</span></span>

<span data-ttu-id="26363-2427">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2427">**Information Fields**</span></span>

- <span data-ttu-id="26363-2428">情報フィールド 1: 構成。</span><span class="sxs-lookup"><span data-stu-id="26363-2428">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="26363-2429">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2429">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2430">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2430">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2431">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2431">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-instance-delete"></a><span data-ttu-id="26363-2432">ホスト スタック構成インスタンス削除</span><span class="sxs-lookup"><span data-stu-id="26363-2432">Host Stack Configuration Instance Delete</span></span> 

#### <a name="ux_host_stack_configuration_instance_delete"></a><span data-ttu-id="26363-2433">ux_host_stack_configuration_instance_delete</span><span class="sxs-lookup"><span data-stu-id="26363-2433">ux_host_stack_configuration_instance_delete</span></span>

<span data-ttu-id="26363-2434">**アイコン** ![ホスト スタック構成インスタンス削除アイコン](./media/user-guide/usbx-events/image190.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2434">**Icon** ![Host Stack Configuration Instance Delete icon](./media/user-guide/usbx-events/image190.png)</span></span>

<span data-ttu-id="26363-2435">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2435">**Description**</span></span>

<span data-ttu-id="26363-2436">USBX ホスト スタック構成インスタンス削除イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2436">This event represents a USBX Host Stack Configuration Instance Delete Event.</span></span>

<span data-ttu-id="26363-2437">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2437">**Information Fields**</span></span>

- <span data-ttu-id="26363-2438">情報フィールド 1: 構成。</span><span class="sxs-lookup"><span data-stu-id="26363-2438">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="26363-2439">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2439">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2440">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2440">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2441">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2441">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-set"></a><span data-ttu-id="26363-2442">ホスト スタック構成設定</span><span class="sxs-lookup"><span data-stu-id="26363-2442">Host Stack Configuration Set</span></span> 

#### <a name="ux_host_stack_configuration_set"></a><span data-ttu-id="26363-2443">ux_host_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="26363-2443">ux_host_stack_configuration_set</span></span>

<span data-ttu-id="26363-2444">**アイコン** ![ホスト スタック構成設定アイコン](./media/user-guide/usbx-events/image191.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2444">**Icon** ![Host Stack Configuration Set icon](./media/user-guide/usbx-events/image191.png)</span></span>

<span data-ttu-id="26363-2445">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2445">**Description**</span></span>

<span data-ttu-id="26363-2446">USBX ホスト スタック構成設定イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2446">This event represents a USBX Host Stack Configuration Set Event.</span></span>

<span data-ttu-id="26363-2447">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2447">**Information Fields**</span></span>

- <span data-ttu-id="26363-2448">情報フィールド 1: 構成。</span><span class="sxs-lookup"><span data-stu-id="26363-2448">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="26363-2449">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2449">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2450">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2450">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2451">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2451">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-address-set"></a><span data-ttu-id="26363-2452">ホスト スタック デバイス アドレス設定</span><span class="sxs-lookup"><span data-stu-id="26363-2452">Host Stack Device Address Set</span></span> 

#### <a name="ux_host_stack_device_address_set"></a><span data-ttu-id="26363-2453">ux_host_stack_device_address_set</span><span class="sxs-lookup"><span data-stu-id="26363-2453">ux_host_stack_device_address_set</span></span>

<span data-ttu-id="26363-2454">**アイコン** ![ホスト スタック デバイス アドレス設定アイコン](./media/user-guide/usbx-events/image192.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2454">**Icon** ![Host Stack Device Address Set icon](./media/user-guide/usbx-events/image192.png)</span></span>

<span data-ttu-id="26363-2455">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2455">**Description**</span></span>

<span data-ttu-id="26363-2456">USBX ホスト スタック デバイス アドレス設定イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2456">This event represents a USBX Host Stack Device Address Set Event.</span></span>

<span data-ttu-id="26363-2457">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2457">**Information Fields**</span></span>

- <span data-ttu-id="26363-2458">情報フィールド 1: デバイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2458">Info Field 1: Device.</span></span>
- <span data-ttu-id="26363-2459">情報フィールド 2: デバイスのアドレス。</span><span class="sxs-lookup"><span data-stu-id="26363-2459">Info Field 2: Device Address.</span></span>
- <span data-ttu-id="26363-2460">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2460">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2461">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2461">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-configuration-get"></a><span data-ttu-id="26363-2462">ホスト スタック デバイス構成取得</span><span class="sxs-lookup"><span data-stu-id="26363-2462">Host Stack Device Configuration Get</span></span> 

#### <a name="ux_host_stack_device_configuration_get"></a><span data-ttu-id="26363-2463">ux_host_stack_device_configuration_get</span><span class="sxs-lookup"><span data-stu-id="26363-2463">ux_host_stack_device_configuration_get</span></span>

<span data-ttu-id="26363-2464">**アイコン** ![ホスト スタック デバイス構成取得アイコン](./media/user-guide/usbx-events/image193.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2464">**Icon** ![Host Stack Device Configuration Get icon](./media/user-guide/usbx-events/image193.png)</span></span>

<span data-ttu-id="26363-2465">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2465">**Description**</span></span>

<span data-ttu-id="26363-2466">USBX ホスト スタック デバイス構成取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2466">This event represents a USBX Host Stack Device Configuration Get Event.</span></span>

<span data-ttu-id="26363-2467">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2467">**Information Fields**</span></span>

- <span data-ttu-id="26363-2468">情報フィールド 1: デバイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2468">Info Field 1: Device.</span></span>
- <span data-ttu-id="26363-2469">情報フィールド 2: 構成。</span><span class="sxs-lookup"><span data-stu-id="26363-2469">nfo Field 2: Configuration.</span></span>
- <span data-ttu-id="26363-2470">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2470">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2471">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2471">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-configuration-select"></a><span data-ttu-id="26363-2472">ホスト スタック デバイス構成選択</span><span class="sxs-lookup"><span data-stu-id="26363-2472">Host Stack Device Configuration Select</span></span> 

#### <a name="ux_host_stack_device_configuration_select"></a><span data-ttu-id="26363-2473">ux_host_stack_device_configuration_select</span><span class="sxs-lookup"><span data-stu-id="26363-2473">ux_host_stack_device_configuration_select</span></span>

<span data-ttu-id="26363-2474">**アイコン** ![ホスト スタック デバイス構成選択アイコン](./media/user-guide/usbx-events/image194.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2474">**Icon** ![Host Stack Device Configuration Select icon](./media/user-guide/usbx-events/image194.png)</span></span>

<span data-ttu-id="26363-2475">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2475">**Description**</span></span>

<span data-ttu-id="26363-2476">USBX ホスト スタック デバイス構成選択イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2476">This event represents a USBX Host Stack Device Configuration Select Event.</span></span>

<span data-ttu-id="26363-2477">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2477">**Information Fields**</span></span>

- <span data-ttu-id="26363-2478">情報フィールド 1: デバイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2478">Info Field 1: Device.</span></span>
- <span data-ttu-id="26363-2479">情報フィールド 2: 構成。</span><span class="sxs-lookup"><span data-stu-id="26363-2479">Info Field 2: Configuration.</span></span>
- <span data-ttu-id="26363-2480">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2480">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2481">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2481">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-descriptor-read"></a><span data-ttu-id="26363-2482">ホスト スタック デバイス記述子読み取り</span><span class="sxs-lookup"><span data-stu-id="26363-2482">Host Stack Device Descriptor Read</span></span> 

#### <a name="ux_host_stack_device_descriptor_read"></a><span data-ttu-id="26363-2483">ux_host_stack_device_descriptor_read</span><span class="sxs-lookup"><span data-stu-id="26363-2483">ux_host_stack_device_descriptor_read</span></span>

<span data-ttu-id="26363-2484">**アイコン** ![ホスト スタック デバイス記述子読み取りアイコン](./media/user-guide/usbx-events/image195.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2484">**Icon** ![Host Stack Device Descriptor Read icon](./media/user-guide/usbx-events/image195.png)</span></span>

<span data-ttu-id="26363-2485">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2485">**Description**</span></span>

<span data-ttu-id="26363-2486">USBX ホスト スタック デバイス記述子読み取りイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2486">This event represents a USBX Host Stack Device Descriptor Read Event.</span></span>

<span data-ttu-id="26363-2487">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2487">**Information Fields**</span></span>

- <span data-ttu-id="26363-2488">情報フィールド 1: デバイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2488">Info Field 1: Device.</span></span>
- <span data-ttu-id="26363-2489">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2489">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2490">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2490">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2491">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2491">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-get"></a><span data-ttu-id="26363-2492">ホスト スタック デバイス取得</span><span class="sxs-lookup"><span data-stu-id="26363-2492">Host Stack Device Get</span></span> 

#### <a name="ux_host_stack_device_get"></a><span data-ttu-id="26363-2493">ux_host_stack_device_get</span><span class="sxs-lookup"><span data-stu-id="26363-2493">ux_host_stack_device_get</span></span>

<span data-ttu-id="26363-2494">**アイコン** ![ホスト スタック デバイス取得アイコン](./media/user-guide/usbx-events/image196.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2494">**Icon** ![Host Stack Device Get icon](./media/user-guide/usbx-events/image196.png)</span></span>

<span data-ttu-id="26363-2495">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2495">**Description**</span></span>

<span data-ttu-id="26363-2496">USBX ホスト スタック デバイス取得イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2496">This event represents a USBX Host Stack Device Get Event.</span></span>

<span data-ttu-id="26363-2497">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2497">**Information Fields**</span></span>

- <span data-ttu-id="26363-2498">情報フィールド 1: デバイスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="26363-2498">Info Field 1: Device index.</span></span>
- <span data-ttu-id="26363-2499">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2499">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2500">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2500">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2501">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2501">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-remove"></a><span data-ttu-id="26363-2502">ホスト スタック デバイス取り外し</span><span class="sxs-lookup"><span data-stu-id="26363-2502">Host Stack Device Remove</span></span> 

#### <a name="ux_host_stack_device_remove"></a><span data-ttu-id="26363-2503">ux_host_stack_device_remove</span><span class="sxs-lookup"><span data-stu-id="26363-2503">ux_host_stack_device_remove</span></span>

<span data-ttu-id="26363-2504">**アイコン** ![ホスト スタック デバイス取り外しアイコン](./media/user-guide/usbx-events/image197.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2504">**Icon** ![Host Stack Device Remove icon](./media/user-guide/usbx-events/image197.png)</span></span>

<span data-ttu-id="26363-2505">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2505">**Description**</span></span>

<span data-ttu-id="26363-2506">USBX ホスト スタック デバイス取り外しイベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2506">This event represents a USBX Host Stack Device Remove Event.</span></span>

<span data-ttu-id="26363-2507">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2507">**Information Fields**</span></span>

- <span data-ttu-id="26363-2508">情報フィールド 1: HCD。</span><span class="sxs-lookup"><span data-stu-id="26363-2508">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="26363-2509">情報フィールド 2: 親。</span><span class="sxs-lookup"><span data-stu-id="26363-2509">Info Field 2: Parent.</span></span>
- <span data-ttu-id="26363-2510">情報フィールド 3: ポートのインデックス。</span><span class="sxs-lookup"><span data-stu-id="26363-2510">Info Field 3: Port Index.</span></span>
- <span data-ttu-id="26363-2511">情報フィールド 4: デバイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2511">Info Field 4: Device.</span></span>

### <a name="host-stack-device-resource-free"></a><span data-ttu-id="26363-2512">ホスト スタック デバイス リソース解放</span><span class="sxs-lookup"><span data-stu-id="26363-2512">Host Stack Device Resource Free</span></span> 

#### <a name="ux_host_stack_device_resource_free"></a><span data-ttu-id="26363-2513">ux_host_stack_device_resource_free</span><span class="sxs-lookup"><span data-stu-id="26363-2513">ux_host_stack_device_resource_free</span></span>

<span data-ttu-id="26363-2514">**アイコン** ![ホスト スタック デバイス リソース解放アイコン](./media/user-guide/usbx-events/image198.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2514">**Icon** ![Host Stack Device Resource Free icon](./media/user-guide/usbx-events/image198.png)</span></span>

<span data-ttu-id="26363-2515">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2515">**Description**</span></span>

<span data-ttu-id="26363-2516">USBX ホスト スタック デバイス リソース解放イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2516">This event represents a USBX Host Stack Device Resource Free Event.</span></span>

<span data-ttu-id="26363-2517">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2517">**Information Fields**</span></span>

- <span data-ttu-id="26363-2518">情報フィールド 1: デバイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2518">Info Field 1: Device.</span></span>
- <span data-ttu-id="26363-2519">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2519">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2520">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2520">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2521">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2521">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-instance-create"></a><span data-ttu-id="26363-2522">ホスト スタック エンドポイント インスタンス作成</span><span class="sxs-lookup"><span data-stu-id="26363-2522">Host Stack Endpoint Instance Create</span></span> 

#### <a name="ux_host_stack_endpoint_instance_create"></a><span data-ttu-id="26363-2523">ux_host_stack_endpoint_instance_create</span><span class="sxs-lookup"><span data-stu-id="26363-2523">ux_host_stack_endpoint_instance_create</span></span>

<span data-ttu-id="26363-2524">**アイコン** ![ホスト スタック エンドポイント インスタンス作成アイコン](./media/user-guide/usbx-events/image199.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2524">**Icon** ![Host Stack Endpoint Instance Create icon](./media/user-guide/usbx-events/image199.png)</span></span>

<span data-ttu-id="26363-2525">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2525">**Description**</span></span>

<span data-ttu-id="26363-2526">USBX ホスト スタック エンドポイント インスタンス作成イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2526">This event represents a USBX Host Stack Endpoint Instance Create Event.</span></span>

<span data-ttu-id="26363-2527">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2527">**Information Fields**</span></span>

- <span data-ttu-id="26363-2528">情報フィールド 1: デバイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2528">Info Field 1: Device.</span></span>
- <span data-ttu-id="26363-2529">情報フィールド 2: エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="26363-2529">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="26363-2530">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2530">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2531">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2531">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-instance-delete"></a><span data-ttu-id="26363-2532">ホスト スタック エンドポイント インスタンス削除</span><span class="sxs-lookup"><span data-stu-id="26363-2532">Host Stack Endpoint Instance Delete</span></span> 

#### <a name="ux_host_stack_endpoint_instance_delete"></a><span data-ttu-id="26363-2533">ux_host_stack_endpoint_instance_delete</span><span class="sxs-lookup"><span data-stu-id="26363-2533">ux_host_stack_endpoint_instance_delete</span></span>

<span data-ttu-id="26363-2534">**アイコン](./media/user-guide/usbx-events/image200.png)** ホスト スタック エンドポイント インスタンス削除アイコン![</span><span class="sxs-lookup"><span data-stu-id="26363-2534">**Icon** ![Host Stack Endpoint Instance Delete icon](./media/user-guide/usbx-events/image200.png)</span></span>

<span data-ttu-id="26363-2535">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2535">**Description**</span></span>

<span data-ttu-id="26363-2536">USBX ホスト スタック エンドポイント インスタンス削除イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2536">This event represents a USBX Host Stack Endpoint Instance Delete Event.</span></span>

<span data-ttu-id="26363-2537">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2537">**Information Fields**</span></span>

- <span data-ttu-id="26363-2538">情報フィールド 2: エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="26363-2538">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="26363-2539">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2539">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2540">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2540">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-reset"></a><span data-ttu-id="26363-2541">ホスト スタック エンドポイント リセット</span><span class="sxs-lookup"><span data-stu-id="26363-2541">Host Stack Endpoint Reset</span></span> 

#### <a name="ux_host_stack_endpoint_reset"></a><span data-ttu-id="26363-2542">ux_host_stack_endpoint_reset</span><span class="sxs-lookup"><span data-stu-id="26363-2542">ux_host_stack_endpoint_reset</span></span>

<span data-ttu-id="26363-2543">**アイコン** ![ホスト スタック エンドポイント リセット アイコン](./media/user-guide/usbx-events/image201.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2543">**Icon** ![Host Stack Endpoint Reset icon](./media/user-guide/usbx-events/image201.png)</span></span>

<span data-ttu-id="26363-2544">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2544">**Description**</span></span>

<span data-ttu-id="26363-2545">USBX ホスト スタック エンドポイント リセット イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2545">This event represents a USBX Host Stack Endpoint Reset Event.</span></span>

<span data-ttu-id="26363-2546">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2546">**Information Fields**</span></span>

- <span data-ttu-id="26363-2547">情報フィールド 1: デバイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2547">Info Field 1: Device.</span></span>
- <span data-ttu-id="26363-2548">情報フィールド 2: エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="26363-2548">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="26363-2549">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2549">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2550">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2550">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-transfer-abort"></a><span data-ttu-id="26363-2551">ホスト スタック エンドポイント転送アボート</span><span class="sxs-lookup"><span data-stu-id="26363-2551">Host Stack Endpoint Transfer Abort</span></span> 

#### <a name="ux_host_stack_endpoint_transfer_abort"></a><span data-ttu-id="26363-2552">ux_host_stack_endpoint_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="26363-2552">ux_host_stack_endpoint_transfer_abort</span></span>

<span data-ttu-id="26363-2553">**アイコン** ![ホスト スタック エンドポイント転送アボート アイコン](./media/user-guide/usbx-events/image202.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2553">**Icon** ![Host Stack Endpoint Transfer Abort icon](./media/user-guide/usbx-events/image202.png)</span></span>

<span data-ttu-id="26363-2554">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2554">**Description**</span></span>

<span data-ttu-id="26363-2555">USBX ホスト スタック エンドポイント転送アボート イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2555">This event represents a USBX Host Stack Endpoint Transfer Abort Event.</span></span>

<span data-ttu-id="26363-2556">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2556">**Information Fields**</span></span>

- <span data-ttu-id="26363-2557">情報フィールド 1: エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="26363-2557">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="26363-2558">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2558">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2559">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2559">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2560">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2560">Info Field 4: Not used.</span></span>

### <a name="host-stack-host-controller-register"></a><span data-ttu-id="26363-2561">ホスト スタック ホスト コントローラー登録</span><span class="sxs-lookup"><span data-stu-id="26363-2561">Host Stack Host Controller Register</span></span> 

#### <a name="ux_host_stack_hcd_register"></a><span data-ttu-id="26363-2562">ux_host_stack_hcd_register</span><span class="sxs-lookup"><span data-stu-id="26363-2562">ux_host_stack_hcd_register</span></span>

<span data-ttu-id="26363-2563">**アイコン** ![ホスト スタック ホスト コントローラー登録アイコン](./media/user-guide/usbx-events/image203.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2563">**Icon** ![Host Stack Host Controller Register icon](./media/user-guide/usbx-events/image203.png)</span></span>

<span data-ttu-id="26363-2564">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2564">**Description**</span></span>

<span data-ttu-id="26363-2565">USBX ホスト スタック ホスト コントローラー登録イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2565">This event represents a USBX Host Stack Host Controller Register.</span></span>

<span data-ttu-id="26363-2566">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2566">**Information Fields**</span></span>

- <span data-ttu-id="26363-2567">情報フィールド 1: HCD 名。</span><span class="sxs-lookup"><span data-stu-id="26363-2567">Info Field 1: Hcd Name.</span></span>
- <span data-ttu-id="26363-2568">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2568">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2569">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2569">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2570">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2570">Info Field 4: Not used.</span></span>

### <a name="host-stack-initialize"></a><span data-ttu-id="26363-2571">ホスト スタック初期化</span><span class="sxs-lookup"><span data-stu-id="26363-2571">Host Stack Initialize</span></span> 

#### <a name="ux_host_stack_initialize"></a><span data-ttu-id="26363-2572">ux_host_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="26363-2572">ux_host_stack_initialize</span></span>

<span data-ttu-id="26363-2573">**アイコン** ![ホスト スタック初期化アイコン](./media/user-guide/usbx-events/image204.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2573">**Icon** ![Host Stack Initialize icon](./media/user-guide/usbx-events/image204.png)</span></span>

<span data-ttu-id="26363-2574">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2574">**Description**</span></span>

<span data-ttu-id="26363-2575">USBX ホスト スタック初期化イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2575">This event represents a USBX Host Stack Initialize Event.</span></span>

<span data-ttu-id="26363-2576">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2576">**Information Fields**</span></span>

- <span data-ttu-id="26363-2577">情報フィールド 1: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2577">Info Field 1: Not used.</span></span>
- <span data-ttu-id="26363-2578">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2578">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2579">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2579">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2580">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2580">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-endpoint-get"></a><span data-ttu-id="26363-2581">ホスト スタック インターフェイス エンドポイント取得</span><span class="sxs-lookup"><span data-stu-id="26363-2581">Host Stack Interface Endpoint Get</span></span> 

#### <a name="interface_-tcp-retry-entry"></a><span data-ttu-id="26363-2582">インターフェイス_ TCP エントリ再試行</span><span class="sxs-lookup"><span data-stu-id="26363-2582">Interface_ TCP retry entry</span></span>

<span data-ttu-id="26363-2583">**アイコン** ![ホスト スタック インターフェイス エンドポイント取得アイコン](./media/user-guide/usbx-events/image205.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2583">**Icon** ![Host Stack Interface Endpoint Get icon](./media/user-guide/usbx-events/image205.png)</span></span>

<span data-ttu-id="26363-2584">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2584">**Description**</span></span>

<span data-ttu-id="26363-2585">NetX の TCP 再試行イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2585">This event represents an internal NetX TCP retry event.</span></span>

<span data-ttu-id="26363-2586">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2586">**Information Fields**</span></span>

- <span data-ttu-id="26363-2587">情報フィールド 1: インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2587">Info Field 1: Interface.</span></span>
- <span data-ttu-id="26363-2588">情報フィールド 2: エンドポイントのインデックス。</span><span class="sxs-lookup"><span data-stu-id="26363-2588">Info Field 2: Endpoint index.</span></span>
- <span data-ttu-id="26363-2589">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2589">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2590">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2590">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-instance-create"></a><span data-ttu-id="26363-2591">ホスト スタック インターフェイス インスタンス作成</span><span class="sxs-lookup"><span data-stu-id="26363-2591">Host Stack Interface Instance Create</span></span> 

#### <a name="ux_host_stack_interface_instance_create"></a><span data-ttu-id="26363-2592">ux_host_stack_interface_instance_create</span><span class="sxs-lookup"><span data-stu-id="26363-2592">ux_host_stack_interface_instance_create</span></span>

<span data-ttu-id="26363-2593">**アイコン** ![ホスト スタック インターフェイス インスタンス作成アイコン](./media/user-guide/usbx-events/image206.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2593">**Icon** ![Host Stack Interface Instance Create icon](./media/user-guide/usbx-events/image206.png)</span></span>

<span data-ttu-id="26363-2594">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2594">**Description**</span></span>

<span data-ttu-id="26363-2595">USBX ホスト スタック インターフェイス インスタンス作成イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2595">This event represents a USBX Host Stack Interface Instance Create Event.</span></span>

<span data-ttu-id="26363-2596">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2596">**Information Fields**</span></span>

- <span data-ttu-id="26363-2597">情報フィールド 1: インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2597">Info Field 1: Interface.</span></span>
- <span data-ttu-id="26363-2598">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2598">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2599">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2599">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2600">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2600">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-instance-delete"></a><span data-ttu-id="26363-2601">ホスト スタック インターフェイス インスタンス削除</span><span class="sxs-lookup"><span data-stu-id="26363-2601">Host Stack Interface Instance Delete</span></span> 

#### <a name="ux_host_stack_interface_instance_delete"></a><span data-ttu-id="26363-2602">ux_host_stack_interface_instance_delete</span><span class="sxs-lookup"><span data-stu-id="26363-2602">ux_host_stack_interface_instance_delete</span></span>

<span data-ttu-id="26363-2603">**アイコン** ![ホスト スタック インターフェイス インスタンス削除アイコン](./media/user-guide/usbx-events/image207.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2603">**Icon** ![Host Stack Interface Instance Delete icon](./media/user-guide/usbx-events/image207.png)</span></span>

<span data-ttu-id="26363-2604">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2604">**Description**</span></span>

<span data-ttu-id="26363-2605">USBX ホスト スタック インターフェイス インスタンス削除イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2605">This event represents a USBX Host Stack Interface Instance Delete Event.</span></span>

<span data-ttu-id="26363-2606">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2606">**Information Fields**</span></span>

- <span data-ttu-id="26363-2607">情報フィールド 1: インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2607">Info Field 1: Interface.</span></span>
- <span data-ttu-id="26363-2608">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2608">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2609">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2609">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2610">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2610">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-set"></a><span data-ttu-id="26363-2611">ホスト スタック インターフェイス設定</span><span class="sxs-lookup"><span data-stu-id="26363-2611">Host Stack Interface Set</span></span> 

#### <a name="ux_host_stack_interface_set"></a><span data-ttu-id="26363-2612">ux_host_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="26363-2612">ux_host_stack_interface_set</span></span>

<span data-ttu-id="26363-2613">**アイコン** ![ホスト スタック インターフェイス設定アイコン](./media/user-guide/usbx-events/image208.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2613">**Icon** ![Host Stack Interface Set icon](./media/user-guide/usbx-events/image208.png)</span></span>

<span data-ttu-id="26363-2614">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2614">**Description**</span></span>

<span data-ttu-id="26363-2615">USBX ホスト スタック インターフェイス設定イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2615">This event represents a USBX Host Stack Interface Set Event.</span></span>

<span data-ttu-id="26363-2616">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2616">**Information Fields**</span></span>

- <span data-ttu-id="26363-2617">情報フィールド 1: インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2617">Info Field 1: Interface.</span></span>
- <span data-ttu-id="26363-2618">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2618">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2619">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2619">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2620">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2620">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-setting-select"></a><span data-ttu-id="26363-2621">ホスト スタック インターフェイス設定選択</span><span class="sxs-lookup"><span data-stu-id="26363-2621">Host Stack Interface Setting Select</span></span> 

#### <a name="ux_host_stack_interface_setting_select"></a><span data-ttu-id="26363-2622">ux_host_stack_interface_setting_select</span><span class="sxs-lookup"><span data-stu-id="26363-2622">ux_host_stack_interface_setting_select</span></span>

<span data-ttu-id="26363-2623">**アイコン** ![ホスト スタック インターフェイス設定選択アイコン](./media/user-guide/usbx-events/image209.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2623">**Icon** ![Host Stack Interface Setting Select icon](./media/user-guide/usbx-events/image209.png)</span></span>

<span data-ttu-id="26363-2624">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2624">**Description**</span></span>

<span data-ttu-id="26363-2625">USBX ホスト スタック インターフェイス設定選択イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2625">This event represents a USBX Host Stack Interface Setting Select Event.</span></span>

<span data-ttu-id="26363-2626">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2626">**Information Fields**</span></span>

- <span data-ttu-id="26363-2627">情報フィールド 1: インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2627">Info Field 1: Interface.</span></span>
- <span data-ttu-id="26363-2628">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2628">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2629">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2629">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2630">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2630">Info Field 4: Not used.</span></span>

### <a name="host-stack-new-configuration-create"></a><span data-ttu-id="26363-2631">ホスト スタック新規構成作成</span><span class="sxs-lookup"><span data-stu-id="26363-2631">Host Stack New Configuration Create</span></span> 

#### <a name="ux_host_stack_new_configuration_create"></a><span data-ttu-id="26363-2632">ux_host_stack_new_configuration_create</span><span class="sxs-lookup"><span data-stu-id="26363-2632">ux_host_stack_new_configuration_create</span></span>

<span data-ttu-id="26363-2633">**アイコン** ![ホスト スタック新規構成作成アイコン](./media/user-guide/usbx-events/image210.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2633">**Icon** ![Host Stack New Configuration Create icon](./media/user-guide/usbx-events/image210.png)</span></span>

<span data-ttu-id="26363-2634">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2634">**Description**</span></span>
 
<span data-ttu-id="26363-2635">USBX ホスト スタック新規構成作成イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2635">This event represents a USBX Host Stack New Configuration Create Event.</span></span>

<span data-ttu-id="26363-2636">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2636">**Information Fields**</span></span>

- <span data-ttu-id="26363-2637">情報フィールド 1: デバイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2637">Info Field 1: Device.</span></span>
- <span data-ttu-id="26363-2638">情報フィールド 2: 構成。</span><span class="sxs-lookup"><span data-stu-id="26363-2638">Info Field 2: Configuration.</span></span>
- <span data-ttu-id="26363-2639">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2639">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2640">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2640">Info Field 4: Not used.</span></span>

### <a name="host-stack-new-device-create"></a><span data-ttu-id="26363-2641">ホスト スタック新規デバイス作成</span><span class="sxs-lookup"><span data-stu-id="26363-2641">Host Stack New Device Create</span></span> 

#### <a name="ux_host_stack_new_device_create"></a><span data-ttu-id="26363-2642">ux_host_stack_new_device_create</span><span class="sxs-lookup"><span data-stu-id="26363-2642">ux_host_stack_new_device_create</span></span>

<span data-ttu-id="26363-2643">**アイコン** ![ホスト スタック新規デバイス作成アイコン](./media/user-guide/usbx-events/image211.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2643">**Icon** ![Host Stack New Device Create icon](./media/user-guide/usbx-events/image211.png)</span></span>

<span data-ttu-id="26363-2644">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2644">**Description**</span></span>
 
 <span data-ttu-id="26363-2645">USBX ホスト スタック新規デバイス作成イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2645">This event represents a USBX Host Stack New Device Create Event.</span></span>

<span data-ttu-id="26363-2646">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2646">**Information Fields**</span></span>

- <span data-ttu-id="26363-2647">情報フィールド 1: HCD。</span><span class="sxs-lookup"><span data-stu-id="26363-2647">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="26363-2648">情報フィールド 2: デバイスの所有者。</span><span class="sxs-lookup"><span data-stu-id="26363-2648">Info Field 2: Device owner.</span></span>
- <span data-ttu-id="26363-2649">情報フィールド 3: ポートのインデックス。</span><span class="sxs-lookup"><span data-stu-id="26363-2649">Info Field 3: Port index.</span></span>
- <span data-ttu-id="26363-2650">情報フィールド 4: デバイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2650">Info Field 4: Device.</span></span>

### <a name="host-stack-new-endpoint-create"></a><span data-ttu-id="26363-2651">ホスト スタック新規エンドポイント作成</span><span class="sxs-lookup"><span data-stu-id="26363-2651">Host Stack New Endpoint Create</span></span> 

#### <a name="ux_host_stack_new_endpoint_create"></a><span data-ttu-id="26363-2652">ux_host_stack_new_endpoint_create</span><span class="sxs-lookup"><span data-stu-id="26363-2652">ux_host_stack_new_endpoint_create</span></span>

<span data-ttu-id="26363-2653">**アイコン** ![ホスト スタック新規エンドポイント作成アイコン](./media/user-guide/usbx-events/image212.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2653">**Icon** ![Host Stack New Endpoint Create icon](./media/user-guide/usbx-events/image212.png)</span></span>

<span data-ttu-id="26363-2654">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2654">**Description**</span></span>
 
<span data-ttu-id="26363-2655">USBX ホスト スタック新規エンドポイント作成イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2655">This event represents a USBX Host Stack New Endpoint Create Event.</span></span>

<span data-ttu-id="26363-2656">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2656">**Information Fields**</span></span>

- <span data-ttu-id="26363-2657">情報フィールド 1: インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2657">Info Field 1: Interface.</span></span>
- <span data-ttu-id="26363-2658">情報フィールド 2: エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="26363-2658">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="26363-2659">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2659">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2660">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2660">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-change-process"></a><span data-ttu-id="26363-2661">ホスト スタック ルート ハブ変更処理</span><span class="sxs-lookup"><span data-stu-id="26363-2661">Host Stack Root Hub Change Process</span></span> 

#### <a name="ux_host_stack_rh_change_process"></a><span data-ttu-id="26363-2662">ux_host_stack_rh_change_process</span><span class="sxs-lookup"><span data-stu-id="26363-2662">ux_host_stack_rh_change_process</span></span>

<span data-ttu-id="26363-2663">**アイコン** ![ホスト スタック ルート ハブ変更処理アイコン](./media/user-guide/usbx-events/image213.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2663">**Icon** ![Host Stack Root Hub Change Process icon](./media/user-guide/usbx-events/image213.png)</span></span>

<span data-ttu-id="26363-2664">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2664">**Description**</span></span>
 
<span data-ttu-id="26363-2665">USBX ホスト スタック ルート ハブ変更処理イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2665">This event represents a USBX Host Stack Root Hub Change Process.</span></span>

<span data-ttu-id="26363-2666">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2666">**Information Fields**</span></span>

- <span data-ttu-id="26363-2667">情報フィールド 1: ポートのインデックス。</span><span class="sxs-lookup"><span data-stu-id="26363-2667">Info Field 1: Port index.</span></span>
- <span data-ttu-id="26363-2668">情報フィールド 2: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2668">Info Field 2: Not used.</span></span>
- <span data-ttu-id="26363-2669">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2669">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2670">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2670">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-device-extraction"></a><span data-ttu-id="26363-2671">ホスト スタック ルート ハブ デバイス抽出</span><span class="sxs-lookup"><span data-stu-id="26363-2671">Host Stack Root Hub Device Extraction</span></span> 

#### <a name="ux_host_stack_rh_device_extraction"></a><span data-ttu-id="26363-2672">ux_host_stack_rh_device_extraction</span><span class="sxs-lookup"><span data-stu-id="26363-2672">ux_host_stack_rh_device_extraction</span></span>

<span data-ttu-id="26363-2673">**アイコン** ![ホスト スタック ルート ハブ デバイス抽出アイコン](./media/user-guide/usbx-events/image214.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2673">**Icon** ![Host Stack Root Hub Device Extraction icon](./media/user-guide/usbx-events/image214.png)</span></span>

<span data-ttu-id="26363-2674">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2674">**Description**</span></span>

<span data-ttu-id="26363-2675">USBX ホスト スタック ルート ハブ デバイス抽出イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2675">This event represents a USBX Host Stack Root Hub Device Extraction Event.</span></span>

<span data-ttu-id="26363-2676">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2676">**Information Fields**</span></span>

- <span data-ttu-id="26363-2677">情報フィールド 1: HCD。</span><span class="sxs-lookup"><span data-stu-id="26363-2677">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="26363-2678">情報フィールド 2: ポートのインデックス。</span><span class="sxs-lookup"><span data-stu-id="26363-2678">Info Field 2: Port index.</span></span>
- <span data-ttu-id="26363-2679">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2679">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2680">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2680">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-device-insertion"></a><span data-ttu-id="26363-2681">ホスト スタック ルート ハブ デバイス挿入</span><span class="sxs-lookup"><span data-stu-id="26363-2681">Host Stack Root Hub Device Insertion</span></span> 

#### <a name="ux_host_stack_rh_device_insertion"></a><span data-ttu-id="26363-2682">ux_host_stack_rh_device_insertion</span><span class="sxs-lookup"><span data-stu-id="26363-2682">ux_host_stack_rh_device_insertion</span></span>

<span data-ttu-id="26363-2683">**アイコン** ![ホスト スタック ルート ハブ デバイス挿入アイコン](./media/user-guide/usbx-events/image215.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2683">**Icon** ![Host Stack Root Hub Device Insertion icon](./media/user-guide/usbx-events/image215.png)</span></span>

<span data-ttu-id="26363-2684">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2684">**Description**</span></span>

<span data-ttu-id="26363-2685">USBX ホスト スタック ルート ハブ デバイス挿入イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2685">This event represents a USBX Host Stack Root Hub Device Insertion.</span></span>

<span data-ttu-id="26363-2686">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2686">**Information Fields**</span></span>

- <span data-ttu-id="26363-2687">情報フィールド 1: HCD。</span><span class="sxs-lookup"><span data-stu-id="26363-2687">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="26363-2688">情報フィールド 2: ポートのインデックス。</span><span class="sxs-lookup"><span data-stu-id="26363-2688">Info Field 2: Port index.</span></span>
- <span data-ttu-id="26363-2689">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2689">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2690">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2690">Info Field 4: Not used.</span></span>

### <a name="host-stack-transfer-request"></a><span data-ttu-id="26363-2691">ホスト スタック転送要求</span><span class="sxs-lookup"><span data-stu-id="26363-2691">Host Stack Transfer Request</span></span> 

#### <a name="ux_host_stack_transfer_request"></a><span data-ttu-id="26363-2692">ux_host_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="26363-2692">ux_host_stack_transfer_request</span></span>

<span data-ttu-id="26363-2693">**アイコン** ![ホスト スタック転送要求アイコン](./media/user-guide/usbx-events/image216.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2693">**Icon** ![Host Stack Transfer Request icon](./media/user-guide/usbx-events/image216.png)</span></span>

<span data-ttu-id="26363-2694">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2694">**Description**</span></span>

<span data-ttu-id="26363-2695">USBX ホスト スタック転送要求イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2695">This event represents a USBX Host Stack Transfer Request.</span></span>

<span data-ttu-id="26363-2696">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2696">**Information Fields**</span></span>

- <span data-ttu-id="26363-2697">情報フィールド 1: デバイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2697">Info Field 1: Device.</span></span>
- <span data-ttu-id="26363-2698">情報フィールド 2: エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="26363-2698">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="26363-2699">情報フィールド 3: 転送要求。</span><span class="sxs-lookup"><span data-stu-id="26363-2699">Info Field 3: Transfer request.</span></span>
- <span data-ttu-id="26363-2700">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2700">Info Field 4: Not used.</span></span>

### <a name="host-stack-transfer-request-abort"></a><span data-ttu-id="26363-2701">ホスト スタック転送要求アボート</span><span class="sxs-lookup"><span data-stu-id="26363-2701">Host Stack Transfer Request Abort</span></span> 

#### <a name="internal-io-driver-get-status"></a><span data-ttu-id="26363-2702">内部 I/O ドライバー状態取得</span><span class="sxs-lookup"><span data-stu-id="26363-2702">Internal I/O driver get status</span></span>

<span data-ttu-id="26363-2703">**アイコン** ![ホスト スタック転送要求アボート アイコン](./media/user-guide/usbx-events/image217.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2703">**Icon** ![Host Stack Transfer Request Abort icon](./media/user-guide/usbx-events/image217.png)</span></span>

<span data-ttu-id="26363-2704">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2704">**Description**</span></span>

<span data-ttu-id="26363-2705">USBX ホスト スタック転送要求アボート イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2705">This event represents a USBX Host Stack Transfer Request Abort.</span></span>

<span data-ttu-id="26363-2706">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2706">**Information Fields**</span></span>

- <span data-ttu-id="26363-2707">情報フィールド 1: デバイス。</span><span class="sxs-lookup"><span data-stu-id="26363-2707">Info Field 1: Device.</span></span>
- <span data-ttu-id="26363-2708">情報フィールド 2: エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="26363-2708">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="26363-2709">情報フィールド 3: 転送要求。</span><span class="sxs-lookup"><span data-stu-id="26363-2709">Info Field 3: Transfer request.</span></span>
- <span data-ttu-id="26363-2710">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2710">Info Field 4: Not used.</span></span>

### <a name="usbx-error"></a><span data-ttu-id="26363-2711">USBX エラー</span><span class="sxs-lookup"><span data-stu-id="26363-2711">USBX Error</span></span> 

#### <a name="ux_error"></a><span data-ttu-id="26363-2712">ux_error</span><span class="sxs-lookup"><span data-stu-id="26363-2712">ux_error</span></span>

<span data-ttu-id="26363-2713">**アイコン** ![USBX エラー アイコン](./media/user-guide/usbx-events/image218.png)</span><span class="sxs-lookup"><span data-stu-id="26363-2713">**Icon** ![U S B X Error icon](./media/user-guide/usbx-events/image218.png)</span></span>

<span data-ttu-id="26363-2714">**説明**</span><span class="sxs-lookup"><span data-stu-id="26363-2714">**Description**</span></span>

<span data-ttu-id="26363-2715">USBX エラー イベントです。</span><span class="sxs-lookup"><span data-stu-id="26363-2715">This event represents a USBX Error Event.</span></span>

<span data-ttu-id="26363-2716">**情報フィールド**</span><span class="sxs-lookup"><span data-stu-id="26363-2716">**Information Fields**</span></span>

- <span data-ttu-id="26363-2717">情報フィールド 1: USBX エラー。</span><span class="sxs-lookup"><span data-stu-id="26363-2717">Info Field 1: USBX error.</span></span>
- <span data-ttu-id="26363-2718">情報フィールド 2: エラー名。</span><span class="sxs-lookup"><span data-stu-id="26363-2718">Info Field 2: Error Name.</span></span>
- <span data-ttu-id="26363-2719">情報フィールド 3: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2719">Info Field 3: Not used.</span></span>
- <span data-ttu-id="26363-2720">情報フィールド 4: 使用されません。</span><span class="sxs-lookup"><span data-stu-id="26363-2720">Info Field 4: Not used.</span></span>