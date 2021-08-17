---
title: 第 8 章 - Azure RTOS NetX トレース イベント
description: この章では、Azure RTOS NetX イベントについて説明します。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: f785b421ffc6d588080eb45a50dad949daf1ca6a9bf36770110f0450cd465bf1
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116805299"
---
# <a name="chapter-8---azure-rtos-netx-trace-events"></a>第 8 章 - Azure RTOS NetX トレース イベント

この章では、Azure RTOS NetX イベントについて説明します。 

## <a name="list-of-events-and-icons"></a>イベントとアイコンの一覧

次に、TraceX によって表示される NetX イベントの一覧を示します。

| アイコン                                           | 意味                 |
| -------------------------------- | ------------------------------------- |
| ![内部 A R P 要求の受信アイコン](./media/user-guide/netx-events/image1.png)    | 内部 ARP 要求の受信 |
| ![内部 A R P 要求の送信アイコン](./media/user-guide/netx-events/image2.png)    | 内部 ARP 要求の送信 |
| ![内部 A R P 応答の受信アイコン](./media/user-guide/netx-events/image3.png)    | 内部 ARP 応答の受信 |
| ![内部 A R P 応答の送信アイコン](./media/user-guide/netx-events/image4.png)    | 内部 ARP 応答の送信 |
| ![内部 I C M P 受信アイコン](./media/user-guide/netx-events/image5.png)    | 内部 ICMP 受信 |
| ![内部 I C M P 送信アイコン](./media/user-guide/netx-events/image6.png)    | 内部 ICMP 送信 |
| ![内部 NetX I G M P 受信アイコン](./media/user-guide/netx-events/image7.png)    | 内部 NetX IGMP 受信 |
| ![内部 I P 受信アイコン](./media/user-guide/netx-events/image8.png)    | 内部 IP 受信 |
| ![内部 I P 送信アイコン](./media/user-guide/netx-events/image9.png)    | 内部 IP 送信 |
| ![内部 T C P データ受信アイコン](./media/user-guide/netx-events/image10.png)    | 内部 TCP データ受信 |
| ![内部 T C P データ送信アイコン](./media/user-guide/netx-events/image11.png)    | 内部 TCP データ送信 |
| ![内部 T C P FIN 受信アイコン](./media/user-guide/netx-events/image12.png)    | 内部 TCP FIN 受信 |
| ![内部 T C P F I N 送信アイコン](./media/user-guide/netx-events/image13.png)    | 内部 TCP FIN 送信 |
| ![内部 T C P R S T 受信アイコン](./media/user-guide/netx-events/image14.png)    | 内部 TCP RST 受信 |
| ![内部 T C P R S T 送信アイコン](./media/user-guide/netx-events/image15.png)    | 内部 TCP RST 送信 |
| ![内部 T C P S Y N 受信アイコン](./media/user-guide/netx-events/image16.png)    | 内部 TCP SYN 受信 |
| ![内部 T C P S Y N 送信アイコン](./media/user-guide/netx-events/image17.png)    | 内部 TCP SYN 送信 |
| ![内部 U D P 受信アイコン](./media/user-guide/netx-events/image18.png)    | 内部 UDP 受信 |
| ![内部 U D P 送信アイコン](./media/user-guide/netx-events/image19.png)    | 内部 UDP 送信 |
| ![内部 R A R P 受信アイコン](./media/user-guide/netx-events/image20.png)    | 内部 RARP 受信 |
| ![内部 R A R P 送信アイコン](./media/user-guide/netx-events/image21.png)    | 内部 RARP 送信 |
| ![内部 T C P 再試行アイコン](./media/user-guide/netx-events/image22.png)    | 内部 TCP 再試行 |
| ![内部 T C P 状態の変更アイコン](./media/user-guide/netx-events/image23.png)    | 内部 TCP 状態の変更 |
| ![内部 I / O ドライバーのパケット送信アイコン](./media/user-guide/netx-events/image24.png)    | 内部 I/O ドライバーのパケット送信 |
| ![icon](./media/user-guide/netx-events/image25.png)    | 内部 I/O ドライバーの初期化 |
| ![内部 I / O ドライバーの初期化アイコン](./media/user-guide/netx-events/image26.png)    | 内部 I/O ドライバー リンクの有効化 |
| ![内部 I / O ドライバー リンクの無効化アイコン](./media/user-guide/netx-events/image27.png)    | 内部 I/O ドライバー リンクの無効化 |
| ![内部 I / O ドライバーのパケット ブロードキャスト アイコン](./media/user-guide/netx-events/image28.png)    | 内部 I/O ドライバーのパケット ブロードキャスト |
| ![内部 I / O ドライバーの ARP 送信アイコン](./media/user-guide/netx-events/image29.png)    | 内部 I/O ドライバーの ARP 送信 |
| ![内部 I / O ドライバーの ARP 応答の送信アイコン](./media/user-guide/netx-events/image30.png)    | 内部 I/O ドライバーの ARP 応答の送信 |
| ![内部 I / O ドライバーの RARP 送信アイコン](./media/user-guide/netx-events/image31.png)    | 内部 I/O ドライバーの RARP 送信 |
| ![内部 I / O ドライバーのマルチキャスト参加アイコン](./media/user-guide/netx-events/image32.png)    | 内部 I/O ドライバーのマルチキャスト参加 |
| ![内部 I / O ドライバーのマルチキャスト離脱アイコン](./media/user-guide/netx-events/image33.png)    | 内部 I/O ドライバーのマルチキャスト離脱 |
| ![内部 I / O ドライバーの状態取得アイコン](./media/user-guide/netx-events/image34.png)    | 内部 I/O ドライバーの状態取得 |
| ![内部 I / O ドライバーの速度取得アイコン](./media/user-guide/netx-events/image35.png)    | 内部 I/O ドライバーの速度取得 |
| ![内部 I / O ドライバーの二重タイプ取得アイコン](./media/user-guide/netx-events/image36.png)    | 内部 I/O ドライバーの二重タイプ取得 |
| ![内部 I / O ドライバーのエラー数取得アイコン](./media/user-guide/netx-events/image37.png)    | 内部 I/O ドライバーのエラー数取得 |
| ![内部 I / O ドライバーの RX 数取得アイコン](./media/user-guide/netx-events/image38.png)    | 内部 I/O ドライバーの RX 数取得 |
| ![内部 I / O ドライバーの TX 数取得アイコン](./media/user-guide/netx-events/image39.png)    | 内部 I/O ドライバーの TX 数取得 |
| ![内部 I / O ドライバーの割り当てエラー数の取得アイコン](./media/user-guide/netx-events/image40.png)    | 内部 I/O ドライバーの割り当てエラー数の取得 |
| ![内部 I / O ドライバーの初期化解除アイコン](./media/user-guide/netx-events/image41.png)    | 内部 I/O ドライバーの初期化解除 |
| ![内部 I / O ドライバーの遅延処理アイコン](./media/user-guide/netx-events/image42.png)    | 内部 I/O ドライバーの遅延処理 |
| ![A R P 動的エントリの無効化アイコン](./media/user-guide/netx-events/image43.png)    | **ARP 動的エントリの無効化** (*nx_arp_dynamic_entries_invalidate*) |
| ![A R P 動的エントリの設定アイコン](./media/user-guide/netx-events/image44.png)    | **ARP 動的エントリの設定** (*nx_arp_dynamic_entry_set*) |
| ![A R P 有効化アイコン](./media/user-guide/netx-events/image45.png)    | **ARP 有効化** (*nx_arp_enable*) |
| ![A R P Gratuitous 送信アイコン](./media/user-guide/netx-events/image46.png)    | **ARP Gratuitous 送信** (*nx_arp_gratuitous_send*) |
| ![A R P ハードウェア アドレス検索アイコン](./media/user-guide/netx-events/image47.png)    | **ARP ハードウェア アドレス検索** (*nx_arp_hardware_address_find*) |
| ![A R P 情報の取得アイコン](./media/user-guide/netx-events/image48.png)    | **ARP 情報の取得** (*nx_arp_info_get*) |
| ![A R P IP アドレス検索アイコン](./media/user-guide/netx-events/image49.png)    | **ARP IP アドレス検索** (*nx_arp_ip_address_find*) |
| ![A R P 静的エントリの作成アイコン](./media/user-guide/netx-events/image50.png)    | **ARP 静的エントリの作成** (*nx_arp_static_entry_create*) |
| ![A R P 静的エントリの削除アイコン](./media/user-guide/netx-events/image51.png)    | **ARP 静的エントリの削除** (*nx_arp_static_entries_delete*) |
| ![A R P 静的エントリの削除アイコン](./media/user-guide/netx-events/image52.png)    | **ARP 静的エントリの削除** (*nx_arp_static_entry_delete*) |
| ![Duo キャッシュ エントリの削除アイコン](./media/user-guide/netx-events/image53.png)    | **Duo キャッシュ エントリの削除** (*nxd_nd_cache_entry_delete*) |
| ![Duo キャッシュ エントリの設定アイコン](./media/user-guide/netx-events/image54.png)    | **Duo キャッシュ エントリの設定** (*nxd_nd_cache_entry_set*) |
| ![Duo キャッシュの無効化アイコン](./media/user-guide/netx-events/image55.png)    | **Duo キャッシュの無効化** (*nxd_nd_cache_invalidate*) |
| ![Duo キャッシュ I P アドレス検索アイコン](./media/user-guide/netx-events/image56.png)    | **Duo キャッシュ IP アドレス検索** (*nxd_nd_cache_ip_address_find*) |
| ![Duo I C M P の有効化アイコン](./media/user-guide/netx-events/image57.png)    | **Duo ICMP の有効化** (*nxd_icmp_enable*) |
| ![Duo I C M P I P v 6 ping アイコン](./media/user-guide/netx-events/image58.png)    | **Duo ICMP IPv6 ping** (*nxd_icmp_ping*) |
| ![Duo I P ペイロードの最大サイズの検索アイコン](./media/user-guide/netx-events/image59.png)    | **Duo IP ペイロードの最大サイズの検索** (*nx_max_payload_size_find*) |
| ![Duo I P 生パケット送信アイコン](./media/user-guide/netx-events/image60.png)    | **Duo IP 生パケット送信** (*nxd_ip_raw_packet_send*) |
| ![Duo I P v 6 既定ルーターの追加アイコン](./media/user-guide/netx-events/image61.png)    | **Duo IPv6 既定ルーターの追加** (*nxd_ipv6_default_router_add*) |
| ![Duo I P v 6 既定ルーターの削除アイコン](./media/user-guide/netx-events/image62.png)    | **Duo IPv6 既定ルーターの削除** (*nxd_ipv6_default_router_delete)* |
| ![Duo I P v 6 の有効化アイコン](./media/user-guide/netx-events/image63.png)    | **Duo IPv6 の有効化** (*nxd_ipv6_enable)* |
| ![Duo I P v 6 グローバル アドレスの取得アイコン](./media/user-guide/netx-events/image64.png)    | **Duo IPv6 グローバル アドレスの取得** (*nxd_ipv6_global_address_get*) |
| ![Duo I P v 6 グローバル アドレスの設定アイコン](./media/user-guide/netx-events/image65.png)    | **Duo IPv6 グローバル アドレスの設定** (*nxd_ipv6_global_address_set*) |
| ![Duo I P v 6 DAD プロセスの開始アイコン](./media/user-guide/netx-events/image66.png)    | **Duo IPv6 DAD プロセスの開始** (*nxd_ipv6_initiate_dad_process*) |
| ![Duo I P v 6 インターフェイス アドレスの取得アイコン](./media/user-guide/netx-events/image67.png)    | **Duo IPv6 インターフェイス アドレスの取得** (*nxd_ipv6_interface_address_get*) |
| ![Duo I P v 6 インターフェイス アドレスの設定アイコン](./media/user-guide/netx-events/image68.png)    | **Duo IPv6 インターフェイス アドレスの設定** (*nxd_ipv6_interface_address_set*) |
| ![Duo I P v 6 リンク ローカル アドレスの取得アイコン](./media/user-guide/netx-events/image69.png)    | **Duo IPv6 リンク ローカル アドレスの取得** (*nxd_ipv6_linklocal_address_get*) |
| ![Duo I P v 6 リンク ローカル アドレスの設定アイコン](./media/user-guide/netx-events/image70.png)    | **Duo IPv6 リンク ローカル アドレスの設定** (*nxd_ipv6_linklocal_address_set*) |
| ![Duo I P v 6 生パケットの送信アイコン](./media/user-guide/netx-events/image71.png)    | **Duo IPv6 生パケットの送信** (*nxd_ipv6_raw_packet_send)* |
| ![Duo T C P ソケット ピア情報の取得アイコン](./media/user-guide/netx-events/image72.png)    | **Duo TCP ソケット ピア情報の取得** (*nxd_tcp_socket_peer_info_get*) |
| ![Duo T C P ソケットの設定インターフェイス アイコン](./media/user-guide/netx-events/image73.png)    | **Duo TCP ソケットの設定インターフェイス** (*nxd_tcp_socket_set_interface*) |
| ![Duo U D P ソケット送信アイコン](./media/user-guide/netx-events/image74.png)    | **Duo UDP ソケット送信** (*nxd_udp_socket_send*) |
| ![Duo U D P ソケットの設定インターフェイス アイコン](./media/user-guide/netx-events/image75.png)    | **Duo UDP ソケットの設定インターフェイス** (*nxd_udp_socket_set_interface*) |
| ![Duo U D P ソース抽出アイコン](./media/user-guide/netx-events/image76.png)    | **Duo UDP ソース抽出** (*nxd_udp_source_extract*) |
| ![I C M P の有効化アイコン](./media/user-guide/netx-events/image77.png)    | **ICMP の有効化** (*nx_icmp_enable*) |
| ![I C M P 情報の取得アイコン](./media/user-guide/netx-events/image78.png)    | **ICMP 情報の取得** (*nx_icmp_info_get*) |
| ![I C M P ping アイコン](./media/user-guide/netx-events/image79.png)    | **ICMP ping** (*nx_icmp_ping*) |
| ![I G M P の有効化アイコン](./media/user-guide/netx-events/image80.png)    | **IGMP の有効化** (*nx_igmp_enable*) |
| ![I G M P 情報の取得アイコン](./media/user-guide/netx-events/image81.png)    | **IGMP 情報の取得** (*nx_igmp_info_get*) |
| ![I G M P ループバックの無効化アイコン](./media/user-guide/netx-events/image82.png)    | **IGMP ループバックの無効化** (*nx_igmp_loopback_disable*) |
| ![I G M P ループバックの有効化アイコン](./media/user-guide/netx-events/image83.png)    | **IGMP ループバックの有効化** (*nx_igmp_loopback_enable*) |
| ![I G M P マルチキャスト参加アイコン](./media/user-guide/netx-events/image84.png)    | **IGMP マルチキャスト参加** (*nx_igmp_multicast_join*) |
| ![I G M P マルチキャスト離脱アイコン](./media/user-guide/netx-events/image85.png)    | **IGMP マルチキャスト離脱** (*nx_igmp_multicast_leave*) |
| ![I P アドレス変更通知アイコン](./media/user-guide/netx-events/image86.png)    | **IP アドレス変更通知** (*nx_ip_address_change_notify*) |
| ![I P アドレス取得アイコン](./media/user-guide/netx-events/image87.png)    | **IP アドレスの取得** (*nx_ip_address_get*) |
| ![I P アドレスの設定アイコン](./media/user-guide/netx-events/image88.png)    | **IP アドレスの設定** (*nx_ip_address_set*) |
| ![I P の作成アイコン](./media/user-guide/netx-events/image89.png)    | **IP の作成** (*nx_ip_create*) |
| ![I P の削除アイコン](./media/user-guide/netx-events/image90.png)    | **IP の削除** (*nx_ip_delete*) |
| ![I P ドライバーのダイレクト コマンド アイコン](./media/user-guide/netx-events/image91.png)    | **IP ドライバーのダイレクト コマンド** (*nx_ip_driver_direct_command*) |
| ![I P 転送の無効化アイコン](./media/user-guide/netx-events/image92.png)    | **IP 転送の無効化** (*nx_ip_forwarding_disable*) |
| ![I P 転送の有効化アイコン](./media/user-guide/netx-events/image93.png)    | **IP 転送の有効化** (*nx_ip_forwarding_enable*) |
| ![I P フラグメントの無効化アイコン](./media/user-guide/netx-events/image94.png)    | **IP フラグメントの無効化** (*nx_ip_fragment_disable*) |
| ![I P フラグメントの有効化アイコン](./media/user-guide/netx-events/image95.png)    | **IP フラグメントの有効化** (*nx_ip_fragment_enable*)  |
| ![I P ゲートウェイ アドレスの設定アイコン](./media/user-guide/netx-events/image96.png)    | **IP ゲートウェイ アドレスの設定** (*nx_ip_gateway_address_set*) |
| ![I P 情報の取得アイコン](./media/user-guide/netx-events/image97.png)    | **IP 情報の取得** (*nx_ip_info_get*) |
| ![I P インターフェイスのアタッチ アイコン](./media/user-guide/netx-events/image98.png)    | **IP インターフェイスのアタッチ** (*nx_ip_interface_attach*) |
| ![I P インターフェイス情報の取得アイコン](./media/user-guide/netx-events/image99.png)    | **IP インターフェイス情報の取得** (*nx_ip_interface_info_get*) |
| ![I P 生パケットの無効化アイコン](./media/user-guide/netx-events/image100.png)    | **IP 生パケットの無効化** (*nx_ip_raw_packet_disable*) |
| ![I P 生パケットの有効化アイコン](./media/user-guide/netx-events/image101.png)    | **IP 生パケットの有効化** (*nx_ip_raw_packet_enable*) |
| ![I P 生パケットの受信アイコン](./media/user-guide/netx-events/image102.png)    | **IP 生パケットの受信** (*nx_ip_raw_packet_receive*) |
| ![I P 生パケットの送信アイコン](./media/user-guide/netx-events/image103.png)    | **IP 生パケットの送信** (*nx_ip_raw_packet_send*) |
| ![I P 静的ルートの追加アイコン](./media/user-guide/netx-events/image104.png)    | **IP 静的ルートの追加** (*nx_ip_static_route_add*) |
| ![I P 静的ルートの削除アイコン](./media/user-guide/netx-events/image105.png)    | **IP 静的ルートの削除** (*nx_ip_static_route_delete)* |
| ![I P 状態チェック アイコン](./media/user-guide/netx-events/image106.png)    | **IP 状態チェック** (*nx_ip_status_check*)|
| ![I P S E C の有効化アイコン](./media/user-guide/netx-events/image107.png)    | **IPSEC の有効化** (*nx_ipsec_enable)* |
| ![パケットの割り当てアイコン](./media/user-guide/netx-events/image108.png)    | **パケットの割り当て** (*nx_packet_allocate*) |
| ![パケット コピー アイコン](./media/user-guide/netx-events/image109.png)    | **パケット コピー** (*nx_packet_copy*) |
| ![パケット データの追加アイコン](./media/user-guide/netx-events/image110.png)    | **パケット データの追加** (*nx_packet_data_append*) |
| ![パケット データ抽出オフセット アイコン](./media/user-guide/netx-events/image111.png)    | **パケット データ抽出オフセット** (*nx_packet_data_extract_offset*) |
| ![パケット データ取得アイコン](./media/user-guide/netx-events/image112.png)    | **パケット データ取得** (*nx_packet_data_retrieve*) |
| ![パケット長の取得アイコン](./media/user-guide/netx-events/image113.png)    | **パケット長の取得** (*nx_packet_length_get*) |
| ![パケット プールの作成アイコン](./media/user-guide/netx-events/image114.png)    | **パケット プールの作成** (*nx_packet_pool_create*) |
| ![パケット プールの削除アイコン](./media/user-guide/netx-events/image115.png)    | **パケット プールの削除** (*nx_packet_pool_delete*) |
| ![パケット プール情報の取得アイコン](./media/user-guide/netx-events/image116.png)    | **パケット プール情報の取得** (*nx_packet_pool_info_get*) |
| ![パケット解放アイコン](./media/user-guide/netx-events/image117.png)    | **パケット解放** (*nx_packet_release*) |
| ![パケット送信解放アイコン](./media/user-guide/netx-events/image118.png)    | **パケット送信解放** (*nx_packet_transmit_release*) |
| ![R A R P の無効化アイコン](./media/user-guide/netx-events/image119.png)    | **RARP の無効化** (*nx_rarp_disable*) |
| ![R A R P の有効化アイコン](./media/user-guide/netx-events/image120.png)    | **RARP の有効化** (*nx_rarp_enable*) |
| ![R A R P 情報の取得アイコン](./media/user-guide/netx-events/image121.png)    | **RARP 情報の取得** (*nx_rarp_info_get*) |
| ![システム初期化アイコン](./media/user-guide/netx-events/image122.png)    | **システム初期化** (*nx_system_initialize*) |
| ![T C P クライアント ソケット バインド アイコン](./media/user-guide/netx-events/image123.png)    | **TCP クライアント ソケット バインド** (*nx_tcp_client_socket_bind*) |
| ![T C P クライアント ソケット接続アイコン](./media/user-guide/netx-events/image124.png)    | **TCP クライアント ソケット接続** (*nx_tcp_client_socket_connect*) |
| ![T C P クライアント ソケット ポートの取得アイコン](./media/user-guide/netx-events/image125.png)    | **TCP クライアント ソケット ポートの取得** (*nx_tcp_client_socket_port_get*) |
| ![T C P クライアント ソケットのバインド解除アイコン](./media/user-guide/netx-events/image126.png)    | **TCP クライアント ソケットのバインド解除** (*nx_tcp_client_socket_unbind*) |
| ![T C P の有効化アイコン](./media/user-guide/netx-events/image127.png)    | **TCP の有効化** (*nx_tcp_enable*) |
| ![T C P 空きポートの検索アイコン](./media/user-guide/netx-events/image128.png)    | **TCP 空きポートの検索** (*nx_tcp_free_port_find*) |
| ![T C P 情報の取得アイコン](./media/user-guide/netx-events/image129.png)    | **TCP 情報の取得** (*nx_tcp_info_get*) |
| ![T C P サーバー ソケットの受け入れアイコン](./media/user-guide/netx-events/image130.png)    | **TCP サーバー ソケットの受け入れ** (*nx_tcp_server_socket_accept*) |
| ![T C P サーバー ソケットのリッスン アイコン](./media/user-guide/netx-events/image131.png)    | **TCP サーバー ソケットのリッスン** (*nx_tcp_server_socket_listen*) |
| ![T C P サーバー ソケットの再リッスン アイコン](./media/user-guide/netx-events/image132.png)    | **TCP サーバー ソケットの再リッスン** (*nx_tcp_server_socket_relisten*) |
| ![T C P サーバー ソケットの受け入れ解除アイコン](./media/user-guide/netx-events/image133.png)    | **TCP サーバー ソケットの受け入れ解除** (*nx_tcp_server_socket_unaccept*) |
| ![T C P サーバー ソケットのリッスン解除アイコン](./media/user-guide/netx-events/image134.png)    | **TCP サーバー ソケットのリッスン解除** (*nx_tcp_server_socket_unlisten*) |
| ![使用可能な T C P ソケット バイト数アイコン](./media/user-guide/netx-events/image135.png)    | **使用可能な TCP ソケット バイト数** (*nx_tcp_socket_bytes_available*) |
| ![T C P ソケットの作成アイコン](./media/user-guide/netx-events/image136.png)    | **TCP ソケットの作成** (*nx_tcp_socket_create*) |
| ![T C P ソケットの削除アイコン](./media/user-guide/netx-events/image137.png)    | **TCP ソケットの削除** (*nx_tcp_socket_delete*) |
| ![T C P ソケットの切断アイコン](./media/user-guide/netx-events/image138.png)    | **TCP ソケットの切断** (*nx_tcp_socket_disconnect*) |
| ![T C P ソケット情報の取得アイコン](./media/user-guide/netx-events/image139.png)    | **TCP ソケット情報の取得** (*nx_tcp_socket_info_get*) |
| ![T C P ソケット MSS の取得アイコン](./media/user-guide/netx-events/image140.png)    | **TCP ソケット MSS の取得** (*nx_tcp_socket_mss_get*) |
| ![T C P ソケット MSS ピアの取得アイコン](./media/user-guide/netx-events/image141.png)    | **TCP ソケット MSS ピアの取得** (*nx_tcp_socket_mss_peer_get*) |
| ![T C P ソケット MSS の設定アイコン](./media/user-guide/netx-events/image142.png)    | **TCP ソケット MSS の設定** (*nx_tcp_socket_mss_set*) |
| ![T C P ソケット ピア情報の取得アイコン](./media/user-guide/netx-events/image143.png)    | **TCP ソケット ピア情報の取得** (*nx_tcp_socket_peer_info_get*) |
| ![T C P ソケット受信アイコン](./media/user-guide/netx-events/image144.png)    | **TCP ソケット受信** (*nx_tcp_socket_receive*) |
| ![T C P ソケット受信通知アイコン](./media/user-guide/netx-events/image145.png)    | **TCP ソケット受信通知** (*nx_tcp_socket_receive_notify*) |
| ![T C P ソケット送信アイコン](./media/user-guide/netx-events/image146.png)    | **TCP ソケット送信** (*nx_tcp_socket_send*) |
| ![T C P ソケット状態待機アイコン](./media/user-guide/netx-events/image147.png)    | **TCP ソケット状態待機** (*nx_tcp_socket_state_wait*) |
| ![T C P ソケット送信の構成アイコン](./media/user-guide/netx-events/image148.png)    | **TCP ソケット送信の構成** (*nx_tcp_socket_transmit_configure*) |
| ![T C P ソケット ウィンドウ更新通知の設定アイコン](./media/user-guide/netx-events/image149.png)    | **TCP ソケット ウィンドウ更新通知の設定** (*nx_tcp_socket_window_update_notify_set*)  |
| ![U D P の有効化アイコン](./media/user-guide/netx-events/image150.png)    | **UDP の有効化** (*nx_udp_enable*) |
| ![U D P 空きポートの検索アイコン](./media/user-guide/netx-events/image151.png)    | **UDP 空きポートの検索** (*nx_udp_free_port_find*) |
| ![U D P 情報の取得アイコン](./media/user-guide/netx-events/image152.png)    | **UDP 情報の取得** (*nx_udp_info_get*) |
| ![U D P ソケット バインド アイコン](./media/user-guide/netx-events/image153.png)    | **UDP ソケット バインド** (*nx_udp_socket_bind*) |
| ![使用可能な U D P ソケット バイト数アイコン](./media/user-guide/netx-events/image154.png)    | **使用可能な UDP ソケット バイト数** (*nx_udp_socket_bytes_available*) |
| ![U D P ソケット チェックサムの無効化アイコン](./media/user-guide/netx-events/image155.png)    | **UDP ソケット チェックサムの無効化** (*nx_udp_socket_checksum_disable*) |
| ![U D P ソケット チェックサムの有効化アイコン](./media/user-guide/netx-events/image156.png)    | **UDP ソケット チェックサムの有効化** (*nx_udp_socket_checksum_disable*) |
| ![U D P ソケットの作成アイコン](./media/user-guide/netx-events/image157.png)    | **UDP ソケットの作成** (*nx_udp_socket_create*) |
| ![U D P ソケットの削除アイコン](./media/user-guide/netx-events/image158.png)    | **UDP ソケットの削除** (*nx_udp_socket_delete*) |
| ![U D ソケット情報の取得アイコン](./media/user-guide/netx-events/image159.png)    | **UDP ソケット情報の取得** (*nx_udp_socket_info_get*) |
| ![U D P ソケット インターフェイスの設定アイコン](./media/user-guide/netx-events/image160.png)    | **UDP ソケット インターフェイスの設定** (*nx_udp_socket_interface_set*) |
| ![U D P ソケット ポートの取得アイコン](./media/user-guide/netx-events/image161.png)    | **UDP ソケット ポートの取得** (*nx_udp_socket_port_get*) |
| ![U D P ソケット受信アイコン](./media/user-guide/netx-events/image162.png)    | **UDP ソケット受信** (*nx_udp_socket_receive*) |
| ![U D P ソケット受信通知アイコン](./media/user-guide/netx-events/image163.png)    | **UDP ソケット受信通知** (*nx_udp_socket_receive_notify*) |
| ![U D P ソケット送信アイコン](./media/user-guide/netx-events/image164.png)    | **UDP ソケット送信** (*nx_udp_socket_send*) |
| ![U D P ソケットのバインド解除アイコン](./media/user-guide/netx-events/image165.png)    | **UDP ソケットのバインド解除** (*nx_udp_socket_unbind*) |
| ![U D P ソース抽出アイコン](./media/user-guide/netx-events/image166.png)    | **UDP ソース抽出** (*nx_udp_source_extract*) |

## <a name="event-descriptions"></a>イベントの説明

次のページでは、NetX トレース イベントについて説明します。

### <a name="internal-arp-request-receive"></a>内部 ARP 要求の受信 

#### <a name="internal-arp-request-receive"></a>内部 ARP 要求の受信

**アイコン** ![内部 ARP 要求の受信アイコン](./media/user-guide/netx-events/image1.png)

**説明**

このイベントは、内部 NetX ARP 要求の受信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 送信元 IP アドレス
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: 使用されていません

### <a name="internal-arp-request-send"></a>内部 ARP 要求の送信 

#### <a name="internal-arp-request-send"></a>内部 ARP 要求の送信

**アイコン** ![内部 ARP 要求の送信アイコン](./media/user-guide/netx-events/image2.png)

**説明**

このイベントは、内部 NetX ARP 要求の送信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 宛先 IP アドレス
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: 使用されていません

### <a name="internal-arp-response-receive"></a>内部 ARP 応答の受信 

#### <a name="internal-arp-request-receive"></a>内部 ARP 要求の受信

**アイコン** ![内部 ARP 要求の受信アイコン](./media/user-guide/netx-events/image3.png)

**説明**

このイベントは、内部 NetX ARP 応答の受信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 送信元 IP アドレス
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: 使用されていません

### <a name="internal-arp-response-send"></a>内部 ARP 応答の送信 

#### <a name="internal-arp-request-send"></a>内部 ARP 要求の送信

**アイコン** ![内部 ARP 要求の送信アイコン](./media/user-guide/netx-events/image4.png)

**説明**

このイベントは、内部 NetX 応答の送信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 宛先 IP アドレス
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: 使用されていません

### <a name="internal-icmp-receive"></a>内部 ICMP 受信 

#### <a name="internal-icmp-receive"></a>内部 ICMP 受信

**アイコン** ![内部 I C M P 受信アイコン](./media/user-guide/netx-events/image5.png)

**説明**

このイベントは、内部 NetX ICMP 受信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 送信元 IP アドレス
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: ICMP ヘッダーのワード 0

### <a name="internal-icmp-send"></a>内部 ICMP 送信 

#### <a name="internal-icmp-send"></a>内部 ICMP 送信

**アイコン** ![内部 I C M P 送信アイコン](./media/user-guide/netx-events/image6.png)

**説明**

このイベントは、内部 NetX ICMP 送信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 宛先 IP アドレス
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: ICMP ヘッダーのワード 0

### <a name="internal-igmp-receive"></a>内部 IGMP 受信 

#### <a name="internal-igmp-receive"></a>内部 IGMP 受信

**アイコン** ![内部 I G M P 受信アイコン](./media/user-guide/netx-events/image7.png)

**説明**

このイベントは、内部 NetX IGMP 受信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP ポインター
- 情報フィールド 2: 送信元 IP アドレス
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: IGMP ヘッダーのワード 0

### <a name="internal-ip-receive"></a>内部 IP 受信 

#### <a name="internal-ip-receive"></a>内部 IP 受信

**アイコン** ![内部 I P 受信アイコン](./media/user-guide/netx-events/image8.png)

**説明**

このイベントは、内部 NetX の IP 受信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 送信元 IP アドレス
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: パケット長

### <a name="internal-ip-send"></a>内部 IP 送信

#### <a name="internal-ip-send"></a>内部 IP 送信

**アイコン** ![内部 I P 送信アイコン](./media/user-guide/netx-events/image9.png)

**説明**

このイベントは、内部 NetX IP 送信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 宛先 IP アドレス
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: パケット長

### <a name="internal-tcp-data-receive"></a>内部 TCP データ受信 

#### <a name="internal-tcp-data-receive"></a>内部 TCP データ受信

**アイコン** ![内部 T C P データ受信アイコン](./media/user-guide/netx-events/image10.png)

**説明**

このイベントは、内部 NetX TCP データ受信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 送信元 IP アドレス
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: 受信シーケンス番号

### <a name="internal-tcp-data-send"></a>内部 TCP データ送信 

#### <a name="internal-tcp-data-send"></a>内部 TCP データ送信

**アイコン** ![内部 T C P データ送信アイコン](./media/user-guide/netx-events/image11.png)

**説明**

このイベントは、内部 NetX TCP データ送信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: 転送シーケンス番号

### <a name="internal-tcp-fin-receive"></a>内部 TCP FIN 受信 

#### <a name="internal-tcp-fin-receive"></a>内部 TCP FIN 受信

**アイコン** ![内部 T C P F I N 受信アイコン](./media/user-guide/netx-events/image12.png)

**説明**

このイベントは、内部 NetX TCP FIN 受信イベントを表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: 受信シーケンス番号

### <a name="internal-tcp-fin-send"></a>内部 TCP FIN 送信 

#### <a name="internal-tcp-fin-send"></a>内部 TCP FIN 送信

**アイコン** ![内部 T C P F I N 送信アイコン](./media/user-guide/netx-events/image13.png)

**説明**

このイベントは、内部 NetX TCP FIN 送信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: 転送シーケンス番号

### <a name="internal-tcp-rst-receive"></a>内部 TCP RST 受信 

#### <a name="internal-tcp-rst-receive"></a>内部 TCP RST 受信

**アイコン** ![内部 T C P R S T 受信アイコン](./media/user-guide/netx-events/image14.png)

**説明**

このイベントは、内部 NetX TCP リセット受信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター。
- 情報フィールド 2: ソケットへのポインター。
- 情報フィールド 3: パケットへのポインター。
- 情報フィールド 4: 受信シーケンス番号。

### <a name="internal-tcp-rst-send"></a>内部 TCP RST 送信 

#### <a name="internal-tcp-rst-send"></a>内部 TCP RST 送信

**アイコン** ![内部 T C P R S T 送信アイコン](./media/user-guide/netx-events/image15.png)

**説明**

このイベントは、内部 NetX TCP リセット送信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: 転送シーケンス番号

### <a name="internal-tcp-syn-receive"></a>内部 TCP SYN 受信 

#### <a name="internal-tcp-syn-receive"></a>内部 TCP SYN 受信

**アイコン** ![内部 T C P S Y N 受信アイコン](./media/user-guide/netx-events/image16.png)

**説明**

このイベントは、内部 NetX TCP SYN 受信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: 受信シーケンス番号

### <a name="internal-tcp-syn-send"></a>内部 TCP SYN 送信 

#### <a name="internal-tcp-syn-send"></a>内部 TCP SYN 送信

**アイコン** ![内部 T C P S Y N 送信アイコン](./media/user-guide/netx-events/image17.png)

**説明**

このイベントは、内部 NetX TCP SYN 送信イベントを表します。

情報フィールド 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: パケットへのポインター - 情報フィールド 4: 転送シーケンス番号

### <a name="internal-udp-receive"></a>内部 UDP 受信 

#### <a name="internal-udp-receive"></a>内部 UDP 受信

**アイコン** ![内部 U D P 受信アイコン](./media/user-guide/netx-events/image18.png)

**説明**

このイベントは、内部 NetX UDP 受信イベントを表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: UDP ヘッダーのワード 0

### <a name="internal-udp-send"></a>内部 UDP 送信 

#### <a name="internal-udp-send"></a>内部 UDP 送信

**アイコン** ![内部 U D P 送信アイコン](./media/user-guide/netx-events/image19.png)

**説明**

このイベントは、内部 NetX UDP 送信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: UDP ヘッダーのワード 0

### <a name="internal-rarp-receive"></a>内部 RARP 受信 

#### <a name="internal-rarp-receive"></a>内部 RARP 受信 

**アイコン** ![内部 R A R P 受信アイコン](./media/user-guide/netx-events/image20.png)

**説明**

このイベントは、内部 NetX RARP 受信イベントを表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ターゲット IP アドレス
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: RARP ヘッダーのワード 1

### <a name="internal-rarp-send"></a>内部 RARP 送信 

#### <a name="internal-rarp-send"></a>内部 RARP 送信 

**アイコン** ![内部 R A R P 送信アイコン](./media/user-guide/netx-events/image21.png)

**説明**

このイベントは、内部 NetX RARP 送信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ターゲット IP アドレス
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: RARP ヘッダーのワード 1

### <a name="internal-tcp-retry"></a>内部 TCP 再試行 

#### <a name="internal-tcp-retry"></a>内部 TCP 再試行 

**アイコン** ![内部 T C P 再試行アイコン](./media/user-guide/netx-events/image22.png)

**説明**

NetX の TCP 再試行イベントです。

**情報フィールド**
- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: パケットへのポインター
- 情報フィールド 4: 再試行回数

### <a name="internal-tcp-state-change"></a>内部 TCP 状態の変更 

#### <a name="internal-tcp-state-change"></a>内部 TCP 状態の変更 

**アイコン** ![内部 T C P 状態の変更アイコン](./media/user-guide/netx-events/image23.png)

**説明**

このイベントは、内部 NetX TCP ソケットの状態変更イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: 以前の状態
- 情報フィールド 4: 新しい状態

### <a name="internal-io-driver-packet-send"></a>内部 I/O ドライバーのパケット送信 

#### <a name="internal-io-driver-packet-send"></a>内部 I/O ドライバーのパケット送信

**アイコン** ![内部 I / O ドライバーのパケット送信アイコン](./media/user-guide/netx-events/image24.png)

**説明**

このイベントは、内部 NetX I/O ドライバーのパケット送信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: パケットへのポインター
- 情報フィールド 3: パケット サイズ
- 情報フィールド 4: 使用されていません

### <a name="internal-io-driver-initialize"></a>内部 I/O ドライバーの初期化 

#### <a name="internal-io-driver-initialize"></a>内部 I/O ドライバーの初期化

**アイコン** ![内部 I / O ドライバーの初期化アイコン](./media/user-guide/netx-events/image25.png)

**説明**

このイベントは、内部 NetX I/O ドライバーの初期化イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="internal-io-driver-link-enable"></a>内部 I/O ドライバー リンクの有効化 

#### <a name="internal-io-driver-link-enable"></a>内部 I/O ドライバー リンクの有効化

**アイコン** ![内部 I / O ドライバー リンクの有効化アイコン](./media/user-guide/netx-events/image26.png)

**説明**

このイベントは、内部 NetX I/O ドライバー リンクの有効化イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター。
- 情報フィールド 2: 使用されていません。
- 情報フィールド 3: 使用されません。
- 情報フィールド 4: 使用されていません。

### <a name="internal-io-driver-link-disable"></a>内部 I/O ドライバー リンクの無効化 

#### <a name="internal-io-driver-link-disable"></a>内部 I/O ドライバー リンクの無効化

**アイコン** ![内部 I / O ドライバー リンクの無効化アイコン](./media/user-guide/netx-events/image27.png)

**説明**

このイベントは、内部 NetX I/O ドライバー リンクの無効化イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="internal-io-driver-packet-broadcast"></a>内部 I/O ドライバーのパケット ブロードキャスト 

#### <a name="internal-io-driver-packet-broadcast"></a>内部 I/O ドライバーのパケット ブロードキャスト

**アイコン** ![内部 I / O ドライバーのパケット ブロードキャスト アイコン](./media/user-guide/netx-events/image28.png)

**説明**

このイベントは、内部 NetX I/O ドライバーのパケット ブロードキャスト イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: パケットへのポインター
- 情報フィールド 3: パケット サイズ
- 情報フィールド 4: 使用されていません

### <a name="internal-io-driver-arp-send"></a>内部 I/O ドライバーの ARP 送信 

#### <a name="internal-io-driver-arp-send"></a>内部 I/O ドライバーの ARP 送信

**アイコン** ![内部 I / O ドライバーの ARP 送信アイコン](./media/user-guide/netx-events/image29.png)

**説明**

このイベントは、内部 NetX I/O ドライバーの ARP 送信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: パケットへのポインター
- 情報フィールド 3: パケット サイズ
- 情報フィールド 4: 使用されていません

### <a name="internal-io-driver-arp-response-send"></a>内部 I/O ドライバーの ARP 応答の送信 

#### <a name="internal-io-driver-arp-response-send"></a>内部 I/O ドライバーの ARP 応答の送信

**アイコン** ![内部 I / O ドライバーの ARP 応答の送信アイコン](./media/user-guide/netx-events/image30.png)

**説明**

このイベントは、内部 NetX I/O ドライバーの ARP 応答送信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: パケットへのポインター
- 情報フィールド 3: パケット サイズ
- 情報フィールド 4: 使用されていません

### <a name="internal-io-driver-rarp-send"></a>内部 I/O ドライバーの RARP 送信 

#### <a name="internal-io-driver-rarp-send"></a>内部 I/O ドライバーの RARP 送信

**アイコン** ![内部 I / O ドライバーの RARP 送信アイコン](./media/user-guide/netx-events/image31.png)

**説明**

このイベントは、内部 NetX I/O ドライバーの RARP 送信イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: パケットへのポインター
- 情報フィールド 3: パケット サイズ
- 情報フィールド 4: 使用されていません

### <a name="internal-io-driver-multicast-join"></a>内部 I/O ドライバーのマルチキャスト参加 

#### <a name="internal-io-driver-multicast-join"></a>内部 I/O ドライバーのマルチキャスト参加

**アイコン** ![内部 I / O ドライバーのマルチキャスト参加アイコン](./media/user-guide/netx-events/image32.png)

**説明**

このイベントは、内部 NetX I/O ドライバーのマルチキャスト参加イベントを表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="internal-io-driver-multicast-leave"></a>内部 I/O ドライバーのマルチキャスト離脱 

#### <a name="internal-io-driver-multicast-leave"></a>内部 I/O ドライバーのマルチキャスト離脱

**アイコン** ![内部 I / O ドライバーのマルチキャスト離脱アイコン](./media/user-guide/netx-events/image33.png)

**説明**

このイベントは、内部 NetX I/O ドライバーのマルチキャスト離脱イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="internal-io-driver-get-status"></a>内部 I/O ドライバーの状態取得 

#### <a name="internal-io-driver-get-status"></a>内部 I/O ドライバーの状態取得

**アイコン** ![内部 I / O ドライバーの状態取得アイコン](./media/user-guide/netx-events/image34.png)

**説明**

このイベントは、内部 NetX I/O ドライバーの状態取得イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="internal-io-driver-get-speed"></a>内部 I/O ドライバーの速度取得 

#### <a name="internal-io-driver-get-speed"></a>内部 I/O ドライバーの速度取得

**アイコン** ![内部 I / O ドライバーの速度取得アイコン](./media/user-guide/netx-events/image35.png)

**説明**

このイベントは、内部 NetX I/O ドライバーの速度取得イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="internal-io-driver-get-duplex-type"></a>内部 I/O ドライバーの二重タイプ取得 

#### <a name="internal-io-driver-get-duplex-type"></a>内部 I/O ドライバーの二重タイプ取得

**アイコン** ![内部 I / O ドライバーの二重タイプ取得アイコン](./media/user-guide/netx-events/image36.png)

**説明**

このイベントは、内部 NetX I/O ドライバーの二重タイプ取得イベントを表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="internal-io-driver-get-error-count"></a>内部 I/O ドライバーのエラー数取得

#### <a name="internal-io-driver-get-error-count"></a>内部 I/O ドライバーのエラー数取得

**アイコン** ![内部 I / O ドライバーのエラー数取得アイコン](./media/user-guide/netx-events/image37.png)

**説明**

このイベントは、内部 NetX I/O ドライバーのエラー数取得イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="internal-io-driver-get-rx-count"></a>内部 I/O ドライバーの RX 数取得 

#### <a name="internal-io-driver-get-rx-count"></a>内部 I/O ドライバーの RX 数取得

**アイコン** ![内部 I / O ドライバーの RX 数取得アイコン](./media/user-guide/netx-events/image38.png)

**説明**

このイベントは、内部 NetX I/O ドライバーの RX 数取得イベントを表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="internal-io-driver-get-tx-count"></a>内部 I/O ドライバーの TX 数取得 

#### <a name="internal-io-driver-get-tx-count"></a>内部 I/O ドライバーの TX 数取得

**アイコン** ![内部 I / O ドライバーの T X 数取得アイコン](./media/user-guide/netx-events/image39.png)

**説明**

このイベントは、内部 NetX I/O ドライバーの TX 数取得イベントを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="internal-io-driver-get-allocation-errors"></a>内部 I/O ドライバーの割り当てエラー数の取得 

#### <a name="internal-io-driver-get-allocation-errors"></a>内部 I/O ドライバーの割り当てエラー数の取得

**アイコン** ![内部 I / O ドライバーの割り当てエラー数の取得アイコン](./media/user-guide/netx-events/image40.png)

**説明**

このイベントは、内部 NetX I/O ドライバーの割り当てエラー数の取得イベントを表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="internal-io-driver-un-initialize"></a>内部 I/O ドライバーの初期化解除 

#### <a name="internal-io-driver-un-initialize"></a>内部 I/O ドライバーの初期化解除 

**アイコン** ![内部 I / O ドライバーの初期化解除アイコン](./media/user-guide/netx-events/image41.png)

**説明**

このイベントは、内部 NetX I/O ドライバーの初期化解除イベントを表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="internal-io-driver-deferred-processing"></a>内部 I/O ドライバーの遅延処理 

#### <a name="internal-io-driver-deferred-processing"></a>内部 I/O ドライバーの遅延処理 

**アイコン** ![内部 I / O ドライバーの遅延処理アイコン](./media/user-guide/netx-events/image42.png)

**説明**

NetX の I/O ドライバーの遅延処理イベントです。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: パケットへのポインター
- 情報フィールド 3: パケット長
- 情報フィールド 4: 使用されていません

### <a name="arp-dynamic-entries-invalidate"></a>ARP 動的エントリの無効化 

#### <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate

**アイコン** ![A R P 動的エントリの無効化アイコン](./media/user-guide/netx-events/image43.png)

**説明**

このイベントは、nx_arp_dynamic_entries_invalidate を使用したすべての動的 ARP エントリの無効化を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 無効化されたエントリ
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="arp-dynamic-entry-set"></a>ARP 動的エントリの設定 

#### <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set

**アイコン** ![A R P 動的エントリの設定アイコン](./media/user-guide/netx-events/image44.png)

**説明**

このイベントは、nx_arp_dynamic_entry_set を使用した動的 ARP エントリの設定を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: IP アドレス
- 情報フィールド 3: 物理アドレス (MSW)
- 情報フィールド 4: 物理アドレス (LSW)

### <a name="arp-enable"></a>ARP 有効化 

#### <a name="nx_arp_enable"></a>nx_arp_enable

**アイコン** ![A R P 有効化アイコン](./media/user-guide/netx-events/image45.png)

**説明**

このイベントは、nx_arp_enable を使用した ARP の有効化を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ARP キャッシュ メモリ ポインター
- 情報フィールド 3: ARP キャッシュ メモリ サイズ
- 情報フィールド 4: 使用されていません

### <a name="arp-gratuitous-send"></a>ARP Gratuitous 送信 

#### <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send

**アイコン** ![A R P Gratuitous 送信アイコン](./media/user-guide/netx-events/image46.png)

**説明**

このイベントは、nx_arp_gratuitous_send を使用した ARP Gratuitous 送信を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="arp-hardware-address-find"></a>ARP ハードウェア アドレス検索 

#### <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find

**アイコン** ![A R P ハードウェア アドレス検索アイコン](./media/user-guide/netx-events/image47.png)

**説明**

このイベントは、nx_arp_hardware_address_find を使用した物理アドレスの検索を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: IP アドレス
- 情報フィールド 3: 物理アドレス (MSW)
- 情報フィールド 4: 物理アドレス (LSW)

### <a name="arp-information-get"></a>ARP 情報の取得 

#### <a name="nx_arp_info_get"></a>nx_arp_info_get

**アイコン** ![A R P 情報の取得アイコン](./media/user-guide/netx-events/image48.png)

**説明**

このイベントは、nx_arp_info_get を使用した情報の取得を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 送信済み ARP
- 情報フィールド 3: ARP 応答
- 情報フィールド 4: 受信済み ARP

### <a name="arp-ip-address-find"></a>ARP IP アドレス検索 

#### <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find

**アイコン** ![A R P I P アドレス検索アイコン](./media/user-guide/netx-events/image49.png)

**説明**

このイベントは、指定された物理アドレスに関連付けられた IP アドレスの、nx_arp_ip_address_find を使用した検索を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: IP アドレス
- 情報フィールド 3: 物理アドレス (MSW)
- 情報フィールド 4: 物理アドレス (LSW)

### <a name="arp-static-entry-create"></a>ARP 静的エントリの作成 

#### <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create

**アイコン** ![A R P 静的エントリの作成アイコン](./media/user-guide/netx-events/image50.png)

**説明**

このイベントは、nx_arp_static_entry_create を使用した静的 ARP エントリの作成を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: IP アドレス
- 情報フィールド 3: 物理アドレス (MSW)
- 情報フィールド 4: 物理アドレス (LSW)

### <a name="arp-static-entries-delete"></a>ARP 静的エントリの削除 

#### <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete

**アイコン** ![A R P 静的エントリの削除アイコン](./media/user-guide/netx-events/image51.png)

**説明**

このイベントは、nx_arp_static_entries_delete を使用したすべての ARP 静的エントリの削除を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 削除されたエントリ
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="arp-static-entry-delete"></a>ARP 静的エントリの削除 

### <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete

**アイコン** ![A R P 静的エントリの削除アイコン](./media/user-guide/netx-events/image52.png)

**説明**

このイベントは、nx_arp_static_entry_delete を使用した静的 ARP エントリの削除を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: IP アドレス
- 情報フィールド 3: 物理アドレス (MSW)
- 情報フィールド 4: 物理アドレス (LSW)

### <a name="duo-cache-entry-delete"></a>Duo キャッシュ エントリの削除 

#### <a name="nxd_und_cache_entry_delete"></a>nxd_und_cache_entry_delete

**アイコン** ![Duo キャッシュ エントリの削除アイコン](./media/user-guide/netx-events/image53.png)

**説明**

このイベントは、nx_udp_socket_create を使用した近隣キャッシュ テーブルに含まれるエントリの削除を表します。

**情報フィールド** 

- 情報フィールド 1: 削除する IPv6 リンク ローカル アドレスの 4 番目 (最下位) のワード
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="duo-cache-entry-set"></a>Duo キャッシュ エントリの設定 

#### <a name="nxd_nd_cache_entry_set"></a>nxd_nd_cache_entry_set

**アイコン** ![Duo キャッシュ エントリの設定アイコン](./media/user-guide/netx-events/image54.png)

**説明**

このイベントは、nxd_nd_cache_entry_set を使用した、キャッシュ エントリの作成と近隣キャッシュ テーブルの追加を表します。

**情報フィールド** 

- 情報フィールド 1: 追加する IPv6 アドレスの 4 番目 (最下位) のワード
- 情報フィールド 2: 物理アドレスの MSB
- 情報フィールド 3: 物理アドレスの LSB
- 情報フィールド 4: 使用されていません

### <a name="duo-cache-invalidate"></a>Duo キャッシュの無効化 

#### <a name="nxd_nd_cache_invalidate"></a>nxd_nd_cache_invalidate

**アイコン** ![Duo キャッシュの無効化アイコン](./media/user-guide/netx-events/image55.png)

**説明**

このイベントは、nxd_nd_cache_invalidate を使用した、近隣ノード キャッシュ テーブル全体の無効化を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="duo-cache-ip-address-find"></a>Duo キャッシュ IP アドレス検索 

#### <a name="nxd_nd_cache_ip_address_find"></a>nxd_nd_cache_ip_address_find

**アイコン** ![Duo キャッシュ I P アドレス検索アイコン](./media/user-guide/netx-events/image56.png)

**説明**

このイベントは、nxd_nd_cache_ip_address_find を使用して、指定された物理アドレスと一致する IP アドレスをキャッシュ テーブルから取得することを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: IPv6 アドレスの 4 番目 (最下位) のワード
- 情報フィールド 3: 物理アドレスの MSB
- 情報フィールド 4: 物理アドレスの LSB

### <a name="duo-icmp-enable"></a>Duo ICMP の有効化 

#### <a name="nxd_icmp_enable"></a>nxd_icmp_enable

**アイコン** ![Duo I C M P の有効化アイコン](./media/user-guide/netx-events/image57.png)

**説明**

このイベントは、nxd_icmp_enable を使用して、指定された IP インスタンスで有効になっている ICMPv4 および ICMPv6 サービスを表します。

**情報フィールド**
- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="duo-icmp-ping"></a>Duo ICMP ping 

#### <a name="nxd_icmp_ping"></a>nxd_icmp_ping

**アイコン** ![Duo I C M P ping アイコン](./media/user-guide/netx-events/image58.png)

**説明**

このイベントは、nxd_icmp_ping を使用した IPv6 ホストへの ping (エコー要求) の送信を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: IPv6 アドレス
- 情報フィールド 3: エコー データへのポインター
- 情報フィールド 4: エコー データのサイズ

### <a name="duo-ip-max-payload-size-find"></a>Duo IP ペイロードの最大サイズの検索 

#### <a name="nxd_ip_max_payload_size"></a>nxd_ip_max_payload_size

**アイコン** ![Duo I P ペイロードの最大サイズの検索アイコン](./media/user-guide/netx-events/image59.png)

**説明**

このイベントは、指定されたパケットに断片化せずに含められる最大ペイロードを計算します。

**情報フィールド**

- 情報フィールド 1: ソケット ポインター
- 情報フィールド 2: ピア IP アドレス
- 情報フィールド 3: ピア ポート 情報フィールド 4: 使用されていません

### <a name="duo-ip-raw-packet-send"></a>Duo IP 生パケット送信 

#### <a name="nxd_ip_max_packet_send"></a>nxd_ip_max_packet_send

**アイコン** ![Duo I P 生パケット送信アイコン](./media/user-guide/netx-events/image60.png)

**説明**

このイベントは、nxd_ip_raw_packet_send を使用した、指定されたネットワーク インターフェイスから指定された IP 宛先アドレスへの生 IP パケットの送信を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 送信するパケットへのポインター
- 情報フィールド 3: 宛先アドレスへのポインター
- 情報フィールド 4: パケット プロトコル

### <a name="duo-ipv6-default-router-add"></a>Duo IPv6 既定ルーターの追加 

#### <a name="nxd_ipv6_default_router_add"></a>nxd_ipv6_default_router_add

**アイコン** ![Duo I P v 6 既定ルーターの追加アイコン](./media/user-guide/netx-events/image61.png)

**説明**

このイベントは、nxd_ipv6_default_router_add を使用して、IP インスタンスの IPv6 ルーティング テーブルに既定のルーターを追加することを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター。
- 情報フィールド 2: 宛先ネットワーク アドレス。
- 情報フィールド 3: 有効期間情報。
- 情報フィールド 4: 使用されていません。

### <a name="duo-ipv6-default-router-delete"></a>Duo IPv6 既定ルーターの削除 

#### <a name="nxd_ipv6_default_router_delete"></a>nxd_ipv6_default_router_delete

**アイコン** ![Duo I P v 6 既定ルーターの削除アイコン](./media/user-guide/netx-events/image62.png)

**説明**

このイベントは、nxd_ipv6_default_router_delete を使用して、IP インスタンスの IPv6 ルーティング テーブルから既定のルーターを削除することを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター。
- 情報フィールド 2: 既定ルーターの IPv6 アドレスで 4 番目のワード (最下位)。
- 情報フィールド 3: 使用されていません。
- 情報フィールド 4: 使用されていません。

### <a name="duo-ipv6-enable"></a>Duo IPv6 の有効化 

#### <a name="nxd_ipv6_enable"></a>nxd_ipv6_enable

**アイコン** ![Duo I P v 6 の有効化アイコン](./media/user-guide/netx-events/image63.png)

**説明**

このイベントは、nxd_ipv6_enable を使用して、指定された IP インスタンスの IPv6 サービスを有効化することを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="duo-ipv6-global-address-get"></a>Duo IPv6 グローバル アドレス取得 

#### <a name="nxd_ipv6_global_address_get"></a>nxd_ipv6_global_address_get

**アイコン** ![Duo I P v 6 グローバル アドレス取得アイコン](./media/user-guide/netx-events/image64.png)

**説明**

このイベントは、nxd_ipv6_global_address_get を使用して、IP インスタンス インターフェイス テーブルのインデックス 1 にある IP インスタンスのグローバル (プライマリ) IP アドレスを取得することを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター。
- 情報フィールド 2: グローバル アドレスの 4 番目のワード (最下位)
- 情報フィールド 3: IPv6 アドレス プレフィックス長。
- 情報フィールド 4: IP インターフェイス テーブル (1) へのインデックス。

### <a name="duo-ipv6-global-address-set"></a>Duo IPv6 グローバル アドレスの設定 

#### <a name="nxd_ipv6_global_address_set"></a>nxd_ipv6_global_address_set

**アイコン** ![Duo I P v 6 グローバル アドレスの設定アイコン](./media/user-guide/netx-events/image65.png)

**説明**

このイベントは、nxd_ipv6_global_address_set を使用して、IP インスタンス インターフェイス テーブルのインデックス 1 にある IP インスタンスのグローバル (プライマリ) IP アドレスを設定することを表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: グローバル アドレスの 4 番目のワード (最下位)
- 情報フィールド 3: IPv6 アドレス プレフィックス長
- 情報フィールド 4: IP インターフェイス テーブル (1) へのインデックス

### <a name="duo-ipv6-initiate-dad-process"></a>Duo IPv6 DAD プロセスの開始 

#### <a name="nxd_ipv6_initiate_dad_process"></a>nxd_ipv6_initiate_dad_process

**アイコン** ![Duo I P v 6 DAD プロセスの開始アイコン](./media/user-guide/netx-events/image66.png)

**説明**

このイベントは、IP インスタンスにリンク ローカルまたは IP インターフェイス アドレスが割り当てられている場合に、nxd_ipv6_initiate_dad_process を使用して、重複アドレス検出 (DAD) プロセスが開始されることを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="duo-ipv6-interface-address-get"></a>Duo IPv6 インターフェイス アドレスの取得 

#### <a name="nxd_ipv6_interface_address_get"></a>nxd_ipv6_interface_address_get

**アイコン** ![Duo I P v 6 インターフェイス アドレスの取得アイコン](./media/user-guide/netx-events/image67.png)

**説明**

このイベントは、nxd_ipv6_interface_address_get を使用して、指定されたインデックス位置にある IP アドレスとプレフィックスを IP インスタンス インターフェイス アドレス テーブルに取得することを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 返す IPv6 アドレスの 4 番目のワード (最下位)
- 情報フィールド 4: IP インスタンス インターフェイス テーブルへのインターフェイスのインデックス

### <a name="duo-ipv6-interface-address-set"></a>Duo IPv6 インターフェイス アドレスの設定 

### <a name="nxd_ipv6_interface_address_set"></a>nxd_ipv6_interface_address_set

**アイコン** ![Duo I P v 6 インターフェイス アドレスの設定アイコン](./media/user-guide/netx-events/image68.png)

**説明**

このイベントは、指定されたインデックスにある IP アドレスとプレフィックスを IP インスタンス インターフェイス アドレス テーブルに設定することを表します。 nxd_ipv6_interface_address_set を使用した場合、インデックス ゼロ (リンク ローカル アドレス) では許可されません。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 返す IPv6 アドレスの 4 番目のワード (最下位)
- 情報フィールド 3: プレフィックス長
- 情報フィールド 4: IP インスタンス インターフェイス テーブルへのインターフェイスのインデックス

### <a name="duo-ipv6-link-local-address-get"></a>Duo IPv6 リンク ローカル アドレスの取得 

#### <a name="nxd_ipv6_linklocal_address_get"></a>nxd_ipv6_linklocal_address_get

**アイコン** ![Duo I P v 6 リンク ローカル アドレスの取得アイコン](./media/user-guide/netx-events/image69.png)

**説明**

このイベントは、指定された IP インスタンスのリンク ローカル アドレスを nxd_ipv6_linklocal_address_get を使用して取得することを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: IPv6 リンク ローカル アドレスの 4 番目のワード (最下位)
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="duo-ipv6-link-local-address-set"></a>Duo IPv6 リンク ローカル アドレスの設定 

#### <a name="nxd_ipv6_linklocal_address_set"></a>nxd_ipv6_linklocal_address_set

**アイコン** ![Duo I P v 6 リンク ローカル アドレスの設定アイコン](./media/user-guide/netx-events/image70.png)

**説明**

このイベントは、nxd_ipv6_linklocal_address_set を使用した、IP インスタンスのリンク ローカル アドレスの設定を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: IPv6 リンク ローカル アドレスの 4 番目 (最下位) のワード
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="duo-ipv6-raw-packet-send"></a>Duo IPv6 生パケット送信 

#### <a name="nxd_ipv6_raw_packet_send"></a>nxd_ipv6_raw_packet_send

**アイコン** ![Duo I P v 6 生パケット送信アイコン](./media/user-guide/netx-events/image71.png)

**説明**

このイベントは、nxd_ip_raw_packet_send を使用して、指定された宛先にプライマリ IP インターフェイスを介して生 IP パケットを送信することを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 送信するパケットへのポインター
- 情報フィールド 3: 宛先 IP アドレス
- 情報フィールド 4: 使用されていません

### <a name="duo-tcp-socket-peer-info-get"></a>Duo TCP ソケット ピア情報の取得 

#### <a name="nxd_tcp_socket_peer_info_get"></a>nxd_tcp_socket_peer_info_get

**アイコン** ![Duo T C P ソケット ピア情報の取得アイコン](./media/user-guide/netx-events/image72.png)

**説明**

このイベントでは、指定されたソケットで受信した TCP パケットから送信者データが抽出されます。 送信元の IP アドレスとポートが返されます。

**情報フィールド**

- 情報フィールド 1: ソケット ポインター
- 情報フィールド 2: ピア IP アドレス
- 情報フィールド 3: ピア ポート
- 情報フィールド 4: IP アドレスの最下位の 32 ビット

### <a name="duo-tcp-socket-set-interface"></a>Duo TCP ソケットの設定インターフェイス 

#### <a name="nxd_tcp_socket_set_interface"></a>nxd_tcp_socket_set_interface

**アイコン** ![Duo T C P ソケットの設定インターフェイス アイコン](./media/user-guide/netx-events/image73.png)

**説明**

このイベントは、クライアントが指定されたサーバー IP アドレスの TCP サーバーに接続した後で、nxd_tcp_client_socket_connect を使用して発信ソケット インターフェイスを設定することを表します。

**情報フィールド** 

- 情報フィールド 1: TCP ソケットへのポインター
- 情報フィールド 2: インターフェイス ID
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="duo-udp-socket-send"></a>Duo UDP ソケット送信 

#### <a name="nxd_udp_socket_send"></a>nxd_udp_socket_send

**アイコン** ![Duo U D P ソケットの送信アイコン](./media/user-guide/netx-events/image74.png)

**説明**

このイベントは、nxd_udp_socket_send 経由で入力 IP アドレスとポートを使用して、指定されたソケットを介して UDP パケットを送信することを表します。

**情報フィールド** 

- 情報フィールド 1: ポインター UDP ソケット
- 情報フィールド 2: UDP パケットへのポインター
- 情報フィールド 3: パケット長
- 情報フィールド 4: 使用されていません


### <a name="duo-udp-socket-set-interface"></a>Duo UDP ソケットの設定インターフェイス 

#### <a name="nxd_udp_socket_set_interface"></a>nxd_udp_socket_set_interface

**アイコン** ![Duo U D P ソケットの設定インターフェイス アイコン](./media/user-guide/netx-events/image75.png)

**説明**

このイベントは、nxd_udp_socket_set_interface を使用して、指定された UDP ソケット送信インターフェイスを入力インターフェイス ID に対応するインターフェイスに設定することを表します。

**情報フィールド** 

- 情報フィールド 1: UDP ソケットへのポインター
- 情報フィールド 2: インターフェイス ID
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="duo-udp-source-extract"></a>Duo UDP ソース抽出 

#### <a name="nxd_udp_socket_extract"></a>nxd_udp_socket_extract

**アイコン** ![Duo U D P ソース抽出アイコン](./media/user-guide/netx-events/image76.png)

**説明**

このイベントは、受信したパケットの IP アドレスと送信元ポートの抽出を表します (IPv4 または IPv6)。 IPv6 の場合、IP アドレスの 4 番目のワード (最下位) が nxd_udp_source_extract によって返されます。

**情報フィールド**

- 情報フィールド 1: パケットへのポインター
- 情報フィールド 2: IP バージョン
- 情報フィールド 3: 送信元 IP アドレス (IPv4 または IPv6)
- 情報フィールド 4: 送信元ポート

### <a name="icmp-enable"></a>ICMP の有効化 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**アイコン** ![I C M P の有効化アイコン](./media/user-guide/netx-events/image77.png)

**説明**

このイベントは、nx_icmp_enable を使用した ICMP の有効化を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンス l へのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="icmp-information-get"></a>ICMP 情報の取得 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**アイコン** ![I C M P 情報の取得アイコン](./media/user-guide/netx-events/image78.png)

**説明**

このイベントは、nx_icmp_info_get を使用した情報の取得を表します。

**情報フィールド**
- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 送信された ping
- 情報フィールド 3: ping 応答
- 情報フィールド 4: 受信した ping

### <a name="icmp-ping"></a>ICMP Ping 

#### <a name="nx_icmp_ping"></a>nx_icmp_ping

**アイコン** ![I C M P ping アイコン](./media/user-guide/netx-events/image79.png)

**説明**

このイベントは、nx_icmp_ping を使用したターゲット IP アドレスの ping を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: IP アドレス
- 情報フィールド 3: データへのポインター
- 情報フィールド 4: データのサイズ

### <a name="igmp-enable"></a>IGMP の有効化 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**アイコン** ![I G M P の有効化アイコン](./media/user-guide/netx-events/image80.png)

**説明**

このイベントは、nx_igmp_enable を使用した IGMP の有効化を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="igmp-information-get"></a>IGMP 情報の取得 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**アイコン** ![I G M P 情報の取得アイコン](./media/user-guide/netx-events/image81.png)

**説明**

このイベントは、nx_igmp_info_get 経由での情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 送信されたレポート
- 情報フィールド 3: 受信したクエリ
- 情報フィールド 4: 参加しているグループ

### <a name="igmp-loopback-disable"></a>IGMP ループバックの無効化 

#### <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable

**アイコン** ![I G M P ループバックの無効化アイコン](./media/user-guide/netx-events/image82.png)

**説明**

このイベントは、nx_igmp_loopback_disable を使用した IGMP ループバックの無効化を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="igmp-loopback-enable"></a>IGMP ループバックの有効化 

#### <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable

**アイコン** ![I G M P ループバックの有効化アイコン](./media/user-guide/netx-events/image83.png)

**説明**

このイベントは、nx_igmp_loopback_enable を使用した IGMP ループバックの有効化を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="igmp-multicast-join"></a>IGMP マルチキャスト参加 

#### <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join

**アイコン** ![I G M P マルチキャスト参加アイコン](./media/user-guide/netx-events/image84.png)

**説明**

このイベントは、nx_igmp_multicast_join を使用したマルチキャスト グループの参加を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: グループ IP アドレス
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="igmp-multicast-leave"></a>IGMP マルチキャスト離脱 

#### <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave

**アイコン** ![I G M P マルチキャスト離脱アイコン](./media/user-guide/netx-events/image85.png)

**説明**

このイベントは、nx_igmp_multicast_leave を使用した、マルチキャスト グループの離脱を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: グループ IP アドレス
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="ip-address-change-notify"></a>IP アドレス変更通知 

#### <a name="nx_ip_address_change_notify"></a>nx_ip_address_change_notify

**アイコン** ![I P アドレス変更通知アイコン](./media/user-guide/netx-events/image86.png)

**説明**

このイベントは、nx_ip_address_change_notify を使用した IP 変更通知の登録を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: コールバック関数ポインター
- 情報フィールド 3: 追加情報ポインター
- 情報フィールド 4: 使用されていません

### <a name="ip-address-get"></a>IP アドレスの取得 

#### <a name="nx_ip_address_get"></a>nx_ip_address_get

**アイコン** ![I P アドレスの取得アイコン](./media/user-guide/netx-events/image87.png)

**説明**

このイベントは、nx_ip_address_get を使用した IP アドレスの取得を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: IP アドレス
- 情報フィールド 3: ネットワーク マスク
- 情報フィールド 4: 使用されていません

### <a name="ip-address-set"></a>IP アドレスの設定 

#### <a name="nx_ip_address_set"></a>nx_ip_address_set

**アイコン** ![I P アドレスの設定アイコン](./media/user-guide/netx-events/image88.png)

**説明**

このイベントは nx_ip_address_set を使用した IP アドレスの設定を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: IP アドレス
- 情報フィールド 3: ネットワーク マスク
- 情報フィールド 4: 使用されていません

### <a name="ip-create"></a>IP の作成 

#### <a name="nx_ip_create"></a>nx_ip_create

**アイコン** ![I P の作成アイコン](./media/user-guide/netx-events/image89.png)

**説明**

このイベントは、nx_ip_create を使用した IP インスタンスの作成を表します。

**情報フィールド** 
- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: IP アドレス
- 情報フィールド 3: ネットワーク マスク
- 情報フィールド 4: 既定のパケット プール ポインター

### <a name="ip-delete"></a>IP の削除 

#### <a name="nx_ip_delete"></a>nx_ip_delete

**アイコン** ![I P の削除アイコン](./media/user-guide/netx-events/image90.png)

**説明**

このイベントは、nx_ip_delete を使用した IP インスタンスの削除を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="ip-driver-direct-command"></a>IP ドライバーのダイレクト コマンド 

#### <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command

**アイコン** ![I P ドライバーのダイレクト コマンド アイコン](./media/user-guide/netx-events/image91.png)

**説明**

このイベントは、nx_ip_driver_direct_command を使用したダイレクト I/O ドライバー コマンドを表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ドライバー コマンド
- 情報フィールド 3: 戻り値
- 情報フィールド 4: 使用されていません

### <a name="ip-forwarding-disable"></a>IP 転送の無効化 

#### <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable

**アイコン** ![I P 転送の無効化アイコン](./media/user-guide/netx-events/image92.png)

**説明**

このイベントは、nx_ip_forwarding_disable を使用した、IP 転送の無効化を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="ip-forwarding-enable"></a>IP 転送の有効化 

#### <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable

**アイコン** ![I P 転送の有効化アイコン](./media/user-guide/netx-events/image93.png)

**説明**

このイベントは、nx_ip_forwarding_enable を使用した IP 転送の有効化を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="ip-fragment-disable"></a>IP フラグメントの無効化 

#### <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable

**アイコン** ![I P フラグメントの無効化アイコン](./media/user-guide/netx-events/image94.png)

**説明**

このイベントは、nx_ip_fragment_disable を使用した、IP フラグメントの無効化を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="ip-fragment-enable"></a>IP フラグメントの有効化 

#### <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable

**アイコン** ![I P フラグメントの有効化アイコン](./media/user-guide/netx-events/image95.png)

**説明**

このイベントは、nx_ip_fragment_enable を使用した IP フラグメントの有効化を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="ip-gateway-address-set"></a>IP ゲートウェイ アドレスの設定 

#### <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set

**アイコン** ![I P ゲートウェイ アドレスの設定アイコン](./media/user-guide/netx-events/image96.png)

**説明**

このイベントは、nx_ip_gateway_address_set を使用したゲートウェイ IP アドレスの設定を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ゲートウェイ IP アドレス
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="ip-information-get"></a>IP 情報の取得 

#### <a name="nx_ip_info_get"></a>nx_ip_info_get

**アイコン** ![I P 情報の取得アイコン](./media/user-guide/netx-events/image97.png)

**説明** このイベントは、nx_ip_info_get を使用した IP 情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 送信された IP バイト数
- 情報フィールド 3: 受信した IP バイト数
- 情報フィールド 4: ドロップされた IP パケット数

### <a name="ip-interface-attach"></a>IP インターフェイスのアタッチ 

#### <a name="nx_interface_attach"></a>nx_interface_attach

**アイコン** ![I P インターフェイスのアタッチ アイコン](./media/user-guide/netx-events/image98.png)

**説明**

このイベントは、nx_ip_interface_attach を使用して、IP インスタンスに接続されているセカンダリ ネットワーク インターフェイスを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: インターフェイスの IP アドレス
- 情報フィールド 3: IP インターフェイス テーブルへのインデックス
- 情報フィールド 4: 使用されていません

### <a name="ip-interface-info-get"></a>IP インターフェイス情報の取得 

#### <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get

**アイコン** ![ IP インターフェイス情報の取得アイコン](./media/user-guide/netx-events/image99.png)

**説明**

このイベントは、nx_ip_interface_info_get を使用して、指定されたネットワーク インターフェイスから取得した情報を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: インターフェイスの IP アドレス
- 情報フィールド 3: インターフェイスの MAC アドレスの MSB
- 情報フィールド 4: インターフェイスの MAC アドレスの LSB

### <a name="ip-raw-packet-disable"></a>IP 生パケットの無効化 

#### <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable

**アイコン** ![I P 生パケットの無効化アイコン](./media/user-guide/netx-events/image100.png)

**説明**

このイベントは、nx_ip_raw_packet_disable を使用した生 IP パケット通信の無効化を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="ip-raw-packet-enable"></a>IP 生パケットの有効化 

#### <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable

**アイコン** ![I P 生パケットの有効化アイコン](./media/user-guide/netx-events/image101.png)

**説明**

このイベントは、nx_ip_raw_packet_enable を使用した生 IP パケット通信の有効化を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="ip-raw-packet-receive"></a>IP 生パケットの受信 

#### <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive

**アイコン** ![I P 生パケットの受信アイコン](./media/user-guide/netx-events/image102.png)

**説明**

このイベントは、nx_ip_raw_packet_receive を使用した生 IP パケットの受信を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: パケットへのポインター
- 情報フィールド 3: 待機オプション
- 情報フィールド 4: 使用されていません

### <a name="ip-raw-packet-send"></a>IP 生パケット送信 

#### <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send

**アイコン** ![I P 生パケット送信アイコン](./media/user-guide/netx-events/image103.png)

**説明**

このイベントは、nx_ip_raw_packet_send を使用した生 IP パケットの送信を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: パケットへのポインター
- 情報フィールド 3: 宛先 IP アドレス
- 情報フィールド 4: サービスの種類

### <a name="ip-static-route-add"></a>IP 静的ルートの追加 

#### <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add

**アイコン** ![I P 静的ルートの追加アイコン](./media/user-guide/netx-events/image104.png)

**説明**

このイベントは、nx_ip_static_route_add を使用して、IP インスタンスのルーティング テーブルに追加される静的ルートを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ネットワーク アドレス
- 情報フィールド 3: ネットワーク マスク
- 情報フィールド 4: ネクスト ホップ

### <a name="ip-static-route-delete"></a>IP 静的ルートの削除 

#### <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete

**アイコン** ![I P 静的ルートの削除アイコン](./media/user-guide/netx-events/image105.png)

**説明**

このイベントは、nx_ip_static_route_delete を使用して、IP インスタンス ルーティング テーブルから削除される静的ルートを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ネットワーク アドレス
- 情報フィールド 3: ネットワーク マスク
- 情報フィールド 4: 使用されていません

### <a name="ip-status-check"></a>IP 状態チェック 

#### <a name="nx_ip_status_check"></a>nx_ip_status_check

**アイコン** ![I P 状態チェック アイコン](./media/user-guide/netx-events/image106.png)

**説明**

このイベントは、nx_ip_status_check を使用した IP 状態の確認を表します。

情報フィールド 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 要求された状態
- 情報フィールド 3: 実際の状態
- 情報フィールド 4: 待機オプション

### <a name="ipsec-enable"></a>IPSEC の有効化 

#### <a name="nx_ipsec_enable"></a>nx_ipsec_enable

**アイコン** ![I P S E C の有効化アイコン](./media/user-guide/netx-events/image107.png)

**説明**

このイベントは、nx_ipsec_enable を使用して、指定された IP インスタンスの IPSec サービスを有効化することを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="packet-allocate"></a>パケットの割り当て 

#### <a name="nx_packet_allocate"></a>nx_packet_allocate

**アイコン** ![パケットの割り当てアイコン](./media/user-guide/netx-events/image108.png)

**説明**

nx_packet_allocate でパケットを割り当てるイベントです。

**情報フィールド**

- 情報フィールド 1: パケット プールへのポインター
- 情報フィールド 2: 割り当てられたパケットへのポインター
- 情報フィールド 3: パケットの種類
- 情報フィールド 4: 使用可能なパケット

### <a name="packet-copy"></a>パケット コピー 

#### <a name="nx_packet_copy"></a>nx_packet_copy

**アイコン** ![パケット コピー アイコン](./media/user-guide/netx-events/image109.png)

**説明**

このイベントは、nx_packet_copy を使用したパケットのコピーを表します。

**情報フィールド**

- 情報フィールド 2: 新しいパケット ポインター
- 情報フィールド 3: パケット プールへのポインター
- 情報フィールド 4: 待機オプション

### <a name="packet-data-append"></a>パケット データの追加 

#### <a name="nx_packet_data_append"></a>nx_packet_data_append

**アイコン** ![パケット データの追加アイコン](./media/user-guide/netx-events/image110.png)

**説明**

このイベントは、nx_packet_data_append を使用したパケットへのデータの追加を表します。

**情報フィールド**

- 情報フィールド 1: パケットへのポインター
- 情報フィールド 2: データへのポインター
- 情報フィールド 3: データのサイズ
- 情報フィールド 4: パケット プールへのポインター

### <a name="packet-data-extract-offset"></a>パケット データ抽出オフセット 

#### <a name="nx_udp_source_extract_offset"></a>nx_udp_source_extract_offset

**アイコン** ![パケット データ抽出オフセット アイコン](./media/user-guide/netx-events/image111.png)

**説明**

このイベントは、nx_udp_source_extract_offset を使用してパケットから指定されたバッファーに抽出されるパケット データを表します。

**情報フィールド**

- 情報フィールド 1: パケットへのポインター
- 情報フィールド 2: 指定されたバッファーのサイズ
- 情報フィールド 3: コピーされたバイト数
- 情報フィールド 4: 使用されていません

### <a name="packet-data-retrieve"></a>パケット データ取得 

#### <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve

**アイコン** ![パケット データ取得アイコン](./media/user-guide/netx-events/image112.png)

**説明**

このイベントは、nx_packet_data_retrieve を使用したパケットからのデータ取得を表します。

**情報フィールド** 

- 情報フィールド 1: パケットへのポインター
- 情報フィールド 2: バッファーの先頭へのポインター
- 情報フィールド 3: コピーされたバイト数
- 情報フィールド 4: 使用されていません

### <a name="packet-length-get"></a>パケット長の取得 

#### <a name="nx_packet_length_get"></a>nx_packet_length_get

**アイコン** ![パケット長の取得アイコン](./media/user-guide/netx-events/image113.png)

**説明**

このイベントは、nx_packet_length_get を使用したパケット長の取得を表します。

**情報フィールド**

- 情報フィールド 1: パケットへのポインター
- 情報フィールド 2: パケット長
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="packet-pool-create"></a>パケット プールの作成 

#### <a name="nx_packet_pool_create"></a>nx_packet_pool_create

**アイコン** ![パケット プールの作成アイコン](./media/user-guide/netx-events/image114.png)

**説明**

このイベントは、nx_packet_pool_create を使用したパケット プールの作成を表します。

**情報フィールド** 

- 情報フィールド 1: パケット プールへのポインター
- 情報フィールド 2: パケット ペイロードのサイズ
- 情報フィールド 3: プール メモリ領域へのポインター
- 情報フィールド 4: プール メモリ領域のサイズ

### <a name="packet-pool-delete"></a>パケット プールの削除 

#### <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete

**アイコン** ![パケット プールの削除アイコン](./media/user-guide/netx-events/image115.png)

**説明**

このイベントは、nx_packet_pool_delete を使用したパケット プールの削除を表します。

**情報フィールド** 

- 情報フィールド 1: パケット プールへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

#### <a name="packet-pool-information-get"></a>パケット プール情報の取得 

#### <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get

**アイコン** ![パケット プール情報の取得アイコン](./media/user-guide/netx-events/image116.png)

**説明**

このイベントは、nx_packet_pool_info_get を使用したパケット プール情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: パケット プールへのポインター
- 情報フィールド 2: 合計パケット数
- 情報フィールド 3: 使用可能なパケット数
- 情報フィールド 4: 空の要求

### <a name="packet-release"></a>パケット解放 

#### <a name="nx_packet_data_release"></a>nx_packet_data_release

**アイコン** ![パケット解放アイコン](./media/user-guide/netx-events/image117.png)

**説明**

このイベントは、nx_packet_release を使用したパケット解放を表します。

**情報フィールド**

- 情報フィールド 1: パケットへのポインター
- 情報フィールド 2: パケットの状態
- 情報フィールド 3: 使用可能なパケット数
- 情報フィールド 4: 使用されていません

### <a name="packet-transmit-release"></a>パケット送信解放 

#### <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release

**アイコン** ![パケット送信解放アイコン](./media/user-guide/netx-events/image118.png)

**説明**

このイベントは、nx_packet_transmit_release を使用した送信パケットの解放を表します。

**情報フィールド**

- 情報フィールド 1: パケットへのポインター
- 情報フィールド 2: パケットの状態
- 情報フィールド 3: 使用可能なパケット数
- 情報フィールド 4: 使用されていません

### <a name="rarp-disable"></a>RARP の無効化 

#### <a name="nx_rarp_disable"></a>nx_rarp_disable

**アイコン** ![R A R P の無効化アイコン](./media/user-guide/netx-events/image119.png)

**説明**

このイベントは、nx_rarp_disable を使用した RARP の無効化を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="rarp-enable"></a>RARP 有効化 

#### <a name="nx_rarp_enable"></a>nx_rarp_enable

**アイコン** ![R A R P 有効化アイコン](./media/user-guide/netx-events/image120.png)

**説明**

このイベントは、nx_rarp_enable を使用した RARP の有効化を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="rarp-information-get"></a>RARP 情報の取得 

#### <a name="nx_rarp_info_get"></a>nx_rarp_info_get

**アイコン** ![R A R P 情報の取得アイコン](./media/user-guide/netx-events/image121.png)

**説明**

nx_rarp_info_get で RARP 情報を取得するイベントです。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 送信された要求
- 情報フィールド 3: 受信した応答
- 情報フィールド 4: 無効な応答

### <a name="system-initialize"></a>システム初期化 

#### <a name="nx_system_initialize"></a>nx_system_initialize

**アイコン** ![システム初期化アイコン](./media/user-guide/netx-events/image122.png)

**説明**

このイベントは、nx_system_initialize を使用した NetX の初期化を表します。

**情報フィールド**

- 情報フィールド 1: 使用されていません
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="tcp-client-socket-bind"></a>TCP クライアント ソケット バインド 

#### <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind

**アイコン** ![T P クライアント ソケット バインド アイコン](./media/user-guide/netx-events/image123.png)

**説明**

このイベントは、nx_tcp_client_socket_bind を介してクライアント ソケットをポートにバインドすることを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: 要求されたポート
- 情報フィールド 4: 待機オプション

### <a name="tcp-client-socket-connect"></a>TCP クライアント ソケット接続 

#### <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect

**アイコン** ![T C P クライアント ソケット接続アイコン](./media/user-guide/netx-events/image124.png)

**説明**

このイベントは、nx_tcp_client_socket_connect を使用したクライアント ソケット接続の確立を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: サーバーの IP アドレス
- 情報フィールド 4: 要求されたサーバー ポート

### <a name="tcp-client-socket-port-get"></a>TCP クライアント ソケット ポートの取得 

#### <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get

**アイコン** ![T C P クライアント ソケット ポートの取得アイコン](./media/user-guide/netx-events/image125.png)

**説明**

このイベントは、nx_tcp_client_socket_port_get を使用したクライアント ソケット ポート番号の取得を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: ポート番号
- 情報フィールド 4: 使用されていません

### <a name="tcp-client-socket-unbind"></a>TCP クライアント ソケットのバインド解除 

#### <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind

**アイコン** ![T C P クライアント ソケットのバインド解除アイコン](./media/user-guide/netx-events/image126.png)

**説明**

このイベントは、nx_tcp_client_socket_unbind を使用した、ソケットに関連付けられているポートのバインド解除を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="tcp-enable"></a>TCP 有効化 

#### <a name="nx_tcp_enable"></a>nx_tcp_enable

**アイコン** ![T C P 有効化アイコン](./media/user-guide/netx-events/image127.png)

**説明**

このイベントは、nx_tcp_enable を使用した TCP の有効化を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

###  <a name="tcp-free-port-find-tcp-free-port-find"></a>TCP 空きポート検索 TCP 空きポート検索 

#### <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find

**アイコン** ![T CP 空きポート検索アイコン](./media/user-guide/netx-events/image128.png)

**説明**

このイベントは、nx_tcp_free_port_find を使用した、TCP 空きポートの検索を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ポート番号検索の開始
- 情報フィールド 3: 空きポート番号
- 情報フィールド 4: 使用されていません

###  <a name="tcp-infomation-get"></a>TCP 情報の取得 

#### <a name="nx_tcp_info_get"></a>nx_tcp_info_get

**アイコン** ![T C P 情報の取得アイコン](./media/user-guide/netx-events/image129.png)

**説明**

このイベントは、nx_tcp_info_get を使用して、指定された IP インスタンスの TCP 情報を取得することを表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 送信されたバイト数
- 情報フィールド 3: 受信したバイト数
- 情報フィールド 4: 無効なパケット数

###  <a name="tcp-server-socket-accept"></a>TCP サーバー ソケットの受け入れ 

#### <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept

**アイコン** ![T C P サーバー ソケットの受け入れアイコン](./media/user-guide/netx-events/image130.png)

**説明**

このイベントは、nx_tcp_server_socket_accept を使用して、アクティブな接続要求を受信した後のサーバー ソケットの設定を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: 待機オプション
- 情報フィールド 4: ソケットの状態

###  <a name="tcp-server-socket-listen"></a>TCP サーバー ソケットのリッスン 

#### <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen

**アイコン** ![T C P サーバー ソケットのリッスン アイコン](./media/user-guide/netx-events/image131.png)

**説明**

このイベントは、nx_tcp_server_socket_listen を使用して、指定された TCP ポートに対するリッスン要求とサーバー ソケットの登録を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: TCP ポート番号
- 情報フィールド 3: ソケットへのポインター
- 情報フィールド 4: キューに入れることができる接続の最大数

###  <a name="tcp-server-socket-relisten"></a>TCP サーバー ソケットの再リッスン 

#### <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten

**アイコン** ![T C P サーバー ソケットの再リッスン アイコン](./media/user-guide/netx-events/image132.png)

**説明**

このイベントは、nx_tcp_server_socket_relisten を使用して、指定された TCP ポート上の既存のリッスン要求に対して別のサーバー ソケットを登録することを表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: TCP ポート番号
- 情報フィールド 3: ソケットへのポインター
- 情報フィールド 4: ソケットの状態

###  <a name="tcp-server-socket-unaccept"></a>TCP サーバー ソケットの受け入れ解除 

#### <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept

**アイコン** ![T C P サーバー ソケットの受け入れ解除アイコン](./media/user-guide/netx-events/image133.png)

**説明**

このイベントは、nx_tcp_server_socket_unaccept を使用して、以前のパッシブ接続を受信するポートとの関連付けからサーバー ソケットを削除することを表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: ソケットの状態
- 情報フィールド 4: 使用されていません

###  <a name="tcp-server-socket-unlisten-tcp-server-socket-unlisten"></a>TCP サーバー ソケットのリッスン解除 TCP サーバー ソケットのリッスン解除 

#### <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten

**アイコン** ![T C P サーバー ソケットのリッスン解除アイコン](./media/user-guide/netx-events/image134.png)

**説明**

このイベントは、nx_tcp_server_socket_unlisten を使用して、指定された TCP ポートに対する前のリッスン要求を削除することを表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: TCP ポート番号
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="tcp-socket-bytes-available"></a>使用可能な TCP ソケット バイト数 

#### <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available

**アイコン** ![使用可能な T C P ソケット バイト数アイコン](./media/user-guide/netx-events/image135.png)

**説明**

このイベントは、nx_tcp_socket_bytes_available を使用して、指定された TCP 受信ソケットで現在使用できるバイト数を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: TCP ソケットへのポインター
- 情報フィールド 3: ソケットで受信したバイト数
- 情報フィールド 4: 使用されていません

### <a name="tcp-socket-create"></a>TCP ソケットの作成 

#### <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create

**アイコン** ![T C P ソケットの作成アイコン](./media/user-guide/netx-events/image136.png)

**説明**

このイベントは、nx_tcp_socket_create を使用した TCP ソケットの作成を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: サービスの種類
- 情報フィールド 4: 受信ウィンドウのサイズ

### <a name="tcp-socket-delete"></a>TCP ソケットの削除 

#### <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete

**アイコン** ![T C P ソケットの削除アイコン](./media/user-guide/netx-events/image137.png)

**説明**

このイベントは、nx_tcp_socket_delete を使用したソケットの削除を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: ソケットの状態
- 情報フィールド 4: 使用されていません

### <a name="tcp-socket-disconnect"></a>TCP ソケットの切断 

#### <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect

**アイコン** ![T C P ソケットの切断アイコン](./media/user-guide/netx-events/image138.png)

**説明**

このイベントは、nx_tcp_socket_disconnect を使用したソケットの切断を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: 待機オプション
- 情報フィールド 4: ソケットの状態

### <a name="tcp-socket-information-get"></a>TCP ソケット情報の取得 

#### <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get

**アイコン** ![T C P ソケット情報の取得アイコン](./media/user-guide/netx-events/image139.png)

**説明**

このイベントは、nx_tcp_socket_info_get を使用したソケットに関する情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: このソケット経由で送信されたバイト数
- 情報フィールド 4: このソケット経由で受信したバイト数

### <a name="tcp-socket-mss-get"></a>TCP ソケット MSS の取得 

#### <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get

**アイコン** ![T C P ソケット M S S の取得アイコン](./media/user-guide/netx-events/image140.png)

**説明**

このイベントは、nx_tcp_socket_mss_get を使用したソケットの MSS 取得を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: 最大セグメント サイズ (MSS)
- 情報フィールド 4: ソケットの状態

### <a name="tcp-socket-mss-peer-get"></a>TCP ソケット MSS ピアの取得 

#### <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get

**アイコン** ![T C P ソケット M S S ピアの取得アイコン](./media/user-guide/netx-events/image141.png)

**説明**

このイベントは、nx_tcp_socket_mss_peer_get を使用して、ソケットのピアの MSS 値を取得することを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: ピアの MSS
- 情報フィールド 4: ソケットの状態

### <a name="tcp-socket-mss-set"></a>TCP ソケット MSS の設定 

#### <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set

**アイコン** ![T C P ソケット M S S の設定アイコン](./media/user-guide/netx-events/image142.png)

**説明**

このイベントは、nx_tcp_socket_mss_set を使用したソケットの MSS 設定を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: MSS
- 情報フィールド 4: ソケットの状態

### <a name="tcp-socket-peer-info-get"></a>TCP ソケット ピア情報の取得 

#### <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get

**アイコン** ![T C P ソケット ピア情報の取得アイコン](./media/user-guide/netx-events/image143.png)

**説明**

このイベントは、nx_tcp_socket_peer_info_get を使用して、ピア (接続ホストなど) の IP アドレスとポートについて TCP ソケットから取得された情報を表します。

**情報フィールド**

- 情報フィールド 1: TCP ソケットへのポインター
- 情報フィールド 2: ピア IP アドレス
- 情報フィールド 3: ピア ポート番号
- 情報フィールド 4: 使用されていません

### <a name="tcp-socket-receive"></a>TCP ソケット受信 

#### <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive

**アイコン** ![T C P ソケット受信アイコン](./media/user-guide/netx-events/image144.png)

**説明**

このイベントは、nx_tcp_socket_receive を使用したソケットからのデータ受信を表します。

**情報フィールド**

- 情報フィールド 1: ソケットへのポインター
- 情報フィールド 2: 受信したパケットへのポインター
- 情報フィールド 3: 受信パケット長
- 情報フィールド 4: 受信シーケンス番号

### <a name="tcp-socket-receive-notify"></a>TCP ソケット受信通知 

#### <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify

**アイコン** ![T C P ソケット受信通知アイコン](./media/user-guide/netx-events/image145.png)

**説明**

このイベントは、nx_tcp_socket_receive_notify を使用した、ソケットの受信通知コールバックの登録を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: 受信通知コールバックへのポインター 情報フィールド 4: 使用されていません

### <a name="tcp-socket-send"></a>TCP ソケット送信 

#### <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send

**アイコン** ![T C P ソケット送信アイコン](./media/user-guide/netx-events/image146.png)

**説明**

このイベントは、nx_tcp_socket_send を使用したソケット上のデータの送信を表します。

**情報フィールド**

- 情報フィールド 1: ソケットへのポインター
- 情報フィールド 2: パケットへのポインター
- 情報フィールド 3: パケットの長さ
- 情報フィールド 4: 転送シーケンス番号

### <a name="tcp-socket-state-wait"></a>TCP ソケット状態待機 

#### <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait

**アイコン** ![T C P ソケット状態待機アイコン](./media/user-guide/netx-events/image147.png)

**説明**

このイベントは、nx_tcp_socket_state_wait を使用して、ソケットが特定の状態になるのを待機していることを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: 期待されるソケット状態
- 情報フィールド 4: 前のソケットの状態

### <a name="tcp-socket-transmit-configure"></a>TCP ソケット送信の構成 

#### <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure

**アイコン** ![T C P ソケット送信の構成アイコン](./media/user-guide/netx-events/image148.png)

**説明**

このイベントは、nx_tcp_socket_transmit_configure を使用したソケットの送信オプションの構成を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: 送信キューの深さ
- 情報フィールド 4: タイムアウト値

### <a name="tcp-socket-window-update-notify-set"></a>TCP ソケット ウィンドウ更新通知の設定 

#### <a name="nx_tcp_window_update_notify_set"></a>nx_tcp_window_update_notify_set

**アイコン** ![T C P ソケット ウィンドウ更新通知の設定アイコン](./media/user-guide/netx-events/image149.png)

**説明**

このイベントは、nx_tcp_window_update_notify_set を使用して、リモート ホストの受信ウィンドウが増加したことの通知を受信する TCP ソケットを表します。

**情報フィールド** 

- 情報フィールド 1: TCP ソケットへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="udp-enable"></a>UDP 有効化 

#### <a name="nx_udp_enable"></a>nx_udp_enable

**アイコン** ![U D P 有効化アイコン](./media/user-guide/netx-events/image150.png)

**説明**

このイベントは、nx_udp_enable を使用した UDP の有効化を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 使用されていません
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="udp-free-port-find"></a>UDP 空きポートの検索 

#### <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find

**アイコン** ![U D P 空きポートの検索アイコン](./media/user-guide/netx-events/image151.png)

**説明**

このイベントは、nx_udp_free_port_find を使用した、空き UDP ポートの検索を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 検索の開始ポート
- 情報フィールド 3: 空きポート
- 情報フィールド 4: 使用されていません

### <a name="udp-information-get"></a>UDP 情報の取得 

#### <a name="nx_udp_info_get"></a>nx_udp_info_get

**アイコン** ![U D P 情報の取得アイコン](./media/user-guide/netx-events/image152.png)

**説明**

このイベントは、nx_udp_info_get を使用した情報の取得を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: 送信された UDP バイト数
- 情報フィールド 3: 受信した UDP バイト数
- 情報フィールド 4: 無効なパケット

### <a name="udp-socket-bind"></a>UDP ソケット バインド 

#### <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind

**アイコン** ![U D P ソケット バインド アイコン](./media/user-guide/netx-events/image153.png)

**説明**

このイベントは、nx_udp_socket_bind を使用したポートへの UDP ソケットのバインドを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: ポート番号
- 情報フィールド 4: 待機オプション

### <a name="udp-socket-bytes-available"></a>使用可能な UDP ソケット バイト数 

#### <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available

**アイコン** ![使用可能な U D P ソケット バイト数アイコン](./media/user-guide/netx-events/image154.png)

**説明**

このイベントは、nx_udp_socket_bytes_available を使用して UDP ソケットで受信した現在のバイト数を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: ソケットで受信したバイト数
- 情報フィールド 4: 使用されていません

### <a name="udp-socket-checksum-disable"></a>UDP ソケット チェックサムの無効化 

#### <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable

**アイコン** ![U D P ソケット チェックサムの無効化アイコン](./media/user-guide/netx-events/image155.png)

**説明**

このイベントは、nx_udp_socket_checksum_disable を使用した UDP ソケット上のデータのチェックサムの無効化を表します。

**情報フィールド** 

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="udp-socket-checksum-enable"></a>UDP ソケット チェックサムの有効化 

#### <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable

**アイコン** ![U D P ソケット チェックサムの有効化アイコン](./media/user-guide/netx-events/image156.png)

**説明**

このイベントは、nx_udp_socket_checksum_enable を使用したソケットでのチェックサム処理の有効化を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="udp-socket-create"></a>UDP ソケットの作成 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**アイコン** ![U D P ソケット作成アイコン](./media/user-guide/netx-events/image157.png)

**説明**

このイベントは、nx_udp_socket_create を使用した UDP ソケットの作成を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: サービスの種類
- 情報フィールド 4: 最大受信キュー

### <a name="udp-socket-delete-event"></a>UDP ソケット削除イベント 

#### <a name="nx_udp_socket_delete-event"></a>nx_udp_socket_delete イベント

**アイコン** ![U D P ソケット削除イベント アイコン](./media/user-guide/netx-events/image158.png)

**説明**

このイベントは、nx_udp_socket_delete を使用した UDP ソケットの削除を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="udp-socket-information-get-event"></a>UDP ソケット情報の取得イベント 

#### <a name="nx_udp_socket_info_get-event"></a>nx_udp_socket_info_get イベント

**アイコン** ![U D P ソケット情報の取得イベント アイコン](./media/user-guide/netx-events/image159.png)

**説明**

このイベントは、nx_udp_socket_info_get を使用して UDP ソケットに関する情報の取得を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: ソケット経由で送信されたバイト数
- 情報フィールド 4: ソケット経由で受信したバイト数

### <a name="udp-socket-interface-set"></a>UDP ソケット インターフェイスの設定 

#### <a name="nx_udp_socket_interface_set-event"></a>nx_udp_socket_interface_set イベント

**アイコン** ![U D P ソケット インターフェイスの設定アイコン](./media/user-guide/netx-events/image160.png)

**説明**

このイベントは、nx_udp_socket_interface_set を使用して、指定された UDP ソケットの発信インターフェイスを、指定されたインターフェイスで設定することを表します。

**情報フィールド**

- 情報フィールド 1: UDP ソケットへのポインター
- 情報フィールド 2: ソケットのインターフェイスに対応するインデックス
- 情報フィールド 3: 使用されていません
- 情報フィールド 4: 使用されていません

### <a name="udp-socket-port-get"></a>UDP ソケット ポートの取得 

#### <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get

**アイコン** ![U D P ソケット ポートの取得アイコン](./media/user-guide/netx-events/image161.png)

**説明**

このイベントは、nx_udp_socket_port_get を使用して、指定された UDP ソケットがバインドされている UDP ポートを取得することを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: UDP ソケットへのポインター
- 情報フィールド 3: ポート番号
- 情報フィールド 4: 使用されていません

### <a name="udp-socket-receive"></a>UDP ソケット受信 

#### <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive

**アイコン** ![U D P ソケット受信アイコン](./media/user-guide/netx-events/image162.png)

**説明**

このイベントは、nx_udp_socket_receive を使用して、指定された UDP ソケットの受信データを表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: UDP ソケットへのポインター
- 情報フィールド 3: 受信したパケットへのポインター
- 情報フィールド 4: 受信したパケットのサイズ

### <a name="udp-socket-receive-notify"></a>UDP ソケットの受信通知 

#### <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify

**アイコン** ![U D P ソケットの受信通知アイコン](./media/user-guide/netx-events/image163.png) **説明**

このイベントは、nx_udp_socket_receive_notify を使用した受信通知コールバックの登録を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: 通知関数を受信するポインター 情報フィールド 4: 使用されていません

### <a name="udp-socket-send"></a>UDP ソケット送信 

#### <a name="nx_udp_socket_send"></a>nx_udp_socket_send

**アイコン** ![U D P ソケット送信アイコン](./media/user-guide/netx-events/image164.png)

**説明**

このイベントは、nx_udp_socket_send を使用した、UDP ソケット経由のデータ送信を表します。

**情報フィールド**

- 情報フィールド 1: ソケットへのポインター
- 情報フィールド 2: パケットへのポインター
- 情報フィールド 3: パケット長
- 情報フィールド 4: 宛先 IP アドレス

### <a name="udp-socket-unbind"></a>UDP ソケットのバインド解除 

#### <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind

**アイコン** ![U D P ソケットのバインド解除アイコン](./media/user-guide/netx-events/image165.png)

**説明**

このイベントは、nx_udp_socket_unbind を使用した UDP ポートのソケットとのバインド解除を表します。

**情報フィールド**

- 情報フィールド 1: IP インスタンスへのポインター
- 情報フィールド 2: ソケットへのポインター
- 情報フィールド 3: ポート番号
- 情報フィールド 4: 使用されていません

### <a name="udp-source-extract"></a>UDP ソース抽出 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**アイコン** ![U D P ソース抽出アイコン](./media/user-guide/netx-events/image166.png)

**説明**

このイベントは、nx_udp_source_extract を使用して、受信した UDP パケットの IP アドレスとポート番号を取得することを表します。

**情報フィールド**

- 情報フィールド 1: パケットへのポインター
- 情報フィールド 2: 送信者の IP アドレス
- 情報フィールド 3: 送信者のポート番号
- 情報フィールド 4: 使用されていません