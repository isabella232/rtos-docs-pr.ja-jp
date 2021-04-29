---
title: Azure RTOS ThreadX を理解する
description: Azure ThreadX は、特に深く組み込まれたアプリケーション向けに設計された高度なリアルタイム オペレーティング システム (RTOS) です。
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: acee58d9c48cb7a66993aaa5dc4a565dfe96234d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812161"
---
# <a name="overview-of-azure-rtos-threadx"></a>Azure RTOS ThreadX の概要

Azure RTOS ThreadX は、深く埋め込まれたリアルタイム IoT アプリケーション向けに特別に設計された、Microsoft の高度な商用リアルタイム オペレーティング システム (RTOS) です。 Azure RTOS ThreadX では、高度なスケジューリング、通信、同期、タイマー、メモリ管理、および割り込み管理機能が提供されます。 さらに、Azure RTOS ThreadX には、picokernel™ アーキテクチャ、プリエンプションしきい値™ スケジューリング、イベントチェーン™、実行プロファイル、パフォーマンス メトリック、システム イベント トレースなど、優れた機能が多数用意されています。 使いやすさの面でも非常に優れているため、Azure RTOS ThreadX は、最も要件の厳しい埋め込みアプリケーションに最適な選択肢と言えます。 2017 年時点で、Azure RTOS ThreadX は、コンシューマー デバイス、医療エレクトロニクス、工業用制御機器など、62 億点以上の幅広い製品に展開されています。

## <a name="api-protocols"></a>API プロトコル

### <a name="azure-rtos-threadx-api"></a>Azure RTOS ThreadX API

* 直感的で一貫性のある API
* 名詞 - 動詞の名前付け規則
* すべての API の先頭を *tx_* にして、Azure RTOS ThreadX として簡単に識別
* ブロックしている API にオプションのスレッド タイムアウトがある
* 多数の API をアプリケーション ISR から直接利用可能

### <a name="azure-rtos-threadx-services"></a>Azure RTOS ThreadX のサービス

* 動的スレッド作成
* スレッド数に制限なし
* 主なスレッド API としては、次のものがあります。
  * tx_thread_create
  * tx_thread_delete
  * tx_thread_preemption_change
  * tx_thread_priority_change
  * tx_thread_relinquish
  * tx_thread_reset
  * tx_thread_resume
  * tx_thread_sleep
  * tx_thread_suspend
  * tx_thread_terminate
  * tx_thread_wait_abort
* 追加情報とパフォーマンス API

### <a name="message-queues"></a>メッセージ キュー

* 動的キュー作成
* キューの数に制限なし
* 値 (またはポインターによる参照) によってコピーされるメッセージ
* メッセージ サイズは 32 ビットの単語で 1 - 16 個
* 空および満杯時におけるオプションでのスレッド中断
* すべての中断時のオプションのタイムアウト
* 主なメッセージ キュー API としては、次のものがあります。
  * tx_queue_create
  * tx_queue_delete
  * tx_queue_flush
  * tx_queue_front_send
  * tx_queue_receive
  * tx_queue_send_notify
* 追加情報とパフォーマンス API

### <a name="counting-semaphores"></a>カウント セマフォ

* 動的セマフォ作成
* セマフォの数に制限なし
* 32 ビット カウント セマフォ (0 から 4,294,967,295)
* コンシューマー プロデューサーまたはリソース保護のサポート
* セマフォが使用できない場合の、オプションでのスレッド中断
* すべての中断時のオプションのタイムアウト
* 主なセマフォ API としては、次のものがあります。
  * tx_semaphore_create
  * tx_semaphore_delete
  * tx_semaphore_get
  * tx_semaphore_put
  * tx_semaphore_put_notify
* 追加情報とパフォーマンス API

### <a name="mutexes"></a>ミューテックス

* 動的ミューテックス作成
* ミューテックスの数に制限なし
* 入れ子になったリソース保護のサポート
* オプションの優先度継承のサポート
* ミューテックスが使用できない場合の、オプションでのスレッド中断
* すべての中断時のオプションのタイムアウト
* 主なミューテックス API としては、次のものがあります。
  * tx_mutex_create
  * tx_mutex_delete
  * tx_mutex_get
  * tx_mutex_put
* 追加情報とパフォーマンス API

### <a name="event-flags"></a>イベント フラグ

* 動的イベント フラグ グループ作成
* イベント フラグ グループの数に制限なし
* 1 つまたは複数のスレッドの同期
* アトミックの取得とクリアのサポート
* AND/OR のイベント セットに対する、オプションでのマルチスレッド中断
* すべての中断時のオプションのタイムアウト
* 主なイベント フラグ API としては、次のものがあります。
  * tx_event_flags_create
  * tx_event_flags_delete
  * tx_event_flags_get
  * tx_event_flags_set
  * tx_event_flags_set_notify
* 追加情報とパフォーマンス API

### <a name="block-memory-pools"></a>ブロック メモリ プール

* 動的ブロック プール作成
* ブロック プールの数に制限なし
* 固定サイズ ブロックのサイズ、またはプールのサイズに制限なし
* きわめて高速なメモリ割り当て/処理配置
* 空のプールに対するオプションでのスレッド中断
* すべての中断時のオプションのタイムアウト
* 主なブロック プール API としては、次のものがあります。
  * tx_block_pool_create
  * tx_block_pool_delete
  * tx_block_allocate
  * tx_block_release
* 追加情報とパフォーマンス API

### <a name="byte-memory-pools"></a>バイト メモリ プール

* 動的バイト プール作成
* バイト プールの数に制限なし
* バイト プールのサイズに制限なし
* きわめて柔軟な可変長メモリ割り当て/割り当て解除
* 割り当てサイズのローカリティのサポート
* 空のプールに対するオプションでのスレッド中断
* すべての中断時のオプションのタイムアウト
* 主なバイト プール API としては、次のものがあります。
  * tx_byte_pool_create
  * tx_byte_pool_delete
  * tx_byte_allocate
  * tx_byte_release
* 追加情報とパフォーマンス API

### <a name="application-timers"></a>アプリケーション タイマー

* 動的タイマーの作成
* タイマーの数に制限なし
* 定期的またはワンショット タイマーのサポート
* 定期的タイマーの初期有効期限に異なる値を設定可能
* タイマーのアクティブ化または非アクティブ化に対する検索なし
* すべてのタイマーは 1 つのハードウェア タイマー割り込みから派生
* 主なタイマー API としては、次のものがあります。
  * tx_timer_create
  * tx_timer_delete
  * tx_timer_activate
  * tx_timer_change
  * tx_timer_deactivate
* 追加情報とパフォーマンス API

### <a name="azure-rtos-threadx-core-scheduler"></a>Azure RTOS ThreadX コア スケジューラ

* 最小限のフットプリント (フラッシュは 2 KB、RAM は 1 KB)
* サブマイクロ秒の高速なコンテキスト切り替え
* スレッド数に関係なく、完全に決定論的
* 優先度に基づく完全なプリエンプティブ スケジューリング
* 32 の既定優先度レベル (オプションで最大 1024 レベル)
* 優先度レベル内での協調スケジューリング (FIFO)
* プリエンプションしきい値テクノロジ
* オプションのタイマー サービス:
  * スレッド単位での、オプションのタイム スライス
  * すべてのブロックに対するオプションのタイムアウト
  * API でハードウェア タイマー割り込みを要求
* 実行プロファイル
* システムレベルのトレース
* 多くの標準に対して認定された安全性

## <a name="most-deployed-rtos"></a>最も多く展開されている RTOS

大手 M2M 市場インテリジェンス企業である VDC Research によると、Azure RTOS ThreadX は全世界で 62 億件以上展開されています。 Azure RTOS ThreadX の人気は、その信頼性、品質、サイズ、パフォーマンス、先進的機能、使いやすさ、および全体的な市場投入時間が高く評価されていることの証明と言えます。

> *「私たちは、会社の設立以来、ワイヤレスおよび IoT 市場における THREADX の成長の軌跡を見てきましたが、THREADX が幅広い業界で導入されていることに、改めて感心しています。」* – VDC Research 取締役副社長 Chris Rommel 氏

## <a name="small-footprint"></a>小さなフットプリント

Azure RTOS ThreadX では、必要な命令領域が 2 KB、RAM が 1 KB と非常に小さいため、フットプリントを最小限に抑えられます。 これは主に、非階層型の picokernel™ アーキテクチャと自動スケーリングによって実現されています。 自動スケーリングとは、アプリケーションで使用されるサービス (およびサポート インフラストラクチャ) だけが、リンク時の最終イメージに含めるられることを意味します。

Azure RTOS ThreadX の典型的なサイズ特性を次に示します。

|Azure RTOS ThreadX のサービス  |典型的なサイズ (バイト単位)  |
|---------|---------|
|コア サービス (必須) |2,000  |
|キュー サービス  |900  |
|イベント フラグ サービス  |900  |
|セマフォ サービス  |450  |
|ミューテックス サービス  |1,200  |
|ブロック メモリ サービス  |550  |
|バイト メモリ サービス  |900  |

## <a name="fast-execution"></a>高速実行

Azure RTOS ThreadX は、ほとんどの一般的なプロセッサでサブマイクロ秒のコンテキスト切り替えを実現しており、他の商用 RTOS よりも全体的にかなり高速です。 高速なだけでなく、Azure RTOS ThreadX は高度に決定論的です。 200 スレッドが待機している場合でも、1 スレッドだけの場合でも、同様に高速なパフォーマンスを発揮します。

Azure RTOS ThreadX の典型的なパフォーマンス特性を次に示します。

* 高速ブート: Azure RTOS ThreadX は、120 サイクル未満で起動します。
* 基本的なエラー チェックの省略 (オプション): Azure RTOS ThreadX の基本的なエラー チェックは、コンパイル時にスキップできます。 これは、アプリケーション コードが検証されていて、各パラメーターに対するエラー チェックがそれ以上必要ない場合に便利です。 これは、システム全体ではなく、コンパイル単位で実行できる点に注意してください。
* picokernel™ 設計: サービスは相互に階層化されていないため、不要な関数呼び出しによるオーバーヘッドが発生しません。
* *最適化された割り込み処理: プリエンプションが必要でない限り、ISR の開始/終了によって保存/復元されるのは、スクラッチ レジスタだけです。
* 最適化された API 処理:

    |Azure RTOS ThreadX のサービス  |サービス時間 (マイクロ秒単位)*  |
    |---------|---------|
    |スレッド中断  |0.6  |
    |スレッド再開  |0.6  |
    |キュー送信  |0.3  |
    |キュー受信  |0.3  |
    |セマフォの取得  |0.2  |
    |セマフォの配置  |0.2  |
    |コンテキスト切り替え  |0.4  |
    |割り込み応答  |0.0 – 0.6  |

    **パフォーマンスの数値は、200MHz で実行されている典型的なプロセッサに基づいたものです*。

## <a name="pre-certified-by-tuv-and-ul-to-many-safety-standards"></a>TUV と UL による多くの安全性標準による事前認定

Azure RTOS ThreadX と Azure RTOS ThreadX SMP は、IEC-61508 SIL 4、IEC-62304 SW セーフティ クラス C、ISO 26262 ASIL D、および EN 50128 に従って、安全性が重要なシステムでの使用が SGS-TUV Saar によって認定されています。 この認定により、「電気、電子、プログラマブル電子安全関連系の機能安全」に関する IEC-61508、IEC-62304、ISO 26262、および EN 50128 の最高の安全性整合性レベルに対応する安全性関連ソフトウェアの開発で Azure RTOS ThreadX と Azure RTOS ThreadX SMP を使用できることが確認されます。 ドイツの SGS-Group と TUV Saarland の共同事業を通じて結成された SGS-TUV Saar は、世界中の安全関連システムのための組み込みソフトウェアのテスト、監査、検証、認定を行う、世界有数の公認された独立系企業になりました。 工業安全規格の IEC 61508 と、それから派生したすべての標準 (IEC-62304、ISO 26262 および EN 50128 を含む) は、電気・電子・プログラマブル電子安全関連の医療機器、プロセス制御システム、工業機械、自動車および鉄道制御システムの機能安全を保証するために使用されます。

:::image type="content" source="media/overview-threadx/partener-logo-sgs-tuv-saar-2.png" alt-text="SGS TUV SAAR 認定":::

Azure RTOS ThreadX と Azure RTOS ThreadX SMP は、プログラム可能なコンポーネント内のソフトウェアに対する UL 60730-1 付属文書 H、CSA E60730-1 付属文書 H、IEC 60730-1 付属文書 H、UL 60335-1 付属文書 R、IEC 60335-1 付属文書 R、UL 1998 の各安全標準に準拠しているものとして UL によって承認されています。 UL は、独立した安全科学のグローバル企業であり、電気の公的な選定からサステナビリティ、再生可能エネルギー、およびナノテクノロジーにおける革新まで、さまざまな安全性ソリューションの革新を 1 世紀以上にわたって専門としてきました。

:::image type="content" source="media/overview-threadx/cru-logo-certification.png" alt-text="UL 認定":::

TUV および UL 認定に関連付けられている成果物 (証明書、安全性マニュアル、テスト レポートなど) は、販売されています。

## <a name="eal4-common-criteria-security-certification"></a>EAL4+ コモン クライテリア セキュリティ認定

Azure RTOS は、EAL4+ のコモン クライテリア セキュリティ認定を達成しました。 評価対象 (TOE) は、Azure RTOS ThreadX、Azure RTOS NetX-Duo、Azure RTOS NetX Secure TLS、および Azure RTOS NetX MQTT です。 これは、深い埋め込み型センサー、デバイス、エッジ ルーター、およびゲートウェイに必要な最も一般的な IoT プロトコルを表します。

:::image type="content" border="false" source="media/overview-threadx/eal-logo-certification.png" alt-text="EAL 認定":::

Azure RTOS セキュリティ認定に使用される IT セキュリティ評価機関は Brightsight BV で、証明機関は SERTIT です。

## <a name="simple-easy-to-use"></a>シンプルで優れた操作性

Azure RTOS ThreadX は、非常に簡単に使用できます。 Azure RTOS ThreadX API は直感的で高機能です。 API 名は、略語や、他の RTOS 製品で一般的な大幅に省略された名前ではなく、実際の言葉で構成されています。 すべての Azure RTOS ThreadX API は、先頭に `tx_` が付き、名詞 - 動詞の名前付け規則に従っています。 さらに、API 全体で機能に一貫性があります。 たとえば、中断を実行するすべての API には、API 用の同様に機能するオプションのタイムアウトがあります。

Azure RTOS ThreadX アプリケーションの構築は簡単です。 アプリケーションで必要なことは、*tx_api.h* を含め、main から `tx_kernel_enter` を呼び出し、`tx_application_define` 関数を定義して 1 つのスレッドを作成し、スレッド エントリ ポイント関数を定義し、Azure RTOS ThreadX ライブラリ (通常は *tx.a*) にリンクするということです。

Azure RTOS ThreadX では、非常に充実した内容のドキュメントが提供されています。 

## <a name="advanced-technology"></a>高度なテクノロジ

Azure RTOS ThreadX は高度なテクノロジであり、その最も注目すべき機能は、プリエンプションしきい値によるスケジューリングです。 この機能は Azure RTOS ThreadX に固有のものであり、広範な学術研究の対象となってきたものです。 例については、「[How to localize reference titles.docx (プリエンプションしきい値を使った固定優先度タスクのスケジューリング)](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf)」(コンコーディア大学 Yun Wang、ピッツバーグ大学 Manas Saksena 共著) を参照してください。

以下に示すのは、Azure RTOS ThreadX の機能です。

* 完全かつ包括的なマルチタスキング機能
  * スレッド、アプリケーション タイマー、メッセージ キュー、カウント セマフォ、ミューテックス、イベント フラグ、ブロックおよびバイト メモリ プール
* 優先度に基づくプリエンプティブ スケジューリング
* 優先度の柔軟性 – 最大 1024 段階の優先度レベル
* 協調スケジューリング
* プリエンプションしきい値™ – Azure RTOS ThreadX に固有の機能。コンテキスト切り替えを減らし、柔軟なスケジューリングを保証するのに役立ちます (学術研究に基づく)
* Azure RTOS ThreadX モジュールによるメモリ保護
* 完全に決定論的
* イベント トレース – 直近の *n* 個のシステム/アプリケーション イベントをキャプチャ
* イベント チェーン™ – Azure RTOS ThreadX の各通信または同期オブジェクトに対して、アプリケーション固有の "通知" コールバック関数を登録
* メモリ保護のオプションを備えた、Azure RTOS ThreadX モジュール
* 実行時パフォーマンス メトリック
  * スレッド再開の数
  * スレッド中断の数
  * 要請されたスレッド プリエンプションの数
  * 非同期スレッド割り込みプリエンプションの数
  * スレッド優先度逆転の数
  * スレッド放棄の数
* 実行プロファイル キット (EPK)
* 個別の割り込みスタック
* 実行時スタック分析
* 最適化されたタイマー割り込み処理

## <a name="multicore-support-amp--smp"></a>マルチコア サポート (AMP と SMP)

標準の Azure RTOS ThreadX は、多くの場合、非対称マルチプロセッシング (AMP) 方式で使用されます。この方式では、Azure RTOS ThreadX とアプリケーション (または Linux) の個別のコピーが各コアで実行され、共有メモリまたは OpenAMP などのプロセッサ間通信メカニズム (Azure RTOS ThreadX では OpenAMP がサポートされています) を介して、相互の通信が行われます。 これは、Azure RTOS ThreadX を使った最も典型的なマルチコア構成であり、アプリケーションがプロセッサを効果的に読み込むことができる場合に、最も効率的に機能します。

プロセッサの読み込みが高度に動的な環境では、次のプロセッサ ファミリで Azure RTOS ThreadX Symetric Multiprocessing (SMP) を使用できます。

* ARM Cortex-Ax
* ARM Cortex-Rx
* ARM Cortex-A5x 64 ビット
* MIPS 34K、1004K、interAptiv
* PowerPC
* Synopsys ARC HS
* x86

Azure RTOS ThreadX SMP では、*n* 個のプロセッサ間で動的な負荷分散が実行されるため、すべての Azure RTOS ThreadX リソース (キュー、セマフォ、イベント フラグ、メモリ プールなど) は、コア上の任意のスレッドからアクセスすることができます。 Azure RTOS ThreadX SMP では、すべてのコアで完全な Azure RTOS ThreadX API が有効になり、SMP の操作に対して、次の新しい API が導入されます。

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a>Azure RTOS ThreadX モジュールによるメモリ保護

Azure RTOS ThreadX モジュールと呼ばれるアドオン製品を使用すると、1 つ以上のアプリケーション スレッドを "モジュール" にバンドルし、それをターゲットで動的に読み込んで実行 (またはインプレース実行) することができます。

モジュールを使用して、フィールドのアップグレード、バグの修正、およびプログラムのパーティション分割を行えば、大規模なアプリケーションでのメモリ使用を、アクティブなスレッドに必要な分だけに抑えることができます。

モジュールには、Azure RTOS ThreadX 自体から完全に分離されたアドレス空間もあります。 これにより、Azure RTOS ThreadX ではモジュールの周囲にメモリ保護 (MPU または MMU を使用) を配置できるようになっているので、モジュールの外部からの偶発的なアクセスによって、他のソフトウェア コンポーネントが破損するのを防止できます。

## <a name="fastest-time-to-market"></a>市場投入までの時間を最短化

Azure RTOS ThreadX は、インストール、習得、使用、デバッグ、検証、認定、保守が簡単です。 その結果、Azure RTOS ThreadX は過去 7 年間、市場投入時間の短縮性において、RTOS 業界をリードしています (Embedded Market Forecasters (EMF) の調査に基づく)。 この調査によると、Azure RTOS ThreadX を使って設計された製品の 70% が、スケジュールどおりに市場に投入されています。これは、他のどの RTOS よりも優れた結果です。

一貫した市場投入まで時間が利点となる理由は、次のとおりです。

* 高品質のドキュメント
* 完全なソース コードを提供
* 使いやすい API
* 包括的かつ高度な機能セット
* 広範なサードパーティ製ツールの統合 – 特に IAR の Embedded Workbench™

## <a name="royalty-free"></a>ロイヤリティ フリー

ソース コードの使用とテストにコストはかかりません。事前にライセンスされたデバイスに展開する場合は、運用環境ライセンスのコストもかかりません。他のすべてのデバイスには、シンプルな年間ライセンスが必要です。

## <a name="full-highest-quality-source-code"></a>最高品質の完全なソース コード

Azure RTOS ThreadX は開発当初から、完全な C ソースコードで配布される、産業用の RTOS として設計されました。 Azure RTOS ThreadX のソース コードは、品質とわかりやすさに一定の基準を設けてきました。 また、ファイルごとに 1 つの関数を使用するという規則により、簡単なソース ナビゲーションが実現されます。

Azure RTOS ThreadX は厳密なコーディング規則に準拠しており、C コードのすべての行に意味のわかるコメントを記述するという要件も設けられていいます。 さらに、Azure RTOS ThreadX のソースは最高クラスの標準で認定を受けています。

## <a name="misra-compliant"></a>MISRA 準拠

Azure RTOS ThreadX と Azure RTOS ThreadX SMP のソース コードは、MISRA-C:2004 と MISRA C:2012 に準拠しています。 MISRA C は、C プログラミング言語を使用した重要なシステム用の一連のプログラミング ガイドラインです。 元の MISRA C ガイドラインは主に自動車アプリケーションを対象としていましたが、今では MISRA C は安全性が重要な任意のアプリケーションに適用可能なものとして広く認識されています。 Azure RTOS ThreadX は、MISRA-C:2004 と MISRA C:2012 のすべての必要規則と必須規則に準拠しています。

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Misra 認定":::

## <a name="supports-most-popular-architectures"></a>最も一般的なアーキテクチャをサポート

Azure RTOS ThreadX は、すぐに利用可能で完全なテストとサポートが実現されている、次のような最も一般的な 32/64 ビットのマイクロプロセッサで動作します。

* Analog Devices: SHARC、Blackfin、CM4xx
* Andes Core: RISC-V
* Ambiqmicro: Apollo MCU
* ARM: ARM7、ARM9、ARM11、Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64 ビット/A7x 64 ビット/R4/R5、TrustZone ARMv8-M
* Cadence: Xtensa、Diamond
* CEVA: PSoC、PSoC 4、PSoC 5、PSoC 6、FM0+、FM3、MF4、WICED WiFi
* Cypress: RISC-V
* EnSilica: eSi-RISC
* Infineon: XMC1000、XMC4000、TriCore
* Intel および Intel FPGA: x36/Pentium、XScale、NIOS II、Cyclone、Arria 10
* Microchip: AVR32、ARM7、ARM9、Cortex-M3/M4/M7、SAM3/4/7/9/A/C/D/E/G/L/SV、PIC24/PIC32
* Microsemi: RISC-V
* NXP: LPC、ARM7、ARM9、PowerPC、68K、i.MX、ColdFire、Kinetis Cortex-M3/M4
* Renesas: SH、HS、V850、RX、RZ、Synergy
* Silicon Labs: EFM32
* Synopsys: ARC 600、700、ARC EM、ARC HS
* ST: STM32、ARM7、ARM9、Cortex-M3/M4/M7
* Tl: C5xxx、C6xxx、Stellaris、Sitara、Tiva-C
* Wave Computing: MIPS32 4K、24K、34K、1004K、MIPS64 5K、microAptiv、interAptiv、proAptiv、M-Class
* Xilinx: MicroBlaze、PowerPC 405、ZYNQ、ZYNQ UltraSCALE

## <a name="supports-most-popular-tools"></a>最も一般的なツールをサポート

Azure RTOS ThreadX では、一般的な埋め込み開発ツールがサポートされています。これには、最も包括的な Azure RTOS ThreadX カーネル認識が利用できる、IAR のEmbedded Workbench™ も含まれています。 その他のツール統合としては、GNU (GCC)、ARM DS-5/uVision®、Green Hills MULTI®、Wind River Workbench™、Imagination Codescape、Renesas e2studio、Metaware SeeCode™、NXP CodeWarrior、Lauterbach TRACE32®、TI Code-Composer Studio、CrossCore などがサポートされています。
