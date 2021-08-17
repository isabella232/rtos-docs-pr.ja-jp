---
title: 付録 B - Azure RTOS NetX Duo DHCPv6 サーバーの状態コード
description: この章では、すべての NetX Duo DHCPv6 サーバーの状態コードについて説明します
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8b9795607c0fed80646ee01e36edf4ecd2aaadad7f0a023e6979e123b81e1660
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791773"
---
# <a name="appendix-b---azure-rtos-netx-duo-dhcpv6-server-status-codes"></a>付録 B - Azure RTOS NetX Duo DHCPv6 サーバーの状態コード

| 名前              | コード            | 説明 |
| ------------------- | ------------------- | --------------- |
| Success | 0 | 成功 |
| Unspecified Failure | 1 | エラー。理由が指定されていません。この状態コードは、クライアント要求が他のコードと一致しないという一般的なエラーを示すために、サーバーによって設定されます |
| 使用可能なアドレスがありません | 2 | サーバーには、クライアントに割り当てることができるアドレスがありません |
| NoBinding | 3 | クライアント IA アドレス (バインド) を使用できません。たとえば、要求された IP アドレスを、サーバーがリースしたり、別のクライアントに割り当てたりすることはできません |
| NotOnLink | 4 | アドレスのプレフィックスが、IP アドレスがオン リンク アドレスではないことを示しています |
| UseMulticast | 5 | *All_DHCP_Relay_Agents_and_Servers* マルチキャスト アドレスの代わりにサーバーのユニキャスト アドレスを使用したクライアント メッセージの受信に応答して、サーバーによって送信されます |