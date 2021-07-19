---
title: Azure RTOS NetX を理解する
description: Azure RTOS NetX は、TCP/IP プロトコル標準のハイパフォーマンス実装です。Azure RTOS ThreadX と完全に統合されており、サポートされるすべてのプロセッサで利用できます。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 63fd212249da6154926684f9bc844d2c2a78e84e
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754847"
---
# <a name="overview-of-azure-rtos-netx"></a><span data-ttu-id="7c55d-103">Azure RTOS NetX の概要</span><span class="sxs-lookup"><span data-stu-id="7c55d-103">Overview of Azure RTOS NetX</span></span>

<span data-ttu-id="7c55d-104">Azure RTOS NetX は、深く組み込まれたリアルタイム IoT アプリケーション専用に設計された、産業用 TCP/IP IPv4 組み込みネットワーク スタックです。</span><span class="sxs-lookup"><span data-stu-id="7c55d-104">Azure RTOS NetX is an industrial grade TCP/IP IPv4 embedded network stack, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="7c55d-105">Azure RTOS NetX は、Microsoft 独自の IPv4 ネットワーク スタックであり、本質的に Azure RTOS のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="7c55d-105">Azure RTOS NetX is Microsoft's original IPv4 network stack, and is essentially a subset of Azure RTOS.</span></span> <span data-ttu-id="7c55d-106">NetX は、IPv4、TCP、UDP などのコア ネットワーク プロトコルと、その他の高度なアドオン プロトコルの完全なスイートを組み込みアプリケーションに提供します。</span><span class="sxs-lookup"><span data-stu-id="7c55d-106">NetX provides embedded applications with core network protocols such as IPv4, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="7c55d-107">小さなフットプリント、高速実行、優れた操作性により、Azure RTOS NetX は、最も要求の厳しい組み込み IoT アプリケーションに最適な選択肢となっています。</span><span class="sxs-lookup"><span data-stu-id="7c55d-107">A small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX an ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="7c55d-108">API のプロトコル</span><span class="sxs-lookup"><span data-stu-id="7c55d-108">API protocols</span></span>
<span data-ttu-id="7c55d-109">Azure RTOS NetX では、次の機能がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7c55d-109">Azure RTOS NetX provides support for the following.</span></span>

### <a name="telnet"></a><span data-ttu-id="7c55d-110">Telnet</span><span class="sxs-lookup"><span data-stu-id="7c55d-110">TELNET</span></span>

* <span data-ttu-id="7c55d-111">最小 0.5 KB と 0.3 KB の RAM フットプリント。</span><span class="sxs-lookup"><span data-stu-id="7c55d-111">Minimal 0.5 KB and 0.3 KB RAM footprint.</span></span>
* <span data-ttu-id="7c55d-112">クライアントとサーバーのサポート。</span><span class="sxs-lookup"><span data-stu-id="7c55d-112">Client and server support.</span></span>

### <a name="auto-ip"></a><span data-ttu-id="7c55d-113">Auto IP</span><span class="sxs-lookup"><span data-stu-id="7c55d-113">Auto IP</span></span>

* <span data-ttu-id="7c55d-114">IPv4 アドレス自動割り当て。</span><span class="sxs-lookup"><span data-stu-id="7c55d-114">Automatic IPv4 address assignment.</span></span>
* <span data-ttu-id="7c55d-115">最小 1.2 KB、300 バイトの RAM。</span><span class="sxs-lookup"><span data-stu-id="7c55d-115">Minimal 1.2 KB, 300 bytes of RAM.</span></span>

### <a name="http---hypertext-transfer-protocolhttp"></a><span data-ttu-id="7c55d-116">HTTP - ハイパーテキスト転送プロトコル (HTTP)</span><span class="sxs-lookup"><span data-stu-id="7c55d-116">HTTP - Hypertext Transfer Protocol(HTTP)</span></span>

* <span data-ttu-id="7c55d-117">最小 2.8 KB から 4.8 KB のフラッシュ、0.4 KB から 1.0 KB の RAM フットプリント。</span><span class="sxs-lookup"><span data-stu-id="7c55d-117">Minimal 2.8 KB to 4.8KBFLASH, 0.4 KB to 1.0 KB RAM footprint.</span></span>
* <span data-ttu-id="7c55d-118">クライアントとサーバーのサポート。</span><span class="sxs-lookup"><span data-stu-id="7c55d-118">Client and server support.</span></span>

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a><span data-ttu-id="7c55d-119">SMTP - 簡易メール転送プロトコル (SMTP)</span><span class="sxs-lookup"><span data-stu-id="7c55d-119">SMTP - Simple Mail Transfer Protocol (SMTP)</span></span>

* <span data-ttu-id="7c55d-120">最小 4.1 KB と 0.6 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="7c55d-120">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="7c55d-121">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="7c55d-121">Client support</span></span>

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a><span data-ttu-id="7c55d-122">DHCP - 動的ホスト構成プロトコル (DHCP)</span><span class="sxs-lookup"><span data-stu-id="7c55d-122">DHCP - Dynamic Host Configuration Protocol (DHCP)</span></span>

* <span data-ttu-id="7c55d-123">最小 3.6 KB から 4.6 KB のフラッシュ、2.7 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="7c55d-123">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="7c55d-124">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="7c55d-124">Client and server support</span></span>
* <span data-ttu-id="7c55d-125">IPv4 のサポート</span><span class="sxs-lookup"><span data-stu-id="7c55d-125">IPv4 support</span></span>

### <a name="p0p3---post-office-protocol-version-3-pop3"></a><span data-ttu-id="7c55d-126">P0P3 - Post Office Protocol Version 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="7c55d-126">P0P3 - Post Office Protocol Version 3 (POP3)</span></span>

* <span data-ttu-id="7c55d-127">最小 8.1 KB と 1.4 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="7c55d-127">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="7c55d-128">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="7c55d-128">Client support</span></span>

### <a name="snmp---simple-network-management-protocol-snmp"></a><span data-ttu-id="7c55d-129">SNMP - 簡易ネットワーク管理プロトコル (SNMP)</span><span class="sxs-lookup"><span data-stu-id="7c55d-129">SNMP - Simple Network Management Protocol (SNMP)</span></span>

* <span data-ttu-id="7c55d-130">最小 10.9 KB と 2.6 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="7c55d-130">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="7c55d-131">VI、V2、V3 のエージェントのサポート</span><span class="sxs-lookup"><span data-stu-id="7c55d-131">Agent support for VI, V2, and V3</span></span>

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a><span data-ttu-id="7c55d-132">FTP、TFTP - ファイル転送プロトコル (FTP)、簡易ファイル転送プロトコル (TFTP)</span><span class="sxs-lookup"><span data-stu-id="7c55d-132">FTP, TFTP - File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span></span>

* <span data-ttu-id="7c55d-133">FTP - 最小 1.8 KB から 7.2 KB のフラッシュ、0.6 KB から 2.1 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="7c55d-133">FTP Minimal 1.8 KB to 7.2KBFLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="7c55d-134">TFTP - 最小 1.7 KB から 2.4 KB のフラッシュ、0.3 KB から 1.8 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="7c55d-134">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="7c55d-135">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="7c55d-135">Client and server support</span></span>

### <a name="ppp---polnt-to-point-protocol-ppp"></a><span data-ttu-id="7c55d-136">PPP - Point-to-Point プロトコル (PPP)</span><span class="sxs-lookup"><span data-stu-id="7c55d-136">PPP - Polnt-to-PoInt Protocol (PPP)</span></span>

* <span data-ttu-id="7c55d-137">最小 7.1 KB と 3.8 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="7c55d-137">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="7c55d-138">信頼性と確実性。</span><span class="sxs-lookup"><span data-stu-id="7c55d-138">Dependable and reliable.</span></span>

### <a name="sntp---simple-network-time-protocol-sntp"></a><span data-ttu-id="7c55d-139">SNTP - Simple Network Time Protocol (SNTP)</span><span class="sxs-lookup"><span data-stu-id="7c55d-139">SNTP - Simple Network Time Protocol (SNTP)</span></span>

* <span data-ttu-id="7c55d-140">最小 4 KB および 0.5 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="7c55d-140">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="7c55d-141">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="7c55d-141">Client support</span></span>

### <a name="azure-rtos-netx-api"></a><span data-ttu-id="7c55d-142">Azure RTOS NetX API</span><span class="sxs-lookup"><span data-stu-id="7c55d-142">Azure RTOS NetX API</span></span>

* <span data-ttu-id="7c55d-143">高速のゼロコピー API 実装</span><span class="sxs-lookup"><span data-stu-id="7c55d-143">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="7c55d-144">レガシ ソケット コードを移植するためのオプションの BSD レイヤー</span><span class="sxs-lookup"><span data-stu-id="7c55d-144">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp---internet-group-management-protocol-igmp"></a><span data-ttu-id="7c55d-145">IGMP - インターネット グループ管理プロトコル (IGMP)</span><span class="sxs-lookup"><span data-stu-id="7c55d-145">IGMP - Internet Group Management Protocol (IGMP)</span></span>

* <span data-ttu-id="7c55d-146">最小 2.5 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="7c55d-146">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="7c55d-147">IPv4 マルチキャスト グループのサポート</span><span class="sxs-lookup"><span data-stu-id="7c55d-147">IPv4 multicast group support</span></span>
* <span data-ttu-id="7c55d-148">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="7c55d-148">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="7c55d-149">オプションの IGMP 統計情報</span><span class="sxs-lookup"><span data-stu-id="7c55d-149">Optional IGMP statistics</span></span>
* <span data-ttu-id="7c55d-150">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="7c55d-150">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="udp---user-datagram-protocol-udp"></a><span data-ttu-id="7c55d-151">UDP - ユーザー データグラム プロトコル (UDP)</span><span class="sxs-lookup"><span data-stu-id="7c55d-151">UDP - User Datagram Protocol (UDP)</span></span>

* <span data-ttu-id="7c55d-152">最小 2.5 KB のフラッシュ、ソケットあたり 124 ソケット バイトの RAM</span><span class="sxs-lookup"><span data-stu-id="7c55d-152">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="7c55d-153">高速でほぼワイヤスピードの TCP パケット処理:</span><span class="sxs-lookup"><span data-stu-id="7c55d-153">Fast, near wirespeed TCP packet processing:</span></span>
* <span data-ttu-id="7c55d-154">RX 95 Mbps (100 Mbps イーサネット)、MCU @100MHz、14% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="7c55d-154">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU Utilization</span></span>
* <span data-ttu-id="7c55d-155">TX 94 Mbps (100 Mbps イーサネット)、MCU @100MHz、10% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="7c55d-155">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU Utilization</span></span>
* <span data-ttu-id="7c55d-156">UDP Fast Path™ テクノロジ</span><span class="sxs-lookup"><span data-stu-id="7c55d-156">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="7c55d-157">UDP の数に制限なし</span><span class="sxs-lookup"><span data-stu-id="7c55d-157">No limits on the number of UDP</span></span>
* <span data-ttu-id="7c55d-158">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="7c55d-158">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="7c55d-159">ソケット受信時のオプションの中断</span><span class="sxs-lookup"><span data-stu-id="7c55d-159">Optional suspension on socket receive</span></span>
* <span data-ttu-id="7c55d-160">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="7c55d-160">Optional timeout on all suspension</span></span>
* <span data-ttu-id="7c55d-161">オプションの UDP 統計情報</span><span class="sxs-lookup"><span data-stu-id="7c55d-161">Optional UDP statistics</span></span>
* <span data-ttu-id="7c55d-162">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="7c55d-162">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="tcp---transmission-control-protocol-tcp"></a><span data-ttu-id="7c55d-163">TCP - 伝送制御プロトコル (TCP)</span><span class="sxs-lookup"><span data-stu-id="7c55d-163">TCP - Transmission Control Protocol (TCP)</span></span>

* <span data-ttu-id="7c55d-164">最小 10.5 KB から 12.5 KB のフラッシュ、ソケットあたり 280 バイトの RAM</span><span class="sxs-lookup"><span data-stu-id="7c55d-164">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="7c55d-165">高速でほぼワイヤスピードの TCP パケット処理:</span><span class="sxs-lookup"><span data-stu-id="7c55d-165">Fast, near wlrespeed TCP packet processing:</span></span>
* <span data-ttu-id="7c55d-166">RX 93 Mbps (100 Mbps イーサネット)、MCU @100MHz、20% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="7c55d-166">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU Utilization</span></span>
* <span data-ttu-id="7c55d-167">TX 94 Mbps (100 Mbps イーサネット)、MCU @100MHz、27% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="7c55d-167">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU Utilization</span></span>
* <span data-ttu-id="7c55d-168">信頼性の高い接続</span><span class="sxs-lookup"><span data-stu-id="7c55d-168">Reliable connection</span></span>
* <span data-ttu-id="7c55d-169">TCP ソケット数に制限なし</span><span class="sxs-lookup"><span data-stu-id="7c55d-169">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="7c55d-170">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="7c55d-170">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="7c55d-171">ソケット受信/送信時のオプションの中断</span><span class="sxs-lookup"><span data-stu-id="7c55d-171">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="7c55d-172">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="7c55d-172">Optional timeout on all suspension</span></span>
* <span data-ttu-id="7c55d-173">オプションの TCP 統計情報</span><span class="sxs-lookup"><span data-stu-id="7c55d-173">Optional TCP statistics</span></span>
* <span data-ttu-id="7c55d-174">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="7c55d-174">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="icmp---internet-control-message-protocol-icmp"></a><span data-ttu-id="7c55d-175">ICMP - インターネット制御メッセージ プロトコル (ICMP)</span><span class="sxs-lookup"><span data-stu-id="7c55d-175">ICMP - Internet Control Message Protocol (ICMP)</span></span>

* <span data-ttu-id="7c55d-176">最小 2.5 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="7c55d-176">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="7c55d-177">IPv4 のサポート</span><span class="sxs-lookup"><span data-stu-id="7c55d-177">IPv4 support</span></span>
* <span data-ttu-id="7c55d-178">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="7c55d-178">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="7c55d-179">ping 要求と ping 応答</span><span class="sxs-lookup"><span data-stu-id="7c55d-179">Ping request and ping response</span></span>
* <span data-ttu-id="7c55d-180">ping 要求時のオプションのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="7c55d-180">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="7c55d-181">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="7c55d-181">Optional timeout on all suspension</span></span>
* <span data-ttu-id="7c55d-182">オプションの ICMP 統計情報</span><span class="sxs-lookup"><span data-stu-id="7c55d-182">Optional ICMP statistics</span></span>
* <span data-ttu-id="7c55d-183">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="7c55d-183">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="ipv4---internet-protocol-ip"></a><span data-ttu-id="7c55d-184">IPv4 - インターネット プロトコル (IP)</span><span class="sxs-lookup"><span data-stu-id="7c55d-184">IPv4 - Internet Protocol (IP)</span></span>

* <span data-ttu-id="7c55d-185">最小 3.5 KB から 8.5 KB のフラッシュ、2 KB から 3 KB の RAM フットプリント。</span><span class="sxs-lookup"><span data-stu-id="7c55d-185">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint.</span></span>
* <span data-ttu-id="7c55d-186">Piconet™ アーキテクチャ。</span><span class="sxs-lookup"><span data-stu-id="7c55d-186">Piconet™ Architecture.</span></span>
* <span data-ttu-id="7c55d-187">高速な、ワイヤスピードに近いパフォーマンス。</span><span class="sxs-lookup"><span data-stu-id="7c55d-187">Fast, near wirespeed performance.</span></span>
* <span data-ttu-id="7c55d-188">複数インターフェイスのサポート。</span><span class="sxs-lookup"><span data-stu-id="7c55d-188">Multiple interface support.</span></span>
* <span data-ttu-id="7c55d-189">マルチホームのサポート。</span><span class="sxs-lookup"><span data-stu-id="7c55d-189">Multi-homed support.</span></span>
* <span data-ttu-id="7c55d-190">静的ルーティングのサポート。</span><span class="sxs-lookup"><span data-stu-id="7c55d-190">Static routing support.</span></span>
* <span data-ttu-id="7c55d-191">IP の断片化と再構築のサポート。</span><span class="sxs-lookup"><span data-stu-id="7c55d-191">IP fragmentation/reassembly support.</span></span>
* <span data-ttu-id="7c55d-192">IPv4 のサポート。</span><span class="sxs-lookup"><span data-stu-id="7c55d-192">IPv4 Support.</span></span>
* <span data-ttu-id="7c55d-193">IXIA IxANVL 検証済み。</span><span class="sxs-lookup"><span data-stu-id="7c55d-193">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="7c55d-194">フェーズ II 対応ロゴ認定。</span><span class="sxs-lookup"><span data-stu-id="7c55d-194">Phase II Ready Logo Certification.</span></span>
* <span data-ttu-id="7c55d-195">オプションの IP 統計情報。</span><span class="sxs-lookup"><span data-stu-id="7c55d-195">Optional IP statistics.</span></span>
* <span data-ttu-id="7c55d-196">明確に定義された直感的な物理層ドライバー インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="7c55d-196">Well defined, intuitive physical layer driver interface.</span></span>
* <span data-ttu-id="7c55d-197">Azure RTOS TraceX によるシステムレベルのトレース。</span><span class="sxs-lookup"><span data-stu-id="7c55d-197">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a><span data-ttu-id="7c55d-198">ARP/RARP - アドレス解決プロトコル (ARP)、逆アドレス解決プロトコル (RARP)</span><span class="sxs-lookup"><span data-stu-id="7c55d-198">ARP/RARP - Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span></span>

* <span data-ttu-id="7c55d-199">最小 1.7 KB のフラッシュ、RAM サイズ。</span><span class="sxs-lookup"><span data-stu-id="7c55d-199">Minimal 1.7 KB FLASH, RAM size.</span></span>
* <span data-ttu-id="7c55d-200">32 ビット IPv4 と 48 ビット MAC アドレスの動的な解決。</span><span class="sxs-lookup"><span data-stu-id="7c55d-200">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses.</span></span>
* <span data-ttu-id="7c55d-201">IXIA IxANVL 検証済み。</span><span class="sxs-lookup"><span data-stu-id="7c55d-201">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="7c55d-202">柔軟なユーザー定義の ARP キャッシュ。</span><span class="sxs-lookup"><span data-stu-id="7c55d-202">Flexible, user-defined ARP cache.</span></span>
* <span data-ttu-id="7c55d-203">Gratuitous ARP のサポート。</span><span class="sxs-lookup"><span data-stu-id="7c55d-203">Gratuitous ARP support.</span></span>
* <span data-ttu-id="7c55d-204">アプリケーションによって決定されるオプションの ARP/RARP 統計情報。</span><span class="sxs-lookup"><span data-stu-id="7c55d-204">Optional ARP/RARP statistics determined by application.</span></span>
* <span data-ttu-id="7c55d-205">Azure RTOS TraceX によるシステムレベルのトレース。</span><span class="sxs-lookup"><span data-stu-id="7c55d-205">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a><span data-ttu-id="7c55d-206">イーサネット、WiFi、Bluetooth LE、15.4 など</span><span class="sxs-lookup"><span data-stu-id="7c55d-206">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="7c55d-207">相互運用性の検証</span><span class="sxs-lookup"><span data-stu-id="7c55d-207">Interoperability verification</span></span>

<span data-ttu-id="7c55d-208">Azure RTOS NetX は RFC 標準に準拠しており、ほとんどのベンダーのデバイスとの完全な相互運用性を提供します。</span><span class="sxs-lookup"><span data-stu-id="7c55d-208">Azure RTOS NetX conforms to RFC standards and offers complete interoperability with devices from most vendors.</span></span> <span data-ttu-id="7c55d-209">Azure RTOS NetX では、Azure RTOS NetX コア TCP/IP プロトコル実装に業界標準の IxANVL (自動ネットワーク検証ライブラリ) も利用しています。</span><span class="sxs-lookup"><span data-stu-id="7c55d-209">Azure RTOS NetX also utilizes the industry standard IxANVL (Automated Network Validation Library) for the Azure RTOS NetX core TCP/IP protocol implementation.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="7c55d-210">高度なテクノロジ</span><span class="sxs-lookup"><span data-stu-id="7c55d-210">Advanced technology</span></span>

<span data-ttu-id="7c55d-211">Azure RTOS NetX は、次の機能を備えた高度なテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="7c55d-211">Azure RTOS NetX is advanced technology that includes the following.</span></span>
* <span data-ttu-id="7c55d-212">Piconet™ アーキテクチャ。</span><span class="sxs-lookup"><span data-stu-id="7c55d-212">Piconet™ architecture.</span></span>
* <span data-ttu-id="7c55d-213">自動スケーリング。</span><span class="sxs-lookup"><span data-stu-id="7c55d-213">Automatic scaling.</span></span>
* <span data-ttu-id="7c55d-214">UDP Fast-Path Technology™。</span><span class="sxs-lookup"><span data-stu-id="7c55d-214">UDP Fast-Path Technology™.</span></span>
* <span data-ttu-id="7c55d-215">柔軟なパケット管理。</span><span class="sxs-lookup"><span data-stu-id="7c55d-215">Flexible packet management.</span></span>
* <span data-ttu-id="7c55d-216">ゼロコピー API と実装。</span><span class="sxs-lookup"><span data-stu-id="7c55d-216">Zero-copy API and implementation.</span></span>
* <span data-ttu-id="7c55d-217">マルチホームのサポート。</span><span class="sxs-lookup"><span data-stu-id="7c55d-217">Multi-homed support.</span></span>
* <span data-ttu-id="7c55d-218">すべての中断時のオプションのタイムアウト。</span><span class="sxs-lookup"><span data-stu-id="7c55d-218">Optional timeout on all suspension.</span></span>
* <span data-ttu-id="7c55d-219">静的ルーティングのサポート。</span><span class="sxs-lookup"><span data-stu-id="7c55d-219">Static routing support.</span></span>
* <span data-ttu-id="7c55d-220">Azure RTOS TraceX システム分析のサポート。</span><span class="sxs-lookup"><span data-stu-id="7c55d-220">Azure RTOS TraceX system analysis support.</span></span>
