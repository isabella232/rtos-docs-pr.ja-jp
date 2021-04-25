---
title: 第 4 章 - LWM2M クライアント サービスの説明
description: この章では、すべての LWM2M クライアント サービスをアルファベット順に説明します。
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 825a215ba756b39b6d76e6cc773c288e8b8aab01
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810745"
---
# <a name="chapter-4--description-of-lwm2m-client-services"></a><span data-ttu-id="1e567-103">第 4 章 LWM2M クライアント サービスの説明</span><span class="sxs-lookup"><span data-stu-id="1e567-103">Chapter 4  Description of LWM2M CLIENT Services</span></span>

<span data-ttu-id="1e567-104">この章では、以下に記載したすべての LWM2M クライアント サービスをアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="1e567-104">This chapter contains a description of all LWM2M Client services listed below in alphabetic order.</span></span>

<span data-ttu-id="1e567-105">以下の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="1e567-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the  **NX_DISABLE_ERROR_CHECKING** define that is used to disable API  error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="1e567-106">**LWM2M クライアント管理:**</span><span class="sxs-lookup"><span data-stu-id="1e567-106">**LWM2M Client Management:**</span></span>

- <span data-ttu-id="1e567-107">nx_lwm2m_client_create: *LWM2M クライアントを作成します*</span><span class="sxs-lookup"><span data-stu-id="1e567-107">nx_lwm2m_client_create: *Create LWM2M Client*</span></span>

- <span data-ttu-id="1e567-108">nx_lwm2m_client_delete: *LWM2M クライアントを削除します*</span><span class="sxs-lookup"><span data-stu-id="1e567-108">nx_lwm2m_client_delete: *Delete LWM2M Client*</span></span>

- <span data-ttu-id="1e567-109">nx_lwm2m_client_lock: *LWM2M クライアントをロックします*</span><span class="sxs-lookup"><span data-stu-id="1e567-109">nx_lwm2m_client_lock: *Lock LWM2M Client*</span></span>

- <span data-ttu-id="1e567-110">nx_lwm2m_client_unlock: *LWM2M クライアントをロック解除します*</span><span class="sxs-lookup"><span data-stu-id="1e567-110">nx_lwm2m_client_unlock: *Unlock LWM2M Client*</span></span>

<span data-ttu-id="1e567-111">**LWM2M クライアント セッション管理:**</span><span class="sxs-lookup"><span data-stu-id="1e567-111">**LWM2M Client Session Management:**</span></span>

- <span data-ttu-id="1e567-112">nx_lwm2m_client_session_create: *LWM2M クライアント セッションを作成します*</span><span class="sxs-lookup"><span data-stu-id="1e567-112">nx_lwm2m_client_session_create: *Create LWM2M Client Session*</span></span>

- <span data-ttu-id="1e567-113">nx_lwm2m_client_session_delete: *LWM2M クライアント セッションを削除します*</span><span class="sxs-lookup"><span data-stu-id="1e567-113">nx_lwm2m_client_session_delete: *Delete LWM2M Client Session*</span></span>

- <span data-ttu-id="1e567-114">nx_lwm2m_client_session_bootstrap: *ブートストラップ サーバーとのセッションを開始します*</span><span class="sxs-lookup"><span data-stu-id="1e567-114">nx_lwm2m_client_session_bootstrap: *Start a session with a Bootstrap Server*</span></span>

- <span data-ttu-id="1e567-115">nx_lwm2m_client_session_bootstrap_dtls: *ブートストラップ サーバーとのセキュリティで保護されたセッションを開始します*</span><span class="sxs-lookup"><span data-stu-id="1e567-115">nx_lwm2m_client_session_bootstrap_dtls: *Start a secure session with a Bootstrap Server*</span></span>

- <span data-ttu-id="1e567-116">nx_lwm2m_client_session_register_info_get: *LWM2M サーバーの登録情報を取得します*</span><span class="sxs-lookup"><span data-stu-id="1e567-116">nx_lwm2m_client_session_register_info_get: *Get LWM2M Server register info*</span></span>

- <span data-ttu-id="1e567-117">nx_lwm2m_client_session_register: *LWM2M Server とのセッションを開始します*</span><span class="sxs-lookup"><span data-stu-id="1e567-117">nx_lwm2m_client_session_register: *Start a session with a LWM2M Server*</span></span>

- <span data-ttu-id="1e567-118">nx_lwm2m_client_session_register_dtls: *LWM2M サーバーとのセキュアなセッションを開始します*</span><span class="sxs-lookup"><span data-stu-id="1e567-118">nx_lwm2m_client_session_register_dtls: *Start a secure session with a LWM2M Server*</span></span>

- <span data-ttu-id="1e567-119">nx_lwm2m_client_session_update: *LWM2M サーバーとのセッションを更新します*</span><span class="sxs-lookup"><span data-stu-id="1e567-119">nx_lwm2m_client_session_update: *Update a session with a LWM2M Server*</span></span>

- <span data-ttu-id="1e567-120">nx_lwm2m_client_session_deregister: *LWM2M サーバーとのセッションを終了します*</span><span class="sxs-lookup"><span data-stu-id="1e567-120">nx_lwm2m_client_session_deregister: *Terminate a session with a LWM2M Server*</span></span>

- <span data-ttu-id="1e567-121">nx_lwm2m_client_session_error_get: *セッションの最後のエラーを取得します*</span><span class="sxs-lookup"><span data-stu-id="1e567-121">nx_lwm2m_client_session_error_get: *Get last error of a session*</span></span>

<span data-ttu-id="1e567-122">**デバイス オブジェクトの実装:**</span><span class="sxs-lookup"><span data-stu-id="1e567-122">**Device Object Implementation:**</span></span>

- <span data-ttu-id="1e567-123">nx_lwm2m_client_device_callbacks_set: *デバイス オブジェクトのアプリケーションのコールバックを設定します*</span><span class="sxs-lookup"><span data-stu-id="1e567-123">nx_lwm2m_client_device_callbacks_set: *Set Device Object application callbacks*</span></span>

- <span data-ttu-id="1e567-124">nx_lwm2m_client_device_error_push:*デバイス オブジェクトにエラー コードを追加します*</span><span class="sxs-lookup"><span data-stu-id="1e567-124">nx_lwm2m_client_device_error_push: *Add error code to Device Object*</span></span>

- <span data-ttu-id="1e567-125">nx_lwm2m_client_device_error_reset: *デバイス オブジェクトのエラー コードをリセットします*</span><span class="sxs-lookup"><span data-stu-id="1e567-125">nx_lwm2m_client_device_error_reset: *Reset error codes of Device Object*</span></span>

- <span data-ttu-id="1e567-126">nx_lwm2m_client_device_resource_changed: *デバイス オブジェクト リソースのシグナルを変更します*</span><span class="sxs-lookup"><span data-stu-id="1e567-126">nx_lwm2m_client_device_resource_changed: *Signal change of Device Object resource*</span></span>

<span data-ttu-id="1e567-127">**ファームウェア更新オブジェクトの実装:**</span><span class="sxs-lookup"><span data-stu-id="1e567-127">**Firmware Update Object Implementation:**</span></span>

- <span data-ttu-id="1e567-128">nx_lwm2m_firmware_create: *ファームウェア更新オブジェクトを作成します*</span><span class="sxs-lookup"><span data-stu-id="1e567-128">nx_lwm2m_firmware_create: *Create Firmware Update Object*</span></span>

- <span data-ttu-id="1e567-129">nx_lwm2m_firmware_package_info_set: *ファームウェア更新パッケージの情報を設定します*</span><span class="sxs-lookup"><span data-stu-id="1e567-129">nx_lwm2m_firmware_package_info_set: *Set Firmware Update Package Information*</span></span>

- <span data-ttu-id="1e567-130">nx_lwm2m_firmware_result_set: *ファームウェア更新の結果を設定します*</span><span class="sxs-lookup"><span data-stu-id="1e567-130">nx_lwm2m_firmware_result_set: *Set Firmware Update Result*</span></span>

- <span data-ttu-id="1e567-131">nx_lwm2m_firmware_state_set: *ファームウェアの更新状態を設定します*</span><span class="sxs-lookup"><span data-stu-id="1e567-131">nx_lwm2m_firmware_state_set: *Set Firmware Update State*</span></span>

<span data-ttu-id="1e567-132">**カスタム オブジェクトの実装:**</span><span class="sxs-lookup"><span data-stu-id="1e567-132">**Custom Objects Implementation:**</span></span>

- <span data-ttu-id="1e567-133">nx_lwm2m_client_object_add: *LWM2M クライアントにオブジェクトの実装を追加します*</span><span class="sxs-lookup"><span data-stu-id="1e567-133">nx_lwm2m_client_object_add: *Add Object implementation to LWM2M Client*</span></span>

- <span data-ttu-id="1e567-134">nx_lwm2m_client_object_remove: *LWM2M クライアントからオブジェクトの実装を削除します*</span><span class="sxs-lookup"><span data-stu-id="1e567-134">nx_lwm2m_client_object_remove: *Remove Object implementation from LWM2M Client*</span></span>

- <span data-ttu-id="1e567-135">nx_lwm2m_client_object_instance_add: *LWM2M クライアントにオブジェクト インスタンスを追加します*</span><span class="sxs-lookup"><span data-stu-id="1e567-135">nx_lwm2m_client_object_instance_add: *Add Object Instance to LWM2M Client*</span></span>

- <span data-ttu-id="1e567-136">nx_lwm2m_client_object_instance_remove: *LWM2M クライアントからオブジェクト インスタンスを削除します*</span><span class="sxs-lookup"><span data-stu-id="1e567-136">nx_lwm2m_client_object_instance_remove: *Remove Object Instance from LWM2M Client*</span></span>

- <span data-ttu-id="1e567-137">nx_lwm2m_object_resource_changed: *オブジェクト インスタンスのリソース値のシグナルを変更します*</span><span class="sxs-lookup"><span data-stu-id="1e567-137">nx_lwm2m_object_resource_changed: *Signal change of a resource value of an Object Instance*</span></span>

<span data-ttu-id="1e567-138">**ローカル デバイス管理**</span><span class="sxs-lookup"><span data-stu-id="1e567-138">**Local Device Management**</span></span>

- <span data-ttu-id="1e567-139">nx_lwm2m_client_object_create: *新しいオブジェクト インスタンスを作成します*</span><span class="sxs-lookup"><span data-stu-id="1e567-139">nx_lwm2m_client_object_create: *Create a new Object Instance*</span></span>

- <span data-ttu-id="1e567-140">nx_lwm2m_client_object_delete: *オブジェクト インスタンスを削除します*</span><span class="sxs-lookup"><span data-stu-id="1e567-140">nx_lwm2m_client_object_delete: *Delete an Object Instance*</span></span>

- <span data-ttu-id="1e567-141">nx_lwm2m_client_object_discover: *オブジェクト インスタンスのリソースを検出します*</span><span class="sxs-lookup"><span data-stu-id="1e567-141">nx_lwm2m_client_object_discover: *Discover resources of an Object Instance*</span></span>

- <span data-ttu-id="1e567-142">nx_lwm2m_client_object_execute: *オブジェクト インスタンスのリソースを実行します*</span><span class="sxs-lookup"><span data-stu-id="1e567-142">nx_lwm2m_client_object_execute: *Execute resource of an Object Instance*</span></span>

- <span data-ttu-id="1e567-143">nx_lwm2m_client_object_next_get: *LWM2M クライアントによって実装されているオブジェクトのリストを取得します*</span><span class="sxs-lookup"><span data-stu-id="1e567-143">nx_lwm2m_client_object_next_get: *Get the list of Objects implemented by the LWM2M Client*</span></span>

- <span data-ttu-id="1e567-144">nx_lwm2m_client_object_instance_next_get: *オブジェクトのインスタンスのリストを取得します*</span><span class="sxs-lookup"><span data-stu-id="1e567-144">nx_lwm2m_client_object_instance_next_get: *Get the list of Instances of an Object*</span></span>

- <span data-ttu-id="1e567-145">nx_lwm2m_client_object_read: *オブジェクト インスタンスのリソース値を読み取ります*</span><span class="sxs-lookup"><span data-stu-id="1e567-145">nx_lwm2m_client_object_read: *Read resources values of an Object Instance*</span></span>

- <span data-ttu-id="1e567-146">nx_lwm2m_client_object_write: *オブジェクト インスタンスのリソース値を変更します*</span><span class="sxs-lookup"><span data-stu-id="1e567-146">nx_lwm2m_client_object_write: *Change resources values of an Object instance*</span></span>

<span data-ttu-id="1e567-147">**リソースの情報と値の設定:**</span><span class="sxs-lookup"><span data-stu-id="1e567-147">**Resources Info and Values Setting:**</span></span>

- <span data-ttu-id="1e567-148">nx_lwm2m_client_resource_info_set: *リソース情報を設定します*</span><span class="sxs-lookup"><span data-stu-id="1e567-148">nx_lwm2m_client_resource_info_set: *Set the resource info*</span></span>

- <span data-ttu-id="1e567-149">nx_lwm2m_client_resource_info_set: *リソース値を文字列として設定します*</span><span class="sxs-lookup"><span data-stu-id="1e567-149">nx_lwm2m_client_resource_string_set: *Set the resource value as string*</span></span>

- <span data-ttu-id="1e567-150">nx_lwm2m_client_resource_integer32_set: *リソース値を 32 ビット整数として設定します*</span><span class="sxs-lookup"><span data-stu-id="1e567-150">nx_lwm2m_client_resource_integer32_set: *Set the resource value as 32-Bit integer*</span></span>

- <span data-ttu-id="1e567-151">nx_lwm2m_client_resource_integer64_set: *リソース値を 64 ビット整数として設定します*</span><span class="sxs-lookup"><span data-stu-id="1e567-151">nx_lwm2m_client_resource_integer64_set: *Set the resource value as 64-Bit integer*</span></span>

- <span data-ttu-id="1e567-152">nx_lwm2m_client_resource_float32_set: *リソース値を 32 ビット浮動小数点数として設定します*</span><span class="sxs-lookup"><span data-stu-id="1e567-152">nx_lwm2m_client_resource_float32_set: *Set the resource value as 32-Bit float*</span></span>

- <span data-ttu-id="1e567-153">nx_lwm2m_client_resource_float64_set: *リソース値を 64 ビット浮動小数点数として設定します*</span><span class="sxs-lookup"><span data-stu-id="1e567-153">nx_lwm2m_client_resource_float64_set: *Set the resource value as 64-Bit float*</span></span>

- <span data-ttu-id="1e567-154">nx_lwm2m_client_resource_boolean_set: *リソース値をブール値として設定します*</span><span class="sxs-lookup"><span data-stu-id="1e567-154">nx_lwm2m_client_resource_boolean_set: *Set the resource value as boolean*</span></span>

- <span data-ttu-id="1e567-155">nx_lwm2m_client_resource_objlnk_set: *リソース値をオブジェクト リンクとして設定します*</span><span class="sxs-lookup"><span data-stu-id="1e567-155">nx_lwm2m_client_resource_objlnk_set: *Set the resource value as object link*</span></span>

- <span data-ttu-id="1e567-156">nx_lwm2m_client_resource_opaque_set: *リソース値を不透明な値として設定します*</span><span class="sxs-lookup"><span data-stu-id="1e567-156">nx_lwm2m_client_resource_opaque_set: *Set the resource value as opaque*</span></span>

- <span data-ttu-id="1e567-157">nx_lwm2m_client_resource_instance_set: *リソース値を複数のリソースのインスタンスとして設定します*</span><span class="sxs-lookup"><span data-stu-id="1e567-157">nx_lwm2m_client_resource_instance_set: *Set the resource value as instance for multiple resource*</span></span>
-
- <span data-ttu-id="1e567-158">nx_lwm2m_client_resource_dim_set: *複数のリソースのリソース ディメンションを設定します。*</span><span class="sxs-lookup"><span data-stu-id="1e567-158">nx_lwm2m_client_resource_dim_set: *Set the resource dimension for multiple resource.*</span></span>

<span data-ttu-id="1e567-159">**リソースの情報と値の取得:**</span><span class="sxs-lookup"><span data-stu-id="1e567-159">**Resources Info and Values Getting:**</span></span>

- <span data-ttu-id="1e567-160">nx_lwm2m_client_resource_info_get: *リソース情報を取得します*</span><span class="sxs-lookup"><span data-stu-id="1e567-160">nx_lwm2m_client_resource_info_get: *Get the resource info*</span></span>

- <span data-ttu-id="1e567-161">nx_lwm2m_client_resource_string_get: *文字列リソースの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="1e567-161">nx_lwm2m_client_resource_string_get: *Get the value of a string resource*</span></span>

- <span data-ttu-id="1e567-162">nx_lwm2m_client_resource_integer32_get: *32 ビット整数リソースの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="1e567-162">nx_lwm2m_client_resource_integer32_get: *Get the value of a 32-Bit integer resource*</span></span>

- <span data-ttu-id="1e567-163">nx_lwm2m_client_resource_integer64_get: *64 ビット整数リソースの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="1e567-163">nx_lwm2m_client_resource_integer64_get: *Get the value of a 64-Bit integer resource*</span></span>

- <span data-ttu-id="1e567-164">nx_lwm2m_client_resource_float32_get: *32 ビット浮動小数点リソースの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="1e567-164">nx_lwm2m_client_resource_float32_get: *Get the value of a 32-Bit float resource*</span></span>

- <span data-ttu-id="1e567-165">nx_lwm2m_client_resource_float64_get: *64 ビット浮動小数点リソースの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="1e567-165">nx_lwm2m_client_resource_float64_get: *Get the value of a 64-Bit float resource*</span></span>

- <span data-ttu-id="1e567-166">nx_lwm2m_client_resource_boolean_get: *ブール値リソースの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="1e567-166">nx_lwm2m_client_resource_boolean_get: *Get the value of a boolean resource*</span></span>

- <span data-ttu-id="1e567-167">nx_lwm2m_client_resource_objlnk_get: *オブジェクト リンク リソースの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="1e567-167">nx_lwm2m_client_resource_objlnk_get: *Get the value of an object link resource*</span></span>

- <span data-ttu-id="1e567-168">nx_lwm2m_client_resource_opaque_get: *不透明なリソースの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="1e567-168">nx_lwm2m_client_resource_opaque_get: *Get the value of an opaque resource*</span></span>

- <span data-ttu-id="1e567-169">nx_lwm2m_client_resource_instance_get: *複数のリソースのリソース インスタンスを取得します*</span><span class="sxs-lookup"><span data-stu-id="1e567-169">nx_lwm2m_client_resource_instance_get: *Get the resource instance for multiple resource*</span></span>

- <span data-ttu-id="1e567-170">nx_lwm2m_client_resource_dim_get: *複数のリソースのリソース ディメンションを取得します。*</span><span class="sxs-lookup"><span data-stu-id="1e567-170">nx_lwm2m_client_resource_dim_get: *Get the resource dimension for multiple resource.*</span></span>

## <a name="nx_lwm2m_client_create"></a><span data-ttu-id="1e567-171">nx_lwm2m_client_create</span><span class="sxs-lookup"><span data-stu-id="1e567-171">nx_lwm2m_client_create</span></span>

<span data-ttu-id="1e567-172">LWM2M クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="1e567-172">Creates a LWM2M client.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-173">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-173">Prototype</span></span>

```C
UINT nx_lwm2m_client_create(
    NX_LWM2M_CLIENT client_ptr,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    const CHAR *name_ptr,
    UINT name_length,
    const CHAR *msisdn_ptr,
    UINT msisdn_length,
    UCHAR binding_modes,
    VOID *stack_ptr,
    ULONG stack_size,
    UINT priority);
```

### <a name="description"></a><span data-ttu-id="1e567-174">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-174">Description</span></span>

<span data-ttu-id="1e567-175">このサービスを使用すると、専用の ThreadX スレッドのコンテキスト内で実行される LWM2M クライアント インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-175">This service creates a LWM2M Client instance, which runs in the context of its own ThreadX thread.</span></span>

<span data-ttu-id="1e567-176">LWM2M クライアントは、次の OMA LWM2M オブジェクトを実装します: セキュリティ (0)、サーバー (1)、アクセス制御 (2)、デバイス (3)。</span><span class="sxs-lookup"><span data-stu-id="1e567-176">The LWM2M Client implements the following OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="1e567-177">その他のオブジェクトの実装は、アプリケーションによって追加される必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e567-177">The other objects implementations must be added by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-178">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-178">Parameters</span></span>

- <span data-ttu-id="1e567-179">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-179">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="1e567-180">**ip_ptr** 以前に作成された IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-180">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="1e567-181">**packet_pool_ptr** この LWM2M クライアントの既定のパケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-181">**packet_pool_ptr** Pointer to the default packet pool for this LWM2M Client.</span></span>
- <span data-ttu-id="1e567-182">**name_ptr** LWM2M クライアント エンドポイント名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-182">**name_ptr** Pointer to LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="1e567-183">**name_length** LWM2M クライアント エンドポイント名の長さ。</span><span class="sxs-lookup"><span data-stu-id="1e567-183">**name_length** Length of LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="1e567-184">**msisdn_ptr** SMS バインディングで使用するために LWM2M クライアントに到達できる MSISDN へのポインター。SMS バインディングがサポートされていない場合は、NULL にすることができます。</span><span class="sxs-lookup"><span data-stu-id="1e567-184">**msisdn_ptr** Pointer to the MSISDN where the LWM2M Client can be reached for use with the SMS binding, can be NULL if SMS binding is not supported.</span></span>
- <span data-ttu-id="1e567-185">**msisdn_length** MSISDN 番号の長さ。</span><span class="sxs-lookup"><span data-stu-id="1e567-185">**msisdn_length** Length of MSISDN number.</span></span>
- <span data-ttu-id="1e567-186">**binding_modes** LWM2M クライアントでサポートされているバインディングとモードは、NX_LWM2M_BINDING_U、NX_LWM2M_BINDING_UQ、NX_LWM2M_BINDING_S、および NX_LWM2M_BINDING_SQ フラグの組み合わせになっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e567-186">**binding_modes** The binding and modes supported by the LWM2M Client, must be a combination of NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S and NX_LWM2M_BINDING_SQ flags.</span></span>
- <span data-ttu-id="1e567-187">**stack_ptr** LWM2M クライアント スレッド スタック領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-187">**stack_ptr** Pointer to LWM2M Client thread stack area.</span></span>
- <span data-ttu-id="1e567-188">**stack_size** LWM2M クライアント スレッド スタック サイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-188">**stack_size** The LWM2M Client thread stack size.</span></span>
- <span data-ttu-id="1e567-189">**priority** LWM2M クライアントの優先順位。</span><span class="sxs-lookup"><span data-stu-id="1e567-189">**priority** Priority of LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-190">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-190">Return Values</span></span>

- <span data-ttu-id="1e567-191">**NX_SUCCESS** LWM2M クライアントの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-191">**NX_SUCCESS** The LWM2M Client has been successfully created.</span></span>
- <span data-ttu-id="1e567-192">**NX_LWM2M_CLIENT_ERROR** LWM2M クライアントの作成エラー。</span><span class="sxs-lookup"><span data-stu-id="1e567-192">**NX_LWM2M_CLIENT_ERROR** LWM2M Client create error.</span></span>
- <span data-ttu-id="1e567-193">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** ポートを使用できません。</span><span class="sxs-lookup"><span data-stu-id="1e567-193">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="1e567-194">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-194">**NX_PTR_ERROR** Invalid pointer.</span></span>
- <span data-ttu-id="1e567-195">**NX_SIZE_ERROR** スタック サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-195">**NX_SIZE_ERROR** Invalid stack size.</span></span>
- <span data-ttu-id="1e567-196">**NX_OPTION_ERROR** 優先順位が無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-196">**NX_OPTION_ERROR** Invalid priority.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-197">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-197">Allowed From</span></span>

<span data-ttu-id="1e567-198">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-198">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-199">例</span><span class="sxs-lookup"><span data-stu-id="1e567-199">Example</span></span>

```C
/* Create LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client, &ip_0, &pool_0, 
  "netxlwm2mclient", sizeof("netxlwm2mclient") - 1,           
                                NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, 
                                stack_ptr, stack_size, priority);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully created.  */
```

## <a name="nx_lwm2m_client_delete"></a><span data-ttu-id="1e567-200">nx_lwm2m_client_delete</span><span class="sxs-lookup"><span data-stu-id="1e567-200">nx_lwm2m_client_delete</span></span>

<span data-ttu-id="1e567-201">LWM2M クライアントを削除します。</span><span class="sxs-lookup"><span data-stu-id="1e567-201">Deletes a LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-202">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-202">Prototype</span></span>

```C
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-203">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-203">Description</span></span>

<span data-ttu-id="1e567-204">このサービスを使用すると、以前に作成された LWM2M クライアント インスタンスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-204">This service deletes a previously created LWM2M Client instance.</span></span>

<span data-ttu-id="1e567-205">現在クライアントにアタッチされているすべてのセッションも、この呼び出しによって削除されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-205">All sessions currently attached the client are also deleted by this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-206">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-206">Parameters</span></span>

- <span data-ttu-id="1e567-207">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-207">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-208">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-208">Return Values</span></span>

- <span data-ttu-id="1e567-209">**NX_SUCCESS** LWM2M クライアントの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-209">**NX_SUCCESS** The LWM2M Client has been successfully deleted.</span></span>
- <span data-ttu-id="1e567-210">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-210">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-211">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-211">Allowed From</span></span>

<span data-ttu-id="1e567-212">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-212">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-213">例</span><span class="sxs-lookup"><span data-stu-id="1e567-213">Example</span></span>

```c
/* Delete the LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_device_callback_set"></a><span data-ttu-id="1e567-214">nx_lwm2m_client_device_callback_set</span><span class="sxs-lookup"><span data-stu-id="1e567-214">nx_lwm2m_client_device_callback_set</span></span>

<span data-ttu-id="1e567-215">デバイス オブジェクトのアプリケーション コールバックを設定します。</span><span class="sxs-lookup"><span data-stu-id="1e567-215">Sets a device object's application callback.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-216">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-216">Prototype</span></span>

```C
UINT **nx_lwm2m_client_device_callback_set**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_OPERATION_CALLBACK operation_callback);
```

### <a name="description"></a><span data-ttu-id="1e567-217">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-217">Description</span></span>

<span data-ttu-id="1e567-218">このサービスを使用すると、LWM2M クライアントによって処理されない LWM2M デバイス オブジェクト リソースの操作を実装するためのアプリケーション コールバックがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="1e567-218">This service installs the application callback for implementing operations on the LWM2M Device Object resources that are not handled by the LWM2M Client.</span></span>

<span data-ttu-id="1e567-219">LWM2M クライアントは、次のリソースを実装します: エラー コード (11)、リセット エラー コード (12)、サポートされているバインドとモード (16)。他のリソースに対する操作は、アプリケーションにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="1e567-219">The LWM2M Client implements the following resources: Error Code (11), Reset Error Code (12) and Supported Binding and Modes (16), operations to the other resources are redirected to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-220">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-220">Parameters</span></span>

- <span data-ttu-id="1e567-221">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-221">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="1e567-222">**operation_callback** "読み取り"、"検出"、"書き込み"、および "実行" の操作コールバック。</span><span class="sxs-lookup"><span data-stu-id="1e567-222">**operation_callback** The operation callback for “Read”, “Discover”, “Write” and “Execute”.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-223">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-223">Return Values</span></span>

- <span data-ttu-id="1e567-224">**NX_SUCCESS** 操作コールバックの設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-224">**NX_SUCCESS** The operation callback has been successfully set.</span></span>
- <span data-ttu-id="1e567-225">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-225">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-226">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-226">Allowed From</span></span>

<span data-ttu-id="1e567-227">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-227">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-228">例</span><span class="sxs-lookup"><span data-stu-id="1e567-228">Example</span></span>

```c
/* Set device callback.  */
status = nx_lwm2m_client_device_callback_set(&lwm2m_client, device_operation);

/* If status is NX_SUCCESS a device callback was successfully set.  */
```

## <a name="nx_lwm2m_client_device_error_push"></a><span data-ttu-id="1e567-229">nx_lwm2m_client_device_error_push</span><span class="sxs-lookup"><span data-stu-id="1e567-229">nx_lwm2m_client_device_error_push</span></span>
<span data-ttu-id="1e567-230">デバイス オブジェクトにエラー コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e567-230">Adds an error code to a device object.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-231">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-231">Prototype</span></span>

```C
UINT **nx_lwm2m_client_device_error_push**(
    NX_LWM2M_CLIENT *client_ptr,
    UCHAR code);
```

### <a name="description"></a><span data-ttu-id="1e567-232">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-232">Description</span></span>

<span data-ttu-id="1e567-233">このサービスを使用すると、オブジェクト デバイスのエラー コード (11) リソースに新しいインスタンスが追加されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-233">This service adds a new instance to the Error Code (11) resource of the Object Device.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-234">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-234">Parameters</span></span>

- <span data-ttu-id="1e567-235">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-235">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="1e567-236">**code** 新しいエラー コード。</span><span class="sxs-lookup"><span data-stu-id="1e567-236">**code** The new error code.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-237">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-237">Return Values</span></span>

- <span data-ttu-id="1e567-238">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-238">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-239">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**</span><span class="sxs-lookup"><span data-stu-id="1e567-239">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**</span></span>

<span data-ttu-id="1e567-240">格納されているエラー コードの最大数に</span><span class="sxs-lookup"><span data-stu-id="1e567-240">The maximum number of stored error codes has</span></span>

<span data-ttu-id="1e567-241">達しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-241">been reached.</span></span>

<span data-ttu-id="1e567-242">NX_PTR_ERROR ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-242">NX_PTR_ERROR Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-243">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-243">Allowed From</span></span>

<span data-ttu-id="1e567-244">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-244">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-245">例</span><span class="sxs-lookup"><span data-stu-id="1e567-245">Example</span></span>

```C
/* Push device error 1 (Low battery power) to server.  */
status = nx_lwm2m_client_device_error_push(&lwm2m_client, 1);

/* If status is NX_SUCCESS a device error was successfully pushed.  */
```

## <a name="nx_lwm2m_client_device_error_reset"></a><span data-ttu-id="1e567-246">nx_lwm2m_client_device_error_reset</span><span class="sxs-lookup"><span data-stu-id="1e567-246">nx_lwm2m_client_device_error_reset</span></span>

<span data-ttu-id="1e567-247">デバイス オブジェクトのエラー コードをリセットします。</span><span class="sxs-lookup"><span data-stu-id="1e567-247">Resets the error codes of Device Object.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-248">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-248">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-249">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-249">Description</span></span>

<span data-ttu-id="1e567-250">このサービスを使用すると、すべてのエラー コード リソース インスタンスがデバイス オブジェクトから削除されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-250">This service deletes all error code resource instances from the Device Object.</span></span> <span data-ttu-id="1e567-251">これは、リソース リセット エラー コード (12) を実行することと同じです。</span><span class="sxs-lookup"><span data-stu-id="1e567-251">This is equivalent to executing the resource Reset Error Code (12).</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-252">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-252">Parameters</span></span>

- <span data-ttu-id="1e567-253">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-253">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-254">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-254">Return Values</span></span>

- <span data-ttu-id="1e567-255">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-255">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-256">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-256">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-257">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-257">Allowed From</span></span>

<span data-ttu-id="1e567-258">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-258">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-259">例</span><span class="sxs-lookup"><span data-stu-id="1e567-259">Example</span></span>

```c
/* Delete all device error code.  */
status = nx_lwm2m_client_device_error_reset(&lwm2m_client);

/* If status is NX_SUCCESS, reset device error successfully.  */
```

## <a name="nx_lwm2m_client_device_resource_changed"></a><span data-ttu-id="1e567-260">nx_lwm2m_client_device_resource_changed</span><span class="sxs-lookup"><span data-stu-id="1e567-260">nx_lwm2m_client_device_resource_changed</span></span>

<span data-ttu-id="1e567-261">デバイス オブジェクト リソースの変更を通知します。</span><span class="sxs-lookup"><span data-stu-id="1e567-261">Signals a change to a Device Object resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-262">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-262">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_resource_changed(
    NX_LWM2M_CLIENT *client_ptr, 
    const NX_LWM2M_RESOURCE *resource);

```

### <a name="description"></a><span data-ttu-id="1e567-263">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-263">Description</span></span>

<span data-ttu-id="1e567-264">このサービスは、アプリケーションによって、オブジェクト デバイスのリソースが変更されたことを LWM2M クライアントに通知するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-264">The service is used by the application to signal to the LWM2M Client that a resource of the Object Device has changed.</span></span> <span data-ttu-id="1e567-265">LWM2M クライアントは、リソースが LWM2M サーバーによって監視されている場合に通知を送信します。</span><span class="sxs-lookup"><span data-stu-id="1e567-265">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-266">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-266">Parameters</span></span>

- <span data-ttu-id="1e567-267">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-267">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="1e567-268">**resource** 変更されたリソースを記述する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-268">**resource** Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-269">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-269">Return Values</span></span>

- <span data-ttu-id="1e567-270">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-270">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-271">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-271">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-272">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-272">Allowed From</span></span>

<span data-ttu-id="1e567-273">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-273">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-274">例</span><span class="sxs-lookup"><span data-stu-id="1e567-274">Example</span></span>

```c
/* Change device resource.  */
status = nx_lwm2m_client_device_resource_changed(&lwm2m_client, &resource);

/* If status is NX_SUCCESS, a device resource was successfully changed.  */
```

##  <a name="nx_lwm2m_client_firmware_create"></a><span data-ttu-id="1e567-275">nx_lwm2m_client_firmware_create</span><span class="sxs-lookup"><span data-stu-id="1e567-275">nx_lwm2m_client_firmware_create</span></span>

<span data-ttu-id="1e567-276">LWM2M クライアント ファームウェア オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="1e567-276">Create a LWM2M Client Firmware Object.</span></span> 

### <a name="prototype"></a><span data-ttu-id="1e567-277">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-277">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_create(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    NX_LWM2M_CLIENT *client_ptr, 
    UINT protocols,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK update_callback);
```

### <a name="description"></a><span data-ttu-id="1e567-278">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-278">Description</span></span>

<span data-ttu-id="1e567-279">このサービスは、アプリケーションによってファームウェア オブジェクトを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-279">The service is used by the application to create firmware object.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-280">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-280">Parameters</span></span>

- <span data-ttu-id="1e567-281">**firmware_ptr** LWM2M クライアント ファームウェア オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-281">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="1e567-282">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-282">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="1e567-283">**protocols** サポートされているプロトコル。</span><span class="sxs-lookup"><span data-stu-id="1e567-283">**protocols** The supported protocols.</span></span>
- <span data-ttu-id="1e567-284">**package_callback** パッケージのコールバック。</span><span class="sxs-lookup"><span data-stu-id="1e567-284">**package_callback** The package callback.</span></span>
- <span data-ttu-id="1e567-285">**package_uri_callback** パッケージ URI のコールバック。</span><span class="sxs-lookup"><span data-stu-id="1e567-285">**package_uri_callback** The package URI callback.</span></span>
- <span data-ttu-id="1e567-286">**update_callback** 更新コールバック。</span><span class="sxs-lookup"><span data-stu-id="1e567-286">**update_callback** The update callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-287">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-287">Return Values</span></span>

<span data-ttu-id="1e567-288">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-288">**NX_SUCCESS** Successful operation.</span></span>
<span data-ttu-id="1e567-289">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-289">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-290">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-290">Allowed From</span></span>

<span data-ttu-id="1e567-291">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-291">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-292">例</span><span class="sxs-lookup"><span data-stu-id="1e567-292">Example</span></span>

```c
/* Create firmware object.  */
status = nx_lwm2m_client_firmware_create(&firmware, &lwm2m_client,     
                                         NX_LWM2M_CLIENT_FIRMWARE_PROTOCOL_HTTP, 
                                         NX_NULL, firmware_packet_uri,
                                         firmware_update);

/* If status is NX_SUCCESS, firmware object was successfully created.  */
```

##  <a name="nx_lwm2m_client_firmware_package_info_set"></a><span data-ttu-id="1e567-293">nx_lwm2m_client_firmware_package_info_set</span><span class="sxs-lookup"><span data-stu-id="1e567-293">nx_lwm2m_client_firmware_package_info_set</span></span>

<span data-ttu-id="1e567-294">LWM2M クライアント ファームウェア パッケージ情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="1e567-294">Sets the LWM2M Client Firmware package information.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-295">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-295">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_package_info_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    const CHAR *name, 
    UINT name_length, 
    const CHAR *version, 
    UINT version_length);
```

### <a name="description"></a><span data-ttu-id="1e567-296">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-296">Description</span></span>

<span data-ttu-id="1e567-297">このサービスは、アプリケーションによって、ファームウェア更新オブジェクトのパッケージ情報リソースを設定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-297">The service is used by the application to set the package information resources of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-298">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-298">Parameters</span></span>

- <span data-ttu-id="1e567-299">**firmware_ptr** LWM2M クライアント ファームウェア オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-299">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="1e567-300">**name** ファームウェア パッケージの名前。</span><span class="sxs-lookup"><span data-stu-id="1e567-300">**name** The name of firmware package.</span></span>
- <span data-ttu-id="1e567-301">**name_length** 名前の長さ。</span><span class="sxs-lookup"><span data-stu-id="1e567-301">**name_length** The length of name.</span></span>
- <span data-ttu-id="1e567-302">**version** ファームウェア パッケージのバージョン。</span><span class="sxs-lookup"><span data-stu-id="1e567-302">**version** The version of firmware package.</span></span>
- <span data-ttu-id="1e567-303">**version_length** バージョンの長さ。</span><span class="sxs-lookup"><span data-stu-id="1e567-303">**version_length** The length of version.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-304">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-304">Return Values</span></span>

- <span data-ttu-id="1e567-305">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-305">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-306">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-306">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-307">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-307">Allowed From</span></span>

<span data-ttu-id="1e567-308">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-308">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-309">例</span><span class="sxs-lookup"><span data-stu-id="1e567-309">Example</span></span>

```c
/* Set the package information resources of the firmware object.  */
status = nx_lwm2m_client_firmware_package_info_set(&firmware, 2m_client,     
                                    “LWM2M Firmware”, sizeof(“LWM2M Firmware”) -1,
                                    “1.0.0.0”, sizeof(“1.0.0.0”) - 1);

/* If status is NX_SUCCESS, package information resources was successfully set. */
```

##  <a name="nx_lwm2m_client_firmware_result_set"></a><span data-ttu-id="1e567-310">nx_lwm2m_client_firmware_result_set</span><span class="sxs-lookup"><span data-stu-id="1e567-310">nx_lwm2m_client_firmware_result_set</span></span>

<span data-ttu-id="1e567-311">ファームウェア更新オブジェクトの更新結果のリソースを設定します。</span><span class="sxs-lookup"><span data-stu-id="1e567-311">Sets the update result resource of the firmware update object.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-312">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-312">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_result_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a><span data-ttu-id="1e567-313">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-313">Description</span></span>

<span data-ttu-id="1e567-314">このサービスは、アプリケーションによって、ファームウェア更新オブジェクトの更新結果リソースを設定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-314">The service is used by the application to set the update result resource of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-315">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-315">Parameters</span></span>

- <span data-ttu-id="1e567-316">**firmware_ptr** LWM2M クライアント ファームウェア オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-316">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="1e567-317">**result** 更新結果。</span><span class="sxs-lookup"><span data-stu-id="1e567-317">**result** The update result.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-318">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-318">Return Values</span></span>

- <span data-ttu-id="1e567-319">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-319">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-320">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-320">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-321">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-321">Allowed From</span></span>

<span data-ttu-id="1e567-322">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-322">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-323">例</span><span class="sxs-lookup"><span data-stu-id="1e567-323">Example</span></span>

```c
/* Set the update result resource of the firmware object.  */
status = nx_lwm2m_client_firmware_result_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_RESULT_SUCCESS);

/* If status is NX_SUCCESS, the update result resource was successfully set.  */
```

##  <a name="nx_lwm2m_client_firmware_state_set"></a><span data-ttu-id="1e567-324">nx_lwm2m_client_firmware_state_set</span><span class="sxs-lookup"><span data-stu-id="1e567-324">nx_lwm2m_client_firmware_state_set</span></span>

<span data-ttu-id="1e567-325">ファームウェア更新オブジェクトの更新結果のリソースを設定します。</span><span class="sxs-lookup"><span data-stu-id="1e567-325">Sets the update result resource of the firmware update object.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-326">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-326">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_state_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a><span data-ttu-id="1e567-327">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-327">Description</span></span>

<span data-ttu-id="1e567-328">このサービスは、アプリケーションによって、ファームウェア更新オブジェクトの状態を設定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-328">The service is used by the application to set the state of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-329">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-329">Parameters</span></span>

- <span data-ttu-id="1e567-330">**firmware_ptr** LWM2M クライアント ファームウェア オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-330">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="1e567-331">**state** ファームウェア オブジェクトの状態。</span><span class="sxs-lookup"><span data-stu-id="1e567-331">**state** The state of the firmware object.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-332">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-332">Return Values</span></span>

- <span data-ttu-id="1e567-333">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-333">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-334">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-334">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-335">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-335">Allowed From</span></span>

<span data-ttu-id="1e567-336">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-336">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-337">例</span><span class="sxs-lookup"><span data-stu-id="1e567-337">Example</span></span>

```c
/* Set the state of the firmware object.  */
status = nx_lwm2m_client_firmware_state_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_STATE_IDLE);

/* If status is NX_SUCCESS, the state was successfully set.  */
```

## <a name="nx_lwm2m_client_lock"></a><span data-ttu-id="1e567-338">nx_lwm2m_client_lock</span><span class="sxs-lookup"><span data-stu-id="1e567-338">nx_lwm2m_client_lock</span></span>

<span data-ttu-id="1e567-339">LWM2M クライアントをロックします。</span><span class="sxs-lookup"><span data-stu-id="1e567-339">Locks the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-340">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-340">Prototype</span></span>

```c
UINT **nx_lwm2m_client_lock**(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-341">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-341">Description</span></span>

<span data-ttu-id="1e567-342">このサービスを使用すると、サーバーまたは別のアプリケーション スレッドからの LWM2M オブジェクトへの同時アクセスを防ぐために、LWM2M クライアントがロックされます。</span><span class="sxs-lookup"><span data-stu-id="1e567-342">This service locks the LWM2M Client to prevent concurrent access to the LWM2M objects from the servers or another application thread.</span></span>

<span data-ttu-id="1e567-343">LWM2M クライアントが現在別のスレッドによってロックされている場合、この関数は LWM2M クライアントがロック解除されるまでブロックします。</span><span class="sxs-lookup"><span data-stu-id="1e567-343">If the LWM2M Client is currently locked by another thread, the function will block until the LWM2M Client is unlocked.</span></span>

<span data-ttu-id="1e567-344">***nx_lwm2m_client_lock** _/_ *_nx_lwm2m_client_unlock_** ペアへの呼び出しは入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="1e567-344">Calls to \***nx_lwm2m_client_lock**_/_*_nx_lwm2m_client_unlock_*\* pairs can be nested.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-345">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-345">Parameters</span></span>

- <span data-ttu-id="1e567-346">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-346">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-347">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-347">Return Values</span></span>

- <span data-ttu-id="1e567-348">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-348">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-349">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-349">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-350">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-350">Allowed From</span></span>

<span data-ttu-id="1e567-351">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-351">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-352">例</span><span class="sxs-lookup"><span data-stu-id="1e567-352">Example</span></span>

```c
/* Lock the LWM2M client.  */
status = nx_lwm2m_client_lock(&lwm2m_client);

/* If status is NX_SUCCESS, lwm2m client was successfully locked.  */
```

## <a name="nx_lwm2m_client_object_add"></a><span data-ttu-id="1e567-353">nx_lwm2m_client_object_add</span><span class="sxs-lookup"><span data-stu-id="1e567-353">nx_lwm2m_client_object_add</span></span>

<span data-ttu-id="1e567-354">オブジェクトの実装を LWM2M クライアントに追加します。</span><span class="sxs-lookup"><span data-stu-id="1e567-354">Adds an Object implementation to the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-355">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-355">Prototype</span></span>

```c
UINT **nx_lwm2m_client_object_add**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK object_operation);
```

### <a name="description"></a><span data-ttu-id="1e567-356">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-356">Description</span></span>

<span data-ttu-id="1e567-357">このサービスを使用すると、新しいオブジェクトの実装が LWM2M クライアントに追加されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-357">This service adds a new Object implementation to the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-358">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-358">Parameters</span></span>

- <span data-ttu-id="1e567-359">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-359">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="1e567-360">**object_ptr** オブジェクトの実装を定義する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-360">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="1e567-361">**object_id** オブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-361">**object_id** The object id.</span></span>
- <span data-ttu-id="1e567-362">**object_operation** オブジェクト操作のコールバック関数。</span><span class="sxs-lookup"><span data-stu-id="1e567-362">**object_operation** The object operation callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-363">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-363">Return Values</span></span>

- <span data-ttu-id="1e567-364">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-364">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-365">**NX_LWM2M_CLIENT_ALREADY_EXIST** オブジェクト ID は既に存在しています。</span><span class="sxs-lookup"><span data-stu-id="1e567-365">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="1e567-366">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-366">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-367">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-367">Allowed From</span></span>

<span data-ttu-id="1e567-368">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-368">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-369">例</span><span class="sxs-lookup"><span data-stu-id="1e567-369">Example</span></span>

```c
/* Add new object to the lwm2m client.  */
status = nx_lwm2m_client_object_add(&lwm2m_client, &object, 
                                    3303, object_operation);

/* If status is NX_SUCCESS, the new object was successfully added.  */
```

## <a name="nx_lwm2m_client_object_create"></a><span data-ttu-id="1e567-370">nx_lwm2m_client_object_create</span><span class="sxs-lookup"><span data-stu-id="1e567-370">nx_lwm2m_client_object_create</span></span>

<span data-ttu-id="1e567-371">新しいオブジェクト インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1e567-371">Creates a new Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-372">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-372">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_create(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-373">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-373">Description</span></span>

<span data-ttu-id="1e567-374">このサービスを使用すると、LWM2M クライアントのオブジェクトに対して "作成" 操作を実行して、新しいオブジェクト インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-374">This service performs a ‘Create’ operation on an Object of the LWM2M Client to create a new Object Instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-375">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-375">Parameters</span></span>

- <span data-ttu-id="1e567-376">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-376">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="1e567-377">**object_id** オブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-377">**object_id** The Object ID.</span></span>
- <span data-ttu-id="1e567-378">**instance_id_ptr** 新しいインスタンスの ID へのポインター。LWM2M クライアントによってインスタンス ID を割り当てる必要がある場合は、**NULL** にすることができます。</span><span class="sxs-lookup"><span data-stu-id="1e567-378">**instance_id_ptr** Pointer to the ID of the new instance, can be **NULL** if the LWM2M Client must assign an Instance ID.</span></span> <span data-ttu-id="1e567-379">ID が予約値 65535 の場合、LWM2M クライアントによってインスタンス ID が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="1e567-379">If the ID is the reserved value 65535 the LWM2M Client will assign an Instance ID.</span></span> <span data-ttu-id="1e567-380">NULL 以外の場合は、割り当てられた ID が呼び出しの後に返されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-380">If not NULL the assigned ID is returned after the call.</span></span>
- <span data-ttu-id="1e567-381">**num_values** 設定する値の数。</span><span class="sxs-lookup"><span data-stu-id="1e567-381">**num_values** The number of values to set.</span></span>
- <span data-ttu-id="1e567-382">**values_ptr** 新しいオブジェクト インスタンスを初期化するためのリソース値の配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-382">**values_ptr** Pointer to an array of resource values to initialize the new Object Instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-383">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-383">Return Values</span></span>

- <span data-ttu-id="1e567-384">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-384">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-385">**NX_LWM2M_CLIENT_ALREADY_EXIST** オブジェクト インスタンス ID は既に存在しています。</span><span class="sxs-lookup"><span data-stu-id="1e567-385">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object Instance ID already exists.</span></span>
- <span data-ttu-id="1e567-386">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** オブジェクトはインスタンスの作成をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1e567-386">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** The Object doesn’t support instance creation.</span></span>
- <span data-ttu-id="1e567-387">**NX_LWM2M_CLIENT_NO_MEMORY** 新しいインスタンスを格納するためのメモリを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="1e567-387">**NX_LWM2M_CLIENT_NO_MEMORY** Cannot allocate memory to store the new instance.</span></span>
- <span data-ttu-id="1e567-388">**NX_LWM2M_CLIENT_NOT_FOUND** オブジェクト ID が存在していません。</span><span class="sxs-lookup"><span data-stu-id="1e567-388">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID doesn’t exist.</span></span>
- <span data-ttu-id="1e567-389">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-389">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-390">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-390">Allowed From</span></span>

<span data-ttu-id="1e567-391">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-391">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-392">例</span><span class="sxs-lookup"><span data-stu-id="1e567-392">Example</span></span>

```c
/* Create new object instance.  */
status = nx_lwm2m_client_object_create(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, a new object instance was successfully created.  */
```

## <a name="nx_lwm2m_client_object_delete"></a><span data-ttu-id="1e567-393">nx_lwm2m_client_object_delete</span><span class="sxs-lookup"><span data-stu-id="1e567-393">nx_lwm2m_client_object_delete</span></span>

<span data-ttu-id="1e567-394">オブジェクト インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="1e567-394">Deletes an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-395">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-395">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_delete(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="1e567-396">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-396">Description</span></span>

<span data-ttu-id="1e567-397">このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンスの "削除" 操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-397">This service performs a ‘Delete’ operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-398">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-398">Parameters</span></span>

- <span data-ttu-id="1e567-399">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-399">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="1e567-400">**object_id** オブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-400">**object_id** The Object ID.</span></span>
- <span data-ttu-id="1e567-401">**instance_id** オブジェクト インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-401">**instance_id** The Object Instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-402">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-402">Return Values</span></span>

- <span data-ttu-id="1e567-403">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-403">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-404">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** オブジェクトはインスタンスの削除をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1e567-404">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** The Object doesn’t support instance deletion.</span></span>
- <span data-ttu-id="1e567-405">**NX_LWM2M_CLIENT_NOT_FOUND** オブジェクト ID またはオブジェクト インスタンス ID が存在していません。</span><span class="sxs-lookup"><span data-stu-id="1e567-405">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="1e567-406">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-406">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-407">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-407">Allowed From</span></span>

<span data-ttu-id="1e567-408">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-408">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-409">例</span><span class="sxs-lookup"><span data-stu-id="1e567-409">Example</span></span>

```c
/* Delete an object instance.  */
status = nx_lwm2m_client_object_delete(&lwm2m_client, 3303, 0);

/* If status is NX_SUCCESS, an object instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_object_discover"></a><span data-ttu-id="1e567-410">nx_lwm2m_client_object_discover</span><span class="sxs-lookup"><span data-stu-id="1e567-410">nx_lwm2m_client_object_discover</span></span>

<span data-ttu-id="1e567-411">オブジェクト インスタンスのリソースを検出します。</span><span class="sxs-lookup"><span data-stu-id="1e567-411">Discovers resources of an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-412">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-412">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_discover(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT *num_resources,
    NX_LWM2M_CLIENT_RESOURCE *resources);

```

### <a name="description"></a><span data-ttu-id="1e567-413">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-413">Description</span></span>

<span data-ttu-id="1e567-414">このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンスの "検出" 操作が実行されます。これにより、オブジェクトによって実装されたリソースのリストが返されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-414">This service performs a ‘Discover’ operation on an Object Instance of the LWM2M Client, this returns the list of resources implemented by the Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-415">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-415">Parameters</span></span>

- <span data-ttu-id="1e567-416">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-416">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="1e567-417">**object_id** オブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-417">**object_id** The Object ID.</span></span>
- <span data-ttu-id="1e567-418">**instance_id** オブジェクト インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-418">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="1e567-419">**num_resources_ptr**: 入力時は宛先バッファーのサイズ、出力時はバッファーに書き込まれた要素の数。</span><span class="sxs-lookup"><span data-stu-id="1e567-419">**num_resources** On input the size of the destination buffer, on output the number of elements written to the buffer.</span></span>
- <span data-ttu-id="1e567-420">**resources_ptr**: 宛先バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-420">**resources** Pointer to the destination buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-421">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-421">Return Values</span></span>

- <span data-ttu-id="1e567-422">*NX_SUCCESS*\* 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-422">*NX_SUCCESS*\* Successful operation.</span></span>
- <span data-ttu-id="1e567-423">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** リソース バッファーが小さすぎて、リソースのリストを格納できません。</span><span class="sxs-lookup"><span data-stu-id="1e567-423">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="1e567-424">**NX_LWM2M_CLIENT_NOT_FOUND** オブジェクト ID またはオブジェクト インスタンス ID が存在していません。</span><span class="sxs-lookup"><span data-stu-id="1e567-424">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="1e567-425">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-425">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-426">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-426">Allowed From</span></span>

<span data-ttu-id="1e567-427">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-427">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-428">例</span><span class="sxs-lookup"><span data-stu-id="1e567-428">Example</span></span>

```c
NX_LWM2M_CLIENT_RESOURCE resources[10]
UINT num_resources = 10;

/* Discover object resources.  */
status = nx_lwm2m_client_object_discover(&lwm2m_client, 3303, 0, 
                                         &num_resources, resource);

/* If status is NX_SUCCESS, discover object resources successfully.  */
```

## <a name="nx_lwm2m_client_object_execute"></a><span data-ttu-id="1e567-429">nx_lwm2m_client_object_execute</span><span class="sxs-lookup"><span data-stu-id="1e567-429">nx_lwm2m_client_object_execute</span></span>

<span data-ttu-id="1e567-430">オブジェクト インスタンスのリソースに対して "実行" 操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="1e567-430">Performs an 'Execute' operation on a resource of an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-431">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-431">Prototype</span></span>

```C
UINT **nx_lwm2m_client_object_execute**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr,
    UINT arguments_length);
```

### <a name="description"></a><span data-ttu-id="1e567-432">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-432">Description</span></span>

<span data-ttu-id="1e567-433">このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンス リソースの "実行" 操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-433">This service performs the ‘Execute’ operation on an Object Instance Resource of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-434">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-434">Parameters</span></span>

- <span data-ttu-id="1e567-435">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-435">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="1e567-436">**object_id** オブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-436">**object_id** The Object ID.</span></span>
- <span data-ttu-id="1e567-437">**instance_id** オブジェクト インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-437">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="1e567-438">**resource_id**: リソース ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-438">**resource_id** The Resource ID.</span></span>
- <span data-ttu-id="1e567-439">**arguments_ptr**: 実行操作の引数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-439">**arguments_ptr** Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="1e567-440">arguments_length が 0 の場合は、NULL を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1e567-440">Can be NULL if arguments_length is zero.</span></span>
- <span data-ttu-id="1e567-441">**arguments_length**: 引数の長さ。</span><span class="sxs-lookup"><span data-stu-id="1e567-441">**arguments_length** The length of the arguments.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-442">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-442">Return Values</span></span>

- <span data-ttu-id="1e567-443">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-443">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-444">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** リソース バッファーが小さすぎて、リソースのリストを格納できません。</span><span class="sxs-lookup"><span data-stu-id="1e567-444">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="1e567-445">**NX_LWM2M_CLIENT_NOT_FOUND** オブジェクト ID またはオブジェクト インスタンス ID が存在していません。</span><span class="sxs-lookup"><span data-stu-id="1e567-445">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="1e567-446">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-446">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-447">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-447">Allowed From</span></span>

<span data-ttu-id="1e567-448">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-448">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-449">例</span><span class="sxs-lookup"><span data-stu-id="1e567-449">Example</span></span>

```c
/* Execute object resource.  */
status = nx_lwm2m_client_object_execute (&lwm2m_client, 3303, 0, 0,  
                                         “5”, 1);

/* If status is NX_SUCCESS, an object resource was successfully executed.  */
```

## <a name="nx_lwm2m_client_object_instance_add"></a><span data-ttu-id="1e567-450">nx_lwm2m_client_object_instance_add</span><span class="sxs-lookup"><span data-stu-id="1e567-450">nx_lwm2m_client_object_instance_add</span></span>

<span data-ttu-id="1e567-451">オブジェクト インスタンスの実装をオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="1e567-451">Adds an Object instance implementation to an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-452">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-452">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_add(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-453">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-453">Description</span></span>

<span data-ttu-id="1e567-454">このサービスを使用すると、新しいオブジェクト インスタンスの実装が LWM2M クライアントに追加されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-454">This service adds a new Object instance implementation to the LWM2M Client.</span></span> <span data-ttu-id="1e567-455">instance_id_ptr の値が **NX_LWM2M_CLIENT_RESERVED_ID** である場合は、LWM2M クライアントによって未使用のインスタンス ID が自動的に割り当てられ、それ以外の場合、LWM2M クライアントではアプリケーションで設定された値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-455">If the value of instance_id_ptr is **NX_LWM2M_CLIENT_RESERVED_ID**, LWM2M Client will automatically assign an unused instance id, otherwise, LWM2M Client will use the value application set.</span></span> <span data-ttu-id="1e567-456">新しいインスタンスが正常に追加されると、instance_id が instance_id_ptr に入力され、アプリケーションに戻されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-456">Once new instance was added successfully, the instance_id will be filled in instance_id_ptr to return to application.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-457">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-457">Parameters</span></span>

- <span data-ttu-id="1e567-458">**object_ptr** オブジェクトの実装を定義する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-458">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="1e567-459">**instance_ptr** オブジェクト インスタンスの実装を定義する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-459">**instance_ptr** Pointer to the structure defining the Object instance implementation.</span></span>
- <span data-ttu-id="1e567-460">**instance_id_ptr** オブジェクト インスタンス ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-460">**instance_id_ptr** Pointer to the object instance id.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-461">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-461">Return Values</span></span>

- <span data-ttu-id="1e567-462">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-462">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-463">**NX_LWM2M_CLIENT_ALREADY_EXIST** オブジェクト ID は既に存在しています。</span><span class="sxs-lookup"><span data-stu-id="1e567-463">**NX_CLIENT_LWM2M_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="1e567-464">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-464">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-465">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-465">Allowed From</span></span>

<span data-ttu-id="1e567-466">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-466">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-467">例</span><span class="sxs-lookup"><span data-stu-id="1e567-467">Example</span></span>

```c
/* Add new object instance to the object.  */
status = nx_lwm2m_client_object_instance_add(&object, &object_instance,
                                             &instance_id);

/* If status is NX_SUCCESS, the new object instance was successfully added.  */
```

## <a name="nx_lwm2m_client_object_instance_next_get"></a><span data-ttu-id="1e567-468">nx_lwm2m_client_object_instance_next_get</span><span class="sxs-lookup"><span data-stu-id="1e567-468">nx_lwm2m_client_object_instance_next_get</span></span>

<span data-ttu-id="1e567-469">オブジェクトの次のインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="1e567-469">Gets the next instance of an Object.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-470">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-470">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-471">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-471">Description</span></span>

<span data-ttu-id="1e567-472">このサービスを使用すると、指定されたオブジェクトの次のオブジェクト インスタンスの ID が返されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-472">This service returns the ID of the next Object Instance of the given Object.</span></span> <span data-ttu-id="1e567-473">現在のインスタンス ID が NX_LWM2M_RESERVED_ID (65535) に設定されている場合は、最初のインスタンスの ID が返されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-473">If the current Instance ID is set to NX_LWM2M_RESERVED_ID (65535) the ID of the first instance is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-474">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-474">Parameters</span></span>

- <span data-ttu-id="1e567-475">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-475">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="1e567-476">**object_id** オブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-476">**object_id** The Object ID.</span></span>
- <span data-ttu-id="1e567-477">**instance_id_ptr** 現在のオブジェクト インスタンス ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-477">**instance_id_ptr** Pointer to the current Object Instance ID.</span></span> <span data-ttu-id="1e567-478">戻り値には、オブジェクトの次のインスタンス ID が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1e567-478">On return contains the next Instance ID of the Object.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-479">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-479">Return Values</span></span>

- <span data-ttu-id="1e567-480">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-480">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-481">**NX_CLIENT_LWM2M_NOT_FOUND** 指定されたインスタンス ID がオブジェクトの最後か、オブジェクト ID が実装されていません。</span><span class="sxs-lookup"><span data-stu-id="1e567-481">**NX_CLIENT_LWM2M_NOT_FOUND** The given Instance ID is the last of the object, or the Object ID is not implemented.</span></span>
- <span data-ttu-id="1e567-482">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-482">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-483">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-483">Allowed From</span></span>

<span data-ttu-id="1e567-484">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-484">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-485">例</span><span class="sxs-lookup"><span data-stu-id="1e567-485">Example</span></span>

```c
/* Get the next instance of an object.  */
status = nx_lwm2m_client_object_instance_next_get(&lwm2m_client, 3303, 
                                                  &instance_id);

/* If status is NX_SUCCESS, get the next instance successfully.  */
```

## <a name="nx_lwm2m_client_object_instance_remove"></a><span data-ttu-id="1e567-486">nx_lwm2m_client_object_instance_remove</span><span class="sxs-lookup"><span data-stu-id="1e567-486">nx_lwm2m_client_object_instance_remove</span></span>

<span data-ttu-id="1e567-487">オブジェクトからオブジェクト インスタンスの実装を削除します。</span><span class="sxs-lookup"><span data-stu-id="1e567-487">Removes an  Object instance implementation from an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-488">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-488">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_remove(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-489">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-489">Description</span></span>

<span data-ttu-id="1e567-490">このサービスを使用すると、オブジェクトからオブジェクト インスタンスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-490">This service removes an Object instance from an object.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-491">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-491">Parameters</span></span>

- <span data-ttu-id="1e567-492">***object_ptr*** オブジェクトの実装を定義する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-492">***object_ptr*** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="1e567-493">**instance_ptr** オブジェクト インスタンスの実装を定義する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-493">**instance_ptr** Pointer to the structure defining the Object instance implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-494">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-494">Return Values</span></span>

- <span data-ttu-id="1e567-495">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-495">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-496">**NX_LWM2M_CLIENT_ALREADY_EXIST** オブジェクト ID は既に存在しています。</span><span class="sxs-lookup"><span data-stu-id="1e567-496">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="1e567-497">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-497">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-498">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-498">Allowed From</span></span>

<span data-ttu-id="1e567-499">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-499">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-500">例</span><span class="sxs-lookup"><span data-stu-id="1e567-500">Example</span></span>

```c
/* Remove object instance from an object.  */
status = nx_lwm2m_client_object_instance_remove(&object, &object_instance);

/* If status is NX_SUCCESS, the object instance was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_next_get"></a><span data-ttu-id="1e567-501">nx_lwm2m_client_object_next_get</span><span class="sxs-lookup"><span data-stu-id="1e567-501">nx_lwm2m_client_object_next_get</span></span>

<span data-ttu-id="1e567-502">LWM2M クライアントの次のオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="1e567-502">Gets the next object of the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-503">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-503">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID \*object_id_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-504">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-504">Description</span></span>

<span data-ttu-id="1e567-505">このサービスを使用すると、LWM2M クライアントによって実装される次のオブジェクトの ID が返されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-505">This service returns the ID of the next Object implemented by the LWM2M Client.</span></span> <span data-ttu-id="1e567-506">現在のオブジェクト ID が NX_LWM2M_RESERVED_ID (65535) に設定されている場合、最初のオブジェクト ID が返されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-506">If the current Object ID is set to NX_LWM2M_RESERVED_ID (65535) the first Object ID is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-507">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-507">Parameters</span></span>

- <span data-ttu-id="1e567-508">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-508">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="1e567-509">**object_id_ptr** 現在のオブジェクト ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-509">**object_id_ptr** Pointer to the current Object ID.</span></span> <span data-ttu-id="1e567-510">戻り値には、LWM2M クライアントによって実装される次のオブジェクト ID が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1e567-510">On return contains the next Object ID implemented by the LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-511">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-511">Return Values</span></span>

- <span data-ttu-id="1e567-512">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-512">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-513">**NX_LWM2M_CLIENT_NOT_FOUND** 指定されたオブジェクト ID は、データベースの最後です。</span><span class="sxs-lookup"><span data-stu-id="1e567-513">**NX_LWM2M_CLIENT_NOT_FOUND** The given Object ID is the last of the database.</span></span>
<span data-ttu-id="1e567-514">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-514">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-515">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-515">Allowed From</span></span>

<span data-ttu-id="1e567-516">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-516">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-517">例</span><span class="sxs-lookup"><span data-stu-id="1e567-517">Example</span></span>

```c
/* Get the next object of lwm2m client.  */
status = nx_lwm2m_client_object_next_get(&lwm2m_client, &object_id);

/* If status is NX_SUCCESS, get the next object successfully.  */
```

## <a name="nx_lwm2m_client_object_read"></a><span data-ttu-id="1e567-518">nx_lwm2m_client_object_read</span><span class="sxs-lookup"><span data-stu-id="1e567-518">nx_lwm2m_client_object_read</span></span>

<span data-ttu-id="1e567-519">オブジェクト インスタンスのリソースの値を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="1e567-519">Reads an Object Instance's resource's values.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-520">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-520">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_read(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a><span data-ttu-id="1e567-521">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-521">Description</span></span>

<span data-ttu-id="1e567-522">このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンスの "読み取り" 操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-522">This service performs a ‘Read’ operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-523">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-523">Parameters</span></span>

- <span data-ttu-id="1e567-524">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-524">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="1e567-525">**object_id** オブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-525">**object_id** The Object ID.</span></span>
- <span data-ttu-id="1e567-526">**instance_id** オブジェクト インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-526">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="1e567-527">**num_values** 読み取るリソースの数。</span><span class="sxs-lookup"><span data-stu-id="1e567-527">**num_values** The number of resources to read.</span></span>
- <span data-ttu-id="1e567-528">**values_ptr** 読み取るリソースの ID を格納する NX_LWM2M_RESOURCE の配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-528">**values_ptr** Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="1e567-529">返されると、配列に対応する型と値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-529">On return the array is filled with the corresponding types and values.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-530">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-530">Return Values</span></span>

- <span data-ttu-id="1e567-531">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-531">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-532">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** リソースで読み取り操作がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1e567-532">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** A resource doesn’t support the read operation.</span></span>
- <span data-ttu-id="1e567-533">**NX_LWM2M_CLIENT_NOT_FOUND** オブジェクト ID、オブジェクト インスタンス ID、またはリソース ID が存在していません。</span><span class="sxs-lookup"><span data-stu-id="1e567-533">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID, Object Instance ID or a resource ID doesn’t exist.</span></span>
- <span data-ttu-id="1e567-534">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-534">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-535">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-535">Allowed From</span></span>

<span data-ttu-id="1e567-536">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-536">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-537">例</span><span class="sxs-lookup"><span data-stu-id="1e567-537">Example</span></span>

```c
/* Read the object resources.  */
status = nx_lwm2m_client_object_read(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, the resources were successfully read.  */
```

## <a name="nx_lwm2m_client_object_remove"></a><span data-ttu-id="1e567-538">nx_lwm2m_client_object_remove</span><span class="sxs-lookup"><span data-stu-id="1e567-538">nx_lwm2m_client_object_remove</span></span>

<span data-ttu-id="1e567-539">オブジェクトからオブジェクト インスタンスの実装を削除します。</span><span class="sxs-lookup"><span data-stu-id="1e567-539">Removes an Object instance implementation from an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-540">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-540">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_remove(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-541">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-541">Description</span></span>

<span data-ttu-id="1e567-542">このサービスを使用すると、LWM2M クライアントからオブジェクトが削除されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-542">This service removes an Object from the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-543">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-543">Parameters</span></span>

- <span data-ttu-id="1e567-544">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-544">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="1e567-545">**object_ptr** オブジェクトの実装を定義する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-545">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-546">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-546">Return Values</span></span>

- <span data-ttu-id="1e567-547">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-547">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-548">**NX_LWM2M_CLIENT_ALREADY_EXIST** オブジェクト ID は既に存在しています。</span><span class="sxs-lookup"><span data-stu-id="1e567-548">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="1e567-549">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-549">**NX_PTR_ERROR** Invalid pointer.</span></span>
- <span data-ttu-id="1e567-550">**NX_LWM2M_CLIENT_FORBIDDEN** 内部オブジェクトの削除は禁止されています。</span><span class="sxs-lookup"><span data-stu-id="1e567-550">**NX_LWM2M_CLIENT_FORBIDDEN** Removing internal object is forbidden.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-551">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-551">Allowed From</span></span>

<span data-ttu-id="1e567-552">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-552">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-553">例</span><span class="sxs-lookup"><span data-stu-id="1e567-553">Example</span></span>

```c
/* Remove object from lwm2m client.  */
status = nx_lwm2m_client_object_remove(&lwm2m_client, &object);

/* If status is NX_SUCCESS, the object was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_resource_changed"></a><span data-ttu-id="1e567-554">nx_lwm2m_client_object_resource_changed</span><span class="sxs-lookup"><span data-stu-id="1e567-554">nx_lwm2m_client_object_resource_changed</span></span>

<span data-ttu-id="1e567-555">オブジェクト リソースの変更を通知します。</span><span class="sxs-lookup"><span data-stu-id="1e567-555">Signals a change of an Object resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-556">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-556">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_resource_changed(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="1e567-557">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-557">Description</span></span>

<span data-ttu-id="1e567-558">このサービスは、アプリケーションによって、オブジェクトのリソースが変更されたことを LWM2M クライアントに通知するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-558">The service is used by the application to signal to the LWM2M Client that a resource of the Object has changed.</span></span> <span data-ttu-id="1e567-559">LWM2M クライアントは、リソースが LWM2M サーバーによって監視されている場合に通知を送信します。</span><span class="sxs-lookup"><span data-stu-id="1e567-559">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-560">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-560">Parameters</span></span>

- <span data-ttu-id="1e567-561">**object_ptr** オブジェクトの実装を定義する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-561">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="1e567-562">***instance_ptr*** オブジェクト インスタンスの実装を定義する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-562">***instance_ptr*** Pointer to the structure defining the Object instance implementation.</span></span>
- <span data-ttu-id="1e567-563">**resource** 変更されたリソースを記述する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-563">**resource** Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-564">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-564">Return Values</span></span>

- <span data-ttu-id="1e567-565">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-565">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-566">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-566">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-567">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-567">Allowed From</span></span>

<span data-ttu-id="1e567-568">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-568">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-569">例</span><span class="sxs-lookup"><span data-stu-id="1e567-569">Example</span></span>

```c
/* Change object resource.  */
status = nx_lwm2m_client_object_resource_changed(&object, &instance, &resource);

/* If status is NX_SUCCESS, a resource was successfully changed.  */
```

## <a name="nx_lwm2m_client_object_write"></a><span data-ttu-id="1e567-570">nx_lwm2m_client_object_write</span><span class="sxs-lookup"><span data-stu-id="1e567-570">nx_lwm2m_client_object_write</span></span>

<span data-ttu-id="1e567-571">オブジェクト インスタンスのリソースの値を変更します。</span><span class="sxs-lookup"><span data-stu-id="1e567-571">Changes resource's values of an Object instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-572">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-572">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_write(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr,
    UINT write_op);
```

### <a name="description"></a><span data-ttu-id="1e567-573">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-573">Description</span></span>

<span data-ttu-id="1e567-574">このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンスの "書き込み" 操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-574">This service performs a ‘Write’ operation on an Object Instance of the LWM2M Client.</span></span>

<span data-ttu-id="1e567-575">*write_op* パラメーターには、次の書き込み操作を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1e567-575">The following write operations can be specified to the *write_op* parameter.</span></span>

| <span data-ttu-id="1e567-576">値</span><span class="sxs-lookup"><span data-stu-id="1e567-576">Value</span></span> | <span data-ttu-id="1e567-577">書き込み&nbsp;操作</span><span class="sxs-lookup"><span data-stu-id="1e567-577">Write&nbsp;Operation</span></span> | <span data-ttu-id="1e567-578">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-578">Description</span></span> |
| --- | ---| --- |
| <span data-ttu-id="1e567-579">0</span><span class="sxs-lookup"><span data-stu-id="1e567-579">0</span></span> | <span data-ttu-id="1e567-580">部分更新</span><span class="sxs-lookup"><span data-stu-id="1e567-580">Partial Update</span></span> | <span data-ttu-id="1e567-581">新しい値で提供されるリソースを追加または更新し、他の既存のリソースを変更せずにそのままにします。</span><span class="sxs-lookup"><span data-stu-id="1e567-581">Adds or updates Resources provided in the new value and leaves other existing Resources unchanged.</span></span> |
| <span data-ttu-id="1e567-582">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span><span class="sxs-lookup"><span data-stu-id="1e567-582">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span></span> | <span data-ttu-id="1e567-583">インスタンスの置換</span><span class="sxs-lookup"><span data-stu-id="1e567-583">Replace Instance</span></span> | <span data-ttu-id="1e567-584">オブジェクト インスタンスを、提供された新しいリソース値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1e567-584">Replaces the Object Instance with the new provided resource values.</span></span> |
| <span data-ttu-id="1e567-585">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span><span class="sxs-lookup"><span data-stu-id="1e567-585">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span></span> | <span data-ttu-id="1e567-586">リソースの置換</span><span class="sxs-lookup"><span data-stu-id="1e567-586">Replace Resource</span></span> | <span data-ttu-id="1e567-587">リソースを、提供された新しいリソース値に置き換えます (複数のリソースを置き換えるために使用されます)。</span><span class="sxs-lookup"><span data-stu-id="1e567-587">Replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span> |
| <span data-ttu-id="1e567-588">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span><span class="sxs-lookup"><span data-stu-id="1e567-588">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span></span> | <span data-ttu-id="1e567-589">ブートストラップ書き込み</span><span class="sxs-lookup"><span data-stu-id="1e567-589">Bootstrap Write</span></span> | <span data-ttu-id="1e567-590">ブートストラップ シーケンスからの呼び出しを示します。</span><span class="sxs-lookup"><span data-stu-id="1e567-590">Indicates a call from a Bootstrap sequence.</span></span> |

### <a name="parameters"></a><span data-ttu-id="1e567-591">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-591">Parameters</span></span>

- <span data-ttu-id="1e567-592">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-592">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="1e567-593">**object_id** オブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-593">**object_id** The Object ID.</span></span>
- <span data-ttu-id="1e567-594">**instance_id** オブジェクト インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-594">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="1e567-595">**num_values**: 書き込むリソースの数。</span><span class="sxs-lookup"><span data-stu-id="1e567-595">**num_values** The number of resources to write.</span></span>
- <span data-ttu-id="1e567-596">**values_ptr** リソースの ID、および書き込む型と値を格納する NX_LWM2M_RESOURCE の配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-596">**values_ptr** Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources, the types and the values to write.</span></span>
- <span data-ttu-id="1e567-597">**write_op**: 書き込み操作の種類。</span><span class="sxs-lookup"><span data-stu-id="1e567-597">**write_op** The type of write operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-598">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-598">Return Values</span></span>

- <span data-ttu-id="1e567-599">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-599">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-600">**NX_LWM2M_CLIENT_BAD_ENCODING** リソースの型が無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-600">**NX_LWM2M_CLIENT_BAD_ENCODING** The type of a resource is not valid.</span></span>
- <span data-ttu-id="1e567-601">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** 値の長さが大きすぎてインスタンスに格納できません。</span><span class="sxs-lookup"><span data-stu-id="1e567-601">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The length of a value is too big to be stored in the instance.</span></span>
- <span data-ttu-id="1e567-602">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** リソースが読み書き込み操作をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1e567-602">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** A resource doesn’t support the write operation.</span></span>
- <span data-ttu-id="1e567-603">**NX_LWM2M_CLIENT_NO_MEMORY** リソース値を格納するためのメモリを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="1e567-603">**NX_LWM2M_CLIENT_NO_MEMORY** Cannot allocate memory to store a resource value.</span></span>
- <span data-ttu-id="1e567-604">**NX_LWM2M_CLIENT_NOT_ACCEPTABLE** リソースの値が無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-604">**NX_LWM2M_CLIENT_NOT_ACCEPTABLE** The value of a resource is not valid.</span></span>
- <span data-ttu-id="1e567-605">**NX_LWM2M_CLIENT_NOT_FOUND** オブジェクト ID、オブジェクト インスタンス ID、またはリソース ID が存在していません。</span><span class="sxs-lookup"><span data-stu-id="1e567-605">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID, Object Instance ID or a resource ID doesn’t exist.</span></span>
- <span data-ttu-id="1e567-606">**NX_OPTION_ERROR** 書き込み操作の種類が無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-606">**NX_OPTION_ERROR** Invalid type of write operation.</span></span> 
- <span data-ttu-id="1e567-607">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-607">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-608">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-608">Allowed From</span></span>

<span data-ttu-id="1e567-609">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-609">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-610">例</span><span class="sxs-lookup"><span data-stu-id="1e567-610">Example</span></span>

```c
/* Write object resources.  */
status = nx_lwm2m_client_object_write(&lwm2m_client, 3303, 0, 2, &resource,
                                      NX_LWM2M_CLIENT_OBJECT_WRITE_UPDATE);

/* If status is NX_SUCCESS, write object resources successfully.  */
```

## <a name="nx_lwm2m_client_resource_boolean_get"></a><span data-ttu-id="1e567-611">nx_lwm2m_client_resource_boolean_get</span><span class="sxs-lookup"><span data-stu-id="1e567-611">nx_lwm2m_client_resource_boolean_get</span></span>

<span data-ttu-id="1e567-612">ブール値リソースの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="1e567-612">Gets the value of a Boolean Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-613">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-613">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_boolean_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-614">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-614">Description</span></span>

<span data-ttu-id="1e567-615">このサービスを使用するとブール値リソースの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-615">The service retrieves the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-616">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-616">Parameters</span></span>

- <span data-ttu-id="1e567-617">**リソース** リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-617">**resource** Pointer to Resource value description.</span></span>
- <span data-ttu-id="1e567-618">**bool_ptr** 宛先のブール値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-618">**bool_ptr** Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-619">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-619">Return Values</span></span>

- <span data-ttu-id="1e567-620">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-620">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-621">**NX_LWM2M_CLIENT_BAD_ENCODING** リソース値がブール値ではありません。</span><span class="sxs-lookup"><span data-stu-id="1e567-621">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="1e567-622">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-622">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-623">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-623">Allowed From</span></span>

<span data-ttu-id="1e567-624">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-624">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-625">例</span><span class="sxs-lookup"><span data-stu-id="1e567-625">Example</span></span>

```c
/* Get the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_get(&resource, &bool);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_boolean_set"></a><span data-ttu-id="1e567-626">nx_lwm2m_client_resource_boolean_set</span><span class="sxs-lookup"><span data-stu-id="1e567-626">nx_lwm2m_client_resource_boolean_set</span></span>

<span data-ttu-id="1e567-627">ブール値リソースの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="1e567-627">Sets the value of a Boolean Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-628">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-628">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_boolean_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL bool_data);
```

### <a name="description"></a><span data-ttu-id="1e567-629">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-629">Description</span></span>

<span data-ttu-id="1e567-630">このサービスを使用するとブール値リソースの値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-630">The service sets the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-631">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-631">Parameters</span></span>

- <span data-ttu-id="1e567-632">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-632">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-633">**bool_data** ブール値のデータ。</span><span class="sxs-lookup"><span data-stu-id="1e567-633">**bool_data** Boolean data.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-634">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-634">Return Values</span></span>

- <span data-ttu-id="1e567-635">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-635">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-636">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-636">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-637">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-637">Allowed From</span></span>

<span data-ttu-id="1e567-638">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-638">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-639">例</span><span class="sxs-lookup"><span data-stu-id="1e567-639">Example</span></span>

```c
/* Set the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_set(&resource, NX_TRUE);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_dim_get"></a><span data-ttu-id="1e567-640">nx_lwm2m_client_resource_dim_get</span><span class="sxs-lookup"><span data-stu-id="1e567-640">nx_lwm2m_client_resource_dim_get</span></span>

<span data-ttu-id="1e567-641">複数のリソースのリソース ディメンションを取得します</span><span class="sxs-lookup"><span data-stu-id="1e567-641">Gets the resource dimension for multiple Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-642">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-642">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_dim_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    UCHAR *dim);
```

### <a name="description"></a><span data-ttu-id="1e567-643">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-643">Description</span></span>

<span data-ttu-id="1e567-644">このサービスを使用すると、複数のリソースのリソース ディメンションが取得されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-644">The service retrieves the resource dimension for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-645">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-645">Parameters</span></span>

- <span data-ttu-id="1e567-646">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-646">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-647">**dim** 宛先のディメンションへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-647">**dim** Pointer to the destination dimension.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-648">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-648">Return Values</span></span>

- <span data-ttu-id="1e567-649">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-649">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-650">**NX_LWM2M_CLIENT_BAD_ENCODING** リソース値がブール値ではありません。</span><span class="sxs-lookup"><span data-stu-id="1e567-650">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="1e567-651">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-651">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-652">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-652">Allowed From</span></span>

<span data-ttu-id="1e567-653">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-653">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-654">例</span><span class="sxs-lookup"><span data-stu-id="1e567-654">Example</span></span>

```c
/* Get the resource dimension for multiple resource.  */
status = nx_lwm2m_client_resource_dim_get(&resource, &dim);

/* If status is NX_SUCCESS, the resource dimension was successfully get. */
```

## <a name="nx_lwm2m_client_resource_dim_set"></a><span data-ttu-id="1e567-655">nx_lwm2m_client_resource_dim_set</span><span class="sxs-lookup"><span data-stu-id="1e567-655">nx_lwm2m_client_resource_dim_set</span></span>

<span data-ttu-id="1e567-656">複数のリソースのリソース ディメンションを設定します。</span><span class="sxs-lookup"><span data-stu-id="1e567-656">Sets the resource dimension for multiple resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-657">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-657">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_dim_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR dim);
```

### <a name="description"></a><span data-ttu-id="1e567-658">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-658">Description</span></span>

<span data-ttu-id="1e567-659">このサービスを使用すると、複数のリソースのリソース ディメンションが設定されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-659">The service sets the resource dimension for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-660">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-660">Parameters</span></span>

- <span data-ttu-id="1e567-661">**value** リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-661">**value** Pointer to Resource value description.</span></span>
- <span data-ttu-id="1e567-662">**dim** ディメンション値。</span><span class="sxs-lookup"><span data-stu-id="1e567-662">**dim** Dimension value.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-663">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-663">Return Values</span></span>

- <span data-ttu-id="1e567-664">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-664">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-665">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-665">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-666">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-666">Allowed From</span></span>

<span data-ttu-id="1e567-667">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-667">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-668">例</span><span class="sxs-lookup"><span data-stu-id="1e567-668">Example</span></span>

```c
/* Set the resource dimension.  */
status = nx_lwm2m_client_resource_dim_set(&resource, 3);

/* If status is NX_SUCCESS, the resource dimension was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float32_get"></a><span data-ttu-id="1e567-669">nx_lwm2m_client_resource_float32_get</span><span class="sxs-lookup"><span data-stu-id="1e567-669">nx_lwm2m_client_resource_float32_get</span></span>

<span data-ttu-id="1e567-670">32 ビット **浮動小数点数** リソースの値を取得します</span><span class="sxs-lookup"><span data-stu-id="1e567-670">Gets the value of a 32-Bit **float** Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-671">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-671">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_float32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-672">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-672">Description</span></span>

<span data-ttu-id="1e567-673">このサービスを使用すると、32 ビットの **浮動小数点数** リソースの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-673">The service retrieves the value of a 32-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-674">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-674">Parameters</span></span>

- <span data-ttu-id="1e567-675">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-675">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-676">**float32_ptr** 宛先の 32 ビット **浮動小数点数** 値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-676">**float32_ptr** Pointer to the destination 32-Bit **float** value.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-677">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-677">Return Values</span></span>

- <span data-ttu-id="1e567-678">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-678">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-679">**NX_LWM2M_CLIENT_BAD_ENCODING** リソース値がブール値ではありません。</span><span class="sxs-lookup"><span data-stu-id="1e567-679">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="1e567-680">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-680">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-681">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-681">Allowed From</span></span>

<span data-ttu-id="1e567-682">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-682">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-683">例</span><span class="sxs-lookup"><span data-stu-id="1e567-683">Example</span></span>

```C
/* Get the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_get(&resource, &float32);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float32_set"></a><span data-ttu-id="1e567-684">nx_lwm2m_client_resource_float32_set</span><span class="sxs-lookup"><span data-stu-id="1e567-684">nx_lwm2m_client_resource_float32_set</span></span>

<span data-ttu-id="1e567-685">32 ビット **浮動小数点数** リソースの値を設定します</span><span class="sxs-lookup"><span data-stu-id="1e567-685">Sets the value of a 32-Bit **float** Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-686">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-686">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_float32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 float32_data);
```

### <a name="description"></a><span data-ttu-id="1e567-687">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-687">Description</span></span>

<span data-ttu-id="1e567-688">32 ビット **浮動小数点数** リソースの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="1e567-688">The service sets the value of a 32-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-689">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-689">Parameters</span></span>

- <span data-ttu-id="1e567-690">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-690">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-691">**float32_data** 32 ビットの **浮動小数点数** データ。</span><span class="sxs-lookup"><span data-stu-id="1e567-691">**float32_data** 32-Bit **float** data.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-692">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-692">Return Values</span></span>

- <span data-ttu-id="1e567-693">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-693">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-694">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-694">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-695">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-695">Allowed From</span></span>

<span data-ttu-id="1e567-696">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-696">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-697">例</span><span class="sxs-lookup"><span data-stu-id="1e567-697">Example</span></span>

```c
/* Set the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float64_get"></a><span data-ttu-id="1e567-698">nx_lwm2m_client_resource_float64_get</span><span class="sxs-lookup"><span data-stu-id="1e567-698">nx_lwm2m_client_resource_float64_get</span></span>

<span data-ttu-id="1e567-699">64 ビット浮動小数点数リソースの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="1e567-699">Gets the value of a 64-Bit float Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-700">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-700">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_float64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-701">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-701">Description</span></span>

<span data-ttu-id="1e567-702">このサービスを使用すると、64 ビットの **浮動小数点数** リソースの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-702">The service retrieves the value of a 64-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-703">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-703">Parameters</span></span>

- <span data-ttu-id="1e567-704">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-704">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-705">**float64_ptr** 宛先の 64 ビット **浮動小数点数** 値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-705">**float64_ptr** Pointer to the destination 64-Bit **float** value.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-706">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-706">Return Values</span></span>

- <span data-ttu-id="1e567-707">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-707">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-708">**NX_LWM2M_CLIENT_BAD_ENCODING** リソース値が浮動小数点数値ではありません。</span><span class="sxs-lookup"><span data-stu-id="1e567-708">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a float value.</span></span>
- <span data-ttu-id="1e567-709">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-709">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-710">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-710">Allowed From</span></span>

<span data-ttu-id="1e567-711">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-711">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-712">例</span><span class="sxs-lookup"><span data-stu-id="1e567-712">Example</span></span>

```c
/* Get the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_get(&resource, &float64);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float64_set"></a><span data-ttu-id="1e567-713">nx_lwm2m_client_resource_float64_set</span><span class="sxs-lookup"><span data-stu-id="1e567-713">nx_lwm2m_client_resource_float64_set</span></span>

<span data-ttu-id="1e567-714">64 ビット **浮動小数点数** リソースの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="1e567-714">Sets the value of a 64-Bit **float** Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-715">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-715">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_float64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a><span data-ttu-id="1e567-716">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-716">Description</span></span>

<span data-ttu-id="1e567-717">このサービスによって 64 ビット **浮動小数点数** リソースの値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-717">The service sets the value of a 64-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-718">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-718">Parameters</span></span>

- <span data-ttu-id="1e567-719">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-719">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-720">**float64_data** 64 ビットの **浮動小数点数** データ。</span><span class="sxs-lookup"><span data-stu-id="1e567-720">**float64_data** 64-bit **float** data.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-721">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-721">Return Values</span></span>

- <span data-ttu-id="1e567-722">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-722">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-723">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-723">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-724">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-724">Allowed From</span></span>

<span data-ttu-id="1e567-725">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-725">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-726">例</span><span class="sxs-lookup"><span data-stu-id="1e567-726">Example</span></span>

```c
/* Set the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_info_get"></a><span data-ttu-id="1e567-727">nx_lwm2m_client_resource_info_get</span><span class="sxs-lookup"><span data-stu-id="1e567-727">nx_lwm2m_client_resource_info_get</span></span>

<span data-ttu-id="1e567-728">リソース情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="1e567-728">Gets the resource info.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-729">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-729">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_info_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *resource_id, 
    ULONG *operation);
```

### <a name="description"></a><span data-ttu-id="1e567-730">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-730">Description</span></span>

<span data-ttu-id="1e567-731">このサービスを使用するとリソースのリソース情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-731">The service retrieves the resource information of Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-732">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-732">Parameters</span></span>

- <span data-ttu-id="1e567-733">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-733">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-734">**resource_id** 宛先リソース ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-734">**resource_id** Pointer to the destination resource ID.</span></span>
- <span data-ttu-id="1e567-735">**操作** 宛先リソース操作へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-735">**operation** Pointer to the destination resource operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-736">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-736">Return Values</span></span>

- <span data-ttu-id="1e567-737">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-737">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-738">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-738">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-739">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-739">Allowed From</span></span>

<span data-ttu-id="1e567-740">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-740">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-741">例</span><span class="sxs-lookup"><span data-stu-id="1e567-741">Example</span></span>

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_info_get(&resource, &resource_id, &operation);

/* If status is NX_SUCCESS, the resource information was successfully get. */
```

## <a name="nx_lwm2m_client_resource_info_set"></a><span data-ttu-id="1e567-742">nx_lwm2m_client_resource_info_set</span><span class="sxs-lookup"><span data-stu-id="1e567-742">nx_lwm2m_client_resource_info_set</span></span>

<span data-ttu-id="1e567-743">リソース情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="1e567-743">Sets the resource information.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-744">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-744">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_info_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a><span data-ttu-id="1e567-745">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-745">Description</span></span>

<span data-ttu-id="1e567-746">このサービスを使用するとリソース情報が設定されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-746">The service sets the resource information.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-747">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-747">Parameters</span></span>

- <span data-ttu-id="1e567-748">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-748">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-749">**resource_id** リソースの ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-749">**resource_id** ID of the resource.</span></span>
- <span data-ttu-id="1e567-750">**operation** リソースの操作。</span><span class="sxs-lookup"><span data-stu-id="1e567-750">**operation** Operation of the resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-751">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-751">Return Values</span></span>

- <span data-ttu-id="1e567-752">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-752">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-753">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-753">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-754">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-754">Allowed From</span></span>

<span data-ttu-id="1e567-755">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-755">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-756">例</span><span class="sxs-lookup"><span data-stu-id="1e567-756">Example</span></span>

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_info_set(&resource, 0, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

/* If status is NX_SUCCESS, the resource information was successfully set. */
```

## <a name="nx_lwm2m_client_resource_instances_get"></a><span data-ttu-id="1e567-757">nx_lwm2m_client_resource_instances_get</span><span class="sxs-lookup"><span data-stu-id="1e567-757">nx_lwm2m_client_resource_instances_get</span></span>

<span data-ttu-id="1e567-758">複数のリソースのインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="1e567-758">Gets the instance of multiple resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-759">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-759">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_instances_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT *count);
```

### <a name="description"></a><span data-ttu-id="1e567-760">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-760">Description</span></span>

<span data-ttu-id="1e567-761">このサービスを使用するとリソースのリソース情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-761">The service retrieves the resource information of Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-762">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-762">Parameters</span></span>

- <span data-ttu-id="1e567-763">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-763">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-764">**resource_id** 宛先リソース ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-764">**resource_instances** Pointer to the destination resource ID.</span></span>
- <span data-ttu-id="1e567-765">**count** カウントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-765">**count** Pointer to the count.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-766">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-766">Return Values</span></span>

- <span data-ttu-id="1e567-767">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-767">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-768">**NX_LWM2M_CLIENT_BAD_ENCODING** リソース値がブール値ではありません。</span><span class="sxs-lookup"><span data-stu-id="1e567-768">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="1e567-769">**NX_LWM2M_CLIENT_NO_MEMORY** インスタンスに入力するためのメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="1e567-769">**NX_LWM2M_CLIENT_NO_MEMORY** No memory to fill out instances.</span></span>
- <span data-ttu-id="1e567-770">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-770">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-771">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-771">Allowed From</span></span>

<span data-ttu-id="1e567-772">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-772">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-773">例</span><span class="sxs-lookup"><span data-stu-id="1e567-773">Example</span></span>

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_instances_get(&resource, &resource_instances,
                                                &count);

/* If status is NX_SUCCESS, the instances of multiple resource information were successfully get. */
```

## <a name="nx_lwm2m_client_resource_instances_set"></a><span data-ttu-id="1e567-774">nx_lwm2m_client_resource_instances_set</span><span class="sxs-lookup"><span data-stu-id="1e567-774">nx_lwm2m_client_resource_instances_set</span></span>

<span data-ttu-id="1e567-775">リソース インスタンスを設定します。</span><span class="sxs-lookup"><span data-stu-id="1e567-775">Sets the resource instances.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-776">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-776">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_instances_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT count);
```
### <a name="description"></a><span data-ttu-id="1e567-777">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-777">Description</span></span>

<span data-ttu-id="1e567-778">このサービスを使用すると、複数のリソースのリソース インスタンスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-778">The service sets the resource instances for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-779">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-779">Parameters</span></span>

- <span data-ttu-id="1e567-780">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-780">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-781">**resource_instance** リソース インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-781">**resource_instance** Pointer to resource instances.</span></span>
- <span data-ttu-id="1e567-782">**count** リソース インスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="1e567-782">**count** Count of resource instances.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-783">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-783">Return Values</span></span>

- <span data-ttu-id="1e567-784">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-784">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-785">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-785">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-786">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-786">Allowed From</span></span>

<span data-ttu-id="1e567-787">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-787">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-788">例</span><span class="sxs-lookup"><span data-stu-id="1e567-788">Example</span></span>

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_instances_set(&resource, &resource_instance, 2);

/* If status is NX_SUCCESS, the resource instances were successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer32_get"></a><span data-ttu-id="1e567-789">nx_lwm2m_client_resource_integer32_get</span><span class="sxs-lookup"><span data-stu-id="1e567-789">nx_lwm2m_client_resource_integer32_get</span></span>

<span data-ttu-id="1e567-790">32 ビット整数リソースの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="1e567-790">Gets the value of a 32-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-791">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-791">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 *integer32_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-792">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-792">Description</span></span>

<span data-ttu-id="1e567-793">このサービスを使用すると、32 ビット整数リソースの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-793">The service retrieves the value of a 32-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-794">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-794">Parameters</span></span>

- <span data-ttu-id="1e567-795">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-795">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-796">**integer32_ptr** 32 ビット整数値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-796">**integer32_ptr** Pointer to the 32-Bit integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-797">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-797">Return Values</span></span>

- <span data-ttu-id="1e567-798">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-798">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-799">**NX_LWM2M_CLIENT_BAD_ENCODING** リソース値が整数値ではありません。</span><span class="sxs-lookup"><span data-stu-id="1e567-799">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not integer value.</span></span>
- <span data-ttu-id="1e567-800">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-800">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-801">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-801">Allowed From</span></span>

<span data-ttu-id="1e567-802">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-802">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-803">例</span><span class="sxs-lookup"><span data-stu-id="1e567-803">Example</span></span>

```c
/* Get the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_get(&resource, &integer32);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer32_set"></a><span data-ttu-id="1e567-804">nx_lwm2m_client_resource_integer32_set</span><span class="sxs-lookup"><span data-stu-id="1e567-804">nx_lwm2m_client_resource_integer32_set</span></span>

<span data-ttu-id="1e567-805">32 ビット整数リソースの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="1e567-805">Sets the value of a 32-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-806">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-806">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 integer32_data);
```

### <a name="description"></a><span data-ttu-id="1e567-807">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-807">Description</span></span>

<span data-ttu-id="1e567-808">このサービスを使用すると、32 ビット整数リソースの値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-808">The service sets the value of a 32-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-809">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-809">Parameters</span></span>

- <span data-ttu-id="1e567-810">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-810">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-811">**integer32_data** 32 ビット整数データ。</span><span class="sxs-lookup"><span data-stu-id="1e567-811">**integer32_data** 32-Bit integer data.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-812">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-812">Return Values</span></span>

- <span data-ttu-id="1e567-813">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-813">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-814">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-814">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-815">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-815">Allowed From</span></span>

<span data-ttu-id="1e567-816">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-816">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-817">例</span><span class="sxs-lookup"><span data-stu-id="1e567-817">Example</span></span>

```c
/* Set the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_set(&resource, 8);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer64_get"></a><span data-ttu-id="1e567-818">nx_lwm2m_client_resource_integer64_get</span><span class="sxs-lookup"><span data-stu-id="1e567-818">nx_lwm2m_client_resource_integer64_get</span></span>

<span data-ttu-id="1e567-819">64 ビット整数リソースの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="1e567-819">Gets the value of a 64-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-820">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-820">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 *integer64_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-821">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-821">Description</span></span>

<span data-ttu-id="1e567-822">このサービスを使用すると、64 ビット整数リソースの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-822">The service retrieves the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-823">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-823">Parameters</span></span>

- <span data-ttu-id="1e567-824">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-824">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-825">**integer64_ptr** 64 ビット整数値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-825">**integer64_ptr** Pointer to the 64-Bit integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-826">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-826">Return Values</span></span>

- <span data-ttu-id="1e567-827">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-827">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-828">**NX_LWM2M_CLIENT_BAD_ENCODING** リソース値が 64 ビット整数値ではありません。</span><span class="sxs-lookup"><span data-stu-id="1e567-828">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not 64-Bit integer value.</span></span>
- <span data-ttu-id="1e567-829">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-829">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-830">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-830">Allowed From</span></span>

<span data-ttu-id="1e567-831">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-831">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-832">例</span><span class="sxs-lookup"><span data-stu-id="1e567-832">Example</span></span>

```c
/* Get the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_get(&resource, &integer64);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer64_set"></a><span data-ttu-id="1e567-833">nx_lwm2m_client_resource_integer64_set</span><span class="sxs-lookup"><span data-stu-id="1e567-833">nx_lwm2m_client_resource_integer64_set</span></span>

## <a name="set-the-value-of-a-64-bit-integer-resource"></a><span data-ttu-id="1e567-834">64 ビット整数リソースの値を設定します</span><span class="sxs-lookup"><span data-stu-id="1e567-834">Set the value of a 64-Bit integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-835">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-835">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 integer64_data);
```

### <a name="description"></a><span data-ttu-id="1e567-836">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-836">Description</span></span>

<span data-ttu-id="1e567-837">このサービスを使用すると、64 ビット整数リソースの値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-837">The service sets the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-838">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-838">Parameters</span></span>

- <span data-ttu-id="1e567-839">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-839">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-840">**integer64_data** 64 ビット整数。</span><span class="sxs-lookup"><span data-stu-id="1e567-840">**integer64_data** 64-bit integer.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-841">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-841">Return Values</span></span>

- <span data-ttu-id="1e567-842">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-842">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-843">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-843">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-844">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-844">Allowed From</span></span>

<span data-ttu-id="1e567-845">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-845">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-846">例</span><span class="sxs-lookup"><span data-stu-id="1e567-846">Example</span></span>

```c
/* Set the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_set(&resource, 32323);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully set. */
```

##  <a name="nx_lwm2m_client_resource_objlnk_get"></a><span data-ttu-id="1e567-847">nx_lwm2m_client_resource_objlnk_get</span><span class="sxs-lookup"><span data-stu-id="1e567-847">nx_lwm2m_client_resource_objlnk_get</span></span>

<span data-ttu-id="1e567-848">オブジェクト リンク リソースの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="1e567-848">Gets the value of an object link resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-849">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-849">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_objlnk_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *object_id, 
    NX_LWM2M_ID *instance_id);
```

### <a name="description"></a><span data-ttu-id="1e567-850">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-850">Description</span></span>

<span data-ttu-id="1e567-851">このサービスを使用すると、オブジェクト リンクの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-851">The service retrieves the value of object link.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-852">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-852">Parameters</span></span>

- <span data-ttu-id="1e567-853">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-853">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-854">**object_id** オブジェクト ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-854">**object_id** Pointer to the object ID.</span></span>
- <span data-ttu-id="1e567-855">**instance_id** オブジェクト インスタンス ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-855">**instance_id** Pointer to the object instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-856">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-856">Return Values</span></span>

- <span data-ttu-id="1e567-857">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-857">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-858">**NX_LWM2M_CLIENT_BAD_ENCODING** リソース値がオブジェクト リンク値ではありません。</span><span class="sxs-lookup"><span data-stu-id="1e567-858">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not an object link value.</span></span>
- <span data-ttu-id="1e567-859">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-859">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-860">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-860">Allowed From</span></span>

<span data-ttu-id="1e567-861">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-861">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-862">例</span><span class="sxs-lookup"><span data-stu-id="1e567-862">Example</span></span>

```c
/* Get the value of the object link resource.  */
status = nx_lwm2m_client_resource_objlnk_get(&resource, &object_id, &instance_id);

/* If status is NX_SUCCESS, the object link value was successfully get. */
```

## <a name="nx_lwm2m_client_resource_objlnk_set"></a><span data-ttu-id="1e567-863">nx_lwm2m_client_resource_objlnk_set</span><span class="sxs-lookup"><span data-stu-id="1e567-863">nx_lwm2m_client_resource_objlnk_set</span></span>

<span data-ttu-id="1e567-864">リソース インスタンスを設定します</span><span class="sxs-lookup"><span data-stu-id="1e567-864">Sets the resource instances</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-865">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-865">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_objlnk_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_ID object_id, 
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="1e567-866">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-866">Description</span></span>

<span data-ttu-id="1e567-867">このサービスを使用すると、オブジェクト リンク リソースの値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-867">The service sets the value of the object link resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-868">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-868">Parameters</span></span>

- <span data-ttu-id="1e567-869">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-869">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-870">**object_id** オブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-870">**object_id** Object ID.</span></span>
- <span data-ttu-id="1e567-871">**instance_id** オブジェクト インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-871">**instance_id** Object instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-872">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-872">Return Values</span></span>

- <span data-ttu-id="1e567-873">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-873">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-874">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-874">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-875">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-875">Allowed From</span></span>

<span data-ttu-id="1e567-876">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-876">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-877">例</span><span class="sxs-lookup"><span data-stu-id="1e567-877">Example</span></span>

```c
/* Set the value of object link resource.  */
status = nx_lwm2m_client_resource_objlnk_set(&resource, 3303, 2);

/* If status is NX_SUCCESS, the value of object link resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_opaque_get"></a><span data-ttu-id="1e567-878">nx_lwm2m_client_resource_opaque_get</span><span class="sxs-lookup"><span data-stu-id="1e567-878">nx_lwm2m_client_resource_opaque_get</span></span>

<span data-ttu-id="1e567-879">不透明なリソースの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="1e567-879">Gets the value of an opaque Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-880">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-880">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_opaque_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const VOID **opaque_ptr, 
    UINT \*opaque_length);
```


### <a name="description"></a><span data-ttu-id="1e567-881">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-881">Description</span></span>

<span data-ttu-id="1e567-882">このサービスを使用すると、不透明なリソースの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-882">The service retrieves the value of an opaque Resource.</span></span> <span data-ttu-id="1e567-883">不透明なリソース値は、バッファーへのポインターと長さで構成されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-883">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-884">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-884">Parameters</span></span>

- <span data-ttu-id="1e567-885">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-885">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-886">**opaque_ptr** 不透明なデータへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-886">**opaque_ptr** Pointer to the opaque data.</span></span>
- <span data-ttu-id="1e567-887">**opaque_ptr** 不透明なデータ長へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-887">**opaque_length** Pointer to the opaque data length.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-888">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-888">Return Values</span></span>

- <span data-ttu-id="1e567-889">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-889">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-890">**NX_LWM2M_CLIENT_BAD_ENCODING** リソース値が不透明なリソースではありません。</span><span class="sxs-lookup"><span data-stu-id="1e567-890">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not an opaque resource.</span></span>
- <span data-ttu-id="1e567-891">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-891">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-892">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-892">Allowed From</span></span>

<span data-ttu-id="1e567-893">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-893">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-894">例</span><span class="sxs-lookup"><span data-stu-id="1e567-894">Example</span></span>

```c
/* Get the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_get(&resource, &opaque_ptr, &opaque_length);

/* If status is NX_SUCCESS, the value of opaque resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_opaque_set"></a><span data-ttu-id="1e567-895">nx_lwm2m_client_resource_opaque_set</span><span class="sxs-lookup"><span data-stu-id="1e567-895">nx_lwm2m_client_resource_opaque_set</span></span>

<span data-ttu-id="1e567-896">不透明なリソースの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="1e567-896">Sets the value of an opaque Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-897">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-897">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_opaque_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    VOID *opaque_ptr, 
    UINT opaque_length);
```

### <a name="description"></a><span data-ttu-id="1e567-898">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-898">Description</span></span>

<span data-ttu-id="1e567-899">このサービスを使用すると、不透明なリソースの値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-899">The service sets the value of an opaque Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-900">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-900">Parameters</span></span>

- <span data-ttu-id="1e567-901">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-901">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-902">**opaque_ptr** 不透明なデータへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-902">**opaque_ptr** Pointer to the opaque data.</span></span>
- <span data-ttu-id="1e567-903">**opaque_length** 不透明なデータの長さ。</span><span class="sxs-lookup"><span data-stu-id="1e567-903">**opaque_length** Length of the opaque data.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-904">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-904">Return Values</span></span>

- <span data-ttu-id="1e567-905">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-905">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-906">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-906">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-907">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-907">Allowed From</span></span>

<span data-ttu-id="1e567-908">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-908">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-909">例</span><span class="sxs-lookup"><span data-stu-id="1e567-909">Example</span></span>

```c
/* Set the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_set(&resource, “AQIDBAU=”, 8);

/* If status is NX_SUCCESS, the value of opaque resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_string_get"></a><span data-ttu-id="1e567-910">nx_lwm2m_client_resource_string_get</span><span class="sxs-lookup"><span data-stu-id="1e567-910">nx_lwm2m_client_resource_string_get</span></span>

<span data-ttu-id="1e567-911">文字列リソースの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="1e567-911">Gets the value of a string Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-912">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-912">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_string_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const CHAR **string_ptr, 
    UINT *string_length);
```

### <a name="description"></a><span data-ttu-id="1e567-913">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-913">Description</span></span>

<span data-ttu-id="1e567-914">このサービスを使用すると、文字列リソースの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-914">The service retrieves the value of a string Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-915">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-915">Parameters</span></span>

- <span data-ttu-id="1e567-916">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-916">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-917">**string_ptr** 宛先文字列ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-917">**string_ptr** Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="1e567-918">**string_ptr** 宛先文字列長へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-918">**string_length** Pointer to the destination string length.</span></span> <span data-ttu-id="1e567-919">文字列が null で終わる場合は **NULL** を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1e567-919">Can be **NULL** if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-920">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-920">Return Values</span></span>

- <span data-ttu-id="1e567-921">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-921">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-922">**NX_LWM2M_CLIENT_BAD_ENCODING** リソース値が文字列値ではありません。</span><span class="sxs-lookup"><span data-stu-id="1e567-922">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a string value.</span></span>
- <span data-ttu-id="1e567-923">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-923">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-924">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-924">Allowed From</span></span>

<span data-ttu-id="1e567-925">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-925">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-926">例</span><span class="sxs-lookup"><span data-stu-id="1e567-926">Example</span></span>

```c
/* Get the value of a string resource.  */
status = nx_lwm2m_client_resource_string_get(&resource, &string_ptr, &string_length);

/* If status is NX_SUCCESS, the value of string resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_string_set"></a><span data-ttu-id="1e567-927">nx_lwm2m_client_resource_string_set</span><span class="sxs-lookup"><span data-stu-id="1e567-927">nx_lwm2m_client_resource_string_set</span></span>

<span data-ttu-id="1e567-928">文字列リソースの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="1e567-928">Sets the value of a string Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-929">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-929">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_string_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR *string_ptr, 
    UINT string_length);
```

### <a name="description"></a><span data-ttu-id="1e567-930">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-930">Description</span></span>

<span data-ttu-id="1e567-931">このサービスを使用すると、64 ビット整数リソースの値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-931">The service sets the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-932">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-932">Parameters</span></span>

- <span data-ttu-id="1e567-933">**resource** リソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-933">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="1e567-934">**string_ptr** 文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-934">**string_ptr** Pointer to the string.</span></span>
- <span data-ttu-id="1e567-935">**string_length** 文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="1e567-935">**string_length** Length of the string.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-936">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-936">Return Values</span></span>

- <span data-ttu-id="1e567-937">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-937">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-938">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-938">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-939">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-939">Allowed From</span></span>

<span data-ttu-id="1e567-940">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-940">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-941">例</span><span class="sxs-lookup"><span data-stu-id="1e567-941">Example</span></span>

```c
/* Set the value of a string resource.  */
status = nx_lwm2m_client_resource_string_set(&resource, “test”, sizeof(“test”) - 1);

/* If status is NX_SUCCESS, the value of string resource was successfully set. */
```

## <a name="nx_lwm2m_client_session_bootstrap"></a><span data-ttu-id="1e567-942">nx_lwm2m_client_session_bootstrap</span><span class="sxs-lookup"><span data-stu-id="1e567-942">nx_lwm2m_client_session_bootstrap</span></span>

<span data-ttu-id="1e567-943">ブートストラップ サーバーとのセッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="1e567-943">Starts a session with a Bootstrap Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-944">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-944">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port);
```

### <a name="description"></a><span data-ttu-id="1e567-945">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-945">Description</span></span>

<span data-ttu-id="1e567-946">このサービスを使用すると、ブートストラップ サーバーとのセッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-946">This service starts a session with a Bootstrap Server.</span></span> <span data-ttu-id="1e567-947">サーバーには、セキュリティ オブジェクト内に対応するセキュリティ インスタンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="1e567-947">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="1e567-948">このサーバーに関連付けられているセキュリティ インスタンスで、"保留中" リソースが 0 以外の場合、セッションはサーバーによって開始されるブートストラップを待機します。この期間が過ぎてもサーバーによってブートストラップが開始されなかった場合は、クライアントによって開始されたブートストラップが実行されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-948">If the ‘Hold Off’ resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, If no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="1e567-949">現在アクティブなセッションは、この呼び出しによって中止され、新しいブートストラップ サーバー セッションに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="1e567-949">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-950">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-950">Parameters</span></span>

- <span data-ttu-id="1e567-951">**session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-951">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="1e567-952">**security_id** ブートストラップ サーバーのセキュリティ インスタンスが定義されていない場合は、ブートストラップ サーバーのセキュリティインスタンス ID を NX_LWM2M_RESERVED_ID (65535) に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e567-952">**security_id** The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="1e567-953">**ip_address** サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="1e567-953">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="1e567-954">**port** サーバーの UDP ポート。</span><span class="sxs-lookup"><span data-stu-id="1e567-954">**port** The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-955">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-955">Return Values</span></span>

- <span data-ttu-id="1e567-956">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-956">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-957">**NX_LWM2M_CLIENT_ERROR** ブートストラップ エラー。</span><span class="sxs-lookup"><span data-stu-id="1e567-957">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="1e567-958">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** ポートを使用できません。</span><span class="sxs-lookup"><span data-stu-id="1e567-958">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="1e567-959">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-959">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-960">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-960">Allowed From</span></span>

<span data-ttu-id="1e567-961">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-961">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-962">例</span><span class="sxs-lookup"><span data-stu-id="1e567-962">Example</span></span>

```c
/* Start bootstrap.  */
status = nx_lwm2m_client_session_bootstrap(&lwm2m_client, 0, &ip_address, 5783);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a><span data-ttu-id="1e567-963">nx_lwm2m_client_session_bootstrap_dtls</span><span class="sxs-lookup"><span data-stu-id="1e567-963">nx_lwm2m_client_session_bootstrap_dtls</span></span>

<span data-ttu-id="1e567-964">ブートストラップ サーバーとのセキュリティで保護されたセッションを開始します</span><span class="sxs-lookup"><span data-stu-id="1e567-964">Starts a secure session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-965">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-965">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port, 
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-966">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-966">Description</span></span>

<span data-ttu-id="1e567-967">このサービスを使用すると、セキュリティで保護された DTLS 接続を使用して、ブートストラップ サーバーとのセッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-967">This service start a session with a Bootstrap Server using a secure DTLS connection.</span></span> <span data-ttu-id="1e567-968">サーバーには、セキュリティ オブジェクト内に対応するセキュリティ インスタンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="1e567-968">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="1e567-969">この関数を呼び出す前に、DTLS セッションが適切な暗号スイートとキー素材で構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e567-969">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="1e567-970">**NX_SECURE_ENABLE_DTLS** を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e567-970">**NX_SECURE_ENABLE_DTLS** must be defined.</span></span>

<span data-ttu-id="1e567-971">このサーバーに関連付けられているセキュリティ インスタンスで、"保留中" リソースが 0 以外の場合、セッションはサーバーによって開始されるブートストラップを待機します。この期間が過ぎてもサーバーによってブートストラップが開始されなかった場合は、クライアントによって開始されたブートストラップが実行されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-971">If the ‘Hold Off’ resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span> 

<span data-ttu-id="1e567-972">現在アクティブなセッションは、この呼び出しによって中止され、新しいブートストラップ サーバー セッションに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="1e567-972">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-973">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-973">Parameters</span></span>

- <span data-ttu-id="1e567-974">**session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-974">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="1e567-975">**security_id** ブートストラップ サーバーのセキュリティ インスタンスが定義されていない場合は、ブートストラップ サーバーのセキュリティインスタンス ID を **NX_LWM2M_RESERVED_ID** (65535) に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e567-975">**security_id** The Security Instance ID of the Bootstrap Server, must be set to **NX_LWM2M_RESERVED_ID** (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="1e567-976">**ip_address** サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="1e567-976">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="1e567-977">**port** サーバーの UDP ポート。</span><span class="sxs-lookup"><span data-stu-id="1e567-977">**port** The UDP port of the server.</span></span>
- <span data-ttu-id="1e567-978">**dtls_session_ptr** ブートストラップ セッションに使用する DTLS セッション。</span><span class="sxs-lookup"><span data-stu-id="1e567-978">**dtls_session_ptr** The DTLS session to use for the Bootstrap session.</span></span>
- <span data-ttu-id="1e567-979">**dtls_local_port** DTLS セッションに使用されるローカル UDP ポート。</span><span class="sxs-lookup"><span data-stu-id="1e567-979">**dtls_local_port** The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-980">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-980">Return Values</span></span>

- <span data-ttu-id="1e567-981">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-981">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-982">**NX_LWM2M_CLIENT_ERROR** ブートストラップ エラー。</span><span class="sxs-lookup"><span data-stu-id="1e567-982">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="1e567-983">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** ポートを使用できません。</span><span class="sxs-lookup"><span data-stu-id="1e567-983">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="1e567-984">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-984">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-985">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-985">Allowed From</span></span>

<span data-ttu-id="1e567-986">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-986">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-987">例</span><span class="sxs-lookup"><span data-stu-id="1e567-987">Example</span></span>

```c
/* Start bootstrap with DTLS.  */
status = nx_lwm2m_client_session_bootstrap_dtls(&lwm2m_client, 0, &ip_address, 5784, &dtls_session);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_create"></a><span data-ttu-id="1e567-988">nx_lwm2m_client_session_create</span><span class="sxs-lookup"><span data-stu-id="1e567-988">nx_lwm2m_client_session_create</span></span>

<span data-ttu-id="1e567-989">LWM2M クライアント セッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="1e567-989">Creates a LWM2M Client Session.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-990">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-990">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_create(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a><span data-ttu-id="1e567-991">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-991">Description</span></span>

<span data-ttu-id="1e567-992">このサービスを使用すると、既存の LWM2M クライアントにアタッチされた新しい LWM2M クライアント セッションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-992">This service creates a new LWM2M Client Session attached to an existing LWM2M Client.</span></span> <span data-ttu-id="1e567-993">セッションは、ブートストラップ サーバーまたは LWM2M サーバーと通信するために LWM2M クライアントによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-993">The session is used by the LWM2M Client to communicate with a Bootstrap Server or a LWM2M Server.</span></span> 

<span data-ttu-id="1e567-994">アプリケーションは、セッションの状態が更新されたときに呼び出されるコールバック関数を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e567-994">The application must provide a callback function that will be called when the state of the session is updated.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-995">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-995">Parameters</span></span>

- <span data-ttu-id="1e567-996">**session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-996">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="1e567-997">**client_ptr** 以前に作成した LWM2M クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-997">**client_ptr** Pointer to the previously created LWM2M Client.</span></span>
- <span data-ttu-id="1e567-998">**state_callback** セッションの状態が変更されたときに呼び出されるアプリケーション コールバック。</span><span class="sxs-lookup"><span data-stu-id="1e567-998">**state_callback** Application callback that is called when the state of the session has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-999">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-999">Return Values</span></span>

- <span data-ttu-id="1e567-1000">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-1000">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-1001">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-1001">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-1002">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-1002">Allowed From</span></span>

<span data-ttu-id="1e567-1003">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-1003">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-1004">例</span><span class="sxs-lookup"><span data-stu-id="1e567-1004">Example</span></span>

```c
/* Create session.  */
status = nx_lwm2m_client_session_create(&session, &lwm2m_client, session_callback);

/* If status is NX_SUCCESS, a session was successfully created.  */
```

## <a name="nx_lwm2m_client_session_delete"></a><span data-ttu-id="1e567-1005">nx_lwm2m_client_session_delete</span><span class="sxs-lookup"><span data-stu-id="1e567-1005">nx_lwm2m_client_session_delete</span></span>

<span data-ttu-id="1e567-1006">LWM2M クライアント セッションを削除します。</span><span class="sxs-lookup"><span data-stu-id="1e567-1006">Deletes a LWM2M Client Session.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-1007">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-1007">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-1008">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-1008">Description</span></span>

<span data-ttu-id="1e567-1009">このサービスを使用すると LWM2M クライアント セッションが削除されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-1009">This service deletes a LWM2M Client Session.</span></span>

<span data-ttu-id="1e567-1010">nx_lwm2m_client_delete を呼び出して LWM2M クライアントを削除すると、クライアントにアタッチされているすべてのセッションも削除されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-1010">When a LWM2M Client is deleted by calling nx_lwm2m_client_delete all sessions attached to the client are also deleted.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-1011">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-1011">Parameters</span></span>

- <span data-ttu-id="1e567-1012">**session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1012">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-1013">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-1013">Return Values</span></span>

- <span data-ttu-id="1e567-1014">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-1014">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-1015">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-1015">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-1016">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-1016">Allowed From</span></span>

<span data-ttu-id="1e567-1017">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-1017">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-1018">例</span><span class="sxs-lookup"><span data-stu-id="1e567-1018">Example</span></span>

```c
/* Delete session.  */
status = nx_lwm2m_client_session_delete(&session);

/* If status is NX_SUCCESS, a session was successfully deleted.  */
```

## <a name="nx_lwm2m_client_session_deregister"></a><span data-ttu-id="1e567-1019">nx_lwm2m_client_session_deregister</span><span class="sxs-lookup"><span data-stu-id="1e567-1019">nx_lwm2m_client_session_deregister</span></span>

<span data-ttu-id="1e567-1020">LWM2M サーバーとのセッションを終了します。</span><span class="sxs-lookup"><span data-stu-id="1e567-1020">Terminates a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-1021">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-1021">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-1022">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-1022">Description</span></span>

<span data-ttu-id="1e567-1023">このサービスを使用すると、LWM2M サーバーに対して "登録解除" 操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-1023">This service performs a ‘De-Register’ operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-1024">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-1024">Parameters</span></span>

- <span data-ttu-id="1e567-1025">**session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1025">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-1026">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-1026">Return Values</span></span>

- <span data-ttu-id="1e567-1027">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-1027">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-1028">**NX_LWM2M_CLIENT_NOT_REGISTERED** クライアントがサーバーに登録されていません。</span><span class="sxs-lookup"><span data-stu-id="1e567-1028">**NX_LWM2M_CLIENT_NOT_REGISTERED** The client is not registered to the server.</span></span>
- <span data-ttu-id="1e567-1029">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-1029">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-1030">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-1030">Allowed From</span></span>

<span data-ttu-id="1e567-1031">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-1031">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-1032">例</span><span class="sxs-lookup"><span data-stu-id="1e567-1032">Example</span></span>

```c
/* De-register session.  */
status = nx_lwm2m_client_session_deregister(&session);

/* If status is NX_SUCCESS, session was successfully de-registered.  */
```

## <a name="nx_lwm2m_client_session_error_get"></a><span data-ttu-id="1e567-1033">nx_lwm2m_client_session_error_get</span><span class="sxs-lookup"><span data-stu-id="1e567-1033">nx_lwm2m_client_session_error_get</span></span>

<span data-ttu-id="1e567-1034">セッションの最後のエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="1e567-1034">Gets the last error of a session.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-1035">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-1035">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-1036">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-1036">Description</span></span>

<span data-ttu-id="1e567-1037">このサービスを使用すると、セッションがエラー状態のときにセッションのエラー コードが返されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-1037">This service returns the error code of the session when the session is in an error state.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-1038">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-1038">Parameters</span></span>

- <span data-ttu-id="1e567-1039">**session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1039">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-1040">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-1040">Return Values</span></span>

- <span data-ttu-id="1e567-1041">**NX_SUCCESS** セッションがエラー状態ではありません。</span><span class="sxs-lookup"><span data-stu-id="1e567-1041">**NX_SUCCESS** The session is not in error state.</span></span>
- <span data-ttu-id="1e567-1042">**NX_LWM2M_CLIENT_ADDRESS_ERROR** サーバー アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-1042">**NX_LWM2M_CLIENT_ADDRESS_ERROR** Invalid server address.</span></span>
- <span data-ttu-id="1e567-1043">**NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** 要求のペイロードがネットワーク バッファーに収まりません。</span><span class="sxs-lookup"><span data-stu-id="1e567-1043">**NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** Payload of request doesn’t fit in network buffer.</span></span>
- <span data-ttu-id="1e567-1044">**NX_LWM2M_ CLIENT_DTLS_ERROR** サーバーとのセキュリティで保護された接続を確立できませんでした。</span><span class="sxs-lookup"><span data-stu-id="1e567-1044">**NX_LWM2M_ CLIENT_DTLS_ERROR** Failed to establish secured connection with server.</span></span>
- <span data-ttu-id="1e567-1045">**NX_LWM2M_ CLIENT_ERROR** 指定されていないエラー。</span><span class="sxs-lookup"><span data-stu-id="1e567-1045">**NX_LWM2M_ CLIENT_ERROR** Unspecified error.</span></span>
- <span data-ttu-id="1e567-1046">**NX_LWM2M_ CLIENT_FORBIDDEN** サーバーによって登録が拒否されました。</span><span class="sxs-lookup"><span data-stu-id="1e567-1046">**NX_LWM2M_ CLIENT_FORBIDDEN** Registration refused by server.</span></span>
- <span data-ttu-id="1e567-1047">**NX_LWM2M_ CLIENT_NOT_FOUND** 更新または登録解除するときに、サーバーがクライアントを見つけることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="1e567-1047">**NX_LWM2M_ CLIENT_NOT_FOUND** Client not found by server when updating/deregistering.</span></span>
- <span data-ttu-id="1e567-1048">**NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED**: セッションに対応するサーバー オブジェクト インスタンスが削除されました。</span><span class="sxs-lookup"><span data-stu-id="1e567-1048">**NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** The Server Object Instance corresponding to the session has been deleted.</span></span>
- <span data-ttu-id="1e567-1049">**NX_LWM2M_ CLIENT_TIMED_OUT** サーバーからの応答がありません。</span><span class="sxs-lookup"><span data-stu-id="1e567-1049">**NX_LWM2M_ CLIENT_TIMED_OUT** No answer from server.</span></span>
- <span data-ttu-id="1e567-1050">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-1050">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-1051">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-1051">Allowed From</span></span>

<span data-ttu-id="1e567-1052">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-1052">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-1053">例</span><span class="sxs-lookup"><span data-stu-id="1e567-1053">Example</span></span>

```c
/* Get the error.  */
status = nx_lwm2m_client_session_error_get(&session);
```
## <a name="nx_lwm2m_client_session_register"></a><span data-ttu-id="1e567-1054">nx_lwm2m_client_session_register</span><span class="sxs-lookup"><span data-stu-id="1e567-1054">nx_lwm2m_client_session_register</span></span>

<span data-ttu-id="1e567-1055">LWM2M サーバーとのセッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="1e567-1055">Starts a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-1056">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-1056">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port);
```


### <a name="description"></a><span data-ttu-id="1e567-1057">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-1057">Description</span></span>

<span data-ttu-id="1e567-1058">このサービスを使用すると、LWM2M サーバーに対して "登録" 操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-1058">This service performs a ‘Register’ operation to a LWM2M Server.</span></span> <span data-ttu-id="1e567-1059">サーバーは、サーバー オブジェクト内に対応するサーバー インスタンスを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e567-1059">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="1e567-1060">登録が正常に完了した場合、LWM2M クライアントによってサーバーからのその後の操作が処理され、クライアントが登録解除されるまで定期的に "更新" メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-1060">If the registration is successfully the LWM2M Client will process further operations from the server and will periodically send ‘Update’ messages until the client is de-registered.</span></span>

<span data-ttu-id="1e567-1061">現在アクティブなセッションは、この呼び出しによって中止され、新しい LWM2M サーバー セッションに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="1e567-1061">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-1062">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-1062">Parameters</span></span>

- <span data-ttu-id="1e567-1063">**session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1063">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="1e567-1064">**server_id** LWM2M サーバーの短いサーバー ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-1064">**server_id** The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="1e567-1065">**ip_address** サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="1e567-1065">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="1e567-1066">**port** サーバーの UDP ポート。</span><span class="sxs-lookup"><span data-stu-id="1e567-1066">**port** The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-1067">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-1067">Return Values</span></span>

- <span data-ttu-id="1e567-1068">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-1068">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-1069">**NX_LWM2M_CLIENT_ERROR** ブートストラップ エラー。</span><span class="sxs-lookup"><span data-stu-id="1e567-1069">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="1e567-1070">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** ポートを使用できません。</span><span class="sxs-lookup"><span data-stu-id="1e567-1070">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="1e567-1071">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-1071">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-1072">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-1072">Allowed From</span></span>

<span data-ttu-id="1e567-1073">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-1073">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-1074">例</span><span class="sxs-lookup"><span data-stu-id="1e567-1074">Example</span></span>

```c
/* Start register.  */
status = nx_lwm2m_client_session_register (&lwm2m_client, 123, &ip_address, 5683);

/* If status is NX_SUCCESS, start register successfully.  */
```

## <a name="nx_lwm2m_client_session_register_dtls"></a><span data-ttu-id="1e567-1075">nx_lwm2m_client_session_register_dtls</span><span class="sxs-lookup"><span data-stu-id="1e567-1075">nx_lwm2m_client_session_register_dtls</span></span>

<span data-ttu-id="1e567-1076">LWM2M サーバーとのセキュリティで保護されたセッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="1e567-1076">Starts a secure session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-1077">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-1077">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port,
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-1078">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-1078">Description</span></span>

<span data-ttu-id="1e567-1079">このサービスを使用すると、セキュリティで保護された DTLS 接続を使用して、LWM2M サーバーへの "登録" 操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-1079">This service performs a ‘Register’ operation to a LWM2M Server using a secure DTLS connection.</span></span> <span data-ttu-id="1e567-1080">サーバーは、サーバー オブジェクト内に対応するサーバー インスタンスを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e567-1080">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="1e567-1081">この関数を呼び出す前に、DTLS セッションが適切な暗号スイートとキー素材で構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e567-1081">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="1e567-1082">**NX_SECURE_ENABLE_DTLS** を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e567-1082">**NX_SECURE_ENABLE_DTLS** must be defined.</span></span>

<span data-ttu-id="1e567-1083">登録が正常に完了した場合、LWM2M クライアントによってサーバーからのその後の操作が処理され、クライアントが登録解除されるまで定期的に "更新" メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-1083">If the registration is successfully the LWM2M Client will process further operations from the server and will periodically send ‘Update’ messages until the client is de-registered.</span></span>

<span data-ttu-id="1e567-1084">現在アクティブなセッションは、この呼び出しによって中止され、新しい LWM2M サーバー セッションに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="1e567-1084">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-1085">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-1085">Parameters</span></span>

- <span data-ttu-id="1e567-1086">**session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1086">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="1e567-1087">**server_id** LWM2M サーバーの短いサーバー ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-1087">**server_id** The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="1e567-1088">**ip_address** サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="1e567-1088">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="1e567-1089">**port** サーバーの UDP ポート。</span><span class="sxs-lookup"><span data-stu-id="1e567-1089">**port** The UDP port of the server.</span></span>
- <span data-ttu-id="1e567-1090">**dtls_session_ptr** LWM2M セッションに使用する DTLS セッション。</span><span class="sxs-lookup"><span data-stu-id="1e567-1090">**dtls_session_ptr** The DTLS session to use for the LWM2M session.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-1091">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-1091">Return Values</span></span>

- <span data-ttu-id="1e567-1092">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-1092">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-1093">**NX_LWM2M_CLIENT_ERROR** ブートストラップ エラー。</span><span class="sxs-lookup"><span data-stu-id="1e567-1093">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="1e567-1094">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** ポートを使用できません。</span><span class="sxs-lookup"><span data-stu-id="1e567-1094">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="1e567-1095">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-1095">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-1096">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-1096">Allowed From</span></span>

<span data-ttu-id="1e567-1097">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-1097">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-1098">例</span><span class="sxs-lookup"><span data-stu-id="1e567-1098">Example</span></span>

```c
/* Start register with DTLS.  */
status = nx_lwm2m_client_session_register_dtls(&lwm2m_client, 123, &ip_address, 5683, &dtls_session);

/* If status is NX_SUCCESS, start register with DTLS successfully.  */
```

## <a name="nx_lwm2m_client_session_register_info_get"></a><span data-ttu-id="1e567-1099">nx_lwm2m_client_session_register_info_get</span><span class="sxs-lookup"><span data-stu-id="1e567-1099">nx_lwm2m_client_session_register_info_get</span></span>

<span data-ttu-id="1e567-1100">LWM2M サーバーとのセキュリティで保護されたセッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="1e567-1100">Starts a secure session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-1101">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-1101">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    UINT security_instance_id, 
    NX_LWM2M_ID *server_id,
    CHAR **server_uri, 
    UINT *server_uri_length, 
    UCHAR *security_mode, 
    UCHAR **pub_key_or_id, 
    UINT *pub_key_or_id_len, 
    UCHAR **server_pub_key, 
    UINT *server_pub_key_len, 
    UCHAR **secret_key, 
    UINT *secret_key_len);
```

### <a name="description"></a><span data-ttu-id="1e567-1102">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-1102">Description</span></span>

<span data-ttu-id="1e567-1103">ブートストラップ サーバーとの通信セッションが確立された後。</span><span class="sxs-lookup"><span data-stu-id="1e567-1103">Once a communication session with a Bootstrap server was established.</span></span> <span data-ttu-id="1e567-1104">アプリケーションからこの API を呼び出して、次の登録ステップのためにサーバーとセキュリティ情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="1e567-1104">Application can call this api to get the server and security information for the next registration step.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-1105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-1105">Parameters</span></span>

- <span data-ttu-id="1e567-1106">**session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1106">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="1e567-1107">**security_instance_id** セキュリティ インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="1e567-1107">**security_instance_id** Security instance ID.</span></span>
- <span data-ttu-id="1e567-1108">**server_id** 宛先サーバー ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1108">**server_id** Pointer to destination server ID.</span></span>
- <span data-ttu-id="1e567-1109">**server_uri** 宛先サーバー URI へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1109">**server_uri** Pointer to destination server uri.</span></span>
- <span data-ttu-id="1e567-1110">**server_uri_len** 宛先サーバー URI 長へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1110">**server_uri_len** Pointer to destination server uri length.</span></span>
- <span data-ttu-id="1e567-1111">**security_mode** 宛先セキュリティ モードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1111">**security_mode** Pointer to destination security mode.</span></span>
- <span data-ttu-id="1e567-1112">**pub_key_or_id** 宛先の公開キーまたは ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1112">**pub_key_or_id** Pointer to destination public key or identity.</span></span>
- <span data-ttu-id="1e567-1113">**pub_key_or_id_len** 宛先の公開キーまたは ID 長へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1113">**pub_key_or_id_len** Pointer to destination public key or identity length.</span></span>
- <span data-ttu-id="1e567-1114">**server_pub_key** 宛先サーバーの公開キーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1114">**server_pub_key** Pointer to destination server public key.</span></span>
- <span data-ttu-id="1e567-1115">**server_pub_key_len** 宛先サーバーの公開キー長へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1115">**server_pub_key_len** Pointer to destination server public key length.</span></span>
- <span data-ttu-id="1e567-1116">**secret_key** 宛先の秘密キーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1116">**secret_key** Pointer to destination secret key.</span></span>
- <span data-ttu-id="1e567-1117">**secret_key_len** 宛先の秘密キー長へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1117">**secret_key_len** Pointer to destination secret key length.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-1118">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-1118">Return Values</span></span>

- <span data-ttu-id="1e567-1119">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-1119">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-1120">**NX_LWM2M_CLIENT_NOT_FOUND** セキュリティ オブジェクト インスタンスがありません。</span><span class="sxs-lookup"><span data-stu-id="1e567-1120">**NX_LWM2M_CLIENT_NOT_FOUND** There is no security Object instance.</span></span>
- <span data-ttu-id="1e567-1121">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-1121">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-1122">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-1122">Allowed From</span></span>

<span data-ttu-id="1e567-1123">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-1123">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-1124">例</span><span class="sxs-lookup"><span data-stu-id="1e567-1124">Example</span></span>

```c
/* Get the register information.  */
status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_length, &security_mode, &pub_key_or_id, &pub_key_or_id_len, NX_NULL, NX_NULL, &secret_key, &secret_key_len);

/* If status is NX_SUCCESS, the register information was successfully gotten.  */
```

## <a name="nx_lwm2m_client_session_update"></a><span data-ttu-id="1e567-1125">nx_lwm2m_client_session_update</span><span class="sxs-lookup"><span data-stu-id="1e567-1125">nx_lwm2m_client_session_update</span></span>

<span data-ttu-id="1e567-1126">LWM2M サーバーとのセッションを更新します。</span><span class="sxs-lookup"><span data-stu-id="1e567-1126">Updates a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-1127">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-1127">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-1128">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-1128">Description</span></span>

<span data-ttu-id="1e567-1129">このサービスを使用すると、LWM2M サーバーに対して "更新" 操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-1129">This service performs an ‘Update’ operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-1130">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-1130">Parameters</span></span>

- <span data-ttu-id="1e567-1131">**session_ptr** LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1131">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-1132">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-1132">Return Values</span></span>

- <span data-ttu-id="1e567-1133">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-1133">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-1134">**NX_LWM2M_CLIENT_NOT_REGISTERED** クライアントがサーバーに登録されていません。</span><span class="sxs-lookup"><span data-stu-id="1e567-1134">**NX_LWM2M_CLIENT_NOT_REGISTERED** The client is not registered to the server.</span></span>
- <span data-ttu-id="1e567-1135">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-1135">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-1136">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-1136">Allowed From</span></span>

<span data-ttu-id="1e567-1137">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-1137">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-1138">例</span><span class="sxs-lookup"><span data-stu-id="1e567-1138">Example</span></span>

```c
/* Update a session.  */
status = nx_lwm2m_client_session_update(&session);

/* If status is NX_SUCCESS, a session was successfully updated.  */
```

## <a name="nx_lwm2m_client_unlock"></a><span data-ttu-id="1e567-1139">nx_lwm2m_client_unlock</span><span class="sxs-lookup"><span data-stu-id="1e567-1139">nx_lwm2m_client_unlock</span></span>

<span data-ttu-id="1e567-1140">LWM2M クライアントをロック解除します。</span><span class="sxs-lookup"><span data-stu-id="1e567-1140">Unlocks a LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="1e567-1141">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="1e567-1141">Prototype</span></span>

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="1e567-1142">説明</span><span class="sxs-lookup"><span data-stu-id="1e567-1142">Description</span></span>

<span data-ttu-id="1e567-1143">このサービスを使用すると、***nx_lwm2m_client_unlock*** の呼び出しによって以前にロックされていた LWM2M クライアントのロックが解除されます。</span><span class="sxs-lookup"><span data-stu-id="1e567-1143">This service unlocks the LWM2M Client previously locked by a call to ***nx_lwm2m_client_unlock***.</span></span>

### <a name="parameters"></a><span data-ttu-id="1e567-1144">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e567-1144">Parameters</span></span>

- <span data-ttu-id="1e567-1145">**client_ptr** LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1e567-1145">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="1e567-1146">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e567-1146">Return Values</span></span>

- <span data-ttu-id="1e567-1147">**NX_SUCCESS** 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="1e567-1147">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="1e567-1148">**NX_PTR_ERROR** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1e567-1148">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1e567-1149">許可元</span><span class="sxs-lookup"><span data-stu-id="1e567-1149">Allowed From</span></span>

<span data-ttu-id="1e567-1150">スレッド、初期化</span><span class="sxs-lookup"><span data-stu-id="1e567-1150">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="1e567-1151">例</span><span class="sxs-lookup"><span data-stu-id="1e567-1151">Example</span></span>

```c
/* Unlock lwm2m client.  */
status = nx_lwm2m_client_unlock(&lwm2m_client);

/* If status is NX_SUCCESS, unlock lwm2m client successfully.  */
```