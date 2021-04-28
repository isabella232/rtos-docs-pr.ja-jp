---
title: 3 章 - SMTP クライアント サービスのクライアントの説明
description: この章では、一般的な SMTP クライアント アプリケーションでの使用順に、すべての NetX Duo SMTP クライアント サービス (以下の一覧を参照) について説明します。
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f590ba5a4c020b4a0aec6628a89c0e5f0f8579d9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810604"
---
# <a name="chapter-3---client-description-of-smtp-client-services"></a><span data-ttu-id="af7be-103">3 章 - SMTP クライアント サービスのクライアントの説明</span><span class="sxs-lookup"><span data-stu-id="af7be-103">Chapter 3 - Client description of SMTP Client services</span></span>

<span data-ttu-id="af7be-104">この章では、一般的な SMTP クライアント アプリケーションでの使用順に、すべての NetX Duo SMTP クライアント サービス (以下の一覧を参照) について説明します。</span><span class="sxs-lookup"><span data-stu-id="af7be-104">This chapter contains a description of all NetX Duo SMTP Client services (listed below) in order of usage in a typical SMTP Client application.</span></span>

> [!NOTE]
> <span data-ttu-id="af7be-105">以下の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にするために使用される **_NX_DISABLE_ERROR_CHECKING_** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="af7be-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **_NX_DISABLE_ERROR_CHECKING_** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nxd_smtp_client_create"></a><span data-ttu-id="af7be-106">nxd_smtp_client_create</span><span class="sxs-lookup"><span data-stu-id="af7be-106">nxd_smtp_client_create</span></span>

<span data-ttu-id="af7be-107">SMTP クライアント インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="af7be-107">Create an SMTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="af7be-108">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="af7be-108">Prototype</span></span>

```C
UINT nxd_smtp_client_create(NX_SMTP_CLIENT *client_ptr,
    NX_IP *ip_ptr, NX_PACKET_POOL
    *client_packet_pool_ptr,
    CHAR *username, CHAR *password,
    CHAR *from_address,
    CHAR *client_domain,
    UINT authentication_type, NXD_ADDRESS *server_address,
    UINT port);
```

### <a name="description"></a><span data-ttu-id="af7be-109">説明</span><span class="sxs-lookup"><span data-stu-id="af7be-109">Description</span></span>

<span data-ttu-id="af7be-110">このサービスでは、指定された IP インスタンスに SMTP クライアント インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="af7be-110">This service creates an SMTP Client instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af7be-111">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="af7be-111">Input Parameters</span></span>

- <span data-ttu-id="af7be-112">**client_ptr** SMTP クライアントの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="af7be-112">**client_ptr** Pointer to SMTP Client control block;</span></span>
- <span data-ttu-id="af7be-113">**ip_ptr** IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="af7be-113">**ip_ptr** Pointer to IP instance;</span></span>
- <span data-ttu-id="af7be-114">**packet_pool_ptr** クライアントのパケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="af7be-114">**packet_pool_ptr** Pointer to Client packet pool;</span></span>
- <span data-ttu-id="af7be-115">**username** NULL で終了する\*\* 認証用のユーザー名</span><span class="sxs-lookup"><span data-stu-id="af7be-115">**username** NULL-terminated\*\* Username for authentication</span></span>
- <span data-ttu-id="af7be-116">**password** NULL で終了する認証用のパスワード</span><span class="sxs-lookup"><span data-stu-id="af7be-116">**password** NULL-terminated password for authentication</span></span>
- <span data-ttu-id="af7be-117">**from_address** NULL で終了する送信者のアドレス</span><span class="sxs-lookup"><span data-stu-id="af7be-117">**from_address** NULL-terminated sender’s address</span></span>
- <span data-ttu-id="af7be-118">**client_domain** NULL で終了するドメイン名</span><span class="sxs-lookup"><span data-stu-id="af7be-118">**client_domain** NULL-terminated domain name</span></span>
- <span data-ttu-id="af7be-119">**authentication_type** クライアント認証の種類。</span><span class="sxs-lookup"><span data-stu-id="af7be-119">**authentication_type** Client authentication type.</span></span> <span data-ttu-id="af7be-120">サポートされる種類は、</span><span class="sxs-lookup"><span data-stu-id="af7be-120">Supported types are:</span></span>
  - <span data-ttu-id="af7be-121">NX_SMTP_CLIENT_AUTH_LOGIN</span><span class="sxs-lookup"><span data-stu-id="af7be-121">NX_SMTP_CLIENT_AUTH_LOGIN</span></span>
  - <span data-ttu-id="af7be-122">NX_SMTP_CLIENT_AUTH_PLAIN</span><span class="sxs-lookup"><span data-stu-id="af7be-122">NX_SMTP_CLIENT_AUTH_PLAIN</span></span>
  - <span data-ttu-id="af7be-123">NX_SMTP_CLIENT_AUTH_NONE</span><span class="sxs-lookup"><span data-stu-id="af7be-123">NX_SMTP_CLIENT_AUTH_NONE</span></span>
- <span data-ttu-id="af7be-124">**server_address** SMTP サーバーの IP アドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="af7be-124">**server_address** Pointer to SMTP Server IP address</span></span>
- <span data-ttu-id="af7be-125">**server_port** SMTP サーバーの TCP ポート</span><span class="sxs-lookup"><span data-stu-id="af7be-125">**server_port** SMTP Server TCP port</span></span>

### <a name="return-values"></a><span data-ttu-id="af7be-126">戻り値</span><span class="sxs-lookup"><span data-stu-id="af7be-126">Return Values</span></span>

- <span data-ttu-id="af7be-127">**NX_SUCCESS** (0x00) SMTP クライアントが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="af7be-127">**NX_SUCCESS** (0x00) SMTP Client successfully created.</span></span> <span data-ttu-id="af7be-128">TCP ソケット作成状態</span><span class="sxs-lookup"><span data-stu-id="af7be-128">TCP socket creation status</span></span>
- <span data-ttu-id="af7be-129">NX_SMTP_INVALID_PARAM (0xA5) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="af7be-129">NX_SMTP_INVALID_PARAM (0xA5) Invalid non pointer input</span></span>
- <span data-ttu-id="af7be-130">NX_IP_ADDRESS_ERROR (0x21) IP アドレスの種類が無効です</span><span class="sxs-lookup"><span data-stu-id="af7be-130">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address type</span></span>
- <span data-ttu-id="af7be-131">NX_PTR_ERROR (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="af7be-131">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af7be-132">許可元</span><span class="sxs-lookup"><span data-stu-id="af7be-132">Allowed From</span></span>

<span data-ttu-id="af7be-133">アプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="af7be-133">Application Code</span></span>

### <a name="example"></a><span data-ttu-id="af7be-134">例</span><span class="sxs-lookup"><span data-stu-id="af7be-134">Example</span></span>

```C
/* Create the SMTP Client instance. */
NX_PACKET_POOL client_packet_pool;
NX_IP client_ip;
NX_SMTP_CLIENT demo_client;

#define USERNAME “myusername”
#define PASSWORD “mypassword”
#define FROM_ADDRESS “<myname@mycompany.com>”
#define LOCAL_DOMAIN “mycompany.com”
#define SERVER_PORT 25

/* Define client authentication type as LOGIN. 
    If not specified or unknown the SMTP Client will set it to PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE NX_SMTP_CLIENT_AUTH_LOGIN

NXD_ADDRESS server_ip_address;

#ifdef USE_IPV6
    /* Set up the Server IPv6 address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x106;
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;
#endif

status = nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
    USERNAME, PASSWORD, FROM_ADDRESS,
    LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
    &server_ip_address, SERVER_PORT);

/* If an SMTP Client instance was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_smtp_client_delete"></a><span data-ttu-id="af7be-135">nx_smtp_client_delete</span><span class="sxs-lookup"><span data-stu-id="af7be-135">nx_smtp_client_delete</span></span>

<span data-ttu-id="af7be-136">SMTP クライアント インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="af7be-136">Delete an SMTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="af7be-137">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="af7be-137">Prototype</span></span>

```C
UINT nx_smtp_client_delete(NX_SMTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="af7be-138">説明</span><span class="sxs-lookup"><span data-stu-id="af7be-138">Description</span></span>

<span data-ttu-id="af7be-139">このサービスでは、以前に作成された SMTP クライアント インスタンスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="af7be-139">This service deletes a previously created SMTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af7be-140">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="af7be-140">Input Parameters</span></span>

- <span data-ttu-id="af7be-141">**client_ptr** SMTP クライアント インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="af7be-141">**client_ptr** Pointer to SMTP Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="af7be-142">戻り値</span><span class="sxs-lookup"><span data-stu-id="af7be-142">Return Values</span></span>

- <span data-ttu-id="af7be-143">**NX_SUCCESS** (0x00) クライアントが正常に削除されました</span><span class="sxs-lookup"><span data-stu-id="af7be-143">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="af7be-144">NX_PTR_ERROR (0x07) 入力ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="af7be-144">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af7be-145">許可元</span><span class="sxs-lookup"><span data-stu-id="af7be-145">Allowed From</span></span>

<span data-ttu-id="af7be-146">Threads</span><span class="sxs-lookup"><span data-stu-id="af7be-146">Threads</span></span>

### <a name="example"></a><span data-ttu-id="af7be-147">例</span><span class="sxs-lookup"><span data-stu-id="af7be-147">Example</span></span>

```C
/* Delete the SMTP Client instance “my_client.” */

NX_SMTP_CLIENT demo_client;

status = nx_smtp_client_delete(&demo_client);

/* If an SMTP Client instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_smtp_mail_send"></a><span data-ttu-id="af7be-148">nx_smtp_mail_send</span><span class="sxs-lookup"><span data-stu-id="af7be-148">nx_smtp_mail_send</span></span>

<span data-ttu-id="af7be-149">SMTP メール アイテムを作成して送信する</span><span class="sxs-lookup"><span data-stu-id="af7be-149">Create and send an SMTP mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="af7be-150">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="af7be-150">Prototype</span></span>

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address,
    UINT priority, CHAR *subject,
    CHAR *mail_body,
    UINT mail_body_length);
```

### <a name="description"></a><span data-ttu-id="af7be-151">説明</span><span class="sxs-lookup"><span data-stu-id="af7be-151">Description</span></span>

<span data-ttu-id="af7be-152">このサービスでは、SMTP メール アイテムを作成して送信します。</span><span class="sxs-lookup"><span data-stu-id="af7be-152">This service creates and sends an SMTP mail item.</span></span> <span data-ttu-id="af7be-153">SMTP クライアントでは、SMTP サーバーとの TCP 接続を確立し、一連の SMTP コマンドを送信します。</span><span class="sxs-lookup"><span data-stu-id="af7be-153">The SMTP Client establishes a TCP connection with the SMTP Server and sends a series of SMTP commands.</span></span> <span data-ttu-id="af7be-154">エラーが発生しなかった場合は、メール メッセージをサーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="af7be-154">If no errors are encountered, it will transmit the mail message to the Server.</span></span> <span data-ttu-id="af7be-155">メールが正常に送信されたかどうかに関係なく、TCP 接続を終了し、メール送信の結果を示す状態を返します。</span><span class="sxs-lookup"><span data-stu-id="af7be-155">Regardless if the mail is sent successfully it will terminate the TCP connection and return a status indicating outcome of the mail transmission.</span></span> <span data-ttu-id="af7be-156">アプリケーションでは、制限なく送信するために、メール メッセージの数に応じてこのサービスを何度でも呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="af7be-156">The application may call this service for as many mail messages as it needs to send without limit.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af7be-157">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="af7be-157">Input Parameters</span></span>

- <span data-ttu-id="af7be-158">**client_ptr** SMTP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="af7be-158">**client_ptr** Pointer to SMTP Client</span></span>
- <span data-ttu-id="af7be-159">**recipient_address** NULL で終了する受信者アドレス。</span><span class="sxs-lookup"><span data-stu-id="af7be-159">**recipient_address** NULL-terminated recipient address.</span></span>
- <span data-ttu-id="af7be-160">**subject** NULL で終了する件名行のテキスト。</span><span class="sxs-lookup"><span data-stu-id="af7be-160">**subject** NULL-terminated subject line text;.</span></span>
- <span data-ttu-id="af7be-161">**priority** メールが配信される優先度レベル</span><span class="sxs-lookup"><span data-stu-id="af7be-161">**priority** Priority level at which mail is delivered</span></span>
- <span data-ttu-id="af7be-162">**mail_body** メール メッセージへのポインター</span><span class="sxs-lookup"><span data-stu-id="af7be-162">**mail_body** Pointer to mail message</span></span>
- <span data-ttu-id="af7be-163">**mail_body_length** メール メッセージのサイズ</span><span class="sxs-lookup"><span data-stu-id="af7be-163">**mail_body_length** Size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="af7be-164">戻り値</span><span class="sxs-lookup"><span data-stu-id="af7be-164">Return Values</span></span>

- <span data-ttu-id="af7be-165">**NX_SUCCESS** (0x00) メールが正常に送信されました</span><span class="sxs-lookup"><span data-stu-id="af7be-165">**NX_SUCCESS** (0x00) Mail successfully sent</span></span>
- <span data-ttu-id="af7be-166">**NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2) SMTP クライアント インスタンスは、SMTP セッションの状態の結果に対して初期化されていません</span><span class="sxs-lookup"><span data-stu-id="af7be-166">**NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2) SMTP Client instance not initialized for SMTP session status Outcome of SMTP session</span></span>
- <span data-ttu-id="af7be-167">NX_PTR_ERROR (0x07) ポインター パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="af7be-167">NX_PTR_ERROR (0x07) Invalid pointer parameter</span></span>
- <span data-ttu-id="af7be-168">NX_SMTP_INVALID_PARAM (0xA5) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="af7be-168">NX_SMTP_INVALID_PARAM (0xA5) Invalid non pointer input</span></span>
- <span data-ttu-id="af7be-169">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="af7be-169">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af7be-170">許可元</span><span class="sxs-lookup"><span data-stu-id="af7be-170">Allowed From</span></span>

<span data-ttu-id="af7be-171">Threads</span><span class="sxs-lookup"><span data-stu-id="af7be-171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="af7be-172">例</span><span class="sxs-lookup"><span data-stu-id="af7be-172">Example</span></span>

```C
/* Create and send a Client mail item. */

#define RECIPIENT_ADDRESS “<your@yourcompany.com>”
#define SUBJECT “NetX Duo SMTP Client Demo”
#define MAIL_BODY "NetX Duo SMTP client is an SMTP client ” \
    “implementation for embedded devices \r\n” \
    "to send email to SMTP servers.\r\n"

status = nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
    NX_SMTP_MAIL_PRIORITY_NORMAL,
    SUBJECT_LINE, MAIL_BODY,
    sizeof(MAIL_BODY) - 1);

/* Return status being NX_SUCCESS indicates the mail has been
    successfully sent. */
```
