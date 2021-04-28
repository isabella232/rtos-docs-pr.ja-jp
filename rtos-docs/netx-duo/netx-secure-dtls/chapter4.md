---
title: 第 4 章 - Azure RTOS NetX Secure DTLS サービスの説明
description: この章では、すべての Azure RTOS NetX Secure DTLS サービスをアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e795a5fa35a4590e508c7fe2eec53f5494809657
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810505"
---
# <a name="chapter-4-description-of-azure-rtos-netx-secure-dtls-services"></a><span data-ttu-id="8397b-103">第 4 章: Azure RTOS NetX Secure DTLS サービスの説明</span><span class="sxs-lookup"><span data-stu-id="8397b-103">Chapter 4: Description of Azure RTOS NetX Secure DTLS services</span></span>

<span data-ttu-id="8397b-104">この章では、すべての Azure RTOS NetX Secure DTLS サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="8397b-104">This chapter contains a description of all Azure RTOS NetX Secure DTLS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="8397b-105">以下の API の説明の「戻り値」セクションでは、**太字** の値は API エラー チェックを無効にする際に使用される **NX_SECURE_DISABLE_ERROR_CHECKING** マクロの影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="8397b-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_SECURE_DISABLE_ERROR_CHECKING** macro that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="8397b-106">nx_secure_dtls_client_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-106">nx_secure_dtls_client_session_start</span></span>](#nx_secure_dtls_client_session_start)
- [<span data-ttu-id="8397b-107">nx_secure_dtls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="8397b-107">nx_secure_dtls_packet_allocate</span></span>](#nx_secure_dtls_packet_allocate)
- [<span data-ttu-id="8397b-108">nx_secure_dtls_psk_add</span><span class="sxs-lookup"><span data-stu-id="8397b-108">nx_secure_dtls_psk_add</span></span>](#nx_secure_dtls_psk_add)
- [<span data-ttu-id="8397b-109">nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="8397b-109">nx_secure_dtls_server_create</span></span>](#nx_secure_dtls_server_create)
- [<span data-ttu-id="8397b-110">nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="8397b-110">nx_secure_dtls_server_delete</span></span>](#nx_secure_dtls_server_delete)
- [<span data-ttu-id="8397b-111">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-111">nx_secure_dtls_server_local_certificate_add</span></span>](#nx_secure_dtls_server_local_certificate_add)
- [<span data-ttu-id="8397b-112">nx_secure_dtls_server_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="8397b-112">nx_secure_dtls_server_local_certificate_remove</span></span>](#nx_secure_dtls_server_local_certificate_remove)
- [<span data-ttu-id="8397b-113">nx_secure_dtls_server_notify_set</span><span class="sxs-lookup"><span data-stu-id="8397b-113">nx_secure_dtls_server_notify_set</span></span>](#nx_secure_dtls_server_notify_set)
- [<span data-ttu-id="8397b-114">nx_secure_dtls_server_psk_add</span><span class="sxs-lookup"><span data-stu-id="8397b-114">nx_secure_dtls_server_psk_add</span></span>](#nx_secure_dtls_server_psk_add)
- [<span data-ttu-id="8397b-115">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="8397b-115">nx_secure_dtls_server_session_send</span></span>](#nx_secure_dtls_server_session_send)
- [<span data-ttu-id="8397b-116">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-116">nx_secure_dtls_server_session_start</span></span>](#nx_secure_dtls_server_session_start)
- [<span data-ttu-id="8397b-117">nx_secure_dtls_server_start</span><span class="sxs-lookup"><span data-stu-id="8397b-117">nx_secure_dtls_server_start</span></span>](#nx_secure_dtls_server_start)
- [<span data-ttu-id="8397b-118">nx_secure_dtls_server_stop</span><span class="sxs-lookup"><span data-stu-id="8397b-118">nx_secure_dtls_server_stop</span></span>](#nx_secure_dtls_server_stop)
- [<span data-ttu-id="8397b-119">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-119">nx_secure_dtls_server_trusted_certificate_add</span></span>](#nx_secure_dtls_server_trusted_certificate_add)
- [<span data-ttu-id="8397b-120">nx_secure_dtls_server_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="8397b-120">nx_secure_dtls_server_trusted_certificate_remove</span></span>](#nx_secure_dtls_server_trusted_certificate_remove)
- [<span data-ttu-id="8397b-121">nx_secure_dtls_server_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="8397b-121">nx_secure_dtls_server_x509_client_verify_configure</span></span>](#nx_secure_dtls_server_x509_client_verify_configure)
- [<span data-ttu-id="8397b-122">nx_secure_dtls_server_x509_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="8397b-122">nx_secure_dtls_server_x509_client_verify_disable</span></span>](#nx_secure_dtls_server_x509_client_verify_disable)
- [<span data-ttu-id="8397b-123">nx_secure_dtls_session_client_info_get</span><span class="sxs-lookup"><span data-stu-id="8397b-123">nx_secure_dtls_session_client_info_get</span></span>](#nx_secure_dtls_session_client_info_get)
- [<span data-ttu-id="8397b-124">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="8397b-124">nx_secure_dtls_session_create</span></span>](#nx_secure_dtls_session_create)
- [<span data-ttu-id="8397b-125">nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="8397b-125">nx_secure_dtls_session_delete</span></span>](#nx_secure_dtls_session_delete)
- [<span data-ttu-id="8397b-126">nx_secure_dtls_session_end</span><span class="sxs-lookup"><span data-stu-id="8397b-126">nx_secure_dtls_session_end</span></span>](#nx_secure_dtls_session_end)
- [<span data-ttu-id="8397b-127">nx_secure_dtls_session_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-127">nx_secure_dtls_session_local_certificate_add</span></span>](#nx_secure_dtls_session_local_certificate_add)
- [<span data-ttu-id="8397b-128">nx_secure_dtls_session_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="8397b-128">nx_secure_dtls_session_local_certificate_remove</span></span>](#nx_secure_dtls_session_local_certificate_remove)
- [<span data-ttu-id="8397b-129">nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="8397b-129">nx_secure_dtls_session_receive</span></span>](#nx_secure_dtls_session_receive)
- [<span data-ttu-id="8397b-130">nx_secure_dtls_session_reset</span><span class="sxs-lookup"><span data-stu-id="8397b-130">nx_secure_dtls_session_reset</span></span>](#nx_secure_dtls_session_reset)
- [<span data-ttu-id="8397b-131">nx_secure_dtls_ session_send</span><span class="sxs-lookup"><span data-stu-id="8397b-131">nx_secure_dtls_ session_send</span></span>](#nx_secure_dtls_-session_send)
- [<span data-ttu-id="8397b-132">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-132">nx_secure_dtls_session_trusted_certificate_add</span></span>](#nx_secure_dtls_session_trusted_certificate_add)
- [<span data-ttu-id="8397b-133">nx_secure_dtls_session_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="8397b-133">nx_secure_dtls_session_trusted_certificate_remove</span></span>](#nx_secure_dtls_session_trusted_certificate_remove)


## <a name="nx_secure_dtls_client_session_start"></a><span data-ttu-id="8397b-134">nx_secure_dtls_client_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-134">nx_secure_dtls_client_session_start</span></span>

<span data-ttu-id="8397b-135">NetX Secure DTLS Client のセッションを開始する</span><span class="sxs-lookup"><span data-stu-id="8397b-135">Start a NetX Secure DTLS Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-136">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-136">Prototype</span></span>

```C
UINT nx_secure_dtls_client_session_start(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        NX_UDP_SOCKET *udp_socket,
                        NXD_ADDRESS *ip_address, UINT port,
                        UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="8397b-137">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-137">Description</span></span>

<span data-ttu-id="8397b-138">このサービスでは、DTLS Client のセッションを開始し、指定された IP アドレスと UDP ポートでサーバーに接続します。ネットワーク通信には、指定された UDP ソケットが使用されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-138">This service starts a DTLS Client session, connecting to the server at the provided IP address and UDP port, using the provided UDP socket for network communications.</span></span>

<span data-ttu-id="8397b-139">このサービスを呼び出す前に、nx_secure_dtls_session_create を使用して DTLS セッションの制御ブロックを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-139">The DTLS session control block must be initialized prior to calling this service using nx_secure_dtls_session_create.</span></span> <span data-ttu-id="8397b-140">さらに、DTLS Client では、nx_secure_dtls_session_trusted_certificate_add を使用して少なくとも 1 つの信頼された CA 証明書がセッションに追加されているか、事前共有キーが有効で構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-140">Additionally, the DTLS Client requires that at least one trusted CA certificate has been added to the session using nx_secure_dtls_session_trusted_certificate_add or Pre-Shared Keys are enabled and configured.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-141">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-141">Parameters</span></span>

- <span data-ttu-id="8397b-142">**dtls_session** 以前に初期化された DTLS Session の構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-142">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="8397b-143">**udp_socket** リモート DTLS サーバーとのネットワーク通信を確立するために使用される、初期化された UDP ソケット。</span><span class="sxs-lookup"><span data-stu-id="8397b-143">**udp_socket** Initialized UDP socket that will be used to establish network communications with the remote DTLS server.</span></span>
- <span data-ttu-id="8397b-144">**ip_address** リモート DTLS サーバーのアドレスを含む IP アドレス構造へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-144">**ip_address** Pointer to IP address structure containing the address of the remote DTLS server.</span></span>
- <span data-ttu-id="8397b-145">**port** リモート DTLS サーバーとのネットワーク通信を確立するために使用される、初期化された UDP ソケット。</span><span class="sxs-lookup"><span data-stu-id="8397b-145">**port** Initialized UDP socket that will be used to establish network communications with the remote DTLS server.</span></span>
- <span data-ttu-id="8397b-146">**wait_option** 接続試行の中断オプション。</span><span class="sxs-lookup"><span data-stu-id="8397b-146">**wait_option** Suspension option for connection attempt.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-147">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-147">Return Values</span></span>

- <span data-ttu-id="8397b-148">**NX_SUCCESS** (0x00) セッションへの証明書の割り当てに成功しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-148">**NX_SUCCESS** (0x00) Successful assignment of certificate to session.</span></span>
- <span data-ttu-id="8397b-149">**NX_NOT_CONNECTED** (0x38) 指定されたアドレスとポートでサーバーに到達できません。</span><span class="sxs-lookup"><span data-stu-id="8397b-149">**NX_NOT_CONNECTED** (0x38) The server cannot be reached at the given address and port.</span></span>
- <span data-ttu-id="8397b-150">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) 受信した TLS/DTLS メッセージの種類が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="8397b-150">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS/DTLS message type is incorrect.</span></span>
- <span data-ttu-id="8397b-151">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) リモート ホストによって提供された暗号はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8397b-151">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="8397b-152">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) TLS ハンドシェイク中のメッセージの処理に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-152">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="8397b-153">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) 受信メッセージのハッシュ MAC チェックに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-153">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a hash MAC check.</span></span>
- <span data-ttu-id="8397b-154">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 基になる TCP ソケットの送信に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-154">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="8397b-155">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) 受信メッセージに無効な長さのフィールドがありました。</span><span class="sxs-lookup"><span data-stu-id="8397b-155">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="8397b-156">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) 受信した ChangeCipherSpec メッセージが正しくありませんでした。</span><span class="sxs-lookup"><span data-stu-id="8397b-156">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="8397b-157">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) 受信した TLS 証明書は、リモート DTLS サーバーの識別に使用できません。</span><span class="sxs-lookup"><span data-stu-id="8397b-157">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) An incoming TLS certificate is unusable for identifying the remote DTLS server.</span></span>
- <span data-ttu-id="8397b-158">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) リモート ホストによって提供された公開キー暗号はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8397b-158">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="8397b-159">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) NetX Secure DTLS スタックによってサポートされている暗号スイートがないことがリモート ホストによって示されています。</span><span class="sxs-lookup"><span data-stu-id="8397b-159">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure DTLS stack.</span></span>
- <span data-ttu-id="8397b-160">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) 受信した DTLS メッセージのヘッダーの DTLS バージョンが不明です。</span><span class="sxs-lookup"><span data-stu-id="8397b-160">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received DTLS message had an unknown DTLS version in its header.</span></span>
- <span data-ttu-id="8397b-161">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) 受信した DTLS メッセージのヘッダーの DTLS バージョンは、既知ですがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8397b-161">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received DTLS message had a known but unsupported DTLS version in its header.</span></span>
- <span data-ttu-id="8397b-162">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) 内部 TLS パケットの割り当てに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-162">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="8397b-163">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) リモート ホストによって無効な証明書が提示されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-163">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="8397b-164">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) リモート ホストによって、エラーを通知して TLS セッションを終了するアラートが送信されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-164">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="8397b-165">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) 暗号スイート テーブル内のエントリに NULL 関数のポインターがありました。</span><span class="sxs-lookup"><span data-stu-id="8397b-165">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) An entry in the ciphersuite table had a NULL function pointer.</span></span>
- <span data-ttu-id="8397b-166">**NX_PTR_ERROR** (0x07) セッション、ソケット、またはアドレス ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8397b-166">**NX_PTR_ERROR** (0x07) Invalid session, socket, or address pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-167">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-167">Allowed From</span></span>

<span data-ttu-id="8397b-168">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-168">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-169">例</span><span class="sxs-lookup"><span data-stu-id="8397b-169">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                           &nx_crypto_tls_ciphers,
                                           crypto_metadata,
                                           sizeof(crypto_metadata),
                                           packet_buffer,
                                           sizeof(packet_buffer),
                                           REMOTE_CERT_NUMBER,
                                           remote_certs_buffer,
                                           sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
       Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                      trusted_cert_der,
                                      trusted_cert_der_len,
                                      NX_NULL, 0, NX_NULL, 0,
                                      NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                   &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                  &udp_socket, &server_ip,
                                                  4443,
                                                  NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
      /* Error! */
      return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="8397b-170">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-170">See Also</span></span>

- <span data-ttu-id="8397b-171">nx_secure_dtls_session_receive、nx_secure_dtls_session_send</span><span class="sxs-lookup"><span data-stu-id="8397b-171">nx_secure_dtls_session_receive, nx_secure_dtls_session_send,</span></span>
- <span data-ttu-id="8397b-172">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="8397b-172">nx_secure_dtls_session_create</span></span>

## <a name="nx_secure_dtls_packet_allocate"></a><span data-ttu-id="8397b-173">nx_secure_dtls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="8397b-173">nx_secure_dtls_packet_allocate</span></span>

<span data-ttu-id="8397b-174">NetX Secure DTLS Session にパケットを割り当てる</span><span class="sxs-lookup"><span data-stu-id="8397b-174">Allocate a packet for a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-175">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-175">Prototype</span></span>

```C
UINT  nx_secure_dtls_packet_allocate(
                              NX_SECURE_DTLS_SESSION *session_ptr,
                         NX_PACKET_POOL *pool_ptr,
                         NX_PACKET **packet_ptr,
                              ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="8397b-176">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-176">Description</span></span>

<span data-ttu-id="8397b-177">このサービスでは、指定された NX_PACKET_POOL から、指定されたアクティブな DTLS セッションに NX_PACKET が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="8397b-177">This service allocates an NX_PACKET for the specified active DTLS session from the specified NX_PACKET_POOL.</span></span> <span data-ttu-id="8397b-178">このサービスは、DTLS 接続を介して送信されるデータ パケットを割り当てる際に、アプリケーションによって呼び出される必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-178">This service should be called by the application to allocate data packets to be sent over a DTLS connection.</span></span> <span data-ttu-id="8397b-179">DTLS セッションは、このサービスが呼び出される前に初期化される必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-179">The DTLS session must be initialized before calling this service.</span></span>

<span data-ttu-id="8397b-180">パケット データが移入された後に DTLS ヘッダーとフッターのデータを追加できるように、割り当てられたパケットは適切に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-180">The allocated packet is properly initialized so that DTLS header and footer data may be added after the packet data is populated.</span></span> <span data-ttu-id="8397b-181">それ以外の動作は、*nx_packet_allocate* と同じです。</span><span class="sxs-lookup"><span data-stu-id="8397b-181">The behavior is otherwise identical to *nx_packet_allocate*.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-182">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-182">Parameters</span></span>

- <span data-ttu-id="8397b-183">**session_ptr** DTLS Session インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-183">**session_ptr** Pointer to a DTLS Session instance.</span></span>
- <span data-ttu-id="8397b-184">**pool_ptr** パケットの割り当て元である NX_PACKET_POOL へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-184">**pool_ptr** Pointer to an NX_PACKET_POOL from which to allocate the packet.</span></span>
- <span data-ttu-id="8397b-185">**packet_ptr** 新しく割り当てられるパケットへの出力ポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-185">**packet_ptr** Output pointer to the newly-allocated packet.</span></span>
- <span data-ttu-id="8397b-186">**wait_option** パケット割り当ての中断オプション。</span><span class="sxs-lookup"><span data-stu-id="8397b-186">**wait_option** Suspension option for packet allocation.</span></span>


### <a name="return-values"></a><span data-ttu-id="8397b-187">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-187">Return Values</span></span>

- <span data-ttu-id="8397b-188">**NX_SUCCESS** (0x00) パケットが正常に割り当てられました。</span><span class="sxs-lookup"><span data-stu-id="8397b-188">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="8397b-189">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) 基になるパケットの割り当てに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-189">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>
- <span data-ttu-id="8397b-190">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) 指定された DTLS セッションは初期化されていませんでした。</span><span class="sxs-lookup"><span data-stu-id="8397b-190">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied DTLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-191">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-191">Allowed From</span></span>

<span data-ttu-id="8397b-192">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-192">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-193">例</span><span class="sxs-lookup"><span data-stu-id="8397b-193">Example</span></span>

```C
/* Allocate a new DTLS packet from the previously created packet pool and
previously initialized DTLS session.   */

status = nx_secure_dtls_packet_allocate(&dtls_session, &pool_0, &packet_ptr,
                                                              NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in
the variable packet_ptr.  */

```

### <a name="see-also"></a><span data-ttu-id="8397b-194">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-194">See Also</span></span>

- <span data-ttu-id="8397b-195">nx_secure_x509_certificate_initialize、nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="8397b-195">nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create,</span></span>
- <span data-ttu-id="8397b-196">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-196">nx_secure_dtls_session_trusted_certificate_add,</span></span>
- <span data-ttu-id="8397b-197">nx_secure_dtls_session_send、nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="8397b-197">nx_secure_dtls_session_send, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="8397b-198">nx_secure_dtls_session_end、nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="8397b-198">nx_secure_dtls_session_end, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_psk_add"></a><span data-ttu-id="8397b-199">nx_secure_dtls_psk_add</span><span class="sxs-lookup"><span data-stu-id="8397b-199">nx_secure_dtls_psk_add</span></span>

<span data-ttu-id="8397b-200">NetX Secure DTLS Session に事前共有キーを追加する</span><span class="sxs-lookup"><span data-stu-id="8397b-200">Add a Pre-Shared Key to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-201">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-201">Prototype</span></span>

```C
UINT  nx_secure_dtls_psk_add(NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a><span data-ttu-id="8397b-202">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-202">Description</span></span>

<span data-ttu-id="8397b-203">このサービスでは、事前共有キー (PSK)、その ID 文字列、ID ヒントが DTLS Session の制御ブロックに追加されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-203">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a DTLS Session control block.</span></span> <span data-ttu-id="8397b-204">PSK 暗号スイートが有効にされて使用されている場合、PSK はデジタル証明書の代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-204">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-205">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-205">Parameters</span></span>

- <span data-ttu-id="8397b-206">**session_ptr** 以前に作成された DTLS Session インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-206">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="8397b-207">**pre_shared_key** 実際の PSK 値。</span><span class="sxs-lookup"><span data-stu-id="8397b-207">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="8397b-208">**psk_length** PSK 値の長さ。</span><span class="sxs-lookup"><span data-stu-id="8397b-208">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="8397b-209">**psk_identity** この PSK 値を識別するために使用される文字列。</span><span class="sxs-lookup"><span data-stu-id="8397b-209">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="8397b-210">**identity_length** PSK の ID の長さ。</span><span class="sxs-lookup"><span data-stu-id="8397b-210">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="8397b-211">**hint** TLS サーバー上のどの PSK グループから選択するかを示すために使用される文字列。</span><span class="sxs-lookup"><span data-stu-id="8397b-211">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="8397b-212">**hint_length** ヒントの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="8397b-212">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-213">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-213">Return Values</span></span>

- <span data-ttu-id="8397b-214">**NX_SUCCESS** (0x00) PSK が正常に追加されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-214">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="8397b-215">**NX_PTR_ERROR** (0x07) DTLS セッションのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8397b-215">**NX_PTR_ERROR** (0x07) Invalid DTLS session pointer.</span></span>
- <span data-ttu-id="8397b-216">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) 別の PSK を追加できません。</span><span class="sxs-lookup"><span data-stu-id="8397b-216">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-217">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-217">Allowed From</span></span>

<span data-ttu-id="8397b-218">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-218">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-219">例</span><span class="sxs-lookup"><span data-stu-id="8397b-219">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_psk_add(&dtls_session, psk,
                            sizeof(psk), “psk_1”, 4,
                            “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */


```

### <a name="see-also"></a><span data-ttu-id="8397b-220">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-220">See Also</span></span>

- <span data-ttu-id="8397b-221">nx_secure_dtls_server_psk_add、nx_secure_dtls_client_session_create</span><span class="sxs-lookup"><span data-stu-id="8397b-221">nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create</span></span>

## <a name="nx_secure_dtls_server_create"></a><span data-ttu-id="8397b-222">nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="8397b-222">nx_secure_dtls_server_create</span></span>

<span data-ttu-id="8397b-223">NetX Secure DTLS サーバーを作成する</span><span class="sxs-lookup"><span data-stu-id="8397b-223">Create a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-224">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-224">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_create(
                NX_SECURE_DTLS_SERVER *server_ptr, NX_IP *ip_ptr,
                UINT port, ULONG timeout, VOID *session_buffer,
                UINT session_buffer_size,
                const NX_SECURE_TLS_CRYPTO *crypto_table,
                VOID *crypto_metadata_buffer, ULONG crypto_metadata_size,
                UCHAR *packet_reassembly_buffer,
                UINT packet_reassembly_buffer_size,
                UINT (*connect_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session,
                              NXD_ADDRESS *ip_address, UINT port),
                UINT (*receive_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session)));

```

### <a name="description"></a><span data-ttu-id="8397b-225">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-225">Description</span></span>

<span data-ttu-id="8397b-226">このサービスでは、特定の UDP ポートで受信された DTLS 要求を処理するために、DTLS サーバーのインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-226">This service creates an instance of a DTLS server to handle incoming DTLS requests on a particular UDP port.</span></span> <span data-ttu-id="8397b-227">UDP はステートレスであるため、他の DTLS セッションがアクティブなときにも、複数のクライアントからの DTLS 要求を 1 つのポートで受信できます。</span><span class="sxs-lookup"><span data-stu-id="8397b-227">Due to the fact that UDP is stateless, DTLS requests from multiple clients can come in on a single port while other DTLS sessions are active.</span></span> <span data-ttu-id="8397b-228">このため、アクティブなセッションを管理し、受信メッセージを適切なハンドラーに適切にルーティングするために、サーバーが必要となります。</span><span class="sxs-lookup"><span data-stu-id="8397b-228">Thus, the server is needed to maintain active sessions and properly route incoming messages to the proper handler.</span></span>

<span data-ttu-id="8397b-229">ip_ptr パラメーターは、DTLS サーバーに関連付けられている内部 UDP ソケットに使用される NX_IP インスタンスを指します (これは NX_SECURE_DTLS_SERVER 制御ブロックに格納されます)。</span><span class="sxs-lookup"><span data-stu-id="8397b-229">The ip_ptr parameter points to an NX_IP instance to be used for the internal UDP socket associated with the DTLS Server (and stored in the NX_SECURE_DTLS_SERVER control block).</span></span> <span data-ttu-id="8397b-230">IP インスタンスとポートは、nx_secure_dtls_server_start サービスを使用してサーバーをインスタンス化する UDP インターフェイスを定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-230">The IP instance and port are used to define the UDP interface upon which the server is instantiated with the nx_secure_dtls_server_start service.</span></span>

<span data-ttu-id="8397b-231">セッション バッファー パラメーターは、DTLS サーバーのすべての可能な同時 DTLS セッションの制御ブロックを保持するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-231">The session buffer parameter is used to hold the control blocks for all the possible simultaneous DTLS sessions for the DTLS server.</span></span> <span data-ttu-id="8397b-232">これは、NX_SECURE_DTLS_SESSION 制御ブロック構造体のサイズの偶数倍のサイズで割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-232">It should be allocated with a size that is an even multiple of the size of the NX_SECURE_DTLS_SESSION control block structure.</span></span>

<span data-ttu-id="8397b-233">必要なメタデータのサイズを計算するには、API nx_secure_tls_metadata_size_calculate を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8397b-233">To calculate the necessary metadata size, the API nx_secure_tls_metadata_size_calculate may be used.</span></span>

<span data-ttu-id="8397b-234">packet_reassembly_buffer パラメーターは、暗号化を解除するために、UDP データグラムを完全な DTLS レコードに再構築するときに DTLS によって使用されます。これは、予想される最大の DTLS レコードを格納するために十分な大きさである必要があります (DTLS のレコードの最大サイズは 16 KB ですが、多くのアプリケーションでは 1 レコードでそれほど大きいデータは送信されません)。</span><span class="sxs-lookup"><span data-stu-id="8397b-234">The packet_reassembly_buffer parameter is used by DTLS to reassemble UDP datagrams into a complete DTLS record for the purposes of decryption and should be large enough to accommodate the largest expected DTLS record (16KB is the DTLS maximum record size but many applications don’t send that much data in a single record).</span></span>

<span data-ttu-id="8397b-235">connect_notify コールバック ルーチンは、新しい DTLS クライアントがサーバーに接続されるたびに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-235">The connect_notify callback routine is invoked whenever a new DTLS client connects to the server.</span></span> <span data-ttu-id="8397b-236">その後、サービス *nx_secure_dtls_server_session_start* を使用して DTLS セッションを開始するのはアプリケーションの責任です。</span><span class="sxs-lookup"><span data-stu-id="8397b-236">It is up to the application to then start the DTLS session using the service *nx_secure_dtls_server_session_start*.</span></span> <span data-ttu-id="8397b-237">このコールバック自体でセッションを開始することができますが、このコールバックはすべての下位レベルのネットワーク処理 (UDP など) を処理するために使用される IP スレッドによって呼び出されるため、接続のアプリケーション スレッド (またはアプリケーションによって作成される専用の DTLS スレッド) を通知するためにのみこのコールバックを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8397b-237">While the session may be started in the callback itself, it is recommended that the callback only be used to notify the application thread (or dedicated DTLS thread created by the application) of the connection as the callback is invoked by the IP thread which is used to process all lower-level network processing (e.g. UDP).</span></span> <span data-ttu-id="8397b-238">これは、DTLS セッション パラメーターを保存し (コールバックにパラメーターとして指定します)、もう一方のスレッドで nx_secure_dtls_server_session_start を呼び出すことによって簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="8397b-238">This can be as simple as saving the DTLS session parameter (provided as a parameter to the callback) and invoking nx_secure_dtls_server_session_start in the other thread.</span></span> <span data-ttu-id="8397b-239">通常、connect_notify コールバックでは NX_SUCCESS が返されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-239">The connect_notify callback should generally return NX_SUCCESS.</span></span>

<span data-ttu-id="8397b-240">receive_notify コールバック ルーチンは、確立された既存の DTLS セッションと一致する DTLS レコードが受信されるたびに呼び出されます (既存のセッションを識別するために、リモート ホストの IP アドレスとポートが使用されます)。</span><span class="sxs-lookup"><span data-stu-id="8397b-240">The receive_notify callback routine is invoked whenever a DTLS record is received that matches an existing established DTLS session (the remote host IP address and port are used to identify an existing session).</span></span> <span data-ttu-id="8397b-241">これは、DTLS で暗号化されて送信される "アプリケーション データ" を表します。</span><span class="sxs-lookup"><span data-stu-id="8397b-241">This represents the “application data” that is encrypted and sent over DTLS.</span></span> <span data-ttu-id="8397b-242">アプリケーションで、受信したデータを取得するには、指定された DTLS セッションでサービス *nx_secure_dtls_session_receive* を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-242">The application must call the service *nx_secure_dtls_session_receive* on the provided DTLS session to retrieve the received data.</span></span> <span data-ttu-id="8397b-243">connect_receive コールバックと同様に、セッションを別のスレッドに渡してメッセージ処理を行うことをお勧めします。これは、コールバックがその IP スレッドから呼び出されるためです。</span><span class="sxs-lookup"><span data-stu-id="8397b-243">As with the connect_receive callback, it is recommended that the session be passed to another thread to handle the message processing as the callback is invoked from the IP thread.</span></span> <span data-ttu-id="8397b-244">通常、receive_notify コールバックでは NX_SUCCESS が返されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-244">The receive_notify callback should generally return NX_SUCCESS.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-245">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-245">Parameters</span></span>

- <span data-ttu-id="8397b-246">**server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-246">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="8397b-247">**ip_ptr** DTLS サーバーのネットワーク インターフェイスとして使用する、初期化された NX_IP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-247">**ip_ptr** Pointer to an initialized NX_IP control block to use as the network interface for the DTLS server.</span></span>
- <span data-ttu-id="8397b-248">**port** DTLS サーバーの UDP ソケットがバインドされているローカル UDP ポート。</span><span class="sxs-lookup"><span data-stu-id="8397b-248">**port** The local UDP port to which the DTLS server UDP socket is bound.</span></span>
- <span data-ttu-id="8397b-249">**timeout** ネットワーク操作に使用されるタイムアウト値。</span><span class="sxs-lookup"><span data-stu-id="8397b-249">**timeout** Timeout value to use for network operations.</span></span>
- <span data-ttu-id="8397b-250">**session_buffer** この DTLS Server インスタンスに割り当てられている NX_SECURE_DTLS_SESSION のすべてのインスタンスの制御ブロックを保持するためのバッファー領域。</span><span class="sxs-lookup"><span data-stu-id="8397b-250">**session_buffer** Buffer space to contain control blocks for all instances of NX_SECURE_DTLS_SESSION assigned to this DTLS Server instance.</span></span>
- <span data-ttu-id="8397b-251">**session_buffer_size** セッション バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="8397b-251">**session_buffer_size** Size of the session buffer.</span></span> <span data-ttu-id="8397b-252">これにより、DTLS Server に割り当てられる DTLS セッションの数が決まります。</span><span class="sxs-lookup"><span data-stu-id="8397b-252">This determines the number of DTLS sessions assigned to the DTLS Server.</span></span>
- <span data-ttu-id="8397b-253">**crypto_table** すべての暗号化操作に使用される TLS/DTLS 暗号化テーブル構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-253">**crypto_table** Pointer to a TLS/DTLS encryption table structure used for all cryptographic operations.</span></span>
- <span data-ttu-id="8397b-254">**crypto_metadata_buffer** 暗号化操作の計算と状態の情報を保持するためのバッファー領域。</span><span class="sxs-lookup"><span data-stu-id="8397b-254">**crypto_metadata_buffer** Buffer space for cryptographic operation calculations and state information.</span></span>
- <span data-ttu-id="8397b-255">**crypto_metadata_size** メタデータ バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="8397b-255">**crypto_metadata_size** Size of metadata buffer.</span></span>
- <span data-ttu-id="8397b-256">**packet_reassembly_buffer** 暗号化の解除で UDP データを DTLS レコードに再構築するために DTLS によって使用されるバッファー。</span><span class="sxs-lookup"><span data-stu-id="8397b-256">**packet_reassembly_buffer** Buffer used by DTLS to reassemble UDP data into DTLS records for decryption.</span></span>
- <span data-ttu-id="8397b-257">**packet_reassembly_buffer_size** 再構築バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="8397b-257">**packet_reassembly_buffer_size** Size of reassembly buffer.</span></span> <span data-ttu-id="8397b-258">通常は 16 KB を超えるサイズにする必要がありますが、アプリケーションによっては小さくすることができます。</span><span class="sxs-lookup"><span data-stu-id="8397b-258">Generally should be greater than 16KB but may be smaller depending on application.</span></span>
- <span data-ttu-id="8397b-259">**connect_notify** リモート DTLS Client でこの DTLS サーバーに接続しようとするたびに呼び出されるコールバック ルーチン。</span><span class="sxs-lookup"><span data-stu-id="8397b-259">**connect_notify** Callback routine invoked whenever a remote DTLS Client attempts to connect to this DTLS server.</span></span>
- <span data-ttu-id="8397b-260">**receive_notify** 既存の DTLS セッションを介してアプリケーション データが受信されるたびに呼び出されるコールバック。</span><span class="sxs-lookup"><span data-stu-id="8397b-260">**receive_notify** Callback invoked whenever application data is received over an existing DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-261">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-261">Return Values</span></span>

- <span data-ttu-id="8397b-262">**NX_SUCCESS** (0x00) DTLS サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-262">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="8397b-263">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-263">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="8397b-264">**NX_INVALID_PARAMETERS** (0x4D) セッション、パケットの再構築、または暗号化のための十分なバッファー領域がありません。</span><span class="sxs-lookup"><span data-stu-id="8397b-264">**NX_INVALID_PARAMETERS** (0x4D) Not enough buffer space for sessions, packet reassembly, or cryptography.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-265">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-265">Allowed From</span></span>

<span data-ttu-id="8397b-266">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-266">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-267">例</span><span class="sxs-lookup"><span data-stu-id="8397b-267">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
    *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE, dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                        device_cert_der_len, NX_NULL, 0,
                        device_cert_key_der, device_cert_key_der_len,
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                           NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                                                   &send_packet, NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data,
        let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done, stop the server
    instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="8397b-268">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-268">See Also</span></span>

- <span data-ttu-id="8397b-269">nx_secure_dtls_server_start、nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="8397b-269">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="8397b-270">nx_secure_dtls_session_receive、nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="8397b-270">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="8397b-271">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-271">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="8397b-272">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="8397b-272">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="8397b-273">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-273">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_delete"></a><span data-ttu-id="8397b-274">nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="8397b-274">nx_secure_dtls_server_delete</span></span>

<span data-ttu-id="8397b-275">NetX Secure DTLS Server によって使用されるリソースを解放する</span><span class="sxs-lookup"><span data-stu-id="8397b-275">Free up resources used by a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-276">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-276">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_delete(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="8397b-277">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-277">Description</span></span>

<span data-ttu-id="8397b-278">このサービスでは、サーバーによって使用される内部 UDP ソケットを含む、DTLS サーバー インスタンスに割り当てられているリソースが解放されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-278">This service frees up the resources allocated to a DTLS Server instance, including the internal UDP socket used by the server.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-279">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-279">Parameters</span></span>

- <span data-ttu-id="8397b-280">**server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-280">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-281">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-281">Return Values</span></span>

- <span data-ttu-id="8397b-282">**NX_SUCCESS** (0x00) サーバーが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-282">**NX_SUCCESS** (0x00) Successful deletion of server.</span></span>
- <span data-ttu-id="8397b-283">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-283">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="8397b-284">**NX_STILL_BOUND** (0x42) UDP ソケットがまだバインドされています。</span><span class="sxs-lookup"><span data-stu-id="8397b-284">**NX_STILL_BOUND** (0x42) UDP socket is still bound.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-285">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-285">Allowed From</span></span>

<span data-ttu-id="8397b-286">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-286">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-287">例</span><span class="sxs-lookup"><span data-stu-id="8397b-287">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
*ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer, sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);


    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                         NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                        &packet_pool,
                                                        &send_packet,
                                                        NX_IP_PERIODIC_RATE);

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="8397b-288">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-288">See Also</span></span>

- <span data-ttu-id="8397b-289">nx_secure_dtls_server_start、nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="8397b-289">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="8397b-290">nx_secure_dtls_session_receive、nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="8397b-290">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="8397b-291">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-291">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_local_certificate_add"></a><span data-ttu-id="8397b-292">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-292">nx_secure_dtls_server_local_certificate_add</span></span>

<span data-ttu-id="8397b-293">NetX Secure DTLS Server にローカル サーバーの ID 証明書を追加する</span><span class="sxs-lookup"><span data-stu-id="8397b-293">Add a local server identity certificate to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-294">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-294">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_local_certificate_add(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                 NX_SECURE_X509_CERT *certificate,
                                 UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="8397b-295">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-295">Description</span></span>

<span data-ttu-id="8397b-296">このサービスでは、ローカル サーバーの ID 証明書が DTLS Server インスタンスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-296">This service adds a local server identity certificate to a DTLS Server instance.</span></span> <span data-ttu-id="8397b-297">代替の認証メカニズム (事前共有キーなど) を使用する場合を除き、クライアントで DTLS サーバーに接続するには、少なくとも 1 つの ID 証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="8397b-297">At least one identity certificate is required for clients to connect to a DTLS server unless an alternate authentication mechanism (e.g. Pre-Shared Keys) is used.</span></span>

<span data-ttu-id="8397b-298">cert_id パラメーターは、証明書の 0 以外の数値の識別子です。</span><span class="sxs-lookup"><span data-stu-id="8397b-298">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="8397b-299">これにより、DTLS サーバー ストアに同じ X.509 の共通名を持つ複数の ID 証明書がある場合に、証明書を簡単に削除したり、見つけたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="8397b-299">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS server store.</span></span> <span data-ttu-id="8397b-300">X.509 サーバー証明書の詳細については、『NetX Secure TLS ユーザー ガイド』を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8397b-300">See the NetX Secure TLS User Guide for more information about X.509 server certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-301">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-301">Parameters</span></span>

- <span data-ttu-id="8397b-302">**server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-302">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="8397b-303">**certificate** 以前に初期化された X.509 証明書構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-303">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="8397b-304">**cert_id** この DTLS サーバー内のこの証明書に対する 0 以外の数値の一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="8397b-304">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-305">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-305">Return Values</span></span>

- <span data-ttu-id="8397b-306">**NX_SUCCESS** (0x00) DTLS サーバーに証明書が正常に追加されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-306">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS server.</span></span>
- <span data-ttu-id="8397b-307">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-307">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="8397b-308">**NX_INVALID_PARAMETERS** (0x4D) 証明書 ID として 0 が渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-308">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-309">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-309">Allowed From</span></span>

<span data-ttu-id="8397b-310">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-311">例</span><span class="sxs-lookup"><span data-stu-id="8397b-311">Example</span></span>

<span data-ttu-id="8397b-312">*より完全な例については、*nx_secure_dtls_server_create\* のリファレンスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8397b-312">\*See reference for *nx_secure_dtls_server_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                            certificate_der_data,
                            sizeof(certificate_der_data),
                            NX_NULL, 0,
                            certificate_key_der_data,
                            sizeof(certificate_key_der_data),
                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a><span data-ttu-id="8397b-313">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-313">See Also</span></span>

- <span data-ttu-id="8397b-314">nx_secure_dtls_server_start、nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="8397b-314">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="8397b-315">nx_secure_dtls_session_receive、nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="8397b-315">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="8397b-316">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-316">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="8397b-317">nx_secure_dtls_server_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="8397b-317">nx_secure_dtls_server_local_certificate_remove,</span></span>
- <span data-ttu-id="8397b-318">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="8397b-318">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_local_certificate_remove"></a><span data-ttu-id="8397b-319">nx_secure_dtls_server_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="8397b-319">nx_secure_dtls_server_local_certificate_remove</span></span>

<span data-ttu-id="8397b-320">NetX Secure DTLS Server からローカル サーバーの ID 証明書を削除する</span><span class="sxs-lookup"><span data-stu-id="8397b-320">Remove a local server identity certificate from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-321">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-321">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_local_certificate_remove(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                   UCHAR *common_name,
                                   UINT common_name_length,
                                   UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="8397b-322">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-322">Description</span></span>

<span data-ttu-id="8397b-323">このサービスでは、DTLS Server インスタンスからローカル サーバーの ID 証明書が削除されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-323">This service removes a local server identity certificate from a DTLS Server instance.</span></span> <span data-ttu-id="8397b-324">代替の認証メカニズム (事前共有キーなど) を使用する場合を除き、クライアントで DTLS サーバーに接続するには、少なくとも 1 つの ID 証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="8397b-324">At least one identity certificate is required for clients to connect to a DTLS server unless an alternate authentication mechanism (e.g. Pre-Shared Keys) is used.</span></span>

<span data-ttu-id="8397b-325">削除する証明書は、X.509 の共通名、または *nx_secure_dtls_server_local_certificate_add* への呼び出しで割り当てられた数値である cert_id によって識別できます。</span><span class="sxs-lookup"><span data-stu-id="8397b-325">The certificate to be removed can be identified either by its X.509 Common Name or by the numeric cert_id that was assigned in the call to *nx_secure_dtls_server_local_certificate_add*.</span></span> <span data-ttu-id="8397b-326">cert_id は証明書の識別にのみ使用され、アプリケーションによって管理されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-326">The cert_id is only used to identify the certificate and is maintained by the application.</span></span> <span data-ttu-id="8397b-327">数値の証明書 ID の代わりに共通名を使用する場合は、cert_id パラメーターを 0 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-327">If the Common Name is used instead of the numeric certificate identifier, the cert_id parameter should be set to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="8397b-328">DTLS ハンドシェイクの処理中に証明書を削除すると、予期しない動作が発生します。</span><span class="sxs-lookup"><span data-stu-id="8397b-328">Removing a certificate while a DTLS handshake is being processed will result in unexpected behavior.</span></span> <span data-ttu-id="8397b-329">証明書を削除する前に、サービス *nx_secure_dtls_server_stop* を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-329">The service *nx_secure_dtls_server_stop* should be called before removing certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-330">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-330">Parameters</span></span>

- <span data-ttu-id="8397b-331">**server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-331">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="8397b-332">**common_name** 削除する証明書の X.509 CommonName。</span><span class="sxs-lookup"><span data-stu-id="8397b-332">**common_name** X.509 CommonName of the certificate to remove.</span></span> <span data-ttu-id="8397b-333">これを使用する場合は、cert_id を 0 として渡します。</span><span class="sxs-lookup"><span data-stu-id="8397b-333">If this is used, pass cert_id as zero.</span></span>
- <span data-ttu-id="8397b-334">**common_name_length** common_name 文字列の長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="8397b-334">**common_name_length** Length of common_name string in bytes.</span></span>
- <span data-ttu-id="8397b-335">**cert_id** この DTLS サーバー内のこの証明書に対する 0 以外の数値の一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="8397b-335">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span> <span data-ttu-id="8397b-336">これを使用する場合は、common_name パラメーターに NX_NULL を渡します。</span><span class="sxs-lookup"><span data-stu-id="8397b-336">If this is used, pass NX_NULL for the common_name parameter.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-337">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-337">Return Values</span></span>

- <span data-ttu-id="8397b-338">**NX_SUCCESS** (0x00) DTLS サーバーから証明書が正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-338">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS server.</span></span>
- <span data-ttu-id="8397b-339">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-339">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="8397b-340">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) 指定された DTLS サーバーで cert_id または common_name に一致する証明書が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="8397b-340">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS server.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-341">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-341">Allowed From</span></span>

<span data-ttu-id="8397b-342">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-342">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-343">例</span><span class="sxs-lookup"><span data-stu-id="8397b-343">Example</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        certificate_der_data,
                                        sizeof(certificate_der_data),
                                        NX_NULL, 0, certificate_key_der_data,
                                        sizeof(certificate_key_der_data),
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                     &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);

    /* At some point in the future we decide to remove the certificate we added.
    We can use the certificate identifier we passed into the call to
    nx_secure_dtls_local_certificate_add (value = 1); */
    status = nx_secure_dtls_server_local_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a><span data-ttu-id="8397b-344">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-344">See Also</span></span>

- <span data-ttu-id="8397b-345">nx_secure_dtls_server_start、nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="8397b-345">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="8397b-346">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-346">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="8397b-347">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="8397b-347">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="8397b-348">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-348">nx_secure_dtls_server_local_certificate_add,</span></span>
- <span data-ttu-id="8397b-349">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="8397b-349">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_notify_set"></a><span data-ttu-id="8397b-350">nx_secure_dtls_server_notify_set</span><span class="sxs-lookup"><span data-stu-id="8397b-350">nx_secure_dtls_server_notify_set</span></span>

<span data-ttu-id="8397b-351">NetX Secure DTLS Server にオプションの通知コールバック ルーチンを割り当てる</span><span class="sxs-lookup"><span data-stu-id="8397b-351">Assign optional notification callback routines to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-352">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-352">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_notify_set(
                         NX_SECURE_DTLS_SERVER *server_ptr,
                         UINT (*disconnect_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session),
                         UINT (*error_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session,
                                      UINT error_code));

```

### <a name="description"></a><span data-ttu-id="8397b-353">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-353">Description</span></span>

<span data-ttu-id="8397b-354">このサービスを使用すると、DTLS サーバーにオプションの通知コールバック ルーチンを追加できます。</span><span class="sxs-lookup"><span data-stu-id="8397b-354">This service can be used to add optional notification callback routines to a DTLS server.</span></span> <span data-ttu-id="8397b-355">コールバックが 1 つだけ必要な場合は、いずれかのコールバック パラメーターを NX_NULL として渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="8397b-355">Either callback parameter may be passed as NX_NULL if only one callback is desired.</span></span>

<span data-ttu-id="8397b-356">リモート クライアントで DTLS セッションを終了するときには、disconnect_notify コールバックが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-356">The disconnect_notify callback is invoked when a remote client ends a DTLS session.</span></span> <span data-ttu-id="8397b-357">dtls_session パラメーターは、閉じられたセッション インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="8397b-357">The dtls_session parameter is the session instance that was closed.</span></span> <span data-ttu-id="8397b-358">通常、このコールバックでは NX_SUCCESS が返されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-358">The callback should generally return NX_SUCCESS.</span></span>

<span data-ttu-id="8397b-359">error_notify コールバックは、DTLS エラーまたはタイムアウトが発生するたびに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-359">The error_notify callback is invoked whenever a DTLS error or timeout occurs.</span></span> <span data-ttu-id="8397b-360">dtls_session パラメーターは、エラーが発生したセッション インスタンスです。error_code は、問題の原因となったエラーの数値の状態コードです（</span><span class="sxs-lookup"><span data-stu-id="8397b-360">The dtls_session parameter is the session instance for which the error occurred, and error_code is the numeric status code for the error that caused the issue (see Appendix A)</span></span>

<span data-ttu-id="8397b-361">返される可能性があるエラー コードの一覧については、付録 A NetX Secure のリターン/エラー コードに関するページを参照してください）。</span><span class="sxs-lookup"><span data-stu-id="8397b-361">NetX Secure Return/Error Codes for a list of error codes that may be returned).</span></span> <span data-ttu-id="8397b-362">通常、このコールバックでは NX_SUCCESS が返されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-362">The callback should generally return NX_SUCCESS.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-363">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-363">Parameters</span></span>

- <span data-ttu-id="8397b-364">**server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-364">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="8397b-365">**disconnect_notify** リモート クライアントのホストで DTLS セッションが閉じられるたびに呼び出されるコールバック ルーチン。</span><span class="sxs-lookup"><span data-stu-id="8397b-365">**disconnect_notify** Callback routine invoked whenever a remote client host closes a DTLS session.</span></span>
- <span data-ttu-id="8397b-366">**error_notify** DTLS でエラーまたはタイムアウトが発生するたびに呼び出されるコールバック ルーチン。</span><span class="sxs-lookup"><span data-stu-id="8397b-366">**error_notify** Callback routine invoked whenever DTLS encounters an error or timeout.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-367">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-367">Return Values</span></span>

- <span data-ttu-id="8397b-368">**NX_SUCCESS** (0x00) コールバック ルーチンが正常に割り当てられました。</span><span class="sxs-lookup"><span data-stu-id="8397b-368">**NX_SUCCESS** (0x00) Successful assignment of callback routines.</span></span>
- <span data-ttu-id="8397b-369">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-369">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-370">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-370">Allowed From</span></span>

<span data-ttu-id="8397b-371">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-371">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-372">例</span><span class="sxs-lookup"><span data-stu-id="8397b-372">Example</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

UINT disconnect_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
NXD_ADDRESS client_ip_addr;
UINT client_port;
UINT local_port;

    /* We have received a disconnection notice (CloseNotify message) from a
       remote client. Application can use the dtls_session parameter for any
       desired processing. */

    /* See what client disconnected by extracting its IP address and port.
       NOTE: depending on how the session ended, the client information may
             no longer be available. */
    status  = nx_secure_dtls_session_client_info_get(dtls_session,
                                                    &ip_addr,
                                                    &client_port,
                                                    &local_port);

    return(NX_SUCCESS);
}

UINT error_notify(NX_SECURE_DTLS_SESSION *dtls_session, UINT error_code)
{
    /* The DTLS server has encountered an error or timeout condition. We
    can use the error_code parameter to determine the error and we
    can insect the dtls_session for more information. */

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Other setup (e.g. certificates) goes here … */

    status = nx_secure_dtls_server_notify_set(&dtls_server, disconnect_notify,
                                                                 error_notify);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

}

```

### <a name="see-also"></a><span data-ttu-id="8397b-373">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-373">See Also</span></span>

- <span data-ttu-id="8397b-374">nx_secure_dtls_server_start、nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="8397b-374">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="8397b-375">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-375">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="8397b-376">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="8397b-376">nx_secure_dtls_server_session_stop</span></span>

## <a name="nx_secure_dtls_server_psk_add"></a><span data-ttu-id="8397b-377">nx_secure_dtls_server_psk_add</span><span class="sxs-lookup"><span data-stu-id="8397b-377">nx_secure_dtls_server_psk_add</span></span>

<span data-ttu-id="8397b-378">NetX Secure DTLS Server に事前共有キーを追加する</span><span class="sxs-lookup"><span data-stu-id="8397b-378">Add a Pre-Shared Key to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-379">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-379">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_psk_add(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *pre_shared_key, UINT psk_length,
                                UCHAR *psk_identity,
                                UINT identity_length, UCHAR *hint,
                                UINT hint_length);

```

### <a name="description"></a><span data-ttu-id="8397b-380">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-380">Description</span></span>

<span data-ttu-id="8397b-381">このサービスでは、事前共有キー (PSK)、その ID 文字列、ID ヒントが DTLS サーバーの制御ブロックに追加されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-381">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a DTLS Server control block.</span></span> <span data-ttu-id="8397b-382">PSK 暗号スイートが有効にされて使用されている場合、PSK はデジタル証明書の代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-382">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

<span data-ttu-id="8397b-383">追加された PSK は、(nx_secure_dtls_server_create の呼び出しで指定されたセッション バッファーを介して) DTLS Server に割り当てられているすべての DTLS セッションにレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="8397b-383">The PSK that is added is replicated across all the DTLS sessions assigned to the DTLS Server (via the session buffer given in the call to nx_secure_dtls_server_create).</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-384">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-384">Parameters</span></span>

- <span data-ttu-id="8397b-385">**server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-385">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="8397b-386">**pre_shared_key** 実際の PSK 値。</span><span class="sxs-lookup"><span data-stu-id="8397b-386">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="8397b-387">**psk_length** PSK 値の長さ。</span><span class="sxs-lookup"><span data-stu-id="8397b-387">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="8397b-388">**psk_identity** この PSK 値を識別するために使用される文字列。</span><span class="sxs-lookup"><span data-stu-id="8397b-388">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="8397b-389">**identity_length** PSK の ID の長さ。</span><span class="sxs-lookup"><span data-stu-id="8397b-389">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="8397b-390">**hint** TLS サーバー上のどの PSK グループから選択するかを示すために使用される文字列。</span><span class="sxs-lookup"><span data-stu-id="8397b-390">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="8397b-391">**hint_length** ヒントの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="8397b-391">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-392">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-392">Return Values</span></span>

- <span data-ttu-id="8397b-393">**NX_SUCCESS** (0x00) PSK が正常に追加されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-393">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="8397b-394">**NX_PTR_ERROR** (0x07) DTLS サーバーへのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8397b-394">**NX_PTR_ERROR** (0x07) Invalid DTLS server pointer.</span></span>
- <span data-ttu-id="8397b-395">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) 別の PSK を追加できません。</span><span class="sxs-lookup"><span data-stu-id="8397b-395">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-396">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-396">Allowed From</span></span>

<span data-ttu-id="8397b-397">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-398">例</span><span class="sxs-lookup"><span data-stu-id="8397b-398">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_server_psk_add(&dtls_server, psk, sizeof(psk), “psk_1”,
   4, “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */

```

### <a name="see-also"></a><span data-ttu-id="8397b-399">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-399">See Also</span></span>

- <span data-ttu-id="8397b-400">nx_secure_dtls_psk_add、nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="8397b-400">nx_secure_dtls_psk_add, nx_secure_dtls_server_create</span></span>

## <a name="nx_secure_dtls_server_session_send"></a><span data-ttu-id="8397b-401">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="8397b-401">nx_secure_dtls_server_session_send</span></span>

<span data-ttu-id="8397b-402">NetX Secure DTLS Server と確立された DTLS セッション経由でデータを送信する</span><span class="sxs-lookup"><span data-stu-id="8397b-402">Send data over a DTLS session established with a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-403">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-403">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_session_send(
                                NX_SECURE_DTLS_SESSION *session_ptr,
                               NX_PACKET *packet_ptr);

```

### <a name="description"></a><span data-ttu-id="8397b-404">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-404">Description</span></span>

<span data-ttu-id="8397b-405">このサービスでは、確立された DTLS Server セッションを介して、リモートの DTLS Client のホストにデータのパケットが送信されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-405">This service sends a packet of data over an established DTLS Server session to a remote DTLS Client host.</span></span> <span data-ttu-id="8397b-406">使用されるセッションは、nx_secure_dtls_session_create に指定された receive_notify コールバック ルーチンで取得されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-406">The session used is obtained in the receive_notify callback routine provided to nx_secure_dtls_session_create.</span></span>

<span data-ttu-id="8397b-407">パケットで提供されるデータは、*nx_secure_dtls_packet_allocate* を使用して割り当てる必要があります。このデータは、DTLS Session の暗号化パラメーターとルーチンを使用して暗号化され、DTLS Server の内部 UDP ポートを介してリモート ホスト (接続されているクライアントの IP アドレスとポート (DTLS Session に格納されています)) に送信されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-407">The data provided in the packet, which must be allocated using *nx_secure_dtls_packet_allocate*, is encrypted using the DTLS session cryptographic parameters and routines and then sent to the remote host over the DTLS Server internal UDP port to the attached client’s IP address and port (stored in the DTLS Session).</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-408">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-408">Parameters</span></span>

- <span data-ttu-id="8397b-409">**session_ptr** アプリケーションによって提供される receive_notify コールバック ルーチンから取得された、DTLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-409">**session_ptr** Pointer to a DTLS session instance obtained from the receive_notify callback routine provided by the application.</span></span>
- <span data-ttu-id="8397b-410">**packet_ptr** 以前に割り当てられ、アプリケーション データが移入された NX_PACKET インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-410">**packet_ptr** Pointer to an NX_PACKET instance allocated previously and populated with application data.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-411">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-411">Return Values</span></span>

- <span data-ttu-id="8397b-412">**NX_SUCCESS** (0x00) DTLS サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-412">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="8397b-413">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-413">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="8397b-414">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 基になる UDP の送信操作でエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-414">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An error occurred in the underlying UDP send operation.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-415">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-415">Allowed From</span></span>

<span data-ttu-id="8397b-416">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-416">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-417">例</span><span class="sxs-lookup"><span data-stu-id="8397b-417">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;


/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key
    and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        device_cert_der,
                                        device_cert_der_len,
                                        NX_NULL,
                                        0, device_cert_key_der,
                                        device_cert_key_der_len,
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

}

/* If not processing connections or received data, let the thread sleep. */
if(!connect_flag && !receive_flag)
{
    tx_thread_sleep(100);
}
    }

    /* Server processing is done, stop the server instance
    from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="8397b-418">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-418">See Also</span></span>

- <span data-ttu-id="8397b-419">nx_secure_dtls_server_start、nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="8397b-419">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="8397b-420">nx_secure_dtls_session_receive、nx_secure_dtls_server_session_create</span><span class="sxs-lookup"><span data-stu-id="8397b-420">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create,</span></span>
- <span data-ttu-id="8397b-421">nx_secure_dtls_server_session_start、nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="8397b-421">nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="8397b-422">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-422">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_session_start"></a><span data-ttu-id="8397b-423">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-423">nx_secure_dtls_server_session_start</span></span>

<span data-ttu-id="8397b-424">NetX Secure DTLS Server から DTLS Session を開始する</span><span class="sxs-lookup"><span data-stu-id="8397b-424">Start a DTLS Session from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-425">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-425">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_session_start(
                 NX_SECURE_DTLS_SESSION *session_ptr, UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="8397b-426">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-426">Description</span></span>

<span data-ttu-id="8397b-427">このサービスでは、リモートの DTLS Client がサーバーに接続して DTLS 接続を要求したときに、サーバー側の DTLS ハンドシェイクが実行され、DTLS Server セッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-427">This service starts a DTLS Server session by performing the server-side DTLS handshake when a remote DTLS Client has connected to the server and requested a DTLS connection.</span></span>

<span data-ttu-id="8397b-428">DTLS Session は、nx_secure_dtls_server_create に指定された connect_notify コールバック ルーチンで取得されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-428">The DTLS Session is obtained in the connect_notify callback routine provided to nx_secure_dtls_server_create.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-429">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-429">Parameters</span></span>

- <span data-ttu-id="8397b-430">**session_ptr** DTLS Server の connect_notify コールバックから取得された DTLS Session インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-430">**session_ptr** Pointer to a DTLS Session instance obtained from a DTLS Server connect_notify callback.</span></span>
- <span data-ttu-id="8397b-431">**wait_option** ネットワーク操作に使用される ThreadX の待機値。</span><span class="sxs-lookup"><span data-stu-id="8397b-431">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-432">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-432">Return Values</span></span>

- <span data-ttu-id="8397b-433">**NX_SUCCESS** (0x00) DTLS サーバーが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-433">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="8397b-434">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-434">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="8397b-435">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) DTLS ハンドシェイクのパケットを割り当てることができませんでした (パケット プールが空です)。</span><span class="sxs-lookup"><span data-stu-id="8397b-435">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate a DTLS handshake packet (packet pool empty).</span></span>
- <span data-ttu-id="8397b-436">**NX_SECURE_TLS_INVALID_PACKET** (0x104) 有効な DTLS レコードではないデータを受信しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-436">**NX_SECURE_TLS_INVALID_PACKET** (0x104) Recevied data that was not a valid DTLS record.</span></span>
- <span data-ttu-id="8397b-437">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) DTLS レコードを正しくハッシュ化できませんでした (暗号化エラー)。</span><span class="sxs-lookup"><span data-stu-id="8397b-437">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A DTLS record failed to be properly hashed (encryption error).</span></span>
- <span data-ttu-id="8397b-438">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) 暗号化のパディング チェックに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-438">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Encryption padding check failure.</span></span>
- <span data-ttu-id="8397b-439">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) DTLS ハンドシェイク中にリモート ホストからアラートを受信しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-439">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied an alert from the remote host during the DTLS handshake.</span></span>
- <span data-ttu-id="8397b-440">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) DTLS ハンドシェイク中に認識されないメッセージを受信しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-440">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Received an unrecognized message during the DTLS handshake.</span></span>
- <span data-ttu-id="8397b-441">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) 長さが無効な DTLS レコードを受信しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-441">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied a DTLS record with an invalid length.</span></span>
- <span data-ttu-id="8397b-442">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) サポートされていない DTLS 暗号スイートの ClientHello を受信しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-442">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Received a ClientHello with no supported DTLS ciphersuites.</span></span>
- <span data-ttu-id="8397b-443">**NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0x118) 不明な圧縮方法の ClientHello を受信しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-443">**NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0x118) Recevied a ClientHello with a unknown compression method.</span></span>
- <span data-ttu-id="8397b-444">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) 全般的な (詳細不明の) ハンドシェイク エラー。通常は拡張処理の問題が原因です。</span><span class="sxs-lookup"><span data-stu-id="8397b-444">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Generic (unspecified) handshake failure, usually due to problems with extension processing.</span></span>
- <span data-ttu-id="8397b-445">**NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130) DTLS ハンドシェイク中に、まだサポートされていない機能が呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-445">**NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130) A feature that is not yet supported was invoked during the DTLS handshake.</span></span>
- <span data-ttu-id="8397b-446">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) 不明な暗号スイートが見つかりました (内部暗号化エラーを示しています)。</span><span class="sxs-lookup"><span data-stu-id="8397b-446">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) An unknown ciphersuite was encountered (indicated internal cryptography error).</span></span>
- <span data-ttu-id="8397b-447">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) DTLS バージョンが一致しない DTLS レコードを受信しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-447">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied a DTLS record with a mismatched DTLS version.</span></span>
- <span data-ttu-id="8397b-448">**NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0x115) DTLS ハンドシェイクのハッシュの検証に失敗しました。セッションは無効です。</span><span class="sxs-lookup"><span data-stu-id="8397b-448">**NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0x115) Failed to validate the DTLS handshake hash, session is invalid.</span></span>
- <span data-ttu-id="8397b-449">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 内部の UDP 送信に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-449">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Internal UDP send failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-450">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-450">Allowed From</span></span>

<span data-ttu-id="8397b-451">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-452">例</span><span class="sxs-lookup"><span data-stu-id="8397b-452">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
* DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len, NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                    &packet_pool, &send_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done,
    stop the server instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="8397b-453">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-453">See Also</span></span>

- <span data-ttu-id="8397b-454">nx_secure_dtls_server_start、nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="8397b-454">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="8397b-455">nx_secure_dtls_session_receive、nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="8397b-455">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="8397b-456">nx_secure_dtls_server_session_create、nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="8397b-456">nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="8397b-457">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-457">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_start"></a><span data-ttu-id="8397b-458">nx_secure_dtls_server_start</span><span class="sxs-lookup"><span data-stu-id="8397b-458">nx_secure_dtls_server_start</span></span>

<span data-ttu-id="8397b-459">構成された UDP ポートでリッスンする NetX Secure DTLS Server インスタンスを開始する</span><span class="sxs-lookup"><span data-stu-id="8397b-459">Start a NetX Secure DTLS Server instance listening on the configured UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-460">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-460">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_start(
                  NX_SECURE_DTLS_SERVER *server_ptr);

```

### <a name="description"></a><span data-ttu-id="8397b-461">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-461">Description</span></span>

<span data-ttu-id="8397b-462">このサービスでは DTLS Server が開始されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-462">This service starts a DTLS Server.</span></span> <span data-ttu-id="8397b-463">呼び出しから制御が戻ると、サーバーがアクティブになり、DTLS クライアントからの受信要求の処理が開始されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-463">After the call returns, the server is active and will begin processing incoming requests from DTLS clients.</span></span> <span data-ttu-id="8397b-464">サーバー インスタンスは、サービス *nx_secure_dtls_server_create* を使用して構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-464">The server instance must have been configured with the service *nx_secure_dtls_server_create*.</span></span>

> [!NOTE]
> <span data-ttu-id="8397b-465">このサービスでは、内部 DTLS Server の UDP ポートが構成済みのローカル ポートにバインドされます。このため、発生するほとんどの問題は UDP 通信とネットワーク構成に関係するものになります。</span><span class="sxs-lookup"><span data-stu-id="8397b-465">This service binds the internal DTLS Server UDP port to the configured local port so most issues encountered will have to do with UDP communications and network configuration.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-466">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-466">Parameters</span></span>

- <span data-ttu-id="8397b-467">**server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-467">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-468">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-468">Return Values</span></span>

- <span data-ttu-id="8397b-469">**NX_SUCCESS** (0x00) サーバーが正常に開始されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-469">**NX_SUCCESS** (0x00) Successful start of server.</span></span>
- <span data-ttu-id="8397b-470">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-470">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="8397b-471">**NX_NOT_ENABLED** (0x14) UDP が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="8397b-471">**NX_NOT_ENABLED** (0x14) UDP not enabled.</span></span>
- <span data-ttu-id="8397b-472">**NX_NO_FREE_PORTS** (0x45) 使用可能な UDP ポートがありません。</span><span class="sxs-lookup"><span data-stu-id="8397b-472">**NX_NO_FREE_PORTS** (0x45) No available UDP ports.</span></span>
- <span data-ttu-id="8397b-473">**NX_INVALID_PORT** (0x46) UDP ポートが無効です。</span><span class="sxs-lookup"><span data-stu-id="8397b-473">**NX_INVALID_PORT** (0x46) Invalid UDP port.</span></span>
- <span data-ttu-id="8397b-474">**NX_ALREADY_BOUND** (0x22) UDP ポートは既にバインドされています。</span><span class="sxs-lookup"><span data-stu-id="8397b-474">**NX_ALREADY_BOUND** (0x22) UDP port already bound.</span></span>
- <span data-ttu-id="8397b-475">**NX_PORT_UNAVAILABLE** (0x23) UDP ポートを使用できません。</span><span class="sxs-lookup"><span data-stu-id="8397b-475">**NX_PORT_UNAVAILABLE** (0x23) UDP port not available for use.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-476">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-476">Allowed From</span></span>

<span data-ttu-id="8397b-477">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-478">例</span><span class="sxs-lookup"><span data-stu-id="8397b-478">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                &send_packet, NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
                (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="8397b-479">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-479">See Also</span></span>

- <span data-ttu-id="8397b-480">nx_secure_dtls_server_stop、nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="8397b-480">nx_secure_dtls_server_stop, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="8397b-481">nx_secure_dtls_server_delete、nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="8397b-481">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="8397b-482">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="8397b-482">nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="8397b-483">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-483">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_stop"></a><span data-ttu-id="8397b-484">nx_secure_dtls_server_stop</span><span class="sxs-lookup"><span data-stu-id="8397b-484">nx_secure_dtls_server_stop</span></span>

<span data-ttu-id="8397b-485">アクティブな NetX Secure DTLS Server インスタンスを停止する</span><span class="sxs-lookup"><span data-stu-id="8397b-485">Stop an active NetX Secure DTLS Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-486">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-486">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_stop(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="8397b-487">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-487">Description</span></span>

<span data-ttu-id="8397b-488">このサービスでは、構成されている UDP ポートでの DTLS Server によるリスニングが停止され、関連付けられているすべての DTLS セッションがリセットされ、進行中の DTLS 通信が停止されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-488">This service stops a DTLS Server from listening on the configure UDP port and resets all the associated DTLS sessions, halting any in-progress DTLS communications.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-489">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-489">Parameters</span></span>

- <span data-ttu-id="8397b-490">**server_ptr** アクティブな DTLS Server インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-490">**server_ptr** Pointer to an active DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-491">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-491">Return Values</span></span>

- <span data-ttu-id="8397b-492">**NX_SUCCESS** (0x00) サーバーが正常に停止されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-492">**NX_SUCCESS** (0x00) Successful stop of server.</span></span>
- <span data-ttu-id="8397b-493">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-493">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-494">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-494">Allowed From</span></span>

<span data-ttu-id="8397b-495">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-495">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-496">例</span><span class="sxs-lookup"><span data-stu-id="8397b-496">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* We have exited the processing loop, stop the server. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="8397b-497">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-497">See Also</span></span>

- <span data-ttu-id="8397b-498">nx_secure_dtls_server_start、nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="8397b-498">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="8397b-499">nx_secure_dtls_server_delete、nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="8397b-499">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="8397b-500">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="8397b-500">nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="8397b-501">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-501">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_trusted_certificate_add"></a><span data-ttu-id="8397b-502">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-502">nx_secure_dtls_server_trusted_certificate_add</span></span>

<span data-ttu-id="8397b-503">NetX Secure DTLS Server に信頼された CA 証明書を追加する</span><span class="sxs-lookup"><span data-stu-id="8397b-503">Add a trusted CA certificate to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-504">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-504">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_trusted_certificate_add(
                                         NX_SECURE_DTLS_SERVER *server_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="8397b-505">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-505">Description</span></span>

<span data-ttu-id="8397b-506">このサービスでは、信頼された CA 証明書または中間 CA 証明書が DTLS Server インスタンスに追加され、すべての内部 DTLS サーバー セッションに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="8397b-506">This service adds a trusted CA or intermediate CA certificate to a DTLS Server instance and assigned to all the internal DTLS server sessions.</span></span> <span data-ttu-id="8397b-507">これは、*nx_secure_dtls_server_x509_client_verify_configure* を使用して X.509 クライアント証明書の認証が有効にされている場合にのみ必要となります。</span><span class="sxs-lookup"><span data-stu-id="8397b-507">This is only necessary if X.509 Client certificate authentication is enabled using *nx_secure_dtls_server_x509_client_verify_configure*.</span></span> <span data-ttu-id="8397b-508">追加された証明書は、受信したクライアントの X.509 証明書の検証に使用されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-508">The added certificate will be used to verify incoming Client X.509 certificates.</span></span>

<span data-ttu-id="8397b-509">cert_id パラメーターは、証明書の 0 以外の数値の識別子です。</span><span class="sxs-lookup"><span data-stu-id="8397b-509">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="8397b-510">これにより、DTLS サーバー ストアに同じ X.509 の共通名を持つ複数の ID 証明書がある場合に、証明書を簡単に削除したり、見つけたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="8397b-510">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS server store.</span></span> <span data-ttu-id="8397b-511">X.509 サーバー証明書の詳細については、『NetX Secure TLS ユーザー ガイド』を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8397b-511">See the NetX Secure TLS User Guide for more information about X.509 server certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-512">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-512">Parameters</span></span>

- <span data-ttu-id="8397b-513">**server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-513">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="8397b-514">**certificate** 以前に初期化された X.509 証明書構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-514">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="8397b-515">**cert_id** この DTLS サーバー内のこの証明書に対する 0 以外の数値の一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="8397b-515">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-516">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-516">Return Values</span></span>

- <span data-ttu-id="8397b-517">**NX_SUCCESS** (0x00) DTLS サーバーに証明書が正常に追加されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-517">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS server.</span></span>
- <span data-ttu-id="8397b-518">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-518">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="8397b-519">**NX_INVALID_PARAMETERS** (0x4D) 証明書 ID として 0 が渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-519">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-520">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-520">Allowed From</span></span>

<span data-ttu-id="8397b-521">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-521">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-522">例</span><span class="sxs-lookup"><span data-stu-id="8397b-522">Example</span></span>

<span data-ttu-id="8397b-523">*より完全な例については、*nx_secure_dtls_server_create\* のリファレンスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8397b-523">\*See reference for *nx_secure_dtls_server_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0, NX_NULL,
                                            0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add trusted CA certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a><span data-ttu-id="8397b-524">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-524">See Also</span></span>

- <span data-ttu-id="8397b-525">nx_secure_dtls_server_start、nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="8397b-525">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="8397b-526">nx_secure_dtls_session_receive、nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="8397b-526">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="8397b-527">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-527">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="8397b-528">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-528">nx_secure_dtls_server_local_certificate_add,</span></span>
- <span data-ttu-id="8397b-529">nx_secure_dtls_server_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="8397b-529">nx_secure_dtls_server_trusted_certificate_remove,</span></span>
- <span data-ttu-id="8397b-530">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="8397b-530">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_trusted_certificate_remove"></a><span data-ttu-id="8397b-531">nx_secure_dtls_server_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="8397b-531">nx_secure_dtls_server_trusted_certificate_remove</span></span>

<span data-ttu-id="8397b-532">NetX Secure DTLS Server から信頼された CA 証明書を削除する</span><span class="sxs-lookup"><span data-stu-id="8397b-532">Remove a trusted CA certificate from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-533">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-533">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_trusted_certificate_remove(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *common_name,
                                UINT common_name_length,
                                UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="8397b-534">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-534">Description</span></span>

<span data-ttu-id="8397b-535">このサービスでは、DTLS Server インスタンスから信頼された CA 証明書が削除されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-535">This service removes a trusted CA certificate from a DTLS Server instance.</span></span> <span data-ttu-id="8397b-536">信頼された CA 証明書が必要になるのは、*nx_secure_dtls_server_x509_client_verify_configure* を呼び出されて X.509 クライアント証明書の検証が有効になっている DTLS Server だけです。</span><span class="sxs-lookup"><span data-stu-id="8397b-536">Trusted CA certificates are only necessary for a DTLS Server for which X.509 Client certificate verification has been enabled by calling *nx_secure_dtls_server_x509_client_verify_configure*.</span></span>

<span data-ttu-id="8397b-537">削除する証明書は、X.509 の共通名、または *nx_secure_dtls_server_trusted_certificate_add* への呼び出しで割り当てられた数値である cert_id によって識別できます。</span><span class="sxs-lookup"><span data-stu-id="8397b-537">The certificate to be removed can be identified either by its X.509 Common Name or by the numeric cert_id that was assigned in the call to *nx_secure_dtls_server_trusted_certificate_add*.</span></span> <span data-ttu-id="8397b-538">cert_id は証明書の識別にのみ使用され、アプリケーションによって管理されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-538">The cert_id is only used to identify the certificate and is maintained by the application.</span></span> <span data-ttu-id="8397b-539">数値の証明書 ID の代わりに共通名を使用する場合は、cert_id パラメーターを 0 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-539">If the Common Name is used instead of the numeric certificate identifier, the cert_id parameter should be set to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="8397b-540">DTLS ハンドシェイクの処理中に証明書を削除すると、予期しない動作が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="8397b-540">Removing a certificate while a DTLS handshake is being processed may result in unexpected behavior.</span></span> <span data-ttu-id="8397b-541">証明書を削除する前に、サービス *nx_secure_dtls_server_stop* を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-541">The service *nx_secure_dtls_server_stop* should be called before removing certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-542">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-542">Parameters</span></span>

- <span data-ttu-id="8397b-543">**server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-543">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="8397b-544">**common_name** 削除する証明書の X.509 CommonName。</span><span class="sxs-lookup"><span data-stu-id="8397b-544">**common_name** X.509 CommonName of the certificate to remove.</span></span> <span data-ttu-id="8397b-545">これを使用する場合は、cert_id を 0 として渡します。</span><span class="sxs-lookup"><span data-stu-id="8397b-545">If this is used, pass cert_id as zero.</span></span>
- <span data-ttu-id="8397b-546">**common_name_length** common_name 文字列の長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="8397b-546">**common_name_length** Length of common_name string in bytes.</span></span>
- <span data-ttu-id="8397b-547">**cert_id** この DTLS サーバー内のこの証明書に対する 0 以外の数値の一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="8397b-547">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span> <span data-ttu-id="8397b-548">これを使用する場合は、common_name パラメーターに NX_NULL を渡します。</span><span class="sxs-lookup"><span data-stu-id="8397b-548">If this is used, pass NX_NULL for the common_name parameter.</span></span>


### <a name="return-values"></a><span data-ttu-id="8397b-549">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-549">Return Values</span></span>

- <span data-ttu-id="8397b-550">**NX_SUCCESS** (0x00) DTLS サーバーから証明書が正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-550">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS server.</span></span>
- <span data-ttu-id="8397b-551">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-551">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="8397b-552">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) 指定された DTLS サーバーで cert_id または common_name に一致する証明書が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="8397b-552">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS server.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-553">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-553">Allowed From</span></span>

<span data-ttu-id="8397b-554">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-555">例</span><span class="sxs-lookup"><span data-stu-id="8397b-555">Example</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                                    certificate_der_data,
                                                    sizeof(certificate_der_data),
                                                    NX_NULL, 0, NX_NULL, 0,
                                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                       &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);


/* At some point in the future we decide to remove the certificate we added. We can
       use the certificate identifier we passed into the call to
       nx_secure_dtls_trusted_certificate_add (value = 1); */
    status = nx_secure_dtls_server_trusted_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a><span data-ttu-id="8397b-556">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-556">See Also</span></span>

- <span data-ttu-id="8397b-557">nx_secure_dtls_server_start、nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="8397b-557">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="8397b-558">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-558">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="8397b-559">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="8397b-559">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="8397b-560">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-560">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="8397b-561">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="8397b-561">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_x509_client_verify_configure"></a><span data-ttu-id="8397b-562">nx_secure_dtls_server_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="8397b-562">nx_secure_dtls_server_x509_client_verify_configure</span></span>

<span data-ttu-id="8397b-563">クライアント証明書を要求して確認するように NetX Secure DTLS Server を構成する</span><span class="sxs-lookup"><span data-stu-id="8397b-563">Configure a NetX Secure DTLS Server to request and verify client certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-564">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-564">Prototype</span></span>

```C
UINT nx_secure_dtls_server_x509_client_verify_configure(
                           NX_SECURE_DTLS_SERVER *server_ptr,
                               UINT certs_per_session,
                               UCHAR *certs_buffer, ULONG buffer_size);

```

### <a name="description"></a><span data-ttu-id="8397b-565">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-565">Description</span></span>

<span data-ttu-id="8397b-566">このサービスでは、DTLS Client 証明書を要求して確認するように DTLS Server が構成されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-566">This service configures a DTLS Server to request and verify DTLS Client certificates.</span></span> <span data-ttu-id="8397b-567">このオプションの機能は、クライアント認証に他のメカニズム (事前共有キーなど) ではなく X.509 証明書が望ましい場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-567">This optional feature is used when X.509 certificates are desired for client authentication in place of other mechanisms (e.g. a Pre-Shared Key).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8397b-568">*DTLS Server がこのサービスを使用してクライアント証明書を検証するように構成されている場合、nx_secure_dtls_server_trusted_certificate_add を使用して少なくとも 1 つの信頼された CA 証明書をサーバーに追加する必要があります。そうしないと、信頼されたストアに対してクライアント証明書を検証できないため、すべての受信クライアント接続がサーバーで拒否されます。*</span><span class="sxs-lookup"><span data-stu-id="8397b-568">*When a DTLS Server is configured to verify client certificates using this service, at least one trusted CA certificate must be added to the server using nx_secure_dtls_server_trusted_certificate_add or the server will reject all incoming client connections because it will be unable to verify client certificates against the trusted store.*</span></span>

<span data-ttu-id="8397b-569">このサービスを呼び出すと、DTLS Server インスタンスでは (開始された後に)、DTLS ハンドシェイクの一環としてクライアント証明書を要求します。</span><span class="sxs-lookup"><span data-stu-id="8397b-569">Upon calling this service, the DTLS Server instance will (once started) request client certificates as part of the DTLS handshake.</span></span> <span data-ttu-id="8397b-570">クライアントが ID 証明書 (および該当する場合は関連する証明書チェーン) を使用して適切に構成されていると想定し、DTLS Server では、クライアント証明書のデータを処理するためにメモリを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-570">Assuming the client is properly configured with an identity certificate (and associated certificate chain when applicable), the DTLS Server requires memory to be allocated to process the client certificate data.</span></span> <span data-ttu-id="8397b-571">このメモリは *certs_buffer* パラメーターとして渡されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-571">This memory is passed in as the *certs_buffer* parameter.</span></span>

<span data-ttu-id="8397b-572">DTLS Client からの予想される最大の証明書チェーン ("*DTLS クライアント x DTLS サーバーのセッション数*") を格納できるように、certs_buffer のサイズを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-572">The certs_buffer must be sized to accommodate the largest expected certificate chain from a DTLS client, *times the number of DTLS server sessions*.</span></span> <span data-ttu-id="8397b-573">バッファーは、クライアント証明書チェーンで予想される最大の証明書数を表す *certs_per_session* パラメーターを使用して、使用可能なセッション間で分割されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-573">The buffer is divided amongst the available sessions using the *certs_per_session* parameter which represents the maximum expected number of certificates in a Client certificate chain.</span></span> <span data-ttu-id="8397b-574">また、このバッファーでは、証明書データを解析するために使用される NX_SECURE_X509_CERT データ構造のための領域が提供される必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-574">The buffer also needs to provide space for the NX_SECURE_X509_CERT data structure which is used to parse the certificate data.</span></span>

<span data-ttu-id="8397b-575">適切なバッファー サイズを計算するには、次の式を使用します。</span><span class="sxs-lookup"><span data-stu-id="8397b-575">Calculating the proper buffer size can be done with the following formula:</span></span>

```C
buffer_size = (# of DTLS sessions in server) *
                (certs_per_session) *
                (    maximum expected certificate size +
                      sizeof(NX_SECURE_X509_CERT)    )

```

- <span data-ttu-id="8397b-576">DTLS セッションの数は、nx_secure_dtls_server_create に渡されるセッション バッファーのサイズによって決まります。</span><span class="sxs-lookup"><span data-stu-id="8397b-576">The number of DTLS sessions is determined by the size of the session buffer passed into nx_secure_dtls_server_create.</span></span>
- <span data-ttu-id="8397b-577">certs_per_session は、クライアント証明書チェーンで予想される最大の証明書数に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-577">certs_per_session should be set to the maximum expected number of certificates in any client certificate chain.</span></span>
- <span data-ttu-id="8397b-578">予想される証明書の最大サイズは、アプリケーション、キーのサイズ、およびその他の要因によって異なりますが、通常は 2 KB で十分です。</span><span class="sxs-lookup"><span data-stu-id="8397b-578">The maximum expected certificate size is dependent on the application, key sizes, and other factors but 2KB is generally sufficient.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-579">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-579">Parameters</span></span>

- <span data-ttu-id="8397b-580">**server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-580">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="8397b-581">**certs_per_session** 各 DTLS サーバー セッションに割り当てる証明書の数。</span><span class="sxs-lookup"><span data-stu-id="8397b-581">**certs_per_session** Number of certificates to allocate to each DTLS server session.</span></span>
- <span data-ttu-id="8397b-582">**certs_buffer** 受信証明書データ用のバッファー領域。</span><span class="sxs-lookup"><span data-stu-id="8397b-582">**certs_buffer** Buffer space for incoming certificate data.</span></span>
- <span data-ttu-id="8397b-583">**buffer_size** 証明書バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="8397b-583">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-584">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-584">Return Values</span></span>

- <span data-ttu-id="8397b-585">**NX_SUCCESS** (0x00) X.509 クライアント検証が正常に構成されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-585">**NX_SUCCESS** (0x00) Successful configuration of X.509 Client verification.</span></span>
- <span data-ttu-id="8397b-586">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-586">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="8397b-587">**NX_INVALID_PARAMETERS** (0x4D) 証明書ストアが無効です (DTLS サーバー インスタンスが初期化されていない?)。</span><span class="sxs-lookup"><span data-stu-id="8397b-587">**NX_INVALID_PARAMETERS** (0x4D) Invalid certificate store (DTLSserver instance not initalized?).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-588">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-588">Allowed From</span></span>

<span data-ttu-id="8397b-589">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-589">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-590">例</span><span class="sxs-lookup"><span data-stu-id="8397b-590">Example</span></span>

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                                    sizeof(certificate_der_data),
                                    NX_NULL, 0,
                                    NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */
}

```

### <a name="see-also"></a><span data-ttu-id="8397b-591">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-591">See Also</span></span>

- <span data-ttu-id="8397b-592">nx_secure_dtls_server_x509_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="8397b-592">nx_secure_dtls_server_x509_client_verify_disable,</span></span>
- <span data-ttu-id="8397b-593">nx_secure_dtls_server_start、nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="8397b-593">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="8397b-594">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-594">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="8397b-595">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="8397b-595">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="8397b-596">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-596">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="8397b-597">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="8397b-597">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_x509_client_verify_disable"></a><span data-ttu-id="8397b-598">nx_secure_dtls_server_x509_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="8397b-598">nx_secure_dtls_server_x509_client_verify_disable</span></span>

<span data-ttu-id="8397b-599">NetX Secure DTLS Server のクライアント X.509 証明書の検証を無効にする</span><span class="sxs-lookup"><span data-stu-id="8397b-599">Disables client X.509 certificate verification for a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-600">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-600">Prototype</span></span>

```C
UINT nx_secure_dtls_server_x509_client_verify_disable(
                           NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="8397b-601">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-601">Description</span></span>

<span data-ttu-id="8397b-602">このサービスでは、DTLS Server での X.509 クライアント証明書の検証が無効にされます。</span><span class="sxs-lookup"><span data-stu-id="8397b-602">This service disables X.509 Client certificate verification on a DTLS Server.</span></span> <span data-ttu-id="8397b-603">X.509 クライアント証明書の検証が有効になっていない場合、このサービスは効果がありません。</span><span class="sxs-lookup"><span data-stu-id="8397b-603">The service has no effect if X.509 Client certificate verification is not enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="8397b-604">アクティブな DTLS Server インスタンスでクライアント認証を無効にすると、予期しない動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-604">Disabling client authentication on an active DTLS Server instance may result in unpredictable behavior.</span></span> <span data-ttu-id="8397b-605">サーバーの状態を変更する前に、nx_secure_dtls_server_stop サービスを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-605">The nx_secure_dtls_server_stop service should be called before changing server state.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-606">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-606">Parameters</span></span>

- <span data-ttu-id="8397b-607">**server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-607">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-608">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-608">Return Values</span></span>

- <span data-ttu-id="8397b-609">**NX_SUCCESS** (0x00) X.509 クライアント認証が正常に無効にされました。</span><span class="sxs-lookup"><span data-stu-id="8397b-609">**NX_SUCCESS** (0x00) Successful disabling of X.509 client authentication.</span></span>
- <span data-ttu-id="8397b-610">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-610">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-611">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-611">Allowed From</span></span>

<span data-ttu-id="8397b-612">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-612">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-613">例</span><span class="sxs-lookup"><span data-stu-id="8397b-613">Example</span></span>

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                        sizeof(certificate_der_data), NX_NULL, 0,
                        NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before changing state. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* Disable X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_disable(&dtls_server);

}

```

### <a name="see-also"></a><span data-ttu-id="8397b-614">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-614">See Also</span></span>

- <span data-ttu-id="8397b-615">nx_secure_dtls_server_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="8397b-615">nx_secure_dtls_server_x509_client_verify_configure,</span></span>
- <span data-ttu-id="8397b-616">nx_secure_dtls_server_start、nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="8397b-616">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="8397b-617">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-617">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="8397b-618">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="8397b-618">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="8397b-619">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-619">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="8397b-620">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="8397b-620">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_client_info_get"></a><span data-ttu-id="8397b-621">nx_secure_dtls_session_client_info_get</span><span class="sxs-lookup"><span data-stu-id="8397b-621">nx_secure_dtls_session_client_info_get</span></span>

<span data-ttu-id="8397b-622">DTLS Server セッションからリモート クライアントの情報を取得する</span><span class="sxs-lookup"><span data-stu-id="8397b-622">Get remote client information from a DTLS Server session</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-623">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-623">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_client_info_get(
                                    NX_SECURE_DTLS_SESSION *session_ptr,
                                    NXD_ADDRESS *client_ip_address,
                                    UINT *client_port, UINT *local_port);

```

### <a name="description"></a><span data-ttu-id="8397b-624">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-624">Description</span></span>

<span data-ttu-id="8397b-625">このサービスでは、特定の DTLS Server セッションに接続されている DTLS Client に関するネットワーク情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-625">This service returns the network information about a DTLS Client that is connected to a particular DTLS Server session.</span></span> <span data-ttu-id="8397b-626">返される情報は、リモート クライアントの IP アドレスと UDP ポート、およびクライアントが接続されているローカル サーバーのポートで構成されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-626">The information returned consists of the remote client’s IP address and UDP port, as well as the local server port to which the client is connected.</span></span>

<span data-ttu-id="8397b-627">一般に、DTLS セッション インスタンスは、いずれかの DTLS 通知コールバック ルーチン (nx_secure_dtls_server_create に渡される connect_notify または receive_notify コールバックなど) の呼び出しで取得されたものです。</span><span class="sxs-lookup"><span data-stu-id="8397b-627">In general, the DTLS session instance will be the one obtained in the invocation of one of the DTLS notification callback routines (e.g. the connect_notify or receive_notify callbacks passed into nx_secure_dtls_server_create).</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-628">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-628">Parameters</span></span>

- <span data-ttu-id="8397b-629">**session_ptr** アクティブな DTLS サーバー セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-629">**session_ptr** Pointer to an active DTLS server session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-630">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-630">Return Values</span></span>

- <span data-ttu-id="8397b-631">**NX_SUCCESS** (0x00) サーバーが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-631">**NX_SUCCESS** (0x00) Successful deletion of server.</span></span>
- <span data-ttu-id="8397b-632">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-632">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="8397b-633">**NX_INVALID_SOCKET** (0x13) 関連付けられている UDP ソケットが有効ではありません (セッションが初期化されていない?)。</span><span class="sxs-lookup"><span data-stu-id="8397b-633">**NX_INVALID_SOCKET** (0x13) The associated UDP socket is not valid (session not initialized?).</span></span>
- <span data-ttu-id="8397b-634">**NX_NOT_CONNECTED** (0x38) UDP ソケットが接続されていません – クライアント接続が切断されたか、まだ確立されていません。</span><span class="sxs-lookup"><span data-stu-id="8397b-634">**NX_NOT_CONNECTED** (0x38) UDP socket is not connected – client connection dropped or not yet established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-635">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-635">Allowed From</span></span>

<span data-ttu-id="8397b-636">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-636">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-637">例</span><span class="sxs-lookup"><span data-stu-id="8397b-637">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array
   or list in case a new connection is
   attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
                                                            *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    NXD_ADDRESS client_ip;
    UINT client_port, server_port;

    /* Get DTLS client information which can be used in filtering or associating
       the DTLS session with application data (e.g. a session pointer table). */
    status = nx_secure_dtls_session_client_info_get(dtls_session, &client_ip,
   &client_port, &server_port);

    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="8397b-638">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-638">See Also</span></span>

- <span data-ttu-id="8397b-639">nx_secure_dtls_server_start、nx_secure_dtls_server_stop</span><span class="sxs-lookup"><span data-stu-id="8397b-639">nx_secure_dtls_server_start, nx_secure_dtls_server_stop,</span></span>
- <span data-ttu-id="8397b-640">nx_secure_dtls_server_create、nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="8397b-640">nx_secure_dtls_server_create, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="8397b-641">nx_secure_dtls_session_receive、nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="8397b-641">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="8397b-642">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-642">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_session_create"></a><span data-ttu-id="8397b-643">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="8397b-643">nx_secure_dtls_session_create</span></span>

<span data-ttu-id="8397b-644">NetX Secure DTLS Session を作成して構成する</span><span class="sxs-lookup"><span data-stu-id="8397b-644">Create and configure a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-645">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-645">Prototype</span></span>

```C
UINT nx_secure_dtls_session_create(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        VOID *metadata_buffer, ULONG metadata_size,
                        UCHAR *packet_reassembly_buffer,
                        UINT packet_reassembly_buffer_size,
                        UINT certs_number,
                        UCHAR *remote_certificate_buffer,
                        ULONG remote_certificate_buffer_size));

```

### <a name="description"></a><span data-ttu-id="8397b-646">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-646">Description</span></span>

<span data-ttu-id="8397b-647">このサービスでは、DTLS セッションを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="8397b-647">This service creates and configures a DTLS session.</span></span> <span data-ttu-id="8397b-648">DTLS Server セッションは DTLS Server のメカニズムで管理されるため、通常、これは DTLS Client のセッションを作成するために使用されます (*nx_secure_dtls_server_create* を参照してください)。ただし、アプリケーションで 1 つのスタンドアロン DTLS Server セッション インスタンスを作成する必要がある場合に、このサービスを使用できます<sup>7</sup>。</span><span class="sxs-lookup"><span data-stu-id="8397b-648">Generally, this will be used to create DTLS Client sessions as DTLS Server sessions are managed with the DTLS Server mechanism (see *nx_secure_dtls_server_create*), but there may be instances where an application needs to create a single stand-alone DTLS Server session instance in which case this service may be used<sup>7</sup>.</span></span>

<span data-ttu-id="8397b-649">パラメーターによって、DTLS セッションをインスタンス化するために必要な情報とメモリの割り当てが構成されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-649">The parameters configure the information and memory allocation needed to instantiate a DTLS session.</span></span> <span data-ttu-id="8397b-650">crypto_table パラメーターは、TLS/DTLS の暗号化と認証に必要なすべての暗号化ルーチンを含む TLS テーブルです。</span><span class="sxs-lookup"><span data-stu-id="8397b-650">The crypto_table parameter is a TLS table containing all of the cryptographic routines needed for TLS/DTLS encryption and authentication.</span></span> <span data-ttu-id="8397b-651">metadata_buffer は、暗号化の計算に使用されます (『NetX Secure TLS ユーザー ガイド』の nx_secure_tls_metadata_size_calculate を参照してください)。また、packet_reassembly_buffer は、暗号化の解除で UDP データグラムを完全な DTLS レコードに再構築するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-651">The metadata_buffer is used for encryption caclulations (see nx_secure_tls_metadata_size_calculate in the NetX Secure TLS User Guide), and the packet_reassembly_buffer is used to reassemble UDP datagrams into a complete DTLS record for decryption.</span></span>

<span data-ttu-id="8397b-652">DTLS Client には、受信した DTLS Server の証明書チェーンを格納して処理するための領域が必要であり、certs_number と remote_certificate_buffer が必要となります。</span><span class="sxs-lookup"><span data-stu-id="8397b-652">The certs_number and remote_certificate_buffer are required for DTLS Clients which need space to store and process the incoming DTLS Server certificate chain.</span></span> <span data-ttu-id="8397b-653">このバッファーでは、接続先のすべてのサーバーの証明書チェーンで予想される最大サイズを格納できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-653">The buffer must be able to accommodate the maximum expected size of the certificate chain for any server to which it will connect.</span></span> <span data-ttu-id="8397b-654">このバッファーは、予想される証明書の数 (certs_number パラメーター) によって分割されます。また、証明書ごとに 1 つの NX_SECURE_X509_CERT 構造体を保持するのに十分な大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-654">The buffer is divided up by the number of expected certificates (certs_number parameter) and must also be large enough to hold one NX_SECURE_X509_CERT structure per certificate.</span></span> <span data-ttu-id="8397b-655">バッファーのサイズは、次の式を使用して判別できます。</span><span class="sxs-lookup"><span data-stu-id="8397b-655">The buffer size can be determined using the following formula:</span></span>

```C
remote_certificate_buffer_size = (certs_number) *
                 (maximum cert size + sizeof(NX_SECURE_X509_CERT))
```

- <span data-ttu-id="8397b-656">certs_number は、サーバーの証明書チェーンで予想される証明書の最大数です</span><span class="sxs-lookup"><span data-stu-id="8397b-656">certs_number is the expected maximum number of certificates in the server’s certificate chain</span></span>
- <span data-ttu-id="8397b-657">証明書の最大サイズは、使用されるキーのサイズと証明書の情報によって異なりますが、通常は 2 KB で十分です。</span><span class="sxs-lookup"><span data-stu-id="8397b-657">Maximum certificate size is dependent on the size of keys being used and the information in the certificate, but 2KB is generally sufficient.</span></span>

<span data-ttu-id="8397b-658">**7** このルーチンを使用して DTLS Server のセッションを作成することは推奨されておらず、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-658">**7** Creating DTLS Server sessions with this routine is not recommended and comes with some limitations.</span></span> <span data-ttu-id="8397b-659">主な問題は、セッションで追加のクライアント接続が正常に処理されないことです。UDP はコネクションレスであるため、2 番目のクライアントでは、以前の DTLS セッションがまだアクティブな状態で、そのセッションによりサーバー セッションがエラーで終了する可能性があるときに、サーバーの UDP ポートに対して正当にデータを送信できます。</span><span class="sxs-lookup"><span data-stu-id="8397b-659">The primary issue is that the session will not handle additional client connections gracefully – since UDP is connectionless a second client can legally send data to the server’s UDP port when a previous DTLS session is still active which would cause the server session to end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-660">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-660">Parameters</span></span>

- <span data-ttu-id="8397b-661">**dtls_session** 初期化されていない DTLS Session 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-661">**dtls_session** Pointer to an uninitialized DTLS Session structure.</span></span>
- <span data-ttu-id="8397b-662">**crypto_table** すべての暗号化操作に使用される TLS/DTLS 暗号化テーブル構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-662">**crypto_table** Pointer to a TLS/DTLS encryption table structure used for all cryptographic operations.</span></span>
- <span data-ttu-id="8397b-663">**crypto_metadata_buffer** 暗号化操作の計算と状態の情報を保持するためのバッファー領域。</span><span class="sxs-lookup"><span data-stu-id="8397b-663">**crypto_metadata_buffer** Buffer space for cryptographic operation calculations and state information.</span></span>
- <span data-ttu-id="8397b-664">**crypto_metadata_size** メタデータ バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="8397b-664">**crypto_metadata_size** Size of metadata buffer.</span></span>
- <span data-ttu-id="8397b-665">**packet_reassembly_buffer** 暗号化の解除で UDP データを DTLS レコードに再構築するために DTLS によって使用されるバッファー。</span><span class="sxs-lookup"><span data-stu-id="8397b-665">**packet_reassembly_buffer** Buffer used by DTLS to reassemble UDP data into DTLS records for decryption.</span></span>
- <span data-ttu-id="8397b-666">**packet_reassembly_buffer_size** 再構築バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="8397b-666">**packet_reassembly_buffer_size** Size of reassembly buffer.</span></span> <span data-ttu-id="8397b-667">通常は 16 KB を超えるサイズにする必要がありますが、アプリケーションによっては小さくすることができます。</span><span class="sxs-lookup"><span data-stu-id="8397b-667">Generally should be greater than 16KB but may be smaller depending on application.</span></span>
- <span data-ttu-id="8397b-668">**certs_number** リモート サーバーの証明書チェーンで予想される証明書の最大数。</span><span class="sxs-lookup"><span data-stu-id="8397b-668">**certs_number** Maximum expected number of certificates in the remote server’s certificate chain.</span></span>
- <span data-ttu-id="8397b-669">**remote_certificate_buffer** 受信証明書データ用のバッファー領域。</span><span class="sxs-lookup"><span data-stu-id="8397b-669">**remote_certificate_buffer** Buffer space for incoming certificate data.</span></span>
- <span data-ttu-id="8397b-670">**remote_certificate_buffer_size** 証明書バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="8397b-670">**remote_certificate_buffer_size** Size of the certificate buffer.</span></span>


### <a name="return-values"></a><span data-ttu-id="8397b-671">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-671">Return Values</span></span>

- <span data-ttu-id="8397b-672">**NX_SUCCESS** (0x00) セッションが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-672">**NX_SUCCESS** (0x00) Successful creation of session.</span></span>
- <span data-ttu-id="8397b-673">**NX_PTR_ERROR** (0x07) セッションまたはバッファーのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8397b-673">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>
- <span data-ttu-id="8397b-674">**NX_INVALID_PARAMETERS** (0x4D) は、パケットの再構築、証明書、または暗号化のための十分なバッファー領域がありません。</span><span class="sxs-lookup"><span data-stu-id="8397b-674">**NX_INVALID_PARAMETERS** (0x4D) Not enough buffer space for packet reassembly, certificates, or cryptography.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-675">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-675">Allowed From</span></span>

<span data-ttu-id="8397b-676">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-676">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-677">例</span><span class="sxs-lookup"><span data-stu-id="8397b-677">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
    &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                            &udp_socket, &server_ip,
                                            4443,
                                            NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session,
                                            &receive_packet,
                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="8397b-678">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-678">See Also</span></span>

- <span data-ttu-id="8397b-679">nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="8397b-679">nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="8397b-680">nx_secure_dtls_session_send</span><span class="sxs-lookup"><span data-stu-id="8397b-680">nx_secure_dtls_session_send</span></span>

## <a name="nx_secure_dtls_session_delete"></a><span data-ttu-id="8397b-681">nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="8397b-681">nx_secure_dtls_session_delete</span></span>

<span data-ttu-id="8397b-682">NetX Secure DTLS Session によって使用されているリソースを解放する</span><span class="sxs-lookup"><span data-stu-id="8397b-682">Free up resources used by a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-683">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-683">Prototype</span></span>

```C
UINT nx_secure_dtls_session_delete(
                        NX_SECURE_DTLS_SESSION *dtls_session);

```

### <a name="description"></a><span data-ttu-id="8397b-684">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-684">Description</span></span>

<span data-ttu-id="8397b-685">このサービスでは、DTLS セッションが削除され、その作成時に割り当てられたすべてのリソースが解放されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-685">This service deletes a DTLS session, freeing up any resources that were allocated when it was created.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-686">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-686">Parameters</span></span>

- <span data-ttu-id="8397b-687">**dtls_session** 以前に初期化された DTLS Session の構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-687">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-688">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-688">Return Values</span></span>

- <span data-ttu-id="8397b-689">**NX_SUCCESS** (0x00) セッションが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-689">**NX_SUCCESS** (0x00) Successful deletion of session.</span></span>
- <span data-ttu-id="8397b-690">**NX_PTR_ERROR** (0x07) セッションまたはバッファーのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8397b-690">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-691">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-691">Allowed From</span></span>

<span data-ttu-id="8397b-692">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-693">例</span><span class="sxs-lookup"><span data-stu-id="8397b-693">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                        trusted_cert_der,
                                        trusted_cert_der_len,
                                        NX_NULL, 0, NX_NULL, 0,
                                        NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                    &udp_socket,
                                                    &server_ip, 4443,
                                                    NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                &receive_packet,
                                                NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="8397b-694">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-694">See Also</span></span>

- <span data-ttu-id="8397b-695">nx_secure_dtls_client_session_start、nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="8397b-695">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="8397b-696">nx_secure_dtls_session_send、nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="8397b-696">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_end"></a><span data-ttu-id="8397b-697">nx_secure_dtls_session_end</span><span class="sxs-lookup"><span data-stu-id="8397b-697">nx_secure_dtls_session_end</span></span>

<span data-ttu-id="8397b-698">Active NetX Secure DTLS Session を停止する</span><span class="sxs-lookup"><span data-stu-id="8397b-698">Shut down an active NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-699">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-699">Prototype</span></span>

```C
UINT nx_secure_dtls_session_end(NX_SECURE_DTLS_SESSION *dtls_session,
                                UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="8397b-700">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-700">Description</span></span>

<span data-ttu-id="8397b-701">このサービスでは、TLS/DTLS の CloseNotify アラートをリモート ホストに送信することによって、アクティブな DTLS セッションが終了されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-701">This service ends an active DTLS session by sending a TLS/DTLS CloseNotify alert to the remote host.</span></span> <span data-ttu-id="8397b-702">使用される IP アドレスとポートは、以前に nx_secure_dtls_session_send を呼び出したときに使用されたものです。</span><span class="sxs-lookup"><span data-stu-id="8397b-702">The IP address and port used are those used in the previous call to nx_secure_dtls_session_send.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-703">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-703">Parameters</span></span>

- <span data-ttu-id="8397b-704">**dtls_session** 以前に初期化された DTLS Session の構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-704">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="8397b-705">**wait_option** ネットワーク操作に使用される ThreadX の待機値。</span><span class="sxs-lookup"><span data-stu-id="8397b-705">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-706">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-706">Return Values</span></span>

- <span data-ttu-id="8397b-707">**NX_SUCCESS** (0x00) セッションが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-707">**NX_SUCCESS** (0x00) Successful deletion of session.</span></span>
- <span data-ttu-id="8397b-708">**NX_PTR_ERROR** (0x07) セッションまたはバッファーのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8397b-708">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>
- <span data-ttu-id="8397b-709">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) CloseNotify アラートのパケットを割り当てることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="8397b-709">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate packet(s) for CloseNotify alert.</span></span>
- <span data-ttu-id="8397b-710">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105): 内部エラーが発生した可能性があります - 暗号化ルーチンが認識されません。</span><span class="sxs-lookup"><span data-stu-id="8397b-710">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Likely internal error – cryptographic routine not recognized.</span></span>
- <span data-ttu-id="8397b-711">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 基になる UDP の送信に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-711">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Underlying UDP send failed.</span></span>
- <span data-ttu-id="8397b-712">**NX_IP_ADDRESS_ERROR** (0x21) リモート ホストの IP アドレスでエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-712">**NX_IP_ADDRESS_ERROR** (0x21) Error with remote host IP address.</span></span>
- <span data-ttu-id="8397b-713">**NX_NOT_BOUND** (0x24) 基になる UDP ソケットがポートにバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="8397b-713">**NX_NOT_BOUND** (0x24) Underlying UDP socket not bound to port.</span></span>
- <span data-ttu-id="8397b-714">**NX_INVALID_PORT** (0x46) UDP ポートが無効です。</span><span class="sxs-lookup"><span data-stu-id="8397b-714">**NX_INVALID_PORT** (0x46) Invalid UDP port.</span></span>
- <span data-ttu-id="8397b-715">**NX_PORT_UNAVAILABLE** (0x23) UDP ポートを使用できません。</span><span class="sxs-lookup"><span data-stu-id="8397b-715">**NX_PORT_UNAVAILABLE** (0x23) UDP port not available for use.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-716">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-716">Allowed From</span></span>

<span data-ttu-id="8397b-717">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-717">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-718">例</span><span class="sxs-lookup"><span data-stu-id="8397b-718">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session,
                                        NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

    }

```

### <a name="see-also"></a><span data-ttu-id="8397b-719">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-719">See Also</span></span>

- <span data-ttu-id="8397b-720">nx_secure_dtls_client_session_start、nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="8397b-720">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="8397b-721">nx_secure_dtls_session_send、nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="8397b-721">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_local_certificate_add"></a><span data-ttu-id="8397b-722">nx_secure_dtls_session_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-722">nx_secure_dtls_session_local_certificate_add</span></span>

<span data-ttu-id="8397b-723">NetX Secure DTLS Session にローカル ID 証明書を追加する</span><span class="sxs-lookup"><span data-stu-id="8397b-723">Add a local identity certificate to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-724">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-724">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_local_certificate_add(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            NX_SECURE_X509_CERT *certificate,
                            UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="8397b-725">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-725">Description</span></span>

<span data-ttu-id="8397b-726">このサービスでは、ローカル ID 証明書が DTLS Session インスタンスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-726">This service adds a local identity certificate to a DTLS Session instance.</span></span> <span data-ttu-id="8397b-727">一般に、このサービスは、DTLS Client セッションでリモート サーバー ホストに ID 証明書を提示する必要がある場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-727">In general, this service will be used when a DTLS Client session needs to provide an identity certificate to a remote server host.</span></span> <span data-ttu-id="8397b-728">これは DTLS のオプションの構成であり、通常、DTLS Client には証明書は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="8397b-728">This is an optional configuration for DTLS so a certificate is not generally required for DTLS Clients.</span></span> <span data-ttu-id="8397b-729">ID 証明書には、関連付けられた秘密キーが必要です。</span><span class="sxs-lookup"><span data-stu-id="8397b-729">An identity certificate requires an associated private key.</span></span>

<span data-ttu-id="8397b-730">cert_id パラメーターは、証明書の 0 以外の数値の識別子です。</span><span class="sxs-lookup"><span data-stu-id="8397b-730">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="8397b-731">これにより、DTLS 証明書ストアに同じ X.509 の共通名を持つ複数の ID 証明書がある場合に、証明書を簡単に削除したり、見つけたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="8397b-731">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="8397b-732">X.509 証明書の詳細については、『NetX Secure TLS ユーザー ガイド』を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8397b-732">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-733">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-733">Parameters</span></span>

- <span data-ttu-id="8397b-734">**session_ptr** 以前に作成された DTLS Session インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-734">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="8397b-735">**certificate** 以前に初期化された X.509 証明書構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-735">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="8397b-736">**cert_id** この DTLS サーバー内のこの証明書に対する 0 以外の数値の一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="8397b-736">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-737">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-737">Return Values</span></span>

- <span data-ttu-id="8397b-738">**NX_SUCCESS** (0x00) DTLS セッションに証明書が正常に追加されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-738">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS session.</span></span>
- <span data-ttu-id="8397b-739">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-739">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="8397b-740">**NX_INVALID_PARAMETERS** (0x4D) 証明書 ID として 0 が渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-740">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-741">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-741">Allowed From</span></span>

<span data-ttu-id="8397b-742">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-742">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-743">例</span><span class="sxs-lookup"><span data-stu-id="8397b-743">Example</span></span>

<span data-ttu-id="8397b-744">*より完全な例については、*nx_secure_dtls_session_create\* のリファレンスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8397b-744">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity
certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

/* Create a TLS session for our socket. Ciphers and metadata defined
   elsewhere. See nx_secure_tls_session_create reference for more
   information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
{
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
}

/* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

/* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                              &certificate, 1);

    /* Initialize local server identity certificate with key and
    add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                        certificate_der_data,
                        sizeof(certificate_der_data),
                        NX_NULL, 0,
                        certificate_key_der_data,
                        sizeof(certificate_key_der_data),
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                    &certificate, 1);

/* Set up IP address of remote host. */
server_ip.nxd_ip_version = NX_IP_VERSION_V4;
server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


/* Now we can start the DTLS session as normal. */
status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                    &udp_socket, &server_ip, 4443,
                                    NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a><span data-ttu-id="8397b-745">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-745">See Also</span></span>

- <span data-ttu-id="8397b-746">nx_secure_dtls_session_create、nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="8397b-746">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="8397b-747">nx_secure_dtls_session_send、nx_secure_dtls_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-747">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="8397b-748">nx_secure_dtls_session_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="8397b-748">nx_secure_dtls_session_local_certificate_remove,</span></span>
- <span data-ttu-id="8397b-749">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="8397b-749">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_local_certificate_remove"></a><span data-ttu-id="8397b-750">nx_secure_dtls_session_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="8397b-750">nx_secure_dtls_session_local_certificate_remove</span></span>

<span data-ttu-id="8397b-751">NetX Secure DTLS Session からローカル ID 証明書を削除する</span><span class="sxs-lookup"><span data-stu-id="8397b-751">Remove a local identity certificate from a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-752">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-752">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_local_certificate_remove(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         UCHAR *common_name,
                                         UINT common_name_length, UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="8397b-753">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-753">Description</span></span>

<span data-ttu-id="8397b-754">このサービスでは、証明書 ID 番号 (nx_secure_dtls_session_local_certificate_add を使用して証明書が追加されたときに割り当てられた) または X.509 の CommonName フィールドを使用して、DTLS Session インスタンスからローカル ID 証明書が削除されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-754">This service removes a local identity certificate from a DTLS Session instance using either a certificate ID number (assigned when the certificate was added with nx_secure_dtls_session_local_certificate_add) or the X.509 CommonName field.</span></span>

<span data-ttu-id="8397b-755">証明書の照合に common_name が使用される場合は、cert_id パラメーターを 0 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-755">If the common_name is used to match the certificate, the cert_id parameter should be set to 0.</span></span> <span data-ttu-id="8397b-756">cert_id を使用する場合は、common_name に NX_NULL を値として渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-756">If cert_id is used, common_name should be passed a value of NX_NULL.</span></span>

<span data-ttu-id="8397b-757">cert_id パラメーターは、証明書の 0 以外の数値の識別子です。</span><span class="sxs-lookup"><span data-stu-id="8397b-757">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="8397b-758">これにより、DTLS 証明書ストアに同じ X.509 の共通名を持つ複数の ID 証明書がある場合に、証明書を簡単に削除したり、見つけたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="8397b-758">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="8397b-759">X.509 証明書の詳細については、『NetX Secure TLS ユーザー ガイド』を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8397b-759">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-760">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-760">Parameters</span></span>

- <span data-ttu-id="8397b-761">**session_ptr** 以前に作成された DTLS Session インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-761">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="8397b-762">**common_name** 照合する CommonName 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-762">**common_name** Pointer to the CommonName string to match.</span></span>
- <span data-ttu-id="8397b-763">**common_name_length** common_name 文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="8397b-763">**common_name_length** Length of the common_name string.</span></span>
- <span data-ttu-id="8397b-764">**cert_id** この DTLS サーバー内のこの証明書に対する 0 以外の数値の一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="8397b-764">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-765">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-765">Return Values</span></span>

- <span data-ttu-id="8397b-766">**NX_SUCCESS** (0x00) DTLS セッションから証明書が正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-766">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS session.</span></span>
- <span data-ttu-id="8397b-767">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-767">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="8397b-768">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) 指定された DTLS セッションで cert_id または common_name に一致する証明書が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="8397b-768">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-769">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-769">Allowed From</span></span>

<span data-ttu-id="8397b-770">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-770">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-771">例</span><span class="sxs-lookup"><span data-stu-id="8397b-771">Example</span></span>

<span data-ttu-id="8397b-772">*より完全な例については、*nx_secure_dtls_session_create\* のリファレンスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8397b-772">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

```C

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

        /* Initialize local server identity certificate with key
        and add to server. */
        status = nx_secure_x509_certificate_initialize(&certificate,
                                certificate_der_data,
                                sizeof(certificate_der_data),
                                NX_NULL, 0,
                                certificate_key_der_data,
                                sizeof(certificate_key_der_data),
                                NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

        /* Add local server identity certificate to DTLS server with ID of 1. */
        status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                            &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
        &udp_socket, &server_ip, 4443,
        NX_IP_PERIODIC_RATE);

        /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
        status = nx_secure_dtls_session_local_certificate_remove(&client_dtls_session,
                                                                NX_NULL, 0, 1);
}

```

### <a name="see-also"></a><span data-ttu-id="8397b-773">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-773">See Also</span></span>

- <span data-ttu-id="8397b-774">nx_secure_dtls_session_create、nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="8397b-774">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="8397b-775">nx_secure_dtls_session_send、nx_secure_dtls_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-775">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="8397b-776">nx_secure_dtls_session_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-776">nx_secure_dtls_session_local_certificate_add,</span></span>
- <span data-ttu-id="8397b-777">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="8397b-777">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_receive"></a><span data-ttu-id="8397b-778">nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="8397b-778">nx_secure_dtls_session_receive</span></span>

<span data-ttu-id="8397b-779">確立された NetX Secure DTLS Session 経由でアプリケーション データを受信する</span><span class="sxs-lookup"><span data-stu-id="8397b-779">Receive application data over an established NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-780">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-780">Prototype</span></span>

```C
UINT nx_secure_dtls_session_receive(
                                NX_SECURE_DTLS_SESSION *dtls_session,
                                NX_PACKET **packet_ptr_ptr,
                                UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="8397b-781">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-781">Description</span></span>

<span data-ttu-id="8397b-782">このサービスでは、アクティブな DTLS Session によって受信されたアプリケーション データが返されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-782">This service returns application data received by an active DTLS Session.</span></span> <span data-ttu-id="8397b-783">DTLS Session は、DTLS Server セッション (DTLS Server インスタンスによって管理されます) または DTLS Client セッションのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="8397b-783">The DTLS Session may be either a DTLS Server session (managed by a DTLS Server instance) or a DTLS Client session.</span></span> <span data-ttu-id="8397b-784">返されるパケットは、任意の NX_PACKET API サービスを使用して処理できます (詳細については、NetX のドキュメントを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="8397b-784">The returned packet may be processed using any of the NX_PACKET API services (see the NetX documentation for more information).</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-785">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-785">Parameters</span></span>

- <span data-ttu-id="8397b-786">**dtls_session** 以前に初期化された DTLS Session の構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-786">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="8397b-787">**packet_ptr_ptr** 戻りパケットの NX_PACKET ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-787">**packet_ptr_ptr** Pointer to an NX_PACKET pointer for the return packet.</span></span>
- <span data-ttu-id="8397b-788">**wait_option** ネットワーク操作に使用される ThreadX の待機値。</span><span class="sxs-lookup"><span data-stu-id="8397b-788">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-789">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-789">Return Values</span></span>

- <span data-ttu-id="8397b-790">**NX_SUCCESS** (0x00) アプリケーション データのパケットが正常に受信されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-790">**NX_SUCCESS** (0x00) Successful receipt of application data packet.</span></span>
- <span data-ttu-id="8397b-791">**NX_PTR_ERROR** (0x07) セッションまたはパケットのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8397b-791">**NX_PTR_ERROR** (0x07) Invalid session or packet pointer.</span></span>
- <span data-ttu-id="8397b-792">**NX_NOT_ENABLED** (0x14) UDP が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="8397b-792">**NX_NOT_ENABLED** (0x14) UDP is not enabled.</span></span>
- <span data-ttu-id="8397b-793">**NX_NOT_BOUND** (0x24) UDP ソケットがポートにバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="8397b-793">**NX_NOT_BOUND** (0x24) UDP socket not bound to port.</span></span>
- <span data-ttu-id="8397b-794">**NX_SECURE_TLS_INVALID_PACKET** (0x104) 有効な DTLS レコードではないデータを受信しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-794">**NX_SECURE_TLS_INVALID_PACKET** (0x104) Recevied data that was not a valid DTLS record.</span></span>
- <span data-ttu-id="8397b-795">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) DTLS レコードを正しくハッシュ化できませんでした (暗号化エラー)。</span><span class="sxs-lookup"><span data-stu-id="8397b-795">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A DTLS record failed to be properly hashed (encryption error).</span></span>
- <span data-ttu-id="8397b-796">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) 暗号化のパディング チェックに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-796">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Encryption padding check failure.</span></span>
- <span data-ttu-id="8397b-797">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) リモート ホストからアラートを受信しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-797">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied an alert from the remote host.</span></span>
- <span data-ttu-id="8397b-798">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) 認識されないメッセージを受信しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-798">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**    (0x102) Received an unrecognized message.</span></span>
- <span data-ttu-id="8397b-799">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) 長さが無効な DTLS レコードを受信しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-799">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied a DTLS record with an invalid length.</span></span>
- <span data-ttu-id="8397b-800">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) 不明な暗号スイートが見つかりました (内部暗号化エラーを示しています)。</span><span class="sxs-lookup"><span data-stu-id="8397b-800">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) An unknown ciphersuite was encountered (indicates internal cryptography error).</span></span>
- <span data-ttu-id="8397b-801">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) DTLS バージョンが一致しない DTLS レコードを受信しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-801">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied a DTLS record with a mismatched DTLS version.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-802">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-802">Allowed From</span></span>

<span data-ttu-id="8397b-803">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-803">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-804">例</span><span class="sxs-lookup"><span data-stu-id="8397b-804">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="8397b-805">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-805">See Also</span></span>

- <span data-ttu-id="8397b-806">nx_secure_dtls_client_session_start、nx_secure_dtls_session_end</span><span class="sxs-lookup"><span data-stu-id="8397b-806">nx_secure_dtls_client_session_start, nx_secure_dtls_session_end,</span></span>
- <span data-ttu-id="8397b-807">nx_secure_dtls_session_send、nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="8397b-807">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_reset"></a><span data-ttu-id="8397b-808">nx_secure_dtls_session_reset</span><span class="sxs-lookup"><span data-stu-id="8397b-808">nx_secure_dtls_session_reset</span></span>

<span data-ttu-id="8397b-809">NetX Secure DTLS Session インスタンスのデータをクリアする</span><span class="sxs-lookup"><span data-stu-id="8397b-809">Clear data in an NetX Secure DTLS Session instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-810">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-810">Prototype</span></span>

```C
UINT nx_secure_dtls_session_reset(NX_SECURE_DTLS_SESSION *dtls_session);
```

### <a name="description"></a><span data-ttu-id="8397b-811">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-811">Description</span></span>

<span data-ttu-id="8397b-812">このサービスでは、DTLS セッションをリセットし、すべての一時暗号化データをクリアし、その構造体を新しいセッションに再利用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8397b-812">This service resets a DTLS session, clearing all ephemeral cryptographic data and allowing the structure to be re-used for a new session.</span></span> <span data-ttu-id="8397b-813">nx_secure_dtls_session_create を繰り返し呼び出す必要がないように、永続データ (証明書ストアなど) は維持されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-813">Persistent data (e.g. certificate stores) are maintained so that nx_secure_dtls_session_create need not be called repeatedly.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-814">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-814">Parameters</span></span>

- <span data-ttu-id="8397b-815">**dtls_session** 以前に初期化された DTLS Session の構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-815">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-816">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-816">Return Values</span></span>

- <span data-ttu-id="8397b-817">**NX_SUCCESS** (0x00) セッションが正常にリセットされました。</span><span class="sxs-lookup"><span data-stu-id="8397b-817">**NX_SUCCESS** (0x00) Successful reset of session.</span></span>
- <span data-ttu-id="8397b-818">**NX_PTR_ERROR** (0x07) セッションまたはバッファーのポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8397b-818">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-819">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-819">Allowed From</span></span>

<span data-ttu-id="8397b-820">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-820">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-821">例</span><span class="sxs-lookup"><span data-stu-id="8397b-821">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_reset(&client_dtls_session);

    /* A new session can now be started using the same structure. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,



    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="8397b-822">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-822">See Also</span></span>

- <span data-ttu-id="8397b-823">nx_secure_dtls_client_session_start、nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="8397b-823">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="8397b-824">nx_secure_dtls_session_send、nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="8397b-824">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_-session_send"></a><span data-ttu-id="8397b-825">nx_secure_dtls_ session_send</span><span class="sxs-lookup"><span data-stu-id="8397b-825">nx_secure_dtls_ session_send</span></span>

<span data-ttu-id="8397b-826">DTLS セッション経由でデータを送信する</span><span class="sxs-lookup"><span data-stu-id="8397b-826">Send data over a DTLS session</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-827">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-827">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_send(NX_SECURE_DTLS_SESSION *session_ptr,
                                          NX_PACKET *packet_ptr,
                                          NXD_ADDRESS *ip_address, UINT port);

```

### <a name="description"></a><span data-ttu-id="8397b-828">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-828">Description</span></span>

<span data-ttu-id="8397b-829">このサービスでは、確立された DTLS Session を介して、指定された IP アドレスとポートのリモート DTLS ホストにデータのパケットが送信されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-829">This service sends a packet of data over an established DTLS Session to a remote DTLS host at the given IP address and port.</span></span> <span data-ttu-id="8397b-830">使用されるセッションは、アクティブな DTLS Client セッションです。</span><span class="sxs-lookup"><span data-stu-id="8397b-830">The session used is an active DTLS Client session.</span></span> <span data-ttu-id="8397b-831">IP アドレスとポートは、UDP のステートレスな性質のために提供されますが、通常は nx_secure_dtls_session_start でセッションを開始するために使用されるアドレスとポートと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-831">Note that the IP address and port are provided due to the stateless nature of UDP but should generally match the address and port used to start the session in nx_secure_dtls_session_start.</span></span>

<span data-ttu-id="8397b-832">パケットで提供されるデータは、*nx_secure_dtls_packet_allocate* を使用して割り当てる必要があります。このデータは、DTLS セッションの暗号化パラメーターとルーチンを使用して暗号化され、DTLS Session の UDP ソケットを介してリモート ホストに送信されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-832">The data provided in the packet, which must be allocated using *nx_secure_dtls_packet_allocate*, is encrypted using the DTLS session cryptographic parameters and routines and then sent to the remote host over the DTLS Session’s UDP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-833">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-833">Parameters</span></span>

- <span data-ttu-id="8397b-834">**session_ptr** アクティブな DTLS クライアント セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-834">**session_ptr** Pointer to an active DTLS client session instance.</span></span>
- <span data-ttu-id="8397b-835">**packet_ptr** 以前に割り当てられ、アプリケーション データが移入された NX_PACKET インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-835">**packet_ptr** Pointer to an NX_PACKET instance allocated previously and populated with application data.</span></span>
- <span data-ttu-id="8397b-836">**ip_address** リモート ホストの IP アドレスが含まれている NXD_ADDRESS 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-836">**ip_address** Pointer to an NXD_ADDRESS structure containing the IP address of the remote host.</span></span>
- <span data-ttu-id="8397b-837">**port** リモート ホストの UDP ポート。</span><span class="sxs-lookup"><span data-stu-id="8397b-837">**port** UDP port on the remote host.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-838">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-838">Return Values</span></span>

- <span data-ttu-id="8397b-839">**NX_SUCCESS** (0x00) パケットが正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-839">**NX_SUCCESS** (0x00) Successful send of packet.</span></span>
- <span data-ttu-id="8397b-840">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-840">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="8397b-841">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 基になる UDP の送信操作でエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="8397b-841">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An error occurred in the underlying UDP send operation.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-842">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-842">Allowed From</span></span>

<span data-ttu-id="8397b-843">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-843">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-844">例</span><span class="sxs-lookup"><span data-stu-id="8397b-844">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
    /* Error! */
    return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="8397b-845">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-845">See Also</span></span>

- <span data-ttu-id="8397b-846">nx_secure_dtls_client_session_start、nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="8397b-846">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="8397b-847">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="8397b-847">nx_secure_dtls_session_create</span></span>

## <a name="nx_secure_dtls_session_trusted_certificate_add"></a><span data-ttu-id="8397b-848">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-848">nx_secure_dtls_session_trusted_certificate_add</span></span>

<span data-ttu-id="8397b-849">NetX Secure DTLS Session に信頼された CA 証明書を追加する</span><span class="sxs-lookup"><span data-stu-id="8397b-849">Add a trusted CA certificate to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-850">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-850">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_trusted_certificate_add(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="8397b-851">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-851">Description</span></span>

<span data-ttu-id="8397b-852">このサービスでは、信頼された CA または中間 CA の X.509 証明書が DTLS Session インスタンスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-852">This service adds a trusted CA or intermediate CA X.509 certificate to a DTLS Session instance.</span></span> <span data-ttu-id="8397b-853">DTLS Client では、別の認証メカニズム (事前共有キーなど) が使用されている場合を除き、リモート サーバー証明書を検証するために、少なくとも 1 つの信頼された証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="8397b-853">A DTLS Client requires at least one trusted certificate in order to validate remote server certificates unless an alternative authentication mechanism is used (e.g. Pre-Shared Keys).</span></span> <span data-ttu-id="8397b-854">通常、信頼された証明書には秘密キーがありません。</span><span class="sxs-lookup"><span data-stu-id="8397b-854">A trusted certificate does not usually have a private key.</span></span>

<span data-ttu-id="8397b-855">cert_id パラメーターは、証明書の 0 以外の数値の識別子です。</span><span class="sxs-lookup"><span data-stu-id="8397b-855">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="8397b-856">これにより、DTLS 証明書ストアに同じ X.509 の共通名を持つ複数の ID 証明書がある場合に、証明書を簡単に削除したり、見つけたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="8397b-856">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="8397b-857">X.509 証明書の詳細については、『NetX Secure TLS ユーザー ガイド』を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8397b-857">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-858">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-858">Parameters</span></span>

- <span data-ttu-id="8397b-859">**session_ptr** 以前に作成された DTLS Session インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-859">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="8397b-860">**certificate** 以前に初期化された X.509 証明書構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-860">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="8397b-861">**cert_id** この DTLS サーバー内のこの証明書に対する 0 以外の数値の一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="8397b-861">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="8397b-862">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-862">Return Values</span></span>

- <span data-ttu-id="8397b-863">**NX_SUCCESS** (0x00) DTLS セッションに証明書が正常に追加されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-863">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS session.</span></span>
- <span data-ttu-id="8397b-864">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-864">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="8397b-865">**NX_INVALID_PARAMETERS** (0x4D) 証明書 ID として 0 が渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-865">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-866">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-866">Allowed From</span></span>

<span data-ttu-id="8397b-867">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-868">例</span><span class="sxs-lookup"><span data-stu-id="8397b-868">Example</span></span>

<span data-ttu-id="8397b-869">*より完全な例については、*nx_secure_dtls_session_create\* のリファレンスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8397b-869">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                            trusted_cert_der,
                                            trusted_cert_der_len,
                                            NX_NULL, 0, NX_NULL, 0,
                                            NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the trusted store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                      &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);

    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
         &udp_socket, &server_ip, 4443,
         NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a><span data-ttu-id="8397b-870">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-870">See Also</span></span>

- <span data-ttu-id="8397b-871">nx_secure_dtls_session_create、nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="8397b-871">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="8397b-872">nx_secure_dtls_session_send、nx_secure_dtls_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-872">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="8397b-873">nx_secure_dtls_session_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="8397b-873">nx_secure_dtls_session_trusted_certificate_remove,</span></span>
- <span data-ttu-id="8397b-874">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="8397b-874">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_trusted_certificate_remove"></a><span data-ttu-id="8397b-875">nx_secure_dtls_session_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="8397b-875">nx_secure_dtls_session_trusted_certificate_remove</span></span>

<span data-ttu-id="8397b-876">NetX Secure DTLS Session から信頼された CA 証明書を削除する</span><span class="sxs-lookup"><span data-stu-id="8397b-876">Remove a trusted CA certificate from a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="8397b-877">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8397b-877">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_trusted_certificate_remove(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *common_name,
                            UINT common_name_length, UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="8397b-878">説明</span><span class="sxs-lookup"><span data-stu-id="8397b-878">Description</span></span>

<span data-ttu-id="8397b-879">このサービスでは、証明書 ID 番号 (nx_secure_dtls_session_trusted_certificate_add を使用して証明書が追加されたときに割り当てられた) または X.509 の CommonName フィールドを使用して、DTLS Session インスタンスから信頼された CA 証明書が削除されます。</span><span class="sxs-lookup"><span data-stu-id="8397b-879">This service removes a trusted CA certificate from a DTLS Session instance using either a certificate ID number (assigned when the certificate was added with nx_secure_dtls_session_trusted_certificate_add) or the X.509 CommonName field.</span></span>

<span data-ttu-id="8397b-880">証明書の照合に common_name が使用される場合は、cert_id パラメーターを 0 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-880">If the common_name is used to match the certificate, the cert_id parameter should be set to 0.</span></span> <span data-ttu-id="8397b-881">cert_id を使用する場合は、common_name に NX_NULL を値として渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8397b-881">If cert_id is used, common_name should be passed a value of NX_NULL.</span></span>

<span data-ttu-id="8397b-882">cert_id パラメーターは、証明書の 0 以外の数値の識別子です。</span><span class="sxs-lookup"><span data-stu-id="8397b-882">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="8397b-883">これにより、DTLS 証明書ストアに同じ X.509 の共通名を持つ複数の ID 証明書がある場合に、証明書を簡単に削除したり、見つけたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="8397b-883">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="8397b-884">X.509 証明書の詳細については、『NetX Secure TLS ユーザー ガイド』を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8397b-884">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="8397b-885">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8397b-885">Parameters</span></span>

- <span data-ttu-id="8397b-886">**session_ptr** 以前に作成された DTLS Session インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-886">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="8397b-887">**common_name** 照合する CommonName 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8397b-887">**common_name** Pointer to the CommonName string to match.</span></span>
- <span data-ttu-id="8397b-888">**common_name_length** common_name 文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="8397b-888">**common_name_length** Length of the common_name string.</span></span>
- <span data-ttu-id="8397b-889">**cert_id** この DTLS サーバー内のこの証明書に対する 0 以外の数値の一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="8397b-889">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>


### <a name="return-values"></a><span data-ttu-id="8397b-890">戻り値</span><span class="sxs-lookup"><span data-stu-id="8397b-890">Return Values</span></span>

- <span data-ttu-id="8397b-891">**NX_SUCCESS** (0x00) DTLS セッションから証明書が正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-891">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS session.</span></span>
- <span data-ttu-id="8397b-892">**NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。</span><span class="sxs-lookup"><span data-stu-id="8397b-892">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="8397b-893">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) 指定された DTLS セッションで cert_id または common_name に一致する証明書が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="8397b-893">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8397b-894">許可元</span><span class="sxs-lookup"><span data-stu-id="8397b-894">Allowed From</span></span>

<span data-ttu-id="8397b-895">Threads</span><span class="sxs-lookup"><span data-stu-id="8397b-895">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8397b-896">例</span><span class="sxs-lookup"><span data-stu-id="8397b-896">Example</span></span>

<span data-ttu-id="8397b-897">*より完全な例については、*nx_secure_dtls_session_create\* のリファレンスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8397b-897">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL, 0,
                                    NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
    status = nx_secure_dtls_session_trusted_certificate_remove(&client_dtls_session,
                                                                    NX_NULL, 0, 1);
}

```

### <a name="see-also"></a><span data-ttu-id="8397b-898">参照</span><span class="sxs-lookup"><span data-stu-id="8397b-898">See Also</span></span>

- <span data-ttu-id="8397b-899">nx_secure_dtls_session_create、nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="8397b-899">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="8397b-900">nx_secure_dtls_session_send、nx_secure_dtls_session_start</span><span class="sxs-lookup"><span data-stu-id="8397b-900">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="8397b-901">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="8397b-901">nx_secure_dtls_session_trusted_certificate_add,</span></span>
- <span data-ttu-id="8397b-902">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="8397b-902">nx_secure_x509_certificate_initialize</span></span>
