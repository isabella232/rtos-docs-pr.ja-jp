---
title: 付録 C - Azure RTOS NetX Duo DHCPv6 の一意識別子 (DUID)
description: この章では、すべての NetX Duo DHCPv6 一意識別子 (DUID) について説明します
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: baa06faa0a4942d472783a11f89409254064e3204d5ae8d9759977cf3b14ef53
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783698"
---
# <a name="appendix-c---azure-rtos-netx-duo-dhcpv6-unique-identifiers-duids"></a>付録 C - Azure RTOS NetX Duo DHCPv6 の一意識別子 (DUID)

| DUID の種類              | コード            | 説明 |
| ------------------- | ------------------- | --------------- |
| DUID-LLT | 1 | リンク レイヤー + 時間。リンク レイヤーのアドレスと時刻に基づく識別子 |
| DUID-EN | 2 | エンタープライズ。エンタープライズ番号に基づいてベンダーによって割り当てられます |
| DUID-LL | 3 | リンク レイヤー。リンク レイヤー アドレスのみに基づきます| 