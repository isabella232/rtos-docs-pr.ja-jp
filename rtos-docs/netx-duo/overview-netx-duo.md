---
title: Azure RTOS NetX Duo を理解する
description: Azure RTOS NetX Duo は、深い埋め込み型のリアルタイム IoT アプリケーション用に特に設計された高度な商用 TCP/IP ネットワーク スタックです。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 2339da391e52b437a2111ae439cccf41e038bdcf
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811741"
---
# <a name="overview-of-azure-rtos-netx-duo"></a>Azure RTOS NetX Duo の概要

Azure RTOS NetX Duo 埋め込み型 TCP/IP ネットワーク スタックは、深い埋め込み型のリアルタイム IoT アプリケーション専用に設計された、Microsoft が提供する高度な商用デュアル IPv4 および IPv6 TCP/IP ネットワーク スタックです。 NetX Duo は、コア ネットワーク プロトコル (IPv4、IPv6、TCP、UDP など) と、その他の高度なアドオン プロトコルの完全なスイートを埋め込み型アプリケーションに提供します。 Azure RTOS NetX Duo は、Azure RTOS NetX Secure IPsec や Azure RTOS NetX Secure SSL/TLS/DTLS を含む追加のアドオン セキュリティ製品を介してセキュリティを提供します。 これらすべてを小さなフットプリント、高速な処理、優れた使いやすさと組み合わせることで、Azure RTOS NetX Duo は、最も要求の厳しい埋め込み型 IoT アプリケーションに最適な選択肢となります。

## <a name="api-protocols"></a>API プロトコル

### <a name="mqtt"></a>MQTT

* Messaging Queue Telemetry Transport (MQTT)
* 最小 2.7 KB のフラッシュ
* 直感的な MQTT API: *nx_mqtt_* \*

### <a name="auto-ip"></a>Auto IP

* IPv4 アドレスの自動割り当て
* 最小 1.2 KB、300 バイトの RAM
* 直感的な AutoIP API: *nx_autoip_\**

### <a name="http-https"></a>HTTP、HTTPS

#### <a name="http-10"></a>HTTP 1.0

* ハイパーテキスト転送プロトコル (HTTP)
* 最小 2.8 KB から 4.8 KB のフラッシュ/0.4 KB から 1.0 KB の RAM
* クライアントとサーバーのサポート
* 直感的な API: *nx_http_\**

#### <a name="httphttps-11"></a>HTTP/HTTPS 1.1

* ハイパーテキスト転送プロトコル (HTTP)
* 最小 3.0 KB から 9.5 KB のフラッシュ/0.5 KB から 2 KB の RAM
* クライアントとサーバーのサポート
* 複数の受信クライアント セッション
* プレーンテキストと暗号化された HTTPS
* 永続的な接続のサポート
* マルチパート ファイルのアップロード
* Azure RTOS NetX Secure TLS と完全に統合
* 直感的な API: *nx_web_http\**

### <a name="smtp"></a>SMTP

* 簡易メール転送プロトコル (SMTP)
* 最小 4.1 KB と 0.6 KB の RAM フットプリント
* クライアントのサポート
* 直感的な SMTP API: *nx_smtp_\**

### <a name="dhcp"></a>DHCP

* 動的ホスト構成プロトコル (DHCP)
* 最小 3.6 KB から 4.6 KB のフラッシュ、2.7 KB の RAM フットプリント
* クライアントとサーバーのサポート
* IPv4 および IPv6 のサポート
* 直感的な DHCP API: *nx_dhcp_\**

### <a name="nat"></a>NAT

* ネットワーク アドレス変換 (NAT)
* 最小 3.5 K6 と 0.6 KB の RAM フットプリント
* IPv4 アドレスのサポート
* 直感的な NAT API: *nx_nat_\**
* NAT は、Azure RTOS NetX Duo でのみ使用可能

### <a name="snmp"></a>SNMP

* 簡易ネットワーク管理プロトコル (SNMP)
* 最小 10.9 KB と 2.6 KB の RAM フットプリント
* VI、V2、V3 のエージェントのサポート
* 直感的な SNMP API: *nx_snmp_\**

### <a name="dns-mdns-dns-sd"></a>DNS、mDNS、DNS-SD

* ドメイン ネーム システム (DNS)
* マルチキャスト ドメイン ネーム システム (mDNS)
* DNS ベースのサービス検出 (DNS-SD)
* DNS 最小 2.4 KB から 3 KB のフラッシュ、1 KB の RAM フットプリント
* クライアントのサポート
* 直感的な API: *nx_dns_\**
* mDNS と DNS-SD は、Azure RTOS NetX Duo でのみ使用可能

### <a name="p0p3"></a>P0P3

* Post Office Protocol Version 3 (POP3)
* 最小 8.1 KB と 1.4 KB の RAM フットプリント
* クライアントのサポート
* 直感的な P0P3 API: *nx_pop3_\**

### <a name="telnet"></a>TELNET

* 最小 0.5 KB と 0.3 KB の RAM フットプリント
* クライアントとサーバーのサポート
* 直感的な Telnet API: *nx_telnet_\**

### <a name="ftp-tftp"></a>FTP、TFTP

* ファイル転送プロトコル (FTP)
* 簡易ファイル転送プロトコル (TFTP)
* FTP 最小 1.8 KB から 7.2 KB のフラッシュ、0.6 KB から 2.1 KB の RAM フットプリント
* TFTP 最小 1.7 KB から 2.4 KB のフラッシュ、0.3 KB から 1.8 KB の RAM フットプリント
* クライアントとサーバーのサポート
* 直感的な FTP および TFTP API: *nx_ftp_\** または *nx_tftp_\**

### <a name="ppp-pppoe"></a>PPP、PPPoE

* Point-to-Point プロトコル (PPP)
* Point-to-Point Protocol over Ethernet (PPPoE)
* 最小 7.1 KB と 3.8 KB の RAM フットプリント
* 直感的な PPP API: *nx_ppp_\**

* PPPoE は、Azure RTOS NetX Duo でのみ使用可能

### <a name="sntp"></a>SNTP

* Simple Network Time Protocol (SNTP)
* 最小 4 KB および 0.5 KB の RAM
* クライアントのサポート
* 直感的な SNTP API: *nx_sntp_\**

### <a name="azure-rtos-netx-duo-api"></a>Azure RTOS NetX Duo API

* 直感的で一貫性のある API
* 名詞 - 動詞の名前付け規則
* 高速のゼロコピー API 実装
* すべての API の先頭を <i>nx_*</i> にして、Azure RTOS NetX として簡単に識別
* ブロックしている API にオプションのスレッド タイムアウトがある
* 詳細については、[Azure RTOS NetX Duo のユーザー ガイド](about-this-guide.md)を参照してください。
* レガシ ソケット コードを移植するためのオプションの BSD レイヤー

### <a name="igmp"></a>IGMP

* インターネット グループ管理プロトコル (IGMP)
* 最小 2.5 KB のフラッシュ
* IPv4 マルチキャスト グループのサポート
* IXIA IxANVL 検証済み
* オプションの IGMP 統計情報
* Azure RTOS ThreadX によるシステムレベルのトレース
* 直感的な IGMP API: *nx_igmp_\**

### <a name="azure-rtos-netx-secure-dtls"></a>Azure RTOS NetX Secure DTLS

* データグラム トランスポート層セキュリティ (DTLS) 1.0 および 1.2
* 最小 11 KB のフラッシュ
* 高速、ソフトウェア RSA 2048 ビットキーのサイズ ～ 1 秒 @120MHz
* 合理化された X.509 実装
* Azure RTOS NetX Duo UDP ソケットと完全に統合
* ハードウェア暗号化のサポート
* ソフトウェアの暗号化のサポート: RSA (すべてのキー サイズ)、AES、DES/3DES、ECC、HMAC、MD5、SHA-1、SHA-2 (SHA-224、SHA-256、SHA-384、SHA-512)
* ECDSA (署名) と ECDH (暗号化) を使用した楕円曲線暗号 (ECC)、P 曲線 192/224/256/384/521 を含む
* 暗号化キーのサポート (ハードウェアに依存)

### <a name="azure-rtos-netx-secure-tls"></a>Azure RTOS NetX Secure TLS

* トランスポート層セキュリティ (TLS) 1.0、1.1、および 1.2
* 最小 8.8 KB のフラッシュ
* 高速、ソフトウェア RSA 2048 ビットキーのサイズ ～ 1 秒 @120MHz
* 合理化された X.509 実装
* Azure RTOS NetX Duo TCP ソケットと完全に統合
* ハードウェア暗号化のサポート
* ソフトウェアの暗号化のサポート: RSA (すべてのキー サイズ)、AES、DES/3DES、ECC、HMAC、MD5、SHA-1、SHA-2 (SHA-224、SHA-256、SHA-384、SHA-512)
* ECDSA (署名) と ECDH (暗号化) を使用した楕円曲線暗号 (ECC)、P 曲線 192/224/256/384/521 を含む
* 暗号化キーのサポート (ハードウェアに依存)

### <a name="icmp"></a>ICMP

* インターネット制御メッセージ プロトコル (ICMP)
* 最小 2.5 KB のフラッシュ
* IPv4 および IPv6 のサポート
* IXIA IxANVL 検証済み
* ping 要求と ping 応答
* ping 要求に対するオプションのスレッドの中断
* すべての中断時のオプションのタイムアウト
* オプションの ICMP 統計情報
* Azure RTOS TraceX によるシステムレベルのトレース
* 直感的な ICMP API: *nx_icmp_\**

### <a name="udp"></a>UDP

* ユーザー データグラム プロトコル (UDP)
* 最小 2.5 KB のフラッシュ、ソケットあたり 124 ソケット バイトの RAM
* 高速でほぼワイヤスピードの TCP パケット処理:
    * RX 95 Mbps (100 Mbps イーサネット)、MCU @100MHz、14% MCU 使用率
    * TX 94 Mbps (100 Mbps イーサネット)、MCU @100MHz、10% MCU 使用率
* UDP Fast Path™ テクノロジ
* UDP の数に制限なし
* IXIA IxANVL 検証済み
* ソケット受信時のオプションによる中断
* すべての中断時のオプションのタイムアウト
* オプションの UDP 統計情報
* Azure RTOS TraceX によるシステムレベルのトレース
* 直感的な UDP API: *nx_udp_\**

### <a name="tcp"></a>TCP

* 伝送制御プロトコル (TCP)
* 最小 10.5 K8 から 12.5 KB のフラッシュ、ソケットあたり 280 バイトの RAM
* 高速でほぼワイヤスピードの TCP パケット処理:
    * RX 93 Mbps (100 Mbps イーサネット)、MCU @100MHz、20% MCU 使用率
    * TX 94 Mbps (100 Mbps イーサネット)、MCU @100MHz、27% MCU 使用率
* 信頼性の高い接続
* TCP ソケット数に制限なし
* IXIA IxANVL 検証済み
* ソケットの受信/送信でオプションの中断
* すべての中断時のオプションのタイムアウト
* オプションの TCP 統計情報
* Azure RTOS TraceX によるシステムレベルのトレース
* 直感的な TCP API: *nx_tcp_\**

### <a name="arprarp"></a>ARP/RARP

* アドレス解決プロトコル (ARP)
* 逆アドレス解決プロトコル (RARP)
* 最小 1.7 KB のフラッシュ、RAM サイズ
* 32 ビット IPv4 と 48 ビット MAC アドレスの動的な解決
* IXIA IxANVL 検証済み
* 柔軟なユーザー定義の ARP キャッシュ
* Gratuitous ARP サポート
* アプリケーションによって決定されるオプションの ARP/RARP 統計
* Azure RTOS TraceX によるシステムレベルのトレース
* 直感的な ARP/RARP API: *nx_arp_\** 、*nx_rarp_\**

### <a name="ipv4-amp-ipv6"></a>IPv4 および IPv6

* インターネット プロトコル (IP)●いんたーねっとぷろとこる(ip)○
* 最小 3.5 KB から 8.5 KB のフラッシュ、2 KB から 3 KB の RAM フットプリント
* Piconet™ アーキテクチャ
* 高速でほぼワイヤスピードのパフォーマンス
* 複数インターフェイスのサポート
* マルチホーム サポート
* 静的ルーティングのサポート
* IP の断片化/再構築のサポート
* IPv4 および IPv6 アドレスのサポート
* IXIA IxANVL 検証済み
* フェーズ II IPv6 対応ロゴ認定
* オプションの IP 統計情報
* 明確に定義された直観的な物理レイヤー ドライバー インターフェイス
* Azure RTOS TraceX によるシステムレベルのトレース
* 直感的な IP レイヤー API: *nx_ip_\** 、*nxd_ip_\** 、*nxd_ipv6_\**
* TUV および UL による IEC 61508 SIL 4、IEC 62304 クラス C、ISO 26262 ASIL D、および EN 50128 SW-SIL4 に対する事前認定

### <a name="azure-rtos-netx-secure-ipsec"></a>Azure RTOS NetX Secure IPSEC

* インターネット プロトコル セキュリティ (IPSEC)
* IP レイヤー
* ハードウェア暗号化のサポート
* ソフトウェア暗号化のサポート (以下を含む):
    * DES、3DES
    * AES
    * HMAC-MD5
    * HMAC-SHA1
* インターネット キー交換 (IKE) バージョン 2 のサポート
* 直感的な IPsec API: *nx_ipsec_\**
* IPsec は、Azure RTOS NetX Duo でのみ使用可能

## <a name="small-footprint"></a>小さいフットプリント

Azure RTOS NetX Duo では、基本的な IP および UDP のサポートに、9 KB から 15 KB の非常に小さなフットプリントが実現されています。 TCP 機能を使用するには、追加で 10 KB から 13 KB の命令領域メモリが必要です。 Azure RTOS NetX Duo の RAM の使用率は、通常、2.6 KB から 3.6 KB に、アプリケーションによって定義されるパケット プール メモリを加えた範囲になります。 Azure RTOS ThreadX と同様に、Azure RTOS NetX Duo のサイズは、アプリケーションで使用されるサービスに基づいて自動的にスケーリングされます。 これにより、複雑な構成やビルド パラメーターが実質的に不要になるため、開発者の作業がより簡単になります。

## <a name="fast-execution"></a>高速実行

Azure RTOS NetX Duo は、Azure RTOS ThreadX と高度に統合された、ゼロコピーのパケット送信/受信実装を提供し、最速のパフォーマンスを実現します。 たとえば、Azure RTOS NetX Duo は、通常、プロセッサ サイクルのごく一部のみを使用しながら、80 MHz (またはそれ以下の) プロセッサでほぼワイヤスピードのデータ転送を実現します。

## <a name="simple-easy-to-use"></a>シンプルで優れた操作性

Azure RTOS NetX Duo API は、直感的でわかりやすく、高い機能を備えています。

API 名は、略語や、他のネットワーク製品で一般的な大幅に省略された名前ではなく、実際の言葉で構成されています。 すべての Azure RTOS NetX Duo API は、先頭に *nx_* が付き、その後に名詞 - 動詞の名前付け規則が続きます。 さらに、API 全体に機能的な一貫性があります。 たとえば、中断されるすべての API 関数には、同じ方法で動作するオプションのタイムアウトがあります。

レガシ アプリケーションに対しては、Azure RTOS NetX Duo で追加の BSD ソケット互換レイヤーが提供されます。 このレイヤーは、開発者が大規模なネットワーク アプリケーションを簡単に移行するのに役立ちます。

## <a name="safe-and-secure"></a>高い安全性

Azure RTOS NetX Duo はセキュリティで保護されています。 このセキュリティは、IPsec、SSL、TLS、DTLS などのアドオン セキュリティ製品を通じて提供されます。 また、アプリケーションでは Azure RTOS NetX Duo へのすべての外部アクセスを完全に制御できるため、セキュリティ上のリスクをより簡単に判断できます。

Microsoft Azure RTOS には、通信をセキュリティで保護し、基になる MCU/MPU ハードウェア保護メカニズムを使用してコードとデータの分離を作成するためのコンポーネントを含む OEM があります。 特定のユース ケースに関連して進化し続けるセキュリティ要件をデバイスが完全に満たすようにすることは、最終的には、デバイス ビルダーの責任です。

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a>TUV と UL による多くの安全性標準による事前認定

Azure RTOS NetX Duo は、IEC-61508 SIL 4、IEC-62304 SW セーフティ クラス C、ISO 26262 ASIL D、および EN 50128 に従って、安全性が重要なシステムでの使用を SGS-TUV Saar によって認定されています。 この認定により、「電気、電子、プログラマブル電子安全関連系の機能安全」に関する IEC-61508、IEC-62304、ISO 26262、および EN 50128 の最高の安全性整合性レベルに対応する安全性関連ソフトウェアの開発で Azure RTOS NetX Duo を使用できることが確認されます。 ドイツの SGS-Group と TUV Saarland の共同事業を通じて結成された SGS-TUV Saar は、世界中の安全関連システムのための組み込みソフトウェアのテスト、監査、検証、認定を行う、世界有数の公認された独立系企業になりました。 工業安全規格の IEC 61508 と、それから派生したすべての標準 (IEC-62304、ISO 26262 および EN 50128 を含む) は、電気・電子・プログラマブル電子安全関連の医療デバイス、プロセス制御システム、工業機械、自動車および鉄道制御システムの機能安全を保証するために使用されます。

:::image type="content" source="media/overview-netx-duo/partener-logo-sgs-tuv-saar.png" alt-text="SGS-TUV 認定":::

Azure RTOS NetX Duo は、プログラム可能なコンポーネント内のソフトウェアに対する UL 60730-1 付属文書 H、CSA E60730-1 付属文書 H、IEC 60730-1 付属文書 H、UL 60335-1 付属文書 R、IEC 60335-1 付属文書 R、UL 1998 の各安全標準に準拠しているものとして UL によって承認されています。 UL は、独立した安全科学のグローバル企業であり、電気の公的な選定からサステナビリティ、再生可能エネルギー、およびナノテクノロジーにおける革新まで、さまざまな安全性ソリューションの革新を 1 世紀以上にわたって専門としてきました。

:::image type="content" source="media/overview-netx-duo/cru-logo-certification.png" alt-text="CRU UL 認定":::

TUV および UL 認定に関連付けられている成果物 (証明書、安全性マニュアル、テスト レポートなど) は、販売されています。

アプリケーションで追加の認定が必要な場合は、Microsoft を通じて認定サービスを利用し、実際のハードウェア プラットフォームを使用してさまざまな標準にターンキー認定を提供したり、アプリケーション コードをカバーしたりできます。 認定サービスの詳細については、お問い合わせください。

## <a name="eal4-common-criteria-security-certification"></a>EAL4+ コモン クライテリア セキュリティ認定

Azure RTOS は、EAL4+ のコモン クライテリア セキュリティ認定を達成しました。 評価対象 (TOE) は、Azure RTOS ThreadX、Azure RTOS NetX Duo、Azure RTOS NetX Secure TLS、および Azure RTOS NetX MQTT です。 これは、深い埋め込み型センサー、デバイス、エッジ ルーター、およびゲートウェイに必要な最も一般的な IoT プロトコルを表します。

:::image type="content" source="media/overview-netx-duo/eal-logo-certification.png" alt-text="EAL 認定":::

Microsoft Azure RTOS SC セキュリティ認定に使用される IT セキュリティ評価機関は Brightsight BV で、証明機関は SERTIT です。

## <a name="fips-140-2-validated"></a>FIPS 140-2 の検証

Azure RTOS NetX Crypto ライブラリは、暗号化モジュールの要件を指定する、Federal Information Processing Standards 140-2 (FIPS 140-2) のソフトウェアの認定を受けています。 FIPS 140-2 では、暗号化ベースのセキュリティを使用するすべての連邦政府機関および部門が、暗号化の強度と機能に関連する特定の標準を満たすことが求められています。 これらの暗号化ベースのセキュリティ標準は、カナダと欧州連合でも承認されています。

Azure RTOS NetX Crypt ライブラリに使用される情報セキュリティ評価ラボは atsec でした。証明機関は米国国立標準技術研究所 (NIST) です。 詳細については、[NIST の Web サイト](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394)を参照してください。

## <a name="interoperability-verification"></a>相互運用性の検証

NetX Duo は RFC 標準に準拠し、ほとんどのベンダーのデバイスとの完全な相互運用性を提供します。

![IPv6 対応のロゴ](./media/overview-netx-duo/ipv6-ready-logo.png)

Azure RTOS NetX Duo は、厳密な IPv6 対応のロゴ認定を達成する唯一の埋め込み型 TCP/IP スタックです。このロゴは、準拠と相互運用性のテストに合格し、IPv6 フォーラムによって管理および検証されていることを証明します。 NetX Duo では、NetX Duo コア TCP/IP プロトコルの実装に対して業界標準の IxANVL (自動ネットワーク検証ライブラリ) も利用されています。

## <a name="comprehensive-iot-solution"></a>包括的な IoT ソリューション

Azure RTOS NetX Duo では、基本的な IP および UDP のサポートに、9 KB から 15 KB の非常に小さなフットプリントが実現されています。 NetX Duo では、深い埋め込み型 IoT アプリケーション向けの最も包括的な TCP/IP ネットワークの 1 つが提供されます。 このサポートには、次のアドオン プロトコル製品が含まれています。

MQTT、CoAP、LWM2M、6LoWPAN、SSL/TLS/DTLS、IPsec、AutoIP、DHCP、DNS、mDNS、DNS-SD、FTP、HTTP、IPsec、NAT、POP3、PPP、PPPoE、SMTP、SNMP v1/2/3、Telnet、TFTP

## <a name="advanced-technology"></a>高度なテクノロジ

Azure RTOS NetX Duo は次の機能を備えた高度なテクノロジです。

* Piconet™ アーキテクチャ
* 自動スケーリング
* UDP Fast-Path Technology™
* 柔軟なパケット管理
* ゼロコピー API と実装
* マルチホーム サポート
* すべての中断時のオプションのタイムアウト
* 静的ルーティングのサポート
* IPsec
* SSL/TLS/DTLS
* Azure RTOS TraceX システム分析のサポート

## <a name="fastest-time-to-market"></a>市場投入までの時間を短縮

Azure RTOS NetX Duo は、簡単にインストール、学習、使用、デバッグ、検証、認定、保守を行うことができます。 その結果、NetX Duo は、Broadcom や Gainspan などの多くの SoC を含む組み込み型 IoT デバイス向けの最も一般的な TCP/IP スタックの 1 つです。次の点に基づいて、市場投入までの時間を一貫して短く保つことができます。

* 品質の高いドキュメント – [Azure RTOS NetX Duo のユーザー ガイド](about-this-guide.md)をご確認ください。
* 完全なソース コードを使用可能
* 使いやすい API
* 包括的かつ高度な機能セット

## <a name="one-simple-license"></a>シンプルな 1 つのライセンス

ソース コードの使用とテストに費用はかからず、事前にライセンスされたデバイスに展開する場合は、運用環境ライセンスにはコストがかかりません。その他のすべてのデバイスには、シンプルな年間ライセンスが必要です。

## <a name="full-highest-quality-source-code"></a>完全な最高品質のソース コード

長年にわたり、Azure RTOS NetX Duo のソース コードは、品質と分かりやすさに一定の基準を設けてきました。 また、ファイルごとに 1 つの関数を使用するという規則により、簡単にソースを移動できます。

## <a name="supports-most-popular-architectures"></a>最も一般的なアーキテクチャをサポート

Azure RTOS NetX Duo は、すぐに利用可能で完全なテストとサポートが実現されている、最も一般的な 32/64 ビットのマイクロプロセッサで動作します。これには、次の高度なアーキテクチャが含まれます。

**Analog Devices**: SHARC、Blackfin、CM4xx

**Andes Core**: RISC-V

**Ambiqmicro**: Apollo MCU

**ARM**: RM7、ARM9、ARM11、Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64 ビット/A7x 64 ビット/R4/R5、TrustZone ARMv8-M

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

**Silicon** Labs: EFM32

**Synopsys**: ARC 600、700、ARC EM、ARC HS

**ST**: STM32、ARM7、ARM9、Cortex-M3/M4/M7

**Tl**: C5xxx、C6xxx、Stellaris、Sitara、Tiva-C

**Wave Computing**: MIPS32 4K、24 K、34 K、1004 K、MIPS64 5K、microAptiv、interAptiv、proAptiv、M-Class

**Xilinx**: MicroBlaze、PowerPC 405、ZYNQ、ZYNQ UltraSCALE

*表示されるすべてのタイミングとサイズの数値は推定値であり、開発プラットフォームによって異なる場合があります。*

## <a name="related-services"></a>関連サービス

Azure Security Center for IoT RTOS セキュリティ モジュールでは、Azure RTOS デバイス向けの包括的なセキュリティ ソリューションが提供されます。 Azure RTOS のセキュリティ モジュールは、悪意のあるネットワーク アクティビティの検出、カスタム アラート ベースのデバイス動作での基準設定、およびデバイス セキュリティ検疫の強化に役立ちます。 [Azure RTOS のセキュリティ モジュール](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos)の詳細を確認するか、[Azure RTOS 用セキュリティ モジュールの構成](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module)に関するクイックスタートを開始してください。

## <a name="next-steps"></a>次のステップ

NetX Duo の詳細については、最初に、[Azure RTOS NetX Duo のユーザー ガイド](about-this-guide.md)を参照してください。
