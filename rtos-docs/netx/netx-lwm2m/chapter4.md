---
title: 第 4 章 - Azure RTOS NetX LWM2M サービスの説明
description: この章では、すべての Azure RTOS NetX LWM2M サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5a402790387c2720db304fe93d74252494d7638
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811489"
---
# <a name="chapter-4---description-of-azure-rtos-netx-lwm2m-services"></a><span data-ttu-id="26a3a-103">第 4 章 - Azure RTOS NetX LWM2M サービスの説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-103">Chapter 4 - Description of Azure RTOS NetX LWM2M services</span></span>

<span data-ttu-id="26a3a-104">この章では、すべての Azure RTOS NetX LWM2M サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="26a3a-104">This chapter contains a description of all Azure RTOS NetX LWM2M services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="26a3a-105">次の API の説明の「戻り値」セクションでは、**太字** の値が API のエラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="26a3a-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

### <a name="lwm2m-client-management"></a><span data-ttu-id="26a3a-106">LWM2M クライアント管理</span><span class="sxs-lookup"><span data-stu-id="26a3a-106">LWM2M Client Management</span></span>

- <span data-ttu-id="26a3a-107">**nx_lwm2m_client_create**: *LWM2M クライアントを作成します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-107">**nx_lwm2m_client_create**: *Create LWM2M Client*</span></span>
- <span data-ttu-id="26a3a-108">**nx_lwm2m_client_delete**: *LWM2M クライアントを削除します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-108">**nx_lwm2m_client_delete**: *Delete LWM2M Client*</span></span>
- <span data-ttu-id="26a3a-109">**nx_lwm2m_client_lock**: *LWM2M クライアントをロックします*</span><span class="sxs-lookup"><span data-stu-id="26a3a-109">**nx_lwm2m_client_lock**: *Lock LWM2M Client*</span></span>
- <span data-ttu-id="26a3a-110">**nx_lwm2m_client_object_add**: *LWM2M クライアントにオブジェクトの実装を追加します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-110">**nx_lwm2m_client_object_add**: *Add Object implementation to the LWM2M Client*</span></span>
- <span data-ttu-id="26a3a-111">**nx_lwm2m_client_unlock**: *LWM2M クライアントをロック解除します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-111">**nx_lwm2m_client_unlock**: *Unlock LWM2M Client*</span></span>

### <a name="lwm2m-client-session-management"></a><span data-ttu-id="26a3a-112">LWM2M クライアント セッション管理</span><span class="sxs-lookup"><span data-stu-id="26a3a-112">LWM2M Client Session Management</span></span>

- <span data-ttu-id="26a3a-113">**nx_lwm2m_client_session_bootstrap**: *ブートストラップ サーバーとのセッションを開始します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-113">**nx_lwm2m_client_session_bootstrap**: *Start a session with a Bootstrap Server*</span></span>
- <span data-ttu-id="26a3a-114">**nx_lwm2m_client_session_bootstrap_dtls**: *ブートストラップ サーバーとのセキュリティで保護されたセッションを開始します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-114">**nx_lwm2m_client_session_bootstrap_dtls**: *Start a secure session with a Bootstrap Server*</span></span>
- <span data-ttu-id="26a3a-115">**nx_lwm2m_client_session_create**: *LWM2M クライアント セッションを作成します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-115">**nx_lwm2m_client_session_create**: *Create LWM2M Client Session*</span></span>
- <span data-ttu-id="26a3a-116">**nx_lwm2m_client_session_delete**: *LWM2M クライアント セッションを削除します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-116">**nx_lwm2m_client_session_delete**: *Delete LWM2M Client Session*</span></span>
- <span data-ttu-id="26a3a-117">**nx_lwm2m_client_session_deregister**: *LWM2M サーバーとのセッションを終了します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-117">**nx_lwm2m_client_session_deregister**: *Terminate a session with a LWM2M Server*</span></span>
- <span data-ttu-id="26a3a-118">**nx_lwm2m_client_session_error_get**: *セッションの最後のエラーを取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-118">**nx_lwm2m_client_session_error_get**: *Get last error of a session*</span></span>
- <span data-ttu-id="26a3a-119">**nx_lwm2m_client_session_register**: *LWM2M Server とのセッションを開始します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-119">**nx_lwm2m_client_session_register**: *Start a session with a LWM2M Server*</span></span>
- <span data-ttu-id="26a3a-120">**nx_lwm2m_client_session_register_dtls**: *LWM2M サーバーとのセキュアなセッションを開始します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-120">**nx_lwm2m_client_session_register_dtls**: *Start a secure session with a LWM2M Server*</span></span>
- <span data-ttu-id="26a3a-121">**nx_lwm2m_client_session_update**: *LWM2M サーバーとのセッションを更新します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-121">**nx_lwm2m_client_session_update**: *Update a session with a LWM2M Server*</span></span>

### <a name="security-object-implementation"></a><span data-ttu-id="26a3a-122">セキュリティ オブジェクトの実装</span><span class="sxs-lookup"><span data-stu-id="26a3a-122">Security Object Implementation</span></span>

- <span data-ttu-id="26a3a-123">**nx_lwm2m_client_security_key_callbacks_set**: *セキュリティ キー管理コールバックを設定します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-123">**nx_lwm2m_client_security_key_callbacks_set**: *Set security key management callbacks*</span></span>

### <a name="device-object-implementation"></a><span data-ttu-id="26a3a-124">デバイス オブジェクトの実装</span><span class="sxs-lookup"><span data-stu-id="26a3a-124">Device Object Implementation</span></span>

- <span data-ttu-id="26a3a-125">**nx_lwm2m_client_device_callbacks_set**: *デバイス オブジェクトのアプリケーションのコールバックを設定します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-125">**nx_lwm2m_client_device_callbacks_set**: *Set Device Object application callbacks*</span></span>
- <span data-ttu-id="26a3a-126">**nx_lwm2m_client_device_error_push**: *デバイス オブジェクトにエラー コードを追加します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-126">**nx_lwm2m_client_device_error_push**: *Add error code to Device Object*</span></span>
- <span data-ttu-id="26a3a-127">**nx_lwm2m_client_device_error_reset**: *デバイス オブジェクトのエラー コードをリセットします*</span><span class="sxs-lookup"><span data-stu-id="26a3a-127">**nx_lwm2m_client_device_error_reset**: *Reset error codes of Device Object*</span></span>
- <span data-ttu-id="26a3a-128">**nx_lwm2m_client_device_resource_changed**: *デバイス オブジェクト リソースのシグナルを変更します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-128">**nx_lwm2m_client_device_resource_changed**: *Signal change of Device Object resource*</span></span>

### <a name="custom-objects-implementation"></a><span data-ttu-id="26a3a-129">カスタム オブジェクトの実装</span><span class="sxs-lookup"><span data-stu-id="26a3a-129">Custom Objects Implementation</span></span>

- <span data-ttu-id="26a3a-130">**nx_lwm2m_object_resource_changed**: *オブジェクト インスタンスのリソース値のシグナルを変更します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-130">**nx_lwm2m_object_resource_changed**: *Signal change of a resource value of an Object Instance*</span></span>

### <a name="local-device-management"></a><span data-ttu-id="26a3a-131">ローカル デバイスの管理</span><span class="sxs-lookup"><span data-stu-id="26a3a-131">Local Device Management</span></span>

- <span data-ttu-id="26a3a-132">**nx_lwm2m_client_object_create**: *新しいオブジェクト インスタンスを作成します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-132">**nx_lwm2m_client_object_create**: *Create a new Object Instance*</span></span>
- <span data-ttu-id="26a3a-133">**nx_lwm2m_client_object_delete**: *オブジェクト インスタンスを削除します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-133">**nx_lwm2m_client_object_delete**: *Delete an Object Instance*</span></span>
- <span data-ttu-id="26a3a-134">**nx_lwm2m_client_object_discover**: *オブジェクト インスタンスのリソースを検出します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-134">**nx_lwm2m_client_object_discover**: *Discover resources of an Object Instance*</span></span>
- <span data-ttu-id="26a3a-135">**nx_lwm2m_client_object_execute**: *オブジェクト インスタンスのリソースを実行します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-135">**nx_lwm2m_client_object_execute**: *Execute resource of an Object Instance*</span></span>
- <span data-ttu-id="26a3a-136">**nx_lwm2m_client_object_get_next**: *LWM2M クライアントによって実装されているオブジェクトのリストを取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-136">**nx_lwm2m_client_object_get_next**: *Get the list of Objects implemented by the LWM2M Client*</span></span>
- <span data-ttu-id="26a3a-137">**nx_lwm2m_client_object_instance_get_next**: *オブジェクトのインスタンスのリストを取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-137">**nx_lwm2m_client_object_instance_get_next**: *Get the list of Instances of an Object*</span></span>
- <span data-ttu-id="26a3a-138">**nx_lwm2m_client_object_read**: *オブジェクト インスタンスのリソース値を読み取ります*</span><span class="sxs-lookup"><span data-stu-id="26a3a-138">**nx_lwm2m_client_object_read**: *Read resources values of an Object Instance*</span></span>
- <span data-ttu-id="26a3a-139">**nx_lwm2m_client_object_write**: *オブジェクト インスタンスのリソース値を変更します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-139">**nx_lwm2m_client_object_write**: *Change resources values of an Object instance*</span></span>

### <a name="resources-values-decoding"></a><span data-ttu-id="26a3a-140">リソース値のデコード</span><span class="sxs-lookup"><span data-stu-id="26a3a-140">Resources Values Decoding</span></span>

- <span data-ttu-id="26a3a-141">**nx_lwm2m_resource_get_boolean**: *ブール型リソースの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-141">**nx_lwm2m_resource_get_boolean**: *Get the value of a Boolean Resource*</span></span>
- <span data-ttu-id="26a3a-142">**nx_lwm2m_resource_get_float32**: *32 ビット浮動小数点リソースの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-142">**nx_lwm2m_resource_get_float32**: *Get the value of a 32-bit Floating Point Resource*</span></span>
- <span data-ttu-id="26a3a-143">**nx_lwm2m_resource_get_float64**: *64 ビット浮動小数点リソースの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-143">**nx_lwm2m_resource_get_float64**: *Get the value of a 64-bit Floating Point Resource*</span></span>
- <span data-ttu-id="26a3a-144">**nx_lwm2m_resource_get_integer32**: *32 ビット整数リソースの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-144">**nx_lwm2m_resource_get_integer32**: *Get the value of a 32-Bit Integer Resource*</span></span>
- <span data-ttu-id="26a3a-145">**nx_lwm2m_resource_get_integer64**: *64 ビット整数リソースの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-145">**nx_lwm2m_resource_get_integer64**: *Get the value of a 64-Bit Integer Resource*</span></span>
- <span data-ttu-id="26a3a-146">**nx_lwm2m_resource_get_objlnk**: *オブジェクト リンク リソースの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-146">**nx_lwm2m_resource_get_objlnk**: *Get the value of an Object Link Resource*</span></span>
- <span data-ttu-id="26a3a-147">**nx_lwm2m_resource_get_opaque**: *非透過リソースの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-147">**nx_lwm2m_resource_get_opaque**: *Get the value of an Opaque Resource*</span></span>
- <span data-ttu-id="26a3a-148">**nx_lwm2m_resource_get_string**: *文字列リソースの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-148">**nx_lwm2m_resource_get_string**: *Get the value of a String Resource*</span></span>
- <span data-ttu-id="26a3a-149">**nx_lwm2m_resource_multiple_get_boolean**: *ブール型リソースの複数リソース インスタンスの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-149">**nx_lwm2m_resource_multiple_get_boolean**: *Get the value of a Boolean Resource Multiple Resource Instance*</span></span>
- <span data-ttu-id="26a3a-150">**nx_lwm2m_resource_multiple_get_float32**: *32 ビット浮動小数点の複数リソース インスタンスの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-150">**nx_lwm2m_resource_multiple_get_float32**: *Get the value of a 32-bit Floating Point Multiple Resource Instance*</span></span>
- <span data-ttu-id="26a3a-151">**nx_lwm2m_resource_multiple_get_float64**: *64 ビット浮動小数点の複数リソース インスタンスの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-151">**nx_lwm2m_resource_multiple_get_float64**: *Get the value of a 64-bit Floating Point Multiple Resource Instance*</span></span>
- <span data-ttu-id="26a3a-152">**nx_lwm2m_resource_multiple_get_integer32**: *32 ビット整数の複数リソース インスタンスの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-152">**nx_lwm2m_resource_multiple_get_integer32**: *Get the value of a 32-Bit Integer Multiple Resource Instance*</span></span>
- <span data-ttu-id="26a3a-153">**nx_lwm2m_resource_multiple_get_integer64**: *64 ビット整数の複数リソース インスタンスの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-153">**nx_lwm2m_resource_multiple_get_integer64**: *Get the value of a 64-Bit Integer Multiple Resource Instance*</span></span>
- <span data-ttu-id="26a3a-154">**nx_lwm2m_resource_multiple_get_objlnk**: *オブジェクト リンクの複数リソース インスタンスの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-154">**nx_lwm2m_resource_multiple_get_objlnk**: *Get the value of an Object Link Multiple Resource Instance*</span></span>
- <span data-ttu-id="26a3a-155">**nx_lwm2m_resource_multiple_get_opaque**: *非透過複数リソース インスタンスの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-155">**nx_lwm2m_resource_multiple_get_opaque**: *Get the value of an Opaque Multiple Resource Instance*</span></span>
- <span data-ttu-id="26a3a-156">**nx_lwm2m_resource_multiple_get_string**: *文字列の複数リソース インスタンスの値を取得します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-156">**nx_lwm2m_resource_multiple_get_string**: *Get the value of a String Multiple Resource Instance*</span></span>

### <a name="firmware-update-object"></a><span data-ttu-id="26a3a-157">ファームウェア更新オブジェクト</span><span class="sxs-lookup"><span data-stu-id="26a3a-157">Firmware Update Object</span></span>

- <span data-ttu-id="26a3a-158">**nx_lwm2m_firmware_create**: *ファームウェア更新オブジェクトを作成します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-158">**nx_lwm2m_firmware_create**: *Create Firmware Update Object*</span></span>
- <span data-ttu-id="26a3a-159">**nx_lwm2m_firmware_package_info_set**: *ファームウェア更新パッケージの情報を設定します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-159">**nx_lwm2m_firmware_package_info_set**: *Set Firmware Update Package Information*</span></span>
- <span data-ttu-id="26a3a-160">**nx_lwm2m_firmware_result_set**: *ファームウェアの更新結果を設定します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-160">**nx_lwm2m_firmware_result_set**: *Set Firmware Update Result*</span></span>
- <span data-ttu-id="26a3a-161">**nx_lwm2m_firmware_state_set**: *ファームウェアの更新状態を設定します*</span><span class="sxs-lookup"><span data-stu-id="26a3a-161">**nx_lwm2m_firmware_state_set**: *Set Firmware Update State*</span></span>

## <a name="nx_lwm2m_client_create"></a><span data-ttu-id="26a3a-162">nx_lwm2m_client_create</span><span class="sxs-lookup"><span data-stu-id="26a3a-162">nx_lwm2m_client_create</span></span>

<span data-ttu-id="26a3a-163">LWM2M クライアントを作成します</span><span class="sxs-lookup"><span data-stu-id="26a3a-163">Create LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-164">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-164">Prototype</span></span>

```c
UINT nx_lwm2m_client_create(NX_LWM2M_CLIENT *client_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr, UINT local_port, const CHAR *name_ptr,
    const CHAR *msisdn_ptr, UCHAR binding_modes, VOID *stack_ptr, ULONG stack_size);
```

### <a name="description"></a><span data-ttu-id="26a3a-165">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-165">Description</span></span>

<span data-ttu-id="26a3a-166">このサービスを使用すると、専用の ThreadX スレッドのコンテキスト内で実行される LWM2M クライアント インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-166">This service creates a LWM2M Client instance, which runs in the context of its own ThreadX thread.</span></span>

<span data-ttu-id="26a3a-167">LWM2M クライアントには、次の OMA LWM2M オブジェクトが実装されています: セキュリティ (0)、サーバー (1)、アクセス制御 (2)、デバイス (3)。</span><span class="sxs-lookup"><span data-stu-id="26a3a-167">The LWM2M Client implements the following OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="26a3a-168">その他のオブジェクトの実装は、アプリケーションによって追加される必要があります。</span><span class="sxs-lookup"><span data-stu-id="26a3a-168">The other objects implementations must be added by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-169">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-169">Parameters</span></span>

- <span data-ttu-id="26a3a-170">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-170">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="26a3a-171">**ip_ptr**: 以前に作成された IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-171">**ip_ptr**: Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="26a3a-172">**packet_pool_ptr**: この LWM2M クライアントの既定のパケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-172">**packet_pool_ptr**: Pointer to the default packet pool for this LWM2M Client.</span></span>
- <span data-ttu-id="26a3a-173">**local_port**: セキュリティで保護されていない通信に使用されるローカル UDP ポート。</span><span class="sxs-lookup"><span data-stu-id="26a3a-173">**local_port**: The local UDP port used for non-secure communication.</span></span>
- <span data-ttu-id="26a3a-174">**name_ptr**: LWM2M クライアント エンドポイント名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-174">**name_ptr**: Pointer to LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="26a3a-175">**msisdn_ptr**: SMS バインディングで使用するために LWM2M クライアントに到達できる MSISDN へのポインター。SMS バインディングがサポートされていない場合は、NULL にすることができます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-175">**msisdn_ptr**: Pointer to the MSISDN where the LWM2M Client can be reached for use with the SMS binding, can be NULL if SMS binding is not supported.</span></span>
- <span data-ttu-id="26a3a-176">**binding_modes**: LWM2M クライアントでサポートされているバインディングとモードは、NX_LWM2M_BINDING_U、NX_LWM2M_BINDING_UQ、NX_LWM2M_BINDING_S、および NX_LWM2M_BINDING_SQ フラグの組み合わせになっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="26a3a-176">**binding_modes**: The binding and modes supported by the LWM2M Client, must be a combination of NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S and NX_LWM2M_BINDING_SQ flags.</span></span>
- <span data-ttu-id="26a3a-177">**stack_ptr**: LWM2M クライアント スレッド スタック領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-177">**stack_ptr**: Pointer to LWM2M Client thread stack area.</span></span>
- <span data-ttu-id="26a3a-178">**stack_size**: LWM2M クライアント スレッド スタック サイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-178">**stack_size**: The LWM2M Client thread stack size.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-179">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-179">Return Values</span></span>

- <span data-ttu-id="26a3a-180">**NX_SUCCESS**: LWM2M クライアントの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-180">**NX_SUCCESS**: The LWM2M Client has been successfully created.</span></span>
- <span data-ttu-id="26a3a-181">**NX_LWM2M_ERROR**: LWM2M クライアントの作成エラー。</span><span class="sxs-lookup"><span data-stu-id="26a3a-181">**NX_LWM2M_ERROR**: LWM2M Client create error.</span></span>
- <span data-ttu-id="26a3a-182">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-182">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_delete"></a><span data-ttu-id="26a3a-183">nx_lwm2m_client_delete</span><span class="sxs-lookup"><span data-stu-id="26a3a-183">nx_lwm2m_client_delete</span></span>

<span data-ttu-id="26a3a-184">LWM2M クライアントを削除します</span><span class="sxs-lookup"><span data-stu-id="26a3a-184">Delete LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-185">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-185">Prototype</span></span>

```c
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-186">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-186">Description</span></span>

<span data-ttu-id="26a3a-187">このサービスを使用すると、以前に作成された LWM2M クライアント インスタンスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-187">This service deletes a previously created LWM2M Client instance.</span></span>

<span data-ttu-id="26a3a-188">現在クライアントにアタッチされているすべてのセッションも、この呼び出しによって削除されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-188">All sessions currently attached the client are also deleted by this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-189">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-189">Parameters</span></span>

- <span data-ttu-id="26a3a-190">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-190">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-191">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-191">Return Values</span></span>

- <span data-ttu-id="26a3a-192">**NX_SUCCESS**: LWM2M クライアントの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-192">**NX_SUCCESS**: The LWM2M Client has been successfully deleted.</span></span>
- <span data-ttu-id="26a3a-193">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-193">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_callbacks_set"></a><span data-ttu-id="26a3a-194">nx_lwm2m_client_device_callbacks_set</span><span class="sxs-lookup"><span data-stu-id="26a3a-194">nx_lwm2m_client_device_callbacks_set</span></span>

<span data-ttu-id="26a3a-195">デバイス オブジェクト アプリケーションのコールバックを設定します</span><span class="sxs-lookup"><span data-stu-id="26a3a-195">Set Device Object application callbacks</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-196">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-196">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_READ_CALLBACK read_callback,
    NX_LWM2M_CLIENT_DEVICE_DISCOVER_CALLBACK discover_callback,
    NX_LWM2M_CLIENT_DEVICE_WRITE_CALLBACK write_callback,
    NX_LWM2M_CLIENT_DEVICE_EXECUTE_CALLBACK execute_callback);
```

### <a name="description"></a><span data-ttu-id="26a3a-197">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-197">Description</span></span>

<span data-ttu-id="26a3a-198">このサービスを使用すると、LWM2M クライアントによって処理されない LWM2M デバイス オブジェクト リソースの操作を実装するためのアプリケーション コールバックがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-198">This service installs the application callbacks for implementing operations on the LWM2M Device Object resources that are not handled by the LWM2M Client.</span></span>

<span data-ttu-id="26a3a-199">LWM2M クライアントは、次のリソースを実装します: エラー コード (11)、リセット エラー コード (12)、サポートされているバインドとモード (16)。他のリソースに対する操作は、アプリケーションにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-199">The LWM2M Client implements the following resources : Error Code (11), Reset Error Code (12) and Supported Binding and Modes (16), operations to the other resources are redirected to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-200">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-200">Parameters</span></span>

- <span data-ttu-id="26a3a-201">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-201">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="26a3a-202">**read_callback**: "Read" メソッドのコールバック。</span><span class="sxs-lookup"><span data-stu-id="26a3a-202">**read_callback**: The 'Read' method callback.</span></span>
- <span data-ttu-id="26a3a-203">**discover_callback**: "Discover" メソッドのコールバック。</span><span class="sxs-lookup"><span data-stu-id="26a3a-203">**discover_callback**: The 'Discover' method callback.</span></span>
- <span data-ttu-id="26a3a-204">**write_callback**: "Write" メソッドのコールバック。</span><span class="sxs-lookup"><span data-stu-id="26a3a-204">**write_callback**: The 'Write' method callback.</span></span>
- <span data-ttu-id="26a3a-205">**execute_callback**: "Execute" メソッドのコールバック。</span><span class="sxs-lookup"><span data-stu-id="26a3a-205">**execute_callback**: The 'Execute' method callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-206">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-206">Return Values</span></span>

- <span data-ttu-id="26a3a-207">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-207">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-208">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-208">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_error_push"></a><span data-ttu-id="26a3a-209">nx_lwm2m_client_device_error_push</span><span class="sxs-lookup"><span data-stu-id="26a3a-209">nx_lwm2m_client_device_error_push</span></span>

<span data-ttu-id="26a3a-210">デバイス オブジェクトにエラー コードを追加します</span><span class="sxs-lookup"><span data-stu-id="26a3a-210">Add error code to Device Object</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-211">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-211">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_push(NX_LWM2M_CLIENT *client_ptr, UCHAR code);
```

### <a name="description"></a><span data-ttu-id="26a3a-212">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-212">Description</span></span>

<span data-ttu-id="26a3a-213">このサービスを使用すると、オブジェクト デバイスのエラー コード (11) リソースに新しいインスタンスが追加されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-213">This service adds a new instance to the Error Code (11) resource of the Object Device.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-214">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-214">Parameters</span></span>

- <span data-ttu-id="26a3a-215">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-215">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="26a3a-216">**code**: 新しいエラー コード。</span><span class="sxs-lookup"><span data-stu-id="26a3a-216">**code**: The new error code.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-217">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-217">Return Values</span></span>

- <span data-ttu-id="26a3a-218">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-218">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-219">**NX_LWM2M_BUFFER_TOO_SMALL**: 格納されているエラー コードの最大数に達しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-219">**NX_LWM2M_BUFFER_TOO_SMALL**: The maximum number of stored error codes has been reached.</span></span>
- <span data-ttu-id="26a3a-220">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-220">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_error_reset"></a><span data-ttu-id="26a3a-221">nx_lwm2m_client_device_error_reset</span><span class="sxs-lookup"><span data-stu-id="26a3a-221">nx_lwm2m_client_device_error_reset</span></span>

<span data-ttu-id="26a3a-222">デバイス オブジェクトのエラー コードをリセットします</span><span class="sxs-lookup"><span data-stu-id="26a3a-222">Reset error codes of Device Object</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-223">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-223">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-224">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-224">Description</span></span>

<span data-ttu-id="26a3a-225">このサービスを使用すると、すべてのエラー コード リソース インスタンスがデバイス オブジェクトから削除されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-225">This service deletes all error code resource instances from the Device Object.</span></span> <span data-ttu-id="26a3a-226">これは、リソース リセット エラー コード (12) を実行することと同じです。</span><span class="sxs-lookup"><span data-stu-id="26a3a-226">This is equivalent to executing the resource Reset Error Code (12).</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-227">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-227">Parameters</span></span>

- <span data-ttu-id="26a3a-228">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-228">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-229">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-229">Return Values</span></span>

- <span data-ttu-id="26a3a-230">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-230">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-231">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-231">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_resource_changed"></a><span data-ttu-id="26a3a-232">nx_lwm2m_client_device_resource_changed</span><span class="sxs-lookup"><span data-stu-id="26a3a-232">nx_lwm2m_client_device_resource_changed</span></span>

<span data-ttu-id="26a3a-233">デバイス オブジェクト リソースのシグナルを変更します</span><span class="sxs-lookup"><span data-stu-id="26a3a-233">Signal change of Device Object resource</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-234">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-234">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_resource_changed(NX_LWM2M_CLIENT *client_ptr,
                                    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="26a3a-235">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-235">Description</span></span>

<span data-ttu-id="26a3a-236">このサービスは、アプリケーションによって、オブジェクト デバイスのリソースが変更されたことを LWM2M クライアントに通知するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-236">The service is used by the application to signal to the LWM2M Client that a resource of the Object Device has changed.</span></span> <span data-ttu-id="26a3a-237">LWM2M クライアントは、リソースが LWM2M サーバーによって監視されている場合に通知を送信します。</span><span class="sxs-lookup"><span data-stu-id="26a3a-237">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-238">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-238">Parameters</span></span>

- <span data-ttu-id="26a3a-239">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-239">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="26a3a-240">**resource**: 変更されたリソースを記述する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-240">**resource**: Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-241">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-241">Return Values</span></span>

- <span data-ttu-id="26a3a-242">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-242">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-243">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-243">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_lock"></a><span data-ttu-id="26a3a-244">nx_lwm2m_client_lock</span><span class="sxs-lookup"><span data-stu-id="26a3a-244">nx_lwm2m_client_lock</span></span>

<span data-ttu-id="26a3a-245">LWM2M クライアントをロックします</span><span class="sxs-lookup"><span data-stu-id="26a3a-245">Lock LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-246">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-246">Prototype</span></span>

```c
UINT nx_lwm2m_client_lock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-247">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-247">Description</span></span>

<span data-ttu-id="26a3a-248">このサービスを使用すると、サーバーまたは別のアプリケーション スレッドからの LWM2M オブジェクトへの同時アクセスを防ぐために、LWM2M クライアントがロックされます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-248">This service locks the LWM2M Client to prevent concurent access to the LWM2M objects from the servers or another application thread.</span></span>

<span data-ttu-id="26a3a-249">LWM2M クライアントが現在別のスレッドによってロックされている場合、この関数は LWM2M クライアントがロック解除されるまでブロックします。</span><span class="sxs-lookup"><span data-stu-id="26a3a-249">If the LWM2M Client is currently locked by another thread, the function will block until the LWM2M Client is unlocked.</span></span>

<span data-ttu-id="26a3a-250">nx_lwm2m_client_lock()/nx_lwm2m_client_unlock() ペアへの呼び出しは入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-250">Calls to nx_lwm2m_client_lock()/nx_lwm2m_client_unlock() pairs can be nested.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-251">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-251">Parameters</span></span>

- <span data-ttu-id="26a3a-252">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-252">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-253">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-253">Return Values</span></span>

- <span data-ttu-id="26a3a-254">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-254">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-255">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-255">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_add"></a><span data-ttu-id="26a3a-256">nx_lwm2m_client_object_add</span><span class="sxs-lookup"><span data-stu-id="26a3a-256">nx_lwm2m_client_object_add</span></span>

<span data-ttu-id="26a3a-257">オブジェクトの実装を LWM2M クライアントに追加します。</span><span class="sxs-lookup"><span data-stu-id="26a3a-257">Add Object implementation to the LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-258">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-258">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_add(NX_LWM2M_CLIENT *client_ptr,
                                NX_LWM2M_OBJECT *object_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-259">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-259">Description</span></span>

<span data-ttu-id="26a3a-260">このサービスを使用すると、新しいオブジェクトの実装が LWM2M クライアントに追加されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-260">This service adds a new Object implementation to the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-261">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-261">Parameters</span></span>

- <span data-ttu-id="26a3a-262">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-262">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="26a3a-263">**object_ptr**: オブジェクトの実装を定義する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-263">**object_ptr**: Pointer to the structure defining the Object implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-264">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-264">Return Values</span></span>

- <span data-ttu-id="26a3a-265">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-265">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-266">**NX_LWM2M_ALREADY_EXIST**: オブジェクト ID は既に存在しています。</span><span class="sxs-lookup"><span data-stu-id="26a3a-266">**NX_LWM2M_ALREADY_EXIST**: The Object ID already exists.</span></span>
- <span data-ttu-id="26a3a-267">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-267">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_create"></a><span data-ttu-id="26a3a-268">nx_lwm2m_client_object_create</span><span class="sxs-lookup"><span data-stu-id="26a3a-268">nx_lwm2m_client_object_create</span></span>

<span data-ttu-id="26a3a-269">新しいオブジェクト インスタンスを作成します</span><span class="sxs-lookup"><span data-stu-id="26a3a-269">Create a new Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-270">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-270">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_create(NX_LWM2M_CLIENT *client_ptr,
            NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr,
            UINT num_values, const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-271">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-271">Description</span></span>

<span data-ttu-id="26a3a-272">このサービスを使用すると、LWM2M クライアントのオブジェクトに対して "作成" 操作を実行して、新しいオブジェクト インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-272">This service performs a 'Create' operation on an Object of the LWM2M Client to create a new Object Instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-273">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-273">Parameters</span></span>

- <span data-ttu-id="26a3a-274">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-274">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="26a3a-275">**object_id**: オブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="26a3a-275">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="26a3a-276">**instance_id_ptr**: 新しいインスタンスの ID へのポインター。LWM2M クライアントによってインスタンス ID を割り当てる必要がある場合は、NULL にすることができます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-276">**instance_id_ptr**: Pointer to the ID of the new instance, can be NULL if the LWM2M Client must assign an Instance ID.</span></span> <span data-ttu-id="26a3a-277">ID が予約値 65535 の場合、LWM2M クライアントによってインスタンス ID が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-277">If the ID is the reserved value 65535 the LWM2M Client will assign an Instance ID.</span></span> <span data-ttu-id="26a3a-278">NULL 以外の場合は、割り当てられた ID が呼び出しの後に返されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-278">If not NULL the assigned ID is returned after the call.</span></span>
- <span data-ttu-id="26a3a-279">**num_values**: 設定する値の数。</span><span class="sxs-lookup"><span data-stu-id="26a3a-279">**num_values**: The number of values to set.</span></span>
- <span data-ttu-id="26a3a-280">**values_ptr**: 新しいオブジェクト インスタンスを初期化するためのリソース値の配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-280">**values_ptr**: Pointer to an array of resource values to initialize the new Object Instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-281">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-281">Return Values</span></span>

- <span data-ttu-id="26a3a-282">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-282">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-283">**NX_LWM2M_ALREADY_EXIST**: オブジェクト インスタンス ID は既に存在しています。</span><span class="sxs-lookup"><span data-stu-id="26a3a-283">**NX_LWM2M_ALREADY_EXIST**: The Object Instance ID already exists.</span></span>
- <span data-ttu-id="26a3a-284">**NX_LWM2M_METHOD_NOT_ALLOWED**: オブジェクトはインスタンスの作成をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-284">**NX_LWM2M_METHOD_NOT_ALLOWED**: The Object doesn't support instance creation.</span></span>
- <span data-ttu-id="26a3a-285">**NX_LWM2M_NO_MEMORY**: 新しいインスタンスを格納するためのメモリを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-285">**NX_LWM2M_NO_MEMORY**: Cannot allocate memory to store the new instance.</span></span>
- <span data-ttu-id="26a3a-286">**NX_LWM2M_NOT_FOUND**: オブジェクト ID が存在していません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-286">**NX_LWM2M_NOT_FOUND**: The Object ID doesn't exist.</span></span>
- <span data-ttu-id="26a3a-287">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-287">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_delete"></a><span data-ttu-id="26a3a-288">nx_lwm2m_client_object_delete</span><span class="sxs-lookup"><span data-stu-id="26a3a-288">nx_lwm2m_client_object_delete</span></span>

<span data-ttu-id="26a3a-289">オブジェクト インスタンスを削除します</span><span class="sxs-lookup"><span data-stu-id="26a3a-289">Delete an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-290">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-290">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_delete(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="26a3a-291">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-291">Description</span></span>

<span data-ttu-id="26a3a-292">このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンスの "削除" 操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-292">This service performs a 'Delete' operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-293">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-293">Parameters</span></span>

- <span data-ttu-id="26a3a-294">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-294">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="26a3a-295">**object_id**: オブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="26a3a-295">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="26a3a-296">**instance_id**: オブジェクト インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="26a3a-296">**instance_id**: The Object Instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-297">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-297">Return Values</span></span>

- <span data-ttu-id="26a3a-298">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-298">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-299">**NX_LWM2M_METHOD_NOT_ALLOWED**: オブジェクトはインスタンスの削除をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-299">**NX_LWM2M_METHOD_NOT_ALLOWED**: The Object doesn't support instance deletion.</span></span>
- <span data-ttu-id="26a3a-300">**NX_LWM2M_NOT_FOUND**: オブジェクト ID またはオブジェクト インスタンス ID が存在していません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-300">**NX_LWM2M_NOT_FOUND**: The Object ID or Object Instance ID doesn't exist.</span></span>
- <span data-ttu-id="26a3a-301">NX_PTR_ERROR ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-301">NX_PTR_ERROR Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_discover"></a><span data-ttu-id="26a3a-302">nx_lwm2m_client_object_discover</span><span class="sxs-lookup"><span data-stu-id="26a3a-302">nx_lwm2m_client_object_discover</span></span>

<span data-ttu-id="26a3a-303">オブジェクト インスタンスのリソースを検出します</span><span class="sxs-lookup"><span data-stu-id="26a3a-303">Discover resources of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-304">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-304">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_discover(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT *num_resources_ptr, NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-305">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-305">Description</span></span>

<span data-ttu-id="26a3a-306">このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンスの "検出" 操作が実行されます。これにより、オブジェクトによって実装されたリソースのリストが返されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-306">This service performs a 'Discover' operation on an Object Instance of the LWM2M Client, this returns the list of resources implemented by the Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-307">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-307">Parameters</span></span>

- <span data-ttu-id="26a3a-308">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-308">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="26a3a-309">**object_id**: オブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="26a3a-309">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="26a3a-310">**instance_id**: オブジェクト インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="26a3a-310">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="26a3a-311">**num_resources_ptr**: 入力時は宛先バッファーのサイズ、出力時はバッファーに書き込まれた要素の数。</span><span class="sxs-lookup"><span data-stu-id="26a3a-311">**num_resources_ptr**: On input the size of the destination buffer, on output the number of elements writen to the buffer.</span></span>
- <span data-ttu-id="26a3a-312">**resources_ptr**: 宛先バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-312">**resources_ptr**: Pointer to the destination buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-313">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-313">Return Values</span></span>

- <span data-ttu-id="26a3a-314">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-314">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="26a3a-315">**NX_LWM2M_BUFFER_TOO_SMALL**: リソース バッファーが小さすぎて、リソースのリストを格納できません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-315">**NX_LWM2M_BUFFER_TOO_SMALL**: The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="26a3a-316">**NX_LWM2M_NOT_FOUND**: オブジェクト ID またはオブジェクト インスタンス ID が存在していません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-316">**NX_LWM2M_NOT_FOUND**: The Object ID or Object Instance ID doesn't exist.</span></span>
- <span data-ttu-id="26a3a-317">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-317">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_execute"></a><span data-ttu-id="26a3a-318">nx_lwm2m_client_object_execute</span><span class="sxs-lookup"><span data-stu-id="26a3a-318">nx_lwm2m_client_object_execute</span></span>

<span data-ttu-id="26a3a-319">オブジェクト インスタンスのリソースを実行します</span><span class="sxs-lookup"><span data-stu-id="26a3a-319">Execute resource of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-320">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-320">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_execute(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr, UINT arguments_length);
```

### <a name="description"></a><span data-ttu-id="26a3a-321">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-321">Description</span></span>

<span data-ttu-id="26a3a-322">このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンス リソースの "実行" 操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-322">This service performs the 'Execute' operation on an Object Instance Resource of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-323">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-323">Parameters</span></span>

- <span data-ttu-id="26a3a-324">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-324">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="26a3a-325">**object_id**: オブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="26a3a-325">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="26a3a-326">**instance_id**: オブジェクト インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="26a3a-326">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="26a3a-327">**resource_id**: リソース ID。</span><span class="sxs-lookup"><span data-stu-id="26a3a-327">**resource_id**: The Resource ID.</span></span>
- <span data-ttu-id="26a3a-328">**arguments_ptr**: 実行操作の引数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-328">**arguments_ptr**: Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="26a3a-329">arguments_length が 0 の場合は、NULL を指定できます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-329">Can be NULL if arguments_length is zero.</span></span>
- <span data-ttu-id="26a3a-330">**arguments_length**: 引数の長さ。</span><span class="sxs-lookup"><span data-stu-id="26a3a-330">**arguments_length**: The length of the arguments.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-331">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-331">Return Values</span></span>

- <span data-ttu-id="26a3a-332">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-332">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-333">**NX_LWM2M_METHOD_NOT_ALLOWED**: リソースは実行操作をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-333">**NX_LWM2M_METHOD_NOT_ALLOWED**: The resource doesn't support the execute operation.</span></span>
- <span data-ttu-id="26a3a-334">**NX_LWM2M_NOT_FOUND**: オブジェクト ID、オブジェクト インスタンス ID、またはリソース ID が存在していません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-334">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or the resource ID doesn't exist.</span></span>
- <span data-ttu-id="26a3a-335">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-335">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_get_next"></a><span data-ttu-id="26a3a-336">nx_lwm2m_client_object_get_next</span><span class="sxs-lookup"><span data-stu-id="26a3a-336">nx_lwm2m_client_object_get_next</span></span>

<span data-ttu-id="26a3a-337">LWM2M クライアントによって実装されたオブジェクトの一覧を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-337">Get the list of Objects implemented by the LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-338">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-338">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_get_next(NX_LWM2M_CLIENT *client_ptr,
                                    NX_LWM2M_ID *object_id_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-339">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-339">Description</span></span>

<span data-ttu-id="26a3a-340">このサービスを使用すると、LWM2M クライアントによって実装される次のオブジェクトの ID が返されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-340">This service returns the ID of the next Object implemented by the LWM2M Client.</span></span> <span data-ttu-id="26a3a-341">現在のオブジェクト ID が NX_LWM2M_RESERVED_ID (65535) に設定されている場合、最初のオブジェクト ID が返されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-341">If the current Object ID is set to NX_LWM2M_RESERVED_ID (65535) the first Object ID is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-342">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-342">Parameters</span></span>

- <span data-ttu-id="26a3a-343">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-343">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="26a3a-344">**object_id_ptr**: 現在のオブジェクト ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-344">**object_id_ptr**: Pointer to the current Object ID.</span></span> <span data-ttu-id="26a3a-345">戻り値には、LWM2M クライアントによって実装される次のオブジェクト ID が含まれます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-345">On return contains the next Object ID implemented by the LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-346">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-346">Return Values</span></span>

- <span data-ttu-id="26a3a-347">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-347">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="26a3a-348">**NX_LWM2M_NOT_FOUND**: 指定されたオブジェクト ID は、データベースの最後です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-348">**NX_LWM2M_NOT_FOUND**: The given Object ID is the last of the database.</span></span>
- <span data-ttu-id="26a3a-349">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-349">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_instance_get_next"></a><span data-ttu-id="26a3a-350">nx_lwm2m_client_object_instance_get_next</span><span class="sxs-lookup"><span data-stu-id="26a3a-350">nx_lwm2m_client_object_instance_get_next</span></span>

<span data-ttu-id="26a3a-351">オブジェクトのインスタンスの一覧を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-351">Get the list of Instances of an Object</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-352">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-352">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_get_next(NX_LWM2M_CLIENT *client_ptr,
                    NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-353">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-353">Description</span></span>

<span data-ttu-id="26a3a-354">このサービスを使用すると、指定されたオブジェクトの次のオブジェクト インスタンスの ID が返されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-354">This service returns the ID of the next Object Instance of the given Object.</span></span> <span data-ttu-id="26a3a-355">現在のインスタンス ID が NX_LWM2M_RESERVED_ID (65535) に設定されている場合は、最初のインスタンスの ID が返されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-355">If the current Instance ID is set to NX_LWM2M_RESERVED_ID (65535) the ID of the first instance is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-356">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-356">Parameters</span></span>

- <span data-ttu-id="26a3a-357">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-357">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="26a3a-358">**object_id**: オブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="26a3a-358">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="26a3a-359">**instance_id_ptr**: 現在のオブジェクト インスタンス ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-359">**instance_id_ptr**: Pointer to the current Object Instance ID.</span></span> <span data-ttu-id="26a3a-360">戻り値には、オブジェクトの次のインスタンス ID が含まれます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-360">On return contains the next Instance ID of the Object.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-361">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-361">Return Values</span></span>

- <span data-ttu-id="26a3a-362">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-362">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="26a3a-363">**NX_LWM2M_NOT_FOUND**: 指定されたインスタンス ID がオブジェクトの最後か、オブジェクト ID が実装されていません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-363">**NX_LWM2M_NOT_FOUND**: The given Instance ID is the last of the object, or the Object ID is not implemented.</span></span>
- <span data-ttu-id="26a3a-364">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-364">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_read"></a><span data-ttu-id="26a3a-365">nx_lwm2m_client_object_read</span><span class="sxs-lookup"><span data-stu-id="26a3a-365">nx_lwm2m_client_object_read</span></span>

<span data-ttu-id="26a3a-366">オブジェクト インスタンスのリソース値を読み取ります</span><span class="sxs-lookup"><span data-stu-id="26a3a-366">Read resources values of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-367">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-367">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_read(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT num_values, NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a><span data-ttu-id="26a3a-368">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-368">Description</span></span>

<span data-ttu-id="26a3a-369">このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンスの "読み取り" 操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-369">This service performs a 'Read' operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-370">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-370">Parameters</span></span>

- <span data-ttu-id="26a3a-371">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-371">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="26a3a-372">**object_id**: オブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="26a3a-372">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="26a3a-373">**instance_id**: オブジェクト インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="26a3a-373">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="26a3a-374">**num_values**: 読み取るリソースの数。</span><span class="sxs-lookup"><span data-stu-id="26a3a-374">**num_values**: The number of resources to read.</span></span>
- <span data-ttu-id="26a3a-375">**values_ptr**: 読み取るリソースの ID を格納する NX_LWM2M_RESOURCE の配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-375">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="26a3a-376">返されると、配列に対応する型と値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-376">On return the array is filled with the corresponding types and values.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-377">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-377">Return Values</span></span>

- <span data-ttu-id="26a3a-378">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-378">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-379">**NX_LWM2M_METHOD_NOT_ALLOWED**: リソースで読み取り操作がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-379">**NX_LWM2M_METHOD_NOT_ALLOWED**: A resource doesn't support the read operation.</span></span>
- <span data-ttu-id="26a3a-380">**NX_LWM2M_NOT_FOUND**: オブジェクト ID、オブジェクト インスタンス ID、またはリソース ID が存在していません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-380">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or a resource ID doesn't exist.</span></span>
- <span data-ttu-id="26a3a-381">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-381">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_write"></a><span data-ttu-id="26a3a-382">nx_lwm2m_client_object_write</span><span class="sxs-lookup"><span data-stu-id="26a3a-382">nx_lwm2m_client_object_write</span></span>

<span data-ttu-id="26a3a-383">オブジェクト インスタンスのリソース値を変更します</span><span class="sxs-lookup"><span data-stu-id="26a3a-383">Change resources values of an Object instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-384">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-384">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_write(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, UINT num_values,
        const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

### <a name="description"></a><span data-ttu-id="26a3a-385">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-385">Description</span></span>

<span data-ttu-id="26a3a-386">このサービスを使用すると、LWM2M クライアントのオブジェクト インスタンスの "書き込み" 操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-386">This service performs a 'Write' operation on an Object Instance of the LWM2M Client.</span></span>

<span data-ttu-id="26a3a-387">*write_op* パラメーターには、次の書き込み操作を指定できます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-387">The following write operations can be specified to the *write_op* parameter:</span></span>

- <span data-ttu-id="26a3a-388">**0** &mdash; 部分更新: 新しい値で提供されるリソースを追加または更新し、他の既存のリソースはそのままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-388">**0** &mdash; Partial Update: adds or updates Resources provided in the new value and leaves other existing Resources unchanged,</span></span>

- <span data-ttu-id="26a3a-389">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; インスタンスの置換: オブジェクト インスタンスを、指定された新しいリソース値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-389">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Replace Instance: replaces the Object Instance with the new provided resource values.</span></span>

- <span data-ttu-id="26a3a-390">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; リソースの置換: リソースを、指定された新しいリソース値に置き換えます (複数リソースを置き換えるために使用されます)。</span><span class="sxs-lookup"><span data-stu-id="26a3a-390">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Replace Resource: replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span>

- <span data-ttu-id="26a3a-391">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; ブートストラップ書き込み: ブートストラップ シーケンスからの呼び出しを示します。</span><span class="sxs-lookup"><span data-stu-id="26a3a-391">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: indicates a call from a Bootstrap sequence.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-392">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-392">Parameters</span></span>

- <span data-ttu-id="26a3a-393">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-393">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="26a3a-394">**object_id**: オブジェクト ID。</span><span class="sxs-lookup"><span data-stu-id="26a3a-394">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="26a3a-395">**instance_id**: オブジェクト インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="26a3a-395">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="26a3a-396">**num_values**: 書き込むリソースの数。</span><span class="sxs-lookup"><span data-stu-id="26a3a-396">**num_values**: The number of resources to write.</span></span>
- <span data-ttu-id="26a3a-397">**values_ptr**: リソースの ID、および書き込む型と値を格納する NX_LWM2M_RESOURCE の配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-397">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources, the types and the values to write.</span></span>
- <span data-ttu-id="26a3a-398">**write_op**: 書き込み操作の種類。</span><span class="sxs-lookup"><span data-stu-id="26a3a-398">**write_op**: The type of write operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-399">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-399">Return Values</span></span>

- <span data-ttu-id="26a3a-400">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-400">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-401">**NX_LWM2M_BAD_ENCODING**: リソースの型が無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-401">**NX_LWM2M_BAD_ENCODING**: The type of a resource is not valid.</span></span>
- <span data-ttu-id="26a3a-402">**NX_LWM2M_BUFFER_TOO_SMALL**: 値の長さが大きすぎてインスタンスに格納できません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-402">**NX_LWM2M_BUFFER_TOO_SMALL**: The length of a value is too big to be stored in the instance.</span></span>
- <span data-ttu-id="26a3a-403">**NX_LWM2M_METHOD_NOT_ALLOWED**: リソースが読み書き込み操作をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-403">**NX_LWM2M_METHOD_NOT_ALLOWED**: A resource doesn't support the write operation.</span></span>
- <span data-ttu-id="26a3a-404">**NX_LWM2M_NO_MEMORY**: リソース値を格納するためのメモリを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-404">**NX_LWM2M_NO_MEMORY**: Cannot allocate memory to store a resource value.</span></span>
- <span data-ttu-id="26a3a-405">**NX_LWM2M_NOT_ACCEPTABLE**: リソースの値が無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-405">**NX_LWM2M_NOT_ACCEPTABLE**: The value of a resource is not valid.</span></span>
- <span data-ttu-id="26a3a-406">**NX_LWM2M_NOT_FOUND**: オブジェクト ID、オブジェクト インスタンス ID、またはリソース ID が存在していません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-406">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or a resource ID doesn't exist.</span></span>
- <span data-ttu-id="26a3a-407">NX_OPTION_ERROR: 書き込み操作の種類が無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-407">NX_OPTION_ERROR: Invalid type of write operation.</span></span>
- <span data-ttu-id="26a3a-408">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-408">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_security_key_callbacks_set"></a><span data-ttu-id="26a3a-409">nx_lwm2m_client_security_key_callbacks_set</span><span class="sxs-lookup"><span data-stu-id="26a3a-409">nx_lwm2m_client_security_key_callbacks_set</span></span>

<span data-ttu-id="26a3a-410">セキュリティ オブジェクト キー管理のコールバックを設定します</span><span class="sxs-lookup"><span data-stu-id="26a3a-410">Set Security Object key management callbacks</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-411">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-411">Prototype</span></span>

```c
UINT nx_lwm2m_client_security_key_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_CLIENT_SECURITY_KEY_WRITE_CALLBACK write_callback,
                NX_LWM2M_CLIENT_SECURITY_KEY_DELETE_CALLBACK delete_callback);
```

### <a name="description"></a><span data-ttu-id="26a3a-412">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-412">Description</span></span>

<span data-ttu-id="26a3a-413">このサービスを使用すると、セキュリティ キーに関連する LWM2M セキュリティ オブジェクト リソースに対する操作を実装するためのアプリケーションのコールバックがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-413">This service installs the application callbacks for implementing operations on the LWM2M Security Object resources related to the security keys.</span></span>

<span data-ttu-id="26a3a-414">ブートストラップ セッション中は、LWM2M クライアントからアプリケーションにセキュリティ キー管理が委任されます。ブートストラップ サーバーによりセキュリティ オブジェクト インスタンスに次のリソースが書き込まれるか削除されると、コールバックが呼び出されます: 公開キーまたは ID (3)、サーバー公開キー (4)、秘密キー (5)。</span><span class="sxs-lookup"><span data-stu-id="26a3a-414">The LWM2M Client delegates the security key management to the application during the Bootstrap sessions, the callbacks will be called when the Bootstrap Server writes or deletes the following resources on a Security Object Instance: Public Key or Identity (3), Server Public Key (4), Secret Key (5).</span></span>

<span data-ttu-id="26a3a-415">アプリケーションは、キー データの格納と、LWM2M クライアントに使用される DTLS セッションの構成を担当します。</span><span class="sxs-lookup"><span data-stu-id="26a3a-415">The application is responsible for storing the keys data and for configuring the DTLS sessions used by the LWM2M client.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-416">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-416">Parameters</span></span>

- <span data-ttu-id="26a3a-417">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-417">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="26a3a-418">**write_callback**: "Write" キー メソッドのコールバック。</span><span class="sxs-lookup"><span data-stu-id="26a3a-418">**write_callback**: The 'Write' key method callback.</span></span>
- <span data-ttu-id="26a3a-419">**delete_callback**: "Delete" キー メソッドのコールバック。</span><span class="sxs-lookup"><span data-stu-id="26a3a-419">**delete_callback**: The 'Delete' key method callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-420">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-420">Return Values</span></span>

- <span data-ttu-id="26a3a-421">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-421">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-422">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-422">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_bootstrap"></a><span data-ttu-id="26a3a-423">nx_lwm2m_client_session_bootstrap</span><span class="sxs-lookup"><span data-stu-id="26a3a-423">nx_lwm2m_client_session_bootstrap</span></span>

<span data-ttu-id="26a3a-424">ブートストラップ サーバーとのセッションを開始します</span><span class="sxs-lookup"><span data-stu-id="26a3a-424">Start a session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-425">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-425">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap(NX_LWM2M_CLIENT_SESSION
    *session_ptr, NX_LWM2M_ID security_id, ULONG ip_address, UINT port);
```

### <a name="description"></a><span data-ttu-id="26a3a-426">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-426">Description</span></span>

<span data-ttu-id="26a3a-427">このサービスを使用すると、ブートストラップ サーバーとのセッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-427">This service start a session with a Bootstrap Server.</span></span> <span data-ttu-id="26a3a-428">サーバーには、セキュリティ オブジェクト内に対応するセキュリティ インスタンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-428">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="26a3a-429">このサーバーに関連付けられているセキュリティ インスタンスで、"保留中" リソースが 0 以外の場合、セッションはサーバーによって開始されるブートストラップを待機します。この期間が過ぎてもサーバーによってブートストラップが開始されなかった場合は、クライアントによって開始されたブートストラップが実行されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-429">If the 'Hold Off' resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="26a3a-430">現在アクティブなセッションは、この呼び出しによって中止され、新しいブートストラップ サーバー セッションに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-430">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-431">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-431">Parameters</span></span>

- <span data-ttu-id="26a3a-432">**session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-432">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="26a3a-433">**security_id**: ブートストラップ サーバーのセキュリティ インスタンスが定義されていない場合は、ブートストラップ サーバーのセキュリティインスタンス ID を NX_LWM2M_RESERVED_ID (65535) に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26a3a-433">**security_id**: The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="26a3a-434">**ip_address**: サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="26a3a-434">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="26a3a-435">**port**: サーバーの UDP ポート。</span><span class="sxs-lookup"><span data-stu-id="26a3a-435">**port**: The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-436">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-436">Return Values</span></span>

- <span data-ttu-id="26a3a-437">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-437">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-438">**NX_LWM2M_NOT_FOUND**: セキュリティ インスタンス ID に対応するセキュリティ オブジェクト インスタンスがありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-438">**NX_LWM2M_NOT_FOUND**: There is No Security Object instance corresponding to the Security Instance ID.</span></span>
- <span data-ttu-id="26a3a-439">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-439">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a><span data-ttu-id="26a3a-440">nx_lwm2m_client_session_bootstrap_dtls</span><span class="sxs-lookup"><span data-stu-id="26a3a-440">nx_lwm2m_client_session_bootstrap_dtls</span></span>

<span data-ttu-id="26a3a-441">ブートストラップ サーバーとのセキュリティで保護されたセッションを開始します</span><span class="sxs-lookup"><span data-stu-id="26a3a-441">Start a secure session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-442">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-442">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID security_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a><span data-ttu-id="26a3a-443">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-443">Description</span></span>

<span data-ttu-id="26a3a-444">このサービスを使用すると、セキュリティで保護された DTLS 接続を使用して、ブートストラップ サーバーとのセッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-444">This service start a session with a Bootstrap Server using a secure DTLS connection.</span></span> <span data-ttu-id="26a3a-445">サーバーには、セキュリティ オブジェクト内に対応するセキュリティ インスタンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-445">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="26a3a-446">この関数を呼び出す前に、DTLS セッションが適切な暗号スイートとキー素材で構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="26a3a-446">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="26a3a-447">NX_SECURE_ENABLE_DTLS を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26a3a-447">NX_SECURE_ENABLE_DTLS must be defined.</span></span>

<span data-ttu-id="26a3a-448">このサーバーに関連付けられているセキュリティ インスタンスで、"保留中" リソースが 0 以外の場合、セッションはサーバーによって開始されるブートストラップを待機します。この期間が過ぎてもサーバーによってブートストラップが開始されなかった場合は、クライアントによって開始されたブートストラップが実行されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-448">If the 'Hold Off' resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="26a3a-449">現在アクティブなセッションは、この呼び出しによって中止され、新しいブートストラップ サーバー セッションに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-449">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-450">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-450">Parameters</span></span>

- <span data-ttu-id="26a3a-451">**session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-451">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="26a3a-452">**security_id**: ブートストラップ サーバーのセキュリティ インスタンスが定義されていない場合は、ブートストラップ サーバーのセキュリティインスタンス ID を NX_LWM2M_RESERVED_ID (65535) に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26a3a-452">**security_id**: The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="26a3a-453">**ip_address**: サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="26a3a-453">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="26a3a-454">**port**: サーバーの UDP ポート。</span><span class="sxs-lookup"><span data-stu-id="26a3a-454">**port**: The UDP port of the server.</span></span>
- <span data-ttu-id="26a3a-455">**dtls_session_ptr**: ブートストラップ セッションに使用する DTLS セッション。</span><span class="sxs-lookup"><span data-stu-id="26a3a-455">**dtls_session_ptr**: The DTLS session to use for the Bootstrap session.</span></span>
- <span data-ttu-id="26a3a-456">**dtls_local_port**: DTLS セッションに使用されるローカル UDP ポート。</span><span class="sxs-lookup"><span data-stu-id="26a3a-456">**dtls_local_port**: The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-457">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-457">Return Values</span></span>

- <span data-ttu-id="26a3a-458">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-458">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-459">**NX_LWM2M_NOT_FOUND**: セキュリティ インスタンス ID に対応するセキュリティ オブジェクト インスタンスがありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-459">**NX_LWM2M_NOT_FOUND**: There is No Security Object instance corresponding to the Security Instance ID.</span></span>
- <span data-ttu-id="26a3a-460">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-460">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_create"></a><span data-ttu-id="26a3a-461">nx_lwm2m_client_session_create</span><span class="sxs-lookup"><span data-stu-id="26a3a-461">nx_lwm2m_client_session_create</span></span>

<span data-ttu-id="26a3a-462">LWM2M クライアント セッションを作成します</span><span class="sxs-lookup"><span data-stu-id="26a3a-462">Create LWM2M Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-463">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-463">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_create(NX_LWM2M_CLIENT_SESSION *session_ptr,
         NX_LWM2M_CLIENT *client_ptr,
         NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a><span data-ttu-id="26a3a-464">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-464">Description</span></span>

<span data-ttu-id="26a3a-465">このサービスを使用すると、既存の LWM2M クライアントにアタッチされた新しい LWM2M クライアント セッションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-465">This service creates a new LWM2M Client Session attached to an existing LWM2M Client.</span></span> <span data-ttu-id="26a3a-466">セッションは、ブートストラップ サーバーまたは LWM2M サーバーと通信するために LWM2M クライアントによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-466">The session is used by the LWM2M Client to communicate with a Bootstrap Server or a LWM2M Server.</span></span>

<span data-ttu-id="26a3a-467">アプリケーションは、セッションの状態が更新されたときに呼び出されるコールバック関数を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26a3a-467">The application must provide a callback function that will be called when the state of the session is updated.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-468">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-468">Parameters</span></span>

- <span data-ttu-id="26a3a-469">**session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-469">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="26a3a-470">**client_ptr**: 以前に作成した LWM2M クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-470">**client_ptr**: Pointer to the previously created LWM2M Client.</span></span>
- <span data-ttu-id="26a3a-471">**state_callback**: セッションの状態が変更されたときに呼び出されるアプリケーション コールバック。</span><span class="sxs-lookup"><span data-stu-id="26a3a-471">**state_callback**: Application callback that is called when the state of the session has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-472">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-472">Return Values</span></span>

- <span data-ttu-id="26a3a-473">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-473">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-474">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-474">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_delete"></a><span data-ttu-id="26a3a-475">nx_lwm2m_client_session_delete</span><span class="sxs-lookup"><span data-stu-id="26a3a-475">nx_lwm2m_client_session_delete</span></span>

<span data-ttu-id="26a3a-476">LWM2M クライアント セッションを削除します</span><span class="sxs-lookup"><span data-stu-id="26a3a-476">Delete LWM2M Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-477">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-477">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-478">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-478">Description</span></span>

<span data-ttu-id="26a3a-479">このサービスを使用すると LWM2M クライアント セッションが削除されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-479">This service deletes a LWM2M Client Session.</span></span>

<span data-ttu-id="26a3a-480">nx_lwm2m_client_delete を呼び出して LWM2M クライアントを削除すると、クライアントにアタッチされているすべてのセッションも削除されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-480">When a LWM2M Client is deleted by calling nx_lwm2m_client_delete all sessions attached to the client are also deleted.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-481">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-481">Parameters</span></span>

- <span data-ttu-id="26a3a-482">**session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-482">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-483">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-483">Return Values</span></span>

- <span data-ttu-id="26a3a-484">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-484">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-485">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-485">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_deregister"></a><span data-ttu-id="26a3a-486">nx_lwm2m_client_session_deregister</span><span class="sxs-lookup"><span data-stu-id="26a3a-486">nx_lwm2m_client_session_deregister</span></span>

<span data-ttu-id="26a3a-487">LWM2M サーバーとのセッションを終了します</span><span class="sxs-lookup"><span data-stu-id="26a3a-487">Terminate a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-488">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-488">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-489">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-489">Description</span></span>

<span data-ttu-id="26a3a-490">このサービスを使用すると、LWM2M サーバーに対して "登録解除" 操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-490">This service performs a 'De-Register' operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-491">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-491">Parameters</span></span>

- <span data-ttu-id="26a3a-492">**session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-492">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-493">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-493">Return Values</span></span>

- <span data-ttu-id="26a3a-494">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-494">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-495">**NX_LWM2M_NOT_REGISTERED**: クライアントがサーバーに登録されていません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-495">**NX_LWM2M_NOT_REGISTERED**: The client is not registered to the server.</span></span>
- <span data-ttu-id="26a3a-496">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-496">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_error_get"></a><span data-ttu-id="26a3a-497">nx_lwm2m_client_session_error_get</span><span class="sxs-lookup"><span data-stu-id="26a3a-497">nx_lwm2m_client_session_error_get</span></span>

<span data-ttu-id="26a3a-498">セッションの最後のエラーを取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-498">Get last error of a session</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-499">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-499">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-500">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-500">Description</span></span>

<span data-ttu-id="26a3a-501">このサービスを使用すると、セッションがエラー状態のときにセッションのエラー コードが返されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-501">This service returns the error code of the session when the session is in an error state.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-502">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-502">Parameters</span></span>

- <span data-ttu-id="26a3a-503">**session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-503">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-504">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-504">Return Values</span></span>

- <span data-ttu-id="26a3a-505">**NX_SUCCESS**: セッションがエラー状態ではありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-505">**NX_SUCCESS**: The session is not in error state.</span></span>
- <span data-ttu-id="26a3a-506">**NX_LWM2M_ADDRESS_ERROR**: サーバー アドレスが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-506">**NX_LWM2M_ADDRESS_ERROR**: Invalid server address.</span></span>
- <span data-ttu-id="26a3a-507">**NX_LWM2M_BUFFER_TOO_SMALL**: 要求のペイロードがネットワーク バッファーに収まりません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-507">**NX_LWM2M_BUFFER_TOO_SMALL**: Payload of request doesn't fit in network buffer.</span></span>
- <span data-ttu-id="26a3a-508">**NX_LWM2M_DTLS_ERROR**: サーバーとのセキュリティで保護された接続を確立できませんでした。</span><span class="sxs-lookup"><span data-stu-id="26a3a-508">**NX_LWM2M_DTLS_ERROR**: Failed to establish secured connection with server.</span></span>
- <span data-ttu-id="26a3a-509">**NX_LWM2M_ERROR**: 特定できないエラー。</span><span class="sxs-lookup"><span data-stu-id="26a3a-509">**NX_LWM2M_ERROR**: Unspecified error.</span></span>
- <span data-ttu-id="26a3a-510">**NX_LWM2M_FORBIDDEN**: サーバーによって登録が拒否されました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-510">**NX_LWM2M_FORBIDDEN**: Registration refused by server.</span></span>
- <span data-ttu-id="26a3a-511">**NX_LWM2M_NOT_FOUND**: 更新または登録解除するときに、サーバーがクライアントを見つけることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="26a3a-511">**NX_LWM2M_NOT_FOUND**: Client not found by server when updating/deregistering.</span></span>
- <span data-ttu-id="26a3a-512">**NX_LWM2M_SERVER_INSTANCE_DELETED**: セッションに対応するサーバー オブジェクト インスタンスが削除されました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-512">**NX_LWM2M_SERVER_INSTANCE_DELETED**: The Server Object Instance corresponding to the session has been deleted.</span></span>
- <span data-ttu-id="26a3a-513">**NX_LWM2M_TIMED_OUT**: サーバーからの応答がありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-513">**NX_LWM2M_TIMED_OUT**: No answer from server.</span></span>
- <span data-ttu-id="26a3a-514">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-514">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_register"></a><span data-ttu-id="26a3a-515">nx_lwm2m_client_session_register</span><span class="sxs-lookup"><span data-stu-id="26a3a-515">nx_lwm2m_client_session_register</span></span>

<span data-ttu-id="26a3a-516">LWM2M サーバーとのセッションを開始します</span><span class="sxs-lookup"><span data-stu-id="26a3a-516">Start a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-517">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-517">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register(NX_LWM2M_CLIENT_SESSION *session_ptr,
                    NX_LWM2M_ID server_id, ULONG ip_address, UINT port);
```

### <a name="description"></a><span data-ttu-id="26a3a-518">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-518">Description</span></span>

<span data-ttu-id="26a3a-519">このサービスを使用すると、LWM2M サーバーに対して "登録" 操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-519">This service performs a 'Register' operation to a LWM2M Server.</span></span> <span data-ttu-id="26a3a-520">サーバーは、サーバー オブジェクト内に対応するサーバー インスタンスを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="26a3a-520">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="26a3a-521">登録が正常に完了した場合、LWM2M クライアントによってサーバーからのその後の操作が処理され、クライアントが登録解除されるまで定期的に "更新" メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-521">If the registration is successful the LWM2M Client will process further operations from the server and will periodically send 'Update' messages until the client is de-registered.</span></span>

<span data-ttu-id="26a3a-522">現在アクティブなセッションは、この呼び出しによって中止され、新しい LWM2M サーバー セッションに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-522">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-523">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-523">Parameters</span></span>

- <span data-ttu-id="26a3a-524">**session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-524">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="26a3a-525">**server_id**: LWM2M サーバーの短いサーバー ID。</span><span class="sxs-lookup"><span data-stu-id="26a3a-525">**server_id**: The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="26a3a-526">**ip_address**: サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="26a3a-526">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="26a3a-527">**port**: サーバーの UDP ポート。</span><span class="sxs-lookup"><span data-stu-id="26a3a-527">**port**: The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-528">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-528">Return Values</span></span>

- <span data-ttu-id="26a3a-529">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-529">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="26a3a-530">**NX_LWM2M_NOT_FOUND**: 短いサーバー ID に対応するサーバー オブジェクト インスタンスがありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-530">**NX_LWM2M_NOT_FOUND**: There is No Server Object instance corresponding to the Short Server ID.</span></span>
- <span data-ttu-id="26a3a-531">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-531">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_register_dtls"></a><span data-ttu-id="26a3a-532">nx_lwm2m_client_session_register_dtls</span><span class="sxs-lookup"><span data-stu-id="26a3a-532">nx_lwm2m_client_session_register_dtls</span></span>

<span data-ttu-id="26a3a-533">LWM2M サーバーとのセキュリティで保護されたセッションを開始します</span><span class="sxs-lookup"><span data-stu-id="26a3a-533">Start a secure session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-534">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-534">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID server_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a><span data-ttu-id="26a3a-535">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-535">Description</span></span>

<span data-ttu-id="26a3a-536">このサービスを使用すると、セキュリティで保護された DTLS 接続を使用して、LWM2M サーバーへの "登録" 操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-536">This service performs a 'Register' operation to a LWM2M Server using a secure DTLS connection.</span></span> <span data-ttu-id="26a3a-537">サーバーは、サーバー オブジェクト内に対応するサーバー インスタンスを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="26a3a-537">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="26a3a-538">この関数を呼び出す前に、DTLS セッションが適切な暗号スイートとキー素材で構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="26a3a-538">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="26a3a-539">NX_SECURE_ENABLE_DTLS を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26a3a-539">NX_SECURE_ENABLE_DTLS must be defined.</span></span>

<span data-ttu-id="26a3a-540">各 DTLS セッションは通信に独自の UDP ソケットを使用されているため、アプリケーションによって複数のセキュリティで保護されたセッションが作成される場合、セッションごとに異なるローカル ポート dtls_local_port にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="26a3a-540">Each DTLS session uses its own UDP socket for communication, so the local port dtls_local_port must be different for each session if the application creates several secure sessions.</span></span>

<span data-ttu-id="26a3a-541">登録が正常に完了した場合、LWM2M クライアントによってサーバーからのその後の操作が処理され、クライアントが登録解除されるまで定期的に "更新" メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-541">If the registration is successful the LWM2M Client will process further operations from the server and will periodically send 'Update' messages until the client is de-registered.</span></span>

<span data-ttu-id="26a3a-542">現在アクティブなセッションは、この呼び出しによって中止され、新しい LWM2M サーバー セッションに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-542">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-543">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-543">Parameters</span></span>

- <span data-ttu-id="26a3a-544">**session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-544">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="26a3a-545">**server_id**: LWM2M サーバーの短いサーバー ID。</span><span class="sxs-lookup"><span data-stu-id="26a3a-545">**server_id**: The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="26a3a-546">**ip_address**: サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="26a3a-546">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="26a3a-547">**port**: サーバーの UDP ポート。</span><span class="sxs-lookup"><span data-stu-id="26a3a-547">**port**: The UDP port of the server.</span></span>
- <span data-ttu-id="26a3a-548">**dtls_session_ptr**: LWM2M セッションに使用する DTLS セッション。</span><span class="sxs-lookup"><span data-stu-id="26a3a-548">**dtls_session_ptr**: The DTLS session to use for the LWM2M session.</span></span>
- <span data-ttu-id="26a3a-549">**dtls_local_port**: DTLS セッションに使用されるローカル UDP ポート。</span><span class="sxs-lookup"><span data-stu-id="26a3a-549">**dtls_local_port**: The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-550">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-550">Return Values</span></span>

- <span data-ttu-id="26a3a-551">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-551">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-552">**NX_LWM2M_NOT_FOUND**: 短いサーバー ID に対応するサーバー オブジェクト インスタンスがありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-552">**NX_LWM2M_NOT_FOUND**: There is No Server Object instance corresponding to the Short Server ID.</span></span>
- <span data-ttu-id="26a3a-553">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-553">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_update"></a><span data-ttu-id="26a3a-554">nx_lwm2m_client_session_update</span><span class="sxs-lookup"><span data-stu-id="26a3a-554">nx_lwm2m_client_session_update</span></span>

<span data-ttu-id="26a3a-555">LWM2M サーバーとのセッションを更新します</span><span class="sxs-lookup"><span data-stu-id="26a3a-555">Update a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-556">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-556">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-557">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-557">Description</span></span>

<span data-ttu-id="26a3a-558">このサービスを使用すると、LWM2M サーバーに対して "更新" 操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-558">This service performs an 'Update' operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-559">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-559">Parameters</span></span>

- <span data-ttu-id="26a3a-560">**session_ptr**: LWM2M クライアント セッション制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-560">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-561">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-561">Return Values</span></span>

- <span data-ttu-id="26a3a-562">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-562">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-563">**NX_LWM2M_NOT_REGISTERED**: クライアントがサーバーに登録されていません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-563">**NX_LWM2M_NOT_REGISTERED**: The client is not registered to the server.</span></span>
- <span data-ttu-id="26a3a-564">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-564">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_unlock"></a><span data-ttu-id="26a3a-565">nx_lwm2m_client_unlock</span><span class="sxs-lookup"><span data-stu-id="26a3a-565">nx_lwm2m_client_unlock</span></span>

<span data-ttu-id="26a3a-566">LWM2M クライアントのロックを解除します</span><span class="sxs-lookup"><span data-stu-id="26a3a-566">Unlock LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-567">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-567">Prototype</span></span>

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-568">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-568">Description</span></span>

<span data-ttu-id="26a3a-569">このサービスを使用すると、nx_lwm2m_client_unlock() の呼び出しによって以前にロックされていた LWM2M クライアントのロックが解除されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-569">This service unlocks the LWM2M Client previoulsy locked by a call to nx_lwm2m_client_unlock().</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-570">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-570">Parameters</span></span>

- <span data-ttu-id="26a3a-571">**client_ptr**: LWM2M クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-571">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-572">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-572">Return Values</span></span>

- <span data-ttu-id="26a3a-573">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-573">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-574">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-574">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_create"></a><span data-ttu-id="26a3a-575">nx_lwm2m_firmware_create</span><span class="sxs-lookup"><span data-stu-id="26a3a-575">nx_lwm2m_firmware_create</span></span>

<span data-ttu-id="26a3a-576">ファームウェア更新オブジェクトを作成します</span><span class="sxs-lookup"><span data-stu-id="26a3a-576">Create Firmware Update Object</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-577">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-577">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_create(NX_LWM2M_FIRMWARE *firmware_ptr,
    NX_LWM2M_CLIENT *client_ptr, UINT protocols,
    NX_LWM2M_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_FIRMWARE_UPDATE_CALLBACK update_callback);
```

### <a name="description"></a><span data-ttu-id="26a3a-578">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-578">Description</span></span>

<span data-ttu-id="26a3a-579">このサービスを使用すると、ファームウェア更新オブジェクトが初期化され、以前に作成した LWM2M クライアントにオブジェクトが追加されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-579">This service initializes a Firmware Update Object and adds the Object to a previously created LWM2M Client.</span></span> <span data-ttu-id="26a3a-580">ファームウェア更新オブジェクトには、LWM2M サーバーと通信するためのリソースが実装されていますが、アプリケーションには、ファームウェアに対する実際の操作 (ファームウェアのダウンロード、格納、および更新) を実装するためのコールバックを用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26a3a-580">The Firmware Update Object implements the resources for communicating with a LWM2M Server but the application must provide callbacks for implementing the actual operations on the firmware (dowloading, storing, and updating the firmware).</span></span>

<span data-ttu-id="26a3a-581">このプロトコル パラメーターは、"パッケージ URI" リソースを使用してファームウェアを取得する場合に、アプリケーションでサポートされているプロトコルを示します。次のフラグが定義されています:</span><span class="sxs-lookup"><span data-stu-id="26a3a-581">The protocols parameter indicates which protocols are supported by the application for retrieving the firmware with the 'Package URI' resource, the following flags are defined:</span></span>

<span data-ttu-id="26a3a-582">NX_LWM2M_FIRMWARE_PROTOCOL_COAP、NX_LWM2M_FIRMWARE_PROTOCOL_COAPS、NX_LWM2M_FIRMWARE_PROTOCOL_HTTP、NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS。</span><span class="sxs-lookup"><span data-stu-id="26a3a-582">NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-583">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-583">Parameters</span></span>

- <span data-ttu-id="26a3a-584">**firmware_ptr**: ファームウェア オブジェクト制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-584">**firmware_ptr**: Pointer to the Firmware Object control block.</span></span>
- <span data-ttu-id="26a3a-585">**client_ptr**: 以前に作成した LWM2M クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-585">**client_ptr**: Pointer to previsously created LWM2M Client.</span></span>
- <span data-ttu-id="26a3a-586">**protocols**: パッケージ URI リソースでサポートされているプロトコルを示すフラグ。</span><span class="sxs-lookup"><span data-stu-id="26a3a-586">**protocols**: Flags indicating which protocols are supported by the Package URI resource.</span></span>
- <span data-ttu-id="26a3a-587">**package_callback**: NULL にする必要があります [TBD]。</span><span class="sxs-lookup"><span data-stu-id="26a3a-587">**package_callback**: Must be NULL [TBD].</span></span>
- <span data-ttu-id="26a3a-588">**package_uri_callback**: パッケージ URI リソースの実装に使用されるコールバック。</span><span class="sxs-lookup"><span data-stu-id="26a3a-588">**package_uri_callback**: Callback used to implement the Package URI resource.</span></span>
- <span data-ttu-id="26a3a-589">**update_callback**: 更新リソースの実装に使用されるコールバック。</span><span class="sxs-lookup"><span data-stu-id="26a3a-589">**update_callback**: Callback used to implement the Update resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-590">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-590">Return Values</span></span>

- <span data-ttu-id="26a3a-591">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-591">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-592">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-592">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_package_info_set"></a><span data-ttu-id="26a3a-593">nx_lwm2m_firmware_package_info_set</span><span class="sxs-lookup"><span data-stu-id="26a3a-593">nx_lwm2m_firmware_package_info_set</span></span>

<span data-ttu-id="26a3a-594">ファームウェア更新パッケージ情報を設定します</span><span class="sxs-lookup"><span data-stu-id="26a3a-594">Set Firmware Update Package Information</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-595">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-595">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_package_info_set(NX_LWM2M_FIRMWARE *firmware_ptr,
                                const CHAR *name, const CHAR *version);
```

### <a name="description"></a><span data-ttu-id="26a3a-596">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-596">Description</span></span>

<span data-ttu-id="26a3a-597">このサービスを使用すると、ファームウェア更新オブジェクトの "PkgName" (6) および "PkgVersion" (7) リソースの値が変更されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-597">This service changes the values of the 'PkgName' (6) and 'PkgVersion' (7) resources of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-598">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-598">Parameters</span></span>

- <span data-ttu-id="26a3a-599">**firmware_ptr**: ファームウェア更新オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-599">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="26a3a-600">**name**: パッケージ名の新しい値。</span><span class="sxs-lookup"><span data-stu-id="26a3a-600">**name**: The new value of the Package Name.</span></span>
- <span data-ttu-id="26a3a-601">**version**: パッケージ バージョンの新しい値。</span><span class="sxs-lookup"><span data-stu-id="26a3a-601">**version**: The new value of the Package Version.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-602">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-602">Return Values</span></span>

- <span data-ttu-id="26a3a-603">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-603">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-604">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-604">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_result_set"></a><span data-ttu-id="26a3a-605">nx_lwm2m_firmware_result_set</span><span class="sxs-lookup"><span data-stu-id="26a3a-605">nx_lwm2m_firmware_result_set</span></span>

<span data-ttu-id="26a3a-606">ファームウェアの更新結果を設定します</span><span class="sxs-lookup"><span data-stu-id="26a3a-606">Set Firmware Update Result</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-607">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-607">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_result_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR result);
```

### <a name="description"></a><span data-ttu-id="26a3a-608">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-608">Description</span></span>

<span data-ttu-id="26a3a-609">このサービスを使用すると、ファームウェア更新オブジェクトの "更新結果" (5) リソースの値が変更されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-609">This service changes the value of the 'Update Result' (5) resource of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-610">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-610">Parameters</span></span>

- <span data-ttu-id="26a3a-611">**firmware_ptr**: ファームウェア更新オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-611">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="26a3a-612">**result**: 更新結果リソースの新しい値。</span><span class="sxs-lookup"><span data-stu-id="26a3a-612">**result**: The new value of the Update Result resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-613">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-613">Return Values</span></span>

- <span data-ttu-id="26a3a-614">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-614">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-615">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-615">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_state_set"></a><span data-ttu-id="26a3a-616">nx_lwm2m_firmware_state_set</span><span class="sxs-lookup"><span data-stu-id="26a3a-616">nx_lwm2m_firmware_state_set</span></span>

<span data-ttu-id="26a3a-617">ファームウェア更新状態を設定します</span><span class="sxs-lookup"><span data-stu-id="26a3a-617">Set Firmware Update State</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-618">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-618">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_state_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR state);
```

### <a name="description"></a><span data-ttu-id="26a3a-619">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-619">Description</span></span>

<span data-ttu-id="26a3a-620">このサービスを使用すると、ファームウェア更新オブジェクトの "状態" (3) リソースの値が変更されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-620">This service changes the value of the 'State' (3) resource of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-621">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-621">Parameters</span></span>

- <span data-ttu-id="26a3a-622">**firmware_ptr**: ファームウェア更新オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-622">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="26a3a-623">**state**: 状態リソースの新しい値。</span><span class="sxs-lookup"><span data-stu-id="26a3a-623">**state**: The new value of the State resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-624">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-624">Return Values</span></span>

- <span data-ttu-id="26a3a-625">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-625">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-626">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-626">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_object_resource_changed"></a><span data-ttu-id="26a3a-627">nx_lwm2m_object_resource_changed</span><span class="sxs-lookup"><span data-stu-id="26a3a-627">nx_lwm2m_object_resource_changed</span></span>

<span data-ttu-id="26a3a-628">オブジェクト インスタンスのリソース値のシグナルを変更します</span><span class="sxs-lookup"><span data-stu-id="26a3a-628">Signal change of a resource value of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-629">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-629">Prototype</span></span>

```c
UINT nx_lwm2m_object_resource_changed(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="26a3a-630">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-630">Description</span></span>

<span data-ttu-id="26a3a-631">このサービスは、リソース値の 1 つが変更されたことを LWM2M クライアントに通知するために、オブジェクトの実装によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-631">This service is used by an Object implementation to signals the LWM2M Client that one of its resource value has changed.</span></span> <span data-ttu-id="26a3a-632">LWM2M クライアントは、リソースが LWM2M サーバーによって監視されている場合に通知を送信します。</span><span class="sxs-lookup"><span data-stu-id="26a3a-632">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-633">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-633">Parameters</span></span>

- <span data-ttu-id="26a3a-634">**object_ptr**: オブジェクト実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-634">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="26a3a-635">**instance_ptr**: オブジェクト インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-635">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="26a3a-636">**resource**: 変更されたリソースを記述する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-636">**resource**: Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-637">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-637">Return Values</span></span>

- <span data-ttu-id="26a3a-638">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-638">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-639">NX_PTR_ERROR: ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-639">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_resource_get_boolean"></a><span data-ttu-id="26a3a-640">nx_lwm2m_resource_get_boolean</span><span class="sxs-lookup"><span data-stu-id="26a3a-640">nx_lwm2m_resource_get_boolean</span></span>

<span data-ttu-id="26a3a-641">ブール値リソースの値を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-641">Get the value of a Boolean Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-642">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-642">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_boolean(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-643">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-643">Description</span></span>

<span data-ttu-id="26a3a-644">このサービスを使用するとブール値リソースの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-644">The service retrieves the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-645">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-645">Parameters</span></span>

- <span data-ttu-id="26a3a-646">**value**: リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-646">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="26a3a-647">**bool_ptr**: 宛先ブール値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-647">**bool_ptr**: Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-648">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-648">Return Values</span></span>

- <span data-ttu-id="26a3a-649">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-649">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-650">**NX_LWM2M_BAD_ENCODING**: リソース値がブール値ではありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-650">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Boolean value.</span></span>

## <a name="nx_lwm2m_resource_get_float32"></a><span data-ttu-id="26a3a-651">nx_lwm2m_resource_get_float32</span><span class="sxs-lookup"><span data-stu-id="26a3a-651">nx_lwm2m_resource_get_float32</span></span>

<span data-ttu-id="26a3a-652">32 ビット浮動小数点リソースの値を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-652">Get the value of a 32-bit Floating Point Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-653">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-653">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_float32(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-654">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-654">Description</span></span>

<span data-ttu-id="26a3a-655">このサービスを使用すると、32 ビット浮動小数点リソースの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-655">The service retrieves the value of a 32-bit Floating Point Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-656">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-656">Parameters</span></span>

- <span data-ttu-id="26a3a-657">**value**: リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-657">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="26a3a-658">**float32_ptr**: 宛先 32 ビット浮動小数点数値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-658">**float32_ptr**: Pointer to the destination 32-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-659">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-659">Return Values</span></span>

- <span data-ttu-id="26a3a-660">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-660">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-661">**NX_LWM2M_BAD_ENCODING**: リソース値は浮動小数点値ではありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-661">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_get_float64"></a><span data-ttu-id="26a3a-662">nx_lwm2m_resource_get_float64</span><span class="sxs-lookup"><span data-stu-id="26a3a-662">nx_lwm2m_resource_get_float64</span></span>

<span data-ttu-id="26a3a-663">64 ビット浮動小数点リソースの値を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-663">Get the value of a 64-bit Floating Point Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-664">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-664">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_float64(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-665">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-665">Description</span></span>

<span data-ttu-id="26a3a-666">このサービスを使用すると、64 ビット浮動小数点リソースの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-666">The service retrieves the value of a 64-bit Floating Point Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-667">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-667">Parameters</span></span>

- <span data-ttu-id="26a3a-668">**value**: リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-668">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="26a3a-669">**float64_ptr**: 宛先 64 ビット浮動小数点数値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-669">**float64_ptr**: Pointer to the destination 64-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-670">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-670">Return Values</span></span>

- <span data-ttu-id="26a3a-671">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-671">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-672">**NX_LWM2M_BAD_ENCODING**: リソース値は浮動小数点値ではありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-672">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_get_integer32"></a><span data-ttu-id="26a3a-673">nx_lwm2m_resource_get_integer32</span><span class="sxs-lookup"><span data-stu-id="26a3a-673">nx_lwm2m_resource_get_integer32</span></span>

<span data-ttu-id="26a3a-674">32 ビット整数リソースの値を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-674">Get the value of a 32-Bit Integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-675">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-675">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_integer32(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-676">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-676">Description</span></span>

<span data-ttu-id="26a3a-677">このサービスを使用すると、32 ビット整数リソースの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-677">The service retrieves the value of a 32-Bit Integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-678">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-678">Parameters</span></span>

- <span data-ttu-id="26a3a-679">**value**: リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-679">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="26a3a-680">**int32_ptr**: 宛先 32 ビット整数値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-680">**int32_ptr**: Pointer to the destination 32-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-681">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-681">Return Values</span></span>

- <span data-ttu-id="26a3a-682">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-682">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-683">**NX_LWM2M_BAD_ENCODING**: リソース値が整数値でないか、整数値が 32 ビットの数値に収まりません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-683">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Integer value, or the Integer value doesn't fit in a 32-Bit number.</span></span>

## <a name="nx_lwm2m_resource_get_integer64"></a><span data-ttu-id="26a3a-684">nx_lwm2m_resource_get_integer64</span><span class="sxs-lookup"><span data-stu-id="26a3a-684">nx_lwm2m_resource_get_integer64</span></span>

<span data-ttu-id="26a3a-685">64 ビット整数リソースの値を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-685">Get the value of a 64-Bit Integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-686">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-686">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_integer64(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-687">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-687">Description</span></span>

<span data-ttu-id="26a3a-688">このサービスを使用すると、64 ビット整数リソースの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-688">The service retrieves the value of a 64-Bit Integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-689">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-689">Parameters</span></span>

- <span data-ttu-id="26a3a-690">**value**: リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-690">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="26a3a-691">**int64_ptr**: 宛先 64 ビット整数値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-691">**int64_ptr**: Pointer to the destination 64-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-692">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-692">Return Values</span></span>

- <span data-ttu-id="26a3a-693">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-693">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-694">**NX_LWM2M_BAD_ENCODING**: リソース値が整数値ではありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-694">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Integer value.</span></span>

## <a name="nx_lwm2m_resource_get_objlnk"></a><span data-ttu-id="26a3a-695">nx_lwm2m_resource_get_objlnk</span><span class="sxs-lookup"><span data-stu-id="26a3a-695">nx_lwm2m_resource_get_objlnk</span></span>

<span data-ttu-id="26a3a-696">オブジェクト リンク リソースの値を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-696">Get the value of an Object Link Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-697">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-697">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_objlnk(const NX_LWM2M_RESOURCE *value,
                                    NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-698">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-698">Description</span></span>

<span data-ttu-id="26a3a-699">このサービスを使用すると、オブジェクト リンク リソースの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-699">The service retrieves the value of an Object Link Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-700">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-700">Parameters</span></span>

- <span data-ttu-id="26a3a-701">**value**: リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-701">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="26a3a-702">**objlnk_ptr**: 宛先オブジェクト リンク値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-702">**objlnk_ptr**: Pointer to the destination Object Link value.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-703">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-703">Return Values</span></span>

- <span data-ttu-id="26a3a-704">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-704">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-705">**NX_LWM2M_BAD_ENCODING**: リソース値がオブジェクト リンク値ではありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-705">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Object Link value.</span></span>

## <a name="nx_lwm2m_resource_get_opaque"></a><span data-ttu-id="26a3a-706">nx_lwm2m_resource_get_opaque</span><span class="sxs-lookup"><span data-stu-id="26a3a-706">nx_lwm2m_resource_get_opaque</span></span>

<span data-ttu-id="26a3a-707">非透過リソースの値を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-707">Get the value of an Opaque Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-708">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-708">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_opaque(const NX_LWM2M_RESOURCE *value,
            const VOID **opaque_ptr_ptr, UINT *opaque_length_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-709">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-709">Description</span></span>

<span data-ttu-id="26a3a-710">このサービスを使用すると、非透過リソースの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-710">The service retrieves the value of an Opaque Resource.</span></span>

<span data-ttu-id="26a3a-711">非透過リソース値は、バッファーへのポインターと長さで構成されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-711">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-712">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-712">Parameters</span></span>

- <span data-ttu-id="26a3a-713">**value**: リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-713">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="26a3a-714">**opaque_ptr_ptr**: 宛先の非透過バッファー ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-714">**opaque_ptr_ptr**: Pointer to the destination opaque buffer pointer.</span></span>
- <span data-ttu-id="26a3a-715">**opaque_length_ptr**: 宛先の非透過バッファー長へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-715">**opaque_length_ptr**: Pointer to the destination opaque buffer length.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-716">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-716">Return Values</span></span>

- <span data-ttu-id="26a3a-717">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-717">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-718">**NX_LWM2M_BAD_ENCODING**: リソース値が非透過値ではありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-718">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Opaque value.</span></span>

## <a name="nx_lwm2m_resource_get_string"></a><span data-ttu-id="26a3a-719">nx_lwm2m_resource_get_string</span><span class="sxs-lookup"><span data-stu-id="26a3a-719">nx_lwm2m_resource_get_string</span></span>

<span data-ttu-id="26a3a-720">文字列リソースの値を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-720">Get the value of a String Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-721">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-721">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_string(const NX_LWM2M_RESOURCE *value,
            const CHAR **string_ptr_ptr, UINT *string_length_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-722">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-722">Description</span></span>

<span data-ttu-id="26a3a-723">このサービスを使用すると、文字列リソースの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-723">The service retrieves the value of a String Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-724">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-724">Parameters</span></span>

- <span data-ttu-id="26a3a-725">**value**: リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-725">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="26a3a-726">**string_ptr_ptr**: 宛先文字列ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-726">**string_ptr_ptr**: Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="26a3a-727">**string_length_ptr**: 宛先文字列長へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-727">**string_length_ptr**: Pointer to the destination string length.</span></span> <span data-ttu-id="26a3a-728">文字列が null で終わる場合は NULL を指定できます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-728">Can be NULL if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-729">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-729">Return Values</span></span>

- <span data-ttu-id="26a3a-730">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-730">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-731">**NX_LWM2M_BAD_ENCODING**: リソース値が文字列値ではありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-731">**NX_LWM2M_BAD_ENCODING**: The resource value is not a String value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_boolean"></a><span data-ttu-id="26a3a-732">nx_lwm2m_resource_multiple_get_boolean</span><span class="sxs-lookup"><span data-stu-id="26a3a-732">nx_lwm2m_resource_multiple_get_boolean</span></span>

<span data-ttu-id="26a3a-733">ブール型リソースの複数リソース インスタンスの値を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-733">Get the value of a Boolean Resource Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-734">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-734">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_boolean(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-735">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-735">Description</span></span>

<span data-ttu-id="26a3a-736">このサービスを使用すると、複数リソースからブール値のリソース インスタンスの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-736">The service retrieves the value of a Boolean Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-737">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-737">Parameters</span></span>

- <span data-ttu-id="26a3a-738">**value**: 複数リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-738">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="26a3a-739">**index**: リソース値の配列で取得するインスタンスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="26a3a-739">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="26a3a-740">**instance_id_ptr**: 宛先インスタンス ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-740">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="26a3a-741">**bool_ptr**: 宛先ブール値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-741">**bool_ptr**: Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-742">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-742">Return Values</span></span>

- <span data-ttu-id="26a3a-743">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-743">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-744">**NX_LWM2M_BAD_PARAMETER**: インデックスは範囲外です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-744">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="26a3a-745">**NX_LWM2M_BAD_ENCODING**: リソースが複数リソースではないか、リソース値がブール値ではありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-745">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Boolean value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_float32"></a><span data-ttu-id="26a3a-746">nx_lwm2m_resource_multiple_get_float32</span><span class="sxs-lookup"><span data-stu-id="26a3a-746">nx_lwm2m_resource_multiple_get_float32</span></span>

<span data-ttu-id="26a3a-747">32 ビット浮動小数点の複数リソース インスタンスの値を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-747">Get the value of a 32-bit Floating Point Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-748">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-748">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_float32(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-749">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-749">Description</span></span>

<span data-ttu-id="26a3a-750">このサービスを使用すると、複数リソースから 32 ビット浮動小数点のリソース インスタンスの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-750">The service retrieves the value of a 32-bit Floating Point Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-751">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-751">Parameters</span></span>

- <span data-ttu-id="26a3a-752">**value**: 複数リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-752">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="26a3a-753">**index**: リソース値の配列で取得するインスタンスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="26a3a-753">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="26a3a-754">**instance_id_ptr**: 宛先インスタンス ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-754">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="26a3a-755">**float32_ptr**: 宛先 32 ビット浮動小数点数値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-755">**float32_ptr**: Pointer to the destination 32-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-756">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-756">Return Values</span></span>

- <span data-ttu-id="26a3a-757">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-757">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-758">**NX_LWM2M_BAD_PARAMETER**: インデックスは範囲外です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-758">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="26a3a-759">**NX_LWM2M_BAD_ENCODING**: リソースが複数リソースではないか、リソース値が浮動小数点値ではありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-759">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_float64"></a><span data-ttu-id="26a3a-760">nx_lwm2m_resource_multiple_get_float64</span><span class="sxs-lookup"><span data-stu-id="26a3a-760">nx_lwm2m_resource_multiple_get_float64</span></span>

<span data-ttu-id="26a3a-761">64 ビット浮動小数点の複数リソース インスタンスの値を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-761">Get the value of a 64-bit Floating Point Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-762">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-762">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_float64(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-763">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-763">Description</span></span>

<span data-ttu-id="26a3a-764">このサービスを使用すると、複数リソースから 64 ビット浮動小数点型のリソース インスタンスの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-764">The service retrieves the value of a 64-bit Floating Point Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-765">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-765">Parameters</span></span>

- <span data-ttu-id="26a3a-766">**value**: 複数リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-766">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="26a3a-767">**index**: リソース値の配列で取得するインスタンスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="26a3a-767">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="26a3a-768">**instance_id_ptr**: 宛先インスタンス ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-768">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="26a3a-769">**float64_ptr**: 宛先 64 ビット浮動小数点数値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-769">**float64_ptr**: Pointer to the destination 64-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-770">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-770">Return Values</span></span>

- <span data-ttu-id="26a3a-771">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-771">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-772">**NX_LWM2M_BAD_PARAMETER**: インデックスは範囲外です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-772">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="26a3a-773">**NX_LWM2M_BAD_ENCODING**: リソースが複数リソースではないか、リソース値が浮動小数点値ではありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-773">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_integer32"></a><span data-ttu-id="26a3a-774">nx_lwm2m_resource_multiple_get_integer32</span><span class="sxs-lookup"><span data-stu-id="26a3a-774">nx_lwm2m_resource_multiple_get_integer32</span></span>

<span data-ttu-id="26a3a-775">32 ビット整数の複数リソース インスタンスの値を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-775">Get the value of a 32-Bit Integer Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-776">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-776">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_integer32(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-777">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-777">Description</span></span>

<span data-ttu-id="26a3a-778">このサービスを使用すると、複数リソースから 32 ビット整数のリソース インスタンスの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-778">The service retrieves the value of a 32-Bit Integer Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-779">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-779">Parameters</span></span>

- <span data-ttu-id="26a3a-780">**value**: 複数リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-780">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="26a3a-781">**index**: リソース値の配列で取得するインスタンスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="26a3a-781">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="26a3a-782">**instance_id_ptr**: 宛先インスタンス ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-782">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="26a3a-783">**int32_ptr**: 宛先 32 ビット整数値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-783">**int32_ptr**: Pointer to the destination 32-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-784">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-784">Return Values</span></span>

- <span data-ttu-id="26a3a-785">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-785">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-786">**NX_LWM2M_BAD_PARAMETER**: インデックスは範囲外です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-786">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="26a3a-787">**NX_LWM2M_BAD_ENCODING**: リソースが複数リソースではないか、リソース値が整数値ではないか、整数値が 32 ビットの数値に収まりません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-787">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Integer value, or the Integer value doesn't fit in a 32-Bit number.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_integer64"></a><span data-ttu-id="26a3a-788">nx_lwm2m_resource_multiple_get_integer64</span><span class="sxs-lookup"><span data-stu-id="26a3a-788">nx_lwm2m_resource_multiple_get_integer64</span></span>

<span data-ttu-id="26a3a-789">64 ビット整数の複数リソース インスタンスの値を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-789">Get the value of a 64-Bit Integer Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-790">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-790">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_integer64(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-791">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-791">Description</span></span>

<span data-ttu-id="26a3a-792">このサービスを使用すると、複数リソースから 64 ビット整数のリソース インスタンスの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-792">The service retrieves the value of a 64-Bit Integer Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-793">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-793">Parameters</span></span>

- <span data-ttu-id="26a3a-794">**value**: 複数リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-794">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="26a3a-795">**index**: リソース値の配列で取得するインスタンスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="26a3a-795">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="26a3a-796">**instance_id_ptr**: 宛先インスタンス ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-796">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="26a3a-797">**int64_ptr**: 宛先 64 ビット整数値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-797">**int64_ptr**: Pointer to the destination 64-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-798">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-798">Return Values</span></span>

- <span data-ttu-id="26a3a-799">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-799">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-800">**NX_LWM2M_BAD_PARAMETER**: インデックスは範囲外です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-800">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="26a3a-801">**NX_LWM2M_BAD_ENCODING**: リソースが複数リソースではないか、リソース値が整数値ではありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-801">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Integer value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_objlnk"></a><span data-ttu-id="26a3a-802">nx_lwm2m_resource_multiple_get_objlnk</span><span class="sxs-lookup"><span data-stu-id="26a3a-802">nx_lwm2m_resource_multiple_get_objlnk</span></span>

<span data-ttu-id="26a3a-803">オブジェクト リンクの複数リソース インスタンスの値を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-803">Get the value of an Object Link Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-804">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-804">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_objlnk(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-805">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-805">Description</span></span>

<span data-ttu-id="26a3a-806">このサービスを使用すると、複数リソースからオブジェクト リンクのリソース インスタンスの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-806">The service retrieves the value of an Object Link Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-807">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-807">Parameters</span></span>

- <span data-ttu-id="26a3a-808">**value**: 複数リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-808">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="26a3a-809">**index**: リソース値の配列で取得するインスタンスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="26a3a-809">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="26a3a-810">**instance_id_ptr**: 宛先インスタンス ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-810">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="26a3a-811">**objlnk_ptr**: 宛先オブジェクト リンク値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-811">**objlnk_ptr**: Pointer to the destination Object Link value.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-812">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-812">Return Values</span></span>

- <span data-ttu-id="26a3a-813">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-813">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-814">**NX_LWM2M_BAD_PARAMETER**: インデックスは範囲外です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-814">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="26a3a-815">**NX_LWM2M_BAD_ENCODING**: リソースが複数リソースではないか、リソース値がオブジェクト リンク値ではありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-815">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Object Link value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_opaque"></a><span data-ttu-id="26a3a-816">nx_lwm2m_resource_multiple_get_opaque</span><span class="sxs-lookup"><span data-stu-id="26a3a-816">nx_lwm2m_resource_multiple_get_opaque</span></span>

<span data-ttu-id="26a3a-817">非透過複数リソース インスタンスの値を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-817">Get the value of an Opaque Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-818">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-818">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_opaque(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const VOID **opaque_ptr_ptr,
    UINT *opaque_length_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-819">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-819">Description</span></span>

<span data-ttu-id="26a3a-820">このサービスを使用すると、複数リソースから非透過のリソース インスタンスの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-820">The service retrieves the value of an Opaque Resource Instance from a Multiple Resource.</span></span>

<span data-ttu-id="26a3a-821">非透過リソース値は、バッファーへのポインターと長さで構成されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-821">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-822">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-822">Parameters</span></span>

- <span data-ttu-id="26a3a-823">**value**: 複数リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-823">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="26a3a-824">**index**: リソース値の配列で取得するインスタンスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="26a3a-824">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="26a3a-825">**instance_id_ptr**: 宛先インスタンス ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-825">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="26a3a-826">**opaque_ptr_ptr**: 宛先の非透過バッファー ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-826">**opaque_ptr_ptr**: Pointer to the destination opaque buffer pointer.</span></span>
- <span data-ttu-id="26a3a-827">**opaque_length_ptr**: 宛先の非透過バッファー長へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-827">**opaque_length_ptr**: Pointer to the destination opaque buffer length.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-828">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-828">Return Values</span></span>

- <span data-ttu-id="26a3a-829">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-829">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-830">**NX_LWM2M_BAD_PARAMETER**: インデックスは範囲外です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-830">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="26a3a-831">**NX_LWM2M_BAD_ENCODING**: リソースが複数リソースではないか、リソース値が非透過値ではありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-831">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Opaque value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_string"></a><span data-ttu-id="26a3a-832">nx_lwm2m_resource_multiple_get_string</span><span class="sxs-lookup"><span data-stu-id="26a3a-832">nx_lwm2m_resource_multiple_get_string</span></span>

<span data-ttu-id="26a3a-833">文字列の複数リソース インスタンスの値を取得します</span><span class="sxs-lookup"><span data-stu-id="26a3a-833">Get the value of a String Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26a3a-834">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="26a3a-834">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_string(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const CHAR **string_ptr_ptr,
    UINT *string_length_ptr);
```

### <a name="description"></a><span data-ttu-id="26a3a-835">説明</span><span class="sxs-lookup"><span data-stu-id="26a3a-835">Description</span></span>

<span data-ttu-id="26a3a-836">このサービスを使用すると、複数リソースから文字列のリソース インスタンスの値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-836">The service retrieves the value of a String Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="26a3a-837">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26a3a-837">Parameters</span></span>

- <span data-ttu-id="26a3a-838">**value**: 複数リソース値の説明へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-838">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="26a3a-839">**index**: リソース値の配列で取得するインスタンスのインデックス。</span><span class="sxs-lookup"><span data-stu-id="26a3a-839">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="26a3a-840">**instance_id_ptr**: 宛先インスタンス ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-840">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="26a3a-841">**string_ptr_ptr**: 宛先文字列ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-841">**string_ptr_ptr**: Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="26a3a-842">**string_length_ptr**: 宛先文字列長へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26a3a-842">**string_length_ptr**: Pointer to the destination string length.</span></span> <span data-ttu-id="26a3a-843">文字列が null で終わる場合は NULL を指定できます。</span><span class="sxs-lookup"><span data-stu-id="26a3a-843">Can be NULL if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="26a3a-844">戻り値</span><span class="sxs-lookup"><span data-stu-id="26a3a-844">Return Values</span></span>

- <span data-ttu-id="26a3a-845">**NX_SUCCESS**: 操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="26a3a-845">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="26a3a-846">**NX_LWM2M_BAD_PARAMETER**: インデックスは範囲外です。</span><span class="sxs-lookup"><span data-stu-id="26a3a-846">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="26a3a-847">**NX_LWM2M_BAD_ENCODING**: リソースが複数リソースではないか、インスタンス値が文字列値ではありません。</span><span class="sxs-lookup"><span data-stu-id="26a3a-847">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the instance value is not a String value.</span></span>
