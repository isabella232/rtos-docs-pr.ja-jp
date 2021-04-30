---
title: 第 2 章 - Azure RTOS USBX デバイス スタックのインストール
description: Azure RTOS USBX デバイス スタックのインストール、およびインストールする前に検討する必要があるホストに関する重要な考慮事項について説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: dd58f77130fa252be9163bd70c29f7deee400d30
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549778"
---
# <a name="chapter-2---azure-rtos-usbx-device-stack-installation"></a>第 2 章 - Azure RTOS USBX デバイス スタックのインストール

## <a name="host-considerations"></a>ホストに関する考慮事項

### <a name="computer-type"></a>コンピューターの種類

埋め込み開発は、通常、Windows PC または Unix ホスト コンピューター上で行われます。 アプリケーションは、ホスト上でコンパイル、リンク、および配置された後、実行のためにターゲット ハードウェアにダウンロードされます。

### <a name="download-interfaces"></a>ダウンロードのインターフェイス

通常、ターゲットのダウンロードは RS-232 のシリアル インターフェイスで行われますが、パラレル インターフェイス、USB、およびイーサネットも普及してきています。 使用可能なオプションについては、開発ツールのドキュメントをご覧ください。

### <a name="debugging-tools"></a>デバッグ ツール

デバッグは、通常、プログラム イメージのダウンロードと同じリンクを使って行われます。 デバッガーには、ターゲット上で動作する小さなモニター プログラムから、バックグラウンド デバッグ モニター (BDM) ツールやインサーキット エミュレーター (ICE) ツールまで、さまざまなものがあります。 ICE ツールには、実際のターゲット ハードウェアの最も堅牢なデバッグ機能が用意されています。

### <a name="required-hard-disk-space"></a>必要なハード ディスク容量

USBX のソース コードは ASCII 形式で提供され、ホスト コンピューターのハード ディスク上に約 500 KB の空き領域が必要です。

### <a name="target-considerations"></a>ターゲットに関する考慮事項

USBX は、ホスト モードでターゲット上に 24 KB から 64 KB の読み取り専用メモリ (ROM) を必要とします。 必要なメモリ容量は、使用するコントローラーの種類と、USBX にリンクされている USB クラスによって異なります。 また、USBX グローバル データ構造およびメモリ プール用に、ターゲットのランダム アクセス メモリ (RAM) がさらに 32 KB 必要です。 このメモリ プールは、USB 上の予期されたデバイス数と USB コントローラーの種類に応じて調整することもできます。 USBX デバイス側には、デバイス コントローラーの種類に応じて、約 10K から 12K の ROM が必要です。 RAM メモリの使用量は、デバイスによってエミュレートされるクラスの種類によって異なります。

また、USBX は、複数スレッド保護のために、ThreadX セマフォ、ミューテックス、およびスレッドを利用しているほか、USB バス トポロジを監視するために I/O 中断および定期的な処理を行っています。

### <a name="product-distribution"></a>製品の配布

Azure RTOS USBX は、<https://github.com/azure-rtos/usbx/> のパブリック ソース コード リポジトリから入手できます。

以下は、リポジトリ内のいくつかの重要なファイルの一覧です。

* ***ux_api.h***: この C ヘッダー ファイルには、すべてのシステム等価物、データ構造、およびサービス プロトタイプが含まれています。
* ***ux_port.h***: この C ヘッダー ファイルには、開発ツール固有のすべてのデータ定義とデータ構造が含まれています。
* ***ux.lib***: これは、USBX C ライブラリのバイナリ バージョンです。 これは標準パッケージと共に配布されます。
* ***demo_usbx c***: シンプルな USBX デモが含まれる C ファイル

すべてのファイル名が小文字で表記されます。 この名前付け規則によって、コマンドを Unix 開発プラットフォームにより簡単に変換できます。

## <a name="usbx-installation"></a>USBX のインストール

USBX は、GitHub リポジトリをローカル コンピューターに複製することによってインストールされます。 お使いの PC 上に USBX リポジトリの複製を作成するための一般的な構文を次に示します。

```c
    git clone https://github.com/azure-rtos/usbx
```

GitHub メイン ページ上のダウンロード ボタンを使用して、リポジトリのコピーをダウンロードすることもできます。

また、オンライン リポジトリのフロント ページ上で USBX ライブラリを構築する手順も紹介します。

次の一般的な手順は、事実上すべてのインストールに適用されます。

1. ホストのハード ドライブ上で以前 ThreadX をインストールした先と同じディレクトリを使用します。 すべての USBX 名が一意で、以前の USBX インストールと競合することはありません。
1. _*_tx_application_define_** の先頭または先頭付近に ***ux_system_initialize** _ への呼び出しを追加します。 これは USBX リソースが初期化される場所です。
1. ***ux_device_stack_initialize*** への呼び出しを追加します。
1. 必要な USBX クラス (ホストまたはデバイス クラス) を初期化するための呼び出しを 1 つ以上追加します
1. システム内で使用可能なデバイス コントローラーを初期化するための呼び出しを 1 つ以上追加します。
1. 低レベルのハードウェア初期化および割り込みベクター ルーティングを追加するために、tx_low_level_initialize.c ファイルの変更が必要になる場合があります。 これはハードウェア プラットフォームに固有であるため、ここでは説明しません。
1. アプリケーション ソース コードをコンパイルし、USBX および ThreadX ランタイム ライブラリ (USB ストレージ クラスや USB ネットワーク クラスをコンパイルする場合は、FileX や Netx も必要になる場合があります)、ux. a (または ux.lib)、および tx.a (または tx.lib) とリンクします。 結果はターゲットにダウンロードして、実行できます。

## <a name="configuration-options"></a>構成オプション

USBX ライブラリを構築するための構成オプションはいくつかあります。 オプションはすべて ***ux_user.h*** にあります。

各構成オプションの詳細を以下に示します。

| 構成&nbsp;オプション | 説明 |
| --- | --- |
| **UX_PERIODIC_RATE** | この値は、特定のハードウェア プラットフォームの 1 秒あたりのティック数を表します。 既定値は 1000 で、ミリ秒あたり 1 ティックを示します。 |
| **UX_THREAD_STACK_SIZE** | この値は、USBX スレッド用のスタックのサイズ (バイト単位) です。 これは、通常、使用されるプロセッサとホスト コントローラーに応じて、1024 バイトまたは 2048 バイトになります。 |
| **UX_THREAD_PRIORITY_ENUM** | これは、バス トポロジを監視する USBX 列挙スレッドの ThreadX 優先度の値です。 |
| **UX_THREAD_PRIORITY_CLASS** | これは、標準 USBX スレッドの ThreadX 優先度の値です。 |
| **UX_THREAD_PRIORITY_KEYBOARD** | これは、USBX HID キーボード クラスの ThreadX 優先度の値です。 |
| **UX_THREAD_PRIORITY_DCD** | これは、デバイス コントローラー スレッドの ThreadX 優先度の値です。 |
| **UX_NO_TIME_SLICE** | この値は、スレッドに使用されるタイム スライスを実際に定義します。 たとえば、0 に定義されている場合、ThreadX ターゲット ポートはタイム スライスを使用しません。 |
| **UX_MAX_SLAVE_CLASS_DRIVER** | これは、ux_device_stack_class_register 経由で登録できる USBX クラスの最大数です。 |
| **UX_MAX_SLAVE_LUN** | この値は、デバイス ストレージ クラス ドライバー内で表される SCSI 論理ユニットの現在の数を表します。 |
| **UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC** | 定義されている場合、ストレージ クラスではマルチメディア コマンド (MMC)、つまり DVD-ROM が処理されます。 |
| **UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES** | この値は、CDC-ECM クラスのパケット プール内にある NetX パケットの数を表します。 既定値は 16 です。 |
| **UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH** | この値は、デバイス スタック内のコントロール エンドポイントで受信される最大バイト数を表します。 既定値は 256 バイトですが、メモリ制約環境では減らすことができます。 |
| **UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH** | この値は、HID レポートの最大長 (バイト単位) を表します。 |
| **UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE** | この値は、一度にキューに入れることができる HID レポートの最大数を表します。 |
| **UX_SLAVE_REQUEST_DATA_MAX_LENGTH** | この値は、デバイス スタック内の一括エンドポイントで受信される最大バイト数を表します。 既定値は 4096 バイトですが、メモリ制約環境では減らすことができます。 |

## <a name="source-code-tree"></a>ソース コード ツリー

USBX ファイルは、複数のディレクトリ内に用意されています。

![ソース コード ツリー](media/usbx-device-stack/source-code-tree.png)

ファイル名によってファイルを認識できるようにするために、次の規則が採用されています。

| ファイルのサフィックス名  | ファイルの説明                          |
| ----------------- | ----------------------------------------- |
| ux_host_stack   | USBX ホスト スタック コア ファイル                |
| ux_host_class   | USBX ホスト スタック クラス ファイル             |
| ux_hcd           | USBX ホスト スタック コントローラー ドライバー ファイル   |
| ux_device_stack | USBX デバイス スタック コア ファイル              |
| ux_device_class | USBX デバイス スタック クラス ファイル           |
| ux_dcd           | USBX デバイス スタック コントローラー ドライバー ファイル |
| ux_otg           | USBX OTG コントローラー ドライバー関連ファイル  |
| ux_pictbridge    | USBX Pictbridge ファイル                     |
| ux_utility       | USBX ユーティリティ関数                    |
| demo_usbx        | USBX のデモンストレーション ファイル              |

## <a name="initialization-of-usbx-resources"></a>USBX リソースの初期化

USBX には、独自のメモリ マネージャーがあります。 メモリは、USBX のホスト側またはデバイス側が初期化される前に、USBX に割り当てられている必要があります。 USBX メモリ マネージャーは、メモリをキャッシュできるシステムに対応できます。

次の関数は、USBX メモリ リソースを通常の 128 K メモリで初期化します。キャッシュ セーフ メモリ用の個別のプールはありません。

```c
/* Initialize USBX Memory */
ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

ux_system_initialize のプロトタイプは次のとおりです。

```c
UINT ux_system_initialize(VOID *regular_memory_pool_start,
        ULONG regular_memory_size,
        VOID *cache_safe_memory_pool_start,
        ULONG cache_safe_memory_size);
```

入力パラメーター:

| パラメーター                          | 説明                             |
| ---------------------------------- | --------------------------------------- |
| VOID *regular_memory_pool_start    | 通常のメモリ プールの開始    |
| ULONG regular_memory_size          | 通常のメモリ プールのサイズ         |
| VOID *cache_safe_memory_pool_start | キャッシュ セーフ メモリ プールの開始 |
| ULONG cache_safe_memory_size       | キャッシュ セーフ メモリ プールのサイズ      |

キャッシュ セーフ メモリの定義を必要としないシステムもあります。 このようなシステムでは、メモリ ポインターの初期化中に渡された値は UX_NULL に、プールのサイズは 0 に設定されます。 その後、USBX はキャッシュ セーフ プールの代わりに通常のメモリ プールを使用します。

通常のメモリがキャッシュ セーフではなく、コントローラーが DMA メモリを実行する必要があるシステムでは、キャッシュ セーフ ゾーン内でメモリ プールを定義する必要があります。

## <a name="uninitialization-of-usbx-resources"></a>USBX リソースを初期化前の状態に戻す

USBX を終了するには、そのリソースを解放します。 USBX を終了する前に、すべてのクラスとコントローラー リソースを適切に終了する必要があります。 次の関数は、USBX メモリ リソースを初期化前の状態に戻します。

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

ux_system_initialize のプロトタイプは次のとおりです。

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-device-controller"></a>USB デバイス コントローラーの定義

デバイス モードで動作する場合は、一度に 1 つの USB デバイス コントローラーだけを定義できます。 アプリケーション初期化ファイルには、この定義が含まれている必要があります。 次の行は、汎用 USB コントローラーの定義を実行します。

```c
ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);
```

USB デバイスの初期化には、次のプロトタイプがあります。

```c
UINT ux_dcd_controller_initialize(ULONG dcd_io,
    ULONG dcd_irq, ULONG dcd_vbus_address);
```

次のパラメーターを使用できます。

| パラメーター               | 説明                      |
| ------------------------ | -------------------------------- |
| ULONG dcd_io            | コントローラー IO のアドレス     |
| ULONG dcd_irq           | コントローラーによって使用される割り込み |
| ULONG dcd_vbus_address | VBUS GPIO のアドレス         |

次の例は、ストレージ デバイス クラスと汎用コントローラーを使って USBX をデバイス モードで初期化する方法を示したものです。

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024), 0, 0);

/* The code below is required for installing the device portion of USBX */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, installation was successful. */

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(ux_system_slave_class_storage_name ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *)&storage_parameter);

/* Register the device controllers available in this system */
status = ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);

/* If status equals UX_SUCCESS, registration was successful. */
```

## <a name="troubleshooting"></a>トラブルシューティング

USBX には、デモンストレーション ファイルとシミュレーション環境が付属しています。 まずは、ターゲット ハードウェアまたは特定のデモンストレーション プラットフォームのいずれかで、デモンストレーション プラットフォームを稼働させることを常にお勧めします。

## <a name="usbx-version-id"></a>USBX のバージョン ID

現在使用している USBX のバージョンは、実行時にユーザーとアプリケーション ソフトウェアのどちらからでも確認できます。 プログラマーは ***ux_port.h** _ ファイルを調べることで USBX のバージョンを確認できます。 加えて、このファイルには、対応するポートのバージョン履歴も含まれています。 アプリケーション ソフトウェアは、_*_ux_port.h_** 内で定義されているグローバル文字列 _ *_ _ux_version_id_* _ を調べることで USBX バージョンを取得できます。
