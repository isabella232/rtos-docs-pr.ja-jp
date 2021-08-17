---
title: 第 2 章 - Azure RTOS NetX Duo のインストールと使用
description: この章では、高パフォーマンス ネットワーク スタック Azure RTO NetX Duo のインストール、設定、および使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 32a9efaac3c85d415316fba2e9536cc40939f1f6debcbe3e2fa588de613a694d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788832"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo"></a>第 2 章 - Azure RTOS NetX Duo のインストールと使用

この章では、高パフォーマンス ネットワーク スタック Azure RTO NetX Duo のインストール、設定、および使用に関連する、以下のような、さまざまな問題について説明します。 

## <a name="host-considerations"></a>ホストに関する考慮事項

組み込み開発は通常 Windows または Linux (Unix) ホスト コンピューター上で行います。 アプリケーションは、コンパイルおよびリンクを行い、実行可能ファイルをホストに生成し、ターゲット ハードウェアにダウンロードすると実行できるようになります。

通常、ターゲットのダウンロードは、開発ツールのデバッガー内から実行されます。 ダウンロード後、デバッガーは、メモリおよびプロセッサ レジスタへのアクセスだけでなく、ターゲットの実行制御 (移動、停止、ブレークポイントなど) を提供します。

ほとんどの開発ツールのデバッガーでは、JTAG (IEEE 1149.1) やバックグラウンド デバッグ モード (BDM) などのオンチップ デバッグ (OCD) 接続でターゲット ハードウェアと通信します。 また、デバッガーは、インサーキット エミュレーション (ICE) 接続を使用してターゲット ハードウェアと通信します。 OCD 接続と ICE 接続はどちらも、ターゲットの常駐ソフトウェアへの侵入を最小限に抑えた堅牢なソリューションを提供します。

ホスト上で使用されるリソースについては、NetX Duo のソースコードは ASCII 形式で提供され、ホスト コンピューターのハード ディスク上に約 1 MB の空き領域が必要です。

## <a name="target-considerations"></a>ターゲットに関する考慮事項

NetX Duo は、ターゲット上に 5 KB から 45 KB の読み取り専用メモリ (ROM) を必要とします。 また、NetX Duo スレッド スタックおよびその他のグローバル データ構造用に、ターゲットのランダム アクセス メモリ (RAM) がさらに 1 KB から 5 KB 必要です。

さらに、2 つのThreadX タイマー オブジェクトと 1 つの ThreadX ミューテックス オブジェクトを、NetX Duo に使用する必要があります。 これらの機能は、NetX Duo プロトコル スタック内の定期的な処理のニーズとスレッド保護に使用されます。

## <a name="product-distribution"></a>製品の配布

Azure RTOS NetX Duo は、<https://github.com/azure-rtos/netxduo/> のパブリック ソース コード リポジトリから入手できます。

以下は、リポジトリ内のいくつかの重要なファイルの一覧です。

**nx_api.h**  
すべてのシステム等価物、データ構造、およびサービス プロトタイプが含まれる C ヘッダーファイル。

**nx_port** すべての開発ツール、およびターゲット固有のデータ定義とデータ構造が含まれる C ヘッダーファイル。 

**demo_netx .c** 小規模なデモ アプリケーションが含まれる C ファイル。

**nx.a (or nx.lib)**  
標準パッケージと共に配布される NetX C ライブラリのバイナリ バージョン。

## <a name="netx-duo-installation"></a>NetX Duo のインストール

NetX Duo は、GitHub リポジトリをローカル コンピューターに複製することによってインストールされます。 お使いの PC 上に NetX Duo リポジトリの複製を作成するための一般的な構文を次に示します。

```c
    git clone https://github.com/azure-rtos/netxduo
```

GitHub メイン ページ上のダウンロード ボタンを使用して、リポジトリのコピーをダウンロードすることもできます。

また、オンライン リポジトリのフロント ページ上で NetX Duo ライブラリを構築する手順も紹介します。

> [!IMPORTANT]
> *アプリケーション ソフトウェアは、NetX Duo ライブラリ ファイル (通常は **nx.a** または **nx.lib**) と、C インクルード ファイル **nx_api.h および nx_port.h** にアクセスする必要があります。これを行うには、開発ツールの適切なパスを設定するか、これらのファイルをアプリケーション開発領域にコピーします。*

## <a name="using-netx-duo"></a>NetX Duo の使用

NetX Duo は簡単に使用できます。 基本的に、コンパイル中にアプリケーション コードに ***nx_api .h** を追加し、Netx Duo ライブラリ _*_nx.a_*_ (または _ *_nx.lib_*)* とリンクする必要があります。

NetX Duo アプリケーションの構築に必要な 4 つの簡単な手順を次に示します。

| 手順  | 説明  |
|---|---|
|手順&nbsp;1: |***nx_api .h*** ファイルを、NetX Duo サービスまたはデータ構造を使用するすべてのアプリケーション ファイル内に追加します。|
|手順&nbsp;2: |_ *_tx_application_define_** 関数またはアプリケーション スレッドから ***nx_system_initialize** _ を呼び出して、NetX Duo システムを初期化します。|
|手順&nbsp;3: |IP インスタンスを作成し、必要に応じてアドレス解決プロトコル (ARP) を有効にし、***nx_system_initialize*** が呼び出された後、ソケットを有効にします。|
|手順&nbsp;4: |アプリケーション ソースをコンパイルし、NetX Duo ランタイム ライブラリ *** nx. a** _ (または _*_nx.lib_**) とリンクします。 結果のイメージはターゲットにダウンロードして、実行できます。|

## <a name="troubleshooting"></a>トラブルシューティング

各 NetX Duo ポートには、実際のネットワーク上で、またはシミュレートされたネットワーク ドライバーを介して実行される 1 つ以上のデモンストレーションが提供されます。 最初にデモンストレーション システムを実行することをお勧めします。

デモンストレーション システムが正常に実行されない場合は、次の操作を行って、問題を絞り込んでください。

1. 実行中のデモンストレーションの量を確認します。
2. 新しいアプリケーション スレッドのスタック サイズを増やします。
3. [構成オプション] セクションに一覧表示されている適切なデバッグ オプションを使用して、NetX Duo ライブラリを再コンパイルします。
4. NX_IP 構造を調べて、パケットが送信または受信されているかどうかを確認します。
5. 既定のパケット プールを調べて、使用可能なパケットがあるかどうかを確認します。
6. IPv4 または IPv6 接続を必要とするアプリケーションについて、ARP および IP パケットがヘッダーと共に、ネットワーク ドライバーによって 4 バイト境界上で提供されていることを確認します。
7. 最近の変更を一時的にバイパスして、問題が解消または変更するかどうかを確認します。 このような情報は、Microsoft サポート エンジニアにとって有益です。

トラブルシューティング手順で収集した情報を送信するには、12 ページの「必要なもの」に記載されている手順に従ってください。

## <a name="configuration-options"></a>構成オプション

NetX Duo を使用して NetX Duo ライブラリとアプリケーションを構築する場合、構成オプションがいくつかあります。 構成オプションは、アプリケーション ソース内、コマンド ライン上、または ***nx_user.h*** インクルード ファイル内で定義できます (特に指定がない場合)。

> [!NOTE]
> ***nx_user.h** 内で定義されているオプションは、アプリケーションと Netx Duo ライブラリが、定義済み* **NX_INCLUDE_USER_DEFINE_FILE** を使用して構築されている場合にのみ適用されます。*

以下のセクションでは、NetX Duo で使用できる構成オプションについて説明します。 最初に IPv4 と IPv6 の両方に適用される一般的なオプションが示され、その後 IPv6 固有のオプションが続きます。

### <a name="system-configuration-options"></a>システム構成オプション

| オプション  | 説明  |
|---|---|
| NX_ASSERT_FAIL    | アサーションが失敗したときに使用するデバッグ ステートメントを定義するシンボル。                               |
| NX_DEBUG           | 定義すると、RAM イーサネット ネットワーク ドライバーから使用できるオプションの印刷デバッグ情報が有効になります。 |
| NX_DEBUG_PACKET   | 定義すると、RAM イーサネット ネットワーク ドライバー内で使用できるオプションのデバッグ パケット ダンプが有効になります。      |
| NX_DISABLE_ASSERT | 定義すると、ソース コード内のアサート チェックが無効になります。 既定では、このオプションは定義されていません。            |
|NX_DISABLE_ERROR_CHECKING | 定義すると、基本的な NetX Duo エラー チェック API が削除され、パフォーマンスが向上します。 エラー チェックを無効にしても影響を受けない API リターン コードは、API 定義内で太字で表示されます。 この定義は、通常、アプリケーションが十分にデバッグされ、その使用によってパフォーマンスが向上し、コード サイズが減少した後に使用されます。|
|NX_DRIVER_DEFERRED_PROCESSING | 定義すると、ネットワーク ドライバーの遅延パケット処理が有効になります。 これにより、ネットワーク ドライバーは、パケットを IP インスタンス上に配置し、実際の処理ルーチンを NetX Duo 内部 IP ヘルパー スレッドから呼び出すことができます。|
|NX_DUAL_PACKET_POOL_ENABLE | ***NX_ENABLE_DUAL_PACKET_POOL** _ に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_ENABLE_DUAL_PACKET_POOL_** を使用することをお勧めします。|
|NX_ENABLE_DUAL_PACKET_POOL | 定義すると、スタックが、2 つのパケット プールを使用できます。1 つは大きなペイロード サイズ用、もう 1 つはより小さなペイロード サイズ用です。 既定では、このオプションは有効になっていません。|
|NX_ENABLE_EXTENDED_NOTIFY_SUPPORT| 定義すると、スタック内でより多くのコールバック フックが有効になります。 これらのコールバック関数は、BSD ラッパー レイヤーによって使用されます。 既定では、このオプションは定義されていません。|
|NX_ENABLE_INTERFACE_CAPABILITY| 定義すると、インターフェイス デバイス ドライバーが、チェックサム オフロードなどの追加機能情報を指定できます。 既定では、このオプションは定義されていません。|
|NX_ENABLE_SOURCE_ADDRESS_CHECK| このオプションを有効にすると、受信パケットの送信元アドレスを確認できます。 既定では、このオプションは無効になっています。|
| NX_IPSEC_ENABLE  | 定義すると、NetX Duo ライブラリが IPsec 操作をサポートできます。 この機能には、オプションの NetX Duo IPsec モジュールが必要です。 既定では、この機能は有効になっていません。            |
| NX_LITTLE_ENDIAN | このオプションを有効にすると、リトル エンディアン環境で必要なバイト スワップを実行して、プロトコルのヘッダーを適切なビッグ エンディアン形式にします。 通常、既定値は ***nx_port.h*** に指定されています。|
|NX_MAX_PHYSICAL_INTERFACES | デバイス上の物理ネットワーク インターフェイスの合計数を指定します。 既定値は 1 で、***nx_api.h*** 内で定義されてい ます。デバイスには、少なくとも 1 つの物理インターフェイスが必要です。 これにはループバック インターフェイスは含まれないことに注意してください。|
| NX_NAT_ENABLE | 定義すると、NetX Duo は NAT プロセスを使用して構築されます。 既定では、このオプションは定義されていません。|
| NX_PHYSICAL_HEADER  | フレームの物理ヘッダーのサイズをbyte 単位で指定します。 既定値は 16 であり、***nx_api.h** _ に指定されています (16 は、32 ビット境界にアラインされた通常の 14 バイトのイーサネット フレームに対応する値)。 アプリケーションで既定値をオーバーライドするには、_*_nx_api.h_*_ が追加される前に、たとえば _ *_nx_user. h_*.* 内で値を定義します。 |
| NX_PHYSICAL_TRAILER | 物理パケット トレーラーのサイズをバイト単位で指定します。通常、イーサネット CRC などのためのストレージを予約する際に使用されます。既定値は 4 で、***nx_api.h*** 内で定義されています。|

### <a name="arp-configuration-options"></a>ARP 構成オプション

| オプション  | 説明  |
|---|---|
|NX_ARP_DEFEND_BY_REPLY | 定義すると、NetX Duo が ARP 応答を送信することで IP アドレスを保護できます。|
|NX_ARP_DEFEND_INTERVAL| 競合するアドレスを示す受信 ARP メッセージへの応答として、ARP モジュールが防衛用のパケットを送信する間隔を秒単位で指定します。|
|NX_ARP_DISABLE_AUTO_ARP_ENTRY|  ***NX_DISABLE_ARP_AUTO_ENTRY** _ に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_DISABLE_ARP_AUTO_ENTRY_** を使用することをお勧めします。|
|NX_ARP_EXPIRATION_RATE| ARP エントリの有効期限を秒単位で指定します。 既定値の 0 では ARP エントリが無期限に有効になります。既定値は ***nx_api.h** に指定されています。 アプリケーションで既定値をオーバーライドするには、_ *_nx_api.h_** が追加される前に値を定義します。|
|NX_ARP_MAC_CHANGE_NOTIFICATION_ENABLE | ***NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION** _ に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION_** を使用することをお勧めします。|
|NX_ARP_MAX_QUEUE_DEPTH | ARP 応答を待つ間にキューに入れるパケットの最大数を指定します。 既定値は 4 であり、***nx_api.h*** に指定されています。|
|NX_ARP_MAXIMUM_RETRIES | ARP 応答がない場合に実行する ARP 再試行の最大回数を指定します。 既定値は 18 で、***nx_api.h** _ 内で定義されています。 アプリケーションで既定値をオーバーライドするには、_ *_nx_api.h_** が追加される前に値を定義します。|
|NX_ARP_UPDATE_RATE | ARP 再試行の間隔を秒単位で指定します。 既定値は 10 で、10 秒を表し、***nx_api.h** _ 内で定義されています。 アプリケーションで既定値をオーバーライドするには、_ *_nx_api.h_** が追加される前に値を定義します。|
|NX_DISABLE_ARP_AUTO_ENTRY | このオプションを有効にすると、ARP キャッシュに ARP 要求の情報を入力しません。|
|NX_DISABLE_ARP_INFO | このオプションを有効にすると、ARP 情報の収集を無効にします。|
|NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION| このオプションを有効にすると、MAC アドレスの更新を検出したときに ARP でコールバック通知関数を実行します。|

### <a name="icmp-configuration-options"></a>ICMP の構成オプション

| オプション  | 説明  |
|---|---|
|NX_DISABLE_ICMP_INFO| このオプションを有効にすると、ICMP 情報の収集を無効にします。|
|NX_DISABLE_ICMP_RX_CHECKSUM| 定義すると、受信した ICMP パケット上で ICMPv4 と ICMPv6 両方のチェックサム計算が無効になります。 このオプションは、ネットワーク インターフェイス ドライバーが ICMPv4 と ICMPv6 のチェックサムを確認でき、アプリケーションによって IP 断片化機能または IPsec 機能が使用されない場合に便利です。 既定では、このオプションは定義されていません。|
|NX_DISABLE_ICMP_TX_CHECKSUM | 定義すると、送信した ICMP パケット上で ICMPv4 と ICMPv6 両方のチェックサム計算が無効になります。 このオプションは、ネットワーク インターフェイス ドライバーが ICMPv4 と ICMPv6 のチェックサムを計算でき、
アプリケーションによって IP 断片化機能または IPsec 機能が使用されていない場合に便利です。 既定では、このオプションは定義されていません。|
|NX_DISABLE_ICMPV4_ERROR_MESSAGE | 定義すると、NetX Duo が、不適切な形式の IPv4 ヘッダーなどのエラー条件への応答として、ICMPv4 エラー メッセージを送信しません。 既定では、このオプションは定義されていません。|
|NX_DISABLE_ICMPV4_RX_CHECKSUM | 定義すると、受信した ICMP パケット上で ICMPv4 チェックサム計算が無効になります。 このオプションは、 ***NX_DISABLE_ICMP_RX_CHECKSUM*** が定義されている場合に自動的に定義されます。 既定では、このオプションは定義されていません。|
|NX_DISABLE_ICMPv4_RX_CHECKSUM | ***NX_DISABLE_ICMPV4_RX_CHECKSUM** _ に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_DISABLE_ICMPV4_RX_CHECKSUM_** を使用することをお勧めします。|
|NX_DISABLE_ICMPV4_TX_CHECKSUM | 定義すると、送信した ICMP パケット上で ICMPv4 チェックサム計算が無効になります。 このオプションは、***NX_DISABLE_ICMP_TX_CHECKSUM*** が定義されている場合に自動的に定義されます。 既定では、このオプションは定義されていません。|
|NX_DISABLE_ICMPv4_TX_CHECKSUM | ***NX_DISABLE_ICMPV4_TX_CHECKSUM** _ に名前が変更されました。</br>現在もサポートされていますが、新しい設計では、_*_NX_DISABLE_ICMPV4_TX_CHECKSUM_** を使用することをお勧めします。|
|NX_ENABLE_ICMP_ADDRESS_CHECK | 定義すると、ICMP パケットの送信先アドレスが確認されます。 既定では無効になっています。 IP ブロードキャストまたは IP マルチキャスト アドレス宛ての ICMP エコー要求が、警告なしで破棄されます。|

### <a name="igmp-configuration-options"></a>IGMP 構成オプション

| オプション  | 説明  |
|---|---|
|NX_DISABLE_IGMP_INFO | このオプションを有効にすると、IGMP 情報の収集を無効にします。|
|NX_DISABLE_IGMPV2 | 定義すると、IGMPv2 サポートが無効になり、NetX Duo は IGMPv1 のみをサポートするようになります。 既定では、このオプションは設定されておらず、***nx_api.h*** 内で定義されています。|
|NX_MAX_MULTICAST_GROUPS | 参加できるマルチキャスト グループの最大数を指定します。 既定値は 7 であり、***nx_api.h** _ に指定されています。 アプリケーションで既定値をオーバーライドするには、_ *_nx_api.h_** が追加される前に値を定義します。|

### <a name="ip-configuration-options"></a>IP の構成オプション

| オプション  | 説明  |
|---|---|
|NX_DISABLE_FRAGMENTATION | 定義すると、IPv4 と IPv6 両方の断片化および再構築のロジックが無効になります。|
| NX_DISABLE_IPV4     | 定義すると、IPv4 機能が無効になります。 このオプションを使用すると、IPv6 のみをサポートするように NetX Duo を構築できます。 既定では、このオプションは定義されていません。 |
| NX_DISABLE_IP_INFO | このオプションを有効にすると、IP 情報の収集を無効にします。|
|NX_DISABLE_IP_RX_CHECKSUM | 定義すると、受信した IPv4 パケット上でチェックサム ロジックが無効になります。 これは、ネットワーク デバイスが IPv4 チェックサムを確認でき、アプリケーションによる IP 断片化または IPsec の使用が想定されない場合に便利です。|
|NX_DISABLE_IP_TX_CHECKSUM | 定義すると、送信した IPv4 パケット上でチェックサム ロジックが無効になります。 これは、基になるネットワーク デバイスが IPv4 ヘッダー チェックサムを生成でき、アプリケーションによる IP 断片化または IPsec の使用が想定されない場合に便利です。|
|NX_DISABLE_LOOPBACK_INTERFACE | 定義すると、ループバック インターフェイスの NetX Duo サポートが無効になります。|
|NX_DISABLE_RX_SIZE_CHECKING | 定義すると、受信したパケット上でサイズ チェックが無効になります。|
|NX_ENABLE_IP_RAW_PACKET_FILTER | 定義すると、IP 生パケット受信フィルター機能が有効になります。 受信する生 IP パケットの種類をより細かく制御する必要があるアプリケーションが、この機能を使用できます。 IP 生パケット フィルター機能は、BSD 互換性レイヤー内の生ソケット操作もサポートしています。 既定では、このオプションは定義されていません。|
|NX_ENABLE_IP_STATIC_ROUTING | 定義すると、ルーティング先アドレスに特定のネクスト ホップ アドレスを割り当てることができる IPv4 静的ルーティングが有効になります。 既定では、IPv4 静的ルーティングは無効になっています。|
|NX_FRAGMENT_IMMEDIATE_ASSEMBLY | 定義すると、IPv4 と IPv6 の再構築ロジックが、IP フラグメントの受信後すぐに実行可能になります。 既定では、このオプションは定義されていません。|
|NX_IP_MAX_REASSEMBLY_TIME | IPv4 フラグメントと IPv6 フラグメント再構築の最大許容時間を制御するシンボル。 ここで定義されている値によって、***NX_IPV4_MAX_REASSEMBLY_TIME** _ と _*_NX_IPV6_MAX_REASSEMBLY_TIME_** の両方が上書きされることに注意してください。|
|NX_IP_PERIODIC_RATE | 定義すると、1 秒間の ThreadX タイマー ティックの数が指定されます。 既定値は、ThreadX シンボル ***TX_TIMER_TICKS_PER_SECOND** _ から派生し、既定では 100 (10 ミリ秒タイマー) に設定されています。 その他の NetX Duo モジュールは _ *_NX_IP_PERIODIC_RATE_** からタイミング情報を取得するため、アプリケーションでこの値を変更するときは注意が必要です。|
|NX_IP_RAW_MAX_QUEUE_DEPTH | 生パケット受信キューに入れることができる生 IP パケットの数を制御するシンボル。 既定では、値は 20 に設定されています。| 
|NX_IP_ROUTING_TABLE_SIZE | 定義すると、送信インターフェイスの一覧と特定の送信先アドレスのネクスト ホップ アドレスである、IPv4 静的ルーティング テーブル内のエントリの最大数が設定されます。 既定値は 8 で、***nx_api.h** _ 内で定義されています。このシンボルは、_ *_NX_ENABLE_IP_STATIC_ROUTING_** が定義されている場合にのみ使用されます。|
|NX_IPV4_MAX_REASSEMBLY_TIME | IPv4 フラグメント再構築の最大許容時間を制御するシンボル。 この値は、NX_IP_MAX_REASSEMBLY_TIME 内で定義されている値によって上書きされることに注意してください。|

### <a name="packet-configuration-options"></a>パケット構成オプション

| オプション  | 説明  |
|---|---|
|NX_DISABLE_PACKET_CHAIN | 定義すると、パケットチェーンのロジックが無効になります。 既定では、これは定義されていません。|
|NX_DISABLE_PACKET_INFO | 定義すると、パケット プール情報の収集が無効になります。|
|NX_ENABLE_LOW_WATERMARK | 定義すると、NetX Duo パケット プールの低レベルのウォーターマーク機能が有効になります。 アプリケーションにより、低レベルのウォーターマーク値が設定されます。 TCP パケットの受信時に、パケット プールの低レベルのウォーターマークに到達した場合、NetX Duo は警告なしにパケットを解放して破棄し、パケット プールが枯渇するのを防ぎます。 既定では、この機能は有効になっていません。|
|NX_ENABLE_PACKET_DEBUG_INFO | 定義すると、パケット デバッグ情報がログに記録されます。|
|NX_PACKET_ALIGNMENT | 定義すると、パケット ペイロード領域の開始アドレスに対して、アラインメント要件がバイト単位で指定されます。 ***NX_PACKET_HEADER_PAD** _ および _*_NX_PACKET_HEADER_PAD_SIZE_** が廃止され、このオプションに置き換えられました。 既定では、このオプションは 4 に定義され、ペイロード領域の開始アドレスが 4 バイトでアラインされます。|
|NX_PACKET_HEADER_PAD | 定義すると、NX_PACKET コントロール ブロックの末尾へのパディングが有効になります。 埋め込む ULONG ワード数は、***NX_PACKET_HEADER_PAD_SIZE** _ によって定義されます。 このオプションは、_*_NX_PACKET_ALIGNMENT_** によって非推奨になっていることに注意してください。|
|NX_PACKET_HEADER_PAD_SIZE | NX_PACKET 構造に埋め込まれる ULONG ワード数を設定します。これにより、目的の配置でパケット ペイロード領域を開始できます。 この機能は、受信バッファ記述子が NX_PACKET ペイロード領域を直接指し、バッファーの開始アドレスが特定のアライメント要件を満たすことを、ネットワーク インタフェイスの受信ロジックまたはキャッシュ操作ロジックが期待しているときに有効です。 この値は、***NX_PACKET_HEADER_PAD** _ が定義されている場合にのみ有効になります。 このオプションは、_*_NX_PACKET_ALIGNMENT_** によって非推奨になっていることに注意してください。|

### <a name="rarp-configuration-options"></a>RARP 構成オプション

| オプション  | 説明  |
|---|---|
|NX_DISABLE_RARP_INFO | このオプションを有効にすると、RARP 情報の収集を無効にします。|

### <a name="tcp-configuration-options"></a>TCP の構成オプション

| オプション | 説明 |
|---|---|
|NX_DISABLE_RESET_DISCONNECT | このオプションを有効にすると、***NX_NO_WAIT*** で指定されたタイムアウト時間が経過したときに、接続切断のリセット処理を行いません。|
|NX_DISABLE_TCP_INFO | このオプションを有効にすると、TCP 情報の収集を無効にします。|
|NX_DISABLE_TCP_RX_CHECKSUM | 定義すると、受信した TCP パケット上でチェックサム ロジックが無効になります。 これは、リンクレイヤーに信頼性が高いチェックサムまたは CRC 処理がある場合、またはインターフェイス ドライバーがハードウェア内で TCP チェックサムを確認でき、アプリケーションによって IPsec が使用されない場合にのみ便利です。|
|NX_DISABLE_TCP_TX_CHECKSUM | 定義すると、TCP パケットを送信するためのチェックサム ロジックが無効になります。 これは、受信ネットワーク ノードで TCP チェックサム ロジックが無効になっている場合、または基になるネットワーク ドライバーが TCP チェックサムを生成でき、アプリケーションによって IPsec が使用されていない場合にのみ便利です。|
|NX_ENABLE_TCP_KEEPALIVE | このオプションを有効にすると、TCP keepalive タイマー (オプション) を有効にします。 既定の設定は有効になっていません。|
|NX_ENABLE_TCP_MSS_CHECK | 定義すると、TCP 接続を受け入れる前に、最小ピア MSS の検証が有効になります。 この機能を使用するには、***NX_ENABLE_TCP_MSS_MINIMUM*** シンボルを有効にする必要があります。 既定では、このオプションはオフです。|
|NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY| 定義すると、アプリケーションが、TCP 送信キューの深さが最大値を超えていないときに呼び出されるコールバック関数をインストールできます。 このコールバックは、TCP ソケットがさらにデータを送信する準備ができていることを示すものです。 既定では、このオプションは有効になっていません。|
|NX_ENABLE_TCP_WINDOW_SCALING | TCP アプリケーションのウィンドウ スケーリング オプションを有効にします。 定義すると、TCP 接続フェーズ中にウィンドウ スケーリング オプションがネゴシエートされ、アプリケーションによって 64 K を超えるウィンドウ サイズを指定できます。 既定の設定は有効になっていません (定義されていません)。|
|NX_MAX_LISTEN_REQUESTS | サーバー リスニング要求の最大数を指定します。 既定値は 10 であり、***nx_api.h** _ に指定されています。 アプリケーションで既定値をオーバーライドするには、_ *_nx_api.h_** が追加される前に値を定義します。|
|NX_TCP_ACK_EVERY_N_PACKETS | ACK を送信する前に、受信する TCP パケットの数を指定します。 ***NX_TCP_IMMEDIATE_ACK** _ が有効で、_ *_NX_TCP_ACK_EVERY_N_PACKETS_** が有効になっていない場合、この値は、旧バージョンとの互換性のために自動的に 1 に設定されます。|
|NX_TCP_ACK_TIMER_RATE | 1 秒をいくつで割った値を、TCP 遅延 ACK 処理のタイマーで用いるシステム タイマー刻み値 (NX_IP_PERIODIC_RATE) として使用するかを指定します。 既定値は 5 で、200 ミリ秒を表し、***nx_tcp.h** _ 内で定義されています。 アプリケーションで既定値をオーバーライドするには、_ *_nx_api.h_** が追加される前に値を定義します。|
|NX_TCP_ENABLE_KEEPALIVE | ***NX_ENABLE_TCP_KEEPALIVE** _ に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_ENABLE_TCP_KEEPALIVE_** を使用することをお勧めします。|
|NX_TCP_ENABLE_MSS_CHECK | ***NX_ENABLE_TCP_MSS_CHECK** _ に名前が変更されました。現在もサポートされていますが、新しい設計では _ *_NX_ENABLE_TCP_MSS_CHECK_** を使用することをお勧めします。|
|NX_TCP_ENABLE_WINDOW_SCALING | ***NX_ENABLE_TCP_WINDOW_SCALING** _ に名前が変更されました。現在もサポートされていますが、新しい設計では _*_NX_ENABLE_TCP_WINDOW_SCALING_** を使用することをお勧めします。|
|NX_TCP_FAST_TIMER_RATE | 高速 TCP タイマー レート計算のための NetX Duo 内部ティック数 (NX_IP_PERIODIC_RATE) の分割方法を指定します。 高速 TCP タイマーは、遅延 ACK タイマーなど、さまざまな TCP タイマーを駆動するために使用されます。 既定値は 10 で、100 ミリ秒を表します。ThreadX タイマーが 10 ミリ秒間隔で進行することを想定しています。 この値は、***nx_tcp.h** _ 内で定義されています。 アプリケーションで既定値をオーバーライドするには、_ *_nx_api.h_** が追加される前に値を定義します。|
|NX_TCP_IMMEDIATE_ACK| 定義すると、オプションの TCP 即時 ACK 応答処理が有効になります。 このシンボルを定義することは、***NX_TCP_ACK_EVERY_N_PACKETS*** を 1 に定義することと同じです。|
|NX_TCP_KEEPALIVE_INITIAL | Keepalive タイマーを開始するまでに経過する無操作時間を秒単位で指定します。 既定値は 7200 で、2 時間を表し、***nx_tcp.h** _ 内で定義されています。 アプリケーションで既定値をオーバーライドするには、_ *_nx_api.h_** が追加される前に値を定義します。|
|NX_TCP_KEEPALIVE_RETRIES | 接続が途切れたとみなすまでに実行する keepalive 再試行の回数を指定します。 既定値は 10 で、10 回を表します。これは ***nx_tcp.h** _ に指定されています。 アプリケーションで既定値をオーバーライドするには、_ *_nx_api.h_** が追加される前に値を定義します。|
|NX_TCP_KEEPALIVE_RETRY | 接続のもう一方の端が応答していないことを想定して keepalive タイマーを再試行する間隔を秒単位で指定します。 既定値は 75 で、再試行の間隔が 75 秒であることを表します。これは ***nx_tcp.h** _ に指定されています。 アプリケーションで既定値をオーバーライドするには、_ *_nx_api.h_** が追加される前に値を定義します。|
|NX_TCP_MAX_OUT_OF_ORDER_PACKETS | TCP ソケット受信キューに保持できる順不同 TCP パケットの最大数を定義するシンボル。 このシンボルを使用して、TCP 受信ソケット内のキューに入っているパケット数を制限し、パケット プールが枯渇するのを防ぐことができます。 既定ではこのシンボルが無効であるため、TCP ソケットのキューに入る異常パケットの数に上限はありません。|
|NX_TCP_MAXIMUM_RETRIES | データ送信の再試行を許容する回数を指定します。この回数を超えると接続が途切れたと見なします。 既定値は 10 で、10 回を表します。これは ***nx_tcp.h** _ に指定されています。 アプリケーションで既定値をオーバーライドするには、_ *_nx_api.h_** が追加される前に値を定義します。|
|NX_TCP_MAXIMUM_RX_QUEUE | TCP ソケットの最大受信キューを定義するシンボル。 この機能は ***NX_ENABLE_LOW_WATERMARK*** によって有効になります。|
|NX_TCP_MAXIMUM_TX_QUEUE | TCP 送信キューの深さの最大値を指定します。この深さに達すると TCP 送信要求を一時停止または拒否します。 既定値は 20 です。これは、どの時点でも最大 20 個までパケットを送信キューに保持できることを意味します。 パケット データの一部または全部に対する ACK を接続のもう一方の端から受信するまで、パケットは送信キューにとどまります。 この定数は、***nx_tcp. h** _ 内で定義されています。 アプリケーションで既定値をオーバーライドするには、_ *_nx_api.h_** が追加される前に値を定義します。|
|NX_TCP_MSS_MINIMUM | NetX Duo TCP モジュールが受け入れる最小 MSS 値を定義するシンボル。 この機能は、***NX_ENABLE_TCP_MSS_CHECK*** によって有効になります。|
|NX_TCP_QUEUE_DEPTH_UPDATE_NOTIFY_ENABLE | ***NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY** _ に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY_** を使用することをお勧めします。|
|NX_TCP_RETRY_SHIFT | 再試行間で、再送信のタイムアウト時間がどのように変化するかを指定します。 この値が 0 の場合、最初の再送信とそれ以降の再送信のタイムアウト時間は同じになります。 この値が 1 の場合、再送信を繰り返すたびにタイムアウト時間が 2 倍になります。 この値が 2 の場合、再送信を繰り返すたびにタイムアウト時間が 4 倍になります。 既定値は 0 で、***nx_tcp.h** _ 内で定義されています。 アプリケーションで既定値をオーバーライドするには、_ *_nx_api.h_** が追加される前に値を定義します。|
|NX_TCP_TRANSMIT_TIMER_RATE | TCP 送信再試行処理のタイマー レート計算のためのシステム ティック数 (***NX_IP_PERIODIC_RATE** _) の分割方法を指定します。 既定値は 1 で、1 秒を表し、_*_nx_tcp.h_*_ 内で定義されています。 アプリケーションで既定値をオーバーライドするには、_ *_nx_api.h_** が追加される前に値を定義します。|

### <a name="udp-configuration-options"></a>UDP 構成オプション

| オプション  | 説明  |
|---|---|
|NX_DISABLE_UDP_INFO | このオプションを有効にすると、UDP 情報の収集を無効にします。|
|NX_DISABLE_UDP_RX_CHECKSUM | 定義すると、着信 UDP パケット上で UDP チェックサム計算が無効になります。 これは、ネットワーク インターフェイス ドライバーがハードウェア内で UDP ヘッダー チェックサムを確認でき、アプリケーションによって IPsec または IP の断片化ロジックが有効になっていない場合に便利です。|
|NX_DISABLE_UDP_TX_CHECKSUM | 定義すると、発信 UDP パケット上で UDP チェックサム計算が無効になります。 これは、ネットワーク インターフェイス ドライバーが UDP ヘッダー チェック サムを計算して、データを送信する前に IP ヘッド内に値を挿入でき、アプリケーションによって IPsec または IP 断片化ロジックが有効になっていない場合に便利です。|

### <a name="ipv6-options"></a>IPv6 オプション  

| オプション  | 説明  |
|---|---|
| NX_DISABLE_IPV6 | NetX Duo ライブラリの構築時に IPv6 機能を無効にします。 IPv6 を必要としないアプリケーションの場合、これにより、IPv6 をサポートするためのコードや追加のストレージ領域をプルする必要がなくなります。|
|NX_DISABLE_IPV6_PATH_MTU_DISCOVERY | 定義すると、NetX Duo ホスト宛先テーブルのターゲットに対するパス内の最大 MTU を決定するときに使用される、パス MTU 検出が無効になります。 これにより、NetX Duo ホストは、断片化を必要としない最大パケットを送信することができます。 既定では、このオプションが定義されています (パス MTU は無効になっています)。|
|NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY | 定義すると、IPv6 アドレスが変更されたときにコールバック関数を呼び出すことができます。 既定では、このオプションは有効になっていません。|
|NX_ENABLE_IPV6_MULTICAST | 定義すると、IPv6 マルチキャスト参加/脱退関数が有効になります。 既定では、このオプションは有効になっていません。|
|NX_ENABLE_IPV6_PATH_MTU_DISCOVERY | 定義すると、IPv6 パス MTU 検出機能が有効になります。 既定では、このオプションは有効になっていません。|
|NX_IPV6_ADDRESS_CHANGE_NOTIFY_ENABLE | ***NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY** _ に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY_** を使用することをお勧めします。|
|NX_IPV6_DEFAULT_ROUTER_TABLE_SIZE | IPv6 ルーティング テーブル内のエントリの数を指定します。 既定のルーターには少なくとも onS エントリが必要です。 ***nx_api.h*** 内で定義され、既定値は 8 です。|
|NX_IPV6_DESTINATION_TABLE_SIZE | IPv6 宛先テーブル内のエントリの数を指定します。 これには、IPv6 アドレスのネクスト ホップ アドレスに関する情報が格納されます。 ***nx_api.h*** 内で定義され、既定値は 8 です。|
|NX_IPV6_MAX_REASSEMBLY_TIME | IPv6 フラグメント再構築の最大許容時間を制御するシンボル。|
|NX_IPV6_MULTICAST_ENABLE | ***NX_ENABLE_IPV6_MULTICAST** _ に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_ENABLE_IPV6_MULTICAST_** を使用することをお勧めします。|
|NX_IPV6_PREFIX_LIST_TABLE_SIZE | プレフィックス テーブルのサイズを指定します。 プレフィックス情報は、ルーター提供情報から取得され、IPv6 アドレス構成の一部です。 ***nx_api.h*** 内で定義され、既定値は 8 です。|
|NX_IPV6_STATELESS_AUTOCONFIG_CONTROL | 定義すると、NetX Duo がステートレス アドレス自動構成機能を無効にできます。 既定では、このオプションは有効になっていません。|
|NX_MAX_IPV6_ADDRESSES | IPv6 アドレス プール内のエントリの数を指定します。 インターフェイスの構成時、NetX Duo はプールから IPv6 エントリを使用します。 既定では (NX_MAX_PHYSICAL_INTERFACES \* 3) に設定され、各インターフェイスが少なくとも 1 つのリンク ローカル アドレスと 2 つのグローバル アドレスを持つことができます。 IPv6 アドレス プールは、すべてのインターフェイスによって共有されていることに注意してください。|
|NX_PATH_MTU_INCREASE_WAIT_INTERVAL | 宛先テーブル内の特定のターゲットに対するパス MTU をリセットするための待機間隔をタイマー ティックで指定します。 ***NX_DISABLE_IPV6_PATH_MTU_DISCOVERY*** が定義されている場合は、このシンボルを定義しても何の影響もありません。|
|NX_PATH_MTU_INCREASE_WAIT_INTERVAL | 宛先テーブル エントリのパス MTU 値をリセットするための待機間隔を (秒単位で) 指定するシンボル。 ***NX_ENABLE_IPV6_PATH_MTU_DISCOVERY*** が定義されている場合にのみ有効です。 既定では、この値は 600 (秒) に設定されています。|

### <a name="neighbor-cache-configuration-options"></a>近隣キャッシュ構成オプション

| オプション  | 説明  |
|---|---|
|NX_DELAY_FIRST_PROBE_TIME | 古い状態のキャッシュ エントリに対して最初の要請が送信されるまでの遅延を秒単位で指定します。 ***nx_nd_cache.h*** 内で定義され、既定値は 5 です。|
|NX_DISABLE_IPV6_DAD | 定義すると、このオプションによって、IPv6 アドレスの割り当て中に、重複するアドレス検出 (DAD) が無効になります。 アドレスは、手動構成またはステートレス アドレス自動構成によって設定されます。|
|NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES | このオプションは、キャッシュ テーブルがいっぱいになったときに、NetX Duo が、新しいエントリ用の領域を確保するために、古いキャッシュ テーブルのエントリをタイムアウト前に削除するのを防ぎます。 静的なエントリとルーター エントリは削除されません。|
|NX_IPV6_DAD_TRANSMITS | NetX Duo がインターフェイス アドレスを有効とマークする前に送信される近隣要請メッセージの数を指定します。 ***NX_DISABLE_IPV6_DAD** _ が定義されている場合 (DAD は無効)、このオプションを設定しても何の影響もありません。 また、値がゼロ (0) の場合、DAD は無効になりますが、NetX Duo 内の機能はそのまま残ります。 _*_nx_api.h_** 内で定義され、既定値は 3 です。|
|NX_IPV6_DISABLE_PURGE_UNUSED_CACHE_ENTRIES | ***NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES** _ に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES_** を使用することをお勧めします。|
|NX_IPV6_NEIGHBOR_CACHE_SIZE | IPv6 近隣キャッシュ テーブル内のエントリの数を指定します。 ***nx_nd_cache.h*** 内で定義され、既定値は 16 です。|
|NX_MAX_MULTICAST_SOLICIT | IPv6 アドレスと MAC アドレスのマッピングが必要な場合に、IPv6 近隣検出プロトコルの一部として NetX Duo が送信する近隣要請メッセージの数を指定します。 ***nx_nd_cache.h*** 内で定義され、既定値は 3 です。|
|NX_MAX_UNICAST_SOLICIT | 特定の近隣の到達可能性を特定するために NetX Duo が送信する近隣要請メッセージの数を指定します。 ***nx_nd_cache.h*** 内で定義され、既定値は 3 です。|
|NX_ND_MAX_QUEUE_DEPTH | ND キャッシュを解決するためにキューに入れられたパケットの最大数を定義するシンボル。 既定では、このシンボルは 4 に設定されています。|
|NX_REACHABLE_TIME | キャッシュの宛先 IPv6 アドレスからパケットを受信せずに、キャッシュ エントリが到達可能な状態で存在するタイムアウトを秒単位で指定します。 ***nx_nd_cache.h*** 内で定義され、既定値は 30 です。|
|NX_RETRANS_TIMER  | NetX Duo によって送信される要請パケット間の遅延の長さをミリ秒単位で指定します。 ***nx_nd_cache.h*** 内で定義され、既定値は 1000 です。|
| NXDUO_DISABLE_DAD | ***NX_DISABLE_IPV6_DAD** _ に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_DISABLE_IPV6_DAD_** を使用することをお勧めします。|
|NXDUO_DUP_ADDR_DETECT_TRANSMITS | ***NX_IPV6_DAD_TRANSMITS** _  に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_IPV6_DAD_TRANSMITS_** を使用することをお勧めします。|

### <a name="miscellaneous-icmpv6-configuration-options"></a>その他の ICMPv6 構成オプション

| オプション  | 説明  |
|---|---|
|NX_DISABLE_ICMPV6_ERROR_MESSAGE | 定義すると、NetX Duo が、他のホストから受信した問題のあるパケット (ヘッダーの形式が不適切、パケットのヘッダーの種類が非推奨など) に対して、ICMPv6 エラー メッセージを送信しなくなります。|
|NX_DISABLE_ICMPV6_REDIRECT_PROCESS | 定義すると、ICMPv6 リダイレクト パケットの処理が無効になります。 既定では、NetX Duo はリダイレクト メッセージを処理し、ネクスト ホップ IP アドレス情報を使用して宛先テーブルを更新します。|
|NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS | 定義すると、NetX Duo が、IPv6 ルーター公開通知パケット内で受信した情報を処理しなくなります。|
|NX_DISABLE_ICMPV6_ROUTER_SOLICITATION | 定義すると、NetX Duo が、IPv6 ルーター要請メッセージを一定の間隔でルーターに送信しなくなります。|
|NX_DISABLE_ICMPV6_RX_CHECKSUM | 定義すると、受信した ICMP パケット上で ICMPv6 チェックサム計算が無効になります。|
|NX_DISABLE_ICMPv6_RX_CHECKSUM | ***NX_DISABLE_ICMPV6_RX_CHECKSUM** _ に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_DISABLE_CMPV6_RX_CHECKSUM_** を使用することをお勧めします。|
|NX_DISABLE_ICMPV6_TX_CHECKSUM | 定義すると、送信した ICMP パケット上で ICMPv6 チェックサム計算が無効になります。|
|NX_DISABLE_ICMPV6_TX_CHECKSUM | ***NX_DISABLE_ICMPV6_TX_CHECKSUM** _  に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_DISABLE_ICMPV6_TX_CHECKSUM_** を使用することをお勧めします。|
|NX_ICMPV6_MAX_RTR_SOLICITATIONS | ルーターの応答を受信するまでの間に、ホストが送信するルーター要請の最大数を定義します。 応答が受信されない場合、ホストはルーターが存在しないと判断します。 既定値は、3 です。|
|NX_ICMPV6_RTR_SOLICITATION_DELAY | 最初のルーター要請に対する最大遅延時間を秒単位で指定します。|
|NX_ICMPV6_RTR_SOLICITATION_INTERVAL | 2 つのルーター要請メッセージの間隔を指定します。 既定値は 4 ですが、|
|NXDUO_DESTINATION_TABLE_SIZE | ***NX_IPV6_DESTINATION_TABLE_SIZE** _ に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_IPV6_DESTINATION_TABLE_SIZE_** を使用することをお勧めします。|
|NXDUO_DISABLE_ICMPV6_ERROR_MESSAGE | ***NX_DISABLE_ICMPV6_ERROR_MESSAGE** _  に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_DISABLE_ICMPV6_ERROR_MESSAGE_** を使用することをお勧めします。|
|NXDUO_DISABLE_ICMPV6_REDIRECT_PROCESS | ***NX_DISABLE_ICMPV6_REDIRECT_PROCESS** _ に名前が変更されました。 現在もサポートされていますが、新しい設計では、_ *_NX_DISABLE_ICMPV6_REDIRECT_PROCESS_** を使用することをお勧めします|  
|NXDUO_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS| ***NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS** _  に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS_** を使用することをお勧めします。|
|NXDUO_DISABLE_ICMPV6_ROUTER_SOLICITATION | ***NX_DISABLE_ICMPV6_ROUTER_SOLICITATION** _ に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_DISABLE_ICMPV6_ROUTER_SOLICITATION_** を使用することをお勧めします。|
|NXDUO_ICMPV6_MAX_RTR_SOLICITATIONS | ***NX_ICMPV6_MAX_RTR_SOLICITATIONS** _ に名前が変更されました。 現在もサポートされていますが、新しい設計では、_*_NX_ICMPV6_MAX_RTR_SOLICITATIONS_** を使用することをお勧めします。|
|NXDUO_ICMPV6_RTR_SOLICITATION_INTERVAL | ***NX_ICMPV6_RTR_SOLICITATION_INTERVAL** _  に名前が変更されました。 このシンボルは非推奨です。 現在もサポートされていますが、新しい設計では、_ *_NX_ICMPV6_RTR_SOLICITATION_INTERVAL_** を使用することをお勧めします|

## <a name="netx-duo-version-id"></a>NetX Duo バージョン ID

現在のバージョンの NetX Duo は、実行時にユーザーとアプリケーション ソフトウェアの両方で使用できます。 NetX Duo バージョンは、**nx_port .h** ファイルを調べることで入手できます。 加えて、このファイルには、対応するポートのバージョン履歴も含まれています。 アプリケーション ソフトウェアは、_*_nx_port.h_** 内でグローバル文字列 _**_nx_version_id_*_ を調べることで NetX Duo バージョンを取得できます。

アプリケーション ソフトウェアでは、***nx_api.h*** 内で定義されている、次に示す定数からリリース情報を取得することもできます。

これらの定数は、現在の製品リリースを、名前と製品のメジャーおよびマイナー バージョンで識別します。

\#define EL_PRODUCT_NETXDUO  
\#define NETXDUO_MAJOR_VERSION  
\#define NETXDUO_MINOR_VERSION