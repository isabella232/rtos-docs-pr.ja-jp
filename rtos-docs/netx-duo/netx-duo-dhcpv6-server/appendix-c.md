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
# <a name="appendix-c---azure-rtos-netx-duo-dhcpv6-unique-identifiers-duids"></a><span data-ttu-id="e4575-103">付録 C - Azure RTOS NetX Duo DHCPv6 の一意識別子 (DUID)</span><span class="sxs-lookup"><span data-stu-id="e4575-103">Appendix C - Azure RTOS NetX Duo DHCPv6 unique identifiers (DUIDs)</span></span>

| <span data-ttu-id="e4575-104">DUID の種類</span><span class="sxs-lookup"><span data-stu-id="e4575-104">DUID Type</span></span>              | <span data-ttu-id="e4575-105">コード</span><span class="sxs-lookup"><span data-stu-id="e4575-105">Code</span></span>            | <span data-ttu-id="e4575-106">説明</span><span class="sxs-lookup"><span data-stu-id="e4575-106">Description</span></span> |
| ------------------- | ------------------- | --------------- |
| <span data-ttu-id="e4575-107">DUID-LLT</span><span class="sxs-lookup"><span data-stu-id="e4575-107">DUID-LLT</span></span> | <span data-ttu-id="e4575-108">1</span><span class="sxs-lookup"><span data-stu-id="e4575-108">1</span></span> | <span data-ttu-id="e4575-109">リンク レイヤー + 時間。リンク レイヤーのアドレスと時刻に基づく識別子</span><span class="sxs-lookup"><span data-stu-id="e4575-109">Link layer plus time; identifier based on link layer address and time</span></span> |
| <span data-ttu-id="e4575-110">DUID-EN</span><span class="sxs-lookup"><span data-stu-id="e4575-110">DUID-EN</span></span> | <span data-ttu-id="e4575-111">2</span><span class="sxs-lookup"><span data-stu-id="e4575-111">2</span></span> | <span data-ttu-id="e4575-112">エンタープライズ。エンタープライズ番号に基づいてベンダーによって割り当てられます</span><span class="sxs-lookup"><span data-stu-id="e4575-112">Enterprise; Assigned by Vendor Based on Enterprise Number</span></span> |
| <span data-ttu-id="e4575-113">DUID-LL</span><span class="sxs-lookup"><span data-stu-id="e4575-113">DUID-LL</span></span> | <span data-ttu-id="e4575-114">3</span><span class="sxs-lookup"><span data-stu-id="e4575-114">3</span></span> | <span data-ttu-id="e4575-115">リンク レイヤー。リンク レイヤー アドレスのみに基づきます</span><span class="sxs-lookup"><span data-stu-id="e4575-115">Link layer; Based on Link-layer Address only</span></span>| 