---
title: 第 2 章 - Azure RTOS USBX ホスト スタックのインストール
description: USBX ホスト スタックをインストールする方法について説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 4c33f95b8ac268c557fd947a1303ec3af315a37e
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377086"
---
# <a name="chapter-2---azure-rtos-usbx-host-stack-installation"></a>第 2 章 - Azure RTOS USBX ホスト スタックのインストール

## <a name="host-considerations"></a>ホストに関する考慮事項

### <a name="computer-type"></a>コンピューターの種類

埋め込み開発は、通常、Windows PC または Unix ホスト コンピューター上で行われます。 アプリケーションは、ホスト上でコンパイル、リンク、および配置された後、実行のためにターゲット ハードウェアにダウンロードされます。

### <a name="download-interfaces"></a>ダウンロードのインターフェイス

通常、ターゲットのダウンロードは RS-232 のシリアル インターフェイスで行われますが、パラレル インターフェイス、USB、およびイーサネットも普及してきています。 使用可能なオプションについては、開発ツールのドキュメントをご覧ください。

### <a name="debugging-tools"></a>デバッグ ツール

デバッグは、通常、プログラム イメージのダウンロードと同じリンクを使って行われます。 デバッガーには、ターゲット上で動作する小さなモニター プログラムから、バックグラウンド デバッグ モニター (BDM) ツールやインサーキット エミュレーター (ICE) ツールまで、さまざまなものがあります。 ICE ツールには、実際のターゲット ハードウェアの最も堅牢なデバッグ機能が用意されています。

### <a name="required-hard-disk-space"></a>必要なハード ディスク容量

USBX のソース コードは ASCII 形式で提供され、ホスト コンピューターのハード ディスク上に約 500 KB の空き領域が必要です。

## <a name="target-considerations"></a>ターゲットに関する考慮事項

USBX は、ホスト モードでターゲット上に 24 KB から 64 KB の読み取り専用メモリ (ROM) を必要とします。 必要なメモリ容量は、使用するコントローラーの種類と、USBX にリンクされている USB クラスによって異なります。 また、USBX グローバル データ構造およびメモリ プール用に、ターゲットのランダム アクセス メモリ (RAM) がさらに 32 KB 必要です。 このメモリ プールは、USB 上の予期されたデバイス数と USB コントローラーの種類に応じて調整することもできます。 USBX デバイス側には、デバイス コントローラーの種類に応じて、約 10K から 12K の ROM が必要です。 RAM メモリの使用量は、デバイスによってエミュレートされるクラスの種類によって異なります。

また、USBX は、複数スレッド保護のために、ThreadX セマフォ、ミューテックス、およびスレッドを利用しているほか、USB バス トポロジを監視するために I/O 中断および定期的な処理を行っています。

### <a name="product-distribution"></a>製品の配布

Azure RTOS USBX は、<https://github.com/azure-rtos/usbx/> のパブリック ソース コード リポジトリから入手できます。

以下は、リポジトリ内のいくつかの重要なファイルの一覧です。

- ***ux_api.h***: この C ヘッダー ファイルには、すべてのシステム等価物、データ構造、およびサービス プロトタイプが含まれています。
- ***ux_port.h***: この C ヘッダー ファイルには、開発ツール固有のすべてのデータ定義とデータ構造が含まれています。
- ***ux.lib***: これは、USBX C ライブラリのバイナリ バージョンです。 これは標準パッケージと共に配布されます。
- ***demo_usbx c***: シンプルな USBX デモが含まれる C ファイル

すべてのファイル名が小文字で表記されます。 この名前付け規則によって、コマンドを Unix 開発プラットフォームにより簡単に変換できます。

## <a name="usbx-installation"></a>USBX のインストール

USBX は、GitHub リポジトリをローカル コンピューターに複製することによってインストールされます。 お使いの PC 上に USBX リポジトリの複製を作成するための一般的な構文を次に示します。

```powershell
    git clone https://github.com/azure-rtos/usbx
```

GitHub メイン ページ上のダウンロード ボタンを使用して、リポジトリのコピーをダウンロードすることもできます。

また、オンライン リポジトリのフロント ページ上で USBX ライブラリを構築する手順も紹介します。

次の一般的な手順は、事実上すべてのインストールに適用されます。

1. ホストのハード ドライブ上で以前 ThreadX をインストールした先と同じディレクトリを使用します。 すべての USBX 名が一意で、以前の USBX インストールと競合することはありません。
2. _ *_tx_application_define_** の先頭または先頭付近に ***ux_system_initialize** _ への呼び出しを追加します。これは USBX リソースが初期化される場所です。
3. ***ux_host_stack_initialize*** への呼び出しを追加します。
4. 必要な USBX を初期化するための呼び出しを 1 つ以上追加します。
5. システム内で使用可能なホスト コントローラーを初期化するための呼び出しを 1 つ以上追加します。
6. 低レベルのハードウェア初期化および割り込みベクター ルーティングを追加するために、tx_low_level_initialize.c ファイルの変更が必要になる場合があります。 これはハードウェア プラットフォームに固有であるため、ここでは説明しません。
7. アプリケーション ソース コードをコンパイルし、USBX および ThreadX ランタイム ライブラリ (USB ストレージ クラスや USB ネットワーク クラスをコンパイルする場合は、FileX や Netx も必要になる場合があります)、ux. a (または ux.lib)、および tx.a (または tx.lib) とリンクします。 結果はターゲットにダウンロードして、実行できます。

## <a name="configuration-options"></a>構成オプション

USBX ライブラリを構築するための構成オプションはいくつかあります。 オプションはすべて ***ux_user.h*** にあります。

各構成オプションの詳細を以下に示します。


- **UX_PERIODIC_RATE**: この値は、特定のハードウェア プラットフォームの 1 秒あたりのティック数を表します。 既定値は 1000 で、ミリ秒あたり 1 ティックを示します。
- **UX_MAX_CLASS_DRIVER**: この値は、USBX によって読み込むことができるクラスの最大数です。 この値はクラス コンテナーを表します。クラスのインスタンス数ではありません。 たとえば、USBX の特定の実装にハブ クラス、プリンター クラス、およびストレージ クラスが必要な場合、これらのクラスに属するデバイスの数に関係なく、UX_MAX_CLASS_DRIVER 値は 3 に設定できます。
- **UX_MAX_HCD**: この値は、システム内で使用できるさまざまなホスト コントローラーの数を表します。 USB 1.1 サポートの場合、この値はほとんどが 1 になります。 USB 2.0 サポートの場合、この値には 1 より大きい値を指定できます。 この値は、同時に実行されているホスト コントローラーの数を表します。 たとえば、OHCI のインスタンスが 2 つ実行されている場合、または EHCI コントローラーと OHCI コントローラーが 1 つずつ実行されている場合、UX_MAX_HCD は 2 に設定する必要があります。 
- **UX_MAX_DEVICES**: この値は、USB にアタッチできるデバイスの最大数を表します。 通常、単一 USB 上の理論上の最大数は 127 デバイスです。 この値は、メモリを節約するためにスケールダウンできます。 この値は、システム内の USB バスの数に関係なく、デバイスの合計数を表すことに注意してください。
- **UX_MAX_ED**: この値は、コントローラー プール内の ED の最大数を表します。 この数は 1 つのコントローラーにのみ割り当てられます。 コントローラーのインスタンスが複数存在する場合、この値は、個別のコントローラーごとに使用されます。
- **UX_MAX_TD と UX_MAX_ISO_TD**: この値は、コントローラー プール内の標準 TD およびアイソクロナス TD の最大数を表します。 この数は 1 つのコントローラーにのみ割り当てられます。 コントローラーのインスタンスが複数存在する場合、この値は、個別のコントローラーごとに使用されます。
- **UX_THREAD_STACK_SIZE**: この値は、USBX スレッド用のスタックのサイズ (バイト単位) です。 これは、通常、使用されるプロセッサとホスト コントローラーに応じて、1024 バイトまたは 2048 バイトになります。
- **UX_HOST_ENUM_THREAD_STACK_SIZE**: この値は、USB ホスト列挙スレッドのスタック サイズです。 このシンボルが設定されていない場合、USBX ホスト列挙スレッドのスタック サイズは **UX_THREAD_STACK_SIZE** に設定されます。 
- **UX_HOST_HCD_THREAD_STACK_SIZE**: この値は、USB ホスト HCD スレッドのスタック サイズです。 このシンボルが設定されていない場合、USBX ホスト HCD スレッドのスタック サイズは **UX_THREAD_STACK_SIZE** に設定されます。
- **UX_THREAD_PRIORITY_ENUM**: これは、バス トポロジを監視する USBX 列挙スレッドの ThreadX 優先度の値です。
- **UX_THREAD_PRIORITY_CLASS**: これは、標準 USBX スレッドの ThreadX 優先度の値です。
- **UX_THREAD_PRIORITY_KEYBOARD**: これは、USBX HID キーボード クラスの ThreadX 優先度の値です。
- **UX_THREAD_PRIORITY_HCD**: これは、ホスト コントローラー スレッドの ThreadX 優先度の値です。
- **UX_NO_TIME_SLICE**: この値は、スレッドに使用されるタイム スライスを実際に定義します。 たとえば、0 に定義されている場合、ThreadX ターゲット ポートはタイム スライスを使用しません。
- **UX_MAX_HOST_LUN**: この値は、ホスト ストレージ クラス ドライバー内で表される SCSI 論理ユニットの最大数を表します。
- **UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: 定義されている場合、この値には、CB または CBI プロトコル (フロッピー ディスクなど) を使用するストレージ デバイスを処理するコードが含まれます。 これらのプロトコルは古い形式で、事実上すべての最新ストレージ デバイスで使用されてい BOT (Bulk Only Transport) プロトコルで置き換えられています。このため、これは既定ではオフになっています。
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: この値が定義されている場合、ux_host_class_hid_keyboard_key_get は、キーの変更、つまりキー押下とキー リリースのみを報告します。 既定では、キーが押されたときのみ報告します。
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** が定義されている場合にのみ使用されます。 定義されている場合、ux_host_class_hid_keyboard_key_get は、キー押下/ダウンの変更のみを報告します。キー リリース/アップの変更は報告されません。
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS**: **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** が定義されている場合にのみ使用されます。 定義されている場合、ux_host_class_hid_keyboard_key_get は、キー ロック (CapsLock/NumLock/ScrollLock) の変更を報告します。
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** が定義されている場合にのみ使用されます。 定義されている場合、ux_host_class_hid_keyboard_key_get は、修飾キー (Ctrl/Alt/Shift/GUI) の変更を報告します。
- **UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: 定義されている場合、この値は CDC-ECM ホスト クラス内のパケット数を表します。 既定値は 16 です。

## <a name="source-code-tree"></a>ソース コード ツリー

USBX ファイルは、複数のディレクトリ内に用意されています。

![ソース コード ツリー](media/usbx-host-stack/source-code-tree.png)

ファイル名によってファイルを認識できるようにするために、次の規則が採用されています。

| ファイルのサフィックス名 | ファイルの説明                          |
| ---------------- | ----------------------------------------- |
| ux_host_stack    | USBX ホスト スタック コア ファイル                |
| ux_host_class    | USBX ホスト スタック クラス ファイル             |
| ux_hcd           | USBX ホスト スタック コントローラー ドライバー ファイル   |
| ux_device_stack  | USBX デバイス スタック コア ファイル              |
| ux_device_class  | USBX デバイス スタック クラス ファイル           |
| ux_dcd           | USBX デバイス スタック コントローラー ドライバー ファイル |
| ux_otg           | USBX OTG コントローラー ドライバー関連ファイル  |
| ux_pictbridge    | USBX Pictbridge ファイル                     |
| ux_utility       | USBXユーティリティ関数                    |
| demo_usbx        | USBX のデモンストレーション ファイル              |

## <a name="initialization-of-usbx-resources"></a>USBX リソースの初期化

USBX には、独自のメモリ マネージャーがあります。 メモリは、USBX のホスト側またはデバイス側が初期化される前に、USBX に割り当てられている必要があります。 USBX メモリ マネージャーは、メモリをキャッシュできるシステムに対応できます。

次の関数は、USBX メモリ リソースを通常の 128K メモリで初期化します。キャッシュ セーフ メモリ用の個別のプールはありません。

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

ux_system_initialize のプロトタイプは次のとおりです。

```c
UINT ux_system_initialize( 
    VOID *regular_memory_pool_start,
    ULONG regular_memory_size,
    VOID *cache_safe_memory_pool_start,
    ULONG cache_safe_memory_size);
```

### <a name="input-parameters"></a>入力パラメーター:

- **regular_memory_pool_start** 通常のメモリ プールの開始。
- **regular_memory_size** 通常のメモリ プールのサイズ。
- **cache_safe_memory_pool_start** キャッシュ セーフ メモリ プールの開始。
- **cache_safe_memory_size** キャッシュ セーフ メモリ プールのサイズ。    |

キャッシュ セーフ メモリの定義を必要としないシステムもあります。 このようなシステムでは、メモリ ポインターの初期化中に渡された値は UX_NULL に、プールのサイズは 0 に設定されます。 その後、USBX はキャッシュ セーフ プールの代わりに通常のメモリ プールを使用します。

通常のメモリがキャッシュ セーフではなく、コントローラーが DMA メモリ (OHCI、EHCI コントローラーなど) を実行する必要があるシステムでは、キャッシュ セーフ ゾーン内でメモリ プールを定義する必要があります。

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

## <a name="definition-of-usb-host-controllers"></a>USB ホスト コントローラーの定義

USBX をホスト モードで動作させるには、USB ホスト コントローラーを少なくとも 1 つ定義する必要があります。 アプリケーション初期化ファイルには、この定義が含まれている必要があります。 次の行は、汎用ホスト コントローラーの定義を実行します。

```c
ux_host_stack_hcd_register("ux_hcd_controller",
        ux_hcd_controller_initialize, 0xd0000, 0x0a);
```

ux_host_stack_hcd_register には、次のプロトタイプが含まれます。

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_initialize_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

ux_host_stack_hcd_register 関数には、次のパラメーターが含まれます。

- **hcd_name**: コントローラー名の文字列
- **hcd_initialize_function**: コントローラーの初期化関数
- **hcd_param1**: 通常、コントローラーによって使用される IO 値またはメモリ
- **hcd_param2**: 通常、コントローラーによって使用される IRQ

前の例の項目はそれぞれ以下を表します。

- "ux_hcd_controller" はコントローラーの名前です
- "ux_hcd_controller_initialize" は、ホスト コントローラーの初期化ルーチンです
- 0xd0000 は、メモリ内でホスト コントローラー レジスタを表示できるアドレスです
- 0x0a は、ホスト コントローラーによって使用される IRQ です。

1 つのホスト コントローラーと複数のクラスを持つ、ホスト モードでの USBX の初期化の例を次に示します。

```c
UINT status;

/* Initialize USBX. */
ux_system_initialize(memory_ptr, (128*1024),0,0);

/* The code below is required for installing the USBX host stack. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, host stack has been initialized. */

/* Register all the host classes for this USBX implementation. */
status = ux_host_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_storage", ux_host_class_storage_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_printer", ux_host_class_printer_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_audio", ux_host_class_audio_entry);

/* If status equals UX_SUCCESS, host class has been registered. */

/* Register all the USB host controllers available in this system. */ 
status = ux_host_stack_hcd_register("ux_hcd_controller", ux_hcd_controller_initialize, 0x300000, 0x0a);

/* If status equals UX_SUCCESS, USB host controllers have been registered. */
```

## <a name="definition-of-host-classes"></a>Host クラスの定義

USBX を使用して 1 つ以上のホスト クラスを定義する必要があります。 USB スタックが USB デバイスを構成した後、その USB デバイスを動作させるには USB クラスが必要です。 USB クラスは、デバイスに固有です。 USB デバイス記述子に含まれるインターフェイスの数によっては、USB デバイスを動作させるために 1 つ以上のクラスが必要になる場合があります。

HUB クラスの登録の例を次に示します。

```c
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);
```

関数 ux_host_class_register には、次のプロトタイプが含まれます。

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name, 
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

- **class_name** はクラスの名前です
- **class_entry_address** はクラスのエントリ ポイントです

HUB クラスの初期化の例の項目はそれぞれ以下を表します。

- "ux_host_class_hub" は HUB クラスの名前です
- ux_host_class_hub_entry は HUB クラスのエントリ ポイントです。

## <a name="troubleshooting"></a>トラブルシューティング

USBX には、デモンストレーション ファイルとシミュレーション環境が付属しています。 まずは、ターゲット ハードウェアまたは特定のデモンストレーション プラットフォームのいずれかで、デモンストレーション プラットフォームを稼働させることを常にお勧めします。

デモンストレーション システムが動作しない場合は、次のことを試して問題を絞り込んでください。

## <a name="usbx-version-id"></a>USBX のバージョン ID

現在使用している USBX のバージョンは、実行時にユーザーとアプリケーション ソフトウェアのどちらからでも確認できます。 プログラマーは ***ux_port.h** _ ファイルを調べることで USBX のバージョンを確認できます。 加えて、このファイルには、対応するポートのバージョン履歴も含まれています。 アプリケーション ソフトウェアは、_*_ux_port.h_** 内で定義されているグローバル文字列 _ *_ _ux_version_id_* _ を調べることで USBX バージョンを取得できます。
