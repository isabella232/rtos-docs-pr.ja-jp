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
# <a name="chapter-9---azure-rtos-usbx-trace-events"></a>チャプター 9 - Azure RTOS USBX トレース イベント

このチャプターでは、TraceX により表示される Azure RTOS USBX イベントについて説明します。 

## <a name="list-of-events-and-icons"></a>イベントとアイコンのリスト

次のリストに、TraceX により表示される USBX イベントを挙げます。

| アイコン                             | 意味                               |
| -------------------------------- | ------------------------------------- |
| ![デバイス クラス CDC アクティブ化アイコン](./media/user-guide/usbx-events/image1.png)    | **デバイス クラス CDC アクティブ化** *(ux_device_class_cdc_activate)* |
| ![デバイス クラス CDC 非アクティブ化アイコン](./media/user-guide/usbx-events/image2.png)    | **デバイス クラス CDC 非アクティブ化** *(ux_device_class_cdc_deactivate)* |
| ![デバイス クラス CDC 読み取りアイコン](./media/user-guide/usbx-events/image3.png)    | **デバイス クラス CDC 読み取り** *(ux_device_class_cdc_read)* |
| ![デバイス クラス CDC 書き込みアイコン](./media/user-guide/usbx-events/image4.png)    | **デバイス クラス CDC 書き込み** *(ux_device_class_cdc_write)* |
| ![デバイス クラス DPUMP アクティブ化アイコン](./media/user-guide/usbx-events/image5.png)    | **デバイス クラス DPUMP アクティブ化** *(ux_device_class_dpump_activate)* |
| ![デバイス クラス DPUMP 非アクティブ化アイコン](./media/user-guide/usbx-events/image6.png)    | **デバイス クラス DPUMP 非アクティブ化** *(ux_device_class_dpump_deactivate)* |
| ![デバイス クラス DPUMP 読み取りアイコン](./media/user-guide/usbx-events/image7.png)    | **デバイス クラス DPUMP 読み取り** *(ux_device_class_dpump_read)* |
| ![デバイス クラス DPUMP 書き込みアイコン](./media/user-guide/usbx-events/image8.png)    | **デバイス クラス DPUMP 書き込み** *(ux_device_class_dpump_write)* |
| ![デバイス クラス HID アクティブ化アイコン](./media/user-guide/usbx-events/image9.png)    | **デバイス クラス HID アクティブ化** *(ux_device_class_hid_activate)* |
| ![デバイス クラス HID 非アクティブ化アイコン](./media/user-guide/usbx-events/image10.png)    | **デバイス クラス HID 非アクティブ化** *(ux_device_class_hid_deactivate)* |
| ![デバイス クラス HID 記述子送信アイコン](./media/user-guide/usbx-events/image11.png)    | **デバイス クラス HID 記述子送信** *(ux_device_class_hid_descriptor_send)* |
| ![デバイス クラス HID イベント取得アイコン](./media/user-guide/usbx-events/image12.png)    | **デバイス クラス HID イベント取得** *(ux_device_class_hid_event_get)* |
| ![デバイス クラス HID イベント設定アイコン](./media/user-guide/usbx-events/image13.png)    | **デバイス クラス HID イベント設定** *(ux_device_class_hid_event_set)* |
| ![デバイス クラス HID レポート取得アイコン](./media/user-guide/usbx-events/image14.png)    | **デバイス クラス HID レポート取得** *(ux_device_class_hid_report_get)* |
| ![デバイス クラス HID レポート設定アイコン](./media/user-guide/usbx-events/image15.png)    | **デバイス クラス HID レポート設定** *(ux_device_class_hid_report_set)* |
| ![デバイス クラス PIMA アクティブ化アイコン](./media/user-guide/usbx-events/image16.png)    | **デバイス クラス PIMA アクティブ化** *(ux_device_class_pima_activate)* |
| ![デバイス クラス PIMA 非アクティブ化アイコン](./media/user-guide/usbx-events/image17.png)    | **デバイス クラス PIMA 非アクティブ化** *(ux_device_class_pima_deactivate)* |
| ![デバイス クラス PIMA デバイス情報送信アイコン](./media/user-guide/usbx-events/image18.png)    | **デバイス クラス PIMA デバイス情報送信** *(ux_device_class_pima_device_info_send)* |
| ![デバイス クラス PIMA イベント取得アイコン](./media/user-guide/usbx-events/image19.png)    | **デバイス クラス PIMA イベント取得** *(ux_device_class_pima_event_get)* |
| ![デバイス クラス PIMA イベント設定アイコン](./media/user-guide/usbx-events/image20.png)    | **デバイス クラス PIMA イベント設定** *(ux_device_class_pima_event_set)* |
| ![デバイス クラス PIMA オブジェクト追加アイコン](./media/user-guide/usbx-events/image21.png)    | **デバイス クラス PIMA オブジェクト追加** *(ux_device_class_pima_object_add)* |
| ![デバイス クラス PIMA オブジェクト データ取得アイコン](./media/user-guide/usbx-events/image22.png)    | **デバイス クラス PIMA オブジェクト データ取得** *(ux_device_class_pima_object_data_get)* |
| ![デバイス クラス PIMA オブジェクト データ送信アイコン](./media/user-guide/usbx-events/image23.png)    | **デバイス クラス PIMA オブジェクト データ送信** *(ux_device_class_pima_object_data_send)* |
| ![デバイス クラス PIMA オブジェクト削除アイコン](./media/user-guide/usbx-events/image24.png)    | **デバイス クラス PIMA オブジェクト削除** *(ux_device_class_pima_object_delete)* |
| ![デバイス クラス PIMA オブジェクト ハンドル送信アイコン](./media/user-guide/usbx-events/image25.png)    | **デバイス クラス PIMA オブジェクト ハンドル送信** *(ux_device_class_pima_object_handles_send)* |
| ![デバイス クラス PIMA オブジェクト情報取得アイコン](./media/user-guide/usbx-events/image26.png)    | **デバイス クラス PIMA オブジェクト情報取得** *(ux_device_class_pima_object_info_get)* |
| ![デバイス クラス PIMA オブジェクト情報送信アイコン](./media/user-guide/usbx-events/image27.png)    | **デバイス クラス PIMA オブジェクト情報送信** *(ux_device_class_pima_object_info_send)* |
| ![デバイス クラス PIMA オブジェクト数送信アイコン](./media/user-guide/usbx-events/image28.png)    | **デバイス クラス PIMA オブジェクト数送信** *(ux_device_class_pima_objects_number_send)* |
| ![デバイス クラス PIMA オブジェクト データ一部取得アイコン](./media/user-guide/usbx-events/image29.png)    | **デバイス クラス PIMA オブジェクトデータ一部取得** *(ux_device_class_pima_partial_object_data_get)* |
| ![デバイス クラス PIMA 応答送信アイコン](./media/user-guide/usbx-events/image30.png)    | **デバイス クラス PIMA 応答送信** *(ux_device_class_pima_response_send)*|
| ![デバイス クラス PIMA ストレージ ID 送信アイコン](./media/user-guide/usbx-events/image31.png)    | **デバイス クラス PIMA ストレージ ID 送信** *(ux_device_class_pima_storage_id_send)* |
| ![デバイス クラス PIMA ストレージ情報送信アイコン](./media/user-guide/usbx-events/image32.png)    | **デバイス クラス PIMA ストレージ情報送信** *(ux_device_class_pima_storage_info_send)* |
| ![デバイス クラス RNDIS アクティブ化アイコン](./media/user-guide/usbx-events/image33.png)    | **デバイス クラス RNDIS アクティブ化** *(ux_device_class_rndis_activate)* |
| ![デバイス クラス RNDIS 非アクティブ化アイコン](./media/user-guide/usbx-events/image34.png)    | **デバイス クラス RNDIS 非アクティブ化** *(ux_device_class_rndis_deactivate)* |
| ![デバイス クラス RNDIS キープ アライブ メッセージ送信アイコン](./media/user-guide/usbx-events/image35.png)    | **デバイス クラス RNDIS キープ アライブ メッセージ送信** *(ux_device_class_rndis_msg_keep_alive)* |
| ![デバイス クラス RNDIS クエリ メッセージ送信アイコン](./media/user-guide/usbx-events/image36.png)    | **デバイス クラス RNDIS クエリ メッセージ送信** *(ux_device_class_rndis_msg_query)* |
| ![デバイス クラス RNDIS リセット メッセージ送信アイコン](./media/user-guide/usbx-events/image37.png)    | **デバイス クラス RNDIS リセット メッセージ送信** *(ux_device_class_rndis_msg_reset)* |
| ![デバイス クラス RNDIS 設定メッセージ送信アイコン](./media/user-guide/usbx-events/image38.png)    | **デバイス クラス RNDIS 設定メッセージ送信** *(ux_device_class_rndis_msg_set)* |
| ![デバイス クラス RNDIS パケット受信アイコン](./media/user-guide/usbx-events/image39.png)    | **デバイス クラス RNDIS パケット受信** *(ux_device_class_rndis_packet_receive)* |
| ![デバイス クラス RNDIS パケット送信アイコン](./media/user-guide/usbx-events/image40.png)    | **デバイス クラス RNDIS パケット送信** *(ux_device_class_rndis_packet_transmit)* |
| ![デバイス クラス Storage アクティブ化アイコン](./media/user-guide/usbx-events/image41.png)    | **デバイス クラス Storage アクティブ化** *(ux_device_class_storage_activate)* |
| ![デバイス クラス Storage 非アクティブ化アイコン](./media/user-guide/usbx-events/image42.png)    | **デバイス クラス Storage 非アクティブ化** *(ux_device_class_storage_deactivate)* |
| ![デバイス クラス Storage フォーマット アイコン](./media/user-guide/usbx-events/image43.png)    | **デバイス クラス Storage フォーマット** *(ux_device_class_storage_format)* |
| ![デバイス クラス Storage 照会アイコン](./media/user-guide/usbx-events/image44.png)    | **デバイス クラス Storage 照会** *(ux_device_class_storage_inquiry)* |
| ![デバイス クラス Storage モード選択アイコン](./media/user-guide/usbx-events/image45.png)    | **デバイス クラス Storage モード選択** *(ux_device_class_storage_mode_select)* |
| ![デバイス クラス Storage モード センス アイコン](./media/user-guide/usbx-events/image46.png)    | **デバイス クラス Storage モード センス** *(ux_device_class_storage_mode_sense)* |
| ![デバイス クラス Storage メディア取り外し禁止/許可アイコン](./media/user-guide/usbx-events/image47.png)    | **デバイス クラス Storage メディア取り外し禁止/許可** *(ux_device_class_storage_prevent_allow_media_removal)* |
| ![デバイス クラス Storage 読み取りアイコン](./media/user-guide/usbx-events/image48.png)    | **デバイス クラス Storage 読み取り** *(ux_device_class_storage_read)* |
| ![デバイス クラス Storage 容量読み取りアイコン](./media/user-guide/usbx-events/image49.png)    | **デバイス クラス Storage 容量読み取り** *(ux_device_class_storage_read_capacity)* |
| ![デバイス クラス Storage フォーマット容量読み取りアイコン](./media/user-guide/usbx-events/image50.png)    | **デバイス クラス Storage フォーマット容量読み取り** *(ux_device_class_storage_read_format_capacity)* |
| ![デバイス クラス Storage TOC 読み取りアイコン](./media/user-guide/usbx-events/image51.png)    | **デバイス クラス Storage TOC 読み取り** *(ux_device_class_storage_read_toc)* |
| ![デバイス クラス Storage センス データ要求アイコン](./media/user-guide/usbx-events/image52.png)    | **デバイス クラス Storage センス データ要求** *(ux_device_class_storage_request_sense)* |
| ![デバイス クラス Storage 開始/停止アイコン](./media/user-guide/usbx-events/image53.png)    | **デバイス クラス Storage 開始/停止** *(ux_device_class_storage_start_stop)* |
| ![デバイス クラス Storage 準備状態テスト アイコン](./media/user-guide/usbx-events/image54.png)    | **デバイス クラス Storage 準備状態テスト** *(ux_device_class_storage_test_ready)* |
| ![デバイス クラス Storage 検証アイコン](./media/user-guide/usbx-events/image55.png)    | **デバイス クラス Storage 検証** *(ux_device_class_storage_verify)* |
| ![デバイス クラス Storage 書き込みアイコン](./media/user-guide/usbx-events/image56.png)    | **デバイス クラス Storage 書き込み** *(ux_device_class_storage_write)* |
| ![デバイス スタック設定選択肢取得アイコン](./media/user-guide/usbx-events/image57.png)    | **デバイス スタック設定選択肢取得** *(ux_device_stack_alternate_setting_get)* |
| ![デバイス スタック設定選択肢設定アイコン](./media/user-guide/usbx-events/image58.png)    | **デバイス スタック設定選択肢設定** *(ux_device_stack_alternate_setting_set)* |
| ![デバイス スタック クラス登録アイコン](./media/user-guide/usbx-events/image59.png)    | **デバイス スタック クラス登録** *(ux_device_stack_class_register)* |
| ![デバイス スタック機能消去アイコン](./media/user-guide/usbx-events/image60.png)    | **デバイス スタック機能消去** *(ux_device_stack_clear_feature)* |
| ![デバイス スタック構成取得アイコン](./media/user-guide/usbx-events/image61.png)    | **デバイス スタック構成取得** *(ux_device_stack_configuration_get)* |
| ![デバイス スタック構成設定アイコン](./media/user-guide/usbx-events/image62.png)    | **デバイス スタック構成設定** *(ux_device_stack_configuration_set)* |
| ![デバイス スタック接続アイコン](./media/user-guide/usbx-events/image63.png)    | **デバイス スタック接続** *(ux_device_stack_connect)* |
| ![デバイス スタック記述子送信アイコン](./media/user-guide/usbx-events/image64.png)    | **デバイス スタック記述子送信** *(ux_device_stack_descriptor_send)* |
| ![デバイス スタック切断アイコン](./media/user-guide/usbx-events/image65.png)    | **デバイス スタック切断** *(ux_device_stack_disconnect)* |
| ![デバイス スタック エンドポイント停止アイコン](./media/user-guide/usbx-events/image66.png)    | **デバイス スタック エンドポイント停止** *(ux_device_stack_endpoint_stall)* |
| ![デバイス スタック状態取得アイコン](./media/user-guide/usbx-events/image67.png)    | **デバイス スタック状態取得** *(ux_device_stack_get_status)* |
| ![デバイス スタック ホスト スリープ解除アイコン](./media/user-guide/usbx-events/image68.png)    | **デバイス スタック ホスト スリープ解除** *(ux_device_stack_host_wakeup)* |
| ![デバイス スタック初期化アイコン](./media/user-guide/usbx-events/image69.png)    | **デバイス スタック初期化** *(ux_device_stack_initialize)* |
| ![デバイス スタック インターフェイス削除アイコン](./media/user-guide/usbx-events/image70.png)    | **デバイス スタック インターフェイス削除** *(ux_device_stack_interface_delete)* |
| ![デバイス スタック インターフェイス取得アイコン](./media/user-guide/usbx-events/image71.png)    | **デバイス スタック インターフェイス取得** *(ux_device_stack_interface_get)* |
| ![デバイス スタック インターフェイス設定アイコン](./media/user-guide/usbx-events/image72.png)    | **デバイス スタック インターフェイス設定** *(ux_device_stack_interface_set)* |
| ![デバイス スタック機能設定アイコン](./media/user-guide/usbx-events/image73.png)    | **デバイス スタック機能設定** *(ux_device_stack_set_feature)* |
| ![デバイス スタック転送アボート アイコン](./media/user-guide/usbx-events/image74.png)    | **デバイス スタック転送アボート** *(ux_device_stack_transfer_abort)* |
| ![\* デバイス スタック全転送要求アボート アイコン](./media/user-guide/usbx-events/image75.png)    | **デバイス スタック全転送要求アボート** *(ux_device_stack_transfer_all_request_abort)* |
| ![デバイス スタック転送要求アイコン](./media/user-guide/usbx-events/image76.png)    | **デバイス スタック転送要求** *(ux_device_stack_transfer_request)* |
| ![ホスト クラス ASIX アクティブ化アイコン](./media/user-guide/usbx-events/image77.png)    | **ホスト クラス ASIX アクティブ化** *(ux_host_class_asix_activate)* |
| ![ホスト クラス ASIX 非アクティブ化アイコン](./media/user-guide/usbx-events/image78.png)    | **ホスト クラス ASIX 非アクティブ化** *(ux_host_class_asix_deactivate)* |
| ![ホスト クラス ASIX 割り込み通知アイコン](./media/user-guide/usbx-events/image79.png)    | **ホスト クラス ASIX 割り込み通知** *(ux_host_class_asix_interrupt_notification)* |
| ![ホスト クラス ASIX 読み取りアイコン](./media/user-guide/usbx-events/image80.png)    | **ホスト クラス ASIX 読み取り** *(ux_host_class_asix_read)* |
| ![ホスト クラス ASIX 書き込みアイコン](./media/user-guide/usbx-events/image81.png)    | **ホスト クラス ASIX 書き込み** *(ux_host_class_asix_write)* |
| ![ホスト クラス Audio アクティブ化アイコン](./media/user-guide/usbx-events/image82.png)    | **ホスト クラス Audio アクティブ化** *(ux_host_class_audio_activate)* |
| ![ホスト クラス Audio コントロール値取得アイコン](./media/user-guide/usbx-events/image83.png)    | **ホスト クラス Audio コントロール値取得** *(ux_host_class_audio_control_value_get)* |
| ![ホスト クラス Audio コントロール値設定アイコン](./media/user-guide/usbx-events/image84.png)    | **ホスト クラス Audio コントロール値設定** *(ux_host_class_audio_control_value_set)* |
| ![ホスト クラス Audio 非アクティブ化アイコン](./media/user-guide/usbx-events/image85.png)    | **ホスト クラス Audio 非アクティブ化** *(ux_host_class_audio_deactivate)* |
| ![ホスト クラス Audio 読み取りアイコン](./media/user-guide/usbx-events/image86.png)    | **ホスト クラス Audio 読み取り** *(ux_host_class_audio_read)* |
| ![ホスト クラス Audio ストリーミング サンプリング取得アイコン](./media/user-guide/usbx-events/image87.png)    | **ホスト クラス Audio ストリーミング サンプリング取得** *(ux_host_class_audio_streaming_sampling_get)* |
| ![ホスト クラス Audio ストリーミング サンプリング設定アイコン](./media/user-guide/usbx-events/image88.png)    | **ホスト クラス Audio ストリーミング サンプリング設定** *(ux_host_class_audio_streaming_sampling_set)* |
| ![ホスト クラス Audio 書き込みアイコン](./media/user-guide/usbx-events/image89.png)    | **ホスト クラス Audio 書き込み** *(ux_host_class_audio_write)* |
| ![ホスト クラス CDC ACM アクティブ化アイコン](./media/user-guide/usbx-events/image90.png)    | **ホスト クラス CDC ACM アクティブ化** *(ux_host_class_cdc_acm_activate)* |
| ![ホスト クラス CDC ACM 非アクティブ化アイコン](./media/user-guide/usbx-events/image91.png)    | **ホスト クラス CDC ACM 非アクティブ化** *(ux_host_class_cdc_acm_deactivate)* |
| ![ホスト クラス CDC ACM IOCTL 入力パイプ アイコン](./media/user-guide/usbx-events/image92.png)    | **ホスト クラス CDC ACM IOCTL 入力パイプ アボート** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)* |
| ![ホスト クラス CDC ACM IOCTL 出力パイプ アボート アイコン](./media/user-guide/usbx-events/image93.png)    | **ホスト クラス CDC ACM IOCTL 出力パイプ アボート** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)* |
| ![ホスト クラス CDC ACM IOCTL デバイス状態取得アイコン](./media/user-guide/usbx-events/image94.png)    | **ホスト クラス CDC ACM IOCTL デバイス状態取得** *(ux_host_class_cdc_acm_ioctl_get_device_status)* |
| ![ホスト クラス CDC ACM IOCTL 伝送路符号化取得アイコン](./media/user-guide/usbx-events/image95.png)    | **ホスト クラス CDC ACM IOCTL 伝送路符号化取得** *(ux_host_class_cdc_acm_ioctl_get_line_coding)* |
| ![ホスト クラス CDC ACM IOCTL 通知コールバック アイコン](./media/user-guide/usbx-events/image96.png)    | **ホスト クラス CDC ACM IOCTL 通知コールバック** *(ux_host_class_cdc_acm_ioctl_notification_callback)* |
| ![ホスト クラス CDC ACM IOCTL ブレーク送信アイコン](./media/user-guide/usbx-events/image97.png)    | **ホスト クラス CDC ACM IOCTL ブレーク送信** *(ux_host_class_cdc_acm_ioctl_send_break)* |
| ![ホスト クラス CDC ACM IOCTL 伝送路符号化設定アイコン](./media/user-guide/usbx-events/image98.png)    | **ホスト クラス CDC ACM IOCTL 伝送路符号化設定** *(ux_host_class_cdc_acm_ioctl_set_line_coding)* |
| ![ホスト クラス CDC ACM IOCTL 伝送路状態設定アイコン](./media/user-guide/usbx-events/image99.png)    | **ホスト クラス CDC ACM IOCTL 伝送路状態設定** *(ux_host_class_cdc_acm_ioctl_set_line_state)* |
| ![ホスト クラス CDC ACM 読み取りアイコン](./media/user-guide/usbx-events/image100.png)    | **ホスト クラス CDC ACM 読み取り** *(ux_host_class_cdc_acm_read)* |
| ![ホスト クラス CDC ACM 受信開始アイコン](./media/user-guide/usbx-events/image101.png)    | **ホスト クラス CDC ACM 受信開始** *(ux_host_class_cdc_acm_reception_start)* |
| ![ホスト クラス CDC ACM 受信停止アイコン](./media/user-guide/usbx-events/image102.png)    | **ホスト クラス CDC ACM 受信停止** *(ux_host_class_cdc_acm_reception_stop)* |
| ![ホスト クラス CDC ACM 書き込みアイコン](./media/user-guide/usbx-events/image103.png)    | **ホスト クラス CDC ACM 書き込み** *(ux_host_class_cdc_acm_write)* |
| ![ホスト クラス DPUMP アクティブ化アイコン](./media/user-guide/usbx-events/image104.png)    | **ホスト クラス DPUMP アクティブ化** *(ux_host_class_dpump_activate)* |
| ![ホスト クラス DPUMP 非アクティブ化アイコン](./media/user-guide/usbx-events/image105.png)    | **ホスト クラス DPUMP 非アクティブ化** *(ux_host_class_dpump_deactivate)* |
| ![ホスト クラス DPUMP 読み取りアイコン](./media/user-guide/usbx-events/image106.png)    | **ホスト クラス DPUMP 読み取り** *(ux_host_class_dpump_read)* |
| ![ホスト クラス DPUMP 書き込みアイコン](./media/user-guide/usbx-events/image107.png)    | **ホスト クラス DPUMP 書き込み** *(ux_host_class_dpump_write)* |
| ![ホスト クラス HID アクティブ化アイコン](./media/user-guide/usbx-events/image108.png)    | **ホスト クラス HID アクティブ化** *(ux_host_class_hid_activate)* |
| ![ホスト クラス HID クライアント登録アイコン](./media/user-guide/usbx-events/image109.png)    | **ホスト クラス HID クライアント登録** *(ux_host_class_hid_client_register)* |
| ![ホスト クラス HID 非アクティブ化アイコン](./media/user-guide/usbx-events/image110.png)    | **ホスト クラス HID 非アクティブ化** *(ux_host_class_hid_deactivate)* |
| ![ホスト クラス HID アイドル取得アイコン](./media/user-guide/usbx-events/image111.png)    | **ホスト クラス HID アイドル取得** *(ux_host_class_hid_idle_get)* |
| ![ホスト クラス HID アイドル設定アイコン](./media/user-guide/usbx-events/image112.png)    | **ホスト クラス HID アイドル設定** *(ux_host_class_hid_idle_set)* |
| ![ホスト クラス HID キーボード アクティブ化アイコン](./media/user-guide/usbx-events/image113.png)    | **ホスト クラス HID キーボード アクティブ化** *(ux_host_class_hid_keyboard_activate)* |
| ![ホスト クラス HID キーボード非アクティブ化アイコン](./media/user-guide/usbx-events/image114.png)    | **ホスト クラス HID キーボード非アクティブ化** *(ux_host_class_hid_keyboard_deactivate)* |
| ![ホスト クラス HID マウス アクティブ化アイコン](./media/user-guide/usbx-events/image115.png)    | **ホスト クラス HID マウス アクティブ化** *(ux_host_class_hid_mouse_activate)* |
| ![ホスト クラス HID マウス非アクティブ化アイコン](./media/user-guide/usbx-events/image116.png)    | **ホスト クラス HID マウス非アクティブ化** *(ux_host_class_hid_mouse_deactivate)* |
| ![ホスト クラス HID リモート制御アクティブ化アイコン](./media/user-guide/usbx-events/image117.png)    | **ホスト クラス HID リモート制御アクティブ化** *(ux_host_class_hid_remote_control_activate)* |
| ![ホスト クラス HID リモート制御非アクティブ化アイコン](./media/user-guide/usbx-events/image118.png)    | **ホスト クラス HID リモート制御非アクティブ化** *(ux_host_class_hid_remote_control_deactivate)* |
| ![ホスト クラス HID レポート取得アイコン](./media/user-guide/usbx-events/image119.png)    | **ホスト クラス HID レポート取得** *(ux_host_class_hid_report_get)* |
| ![ホスト クラス HID レポート設定アイコン](./media/user-guide/usbx-events/image120.png)    | **ホスト クラス HID レポート設定** *(ux_host_class_hid_report_set)* |
| ![ホスト クラス Hub アクティブ化アイコン](./media/user-guide/usbx-events/image121.png)    | **ホスト クラス Hub アクティブ化** *(ux_host_class_hub_activate)* |
| ![ホスト クラス Hub 変更検出アイコン](./media/user-guide/usbx-events/image122.png)    | **ホスト クラス Hub 変更検出** *(ux_host_class_hub_change_detect)* |
| ![\* ホストクラス Hub 非アクティブ化アイコン](./media/user-guide/usbx-events/image123.png)    | **ホスト クラス Hub 非アクティブ化** *(ux_host_class_hub_deactivate)* |
| ![ホスト クラス Hub ポート変更接続処理アイコン](./media/user-guide/usbx-events/image124.png)    | **ホスト クラス Hub ポート変更接続処理** *(ux_host_class_hub_port_change_connection_process)* |
| ![ホスト クラス Hub ポート変更有効化処理アイコン](./media/user-guide/usbx-events/image125.png)    | **ホスト クラス Hub ポート変更有効化処理** *(ux_host_class_hub_port_change_enable_process)* |
| ![ホスト クラス Hub ポート変更過電流処理アイコン](./media/user-guide/usbx-events/image126.png)    | **ホスト クラス Hub ポート変更過電流処理** *(ux_host_class_hub_port_change_over_current_process)* |
| ![ホスト クラス Hub ポート変更リセット処理アイコン](./media/user-guide/usbx-events/image127.png)    | **ホスト クラス Hub ポート変更リセット処理** *(ux_host_class_hub_port_change_reset_process)* |
| ![ホスト クラス Hub ポート変更中断処理アイコン](./media/user-guide/usbx-events/image128.png)    | **ホスト クラス Hub ポート変更中断処理** *(ux_host_class_hub_port_change_suspend_process)* |
| ![ホスト クラス PIMA アクティブ化アイコン](./media/user-guide/usbx-events/image129.png)    | **ホスト クラス PIMA アクティブ化** *(ux_host_class_prima_activate)* |
| ![ホスト クラス PIMA 非アクティブ化アイコン](./media/user-guide/usbx-events/image130.png)    | **ホスト クラス PIMA 非アクティブ化** *(ux_host_class_pima_deactivate)* |
| ![ホスト クラス PIMA デバイス情報取得アイコン](./media/user-guide/usbx-events/image131.png)    | **ホスト クラス PIMA デバイス情報取得** *(ux_host_class_pima_device_info_get)* |
| ![ホスト クラス PIMA デバイス リセット アイコン](./media/user-guide/usbx-events/image132.png)    | **ホスト クラス PIMA デバイス リセット** *(ux_host_class_pima_device_reset)* |
| ![ホスト クラス PIMA 通知アイコン](./media/user-guide/usbx-events/image133.png)    | **ホスト クラス PIMA 通知** *(ux_host_class_pima_notification)* |
| ![ホスト クラス PIMA オブジェクト数取得アイコン](./media/user-guide/usbx-events/image134.png)    | **ホスト クラス PIMA オブジェクト数取得** *(ux_host_class_pima_num_objects_get)* |
| ![ホスト クラス PIMA オブジェクト クローズ アイコン](./media/user-guide/usbx-events/image135.png)    | **ホスト クラス PIMA オブジェクト クローズ** *(ux_host_class_pima_object_close)* |
| ![ホスト クラス PIMA オブジェクト コピー アイコン](./media/user-guide/usbx-events/image136.png)    | **ホスト クラス PIMA オブジェクト コピー** *(ux_host_class_pima_object_copy)* |
| ![ホスト クラス PIMA オブジェクト削除アイコン](./media/user-guide/usbx-events/image137.png)    | **ホスト クラス PIMA オブジェクト削除** *(ux_host_class_pima_object_delete)* |
| ![ホスト クラス PIMA オブジェクト取得アイコン](./media/user-guide/usbx-events/image138.png)    | **ホスト クラス PIMA オブジェクト取得** *(ux_host_class_pima_object_get)* |
| ![ホスト クラス PIMA オブジェクト情報取得アイコン](./media/user-guide/usbx-events/image139.png)    | **ホスト クラス PIMA オブジェクト情報取得** *(ux_host_class_pima_object_info_get)* |
| ![ホスト クラス PIMA オブジェクト情報送信アイコン](./media/user-guide/usbx-events/image140.png)    | **ホスト クラス PIMA オブジェクト情報送信** *(ux_host_class_pima_object_info_send)* |
| ![ホスト クラス PIMA オブジェクト移動アイコン](./media/user-guide/usbx-events/image141.png)    | **ホスト クラス PIMA オブジェクト移動** *(ux_host_class_pima_object_move)* |
| ![ホスト クラス PIMA オブジェクト送信アイコン](./media/user-guide/usbx-events/image142.png)    | **ホスト クラス PIMA オブジェクト送信** *(ux_host_class_pima_object_send)* |
| ![ホスト クラス PIMA オブジェクト転送アボート アイコン](./media/user-guide/usbx-events/image143.png)    | **ホスト クラス PIMA オブジェクト転送アボード** *(ux_host_class_object_transfer_abort)* |
| ![ホスト クラス PIMA 読み取りアイコン](./media/user-guide/usbx-events/image144.png)    | **ホスト クラス PIMA 読み取り** *(ux_host_class_pima_read)* |
| ![ホスト クラス PIMA 要求取り消しアイコン](./media/user-guide/usbx-events/image145.png)    | **ホスト クラス PIMA 要求取り消し** *(ux_host_class_pima_request_cancel)* |
| ![ホスト クラス PIMA セッション終了アイコン](./media/user-guide/usbx-events/image146.png)    | **ホスト クラス PIMA セッション終了** *(ux_host_class_pima_session_close)* |
| ![ホスト クラス PIMA セッション開始アイコン](./media/user-guide/usbx-events/image147.png)    | **ホスト クラス PIMA セッション開始** *(ux_host_class_pima_session_open)* |
| ![ホスト クラス PIMA ストレージ ID 取得アイコン](./media/user-guide/usbx-events/image148.png)    | **ホスト クラス PIMA ストレージ ID 取得** *(ux_host_class_pima_storage_ids_get)* |
| ![ホスト クラス PIMA ストレージ情報取得アイコン](./media/user-guide/usbx-events/image149.png)    | **ホスト クラス PIMA ストレージ情報取得** *(ux_host_class_pima_storage_info_get)* |
| ![ホスト クラス PIMA Thumb 取得アイコン](./media/user-guide/usbx-events/image150.png)    | **ホスト クラス PIMA Thumb 取得** *(ux_host_class_pima_thumb_get)* |
| ![ホスト クラス PIMA 書き込みアイコン](./media/user-guide/usbx-events/image151.png)    | **ホスト クラス PIMA 書き込み** *(ux_host_class_pima_write)* |
| ![ホスト クラス Printer アクティブ化アイコン](./media/user-guide/usbx-events/image152.png)    | **ホスト クラス Printer アクティブ化** *(ux_host_class_printer_activate)* |
| ![ホスト クラス Printer 非アクティブ化アイコン](./media/user-guide/usbx-events/image153.png)    | **ホスト クラス Printer 非アクティブ化** *(ux_host_class_printer_deactivate)* |
| ![ホスト クラス Printer 名前取得アイコン](./media/user-guide/usbx-events/image154.png)    | **ホスト クラス Printer 名前取得** *(ux_host_class_printer_name_get)* |
| ![ホスト クラス Printer 読み取りアイコン](./media/user-guide/usbx-events/image155.png)    |  **ホスト クラス Printer 読み取り** *(ux_host_class_printer_read)* |
| ![ホスト クラス Printer ソフト リセット アイコン](./media/user-guide/usbx-events/image156.png)    | **ホスト クラス Printer ソフト リセット** *(ux_host_class_printer_soft_reset)* |
| ![ホスト クラス Printer 状態取得アイコン](./media/user-guide/usbx-events/image157.png)    | **ホスト クラス Printer 状態取得** *(ux_host_class_printer_status_get)* |
| ![ホスト クラス Printer 書き込みアイコン](./media/user-guide/usbx-events/image158.png)    | **ホスト クラス Printer 書き込み** *(ux_host_class_printer_write)* |
| ![ホスト クラス Prolific アクティブ化アイコン](./media/user-guide/usbx-events/image159.png)    | **ホスト クラス Prolific アクティブ化** *(ux_host_class_prolific_activate)* |
| ![ホスト クラス Prolific 非アクティブ化アイコン](./media/user-guide/usbx-events/image160.png)    | **ホスト クラス Prolific 非アクティブ化** *(ux_host_class_prolific_deactivate)* |
| ![ホスト クラス Prolific IOCTL 入力パイプ アボート アイコン](./media/user-guide/usbx-events/image161.png)    | **ホスト クラス Prolific IOCTL 入力パイプ アボート** *(ux_host_class_prolific_ioctl_abort_in_pipe)* |
| ![ホスト クラス Prolific IOCTL 出力パイプ アボート アイコン](./media/user-guide/usbx-events/image162.png)    | **ホスト クラス Prolific IOCTL 出力パイプ アボート** *(ux_host_class_prolific_ioctl_abort_out_pipe)* |
| ![ホスト クラス Prolific IOCTL デバイス情報取得アイコン](./media/user-guide/usbx-events/image163.png)    | **ホスト クラス Prolific IOCTL デバイス情報取得** *(ux_host_class_prolific_ioctl_get_device_status)* |
| ![ホスト クラス Prolific IOCTL 伝送路符号化取得アイコン](./media/user-guide/usbx-events/image164.png)    | **ホスト クラス Prolific IOCTL 伝送路符号化取得** *(ux_host_class_prolific_ioctl_get_line_coding)* |
| ![ホスト クラス Prolific IOCTL パージ アイコン](./media/user-guide/usbx-events/image165.png)    | **ホスト クラス Prolific IOCTL パージ** *(ux_host_class_prolific_ioctl_purge)* |
| ![ホスト クラス Prolific IOCTL デバイス状態変更報告アイコン](./media/user-guide/usbx-events/image166.png)    | **ホスト クラス Prolific IOCTL デバイス状態変更報告** *(ux_host_class_prolific_ioctl_report_device_status_change)* |
| ![ホスト クラス Prolific IOCTL ブレーク送信アイコン](./media/user-guide/usbx-events/image167.png)    | **ホスト クラス Prolific IOCTL ブレーク送信** *(ux_host_class_prolific_ioctl_send_break)* |
| ![ホスト クラス Prolific IOCTL 伝送路符号化設定アイコン](./media/user-guide/usbx-events/image168.png)    | **ホスト クラス Prolific IOCTL 伝送路符号化設定** *(ux_host_class_prolific_ioctl_set_line_coding)* |
| ![ホスト クラス Prolific IOCTL 伝送路状態設定アイコン](./media/user-guide/usbx-events/image169.png)    | **ホスト クラス Prolific IOCTL 伝送路状態設定** *(ux_host_class_prolific_ioctl_set_line_state)* |
| ![ホスト クラス Prolific 読み取りアイコン](./media/user-guide/usbx-events/image170.png)    | **ホスト クラス Prolific 読み取り** *(ux_host_class_prolific_read)* |
| ![ホスト クラス Prolific 受信開始アイコン](./media/user-guide/usbx-events/image171.png)    | **ホスト クラス Prolific 受信開始** *(ux_host_class_prolific_reception_start)* |
| ![ホスト クラス Prolific 受信停止アイコン](./media/user-guide/usbx-events/image172.png)    | **ホスト クラス Prolific 受信停止** *(ux_host_class_prolific_reception_stop)* |
| ![ホスト クラス Prolific 書き込みアイコン](./media/user-guide/usbx-events/image173.png)    | **ホスト クラス Prolific 書き込み** *(ux_host_class_prolific_write)* |
| ![ホスト クラス Storage アクティブ化アイコン](./media/user-guide/usbx-events/image174.png)    | **ホスト クラス Storage アクティブ化** *(ux_host_class_storage_activate)* |
| ![ホスト クラス Storage 非アクティブ化アイコン](./media/user-guide/usbx-events/image175.png)    | **ホスト クラス Storage 非アクティブ化** (*ux_host_class_storage_deactivate)* |
| ![ホスト クラス Storage メディア容量取得アイコン](./media/user-guide/usbx-events/image176.png)    | **ホスト クラス Storage メディア容量取得** *(ux_host_class_storage_media_capacity_get)* |
| ![ホスト クラス Storage メディア フォーマット容量取得アイコン](./media/user-guide/usbx-events/image177.png)    | **ホスト クラス Storage メディア フォーマット容量取得** *(ux_host_class_storage_media_format_capacity_get)* |
| ![ホスト クラス Storage メディア マウント アイコン](./media/user-guide/usbx-events/image178.png)    | **ホスト クラス Storage メディア マウント** (ux_host_class_storage_media_mount)* |
| ![ホスト クラス Storage メディア オープン アイコン](./media/user-guide/usbx-events/image179.png)    | **ホスト クラス Storage メディア オープン** *(ux_host_class_storage_media_open)* |
| ![ホスト クラス Storage メディア読み取りアイコン](./media/user-guide/usbx-events/image180.png)    | **ホスト クラス Storage メディア読み取り** *(ux_host_class_storage_media_read)* |
| ![ホスト クラス Storage メディア書き込みアイコン](./media/user-guide/usbx-events/image181.png)    | **ホスト クラス Storage メディア書き込み** *(ux_host_class_storage_media_write)* |
| ![ホスト クラス Storage センス データ要求アイコン](./media/user-guide/usbx-events/image182.png)    | **ホスト クラス Storage センス データ要求** *(ux_host_class_storage_request_sense)* |
| ![ホスト クラス Storage 開始/停止アイコン](./media/user-guide/usbx-events/image183.png)    | **ホスト クラス Storage 開始/停止** *(ux_host_class_storage_start_stop)* |
| ![ホスト クラス Storage ユニット準備状態テスト アイコン](./media/user-guide/usbx-events/image184.png)    | **ホスト クラス Storage ユニット準備状態テスト** *(ux_host_class_storage_activate)* |
| ![ホスト スタック クラス インスタンス作成アイコン](./media/user-guide/usbx-events/image185.png)    | **ホスト スタック クラス インスタンス作成** *(ux_host_stack_class_instance_create)* |
| ![ホスト スタック クラス インスタンス破棄アイコン](./media/user-guide/usbx-events/image186.png)    | **ホスト スタック クラス インスタンス破棄** *(ux_host_stack_class_instance_destroy)* |
| ![ホスト スタック構成削除アイコン](./media/user-guide/usbx-events/image187.png)    | **ホスト スタック構成削除** *(ux_host_stack_configuration_delete)* |
| ![ホスト スタック構成エニュメレーション アイコン](./media/user-guide/usbx-events/image188.png)    | **ホスト スタック構成エニュメレーション** *(ux_host_stack_configuration_enumerate)* |
| ![ホスト スタック構成インスタンス作成アイコン](./media/user-guide/usbx-events/image189.png)    | **ホスト スタック構成インスタンス作成** *(ux_host_stack_configuration_instance_create)* |
| ![ホスト スタック構成インスタンス削除アイコン](./media/user-guide/usbx-events/image190.png)    | **ホスト スタック構成インスタンス削除** *(ux_host_stack_configuration_instance_delete)* |
| ![ホスト スタック構成設定アイコン](./media/user-guide/usbx-events/image191.png)    | **ホスト スタック構成設定** *(ux_host_stack_configuration_set)* |
| ![ホスト スタック デバイス アドレス設定アイコン](./media/user-guide/usbx-events/image192.png)    | **ホスト スタック デバイス アドレス設定** *(ux_host_stack_device_set)* |
| ![ホスト スタック デバイス構成取得アイコン](./media/user-guide/usbx-events/image193.png)    | **ホスト スタック デバイス構成取得** *(ux_host_stack_device_configuration_get)* |
| ![ホスト スタック デバイス構成選択アイコン](./media/user-guide/usbx-events/image194.png)    | **ホスト スタック デバイス構成選択** *(ux_host_stack_device_configuration_select)* |
| ![ホスト スタック デバイス記述子読み取りアイコン](./media/user-guide/usbx-events/image195.png)    | **ホスト スタック デバイス記述子読み取り** *(ux_host_stack_device_descriptor_read)* |
| ![ホスト スタック デバイス取得アイコン](./media/user-guide/usbx-events/image196.png)    | **ホスト スタック デバイス取得** (ux_host_stack_device_get) |
| ![ホスト スタック デバイス取り外しアイコン](./media/user-guide/usbx-events/image197.png)    | **ホスト スタック デバイス取り外し** (ux_host_stack_device_get) |
| ![ホスト スタック デバイス リソース解放アイコン](./media/user-guide/usbx-events/image198.png)    | **ホスト スタック デバイス リソース解放** (ux_host_stack_device_resource_free) |
| ![ホスト スタック エンドポイント インスタンス作成アイコン](./media/user-guide/usbx-events/image199.png)    | **ホスト スタック エンドポイント インスタンス作成** (ux_host_stack_endpoint_instance_create) |
| ![ホスト スタック エンドポイント インスタンス削除アイコン](./media/user-guide/usbx-events/image200.png)    | **ホスト スタック エンドポイント インスタンス削除** (ux_host_stack_endpoint_instance_delete) |
| ![ホスト スタック エンドポイント リセット アイコン](./media/user-guide/usbx-events/image201.png)    | **ホスト スタック エンドポイント リセット** (ux_host_stack_endpoint_reset) |
| ![ホスト スタック エンドポイント転送アボート アイコン](./media/user-guide/usbx-events/image202.png)    | **ホスト スタック エンドポイント転送アボート** (ux_host_stack_endpoint_transfer_abort) |
| ![ホスト スタック ホスト コントローラー登録アイコン](./media/user-guide/usbx-events/image203.png)    | **ホスト スタック ホスト コントローラー登録** *(ux_host_stack_hcd_register)* |
| ![ホスト スタック初期化アイコン](./media/user-guide/usbx-events/image204.png)    | **ホスト スタック初期化** *(ux_host_stack_initialize)* |
| ![ホスト スタック インターフェイス エンドポイント取得アイコン](./media/user-guide/usbx-events/image205.png)    | **ホスト スタック インターフェイス エンドポイント取得** *(ux_host_stack_interface_endpoint_get)* |
| ![ホスト スタック インターフェイス インスタンス作成アイコン](./media/user-guide/usbx-events/image206.png)    | **ホスト スタック インターフェイス インスタンス作成** *(ux_host_stack_interface_instance_create)* |
| ![ホスト スタック インターフェイス インスタンス削除アイコン](./media/user-guide/usbx-events/image207.png)    | **ホスト スタック インターフェイス インスタンス削除** *(ux_host_stack_interface_instance_delete)* |
| ![ホスト スタック インターフェイス設定アイコン](./media/user-guide/usbx-events/image208.png)    | **ホスト スタック インターフェイス設定** *(ux_host_stack_interface_set)* |
| ![ホスト スタック インターフェイス設定選択アイコン](./media/user-guide/usbx-events/image209.png)    | **ホスト スタック インターフェイス設定選択** *(ux_host_stack_interface_setting_select)* |
| ![ホスト スタック新規構成作成アイコン](./media/user-guide/usbx-events/image210.png)    | **ホスト スタック新規構成作成** *(ux_host_stack_new_configuration_create)* |
| ![ホスト スタック新規デバイス作成アイコン](./media/user-guide/usbx-events/image211.png)    | **ホスト スタック新規デバイス作成** *(ux_host_stack_new_device_create)* |
| ![ホスト スタック新規エンドポイント作成アイコン](./media/user-guide/usbx-events/image212.png)    | **ホスト スタック新規エンドポイント作成** *(ux_host_stack_new_endpoint_create)* |
| ![ホスト スタック ルート ハブ変更処理アイコン](./media/user-guide/usbx-events/image213.png)    | **ホスト スタック ルート ハブ変更処理** *(ux_host_stack_rh_change_process)* |
| ![ホスト スタック ルート ハブ デバイス抽出アイコン](./media/user-guide/usbx-events/image214.png)    | **ホスト スタック ルート ハブ デバイス抽出** *(ux_host_stack_rh_device_extraction)* |
| ![ホスト スタック ルート ハブ デバイス挿入アイコン](./media/user-guide/usbx-events/image215.png)    | **ホスト スタック ルート ハブ デバイス挿入** *(ux_host_stack_rh_device_insertion)* |
| ![ホスト スタック転送要求アイコン](./media/user-guide/usbx-events/image216.png)    | **ホスト スタック転送要求** *(ux_host_stack_transfer_request)* |
| ![ホスト スタック転送要求アボート アイコン](./media/user-guide/usbx-events/image217.png)    | **ホスト スタック転送要求アボート** *(ux_host_stack_transfer_request_abort)* |
| ![USBX エラー アイコン](./media/user-guide/usbx-events/image218.png)    | **USBX エラー** *(ux_error)* |

## <a name="event-descriptions"></a>イベントの説明

以下のページでは USBX トレース イベントについて説明します。

### <a name="device-class-cdc-activate"></a>デバイス クラス CDC アクティブ化 

#### <a name="ux_device_class_cdc_activate"></a>ux_device_class_cdc_activate

**アイコン** ![デバイス クラス CDC アクティブ化アイコン](./media/user-guide/usbx-events/image1.png)

**説明**

USBX デバイス クラス CDC アクティブ化イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-cdc-deactivate"></a>デバイス クラス CDC 非アクティブ化 

#### <a name="ux_device_class_cdc_deactivate"></a>ux_device_class_cdc_deactivate

**アイコン** ![デバイス クラス CDC 非アクティブ化アイコン](./media/user-guide/usbx-events/image2.png)

**説明**

USBX デバイス クラス CDC 非アクティブ化イベントです。

情報フィールド 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-cdc-read"></a>デバイス クラス CDC 読み取り 

#### <a name="ux_device_class_cdc_read"></a>ux_device_class_cdc_read

**アイコン** ![デバイス クラス CDC 読み取りアイコン](./media/user-guide/usbx-events/image3.png)

**説明**

USBX デバイス クラス CDC 読み取りイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: データ ポインター。
- 情報フィールド 3: 要求された長さ。
- 情報フィールド 4: 使用されません。

### <a name="device-class-cdc-write"></a>デバイス クラス CDC 書き込み 

#### <a name="ux_device_class_cdc_write"></a>ux_device_class_cdc_write

**アイコン** ![デバイス クラス CDC 書き込みアイコン](./media/user-guide/usbx-events/image4.png)

**説明**

USBX デバイス クラス CDC 書き込みイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: データ ポインター。
- 情報フィールド 3: 要求された長さ。
- 情報フィールド 4: 使用されません。

### <a name="device-class-dpump-activate"></a>デバイス クラス DPUMP アクティブ化 

#### <a name="ux_device_class_dpump_activate"></a>ux_device_class_dpump_activate

**アイコン** ![デバイス クラス DPUMP アクティブ化アイコン](./media/user-guide/usbx-events/image5.png)

**説明**

USBX デバイス クラス DPUMP アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-dpump-deactivate"></a>デバイス クラス DPUMP 非アクティブ化 

#### <a name="ux_device_class_dpump_deactivate"></a>ux_device_class_dpump_deactivate

**アイコン** ![デバイス クラス DPUMP 非アクティブ化アイコン](./media/user-guide/usbx-events/image6.png)

**説明**

USBX デバイス クラス DPUMP 非アクティブ化イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-dpump-read"></a>デバイス クラス DPUMP 読み取り 

#### <a name="ux_device_class_dpump_read"></a>ux_device_class_dpump_read

**アイコン** ![デバイス クラス DPUMP 読み取りアイコン](./media/user-guide/usbx-events/image7.png)

**説明**

USBX デバイス クラス DPUMP 読み取りイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: バッファー。
- 情報フィールド 3: 要求された長さ。
- 情報フィールド 4: 使用されません。

### <a name="device-class-dpump-write"></a>デバイス クラス DPUMP 書き込み 

#### <a name="ux_device_class_dpump_write"></a>ux_device_class_dpump_write

**アイコン** ![デバイス クラス DPUMP 書き込みアイコン](./media/user-guide/usbx-events/image8.png)

**説明**

USBX デバイス クラス DPUMP 書き込みイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: データ ポインター。
- 情報フィールド 3: 要求された長さ。
- 情報フィールド 4: 使用されません。

### <a name="device-class-hid-activate"></a>デバイス クラス HID アクティブ化 

#### <a name="ux_device_class_hid_activate"></a>ux_device_class_hid_activate

**アイコン** ![デバイス クラス HID アクティブ化アイコン](./media/user-guide/usbx-events/image9.png)

**説明**

USBX デバイス クラス HID アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-hid-deactivate"></a>デバイス クラス HID 非アクティブ化 

#### <a name="ux_device_class_hid_deactivate"></a>ux_device_class_hid_deactivate

**アイコン** ![デバイス クラス HID 非アクティブ化アイコン](./media/user-guide/usbx-events/image10.png)

**説明**

USBX デバイス クラス HID 非アクティブ化イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-hid-descriptor-send"></a>デバイス クラス HID 記述子送信 

#### <a name="ux_device_class_hid_descritpor_send"></a>ux_device_class_hid_descritpor_send

**アイコン** ![デバイス クラス HID 記述子送信アイコン](./media/user-guide/usbx-events/image11.png)

**説明**

USBX デバイス クラス HID 記述子送信イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 記述子の種類。
- 情報フィールド 3: 要求のインデックス。
- 情報フィールド 4: 使用されません。

### <a name="device-class-hid-event-get"></a>デバイス クラス HID イベント取得 

#### <a name="ux_device_class_hid_event_get"></a>ux_device_class_hid_event_get

**アイコン** ![デバイス クラス HID イベント取得アイコン](./media/user-guide/usbx-events/image12.png)

**説明**

USBX デバイス クラス HID イベント取得イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-hid-event-set"></a>デバイス クラス HID イベント設定 

#### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

**アイコン** ![デバイス クラス HID イベント設定アイコン](./media/user-guide/usbx-events/image13.png)

**説明**

USBX デバイス クラス HID イベント設定イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-hid-report-get"></a>デバイス クラス HID レポート取得 

#### <a name="ux_device_class_hid_report_get"></a>ux_device_class_hid_report_get

**アイコン** ![デバイス クラス HID レポート取得アイコン](./media/user-guide/usbx-events/image14.png)

**説明**

USBX デバイス クラス HID レポート取得イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 記述子の種類。
- 情報フィールド 3: 要求のインデックス。
- 情報フィールド 4: 使用されません。

### <a name="device-class-hid-report-set"></a>デバイス クラス HID レポート設定 

#### <a name="ux_device_class_hid_report_set"></a>ux_device_class_hid_report_set

**アイコン** ![デバイス クラス HID レポート設定アイコン](./media/user-guide/usbx-events/image15.png)

**説明**

USBX デバイス クラス HID レポート設定イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 記述子の種類。
- 情報フィールド 3: 要求のインデックス。
- 情報フィールド 4: 使用されません。

### <a name="device-class-pima-activate"></a>デバイス クラス PIMA アクティブ化

#### <a name="ux_device_class_pima_activate"></a>ux_device_class_pima_activate

**アイコン** ![デバイス クラス PIMA アクティブ化アイコン](./media/user-guide/usbx-events/image16.png)

**説明**

USBX デバイス クラス PIMA アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-pima-deactivate"></a>デバイス クラス PIMA 非アクティブ化 

#### <a name="ux_device_class_pima_deactivate"></a>ux_device_class_pima_deactivate

**アイコン** ![デバイス クラス PIMA 非アクティブ化アイコン](./media/user-guide/usbx-events/image17.png)

**説明**

USBX デバイス クラス PIMA 非アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-pima-device-info-send"></a>デバイス クラス PIMA デバイス情報送信 

#### <a name="ux_device_class_pima_device_info_send"></a>ux_device_class_pima_device_info_send

**アイコン** ![デバイス クラス PIMA デバイス情報送信アイコン](./media/user-guide/usbx-events/image18.png)

**説明**

USBX デバイス クラス PIMA デバイス情報送信イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。

### <a name="device-class-pima-event-get"></a>デバイス クラス PIMA イベント取得 

#### <a name="ux_device_class_pima_event_get"></a>ux_device_class_pima_event_get

**アイコン** ![デバイス クラス PIMA イベント取得アイコン](./media/user-guide/usbx-events/image19.png)

**説明**

USBX デバイス クラス PIMA イベント取得イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: PIMA イベント。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-pima-event-set"></a>デバイス クラス PIMA イベント設定 

#### <a name="ux_device_class_pima_event_set"></a>ux_device_class_pima_event_set

**アイコン** ![デバイス クラス PIMA イベント設定アイコン](./media/user-guide/usbx-events/image20.png)

**説明**

USBX デバイス クラス PIMA イベント設定イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: PIMA イベント。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-pima-object-add"></a>デバイス クラス PIMA オブジェクト追加 

#### <a name="ux_device_class_pima_object_add"></a>ux_device_class_pima_object_add

**アイコン** ![デバイス クラス PIMA オブジェクト追加アイコン](./media/user-guide/usbx-events/image21.png)

**説明**

USBX デバイス クラス PIMA オブジェクト追加イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オブジェクトのハンドル。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-pima-object-data-get"></a>デバイス クラス PIMA オブジェクト データ取得 

#### <a name="ux_device_class_pima_object_data_get"></a>ux_device_class_pima_object_data_get

**アイコン** ![デバイス クラス PIMA オブジェクト データ取得アイコン](./media/user-guide/usbx-events/image22.png)

**説明**

USBX デバイス クラス PIMA オブジェクト データ取得イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オブジェクトのハンドル。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-pima-object-data-send"></a>デバイス クラス PIMA オブジェクト データ送信 

#### <a name="ux_device_class_pima_object_data_send"></a>ux_device_class_pima_object_data_send

**アイコン** ![デバイス クラス PIMA オブジェクト データ送信アイコン](./media/user-guide/usbx-events/image23.png)

**説明**

USBX デバイス クラス PIMA オブジェクト データ送信イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オブジェクトのハンドル。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-pima-object-delete"></a>デバイス クラス PIMA オブジェクト削除 

#### <a name="ux_device_class_pima_object_delete"></a>ux_device_class_pima_object_delete

**アイコン** ![デバイス クラス PIMA オブジェクト削除アイコン](./media/user-guide/usbx-events/image24.png)

**説明**

USBX デバイス クラス PIMA オブジェクト データ削除イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オブジェクトのハンドル。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-pima-object-handles-send"></a>デバイス クラス PIMA オブジェクト ハンドル送信 

#### <a name="ux_device_class_pima_object_handles_send"></a>ux_device_class_pima_object_handles_send

**アイコン** ![デバイス クラス PIMA オブジェクト ハンドル送信アイコン](./media/user-guide/usbx-events/image25.png)

**説明**

USBX デバイス クラス PIMA オブジェクト ハンドル送信イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: ストレージ ID。
- 情報フィールド 3: オブジェクトのフォーマットのコード。
- 情報フィールド 4: オブジェクトの関連付け。

### <a name="device-class-pima-object-info-get"></a>デバイス クラス PIMA オブジェクト情報取得 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**アイコン** ![デバイス クラス PIMA オブジェクト情報取得アイコン](./media/user-guide/usbx-events/image26.png)

**説明**

USBX デバイス クラス PIMA オブジェクト情報取得イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オブジェクトのハンドル。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-pima-object-info-send"></a>デバイス クラス PIMA オブジェクト情報送信 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**アイコン** ![デバイス クラス PIMA オブジェクト情報送信アイコン](./media/user-guide/usbx-events/image27.png)

**説明**

USBX デバイス クラス PIMA オブジェクト情報送信イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-pima-objects-number-send"></a>デバイス クラス PIMA オブジェクト数送信 

#### <a name="ux_device_class_pima_object_number_send"></a>ux_device_class_pima_object_number_send

**アイコン** ![デバイス クラス PIMA オブジェクト数送信アイコン](./media/user-guide/usbx-events/image28.png)

**説明**

USBX デバイス クラス PIMA オブジェクト数送信イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: ストレージ ID。
- 情報フィールド 3: オブジェクトのフォーマットのコード。
- 情報フィールド 4: オブジェクトの関連付け。

### <a name="device-class-pima-partial-object-data-get"></a>デバイス クラス PIMA オブジェクト データ一部取得

#### <a name="ux_device_class_pima_partial_object_data_get"></a>ux_device_class_pima_partial_object_data_get

**アイコン** ![デバイス クラス PIMA オブジェクト データ一部取得アイコン](./media/user-guide/usbx-events/image29.png)

**説明**

USBX デバイス クラス PIMA オブジェクト データ一部取得イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オブジェクトのハンドル。
- 情報フィールド 3: 要求されたオフセット。
- 情報フィールド 4: 要求された長さ。

### <a name="device-class-pima-response-send"></a>デバイス クラス PIMA 応答送信 

#### <a name="ux_device_class_pima_response_send"></a>ux_device_class_pima_response_send

**アイコン** ![デバイス クラス PIMA 応答送信アイコン](./media/user-guide/usbx-events/image30.png)

**説明**

USBX デバイス クラス PIMA 応答送信イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 応答コード。
- 情報フィールド 3: 番号パラメーター。
- 情報フィールド 4: PIMA パラメーター 1。

### <a name="device-class-pima-storage-id-send"></a>デバイス クラス PIMA ストレージ ID 送信 

#### <a name="ux_device_class_pima_storage_id_send"></a>ux_device_class_pima_storage_id_send

**アイコン** ![デバイス クラス PIMA ストレージ ID 送信アイコン](./media/user-guide/usbx-events/image31.png)

**説明**

USBX デバイス クラス PIMA ストレージ ID 送信イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-pima-storage-info-send"></a>デバイス クラス PIMA ストレージ情報送信 

#### <a name="ux_device_class_pima_storage_info_send"></a>ux_device_class_pima_storage_info_send

**アイコン** ![デバイス クラス PIMA ストレージ情報送信アイコン](./media/user-guide/usbx-events/image32.png)

**説明**

USBX デバイス クラス PIMA ストレージ情報送信イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-rndis-activate"></a>デバイス クラス RNDIS アクティブ化 

#### <a name="ux_device_class_rndis_activate"></a>ux_device_class_rndis_activate

**アイコン** ![デバイス クラス RNDIS アクティブ化アイコン](./media/user-guide/usbx-events/image33.png)

**説明**

USBX デバイス クラス RNDIS アクティブ化イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-rndis-deactivate"></a>デバイス クラス RNDIS 非アクティブ化 

#### <a name="ux_device_class_rndis_deactivate"></a>ux_device_class_rndis_deactivate

**アイコン** ![デバイス クラス RNDIS 非アクティブ化アイコン](./media/user-guide/usbx-events/image34.png)

**説明**

USBX デバイス クラス RNDIS 非アクティブ化イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-rndis-message-keep-alive"></a>デバイス クラス RNDIS キープ アライブ メッセージ送信 

#### <a name="ux_device_class_rndis_msg_keep_alive"></a>ux_device_class_rndis_msg_keep_alive

**アイコン** ![デバイス クラス RNDIS キープ アライブ メッセージ送信アイコン](./media/user-guide/usbx-events/image35.png)

**説明**

USBX デバイス クラス RNDIS キープ アライブ メッセージ送信イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-rndis-message-query"></a>デバイス クラス RNDIS クエリ メッセージ送信 

#### <a name="ux_device_class_rndis_msg_keep_query"></a>ux_device_class_rndis_msg_keep_query

**アイコン** ![デバイス クラス RNDIS クエリ メッセージ送信アイコン](./media/user-guide/usbx-events/image36.png)

**説明**

USBX デバイス クラス RNDIS クエリ メッセージ送信イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: RNDIS OID。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-rndis-message-reset"></a>デバイス クラス RNDIS リセット メッセージ送信 

#### <a name="ux_device_class_rndis_msg_reset"></a>ux_device_class_rndis_msg_reset

**アイコン** ![デバイス クラス RNDIS リセット メッセージ送信アイコン](./media/user-guide/usbx-events/image37.png)

**説明**

USBX デバイス クラス RNDIS リセット メッセージ送信イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。

### <a name="device-class-rndis-message-set"></a>デバイス クラス RNDIS 設定メッセージ送信 

#### <a name="ux_device_class_rndis_msg_set"></a>ux_device_class_rndis_msg_set

**アイコン** ![デバイス クラス RNDIS 設定メッセージ送信アイコン](./media/user-guide/usbx-events/image38.png)

**説明**

USBX デバイス クラス RNDIS 設定メッセージ送信イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: RNDIS OID。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-rndis-packet-receive"></a>デバイス クラス RNDIS パケット受信 

#### <a name="ux_device_class_rndis_packet_receive"></a>ux_device_class_rndis_packet_receive

**アイコン** ![デバイス クラス RNDIS パケット受信アイコン](./media/user-guide/usbx-events/image39.png)

**説明**

USBX デバイス クラス RNDIS パケット受信イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-rndis-packet-transmit"></a>デバイス クラス RNDIS パケット送信 

#### <a name="ux_device_class_rndis_packet_transmit"></a>ux_device_class_rndis_packet_transmit

**アイコン** ![デバイス クラス RNDIS パケット送信アイコン](./media/user-guide/usbx-events/image40.png)

**説明**

USBX デバイス クラス RNDIS パケット送信イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-storage-activate"></a>デバイス クラス Storage アクティブ化 

#### <a name="ux_device_class_storage_activate"></a>ux_device_class_storage_activate

**アイコン** ![デバイス クラス Storage アクティブ化アイコン](./media/user-guide/usbx-events/image41.png)

**説明**

USBX デバイス クラス Storage アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-storage-deactivate"></a>デバイス クラス Storage 非アクティブ化 

#### <a name="ux_device_class_storage_deactivate"></a>ux_device_class_storage_deactivate

**アイコン** ![デバイス クラス Storage 非アクティブ化アイコン](./media/user-guide/usbx-events/image42.png)

**説明**

USBX デバイス クラス Storage 非アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-storage-format"></a>デバイス クラス Storage フォーマット 

#### <a name="ux_device_class_storage_format"></a>ux_device_class_storage_format

**アイコン** ![デバイス クラス Storage フォーマット アイコン](./media/user-guide/usbx-events/image43.png)

**説明**

USBX デバイス クラス Storage フォーマット イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: Lun。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-storage-inquiry"></a>デバイス クラス Storage 照会 

#### <a name="ux_device_class_storage_inquiry"></a>ux_device_class_storage_inquiry

**アイコン** ![デバイス クラス Storage 照会アイコン](./media/user-guide/usbx-events/image44.png)

**説明**

USBX デバイス クラス Storage 照会イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: Lun。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-storage-mode-select"></a>デバイス クラス Storage モード選択

#### <a name="ux_device_class_storage_mode_select"></a>ux_device_class_storage_mode_select

**アイコン** ![デバイス クラス Storage モード選択アイコン](./media/user-guide/usbx-events/image45.png)

**説明**

USBX デバイス クラス Storage モード選択イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: Lun。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-storage-mode-sense"></a>デバイス クラス Storage モード センス 

#### <a name="ux_device_class_storage_mode_sense"></a>ux_device_class_storage_mode_sense

**アイコン](./media/user-guide/usbx-events/image46.png)** デバイス クラス Storage モード センス アイコン![

**説明**

USBX デバイス クラス Storage モード センス イベントです。

情報フィールド 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: Lun。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-storage-prevent-allow-media-removal"></a>デバイス クラス Storage メディア取り外し禁止/許可 

#### <a name="ux_device_class_storage_prevent_allow_media_removal"></a>ux_device_class_storage_prevent_allow_media_removal

**アイコン** ![デバイス クラス Storage メディア取り外し禁止/許可アイコン](./media/user-guide/usbx-events/image47.png)

**説明**

USBX デバイス クラス Storage メディア取り外し禁止/許可イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: Lun。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-storage-read"></a>デバイス クラス Storage 読み取り 

#### <a name="ux_device_class_storage_read"></a>ux_device_class_storage_read

**アイコン** ![デバイス クラス Storage 読み取りアイコン](./media/user-guide/usbx-events/image48.png)

**説明**

USBX デバイス クラス Storage 読み取りイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: Lun。
- 情報フィールド 3: セクター。
- 情報フィールド 4: セクター数。

### <a name="device-class-storage-read-capacity"></a>デバイス クラス Storage 容量読み取り 

#### <a name="ux_device_class_storage_read_capacity"></a>ux_device_class_storage_read_capacity

**アイコン** ![デバイス クラス Storage 容量読み取りアイコン](./media/user-guide/usbx-events/image49.png)

**説明**

USBX デバイス クラス Storage 容量読み取りイベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: Lun。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-storage-read-format-capacity"></a>デバイス クラス Storage フォーマット容量読み取り 

#### <a name="ux_device_class_storage_read_format_capacity"></a>ux_device_class_storage_read_format_capacity

**アイコン** ![デバイス クラス Storage フォーマット容量読み取りアイコン](./media/user-guide/usbx-events/image50.png)

**説明**

USBX デバイス クラス Storage フォーマット容量読み取りイベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: Lun。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-storage-read-toc"></a>デバイス クラス Storage TOC 読み取り 

#### <a name="ux_device_class_storage_read_toc"></a>ux_device_class_storage_read_toc

**アイコン** ![デバイス クラス Storage TOC 読み取りアイコン](./media/user-guide/usbx-events/image51.png)

**説明**

USBX デバイス クラス Storage TOC 読み取りイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: Lun。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-storage-request-sense"></a>デバイス クラス Storage センス データ要求 

#### <a name="ux_device_class_storage_request_sense"></a>ux_device_class_storage_request_sense

**アイコン** ![デバイス クラス Storage センス データ要求アイコン](./media/user-guide/usbx-events/image52.png)

**説明**

USBX デバイス クラス Storage センス データ要求イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: Lun。
- 情報フィールド 3: センス キー。
- 情報フィールド 4: コード。

### <a name="device-class-storage-start-stop"></a>デバイス クラス Storage 開始/停止 

#### <a name="ux_device_class_storage_start_stop"></a>ux_device_class_storage_start_stop

**アイコン** ![デバイス クラス Storage 開始/停止アイコン](./media/user-guide/usbx-events/image53.png)

**説明**

USBX デバイス クラス Storage 開始/停止イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: Lun。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-storage-test-ready"></a>デバイス クラス Storage 準備状態テスト 

#### <a name="ux_device_class_storage_test_ready"></a>ux_device_class_storage_test_ready

**アイコン** ![デバイス クラス Storage 準備状態テスト アイコン](./media/user-guide/usbx-events/image54.png)

**説明**

USBX デバイス クラス Storage 準備状態テスト イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: Lun。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-storage-verify"></a>デバイス クラス Storage 検証 

#### <a name="ux_device_class_storage_verify"></a>ux_device_class_storage_verify

**アイコン** ![デバイス クラス Storage 検証アイコン](./media/user-guide/usbx-events/image55.png)

**説明**

USBX デバイス クラス Storage 検証イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: Lun。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-class-storage-write"></a>デバイス クラス Storage 書き込み 

#### <a name="ux_device_class_storage_write"></a>ux_device_class_storage_write

**アイコン** ![デバイス クラス Storage 書き込みアイコン](./media/user-guide/usbx-events/image56.png)

**説明**

USBX デバイス クラス Storage 書き込みイベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: Lun。
- 情報フィールド 3: セクター。
- 情報フィールド 4: セクター数。

### <a name="device-stack-alternate-setting-get"></a>デバイス スタック設定選択肢取得 

#### <a name="ux_device_class_alternate_setting_get"></a>ux_device_class_alternate_setting_get

**アイコン** ![デバイス スタック設定選択肢取得アイコン](./media/user-guide/usbx-events/image57.png)

**説明**

USBX デバイス スタック設定選択肢取得イベントです。

**情報フィールド**

- 情報フィールド 1: インターフェイスの値。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-alternate-setting-set"></a>デバイス スタック設定選択肢設定 

#### <a name="ux_device_class_alternate_setting_set"></a>ux_device_class_alternate_setting_set

**アイコン** ![デバイス スタック設定選択肢設定アイコン](./media/user-guide/usbx-events/image58.png)

**説明**

USBX デバイス スタック設定選択肢設定イベントです。

**情報フィールド**
- 情報フィールド 1: インターフェイスの値。
- 情報フィールド 2: 選択可能な設定の値。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-class-register"></a>デバイス スタック クラス登録 

#### <a name="ux_device_stack_class_register"></a>ux_device_stack_class_register

**アイコン** ![デバイス スタック クラス登録アイコン](./media/user-guide/usbx-events/image59.png)

**説明**

USBX デバイス スタック クラス登録イベントです。

**情報フィールド**

- 情報フィールド 1: クラス名。
- 情報フィールド 2: インターフェイス番号。
- 情報フィールド 3: パラメーター。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-clear-feature"></a>デバイス スタック機能消去 

#### <a name="ux_device_stack_clear_feature"></a>ux_device_stack_clear_feature

**アイコン** ![デバイス スタック機能消去アイコン](./media/user-guide/usbx-events/image60.png)

**説明**

USBX デバイス スタック機能消去イベントです。

**情報フィールド**

- 情報フィールド 1: 要求の種類。
- 情報フィールド 2: 要求の値。 情報フィールド 3: 要求のインデックス。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-configuration-get"></a>デバイス スタック構成取得 

#### <a name="ux_device_stack_configuration_get-t"></a>ux_device_stack_configuration_get t

**アイコン** ![デバイス スタック構成取得アイコン](./media/user-guide/usbx-events/image61.png)

**説明**

USBX デバイス スタック構成取得イベントです。

**情報フィールド** 

- 情報フィールド 1: 構成値。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-configuration-set"></a>デバイス スタック構成設定 

#### <a name="ux_device_stack_configuration_set"></a>ux_device_stack_configuration_set

**アイコン** ![デバイス スタック構成設定アイコン](./media/user-guide/usbx-events/image62.png)

**説明**

USBX デバイス スタック構成設定イベントです。

**情報フィールド** 

- 情報フィールド 1: 構成値。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-connect"></a>デバイス スタック接続 

#### <a name="ux_device_stack_connect"></a>ux_device_stack_connect

**アイコン** ![デバイス スタック接続アイコン](./media/user-guide/usbx-events/image63.png)

**説明**

USBX デバイス スタック記述子送信イベントです。

**情報フィールド**

- 情報フィールド 1: 使用されません。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-descriptor-send"></a>デバイス スタック記述子送信 

#### <a name="ux_device_stack_descriptor_send"></a>ux_device_stack_descriptor_send

**アイコン** ![デバイス スタック記述子送信アイコン](./media/user-guide/usbx-events/image64.png)

**説明**

USBX デバイス スタック記述子送信イベントです。

**情報フィールド**

- 情報フィールド 1: 記述子の種類。
- 情報フィールド 2: 要求のインデックス。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-disconnect"></a>デバイス スタック切断 

#### <a name="ux_device_stack_disconnect"></a>ux_device_stack_disconnect

**アイコン** ![デバイス スタック切断アイコン](./media/user-guide/usbx-events/image65.png)

**説明**

USBX デバイス スタック切断イベントです。

**情報フィールド**

- 情報フィールド 1: デバイス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-endpoint-stall"></a>デバイス スタック エンドポイント停止 

#### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

**アイコン** ![デバイス スタック エンドポイント停止アイコン](./media/user-guide/usbx-events/image66.png)

**説明**

USBX デバイス スタック エンドポイント停止イベントです。

**情報フィールド** 

- 情報フィールド 1: エンドポイント。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-get-status"></a>デバイス スタック状態取得 

#### <a name="ux_device_stack_get_status"></a>ux_device_stack_get_status

**アイコン** ![デバイス スタック状態取得アイコン](./media/user-guide/usbx-events/image67.png)

**説明**

USBX デバイス スタック状態取得イベントです。

**情報フィールド**

- 情報フィールド 1: 使用されません。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-host-wakeup"></a>デバイス スタック ホスト スリープ解除 

#### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

**アイコン** ![デバイス スタック ホスト スリープ解除アイコン](./media/user-guide/usbx-events/image68.png)

**説明**

USBX デバイス スタック ホスト スリープ解除イベントです。

**情報フィールド** 

- 情報フィールド 1: 使用されません。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-initialize"></a>デバイス スタック初期化 

#### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

**アイコン** ![デバイス スタック初期化アイコン](./media/user-guide/usbx-events/image69.png)

**説明**

USBX デバイス スタック初期化イベントです。

**情報フィールド** 

- 情報フィールド 1: 使用されません。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-interface-delete"></a>デバイス スタック インターフェイス削除 

#### <a name="ux_device_stack_interface_delete"></a>ux_device_stack_interface_delete

**アイコン** ![デバイス スタック インターフェイス削除アイコン](./media/user-guide/usbx-events/image70.png)

**説明**

USBX デバイス スタック インターフェイス削除イベントです。

**情報フィールド**

- 情報フィールド 1: インターフェイス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-interface-get"></a>デバイス スタック インターフェイス取得 

#### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

**アイコン** ![デバイス スタック インターフェイス取得アイコン](./media/user-guide/usbx-events/image71.png)

**説明**

USBX デバイス スタック インターフェイス取得イベントです。

**情報フィールド** 

- 情報フィールド 1: インターフェイスの値。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-interface-set"></a>デバイス スタック インターフェイス設定 

#### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

**アイコン** ![デバイス スタック インターフェイス設定アイコン](./media/user-guide/usbx-events/image72.png)

**説明**

USBX デバイス スタック インターフェイス設定イベントです。

**情報フィールド** 

- 情報フィールド 1: 要求の値。 情報フィールド 2: 要求のインデックス。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-set-feature"></a>デバイス スタック機能設定 

#### <a name="ux_device_stack_set_feature"></a>ux_device_stack_set_feature

**アイコン** ![デバイス スタック機能設定アイコン](./media/user-guide/usbx-events/image73.png)

**説明**

USBX デバイス スタック機能設定イベントです。

**情報フィールド** 

- 情報フィールド 1: 要求の値。 情報フィールド 2: 要求のインデックス。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-transfer-abort"></a>デバイス スタック転送アボート 

#### <a name="ux_device_stack_transfer_abort"></a>ux_device_stack_transfer_abort

**アイコン** ![デバイス スタック転送アボート アイコン](./media/user-guide/usbx-events/image74.png)

**説明**

USBX デバイス スタック転送アボート イベントです。

**情報フィールド** 

- 情報フィールド 1: 転送要求。
- 情報フィールド 2: 完了コード。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-transfer-all-request-abort"></a>デバイス スタック全転送要求アボート 

#### <a name="ux_device_stack_transfer_all_request_abort"></a>ux_device_stack_transfer_all_request_abort

**アイコン** ![デバイス スタック全転送要求アボート アイコン](./media/user-guide/usbx-events/image75.png)

**説明**

USBX デバイス スタック全転送要求アボート イベントです。

**情報フィールド** 

- 情報フィールド 1: エンドポイント。
- 情報フィールド 2: 完了コード。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="device-stack-transfer-request"></a>デバイス スタック転送要求 

#### <a name="ux_device_stack_transfer_request"></a>ux_device_stack_transfer_request

**アイコン** ![デバイス スタック転送要求アイコン](./media/user-guide/usbx-events/image76.png)

**説明**

USBX デバイス スタック転送要求イベントです。

**情報フィールド**

- 情報フィールド 1: 転送要求。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-asix-activate"></a>ホスト クラス ASIX アクティブ化 

#### <a name="ux_host_class_asix_activate"></a>ux_host_class_asix_activate

**アイコン** ![ホスト クラス ASIX アクティブ化アイコン](./media/user-guide/usbx-events/image77.png)

**説明**

USBX ホスト クラス ASIX アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-asix-deactivate"></a>ホスト クラス ASIX 非アクティブ化 

#### <a name="ux_host_class_asix_deactivate"></a>ux_host_class_asix_deactivate

**アイコン** ![ホスト クラス ASIX 非アクティブ化アイコン](./media/user-guide/usbx-events/image78.png)

**説明**

USBX ホスト クラス ASIX 非アクティブ化イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-asix-interrupt-notification"></a>ホスト クラス ASIX 割り込み通知 

#### <a name="ux_host_class_asix_interrupt_notification"></a>ux_host_class_asix_interrupt_notification

**アイコン** ![ホスト クラス ASIX 割り込み通知アイコン](./media/user-guide/usbx-events/image79.png)

**説明**

USBX ホスト クラス ASIX 割り込み通知イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-asix-read"></a>ホスト クラス ASIX 読み取り 

#### <a name="ux_host_class_asix_read"></a>ux_host_class_asix_read

**アイコン** ![ホスト クラス ASIX 読み取りアイコン](./media/user-guide/usbx-events/image80.png)

**説明**

USBX ホスト クラス ASIX 読み取りイベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: データ ポインター。
- 情報フィールド 3: 要求された長さ。
- 情報フィールド 4: 使用されません。

### <a name="host-class-asix-write"></a>ホスト クラス ASIX 書き込み 

#### <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

**アイコン** ![ホスト クラス ASIX 書き込みアイコン](./media/user-guide/usbx-events/image81.png)

**説明**

USBX ホスト クラス ASIX 書き込みイベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: データ ポインター。
- 情報フィールド 3: 要求された長さ。
- 情報フィールド 4: 使用されません。

### <a name="host-class-audio-activate"></a>ホスト クラス Audio アクティブ化 

#### <a name="ux_host_class_audio_activate"></a>ux_host_class_audio_activate

**アイコン** ![ホスト クラス Audio アクティブ化アイコン](./media/user-guide/usbx-events/image82.png)

**説明**

USBX ホスト クラス Audio アクティブ化イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-audio-control-value-get"></a>ホスト クラス Audio コントロール値取得 

#### <a name="ux_host_class_audio_control_value_get"></a>ux_host_class_audio_control_value_get

**アイコン** ![ホスト クラス Audio コントロール値取得アイコン](./media/user-guide/usbx-events/image83.png)

**説明**

USBX ホスト クラス Audio コントロール値取得イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-audio-control-value-set"></a>ホスト クラス Audio コントロール値設定 

#### <a name="ux_host_class_audio_control_value_set"></a>ux_host_class_audio_control_value_set

**アイコン** ![ホスト クラス Audio コントロール値設定アイコン](./media/user-guide/usbx-events/image84.png)

**説明**

NetX の I/O ドライバーの遅延処理イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オーディオ コントロール。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-audio-deactivate"></a>ホスト クラス Audio 非アクティブ化 

#### <a name="ux_host_class_audio_deactivate"></a>ux_host_class_audio_deactivate

**アイコン** ![ホスト クラス Audio 非アクティブ化アイコン](./media/user-guide/usbx-events/image85.png)

**説明**

USBX ホスト クラス Audio 非アクティブ化イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-audio-read"></a>ホスト クラス Audio 読み取り 

#### <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

**アイコン** ![ホスト クラス Audio 読み取りアイコン](./media/user-guide/usbx-events/image86.png)

**説明**

USBX ホスト クラス Audio 読み取りイベントです。

- 情報フィールド 
- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: データ ポインター。
- 情報フィールド 3: 要求された長さ。
- 情報フィールド 4: 使用されません。

### <a name="host-class-audio-streaming-sampling-get"></a>ホスト クラス Audio ストリーミング サンプリング取得 

#### <a name="ux_host_class_audio_streaming_sampling_get"></a>ux_host_class_audio_streaming_sampling_get

**アイコン** ![ホスト クラス Audio ストリーミング サンプリング取得アイコン](./media/user-guide/usbx-events/image87.png)

**説明**

USBX ホスト クラス Audio ストリーミング サンプリング取得イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-audio-streaming-sampling-set"></a>ホスト クラス Audio ストリーミング サンプリング設定 

#### <a name="ux_host_class_audio_streaming_sampling_set"></a>ux_host_class_audio_streaming_sampling_set

**アイコン** ![ホスト クラス Audio ストリーミング サンプリング設定アイコン](./media/user-guide/usbx-events/image88.png)

**説明**

USBX ホスト クラス Audio ストリーミング サンプリング設定イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オーディオ サンプリング。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-audio-write"></a>ホスト クラス Audio 書き込み 

#### <a name="ux_host_class_audio_write"></a>ux_host_class_audio_write

**アイコン** ![ホスト クラス Audio 書き込みアイコン](./media/user-guide/usbx-events/image89.png)

**説明**

USBX ホスト クラス Audio 書き込みイベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: データ ポインター。
- 情報フィールド 3: 要求された長さ。
- 情報フィールド 4: 使用されません。

### <a name="host-class-cdc-acm-activate"></a>ホスト クラス CDC ACM アクティブ化 

#### <a name="ux_host_class_cdc_acm_activate"></a>ux_host_class_cdc_acm_activate

**アイコン** ![ホスト クラス CDC ACM アクティブ化アイコン](./media/user-guide/usbx-events/image90.png)

**説明**

USBX ホスト クラス CDC ACM アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-cdc-acm-deactivate"></a>ホスト クラス CDC ACM 非アクティブ化 

#### <a name="ux_host_class_cdc_acm_deactivate"></a>ux_host_class_cdc_acm_deactivate

**アイコン** ![ホスト クラス CDC ACM 非アクティブ化アイコン](./media/user-guide/usbx-events/image91.png)

**説明**

USBX ホスト クラス CDC ACM 非アクティブ化イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-cdc-acm-ioctl-abort-in-pipe"></a>ホスト クラス CDC ACM IOCTL 入力パイプ アボート 

#### <a name="ux_host_class_cdc_acm_ioctl_abort_in_pipe"></a>ux_host_class_cdc_acm_ioctl_abort_in_pipe

**アイコン** ![ホスト クラス CDC ACM IOCTL 入力パイプ アボート アイコン](./media/user-guide/usbx-events/image92.png)

**説明**

USBX ホスト クラス CDC ACM IOCTL 入力パイプ アボート イベントです。

情報フィールド 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: エンドポイント。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-cdc-acm-ioctl-abort-out-pipe"></a>ホスト クラス CDC ACM IOCTL 出力パイプ アボート 

#### <a name="ux_host_class_cdc_acm_ioct_abort_out_pipe"></a>ux_host_class_cdc_acm_ioct_abort_out_pipe

**アイコン** ![[ホスト クラス CDC ACM IOCTL 出力パイプ アボート アイコン](./media/user-guide/usbx-events/image93.png)

**説明**

USBX ホスト クラス CDC ACM IOCTL 出力パイプ アボート イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: エンドポイント。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-cdc-acm-ioctl-get-device-status"></a>ホスト クラス CDC ACM IOCTL デバイス状態取得 

#### <a name="ux_host_class_cdc_acm_ioctl_get_device_status"></a>ux_host_class_cdc_acm_ioctl_get_device_status

**アイコン** ![ホスト クラス CDC ACM IOCTL デバイス状態取得アイコン](./media/user-guide/usbx-events/image94.png)

**説明**

USBX ホスト クラス CDC ACM IOCTL デバイス状態取得イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: デバイスの状態。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-cdc-acm-ioctl-get-line-coding"></a>ホスト クラス CDC ACM IOCTL 伝送路符号化取得 

#### <a name="ux_host_class_cdc_acm_ioctl_get_line_coding"></a>ux_host_class_cdc_acm_ioctl_get_line_coding

**アイコン** ![ホスト クラス CDC ACM IOCTL 伝送路符号化取得アイコン](./media/user-guide/usbx-events/image95.png)

**説明**

USBX ホスト クラス CDC ACM IOCTL 伝送路符号化取得イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: パラメーター。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-cdc-acm-ioctl-notification-callback"></a>ホスト クラス CDC ACM IOCTL 通知コールバック

#### <a name="ux_host_class_cdc_acm_ioctl_notification_callback"></a>ux_host_class_cdc_acm_ioctl_notification_callback

**アイコン** ![ホスト クラス CDC ACM IOCTL 通知コールバック アイコン](./media/user-guide/usbx-events/image96.png)

**説明**

USBX ホスト クラス CDC ACM IOCTL 通知コールバック イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: パラメーター。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-cdc-acm-ioctl-send-break"></a>ホスト クラス CDC ACM IOCTL ブレーク送信 

#### <a name="ux_host_class_cdc_acm_ioctl_send_break"></a>ux_host_class_cdc_acm_ioctl_send_break

**アイコン** ![ホスト クラス CDC ACM IOCTL ブレーク送信アイコン](./media/user-guide/usbx-events/image97.png)

**説明**

USBX ホスト クラス CDC ACM IOCTL ブレーク送信イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: パラメーター。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-cdc-acm-ioctl-set-line-coding"></a>ホスト クラス CDC ACM IOCTL 伝送路符号化設定 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_coding"></a>ux_host_class_cdc_acm_ioctl_set_line_coding

**アイコン** ![ホスト クラス CDC ACM IOCTL 伝送路符号化設定アイコン](./media/user-guide/usbx-events/image97.png) icon](./media/user-guide/usbx-events/image98.png)

**説明**

USBX ホスト クラス CDC ACM IOCTL 伝送路符号化設定イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: パラメーター。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-cdc-acm-ioctl-set-line-state"></a>ホスト クラス CDC ACM IOCTL 伝送路状態設定 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_state"></a>ux_host_class_cdc_acm_ioctl_set_line_state

**アイコン** ![ホスト クラス CDC ACM IOCTL 伝送路状態設定アイコン](./media/user-guide/usbx-events/image99.png)

**説明**

USBX ホスト クラス CDC ACM IOCTL 伝送路状態設定イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: パラメーター。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-cdc-acm-read"></a>ホスト クラス CDC ACM 読み取り 

#### <a name="ux_host_class_cdc_acm_read"></a>ux_host_class_cdc_acm_read

**アイコン** ![ホスト クラス CDC ACM 読み取りアイコン](./media/user-guide/usbx-events/image100.png)

**説明**

USBX ホスト クラス CDC ACM 読み取りイベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: データ ポインター。
- 情報フィールド 3: 要求された長さ。
- 情報フィールド 4: 使用されません。

### <a name="host-class-cdc-acm-reception-start"></a>ホスト クラス CDC ACM 受信開始 

#### <a name="ux_host_class_cdc_acm_reception_start"></a>ux_host_class_cdc_acm_reception_start

**アイコン** ![ホスト クラス CDC ACM 受信開始アイコン](./media/user-guide/usbx-events/image101.png)

**説明**

USBX ホスト クラス CDC ACM 受信開始イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-cdc-acm-reception-stop"></a>ホスト クラス CDC ACM 受信停止 

#### <a name="ux_host_class_cdc_acm_reception_stop"></a>ux_host_class_cdc_acm_reception_stop

**アイコン** ![ホスト クラス CDC ACM 受信停止アイコン](./media/user-guide/usbx-events/image102.png)

**説明**

USBX ホスト クラス CDC ACM 受信停止イベントです。

**情報フィールド**

- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-cdc-acm-write"></a>ホスト クラス CDC ACM 書き込み 

#### <a name="ux_host_class_acm_write"></a>ux_host_class_acm_write

**アイコン** ![ホスト クラス CDC ACM 書き込みアイコン](./media/user-guide/usbx-events/image103.png)

**説明**

USBX ホスト クラス CDC ACM 書き込みイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: データ ポインター。
- 情報フィールド 3: 要求された長さ。
- 情報フィールド 4: 使用されません。

### <a name="host-class-dpump-activate"></a>ホスト クラス DPUMP アクティブ化 

#### <a name="ux_host_class_dpump_activate"></a>ux_host_class_dpump_activate

**アイコン** ![ホスト クラス DPUMP アクティブ化アイコン](./media/user-guide/usbx-events/image104.png)

**説明**

USBX ホスト クラス DPUMP アクティブ化イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-dpump-deactivate"></a>ホスト クラス DPUMP 非アクティブ化 

#### <a name="ux_host_class_dpump_deactivate"></a>ux_host_class_dpump_deactivate

**アイコン** ![ホスト クラス DPUMP 非アクティブ化アイコン](./media/user-guide/usbx-events/image105.png)

**説明**

USBX ホスト クラス DPUMP 非アクティブ化イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-dpump-read"></a>ホスト クラス DPUMP 読み取り 

#### <a name="ux_host_class_dpump_read"></a>ux_host_class_dpump_read

**アイコン** ![ホスト クラス DPUMP 読み取りアイコン](./media/user-guide/usbx-events/image106.png)

**説明**

USBX ホスト クラス DPUMP 読み取りイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: データ ポインター。
- 情報フィールド 3: 要求された長さ。
- 情報フィールド 4: 使用されません。

### <a name="host-class-dpump-write"></a>ホスト クラス DPUMP 書き込み 

#### <a name="ux_host_class_dpump_write"></a>ux_host_class_dpump_write

**アイコン** ![ホスト クラス DPUMP 書き込みアイコン](./media/user-guide/usbx-events/image107.png)

**説明**

USBX ホスト クラス DPUMP 書き込みイベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: データ ポインター。
- 情報フィールド 3: 要求された長さ。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hid-activate"></a>ホスト クラス HID アクティブ化 

#### <a name="ux_host_class_hid_activate"></a>ux_host_class_hid_activate

**アイコン** ![ホスト クラス HID アクティブ化アイコン](./media/user-guide/usbx-events/image108.png)

**説明**

USBX ホスト クラス HID アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hid-client-register"></a>ホスト クラス HID クライアント登録 

#### <a name="ux_host_class_hid_client_register"></a>ux_host_class_hid_client_register

**アイコン** ![ホスト クラス HID クライアント登録アイコン](./media/user-guide/usbx-events/image109.png)

**説明**

USBX ホスト クラス HID クライアント登録イベントです。

**情報フィールド** 

- 情報フィールド 1: HID クライアント名。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hid-deactivate"></a>ホスト クラス HID 非アクティブ化 

#### <a name="ux_host_class_hid_deactivate"></a>ux_host_class_hid_deactivate

**アイコン** ![ホスト クラス HID 非アクティブ化アイコン](./media/user-guide/usbx-events/image110.png)

**説明**

USBX ホスト クラス HID 非アクティブ化イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hid-idle-get"></a>ホスト クラス HID アイドル取得 

#### <a name="ux_host_class_hid_idle_get"></a>ux_host_class_hid_idle_get

**アイコン** ![ホスト クラス HID アイドル取得アイコン](./media/user-guide/usbx-events/image111.png)

**説明**

USBX ホスト クラス HID アイドル取得イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hid-idle-set"></a>ホスト クラス HID アイドル設定 

#### <a name="ux_host_class_hid_idle_set"></a>ux_host_class_hid_idle_set

**アイコン** ![ホスト クラス HID アイドル設定アイコン](./media/user-guide/usbx-events/image112.png)

**説明**

USBX ホスト クラス HID アイドル設定イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hid-keyboard-activate"></a>ホスト クラス HID キーボード アクティブ化 

#### <a name="ux_host_class_hid_keyboard_activate"></a>ux_host_class_hid_keyboard_activate

**アイコン** ![ホスト クラス HID キーボード アクティブ化アイコン](./media/user-guide/usbx-events/image113.png)

**説明**

USBX ホスト クラス HID キーボード アクティブ化イベントです。

**情報フィールド**
<p>情報フィールド 1: クラスのインスタンス。
<p>情報フィールド 2: HID クライアント インスタンス。
<p>情報フィールド 3: 使用されません。
<p>情報フィールド 4: 使用されません。

### <a name="host-class-hid-keyboard-deactivate"></a>ホスト クラス HID キーボード非アクティブ化 

#### <a name="ux_host_class_hid_keyboard_deactivate"></a>ux_host_class_hid_keyboard_deactivate

**アイコン** ![ホスト クラス HID キーボード非アクティブ化アイコン](./media/user-guide/usbx-events/image114.png)

**説明**

USBX ホスト クラス HID キーボード非アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: HID クライアント インスタンス。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hid-mouse-activate"></a>ホスト クラス HID マウス アクティブ化 

#### <a name="ux_host_class_hid_mouse_activate"></a>ux_host_class_hid_mouse_activate

**アイコン** ![ホスト クラス HID マウス アクティブ化アイコン](./media/user-guide/usbx-events/image115.png)

**説明**

USBX ホスト クラス HID マウス アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: HID クライアント インスタンス。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hid-mouse-deactivate"></a>ホストクラス HID マウス非アクティブ化 

#### <a name="ux_host_class_hid_mouse_deactivate"></a>ux_host_class_hid_mouse_deactivate

**アイコン** ![ホスト クラス HID マウス非アクティブ化アイコン](./media/user-guide/usbx-events/image116.png)

**説明**

- USBX ホスト クラス HID マウス非アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: HID クライアント インスタンス。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hid-remote-control-activate"></a>ホスト クラス HID リモート制御アクティブ化 

#### <a name="ux_host_class_hid_remote_control_activate"></a>ux_host_class_hid_remote_control_activate

**アイコン** ![ホスト クラス HID リモート制御アクティブ化アイコン](./media/user-guide/usbx-events/image117.png)

**説明**

USBX ホスト クラス HID リモート制御アクティブ化イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: HID クライアント インスタンス。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hid-remote-control-deactivate"></a>ホスト クラス HID リモート制御非アクティブ化 

#### <a name="ux_host_class_hid_remote_control_deactivate"></a>ux_host_class_hid_remote_control_deactivate

**アイコン** ![ホスト クラス HID リモート制御非アクティブ化アイコン](./media/user-guide/usbx-events/image118.png)

**説明**

USBX ホスト クラス HID リモート制御非アクティブ化イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: HID クライアント インスタンス。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hid-report-get"></a>ホスト クラス HID レポート取得 

#### <a name="ux_host_class_hid_report_get"></a>ux_host_class_hid_report_get

**アイコン** ![ホスト クラス HID レポート取得アイコン](./media/user-guide/usbx-events/image119.png)

**説明**

USBX ホスト クラス HID レポート取得イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: クライアントのレポート。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hid-report-set"></a>ホスト クラス HID レポート設定 

#### <a name="ux_host_class_hid_report_set"></a>ux_host_class_hid_report_set

**アイコン** ![ホスト クラス HID レポート設定アイコン](./media/user-guide/usbx-events/image120.png)

**説明** USBX ホスト クラス HID レポート設定イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: クライアントのレポート。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hub-activate"></a>ホスト クラス Hub アクティブ化 

#### <a name="ux_host_class_hub_activate"></a>ux_host_class_hub_activate

**アイコン** ![ホスト クラス Hub アクティブ化アイコン](./media/user-guide/usbx-events/image121.png)

**説明**

USBX ホスト クラス Hub アクティブ化イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hub-change-detect"></a>ホスト クラス Hub 変更検出 

#### <a name="ux_host_class_hub_change_detect"></a>ux_host_class_hub_change_detect

**アイコン** ![ホスト クラス Hub 変更検出アイコン](./media/user-guide/usbx-events/image122.png)

**説明**

USBX ホスト クラス Hub 変更検出イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hub-deactivate"></a>ホスト クラス Hub 非アクティブ化 

#### <a name="ux_host_class_hub_deactivate"></a>ux_host_class_hub_deactivate

**アイコン** ![ホスト クラス Hub 非アクティブ化アイコン](./media/user-guide/usbx-events/image123.png)

**説明**

USBX ホスト クラス Hub 非アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hub-port-change-connection-process"></a>ホスト クラス Hub ポート変更接続処理 

#### <a name="ux_host_class_hub_change_connection_process"></a>ux_host_class_hub_change_connection_process

**アイコン** ![ホスト クラス Hub ポート変更接続処理アイコン](./media/user-guide/usbx-events/image124.png)

**説明**

USBX ホスト クラス Hub ポート変更接続処理イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: ポート。
- 情報フィールド 3: ポートの状態。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hub-port-change-enable-process"></a>ホスト クラス Hub ポート変更有効化処理 

#### <a name="ux_host_class_hub_port_change_enable_process"></a>ux_host_class_hub_port_change_enable_process

**アイコン** ![ホスト クラス Hub ポート変更有効化処理アイコン](./media/user-guide/usbx-events/image125.png)

**説明**

USBX ホスト クラス Hub ポート変更有効化処理イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: ポート。
- 情報フィールド 3: ポートの状態。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hub-port-change-over-current-process"></a>ホスト クラス Hub ポート変更過電流処理 

#### <a name="ux_host_class_hub_port_change_over_current_process"></a>ux_host_class_hub_port_change_over_current_process

**アイコン** ![ホスト クラス Hub ポート変更過電流処理アイコン](./media/user-guide/usbx-events/image126.png)

**説明**

nx_packet_allocate でパケットを割り当てるイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: ポート。
- 情報フィールド 3: ポートの状態。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hub-port-change-reset-process"></a>ホスト クラス Hub ポート変更リセット処理 

#### <a name="ux_host_class_hub_port_change_reset_process"></a>ux_host_class_hub_port_change_reset_process

**アイコン** ![ホスト クラス Hub ポート変更リセット処理アイコン](./media/user-guide/usbx-events/image127.png)

**説明**

USBX ホスト クラス Hub ポート変更リセット処理イベントです。

**情報フィールド**

- 情報フィールド 1: ハブ。 情報フィールド 2: ポート。
- 情報フィールド 3: ポートの状態。
- 情報フィールド 4: 使用されません。

### <a name="host-class-hub-port-change-suspend-process"></a>ホスト クラス Hub ポート変更中断処理 

#### <a name="ux_host_class_hub_port_change_suspend_process"></a>ux_host_class_hub_port_change_suspend_process

**アイコン** ![ホスト クラス Hub ポート変更中断処理アイコン](./media/user-guide/usbx-events/image128.png)

**説明**

USBX ホスト クラス Hub ポート変更中断処理イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: ポート。
- 情報フィールド 3: ポートの状態。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-activate"></a>ホスト クラス PIMA アクティブ化 

#### <a name="ux_host_class_pima_activate"></a>ux_host_class_pima_activate

**アイコン** ![ホスト クラス PIMA アクティブ化アイコン](./media/user-guide/usbx-events/image129.png)

**説明**

USBX ホスト クラス PIMA アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-deactivate"></a>ホスト クラス PIMA 非アクティブ化 

#### <a name="ux_host_class_pima_deactivate"></a>ux_host_class_pima_deactivate

**アイコン** ![ホスト クラス PIMA 非アクティブ化アイコン](./media/user-guide/usbx-events/image130.png)

**説明**

USBX ホスト クラス PIMA 非アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-device-info-get"></a>ホスト クラス PIMA デバイス情報取得 

#### <a name="ux_host_class_pima_device_info_get"></a>ux_host_class_pima_device_info_get

**アイコン** ![ホスト クラス PIMA デバイス情報取得アイコン](./media/user-guide/usbx-events/image131.png)

**説明**

USBX ホスト クラス PIMA デバイス情報取得イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: PIMA デバイス。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-device-reset"></a>ホスト クラス PIMA デバイス リセット 

#### <a name="ux_host_class_pima_device_reset"></a>ux_host_class_pima_device_reset

**アイコン** ![ホスト クラス PIMA デバイス リセット アイコン](./media/user-guide/usbx-events/image132.png)

**説明**

USBX ホスト クラス PIMA デバイス リセット イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-notification"></a>ホスト クラス PIMA 通知 

#### <a name="ux_host_class_pima_notification"></a>ux_host_class_pima_notification

**アイコン** ![ホスト クラス PIMA 通知アイコン](./media/user-guide/usbx-events/image133.png)

**説明**

USBX ホスト クラス PIMA 通知イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。 情報フィールド 2: イベント コード。
- 情報フィールド 3: トランザクション ID。
- 情報フィールド 4: パラメーター 1。

### <a name="host-class-pima-number-objects-get"></a>ホスト クラス PIMA オブジェクト数取得 

#### <a name="ux_host_class_pima_number_objects_get"></a>ux_host_class_pima_number_objects_get

**アイコン** ![ホスト クラス PIMA オブジェクト数取得アイコン](./media/user-guide/usbx-events/image134.png)

**説明**

USBX ホスト クラス PIMA オブジェクト数取得イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-object-close"></a>ホスト クラス PIMA オブジェクト クローズ 

#### <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

**アイコン** ![ホスト クラス PIMA オブジェクト クローズ アイコン](./media/user-guide/usbx-events/image135.png)

**説明**

USBX ホスト クラス PIMA オブジェクト クローズ イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オブジェクト。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-object-copy"></a>ホスト クラス PIMA オブジェクト コピー 

#### <a name="ux_host_class_pima_object_copy"></a>ux_host_class_pima_object_copy

**アイコン** ![ホスト クラス PIMA オブジェクト コピー アイコン](./media/user-guide/usbx-events/image136.png)

**説明**

USBX ホスト クラス PIMA オブジェクト コピー イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オブジェクトのハンドル。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-object-delete"></a>ホスト クラス PIMA オブジェクト削除 

#### <a name="ux_host_class_pima_object_delete"></a>ux_host_class_pima_object_delete

**アイコン** ![ホスト クラス PIMA オブジェクト削除アイコン](./media/user-guide/usbx-events/image137.png)

**説明**

USBX ホスト クラス PIMA オブジェクト削除イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オブジェクトのハンドル。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-object-get"></a>ホスト クラス PIMA オブジェクト取得 

#### <a name="ux_host_class_pima_object_get"></a>ux_host_class_pima_object_get

**アイコン** ![ホスト クラス PIMA オブジェクト取得アイコン](./media/user-guide/usbx-events/image138.png)

**説明**

nx_rarp_info_get で RARP 情報を取得するイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オブジェクトのハンドル。
- 情報フィールド 3: オブジェクト。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-object-info-get"></a>ホスト クラス PIMA オブジェクト情報取得 

#### <a name="ux_host_class_pima_object_info_get"></a>ux_host_class_pima_object_info_get

**アイコン** ![ホスト クラス PIMA オブジェクト情報取得アイコン](./media/user-guide/usbx-events/image139.png)

**説明**

USBX ホスト クラス PIMA オブジェクト情報取得イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オブジェクトのハンドル。
- 情報フィールド 3: オブジェクト。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-object-info-send"></a>ホスト クラス PIMA オブジェクト情報送信 

#### <a name="ux_host_class_pima_object_info_send"></a>ux_host_class_pima_object_info_send

**アイコン** ![ホスト クラス PIMA オブジェクト情報送信アイコン](./media/user-guide/usbx-events/image140.png)

**説明**

USBX ホスト クラス PIMA オブジェクト情報送信イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オブジェクト。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-object-move"></a>ホスト クラス PIMA オブジェクト移動 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**アイコン** ![ホスト クラス PIMA オブジェクト移動アイコン](./media/user-guide/usbx-events/image141.png)

**説明**

USBX ホスト クラス PIMA オブジェクト移動イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オブジェクトのハンドル。
- 情報フィールド 3: オブジェクト。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-object-send"></a>ホスト クラス PIMA オブジェクト送信 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**アイコン** ![ホスト クラス PIMA オブジェクト送信アイコン](./media/user-guide/usbx-events/image142.png)

**説明**

USBX ホスト クラス PIMA オブジェクト送信イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オブジェクト。
- 情報フィールド 3: オブジェクトのバッファー。
- 情報フィールド 4: オブジェクトの長さ。

### <a name="host-class-pima-object-transfer-abort"></a>ホスト クラス PIMA オブジェクト転送アボート 

#### <a name="ux_host_class_pima_object_transfer_abort"></a>ux_host_class_pima_object_transfer_abort

**アイコン** ![ホスト クラス PIMA オブジェクト転送アボート アイコン](./media/user-guide/usbx-events/image143.png)

**説明**

USBX ホスト クラス PIMA オブジェクト転送アボート イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オブジェクトのハンドル。
- 情報フィールド 3: オブジェクト。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-read"></a>ホスト クラス PIMA 読み取り 

#### <a name="ux_host_class_pima_read"></a>ux_host_class_pima_read

**アイコン** ![ホスト クラス PIMA 読み取りアイコン](./media/user-guide/usbx-events/image144.png)

**説明**

USBX ホスト クラス PIMA 読み取りイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: データ ポインター。
- 情報フィールド 3: データの長さ。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-request-cancel"></a>ホスト クラス PIMA 要求取り消し 

#### <a name="ux_host_class_pima_request_cancel"></a>ux_host_class_pima_request_cancel

**アイコン** ![ホスト クラス PIMA 要求取り消しアイコン](./media/user-guide/usbx-events/image145.png)

**説明**

USBX ホスト クラス PIMA 要求取り消しイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-session-close"></a>ホスト クラス PIMA セッション終了 

#### <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

**アイコン** ![ホスト クラス PIMA セッション終了アイコン](./media/user-guide/usbx-events/image146.png)

**説明**

USBX ホスト クラス PIMA セッション終了イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: PIMA セッション。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-session-open"></a>ホスト クラス PIMA セッション開始 

#### <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

**アイコン** ![ホスト クラス PIMA セッション開始アイコン](./media/user-guide/usbx-events/image147.png)

**説明** USBX ホスト クラス PIMA セッション開始イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: PIMA セッション。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-storage-ids-get"></a>ホスト クラス PIMA ストレージ ID 取得 

#### <a name="ux_host_class_pima_session_ids_get"></a>ux_host_class_pima_session_ids_get

**アイコン** ![ホスト クラス PIMA ストレージ ID 取得アイコン](./media/user-guide/usbx-events/image148.png)

**説明**

USBX ホスト クラス PIMA ストレージ ID 取得イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: ストレージ ID の配列。
- 情報フィールド 3: ストレージ ID の長さ。
情報フィールド 4: 使用されません。

### <a name="host-class-pima-storage-info-get"></a>ホスト クラス PIMA ストレージ情報取得 

#### <a name="ux_host_class_pima_storage_info_get"></a>ux_host_class_pima_storage_info_get

**アイコン** ![ホスト クラス PIMA ストレージ情報取得アイコン](./media/user-guide/usbx-events/image149.png)

**説明**

USBX ホスト クラス PIMA ストレージ情報取得イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: ストレージ ID。
- 情報フィールド 3: ストレージ。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-thumb-get"></a>ホスト クラス PIMA Thumb 取得 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**アイコン** ![ホスト クラス PIMA Thumb 取得アイコン](./media/user-guide/usbx-events/image150.png)

**説明**

nx_tcp_server_socket_unaccept で TCP サーバーの接続を拒否するイベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: オブジェクトのハンドル。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-pima-write"></a>ホスト クラス PIMA 書き込み 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**アイコン** ![ホスト クラス PIMA 書き込みアイコン](./media/user-guide/usbx-events/image151.png)

**説明**

USBX ホスト クラス PIMA 書き込みイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: データ ポインター。
- 情報フィールド 3: データの長さ。
- 情報フィールド 4: 使用されません。

### <a name="host-class-printer-activate"></a>ホスト クラス Printer アクティブ化 

#### <a name="ux_host_class_printer_activate"></a>ux_host_class_printer_activate

**アイコン** ![ホスト クラス Printer アクティブ化アイコン](./media/user-guide/usbx-events/image152.png)

**説明**

USBX ホスト クラス Printer アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター。
- 情報フィールド 2: ソケットへのポインター。
- 情報フィールド 3: サービスの種類。
- 情報フィールド 4: 受信ウィンドウのサイズ。

### <a name="host-class-printer-deactivate"></a>ホスト クラス Printer 非アクティブ化 

#### <a name="ux_host_class_printer_deactivate"></a>ux_host_class_printer_deactivate

**アイコン** ![ホスト クラス Printer 非アクティブ化アイコン](./media/user-guide/usbx-events/image153.png)

**説明**

USBX ホスト クラス Printer 非アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-printer-name-get"></a>ホスト クラス Printer 名前取得 

#### <a name="ux_host_class_printer_name_get"></a>ux_host_class_printer_name_get

**アイコン** ![ホスト クラス Printer 名前取得アイコン](./media/user-guide/usbx-events/image154.png)

**説明**

USBX ホスト クラス Printer 名前取得イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-printer-read"></a>ホスト クラス Printer 読み取り 

#### <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

**アイコン** ![ホスト クラス Printer 読み取りアイコン](./media/user-guide/usbx-events/image155.png)

**説明**

USBX ホスト クラス Printer 読み取りイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: データ ポインター。
- 情報フィールド 3: 要求された長さ。
- 情報フィールド 4: 使用されません。

### <a name="host-class-printer-soft-reset"></a>ホスト クラス Printer ソフト リセット 

#### <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

**アイコン** ![ホスト クラス Printer ソフト リセット アイコン](./media/user-guide/usbx-events/image156.png)

**説明**

USBX ホスト クラス Printer ソフト リセット イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-printer-status-get"></a>ホスト クラス Printer 状態取得 

#### <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

**アイコン** ![ホスト クラス Printer 状態取得アイコン](./media/user-guide/usbx-events/image157.png)

**説明**

USBX ホスト クラス Printer 状態取得イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: プリンターの状態。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-printer-write"></a>ホスト クラス Printer 書き込み 

#### <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

**アイコン** ![ホスト クラス Printer 書き込みアイコン](./media/user-guide/usbx-events/image158.png)

**説明**

USBX ホスト クラス Printer 書き込みイベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: データ ポインター。
- 情報フィールド 3: 要求された長さ。
- 情報フィールド 4: 使用されません。

### <a name="host-class-prolific-activate"></a>ホスト クラス Prolific アクティブ化 

#### <a name="ux_host_class_prolific_activate"></a>ux_host_class_prolific_activate 

**アイコン** ![ホスト クラス Prolific アクティブ化アイコン](./media/user-guide/usbx-events/image159.png)

**説明**

USBX ホスト クラス Prolific アクティブ化イベントです。

**情報フィールド** 

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-prolific-deactivate"></a>ホスト クラス Prolific 非アクティブ化 

#### <a name="ux_host_class_prolific_deactivate"></a>ux_host_class_prolific_deactivate 

**アイコン** ![ホスト クラス Prolific 非アクティブ化アイコン](./media/user-guide/usbx-events/image160.png)

**説明**

USBX ホスト クラス Prolific 非アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-prolific-ioctl-abort-in-pipe"></a>ホスト クラス Prolific IOCTL 入力パイプ アボート 

#### <a name="ux_host_class_prolific_ioctl_abort_in_pipe"></a>ux_host_class_prolific_ioctl_abort_in_pipe

**アイコン** ![ホスト クラス Prolific IOCTL 入力パイプ アボート アイコン](./media/user-guide/usbx-events/image161.png)

**説明**

USBX ホスト クラス Prolific IOCTL 入力パイプ アボート イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: エンドポイント。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-prolific-ioctl-abort-out-pipe"></a>ホスト クラス Prolific IOCTL 出力パイプ アボート 

#### <a name="ux_host_class_prolific_ioctl_abort_out_pipe"></a>ux_host_class_prolific_ioctl_abort_out_pipe

**アイコン** ![ホスト クラス Prolific IOCTL 出力パイプ アボート アイコン](./media/user-guide/usbx-events/image162.png)

**説明**

USBX ホスト クラス Prolific IOCTL 出力パイプ アボート イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: エンドポイント。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-prolific-ioctl-get-device-status"></a>ホスト クラス Prolific IOCTL デバイス状態取得 

#### <a name="ux_host_class_prolific_ioctl_get_device_status"></a>ux_host_class_prolific_ioctl_get_device_status

**アイコン** ![ホスト クラス Prolific IOCTL デバイス状態取得アイコン](./media/user-guide/usbx-events/image163.png)

**説明**

USBX ホスト クラス Prolific IOCTL デバイス状態取得イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: デバイスの状態。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-prolific-ioctl-get-line-coding"></a>ホスト クラス Prolific IOCTL 伝送路符号化取得 

#### <a name="ux_host_class_prolific_ioctl_get_line_coding"></a>ux_host_class_prolific_ioctl_get_line_coding

**アイコン** ![ホスト クラス Prolific IOCTL 伝送路符号化取得アイコン](./media/user-guide/usbx-events/image164.png)

**説明**

USBX ホスト クラス Prolific IOCTL 伝送路符号化取得イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: パラメーター。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-prolific-ioctl-purge"></a>ホスト クラス Prolific IOCTL パージ 

#### <a name="ux_host_class_prolific_ioctl_purge"></a>ux_host_class_prolific_ioctl_purge

**アイコン** ![ホスト クラス Prolific IOCTL パージ アイコン](./media/user-guide/usbx-events/image165.png)

**説明**

USBX ホスト クラス Prolific IOCTL パージ イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: パラメーター。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-prolific-ioctl-report-device"></a>ホスト クラス Prolific IOCTL デバイス報告 

#### <a name="ux_host_class_prolific_ioctl_report_device"></a>ux_host_class_prolific_ioctl_report_device

**アイコン** ![ホスト クラス Prolific IOCTL デバイス報告アイコン](./media/user-guide/usbx-events/image166.png)

**説明**

USBX ホスト クラス Prolific IOCTL デバイス状態変更報告イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: パラメーター。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-prolific-ioctl-send-break"></a>ホスト クラス Prolific IOCTL ブレーク送信 

#### <a name="ux_host_class_prolific_ioctl_send_break"></a>ux_host_class_prolific_ioctl_send_break

**アイコン** ![ホスト クラス Prolific IOCTL ブレーク送信アイコン](./media/user-guide/usbx-events/image167.png)

**説明**

USBX ホスト クラス Prolific IOCTL ブレーク送信イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-prolific-ioctl-set-line-coding"></a>ホスト クラス Prolific IOCTL 伝送路符号化設定 

#### <a name="ux_host_class_prolific_ioctl_set_line_coding"></a>ux_host_class_prolific_ioctl_set_line_coding

**アイコン** ![ホスト クラス Prolific IOCTL 伝送路符号化設定アイコン](./media/user-guide/usbx-events/image168.png)

**説明**

USBX ホスト クラス Prolific IOCTL 伝送路符号化設定イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: パラメーター。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-prolific-ioctl-set-line-state"></a>ホスト クラス Prolific IOCTL 伝送路状態設定 

#### <a name="ux_host_class_prolific_ioctl_set_line_state"></a>ux_host_class_prolific_ioctl_set_line_state

**アイコン** ![ホスト クラス Prolific IOCTL 伝送路状態設定アイコン](./media/user-guide/usbx-events/image169.png)

**説明**

USBX ホスト クラス Prolific IOCTL 伝送路状態設定イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: パラメーター。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-prolific-read"></a>ホスト クラス Prolific 読み取り 

#### <a name="ux_host_class_prolific_read"></a>ux_host_class_prolific_read

**アイコン** ![ホスト クラス Prolific 読み取りアイコン](./media/user-guide/usbx-events/image170.png)

**説明**

USBX ホスト クラス Prolific 読み取りイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: データ ポインター。
- 情報フィールド 3: 要求された長さ。
- 情報フィールド 4: 使用されません。

### <a name="host-class-prolific-reception-start"></a>ホスト クラス Prolific 受信開始 

#### <a name="ux_host_class_prolific_reception_start"></a>ux_host_class_prolific_reception_start

**アイコン** ![ホスト クラス Prolific 受信開始アイコン](./media/user-guide/usbx-events/image171.png)

**説明**

USBX ホスト クラス Prolific 受信開始イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-prolific-reception-stop"></a>ホスト クラス Prolific 受信停止 

#### <a name="ux_host_class_prolific_reception_stop"></a>ux_host_class_prolific_reception_stop

**アイコン** ![ホスト クラス Prolific 受信停止アイコン](./media/user-guide/usbx-events/image172.png)

**説明**

USBX ホスト クラス Prolific 受信停止イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-prolific-write"></a>ホスト クラス Prolific 書き込み 

#### <a name="ux_host_class_prolific_write"></a>ux_host_class_prolific_write

**アイコン** ![ホスト クラス Prolific 書き込みアイコン](./media/user-guide/usbx-events/image173.png)

**説明**

USBX ホスト クラス Prolific 書き込みイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: データ ポインター。
- 情報フィールド 3: 要求された長さ。
- 情報フィールド 4: 使用されません。

### <a name="host-class-storage-activate"></a>ホスト クラス Storage アクティブ化 

#### <a name="ux_host_class_storage_activate"></a>ux_host_class_storage_activate

**アイコン** ![ホスト クラス Storage アクティブ化アイコン](./media/user-guide/usbx-events/image174.png)

**説明**

USBX ホスト クラス Storage アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-storage-deactivate"></a>ホスト クラス Storage 非アクティブ化 

#### <a name="ux_host_class_storage_deactivate"></a>ux_host_class_storage_deactivate

**アイコン** ![ホスト クラス Storage 非アクティブ化アイコン](./media/user-guide/usbx-events/image175.png)

**説明**

USBX ホスト クラス Storage 非アクティブ化イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-storage-media-capacity-get"></a>ホスト クラス Storage メディア容量取得 

#### <a name="ux_host_class_storage_media_capacity_get"></a>ux_host_class_storage_media_capacity_get

**アイコン** ![ホスト クラス Storage メディア容量取得アイコン](./media/user-guide/usbx-events/image176.png)

**説明**

USBX ホスト クラス Storage メディア容量取得イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-storage-media-format-capacity-get"></a>ホスト クラス Storage メディア フォーマット容量取得

#### <a name="ux_host_class_storage_media_format_capacity_get"></a>ux_host_class_storage_media_format_capacity_get

**アイコン** ![ホスト クラス Storage メディア フォーマット容量取得アイコン](./media/user-guide/usbx-events/image177.png)

**説明**

USBX ホスト クラス Storage メディア フォーマット容量取得イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

#### <a name="host-class-storage-media-mount"></a>ホスト クラス Storage メディア マウント 

#### <a name="ux_host_class_storage_media_mount"></a>ux_host_class_storage_media_mount

**アイコン** ![ホスト クラス Storage メディア マウント アイコン](./media/user-guide/usbx-events/image178.png)

**説明**

USBX ホスト クラス Storage メディア マウント イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: セクター。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-storage-media-open"></a>ホスト クラス Storage メディア オープン 

#### <a name="ux_host_class_storage_media_open"></a>ux_host_class_storage_media_open

**アイコン** ![ホスト クラス Storage メディア オープン アイコン](./media/user-guide/usbx-events/image179.png)

**説明**

USBX ホスト クラス Storage メディア オープン イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: メディア。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-storage-media-read"></a>ホスト クラス Storage メディア読み取り 

#### <a name="ux_host_class_storage_media_read"></a>ux_host_class_storage_media_read

**アイコン** ![ホスト クラス Storage メディア読み取りアイコン](./media/user-guide/usbx-events/image180.png)

**説明**

USBX ホスト クラス Storage メディア読み取りイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: セクターの開始位置。
- 情報フィールド 3: セクター数。
- 情報フィールド 4: データ ポインター。

### <a name="host-class-storage-media-write"></a>ホスト クラス Storage メディア書き込み 

#### <a name="ux_host_class_storage_media_write"></a>ux_host_class_storage_media_write

**アイコン** ![ホスト クラス Storage メディア書き込みアイコン](./media/user-guide/usbx-events/image181.png)

**説明**

USBX ホスト クラス Storage メディア書き込みイベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: セクターの開始位置。
- 情報フィールド 3: セクター数。
- 情報フィールド 4: データ ポインター。

### <a name="host-class-storage-request-sense"></a>ホスト クラス Storage センス データ要求 

#### <a name="ux_host_class_storage_request_sense"></a>ux_host_class_storage_request_sense

**アイコン** ![ホスト クラス Storage センス データ要求アイコン](./media/user-guide/usbx-events/image182.png)

**説明**

USBX ホスト クラス Storage センス データ要求イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-storage-start-stop"></a>ホスト クラス Storage 開始/停止 

#### <a name="ux_host_class_storage_start_stop"></a>ux_host_class_storage_start_stop

**アイコン** ![ホスト クラス Storage 開始/停止アイコン](./media/user-guide/usbx-events/image183.png)

**説明**

USBX ホスト クラス Storage 開始/停止イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 開始/停止信号。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-class-storage-unit-ready-test"></a>ホスト クラス Storage ユニット準備状態テスト 

#### <a name="ux_host_class_storage_unit_ready_test"></a>ux_host_class_storage_unit_ready_test

**アイコン** ![ホスト クラス Storage ユニット準備状態テスト アイコン](./media/user-guide/usbx-events/image184.png)

**説明**

USBX ホスト クラス Storage ユニット準備状態テスト イベントです。

**情報フィールド**

- 情報フィールド 1: クラスのインスタンス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-class-instance-create"></a>ホスト スタック クラス インスタンス作成 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**アイコン** ![ホスト スタック クラス インスタンス作成アイコン](./media/user-guide/usbx-events/image185.png)

**説明**

USBX ホスト スタック クラス インスタンス作成イベントです。

**情報フィールド**

- 情報フィールド 1: クラス。
- 情報フィールド 2: クラスのインスタンス。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-class-instance-destroy"></a>ホスト スタック クラス インスタンス破棄 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**アイコン** ![ホスト スタック クラス インスタンス破棄アイコン](./media/user-guide/usbx-events/image186.png)

**説明**

USBX ホスト スタック クラス インスタンス破棄イベントです。

**情報フィールド**

- 情報フィールド 1: クラス。
- 情報フィールド 2: クラスのインスタンス。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-configuration-delete"></a>ホスト スタック構成削除 

#### <a name="ux_host_class_configuration_delete"></a>ux_host_class_configuration_delete

**アイコン** ![ホスト スタック構成削除アイコン](./media/user-guide/usbx-events/image187.png)

**説明**

USBX ホスト スタック構成削除イベントです。

**情報フィールド**

- 情報フィールド 1: 構成。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-configuration-enumerate"></a>ホスト スタック構成エニュメレーション 

#### <a name="ux_host_stack_configuration_enumerate"></a>ux_host_stack_configuration_enumerate

**アイコン** ![ホスト スタック構成エニュメレーション アイコン](./media/user-guide/usbx-events/image188.png)

**説明**

USBX ホスト スタック構成エニュメレーション イベントです。

**情報フィールド**

- 情報フィールド 1: デバイス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="stack-configuration-instance-create"></a>スタック構成インスタンス作成 

#### <a name="ux_host_stack_configuration_instance_create"></a>ux_host_stack_configuration_instance_create

**アイコン** ![スタック構成インスタンス作成アイコン](./media/user-guide/usbx-events/image189.png)

**説明**

USBX ホスト スタック構成インスタンス作成イベントです。

**情報フィールド**

- 情報フィールド 1: 構成。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-configuration-instance-delete"></a>ホスト スタック構成インスタンス削除 

#### <a name="ux_host_stack_configuration_instance_delete"></a>ux_host_stack_configuration_instance_delete

**アイコン** ![ホスト スタック構成インスタンス削除アイコン](./media/user-guide/usbx-events/image190.png)

**説明**

USBX ホスト スタック構成インスタンス削除イベントです。

**情報フィールド**

- 情報フィールド 1: 構成。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-configuration-set"></a>ホスト スタック構成設定 

#### <a name="ux_host_stack_configuration_set"></a>ux_host_stack_configuration_set

**アイコン** ![ホスト スタック構成設定アイコン](./media/user-guide/usbx-events/image191.png)

**説明**

USBX ホスト スタック構成設定イベントです。

**情報フィールド**

- 情報フィールド 1: 構成。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-device-address-set"></a>ホスト スタック デバイス アドレス設定 

#### <a name="ux_host_stack_device_address_set"></a>ux_host_stack_device_address_set

**アイコン** ![ホスト スタック デバイス アドレス設定アイコン](./media/user-guide/usbx-events/image192.png)

**説明**

USBX ホスト スタック デバイス アドレス設定イベントです。

**情報フィールド**

- 情報フィールド 1: デバイス。
- 情報フィールド 2: デバイスのアドレス。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-device-configuration-get"></a>ホスト スタック デバイス構成取得 

#### <a name="ux_host_stack_device_configuration_get"></a>ux_host_stack_device_configuration_get

**アイコン** ![ホスト スタック デバイス構成取得アイコン](./media/user-guide/usbx-events/image193.png)

**説明**

USBX ホスト スタック デバイス構成取得イベントです。

**情報フィールド**

- 情報フィールド 1: デバイス。
- 情報フィールド 2: 構成。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-device-configuration-select"></a>ホスト スタック デバイス構成選択 

#### <a name="ux_host_stack_device_configuration_select"></a>ux_host_stack_device_configuration_select

**アイコン** ![ホスト スタック デバイス構成選択アイコン](./media/user-guide/usbx-events/image194.png)

**説明**

USBX ホスト スタック デバイス構成選択イベントです。

**情報フィールド**

- 情報フィールド 1: デバイス。
- 情報フィールド 2: 構成。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-device-descriptor-read"></a>ホスト スタック デバイス記述子読み取り 

#### <a name="ux_host_stack_device_descriptor_read"></a>ux_host_stack_device_descriptor_read

**アイコン** ![ホスト スタック デバイス記述子読み取りアイコン](./media/user-guide/usbx-events/image195.png)

**説明**

USBX ホスト スタック デバイス記述子読み取りイベントです。

**情報フィールド**

- 情報フィールド 1: デバイス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-device-get"></a>ホスト スタック デバイス取得 

#### <a name="ux_host_stack_device_get"></a>ux_host_stack_device_get

**アイコン** ![ホスト スタック デバイス取得アイコン](./media/user-guide/usbx-events/image196.png)

**説明**

USBX ホスト スタック デバイス取得イベントです。

**情報フィールド**

- 情報フィールド 1: デバイスのインデックス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-device-remove"></a>ホスト スタック デバイス取り外し 

#### <a name="ux_host_stack_device_remove"></a>ux_host_stack_device_remove

**アイコン** ![ホスト スタック デバイス取り外しアイコン](./media/user-guide/usbx-events/image197.png)

**説明**

USBX ホスト スタック デバイス取り外しイベントです。

**情報フィールド**

- 情報フィールド 1: HCD。
- 情報フィールド 2: 親。
- 情報フィールド 3: ポートのインデックス。
- 情報フィールド 4: デバイス。

### <a name="host-stack-device-resource-free"></a>ホスト スタック デバイス リソース解放 

#### <a name="ux_host_stack_device_resource_free"></a>ux_host_stack_device_resource_free

**アイコン** ![ホスト スタック デバイス リソース解放アイコン](./media/user-guide/usbx-events/image198.png)

**説明**

USBX ホスト スタック デバイス リソース解放イベントです。

**情報フィールド**

- 情報フィールド 1: デバイス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-endpoint-instance-create"></a>ホスト スタック エンドポイント インスタンス作成 

#### <a name="ux_host_stack_endpoint_instance_create"></a>ux_host_stack_endpoint_instance_create

**アイコン** ![ホスト スタック エンドポイント インスタンス作成アイコン](./media/user-guide/usbx-events/image199.png)

**説明**

USBX ホスト スタック エンドポイント インスタンス作成イベントです。

**情報フィールド**

- 情報フィールド 1: デバイス。
- 情報フィールド 2: エンドポイント。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-endpoint-instance-delete"></a>ホスト スタック エンドポイント インスタンス削除 

#### <a name="ux_host_stack_endpoint_instance_delete"></a>ux_host_stack_endpoint_instance_delete

**アイコン](./media/user-guide/usbx-events/image200.png)** ホスト スタック エンドポイント インスタンス削除アイコン![

**説明**

USBX ホスト スタック エンドポイント インスタンス削除イベントです。

**情報フィールド**

- 情報フィールド 2: エンドポイント。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-endpoint-reset"></a>ホスト スタック エンドポイント リセット 

#### <a name="ux_host_stack_endpoint_reset"></a>ux_host_stack_endpoint_reset

**アイコン** ![ホスト スタック エンドポイント リセット アイコン](./media/user-guide/usbx-events/image201.png)

**説明**

USBX ホスト スタック エンドポイント リセット イベントです。

**情報フィールド**

- 情報フィールド 1: デバイス。
- 情報フィールド 2: エンドポイント。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-endpoint-transfer-abort"></a>ホスト スタック エンドポイント転送アボート 

#### <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

**アイコン** ![ホスト スタック エンドポイント転送アボート アイコン](./media/user-guide/usbx-events/image202.png)

**説明**

USBX ホスト スタック エンドポイント転送アボート イベントです。

**情報フィールド**

- 情報フィールド 1: エンドポイント。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-host-controller-register"></a>ホスト スタック ホスト コントローラー登録 

#### <a name="ux_host_stack_hcd_register"></a>ux_host_stack_hcd_register

**アイコン** ![ホスト スタック ホスト コントローラー登録アイコン](./media/user-guide/usbx-events/image203.png)

**説明**

USBX ホスト スタック ホスト コントローラー登録イベントです。

**情報フィールド**

- 情報フィールド 1: HCD 名。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-initialize"></a>ホスト スタック初期化 

#### <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

**アイコン** ![ホスト スタック初期化アイコン](./media/user-guide/usbx-events/image204.png)

**説明**

USBX ホスト スタック初期化イベントです。

**情報フィールド**

- 情報フィールド 1: 使用されません。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-interface-endpoint-get"></a>ホスト スタック インターフェイス エンドポイント取得 

#### <a name="interface_-tcp-retry-entry"></a>インターフェイス_ TCP エントリ再試行

**アイコン** ![ホスト スタック インターフェイス エンドポイント取得アイコン](./media/user-guide/usbx-events/image205.png)

**説明**

NetX の TCP 再試行イベントです。

**情報フィールド**

- 情報フィールド 1: インターフェイス。
- 情報フィールド 2: エンドポイントのインデックス。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-interface-instance-create"></a>ホスト スタック インターフェイス インスタンス作成 

#### <a name="ux_host_stack_interface_instance_create"></a>ux_host_stack_interface_instance_create

**アイコン** ![ホスト スタック インターフェイス インスタンス作成アイコン](./media/user-guide/usbx-events/image206.png)

**説明**

USBX ホスト スタック インターフェイス インスタンス作成イベントです。

**情報フィールド**

- 情報フィールド 1: インターフェイス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-interface-instance-delete"></a>ホスト スタック インターフェイス インスタンス削除 

#### <a name="ux_host_stack_interface_instance_delete"></a>ux_host_stack_interface_instance_delete

**アイコン** ![ホスト スタック インターフェイス インスタンス削除アイコン](./media/user-guide/usbx-events/image207.png)

**説明**

USBX ホスト スタック インターフェイス インスタンス削除イベントです。

**情報フィールド**

- 情報フィールド 1: インターフェイス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-interface-set"></a>ホスト スタック インターフェイス設定 

#### <a name="ux_host_stack_interface_set"></a>ux_host_stack_interface_set

**アイコン** ![ホスト スタック インターフェイス設定アイコン](./media/user-guide/usbx-events/image208.png)

**説明**

USBX ホスト スタック インターフェイス設定イベントです。

**情報フィールド**

- 情報フィールド 1: インターフェイス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-interface-setting-select"></a>ホスト スタック インターフェイス設定選択 

#### <a name="ux_host_stack_interface_setting_select"></a>ux_host_stack_interface_setting_select

**アイコン** ![ホスト スタック インターフェイス設定選択アイコン](./media/user-guide/usbx-events/image209.png)

**説明**

USBX ホスト スタック インターフェイス設定選択イベントです。

**情報フィールド**

- 情報フィールド 1: インターフェイス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-new-configuration-create"></a>ホスト スタック新規構成作成 

#### <a name="ux_host_stack_new_configuration_create"></a>ux_host_stack_new_configuration_create

**アイコン** ![ホスト スタック新規構成作成アイコン](./media/user-guide/usbx-events/image210.png)

**説明**
 
USBX ホスト スタック新規構成作成イベントです。

**情報フィールド**

- 情報フィールド 1: デバイス。
- 情報フィールド 2: 構成。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-new-device-create"></a>ホスト スタック新規デバイス作成 

#### <a name="ux_host_stack_new_device_create"></a>ux_host_stack_new_device_create

**アイコン** ![ホスト スタック新規デバイス作成アイコン](./media/user-guide/usbx-events/image211.png)

**説明**
 
 USBX ホスト スタック新規デバイス作成イベントです。

**情報フィールド**

- 情報フィールド 1: HCD。
- 情報フィールド 2: デバイスの所有者。
- 情報フィールド 3: ポートのインデックス。
- 情報フィールド 4: デバイス。

### <a name="host-stack-new-endpoint-create"></a>ホスト スタック新規エンドポイント作成 

#### <a name="ux_host_stack_new_endpoint_create"></a>ux_host_stack_new_endpoint_create

**アイコン** ![ホスト スタック新規エンドポイント作成アイコン](./media/user-guide/usbx-events/image212.png)

**説明**
 
USBX ホスト スタック新規エンドポイント作成イベントです。

**情報フィールド**

- 情報フィールド 1: インターフェイス。
- 情報フィールド 2: エンドポイント。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-root-hub-change-process"></a>ホスト スタック ルート ハブ変更処理 

#### <a name="ux_host_stack_rh_change_process"></a>ux_host_stack_rh_change_process

**アイコン** ![ホスト スタック ルート ハブ変更処理アイコン](./media/user-guide/usbx-events/image213.png)

**説明**
 
USBX ホスト スタック ルート ハブ変更処理イベントです。

**情報フィールド**

- 情報フィールド 1: ポートのインデックス。
- 情報フィールド 2: 使用されません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-root-hub-device-extraction"></a>ホスト スタック ルート ハブ デバイス抽出 

#### <a name="ux_host_stack_rh_device_extraction"></a>ux_host_stack_rh_device_extraction

**アイコン** ![ホスト スタック ルート ハブ デバイス抽出アイコン](./media/user-guide/usbx-events/image214.png)

**説明**

USBX ホスト スタック ルート ハブ デバイス抽出イベントです。

**情報フィールド**

- 情報フィールド 1: HCD。
- 情報フィールド 2: ポートのインデックス。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-root-hub-device-insertion"></a>ホスト スタック ルート ハブ デバイス挿入 

#### <a name="ux_host_stack_rh_device_insertion"></a>ux_host_stack_rh_device_insertion

**アイコン** ![ホスト スタック ルート ハブ デバイス挿入アイコン](./media/user-guide/usbx-events/image215.png)

**説明**

USBX ホスト スタック ルート ハブ デバイス挿入イベントです。

**情報フィールド**

- 情報フィールド 1: HCD。
- 情報フィールド 2: ポートのインデックス。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-transfer-request"></a>ホスト スタック転送要求 

#### <a name="ux_host_stack_transfer_request"></a>ux_host_stack_transfer_request

**アイコン** ![ホスト スタック転送要求アイコン](./media/user-guide/usbx-events/image216.png)

**説明**

USBX ホスト スタック転送要求イベントです。

**情報フィールド**

- 情報フィールド 1: デバイス。
- 情報フィールド 2: エンドポイント。
- 情報フィールド 3: 転送要求。
- 情報フィールド 4: 使用されません。

### <a name="host-stack-transfer-request-abort"></a>ホスト スタック転送要求アボート 

#### <a name="internal-io-driver-get-status"></a>内部 I/O ドライバー状態取得

**アイコン** ![ホスト スタック転送要求アボート アイコン](./media/user-guide/usbx-events/image217.png)

**説明**

USBX ホスト スタック転送要求アボート イベントです。

**情報フィールド**

- 情報フィールド 1: デバイス。
- 情報フィールド 2: エンドポイント。
- 情報フィールド 3: 転送要求。
- 情報フィールド 4: 使用されません。

### <a name="usbx-error"></a>USBX エラー 

#### <a name="ux_error"></a>ux_error

**アイコン** ![USBX エラー アイコン](./media/user-guide/usbx-events/image218.png)

**説明**

USBX エラー イベントです。

**情報フィールド**

- 情報フィールド 1: USBX エラー。
- 情報フィールド 2: エラー名。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されません。