---
title: チャプター 1 - Azure RTOS NetX BSD の概要
description: Azure RTOS NetX BSD Sockets API Compliancy Wrapper では、基本的な BSD Sockets API の一部を制限付きでサポートしています。その処理には NetX の基本操作を使用しています。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b58283a38a25ffdd438d7853999f3b6e390f280a947aa45101d8df86447bf3dd
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796721"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-bsd"></a>チャプター 1 - Azure RTOS NetX BSD の概要

NetX BSD Sockets API Compliancy Wrapper では、基本的な BSD Sockets API の一部を制限付きでサポートしています。その処理には NetX の基本操作を使用しています。 この BSD Sockets API 互換レイヤーでは NetX の基本操作を利用し、NetX の基本的なエラー チェックを無視するため、このラッパーは通常の BSD 実装と同等か、それよりも少し高速です。

## <a name="bsd-sockets-api-compliancy-wrapper-source"></a>BSD Sockets API Compliancy Wrapper のソース

この BSD ラッパーのソース コードはシンプルさを重視しており、2 つのファイル *nx_bsd.h* と *nx_bsd.c* のみで構成されます。 *nx_bsd.h* ファイルでは、BSD Sockets API Wrapper の必要な定数とサブルーチン プロトタイプをすべて定義しています。*nx_bsd.c* は BSD Sockets API 互換レイヤーのソース コードそのものです。 これらのBSD ラッパーソース ファイルは、すべての NetX サポート パッケージに共通です。

パッケージは次のもので構成されます。

- **nx_bsd.c**: ラッパーのソース コード
- **nx_bsd.h**: メインのヘッダー ファイル

サンプル デモ プログラム:

- **bsd_demo_tcp.c**: *TCP サーバーおよびクライアントを 1 つずつ使用するデモ*
- **bsd_demo_udp.c**: *UDP クライアント 2 つと UDP サーバー 1 つを使用するデモ*
