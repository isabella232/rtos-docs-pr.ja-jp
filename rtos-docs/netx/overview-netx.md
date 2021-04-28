---
title: Azure RTOS NetX を理解する
description: Azure RTOS NetX は、TCP/IP プロトコル標準のハイパフォーマンス実装です。Azure RTOS ThreadX と完全に統合されており、サポートされるすべてのプロセッサで利用できます。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 029f73b755d5c40279125fb010ec35baaaf7f38d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810400"
---
# <a name="overview-of-azure-rtos-netx"></a>Azure RTOS NetX の概要

Azure RTOS NetX は、深く組み込まれたリアルタイム IoT アプリケーション専用に設計された、産業用 TCP/IP IPv4 組み込みネットワーク スタックです。 Azure RTOS NetX は、Microsoft 独自の IPv4 ネットワーク スタックであり、本質的に Azure RTOS のサブセットです。 NetX は、IPv4、TCP、UDP などのコア ネットワーク プロトコルと、その他の高度なアドオン プロトコルの完全なスイートを組み込みアプリケーションに提供します。 小さなフットプリント、高速実行、優れた操作性により、Azure RTOS NetX は、最も要求の厳しい組み込み IoT アプリケーションに最適な選択肢となっています。

## <a name="api-protocols"></a>API のプロトコル

### <a name="telnet"></a>Telnet

* 最小 0.5 KB と 0.3 KB の RAM フットプリント
* クライアントとサーバーのサポート
* 直感的な Telnet API: *nx_telnet_\**

### <a name="auto-ip"></a>Auto IP

* IPv4 アドレス自動割り当て
* 最小 1.2 KB、300 バイトの RAM
* 直感的な AutoIP API: *nx_autoip_\**

### <a name="http---hypertext-transfer-protocolhttp"></a>HTTP - ハイパーテキスト転送プロトコル (HTTP)

* 最小 2.8 KB から 4.8 KB のフラッシュ、0.4 KB から 1.0 KB の RAM フットプリント
* クライアントとサーバーのサポート
* 直感的な HTTP API: *nx_http_\**

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a>SMTP - 簡易メール転送プロトコル (SMTP)

* 最小 4.1 KB と 0.6 KB の RAM フットプリント
* クライアントのサポート
* 直感的な SMTP API: *nx_smtp_\**

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a>DHCP - 動的ホスト構成プロトコル (DHCP)

* 最小 3.6 KB から 4.6 KB のフラッシュ、2.7 KB の RAM フットプリント
* クライアントとサーバーのサポート
* IPv4 のサポート
* 直感的な DHCP API: *nx_dhcp_\**

### <a name="p0p3---post-office-protocol-version-3-pop3"></a>P0P3 - Post Office Protocol Version 3 (POP3)

* 最小 8.1 KB と 1.4 KB の RAM フットプリント
* クライアントのサポート
* 直感的な POP3 API: *nx_pop3_\**

### <a name="snmp---simple-network-management-protocol-snmp"></a>SNMP - 簡易ネットワーク管理プロトコル (SNMP)

* 最小 10.9 KB と 2.6 KB の RAM フットプリント
* VI、V2、V3 のエージェントのサポート
* 直感的な SNMP API: *nx_snmp_\**

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a>FTP、TFTP - ファイル転送プロトコル (FTP)、簡易ファイル転送プロトコル (TFTP)

* FTP - 最小 1.8 KB から 7.2 KB のフラッシュ、0.6 KB から 2.1 KB の RAM フットプリント
* TFTP - 最小 1.7 KB から 2.4 KB のフラッシュ、0.3 KB から 1.8 KB の RAM フットプリント
* クライアントとサーバーのサポート
* 直感的な FTP および TFTP API: <i>nx_ftp_ *</i> または <i>nx_tftp_* </i>

### <a name="ppp---polnt-to-point-protocol-ppp"></a>PPP - Point-to-Point プロトコル (PPP)

* 最小 7.1 KB と 3.8 KB の RAM フットプリント
* 直感的な PPP API: *nx_ppp_\**

### <a name="sntp---simple-network-time-protocol-sntp"></a>SNTP - Simple Network Time Protocol (SNTP)

* 最小 4 KB および 0.5 KB の RAM
* クライアントのサポート
* 直感的な SNTP API: *nx_sntp_\**

### <a name="azure-rtos-netx-api"></a>Azure RTOS NetX API

* 直感的で一貫性のある API
* 名詞 - 動詞の名前付け規則
* 高速のゼロコピー API 実装
* Azure RTOS NetX として簡単に識別できるように、すべての API 関数の先頭を <i>nx_*</i> で統一
* ブロッキング API 関数に用意されたオプションのスレッド タイムアウト
* レガシ ソケット コードを移植するためのオプションの BSD レイヤー

### <a name="igmp---internet-group-management-protocol-igmp"></a>IGMP - インターネット グループ管理プロトコル (IGMP)

* 最小 2.5 KB のフラッシュ
* IPv4 マルチキャスト グループのサポート
* IXIA IxANVL 検証済み
* オプションの IGMP 統計情報
* Azure RTOS TraceX によるシステムレベルのトレース
* 直感的な IGMP API: *nx_igmp_\**

### <a name="udp---user-datagram-protocol-udp"></a>UDP - ユーザー データグラム プロトコル (UDP)

* 最小 2.5 KB のフラッシュ、ソケットあたり 124 ソケット バイトの RAM
* 高速でほぼワイヤスピードの TCP パケット処理:
* RX 95 Mbps (100 Mbps イーサネット)、MCU @100MHz、14% MCU 使用率
* TX 94 Mbps (100 Mbps イーサネット)、MCU @100MHz、10% MCU 使用率
* UDP Fast Path™ テクノロジ
* UDP の数に制限なし
* IXIA IxANVL 検証済み
* ソケット受信時のオプションの中断
* すべての中断時のオプションのタイムアウト
* オプションの UDP 統計情報
* Azure RTOS TraceX によるシステムレベルのトレース
* 直感的な UDP API: *nx_udp_\**

### <a name="tcp---transmission-control-protocol-tcp"></a>TCP - 伝送制御プロトコル (TCP)

* 最小 10.5 KB から 12.5 KB のフラッシュ、ソケットあたり 280 バイトの RAM
* 高速でほぼワイヤスピードの TCP パケット処理:
* RX 93 Mbps (100 Mbps イーサネット)、MCU @100MHz、20% MCU 使用率
* TX 94 Mbps (100 Mbps イーサネット)、MCU @100MHz、27% MCU 使用率
* 信頼性の高い接続
* TCP ソケット数に制限なし
* IXIA IxANVL 検証済み
* ソケット受信/送信時のオプションの中断
* すべての中断時のオプションのタイムアウト
* オプションの TCP 統計情報
* Azure RTOS TraceX によるシステムレベルのトレース
* 直感的な TCP API: *nx_tcp_\**

### <a name="icmp---internet-control-message-protocol-icmp"></a>ICMP - インターネット制御メッセージ プロトコル (ICMP)

* 最小 2.5 KB のフラッシュ
* IPv4 のサポート
* IXIA IxANVL 検証済み
* ping 要求と ping 応答
* ping 要求時のオプションのスレッド中断
* すべての中断時のオプションのタイムアウト
* オプションの ICMP 統計情報
* Azure RTOS TraceX によるシステムレベルのトレース
* 直感的な ICMP API: *nx_icmp_\**

### <a name="ipv4---internet-protocol-ip"></a>IPv4 - インターネット プロトコル (IP)

* 最小 3.5 KB から 8.5 KB のフラッシュ、2 KB から 3 KB の RAM フットプリント
* Piconet™ アーキテクチャ
* 高速でほぼワイヤスピードのパフォーマンス
* 複数インターフェイスのサポート
* マルチホーム サポート
* 静的ルーティングのサポート
* IP の断片化/再構築のサポート
* IPv4 のサポート
* IXIA IxANVL 検証済み
* フェーズ II 対応ロゴ認定
* オプションの IP 統計情報
* 明確に定義された直感的な物理層ドライバー インターフェイス
* Azure RTOS TraceX によるシステムレベルのトレース
* 直感的な IP レイヤー API: *nx_ip_\** 、*nxd_ip_\**
* TUV および UL による IEC 61508 SIL 4、IEC 62304 クラス C、ISO 26262 ASIL D、および EN 50128 SW-SIL4 に対する事前認定

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a>ARP/RARP - アドレス解決プロトコル (ARP)、逆アドレス解決プロトコル (RARP)

* 最小 1.7 KB のフラッシュ、RAM サイズ
* 32 ビット IPv4 と 48 ビット MAC アドレスの動的な解決
* IXIA IxANVL 検証済み
* 柔軟なユーザー定義の ARP キャッシュ
* Gratuitous ARP のサポート
* アプリケーションによって決定されるオプションの ARP/RARP 統計情報
* Azure RTOS TraceX によるシステムレベルのトレース
* 直感的な ARP/RARP API: *nx_arp_\** 、*nx_rarp_\**

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a>イーサネット、WiFi、Bluetooth LE、15.4 など

## <a name="small-footprint"></a>小さなフットプリント

Azure RTOS NetX では、基本的な IP および UDP のサポートに、9 KB から 15 KB の非常に小さなフットプリントが実現されています。 TCP 機能を使用するには、追加で 10 KB から 13 KB の命令領域メモリが必要です。 Azure RTOS NetX の RAM 使用量は、通常、2.6 KB から 3.6 KB に、アプリケーションによって定義されるパケット プール メモリを加えた量になります。 Azure RTOS ThreadX と同様に、Azure RTOS NetX のサイズは、アプリケーションで使用されるサービスに基づいて自動的にスケーリングされます。 これにより、複雑な構成やビルド パラメーターが実質的に不要になるため、開発者の作業がより簡単になります。

## <a name="fast-execution"></a>高速実行

Azure RTOS NetX は、ゼロコピーのパケット送信/受信実装を提供します。また、Azure RTOS ThreadX と高度に統合されており、可能な限り最速のパフォーマンスを実現します。 たとえば、Azure RTOS NetX では通常、プロセッサ サイクルのごく一部のみを使用しながら、80 MHz (またはそれ以下の) プロセッサでほぼワイヤスピードのデータ転送を実現します。

## <a name="simple-easy-to-use"></a>シンプルで優れた操作性

Azure RTOS NetX は簡単に使用できます。 Azure RTOS NetX API は直感的かつ高機能です。 API 名は、他のネットワーク製品でよく見られる略語や大幅に省略された名前ではなく、実際の単語で構成されています。 すべての Azure RTOS NetX API は、先頭に *nx_* が付き、名詞 - 動詞の名前付け規則に従っています。 さらに、API 全体で機能に一貫性があります。 たとえば、中断を実行するすべての API 関数には、同様に機能するオプションのタイムアウトがあります。 レガシ アプリケーションに対しては、Azure RTOS NetX で追加の BSD ソケット互換レイヤーが提供されます。 このレイヤーは、開発者が大規模なネットワーク アプリケーションを簡単に移行するのに役立ちます。

## <a name="interoperability-verification"></a>相互運用性の検証

Azure RTOS NetX は RFC 標準に準拠しており、ほとんどのベンダーのデバイスとの完全な相互運用性を提供します。 Azure RTOS NetX では、Azure RTOS NetX コア TCP/IP プロトコル実装に業界標準の IxANVL (自動ネットワーク検証ライブラリ) も利用しています。

## <a name="advanced-technology"></a>高度なテクノロジ

Azure RTOS NetX は、次の機能を備えた高度なテクノロジです。

* Piconet™ アーキテクチャ
* 自動スケーリング
* UDP Fast-Path™ テクノロジ
* 柔軟なパケット管理
* ゼロコピー API と実装
* マルチホーム サポート
* すべての中断時のオプションのタイムアウト
* 静的ルーティングのサポート
* Azure RTOS TraceX システム分析のサポート

## <a name="fastest-time-to-market"></a>市場投入までの時間を最短化

Azure RTOS NetX は、インストール、習得、使用、デバッグ、検証、認定、保守が簡単です。 その結果、Azure RTOS NetX は、Broadcom や Gainspan などが提供する多くの SoC を含む、組み込み型 IoT デバイス向けの最も一般的な TCP/IP スタックの 1 つとなっています。 一貫した市場投入までの時間の優位性は、次の要素を基に構築されています。

* 質の高いドキュメント - [Azure RTOS NetX ユーザー ガイド](about-this-guide.md)を参照し、ご自身の目でお確かめください
* 完全なソース コードを提供
* 使いやすい API
* 包括的で高度な機能セット

## <a name="one-simple-license"></a>シンプルな 1 つのライセンス

ソース コードの使用とテストにコストはかかりません。事前にライセンスされたデバイスにデプロイする場合は、運用環境ライセンスのコストはかかりません。他のすべてのデバイスには、シンプルな年間ライセンスが必要です。

## <a name="full-highest-quality-source-code"></a>最高品質の完全なソース コード

長年にわたり、Azure RTOS NetX のソース コードは、品質とわかりやすさに一定の基準を設けてきました。 また、ファイルごとに 1 つの関数を使用するという規則により、簡単なソース ナビゲーションが実現されます。

## <a name="supports-most-popular-architectures"></a>最も一般的なアーキテクチャをサポート

Azure RTOS NetX は、完全にテストされ、サポートされている、すぐに使える最も一般的な 32 および 64 ビット マイクロプロセッサで動作します。これには、次の高度なアーキテクチャが含まれます。

**Analog Devices**: SHARC、Blackfin、CM4xx

**Andes Core**: RISC-V

**Ambiqmicro**: Apollo MCU

**ARM**: ARM7、ARM9、ARM11、Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64 ビット/A7x 64 ビット/R4/R5、TrustZone ARMv8-M

**Cadence**: Xtensa、Diamond

**CEVA**: PSoC、PSoC 4、PSoC 5、PSoC 6、FM0+、FM3、MF4、WICED WiFi

**Cypress**: RISC-V

**EnSilica**: eSi-RISC

**Infineon**: XMC1000、XMC4000、TriCore

**Intel および Intel FPGA**: x36/Pentium、XScale、NIOS II、Cyclone、Arria 10

**Microchip**: AVR32、ARM7、ARM9、Cortex-M3/M4/M7、SAM3/4/7/9/A/C/D/E/G/L/SV、PIC24/PIC32

**Microsemi**: RISC-V

**NXP**: LPC、ARM7、ARM9、PowerPC、68 K、i.MX、ColdFire、Kinetis Cortex-M3/M4

**Renesas**: SH、HS、V850、RX、RZ、Synergy

**Silicon Labs**: EFM32

**Synopsys**: ARC 600、700、ARC EM、ARC HS

**ST**: STM32、ARM7、ARM9、Cortex-M3/M4/M7

**Tl**: C5xxx、C6xxx、Stellaris、Sitara、Tiva-C

**Wave Computing**: MIPS32 4K、24 K、34 K、1004 K、MIPS64 5K、microAptiv、interAptiv、proAptiv、M-Class

**Xilinx**: MicroBlaze、PowerPC 405、ZYNQ、ZYNQ UltraSCALE

*記載されているタイミングとサイズの数値はすべて推定値であり、開発プラットフォームによって異なる場合があります。*
