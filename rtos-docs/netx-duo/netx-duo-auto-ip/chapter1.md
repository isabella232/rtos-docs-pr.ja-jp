---
title: 第 1 章 - Azure RTOS NetX Duo AutoIP の概要
description: AutoIP プロトコルは、ローカル ネットワーク上で IPv4 アドレスを動的に構成するために設計されたプロトコルです。 Azure RTOS NetX Duo AutoIP パッケージが正しく機能するには、NetX IP インスタンスが既に作成されている必要があります。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7f756f0e9f4ab1bddd6c28449dbd695e23758b16
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811828"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-autoip"></a><span data-ttu-id="e688c-104">第 1 章 - Azure RTOS NetX Duo AutoIP の概要</span><span class="sxs-lookup"><span data-stu-id="e688c-104">Chapter 1 - Introduction to Azure RTOS NetX Duo AutoIP</span></span>

<span data-ttu-id="e688c-105">AutoIP プロトコルは、ローカル ネットワーク上で IPv4 アドレスを動的に構成するために設計されたプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="e688c-105">The AutoIP Protocol is a protocol designed for dynamically configuring IPv4 addresses on a local network.</span></span> <span data-ttu-id="e688c-106">AutoIP は、その IP アドレス自動割り当て機能を実行するために ARP 機能を利用する単純なプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="e688c-106">AutoIP is a simple protocol that utilizes ARP capabilities to perform its automatic IP address assignment function.</span></span> <span data-ttu-id="e688c-107">AutoIP では、169.254.1.0 ～ 169.254.254.255 の範囲のアドレスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e688c-107">AutoIP allocates addresses in the range of 169.254.1.0 through 169.254.254.255.</span></span>

## <a name="autoip-requirements"></a><span data-ttu-id="e688c-108">AutoIP の要件</span><span class="sxs-lookup"><span data-stu-id="e688c-108">AutoIP Requirements</span></span>

<span data-ttu-id="e688c-109">Azure RTOS NetX Duo AutoIP パッケージが正しく機能するには、NetX IP インスタンスが既に作成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e688c-109">In order to function properly, the Azure RTOS NetX Duo AutoIP package requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="e688c-110">さらに、その同じ IP インスタンス上で ARP が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e688c-110">In addition, ARP must be enabled on that same IP instance.</span></span> <span data-ttu-id="e688c-111">NetX AutoIP パッケージには、それ以上の要件はありません。</span><span class="sxs-lookup"><span data-stu-id="e688c-111">The NetX AutoIP package has no further requirements.</span></span>

## <a name="autoip-constraints"></a><span data-ttu-id="e688c-112">AutoIP の制約</span><span class="sxs-lookup"><span data-stu-id="e688c-112">AutoIP Constraints</span></span>

<span data-ttu-id="e688c-113">NetX AutoIP プロトコルでは、RFC3927 標準の要件を実装しています。</span><span class="sxs-lookup"><span data-stu-id="e688c-113">The NetX AutoIP protocol implements the requirements of the RFC3927 standard.</span></span> <span data-ttu-id="e688c-114">ただし、次の制約があります。</span><span class="sxs-lookup"><span data-stu-id="e688c-114">However, there are the following constraints:</span></span>

1. <span data-ttu-id="e688c-115">NetX DHCP が使用される場合は、DHCP スレッドを、NetX IP インスタンス スレッドと AutoIP スレッドの両方より高い優先度で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e688c-115">If NetX DHCP is used, the DHCP thread must be created with a higher priority than both the NetX IP instance thread and the AutoIP thread.</span></span>

1. <span data-ttu-id="e688c-116">NetX AutoIP には、古い IP アドレスを引き続き使用するためのメカニズムは用意されていません。</span><span class="sxs-lookup"><span data-stu-id="e688c-116">NetX AutoIP does not provide a mechanism for old IP addresses to continue being used.</span></span>

1. <span data-ttu-id="e688c-117">IP アドレスが変更された場合、既存の TCP 接続をすべて切断し、それらを新しい IP アドレス上で再確立する処理はアプリケーションが担当します。</span><span class="sxs-lookup"><span data-stu-id="e688c-117">When the IP address changes, the application is responsible for tearing down any existing TCP connections and re-establishing them on the new IP address.</span></span>

## <a name="autoip-protocol-implementation"></a><span data-ttu-id="e688c-118">AutoIP プロトコルの実装</span><span class="sxs-lookup"><span data-stu-id="e688c-118">AutoIP Protocol Implementation</span></span>

<span data-ttu-id="e688c-119">NetX AutoIP プロトコルでは、最初に 169.254.1.0 ～ 169.254.254.255 の AutoIP IPv4 アドレス範囲内のランダムなアドレスを選択します。</span><span class="sxs-lookup"><span data-stu-id="e688c-119">The NetX AutoIP protocol first selects a random address within the AutoIP IPv4 address range of 169.254.1.0 through 169.254.254.255.</span></span> <span data-ttu-id="e688c-120">あるいは、***nx_auto_ip_start*** 関数に指定することにより、アプリケーションで開始 IP アドレスを強制することもできます。</span><span class="sxs-lookup"><span data-stu-id="e688c-120">Alternatively, the application may force a starting IP address by providing it to the ***nx_auto_ip_start*** function.</span></span> <span data-ttu-id="e688c-121">これは、以前の実行である AutoIP アドレスが正常に使用されていた状況で役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e688c-121">This is useful in situations where an AutoIP address was successfully used in a prior run.</span></span>

<span data-ttu-id="e688c-122">AutoIP アドレスが選択されると、NetX AutoIP では、その選択されたアドレスの一連の ARP プローブを送出します。</span><span class="sxs-lookup"><span data-stu-id="e688c-122">Once an AutoIP address is selected, NetX AutoIP sends out a series of ARP probes for the selected address.</span></span> <span data-ttu-id="e688c-123">ARP プローブは、送信者アドレスが 0.0.0.0 に設定され、ターゲット アドレスが目的の AutoIP アドレスに設定されている ARP 要求メッセージで構成されます。</span><span class="sxs-lookup"><span data-stu-id="e688c-123">An ARP probe consists of an ARP request message with the sender address set to 0.0.0.0 and the target address set to the desired AutoIP address.</span></span> <span data-ttu-id="e688c-124">これらの一連の ARP プローブが送信されます (実際の数は、定義 NX_AUTO_IP_PROBE_NUM によって決定されます)。</span><span class="sxs-lookup"><span data-stu-id="e688c-124">A series of these ARP probes are sent (the actual number is determined by the define NX_AUTO_IP_PROBE_NUM).</span></span> <span data-ttu-id="e688c-125">別のネットワーク ノードがこのプローブに応答するか、または同じアドレスの同一のプローブを送信した場合は、新しい AutoIP アドレスが AutoIP IPv4 アドレス範囲内でランダムに選択され、プローブ処理が繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="e688c-125">If another network node responds to this probe or sends an identical probe for the same address, a new AutoIP address is randomly selected within the AutoIP IPv4 address range and the probe processing repeats.</span></span>

<span data-ttu-id="e688c-126">NX_AUTO_IP_PROBE_NUM 個のプローブが送信されても応答がなかった場合、NetX AutoIP では、選択されたアドレスの一連の ARP アナウンスを発行します。</span><span class="sxs-lookup"><span data-stu-id="e688c-126">If NX_AUTO_IP_PROBE_NUM probes are sent without any responses, NetX AutoIP issues a series of ARP announcements for the selected address.</span></span> <span data-ttu-id="e688c-127">ARP アナウンスは、ARP メッセージ内の送信者アドレスとターゲット アドレスの両方が選択された AutoIP アドレスに設定されている ARP 要求メッセージで構成されます。</span><span class="sxs-lookup"><span data-stu-id="e688c-127">An ARP announcement consists of an ARP request message with both the sender and target address in the ARP message set to the selected AutoIP address.</span></span> <span data-ttu-id="e688c-128">定義 NX_AUTO_IP_ANNOUNCE_NUM に対応する一連の ARP アナウンス メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="e688c-128">A series of ARP announcement messages are sent, corresponding to the define NX_AUTO_IP_ANNOUNCE_NUM.</span></span> <span data-ttu-id="e688c-129">別のネットワーク ノードがアナウンス メッセージに応答するか、または同じアドレスの同一のアナウンスを送信した場合は、新しい AutoIP アドレスが AutoIP IPv4 アドレス範囲内でランダムに選択され、プローブ処理が始めからやり直されます。</span><span class="sxs-lookup"><span data-stu-id="e688c-129">If another network node responds to an announce message or sends an identical announcement for the same address, a new AutoIP address is randomly selected within the AutoIP IPv4 address range and the probe processing starts over.</span></span>

<span data-ttu-id="e688c-130">競合がまったく検出されずにプローブとアナウンスが完了すると、選択された AutoIP アドレスは有効と見なされ、関連付けられた IP インスタンスがこのアドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="e688c-130">When the probe and announcement completes without any detected conflicts, the selected AutoIP address is considered valid and the associated IP instance is setup with this address.</span></span>

## <a name="autoip-address-change"></a><span data-ttu-id="e688c-131">AutoIP アドレスの変更</span><span class="sxs-lookup"><span data-stu-id="e688c-131">AutoIP Address Change</span></span>

<span data-ttu-id="e688c-132">先に説明したように、NetX AutoIP では、プローブ処理とアナウンス処理が成功した後に IP インスタンス アドレスを変更します。</span><span class="sxs-lookup"><span data-stu-id="e688c-132">As mentioned before, NetX AutoIP changes the IP instance address after successful probe and announcement processing.</span></span> <span data-ttu-id="e688c-133">このケースの監視はそれほど重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="e688c-133">Monitoring for this case is not terribly important.</span></span> <span data-ttu-id="e688c-134">ただし、将来 AutoIP アドレスが変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e688c-134">However, it is possible to have the AutoIP address change in the future.</span></span> <span data-ttu-id="e688c-135">潜在的な原因には、将来の AutoIP アドレスの競合や DHCP アドレス解決が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e688c-135">Potential causes include future AutoIP address conflicts as well as DHCP address resolution.</span></span> <span data-ttu-id="e688c-136">これらの潜在的な状況を適切に処理するために、アプリケーションでは、次の NetX API を使用して IP アドレスのすべての変更を自身に通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e688c-136">In order to process these potential situations properly, the application should use the following NetX API to alert it of any and all IP address changes:</span></span>

```c
nx_ip_address_change_notify(NX_IP *ip_ptr,
            VOID (*ip_address_change_notify)(NX_IP *,VOID*),
            VOID *additional_info);
```

<span data-ttu-id="e688c-137">指定されている *ip_address_change_notify* 関数の処理では、NetX AutoIP プロセッサを再起動するか、またはその後 DHCP でその IP アドレスが解決された場合はそれを無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e688c-137">The processing in the supplied *ip_address_change_notify* function must either restart the NetX AutoIP processor or disable it if DHCP has subsequently resolved the IP address.</span></span> <span data-ttu-id="e688c-138">処理の例については、「*小規模システムの例*」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e688c-138">Please refer to the *Small Example System* section for sample processing.</span></span>

## <a name="autoip-rfcs"></a><span data-ttu-id="e688c-139">AutoIP RFC</span><span class="sxs-lookup"><span data-stu-id="e688c-139">AutoIP RFCs</span></span>

<span data-ttu-id="e688c-140">NetX AutoIP は、RFC3927 および関連する RFC に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="e688c-140">NetX AutoIP is compliant with RFC3927 and related RFCs.</span></span>