---
title: 第 2 章 - Azure RTOS NetX Secure のインストールと使用
description: この章では、NetX Secure コンポーネントのインストール、セットアップ、および使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b3ef82bd113518b35105fb2eefe23bd3e755ca06
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811768"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-secure"></a><span data-ttu-id="1a54c-103">第 2 章 - Azure RTOS NetX Secure のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="1a54c-103">Chapter 2 - Installation and use of Azure RTOS NetX Secure</span></span>

<span data-ttu-id="1a54c-104">この章では、Azure RTOS NetX Secure コンポーネントのインストール、セットアップ、および使用に関連するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="1a54c-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Secure component.</span></span>

## <a name="product-version-number"></a><span data-ttu-id="1a54c-105">製品バージョン番号</span><span class="sxs-lookup"><span data-stu-id="1a54c-105">Product Version Number</span></span>

<span data-ttu-id="1a54c-106">ユーザーは nx_secure_tls.h で次のシンボルを見つけて、製品のバージョン番号を確認できます。</span><span class="sxs-lookup"><span data-stu-id="1a54c-106">User may verify the product version number by finding the following symbols in nx_secure_tls.h:</span></span>

<span data-ttu-id="1a54c-107">***NETX_SECURE_MAJOR_VERSION***</span><span class="sxs-lookup"><span data-stu-id="1a54c-107">***NETX_SECURE_MAJOR_VERSION***</span></span>

<span data-ttu-id="1a54c-108">***NETX_SECURE_MINOR_VERSION***</span><span class="sxs-lookup"><span data-stu-id="1a54c-108">***NETX_SECURE_MINOR_VERSION***</span></span>

<span data-ttu-id="1a54c-109">サービス パックのリリースでは、サービス パック番号を示す次のシンボルが定義されています。</span><span class="sxs-lookup"><span data-stu-id="1a54c-109">Service Pack releases has the following symbol defined to indicate the service pack number:</span></span>

<span data-ttu-id="1a54c-110">***NETX_SECURE_SERVICE_PACK_VERSION***</span><span class="sxs-lookup"><span data-stu-id="1a54c-110">***NETX_SECURE_SERVICE_PACK_VERSION***</span></span>

## <a name="product-distribution"></a><span data-ttu-id="1a54c-111">製品ディストリビューション</span><span class="sxs-lookup"><span data-stu-id="1a54c-111">Product Distribution</span></span>

<span data-ttu-id="1a54c-112">NetX Secure は [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="1a54c-112">NetX Secure is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="1a54c-113">パッケージに含まれているソース ファイル、インクルード ファイル、このドキュメントを含む PDF ファイルを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="1a54c-113">The package includes source files, include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="1a54c-114">**nx_secure_tls_api.h** NetX Secure TLS のパブリック API ヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="1a54c-114">**nx_secure_tls_api.h** Public API header file for NetX Secure TLS</span></span>
- <span data-ttu-id="1a54c-115">**nx_secure_tls_user.h** NetX Secure TLS のユーザー定義ヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="1a54c-115">**nx_secure_tls_user.h** User defines header file for NetX Secure TLS</span></span>
- <span data-ttu-id="1a54c-116">**nx_secure_tls_port.h** NetX Secure のプラットフォーム固有の定義</span><span class="sxs-lookup"><span data-stu-id="1a54c-116">**nx_secure_tls_port.h** Platform-specific definitions for NetX Secure</span></span>
- <span data-ttu-id="1a54c-117">**nx_secure_tls.h** NetX Secure TLS のヘッダーファイル</span><span class="sxs-lookup"><span data-stu-id="1a54c-117">**nx_secure_tls.h** Header file for NetX Secure TLS</span></span>
- <span data-ttu-id="1a54c-118">**nx_secure_tls&#42;.c/h** NetX Secure TLS の C/H ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="1a54c-118">**nx_secure_tls&#42;.c/h** C/H Source files for NetX Secure TLS</span></span>
- <span data-ttu-id="1a54c-119">**nx_crypto&#42;.c/h** NetX Secure Cryptography の C/H ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="1a54c-119">**nx_crypto&#42;.c/h** C/H Source files for NetX Secure Cryptography</span></span>
- <span data-ttu-id="1a54c-120">**nx_secure_x509&#42;.c/h** X.509 デジタル証明書の C/H ソース ファイル。</span><span class="sxs-lookup"><span data-stu-id="1a54c-120">**nx_secure_x509&#42;.c/h** C/H Source files for X.509 digital certificates.</span></span>
- <span data-ttu-id="1a54c-121">**demo_netx_secure_tls.c** NetX Secure TLS Demo の C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="1a54c-121">**demo_netx_secure_tls.c** C Source file for NetX Secure TLS Demo</span></span>
- <span data-ttu-id="1a54c-122">**NetX_Secure_User_Guide.pdf** NetX Secure 製品の PDF 説明書</span><span class="sxs-lookup"><span data-stu-id="1a54c-122">**NetX_Secure_User_Guide.pdf** PDF description of NetX Secure product</span></span>

> [!NOTE]
> <span data-ttu-id="1a54c-123">さまざまなハードウェア プラットフォームのための nx_crypto\* ファイルが、NetX Secure 親ディレクトリのサブディレクトリに用意されています。</span><span class="sxs-lookup"><span data-stu-id="1a54c-123">The nx_crypto\* files are provided for different hardware platforms in a subdirectory of the NetX Secure parent directory.</span></span>

## <a name="netx-secure-installation"></a><span data-ttu-id="1a54c-124">NetX Secure のインストール</span><span class="sxs-lookup"><span data-stu-id="1a54c-124">NetX Secure Installation</span></span>

<span data-ttu-id="1a54c-125">NetX Secure を使用するためには、前述のディストリビューション全体を、NetX がインストールされているのと同じディレクトリ レベルにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-125">In order to use NetX Secure, the entire distribution mentioned previously should be copied to the same directory level where NetX is installed.</span></span> <span data-ttu-id="1a54c-126">たとえば、NetX がディレクトリ " *\threadx\arm7\NetX*" にインストールされている場合は、*nx_secure\*\*.*</span><span class="sxs-lookup"><span data-stu-id="1a54c-126">For example, if NetX is installed in the directory "*\threadx\arm7\NetX*" then the *nx_secure\*\*.*</span></span> <span data-ttu-id="1a54c-127">ディレクトリを " *\threadx\arm7\NetXSecure*" にコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-127">directories should be copied into "*\threadx\arm7\NetXSecure*".</span></span>

## <a name="using-netx-secure"></a><span data-ttu-id="1a54c-128">NetX Secure を使用する</span><span class="sxs-lookup"><span data-stu-id="1a54c-128">Using NetX Secure</span></span>

<span data-ttu-id="1a54c-129">NetX Secure TLS の使用は簡単です。</span><span class="sxs-lookup"><span data-stu-id="1a54c-129">Using NetX Secure TLS is straightforward.</span></span> <span data-ttu-id="1a54c-130">基本的に、ThreadX と NetX を使用するために、アプリケーション コードには、*tx_api.h* と *nx_api.h* をインクルードした後に *nx_secure_tls_api.h* を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-130">Basically, the application code must include *nx_secure_tls_api.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="1a54c-131">*nx_secure_tls_api.h* をインクルードすると、アプリケーション コードは、このガイドの後半で指定している NetX Secure 関数呼び出しができるようになります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-131">Once *nx_secure_tls_api.h* is included, the application code is then able to make the NetX Secure function calls specified later in this guide.</span></span> <span data-ttu-id="1a54c-132">アプリケーションは *nx_secure\*\*.*</span><span class="sxs-lookup"><span data-stu-id="1a54c-132">The application must also import the *nx_secure\*\*.*</span></span> <span data-ttu-id="1a54c-133">ファイルを NetXSecure ライブラリにインポートし、プラットフォーム固有の *nx_crypto\*\*.*</span><span class="sxs-lookup"><span data-stu-id="1a54c-133">files into a NetXSecure library, and the platform-specific *nx_crypto\*\*.*</span></span> <span data-ttu-id="1a54c-134">ファイルを NetXCrypto ライブラリにインポートする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-134">files into a NetXCrypto library.</span></span>

## <a name="small-example-system-tls-client"></a><span data-ttu-id="1a54c-135">小さなシステム例 (TLS クライアント)</span><span class="sxs-lookup"><span data-stu-id="1a54c-135">Small Example System (TLS Client)</span></span>

<span data-ttu-id="1a54c-136">NetX Secure の使用がいかに簡単であるかを示す例について、下の図 1.1 で説明しています。</span><span class="sxs-lookup"><span data-stu-id="1a54c-136">An example of how easy it is to use NetX Secure is described in Figure 1.1, which appears below.</span></span> <span data-ttu-id="1a54c-137">これは、ソフトウェア暗号化モジュール (ハードウェア固有でない) を暗号化で使用する単純な TLS クライアントを示しています。</span><span class="sxs-lookup"><span data-stu-id="1a54c-137">This demonstrates a simple TLS Client, using software crypto modules (not hardware specific) for encryption.</span></span> <span data-ttu-id="1a54c-138">OpenSSL リバースエコー サーバー (openssl s_server -rev) と連携するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="1a54c-138">It is designed to work with the OpenSSL reverse-echo server (openssl s_server -rev).</span></span>

<span data-ttu-id="1a54c-139">この例を実行するために、x.509 CA 証明書を使用してターゲット サーバーの証明書を認証する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1a54c-139">Note that in order to run this example, you will need an X.509 CA certificate to authenticate your target server's certificate.</span></span> <span data-ttu-id="1a54c-140">OpenSSL の例では、単純な 2 レベル PKI (ルート CA 証明書 -> >サーバー証明書) で十分です。</span><span class="sxs-lookup"><span data-stu-id="1a54c-140">For the OpenSSL example, a simple 2-level PKI (root CA certificate-> >server certificate) will suffice.</span></span> <span data-ttu-id="1a54c-141">"trusted_ca_data" 配列に DER エンコード バイナリ バージョンの CA 証明書を入力し、"trusted_ca_length" 変数を証明書の実際の長さが反映されるよう更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-141">You will need to fill in the "trusted_ca_data" array with a DER-encoded binary version of your CA certificate and update the "trusted_ca_length" variable to reflect your certificate's actual length.</span></span>

<span data-ttu-id="1a54c-142">また、ハードウェアのネットワーク ドライバーも必要になります (nx_ip_create 呼び出しで "nx_driver_xx" パラメーターを置き換えます)。</span><span class="sxs-lookup"><span data-stu-id="1a54c-142">You will also need the network driver for your hardware (replace "nx_driver_xx" parameter in nx_ip_create call).</span></span>

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_tls_api.h"
#include "nx_secure_x509.h"

/* Define the size of our application stack. */
#define     DEMO_STACK_SIZE             4096

/* Define the remote server IP address using NetX IP_ADDRESS macro. */
#define     REMOTE_SERVER_IP_ADDRESS    IP_ADDRESS(192, 168, 1, 1)

/* Define the IP address for this device. */
#define     DEVICE_IP_ADDRESS           IP_ADDRESS(192, 168, 1, 2)

/* Define the remote server port. 443 is the HTTPS default. */
#define     REMOTE_SERVER_PORT          443

/* Define the ThreadX and NetX object control blocks...  */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Define an HTTP request to be sent to the HTTPS web server not defined here but
  represented by the ellipsis. */
UCHAR http_request[] = { "GET /example.html HTTP/1.1"  };

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];

/* Define the TLS Client thread.  */
ULONG             tls_client_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         tls_client_thread;
void              client_thread_entry(ULONG thread_input);

/* Define the TLS packet reassembly buffer. */
UCHAR tls_packet_buffer[18000];

/* Define the metadata area for TLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR tls_crypto_metadata[18000];

/* Pointer to the TLS ciphersuite table that is included in the platform-specific
   cryptography subdirectory. The table maps the cryptographic routines for the
   platform to function pointers usable by the TLS library.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers_ecc;
extern const USHORT nx_crypto_ecc_supported_groups[];
extern const NX_CRYPTO_METHOD *nx_crypto_ecc_curves[];
extern const UINT nx_crypto_ecc_supported_groups_size;

/* Binary data for the TLS Client X.509 trusted root CA certificate, ASN.1 DER-
   encoded. A trusted certificate must be provided for TLS Client applications
   (unless X.509 authentication is disabled) or TLS will treat all certificates as
   untrusted and the handshake will fail.
*/

/* DER-encoded binary certificate, not defined here but represented by the ellipsis,
   for the sake of brevity. */
const UCHAR trusted_ca_data[] = { … };
const UINT trusted_ca_length = 0x574;

/* Define the application – initialize drivers and TCP/IP setup.
   NOTE: the variable “status” should be checked after every API call. Most error
         checking has been omitted for clarity. */
void    tx_application_define(void *first_unused_memory)
{
UINT  status;

   /* Initialize the NetX system.  */
   nx_system_initialize();

   /* Create a packet pool. Check status for errors. */
   status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,
                                   (ULONG*)(((int)packet_pool_area + 64) & ~63) ,
                                   NX_PACKET_POOL_SIZE);

   /* Create an IP instance for the specific target. Check status for errors. This
      call is not completely defined. Please see other demo files for proper usage
      of the nx_ip_create call. */
   status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                         DEVICE_IP_ADDRESS ,
                         0xFFFFFF00UL,
                         &pool_0, nx_driver_xx,
                         (UCHAR*)ip_thread_stack,
                         sizeof(ip_thread_stack),
                         1);

   /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
       errors. */
   status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

   /* Enable TCP traffic. Check status for errors. */
   status =  nx_tcp_enable(&ip_0);

   status =  nx_ip_fragment_enable(&ip_0);

   /* Initialize the NetX Secure TLS system.  */
   nx_secure_tls_initialize();

    /* Create the TLS client thread to start handling incoming requests. */
   tx_thread_create(&tls_client_thread, "TLS Client thread", client_thread_entry, 0,
                     tls_client_thread_stack, sizeof(tls_client_thread_stack),
                     16, 16, 4, TX_AUTO_START);
   return;
}

/* Thread to handle the TLS Client instance. */
void client_thread_entry(ULONG thread_input)
{
UINT       status;
ULONG       actual_status;
NX_PACKET *send_packet;
NX_PACKET *receive_packet;
UCHAR receive_buffer[100];
ULONG bytes;
ULONG server_ipv4_address;

    /* We are not using the thread input parameter so suppress compiler warning. */
    NX_PARAMETER_NOT_USED(thread_input);

   /* Ensure the IP instance has been initialized.  */
   status =  nx_ip_status_check(&ip_0, NX_IP_INITIALIZE_DONE, &actual_status,
                                 NX_IP_PERIODIC_RATE);

   /* Create a TCP socket to use for our TLS session.  */
   status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Client Socket",
                                  NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                  NX_IP_TIME_TO_LIVE, 8192, NX_NULL, NX_NULL);

   /* Create a TLS session for our socket. This sets up the TLS session object for
          later use */
   status =  nx_secure_tls_session_create(&tls_session,
                                          &nx_crypto_tls_ciphers_ecc,
                                          tls_crypto_metadata,
                                          sizeof(tls_crypto_metadata));

   /* Initialize ECC parameters for this session. */
   status = nx_secure_tls_ecc_initialize(&tls_session,
                                             nx_crypto_ecc_supported_groups,
                                             nx_crypto_ecc_supported_groups_size,
                                             nx_crypto_ecc_curves);

   /* Set the packet reassembly buffer for this TLS session. */
   status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                    sizeof(tls_packet_buffer));

   /* Initialize an X.509 certificate with our CA root certificate data. */
   nx_secure_x509_certificate_initialize(&certificate, trusted_ca_data,
                                         trusted_ca_length, NX_NULL, 0, NX_NULL, 0,
                                         NX_SECURE_X509_KEY_TYPE_NONE);

   /* Add the initialized certificate as a trusted root certificate. */
   nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);

   /* Setup this thread to open a connection on the TCP socket to a remote server.
      The IP address can be used directly or it can be obtained via DNS or other
      means.*/
   server_ipv4_address = REMOTE_SERVER_IP_ADDRESS;
   status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
                                         REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

   /* Start the TLS Session using the connected TCP socket. This function will
      ascertain from the TCP socket state that this is a TLS Client session. */
   status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                         NX_WAIT_FOREVER);

    /* Allocate a TLS packet to send an HTTP request over TLS (HTTPS). */
    status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                          NX_WAIT_FOREVER);

    /* Populate the packet with our HTTP request. */
    nx_packet_data_append(send_packet, http_request, sizeof(http_request), &pool_0,
                          NX_WAIT_FOREVER);


   /* Send the HTTP request over the TLS Session, turning it into HTTPS. */
   status = nx_secure_tls_session_send(&tls_session, send_packet, NX_WAIT_FOREVER);

   /* If the send fails, you must release the packet.  */
   if (status != NX_SUCCESS)
   {
         /* Release the packet since the packet was not sent.  */
         nx_packet_release(send_packet);
   }

   /* Receive the HTTP response and any data from the server. */
   status = nx_secure_tls_session_receive(&tls_session, &receive_packet,
   NX_WAIT_FOREVER);
   if (status == NX_SUCCESS)
   {
       /* Extract the data we received from the remote server. */
       status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer,
                                             100,  &bytes);
        /* Display the response data. */
       receive_buffer[bytes] = 0;
       printf("Received data: %s\n", receive_buffer);

        /* Release the packet when done with it. */
       nx_packet_release(receive_packet);
   }

   /* End the TLS session now that we have received our HTTPS/HTML response. */
   status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

   /* Check for errors to make sure the session ended cleanly. */

   /* Disconnect the TCP socket. */
   status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

}
```

<span data-ttu-id="1a54c-143">**図 1.1 NetX を使用した NetX Secure の使用例**</span><span class="sxs-lookup"><span data-stu-id="1a54c-143">**Figure 1.1 Example of NetX Secure use with NetX**</span></span>

## <a name="small-example-system-tls-web-server"></a><span data-ttu-id="1a54c-144">小さなシステム例 (TLS Web サーバー)</span><span class="sxs-lookup"><span data-stu-id="1a54c-144">Small Example System (TLS Web Server)</span></span>

<span data-ttu-id="1a54c-145">NetX Secure の使用がいかに簡単であるかの例を、下の図 1.1 で説明しています。これは、単純な TLS Web サーバー (HTTPS) を示しています。</span><span class="sxs-lookup"><span data-stu-id="1a54c-145">An example of how easy it is to use NetX Secure is described in Figure 1.1, which appears below and demonstrates a simple TLS Web Server (HTTPS).</span></span>

<span data-ttu-id="1a54c-146">この例を実行するためには、サーバーを TLS クライアントに識別させるための X.509 証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="1a54c-146">Note that in order to run this example, you will need an X.509 certificate to identify your server to TLS clients.</span></span> <span data-ttu-id="1a54c-147">ほとんどの Web ブラウザーでは、単純な自己署名証明書で十分です。</span><span class="sxs-lookup"><span data-stu-id="1a54c-147">For most web browers a simple self-signed certificate should be sufficient.</span></span> <span data-ttu-id="1a54c-148">ブラウザーでサーバーを認証できないというメッセージが表示され、場合によってはサーバーと TLS/HTTPS 接続を確立できない場合があります<sup>3</sup>。</span><span class="sxs-lookup"><span data-stu-id="1a54c-148">Your browser will complain about not being able to authenticate the server and in some cases may be unable to establish a TLS/HTTPS connection to your server<sup>3</sup>.</span></span> <span data-ttu-id="1a54c-149">"certificate_data" 配列に DER エンコード バイナリ バージョンのサーバー証明書を入力し、"certificate_length" 変数を証明書の実際の長さが反映されるよう更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-149">You will need to fill in the "certificate_data" array with a DER-encoded binary version of your server certificate and update the "certificate_length" variable to reflect your certificate's actual length.</span></span> <span data-ttu-id="1a54c-150">また、"private_key" 配列に、RSA キーの場合は PKCS#1、ECC キーの場合は RFC 5915 を使用して書式設定された、DER エンコード バージョンの証明書の秘密キーを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-150">You also need to fill in the "private_key" array with a DER-encoded version of your certificate's private key, formatted using PKCS#1 for RSA key and RFC 5915 for ECC keys.</span></span> <span data-ttu-id="1a54c-151">"private_key_length" 変数にキー データの実際の長さを入力します。</span><span class="sxs-lookup"><span data-stu-id="1a54c-151">Fill in the "private_key_length" variable with the actual length of your key data.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1a54c-152">一部のブラウザー (特に Chrome ブラウザーの一部のバージョン) が、自己署名証明書を拒否する場合があります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-152">Some browsers (particularly some versions of the Chrome browser) may reject self-signed certificates.</span></span> <span data-ttu-id="1a54c-153">この場合、サーバー証明書の署名に使用するルート CA 証明書を使用した 2 レベルの PKI を作成できます。</span><span class="sxs-lookup"><span data-stu-id="1a54c-153">In this case you can create a 2-level PKI with a root CA certificate that is used to sign your server certificate.</span></span> <span data-ttu-id="1a54c-154">この場合、ルート CA 証明書は、信頼されたルート証明書としてブラウザーにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="1a54c-154">In this situation, the root CA certificate is installed as a trusted root certificate in your browser.</span></span> <span data-ttu-id="1a54c-155">!!!</span><span class="sxs-lookup"><span data-stu-id="1a54c-155">!!!</span></span> <span data-ttu-id="1a54c-156">重要 - 終わったらルート CA 証明書をブラウザーから削除して、運用アプリケーションで使用しないようにしてください!!!</span><span class="sxs-lookup"><span data-stu-id="1a54c-156">IMPORTANT – remove your root CA certificate from your browser when done and do not use it for any production applications !!!</span></span>

<span data-ttu-id="1a54c-157">また、ハードウェアのネットワーク ドライバーも必要になります (nx_ip_create 呼び出しで "nx_driver_xx" パラメーターを置き換えます)。</span><span class="sxs-lookup"><span data-stu-id="1a54c-157">You will also need the network driver for your hardware (replace "nx_driver_xx" parameter in nx_ip_create call).</span></span>

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_tls_api.h"
#include "nx_secure_x509.h"

#define     DEMO_STACK_SIZE         4096

/* Define the IP address for this device. */
#define     DEVICE_IP_ADDRESS             IP_ADDRESS(192, 168, 1, 2)

/* Define the ThreadX and NetX object control blocks...  */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];


/* Define the TLS Server thread.  */
ULONG             tls_server_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         tls_server_thread;
void              server_thread_entry(ULONG thread_input);

/* Define the TLS packet reassembly buffer. */
UCHAR tls_packet_buffer[18000];

/* Define the metadata area for TLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR tls_crypto_metadata[18000];

/* Pointer to the TLS ciphersuite table that is included in the platform-specific
   cryptography subdirectory. The table maps the cryptographic routines for the
   platform to function pointers usable by the TLS library.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers_ecc;
extern const USHORT nx_crypto_ecc_supported_groups[];
extern const NX_CRYPTO_METHOD *nx_crypto_ecc_curves[];
extern const UINT nx_crypto_ecc_supported_groups_size;

/* Binary data for the TLS Server X.509 certificate, ASN.1 DER-encoded. Note that the
   certificate data and private key data is represented by an ellipsis for the sake
   of brevity.
*/
const UCHAR certificate_data[] = { … }; /* DER-encoded binary certificate. */
const UINT certificate_length = 0x574;

/* Binary data for the TLS Server Private Key, from private key
   file generated at the time of the X.509 certificate creation. ASN.1 DER-encoded. */
const UCHAR private_key[] = { … }; /* DER-encoded private key file (PKCS#1 RSA or ECC) */
const UINT private_key_length = 0x40;

/* Define some HTML data (web page) with an HTTPS header to serve to connecting
   clients. */
UCHAR html_data[] = { "HTTP/1.1 200 OK\r\n" \
        "Date: Tue, 19 May 2020 23:59:59 GMT\r\n" \
        "Content-Type: text/html\r\n" \
        "Content-Length: 200\r\n\r\n" \
        "<html>\r\n"\
        "<body>\r\n"\
        "<b>Hello NetX Secure User!</b>\r\n"\
        "This is a simple webpage\r\n"\
        "served up using NetX Secure!\r\n"\
        "</body>\r\n"\
        "</html>\r\n" };

/* Define the application – initialize drivers and TCP/IP setup.  */
void    tx_application_define(void *first_unused_memory)
{
UINT  status;


    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create a packet pool. Check status for errors. */
    status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,
                                    (ULONG*)(((int)packet_pool_area + 64) & ~63) ,
                                    NX_PACKET_POOL_SIZE);

    /* Create an IP instance for the specific target. Check status for errors. */
    status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                          DEVICE_IP_ADDRESS,
                          0xFFFFFF00UL,
                          &pool_0, nx_driver_xx,
                          (UCHAR*)ip_thread_stack,
                          sizeof(ip_thread_stack),
                          1);

    /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
         errors. */
    status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

    /* Enable TCP traffic. Check status for errors. */
    status =  nx_tcp_enable(&ip_0);

    status =  nx_ip_fragment_enable(&ip_0);

    /* Initialize the NetX Secure TLS system.  */
    nx_secure_tls_initialize();

    /* Create the TLS server thread to start handling incoming requests. */
    tx_thread_create(&tls_server_thread, "TLS Server thread", server_thread_entry, 0,
                   tls_server_thread_stack, sizeof(tls_server_thread_stack),
                   16, 16, 4, TX_AUTO_START);
    return;
}

/* Thread to handle the TLS Server instance. */
void server_thread_entry(ULONG thread_input)
{
UINT       status;
ULONG      actual_status;
NX_PACKET *send_packet;
NX_PACKET *receive_packet;
UCHAR receive_buffer[100];
ULONG bytes;

    NX_PARAMETER_NOT_USED(thread_input);

    /* Ensure the IP instance has been initialized.  */
    status =  nx_ip_status_check(&ip_0, NX_IP_INITIALIZE_DONE, &actual_status,
                                 NX_IP_PERIODIC_RATE);

    /* Create a TCP socket to use for our TLS session.  */
    status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket",
                                   NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                   NX_IP_TIME_TO_LIVE, 8192, NX_NULL, NX_NULL);

    /* Create a TLS session for our socket.  */
    status =  nx_secure_tls_session_create(&tls_session,
                                        &nx_crypto_tls_ciphers_ecc,
                                        tls_crypto_metadata,
                                        sizeof(tls_crypto_metadata));

    status = nx_secure_tls_ecc_initialize(&tls_session,
                                          nx_crypto_ecc_supported_groups,
                                          nx_crypto_ecc_supported_groups_size,
                                          nx_crypto_ecc_curves);

     /* Set the packet reassembly buffer for this TLS session. */
     status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                      sizeof(tls_packet_buffer));

    /* Initialize an X.509 certificate and private ECC key for our TLS Session. */
    nx_secure_x509_certificate_initialize(&certificate, certificate_data, NX_NULL, 0,
                                          certificate_length, private_key,
                                          private_key_length,
                                          NX_SECURE_X509_KEY_TYPE_EC_DER);

    /* Add the initialized certificate as a local identity certificate. */
    nx_secure_tls_local_certificate_add(&tls_session, &certificate);


    /* Setup this thread to listen on the TCP socket.
       Port 443 is standard for HTTPS. */
    status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

    while(1)
     {
         /* Accept a client TCP socket connection.  */
         status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

         /* Start the TLS Session using the connected TCP socket. */
         status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                              NX_WAIT_FOREVER);

         /* Receive the HTTPS request. */
         status = nx_secure_tls_session_receive(&tls_session, &receive_packet,
                                                NX_WAIT_FOREVER);

if (status == NX_SUCCESS)
      {
         /* Extract the HTTP request information from the HTTPS request. */
            status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer,
                                                  100, &bytes);
         /* Display the HTTP request data. */
            receive_buffer[bytes] = 0;
            printf("Received data: %s\n", receive_buffer);

         /* Release the packet when done with it */
            nx_packet_release(receive_packet);
      }

         /* Allocate a TLS packet to send HTML data back to client. */
         status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                                NX_WAIT_FOREVER);

         /* Populate the packet with our HTTP response and HTML web page data. */
         nx_packet_data_append(send_packet, html_data, sizeof(html_data), &pool_0,
                               NX_WAIT_FOREVER);

         /* Send the HTTP response over the TLS Session, turning it into HTTPS. */
         status = nx_secure_tls_session_send(&tls_session, send_packet,
                                                 NX_WAIT_FOREVER);

         /* If the send fails, you must release the packet.  */
         if (status != NX_SUCCESS)
         {
              /* Release the packet since it was not sent.  */
              nx_packet_release(send_packet);
         }

         /* End the TLS session now that we have sent our HTTPS/HTML response. */
         status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

         /* Check for errors to make sure the session ended cleanly! */

         /* Disconnect the TCP socket so we can be ready for the next request. */
         status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

         /* Unaccept the server socket.  */
         status =  nx_tcp_server_socket_unaccept(&tcp_socket);

         /* Setup server socket for listening again.  */
         status =  nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
     }
}
```

<span data-ttu-id="1a54c-158">**図 1.2 NetX を使用した NetX Secure の使用例**</span><span class="sxs-lookup"><span data-stu-id="1a54c-158">**Figure 1.2 Example of NetX Secure use with NetX**</span></span>

## <a name="a-note-on-tls-session-error-recovery"></a><span data-ttu-id="1a54c-159">TLS セッション エラー回復に関する注意事項</span><span class="sxs-lookup"><span data-stu-id="1a54c-159">A Note on TLS Session Error Recovery</span></span>

<span data-ttu-id="1a54c-160">上記のシステム例は、TLS クライアントとサーバーそれぞれの基本的な概要を示していますが、わかりやすいように、エラー処理は省略しています。</span><span class="sxs-lookup"><span data-stu-id="1a54c-160">The example systems described above show the basic outlines for a TLS Client and Server, respectively, but for clarity the error handling is omitted.</span></span> <span data-ttu-id="1a54c-161">ただし、TLS が提供するセキュリティの一部は、エラー状況の適切な処理に依存します。</span><span class="sxs-lookup"><span data-stu-id="1a54c-161">However, part of the security TLS provides is dependent on the proper handling of error conditions.</span></span> <span data-ttu-id="1a54c-162">一般に、最も深刻な潜在的問題は TLS スタック自体の中で処理されますが、重要なのは TLS アプリケーションが TLS 実装内で処理されない TLS エラーに対して適切に対応して復旧することです。</span><span class="sxs-lookup"><span data-stu-id="1a54c-162">Generally, the most serious potential problems will be handled within the TLS stack itself, but it is important for the TLS application to properly respond to and recover from TLS errors that are not handled within the TLS implementation.</span></span>

<span data-ttu-id="1a54c-163">適切なエラー処理に必要なロジックを説明するために、次の関数は、TLS エラーを適切に処理して、エラー状態が発生した後の TLS 状態をクリーン リセットするために使用できる一般的な API サービスを示しています。</span><span class="sxs-lookup"><span data-stu-id="1a54c-163">In order to illustrate the necessary logic for proper error handling, the following function demonstrates a typical collection of API services that can be used to properly handle TLS errors and cleanly reset the TLS state after an error condition is encountered.</span></span> <span data-ttu-id="1a54c-164">ここで説明したセクション以外に、このロジックは TLS クライアントと TLS サーバーの両インスタンスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="1a54c-164">Other than the section where noted, the logic applies to both TLS Client and TLS Server instances.</span></span>

<span data-ttu-id="1a54c-165">関数の中で最も重要な API 呼び出しは、TLS セッションまたはハンドシェイクを完全に終了する *nx_secure_tls_session_end* サービスに対する呼び出しと、 TLS セッション状態をクリアして tls_session 制御構造インスタンスを新しい TLS セッションで再利用できるようにする *nx_secure_tls_session_reset* サービスに対する呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="1a54c-165">Note that the most important API calls in the function are to the services *nx_secure_tls_session_end*, which cleanly closes the TLS session or handshake, and *nx_secure_tls_session_reset*, which clears the TLS session state so the tls_session control structure instance can be reused for a new TLS session.</span></span> <span data-ttu-id="1a54c-166">また、*nx_secure_tls_session_reset* では証明書や割り当てバッファーなどのユーザーが構成した状態がクリアされないため、*nx_secure_tls_session_create* を再度呼び出すことなくセッションを再利用できます。</span><span class="sxs-lookup"><span data-stu-id="1a54c-166">Also note that *nx_secure_tls_session_reset* does not clear the user-configured state such as certificates or assigned buffers, allowing the session to be reused without calling *nx_secure_tls_session_create* again.</span></span> <span data-ttu-id="1a54c-167">すべての TLS セッション状態を完全クリアするには、*nx_secure_tls_session_delete* サービスを代わりに使用できます。</span><span class="sxs-lookup"><span data-stu-id="1a54c-167">To completely clear all TLS session state, the service *nx_secure_tls_session_delete* may be used instead.</span></span>

```C
/* Define a helper function to clean up a broken TLS session (to be called on any
   error from nx_secure_tls_session_start onwards). Note that the variables
   tls_session, tcp_socket, and ip_0 are global in the above examples. */
VOID tls_session_error_cleanup(VOID)
{
UINT status;
UINT alert_level, alert_value;

      /* If we got an error back from a TLS API call, there may be an alert from the
         remote host. Extract the alert level and value to print out. Note that the TLS
         API will return NX_SECURE_TLS_ALERT_RECEIVED (0x114) if an alert was received.
         For other error codes the alert value and level are not valid. */
      status = nx_secure_tls_session_alert_value_get(&tls_session, &alert_level,
                                                     &alert_value);
      if(status)
      {
         printf("Pointer error in getting alert value.\n");
      }
      else
      {
         printf("Alert recieved. Value: %d, Level: %d\n", alert_value, alert_level);
      }

      /* End the TLS session. This is required to properly shut down the TLS
         connection. */
      status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

      /* If the session did not shut down cleanly, this is a possible security issue. */
      if (status)
      {
         printf("Error in TLS session end: %x\n", status);
      }

      /* Reset the TLS session to re-use the control structure for the next connection.
         This API service resets the TLS session state but does not remove user-
         configured options such as certificates, PSKs, buffers, and cipher routines. */
      nx_secure_tls_session_reset(&tls_session);

      /* Disconnect the TCP socket, closing the connection. */
      status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket close: %x\n", status);
      }

   /* The following code applies only to a TLS server instance. */
   #if NX_SECURE_TLS_SERVER
      /* Unaccept the server socket.  */
      status =  nx_tcp_server_socket_unaccept(&tcp_socket);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket unaccept: %x\n", status);
      }

      /* Setup server socket for listening again.  */
      status =  nx_tcp_server_socket_relisten(&ip_0, DEVICE_SERVER_PORT, &tcp_socket);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket relisten: %x\n", status);
      }
#endif
} /* End function. */
```

## <a name="configuration-options"></a><span data-ttu-id="1a54c-168">構成オプション</span><span class="sxs-lookup"><span data-stu-id="1a54c-168">Configuration Options</span></span>

<span data-ttu-id="1a54c-169">NetX Secure を構築するためのいくつかの構成オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-169">There are several configuration options for building NetX Secure.</span></span> <span data-ttu-id="1a54c-170">以下に示すすべてのオプションの一覧で、それぞれのオプションについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="1a54c-170">Following is a list of all options, where each is described in detail:</span></span>

| <span data-ttu-id="1a54c-171">定義</span><span class="sxs-lookup"><span data-stu-id="1a54c-171">Define</span></span> | <span data-ttu-id="1a54c-172">意味</span><span class="sxs-lookup"><span data-stu-id="1a54c-172">Meaning</span></span> |
|----------------------|------------------------------------------------|
| <span data-ttu-id="1a54c-173">**NX_SECURE_DISABLE_ERROR_CHECKING**</span><span class="sxs-lookup"><span data-stu-id="1a54c-173">**NX_SECURE_DISABLE_ERROR_CHECKING**</span></span>                | <span data-ttu-id="1a54c-174">このオプションを定義すると、基本的な NetX Secure エラー チェックが削除されます。</span><span class="sxs-lookup"><span data-stu-id="1a54c-174">Defined, this option removes the basic NetX Secure error checking.</span></span> <span data-ttu-id="1a54c-175">通常は、アプリケーションがデバッグされた後に使用します。</span><span class="sxs-lookup"><span data-stu-id="1a54c-175">It is typically used after the application has been debugged.</span></span> |
| <span data-ttu-id="1a54c-176">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**</span><span class="sxs-lookup"><span data-stu-id="1a54c-176">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**</span></span>                  | <span data-ttu-id="1a54c-177">このオプションを定義すると、予想される RSA 最大係数がビット単位で提供されます。</span><span class="sxs-lookup"><span data-stu-id="1a54c-177">Defined, this option gives the maximum RSA modulus expected, in bits.</span></span> <span data-ttu-id="1a54c-178">4096 ビット係数の既定値は 4096 です。</span><span class="sxs-lookup"><span data-stu-id="1a54c-178">The default value is 4096 for a 4096-bit modulus.</span></span> <span data-ttu-id="1a54c-179">他に 3072、2048、または 1024 の値を指定できます (推奨されません)。</span><span class="sxs-lookup"><span data-stu-id="1a54c-179">Other values can be 3072, 2048, or 1024 (not recommended).</span></span> |
| <span data-ttu-id="1a54c-180">**NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES**</span><span class="sxs-lookup"><span data-stu-id="1a54c-180">**NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES**</span></span>        | <span data-ttu-id="1a54c-181">このオプションを定義すると、TLS がリモート ホストから自己署名証明書を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="1a54c-181">Defined, this option allows TLS to accept self-signed certificates from a remote host.</span></span> <span data-ttu-id="1a54c-182">既定では、TLS はセキュリティ上の理由で自己署名サーバー証明書を拒否します。</span><span class="sxs-lookup"><span data-stu-id="1a54c-182">By default, TLS will reject self-signed server certificates as a security precaution.</span></span> <span data-ttu-id="1a54c-183">このマクロが定義されている場合は、自己署名証明書を信頼ストアに追加して、受け入れられるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-183">If this macro is defined, self-signed certificates must still be added to the trusted store to be accepted.</span></span> |
| <span data-ttu-id="1a54c-184">**NX_SECURE_ENABLE_CLIENT_CERTIFICATE_VERIFY**</span><span class="sxs-lookup"><span data-stu-id="1a54c-184">**NX_SECURE_ENABLE_CLIENT_CERTIFICATE_VERIFY**</span></span>      | <span data-ttu-id="1a54c-185">このオプションを定義すると、オプションの X.509 クライアント証明書検証が TLS サーバーに対して有効になります<sup>4</sup>。</span><span class="sxs-lookup"><span data-stu-id="1a54c-185">Defined, this option enables the optional X.509 Client Certificate Verification for TLS Servers<sup>4</sup>.</span></span>  |
| <span data-ttu-id="1a54c-186">**NX_SECURE_ENABLE_PSK_CIPHERSUITES**</span><span class="sxs-lookup"><span data-stu-id="1a54c-186">**NX_SECURE_ENABLE_PSK_CIPHERSUITES**</span></span>               | <span data-ttu-id="1a54c-187">このオプションを定義すると、事前共有キー (PSK) 機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-187">Defined, this option enables Pre-Shared Key (PSK) functionality.</span></span> <span data-ttu-id="1a54c-188">デジタル証明書は無効になりません。</span><span class="sxs-lookup"><span data-stu-id="1a54c-188">It does not disable digital certificates.</span></span> |
| <span data-ttu-id="1a54c-189">**NX_SECURE_TLS_CLIENT_DISABLED**</span><span class="sxs-lookup"><span data-stu-id="1a54c-189">**NX_SECURE_TLS_CLIENT_DISABLED**</span></span>                   | <span data-ttu-id="1a54c-190">このオプションを定義すると、TLS クライアント モードに関連するすべての TLS スタック コードが削除され、コードとデータの使用量が減ります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-190">Defined, this option removes all TLS stack code related to TLS Client mode, reducing code and data usage.</span></span> |
| <span data-ttu-id="1a54c-191">**NX_SECURE_TLS_SERVER_DISABLED**</span><span class="sxs-lookup"><span data-stu-id="1a54c-191">**NX_SECURE_TLS_SERVER_DISABLED**</span></span>                   | <span data-ttu-id="1a54c-192">このオプションを定義すると、TLS サーバー モードに関連するすべての TLS スタック コードが削除され、コードとデータの使用量が減ります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-192">Defined, this option removes all TLS stack code related to TLS Server mode, reducing code and data usage.</span></span>  |
| <span data-ttu-id="1a54c-193">**NX_SECURE_DISABLE_ECC_CIPHERSUITE**</span><span class="sxs-lookup"><span data-stu-id="1a54c-193">**NX_SECURE_DISABLE_ECC_CIPHERSUITE**</span></span>               | <span data-ttu-id="1a54c-194">このオプションを定義すると、楕円曲線暗号 (ECC) 暗号スイートのすべての TLS ロジックが削除されます。</span><span class="sxs-lookup"><span data-stu-id="1a54c-194">Defined, this option removes all TLS logic for Elliptic Curve Cryptography (ECC) ciphersuites.</span></span> <span data-ttu-id="1a54c-195">これらの暗号スイートは TLS 1.2 以前では省略可能であり、無効にすると、コードとデータのサイズが大きく減る可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-195">These ciphersuites are optional in TLS 1.2 and earlier and disabling them can result in significant code and data size reduction.</span></span>|
| <span data-ttu-id="1a54c-196">**NX_SECURE_TLS_ENABLE_TLS_1_3**</span><span class="sxs-lookup"><span data-stu-id="1a54c-196">**NX_SECURE_TLS_ENABLE_TLS_1_3**</span></span>                    | <span data-ttu-id="1a54c-197">このオプションを定義すると、TLSv1.3 モードが有効になります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-197">Defined, this option enables TLSv1.3 mode.</span></span> <span data-ttu-id="1a54c-198">TLS 1.3 は最新バージョンの TLS であり、既定では無効になっています。</span><span class="sxs-lookup"><span data-stu-id="1a54c-198">TLS 1.3 is the newest version of TLS and is disabled by default.</span></span> |
| <span data-ttu-id="1a54c-199">**NX_SECURE_TLS_ENABLE_TLS_1_0**</span><span class="sxs-lookup"><span data-stu-id="1a54c-199">**NX_SECURE_TLS_ENABLE_TLS_1_0**</span></span>                    | <span data-ttu-id="1a54c-200">このオプションを定義すると、従来の TLSv1.0 モードが有効になります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-200">Defined, this option enables the legacy TLSv1.0 mode.</span></span> <span data-ttu-id="1a54c-201">TLSv1.0 は廃止と見なされているため、有効にするのは古いアプリケーションとの下位互換性のためだけにしてください。</span><span class="sxs-lookup"><span data-stu-id="1a54c-201">TLSv1.0 is considered obsolete so it should only be enabled for backward-compatibility with older applications.</span></span> |
| <span data-ttu-id="1a54c-202">**NX_SECURE_TLS_ENABLE_TLS_1_1**</span><span class="sxs-lookup"><span data-stu-id="1a54c-202">**NX_SECURE_TLS_ENABLE_TLS_1_1**</span></span>                    | <span data-ttu-id="1a54c-203">このオプションを定義すると、従来の TLSv1.1 モードが有効になります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-203">Defined, this option enables the legacy TLSv1.1 mode.</span></span> <span data-ttu-id="1a54c-204">TLSv1.1 は廃止と見なされているため、有効にするのは古いアプリケーションとの下位互換性のためだけにしてください。</span><span class="sxs-lookup"><span data-stu-id="1a54c-204">TLSv1.1 is considered obsolete so it should only be enabled for backward-compatibility with older applications.</span></span> |
| <span data-ttu-id="1a54c-205">**NX_SECURE_TLS_DISABLE_TLS_1_1**</span><span class="sxs-lookup"><span data-stu-id="1a54c-205">**NX_SECURE_TLS_DISABLE_TLS_1_1**</span></span>                   | <span data-ttu-id="1a54c-206">このオプションを定義すると、TLSv1.1 モードが無効になります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-206">Defined, this option disables TLSv1.1 mode.</span></span> <span data-ttu-id="1a54c-207">既定では定義されています。</span><span class="sxs-lookup"><span data-stu-id="1a54c-207">It is defined by default.</span></span> <span data-ttu-id="1a54c-208">TLSv 1.1 が無効になっているのは、より安全な TLSv1.2 だけを使用することを優先しているためです<sup>5</sup>。</span><span class="sxs-lookup"><span data-stu-id="1a54c-208">TLSv1.1 is disabled in favor of using only the more-secure TLSv1.2<sup>5</sup>.</span></span>  |
| <span data-ttu-id="1a54c-209">**NX_SECURE_X509_STRICT_NAME_COMPARE**</span><span class="sxs-lookup"><span data-stu-id="1a54c-209">**NX_SECURE_X509_STRICT_NAME_COMPARE**</span></span>              | <span data-ttu-id="1a54c-210">このオプションを定義すると、証明書の検索と検証で X.509 証明書の厳密な識別名の比較が可能になります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-210">Defined, this option enables strict distinguished name comparison for X.509 certificates for certificate searching and verification.</span></span> <span data-ttu-id="1a54c-211">既定では、識別名の「共通名」フィールドの比較だけが行われます。</span><span class="sxs-lookup"><span data-stu-id="1a54c-211">The default is to only compare the Common Name fields of the Distinguished Names.</span></span>|
| <span data-ttu-id="1a54c-212">**NX_SECURE_X509_USE_EXTENDED_DISTINGUISHED_NAMES**</span><span class="sxs-lookup"><span data-stu-id="1a54c-212">**NX_SECURE_X509_USE_EXTENDED_DISTINGUISHED_NAMES**</span></span> | <span data-ttu-id="1a54c-213">このオプションを定義するとオプションの「X.509 識別名」フィールドが有効になり、余分なメモリが X.509 証明書で消費されます。</span><span class="sxs-lookup"><span data-stu-id="1a54c-213">Defined, this option enables the optional X.509 Distinguished Name fields, at the expense of extra memory use for X.509 certificates.</span></span> |

4. <span data-ttu-id="1a54c-214">このオプションで有効になるのは、コードがアプリケーションにリンクされることだけです。</span><span class="sxs-lookup"><span data-stu-id="1a54c-214">Note that this option only enables the code to be linked into the application.</span></span> <span data-ttu-id="1a54c-215">この機能は API サービス nx_secure_tls_session_client_verify_enable で有効にするか、クライアント証明書検証を使用するために nx_secure_tls_session_x509_client_verify_configure を使用して構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a54c-215">The feature will need to be enabled with the API service nx_secure_tls_session_client_verify_enable or configured using nx_secure_tls_session_x509_client_verify_configure in order to use Client Certificate Verification.</span></span>

5. <span data-ttu-id="1a54c-216">TLS 1.0 または TLS 1.1 のみを使用している場合は、TLSv1.2 も無効にすることが可能です。</span><span class="sxs-lookup"><span data-stu-id="1a54c-216">Note that it is also possible to disable TLSv1.2 if using TLS 1.0 or TLS 1.1 only.</span></span> <span data-ttu-id="1a54c-217">ただし、これは推奨されておらず、直接サポートされているわけでありません。</span><span class="sxs-lookup"><span data-stu-id="1a54c-217">However, this is not recommended and not directly supported.</span></span>
