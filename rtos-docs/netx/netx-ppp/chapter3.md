---
title: 第 3 章 - Azure RTOS NetX Point-to-Point プロトコル (PPP) のサービスの説明
description: この章では、すべての Azure RTOS NetX PPP サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f24d7366d27a8223b069a54ef7b93f6b3e38bf3a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811468"
---
# <a name="chapter-3---description-of-azure-rtos-netx-point-to-point-protocol-ppp-services"></a><span data-ttu-id="8c660-103">第 3 章 - Azure RTOS NetX Point-to-Point プロトコル (PPP) のサービスの説明</span><span class="sxs-lookup"><span data-stu-id="8c660-103">Chapter 3 - Description of Azure RTOS NetX Point-to-Point Protocol (PPP) services</span></span>

<span data-ttu-id="8c660-104">この章では、すべての Azure RTOS NetX PPP サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="8c660-104">This chapter contains a description of all Azure RTOS NetX PPP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="8c660-105">以下の API の説明の「戻り値」セクションで、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字でない値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="8c660-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="8c660-106">**nx_ppp_byte_receive**: "*シリアル ISR からバイトを受信する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-106">**nx_ppp_byte_receive**: *Receive a byte from serial ISR*</span></span>
- <span data-ttu-id="8c660-107">**nx_ppp_chap_challenge**: "*CHAP チャレンジを生成する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-107">**nx_ppp_chap_challenge**: *Generate a CHAP challenge*</span></span>
- <span data-ttu-id="8c660-108">**nx_ppp_chap_enable**: "*CHAP 認証を有効にする*"</span><span class="sxs-lookup"><span data-stu-id="8c660-108">**nx_ppp_chap_enable**: *Enable CHAP authentication*</span></span>
- <span data-ttu-id="8c660-109">**nx_ppp_create**: "*PPP インスタンスを作成する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-109">**nx_ppp_create**: *Create a PPP instance*</span></span>
- <span data-ttu-id="8c660-110">**nx_ppp_delete**: "*PPP インスタンスを削除する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-110">**nx_ppp_delete**: *Delete a PPP instance*</span></span>
- <span data-ttu-id="8c660-111">**nx_ppp_dns_address_get**: "*DNS の IP アドレスを取得する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-111">**nx_ppp_dns_address_get**: *Get DNS IP address*</span></span>
- <span data-ttu-id="8c660-112">**nx_ppp_dns_address_set**: "*DNS サーバーの IP アドレスを設定する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-112">**nx_ppp_dns_address_set**:*Set DNS Server IP address*</span></span>
- <span data-ttu-id="8c660-113">**nx_ppp_secondary_dns_address_get**: "*セカンダリ DNS サーバーの IP アドレスを取得する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-113">**nx_ppp_secondary_dns_address_get**: *Get Secondary DNS Server IP address*</span></span>
- <span data-ttu-id="8c660-114">**nx_ppp_secondary_dns_address_set**: "*セカンダリ DNS サーバーの IP アドレスを設定する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-114">**nx_ppp_secondary_dns_address_set**: *Set Secondary_DNS Server IP address*</span></span>
- <span data-ttu-id="8c660-115">**nx_ppp_interface_index_get**: "*IP インターフェイス インデックスを取得する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-115">**nx_ppp_interface_index_get**: *Get IP interface index*</span></span>
- <span data-ttu-id="8c660-116">**nx_ppp_ip_address_assign**: "*IPCP 用の IP アドレスを割り当てる*"</span><span class="sxs-lookup"><span data-stu-id="8c660-116">**nx_ppp_ip_address_assign**: *Assign IP addresses for IPCP*</span></span>
- <span data-ttu-id="8c660-117">**nx_ppp_link_down_notify**: "*リンクダウン時にアプリケーションに通知する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-117">**nx_ppp_link_down_notify**: *Notify application on link down*</span></span>
- <span data-ttu-id="8c660-118">**nx_ppp_link_down_notify**: "*リンクアップ時にアプリケーションに通知する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-118">**nx_ppp_link_up_notify**: *Notify application on link up*</span></span>
- <span data-ttu-id="8c660-119">**nx_ppp_nak_authentication_notify**: "*認証 NAK を受信した場合にアプリケーションに通知する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-119">**nx_ppp_nak_authentication_notify**: *Notify application if authentication NAK is received*</span></span>
- <span data-ttu-id="8c660-120">**nx_ppp_pap_enable**: "*PAP 認証を有効にする*"</span><span class="sxs-lookup"><span data-stu-id="8c660-120">**nx_ppp_pap_enable**: *Enable PAP authentication*</span></span>
- <span data-ttu-id="8c660-121">**nx_ppp_ping_request**: "*LCP エコー要求を送信する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-121">**nx_ppp_ping_request**: *Send an LCP echo request*</span></span>
- <span data-ttu-id="8c660-122">**nx_ppp_raw_string_send**: "*PPP 以外の文字列を送信する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-122">**nx_ppp_raw_string_send**: *Send non PPP string*</span></span>
- <span data-ttu-id="8c660-123">**nx_ppp_restart**: "*PPP の処理を再開する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-123">**nx_ppp_restart**: *Restart PPP processing*</span></span>
- <span data-ttu-id="8c660-124">**nx_ppp_start**: "*PPP の処理を開始する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-124">**nx_ppp_start**: *Start PPP processing*</span></span>
- <span data-ttu-id="8c660-125">**nx_ppp_status_get**: "*PPP の現在の状態を取得する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-125">**nx_ppp_status_get**: *Get current PPP status*</span></span>
- <span data-ttu-id="8c660-126">**nx_ppp_stop**: "*PPP の処理を停止する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-126">**nx_ppp_stop**: *Stop PPP processing*</span></span>
- <span data-ttu-id="8c660-127">**nx_ppp_packet_receive**: "*PPP パケットを受信する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-127">**nx_ppp_packet_receive**: *Receive PPP packet*</span></span>
- <span data-ttu-id="8c660-128">**nx_ppp_packet_send_set**: "*PPP パケット送信関数を設定する*"</span><span class="sxs-lookup"><span data-stu-id="8c660-128">**nx_ppp_packet_send_set**: *Set PPP packet send function*</span></span>

## <a name="nx_ppp_byte_receive"></a><span data-ttu-id="8c660-129">nx_ppp_byte_receive</span><span class="sxs-lookup"><span data-stu-id="8c660-129">nx_ppp_byte_receive</span></span>

<span data-ttu-id="8c660-130">シリアル ISR からバイトを受信します</span><span class="sxs-lookup"><span data-stu-id="8c660-130">Receive a byte from serial ISR</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-131">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-131">Prototype</span></span>

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a><span data-ttu-id="8c660-132">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-132">Description</span></span>

<span data-ttu-id="8c660-133">このサービスは通常、受信したバイトを PPP に転送するために、アプリケーションのシリアル ドライバーの割り込みサービス ルーチン (ISR) から呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-133">This service is typically called from the application’s serial driver Interrupt Service Routine (ISR) to transfer a received byte to PPP.</span></span> <span data-ttu-id="8c660-134">呼び出されると、このルーチンは受信したバイトを循環バイト バッファーに配置し、処理のために適切な PPP スレッドに通知します。</span><span class="sxs-lookup"><span data-stu-id="8c660-134">When called, this routine places the received byte into a circular byte buffer and notifies the appropriate PPP thread for processing.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-135">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-135">Input Parameters</span></span>

- <span data-ttu-id="8c660-136">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-136">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-137">**byte**: シリアル デバイスから受信したバイト。</span><span class="sxs-lookup"><span data-stu-id="8c660-137">**byte**: Byte received from serial device</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-138">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-138">Return Values</span></span>

- <span data-ttu-id="8c660-139">**NX_SUCCESS**: (0x00) PPP バイトを正常に受信しました。</span><span class="sxs-lookup"><span data-stu-id="8c660-139">**NX_SUCCESS**: (0x00) Successful PPP byte receive.</span></span>
- <span data-ttu-id="8c660-140">**NX_PPP_BUFFER_FULL**: (0xB1) PPP シリアル バッファーが既にいっぱいになっています。</span><span class="sxs-lookup"><span data-stu-id="8c660-140">**NX_PPP_BUFFER_FULL**: (0xB1) PPP serial buffer is already full.</span></span>
- <span data-ttu-id="8c660-141">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-141">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-142">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-142">Allowed From</span></span>

<span data-ttu-id="8c660-143">スレッド、ISR</span><span class="sxs-lookup"><span data-stu-id="8c660-143">Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8c660-144">例</span><span class="sxs-lookup"><span data-stu-id="8c660-144">Example</span></span>

```c
/* Notify “my_ppp” of a received byte. */
status =  nx_ppp_byte_receive(&my_ppp, new_byte);

/* If status is NX_SUCCESS the received byte was successfully
   buffered. */
```

## <a name="nx_ppp_chap_challenge"></a><span data-ttu-id="8c660-145">nx_ppp_chap_challenge</span><span class="sxs-lookup"><span data-stu-id="8c660-145">nx_ppp_chap_challenge</span></span>

<span data-ttu-id="8c660-146">CHAP チャレンジを生成します</span><span class="sxs-lookup"><span data-stu-id="8c660-146">Generate a CHAP challenge</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-147">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-147">Prototype</span></span>

```c
UINT nx_ppp_chap_challenge(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="8c660-148">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-148">Description</span></span>

<span data-ttu-id="8c660-149">このサービスを使用すると、PPP 接続が稼働状態になった後に CHAP チャレンジが開始されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-149">This service initiates a CHAP challenge after the PPP connection is already up and running.</span></span> <span data-ttu-id="8c660-150">これにより、アプリケーションは接続の信頼性を定期的に確認できます。</span><span class="sxs-lookup"><span data-stu-id="8c660-150">This gives the application the ability to verify the authenticity of the connection on a periodic basis.</span></span> <span data-ttu-id="8c660-151">チャレンジが失敗すると、PPP リンクは閉じられます。</span><span class="sxs-lookup"><span data-stu-id="8c660-151">If the challenge is unsuccessful, the PPP link is closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-152">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-152">Input Parameters</span></span>

- <span data-ttu-id="8c660-153">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-153">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-154">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-154">Return Values</span></span>

- <span data-ttu-id="8c660-155">**NX_SUCCESS**: (0x00) PPP チャレンジが正常に開始されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-155">**NX_SUCCESS**: (0x00) Successful PPP challenge initiated.</span></span>
- <span data-ttu-id="8c660-156">**NX_PPP_FAILURE**: (0xB0) PPP チャレンジが無効です。CHAP は応答でのみ有効になっています。</span><span class="sxs-lookup"><span data-stu-id="8c660-156">**NX_PPP_FAILURE**: (0xB0) Invalid PPP challenge, CHAP was enabled only for response.</span></span>
- <span data-ttu-id="8c660-157">**NX_NOT_IMPLEMENTED**: (0x80) NX_PPP_DISABLE_CHAP によって CHAP ロジックが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="8c660-157">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="8c660-158">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-158">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="8c660-159">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-159">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-160">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-160">Allowed From</span></span>

<span data-ttu-id="8c660-161">Threads</span><span class="sxs-lookup"><span data-stu-id="8c660-161">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c660-162">例</span><span class="sxs-lookup"><span data-stu-id="8c660-162">Example</span></span>

```c
/* Initiate a PPP challenge for instance “my_ppp”. */
status =  nx_ppp_chap_challenge(&my_ppp);

/* If status is NX_SUCCESS a CHAP challenge “my_ppp” was successfully 
initiated. */
```

## <a name="nx_ppp_chap_enable"></a><span data-ttu-id="8c660-163">nx_ppp_chap_enable</span><span class="sxs-lookup"><span data-stu-id="8c660-163">nx_ppp_chap_enable</span></span>

<span data-ttu-id="8c660-164">CHAP 認証を有効にします</span><span class="sxs-lookup"><span data-stu-id="8c660-164">Enable CHAP authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-165">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-165">Prototype</span></span>

```c
UINT nx_ppp_chap_enable(NX_PPP *ppp_ptr, 
                        UINT (*get_challenge_values)(CHAR *rand_value,CHAR *id,CHAR *name),
                        UINT (*get_responder_values)(CHAR *system,CHAR *name,CHAR *secret),
                        UINT (*get_verification_values)(CHAR *system,CHAR *name,CHAR *secret)); 
```

### <a name="description"></a><span data-ttu-id="8c660-166">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-166">Description</span></span>

<span data-ttu-id="8c660-167">このサービスを使用すると、指定した PPP インスタンスのチャレンジ ハンドシェイク認証プロトコル (CHAP) が有効になります。</span><span class="sxs-lookup"><span data-stu-id="8c660-167">This service enables the Challenge-Handshake Authentication Protocol (CHAP) for the specified PPP instance.</span></span>

<span data-ttu-id="8c660-168">関数ポインター "\***get_challenge_values** _" と "_ \*_get_verification_values_\*\*" が指定されている場合、この PPP インスタンスに CHAP が必要になります。</span><span class="sxs-lookup"><span data-stu-id="8c660-168">If the “\***get_challenge_values**_” and “_\*_get_verification_values_\*\*” function pointers are specified, CHAP is required by this PPP instance.</span></span> <span data-ttu-id="8c660-169">それ以外の場合、CHAP はピアのチャレンジ要求にのみ応答します。</span><span class="sxs-lookup"><span data-stu-id="8c660-169">Otherwise, CHAP only responds to the peer’s challenge requests.</span></span>

<span data-ttu-id="8c660-170">必要なコールバック関数で参照されるデータ項目がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="8c660-170">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="8c660-171">*secret*、*name*、*system* の各データ項目は、最大サイズが NX_PPP_NAME_SIZE-1 の NULL 終端文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c660-171">The data items *secret*, *name*, and *system* are expected to be NULL-terminated strings with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="8c660-172">*rand_value* データ項目は、最大サイズが NX_PPP_VALUE_SIZE-1 の NULL 終端文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c660-172">The data item *rand_value* is expected to be a NULL-terminated string with a maximum size of NX_PPP_VALUE_SIZE-1.</span></span> <span data-ttu-id="8c660-173">*id* データ項目は、単純な符号なし文字型です。</span><span class="sxs-lookup"><span data-stu-id="8c660-173">The data item *id* is a simple unsigned character type.</span></span>

>[!NOTE]
> <span data-ttu-id="8c660-174">この関数は、*nx_ppp_create* の後、nx_ip_create または *nx_ip_interface_attach* の前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c660-174">This function must be called after *nx_ppp_create* but before nx_ip_create or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-175">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-175">Input Parameters</span></span>

- <span data-ttu-id="8c660-176">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-176">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-177">**get_challenge_values**: チャレンジに使用される値を取得するアプリケーション関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-177">**get_challenge_values**: Pointer to application function to retrieve values used for the challenge.</span></span> <span data-ttu-id="8c660-178">*rand_value*、*id*、*secret* の各値は、指定されたコピー先にコピーする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8c660-178">Note that the *rand_value*, *id*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="8c660-179">**get_responder_values**: チャレンジへの応答に使用される値を取得するアプリケーション関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-179">**get_responder_values**: Pointer to application function that retrieves values used to respond to a challenge.</span></span> <span data-ttu-id="8c660-180">*system*、*name*、*secret* の各値は、指定されたコピー先にコピーする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8c660-180">Note that the *system*, *name*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="8c660-181">**get_verification_values**: チャレンジ応答の検証に使用される値を取得するアプリケーション関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-181">**get_verification_values**: Pointer to application function that retrieves values used to verify the challenge response.</span></span> <span data-ttu-id="8c660-182">*system*、*name*、*secret* の各値は、指定されたコピー先にコピーする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8c660-182">Note that the *system*,*name*, and *secret* values must be copied into the supplied destinations.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-183">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-183">Return Values</span></span>

- <span data-ttu-id="8c660-184">**NX_SUCCESS**: (0x00) PPP CHAP が正常に有効になりました。</span><span class="sxs-lookup"><span data-stu-id="8c660-184">**NX_SUCCESS**: (0x00) Successful PPP CHAP enable</span></span>
- <span data-ttu-id="8c660-185">**NX_NOT_IMPLEMENTED**: (0x80) NX_PPP_DISABLE_CHAP によって CHAP ロジックが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="8c660-185">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="8c660-186">NX_PTR_ERROR: (0x07) PPP ポインターまたはコールバック関数ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-186">NX_PTR_ERROR: (0x07) Invalid PPP pointer or callback function pointer.</span></span> <span data-ttu-id="8c660-187">*get_challenge_values* が指定されている場合は、*get_verification_values* 関数も指定する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8c660-187">Note that if *get_challenge_values* is specified, then the *get_verification_values* function must also be supplied.</span></span>
- <span data-ttu-id="8c660-188">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-188">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-189">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-189">Allowed From</span></span>

<span data-ttu-id="8c660-190">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="8c660-190">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8c660-191">例</span><span class="sxs-lookup"><span data-stu-id="8c660-191">Example</span></span>

```c
CHAR    name_string[] = "username";
CHAR    rand_value_string[] = "123456";
CHAR    system_string[] = "system";
CHAR    secret_string[] = "secret";

/* Enable CHAP in both directions (CHAP challenger and CHAP responder) for 
“my_ppp”. */
status =  nx_ppp_chap_enable(&my_ppp,   get_challenge_values, 
                              get_responder_values,
                              get_verification_values);


/* If status is NX_SUCCESS, “my_ppp” has CHAP enabled. */
/* Define the CHAP enable routines.  */
UINT  get_challenge_values(CHAR *rand_value, CHAR *id, CHAR *name)
{
   UINT    i;
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   *id =  '1';  /* One byte  */
   for (i = 0; i< (NX_PPP_VALUE_SIZE-1); i++)
   {
      rand_value[i] =  rand_value_string[i];
   }
   rand_value[i] =  0;
   
   return(NX_SUCCESS);  
}


UINT  get_responder_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;

   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

UINT  get_verification_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

```
## <a name="nx_ppp_create"></a><span data-ttu-id="8c660-192">nx_ppp_create</span><span class="sxs-lookup"><span data-stu-id="8c660-192">nx_ppp_create</span></span>

<span data-ttu-id="8c660-193">PPP インスタンスを作成します</span><span class="sxs-lookup"><span data-stu-id="8c660-193">Create a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-194">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-194">Prototype</span></span>

```c
UINT  nx_ppp_create(NX_PPP *ppp_ptr, CHAR *name, NX_IP *ip_ptr, 
                    VOID *stack_memory_ptr, ULONG stack_size, 
                    UINT thread_priority, NX_PACKET_POOL *pool_ptr,
                    void (*ppp_invalid_packet_handler)(NX_PACKET *packet_ptr),
                    void (*ppp_byte_send)(UCHAR byte));
```

### <a name="description"></a><span data-ttu-id="8c660-195">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-195">Description</span></span>

<span data-ttu-id="8c660-196">このサービスを使用すると、指定した NetX IP インスタンスの PPP インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-196">This service creates a PPP instance for the specified NetX IP instance.</span></span>

>[!NOTE]
> <span data-ttu-id="8c660-197">一般に、PPP スレッドの優先順位よりも高い優先順位で NetX IP スレッドを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8c660-197">It is generally a good idea to create the NetX IP thread at a higher priority than the PPP thread priority.</span></span> <span data-ttu-id="8c660-198">IP スレッドの優先順位の指定の詳細については、*nx_ip_create* サービスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c660-198">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-199">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-199">Input Parameters</span></span>

- <span data-ttu-id="8c660-200">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-200">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-201">**name**: この PPP インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="8c660-201">**name**: Name of this PPP instance.</span></span>
- <span data-ttu-id="8c660-202">**ip_ptr**: まだ作成されていない IP インスタンスの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-202">**ip_ptr**: Pointer to control block for not-yet-created IP instance.</span></span>
- <span data-ttu-id="8c660-203">**stack_memory_ptr**: PPP スレッドのスタック領域の先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-203">**stack_memory_ptr**: Pointer to start of PPP thread’s stack area.</span></span>
- <span data-ttu-id="8c660-204">**stack_size**: スレッドのスタックのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="8c660-204">**stack_size**: Size in bytes in the thread’s stack.</span></span>
- <span data-ttu-id="8c660-205">**pool_ptr**: 既定のパケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-205">**pool_ptr**: Pointer to default packet pool.</span></span>
- <span data-ttu-id="8c660-206">**thread_priority**: 内部 PPP スレッドの優先順位 (1 - 31)。</span><span class="sxs-lookup"><span data-stu-id="8c660-206">**thread_priority**: Priority of internal PPP threads (1-31).</span></span>
- <span data-ttu-id="8c660-207">**ppp_invalid_packet_handler**: PPP 以外のすべてのパケットに対するアプリケーションのハンドラーへの関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-207">**ppp_invalid_packet_handler**: Function pointer to application’s handler for all non-PPP packets.</span></span> <span data-ttu-id="8c660-208">通常、このルーチンは初期化の間に NetX PPP によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-208">The NetX PPP typically calls this routine during initialization.</span></span> <span data-ttu-id="8c660-209">ここで、アプリケーションはモデムのコマンドに応答できます。Windows XP の場合、NetX PPP アプリケーションでは、Windows XP によって送信された最初の "CLIENT" に "CLIENT SERVER" で応答することで PPP を開始できます。</span><span class="sxs-lookup"><span data-stu-id="8c660-209">This is where the application can respond to modem commands or in the case of Windows XP, the NetX PPP application can initiate PPP by responding with“ CLIENT SERVER” to the initial “CLIENT” sent by Windows XP.</span></span>
- <span data-ttu-id="8c660-210">**ppp_byte_send**: アプリケーションのシリアル バイト出力ルーチンへの関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-210">**ppp_byte_send**: Function pointer to application’s serial byte output routine.</span></span>


### <a name="return-values"></a><span data-ttu-id="8c660-211">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-211">Return Values</span></span>

- <span data-ttu-id="8c660-212">**NX_SUCCESS**: (0x00) PPP が正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-212">**NX_SUCCESS**: (0x00) Successful PPP create.</span></span>
- <span data-ttu-id="8c660-213">NX_PTR_ERROR: (0x07) PPP、IP、またはバイト出力関数ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-213">NX_PTR_ERROR: (0x07) Invalid PPP, IP, or byte output function pointer.</span></span>
- <span data-ttu-id="8c660-214">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-214">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-215">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-215">Allowed From</span></span>

<span data-ttu-id="8c660-216">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="8c660-216">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8c660-217">例</span><span class="sxs-lookup"><span data-stu-id="8c660-217">Example</span></span>

```c
/* Create “my_ppp” for IP instance “my_ip”. */
status =  nx_ppp_create(&my_ppp, “my PPP”, &my_ip, stack_start, 1024, 2, 
                        &my_pool, my_invalid_packet_handler, my_out_byte);

/* If status is NX_SUCCESS the PPP instance was successfully
   created. */
```

## <a name="nx_ppp_delete"></a><span data-ttu-id="8c660-218">nx_ppp_delete</span><span class="sxs-lookup"><span data-stu-id="8c660-218">nx_ppp_delete</span></span>

<span data-ttu-id="8c660-219">PPP インスタンスを削除します</span><span class="sxs-lookup"><span data-stu-id="8c660-219">Delete a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-220">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-220">Prototype</span></span>

```c
UINT nx_ppp_delete(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="8c660-221">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-221">Description</span></span>

<span data-ttu-id="8c660-222">このサービスを使用すると、以前に作成された PPP インスタンスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-222">This service deletes the previously created PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-223">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-223">Input Parameters</span></span>

- <span data-ttu-id="8c660-224">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-224">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-225">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-225">Return Values</span></span>

- <span data-ttu-id="8c660-226">**NX_SUCCESS**: (0x00) PPP が正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-226">**NX_SUCCESS**: (0x00) Successful PPP deletion.</span></span>
- <span data-ttu-id="8c660-227">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-227">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="8c660-228">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-228">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-229">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-229">Allowed From</span></span>

<span data-ttu-id="8c660-230">Threads</span><span class="sxs-lookup"><span data-stu-id="8c660-230">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c660-231">例</span><span class="sxs-lookup"><span data-stu-id="8c660-231">Example</span></span>

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a><span data-ttu-id="8c660-232">nx_ppp_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="8c660-232">nx_ppp_dns_address_get</span></span>

<span data-ttu-id="8c660-233">DNS IP アドレスを取得します</span><span class="sxs-lookup"><span data-stu-id="8c660-233">Get DNS IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-234">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-234">Prototype</span></span>

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="8c660-235">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-235">Description</span></span>

<span data-ttu-id="8c660-236">このサービスを使用すると、ピアによって提供された DNS IP アドレスが取得されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-236">This service retrieves the DNS IP address supplied by the peer.</span></span> <span data-ttu-id="8c660-237">ピアから IP アドレスが提供されていない場合は、IP アドレスとして 0 が返されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-237">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-238">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-238">Input Parameters</span></span>

- <span data-ttu-id="8c660-239">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-239">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-240">**dns_address_ptr**: DNS IP アドレスの格納先。</span><span class="sxs-lookup"><span data-stu-id="8c660-240">**dns_address_ptr**: Destination for DNS IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-241">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-241">Return Values</span></span>

- <span data-ttu-id="8c660-242">**NX_SUCCESS**: (0x00) PPP アドレスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="8c660-242">**NX_SUCCESS**: (0x00) Successful PPP address get.</span></span>
- <span data-ttu-id="8c660-243">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP はピアとのネゴシエーションを完了していません。</span><span class="sxs-lookup"><span data-stu-id="8c660-243">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="8c660-244">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-244">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-245">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-245">Allowed From</span></span>

<span data-ttu-id="8c660-246">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="8c660-246">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8c660-247">例</span><span class="sxs-lookup"><span data-stu-id="8c660-247">Example</span></span>

```c

ULONG  my_dns_address;

/* Get IP Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a><span data-ttu-id="8c660-248">nx_ppp_secondary_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="8c660-248">nx_ppp_secondary_dns_address_get</span></span>

<span data-ttu-id="8c660-249">セカンダリ DNS サーバーの IP アドレスを取得します</span><span class="sxs-lookup"><span data-stu-id="8c660-249">Get Secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-250">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-250">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="8c660-251">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-251">Description</span></span>

<span data-ttu-id="8c660-252">このサービスを使用すると、IPCP ハンドシェイクでピアによって提供されたセカンダリ DNS IP アドレスが取得されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-252">This service retrieves the secondary DNS IP address supplied by the peer in the IPCP handshake.</span></span> <span data-ttu-id="8c660-253">ピアから IP アドレスが提供されていない場合は、IP アドレスとして 0 が返されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-253">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-254">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-254">Input Parameters</span></span>

- <span data-ttu-id="8c660-255">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-255">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-256">**dns_address_ptr**: セカンダリ DNS サーバーのアドレスの格納先</span><span class="sxs-lookup"><span data-stu-id="8c660-256">**dns_address_ptr**: Destination for Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-257">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-257">Return Values</span></span>

- <span data-ttu-id="8c660-258">**NX_SUCCESS**: (0x00) DNS アドレスが正常に取得されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-258">**NX_SUCCESS**: (0x00) Successful DNS address get.</span></span>
- <span data-ttu-id="8c660-259">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP はピアとのネゴシエーションを完了していません。</span><span class="sxs-lookup"><span data-stu-id="8c660-259">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="8c660-260">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-260">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-261">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-261">Allowed From</span></span>

<span data-ttu-id="8c660-262">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="8c660-262">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8c660-263">例</span><span class="sxs-lookup"><span data-stu-id="8c660-263">Example</span></span>

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a><span data-ttu-id="8c660-264">nx_ppp_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="8c660-264">nx_ppp_dns_address_set</span></span>

<span data-ttu-id="8c660-265">プライマリ DNS サーバーの IP アドレスを設定します</span><span class="sxs-lookup"><span data-stu-id="8c660-265">Set primary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-266">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-266">Prototype</span></span>

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="8c660-267">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-267">Description</span></span>

<span data-ttu-id="8c660-268">このサービスを使用すると、DNS サーバーの IP アドレスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-268">This service sets the DNS Server IP address.</span></span> <span data-ttu-id="8c660-269">ピアが IPCP 状態で DNS サーバー オプション要求を送信すると、このホストが情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="8c660-269">If the peer sends a DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-270">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-270">Input Parameters</span></span>

- <span data-ttu-id="8c660-271">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-271">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-272">**dns_address**: DNS サーバー アドレス。</span><span class="sxs-lookup"><span data-stu-id="8c660-272">**dns_address**: DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-273">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-273">Return Values</span></span>

- <span data-ttu-id="8c660-274">**NX_SUCCESS**: (0x00) DNS アドレスが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-274">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span>
- <span data-ttu-id="8c660-275">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP はピアとのネゴシエーションを完了していません。</span><span class="sxs-lookup"><span data-stu-id="8c660-275">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="8c660-276">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-276">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-277">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-277">Allowed From</span></span>

<span data-ttu-id="8c660-278">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="8c660-278">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8c660-279">例</span><span class="sxs-lookup"><span data-stu-id="8c660-279">Example</span></span>

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a><span data-ttu-id="8c660-280">nx_ppp_secondary_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="8c660-280">nx_ppp_secondary_dns_address_set</span></span>

<span data-ttu-id="8c660-281">セカンダリ DNS サーバーの IP アドレスを設定します</span><span class="sxs-lookup"><span data-stu-id="8c660-281">Set secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-282">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-282">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="8c660-283">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-283">Description</span></span>

<span data-ttu-id="8c660-284">このサービスを使用すると、セカンダリ DNS サーバーの IP アドレスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-284">This service sets the secondary DNS Server IP address.</span></span> <span data-ttu-id="8c660-285">ピアが IPCP 状態でセカンダリ DNS サーバー オプション要求を送信すると、このホストが情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="8c660-285">If the peer sends a secondary DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-286">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-286">Input Parameters</span></span>

- <span data-ttu-id="8c660-287">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-287">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-288">**dns_address**: セカンダリ DNS サーバー アドレス</span><span class="sxs-lookup"><span data-stu-id="8c660-288">**dns_address**: Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-289">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-289">Return Values</span></span>

- <span data-ttu-id="8c660-290">**NX_SUCCESS**: (0x00) DNS アドレスが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-290">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span> 
- <span data-ttu-id="8c660-291">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP はピアとのネゴシエーションを完了していません。</span><span class="sxs-lookup"><span data-stu-id="8c660-291">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="8c660-292">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-292">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-293">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-293">Allowed From</span></span>

<span data-ttu-id="8c660-294">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="8c660-294">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8c660-295">例</span><span class="sxs-lookup"><span data-stu-id="8c660-295">Example</span></span>

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a><span data-ttu-id="8c660-296">nx_ppp_interface_index_get</span><span class="sxs-lookup"><span data-stu-id="8c660-296">nx_ppp_interface_index_get</span></span>

<span data-ttu-id="8c660-297">IP インターフェイスのインデックスを取得します</span><span class="sxs-lookup"><span data-stu-id="8c660-297">Get IP interface index</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-298">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-298">Prototype</span></span>

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a><span data-ttu-id="8c660-299">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-299">Description</span></span>

<span data-ttu-id="8c660-300">このサービスを使用すると、この PPP インスタンスに関連付けられている IP インターフェイスのインデックスが取得されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-300">This service retrieves the IP interface index associated with this PPP instance.</span></span> <span data-ttu-id="8c660-301">これは、PPP インスタンスが IP インスタンスのプライマリ インターフェイスではない場合にのみ役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8c660-301">This is only useful when the PPP instance is not the primary interface of an IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-302">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-302">Input Parameters</span></span>

- <span data-ttu-id="8c660-303">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-303">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-304">**index_ptr**: インターフェイスのインデックスの格納先</span><span class="sxs-lookup"><span data-stu-id="8c660-304">**index_ptr**: Destination for interface index</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-305">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-305">Return Values</span></span>

- <span data-ttu-id="8c660-306">**NX_SUCCESS**: (0x00) PPP インデックスが正常に取得されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-306">**NX_SUCCESS**: (0x00) Successful PPP index get.</span></span>
- <span data-ttu-id="8c660-307">**NX_IN_PROGRESS**: (0x37) PPP は初期化を完了していません。</span><span class="sxs-lookup"><span data-stu-id="8c660-307">**NX_IN_PROGRESS**: (0x37) PPP has not completed initialization.</span></span>
- <span data-ttu-id="8c660-308">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-308">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-309">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-309">Allowed From</span></span>

<span data-ttu-id="8c660-310">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="8c660-310">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8c660-311">例</span><span class="sxs-lookup"><span data-stu-id="8c660-311">Example</span></span>

```c
ULONG  my_index;

/* Get the interface index for this PPP instance. */
status =  nx_ppp_interface_index_get(&my_ppp, &my_index);

/* If status is NX_SUCCESS the “my_index” contains the IP interface index for
   this PPP instance. */

```
## <a name="nx_ppp_ip_address_assign"></a><span data-ttu-id="8c660-312">nx_ppp_ip_address_assign</span><span class="sxs-lookup"><span data-stu-id="8c660-312">nx_ppp_ip_address_assign</span></span>

<span data-ttu-id="8c660-313">IPCP 用の IP アドレスを割り当てます</span><span class="sxs-lookup"><span data-stu-id="8c660-313">Assign IP addresses for IPCP</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-314">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-314">Prototype</span></span>

```c
UINT nx_ppp_ip_address_assign(NX_PPP *ppp_ptr, ULONG local_ip_address, 
            ULONG peer_ip_address);
```

### <a name="description"></a><span data-ttu-id="8c660-315">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-315">Description</span></span>

<span data-ttu-id="8c660-316">このサービスを使用すると、インターネット プロトコル制御プロトコル (IPCP) で使用するローカルおよびピアの IP アドレスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-316">This service sets up the local and peer IP addresses for use in the Internet Protocol Control Protocol (IPCP).</span></span> <span data-ttu-id="8c660-317">PPP アプリケーションでは、それ自体と他のピアで有効な IP アドレスを持つ PPP インスタンスで、このサービスを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c660-317">The PPP application should invoke this service on a PPP instance with valid IP addresses for itself and the other peer.</span></span>  <span data-ttu-id="8c660-318">有効なアドレスが PPP インスタンスに登録されていない場合は、PPP ピアに依存してその IP アドレスを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c660-318">If no valid addresses are registered with a PPP instance, it must rely on the PPP peer to define its IP address.</span></span>


### <a name="input-parameters"></a><span data-ttu-id="8c660-319">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-319">Input Parameters</span></span>

- <span data-ttu-id="8c660-320">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-320">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-321">**local_ip_address**: ローカル IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="8c660-321">**local_ip_address**: Local IP address.</span></span>
- <span data-ttu-id="8c660-322">**peer_ip_address**: ピアの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="8c660-322">**peer_ip_address**: Peer’s IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-323">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-323">Return Values</span></span>

- <span data-ttu-id="8c660-324">**NX_SUCCESS**: (0x00) PPP アドレスが正常に割り当てられました。</span><span class="sxs-lookup"><span data-stu-id="8c660-324">**NX_SUCCESS**: (0x00) Successful PPP address assignment.</span></span>
- <span data-ttu-id="8c660-325">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-325">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="8c660-326">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-326">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-327">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-327">Allowed From</span></span>

<span data-ttu-id="8c660-328">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="8c660-328">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8c660-329">例</span><span class="sxs-lookup"><span data-stu-id="8c660-329">Example</span></span>

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a><span data-ttu-id="8c660-330">nx_ppp_link_down_notify</span><span class="sxs-lookup"><span data-stu-id="8c660-330">nx_ppp_link_down_notify</span></span>

<span data-ttu-id="8c660-331">リンク ダウン時にアプリケーションに通知します</span><span class="sxs-lookup"><span data-stu-id="8c660-331">Notify application on link down</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-332">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-332">Prototype</span></span>

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a><span data-ttu-id="8c660-333">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-333">Description</span></span>

<span data-ttu-id="8c660-334">このサービスを使用すると、アプリケーションのリンク ダウン通知コールバックが、指定した PPP インスタンスに登録されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-334">This service registers the application’s link down notification callback with the specified PPP instance.</span></span> <span data-ttu-id="8c660-335">NULL 以外の場合、リンクがダウンするたびに、アプリケーションのリンクダウン コールバック関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-335">If non-NULL, the application’s link down callback function is called whenever the link goes down.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-336">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-336">Input Parameters</span></span>

- <span data-ttu-id="8c660-337">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-337">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-338">**link_down_callback**: アプリケーションのリンク ダウン通知関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-338">**link_down_callback**: Application’s link down notification function pointer.</span></span> <span data-ttu-id="8c660-339">NULL の場合、リンクダウン通知は無効になります。</span><span class="sxs-lookup"><span data-stu-id="8c660-339">If NULL, link down notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-340">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-340">Return Values</span></span>

- <span data-ttu-id="8c660-341">**NX_SUCCESS**: (0x00) リンクダウン通知コールバックが正常に登録されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-341">**NX_SUCCESS**: (0x00) Successful link down notification callback registration.</span></span>
- <span data-ttu-id="8c660-342">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-342">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-343">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-343">Allowed From</span></span>

<span data-ttu-id="8c660-344">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="8c660-344">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8c660-345">例</span><span class="sxs-lookup"><span data-stu-id="8c660-345">Example</span></span>

```c
/* Register “my_link_down_callback” to be called whenever the PPP
   link goes down. */
status =  nx_ppp_link_down_notify(&my_ppp, my_link_down_callback);


/* If status is NX_SUCCESS the function “my_link_down_callback” has been
   registered with this PPP instance. */

VOID my_link_down_callback(NX_PPP *ppp_ptr)
{

/* On link down, simply restart PPP.  */
    nx_ppp_restart(ppp_ptr);
} 
```
## <a name="nx_ppp_link_up_notify"></a><span data-ttu-id="8c660-346">nx_ppp_link_up_notify</span><span class="sxs-lookup"><span data-stu-id="8c660-346">nx_ppp_link_up_notify</span></span>

<span data-ttu-id="8c660-347">リンク アップ時にアプリケーションに通知します</span><span class="sxs-lookup"><span data-stu-id="8c660-347">Notify application on link up</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-348">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-348">Prototype</span></span>

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a><span data-ttu-id="8c660-349">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-349">Description</span></span>

<span data-ttu-id="8c660-350">このサービスを使用すると、アプリケーションのリンク アップ通知コールバックが、指定した PPP インスタンスに登録されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-350">This service registers the application’s link up notification callback with the specified PPP instance.</span></span> <span data-ttu-id="8c660-351">NULL 以外の場合、リンクがアップするたびに、アプリケーションのリンクアップ コールバック関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-351">If non-NULL, the application’s link up callback function is called whenever the link comes up.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-352">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-352">Input Parameters</span></span>

- <span data-ttu-id="8c660-353">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-353">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-354">**link_down_callback**: アプリケーションのリンク アップ通知関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-354">**link_up_callback**: Application’s link up notification function pointer.</span></span> <span data-ttu-id="8c660-355">NULL の場合、リンクアップ通知は無効になります。\*\*</span><span class="sxs-lookup"><span data-stu-id="8c660-355">If NULL, link up notification is disabled.\*\*</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-356">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-356">Return Values</span></span>

- <span data-ttu-id="8c660-357">**NX_SUCCESS**: (0x00) リンクアップ通知コールバックが正常に登録されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-357">**NX_SUCCESS**: (0x00) Successful link up notification callback registration.</span></span>
- <span data-ttu-id="8c660-358">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-358">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-359">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-359">Allowed From</span></span>

<span data-ttu-id="8c660-360">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="8c660-360">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8c660-361">例</span><span class="sxs-lookup"><span data-stu-id="8c660-361">Example</span></span>

```c
/* Register “my_link_up_callback” to be called whenever the PPP
   link comes up. */
status =  nx_ppp_link_up_notify(&my_ppp, my_link_up_callback);


/* If status is NX_SUCCESS the function “my_link_up_callback” has been
   registered with this PPP instance. */

VOID my_link_up_callback(NX_PPP *ppp_ptr)
{
    /* On link up, the application my want to start sending/receiving
       UPD/TCP data.  */
}
```

## <a name="nx_ppp_nak_authentication_notify"></a><span data-ttu-id="8c660-362">nx_ppp_nak_authentication_notify</span><span class="sxs-lookup"><span data-stu-id="8c660-362">nx_ppp_nak_authentication_notify</span></span>

<span data-ttu-id="8c660-363">認証 NAK を受信した場合にアプリケーションに通知します</span><span class="sxs-lookup"><span data-stu-id="8c660-363">Notify application if authentication NAK received</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-364">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-364">Prototype</span></span>

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a><span data-ttu-id="8c660-365">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-365">Description</span></span>

<span data-ttu-id="8c660-366">このサービスを使用すると、アプリケーションの認証 NAK 通知コールバックが、指定した PPP インスタンスに登録されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-366">This service registers the application’s authentication nak notification callback with the specified PPP instance.</span></span> <span data-ttu-id="8c660-367">NULL 以外の場合、PPP インスタンスが認証時に NAK を受信するたびに、このコールバック関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-367">If non-NULL, this callback function is called whenever the PPP instance receives a NAK during authentiaction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-368">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-368">Input Parameters</span></span>

- <span data-ttu-id="8c660-369">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-369">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-370">**nak_authentication_notify**: PPP インスタンスが認証 NAK を受信したときに呼び出される関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-370">**nak_authentication_notify**: Pointer to function called when the PPP instance receives an authentication NAK.</span></span> <span data-ttu-id="8c660-371">NULL の場合、通知は無効になります。</span><span class="sxs-lookup"><span data-stu-id="8c660-371">If NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-372">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-372">Return Values</span></span>

- <span data-ttu-id="8c660-373">**NX_SUCCESS**: (0x00) 通知コールバックが正常に登録されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-373">**NX_SUCCESS**: (0x00) Successful notification callback registration.</span></span>
- <span data-ttu-id="8c660-374">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-374">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-375">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-375">Allowed From</span></span>

<span data-ttu-id="8c660-376">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="8c660-376">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8c660-377">例</span><span class="sxs-lookup"><span data-stu-id="8c660-377">Example</span></span>

```c
/* Register “my_nak_auth_callback” to be called whenever the PPP
   receives a NAK during authentication. */
status =  nx_ppp_nak_authentication_notify(&my_ppp, my_nak_auth_callback);

/* If status is NX_SUCCESS the function “my_nak_auth_callback” has been
   registered with this PPP instance. */

VOID my_nak_auth_callback(NX_PPP *ppp_ptr)
{
   /* Handle the situation of receiving an authentication NAK */
}

```

## <a name="nx_ppp_pap_enable"></a><span data-ttu-id="8c660-378">nx_ppp_pap_enable</span><span class="sxs-lookup"><span data-stu-id="8c660-378">nx_ppp_pap_enable</span></span>

<span data-ttu-id="8c660-379">PAP 認証を有効にします</span><span class="sxs-lookup"><span data-stu-id="8c660-379">Enable PAP Authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-380">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-380">Prototype</span></span>

```c

UINT  nx_ppp_pap_enable(NX_PPP *ppp_ptr, 
                        UINT (*generate_login)(CHAR *name, CHAR *password),
                        UINT (*verify_login)(CHAR *name, CHAR *password));
```

### <a name="description"></a><span data-ttu-id="8c660-381">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-381">Description</span></span>

<span data-ttu-id="8c660-382">このサービスを使用すると、指定した PPP インスタンスでパスワード認証プロトコル (PAP) が有効になります。</span><span class="sxs-lookup"><span data-stu-id="8c660-382">This service enables the Password Authentication Protocol (PAP) for the specified PPP instance.</span></span> <span data-ttu-id="8c660-383">"***verify_login***" 関数ポインターが指定されている場合は、この PPP インスタンスに PAP が必要になります。</span><span class="sxs-lookup"><span data-stu-id="8c660-383">If the “***verify_login***” function pointer is specified, PAP is required by this PPP instance.</span></span> <span data-ttu-id="8c660-384">それ以外の場合、PAP は、LCP ネゴシエーション中に指定された、ピアの PAP 要件にのみ応答します。</span><span class="sxs-lookup"><span data-stu-id="8c660-384">Otherwise, PAP only responds to the peer’s PAP requirements as specified during LCP negotiation.</span></span>

<span data-ttu-id="8c660-385">必要なコールバック関数で参照されるデータ項目がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="8c660-385">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="8c660-386">*name* データ項目は、最大サイズが NX_PPP_NAME_SIZE-1 の NULL 終端文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c660-386">The data item *name* is expected to be NULL-terminated string with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="8c660-387">*password* データ項目も、最大サイズが NX_PPP_PASSWORD_SIZE-1 の NULL 終端文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c660-387">The data item *password* is also expected to be a NULL-terminated string with a maximum size of NX_PPP_PASSWORD_SIZE-1.</span></span>

>[!NOTE]
> <span data-ttu-id="8c660-388">この関数は、*nx_ppp_create* の後、*nx_ip_create* または *nx_ip_interface_attach* の前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c660-388">This function must be called after *nx_ppp_create* but before *nx_ip_create* or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-389">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-389">Input Parameters</span></span>

- <span data-ttu-id="8c660-390">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-390">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-391">**generate_login**: ピアによる認証用の *name* と *password* を生成するアプリケーション関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-391">**generate_login**: Pointer to application function that produces a *name* and *password* for authentication by the peer.</span></span> <span data-ttu-id="8c660-392">*name* と *password* の値は、指定されたコピー先にコピーする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8c660-392">Note that the *name* and *password* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="8c660-393">**verify_login**: ピアから提供された *name* と *password* を検証するアプリケーション関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-393">**verify_login**: Pointer to application function that verifies the *name* and *password* supplied by the peer.</span></span> <span data-ttu-id="8c660-394">このルーチンでは、提供された *name* および *password* を比較する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c660-394">This routine must compare the supplied *name* and *password*.</span></span> <span data-ttu-id="8c660-395">このルーチンから NX_SUCCESS が返された場合、名前とパスワードは正しいので、PPP は次の手順に進むことができます。</span><span class="sxs-lookup"><span data-stu-id="8c660-395">If this routine returns NX_SUCCESS, the name and password are correct and PPP can proceed to the next step.</span></span> <span data-ttu-id="8c660-396">それ以外の場合、このルーチンは NX_PPP_ERROR を返します。PPP は別の名前とパスワードを待機するだけです。</span><span class="sxs-lookup"><span data-stu-id="8c660-396">Otherwise, this routine returns NX_PPP_ERROR and PPP simply waits for another name and password.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-397">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-397">Return Values</span></span>

- <span data-ttu-id="8c660-398">**NX_SUCCESS**: (0x00) PPP PAP が正常に有効になりました。</span><span class="sxs-lookup"><span data-stu-id="8c660-398">**NX_SUCCESS**: (0x00) Successful PPP PAP enable.</span></span>
- <span data-ttu-id="8c660-399">**NX_NOT_IMPLEMENTED**: (0x80) NX_PPP_DISABLE_PAP によって PAP ロジックが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="8c660-399">**NX_NOT_IMPLEMENTED**: (0x80) PAP logic was disabled via NX_PPP_DISABLE_PAP.</span></span>
- <span data-ttu-id="8c660-400">NX_PTR_ERROR: (0x07) PPP ポインターまたはアプリケーション関数ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-400">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="8c660-401">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-401">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-402">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-402">Allowed From</span></span>

<span data-ttu-id="8c660-403">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="8c660-403">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8c660-404">例</span><span class="sxs-lookup"><span data-stu-id="8c660-404">Example</span></span>

```c
CHAR    name_string[] = "username";
CHAR    password_string[] =  "password";

/* Enable PAP for PPP instance “my_ppp”. */
status =  nx_ppp_pap_enable(&my_ppp, my_generate_login, my_verify_login);

/* If status is NX_SUCCESS the “my_ppp” now has PAP enabled. */

/* Define callback routines for PAP enable.  */

UINT  generate_login(CHAR *name, CHAR *password)
{

UINT    i;

for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
name[i] = name_string[i];
name[i] =  0;

for (i = 0; i< (NX_PPP_PASSWORD_SIZE-1); i++)
password[i] = password_string[i];
password_string[i] =  0;

return(NX_SUCCESS);  
}

UINT  verify_login(CHAR *name, CHAR *password)
{

/* Assume name and password are correct. Normally, 
a comparison would be made here!  */
printf("Name: %s, Password: %s\n", name, password);

return(NX_SUCCESS);  
}
```

## <a name="nx_ppp_ping_request"></a><span data-ttu-id="8c660-405">nx_ppp_ping_request</span><span class="sxs-lookup"><span data-stu-id="8c660-405">nx_ppp_ping_request</span></span>

<span data-ttu-id="8c660-406">LCP ping 要求を送信します</span><span class="sxs-lookup"><span data-stu-id="8c660-406">Send an LCP ping request</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-407">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-407">Prototype</span></span>

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a><span data-ttu-id="8c660-408">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-408">Description</span></span>

<span data-ttu-id="8c660-409">このサービスを使用すると、LCP ping 要求が送信され、PPP デバイスがエコー応答を待機していることを示すフラグが設定されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-409">This service sends an LCP ping request and sets a flag that the PPP device is waiting for an echo response.</span></span> <span data-ttu-id="8c660-410">要求が送信されるとすぐに、サービスに制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="8c660-410">The service returns as soon as the request is sent.</span></span> <span data-ttu-id="8c660-411">応答を待機することはありません。</span><span class="sxs-lookup"><span data-stu-id="8c660-411">It does not wait for a response.</span></span> 

<span data-ttu-id="8c660-412">対応するエコー応答を受信すると、PPP スレッド タスクによってフラグがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="8c660-412">When a matching echo response is received, the PPP thread task will clear the flag.</span></span> <span data-ttu-id="8c660-413">PPP デバイスは、PPP ネゴシエーションの LCP 部分を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c660-413">The PPP device must have completed the LCP part of the PPP negotiation.</span></span>

<span data-ttu-id="8c660-414">このサービスは、リンクの状態を確認するためのハードウェアのポーリングを簡単に行うことができない可能性がある PPP 設定で役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8c660-414">This service is useful for PPP set ups where polling the hardware for link status may not be readily possible.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-415">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-415">Input Parameters</span></span>

- <span data-ttu-id="8c660-416">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-416">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-417">**data**: エコー要求で送信するデータへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-417">**data**: Pointer to data to send in echo request.</span></span>
- <span data-ttu-id="8c660-418">**data_size**: 送信するデータのサイズ。wait_option: LCP エコー メッセージの送信を待機する時間。</span><span class="sxs-lookup"><span data-stu-id="8c660-418">**data_size**: Size of data to send wait_option Time to wait to send the LCP echo message.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-419">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-419">Return Values</span></span>

- <span data-ttu-id="8c660-420">**NX_SUCCESS**: (0x00) エコー要求が正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-420">**NX_SUCCESS**: (0x00) Successful sent echo request.</span></span>
- <span data-ttu-id="8c660-421">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP 接続が確立されていません。</span><span class="sxs-lookup"><span data-stu-id="8c660-421">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP connection not established.</span></span>
- <span data-ttu-id="8c660-422">NX_PTR_ERROR: (0x07) PPP ポインターまたはアプリケーション関数ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-422">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="8c660-423">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-423">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-424">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-424">Allowed From</span></span>

<span data-ttu-id="8c660-425">アプリケーション スレッド</span><span class="sxs-lookup"><span data-stu-id="8c660-425">Application threads</span></span>

### <a name="example"></a><span data-ttu-id="8c660-426">例</span><span class="sxs-lookup"><span data-stu-id="8c660-426">Example</span></span>

```c

CHAR    buffer[] = "username";
UINT    buffer_length =  strlen("username ");

/* Send an LCP ping request”. */
status =  nx_ppp_ping_request(&my_ppp, &buffer[0], buffer_length, 200);

/* If status is NX_SUCCESS the LCP echo request was successfully sent. Now wait to 
   receive a response. */

while(my_ppp.nx_ppp_lcp_echo_reply_id > 0)
{
    tx_thread_sleep(100);
}

/* Got a valid reply! */
```

## <a name="nx_ppp_raw_string_send"></a><span data-ttu-id="8c660-427">nx_ppp_raw_string_send</span><span class="sxs-lookup"><span data-stu-id="8c660-427">nx_ppp_raw_string_send</span></span>

<span data-ttu-id="8c660-428">生の ASCII 文字列を送信します</span><span class="sxs-lookup"><span data-stu-id="8c660-428">Send a raw ASCII string</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-429">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-429">Prototype</span></span>

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a><span data-ttu-id="8c660-430">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-430">Description</span></span>

<span data-ttu-id="8c660-431">このサービスを使用すると、PPP 以外の ASCII 文字列が PPP インターフェイスから直接送信されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-431">This service sends a non-PPP ASCII string directly out the PPP interface.</span></span> <span data-ttu-id="8c660-432">通常、モデム制御情報を含む PPP 以外のパケットを PPP が受信した後に使用されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-432">It is typically used after PPP receives a non-PPP packet that contains modem control information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-433">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-433">Input Parameters</span></span>

- <span data-ttu-id="8c660-434">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-434">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-435">**string_ptr**: 送信する文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-435">**string_ptr**: Pointer to string to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-436">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-436">Return Values</span></span>

- <span data-ttu-id="8c660-437">**NX_SUCCESS**: (0x00) PPP 生文字列が正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-437">**NX_SUCCESS**: (0x00) Successful PPP raw string send.</span></span>
- <span data-ttu-id="8c660-438">NX_PTR_ERROR: (0x07) PPP ポインターまたは文字列ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-438">NX_PTR_ERROR: (0x07) Invalid PPP pointer or string pointer.</span></span>
- <span data-ttu-id="8c660-439">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-439">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-440">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-440">Allowed From</span></span>

<span data-ttu-id="8c660-441">Threads</span><span class="sxs-lookup"><span data-stu-id="8c660-441">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c660-442">例</span><span class="sxs-lookup"><span data-stu-id="8c660-442">Example</span></span>

```c

/* Send “CLIENTSERVER” to “CLIENT” sent by Windows 98 before PPP is
initiated.  */
status =  nx_ppp_raw_string_send(&my_ppp, “CLIENTSERVER”);

/* If status is NX_SUCCESS the raw string was successfully Sent via PPP. */
```
## <a name="nx_ppp_restart"></a><span data-ttu-id="8c660-443">nx_ppp_restart</span><span class="sxs-lookup"><span data-stu-id="8c660-443">nx_ppp_restart</span></span>

<span data-ttu-id="8c660-444">PPP の処理を再開します</span><span class="sxs-lookup"><span data-stu-id="8c660-444">Restart PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-445">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-445">Prototype</span></span>

```c
UINT  nx_ppp_restart(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="8c660-446">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-446">Description</span></span>

<span data-ttu-id="8c660-447">このサービスを使用すると、PPP の処理が再開されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-447">This service restarts the PPP processing.</span></span> <span data-ttu-id="8c660-448">通常、リンクを再確立する必要がある場合に、リンクダウン コールバックから呼び出されるか、通信が失われたことを示す PPP 以外のモデム メッセージによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-448">It is typically called when the link needs to be re-established either from a link down callback or by a non-PPP modem message indicating communication was lost.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-449">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-449">Input Parameters</span></span>

- <span data-ttu-id="8c660-450">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-450">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-451">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-451">Return Values</span></span>

- <span data-ttu-id="8c660-452">**NX_SUCCESS**: (0x00) PPP の再開が正常に開始されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-452">**NX_SUCCESS**: (0x00) Successful PPP restart initiated.</span></span>
- <span data-ttu-id="8c660-453">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-453">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="8c660-454">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-454">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-455">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-455">Allowed From</span></span>

<span data-ttu-id="8c660-456">Threads</span><span class="sxs-lookup"><span data-stu-id="8c660-456">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c660-457">例</span><span class="sxs-lookup"><span data-stu-id="8c660-457">Example</span></span>

```c
/* Restart the PPP instance “my_ppp”.  */
status =  nx_ppp_restart(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been restarted. */
```

## <a name="nx_ppp_start"></a><span data-ttu-id="8c660-458">nx_ppp_start</span><span class="sxs-lookup"><span data-stu-id="8c660-458">nx_ppp_start</span></span>

<span data-ttu-id="8c660-459">PPP の処理を開始します</span><span class="sxs-lookup"><span data-stu-id="8c660-459">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-460">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-460">Prototype</span></span>

```c
UINT  nx_ppp_start(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="8c660-461">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-461">Description</span></span>

<span data-ttu-id="8c660-462">このサービスを使用すると、PPP の処理が開始されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-462">This service starts the PPP processing.</span></span> <span data-ttu-id="8c660-463">通常は、nx_ppp_stop() が呼び出された後に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-463">It is typically called after nx_ppp_stop() called.</span></span>

>[!NOTE]
> <span data-ttu-id="8c660-464">PPP では、リンクが有効になると、PPP の処理が自動的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-464">PPP automatically starts the PPP processing when the link is enabled.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-465">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-465">Input Parameters</span></span>

- <span data-ttu-id="8c660-466">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-466">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-467">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-467">Return Values</span></span>

- <span data-ttu-id="8c660-468">**NX_SUCCESS**: (0x00) PPP が正常に開始されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-468">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="8c660-469">**NX_PPP_ALREADY_STARTED**: (0xb9) PPP は既に開始されています。</span><span class="sxs-lookup"><span data-stu-id="8c660-469">**NX_PPP_ALREADY_STARTED**: (0xb9) PPP already started.</span></span>
- <span data-ttu-id="8c660-470">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-470">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="8c660-471">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-471">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-472">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-472">Allowed From</span></span>

<span data-ttu-id="8c660-473">Threads</span><span class="sxs-lookup"><span data-stu-id="8c660-473">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c660-474">例</span><span class="sxs-lookup"><span data-stu-id="8c660-474">Example</span></span>

```c
/* Start the PPP instance “my_ppp”.  */
status =  nx_ppp_start(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been started. */
```

## <a name="nx_ppp_status_get"></a><span data-ttu-id="8c660-475">nx_ppp_status_get</span><span class="sxs-lookup"><span data-stu-id="8c660-475">nx_ppp_status_get</span></span>

<span data-ttu-id="8c660-476">PPP の現在の状態を取得します</span><span class="sxs-lookup"><span data-stu-id="8c660-476">Get current PPP status</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-477">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-477">Prototype</span></span>

```c
UINT  nx_ppp_status_get(NX_PPP *ppp_ptr, UINT *status_ptr);
```
### <a name="description"></a><span data-ttu-id="8c660-478">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-478">Description</span></span>

<span data-ttu-id="8c660-479">このサービスを使用すると、指定した PPP インスタンスの現在の状態が取得されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-479">This service gets the current status of the specified PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-480">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-480">Input Parameters</span></span>

- <span data-ttu-id="8c660-481">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-481">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-482">**status_ptr**: PPP の状態の格納先。可能性のある状態値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8c660-482">**status_ptr**: Destination for the PPP status, the following are possible status values:</span></span>
    - <span data-ttu-id="8c660-483">**NX_PPP_STATUS_ESTABLISHED**</span><span class="sxs-lookup"><span data-stu-id="8c660-483">**NX_PPP_STATUS_ESTABLISHED**</span></span>
    - <span data-ttu-id="8c660-484">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="8c660-484">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="8c660-485">**NX_PPP_STATUS_LCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="8c660-485">**NX_PPP_STATUS_LCP_FAILED**</span></span>
    - <span data-ttu-id="8c660-486">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="8c660-486">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="8c660-487">**NX_PPP_STATUS_PAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="8c660-487">**NX_PPP_STATUS_PAP_FAILED**</span></span>
    - <span data-ttu-id="8c660-488">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="8c660-488">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="8c660-489">**NX_PPP_STATUS_CHAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="8c660-489">**NX_PPP_STATUS_CHAP_FAILED**</span></span>
    - <span data-ttu-id="8c660-490">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="8c660-490">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="8c660-491">**NX_PPP_STATUS_IPCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="8c660-491">**NX_PPP_STATUS_IPCP_FAILED**</span></span>

>[!NOTE]
> <span data-ttu-id="8c660-492">状態は、API から NX_SUCCESS が返された場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-492">The status is only valid if the API returns NX_SUCCESS.</span></span> <span data-ttu-id="8c660-493">さらに、\*_FAILED 状態値のいずれかが返された場合、PPP の処理は、アプリケーションによってもう一度再開されるまで実質的に停止されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-493">In addition, if any of the \*_FAILED status values are returned, PPP processing is effectively stopped until it is restarted again by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-494">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-494">Return Values</span></span>

- <span data-ttu-id="8c660-495">**NX_SUCCESS**: (0x00) PPP 状態要求が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-495">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="8c660-496">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-496">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-497">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-497">Allowed From</span></span>

<span data-ttu-id="8c660-498">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="8c660-498">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8c660-499">例</span><span class="sxs-lookup"><span data-stu-id="8c660-499">Example</span></span>

```c
UINT ppp_status;
UINT status;


/* Get the current status of PPP instance “my_ppp”.  */
status =  nx_ppp_status_get(&my_ppp, &ppp_status);

/* If status is NX_SUCCESS the current internal PPP status is contained in
   “ppp_status”. */
```
## <a name="nx_ppp_stop"></a><span data-ttu-id="8c660-500">nx_ppp_stop</span><span class="sxs-lookup"><span data-stu-id="8c660-500">nx_ppp_stop</span></span>

<span data-ttu-id="8c660-501">PPP の処理を開始します</span><span class="sxs-lookup"><span data-stu-id="8c660-501">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-502">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-502">Prototype</span></span>

```c
UINT  nx_ppp_stop(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="8c660-503">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-503">Description</span></span>

<span data-ttu-id="8c660-504">このサービスを使用すると、PPP の処理が停止されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-504">This service stops the PPP processing.</span></span> <span data-ttu-id="8c660-505">ユーザーは、必要に応じて nx_ppp_start() を呼び出して、PPP の処理を開始することもできます。</span><span class="sxs-lookup"><span data-stu-id="8c660-505">User also can calls nx_ppp_start() to start the PPP processing if needed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-506">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-506">Input Parameters</span></span>

- <span data-ttu-id="8c660-507">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-507">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-508">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-508">Return Values</span></span>

- <span data-ttu-id="8c660-509">**NX_SUCCESS**: (0x00) PPP が正常に開始されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-509">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="8c660-510">**NX_PPP_ALREADY_STOPPED**: (0xb8) PPP は既に停止しています。</span><span class="sxs-lookup"><span data-stu-id="8c660-510">**NX_PPP_ALREADY_STOPPED**: (0xb8) PPP already stopped.</span></span>
- <span data-ttu-id="8c660-511">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-511">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="8c660-512">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-512">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-513">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-513">Allowed From</span></span>

<span data-ttu-id="8c660-514">Threads</span><span class="sxs-lookup"><span data-stu-id="8c660-514">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c660-515">例</span><span class="sxs-lookup"><span data-stu-id="8c660-515">Example</span></span>

```c
/* Stop the PPP instance “my_ppp”.  */
status =  nx_ppp_stop(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been stopped. */
```
## <a name="nx_ppp_packet_receive"></a><span data-ttu-id="8c660-516">nx_ppp_packet_receive</span><span class="sxs-lookup"><span data-stu-id="8c660-516">nx_ppp_packet_receive</span></span>

<span data-ttu-id="8c660-517">PPP パケットを受信します</span><span class="sxs-lookup"><span data-stu-id="8c660-517">Receive PPP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-518">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-518">Prototype</span></span>

```c
UINT  nx_ppp_packet_receive(NX_PPP *ppp_ptr, NX_PACKET *packet_ptr);

```

### <a name="description"></a><span data-ttu-id="8c660-519">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-519">Description</span></span>

<span data-ttu-id="8c660-520">このサービスを使用すると、PPP パケットが受信されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-520">This service receives PPP packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-521">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-521">Input Parameters</span></span>

- <span data-ttu-id="8c660-522">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-522">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-523">**packet_ptr**: PPP パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-523">**packet_ptr**: Pointer to PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-524">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-524">Return Values</span></span>

- <span data-ttu-id="8c660-525">**NX_SUCCESS**: (0x00) PPP 状態要求が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-525">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="8c660-526">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-526">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-527">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-527">Allowed From</span></span>

<span data-ttu-id="8c660-528">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="8c660-528">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8c660-529">例</span><span class="sxs-lookup"><span data-stu-id="8c660-529">Example</span></span>

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a><span data-ttu-id="8c660-530">nx_ppp_packet_send_set</span><span class="sxs-lookup"><span data-stu-id="8c660-530">nx_ppp_packet_send_set</span></span>

<span data-ttu-id="8c660-531">PPP パケット送信関数を設定します</span><span class="sxs-lookup"><span data-stu-id="8c660-531">Set the PPP packet send function</span></span>

### <a name="prototype"></a><span data-ttu-id="8c660-532">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="8c660-532">Prototype</span></span>

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a><span data-ttu-id="8c660-533">説明</span><span class="sxs-lookup"><span data-stu-id="8c660-533">Description</span></span>

<span data-ttu-id="8c660-534">このサービスを使用すると、PPP パケット送信関数が設定されます。</span><span class="sxs-lookup"><span data-stu-id="8c660-534">This service sets the PPP packet send funciton.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c660-535">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c660-535">Input Parameters</span></span>

- <span data-ttu-id="8c660-536">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c660-536">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="8c660-537">**nx_ppp_packet_send**: PPP パケットを送信するルーチン。</span><span class="sxs-lookup"><span data-stu-id="8c660-537">**nx_ppp_packet_send**: Routine to send PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c660-538">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c660-538">Return Values</span></span>

- <span data-ttu-id="8c660-539">**NX_SUCCESS**: (0x00) PPP 状態要求が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="8c660-539">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="8c660-540">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="8c660-540">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c660-541">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="8c660-541">Allowed From</span></span>

<span data-ttu-id="8c660-542">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="8c660-542">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8c660-543">例</span><span class="sxs-lookup"><span data-stu-id="8c660-543">Example</span></span>

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```