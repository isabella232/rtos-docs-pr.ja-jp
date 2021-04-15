---
title: 第 2 章 - Azure RTOS LevelX のインストールと使用
description: LevelX のインストールと使用は簡単で、この章の次のセクションで説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 575776875452cfc718401556a6440d787cb18893
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811882"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a>第 2 章 - Azure RTOS LevelX のインストールと使用

Azure RTOS LevelX のインストールと使用は簡単で、この章の次のセクションで説明します。

## <a name="distribution"></a>Distribution

LevelX は ANSI C で配布されます。各関数は、それぞれ個別の C ファイルに含まれています。 LevelX の配布に含まれるファイルは次のとおりです。
- lx_api.h
- lx_nand_flash_256byte_ecc_check.c
- lx_nand_flash_256byte_ecc_compute.c
- lx_nand_flash_block_full_update.c
- lx_nand_flash_block_reclaim.c
- lx_nand_flash_close.c
- lx_nand_flash_defragment.c  
- lx_nand_flash_extended_cache_enable.c
- lx_nand_flash_initialize.c
- lx_nand_flash_logical_sector_find.c
- lx_nand_flash_next_block_to_erase_find.c
- lx_nand_flash_open.c
- lx_nand_flash_page_ecc_check.c
- lx_nand_flash_page_ecc_compute.c  
- lx_nand_flash_partial_defragment.c
- lx_nand_flash_physical_page_allocate.c
- lx_nand_flash_sector_mapping_cache_invalidate.c
- lx_nand_flash_sector_read.c
- lx_nand_flash_sector_release.c
- lx_nand_flash_sector_write.c
- lx_nand_flash_system_error.c
- lx_nor_flash_block_reclaim.c
- lx_nor_flash_close.c
- lx_nor_flash_defragment.c  
- lx_nor_flash_extended_cache_enable.c
- lx_nor_flash_initialize.c
- lx_nor_flash_logical_sector_find.c
- lx_nor_flash_next_block_to_erase_find.c
- lx_nor_flash_open.c
- lx_nor_flash_partial_defragment.c
- lx_nor_flash_physical_sector_allocate.c
- lx_nor_flash_sector_mapping_cache_invalidate.c
- lx_nor_flash_sector_read.c
- lx_nor_flash_sector_release.c
- lx_nor_flash_sector_write.c
- lx_nor_flash_system_error.c

次に示すように、LevelX の NAND と NOR インスタンスの両方に対してシミュレーターと FileX ドライバーのサンプルもあります。

- demo_filex_nand_flash.c  
- fx_nand_flash_simulated_driver.c
- lx_nand_flash_simulator.c
- demo_filex_nor_flash.c  
- fx_nor_flash_simulated_driver.c
- lx_nor_flash_simulator.c

NAND フラッシュのみが必要な場合は、LevelX NAND フラッシュ ファイル (***lx_nand_\*.c***) のみが必要です。 同様に、NOR フラッシュのみが必要な場合は、NOR フラッシュ ファイル (**_lx_nor_\_.c***) のみが必要です。

## <a name="configuration-options"></a>構成オプション

次に説明する条件定義を使用して、コンパイル時に LevelX を構成できます。 オプションを使用するには、必要な定義を各 LevelX ソースのコンパイルに追加するだけです。

- **LX_DIRECT_READ**: このオプションを定義すると、NOR メモリの直接読み取りが優先されて、NOR フラッシュ ドライバーの読み取りルーチンがバイパスされるため、パフォーマンスが大幅に向上します。
- **LX_FREE_SECTOR_DATA_VERIFY**: これが定義されると、LevelX NOR インスタンスのオープン ロジックによって、空き NOR セクターがすべて 1 かどうかが検証されます。
- **LX_NAND_SECTOR_MAPPING_CACHE_SIZE**: 既定では、この値は 16 で、論理セクター マッピングのキャッシュ サイズが定義されます。 大きい値を指定すると、パフォーマンスは向上しますが、メモリが必要になります。 最小サイズは 8 で、すべての値は 2 の累乗でなければなりません。
- **LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: これが定義されていると、キャッシュ ミスがないように直接マッピング キャッシュが作成されます。 また、LX_NAND_SECTOR_MAPPING_CACHE_SIZE でフラッシュ デバイス内の合計ページ数を正確に表す必要があります。
- **LX_NOR_DISABLE_EXTENDED_CACHE**: これが定義されていると、拡張された NOR キャッシュが無効になります。
- **LX_NOR_EXTENDED_CACHE_SIZE**: この値の既定値は 8 です。これは、NOR インスタンスにキャッシュできる最大セクター数が 8 であることを表します。
- **LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: 既定では、この値は 16 で、論理セクター マッピングのキャッシュ サイズを定義します。 大きい値を指定すると、パフォーマンスは向上しますが、メモリが必要になります。 最小サイズは 8 で、すべての値は 2 の累乗でなければなりません。
- **LX_THREAD_SAFE_ENABLE**: これが定義されていると、API 全体で ThreadX ミューテックス オブジェクトを使用して LevelX がスレッドセーフになります。

## <a name="using-levelx"></a>LevelX の使用

LevelX を単独で、または FileX と共に使用するには、LevelX API を参照するコードにファイル ***lx_api.h** _ を含めます。 また、LevelX オブジェクト コードがリンク時に使用可能であることを確認します。 LevelX を使用する方法の例については、ファイル _*_demo_filex_nand_flash.c_*_ と _ *_demo_filex_nor_flash_** を確認してください。
