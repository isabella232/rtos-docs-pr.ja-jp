---
title: チャプター 3 - Azure RTOS NetX Duo SNMP エージェントのサービスの説明
description: このチャプターでは、NetX Duo SNMP エージェントのすべてのサービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf4c4cb0edb7deb7bd0f257f48949b5c7355426b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810583"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-snmp-agent-services"></a><span data-ttu-id="25b31-103">チャプター 3 - Azure RTOS NetX Duo SNMP エージェントのサービスの説明</span><span class="sxs-lookup"><span data-stu-id="25b31-103">Chapter 3 - Description of Azure RTOS NetX Duo SNMP agent services</span></span>

<span data-ttu-id="25b31-104">このチャプターでは、Azure RTOS NetX Duo SNMP エージェントのすべてのサービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="25b31-104">This chapter contains a description of all Azure RTOS NetX Duo SNMP agent services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="25b31-105">次の API の説明の「戻り値」セクションで、**太字** の値は、API のエラー チェックを有効にするための **NX_DISABLE_ERROR_CHECKING** を有効にしてもその影響を受けないことを表します。太字でない値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="25b31-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="25b31-106">nx_snmp_agent_auth_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="25b31-106">nx_snmp_agent_auth_trap_key_use</span></span>](#nx_snmp_agent_auth_trap_key_use)
   - <span data-ttu-id="25b31-107">*トラップ メッセージの認証キーを指定します (SNMP v3 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-107">*Specify authentication key (SNMP v3 only) for trap messages*</span></span>
- [<span data-ttu-id="25b31-108">nx_snmp_agent_authenticate_key_use</span><span class="sxs-lookup"><span data-stu-id="25b31-108">nx_snmp_agent_authenticate_key_use</span></span>](#nx_snmp_agent_authenticate_key_use)
   - <span data-ttu-id="25b31-109">*応答メッセージの認証キーを指定します (SNMP v3 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-109">*Specify authentication key (SNMP v3 only) for response messages*</span></span>
- [<span data-ttu-id="25b31-110">nx_snmp_agent_community_get</span><span class="sxs-lookup"><span data-stu-id="25b31-110">nx_snmp_agent_community_get</span></span>](#nx_snmp_agent_community_get)
   - <span data-ttu-id="25b31-111">*コミュニティ名を取得します*</span><span class="sxs-lookup"><span data-stu-id="25b31-111">*Retrieve community name*</span></span>
- [<span data-ttu-id="25b31-112">nx_snmp_agent_context_engine_set</span><span class="sxs-lookup"><span data-stu-id="25b31-112">nx_snmp_agent_context_engine_set</span></span>](#nx_snmp_agent_context_engine_set)
   - <span data-ttu-id="25b31-113">*コンテキスト エンジンを設定します (SNMP v3 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-113">*Set context engine (SNMP v3 only)*</span></span>
- [<span data-ttu-id="25b31-114">nx_snmp_agent_context_name_set</span><span class="sxs-lookup"><span data-stu-id="25b31-114">nx_snmp_agent_context_name_set</span></span>](#nx_snmp_agent_context_name_set)
   - <span data-ttu-id="25b31-115">*コンテキスト名を設定します (SNMP v3 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-115">*Set context name (SNMP v3 only)*</span></span>
- [<span data-ttu-id="25b31-116">nx_snmp_agent_create</span><span class="sxs-lookup"><span data-stu-id="25b31-116">nx_snmp_agent_create</span></span>](#nx_snmp_agent_create)
   - <span data-ttu-id="25b31-117">*SNMP エージェントを作成します*</span><span class="sxs-lookup"><span data-stu-id="25b31-117">*Create SNMP agent*</span></span>
- [<span data-ttu-id="25b31-118">nx_snmp_agent_current_version_get</span><span class="sxs-lookup"><span data-stu-id="25b31-118">nx_snmp_agent_current_version_get</span></span>](#nx_snmp_agent_current_version_get)
   - <span data-ttu-id="25b31-119">*受信パケットの SNMP のバージョンを取得します*</span><span class="sxs-lookup"><span data-stu-id="25b31-119">*Get the SNMP version of received packet*</span></span>
- [<span data-ttu-id="25b31-120">nx_snmp_agent_request_get_type_test</span><span class="sxs-lookup"><span data-stu-id="25b31-120">nx_snmp_agent_request_get_type_test</span></span>](#nx_snmp_agent_request_get_type_test)
   - <span data-ttu-id="25b31-121">*最後に受け取った SNMP 要求が GET と SET どちらのタイプであるかを示します*</span><span class="sxs-lookup"><span data-stu-id="25b31-121">*Indicate if last SNMP request is GET or SET type*</span></span>
- [<span data-ttu-id="25b31-122">nx_snmp_agent_private_string_test</span><span class="sxs-lookup"><span data-stu-id="25b31-122">nx_snmp_agent_private_string_test</span></span>](#nx_snmp_agent_private_string_test)
   - <span data-ttu-id="25b31-123">*文字列がエージェントのプライベート文字列に一致するかどうかを判断します*</span><span class="sxs-lookup"><span data-stu-id="25b31-123">*Determine if string matches agent private string*</span></span>
- [<span data-ttu-id="25b31-124">nx_snmp_agent_public_string_test</span><span class="sxs-lookup"><span data-stu-id="25b31-124">nx_snmp_agent_public_string_test</span></span>](#nx_snmp_agent_public_string_test)
   - <span data-ttu-id="25b31-125">*文字列がエージェントのパブリック文字列に一致するかどうかを判断します*</span><span class="sxs-lookup"><span data-stu-id="25b31-125">*Determine if string matches agent public string*</span></span>
- [<span data-ttu-id="25b31-126">nx_snmp_agent_set_interface</span><span class="sxs-lookup"><span data-stu-id="25b31-126">nx_snmp_agent_set_interface</span></span>](#nx_snmp_agent_set_interface)
   - <span data-ttu-id="25b31-127">*SNMP メッセージのネットワーク インターフェイスを設定します*</span><span class="sxs-lookup"><span data-stu-id="25b31-127">*Set network interface for SNMP messaging*</span></span>
- [<span data-ttu-id="25b31-128">nx_snmp_agent_private_string_set</span><span class="sxs-lookup"><span data-stu-id="25b31-128">nx_snmp_agent_private_string_set</span></span>](#nx_snmp_agent_private_string_set)
   - <span data-ttu-id="25b31-129">*SNMP エージェントのプライベート コミュニティ文字列を設定します*</span><span class="sxs-lookup"><span data-stu-id="25b31-129">*Set the SNMP agent private community string*</span></span>
- [<span data-ttu-id="25b31-130">nx_snmp_agent_public_string_set</span><span class="sxs-lookup"><span data-stu-id="25b31-130">nx_snmp_agent_public_string_set</span></span>](#nx_snmp_agent_public_string_set)
   - <span data-ttu-id="25b31-131">*SNMP エージェントのパブリック コミュニティ文字列を設定します*</span><span class="sxs-lookup"><span data-stu-id="25b31-131">*Set the SNMP agent public community string*</span></span>
- [<span data-ttu-id="25b31-132">nx_snmp_agent_version_set</span><span class="sxs-lookup"><span data-stu-id="25b31-132">nx_snmp_agent_version_set</span></span>](#nx_snmp_agent_version_set)
   - <span data-ttu-id="25b31-133">*すべての SNMP バージョンに対して SNMP エージェントの状態を設定します*</span><span class="sxs-lookup"><span data-stu-id="25b31-133">*Set the SNMP agent status for all SNMP versions*</span></span>
- [<span data-ttu-id="25b31-134">nx_snmp_agent_delete</span><span class="sxs-lookup"><span data-stu-id="25b31-134">nx_snmp_agent_delete</span></span>](#nx_snmp_agent_delete)
   - <span data-ttu-id="25b31-135">*SNMP エージェントを削除します*</span><span class="sxs-lookup"><span data-stu-id="25b31-135">*Delete SNMP agent*</span></span>
- [<span data-ttu-id="25b31-136">nx_snmp_agent_md5_key_create</span><span class="sxs-lookup"><span data-stu-id="25b31-136">nx_snmp_agent_md5_key_create</span></span>](#nx_snmp_agent_md5_key_create)
   - <span data-ttu-id="25b31-137">*MD5 キーを作成します (SNMP v3 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-137">*Create md5 key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="25b31-138">nx_snmp_agent_md5_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="25b31-138">nx_snmp_agent_md5_key_create_extended</span></span>](#nx_snmp_agent_md5_key_create_extended)
   - <span data-ttu-id="25b31-139">*MD5 キーを作成します (SNMP v3 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-139">*Create md5 key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="25b31-140">nx_snmp_agent_priv_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="25b31-140">nx_snmp_agent_priv_trap_key_use</span></span>](#nx_snmp_agent_priv_trap_key_use)
   - <span data-ttu-id="25b31-141">*トラップ メッセージの暗号化キーを指定します (SNMP v3 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-141">*Specify encryption key (SNMP v3 only) for trap messages*</span></span>
- [<span data-ttu-id="25b31-142">nx_snmp_agent_privacy_key_use</span><span class="sxs-lookup"><span data-stu-id="25b31-142">nx_snmp_agent_privacy_key_use</span></span>](#nx_snmp_agent_privacy_key_use)
   - <span data-ttu-id="25b31-143">*応答メッセージの暗号化キーを指定します (SNMP v3 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-143">*Specify encryption key (SNMP v3 only) for response messages*</span></span>
- [<span data-ttu-id="25b31-144">nx_snmp_agent_sha_key_create</span><span class="sxs-lookup"><span data-stu-id="25b31-144">nx_snmp_agent_sha_key_create</span></span>](#nx_snmp_agent_sha_key_create)
   - <span data-ttu-id="25b31-145">*SHA キーを作成します (SNMP v3 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-145">*Create sha key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="25b31-146">nx_snmp_agent_sha_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="25b31-146">nx_snmp_agent_sha_key_create_extended</span></span>](#nx_snmp_agent_sha_key_create_extended)
   - <span data-ttu-id="25b31-147">*SHA キーを作成します (SNMP v3 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-147">*Create sha key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="25b31-148">nx_snmp_agent_start</span><span class="sxs-lookup"><span data-stu-id="25b31-148">nx_snmp_agent_start</span></span>](#nx_snmp_agent_start)
   - <span data-ttu-id="25b31-149">*SNMP エージェントを起動します*</span><span class="sxs-lookup"><span data-stu-id="25b31-149">*Start SNMP agent*</span></span>
- [<span data-ttu-id="25b31-150">nx_snmp_agent_stop</span><span class="sxs-lookup"><span data-stu-id="25b31-150">nx_snmp_agent_stop</span></span>](#nx_snmp_agent_stop)
   - <span data-ttu-id="25b31-151">*SNMP エージェントを停止します*</span><span class="sxs-lookup"><span data-stu-id="25b31-151">*Stop SNMP agent*</span></span>
- [<span data-ttu-id="25b31-152">nx_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="25b31-152">nx_snmp_agent_trap_send</span></span>](#nx_snmp_agent_trap_send)
   - <span data-ttu-id="25b31-153">*SNMPv1 トラップを送信します (IPv4 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-153">*Send SNMP v1 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="25b31-154">nx_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="25b31-154">nx_snmp_agent_trapv2_send</span></span>](#nx_snmp_agent_trapv2_send)
   - <span data-ttu-id="25b31-155">*SNMPv2 トラップを送信します (IPv4 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-155">*Send SNMP v2 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="25b31-156">nx_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="25b31-156">nx_snmp_agent_trapv2_oid_send</span></span>](#nx_snmp_agent_trapv2_oid_send)
   - <span data-ttu-id="25b31-157">*OID を指定して SNMPv2 トラップを送信します (IPv4 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-157">*Send SNMP v2 trap (IPv4 only) specifying the OID*</span></span>
- [<span data-ttu-id="25b31-158">nx_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="25b31-158">nx_snmp_agent_trapv3_send</span></span>](#nx_snmp_agent_trapv3_send)
   - <span data-ttu-id="25b31-159">*SNMPv3 トラップを送信します (IPv4 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-159">*Send SNMP v3 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="25b31-160">nx_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="25b31-160">nx_snmp_agent_trapv3_oid_send</span></span>](#nx_snmp_agent_trapv3_oid_send)
   - <span data-ttu-id="25b31-161">*OID を指定して SNMPv2 トラップを送信します (IPv4 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-161">*Send SNMP v2 trap (IPv4 only) specifying the OID*</span></span>
- [<span data-ttu-id="25b31-162">nxd_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="25b31-162">nxd_snmp_agent_trap_send</span></span>](#nxd_snmp_agent_trap_send)
   - <span data-ttu-id="25b31-163">*SNMPv1 トラップを送信します (IPv4 と IPv6)*</span><span class="sxs-lookup"><span data-stu-id="25b31-163">*Send SNMP v1 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="25b31-164">nxd_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="25b31-164">nxd_snmp_agent_trapv2_send</span></span>](#nxd_snmp_agent_trapv2_send)
   - <span data-ttu-id="25b31-165">*SNMPv2 トラップを送信します (IPv4 と IPv6)*</span><span class="sxs-lookup"><span data-stu-id="25b31-165">*Send SNMP v2 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="25b31-166">nxd_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="25b31-166">nxd_snmp_agent_trapv2_oid_send</span></span>](#nxd_snmp_agent_trapv2_oid_send)
   - <span data-ttu-id="25b31-167">*OID を指定して SNMPv2 トラップを送信します (IPv4 と IPv6)*</span><span class="sxs-lookup"><span data-stu-id="25b31-167">*Send SNMP v2 trap (IPv4/IPv6) specifying the OID*</span></span>
- [<span data-ttu-id="25b31-168">nxd_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="25b31-168">nxd_snmp_agent_trapv3_send</span></span>](#nxd_snmp_agent_trapv3_send)
   - <span data-ttu-id="25b31-169">*SNMPv3 トラップを送信します (IPv4 と IPv6)*</span><span class="sxs-lookup"><span data-stu-id="25b31-169">*Send SNMP v3 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="25b31-170">nxd_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="25b31-170">nxd_snmp_agent_trapv3_oid_send</span></span>](#nxd_snmp_agent_trapv3_oid_send)
   - <span data-ttu-id="25b31-171">*OID を指定して SNMP v2 トラップを送信します (IPv4 と IPv6)*</span><span class="sxs-lookup"><span data-stu-id="25b31-171">*Send SNMP v2 trap (IPv4/IPv6) specifying the OID*</span></span>
- [<span data-ttu-id="25b31-172">nx_snmp_agent_v3_context_boots_set</span><span class="sxs-lookup"><span data-stu-id="25b31-172">nx_snmp_agent_v3_context_boots_set</span></span>](#nx_snmp_agent_v3_context_boots_set)
   - <span data-ttu-id="25b31-173">*再起動回数を設定します*</span><span class="sxs-lookup"><span data-stu-id="25b31-173">*Set the number of reboots*</span></span>
- [<span data-ttu-id="25b31-174">nx_snmp_object_compare</span><span class="sxs-lookup"><span data-stu-id="25b31-174">nx_snmp_object_compare</span></span>](#nx_snmp_object_compare)
   - <span data-ttu-id="25b31-175">*2 つのオブジェクトを比較します*</span><span class="sxs-lookup"><span data-stu-id="25b31-175">*Compare two objects*</span></span>
- [<span data-ttu-id="25b31-176">nx_snmp_object_compare_extended</span><span class="sxs-lookup"><span data-stu-id="25b31-176">nx_snmp_object_compare_extended</span></span>](#nx_snmp_object_compare_extended)
   - <span data-ttu-id="25b31-177">*2 つのオブジェクトを比較します*</span><span class="sxs-lookup"><span data-stu-id="25b31-177">*Compare two objects*</span></span>
- [<span data-ttu-id="25b31-178">nx_snmp_object_copy</span><span class="sxs-lookup"><span data-stu-id="25b31-178">nx_snmp_object_copy</span></span>](#nx_snmp_object_copy)
   - <span data-ttu-id="25b31-179">*オブジェクトをコピーする*</span><span class="sxs-lookup"><span data-stu-id="25b31-179">*Copy an object*</span></span>
- [<span data-ttu-id="25b31-180">nx_snmp_object_copy_extended</span><span class="sxs-lookup"><span data-stu-id="25b31-180">nx_snmp_object_copy_extended</span></span>](#nx_snmp_object_copy_extended)
   - <span data-ttu-id="25b31-181">*オブジェクトをコピーする*</span><span class="sxs-lookup"><span data-stu-id="25b31-181">*Copy an object*</span></span>
- [<span data-ttu-id="25b31-182">nx_snmp_object_counter_get</span><span class="sxs-lookup"><span data-stu-id="25b31-182">nx_snmp_object_counter_get</span></span>](#nx_snmp_object_counter_get)
   - <span data-ttu-id="25b31-183">*カウンター オブジェクトを取得します*</span><span class="sxs-lookup"><span data-stu-id="25b31-183">*Get counter object*</span></span>
- [<span data-ttu-id="25b31-184">nx_snmp_object_counter_set</span><span class="sxs-lookup"><span data-stu-id="25b31-184">nx_snmp_object_counter_set</span></span>](#nx_snmp_object_counter_set)
   - <span data-ttu-id="25b31-185">*カウンター オブジェクトを設定します*</span><span class="sxs-lookup"><span data-stu-id="25b31-185">*Set counter object*</span></span>
- [<span data-ttu-id="25b31-186">nx_snmp_object_counter64_get</span><span class="sxs-lookup"><span data-stu-id="25b31-186">nx_snmp_object_counter64_get</span></span>](#nx_snmp_object_counter64_get)
   - <span data-ttu-id="25b31-187">*64 ビットのカウンター オブジェクトを取得します*</span><span class="sxs-lookup"><span data-stu-id="25b31-187">*Get 64-bit counter object*</span></span>
- [<span data-ttu-id="25b31-188">nx_snmp_object_counter64_set</span><span class="sxs-lookup"><span data-stu-id="25b31-188">nx_snmp_object_counter64_set</span></span>](#nx_snmp_object_counter64_set)
   - <span data-ttu-id="25b31-189">*64ビットのカウンター オブジェクトを設定します*</span><span class="sxs-lookup"><span data-stu-id="25b31-189">*Set 64-bit counter object*</span></span>
- [<span data-ttu-id="25b31-190">nx_snmp_object_end_of_mib</span><span class="sxs-lookup"><span data-stu-id="25b31-190">nx_snmp_object_end_of_mib</span></span>](#nx_snmp_object_end_of_mib)
   - <span data-ttu-id="25b31-191">*end-of-mib (MIB の末尾) の値を設定します*</span><span class="sxs-lookup"><span data-stu-id="25b31-191">*Set end-of-mib value*</span></span>
- [<span data-ttu-id="25b31-192">nx_snmp_object_gauge_get</span><span class="sxs-lookup"><span data-stu-id="25b31-192">nx_snmp_object_gauge_get</span></span>](#nx_snmp_object_gauge_get)
   - <span data-ttu-id="25b31-193">*ゲージ オブジェクトを取得します*</span><span class="sxs-lookup"><span data-stu-id="25b31-193">*Get gauge object*</span></span>
- [<span data-ttu-id="25b31-194">nx_snmp_object_gauge_set</span><span class="sxs-lookup"><span data-stu-id="25b31-194">nx_snmp_object_gauge_set</span></span>](#nx_snmp_object_gauge_set)
   - <span data-ttu-id="25b31-195">*ゲージ オブジェクトを設定します*</span><span class="sxs-lookup"><span data-stu-id="25b31-195">*Set gauge object*</span></span>
- [<span data-ttu-id="25b31-196">nx_snmp_object_id_get</span><span class="sxs-lookup"><span data-stu-id="25b31-196">nx_snmp_object_id_get</span></span>](#nx_snmp_object_id_get)
   - <span data-ttu-id="25b31-197">*オブジェクト ID を取得します*</span><span class="sxs-lookup"><span data-stu-id="25b31-197">*Get object id*</span></span>
- [<span data-ttu-id="25b31-198">nx_snmp_object_id_set</span><span class="sxs-lookup"><span data-stu-id="25b31-198">nx_snmp_object_id_set</span></span>](#nx_snmp_object_id_set)
   - <span data-ttu-id="25b31-199">*オブジェクト ID を設定します*</span><span class="sxs-lookup"><span data-stu-id="25b31-199">*Set object id*</span></span>
- [<span data-ttu-id="25b31-200">nx_snmp_object_integer_get</span><span class="sxs-lookup"><span data-stu-id="25b31-200">nx_snmp_object_integer_get</span></span>](#nx_snmp_object_integer_get)
   - <span data-ttu-id="25b31-201">*整数オブジェクトを取得します*</span><span class="sxs-lookup"><span data-stu-id="25b31-201">*Get integer object*</span></span>
- [<span data-ttu-id="25b31-202">nx_snmp_object_integer_set</span><span class="sxs-lookup"><span data-stu-id="25b31-202">nx_snmp_object_integer_set</span></span>](#nx_snmp_object_integer_set)
   - <span data-ttu-id="25b31-203">*整数オブジェクトを設定します*</span><span class="sxs-lookup"><span data-stu-id="25b31-203">*Set integer object*</span></span>
- [<span data-ttu-id="25b31-204">nx_snmp_object_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="25b31-204">nx_snmp_object_ip_address_get</span></span>](#nx_snmp_object_ip_address_get)
   - <span data-ttu-id="25b31-205">*IP アドレス オブジェクトを取得します (IPv4 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-205">*Get IP address object (IPv4 only)*</span></span>
- [<span data-ttu-id="25b31-206">nx_snmp_object_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="25b31-206">nx_snmp_object_ip_address_set</span></span>](#nx_snmp_object_ip_address_set)
   - <span data-ttu-id="25b31-207">*IP アドレス オブジェクトを設定します (IPv4 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-207">*Set IP address object (IPv4 only)*</span></span>
- [<span data-ttu-id="25b31-208">nx_snmp_object_ipv6_address_get</span><span class="sxs-lookup"><span data-stu-id="25b31-208">nx_snmp_object_ipv6_address_get</span></span>](#nx_snmp_object_ipv6_address_get)
   - <span data-ttu-id="25b31-209">*IP アドレス オブジェクトを取得します (IPv6 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-209">*Get IP address object (IPv6 only)*</span></span>
- [<span data-ttu-id="25b31-210">nx_snmp_object_ipv6_address_set</span><span class="sxs-lookup"><span data-stu-id="25b31-210">nx_snmp_object_ipv6_address_set</span></span>](#nx_snmp_object_ipv6_address_set)
   - <span data-ttu-id="25b31-211">*IP アドレス オブジェクトを設定します (IPv6 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-211">*Set IP address object (IPv6 only)*</span></span>
- [<span data-ttu-id="25b31-212">nx_snmp_object_no_instance</span><span class="sxs-lookup"><span data-stu-id="25b31-212">nx_snmp_object_no_instance</span></span>](#nx_snmp_object_no_instance)
   - <span data-ttu-id="25b31-213">*インスタンス不在の値を設定します*</span><span class="sxs-lookup"><span data-stu-id="25b31-213">*Set no-instance value*</span></span>
- [<span data-ttu-id="25b31-214">nx_snmp_object_not_found</span><span class="sxs-lookup"><span data-stu-id="25b31-214">nx_snmp_object_not_found</span></span>](#nx_snmp_object_not_found)
   - <span data-ttu-id="25b31-215">*不検出の値を設定します*</span><span class="sxs-lookup"><span data-stu-id="25b31-215">*Set not-found value*</span></span>
- [<span data-ttu-id="25b31-216">nx_snmp_object_octet_string_get</span><span class="sxs-lookup"><span data-stu-id="25b31-216">nx_snmp_object_octet_string_get</span></span>](#nx_snmp_object_octet_string_get)
   - <span data-ttu-id="25b31-217">*オクテット文字列オブジェクトを取得します*</span><span class="sxs-lookup"><span data-stu-id="25b31-217">*Get octet string object*</span></span>
- [<span data-ttu-id="25b31-218">nx_snmp_object_octet_string_set</span><span class="sxs-lookup"><span data-stu-id="25b31-218">nx_snmp_object_octet_string_set</span></span>](#nx_snmp_object_octet_string_set)
   - <span data-ttu-id="25b31-219">*オクテット文字列オブジェクトを設定します*</span><span class="sxs-lookup"><span data-stu-id="25b31-219">*Set octet string object*</span></span>
- [<span data-ttu-id="25b31-220">nx_snmp_object_string_get</span><span class="sxs-lookup"><span data-stu-id="25b31-220">nx_snmp_object_string_get</span></span>](#nx_snmp_object_string_get)
   - <span data-ttu-id="25b31-221">*ASCII 文字列オブジェクトを取得します*</span><span class="sxs-lookup"><span data-stu-id="25b31-221">*Get ASCII string object*</span></span>
- [<span data-ttu-id="25b31-222">nx_snmp_object_string_set</span><span class="sxs-lookup"><span data-stu-id="25b31-222">nx_snmp_object_string_set</span></span>](#nx_snmp_object_string_set)
   - <span data-ttu-id="25b31-223">*ASCII 文字列オブジェクトを設定します*</span><span class="sxs-lookup"><span data-stu-id="25b31-223">*Set ASCII string object*</span></span>
- [<span data-ttu-id="25b31-224">nx_snmp_object_timetics_get</span><span class="sxs-lookup"><span data-stu-id="25b31-224">nx_snmp_object_timetics_get</span></span>](#nx_snmp_object_timetics_get)
   - <span data-ttu-id="25b31-225">*timetics オブジェクトを取得します*</span><span class="sxs-lookup"><span data-stu-id="25b31-225">*Get timetics object*</span></span>
- [<span data-ttu-id="25b31-226">nx_snmp_object_timetics_set</span><span class="sxs-lookup"><span data-stu-id="25b31-226">nx_snmp_object_timetics_set</span></span>](#nx_snmp_object_timetics_set)
   - <span data-ttu-id="25b31-227">*timetics オブジェクトを設定します*</span><span class="sxs-lookup"><span data-stu-id="25b31-227">*Set timetics object*</span></span>

## <a name="nx_snmp_agent_auth_trap_key_use"></a><span data-ttu-id="25b31-228">nx_snmp_agent_auth_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="25b31-228">nx_snmp_agent_auth_trap_key_use</span></span>
<span data-ttu-id="25b31-229">トラップ メッセージの認証キーを指定します</span><span class="sxs-lookup"><span data-stu-id="25b31-229">Specify authentication key for trap messages</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-230">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-230">Prototype</span></span>

```c
UINT nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="25b31-231">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-231">Description</span></span>

<span data-ttu-id="25b31-232">このサービスでは、トラップ メッセージの SNMPv3 セキュリティ ヘッダーに認証パラメーターを設定する際に使用するキーを指定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-232">This service specifies the key to be used for setting authentication parameters in the SNMPv3 security header in trap messages.</span></span> <span data-ttu-id="25b31-233">キーに NX_NULL の値を指定すると認証を無効にします。</span><span class="sxs-lookup"><span data-stu-id="25b31-233">Supplying a NX_NULL value for the key disables authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="25b31-234">キーを前もって作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="25b31-234">The key must be previously created.</span></span> <span data-ttu-id="25b31-235">nx_snmp_agent_md5_key_create または nx_snmp_agent_sha_key_create を参考にしてください。</span><span class="sxs-lookup"><span data-stu-id="25b31-235">See nx_snmp_agent_md5_key_create or nx_snmp_agent_sha_key_create.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-236">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-236">Input Parameters</span></span>

- <span data-ttu-id="25b31-237">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-237">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-238">**key** 作成済みの MD5 キーまたは SHA キーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-238">**key** Pointer to a previously created MD5 or SHA key.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-239">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-239">Return Values</span></span>

- <span data-ttu-id="25b31-240">**NX_SUCCESS** (0x00) 認証キーの設定に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-240">**NX_SUCCESS** (0x00) Successful authentication key set.</span></span>
- <span data-ttu-id="25b31-241">**NX_NOT_ENABLED** (0x14) SNMP セキュリティが無効になっています</span><span class="sxs-lookup"><span data-stu-id="25b31-241">**NX_NOT_ENABLED** (0x14) SNMP Security disabled</span></span> 
- <span data-ttu-id="25b31-242">**NX_PTR_ERROR** (0x07) SNMP エージェントへのポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-242">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-243">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-243">Allowed From</span></span>

<span data-ttu-id="25b31-244">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-244">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-245">例</span><span class="sxs-lookup"><span data-stu-id="25b31-245">Example</span></span>

```c
/* Use previously created “my_key” for SNMPv3 trap message authentication.  */
status =  nx_snmp_agent_auth_trap_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for authentication parameters in trap messages.  */
```

## <a name="nx_snmp_agent_authenticate_key_use"></a><span data-ttu-id="25b31-246">nx_snmp_agent_authenticate_key_use</span><span class="sxs-lookup"><span data-stu-id="25b31-246">nx_snmp_agent_authenticate_key_use</span></span>
<span data-ttu-id="25b31-247">応答メッセージの認証キーを指定します</span><span class="sxs-lookup"><span data-stu-id="25b31-247">Specify authentication key for response messages</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-248">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-248">Prototype</span></span>

```c
UINT nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr, 
                                        NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="25b31-249">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-249">Description</span></span>

<span data-ttu-id="25b31-250">このサービスでは、それ以降のすべての要求で SNMPv3 セキュリティ パラメーターの認証パラメーターに使用するキーを指定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-250">This service specifies the key to be used for authentication parameters in the SNMPv3 security parameter for all requests made after it is set.</span></span> <span data-ttu-id="25b31-251">キーに NX_NULL の値を指定すると認証を無効にします。</span><span class="sxs-lookup"><span data-stu-id="25b31-251">Supplying a NX_NULL value for the key disables authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="25b31-252">キーを前もって作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="25b31-252">The key must be previously created.</span></span> <span data-ttu-id="25b31-253">nx_snmp_agent_md5_key_create または nx_snmp_agent_sha_key_create を参考にしてください。</span><span class="sxs-lookup"><span data-stu-id="25b31-253">See nx_snmp_agent_md5_key_create or nx_snmp_agent_sha_key_create.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-254">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-254">Input Parameters</span></span>

- <span data-ttu-id="25b31-255">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-255">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-256">**key** 作成済みの MD5 キーまたは SHA キーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-256">**key** Pointer to a previously created MD5 or SHA key.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-257">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-257">Return Values</span></span>

- <span data-ttu-id="25b31-258">**NX_SUCCESS** (0x00) SNMP キーの設定に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-258">**NX_SUCCESS** (0x00) Successful SNMP key set.</span></span>
- <span data-ttu-id="25b31-259">**NX_NOT_ENABLED** (0x14) SNMP セキュリティが無効になっています</span><span class="sxs-lookup"><span data-stu-id="25b31-259">**NX_NOT_ENABLED** (0x14) SNMP Security disabled</span></span>
- <span data-ttu-id="25b31-260">**NX_PTR_ERROR** (0x07) SNMP エージェントへのポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-260">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-261">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-261">Allowed From</span></span>

<span data-ttu-id="25b31-262">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-262">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-263">例</span><span class="sxs-lookup"><span data-stu-id="25b31-263">Example</span></span>

```c
/* Use previously created “my_key” for SNMPv3 authentication.  */
status =  nx_snmp_agent_authenticate_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for setting the authentication parameters of SNMPv3 requests.  */
```

## <a name="nx_snmp_agent_community_get"></a><span data-ttu-id="25b31-264">nx_snmp_agent_community_get</span><span class="sxs-lookup"><span data-stu-id="25b31-264">nx_snmp_agent_community_get</span></span>
<span data-ttu-id="25b31-265">コミュニティ名を取得します</span><span class="sxs-lookup"><span data-stu-id="25b31-265">Retrieve community name</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-266">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-266">Prototype</span></span>

```c
UINT nx_snmp_agent_community_get(NX_SNMP_AGENT *agent_ptr, 
                                 UCHAR **community_string_ptr);
```

### <a name="description"></a><span data-ttu-id="25b31-267">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-267">Description</span></span>

<span data-ttu-id="25b31-268">このサービスでは、SNMP エージェントで最後に受信した SNMP 要求からコミュニティ名を取得します。</span><span class="sxs-lookup"><span data-stu-id="25b31-268">This service retrieves the community name from the most recent SNMP request received by the SNMP Agent.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-269">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-269">Input Parameters</span></span>

- <span data-ttu-id="25b31-270">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-270">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-271">**community_string_ptr** SNMP エージェントのコミュニティ文字列への文字列ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-271">**community_string_ptr** Pointer to a string pointer to return the SNMP Agent community string.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-272">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-272">Return Values</span></span>

- <span data-ttu-id="25b31-273">**NX_SUCCESS** (0x00) SNMP のコミュニティ名の取得に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-273">**NX_SUCCESS** (0x00) Successful SNMP community get.</span></span>
- <span data-ttu-id="25b31-274">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-274">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-275">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-275">Allowed From</span></span>

<span data-ttu-id="25b31-276">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-276">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-277">例</span><span class="sxs-lookup"><span data-stu-id="25b31-277">Example</span></span>

```c
UCHAR *string_ptr;

/* Pickup the community string pointer for my_agent.  */
status =  nx_snmp_agent_community_get(&my_agent, &string_ptr);


/* If status is NX_SUCCESS the pointer “string_ptr” points to the
   last community name supplied to the SNMP agent.  */
```

## <a name="nx_snmp_agent_request_get_type_test"></a><span data-ttu-id="25b31-278">nx_snmp_agent_request_get_type_test</span><span class="sxs-lookup"><span data-stu-id="25b31-278">nx_snmp_agent_request_get_type_test</span></span>
<span data-ttu-id="25b31-279">最後に受け取った SNMP 要求が GET と SET どちらのタイプであるかを示します</span><span class="sxs-lookup"><span data-stu-id="25b31-279">Indicate if last SNMP request is GET or SET type</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-280">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-280">Prototype</span></span>

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

### <a name="description"></a><span data-ttu-id="25b31-281">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-281">Description</span></span>

<span data-ttu-id="25b31-282">このサービスでは、SNMP マネージャーから最後に受け取った要求が GET タイプ (GET、GETNEXT、または GETBULK) と SET タイプのどちらであるかを示します。</span><span class="sxs-lookup"><span data-stu-id="25b31-282">This service indicates if the most recent request from the SNMP Manager is a GET (GET, GETNEXT, or GETBULK) or SET type.</span></span> <span data-ttu-id="25b31-283">このサービスは、要求が GET タイプである場合は SNMPv1 または SNMPv2 アプリケーションで受信したコミュニティ文字列を SNMP エージェントのパブリック文字列と比較し、要求が SET タイプである場合は SNMP エージェントのプライベート文字列と比較するユーザー名コールバックと合わせて使用することを意図しています。</span><span class="sxs-lookup"><span data-stu-id="25b31-283">It is intended for use with the username callback where the SNMPv1 or SNMPv2 application will want to compare the received community string to the SNMP Agent public string if the request is a GET type, or to the SNMP Agent private string if the request is a SET type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-284">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-284">Input Parameters</span></span>

- <span data-ttu-id="25b31-285">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-285">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-286">**is_get_type** 要求のタイプへのポインター:</span><span class="sxs-lookup"><span data-stu-id="25b31-286">**is_get_type** Pointer to request type status:</span></span>  
<span data-ttu-id="25b31-287">GET タイプの場合は NX_TRUE</span><span class="sxs-lookup"><span data-stu-id="25b31-287">NX_TRUE if GET type</span></span>  
<span data-ttu-id="25b31-288">SET タイプの場合は NX_FALSE</span><span class="sxs-lookup"><span data-stu-id="25b31-288">NX_FALSE if SET type</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-289">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-289">Return Values</span></span>

- <span data-ttu-id="25b31-290">**NX_SUCCESS** (0x00) タイプを返すことに成功</span><span class="sxs-lookup"><span data-stu-id="25b31-290">**NX_SUCCESS** (0x00) Successfully returned type</span></span>
- <span data-ttu-id="25b31-291">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-291">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-292">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-292">Allowed From</span></span>

<span data-ttu-id="25b31-293">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-293">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-294">例</span><span class="sxs-lookup"><span data-stu-id="25b31-294">Example</span></span>

```c
UINT is_get_type;

/* Determine if the current SNMP request is a GET or SET type.  */
status =  nx_snmp_agent_request_get_type_test(&my_agent, &is_get_type);


/* If status is NX_SUCCESS, is_get_type will indicate the request type.  */
```

## <a name="nx_snmp_agent_context_engine_set"></a><span data-ttu-id="25b31-295">nx_snmp_agent_context_engine_set</span><span class="sxs-lookup"><span data-stu-id="25b31-295">nx_snmp_agent_context_engine_set</span></span>
<span data-ttu-id="25b31-296">コンテキスト エンジンを設定します (SNMP v3 のみ)</span><span class="sxs-lookup"><span data-stu-id="25b31-296">Set context engine (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-297">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-297">Prototype</span></span>

```c
UINT nx_snmp_agent_context_engine_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *context_engine, 
                                      UINT context_engine_size);
```
### <a name="description"></a><span data-ttu-id="25b31-298">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-298">Description</span></span>

<span data-ttu-id="25b31-299">このサービスでは、SNMP エージェントのコンテキスト エンジンを設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-299">This service sets the context engine of the SNMP Agent.</span></span> <span data-ttu-id="25b31-300">SNMPv3 の処理にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="25b31-300">It is only applicable for SNMPv3 processing.</span></span> <span data-ttu-id="25b31-301">コンテキスト エンジン ID はキーの作成に使用するため、アプリケーションで認証と暗号化を使用している場合は、セキュリティ キーを作成する前にこのサービスを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="25b31-301">This should be called before creating security keys if the application is using authentication and encryption, since the context engine ID is used in the key creation process.</span></span> <span data-ttu-id="25b31-302">その他の場合、NetX Duo SNMP では、*nxd_snmp.c* の冒頭に既定のコンテキスト エンジン ID を用意しています:</span><span class="sxs-lookup"><span data-stu-id="25b31-302">If not, NetX Duo SNMP provides a default context engine id at the top of *nxd_snmp.c:*</span></span>

```c
UCHAR _nx_snmp_default_context_engine[NX_SNMP_MAX_CONTEXT_STRING] =  
                {0x80, 0x00, 0x03, 0x10, 0x01, 0xc0, 0xa8, 0x64, 0xaf};

```

### <a name="input-parameters"></a><span data-ttu-id="25b31-303">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-303">Input Parameters</span></span>

- <span data-ttu-id="25b31-304">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-304">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-305">**context_engine** コンテキスト エンジンの文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-305">**context_engine** Pointer to the context engine string.</span></span>
- <span data-ttu-id="25b31-306">**context_engine_size** コンテキスト エンジンの文字列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="25b31-306">**context_engine_size** Size of context engine string.</span></span> <span data-ttu-id="25b31-307">コンテキスト エンジンの最大バイト数は、NX_SNMP_MAX_CONTEXT_STRING で指定されます。</span><span class="sxs-lookup"><span data-stu-id="25b31-307">Note that the maximum number of bytes in a context engine is defined by NX_SNMP_MAX_CONTEXT_STRING.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-308">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-308">Return Values</span></span>

- <span data-ttu-id="25b31-309">**NX_SUCCESS** (0x00) SNMP コンテキスト エンジンの設定に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-309">**NX_SUCCESS** (0x00) Successful SNMP context engine set.</span></span>
- <span data-ttu-id="25b31-310">**NX_NOT_ENABLED** (0x14) SNMPv3 が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="25b31-310">**NX_NOT_ENABLED** (0x14) SNMPv3 is not enabled</span></span>
- <span data-ttu-id="25b31-311">**NX_SNMP_ERROR** (0x100) コンテキスト エンジンのサイズのエラー。</span><span class="sxs-lookup"><span data-stu-id="25b31-311">**NX_SNMP_ERROR** (0x100) Context engine size error.</span></span>
- <span data-ttu-id="25b31-312">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-312">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-313">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-313">Allowed From</span></span>

<span data-ttu-id="25b31-314">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-314">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-315">例</span><span class="sxs-lookup"><span data-stu-id="25b31-315">Example</span></span>

```c
UCHAR my_engine[] = {0x80, 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07};

/* Set the context engine for my_agent.  */
status =  nx_snmp_agent_context_engine_set(&my_agent, my_engine, 9);


/* If status is NX_SUCCESS the context engine has been set.  */
```
## <a name="nx_snmp_agent_context_name_set"></a><span data-ttu-id="25b31-316">nx_snmp_agent_context_name_set</span><span class="sxs-lookup"><span data-stu-id="25b31-316">nx_snmp_agent_context_name_set</span></span>
<span data-ttu-id="25b31-317">コンテキスト名を設定します (SNMP v3 のみ)</span><span class="sxs-lookup"><span data-stu-id="25b31-317">Set context name (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-318">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-318">Prototype</span></span>

```c
UINT nx_snmp_agent_context_name_set(NX_SNMP_AGENT *agent_ptr, 
                                    UCHAR *context_name, 
                                    UINT context_name_size);
```

### <a name="description"></a><span data-ttu-id="25b31-319">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-319">Description</span></span>

<span data-ttu-id="25b31-320">このサービスでは、SNMP エージェントのコンテキスト名を設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-320">This service sets the context name of the SNMP Agent.</span></span> <span data-ttu-id="25b31-321">SNMPv3 の処理にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="25b31-321">It is only applicable for SNMPv3 processing.</span></span> <span data-ttu-id="25b31-322">これを呼び出さない場合、NetX Duo SNMP エージェントのコンテキスト名は空白のままになります。</span><span class="sxs-lookup"><span data-stu-id="25b31-322">If not called, NetX Duo SNMP Agent will leave the context name blank.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-323">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-323">Input Parameters</span></span>

- <span data-ttu-id="25b31-324">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-324">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-325">**context_name** コンテキスト名の文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-325">**context_name** Pointer to the context name string.</span></span>
- <span data-ttu-id="25b31-326">**context_name_size** コンテキスト名の文字列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="25b31-326">**context_name_size** Size of context name string.</span></span> <span data-ttu-id="25b31-327">コンテキスト名の最大バイト数は NX_SNMP_MAX_CONTEXT_STRING で指定されます。</span><span class="sxs-lookup"><span data-stu-id="25b31-327">Note that the maximum number of bytes in a context name is defined by NX_SNMP_MAX_CONTEXT_STRING.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-328">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-328">Return Values</span></span>

- <span data-ttu-id="25b31-329">**NX_SUCCESS** (0x00) SNMP コンテキスト名の設定に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-329">**NX_SUCCESS** (0x00) Successful SNMP context name set.</span></span>
- <span data-ttu-id="25b31-330">**NX_SNMP_ERROR** (0x100) コンテキスト名のサイズのエラー。</span><span class="sxs-lookup"><span data-stu-id="25b31-330">**NX_SNMP_ERROR** (0x100) Context name size error.</span></span>
- <span data-ttu-id="25b31-331">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-331">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-332">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-332">Allowed From</span></span>

<span data-ttu-id="25b31-333">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-333">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-334">例</span><span class="sxs-lookup"><span data-stu-id="25b31-334">Example</span></span>

```c
/* Set the context name for my_agent.  */
status =  nx_snmp_agent_context_name_set(&my_agent, “my_context_name”, 15);


/* If status is NX_SUCCESS the context name has been set.  */
```

## <a name="nx_snmp_agent_create"></a><span data-ttu-id="25b31-335">nx_snmp_agent_create</span><span class="sxs-lookup"><span data-stu-id="25b31-335">nx_snmp_agent_create</span></span>
<span data-ttu-id="25b31-336">SNMP エージェントを作成します</span><span class="sxs-lookup"><span data-stu-id="25b31-336">Create SNMP agent</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-337">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-337">Prototype</span></span>

```c
UINT nx_snmp_agent_create(NX_SNMP_AGENT *agent_ptr, 
      CHAR *snmp_agent_name, NX_IP *ip_ptr, VOID *stack_ptr, 
      ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*snmp_agent_username_process)(struct NX_SNMP_AGENT_STRUCT 
                                    *agent_ptr, UCHAR *username),
      UINT (*snmp_agent_get_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_getnext_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_set_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data));
```
### <a name="description"></a><span data-ttu-id="25b31-338">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-338">Description</span></span>

<span data-ttu-id="25b31-339">このサービスでは、指定した IP インスタンスに SNMP エージェントを作成します。</span><span class="sxs-lookup"><span data-stu-id="25b31-339">This service creates a SNMP Agent on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-340">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-340">Input Parameters</span></span>

- <span data-ttu-id="25b31-341">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-341">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-342">**snmp_agent_name** SNMP エージェント名の文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-342">**snmp_agent_name** Pointer to the SNMP Agent name string.</span></span>
- <span data-ttu-id="25b31-343">**ip_ptr** IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-343">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="25b31-344">**stack_ptr** SNMP エージェントのスレッド スタックへのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-344">**stack_ptr** Pointer to SNMP Agent thread stack pointer.</span></span>
- <span data-ttu-id="25b31-345">**stack_size** byte 単位のスタック サイズ。</span><span class="sxs-lookup"><span data-stu-id="25b31-345">**stack_size** Stack size in bytes.</span></span>
- <span data-ttu-id="25b31-346">**pool_ptr** この SNMP エージェントの既定のパケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-346">**pool_ptr** Pointer the default packet pool for this SNMP Agent.</span></span>
- <span data-ttu-id="25b31-347">**snmp_agent_username_process** アプリケーションのユーザー名処理ルーチンへの関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-347">**snmp_agent_username_process** Function pointer to application’s username handling routine.</span></span>
- <span data-ttu-id="25b31-348">**snmp_agent_get_process** アプリケーションの GET 要求処理ルーチンへの関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-348">**snmp_agent_get_process** Function pointer to application’s GET request handling routine.</span></span>
- <span data-ttu-id="25b31-349">**snmp_agent_getnext_process** アプリケーションの GETNEXT 要求処理ルーチンへの関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-349">**snmp_agent_getnext_process** Function pointer to application’s GETNEXT request handling routine.</span></span>
- <span data-ttu-id="25b31-350">**snmp_agent_set_process** アプリケーションの SET 要求処理ルーチンへの関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-350">**snmp_agent_set_process** Function pointer to application’s SET request handling routine.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-351">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-351">Return Values</span></span>

- <span data-ttu-id="25b31-352">**NX_SUCCESS** (0x00) SNMP エージェントの作成に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-352">**NX_SUCCESS** (0x00) Successful SNMP Agent create.</span></span>
- <span data-ttu-id="25b31-353">**NX_SNMP_ERROR** (0x100) SNMP エージェント作成エラー。</span><span class="sxs-lookup"><span data-stu-id="25b31-353">**NX_SNMP_ERROR** (0x100) SNMP Agent create error.</span></span>
- <span data-ttu-id="25b31-354">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-354">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-355">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-355">Allowed From</span></span>

<span data-ttu-id="25b31-356">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-356">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-357">例</span><span class="sxs-lookup"><span data-stu-id="25b31-357">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Create the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_create(&my_agent, "My SNMP Agent", &ip_0, stack_start_ptr,
                4096, &pool_0, my_username_processing, my_get_processing, 
                my_getnext_processing, my_set_processing);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been created.  */
```

## <a name="nx_snmp_agent_current_version_get"></a><span data-ttu-id="25b31-358">nx_snmp_agent_current_version_get</span><span class="sxs-lookup"><span data-stu-id="25b31-358">nx_snmp_agent_current_version_get</span></span>
<span data-ttu-id="25b31-359">SNMP パケットのバージョンを取得します</span><span class="sxs-lookup"><span data-stu-id="25b31-359">Get the SNMP packet version</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-360">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-360">Prototype</span></span>

```c
UINT nx_snmp_agent_current_version_get(NX_SNMP_AGENT *agent_ptr, 
                                       UINT *version);
```

### <a name="description"></a><span data-ttu-id="25b31-361">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-361">Description</span></span>

<span data-ttu-id="25b31-362">このサービスでは、最後に受信した SNMP パケットを解析して SNMP のバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="25b31-362">This service retrieves the SNMP version parsed from the most recent SNMP packet received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-363">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-363">Input Parameters</span></span>

- <span data-ttu-id="25b31-364">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-364">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-365">**version** 受信した SNMP パケットを解析して得た SNMP のバージョンへのポインター</span><span class="sxs-lookup"><span data-stu-id="25b31-365">**version** Pointer to the SNMP version parsed from received SNMP packet</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-366">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-366">Return Values</span></span>

- <span data-ttu-id="25b31-367">**NX_SUCCESS** (0x00) SNMP のバージョンの取得に成功</span><span class="sxs-lookup"><span data-stu-id="25b31-367">**NX_SUCCESS** (0x00) Successful SNMP version get</span></span>
- <span data-ttu-id="25b31-368">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-368">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-369">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-369">Allowed From</span></span>

<span data-ttu-id="25b31-370">Threads</span><span class="sxs-lookup"><span data-stu-id="25b31-370">Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-371">例</span><span class="sxs-lookup"><span data-stu-id="25b31-371">Example</span></span>

```c
UINT          snmp_version;
NX_SNMP_AGENT my_agent;

/* Get the version of the last received SNMP packet. */
status =  nx_snmp_agent_current_version_get (&my_agent, &snmp_version);


/* If status is NX_SUCCESS, snmp_version contains 
   the received packet SNMP version.  */
```

## <a name="nx_snmp_agent_private_string_test"></a><span data-ttu-id="25b31-372">nx_snmp_agent_private_string_test</span><span class="sxs-lookup"><span data-stu-id="25b31-372">nx_snmp_agent_private_string_test</span></span>
<span data-ttu-id="25b31-373">プライベート文字列がエージェントのプライベート文字列と一致することを確認します</span><span class="sxs-lookup"><span data-stu-id="25b31-373">Verify private string matches Agent private string</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-374">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-374">Prototype</span></span>

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr, 
                                       UCHAR *community_string,          
                                       UINT *is_private);
```

### <a name="description"></a><span data-ttu-id="25b31-375">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-375">Description</span></span>

<span data-ttu-id="25b31-376">このサービスでは、NULL で終わる入力コミュニティ文字列を SNMP エージェントのプライベート文字列と比較して、一致するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="25b31-376">This service compares the null terminated input community string with the SNMP agent private string and indicates if they match.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-377">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-377">Input Parameters</span></span>

- <span data-ttu-id="25b31-378">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-378">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-379">**community_string** 比較する文字列へのポインター</span><span class="sxs-lookup"><span data-stu-id="25b31-379">**community_string** Pointer to string to compare</span></span>
- <span data-ttu-id="25b31-380">**is_private** 比較結果へのポインター</span><span class="sxs-lookup"><span data-stu-id="25b31-380">**is_private** Pointer to result of comparison</span></span>  
<span data-ttu-id="25b31-381">NX_TRUE - 文字列が一致します</span><span class="sxs-lookup"><span data-stu-id="25b31-381">NX_TRUE - string matches</span></span>  
<span data-ttu-id="25b31-382">NX_FALSE - 文字列が一致しません</span><span class="sxs-lookup"><span data-stu-id="25b31-382">NX_FALSE - string does not match</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-383">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-383">Return Values</span></span>

- <span data-ttu-id="25b31-384">**NX_SUCCESS** (0x00) 比較に成功</span><span class="sxs-lookup"><span data-stu-id="25b31-384">**NX_SUCCESS** (0x00) Successful comparison</span></span>
- <span data-ttu-id="25b31-385">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-385">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-386">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-386">Allowed From</span></span>

<span data-ttu-id="25b31-387">Threads</span><span class="sxs-lookup"><span data-stu-id="25b31-387">Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-388">例</span><span class="sxs-lookup"><span data-stu-id="25b31-388">Example</span></span>

```c
UINT        is_private;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;

/* Determine if the community string matches the agent private string */
status =  nx_snmp_agent_private_string_test(&my_agent, community_string_ptr,  
                                            &is_private);


/* If status is NX_SUCCESS, is_private will indicate if there is a match. 
   If is_private is NX_TRUE, they match.  */
```

## <a name="nx_snmp_agent_public_string_test"></a><span data-ttu-id="25b31-389">nx_snmp_agent_public_string_test</span><span class="sxs-lookup"><span data-stu-id="25b31-389">nx_snmp_agent_public_string_test</span></span>
<span data-ttu-id="25b31-390">受信したパブリック文字列がエージェントのパブリック文字列と一致することを確認します</span><span class="sxs-lookup"><span data-stu-id="25b31-390">Verify received public string matches Agent’s public string</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-391">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-391">Prototype</span></span>

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string,          
                                      UINT *is_public);
```
### <a name="description"></a><span data-ttu-id="25b31-392">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-392">Description</span></span>

<span data-ttu-id="25b31-393">このサービスでは、NULL で終わる入力コミュニティ文字列を SNMP エージェントのパブリック文字列と比較し、一致するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="25b31-393">This service compares a null terminated input community string with the SNMP agent public string and indicates if they match.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-394">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-394">Input Parameters</span></span>

- <span data-ttu-id="25b31-395">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-395">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-396">**community_string** 比較する文字列へのポインター</span><span class="sxs-lookup"><span data-stu-id="25b31-396">**community_string** Pointer to string to compare</span></span>
- <span data-ttu-id="25b31-397">**is_public** 比較結果へのポインター</span><span class="sxs-lookup"><span data-stu-id="25b31-397">**is_public** Pointer to result of comparison</span></span>  
<span data-ttu-id="25b31-398">NX_TRUE - 文字列が一致します</span><span class="sxs-lookup"><span data-stu-id="25b31-398">NX_TRUE - string matches</span></span>  
<span data-ttu-id="25b31-399">NX_FALSE - 文字列が一致しません</span><span class="sxs-lookup"><span data-stu-id="25b31-399">NX_FALSE - string does not match</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-400">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-400">Return Values</span></span>

- <span data-ttu-id="25b31-401">**NX_SUCCESS** (0x00) 比較に成功</span><span class="sxs-lookup"><span data-stu-id="25b31-401">**NX_SUCCESS** (0x00) Successful comparison</span></span>
- <span data-ttu-id="25b31-402">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-402">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-403">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-403">Allowed From</span></span>

<span data-ttu-id="25b31-404">Threads</span><span class="sxs-lookup"><span data-stu-id="25b31-404">Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-405">例</span><span class="sxs-lookup"><span data-stu-id="25b31-405">Example</span></span>

```c
UINT        is_public;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;


/* Determine if the community string matches the agent public string */
status =  nx_snmp_agent_public_string_test(&my_agent, community_string_ptr,  
                                           &is_public);


/* If status is NX_SUCCESS, is_public will indicate if there is a match. 
   If is_public is true they match.  */
```

## <a name="nx_snmp_agent_version_set"></a><span data-ttu-id="25b31-406">nx_snmp_agent_version_set</span><span class="sxs-lookup"><span data-stu-id="25b31-406">nx_snmp_agent_version_set</span></span>
<span data-ttu-id="25b31-407">SNMP の各バージョンに対する SNMP エージェントの状態を設定します</span><span class="sxs-lookup"><span data-stu-id="25b31-407">Set the SNMP agent status for each SNMP version</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-408">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-408">Prototype</span></span>

```c
UINT nx_snmp_agent_version_set(NX_SNMP_AGENT *agent_ptr, 
                               UINT enabled_v1, UINT enable_v2, 
                               UINT enable_v3);
```

### <a name="description"></a><span data-ttu-id="25b31-409">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-409">Description</span></span>

<span data-ttu-id="25b31-410">このサービスでは、 SNMP の各バージョン (V1、V2、V3) に対する SNMP エージェントの状態 (有効/無効) を設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-410">This service sets the status (enabled/disabled) for each of the SNMP versions, V1, V2 and V3 on the SNMP agent.</span></span> <span data-ttu-id="25b31-411">これらのランタイム設定よりも、ユーザーが構成できるオプション、NX_SNMP_DISABLE_V1、NX_SNMP_DISABLE_V2、 NX_SNMP_DISABLE_V3 の効果が優先されます。</span><span class="sxs-lookup"><span data-stu-id="25b31-411">Note that the user configurable options, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2, and NX_SNMP_DISABLE_V3, will override these run time settings.</span></span> <span data-ttu-id="25b31-412">既定では、SNMP エージェントは 3 つのバージョンすべてに対して有効になっています。</span><span class="sxs-lookup"><span data-stu-id="25b31-412">By default, the SNMP agent is enabled for all three versions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-413">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-413">Input Parameters</span></span>

- <span data-ttu-id="25b31-414">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-414">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-415">**enabled_v1** SNMP V1 に対する有効/無効を設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-415">**enabled_v1** Sets enabled status for SNMP V1 to on/off.</span></span>
- <span data-ttu-id="25b31-416">**enabled_v2** SNMP V2 に対する有効/無効を設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-416">**enabled_v2** Sets enabled status for SNMP V2 to on/off.</span></span>
- <span data-ttu-id="25b31-417">**enabled_v3** SNMP V3 に対する有効/無効を設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-417">**enabled_v3** Sets enabled status for SNMP V3 to on/off.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-418">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-418">Return Values</span></span>

- <span data-ttu-id="25b31-419">**NX_SUCCESS** (0x00) SNMP バージョンに対する設定に成功</span><span class="sxs-lookup"><span data-stu-id="25b31-419">**NX_SUCCESS** (0x00) Successful SNMP version set</span></span>
- <span data-ttu-id="25b31-420">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-420">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-421">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-421">Allowed From</span></span>

<span data-ttu-id="25b31-422">Threads</span><span class="sxs-lookup"><span data-stu-id="25b31-422">Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-423">例</span><span class="sxs-lookup"><span data-stu-id="25b31-423">Example</span></span>

```c
UINT          v1_on = NX_TRUE;
UINT          v2_on = NX_TRUE;
UINT          v3_on = NX_FALSE;

NX_SNMP_AGENT my_agent;

/* Enable/Disable each SNMP protocol (version) for the SNMP Agent) */
status =  nx_snmp_agent_version_set(&my_agent, v1_on, v2_on, v3_on);


/* If status is NX_SUCCESS, my_agent is enabled only for V1 and V2 assuming 
   NX_SNMP_DISABLE_V1 and NX_SNMP_DISABLE_V2 are not defined. */
```

## <a name="nx_snmp_agent_private_string_set"></a><span data-ttu-id="25b31-424">nx_snmp_agent_private_string_set</span><span class="sxs-lookup"><span data-stu-id="25b31-424">nx_snmp_agent_private_string_set</span></span>
<span data-ttu-id="25b31-425">SNMP エージェントのプライベート文字列を設定します</span><span class="sxs-lookup"><span data-stu-id="25b31-425">Set the SNMP agent private string</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-426">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-426">Prototype</span></span>

```c
UINT nx_snmp_agent_private_string_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string);
```

### <a name="description"></a><span data-ttu-id="25b31-427">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-427">Description</span></span>

<span data-ttu-id="25b31-428">このサービスは、NULL で終わる入力文字列を使用して、SNMP エージェントのプライベート コミュニティ文字列を設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-428">This service sets the SNMP agent private community string with the input null terminated string.</span></span> <span data-ttu-id="25b31-429">既定値は NULL です (プライベート文字列が設定されていない状態)。そのため、受信した SNMP パケットが “プライベート” コミュニティ文字列を含む場合、SNMP エージェントで読み取り/書き込みはできません。</span><span class="sxs-lookup"><span data-stu-id="25b31-429">The default value is NULL (no private string set), such that any SNMP packet received with a “private” community string will not be accepted by the SNMP agent for read/write access.</span></span> <span data-ttu-id="25b31-430">入力文字列は、ユーザーが構成できる NX_SNMP_MAX_USER_NAME-1 のサイズ以下である必要があります (NULL 終端のスペースを確保するため)。</span><span class="sxs-lookup"><span data-stu-id="25b31-430">The input string must be less than or equal to the user configurable NX_SNMP_MAX_USER_NAME-1 (to allow room for null termination) size.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-431">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-431">Input Parameters</span></span>

- <span data-ttu-id="25b31-432">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-432">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-433">**community_string** 割り当てるプライベート文字列へのポインター</span><span class="sxs-lookup"><span data-stu-id="25b31-433">**community_string** Pointer to the private string to assign</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-434">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-434">Return Values</span></span>

- <span data-ttu-id="25b31-435">**NX_SUCCESS** (0x00) プライベート文字列の設定に成功</span><span class="sxs-lookup"><span data-stu-id="25b31-435">**NX_SUCCESS** (0x00) Successfully set private string</span></span>
- <span data-ttu-id="25b31-436">**NX_SNMP_ERROR_TOOBIG** (0x01) 文字列のサイズが大きすぎます</span><span class="sxs-lookup"><span data-stu-id="25b31-436">**NX_SNMP_ERROR_TOOBIG** (0x01) String size too large</span></span> 
- <span data-ttu-id="25b31-437">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-437">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-438">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-438">Allowed From</span></span>

<span data-ttu-id="25b31-439">Threads</span><span class="sxs-lookup"><span data-stu-id="25b31-439">Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-440">例</span><span class="sxs-lookup"><span data-stu-id="25b31-440">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s private community string */
status =  nx_snmp_agent_private_string_set(&my_agent, “private”));


/* If status is NX_SUCCESS, the SNMP agent private string is set.  */
```

## <a name="nx_snmp_agent_public_string_set"></a><span data-ttu-id="25b31-441">nx_snmp_agent_public_string_set</span><span class="sxs-lookup"><span data-stu-id="25b31-441">nx_snmp_agent_public_string_set</span></span>
<span data-ttu-id="25b31-442">SNMP エージェントのパブリック文字列を設定します</span><span class="sxs-lookup"><span data-stu-id="25b31-442">Set the SNMP agent public string</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-443">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-443">Prototype</span></span>

```c
UINT nx_snmp_agent_public_string_set(NX_SNMP_AGENT *agent_ptr, 
                                     UCHAR *community_string);
```

### <a name="description"></a><span data-ttu-id="25b31-444">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-444">Description</span></span>

<span data-ttu-id="25b31-445">このサービスでは、NULL で終わる入力文字列を使用して、SNMP エージェントのパブリック コミュニティ文字列を設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-445">This service sets the SNMP agent public community string with the input null terminated string.</span></span> <span data-ttu-id="25b31-446">コミュニティ文字列は、ユーザーが構成できる NX_SNMP_MAX_USER_NAME-1 のサイズ以下である必要があります (NULL 終端のスペースを確保するため)。</span><span class="sxs-lookup"><span data-stu-id="25b31-446">The community string must be less than or equal to the user configurable NX_SNMP_MAX_USER_NAME-1 (to allow room for null termination) size.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-447">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-447">Input Parameters</span></span>

- <span data-ttu-id="25b31-448">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-448">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-449">**community_string** 割り当てるパブリック文字列へのポインター</span><span class="sxs-lookup"><span data-stu-id="25b31-449">**community_string** Pointer to the public string to assign</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-450">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-450">Return Values</span></span>

- <span data-ttu-id="25b31-451">**NX_SUCCESS** (0x00) パブリック文字列の設定に成功</span><span class="sxs-lookup"><span data-stu-id="25b31-451">**NX_SUCCESS** (0x00) Successfully set public string</span></span>
- <span data-ttu-id="25b31-452">**NX_SNMP_ERROR_TOOBIG** (0x01) 文字列のサイズが大きすぎます</span><span class="sxs-lookup"><span data-stu-id="25b31-452">**NX_SNMP_ERROR_TOOBIG** (0x01) String size too large</span></span>
- <span data-ttu-id="25b31-453">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-453">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-454">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-454">Allowed From</span></span>

<span data-ttu-id="25b31-455">Threads</span><span class="sxs-lookup"><span data-stu-id="25b31-455">Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-456">例</span><span class="sxs-lookup"><span data-stu-id="25b31-456">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s public string. */
nx_snmp_agent_public_string_set(&my_agent, “my_public”));


/* If status is NX_SUCCESS, the SNMP agent public string is set.  */
```

## <a name="nx_snmp_agent_delete"></a><span data-ttu-id="25b31-457">nx_snmp_agent_delete</span><span class="sxs-lookup"><span data-stu-id="25b31-457">nx_snmp_agent_delete</span></span>
<span data-ttu-id="25b31-458">SNMP エージェントを削除します</span><span class="sxs-lookup"><span data-stu-id="25b31-458">Delete SNMP agent</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-459">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-459">Prototype</span></span>

```C
UINT nx_snmp_agent_delete(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="25b31-460">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-460">Description</span></span>

<span data-ttu-id="25b31-461">このサービスでは、作成済みの SNMP エージェントを削除します。</span><span class="sxs-lookup"><span data-stu-id="25b31-461">This service deletes a previously created SNMP Agent.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-462">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-462">Input Parameters</span></span>

- <span data-ttu-id="25b31-463">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-463">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-464">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-464">Return Values</span></span>

- <span data-ttu-id="25b31-465">**NX_SUCCESS** (0x00) SNMP エージェントの削除に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-465">**NX_SUCCESS** (0x00) Successful SNMP Agent delete.</span></span>
- <span data-ttu-id="25b31-466">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-466">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-467">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-467">Allowed From</span></span>

<span data-ttu-id="25b31-468">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-468">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-469">例</span><span class="sxs-lookup"><span data-stu-id="25b31-469">Example</span></span>

```c
/* Delete the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_delete(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been deleted.  */
```

## <a name="nx_snmp_agent_set_interface"></a><span data-ttu-id="25b31-470">nx_snmp_agent_set_interface</span><span class="sxs-lookup"><span data-stu-id="25b31-470">nx_snmp_agent_set_interface</span></span>
<span data-ttu-id="25b31-471">SNMP エージェントのネットワーク インターフェイスを設定します</span><span class="sxs-lookup"><span data-stu-id="25b31-471">Set the SNMP agent network interface</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-472">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-472">Prototype</span></span>

```c
UINT nx_snmp_agent_set_interface(NX_SNMP_AGENT *agent_ptr,  
                                 UINT if_index);
```

### <a name="description"></a><span data-ttu-id="25b31-473">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-473">Description</span></span>

<span data-ttu-id="25b31-474">このサービスでは、インターフェイス インデックスの指定に基づいて、SNMP エージェントの SNMP ネットワーク インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-474">This service sets the SNMP network interface for the SNMP Agent as specified by the input interface index.</span></span> <span data-ttu-id="25b31-475">複数のネットワーク インターフェイスをサポートしているバージョン 5.6 以降の NetX Duo を SNMP ホスト アプリケーションで使用する場合のみ、このサービスは役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="25b31-475">This is only useful for SNMP host applications with NetX Duo 5.6 or higher which support multiple network interfaces.</span></span> <span data-ttu-id="25b31-476">ホストで指定しない場合、プライマリ インターフェイスの既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="25b31-476">The default value if not specified by the host is zero, for the primary interface.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-477">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-477">Input Parameters</span></span>

- <span data-ttu-id="25b31-478">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-478">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-479">**If_index** SNMP インターフェイスを指定するインデックス。</span><span class="sxs-lookup"><span data-stu-id="25b31-479">**If_index** Index specifying the SNMP interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-480">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-480">Return Values</span></span>

- <span data-ttu-id="25b31-481">**NX_SUCCESS** (0x00) SNMP インターフェイスの設定に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-481">**NX_SUCCESS** (0x00) Successful SNMP interface set.</span></span>
- <span data-ttu-id="25b31-482">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-482">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-483">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-483">Allowed From</span></span>

<span data-ttu-id="25b31-484">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-484">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-485">例</span><span class="sxs-lookup"><span data-stu-id="25b31-485">Example</span></span>

```c
/* Set the SNMP Agent “my_agent” to the secondary interface.  */
if_index = 1;
status =  nx_snmp_agent_set_interface(&my_agent, if_index);


/* If status is NX_SUCCESS the SNMP agent interface is set.  */
```

## <a name="nx_snmp_agent_md5_key_create"></a><span data-ttu-id="25b31-486">nx_snmp_agent_md5_key_create</span><span class="sxs-lookup"><span data-stu-id="25b31-486">nx_snmp_agent_md5_key_create</span></span>
<span data-ttu-id="25b31-487">MD5 キーを作成します (SNMP v3 のみ)</span><span class="sxs-lookup"><span data-stu-id="25b31-487">Create md5 key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-488">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-488">Prototype</span></span>

```c
UINT nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY 
                                       *destination_key);
```
### <a name="description"></a><span data-ttu-id="25b31-489">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-489">Description</span></span>

<span data-ttu-id="25b31-490">このサービスでは、認証と暗号化に使用できる MD5 キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="25b31-490">This service creates a MD5 key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="25b31-491">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="25b31-491">This service is deprecated.</span></span> <span data-ttu-id="25b31-492">開発者は *nx_snmp_agent_md5_key_create_extended()* に移行することを推奨します。</span><span class="sxs-lookup"><span data-stu-id="25b31-492">Developers are encouraged to migrate to *nx_snmp_agent_md5_key_create_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-493">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-493">Input Parameters</span></span>

- <span data-ttu-id="25b31-494">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-494">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-495">**password** パスワードの文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-495">**password** Pointer to password string.</span></span>
- <span data-ttu-id="25b31-496">**destination_key** SNMP のキーのデータ構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-496">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-497">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-497">Return Values</span></span>

- <span data-ttu-id="25b31-498">**NX_SUCCESS** (0x00) キーの作成に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-498">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="25b31-499">**NX_NOT_ENABLED** (0x14) セキュリティが有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="25b31-499">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="25b31-500">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-500">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-501">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-501">Allowed From</span></span>

<span data-ttu-id="25b31-502">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-502">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-503">例</span><span class="sxs-lookup"><span data-stu-id="25b31-503">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS an MD5 key has been created.  */
```

## <a name="nx_snmp_agent_md5_key_create_extended"></a><span data-ttu-id="25b31-504">nx_snmp_agent_md5_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="25b31-504">nx_snmp_agent_md5_key_create_extended</span></span>
<span data-ttu-id="25b31-505">MD5 キーを作成します (SNMP v3 のみ)</span><span class="sxs-lookup"><span data-stu-id="25b31-505">Create md5 key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-506">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-506">Prototype</span></span>

```c
UINT nx_snmp_agent_md5_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY 
                                           *destination_key);
```
### <a name="description"></a><span data-ttu-id="25b31-507">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-507">Description</span></span>

<span data-ttu-id="25b31-508">このサービスでは、認証と暗号化に使用できる MD5 キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="25b31-508">This service creates a MD5 key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="25b31-509">これは *nx_snmp_agent_md5_key_create()* の後継サービスです。</span><span class="sxs-lookup"><span data-stu-id="25b31-509">This service replaces *nx_snmp_agent_md5_key_create().*</span></span> <span data-ttu-id="25b31-510">このバージョンでは、呼び出し元でパスワードの長さを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25b31-510">This version requires caller to supply password length.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-511">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-511">Input Parameters</span></span>

- <span data-ttu-id="25b31-512">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-512">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-513">**password** パスワードの文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-513">**password** Pointer to password string.</span></span>
- <span data-ttu-id="25b31-514">**password_length** パスワードの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="25b31-514">**password_length** Length of password string.</span></span>
- <span data-ttu-id="25b31-515">**destination_key** SNMP のキーのデータ構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-515">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-516">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-516">Return Values</span></span>

- <span data-ttu-id="25b31-517">**NX_SUCCESS** (0x00) キーの作成に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-517">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="25b31-518">**NX_NOT_ENABLED** (0x14) セキュリティが有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="25b31-518">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="25b31-519">**NX_SNMP_FAILED** (0x102) SNMP が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="25b31-519">**NX_SNMP_FAILED** (0x102) SNMP failed.</span></span>
- <span data-ttu-id="25b31-520">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-520">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-521">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-521">Allowed From</span></span>

<span data-ttu-id="25b31-522">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-522">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-523">例</span><span class="sxs-lookup"><span data-stu-id="25b31-523">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_priv_trap_key_use"></a><span data-ttu-id="25b31-524">nx_snmp_agent_priv_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="25b31-524">nx_snmp_agent_priv_trap_key_use</span></span>
<span data-ttu-id="25b31-525">トラップ メッセージの暗号化キーを指定します</span><span class="sxs-lookup"><span data-stu-id="25b31-525">Specify encryption key for trap messages</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-526">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-526">Prototype</span></span>

```c
UINT nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```

### <a name="description"></a><span data-ttu-id="25b31-527">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-527">Description</span></span>

<span data-ttu-id="25b31-528">このサービスでは、作成済みのプライバシー キーを使用して SNMPv3 トラップ メッセージの暗号化と復号を行うよう指定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-528">This service specifies that a previously created privacy key is to be used for encryption and decryption of SNMPv3 trap messages.</span></span>

> [!NOTE]
> <span data-ttu-id="25b31-529">*認証キーを前もって作成しておく必要があります。SNMP v3 のプライバシー (暗号化) には認証が必要です。詳細は nx_snmp_agent_auth_trap_key_use をご覧ください。*</span><span class="sxs-lookup"><span data-stu-id="25b31-529">*An authentictation key must be previously created. SNMP v3 privacy (encryption) requires authentication. See nx_snmp_agent_auth_trap_key_use for details.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-530">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-530">Input Parameters</span></span>

- <span data-ttu-id="25b31-531">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-531">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-532">**key** 作成済みのキーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-532">**key** Pointer to previously create key.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-533">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-533">Return Values</span></span>

- <span data-ttu-id="25b31-534">**NX_SUCCESS** (0x00) パライバシー キーの設定に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-534">**NX_SUCCESS** (0x00) Successful privacy key set.</span></span>
- <span data-ttu-id="25b31-535">**NX_NOT_ENABLED** (0x14) セキュリティが有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="25b31-535">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="25b31-536">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-536">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-537">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-537">Allowed From</span></span>

<span data-ttu-id="25b31-538">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-538">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-539">例</span><span class="sxs-lookup"><span data-stu-id="25b31-539">Example</span></span>

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent” trap messages.   */
status =  nx_snmp_agent_priv_trap_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_privacy_key_use"></a><span data-ttu-id="25b31-540">nx_snmp_agent_privacy_key_use</span><span class="sxs-lookup"><span data-stu-id="25b31-540">nx_snmp_agent_privacy_key_use</span></span>
<span data-ttu-id="25b31-541">応答メッセージの暗号化キーを指定します</span><span class="sxs-lookup"><span data-stu-id="25b31-541">Specify encryption key for response messages</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-542">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-542">Prototype</span></span>

```c
UINT nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr, 
                                   NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="25b31-543">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-543">Description</span></span>

<span data-ttu-id="25b31-544">このサービスでは、作成済みのキーを使用して SNMPv3 の応答メッセージの暗号化と復号を行うよう指定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-544">This service specifies that the previously created key is to be used for encryption and decryption of SNMPv3 response messages.</span></span>

> [!NOTE]
> <span data-ttu-id="25b31-545">*認証キーを前もって指定しておく必要があります。SNMPv3 の暗号化では認証キーの作成も必要です。詳細は nx_snmp_agent_authentiation_key_use をご覧ください。*</span><span class="sxs-lookup"><span data-stu-id="25b31-545">*An authentication key must have previously been specified. SNMP v3 encryption requires creation of an authentication key as well. See nx_snmp_agent_authentiation_key_use for details.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-546">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-546">Input Parameters</span></span>

- <span data-ttu-id="25b31-547">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-547">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-548">**key** 作成済みのキーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-548">**key** Pointer to previously create key.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-549">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-549">Return Values</span></span>

- <span data-ttu-id="25b31-550">**NX_SUCCESS** (0x00) パライバシー キーの設定に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-550">**NX_SUCCESS** (0x00) Successful privacy key set.</span></span>
- <span data-ttu-id="25b31-551">**NX_NOT_ENABLED** (0x14) セキュリティが有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="25b31-551">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="25b31-552">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-552">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-553">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-553">Allowed From</span></span>

<span data-ttu-id="25b31-554">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-554">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-555">例</span><span class="sxs-lookup"><span data-stu-id="25b31-555">Example</span></span>

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_sha_key_create"></a><span data-ttu-id="25b31-556">nx_snmp_agent_sha_key_create</span><span class="sxs-lookup"><span data-stu-id="25b31-556">nx_snmp_agent_sha_key_create</span></span>
<span data-ttu-id="25b31-557">SHA キーを作成します (SNMP v3 のみ)</span><span class="sxs-lookup"><span data-stu-id="25b31-557">Create SHA key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-558">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-558">Prototype</span></span>

```c
UINT nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY  
                                  *destination_key);
```
### <a name="description"></a><span data-ttu-id="25b31-559">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-559">Description</span></span>

<span data-ttu-id="25b31-560">このサービスでは、認証と暗号化に使用できる SHA キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="25b31-560">This service creates a SHA key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="25b31-561">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="25b31-561">This service is deprecated.</span></span> <span data-ttu-id="25b31-562">開発者は *nx_snmp_agent_sha_key_create_extended()* に移行することを推奨します。</span><span class="sxs-lookup"><span data-stu-id="25b31-562">Developers are encouraged to migrate to *nx_snmp_agent_sha_key_create_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-563">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-563">Input Parameters</span></span>

- <span data-ttu-id="25b31-564">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-564">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-565">**password** パスワードの文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-565">**password** Pointer to password string.</span></span>
- <span data-ttu-id="25b31-566">**destination_key** SNMP のキーのデータ構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-566">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-567">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-567">Return Values</span></span>

- <span data-ttu-id="25b31-568">**NX_SUCCESS** (0x00) キーの作成に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-568">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="25b31-569">**NX_SNMP_ERROR** (0x100) キー作成エラー。</span><span class="sxs-lookup"><span data-stu-id="25b31-569">**NX_SNMP_ERROR** (0x100) Key create error.</span></span>
- <span data-ttu-id="25b31-570">**NX_PTR_ERROR** (0x07) SNMP エージェントまたはキーへのポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-570">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent or key pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-571">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-571">Allowed From</span></span>

<span data-ttu-id="25b31-572">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-572">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-573">例</span><span class="sxs-lookup"><span data-stu-id="25b31-573">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_sha_key_create_extended"></a><span data-ttu-id="25b31-574">nx_snmp_agent_sha_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="25b31-574">nx_snmp_agent_sha_key_create_extended</span></span>
<span data-ttu-id="25b31-575">SHA キーを作成します (SNMP v3 のみ)</span><span class="sxs-lookup"><span data-stu-id="25b31-575">Create SHA key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-576">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-576">Prototype</span></span>

```c
UINT nx_snmp_agent_sha_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY  
                                           *destination_key);
```
### <a name="description"></a><span data-ttu-id="25b31-577">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-577">Description</span></span>

<span data-ttu-id="25b31-578">このサービスでは、認証と暗号化に使用できる SHA キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="25b31-578">This service creates a SHA key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="25b31-579">これは *nx_snmp_agent_sha_key_create()* の後継サービスです。</span><span class="sxs-lookup"><span data-stu-id="25b31-579">This service replaces *nx_snmp_agent_sha_key_create().*</span></span> <span data-ttu-id="25b31-580">このバージョンでは、呼び出し元でパスワードの長さを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25b31-580">This version requires caller to supply password length.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-581">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-581">Input Parameters</span></span>

- <span data-ttu-id="25b31-582">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-582">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-583">**password** パスワードの文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-583">**password** Pointer to password string.</span></span>
- <span data-ttu-id="25b31-584">**password_length** パスワードの文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="25b31-584">**password_length** Length of password string.</span></span>
- <span data-ttu-id="25b31-585">**destination_key** SNMP のキーのデータ構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-585">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-586">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-586">Return Values</span></span>

- <span data-ttu-id="25b31-587">**NX_SUCCESS** (0x00) キーの作成に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-587">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="25b31-588">**NX_SNMP_ERROR** (0x100) キー作成エラー。</span><span class="sxs-lookup"><span data-stu-id="25b31-588">**NX_SNMP_ERROR** (0x100) Key create error.</span></span>
- <span data-ttu-id="25b31-589">**NX_SNMP_FAILED** (0x102) キー作成に失敗。</span><span class="sxs-lookup"><span data-stu-id="25b31-589">**NX_SNMP_FAILED** (0x102) Key create failed.</span></span>
- <span data-ttu-id="25b31-590">**NX_PTR_ERROR** (0x07) SNMP エージェントまたはキーへのポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-590">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent or key pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-591">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-591">Allowed From</span></span>

<span data-ttu-id="25b31-592">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-592">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-593">例</span><span class="sxs-lookup"><span data-stu-id="25b31-593">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_start"></a><span data-ttu-id="25b31-594">nx_snmp_agent_start</span><span class="sxs-lookup"><span data-stu-id="25b31-594">nx_snmp_agent_start</span></span>
<span data-ttu-id="25b31-595">SNMP エージェントを起動します</span><span class="sxs-lookup"><span data-stu-id="25b31-595">Start SNMP agent</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-596">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-596">Prototype</span></span>

```c
UINT nx_snmp_agent_start(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="25b31-597">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-597">Description</span></span>

<span data-ttu-id="25b31-598">このサービスでは、UDP ソケットを 161 番の SNMP ポートにバインドし、SNMP エージェントのスレッドのタスクを開始します。</span><span class="sxs-lookup"><span data-stu-id="25b31-598">This service binds the UDP socket to the SNMP port 161 and starts the SNMP Agent thread task.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-599">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-599">Input Parameters</span></span>

- <span data-ttu-id="25b31-600">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-600">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-601">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-601">Return Values</span></span>

- <span data-ttu-id="25b31-602">**NX_SUCCESS** (0x00) SNMP エージェントの起動に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-602">**NX_SUCCESS** (0x00) Successful start of SNMP Agent.</span></span>
- <span data-ttu-id="25b31-603">**NX_SNMP_ERROR** (0x100) SNMP エージェントの起動エラー。</span><span class="sxs-lookup"><span data-stu-id="25b31-603">**NX_SNMP_ERROR** (0x100) SNMP Agent start error.</span></span>
- <span data-ttu-id="25b31-604">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-604">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-605">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-605">Allowed From</span></span>

<span data-ttu-id="25b31-606">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-606">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-607">例</span><span class="sxs-lookup"><span data-stu-id="25b31-607">Example</span></span>

```c
/* Start the previously created SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_start(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been started.  */
```
## <a name="nx_snmp_agent_stop"></a><span data-ttu-id="25b31-608">nx_snmp_agent_stop</span><span class="sxs-lookup"><span data-stu-id="25b31-608">nx_snmp_agent_stop</span></span>
<span data-ttu-id="25b31-609">SNMP エージェントを停止します</span><span class="sxs-lookup"><span data-stu-id="25b31-609">Stop SNMP agent</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-610">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-610">Prototype</span></span>

```c
UINT nx_snmp_agent_stop(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="25b31-611">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-611">Description</span></span>

<span data-ttu-id="25b31-612">このサービスでは、SNMP エージェントのスレッドのタスクを停止し、UDP ソケットを SNMP ポートからバインド解除します。</span><span class="sxs-lookup"><span data-stu-id="25b31-612">This service stops the SNMP Agent thread task and unbinds the UDP socket to the SNMP port.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-613">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-613">Input Parameters</span></span>

- <span data-ttu-id="25b31-614">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-614">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-615">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-615">Return Values</span></span>

- <span data-ttu-id="25b31-616">**NX_SUCCESS** (0x00) SNMP エージェントの停止に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-616">**NX_SUCCESS** (0x00) Successful stop of SNMP Agent.</span></span>
- <span data-ttu-id="25b31-617">**NX_PTR_ERROR** (0x07) SNMP エージェントへのポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-617">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-618">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-618">Allowed From</span></span>

<span data-ttu-id="25b31-619">Threads</span><span class="sxs-lookup"><span data-stu-id="25b31-619">Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-620">例</span><span class="sxs-lookup"><span data-stu-id="25b31-620">Example</span></span>

```c
/* Stop the previously created and started SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_stop(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been stopped.  */
```
## <a name="nx_snmp_agent_trap_send"></a><span data-ttu-id="25b31-621">nx_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="25b31-621">nx_snmp_agent_trap_send</span></span>
<span data-ttu-id="25b31-622">SNMPv1 トラップを送信します *(IPv4 のみ)*</span><span class="sxs-lookup"><span data-stu-id="25b31-622">Send SNMPv1 trap *(IPv4 only)*</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-623">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-623">Prototype</span></span>

```c
UINT nx_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
                             ULONG ip_address, UCHAR *enterprise, 
                             UINT trap_type, UINT trap_code, 
                             ULONG elapsed_time, 
                             NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a><span data-ttu-id="25b31-624">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-624">Description</span></span>

<span data-ttu-id="25b31-625">このサービスでは、指定した IPv4 アドレスの SNMP マネージャーに SNMP トラップを送信します。</span><span class="sxs-lookup"><span data-stu-id="25b31-625">This service sends an SNMP trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="25b31-626">NetX Duo で SNMP トラップを送信する際は *nxd_snmp_agent_trap_send* サービスを使用することを推奨します。</span><span class="sxs-lookup"><span data-stu-id="25b31-626">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trap_send* service.</span></span> <span data-ttu-id="25b31-627">*nx_snmp_agent_trap_send* が NetX Duo に含まれているのは、既存の NetX SNMP エージェント アプリケーションをサポートするためです。</span><span class="sxs-lookup"><span data-stu-id="25b31-627">*nx_snmp_agent_trap_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-628">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-628">Input Parameters</span></span>

- <span data-ttu-id="25b31-629">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-629">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-630">**ip_address** SNMP マネージャーの IPv4 アドレス。</span><span class="sxs-lookup"><span data-stu-id="25b31-630">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="25b31-631">**enterprise** エンタープライズ オブジェクト ID の文字列 (sysObectID)。</span><span class="sxs-lookup"><span data-stu-id="25b31-631">**enterprise** Enterprise object ID string (sysObectID).</span></span>
- <span data-ttu-id="25b31-632">**trap_type** 要求されたトラップの種類。次の種類があります:</span><span class="sxs-lookup"><span data-stu-id="25b31-632">**trap_type** Type of trap requested, as follows:</span></span>  
   - <span data-ttu-id="25b31-633">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="25b31-633">NX_SNMP_TRAP_COLDSTART (0)</span></span>  
   - <span data-ttu-id="25b31-634">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="25b31-634">NX_SNMP_TRAP_WARMSTART (1)</span></span>  
   - <span data-ttu-id="25b31-635">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="25b31-635">NX_SNMP_TRAP_LINKDOWN (2)</span></span>  
   - <span data-ttu-id="25b31-636">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="25b31-636">NX_SNMP_TRAP_LINKUP (3)</span></span>  
   - <span data-ttu-id="25b31-637">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="25b31-637">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>  
   - <span data-ttu-id="25b31-638">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="25b31-638">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>  

- <span data-ttu-id="25b31-639">**trap_code** 特定のトラップコード。</span><span class="sxs-lookup"><span data-stu-id="25b31-639">**trap_code** Specific trap code.</span></span>
- <span data-ttu-id="25b31-640">**elapsed_time** システムの稼働時間 (sysUpTime)。</span><span class="sxs-lookup"><span data-stu-id="25b31-640">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="25b31-641">**object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。</span><span class="sxs-lookup"><span data-stu-id="25b31-641">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="25b31-642">リストは NX_NULL で終わります。</span><span class="sxs-lookup"><span data-stu-id="25b31-642">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-643">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-643">Return Values</span></span>

- <span data-ttu-id="25b31-644">**NX_SUCCESS** (0x00) SNMP トラップの送信に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-644">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="25b31-645">**NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。</span><span class="sxs-lookup"><span data-stu-id="25b31-645">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="25b31-646">**NX_NOT_ENABLED** (0x14) SNMPv1 が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="25b31-646">**NX_NOT_ENABLED** (0x14) SNMPv1 not enabled.</span></span>
- <span data-ttu-id="25b31-647">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-647">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-648">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-648">Allowed From</span></span>

<span data-ttu-id="25b31-649">Threads</span><span class="sxs-lookup"><span data-stu-id="25b31-649">Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-650">例</span><span class="sxs-lookup"><span data-stu-id="25b31-650">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nx_snmp_agent_trap_send(&my_agent,dest_ip_address,
                                   "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, 
                                  tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trap_send"></a><span data-ttu-id="25b31-651">nxd_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="25b31-651">nxd_snmp_agent_trap_send</span></span>
<span data-ttu-id="25b31-652">SNMPv1 トラップを送信します *(IPv4 と IPv6)*</span><span class="sxs-lookup"><span data-stu-id="25b31-652">Send SNMPv1 trap *(IPv4 and IPv6)*</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-653">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-653">Prototype</span></span>

```c
UINT nxd_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *enterprise, UINT trap_type, 
            UINT trap_code, ULONG elapsed_time, 
            NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="25b31-654">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-654">Description</span></span>

<span data-ttu-id="25b31-655">このサービスでは、指定した IP アドレスの SNMP マネージャーに SNMP トラップを送信します。</span><span class="sxs-lookup"><span data-stu-id="25b31-655">This service sends an SNMP trap to the SNMP Manager at the specified IP address.</span></span> <span data-ttu-id="25b31-656">NetX で SNMP トラップを送信するためのこれに相当するサービスは *nxd_snmp_agent_trap_send* です。</span><span class="sxs-lookup"><span data-stu-id="25b31-656">The equivalent method for sending an SNMP trap in NetX is the *nxd_snmp_agent_trap_send* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-657">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-657">Input Parameters</span></span>

- <span data-ttu-id="25b31-658">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-658">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-659">**ip_address** SNMP マネージャーの IPv4 または IPv6 アドレス。</span><span class="sxs-lookup"><span data-stu-id="25b31-659">**ip_address** IPv4 or IPv6 address of the SNMP Manager.</span></span>
- <span data-ttu-id="25b31-660">**enterprise** エンタープライズ オブジェクト ID の文字列 (sysObectID)。</span><span class="sxs-lookup"><span data-stu-id="25b31-660">**enterprise** Enterprise object ID string (sysObectID).</span></span>
- <span data-ttu-id="25b31-661">**trap_type** 要求されたトラップの種類。次の種類があります:</span><span class="sxs-lookup"><span data-stu-id="25b31-661">**trap_type** Type of trap requested, as follows:</span></span>  
   - <span data-ttu-id="25b31-662">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="25b31-662">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="25b31-663">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="25b31-663">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="25b31-664">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="25b31-664">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="25b31-665">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="25b31-665">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="25b31-666">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="25b31-666">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="25b31-667">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="25b31-667">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

- <span data-ttu-id="25b31-668">**trap_code** 特定のトラップコード。</span><span class="sxs-lookup"><span data-stu-id="25b31-668">**trap_code** Specific trap code.</span></span>
- <span data-ttu-id="25b31-669">**elapsed_time** システムの稼働時間 (sysUpTime)。</span><span class="sxs-lookup"><span data-stu-id="25b31-669">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="25b31-670">**object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。</span><span class="sxs-lookup"><span data-stu-id="25b31-670">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="25b31-671">リストは NX_NULL で終わります。</span><span class="sxs-lookup"><span data-stu-id="25b31-671">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-672">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-672">Return Values</span></span>

- <span data-ttu-id="25b31-673">**NX_SUCCESS** (0x00) SNMP トラップの送信に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-673">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="25b31-674">**NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。</span><span class="sxs-lookup"><span data-stu-id="25b31-674">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="25b31-675">**NX_NOT_ENABLED** (0x14) SNMPv1 が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="25b31-675">**NX_NOT_ENABLED** (0x14) SNMPv1 not enabled.</span></span>
- <span data-ttu-id="25b31-676">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-676">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-677">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-677">Allowed From</span></span>

<span data-ttu-id="25b31-678">Threads</span><span class="sxs-lookup"><span data-stu-id="25b31-678">Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-679">例</span><span class="sxs-lookup"><span data-stu-id="25b31-679">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nxd_snmp_agent_trap_send(&my_agent,&dest_ip_address,
                 "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, tx_time_get(), 
               trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_send"></a><span data-ttu-id="25b31-680">nx_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="25b31-680">nx_snmp_agent_trapv2_send</span></span>
<span data-ttu-id="25b31-681">SNMPv2 トラップを送信します (IPv4 のみ)</span><span class="sxs-lookup"><span data-stu-id="25b31-681">Send SNMPv2 trap (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-682">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-682">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
            NXD_ADDRESS *ip_address, UCHAR *community, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="25b31-683">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-683">Description</span></span>

<span data-ttu-id="25b31-684">このサービスでは、指定した IPv4 アドレスの SNMP マネージャーに SNMPv2 トラップを送信します。</span><span class="sxs-lookup"><span data-stu-id="25b31-684">This service sends an SNMPv2 trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="25b31-685">NetX Duo で SNMP トラップを送信する際は *nxd_snmp_agent_trapv2_send* サービスを使用することを推奨します。</span><span class="sxs-lookup"><span data-stu-id="25b31-685">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trapv2_send* service.</span></span> <span data-ttu-id="25b31-686">*nx_snmp_agent_trapv2_send* が NetX Duo に含まれているのは、既存の NetX SNMP エージェント アプリケーションをサポートするためです。</span><span class="sxs-lookup"><span data-stu-id="25b31-686">*nx_snmp_agent_trapv2_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-687">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-687">Input Parameters</span></span>

- <span data-ttu-id="25b31-688">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-688">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-689">**ip_address** SNMP マネージャーの IPv4 アドレス。</span><span class="sxs-lookup"><span data-stu-id="25b31-689">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="25b31-690">**community** コミュニティ名 (ユーザー名)。</span><span class="sxs-lookup"><span data-stu-id="25b31-690">**community** Community name (username).</span></span>
- <span data-ttu-id="25b31-691">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="25b31-691">**trap_type**</span></span>  
   <span data-ttu-id="25b31-692">要求されたトラップの種類。</span><span class="sxs-lookup"><span data-stu-id="25b31-692">Type of trap requested.</span></span> <span data-ttu-id="25b31-693">標準のイベントは次のとおりです:</span><span class="sxs-lookup"><span data-stu-id="25b31-693">The standard events are:</span></span>  
   - <span data-ttu-id="25b31-694">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="25b31-694">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="25b31-695">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="25b31-695">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="25b31-696">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="25b31-696">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="25b31-697">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="25b31-697">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="25b31-698">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="25b31-698">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="25b31-699">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="25b31-699">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="25b31-700">独自データを使用する場合:</span><span class="sxs-lookup"><span data-stu-id="25b31-700">For proprietary data:</span></span>  
   - <span data-ttu-id="25b31-701">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF。*nxd_snmp.h* で指定されます)</span><span class="sxs-lookup"><span data-stu-id="25b31-701">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>
   
- <span data-ttu-id="25b31-702">**elapsed_time** システムの稼働時間 (sysUpTime)。</span><span class="sxs-lookup"><span data-stu-id="25b31-702">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="25b31-703">**object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。</span><span class="sxs-lookup"><span data-stu-id="25b31-703">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="25b31-704">リストは NX_NULL で終わります。</span><span class="sxs-lookup"><span data-stu-id="25b31-704">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-705">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-705">Return Values</span></span>

- <span data-ttu-id="25b31-706">**NX_SUCCESS** (0x00) SNMP トラップの送信に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-706">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="25b31-707">**NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。</span><span class="sxs-lookup"><span data-stu-id="25b31-707">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="25b31-708">**NX_NOT_ENABLED** (0x14) SNMPv2 が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="25b31-708">**NX_NOT_ENABLED** (0x14) SNMPv2 not enabled.</span></span>
- <span data-ttu-id="25b31-709">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-709">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-710">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-710">Allowed From</span></span>

<span data-ttu-id="25b31-711">Threads</span><span class="sxs-lookup"><span data-stu-id="25b31-711">Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-712">例</span><span class="sxs-lookup"><span data-stu-id="25b31-712">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG  dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_send(&my_agent,dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_oid_send"></a><span data-ttu-id="25b31-713">nx_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="25b31-713">nx_snmp_agent_trapv2_oid_send</span></span>
<span data-ttu-id="25b31-714">OID を直接指定して SNMPv2 トラップを送信します</span><span class="sxs-lookup"><span data-stu-id="25b31-714">Send SNMPv2 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-715">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-715">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *community,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="25b31-716">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-716">Description</span></span>

<span data-ttu-id="25b31-717">このサービスでは、指定した IP アドレス (IPv4 のみ) の SNMP マネージャーに SNMPv2 トラップを送信し、呼び出し元で OID を直接指定できます。</span><span class="sxs-lookup"><span data-stu-id="25b31-717">This service sends an SNMPv2 trap to the SNMP Manager at the specified IP address (IPv4 only) and allows the caller to specify the OID directly.</span></span> <span data-ttu-id="25b31-718">NetX Duo で OID を指定して SNMP トラップを送信する際は、*nxd_snmp_agent_trapv2_oid_send* サービスを使用することを推奨します。</span><span class="sxs-lookup"><span data-stu-id="25b31-718">The preferred method for sending an SNMP trap with specified OID in NetX Duo is to use the *nxd_snmp_agent_trapv2_oid_send* service.</span></span> <span data-ttu-id="25b31-719">*nx_snmp_agent_trapv2_oid_ send* が NetX Duo に含まれているのは、既存の NetX SNMP エージェント アプリケーションをサポートするためです。</span><span class="sxs-lookup"><span data-stu-id="25b31-719">*nx_snmp_agent_trapv2_oid_ send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-720">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-720">Input Parameters</span></span>

- <span data-ttu-id="25b31-721">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-721">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-722">**ip_address** SNMP マネージャーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="25b31-722">**ip_address** IP address of SNMP Manager.</span></span>
- <span data-ttu-id="25b31-723">**community** コミュニティ名 (ユーザー名)。</span><span class="sxs-lookup"><span data-stu-id="25b31-723">**community** Community name (username).</span></span>
- <span data-ttu-id="25b31-724">**oid** OID を保持するバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-724">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="25b31-725">**elapsed_time** システムの稼働時間 (sysUpTime)。</span><span class="sxs-lookup"><span data-stu-id="25b31-725">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="25b31-726">**object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。</span><span class="sxs-lookup"><span data-stu-id="25b31-726">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="25b31-727">リストは NX_NULL で終わります。</span><span class="sxs-lookup"><span data-stu-id="25b31-727">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-728">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-728">Return Values</span></span>

- <span data-ttu-id="25b31-729">**NX_SUCCESS** (0x00) SNMP トラップの送信に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-729">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="25b31-730">**NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。</span><span class="sxs-lookup"><span data-stu-id="25b31-730">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="25b31-731">**NX_PTR_ERROR** (0x16) SNMP エージェントまたはパラメーターへのポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-731">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="25b31-732">**NX_IP_ADDRESS_ERROR** (0x21) 宛先の IP アドレスが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-732">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="25b31-733">**NX_OPTION_ERROR** (0x0a) 無効なパラメーター。</span><span class="sxs-lookup"><span data-stu-id="25b31-733">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-734">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-734">Allowed From</span></span>

<span data-ttu-id="25b31-735">Threads</span><span class="sxs-lookup"><span data-stu-id="25b31-735">Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-736">例</span><span class="sxs-lookup"><span data-stu-id="25b31-736">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_send"></a><span data-ttu-id="25b31-737">nxd_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="25b31-737">nxd_snmp_agent_trapv2_send</span></span>
<span data-ttu-id="25b31-738">SNMPv2 トラップを送信します (IPv4 と IPv6)</span><span class="sxs-lookup"><span data-stu-id="25b31-738">Send SNMPv2 trap (IPv4 and IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-739">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-739">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *community, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="25b31-740">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-740">Description</span></span>

<span data-ttu-id="25b31-741">このサービスでは、指定した IP アドレスの SNMP マネージャーに SNMP V2 トラップを送信します。</span><span class="sxs-lookup"><span data-stu-id="25b31-741">This service sends an SNMP V2 trap to the SNMP Manager at the specified IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-742">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-742">Input Parameters</span></span>

- <span data-ttu-id="25b31-743">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-743">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-744">**ip_address** SNMP マネージャーの IP アドレス (IPv4 または IPv6)</span><span class="sxs-lookup"><span data-stu-id="25b31-744">**ip_address** IP (IPv4 or IPv6) address of the SNMP Manager.</span></span>
- <span data-ttu-id="25b31-745">**community** コミュニティ名 (ユーザー名)。</span><span class="sxs-lookup"><span data-stu-id="25b31-745">**community** Community name (username).</span></span>
- <span data-ttu-id="25b31-746">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="25b31-746">**trap_type**</span></span>  
   <span data-ttu-id="25b31-747">要求されたトラップの種類。</span><span class="sxs-lookup"><span data-stu-id="25b31-747">Type of trap requested.</span></span> <span data-ttu-id="25b31-748">標準のイベントは次のとおりです:</span><span class="sxs-lookup"><span data-stu-id="25b31-748">The standard events are:</span></span>  
   - <span data-ttu-id="25b31-749">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="25b31-749">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="25b31-750">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="25b31-750">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="25b31-751">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="25b31-751">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="25b31-752">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="25b31-752">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="25b31-753">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="25b31-753">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="25b31-754">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="25b31-754">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="25b31-755">独自データを使用する場合:</span><span class="sxs-lookup"><span data-stu-id="25b31-755">For proprietary data:</span></span>

   - <span data-ttu-id="25b31-756">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF。*nxd_snmp.h* で指定されます)</span><span class="sxs-lookup"><span data-stu-id="25b31-756">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="25b31-757">**elapsed_time** システムの稼働時間 (sysUpTime)。</span><span class="sxs-lookup"><span data-stu-id="25b31-757">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="25b31-758">**object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。</span><span class="sxs-lookup"><span data-stu-id="25b31-758">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="25b31-759">リストは NX_NULL で終わります。</span><span class="sxs-lookup"><span data-stu-id="25b31-759">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-760">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-760">Return Values</span></span>

- <span data-ttu-id="25b31-761">**NX_SUCCESS** (0x00) SNMP トラップの送信に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-761">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="25b31-762">**NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。</span><span class="sxs-lookup"><span data-stu-id="25b31-762">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="25b31-763">**NX_NOT_ENABLED** (0x14) SNMPv2 が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="25b31-763">**NX_NOT_ENABLED** (0x14) SNMPv2 not enabled.</span></span>
- <span data-ttu-id="25b31-764">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) サポートされていない IP バージョン</span><span class="sxs-lookup"><span data-stu-id="25b31-764">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Unsupported IP version</span></span>
- <span data-ttu-id="25b31-765">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-765">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-766">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-766">Allowed From</span></span>

<span data-ttu-id="25b31-767">Threads</span><span class="sxs-lookup"><span data-stu-id="25b31-767">Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-768">例</span><span class="sxs-lookup"><span data-stu-id="25b31-768">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send a standard event trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_send(&my_agent,&dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_oid_send"></a><span data-ttu-id="25b31-769">nxd_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="25b31-769">nxd_snmp_agent_trapv2_oid_send</span></span>
<span data-ttu-id="25b31-770">OID を直接指定して SNMPv2 トラップを送信します</span><span class="sxs-lookup"><span data-stu-id="25b31-770">Send SNMPv2 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-771">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-771">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *community,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                    *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="25b31-772">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-772">Description</span></span>

<span data-ttu-id="25b31-773">このサービスでは、指定された IP アドレス (IPv4 または IPv6) の SNMP マネージャーに SNMP v2 トラップを送信し、呼び出し元で OID を直接指定できます。</span><span class="sxs-lookup"><span data-stu-id="25b31-773">This service sends an SNMP v2 trap to the SNMP Manager at the specified IP address (IPv4/IPv6) and allows the caller to specify the OID directly.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-774">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-774">Input Parameters</span></span>

- <span data-ttu-id="25b31-775">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-775">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-776">**ip_address** SNMP マネージャーの IP アドレス (IPv4 または IPv6)。</span><span class="sxs-lookup"><span data-stu-id="25b31-776">**ip_address** IP address of SNMP Manager (IPv4/IPv6).</span></span>
- <span data-ttu-id="25b31-777">**community** コミュニティ名 (ユーザー名)。</span><span class="sxs-lookup"><span data-stu-id="25b31-777">**community** Community name (username).</span></span>
- <span data-ttu-id="25b31-778">**oid** OID を保持するバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-778">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="25b31-779">**elapsed_time** システムの稼働時間 (sysUpTime)。</span><span class="sxs-lookup"><span data-stu-id="25b31-779">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="25b31-780">**object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。</span><span class="sxs-lookup"><span data-stu-id="25b31-780">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="25b31-781">リストは NX_NULL で終わります。</span><span class="sxs-lookup"><span data-stu-id="25b31-781">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-782">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-782">Return Values</span></span>

- <span data-ttu-id="25b31-783">**NX_SUCCESS** (0x00) SNMP トラップの送信に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-783">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="25b31-784">**NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。</span><span class="sxs-lookup"><span data-stu-id="25b31-784">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="25b31-785">**NX_PTR_ERROR** (0x16) SNMP エージェントまたはパラメーターへのポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-785">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="25b31-786">**NX_IP_ADDRESS_ERROR** (0x21) 宛先の IP アドレスが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-786">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="25b31-787">**NX_OPTION_ERROR** (0x0a) 無効なパラメーター。</span><span class="sxs-lookup"><span data-stu-id="25b31-787">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-788">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-788">Allowed From</span></span>

<span data-ttu-id="25b31-789">Threads</span><span class="sxs-lookup"><span data-stu-id="25b31-789">Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-790">例</span><span class="sxs-lookup"><span data-stu-id="25b31-790">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS         address;


/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

address.nxd_ip_version = NX_IP_VERSION_V4;
address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61)

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_oid_send(&my_agent, &address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_trapv3_send"></a><span data-ttu-id="25b31-791">nx_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="25b31-791">nx_snmp_agent_trapv3_send</span></span>
<span data-ttu-id="25b31-792">SNMPv3 トラップを送信します (IPv4 のみ)</span><span class="sxs-lookup"><span data-stu-id="25b31-792">Send SNMPv3 trap (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-793">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-793">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *username, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a><span data-ttu-id="25b31-794">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-794">Description</span></span>

<span data-ttu-id="25b31-795">このサービスでは、指定した IPv4 アドレスの SNMP マネージャーに SNMPv3 トラップを送信します。</span><span class="sxs-lookup"><span data-stu-id="25b31-795">This service sends an SNMPv3 trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="25b31-796">NetX Duo で SNMP トラップを送信する際は *nxd_snmp_agent_trapv3_send* サービスを使用することを推奨します。</span><span class="sxs-lookup"><span data-stu-id="25b31-796">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trapv3_send* service.</span></span> <span data-ttu-id="25b31-797">*nx_snmp_agent_trapv3_send* が NetX Duo に含まれているのは、既存の NetX SNMP エージェント アプリケーションをサポートするためです。</span><span class="sxs-lookup"><span data-stu-id="25b31-797">*nx_snmp_agent_trapv3_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-798">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-798">Input Parameters</span></span>

- <span data-ttu-id="25b31-799">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-799">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-800">**ip_address** SNMP マネージャーの IPv4 アドレス。</span><span class="sxs-lookup"><span data-stu-id="25b31-800">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="25b31-801">**username** コミュニティ名 (ユーザー名)。</span><span class="sxs-lookup"><span data-stu-id="25b31-801">**username** Community name (username).</span></span>
- <span data-ttu-id="25b31-802">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="25b31-802">**trap_type**</span></span>  
   <span data-ttu-id="25b31-803">要求されたトラップの種類。</span><span class="sxs-lookup"><span data-stu-id="25b31-803">Type of trap requested.</span></span> <span data-ttu-id="25b31-804">標準のイベントは次のとおりです:</span><span class="sxs-lookup"><span data-stu-id="25b31-804">The standard events are:</span></span>  
   - <span data-ttu-id="25b31-805">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="25b31-805">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="25b31-806">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="25b31-806">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="25b31-807">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="25b31-807">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="25b31-808">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="25b31-808">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="25b31-809">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="25b31-809">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="25b31-810">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="25b31-810">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="25b31-811">独自データを使用する場合:</span><span class="sxs-lookup"><span data-stu-id="25b31-811">For proprietary data:</span></span>
   - <span data-ttu-id="25b31-812">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) *nxd_snmp.h* で指定されます)</span><span class="sxs-lookup"><span data-stu-id="25b31-812">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="25b31-813">**elapsed_time** システムの稼働時間 (sysUpTime)。</span><span class="sxs-lookup"><span data-stu-id="25b31-813">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="25b31-814">**object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。</span><span class="sxs-lookup"><span data-stu-id="25b31-814">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="25b31-815">リストは NX_NULL で終わります。</span><span class="sxs-lookup"><span data-stu-id="25b31-815">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-816">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-816">Return Values</span></span>

- <span data-ttu-id="25b31-817">**NX_SUCCESS** (0x00) SNMP トラップの送信に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-817">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="25b31-818">**NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。</span><span class="sxs-lookup"><span data-stu-id="25b31-818">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="25b31-819">**NX_NOT_ENABLED** (0x14) SNMPv3 が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="25b31-819">**NX_NOT_ENABLED** (0x14) SNMPv3 not enabled.</span></span>
- <span data-ttu-id="25b31-820">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-820">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-821">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-821">Allowed From</span></span>

<span data-ttu-id="25b31-822">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-822">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-823">例</span><span class="sxs-lookup"><span data-stu-id="25b31-823">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_send(&my_agent, dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv3_oid_send"></a><span data-ttu-id="25b31-824">nx_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="25b31-824">nx_snmp_agent_trapv3_oid_send</span></span>
<span data-ttu-id="25b31-825">OID を直接指定して SNMPv3 トラップを送信します</span><span class="sxs-lookup"><span data-stu-id="25b31-825">Send SNMPv3 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-826">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-826">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *username,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                   *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="25b31-827">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-827">Description</span></span>

<span data-ttu-id="25b31-828">このサービスでは、指定した IP アドレス (IPv4 のみ) の SNMP マネージャーに SNMPv3 トラップを送信し、呼び出し元で OID を直接指定できます。</span><span class="sxs-lookup"><span data-stu-id="25b31-828">This service sends an SNMPv3 trap to the SNMP Manager at the specified IP address (IPv4 only) and allows the caller to specify the OID directly.</span></span> <span data-ttu-id="25b31-829">NetX Duo で OID を指定して SNMP トラップを送信する際は、*nxd_snmp_agent_trapv3_oid_send* サービスを使用することを推奨します。</span><span class="sxs-lookup"><span data-stu-id="25b31-829">The preferred method for sending an SNMP trap with specified OID in NetX Duo is to use the *nxd_snmp_agent_trapv3_oid_send* service.</span></span> <span data-ttu-id="25b31-830">*nx_snmp_agent_trapv3_oid_ send* が NetX Duo に含まれているのは、既存の NetX SNMP エージェント アプリケーションをサポートするためです。</span><span class="sxs-lookup"><span data-stu-id="25b31-830">*nx_snmp_agent_trapv3_oid_ send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-831">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-831">Input Parameters</span></span>

- <span data-ttu-id="25b31-832">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-832">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-833">**ip_address** SNMP マネージャーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="25b31-833">**ip_address** IP address of SNMP Manager.</span></span>
- <span data-ttu-id="25b31-834">**username** コミュニティ名 (ユーザー名)。</span><span class="sxs-lookup"><span data-stu-id="25b31-834">**username** Community name (username).</span></span>
- <span data-ttu-id="25b31-835">**oid** OID を保持するバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-835">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="25b31-836">**elapsed_time** システムの稼働時間 (sysUpTime)。</span><span class="sxs-lookup"><span data-stu-id="25b31-836">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="25b31-837">**object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。</span><span class="sxs-lookup"><span data-stu-id="25b31-837">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="25b31-838">リストは NX_NULL で終わります。</span><span class="sxs-lookup"><span data-stu-id="25b31-838">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-839">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-839">Return Values</span></span>

- <span data-ttu-id="25b31-840">**NX_SUCCESS** (0x00) SNMP トラップの送信に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-840">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="25b31-841">**NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。</span><span class="sxs-lookup"><span data-stu-id="25b31-841">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="25b31-842">**NX_PTR_ERROR** (0x16) SNMP エージェントまたはパラメーターへのポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-842">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="25b31-843">**NX_IP_ADDRESS_ERROR** (0x21) 宛先の IP アドレスが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-843">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="25b31-844">**NX_OPTION_ERROR** (0x0a) 無効なパラメーター。</span><span class="sxs-lookup"><span data-stu-id="25b31-844">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-845">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-845">Allowed From</span></span>

<span data-ttu-id="25b31-846">Threads</span><span class="sxs-lookup"><span data-stu-id="25b31-846">Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-847">例</span><span class="sxs-lookup"><span data-stu-id="25b31-847">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trapv3_send"></a><span data-ttu-id="25b31-848">nxd_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="25b31-848">nxd_snmp_agent_trapv3_send</span></span>
<span data-ttu-id="25b31-849">SNMPv3 トラップを送信します (IPv4 と IPv6)</span><span class="sxs-lookup"><span data-stu-id="25b31-849">Send SNMPv3 trap (IPv4 and IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-850">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-850">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *username, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="25b31-851">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-851">Description</span></span>

<span data-ttu-id="25b31-852">このサービスでは、指定した IP アドレスの SNMP マネージャーに SNMP トラップを送信します。</span><span class="sxs-lookup"><span data-stu-id="25b31-852">This service sends an SNMP trap to the SNMP Manager at the specified IP address.</span></span> <span data-ttu-id="25b31-853">このトラップは基本的に SNMP v2 トラップと同じですが、SNMP v3 ではトラップ メッセージの形式を PDU に入れる点が異なります。</span><span class="sxs-lookup"><span data-stu-id="25b31-853">This trap is basically the same as the SNMP v2 trap, except the trap message format is contained in the SNMP v3 PDU.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-854">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-854">Input Parameters</span></span>

- <span data-ttu-id="25b31-855">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-855">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-856">**ip_address** SNMP マネージャーの IP アドレス (IPv4 または IPv6)</span><span class="sxs-lookup"><span data-stu-id="25b31-856">**ip_address** IP (IPv4 or IPv6) address of the SNMP Manager.</span></span>
- <span data-ttu-id="25b31-857">**username** コミュニティ名 (ユーザー名)。</span><span class="sxs-lookup"><span data-stu-id="25b31-857">**username** Community name (username).</span></span>
- <span data-ttu-id="25b31-858">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="25b31-858">**trap_type**</span></span>  
   <span data-ttu-id="25b31-859">要求されたトラップの種類。</span><span class="sxs-lookup"><span data-stu-id="25b31-859">Type of trap requested.</span></span> <span data-ttu-id="25b31-860">標準のイベントは次のとおりです:</span><span class="sxs-lookup"><span data-stu-id="25b31-860">The standard events are:</span></span>
   - <span data-ttu-id="25b31-861">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="25b31-861">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="25b31-862">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="25b31-862">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="25b31-863">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="25b31-863">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="25b31-864">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="25b31-864">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="25b31-865">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="25b31-865">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="25b31-866">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="25b31-866">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>  
   <span data-ttu-id="25b31-867">独自データを使用する場合:</span><span class="sxs-lookup"><span data-stu-id="25b31-867">For proprietary data:</span></span>
   - <span data-ttu-id="25b31-868">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (*nxd_snmp.h* で指定されます)</span><span class="sxs-lookup"><span data-stu-id="25b31-868">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="25b31-869">**elapsed_time** システムの稼働時間 (sysUpTime)。</span><span class="sxs-lookup"><span data-stu-id="25b31-869">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="25b31-870">**object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。</span><span class="sxs-lookup"><span data-stu-id="25b31-870">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="25b31-871">リストは NX_NULL で終わります。</span><span class="sxs-lookup"><span data-stu-id="25b31-871">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-872">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-872">Return Values</span></span>

- <span data-ttu-id="25b31-873">**NX_SUCCESS** (0x00) SNMP トラップの送信に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-873">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="25b31-874">**NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。</span><span class="sxs-lookup"><span data-stu-id="25b31-874">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="25b31-875">**NX_NOT_ENABLED** (0x14) SNMPv3 が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="25b31-875">**NX_NOT_ENABLED** (0x14) SNMPv3 not enabled.</span></span>
- <span data-ttu-id="25b31-876">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) サポートされていない IP バージョン</span><span class="sxs-lookup"><span data-stu-id="25b31-876">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Unsupported IP version</span></span>
- <span data-ttu-id="25b31-877">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-877">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-878">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-878">Allowed From</span></span>

<span data-ttu-id="25b31-879">Threads</span><span class="sxs-lookup"><span data-stu-id="25b31-879">Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-880">例</span><span class="sxs-lookup"><span data-stu-id="25b31-880">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_send(&my_agent, &dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv3_oid_send"></a><span data-ttu-id="25b31-881">nxd_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="25b31-881">nxd_snmp_agent_trapv3_oid_send</span></span>
<span data-ttu-id="25b31-882">OID を直接指定して SNMPv3 トラップを送信します</span><span class="sxs-lookup"><span data-stu-id="25b31-882">Send SNMPv3 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-883">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-883">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *username,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="25b31-884">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-884">Description</span></span>

<span data-ttu-id="25b31-885">このサービスでは、指定した IP アドレス (IPv4 または IPv6) の SNMP マネージャーに SNMPv3 トラップを送信し、呼び出し元で OID を直接指定できます。</span><span class="sxs-lookup"><span data-stu-id="25b31-885">This service sends an SNMPv3 trap to the SNMP Manager at the specified IP address (IPv4/IPv6) and allows the caller to specify the OID directly.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-886">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-886">Input Parameters</span></span>

- <span data-ttu-id="25b31-887">**agent_ptr** SNMP エージェント制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-887">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="25b31-888">**ip_address** SNMP マネージャーの IP アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-888">**ip_address** Pointer to IP address of SNMP Manager.</span></span>
- <span data-ttu-id="25b31-889">**username** ユーザー名 (コミュニティ名)。</span><span class="sxs-lookup"><span data-stu-id="25b31-889">**username** Username (community name).</span></span>
- <span data-ttu-id="25b31-890">**oid** OID を保持するバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-890">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="25b31-891">**elapsed_time** システムの稼働時間 (sysUpTime)。</span><span class="sxs-lookup"><span data-stu-id="25b31-891">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="25b31-892">**object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。</span><span class="sxs-lookup"><span data-stu-id="25b31-892">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="25b31-893">リストは NX_NULL で終わります。</span><span class="sxs-lookup"><span data-stu-id="25b31-893">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-894">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-894">Return Values</span></span>

- <span data-ttu-id="25b31-895">**NX_SUCCESS** (0x00) SNMP トラップの送信に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-895">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="25b31-896">**NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。</span><span class="sxs-lookup"><span data-stu-id="25b31-896">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="25b31-897">**NX_PTR_ERROR** (0x16) SNMP エージェントまたはパラメーターへのポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-897">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="25b31-898">**NX_IP_ADDRESS_ERROR** (0x21) 宛先の IP アドレスが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-898">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-899">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-899">Allowed From</span></span>

<span data-ttu-id="25b31-900">Threads</span><span class="sxs-lookup"><span data-stu-id="25b31-900">Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-901">例</span><span class="sxs-lookup"><span data-stu-id="25b31-901">Example</span></span>

```c
NXD_ADDRESS         ip_address;
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

ip_address.nxd_ip_version = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61);

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_oid_send(&my_agent, &ip_address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_v3_context_boots_set"></a><span data-ttu-id="25b31-902">nx_snmp_agent_v3_context_boots_set</span><span class="sxs-lookup"><span data-stu-id="25b31-902">nx_snmp_agent_v3_context_boots_set</span></span>
<span data-ttu-id="25b31-903">再起動の回数を設定します (SNMPv3 が有効になっている場合)</span><span class="sxs-lookup"><span data-stu-id="25b31-903">Set the number of reboots (if SNMPv3 enabled)</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-904">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-904">Prototype</span></span>

```c
UINT nx_snmp_agent_v3_context_boots_set(NX_SNMP_AGENT *agent_ptr, 
                                        UINT boots);
```

### <a name="description"></a><span data-ttu-id="25b31-905">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-905">Description</span></span>

<span data-ttu-id="25b31-906">このサービスでは、SNMP エージェントで記録する再起動の回数を設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-906">This service sets the number of reboots recorded by the SNMP agent.</span></span> <span data-ttu-id="25b31-907">起動回数は SNMPv3 プロトコルでのみ使用されるため、このサービスは、SNMP エージェントで SNMPv3 が有効になっている場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="25b31-907">This service is only available if SNMPv3 is enabled for the SNMP agent because boot count is only used in the SNMPv3 protocol.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-908">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-908">Input Parameters</span></span>

- <span data-ttu-id="25b31-909">**agent_ptr** SNMP エージェント制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="25b31-909">**agent_ptr** Pointer to SNMP Agent control block</span></span>
- <span data-ttu-id="25b31-910">**boots** SNMP エージェントの起動回数として設定する値</span><span class="sxs-lookup"><span data-stu-id="25b31-910">**boots** The value to set SNMP Agent boot count to</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-911">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-911">Return Values</span></span>

- <span data-ttu-id="25b31-912">**NX_SUCCESS** (0x00) 起動回数の設定に成功</span><span class="sxs-lookup"><span data-stu-id="25b31-912">**NX_SUCCESS** (0x00) Successfully set boot count</span></span>
- <span data-ttu-id="25b31-913">**NX_SNMP_ERROR** (0x100) 起動回数設定エラー</span><span class="sxs-lookup"><span data-stu-id="25b31-913">**NX_SNMP_ERROR** (0x100) Error setting boot count</span></span>
- <span data-ttu-id="25b31-914">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-914">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-915">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-915">Allowed From</span></span>

<span data-ttu-id="25b31-916">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-916">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-917">例</span><span class="sxs-lookup"><span data-stu-id="25b31-917">Example</span></span>

```c
UINT my_boots = 4;

if (my_agent.nx_snmp_agent_v3_enabled == NX_TRUE)
{
   status = nx_snmp_agent_v3_context_boots_set(&my_agent, my_boots);
}


/* If status is NX_SUCCESS the SNMP boot count is set.  */
```

## <a name="nx_snmp_object_compare"></a><span data-ttu-id="25b31-918">nx_snmp_object_compare</span><span class="sxs-lookup"><span data-stu-id="25b31-918">nx_snmp_object_compare</span></span>
<span data-ttu-id="25b31-919">2 つのオブジェクトを比較します</span><span class="sxs-lookup"><span data-stu-id="25b31-919">Compare two objects</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-920">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-920">Prototype</span></span>

```c
UINT nx_snmp_object_compare(UCHAR *object, UCHAR *reference_object);
```

### <a name="description"></a><span data-ttu-id="25b31-921">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-921">Description</span></span>

<span data-ttu-id="25b31-922">このサービスでは、指定されたオブジェクト ID と参照オブジェクト ID を比較します。</span><span class="sxs-lookup"><span data-stu-id="25b31-922">This service compares the supplied object ID with the reference object ID.</span></span> <span data-ttu-id="25b31-923">どちらのオブジェクト ID も、SMI の表記形式の ASCII 文字列です。たとえば、どちらのオブジェクトも ASCII 文字列 “1.3.6” で始まる必要があります。</span><span class="sxs-lookup"><span data-stu-id="25b31-923">Both object IDs are in the ASCII SMI notation, e.g., both object must start with the ASCII string “1.3.6”.</span></span>

<span data-ttu-id="25b31-924">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="25b31-924">This service is deprecated.</span></span> <span data-ttu-id="25b31-925">開発者は *nx_snmp_object_compare_extended()* に移行することを推奨します。</span><span class="sxs-lookup"><span data-stu-id="25b31-925">Developers are encouraged to migrate to *nx_snmp_object_compare_extended().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-926">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-926">Input Parameters</span></span>

- <span data-ttu-id="25b31-927">**object** オブジェクト ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-927">**object** Pointer to object ID.</span></span>
- <span data-ttu-id="25b31-928">**reference_object** 参照オブジェクト ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-928">**reference_object** Pointer to the reference object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-929">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-929">Return Values</span></span>

- <span data-ttu-id="25b31-930">**NX_SUCCESS** (0x00) オブジェクトが参照オブジェクトに一致。</span><span class="sxs-lookup"><span data-stu-id="25b31-930">**NX_SUCCESS** (0x00) The object matches the reference object.</span></span>
- <span data-ttu-id="25b31-931">**NX_SNMP_NEXT_ENTRY** (0x101) オブジェクトが参照オブジェクトより小さいです。</span><span class="sxs-lookup"><span data-stu-id="25b31-931">**NX_SNMP_NEXT_ENTRY** (0x101) The object is less than the reference object.</span></span>
- <span data-ttu-id="25b31-932">**NX_SNMP_ERROR** (0x100) オブジェクトが参照オブジェクトより大きいです。</span><span class="sxs-lookup"><span data-stu-id="25b31-932">**NX_SNMP_ERROR** (0x100) The object is greater than the reference object.</span></span>
- <span data-ttu-id="25b31-933">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-933">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-934">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-934">Allowed From</span></span>

<span data-ttu-id="25b31-935">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-935">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-936">例</span><span class="sxs-lookup"><span data-stu-id="25b31-936">Example</span></span>

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare(requested_object, "1.3.6.1.2.1.1.1.0");

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_compare_extended"></a><span data-ttu-id="25b31-937">nx_snmp_object_compare_extended</span><span class="sxs-lookup"><span data-stu-id="25b31-937">nx_snmp_object_compare_extended</span></span>
<span data-ttu-id="25b31-938">2 つのオブジェクトを比較します</span><span class="sxs-lookup"><span data-stu-id="25b31-938">Compare two objects</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-939">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-939">Prototype</span></span>

```c
UINT nx_snmp_object_compare_extended(UCHAR *request_object, 
                                     UINT requested_object_length,
                                     UCHAR *reference_object
                                     UINT reference_object_length);
```
### <a name="description"></a><span data-ttu-id="25b31-940">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-940">Description</span></span>

<span data-ttu-id="25b31-941">このサービスでは、指定されたオブジェクト ID と参照オブジェクトID を比較します。</span><span class="sxs-lookup"><span data-stu-id="25b31-941">This service compares the supplied object ID with the reference object ID.</span></span> <span data-ttu-id="25b31-942">どちらのオブジェクト ID も、SMI の表記形式の ASCII 文字列です。たとえば、どちらのオブジェクトも ASCII 文字列 “1.3.6” で始まる必要があります。</span><span class="sxs-lookup"><span data-stu-id="25b31-942">Both object IDs are in the ASCII SMI notation, e.g., both object must start with the ASCII string “1.3.6”.</span></span>

<span data-ttu-id="25b31-943">これは *nx_snmp_object_compare()* の後継サービスです。</span><span class="sxs-lookup"><span data-stu-id="25b31-943">This service replaces *nx_snmp_object_compare().*</span></span> <span data-ttu-id="25b31-944">このバージョンでは、呼び出し元で長さを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25b31-944">This version requires callers to supply length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-945">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-945">Input Parameters</span></span>

- <span data-ttu-id="25b31-946">**request_object** 要求オブジェクト ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-946">**request_object** Pointer to request object ID.</span></span>
- <span data-ttu-id="25b31-947">**request_object_length** 要求オブジェクトID の長さ。</span><span class="sxs-lookup"><span data-stu-id="25b31-947">**request_object_length** Length of the request object ID.</span></span>
- <span data-ttu-id="25b31-948">**reference_object** 参照オブジェクト ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-948">**reference_object** Pointer to the reference object ID.</span></span>
- <span data-ttu-id="25b31-949">**reference_object_length** 参照オブジェクト ID の長さ。</span><span class="sxs-lookup"><span data-stu-id="25b31-949">**reference_object_length** Length of the reference object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-950">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-950">Return Values</span></span>

- <span data-ttu-id="25b31-951">**NX_SUCCESS** (0x00) オブジェクトが参照オブジェクトに一致。</span><span class="sxs-lookup"><span data-stu-id="25b31-951">**NX_SUCCESS** (0x00) The object matches the reference object.</span></span>
- <span data-ttu-id="25b31-952">**NX_SNMP_NEXT_ENTRY** (0x101) オブジェクトが参照オブジェクトより小さいです。</span><span class="sxs-lookup"><span data-stu-id="25b31-952">**NX_SNMP_NEXT_ENTRY** (0x101) The object is less than the reference object.</span></span>
- <span data-ttu-id="25b31-953">**NX_SNMP_ERROR** (0x100) オブジェクトが参照オブジェクトより大きいです。</span><span class="sxs-lookup"><span data-stu-id="25b31-953">**NX_SNMP_ERROR** (0x100) The object is greater than the reference object.</span></span>
- <span data-ttu-id="25b31-954">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-954">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-955">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-955">Allowed From</span></span>

<span data-ttu-id="25b31-956">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-956">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-957">例</span><span class="sxs-lookup"><span data-stu-id="25b31-957">Example</span></span>

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare_extended(requested_object, 17,
                                          "1.3.6.1.2.1.1.1.0", 17);

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_copy"></a><span data-ttu-id="25b31-958">nx_snmp_object_copy</span><span class="sxs-lookup"><span data-stu-id="25b31-958">nx_snmp_object_copy</span></span>
<span data-ttu-id="25b31-959">オブジェクトをコピーする</span><span class="sxs-lookup"><span data-stu-id="25b31-959">Copy an object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-960">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-960">Prototype</span></span>

```c
UINT  nx_snmp_object_copy(UCHAR *source_object_name, 
                          UCHAR *destination_object_name);
```
### <a name="description"></a><span data-ttu-id="25b31-961">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-961">Description</span></span>

<span data-ttu-id="25b31-962">このサービスでは、SMI の表記形式の ASCII 文字列を使用するソース オブジェクトを、目的のオブジェクトにコピーします。</span><span class="sxs-lookup"><span data-stu-id="25b31-962">This service copies the source object in ASCII SIM notation to the destination object.</span></span>

<span data-ttu-id="25b31-963">このサービスは推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="25b31-963">This service is deprecated.</span></span> <span data-ttu-id="25b31-964">開発者は *nx_snmp_object_copy_extended()* に移行することを推奨します。</span><span class="sxs-lookup"><span data-stu-id="25b31-964">Developers are encouraged to migrate to *nx_snmp_object_copy_extended().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-965">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-965">Input Parameters</span></span>

- <span data-ttu-id="25b31-966">**source_object_name** ソース オブジェクト ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-966">**source_object_name** Pointer to source object ID.</span></span>
- <span data-ttu-id="25b31-967">**destination_object_name** コピー先のオブジェクト ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-967">**destination_object_name** Pointer to destination object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-968">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-968">Return Values</span></span>

- <span data-ttu-id="25b31-969">**size** コピー先の名前にコピーするバイト数。</span><span class="sxs-lookup"><span data-stu-id="25b31-969">**size** Number of bytes copied to destination name.</span></span> <span data-ttu-id="25b31-970">エラーが発生した場合は 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="25b31-970">If error, zero is returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-971">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-971">Allowed From</span></span>

<span data-ttu-id="25b31-972">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-972">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-973">例</span><span class="sxs-lookup"><span data-stu-id="25b31-973">Example</span></span>

```c
/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, my_new_object);

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_copy_extended"></a><span data-ttu-id="25b31-974">nx_snmp_object_copy_extended</span><span class="sxs-lookup"><span data-stu-id="25b31-974">nx_snmp_object_copy_extended</span></span>
<span data-ttu-id="25b31-975">オブジェクトをコピーする</span><span class="sxs-lookup"><span data-stu-id="25b31-975">Copy an object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-976">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-976">Prototype</span></span>

```c
UINT  nx_snmp_object_copy_extended(UCHAR *source_object_name, 
                             UINT source_object_name_length,
                             UCHAR *destination_object_name_buffer,
                             UINT destination_object_name_buffer_size);
```

### <a name="description"></a><span data-ttu-id="25b31-977">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-977">Description</span></span>

<span data-ttu-id="25b31-978">このサービスでは、SMI の表記形式の ASCII 文字列を使用するソース オブジェクトを、目的のオブジェクトにコピーします。</span><span class="sxs-lookup"><span data-stu-id="25b31-978">This service copies the source object in ASCII SIM notation to the destination object.</span></span>

<span data-ttu-id="25b31-979">これは *nx_snmp_object_copy()* の後継サービスです。</span><span class="sxs-lookup"><span data-stu-id="25b31-979">This service replaces *nx_snmp_object_copy().*</span></span> <span data-ttu-id="25b31-980">このバージョンでは、呼び出し元で長さを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25b31-980">This version requires callers to supply length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-981">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-981">Input Parameters</span></span>

- <span data-ttu-id="25b31-982">**source_object_name** ソース オブジェクト ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-982">**source_object_name** Pointer to source object ID.</span></span>
- <span data-ttu-id="25b31-983">**source_object_name_length** ソース オブジェクト ID の長さ。</span><span class="sxs-lookup"><span data-stu-id="25b31-983">**source_object_name_length** Length of source object ID.</span></span>
- <span data-ttu-id="25b31-984">**destination_object_name_buffer** コピー先のオブジェクトのバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-984">**destination_object_name_buffer** Pointer to destination object buffer.</span></span>
- <span data-ttu-id="25b31-985">**destination_object_name_buffer_size** コピー先のオブジェクトのバッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="25b31-985">**destination_object_name_buffer_size** Size of destination object buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-986">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-986">Return Values</span></span>

- <span data-ttu-id="25b31-987">**size** コピー先の名前にコピーするバイト数。</span><span class="sxs-lookup"><span data-stu-id="25b31-987">**size** Number of bytes copied to destination name.</span></span> <span data-ttu-id="25b31-988">エラーが発生した場合は 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="25b31-988">If error, zero is returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-989">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-989">Allowed From</span></span>

<span data-ttu-id="25b31-990">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-990">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-991">例</span><span class="sxs-lookup"><span data-stu-id="25b31-991">Example</span></span>

```c
UCHAR   my_object = "1.3.6.1.2.1.1.1.0";
UCHAR   my_new_object[32];


/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, 17, my_new_object, sizeof(my_new_object));

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_counter_get"></a><span data-ttu-id="25b31-992">nx_snmp_object_counter_get</span><span class="sxs-lookup"><span data-stu-id="25b31-992">nx_snmp_object_counter_get</span></span>
<span data-ttu-id="25b31-993">カウンター オブジェクトを取得します</span><span class="sxs-lookup"><span data-stu-id="25b31-993">Get counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-994">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-994">Prototype</span></span>

```c
UINT  nx_snmp_object_counter_get(VOID *source_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a><span data-ttu-id="25b31-995">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-995">Description</span></span>

<span data-ttu-id="25b31-996">このサービスでは、ソースへのポインターで指定したアドレスのカウンター オブジェクトを取得し、それを NetX オブジェクト データ構造体に配置します。</span><span class="sxs-lookup"><span data-stu-id="25b31-996">This service retrieves the counter object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="25b31-997">このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-997">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-998">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-998">Input Parameters</span></span>

- <span data-ttu-id="25b31-999">**source_ptr** カウンターのソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-999">**source_ptr** Pointer to counter source.</span></span>
- <span data-ttu-id="25b31-1000">**object_data** 配置先のオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1000">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1001">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1001">Return Values</span></span>

- <span data-ttu-id="25b31-1002">**NX_SUCCESS** (0x00) カウンター オブジェクトの取得に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1002">**NX_SUCCESS** (0x00) The counter object has be successfully retrieved.</span></span>
- <span data-ttu-id="25b31-1003">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-1003">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1004">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1004">Allowed From</span></span>

<span data-ttu-id="25b31-1005">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1005">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1006">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1006">Example</span></span>

```c
/* Get the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object.  */
status =  nx_snmp_object_counter_get(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter_set"></a><span data-ttu-id="25b31-1007">nx_snmp_object_counter_set</span><span class="sxs-lookup"><span data-stu-id="25b31-1007">nx_snmp_object_counter_set</span></span>
<span data-ttu-id="25b31-1008">カウンター オブジェクトを設定します</span><span class="sxs-lookup"><span data-stu-id="25b31-1008">Set counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1009">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1009">Prototype</span></span>

```c
UINT  nx_snmp_object_counter_set(VOID *destination_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1010">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1010">Description</span></span>

<span data-ttu-id="25b31-1011">このサービスでは、設定先へのポインターで指定したアドレスのカウンターを、NetX オブジェクト データ構造体にあるカウンターの値に設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1011">This service sets the counter at the address specified by the destination pointer with the counter value in the NetX object data structure.</span></span> <span data-ttu-id="25b31-1012">このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1012">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1013">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1013">Input Parameters</span></span>

- <span data-ttu-id="25b31-1014">**destination_ptr** カウンターの設定先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1014">**destination_ptr** Pointer to counter destination.</span></span>
- <span data-ttu-id="25b31-1015">**object_data** カウンターのソースのオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1015">**object_data** Pointer to counter source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1016">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1016">Return Values</span></span>

- <span data-ttu-id="25b31-1017">**NX_SUCCESS** (0x00) カウンター オブジェクトの設定に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1017">**NX_SUCCESS** (0x00) The counter object has be successfully set.</span></span>
- <span data-ttu-id="25b31-1018">**NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-1018">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="25b31-1019">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-1019">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1020">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1020">Allowed From</span></span>

<span data-ttu-id="25b31-1021">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1021">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1022">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1022">Example</span></span>

```c
/* Set the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object with
   the counter object value contained in my_object.  */
status =  nx_snmp_object_counter_set(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   set. */
```

## <a name="nx_snmp_object_counter64_get"></a><span data-ttu-id="25b31-1023">nx_snmp_object_counter64_get</span><span class="sxs-lookup"><span data-stu-id="25b31-1023">nx_snmp_object_counter64_get</span></span>
<span data-ttu-id="25b31-1024">64 ビットのカウンター オブジェクトを取得します</span><span class="sxs-lookup"><span data-stu-id="25b31-1024">Get 64-bit counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1025">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1025">Prototype</span></span>

```c
UINT  nx_snmp_object_counter64_get(VOID *source_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1026">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1026">Description</span></span>

<span data-ttu-id="25b31-1027">このサービスでは、ソースへのポインターで指定したアドレスにある 64 ビットのカウンター オブジェクトを取得し、NetX オブジェクト データ構造体に配置します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1027">This service retrieves the 64-bit counter object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="25b31-1028">このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1028">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1029">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1029">Input Parameters</span></span>

- <span data-ttu-id="25b31-1030">**source_ptr** カウンターのソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1030">**source_ptr** Pointer to counter source.</span></span>
- <span data-ttu-id="25b31-1031">**object_data** 配置先のオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1031">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1032">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1032">Return Values</span></span>

- <span data-ttu-id="25b31-1033">**NX_SUCCESS** (0x00) カウンター オブジェクトの取得に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1033">**NX_SUCCESS** (0x00) The counter object has be successfully retrieved.</span></span>
- <span data-ttu-id="25b31-1034">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1034">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1035">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1035">Allowed From</span></span>

<span data-ttu-id="25b31-1036">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1036">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1037">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1037">Example</span></span>

```c
/* Get the value of my_64_bit_counter and place it into my_object
   for return.  */
status =  nx_snmp_object_counter64_get(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter64_set"></a><span data-ttu-id="25b31-1038">nx_snmp_object_counter64_set</span><span class="sxs-lookup"><span data-stu-id="25b31-1038">nx_snmp_object_counter64_set</span></span>
<span data-ttu-id="25b31-1039">64 ビット カウンター オブジェクトを設定します</span><span class="sxs-lookup"><span data-stu-id="25b31-1039">Set 64-bit counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1040">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1040">Prototype</span></span>

```c
UINT  nx_snmp_object_counter64_set(VOID *destination_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a><span data-ttu-id="25b31-1041">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1041">Description</span></span>

<span data-ttu-id="25b31-1042">このサービスでは、設定先へのポインターで指定したアドレスの 64 ビット カウンターを、NetX オブジェクト データ構造体にあるカウンターの値に設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1042">This service sets the 64-bit counter at the address specified by the destination pointer with the counter value in the NetX object data structure.</span></span> <span data-ttu-id="25b31-1043">このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1043">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1044">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1044">Input Parameters</span></span>

- <span data-ttu-id="25b31-1045">**destination_ptr** カウンターの設定先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1045">**destination_ptr** Pointer to counter destination.</span></span>
- <span data-ttu-id="25b31-1046">**object_data** カウンターのソースのオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1046">**object_data** Pointer to counter source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1047">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1047">Return Values</span></span>

- <span data-ttu-id="25b31-1048">**NX_SUCCESS** (0x00) カウンター オブジェクトの設定に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1048">**NX_SUCCESS** (0x00) The counter object has be successfully set.</span></span>
- <span data-ttu-id="25b31-1049">**NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-1049">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="25b31-1050">**NX_PTR_ERROR** (0x07) 入力したポインターが無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-1050">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1051">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1051">Allowed From</span></span>

<span data-ttu-id="25b31-1052">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1052">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1053">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1053">Example</span></span>

```c
/* Set the value of my_64_bit_counter with the value in my_object.  */
status =  nx_snmp_object_counter64_set(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   set. */
```

## <a name="nx_snmp_object_end_of_mib"></a><span data-ttu-id="25b31-1054">nx_snmp_object_end_of_mib</span><span class="sxs-lookup"><span data-stu-id="25b31-1054">nx_snmp_object_end_of_mib</span></span>
<span data-ttu-id="25b31-1055">end-of-mib (MIB の末尾) の値を設定します</span><span class="sxs-lookup"><span data-stu-id="25b31-1055">Set end-of-mib value</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1056">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1056">Prototype</span></span>

```c
UINT  nx_snmp_object_end_of_mib(VOID *not_used_ptr, 
                              NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1057">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1057">Description</span></span>

<span data-ttu-id="25b31-1058">このサービスでは、MIB の末尾を示すオブジェクトを作成します。通常 GET または GETNEXT アプリケーション コールバック ルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1058">This service creates an object signaling the end of the MIB and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1059">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1059">Input Parameters</span></span>

- <span data-ttu-id="25b31-1060">**not_used_ptr** 使用しないポインター - NX_NULL にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="25b31-1060">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="25b31-1061">**object_data** 配置先のオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1061">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1062">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1062">Return Values</span></span>

- <span data-ttu-id="25b31-1063">**NX_SUCCESS** (0x00) end-of-mib オブジェクトの構築に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1063">**NX_SUCCESS** (0x00) The end-of-mib object has be successfully built.</span></span>
- <span data-ttu-id="25b31-1064">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1064">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1065">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1065">Allowed From</span></span>

<span data-ttu-id="25b31-1066">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1066">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1067">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1067">Example</span></span>

```c
/* Place an end-of-mib value in my_object.  */
status =  nx_snmp_object_end_of_mib(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now an end-of-mib object. */
```

## <a name="nx_snmp_object_gauge_get"></a><span data-ttu-id="25b31-1068">nx_snmp_object_gauge_get</span><span class="sxs-lookup"><span data-stu-id="25b31-1068">nx_snmp_object_gauge_get</span></span>
<span data-ttu-id="25b31-1069">ゲージ オブジェクトを取得します</span><span class="sxs-lookup"><span data-stu-id="25b31-1069">Get gauge object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1070">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1070">Prototype</span></span>

```c
UINT  nx_snmp_object_gauge_get(VOID *source_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1071">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1071">Description</span></span>

<span data-ttu-id="25b31-1072">このサービスでは、ソースへのポインターで指定したアドレスのゲージ オブジェクトを取得し、NetX オブジェクト データ構造体に配置します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1072">This service retrieves the gauge object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="25b31-1073">このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1073">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1074">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1074">Input Parameters</span></span>

- <span data-ttu-id="25b31-1075">**source_ptr** ゲージのソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1075">**source_ptr** Pointer to gauge source.</span></span>
- <span data-ttu-id="25b31-1076">**object_data** 配置先のオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1076">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1077">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1077">Return Values</span></span>

- <span data-ttu-id="25b31-1078">**NX_SUCCESS** (0x00) ゲージ オブジェクトの取得に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1078">**NX_SUCCESS** (0x00) The gauge object has be successfully retrieved.</span></span>
- <span data-ttu-id="25b31-1079">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1079">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1080">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1080">Allowed From</span></span>

<span data-ttu-id="25b31-1081">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1081">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1082">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1082">Example</span></span>

```c
/* Get the value of ifSpeed (1.3.6.1.2.1.2.2.1.5.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_gauge_get(&ifSpeed, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ifSpeed gauge value. */
```

## <a name="nx_snmp_object_gauge_set"></a><span data-ttu-id="25b31-1083">nx_snmp_object_gauge_set</span><span class="sxs-lookup"><span data-stu-id="25b31-1083">nx_snmp_object_gauge_set</span></span>
<span data-ttu-id="25b31-1084">ゲージ オブジェクトを設定します</span><span class="sxs-lookup"><span data-stu-id="25b31-1084">Set gauge object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1085">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1085">Prototype</span></span>

```c
UINT  nx_snmp_object_gauge_set(VOID *destination_ptr,
                                     NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1086">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1086">Description</span></span>

<span data-ttu-id="25b31-1087">このサービスでは、設定先へのポインターで指定したアドレスのゲージを、NetX オブジェクト データ構造体にあるゲージの値に設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1087">This service sets the gauge at the address specified by the destination pointer with the gauge value in the NetX object data structure.</span></span> <span data-ttu-id="25b31-1088">このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1088">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1089">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1089">Input Parameters</span></span>

- <span data-ttu-id="25b31-1090">**destination_ptr** ゲージの設定先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1090">**destination_ptr** Pointer to gauge destination.</span></span>
- <span data-ttu-id="25b31-1091">**object_data** ゲージのソースのオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1091">**object_data** Pointer to gauge source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1092">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1092">Return Values</span></span>

- <span data-ttu-id="25b31-1093">**NX_SUCCESS** (0x00) ゲージ オブジェクトの設定に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1093">**NX_SUCCESS** (0x00) The gauge object has be successfully set.</span></span>
- <span data-ttu-id="25b31-1094">**NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-1094">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="25b31-1095">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1095">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1096">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1096">Allowed From</span></span>

<span data-ttu-id="25b31-1097">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1097">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1098">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1098">Example</span></span>

```c
/* Set the value of “my_gauge” from the gauge value in my_object.  */
status =  nx_snmp_object_gauge_set(&my_gauge, my_object);

/* If status is NX_SUCCESS, the my_gauge now contains the new gauge value. */
```

## <a name="nx_snmp_object_id_get"></a><span data-ttu-id="25b31-1099">nx_snmp_object_id_get</span><span class="sxs-lookup"><span data-stu-id="25b31-1099">nx_snmp_object_id_get</span></span>
<span data-ttu-id="25b31-1100">オブジェクト ID を取得します</span><span class="sxs-lookup"><span data-stu-id="25b31-1100">Get object id</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1101">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1101">Prototype</span></span>

```c
UINT  nx_snmp_object_id_get(VOID *source_ptr, 
                            NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1102">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1102">Description</span></span>

<span data-ttu-id="25b31-1103">このサービスでは、ソースへのポインターで指定したアドレスのオブジェクト ID (SMI の表記形式の ASCII 文字列) を取得し、NetX オブジェクト データ構造体に配置します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1103">This service retrieves the object ID (in ASCII SIM notation) at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="25b31-1104">このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1104">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1105">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1105">Input Parameters</span></span>

- <span data-ttu-id="25b31-1106">**source_ptr** オブジェクト ID のソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1106">**source_ptr** Pointer to object ID source.</span></span>
- <span data-ttu-id="25b31-1107">**object_data** 配置先のオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1107">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1108">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1108">Return Values</span></span>

- <span data-ttu-id="25b31-1109">**NX_SUCCESS** (0x00) オブジェクト ID の取得に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1109">**NX_SUCCESS** (0x00) The object ID has be successfully retrieved.</span></span>
- <span data-ttu-id="25b31-1110">**NX_SNMP_ERROR** (0x100) オブジェクトの長さが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1110">**NX_SNMP_ERROR** (0x100) Invalid length of object</span></span>
- <span data-ttu-id="25b31-1111">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1111">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1112">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1112">Allowed From</span></span>

<span data-ttu-id="25b31-1113">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1113">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1114">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1114">Example</span></span>

```c
/* Get the value of sysObjectID(1.3.6.1.2.1.1.2.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_id_get(&sysObjectID, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysObjectID value. */
```

## <a name="nx_snmp_object_id_set"></a><span data-ttu-id="25b31-1115">nx_snmp_object_id_set</span><span class="sxs-lookup"><span data-stu-id="25b31-1115">nx_snmp_object_id_set</span></span>
<span data-ttu-id="25b31-1116">オブジェクト ID を設定します</span><span class="sxs-lookup"><span data-stu-id="25b31-1116">Set object id</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1117">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1117">Prototype</span></span>

```c
UINT  nx_snmp_object_id_set(VOID *destination_ptr, 
                             NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1118">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1118">Description</span></span>

<span data-ttu-id="25b31-1119">このサービスでは、設定先へのポインターで指定したアドレスのオブジェクト ID (SMI の表記形式の ASCII 文字列) を、NetX オブジェクト データ構造体にあるオブジェクト ID に設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1119">This service sets the object ID (in ASCII SIM notation) at the address specified by the destination pointer with the object ID in the NetX object data structure.</span></span> <span data-ttu-id="25b31-1120">このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1120">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1121">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1121">Input Parameters</span></span>

- <span data-ttu-id="25b31-1122">**destination_ptr** オブジェクト ID の設定先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1122">**destination_ptr** Pointer to object ID destination.</span></span>
- <span data-ttu-id="25b31-1123">**object_data** オブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1123">**object_data** Pointer to object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1124">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1124">Return Values</span></span>

- <span data-ttu-id="25b31-1125">**NX_SUCCESS** (0x00) オブジェクト ID の設定に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1125">**NX_SUCCESS** (0x00) The object ID has been successfully set.</span></span>
- <span data-ttu-id="25b31-1126">**NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-1126">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="25b31-1127">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1127">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1128">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1128">Allowed From</span></span>

<span data-ttu-id="25b31-1129">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1129">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1130">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1130">Example</span></span>

```c
/* Set the string “my_object_id” with the object ID value contained 
   in my_object.  */
status =  nx_snmp_object_id_set(my_object_id, my_object);

/* If status is NX_SUCCESS, the my_object_id now contains the object ID value. */
```

## <a name="nx_snmp_object_integer_get"></a><span data-ttu-id="25b31-1131">nx_snmp_object_integer_get</span><span class="sxs-lookup"><span data-stu-id="25b31-1131">nx_snmp_object_integer_get</span></span>
<span data-ttu-id="25b31-1132">整数オブジェクトを取得します</span><span class="sxs-lookup"><span data-stu-id="25b31-1132">Get integer object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1133">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1133">Prototype</span></span>

```c
UINT  nx_snmp_object_integer_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1134">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1134">Description</span></span>

<span data-ttu-id="25b31-1135">このサービスでは、ソースへのポインターで指定したアドレスの整数オブジェクトを取得し、NetX オブジェクト データ構造体に配置します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1135">This service retrieves the integer object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="25b31-1136">このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1136">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1137">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1137">Input Parameters</span></span>

- <span data-ttu-id="25b31-1138">**source_ptr** 整数のソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1138">**source_ptr** Pointer to integer source.</span></span>
- <span data-ttu-id="25b31-1139">**object_data** 配置先のオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1139">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1140">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1140">Return Values</span></span>

- <span data-ttu-id="25b31-1141">**NX_SUCCESS** (0x00) 整数オブジェクトの取得に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1141">**NX_SUCCESS** (0x00) The integer object has been successfully retrieved.</span></span>
- <span data-ttu-id="25b31-1142">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1142">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1143">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1143">Allowed From</span></span>

<span data-ttu-id="25b31-1144">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1144">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1145">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1145">Example</span></span>

```c
/* Get the value of sysServices (1.3.6.1.2.1.1.7.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_integer_get(&sysServices, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysServices value. */
```

## <a name="nx_snmp_object_integer_set"></a><span data-ttu-id="25b31-1146">nx_snmp_object_integer_set</span><span class="sxs-lookup"><span data-stu-id="25b31-1146">nx_snmp_object_integer_set</span></span>
<span data-ttu-id="25b31-1147">整数オブジェクトを設定します</span><span class="sxs-lookup"><span data-stu-id="25b31-1147">Set integer object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1148">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1148">Prototype</span></span>

```c
UINT  nx_snmp_object_integer_set(VOID *destination_ptr,
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1149">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1149">Description</span></span>

<span data-ttu-id="25b31-1150">このサービスでは、設定先へのポインターで指定したアドレスの整数を、NetX オブジェクト データ構造体にある整数値に設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1150">This service sets the integer at the address specified by the destination pointer with the integer value in the NetX object data structure.</span></span> <span data-ttu-id="25b31-1151">このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1151">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1152">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1152">Input Parameters</span></span>

- <span data-ttu-id="25b31-1153">**destination_ptr** 整数の設定先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1153">**destination_ptr** Pointer to integer destination.</span></span>
- <span data-ttu-id="25b31-1154">**object_data** 整数のソースのオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1154">**object_data** Pointer to integer source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1155">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1155">Return Values</span></span>

- <span data-ttu-id="25b31-1156">**NX_SUCCESS** (0x00) 整数オブジェクトの設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="25b31-1156">**NX_SUCCESS** (0x00) The integer object has been successfully set.</span></span>
- <span data-ttu-id="25b31-1157">**NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-1157">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="25b31-1158">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1158">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1159">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1159">Allowed From</span></span>

<span data-ttu-id="25b31-1160">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1160">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1161">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1161">Example</span></span>

```c
/* Set the value of ifAdminStatus from the integer value in my_object.  */
status =  nx_snmp_object_integer_set(&ifAdminStatus, my_object);

/* If status is NX_SUCCESS, ifAdnminStatus now contains the new integer value. */
```

## <a name="nx_snmp_object_ip_address_get"></a><span data-ttu-id="25b31-1162">nx_snmp_object_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="25b31-1162">nx_snmp_object_ip_address_get</span></span>
<span data-ttu-id="25b31-1163">IP アドレス オブジェクトを取得します (IPv4 のみ)</span><span class="sxs-lookup"><span data-stu-id="25b31-1163">Get IP address object (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-1164">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1164">Prototype</span></span>

```c
UINT  nx_snmp_object_ip_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1165">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1165">Description</span></span>

<span data-ttu-id="25b31-1166">このサービスでは、ソースへのポインターで指定したアドレスの IP アドレス オブジェクトを取得し、NetX オブジェクト データ構造体に配置します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1166">This service retrieves the IP address object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="25b31-1167">このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1167">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1168">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1168">Input Parameters</span></span>

- <span data-ttu-id="25b31-1169">**source_ptr** IPv4 アドレスのソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1169">**source_ptr** Pointer to IPv4 address source.</span></span>
- <span data-ttu-id="25b31-1170">**object_data** 配置先のオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1170">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1171">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1171">Return Values</span></span>

- <span data-ttu-id="25b31-1172">**NX_SUCCESS** (0x00) IP アドレス オブジェクトの取得に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1172">**NX_SUCCESS** (0x00) The IP address object has been successfully retrieved.</span></span>
- <span data-ttu-id="25b31-1173">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1173">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1174">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1174">Allowed From</span></span>

<span data-ttu-id="25b31-1175">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1175">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1176">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1176">Example</span></span>

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ip_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ipv6_address_get"></a><span data-ttu-id="25b31-1177">nx_snmp_object_ipv6_address_get</span><span class="sxs-lookup"><span data-stu-id="25b31-1177">nx_snmp_object_ipv6_address_get</span></span>
<span data-ttu-id="25b31-1178">IP アドレス オブジェクトを取得します (IPv6 のみ)</span><span class="sxs-lookup"><span data-stu-id="25b31-1178">Get IP address object (IPv6 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="25b31-1179">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1179">Prototype</span></span>

```c
UINT  nx_snmp_object_ipv6_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA 
                                      *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1180">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1180">Description</span></span>

<span data-ttu-id="25b31-1181">このサービスでは、ソースへのポインターで指定したアドレスの IPv6 アドレス オブジェクトを取得し、NetX オブジェクト データ構造体に配置します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1181">This service retrieves the IPv6 address object at the address specified by the source pointer and places it in the NetX object data structure.</span></span>
<span data-ttu-id="25b31-1182">このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1182">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1183">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1183">Input Parameters</span></span>

- <span data-ttu-id="25b31-1184">**source_ptr** IPv6 アドレスのソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1184">**source_ptr** Pointer to IPv6 address source.</span></span>
- <span data-ttu-id="25b31-1185">**object_data** 配置先のオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1185">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1186">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1186">Return Values</span></span>

- <span data-ttu-id="25b31-1187">**NX_SUCCESS** (0x00) IP アドレス オブジェクトの取得に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1187">**NX_SUCCESS** (0x00) The IP address object has been successfully retrieved.</span></span>
- <span data-ttu-id="25b31-1188">**NX_SNMP_ERROR_WRONGTYPE** (0x07) 入力した SNMP オブジェクト コードが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1188">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Incorrect input SNMP object code</span></span>
- <span data-ttu-id="25b31-1189">**NX_NOT_ENABLED** (0x14) IPv6 が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="25b31-1189">**NX_NOT_ENABLED** (0x14) IPv6 not enabled</span></span>
- <span data-ttu-id="25b31-1190">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1190">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1191">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1191">Allowed From</span></span>

<span data-ttu-id="25b31-1192">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1192">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1193">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1193">Example</span></span>

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ipv6_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ip_address_set"></a><span data-ttu-id="25b31-1194">nx_snmp_object_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="25b31-1194">nx_snmp_object_ip_address_set</span></span>
<span data-ttu-id="25b31-1195">IPv4 アドレス オブジェクトを設定します</span><span class="sxs-lookup"><span data-stu-id="25b31-1195">Set IPv4 address object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1196">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1196">Prototype</span></span>

```c
UINT  nx_snmp_object_ip_address_set(VOID *destination_ptr, 
                                    NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1197">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1197">Description</span></span>

<span data-ttu-id="25b31-1198">このサービスでは、設定先へのポインターで指定した IPv4 アドレスを、NetX オブジェクト データ構造体にある IP アドレスに設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1198">This service sets the IPv4 address at the address specified by the destination pointer with the IP address in the NetX object data structure.</span></span> <span data-ttu-id="25b31-1199">このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1199">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1200">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1200">Input Parameters</span></span>

- <span data-ttu-id="25b31-1201">**destination_ptr** 設定先の IP アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1201">**destination_ptr** Pointer to IP address to set.</span></span>
- <span data-ttu-id="25b31-1202">**object_data** IP アドレス オブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1202">**object_data** Pointer to IP address object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1203">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1203">Return Values</span></span>

- <span data-ttu-id="25b31-1204">**NX_SUCCESS** (0x00) IP アドレス オブジェクトの設定に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1204">**NX_SUCCESS** (0x00) The IP address object has been successfully set.</span></span>
- <span data-ttu-id="25b31-1205">**NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-1205">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="25b31-1206">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1206">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1207">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1207">Allowed From</span></span>

<span data-ttu-id="25b31-1208">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1208">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1209">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1209">Example</span></span>

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ip_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_ipv6_address_set"></a><span data-ttu-id="25b31-1210">nx_snmp_object_ipv6_address_set</span><span class="sxs-lookup"><span data-stu-id="25b31-1210">nx_snmp_object_ipv6_address_set</span></span>
<span data-ttu-id="25b31-1211">IPv6 アドレス オブジェクトを設定します</span><span class="sxs-lookup"><span data-stu-id="25b31-1211">Set IPv6 address object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1212">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1212">Prototype</span></span>

```c
UINT  nx_snmp_object_ipv6_address_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA  
                                      *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1213">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1213">Description</span></span>

<span data-ttu-id="25b31-1214">このサービスでは、設定先へのポインターで指定した IPv6 アドレスを、NetX オブジェクト データ構造体にある IP アドレスに設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1214">This service sets the IPv6 address at the address specified by the destination pointer with the IP address in the NetX object data structure.</span></span> <span data-ttu-id="25b31-1215">このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1215">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1216">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1216">Input Parameters</span></span>

- <span data-ttu-id="25b31-1217">**destination_ptr** 設定先の IP アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1217">**destination_ptr** Pointer to IP address to set.</span></span>
- <span data-ttu-id="25b31-1218">**object_data** IP アドレス オブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1218">**object_data** Pointer to IP address object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1219">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1219">Return Values</span></span>

- <span data-ttu-id="25b31-1220">**NX_SUCCESS** (0x00) IPv6 アドレスの設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="25b31-1220">**NX_SUCCESS** (0x00) The IPv6 address has been successfully set.</span></span>
- <span data-ttu-id="25b31-1221">**NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-1221">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="25b31-1222">**NX_NOT_ENABLED** (0x14) IPv6 が有効になっていません</span><span class="sxs-lookup"><span data-stu-id="25b31-1222">**NX_NOT_ENABLED** (0x14) IPv6 not enabled</span></span>
- <span data-ttu-id="25b31-1223">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1223">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1224">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1224">Allowed From</span></span>

<span data-ttu-id="25b31-1225">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1225">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1226">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1226">Example</span></span>

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ipv6_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_no_instance"></a><span data-ttu-id="25b31-1227">nx_snmp_object_no_instance</span><span class="sxs-lookup"><span data-stu-id="25b31-1227">nx_snmp_object_no_instance</span></span>
<span data-ttu-id="25b31-1228">インスタンス不在オブジェクトを設定します</span><span class="sxs-lookup"><span data-stu-id="25b31-1228">Set no-instance object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1229">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1229">Prototype</span></span>

```c
UINT  nx_snmp_object_no_instance(VOID *not_used_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1230">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1230">Description</span></span>

<span data-ttu-id="25b31-1231">このサービスでは、指定したオブジェクトのインスタンスが存在しなかったことを示すオブジェクトを作成します。通常 GET または GETNEXT アプリケーション コールバック ルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1231">This service creates an object signaling that there was no instance of the specified object and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1232">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1232">Input Parameters</span></span>

- <span data-ttu-id="25b31-1233">**not_used_ptr** 使用しないポインター - NX_NULL にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="25b31-1233">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="25b31-1234">**object_data** 配置先のオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1234">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1235">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1235">Return Values</span></span>

- <span data-ttu-id="25b31-1236">**NX_SUCCESS** (0x00) インスタンス不在オブジェクトの構築に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1236">**NX_SUCCESS** (0x00) The no-instance object has been successfully built.</span></span>
- <span data-ttu-id="25b31-1237">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1237">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1238">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1238">Allowed From</span></span>

<span data-ttu-id="25b31-1239">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1239">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1240">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1240">Example</span></span>

```c
/* Place no-instance value in my_object.  */
status =  nx_snmp_object_no_instance(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a no-instance object. */
```

## <a name="nx_snmp_object_not_found"></a><span data-ttu-id="25b31-1241">nx_snmp_object_not_found</span><span class="sxs-lookup"><span data-stu-id="25b31-1241">nx_snmp_object_not_found</span></span>
<span data-ttu-id="25b31-1242">不検出オブジェクトを作成します</span><span class="sxs-lookup"><span data-stu-id="25b31-1242">Set not-found object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1243">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1243">Prototype</span></span>

```c
UINT  nx_snmp_object_not_found(VOID *not_used_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1244">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1244">Description</span></span>

<span data-ttu-id="25b31-1245">このサービスでは、オブジェクトが見つからなかったことを示すオブジェクトを作成します。通常 GET または GETNEXT アプリケーション コールバック ルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1245">This service creates an object signaling the object was not found and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1246">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1246">Input Parameters</span></span>

- <span data-ttu-id="25b31-1247">**not_used_ptr** 使用しないポインター - NX_NULL にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="25b31-1247">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="25b31-1248">**object_data** 配置先のオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1248">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1249">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1249">Return Values</span></span>

- <span data-ttu-id="25b31-1250">**NX_SUCCESS** (0x00) 不検出オブジェクトの構築に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1250">**NX_SUCCESS** (0x00) The not-found object has been successfully built.</span></span>
- <span data-ttu-id="25b31-1251">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1251">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1252">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1252">Allowed From</span></span>

<span data-ttu-id="25b31-1253">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1253">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1254">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1254">Example</span></span>

```c
/* Place not-found value in my_object.  */
status =  nx_snmp_object_not_found(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a not-found object. */
```

## <a name="nx_snmp_object_octet_string_get"></a><span data-ttu-id="25b31-1255">nx_snmp_object_octet_string_get</span><span class="sxs-lookup"><span data-stu-id="25b31-1255">nx_snmp_object_octet_string_get</span></span>
<span data-ttu-id="25b31-1256">オクテット文字列オブジェクトを取得します</span><span class="sxs-lookup"><span data-stu-id="25b31-1256">Get octet string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1257">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1257">Prototype</span></span>

```c
UINT  nx_snmp_object_octet_string_get(VOID *source_ptr,
                                            NX_SNMP_OBJECT_DATA *object_data, 
                                      UINT length);
```
### <a name="description"></a><span data-ttu-id="25b31-1258">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1258">Description</span></span>

<span data-ttu-id="25b31-1259">このサービスでは、ソースへのポインターで指定したアドレスのオクテット文字列を取得し、NetX オブジェクト データ構造体に配置します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1259">This service retrieves the octet string at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="25b31-1260">このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1260">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1261">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1261">Input Parameters</span></span>

- <span data-ttu-id="25b31-1262">**source_ptr** オクテット文字列のソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1262">**source_ptr** Pointer to octet string source.</span></span>
- <span data-ttu-id="25b31-1263">**object_data** 配置先のオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1263">**object_data** Pointer to destination object structure.</span></span>
- <span data-ttu-id="25b31-1264">**length** オクテット文字列のバイト数。</span><span class="sxs-lookup"><span data-stu-id="25b31-1264">**length** Number of bytes in octet string.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1265">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1265">Return Values</span></span>

- <span data-ttu-id="25b31-1266">**NX_SUCCESS** (0x00) オクテット文字列オブジェクトの取得に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1266">**NX_SUCCESS** (0x00) The octet string object has been successfully retrieved.</span></span>
- <span data-ttu-id="25b31-1267">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1267">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1268">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1268">Allowed From</span></span>

<span data-ttu-id="25b31-1269">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1269">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1270">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1270">Example</span></span>

```c
/* Get the value of the 6-byte ifPhysAddress (1.3.6.1.2.1.2.2.1.6.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_octet_string_get(ifPhysAddress, my_object, 6);

/* If status is NX_SUCCESS, the my_object now contains the ifPhysAddress value. */
```

## <a name="nx_snmp_object_octet_string_set"></a><span data-ttu-id="25b31-1271">nx_snmp_object_octet_string_set</span><span class="sxs-lookup"><span data-stu-id="25b31-1271">nx_snmp_object_octet_string_set</span></span>
<span data-ttu-id="25b31-1272">オクテット文字列オブジェクトを設定します</span><span class="sxs-lookup"><span data-stu-id="25b31-1272">Set octet string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1273">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1273">Prototype</span></span>

```c
UINT  nx_snmp_object_octet_string_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1274">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1274">Description</span></span>

<span data-ttu-id="25b31-1275">このサービスでは、設定先へのポインターで指定したアドレスのオクテット文字列を、NetX オブジェクト データ構造体にあるオクテット文字列に設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1275">This service sets the octet string at the address specified by the destination pointer with the octet string in the NetX object data structure.</span></span> <span data-ttu-id="25b31-1276">このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1276">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1277">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1277">Input Parameters</span></span>

- <span data-ttu-id="25b31-1278">**destination_ptr** オクテット文字列の設定先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1278">**destination_ptr** Pointer to octet string destination.</span></span>
- <span data-ttu-id="25b31-1279">**object_data** オクテット文字列のソースのオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1279">**object_data** Pointer to octet string source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1280">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1280">Return Values</span></span>

- <span data-ttu-id="25b31-1281">**NX_SUCCESS** (0x00) オクテット文字列オブジェクトの設定に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1281">**NX_SUCCESS** (0x00) The octet string object has been successfully set.</span></span>
- <span data-ttu-id="25b31-1282">**NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-1282">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="25b31-1283">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1283">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1284">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1284">Allowed From</span></span>

<span data-ttu-id="25b31-1285">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1285">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1286">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1286">Example</span></span>

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   octet string in my_object.  */
status =  nx_snmp_object_octet_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new octet string. */
```

## <a name="nx_snmp_object_string_get"></a><span data-ttu-id="25b31-1287">nx_snmp_object_string_get</span><span class="sxs-lookup"><span data-stu-id="25b31-1287">nx_snmp_object_string_get</span></span>
<span data-ttu-id="25b31-1288">ASCII 文字列オブジェクトを取得します</span><span class="sxs-lookup"><span data-stu-id="25b31-1288">Get ASCII string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1289">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1289">Prototype</span></span>

```c
UINT  nx_snmp_object_string_get(VOID *source_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1290">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1290">Description</span></span>

<span data-ttu-id="25b31-1291">このサービスでは、ソースへのポインターで指定したアドレスの ASCII 文字列を取得し、NetX オブジェクト データ構造体に配置します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1291">This service retrieves the ASCII string at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="25b31-1292">このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1292">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1293">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1293">Input Parameters</span></span>

- <span data-ttu-id="25b31-1294">**source_ptr** ASCII 文字列のソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1294">**source_ptr** Pointer to ASCII string source.</span></span>
- <span data-ttu-id="25b31-1295">**object_data** 配置先のオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1295">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1296">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1296">Return Values</span></span>

- <span data-ttu-id="25b31-1297">**NX_SUCCESS** (0x00) ASCII 文字列オブジェクトの取得に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1297">**NX_SUCCESS** (0x00) The ASCII string object has been successfully retrieved.</span></span>
- <span data-ttu-id="25b31-1298">**NX_SNMP_ERROR** (0x100) 文字列が大きすぎます</span><span class="sxs-lookup"><span data-stu-id="25b31-1298">**NX_SNMP_ERROR** (0x100) String is too big</span></span>  
- <span data-ttu-id="25b31-1299">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1299">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1300">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1300">Allowed From</span></span>

<span data-ttu-id="25b31-1301">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1301">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1302">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1302">Example</span></span>

```c
/* Get the value of the sysDescr (1.3.6.1.2.1.1.1.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_string_get(sysDescr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysDescr string. */
```

## <a name="nx_snmp_object_string_set"></a><span data-ttu-id="25b31-1303">nx_snmp_object_string_set</span><span class="sxs-lookup"><span data-stu-id="25b31-1303">nx_snmp_object_string_set</span></span>
<span data-ttu-id="25b31-1304">ASCII 文字列オブジェクトを設定します</span><span class="sxs-lookup"><span data-stu-id="25b31-1304">Set ASCII string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1305">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1305">Prototype</span></span>

```c
UINT  nx_snmp_object_string_set(VOID *destination_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1306">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1306">Description</span></span>

<span data-ttu-id="25b31-1307">このサービスでは、設定先へのポインターで指定したアドレスの ASCII 文字列を、NetX オブジェクト データ構造体にある ASCII 文字列に設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1307">This service sets the ASCII string at the address specified by the destination pointer with the ASCII string in the NetX object data structure.</span></span> <span data-ttu-id="25b31-1308">このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1308">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1309">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1309">Input Parameters</span></span>

- <span data-ttu-id="25b31-1310">**destination_ptr** ASCII 文字列の設定先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1310">**destination_ptr** Pointer to ASCII string destination.</span></span>
- <span data-ttu-id="25b31-1311">**object_data** ASCII 文字列のソースのオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1311">**object_data** Pointer to ASCII string source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1312">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1312">Return Values</span></span>

- <span data-ttu-id="25b31-1313">**NX_SUCCESS** (0x00) ASCII 文字列オブジェクトの設定に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1313">**NX_SUCCESS** (0x00) The ASCII string object has been successfully set.</span></span>
- <span data-ttu-id="25b31-1314">**NX_SNMP_ERROR** (0x100) 文字列が大きすぎます。</span><span class="sxs-lookup"><span data-stu-id="25b31-1314">**NX_SNMP_ERROR** (0x100) String too large.</span></span>
- <span data-ttu-id="25b31-1315">**NX_SNMP_ERROR_BADVALUE** (0x03) 文字列中の文字が無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1315">**NX_SNMP_ERROR_BADVALUE** (0x03) Invalid character in string</span></span>
- <span data-ttu-id="25b31-1316">**NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-1316">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="25b31-1317">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1317">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1318">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1318">Allowed From</span></span>

<span data-ttu-id="25b31-1319">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1319">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1320">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1320">Example</span></span>

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   ASCII string in my_object.  */
status =  nx_snmp_object_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new ASCII string. */
```

## <a name="nx_snmp_object_timetics_get"></a><span data-ttu-id="25b31-1321">nx_snmp_object_timetics_get</span><span class="sxs-lookup"><span data-stu-id="25b31-1321">nx_snmp_object_timetics_get</span></span>
<span data-ttu-id="25b31-1322">timetics オブジェクトを取得します</span><span class="sxs-lookup"><span data-stu-id="25b31-1322">Get timetics object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1323">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1323">Prototype</span></span>

```c
UINT  nx_snmp_object_timetics_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1324">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1324">Description</span></span>

<span data-ttu-id="25b31-1325">このサービスでは、ソースへのポインターで指定したアドレスの timetics を取得し、NetX オブジェクト データ構造体に配置します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1325">This service retrieves the timetics at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="25b31-1326">このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1326">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1327">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1327">Input Parameters</span></span>

- <span data-ttu-id="25b31-1328">**source_ptr** timetics のソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1328">**source_ptr** Pointer to timetics source.</span></span>
- <span data-ttu-id="25b31-1329">**object_data** 配置先のオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1329">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1330">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1330">Return Values</span></span>

- <span data-ttu-id="25b31-1331">**NX_SUCCESS** (0x00) timetics オブジェクトの取得に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1331">**NX_SUCCESS** (0x00) The timetics object has been successfully retrieved.</span></span>
- <span data-ttu-id="25b31-1332">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1332">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1333">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1333">Allowed From</span></span>

<span data-ttu-id="25b31-1334">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1334">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1335">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1335">Example</span></span>

```c
/* Get the value of the sysUpTime (1.3.6.1.2.1.1.3.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_timetics_get(sysUpTime, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysUpTime value. */
```

## <a name="nx_snmp_object_timetics_set"></a><span data-ttu-id="25b31-1336">nx_snmp_object_timetics_set</span><span class="sxs-lookup"><span data-stu-id="25b31-1336">nx_snmp_object_timetics_set</span></span>
<span data-ttu-id="25b31-1337">timetics オブジェクトを設定します</span><span class="sxs-lookup"><span data-stu-id="25b31-1337">Set timetics object</span></span> 

### <a name="prototype"></a><span data-ttu-id="25b31-1338">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="25b31-1338">Prototype</span></span>

```c
UINT  nx_snmp_object_timetics_set(VOID *destination_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="25b31-1339">説明</span><span class="sxs-lookup"><span data-stu-id="25b31-1339">Description</span></span>

<span data-ttu-id="25b31-1340">このサービスでは、設定先へのポインターで指定したアドレスの timetics 変数を、NetX オブジェクト データ構造体にある timetics に設定します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1340">This service sets the timetics variable at the address specified by the destination pointer with the timetics in the NetX object data structure.</span></span>
<span data-ttu-id="25b31-1341">このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25b31-1341">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="25b31-1342">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="25b31-1342">Input Parameters</span></span>

- <span data-ttu-id="25b31-1343">**destination_ptr** timetics の設定先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1343">**destination_ptr** Pointer to timetics destination.</span></span>
- <span data-ttu-id="25b31-1344">**object_data** timetics のソースのオブジェクト構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="25b31-1344">**object_data** Pointer to timetics source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="25b31-1345">戻り値</span><span class="sxs-lookup"><span data-stu-id="25b31-1345">Return Values</span></span>

- <span data-ttu-id="25b31-1346">**NX_SUCCESS** (0x00) timetics オブジェクトの設定に成功。</span><span class="sxs-lookup"><span data-stu-id="25b31-1346">**NX_SUCCESS** (0x00) The timetics object has been successfully set.</span></span>
- <span data-ttu-id="25b31-1347">**NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。</span><span class="sxs-lookup"><span data-stu-id="25b31-1347">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="25b31-1348">**NX_PTR_ERROR** (0x07) 入力したポインターが無効</span><span class="sxs-lookup"><span data-stu-id="25b31-1348">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="25b31-1349">許可元</span><span class="sxs-lookup"><span data-stu-id="25b31-1349">Allowed From</span></span>

<span data-ttu-id="25b31-1350">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="25b31-1350">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="25b31-1351">例</span><span class="sxs-lookup"><span data-stu-id="25b31-1351">Example</span></span>

```c
/* Set the value of “my_time” from the timetics value in my_object.  */
status =  nx_snmp_object_timetics_set(&my_time, my_object);

/* If status is NX_SUCCESS, my_time now contains the new timetics. */
```