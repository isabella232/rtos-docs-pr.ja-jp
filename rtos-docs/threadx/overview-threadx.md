---
title: Azure RTOS ThreadX を理解する
description: Azure ThreadX は、特に深く組み込まれたアプリケーション向けに設計された高度なリアルタイム オペレーティング システム (RTOS) です。
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: e786e5bf1f434ec9543823dee8784b677a2b371f
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171388"
---
# <a name="overview-of-azure-rtos-threadx"></a>Azure RTOS ThreadX の概要

Azure RTOS ThreadX は、深く埋め込まれたリアルタイム IoT アプリケーション向けに特別に設計された、Microsoft の高度な商用リアルタイム オペレーティング システム (RTOS) です。 Azure RTOS ThreadX では、高度なスケジューリング、通信、同期、タイマー、メモリ管理、および割り込み管理機能が提供されます。 さらに、Azure RTOS ThreadX には、picokernel™ アーキテクチャ、プリエンプションしきい値™ スケジューリング、イベントチェーン™、実行プロファイル、パフォーマンス メトリック、システム イベント トレースなど、優れた機能が多数用意されています。 使いやすさの面でも非常に優れているため、Azure RTOS ThreadX は、最も要件の厳しい埋め込みアプリケーションに最適な選択肢と言えます。 2017 年時点で、Azure RTOS ThreadX は、コンシューマー デバイス、医療エレクトロニクス、工業用制御機器など、62 億点以上の幅広い製品に展開されています。

## <a name="api-protocols"></a>API プロトコル

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
