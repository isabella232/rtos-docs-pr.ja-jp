---
title: チャプター 2 - Azure RTOS NetX のインストールと使用
description: このチャプターでは、高速ネットワーク スタック Azure RTOS NetX のインストール、セットアップ、使用に関するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 80d6ba18f47ad2b017dfa32260c83ba074a6dbac
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810454"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx"></a>チャプター 2 - Azure RTOS NetX のインストールと使用

このチャプターでは、高速ネットワーク スタック Azure RTOS NetX のインストール、セットアップ、使用に関するさまざまな問題について説明します。

## <a name="host-considerations"></a>ホストに関して考慮するべきこと

組み込み開発は通常 Windows または Linux (Unix) ホスト コンピューター上で行います。 アプリケーションは、コンパイルおよびリンクを行い、実行可能ファイルをホストに生成し、ターゲット ハードウェアにダウンロードすると実行できるようになります。

通常、ターゲットのダウンロードは開発ツールのデバッガーから行います。 ダウンロード後は、必要な実行制御機能 (実行、停止、ブレークポイントなど)、メモリおよびプロセッサのレジスタへのアクセスを、デバッガーで提供します。

ほとんどの開発ツールのデバッガーでは、JTAG (IEEE 1149.1) やバックグラウンド デバッグ モード (BDM) などのオンチップ デバッグ (OCD) 接続でターゲット ハードウェアと通信します。 デバッガーでは、インサーキット エミュレーション (ICE) 接続でターゲット ハードウェアと通信することもあります。 OCD 接続と ICE 接続はどちらも、ターゲットの常駐ソフトウェアへの侵入を最小限に抑える堅牢な通信方法です。

ホストで使用するリソースについては、NetX のソース コードは ASCII 形式で目的のホストに送り、ホスト コンピューターのハード ディスクにはおよそ 1 MB の領域が必要です。

## <a name="target-considerations"></a>ターゲットに関して考慮するべきこと

NetX では、ターゲットに 5 - 45 KB のリードオンリー メモリ (ROM) が必要です。 NetX のスレッド スタックと他のグローバル データ構造体のために、ターゲットのランダム アクセス メモリ (RAM) には、それとは別に 1 - 5 KB が必要です。

さらに NetX では、ThreadX タイマー オブジェクト 2 つと ThreadX ミューテックス オブジェクト 1 つを使用する必要があります。 これらの機能は、NetX のプロトコル スタックでの定期的処理とスレッド保護に使用します。

## <a name="product-distribution"></a>製品の配布パッケージ

Azure RTOS NetX は <https://github.com/azure-rtos/netx/> の公開ソース コード リポジトリから入手できます。

次のリストで、リポジトリ内のいくつかの重要ファイルについて説明します:

- ***nx_api.h***: システムの equate、データ構造体、サービスのプロトタイプすべてを含む C 言語のヘッダー ファイル。
- ***nx_port.h***: 各開発ツールおよびターゲット専用のデータ定義とデータ構造体すべてを含む C 言語のヘッダー ファイル。  
- ***demo_netx.c***: 簡単なデモ アプリケーションの C 言語ファイル。
- ***nx.a (または nx.lib)** _: _standard* パッケージと合わせて配布される NetX の C 言語ライブラリのバイナリ バージョン。             |

## <a name="netx-installation"></a>NetX のインストール

NetX をインストールするには、GitHub リポジトリをローカル コンピューターに複製します。 PC に NetX リポジトリの複製を作成する一般的な構文を次に示します:

```c
    git clone https://github.com/azure-rtos/netx
```

または、GitHub メイン ページの **[ダウンロード]** ボタンを使用してリポジトリのコピーをダウンロードすることもできます。

また、オンライン リポジトリのトップ ページから、NetX ライブラリの構築方法の説明を見ることもできます。

> [!IMPORTANT]
> アプリケーション ソフトウェアには、NetX のライブラリ ファイル (通常 ***nx.a** _ または _*_nx.lib_*_) と、C 言語のインクルード ファイル _*_nx_api.h および nx_port.h_** へのアクセスが必要です。 そのためには、開発ツールで適切なパスを設定するか、アプリケーション開発を行う領域にこれらのファイルをコピーします。

## <a name="using-netx"></a>NetX を使用する

NetX を使用するには、アプリケーションのコードのコンパイル時に ***nx_api.h** _ をインクルードし、NetX ライブラリ _*_nx.a_*_ (または _ *_nx.lib_*)* とリンクする必要があります。

NetX アプリケーションの構築に必要な 4 ステップを次に示します:

1. NetX のサービスまたはデータ構造体を使用するすべてのアプリケーションのファイルで ***nx_api.h*** ファイルをインクルードします。
1. _ *_tx_application_define_** 関数またはアプリケーション スレッドから ***nx_system_initialize** _ を呼び出して、NetX システムを初期化します。  
1. ***nx_system_initialize*** を呼び出した後で、IP インスタンスを作成し、必要に応じてアドレス解決プロトコル (ARP) を有効にし、ソケットを有効にします。  
1. アプリケーションのソースをコンパイルし、NetX のランタイム ライブラリ ***nx.a** _ (または _*_nx.lib_**) とリンクします。 作成されたイメージをターゲットにダウンロードして実行できます。

## <a name="troubleshooting"></a>トラブルシューティング

各プラットフォーム用の NetX は、現実のネットワーク上で、またはネットワーク ドライバーをシミュレートして実行する 1 つまたは複数のサンプルと合わせて配布されています。 最初にサンプル システムを実行してみるといいでしょう。

サンプル システムが正常に動作しない場合は、次の操作を実行して問題を絞り込みます:

1. サンプルの実行量を確認します。
2. 新しいアプリケーション スレッドのスタック サイズを増やします。
3. 「構成オプション」セクションに挙げるデバッグ オプションのうち適切なものを使用して、NetX ライブラリを再コンパイルします。
4. **NX_IP** 構造体を調べて、パケットを送信または受信中でないかどうか確認します。
5. 既定のパケット プールを調べて、使用可能なパケットがあるかどうかを確認します。
6. IP 接続が必要なアプリケーションでは、ヘッダーを 4 バイト境界にアラインした ARP パケットと IP パケットが、ネットワーク ドライバーにより供給されていることを確認します。
7. 最近の変更を一時的に無視して、問題が発生または変化するかどうかを確認します。 こうした情報はサポート エンジニアの役に立ちます。

「[カスタマー サポート センター](about-this-guide.md)」トピックで概説する手順に従って、トラブルシューティングのステップで収集した情報を送信します。

## <a name="configuration-options"></a>構成オプション

NetX ライブラリと NetX を使用するアプリケーションを構築する際、いくつかの構成オプションがあります。 構成オプションは、アプリケーションのソース、コマンド ラインまたは ***nx_user.h*** インクルード ファイルで設定できます (特別な指定がある場合を除く)。

> [!IMPORTANT]
> ***nx_user.h** _ で設定するオプションは、_ *NX_INCLUDE_USER_DEFINE_FILE** を設定した上でアプリケーションと NetX ライブラリをビルドする場合にのみ適用されます。

NetX で使用できる構成オプションを以下のセクションに挙げます。

### <a name="system-configuration-options"></a>システムの構成オプション  

| オプション  | 説明  |
|---|---|
| X_DEBUG | このオプションを有効にすると、RAM イーサネット ネットワーク ドライバーのオプションのデバッグ情報を表示します。 |
| NX_DISABLE_ERROR_CHECKING | このオプションを有効にすると、NetX の基本的なエラー チェック用 API を削除してパフォーマンスを高めます。 エラー チェックを無効にしても影響を受けない API の戻りコードは、API 定義に太字で挙げられています。 このオプションは通常アプリケーションのデバッグ後に使用し、パフォーマンスを高めてコード サイズを縮小します。 |
| NX_DRIVER_DEFERRED_PROCESSING | このオプションを有効にすると、ネットワーク ドライバーの遅延パケット処理を有効にします。 これにより、ネットワーク ドライバーでパケットを IP インスタンスに配置し、NetX 内部の IP ヘルパー スレッドから処理ルーチンを呼び出せます。 |
| NX_ENABLE_EXTENDED_NOTIFY_SUPPORT | スタックで、より多くのコールバック フックを有効にします。 これらのコールバック関数は BSD ラッパー レイヤーで使用します。 既定では、このオプションは無効です。 |
| NX_ENABLE_SOURCE_ADDRESS_CHECK | このオプションを有効にすると、受信パケットの送信元アドレスを確認できます。 既定では、このオプションは無効になっています。 |
| NX_LITTLE_ENDIAN | このオプションを有効にすると、リトル エンディアン環境で必要なバイト スワップを実行して、プロトコルのヘッダーを適切なビッグ エンディアン形式にします。 通常、既定値は ***nx_port.h*** に指定されています。 |
| NX_MAX_PHYSICAL_INTERFACES | デバイス上の物理ネットワーク インターフェイスの合計数を指定します。 既定値は 1 であり、***nx_api.h*** に指定されています。 デバイスには少なくとも 1 つの物理インターフェイスが必要です。 ただし、ループバック インターフェイスを除きます。 |
| NX_PHYSICAL_HEADER | フレームの物理ヘッダーのサイズをbyte 単位で指定します。 既定値は 16 であり、***nx_api.h** _ に指定されています (16 は、32 ビット境界にアラインされた通常の 14 バイトのイーサネット フレームに対応する値)。 アプリケーションで既定値を上書きするには、_*_nx_api.h_*_ をインクルードする前に _ *_nx_user.h_* などで値を指定します。* |

### <a name="arp-configuration-options"></a>ARP の構成オプション  

| オプション  | 説明  |
|---|---|
| NX_ARP_DEFEND_BY_REPLY | このオプションを有効にすると、ARP 応答を送信することにより NetX の IP アドレスを維持 (防衛) できます。 |
| NX_ARP_DEFEND_INTERVAL | 競合するアドレスを示す受信 ARP メッセージへの応答として、ARP モジュールが防衛用のパケットを送信する間隔を秒単位で指定します。 |
| NX_ARP_DISABLE_AUTO_ARP_ENTRY | **NX_DISABLE_ARP_AUTO_ENTRY** に名称が変更されました。 現在でもサポートされていますが、新たに開発を行うときは **NX_DISABLE_ARP_AUTO_ENTRY** を使用することを推奨します。
| NX_ARP_EXPIRATION_RATE | ARP エントリの有効期限を秒単位で指定します。 既定値の 0 では ARP エントリが無期限に有効になります。既定値は ***nx_api.h** に指定されています。 アプリケーションで既定値を上書きするには、_ *_nx_api.h_* をインクルードする前に値を指定します。
| NX_ARP_MAC_CHANGE_NOTIFICATION_ENABLE | **NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION** に名称が変更されました。 現在もサポートされていますが、新たに開発を行うときは **NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION** を使用することを推奨します。 |
| NX_ARP_MAX_QUEUE_DEPTH | ARP 応答を待つ間にキューに入れるパケットの最大数を指定します。 既定値は 4 であり、***nx_api.h*** に指定されています。 |
| NX_ARP_MAXIMUM_RETRIES | ARP 応答がない場合に実行する ARP 再試行の最大回数を指定します。 既定値は 18 であり、***nx_api.h** _ に指定されています。 アプリケーションで既定値を上書きするには、_*_nx_api.h_** をインクルードする前に値を指定します。 |
| NX_ARP_UPDATE_RATE | ARP 再試行の間隔を秒単位で指定します。 既定値は 10 で、10 秒を表します。これは ***nx_api.h** _ に指定されています。 アプリケーションで既定値を上書きするには、_*_nx_api.h_** をインクルードする前に値を指定します。 |
| NX_DISABLE_ARP_AUTO_ENTRY | このオプションを有効にすると、ARP キャッシュに ARP 要求の情報を入力しません。 |
| NX_DISABLE_ARP_INFO | このオプションを有効にすると、ARP 情報の収集を無効にします。 |
| NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION | このオプションを有効にすると、MAC アドレスの更新を検出したときに ARP でコールバック通知関数を実行します。 |

### <a name="icmp-configuration-options"></a>ICMP の構成オプション  

| オプション  | 説明  |
|---|---|
| NX_DISABLE_ICMP_INFO | このオプションを有効にすると、ICMP 情報の収集を無効にします。 |
| NX_DISABLE_ICMP_RX_CHECKSUM | 受信した ICMP パケットでの ICMP チェックサムの計算を無効にします。 このオプションは、ネットワーク インターフェイス ドライバーで ICMP チェックサムを検証でき、アプリケーションで IP 断片化機能を使用しない場合に役に立ちます。 既定では、このオプションは無効です。 |
| NX_DISABLE_ICMP_TX_CHECKSUM | 送信する ICMP パケットでの ICMP チェックサムの計算を無効にします。 このオプションは、ネットワーク インターフェイス ドライバーで ICMP チェックサムを計算でき、アプリケーションで IP 断片化機能を使用しない場合に役に立ちます。 既定では、このオプションは無効です。 |

### <a name="igmp-configuration-options"></a>IGMP の構成オプション  

| オプション  | 説明  |
|---|---| 
| NX_DISABLE_IGMP_INFO | このオプションを有効にすると、IGMP 情報の収集を無効にします。 |
| NX_DISABLE_IGMPV2 | このオプションを有効にすると、IGMPv2 のサポートを無効にし、NetX でサポートするのが IGMPv1 のみになります。 既定ではこのオプションは無効です。これは ***nx_api.h*** に指定されています。 |
| NX_MAX_MULTICAST_GROUPS | 参加できるマルチキャスト グループの最大数を指定します。 既定値は 7 であり、***nx_api.h** _ に指定されています。 アプリケーションで既定値を上書きするには、_ *_nx_api.h_* をインクルードする前に値を指定します。 |

### <a name="ip-configuration-options"></a>IP の構成オプション

| オプション  | 説明  |
|---|---|
| NX_DISABLE_FRAGMENTATION | このオプションを有効にすると、IP 断片化と断片の復元ロジックを無効にします。 |
| NX_DISABLE_IP_INFO | このオプションを有効にすると、IP 情報の収集を無効にします。 |
| NX_DISABLE_IP_RX_CHECKSUM | このオプションを有効にすると、受信 IP パケットのチェックサム ロジックを無効にします。 これは、ネットワーク デバイスで IP ヘッダーのチェックサムを検証でき、アプリケーションで IP 断片化を使用しない場合に役に立ちます。 |
| NX_DISABLE_IP_TX_CHECKSUM | このオプションを有効にすると、送信した IP パケットのチェックサム ロジックを無効にします。 これは、処理を実行するネットワーク デバイスが IP ヘッダーのチェックサムを生成でき、アプリケーションで IP 断片化を使用しない場合に役立ちます。 |
| NX_DISABLE_LOOPBACK_INTERFACE | このオプションを有効にすると、NetX で ループバック インターフェイスのサポートを無効にします。 |
| NX_DISABLE_RX_SIZE_CHECKING | このオプションを有効にすると、受信パケットのサイズ確認を無効にします。 |
| NX_ENABLE_IP_STATIC_ROUTING | このオプションを有効にすると、宛先アドレスに特定のネクスト ホップ アドレスを割り当てられる静的 IP ルーティングを有効にします。 既定では、静的 IP ルーティングは無効です。 |
| NX_IP_PERIODIC_RATE | 1 秒あたりの ThreadX タイマー刻み数を指定します。 既定値は ThreadX シンボル **TX_TIMER_TICKS_PER_SECOND** から取得します。既定値は 100 (10 ミリ秒タイマー) です。 他の NetX モジュールは **NX_IP_PERIODIC_RATE*** からタイマーの情報を取得するため、アプリケーションでこの値を変更するときは注意が必要です。 |
| NX_IP_ROUTING_TABLE_SIZE | このオプションを有効にすると、静的 IP ルーティング テーブルのエントリの最大数を設定できます。このテーブルは、送信インターフェイスと、特定の宛先アドレスに対するネクスト ホップ
アドレスのリストです。 既定値は 8 であり、***nx_api.h** に指定されています。このシンボルは _ *NX_ENABLE_IP_STATIC_ROUTING** が有効である場合にのみ使用します。 |

### <a name="packet-configuration-options"></a>パケットの構成オプション  

| オプション  | 説明  |
|---|---|
| NX_DISABLE_PACKET_INFO | このオプションを有効にすると、パケット プール情報の収集を無効にします。 | 
| NX_PACKET_HEADER_PAD | このオプションを有効にすると、NX_PACKET 制御ブロック末尾のパディングを有効にします。 パディングする **ULONG** 型ワード数は **NX_PACKET_HEADER_PAD_SIZE** で指定します。 |
| NX_PACKET_HEADER_PAD_SIZE | NX_PACKET 構造体をパディングする際の **ULONG** 型ワード数を設定します。これにより、パケットのペイロード領域を必要な
アライメントで開始できます。 受信バッファー記述子が NX_PACKET のペイロード領域を直接指定していて、ネットワーク インターフェイス の受信ロジックまたはキャッシュ操作ロジックでバッファーの開始位置を特定のアライメントに合わせる必要がある場合に、この機能が役立ちます。 この値は **NX_PACKET_HEADER_PAD** が有効である場合にのみ有効になります。 |

### <a name="rarp-configuration-options"></a>RARP の構成オプション  

| オプション  | 説明  |
|---|---|
| NX_DISABLE_RARP_INFO | このオプションを有効にすると、RARP 情報の収集を無効にします。 |

### <a name="tcp-configuration-options"></a>TCP の構成オプション

| オプション  | 説明  |
|---|---|
| NX_DISABLE_RESET_DISCONNECT | このオプションを有効にすると、**NX_NO_WAIT** で指定されたタイムアウト時間が経過したときに、接続切断のリセット処理を行いません。 |
| NX_DISABLE_TCP_INFO | このオプションを有効にすると、TCP 情報の収集を無効にします。 |
| NX_DISABLE_TCP_RX_CHECKSUM | このオプションを有効にすると、受信する TCP パケットのチェックサム ロジックを無効にします。 これは、リンク層で信頼性の高いチェックサム処理または CRC 処理ができる場合、またはインターフェイスのドライバーがハードウェアで TCP チェックサムを検証できる場合にのみ役立ちます。 |
| NX_DISABLE_TCP_TX_CHECKSUM | このオプションを有効にすると、TCP パケットを送信するためのチェックサム ロジックを無効にします。 これは、受信ネットワーク ノードで受信 TCP チェックサム ロジックを無効にしている場合、または処理を実行するネットワーク ドライバーで TCP チェックサムを生成できる場合にのみ役立ちます。 |
| NX_ENABLE_TCP_KEEPALIVE | このオプションを有効にすると、TCP keepalive タイマー (オプション) を有効にします。 既定では有効になっていません。 |
| NX_ENABLE_TCP_MSS_CHECKING | このオプションを有効にすると、TCP 接続を受け入れる前にピアの最小 MSS を確認します。 この機能を使用するには、**NX_ENABLE_TCP_MSS_MINIMUM** シンボルを有効にする必要があります。 既定では、このオプションはオフです。 |
NX_ENABLE_TCP_WINDOW_SCALING | TCP アプリケーションのウィンドウ スケーリング オプションを有効にします。 このオプションを有効にすると、TCP 接続処理中にウィンドウ スケーリング オプションをネゴシエートし、アプリケーションで 64 K より大きなウィンドウ サイズを指定できるようになります。 既定では有効になっていません。 |
| NX_MAX_LISTEN_REQUESTS | サーバー リスニング要求の最大数を指定します。 既定値は 10 であり、***nx_api.h** _ に指定されています。 アプリケーションで既定値を上書きするには、_ *_nx_api.h_* をインクルードする前に値を指定します。 |
| NX_TCP_ACK_EVERY_N_PACKETS | ACK を送信するまでに受信する TCP パケットの数を指定します。 **NX_TCP_IMMEDIATE_ACK** が有効なのに **NX_TCP_ACK_EVERY_N_PACKETS** が有効でない場合、後方互換性のためにこの値は自動的に 1 に設定されます。 |
| NX_TCP_ACK_TIMER_RATE | 1 秒をいくつで割った値を、TCP 遅延 ACK 処理のタイマーで用いるシステム タイマー刻み値 (NX_IP_PERIODIC_RATE) として使用するかを指定します。 既定値は 5 で、200 ミリ秒を表します。これは ***nx_tcp.h** _ に指定されています。 アプリケーションで既定値を上書きするには、_*_nx_api.h_** をインクルードする前に値を指定します。 |
| NX_TCP_ENABLE_KEEPALIVE | **NX_ENABLE_TCP_KEEPALIVE** に名称が変更されました。 現在もサポートされていますが、新たに開発を行うときは **NX_ENABLE_TCP_KEEPALIVE** を使用することを推奨します。 |
| NX_TCP_ENABLE_WINDOW_SCALING | **NX_ENABLE_TCP_WINDOW_SCALING** に名称が変更されました。 現在もサポートされていますが、新たに開発を行うときは **NX_ENABLE_TCP_WINDOW_SCALING** を使用することを推奨します。 |
| NX_TCP_FAST_TIMER_RATE | 1 秒をいくつで割った値を、高速 TCP タイマーで用いる NetX タイマー刻み値 (NX_IP_PERIODIC_RATE) として使用するかを指定します。 高速 TCP タイマーは、遅延 ACK タイマーなどのさまざまな TCP タイマーで使用します。 既定値は 10 で、100 ミリ秒を表します。ThreadX タイマーが 10 ミリ秒間隔で進行することを想定しています。 この値は ***nx_tcp.h** _ に指定されています。 アプリケーションで既定値を上書きするには、_*_nx_api.h_** をインクルードする前に値を指定します。 |
| NX_TCP_IMMEDIATE_ACK | このオプションを有効にすると、TCP 即時 ACK 応答処理 (オプション) を有効にします。 このシンボルを有効にした場合と **NX_TCP_ACK_EVERY_N_PACKETS** を 1 に指定した場合は、同じ結果になります。 |
| NX_TCP_KEEPALIVE_INITIAL | Keepalive タイマーを開始するまでに経過する無操作時間を秒単位で指定します。 既定値は 7200 で、2 時間を表します。これは ***nx_tcp.h** _ に指定されています。 アプリケーションで既定値を上書きするには、_*_nx_api.h_** をインクルードする前に値を指定します。 |
| NX_TCP_KEEPALIVE_RETRIES | 接続が途切れたとみなすまでに実行する keepalive 再試行の回数を指定します。 既定値は 10 で、10 回を表します。これは ***nx_tcp.h** _ に指定されています。 アプリケーションで既定値を上書きするには、_ *_nx_api.h_* をインクルードする前に値を指定します。 |
| NX_TCP_KEEPALIVE_RETRY | 接続のもう一方の端が応答していないことを想定して keepalive タイマーを再試行する間隔を秒単位で指定します。 既定値は 75 で、再試行の間隔が 75 秒であることを表します。これは ***nx_tcp.h** _ に指定されています。 アプリケーションで既定値を上書きするには、_ *_nx_api.h_* をインクルードする前に値を指定します。 |
| NX_TCP_MAX_OUT_OF_ORDER_PACKETS | TCP ソケットの受信キューに保持できる異常 TCP パケットの最大数を指定するシンボル。 このシンボルを使用することで TCP 受信ソケットのキューに入れるパケットの最大数を指定し、パケット プールの枯渇を防止できます。 既定ではこのシンボルが無効であるため、TCP ソケットのキューに入る異常パケットの数に上限はありません。 |
| NX_TCP_MAXIMUM_RETRIES | データ送信の再試行を許容する回数を指定します。この回数を超えると接続が途切れたと見なします。 既定値は 10 で、10 回を表します。これは ***nx_tcp.h** _ に指定されています。 アプリケーションで既定値を上書きするには、_*_nx_api.h_** をインクルードする前に値を指定します。 |
| NX_TCP_MAXIMUM_TX_QUEUE | TCP 送信キューの深さの最大値を指定します。この深さに達すると TCP 送信要求を一時停止または拒否します。 既定値は 20 です。これは、どの時点でも最大 20 個までパケットを送信キューに保持できることを意味します。 パケット データの一部または全部に対する ACK を接続のもう一方の端から受信するまで、パケットは送信キューにとどまります。 この定数は ***nx_tcp.h** _ に指定されています。 アプリケーションで既定値を上書きするには _*_nx_api.h_** をインクルードする前に値を指定します。 |
| X_TCP_MSS_CHECKING_ENABLED | **NX_ENABLE_TCP_MSS_CHECKING** に名称が変更されました。 現在もサポートされていますが、新たに開発を行うときは **NX_ENABLE_TCP_MSS_CHECKING** を使用することを推奨します。 |
| NX_TCP_MSS_MINIMUM | NetX TCP モジュールで受け入れる MSS の最小値を指定するシンボル。 この機能は **NX_ENABLE_TCP_MSS_CHECK** により有効になります |
| NX_TCP_RETRY_SHIFT | 再試行間で、再送信のタイムアウト時間がどのように変化するかを指定します。 この値が 0 の場合、最初の再送信とそれ以降の再送信のタイムアウト時間は同じになります。 この値が 1 の場合、再送信を繰り返すたびにタイムアウト時間が 2 倍になります。 この値が 2 の場合、再送信を繰り返すたびにタイムアウト時間が 4 倍になります。 既定値は 0 であり、***nx_tcp.h** _ に指定されています。 アプリケーションで既定値を上書きするには、_*_nx_api.h_** をインクルードする前に値を指定します。 |
| NX_TCP_TRANSMIT_TIMER_RATE| 1 秒をいくつで割った値を、TCP 送信再試行処理のタイマーで用いるシステム タイマー刻み値 (**NX_IP_PERIODIC_RATE**) として使用するかを指定します。 既定値は 1 で、1 秒を表します。これは **_nx_tcp.h_ *_ に指定されています。アプリケーションで既定値を上書きするには、_* _nx_api.h_** をインクルードする前に値を指定します。 |

### <a name="udp-configuration-options"></a>UDP の構成オプション
| オプション  | 説明  |
|---|---|
| NX_DISABLE_UDP_INFO | このオプションを有効にすると、UDP 情報の収集を無効にします。 |
| NX_DISABLE_UDP_RX_CHECKSUM | このオプションを有効にすると、受信 UDP パケットの UDP チェックサムの計算を無効にします。 これは、ネットワーク インターフェイス ドライバーによってハードウェアで UDP ヘッダーのチェックサムを検証でき、アプリケーションで IP 断片化ロジックが有効でない場合に役立ちます。 |
| NX_DISABLE_UDP_TX_CHECKSUM | このオプションを有効にすると、送信 UDP パケットの UDP チェックサムの計算を無効にします。 これは、ネットワーク インターフェイス ドライバーで UDP ヘッダーのチェックサムを計算すること、データを送信する前にその値を IP ヘッダーに挿入することができ、なおかつアプリケーションで IP 断片化ロジックが有効でない場合に役立ちます。 |

## <a name="netx-version-id"></a>NetX のバージョン ID

現在使用している NetX のバージョンは、実行時にユーザーとアプリケーション ソフトウェアのどちらからでも確認できます。 プログラマーは **nx_port.h** ファイルから NetX のバージョンを取得できます。 さらに、このファイルには、対応するポートのバージョン履歴も含まれています。 アプリケーション ソフトウェアでは、**_nx_port.h_** にあるグローバル文字列 **_nx_version_id** を調べることで NetX のバージョンを取得できます。  

アプリケーション ソフトウェアでは、下に示す定数からもリリース情報を取得できます。これらの定数は ***nx_api.h** に定義されています。*

これらの定数では、現在使用している製品のリリースを、名称および製品のメジャーバージョンとマイナーバージョンによって表現します。

```c
#define EL_PRODUCT_NETX

#define NETX_MAJOR_VERSION

#define NETX_MINOR_VERSION
```