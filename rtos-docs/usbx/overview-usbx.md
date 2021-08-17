---
title: Azure RTOS USBX を理解する
description: Azure RTOS USBX は、ハイパフォーマンスの USB ホスト、デバイス、On-The-Go (OTG) の埋め込みスタックです。Azure RTOS USBX は Azure RTOS ThreadX と完全に統合されており、すべての Azure RTOS ThreadX でサポートされているプロセッサで利用できます。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 8950e7573bf705feb16de6ac1adb5f55559ea4b04b453944c5a24baddc6ae7b9
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791450"
---
# <a name="overview-of-azure-rtos-usbx"></a>Azure RTOS USBX の概要

Azure RTOS USBXは、ハイ パフォーマンスの USB ホスト、デバイス、On-The-Go (OTG) の埋め込みスタックです。 Azure RTOS USBX は Azure RTOS ThreadX と完全に統合されており、ThreadX でサポートされているすべてのプロセッサで利用できます。 ThreadX と同様に、Azure RTOS USBX は、小さいフットプリントでハイパフォーマンスを実現するように設計されているため、USB デバイスとのインターフェイスを必要とする深い埋め込み型のアプリケーションに最適です。

## <a name="host-device-otg--extensive-class-support"></a>ホスト、デバイス、OTG、および広範なクラスのサポート

Azure RTOS USBX ホストまたはデバイス埋め込み USB プロトコル スタックは、リアルタイムの深い埋め込み型 IoT アプリケーション用に設計された産業用埋め込み USB ソリューションです。 Azure RTOS USBX は、ホスト、デバイス、および OTG のサポートに加えて、広範なクラスのサポートを提供しています。 Azure RTOS USBX は、ThreadX Real-Time オペレーティング システム、Azure RTOS FileX 埋め込み FAT 互換ファイル システム、Azure RTOS NetX、および Azure RTOS NetX Duo 埋め込み TCP/IP スタックと完全に統合されています。 これらすべてを非常に小さなフットプリント、高速な処理、優れた使いやすさと組み合わせることで、Azure RTOS USBX は、USB 接続を必要とする最も要求の厳しい埋め込み型 IoT アプリケーションに最適な選択肢となります。

### <a name="usbx-memory-footprint"></a>USBX のメモリ占有領域

Azure RTOS USBX では、Azure RTOS USBX デバイスの CDC/ACM サポートのために、10.5 KB のフラッシュと 5.1 KB の RAM という非常に小さなフットプリントを実現しています。 Azure RTOS USBX ホストには、CDC/ACM のサポートのために最低 18 KB のフラッシュと 25 KB の RAM が必要です。

TCP 機能を使用するには、追加で 10 KB から 13 KB の命令領域メモリが必要です。 Azure RTOS USBX の RAM の使用率は、通常、2.6 KB から 3.6 KB に、アプリケーションによって定義されるパケット プール メモリを加えた分になります。

ThreadX と同様に、Azure RTOS USBX のサイズは、アプリケーションで実際に使用されるサービスに基づいて自動的にスケーリングされます。 これにより、複雑な構成やビルド パラメーターが実質的に不要になるため、開発者の作業がより簡単になります。

### <a name="usb-interoperability-verification"></a>USB 相互運用性の検証

Azure RTOS USBX デバイス スタックは、USB IF 標準テスト ツール USBCV で厳格にテストされ、USB 仕様に完全に準拠し、さまざまなホスト システムと相互運用性があることが確認されています。
さらに、Azure RTOS USBX OTG スタックは、台湾の独立テスト ラボ Allion によって検証および認定されています。

### <a name="usb-host-controller-support"></a>USB ホスト コントローラーのサポート

Azure RTOS USBX は、OHCI や EHCI などの主要な USB 標準をサポートしています。 さらに、Azure RTOS USBX は、Atmel、Microchip、Philips、Renesas、ST、TI、およびその他のベンダーの独自の USB ホスト コントローラーをサポートしています。 Azure RTOS USBX は、同じアプリケーション内の複数のホスト コントローラーもサポートしています。
USB デバイス コントローラーのサポート。Azure RTOS USBX は、Analog Devices、Atmel、Microchip、NXP、Philips、Renesas、ST、TI、およびその他のベンダーの人気のある USB デバイス コントローラーをサポートしています。

### <a name="extensive-host-class-support"></a>広範なホスト クラスのサポート

Azure RTOS USBX ホストは、ASIX、AUDIO、CDC/ACM、CDC/ECM、GSER、HID (キーボード、マウス、およびリモート コントロール)、HUB、PIMA (PTP/MTP)、PRINTER、PROLIFIC、STORAGE などの、最も一般的なクラスをサポートしています。

### <a name="extensive-usb-device-class-support"></a>広範な USB デバイス クラスのサポート

Azure RTOS USBX デバイスは、CDC/ACM、CDC/ECM、DFU、HID、PIMA (PTP/MTP) (w/MTP)、RNDIS、STORAGE などの最も一般的なクラスをサポートしています。 カスタム クラスのサポートも利用できます。

### <a name="pictbridge-support"></a>Pictbridge のサポート

Azure RTOS USBX では、ホストとデバイスの両方で完全な Pictbridge 実装がサポートされています。 Pictbridge は、両方の側の Azure RTOS USBX PIMA (PTP/MTP) クラスの上に配置されます。 PictBridge 標準では、PC を使用せずに、デジタル スチル カメラまたはスマートフォンを直接プリンターに接続できるので、特定の Pictbridge 対応プリンターに直接印刷できます。 カメラまたはスマートフォンがプリンターに接続されている場合、プリンターは USB ホストであり、カメラは USB デバイスです。 ただし、Pictbridge では、カメラはホストとして表示され、コマンドはカメラから実行されます。 カメラはストレージ サーバーであり、プリンターはストレージ クライアントです。 カメラはプリント クライアントであり、プリンターはもちろんプリント サーバーです。 Pictbridge は、トランスポート層として USB を使用しますが、通信プロトコルとしては PTP (Picture Transfer Protocol) に依存します。

### <a name="custom-class-support"></a>カスタム クラスのサポート

Azure RTOS USBX ホストとデバイスはカスタム クラスをサポートします。 カスタム クラスの例は、Azure RTOS USBX ディストリビューションに用意されています。 この単純なデータ ポンプ クラスは DPUMP と呼ばれ、カスタム アプリケーション クラスのモデルとして使用できます。
高度なテクノロジである Azure RTOS USBX ホストとデバイスはカスタム クラスをサポートします。 カスタム クラスの例は、Azure RTOS USBX ディストリビューションに用意されています。 Azure RTOS USBX は、次の機能を備えた高度なテクノロジです。

* ホスト、デバイス、および OTG のサポート
* USB の低速、フルスピード、および高速のサポート
* 自動スケーリング
* ThreadX、Azure RTOS FileX、Azure RTOS NetX との完全な統合
* オプションのパフォーマンス メトリック
* Azure RTOS TraceX システム分析のサポート

## <a name="azure-rtos-usbx-apis"></a>Azure RTOS USBX API

### <a name="azure-rtos-usbx-host-api"></a>Azure RTOS USBX Host API

Azure RTOS USBX Host API は、名詞 - 動詞の名前付け規則に従った直感的で一貫性のある API です。 すべての API の先頭を ux_host_* にして USBX として簡単に識別できるようにしています。 ブロック API には、オプションのスレッド タイムアウトがあります。

* ASIX
    - 最小 0.3 KB のフラッシュ、4 KB の RAM
    - 自動スケーリング、Azure RTOS TraceX によるシステム レベルのトレース
    - 直観的な Azure RTOS USBX Host API の形式: *ux_host_class_asix_* *
* AUDIO
    - 最小 1.2 KB のフラッシュ、4 KB の RAM
    - 自動スケーリング
    - 直観的な Azure RTOS USBX Host API の形式: *ux_host_class_audio_* *
* CDC/ACM
    - 最小 1.4 KB のフラッシュ、4 KB の RAM
    - 自動スケーリング
    - Azure RTOS TraceX によるシステムレベルのトレース
    - 直観的な Azure RTOS USBX Host API の形式: *ux_host_class_cdc_acm_* *
* HID
    - 最小 0.3 KB のフラッシュ、4 KB の RAM
    - キーボード、マウス、およびリモート サポート
    - 自動スケーリング
    - Azure RTOS TraceX によるシステムレベルのトレース
    - 直観的な Azure RTOS USBX Host API の形式: *ux_host_class_hid_* * 
* ハブ
    - 最小 1.7 KB のフラッシュ、2 KB の RAM
    - 自動スケーリング
    - Azure RTOS TraceX によるシステムレベルのトレース
    - 直観的な Azure RTOS USBX Host API の形式: *ux_host_class_hub_* *
* PIMA (PTP/MTP)
    - 最小 0.9 KB のフラッシュ、8 KB の RAM
    - 自動スケーリング
    - Azure RTOS TraceX によるシステムレベルのトレース
    - 直観的な Azure RTOS USBX Host API の形式: *ux_host_class_pima_* *
* PRINTER
    - 最小 0.8 KB のフラッシュ、8 KB の RAM
    - 自動スケーリング
    -  Azure RTOS TraceX によるシステムレベルのトレース
    -  直観的な Azure RTOS USBX Host API の形式: *ux_host_class_printer_* *
* PROLIFIC
    - 最小 1.5 KB のフラッシュ、4 KB の RAM
    - 自動スケーリング
    - Azure RTOS TraceX によるシステムレベルのトレース
    - 直観的な Azure RTOS USBX Host API の形式: *ux_host_class_prolific_* *
* STORAG
    - 最小 5.6 KB のフラッシュ、4 KB の RAM
    - 自動スケーリング<br> Azure RTOS FileX との統合
    - Azure RTOS TraceX によるシステムレベルのトレース
    - 直観的な Azure RTOS USBX Host API の形式: *ux_host_class_storage_* *
* USB ホスト スタック
    - 多くのホスト コントローラーのサポート
    - 最小 18 KB のフラッシュ、25 KB の RAM
    - 自動スケーリング
    - 同じプラットフォーム上の複数のホスト コントローラーのサポート
    -  USB の低速、フルスピード、および高速のサポート
    -  Azure RTOS TraceX によるシステムレベルのトレース
    -  直観的な Azure RTOS USBX Host API の形式: *ux_host_stack_*  * 
* OHCI、EHCI、専用のホスト コントローラー 

### <a name="azure-rtos-usbx-device-api"></a>Azure RTOS USBX Device API

Azure RTOS USBX Device API は、名詞 - 動詞の名前付け規則に従った直感的で一貫性のある API です。 すべての API の先頭を ux_device_* にして USBX として簡単に識別できるようにしています。 ブロック API にオプションのスレッド タイムアウトがあります。 詳細については、[Azure RTOS USBX ホスト ユーザー ガイド](usbx-host-stack-about.md)に関する記事を参照してください。

* CDC/ACM
    - 最小 0.8 KB のフラッシュ、2 KB の RAM
    - 自動スケーリング
    - Azure RTOS TraceX によるシステムレベルのトレース
    - 直観的な Azure RTOS USBX Device API の形式: *ux_device_class_cdc_acm_**.
* CDC/ECM
    - 最小 1.5 KB のフラッシュ、4 KB から 8 KB の RAM
    - 自動スケーリング
    - Azure RTOS TraceX によるシステムレベルのトレース<br> 直観的な Azure RTOS USBX Device API の形式: *ux_device_class_cdc_ecm_**.
* DFU
    - 最小 1.1 KB のフラッシュ、2 KB の RAM
    -  自動スケーリング
    -  Azure RTOS TraceX によるシステムレベルのトレース
    - 直観的な Azure RTOS USBX Device API の形式: *ux_device_class_dfu_* * 
* GSER
    - 最小 0.6 KB のフラッシュ、4 KB の RAM
    - 自動スケーリング
    - Azure RTOS TraceX によるシステムレベルのトレース
    - 直観的な Azure RTOS USBX Device API の形式: *ux_device_class_gser_* *
* HID
    - 最小 0.9 KB のフラッシュ、2 KB の RAM
    - 自動スケーリング
    - Azure RTOS TraceX によるシステムレベルのトレース
    - 直観的な Azure RTOS USBX Device API の形式: *ux_device_class_hid_* * PIMA (PTP/MTP)
    - 最小 5.2 KB のフラッシュ、8 KB の RAM
    - 自動スケーリング
    - Azure RTOS TraceX によるシステムレベルのトレース
    - 直観的な Azure RTOS USBX Device API の形式: *ux_device_class_pima_* * 
* 記憶域
    - 最小 2.3 KB のフラッシュ、4 KB の RAM
    - 自動スケーリング
    - Azure RTOS TraceX によるシステムレベルのトレース
    - 直観的な Azure RTOS USBX Device API の形式: *ux_device_class_storage_* *
* RNDIS
    - 最小 2.3 KB のフラッシュ、4 KB から 8 KB の RAM
    - 自動スケーリング
    - Azure RTOS NetX と Azure RTOS NetX DUO との統合
    - Azure RTOS TraceX によるシステムレベルのトレース
    - 直観的な Azure RTOS USBX Device API の形式: *ux_device_class_rndls_* *
* Azure RTOS USBX デバイス スタック
    - 最小 2.3 KB のフラッシュ、4 KB の RAM
    - 自動スケーリング
    - Azure RTOS TraceX によるシステムレベルのトレース
    - 直観的な Azure RTOS USBX Device API の形式: *ux_device_class_storage_* *
* 専用のホスト コントローラー

## <a name="next-steps"></a>次のステップ

[ホスト スタック ユーザー ガイド](usbx-host-stack-about.md)または[デバイス スタック ユーザー ガイド](usbx-device-stack-about.md)に関する記事に従って、Azure RTOS USBX ホストおよびデバイス スタックの使用を開始します。