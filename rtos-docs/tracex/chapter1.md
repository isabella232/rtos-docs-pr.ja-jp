---
title: 第 1 章 - Azure RTOS TraceX の概要
description: Azure RTOS TraceX は、組み込みターゲット上で実行されている ThreadX によって収集されたシステム イベント情報を表示する、Microsoft のシステム分析ツールです。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 3009d13388b3b7e8eca041dc6ede569a5caf5e9b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812500"
---
# <a name="chapter-1---introduction-to-azure-rtos-tracex"></a>第 1 章 - Azure RTOS TraceX の概要

Azure RTOS TraceX は、組み込みターゲット上で実行されている ThreadX によって収集されたシステム イベント情報を表示する、Microsoft のシステム分析ツールです。 ユーザーは、組み込みターゲットの RAM に格納されているトレース バッファーを、ホスト コンピューター上のバイナリ ファイルに転送する役割を担います。 次に、ユーザーはこのファイルを TraceX で開き、対象のイベントをグラフィカルに分析して、システムの問題を診断し、動作しているアプリケーションをチューニングしてパフォーマンスとリソース管理を向上させることができます。

## <a name="tracex-requirements"></a>TraceX の要件

TraceX には Windows XP (またはそれ以降) が必要です。 システムには、最低 192 MB の RAM、2 GB のハードディスク空き領域、および最低 256 色、1024x768 の表示が必要です。 また、アプリケーションは ThreadX V5.0 以降で実行されている必要があります。

TraceX では、Microsoft .NET Framework をインストールする必要もあります。これは TraceX インストーラーによって自動的に行われます。

## <a name="tracex-constraints"></a>TraceX の制約

TraceX には次の制約があります。

- TraceX のファイルは、最大 32,768 イベント (約 1 MB) に制限されています。
- タイムスタンプ ソースには、適切な解像度が必要です。 解像度が低すぎると、イベントは重複します。 解像度が高すぎると、イベント間に長時間のギャップが生じる可能性があります。
- TraceX では、タイマー期間よりも長いイベント間の間隔を正確に測定することはできません。
