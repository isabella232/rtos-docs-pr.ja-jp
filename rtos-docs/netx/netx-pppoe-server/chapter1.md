---
title: 第 1 章 - Azure RTOS NetX PPPoE サーバーの概要
description: このドキュメントでは、Azure RTOS NetX PPPoE モジュールの詳細について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 85a762f669e31c7e753f78b270ced15677a87c4c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811426"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pppoe-server"></a>第 1 章 - Azure RTOS NetX PPPoE サーバーの概要

ホスト で PPP over Ethernet (PPPoE) を使用することにより、従来の文字ベースのシリアル回線通信ではなく、イーサネット経由で PPP サーバーに接続できます。 PPPoE の技術的な詳細については、RFC 2516 の PPP over Ethernet (PPPoE) を送信する方法に関する説明を参照してください。 このドキュメントでは、Azure RTOS NetX PPPoE モジュールの詳細について説明します。

イーサネット経由のポイント ツー ポイント接続を提供するには、各 PPP セッションでリモート ピアのイーサネット アドレスを認識し、一意のセッション識別子を確立する必要があります。

RFC 2516 によれば、PPPoE は、検出ステージと PPPoE セッション ステージという 2 つのステージで構成されます。 ホスト (クライアント) で PPP セッションを開始するときは、最初に、検出を実行して PPPoE サーバーを見つける必要があります。 また、このステップにより、サーバーとクライアントは互いのイーサネット MAC アドレスと SESSION_ID を識別できます。これは、PPP セッションの残りの部分で使用されます。

イーサネット フレームは次のとおりです。

![イーサネット フレームを示す図。](media/netx-pppoe-server-01.png)

PPPoE のイーサネット ペイロードは次のとおりです。

![PPPoE のイーサネット ペイロードを示す図。](media/netx-pppoe-server-02.png)

## <a name="pppoe-discovery-stage"></a>PPPoE 検出ステージ

PPPoE 検出ステージにより、クライアントは、ネットワーク上の使用可能なすべてのサーバーから 1 つのサーバーを選択し、PPP フレーム交換の前にセッションを効率的に作成できます。 検出ステージの終了時には、クライアントとサーバーの両方が一意のセッション ID に同意し、両方の側がピアの MAC アドレスを認識している必要があります。

| 検出メッセージ                                  | コード | Direction                                     |
| -------------------------------------------------- | ---- | --------------------------------------------- |
| PPPoE アクティブ検出開始 (PADI)           | 0x09 | クライアントからブロードキャストへ                      |
| PPPoE アクティブ検出提供 (PADO)                | 0x07 | サーバーからクライアントへ                         |
| PPPoE アクティブ検出要求 (PADR)              | 0x19 | クライアントからサーバーへ                         |
| PPPOE アクティブ検出セッション確認 (PADS) | 0x65 | サーバーからクライアントへ                         |
| PPPoE アクティブ検出終了 (PADT)            | 0xa7 | サーバーまたはクライアントのどちらからでも開始可能 |

すべての検出イーサネット フレームには、値 0x8863 に設定された ETHER_TYPE フィールドがあります。

## <a name="pppoe-session-message"></a>PPPoE セッション メッセージ

クライアントとサーバーによってセッションが作成された後、PPPoE セッション メッセージとして PPP フレームを転送できます。 セッションの間に、SESSION_ID が変化してはならず、検出ステージの間にサーバーによって割り当てられた値である必要があります。

すべての PPPoE セッション イーサネット フレームには、値 0x8864 に設定された ETHER_TYPE フィールドがあります。