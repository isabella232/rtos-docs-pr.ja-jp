---
title: Azure RTOS NetX Duo を理解する
description: Azure RTOS NetX Duo は、深い埋め込み型のリアルタイム IoT アプリケーション用に特に設計された高度な商用 TCP/IP ネットワーク スタックです。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: e3fe3bcc602f409cc76f3be47aca865bf8116697
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171337"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="3f081-103">Azure RTOS NetX Duo の概要</span><span class="sxs-lookup"><span data-stu-id="3f081-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="3f081-104">Azure RTOS NetX Duo 埋め込み型 TCP/IP ネットワーク スタックは、深い埋め込み型のリアルタイム IoT アプリケーション専用に設計された、Microsoft が提供する高度な商用デュアル IPv4 および IPv6 TCP/IP ネットワーク スタックです。</span><span class="sxs-lookup"><span data-stu-id="3f081-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="3f081-105">NetX Duo は、コア ネットワーク プロトコル (IPv4、IPv6、TCP、UDP など) と、その他の高度なアドオン プロトコルの完全なスイートを埋め込み型アプリケーションに提供します。</span><span class="sxs-lookup"><span data-stu-id="3f081-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="3f081-106">Azure RTOS NetX Duo は、Azure RTOS NetX Secure IPsec や Azure RTOS NetX Secure SSL/TLS/DTLS を含む追加のアドオン セキュリティ製品を介してセキュリティを提供します。</span><span class="sxs-lookup"><span data-stu-id="3f081-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="3f081-107">これらすべてを小さなフットプリント、高速な処理、優れた使いやすさと組み合わせることで、Azure RTOS NetX Duo は、最も要求の厳しい埋め込み型 IoT アプリケーションに最適な選択肢となります。</span><span class="sxs-lookup"><span data-stu-id="3f081-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="3f081-108">API プロトコル</span><span class="sxs-lookup"><span data-stu-id="3f081-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="3f081-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="3f081-109">MQTT</span></span>

* <span data-ttu-id="3f081-110">Messaging Queue Telemetry Transport (MQTT)</span><span class="sxs-lookup"><span data-stu-id="3f081-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="3f081-111">最小 2.7 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="3f081-111">Minimal 2.7 KB FLASH</span></span>

### <a name="auto-ip"></a><span data-ttu-id="3f081-112">Auto IP</span><span class="sxs-lookup"><span data-stu-id="3f081-112">Auto IP</span></span>

* <span data-ttu-id="3f081-113">IPv4 アドレス自動割り当て</span><span class="sxs-lookup"><span data-stu-id="3f081-113">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="3f081-114">最小 1.2 KB、300 バイトの RAM</span><span class="sxs-lookup"><span data-stu-id="3f081-114">Minimal 1.2 KB, 300 bytes of RAM</span></span>

### <a name="http-https"></a><span data-ttu-id="3f081-115">HTTP、HTTPS</span><span class="sxs-lookup"><span data-stu-id="3f081-115">HTTP, HTTPS</span></span>

#### <a name="http-10"></a><span data-ttu-id="3f081-116">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="3f081-116">HTTP 1.0</span></span>

* <span data-ttu-id="3f081-117">ハイパーテキスト転送プロトコル (HTTP)</span><span class="sxs-lookup"><span data-stu-id="3f081-117">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="3f081-118">最小 2.8 KB から 4.8 KB のフラッシュ/0.4 KB から 1.0 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="3f081-118">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="3f081-119">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-119">Client and server support</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="3f081-120">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="3f081-120">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="3f081-121">ハイパーテキスト転送プロトコル (HTTP)</span><span class="sxs-lookup"><span data-stu-id="3f081-121">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="3f081-122">最小 3.0 KB から 9.5 KB のフラッシュ/0.5 KB から 2 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="3f081-122">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="3f081-123">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-123">Client and server support</span></span>
* <span data-ttu-id="3f081-124">複数の受信クライアント セッション</span><span class="sxs-lookup"><span data-stu-id="3f081-124">Multiple incoming client sessions</span></span>
* <span data-ttu-id="3f081-125">プレーンテキストと暗号化された HTTPS</span><span class="sxs-lookup"><span data-stu-id="3f081-125">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="3f081-126">永続的な接続のサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-126">Persistent connection support</span></span>
* <span data-ttu-id="3f081-127">マルチパート ファイルのアップロード</span><span class="sxs-lookup"><span data-stu-id="3f081-127">Multipart file upload</span></span>
* <span data-ttu-id="3f081-128">Azure RTOS NetX Secure TLS と完全に統合</span><span class="sxs-lookup"><span data-stu-id="3f081-128">Fully integrated with Azure RTOS NetX Secure TLS</span></span>

### <a name="smtp"></a><span data-ttu-id="3f081-129">SMTP</span><span class="sxs-lookup"><span data-stu-id="3f081-129">SMTP</span></span>

* <span data-ttu-id="3f081-130">簡易メール転送プロトコル (SMTP)</span><span class="sxs-lookup"><span data-stu-id="3f081-130">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="3f081-131">最小 4.1 KB と 0.6 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="3f081-131">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="3f081-132">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-132">Client support</span></span>

### <a name="dhcp"></a><span data-ttu-id="3f081-133">DHCP</span><span class="sxs-lookup"><span data-stu-id="3f081-133">DHCP</span></span>

* <span data-ttu-id="3f081-134">動的ホスト構成プロトコル (DHCP)</span><span class="sxs-lookup"><span data-stu-id="3f081-134">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="3f081-135">最小 3.6 KB から 4.6 KB のフラッシュ、2.7 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="3f081-135">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="3f081-136">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-136">Client and server support</span></span>
* <span data-ttu-id="3f081-137">IPv4 および IPv6 のサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-137">IPv4 and IPv6 support</span></span>

### <a name="nat"></a><span data-ttu-id="3f081-138">NAT</span><span class="sxs-lookup"><span data-stu-id="3f081-138">NAT</span></span>

* <span data-ttu-id="3f081-139">ネットワーク アドレス変換 (NAT)</span><span class="sxs-lookup"><span data-stu-id="3f081-139">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="3f081-140">最小 3.5 K6 と 0.6 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="3f081-140">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="3f081-141">IPv4 アドレスのサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-141">IPv4 address support</span></span>
* <span data-ttu-id="3f081-142">NAT は、Azure RTOS NetX Duo でのみ使用可能</span><span class="sxs-lookup"><span data-stu-id="3f081-142">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="3f081-143">SNMP</span><span class="sxs-lookup"><span data-stu-id="3f081-143">SNMP</span></span>

* <span data-ttu-id="3f081-144">簡易ネットワーク管理プロトコル (SNMP)</span><span class="sxs-lookup"><span data-stu-id="3f081-144">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="3f081-145">最小 10.9 KB と 2.6 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="3f081-145">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="3f081-146">VI、V2、V3 のエージェントのサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-146">Agent support for VI, V2, and V3</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="3f081-147">DNS、mDNS、DNS-SD</span><span class="sxs-lookup"><span data-stu-id="3f081-147">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="3f081-148">ドメイン ネーム システム (DNS)</span><span class="sxs-lookup"><span data-stu-id="3f081-148">Domain Name System (DNS)</span></span>
* <span data-ttu-id="3f081-149">マルチキャスト ドメイン ネーム システム (mDNS)</span><span class="sxs-lookup"><span data-stu-id="3f081-149">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="3f081-150">DNS ベースのサービス検出 (DNS-SD)</span><span class="sxs-lookup"><span data-stu-id="3f081-150">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="3f081-151">DNS 最小 2.4 KB から 3 KB のフラッシュ、1 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="3f081-151">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="3f081-152">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-152">Client support</span></span>
* <span data-ttu-id="3f081-153">mDNS と DNS-SD は、Azure RTOS NetX Duo でのみ使用可能</span><span class="sxs-lookup"><span data-stu-id="3f081-153">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="p0p3"></a><span data-ttu-id="3f081-154">P0P3</span><span class="sxs-lookup"><span data-stu-id="3f081-154">P0P3</span></span>

* <span data-ttu-id="3f081-155">Post Office Protocol Version 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="3f081-155">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="3f081-156">最小 8.1 KB と 1.4 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="3f081-156">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="3f081-157">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-157">Client support</span></span>

### <a name="telnet"></a><span data-ttu-id="3f081-158">Telnet</span><span class="sxs-lookup"><span data-stu-id="3f081-158">TELNET</span></span>

* <span data-ttu-id="3f081-159">最小 0.5 KB と 0.3 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="3f081-159">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="3f081-160">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-160">Client and server support</span></span>
* <span data-ttu-id="3f081-161">直感的な Telnet API: *nx_telnet_\**</span><span class="sxs-lookup"><span data-stu-id="3f081-161">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="3f081-162">FTP、TFTP</span><span class="sxs-lookup"><span data-stu-id="3f081-162">FTP, TFTP</span></span>

* <span data-ttu-id="3f081-163">ファイル転送プロトコル (FTP)</span><span class="sxs-lookup"><span data-stu-id="3f081-163">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="3f081-164">簡易ファイル転送プロトコル (TFTP)</span><span class="sxs-lookup"><span data-stu-id="3f081-164">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="3f081-165">FTP 最小 1.8 KB から 7.2 KB のフラッシュ、0.6 KB から 2.1 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="3f081-165">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="3f081-166">TFTP 最小 1.7 KB から 2.4 KB のフラッシュ、0.3 KB から 1.8 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="3f081-166">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="3f081-167">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-167">Client and server support</span></span>
* <span data-ttu-id="3f081-168">直感的な FTP および TFTP API: *nx_ftp_\** または *nx_tftp_\**</span><span class="sxs-lookup"><span data-stu-id="3f081-168">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="3f081-169">PPP、PPPoE</span><span class="sxs-lookup"><span data-stu-id="3f081-169">PPP, PPPoE</span></span>

* <span data-ttu-id="3f081-170">Point-to-Point プロトコル (PPP)</span><span class="sxs-lookup"><span data-stu-id="3f081-170">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="3f081-171">Point-to-Point Protocol over Ethernet (PPPoE)</span><span class="sxs-lookup"><span data-stu-id="3f081-171">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="3f081-172">最小 7.1 KB と 3.8 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="3f081-172">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="3f081-173">直感的な PPP API: *nx_ppp_\**</span><span class="sxs-lookup"><span data-stu-id="3f081-173">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="3f081-174">PPPoE は、Azure RTOS NetX Duo でのみ使用可能</span><span class="sxs-lookup"><span data-stu-id="3f081-174">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="3f081-175">SNTP</span><span class="sxs-lookup"><span data-stu-id="3f081-175">SNTP</span></span>

* <span data-ttu-id="3f081-176">Simple Network Time Protocol (SNTP)</span><span class="sxs-lookup"><span data-stu-id="3f081-176">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="3f081-177">最小 4 KB および 0.5 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="3f081-177">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="3f081-178">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-178">Client support</span></span>
* <span data-ttu-id="3f081-179">直感的な SNTP API: *nx_sntp_\**</span><span class="sxs-lookup"><span data-stu-id="3f081-179">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-duo-api"></a><span data-ttu-id="3f081-180">Azure RTOS NetX Duo API</span><span class="sxs-lookup"><span data-stu-id="3f081-180">Azure RTOS NetX Duo API</span></span>

* <span data-ttu-id="3f081-181">直感的で一貫性のある API</span><span class="sxs-lookup"><span data-stu-id="3f081-181">Intuitive and consistent API</span></span>
* <span data-ttu-id="3f081-182">名詞 - 動詞の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="3f081-182">Noun-verb naming convention</span></span>
* <span data-ttu-id="3f081-183">高速のゼロコピー API 実装</span><span class="sxs-lookup"><span data-stu-id="3f081-183">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="3f081-184">すべての API の先頭を <i>nx_\*</i> にして、Azure RTOS NetX として簡単に識別</span><span class="sxs-lookup"><span data-stu-id="3f081-184">All APIs have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="3f081-185">ブロックしている API にオプションのスレッド タイムアウトがある</span><span class="sxs-lookup"><span data-stu-id="3f081-185">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="3f081-186">詳細については、[Azure RTOS NetX Duo のユーザー ガイド](about-this-guide.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f081-186">See [Azure RTOS NetX Duo User Guide](about-this-guide.md) for more details</span></span>
* <span data-ttu-id="3f081-187">レガシ ソケット コードを移植するためのオプションの BSD レイヤー</span><span class="sxs-lookup"><span data-stu-id="3f081-187">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="3f081-188">IGMP</span><span class="sxs-lookup"><span data-stu-id="3f081-188">IGMP</span></span>

* <span data-ttu-id="3f081-189">インターネット グループ管理プロトコル (IGMP)</span><span class="sxs-lookup"><span data-stu-id="3f081-189">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="3f081-190">最小 2.5 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="3f081-190">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="3f081-191">IPv4 マルチキャスト グループのサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-191">IPv4 multicast group support</span></span>
* <span data-ttu-id="3f081-192">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="3f081-192">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3f081-193">オプションの IGMP 統計情報</span><span class="sxs-lookup"><span data-stu-id="3f081-193">Optional IGMP statistics</span></span>
* <span data-ttu-id="3f081-194">Azure RTOS ThreadX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="3f081-194">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="3f081-195">直感的な IGMP API: *nx_igmp_\**</span><span class="sxs-lookup"><span data-stu-id="3f081-195">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="3f081-196">Azure RTOS NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="3f081-196">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="3f081-197">データグラム トランスポート層セキュリティ (DTLS) 1.0 および 1.2</span><span class="sxs-lookup"><span data-stu-id="3f081-197">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="3f081-198">最小 11 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="3f081-198">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="3f081-199">高速、ソフトウェア RSA 2048 ビットキーのサイズ ～ 1 秒 @120MHz</span><span class="sxs-lookup"><span data-stu-id="3f081-199">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="3f081-200">合理化された X.509 実装</span><span class="sxs-lookup"><span data-stu-id="3f081-200">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="3f081-201">Azure RTOS NetX Duo UDP ソケットと完全に統合</span><span class="sxs-lookup"><span data-stu-id="3f081-201">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="3f081-202">ハードウェア暗号化のサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-202">Hardware Crypto Support</span></span>
* <span data-ttu-id="3f081-203">ソフトウェアの暗号化のサポート: RSA (すべてのキー サイズ)、AES、DES/3DES、ECC、HMAC、MD5、SHA-1、SHA-2 (SHA-224、SHA-256、SHA-384、SHA-512)</span><span class="sxs-lookup"><span data-stu-id="3f081-203">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="3f081-204">ECDSA (署名) と ECDH (暗号化) を使用した楕円曲線暗号 (ECC)、P 曲線 192/224/256/384/521 を含む</span><span class="sxs-lookup"><span data-stu-id="3f081-204">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="3f081-205">暗号化キーのサポート (ハードウェアに依存)</span><span class="sxs-lookup"><span data-stu-id="3f081-205">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="3f081-206">Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3f081-206">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="3f081-207">トランスポート層セキュリティ (TLS) 1.0、1.1、および 1.2</span><span class="sxs-lookup"><span data-stu-id="3f081-207">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="3f081-208">最小 8.8 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="3f081-208">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="3f081-209">高速、ソフトウェア RSA 2048 ビットキーのサイズ ～ 1 秒 @120MHz</span><span class="sxs-lookup"><span data-stu-id="3f081-209">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="3f081-210">合理化された X.509 実装</span><span class="sxs-lookup"><span data-stu-id="3f081-210">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="3f081-211">Azure RTOS NetX Duo TCP ソケットと完全に統合</span><span class="sxs-lookup"><span data-stu-id="3f081-211">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="3f081-212">ハードウェア暗号化のサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-212">Hardware Crypto Support</span></span>
* <span data-ttu-id="3f081-213">ソフトウェアの暗号化のサポート: RSA (すべてのキー サイズ)、AES、DES/3DES、ECC、HMAC、MD5、SHA-1、SHA-2 (SHA-224、SHA-256、SHA-384、SHA-512)</span><span class="sxs-lookup"><span data-stu-id="3f081-213">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="3f081-214">ECDSA (署名) と ECDH (暗号化) を使用した楕円曲線暗号 (ECC)、P 曲線 192/224/256/384/521 を含む</span><span class="sxs-lookup"><span data-stu-id="3f081-214">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="3f081-215">暗号化キーのサポート (ハードウェアに依存)</span><span class="sxs-lookup"><span data-stu-id="3f081-215">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="3f081-216">ICMP</span><span class="sxs-lookup"><span data-stu-id="3f081-216">ICMP</span></span>

* <span data-ttu-id="3f081-217">インターネット制御メッセージ プロトコル (ICMP)</span><span class="sxs-lookup"><span data-stu-id="3f081-217">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="3f081-218">最小 2.5 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="3f081-218">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="3f081-219">IPv4 および IPv6 のサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-219">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="3f081-220">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="3f081-220">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3f081-221">ping 要求と ping 応答</span><span class="sxs-lookup"><span data-stu-id="3f081-221">Ping request and ping response</span></span>
* <span data-ttu-id="3f081-222">ping 要求時のオプションのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="3f081-222">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="3f081-223">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="3f081-223">Optional timeout on all suspension</span></span>
* <span data-ttu-id="3f081-224">オプションの ICMP 統計情報</span><span class="sxs-lookup"><span data-stu-id="3f081-224">Optional ICMP statistics</span></span>
* <span data-ttu-id="3f081-225">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="3f081-225">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="3f081-226">直感的な ICMP API: *nx_icmp_\**</span><span class="sxs-lookup"><span data-stu-id="3f081-226">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="3f081-227">UDP</span><span class="sxs-lookup"><span data-stu-id="3f081-227">UDP</span></span>

* <span data-ttu-id="3f081-228">ユーザー データグラム プロトコル (UDP)</span><span class="sxs-lookup"><span data-stu-id="3f081-228">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="3f081-229">最小 2.5 KB のフラッシュ、ソケットあたり 124 ソケット バイトの RAM</span><span class="sxs-lookup"><span data-stu-id="3f081-229">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="3f081-230">高速でほぼワイヤスピードの TCP パケット処理:</span><span class="sxs-lookup"><span data-stu-id="3f081-230">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="3f081-231">RX 95 Mbps (100 Mbps イーサネット)、MCU @100MHz、14% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="3f081-231">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="3f081-232">TX 94 Mbps (100 Mbps イーサネット)、MCU @100MHz、10% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="3f081-232">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="3f081-233">UDP Fast Path™ テクノロジ</span><span class="sxs-lookup"><span data-stu-id="3f081-233">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="3f081-234">UDP の数に制限なし</span><span class="sxs-lookup"><span data-stu-id="3f081-234">No limits on the number of UDP</span></span>
* <span data-ttu-id="3f081-235">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="3f081-235">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3f081-236">ソケット受信時のオプションによる中断</span><span class="sxs-lookup"><span data-stu-id="3f081-236">Optional suspension on socket receive</span></span>
* <span data-ttu-id="3f081-237">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="3f081-237">Optional timeout on all suspension</span></span>
* <span data-ttu-id="3f081-238">オプションの UDP 統計情報</span><span class="sxs-lookup"><span data-stu-id="3f081-238">Optional UDP statistics</span></span>
* <span data-ttu-id="3f081-239">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="3f081-239">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="3f081-240">直感的な UDP API: *nx_udp_\**</span><span class="sxs-lookup"><span data-stu-id="3f081-240">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="3f081-241">TCP</span><span class="sxs-lookup"><span data-stu-id="3f081-241">TCP</span></span>

* <span data-ttu-id="3f081-242">伝送制御プロトコル (TCP)</span><span class="sxs-lookup"><span data-stu-id="3f081-242">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="3f081-243">最小 10.5 K8 から 12.5 KB のフラッシュ、ソケットあたり 280 バイトの RAM</span><span class="sxs-lookup"><span data-stu-id="3f081-243">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="3f081-244">高速でほぼワイヤスピードの TCP パケット処理:</span><span class="sxs-lookup"><span data-stu-id="3f081-244">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="3f081-245">RX 93 Mbps (100 Mbps イーサネット)、MCU @100MHz、20% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="3f081-245">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="3f081-246">TX 94 Mbps (100 Mbps イーサネット)、MCU @100MHz、27% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="3f081-246">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="3f081-247">信頼性の高い接続</span><span class="sxs-lookup"><span data-stu-id="3f081-247">Reliable connection</span></span>
* <span data-ttu-id="3f081-248">TCP ソケット数に制限なし</span><span class="sxs-lookup"><span data-stu-id="3f081-248">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="3f081-249">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="3f081-249">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3f081-250">ソケットの受信/送信でオプションの中断</span><span class="sxs-lookup"><span data-stu-id="3f081-250">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="3f081-251">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="3f081-251">Optional timeout on all suspension</span></span>
* <span data-ttu-id="3f081-252">オプションの TCP 統計情報</span><span class="sxs-lookup"><span data-stu-id="3f081-252">Optional TCP statistics</span></span>
* <span data-ttu-id="3f081-253">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="3f081-253">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="3f081-254">直感的な TCP API: *nx_tcp_\**</span><span class="sxs-lookup"><span data-stu-id="3f081-254">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="3f081-255">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="3f081-255">ARP/RARP</span></span>

* <span data-ttu-id="3f081-256">アドレス解決プロトコル (ARP)</span><span class="sxs-lookup"><span data-stu-id="3f081-256">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="3f081-257">逆アドレス解決プロトコル (RARP)</span><span class="sxs-lookup"><span data-stu-id="3f081-257">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="3f081-258">最小 1.7 KB のフラッシュ、RAM サイズ</span><span class="sxs-lookup"><span data-stu-id="3f081-258">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="3f081-259">32 ビット IPv4 と 48 ビット MAC アドレスの動的な解決</span><span class="sxs-lookup"><span data-stu-id="3f081-259">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="3f081-260">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="3f081-260">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3f081-261">柔軟なユーザー定義の ARP キャッシュ</span><span class="sxs-lookup"><span data-stu-id="3f081-261">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="3f081-262">Gratuitous ARP のサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-262">Gratuitous ARP support</span></span>
* <span data-ttu-id="3f081-263">アプリケーションによって決定されるオプションの ARP/RARP 統計</span><span class="sxs-lookup"><span data-stu-id="3f081-263">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="3f081-264">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="3f081-264">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="3f081-265">直感的な ARP/RARP API: *nx_arp_\** 、*nx_rarp_\**</span><span class="sxs-lookup"><span data-stu-id="3f081-265">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="3f081-266">IPv4 および IPv6</span><span class="sxs-lookup"><span data-stu-id="3f081-266">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="3f081-267">インターネット プロトコル (IP)●いんたーねっとぷろとこる(ip)○</span><span class="sxs-lookup"><span data-stu-id="3f081-267">Internet Protocol (IP)</span></span>
* <span data-ttu-id="3f081-268">最小 3.5 KB から 8.5 KB のフラッシュ、2 KB から 3 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="3f081-268">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="3f081-269">Piconet™ アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="3f081-269">Piconet™ architecture</span></span>
* <span data-ttu-id="3f081-270">高速でほぼワイヤスピードのパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="3f081-270">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="3f081-271">複数インターフェイスのサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-271">Multiple interface support</span></span>
* <span data-ttu-id="3f081-272">マルチホーム サポート</span><span class="sxs-lookup"><span data-stu-id="3f081-272">Multihomed support</span></span>
* <span data-ttu-id="3f081-273">静的ルーティングのサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-273">Static routing support</span></span>
* <span data-ttu-id="3f081-274">IP の断片化/再構築のサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-274">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="3f081-275">IPv4 および IPv6 アドレスのサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-275">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="3f081-276">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="3f081-276">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3f081-277">フェーズ II IPv6 対応ロゴ認定</span><span class="sxs-lookup"><span data-stu-id="3f081-277">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="3f081-278">オプションの IP 統計情報</span><span class="sxs-lookup"><span data-stu-id="3f081-278">Optional IP statistics</span></span>
* <span data-ttu-id="3f081-279">明確に定義された直観的な物理レイヤー ドライバー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f081-279">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="3f081-280">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="3f081-280">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="3f081-281">直感的な IP レイヤー API: *nx_ip_\** 、*nxd_ip_\** 、*nxd_ipv6_\**</span><span class="sxs-lookup"><span data-stu-id="3f081-281">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="3f081-282">TUV および UL による IEC 61508 SIL 4、IEC 62304 クラス C、ISO 26262 ASIL D、および EN 50128 SW-SIL4 に対する事前認定</span><span class="sxs-lookup"><span data-stu-id="3f081-282">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="3f081-283">Azure RTOS NetX Secure IPSEC</span><span class="sxs-lookup"><span data-stu-id="3f081-283">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="3f081-284">インターネット プロトコル セキュリティ (IPSEC)</span><span class="sxs-lookup"><span data-stu-id="3f081-284">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="3f081-285">IP レイヤー</span><span class="sxs-lookup"><span data-stu-id="3f081-285">IP layer</span></span>
* <span data-ttu-id="3f081-286">ハードウェア暗号化のサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-286">Hardware crypto support</span></span>
* <span data-ttu-id="3f081-287">ソフトウェア暗号化のサポート (以下を含む):</span><span class="sxs-lookup"><span data-stu-id="3f081-287">Software crypto support, including:</span></span>
    * <span data-ttu-id="3f081-288">DES、3DES</span><span class="sxs-lookup"><span data-stu-id="3f081-288">DES, 3DES</span></span>
    * <span data-ttu-id="3f081-289">AES</span><span class="sxs-lookup"><span data-stu-id="3f081-289">AES</span></span>
    * <span data-ttu-id="3f081-290">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="3f081-290">HMAC-MD5</span></span>
    * <span data-ttu-id="3f081-291">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="3f081-291">HMAC-SHA1</span></span>
* <span data-ttu-id="3f081-292">インターネット キー交換 (IKE) バージョン 2 のサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-292">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="3f081-293">直感的な IPsec API: *nx_ipsec_\**</span><span class="sxs-lookup"><span data-stu-id="3f081-293">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="3f081-294">IPsec は、Azure RTOS NetX Duo でのみ使用可能</span><span class="sxs-lookup"><span data-stu-id="3f081-294">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="3f081-295">高い安全性</span><span class="sxs-lookup"><span data-stu-id="3f081-295">Safe and secure</span></span>

<span data-ttu-id="3f081-296">Azure RTOS NetX Duo はセキュリティで保護されています。</span><span class="sxs-lookup"><span data-stu-id="3f081-296">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="3f081-297">このセキュリティは、IPsec、SSL、TLS、DTLS などのアドオン セキュリティ製品を通じて提供されます。</span><span class="sxs-lookup"><span data-stu-id="3f081-297">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="3f081-298">また、アプリケーションでは Azure RTOS NetX Duo へのすべての外部アクセスを完全に制御できるため、セキュリティ上のリスクをより簡単に判断できます。</span><span class="sxs-lookup"><span data-stu-id="3f081-298">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="3f081-299">Microsoft Azure RTOS には、通信をセキュリティで保護し、基になる MCU/MPU ハードウェア保護メカニズムを使用してコードとデータの分離を作成するためのコンポーネントを含む OEM があります。</span><span class="sxs-lookup"><span data-stu-id="3f081-299">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="3f081-300">特定のユース ケースに関連して進化し続けるセキュリティ要件をデバイスが完全に満たすようにすることは、最終的には、デバイス ビルダーの責任です。</span><span class="sxs-lookup"><span data-stu-id="3f081-300">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>


## <a name="interoperability-verification"></a><span data-ttu-id="3f081-301">相互運用性の検証</span><span class="sxs-lookup"><span data-stu-id="3f081-301">Interoperability verification</span></span>

<span data-ttu-id="3f081-302">NetX Duo は RFC 標準に準拠し、ほとんどのベンダーのデバイスとの完全な相互運用性を提供します。</span><span class="sxs-lookup"><span data-stu-id="3f081-302">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![IPv6 対応のロゴ](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="3f081-304">Azure RTOS NetX Duo は、厳密な IPv6 対応のロゴ認定を達成する唯一の埋め込み型 TCP/IP スタックです。このロゴは、準拠と相互運用性のテストに合格し、IPv6 フォーラムによって管理および検証されていることを証明します。</span><span class="sxs-lookup"><span data-stu-id="3f081-304">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="3f081-305">NetX Duo では、NetX Duo コア TCP/IP プロトコルの実装に対して業界標準の IxANVL (自動ネットワーク検証ライブラリ) も利用されています。</span><span class="sxs-lookup"><span data-stu-id="3f081-305">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="3f081-306">包括的な IoT ソリューション</span><span class="sxs-lookup"><span data-stu-id="3f081-306">Comprehensive IoT solution</span></span>

<span data-ttu-id="3f081-307">NetX Duo では、深い埋め込み型 IoT アプリケーション向けの最も包括的な TCP/IP ネットワークの 1 つが提供されます。</span><span class="sxs-lookup"><span data-stu-id="3f081-307">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="3f081-308">このサポートには、次のアドオン プロトコル製品が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3f081-308">This support includes the following add-on protocol products.</span></span>

<span data-ttu-id="3f081-309">MQTT、CoAP、LWM2M、6LoWPAN、SSL/TLS/DTLS、IPsec、AutoIP、DHCP、DNS、mDNS、DNS-SD、FTP、HTTP、IPsec、NAT、POP3、PPP、PPPoE、SMTP、SNMP v1/2/3、Telnet、TFTP</span><span class="sxs-lookup"><span data-stu-id="3f081-309">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="3f081-310">高度なテクノロジ</span><span class="sxs-lookup"><span data-stu-id="3f081-310">Advanced technology</span></span>

<span data-ttu-id="3f081-311">Azure RTOS NetX Duo は次の機能を備えた高度なテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="3f081-311">Azure RTOS NetX Duo is advanced technology that includes:</span></span>

* <span data-ttu-id="3f081-312">Piconet™ アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="3f081-312">Piconet™ architecture</span></span>
* <span data-ttu-id="3f081-313">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="3f081-313">Automatic scaling</span></span>
* <span data-ttu-id="3f081-314">UDP Fast-Path Technology™</span><span class="sxs-lookup"><span data-stu-id="3f081-314">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="3f081-315">柔軟なパケット管理</span><span class="sxs-lookup"><span data-stu-id="3f081-315">Flexible packet management</span></span>
* <span data-ttu-id="3f081-316">ゼロコピー API と実装</span><span class="sxs-lookup"><span data-stu-id="3f081-316">Zero-copy API and implementation</span></span>
* <span data-ttu-id="3f081-317">マルチホーム サポート</span><span class="sxs-lookup"><span data-stu-id="3f081-317">Multihomed support</span></span>
* <span data-ttu-id="3f081-318">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="3f081-318">Optional timeout on all suspension</span></span>
* <span data-ttu-id="3f081-319">静的ルーティングのサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-319">Static routing support</span></span>
* <span data-ttu-id="3f081-320">IPsec</span><span class="sxs-lookup"><span data-stu-id="3f081-320">IPsec</span></span>
* <span data-ttu-id="3f081-321">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="3f081-321">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="3f081-322">Azure RTOS TraceX システム分析のサポート</span><span class="sxs-lookup"><span data-stu-id="3f081-322">Azure RTOS TraceX system analysis support</span></span>

## <a name="related-services"></a><span data-ttu-id="3f081-323">関連サービス</span><span class="sxs-lookup"><span data-stu-id="3f081-323">Related services</span></span>

<span data-ttu-id="3f081-324">Azure Security Center for IoT RTOS セキュリティ モジュールでは、Azure RTOS デバイス向けの包括的なセキュリティ ソリューションが提供されます。</span><span class="sxs-lookup"><span data-stu-id="3f081-324">The Azure Security Center for IoT RTOS security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="3f081-325">Azure RTOS のセキュリティ モジュールは、悪意のあるネットワーク アクティビティの検出、カスタム アラート ベースのデバイス動作での基準設定、およびデバイス セキュリティ検疫の強化に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3f081-325">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="3f081-326">[Azure RTOS のセキュリティ モジュール](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos)の詳細を確認するか、[Azure RTOS 用セキュリティ モジュールの構成](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module)に関するクイックスタートを開始してください。</span><span class="sxs-lookup"><span data-stu-id="3f081-326">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3f081-327">次のステップ</span><span class="sxs-lookup"><span data-stu-id="3f081-327">Next steps</span></span>

<span data-ttu-id="3f081-328">NetX Duo の詳細については、最初に、[Azure RTOS NetX Duo のユーザー ガイド](about-this-guide.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f081-328">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
