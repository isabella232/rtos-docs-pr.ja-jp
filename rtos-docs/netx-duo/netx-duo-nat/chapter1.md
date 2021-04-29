---
title: 第 1 章 - ネットワーク アドレス変換の概要
description: IP のネットワーク アドレス変換 (NAT) は、もともと、限られた数のインターネット IPv4 アドレスの問題を解決するために開発されました。
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3d01aa6f68e21ea82f65a59a19c4f5c7958a6b92
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810685"
---
# <a name="chapter-1---an-introduction-to-network-address-translation"></a><span data-ttu-id="e9c62-103">第 1 章 - ネットワーク アドレス変換の概要</span><span class="sxs-lookup"><span data-stu-id="e9c62-103">Chapter 1 - An introduction to Network Address Translation</span></span>

## <a name="the-need-for-network-address-translation"></a><span data-ttu-id="e9c62-104">ネットワーク アドレス変換の必要性</span><span class="sxs-lookup"><span data-stu-id="e9c62-104">The Need for Network Address Translation</span></span>

<span data-ttu-id="e9c62-105">IP のネットワーク アドレス変換 (NAT) は、もともと、限られた数のインターネット IPv4 アドレスの問題を解決するために開発されました。</span><span class="sxs-lookup"><span data-stu-id="e9c62-105">IP Network Address Translation (NAT) was originally developed to solve the problem of a limited number of Internet IPv4 addresses.</span></span> <span data-ttu-id="e9c62-106">複数のデバイスがインターネットにアクセスする必要があり、しかしインターネット サービス プロバイダー (ISP) によって割り当てられる IPv4 インターネット アドレスが 1 つだけである場合、NAT が必要になります。</span><span class="sxs-lookup"><span data-stu-id="e9c62-106">The need for NAT arises when multiple devices need to access the Internet but only one IPv4 Internet address is assigned by the Internet Service Provider (ISP).</span></span>

<span data-ttu-id="e9c62-107">NAT を使用すると、他にも利点があります。</span><span class="sxs-lookup"><span data-stu-id="e9c62-107">There are other benefits of using NAT as well.</span></span> <span data-ttu-id="e9c62-108">ローカル ドメインの外部のネットワーク トポロジを、さまざまな方法で変更できます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-108">Network topology outside the local domain can change in many ways.</span></span> <span data-ttu-id="e9c62-109">お客様はプロバイダーを変更したり、企業はバックボーンを再構成したり、プロバイダーを結合または分割したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-109">Customers may change providers, company backbones may be reorganized, or providers may merge or split.</span></span> <span data-ttu-id="e9c62-110">外部のトポロジが変化するたびに、それらの外部の変更を反映するように、ローカル ドメイン内のホストのアドレスの割り当ても変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9c62-110">Whenever the external topology changes, address assignments for hosts within the local domain must also change to reflect these external changes.</span></span> <span data-ttu-id="e9c62-111">この種の変更は、単一のアドレス変換ルーターに変更を一元化することで、ドメイン内のユーザーに認識されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-111">Changes of this type can be hidden from users within the domain by centralizing changes to a single address translation router.</span></span> <span data-ttu-id="e9c62-112">NAT を使用すると、ローカル ホストからパブリック インターネットにアクセスできるようになり、外部からの直接アクセスから保護されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-112">NAT enables access for local hosts to the public Internet and protects them from direct access from the outside.</span></span> <span data-ttu-id="e9c62-113">ネットワークのセットアップは内部使用が中心で、外部アクセスの必要性が低い組織は、このスキームの候補として適しています。</span><span class="sxs-lookup"><span data-stu-id="e9c62-113">Organizations with a network setup predominantly for internal use, with a need for occasional external access are good candidates for this scheme.</span></span>

## <a name="basic-nat-and-network-address-port-translation"></a><span data-ttu-id="e9c62-114">基本的な NAT とネットワーク アドレス ポート変換</span><span class="sxs-lookup"><span data-stu-id="e9c62-114">Basic NAT and Network Address Port Translation</span></span>

<span data-ttu-id="e9c62-115">NAT 対応のルーターは、パブリック ネットワークとプライベート ネットワークの間にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-115">A NAT-enabled router is installed between the public network and the private network.</span></span> <span data-ttu-id="e9c62-116">NAT 対応のルーターの役割は、内部のプライベート IPv4 アドレスと、割り当てられているパブリック IPv4 アドレスとの間の変換を行うことなので、プライベート ネットワーク上のすべてのデバイスが、同じパブリック IPv4 アドレスを共有できます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-116">The role of the NAT-enabled router is to translate between the internal private IPv4 addresses and the assigned public IPv4 address, so all the devices on the private network are able to share the same public IPv4 address.</span></span>

<span data-ttu-id="e9c62-117">NAT の基本的な実装では、NAT ルーターにより、自身の IP アドレスとは別に、1 つまたは複数のグローバルに登録された IP アドレスが "所有されます"。</span><span class="sxs-lookup"><span data-stu-id="e9c62-117">In the basic implementation of NAT, the NAT router ‘owns’ one or more globally registered IP addresses different from its own IP address.</span></span> <span data-ttu-id="e9c62-118">これらのグローバル アドレスは、プライベート ネットワーク上のホストに静的または動的に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-118">These global addresses are available to assign to hosts on its private network either statically or dynamically.</span></span> <span data-ttu-id="e9c62-119">NAPT (ネットワーク アドレス ポート変換) は基本的な NAT の一種であり、"トランスポート" 識別子を含むようにネットワーク アドレス変換が拡張されたものです。</span><span class="sxs-lookup"><span data-stu-id="e9c62-119">NAPT, or Network Address Port Translation, is a variation of basic NAT, where network address translation is extended to include a ‘transport’ identifier.</span></span> <span data-ttu-id="e9c62-120">通常、これは、TCP および UDP パケットの場合はポート番号、ICMP パケットの場合はクエリ ID です。</span><span class="sxs-lookup"><span data-stu-id="e9c62-120">Most typically this is the port number for TCP and UDP packets, and the Query ID for ICMP packets.</span></span>

<span data-ttu-id="e9c62-121">NAT 境界をまたぐ接続は、通常、外部ホストに発信パケットを送信するプライベート ネットワーク上のホストによって開始されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-121">Connections across the NAT boundary are typically initiated by hosts on the private network sending outbound packets to an external host.</span></span> <span data-ttu-id="e9c62-122">通常、これらのホストには、この目的のために (一時的な) IP アドレスが "*動的に*" 割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-122">These hosts are usually assigned *dynamic* (temporary) IP addresses for this purpose.</span></span> <span data-ttu-id="e9c62-123">ただし、プライベート ネットワークに "サーバー" (たとえば、外部ネットワークからのクライアント要求を受け付ける HTTP または FTP サーバーなど) がある場合は、逆方向に接続を開始することもできます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-123">However, it is also possible to have connections initiated in the opposite direction if the private network has ‘servers’ e.g. HTTP or FTP servers that will accept Client requests from the external network.</span></span> <span data-ttu-id="e9c62-124">通常、これらのローカル ホストには、NAT により、"*静的な*" (永続的) IP アドレス:ポートが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-124">NAT will typically assign these local hosts a *static* (permanent) IP address:port.</span></span>

## <a name="how-network-address-translation-works"></a><span data-ttu-id="e9c62-125">ネットワーク アドレス変換の仕組み</span><span class="sxs-lookup"><span data-stu-id="e9c62-125">How Network Address Translation Works</span></span>

<span data-ttu-id="e9c62-126">図 1 は、NAT 対応ルーターを使用する一般的なネットワーク設定を示したものです。</span><span class="sxs-lookup"><span data-stu-id="e9c62-126">A typical network setup with a NAT-enabled router is illustrated in Figure 1.</span></span>

![NAT 対応ルーターのある一般的なネットワーク設定](media/image2.png)

<span data-ttu-id="e9c62-128">**図 1 - NAT 対応ルーターのある一般的なネットワーク設定**</span><span class="sxs-lookup"><span data-stu-id="e9c62-128">**Figure 1 - A typical network setup with a NAT-enabled router**</span></span>

<span data-ttu-id="e9c62-129">NAT 対応ルーターには、通常、2 つのネットワーク インターフェイスがあります。</span><span class="sxs-lookup"><span data-stu-id="e9c62-129">A NAT-enabled router typically has two network interfaces.</span></span> <span data-ttu-id="e9c62-130">1 つのインターフェイスは、パブリック インターネットに接続されています。もう 1 つは、プライベート ネットワークに接続されています。</span><span class="sxs-lookup"><span data-stu-id="e9c62-130">One interface is connected to the public Internet; the other is connected to the private network.</span></span> <span data-ttu-id="e9c62-131">このセットアップでの一般的なルーターには、宛先 IP アドレスに基づいてプライベート ネットワークとパブリック ネットワークの間で IP データグラムをルーティングする役割があります。</span><span class="sxs-lookup"><span data-stu-id="e9c62-131">A typical router in this setup is responsible for routing IP datagrams between the private network and the public network based on destination IP address.</span></span> <span data-ttu-id="e9c62-132">NAT 対応ルーターにより、パブリック インターフェイスとプライベート インターフェイスの間で IPv4 データグラムがルーティングされる前に、アドレス変換が実行されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-132">A NAT-enabled router performs address translation before routing an IPv4 datagram between the public and the private interface.</span></span> <span data-ttu-id="e9c62-133">変換は、内部送信元アドレス、送信元ポート番号、外部宛先アドレス、宛先ポート番号に基づいて、TCP または UDP のセッションごとに確立されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-133">A translation is established for each TCP or UDP session, based the internal source address, source port number, and external destination address and destination port number.</span></span> <span data-ttu-id="e9c62-134">ICMP のエコー要求と応答データグラムの場合は、ポート番号の代わりに ICMP クエリ ID が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-134">For ICMP echo request and response datagram, the ICMP query ID is used instead of the port number.</span></span>

<span data-ttu-id="e9c62-135">ネットワーク アドレス変換の一般的な実装を示すため、図 2 のネットワーク設定について考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="e9c62-135">To illustrate a typical implementation of Network Address Translation, let us consider a network setup in Figure 2.</span></span>

![ネットワーク アドレス変換の一般的な実装](media/image3.png)

<span data-ttu-id="e9c62-137">**図 2 - ネットワーク アドレス変換の一般的な実装**</span><span class="sxs-lookup"><span data-stu-id="e9c62-137">**Figure 2 - A typical implementation of Network Address Translation**</span></span>

<span data-ttu-id="e9c62-138">このシナリオでは、NAT ルーターによって、左側のプライベート ネットワークと、右側のパブリック ネットワークが接続されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-138">In this scenario, the NAT router connects the private network to the left, and the public network to the right.</span></span> <span data-ttu-id="e9c62-139">パブリック ネットワーク側の NAT ルーター インターフェイスの IP アドレスは 202.151.25.14 であり、プライベート ネットワーク インターフェイス側では、NAT ルーターによって IP アドレス 192.168.1.254 が使用されているものとします。</span><span class="sxs-lookup"><span data-stu-id="e9c62-139">Let’s assume on the public network side, the NAT router interface IP address is 202.151.25.14; on the private network interface, the NAT router uses the IP address 192.168.1.254.</span></span> <span data-ttu-id="e9c62-140">プライベート ネットワーク上のノードによって、インターネット上の Web サーバーとの TCP 接続が開始されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-140">A node on the private network initiates a TCP connection with a web server on the Internet.</span></span>

<span data-ttu-id="e9c62-141">図 3 は、ネットワーク アドレス変換プロセスの概要を示したものです。</span><span class="sxs-lookup"><span data-stu-id="e9c62-141">Figure 3 shows a high-level view of the Network Address Translation process.</span></span>

![ネットワーク アドレス変換プロセスの概要](media/image4.png)

<span data-ttu-id="e9c62-143">**図 3 - ネットワーク アドレス変換プロセスの概要**</span><span class="sxs-lookup"><span data-stu-id="e9c62-143">**Figure 3 - A high-level view of the Network Address Translation process**</span></span>

1. <span data-ttu-id="e9c62-144">クライアントによって、TCP SYN メッセージが Web サーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-144">Client transmits a TCP SYN message to the web server.</span></span> <span data-ttu-id="e9c62-145">送信元のアドレスは 192.168.1.15 で、ポート番号 6732 です。宛先のアドレスは 128.15.54.3 で、ポート番号 80 です。</span><span class="sxs-lookup"><span data-stu-id="e9c62-145">The sender address is 192.168.1.15, port number 6732; the destination address is 128.15.54.3, port number 80.</span></span>
1. <span data-ttu-id="e9c62-146">クライアントからのパケットは、NAT ルーターによってプライベート ネットワーク インターフェイスで受信されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-146">The packet from the Client is received on the private network interface by the NAT router.</span></span> <span data-ttu-id="e9c62-147">送信トラフィック規則がパケットに適用されます。送信側 (クライアント) のアドレスは NAT ルーターのパブリック IP アドレス 202.15.25.14 に変換され、送信側 (クライアント) の送信元ポート番号はパブリック インターフェイスの TCP ポート番号 2015 に変換されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-147">The outbound traffic rule applies to the packet: the sender’s (Client’s) address is translated to the NAT router’s public IP address 202.15.25.14, and sender (Client) source port number is translated to the TCP port number 2015 on the public interface.</span></span>
1. <span data-ttu-id="e9c62-148">パケットが、インターネットを介して送信され、最終的に宛先ホスト 128.15.54.3 に到達します。</span><span class="sxs-lookup"><span data-stu-id="e9c62-148">The packet is then transmitted over the Internet and ultimately reaches its destination host 128.15.54.3.</span></span> <span data-ttu-id="e9c62-149">受信側では、IP レイヤーの送信元アドレスと TCP レイヤーのポート番号に基づいて、パケットの発信元が 202.151.24.14、ポート番号が 2015 であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="e9c62-149">Notice that on the receiving side, based on the IP layer source address and TCP layer port number, the packet appears to have originated from 202.151.24.14, port number 2015.</span></span>
   <span data-ttu-id="e9c62-150">図 4 に、戻りパスでの NAT プロセスを示します。</span><span class="sxs-lookup"><span data-stu-id="e9c62-150">Figure 4 shows the NAT process on the return path.</span></span>

   ![戻りパスでの NAT プロセス](media/image5.png)

   <span data-ttu-id="e9c62-152">**図 4 - 戻りパスでの NAT プロセス**</span><span class="sxs-lookup"><span data-stu-id="e9c62-152">**Figure 4 - NAT process on the return path**</span></span>
1. <span data-ttu-id="e9c62-153">このシナリオでは、インターネット ホスト 128.15.54.3 により、NAT ルーターのインターネット アドレスを宛先として、応答パケットが送信されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-153">In this scenario, the Internet host 128.15.54.3 sends a response packet with the NAT router’s Internet address as its destination.</span></span>
1. <span data-ttu-id="e9c62-154">パケットが NAT ルーターに到達します。</span><span class="sxs-lookup"><span data-stu-id="e9c62-154">The packet reaches the NAT router.</span></span> <span data-ttu-id="e9c62-155">これは受信パケットであるため、受信変換規則が適用されます。宛先アドレスは、元の送信側 (クライアント) の IP アドレス 192.168.1.15 と宛先ポート番号 6732 に戻されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-155">Since this is an in-bound packet, the in-bound translation rules apply: the destination address is changed back to the original sender’s (Client’s) IP address: 192.168.1.15, destination port number 6732.</span></span>
1. <span data-ttu-id="e9c62-156">その後、パケットは、内部ネットワークに接続されているインターフェイスを介してクライアントに転送されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-156">The packet is then forwarded to the Client through the interface that is connected to the internal network.</span></span>

<span data-ttu-id="e9c62-157">この方法では、送信側のインターネット ネットワーク アドレスとポート番号は、パブリック インターネット上の他のホストに公開されません。</span><span class="sxs-lookup"><span data-stu-id="e9c62-157">In this manner the internet network address and port number of the sender is not exposed to other hosts on the public Internet.</span></span>

## <a name="netx-duo-nat-features"></a><span data-ttu-id="e9c62-158">NetX Duo NAT の機能</span><span class="sxs-lookup"><span data-stu-id="e9c62-158">NetX Duo NAT Features</span></span>

<span data-ttu-id="e9c62-159">*nx_nat_create* の呼び出しを使用して NAT インスタンスが作成されると、NAT 変換テーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-159">When the NAT instance is created using *nx_nat_create* call, the NAT translation table is created.</span></span>

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

<span data-ttu-id="e9c62-160">ローカルと外部のネットワーク間のすべてのアクティブな接続のネットワーク アドレス変換を追跡するため、NetX Duo NAT 対応ルーターによって、送信元と宛先の IP アドレスとポート番号が含まれる、各プライベート ホスト接続に関する情報についての変換テーブルが保持されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-160">To keep track of the network address translations for all active connections between local and external networks, the NetX Duo NAT-enabled router maintains a translation table with information about each private host connection which includes source and destination IP address and port number.</span></span>

<span data-ttu-id="e9c62-161">この変換テーブル ("cache") の場所は、dynamic_cache_memory ポインターを使用して設定されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-161">The location of this translation table (“cache”) is set with the dynamic_cache_memory pointer.</span></span> <span data-ttu-id="e9c62-162">この領域は、4 バイトでアラインされたバッファー領域である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9c62-162">This area must be a 4 byte aligned buffer space.</span></span> <span data-ttu-id="e9c62-163">テーブルのサイズ (つまりエントリの数) は、キャッシュ サイズ dynamic_cache_size を NAT テーブル エントリのサイズで除算することによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-163">The size of the table (or number of entries) is determined by dividing the cache size dynamic_cache_size by the size of a NAT table entry.</span></span> <span data-ttu-id="e9c62-164">テーブルは、*nx_nat.h* で定義されている **NX_NAT_MIN_ENTRY_COUNT によって指定されている最小エントリ数に対して十分な大きさである必要があります。既定値は 3 です。**</span><span class="sxs-lookup"><span data-stu-id="e9c62-164">The table must be large enough for the minimal number of entries specified by **NX_NAT_MIN_ENTRY_COUNT which is defined in *nx_nat.h*. The default value is 3.**</span></span>

<span data-ttu-id="e9c62-165">NetX Duo NAT 変換テーブル内のすべての動的エントリのタイムアウトは、*nx_nat.h* で定義されている NX_NAT_ENTRY_RESPONSE_TIMEOUT に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-165">The timeout for all dynamic entries in the NetX Duo NAT translation table are initialized to NX_NAT_ENTRY_RESPONSE_TIMEOUT which is defined in *nx_nat.h*.</span></span> <span data-ttu-id="e9c62-166">RFC 2663 で推奨されているように、既定値は 4 分 (つまり、100 mHz プロセッサで 240 システム ティック) です。</span><span class="sxs-lookup"><span data-stu-id="e9c62-166">The default value is 4 minutes (or 240 system ticks for a 100 mHz processor) as recommended by RFC 2663.</span></span> <span data-ttu-id="e9c62-167">NetX Duo NAT により、テーブル内の動的エントリと一致するパケットが受信または送信されるたびに、そのエントリのタイムアウトが NX_NAT_ENTRY_RESPONSE_TIMEOUT にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-167">Each time NetX Duo NAT receives or sends a packet matching a dynamic entry in the table it resets that entry’s time out to NX_NAT_ENTRY_RESPONSE_TIMEOUT.</span></span> <span data-ttu-id="e9c62-168">テーブルを検索するときに、NetX Duo NAT によってテーブルで期限切れのエントリもチェックされて、削除されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-168">When searching the table, NetX Duo NAT will also check the table for expired entries and delete them.</span></span>

<span data-ttu-id="e9c62-169">テーブルで受信エントリを静的として作成するには (ローカル ネットワーク上のサーバーなど)、NetX Duo NAT によって *nx_nat_inbound_entry_create* サービスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-169">To create inbound entries as static in the table e.g. for servers on the local network, NetX Duo NAT provides the *nx_nat_inbound_entry_create* service.</span></span> <span data-ttu-id="e9c62-170">テーブル エントリで静的として定義されているローカル ホスト接続には、有効期限はありません。</span><span class="sxs-lookup"><span data-stu-id="e9c62-170">If a table entry defines the local host connection as static, it never expires.</span></span>

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr,
    ULONG local_ip_address, USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

<span data-ttu-id="e9c62-171">このサービスについては、[サービスの説明に関する第 4 章](chapter4.md)で詳しく説明されています</span><span class="sxs-lookup"><span data-stu-id="e9c62-171">This service is described in more detail in [Chapter 4 - Description of Services](chapter4.md)</span></span>

<span data-ttu-id="e9c62-172">実行時に、変換テーブルに空きがなく、それ以上エントリを追加できない場合、キャッシュ フル コールバックが NAT インスタンスに登録されていると、NetX Duo NAT によりそれを通して NAT アプリケーションに通知されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-172">During runtime, if the translation table is full and no more entries can be added, NetX Duo NAT will notify the NAT application with a cache full callback if one is registered with the NAT instance.</span></span> <span data-ttu-id="e9c62-173">これは、*nx_nat_cache_notify_set* サービスを使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-173">This is done using the *nx_nat_cache_notify_set* service:</span></span>

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)(NX_NAT_DEVICE *nat_ptr));
```

<span data-ttu-id="e9c62-174">このサービスの詳細については、[サービスの説明に関する第 4 章](chapter4.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9c62-174">See [Chapter 4 - Description of Services](chapter4.md) for more details about this service.</span></span>

## <a name="nat-packet-processing-in-netx-duo"></a><span data-ttu-id="e9c62-175">NetX Duo での NAT パケットの処理</span><span class="sxs-lookup"><span data-stu-id="e9c62-175">NAT Packet Processing in NetX Duo</span></span>

<span data-ttu-id="e9c62-176">NetX Duo NAT は、IPv4 ルーターで使用することが意図されています。</span><span class="sxs-lookup"><span data-stu-id="e9c62-176">NetX Duo NAT is intended for use on an IPv4 router.</span></span> <span data-ttu-id="e9c62-177">NAT が機能するには、NAT サーバーにパケットを転送するように NetX Duo を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9c62-177">For NAT to work, NetX Duo must be configured for forwarding packets to the NAT server.</span></span> <span data-ttu-id="e9c62-178">その方法については、NetX Duo NAT のインストールに関する第 2 章を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9c62-178">See Chapter 2 on NetX Duo NAT installation for how to do so.</span></span> <span data-ttu-id="e9c62-179">その場合、NAT サーバーでは、いずれかのネットワーク上のホストに対するパケットを "使用" (転送を試行) するかどうかが示されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-179">The NAT server then indicates if it will ‘consume’ (attempt to forward) the packet to a host on either of its networks.</span></span> <span data-ttu-id="e9c62-180">パケットが使用されない場合、パケットは、通常どおり、パケットの処理のために NetX Duo に "返され" ます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-180">If it will not consume the packet, the packet is ‘returned’ to NetX Duo to process the packet as it normally would.</span></span>

<span data-ttu-id="e9c62-181">NAT サーバーは、NetX Duo から転送するパケットを受信すると、パケットが受信と送信のどちらであるかを判断します。</span><span class="sxs-lookup"><span data-stu-id="e9c62-181">When the NAT server receives a packet to forward from NetX Duo, it determines if the packet is inbound or outbound.</span></span>

<span data-ttu-id="e9c62-182">送信パケットの場合は、NAT サーバーによってパケットの IP ヘッダーの送信元アドレスとポートが確認されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-182">For outbound packets, the NAT server checks the packet IP header source address and port.</span></span> <span data-ttu-id="e9c62-183">以前にこのホストによって同じ宛先に送信されたパケットのエントリが変換テーブルに含まれていない場合は、NAT によって、その接続に対する一意のグローバル送信元 IP アドレス:ポートが含まれる新しいエントリが作成され、外部ネットワークに送信する前に、パケットのヘッダーがこの新しい IP アドレス:ポートで変更されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-183">If the translation table does not contain an entry for a packet previously sent by this host for the same destination, NAT will create a new entry which will contain a unique global source IP address:port for the connection, and modify the packet headers with this new IP address:port before sending it onto the external network.</span></span>

<span data-ttu-id="e9c62-184">受信パケットの場合は、NAT サーバーによって、パケットの宛先 IP アドレス:ポートと一致する外部 IP アドレス:ポートが含まれる以前のエントリが、変換テーブルで検索されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-184">For inbound packets, the NAT server looks for a previous entry in its translation table with an external IP address: port matching the packet destination IP address: port.</span></span> <span data-ttu-id="e9c62-185">一致するものが見つからない場合、宛先アドレス:ポートがローカル ネットワーク上のサーバーの外部アドレスでない限り、パケットは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-185">If no match is found, it will discard the packet unless the destination address: port is the external address for server on the local network.</span></span> <span data-ttu-id="e9c62-186">一致するものが見つかった場合は、パケット ヘッダーの外部宛先 IP アドレス:ポートがプライベート IP アドレス:ポートに置き換えられて、パケットはローカル ネットワーク上の目的のプライベート ホストに送信されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-186">If it does find a match, it will replace the packet header’s external destination IP address: port with the private IP address: port and send the packet onto the local network to the intended private host.</span></span>

<span data-ttu-id="e9c62-187">外部ホストと接続するローカル ホスト用の一意のローカル アドレス:ポート接続を作成するため、NetX Duo NAT により、TCP、UDP、ICMP の変換ポートの範囲が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-187">NetX Duo NAT uses a range of TCP, UDP and ICMP translation ports for creating unique local address: port connections for local hosts connecting with outside hosts.</span></span> <span data-ttu-id="e9c62-188">*nx_nat.h* で定義されている次のユーザー構成可能なオプションにより、各プロトコルの範囲が定義されます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-188">The following user configurable options, defined in *nx_nat.h,* define the range for each protocol:</span></span>

```C
NX_NAT_START_TCP_PORT

NX_NAT_END_TCP_PORT

NX_NAT_START_UDP_PORT

NX_NAT_END_UDP_PORT

NX_NAT_START_ICMP_QUERY_ID

NX_NAT_END_ICMP_QUERY_ID
```

## <a name="nat-requirements-and-constraints"></a><span data-ttu-id="e9c62-189">NAT の要件と制約</span><span class="sxs-lookup"><span data-stu-id="e9c62-189">NAT Requirements and Constraints</span></span>

<span data-ttu-id="e9c62-190">NetX Duo NAT には、NetX Duo 5.8 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="e9c62-190">NetX Duo NAT requires NetX Duo 5.8 or later.</span></span> <span data-ttu-id="e9c62-191">単一の IP インスタンスと、内部および外部の物理ネットワークへのインターフェイスを、NAT アプリケーションで作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9c62-191">The NAT application requires creation of a single IP instance and an interface to the internal and external physical network.</span></span>

<span data-ttu-id="e9c62-192">制約:</span><span class="sxs-lookup"><span data-stu-id="e9c62-192">Constraints:</span></span>

- <span data-ttu-id="e9c62-193">NetX Duo NAT では、TCP、UDP、ICMP がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e9c62-193">NetX Duo NAT supports TCP, UDP and ICMP.</span></span> <span data-ttu-id="e9c62-194">IGMP はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e9c62-194">IGMP is not supported.</span></span>
- <span data-ttu-id="e9c62-195">NetX Duo NAT は、IPv6 のアドレス指定に対応していません。</span><span class="sxs-lookup"><span data-stu-id="e9c62-195">NetX Duo NAT does not support IPv6 addressing.</span></span>
- <span data-ttu-id="e9c62-196">NetX Duo NAT には DNS または DHCP サービスは含まれませんが、NetX Duo NAT は NAT 操作でこれらのサービスと統合できます。</span><span class="sxs-lookup"><span data-stu-id="e9c62-196">NetX Duo NAT does not include DNS or DHCP services, although NetX Duo NAT can integrate those services with its NAT operations.</span></span>

## <a name="rfcs-supported-by-netx-duo-nat"></a><span data-ttu-id="e9c62-197">NetX Duo NAT によってサポートされている RFC</span><span class="sxs-lookup"><span data-stu-id="e9c62-197">RFCs Supported by NetX Duo NAT</span></span>

<span data-ttu-id="e9c62-198">NetX Duo NAT の実装は、次の RFC に記載されている情報に基づいています。</span><span class="sxs-lookup"><span data-stu-id="e9c62-198">NetX Duo NAT implementation is based on information presented in the following RFCs:</span></span>

- <span data-ttu-id="e9c62-199">RFC 2663: IP ネットワーク アドレス トランスレーター (NAT) の用語と考慮事項</span><span class="sxs-lookup"><span data-stu-id="e9c62-199">RFC 2663: IP Network Address Translator (NAT) Terminology and Considerations</span></span>
- <span data-ttu-id="e9c62-200">RFC 3022: 従来の IP ネットワーク アドレス トランスレーター (従来の NAT)</span><span class="sxs-lookup"><span data-stu-id="e9c62-200">RFC 3022: Traditional IP Netowrk Address Translator (Traditional NAT)</span></span>
- <span data-ttu-id="e9c62-201">RFC 4787: ユニキャスト UDP に関するネットワークアドレス変換 (NAT) の動作の要件</span><span class="sxs-lookup"><span data-stu-id="e9c62-201">RFC 4787: Network Address Translation (NAT) Behavioral Requirements for Unicast UDP</span></span>
