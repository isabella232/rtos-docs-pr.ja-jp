---
title: 付録 B - Azure RTOS NetX Duo DHCPv6 サーバーの状態コード
description: この章では、すべての NetX Duo DHCPv6 サーバーの状態コードについて説明します
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7c79a0c0bc9acfcfca69c7333d30cd7cab35ba5f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810874"
---
# <a name="appendix-b---azure-rtos-netx-duo-dhcpv6-server-status-codes"></a><span data-ttu-id="ad8bb-103">付録 B - Azure RTOS NetX Duo DHCPv6 サーバーの状態コード</span><span class="sxs-lookup"><span data-stu-id="ad8bb-103">Appendix B - Azure RTOS NetX Duo DHCPv6 server status codes</span></span>

| <span data-ttu-id="ad8bb-104">名前</span><span class="sxs-lookup"><span data-stu-id="ad8bb-104">Name</span></span>              | <span data-ttu-id="ad8bb-105">コード</span><span class="sxs-lookup"><span data-stu-id="ad8bb-105">Code</span></span>            | <span data-ttu-id="ad8bb-106">説明</span><span class="sxs-lookup"><span data-stu-id="ad8bb-106">Description</span></span> |
| ------------------- | ------------------- | --------------- |
| <span data-ttu-id="ad8bb-107">Success</span><span class="sxs-lookup"><span data-stu-id="ad8bb-107">Success</span></span> | <span data-ttu-id="ad8bb-108">0</span><span class="sxs-lookup"><span data-stu-id="ad8bb-108">0</span></span> | <span data-ttu-id="ad8bb-109">成功</span><span class="sxs-lookup"><span data-stu-id="ad8bb-109">Success</span></span> |
| <span data-ttu-id="ad8bb-110">Unspecified Failure</span><span class="sxs-lookup"><span data-stu-id="ad8bb-110">Unspecified Failure</span></span> | <span data-ttu-id="ad8bb-111">1</span><span class="sxs-lookup"><span data-stu-id="ad8bb-111">1</span></span> | <span data-ttu-id="ad8bb-112">エラー。理由が指定されていません。この状態コードは、クライアント要求が他のコードと一致しないという一般的なエラーを示すために、サーバーによって設定されます</span><span class="sxs-lookup"><span data-stu-id="ad8bb-112">Failure, reason unspecified; this status code is set by the Server to indicate a general failure in granting the Client request not matching the other codes</span></span> |
| <span data-ttu-id="ad8bb-113">使用可能なアドレスがありません</span><span class="sxs-lookup"><span data-stu-id="ad8bb-113">NoAddress Available</span></span> | <span data-ttu-id="ad8bb-114">2</span><span class="sxs-lookup"><span data-stu-id="ad8bb-114">2</span></span> | <span data-ttu-id="ad8bb-115">サーバーには、クライアントに割り当てることができるアドレスがありません</span><span class="sxs-lookup"><span data-stu-id="ad8bb-115">Server has no addresses available to assign to the Client</span></span> |
| <span data-ttu-id="ad8bb-116">NoBinding</span><span class="sxs-lookup"><span data-stu-id="ad8bb-116">NoBinding</span></span> | <span data-ttu-id="ad8bb-117">3</span><span class="sxs-lookup"><span data-stu-id="ad8bb-117">3</span></span> | <span data-ttu-id="ad8bb-118">クライアント IA アドレス (バインド) を使用できません。たとえば、要求された IP アドレスを、サーバーがリースしたり、別のクライアントに割り当てたりすることはできません</span><span class="sxs-lookup"><span data-stu-id="ad8bb-118">Client IA address (binding) is not available e.g. the requested IP address is not available for the Server to lease or assigned to another Client.</span></span> |
| <span data-ttu-id="ad8bb-119">NotOnLink</span><span class="sxs-lookup"><span data-stu-id="ad8bb-119">NotOnLink</span></span> | <span data-ttu-id="ad8bb-120">4</span><span class="sxs-lookup"><span data-stu-id="ad8bb-120">4</span></span> | <span data-ttu-id="ad8bb-121">アドレスのプレフィックスが、IP アドレスがオン リンク アドレスではないことを示しています</span><span class="sxs-lookup"><span data-stu-id="ad8bb-121">The prefix for the address indicates the IP address is not an on link address</span></span> |
| <span data-ttu-id="ad8bb-122">UseMulticast</span><span class="sxs-lookup"><span data-stu-id="ad8bb-122">UseMulticast</span></span> | <span data-ttu-id="ad8bb-123">5</span><span class="sxs-lookup"><span data-stu-id="ad8bb-123">5</span></span> | <span data-ttu-id="ad8bb-124">*All_DHCP_Relay_Agents_and_Servers* マルチキャスト アドレスの代わりにサーバーのユニキャスト アドレスを使用したクライアント メッセージの受信に応答して、サーバーによって送信されます</span><span class="sxs-lookup"><span data-stu-id="ad8bb-124">Sent by a Server in response to receiving a Client message using the Server’s unicast address instead of the *All_DHCP_Relay_Agents_and_Servers* multicast address</span></span> |