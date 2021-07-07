---
title: Azure RTOS NetX Duo を理解する
description: Azure RTOS NetX Duo は、深い埋め込み型のリアルタイム IoT アプリケーション用に特に設計された高度な商用 TCP/IP ネットワーク スタックです。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 6112ab5cb711ca1a5c83fd5cd4b43abc0302c6c5
ms.sourcegitcommit: f9d8cf23becf96d5bd6d31dd54f89c48962fd09b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549334"
---
# <a name="overview-of-azure-rtos-netx-duo"></a>Azure RTOS NetX Duo の概要

Azure RTOS NetX Duo 埋め込み型 TCP/IP ネットワーク スタックは、深い埋め込み型のリアルタイム IoT アプリケーション専用に設計された、Microsoft が提供する高度な商用デュアル IPv4 および IPv6 TCP/IP ネットワーク スタックです。 NetX Duo は、コア ネットワーク プロトコル (IPv4、IPv6、TCP、UDP など) と、その他の高度なアドオン プロトコルの完全なスイートを埋め込み型アプリケーションに提供します。 Azure RTOS NetX Duo は、Azure RTOS NetX Secure IPsec や Azure RTOS NetX Secure SSL/TLS/DTLS を含む追加のアドオン セキュリティ製品を介してセキュリティを提供します。 これらすべてを小さなフットプリント、高速な処理、優れた使いやすさと組み合わせることで、Azure RTOS NetX Duo は、最も要求の厳しい埋め込み型 IoT アプリケーションに最適な選択肢となります。

## <a name="api-protocols"></a>API プロトコル

### <a name="mqtt"></a>MQTT

* Messaging Queue Telemetry Transport (MQTT)
* 最小 2.7 KB のフラッシュ

### <a name="auto-ip"></a>Auto IP

* IPv4 アドレス自動割り当て
* 最小 1.2 KB、300 バイトの RAM

### <a name="http-https"></a>HTTP、HTTPS

#### <a name="http-10"></a>HTTP 1.0

* ハイパーテキスト転送プロトコル (HTTP)
* 最小 2.8 KB から 4.8 KB のフラッシュ/0.4 KB から 1.0 KB の RAM
* クライアントとサーバーのサポート

#### <a name="httphttps-11"></a>HTTP/HTTPS 1.1

* ハイパーテキスト転送プロトコル (HTTP)
* 最小 3.0 KB から 9.5 KB のフラッシュ/0.5 KB から 2 KB の RAM
* クライアントとサーバーのサポート
* 複数の受信クライアント セッション
* プレーンテキストと暗号化された HTTPS
* 永続的な接続のサポート
* マルチパート ファイルのアップロード
* Azure RTOS NetX Secure TLS と完全に統合

### <a name="smtp"></a>SMTP

* 簡易メール転送プロトコル (SMTP)
* 最小 4.1 KB と 0.6 KB の RAM フットプリント
* クライアントのサポート

### <a name="dhcp"></a>DHCP

* 動的ホスト構成プロトコル (DHCP)
* 最小 3.6 KB から 4.6 KB のフラッシュ、2.7 KB の RAM フットプリント
* クライアントとサーバーのサポート
* IPv4 および IPv6 のサポート

### <a name="nat"></a>NAT

* ネットワーク アドレス変換 (NAT)
* 最小 3.5 K6 と 0.6 KB の RAM フットプリント
* IPv4 アドレスのサポート
* NAT は、Azure RTOS NetX Duo でのみ使用可能

### <a name="snmp"></a>SNMP

* 簡易ネットワーク管理プロトコル (SNMP)
* 最小 10.9 KB と 2.6 KB の RAM フットプリント
* VI、V2、V3 のエージェントのサポート

### <a name="dns-mdns-dns-sd"></a>DNS、mDNS、DNS-SD

* ドメイン ネーム システム (DNS)
* マルチキャスト ドメイン ネーム システム (mDNS)
* DNS ベースのサービス検出 (DNS-SD)
* DNS 最小 2.4 KB から 3 KB のフラッシュ、1 KB の RAM フットプリント
* クライアントのサポート
* mDNS と DNS-SD は、Azure RTOS NetX Duo でのみ使用可能

### <a name="pop3"></a>POP3

* Post Office Protocol Version 3 (POP3)
* 最小 8.1 KB と 1.4 KB の RAM フットプリント
* クライアントのサポート

### <a name="telnet"></a>Telnet

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
* ping 要求時のオプションのスレッド中断
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
* Gratuitous ARP のサポート
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

## <a name="safe-and-secure"></a>高い安全性

Azure RTOS NetX Duo はセキュリティで保護されています。 このセキュリティは、IPsec、SSL、TLS、DTLS などのアドオン セキュリティ製品を通じて提供されます。 また、アプリケーションでは Azure RTOS NetX Duo へのすべての外部アクセスを完全に制御できるため、セキュリティ上のリスクをより簡単に判断できます。

Microsoft Azure RTOS には、通信をセキュリティで保護し、基になる MCU/MPU ハードウェア保護メカニズムを使用してコードとデータの分離を作成するためのコンポーネントを含む OEM があります。 特定のユース ケースに関連して進化し続けるセキュリティ要件をデバイスが完全に満たすようにすることは、最終的には、デバイス ビルダーの責任です。


## <a name="interoperability-verification"></a>相互運用性の検証

NetX Duo は RFC 標準に準拠し、ほとんどのベンダーのデバイスとの完全な相互運用性を提供します。

![IPv6 対応のロゴ](./media/overview-netx-duo/ipv6-ready-logo.png)

Azure RTOS NetX Duo は、厳密な IPv6 対応のロゴ認定を達成する唯一の埋め込み型 TCP/IP スタックです。このロゴは、準拠と相互運用性のテストに合格し、IPv6 フォーラムによって管理および検証されていることを証明します。 NetX Duo では、NetX Duo コア TCP/IP プロトコルの実装に対して業界標準の IxANVL (自動ネットワーク検証ライブラリ) も利用されています。

## <a name="comprehensive-iot-solution"></a>包括的な IoT ソリューション

NetX Duo では、深い埋め込み型 IoT アプリケーション向けの最も包括的な TCP/IP ネットワークの 1 つが提供されます。 このサポートには、次のアドオン プロトコル製品が含まれています。

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

## <a name="related-services"></a>関連サービス

### <a name="azure-iot"></a>Azure IoT

NetX Duo には [Azure RTOS 用の Azure IoT ミドルウェア](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md)が含まれています。これは、Azure RTOS と Azure SDK for Embedded C の間のバインド層として機能し、Azure IoT サービスへの接続を容易にするプラットフォーム固有のライブラリです。 Azure IoT ミドルウェアの目的は次のとおりです。
* 開発者がアプリケーションに必要とするスマートなクライアント インターフェイス (IoTHub_Client、DeviceProvisioning_Client) を提供する。
* Embedded C SDK とプラットフォーム間の対話を調整する。
* Azure RTOS プラットフォームの初期化を提供する。
* IoT Plug and Play のサポート。
* セキュリティ機能。
* リソース制限への対応。
* プロトコルのサポート。

![Azure RTOS NetX Duo 関連のサービス](./media/overview-netx-duo/related-services.png)

### <a name="azure-defender"></a>Azure Defender

Azure Defender for IoT セキュリティ モジュールでは、Azure RTOS デバイス向けの包括的なセキュリティ ソリューションが提供されます。 Azure RTOS のセキュリティ モジュールは、悪意のあるネットワーク アクティビティの検出、カスタム アラート ベースのデバイス動作での基準設定、およびデバイス セキュリティ検疫の強化に役立ちます。 [Azure RTOS のセキュリティ モジュール](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos)の詳細を確認するか、[Azure RTOS 用セキュリティ モジュールの構成](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module)に関するクイックスタートを開始してください。

### <a name="device-update-for-iot-hub"></a>Device Update for IoT Hub

[Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) は、IoT デバイスの Over-the-Air (OTA) 更新をデプロイできるようにするサービスです。 Device Update for IoT Hub モジュールは、Azure RTOS NetX Duo での Device Update for IoT Hub エージェントの実装です。 これは、デバイス開発者がアプリケーションにデバイス更新機能を統合するための簡単な API を提供します。

主要な半導体評価ボードのサンプルをご覧ください。デバイスへの無線 (OTA) での更新を構成、構築、デプロイする方法が学べるファースト ステップ ガイドが含まれています。

さらに、[Azure RTOS を使用した Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system) に関する記事で詳細を確認できます。

## <a name="next-steps"></a>次のステップ

NetX Duo の詳細については、最初に、[Azure RTOS NetX Duo のユーザー ガイド](about-this-guide.md)を参照してください。
