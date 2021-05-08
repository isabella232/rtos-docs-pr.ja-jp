---
title: Azure RTOS NetX を理解する
description: Azure RTOS NetX は、TCP/IP プロトコル標準のハイパフォーマンス実装です。Azure RTOS ThreadX と完全に統合されており、サポートされるすべてのプロセッサで利用できます。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 7c864c23f019e4841ddb3096fde663c8039baf44
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171320"
---
# <a name="overview-of-azure-rtos-netx"></a><span data-ttu-id="89cb3-103">Azure RTOS NetX の概要</span><span class="sxs-lookup"><span data-stu-id="89cb3-103">Overview of Azure RTOS NetX</span></span>

<span data-ttu-id="89cb3-104">Azure RTOS NetX は、深く組み込まれたリアルタイム IoT アプリケーション専用に設計された、産業用 TCP/IP IPv4 組み込みネットワーク スタックです。</span><span class="sxs-lookup"><span data-stu-id="89cb3-104">Azure RTOS NetX is an industrial grade TCP/IP IPv4 embedded network stack, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="89cb3-105">Azure RTOS NetX は、Microsoft 独自の IPv4 ネットワーク スタックであり、本質的に Azure RTOS のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="89cb3-105">Azure RTOS NetX is Microsoft's original IPv4 network stack, and is essentially a subset of Azure RTOS.</span></span> <span data-ttu-id="89cb3-106">NetX は、IPv4、TCP、UDP などのコア ネットワーク プロトコルと、その他の高度なアドオン プロトコルの完全なスイートを組み込みアプリケーションに提供します。</span><span class="sxs-lookup"><span data-stu-id="89cb3-106">NetX provides embedded applications with core network protocols such as IPv4, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="89cb3-107">小さなフットプリント、高速実行、優れた操作性により、Azure RTOS NetX は、最も要求の厳しい組み込み IoT アプリケーションに最適な選択肢となっています。</span><span class="sxs-lookup"><span data-stu-id="89cb3-107">A small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX an ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="89cb3-108">API のプロトコル</span><span class="sxs-lookup"><span data-stu-id="89cb3-108">API protocols</span></span>

### <a name="telnet"></a><span data-ttu-id="89cb3-109">Telnet</span><span class="sxs-lookup"><span data-stu-id="89cb3-109">TELNET</span></span>

* <span data-ttu-id="89cb3-110">最小 0.5 KB と 0.3 KB の RAM フットプリント。</span><span class="sxs-lookup"><span data-stu-id="89cb3-110">Minimal 0.5 KB and 0.3 KB RAM footprint.</span></span>
* <span data-ttu-id="89cb3-111">クライアントとサーバーのサポート。</span><span class="sxs-lookup"><span data-stu-id="89cb3-111">Client and server support.</span></span>

### <a name="auto-ip"></a><span data-ttu-id="89cb3-112">Auto IP</span><span class="sxs-lookup"><span data-stu-id="89cb3-112">Auto IP</span></span>

* <span data-ttu-id="89cb3-113">IPv4 アドレス自動割り当て。</span><span class="sxs-lookup"><span data-stu-id="89cb3-113">Automatic IPv4 address assignment.</span></span>
* <span data-ttu-id="89cb3-114">最小 1.2 KB、300 バイトの RAM。</span><span class="sxs-lookup"><span data-stu-id="89cb3-114">Minimal 1.2 KB, 300 bytes of RAM.</span></span>

### <a name="http---hypertext-transfer-protocolhttp"></a><span data-ttu-id="89cb3-115">HTTP - ハイパーテキスト転送プロトコル (HTTP)</span><span class="sxs-lookup"><span data-stu-id="89cb3-115">HTTP - Hypertext Transfer Protocol(HTTP)</span></span>

* <span data-ttu-id="89cb3-116">最小 2.8 KB から 4.8 KB のフラッシュ、0.4 KB から 1.0 KB の RAM フットプリント。</span><span class="sxs-lookup"><span data-stu-id="89cb3-116">Minimal 2.8 KB to 4.8KBFLASH, 0.4 KB to 1.0 KB RAM footprint.</span></span>
* <span data-ttu-id="89cb3-117">クライアントとサーバーのサポート。</span><span class="sxs-lookup"><span data-stu-id="89cb3-117">Client and server support.</span></span>

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a><span data-ttu-id="89cb3-118">SMTP - 簡易メール転送プロトコル (SMTP)</span><span class="sxs-lookup"><span data-stu-id="89cb3-118">SMTP - Simple Mail Transfer Protocol (SMTP)</span></span>

* <span data-ttu-id="89cb3-119">最小 4.1 KB と 0.6 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="89cb3-119">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="89cb3-120">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="89cb3-120">Client support</span></span>

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a><span data-ttu-id="89cb3-121">DHCP - 動的ホスト構成プロトコル (DHCP)</span><span class="sxs-lookup"><span data-stu-id="89cb3-121">DHCP - Dynamic Host Configuration Protocol (DHCP)</span></span>

* <span data-ttu-id="89cb3-122">最小 3.6 KB から 4.6 KB のフラッシュ、2.7 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="89cb3-122">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="89cb3-123">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="89cb3-123">Client and server support</span></span>
* <span data-ttu-id="89cb3-124">IPv4 のサポート</span><span class="sxs-lookup"><span data-stu-id="89cb3-124">IPv4 support</span></span>

### <a name="p0p3---post-office-protocol-version-3-pop3"></a><span data-ttu-id="89cb3-125">P0P3 - Post Office Protocol Version 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="89cb3-125">P0P3 - Post Office Protocol Version 3 (POP3)</span></span>

* <span data-ttu-id="89cb3-126">最小 8.1 KB と 1.4 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="89cb3-126">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="89cb3-127">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="89cb3-127">Client support</span></span>

### <a name="snmp---simple-network-management-protocol-snmp"></a><span data-ttu-id="89cb3-128">SNMP - 簡易ネットワーク管理プロトコル (SNMP)</span><span class="sxs-lookup"><span data-stu-id="89cb3-128">SNMP - Simple Network Management Protocol (SNMP)</span></span>

* <span data-ttu-id="89cb3-129">最小 10.9 KB と 2.6 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="89cb3-129">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="89cb3-130">VI、V2、V3 のエージェントのサポート</span><span class="sxs-lookup"><span data-stu-id="89cb3-130">Agent support for VI, V2, and V3</span></span>

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a><span data-ttu-id="89cb3-131">FTP、TFTP - ファイル転送プロトコル (FTP)、簡易ファイル転送プロトコル (TFTP)</span><span class="sxs-lookup"><span data-stu-id="89cb3-131">FTP, TFTP - File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span></span>

* <span data-ttu-id="89cb3-132">FTP - 最小 1.8 KB から 7.2 KB のフラッシュ、0.6 KB から 2.1 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="89cb3-132">FTP Minimal 1.8 KB to 7.2KBFLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="89cb3-133">TFTP - 最小 1.7 KB から 2.4 KB のフラッシュ、0.3 KB から 1.8 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="89cb3-133">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="89cb3-134">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="89cb3-134">Client and server support</span></span>

### <a name="ppp---polnt-to-point-protocol-ppp"></a><span data-ttu-id="89cb3-135">PPP - Point-to-Point プロトコル (PPP)</span><span class="sxs-lookup"><span data-stu-id="89cb3-135">PPP - Polnt-to-PoInt Protocol (PPP)</span></span>

* <span data-ttu-id="89cb3-136">最小 7.1 KB と 3.8 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="89cb3-136">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="89cb3-137">信頼性と確実性。</span><span class="sxs-lookup"><span data-stu-id="89cb3-137">Dependable and reliable.</span></span>

### <a name="sntp---simple-network-time-protocol-sntp"></a><span data-ttu-id="89cb3-138">SNTP - Simple Network Time Protocol (SNTP)</span><span class="sxs-lookup"><span data-stu-id="89cb3-138">SNTP - Simple Network Time Protocol (SNTP)</span></span>

* <span data-ttu-id="89cb3-139">最小 4 KB および 0.5 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="89cb3-139">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="89cb3-140">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="89cb3-140">Client support</span></span>

### <a name="azure-rtos-netx-api"></a><span data-ttu-id="89cb3-141">Azure RTOS NetX API</span><span class="sxs-lookup"><span data-stu-id="89cb3-141">Azure RTOS NetX API</span></span>

* <span data-ttu-id="89cb3-142">高速のゼロコピー API 実装</span><span class="sxs-lookup"><span data-stu-id="89cb3-142">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="89cb3-143">レガシ ソケット コードを移植するためのオプションの BSD レイヤー</span><span class="sxs-lookup"><span data-stu-id="89cb3-143">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp---internet-group-management-protocol-igmp"></a><span data-ttu-id="89cb3-144">IGMP - インターネット グループ管理プロトコル (IGMP)</span><span class="sxs-lookup"><span data-stu-id="89cb3-144">IGMP - Internet Group Management Protocol (IGMP)</span></span>

* <span data-ttu-id="89cb3-145">最小 2.5 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="89cb3-145">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="89cb3-146">IPv4 マルチキャスト グループのサポート</span><span class="sxs-lookup"><span data-stu-id="89cb3-146">IPv4 multicast group support</span></span>
* <span data-ttu-id="89cb3-147">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="89cb3-147">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="89cb3-148">オプションの IGMP 統計情報</span><span class="sxs-lookup"><span data-stu-id="89cb3-148">Optional IGMP statistics</span></span>
* <span data-ttu-id="89cb3-149">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="89cb3-149">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="udp---user-datagram-protocol-udp"></a><span data-ttu-id="89cb3-150">UDP - ユーザー データグラム プロトコル (UDP)</span><span class="sxs-lookup"><span data-stu-id="89cb3-150">UDP - User Datagram Protocol (UDP)</span></span>

* <span data-ttu-id="89cb3-151">最小 2.5 KB のフラッシュ、ソケットあたり 124 ソケット バイトの RAM</span><span class="sxs-lookup"><span data-stu-id="89cb3-151">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="89cb3-152">高速でほぼワイヤスピードの TCP パケット処理:</span><span class="sxs-lookup"><span data-stu-id="89cb3-152">Fast, near wirespeed TCP packet processing:</span></span>
* <span data-ttu-id="89cb3-153">RX 95 Mbps (100 Mbps イーサネット)、MCU @100MHz、14% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="89cb3-153">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU Utilization</span></span>
* <span data-ttu-id="89cb3-154">TX 94 Mbps (100 Mbps イーサネット)、MCU @100MHz、10% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="89cb3-154">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU Utilization</span></span>
* <span data-ttu-id="89cb3-155">UDP Fast Path™ テクノロジ</span><span class="sxs-lookup"><span data-stu-id="89cb3-155">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="89cb3-156">UDP の数に制限なし</span><span class="sxs-lookup"><span data-stu-id="89cb3-156">No limits on the number of UDP</span></span>
* <span data-ttu-id="89cb3-157">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="89cb3-157">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="89cb3-158">ソケット受信時のオプションの中断</span><span class="sxs-lookup"><span data-stu-id="89cb3-158">Optional suspension on socket receive</span></span>
* <span data-ttu-id="89cb3-159">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="89cb3-159">Optional timeout on all suspension</span></span>
* <span data-ttu-id="89cb3-160">オプションの UDP 統計情報</span><span class="sxs-lookup"><span data-stu-id="89cb3-160">Optional UDP statistics</span></span>
* <span data-ttu-id="89cb3-161">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="89cb3-161">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="tcp---transmission-control-protocol-tcp"></a><span data-ttu-id="89cb3-162">TCP - 伝送制御プロトコル (TCP)</span><span class="sxs-lookup"><span data-stu-id="89cb3-162">TCP - Transmission Control Protocol (TCP)</span></span>

* <span data-ttu-id="89cb3-163">最小 10.5 KB から 12.5 KB のフラッシュ、ソケットあたり 280 バイトの RAM</span><span class="sxs-lookup"><span data-stu-id="89cb3-163">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="89cb3-164">高速でほぼワイヤスピードの TCP パケット処理:</span><span class="sxs-lookup"><span data-stu-id="89cb3-164">Fast, near wlrespeed TCP packet processing:</span></span>
* <span data-ttu-id="89cb3-165">RX 93 Mbps (100 Mbps イーサネット)、MCU @100MHz、20% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="89cb3-165">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU Utilization</span></span>
* <span data-ttu-id="89cb3-166">TX 94 Mbps (100 Mbps イーサネット)、MCU @100MHz、27% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="89cb3-166">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU Utilization</span></span>
* <span data-ttu-id="89cb3-167">信頼性の高い接続</span><span class="sxs-lookup"><span data-stu-id="89cb3-167">Reliable connection</span></span>
* <span data-ttu-id="89cb3-168">TCP ソケット数に制限なし</span><span class="sxs-lookup"><span data-stu-id="89cb3-168">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="89cb3-169">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="89cb3-169">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="89cb3-170">ソケット受信/送信時のオプションの中断</span><span class="sxs-lookup"><span data-stu-id="89cb3-170">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="89cb3-171">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="89cb3-171">Optional timeout on all suspension</span></span>
* <span data-ttu-id="89cb3-172">オプションの TCP 統計情報</span><span class="sxs-lookup"><span data-stu-id="89cb3-172">Optional TCP statistics</span></span>
* <span data-ttu-id="89cb3-173">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="89cb3-173">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="icmp---internet-control-message-protocol-icmp"></a><span data-ttu-id="89cb3-174">ICMP - インターネット制御メッセージ プロトコル (ICMP)</span><span class="sxs-lookup"><span data-stu-id="89cb3-174">ICMP - Internet Control Message Protocol (ICMP)</span></span>

* <span data-ttu-id="89cb3-175">最小 2.5 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="89cb3-175">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="89cb3-176">IPv4 のサポート</span><span class="sxs-lookup"><span data-stu-id="89cb3-176">IPv4 support</span></span>
* <span data-ttu-id="89cb3-177">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="89cb3-177">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="89cb3-178">ping 要求と ping 応答</span><span class="sxs-lookup"><span data-stu-id="89cb3-178">Ping request and ping response</span></span>
* <span data-ttu-id="89cb3-179">ping 要求時のオプションのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="89cb3-179">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="89cb3-180">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="89cb3-180">Optional timeout on all suspension</span></span>
* <span data-ttu-id="89cb3-181">オプションの ICMP 統計情報</span><span class="sxs-lookup"><span data-stu-id="89cb3-181">Optional ICMP statistics</span></span>
* <span data-ttu-id="89cb3-182">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="89cb3-182">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="ipv4---internet-protocol-ip"></a><span data-ttu-id="89cb3-183">IPv4 - インターネット プロトコル (IP)</span><span class="sxs-lookup"><span data-stu-id="89cb3-183">IPv4 - Internet Protocol (IP)</span></span>

* <span data-ttu-id="89cb3-184">最小 3.5 KB から 8.5 KB のフラッシュ、2 KB から 3 KB の RAM フットプリント。</span><span class="sxs-lookup"><span data-stu-id="89cb3-184">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint.</span></span>
* <span data-ttu-id="89cb3-185">Piconet™ アーキテクチャ。</span><span class="sxs-lookup"><span data-stu-id="89cb3-185">Piconet™ Architecture.</span></span>
* <span data-ttu-id="89cb3-186">高速な、ワイヤスピードに近いパフォーマンス。</span><span class="sxs-lookup"><span data-stu-id="89cb3-186">Fast, near wirespeed performance.</span></span>
* <span data-ttu-id="89cb3-187">複数インターフェイスのサポート。</span><span class="sxs-lookup"><span data-stu-id="89cb3-187">Multiple interface support.</span></span>
* <span data-ttu-id="89cb3-188">マルチホームのサポート。</span><span class="sxs-lookup"><span data-stu-id="89cb3-188">Multi-homed support.</span></span>
* <span data-ttu-id="89cb3-189">静的ルーティングのサポート。</span><span class="sxs-lookup"><span data-stu-id="89cb3-189">Static routing support.</span></span>
* <span data-ttu-id="89cb3-190">IP の断片化と再構築のサポート。</span><span class="sxs-lookup"><span data-stu-id="89cb3-190">IP fragmentation/reassembly support.</span></span>
* <span data-ttu-id="89cb3-191">IPv4 のサポート。</span><span class="sxs-lookup"><span data-stu-id="89cb3-191">IPv4 Support.</span></span>
* <span data-ttu-id="89cb3-192">IXIA IxANVL 検証済み。</span><span class="sxs-lookup"><span data-stu-id="89cb3-192">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="89cb3-193">フェーズ II 対応ロゴ認定。</span><span class="sxs-lookup"><span data-stu-id="89cb3-193">Phase II Ready Logo Certification.</span></span>
* <span data-ttu-id="89cb3-194">オプションの IP 統計情報。</span><span class="sxs-lookup"><span data-stu-id="89cb3-194">Optional IP statistics.</span></span>
* <span data-ttu-id="89cb3-195">明確に定義された直感的な物理層ドライバー インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="89cb3-195">Well defined, intuitive physical layer driver interface.</span></span>
* <span data-ttu-id="89cb3-196">Azure RTOS TraceX によるシステムレベルのトレース。</span><span class="sxs-lookup"><span data-stu-id="89cb3-196">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a><span data-ttu-id="89cb3-197">ARP/RARP - アドレス解決プロトコル (ARP)、逆アドレス解決プロトコル (RARP)</span><span class="sxs-lookup"><span data-stu-id="89cb3-197">ARP/RARP - Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span></span>

* <span data-ttu-id="89cb3-198">最小 1.7 KB のフラッシュ、RAM サイズ。</span><span class="sxs-lookup"><span data-stu-id="89cb3-198">Minimal 1.7 KB FLASH, RAM size.</span></span>
* <span data-ttu-id="89cb3-199">32 ビット IPv4 と 48 ビット MAC アドレスの動的な解決。</span><span class="sxs-lookup"><span data-stu-id="89cb3-199">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses.</span></span>
* <span data-ttu-id="89cb3-200">IXIA IxANVL 検証済み。</span><span class="sxs-lookup"><span data-stu-id="89cb3-200">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="89cb3-201">柔軟なユーザー定義の ARP キャッシュ。</span><span class="sxs-lookup"><span data-stu-id="89cb3-201">Flexible, user-defined ARP cache.</span></span>
* <span data-ttu-id="89cb3-202">Gratuitous ARP のサポート。</span><span class="sxs-lookup"><span data-stu-id="89cb3-202">Gratuitous ARP support.</span></span>
* <span data-ttu-id="89cb3-203">アプリケーションによって決定されるオプションの ARP/RARP 統計情報。</span><span class="sxs-lookup"><span data-stu-id="89cb3-203">Optional ARP/RARP statistics determined by application.</span></span>
* <span data-ttu-id="89cb3-204">Azure RTOS TraceX によるシステムレベルのトレース。</span><span class="sxs-lookup"><span data-stu-id="89cb3-204">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a><span data-ttu-id="89cb3-205">イーサネット、WiFi、Bluetooth LE、15.4 など</span><span class="sxs-lookup"><span data-stu-id="89cb3-205">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="89cb3-206">相互運用性の検証</span><span class="sxs-lookup"><span data-stu-id="89cb3-206">Interoperability verification</span></span>

<span data-ttu-id="89cb3-207">Azure RTOS NetX は RFC 標準に準拠しており、ほとんどのベンダーのデバイスとの完全な相互運用性を提供します。</span><span class="sxs-lookup"><span data-stu-id="89cb3-207">Azure RTOS NetX conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span> <span data-ttu-id="89cb3-208">Azure RTOS NetX では、Azure RTOS NetX コア TCP/IP プロトコル実装に業界標準の IxANVL (自動ネットワーク検証ライブラリ) も利用しています。</span><span class="sxs-lookup"><span data-stu-id="89cb3-208">Azure RTOS NetX also utilizes the industry standard IxANVL (Automated Network Validation Library) for the Azure RTOS NetX core TCP/IP protocol implementation.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="89cb3-209">高度なテクノロジ</span><span class="sxs-lookup"><span data-stu-id="89cb3-209">Advanced technology</span></span>

<span data-ttu-id="89cb3-210">Azure RTOS NetX は、次の機能を備えた高度なテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="89cb3-210">Azure RTOS NetX is advanced technology that includes the following.</span></span>
* <span data-ttu-id="89cb3-211">Piconet™ アーキテクチャ。</span><span class="sxs-lookup"><span data-stu-id="89cb3-211">Piconet™ architecture.</span></span>
* <span data-ttu-id="89cb3-212">自動スケーリング。</span><span class="sxs-lookup"><span data-stu-id="89cb3-212">Automatic scaling.</span></span>
* <span data-ttu-id="89cb3-213">UDP Fast-Path Technology™。</span><span class="sxs-lookup"><span data-stu-id="89cb3-213">UDP Fast-Path Technology™.</span></span>
* <span data-ttu-id="89cb3-214">柔軟なパケット管理。</span><span class="sxs-lookup"><span data-stu-id="89cb3-214">Flexible packet management.</span></span>
* <span data-ttu-id="89cb3-215">ゼロコピー API と実装。</span><span class="sxs-lookup"><span data-stu-id="89cb3-215">Zero-copy API and implementation.</span></span>
* <span data-ttu-id="89cb3-216">マルチホームのサポート。</span><span class="sxs-lookup"><span data-stu-id="89cb3-216">Multi-homed support.</span></span>
* <span data-ttu-id="89cb3-217">すべての中断時のオプションのタイムアウト。</span><span class="sxs-lookup"><span data-stu-id="89cb3-217">Optional timeout on all suspension.</span></span>
* <span data-ttu-id="89cb3-218">静的ルーティングのサポート。</span><span class="sxs-lookup"><span data-stu-id="89cb3-218">Static routing support.</span></span>
* <span data-ttu-id="89cb3-219">Azure RTOS TraceX システム分析のサポート。</span><span class="sxs-lookup"><span data-stu-id="89cb3-219">Azure RTOS TraceX system analysis support.</span></span>
