---
title: 付録 C - Azure RTOS NetX Duo DHCPv6 の一意識別子 (DUID)
description: この章では、すべての NetX Duo DHCPv6 一意識別子 (DUID) について説明します
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dc9dadcabb3f87d217a4560457614a55a3be03aa
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810871"
---
# <a name="appendix-c---azure-rtos-netx-duo-dhcpv6-unique-identifiers-duids"></a>付録 C - Azure RTOS NetX Duo DHCPv6 の一意識別子 (DUID)

| DUID の種類              | コード            | 説明 |
| ------------------- | ------------------- | --------------- |
| DUID-LLT | 1 | リンク レイヤー + 時間。リンク レイヤーのアドレスと時刻に基づく識別子 |
| DUID-EN | 2 | エンタープライズ。エンタープライズ番号に基づいてベンダーによって割り当てられます |
| DUID-LL | 3 | リンク レイヤー。リンク レイヤー アドレスのみに基づきます| 