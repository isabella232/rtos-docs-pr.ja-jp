---
title: Microsoft Azure RTOS とは
description: Azure RTOS は、マイクロコントローラー ユニット (MCU) を搭載した IoT デバイスとエッジ デバイスのためのリアル タイム オペレーティング システム (RTOS) です。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 3b1c63135f6069652d7f66fc976b9d770a4dfeb2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811414"
---
# <a name="what-is-microsoft-azure-rtos"></a>Microsoft Azure RTOS とは

Azure RTOS は、マイクロコントローラー ユニット (MCU) を搭載した IoT デバイスとエッジ デバイスのためのリアル タイム オペレーティング システム (RTOS) です。 Azure RTOS は、非常に制約の厳しいデバイス (バッテリ駆動で、フラッシュ メモリが 64 KB 未満) をサポートするように設計されています。
 
Azure RTOS は、さまざまな安全性標準に対する認定をあらかじめ受けています。 これには、IEC 61508 SIL 4、IEC 62304 Class C、ISO 26262 ASIL D の各認定が含まれます。 Azure RTOS ThreadX は、DO-178 の認定も受けています。

Azure RTOS により、IPsec による完全な IP 層セキュリティおよび TLS と DTLS によるソケット層セキュリティを含む、EAL4+ の情報セキュリティ国際評価基準認定環境が提供されます。 Microsoft のソフトウェア暗号化ライブラリは、FIPS 140-2 の認定を受けています。 また、ハードウェア暗号化機能、ThreadX MODULES によるメモリ保護、ARM の TrustZone ARMv8-M セキュリティ機能のサポートも利用しています。

## <a name="components-of-azure-rtos"></a>Azure RTOS のコンポーネント

Azure RTOS プラットフォームは、Azure RTOS ThreadX、Azure RTOS FileX、Azure RTOS GUIX、Azure RTOS NetX、Azure RTOS NetX Duo、Azure RTOS USBX などの実行時ソリューションのコレクションです。

### <a name="azure-rtos-threadx"></a>Azure RTOS ThreadX

Azure RTOS ThreadX は、特に深く組み込まれたアプリケーション向けに設計された高度なリアルタイム オペレーティング システム (RTOS) です。 Azure RTOS ThreadX によって提供されるさまざまな利点としては、高度なスケジュール機能、メッセージ パッシング、割り込み管理、メッセージング サービスなどがあります。 Azure RTOS ThreadX には、ピコカーネル アーキテクチャ、優先しきい値のスケジュール設定、イベント チェーン、豊富なシステム サービスのセットなど、高度な機能が多数用意されています。

### <a name="azure-rtos-filex"></a>Azure RTOS FileX

Azure RTOS FileX は、高パフォーマンスの FAT 互換ファイル システムです。 Azure RTOS ThreadX と完全に統合されており、サポートされているすべてのプロセッサで利用できます。 Azure RTOS ThreadX と同様に、Azure RTOS FileX は、小さい専有領域でハイ パフォーマンスを実現するように設計されているため、ファイル操作を必要とする昨今の深い埋め込み型のアプリケーションに最適です。 Azure RTOS FileX により、RAM ディスク、USBX、SD カード、および Azure RTOS LevelX 経由の NAND と NOR フラッシュ メモリなど、ほとんどの物理メディアがサポートされています。

### <a name="azure-rtos-guix"></a>Azure RTOS GUIX

Azure RTOS GUIX は、埋め込みシステム開発者のニーズに対応するために作成された、プロフェッショナル品質のグラフィカル ユーザー インターフェイス パッケージです。 代替製品とは異なり、Azure RTOS GUIX は小さく高速で、グラフィカル出力をサポートできる事実上すべてのハードウェア構成に簡単に移植できます。 また、Azure RTOS GUIX には、魅力的な外観と、アプリケーション レベルのユーザー インターフェイス開発用の直感的で強力な API も用意されています。

### <a name="azure-rtos-netx"></a>Azure RTOS NetX

Azure RTOS NetX は、TCP/IP プロトコル標準の高パフォーマンスの実装です。 Azure RTOS ThreadX と完全に統合されており、サポートされているすべてのプロセッサで利用できます。 Azure RTOS NetX は、独自の Piconet アーキテクチャを備えています。 ゼロコピー API と組み合わせることで、ネットワーク接続を必要とする今日の深く組み込まれたアプリケーションに最適なものになります。

### <a name="azure-rtos-netx-duo"></a>Azure RTOS NetX Duo

Azure RTOS NetX Duo は、特に深く組み込まれたリアルタイムの IoT アプリケーション用に設計された、高度な商用 TCP/IP ネットワーク スタックです。 Azure RTOS NetX Duo が IPv4 と IPv6 のデュアル ネットワーク スタックであるのに対し、NetX は元の IPv4 ネットワーク スタックで、実質的には Azure RTOS NetX Duo のサブセットです。

### <a name="azure-rtos-usbx"></a>Azure RTOS USBX

Azure RTOS USBXは、ハイ パフォーマンスの USB ホスト、デバイス、On-The-Go (OTG) の埋め込みスタックです。 ThreadX と完全に統合されており、Azure RTOS ThreadX でサポートされているすべてのプロセッサで利用できます。 Azure RTOS ThreadX と同様に、Azure RTOS USBX は、小さいフットプリントでハイパフォーマンスを実現するように設計されているため、USB デバイスとのインターフェイスを必要とする深く組み込まれたアプリケーションに最適です。

### <a name="windows-tools"></a>Windows ツール

Azure RTOS GUIX には完全な GUI アプリケーション デザイン環境が用意されており、アプリケーションの GUI のすべてのグラフィカル要素を容易に作成および保守できます。 Azure RTOS GUIX Studio によって、Azure RTOS GUIX ライブラリと互換性がある C コードが自動的に生成されます。これはターゲット上でコンパイルおよび実行できます。

Azure RTOS TraceX は、開発者がリアルタイム システムのイベントをグラフィカルに表示し、リアルタイム システムの動作への理解を深めることができる、ホストベースの分析ツールです。

## <a name="in-the-context-of-azure-iot"></a>Azure IoT のコンテキストで

Azure IoT に直接接続したり、Azure IoT Edge 経由で間接的に接続したりするだけでなく、Azure Sphere デバイスでも Azure RTOS を利用できます。 Azure RTOS と Azure Sphere を組み合わせることにより、クラス最高のリアルタイム処理とセキュリティを 1 つのデバイスでまとめて実現できます。
