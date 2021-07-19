---
title: Azure RTOS NetX を理解する
description: Azure RTOS NetX は、TCP/IP プロトコル標準のハイパフォーマンス実装です。Azure RTOS ThreadX と完全に統合されており、サポートされるすべてのプロセッサで利用できます。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 63fd212249da6154926684f9bc844d2c2a78e84e
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754847"
---
# <a name="overview-of-azure-rtos-netx"></a>Azure RTOS NetX の概要

Azure RTOS NetX は、深く組み込まれたリアルタイム IoT アプリケーション専用に設計された、産業用 TCP/IP IPv4 組み込みネットワーク スタックです。 Azure RTOS NetX は、Microsoft 独自の IPv4 ネットワーク スタックであり、本質的に Azure RTOS のサブセットです。 NetX は、IPv4、TCP、UDP などのコア ネットワーク プロトコルと、その他の高度なアドオン プロトコルの完全なスイートを組み込みアプリケーションに提供します。 小さなフットプリント、高速実行、優れた操作性により、Azure RTOS NetX は、最も要求の厳しい組み込み IoT アプリケーションに最適な選択肢となっています。

## <a name="api-protocols"></a>API のプロトコル
Azure RTOS NetX では、次の機能がサポートされています。

### <a name="telnet"></a>Telnet

* 最小 0.5 KB と 0.3 KB の RAM フットプリント。
* クライアントとサーバーのサポート。

### <a name="auto-ip"></a>Auto IP

* IPv4 アドレス自動割り当て。
* 最小 1.2 KB、300 バイトの RAM。

### <a name="http---hypertext-transfer-protocolhttp"></a>HTTP - ハイパーテキスト転送プロトコル (HTTP)

* 最小 2.8 KB から 4.8 KB のフラッシュ、0.4 KB から 1.0 KB の RAM フットプリント。
* クライアントとサーバーのサポート。

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a>SMTP - 簡易メール転送プロトコル (SMTP)

* 最小 4.1 KB と 0.6 KB の RAM フットプリント
* クライアントのサポート

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a>DHCP - 動的ホスト構成プロトコル (DHCP)

* 最小 3.6 KB から 4.6 KB のフラッシュ、2.7 KB の RAM フットプリント
* クライアントとサーバーのサポート
* IPv4 のサポート

### <a name="p0p3---post-office-protocol-version-3-pop3"></a>P0P3 - Post Office Protocol Version 3 (POP3)

* 最小 8.1 KB と 1.4 KB の RAM フットプリント
* クライアントのサポート

### <a name="snmp---simple-network-management-protocol-snmp"></a>SNMP - 簡易ネットワーク管理プロトコル (SNMP)

* 最小 10.9 KB と 2.6 KB の RAM フットプリント
* VI、V2、V3 のエージェントのサポート

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a>FTP、TFTP - ファイル転送プロトコル (FTP)、簡易ファイル転送プロトコル (TFTP)

* FTP - 最小 1.8 KB から 7.2 KB のフラッシュ、0.6 KB から 2.1 KB の RAM フットプリント
* TFTP - 最小 1.7 KB から 2.4 KB のフラッシュ、0.3 KB から 1.8 KB の RAM フットプリント
* クライアントとサーバーのサポート

### <a name="ppp---polnt-to-point-protocol-ppp"></a>PPP - Point-to-Point プロトコル (PPP)

* 最小 7.1 KB と 3.8 KB の RAM フットプリント
* 信頼性と確実性。

### <a name="sntp---simple-network-time-protocol-sntp"></a>SNTP - Simple Network Time Protocol (SNTP)

* 最小 4 KB および 0.5 KB の RAM
* クライアントのサポート

### <a name="azure-rtos-netx-api"></a>Azure RTOS NetX API

* 高速のゼロコピー API 実装
* レガシ ソケット コードを移植するためのオプションの BSD レイヤー

### <a name="igmp---internet-group-management-protocol-igmp"></a>IGMP - インターネット グループ管理プロトコル (IGMP)

* 最小 2.5 KB のフラッシュ
* IPv4 マルチキャスト グループのサポート
* IXIA IxANVL 検証済み
* オプションの IGMP 統計情報
* Azure RTOS TraceX によるシステムレベルのトレース

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

### <a name="icmp---internet-control-message-protocol-icmp"></a>ICMP - インターネット制御メッセージ プロトコル (ICMP)

* 最小 2.5 KB のフラッシュ
* IPv4 のサポート
* IXIA IxANVL 検証済み
* ping 要求と ping 応答
* ping 要求時のオプションのスレッド中断
* すべての中断時のオプションのタイムアウト
* オプションの ICMP 統計情報
* Azure RTOS TraceX によるシステムレベルのトレース

### <a name="ipv4---internet-protocol-ip"></a>IPv4 - インターネット プロトコル (IP)

* 最小 3.5 KB から 8.5 KB のフラッシュ、2 KB から 3 KB の RAM フットプリント。
* Piconet™ アーキテクチャ。
* 高速な、ワイヤスピードに近いパフォーマンス。
* 複数インターフェイスのサポート。
* マルチホームのサポート。
* 静的ルーティングのサポート。
* IP の断片化と再構築のサポート。
* IPv4 のサポート。
* IXIA IxANVL 検証済み。
* フェーズ II 対応ロゴ認定。
* オプションの IP 統計情報。
* 明確に定義された直感的な物理層ドライバー インターフェイス。
* Azure RTOS TraceX によるシステムレベルのトレース。

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a>ARP/RARP - アドレス解決プロトコル (ARP)、逆アドレス解決プロトコル (RARP)

* 最小 1.7 KB のフラッシュ、RAM サイズ。
* 32 ビット IPv4 と 48 ビット MAC アドレスの動的な解決。
* IXIA IxANVL 検証済み。
* 柔軟なユーザー定義の ARP キャッシュ。
* Gratuitous ARP のサポート。
* アプリケーションによって決定されるオプションの ARP/RARP 統計情報。
* Azure RTOS TraceX によるシステムレベルのトレース。

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a>イーサネット、WiFi、Bluetooth LE、15.4 など

## <a name="interoperability-verification"></a>相互運用性の検証

Azure RTOS NetX は RFC 標準に準拠しており、ほとんどのベンダーのデバイスとの完全な相互運用性を提供します。 Azure RTOS NetX では、Azure RTOS NetX コア TCP/IP プロトコル実装に業界標準の IxANVL (自動ネットワーク検証ライブラリ) も利用しています。

## <a name="advanced-technology"></a>高度なテクノロジ

Azure RTOS NetX は、次の機能を備えた高度なテクノロジです。
* Piconet™ アーキテクチャ。
* 自動スケーリング。
* UDP Fast-Path Technology™。
* 柔軟なパケット管理。
* ゼロコピー API と実装。
* マルチホームのサポート。
* すべての中断時のオプションのタイムアウト。
* 静的ルーティングのサポート。
* Azure RTOS TraceX システム分析のサポート。
