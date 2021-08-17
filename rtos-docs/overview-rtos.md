---
title: Microsoft Azure RTOS とは
description: Azure RTOS は、マイクロコントローラー ユニット (MCU) を搭載した IoT デバイスとエッジ デバイスのためのリアル タイム オペレーティング システム (RTOS) です。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: d9bd7cfda454e73e9bd270b86616780ab7ceab1a76160a66cf49a9ef82efae05
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792402"
---
# <a name="what-is-microsoft-azure-rtos"></a>Microsoft Azure RTOS とは

Azure RTOS は、マイクロコントローラー ユニット (MCU) を搭載したモノのインターネット (IoT) およびエッジ デバイスのためのリアル タイム オペレーティング システム (RTOS) です。 Azure RTOS は、非常に制約の厳しいデバイス (バッテリ駆動で、フラッシュ メモリが 64 KB 未満) をサポートするように設計されています。

Azure RTOS は、さまざまな安全性標準に対する認定をあらかじめ受けています。 これには、IEC 61508 SIL 4、IEC 62304 Class C、ISO 26262 ASIL D の各認定が含まれます。

Azure RTOS により、IPsec による完全な IP 層セキュリティおよび TLS と DTLS によるソケット層セキュリティを含む、EAL4+ の情報セキュリティ国際評価基準認定環境が提供されます。 Microsoft のソフトウェア暗号化ライブラリは、FIPS 140-2 の認定を受けています。 また、ハードウェア暗号化機能、ThreadX MODULES によるメモリ保護、ARM の TrustZone ARMv8-M セキュリティ機能のサポートも利用しています。

## <a name="components-of-azure-rtos"></a>Azure RTOS のコンポーネント

Azure RTOS プラットフォームは、Azure RTOS ThreadX、Azure RTOS FileX、Azure RTOS GUIX、Azure RTOS NetX、Azure RTOS NetX Duo、Azure RTOS USBX などの実行時ソリューションのコレクションです。

### <a name="azure-rtos-threadx"></a>Azure RTOS ThreadX

Azure [RTOS ThreadX](threadx/overview-threadx.md) は、特に深く組み込まれたアプリケーション向けに設計された高度なリアルタイム オペレーティング システム (RTOS) です。 Azure RTOS ThreadX によって提供されるさまざまな利点としては、高度なスケジュール機能、メッセージ パッシング、割り込み管理、メッセージング サービスなどがあります。 Azure RTOS ThreadX には、ピコカーネル アーキテクチャ、優先しきい値のスケジュール設定、イベント チェーン、豊富なシステム サービスのセットなど、高度な機能が多数用意されています。

### <a name="azure-rtos-filex"></a>Azure RTOS FileX

Azure [RTOS FileX](filex/overview-filex.md) は、高パフォーマンスの FAT 互換ファイル システムです。 Azure RTOS ThreadX と完全に統合されており、サポートされているすべてのプロセッサで利用できます。 Azure RTOS ThreadX と同様に、Azure RTOS FileX は、小さい専有領域でハイ パフォーマンスを実現するように設計されているため、ファイル操作を必要とする昨今の深い埋め込み型のアプリケーションに最適です。 Azure RTOS FileX により、RAM ディスク、USBX、SD カード、および Azure RTOS LevelX 経由の NAND と NOR フラッシュ メモリなど、ほとんどの物理メディアがサポートされています。

### <a name="azure-rtos-guix"></a>Azure RTOS GUIX

Azure [RTOS GUIX](guix/overview-guix.md) は、埋め込みシステム開発者のニーズに対応するために作成された、プロフェッショナル品質のグラフィカル ユーザー インターフェイス パッケージです。 代替製品とは異なり、Azure RTOS GUIX は小さく高速で、グラフィカル出力をサポートできる事実上すべてのハードウェア構成に簡単に移植できます。 また、Azure RTOS GUIX には、魅力的な外観と、アプリケーション レベルのユーザー インターフェイス開発用の直感的で強力な API も用意されています。

### <a name="azure-rtos-netx"></a>Azure RTOS NetX

Azure [RTOS NetX](netx/overview-netx.md) は、TCP/IP プロトコル標準の高パフォーマンスの実装です。 Azure RTOS ThreadX と完全に統合されており、サポートされているすべてのプロセッサで利用できます。 Azure RTOS NetX は、独自の Piconet アーキテクチャを備えています。 ゼロコピー API と組み合わせることで、ネットワーク接続を必要とする今日の深く組み込まれたアプリケーションに最適なものになります。

### <a name="azure-rtos-netx-duo"></a>Azure RTOS NetX Duo

Azure [RTOS NetX](netx-duo/overview-netx-duo.md) Duo は、特に深く組み込まれたリアルタイムの IoT アプリケーション用に設計された、高度な商用 TCP/IP ネットワーク スタックです。 Azure RTOS NetX Duo が IPv4 と IPv6 のデュアル ネットワーク スタックであるのに対し、NetX は元の IPv4 ネットワーク スタックで、実質的には Azure RTOS NetX Duo のサブセットです。

### <a name="azure-rtos-usbx"></a>Azure RTOS USBX

Azure [RTOS USBX](usbx/overview-usbx.md) は、ハイ パフォーマンスの USB ホスト、デバイス、On-The-Go (OTG) の埋め込みスタックです。 ThreadX と完全に統合されており、Azure RTOS ThreadX でサポートされているすべてのプロセッサで利用できます。 Azure RTOS ThreadX と同様に、Azure RTOS USBX は、小さいフットプリントでハイパフォーマンスを実現するように設計されているため、USB デバイスとのインターフェイスを必要とする深く組み込まれたアプリケーションに最適です。

### <a name="windows-tools"></a>Windows ツール

Azure [RTOS GUIX Studio](guix/about-guix-studio.md) には完全な GUI アプリケーション デザイン環境が用意されており、アプリケーションの GUI のすべてのグラフィカル要素を容易に作成および保守できます。 Azure RTOS GUIX Studio によって、Azure RTOS GUIX ライブラリと互換性がある C コードが自動的に生成されます。これはターゲット上でコンパイルおよび実行できます。

Azure [RTOS TraceX](tracex/overview-tracex.md) は、開発者がリアルタイム システムのイベントをグラフィカルに表示し、リアルタイム システムの動作への理解を深めることができる、ホストベースの分析ツールです。

## <a name="the-azure-rtos-advantage"></a>Azure RTOS の利点
Azure RTOS には、他のリアルタイム オペレーティング システムに比べて次のような利点があります。

### <a name="most-deployed-rtos"></a>最も多く展開されている RTOS

大手 M2M 市場インテリジェンス企業である VDC Research によると、Azure RTOS は全世界で 62 億件以上展開されています。 Azure RTOS の人気は、その信頼性、品質、サイズ、パフォーマンス、先進的機能、使いやすさ、および全体的な市場投入時間が高く評価されていることの証明と言えます。

> *「私たちは、会社の設立以来、ワイヤレスおよび IoT 市場における THREADX の成長の軌跡を見てきましたが、THREADX が幅広い業界で導入されていることに、改めて感心しています。」* – VDC Research 取締役副社長 Chris Rommel 氏

### <a name="intuitive-and-consistent-api-design"></a>直感的で一貫性のある API のデザイン

* 直感的で一貫性のある API。
* 名詞 - 動詞の名前付け規則。
* すべての API には、ThreadX の *tx_* や FileX の *fx_* など、先頭にプレフィックスが付けられており、それらが所属する Azure RTOS コンポーネントを簡単に識別可能です。
* API 全体の機能の整合性。 たとえば、中断を実行するすべての API 関数には、同様に機能するオプションのタイムアウトがあります。
* 多数の API をアプリケーション ISR から直接利用可能。
- メディアとファイルを操作するための省略可能なユーザー通知コールバック。
* イベントドリブン プログラミング モデル (API)。

### <a name="high-efficiency"></a>高効率

- 小さいコード フットプリント。
- 使用されるサービスに基づいたスケーラブルなコード フットプリント。
- TUV および UL による IEC 61508 SIL 4、IEC 62304 クラス C、ISO 26262 ASIL D、および EN 50128 SW-SIL4 に対する事前認定。
- 高速実行。 Azure RTOS は速度を目的として設計され、可能な限り最速のパフォーマンスを実現するために最小限の内部関数呼び出しレイヤーで構成されています。

### <a name="fastest-time-to-market"></a>市場投入までの時間を最短化

Azure RTOS は、インストール、習得、使用、デバッグ、検証、認定、保守が簡単です。 その結果、Azure RTOS は、Broadcom や Gainspan などが提供する多くの SoC を含む、組み込み型 IoT デバイス向けの最も一般的なリアルタイム オペレーティング システムの 1 つとなっています。 一貫した市場投入までの時間の優位性は、次の要素を基に構築されています。

* 完全なソース コードを提供。
* 使いやすい API。
* 包括的かつ高度な機能セット。
* 高品質のドキュメント

### <a name="one-simple-license"></a>シンプルな 1 つのライセンス

ソース コードの使用とテストにコストはかかりません。事前にライセンスされたデバイスに展開する場合は、運用環境ライセンスのコストもかかりません。他のすべてのデバイスには、シンプルな年間ライセンスが必要です。

### <a name="full-highest-quality-source-code"></a>最高品質の完全なソース コード

長年にわたり、Azure RTOS のソース コードは、品質とわかりやすさに一定の基準を設けてきました。 また、ファイルごとに 1 つの関数を使用するという規則により、簡単なソース ナビゲーションが実現されます。

### <a name="pre-certified-by-tuv-and-ul-to-many-safety-standards"></a>TUV と UL による多くの安全性標準による事前認定

Azure RTOS は、IEC-61508 SIL 4、IEC-62304 SW セーフティ クラス C、ISO 26262 ASIL D、および EN 50128 に従って、安全性が重要なシステムでの使用が SGS-TUV Saar によって認定されています。 この認定により、「電気、電子、プログラマブル電子安全関連系の機能安全」に関する IEC-61508、IEC-62304、ISO 26262、および EN 50128 の最高の安全性整合性レベルに対応する安全性関連ソフトウェアの開発で Azure RTOS を使用できることが確認されます。 ドイツの SGS-Group と TUV Saarland の共同事業を通じて結成された SGS-TUV Saar は、世界中の安全関連システムのための組み込みソフトウェアのテスト、監査、検証、認定を行う、世界有数の公認された独立系企業になりました。 工業安全規格の IEC 61508 と、それから派生したすべての標準 (IEC-62304、ISO 26262 および EN 50128 を含む) は、電気・電子・プログラマブル電子安全関連の医療デバイス、プロセス制御システム、工業機械、自動車および鉄道制御システムの機能安全を保証するために使用されます。

:::image type="content" source="media/partener-logo-sgs-tuv-saar.png" alt-text="SGS-TUV 認定":::

Azure RTOS は、プログラム可能なコンポーネント内のソフトウェアに対する UL 60730-1 付属文書 H、CSA E60730-1 付属文書 H、IEC 60730-1 付属文書 H、UL 60335-1 付属文書 R、IEC 60335-1 付属文書 R、UL 1998 の各安全標準に準拠しているものとして UL によって承認されています。 UL は、独立した安全科学のグローバル企業であり、電気の公的な選定からサステナビリティ、再生可能エネルギー、およびナノテクノロジーにおける革新まで、さまざまな安全性ソリューションの革新を 1 世紀以上にわたって専門としてきました。

:::image type="content" source="media/cru-logo-certification.png" alt-text="CRU UL 認定":::

TUV および UL 認定に関連付けられている成果物 (証明書、安全性マニュアル、テスト レポートなど) は、販売されています。

アプリケーションで追加の認定が必要な場合は、Microsoft を通じて認定サービスを利用し、実際のハードウェア プラットフォームを使用してさまざまな標準にターンキー認定を提供したり、アプリケーション コードをカバーしたりできます。 認定サービスの詳細については、お問い合わせください。

### <a name="eal4-common-criteria-security-certification"></a>EAL4+ コモン クライテリア セキュリティ認定

Azure RTOS は、EAL4+ のコモン クライテリア セキュリティ認定を達成しました。 評価対象 (TOE) は、Azure RTOS ThreadX、Azure RTOS NetX-Duo、Azure RTOS NetX Secure TLS、および Azure RTOS NetX MQTT です。 これは、深い埋め込み型センサー、デバイス、エッジ ルーター、およびゲートウェイに必要な最も一般的な IoT プロトコルを表します。

:::image type="content" source="media/eal-logo-certification.png" alt-text="EAL 認定":::

Microsoft Azure RTOS SC セキュリティ認定に使用される IT セキュリティ評価機関は Brightsight BV で、証明機関は SERTIT です。

### <a name="fips-140-2-validated"></a>FIPS 140-2 の検証

Azure RTOS Crypto ライブラリは、暗号化モジュールの要件を指定する、Federal Information Processing Standards 140-2 (FIPS 140-2) のソフトウェアの認定を受けています。 FIPS 140-2 では、暗号化ベースのセキュリティを使用するすべての連邦政府機関および部門が、暗号化の強度と機能に関連する特定の標準を満たすことが求められています。 これらの暗号化ベースのセキュリティ標準は、カナダと欧州連合でも承認されています。

Azure RTOS Crypt ライブラリに使用される情報セキュリティ評価ラボは atsec でした。証明機関は[米国国立標準技術研究所 (NIST)](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394) です。

### <a name="supports-most-popular-architectures"></a>最も一般的なアーキテクチャをサポート

Azure RTOS は、完全にテストされ、サポートされている、すぐに使える最も一般的な 32 および 64 ビット マイクロプロセッサで動作します。これには、次の高度なアーキテクチャが含まれます。

- **Analog Devices**: SHARC、Blackfin、CM4xx

- **Andes Core**: RISC-V

- **Ambiqmicro**: Apollo MCU

- **ARM**: ARM7、ARM9、ARM11、Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64 ビット/A7x 64 ビット/R4/R5、TrustZone ARMv8-M

- **Cadence**: Xtensa、Diamond

- **CEVA**: PSoC、PSoC 4、PSoC 5、PSoC 6、FM0+、FM3、MF4、WICED WiFi

- **Cypress**: RISC-V

- **EnSilica**: eSi-RISC

- **Infineon**: XMC1000、XMC4000、TriCore

- **Intel および Intel FPGA**: x36/Pentium、XScale、NIOS II、Cyclone、Arria 10

- **Microchip**: AVR32、ARM7、ARM9、Cortex-M3/M4/M7、SAM3/4/7/9/A/C/D/E/G/L/SV、PIC24/PIC32

- **Microsemi**: RISC-V

- **NXP**: LPC、ARM7、ARM9、PowerPC、68 K、i.MX、ColdFire、Kinetis Cortex-M3/M4

- **Renesas**: SH、HS、V850、RX、RZ、Synergy

- **Silicon Labs**: EFM32

- **Synopsys**: ARC 600、700、ARC EM、ARC HS

- **ST**: STM32、ARM7、ARM9、Cortex-M3/M4/M7

- **Tl**: C5xxx、C6xxx、Stellaris、Sitara、Tiva-C

- **Wave Computing**: MIPS32 4K、24 K、34 K、1004 K、MIPS64 5K、microAptiv、interAptiv、proAptiv、M-Class

- **Xilinx**: MicroBlaze、PowerPC 405、ZYNQ、ZYNQ UltraSCALE

*記載されているタイミングとサイズの数値はすべて推定値であり、開発プラットフォームによって異なる場合があります。*

## <a name="in-the-context-of-azure-iot"></a>Azure IoT のコンテキストで

Azure IoT に直接接続したり、Azure IoT Edge 経由で間接的に接続したりするだけでなく、Azure Sphere デバイスでも Azure RTOS を利用できます。 Azure RTOS と Azure Sphere を組み合わせることにより、クラス最高のリアルタイム処理とセキュリティを 1 つのデバイスでまとめて実現できます。
