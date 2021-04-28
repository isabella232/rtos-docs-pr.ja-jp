---
title: 第 3 章 - POP3 クライアント サービスの説明
description: この章では、すべての NetX Duo POP3 クライアント サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1f7681c8f3fe161db8a37a82574ab7d5e9bf348e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810658"
---
# <a name="chapter-3---description-of-pop3-client-services"></a><span data-ttu-id="bffa4-103">第 3 章 - POP3 クライアント サービスの説明</span><span class="sxs-lookup"><span data-stu-id="bffa4-103">Chapter 3 - Description of POP3 Client Services</span></span>

<span data-ttu-id="bffa4-104">この章では、すべての NetX Duo POP3 クライアント サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="bffa4-104">This chapter contains a description of all NetX Duo POP3 Client services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="bffa4-105">以下の API の説明の「戻り値」セクションで、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字でない値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="bffa4-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_pop3_client_create"></a><span data-ttu-id="bffa4-106">nx_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="bffa4-106">nx_pop3_client_create</span></span>

<span data-ttu-id="bffa4-107">IPv4 用の POP3 クライアント インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="bffa4-107">Create a POP3 Client instance for IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="bffa4-108">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="bffa4-108">Prototype</span></span>

```C
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    ULONG server_ip_address, ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="bffa4-109">説明</span><span class="sxs-lookup"><span data-stu-id="bffa4-109">Description</span></span>

<span data-ttu-id="bffa4-110">このサービスは、POP3 クライアントのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="bffa4-110">This service creates an instance of the POP3 Client.</span></span> <span data-ttu-id="bffa4-111">IPv4 POP3 サーバー アドレスのみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bffa4-111">It supports only IPv4 POP3 server addresses.</span></span>

<span data-ttu-id="bffa4-112">デバイス アプリケーションでは、POP3 クライアントがパケットを送信するための IP インスタンスとパケット プールを最初に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bffa4-112">Note that the device application must first create an IP instance and a packet pool for the POP3 Client to transmit packets.</span></span> <span data-ttu-id="bffa4-113">POP3 クライアント タスク専用のパケット プールを作成するか、IP インスタンスの作成に使用したものと同じパケット プールを使用します。</span><span class="sxs-lookup"><span data-stu-id="bffa4-113">This packet pool created for use exclusively by the POP3 Client task or the same packet pool used in the IP instance creation.</span></span> <span data-ttu-id="bffa4-114">パケット プールはイーサネット ドライバーのパケット プールと共有することもできますが、これには欠点があります。POP3 クライアントが比較的小さな POP3 メッセージ パケットをサーバーに送信するために、サイズが大きい可能性のあるパケット ペイロードを受信することを目的とした大きなパケット プールを使用することになります。</span><span class="sxs-lookup"><span data-stu-id="bffa4-114">The packet pool may also be shared with the Ethernet driver packet pool but this has the disadvantage of using large packet pools whose payload is intended for receiving potentially large packets payload for the POP3 Client to send relatively small POP3 message packets to the server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bffa4-115">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="bffa4-115">Input Parameters</span></span>

- <span data-ttu-id="bffa4-116">**client_ptr**: 作成するクライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-116">**client_ptr** Pointer to Client to create</span></span>
- <span data-ttu-id="bffa4-117">**APOP_authentication**: APOP 認証を有効にします</span><span class="sxs-lookup"><span data-stu-id="bffa4-117">**APOP_authentication** Enable APOP authentication</span></span>
- <span data-ttu-id="bffa4-118">**ip_ptr**: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-118">**ip_ptr Pointer** to IP instance</span></span>
- <span data-ttu-id="bffa4-119">**packet_pool_ptr**: クライアントのパケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-119">**packet_pool_ptr** Pointer to Client packet pool</span></span>
- <span data-ttu-id="bffa4-120">**server_ip_address**: POP3 サーバーの IPv4 アドレス</span><span class="sxs-lookup"><span data-stu-id="bffa4-120">**server_ip_address** POP3 server IPv4 address</span></span>
- <span data-ttu-id="bffa4-121">**server_port**: POP3 サーバー ポート</span><span class="sxs-lookup"><span data-stu-id="bffa4-121">**server_port** POP3 server port</span></span>
- <span data-ttu-id="bffa4-122">**client_name**: クライアント名へのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-122">**client_name** Pointer to Client name</span></span>
- <span data-ttu-id="bffa4-123">**client_password**: クライアント パスワードへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-123">**client_password** Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="bffa4-124">戻り値</span><span class="sxs-lookup"><span data-stu-id="bffa4-124">Return Values</span></span>

- <span data-ttu-id="bffa4-125">**NX_SUCCESS**: (0x00) クライアントが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="bffa4-125">**NX_SUCCESS** (0x00) Client successfully created</span></span>
- <span data-ttu-id="bffa4-126">**status**: NetX Duo および ThreadX サービス呼び出しの完了状態</span><span class="sxs-lookup"><span data-stu-id="bffa4-126">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
- <span data-ttu-id="bffa4-127">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="bffa4-127">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="bffa4-128">NX_POP3_PARAM_ERROR: (0xB1) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="bffa4-128">NX_POP3_PARAM_ERROR (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bffa4-129">許可元</span><span class="sxs-lookup"><span data-stu-id="bffa4-129">Allowed From</span></span>

<span data-ttu-id="bffa4-130">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="bffa4-130">Application code</span></span>

### <a name="example"></a><span data-ttu-id="bffa4-131">例</span><span class="sxs-lookup"><span data-stu-id="bffa4-131">Example</span></span>

```C
/* Create the POP3 Client. Note that the Client uses its password for its APOP shared
    secret. */

/* Set up user defined callback services. */
/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_ADDRESS IP_ADDRESS(192,2,2,92)
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. */
status = nx_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    POP3_SERVER_ADDRESS, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nxd_pop3_client_create"></a><span data-ttu-id="bffa4-132">nxd_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="bffa4-132">nxd_pop3_client_create</span></span>

<span data-ttu-id="bffa4-133">IPv4 または IPv6 用の POP3 クライアント インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="bffa4-133">Create a POP3 Client instance for IPv4 or IPv6</span></span>

### <a name="prototype"></a><span data-ttu-id="bffa4-134">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="bffa4-134">Prototype</span></span>

```C
UINT nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    NXD_ADDRESS *server_ip_address,
    ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="bffa4-135">説明</span><span class="sxs-lookup"><span data-stu-id="bffa4-135">Description</span></span>

<span data-ttu-id="bffa4-136">このサービスは、POP3 クライアントのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="bffa4-136">This service creates an instance of the POP3 Client.</span></span> <span data-ttu-id="bffa4-137">IPv4 と IPv6 の両方の POP3 サーバー アドレスがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bffa4-137">It supports both IPv4 and IPv6 POP3 server addresses.</span></span> <span data-ttu-id="bffa4-138">POP3 クライアントの作成プロセスの詳細については、前述の *nx_pop3_client_create* サービスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bffa4-138">See the previously described *nx_pop3_client_create* service for more details on POP3 Client create process.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bffa4-139">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="bffa4-139">Input Parameters</span></span>

- <span data-ttu-id="bffa4-140">**client_ptr**: 作成するクライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-140">**client_ptr** Pointer to Client to create</span></span>
- <span data-ttu-id="bffa4-141">**APOP_authentication**: APOP 認証を有効にします</span><span class="sxs-lookup"><span data-stu-id="bffa4-141">**APOP_authentication** Enable APOP authentication</span></span>
- <span data-ttu-id="bffa4-142">**ip_ptr**: IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-142">**ip_ptr** Pointer to IP instance</span></span>
- <span data-ttu-id="bffa4-143">**packet_pool_ptr**: クライアントのパケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-143">**packet_pool_ptr** Pointer to Client packet pool</span></span>
- <span data-ttu-id="bffa4-144">**server_ip_address**: POP3 サーバーの IPv6 または IPv4 アドレス</span><span class="sxs-lookup"><span data-stu-id="bffa4-144">**server_ip_address** POP3 server IPv6 or IPv4 address</span></span>
- <span data-ttu-id="bffa4-145">**server_port**: POP3 サーバー ポート</span><span class="sxs-lookup"><span data-stu-id="bffa4-145">**server_port** POP3 server port</span></span>
- <span data-ttu-id="bffa4-146">**client_name**: クライアント名へのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-146">**client_name**  Pointer to Client name</span></span>
- <span data-ttu-id="bffa4-147">**client_password**: クライアント パスワードへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-147">**client_password** Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="bffa4-148">戻り値</span><span class="sxs-lookup"><span data-stu-id="bffa4-148">Return Values</span></span>

- <span data-ttu-id="bffa4-149">**NX_SUCCESS**: (0x00) クライアントが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="bffa4-149">**NX_SUCCESS** (0x00) Client successfully created</span></span>
- <span data-ttu-id="bffa4-150">**status**: NetX Duo および ThreadX サービス呼び出しの完了状態</span><span class="sxs-lookup"><span data-stu-id="bffa4-150">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
- <span data-ttu-id="bffa4-151">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="bffa4-151">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="bffa4-152">NX_POP3_PARAM_ERROR: (0xB1) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="bffa4-152">NX_POP3_PARAM_ERROR (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bffa4-153">許可元</span><span class="sxs-lookup"><span data-stu-id="bffa4-153">Allowed From</span></span>

<span data-ttu-id="bffa4-154">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="bffa4-154">Application code</span></span>

### <a name="example"></a><span data-ttu-id="bffa4-155">例</span><span class="sxs-lookup"><span data-stu-id="bffa4-155">Example</span></span>

```C
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. Also note the details of IPv6 address validation
    and enabling IPv6 and ICMPv6 services on the IP task are not shown here. See the
    NetX Duo User Guide for more details on this process.
*/
NXD_ADDRESS server_ip_address;

/* Set client IP interface address. */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0xf101;
server_ip_address.nxd_ip_address.v6[2] = 0;
server_ip_address.nxd_ip_address.v6[3] = 0x101;
status = nxd_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    &server_ip_address, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a><span data-ttu-id="bffa4-156">nx_pop3_client_delete</span><span class="sxs-lookup"><span data-stu-id="bffa4-156">nx_pop3_client_delete</span></span>

<span data-ttu-id="bffa4-157">POP3 クライアント インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="bffa4-157">Delete a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="bffa4-158">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="bffa4-158">Prototype</span></span>

```C
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="bffa4-159">説明</span><span class="sxs-lookup"><span data-stu-id="bffa4-159">Description</span></span>

<span data-ttu-id="bffa4-160">このサービスは、以前に作成された POP3 クライアントを削除します。</span><span class="sxs-lookup"><span data-stu-id="bffa4-160">This service deletes a previously created POP3 Client.</span></span> <span data-ttu-id="bffa4-161">このサービスでは、POP3 クライアントのパケット プールは削除されません。</span><span class="sxs-lookup"><span data-stu-id="bffa4-161">Not that this service does not delete the POP3 Client packet pool.</span></span> <span data-ttu-id="bffa4-162">パケット プールを使用しなくなった場合は、デバイス アプリケーションでこのリソースを個別に削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bffa4-162">The device application must delete this resource separately if it no longer has use for the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bffa4-163">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="bffa4-163">Input Parameters</span></span>

- <span data-ttu-id="bffa4-164">**client_ptr**: 削除するクライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-164">**client_ptr** Pointer to Client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="bffa4-165">戻り値</span><span class="sxs-lookup"><span data-stu-id="bffa4-165">Return Values</span></span>

- <span data-ttu-id="bffa4-166">**NX_SUCCESS**: (0x00) クライアントが正常に削除されました</span><span class="sxs-lookup"><span data-stu-id="bffa4-166">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="bffa4-167">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="bffa4-167">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bffa4-168">許可元</span><span class="sxs-lookup"><span data-stu-id="bffa4-168">Allowed From</span></span>

<span data-ttu-id="bffa4-169">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="bffa4-169">Application code</span></span>

### <a name="example"></a><span data-ttu-id="bffa4-170">例</span><span class="sxs-lookup"><span data-stu-id="bffa4-170">Example</span></span>

```C
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a><span data-ttu-id="bffa4-171">nx_pop3_client_mail_item_delete</span><span class="sxs-lookup"><span data-stu-id="bffa4-171">nx_pop3_client_mail_item_delete</span></span>

<span data-ttu-id="bffa4-172">指定されたメール アイテムをクライアントのメールドロップから削除する</span><span class="sxs-lookup"><span data-stu-id="bffa4-172">Delete a specified mail item from the Client maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="bffa4-173">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="bffa4-173">Prototype</span></span>

```C
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
    UINT mail_index);
```

### <a name="description"></a><span data-ttu-id="bffa4-174">説明</span><span class="sxs-lookup"><span data-stu-id="bffa4-174">Description</span></span>

<span data-ttu-id="bffa4-175">このサービスは、指定されたメール アイテムをクライアントのメールドロップから削除します。</span><span class="sxs-lookup"><span data-stu-id="bffa4-175">This service deletes the specified mail item from the Client maildrop.</span></span> <span data-ttu-id="bffa4-176">これはメール アイテムのダウンロード後を対象としていますが、クライアントから要求された後にメール アイテムを自動的に削除する POP3 サーバーもあります。</span><span class="sxs-lookup"><span data-stu-id="bffa4-176">It is intended for after downloading the mail item, although some POP3 servers may automatically delete mail items after being requested by the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bffa4-177">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="bffa4-177">Input Parameters</span></span>

- <span data-ttu-id="bffa4-178">**client_ptr**: クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-178">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="bffa4-179">**mail_index**: クライアントのメールドロップへのインデックス</span><span class="sxs-lookup"><span data-stu-id="bffa4-179">**mail_index** Index into Client maildrop</span></span>

### <a name="return-values"></a><span data-ttu-id="bffa4-180">戻り値</span><span class="sxs-lookup"><span data-stu-id="bffa4-180">Return Values</span></span>

- <span data-ttu-id="bffa4-181">**NX_SUCCESS**: (0x00) 削除要求が成功しました</span><span class="sxs-lookup"><span data-stu-id="bffa4-181">**NX_SUCCESS** (0x00) Delete request successful</span></span>
- <span data-ttu-id="bffa4-182">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) メール アイテムのインデックスが無効です</span><span class="sxs-lookup"><span data-stu-id="bffa4-182">**NX_POP3_INVALID_MAIL_ITEM**(0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="bffa4-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます</span><span class="sxs-lookup"><span data-stu-id="bffa4-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**(0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="bffa4-184">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) サーバーがエラー状態で応答しました</span><span class="sxs-lookup"><span data-stu-id="bffa4-184">**NX_POP3_SERVER_ERROR_STATUS**(0xB4) Server replies with error status</span></span>
- <span data-ttu-id="bffa4-185">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) メール インデックス入力が無効です</span><span class="sxs-lookup"><span data-stu-id="bffa4-185">NX_POP3_CLIENT_INVALID_INDEX(0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="bffa4-186">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="bffa4-186">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bffa4-187">許可元</span><span class="sxs-lookup"><span data-stu-id="bffa4-187">Allowed From</span></span>

<span data-ttu-id="bffa4-188">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="bffa4-188">Application code</span></span>

### <a name="example"></a><span data-ttu-id="bffa4-189">例</span><span class="sxs-lookup"><span data-stu-id="bffa4-189">Example</span></span>

```C
ULONG item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status =
    NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a><span data-ttu-id="bffa4-190">nx_pop3_client_mail_item_get</span><span class="sxs-lookup"><span data-stu-id="bffa4-190">nx_pop3_client_mail_item_get</span></span>

<span data-ttu-id="bffa4-191">指定されたメール アイテムを取得する</span><span class="sxs-lookup"><span data-stu-id="bffa4-191">Retrieve a specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="bffa4-192">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="bffa4-192">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *item_size);
```

### <a name="description"></a><span data-ttu-id="bffa4-193">説明</span><span class="sxs-lookup"><span data-stu-id="bffa4-193">Description</span></span>

<span data-ttu-id="bffa4-194">このサービスは RETR 要求を行って、クライアントのメールドロップから、インデックス mail_item で指定されたメール アイテムを取得します。</span><span class="sxs-lookup"><span data-stu-id="bffa4-194">This service makes a RETR request to retrieve a mail item from the Client maildrop specified by the index mail_item.</span></span> <span data-ttu-id="bffa4-195">RETR 要求を行い、サーバーから肯定応答を受信したら、クライアントは *nx_pop3_client_mail_item_message_get* サービスを使用して、メール メッセージのダウンロードを開始できます。</span><span class="sxs-lookup"><span data-stu-id="bffa4-195">After making a RETR request, and receiving a positive response from the Server, the Client can start downloading the mail message using the *nx_pop3_client_mail_item_message_get* service.</span></span> <span data-ttu-id="bffa4-196">このサービスは、サーバーの応答から抽出された、要求されたメール アイテムのサイズも提供します。</span><span class="sxs-lookup"><span data-stu-id="bffa4-196">Note that the service also supplies the size of the requested mail item extracted from the Server reply.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bffa4-197">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="bffa4-197">Input Parameters</span></span>

- <span data-ttu-id="bffa4-198">**client_ptr**: クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-198">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="bffa4-199">**mail_item**: クライアントのメールドロップへのインデックス</span><span class="sxs-lookup"><span data-stu-id="bffa4-199">**mail_item** Index into Client maildrop</span></span>
- <span data-ttu-id="bffa4-200">**item_size**: メール メッセージのサイズへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-200">**item_size** Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="bffa4-201">戻り値</span><span class="sxs-lookup"><span data-stu-id="bffa4-201">Return Values</span></span>

- <span data-ttu-id="bffa4-202">**NX_SUCCESS**: (0x00) メール アイテムが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="bffa4-202">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="bffa4-203">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) メール アイテムのインデックスが無効です</span><span class="sxs-lookup"><span data-stu-id="bffa4-203">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="bffa4-204">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます</span><span class="sxs-lookup"><span data-stu-id="bffa4-204">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="bffa4-205">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) サーバーがエラー状態で応答しました</span><span class="sxs-lookup"><span data-stu-id="bffa4-205">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="bffa4-206">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) メール インデックス入力が無効です</span><span class="sxs-lookup"><span data-stu-id="bffa4-206">NX_POP3_CLIENT_INVALID_INDEX (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="bffa4-207">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="bffa4-207">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bffa4-208">許可元</span><span class="sxs-lookup"><span data-stu-id="bffa4-208">Allowed From</span></span>

<span data-ttu-id="bffa4-209">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="bffa4-209">Application code</span></span>

### <a name="example"></a><span data-ttu-id="bffa4-210">例</span><span class="sxs-lookup"><span data-stu-id="bffa4-210">Example</span></span>

```C
ULONG item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a><span data-ttu-id="bffa4-211">nx_pop3_client_mail_items_get</span><span class="sxs-lookup"><span data-stu-id="bffa4-211">nx_pop3_client_mail_items_get</span></span>

<span data-ttu-id="bffa4-212">メールドロップ内のメール アイテムの数を取得する</span><span class="sxs-lookup"><span data-stu-id="bffa4-212">Retrieve the number of mail items in maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="bffa4-213">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="bffa4-213">Prototype</span></span>

```C
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
    UINT *number_mail_items,
    ULONG *maildrop_total_size);
```

### <a name="description"></a><span data-ttu-id="bffa4-214">説明</span><span class="sxs-lookup"><span data-stu-id="bffa4-214">Description</span></span>

<span data-ttu-id="bffa4-215">このサービスは STAT 要求を行って、クライアントのメールドロップからメール アイテムの数とメール メッセージ データの合計サイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="bffa4-215">This service makes a STAT request to retrieve the number of mail items and total size of mail message data from the Client maildrop.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bffa4-216">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="bffa4-216">Input Parameters</span></span>

- <span data-ttu-id="bffa4-217">**client_ptr**: クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-217">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="bffa4-218">**number_mail_item**: クライアントのメールドロップ内のメール数</span><span class="sxs-lookup"><span data-stu-id="bffa4-218">**number_mail_item** Number of mail in Client maildrop</span></span>
- <span data-ttu-id="bffa4-219">**maildrop_total_size**: すべてのメール メッセージのサイズへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-219">**maildrop_total_size** Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="bffa4-220">戻り値</span><span class="sxs-lookup"><span data-stu-id="bffa4-220">Return Values</span></span>

- <span data-ttu-id="bffa4-221">**NX_SUCCESS**: (0x00) メール アイテムが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="bffa4-221">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="bffa4-222">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) メール アイテムのインデックスが無効です</span><span class="sxs-lookup"><span data-stu-id="bffa4-222">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="bffa4-223">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます</span><span class="sxs-lookup"><span data-stu-id="bffa4-223">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="bffa4-224">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) サーバーがエラー状態で応答しました</span><span class="sxs-lookup"><span data-stu-id="bffa4-224">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="bffa4-225">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="bffa4-225">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bffa4-226">許可元</span><span class="sxs-lookup"><span data-stu-id="bffa4-226">Allowed From</span></span>

<span data-ttu-id="bffa4-227">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="bffa4-227">Application code</span></span>

### <a name="example"></a><span data-ttu-id="bffa4-228">例</span><span class="sxs-lookup"><span data-stu-id="bffa4-228">Example</span></span>

```C
UINT number_mail_items;

ULONG maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
    &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a><span data-ttu-id="bffa4-229">nx_pop3_client_mail_item_message_get</span><span class="sxs-lookup"><span data-stu-id="bffa4-229">nx_pop3_client_mail_item_message_get</span></span>

<span data-ttu-id="bffa4-230">指定されたメール アイテム メッセージを取得する</span><span class="sxs-lookup"><span data-stu-id="bffa4-230">Retrieve the specified mail item message</span></span>

### <a name="prototype"></a><span data-ttu-id="bffa4-231">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="bffa4-231">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_message_get(
    NX_POP3_CLIENT *client_ptr,
    NX_PACKET **recv_packet_ptr,
    ULONG *bytes_retrieved,
    UINT *final_packet);
```

### <a name="description"></a><span data-ttu-id="bffa4-232">説明</span><span class="sxs-lookup"><span data-stu-id="bffa4-232">Description</span></span>

<span data-ttu-id="bffa4-233">このサービスは、メール アイテム メッセージ、メール メッセージのサイズ、メール メッセージの最後のパケットかどうかを取得します。</span><span class="sxs-lookup"><span data-stu-id="bffa4-233">This service retrieves the mail item message, size of the mail message, and if it is the last packet in the mail message.</span></span> <span data-ttu-id="bffa4-234">final_packet が NX_TRUE の場合、recv_packet_ptr が指すパケットは、メール アイテム メッセージの最後のパケットになります。</span><span class="sxs-lookup"><span data-stu-id="bffa4-234">If final_packet is NX_TRUE the packet pointed to by recv_packet_ptr is the final packet in the mail item message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bffa4-235">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="bffa4-235">Input Parameters</span></span>

- <span data-ttu-id="bffa4-236">**client_ptr**: クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-236">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="bffa4-237">**recv_packet_ptr**: メッセージ データの受信パケット</span><span class="sxs-lookup"><span data-stu-id="bffa4-237">**recv_packet_ptr** Received packet of message data</span></span>
- <span data-ttu-id="bffa4-238">**number_mail_item**: クライアントのメールドロップ内のメール数</span><span class="sxs-lookup"><span data-stu-id="bffa4-238">**number_mail_item** Number of mail in Client maildrop</span></span>
- <span data-ttu-id="bffa4-239">**maildrop_total_size**: すべてのメール メッセージのサイズへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-239">**maildrop_total_size** Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="bffa4-240">戻り値</span><span class="sxs-lookup"><span data-stu-id="bffa4-240">Return Values</span></span>

- <span data-ttu-id="bffa4-241">**NX_SUCCESS**: (0x00) メール アイテムが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="bffa4-241">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="bffa4-242">**NX_POP3_CLIENT_INVALID_STATE**: (0xB7) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます</span><span class="sxs-lookup"><span data-stu-id="bffa4-242">**NX_POP3_CLIENT_INVALID_STATE** (0xB7) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="bffa4-243">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="bffa4-243">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bffa4-244">許可元</span><span class="sxs-lookup"><span data-stu-id="bffa4-244">Allowed From</span></span>

<span data-ttu-id="bffa4-245">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="bffa4-245">Application code</span></span>

### <a name="example"></a><span data-ttu-id="bffa4-246">例</span><span class="sxs-lookup"><span data-stu-id="bffa4-246">Example</span></span>

```C
NX_PACKET *recv_packet_ptr;

ULONG bytes_retrieved;

UINT final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
    bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a><span data-ttu-id="bffa4-247">nx_pop3_client_mail_item_size_get</span><span class="sxs-lookup"><span data-stu-id="bffa4-247">nx_pop3_client_mail_item_size_get</span></span>

<span data-ttu-id="bffa4-248">指定されたメール アイテムのサイズを取得する</span><span class="sxs-lookup"><span data-stu-id="bffa4-248">Retrieve the size of the specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="bffa4-249">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="bffa4-249">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_size_get(
    NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *size);
```

### <a name="description"></a><span data-ttu-id="bffa4-250">説明</span><span class="sxs-lookup"><span data-stu-id="bffa4-250">Description</span></span>

<span data-ttu-id="bffa4-251">このサービスは LIST 要求を行って、指定されたメール アイテムのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="bffa4-251">This service makes a LIST request to obtain the size of the specified mail item.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bffa4-252">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="bffa4-252">Input Parameters</span></span>

- <span data-ttu-id="bffa4-253">**client_ptr**: クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-253">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="bffa4-254">**mail_item**: クライアントのメールドロップへのインデックス</span><span class="sxs-lookup"><span data-stu-id="bffa4-254">**mail_item** Index into Client maildrop</span></span>
- <span data-ttu-id="bffa4-255">**size**: メール メッセージのサイズへのポインター</span><span class="sxs-lookup"><span data-stu-id="bffa4-255">**size** Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="bffa4-256">戻り値</span><span class="sxs-lookup"><span data-stu-id="bffa4-256">Return Values</span></span>

- <span data-ttu-id="bffa4-257">**NX_SUCCESS**: (0x00) メール アイテムが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="bffa4-257">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="bffa4-258">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) メール アイテムのインデックスが無効です</span><span class="sxs-lookup"><span data-stu-id="bffa4-258">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="bffa4-259">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます</span><span class="sxs-lookup"><span data-stu-id="bffa4-259">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="bffa4-260">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) サーバーがエラー状態で応答しました</span><span class="sxs-lookup"><span data-stu-id="bffa4-260">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="bffa4-261">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) メール インデックス入力が無効です</span><span class="sxs-lookup"><span data-stu-id="bffa4-261">NX_POP3_CLIENT_INVALID_INDEX (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="bffa4-262">NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="bffa4-262">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bffa4-263">許可元</span><span class="sxs-lookup"><span data-stu-id="bffa4-263">Allowed From</span></span>

<span data-ttu-id="bffa4-264">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="bffa4-264">Application code</span></span>

### <a name="example"></a><span data-ttu-id="bffa4-265">例</span><span class="sxs-lookup"><span data-stu-id="bffa4-265">Example</span></span>

```C
ULONG size;

UINT mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
