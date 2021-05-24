---
title: 第 4 章 - Azure RTOS NetX Secure サービスの説明
description: この章では、すべての NetX Secure サービス （以下に記載） をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 80ec22058ab64ed0c6258bb3d9364ec44f9a741b
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223394"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a><span data-ttu-id="f21e6-103">第 4 章 - Azure RTOS NetX Secure サービスの説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-103">Chapter 4 - Description of Azure RTOS NetX Secure services</span></span>

<span data-ttu-id="f21e6-104">この章では、すべての Azure RTOS NetX Secure サービス （以下に記載） をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-104">This chapter contains a description of all Azure RTOS NetX Secure services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="f21e6-105">次の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にする際に使用される **NX_SECURE_DISABLE_ERROR_CHECKING** マクロの影響を受けません。一方、太字以外の値は完全に無効になっています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_SECURE_DISABLE_ERROR_CHECKING** macro that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="f21e6-106">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="f21e6-106">nx_secure_crypto_table_self_test</span></span>](#nx_secure_crypto_table_self_test)
  - <span data-ttu-id="f21e6-107">暗号化メソッドで自己テストを実行します</span><span class="sxs-lookup"><span data-stu-id="f21e6-107">Perform self_test on the crypto methods</span></span>
- [<span data-ttu-id="f21e6-108">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="f21e6-108">nx_secure_module_hash_compute</span></span>](#nx_secure_module_hash_compute)
  - <span data-ttu-id="f21e6-109">user_supplied ハッシュ関数を使用してハッシュ値を計算します</span><span class="sxs-lookup"><span data-stu-id="f21e6-109">Computes hash value using user_supplied hash function</span></span>
- [<span data-ttu-id="f21e6-110">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-110">nx_secure_tls_active_certificate_set</span></span>](#nx_secure_tls_active_certificate_set)
  - <span data-ttu-id="f21e6-111">NetX Secure TLS セッションに対してアクティブな ID 証明書を設定します</span><span class="sxs-lookup"><span data-stu-id="f21e6-111">Set the active identity certificate for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-112">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-112">nx_secure_tls_client_psk_set</span></span>](#nx_secure_tls_client_psk_set)
  - <span data-ttu-id="f21e6-113">NetX Secure TLS クライアント セッションに対して事前共有キーを設定します</span><span class="sxs-lookup"><span data-stu-id="f21e6-113">Set a Pre_Shared Key for a NetX Secure TLS Client Session</span></span>
- [<span data-ttu-id="f21e6-114">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-114">nx_secure_tls_initialize</span></span>](#nx_secure_tls_initialize)
  - <span data-ttu-id="f21e6-115">NetX Secure TLS モジュールを初期化します</span><span class="sxs-lookup"><span data-stu-id="f21e6-115">Initializes the NetX Secure TLS module]</span></span>
- [<span data-ttu-id="f21e6-116">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-116">nx_secure_tls_local_certificate_add</span></span>](#nx_secure_tls_local_certificate_add)
  - <span data-ttu-id="f21e6-117">NetX Secure TLS セッションにローカル証明書を追加します</span><span class="sxs-lookup"><span data-stu-id="f21e6-117">Add a local certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-118">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="f21e6-118">nx_secure_tls_local_certificate_find</span></span>](#nx_secure_tls_local_certificate_find)
  - <span data-ttu-id="f21e6-119">NetX Secure TLS セッション内で共通名によってローカル証明書を検索します</span><span class="sxs-lookup"><span data-stu-id="f21e6-119">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>
- [<span data-ttu-id="f21e6-120">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="f21e6-120">nx_secure_tls_local_certificate_remove</span></span>](#nx_secure_tls_local_certificate_remove)
  - <span data-ttu-id="f21e6-121">NetX Secure TLS セッションからローカル証明書を削除します</span><span class="sxs-lookup"><span data-stu-id="f21e6-121">Remove local certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-122">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="f21e6-122">nx_secure_tls_metadata_size_calculate</span></span>](#nx_secure_tls_metadata_size_calculate)
  - <span data-ttu-id="f21e6-123">NetX Secure TLS セッション用の暗号化メタデータのサイズを計算します</span><span class="sxs-lookup"><span data-stu-id="f21e6-123">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-124">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-124">nx_secure_tls_packet_allocate</span></span>](#nx_secure_tls_packet_allocate)
  - <span data-ttu-id="f21e6-125">NetX Secure TLS セッション用のパケットを割り当てます</span><span class="sxs-lookup"><span data-stu-id="f21e6-125">Allocate a packet for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-126">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-126">nx_secure_tls_psk_add</span></span>](#nx_secure_tls_psk_add)
  - <span data-ttu-id="f21e6-127">NetX Secure TLS セッションに事前共有キーを追加します</span><span class="sxs-lookup"><span data-stu-id="f21e6-127">Add a Pre_Shared Key to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-128">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-128">nx_secure_tls_remote_certificate_allocate</span></span>](#nx_secure_tls_remote_certificate_allocate)
  - <span data-ttu-id="f21e6-129">リモート TLS ホストによって提供された証明書用の領域を割り当てます</span><span class="sxs-lookup"><span data-stu-id="f21e6-129">Allocate space for the certificate provided by a remote TLS host</span></span>
- [<span data-ttu-id="f21e6-130">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-130">nx_secure_tls_remote_certificate_buffer_allocate</span></span>](#nx_secure_tls_remote_certificate_buffer_allocate)
  - <span data-ttu-id="f21e6-131">リモート TLS ホストによって提供されたすべての証明書用の領域を割り当てます</span><span class="sxs-lookup"><span data-stu-id="f21e6-131">Allocate space for all certificates provided by a remote TLS host</span></span>
- [<span data-ttu-id="f21e6-132">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="f21e6-132">nx_secure_tls_remote_certificate_free_all</span></span>](#nx_secure_tls_remote_certificate_free_all)
  - <span data-ttu-id="f21e6-133">受信証明書用に割り当てられた領域を解放します</span><span class="sxs-lookup"><span data-stu-id="f21e6-133">Free space allocated for incoming certificates</span></span>
- [<span data-ttu-id="f21e6-134">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-134">nx_secure_tls_server_certificate_add</span></span>](#nx_secure_tls_server_certificate_add)
  - <span data-ttu-id="f21e6-135">数値識別子を使用して TLS サーバー専用の証明書を追加します</span><span class="sxs-lookup"><span data-stu-id="f21e6-135">Add a certificate specifically for TLS servers using a numeric identifier</span></span>
- [<span data-ttu-id="f21e6-136">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="f21e6-136">nx_secure_tls_server_certificate_find</span></span>](#nx_secure_tls_server_certificate_find)
  - <span data-ttu-id="f21e6-137">数値識別子を使用して証明書を検索します</span><span class="sxs-lookup"><span data-stu-id="f21e6-137">Find a certificate using a numeric identifier</span></span>
- [<span data-ttu-id="f21e6-138">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="f21e6-138">nx_secure_tls_server_certificate_remove</span></span>](#nx_secure_tls_server_certificate_remove)
  - <span data-ttu-id="f21e6-139">数値識別子を使用してローカル サーバー証明書を削除します</span><span class="sxs-lookup"><span data-stu-id="f21e6-139">Remove a local server certificate using a numeric identifier</span></span>
- [<span data-ttu-id="f21e6-140">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-140">nx_secure_tls_session_certificate_callback_set</span></span>](#nx_secure_tls_session_certificate_callback_set)
  - <span data-ttu-id="f21e6-141">追加の証明書検証に使用する TLS 用のコールバックを設定します</span><span class="sxs-lookup"><span data-stu-id="f21e6-141">Set up a callback for TLS to use for additional certificate validation</span></span>
- [<span data-ttu-id="f21e6-142">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-142">nx_secure_tls_session_client_callback_set</span></span>](#nx_secure_tls_session_client_callback_set)
  - <span data-ttu-id="f21e6-143">TLS クライアント ハンドシェイクの開始時に呼び出す TLS 用のコールバックを設定します</span><span class="sxs-lookup"><span data-stu-id="f21e6-143">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>
- [<span data-ttu-id="f21e6-144">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="f21e6-144">nx_secure_tls_session_x509_client_verify_configure</span></span>](#nx_secure_tls_session_x509_client_verify_configure)
  - <span data-ttu-id="f21e6-145">クライアント X.509 検証を有効にし、クライアント証明書用の領域を割り当てます</span><span class="sxs-lookup"><span data-stu-id="f21e6-145">Enable client X.509 verification and allocate space for client certificates</span></span>
- [<span data-ttu-id="f21e6-146">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="f21e6-146">nx_secure_tls_session_client_verify_disable</span></span>](#nx_secure_tls_session_client_verify_disable)
  - <span data-ttu-id="f21e6-147">NetX Secure TLS セッション用のクライアント証明書認証を無効にします</span><span class="sxs-lookup"><span data-stu-id="f21e6-147">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-148">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="f21e6-148">nx_secure_tls_session_client_verify_enable</span></span>](#nx_secure_tls_session_client_verify_enable)
  - <span data-ttu-id="f21e6-149">NetX Secure TLS セッション用のクライアント証明書認証を有効にします</span><span class="sxs-lookup"><span data-stu-id="f21e6-149">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-150">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-150">nx_secure_tls_session_create</span></span>](#nx_secure_tls_session_create)
  - <span data-ttu-id="f21e6-151">セキュリティで保護された通信用の NetX Secure TLS セッションを作成します</span><span class="sxs-lookup"><span data-stu-id="f21e6-151">Create a NetX Secure TLS Session for secure communications</span></span>
- [<span data-ttu-id="f21e6-152">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="f21e6-152">nx_secure_tls_session_delete</span></span>](#nx_secure_tls_session_delete)
  - <span data-ttu-id="f21e6-153">NetX Secure TLS セッションを削除します</span><span class="sxs-lookup"><span data-stu-id="f21e6-153">Delete a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-154">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="f21e6-154">nx_secure_tls_session_end</span></span>](#nx_secure_tls_session_end)
  - <span data-ttu-id="f21e6-155">アクティブな NetX Secure TLS セッションを終了します</span><span class="sxs-lookup"><span data-stu-id="f21e6-155">End an active NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-156">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-156">nx_secure_tls_session_packet_buffer_set</span></span>](#nx_secure_tls_session_packet_buffer_set)
  - <span data-ttu-id="f21e6-157">NetX Secure TLS セッション用のパケット再構築バッファーを設定します</span><span class="sxs-lookup"><span data-stu-id="f21e6-157">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-158">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="f21e6-158">nx_secure_tls_session_protocol_version_override</span></span>](#nx_secure_tls_session_protocol_version_override)
  - <span data-ttu-id="f21e6-159">NetX Secure TLS セッション用の既定の TLS プロトコル バージョンをオーバーライドします</span><span class="sxs-lookup"><span data-stu-id="f21e6-159">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-160">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-160">nx_secure_tls_session_receive</span></span>](#nx_secure_tls_session_receive)
  - <span data-ttu-id="f21e6-161">NetX Secure TLS セッションからデータを受信します</span><span class="sxs-lookup"><span data-stu-id="f21e6-161">Receive data from a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-162">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-162">nx_secure_tls_session_renegotiate_callback_set</span></span>](#nx_secure_tls_session_renegotiate_callback_set)
  - <span data-ttu-id="f21e6-163">セッションの再ネゴシエーションの開始時に呼び出されるコールバックを割り当てます</span><span class="sxs-lookup"><span data-stu-id="f21e6-163">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>
- [<span data-ttu-id="f21e6-164">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="f21e6-164">nx_secure_tls_session_renegotiate</span></span>](#nx_secure_tls_session_renegotiate)
  - <span data-ttu-id="f21e6-165">リモート ホストでセッション再ネゴシエーション ハンドシェイクを開始します</span><span class="sxs-lookup"><span data-stu-id="f21e6-165">Initiate a session renegotiation handshake with the remote host</span></span>
- [<span data-ttu-id="f21e6-166">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="f21e6-166">nx_secure_tls_session_reset</span></span>](#nx_secure_tls_session_reset)
  - <span data-ttu-id="f21e6-167">NetX Secure TLS セッションのクリアし、リセットします</span><span class="sxs-lookup"><span data-stu-id="f21e6-167">Clear out and reset a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-168">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="f21e6-168">nx_secure_tls_session_send</span></span>](#nx_secure_tls_session_send)
  - <span data-ttu-id="f21e6-169">NetX Secure TLS セッションを介してデータを送信します</span><span class="sxs-lookup"><span data-stu-id="f21e6-169">Send data through a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-170">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-170">nx_secure_tls_session_server_callback_set</span></span>](#nx_secure_tls_session_server_callback_set)
  - <span data-ttu-id="f21e6-171">TLS サーバー ハンドシェイクの開始時に呼び出す TLS 用のコールバックを設定します</span><span class="sxs-lookup"><span data-stu-id="f21e6-171">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>
- [<span data-ttu-id="f21e6-172">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="f21e6-172">nx_secure_tls_session_sni_extension_parse</span></span>](#nx_secure_tls_session_sni_extension_parse)
  - <span data-ttu-id="f21e6-173">TLS クライアントから受信した Server Name Indication （SNI） 拡張機能を解析します</span><span class="sxs-lookup"><span data-stu-id="f21e6-173">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>
- [<span data-ttu-id="f21e6-174">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-174">nx_secure_tls_session_sni_extension_set</span></span>](#nx_secure_tls_session_sni_extension_set)
  - <span data-ttu-id="f21e6-175">リモートサーバーに送信する Server Name Indication （SNI） 拡張機能の DNS 名を設定します</span><span class="sxs-lookup"><span data-stu-id="f21e6-175">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>
- [<span data-ttu-id="f21e6-176">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-176">nx_secure_tls_session_start</span></span>](#nx_secure_tls_session_start)
  - <span data-ttu-id="f21e6-177">NetX Secure TLS セッションを開始します</span><span class="sxs-lookup"><span data-stu-id="f21e6-177">Start a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-178">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-178">nx_secure_tls_session_time_function_set</span></span>](#nx_secure_tls_session_time_function_set)
  - <span data-ttu-id="f21e6-179">NetX Secure TLS セッションにタイムスタンプ関数を割り当てます</span><span class="sxs-lookup"><span data-stu-id="f21e6-179">Assign a timestamp function to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-180">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-180">nx_secure_tls_trusted_certificate_add</span></span>](#nx_secure_tls_trusted_certificate_add)
  - <span data-ttu-id="f21e6-181">信頼された証明書を NetX Secure TLS セッションに追加します</span><span class="sxs-lookup"><span data-stu-id="f21e6-181">Add trusted certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-182">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="f21e6-182">nx_secure_tls_trusted_certificate_remove</span></span>](#nx_secure_tls_trusted_certificate_remove)
  - <span data-ttu-id="f21e6-183">信頼された証明書を NetX Secure TLS セッションから削除します</span><span class="sxs-lookup"><span data-stu-id="f21e6-183">Remove trusted certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="f21e6-184">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-184">nx_secure_x509_certificate_initialize</span></span>](#nx_secure_x509_certificate_initialize)
  - <span data-ttu-id="f21e6-185">NetX Secure TLS 用の X.509 証明書を初期化します</span><span class="sxs-lookup"><span data-stu-id="f21e6-185">Initialize X.509 Certificate for NetX Secure TLS</span></span>
- [<span data-ttu-id="f21e6-186">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="f21e6-186">nx_secure_x509_common_name_dns_check</span></span>](#nx_secure_x509_common_name_dns_check)
  - <span data-ttu-id="f21e6-187">DNS 名を X.509 証明書と照合して確認します</span><span class="sxs-lookup"><span data-stu-id="f21e6-187">Check DNS name against X.509 Certificate</span></span>
- [<span data-ttu-id="f21e6-188">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="f21e6-188">nx_secure_x509_crl_revocation_check</span></span>](#nx_secure_x509_crl_revocation_check)
  - <span data-ttu-id="f21e6-189">X.509 証明書を指定された証明書失効リスト （CRL） と照合して確認します</span><span class="sxs-lookup"><span data-stu-id="f21e6-189">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)]</span></span>
- [<span data-ttu-id="f21e6-190">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-190">nx_secure_x509_dns_name_initialize</span></span>](#nx_secure_x509_dns_name_initialize)
  - <span data-ttu-id="f21e6-191">X.509 DNS 名の構造体を初期化します</span><span class="sxs-lookup"><span data-stu-id="f21e6-191">Initialize an X.509 DNS name structure</span></span>
- [<span data-ttu-id="f21e6-192">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="f21e6-192">nx_secure_x509_extended_key_usage_extension_parse</span></span>](#nx_secure_x509_extended_key_usage_extension_parse)
  - <span data-ttu-id="f21e6-193">X.509 証明書内で X.509 拡張キー使用拡張機能を検索して解析します</span><span class="sxs-lookup"><span data-stu-id="f21e6-193">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>
- [<span data-ttu-id="f21e6-194">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="f21e6-194">nx_secure_x509_extension_find</span></span>](#nx_secure_x509_extension_find)
  - <span data-ttu-id="f21e6-195">X.509 証明書内で X.509 拡張機能を検索して返します</span><span class="sxs-lookup"><span data-stu-id="f21e6-195">Find and return an X.509 extension in an X.509 certificate</span></span>
- [<span data-ttu-id="f21e6-196">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="f21e6-196">nx_secure_x509_key_usage_extension_parse</span></span>](#nx_secure_x509_key_usage_extension_parse)
  - <span data-ttu-id="f21e6-197">X.509 証明書内で X.509 キー使用法拡張機能を検索して解析します</span><span class="sxs-lookup"><span data-stu-id="f21e6-197">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

## <a name="nx_secure_crypto_table_self_test"></a><span data-ttu-id="f21e6-198">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="f21e6-198">nx_secure_crypto_table_self_test</span></span>

<span data-ttu-id="f21e6-199">暗号化メソッドで自己テストを実行します</span><span class="sxs-lookup"><span data-stu-id="f21e6-199">Perform self-test on the crypto methods</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-200">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-200">Prototype</span></span>

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a><span data-ttu-id="f21e6-201">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-201">Description</span></span>

<span data-ttu-id="f21e6-202">このサービスは、検証する暗号化メソッドの自己テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-202">This service runs through the crypto method self tests to validate.</span></span> <span data-ttu-id="f21e6-203">自己テストは、シンボル NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK が定義された状態で、NetX Secure ライブラリが構築されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-203">The self test is available only if NetX Secure library is built with the symbol NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK defined.</span></span>

<span data-ttu-id="f21e6-204">自己テストは、サポートされている暗号化メソッドごとに、事前定義された入力データを提供し、出力が、その事前定義された期待値と一致することを確認します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-204">For each supported crypto method, the self test provides pre-defined input data, and verified the output matches the pre-defined expected value.</span></span>

<span data-ttu-id="f21e6-205">NetX Secure 暗号化自己テストは、次のアルゴリズムとキー サイズをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-205">NetX Secure crypto self test supports the following algorithms and key sizes:</span></span>

- <span data-ttu-id="f21e6-206">DES: 暗号化と解読</span><span class="sxs-lookup"><span data-stu-id="f21e6-206">DES: encryption and decryption</span></span>
- <span data-ttu-id="f21e6-207">Triple DES （3DES）: 暗号化と解読</span><span class="sxs-lookup"><span data-stu-id="f21e6-207">Triple DES (3DES): encryption and decryption</span></span>
- <span data-ttu-id="f21e6-208">AES: CBC モードおよびカウンター モードでの 128 ビット、192 ビット、256 ビットのキー サイズ、暗号化と解読。</span><span class="sxs-lookup"><span data-stu-id="f21e6-208">AES: 128-, 192-, 256-bit key size, encryption and decryption, in CBC mode and counter mode.</span></span>
- <span data-ttu-id="f21e6-209">HMAC-MD5: 認証とハッシュ計算</span><span class="sxs-lookup"><span data-stu-id="f21e6-209">HMAC-MD5: authentication and hash computation</span></span>
- <span data-ttu-id="f21e6-210">HMAC-SHA: SHA1-96、SHA1-160、SHA2-256、SHA2-384、SHA2- 512、認証とハッシュ計算</span><span class="sxs-lookup"><span data-stu-id="f21e6-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2- 512, authentication and hash computation</span></span>
- <span data-ttu-id="f21e6-211">MD5: 認証</span><span class="sxs-lookup"><span data-stu-id="f21e6-211">MD5: authentication</span></span>
- <span data-ttu-id="f21e6-212">擬似乱数関数 （PRF）: PRF_HMAC_SHA1 および PRF_HMAC_SHA2-256</span><span class="sxs-lookup"><span data-stu-id="f21e6-212">Pseudo-random Function (PRF): PRF_HMAC_SHA1 and PRF_HMAC_SHA2-256</span></span>
- <span data-ttu-id="f21e6-213">RSA: 1024 ビット、2048 ビット、4096 ビットの RSA 累乗剰余演算</span><span class="sxs-lookup"><span data-stu-id="f21e6-213">RSA: 1024-, 2048-, 4096-bit RSA power-modulus operation</span></span>
- <span data-ttu-id="f21e6-214">SHA: SHA1 （96 ビットおよび 160 ビット）、SHA2 （256 ビット、384 ビット、512 ビット） 認証</span><span class="sxs-lookup"><span data-stu-id="f21e6-214">SHA: SHA1 (96- and 160-bit), SHA2 (256bit, 384bit, 512bit) authentication</span></span>

<span data-ttu-id="f21e6-215">この関数には、上に示した暗号アルゴリズム用の組み込みベクターがあります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-215">This function has the built-in vectors for the crypto algorithms listed above.</span></span> <span data-ttu-id="f21e6-216">ただし、テスト対象は、この関数に渡される *cipher_table* 内に示されているものだけです。</span><span class="sxs-lookup"><span data-stu-id="f21e6-216">However it only tests the ones listed in the *cipher_table* passed into this function.</span></span> <span data-ttu-id="f21e6-217">たとえば、暗号スイート TLS_RSA_WITH_AES_128_CBC_SHA のみが使用される TLS セッションの場合、この関数は、RSA （1024 ビット、2048 ビット、4096 ビット）、AES-CBC （128 ビット）、および SHA1 上で自己テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-217">For example, for a TLS session uses only the ciphersuite TLS_RSA_WITH_AES_128_CBC_SHA, this function will perform self test on the RSA (1024-, 2048-, 4096-bit), AES-CBC (128-bit) and SHA1.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-218">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-218">Parameters</span></span>

- <span data-ttu-id="f21e6-219">**crypto_table** TLS セッションによって使用されている暗号化テーブルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-219">**crypto_table** Pointer to the crypto table being used by the TLS session.</span></span> <span data-ttu-id="f21e6-220">これは **_nx_secure_tls_session_create （）_** 呼び出しに渡される crypto_table と同じです。</span><span class="sxs-lookup"><span data-stu-id="f21e6-220">This is the same crypto_table being passed into the **_nx_secure_tls_session_create()_** call.</span></span>
- <span data-ttu-id="f21e6-221">**metadata** 暗号メタデータ領域用のスペースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-221">**metadata** Pointer to space for cryptography metadata area.</span></span> <span data-ttu-id="f21e6-222">.</span><span class="sxs-lookup"><span data-stu-id="f21e6-222">.</span></span>
- <span data-ttu-id="f21e6-223">**metadata_size** メタデータ バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-223">**metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-224">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-224">Return Values</span></span>

- <span data-ttu-id="f21e6-225">**NX_SECURE_TLS_SUCCESS** （0x00） 指定された暗号化メソッドを正常にテストしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-225">**NX_SECURE_TLS_SUCCESS** (0x00) Successfully tested the crypto methods provided.</span></span>
- <span data-ttu-id="f21e6-226">**NX_PTR_ERROR** （0x07） 無効な暗号化メソッド構造体</span><span class="sxs-lookup"><span data-stu-id="f21e6-226">**NX_PTR_ERROR** (0x07) Invalid crypto method structure</span></span>
- <span data-ttu-id="f21e6-227">**NX_NOT_SUCCESSFUL** （0x43） 暗号化自己テストに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-227">**NX_NOT_SUCCESSFUL** (0x43) Crypto self test fails.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-228">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-228">Allowed From</span></span>

<span data-ttu-id="f21e6-229">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="f21e6-229">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-230">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-230">Example</span></span>

```C
/* crypto_tls_ciphers is the cipher table for the TLS session. */
/* metadata_buffer is the memory area used by the cipher functions. */

/* The following function verifies the supplied ciphersuties using the built-in
   self test. */

if (nx_secure_crypto_table_self_test(&crypto_tls_ciphers, metadata_buffer,
    sizeof(metadata_buffer)))
{
    printf("Crypto self test failed!\r\n");
    exit(0);
}
else
{
    printf("Crypto self test succeed!\r\n");
}

/* Now the ciphersuites are successfully test, it can be used in
   nx_secure_tls_session_create() */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-231">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-231">See Also</span></span>

- <span data-ttu-id="f21e6-232">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-232">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_module_hash_compute"></a><span data-ttu-id="f21e6-233">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="f21e6-233">nx_secure_module_hash_compute</span></span>

<span data-ttu-id="f21e6-234">user-supplied ハッシュ関数を使用してハッシュ値を計算します</span><span class="sxs-lookup"><span data-stu-id="f21e6-234">Computes hash value using user-supplied hash function</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-235">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-235">Prototype</span></span>

```C
UINT nx_secure_module_hash_compute(
                      NX_CRYPTO_METHOD *hamc_ptr,
                      UINT start_address, UINT end_address,
                      UCHAR *key, UINT key_length,
                      VOID *metadata, UINT metadata_size,
                      UCHAR *output_buffer, UINT output_buffer_size,
                      UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="f21e6-236">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-236">Description</span></span>

<span data-ttu-id="f21e6-237">この関数は、指定された HMAC 暗号化メソッドとキー文字列を使用して、指定されたメモリ領域内のデータ ストリームのハッシュ値を計算します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-237">This function computes the hash value of the data stream in the specified memory area, using supplied HMAC crypto method and the key string.</span></span> <span data-ttu-id="f21e6-238">モジュール ハッシュ計算関数は、シンボル NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK が定義された状態で、NetX Secure ライブラリが構築されている場合にのみ使用できます</span><span class="sxs-lookup"><span data-stu-id="f21e6-238">The module hash compute function is available only if NetX Secure library is built with the following symbol being defined: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-239">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-239">Parameters</span></span>

- <span data-ttu-id="f21e6-240">**hmac_ptr** ハッシュ値の計算に使用されている HMAC 暗号化メソッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-240">**hmac_ptr** Pointer to the HMAC crypto method being used for the hash value computation.</span></span>
- <span data-ttu-id="f21e6-241">**start_address** データ バッファーの開始アドレス</span><span class="sxs-lookup"><span data-stu-id="f21e6-241">**start_address** The starting address of the data buffer</span></span>
- <span data-ttu-id="f21e6-242">**end_address** データ バッファーの終了アドレス。</span><span class="sxs-lookup"><span data-stu-id="f21e6-242">**end_address** The ending address of the data buffer.</span></span> <span data-ttu-id="f21e6-243">ハッシュ計算は、この end_address のデータに対応していないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f21e6-243">Note that hash computation does not cover the data at this end_address.</span></span>
- <span data-ttu-id="f21e6-244">**key** HMAC 計算内で使用されているキー文字列。</span><span class="sxs-lookup"><span data-stu-id="f21e6-244">**key** The key string being used in the HMAC computation.</span></span>
- <span data-ttu-id="f21e6-245">**key_length** キー文字列のサイズ （バイト単位）</span><span class="sxs-lookup"><span data-stu-id="f21e6-245">**key_length** The size of the key string, in bytes</span></span>
- <span data-ttu-id="f21e6-246">**metadata** HMAC アルゴリズムによって使用されている領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-246">**metadata** Pointer to space used by the HMAC algorithm.</span></span>
- <span data-ttu-id="f21e6-247">**metadata_size** メタデータ バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-247">**metadata_size** Size of the metadata buffer.</span></span>
- <span data-ttu-id="f21e6-248">**output_buffer** ハッシュ出力が格納されているメモリ位置。</span><span class="sxs-lookup"><span data-stu-id="f21e6-248">**output_buffer** The memory location where the hash output is being stored at.</span></span>
- <span data-ttu-id="f21e6-249">**output_buffer_size** 出力バッファーの使用可能な領域 （バイト単位）</span><span class="sxs-lookup"><span data-stu-id="f21e6-249">**output_buffer_size** The available space of the output buffer, in bytes</span></span>
- <span data-ttu-id="f21e6-250">**actual_size** output_buffer に書き込まれている実際のバイト数を示す関数によって返されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-250">**actual_size** Returned by the function indicating the actual number of bytes being written into the output_buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-251">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-251">Return Values</span></span>

- <span data-ttu-id="f21e6-252">**0** ハッシュ値が正常に計算されました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-252">**0** Successfully computed the hash value.</span></span>
- <span data-ttu-id="f21e6-253">**1** ハッシュ計算が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-253">**1** The hash computation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-254">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-254">Allowed From</span></span>

<span data-ttu-id="f21e6-255">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="f21e6-255">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-256">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-256">Example</span></span>

```C
/* Define the HMAC SHA256 method */
NX_CRYPTO_METHOD hmac_sha256 =
{
    NX_CRYPTO_AUTHENTICATION_HMAC_SHA2_256,    /* HMAC SHA256 algorithm  */
    0,                                         /* Key size, not used     */
    0,                                         /* IV size, not used      */
    NX_CRYPTO_HMAC_SHA256_ICV_FULL_LEN_IN_BITS,/* Transmitted ICV size   */
    NX_CRYPTO_SHA2_BLOCK_SIZE_IN_BYTES,        /* Block size in bytes    */
    sizeof(NX_CRYPTO_SHA256_HMAC),             /* Metadata size in bytes */
    _nx_crypto_method_hmac_sha256_init,        /* HMAC SHA256 init       */
    _nx_crypto_method_hmac_sha256_cleanup,     /* HMAC SHA256 cleanup    */
    _nx_crypto_method_hmac_sha256_operation    /* HMAC SHA256 operation  */
};

/* Define the hash key being used. */
const CHAR hash_key = “my hash key”;

/* Define starting address. */
UINT starting_address = 0x10000;

/* Define the ending address.
   Note that the hash computation covers the memory location
   before the ending address. */
UINT ending_address = 0x11000;

/* Declare the output buffer. */
#define OUTPUT_BUFFER_SIZE
UCHAR output_buffer[OUTPUT_BUFFER_SIZE];

UINT actual_size;

/* Declare 1K bytes of metadata buffer area. */
UCHAR metadata_buffer[1024];

/* Compute the hash value of the data between 0x10000 – 0x10FFF */
nx_secure_module_hash_compute(&hmac_sha256,
                              starting_address, ending_address,
                              hash_key, strlen(hash_key),
                              metadata_buffer, sizeof(metadata_buffer),
                              output_buffer, OUTPUT_BUFFER_SIZE, &actual_size);

/* If this function returns “0”, the hash value has been computed and is stored
   in output_buffer. */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-257">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-257">See Also</span></span>

- <span data-ttu-id="f21e6-258">nx_secure_crypto_method_self_test</span><span class="sxs-lookup"><span data-stu-id="f21e6-258">nx_secure_crypto_method_self_test</span></span>

## <a name="nx_secure_tls_active_certificate_set"></a><span data-ttu-id="f21e6-259">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-259">nx_secure_tls_active_certificate_set</span></span>

<span data-ttu-id="f21e6-260">NetX Secure TLS セッションに対してアクティブな ID 証明書を設定します</span><span class="sxs-lookup"><span data-stu-id="f21e6-260">Set the active identity certificate for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-261">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-261">Prototype</span></span>

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="f21e6-262">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-262">Description</span></span>

<span data-ttu-id="f21e6-263">このサービスは、セッション コールバック内から呼び出されるように意図されています （nx_secure_tls_session_client_callback_set　および　nx_secure_tls_session_server_callback_set　をご覧ください）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-263">This service is intended to be called from within a session callback (see nx_secure_tls_session_client_callback_set and nx_secure_tls_session_server_callback_set).</span></span> <span data-ttu-id="f21e6-264">前に初期化された NX_SECURE_X509_CERT 構造体を使って呼び出されたときは、既定の ID 証明書ではなく、その証明書が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-264">When called with a previously-initialized NX_SECURE_X509_CERT structure, that certificate will be used instead of the default identity certificate.</span></span> <span data-ttu-id="f21e6-265">ほとんどの場合、証明書はローカル ストアに追加されている必要があります （nx_secure_tls_local_certificate_add をご覧ください）。そうでない場合、TLS ハンドシェイクは失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-265">In most cases, the certificate must have been added to the local store (see nx_secure_tls_local_certificate_add) or the TLS handshake may fail.</span></span>

<span data-ttu-id="f21e6-266">このサービスは、TLS が複数の ID 証明書をサポートできるようにすることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-266">This service is intended to allow TLS to support multiple identity certificates.</span></span> <span data-ttu-id="f21e6-267">これは、複数のネットワーク アドレスにサービスを提供する TLS サーバーにとって便利な機能で、サーバーは、クライアントのエントリポイントに応じて、適切な証明書を選択してリモート クライアントに提供することができます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-267">This is useful for a TLS server that services multiple network addresses so the server can pick an appropriate certificate to provide to the remote client depending on the client's entrypoint.</span></span> <span data-ttu-id="f21e6-268">TLS クライアントの場合は、サーバーが TLS ハンドシェイク内で自身を特定した後に、このルーチンを使用して、実行時にリモート サーバーに送信された証明書を変更できます （これは TLS サーバーの使用例よりもまれです）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-268">For a TLS client, this routine may be used to change the certificate sent to a remote server at runtime after the server has identified itself in the TLS handshake (this is more rare than the TLS server use-case).</span></span>

<span data-ttu-id="f21e6-269">複数の証明書が同じ X.509 識別名を共有している可能性がある場合は、nx_secure_tls_server_certificate_add を使用して、証明書を追加する必要があります。これにより、証明書とは別に数値の識別子が導入されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-269">In the case where multiple certificates may share the same X.509 distinguished name, certificates will need to be added using nx_secure_tls_server_certificate_add, which introduces a numeric identifier separate from the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-270">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-270">Parameters</span></span>

- <span data-ttu-id="f21e6-271">**session_ptr** セッション コールバックに渡される TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-271">**session_ptr** Pointer to a TLS Session instance passed into the session callback.</span></span>
- <span data-ttu-id="f21e6-272">**certificate** 現在のセッションに使用される初期化済み X.509 証明書へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-272">**certificate** Pointer to an initialized X.509 certificate that is to be used for the current session.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-273">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-273">Return Values</span></span>

- <span data-ttu-id="f21e6-274">**NX_SUCCESS** （0x00） セッションへの証明書の割り当てに成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-274">**NX_SUCCESS** (0x00) Successful assignment of certificate to session.</span></span>
- <span data-ttu-id="f21e6-275">**NX_PTR_ERROR** （0x07） 無効な TLS セッションまたは証明書ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-275">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-276">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-276">Allowed From</span></span>

<span data-ttu-id="f21e6-277">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-278">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-278">Example</span></span>

```C
#define TLS_SNI_SERVER_NAME “www.example.com”
#define TLS_DEFAULT_SERVER_CERT_ID 2
#define TLS_EXAMPLE_CERT_ID 3


/* Callback for ClientHello extensions processing. */
static ULONG tls_server_callback(NX_SECURE_TLS_SESSION *tls_session,
                                 NX_SECURE_TLS_HELLO_EXTENSION *extensions,
                                 UINT num_extensions)
{
NX_SECURE_X509_DNS_NAME dns_name;
INT compare_value;
UINT status;
NX_SECURE_X509_CERT *cert_ptr;

    /* Grab a pointer to our default certificate in case the SNI extension is not
       available or the specified server name is unknown. */
    nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                     TLS_DEFAULT_SERVER_CERT_ID);


    /* Process Server Name Indication extension. */
    status = _nx_secure_tls_session_sni_extension_parse(tls_session, extensions,
                                                    num_extensions, &dns_name);

    /* If no extension found, that is OK. Use default certificate. */
    if(status == NX_SUCCESS)
    {
          /* SNI extension found, select an active certificate based on the server
             name. */

          /* Make sure our SNI name matches. */
          compare_value = memcmp(dns_name.nx_secure_x509_dns_name,
                                TLS_SNI_SERVER_NAME, strlen(TLS_SNI_SERVER_NAME));

          if(compare_value == 0 && dns_name.nx_secure_x509_dns_name_length !=
             strlen(TLS_SNI_SERVER_NAME))
          {
             /* Found a match, find the certificate we want to use. */
             _nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                                      TLS_EXAMPLE_CERT_ID);
          }
          else
          {
             /* No matching server name found. The application may choose to simply
                provide the default certificate (and probably resulting in an error
                in the remote client) or returning an error here to end the
                handshake. A user-defined non-zero error code will be sufficient –
                the error code will abort the TLS handshake and be returned to the
                caller that started the server. */
                return(0x500);
          }
      }
      else
      {
      }
      /* Set the certificate we want to use. */
      nx_secure_tls_active_certificate_set(tls_session, cert_ptr);

      /* Return success to continue TLS handshake. */
      return(NX_SUCCESS);
}

/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_TLS_SESSION server_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&server_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_tls_session_create: 0x%x\n", status);
    }

    /* Setup our packet reassembly buffer. See
       nx_secure_tls_session_packet_buffer_set for more information. */
    nx_secure_tls_session_packet_buffer_set(&server_tls_session,
                                      server_packet_buffer,
                                      sizeof(server_packet_buffer));


    /* Set callback for server TLS extension handling. */
    _nx_secure_tls_session_server_callback_set(&server_tls_session,
                                              tls_server_callback);

    /* Initialize our certificates – certificate data defined elsewhere. See
       section “Importing X.509 Certificates into NetX Secure” for more
       information. */
    nx_secure_x509_certificate_initialize(&default_certificate,
                                      default_cert_der,
                                      default _cert_der_len, NX_NULL, 0,
                                      default_cert_key_der,
                                      default_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &default_certificate,
                                         TLS_DEFAULT_SERVER_CERT_ID);

    /* Alternative identity certificate, needs to have a private key! */
    nx_secure_x509_certificate_initialize(&example_certificate,
                                      example_cert_der,
                                      example cert_der_len, NX_NULL, 0,
                                      example_cert_key_der,
                                      example_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &example_certificate,
                                         TLS_EXAMPLE_CERT_ID);

    /* Now we can start the TLS session as normal. */
       …
}
```

### <a name="see-also"></a><span data-ttu-id="f21e6-279">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-279">See Also</span></span>

- <span data-ttu-id="f21e6-280">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-280">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-281">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-281">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="f21e6-282">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-282">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="f21e6-283">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-283">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="f21e6-284">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-284">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="f21e6-285">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="f21e6-285">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="f21e6-286">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="f21e6-286">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_client_psk_set"></a><span data-ttu-id="f21e6-287">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-287">nx_secure_tls_client_psk_set</span></span>

<span data-ttu-id="f21e6-288">NetX Secure TLS クライアント セッションに対して事前共有キーを設定します</span><span class="sxs-lookup"><span data-stu-id="f21e6-288">Set a Pre-Shared Key for a NetX Secure TLS Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-289">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-289">Prototype</span></span>

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a><span data-ttu-id="f21e6-290">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-290">Description</span></span>

<span data-ttu-id="f21e6-291">このサービスは、事前共有キー （PSK）、その ID文字列、および ID ヒントを TLS セッション制御ブロックに追加し、その PSK が、それ以降の TLS クライアント接続内で使用されるように設定します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-291">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block, and sets that PSK to be used in subsequent TLS Client connections.</span></span> <span data-ttu-id="f21e6-292">PSK 暗号スイートが有効で、使用されている場合、PSK はデジタル証明書の代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-292">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

<span data-ttu-id="f21e6-293">この場合、PSK は、TLS クライアントが通信する特定のリモート TLS サーバーに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-293">In this case, the PSK is associated with a specific remote TLS Server with which the TLS Client wishes to communicate.</span></span> <span data-ttu-id="f21e6-294">この API を使用して設定された PSK は、次の TLS ハンドシェイク中にリモート TLS サーバー ホストに提供されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-294">The PSK set through this API will be provided to the remote TLS Server host during the next TLS handshake.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-295">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-295">Parameters</span></span>

- <span data-ttu-id="f21e6-296">**session_ptr** 前に作成した TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-296">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-297">**pre_shared_key** 実際の PSK 値。</span><span class="sxs-lookup"><span data-stu-id="f21e6-297">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="f21e6-298">**psk_length** PSK 値の長さ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-298">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="f21e6-299">**psk_identity** この PSK 値を識別するために使用される文字列。</span><span class="sxs-lookup"><span data-stu-id="f21e6-299">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="f21e6-300">**identity_length** PSK ID の長さ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-300">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="f21e6-301">**hint** TLS サーバー上のどの PSK グループから選択するかを示すために使用される文字列。</span><span class="sxs-lookup"><span data-stu-id="f21e6-301">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="f21e6-302">**hint_length** ヒントの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-302">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-303">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-303">Return Values</span></span>

- <span data-ttu-id="f21e6-304">**NX_SUCCESS** （0x00） PSK の追加に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-304">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="f21e6-305">**NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-305">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="f21e6-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** （0x125） 別の PSK を追加できません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-307">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-307">Allowed From</span></span>

<span data-ttu-id="f21e6-308">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-308">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-309">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-309">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_client_psk_set(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-310">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-310">See Also</span></span>

- <span data-ttu-id="f21e6-311">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-311">nx_secure_tls_psk_add</span></span>
- <span data-ttu-id="f21e6-312">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-312">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-313">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-313">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-314">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-314">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-315">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-315">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_initialize"></a><span data-ttu-id="f21e6-316">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-316">nx_secure_tls_initialize</span></span>

<span data-ttu-id="f21e6-317">NetX Secure TLS モジュールを初期化します</span><span class="sxs-lookup"><span data-stu-id="f21e6-317">Initializes the NetX Secure TLS module</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-318">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-318">Prototype</span></span>

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="f21e6-319">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-319">Description</span></span>

<span data-ttu-id="f21e6-320">このサービスは、NetX Secure TLS モジュールを初期化します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-320">This service initializes the NetX Secure TLS module.</span></span> <span data-ttu-id="f21e6-321">これは、他の NetX Secure サービスにアクセスする前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-321">It must be called before other NetX Secure services can be accessed.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-322">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-322">Parameters</span></span>

<span data-ttu-id="f21e6-323">None</span><span class="sxs-lookup"><span data-stu-id="f21e6-323">None</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-324">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-324">Return Values</span></span>

<span data-ttu-id="f21e6-325">なし</span><span class="sxs-lookup"><span data-stu-id="f21e6-325">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-326">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-326">Allowed From</span></span>

<span data-ttu-id="f21e6-327">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="f21e6-327">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-328">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-328">Example</span></span>

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a><span data-ttu-id="f21e6-329">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-329">See Also</span></span>

- <span data-ttu-id="f21e6-330">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-330">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_local_certificate_add"></a><span data-ttu-id="f21e6-331">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-331">nx_secure_tls_local_certificate_add</span></span>

<span data-ttu-id="f21e6-332">NetX Secure TLS セッションにローカル証明書を追加します</span><span class="sxs-lookup"><span data-stu-id="f21e6-332">Add a local certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-333">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-333">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="f21e6-334">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-334">Description</span></span>

<span data-ttu-id="f21e6-335">このサービスは、初期化された NX_SECURE_X509_CERT 構造体インスタンスを、TLS セッションのローカル ストアに追加します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-335">This service adds an initialized NX_SECURE_X509_CERT structure instance to the local store of a TLS session.</span></span> <span data-ttu-id="f21e6-336">この証明書は、TLS ハンドシェイク中、TLS スタックがデバイスを識別するために使用できます （nx_secure_x509_certificate_initialize を使用して証明書構造体を初期化中、ID 証明書としてマークされた場合）。または、発行者として、TLS ハンドシェイク中にリモート ホストに提供される証明書チェーンの一部として使用できます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-336">This certificate may used by the TLS stack to identify the device during the TLS handshake (if it was marked as an identity certificate during initialization of the certificate structure using nx_secure_x509_certificate_initialize), or as an issuer as part of a certificate chain provided to the remote host during the TLS handshake.</span></span>

<span data-ttu-id="f21e6-337">同じ共通名を持つ複数のローカル証明書が必要な場合は、*nx_secure_tls_server_certificate_add* サービスを使用して証明書を追加できます （以下の警告をご覧ください）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-337">If multiple local certificates with the same Common Name are needed, certificates may be added using the *nx_secure_tls_server_certificate_add* service (see warning below).</span></span>

<span data-ttu-id="f21e6-338">TLS サーバー モードに証明書が **必要** です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-338">A certificate is **required** for TLS Server mode.</span></span>

<span data-ttu-id="f21e6-339">TLS クライアント モードの場合、証明書は 「*省略可能*」 です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-339">A certificate is *optional* for TLS Client mode.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f21e6-340">*nx_secure_tls_server_certificate_add を使用する場合、この API は、同じ TLS セッションで使用しないでください。サーバー証明書 API は、証明書ごとに一意の数値識別子を使用し、nx_secure_tls_local_certificate_add は、X.509 共通名に基づいてインデックスを作成します。ローカル証明書サービスは、単一の ID 証明書のみを使用するアプリケーションに対して、数値識別子に代わる便利な手段を提供します。共通名を使用すると、アプリケーションは数値識別子を追跡する必要がありません。*</span><span class="sxs-lookup"><span data-stu-id="f21e6-340">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-341">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-341">Parameters</span></span>

- <span data-ttu-id="f21e6-342">**session_ptr** 前に作成した TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-342">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-343">**certificate_ptr** 初期化された TLS 証明書インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-343">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-344">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-344">Return Values</span></span>

- <span data-ttu-id="f21e6-345">**NX_SUCCESS** （0x00） 証明書の追加に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-345">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="f21e6-346">**NX_INVALID_PARAMETERS** （0x4D） 無効または重複する証明書を追加しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-346">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid or duplicate certificate.</span></span>
- <span data-ttu-id="f21e6-347">**NX_PTR_ERROR** （0x07） 無効な TLS セッションまたは証明書ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-347">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-348">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-348">Allowed From</span></span>

<span data-ttu-id="f21e6-349">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-350">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-350">Example</span></span>

```C
/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-351">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-351">See Also</span></span>

- <span data-ttu-id="f21e6-352">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-352">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-353">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-353">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-354">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-354">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-355">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="f21e6-355">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="f21e6-356">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="f21e6-356">nx_secure_tls_local_certificate_find</span></span>

## <a name="nx_secure_tls_local_certificate_find"></a><span data-ttu-id="f21e6-357">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="f21e6-357">nx_secure_tls_local_certificate_find</span></span>

<span data-ttu-id="f21e6-358">NetX Secure TLS セッション内で共通名によってローカル証明書を検索します</span><span class="sxs-lookup"><span data-stu-id="f21e6-358">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-359">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-359">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a><span data-ttu-id="f21e6-360">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-360">Description</span></span>

<span data-ttu-id="f21e6-361">このサービスは、TLS セッションのローカル デバイス証明書ストア内の証明書を検索し、ストア内の NX_SECURE_X509_CERT 構造体へのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-361">This service finds a certificate in the local device certificate store of a TLS session and returns a pointer to the NX_SECURE_X509_CERT structure in the store.</span></span> <span data-ttu-id="f21e6-362">common_name パラメーターとその長さ （name_length） は、証明書の X.509 サブジェクト共通名フィールドを照合することで、ストア内の証明書を識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-362">The common_name parameter and it's length (name_length) are used to identify the certificate in the store by matching the certificate's X.509 Subject Common Name field.</span></span>

<span data-ttu-id="f21e6-363">同じ共通名の証明書が複数存在する場合は、最初のものだけが返されます。代わりに *nx_secure_tls_server_certificate_find* を使用してください。</span><span class="sxs-lookup"><span data-stu-id="f21e6-363">If more than one certificate with the same Common Name is present, only the first one will be returned – use *nx_secure_tls_server_certificate_find* instead.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f21e6-364">*nx_secure_tls_server_certificate_add を使用する場合、この API は、同じ TLS セッションで使用しないでください。サーバー証明書 API は、証明書ごとに一意の数値識別子を使用し、nx_secure_tls_local_certificate_add は、X.509 共通名に基づいてインデックスを作成します。ローカル証明書サービスは、単一の ID 証明書のみを使用するアプリケーションに対して、数値識別子に代わる便利な手段を提供します。共通名を使用すると、アプリケーションは数値識別子を追跡する必要がありません。*</span><span class="sxs-lookup"><span data-stu-id="f21e6-364">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-365">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-365">Parameters</span></span>

- <span data-ttu-id="f21e6-366">**session_ptr** 前に作成した TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-366">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-367">**certificate** 一致した証明書へのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-367">**certificate** Return Pointer to matched certificate.</span></span>
- <span data-ttu-id="f21e6-368">**common_name** 一致する共通名の文字列 （DNS 名）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-368">**common_name** Common Name string to match (DNS name).</span></span>
- <span data-ttu-id="f21e6-369">**name_length** common_name 文字列データの長さ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-369">**name_length** Length of common_name string data.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-370">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-370">Return Values</span></span>

- <span data-ttu-id="f21e6-371">**NX_SUCCESS** （0x00） 証明書が見つかり、「certificate」 パラメーター内でポインターが返されました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-371">**NX_SUCCESS** (0x00) Certificate was found and pointer returned in "certificate" parameter.</span></span>
- <span data-ttu-id="f21e6-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** （0x119） 指定された共通名の証明書が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate with the supplied Common Name was found.</span></span>
- <span data-ttu-id="f21e6-373">**NX_PTR_ERROR** （0x07） 無効な TLS セッション、証明書ポインター、または共通名の文字列。</span><span class="sxs-lookup"><span data-stu-id="f21e6-373">**NX_PTR_ERROR** (0x07) Invalid TLS session, certificate pointer, or common name string.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-374">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-374">Allowed From</span></span>

<span data-ttu-id="f21e6-375">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-375">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-376">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-376">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate_ptr;

/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */

status = nx_secure_tls_local_certificate_find(&tls_session, &certificate_ptr,
                                      “common name”, strlen(“common name”));

/* If status is NX_SUCCESS the variable “certificate_ptr” points to a certificate
   structure containing a certificate with the Common Name “common name”. */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-377">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-377">See Also</span></span>

- <span data-ttu-id="f21e6-378">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-378">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-379">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-379">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-380">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-380">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-381">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="f21e6-381">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="f21e6-382">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-382">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_local_certificate_remove"></a><span data-ttu-id="f21e6-383">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="f21e6-383">nx_secure_tls_local_certificate_remove</span></span>

<span data-ttu-id="f21e6-384">NetX Secure TLS セッションからローカル証明書を削除します</span><span class="sxs-lookup"><span data-stu-id="f21e6-384">Remove local certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-385">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-385">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a><span data-ttu-id="f21e6-386">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-386">Description</span></span>

<span data-ttu-id="f21e6-387">このサービスは、証明書内の共通名フィールドをキーとして、TLS セッションからローカル証明書インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-387">This service removes a local certificate instance from a TLS session, keyed on the Common Name field in the certificate.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f21e6-388">*nx_secure_tls_server_certificate_add を使用する場合、この API は、同じ TLS セッションで使用しないでください。サーバー証明書 API は、証明書ごとに一意の数値識別子を使用し、nx_secure_tls_local_certificate_add は、X.509 共通名に基づいてインデックスを作成します。ローカル証明書サービスは、単一の ID 証明書のみを使用するアプリケーションに対して、数値識別子に代わる便利な手段を提供します。共通名を使用すると、アプリケーションは数値識別子を追跡する必要がありません。*</span><span class="sxs-lookup"><span data-stu-id="f21e6-388">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-389">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-389">Parameters</span></span>

- <span data-ttu-id="f21e6-390">**session_ptr** 前に作成した TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-390">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-391">**common_name** 削除する証明書の共通名の値。</span><span class="sxs-lookup"><span data-stu-id="f21e6-391">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="f21e6-392">**common_name_length** 共通名の文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-392">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-393">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-393">Return Values</span></span>

- <span data-ttu-id="f21e6-394">**NX_SUCCESS** （0x00） 証明書の追加に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-394">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="f21e6-395">**NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-395">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="f21e6-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** （0x119） 証明書が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-397">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-397">Allowed From</span></span>

<span data-ttu-id="f21e6-398">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-398">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-399">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-399">Example</span></span>

```C
/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-400">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-400">See Also</span></span>

- <span data-ttu-id="f21e6-401">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-401">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-402">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-402">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-403">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-403">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-404">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-404">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_metadata_size_calculate"></a><span data-ttu-id="f21e6-405">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="f21e6-405">nx_secure_tls_metadata_size_calculate</span></span>

<span data-ttu-id="f21e6-406">NetX Secure TLS セッション用の暗号化メタデータのサイズを計算します</span><span class="sxs-lookup"><span data-stu-id="f21e6-406">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-407">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-407">Prototype</span></span>

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a><span data-ttu-id="f21e6-408">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-408">Description</span></span>

<span data-ttu-id="f21e6-409">このサービスは、特定の TLS セッションおよび TLS 暗号テーブルに必要な暗号化メタデータのサイズを計算し、返します （暗号化テーブルの詳細については、暗号化メソッドを使用した TLS の初期化に関するセクションをご覧ください）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-409">This service calculates and returns the size of the cryptographic metadata needed for a particular TLS session and TLS cryptography table (see the section "Initializing TLS with Cryptographic Methods" for more information on the cryptographic cipher table).</span></span>

<span data-ttu-id="f21e6-410">このサービスは、nx_secure_tls_session_create に渡されるメタデータ バッファーのサイズを計算する際に、必要な暗号化テーブルを使用して呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-410">This service should be called with the desired cryptographic table to calculate the size of the metadata buffer passed into nx_secure_tls_session_create.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-411">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-411">Parameters</span></span>

- <span data-ttu-id="f21e6-412">**crypto_table** 完全な NetX Secure TLS 暗号テーブルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-412">**crypto_table** Pointer to a complete NetX Secure TLS cryptography table.</span></span>
- <span data-ttu-id="f21e6-413">**metadata_size** サイズ計算の出力 （バイト単位）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-413">**metadata_size** The output of the size calculation in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-414">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-414">Return Values</span></span>

- <span data-ttu-id="f21e6-415">**NX_SUCCESS** （0x00） メタデータ サイズの計算に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-415">**NX_SUCCESS** (0x00) Successful calculation of metadata size.</span></span>
- <span data-ttu-id="f21e6-416">**NX_PTR_ERROR** （0x07） 無効な暗号化テーブルまたは戻り値のサイズのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-416">**NX_PTR_ERROR** (0x07) Invalid crypto table or return size pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-417">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-417">Allowed From</span></span>

<span data-ttu-id="f21e6-418">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-418">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-419">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-419">Example</span></span>

```C
/* Pointer to the platform-specific cipher table. */
extern nx_crypto_tls_ciphers;

/* Return variable for metadata size. */
ULONG crypto_metadata_size;

/* Calculate metadata size.  */
status =  nx_secure_tls_metadata_size_calculate(&nx_crypto_tls_ciphers,
                                                &crypto_metadata_size);


/* If status is NX_SUCCESS then crypto_metadata_size contains the size of the
   metadata buffer for the table nx_crypto_tls_ciphers.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-420">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-420">See Also</span></span>

- <span data-ttu-id="f21e6-421">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-421">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_packet_allocate"></a><span data-ttu-id="f21e6-422">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-422">nx_secure_tls_packet_allocate</span></span>

<span data-ttu-id="f21e6-423">NetX Secure TLS セッション用のパケットを割り当てます</span><span class="sxs-lookup"><span data-stu-id="f21e6-423">Allocate a packet for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-424">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-424">Prototype</span></span>

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f21e6-425">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-425">Description</span></span>

<span data-ttu-id="f21e6-426">このサービスは、指定された NX_PACKET_POOL から、指定されたアクティブな TLS セッション用に NX_PACKET を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-426">This service allocates an NX_PACKET for the specified active TLS session from the specified NX_PACKET_POOL.</span></span> <span data-ttu-id="f21e6-427">このサービスは、TLS 接続を介して送信されるデータ パケットを割り当てる際に、アプリケーションによって呼び出される必要があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-427">This service should be called by the application to allocate data packets to be sent over a TLS connection.</span></span> <span data-ttu-id="f21e6-428">TLS セッションは、このサービスが呼び出される前に初期化される必要があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-428">The TLS session must be initialized before calling this service.</span></span>

<span data-ttu-id="f21e6-429">割り当てられたパケットは適切に初期化されるため、パケット データが入力された後、TLS ヘッダーとフッターのデータが追加される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-429">The allocated packet is properly initialized so that TLS header and footer data may be added after the packet data is populated.</span></span> <span data-ttu-id="f21e6-430">それ以外の動作は、*nx_packet_allocate* と同じです。</span><span class="sxs-lookup"><span data-stu-id="f21e6-430">The behavior is otherwise identical to *nx_packet_allocate*.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-431">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-431">Parameters</span></span>

- <span data-ttu-id="f21e6-432">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-432">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-433">**pool_ptr** パケットの割り当て元となる NX_PACKET_POOL へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-433">**pool_ptr** Pointer to an NX_PACKET_POOL from which to allocate the packet.</span></span>
- <span data-ttu-id="f21e6-434">**packet_ptr** 新しく割り当てられたパケットへの出力ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-434">**packet_ptr** Output pointer to the newly-allocated packet.</span></span>
- <span data-ttu-id="f21e6-435">**wait_option** パケット割り当ての中断オプション。</span><span class="sxs-lookup"><span data-stu-id="f21e6-435">**wait_option** Suspension option for packet allocation.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-436">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-436">Return Values</span></span>

- <span data-ttu-id="f21e6-437">**NX_SUCCESS** （0x00） パケットの割り当てに成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-437">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="f21e6-438">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** （0x111） 基になるパケットの割り当てに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-438">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>
- <span data-ttu-id="f21e6-439">**NX_SECURE_TLS_SESSION_UNINITIALIZED** （0x101） 指定された TLS セッションは初期化されませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-439">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-440">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-440">Allowed From</span></span>

<span data-ttu-id="f21e6-441">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-441">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-442">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-442">Example</span></span>

```C
/* Allocate a new TLS packet from the previously created packet pool and
previously initialized TLS session.   */

status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &packet_ptr,
                                       NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
variable packet_ptr.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-443">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-443">See Also</span></span>

- <span data-ttu-id="f21e6-444">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-444">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="f21e6-445">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-445">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-446">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-446">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-447">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-447">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="f21e6-448">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="f21e6-448">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="f21e6-449">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-449">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="f21e6-450">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="f21e6-450">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="f21e6-451">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="f21e6-451">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="f21e6-452">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-452">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_psk_add"></a><span data-ttu-id="f21e6-453">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-453">nx_secure_tls_psk_add</span></span>

<span data-ttu-id="f21e6-454">NetX Secure TLS セッションに事前共有キーを追加します</span><span class="sxs-lookup"><span data-stu-id="f21e6-454">Add a Pre-Shared Key to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-455">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-455">Prototype</span></span>

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a><span data-ttu-id="f21e6-456">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-456">Description</span></span>

<span data-ttu-id="f21e6-457">このサービスは、事前共有キー （PSK）、その ID 文字列、および ID ヒントを TLS セッション制御ブロックに追加します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-457">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block.</span></span> <span data-ttu-id="f21e6-458">PSK 暗号スイートが有効で、使用されている場合、PSK はデジタル証明書の代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-458">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-459">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-459">Parameters</span></span>

- <span data-ttu-id="f21e6-460">**session_ptr** 前に作成した TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-460">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-461">**pre_shared_key** 実際の PSK 値。</span><span class="sxs-lookup"><span data-stu-id="f21e6-461">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="f21e6-462">**psk_length** PSK 値の長さ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-462">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="f21e6-463">**psk_identity** この PSK 値を識別するために使用される文字列。</span><span class="sxs-lookup"><span data-stu-id="f21e6-463">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="f21e6-464">**identity_length** PSK ID の長さ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-464">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="f21e6-465">**hint** TLS サーバー上のどの PSK グループから選択するかを示すために使用される文字列。</span><span class="sxs-lookup"><span data-stu-id="f21e6-465">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="f21e6-466">**hint_length** ヒントの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-466">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-467">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-467">Return Values</span></span>

- <span data-ttu-id="f21e6-468">**NX_SUCCESS** （0x00） PSK の追加に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-468">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="f21e6-469">**NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-469">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="f21e6-470">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** （0x125） 別の PSK を追加できません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-470">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125)  Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-471">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-471">Allowed From</span></span>

<span data-ttu-id="f21e6-472">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-472">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-473">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-473">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_psk_add(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-474">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-474">See Also</span></span>

- <span data-ttu-id="f21e6-475">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-475">nx_secure_tls_client_psk_set</span></span>
- <span data-ttu-id="f21e6-476">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-476">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-477">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-477">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-478">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-478">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-479">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-479">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_remote_certificate_allocate"></a><span data-ttu-id="f21e6-480">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-480">nx_secure_tls_remote_certificate_allocate</span></span>

<span data-ttu-id="f21e6-481">リモート TLS ホストによって提供された証明書用の領域を割り当てます</span><span class="sxs-lookup"><span data-stu-id="f21e6-481">Allocate space for the certificate provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-482">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-482">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a><span data-ttu-id="f21e6-483">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-483">Description</span></span>

<span data-ttu-id="f21e6-484">このサービスは、TLS セッション中にリモート ホストによって提供される証明書の領域を割り当てる目的で、初期化されていない NX_SECURE_X509_CERT 構造体インスタンスを TLS セッションに追加します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-484">This service adds an uninitialized NX_SECURE_X509_CERT structure instance to a TLS session for the purpose of allocating space for certificates provided by a remote host during a TLS session.</span></span> <span data-ttu-id="f21e6-485">リモート証明書のデータは NetX Secure TLS によって解析され、その情報を使用して、この関数に提供される証明書構造体のインスタンスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-485">The remote certificate data is parsed by NetX Secure TLS and that information is used to populate the certificate structure instance provided to this function.</span></span> <span data-ttu-id="f21e6-486">この方法で追加された証明書は、リンク リストに配置されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-486">Certificates added in this manner are placed in a linked list.</span></span>

<span data-ttu-id="f21e6-487">リモート ホストが複数の証明書を提供することが予想される場合は、この関数を繰り返し呼び出して、すべての証明書の領域を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-487">If it is expected that the remote host will provide multiple certificates, this function should be called repeatedly to allocate space for all certificates.</span></span> <span data-ttu-id="f21e6-488">追加の証明書は、証明書のリンク リストの最後に追加されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-488">The additional certificates are added to the end of the certificate linked list.</span></span>

<span data-ttu-id="f21e6-489">リモート証明書の割り当てに失敗すると、事前共有キー （PSK） 暗号スイートが使用されていない限り、TLS ハンドシェイク中に TLS クライアント モードが失敗します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-489">Failure to allocate a remote certificate will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="f21e6-490">*raw_certificate_buffer* パラメーターは、受信リモート証明書を格納するために割り当てられた領域を指します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-490">The *raw_certificate_buffer* parameter points to space allocated to store the incoming remote certificate.</span></span> <span data-ttu-id="f21e6-491">署名に SHA-256 を使用する 2048 ビットの RSA キーを持つ一般的な証明書の範囲は、1000 バイトから 2000 バイトです。</span><span class="sxs-lookup"><span data-stu-id="f21e6-491">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="f21e6-492">バッファーは、少なくともそのサイズを保持できるだけの大きさが必要ですが、リモート ホスト証明書によっては、大幅に小さい、または大きいことがあります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-492">The buffer should be large enough to at least hold that size, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="f21e6-493">バッファーが小さすぎて受信証明書を保持できない場合、TLS ハンドシェイクはエラーで終了します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-493">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

<span data-ttu-id="f21e6-494">TLS サーバー モードの場合、クライアント証明書の認証が有効になっている場合にのみ、リモート証明書の割り当てが必要です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-494">For TLS Server mode, a remote certificate allocation is needed only if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-495">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-495">Parameters</span></span>

- <span data-ttu-id="f21e6-496">**session_ptr** 前に作成した TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-496">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-497">**certificate_ptr** 初期化されていない X.509 証明書インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-497">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="f21e6-498">**raw_certificate_buffer** リモート ホストから受信した解析されていない証明書を保持するバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-498">**raw_certificate_buffer** Pointer to a buffer to hold the un-parsed certificate received from the remote host.</span></span>
- <span data-ttu-id="f21e6-499">**buffer_size** 生の証明書バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-499">**raw_buffer_size** Size of the raw certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-500">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-500">Return Values</span></span>

- <span data-ttu-id="f21e6-501">**NX_SUCCESS** （0x00） 証明書の割り当てに成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-501">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="f21e6-502">**NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-502">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="f21e6-503">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** （0x12D） 指定されたバッファーが小さすぎました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-503">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="f21e6-504">**NX_INVALID_PARAMETERS** （0x4D） 無効な証明書を追加しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-504">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-505">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-505">Allowed From</span></span>

<span data-ttu-id="f21e6-506">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-506">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-507">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-507">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-508">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-508">See Also</span></span>

- <span data-ttu-id="f21e6-509">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-509">nx_secure_x509_certificate_initialize,</span></span>
- <span data-ttu-id="f21e6-510">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-510">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_buffer_allocate"></a><span data-ttu-id="f21e6-511">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-511">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

<span data-ttu-id="f21e6-512">リモート TLS ホストによって提供されたすべての証明書用の領域を割り当てます</span><span class="sxs-lookup"><span data-stu-id="f21e6-512">Allocate space for all certificates provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-513">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-513">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="f21e6-514">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-514">Description</span></span>

<span data-ttu-id="f21e6-515">このサービスは、TLS クライアント インスタンス内で X.509 認証と検証を実行するために、リモート サーバー ホストからの受信証明書チェーンを処理する目的で領域を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-515">This service allocates space to process incoming certificate chains from remote server hosts in order to perform X.509 authentication and verification in a TLS Client instance.</span></span> <span data-ttu-id="f21e6-516">TLS サーバー モードの場合、クライアントの X.509 証明書の認証が有効になっている場合にのみ、リモート証明書の割り当てが必要です。TLS サーバー インスタンスについては、サービス *nx_secure_tls_session_x509_client_verify_configure* を代わりに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-516">For TLS Server mode, remote certificate allocation is needed only if client X.509 certificate authentication is enabled – for TLS Server instances the service *nx_secure_tls_session_x509_client_verify_configure* should be used instead.</span></span>

<span data-ttu-id="f21e6-517">リモート証明書の割り当てに失敗すると、事前共有キー （PSK） 暗号スイートが使用されていない限り、TLS ハンドシェイク中に TLS クライアントモードが失敗します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-517">Failure to allocate remote certificates will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="f21e6-518">*certificate_buffer* パラメーターは、受信リモート証明書とそれらの証明書に必要な制御ブロックを格納するために割り当てられた領域を指します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-518">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="f21e6-519">バッファーは、証明書の数 （*certs_number*） で除算され、各証明書に均等に指定されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-519">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="f21e6-520">*Buffer_size* パラメーターは、バッファーのサイズを示します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-520">The *buffer_size*  parameter indicates the size of the buffer.</span></span> <span data-ttu-id="f21e6-521">必要な領域を見つけるには、次の数式を使用します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-521">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="f21e6-522">署名に SHA-256 を使用する 2048 ビットの RSA キーを持つ一般的な証明書の範囲は、1000 バイトから 2000 バイトです。</span><span class="sxs-lookup"><span data-stu-id="f21e6-522">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="f21e6-523">バッファーは、証明書ごとに少なくともそのサイズを保持できるだけの大きさが必要ですが、リモート ホスト証明書によっては、大幅に小さい、または大きいことがあります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-523">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="f21e6-524">バッファーが小さすぎて受信証明書を保持できない場合、TLS ハンドシェイクはエラーで終了します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-524">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-525">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-525">Parameters</span></span>

- <span data-ttu-id="f21e6-526">**session_ptr** 前に作成した TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-526">**session_ptr** Pointer to a previously created TLS Session  instance.</span></span>
- <span data-ttu-id="f21e6-527">**certs_number** 指定されたバッファーから割り当てる証明書の数。</span><span class="sxs-lookup"><span data-stu-id="f21e6-527">**certs_number** Number of certificates to allocate from the  provided buffer.</span></span>
- <span data-ttu-id="f21e6-528">**certificate_buffer** リモート ホストから受信した証明書を保持するバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-528">**certificate_buffer** Pointer to a buffer to hold certificates received  from a remote host.</span></span>
- <span data-ttu-id="f21e6-529">**buffer_size** 証明書バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-529">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-530">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-530">Return Values</span></span>

- <span data-ttu-id="f21e6-531">**NX_SUCCESS** （0x00） 証明書の割り当てに成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-531">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="f21e6-532">**NX_PTR_ERROR** （0x07） 無効な TLS セッションまたはバッファー ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-532">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="f21e6-533">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** （0x12D） 指定されたバッファーが小さすぎました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-533">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="f21e6-534">**NX_INVALID_PARAMETERS** （0x4D） バッファーが小さすぎて、必要な数の証明書を保持できませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-534">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold  the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-535">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-535">Allowed From</span></span>

<span data-ttu-id="f21e6-536">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-536">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-537">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-537">Example</span></span>

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE           (CERTIFICATE_NUMBER * \
                              (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_buffer_allocate(&tls_session,
                                                      CERTIFICATE_NUMBER,
                                                      certificate_buffer,
                                                      BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-538">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-538">See Also</span></span>

- <span data-ttu-id="f21e6-539">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-539">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-540">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-540">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_free_all"></a><span data-ttu-id="f21e6-541">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="f21e6-541">nx_secure_tls_remote_certificate_free_all</span></span>

<span data-ttu-id="f21e6-542">受信証明書用に割り当てられた領域を解放します</span><span class="sxs-lookup"><span data-stu-id="f21e6-542">Free space allocated for incoming certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-543">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-543">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="f21e6-544">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-544">Description</span></span>

<span data-ttu-id="f21e6-545">このサービスを使用すると、nx_secure_tls_remote_certificate_allocated によって特定の TLS セッションに割り当てられたすべての証明書バッファーを、そのセッションの空き証明書領域に返すことによって解放できます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-545">This service is used to free all of the certificate buffers allocated to a particular TLS Session by nx_secure_tls_remote_certificate_allocated by returning them to that session's free certificate space.</span></span> <span data-ttu-id="f21e6-546">これは、アプリケーションが、nx_secure_tls_session_delete と nx_secure_tls_session_create を使って TLS セッション オブジェクトを削除および再作成せずに、再利用する場合に必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-546">This may be necessary if an application reuses a TLS session object without deleting it and recreating it with nx_secure_tls_session_delete and nx_secure_tls_session_create.</span></span>

<span data-ttu-id="f21e6-547">nx_secure_tls_session_end の場合のように、リモート証明書スペースは、TLS セッションがリセットされるときに自動的に復旧されるため、ほとんどのアプリケーションは、このサービスを呼び出す必要がありません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-547">Note that the remote certificate space is recovered automatically when the TLS session is reset as happens in nx_secure_tls_session_end so most applications should not need to call this service.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-548">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-548">Parameters</span></span>

- <span data-ttu-id="f21e6-549">**session_ptr** 前に作成した TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-549">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-550">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-550">Return Values</span></span>

- <span data-ttu-id="f21e6-551">**NX_SUCCESS** （0x00） 操作に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-551">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="f21e6-552">**NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-552">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="f21e6-553">**NX_INVALID_PARAMETERS** （0x4D） 内部エラー - 証明書ストアが壊れている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-553">**NX_INVALID_PARAMETERS** (0x4D) Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-554">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-554">Allowed From</span></span>

<span data-ttu-id="f21e6-555">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-555">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-556">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-556">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */

/* … TLS session setup, TCP connection, etc… */

/* End TLS session. */
nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

/* Free up certificate buffers for next connection. */
nx_secure_tls_remote_certificate_free_all(&tls_session);
```

### <a name="see-also"></a><span data-ttu-id="f21e6-557">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-557">See Also</span></span>

- <span data-ttu-id="f21e6-558">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-558">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-559">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-559">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-560">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-560">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-561">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="f21e6-561">nx_secure_tls_session_end</span></span>

## <a name="nx_secure_tls_server_certificate_add"></a><span data-ttu-id="f21e6-562">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-562">nx_secure_tls_server_certificate_add</span></span>

<span data-ttu-id="f21e6-563">数値識別子を使用して TLS サーバー専用の証明書を追加します</span><span class="sxs-lookup"><span data-stu-id="f21e6-563">Add a certificate specifically for TLS servers using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-564">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-564">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="f21e6-565">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-565">Description</span></span>

<span data-ttu-id="f21e6-566">このサービスを使用すると、証明書内で X.509 サブジェクト （共通名） を使用してストアにインデックスを作成するのではなく、数値識別子を使用して、証明書を TLS セッションのローカル ストアに追加できます （nx_secure_tls_local_certificate_add をご覧ください）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-566">This service is used to add a certificate to a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span> <span data-ttu-id="f21e6-567">数値識別子は証明書とは別のもので、これにより複数の証明書を ID 証明書として TLS サーバーに追加したり、同じ共通名を持つ複数の証明書を、同じ TLS セッション ローカル ストアに追加したりできます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-567">The numeric identifier is separate from the certificate and allows multiple certificates to be added as identity certificates to a TLS server, as well as allowing multiple certificates with the same Common Name to be added to the same TLS session local store.</span></span> <span data-ttu-id="f21e6-568">この同じサービスをクライアント証明書に使用することもできますが、TLS クライアントが複数の ID 証明書を持つことはめったにありません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-568">This same service can be used for client certificates, but it is rare for a TLS client to have multiple identity certificates.</span></span>

<span data-ttu-id="f21e6-569">cert_id パラメーターは、アプリケーションによって割り当てられる 0 以外の正の整数です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-569">The cert_id parameter is a non-zero positive integer assigned by the application.</span></span> <span data-ttu-id="f21e6-570">実際の値は重要ではありませんが （0 以外）、指定された TLS セッションに対するストア内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-570">The actual value does not matter (other than zero) but it must be unique in the store for the provided TLS session.</span></span> <span data-ttu-id="f21e6-571">cert_id 値を使用すると、nx_secure_tls_server_certificate_find と nx_secure_tls_server_certificate_remove を使用して、ローカル ストアから証明書を検索し、削除することができます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-571">The cert_id value can be used to find and remove certificates from the local store using nx_secure_tls_server_certificate_find and nx_secure_tls_server_certificate_remove, respectively.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f21e6-572">*nx_secure_tls_local_certificate_add を使用している場合、この API を同じ TLS セッションで使用することはできません。nx_secure_tls_server_certificate_add API は、証明書ごとに一意の数値識別子と、X.509 共通名に基づくローカル証明書サービス インデックスを使用します。サーバー証明書サービスを使用すると、共有データ （特に共通名） を持つ複数の証明書を同じローカル ストアに存在させることができます。これは、複数の ID を持つサーバーに便利です。*</span><span class="sxs-lookup"><span data-stu-id="f21e6-572">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-573">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-573">Parameters</span></span>

- <span data-ttu-id="f21e6-574">**session_ptr** 前に作成した TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-574">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-575">**certificate** 前に初期化された X.509 証明書インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-575">**certificate** Pointer to a previously initialized X.509 certificate instance.</span></span>
- <span data-ttu-id="f21e6-576">**cert_id** 0 以外の正で比較的一意の証明書 ID 番号。</span><span class="sxs-lookup"><span data-stu-id="f21e6-576">**cert_id** Positive, non-zero, relatively unique certificate ID number.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-577">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-577">Return Values</span></span>

- <span data-ttu-id="f21e6-578">**NX_SUCCESS** （0x00） 操作に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-578">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="f21e6-579">**NX_PTR_ERROR** （0x07） 無効な TLS セッションまたは証明書ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-579">**NX_PTR_ERROR** (0x07) Invalid TLS session orcertificate pointer.</span></span>
- <span data-ttu-id="f21e6-580">**NX_SECURE_TLS_CERT_ID_INVALID** （0x138） 指定された証明書 ID に無効な値が含まれています （0 の可能性があります）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-580">**NX_SECURE_TLS_CERT_ID_INVALID** (0x138) The provided certificate ID had An invalid value (likely 0).</span></span>
- <span data-ttu-id="f21e6-581">**NX_SECURE_TLS_CERT_ID_DUPLICATE** （0x139） 指定された証明書 ID は既にローカル ストアに存在しています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-581">**NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) The provided certificate ID was already present in the local store.</span></span>
- <span data-ttu-id="f21e6-582">**NX_INVALID_PARAMETERS** （0x4D） 内部エラー - 証明書ストアが壊れている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-582">**NX_INVALID_PARAMETERS(0x4D)** Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-583">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-583">Allowed From</span></span>

<span data-ttu-id="f21e6-584">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-584">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-585">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-585">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully added with the ID
0x12.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-586">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-586">See Also</span></span>

- <span data-ttu-id="f21e6-587">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-587">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-588">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-588">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="f21e6-589">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-589">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="f21e6-590">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="f21e6-590">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="f21e6-591">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="f21e6-591">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_server_certificate_find"></a><span data-ttu-id="f21e6-592">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="f21e6-592">nx_secure_tls_server_certificate_find</span></span>

<span data-ttu-id="f21e6-593">数値識別子を使用して証明書を検索します</span><span class="sxs-lookup"><span data-stu-id="f21e6-593">Find a certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-594">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-594">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="f21e6-595">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-595">Description</span></span>

<span data-ttu-id="f21e6-596">このサービスを使用すると、証明書内で X.509 サブジェクト （共通名） を使用してストアにインデックスを作成するのではなく、数値識別子を使用して、証明書を TLS セッションのローカル ストア内で検索できます （nx_secure_tls_local_certificate_add をご覧ください）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-596">This service is used to find a certificate in a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="f21e6-597">cert_id パラメーターは、nx_secure_tls_server_certificate_add を使用して証明書が TLS セッション ローカル ストアに追加されるときに、アプリケーションによって割り当てられる 0 以外の正の整数です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-597">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f21e6-598">*nx_secure_tls_local_certificate_add を使用している場合、この API を同じ TLS セッションで使用することはできません。nx_secure_tls_server_certificate_add API は、証明書ごとに一意の数値識別子と、X.509 共通名に基づくローカル証明書サービス インデックスを使用します。サーバー証明書サービスを使用すると、共有データ （特に共通名） を持つ複数の証明書を同じローカル ストアに存在させることができます。これは、複数の ID を持つサーバーに便利です。*</span><span class="sxs-lookup"><span data-stu-id="f21e6-598">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-599">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-599">Parameters</span></span>

- <span data-ttu-id="f21e6-600">**session_ptr** 前に作成した TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-600">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-601">**certificate** 見つかった証明書への参照を返す X.509 証明書ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-601">**certificate** Pointer to an X.509 certificate pointer to return a reference to the found certificate.</span></span>
- <span data-ttu-id="f21e6-602">**cert_id** 0 以外の正の証明書 ID 値。</span><span class="sxs-lookup"><span data-stu-id="f21e6-602">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-603">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-603">Return Values</span></span>

- <span data-ttu-id="f21e6-604">**NX_SUCCESS** （0x00） 操作に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-604">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="f21e6-605">**NX_PTR_ERROR** （0x07） 無効な TLS セッションまたは証明書ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-605">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>
- <span data-ttu-id="f21e6-606">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** （0x119） 指定された証明書 ID が、指定された TLS セッションのローカル ストア内のいずれとも一致しませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-606">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-607">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-607">Allowed From</span></span>

<span data-ttu-id="f21e6-608">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-608">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-609">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-609">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate;


/* Find certificate in TLS session.  */
status =  nx_secure_tls_server_certificate_find(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully found and a reference
returned in the certificate parameter.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-610">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-610">See Also</span></span>

- <span data-ttu-id="f21e6-611">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-611">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-612">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-612">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="f21e6-613">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-613">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="f21e6-614">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-614">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="f21e6-615">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="f21e6-615">nx_secure_tls_server_certificate_remove</span></span>

##  <a name="nx_secure_tls_server_certificate_remove"></a><span data-ttu-id="f21e6-616">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="f21e6-616">nx_secure_tls_server_certificate_remove</span></span>

<span data-ttu-id="f21e6-617">数値識別子を使用してローカル サーバー証明書を削除します</span><span class="sxs-lookup"><span data-stu-id="f21e6-617">Remove a local server certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-618">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-618">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="f21e6-619">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-619">Description</span></span>

<span data-ttu-id="f21e6-620">このサービスを使用すると、証明書内で X.509 サブジェクト （共通名） を使用してストアにインデックスを作成するのではなく、数値識別子を使用して、証明書を TLS セッションのローカル ストアから削除できます （nx_secure_tls_local_certificate_add をご覧ください）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-620">This service is used to remove a certificate from a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="f21e6-621">cert_id パラメーターは、nx_secure_tls_server_certificate_add を使用して証明書が TLS セッション ローカル ストアに追加されるときに、アプリケーションによって割り当てられる 0 以外の正の整数です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-621">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-622">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-622">Parameters</span></span>

- <span data-ttu-id="f21e6-623">**session_ptr** 前に作成した TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-623">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-624">**cert_id** 0 以外の正の証明書 ID 値。</span><span class="sxs-lookup"><span data-stu-id="f21e6-624">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-625">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-625">Return Values</span></span>

- <span data-ttu-id="f21e6-626">**NX_SUCCESS** （0x00） 操作に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-626">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="f21e6-627">**NX_PTR_ERROR** （0x07） 無効な TLS セッション。</span><span class="sxs-lookup"><span data-stu-id="f21e6-627">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>
- <span data-ttu-id="f21e6-628">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** （0x119） 指定された証明書 ID が、指定された TLS セッションのローカル ストア内のいずれとも一致しませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-628">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-629">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-629">Allowed From</span></span>

<span data-ttu-id="f21e6-630">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-630">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-631">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-631">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);
/* Use certificate in TLS session, etc… */

/* Remove certificate from TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_remove(&tls_session, 0x12);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-632">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-632">See Also</span></span>

- <span data-ttu-id="f21e6-633">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-633">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-634">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-634">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="f21e6-635">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-635">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="f21e6-636">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-636">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="f21e6-637">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="f21e6-637">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_alert_value_get"></a><span data-ttu-id="f21e6-638">nx_secure_tls_session_alert_value_get</span><span class="sxs-lookup"><span data-stu-id="f21e6-638">nx_secure_tls_session_alert_value_get</span></span>

<span data-ttu-id="f21e6-639">リモート ホストによって送信された TLS アラートの値とレベルを取得します</span><span class="sxs-lookup"><span data-stu-id="f21e6-639">Get the TLS alert value and level sent by the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-640">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-640">Prototype</span></span>

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a><span data-ttu-id="f21e6-641">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-641">Description</span></span>

<span data-ttu-id="f21e6-642">このサービスは、何らかの問題またはエラーへの応答としてリモート ホストがアラートを送信するときに、TLS アラート レベルと値を取得する際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-642">This service is used to retrieve the TLS alert level and value when the remote host sends an alert in response to some problem or error.</span></span>

<span data-ttu-id="f21e6-643">alert_level パラメーターと alert_value パラメーターの値は、リモート ホストからアラートを受信したことを示す NX_SECURE_TLS_ALERT_RECEIVED （0x114） の状態を返した TLS API 呼び出しの直後に、この関数が呼び出された場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-643">The values of the alert_level and alert_value parameters are only valid if this function is called immediately following a TLS API call that returned a status of NX_SECURE_TLS_ALERT_RECEIVED (0x114) indicating that an alert was received from the remote host.</span></span>

<span data-ttu-id="f21e6-644">TLS アラート値は、ある種の攻撃 （「パディング オラクル」 攻撃など） を防ぐために意図的にあいまいなままになっているため、ローカル ホスト TLS がアラートを送信した場合、返されるエラー コードは、TLS アラート自体よりも実際のエラーをわかりやすく説明していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f21e6-644">Note that if the local host TLS sends an alert, the returned error codes are far more descriptive of the actual error than the TLS alert itself because TLS alert values are intentionally left ambiguous to prevent certain types of attack (such as a "padding oracle" attack or similar).</span></span>

<span data-ttu-id="f21e6-645">アラート レベルの値は、NX_SECURE_TLS_ALERT_LEVEL_WARNING （0x1） または NX_SECURE_TLS_ALERT_LEVEL_FATAL （0x2） の 2 つの値のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="f21e6-645">The alert level only takes one of two values: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) or NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2).</span></span> <span data-ttu-id="f21e6-646">一般的に、CloseNotify アラート （TLS セッションの正常終了を示すために使用） にのみ 「警告」 レベルが提供されますが、一部の拡張機能の構成状況が警告と見なされることもあります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-646">In general, only the CloseNotify Alert (used to indicate a successful end to a TLS session) will be given a level of "Warning" though some extension configuration situations may also be considered warnings.</span></span> <span data-ttu-id="f21e6-647">アラートの大部分が 「致命的」 で、潜在的なセキュリティ障害を示しているため、TLS 接続 （ハンドシェイクまたはセッション） が直ちに終了します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-647">The vast majority of alerts will be "Fatal" indicating a potential security failure and resulting in immediate closure of the TLS connection (handshake or session).</span></span>

<span data-ttu-id="f21e6-648">TLS アラート値は TLS RFC 内で定義されています。参照用の RFC 5246 （TLSv1.2） の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-648">The TLS alert values are defined in the TLS RFCs, here is the list from RFC 5246 (TLSv1.2) for reference:</span></span>

| <span data-ttu-id="f21e6-649">アラート名</span><span class="sxs-lookup"><span data-stu-id="f21e6-649">Alert Name</span></span>                     | <span data-ttu-id="f21e6-650">値</span><span class="sxs-lookup"><span data-stu-id="f21e6-650">Value</span></span> | <span data-ttu-id="f21e6-651">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-651">Description</span></span>                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f21e6-652">close_notify</span><span class="sxs-lookup"><span data-stu-id="f21e6-652">close_notify</span></span>                  | <span data-ttu-id="f21e6-653">0</span><span class="sxs-lookup"><span data-stu-id="f21e6-653">0</span></span>     | <span data-ttu-id="f21e6-654">エラーなし。セッションが正常に終了したことを示します</span><span class="sxs-lookup"><span data-stu-id="f21e6-654">No error, indicates successful session end</span></span>                                                                                                                   |
| <span data-ttu-id="f21e6-655">unexpected_message</span><span class="sxs-lookup"><span data-stu-id="f21e6-655">unexpected_message</span></span>            | <span data-ttu-id="f21e6-656">10</span><span class="sxs-lookup"><span data-stu-id="f21e6-656">10</span></span>    | <span data-ttu-id="f21e6-657">TLS が予期しないメッセージまたは順番を無視したメッセージを受信しました</span><span class="sxs-lookup"><span data-stu-id="f21e6-657">TLS received an unexpected or out-of-order message</span></span>                                                                                                           |
| <span data-ttu-id="f21e6-658">bad_record_mac</span><span class="sxs-lookup"><span data-stu-id="f21e6-658">bad_record_mac</span></span>               | <span data-ttu-id="f21e6-659">20</span><span class="sxs-lookup"><span data-stu-id="f21e6-659">20</span></span>    | <span data-ttu-id="f21e6-660">解読、MAC 検証、またはその両方に失敗しました</span><span class="sxs-lookup"><span data-stu-id="f21e6-660">Decryption and/or MAC verification failed</span></span>                                                                                                                    |
| <span data-ttu-id="f21e6-661">decryption_failed_RESERVED</span><span class="sxs-lookup"><span data-stu-id="f21e6-661">decryption_failed_RESERVED</span></span>   | <span data-ttu-id="f21e6-662">21</span><span class="sxs-lookup"><span data-stu-id="f21e6-662">21</span></span>    | <span data-ttu-id="f21e6-663">**非推奨** 解読に失敗しました （パディング オラクル攻撃により非推奨）</span><span class="sxs-lookup"><span data-stu-id="f21e6-663">**DEPRECATED** Decryption failed (deprecated due to padding oracle attacks)</span></span>                                                                                      |
| <span data-ttu-id="f21e6-664">record_overflow</span><span class="sxs-lookup"><span data-stu-id="f21e6-664">record_overflow</span></span>               | <span data-ttu-id="f21e6-665">22</span><span class="sxs-lookup"><span data-stu-id="f21e6-665">22</span></span>    | <span data-ttu-id="f21e6-666">TLS 最大レコード サイズを超えるレコードを受信しました</span><span class="sxs-lookup"><span data-stu-id="f21e6-666">A record was received that is larger than the TLS maximum record size</span></span>                                                                                        |
| <span data-ttu-id="f21e6-667">decompression_failure</span><span class="sxs-lookup"><span data-stu-id="f21e6-667">decompression_failure</span></span>         | <span data-ttu-id="f21e6-668">30</span><span class="sxs-lookup"><span data-stu-id="f21e6-668">30</span></span>    | <span data-ttu-id="f21e6-669">TLS レコードの圧縮/圧縮解除内で問題が発生しました</span><span class="sxs-lookup"><span data-stu-id="f21e6-669">A problem was encountered in compression/decompression of a TLS record</span></span>                                                                                       |
| <span data-ttu-id="f21e6-670">handshake_failure</span><span class="sxs-lookup"><span data-stu-id="f21e6-670">handshake_failure</span></span>             | <span data-ttu-id="f21e6-671">40</span><span class="sxs-lookup"><span data-stu-id="f21e6-671">40</span></span>    | <span data-ttu-id="f21e6-672">別のアラートの対象となっていない未指定のハンドシェイク エラーが発生しました</span><span class="sxs-lookup"><span data-stu-id="f21e6-672">Some unspecified handshake error occurred that isn't covered by a different alert</span></span>                                                                            |
| <span data-ttu-id="f21e6-673">no_certificate_RESERVED</span><span class="sxs-lookup"><span data-stu-id="f21e6-673">no_certificate_RESERVED</span></span>      | <span data-ttu-id="f21e6-674">41</span><span class="sxs-lookup"><span data-stu-id="f21e6-674">41</span></span>    | <span data-ttu-id="f21e6-675">TLS で **非推奨** （SSL のみ）</span><span class="sxs-lookup"><span data-stu-id="f21e6-675">**DEPRECATED** in TLS (SSL only)</span></span>                                                                                                                                 |
| <span data-ttu-id="f21e6-676">bad_certificate</span><span class="sxs-lookup"><span data-stu-id="f21e6-676">bad_certificate</span></span>               | <span data-ttu-id="f21e6-677">42</span><span class="sxs-lookup"><span data-stu-id="f21e6-677">42</span></span>    | <span data-ttu-id="f21e6-678">受信した証明書に無効な書式または署名が含まれています</span><span class="sxs-lookup"><span data-stu-id="f21e6-678">A certificate that was received contained invalid formatting or signatures</span></span>                                                                                   |
| <span data-ttu-id="f21e6-679">unsupported_certificate</span><span class="sxs-lookup"><span data-stu-id="f21e6-679">unsupported_certificate</span></span>       | <span data-ttu-id="f21e6-680">43</span><span class="sxs-lookup"><span data-stu-id="f21e6-680">43</span></span>    | <span data-ttu-id="f21e6-681">無効な種類の証明書を受信しました （例: TLS サーバー認証に使用される署名専用証明書）</span><span class="sxs-lookup"><span data-stu-id="f21e6-681">A certificate was received that was of an invalid type (e.g. signing-only certificate used for TLS server authentication)</span></span>                                    |
| <span data-ttu-id="f21e6-682">certificate_revoked</span><span class="sxs-lookup"><span data-stu-id="f21e6-682">certificate_revoked</span></span>           | <span data-ttu-id="f21e6-683">44</span><span class="sxs-lookup"><span data-stu-id="f21e6-683">44</span></span>    | <span data-ttu-id="f21e6-684">証明書の状態 （CRL または OCSP によって提供） が 「失効」 として示されました</span><span class="sxs-lookup"><span data-stu-id="f21e6-684">The certificate status (as provided by a CRL or OCSP) was indicated as being "revoked"</span></span>                                                                       |
| <span data-ttu-id="f21e6-685">certificate_expired</span><span class="sxs-lookup"><span data-stu-id="f21e6-685">certificate_expired</span></span>           | <span data-ttu-id="f21e6-686">45</span><span class="sxs-lookup"><span data-stu-id="f21e6-686">45</span></span>    | <span data-ttu-id="f21e6-687">受信した証明書の日付が有効な日付範囲外です （まだ有効でないか期限切れ）</span><span class="sxs-lookup"><span data-stu-id="f21e6-687">The received certificate was outside it's valid date range (either not valid yet or expired)</span></span>                                                                 |
| <span data-ttu-id="f21e6-688">certificate_unknown</span><span class="sxs-lookup"><span data-stu-id="f21e6-688">certificate_unknown</span></span>           | <span data-ttu-id="f21e6-689">46</span><span class="sxs-lookup"><span data-stu-id="f21e6-689">46</span></span>    | <span data-ttu-id="f21e6-690">他のアラートの対象とならなかった不明な証明書の問題が発生しました</span><span class="sxs-lookup"><span data-stu-id="f21e6-690">Some unknown certificate issue was encountered that was not covered by other alerts</span></span>                                                                          |
| <span data-ttu-id="f21e6-691">illegal_parameter</span><span class="sxs-lookup"><span data-stu-id="f21e6-691">illegal_parameter</span></span>             | <span data-ttu-id="f21e6-692">47</span><span class="sxs-lookup"><span data-stu-id="f21e6-692">47</span></span>    | <span data-ttu-id="f21e6-693">TLS ハンドシェイク内の構成またはネゴシエートされた値の一部が無効または範囲外です</span><span class="sxs-lookup"><span data-stu-id="f21e6-693">Some configuration or negotiated value in the TLS handshake was invalid or out of range</span></span>                                                                      |
| <span data-ttu-id="f21e6-694">unknown_ca</span><span class="sxs-lookup"><span data-stu-id="f21e6-694">unknown_ca</span></span>                    | <span data-ttu-id="f21e6-695">48</span><span class="sxs-lookup"><span data-stu-id="f21e6-695">48</span></span>    | <span data-ttu-id="f21e6-696">受信した ID 証明書は、信頼されたルート CA 証明書への証明書チェーンを使用してトレースできませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-696">The received identity certificate could not be traced via a certificate chain to a trusted root CA certificate.</span></span>                                              |
| <span data-ttu-id="f21e6-697">access_denied</span><span class="sxs-lookup"><span data-stu-id="f21e6-697">access_denied</span></span>                 | <span data-ttu-id="f21e6-698">49</span><span class="sxs-lookup"><span data-stu-id="f21e6-698">49</span></span>    | <span data-ttu-id="f21e6-699">有効な証明書を受信したが、要求されたリソースに対してその証明書が無効であったことが、アプリケーションのアクセス制御により示されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-699">Indicates a valid certificate was received but application access control indicated that the certificate was invalid for the requested resources.</span></span>            |
| <span data-ttu-id="f21e6-700">decode_error</span><span class="sxs-lookup"><span data-stu-id="f21e6-700">decode_error</span></span>                  | <span data-ttu-id="f21e6-701">50</span><span class="sxs-lookup"><span data-stu-id="f21e6-701">50</span></span>    | <span data-ttu-id="f21e6-702">TLS ヘッダーまたはハンドシェイク メッセージの一部のフィールドまたは値が範囲外であるか無効であるため、TLS レコードのデコードに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-702">Some field or value in a TLS header or handshake message was out of range or invalid, leading to a failure in decoding of a TLS record.</span></span>                      |
| <span data-ttu-id="f21e6-703">decrypt_error</span><span class="sxs-lookup"><span data-stu-id="f21e6-703">decrypt_error</span></span>                 | <span data-ttu-id="f21e6-704">51</span><span class="sxs-lookup"><span data-stu-id="f21e6-704">51</span></span>    | <span data-ttu-id="f21e6-705">TLS ハンドシェイク中に署名または完了したメッセージ ハッシュを検証できませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-705">A signature or Finished message hash during the TLS handshake could not be verified.</span></span>                                                                         |
| <span data-ttu-id="f21e6-706">export_restriction_RESERVED</span><span class="sxs-lookup"><span data-stu-id="f21e6-706">export_restriction_RESERVED</span></span>  | <span data-ttu-id="f21e6-707">60</span><span class="sxs-lookup"><span data-stu-id="f21e6-707">60</span></span>    | <span data-ttu-id="f21e6-708">TLSv1.2 で非推奨になりました</span><span class="sxs-lookup"><span data-stu-id="f21e6-708">DEPRECATED in TLSv1.2</span></span>                                                                                                                                        |
| <span data-ttu-id="f21e6-709">protocol_version</span><span class="sxs-lookup"><span data-stu-id="f21e6-709">protocol_version</span></span>              | <span data-ttu-id="f21e6-710">70</span><span class="sxs-lookup"><span data-stu-id="f21e6-710">70</span></span>    | <span data-ttu-id="f21e6-711">ハンドシェイク中にネゴシエートされた TLS プロトコルのバージョンは、認識されますが、サポートされていません （例: TLSv1.0 が示されたが、有効になっていない）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-711">The TLS protocol version negotiated during the handshake is recognized but not supported (e.g. TLSv1.0 was presented but not enabled).</span></span>                       |
| <span data-ttu-id="f21e6-712">insufficient_security</span><span class="sxs-lookup"><span data-stu-id="f21e6-712">insufficient_security</span></span>         | <span data-ttu-id="f21e6-713">71</span><span class="sxs-lookup"><span data-stu-id="f21e6-713">71</span></span>    | <span data-ttu-id="f21e6-714">セキュリティで保護された暗号がないことが原因でハンドシェイクが失敗したときに必ず送信されます （例: キー サイズがアプリケーション要件に対して小さすぎる）</span><span class="sxs-lookup"><span data-stu-id="f21e6-714">Sent whenever a handshake fails due to a lack of secure ciphers (e.g. key size is too small for the application requirements)</span></span>                                |
| <span data-ttu-id="f21e6-715">internal_error</span><span class="sxs-lookup"><span data-stu-id="f21e6-715">internal_error</span></span>                | <span data-ttu-id="f21e6-716">80</span><span class="sxs-lookup"><span data-stu-id="f21e6-716">80</span></span>    | <span data-ttu-id="f21e6-717">一部の非 TLS エラー （メモリ割り当ての問題、アプリケーションの問題など） が発生したため、TLS セッションが中断されました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-717">Some non-TLS error (e.g. memory allocation problems, application issues) occurred resulting in a broken TLS session.</span></span>                                         |
| <span data-ttu-id="f21e6-718">user_canceled</span><span class="sxs-lookup"><span data-stu-id="f21e6-718">user_canceled</span></span>                 | <span data-ttu-id="f21e6-719">90</span><span class="sxs-lookup"><span data-stu-id="f21e6-719">90</span></span>    | <span data-ttu-id="f21e6-720">ハンドシェイクが完了する前にユーザーまたはアプリケーションによって TLS セッションがキャンセルされた場合に返されます （CloseNotify と同様）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-720">Returned if the TLS session is cancelled by a user or application before the handshake is complete (similar to CloseNotify).</span></span>                                 |
| <span data-ttu-id="f21e6-721">no_renegotiation</span><span class="sxs-lookup"><span data-stu-id="f21e6-721">no_renegotiation</span></span>              | <span data-ttu-id="f21e6-722">100</span><span class="sxs-lookup"><span data-stu-id="f21e6-722">100</span></span>   | <span data-ttu-id="f21e6-723">再ネゴシエーション要求に応答して、リモート ホストが TLS 再ネゴシエーション ハンドシェイクを実行しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-723">Indiates that the remote host is not willing to perform TLS renegotiation handshakes in response to a renegotiation request.</span></span>                                 |
| <span data-ttu-id="f21e6-724">unsupported_extension</span><span class="sxs-lookup"><span data-stu-id="f21e6-724">unsupported_extension</span></span>         | <span data-ttu-id="f21e6-725">110</span><span class="sxs-lookup"><span data-stu-id="f21e6-725">110</span></span>   | <span data-ttu-id="f21e6-726">明示的に要求されていない拡張機能を含む ServerHello を、TLS クライアントが最初の ClientHello 内で受信した場合に送信されます （これは、サーバーに問題があることを示します）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-726">Sent if a TLS Client receives a ServerHello containing extensions not explicitly asked for in the initial ClientHello (indicating the server has a problem).</span></span> |

### <a name="parameters"></a><span data-ttu-id="f21e6-727">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-727">Parameters</span></span>

- <span data-ttu-id="f21e6-728">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-728">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-729">**alert_level** 受信したアラートのレベル （警告または致命的） を返します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-729">**alert_level** Return the level of the received alert (warning or fatal).</span></span>
- <span data-ttu-id="f21e6-730">**alert_value** 受信したアラートの値を返します （表をご覧ください）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-730">**alert_value** Return the value of the received alert (see table).</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-731">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-731">Return Values</span></span>

- <span data-ttu-id="f21e6-732">**NX_SUCCESS** （0x00） 操作に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-732">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="f21e6-733">**NX_PTR_ERROR** （0x07） 無効な TLS セッション。</span><span class="sxs-lookup"><span data-stu-id="f21e6-733">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-734">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-734">Allowed From</span></span>

<span data-ttu-id="f21e6-735">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-735">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-736">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-736">Example</span></span>

```C
/* Return values. */
UINT status, alert_level, alert_value;


/* Start a TLS session.  */
status =  nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Check for “alert received” error. */
if(status == NX_SECURE_TLS_ALERT_RECEIVED)
{

        /* Get the alert level and value. */
        status =  nx_secure_tls_session_alert_value_get(&tls_session,
                                             &alert_level, &alert_value);

        /* Print out the received alert level and value. */
        printf("Alert recieved. Value: %d, Level: %d\n", alert_value,
                alert_level);
}
else if(status != NX_SUCCESS)
{
    /* Additional error handling. */
}
```

### <a name="see-also"></a><span data-ttu-id="f21e6-737">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-737">See Also</span></span>

- <span data-ttu-id="f21e6-738">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-738">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="f21e6-739">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="f21e6-739">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="f21e6-740">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-740">nx_secure_tls_session_receive</span></span>

## <a name="nx_secure_tls_session_certificate_callback_set"></a><span data-ttu-id="f21e6-741">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-741">nx_secure_tls_session_certificate_callback_set</span></span>

<span data-ttu-id="f21e6-742">追加の証明書検証に使用する TLS 用のコールバックを設定します</span><span class="sxs-lookup"><span data-stu-id="f21e6-742">Set up a callback for TLS to use for additional certificate validation</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-743">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-743">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a><span data-ttu-id="f21e6-744">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-744">Description</span></span>

<span data-ttu-id="f21e6-745">このサービスは、TLS セッションに関数ポインターを割り当てます。これは、リモート ホストから証明書を受信したときに TLS によって呼び出されます。これにより、アプリケーションは、DNS 検証、証明書失効、証明書ポリシーの適用などの検証チェックを実行できます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-745">This service assigns a function pointer to a TLS session that TLS will invoke when a certificate is received from a remote host, allowing the application to perform validation checks such as DNS validation, certificate revocation, and certificate policy enforcement.</span></span>

<span data-ttu-id="f21e6-746">NetX Secure TLS は、コールバックを呼び出す前に証明書に対して基本的な X.509 パス検証を実行して、その証明書を、TLS の信頼された証明書ストア内の証明書にトレースできることを確認しますが、その他の検証はすべて、このコールバックによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-746">NetX Secure TLS will perform basic X.509 path validation on the certificate before invoking the callback to assure that the certificate can be traced to a certificate in the TLS trusted certificate store, but all other validation will be handled by this callback.</span></span>

<span data-ttu-id="f21e6-747">コールバックは、TLS セッション ポインターと、リモート ホスト ID 証明書 （証明書チェーン内のリーフ） へのポインターを提供します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-747">The callback provides the TLS session pointer and a pointer to the remote host identity certificate (the leaf in the certificate chain).</span></span> <span data-ttu-id="f21e6-748">すべての検証が成功した場合、コールバックは NX_SUCCESS を返します。それ以外の場合は、検証エラーを示すエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-748">The callback should return NX_SUCCESS if all validation is successful, otherwise it should return an error code indicating the validation failure.</span></span> <span data-ttu-id="f21e6-749">NX_SUCCESS 以外の値の場合は、TLS ハンドシェイクは直ちに中止されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-749">Any value other than NX_SUCCESS will cause the TLS handshake to immediately abort.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-750">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-750">Parameters</span></span>

- <span data-ttu-id="f21e6-751">**session_ptr** 前に作成した TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-751">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-752">**func_ptr** 証明書検証コールバック関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-752">**func_ptr** Pointer to the certificate validation callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-753">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-753">Return Values</span></span>

- <span data-ttu-id="f21e6-754">**NX_SUCCESS** （0x00） 関数ポインターの割り当てに成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-754">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="f21e6-755">**NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-755">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-756">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-756">Allowed From</span></span>

<span data-ttu-id="f21e6-757">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-757">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-758">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-758">Example</span></span>

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
    /* Certificate validation checking goes here. */
    return(NX_SUCCESS);
}

/* In TLS setup routine. */
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                            certificate_callback);

        /* If status is NX_SUCCESS the certificate callback was added.  */
}
```

### <a name="see-also"></a><span data-ttu-id="f21e6-759">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-759">See Also</span></span>

- <span data-ttu-id="f21e6-760">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-760">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-761">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="f21e6-761">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="f21e6-762">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="f21e6-762">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_tls_session_client_callback_set"></a><span data-ttu-id="f21e6-763">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-763">nx_secure_tls_session_client_callback_set</span></span>

<span data-ttu-id="f21e6-764">TLS クライアント ハンドシェイクの開始時に呼び出す TLS 用のコールバックを設定します</span><span class="sxs-lookup"><span data-stu-id="f21e6-764">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-765">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-765">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="f21e6-766">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-766">Description</span></span>

<span data-ttu-id="f21e6-767">このサービスは、TLS セッションに関数ポインターを割り当てます。これは、TLS クライアント ハンドシェイクが ServerHelloDone メッセージを受信したときに TLS によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-767">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Client handshake has received a ServerHelloDone message.</span></span> <span data-ttu-id="f21e6-768">コールバック関数を使用すると、アプリケーションが、入力または意思決定を必要とする受信した ServerHello メッセージから、任意の TLS 拡張機能を処理できます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-768">The callback function allows an application to process any TLS extensions from the received ServerHello message that require input or decision making.</span></span>

<span data-ttu-id="f21e6-769">コールバックは、呼び出し元の TLS セッション制御ブロックと NX_SECURE_TLS_HELLO_EXTENSION オブジェクトの配列を使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-769">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="f21e6-770">拡張オブジェクトの配列は、特定の拡張機能を検索して解析するヘルパー関数に渡されるように意図されています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-770">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="f21e6-771">現在、TLS クライアント入力を必要とする、サポートされている特定の拡張機能は NetX Secure 内にありませんが、コールバックは、使用可能になる可能性があるカスタムまたは新しい拡張機能を処理するために、アプリケーション設計者が使用できます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-771">Currently, there are no specific extensions supported in NetX Secure that require TLS Client input, but the callback is available for application designers to handle custom or new extensions that may become available.</span></span> <span data-ttu-id="f21e6-772">hello メッセージで提供されている TLS 拡張を解析するヘルパー関数の例については、「*nx_secure_tls_session_sni_extension_parse*」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f21e6-772">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="f21e6-773">また、リモート サーバーが証明書を要求して情報を提供し、TLS クライアントが特定の証明書を選択できるようにした場合は、TLS クライアントに対して *nx_secure_tls_active_certificate_set* を使用して、アクティブな ID 証明書を選択するためにクライアント コールバックを使うこともできます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-773">The client callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Client in the event that the remote server has requested a certificate and provided information to allow the TLS Client to select a specific certificate.</span></span> <span data-ttu-id="f21e6-774">詳細については、「nx_secure_tls_active_certificate_set」のリファレンスをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f21e6-774">See the reference for nx_secure_tls_active_certificate_set for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-775">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-775">Parameters</span></span>

- <span data-ttu-id="f21e6-776">**session_ptr** 前に作成した TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-776">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-777">**func_ptr** TLS クライアント コールバック関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-777">**func_ptr** Pointer to the TLS Client callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-778">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-778">Return Values</span></span>

- <span data-ttu-id="f21e6-779">**NX_SUCCESS** （0x00） 関数ポインターの割り当てに成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-779">**NX_SUCCESS** (0x00) Successful allocation of function pointer.</span></span>
- <span data-ttu-id="f21e6-780">**NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-780">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-781">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-781">Allowed From</span></span>

<span data-ttu-id="f21e6-782">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-782">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-783">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-783">Example</span></span>

```C
/* Callback routine used to process ServerHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the server). */

ULONG tls_client_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{

    /* Extension parsing would go here. */

    /* Set an active identity certificate – the certificate should have been added
       to the local store at application start with
       nx_secure_tls_local_certificate_add. */
    nx_secure_tls_active_certificate_set(session, &global_identity_certificate);

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
    /* Add callback to TLS session.  */
    status =  nx_secure_tls_session_client_callback_set(tls_session,
                                                        client_callback);

    /* If status is NX_SUCCESS the callback was added and will be invoked once
       a ServerHelloDone message is received. */

    return(status);
}
```

### <a name="see-also"></a><span data-ttu-id="f21e6-784">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-784">See Also</span></span>

- <span data-ttu-id="f21e6-785">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-785">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-786">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-786">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="f21e6-787">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-787">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_x509_client_verify_configure"></a><span data-ttu-id="f21e6-788">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="f21e6-788">nx_secure_tls_session_x509_client_verify_configure</span></span>

<span data-ttu-id="f21e6-789">クライアント X.509 検証を有効にし、クライアント証明書用の領域を割り当てます</span><span class="sxs-lookup"><span data-stu-id="f21e6-789">Enable client X.509 verification and allocate space for client certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-790">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-790">Prototype</span></span>

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="f21e6-791">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-791">Description</span></span>

<span data-ttu-id="f21e6-792">このサービスを使用すると、TLS サーバー インスタンスに対するオプションの X.509 クライアント認証が有効になります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-792">This service enables the optional X.509 Client Authentication for a TLS Server instance.</span></span> <span data-ttu-id="f21e6-793">また、リモート クライアント ホストからの受信証明書チェーンの処理に必要な領域も割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-793">It also allocates the space needed to process incoming certificate chains from the remote client host.</span></span> <span data-ttu-id="f21e6-794">リモート クライアントによって提供される証明書は、サービス *nx_secure_tls_trusted_certificate_add* を使用して割り当てられた、TLS サーバー インスタンスの信頼された証明書と照合して検証され ます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-794">The certificates supplied by the remote client will be verified against the TLS server instance's trusted certificates, assigned with the service *nx_secure_tls_trusted_certificate_add.*</span></span>

<span data-ttu-id="f21e6-795">TLS クライアント モードの場合は、リモート証明書の割り当てが必要なので、代わりにサービス *nx_secure_tls_remote_certificate_buffer_allocate* を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-795">For TLS Client mode, remote certificate allocation is required and the service *nx_secure_tls_remote_certificate_buffer_allocate* should be used instead.</span></span> <span data-ttu-id="f21e6-796">TLS クライアント インスタンス上で X.509 クライアント認証を有効にしても何の影響もありません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-796">Enabling X.509 Client Authentication on a TLS Client instance will have no effect.</span></span>

<span data-ttu-id="f21e6-797">*certificate_buffer* パラメーターは、受信リモート証明書とそれらの証明書に必要な制御ブロックを格納するために割り当てられた領域を指します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-797">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="f21e6-798">バッファーは、証明書の数 （*certs_number*） で除算され、各証明書に均等に指定されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-798">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="f21e6-799">*buffer_size* パラメーターは、バッファーのサイズを示します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-799">The *buffer_size* parameter indicates the size of the buffer.</span></span> <span data-ttu-id="f21e6-800">必要な領域を見つけるには、次の数式を使用します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-800">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="f21e6-801">署名に SHA-256 を使用する 2048 ビットの RSA キーを持つ一般的な証明書の範囲は、1000 バイトから 2000 バイトです。</span><span class="sxs-lookup"><span data-stu-id="f21e6-801">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="f21e6-802">バッファーは、証明書ごとに少なくともそのサイズを保持できるだけの大きさが必要ですが、リモート ホスト証明書によっては、大幅に小さい、または大きいことがあります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-802">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="f21e6-803">バッファーが小さすぎて受信証明書を保持できない場合、TLS ハンドシェイクはエラーで終了します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-803">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-804">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-804">Parameters</span></span>

- <span data-ttu-id="f21e6-805">**session_ptr** 前に作成した TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-805">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-806">**certs_number** 指定されたバッファーから割り当てる証明書の数。</span><span class="sxs-lookup"><span data-stu-id="f21e6-806">**certs_number** Number of certificates to allocate from the provided buffer.</span></span>
- <span data-ttu-id="f21e6-807">**certificate_buffer** リモート ホストから受信した証明書を保持するバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-807">**certificate_buffer** Pointer to a buffer to hold certificates received from a remote host.</span></span>
- <span data-ttu-id="f21e6-808">**buffer_size** 証明書バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-808">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-809">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-809">Return Values</span></span>

- <span data-ttu-id="f21e6-810">**NX_SUCCESS** （0x00） 証明書の割り当てに成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-810">**NX_SUCCESS** (0x00)Successful allocation of certificate.</span></span>
- <span data-ttu-id="f21e6-811">**NX_PTR_ERROR** （0x07） 無効な TLS セッションまたはバッファー ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-811">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="f21e6-812">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** （0x12D） 指定されたバッファーが小さすぎました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-812">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="f21e6-813">**NX_INVALID_PARAMETERS** （0x4D） バッファーが小さすぎて、必要な数の証明書を保持できませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-813">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-814">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-814">Allowed From</span></span>

<span data-ttu-id="f21e6-815">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-815">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-816">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-816">Example</span></span>

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE          (CERTIFICATE_NUMBER * \
                                (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Enable X.509 Client verification and allocate certificate space in our TLS
   Server session.  */
status =  nx_secure_tls_session_x509_client_verify_configure(&tls_session,
                                                    CERTIFICATE_NUMBER,
                                                    certificate_buffer,
                                                    BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-817">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-817">See Also</span></span>

- <span data-ttu-id="f21e6-818">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-818">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-819">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-819">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-820">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-820">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

## <a name="nx_secure_tls_session_client_verify_disable"></a><span data-ttu-id="f21e6-821">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="f21e6-821">nx_secure_tls_session_client_verify_disable</span></span>

<span data-ttu-id="f21e6-822">NetX Secure TLS セッション用のクライアント証明書認証を無効にします</span><span class="sxs-lookup"><span data-stu-id="f21e6-822">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-823">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-823">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="f21e6-824">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-824">Description</span></span>

<span data-ttu-id="f21e6-825">このサービスは、特定の TLS セッションのクライアント証明書の認証を無効にします。</span><span class="sxs-lookup"><span data-stu-id="f21e6-825">This service disables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="f21e6-826">詳細については、「nx_secure_tls_session_client_verify_enable」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f21e6-826">See nx_secure_tls_session_client_verify_enable for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-827">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-827">Parameters</span></span>

- <span data-ttu-id="f21e6-828">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-828">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-829">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-829">Return Values</span></span>

- <span data-ttu-id="f21e6-830">**NX_SUCCESS** （0x00） 状態の変更に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-830">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="f21e6-831">**NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-831">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-832">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-832">Allowed From</span></span>

<span data-ttu-id="f21e6-833">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-833">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-834">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-834">Example</span></span>

```C
/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_disable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will not
request certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-835">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-835">See Also</span></span>

- <span data-ttu-id="f21e6-836">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="f21e6-836">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="f21e6-837">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-837">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="f21e6-838">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-838">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_client_verify_enable"></a><span data-ttu-id="f21e6-839">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="f21e6-839">nx_secure_tls_session_client_verify_enable</span></span>

<span data-ttu-id="f21e6-840">NetX Secure TLS セッション用のクライアント証明書認証を有効にします</span><span class="sxs-lookup"><span data-stu-id="f21e6-840">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-841">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-841">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="f21e6-842">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-842">Description</span></span>

<span data-ttu-id="f21e6-843">このサービスは、特定の TLS セッションのクライアント証明書の認証を有効にします。</span><span class="sxs-lookup"><span data-stu-id="f21e6-843">This service enables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="f21e6-844">TLS サーバー インスタンスのクライアント証明書の認証を有効にすることで、初期 TLS ハンドシェイク中、TLS サーバーによって、任意のリモート TLS クライアントから証明書が要求されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-844">Enabling Client Certificate Authentication for a TLS Server instance will cause the TLS Server to request a certificate from any remote TLS Client during the initial TLS handshake.</span></span> <span data-ttu-id="f21e6-845">リモート TLS クライアントから受信した証明書には、CertificateVerify メッセージが伴います。TLS サーバーは、このメッセージを使用して、クライアントが証明書を所有していること （その証明書に関連付けられている秘密キーにアクセスできること） を確認します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-845">The certificate received from the remote TLS Client is accompanied by a CertificateVerify message, which the TLS Server uses to verify that the Client owns the certificate (has access to the private key associated with that certificate).</span></span>

<span data-ttu-id="f21e6-846">指定された証明書が検証され、X.509 証明書チェーンを介して TLS サーバーの信頼された証明書ストア内の証明書にトレースできる場合、リモート TLS クライアントは認証され、ハンドシェイクが続行されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-846">If the provided certificate can be verified and traced back to a certificate in the TLS Server trusted certificate store via an X.509 certificate chain, the remote TLS Client is authenticated and the handshake proceeds.</span></span> <span data-ttu-id="f21e6-847">証明書または CertificateVerify メッセージの処理中にエラーが発生した場合、TLS ハンドシェイクはエラーで終了します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-847">In case of any errors in processing the certificate or CertificateVerify message, the TLS handshake ends with an error.</span></span>

> [!NOTE]
> <span data-ttu-id="f21e6-848">*TLS サーバーの信頼されたストアには、nx_secure_tls_trusted_certificate_add によって追加された証明書が少なくとも 1 つ必要です。これがない場合、常に認証に失敗します。*</span><span class="sxs-lookup"><span data-stu-id="f21e6-848">*The TLS Server must have at least one certificate in its trusted store added with nx_secure_tls_trusted_certificate_add or authentication will always fail.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-849">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-849">Parameters</span></span>

- <span data-ttu-id="f21e6-850">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-850">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-851">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-851">Return Values</span></span>

- <span data-ttu-id="f21e6-852">**NX_SUCCESS** （0x00） 状態の変更に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-852">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="f21e6-853">**NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-853">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-854">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-854">Allowed From</span></span>

<span data-ttu-id="f21e6-855">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-855">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-856">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-856">Example</span></span>

```C
/* Add a trusted certificate so the TLS Server has something to verify against. */
status = nx_secure_tls_trusted_certificate_add(&tls_session,
                                               &trusted_certificate);

/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_enable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will now
request and verify certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-857">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-857">See Also</span></span>

- <span data-ttu-id="f21e6-858">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="f21e6-858">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="f21e6-859">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-859">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="f21e6-860">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-860">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-861">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-861">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_tls_session_create"></a><span data-ttu-id="f21e6-862">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-862">nx_secure_tls_session_create</span></span>

<span data-ttu-id="f21e6-863">セキュリティで保護された通信用の NetX Secure TLS セッションを作成します</span><span class="sxs-lookup"><span data-stu-id="f21e6-863">Create a NetX Secure TLS Session for secure communications</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-864">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-864">Prototype</span></span>

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a><span data-ttu-id="f21e6-865">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-865">Description</span></span>

<span data-ttu-id="f21e6-866">このサービスは、ネットワーク接続を介してセキュリティで保護された TLS 通信を確立する際に使用する、NX_SECURE_TLS_SESSION 構造体のインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-866">This service initializes an NX_SECURE_TLS_SESSION structure instance for use in establishing secure TLS communications over a network connection.</span></span>

<span data-ttu-id="f21e6-867">メソッドは、TLS に使用される使用可能な暗号化メソッドが設定された NX_SECURE_TLS_CRYPTO オブジェクトを取ります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-867">The method takes a NX_SECURE_TLS_CRYPTO object that is populated with the available cryptographic methods to be used for TLS.</span></span> <span data-ttu-id="f21e6-868">*encryption_metadata_area* は、TLS が使用するために割り当てられた 「メタデータ」 用のバッファーを指します。NX_SECURE_TLS_CRYPTO テーブル内の暗号化メソッドは、このメタデータを計算に使用します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-868">The *encryption_metadata_area* points to a buffer allocated for use by TLS for the "metadata" used by the cryptographic methods in the NX_SECURE_TLS_CRYPTO table for calculations.</span></span> <span data-ttu-id="f21e6-869">テーブルのサイズは、nx_secure_tls_metadata_size_calculate サービスを使用して決定できます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-869">The size of the table can be determined by using the nx_secure_tls_metadata_size_calculate service.</span></span> <span data-ttu-id="f21e6-870">詳細については、第 3 章の「NetX Secure TLS」の暗号」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f21e6-870">See the section "Cryptography in NetX Secure TLS" in Chapter 3 for more details.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-871">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-871">Parameters</span></span>

- <span data-ttu-id="f21e6-872">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-872">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-873">**cipher_table** TLS 暗号化メソッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-873">**cipher_table** Pointer to TLS cryptographic methods.</span></span>
- <span data-ttu-id="f21e6-874">**metadata** 暗号メタデータ用のスペースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-874">**encryption_metadata_area** Pointer to space for cryptography metadata.</span></span>
- <span data-ttu-id="f21e6-875">**encryption_metadata_size** メタデータ バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-875">**encryption_metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-876">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-876">Return Values</span></span>

- <span data-ttu-id="f21e6-877">**NX_SUCCESS** （0x00） TLS セッションの初期化に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-877">**NX_SUCCESS** (0x00)Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="f21e6-878">**NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-878">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="f21e6-879">**NX_INVALID_PARAMETERS** （0x4D） メタデータ バッファーが、指定されたメソッドに対して小さすぎました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-879">**NX_INVALID_PARAMETERS** (0x4D) The metadata buffer was too small for the given methods.</span></span>
- <span data-ttu-id="f21e6-880">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** （0x106） 有効なバージョンの TLS に必要な暗号メソッドが暗号テーブルに指定されていませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-880">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A required cipher method for the enabled version of TLS was not supplied in the cipher table.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-881">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-881">Allowed From</span></span>

<span data-ttu-id="f21e6-882">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-882">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-883">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-883">Example</span></span>

```C
/* Reference the platform-specific TLS cryptographic method table. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Declare a buffer for the cryptographic metadata. The size should be calculated
   using nx_secure_tls_metadata_size_calculate. */
UCHAR crypto_metadata[4500];

/* Initialize TLS session.  */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* If status is NX_SUCCESS the TLS Session was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-884">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-884">See Also</span></span>

- <span data-ttu-id="f21e6-885">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-885">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-886">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="f21e6-886">nx_secure_tls_metadata_size_calculate</span></span>
- <span data-ttu-id="f21e6-887">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-887">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-888">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-888">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="f21e6-889">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="f21e6-889">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="f21e6-890">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="f21e6-890">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="f21e6-891">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-891">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="f21e6-892">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="f21e6-892">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="f21e6-893">第 3 章の「NetX Secure TLS の暗号」</span><span class="sxs-lookup"><span data-stu-id="f21e6-893">Cryptography in NetX Secure TLS in Chapter 3</span></span>

## <a name="nx_secure_tls_session_delete"></a><span data-ttu-id="f21e6-894">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="f21e6-894">nx_secure_tls_session_delete</span></span>

<span data-ttu-id="f21e6-895">NetX Secure TLS セッションを削除します</span><span class="sxs-lookup"><span data-stu-id="f21e6-895">Delete a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-896">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-896">Prototype</span></span>

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="f21e6-897">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-897">Description</span></span>

<span data-ttu-id="f21e6-898">このサービスは、NX_SECURE_TLS_SESSION 構造体インスタンスによって表される TLS セッションを削除し、そのセッション インスタンスが所有するすべてのシステム リソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-898">This service deletes a TLS session represented by an NX_SECURE_TLS_SESSION structure instance and releases all system resources owned by that session instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-899">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-899">Parameters</span></span>

- <span data-ttu-id="f21e6-900">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-900">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-901">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-901">Return Values</span></span>

- <span data-ttu-id="f21e6-902">**NX_SUCCESS** （0x00） TLS セッションの初期化に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-902">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="f21e6-903">**NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-903">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-904">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-904">Allowed From</span></span>

<span data-ttu-id="f21e6-905">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-905">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-906">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-906">Example</span></span>

```C
/* Delete TLS session.  */
status =  nx_secure_tls_session_delete(&tls_session);


/* If status is NX_SUCCESS the TLS Session was successfully deleted.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-907">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-907">See Also</span></span>

- <span data-ttu-id="f21e6-908">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-908">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-909">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-909">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-910">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-910">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="f21e6-911">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="f21e6-911">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="f21e6-912">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="f21e6-912">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="f21e6-913">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-913">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="f21e6-914">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-914">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_end"></a><span data-ttu-id="f21e6-915">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="f21e6-915">nx_secure_tls_session_end</span></span>

<span data-ttu-id="f21e6-916">アクティブな NetX Secure TLS セッションを終了します</span><span class="sxs-lookup"><span data-stu-id="f21e6-916">End an active NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-917">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-917">Prototype</span></span>

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f21e6-918">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-918">Description</span></span>

<span data-ttu-id="f21e6-919">このサービスは、TLS CloseNotify メッセージをリモート ホストに送信することで、NX_SECURE_TLS_SESSION 構造体インスタンスによって表される TLS セッションを終了します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-919">This service ends a TLS session represented by an NX_SECURE_TLS_SESSION structure instance by sending the TLS CloseNotify message to the remote host.</span></span> <span data-ttu-id="f21e6-920">その後、サービスは、リモート ホストが独自の CloseNotify メッセージで応答するのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-920">The service then waits for the remote host to respond with its own CloseNotify message.</span></span>

<span data-ttu-id="f21e6-921">リモート ホストによって CloseNotify メッセージが送信されない場合、TLS はこれをエラーと考え、セキュリティ違反の可能性があると見なします。このため、セキュリティで保護された接続にとって、戻り値を確認することは重要です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-921">If the remote host does not send a CloseNotify message, TLS considers this an error and a possible security breach, so checking the return value is important for a secure connection.</span></span> <span data-ttu-id="f21e6-922">**wait_option** パラメーターを使用すると、呼び出し元スレッドに制御を返すまでの、サービスの応答待機時間を制御できます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-922">The **wait_option** parameter can be used to control how long the service should wait for the response before returning control to the calling thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-923">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-923">Parameters</span></span>

- <span data-ttu-id="f21e6-924">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-924">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-925">**wait_option** サービスがリモート ホストからの応答を待機する時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-925">**wait_option** Indicates how long the service should wait for the response from the remote host.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-926">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-926">Return Values</span></span>

- <span data-ttu-id="f21e6-927">**NX_SUCCESS** （0x00） TLS セッションの初期化に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-927">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="f21e6-928">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** （0x113） リモート ホストから応答を受信せずにタイムアウトになりました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-928">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) Did not receive a response from the remote host before timing out.</span></span>
- <span data-ttu-id="f21e6-929">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** （0x111） CloseNotify メッセージを送信するパケットを割り当てることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-929">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate a packet to send the CloseNotify message.</span></span>
- <span data-ttu-id="f21e6-930">**NX_SECURE_TLS_TCP_SEND_FAILED** （0x109） CloseNotify メッセージを TCP ソケット経由で送信できませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-930">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Could not send the CloseNotify message over the TCP socket.</span></span>
- <span data-ttu-id="f21e6-931">**NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-931">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-932">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-932">Allowed From</span></span>

<span data-ttu-id="f21e6-933">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-933">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-934">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-934">Example</span></span>

```C
/* End TLS session.  */
status =  nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the TLS Session was successfully ended.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-935">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-935">See Also</span></span>

- <span data-ttu-id="f21e6-936">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-936">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-937">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-937">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-938">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-938">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="f21e6-939">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="f21e6-939">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="f21e6-940">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="f21e6-940">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="f21e6-941">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-941">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="f21e6-942">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-942">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_packet_buffer_set"></a><span data-ttu-id="f21e6-943">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-943">nx_secure_tls_session_packet_buffer_set</span></span>

<span data-ttu-id="f21e6-944">NetX Secure TLS セッション用のパケット再構築バッファーを設定します</span><span class="sxs-lookup"><span data-stu-id="f21e6-944">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-945">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-945">Prototype</span></span>

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="f21e6-946">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-946">Description</span></span>

<span data-ttu-id="f21e6-947">このサービスは、パケット再構築バッファーを TLS セッションに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-947">This service associates a packet reassembly buffer to a TLS session.</span></span> <span data-ttu-id="f21e6-948">受信 TLS レコードを解読および解析するには、各レコード内のデータを、基になる TCP パケットからアセンブルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-948">In order to decrypt and parse incoming TLS records, the data in each record must be assembled from the underlying TCP packets.</span></span> <span data-ttu-id="f21e6-949">TLS レコードのサイズは最大 16 KB であるため （通常はこれよりもかなり小さくなりますが）、1 つの TCP パケットに収まらない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-949">TLS records can be up to 16KB in size (though typically are much smaller) so may not fit into a single TCP packet.</span></span>

<span data-ttu-id="f21e6-950">受信メッセージのサイズが TLS レコードの上限である 16 KB 未満であることがわかっている場合は、バッファー サイズを小さくできますが、不明な受信データを処理するには、バッファーをできるだけ大きくする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-950">If you know the incoming message size will be smaller than the TLS record limit of 16KB, the buffer size can be made smaller, but in order to handle unknown incoming data the buffer should be made as large as possible.</span></span> <span data-ttu-id="f21e6-951">指定されたバッファーより受信レコードが大きい場合、TLS セッションはエラーで終了します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-951">If an incoming record is larger than the supplied buffer, the TLS session will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-952">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-952">Parameters</span></span>

- <span data-ttu-id="f21e6-953">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-953">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-954">**buffer_ptr** パケットの再構築に使用する TLS 用バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-954">**buffer_ptr** Pointer to buffer for TLS to use for packet reassembly.</span></span>
- <span data-ttu-id="f21e6-955">**buffer_size** 指定されたバッファーのサイズ （バイト単位）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-955">**buffer_size** Size of the supplied buffer in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-956">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-956">Return Values</span></span>

- <span data-ttu-id="f21e6-957">**NX_SUCCESS** （0x00） TLS セッションの初期化に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-957">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="f21e6-958">**NX_INVALID_PARAMETERS** （0x4D） 無効なバッファーまたは TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-958">**NX_INVALID_PARAMETERS** (0x4D) Invalid buffer or TLS session pointer.</span></span>
- <span data-ttu-id="f21e6-959">**NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-959">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-960">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-960">Allowed From</span></span>

<span data-ttu-id="f21e6-961">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-961">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-962">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-962">Example</span></span>

```C
/* Buffer for TLS packet reassembly. */
UCHAR tls_packet_buffer[16384];
/* Assign buffer to TLS session.  */
status =  nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                  sizeof(tls_packet_buffer));


/* If status is NX_SUCCESS the buffer was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-963">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-963">See Also</span></span>

- <span data-ttu-id="f21e6-964">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-964">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-965">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-965">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-966">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-966">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="f21e6-967">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="f21e6-967">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="f21e6-968">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="f21e6-968">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="f21e6-969">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-969">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="f21e6-970">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-970">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_protocol_version_override"></a><span data-ttu-id="f21e6-971">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="f21e6-971">nx_secure_tls_session_protocol_version_override</span></span>

<span data-ttu-id="f21e6-972">NetX Secure TLS セッション用の既定の TLS プロトコル バージョンをオーバーライドします</span><span class="sxs-lookup"><span data-stu-id="f21e6-972">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-973">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-973">Prototype</span></span>

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a><span data-ttu-id="f21e6-974">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-974">Description</span></span>

<span data-ttu-id="f21e6-975">このサービスは、特定のセッションで使用される既定 （最新） の TLS プロトコル バージョンをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="f21e6-975">This service overrides the default (newest) TLS protocol version used by a particular session.</span></span> <span data-ttu-id="f21e6-976">これにより、NetX Secure TLS が、コンパイル時に新しい TLS バージョンを無効にせずに、特定の TLS セッションに対して古いバージョンの TLS を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-976">This enables NetX Secure TLS to use an older version of TLS for a specific TLS Session without disabling newer TLS versions at compile time.</span></span> <span data-ttu-id="f21e6-977">これは、アプリケーションが、最新バージョンの TLS をサポートしていない古いホストとの通信が必要になる可能性があるときに、役に立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-977">This may be useful in applications that may need to communicate with an older host that does not support the newest version of TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f21e6-978">*バージョン 5.11SP3 の時点で、NetX Secure TLS は RFC 7507 をサポートしており （以下の注をご覧ください）、この API を使用して古いバージョンにオーバーライドすると、ClientHello 内でフォールバック SCSV が送信されます。サーバーが新しいバージョンの TLS をサポートしていて、フォールバック SCSV が ClientHello に含まれていると、そのサーバーは 「不適切なフォールバック」アラートで TLS ハンドシェイクを中止します。SCSV は、バージョンのオーバーライドが、有効になっているものより古いバージョンの TLS の場合にのみ送信されます （たとえば、バージョンを TLS 1.2 にオーバーライドしても、SCSV は送信されません）。*</span><span class="sxs-lookup"><span data-stu-id="f21e6-978">*As of version 5.11SP3, NetX Secure TLS supports RFC 7507 (see note below) and any override to an older version with this API will result in a fallback SCSV being sent in the ClientHello. If the server supports a newer version of TLS and the fallback SCSV is included in the ClientHello, that server will abort the TLS handshake with an "Inappropriate Fallback" alert. The SCSV is only sent when the version override is an older version of TLS than is enabled (e.g. if you override the version to TLS 1.2, no SCSV will be sent).*</span></span>

<span data-ttu-id="f21e6-979">protocol_version パラメーターの有効な値は、マクロ NX_SECURE_TLS_VERSION_TLS_1_0、NX_SECURE_TLS_VERSION_TLS_1_1、および NX_SECURE_TLS_VERSION_TLS_1_2 です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-979">Valid values for the protocol_version parameter are the following macros: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1, and NX_SECURE_TLS_VERSION_TLS_1_2.</span></span>

<span data-ttu-id="f21e6-980">マクロ NX_SECURE_TLS_DISABLE_TLS_1_1 と NX_SECURE_TLS_ENABLE_TLS_1_0 は、アプリケーションにコンパイルされる TLS のバージョンの制御に使用できます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-980">The macros NX_SECURE_TLS_DISABLE_TLS_1_1 and NX_SECURE_TLS_ENABLE_TLS_1_0 can be used to control the versions of TLS that are compiled into the application.</span></span> <span data-ttu-id="f21e6-981">TLS バージョン1.2 は常に有効です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-981">TLS version 1.2 is always enabled.</span></span>

<span data-ttu-id="f21e6-982">指定されたバージョンをリモート ホストがサポートしていない場合、接続は失敗します。NetX Secure TLS によってネゴシエートされるのは、指定されたオーバーライド バージョンのみです。</span><span class="sxs-lookup"><span data-stu-id="f21e6-982">Note that if the remote host does not support the supplied version, the connection will fail – only the supplied override version will be negotiated by NetX Secure TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f21e6-983">RFC 7507: TLS フォールバック SCSV。</span><span class="sxs-lookup"><span data-stu-id="f21e6-983">RFC 7507: TLS Fallback SCSV.</span></span> <span data-ttu-id="f21e6-984">この RFC は、プロトコル ダウングレード ネゴシエーションを不適切に処理し、有効な ClientHello メッセージを拒否したサーバーに起因するセキュリティ上の問題を軽減するために導入されました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-984">This RFC was introduced to mitigate a security problem that was originally caused by servers that improperly handled protocol downgrade negotiation and instead rejected otherwise valid ClientHello messages.</span></span> <span data-ttu-id="f21e6-985">このような古いサーバーとの互換性を維持するために、一部の TLS クライアント アプリケーションは、失敗したハンドシェイクの再試行を、古い TLS バージョンを使用して開始します （たとえば、TLS 1.2 で失敗した場合は TLS 1.1 を使ってみます）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-985">In an attempt to remain compatible with these old servers, some TLS client applications started to retry failed handshakes with and older TLS version (e.g. TLS 1.2 failed so try TLS 1.1).</span></span> <span data-ttu-id="f21e6-986">ただし、この回避策による新しい問題が発生しました。サーバーが新しい TLS バージョンをサポートしているのに、攻撃者がネットワークまたはパケット エラーを意図的に引き起こしてクライアントを強制的にダウングレードし、サーバー接続を失敗させるのです。</span><span class="sxs-lookup"><span data-stu-id="f21e6-986">This workaround however introduced a new problem – an attacker could force a client to downgrade by artificially introducing a network or packet error causing the server connection to fail – even when the server supported the newer TLS version.</span></span> <span data-ttu-id="f21e6-987">以前のバージョンにダウングレードすることで、攻撃者はそのバージョンの弱点を悪用する可能性があります （特に、SSLv3<sup>21</sup> は POODLE 攻撃に対して脆弱です）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-987">By downgrading to an older version the attacker could exploit weaknesses in that version (SSLv3<sup>21</sup> in particular is weak to the POODLE attack).</span></span> <span data-ttu-id="f21e6-988">このような状況を防ぐために、RFC 7507 は、疑似暗号スイート <sup>22</sup>、「フォールバック SCSV」 を導入しました。このフォールバック SCSV は、TLS クライアントが自身がサポートする最新バージョンではない TLS バージョンを使用している場合に、TLS サーバーに通知するために、ClientHello を使用して送信されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-988">To prevent this situation, RFC 7507 introdued the "fallback SCSV," a pseudo-ciphersuite<sup>22</sup> sent in the ClientHello that notifies a TLS server when a TLS client is using a TLS version that is not the newest version it supports.</span></span> <span data-ttu-id="f21e6-989">この方法で、新しいバージョンをサポートするサーバーが、フォールバック SCSV を含む ClientHello を拒否し、ダウングレード攻撃が成功するのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-989">This way, a server that supports a newer version can reject a ClientHello containing the fallback SCSV and prevent the downgrade attack from succeeding.</span></span>

21. <span data-ttu-id="f21e6-990">NetX Secure は、POODLE などの既知の深刻な弱点が存在するため SSLv3 を実装していません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-990">NetX Secure does not implement SSLv3 due to the existence of known serious weaknesses such as POODLE.</span></span>

22. <span data-ttu-id="f21e6-991">疑似暗号スイート、つまり SCSV （シグナリング暗号スイート値） は予約済み暗号スイート番号で、以前の TLS バージョンでは使用できなかった機能に関する有効な TLS 実装にシグナルを送るために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-991">A pseudo-ciphersuite, or SCSV (Signaling Cipher Suite Value), is a reserved ciphersuite number that is used to signal enabled TLS implementations about features that were not available in older TLS versions.</span></span> <span data-ttu-id="f21e6-992">フォールバック SCSV と TLS_EMPTY_RENEGOTIATION_INFO_SCSV （RFC 5746） は例です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-992">The fallback SCSV and the TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) are examples.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-993">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-993">Parameters</span></span>

- <span data-ttu-id="f21e6-994">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-994">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-995">**protocol_version** 使用する特定の TLS バージョンの TLS バージョン マクロ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-995">**protocol_version** TLS version macro for the specific TLS version to use.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-996">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-996">Return Values</span></span>

- <span data-ttu-id="f21e6-997">**NX_SUCCESS** （0x00） 状態の変更に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-997">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="f21e6-998">**NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-998">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="f21e6-999">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** （0x110） 既知だがサポートされていない TLS バージョン。</span><span class="sxs-lookup"><span data-stu-id="f21e6-999">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Known but unsupported TLS version.</span></span>
- <span data-ttu-id="f21e6-1000">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** （0x10F） 無効なプロトコル バージョン。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1000">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Invalid protocol version.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1001">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1001">Allowed From</span></span>

<span data-ttu-id="f21e6-1002">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1002">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1003">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1003">Example</span></span>

```C
/* Set the protocol version to be used to TLSv1.1. */
status = nx_secure_tls_session_protocol_version_override(&tls_session,
                                              NX_SECURE_TLS_VERSION_TLS_1_1);

/* This TLS Session will use TLSv1.1 for the handshake and TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1004">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1004">See Also</span></span>

- <span data-ttu-id="f21e6-1005">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-1005">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="f21e6-1006">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-1006">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_receive"></a><span data-ttu-id="f21e6-1007">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-1007">nx_secure_tls_session_receive</span></span>

<span data-ttu-id="f21e6-1008">NetX Secure TLS セッションからデータを受信します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1008">Receive data from a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1009">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1009">Prototype</span></span>

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f21e6-1010">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1010">Description</span></span>

<span data-ttu-id="f21e6-1011">このサービスは、指定されたアクティブな TLS セッションからデータを受信し、そのデータの解読を処理してから、NX_PACKET パラメーター内で呼び出し元に提供します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1011">This service receives data from the specified active TLS session, handling the decryption of that data before providing it to the caller in the NX_PACKET parameter.</span></span> <span data-ttu-id="f21e6-1012">指定されたセッション内でデータがキューに入れられていない場合、呼び出しは、指定された待機オプションに基づいて中断します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1012">If no data is queued in the specified session, the call suspends based on the supplied wait option.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f21e6-1013">*NX_SUCCESS が返された場合は、そのアプリケーションが、不要になった受信パケットを解放する役割を果たします。*</span><span class="sxs-lookup"><span data-stu-id="f21e6-1013">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1014">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1014">Parameters</span></span>

- <span data-ttu-id="f21e6-1015">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1015">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-1016">**packet_ptr** 割り当てられた TLS パケット ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1016">**packet_ptr** Pointer to an allocated TLS packet pointer.</span></span>
- <span data-ttu-id="f21e6-1017">**wait_option** サービスが戻る前にリモート ホストからのパケットを待機する長さを指定します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1017">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1018">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1018">Return Values</span></span>

- <span data-ttu-id="f21e6-1019">**NX_SUCCESS** （0x00） TLS セッションの初期化に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1019">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="f21e6-1020">**NX_NO_PACKET** （0x01） 受信したデータはありません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1020">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="f21e6-1021">**NX_NOT_CONNECTED** （0x38） 基になる TCP ソケットの接続が解除されています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1021">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="f21e6-1022">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** （0x108） 受信したメッセージの認証ハッシュの確認に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1022">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="f21e6-1023">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** （0x10F） 受信したメッセージのヘッダーに不明なプロトコル バージョンが含まれていました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1023">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="f21e6-1024">**NX_SECURE_TLS_ALERT_RECEIVED** （0x114） リモート ホストから TLS アラートを受信しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1024">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="f21e6-1025">**NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1025">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="f21e6-1026">**NX_SECURE_TLS_SESSION_UNINITIALIZED** （0x101） 指定された TLS セッションは初期化されませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1026">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1027">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1027">Allowed From</span></span>

<span data-ttu-id="f21e6-1028">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1028">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1029">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1029">Example</span></span>

```C
/* Receive a packet from an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is received, blocking otherwise.
*/
status =  nx_secure_tls_session_receive(&tls_session, &packet_ptr,
NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the received packet is pointed to by  "packet_ptr". */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1030">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1030">See Also</span></span>

- <span data-ttu-id="f21e6-1031">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-1031">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="f21e6-1032">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-1032">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-1033">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-1033">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-1034">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-1034">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="f21e6-1035">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="f21e6-1035">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="f21e6-1036">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="f21e6-1036">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="f21e6-1037">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="f21e6-1037">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="f21e6-1038">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-1038">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_renegotiate_callback_set"></a><span data-ttu-id="f21e6-1039">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-1039">nx_secure_tls_session_renegotiate_callback_set</span></span>

<span data-ttu-id="f21e6-1040">セッションの再ネゴシエーションの開始時に呼び出されるコールバックを割り当てます</span><span class="sxs-lookup"><span data-stu-id="f21e6-1040">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1041">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1041">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a><span data-ttu-id="f21e6-1042">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1042">Description</span></span>

<span data-ttu-id="f21e6-1043">このサービスは、TLS セッションにコールバックを割り当てます。これは、再ネゴシエーション ハンドシェイクの最初のメッセージをリモート ホストから受信するたびに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1043">This service assigns a callback to a TLS session that will be invoked whenever the first message of a session renegotiation handshake is received from the remote host.</span></span>

<span data-ttu-id="f21e6-1044">このコールバック関数の目的は、再ネゴシエーション ハンドシェイクが開始していることをアプリケーションに通知することです。アプリケーションは、コールバックから 0 以外の値を返すことによって TLS セッションを終了できます。これにより TLS は TLS セッションをエラーで終了します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1044">The callback function is intended as a notification to the application that a renegotiation handshake is beginning – the application may choose to terminate the TLS session by returning any non-zero value from the callback which will cause TLS to end the TLS session with an error.</span></span> <span data-ttu-id="f21e6-1045">アプリケーションが再ネゴシエーションを続行する場合、コールバックは NX_SUCCESS を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1045">If the application wishes to proceed with the renegotiation, the callback should return NX_SUCCESS.</span></span>

> [!NOTE]
> <span data-ttu-id="f21e6-1046">*TLS 再ネゴシエーションのセマンティクスにより、コールバックは、リモートサーバーから HelloRequest を受信したときに必ず NetX Secure TLS クライアントに対して呼び出されますが、クライアントが再ネゴシエーションを開始したときは呼び出されません。NetX Secure TLS Server 上では、コールバックは、再ネゴシエーション用の ClientHello （アクティブな TLS セッションのコンテキスト内で受信したすべての ClientHello） を受信すると必ず呼び出されます。つまり、TLS サーバーは、応答するリモート ホストに対して HelloRequest を送信するため、コールバックは、リモート ホストまたはローカル アプリケーションのどちらが再ネゴシエーションを開始したかにかかわらず呼び出されます。*</span><span class="sxs-lookup"><span data-stu-id="f21e6-1046">*Due to the semantics of TLS renegotiation, the callback will be invoked for NetX Secure TLS Clients whenever a HelloRequest is received from the remote server, but not when the client initiates the renegotiation. On NetX Secure TLS Servers, the callback will be invoked whenever a renegotiation ClientHello is received (any ClientHello received in the context of an active TLS session). This means that the callback will be invoked whether the remote host or the local application has initiated the renegotiation because the TLS server will send a HelloRequest to which the remote client will respond.*</span></span>

<span data-ttu-id="f21e6-1047">NetX Secure TLS は、RFC 5746 の Secure Renegotiation Indication 拡張機能を実装しており、再ネゴシエーションのハンドシェイクが中間者攻撃の対象にならないようにしています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1047">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1048">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1048">Parameters</span></span>

- <span data-ttu-id="f21e6-1049">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1049">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-1050">**func_ptr** コールバック関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1050">**func_ptr** Pointer to callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1051">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1051">Return Values</span></span>

- <span data-ttu-id="f21e6-1052">**NX_SUCCESS** （0x00） コールバックの割り当てに成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1052">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="f21e6-1053">**NX_PTR_ERROR** （0x07） コールバック関数または TLS セッションに対して無効なポインターを使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1053">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer for the callback function or TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1054">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1054">Allowed From</span></span>

<span data-ttu-id="f21e6-1055">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1055">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1056">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1056">Example</span></span>

```C
/* Simple callback notifying the user that a renegotiation is starting. */
ULONG tls_renegotiation_callback(NX_SECURE_TLS_SESSION *session)
{
    printf("Renegotiation initiated by remote host\n");

    return(NX_SUCCESS);
}

/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Set callback for renegotiation notification. */
status = nx_secure_tls_session_renegotiate_callback_set(&tls_session,
                                                tls_renegotiation_callback);
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1057">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1057">See Also</span></span>

- <span data-ttu-id="f21e6-1058">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-1058">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-1059">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-1059">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="f21e6-1060">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-1060">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="f21e6-1061">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="f21e6-1061">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="f21e6-1062">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="f21e6-1062">nx_secure_tls_session_renegotiate</span></span>

## <a name="nx_secure_tls_session_renegotiate"></a><span data-ttu-id="f21e6-1063">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="f21e6-1063">nx_secure_tls_session_renegotiate</span></span>

<span data-ttu-id="f21e6-1064">リモート ホストでセッション再ネゴシエーション ハンドシェイクを開始します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1064">Initiate a session renegotiation handshake with the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1065">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1065">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="f21e6-1066">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1066">Description</span></span>

<span data-ttu-id="f21e6-1067">このサービスは、接続されたリモート TLS ホストとのセッション 「*再ネゴシエーション*」 ハンドシェイクを開始します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1067">This service initiates a session *renegotiation* handshake with a connected remote TLS host.</span></span> <span data-ttu-id="f21e6-1068">再ネゴシエーションは、前に確立された TLS セッションのコンテキスト内での 2 番目の TLS ハンドシェイクで構成されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1068">A renegotiation consists of a second TLS handshake within the context of a previously-established TLS session.</span></span> <span data-ttu-id="f21e6-1069">新しいハンドシェイク メッセージはそれぞれ、新しいセッション キーが生成され、ChangeCipherSpec メッセージが交換されるまで、TLS セッションを使用して暗号化され、その時点で新しいキーを使用して、すべてのメッセージが暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1069">Each of the new handshake messages is encrypted using the TLS session until new session keys are generated and ChangeCipherSpec messages are exchanged, at which time the new keys are used to encrypt all messages.</span></span>

<span data-ttu-id="f21e6-1070">一度 TLS セッションが確立されたら、いつでも再ネゴシエーションを開始できます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1070">A renegotiation can be initiated at any time once a TLS session is established.</span></span> <span data-ttu-id="f21e6-1071">TLS ハンドシェイク中または TLS セッションが確立される前に再ネゴシエーションが試行された場合、処理は実行されません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1071">If a renegotiation is attempted during a TLS handshake or before a TLS session is established no action will be taken.</span></span>

> [!NOTE]
> <span data-ttu-id="f21e6-1072">*このサービスの起動時は、TLS ハンドシェイク全体が実行されるため、完了までの時間と返される状態は、現在の TLS 設定やセッション パラメーターによって異なります。*</span><span class="sxs-lookup"><span data-stu-id="f21e6-1072">*An entire TLS handshake will be performed when this service is invoked so the time to completion and returned status will vary depending on the current TLS settings and session parameters.*</span></span>

<span data-ttu-id="f21e6-1073">NetX Secure TLS は、RFC 5746 の Secure Renegotiation Indication 拡張機能を実装しており、再ネゴシエーションのハンドシェイクが中間者攻撃の対象にならないようにしています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1073">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1074">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1074">Parameters</span></span>

- <span data-ttu-id="f21e6-1075">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1075">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-1076">**wait_option** サービスが戻る前にリモート ホストからのパケットを待機する長さを指定します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1076">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span> <span data-ttu-id="f21e6-1077">これは TLS 内のすべての NetX サービスに渡されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1077">This is passed to all NetX services within TLS.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1078">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1078">Return Values</span></span>

- <span data-ttu-id="f21e6-1079">**NX_SUCCESS** （0x00） 再ネゴシエーションに成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1079">**NX_SUCCESS** (0x00) Successful renegotiation.</span></span>
- <span data-ttu-id="f21e6-1080">**NX_NO_PACKET** （0x01） 受信したデータはありません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1080">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="f21e6-1081">**NX_NOT_CONNECTED** （0x38） 基になる TCP ソケットの接続が解除されています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1081">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="f21e6-1082">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** （0x108） 受信したメッセージの認証ハッシュの確認に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1082">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="f21e6-1083">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** （0x10F） 受信したメッセージのヘッダーに不明なプロトコル バージョンが含まれていました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1083">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="f21e6-1084">**NX_SECURE_TLS_ALERT_RECEIVED** （0x114） リモート ホストから TLS アラートを受信しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1084">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="f21e6-1085">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** （0x134） ローカルまたはリモート TLS セッションが非アクティブになっているため、再ネゴシエーションができません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1085">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) The local or remote TLS session is inactive, making renegotiation impossible.</span></span>
- <span data-ttu-id="f21e6-1086">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** （0x13A） リモート ホストが SCSV または Secure Renegotiation Indication 拡張機能を提供しなかったため、再ネゴシエーションを実行できません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1086">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) The remote host did not provide either the SCSV or Secure Renegotiation Extension and thus renegotiation cannot be performed.</span></span>
- <span data-ttu-id="f21e6-1087">**NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1087">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="f21e6-1088">**NX_SECURE_TLS_SESSION_UNINITIALIZED** （0x101） 指定された TLS セッションは初期化されませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1088">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>
- <span data-ttu-id="f21e6-1089">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** （0x111） 基になるパケットの割り当てに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1089">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1090">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1090">Allowed From</span></span>

<span data-ttu-id="f21e6-1091">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1091">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1092">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1092">Example</span></span>

```C
/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Setup a client socket connection.  */
status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

/* Start the TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Send some data in the first TLS session. (Check “status” for errors…)*/
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Hello there!\r\n", 14, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);

/* Now renegotiate the session. */
status  = nx_secure_tls_session_renegotiate(&tls_session, NX_WAIT_FOREVER);

/* If status == NX_SUCCESS, new TLS session keys have been generated. */

/* Send some data in the new TLS session. This will be encrypted using the new
   keys. */
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Another message…\r\n", 18, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1093">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1093">See Also</span></span>

- <span data-ttu-id="f21e6-1094">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-1094">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-1095">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-1095">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="f21e6-1096">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-1096">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="f21e6-1097">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="f21e6-1097">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="f21e6-1098">nx_secure_tls_session_renegotiation_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-1098">nx_secure_tls_session_renegotiation_callback_set</span></span>

## <a name="nx_secure_tls_session_reset"></a><span data-ttu-id="f21e6-1099">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="f21e6-1099">nx_secure_tls_session_reset</span></span>

<span data-ttu-id="f21e6-1100">NetX Secure TLS セッションのクリアし、リセットします</span><span class="sxs-lookup"><span data-stu-id="f21e6-1100">Clear out and reset a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1101">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1101">Prototype</span></span>

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="f21e6-1102">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1102">Description</span></span>

<span data-ttu-id="f21e6-1103">このサービスは、TLS セッションをクリアして、セッションが作成されたばかりのように状態をリセットし、既存の TLS セッション オブジェクトを新しいセッションに再利用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1103">This service clears out a TLS session and resets the state as if the session had just been created so an existing TLS session object can be re-used for a new session.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1104">Parameters</span></span>

- <span data-ttu-id="f21e6-1105">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1105">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1106">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1106">Return Values</span></span>

- <span data-ttu-id="f21e6-1107">**NX_SUCCESS** （0x00） TLS セッションの初期化に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1107">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="f21e6-1108">**NX_INVALID_PARAMETERS** （0x4D） 無効な TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1108">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="f21e6-1109">**NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1109">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1110">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1110">Allowed From</span></span>

<span data-ttu-id="f21e6-1111">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1111">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1112">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1112">Example</span></span>

```C
/* Reset a TLS session.  */
status =  nx_secure_tls_session_reset(&tls_session);


/* If status is NX_SUCCESS the session was successfully reset and may be reused.*/
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1113">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1113">See Also</span></span>

- <span data-ttu-id="f21e6-1114">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-1114">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-1115">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-1115">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-1116">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-1116">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="f21e6-1117">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="f21e6-1117">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="f21e6-1118">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="f21e6-1118">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="f21e6-1119">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-1119">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="f21e6-1120">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-1120">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_send"></a><span data-ttu-id="f21e6-1121">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="f21e6-1121">nx_secure_tls_session_send</span></span>

<span data-ttu-id="f21e6-1122">NetX Secure TLS セッションを介してデータを送信します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1122">Send data through a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1123">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1123">Prototype</span></span>

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f21e6-1124">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1124">Description</span></span>

<span data-ttu-id="f21e6-1125">このサービスは、指定されたアクティブな TLS セッションを使用して、指定された NX_PACKET でデータを送信し、そのデータの暗号化を処理してから、リモート ホストに送信します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1125">This service sends data in the supplied NX_PACKET, using the specified active TLS session, and handling the encryption of that data before sending it to the remote host.</span></span> <span data-ttu-id="f21e6-1126">受信側の最後に公開されたウィンドウのサイズがこの要求よりも小さい場合、サービスは、指定された待機オプションに基づいて、必要に応じて中断します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1126">If the receiver's last advertised window size is less than this request, the service optionally suspends based on the wait options specified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f21e6-1127">*エラーが返されない限り、アプリケーションは、この呼び出しの後にパケットを解放することはできません。送信後、ネットワーク ドライバーがパケットを解放するため、これを行うと予期しない結果が発生します。*</span><span class="sxs-lookup"><span data-stu-id="f21e6-1127">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1128">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1128">Parameters</span></span>

- <span data-ttu-id="f21e6-1129">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1129">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-1130">**packet_ptr** 送信するデータを含む TLS パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1130">**packet_ptr** Pointer to a TLS packet containing data to be sent.</span></span>
- <span data-ttu-id="f21e6-1131">**wait_option** 要求が受信側のウィンドウ サイズより大きい場合に、サービスがどのように動作するかを定義します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1131">**wait_option** Defines how the service behaves if the request is greater than the window size of the receiver.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1132">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1132">Return Values</span></span>

- <span data-ttu-id="f21e6-1133">**NX_SUCCESS** （0x00） TLS セッションの初期化に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1133">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="f21e6-1134">**NX_NO_PACKET** （0x01） 受信したデータはありません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1134">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="f21e6-1135">**NX_NOT_CONNECTED** （0x38） 基になる TCP ソケットの接続が解除されています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1135">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="f21e6-1136">**NX_SECURE_TLS_TCP_SEND_FAILED** （0x109） 基になる TCP ソケットの送信に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1136">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) The underlying TCP socket send failed.</span></span>
- <span data-ttu-id="f21e6-1137">**NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1137">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="f21e6-1138">**NX_SECURE_TLS_SESSION_UNINITIALIZED** （0x101） 指定された TLS セッションは初期化されませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1138">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1139">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1139">Allowed From</span></span>

<span data-ttu-id="f21e6-1140">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1140">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1141">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1141">Example</span></span>

```C
/* Send a packet using an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is sent, blocking otherwise.   */
status =  nx_secure_tls_session_send(&tls_session, &packet_ptr, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the packet has been sent. */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1142">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1142">See Also</span></span>

- <span data-ttu-id="f21e6-1143">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-1143">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="f21e6-1144">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-1144">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-1145">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-1145">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-1146">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-1146">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="f21e6-1147">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-1147">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="f21e6-1148">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="f21e6-1148">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="f21e6-1149">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-1149">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="f21e6-1150">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="f21e6-1150">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="f21e6-1151">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-1151">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_server_callback_set"></a><span data-ttu-id="f21e6-1152">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-1152">nx_secure_tls_session_server_callback_set</span></span>

<span data-ttu-id="f21e6-1153">TLS サーバー ハンドシェイクの開始時に呼び出す TLS 用のコールバックを設定します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1153">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1154">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1154">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="f21e6-1155">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1155">Description</span></span>

<span data-ttu-id="f21e6-1156">このサービスは、TLS セッションに関数ポインターを割り当てます。これは、TLS サーバー ハンドシェイクが ClientHello メッセージを受信したときに TLS によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1156">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Server handshake has received a ClientHello message.</span></span> <span data-ttu-id="f21e6-1157">コールバック関数を使用すると、アプリケーションが、入力または意思決定を必要とする受信した ClientHello メッセージから、任意の TLS 拡張機能を処理できます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1157">The callback function allows an application to process any TLS extensions from the received ClientHello message that require input or decision making.</span></span>

<span data-ttu-id="f21e6-1158">コールバックは、呼び出し元の TLS セッション制御ブロックと NX_SECURE_TLS_HELLO_EXTENSION オブジェクトの配列を使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1158">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="f21e6-1159">拡張オブジェクトの配列は、特定の拡張機能を検索して解析するヘルパー関数に渡されるように意図されています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1159">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="f21e6-1160">hello メッセージで提供されている TLS 拡張を解析するヘルパー関数の例については、「*nx_secure_tls_session_sni_extension_parse*」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1160">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="f21e6-1161">サーバー コールバックを使用して、TLS サーバー用の *nx_secure_tls_active_certificate_set* を使ってアクティブな ID 証明書を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1161">The server callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Server.</span></span> <span data-ttu-id="f21e6-1162">これは、通常、Server Name Indication （SNI） 拡張機能に応答して発生します。これにより、TLS クライアントが、接続しようとしているサーバーを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1162">This will most often occur in response to a Server Name Indication (SNI) extension which allows a TLS Client to indicate which server it is attempting to contact.</span></span> <span data-ttu-id="f21e6-1163">詳細については、「*nx_secure_tls_session_sni_extension_parse*」および「*nx_secure_tls_active_certificate_set*」のリファレンスをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1163">See the references for *nx_secure_tls_session_sni_extension_parse* and *nx_secure_tls_active_certificate_set* for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1164">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1164">Parameters</span></span>

- <span data-ttu-id="f21e6-1165">**session_ptr** 前に作成した TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1165">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-1166">**func_ptr** TLS サーバー コールバック関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1166">**func_ptr** Pointer to the TLS Server callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1167">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1167">Return Values</span></span>

- <span data-ttu-id="f21e6-1168">**NX_SUCCESS** （0x00） 関数ポインターの割り当てに成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1168">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="f21e6-1169">**NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1169">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1170">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1170">Allowed From</span></span>

<span data-ttu-id="f21e6-1171">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1172">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1172">Example</span></span>

```C
/* Application-supplied function to map server DNS name to a specific certificate
   ID. The certificate ID is supplied by the application when the certificate is
   added with nx_secure_tls_server_certificate_add. */
UINT application_find_id_by_dns_name(NX_SECURE_X509_DNS_NAME *dns_name)
{
    if(strncmp(dns_name->nx_secure_x509_dns_name, “server_name”,
               dns_name->nx_secure_x509_dns_name_length) == 0)
    {
        /* DNS name matches one we know, return it’s ID. */
        return(0x12);
    }

    /* Unknown DNS name, return 0 to indicate no matching ID found. */
    return(0);
}

/* Callback routine used to process ClientHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the client). */
ULONG tls_server_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{
UINT status;
NX_SECURE_X509_DNS_NAME dns_name;
UINT cert_id;
NX_SECURE_X509_CERT *certificate;


    /* Find and parse a Server Name Indication (SNI) extension. */
    status = nx_secure_tls_session_sni_extension_parse(session, extensions,
                                                       num_extensions, &dns_name);

    if(status != NX_SUCCESS && status != NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
        /* Parsed an invalid extension, return the error. */
        return(status);
    }

    if(status == NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
            /* SNI extension not found, just return success to use the default
               certificate. */
            return(NX_SUCCESS);
    }

    /* Find the application-supplied numeric identifier for the specified DNS
       name provided by the remote client. */
    cert_id = application_find_id_by_dns_name(&dns_name);

    /* If cert_id is 0, just use the default identity certificate added with
       nx_secure_tls_local_certificate_add. */
    if(cert_id != 0)
    {
        /* Application found a matching name, find the certificate in our
           store. */
        status = nx_secure_tls_server_certificate_find(tls_session, &certificate,
                                                       cert_id);

        if(status != NX_SUCCESS)
        {
            /* Didn’t find a valid certificate with the supplied ID. Return an
               error so TLS can shut down the handshake. */
            return(NX_SECURE_TLS_CERTIFICATE_NOT_FOUND);
        }

        /* Set the active identity certificate – the certificate should have been
           added to the local store at application start with
           nx_secure_tls_local_certificate_add. */
        nx_secure_tls_active_certificate_set(session, certificate);
    }

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_server_callback_set(tls_session,
                                                            server_callback);

        /* If status is NX_SUCCESS the callback was added and will be invoked
           immediately after a ClientHello message is received. */

        return(status);
}
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1173">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1173">See Also</span></span>

- <span data-ttu-id="f21e6-1174">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-1174">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-1175">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-1175">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="f21e6-1176">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-1176">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="f21e6-1177">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="f21e6-1177">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="f21e6-1178">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-1178">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="f21e6-1179">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="f21e6-1179">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_sni_extension_parse"></a><span data-ttu-id="f21e6-1180">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="f21e6-1180">nx_secure_tls_session_sni_extension_parse</span></span>

<span data-ttu-id="f21e6-1181">TLS クライアントから受信した Server Name Indication （SNI） 拡張機能を解析します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1181">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1182">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1182">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="f21e6-1183">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1183">Description</span></span>

<span data-ttu-id="f21e6-1184">このサービスは、TLS サーバー セッション コールバック内から呼び出され、nx_secure_tls_session_server_callback_set を使用して TLS セッションに追加されるように意図されています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1184">This service is intended to be called from within a TLS Server session callback, added to a TLS session using nx_secure_tls_session_server_callback_set.</span></span> <span data-ttu-id="f21e6-1185">コールバックは、リモート TLS クライアントから ClientHello メッセージを受信した後に呼び出され、使用可能な拡張機能の配列 （および配列内の拡張機能の数） が提供されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1185">The callback is invoked following the reception of a ClientHello message from a remote TLS client and is supplied an array of available extensions (and the number of extensions in the array).</span></span> <span data-ttu-id="f21e6-1186">その配列とその長さをこのルーチンに直接渡して、SNI 拡張機能が存在するかどうかを判断できます。存在しない場合は、NX_SECURE_TLS_EXTENSION_NOT_FOUND が返されますが、これは単にクライアントが SNI 拡張機能を提供しないことを選択したことを示します （エラーではありません）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1186">That array and its length can be passed directly to this routine to determine if there is an SNI extension present – if not, NX_SECURE_TLS_EXTENSION_NOT_FOUND is returned indicating simply that the client opted not to provice the SNI extension (this is not an error).</span></span>

<span data-ttu-id="f21e6-1187">SNI 拡張機能が見つかった場合、TLS クライアントによって提供される X.509 DNS 名が dns_name 構造体で返されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1187">If the SNI extension is found, the X.509 DNS name supplied by the TLS client is returned in the dns_name structure.</span></span> <span data-ttu-id="f21e6-1188">現在、SNI 拡張機能が提供しているのは単一の DNS 名エントリのみです。これは、TLS サーバーがリモート クライアントに送信する ID 証明書を決定するために使用されることがあります。\*\*</span><span class="sxs-lookup"><span data-stu-id="f21e6-1188">Currently, the SNI extension only supplies a single DNS name entry, which may be used by the TLS server to determine which identity certificate to send to the remote client.\*\*</span></span>

<span data-ttu-id="f21e6-1189">NX_SECURE_X509_DNS_NAME 構造体のフィールド *nx_secure_x509_dns_name* 内には、単に DNS が UCHAR 文字列として、また *nx_secure_x509_dns_name_length* 内には名前文字列の長さが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1189">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="f21e6-1190">マクロ NX_SECURE_X509_DNS_NAME_MAX は、nx_secure_x509_dns_name バッファーのサイズを制御します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1190">The macro NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1191">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1191">Parameters</span></span>

- <span data-ttu-id="f21e6-1192">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1192">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-1193">**extensions** （セッション コールバックからの） TLS Hello 拡張機能の配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1193">**extensions** Pointer to an array of TLS Hello extensions (from session callback).</span></span>
- <span data-ttu-id="f21e6-1194">**num_extensions** （セッション コールバックからの） 配列内の拡張機能の数。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1194">**num_extensions** Number of extensions in array (from session callback).</span></span>
- <span data-ttu-id="f21e6-1195">**dns_name** SNI 拡張機能内で指定された DNS 名を返します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1195">**dns_name** Return DNS name supplied in the SNI extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1196">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1196">Return Values</span></span>

- <span data-ttu-id="f21e6-1197">**NX_SUCCESS** （0x00） 拡張機能の解析に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1197">**NX_SUCCESS** (0x00) Successful parsing of the extension.</span></span>
- <span data-ttu-id="f21e6-1198">**NX_PTR_ERROR** （0x07） 無効な拡張機能の配列または TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1198">**NX_PTR_ERROR** (0x07) Invalid extensions array or TLS session pointer.</span></span>
- <span data-ttu-id="f21e6-1199">**NX_SECURE_TLS_EXTENSION_NOT_FOUND** （0x136） SNI 拡張機能が見つかりません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1199">**NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) SNI extension not found.</span></span>
- <span data-ttu-id="f21e6-1200">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** （0x137） SNI 拡張形式が無効でした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1200">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) SNI extension format was invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1201">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1201">Allowed From</span></span>

<span data-ttu-id="f21e6-1202">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1202">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1203">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1203">Example</span></span>

### <a name="see-also"></a><span data-ttu-id="f21e6-1204">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1204">See Also</span></span>

- <span data-ttu-id="f21e6-1205">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-1205">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="f21e6-1206">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-1206">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="f21e6-1207">nx_secure_tls_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-1207">nx_secure_tls_server_callback_set</span></span>
- <span data-ttu-id="f21e6-1208">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-1208">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_sni_extension_set"></a><span data-ttu-id="f21e6-1209">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-1209">nx_secure_tls_session_sni_extension_set</span></span>

<span data-ttu-id="f21e6-1210">リモートサーバーに送信する Server Name Indication （SNI） 拡張機能の DNS 名を設定します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1210">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1211">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1211">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="f21e6-1212">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1212">Description</span></span>

<span data-ttu-id="f21e6-1213">このサービスにより、TLS クライアント アプリケーションが、Server Name Indication （SNI） TLS 拡張機能を使用して、リモート TLS サーバーに優先サーバー DNS 名を提供できます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1213">This service allows a TLS Client application to provide a preferred server DNS name to a remote TLS server using the Server Name Indication (SNI) TLS extension.</span></span> <span data-ttu-id="f21e6-1214">SNI 拡張機能を使用すると、サーバーは、クライアントによって指定されたサーバーの設定に基づいて、適切な ID 証明書とパラメーターを選択できます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1214">The SNI extension allows the server to select the proper identity certificate and parameters based on the client's indicated server preference.</span></span> <span data-ttu-id="f21e6-1215">SNI 拡張機能は現在、送信される単一の DNS 名のみをサポートしているため、単一の名前パラメーターをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1215">The SNI extension currently only supports a single DNS name to be sent, hence the singular name parameter.</span></span> <span data-ttu-id="f21e6-1216">dns_name パラメーターは、*nx_secure_x509_dns_name_initialize* を使用して初期化する必要があり、クライアントの優先サーバーが追加されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1216">The dns_name parameter must be initialized with *nx_secure_x509_dns_name_initialize* and will contain the client's preferred server.</span></span> <span data-ttu-id="f21e6-1217">拡張機能の名前を設定解除するには、「dns_name」 パラメーターの値に NX_NULL に指定して呼び出すだけです。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1217">To unset the extension name, simply call this service with a "dns_name" parameter value of NX_NULL.</span></span>

<span data-ttu-id="f21e6-1218">NX_SECURE_X509_DNS_NAME 構造体のフィールド *nx_secure_x509_dns_name* 内には、単に DNS が UCHAR 文字列として含まれます。また *nx_secure_x509_dns_name_length* 内には名前文字列の長さが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1218">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field  *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="f21e6-1219">マクロ NX_SECURE_X509_DNS_NAME_MAX は、nx_secure_x509_dns_name バッファーのサイズを制御します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1219">The macro  NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

> [!NOTE]
> <span data-ttu-id="f21e6-1220">*このルーチンは、nx_secure_tls_session_start が呼び出される前に呼び出す必要があります。そうしないと、ClientHello に SNI 拡張機能が追加されません。*</span><span class="sxs-lookup"><span data-stu-id="f21e6-1220">*This routine must be called before nx_secure_tls_session_start is invoked or the ClientHello will not contain the SNI extension.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1221">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1221">Parameters</span></span>

- <span data-ttu-id="f21e6-1222">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1222">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-1223">**dns_name** アプリケーションによって指定された DNS 名。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1223">**dns_name** DNS name supplied by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1224">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1224">Return Values</span></span>

- <span data-ttu-id="f21e6-1225">**NX_SUCCESS** （0x00） DNS サーバー名の追加に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1225">**NX_SUCCESS** (0x00) Successful addition of DNS server name.</span></span>
- <span data-ttu-id="f21e6-1226">**NX_PTR_ERROR** （0x07） 無効な DNS 名または TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1226">**NX_PTR_ERROR** (0x07) Invalid DNS name or TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1227">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1227">Allowed From</span></span>

<span data-ttu-id="f21e6-1228">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1228">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1229">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1229">Example</span></span>

```C
#define TLS_SNI_SERVER_NAME “www.example.com”

NX_SECURE_X509_DNS_NAME dns_name;
NX_SECURE_TLS_SESSION client_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&client_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));


    /* Initialize the DNS server name we want to send in the SNI extension. */
    nx_secure_x509_dns_name_initialize(&dns_name, TLS_SNI_SERVER_NAME,
                                    strlen(TLS_SNI_SERVER_NAME));

    /* The SNI server name needs to be set prior to starting the TLS session. */
    nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);

   /* Start TLS session as normal. */
}
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1230">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1230">See Also</span></span>

- <span data-ttu-id="f21e6-1231">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-1231">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="f21e6-1232">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-1232">nx_secure_x509_dns_name_initialize</span></span>

## <a name="nx_secure_tls_session_start"></a><span data-ttu-id="f21e6-1233">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-1233">nx_secure_tls_session_start</span></span>

<span data-ttu-id="f21e6-1234">NetX Secure TLS セッションを開始します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1234">Start a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1235">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1235">Prototype</span></span>

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f21e6-1236">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1236">Description</span></span>

<span data-ttu-id="f21e6-1237">このサービスは、指定された TLS セッション制御ブロック、および接続されている TCP ソケットを使用して、TLS セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1237">This service starts a TLS session using the supplied TLS session control block and a connected TCP socket.</span></span> <span data-ttu-id="f21e6-1238">nx_tcp_client_socket_connect または nx_tcp_server_socket_accept のいずれかに対する呼び出しが成功した後、TCP 接続は既に完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1238">The TCP connection must already be complete following a successful call to either nx_tcp_client_socket_connect or nx_tcp_server_socket_accept.</span></span>

<span data-ttu-id="f21e6-1239">このサービスは、TCP ソケットからの TLS セッション （クライアントまたはサーバー） の種類を決定します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1239">This service will determine the type of TLS session (Client or Server) from the TCP socket.</span></span>

<span data-ttu-id="f21e6-1240">待機オプションは、TLS ハンドシェイクの進行中にサービスがどのように動作するかを定義します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1240">The wait option defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1241">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1241">Parameters</span></span>

- <span data-ttu-id="f21e6-1242">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1242">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-1243">**tcp_socket_ptr** 接続されている TCP ソケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1243">**tcp_socket_ptr** Pointer to a connected TCP socket.</span></span>
- <span data-ttu-id="f21e6-1244">**wait_option** TLS ハンドシェイクの進行中にサービスがどのように動作するかを定義します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1244">**wait_option** Defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1245">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1245">Return Values</span></span>

- <span data-ttu-id="f21e6-1246">**NX_SUCCESS** （0x00） TLS セッションの初期化に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1246">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="f21e6-1247">**NX_NOT_CONNECTED** （0x38） 基になる TCP ソケットの接続が解除されています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1247">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="f21e6-1248">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** （0x102） 受信した TLS メッセージの種類が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1248">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="f21e6-1249">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** （0x106） リモート ホストによって提供された暗号はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1249">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="f21e6-1250">**NX_SECURE_TLS_HANDSHAKE_FAILURE** （0x107） TLS ハンドシェイク中のメッセージの処理に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1250">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="f21e6-1251">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** （0x108） 受信メッセージがハッシュ MAC チェックに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1251">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a hash MAC check.</span></span>
- <span data-ttu-id="f21e6-1252">**NX_SECURE_TLS_TCP_SEND_FAILED** （0x109） 基になる TCP ソケットの送信に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1252">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="f21e6-1253">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** （0x10A） 受信メッセージに無効な長さのフィールドがありました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1253">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="f21e6-1254">**NX_SECURE_TLS_BAD_CIPHERSPEC** （0x10B） 受信 ChangeCipherSpec メッセージが正しくありませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1254">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="f21e6-1255">**NX_SECURE_TLS_INVALID_SERVER_CERT** （0x10C） 受信 TLS 証明書を、リモート TLS サーバーの識別に使用できません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1255">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="f21e6-1256">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** （0x10D） リモート ホストによって提供された公開キー暗号はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1256">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="f21e6-1257">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** （0x10E） リモート ホストは、NetX Secure TLS スタックによってサポートされている暗号スイートがないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1257">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="f21e6-1258">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** （0x10F） 受信した TLS メッセージのヘッダーに不明な TLS バージョンがありました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1258">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="f21e6-1259">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** （0x110） 受信した TLS メッセージのヘッダーに既知だがサポートされていない TLS バージョンがありました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1259">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="f21e6-1260">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** （0x111） 内部 TLS パケットの割り当てに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1260">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="f21e6-1261">**NX_SECURE_TLS_INVALID_CERTIFICATE** （0x112） リモート ホストが無効な証明書を提供しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1261">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="f21e6-1262">**NX_SECURE_TLS_ALERT_RECEIVED** （0x114） リモート ホストが、エラーを通知して TLS セッションを終了するアラートを送信しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1262">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="f21e6-1263">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** （0x13B） 暗号スイート テーブル内のエントリに NULL 関数ポインターがありました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1263">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) An entry in the ciphersuite table had a NULL function pointer.</span></span>
- <span data-ttu-id="f21e6-1264">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** （0x146） リモート TLS ClientHello にフォールバック SCSV が含まれており、バージョン フォールバックを試行しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1264">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) A remote TLS ClientHello included the fallback SCSV andattempted a version fallback.</span></span>
- <span data-ttu-id="f21e6-1265">**NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1265">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1266">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1266">Allowed From</span></span>

<span data-ttu-id="f21e6-1267">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1268">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1268">Example</span></span>

```C
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Initialize the TLS session structure. */
nx_secure_tls_session_create(&tls_session,
                              &nx_crypto_tls_ciphers,
                              crypto_metadata,
                              sizeof(crypto_metadata));

/* Setup the TLS packet reassembly buffer. */
status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                 sizeof(tls_packet_buffer));

/* Initialize a certificate for the TLS server. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data, 500,
NX_NULL, 0, private_key, 64);

/* If status is NX_SUCCESS, certificate is initialized. */

/* Add the certificate a local certificate to identify this TLS server. */
status = nx_secure_tls_add_local_certificate(&tls_session, &certificate);

/* If status is NX_SUCCESS, certificate was added successfully. */

/* Create and start a TCP socket as a server. */
/* NOTE: This assumes an IP instance called “ip_0” has already been created. */

/* Create a TCP server socket on the previously created IP instance, with normal
   delivery, IP fragmentation enabled, default time to live, a 8192-byte receive
   window, no urgent callback routine, and the "client_disconnect" routine to
   handle disconnection initiated from the other end of the connection.  */
status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket", NX_IP_NORMAL,
                               NX_FRAGMENT_OKAY, NX_IP_TIME_TO_LIVE, 8192, NX_NULL,
                               NX_NULL);

/* If status is NX_SUCCESS, the TCP socket was created successfully. */

/* Start up a TCP server socket by listening on port 443 with a listen queue of
   size 5. */
status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

/* Application main loop. */
while(1)
{
        /* Accept incoming requests on the TCP socket. */
        status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

        /* At this point, the TCP socket should be established (but not the TLS
        session yet). */

        /* Start the TLS session on our active TCP socket. */
        status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                             NX_WAIT_FOREVER);

        /* At this point, if status is NX_SUCCESS, the TLS session has been
           established.  Application may now send/receive data through this
           channel. */

        /* Send and receive data using the TLS session. */
        /* Allocate TLS packets using nx_secure_tls_packet_allocate, write data with
           nx_packet_data_append, read data with nx_packet_data_extract_offset. */

        /* Send TLS data. */
        nx_secure_tls_session_send(&tls_session, &send_packet, NX_WAIT_FOREVER);

        nx_secure_tls_session_receive(&tls_session, &receive_packet_ptr,
        NX_WAIT_FOREVER);


        /* Once all application data is sent/received, end the TLS session. */
        status = nx_secure_tls_session_end(&tls_session);

        /* If status is NX_SUCCESS, the TLS session has been closed properly. */

        /* Now disconnect the TCP server socket from the client.  */
        nx_tcp_socket_disconnect(&tcp_socket, 200);

        /* Unaccept the TCP server socket.  Note that unaccept is called even if
           disconnect or accept fails.  */
        nx_tcp_server_socket_unaccept(&tcp_socket);

        /* Setup server socket for listening with this socket again.  */
        nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
}

/* When the server application is shut down, clean up the TLS session. */
nx_secure_tls_session_delete(&tls_session);

/* Finally, clean up the TCP socket as well. */
nx_tcp_socket_delete(&tcp_socket);
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1269">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1269">See Also</span></span>

- <span data-ttu-id="f21e6-1270">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-1270">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="f21e6-1271">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-1271">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-1272">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-1272">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-1273">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="f21e6-1273">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="f21e6-1274">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="f21e6-1274">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="f21e6-1275">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-1275">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="f21e6-1276">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-1276">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="f21e6-1277">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="f21e6-1277">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="f21e6-1278">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-1278">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-1279">nx_tcp_socket_accept</span><span class="sxs-lookup"><span data-stu-id="f21e6-1279">nx_tcp_socket_accept</span></span>
- <span data-ttu-id="f21e6-1280">nx_tcp_socket_listen</span><span class="sxs-lookup"><span data-stu-id="f21e6-1280">nx_tcp_socket_listen</span></span>
- <span data-ttu-id="f21e6-1281">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="f21e6-1281">nx_tcp_socket_disconnect</span></span>
- <span data-ttu-id="f21e6-1282">nx_tcp_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="f21e6-1282">nx_tcp_socket_unaccept</span></span>
- <span data-ttu-id="f21e6-1283">nx_tcp_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="f21e6-1283">nx_tcp_socket_relisten</span></span>
- <span data-ttu-id="f21e6-1284">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="f21e6-1284">nx_tcp_socket_delete</span></span>
- <span data-ttu-id="f21e6-1285">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-1285">nx_packet_allocate</span></span>
- <span data-ttu-id="f21e6-1286">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="f21e6-1286">nx_packet_data_append</span></span>
- <span data-ttu-id="f21e6-1287">nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="f21e6-1287">nx_packet_data_extract_offset</span></span>

## <a name="nx_secure_tls_session_time_function_set"></a><span data-ttu-id="f21e6-1288">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-1288">nx_secure_tls_session_time_function_set</span></span>

<span data-ttu-id="f21e6-1289">NetX Secure TLS セッションにタイムスタンプ関数を割り当てます</span><span class="sxs-lookup"><span data-stu-id="f21e6-1289">Assign a timestamp function to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1290">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1290">Prototype</span></span>

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a><span data-ttu-id="f21e6-1291">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1291">Description</span></span>

<span data-ttu-id="f21e6-1292">この関数は、TLS が現在の時刻を取得する必要があるときに呼び出す関数ポインターを設定します。これは、さまざまな TLS ハンドシェイク メッセージ内で、また、証明書を検証するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1292">This function sets up a function pointer that TLS will invoke when it needs to get the current time, which is used in various TLS handshake messages and for verification of certificates.</span></span>

<span data-ttu-id="f21e6-1293">この関数は、TLS RFC 5246 内の ClientHello の要件に従って、UNIX 32 ビット形式で現在の GMT （UTC 1970 年 1 月 1 日午前 0 時からの秒数、うるう秒は無視） を返すことが想定されています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1293">The function is expected to return the current GMT in UNIX 32-bit format (seconds since the midnight starting Jan 1, 1970, UTC, ignoring leap seconds), as per the ClientHello requirements in the TLS RFC 5246.</span></span>

<span data-ttu-id="f21e6-1294">タイムスタンプ関数が割り当てられていない場合は、TLS ハンドシェイク内のタイムスタンプに対して値 0 が使用され、証明書の有効期限の確認は機能しません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1294">If no timestamp function is assigned, a value of 0 for the timestamp in the TLS handshake will be used and certificate expiration checking will not work.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1295">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1295">Parameters</span></span>

- <span data-ttu-id="f21e6-1296">**session_ptr** TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1296">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-1297">**time_func_ptr** UNIX 32 ビット形式で現在の時刻 （GMT） を返す関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1297">**time_func_ptr** Pointer to a function that returns the current time (GMT) in UNIX 32-bit format.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1298">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1298">Return Values</span></span>

- <span data-ttu-id="f21e6-1299">**NX_SUCCESS** （0x00） TLS セッションの初期化に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1299">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="f21e6-1300">**NX_INVALID_PARAMETERS** （0x4D） 無効な TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1300">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="f21e6-1301">**NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1301">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1302">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1302">Allowed From</span></span>

<span data-ttu-id="f21e6-1303">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1303">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1304">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1304">Example</span></span>

```C
/* This function returns a 32-bit UNIX-style representation of the current GMT
   time. */
ULONG get_gmt_time(void)
{
ULONG time_value;

   /* Platform-specific time calculation goes here… */

   return(time_value);
}

/* Reset a TLS session.  */
status =  nx_secure_tls_timestamp_function_set(&tls_session, get_gmt_time);


/* If status is NX_SUCCESS the function was successfully added.*/
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1305">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1305">See Also</span></span>

- <span data-ttu-id="f21e6-1306">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-1306">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-1307">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-1307">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-1308">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="f21e6-1308">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="f21e6-1309">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="f21e6-1309">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="f21e6-1310">nx_secure_tls_session_sendnx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="f21e6-1310">nx_secure_tls_session_sendnx_secure_tls_session_receive</span></span>
- <span data-ttu-id="f21e6-1311">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-1311">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_trusted_certificate_add"></a><span data-ttu-id="f21e6-1312">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-1312">nx_secure_tls_trusted_certificate_add</span></span>

<span data-ttu-id="f21e6-1313">信頼された証明書を NetX Secure TLS セッションに追加します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1313">Add trusted certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1314">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1314">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="f21e6-1315">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1315">Description</span></span>

<span data-ttu-id="f21e6-1316">このサービスは、初期化された NX_SECURE_X509_CERT 構造体インスタンスを、TLS セッションに追加します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1316">This service adds an initialized NX_SECURE_X509_CERT structure instance to a TLS session.</span></span> <span data-ttu-id="f21e6-1317">TLS スタックはこの証明書を使用して、TLS ハンドシェイク中にリモート ホストによって提供される証明書を検証します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1317">This certificate is used by the TLS stack to verify certificates supplied by the remote host during the TLS handshake.</span></span>

<span data-ttu-id="f21e6-1318">TLS クライアント モードの場合は、信頼された証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1318">Trusted certificates are required for TLS Client mode.</span></span>

<span data-ttu-id="f21e6-1319">TLS サーバー モードの場合は、クライアント証明書認証が有効になっているときにのみ、信頼された証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1319">Trusted certificates are only required for TLS Server mode if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1320">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1320">Parameters</span></span>

- <span data-ttu-id="f21e6-1321">**session_ptr** 前に作成した TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1321">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-1322">**certificate_ptr** 初期化された TLS 証明書インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1322">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1323">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1323">Return Values</span></span>

- <span data-ttu-id="f21e6-1324">**NX_SUCCESS** （0x00） 証明書の追加に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1324">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="f21e6-1325">**NX_INVALID_PARAMETERS** （0x4D） 無効な証明書を追加しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1325">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>
- <span data-ttu-id="f21e6-1326">**NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1326">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1327">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1327">Allowed From</span></span>

<span data-ttu-id="f21e6-1328">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1329">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1329">Example</span></span>

```C
/* Initialize certificate structure. */
status = nx_secure_x509_certificate_initialize(&certificate, certificate_data,
                                               certificate_buffer,
                                               sizeof(certificate_buffer), 500,
                                               private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1330">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1330">See Also</span></span>

- <span data-ttu-id="f21e6-1331">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-1331">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-1332">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-1332">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-1333">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-1333">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-1334">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="f21e6-1334">nx_secure_tls_trusted_certificate_remove</span></span>

## <a name="nx_secure_tls_trusted_certificate_remove"></a><span data-ttu-id="f21e6-1335">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="f21e6-1335">nx_secure_tls_trusted_certificate_remove</span></span>

<span data-ttu-id="f21e6-1336">信頼された証明書を NetX Secure TLS セッションから削除します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1336">Remove trusted certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1337">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1337">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a><span data-ttu-id="f21e6-1338">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1338">Description</span></span>

<span data-ttu-id="f21e6-1339">このサービスは、証明書の共通名フィールドをキーとして、信頼された証明書を TLS セッションから削除します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1339">This service removes a trusted certificate from a TLS session, keyed on the Common Name field in the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1340">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1340">Parameters</span></span>

- <span data-ttu-id="f21e6-1341">**session_ptr** 前に作成した TLS セッション インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1341">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="f21e6-1342">**common_name** 削除する証明書の共通名の値。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1342">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="f21e6-1343">**common_name_length** 共通名の文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1343">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1344">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1344">Return Values</span></span>

- <span data-ttu-id="f21e6-1345">**NX_SUCCESS** （0x00） 証明書の追加に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1345">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="f21e6-1346">**NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1346">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="f21e6-1347">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** （0x119） 証明書が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1347">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1348">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1348">Allowed From</span></span>

<span data-ttu-id="f21e6-1349">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1350">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1350">Example</span></span>

```C
/* Remove certificate from TLS session.  */
status =  nx_secure_tls_trusted_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1351">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1351">See Also</span></span>

- <span data-ttu-id="f21e6-1352">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-1352">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="f21e6-1353">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-1353">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-1354">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-1354">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-1355">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-1355">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_x509_certificate_initialize"></a><span data-ttu-id="f21e6-1356">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-1356">nx_secure_x509_certificate_initialize</span></span>

<span data-ttu-id="f21e6-1357">NetX Secure TLS 用の X.509 証明書を初期化します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1357">Initialize X.509 Certificate for NetX Secure TLS</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1358">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1358">Prototype</span></span>

```C
UINT  nx_secure_x509_certificate_initialize(
                  NX_SECURE_X509_CERT *certificate_ptr,
                  const UCHAR *certificate_data,
                  USHORT certificate_data_length,
                  UCHAR *raw_data_buffer,
                  USHORT buffer_size,
                  const UCHAR *private_key_data,
                  USHORT private_key_data_length,
                  UINT private_key_type);
```

### <a name="description"></a><span data-ttu-id="f21e6-1359">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1359">Description</span></span>

<span data-ttu-id="f21e6-1360">このサービスは、TLS セッションで使用するために、バイナリエンコードされた X.509 デジタル証明書から NX_SECURE_X509_CERT 構造体を初期化します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1360">This service initializes an NX_SECURE_X509_CERT structure from a binary-encoded X.509 digital certificate for use in a TLS session.</span></span>

<span data-ttu-id="f21e6-1361">証明書データは、DER でエンコードされたバイナリ形式の有効な X.509 デジタル証明書である **必要があります**。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1361">The certificate data **must** be a valid X.509 digital certificate in DER-encoded binary format.</span></span> <span data-ttu-id="f21e6-1362">データは、そのデータへの UCHAR ポインターが提供されていれば、どのようなソース （ファイル システム、コンパイル済みの定数バッファーなど） のものでも構いません。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1362">The data can some from any source (e.g. file system, compiled constant buffer, etc.) as long as a UCHAR pointer to that data is provided.</span></span>

<span data-ttu-id="f21e6-1363">*raw_data_buffer* パラメーターとそのサイズは、解析前に証明書データがコピーされる専用バッファーを指定する省略可能なパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1363">The *raw_data_buffer* parameter and its size are optional parameters that specify a dedicated buffer into which the certificate data is copied before parsing.</span></span> <span data-ttu-id="f21e6-1364">raw_data_buffer が NX_NULL として渡された場合、NX_SECURE_X509_CERT 構造体は、certificate_data 配列を直接指します （この場合、buffer_size は無視されます）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1364">If raw_data_buffer is passed as NX_NULL then the NX_SECURE_X509_CERT structure will point directly into the certificate_data array (buffer_size is ignored in this case).</span></span> <span data-ttu-id="f21e6-1365">raw_data_buffer が NX_NULL として渡された場合は、certificate_data ポインターが指すデータを変更 ***しないでください***。そうしないと証明書の処理が失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1365">If raw_data_buffer is passed as NX_NULL, ***do not*** modify the data pointed to by the certificate_data pointer or certificate processing will likely fail!</span></span>

<span data-ttu-id="f21e6-1366">秘密キー パラメーターはローカル ID 証明書のためのものです。サーバーは秘密キーを使用して、クライアントから受信するキー データ （サーバーの公開キーを使用して暗号化されたもの） を解読し、クライアントは、秘密キーを使用して、サーバーがクライアント証明書を要求したときに、サーバーに対して自身の ID を証明するために使用します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1366">The private key parameter is for local identity certificates – the private key is used by servers to decrypt the incoming key data from a client (encrypted using the server's public key) and by clients to verify their identity to a server when the server requests a client certificate.</span></span> <span data-ttu-id="f21e6-1367">この API を使用して秘密キーを追加すると、関連付けられている証明書が、TLS アプリケーションの ID 証明書として自動的にマークされます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1367">Adding a private key with this API will automatically mark the associated certificate as being an identity certificate for a TLS application.</span></span> <span data-ttu-id="f21e6-1368">他の目的 （信頼されたストアなど） のために証明書を初期化する場合は、*private_key_data* パラメーターを NULL として、*private_key_data_length* を 0 として、また *private_key_type* を NX_SECURE_X509_KEY_TYPE_NONE として渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1368">When initializing certificates for other purposes (e.g. the trusted store), the *private_key_data* parameter should be passed as NULL, the *private_key_data_length* as 0, and the *private_key_type* should be passed as NX_SECURE_X509_KEY_TYPE_NONE.</span></span>

<span data-ttu-id="f21e6-1369">*private_key_type* パラメーターは、秘密キーの形式を示します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1369">The *private_key_type* parameter indicates the formatting of the private key.</span></span> <span data-ttu-id="f21e6-1370">たとえば、秘密キーが DER でエンコードされた PKCS#1 形式の RSA 秘密キーである場合は、private_key_type を NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER として渡す必要があります。これは NetX Secure の既知の種類で、すぐに解析され、後で使用するために保存されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1370">For example, if the private key is a DER-encoded PKCS#1-format RSA private key, the private_key_type should be passed as NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, a type known to NetX Secure which will be parsed immediately and saved for later use.</span></span>

<span data-ttu-id="f21e6-1371">private_key_type は、特定のキー形式やその他のニーズを持つプラットフォームやアプリケーションに対応するために、ユーザー定義のキーの種類<sup>23</sup> もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1371">The private_key_type also supports user-defined key types<sup>23</sup> for platforms and applications that have specific key formats or other needs.</span></span> <span data-ttu-id="f21e6-1372">たとえば、NetX Secure ソフトウェアによって認識されない特定の形式が、ハードウェアベースの暗号化エンジンによって使用されている場合があります。また、秘密キーは、トラステッド プラットフォーム モジュール （TPM） や PKCS#11 暗号化ハードウェアのように、暗号化トークンによって暗号化または表される場合があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1372">For example, a hardware-based encryption engine may use a specific format not understood by the NetX Secure software, or a private key may be encrypted or represented by a cryptographic token as might be the case with a Trusted Platform Module (TPM) or PKCS#11 cryptographic hardware.</span></span> <span data-ttu-id="f21e6-1373">ユーザー定義のキーの種類を使用すると、キー データは適切な暗号化ルーチンにそのまま渡されます。たとえば、RSA 秘密キーは、解析や処理を行わずに、暗号スイート テーブル内の TLS に提供された RSA 暗号化ルーチンに直接渡されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1373">When a user-defined key type is used, the key data is passed verbatim to the appropriate cryptographic routine - for example, an RSA private key would be passed, without any parsing or processing, directly to the RSA cryptographic routine provided to TLS in the ciphersuite table.</span></span> <span data-ttu-id="f21e6-1374">また、ユーザー定義のキーの種類も暗号化ルーチンに渡されます （RSA の場合、これは 「op」 パラメーターです）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1374">The user-defined key type is also passed to the cryptographic routine (in the case of RSA, this is the "op" parameter).</span></span>

<span data-ttu-id="f21e6-1375">ユーザー定義キーの範囲は、0x0001 0000-0xFFFF FFFF から、32 ビット符号なし整数の上半分を対象としています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1375">The range of user-defined keys covers the top half of a 32-bit unsigned integer, from 0x0001 0000-0xFFFF FFFF.</span></span> <span data-ttu-id="f21e6-1376">0x0001 0000 未満の値は、NetX Secure use 用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1376">Values less than 0x0001 0000 are reserved for NetX Secure use.</span></span>

<span data-ttu-id="f21e6-1377">ユーザー定義のキーの種類は、秘密キーの生データを処理するためのカスタム暗号化ルーチンを必要とする高度な機能です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1377">User-defined key types are an advanced feature that requires custom cryptographic routines to handle the raw private key data.</span></span> <span data-ttu-id="f21e6-1378">この機能が必要な場合は、Express Logic の担当者にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1378">Please contact your Express Logic representative if you have need of this feature.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1379">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1379">Parameters</span></span>

- <span data-ttu-id="f21e6-1380">**certificate_ptr** 初期化されていない X.509 証明書インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1380">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="f21e6-1381">**certificate_data** DER でエンコードされた X.509 バイナリ データへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1381">**certificate_data** Pointer to DER-encoded X.509 binary data.</span></span>
- <span data-ttu-id="f21e6-1382">**raw_data_buffer** オプションの専用証明書データ バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1382">**raw_data_buffer** Pointer to optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="f21e6-1383">**buffer_size** オプションの専用証明書データ バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1383">**buffer_size** Size of optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="f21e6-1384">**certificate_data_length** 証明書のバイナリ データの長さ （バイト単位）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1384">**certificate_data_length** Length of certificate binary data in bytes.</span></span>
- <span data-ttu-id="f21e6-1385">**private_key_data** オプションの秘密キー データへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1385">**private_key_data** Pointer to optional private key data.</span></span>
- <span data-ttu-id="f21e6-1386">**private_key_data_length** 秘密キー データの長さ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1386">**private_key_data_length** Length of private key data.</span></span>
- <span data-ttu-id="f21e6-1387">**private_key_type** キーの種類の識別子。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1387">**private_key_type** Key type identifier.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1388">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1388">Return Values</span></span>

- <span data-ttu-id="f21e6-1389">**NX_SUCCESS** （0x00） 証明書の追加に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1389">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="f21e6-1390">**NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1390">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="f21e6-1391">**NX_SECURE_TLS_INVALID_CERTIFICATE** （0x112） 証明書データに DER でエンコードされた X.509 証明書が含まれていませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1391">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Certificate data did not contain a DER-encoded X.509 certificate.</span></span>
- <span data-ttu-id="f21e6-1392">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** （0x10D） 証明書に、NetX Secure によってサポートされている公開キー暗号がありませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1392">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Certificate did not have a public-key cipher that is supported by NetX Secure.</span></span>
- <span data-ttu-id="f21e6-1393">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** （0x186） 秘密キーまたは証明書に、有効な ASN.1 シーケンスが含まれていませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1393">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) Private key or certificate did not contain a valid ASN.1 sequence.</span></span>
- <span data-ttu-id="f21e6-1394">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** （0x18A） 指定された秘密キーは、有効な PKCS#1 RSA キーではありませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1394">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) The provided private key was not a valid PKCS#1 RSA key.</span></span>
- <span data-ttu-id="f21e6-1395">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** （0x19D） 指定された秘密キーの種類は、ユーザー定義ではなく、既知の種類と一致しませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1395">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) The private key type provided was not user-defined and did not match any known type.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1396">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1396">Allowed From</span></span>

<span data-ttu-id="f21e6-1397">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1398">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1398">Example</span></span>

```C
/* Initialize certificate structure. The certificate structure will point directly
   into the certificate_data array since we are passing the raw_data_buffer as
   NX_NULL. This certificate has a private key so it will be used to identify this
   device. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, NX_NULL, 0, private_key, 64, NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);


/* If status is NX_SUCCESS the certificate was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1399">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1399">See Also</span></span>

- <span data-ttu-id="f21e6-1400">nx_secure_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="f21e6-1400">nx_secure_local_certificate_add</span></span>
- <span data-ttu-id="f21e6-1401">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-1401">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-1402">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="f21e6-1402">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="f21e6-1403">第 3 章の「X.509 証明書を NetX Secure にインポートする」</span><span class="sxs-lookup"><span data-stu-id="f21e6-1403">Importing X.509 Certificates into NetX Secure in Chapter 3.</span></span>

## <a name="nx_secure_x509_common_name_dns_check"></a><span data-ttu-id="f21e6-1404">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="f21e6-1404">nx_secure_x509_common_name_dns_check</span></span>

<span data-ttu-id="f21e6-1405">DNS 名を X.509 証明書と照合して確認します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1405">Check DNS name against X.509 Certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1406">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1406">Prototype</span></span>

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a><span data-ttu-id="f21e6-1407">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1407">Description</span></span>

<span data-ttu-id="f21e6-1408">このサービスは、リモート ホストの DNS 検証の目的で、証明書の共通名を、呼び出し元によって提供されたトップドメイン名 （TLD） と照合して確認します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1408">This service checks a certificate's Common Name against a Top- Domain name (TLD) provided by the caller for the purposes of DNS validation of a remote host.</span></span> <span data-ttu-id="f21e6-1409">このユーティリティ関数は、アプリケーションによって提供された証明書検証コールバック ルーチン内から呼び出されるように意図されています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1409">This utility function is intended to be called from within a certificate validation callback routine provided by the application.</span></span> <span data-ttu-id="f21e6-1410">TLD 名は、リモート ホストへのアクセスに使用された URL の先頭部分 （最初のスラッシュの前の 「. 」 で区切られた文字列） です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1410">The TLD name should be the top part of the URL used to access the remote host (the "."-separated string before the first slash).</span></span> <span data-ttu-id="f21e6-1411">共通名にワイルドカード （ *.example.com など） が含まれる場合、そのワイルドカードは、同じサフィックスを持つものと一致します。ワイルドカード照合では、最初のワイルドカード （「* 」） のみが考慮されることに注意してください （右から左に読み取り）。たとえば、abc.\*.exampl.com は、末尾が 「.example.com」 の *すべて*」 の名前と一致します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1411">If the Common Name contains a wildcard (such as *.example.com), the wildcard will match any with the same suffix. Note that only the first wildcard ("*") encountered (reading right-to-left) will be considered for wildcard matching – for example, abc.\*.example.com will match *any* name ending in ".example.com".</span></span>

<span data-ttu-id="f21e6-1412">指定された文字列と共通名が一致しない場合は、「subjectAltName」 拡張機能が解析され （証明書に存在する場合）、さらに DNSName エントリも比較されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1412">If the Common Name does not match the provided string, the "subjectAltName" extension is parsed (if it exists in the certificate) and any DNSName entries are also compared.</span></span> <span data-ttu-id="f21e6-1413">一致するエントリがない場合は、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1413">If none of those entries match, an error is returned.</span></span>

<span data-ttu-id="f21e6-1414">予想される証明書内の共通名 （および subjectAltName エントリ） の形式を理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1414">It is important to understand the format of the common name (and subjectAltName entries) in expected certificates.</span></span> <span data-ttu-id="f21e6-1415">たとえば、証明書によっては、生 IP アドレスまたはワイルド カードが使用されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1415">For example, some certificates may use a raw IP address or a wild card.</span></span> <span data-ttu-id="f21e6-1416">DNS TLD 文字列は、受信した証明書内の予期される値と一致するように書式設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1416">The DNS TLD string must be formatted such that it will match the expected values in received certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1417">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1417">Parameters</span></span>

- <span data-ttu-id="f21e6-1418">**certificate_ptr** X.509 証明書インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1418">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>
- <span data-ttu-id="f21e6-1419">**dns_tld** 比較対象となる最上位レベルのドメイン名。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1419">**dns_tld** Top-Level Domain name to compare against.</span></span>
- <span data-ttu-id="f21e6-1420">**dns_tld_length** TLD 文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1420">**dns_tld_length** Length of TLD string.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1421">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1421">Return Values</span></span>

- <span data-ttu-id="f21e6-1422">**NX_SUCCESS** （0x00） 共通名または subjectAltName との比較に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1422">**NX_SUCCESS** (0x00) Successful comparison with Common Name or subjectAltName.</span></span>
- <span data-ttu-id="f21e6-1423">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** （0x195） 一致する名前が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1423">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) No matching name found.</span></span>
- <span data-ttu-id="f21e6-1424">**NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1424">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1425">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1425">Allowed From</span></span>

<span data-ttu-id="f21e6-1426">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1426">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1427">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1427">Example</span></span>

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
UCHAR *tld = “www.example.com”;

    /* Check our DNS TLD against the certificate provided by the
       remote TLS host. */
    status = nx_secure_x509_common_name_dns_check(certificate, tld, strlen(tld));

        if(status != NX_SUCCESS)
        {
            /* TLD did not match any names in the certificate. */
            return(status);
        }

        /* DNS validation and any other checks were successful. */
        return(NX_SUCCESS);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1428">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1428">See Also</span></span>

- <span data-ttu-id="f21e6-1429">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-1429">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-1430">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-1430">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="f21e6-1431">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="f21e6-1431">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_x509_crl_revocation_check"></a><span data-ttu-id="f21e6-1432">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="f21e6-1432">nx_secure_x509_crl_revocation_check</span></span>

<span data-ttu-id="f21e6-1433">X.509 証明書を指定された証明書失効リスト （CRL） と照合して確認します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1433">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1434">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1434">Prototype</span></span>

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="f21e6-1435">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1435">Description</span></span>

<span data-ttu-id="f21e6-1436">このサービスは、DER でエンコードされた証明書失効リストを取得し、そのリスト内で特定の証明書を検索します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1436">This service takes a DER-encoded Certificate Revocation List and searches for a specific certificate in that list.</span></span> <span data-ttu-id="f21e6-1437">CRL の発行者は、指定された証明書ストアに対して検証されます。CRL の発行者は、確認対象の証明書の発行者と同じであることが検証され、該当する証明書のシリアル番号を使用して、失効証明書リストが検索されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1437">The issuer of the CRL is validated against a supplied certificate store, the CRL issuer is validated to be the same as the one for the certificate being checked, and the serial number of the certificate in question is used to search the revoked certificates list.</span></span> <span data-ttu-id="f21e6-1438">発行者が一致し、署名がチェックアウトされ、証明書がリストに存在 **しない** 場合、呼び出しは成功します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1438">If the issuers match, the signature checks out, and the certificate is **not** present in the list, the call is successful.</span></span> <span data-ttu-id="f21e6-1439">それ以外の場合は、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1439">All other cases cause an error to be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1440">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1440">Parameters</span></span>

- <span data-ttu-id="f21e6-1441">**crl_data** DER でエンコードされた CRL へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1441">**crl_data** Pointer to a DER-encoded CRL.</span></span>
- <span data-ttu-id="f21e6-1442">**crl_length** CRL データの長さ （バイト単位）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1442">**crl_length** Length in bytes of CRL data.</span></span>
- <span data-ttu-id="f21e6-1443">**store** X.509 証明書ストアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1443">**store** Pointer to an X.509 Certificate store.</span></span>
- <span data-ttu-id="f21e6-1444">**certificate_ptr** X.509 証明書インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1444">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1445">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1445">Return Values</span></span>

- <span data-ttu-id="f21e6-1446">**NX_SUCCESS** （0x00） 証明書が失効していないことの検証に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1446">**NX_SUCCESS** (0x00) Successful validation that the certificate was not revoked.</span></span>
- <span data-ttu-id="f21e6-1447">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** （0x119） CRL の発行者が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1447">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) CRL issuer certificate not found.</span></span>
- <span data-ttu-id="f21e6-1448">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** （0x11B） 証明書の発行者が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1448">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Certificate issuer certificate not found.</span></span>
- <span data-ttu-id="f21e6-1449">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** （0x182） CRL ASN.1 に無効な長さのフィールドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1449">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) The CRL ASN.1 contained an invalid length field.</span></span>
- <span data-ttu-id="f21e6-1450">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG （0x189）** CRL に無効な ASN.1 が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1450">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** The CRL contained invalid ASN.1.</span></span>
- <span data-ttu-id="f21e6-1451">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** （0x18C） 証明書チェーンの検証に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1451">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) A certificate chain verification failed.</span></span>
- <span data-ttu-id="f21e6-1452">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** （0x197） CRL と証明書の発行者が一致しませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1452">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) CRL and certificate issuers did not match.</span></span>
- <span data-ttu-id="f21e6-1453">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** （0x198） CRL の署名が無効でした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1453">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) The CRL signature was invalid.</span></span>
- <span data-ttu-id="f21e6-1454">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** （0x199） 確認対象の証明書は、CRL 内に見つかったため失効します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1454">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) The certificate being checked was found in the CRL and is therefore revoked.</span></span>
- <span data-ttu-id="f21e6-1455">**NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1455">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1456">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1456">Allowed From</span></span>

<span data-ttu-id="f21e6-1457">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1457">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1458">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1458">Example</span></span>

```C
/* CRL obtained for the expected certificate issuer through some means (downloaded
   from server manually, obtained from CRL endpoint, etc…) */
const UCHAR *crl_data;
UINT crl_length = 300;

/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
NX_SECURE_X509_CERTIFICATE_STORE *store;

    /* Obtain a certificate store to check against. In the certificate callback,
       it usually makes the most sense to use the store associated with the TLS
       session. */
    store = &session -> nx_secure_tls_credentials.nx_secure_tls_certificate_store;

    /* Check our certificate against the CRL and TLS certificate store. */
    status = nx_secure_x509_crl_revocation_check(crl, crl_length, store,
                                                 certificate);

        if(status != NX_SUCCESS)
        {
            if(status == NX_SECURE_X509_CRL_CERTIFICATE_REVOKED)
            {
                /* Certificate was revoked. */
               return(status);
            }
            else
            {
               /* CRL was invalid or some other issue. In this case the certificate
                  may still be valid since the CRL itself was a problem. At this
                  point it is up to the application to decide whether to continue
                  with the TLS handshake. For this example, assume certificate is
                  valid (faulty CRL is a possible Denial-of-Service attack).*/
               status = NX_SUCCESS;
        }

    /* Other certificate checking can go here. */

    /* Return status of certificate checks. */
    return(status);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1459">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1459">See Also</span></span>

- <span data-ttu-id="f21e6-1460">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-1460">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-1461">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-1461">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="f21e6-1462">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="f21e6-1462">nx_secure_x509_common_name_dns_check</span></span>

## <a name="nx_secure_x509_dns_name_initialize"></a><span data-ttu-id="f21e6-1463">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="f21e6-1463">nx_secure_x509_dns_name_initialize</span></span>

<span data-ttu-id="f21e6-1464">X.509 DNS 名の構造体を初期化します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1464">Initialize an X.509 DNS name structure</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1465">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1465">Prototype</span></span>

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a><span data-ttu-id="f21e6-1466">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1466">Description</span></span>

<span data-ttu-id="f21e6-1467">このサービスは、特定の名前形式を必要とする特定の API サービスで使用するために、X.509 DNS 名を初期化します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1467">This service initializes an X.509 DNS name for use with certain API services requiring a specific name format.</span></span> <span data-ttu-id="f21e6-1468">たとえば、*nx_secure_tls_sni_extension_parse* サービスは、TLS ハンドシェイク中にリモート ホストが Server Name Indication 拡張機能内で提供した名前と一致させるために、NX_SECURE_X509_DNS_NAME オブジェクトを期待します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1468">For example, the *nx_secure_tls_sni_extension_parse* service expects an NX_SECURE_X509_DNS_NAME object in order to match the name provided by a remote host in the Server Name Indication extension during the TLS handshake.</span></span> <span data-ttu-id="f21e6-1469">DNS 名は、長さを持つシンプルな文字列です。DNS 名の許容最大長 （および NX_SECURE_X509_DNS_NAME 内の内部バッファーのサイズ） は、マクロ NX_SECURE_X509_DNS_NAME_MAX によって制御されます （既定値は 100 バイト）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1469">A DNS name is simply a charater string with a length – the maximum allowed length of a DNS name (and the size of the internal buffer in NX_SECURE_X509_DNS_NAME) is controlled by the macro NX_SECURE_X509_DNS_NAME_MAX (default 100 bytes).</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1470">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1470">Parameters</span></span>

- <span data-ttu-id="f21e6-1471">**dns_name** 初期化する DNS 名の構造体。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1471">**dns_name** DNS name structure to initialize.</span></span>
- <span data-ttu-id="f21e6-1472">**name_string** DNS 名の文字列データ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1472">**name_string** DNS name string data.</span></span>
- <span data-ttu-id="f21e6-1473">**length** 名前の文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1473">**length** Length of name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1474">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1474">Return Values</span></span>

- <span data-ttu-id="f21e6-1475">**NX_SUCCESS** （0x00） 初期化に成功。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1475">**NX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="f21e6-1476">**NX_SECURE_X509_NAME_STRING_TOO_LONG** （0x19E） 指定された名前の文字列が NX_SECURE_X509_DNS_NAME_MAX を超えました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1476">**NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) The given name string exceeded NX_SECURE_X509_DNS_NAME_MAX.</span></span>
- <span data-ttu-id="f21e6-1477">**NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1477">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1478">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1478">Allowed From</span></span>

<span data-ttu-id="f21e6-1479">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1480">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1480">Example</span></span>

```C
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, “www.example.com”,
                                            strlen(“www.example.com”);

/* Use initialized DNS name to send the Server Name Indication extension to the
   remote TLS server. */
status = nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1481">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1481">See Also</span></span>

- <span data-ttu-id="f21e6-1482">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="f21e6-1482">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="f21e6-1483">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="f21e6-1483">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="f21e6-1484">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-1484">nx_secure_tls_session_sni_extension_set</span></span>

## <a name="nx_secure_x509_extended_key_usage_extension_parse"></a><span data-ttu-id="f21e6-1485">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="f21e6-1485">nx_secure_x509_extended_key_usage_extension_parse</span></span>

<span data-ttu-id="f21e6-1486">X.509 証明書内で X.509 拡張キー使用拡張機能を検索して解析します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1486">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1487">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1487">Prototype</span></span>

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a><span data-ttu-id="f21e6-1488">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1488">Description</span></span>

<span data-ttu-id="f21e6-1489">このサービスは、証明書の検証コールバック内から呼び出されるように意図されています （「*nx_secure_tls_session_certificate_callback_set*」をご覧ください）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1489">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="f21e6-1490">このメソッドは、X.509 証明書内で特定の拡張キー使用 OID を検索し、OID が存在するかどうかを返します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1490">It will search for a specific extended key usage OID within an X.509 certificate and return whether the OID is present.</span></span> <span data-ttu-id="f21e6-1491">key_usage パラメーターは OID の整数マッピングで、NetX Secure X.509 と TLS によって内部的に使用され、可変長 OID 文字列がパラメーターとして渡されないようにします。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1491">The key_usage parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="f21e6-1492">以下の表に、拡張キー使用拡張機能の関連する OID を示します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1492">The relevant OIDs for the extended key usage extension are given in the table below.</span></span> <span data-ttu-id="f21e6-1493">受信した TLS サーバー証明書内で拡張キー使用を確認する一般的な TLS クライアント実装は、OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH が存在するかどうかをチェックします。拡張機能が存在しても、OID が存在しない場合、証明書は、ホストを TLS サーバーとして特定するには無効と見なされ、証明書検証コールバックはエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1493">A typical TLS Client implementation wishing to check extended key usage in a received TLS server certificate would check for the existence of the OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH – if the extension is present but that OID is not, then the certificate would be considered invalid for identifiying the host as a TLS server and the certificate verification callback should return an error.</span></span> <span data-ttu-id="f21e6-1494">拡張機能自体がない場合は、TLS ハンドシェイクを続行するかどうかにかかわらず、アプリケーションによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1494">If the extension itself is missing, then it is up to the application whether or not to proceed with the TLS handshake.</span></span>

<span data-ttu-id="f21e6-1495">証明書の検証コールバックでは、エラー リターン コード NX_SECURE_X509_KEY_USAGE_ERROR は、アプリケーションの用途のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1495">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="f21e6-1496">キーの使用の確認中にエラーが発生した場合は、この値がコールバックから返され、エラーの原因を示すことがあります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1496">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="f21e6-1497">NetX Secure 識別子</span><span class="sxs-lookup"><span data-stu-id="f21e6-1497">NetX Secure Identifier</span></span>                                | <span data-ttu-id="f21e6-1498">OID 値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1498">OID Value</span></span>         | <span data-ttu-id="f21e6-1499">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1499">Description</span></span>                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| <span data-ttu-id="f21e6-1500">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span><span class="sxs-lookup"><span data-stu-id="f21e6-1500">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span></span>   | <span data-ttu-id="f21e6-1501">1.3.6.1.5.5.7.3.1</span><span class="sxs-lookup"><span data-stu-id="f21e6-1501">1.3.6.1.5.5.7.3.1</span></span> | <span data-ttu-id="f21e6-1502">証明書を使用して TLS サーバーの識別できます</span><span class="sxs-lookup"><span data-stu-id="f21e6-1502">Certificate can be used to identify a TLS server</span></span> |
| <span data-ttu-id="f21e6-1503">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span><span class="sxs-lookup"><span data-stu-id="f21e6-1503">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span></span>   | <span data-ttu-id="f21e6-1504">1.3.6.1.5.5.7.3.2</span><span class="sxs-lookup"><span data-stu-id="f21e6-1504">1.3.6.1.5.5.7.3.2</span></span> | <span data-ttu-id="f21e6-1505">証明書を使用して TLS クライアントを識別できます</span><span class="sxs-lookup"><span data-stu-id="f21e6-1505">Certificate can be used to identify a TLS client</span></span> |
| <span data-ttu-id="f21e6-1506">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span><span class="sxs-lookup"><span data-stu-id="f21e6-1506">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span></span>  | <span data-ttu-id="f21e6-1507">1.3.6.1.5.5.7.3.3</span><span class="sxs-lookup"><span data-stu-id="f21e6-1507">1.3.6.1.5.5.7.3.3</span></span> | <span data-ttu-id="f21e6-1508">証明書を使用してコードに署名できます</span><span class="sxs-lookup"><span data-stu-id="f21e6-1508">Certificate can be used to sign code</span></span>             |
| <span data-ttu-id="f21e6-1509">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span><span class="sxs-lookup"><span data-stu-id="f21e6-1509">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span></span> | <span data-ttu-id="f21e6-1510">1.3.6.1.5.5.7.3.4</span><span class="sxs-lookup"><span data-stu-id="f21e6-1510">1.3.6.1.5.5.7.3.4</span></span> | <span data-ttu-id="f21e6-1511">証明書を使用してメールに署名できます</span><span class="sxs-lookup"><span data-stu-id="f21e6-1511">Certificate can be used to sign emails</span></span>           |
| <span data-ttu-id="f21e6-1512">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span><span class="sxs-lookup"><span data-stu-id="f21e6-1512">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span></span> | <span data-ttu-id="f21e6-1513">1.3.6.1.5.5.7.3.8</span><span class="sxs-lookup"><span data-stu-id="f21e6-1513">1.3.6.1.5.5.7.3.8</span></span> | <span data-ttu-id="f21e6-1514">証明書を使用してタイムスタンプに署名できます</span><span class="sxs-lookup"><span data-stu-id="f21e6-1514">Certificate can be used to sign timestamps</span></span>       |
| <span data-ttu-id="f21e6-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span><span class="sxs-lookup"><span data-stu-id="f21e6-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span></span>  | <span data-ttu-id="f21e6-1516">1.3.6.1.5.5.7.3.9</span><span class="sxs-lookup"><span data-stu-id="f21e6-1516">1.3.6.1.5.5.7.3.9</span></span> | <span data-ttu-id="f21e6-1517">証明書を使用して OCSP 応答に署名できます</span><span class="sxs-lookup"><span data-stu-id="f21e6-1517">Certificate can be used to sign OCSP responses</span></span>   |

<span data-ttu-id="f21e6-1518">X.509 拡張キー使用拡張機能 の OID とマッピング</span><span class="sxs-lookup"><span data-stu-id="f21e6-1518">OIDs and mappings for X.509 Extended Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1519">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1519">Parameters</span></span>

- <span data-ttu-id="f21e6-1520">**certificate** 検証している証明書へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1520">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="f21e6-1521">**key_usage** 上記の表からの OID 整数のマッピング。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1521">**key_usage** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1522">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1522">Return Values</span></span>

- <span data-ttu-id="f21e6-1523">**NX_SUCCESS** （0x00） 指定されたキー使用 OID が見つかりました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1523">**NX_SUCCESS** (0x00) Specified key usage OID found.</span></span>
- <span data-ttu-id="f21e6-1524">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** （0x181） ASN.1 マルチバイト タグが見つかりました （サポートされていない証明書）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1524">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="f21e6-1525">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** （0x182） 無効な ASN.1 フィールドが見つかりました （無効な証明書）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1525">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="f21e6-1526">**NX_SECURE_X509_INVALID_TAG_CLASS** （0x190） 無効な ASN.1 タグ クラスが見つかりました （無効な証明書）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1526">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="f21e6-1527">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** （0x192） 無効な拡張機能が見つかりました （無効な証明書）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1527">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="f21e6-1528">**NX_SECURE_X509_EXTENSION_NOT_FOUND** （0x19B） 指定された証明書内に拡張キー使用拡張機能が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1528">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The Extended Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="f21e6-1529">**NX_PTR_ERROR** （0x07） 無効な証明書ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1529">**NX_PTR_ERROR** (0x07) Invalid certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1530">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1530">Allowed From</span></span>

<span data-ttu-id="f21e6-1531">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1531">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1532">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1532">Example</span></span>

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT* certificate)
{
UINT status;

    /* Extended key usage - look for specific OIDs. */
    status = nx_secure_x509_extended_key_usage_extension_parse(certificate,
                        NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH);

    if(status != NX_SUCCESS)
    {
        if(NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND)
        {
            printf("Extended key usage extension not found or specified key usage OID not
                    provided in extension.\n");
            /* The certificate was valid but the specified OID was not found. The
               application can decide whether to continue or abort the TLS handshake. */
            return(NX_SECURE_X509_KEY_USAGE_ERROR);
        }
        else
        {
            /* The extension or certificate was invalid. */
            return(status);
        }
    }

    /* The specified OID was found, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1533">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1533">See Also</span></span>

- <span data-ttu-id="f21e6-1534">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-1534">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="f21e6-1535">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="f21e6-1535">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="f21e6-1536">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="f21e6-1536">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="f21e6-1537">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="f21e6-1537">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="f21e6-1538">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="f21e6-1538">nx_secure_x509_extension_find</span></span>

## <a name="nx_secure_x509_extension_find"></a><span data-ttu-id="f21e6-1539">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="f21e6-1539">nx_secure_x509_extension_find</span></span>

<span data-ttu-id="f21e6-1540">X.509 証明書内で X.509 拡張機能を検索して返します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1540">Find and return an X.509 extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1541">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1541">Prototype</span></span>

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a><span data-ttu-id="f21e6-1542">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1542">Description</span></span>

<span data-ttu-id="f21e6-1543">このサービスは、証明書の検証コールバック内から呼び出されるように意図されています （「*nx_secure_tls_session_certificate_callback_set*」をご覧ください）。これは、高度な X.509 サービスです。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1543">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)* and is an advanced X.509 service.</span></span>

<span data-ttu-id="f21e6-1544">関数は、OID に基づいて X.509 証明書内で特定の拡張機能を検索し、OID が存在するかどうかを、関連する拡張機能の生データへの参照を含む構造体と共に返します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1544">The function will search for a specific extension within an X.509 certificate based on an OID and return whether the OID is present, along with a structure containing references to the relevant raw extension data.</span></span> <span data-ttu-id="f21e6-1545">extension_id パラメーターは OID の整数マッピングで、NetX Secure X.509 と TLS によって内部的に使用され、可変長 OID 文字列がパラメーターとして渡されないようにします。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1545">The extension_id parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="f21e6-1546">特定の拡張機能 （*nx_secure_x509_key_usage_extension_parse* など） 用に提供されるヘルパー関数は、拡張機能データを取得するために、内部的に nx_secure_x509_extension_find を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1546">The helper functions provided for specific extensions (such as *nx_secure_x509_key_usage_extension_parse*) call nx_secure_x509_extension_find internally to obtain the extension data.</span></span>

<span data-ttu-id="f21e6-1547">既知の X.509 拡張機能に関連する OID については、以下の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1547">The relevant OIDs for known X.509 extensions are given in the table below.</span></span>

<span data-ttu-id="f21e6-1548">NX_SECURE_X509_EXTENSION 構造体には、X.509 証明書へのポインターが含まれています。これを使用すると、*nx_secure_x509_key_usage_extension_parse* などのヘルパー関数が、DER でエンコードされた拡張機能の生 ASN.1 データをすばやくデコードできます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1548">The NX_SECURE_X509_EXTENSION structure contains pointers into the X.509 certificate that allow helper functions such as *nx_secure_x509_key_usage_extension_parse* to quickly decode the raw extension DER-encoded ASN.1 data.</span></span>

<span data-ttu-id="f21e6-1549">特定の拡張機能については、RFC 5280 （X.509 仕様） または適切なヘルパー関数のリファレンス （使用可能な場合） をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1549">For information on specific extensions, see RFC 5280 (X.509 specification) or the reference for the appropriate helper functions if available.</span></span>

<span data-ttu-id="f21e6-1550">現在のバージョンの NetX Secure X.509 では、X.509 拡張機能が制限付きでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1550">The current version of NetX Secure X.509 has limited support for X.509 extensions.</span></span> <span data-ttu-id="f21e6-1551">今後、さらにヘルパー関数が追加される予定です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1551">More helper functions will be added in the future.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f21e6-1552">*このサービスは、X.509 拡張機能と DER でエンコードされた ASN.1 に精通しているユーザー向けの高度な機能で、NetX Secure X.509 が現在ヘルパー関数を提供していない拡張機能に、これらのユーザーがアクセスできるようにするために用意されています。このようなヘルパー関数のない拡張機能については、DER でエンコードされた生の ASN.1 をご自身で解析する必要があります。*</span><span class="sxs-lookup"><span data-stu-id="f21e6-1552">*This service is an advanced feature for users familiar with X.509 extensions and DER-encoded ASN.1. It is provided to enable those users to access extensions for which NetX Secure X.509 does not currently provide helper functions. For those extensions without helper functions, you will have to parse the raw DER-encoded ASN.1 yourself.*</span></span>

| <span data-ttu-id="f21e6-1553">NetX Secure 識別子</span><span class="sxs-lookup"><span data-stu-id="f21e6-1553">NetX Secure Identifier</span></span>                              | <span data-ttu-id="f21e6-1554">OID 値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1554">OID Value</span></span> | <span data-ttu-id="f21e6-1555">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1555">Description</span></span>                                                                    | <span data-ttu-id="f21e6-1556">ヘルパー関数</span><span class="sxs-lookup"><span data-stu-id="f21e6-1556">Helper function?</span></span> |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| <span data-ttu-id="f21e6-1557">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span><span class="sxs-lookup"><span data-stu-id="f21e6-1557">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span></span>  | <span data-ttu-id="f21e6-1558">2.5.29.9</span><span class="sxs-lookup"><span data-stu-id="f21e6-1558">2.5.29.9</span></span>  | <span data-ttu-id="f21e6-1559">ディレクトリ属性 - 証明書のサブジェクトに関する基本情報の属性</span><span class="sxs-lookup"><span data-stu-id="f21e6-1559">Directory Attributes – basic information attributes about certificate subject</span></span>  | <span data-ttu-id="f21e6-1560">いいえ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1560">No</span></span>               |
| <span data-ttu-id="f21e6-1561">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="f21e6-1561">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span></span>       | <span data-ttu-id="f21e6-1562">2.5.29.14</span><span class="sxs-lookup"><span data-stu-id="f21e6-1562">2.5.29.14</span></span> | <span data-ttu-id="f21e6-1563">特定の公開キーを識別するために使用されます</span><span class="sxs-lookup"><span data-stu-id="f21e6-1563">Used to identify a specific public key</span></span>                                         | <span data-ttu-id="f21e6-1564">いいえ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1564">No</span></span>               |
| <span data-ttu-id="f21e6-1565">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="f21e6-1565">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span></span>             | <span data-ttu-id="f21e6-1566">2.5.29.15</span><span class="sxs-lookup"><span data-stu-id="f21e6-1566">2.5.29.15</span></span> | <span data-ttu-id="f21e6-1567">証明書の公開キーの有効な使用方法に関する情報を提供します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1567">Provides information on valid uses for the certificate public key</span></span>              | <span data-ttu-id="f21e6-1568">はい</span><span class="sxs-lookup"><span data-stu-id="f21e6-1568">Yes</span></span>              |
| <span data-ttu-id="f21e6-1569">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="f21e6-1569">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span></span>     | <span data-ttu-id="f21e6-1570">2.5.29.17</span><span class="sxs-lookup"><span data-stu-id="f21e6-1570">2.5.29.17</span></span> | <span data-ttu-id="f21e6-1571">証明書を識別するための代替 DNS 名を提供します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1571">Provides alternative DNS names to identify the certificate</span></span>                     | <span data-ttu-id="f21e6-1572">はい<sup>24</sup></span><span class="sxs-lookup"><span data-stu-id="f21e6-1572">Yes<sup>24</sup></span></span>        |
| <span data-ttu-id="f21e6-1573">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="f21e6-1573">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span></span>      | <span data-ttu-id="f21e6-1574">2.5.29.18</span><span class="sxs-lookup"><span data-stu-id="f21e6-1574">2.5.29.18</span></span> | <span data-ttu-id="f21e6-1575">証明書の発行者を識別するための代替 DNS 名を提供します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1575">Provides alternative DNS names to identify the certificate's issuer</span></span>            | <span data-ttu-id="f21e6-1576">いいえ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1576">No</span></span>               |
| <span data-ttu-id="f21e6-1577">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="f21e6-1577">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span></span>     | <span data-ttu-id="f21e6-1578">2.5.29.19</span><span class="sxs-lookup"><span data-stu-id="f21e6-1578">2.5.29.19</span></span> | <span data-ttu-id="f21e6-1579">基本証明書の使用に関する制約情報を提供します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1579">Provides basic certificate usage constraint information</span></span>                        | <span data-ttu-id="f21e6-1580">いいえ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1580">No</span></span>               |
| <span data-ttu-id="f21e6-1581">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="f21e6-1581">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span></span>      | <span data-ttu-id="f21e6-1582">2.5.29.30</span><span class="sxs-lookup"><span data-stu-id="f21e6-1582">2.5.29.30</span></span> | <span data-ttu-id="f21e6-1583">証明書名を特定のドメインに制限するために使用されます</span><span class="sxs-lookup"><span data-stu-id="f21e6-1583">Used to constrain certificate names to specific domains</span></span>                        | <span data-ttu-id="f21e6-1584">いいえ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1584">No</span></span>               |
| <span data-ttu-id="f21e6-1585">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="f21e6-1585">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span></span>      | <span data-ttu-id="f21e6-1586">2.5.29.31</span><span class="sxs-lookup"><span data-stu-id="f21e6-1586">2.5.29.31</span></span> | <span data-ttu-id="f21e6-1587">CRL 配布の URI を提供します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1587">Provides URIs for CRL distribution</span></span>                                             | <span data-ttu-id="f21e6-1588">いいえ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1588">No</span></span>               |
| <span data-ttu-id="f21e6-1589">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span><span class="sxs-lookup"><span data-stu-id="f21e6-1589">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span></span>  | <span data-ttu-id="f21e6-1590">2.5.29.32</span><span class="sxs-lookup"><span data-stu-id="f21e6-1590">2.5.29.32</span></span> | <span data-ttu-id="f21e6-1591">大規模な PKI システムの証明書ポリシーのリスト</span><span class="sxs-lookup"><span data-stu-id="f21e6-1591">List of certificate policies for large PKI systems</span></span>                             | <span data-ttu-id="f21e6-1592">いいえ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1592">No</span></span>               |
| <span data-ttu-id="f21e6-1593">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span><span class="sxs-lookup"><span data-stu-id="f21e6-1593">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span></span> | <span data-ttu-id="f21e6-1594">2.5.29.33</span><span class="sxs-lookup"><span data-stu-id="f21e6-1594">2.5.29.33</span></span> | <span data-ttu-id="f21e6-1595">CA 証明書ポリシーのリスト</span><span class="sxs-lookup"><span data-stu-id="f21e6-1595">List of CA certificate policies</span></span>                                                | <span data-ttu-id="f21e6-1596">いいえ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1596">No</span></span>               |
| <span data-ttu-id="f21e6-1597">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="f21e6-1597">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span></span>     | <span data-ttu-id="f21e6-1598">2.5.29.35</span><span class="sxs-lookup"><span data-stu-id="f21e6-1598">2.5.29.35</span></span> | <span data-ttu-id="f21e6-1599">証明書の署名に関連付けられている特定の公開キーを識別するために使用されます</span><span class="sxs-lookup"><span data-stu-id="f21e6-1599">Used to identify a specific public key associated with a certificate signature</span></span> | <span data-ttu-id="f21e6-1600">いいえ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1600">No</span></span>               |
| <span data-ttu-id="f21e6-1601">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="f21e6-1601">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span></span>    | <span data-ttu-id="f21e6-1602">2.5.29.36</span><span class="sxs-lookup"><span data-stu-id="f21e6-1602">2.5.29.36</span></span> | <span data-ttu-id="f21e6-1603">CA ポリシー制約</span><span class="sxs-lookup"><span data-stu-id="f21e6-1603">CA policy constraints</span></span>                                                          | <span data-ttu-id="f21e6-1604">いいえ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1604">No</span></span>               |
| <span data-ttu-id="f21e6-1605">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="f21e6-1605">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span></span>   | <span data-ttu-id="f21e6-1606">2.5.29.37</span><span class="sxs-lookup"><span data-stu-id="f21e6-1606">2.5.29.37</span></span> | <span data-ttu-id="f21e6-1607">追加 OID ベースのキー使用情報</span><span class="sxs-lookup"><span data-stu-id="f21e6-1607">Additional OID-based key usage information</span></span>                                     | <span data-ttu-id="f21e6-1608">はい</span><span class="sxs-lookup"><span data-stu-id="f21e6-1608">Yes</span></span>              |
| <span data-ttu-id="f21e6-1609">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span><span class="sxs-lookup"><span data-stu-id="f21e6-1609">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span></span>          | <span data-ttu-id="f21e6-1610">2.5.29.46</span><span class="sxs-lookup"><span data-stu-id="f21e6-1610">2.5.29.46</span></span> | <span data-ttu-id="f21e6-1611">Delta CRL を取得するための情報を提供します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1611">Provides information for obtaining delta CRLs</span></span>                                  | <span data-ttu-id="f21e6-1612">いいえ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1612">No</span></span>               |
| <span data-ttu-id="f21e6-1613">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span><span class="sxs-lookup"><span data-stu-id="f21e6-1613">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span></span>     | <span data-ttu-id="f21e6-1614">2.5.29.54</span><span class="sxs-lookup"><span data-stu-id="f21e6-1614">2.5.29.54</span></span> | <span data-ttu-id="f21e6-1615">AnyPolicy を使用できないことを示す CA 証明書フィールド</span><span class="sxs-lookup"><span data-stu-id="f21e6-1615">CA certificate field indicating that AnyPolicy cannot be used</span></span>                  | <span data-ttu-id="f21e6-1616">いいえ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1616">No</span></span>               |

<span data-ttu-id="f21e6-1617">X.509 拡張機能の OID とマッピング</span><span class="sxs-lookup"><span data-stu-id="f21e6-1617">OIDs and mappings for X.509 Extensions</span></span>

24. <span data-ttu-id="f21e6-1618">SubjectAltName 拡張機能は、サービス nx_secure_x509_common_name_dns_check 内で DNS 名チェックの一部として解析されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1618">The SubjectAltName extension is parsed as part of the DNS name check in the service nx_secure_x509_common_name_dns_check.</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1619">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1619">Parameters</span></span>

- <span data-ttu-id="f21e6-1620">**certificate** 検証している証明書へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1620">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="f21e6-1621">**extension** 拡張機能データ ポインターと長さを含む構造体を返します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1621">**extension** Return structure containing extension data pointer and length.</span></span>
- <span data-ttu-id="f21e6-1622">**extension_id** 上記の表からの OID 整数のマッピング。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1622">**extension_id** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1623">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1623">Return Values</span></span>

- <span data-ttu-id="f21e6-1624">**NX_SUCCESS** （0x00） 指定された拡張機能 OID が見つかり、データが返されました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1624">**NX_SUCCESS** (0x00) Specified extension OID found and data returned.</span></span>
- <span data-ttu-id="f21e6-1625">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** （0x181） ASN.1 マルチバイト タグが見つかりました （サポートされていない証明書）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1625">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="f21e6-1626">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** （0x182） 無効な ASN.1 フィールドが見つかりました （無効な証明書）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1626">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="f21e6-1627">**NX_SECURE_X509_INVALID_TAG_CLASS** （0x190） 無効な ASN.1 タグ クラスが見つかりました （無効な証明書）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1627">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="f21e6-1628">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** （0x192） 無効な拡張機能が見つかりました</span><span class="sxs-lookup"><span data-stu-id="f21e6-1628">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered</span></span>
- <span data-ttu-id="f21e6-1629">**NX_SECURE_X509_EXTENSION_NOT_FOUND** （0x19B） 指定された証明書内に拡張機能 OID が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1629">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The given extension OID was not found in the provided certificate.</span></span>
- <span data-ttu-id="f21e6-1630">**NX_PTR_ERROR** （0x07） 無効な証明書または拡張ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1630">**NX_PTR_ERROR** (0x07) Invalid certificate or extension pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1631">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1631">Allowed From</span></span>

<span data-ttu-id="f21e6-1632">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1632">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1633">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1633">Example</span></span>

```C
/* Function to parse a Basic Constraints X.509 extension. */
UINT _basic_constraints_extension_parse(NX_SECURE_X509_CERT *certificate)
{
const UCHAR             *current_buffer;
ULONG                    length;
UINT                     status;
NX_SECURE_X509_EXTENSION extension_data;

    /* Find the Basic Constraints extension in the certificate. */
    status = _nx_secure_x509_extension_find(certificate, &extension_data,
                              NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS);

    /* See if extension present - it might be OK if not present! */
    if (status != NX_SUCCESS)
    {
        return(status);
    }

    /* The extension_data structure now points to the raw extension ASN.1
      (DER-encoded). */
    current_buffer = extension_data.nx_secure_x509_extension_data;
    length = extension_data.nx_secure_x509_extension_data_length;

   /* Extension ASN.1 parsing… */

   return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1634">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1634">See Also</span></span>

- <span data-ttu-id="f21e6-1635">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-1635">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="f21e6-1636">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="f21e6-1636">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="f21e6-1637">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="f21e6-1637">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="f21e6-1638">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="f21e6-1638">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="f21e6-1639">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="f21e6-1639">nx_secure_x509_extended_key_usage_extension_parse</span></span>

## <a name="nx_secure_x509_key_usage_extension_parse"></a><span data-ttu-id="f21e6-1640">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="f21e6-1640">nx_secure_x509_key_usage_extension_parse</span></span>

<span data-ttu-id="f21e6-1641">X.509 証明書内で X.509 キー使用法拡張機能を検索して解析します</span><span class="sxs-lookup"><span data-stu-id="f21e6-1641">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="f21e6-1642">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="f21e6-1642">Prototype</span></span>

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a><span data-ttu-id="f21e6-1643">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1643">Description</span></span>

<span data-ttu-id="f21e6-1644">このサービスは、証明書の検証コールバック内から呼び出されるように意図されています （「*nx_secure_tls_session_certificate_callback_set*」をご覧ください）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1644">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="f21e6-1645">これは、キー使用拡張機能を検索し、見つかった場合は、「ビットフィールド」 パラメーター内でキー使用ビットフィールドを返します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1645">It will search for the Key Usage extension and if found, will return the Key Usage bitfield in the "bitfield" parameter.</span></span>

<span data-ttu-id="f21e6-1646">X.509 仕様 （RFC 5280） で定義されているビットを以下の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1646">The bits, as defined by the X.509 specification (RFC 5280) are given in the table below.</span></span> <span data-ttu-id="f21e6-1647">ビットごとの AND と適切なビットマスク （および 0 以外のチェック） により、各ビットの値が提供されます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1647">A bitwise AND with the appropriate bitmask (and checking for non-zero) will give the value of each bit.</span></span>

<span data-ttu-id="f21e6-1648">ビットフィールドの DER エンコードにより余分なゼロが削除されるため、証明書の生データ内でのビットの実際の位置は、デコードされたビットフィールドの位置と異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1648">Note that the DER-encoding of the bitfield eliminates extra zeroes so the actual position of the bits in the raw certificate data will likely be different from their positions in the decoded bitfield.</span></span> <span data-ttu-id="f21e6-1649">指定されたビットマスクは、*nx_secure_x509_key_usage_extension_parse* によって返されるデコードされたビットフィールド上でのみ使用されるように意図されており、DER でエンコードされた証明書の生データとは異なります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1649">The supplied bitmasks are only intended to be used on the decoded bitfield returned by *nx_secure_x509_key_usage_extension_parse* and not with the raw DER-encoded certificate data.</span></span>

<span data-ttu-id="f21e6-1650">証明書の検証コールバックでは、エラー リターン コード NX_SECURE_X509_KEY_USAGE_ERROR は、アプリケーションの用途のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1650">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="f21e6-1651">キーの使用の確認中にエラーが発生した場合は、この値がコールバックから返され、エラーの原因を示すことがあります。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1651">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="f21e6-1652">NetX Secure 識別子</span><span class="sxs-lookup"><span data-stu-id="f21e6-1652">NetX Secure Identifier</span></span>                            | <span data-ttu-id="f21e6-1653">ビット位置</span><span class="sxs-lookup"><span data-stu-id="f21e6-1653">Bit position</span></span> | <span data-ttu-id="f21e6-1654">説明</span><span class="sxs-lookup"><span data-stu-id="f21e6-1654">Description</span></span>                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f21e6-1655">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span><span class="sxs-lookup"><span data-stu-id="f21e6-1655">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span></span>  | <span data-ttu-id="f21e6-1656">0</span><span class="sxs-lookup"><span data-stu-id="f21e6-1656">0</span></span>            | <span data-ttu-id="f21e6-1657">証明書をデジタル署名に使用できます</span><span class="sxs-lookup"><span data-stu-id="f21e6-1657">Certificate can be used for digital signatures</span></span>                                                                                                               |
| <span data-ttu-id="f21e6-1658">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span><span class="sxs-lookup"><span data-stu-id="f21e6-1658">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span></span>    | <span data-ttu-id="f21e6-1659">1</span><span class="sxs-lookup"><span data-stu-id="f21e6-1659">1</span></span>            | <span data-ttu-id="f21e6-1660">証明書を使用して、証明書および CRL 以外のデジタル署名を検証できます</span><span class="sxs-lookup"><span data-stu-id="f21e6-1660">Certificate can be used to verify digital signatures other than those for certificates and CRLs</span></span>                                                              |
| <span data-ttu-id="f21e6-1661">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="f21e6-1661">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span></span>   | <span data-ttu-id="f21e6-1662">2</span><span class="sxs-lookup"><span data-stu-id="f21e6-1662">2</span></span>            | <span data-ttu-id="f21e6-1663">証明書を使用して、対称キーを暗号化できます （キー トランスポート）</span><span class="sxs-lookup"><span data-stu-id="f21e6-1663">Certificate can be used to encrypt symmetric keys (key transport)</span></span>                                                                                            |
| <span data-ttu-id="f21e6-1664">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="f21e6-1664">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span></span>  | <span data-ttu-id="f21e6-1665">3</span><span class="sxs-lookup"><span data-stu-id="f21e6-1665">3</span></span>            | <span data-ttu-id="f21e6-1666">証明書を使用して、ユーザーの生データを直接暗号化できます （一般的ではありません）</span><span class="sxs-lookup"><span data-stu-id="f21e6-1666">Certificate can be used to directly encrypt raw user data (uncommon)</span></span>                                                                                         |
| <span data-ttu-id="f21e6-1667">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span><span class="sxs-lookup"><span data-stu-id="f21e6-1667">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span></span>      | <span data-ttu-id="f21e6-1668">4</span><span class="sxs-lookup"><span data-stu-id="f21e6-1668">4</span></span>            | <span data-ttu-id="f21e6-1669">証明書をキーの承諾に使用できます （Diffie-Hellman と同様）</span><span class="sxs-lookup"><span data-stu-id="f21e6-1669">Certificate can be used for key agreement (as with Diffie-Hellman)</span></span>                                                                                           |
| <span data-ttu-id="f21e6-1670">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span><span class="sxs-lookup"><span data-stu-id="f21e6-1670">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span></span>     | <span data-ttu-id="f21e6-1671">5</span><span class="sxs-lookup"><span data-stu-id="f21e6-1671">5</span></span>            | <span data-ttu-id="f21e6-1672">証明書を使用して、他の証明書に署名して検証できます （証明書は CA または ICA 証明書です）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1672">Certificate can be used to sign and verify other certificates (the certificate is a CA or ICA certificate).</span></span>                                                  |
| <span data-ttu-id="f21e6-1673">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span><span class="sxs-lookup"><span data-stu-id="f21e6-1673">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span></span>           | <span data-ttu-id="f21e6-1674">6</span><span class="sxs-lookup"><span data-stu-id="f21e6-1674">6</span></span>            | <span data-ttu-id="f21e6-1675">証明書の公開キーが、CRL 上の署名の検証に使用されます</span><span class="sxs-lookup"><span data-stu-id="f21e6-1675">Certificate public key is used to verify signatures on CRLs</span></span>                                                                                                  |
| <span data-ttu-id="f21e6-1676">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="f21e6-1676">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span></span>      | <span data-ttu-id="f21e6-1677">7</span><span class="sxs-lookup"><span data-stu-id="f21e6-1677">7</span></span>            | <span data-ttu-id="f21e6-1678">キーの承諾ビット （ビット 4） に使用されます。設定されている場合、キーの承諾中、暗号化にのみ証明書キーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1678">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to encrypt during key agreement.</span></span> <span data-ttu-id="f21e6-1679">キーの承諾ビットが設定されていない場合は、未定義です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1679">Undefined if Key Agreement bit is not set.</span></span> |
| <span data-ttu-id="f21e6-1680">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="f21e6-1680">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span></span>      | <span data-ttu-id="f21e6-1681">8</span><span class="sxs-lookup"><span data-stu-id="f21e6-1681">8</span></span>            | <span data-ttu-id="f21e6-1682">キーの承諾ビット （ビット 4） に使用されます。設定されている場合、キーの承諾中、解読にのみ証明書キーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1682">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to decrypt during key agreement.</span></span> <span data-ttu-id="f21e6-1683">キーの承諾ビットが設定されていない場合は、未定義です。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1683">Undefined if Key Agreement bit is not set.</span></span> |

<span data-ttu-id="f21e6-1684">X.509 キー使用拡張機能のビットマスクと値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1684">Bitmasks and values for X.509 Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="f21e6-1685">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f21e6-1685">Parameters</span></span>

- <span data-ttu-id="f21e6-1686">**certificate** 検証している証明書へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1686">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="f21e6-1687">**bitfield** 拡張機能からビットフィールド全体を返します。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1687">**bitfield** Return the entire bitfield from the extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="f21e6-1688">戻り値</span><span class="sxs-lookup"><span data-stu-id="f21e6-1688">Return Values</span></span>

- <span data-ttu-id="f21e6-1689">**NX_SUCCESS** （0x00） キー使用拡張機能が見つかり、ビットフィールドが返されました。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1689">**NX_SUCCESS** (0x00) Key usage extension found and bitfield returned.</span></span>
- <span data-ttu-id="f21e6-1690">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** （0x181） ASN.1 マルチバイト タグが見つかりました （サポートされていない証明書）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1690">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="f21e6-1691">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** （0x182） 無効な ASN.1 フィールドが見つかりました （無効な証明書）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1691">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="f21e6-1692">**NX_SECURE_X509_INVALID_TAG_CLASS** （0x190） 無効な ASN.1 タグ クラスが見つかりました （無効な証明書）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1692">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="f21e6-1693">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** （0x192） 無効な拡張機能が見つかりました （無効な証明書）。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1693">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="f21e6-1694">**NX_SECURE_X509_EXTENSION_NOT_FOUND** （0x19B） 指定された証明書内にキー使用拡張機能が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1694">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B)The Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="f21e6-1695">**NX_PTR_ERROR** （0x07） 無効な証明書またはビットフィールド ポインター。</span><span class="sxs-lookup"><span data-stu-id="f21e6-1695">**NX_PTR_ERROR** (0x07) Invalid certificate or bitfield pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f21e6-1696">許可元</span><span class="sxs-lookup"><span data-stu-id="f21e6-1696">Allowed From</span></span>

<span data-ttu-id="f21e6-1697">Threads</span><span class="sxs-lookup"><span data-stu-id="f21e6-1697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f21e6-1698">例</span><span class="sxs-lookup"><span data-stu-id="f21e6-1698">Example</span></span>

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session,
  NX_SECURE_X509_CERT* certificate)
{
UINT status;
USHORT key_usage_bitfield;

    /* Key usage – extract key usage bitfield. */
    status = nx_secure_x509_key_usage_extension_parse(certificate, &key_usage_bitfield);

   /* Check certificate for a few specific key usage bits. */
   if((key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE) == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION)   == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT)  == 0)
    {
        printf("Expected key usage bitfield bits not set!\n");
        return(NX_SECURE_X509_KEY_USAGE_ERROR);
    }

    /* The specified bits were set, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="f21e6-1699">参照</span><span class="sxs-lookup"><span data-stu-id="f21e6-1699">See Also</span></span>

- <span data-ttu-id="f21e6-1700">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="f21e6-1700">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="f21e6-1701">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="f21e6-1701">nx_secure_x509_extended_key_usage_extension_parse</span></span>
- <span data-ttu-id="f21e6-1702">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="f21e6-1702">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="f21e6-1703">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="f21e6-1703">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="f21e6-1704">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="f21e6-1704">nx_secure_x509_extension_find</span></span>
