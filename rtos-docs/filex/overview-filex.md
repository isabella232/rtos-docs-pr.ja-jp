---
title: Azure RTOS FileX を理解する
description: Azure RTO FileX は、ファイル アロケーション テーブル (FAT) 互換のハイ パフォーマンスのファイル システムであり、Azure RTOS ThreadX と完全に統合されており、サポートされるすべてのプロセッサで利用できます。 Azure RTOS ThreadX と同様に、Azure RTOS FileX は、小さい専有領域でハイ パフォーマンスを実現するように設計されているため、ファイル管理操作を必要とする昨今の深い埋め込み型のアプリケーションに最適です。 FileX は、RAM、Azure RTOS USBX、SD カード、および Azure RTOS LevelX 経由の NAND と NOR フラッシュ メモリなど、ほとんどの物理メディアをサポートしています。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 399586eca18ef9345b94cc577bdacbf3c3a591bcd22b474b4e3d4ca4eefb4432
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782850"
---
# <a name="overview-of-azure-rtos-filex"></a>Azure RTOS FileX の概要

Azure RTOS FileX の埋め込みファイル システムは、Microsoft FAT ファイル形式の高度な商用ソリューションであり、深く埋め込まれたリアルタイムの IoT アプリケーション向けに特別に設計されました。 Azure RTOS FileX では、Microsoft のすべてのファイル形式 (FAT12、FAT16、FAT32、exFAT など) がサポートされています。 FileX では、[Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/) と呼ばれるアドオン製品を使用した省略可能なフォールト トレランスや FLASH 消耗平準化も提供されます。 これらすべてを小さな占有領域、高速な処理、優れた使いやすさと組み合わせることで、Azure RTOS FileX は、最も要求の厳しい埋め込み型 IoT アプリケーションに最適な選択肢となります。

## <a name="api-protocols"></a>API プロトコル

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
