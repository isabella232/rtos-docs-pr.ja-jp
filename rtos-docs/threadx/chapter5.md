---
title: 第 5 章 - Azure RTOS ThreadX のデバイス ドライバー
description: この章では、Azure RTOS ThreadX のデバイス ドライバーについて説明します。
author: philmea
ms.author: philmea
ms.date: 05/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2432b291f2b3fa7d6d798b8b4c187dd20b97db6b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812173"
---
# <a name="chapter-5---device-drivers-for-azure-rtos-threadx"></a>第 5 章 - Azure RTOS ThreadX のデバイス ドライバー

この章では、Azure RTOS ThreadX のデバイス ドライバーについて説明します。 この章に記載されている情報は、アプリケーション固有のドライバーを作成する開発者を支援することを目的としています。

## <a name="device-driver-introduction"></a>デバイス ドライバーの概要

外部環境との通信は、ほとんどの組み込みアプリケーションの重要な構成要素です。 この通信は、組み込みアプリケーション ソフトウェアがアクセス可能なハードウェア デバイスを介して行われます。 このようなデバイスを管理する役割を担うソフトウェア コンポーネントは、一般に "*デバイス ドライバー*" と呼ばれます。

組み込みのリアルタイム システムのデバイス ドライバーは、本質的にアプリケーションに依存しています。 これには 2 つの主な理由があります。それは、ターゲット ハードウェアが多種多様であることと、リアルタイム アプリケーションに課せられるパフォーマンス要件も同様に広範であることです。 そのため、すべてのアプリケーションの要件を満たすことができる共通のドライバー セットを提供するのは実質的に不可能です。 これらの理由から、この章の情報は、ユーザーが "*既製*" の ThreadX デバイス ドライバーをカスタマイズし、独自のドライバーを作成できるよう支援することを目的としています。

## <a name="driver-functions"></a>ドライバーの機能

ThreadX デバイス ドライバーは、次の 8 つの基本的な機能領域で構成されています。

- **ドライバーの初期化**
- **ドライバー制御**
- **ドライバー アクセス**
- **ドライバーの入力**
- **ドライバーの出力**
- **ドライバーの割り込み**
- **ドライバーの状態**
- **ドライバーの終了**

初期化を除き、ドライバーの各機能領域は省略可能です。 さらに、各領域での正確な処理はデバイス ドライバーに固有です。

### <a name="driver-initialization"></a>ドライバーの初期化
この機能領域は、実際のハードウェア デバイスとドライバーの内部データ構造の初期化を担当します。 初期化が完了するまで、他のドライバー サービスを呼び出すことはできません。

> [!NOTE]
> "*ドライバーの初期化関数コンポーネントは、通常、***tx_application_define** _ 関数または初期化スレッドから呼び出されます。_"

### <a name="driver-control"></a>ドライバー制御

ドライバーが初期化され、操作の準備が整うと、この機能領域が実行時の制御を担当します。 通常、実行時の制御は、基になるハードウェア デバイスの変更で構成されます。 例として、シリアル デバイスのボー レートの変更や、ディスク上の新しいセクターのシークが挙げられます。

### <a name="driver-access"></a>ドライバー アクセス

一部のデバイス ドライバーは、1 つのアプリケーション スレッドからのみ呼び出されます。 このような場合、この機能領域は不要です。 ただし、複数のスレッドがドライバーに同時にアクセスする必要があるアプリケーションでは、デバイス ドライバーに割り当て/解放機能を追加して、対話を制御する必要があります。 代わりに、アプリケーションでセマフォを使用してドライバー アクセスを制御し、ドライバー内の余分なオーバーヘッドや複雑さを回避することもできます。

### <a name="driver-input"></a>ドライバーの入力

この機能領域は、すべてのデバイス入力を担当します。 ドライバーの入力に関連する主な問題には、通常、入力をバッファーする方法と、スレッドがその入力を待機する方法が含まれます。

### <a name="driver-output"></a>ドライバーの出力

この機能領域は、すべてのデバイス出力を担当します。 ドライバーの出力に関連する主な問題には、通常、出力をバッファーする方法と、スレッドが出力の実行を待機する方法が含まれます。

### <a name="driver-interrupts"></a>ドライバーの割り込み

ほとんどのリアルタイム システムでは、デバイスの入力、出力、制御、エラーの各イベントをドライバーに通知するために、ハードウェア割り込みを利用します。 割り込みにより、このような外部イベントに対する応答時間が保証されます。 割り込みの代わりに、ドライバー ソフトウェアで外部ハードウェアを定期的にチェックして、このようなイベントの有無を確認することもできます。 この手法は "*ポーリング*" と呼ばれます。 割り込みに比べてリアルタイム性は劣りますが、リアルタイム性の低いアプリケーションではポーリングが効果的である場合もあります。

### <a name="driver-status"></a>ドライバーの状態

この機能領域は、ドライバー操作に関連する実行時の状態と統計情報を提供する役割を担います。 この機能領域によって管理される情報には、通常、次のものが含まれます。

- デバイスの現在の状態
- 入力バイト数
- 出力バイト数
- デバイスのエラー数

### <a name="driver-termination"></a>ドライバーの終了

この機能領域は省略可能です。 ドライバーや物理ハードウェア デバイスをシャットダウンする必要がある場合にのみ必要となります。 終了後は、再初期化されるまでドライバーを再度呼び出すことはできません。

## <a name="simple-driver-example"></a>簡易ドライバーの例

デバイス ドライバーを記述するための最良の方法は例を使うことです。 この例では、構成レジスタ、入力レジスタ、出力レジスタを備えた単純なシリアル ハードウェア デバイスがドライバーによって想定されます。 この簡易ドライバーの例では、初期化、入力、出力、割り込みの各機能領域を示します。

### <a name="simple-driver-initialization"></a>簡易ドライバーの初期化

簡易ドライバーの ***tx_sdriver_initialize*** 関数により、ドライバーの入出力操作の管理に使用される 2 つのカウント セマフォが作成されます。 入力セマフォは、シリアル ハードウェア デバイスが文字を受信したときに入力 ISR によって設定されます。 そのため、入力セマフォは初期カウントが 0 で作成されます。

一方、出力セマフォは、シリアル ハードウェアの送信レジスタの可用性を示します。 送信レジスタが最初に使用可能であることを示すために値 1 で作成されます。

初期化関数は、入力および出力通知用の低レベルの割り込みベクター ハンドラーをインストールする役割も担います。 他の ThreadX 割り込みサービス ルーチンと同様に、低レベル ハンドラーでは、簡易ドライバーの ISR を呼び出す前に、* **_tx_thread_context_save** _ を呼び出す必要があります。 ドライバーの ISR に制御が戻ったら、低レベル ハンドラーで _*_ _tx_thread_context_restore_** を呼び出す必要があります。

> [!IMPORTANT]
> *初期化は、他のドライバー関数の前に呼び出すことが重要です。 通常、ドライバーの初期化は ***tx_application_define*** から呼び出されます。

```c
VOID tx_sdriver_initialize(VOID)
{
    /* Initialize the two counting semaphores used to control
    the simple driver I/O. */
    tx_semaphore_create(&tx_sdriver_input_semaphore,
                        "simple driver input semaphore", 0);
    tx_semaphore_create(&tx_sdriver_output_semaphore,
                        "simple driver output semaphore", 1);

    /* Setup interrupt vectors for input and output ISRs.
    The initial vector handling should call the ISRs
    defined in this file. */

    /* Configure serial device hardware for RX/TX interrupt
    generation, baud rate, stop bits, etc. */
}
```
**図 9. 簡易ドライバーの初期化**

### <a name="simple-driver-input"></a>簡易ドライバーの入力

簡易ドライバーの入力は、入力セマフォを中心としています。 シリアル デバイスの入力割り込みを受信すると、入力セマフォが設定されます。 1 つ以上のスレッドがドライバーからの文字を待機している場合、待機時間が最も長いスレッドが再開されます。 待機しているスレッドがない場合は、スレッドがドライバー入力関数を呼び出すまで、セマフォは単に設定されたままになります。

簡易ドライバーの入力処理にはいくつかの制限があります。 最も重要なのは、入力文字が破棄される可能性があることです。 この可能性があるのは、前の文字が処理される前に到着した入力文字をバッファーする機能がないためです。 これは、入力文字バッファーを追加することで簡単に処理できます。

> [!NOTE]
> " ***tx_sdriver_input** _ _ 関数を呼び出すことができるのはスレッドだけです。*"

図 10 は、簡易ドライバーの入力に関連するソース コードを示しています。

```c
UCHAR tx_sdriver_input(VOID)
{
  /* Determine if there is a character waiting. If not,
  suspend. */
  tx_semaphore_get(&tx_sdriver_input_semaphore,
  TX_WAIT_FOREVER;

  /* Return character from serial RX hardware register. */
  return(*serial_hardware_input_ptr);
}
  VOID tx_sdriver_input_ISR(VOID)
{
  /* See if an input character notification is pending. */
  if (!tx_sdriver_input_semaphore.tx_semaphore_count)
  {
    /* If not, notify thread of an input character. */
    tx_semaphore_put(&tx_sdriver_input_semaphore);
  }
}
```
**図 10. 簡易ドライバーの入力**

### <a name="simple-driver-output"></a>簡易ドライバーの出力

出力処理では、出力セマフォを利用して、シリアル デバイスの送信レジスタが解放されたことを通知します。 出力文字が実際にデバイスに書き込まれる前に、出力セマフォが取得されます。 これが使用できない場合は、前の送信がまだ完了していません。

出力 ISR は、送信完了割り込みを処理する役割を担います。 出力 ISR の処理では、出力セマフォを設定することによって別の文字の出力を可能にします。

> [!NOTE]
> " ***tx_sdriver_output** _ _ 関数を呼び出すことができるのはスレッドだけです。*"

図 11 は、簡易ドライバーの出力に関連するソース コードを示しています。

```c
VOID tx_sdriver_output(UCHAR alpha)
{
  /* Determine if the hardware is ready to transmit a
  character. If not, suspend until the previous output
  completes. */
  tx_semaphore_get(&tx_sdriver_output_semaphore,
                                          TX_WAIT_FOREVER);

  /* Send the character through the hardware. */
  *serial_hardware_output_ptr = alpha;
}
  
VOID tx_sdriver_output_ISR(VOID)
{
  /* Notify thread last character transmit is
  complete. */
  tx_semaphore_put(&tx_sdriver_output_semaphore);
}
```
**図 11. 簡易ドライバーの出力**

### <a name="simple-driver-shortcomings"></a>簡易ドライバーの欠点

この簡易デバイス ドライバーの例は、ThreadX デバイス ドライバーの基本概念を示しています。 ただし、簡易デバイス ドライバーは、データ バッファリングやオーバーヘッドの問題に対処していないため、実際の ThreadX ドライバーを完全に表しているわけではありません。 次のセクションでは、デバイス ドライバーに関連するより高度な問題について説明します。

## <a name="advanced-driver-issues"></a>ドライバーの高度な問題

前述のように、デバイス ドライバーには、アプリケーションに固有の要件があります。 大量のデータ バッファリングを必要とするアプリケーションもあれば、デバイスの割り込みが高頻度で発生するため、最適化されたドライバー ISR を必要とするアプリケーションもあります。

### <a name="io-buffering"></a>I/O バッファリング

リアルタイム組み込みアプリケーションでのデータ バッファリングには、かなりの計画が必要です。 設計の一部は、基になるハードウェア デバイスによって決まります。 デバイスで基本的なバイト I/O が提供される場合は、単純な循環バッファーが適していると考えられます。 ただし、デバイスでブロック、DMA、またはパケット I/O が提供される場合は、バッファー管理スキームが必要になる可能性があります。

### <a name="circular-byte-buffers"></a>循環バイト バッファー

通常、循環バイト バッファーは、UART のような単純なシリアル ハードウェア デバイスを管理するドライバーで使用されます。 このような場合、2 つの循環バッファー (1 つは入力用、もう 1 つは出力用) が最もよく使用されます。

各循環バイト バッファーは、バイト メモリ領域 (通常は **UCHAR** の配列)、読み取りポインター、書き込みポインターで構成されます。 読み取りポインターと書き込みポインターがバッファー内の同じメモリ位置を参照している場合、バッファーは空と見なされます。 ドライバーの初期化により、読み取りと書き込み両方のバッファーのポインターがバッファーの開始アドレスに設定されます。

### <a name="circular-buffer-input"></a>循環バッファー入力

入力バッファーは、アプリケーションの準備が整う前に到着した文字を保持するために使用されます。 (通常は割り込みサービス ルーチンで) 入力文字を受信すると、その新しい文字がハードウェア デバイスから取得され、書き込みポインターが指す位置の入力バッファーに配置されます。 その後、書き込みポインターはバッファー内の次の位置に進められます。 次の位置がバッファーの末尾を越える場合、書き込みポインターはバッファーの先頭に設定されます。 新しい書き込みポインターが読み取りポインターと同じである場合、書き込みポインターの前進をキャンセルすることによって、キューの満杯状態が処理されます。

ドライバーに対するアプリケーションの入力バイト要求では、まず、入力バッファーの読み取りおよび書き込みポインターが調べられます。 読み取りと書き込みのポインターが同一の場合、バッファーは空です。 読み取りポインターが同じでない場合は、読み取りポインターが指すバイトが入力バッファーからコピーされ、読み取りポインターが次のバッファー位置に進められます。 新しい読み取りポインターがバッファーの末尾を越える場合は、先頭にリセットされます。 図 12 は、循環入力バッファーのロジックを示しています。

```c
UCHAR   tx_input_buffer[MAX_SIZE];
UCHAR   tx_input_write_ptr;
UCHAR   tx_input_read_ptr;

/* Initialization. */
tx_input_write_ptr =    &tx_input_buffer[0];
tx_input_read_ptr =     &tx_input_buffer[0];

/* Input byte ISR... UCHAR alpha has character from device. */
save_ptr = tx_input_write_ptr;
*tx_input_write_ptr++ = alpha;
if (tx_input_write_ptr > &tx_input_buffer[MAX_SIZE-1])
    tx_input_write_ptr = &tx_input_buffer[0]; /* Wrap */
if (tx_input_write_ptr == tx_input_read_ptr)
    tx_input_write_ptr = save_ptr; /* Buffer full */

/* Retrieve input byte from buffer... */
if (tx_input_read_ptr != tx_input_write_ptr)
{
  alpha = *tx_input_read_ptr++;
  if (tx_input_read_ptr > &tx_input_buffer[MAX_SIZE-1])
      tx_input_read_ptr = &tx_input_buffer[0];
}
```
**図 12. 循環入力バッファーのロジック**

> [!NOTE]
> *信頼性の高い動作を実現するために、入力と出力の両方の循環バッファーの読み取りおよび書き込みポインターを操作するときに、割り込みをロックアウトすることが必要な場合があります。 *

### <a name="circular-output-buffer"></a>循環出力バッファー

出力バッファーは、ハードウェア デバイスが前のバイトの送信を終了する前に、出力用に到着した文字を保持するために使用されます。 出力バッファー処理は入力バッファー処理と似ていますが、送信完了割り込み処理によって出力読み取りポインターが操作され、アプリケーションの出力要求で出力書き込みポインターが利用される点が異なります。
それ以外の点では、出力バッファー処理は同じです。 図 13 は、循環出力バッファーのロジックを示しています。

```c
UCHAR   tx_output_buffer[MAX_SIZE];
UCHAR   tx_output_write_ptr;
UCHAR   tx_output_read_ptr;

/* Initialization. */
tx_output_write_ptr = &tx_output_buffer[0];
tx_output_read_ptr = &tx_output_buffer[0];

/* Transmit complete ISR... Device ready to send. */
if (tx_output_read_ptr != tx_output_write_ptr)
{
  *device_reg = *tx_output_read_ptr++;
  if (tx_output_read_reg > &tx_output_buffer[MAX_SIZE-1])
      tx_output_read_ptr = &tx_output_buffer[0];
}

/* Output byte driver service. If device busy, buffer! */
save_ptr = tx_output_write_ptr;
*tx_output_write_ptr++ = alpha;
if (tx_output_write_ptr > &tx_output_buffer[MAX_SIZE-1])
    tx_output_write_ptr = &tx_output_buffer[0]; /* Wrap */
if (tx_output_write_ptr == tx_output_read_ptr)
    tx_output_write_ptr = save_ptr; /* Buffer full! */
```
**図 13. 循環出力バッファーのロジック**

### <a name="buffer-io-management"></a>バッファー I/O の管理

組み込みマイクロプロセッサのパフォーマンスを向上させるために、多くの周辺機器では、ソフトウェアによって提供されるバッファーを使用してデータが送受信されます。 実装によっては、データの個々のパケットを送受信するために複数のバッファーが使用される場合があります。

I/O バッファーのサイズと場所は、アプリケーションやドライバー ソフトウェアによって決定されます。 通常、バッファーはサイズが固定されており、ThreadX ブロック メモリ プール内で管理されます。 図 14 は、一般的な I/O バッファーと、それらの割り当てを管理する ThreadX ブロック メモリ プールを示しています。

```c
typedef struct TX_IO_BUFFER_STRUCT
{
      struct TX_IO_BUFFER_STRUCT *tx_next_packet;
      struct TX_IO_BUFFER_STRUCT *tx_next_buffer;
      UCHAR tx_buffer_area[TX_MAX_BUFFER_SIZE];
} TX_IO_BUFFER;

TX_BLOCK_POOL tx_io_block_pool;

/* Create a pool of I/O buffers. Assume that the pointer
"free_memory_ptr"points to an available memory area that
is 64 KBytes in size. */
tx_block_pool_create(&tx_io_block_pool,
                  "Sample IO Driver Buffer Pool",
                  free_memory_ptr, 0x10000,
                  sizeof(TX_IO_BUFFER));
```

**図 14. I/O バッファー**

### <a name="tx_io_buffer"></a>TX_IO_BUFFER

typedef TX_IO_BUFFER は、2 つのポインターで構成されます。 **tx_next_packet** ポインターは、入力または出力リストで複数のパケットをリンクするために使用されます。 **tx_next_buffer** ポインターは、デバイスからのデータの個々のパケットを構成するバッファーを一緒にリンクするために使用されます。 バッファーがプールから割り当てられるときに、これらのポインターはどちらも NULL に設定されます。 さらに、一部のデバイスでは、実際にデータを格納するバッファー領域の量を示す別のフィールドが必要になる場合があります。

### <a name="buffered-io-advantage"></a>バッファー I/O の利点

バッファー I/O スキームの利点は何でしょうか。 最大の利点は、デバイスのレジスタとアプリケーションのメモリの間でデータがコピーされないことです。 代わりに、ドライバーによって一連のバッファー ポインターがデバイスに提供されます。 物理デバイス I/O では、指定されたバッファー メモリを直接利用します。

プロセッサを使用して情報の入力または出力パケットをコピーすることは非常にコストがかかるので、高スループットの I/O 状況では避ける必要があります。

バッファー I/O アプローチのもう 1 つの利点は、入力と出力のリストに満杯状態がないことです。 どちらのリストにも、使用可能なすべてのバッファーをいつでも配置できます。 これは、この章で前述した単純なバイト循環バッファーとは対照的です。 それぞれ、コンパイル時に決定されたサイズに固定されていました。

### <a name="buffered-driver-responsibilities"></a>バッファー型ドライバーの役割

バッファー型デバイス ドライバーは、I/O バッファーのリンク リストの管理にのみ関与します。 入力バッファー リストは、アプリケーション ソフトウェアの準備が整う前に受信したパケット用に保持されます。 一方、出力バッファー リストは、ハードウェア デバイスが処理できるようになる前に送られてくるパケット用に保持されます。 図 15 は、データ パケットと各パケットを構成するバッファーの単純な入力および出力リンク リストを示しています。

**入力リスト**

![入力リスト](./media/user-guide/input-list.png)

**出力リスト**

![出力リスト](./media/user-guide/output-list.png)

**図 15. 入力と出力のリスト**

アプリケーションは、同じ I/O バッファーを使用するバッファー型ドライバーとやり取りします。 送信時に、アプリケーション ソフトウェアは、送信する 1 つ以上のバッファーをドライバーに提供します。 アプリケーション ソフトウェアが入力を要求すると、ドライバーは I/O バッファーに入力データを返します。

> [!NOTE]
> "*一部のアプリケーションでは、空きバッファーをドライバーからの入力バッファーと交換することをアプリケーションに要求する、ドライバー入力インターフェイスを構築すると役立つ場合があります。これにより、ドライバーの内部でのバッファー割り当て処理が軽減される可能性があります。* "

### <a name="interrupt-management"></a>割り込み管理

一部のアプリケーションでは、デバイスの割り込み頻度により、ISR を C で記述したり、各割り込みで ThreadX と対話したりすることが妨げられる場合があります。 たとえば、中断されたコンテキストの保存と復元に 25 マイクロ秒かかる場合、割り込み頻度が 50 マイクロ秒であるとすると、コンテキストの完全な保存を実行することはお勧めできません。 このような場合は、アセンブリ言語の小さな ISR を使用して、デバイスの割り込みの大半を処理します。 この低オーバーヘッドの ISR は、必要な場合にのみ ThreadX と対話します。

第 3 章の最後にある割り込み管理の説明にも同様の説明があります。

### <a name="thread-suspension"></a>スレッドの中断

この章で前述した簡易ドライバーの例では、文字が使用できない場合に、入力サービスの呼び出し元が一時停止されます。 アプリケーションによっては、これを許容できない場合があります。

たとえば、ドライバーからの入力を処理する役割を担うスレッドにほかの役割もある場合、ドライバーの入力だけで一時停止しても、うまく機能しない可能性があります。 代わりに、スレッドに対する他の処理要求と同様に処理を要求するように、ドライバーをカスタマイズする必要があります。

ほとんどの場合、入力バッファーはリンク リストに配置され、入力イベント メッセージがスレッドの入力キューに送信されます。
