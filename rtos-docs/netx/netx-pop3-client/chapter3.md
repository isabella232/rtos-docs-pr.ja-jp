---
title: 第 3 章 - Azure RTOS NetX POP3 クライアント サービスの説明
description: この章では、Azure RTOS NetX POP3 エージェントのすべてのサービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1a0ab96a454bea9f56ced0d7aa8de5d481b284e9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811477"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pop3-client-services"></a><span data-ttu-id="90024-103">第 3 章 - Azure RTOS NetX POP3 クライアント サービスの説明</span><span class="sxs-lookup"><span data-stu-id="90024-103">Chapter 3 - Description of Azure RTOS NetX POP3 Client services</span></span>

<span data-ttu-id="90024-104">この章では、Azure RTOS NetX POP3 エージェントのすべてのサービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="90024-104">This chapter contains a description of all Azure RTOS NetX POP3 Client services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="90024-105">以下の API の説明の「戻り値」セクションでは、**太字** の値は API のエラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="90024-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="90024-106">nx_pop3_client_create: *Pop3 クライアント インスタンスを作成する*</span><span class="sxs-lookup"><span data-stu-id="90024-106">nx_pop3_client_create: *Create a POP3 Client Instance*</span></span>
- <span data-ttu-id="90024-107">nx_pop3_client_delete: *Pop3 クライアント インスタンスを削除する*</span><span class="sxs-lookup"><span data-stu-id="90024-107">nx_pop3_client_delete: *Delete a POP3 Client instance*</span></span>
- <span data-ttu-id="90024-108">nx_pop3_client_ mail_item_get: *サーバー maildrop からクライアント メール アイテムを削除する*</span><span class="sxs-lookup"><span data-stu-id="90024-108">nx_pop3_client_ mail_item_get: *Delete a Client mail item from Server maildrop*</span></span>
- <span data-ttu-id="90024-109">nx_pop3_client_mail_item_get: *特定サイズのメール メッセージを取得する*</span><span class="sxs-lookup"><span data-stu-id="90024-109">nx_pop3_client_mail_item_get: *Retrieve a specific mail message size*</span></span>
- <span data-ttu-id="90024-110">nx_pop3_client_mail_items_get: *maildrop でメール アイテムの数を取得する*</span><span class="sxs-lookup"><span data-stu-id="90024-110">nx_pop3_client_mail_items_get: *Obtain the number of mail items in maildrop*</span></span>
- <span data-ttu-id="90024-111">nx_pop3_client_mail_item_message _get: *特定のメール メッセージをダウンロードする*</span><span class="sxs-lookup"><span data-stu-id="90024-111">nx_pop3_client_mail_item_message _get: *Download a specific mail message*</span></span>
- <span data-ttu-id="90024-112">nx_pop3_client_mail_item_size_get: *特定のメール アイテムのサイズを取得する*</span><span class="sxs-lookup"><span data-stu-id="90024-112">nx_pop3_client_mail_item_size_get: *Obtain the size of a specific mail item*</span></span>

## <a name="nx_pop3_client_create"></a><span data-ttu-id="90024-113">nx_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="90024-113">nx_pop3_client_create</span></span>

<span data-ttu-id="90024-114">POP3 クライアント インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="90024-114">Create a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="90024-115">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="90024-115">Prototype</span></span>

```c
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                        UINT APOP_authentication, NX_IP *ip_ptr,
                        NX_PACKET_POOL *packet_pool_ptr,
                        ULONG server_ip_address,
                        ULONG server_port,
                        CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="90024-116">説明</span><span class="sxs-lookup"><span data-stu-id="90024-116">Description</span></span>

<span data-ttu-id="90024-117">このサービスでは、POP3 クライアントのインスタンスを作成し、入力パラメーターを使用してその構成を設定します。</span><span class="sxs-lookup"><span data-stu-id="90024-117">This service creates an instance of the POP3 Client and sets up its configuration with the input parameters.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90024-118">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="90024-118">Input Parameters</span></span>

- <span data-ttu-id="90024-119">**client_ptr**: 作成するクライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="90024-119">**client_ptr**: Pointer to Client to create</span></span>
- <span data-ttu-id="90024-120">**APOP_authentication**: APOP 認証を有効にする</span><span class="sxs-lookup"><span data-stu-id="90024-120">**APOP_authentication**: Enable APOP authentication</span></span>
- <span data-ttu-id="90024-121">**ip_ptr** IP インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="90024-121">**ip_ptr**: Pointer to IP instance</span></span>
- <span data-ttu-id="90024-122">**packet_pool_ptr** クライアントのパケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="90024-122">**packet_pool_ptr**: Pointer to Client packet pool</span></span>
- <span data-ttu-id="90024-123">**server_ip_address**: POP3 サーバーのアドレス</span><span class="sxs-lookup"><span data-stu-id="90024-123">**server_ip_address**: POP3 server address</span></span>
- <span data-ttu-id="90024-124">**server_port**: POP3 サーバー ポート</span><span class="sxs-lookup"><span data-stu-id="90024-124">**server_port**: POP3 server port</span></span>
- <span data-ttu-id="90024-125">**client_name**: クライアント名へのポインター</span><span class="sxs-lookup"><span data-stu-id="90024-125">**client_name**: Pointer to Client name</span></span>
- <span data-ttu-id="90024-126">**client_password**: クライアント パスワードへのポインター</span><span class="sxs-lookup"><span data-stu-id="90024-126">**client_password**: Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="90024-127">戻り値</span><span class="sxs-lookup"><span data-stu-id="90024-127">Return Values</span></span>

- <span data-ttu-id="90024-128">**NX_SUCCESS**: (0x00) クライアントが正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="90024-128">**NX_SUCCESS**: (0x00) Client successfully created</span></span>
- <span data-ttu-id="90024-129">**status**: NetX および ThreadX サービス呼び出しの完了状態</span><span class="sxs-lookup"><span data-stu-id="90024-129">**status**: Status completion of NetX and ThreadX service calls</span></span>
- <span data-ttu-id="90024-130">NX_PTR_ERROR (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="90024-130">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="90024-131">NX_POP3_PARAM_ERROR: (0xB1) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="90024-131">NX_POP3_PARAM_ERROR: (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90024-132">許可元</span><span class="sxs-lookup"><span data-stu-id="90024-132">Allowed From</span></span>

<span data-ttu-id="90024-133">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="90024-133">Application code</span></span>

### <a name="example"></a><span data-ttu-id="90024-134">例</span><span class="sxs-lookup"><span data-stu-id="90024-134">Example</span></span>

```c
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST                   "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD          "pass"
#define POP3_SERVER_ADDRESS         IP_ADDRESS(192,2,2,92
#define POP3_SERVER_PORT            110

/* Create a NetX POP3 Client instance. */
ULONG server_ip_address = IP_ADDRESS(1,2,3,4);
status = nx_pop3_client_create(&demo_client,
        NX_FALSE /* disable APOP authentication */,
        &client_ip, &client_packet_pool,
        server_ip_address, POP3_SERVER_PORT,
        LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a><span data-ttu-id="90024-135">nx_pop3_client_delete</span><span class="sxs-lookup"><span data-stu-id="90024-135">nx_pop3_client_delete</span></span>

<span data-ttu-id="90024-136">POP3 クライアント インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="90024-136">Delete a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="90024-137">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="90024-137">Prototype</span></span>

```c
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr)
```

### <a name="description"></a><span data-ttu-id="90024-138">説明</span><span class="sxs-lookup"><span data-stu-id="90024-138">Description</span></span>

<span data-ttu-id="90024-139">このサービスでは、以前に作成された POP3 クライアントを削除します。</span><span class="sxs-lookup"><span data-stu-id="90024-139">This service deletes a previously created POP3 Client.</span></span> <span data-ttu-id="90024-140">このサービスでは、POP3 クライアントのパケット プールは削除されません。</span><span class="sxs-lookup"><span data-stu-id="90024-140">Not that this service does not delete the POP3 Client packet pool.</span></span> <span data-ttu-id="90024-141">パケット プールを使用しなくなった場合は、デバイス アプリケーションでこのリソースを個別に削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90024-141">The device application must delete this resource separately if it no longer has use for the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90024-142">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="90024-142">Input Parameters</span></span>

- <span data-ttu-id="90024-143">**client_ptr**: 削除するクライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="90024-143">**client_ptr**: Pointer to Client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="90024-144">戻り値</span><span class="sxs-lookup"><span data-stu-id="90024-144">Return Values</span></span>

- <span data-ttu-id="90024-145">**NX_SUCCESS** (0x00) クライアントが正常に削除されました</span><span class="sxs-lookup"><span data-stu-id="90024-145">**NX_SUCCESS**: (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="90024-146">NX_PTR_ERROR (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="90024-146">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90024-147">許可元</span><span class="sxs-lookup"><span data-stu-id="90024-147">Allowed From</span></span>

<span data-ttu-id="90024-148">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="90024-148">Application code</span></span>

### <a name="example"></a><span data-ttu-id="90024-149">例</span><span class="sxs-lookup"><span data-stu-id="90024-149">Example</span></span>

```c
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a><span data-ttu-id="90024-150">nx_pop3_client_mail_item_delete</span><span class="sxs-lookup"><span data-stu-id="90024-150">nx_pop3_client_mail_item_delete</span></span>

<span data-ttu-id="90024-151">指定されたメール アイテムをクライアントの maildrop から削除する</span><span class="sxs-lookup"><span data-stu-id="90024-151">Delete a specified mail item from the Client maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="90024-152">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="90024-152">Prototype</span></span>

```c
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
                                    UINT mail_index)
```

### <a name="description"></a><span data-ttu-id="90024-153">説明</span><span class="sxs-lookup"><span data-stu-id="90024-153">Description</span></span>

<span data-ttu-id="90024-154">このサービスでは、指定されたメール アイテムをクライアントの maildrop から削除します。</span><span class="sxs-lookup"><span data-stu-id="90024-154">This service deletes the specified mail item from the Client maildrop.</span></span> <span data-ttu-id="90024-155">これはメール アイテムのダウンロード後を対象としていますが、クライアントから要求された後にメール アイテムを自動的に削除する POP3 サーバーもあります。</span><span class="sxs-lookup"><span data-stu-id="90024-155">It is intended for after downloading the mail item, although some POP3 servers may automatically delete mail items after being requested by the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90024-156">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="90024-156">Input Parameters</span></span>

- <span data-ttu-id="90024-157">**client_ptr**: クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="90024-157">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="90024-158">**mail_index**: クライアントの maildrop へのインデックス</span><span class="sxs-lookup"><span data-stu-id="90024-158">**mail_index**: Index into Client maildrop</span></span>

### <a name="return-values"></a><span data-ttu-id="90024-159">戻り値</span><span class="sxs-lookup"><span data-stu-id="90024-159">Return Values</span></span>

- <span data-ttu-id="90024-160">**NX_SUCCESS**: (0x00) 削除要求が成功しました</span><span class="sxs-lookup"><span data-stu-id="90024-160">**NX_SUCCESS**: (0x00) Delete request successful</span></span>
- <span data-ttu-id="90024-161">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) メール アイテムのインデックスが無効です</span><span class="sxs-lookup"><span data-stu-id="90024-161">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="90024-162">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます</span><span class="sxs-lookup"><span data-stu-id="90024-162">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="90024-163">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) サーバーがエラー状態で応答しました</span><span class="sxs-lookup"><span data-stu-id="90024-163">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="90024-164">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) メール インデックス入力が無効です</span><span class="sxs-lookup"><span data-stu-id="90024-164">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="90024-165">NX_PTR_ERROR (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="90024-165">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90024-166">許可元</span><span class="sxs-lookup"><span data-stu-id="90024-166">Allowed From</span></span>

<span data-ttu-id="90024-167">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="90024-167">Application code</span></span>

### <a name="example"></a><span data-ttu-id="90024-168">例</span><span class="sxs-lookup"><span data-stu-id="90024-168">Example</span></span>

```c
ULONG     item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status = 
   NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a><span data-ttu-id="90024-169">nx_pop3_client_mail_item_get</span><span class="sxs-lookup"><span data-stu-id="90024-169">nx_pop3_client_mail_item_get</span></span>

<span data-ttu-id="90024-170">指定されたメール アイテムを取得する</span><span class="sxs-lookup"><span data-stu-id="90024-170">Retrieve a specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="90024-171">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="90024-171">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item, ULONG *item_size)
```

### <a name="description"></a><span data-ttu-id="90024-172">説明</span><span class="sxs-lookup"><span data-stu-id="90024-172">Description</span></span>

<span data-ttu-id="90024-173">このサービスでは RETR 要求を行って、クライアントの maildrop から、インデックス mail_item で指定されたメール アイテムを取得します。</span><span class="sxs-lookup"><span data-stu-id="90024-173">This service makes a RETR request to retrieve a mail item from the Client maildrop specified by the index mail_item.</span></span> <span data-ttu-id="90024-174">RETR 要求を行い、サーバーから肯定応答を受信したら、クライアントは *nx_pop3_client_mail_item_message_get* サービスを使用して、メール メッセージのダウンロードを開始できます。</span><span class="sxs-lookup"><span data-stu-id="90024-174">After making a RETR request, and receiving a positive response from the Server, the Client can start downloading the mail message using the *nx_pop3_client_mail_item_message_get* service.</span></span> <span data-ttu-id="90024-175">このサービスでは、サーバーの応答から抽出された、要求されたメール アイテムのサイズも提供します。</span><span class="sxs-lookup"><span data-stu-id="90024-175">Note that the service also supplies the size of the requested mail item extracted from the Server reply.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90024-176">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="90024-176">Input Parameters</span></span>

- <span data-ttu-id="90024-177">**client_ptr**: クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="90024-177">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="90024-178">**mail_item**: クライアントの maildrop へのインデックス</span><span class="sxs-lookup"><span data-stu-id="90024-178">**mail_item**: Index into Client maildrop</span></span>
- <span data-ttu-id="90024-179">**item_size**: メール メッセージのサイズへのポインター</span><span class="sxs-lookup"><span data-stu-id="90024-179">**item_size**: Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="90024-180">戻り値</span><span class="sxs-lookup"><span data-stu-id="90024-180">Return Values</span></span>

- <span data-ttu-id="90024-181">**NX_SUCCESS**: (0x00) メール アイテムが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="90024-181">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="90024-182">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) メール アイテムのインデックスが無効です</span><span class="sxs-lookup"><span data-stu-id="90024-182">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="90024-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます</span><span class="sxs-lookup"><span data-stu-id="90024-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="90024-184">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) サーバーがエラー状態で応答しました</span><span class="sxs-lookup"><span data-stu-id="90024-184">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="90024-185">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) メール インデックス入力が無効です</span><span class="sxs-lookup"><span data-stu-id="90024-185">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="90024-186">NX_PTR_ERROR (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="90024-186">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90024-187">許可元</span><span class="sxs-lookup"><span data-stu-id="90024-187">Allowed From</span></span>

<span data-ttu-id="90024-188">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="90024-188">Application code</span></span>

### <a name="example"></a><span data-ttu-id="90024-189">例</span><span class="sxs-lookup"><span data-stu-id="90024-189">Example</span></span>

```c
ULONG     item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a><span data-ttu-id="90024-190">nx_pop3_client_mail_items_get</span><span class="sxs-lookup"><span data-stu-id="90024-190">nx_pop3_client_mail_items_get</span></span>

<span data-ttu-id="90024-191">maildrop 内のメール アイテムの数を取得する</span><span class="sxs-lookup"><span data-stu-id="90024-191">Retrieve the number of mail items in maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="90024-192">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="90024-192">Prototype</span></span>

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

### <a name="description"></a><span data-ttu-id="90024-193">説明</span><span class="sxs-lookup"><span data-stu-id="90024-193">Description</span></span>

<span data-ttu-id="90024-194">このサービスでは STAT 要求を行って、クライアントの maildrop からメール アイテムの数とメール メッセージ データの合計サイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="90024-194">This service makes a STAT request to retrieve the number of mail items and total size of mail message data from the Client maildrop.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90024-195">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="90024-195">Input Parameters</span></span>

- <span data-ttu-id="90024-196">**client_ptr**: クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="90024-196">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="90024-197">**number_mail_item**: クライアントの maildrop 内のメール数</span><span class="sxs-lookup"><span data-stu-id="90024-197">**number_mail_item**: Number of mail in Client maildrop</span></span>
- <span data-ttu-id="90024-198">**maildrop_total_size**: すべてのメール メッセージのサイズへのポインター</span><span class="sxs-lookup"><span data-stu-id="90024-198">**maildrop_total_size**: Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="90024-199">戻り値</span><span class="sxs-lookup"><span data-stu-id="90024-199">Return Values</span></span>

- <span data-ttu-id="90024-200">**NX_SUCCESS**: (0x00) メール アイテムが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="90024-200">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="90024-201">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) メール アイテムのインデックスが無効です</span><span class="sxs-lookup"><span data-stu-id="90024-201">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="90024-202">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます</span><span class="sxs-lookup"><span data-stu-id="90024-202">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="90024-203">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) サーバーがエラー状態で応答しました</span><span class="sxs-lookup"><span data-stu-id="90024-203">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span> 
- <span data-ttu-id="90024-204">NX_PTR_ERROR (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="90024-204">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90024-205">許可元</span><span class="sxs-lookup"><span data-stu-id="90024-205">Allowed From</span></span>

<span data-ttu-id="90024-206">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="90024-206">Application code</span></span>

### <a name="example"></a><span data-ttu-id="90024-207">例</span><span class="sxs-lookup"><span data-stu-id="90024-207">Example</span></span>

```c
UINT      number_mail_items;
ULONG     maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
                                        &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a><span data-ttu-id="90024-208">nx_pop3_client_mail_item_message_get</span><span class="sxs-lookup"><span data-stu-id="90024-208">nx_pop3_client_mail_item_message_get</span></span>

<span data-ttu-id="90024-209">指定されたメール アイテム メッセージを取得する</span><span class="sxs-lookup"><span data-stu-id="90024-209">Retrieve the specified mail item message</span></span>

### <a name="prototype"></a><span data-ttu-id="90024-210">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="90024-210">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_message_get(
                NX_POP3_CLIENT *client_ptr,
                NX_PACKET **recv_packet_ptr,
                ULONG *bytes_retrieved,
                UINT *final_packet)
```

### <a name="description"></a><span data-ttu-id="90024-211">説明</span><span class="sxs-lookup"><span data-stu-id="90024-211">Description</span></span>

<span data-ttu-id="90024-212">このサービスでは、メール アイテム メッセージ、メール メッセージのサイズ、メール メッセージの最後のパケットかどうかを取得します。</span><span class="sxs-lookup"><span data-stu-id="90024-212">This service retrieves the mail item message, size of the mail message, and if it is the last packet in the mail message.</span></span> <span data-ttu-id="90024-213">`final_packet` が NX_TRUE の場合、`recv_packet_ptr` によってポイントされるパケットは、メール アイテム メッセージの最後のパケットです。</span><span class="sxs-lookup"><span data-stu-id="90024-213">If `final_packet` is NX_TRUE the packet pointed to by `recv_packet_ptr` is the final packet in the mail item message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90024-214">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="90024-214">Input Parameters</span></span>

- <span data-ttu-id="90024-215">**client_ptr**: クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="90024-215">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="90024-216">**recv_packet_ptr**: メッセージ データの受信パケット</span><span class="sxs-lookup"><span data-stu-id="90024-216">**recv_packet_ptr**: Received packet of message data</span></span>
- <span data-ttu-id="90024-217">**number_mail_item**: クライアントの maildrop 内のメール数</span><span class="sxs-lookup"><span data-stu-id="90024-217">**number_mail_item**: Number of mail in Client maildrop</span></span>
- <span data-ttu-id="90024-218">**maildrop_total_size**: すべてのメール メッセージのサイズへのポインター</span><span class="sxs-lookup"><span data-stu-id="90024-218">**maildrop_total_size**: Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="90024-219">戻り値</span><span class="sxs-lookup"><span data-stu-id="90024-219">Return Values</span></span>

- <span data-ttu-id="90024-220">**NX_SUCCESS**: (0x00) メール アイテムが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="90024-220">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="90024-221">**NX_POP3_CLIENT_INVALID_STATE**: (0xB7) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="90024-221">**NX_POP3_CLIENT_INVALID_STATE**: (0xB7) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="90024-222">NX_PTR_ERROR (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="90024-222">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90024-223">許可元</span><span class="sxs-lookup"><span data-stu-id="90024-223">Allowed From</span></span>

<span data-ttu-id="90024-224">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="90024-224">Application code</span></span>

### <a name="example"></a><span data-ttu-id="90024-225">例</span><span class="sxs-lookup"><span data-stu-id="90024-225">Example</span></span>

```c
NX_PACKET     *recv_packet_ptr;
ULONG         bytes_retrieved;
UINT          final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
                                                bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a><span data-ttu-id="90024-226">nx_pop3_client_mail_item_size_get</span><span class="sxs-lookup"><span data-stu-id="90024-226">nx_pop3_client_mail_item_size_get</span></span>

<span data-ttu-id="90024-227">指定されたメール アイテムのサイズを取得する</span><span class="sxs-lookup"><span data-stu-id="90024-227">Retrieve the size of the specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="90024-228">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="90024-228">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_size_get(
                NX_POP3_CLIENT *client_ptr,
                UINT mail_item, ULONG *size)
```

### <a name="description"></a><span data-ttu-id="90024-229">説明</span><span class="sxs-lookup"><span data-stu-id="90024-229">Description</span></span>

<span data-ttu-id="90024-230">このサービスでは LIST 要求を行って、指定されたメール アイテムのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="90024-230">This service makes a LIST request to obtain the size of the specified mail item.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90024-231">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="90024-231">Input Parameters</span></span>

- <span data-ttu-id="90024-232">**client_ptr**: クライアント インスタンスへのポインター</span><span class="sxs-lookup"><span data-stu-id="90024-232">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="90024-233">**mail_item**: クライアントの maildrop へのインデックス</span><span class="sxs-lookup"><span data-stu-id="90024-233">**mail_item**: Index into Client maildrop</span></span>
- <span data-ttu-id="90024-234">**size**: メール メッセージのサイズへのポインター</span><span class="sxs-lookup"><span data-stu-id="90024-234">**size**: Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="90024-235">戻り値</span><span class="sxs-lookup"><span data-stu-id="90024-235">Return Values</span></span>

- <span data-ttu-id="90024-236">**NX_SUCCESS**: (0x00) メール アイテムが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="90024-236">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="90024-237">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) メール アイテムのインデックスが無効です</span><span class="sxs-lookup"><span data-stu-id="90024-237">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="90024-238">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) クライアントのパケット ペイロードが POP3 要求に対して小さすぎます</span><span class="sxs-lookup"><span data-stu-id="90024-238">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="90024-239">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) サーバーがエラー状態で応答しました</span><span class="sxs-lookup"><span data-stu-id="90024-239">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="90024-240">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) メール インデックス入力が無効です</span><span class="sxs-lookup"><span data-stu-id="90024-240">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="90024-241">NX_PTR_ERROR (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="90024-241">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90024-242">許可元</span><span class="sxs-lookup"><span data-stu-id="90024-242">Allowed From</span></span>

<span data-ttu-id="90024-243">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="90024-243">Application code</span></span>

### <a name="example"></a><span data-ttu-id="90024-244">例</span><span class="sxs-lookup"><span data-stu-id="90024-244">Example</span></span>

```c
ULONG     size;
UINT      mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
