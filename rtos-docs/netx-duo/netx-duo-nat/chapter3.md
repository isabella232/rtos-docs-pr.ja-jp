---
title: 第 3 章 - NAT 構成オプション
description: 次の一覧に、すべてのオプションとその機能について詳しく説明します
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9c10d6f0d2f36d2794ab1229081799f0032cada8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810676"
---
# <a name="chapter-3---nat-configuration-options"></a>第 3 章 - NAT 構成オプション

NetX Duo NAT API の構成可能なオプションは *nx_nat.h* に含まれていますが、最初の **NX_DISABLE_ERROR_CHECKING** は例外で *nx_nat.c* に含まれています。 次の一覧に、すべてのオプションとその機能について詳しく説明します。

- **NX_NAT_DISABLE_ERROR_CHECKING**: このオプションを定義すると、基本的な NAT エラー チェックが削除されます。 通常は、アプリケーションがデバッグされた後に使用されます。 既定の NetX Duo NAT の状態が定義されます (有効)。
- **NX_NAT_ENABLE_REPLACEMENT**: このオプションを定義すると、NAT キャッシュがいっぱいになったときに自動置換が有効になります。
  > [!NOTE]
  > 最も古い非 TCP セッションのみを置き換えます。
- **NX_NAT_MIN_ENTRY_COUNT**: このオプションは、変換エントリの最小数を設定します。 既定値は 3 です。
- **NX_NAT_TCP_SESSION_TIMEOUT**: このオプションは、TCP セッションの変換エントリのタイムアウトを設定します。 既定のタイムアウトは 24 時間です。
- **NX_NAT_NON_TCP_SESSION_TIMEOUT**: このオプションは、非 TCP セッションの変換エントリのタイムアウトを設定します。 既定のタイムアウトは 240 秒です。
- **NX_NAT_START_TCP_PORT**: このオプションは、送信 TCP パケットを割り当てる未使用の TCP ポートを検索する際の開始値を設定します。 既定値は 20000 です。
- **NX_NAT_END_TCP_PORT**: このオプションは、送信 TCP パケットを割り当てる TCP ポートの上限を設定します。 既定値は 30,000 です。
- **NX_NAT_START_UDP_PORT**: このオプションは、送信 UDP パケットを割り当てる未使用の UDP ポートを検索する際の開始値を設定します。 既定値は 20000 です。
- **NX_NAT_END_UDP_PORT**: このオプションは、送信 UDP パケットを割り当てる UDP ポートの上限を設定します。 既定値は 30,000 です。
- **NX_NAT_START_ICMP_QUERY_ID**: このオプションは、送信 ICMP クエリ パケットを割り当てる未使用のクエリ ID を検索する際の開始値を設定します。 既定値は 20000 です。
- **NX_NAT_START_ICMP_QUERY_ID**: このオプションは、送信 ICMP クエリ パケットを割り当てる未使用のクエリ ID の上限を設定します。 既定値は 30,000 です。
