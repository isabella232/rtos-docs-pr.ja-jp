---
title: Azure RTOS NetX を理解する
description: Azure RTOS NetX は、TCP/IP プロトコル標準のハイパフォーマンス実装です。Azure RTOS ThreadX と完全に統合されており、サポートされるすべてのプロセッサで利用できます。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 029f73b755d5c40279125fb010ec35baaaf7f38d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810400"
---
# <a name="overview-of-azure-rtos-netx"></a><span data-ttu-id="92317-103">Azure RTOS NetX の概要</span><span class="sxs-lookup"><span data-stu-id="92317-103">Overview of Azure RTOS NetX</span></span>

<span data-ttu-id="92317-104">Azure RTOS NetX は、深く組み込まれたリアルタイム IoT アプリケーション専用に設計された、産業用 TCP/IP IPv4 組み込みネットワーク スタックです。</span><span class="sxs-lookup"><span data-stu-id="92317-104">Azure RTOS NetX is an industrial grade TCP/IP IPv4 embedded network stack, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="92317-105">Azure RTOS NetX は、Microsoft 独自の IPv4 ネットワーク スタックであり、本質的に Azure RTOS のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="92317-105">Azure RTOS NetX is Microsoft's original IPv4 network stack, and is essentially a subset of Azure RTOS.</span></span> <span data-ttu-id="92317-106">NetX は、IPv4、TCP、UDP などのコア ネットワーク プロトコルと、その他の高度なアドオン プロトコルの完全なスイートを組み込みアプリケーションに提供します。</span><span class="sxs-lookup"><span data-stu-id="92317-106">NetX provides embedded applications with core network protocols such as IPv4, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="92317-107">小さなフットプリント、高速実行、優れた操作性により、Azure RTOS NetX は、最も要求の厳しい組み込み IoT アプリケーションに最適な選択肢となっています。</span><span class="sxs-lookup"><span data-stu-id="92317-107">A small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX an ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="92317-108">API のプロトコル</span><span class="sxs-lookup"><span data-stu-id="92317-108">API protocols</span></span>

### <a name="telnet"></a><span data-ttu-id="92317-109">Telnet</span><span class="sxs-lookup"><span data-stu-id="92317-109">TELNET</span></span>

* <span data-ttu-id="92317-110">最小 0.5 KB と 0.3 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="92317-110">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="92317-111">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="92317-111">Client and server support</span></span>
* <span data-ttu-id="92317-112">直感的な Telnet API: *nx_telnet_\**</span><span class="sxs-lookup"><span data-stu-id="92317-112">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="auto-ip"></a><span data-ttu-id="92317-113">Auto IP</span><span class="sxs-lookup"><span data-stu-id="92317-113">Auto IP</span></span>

* <span data-ttu-id="92317-114">IPv4 アドレス自動割り当て</span><span class="sxs-lookup"><span data-stu-id="92317-114">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="92317-115">最小 1.2 KB、300 バイトの RAM</span><span class="sxs-lookup"><span data-stu-id="92317-115">Minimal 1.2 KB, 300 bytes of RAM</span></span>
* <span data-ttu-id="92317-116">直感的な AutoIP API: *nx_autoip_\**</span><span class="sxs-lookup"><span data-stu-id="92317-116">Intuitive AutoIP APIs: *nx_autoip_\**</span></span>

### <a name="http---hypertext-transfer-protocolhttp"></a><span data-ttu-id="92317-117">HTTP - ハイパーテキスト転送プロトコル (HTTP)</span><span class="sxs-lookup"><span data-stu-id="92317-117">HTTP - Hypertext Transfer Protocol(HTTP)</span></span>

* <span data-ttu-id="92317-118">最小 2.8 KB から 4.8 KB のフラッシュ、0.4 KB から 1.0 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="92317-118">Minimal 2.8 KB to 4.8KBFLASH, 0.4 KB to 1.0 KB RAM footprint</span></span>
* <span data-ttu-id="92317-119">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="92317-119">Client and server support</span></span>
* <span data-ttu-id="92317-120">直感的な HTTP API: *nx_http_\**</span><span class="sxs-lookup"><span data-stu-id="92317-120">Intuitive HTTP APIs: *nx_http_\**</span></span>

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a><span data-ttu-id="92317-121">SMTP - 簡易メール転送プロトコル (SMTP)</span><span class="sxs-lookup"><span data-stu-id="92317-121">SMTP - Simple Mail Transfer Protocol (SMTP)</span></span>

* <span data-ttu-id="92317-122">最小 4.1 KB と 0.6 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="92317-122">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="92317-123">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="92317-123">Client support</span></span>
* <span data-ttu-id="92317-124">直感的な SMTP API: *nx_smtp_\**</span><span class="sxs-lookup"><span data-stu-id="92317-124">Intuitive SMTP APIs: *nx_smtp_\**</span></span>

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a><span data-ttu-id="92317-125">DHCP - 動的ホスト構成プロトコル (DHCP)</span><span class="sxs-lookup"><span data-stu-id="92317-125">DHCP - Dynamic Host Configuration Protocol (DHCP)</span></span>

* <span data-ttu-id="92317-126">最小 3.6 KB から 4.6 KB のフラッシュ、2.7 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="92317-126">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="92317-127">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="92317-127">Client and server support</span></span>
* <span data-ttu-id="92317-128">IPv4 のサポート</span><span class="sxs-lookup"><span data-stu-id="92317-128">IPv4 support</span></span>
* <span data-ttu-id="92317-129">直感的な DHCP API: *nx_dhcp_\**</span><span class="sxs-lookup"><span data-stu-id="92317-129">Intuitive DHCP APIs: *nx_dhcp_\**</span></span>

### <a name="p0p3---post-office-protocol-version-3-pop3"></a><span data-ttu-id="92317-130">P0P3 - Post Office Protocol Version 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="92317-130">P0P3 - Post Office Protocol Version 3 (POP3)</span></span>

* <span data-ttu-id="92317-131">最小 8.1 KB と 1.4 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="92317-131">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="92317-132">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="92317-132">Client support</span></span>
* <span data-ttu-id="92317-133">直感的な POP3 API: *nx_pop3_\**</span><span class="sxs-lookup"><span data-stu-id="92317-133">Intuitive P0P3 APIs: *nx_pop3_\**</span></span>

### <a name="snmp---simple-network-management-protocol-snmp"></a><span data-ttu-id="92317-134">SNMP - 簡易ネットワーク管理プロトコル (SNMP)</span><span class="sxs-lookup"><span data-stu-id="92317-134">SNMP - Simple Network Management Protocol (SNMP)</span></span>

* <span data-ttu-id="92317-135">最小 10.9 KB と 2.6 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="92317-135">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="92317-136">VI、V2、V3 のエージェントのサポート</span><span class="sxs-lookup"><span data-stu-id="92317-136">Agent support for VI, V2, and V3</span></span>
* <span data-ttu-id="92317-137">直感的な SNMP API: *nx_snmp_\**</span><span class="sxs-lookup"><span data-stu-id="92317-137">Intuitive SNMP APIs: *nx_snmp_\**</span></span>

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a><span data-ttu-id="92317-138">FTP、TFTP - ファイル転送プロトコル (FTP)、簡易ファイル転送プロトコル (TFTP)</span><span class="sxs-lookup"><span data-stu-id="92317-138">FTP, TFTP - File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span></span>

* <span data-ttu-id="92317-139">FTP - 最小 1.8 KB から 7.2 KB のフラッシュ、0.6 KB から 2.1 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="92317-139">FTP Minimal 1.8 KB to 7.2KBFLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="92317-140">TFTP - 最小 1.7 KB から 2.4 KB のフラッシュ、0.3 KB から 1.8 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="92317-140">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="92317-141">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="92317-141">Client and server support</span></span>
* <span data-ttu-id="92317-142">直感的な FTP および TFTP API: <i>nx_ftp_ *</i> または <i>nx_tftp_* </i></span><span class="sxs-lookup"><span data-stu-id="92317-142">Intuitive FTP and TFTP APIs: <i>nx_ftp_ *</i> or <i>nx_tftp_*</i></span></span>

### <a name="ppp---polnt-to-point-protocol-ppp"></a><span data-ttu-id="92317-143">PPP - Point-to-Point プロトコル (PPP)</span><span class="sxs-lookup"><span data-stu-id="92317-143">PPP - Polnt-to-PoInt Protocol (PPP)</span></span>

* <span data-ttu-id="92317-144">最小 7.1 KB と 3.8 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="92317-144">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="92317-145">直感的な PPP API: *nx_ppp_\**</span><span class="sxs-lookup"><span data-stu-id="92317-145">Intuitive PPP APIs: *nx_ppp_\**</span></span>

### <a name="sntp---simple-network-time-protocol-sntp"></a><span data-ttu-id="92317-146">SNTP - Simple Network Time Protocol (SNTP)</span><span class="sxs-lookup"><span data-stu-id="92317-146">SNTP - Simple Network Time Protocol (SNTP)</span></span>

* <span data-ttu-id="92317-147">最小 4 KB および 0.5 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="92317-147">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="92317-148">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="92317-148">Client support</span></span>
* <span data-ttu-id="92317-149">直感的な SNTP API: *nx_sntp_\**</span><span class="sxs-lookup"><span data-stu-id="92317-149">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-api"></a><span data-ttu-id="92317-150">Azure RTOS NetX API</span><span class="sxs-lookup"><span data-stu-id="92317-150">Azure RTOS NetX API</span></span>

* <span data-ttu-id="92317-151">直感的で一貫性のある API</span><span class="sxs-lookup"><span data-stu-id="92317-151">Intuitive and consistent API</span></span>
* <span data-ttu-id="92317-152">名詞 - 動詞の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="92317-152">Noun-verb naming convention</span></span>
* <span data-ttu-id="92317-153">高速のゼロコピー API 実装</span><span class="sxs-lookup"><span data-stu-id="92317-153">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="92317-154">Azure RTOS NetX として簡単に識別できるように、すべての API 関数の先頭を <i>nx_\*</i> で統一</span><span class="sxs-lookup"><span data-stu-id="92317-154">All API functions have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="92317-155">ブロッキング API 関数に用意されたオプションのスレッド タイムアウト</span><span class="sxs-lookup"><span data-stu-id="92317-155">Blocking API functions have an optional thread timeout</span></span>
* <span data-ttu-id="92317-156">レガシ ソケット コードを移植するためのオプションの BSD レイヤー</span><span class="sxs-lookup"><span data-stu-id="92317-156">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp---internet-group-management-protocol-igmp"></a><span data-ttu-id="92317-157">IGMP - インターネット グループ管理プロトコル (IGMP)</span><span class="sxs-lookup"><span data-stu-id="92317-157">IGMP - Internet Group Management Protocol (IGMP)</span></span>

* <span data-ttu-id="92317-158">最小 2.5 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="92317-158">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="92317-159">IPv4 マルチキャスト グループのサポート</span><span class="sxs-lookup"><span data-stu-id="92317-159">IPv4 multicast group support</span></span>
* <span data-ttu-id="92317-160">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="92317-160">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="92317-161">オプションの IGMP 統計情報</span><span class="sxs-lookup"><span data-stu-id="92317-161">Optional IGMP statistics</span></span>
* <span data-ttu-id="92317-162">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="92317-162">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="92317-163">直感的な IGMP API: *nx_igmp_\**</span><span class="sxs-lookup"><span data-stu-id="92317-163">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="udp---user-datagram-protocol-udp"></a><span data-ttu-id="92317-164">UDP - ユーザー データグラム プロトコル (UDP)</span><span class="sxs-lookup"><span data-stu-id="92317-164">UDP - User Datagram Protocol (UDP)</span></span>

* <span data-ttu-id="92317-165">最小 2.5 KB のフラッシュ、ソケットあたり 124 ソケット バイトの RAM</span><span class="sxs-lookup"><span data-stu-id="92317-165">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="92317-166">高速でほぼワイヤスピードの TCP パケット処理:</span><span class="sxs-lookup"><span data-stu-id="92317-166">Fast, near wirespeed TCP packet processing:</span></span>
* <span data-ttu-id="92317-167">RX 95 Mbps (100 Mbps イーサネット)、MCU @100MHz、14% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="92317-167">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU Utilization</span></span>
* <span data-ttu-id="92317-168">TX 94 Mbps (100 Mbps イーサネット)、MCU @100MHz、10% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="92317-168">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU Utilization</span></span>
* <span data-ttu-id="92317-169">UDP Fast Path™ テクノロジ</span><span class="sxs-lookup"><span data-stu-id="92317-169">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="92317-170">UDP の数に制限なし</span><span class="sxs-lookup"><span data-stu-id="92317-170">No limits on the number of UDP</span></span>
* <span data-ttu-id="92317-171">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="92317-171">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="92317-172">ソケット受信時のオプションの中断</span><span class="sxs-lookup"><span data-stu-id="92317-172">Optional suspension on socket receive</span></span>
* <span data-ttu-id="92317-173">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="92317-173">Optional timeout on all suspension</span></span>
* <span data-ttu-id="92317-174">オプションの UDP 統計情報</span><span class="sxs-lookup"><span data-stu-id="92317-174">Optional UDP statistics</span></span>
* <span data-ttu-id="92317-175">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="92317-175">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="92317-176">直感的な UDP API: *nx_udp_\**</span><span class="sxs-lookup"><span data-stu-id="92317-176">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp---transmission-control-protocol-tcp"></a><span data-ttu-id="92317-177">TCP - 伝送制御プロトコル (TCP)</span><span class="sxs-lookup"><span data-stu-id="92317-177">TCP - Transmission Control Protocol (TCP)</span></span>

* <span data-ttu-id="92317-178">最小 10.5 KB から 12.5 KB のフラッシュ、ソケットあたり 280 バイトの RAM</span><span class="sxs-lookup"><span data-stu-id="92317-178">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="92317-179">高速でほぼワイヤスピードの TCP パケット処理:</span><span class="sxs-lookup"><span data-stu-id="92317-179">Fast, near wlrespeed TCP packet processing:</span></span>
* <span data-ttu-id="92317-180">RX 93 Mbps (100 Mbps イーサネット)、MCU @100MHz、20% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="92317-180">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU Utilization</span></span>
* <span data-ttu-id="92317-181">TX 94 Mbps (100 Mbps イーサネット)、MCU @100MHz、27% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="92317-181">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU Utilization</span></span>
* <span data-ttu-id="92317-182">信頼性の高い接続</span><span class="sxs-lookup"><span data-stu-id="92317-182">Reliable connection</span></span>
* <span data-ttu-id="92317-183">TCP ソケット数に制限なし</span><span class="sxs-lookup"><span data-stu-id="92317-183">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="92317-184">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="92317-184">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="92317-185">ソケット受信/送信時のオプションの中断</span><span class="sxs-lookup"><span data-stu-id="92317-185">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="92317-186">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="92317-186">Optional timeout on all suspension</span></span>
* <span data-ttu-id="92317-187">オプションの TCP 統計情報</span><span class="sxs-lookup"><span data-stu-id="92317-187">Optional TCP statistics</span></span>
* <span data-ttu-id="92317-188">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="92317-188">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="92317-189">直感的な TCP API: *nx_tcp_\**</span><span class="sxs-lookup"><span data-stu-id="92317-189">Intuitive TCP APIs:  *nx_tcp_\**</span></span>

### <a name="icmp---internet-control-message-protocol-icmp"></a><span data-ttu-id="92317-190">ICMP - インターネット制御メッセージ プロトコル (ICMP)</span><span class="sxs-lookup"><span data-stu-id="92317-190">ICMP - Internet Control Message Protocol (ICMP)</span></span>

* <span data-ttu-id="92317-191">最小 2.5 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="92317-191">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="92317-192">IPv4 のサポート</span><span class="sxs-lookup"><span data-stu-id="92317-192">IPv4 support</span></span>
* <span data-ttu-id="92317-193">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="92317-193">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="92317-194">ping 要求と ping 応答</span><span class="sxs-lookup"><span data-stu-id="92317-194">Ping request and ping response</span></span>
* <span data-ttu-id="92317-195">ping 要求時のオプションのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="92317-195">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="92317-196">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="92317-196">Optional timeout on all suspension</span></span>
* <span data-ttu-id="92317-197">オプションの ICMP 統計情報</span><span class="sxs-lookup"><span data-stu-id="92317-197">Optional ICMP statistics</span></span>
* <span data-ttu-id="92317-198">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="92317-198">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="92317-199">直感的な ICMP API: *nx_icmp_\**</span><span class="sxs-lookup"><span data-stu-id="92317-199">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="ipv4---internet-protocol-ip"></a><span data-ttu-id="92317-200">IPv4 - インターネット プロトコル (IP)</span><span class="sxs-lookup"><span data-stu-id="92317-200">IPv4 - Internet Protocol (IP)</span></span>

* <span data-ttu-id="92317-201">最小 3.5 KB から 8.5 KB のフラッシュ、2 KB から 3 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="92317-201">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="92317-202">Piconet™ アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="92317-202">Piconet™ Architecture</span></span>
* <span data-ttu-id="92317-203">高速でほぼワイヤスピードのパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="92317-203">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="92317-204">複数インターフェイスのサポート</span><span class="sxs-lookup"><span data-stu-id="92317-204">Multiple interface support</span></span>
* <span data-ttu-id="92317-205">マルチホーム サポート</span><span class="sxs-lookup"><span data-stu-id="92317-205">Multihomed support</span></span>
* <span data-ttu-id="92317-206">静的ルーティングのサポート</span><span class="sxs-lookup"><span data-stu-id="92317-206">Static routing support</span></span>
* <span data-ttu-id="92317-207">IP の断片化/再構築のサポート</span><span class="sxs-lookup"><span data-stu-id="92317-207">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="92317-208">IPv4 のサポート</span><span class="sxs-lookup"><span data-stu-id="92317-208">IPv4 Support</span></span>
* <span data-ttu-id="92317-209">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="92317-209">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="92317-210">フェーズ II 対応ロゴ認定</span><span class="sxs-lookup"><span data-stu-id="92317-210">Phase II Ready Logo Certification</span></span>
* <span data-ttu-id="92317-211">オプションの IP 統計情報</span><span class="sxs-lookup"><span data-stu-id="92317-211">Optional IP statistics</span></span>
* <span data-ttu-id="92317-212">明確に定義された直感的な物理層ドライバー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="92317-212">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="92317-213">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="92317-213">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="92317-214">直感的な IP レイヤー API: *nx_ip_\** 、*nxd_ip_\**</span><span class="sxs-lookup"><span data-stu-id="92317-214">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**</span></span>
* <span data-ttu-id="92317-215">TUV および UL による IEC 61508 SIL 4、IEC 62304 クラス C、ISO 26262 ASIL D、および EN 50128 SW-SIL4 に対する事前認定</span><span class="sxs-lookup"><span data-stu-id="92317-215">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a><span data-ttu-id="92317-216">ARP/RARP - アドレス解決プロトコル (ARP)、逆アドレス解決プロトコル (RARP)</span><span class="sxs-lookup"><span data-stu-id="92317-216">ARP/RARP - Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span></span>

* <span data-ttu-id="92317-217">最小 1.7 KB のフラッシュ、RAM サイズ</span><span class="sxs-lookup"><span data-stu-id="92317-217">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="92317-218">32 ビット IPv4 と 48 ビット MAC アドレスの動的な解決</span><span class="sxs-lookup"><span data-stu-id="92317-218">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="92317-219">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="92317-219">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="92317-220">柔軟なユーザー定義の ARP キャッシュ</span><span class="sxs-lookup"><span data-stu-id="92317-220">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="92317-221">Gratuitous ARP のサポート</span><span class="sxs-lookup"><span data-stu-id="92317-221">Gratuitous ARP support</span></span>
* <span data-ttu-id="92317-222">アプリケーションによって決定されるオプションの ARP/RARP 統計情報</span><span class="sxs-lookup"><span data-stu-id="92317-222">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="92317-223">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="92317-223">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="92317-224">直感的な ARP/RARP API: *nx_arp_\** 、*nx_rarp_\**</span><span class="sxs-lookup"><span data-stu-id="92317-224">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a><span data-ttu-id="92317-225">イーサネット、WiFi、Bluetooth LE、15.4 など</span><span class="sxs-lookup"><span data-stu-id="92317-225">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span></span>

## <a name="small-footprint"></a><span data-ttu-id="92317-226">小さなフットプリント</span><span class="sxs-lookup"><span data-stu-id="92317-226">Small-footprint</span></span>

<span data-ttu-id="92317-227">Azure RTOS NetX では、基本的な IP および UDP のサポートに、9 KB から 15 KB の非常に小さなフットプリントが実現されています。</span><span class="sxs-lookup"><span data-stu-id="92317-227">Azure RTOS NetX has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="92317-228">TCP 機能を使用するには、追加で 10 KB から 13 KB の命令領域メモリが必要です。</span><span class="sxs-lookup"><span data-stu-id="92317-228">An additional 10 KB to 13 KB of instruction area memory is needed for TCP functionality.</span></span> <span data-ttu-id="92317-229">Azure RTOS NetX の RAM 使用量は、通常、2.6 KB から 3.6 KB に、アプリケーションによって定義されるパケット プール メモリを加えた量になります。</span><span class="sxs-lookup"><span data-stu-id="92317-229">Azure RTOS NetX RAM usage typically ranges from 2.6 KB to 3.6 KB plus the packet pool memory, which is defined by the application.</span></span> <span data-ttu-id="92317-230">Azure RTOS ThreadX と同様に、Azure RTOS NetX のサイズは、アプリケーションで使用されるサービスに基づいて自動的にスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="92317-230">Like Azure RTOS ThreadX, the size of Azure RTOS NetX automatically scales based on the services used by the application.</span></span> <span data-ttu-id="92317-231">これにより、複雑な構成やビルド パラメーターが実質的に不要になるため、開発者の作業がより簡単になります。</span><span class="sxs-lookup"><span data-stu-id="92317-231">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="92317-232">高速実行</span><span class="sxs-lookup"><span data-stu-id="92317-232">Fast execution</span></span>

<span data-ttu-id="92317-233">Azure RTOS NetX は、ゼロコピーのパケット送信/受信実装を提供します。また、Azure RTOS ThreadX と高度に統合されており、可能な限り最速のパフォーマンスを実現します。</span><span class="sxs-lookup"><span data-stu-id="92317-233">Azure RTOS NetX provides a zero-copy packet send/receive implementation and is highly integrated with Azure RTOS ThreadX to achieve the fastest possible performance.</span></span> <span data-ttu-id="92317-234">たとえば、Azure RTOS NetX では通常、プロセッサ サイクルのごく一部のみを使用しながら、80 MHz (またはそれ以下の) プロセッサでほぼワイヤスピードのデータ転送を実現します。</span><span class="sxs-lookup"><span data-stu-id="92317-234">For example, Azure RTOS NetX can typically achieve near wirespeed data transfers on an 80-MHz processor (or less), while using only a small percentage of the processor cycles.</span></span>

## <a name="simple-easy-to-use"></a><span data-ttu-id="92317-235">シンプルで優れた操作性</span><span class="sxs-lookup"><span data-stu-id="92317-235">Simple, easy-to-use</span></span>

<span data-ttu-id="92317-236">Azure RTOS NetX は簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="92317-236">Azure RTOS NetX is simple to use.</span></span> <span data-ttu-id="92317-237">Azure RTOS NetX API は直感的かつ高機能です。</span><span class="sxs-lookup"><span data-stu-id="92317-237">The Azure RTOS NetX API is both intuitive and highly functional.</span></span> <span data-ttu-id="92317-238">API 名は、他のネットワーク製品でよく見られる略語や大幅に省略された名前ではなく、実際の単語で構成されています。</span><span class="sxs-lookup"><span data-stu-id="92317-238">The API names are made of real words and not “alphabet soup” or highly abbreviated names that are so common in other networking products.</span></span> <span data-ttu-id="92317-239">すべての Azure RTOS NetX API は、先頭に *nx_* が付き、名詞 - 動詞の名前付け規則に従っています。</span><span class="sxs-lookup"><span data-stu-id="92317-239">All Azure RTOS NetX APIs have a leading *nx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="92317-240">さらに、API 全体で機能に一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="92317-240">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="92317-241">たとえば、中断を実行するすべての API 関数には、同様に機能するオプションのタイムアウトがあります。</span><span class="sxs-lookup"><span data-stu-id="92317-241">For example, all API functions that suspend have an optional timeout that functions in an identical manner.</span></span> <span data-ttu-id="92317-242">レガシ アプリケーションに対しては、Azure RTOS NetX で追加の BSD ソケット互換レイヤーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="92317-242">For legacy applications, Azure RTOS NetX offers an additional BSD socket compatible layer.</span></span> <span data-ttu-id="92317-243">このレイヤーは、開発者が大規模なネットワーク アプリケーションを簡単に移行するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="92317-243">This layer helps developers migrate large networking applications with ease.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="92317-244">相互運用性の検証</span><span class="sxs-lookup"><span data-stu-id="92317-244">Interoperability verification</span></span>

<span data-ttu-id="92317-245">Azure RTOS NetX は RFC 標準に準拠しており、ほとんどのベンダーのデバイスとの完全な相互運用性を提供します。</span><span class="sxs-lookup"><span data-stu-id="92317-245">Azure RTOS NetX conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span> <span data-ttu-id="92317-246">Azure RTOS NetX では、Azure RTOS NetX コア TCP/IP プロトコル実装に業界標準の IxANVL (自動ネットワーク検証ライブラリ) も利用しています。</span><span class="sxs-lookup"><span data-stu-id="92317-246">Azure RTOS NetX also utilizes the industry standard IxANVL (Automated Network Validation Library) for the Azure RTOS NetX core TCP/IP protocol implementation.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="92317-247">高度なテクノロジ</span><span class="sxs-lookup"><span data-stu-id="92317-247">Advanced technology</span></span>

<span data-ttu-id="92317-248">Azure RTOS NetX は、次の機能を備えた高度なテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="92317-248">Azure RTOS NetX is advanced technology that includes:</span></span>

* <span data-ttu-id="92317-249">Piconet™ アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="92317-249">Piconet™ architecture</span></span>
* <span data-ttu-id="92317-250">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="92317-250">automatic scaling</span></span>
* <span data-ttu-id="92317-251">UDP Fast-Path™ テクノロジ</span><span class="sxs-lookup"><span data-stu-id="92317-251">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="92317-252">柔軟なパケット管理</span><span class="sxs-lookup"><span data-stu-id="92317-252">flexible packet management</span></span>
* <span data-ttu-id="92317-253">ゼロコピー API と実装</span><span class="sxs-lookup"><span data-stu-id="92317-253">zero-copy API and implementation</span></span>
* <span data-ttu-id="92317-254">マルチホーム サポート</span><span class="sxs-lookup"><span data-stu-id="92317-254">multihomed support</span></span>
* <span data-ttu-id="92317-255">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="92317-255">optional timeout on all suspension</span></span>
* <span data-ttu-id="92317-256">静的ルーティングのサポート</span><span class="sxs-lookup"><span data-stu-id="92317-256">static routing support</span></span>
* <span data-ttu-id="92317-257">Azure RTOS TraceX システム分析のサポート</span><span class="sxs-lookup"><span data-stu-id="92317-257">Azure RTOS TraceX system analysis support</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="92317-258">市場投入までの時間を最短化</span><span class="sxs-lookup"><span data-stu-id="92317-258">Fastest time-to-market</span></span>

<span data-ttu-id="92317-259">Azure RTOS NetX は、インストール、習得、使用、デバッグ、検証、認定、保守が簡単です。</span><span class="sxs-lookup"><span data-stu-id="92317-259">Azure RTOS NetX is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="92317-260">その結果、Azure RTOS NetX は、Broadcom や Gainspan などが提供する多くの SoC を含む、組み込み型 IoT デバイス向けの最も一般的な TCP/IP スタックの 1 つとなっています。</span><span class="sxs-lookup"><span data-stu-id="92317-260">As a result, Azure RTOS NetX is one of the most popular TCP/IP stacks for embedded IoT devices, including many SoCs from Broadcom, Gainspan, and so forth.</span></span> <span data-ttu-id="92317-261">一貫した市場投入までの時間の優位性は、次の要素を基に構築されています。</span><span class="sxs-lookup"><span data-stu-id="92317-261">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="92317-262">質の高いドキュメント - [Azure RTOS NetX ユーザー ガイド](about-this-guide.md)を参照し、ご自身の目でお確かめください</span><span class="sxs-lookup"><span data-stu-id="92317-262">quality documentation – please review our [Azure RTOS NetX User Guide](about-this-guide.md) and see for yourself!</span></span>
* <span data-ttu-id="92317-263">完全なソース コードを提供</span><span class="sxs-lookup"><span data-stu-id="92317-263">complete source code availability</span></span>
* <span data-ttu-id="92317-264">使いやすい API</span><span class="sxs-lookup"><span data-stu-id="92317-264">easy-to-use API</span></span>
* <span data-ttu-id="92317-265">包括的で高度な機能セット</span><span class="sxs-lookup"><span data-stu-id="92317-265">comprehensive and advanced feature set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="92317-266">シンプルな 1 つのライセンス</span><span class="sxs-lookup"><span data-stu-id="92317-266">One Simple License</span></span>

<span data-ttu-id="92317-267">ソース コードの使用とテストにコストはかかりません。事前にライセンスされたデバイスにデプロイする場合は、運用環境ライセンスのコストはかかりません。他のすべてのデバイスには、シンプルな年間ライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="92317-267">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="92317-268">最高品質の完全なソース コード</span><span class="sxs-lookup"><span data-stu-id="92317-268">Full, highest-quality source code</span></span>

<span data-ttu-id="92317-269">長年にわたり、Azure RTOS NetX のソース コードは、品質とわかりやすさに一定の基準を設けてきました。</span><span class="sxs-lookup"><span data-stu-id="92317-269">Throughout the years, Azure RTOS NetX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="92317-270">また、ファイルごとに 1 つの関数を使用するという規則により、簡単なソース ナビゲーションが実現されます。</span><span class="sxs-lookup"><span data-stu-id="92317-270">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="92317-271">最も一般的なアーキテクチャをサポート</span><span class="sxs-lookup"><span data-stu-id="92317-271">Supports most popular architectures</span></span>

<span data-ttu-id="92317-272">Azure RTOS NetX は、完全にテストされ、サポートされている、すぐに使える最も一般的な 32 および 64 ビット マイクロプロセッサで動作します。これには、次の高度なアーキテクチャが含まれます。</span><span class="sxs-lookup"><span data-stu-id="92317-272">Azure RTOS NetX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following advanced architectures:</span></span>

<span data-ttu-id="92317-273">**Analog Devices**: SHARC、Blackfin、CM4xx</span><span class="sxs-lookup"><span data-stu-id="92317-273">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="92317-274">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="92317-274">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="92317-275">**Ambiqmicro**: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="92317-275">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="92317-276">**ARM**: ARM7、ARM9、ARM11、Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64 ビット/A7x 64 ビット/R4/R5、TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="92317-276">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="92317-277">**Cadence**: Xtensa、Diamond</span><span class="sxs-lookup"><span data-stu-id="92317-277">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="92317-278">**CEVA**: PSoC、PSoC 4、PSoC 5、PSoC 6、FM0+、FM3、MF4、WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="92317-278">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="92317-279">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="92317-279">**Cypress**: RISC-V</span></span>

<span data-ttu-id="92317-280">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="92317-280">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="92317-281">**Infineon**: XMC1000、XMC4000、TriCore</span><span class="sxs-lookup"><span data-stu-id="92317-281">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="92317-282">**Intel および Intel FPGA**: x36/Pentium、XScale、NIOS II、Cyclone、Arria 10</span><span class="sxs-lookup"><span data-stu-id="92317-282">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="92317-283">**Microchip**: AVR32、ARM7、ARM9、Cortex-M3/M4/M7、SAM3/4/7/9/A/C/D/E/G/L/SV、PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="92317-283">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="92317-284">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="92317-284">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="92317-285">**NXP**: LPC、ARM7、ARM9、PowerPC、68 K、i.MX、ColdFire、Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="92317-285">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="92317-286">**Renesas**: SH、HS、V850、RX、RZ、Synergy</span><span class="sxs-lookup"><span data-stu-id="92317-286">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="92317-287">**Silicon Labs**: EFM32</span><span class="sxs-lookup"><span data-stu-id="92317-287">**Silicon Labs**: EFM32</span></span>

<span data-ttu-id="92317-288">**Synopsys**: ARC 600、700、ARC EM、ARC HS</span><span class="sxs-lookup"><span data-stu-id="92317-288">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="92317-289">**ST**: STM32、ARM7、ARM9、Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="92317-289">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="92317-290">**Tl**: C5xxx、C6xxx、Stellaris、Sitara、Tiva-C</span><span class="sxs-lookup"><span data-stu-id="92317-290">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="92317-291">**Wave Computing**: MIPS32 4K、24 K、34 K、1004 K、MIPS64 5K、microAptiv、interAptiv、proAptiv、M-Class</span><span class="sxs-lookup"><span data-stu-id="92317-291">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="92317-292">**Xilinx**: MicroBlaze、PowerPC 405、ZYNQ、ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="92317-292">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="92317-293">*記載されているタイミングとサイズの数値はすべて推定値であり、開発プラットフォームによって異なる場合があります。*</span><span class="sxs-lookup"><span data-stu-id="92317-293">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>
