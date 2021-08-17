---
title: 第 1 章 - Azure RTOS NetX Duo mDNS/DNS-SD の概要
description: Azure RTOS NetX Duo mDNS/DNS-SD は、従来の DNS サービスを強化します。
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7cde8e81809dcc74ee5d0b09d8e7a8d2ae96850cd84250a5bf003fdd5763925a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796448"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mdnsdns-sd"></a>第 1 章 - Azure RTOS NetX Duo mDNS/DNS-SD の概要

mDNS と DNS-SD は、従来の DNS サービスを強化するように設計されたプロトコルです。 mDNS は、ホスト名とサービス検索をローカル ネットワーク上のノードに提供します。 各ノードでは、提供するサービスを IPv4 または IPv6 マルチキャスト チャネルを使用してその近隣ノードにアナウンスし、近隣からのクエリに応答し、アプリケーションに代わってクエリを送信します。 設計上、mDNS は分散環境で動作するため、集中管理されたサービスが排除されます。

DNS-SD は、mDNS の上位に構築されます。 DNS-SD を使用すると、ノードが提供するサービスをローカル ネットワークにアナウンスしたり、ローカル ネット ワーク上の他のノードによって提供されるサービスを探索したりできます。 このドキュメント全体で、*mDNS* という用語は、mDNS 仕様と DNS-SD 仕様の両方をカバーするサービスを指します。

## <a name="mdns-standard"></a>mDNS 標準

NetX Duo mDNS/DNS-SD の実装は、次の RFC に準拠しています。

- RFC 6762: mDNS 仕様
- RFC 6763: DNS-SD 仕様