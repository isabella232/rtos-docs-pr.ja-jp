---
title: Azure RTOS NetX Duo を理解する
description: Azure RTOS NetX Duo は、深い埋め込み型のリアルタイム IoT アプリケーション用に特に設計された高度な商用 TCP/IP ネットワーク スタックです。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 2339da391e52b437a2111ae439cccf41e038bdcf
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811741"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="023d7-103">Azure RTOS NetX Duo の概要</span><span class="sxs-lookup"><span data-stu-id="023d7-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="023d7-104">Azure RTOS NetX Duo 埋め込み型 TCP/IP ネットワーク スタックは、深い埋め込み型のリアルタイム IoT アプリケーション専用に設計された、Microsoft が提供する高度な商用デュアル IPv4 および IPv6 TCP/IP ネットワーク スタックです。</span><span class="sxs-lookup"><span data-stu-id="023d7-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="023d7-105">NetX Duo は、コア ネットワーク プロトコル (IPv4、IPv6、TCP、UDP など) と、その他の高度なアドオン プロトコルの完全なスイートを埋め込み型アプリケーションに提供します。</span><span class="sxs-lookup"><span data-stu-id="023d7-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="023d7-106">Azure RTOS NetX Duo は、Azure RTOS NetX Secure IPsec や Azure RTOS NetX Secure SSL/TLS/DTLS を含む追加のアドオン セキュリティ製品を介してセキュリティを提供します。</span><span class="sxs-lookup"><span data-stu-id="023d7-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="023d7-107">これらすべてを小さなフットプリント、高速な処理、優れた使いやすさと組み合わせることで、Azure RTOS NetX Duo は、最も要求の厳しい埋め込み型 IoT アプリケーションに最適な選択肢となります。</span><span class="sxs-lookup"><span data-stu-id="023d7-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="023d7-108">API プロトコル</span><span class="sxs-lookup"><span data-stu-id="023d7-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="023d7-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="023d7-109">MQTT</span></span>

* <span data-ttu-id="023d7-110">Messaging Queue Telemetry Transport (MQTT)</span><span class="sxs-lookup"><span data-stu-id="023d7-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="023d7-111">最小 2.7 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="023d7-111">Minimal 2.7 KB FLASH</span></span>
* <span data-ttu-id="023d7-112">直感的な MQTT API: *nx_mqtt_* \*</span><span class="sxs-lookup"><span data-stu-id="023d7-112">Intuitive MQTT APIs: *nx_mqtt_*\*</span></span>

### <a name="auto-ip"></a><span data-ttu-id="023d7-113">Auto IP</span><span class="sxs-lookup"><span data-stu-id="023d7-113">Auto IP</span></span>

* <span data-ttu-id="023d7-114">IPv4 アドレスの自動割り当て</span><span class="sxs-lookup"><span data-stu-id="023d7-114">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="023d7-115">最小 1.2 KB、300 バイトの RAM</span><span class="sxs-lookup"><span data-stu-id="023d7-115">Minimal 1.2 KB, 300 bytes of RAM</span></span>
* <span data-ttu-id="023d7-116">直感的な AutoIP API: *nx_autoip_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-116">Intuitive AutoIP APIs: *nx_autoip_\**</span></span>

### <a name="http-https"></a><span data-ttu-id="023d7-117">HTTP、HTTPS</span><span class="sxs-lookup"><span data-stu-id="023d7-117">HTTP, HTTPS</span></span>

#### <a name="http-10"></a><span data-ttu-id="023d7-118">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="023d7-118">HTTP 1.0</span></span>

* <span data-ttu-id="023d7-119">ハイパーテキスト転送プロトコル (HTTP)</span><span class="sxs-lookup"><span data-stu-id="023d7-119">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="023d7-120">最小 2.8 KB から 4.8 KB のフラッシュ/0.4 KB から 1.0 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="023d7-120">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="023d7-121">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-121">Client and server support</span></span>
* <span data-ttu-id="023d7-122">直感的な API: *nx_http_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-122">Intuitive APIs: *nx_http_\**</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="023d7-123">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="023d7-123">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="023d7-124">ハイパーテキスト転送プロトコル (HTTP)</span><span class="sxs-lookup"><span data-stu-id="023d7-124">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="023d7-125">最小 3.0 KB から 9.5 KB のフラッシュ/0.5 KB から 2 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="023d7-125">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="023d7-126">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-126">Client and server support</span></span>
* <span data-ttu-id="023d7-127">複数の受信クライアント セッション</span><span class="sxs-lookup"><span data-stu-id="023d7-127">Multiple incoming client sessions</span></span>
* <span data-ttu-id="023d7-128">プレーンテキストと暗号化された HTTPS</span><span class="sxs-lookup"><span data-stu-id="023d7-128">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="023d7-129">永続的な接続のサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-129">Persistent connection support</span></span>
* <span data-ttu-id="023d7-130">マルチパート ファイルのアップロード</span><span class="sxs-lookup"><span data-stu-id="023d7-130">Multipart file upload</span></span>
* <span data-ttu-id="023d7-131">Azure RTOS NetX Secure TLS と完全に統合</span><span class="sxs-lookup"><span data-stu-id="023d7-131">Fully integrated with Azure RTOS NetX Secure TLS</span></span>
* <span data-ttu-id="023d7-132">直感的な API: *nx_web_http\**</span><span class="sxs-lookup"><span data-stu-id="023d7-132">Intuitive APIs: *nx_web_http\**</span></span>

### <a name="smtp"></a><span data-ttu-id="023d7-133">SMTP</span><span class="sxs-lookup"><span data-stu-id="023d7-133">SMTP</span></span>

* <span data-ttu-id="023d7-134">簡易メール転送プロトコル (SMTP)</span><span class="sxs-lookup"><span data-stu-id="023d7-134">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="023d7-135">最小 4.1 KB と 0.6 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="023d7-135">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="023d7-136">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-136">Client support</span></span>
* <span data-ttu-id="023d7-137">直感的な SMTP API: *nx_smtp_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-137">Intuitive SMTP APIs: *nx_smtp_\**</span></span>

### <a name="dhcp"></a><span data-ttu-id="023d7-138">DHCP</span><span class="sxs-lookup"><span data-stu-id="023d7-138">DHCP</span></span>

* <span data-ttu-id="023d7-139">動的ホスト構成プロトコル (DHCP)</span><span class="sxs-lookup"><span data-stu-id="023d7-139">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="023d7-140">最小 3.6 KB から 4.6 KB のフラッシュ、2.7 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="023d7-140">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="023d7-141">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-141">Client and server support</span></span>
* <span data-ttu-id="023d7-142">IPv4 および IPv6 のサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-142">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="023d7-143">直感的な DHCP API: *nx_dhcp_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-143">Intuitive DHCP APIs: *nx_dhcp_\**</span></span>

### <a name="nat"></a><span data-ttu-id="023d7-144">NAT</span><span class="sxs-lookup"><span data-stu-id="023d7-144">NAT</span></span>

* <span data-ttu-id="023d7-145">ネットワーク アドレス変換 (NAT)</span><span class="sxs-lookup"><span data-stu-id="023d7-145">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="023d7-146">最小 3.5 K6 と 0.6 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="023d7-146">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="023d7-147">IPv4 アドレスのサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-147">IPv4 address support</span></span>
* <span data-ttu-id="023d7-148">直感的な NAT API: *nx_nat_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-148">Intuitive NAT APIs: *nx_nat_\**</span></span>
* <span data-ttu-id="023d7-149">NAT は、Azure RTOS NetX Duo でのみ使用可能</span><span class="sxs-lookup"><span data-stu-id="023d7-149">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="023d7-150">SNMP</span><span class="sxs-lookup"><span data-stu-id="023d7-150">SNMP</span></span>

* <span data-ttu-id="023d7-151">簡易ネットワーク管理プロトコル (SNMP)</span><span class="sxs-lookup"><span data-stu-id="023d7-151">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="023d7-152">最小 10.9 KB と 2.6 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="023d7-152">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="023d7-153">VI、V2、V3 のエージェントのサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-153">Agent support for VI, V2, and V3</span></span>
* <span data-ttu-id="023d7-154">直感的な SNMP API: *nx_snmp_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-154">Intuitive SNMP APIs: *nx_snmp_\**</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="023d7-155">DNS、mDNS、DNS-SD</span><span class="sxs-lookup"><span data-stu-id="023d7-155">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="023d7-156">ドメイン ネーム システム (DNS)</span><span class="sxs-lookup"><span data-stu-id="023d7-156">Domain Name System (DNS)</span></span>
* <span data-ttu-id="023d7-157">マルチキャスト ドメイン ネーム システム (mDNS)</span><span class="sxs-lookup"><span data-stu-id="023d7-157">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="023d7-158">DNS ベースのサービス検出 (DNS-SD)</span><span class="sxs-lookup"><span data-stu-id="023d7-158">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="023d7-159">DNS 最小 2.4 KB から 3 KB のフラッシュ、1 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="023d7-159">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="023d7-160">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-160">Client support</span></span>
* <span data-ttu-id="023d7-161">直感的な API: *nx_dns_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-161">Intuitive APIs: *nx_dns_\**</span></span>
* <span data-ttu-id="023d7-162">mDNS と DNS-SD は、Azure RTOS NetX Duo でのみ使用可能</span><span class="sxs-lookup"><span data-stu-id="023d7-162">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="p0p3"></a><span data-ttu-id="023d7-163">P0P3</span><span class="sxs-lookup"><span data-stu-id="023d7-163">P0P3</span></span>

* <span data-ttu-id="023d7-164">Post Office Protocol Version 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="023d7-164">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="023d7-165">最小 8.1 KB と 1.4 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="023d7-165">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="023d7-166">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-166">Client support</span></span>
* <span data-ttu-id="023d7-167">直感的な P0P3 API: *nx_pop3_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-167">Intuitive P0P3 APIs: *nx_pop3_\**</span></span>

### <a name="telnet"></a><span data-ttu-id="023d7-168">TELNET</span><span class="sxs-lookup"><span data-stu-id="023d7-168">TELNET</span></span>

* <span data-ttu-id="023d7-169">最小 0.5 KB と 0.3 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="023d7-169">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="023d7-170">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-170">Client and server support</span></span>
* <span data-ttu-id="023d7-171">直感的な Telnet API: *nx_telnet_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-171">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="023d7-172">FTP、TFTP</span><span class="sxs-lookup"><span data-stu-id="023d7-172">FTP, TFTP</span></span>

* <span data-ttu-id="023d7-173">ファイル転送プロトコル (FTP)</span><span class="sxs-lookup"><span data-stu-id="023d7-173">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="023d7-174">簡易ファイル転送プロトコル (TFTP)</span><span class="sxs-lookup"><span data-stu-id="023d7-174">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="023d7-175">FTP 最小 1.8 KB から 7.2 KB のフラッシュ、0.6 KB から 2.1 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="023d7-175">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="023d7-176">TFTP 最小 1.7 KB から 2.4 KB のフラッシュ、0.3 KB から 1.8 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="023d7-176">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="023d7-177">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-177">Client and server support</span></span>
* <span data-ttu-id="023d7-178">直感的な FTP および TFTP API: *nx_ftp_\** または *nx_tftp_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-178">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="023d7-179">PPP、PPPoE</span><span class="sxs-lookup"><span data-stu-id="023d7-179">PPP, PPPoE</span></span>

* <span data-ttu-id="023d7-180">Point-to-Point プロトコル (PPP)</span><span class="sxs-lookup"><span data-stu-id="023d7-180">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="023d7-181">Point-to-Point Protocol over Ethernet (PPPoE)</span><span class="sxs-lookup"><span data-stu-id="023d7-181">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="023d7-182">最小 7.1 KB と 3.8 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="023d7-182">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="023d7-183">直感的な PPP API: *nx_ppp_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-183">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="023d7-184">PPPoE は、Azure RTOS NetX Duo でのみ使用可能</span><span class="sxs-lookup"><span data-stu-id="023d7-184">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="023d7-185">SNTP</span><span class="sxs-lookup"><span data-stu-id="023d7-185">SNTP</span></span>

* <span data-ttu-id="023d7-186">Simple Network Time Protocol (SNTP)</span><span class="sxs-lookup"><span data-stu-id="023d7-186">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="023d7-187">最小 4 KB および 0.5 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="023d7-187">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="023d7-188">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-188">Client support</span></span>
* <span data-ttu-id="023d7-189">直感的な SNTP API: *nx_sntp_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-189">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-duo-api"></a><span data-ttu-id="023d7-190">Azure RTOS NetX Duo API</span><span class="sxs-lookup"><span data-stu-id="023d7-190">Azure RTOS NetX Duo API</span></span>

* <span data-ttu-id="023d7-191">直感的で一貫性のある API</span><span class="sxs-lookup"><span data-stu-id="023d7-191">Intuitive and consistent API</span></span>
* <span data-ttu-id="023d7-192">名詞 - 動詞の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="023d7-192">Noun-verb naming convention</span></span>
* <span data-ttu-id="023d7-193">高速のゼロコピー API 実装</span><span class="sxs-lookup"><span data-stu-id="023d7-193">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="023d7-194">すべての API の先頭を <i>nx_\*</i> にして、Azure RTOS NetX として簡単に識別</span><span class="sxs-lookup"><span data-stu-id="023d7-194">All APIs have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="023d7-195">ブロックしている API にオプションのスレッド タイムアウトがある</span><span class="sxs-lookup"><span data-stu-id="023d7-195">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="023d7-196">詳細については、[Azure RTOS NetX Duo のユーザー ガイド](about-this-guide.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="023d7-196">See [Azure RTOS NetX Duo User Guide](about-this-guide.md) for more details</span></span>
* <span data-ttu-id="023d7-197">レガシ ソケット コードを移植するためのオプションの BSD レイヤー</span><span class="sxs-lookup"><span data-stu-id="023d7-197">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="023d7-198">IGMP</span><span class="sxs-lookup"><span data-stu-id="023d7-198">IGMP</span></span>

* <span data-ttu-id="023d7-199">インターネット グループ管理プロトコル (IGMP)</span><span class="sxs-lookup"><span data-stu-id="023d7-199">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="023d7-200">最小 2.5 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="023d7-200">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="023d7-201">IPv4 マルチキャスト グループのサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-201">IPv4 multicast group support</span></span>
* <span data-ttu-id="023d7-202">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="023d7-202">IXIA IxANVL validated</span></span>
* <span data-ttu-id="023d7-203">オプションの IGMP 統計情報</span><span class="sxs-lookup"><span data-stu-id="023d7-203">Optional IGMP statistics</span></span>
* <span data-ttu-id="023d7-204">Azure RTOS ThreadX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="023d7-204">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="023d7-205">直感的な IGMP API: *nx_igmp_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-205">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="023d7-206">Azure RTOS NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="023d7-206">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="023d7-207">データグラム トランスポート層セキュリティ (DTLS) 1.0 および 1.2</span><span class="sxs-lookup"><span data-stu-id="023d7-207">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="023d7-208">最小 11 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="023d7-208">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="023d7-209">高速、ソフトウェア RSA 2048 ビットキーのサイズ ～ 1 秒 @120MHz</span><span class="sxs-lookup"><span data-stu-id="023d7-209">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="023d7-210">合理化された X.509 実装</span><span class="sxs-lookup"><span data-stu-id="023d7-210">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="023d7-211">Azure RTOS NetX Duo UDP ソケットと完全に統合</span><span class="sxs-lookup"><span data-stu-id="023d7-211">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="023d7-212">ハードウェア暗号化のサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-212">Hardware Crypto Support</span></span>
* <span data-ttu-id="023d7-213">ソフトウェアの暗号化のサポート: RSA (すべてのキー サイズ)、AES、DES/3DES、ECC、HMAC、MD5、SHA-1、SHA-2 (SHA-224、SHA-256、SHA-384、SHA-512)</span><span class="sxs-lookup"><span data-stu-id="023d7-213">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="023d7-214">ECDSA (署名) と ECDH (暗号化) を使用した楕円曲線暗号 (ECC)、P 曲線 192/224/256/384/521 を含む</span><span class="sxs-lookup"><span data-stu-id="023d7-214">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="023d7-215">暗号化キーのサポート (ハードウェアに依存)</span><span class="sxs-lookup"><span data-stu-id="023d7-215">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="023d7-216">Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="023d7-216">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="023d7-217">トランスポート層セキュリティ (TLS) 1.0、1.1、および 1.2</span><span class="sxs-lookup"><span data-stu-id="023d7-217">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="023d7-218">最小 8.8 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="023d7-218">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="023d7-219">高速、ソフトウェア RSA 2048 ビットキーのサイズ ～ 1 秒 @120MHz</span><span class="sxs-lookup"><span data-stu-id="023d7-219">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="023d7-220">合理化された X.509 実装</span><span class="sxs-lookup"><span data-stu-id="023d7-220">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="023d7-221">Azure RTOS NetX Duo TCP ソケットと完全に統合</span><span class="sxs-lookup"><span data-stu-id="023d7-221">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="023d7-222">ハードウェア暗号化のサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-222">Hardware Crypto Support</span></span>
* <span data-ttu-id="023d7-223">ソフトウェアの暗号化のサポート: RSA (すべてのキー サイズ)、AES、DES/3DES、ECC、HMAC、MD5、SHA-1、SHA-2 (SHA-224、SHA-256、SHA-384、SHA-512)</span><span class="sxs-lookup"><span data-stu-id="023d7-223">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="023d7-224">ECDSA (署名) と ECDH (暗号化) を使用した楕円曲線暗号 (ECC)、P 曲線 192/224/256/384/521 を含む</span><span class="sxs-lookup"><span data-stu-id="023d7-224">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="023d7-225">暗号化キーのサポート (ハードウェアに依存)</span><span class="sxs-lookup"><span data-stu-id="023d7-225">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="023d7-226">ICMP</span><span class="sxs-lookup"><span data-stu-id="023d7-226">ICMP</span></span>

* <span data-ttu-id="023d7-227">インターネット制御メッセージ プロトコル (ICMP)</span><span class="sxs-lookup"><span data-stu-id="023d7-227">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="023d7-228">最小 2.5 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="023d7-228">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="023d7-229">IPv4 および IPv6 のサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-229">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="023d7-230">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="023d7-230">IXIA IxANVL validated</span></span>
* <span data-ttu-id="023d7-231">ping 要求と ping 応答</span><span class="sxs-lookup"><span data-stu-id="023d7-231">Ping request and ping response</span></span>
* <span data-ttu-id="023d7-232">ping 要求に対するオプションのスレッドの中断</span><span class="sxs-lookup"><span data-stu-id="023d7-232">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="023d7-233">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="023d7-233">Optional timeout on all suspension</span></span>
* <span data-ttu-id="023d7-234">オプションの ICMP 統計情報</span><span class="sxs-lookup"><span data-stu-id="023d7-234">Optional ICMP statistics</span></span>
* <span data-ttu-id="023d7-235">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="023d7-235">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="023d7-236">直感的な ICMP API: *nx_icmp_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-236">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="023d7-237">UDP</span><span class="sxs-lookup"><span data-stu-id="023d7-237">UDP</span></span>

* <span data-ttu-id="023d7-238">ユーザー データグラム プロトコル (UDP)</span><span class="sxs-lookup"><span data-stu-id="023d7-238">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="023d7-239">最小 2.5 KB のフラッシュ、ソケットあたり 124 ソケット バイトの RAM</span><span class="sxs-lookup"><span data-stu-id="023d7-239">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="023d7-240">高速でほぼワイヤスピードの TCP パケット処理:</span><span class="sxs-lookup"><span data-stu-id="023d7-240">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="023d7-241">RX 95 Mbps (100 Mbps イーサネット)、MCU @100MHz、14% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="023d7-241">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="023d7-242">TX 94 Mbps (100 Mbps イーサネット)、MCU @100MHz、10% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="023d7-242">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="023d7-243">UDP Fast Path™ テクノロジ</span><span class="sxs-lookup"><span data-stu-id="023d7-243">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="023d7-244">UDP の数に制限なし</span><span class="sxs-lookup"><span data-stu-id="023d7-244">No limits on the number of UDP</span></span>
* <span data-ttu-id="023d7-245">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="023d7-245">IXIA IxANVL validated</span></span>
* <span data-ttu-id="023d7-246">ソケット受信時のオプションによる中断</span><span class="sxs-lookup"><span data-stu-id="023d7-246">Optional suspension on socket receive</span></span>
* <span data-ttu-id="023d7-247">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="023d7-247">Optional timeout on all suspension</span></span>
* <span data-ttu-id="023d7-248">オプションの UDP 統計情報</span><span class="sxs-lookup"><span data-stu-id="023d7-248">Optional UDP statistics</span></span>
* <span data-ttu-id="023d7-249">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="023d7-249">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="023d7-250">直感的な UDP API: *nx_udp_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-250">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="023d7-251">TCP</span><span class="sxs-lookup"><span data-stu-id="023d7-251">TCP</span></span>

* <span data-ttu-id="023d7-252">伝送制御プロトコル (TCP)</span><span class="sxs-lookup"><span data-stu-id="023d7-252">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="023d7-253">最小 10.5 K8 から 12.5 KB のフラッシュ、ソケットあたり 280 バイトの RAM</span><span class="sxs-lookup"><span data-stu-id="023d7-253">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="023d7-254">高速でほぼワイヤスピードの TCP パケット処理:</span><span class="sxs-lookup"><span data-stu-id="023d7-254">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="023d7-255">RX 93 Mbps (100 Mbps イーサネット)、MCU @100MHz、20% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="023d7-255">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="023d7-256">TX 94 Mbps (100 Mbps イーサネット)、MCU @100MHz、27% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="023d7-256">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="023d7-257">信頼性の高い接続</span><span class="sxs-lookup"><span data-stu-id="023d7-257">Reliable connection</span></span>
* <span data-ttu-id="023d7-258">TCP ソケット数に制限なし</span><span class="sxs-lookup"><span data-stu-id="023d7-258">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="023d7-259">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="023d7-259">IXIA IxANVL validated</span></span>
* <span data-ttu-id="023d7-260">ソケットの受信/送信でオプションの中断</span><span class="sxs-lookup"><span data-stu-id="023d7-260">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="023d7-261">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="023d7-261">Optional timeout on all suspension</span></span>
* <span data-ttu-id="023d7-262">オプションの TCP 統計情報</span><span class="sxs-lookup"><span data-stu-id="023d7-262">Optional TCP statistics</span></span>
* <span data-ttu-id="023d7-263">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="023d7-263">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="023d7-264">直感的な TCP API: *nx_tcp_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-264">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="023d7-265">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="023d7-265">ARP/RARP</span></span>

* <span data-ttu-id="023d7-266">アドレス解決プロトコル (ARP)</span><span class="sxs-lookup"><span data-stu-id="023d7-266">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="023d7-267">逆アドレス解決プロトコル (RARP)</span><span class="sxs-lookup"><span data-stu-id="023d7-267">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="023d7-268">最小 1.7 KB のフラッシュ、RAM サイズ</span><span class="sxs-lookup"><span data-stu-id="023d7-268">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="023d7-269">32 ビット IPv4 と 48 ビット MAC アドレスの動的な解決</span><span class="sxs-lookup"><span data-stu-id="023d7-269">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="023d7-270">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="023d7-270">IXIA IxANVL validated</span></span>
* <span data-ttu-id="023d7-271">柔軟なユーザー定義の ARP キャッシュ</span><span class="sxs-lookup"><span data-stu-id="023d7-271">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="023d7-272">Gratuitous ARP サポート</span><span class="sxs-lookup"><span data-stu-id="023d7-272">Gratuitous ARP support</span></span>
* <span data-ttu-id="023d7-273">アプリケーションによって決定されるオプションの ARP/RARP 統計</span><span class="sxs-lookup"><span data-stu-id="023d7-273">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="023d7-274">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="023d7-274">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="023d7-275">直感的な ARP/RARP API: *nx_arp_\** 、*nx_rarp_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-275">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="023d7-276">IPv4 および IPv6</span><span class="sxs-lookup"><span data-stu-id="023d7-276">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="023d7-277">インターネット プロトコル (IP)●いんたーねっとぷろとこる(ip)○</span><span class="sxs-lookup"><span data-stu-id="023d7-277">Internet Protocol (IP)</span></span>
* <span data-ttu-id="023d7-278">最小 3.5 KB から 8.5 KB のフラッシュ、2 KB から 3 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="023d7-278">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="023d7-279">Piconet™ アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="023d7-279">Piconet™ architecture</span></span>
* <span data-ttu-id="023d7-280">高速でほぼワイヤスピードのパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="023d7-280">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="023d7-281">複数インターフェイスのサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-281">Multiple interface support</span></span>
* <span data-ttu-id="023d7-282">マルチホーム サポート</span><span class="sxs-lookup"><span data-stu-id="023d7-282">Multihomed support</span></span>
* <span data-ttu-id="023d7-283">静的ルーティングのサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-283">Static routing support</span></span>
* <span data-ttu-id="023d7-284">IP の断片化/再構築のサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-284">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="023d7-285">IPv4 および IPv6 アドレスのサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-285">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="023d7-286">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="023d7-286">IXIA IxANVL validated</span></span>
* <span data-ttu-id="023d7-287">フェーズ II IPv6 対応ロゴ認定</span><span class="sxs-lookup"><span data-stu-id="023d7-287">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="023d7-288">オプションの IP 統計情報</span><span class="sxs-lookup"><span data-stu-id="023d7-288">Optional IP statistics</span></span>
* <span data-ttu-id="023d7-289">明確に定義された直観的な物理レイヤー ドライバー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="023d7-289">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="023d7-290">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="023d7-290">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="023d7-291">直感的な IP レイヤー API: *nx_ip_\** 、*nxd_ip_\** 、*nxd_ipv6_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-291">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="023d7-292">TUV および UL による IEC 61508 SIL 4、IEC 62304 クラス C、ISO 26262 ASIL D、および EN 50128 SW-SIL4 に対する事前認定</span><span class="sxs-lookup"><span data-stu-id="023d7-292">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="023d7-293">Azure RTOS NetX Secure IPSEC</span><span class="sxs-lookup"><span data-stu-id="023d7-293">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="023d7-294">インターネット プロトコル セキュリティ (IPSEC)</span><span class="sxs-lookup"><span data-stu-id="023d7-294">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="023d7-295">IP レイヤー</span><span class="sxs-lookup"><span data-stu-id="023d7-295">IP layer</span></span>
* <span data-ttu-id="023d7-296">ハードウェア暗号化のサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-296">Hardware crypto support</span></span>
* <span data-ttu-id="023d7-297">ソフトウェア暗号化のサポート (以下を含む):</span><span class="sxs-lookup"><span data-stu-id="023d7-297">Software crypto support, including:</span></span>
    * <span data-ttu-id="023d7-298">DES、3DES</span><span class="sxs-lookup"><span data-stu-id="023d7-298">DES, 3DES</span></span>
    * <span data-ttu-id="023d7-299">AES</span><span class="sxs-lookup"><span data-stu-id="023d7-299">AES</span></span>
    * <span data-ttu-id="023d7-300">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="023d7-300">HMAC-MD5</span></span>
    * <span data-ttu-id="023d7-301">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="023d7-301">HMAC-SHA1</span></span>
* <span data-ttu-id="023d7-302">インターネット キー交換 (IKE) バージョン 2 のサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-302">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="023d7-303">直感的な IPsec API: *nx_ipsec_\**</span><span class="sxs-lookup"><span data-stu-id="023d7-303">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="023d7-304">IPsec は、Azure RTOS NetX Duo でのみ使用可能</span><span class="sxs-lookup"><span data-stu-id="023d7-304">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="small-footprint"></a><span data-ttu-id="023d7-305">小さいフットプリント</span><span class="sxs-lookup"><span data-stu-id="023d7-305">Small-footprint</span></span>

<span data-ttu-id="023d7-306">Azure RTOS NetX Duo では、基本的な IP および UDP のサポートに、9 KB から 15 KB の非常に小さなフットプリントが実現されています。</span><span class="sxs-lookup"><span data-stu-id="023d7-306">Azure RTOS NetX Duo has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="023d7-307">TCP 機能を使用するには、追加で 10 KB から 13 KB の命令領域メモリが必要です。</span><span class="sxs-lookup"><span data-stu-id="023d7-307">An additional 10 KB to 13 KB of instruction area memory is needed for TCP functionality.</span></span> <span data-ttu-id="023d7-308">Azure RTOS NetX Duo の RAM の使用率は、通常、2.6 KB から 3.6 KB に、アプリケーションによって定義されるパケット プール メモリを加えた範囲になります。</span><span class="sxs-lookup"><span data-stu-id="023d7-308">Azure RTOS NetX Duo RAM usage typically ranges from 2.6 KB to 3.6 KB plus the packet pool memory, which is defined by the application.</span></span> <span data-ttu-id="023d7-309">Azure RTOS ThreadX と同様に、Azure RTOS NetX Duo のサイズは、アプリケーションで使用されるサービスに基づいて自動的にスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="023d7-309">Like Azure RTOS ThreadX, the size of Azure RTOS NetX Duo automatically scales based on the services used by the application.</span></span> <span data-ttu-id="023d7-310">これにより、複雑な構成やビルド パラメーターが実質的に不要になるため、開発者の作業がより簡単になります。</span><span class="sxs-lookup"><span data-stu-id="023d7-310">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="023d7-311">高速実行</span><span class="sxs-lookup"><span data-stu-id="023d7-311">Fast execution</span></span>

<span data-ttu-id="023d7-312">Azure RTOS NetX Duo は、Azure RTOS ThreadX と高度に統合された、ゼロコピーのパケット送信/受信実装を提供し、最速のパフォーマンスを実現します。</span><span class="sxs-lookup"><span data-stu-id="023d7-312">Azure RTOS NetX Duo provides a zero-copy packet send/receive implementation, highly integrated with Azure RTOS ThreadX, to achieve the fastest possible performance.</span></span> <span data-ttu-id="023d7-313">たとえば、Azure RTOS NetX Duo は、通常、プロセッサ サイクルのごく一部のみを使用しながら、80 MHz (またはそれ以下の) プロセッサでほぼワイヤスピードのデータ転送を実現します。</span><span class="sxs-lookup"><span data-stu-id="023d7-313">For example, Azure RTOS NetX Duo can typically achieve near wirespeed data transfers on an 80 MHz (or less) processor, while using only a small percentage of the processor cycles.</span></span>

## <a name="simple-easy-to-use"></a><span data-ttu-id="023d7-314">シンプルで優れた操作性</span><span class="sxs-lookup"><span data-stu-id="023d7-314">Simple, easy-to-use</span></span>

<span data-ttu-id="023d7-315">Azure RTOS NetX Duo API は、直感的でわかりやすく、高い機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="023d7-315">The Azure RTOS NetX Duo API is intuitive, straightforward,  and highly functional.</span></span>

<span data-ttu-id="023d7-316">API 名は、略語や、他のネットワーク製品で一般的な大幅に省略された名前ではなく、実際の言葉で構成されています。</span><span class="sxs-lookup"><span data-stu-id="023d7-316">The API names are made of real words and not the “alphabet soup” or highly abbreviated names that are so common in other networking products.</span></span> <span data-ttu-id="023d7-317">すべての Azure RTOS NetX Duo API は、先頭に *nx_* が付き、その後に名詞 - 動詞の名前付け規則が続きます。</span><span class="sxs-lookup"><span data-stu-id="023d7-317">All Azure RTOS NetX Duo APIs have a leading *nx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="023d7-318">さらに、API 全体に機能的な一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="023d7-318">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="023d7-319">たとえば、中断されるすべての API 関数には、同じ方法で動作するオプションのタイムアウトがあります。</span><span class="sxs-lookup"><span data-stu-id="023d7-319">For example, all API functions that suspend have an optional timeout that operates in an identical manner.</span></span>

<span data-ttu-id="023d7-320">レガシ アプリケーションに対しては、Azure RTOS NetX Duo で追加の BSD ソケット互換レイヤーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="023d7-320">For legacy applications, Azure RTOS NetX Duo offers an additional BSD socket compatible layer.</span></span> <span data-ttu-id="023d7-321">このレイヤーは、開発者が大規模なネットワーク アプリケーションを簡単に移行するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="023d7-321">This layer helps developers migrate large networking applications with ease.</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="023d7-322">高い安全性</span><span class="sxs-lookup"><span data-stu-id="023d7-322">Safe and secure</span></span>

<span data-ttu-id="023d7-323">Azure RTOS NetX Duo はセキュリティで保護されています。</span><span class="sxs-lookup"><span data-stu-id="023d7-323">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="023d7-324">このセキュリティは、IPsec、SSL、TLS、DTLS などのアドオン セキュリティ製品を通じて提供されます。</span><span class="sxs-lookup"><span data-stu-id="023d7-324">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="023d7-325">また、アプリケーションでは Azure RTOS NetX Duo へのすべての外部アクセスを完全に制御できるため、セキュリティ上のリスクをより簡単に判断できます。</span><span class="sxs-lookup"><span data-stu-id="023d7-325">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="023d7-326">Microsoft Azure RTOS には、通信をセキュリティで保護し、基になる MCU/MPU ハードウェア保護メカニズムを使用してコードとデータの分離を作成するためのコンポーネントを含む OEM があります。</span><span class="sxs-lookup"><span data-stu-id="023d7-326">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="023d7-327">特定のユース ケースに関連して進化し続けるセキュリティ要件をデバイスが完全に満たすようにすることは、最終的には、デバイス ビルダーの責任です。</span><span class="sxs-lookup"><span data-stu-id="023d7-327">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="023d7-328">TUV と UL による多くの安全性標準による事前認定</span><span class="sxs-lookup"><span data-stu-id="023d7-328">Pre-certified  by TUV and UL to many safety standards</span></span>

<span data-ttu-id="023d7-329">Azure RTOS NetX Duo は、IEC-61508 SIL 4、IEC-62304 SW セーフティ クラス C、ISO 26262 ASIL D、および EN 50128 に従って、安全性が重要なシステムでの使用を SGS-TUV Saar によって認定されています。</span><span class="sxs-lookup"><span data-stu-id="023d7-329">Azure RTOS NetX Duo has been certified by SGS-TUV  Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="023d7-330">この認定により、「電気、電子、プログラマブル電子安全関連系の機能安全」に関する IEC-61508、IEC-62304、ISO 26262、および EN 50128 の最高の安全性整合性レベルに対応する安全性関連ソフトウェアの開発で Azure RTOS NetX Duo を使用できることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="023d7-330">The certification confirms that Azure RTOS NetX Duo can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="023d7-331">ドイツの SGS-Group と TUV Saarland の共同事業を通じて結成された SGS-TUV Saar は、世界中の安全関連システムのための組み込みソフトウェアのテスト、監査、検証、認定を行う、世界有数の公認された独立系企業になりました。</span><span class="sxs-lookup"><span data-stu-id="023d7-331">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying, and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="023d7-332">工業安全規格の IEC 61508 と、それから派生したすべての標準 (IEC-62304、ISO 26262 および EN 50128 を含む) は、電気・電子・プログラマブル電子安全関連の医療デバイス、プロセス制御システム、工業機械、自動車および鉄道制御システムの機能安全を保証するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="023d7-332">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

:::image type="content" source="media/overview-netx-duo/partener-logo-sgs-tuv-saar.png" alt-text="SGS-TUV 認定":::

<span data-ttu-id="023d7-334">Azure RTOS NetX Duo は、プログラム可能なコンポーネント内のソフトウェアに対する UL 60730-1 付属文書 H、CSA E60730-1 付属文書 H、IEC 60730-1 付属文書 H、UL 60335-1 付属文書 R、IEC 60335-1 付属文書 R、UL 1998 の各安全標準に準拠しているものとして UL によって承認されています。</span><span class="sxs-lookup"><span data-stu-id="023d7-334">Azure RTOS NetX Duo has been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="023d7-335">UL は、独立した安全科学のグローバル企業であり、電気の公的な選定からサステナビリティ、再生可能エネルギー、およびナノテクノロジーにおける革新まで、さまざまな安全性ソリューションの革新を 1 世紀以上にわたって専門としてきました。</span><span class="sxs-lookup"><span data-stu-id="023d7-335">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

:::image type="content" source="media/overview-netx-duo/cru-logo-certification.png" alt-text="CRU UL 認定":::

<span data-ttu-id="023d7-337">TUV および UL 認定に関連付けられている成果物 (証明書、安全性マニュアル、テスト レポートなど) は、販売されています。</span><span class="sxs-lookup"><span data-stu-id="023d7-337">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

<span data-ttu-id="023d7-338">アプリケーションで追加の認定が必要な場合は、Microsoft を通じて認定サービスを利用し、実際のハードウェア プラットフォームを使用してさまざまな標準にターンキー認定を提供したり、アプリケーション コードをカバーしたりできます。</span><span class="sxs-lookup"><span data-stu-id="023d7-338">In cases where the application needs additional certification, a certification service is available through Microsoft for providing turn-key certification to various standards using the actual hardware platform and even covering the application code.</span></span> <span data-ttu-id="023d7-339">認定サービスの詳細については、お問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="023d7-339">Contact us for more details on our certification service.</span></span>

## <a name="eal4-common-criteria-security-certification"></a><span data-ttu-id="023d7-340">EAL4+ コモン クライテリア セキュリティ認定</span><span class="sxs-lookup"><span data-stu-id="023d7-340">EAL4+ Common Criteria security certification</span></span>

<span data-ttu-id="023d7-341">Azure RTOS は、EAL4+ のコモン クライテリア セキュリティ認定を達成しました。</span><span class="sxs-lookup"><span data-stu-id="023d7-341">Azure RTOS has achieved EAL4+ Common Criteria security certification.</span></span> <span data-ttu-id="023d7-342">評価対象 (TOE) は、Azure RTOS ThreadX、Azure RTOS NetX Duo、Azure RTOS NetX Secure TLS、および Azure RTOS NetX MQTT です。</span><span class="sxs-lookup"><span data-stu-id="023d7-342">The Target of Evalution (TOE) covers Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS, and Azure RTOS NetX MQTT.</span></span> <span data-ttu-id="023d7-343">これは、深い埋め込み型センサー、デバイス、エッジ ルーター、およびゲートウェイに必要な最も一般的な IoT プロトコルを表します。</span><span class="sxs-lookup"><span data-stu-id="023d7-343">This represents the most typical IoT protocols required by deeply embedded sensors, devices, edge routers, and gateways.</span></span>

:::image type="content" source="media/overview-netx-duo/eal-logo-certification.png" alt-text="EAL 認定":::

<span data-ttu-id="023d7-345">Microsoft Azure RTOS SC セキュリティ認定に使用される IT セキュリティ評価機関は Brightsight BV で、証明機関は SERTIT です。</span><span class="sxs-lookup"><span data-stu-id="023d7-345">The IT Security Evaluation Facility used for the Microsoft Azure RTOS SC security certification is Brightsight BV and the Certification Authority is SERTIT.</span></span>

## <a name="fips-140-2-validated"></a><span data-ttu-id="023d7-346">FIPS 140-2 の検証</span><span class="sxs-lookup"><span data-stu-id="023d7-346">FIPS 140-2 Validated</span></span>

<span data-ttu-id="023d7-347">Azure RTOS NetX Crypto ライブラリは、暗号化モジュールの要件を指定する、Federal Information Processing Standards 140-2 (FIPS 140-2) のソフトウェアの認定を受けています。</span><span class="sxs-lookup"><span data-stu-id="023d7-347">Azure RTOS NetX Crypto libraries have achieved Federal Information Processing Standardization 140-2 (FIPS 140-2) Certification for software, which specifies requirements for cryptography modules.</span></span> <span data-ttu-id="023d7-348">FIPS 140-2 では、暗号化ベースのセキュリティを使用するすべての連邦政府機関および部門が、暗号化の強度と機能に関連する特定の標準を満たすことが求められています。</span><span class="sxs-lookup"><span data-stu-id="023d7-348">FIPS 140-2 requires all federal government agencies and departments that use cryptographic-based security to meet specific standards related to encryption strength and capabilities.</span></span> <span data-ttu-id="023d7-349">これらの暗号化ベースのセキュリティ標準は、カナダと欧州連合でも承認されています。</span><span class="sxs-lookup"><span data-stu-id="023d7-349">These cryptographic-based security standards are also recognized in Canada and the European Union.</span></span>

<span data-ttu-id="023d7-350">Azure RTOS NetX Crypt ライブラリに使用される情報セキュリティ評価ラボは atsec でした。証明機関は米国国立標準技術研究所 (NIST) です。</span><span class="sxs-lookup"><span data-stu-id="023d7-350">The Information Security evaluation lab used for Azure RTOS NetX Crypto libraries was atsec and the certification authority is The National Institute of Standards and Technology (NIST).</span></span> <span data-ttu-id="023d7-351">詳細については、[NIST の Web サイト](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="023d7-351">Review the [NIST website](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394) for additional details.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="023d7-352">相互運用性の検証</span><span class="sxs-lookup"><span data-stu-id="023d7-352">Interoperability verification</span></span>

<span data-ttu-id="023d7-353">NetX Duo は RFC 標準に準拠し、ほとんどのベンダーのデバイスとの完全な相互運用性を提供します。</span><span class="sxs-lookup"><span data-stu-id="023d7-353">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![IPv6 対応のロゴ](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="023d7-355">Azure RTOS NetX Duo は、厳密な IPv6 対応のロゴ認定を達成する唯一の埋め込み型 TCP/IP スタックです。このロゴは、準拠と相互運用性のテストに合格し、IPv6 フォーラムによって管理および検証されていることを証明します。</span><span class="sxs-lookup"><span data-stu-id="023d7-355">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="023d7-356">NetX Duo では、NetX Duo コア TCP/IP プロトコルの実装に対して業界標準の IxANVL (自動ネットワーク検証ライブラリ) も利用されています。</span><span class="sxs-lookup"><span data-stu-id="023d7-356">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="023d7-357">包括的な IoT ソリューション</span><span class="sxs-lookup"><span data-stu-id="023d7-357">Comprehensive IoT solution</span></span>

<span data-ttu-id="023d7-358">Azure RTOS NetX Duo では、基本的な IP および UDP のサポートに、9 KB から 15 KB の非常に小さなフットプリントが実現されています。</span><span class="sxs-lookup"><span data-stu-id="023d7-358">Azure RTOS NetX Duo has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="023d7-359">NetX Duo では、深い埋め込み型 IoT アプリケーション向けの最も包括的な TCP/IP ネットワークの 1 つが提供されます。</span><span class="sxs-lookup"><span data-stu-id="023d7-359">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="023d7-360">このサポートには、次のアドオン プロトコル製品が含まれています。</span><span class="sxs-lookup"><span data-stu-id="023d7-360">This support includes the following add-on protocol products:</span></span>

<span data-ttu-id="023d7-361">MQTT、CoAP、LWM2M、6LoWPAN、SSL/TLS/DTLS、IPsec、AutoIP、DHCP、DNS、mDNS、DNS-SD、FTP、HTTP、IPsec、NAT、POP3、PPP、PPPoE、SMTP、SNMP v1/2/3、Telnet、TFTP</span><span class="sxs-lookup"><span data-stu-id="023d7-361">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="023d7-362">高度なテクノロジ</span><span class="sxs-lookup"><span data-stu-id="023d7-362">Advanced technology</span></span>

<span data-ttu-id="023d7-363">Azure RTOS NetX Duo は次の機能を備えた高度なテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="023d7-363">Azure RTOS NetX Duo is advanced technology that includes:</span></span>

* <span data-ttu-id="023d7-364">Piconet™ アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="023d7-364">Piconet™ architecture</span></span>
* <span data-ttu-id="023d7-365">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="023d7-365">Automatic scaling</span></span>
* <span data-ttu-id="023d7-366">UDP Fast-Path Technology™</span><span class="sxs-lookup"><span data-stu-id="023d7-366">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="023d7-367">柔軟なパケット管理</span><span class="sxs-lookup"><span data-stu-id="023d7-367">Flexible packet management</span></span>
* <span data-ttu-id="023d7-368">ゼロコピー API と実装</span><span class="sxs-lookup"><span data-stu-id="023d7-368">Zero-copy API and implementation</span></span>
* <span data-ttu-id="023d7-369">マルチホーム サポート</span><span class="sxs-lookup"><span data-stu-id="023d7-369">Multihomed support</span></span>
* <span data-ttu-id="023d7-370">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="023d7-370">Optional timeout on all suspension</span></span>
* <span data-ttu-id="023d7-371">静的ルーティングのサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-371">Static routing support</span></span>
* <span data-ttu-id="023d7-372">IPsec</span><span class="sxs-lookup"><span data-stu-id="023d7-372">IPsec</span></span>
* <span data-ttu-id="023d7-373">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="023d7-373">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="023d7-374">Azure RTOS TraceX システム分析のサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-374">Azure RTOS TraceX system analysis support</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="023d7-375">市場投入までの時間を短縮</span><span class="sxs-lookup"><span data-stu-id="023d7-375">Fastest time-to-market</span></span>

<span data-ttu-id="023d7-376">Azure RTOS NetX Duo は、簡単にインストール、学習、使用、デバッグ、検証、認定、保守を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="023d7-376">Azure RTOS NetX Duo is easy to install, learn, use, debug, verify, certify and maintain.</span></span> <span data-ttu-id="023d7-377">その結果、NetX Duo は、Broadcom や Gainspan などの多くの SoC を含む組み込み型 IoT デバイス向けの最も一般的な TCP/IP スタックの 1 つです。次の点に基づいて、市場投入までの時間を一貫して短く保つことができます。</span><span class="sxs-lookup"><span data-stu-id="023d7-377">As a result, NetX Duo is one of the most popular TCP/IP stacks for embedded IoT devices, including many SoCs from Broadcom, Gainspan, etc. Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="023d7-378">品質の高いドキュメント – [Azure RTOS NetX Duo のユーザー ガイド](about-this-guide.md)をご確認ください。</span><span class="sxs-lookup"><span data-stu-id="023d7-378">Quality documentation – please review our [Azure RTOS NetX Duo User Guide](about-this-guide.md) and see for yourself!</span></span>
* <span data-ttu-id="023d7-379">完全なソース コードを使用可能</span><span class="sxs-lookup"><span data-stu-id="023d7-379">Complete source code availability</span></span>
* <span data-ttu-id="023d7-380">使いやすい API</span><span class="sxs-lookup"><span data-stu-id="023d7-380">Easy-to-use API</span></span>
* <span data-ttu-id="023d7-381">包括的かつ高度な機能セット</span><span class="sxs-lookup"><span data-stu-id="023d7-381">Comprehensive and advanced feature set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="023d7-382">シンプルな 1 つのライセンス</span><span class="sxs-lookup"><span data-stu-id="023d7-382">One Simple License</span></span>

<span data-ttu-id="023d7-383">ソース コードの使用とテストに費用はかからず、事前にライセンスされたデバイスに展開する場合は、運用環境ライセンスにはコストがかかりません。その他のすべてのデバイスには、シンプルな年間ライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="023d7-383">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="023d7-384">完全な最高品質のソース コード</span><span class="sxs-lookup"><span data-stu-id="023d7-384">Full, highest-quality source code</span></span>

<span data-ttu-id="023d7-385">長年にわたり、Azure RTOS NetX Duo のソース コードは、品質と分かりやすさに一定の基準を設けてきました。</span><span class="sxs-lookup"><span data-stu-id="023d7-385">Throughout the years, Azure RTOS NetX Duo source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="023d7-386">また、ファイルごとに 1 つの関数を使用するという規則により、簡単にソースを移動できます。</span><span class="sxs-lookup"><span data-stu-id="023d7-386">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="023d7-387">最も一般的なアーキテクチャをサポート</span><span class="sxs-lookup"><span data-stu-id="023d7-387">Supports most popular architectures</span></span>

<span data-ttu-id="023d7-388">Azure RTOS NetX Duo は、すぐに利用可能で完全なテストとサポートが実現されている、最も一般的な 32/64 ビットのマイクロプロセッサで動作します。これには、次の高度なアーキテクチャが含まれます。</span><span class="sxs-lookup"><span data-stu-id="023d7-388">Azure RTOS NetX Duo runs on most popular 32/64-bit microprocessors out-of-the-box, fully tested and fully supported, including the following advanced architectures:</span></span>

<span data-ttu-id="023d7-389">**Analog Devices**: SHARC、Blackfin、CM4xx</span><span class="sxs-lookup"><span data-stu-id="023d7-389">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="023d7-390">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="023d7-390">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="023d7-391">**Ambiqmicro**: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="023d7-391">**Ambiqmicro**: pollo MCUs</span></span>

<span data-ttu-id="023d7-392">**ARM**: RM7、ARM9、ARM11、Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64 ビット/A7x 64 ビット/R4/R5、TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="023d7-392">**ARM**: RM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="023d7-393">**Cadence**: Xtensa、Diamond</span><span class="sxs-lookup"><span data-stu-id="023d7-393">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="023d7-394">**CEVA**: PSoC、PSoC 4、PSoC 5、PSoC 6、FM0+、FM3、MF4、WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="023d7-394">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="023d7-395">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="023d7-395">**Cypress**: RISC-V</span></span>

<span data-ttu-id="023d7-396">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="023d7-396">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="023d7-397">**Infineon**: XMC1000、XMC4000、TriCore</span><span class="sxs-lookup"><span data-stu-id="023d7-397">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="023d7-398">**Intel および Intel FPGA**: x36/Pentium、XScale、NIOS II、Cyclone、Arria 10</span><span class="sxs-lookup"><span data-stu-id="023d7-398">**Intel & Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="023d7-399">**Microchip**: AVR32、ARM7、ARM9、Cortex-M3/M4/M7、SAM3/4/7/9/A/C/D/E/G/L/SV、PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="023d7-399">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="023d7-400">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="023d7-400">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="023d7-401">**NXP**: LPC、ARM7、ARM9、PowerPC、68 K、i.MX、ColdFire、Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="023d7-401">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="023d7-402">**Renesas**: SH、HS、V850、RX、RZ、Synergy</span><span class="sxs-lookup"><span data-stu-id="023d7-402">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="023d7-403">**Silicon** Labs: EFM32</span><span class="sxs-lookup"><span data-stu-id="023d7-403">**Silicon** Labs: EFM32</span></span>

<span data-ttu-id="023d7-404">**Synopsys**: ARC 600、700、ARC EM、ARC HS</span><span class="sxs-lookup"><span data-stu-id="023d7-404">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="023d7-405">**ST**: STM32、ARM7、ARM9、Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="023d7-405">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="023d7-406">**Tl**: C5xxx、C6xxx、Stellaris、Sitara、Tiva-C</span><span class="sxs-lookup"><span data-stu-id="023d7-406">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="023d7-407">**Wave Computing**: MIPS32 4K、24 K、34 K、1004 K、MIPS64 5K、microAptiv、interAptiv、proAptiv、M-Class</span><span class="sxs-lookup"><span data-stu-id="023d7-407">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="023d7-408">**Xilinx**: MicroBlaze、PowerPC 405、ZYNQ、ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="023d7-408">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="023d7-409">*表示されるすべてのタイミングとサイズの数値は推定値であり、開発プラットフォームによって異なる場合があります。*</span><span class="sxs-lookup"><span data-stu-id="023d7-409">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>

## <a name="related-services"></a><span data-ttu-id="023d7-410">関連サービス</span><span class="sxs-lookup"><span data-stu-id="023d7-410">Related services</span></span>

<span data-ttu-id="023d7-411">Azure Security Center for IoT RTOS セキュリティ モジュールでは、Azure RTOS デバイス向けの包括的なセキュリティ ソリューションが提供されます。</span><span class="sxs-lookup"><span data-stu-id="023d7-411">The Azure Security Center for IoT RTOS security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="023d7-412">Azure RTOS のセキュリティ モジュールは、悪意のあるネットワーク アクティビティの検出、カスタム アラート ベースのデバイス動作での基準設定、およびデバイス セキュリティ検疫の強化に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="023d7-412">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="023d7-413">[Azure RTOS のセキュリティ モジュール](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos)の詳細を確認するか、[Azure RTOS 用セキュリティ モジュールの構成](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module)に関するクイックスタートを開始してください。</span><span class="sxs-lookup"><span data-stu-id="023d7-413">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

## <a name="next-steps"></a><span data-ttu-id="023d7-414">次のステップ</span><span class="sxs-lookup"><span data-stu-id="023d7-414">Next steps</span></span>

<span data-ttu-id="023d7-415">NetX Duo の詳細については、最初に、[Azure RTOS NetX Duo のユーザー ガイド](about-this-guide.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="023d7-415">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
