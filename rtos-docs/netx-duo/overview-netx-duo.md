---
title: Azure RTOS NetX Duo を理解する
description: Azure RTOS NetX Duo は、深い埋め込み型のリアルタイム IoT アプリケーション用に特に設計された高度な商用 TCP/IP ネットワーク スタックです。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: b40a57bf385ddcf623ff7cbe0d2e798c547227d7
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754898"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="8d4ea-103">Azure RTOS NetX Duo の概要</span><span class="sxs-lookup"><span data-stu-id="8d4ea-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="8d4ea-104">Azure RTOS NetX Duo 埋め込み型 TCP/IP ネットワーク スタックは、深い埋め込み型のリアルタイム IoT アプリケーション専用に設計された、Microsoft が提供する高度な商用デュアル IPv4 および IPv6 TCP/IP ネットワーク スタックです。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="8d4ea-105">NetX Duo は、コア ネットワーク プロトコル (IPv4、IPv6、TCP、UDP など) と、その他の高度なアドオン プロトコルの完全なスイートを埋め込み型アプリケーションに提供します。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="8d4ea-106">Azure RTOS NetX Duo は、Azure RTOS NetX Secure IPsec や Azure RTOS NetX Secure SSL/TLS/DTLS を含む追加のアドオン セキュリティ製品を介してセキュリティを提供します。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="8d4ea-107">これらすべてを小さなフットプリント、高速な処理、優れた使いやすさと組み合わせることで、Azure RTOS NetX Duo は、最も要求の厳しい埋め込み型 IoT アプリケーションに最適な選択肢となります。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="8d4ea-108">API プロトコル</span><span class="sxs-lookup"><span data-stu-id="8d4ea-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="8d4ea-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="8d4ea-109">MQTT</span></span>

* <span data-ttu-id="8d4ea-110">Messaging Queue Telemetry Transport (MQTT)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="8d4ea-111">最小 2.7 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="8d4ea-111">Minimal 2.7 KB FLASH</span></span>

### <a name="auto-ip"></a><span data-ttu-id="8d4ea-112">Auto IP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-112">Auto IP</span></span>

* <span data-ttu-id="8d4ea-113">IPv4 アドレス自動割り当て</span><span class="sxs-lookup"><span data-stu-id="8d4ea-113">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="8d4ea-114">最小 1.2 KB、300 バイトの RAM</span><span class="sxs-lookup"><span data-stu-id="8d4ea-114">Minimal 1.2 KB, 300 bytes of RAM</span></span>

### <a name="http-https"></a><span data-ttu-id="8d4ea-115">HTTP、HTTPS</span><span class="sxs-lookup"><span data-stu-id="8d4ea-115">HTTP, HTTPS</span></span>
<span data-ttu-id="8d4ea-116">NetX Duo は、次の HTTP/HTTPS プロトコルをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-116">NetX Duo supports the following HTTP/HTTPS protocols.</span></span>

#### <a name="http-10"></a><span data-ttu-id="8d4ea-117">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="8d4ea-117">HTTP 1.0</span></span>

* <span data-ttu-id="8d4ea-118">ハイパーテキスト転送プロトコル (HTTP)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-118">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="8d4ea-119">最小 2.8 KB から 4.8 KB のフラッシュ/0.4 KB から 1.0 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="8d4ea-119">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="8d4ea-120">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-120">Client and server support</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="8d4ea-121">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="8d4ea-121">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="8d4ea-122">ハイパーテキスト転送プロトコル (HTTP)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-122">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="8d4ea-123">最小 3.0 KB から 9.5 KB のフラッシュ/0.5 KB から 2 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="8d4ea-123">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="8d4ea-124">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-124">Client and server support</span></span>
* <span data-ttu-id="8d4ea-125">複数の受信クライアント セッション</span><span class="sxs-lookup"><span data-stu-id="8d4ea-125">Multiple incoming client sessions</span></span>
* <span data-ttu-id="8d4ea-126">プレーンテキストと暗号化された HTTPS</span><span class="sxs-lookup"><span data-stu-id="8d4ea-126">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="8d4ea-127">永続的な接続のサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-127">Persistent connection support</span></span>
* <span data-ttu-id="8d4ea-128">マルチパート ファイルのアップロード</span><span class="sxs-lookup"><span data-stu-id="8d4ea-128">Multipart file upload</span></span>
* <span data-ttu-id="8d4ea-129">Azure RTOS NetX Secure TLS と完全に統合</span><span class="sxs-lookup"><span data-stu-id="8d4ea-129">Fully integrated with Azure RTOS NetX Secure TLS</span></span>

### <a name="smtp"></a><span data-ttu-id="8d4ea-130">SMTP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-130">SMTP</span></span>

* <span data-ttu-id="8d4ea-131">簡易メール転送プロトコル (SMTP)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-131">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="8d4ea-132">最小 4.1 KB と 0.6 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="8d4ea-132">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="8d4ea-133">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-133">Client support</span></span>

### <a name="dhcp"></a><span data-ttu-id="8d4ea-134">DHCP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-134">DHCP</span></span>

* <span data-ttu-id="8d4ea-135">動的ホスト構成プロトコル (DHCP)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-135">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="8d4ea-136">最小 3.6 KB から 4.6 KB のフラッシュ、2.7 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="8d4ea-136">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="8d4ea-137">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-137">Client and server support</span></span>
* <span data-ttu-id="8d4ea-138">IPv4 および IPv6 のサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-138">IPv4 and IPv6 support</span></span>

### <a name="nat"></a><span data-ttu-id="8d4ea-139">NAT</span><span class="sxs-lookup"><span data-stu-id="8d4ea-139">NAT</span></span>

* <span data-ttu-id="8d4ea-140">ネットワーク アドレス変換 (NAT)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-140">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="8d4ea-141">最小 3.5 K6 と 0.6 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="8d4ea-141">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="8d4ea-142">IPv4 アドレスのサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-142">IPv4 address support</span></span>
* <span data-ttu-id="8d4ea-143">NAT は、Azure RTOS NetX Duo でのみ使用可能</span><span class="sxs-lookup"><span data-stu-id="8d4ea-143">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="8d4ea-144">SNMP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-144">SNMP</span></span>

* <span data-ttu-id="8d4ea-145">簡易ネットワーク管理プロトコル (SNMP)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-145">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="8d4ea-146">最小 10.9 KB と 2.6 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="8d4ea-146">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="8d4ea-147">VI、V2、V3 のエージェントのサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-147">Agent support for VI, V2, and V3</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="8d4ea-148">DNS、mDNS、DNS-SD</span><span class="sxs-lookup"><span data-stu-id="8d4ea-148">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="8d4ea-149">ドメイン ネーム システム (DNS)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-149">Domain Name System (DNS)</span></span>
* <span data-ttu-id="8d4ea-150">マルチキャスト ドメイン ネーム システム (mDNS)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-150">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="8d4ea-151">DNS ベースのサービス検出 (DNS-SD)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-151">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="8d4ea-152">DNS 最小 2.4 KB から 3 KB のフラッシュ、1 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="8d4ea-152">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="8d4ea-153">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-153">Client support</span></span>
* <span data-ttu-id="8d4ea-154">mDNS と DNS-SD は、Azure RTOS NetX Duo でのみ使用可能</span><span class="sxs-lookup"><span data-stu-id="8d4ea-154">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="pop3"></a><span data-ttu-id="8d4ea-155">POP3</span><span class="sxs-lookup"><span data-stu-id="8d4ea-155">POP3</span></span>

* <span data-ttu-id="8d4ea-156">Post Office Protocol Version 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-156">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="8d4ea-157">最小 8.1 KB と 1.4 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="8d4ea-157">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="8d4ea-158">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-158">Client support</span></span>

### <a name="telnet"></a><span data-ttu-id="8d4ea-159">Telnet</span><span class="sxs-lookup"><span data-stu-id="8d4ea-159">TELNET</span></span>

* <span data-ttu-id="8d4ea-160">最小 0.5 KB と 0.3 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="8d4ea-160">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="8d4ea-161">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-161">Client and server support</span></span>
* <span data-ttu-id="8d4ea-162">直感的な Telnet API: *nx_telnet_\**</span><span class="sxs-lookup"><span data-stu-id="8d4ea-162">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="8d4ea-163">FTP、TFTP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-163">FTP, TFTP</span></span>

* <span data-ttu-id="8d4ea-164">ファイル転送プロトコル (FTP)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-164">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="8d4ea-165">簡易ファイル転送プロトコル (TFTP)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-165">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="8d4ea-166">FTP 最小 1.8 KB から 7.2 KB のフラッシュ、0.6 KB から 2.1 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="8d4ea-166">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="8d4ea-167">TFTP 最小 1.7 KB から 2.4 KB のフラッシュ、0.3 KB から 1.8 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="8d4ea-167">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="8d4ea-168">クライアントとサーバーのサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-168">Client and server support</span></span>
* <span data-ttu-id="8d4ea-169">直感的な FTP および TFTP API: *nx_ftp_\** または *nx_tftp_\**</span><span class="sxs-lookup"><span data-stu-id="8d4ea-169">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="8d4ea-170">PPP、PPPoE</span><span class="sxs-lookup"><span data-stu-id="8d4ea-170">PPP, PPPoE</span></span>

* <span data-ttu-id="8d4ea-171">Point-to-Point プロトコル (PPP)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-171">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="8d4ea-172">Point-to-Point Protocol over Ethernet (PPPoE)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-172">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="8d4ea-173">最小 7.1 KB と 3.8 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="8d4ea-173">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="8d4ea-174">直感的な PPP API: *nx_ppp_\**</span><span class="sxs-lookup"><span data-stu-id="8d4ea-174">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="8d4ea-175">PPPoE は、Azure RTOS NetX Duo でのみ使用可能</span><span class="sxs-lookup"><span data-stu-id="8d4ea-175">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="8d4ea-176">SNTP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-176">SNTP</span></span>

* <span data-ttu-id="8d4ea-177">Simple Network Time Protocol (SNTP)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-177">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="8d4ea-178">最小 4 KB および 0.5 KB の RAM</span><span class="sxs-lookup"><span data-stu-id="8d4ea-178">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="8d4ea-179">クライアントのサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-179">Client support</span></span>
* <span data-ttu-id="8d4ea-180">直感的な SNTP API: *nx_sntp_\**</span><span class="sxs-lookup"><span data-stu-id="8d4ea-180">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="legacy-code-support"></a><span data-ttu-id="8d4ea-181">レガシ コードのサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-181">Legacy code support</span></span>

* <span data-ttu-id="8d4ea-182">レガシ ソケット コードを移植するためのオプションの BSD レイヤー</span><span class="sxs-lookup"><span data-stu-id="8d4ea-182">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="8d4ea-183">IGMP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-183">IGMP</span></span>

* <span data-ttu-id="8d4ea-184">インターネット グループ管理プロトコル (IGMP)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-184">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="8d4ea-185">最小 2.5 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="8d4ea-185">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="8d4ea-186">IPv4 マルチキャスト グループのサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-186">IPv4 multicast group support</span></span>
* <span data-ttu-id="8d4ea-187">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="8d4ea-187">IXIA IxANVL validated</span></span>
* <span data-ttu-id="8d4ea-188">オプションの IGMP 統計情報</span><span class="sxs-lookup"><span data-stu-id="8d4ea-188">Optional IGMP statistics</span></span>
* <span data-ttu-id="8d4ea-189">Azure RTOS ThreadX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="8d4ea-189">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="8d4ea-190">直感的な IGMP API: *nx_igmp_\**</span><span class="sxs-lookup"><span data-stu-id="8d4ea-190">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="8d4ea-191">Azure RTOS NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="8d4ea-191">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="8d4ea-192">データグラム トランスポート層セキュリティ (DTLS) 1.0 および 1.2</span><span class="sxs-lookup"><span data-stu-id="8d4ea-192">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="8d4ea-193">最小 11 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="8d4ea-193">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="8d4ea-194">高速、ソフトウェア RSA 2048 ビットキーのサイズ ～ 1 秒 @120MHz</span><span class="sxs-lookup"><span data-stu-id="8d4ea-194">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="8d4ea-195">合理化された X.509 実装</span><span class="sxs-lookup"><span data-stu-id="8d4ea-195">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="8d4ea-196">Azure RTOS NetX Duo UDP ソケットと完全に統合</span><span class="sxs-lookup"><span data-stu-id="8d4ea-196">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="8d4ea-197">ハードウェア暗号化のサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-197">Hardware Crypto Support</span></span>
* <span data-ttu-id="8d4ea-198">ソフトウェアの暗号化のサポート: RSA (すべてのキー サイズ)、AES、DES/3DES、ECC、HMAC、MD5、SHA-1、SHA-2 (SHA-224、SHA-256、SHA-384、SHA-512)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-198">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="8d4ea-199">ECDSA (署名) と ECDH (暗号化) を使用した楕円曲線暗号 (ECC)、P 曲線 192/224/256/384/521 を含む</span><span class="sxs-lookup"><span data-stu-id="8d4ea-199">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="8d4ea-200">暗号化キーのサポート (ハードウェアに依存)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-200">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="8d4ea-201">Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="8d4ea-201">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="8d4ea-202">トランスポート層セキュリティ (TLS) 1.0、1.1、および 1.2</span><span class="sxs-lookup"><span data-stu-id="8d4ea-202">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="8d4ea-203">最小 8.8 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="8d4ea-203">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="8d4ea-204">高速、ソフトウェア RSA 2048 ビットキーのサイズ ～ 1 秒 @120MHz</span><span class="sxs-lookup"><span data-stu-id="8d4ea-204">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="8d4ea-205">合理化された X.509 実装</span><span class="sxs-lookup"><span data-stu-id="8d4ea-205">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="8d4ea-206">Azure RTOS NetX Duo TCP ソケットと完全に統合</span><span class="sxs-lookup"><span data-stu-id="8d4ea-206">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="8d4ea-207">ハードウェア暗号化のサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-207">Hardware Crypto Support</span></span>
* <span data-ttu-id="8d4ea-208">ソフトウェアの暗号化のサポート: RSA (すべてのキー サイズ)、AES、DES/3DES、ECC、HMAC、MD5、SHA-1、SHA-2 (SHA-224、SHA-256、SHA-384、SHA-512)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-208">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="8d4ea-209">ECDSA (署名) と ECDH (暗号化) を使用した楕円曲線暗号 (ECC)、P 曲線 192/224/256/384/521 を含む</span><span class="sxs-lookup"><span data-stu-id="8d4ea-209">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="8d4ea-210">暗号化キーのサポート (ハードウェアに依存)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-210">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="8d4ea-211">ICMP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-211">ICMP</span></span>

* <span data-ttu-id="8d4ea-212">インターネット制御メッセージ プロトコル (ICMP)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-212">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="8d4ea-213">最小 2.5 KB のフラッシュ</span><span class="sxs-lookup"><span data-stu-id="8d4ea-213">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="8d4ea-214">IPv4 および IPv6 のサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-214">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="8d4ea-215">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="8d4ea-215">IXIA IxANVL validated</span></span>
* <span data-ttu-id="8d4ea-216">ping 要求と ping 応答</span><span class="sxs-lookup"><span data-stu-id="8d4ea-216">Ping request and ping response</span></span>
* <span data-ttu-id="8d4ea-217">ping 要求時のオプションのスレッド中断</span><span class="sxs-lookup"><span data-stu-id="8d4ea-217">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="8d4ea-218">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="8d4ea-218">Optional timeout on all suspension</span></span>
* <span data-ttu-id="8d4ea-219">オプションの ICMP 統計情報</span><span class="sxs-lookup"><span data-stu-id="8d4ea-219">Optional ICMP statistics</span></span>
* <span data-ttu-id="8d4ea-220">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="8d4ea-220">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="8d4ea-221">直感的な ICMP API: *nx_icmp_\**</span><span class="sxs-lookup"><span data-stu-id="8d4ea-221">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="8d4ea-222">UDP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-222">UDP</span></span>

* <span data-ttu-id="8d4ea-223">ユーザー データグラム プロトコル (UDP)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-223">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="8d4ea-224">最小 2.5 KB のフラッシュ、ソケットあたり 124 ソケット バイトの RAM</span><span class="sxs-lookup"><span data-stu-id="8d4ea-224">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="8d4ea-225">高速でほぼワイヤスピードの TCP パケット処理:</span><span class="sxs-lookup"><span data-stu-id="8d4ea-225">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="8d4ea-226">RX 95 Mbps (100 Mbps イーサネット)、MCU @100MHz、14% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="8d4ea-226">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="8d4ea-227">TX 94 Mbps (100 Mbps イーサネット)、MCU @100MHz、10% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="8d4ea-227">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="8d4ea-228">UDP Fast Path™ テクノロジ</span><span class="sxs-lookup"><span data-stu-id="8d4ea-228">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="8d4ea-229">UDP の数に制限なし</span><span class="sxs-lookup"><span data-stu-id="8d4ea-229">No limits on the number of UDP</span></span>
* <span data-ttu-id="8d4ea-230">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="8d4ea-230">IXIA IxANVL validated</span></span>
* <span data-ttu-id="8d4ea-231">ソケット受信時のオプションによる中断</span><span class="sxs-lookup"><span data-stu-id="8d4ea-231">Optional suspension on socket receive</span></span>
* <span data-ttu-id="8d4ea-232">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="8d4ea-232">Optional timeout on all suspension</span></span>
* <span data-ttu-id="8d4ea-233">オプションの UDP 統計情報</span><span class="sxs-lookup"><span data-stu-id="8d4ea-233">Optional UDP statistics</span></span>
* <span data-ttu-id="8d4ea-234">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="8d4ea-234">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="8d4ea-235">直感的な UDP API: *nx_udp_\**</span><span class="sxs-lookup"><span data-stu-id="8d4ea-235">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="8d4ea-236">TCP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-236">TCP</span></span>

* <span data-ttu-id="8d4ea-237">伝送制御プロトコル (TCP)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-237">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="8d4ea-238">最小 10.5 K8 から 12.5 KB のフラッシュ、ソケットあたり 280 バイトの RAM</span><span class="sxs-lookup"><span data-stu-id="8d4ea-238">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="8d4ea-239">高速でほぼワイヤスピードの TCP パケット処理:</span><span class="sxs-lookup"><span data-stu-id="8d4ea-239">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="8d4ea-240">RX 93 Mbps (100 Mbps イーサネット)、MCU @100MHz、20% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="8d4ea-240">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="8d4ea-241">TX 94 Mbps (100 Mbps イーサネット)、MCU @100MHz、27% MCU 使用率</span><span class="sxs-lookup"><span data-stu-id="8d4ea-241">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="8d4ea-242">信頼性の高い接続</span><span class="sxs-lookup"><span data-stu-id="8d4ea-242">Reliable connection</span></span>
* <span data-ttu-id="8d4ea-243">TCP ソケット数に制限なし</span><span class="sxs-lookup"><span data-stu-id="8d4ea-243">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="8d4ea-244">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="8d4ea-244">IXIA IxANVL validated</span></span>
* <span data-ttu-id="8d4ea-245">ソケットの受信/送信でオプションの中断</span><span class="sxs-lookup"><span data-stu-id="8d4ea-245">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="8d4ea-246">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="8d4ea-246">Optional timeout on all suspension</span></span>
* <span data-ttu-id="8d4ea-247">オプションの TCP 統計情報</span><span class="sxs-lookup"><span data-stu-id="8d4ea-247">Optional TCP statistics</span></span>
* <span data-ttu-id="8d4ea-248">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="8d4ea-248">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="8d4ea-249">直感的な TCP API: *nx_tcp_\**</span><span class="sxs-lookup"><span data-stu-id="8d4ea-249">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="8d4ea-250">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-250">ARP/RARP</span></span>

* <span data-ttu-id="8d4ea-251">アドレス解決プロトコル (ARP)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-251">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="8d4ea-252">逆アドレス解決プロトコル (RARP)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-252">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="8d4ea-253">最小 1.7 KB のフラッシュ、RAM サイズ</span><span class="sxs-lookup"><span data-stu-id="8d4ea-253">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="8d4ea-254">32 ビット IPv4 と 48 ビット MAC アドレスの動的な解決</span><span class="sxs-lookup"><span data-stu-id="8d4ea-254">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="8d4ea-255">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="8d4ea-255">IXIA IxANVL validated</span></span>
* <span data-ttu-id="8d4ea-256">柔軟なユーザー定義の ARP キャッシュ</span><span class="sxs-lookup"><span data-stu-id="8d4ea-256">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="8d4ea-257">Gratuitous ARP のサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-257">Gratuitous ARP support</span></span>
* <span data-ttu-id="8d4ea-258">アプリケーションによって決定されるオプションの ARP/RARP 統計</span><span class="sxs-lookup"><span data-stu-id="8d4ea-258">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="8d4ea-259">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="8d4ea-259">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="8d4ea-260">直感的な ARP/RARP API: *nx_arp_\** 、*nx_rarp_\**</span><span class="sxs-lookup"><span data-stu-id="8d4ea-260">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="8d4ea-261">IPv4 および IPv6</span><span class="sxs-lookup"><span data-stu-id="8d4ea-261">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="8d4ea-262">インターネット プロトコル (IP)●いんたーねっとぷろとこる(ip)○</span><span class="sxs-lookup"><span data-stu-id="8d4ea-262">Internet Protocol (IP)</span></span>
* <span data-ttu-id="8d4ea-263">最小 3.5 KB から 8.5 KB のフラッシュ、2 KB から 3 KB の RAM フットプリント</span><span class="sxs-lookup"><span data-stu-id="8d4ea-263">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="8d4ea-264">Piconet™ アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="8d4ea-264">Piconet™ architecture</span></span>
* <span data-ttu-id="8d4ea-265">高速でほぼワイヤスピードのパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="8d4ea-265">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="8d4ea-266">複数インターフェイスのサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-266">Multiple interface support</span></span>
* <span data-ttu-id="8d4ea-267">マルチホーム サポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-267">Multihomed support</span></span>
* <span data-ttu-id="8d4ea-268">静的ルーティングのサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-268">Static routing support</span></span>
* <span data-ttu-id="8d4ea-269">IP の断片化/再構築のサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-269">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="8d4ea-270">IPv4 および IPv6 アドレスのサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-270">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="8d4ea-271">IXIA IxANVL 検証済み</span><span class="sxs-lookup"><span data-stu-id="8d4ea-271">IXIA IxANVL validated</span></span>
* <span data-ttu-id="8d4ea-272">フェーズ II IPv6 対応ロゴ認定</span><span class="sxs-lookup"><span data-stu-id="8d4ea-272">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="8d4ea-273">オプションの IP 統計情報</span><span class="sxs-lookup"><span data-stu-id="8d4ea-273">Optional IP statistics</span></span>
* <span data-ttu-id="8d4ea-274">明確に定義された直観的な物理レイヤー ドライバー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d4ea-274">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="8d4ea-275">Azure RTOS TraceX によるシステムレベルのトレース</span><span class="sxs-lookup"><span data-stu-id="8d4ea-275">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="8d4ea-276">直感的な IP レイヤー API: *nx_ip_\** 、*nxd_ip_\** 、*nxd_ipv6_\**</span><span class="sxs-lookup"><span data-stu-id="8d4ea-276">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="8d4ea-277">TUV および UL による IEC 61508 SIL 4、IEC 62304 クラス C、ISO 26262 ASIL D、および EN 50128 SW-SIL4 に対する事前認定</span><span class="sxs-lookup"><span data-stu-id="8d4ea-277">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="8d4ea-278">Azure RTOS NetX Secure IPSEC</span><span class="sxs-lookup"><span data-stu-id="8d4ea-278">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="8d4ea-279">インターネット プロトコル セキュリティ (IPSEC)</span><span class="sxs-lookup"><span data-stu-id="8d4ea-279">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="8d4ea-280">IP レイヤー</span><span class="sxs-lookup"><span data-stu-id="8d4ea-280">IP layer</span></span>
* <span data-ttu-id="8d4ea-281">ハードウェア暗号化のサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-281">Hardware crypto support</span></span>
* <span data-ttu-id="8d4ea-282">ソフトウェア暗号化のサポート (以下を含む):</span><span class="sxs-lookup"><span data-stu-id="8d4ea-282">Software crypto support, including:</span></span>
    * <span data-ttu-id="8d4ea-283">DES、3DES</span><span class="sxs-lookup"><span data-stu-id="8d4ea-283">DES, 3DES</span></span>
    * <span data-ttu-id="8d4ea-284">AES</span><span class="sxs-lookup"><span data-stu-id="8d4ea-284">AES</span></span>
    * <span data-ttu-id="8d4ea-285">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="8d4ea-285">HMAC-MD5</span></span>
    * <span data-ttu-id="8d4ea-286">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="8d4ea-286">HMAC-SHA1</span></span>
* <span data-ttu-id="8d4ea-287">インターネット キー交換 (IKE) バージョン 2 のサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-287">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="8d4ea-288">直感的な IPsec API: *nx_ipsec_\**</span><span class="sxs-lookup"><span data-stu-id="8d4ea-288">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="8d4ea-289">IPsec は、Azure RTOS NetX Duo でのみ使用可能</span><span class="sxs-lookup"><span data-stu-id="8d4ea-289">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="8d4ea-290">高い安全性</span><span class="sxs-lookup"><span data-stu-id="8d4ea-290">Safe and secure</span></span>

<span data-ttu-id="8d4ea-291">Azure RTOS NetX Duo はセキュリティで保護されています。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-291">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="8d4ea-292">このセキュリティは、IPsec、SSL、TLS、DTLS などのアドオン セキュリティ製品を通じて提供されます。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-292">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="8d4ea-293">また、アプリケーションでは Azure RTOS NetX Duo へのすべての外部アクセスを完全に制御できるため、セキュリティ上のリスクをより簡単に判断できます。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-293">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="8d4ea-294">Microsoft Azure RTOS には、通信をセキュリティで保護し、基になる MCU/MPU ハードウェア保護メカニズムを使用してコードとデータの分離を作成するためのコンポーネントを含む OEM があります。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-294">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="8d4ea-295">特定のユース ケースに関連して進化し続けるセキュリティ要件をデバイスが完全に満たすようにすることは、最終的には、デバイス ビルダーの責任です。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-295">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="8d4ea-296">相互運用性の検証</span><span class="sxs-lookup"><span data-stu-id="8d4ea-296">Interoperability verification</span></span>

<span data-ttu-id="8d4ea-297">NetX Duo は RFC 標準に準拠し、ほとんどのベンダーのデバイスとの完全な相互運用性を提供します。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-297">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![IPv6 対応のロゴ](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="8d4ea-299">Azure RTOS NetX Duo は、厳密な IPv6 対応のロゴ認定を達成する唯一の埋め込み型 TCP/IP スタックです。このロゴは、準拠と相互運用性のテストに合格し、IPv6 フォーラムによって管理および検証されていることを証明します。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-299">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="8d4ea-300">NetX Duo では、NetX Duo コア TCP/IP プロトコルの実装に対して業界標準の IxANVL (自動ネットワーク検証ライブラリ) も利用されています。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-300">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="8d4ea-301">包括的な IoT ソリューション</span><span class="sxs-lookup"><span data-stu-id="8d4ea-301">Comprehensive IoT solution</span></span>

<span data-ttu-id="8d4ea-302">NetX Duo では、深い埋め込み型 IoT アプリケーション向けの最も包括的な TCP/IP ネットワークの 1 つが提供されます。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-302">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="8d4ea-303">このサポートには、次のアドオン プロトコル製品が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-303">This support includes the following add-on protocol products.</span></span>

* <span data-ttu-id="8d4ea-304">MQTT</span><span class="sxs-lookup"><span data-stu-id="8d4ea-304">MQTT</span></span>
* <span data-ttu-id="8d4ea-305">CoAP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-305">CoAP</span></span>
* <span data-ttu-id="8d4ea-306">LWM2M</span><span class="sxs-lookup"><span data-stu-id="8d4ea-306">LWM2M</span></span>
* <span data-ttu-id="8d4ea-307">6LoWPAN</span><span class="sxs-lookup"><span data-stu-id="8d4ea-307">6LoWPAN</span></span>
* <span data-ttu-id="8d4ea-308">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="8d4ea-308">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="8d4ea-309">IPsec</span><span class="sxs-lookup"><span data-stu-id="8d4ea-309">IPsec</span></span>
* <span data-ttu-id="8d4ea-310">AutoIP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-310">AutoIP</span></span>
* <span data-ttu-id="8d4ea-311">DHCP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-311">DHCP</span></span>
* <span data-ttu-id="8d4ea-312">DNS</span><span class="sxs-lookup"><span data-stu-id="8d4ea-312">DNS</span></span>
* <span data-ttu-id="8d4ea-313">mDNS</span><span class="sxs-lookup"><span data-stu-id="8d4ea-313">mDNS</span></span>
* <span data-ttu-id="8d4ea-314">DNS-SD</span><span class="sxs-lookup"><span data-stu-id="8d4ea-314">DNS-SD</span></span>
* <span data-ttu-id="8d4ea-315">FTP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-315">FTP</span></span>
* <span data-ttu-id="8d4ea-316">HTTP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-316">HTTP</span></span>
* <span data-ttu-id="8d4ea-317">IPsec</span><span class="sxs-lookup"><span data-stu-id="8d4ea-317">IPsec</span></span>
* <span data-ttu-id="8d4ea-318">NAT</span><span class="sxs-lookup"><span data-stu-id="8d4ea-318">NAT</span></span>
* <span data-ttu-id="8d4ea-319">POP3</span><span class="sxs-lookup"><span data-stu-id="8d4ea-319">POP3</span></span>
* <span data-ttu-id="8d4ea-320">PPP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-320">PPP</span></span>
* <span data-ttu-id="8d4ea-321">PPPoE</span><span class="sxs-lookup"><span data-stu-id="8d4ea-321">PPPoE</span></span>
* <span data-ttu-id="8d4ea-322">SMTP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-322">SMTP</span></span>
* <span data-ttu-id="8d4ea-323">SNMP v1/2/3</span><span class="sxs-lookup"><span data-stu-id="8d4ea-323">SNMP v1/2/3</span></span>
* <span data-ttu-id="8d4ea-324">Telnet</span><span class="sxs-lookup"><span data-stu-id="8d4ea-324">Telnet</span></span>
* <span data-ttu-id="8d4ea-325">TFTP</span><span class="sxs-lookup"><span data-stu-id="8d4ea-325">TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="8d4ea-326">高度なテクノロジ</span><span class="sxs-lookup"><span data-stu-id="8d4ea-326">Advanced technology</span></span>

<span data-ttu-id="8d4ea-327">Azure RTOS NetX Duo は、次の機能を備えた高度なテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-327">Azure RTOS NetX Duo is advanced technology that includes the following.</span></span>

* <span data-ttu-id="8d4ea-328">Piconet™ アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="8d4ea-328">Piconet™ architecture</span></span>
* <span data-ttu-id="8d4ea-329">自動スケーリング</span><span class="sxs-lookup"><span data-stu-id="8d4ea-329">Automatic scaling</span></span>
* <span data-ttu-id="8d4ea-330">UDP Fast-Path Technology™</span><span class="sxs-lookup"><span data-stu-id="8d4ea-330">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="8d4ea-331">柔軟なパケット管理</span><span class="sxs-lookup"><span data-stu-id="8d4ea-331">Flexible packet management</span></span>
* <span data-ttu-id="8d4ea-332">ゼロコピー API と実装</span><span class="sxs-lookup"><span data-stu-id="8d4ea-332">Zero-copy API and implementation</span></span>
* <span data-ttu-id="8d4ea-333">マルチホーム サポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-333">Multihomed support</span></span>
* <span data-ttu-id="8d4ea-334">すべての中断時のオプションのタイムアウト</span><span class="sxs-lookup"><span data-stu-id="8d4ea-334">Optional timeout on all suspension</span></span>
* <span data-ttu-id="8d4ea-335">静的ルーティングのサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-335">Static routing support</span></span>
* <span data-ttu-id="8d4ea-336">IPsec</span><span class="sxs-lookup"><span data-stu-id="8d4ea-336">IPsec</span></span>
* <span data-ttu-id="8d4ea-337">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="8d4ea-337">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="8d4ea-338">Azure RTOS TraceX システム分析のサポート</span><span class="sxs-lookup"><span data-stu-id="8d4ea-338">Azure RTOS TraceX system analysis support</span></span>

## <a name="related-services"></a><span data-ttu-id="8d4ea-339">関連サービス</span><span class="sxs-lookup"><span data-stu-id="8d4ea-339">Related services</span></span>

<span data-ttu-id="8d4ea-340">NetX Duo には、次の追加サービスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-340">NetX Duo provides the following additional services.</span></span>

* <span data-ttu-id="8d4ea-341">Azure IoT ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="8d4ea-341">Azure IoT Middleware</span></span>
* <span data-ttu-id="8d4ea-342">Azure Defender</span><span class="sxs-lookup"><span data-stu-id="8d4ea-342">Azure Defender</span></span>
* <span data-ttu-id="8d4ea-343">Device Update for IoT Hub</span><span class="sxs-lookup"><span data-stu-id="8d4ea-343">Device update for IoT Hub.</span></span>

### <a name="azure-iot-middleware"></a><span data-ttu-id="8d4ea-344">Azure IoT ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="8d4ea-344">Azure IoT Middleware</span></span>

<span data-ttu-id="8d4ea-345">NetX Duo には [Azure RTOS 用の Azure IoT ミドルウェア](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md)が含まれています。これは、Azure RTOS と Azure SDK for Embedded C の間のバインド層として機能し、Azure IoT サービスへの接続を容易にするプラットフォーム固有のライブラリです。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-345">NetX Duo includes [Azure IoT Middleware for Azure RTOS](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), a platform-specific library that acts as a binding layer between the Azure RTOS and the Azure SDK for Embedded C to facilitate connectivity to Azure IoT services.</span></span> <span data-ttu-id="8d4ea-346">Azure IoT ミドルウェアの目的は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-346">The goals of Azure IoT Middleware are the following.</span></span>
* <span data-ttu-id="8d4ea-347">開発者がアプリケーションに必要とするスマートなクライアント インターフェイス (IoTHub_Client、DeviceProvisioning_Client) を提供する。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-347">Provide the smart client interfaces (IoTHub_Client, DeviceProvisioning_Client) that developers need for their applications.</span></span>
* <span data-ttu-id="8d4ea-348">Embedded C SDK とプラットフォーム間の対話を調整する。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-348">Orchestrate the interaction between the Embedded C SDK and the platform.</span></span>
* <span data-ttu-id="8d4ea-349">Azure RTOS プラットフォームの初期化を提供する。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-349">Provide Azure RTOS platform initialization.</span></span>
* <span data-ttu-id="8d4ea-350">IoT Plug and Play のサポート。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-350">IoT Plug and Play support.</span></span>
* <span data-ttu-id="8d4ea-351">セキュリティ機能。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-351">Security capabilities.</span></span>
* <span data-ttu-id="8d4ea-352">リソース制限への対応。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-352">Resource limitation aware.</span></span>
* <span data-ttu-id="8d4ea-353">プロトコルのサポート。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-353">Protocol support.</span></span>

![Azure RTOS NetX Duo 関連のサービス](./media/overview-netx-duo/related-services.png)

### <a name="azure-defender"></a><span data-ttu-id="8d4ea-355">Azure Defender</span><span class="sxs-lookup"><span data-stu-id="8d4ea-355">Azure Defender</span></span>

<span data-ttu-id="8d4ea-356">Azure Defender for IoT セキュリティ モジュールでは、Azure RTOS デバイス向けの包括的なセキュリティ ソリューションが提供されます。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-356">The Azure Defender for IoT security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="8d4ea-357">Azure RTOS のセキュリティ モジュールは、悪意のあるネットワーク アクティビティの検出、カスタム アラート ベースのデバイス動作での基準設定、およびデバイス セキュリティ検疫の強化に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-357">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="8d4ea-358">[Azure RTOS のセキュリティ モジュール](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos)の詳細を確認するか、[Azure RTOS 用セキュリティ モジュールの構成](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module)に関するクイックスタートを開始してください。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-358">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

### <a name="device-update-for-iot-hub"></a><span data-ttu-id="8d4ea-359">Device Update for IoT Hub</span><span class="sxs-lookup"><span data-stu-id="8d4ea-359">Device Update for IoT Hub</span></span>

<span data-ttu-id="8d4ea-360">[Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) は、IoT デバイスの Over-the-Air (OTA) 更新をデプロイできるようにするサービスです。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-360">The [Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) is a service that enables you to deploy over-the-air updates (OTA) for your IoT devices.</span></span> <span data-ttu-id="8d4ea-361">Device Update for IoT Hub モジュールは、Azure RTOS NetX Duo での Device Update for IoT Hub エージェントの実装です。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-361">The Device Update for IoT Hub module is the implementation of Device Update for IoT Hub Agent in Azure RTOS NetX Duo.</span></span> <span data-ttu-id="8d4ea-362">これは、デバイス開発者がアプリケーションにデバイス更新機能を統合するための簡単な API を提供します。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-362">It provides simple APIs for device builders to integrate the Device Update capability in their application.</span></span>

<span data-ttu-id="8d4ea-363">主要な半導体評価ボードのサンプルをご覧ください。デバイスへの無線 (OTA) での更新を構成、構築、デプロイする方法が学べるファースト ステップ ガイドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-363">See the samples of key semiconductors evaluation boards that include the get started guides to learn configure, build and deploy the over-the-air (OTA) updates to the devices.</span></span>

<span data-ttu-id="8d4ea-364">さらに、[Azure RTOS を使用した Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system) に関する記事で詳細を確認できます。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-364">And you can learn more details about use [Device Update for IoT Hub with Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8d4ea-365">次のステップ</span><span class="sxs-lookup"><span data-stu-id="8d4ea-365">Next steps</span></span>

<span data-ttu-id="8d4ea-366">NetX Duo の詳細については、最初に、[Azure RTOS NetX Duo のユーザー ガイド](about-this-guide.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d4ea-366">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
