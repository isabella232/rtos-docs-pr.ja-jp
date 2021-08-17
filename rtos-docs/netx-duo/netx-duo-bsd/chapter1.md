---
title: 第 1 章 - Azure RTOS NetX Duo BSD の概要
description: BSD Socket API の Compliancy Wrapper では、基本的な BSD Socket API 呼び出しの一部を一定の制限付きでサポートしており、その基盤では Azure RTOS NetX Duo のプリミティブが利用されています。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: caf8d5374204bc553ac903f4720d3db402d9a10da5c26caa0fa67c4b5d340049
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790498"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-bsd"></a>第 1 章 - Azure RTOS NetX Duo BSD の概要

BSD Socket API の Compliancy Wrapper では、基本的な BSD Socket API 呼び出しの一部を一定の制限付きでサポートしており、その基盤では Azure RTOS NetX Duo のプリミティブが利用されています。

## <a name="bsd-socket-api-compliancy-wrapper-source"></a>BSD Socket API の Compliancy Wrapper のソース

このラッパーのソース コードは単純さのために設計されており、2 つのファイルで構成されています。つまり、*nxd_bsd.h* と *nxd_bsd.c* です。 *nxd_bsd.h* ファイルでは、BSD Socket API Wrapper の必要な定数とサブルーチン プロトタイプがすべて定義されています。一方 *nxd_bsd.c* には、BSD Socket API と互換性がある実際のソース コードが含まれています。 ラッパーのこれらのソース ファイルは、すべての NetX Duo サポート パッケージに共通です。

パッケージは次のもので構成されます。

- **nxd_bsd.c**: ラッパーのソース コード
- **nxd_bsd.h**: メインのヘッダー ファイル

サンプル デモ プログラム:

- **bsd_demo_udp.c**: *2 つの UDP ピアを使用したデモ (IPv4 のみ)*
- **bsd_demo_tcp.c**: *1 つの TCP サーバーとクライアントを使用したデモ*
- **bsd_demo_raw.c**: *2 つの RAW ピアを使用したデモ*