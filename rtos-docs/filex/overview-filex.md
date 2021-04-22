---
title: Azure RTOS FileX を理解する
description: Azure RTO FileX は、ファイル アロケーション テーブル (FAT) 互換のハイ パフォーマンスのファイル システムであり、Azure RTOS ThreadX と完全に統合されており、サポートされるすべてのプロセッサで利用できます。 Azure RTOS ThreadX と同様に、Azure RTOS FileX は、小さい専有領域でハイ パフォーマンスを実現するように設計されているため、ファイル管理操作を必要とする昨今の深い埋め込み型のアプリケーションに最適です。 FileX は、RAM、Azure RTOS USBX、SD カード、および Azure RTOS LevelX 経由の NAND と NOR フラッシュ メモリなど、ほとんどの物理メディアをサポートしています。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: a3a20c8ced3426399ceedf6994c872ce7aec93c3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812137"
---
# <a name="overview-of-azure-rtos-filex"></a>Azure RTOS FileX の概要

Azure RTOS FileX の埋め込みファイル システムは、Microsoft FAT ファイル形式の高度な商用ソリューションであり、深く埋め込まれたリアルタイムの IoT アプリケーション向けに特別に設計されました。 Azure RTOS FileX では、Microsoft のすべてのファイル形式 (FAT12、FAT16、FAT32、exFAT など) がサポートされています。 FileX では、[Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/) と呼ばれるアドオン製品を使用した省略可能なフォールト トレランスや FLASH 消耗平準化も提供されます。 これらすべてを小さな占有領域、高速な処理、優れた使いやすさと組み合わせることで、Azure RTOS FileX は、最も要求の厳しい埋め込み型 IoT アプリケーションに最適な選択肢となります。

## <a name="api-protocols"></a>API プロトコル

### <a name="azure-rtos-filex-api"></a>Azure RTOS FileX API

- 直感的で一貫性のある API
- 名詞 - 動詞の名前付け規則
- すべての API の先頭を *fx_* にして FileX として簡単に識別
- ブロックしている API にオプションのスレッド タイムアウトがある
- メディアとファイルを操作するための省略可能なユーザー通知コールバック
- 詳細については、「[Azure RTOS FileX ユーザー ガイド](about-this-guide.md)」を参照

### <a name="media-services"></a>Media Services

- FAT 12/16/32 と exFAT のサポート
- 最小 6 KB のフラッシュ、2.5 KB の RAM
- 完全なメディア アクセス サービス
- 無制限のメディア インスタンス数
- 単純な読み取り/書き込み論理セクター ドライバー インターフェイス
- 複数パーティションのサポート
- 論理セクター キャッシュ
- FAT エントリ キャッシュ
- 省略可能なフォールト トレランスのサポート
- セカンダリ FAT の遅延更新
- Azure RTOS TraceX によるシステムレベルのトレース
- 次のような直感的なメディア アクセス API:
  - fx_media_open
  - fx_media_close
  - fx_media_format
  - fx_media_space_available

### <a name="directory-services"></a>ディレクトリ サービス

- 最大 256 バイトのパス
- 長い 8.3 ディレクトリ名をサポート
- ディレクトリの作成と削除
- ディレクトリの移動と走査
- ディレクトリ属性の管理
- Azure RTOS TraceX によるシステムレベルのトレース
- 次のような直感的なディレクトリ アクセス API:
  - fx_directory_create
  - fx_directory_delete
  - fx_directory_attributes_set
  - fx_directory_attributes_read
  - fx_directory_first_entry_find
  - fx_directory_next_entry_find

### <a name="file-services"></a>ファイル サービス

- 最小 3.3 KB のフラッシュ
- 無制限の開いているファイル数
- 読み取り専用ファイルを複数回開くことが可能
- 長い 8.3 ディレクトリ名をサポート
- 連続ファイルのサポート
- 高速シーク ロジック
- クラスターの事前割り当て
- ファイルの作成、削除、名前の変更
- ファイルの読み取り、書き込み、参照
- ファイル属性の管理
- Azure RTOS TraceX によるシステムレベルのトレース
- 次のような直感的なファイル アクセス API:
  - fx_file_create
  - fx_file_delete
  - fx_file_attributes_set
  - fx_file_attributes_read
  - fx_file_read
  - fx_file_seek
  - fx_file_write

## <a name="small-footprint"></a>小さなメモリ専有領域

Azure RTOS FileX の埋め込みファイル システムでは、基本的なファイルの読み取り/書き込みをサポートするために、8.6 KB から 12 KB の非常に小さな最小占有領域が実現されています。 最小限の Azure RTOS FileX RAM の使用量は、1 メディア インスタンスあたり約 1.8 KB であり、論理セクター キャッシュは 512 バイトのみです。 Azure RTOS ThreadX と同様に、Azure RTOS FileX のサイズは、アプリケーションで使用されるサービスに基づいて自動的にスケーリングされます。 これにより、複雑な構成やビルド パラメーターが実質的に不要になるため、開発者の作業がより簡単になります。

## <a name="fast-execution"></a>高速実行

Azure RTOS FileX では、論理セクター キャッシュと FAT エントリ キャッシュが提供されます。 どちらのサイズも、アプリケーションで直接制御されます。 さらに、Azure RTOS FileX では、連続したクラスターの割り当てと連続したクラスターの読み取り/書き込みも実現されます。 セクター全体の読み取り/書き込み要求は、アプリケーション バッファーとメディア間で直接実行されます。つまり、中間バッファーは実行されません。 このように設計された一般的な考え方はすべて、Azure RTOS FileX が最高のパフォーマンスを実現するのに役立ちます。

## <a name="advanced-technology"></a>高度なテクノロジ

Azure RTOS FileX は、次のような高度なテクノロジです。

- FAT 12/16/32 と exFAT のサポート
- 複数パーティションのサポート
- 自動スケーリング
- エンディアン ニュートラル
- 長いファイル名と 8.3 のサポート
- 省略可能なフォールト トレランスのサポート
- 論理セクター キャッシュ
- FAT エントリ キャッシュ
- クラスターの事前割り当て
- 連続ファイルのサポート
- 省略可能なパフォーマンス メトリック
- Azure RTOS TraceX システム分析のサポート

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a>NOR/NAND 消耗平準化 (Azure RTOS LevelX)

Azure RTOS LevelX は、Microsoft の NOR/NAND FLASH 消耗平準化製品です。 Azure RTOS LevelX は、FileX と共に使用することも、アプリケーション用のスタンドアロンの直接読み取り/書き込み FLASH セクター ライブラリとして使用することもできます。

## <a name="fastest-time-to-market"></a>市場投入までの時間を短縮

Azure RTOS FileX は、インストール、習得、使用、デバッグ、検証、認定、保守が簡単です。 そのため、Azure RTOS FileX は、埋め込み IoT デバイス用の最も一般的な FAT ファイル システムの 1 つです。 一貫した市場投入まで時間が利点となる理由の一部は、次のとおりです。

- 質の高いドキュメント - [Azure RTOS FileX ユーザー ガイド](about-this-guide.md)をご覧になり、ご自身でお確かめください。
- 完全なソース コードを提供
- 使いやすい API
- 包括的かつ高度な機能セット

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a>TUV と UL による多くの安全性標準による事前認定

![SGS-TUV Saar](./media/overview-filex/partener-logo-sgs-tuv-saar-2.png)

Azure RTOS FileX は、IEC-61508 SIL 4、IEC-62304 SW セーフティ クラス C、ISO 26262 ASIL D、および EN 50128 に従って、安全性が重要なシステムでの使用が SGS-TUV Saar によって認定されています。 この認定により、「電気、電子、プログラマブル電子安全関連系の機能安全」に関する IEC-61508、IEC-62304、ISO 26262、および EN 50128 の最高の安全性整合性レベルに対応する安全性関連ソフトウェアの開発で FileX を使用できることが確認されます。 ドイツの SGS-Group と TUV Saarland の共同事業を通じて結成された SGS-TUV Saar は、世界中の安全関連システムのための組み込みソフトウェアのテスト、監査、検証、認定を行う、世界有数の公認された独立系企業になりました。 工業安全規格の IEC 61508 と、それから派生したすべての標準 (IEC-62304、ISO 26262 および EN 50128 を含む) は、電気・電子・プログラマブル電子安全関連の医療デバイス、プロセス制御システム、工業機械、自動車および鉄道制御システムの機能安全を保証するために使用されます。

:::image type="content" source="media/overview-filex/cru-logo-certification.png" alt-text="CRU UL 認定":::

Azure RTOS FileX は、プログラム可能なコンポーネント内のソフトウェアに対する UL 60730-1 付属文書 H、CSA E60730-1 付属文書 H、IEC 60730-1 付属文書 H、UL 60335-1 付属文書 R、IEC 60335-1 付属文書 R、UL 1998 の各安全標準に準拠しているものとして UL によって承認されています。 UL は、独立した安全科学のグローバル企業であり、電気の公的な選定からサステナビリティ、再生可能エネルギー、およびナノテクノロジーにおける革新まで、さまざまな安全性ソリューションの革新を 1 世紀以上にわたって専門としてきました。

TUV および UL 認定に関連付けられている成果物 (証明書、安全性マニュアル、テスト レポートなど) は、販売されています。

アプリケーションで追加の認定が必要な場合は、Microsoft を通じて認定サービスを利用し、実際のハードウェア プラットフォームを使用してさまざまな標準にターンキー認定を提供したり、アプリケーション コードをカバーしたりできます。

## <a name="one-simple-license"></a>シンプルな 1 つのライセンス

ソース コードの使用とテストに費用はかからず、事前にライセンスされたデバイスに展開する場合は、運用環境ライセンスにはコストがかかりません。その他のすべてのデバイスには、シンプルな年間ライセンスが必要です。

## <a name="full-highest-quality-source-code"></a>完全な最高品質のソース コード

長年にわたり、Azure RTOS FileX のソース コードは、品質とわかりやすさに一定の基準を設けてきました。 また、ファイルごとに 1 つの関数を使用するという規則により、簡単にソースを移動できます。

## <a name="supports-most-popular-architectures"></a>最も一般的なアーキテクチャをサポート

Azure RTOS FileX は、すぐに利用可能で完全なテストとサポートが実現されている、最も一般的な 32/64 ビットのマイクロプロセッサで動作します。

**Analog Devices**: SHARC、Blackfin、CM4xx

**Andes Core**: RISC-V

**Ambiqmicro**: Apollo MCU

**ARM**: ARM7、ARM9、ARM11、Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64 ビット/A7x 64 ビット/R4/R5、TrustZone ARMv8-M

**Cadence**: Xtensa、Diamond

**CEVA**: PSoC、PSoC 4、PSoC 5、PSoC 6、FM0+、FM3、MF4、WICED WiFi

**Cypress**: RISC-V

**EnSilica**: eSi-RISC

**Infineon**: XMC1000、XMC4000、TriCore

**Intel**、**Intel FPGA**: x36/Pentium、XScale、NIOS II、Cyclone、Arria 10

**Microchip**: AVR32、ARM7、ARM9、Cortex-M3/M4/M7、SAM3/4/7/9/A/C/D/E/G/L/SV、PIC24/PIC32

**Microsemi**: RISC-V

**NXP**: LPC、ARM7、ARM9、PowerPC、68 K、i.MX、ColdFire、Kinetis Cortex-M3/M4

**Renesas**: SH、HS、V850、RX、RZ、Synergy

**Silicon** Labs: EFM32

**Synopsys**: ARC 600、700、ARC EM、ARC HS

**ST**: STM32、ARM7、ARM9、Cortex-M3/M4/M7

**Tl**: C5xxx、C6xxx、Stellaris、Sitara、Tiva-C

**Wave Computing**: MIPS32 4K、24 K、34 K、1004 K、MIPS64 5K、microAptiv、interAptiv、proAptiv、M-Class

**Xilinx**: MicroBlaze、PowerPC 405、ZYNQ、ZYNQ UltraSCALE

*表示されるすべてのタイミングとサイズの数値は推定値であり、開発プラットフォームによって異なる場合があります。*
