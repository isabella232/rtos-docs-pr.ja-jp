---
title: Azure RTOS ThreadX を理解する
description: 深く組み込まれたアプリケーション向けに特別に設計された高度なリアルタイム オペレーティング システム (RTOS) である Azure ThreadX について説明します。
author: philmea
ms.author: philmea
ms.date: 6/9/2021
ms.service: rtos
ms.topic: overview
ms.custom: contperf-fy21q4
ms.openlocfilehash: 4b6c8df5133f16cf3ed4006c12433ac426453cb5
ms.sourcegitcommit: 62cfdf02628530807f4d9c390d6ab623e2973fee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/05/2021
ms.locfileid: "115178206"
---
# <a name="overview-of-azure-rtos-threadx"></a>Azure RTOS ThreadX の概要

Azure RTOS ThreadX は、Microsoft の高度な商用リアルタイム オペレーティング システム (RTOS) です。 これは、特に深い埋め込み型、リアルタイム、および IoT のアプリケーション向けに設計されています。 Azure RTOS ThreadX では、高度なスケジューリング、通信、同期、タイマー、メモリ管理、および割り込み管理機能が提供されます。 さらに、Azure RTOS ThreadX には、picokernel™ アーキテクチャ、プリエンプションしきい値™ スケジューリング、イベントチェーン™、実行プロファイル、パフォーマンス メトリック、システム イベント トレースなど、優れた機能が多数用意されています。 使いやすさの面でも非常に優れているため、Azure RTOS ThreadX は、最も要件の厳しい埋め込みアプリケーションに最適な選択肢と言えます。 Azure RTOS ThreadX は、コンシューマー デバイス、医療エレクトロニクス、工業用制御機器など、何十億もの幅広い製品に展開されています。

## <a name="threadx-footprint"></a>ThreadX メモリ占有領域

Azure RTOS ThreadX では、命令領域が 2 KB、RAM が 1 KB と非常に小さいため、占有領域を最小限に抑えられます。 この小さいサイズは主に、非階層型の picokernel アーキテクチャと自動スケーリングによって実現されています。 自動スケーリングとは、アプリケーションで使用されるサービス (およびサポート インフラストラクチャ) だけが、リンク時の最終イメージに含めるられることを意味します。

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

## <a name="threadx-execution-speed"></a>ThreadX 実行速度

Azure RTOS ThreadX は、ほとんどの一般的なプロセッサでサブマイクロ秒のコンテキスト切り替えを実現しており、他の商用 RTOS よりも全体的に高速です。 高速なだけでなく、Azure RTOS ThreadX は高度に決定論的です。 200 スレッドが待機している場合でも、1 スレッドだけの場合でも、同様に高速なパフォーマンスを発揮します。

Azure RTOS ThreadX の典型的なパフォーマンス特性を次に示します。

* 高速ブート: Azure RTOS ThreadX は、120 サイクル未満で起動します。
* 基本的なエラー チェックの省略 (オプション): Azure RTOS ThreadX の基本的なエラー チェックは、コンパイル時にスキップできます。 これは、アプリケーション コードが検証されていて、各パラメーターに対するエラー チェックがそれ以上必要ない場合に便利です。 エラー チェックのスキップは、システム全体ではなく、コンパイル単位で実行できる点に注意してください。
* picokernel 設計: サービスは相互に階層化されていないため、不要な関数呼び出しによるオーバーヘッドが発生しません。
* 最適化された割り込み処理: プリエンプションが必要でない限り、ISR の開始/終了によって保存/復元されるのは、スクラッチ レジスタだけです。
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

    **パフォーマンスの数値は、200 MHz で実行されている典型的なプロセッサに基づいたものです*。

## <a name="advanced-technology"></a>高度なテクノロジ

Azure RTOS ThreadX のプリエプションしきい値のスケジューリングは非常に優れています。 この機能は Azure RTOS ThreadX に固有のものであり、広範な学術研究の対象となってきたものです。 詳細については、「[Scheduling Fixed-Priority Tasks with Preemption Threshold (プリエンプションしきい値を使った固定優先度タスクのスケジューリング)](https://ieeexplore.ieee.org/document/811269)」(コンコーディア大学 Yun Wang、ピッツバーグ大学 Manas Saksena 共著) を参照してください。

Azure RTOS ThreadX の主要な機能:

* 完全かつ包括的なマルチタスキング機能
  * スレッド、アプリケーション タイマー、メッセージ キュー、カウント セマフォ、ミューテックス、イベント フラグ、ブロック、およびバイト メモリ プール
* 優先度に基づくプリエンプティブ スケジューリング
* 優先度の柔軟性 – 最大 1024 段階の優先度レベル
* 協調スケジューリング
* プリエンプションしきい値 – Azure RTOS ThreadX に固有の機能。コンテキスト切り替えを減らし、柔軟なスケジューリングを保証するのに役立ちます (学術研究に基づく)
* Azure RTOS ThreadX モジュールによるメモリ保護
* 完全に決定論的
* イベント トレース – 直近の *n* 個のシステム/アプリケーション イベントをキャプチャ
* イベント チェーン – Azure RTOS ThreadX の各通信または同期オブジェクトに対して、アプリケーション固有の "通知" コールバック関数を登録
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

標準の Azure RTOS ThreadX は、多くの場合、非対称マルチプロセッシング (AMP) 方式で使用されます。この方式では、Azure RTOS ThreadX とアプリケーション (または Linux) の個別のコピーが各コアで実行され、共有メモリまたは OpenAMP などのプロセッサ間通信メカニズム (Azure RTOS ThreadX では OpenAMP がサポートされています) を介して、相互の通信が行われます。

プロセッサの読み込みが高度に動的な環境では、次のプロセッサ ファミリで Azure RTOS ThreadX 対称型マルチプロセッシング (SMP) を使用できます。

* ARM Cortex-Ax
* ARM Cortex-Rx
* ARM Cortex-A5x 64 ビット
* MIPS 34 K、1004 K、および interAptiv
* PowerPC
* Synopsys ARC HS
* x86

Azure RTOS ThreadX SMP は *n* 個のプロセッサ間で動的負荷分散を実行します。 これにより、すべての Azure RTOS ThreadX リソース (キュー、セマフォ、イベント フラグ、メモリ プールなど) は、コア上の任意のスレッドからアクセスすることができます。 Azure RTOS ThreadX SMP では、すべてのコアで完全な Azure RTOS ThreadX API が有効になり、SMP の操作に対して、次の新しい API が導入されます。

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a>Azure RTOS ThreadX モジュールによるメモリ保護

Azure RTOS ThreadX モジュールと呼ばれるアドオン製品を使用すると、1 つ以上のアプリケーション スレッドを "モジュール" にバンドルし、それをターゲットで動的に読み込んで実行 (またはインプレース実行) することができます。

モジュールを使用して、フィールドのアップグレード、バグの修正、およびプログラムのパーティション分割を行えば、大規模なアプリケーションでのメモリ使用を、アクティブなスレッドに必要な分だけに抑えることができます。

モジュールには、Azure RTOS ThreadX 自体から分離されたアドレス空間もあります。 これにより、Azure RTOS ThreadX ではモジュールの周囲にメモリ保護 (MPU または MMU を使用) を配置できるようになっているので、モジュールの外部からの偶発的なアクセスによって、他のソフトウェア コンポーネントが破損するのを防止できます。

## <a name="misra-compliant"></a>MISRA 準拠

Azure RTOS ThreadX と Azure RTOS ThreadX SMP のソース コードは、MISRA-C: 2004 と MISRA C:2012 に準拠しています。 MISRA C は、C プログラミング言語を使用した重要なシステム用の一連のプログラミング ガイドラインです。 元の MISRA C ガイドラインは主に自動車アプリケーションを対象としていましたが、今では MISRA C は安全性が重要な任意のアプリケーションに適用可能なものとして広く認識されています。 Azure RTOS ThreadX は、MISRA-C: 2004 と MISRA C:2012 のすべての必要規則と必須規則に準拠しています。

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Misra 認定":::

## <a name="supports-most-popular-tools"></a>最も一般的なツールをサポート

Azure RTOS ThreadX では、一般的な埋め込み開発ツールのほとんどがサポートされています。これには、最も包括的な Azure RTOS ThreadX カーネル認識が利用できる、IAR のEmbedded Workbench も含まれています。 その他のツール統合としては、GNU (GCC)、ARM DS-5/uVision®、Green Hills MULTI®、Wind River Workbench、Imagination Codescape、Renesas e2studio、Metaware SeeCode、NXP CodeWarrior、Lauterbach TRACE32®、TI Code-Composer Studio、CrossCore などがサポートされています。

## <a name="adaptation-layer-for-threadx"></a>ThreadX の適合レイヤー

さまざまなレガシ RTOS API (FreeRTOS、POSIX、OSEK など) に ThreadX [適合レイヤー](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers)を使用することで、Azure RTOS へのアプリケーション移行の問題を緩和できます。

> [!div class="nextstepaction"]
> [Azure RTOS ThreadX の概要](chapter1.md)