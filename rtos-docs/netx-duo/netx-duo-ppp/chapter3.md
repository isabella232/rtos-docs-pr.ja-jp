---
title: 第 3 章 - Azure RTOS NetX Duo Point-to-Point プロトコル (PPP) サービスの説明
description: この章では、すべての Azure RTOS NetX Duo PPP サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 90c24cad5e595087ba27178243f9dda0dab11029
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810640"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-point-to-point-protocol-ppp-services"></a><span data-ttu-id="499bf-103">第 3 章 - Azure RTOS NetX Duo Point-to-Point プロトコル (PPP) サービスの説明</span><span class="sxs-lookup"><span data-stu-id="499bf-103">Chapter 3 - Description of Azure RTOS NetX Duo Point-to-Point Protocol (PPP) services</span></span>

<span data-ttu-id="499bf-104">この章では、すべての Azure RTOS NetX Duo PPP サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="499bf-104">This chapter contains a description of all Azure RTOS NetX Duo PPP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="499bf-105">以下の API の説明の「戻り値」セクションで、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字でない値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="499bf-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="499bf-106">**nx_ppp_byte_receive**: "*シリアル ISR からバイトを受信する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-106">**nx_ppp_byte_receive**: *Receive a byte from serial ISR*</span></span>
- <span data-ttu-id="499bf-107">**nx_ppp_chap_challenge**: "*CHAP チャレンジを生成する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-107">**nx_ppp_chap_challenge**: *Generate a CHAP challenge*</span></span>
- <span data-ttu-id="499bf-108">**nx_ppp_chap_enable**: "*CHAP 認証を有効にする*"</span><span class="sxs-lookup"><span data-stu-id="499bf-108">**nx_ppp_chap_enable**: *Enable CHAP authentication*</span></span>
- <span data-ttu-id="499bf-109">**nx_ppp_create**: "*PPP インスタンスを作成する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-109">**nx_ppp_create**: *Create a PPP instance*</span></span>
- <span data-ttu-id="499bf-110">**nx_ppp_delete**: "*PPP インスタンスを削除する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-110">**nx_ppp_delete**: *Delete a PPP instance*</span></span>
- <span data-ttu-id="499bf-111">**nx_ppp_dns_address_get**: "*DNS サーバーの IP アドレスを取得する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-111">**nx_ppp_dns_address_get**: *Get DNS Server IP address*</span></span>
- <span data-ttu-id="499bf-112">**nx_ppp_dns_address_set**: "*DNS サーバーの IP アドレスを設定する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-112">**nx_ppp_dns_address_set**:*Set DNS Server IP address*</span></span>
- <span data-ttu-id="499bf-113">**nx_ppp_secondary_dns_address_get**: "*セカンダリ DNS サーバーの IP アドレスを取得する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-113">**nx_ppp_secondary_dns_address_get**: *Get Secondary DNS Server IP address*</span></span>
- <span data-ttu-id="499bf-114">**nx_ppp_secondary_dns_address_set**: "*セカンダリ DNS サーバーの IP アドレスを設定する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-114">**nx_ppp_secondary_dns_address_set**: *Set Secondary_DNS Server IP address*</span></span>
- <span data-ttu-id="499bf-115">**nx_ppp_interface_index_get**: "*IP インターフェイス インデックスを取得する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-115">**nx_ppp_interface_index_get**: *Get IP interface index*</span></span>
- <span data-ttu-id="499bf-116">**nx_ppp_ip_address_assign**: "*IPCP 用の IP アドレスを割り当てる*"</span><span class="sxs-lookup"><span data-stu-id="499bf-116">**nx_ppp_ip_address_assign**: *Assign IP addresses for IPCP*</span></span>
- <span data-ttu-id="499bf-117">**nx_ppp_link_down_notify**: "*リンクダウン時にアプリケーションに通知する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-117">**nx_ppp_link_down_notify**: *Notify application on link down*</span></span>
- <span data-ttu-id="499bf-118">**nx_ppp_link_down_notify**: "*リンクアップ時にアプリケーションに通知する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-118">**nx_ppp_link_up_notify**: *Notify application on link up*</span></span>
- <span data-ttu-id="499bf-119">**nx_ppp_nak_authentication_notify**: "*認証 NAK を受信した場合にアプリケーションに通知する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-119">**nx_ppp_nak_authentication_notify**: *Notify application if authentication NAK is received*</span></span>
- <span data-ttu-id="499bf-120">**nx_ppp_pap_enable**: "*PAP 認証を有効にする*"</span><span class="sxs-lookup"><span data-stu-id="499bf-120">**nx_ppp_pap_enable**: *Enable PAP authentication*</span></span>
- <span data-ttu-id="499bf-121">**nx_ppp_ping_request**: "*LCP エコー要求を送信する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-121">**nx_ppp_ping_request**: *Send an LCP echo request*</span></span>
- <span data-ttu-id="499bf-122">**nx_ppp_raw_string_send**: "*PPP 以外の文字列を送信する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-122">**nx_ppp_raw_string_send**: *Send non PPP string*</span></span>
- <span data-ttu-id="499bf-123">**nx_ppp_restart**: "*PPP の処理を再開する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-123">**nx_ppp_restart**: *Restart PPP processing*</span></span>
- <span data-ttu-id="499bf-124">**nx_ppp_start**: "*PPP の処理を開始する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-124">**nx_ppp_start**: *Start PPP processing*</span></span>
- <span data-ttu-id="499bf-125">**nx_ppp_status_get**: "*PPP の現在の状態を取得する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-125">**nx_ppp_status_get**: *Get current PPP status*</span></span>
- <span data-ttu-id="499bf-126">**nx_ppp_stop**: "*PPP の処理を停止する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-126">**nx_ppp_stop**: *Stop PPP processing*</span></span>
- <span data-ttu-id="499bf-127">**nx_ppp_packet_receive**: "*PPP パケットを受信する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-127">**nx_ppp_packet_receive**: *Receive PPP packet*</span></span>
- <span data-ttu-id="499bf-128">**nx_ppp_packet_send_set**: "*PPP パケット送信関数を設定する*"</span><span class="sxs-lookup"><span data-stu-id="499bf-128">**nx_ppp_packet_send_set**: *Set PPP packet send function*</span></span>

## <a name="nx_ppp_byte_receive"></a><span data-ttu-id="499bf-129">nx_ppp_byte_receive</span><span class="sxs-lookup"><span data-stu-id="499bf-129">nx_ppp_byte_receive</span></span>

<span data-ttu-id="499bf-130">シリアル ISR からバイトを受信する</span><span class="sxs-lookup"><span data-stu-id="499bf-130">Receive a byte from serial ISR</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-131">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-131">Prototype</span></span>

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a><span data-ttu-id="499bf-132">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-132">Description</span></span>

<span data-ttu-id="499bf-133">このサービスは通常、受信したバイトを PPP に転送するために、アプリケーションのシリアル ドライバーの割り込みサービス ルーチン (ISR) から呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="499bf-133">This service is typically called from the application’s serial driver Interrupt Service Routine (ISR) to transfer a received byte to PPP.</span></span> <span data-ttu-id="499bf-134">呼び出されると、このルーチンは受信したバイトを循環バイト バッファーに配置し、処理のために適切な PPP スレッドに通知します。</span><span class="sxs-lookup"><span data-stu-id="499bf-134">When called, this routine places the received byte into a circular byte buffer and notifies the appropriate PPP thread for processing.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-135">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-135">Input Parameters</span></span>

- <span data-ttu-id="499bf-136">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-136">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-137">**byte**: シリアル デバイスから受信したバイト。</span><span class="sxs-lookup"><span data-stu-id="499bf-137">**byte**: Byte received from serial device</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-138">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-138">Return Values</span></span>

- <span data-ttu-id="499bf-139">**NX_SUCCESS**: (0x00) PPP バイトを正常に受信しました。</span><span class="sxs-lookup"><span data-stu-id="499bf-139">**NX_SUCCESS**: (0x00) Successful PPP byte receive.</span></span>
- <span data-ttu-id="499bf-140">**NX_PPP_BUFFER_FULL**: (0xB1) PPP シリアル バッファーが既にいっぱいになっています。</span><span class="sxs-lookup"><span data-stu-id="499bf-140">**NX_PPP_BUFFER_FULL**: (0xB1) PPP serial buffer is already full.</span></span>
- <span data-ttu-id="499bf-141">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-141">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-142">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-142">Allowed From</span></span>

<span data-ttu-id="499bf-143">スレッド、ISR</span><span class="sxs-lookup"><span data-stu-id="499bf-143">Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="499bf-144">例</span><span class="sxs-lookup"><span data-stu-id="499bf-144">Example</span></span>

```c
/* Notify “my_ppp” of a received byte. */
status =  nx_ppp_byte_receive(&my_ppp, new_byte);

/* If status is NX_SUCCESS the received byte was successfully
   buffered. */
```

## <a name="nx_ppp_chap_challenge"></a><span data-ttu-id="499bf-145">nx_ppp_chap_challenge</span><span class="sxs-lookup"><span data-stu-id="499bf-145">nx_ppp_chap_challenge</span></span>

<span data-ttu-id="499bf-146">CHAP チャレンジを生成する</span><span class="sxs-lookup"><span data-stu-id="499bf-146">Generate a CHAP challenge</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-147">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-147">Prototype</span></span>

```c
UINT nx_ppp_chap_challenge(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="499bf-148">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-148">Description</span></span>

<span data-ttu-id="499bf-149">このサービスでは、PPP 接続が稼働状態になった後に CHAP チャレンジを開始します。</span><span class="sxs-lookup"><span data-stu-id="499bf-149">This service initiates a CHAP challenge after the PPP connection is already up and running.</span></span> <span data-ttu-id="499bf-150">これにより、アプリケーションは接続の信頼性を定期的に確認できます。</span><span class="sxs-lookup"><span data-stu-id="499bf-150">This gives the application the ability to verify the authenticity of the connection on a periodic basis.</span></span> <span data-ttu-id="499bf-151">チャレンジが失敗すると、PPP リンクは閉じられます。</span><span class="sxs-lookup"><span data-stu-id="499bf-151">If the challenge is unsuccessful, the PPP link is closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-152">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-152">Input Parameters</span></span>

- <span data-ttu-id="499bf-153">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-153">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-154">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-154">Return Values</span></span>

- <span data-ttu-id="499bf-155">**NX_SUCCESS**: (0x00) PPP チャレンジが正常に開始されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-155">**NX_SUCCESS**: (0x00) Successful PPP challenge initiated.</span></span>
- <span data-ttu-id="499bf-156">**NX_PPP_FAILURE**: (0xB0) PPP チャレンジが無効です。CHAP は応答でのみ有効になっています。</span><span class="sxs-lookup"><span data-stu-id="499bf-156">**NX_PPP_FAILURE**: (0xB0) Invalid PPP challenge, CHAP was enabled only for response.</span></span>
- <span data-ttu-id="499bf-157">**NX_NOT_IMPLEMENTED**: (0x80) NX_PPP_DISABLE_CHAP によって CHAP ロジックが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="499bf-157">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="499bf-158">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-158">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="499bf-159">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-159">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-160">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-160">Allowed From</span></span>

<span data-ttu-id="499bf-161">Threads</span><span class="sxs-lookup"><span data-stu-id="499bf-161">Threads</span></span>

### <a name="example"></a><span data-ttu-id="499bf-162">例</span><span class="sxs-lookup"><span data-stu-id="499bf-162">Example</span></span>

```c
/* Initiate a PPP challenge for instance “my_ppp”. */
status =  nx_ppp_chap_challenge(&my_ppp);

/* If status is NX_SUCCESS a CHAP challenge “my_ppp” was successfully 
initiated. */
```

## <a name="nx_ppp_chap_enable"></a><span data-ttu-id="499bf-163">nx_ppp_chap_enable</span><span class="sxs-lookup"><span data-stu-id="499bf-163">nx_ppp_chap_enable</span></span>

<span data-ttu-id="499bf-164">CHAP 認証を有効にする</span><span class="sxs-lookup"><span data-stu-id="499bf-164">Enable CHAP authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-165">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-165">Prototype</span></span>

```c
UINT nx_ppp_chap_enable(NX_PPP *ppp_ptr, 
                        UINT (*get_challenge_values)(CHAR *rand_value,CHAR *id,CHAR *name),
                        UINT (*get_responder_values)(CHAR *system,CHAR *name,CHAR *secret),
                        UINT (*get_verification_values)(CHAR *system,CHAR *name,CHAR *secret)); 
```

### <a name="description"></a><span data-ttu-id="499bf-166">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-166">Description</span></span>

<span data-ttu-id="499bf-167">このサービスでは、指定された PPP インスタンスのチャレンジ ハンドシェイク認証プロトコル (CHAP) を有効にします。</span><span class="sxs-lookup"><span data-stu-id="499bf-167">This service enables the Challenge-Handshake Authentication Protocol (CHAP) for the specified PPP instance.</span></span>

<span data-ttu-id="499bf-168">関数ポインター "\***get_challenge_values** _" と "_ \*_get_verification_values_\*\*" が指定されている場合、この PPP インスタンスに CHAP が必要になります。</span><span class="sxs-lookup"><span data-stu-id="499bf-168">If the “\***get_challenge_values**_” and “_\*_get_verification_values_\*\*” function pointers are specified, CHAP is required by this PPP instance.</span></span> <span data-ttu-id="499bf-169">それ以外の場合、CHAP はピアのチャレンジ要求にのみ応答します。</span><span class="sxs-lookup"><span data-stu-id="499bf-169">Otherwise, CHAP only responds to the peer’s challenge requests.</span></span>

<span data-ttu-id="499bf-170">必要なコールバック関数で参照されるデータ項目がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="499bf-170">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="499bf-171">*secret*、*name*、*system* の各データ項目は、最大サイズが NX_PPP_NAME_SIZE-1 の NULL 終端文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="499bf-171">The data items *secret*, *name*, and *system* are expected to be NULL-terminated strings with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="499bf-172">*rand_value* データ項目は、最大サイズが NX_PPP_VALUE_SIZE-1 の NULL 終端文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="499bf-172">The data item *rand_value* is expected to be a NULL-terminated string with a maximum size of NX_PPP_VALUE_SIZE-1.</span></span> <span data-ttu-id="499bf-173">*id* データ項目は、単純な符号なし文字型です。</span><span class="sxs-lookup"><span data-stu-id="499bf-173">The data item *id* is a simple unsigned character type.</span></span>

>[!NOTE]
> <span data-ttu-id="499bf-174">この関数は、*nx_ppp_create* の後、nx_ip_create または *nx_ip_interface_attach* の前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="499bf-174">This function must be called after *nx_ppp_create* but before nx_ip_create or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-175">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-175">Input Parameters</span></span>

- <span data-ttu-id="499bf-176">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-176">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-177">**get_challenge_values**: チャレンジに使用される値を取得するアプリケーション関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-177">**get_challenge_values**: Pointer to application function to retrieve values used for the challenge.</span></span> <span data-ttu-id="499bf-178">*rand_value*、*id*、*secret* の各値は、指定されたコピー先にコピーする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="499bf-178">Note that the *rand_value*, *id*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="499bf-179">**get_responder_values**: チャレンジへの応答に使用される値を取得するアプリケーション関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-179">**get_responder_values**: Pointer to application function that retrieves values used to respond to a challenge.</span></span> <span data-ttu-id="499bf-180">*system*、*name*、*secret* の各値は、指定されたコピー先にコピーする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="499bf-180">Note that the *system*, *name*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="499bf-181">**get_verification_values**: チャレンジ応答の検証に使用される値を取得するアプリケーション関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-181">**get_verification_values**: Pointer to application function that retrieves values used to verify the challenge response.</span></span> <span data-ttu-id="499bf-182">*system*、*name*、*secret* の各値は、指定されたコピー先にコピーする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="499bf-182">Note that the *system*,*name*, and *secret* values must be copied into the supplied destinations.</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-183">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-183">Return Values</span></span>

- <span data-ttu-id="499bf-184">**NX_SUCCESS**: (0x00) PPP CHAP が正常に有効になりました。</span><span class="sxs-lookup"><span data-stu-id="499bf-184">**NX_SUCCESS**: (0x00) Successful PPP CHAP enable</span></span>
- <span data-ttu-id="499bf-185">**NX_NOT_IMPLEMENTED**: (0x80) NX_PPP_DISABLE_CHAP によって CHAP ロジックが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="499bf-185">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="499bf-186">NX_PTR_ERROR: (0x07) PPP ポインターまたはコールバック関数ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-186">NX_PTR_ERROR: (0x07) Invalid PPP pointer or callback function pointer.</span></span> <span data-ttu-id="499bf-187">*get_challenge_values* が指定されている場合は、*get_verification_values* 関数も指定する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="499bf-187">Note that if *get_challenge_values* is specified, then the *get_verification_values* function must also be supplied.</span></span>
- <span data-ttu-id="499bf-188">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-188">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-189">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-189">Allowed From</span></span>

<span data-ttu-id="499bf-190">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="499bf-190">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="499bf-191">例</span><span class="sxs-lookup"><span data-stu-id="499bf-191">Example</span></span>

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
## <a name="nx_ppp_create"></a><span data-ttu-id="499bf-192">nx_ppp_create</span><span class="sxs-lookup"><span data-stu-id="499bf-192">nx_ppp_create</span></span>

<span data-ttu-id="499bf-193">PPP インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="499bf-193">Create a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-194">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-194">Prototype</span></span>

```c
UINT  nx_ppp_create(NX_PPP *ppp_ptr, CHAR *name, NX_IP *ip_ptr, 
                    VOID *stack_memory_ptr, ULONG stack_size, 
                    UINT thread_priority, NX_PACKET_POOL *pool_ptr,
                    void (*ppp_invalid_packet_handler)(NX_PACKET *packet_ptr),
                    void (*ppp_byte_send)(UCHAR byte));
```

### <a name="description"></a><span data-ttu-id="499bf-195">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-195">Description</span></span>

<span data-ttu-id="499bf-196">このサービスでは、指定された NetX IP インスタンスの PPP インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="499bf-196">This service creates a PPP instance for the specified NetX IP instance.</span></span> <span data-ttu-id="499bf-197">NetX IP インスタンスを作成する前に、この関数を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="499bf-197">This function must be called prior to creating the NetX IP instance.</span></span>

>[!NOTE]
> <span data-ttu-id="499bf-198">一般に、PPP スレッドの優先順位よりも高い優先順位で NetX IP スレッドを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="499bf-198">It is generally a good idea to create the NetX IP thread at a higher priority than the PPP thread priority.</span></span> <span data-ttu-id="499bf-199">IP スレッドの優先順位の指定の詳細については、*nx_ip_create* サービスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="499bf-199">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-200">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-200">Input Parameters</span></span>

- <span data-ttu-id="499bf-201">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-201">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-202">**name**: この PPP インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="499bf-202">**name**: Name of this PPP instance.</span></span>
- <span data-ttu-id="499bf-203">**ip_ptr**: まだ作成されていない IP インスタンスの制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-203">**ip_ptr**: Pointer to control block for not-yet-created IP instance.</span></span>
- <span data-ttu-id="499bf-204">**stack_memory_ptr**: PPP スレッドのスタック領域の先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-204">**stack_memory_ptr**: Pointer to start of PPP thread’s stack area.</span></span>
- <span data-ttu-id="499bf-205">**stack_size**: スレッドのスタックのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="499bf-205">**stack_size**: Size in bytes in the thread’s stack.</span></span>
- <span data-ttu-id="499bf-206">**pool_ptr**: 既定のパケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-206">**pool_ptr**: Pointer to default packet pool.</span></span>
- <span data-ttu-id="499bf-207">**thread_priority**: 内部 PPP スレッドの優先順位 (1 - 31)。</span><span class="sxs-lookup"><span data-stu-id="499bf-207">**thread_priority**: Priority of internal PPP threads (1-31).</span></span>
- <span data-ttu-id="499bf-208">**ppp_invalid_packet_handler**: PPP 以外のすべてのパケットに対するアプリケーションのハンドラーへの関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-208">**ppp_invalid_packet_handler**: Function pointer to application’s handler for all non-PPP packets.</span></span> <span data-ttu-id="499bf-209">通常、NetX PPP は初期化中にこのルーチンを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="499bf-209">The NetX PPP typically calls this routine during initialization.</span></span> <span data-ttu-id="499bf-210">ここで、アプリケーションはモデムのコマンドに応答できます。Windows XP の場合、NetX PPP アプリケーションでは、Windows XP によって送信された最初の "CLIENT" に "CLIENT SERVER" で応答することで PPP を開始できます。</span><span class="sxs-lookup"><span data-stu-id="499bf-210">This is where the application can respond to modem commands or in the case of Windows XP, the NetX PPP application can initiate PPP by responding with“ CLIENT SERVER” to the initial “CLIENT” sent by Windows XP.</span></span>
- <span data-ttu-id="499bf-211">**ppp_byte_send**: アプリケーションのシリアル バイト出力ルーチンへの関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-211">**ppp_byte_send**: Function pointer to application’s serial byte output routine.</span></span>


### <a name="return-values"></a><span data-ttu-id="499bf-212">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-212">Return Values</span></span>

- <span data-ttu-id="499bf-213">**NX_SUCCESS**: (0x00) PPP が正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-213">**NX_SUCCESS**: (0x00) Successful PPP create.</span></span>
- <span data-ttu-id="499bf-214">NX_PTR_ERROR: (0x07) PPP、IP、またはバイト出力関数ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-214">NX_PTR_ERROR: (0x07) Invalid PPP, IP, or byte output function pointer.</span></span>
- <span data-ttu-id="499bf-215">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-215">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-216">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-216">Allowed From</span></span>

<span data-ttu-id="499bf-217">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="499bf-217">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="499bf-218">例</span><span class="sxs-lookup"><span data-stu-id="499bf-218">Example</span></span>

```c
/* Create “my_ppp” for IP instance “my_ip”. */
status =  nx_ppp_create(&my_ppp, “my PPP”, &my_ip, stack_start, 1024, 2, 
                        &my_pool, my_invalid_packet_handler, my_out_byte);

/* If status is NX_SUCCESS the PPP instance was successfully
   created. */
```

## <a name="nx_ppp_delete"></a><span data-ttu-id="499bf-219">nx_ppp_delete</span><span class="sxs-lookup"><span data-stu-id="499bf-219">nx_ppp_delete</span></span>

<span data-ttu-id="499bf-220">PPP インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="499bf-220">Delete a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-221">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-221">Prototype</span></span>

```c
UINT nx_ppp_delete(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="499bf-222">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-222">Description</span></span>

<span data-ttu-id="499bf-223">このサービスでは、以前に作成された PPP インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="499bf-223">This service deletes the previously created PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-224">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-224">Input Parameters</span></span>

- <span data-ttu-id="499bf-225">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-225">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-226">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-226">Return Values</span></span>

- <span data-ttu-id="499bf-227">**NX_SUCCESS**: (0x00) PPP が正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-227">**NX_SUCCESS**: (0x00) Successful PPP deletion.</span></span>
- <span data-ttu-id="499bf-228">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-228">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="499bf-229">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-229">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-230">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-230">Allowed From</span></span>

<span data-ttu-id="499bf-231">Threads</span><span class="sxs-lookup"><span data-stu-id="499bf-231">Threads</span></span>

### <a name="example"></a><span data-ttu-id="499bf-232">例</span><span class="sxs-lookup"><span data-stu-id="499bf-232">Example</span></span>

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a><span data-ttu-id="499bf-233">nx_ppp_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="499bf-233">nx_ppp_dns_address_get</span></span>

<span data-ttu-id="499bf-234">DNS サーバーの IP アドレスを取得する</span><span class="sxs-lookup"><span data-stu-id="499bf-234">Get DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-235">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-235">Prototype</span></span>

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="499bf-236">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-236">Description</span></span>

<span data-ttu-id="499bf-237">このサービスでは、IPCP ハンドシェイクでピアから提供された DNS IP アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="499bf-237">This service retrieves the DNS IP address supplied by the peer in the IPCP handshake.</span></span> <span data-ttu-id="499bf-238">ピアから IP アドレスが提供されていない場合は、IP アドレスとして 0 が返されます。</span><span class="sxs-lookup"><span data-stu-id="499bf-238">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-239">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-239">Input Parameters</span></span>

- <span data-ttu-id="499bf-240">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-240">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-241">**dns_address_ptr**: DNS サーバー アドレスの宛先。</span><span class="sxs-lookup"><span data-stu-id="499bf-241">**dns_address_ptr**: Destination for DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-242">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-242">Return Values</span></span>

- <span data-ttu-id="499bf-243">**NX_SUCCESS**: (0x00) DNS アドレスが正常に取得されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-243">**NX_SUCCESS**: (0x00) Successful DNS address get.</span></span>
- <span data-ttu-id="499bf-244">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP はピアとのネゴシエーションを完了していません。</span><span class="sxs-lookup"><span data-stu-id="499bf-244">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="499bf-245">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-245">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-246">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-246">Allowed From</span></span>

<span data-ttu-id="499bf-247">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="499bf-247">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="499bf-248">例</span><span class="sxs-lookup"><span data-stu-id="499bf-248">Example</span></span>

```c

ULONG  my_dns_address;

/* Get DNS Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a><span data-ttu-id="499bf-249">nx_ppp_secondary_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="499bf-249">nx_ppp_secondary_dns_address_get</span></span>

<span data-ttu-id="499bf-250">セカンダリ DNS サーバーの IP アドレスを取得する</span><span class="sxs-lookup"><span data-stu-id="499bf-250">Get Secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-251">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-251">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="499bf-252">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-252">Description</span></span>

<span data-ttu-id="499bf-253">このサービスでは、IPCP ハンドシェイクでピアによって提供されたセカンダリ DNS IP アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="499bf-253">This service retrieves the secondary DNS IP address supplied by the peer in the IPCP handshake.</span></span> <span data-ttu-id="499bf-254">ピアから IP アドレスが提供されていない場合は、IP アドレスとして 0 が返されます。</span><span class="sxs-lookup"><span data-stu-id="499bf-254">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-255">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-255">Input Parameters</span></span>

- <span data-ttu-id="499bf-256">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-256">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-257">**dns_address_ptr**: セカンダリ DNS サーバー アドレスの宛先。</span><span class="sxs-lookup"><span data-stu-id="499bf-257">**dns_address_ptr**: Destination for Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-258">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-258">Return Values</span></span>

- <span data-ttu-id="499bf-259">**NX_SUCCESS**: (0x00) DNS アドレスが正常に取得されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-259">**NX_SUCCESS**: (0x00) Successful DNS address get.</span></span>
- <span data-ttu-id="499bf-260">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP はピアとのネゴシエーションを完了していません。</span><span class="sxs-lookup"><span data-stu-id="499bf-260">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="499bf-261">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-261">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-262">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-262">Allowed From</span></span>

<span data-ttu-id="499bf-263">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="499bf-263">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="499bf-264">例</span><span class="sxs-lookup"><span data-stu-id="499bf-264">Example</span></span>

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a><span data-ttu-id="499bf-265">nx_ppp_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="499bf-265">nx_ppp_dns_address_set</span></span>

<span data-ttu-id="499bf-266">プライマリ DNS サーバーの IP アドレスを設定する</span><span class="sxs-lookup"><span data-stu-id="499bf-266">Set primary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-267">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-267">Prototype</span></span>

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="499bf-268">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-268">Description</span></span>

<span data-ttu-id="499bf-269">このサービスでは、DNS サーバーの IP アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="499bf-269">This service sets the DNS Server IP address.</span></span> <span data-ttu-id="499bf-270">ピアが IPCP 状態で DNS サーバー オプション要求を送信すると、このホストが情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="499bf-270">If the peer sends a DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-271">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-271">Input Parameters</span></span>

- <span data-ttu-id="499bf-272">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-272">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-273">**dns_address**: DNS サーバー アドレス。</span><span class="sxs-lookup"><span data-stu-id="499bf-273">**dns_address**: DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-274">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-274">Return Values</span></span>

- <span data-ttu-id="499bf-275">**NX_SUCCESS**: (0x00) DNS アドレスが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-275">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span>
- <span data-ttu-id="499bf-276">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP はピアとのネゴシエーションを完了していません。</span><span class="sxs-lookup"><span data-stu-id="499bf-276">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="499bf-277">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-277">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-278">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-278">Allowed From</span></span>

<span data-ttu-id="499bf-279">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="499bf-279">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="499bf-280">例</span><span class="sxs-lookup"><span data-stu-id="499bf-280">Example</span></span>

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a><span data-ttu-id="499bf-281">nx_ppp_secondary_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="499bf-281">nx_ppp_secondary_dns_address_set</span></span>

<span data-ttu-id="499bf-282">セカンダリ DNS サーバーの IP アドレスを設定する</span><span class="sxs-lookup"><span data-stu-id="499bf-282">Set secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-283">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-283">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="499bf-284">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-284">Description</span></span>

<span data-ttu-id="499bf-285">このサービスは、セカンダリ DNS サーバーの IP アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="499bf-285">This service sets the secondary DNS Server IP address.</span></span> <span data-ttu-id="499bf-286">ピアが IPCP 状態でセカンダリ DNS サーバー オプション要求を送信すると、このホストが情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="499bf-286">If the peer sends a secondary DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-287">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-287">Input Parameters</span></span>

- <span data-ttu-id="499bf-288">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-288">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-289">**dns_address**: セカンダリ DNS サーバー アドレス。</span><span class="sxs-lookup"><span data-stu-id="499bf-289">**dns_address**: Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-290">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-290">Return Values</span></span>

- <span data-ttu-id="499bf-291">**NX_SUCCESS**: (0x00) DNS アドレスが正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-291">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span> 
- <span data-ttu-id="499bf-292">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP はピアとのネゴシエーションを完了していません。</span><span class="sxs-lookup"><span data-stu-id="499bf-292">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="499bf-293">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-293">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-294">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-294">Allowed From</span></span>

<span data-ttu-id="499bf-295">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="499bf-295">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="499bf-296">例</span><span class="sxs-lookup"><span data-stu-id="499bf-296">Example</span></span>

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a><span data-ttu-id="499bf-297">nx_ppp_interface_index_get</span><span class="sxs-lookup"><span data-stu-id="499bf-297">nx_ppp_interface_index_get</span></span>

<span data-ttu-id="499bf-298">IP インターフェイス インデックスを取得する</span><span class="sxs-lookup"><span data-stu-id="499bf-298">Get IP interface index</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-299">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-299">Prototype</span></span>

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a><span data-ttu-id="499bf-300">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-300">Description</span></span>

<span data-ttu-id="499bf-301">このサービスでは、この PPP インスタンスに関連付けられている IP インターフェイス インデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="499bf-301">This service retrieves the IP interface index associated with this PPP instance.</span></span> <span data-ttu-id="499bf-302">これは、PPP インスタンスが IP インスタンスのプライマリ インターフェイスではない場合にのみ役立ちます。</span><span class="sxs-lookup"><span data-stu-id="499bf-302">This is only useful when the PPP instance is not the primary interface of an IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-303">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-303">Input Parameters</span></span>

- <span data-ttu-id="499bf-304">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-304">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-305">**index_ptr**: インターフェイス インデックスの参照先。</span><span class="sxs-lookup"><span data-stu-id="499bf-305">**index_ptr**: Destination for interface index</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-306">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-306">Return Values</span></span>

- <span data-ttu-id="499bf-307">**NX_SUCCESS**: (0x00) PPP インデックスが正常に取得されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-307">**NX_SUCCESS**: (0x00) Successful PPP index get.</span></span>
- <span data-ttu-id="499bf-308">**NX_IN_PROGRESS**: (0x37) PPP は初期化を完了していません。</span><span class="sxs-lookup"><span data-stu-id="499bf-308">**NX_IN_PROGRESS**: (0x37) PPP has not completed initialization.</span></span>
- <span data-ttu-id="499bf-309">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-309">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-310">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-310">Allowed From</span></span>

<span data-ttu-id="499bf-311">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="499bf-311">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="499bf-312">例</span><span class="sxs-lookup"><span data-stu-id="499bf-312">Example</span></span>

```c
ULONG  my_index;

/* Get the interface index for this PPP instance. */
status =  nx_ppp_interface_index_get(&my_ppp, &my_index);

/* If status is NX_SUCCESS the “my_index” contains the IP interface index for
   this PPP instance. */

```
## <a name="nx_ppp_ip_address_assign"></a><span data-ttu-id="499bf-313">nx_ppp_ip_address_assign</span><span class="sxs-lookup"><span data-stu-id="499bf-313">nx_ppp_ip_address_assign</span></span>

<span data-ttu-id="499bf-314">IPCP 用の IP アドレスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="499bf-314">Assign IP addresses for IPCP</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-315">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-315">Prototype</span></span>

```c
UINT nx_ppp_ip_address_assign(NX_PPP *ppp_ptr, ULONG local_ip_address, 
            ULONG peer_ip_address);
```

### <a name="description"></a><span data-ttu-id="499bf-316">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-316">Description</span></span>

<span data-ttu-id="499bf-317">このサービスでは、インターネット プロトコル制御プロトコル (IPCP) で使用するローカルおよびピアの IP アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="499bf-317">This service sets up the local and peer IP addresses for use in the Internet Protocol Control Protocol (IPCP.</span></span> <span data-ttu-id="499bf-318">これは、自身ともう一方のピアの有効な IP アドレスを備えた PPP インスタンスに対して呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="499bf-318">It should be called for the PPP instance that has valid IP addresses for itself and the other peer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-319">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-319">Input Parameters</span></span>

- <span data-ttu-id="499bf-320">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-320">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-321">**local_ip_address**: ローカル IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="499bf-321">**local_ip_address**: Local IP address.</span></span>
- <span data-ttu-id="499bf-322">**peer_ip_address**: ピアの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="499bf-322">**peer_ip_address**: Peer’s IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-323">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-323">Return Values</span></span>

- <span data-ttu-id="499bf-324">**NX_SUCCESS**: (0x00) PPP アドレスが正常に割り当てられました。</span><span class="sxs-lookup"><span data-stu-id="499bf-324">**NX_SUCCESS**: (0x00) Successful PPP address assignment.</span></span>
- <span data-ttu-id="499bf-325">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-325">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="499bf-326">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-326">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-327">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-327">Allowed From</span></span>

<span data-ttu-id="499bf-328">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="499bf-328">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="499bf-329">例</span><span class="sxs-lookup"><span data-stu-id="499bf-329">Example</span></span>

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a><span data-ttu-id="499bf-330">nx_ppp_link_down_notify</span><span class="sxs-lookup"><span data-stu-id="499bf-330">nx_ppp_link_down_notify</span></span>

<span data-ttu-id="499bf-331">リンクダウン時にアプリケーションに通知する</span><span class="sxs-lookup"><span data-stu-id="499bf-331">Notify application on link down</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-332">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-332">Prototype</span></span>

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a><span data-ttu-id="499bf-333">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-333">Description</span></span>

<span data-ttu-id="499bf-334">このサービスでは、アプリケーションのリンクダウン通知コールバックを、指定された PPP インスタンスに登録します。</span><span class="sxs-lookup"><span data-stu-id="499bf-334">This service registers the application’s link down notification callback with the specified PPP instance.</span></span> <span data-ttu-id="499bf-335">NULL 以外の場合、リンクがダウンするたびに、アプリケーションのリンクダウン コールバック関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="499bf-335">If non-NULL, the application’s link down callback function is called whenever the link goes down.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-336">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-336">Input Parameters</span></span>

- <span data-ttu-id="499bf-337">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-337">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-338">**link_down_callback**: アプリケーションのリンクダウン通知関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-338">**link_down_callback**: Application’s link down notification function pointer.</span></span> <span data-ttu-id="499bf-339">NULL の場合、リンクダウン通知は無効になります。</span><span class="sxs-lookup"><span data-stu-id="499bf-339">If NULL, link down notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-340">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-340">Return Values</span></span>

- <span data-ttu-id="499bf-341">**NX_SUCCESS**: (0x00) リンクダウン通知コールバックが正常に登録されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-341">**NX_SUCCESS**: (0x00) Successful link down notification callback registration.</span></span>
- <span data-ttu-id="499bf-342">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-342">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-343">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-343">Allowed From</span></span>

<span data-ttu-id="499bf-344">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="499bf-344">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="499bf-345">例</span><span class="sxs-lookup"><span data-stu-id="499bf-345">Example</span></span>

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
## <a name="nx_ppp_link_up_notify"></a><span data-ttu-id="499bf-346">nx_ppp_link_up_notify</span><span class="sxs-lookup"><span data-stu-id="499bf-346">nx_ppp_link_up_notify</span></span>

<span data-ttu-id="499bf-347">リンクアップ時にアプリケーションに通知する</span><span class="sxs-lookup"><span data-stu-id="499bf-347">Notify application on link up</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-348">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-348">Prototype</span></span>

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a><span data-ttu-id="499bf-349">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-349">Description</span></span>

<span data-ttu-id="499bf-350">このサービスでは、アプリケーションのリンクアップ通知コールバックを、指定された PPP インスタンスに登録します。</span><span class="sxs-lookup"><span data-stu-id="499bf-350">This service registers the application’s link up notification callback with the specified PPP instance.</span></span> <span data-ttu-id="499bf-351">NULL 以外の場合、リンクがアップするたびに、アプリケーションのリンクアップ コールバック関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="499bf-351">If non-NULL, the application’s link up callback function is called whenever the link comes up.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-352">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-352">Input Parameters</span></span>

- <span data-ttu-id="499bf-353">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-353">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-354">**link_down_callback**: アプリケーションのリンク アップ通知関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-354">**link_up_callback**: Application’s link up notification function pointer.</span></span> <span data-ttu-id="499bf-355">NULL の場合、リンクアップ通知は無効になります。\*\*</span><span class="sxs-lookup"><span data-stu-id="499bf-355">If NULL, link up notification is disabled.\*\*</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-356">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-356">Return Values</span></span>

- <span data-ttu-id="499bf-357">**NX_SUCCESS**: (0x00) リンクアップ通知コールバックが正常に登録されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-357">**NX_SUCCESS**: (0x00) Successful link up notification callback registration.</span></span>
- <span data-ttu-id="499bf-358">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-358">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-359">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-359">Allowed From</span></span>

<span data-ttu-id="499bf-360">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="499bf-360">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="499bf-361">例</span><span class="sxs-lookup"><span data-stu-id="499bf-361">Example</span></span>

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

## <a name="nx_ppp_nak_authentication_notify"></a><span data-ttu-id="499bf-362">nx_ppp_nak_authentication_notify</span><span class="sxs-lookup"><span data-stu-id="499bf-362">nx_ppp_nak_authentication_notify</span></span>

<span data-ttu-id="499bf-363">認証 NAK を受信した場合にアプリケーションに通知する</span><span class="sxs-lookup"><span data-stu-id="499bf-363">Notify application if authentication NAK received</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-364">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-364">Prototype</span></span>

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a><span data-ttu-id="499bf-365">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-365">Description</span></span>

<span data-ttu-id="499bf-366">このサービスは、アプリケーションの認証 NAK 通知コールバックを、指定された PPP インスタンスに登録します。</span><span class="sxs-lookup"><span data-stu-id="499bf-366">This service registers the application’s authentication nak notification callback with the specified PPP instance.</span></span> <span data-ttu-id="499bf-367">NULL 以外の場合、PPP インスタンスが認証時に NAK を受信するたびに、このコールバック関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="499bf-367">If non-NULL, this callback function is called whenever the PPP instance receives a NAK during authentiaction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-368">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-368">Input Parameters</span></span>

- <span data-ttu-id="499bf-369">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-369">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-370">**nak_authentication_notify**: PPP インスタンスが認証 NAK を受信したときに呼び出される関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-370">**nak_authentication_notify**: Pointer to function called when the PPP instance receives an authentication NAK.</span></span> <span data-ttu-id="499bf-371">NULL の場合、通知は無効になります。</span><span class="sxs-lookup"><span data-stu-id="499bf-371">If NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-372">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-372">Return Values</span></span>

- <span data-ttu-id="499bf-373">**NX_SUCCESS**: (0x00) 通知コールバックが正常に登録されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-373">**NX_SUCCESS**: (0x00) Successful notification callback registration.</span></span>
- <span data-ttu-id="499bf-374">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-374">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-375">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-375">Allowed From</span></span>

<span data-ttu-id="499bf-376">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="499bf-376">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="499bf-377">例</span><span class="sxs-lookup"><span data-stu-id="499bf-377">Example</span></span>

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

## <a name="nx_ppp_pap_enable"></a><span data-ttu-id="499bf-378">nx_ppp_pap_enable</span><span class="sxs-lookup"><span data-stu-id="499bf-378">nx_ppp_pap_enable</span></span>

<span data-ttu-id="499bf-379">PAP 認証を有効にする</span><span class="sxs-lookup"><span data-stu-id="499bf-379">Enable PAP Authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-380">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-380">Prototype</span></span>

```c

UINT  nx_ppp_pap_enable(NX_PPP *ppp_ptr, 
                        UINT (*generate_login)(CHAR *name, CHAR *password),
                        UINT (*verify_login)(CHAR *name, CHAR *password));
```

### <a name="description"></a><span data-ttu-id="499bf-381">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-381">Description</span></span>

<span data-ttu-id="499bf-382">このサービスは、指定された PPP インスタンスのパスワード認証プロトコル (PAP) を有効にします。</span><span class="sxs-lookup"><span data-stu-id="499bf-382">This service enables the Password Authentication Protocol (PAP) for the specified PPP instance.</span></span> <span data-ttu-id="499bf-383">"***verify_login***" 関数ポインターが指定されている場合は、この PPP インスタンスに PAP が必要になります。</span><span class="sxs-lookup"><span data-stu-id="499bf-383">If the “***verify_login***” function pointer is specified, PAP is required by this PPP instance.</span></span> <span data-ttu-id="499bf-384">それ以外の場合、PAP は、LCP ネゴシエーション中に指定された、ピアの PAP 要件にのみ応答します。</span><span class="sxs-lookup"><span data-stu-id="499bf-384">Otherwise, PAP only responds to the peer’s PAP requirements as specified during LCP negotiation.</span></span>

<span data-ttu-id="499bf-385">必要なコールバック関数で参照されるデータ項目がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="499bf-385">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="499bf-386">*name* データ項目は、最大サイズが NX_PPP_NAME_SIZE-1 の NULL 終端文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="499bf-386">The data item *name* is expected to be NULL-terminated string with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="499bf-387">*password* データ項目も、最大サイズが NX_PPP_PASSWORD_SIZE-1 の NULL 終端文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="499bf-387">The data item *password* is also expected to be a NULL-terminated string with a maximum size of NX_PPP_PASSWORD_SIZE-1.</span></span>

>[!NOTE]
> <span data-ttu-id="499bf-388">この関数は、*nx_ppp_create* の後、*nx_ip_create* または *nx_ip_interface_attach* の前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="499bf-388">This function must be called after *nx_ppp_create* but before *nx_ip_create* or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-389">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-389">Input Parameters</span></span>

- <span data-ttu-id="499bf-390">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-390">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-391">**generate_login**: ピアによる認証用の *name* と *password* を生成するアプリケーション関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-391">**generate_login**: Pointer to application function that produces a *name* and *password* for authentication by the peer.</span></span> <span data-ttu-id="499bf-392">*name* と *password* の値は、指定されたコピー先にコピーする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="499bf-392">Note that the *name* and *password* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="499bf-393">**verify_login**: ピアから提供された *name* と *password* を検証するアプリケーション関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-393">**verify_login**: Pointer to application function that verifies the *name* and *password* supplied by the peer.</span></span> <span data-ttu-id="499bf-394">このルーチンでは、提供された *name* および *password* を比較する必要があります。</span><span class="sxs-lookup"><span data-stu-id="499bf-394">This routine must compare the supplied *name* and *password*.</span></span> <span data-ttu-id="499bf-395">このルーチンから NX_SUCCESS が返された場合、名前とパスワードは正しいので、PPP は次の手順に進むことができます。</span><span class="sxs-lookup"><span data-stu-id="499bf-395">If this routine returns NX_SUCCESS, the name and password are correct and PPP can proceed to the next step.</span></span> <span data-ttu-id="499bf-396">それ以外の場合、このルーチンは NX_PPP_ERROR を返します。PPP は別の名前とパスワードを待機するだけです。</span><span class="sxs-lookup"><span data-stu-id="499bf-396">Otherwise, this routine returns NX_PPP_ERROR and PPP simply waits for another name and password.</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-397">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-397">Return Values</span></span>

- <span data-ttu-id="499bf-398">**NX_SUCCESS**: (0x00) PPP PAP が正常に有効になりました。</span><span class="sxs-lookup"><span data-stu-id="499bf-398">**NX_SUCCESS**: (0x00) Successful PPP PAP enable.</span></span>
- <span data-ttu-id="499bf-399">**NX_NOT_IMPLEMENTED**: (0x80) NX_PPP_DISABLE_PAP によって PAP ロジックが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="499bf-399">**NX_NOT_IMPLEMENTED**: (0x80) PAP logic was disabled via NX_PPP_DISABLE_PAP.</span></span>
- <span data-ttu-id="499bf-400">NX_PTR_ERROR: (0x07) PPP ポインターまたはアプリケーション関数ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-400">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="499bf-401">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-401">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-402">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-402">Allowed From</span></span>

<span data-ttu-id="499bf-403">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="499bf-403">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="499bf-404">例</span><span class="sxs-lookup"><span data-stu-id="499bf-404">Example</span></span>

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

## <a name="nx_ppp_ping_request"></a><span data-ttu-id="499bf-405">nx_ppp_ping_request</span><span class="sxs-lookup"><span data-stu-id="499bf-405">nx_ppp_ping_request</span></span>

<span data-ttu-id="499bf-406">LCP ping 要求を送信する</span><span class="sxs-lookup"><span data-stu-id="499bf-406">Send an LCP ping request</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-407">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-407">Prototype</span></span>

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a><span data-ttu-id="499bf-408">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-408">Description</span></span>

<span data-ttu-id="499bf-409">このサービスでは LCP 要求を送信し、PPP デバイスがエコー応答を待機していることを示すフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="499bf-409">This service sends an LCP request and sets a flag that the PPP device is waiting for an echo response.</span></span> <span data-ttu-id="499bf-410">待機オプションは、主に *nx_packet_allocate* 呼び出し用です。</span><span class="sxs-lookup"><span data-stu-id="499bf-410">The wait option is primarily for the *nx_packet_allocate* call.</span></span> <span data-ttu-id="499bf-411">要求が送信されるとすぐに、サービスに制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="499bf-411">The service returns as soon as the request is sent.</span></span> <span data-ttu-id="499bf-412">応答を待機することはありません。</span><span class="sxs-lookup"><span data-stu-id="499bf-412">It does not wait for a response.</span></span> 

<span data-ttu-id="499bf-413">対応するエコー応答を受信すると、PPP スレッド タスクによってフラグがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="499bf-413">When a matching echo response is received, the PPP thread task will clear the flag.</span></span> <span data-ttu-id="499bf-414">PPP デバイスは、PPP ネゴシエーションの LCP 部分を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="499bf-414">The PPP device must have completed the LCP part of the PPP negotiation.</span></span>

<span data-ttu-id="499bf-415">このサービスは、リンクの状態を確認するためのハードウェアのポーリングを簡単に行うことができない可能性がある PPP 設定で役立ちます。</span><span class="sxs-lookup"><span data-stu-id="499bf-415">This service is useful for PPP set ups where polling the hardware for link status may not be readily possible.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-416">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-416">Input Parameters</span></span>

- <span data-ttu-id="499bf-417">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-417">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-418">**data**: エコー要求で送信するデータへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-418">**data**: Pointer to data to send in echo request.</span></span>
- <span data-ttu-id="499bf-419">**data_size**: 送信するデータのサイズ。wait_option: LCP エコー メッセージの送信を待機する時間。</span><span class="sxs-lookup"><span data-stu-id="499bf-419">**data_size**: Size of data to send wait_option Time to wait to send the LCP echo message.</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-420">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-420">Return Values</span></span>

- <span data-ttu-id="499bf-421">**NX_SUCCESS**: (0x00) エコー要求が正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-421">**NX_SUCCESS**: (0x00) Successful sent echo request.</span></span>
- <span data-ttu-id="499bf-422">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP 接続が確立されていません。</span><span class="sxs-lookup"><span data-stu-id="499bf-422">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP connection not established.</span></span>
- <span data-ttu-id="499bf-423">NX_PTR_ERROR: (0x07) PPP ポインターまたはアプリケーション関数ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-423">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="499bf-424">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-424">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-425">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-425">Allowed From</span></span>

<span data-ttu-id="499bf-426">アプリケーション スレッド</span><span class="sxs-lookup"><span data-stu-id="499bf-426">Application threads</span></span>

### <a name="example"></a><span data-ttu-id="499bf-427">例</span><span class="sxs-lookup"><span data-stu-id="499bf-427">Example</span></span>

```c

CHAR    buffer[] = "username";
UINT    buffer_length =  sizeof("username ") - 1;

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

## <a name="nx_ppp_raw_string_send"></a><span data-ttu-id="499bf-428">nx_ppp_raw_string_send</span><span class="sxs-lookup"><span data-stu-id="499bf-428">nx_ppp_raw_string_send</span></span>

<span data-ttu-id="499bf-429">生の ASCII 文字列を送信する</span><span class="sxs-lookup"><span data-stu-id="499bf-429">Send a raw ASCII string</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-430">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-430">Prototype</span></span>

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a><span data-ttu-id="499bf-431">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-431">Description</span></span>

<span data-ttu-id="499bf-432">このサービスでは、PPP 以外の ASCII 文字列を PPP インターフェイスから直接送信します。</span><span class="sxs-lookup"><span data-stu-id="499bf-432">This service sends a non-PPP ASCII string directly out the PPP interface.</span></span> <span data-ttu-id="499bf-433">通常、モデム制御情報を含む PPP 以外のパケットを PPP が受信した後に使用されます。</span><span class="sxs-lookup"><span data-stu-id="499bf-433">It is typically used after PPP receives an non-PPP packet that contains modem control information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-434">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-434">Input Parameters</span></span>

- <span data-ttu-id="499bf-435">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-435">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-436">**string_ptr**: 送信する文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-436">**string_ptr**: Pointer to string to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-437">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-437">Return Values</span></span>

- <span data-ttu-id="499bf-438">**NX_SUCCESS**: (0x00) PPP 生文字列が正常に送信されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-438">**NX_SUCCESS**: (0x00) Successful PPP raw string send.</span></span>
- <span data-ttu-id="499bf-439">NX_PTR_ERROR: (0x07) PPP ポインターまたは文字列ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-439">NX_PTR_ERROR: (0x07) Invalid PPP pointer or string pointer.</span></span>
- <span data-ttu-id="499bf-440">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-440">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-441">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-441">Allowed From</span></span>

<span data-ttu-id="499bf-442">Threads</span><span class="sxs-lookup"><span data-stu-id="499bf-442">Threads</span></span>

### <a name="example"></a><span data-ttu-id="499bf-443">例</span><span class="sxs-lookup"><span data-stu-id="499bf-443">Example</span></span>

```c

/* Send “CLIENTSERVER” to “CLIENT” sent by Windows 98 before PPP is
initiated.  */
status =  nx_ppp_raw_string_send(&my_ppp, “CLIENTSERVER”);

/* If status is NX_SUCCESS the raw string was successfully Sent via PPP. */
```
## <a name="nx_ppp_restart"></a><span data-ttu-id="499bf-444">nx_ppp_restart</span><span class="sxs-lookup"><span data-stu-id="499bf-444">nx_ppp_restart</span></span>

<span data-ttu-id="499bf-445">PPP の処理を再開する</span><span class="sxs-lookup"><span data-stu-id="499bf-445">Restart PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-446">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-446">Prototype</span></span>

```c
UINT  nx_ppp_restart(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="499bf-447">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-447">Description</span></span>

<span data-ttu-id="499bf-448">このサービスは PPP の処理を再開します。</span><span class="sxs-lookup"><span data-stu-id="499bf-448">This service restarts the PPP processing.</span></span> <span data-ttu-id="499bf-449">通常、リンクを再確立する必要がある場合に、リンクダウン コールバックから呼び出されるか、通信が失われたことを示す PPP 以外のモデム メッセージによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="499bf-449">It is typically called when the link needs to be re-established either from a link down callback or by a non-PPP modem message indicating communication was lost.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-450">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-450">Input Parameters</span></span>

- <span data-ttu-id="499bf-451">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-451">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-452">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-452">Return Values</span></span>

- <span data-ttu-id="499bf-453">**NX_SUCCESS**: (0x00) PPP の再開が正常に開始されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-453">**NX_SUCCESS**: (0x00) Successful PPP restart initiated.</span></span>
- <span data-ttu-id="499bf-454">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-454">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="499bf-455">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-455">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-456">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-456">Allowed From</span></span>

<span data-ttu-id="499bf-457">Threads</span><span class="sxs-lookup"><span data-stu-id="499bf-457">Threads</span></span>

### <a name="example"></a><span data-ttu-id="499bf-458">例</span><span class="sxs-lookup"><span data-stu-id="499bf-458">Example</span></span>

```c
/* Restart the PPP instance “my_ppp”.  */
status =  nx_ppp_restart(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been restarted. */
```

## <a name="nx_ppp_start"></a><span data-ttu-id="499bf-459">nx_ppp_start</span><span class="sxs-lookup"><span data-stu-id="499bf-459">nx_ppp_start</span></span>

<span data-ttu-id="499bf-460">PPP の処理を開始する</span><span class="sxs-lookup"><span data-stu-id="499bf-460">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-461">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-461">Prototype</span></span>

```c
UINT  nx_ppp_start(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="499bf-462">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-462">Description</span></span>

<span data-ttu-id="499bf-463">このサービスは PPP の処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="499bf-463">This service starts the PPP processing.</span></span> <span data-ttu-id="499bf-464">通常は、nx_ppp_stop() が呼び出された後に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="499bf-464">It is typically called after nx_ppp_stop() called.</span></span>

>[!NOTE]
> <span data-ttu-id="499bf-465">PPP では、リンクが有効になると、PPP の処理が自動的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="499bf-465">PPP automatically starts the PPP processing when the link is enabled.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-466">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-466">Input Parameters</span></span>

- <span data-ttu-id="499bf-467">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-467">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-468">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-468">Return Values</span></span>

- <span data-ttu-id="499bf-469">**NX_SUCCESS**: (0x00) PPP が正常に開始されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-469">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="499bf-470">**NX_PPP_ALREADY_STARTED**: (0xb9) PPP は既に開始されています。</span><span class="sxs-lookup"><span data-stu-id="499bf-470">**NX_PPP_ALREADY_STARTED**: (0xb9) PPP already started.</span></span>
- <span data-ttu-id="499bf-471">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-471">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="499bf-472">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-472">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-473">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-473">Allowed From</span></span>

<span data-ttu-id="499bf-474">Threads</span><span class="sxs-lookup"><span data-stu-id="499bf-474">Threads</span></span>

### <a name="example"></a><span data-ttu-id="499bf-475">例</span><span class="sxs-lookup"><span data-stu-id="499bf-475">Example</span></span>

```c
/* Start the PPP instance “my_ppp”.  */
status =  nx_ppp_start(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been started. */
```

## <a name="nx_ppp_status_get"></a><span data-ttu-id="499bf-476">nx_ppp_status_get</span><span class="sxs-lookup"><span data-stu-id="499bf-476">nx_ppp_status_get</span></span>

<span data-ttu-id="499bf-477">PPP の現在の状態を取得する</span><span class="sxs-lookup"><span data-stu-id="499bf-477">Get current PPP status</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-478">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-478">Prototype</span></span>

```c
UINT  nx_ppp_status_get(NX_PPP *ppp_ptr, UINT *status_ptr);
```
### <a name="description"></a><span data-ttu-id="499bf-479">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-479">Description</span></span>

<span data-ttu-id="499bf-480">このサービスは、指定された PPP インスタンスの現在の状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="499bf-480">This service gets the current status of the specified PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-481">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-481">Input Parameters</span></span>

- <span data-ttu-id="499bf-482">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-482">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-483">**status_ptr**: PPP の状態の参照先。使用可能な状態値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="499bf-483">**status_ptr**: Destination for the PPP status, the following are possible status values:</span></span>
    - <span data-ttu-id="499bf-484">**NX_PPP_STATUS_ESTABLISHED**</span><span class="sxs-lookup"><span data-stu-id="499bf-484">**NX_PPP_STATUS_ESTABLISHED**</span></span>
    - <span data-ttu-id="499bf-485">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="499bf-485">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="499bf-486">**NX_PPP_STATUS_LCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="499bf-486">**NX_PPP_STATUS_LCP_FAILED**</span></span>
    - <span data-ttu-id="499bf-487">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="499bf-487">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="499bf-488">**NX_PPP_STATUS_PAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="499bf-488">**NX_PPP_STATUS_PAP_FAILED**</span></span>
    - <span data-ttu-id="499bf-489">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="499bf-489">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="499bf-490">**NX_PPP_STATUS_CHAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="499bf-490">**NX_PPP_STATUS_CHAP_FAILED**</span></span>
    - <span data-ttu-id="499bf-491">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="499bf-491">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="499bf-492">**NX_PPP_STATUS_IPCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="499bf-492">**NX_PPP_STATUS_IPCP_FAILED**</span></span>

>[!NOTE]
> <span data-ttu-id="499bf-493">状態は、API から NX_SUCCESS が返された場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-493">The status is only valid if the API returns NX_SUCCESS.</span></span> <span data-ttu-id="499bf-494">さらに、\*_FAILED 状態値のいずれかが返された場合、PPP の処理は、アプリケーションによってもう一度再開されるまで実質的に停止されます。</span><span class="sxs-lookup"><span data-stu-id="499bf-494">In addition, if any of the \*_FAILED status values are returned, PPP processing is effectively stopped until it is restarted again by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-495">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-495">Return Values</span></span>

- <span data-ttu-id="499bf-496">**NX_SUCCESS**: (0x00) PPP 状態要求が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-496">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="499bf-497">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-497">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-498">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-498">Allowed From</span></span>

<span data-ttu-id="499bf-499">初期化、スレッド、タイマー、ISR</span><span class="sxs-lookup"><span data-stu-id="499bf-499">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="499bf-500">例</span><span class="sxs-lookup"><span data-stu-id="499bf-500">Example</span></span>

```c
UINT ppp_status;
UINT status;


/* Get the current status of PPP instance “my_ppp”.  */
status =  nx_ppp_status_get(&my_ppp, &ppp_status);

/* If status is NX_SUCCESS the current internal PPP status is contained in
   “ppp_status”. */
```
## <a name="nx_ppp_stop"></a><span data-ttu-id="499bf-501">nx_ppp_stop</span><span class="sxs-lookup"><span data-stu-id="499bf-501">nx_ppp_stop</span></span>

<span data-ttu-id="499bf-502">PPP の処理を停止する</span><span class="sxs-lookup"><span data-stu-id="499bf-502">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-503">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-503">Prototype</span></span>

```c
UINT  nx_ppp_stop(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="499bf-504">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-504">Description</span></span>

<span data-ttu-id="499bf-505">このサービスは PPP の処理を停止します。</span><span class="sxs-lookup"><span data-stu-id="499bf-505">This service stops the PPP processing.</span></span> <span data-ttu-id="499bf-506">ユーザーは、必要に応じて nx_ppp_start() を呼び出して、PPP の処理を開始することもできます。</span><span class="sxs-lookup"><span data-stu-id="499bf-506">User also can calls nx_ppp_start() to start the PPP processing if needed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-507">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-507">Input Parameters</span></span>

- <span data-ttu-id="499bf-508">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-508">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-509">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-509">Return Values</span></span>

- <span data-ttu-id="499bf-510">**NX_SUCCESS**: (0x00) PPP が正常に停止されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-510">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="499bf-511">**NX_PPP_ALREADY_STOPPED**: (0xb8) PPP は既に停止しています。</span><span class="sxs-lookup"><span data-stu-id="499bf-511">**NX_PPP_ALREADY_STOPPED**: (0xb8) PPP already stopped.</span></span>
- <span data-ttu-id="499bf-512">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-512">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="499bf-513">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-513">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-514">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-514">Allowed From</span></span>

<span data-ttu-id="499bf-515">Threads</span><span class="sxs-lookup"><span data-stu-id="499bf-515">Threads</span></span>

### <a name="example"></a><span data-ttu-id="499bf-516">例</span><span class="sxs-lookup"><span data-stu-id="499bf-516">Example</span></span>

```c
/* Stop the PPP instance “my_ppp”.  */
status =  nx_ppp_stop(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been stopped. */
```
## <a name="nx_ppp_packet_receive"></a><span data-ttu-id="499bf-517">nx_ppp_packet_receive</span><span class="sxs-lookup"><span data-stu-id="499bf-517">nx_ppp_packet_receive</span></span>

<span data-ttu-id="499bf-518">PPP パケットを受信する</span><span class="sxs-lookup"><span data-stu-id="499bf-518">Receive PPP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-519">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-519">Prototype</span></span>

```c
UINT  nx_ppp_packet_receive(NX_PPP *ppp_ptr, NX_PACKET *packet_ptr);

```

### <a name="description"></a><span data-ttu-id="499bf-520">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-520">Description</span></span>

<span data-ttu-id="499bf-521">このサービスは PPP パケットを受信します。</span><span class="sxs-lookup"><span data-stu-id="499bf-521">This service receives PPP packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-522">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-522">Input Parameters</span></span>

- <span data-ttu-id="499bf-523">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-523">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-524">**packet_ptr**: PPP パケットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-524">**packet_ptr**: Pointer to PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-525">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-525">Return Values</span></span>

- <span data-ttu-id="499bf-526">**NX_SUCCESS**: (0x00) PPP 状態要求が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-526">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="499bf-527">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-527">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-528">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-528">Allowed From</span></span>

<span data-ttu-id="499bf-529">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="499bf-529">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="499bf-530">例</span><span class="sxs-lookup"><span data-stu-id="499bf-530">Example</span></span>

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a><span data-ttu-id="499bf-531">nx_ppp_packet_send_set</span><span class="sxs-lookup"><span data-stu-id="499bf-531">nx_ppp_packet_send_set</span></span>

<span data-ttu-id="499bf-532">PPP パケット送信関数を設定する</span><span class="sxs-lookup"><span data-stu-id="499bf-532">Set the PPP packet send function</span></span>

### <a name="prototype"></a><span data-ttu-id="499bf-533">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="499bf-533">Prototype</span></span>

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a><span data-ttu-id="499bf-534">説明</span><span class="sxs-lookup"><span data-stu-id="499bf-534">Description</span></span>

<span data-ttu-id="499bf-535">このサービスは、PPP パケット送信関数を設定します。</span><span class="sxs-lookup"><span data-stu-id="499bf-535">This service sets the PPP packet send funciton.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="499bf-536">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="499bf-536">Input Parameters</span></span>

- <span data-ttu-id="499bf-537">**ppp_ptr**: PPP 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="499bf-537">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="499bf-538">**nx_ppp_packet_send**: PPP パケットを送信するルーチン。</span><span class="sxs-lookup"><span data-stu-id="499bf-538">**nx_ppp_packet_send**: Routine to send PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="499bf-539">戻り値</span><span class="sxs-lookup"><span data-stu-id="499bf-539">Return Values</span></span>

- <span data-ttu-id="499bf-540">**NX_SUCCESS**: (0x00) PPP 状態要求が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="499bf-540">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="499bf-541">NX_PTR_ERROR: (0x07) PPP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="499bf-541">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="499bf-542">許可元</span><span class="sxs-lookup"><span data-stu-id="499bf-542">Allowed From</span></span>

<span data-ttu-id="499bf-543">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="499bf-543">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="499bf-544">例</span><span class="sxs-lookup"><span data-stu-id="499bf-544">Example</span></span>

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```