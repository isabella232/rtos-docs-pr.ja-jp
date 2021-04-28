---
title: 付録 A - 状態の復元機能の説明
description: Azure RTOS NetX の DHDP クライアント構成オプションである NX_DHCP_CLIENT_RESTORE_STATE を使用すると、システムの再起動の間に、以前に作成された DHCP クライアント レコードを Bound 状態で復元できます。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be8b5dc4885951bee3dba38af6fe5e21b81aa767
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811624"
---
# <a name="appendix-a---description-of-the-restore-state-feature"></a><span data-ttu-id="df029-103">付録 A - 状態の復元機能の説明</span><span class="sxs-lookup"><span data-stu-id="df029-103">Appendix A - Description of the Restore State Feature</span></span>

<span data-ttu-id="df029-104">Azure RTOS NetX の DHDP クライアント構成オプションである NX_DHCP_CLIENT_RESTORE_STATE を使用すると、システムの再起動の間に、以前に作成された DHCP クライアント レコードを Bound 状態で復元できます。</span><span class="sxs-lookup"><span data-stu-id="df029-104">The Azure RTOS NetX DHDP Client configuration option, NX_DHCP_CLIENT_RESTORE_STATE, allows a system to restore a previously created DHCP Client Record in a Bound state between system reboots.</span></span>

<span data-ttu-id="df029-105">このオプションを有効にすると、アプリケーションでは DHCP クライアントのスレッドを中断および再開できます。</span><span class="sxs-lookup"><span data-stu-id="df029-105">When this option is enabled, the application can suspend and resume the DHCP Client thread.</span></span> <span data-ttu-id="df029-106">また、スレッドを中断して再開するまでの経過時間に DHCP クライアントを更新するサービスもあります。</span><span class="sxs-lookup"><span data-stu-id="df029-106">There is also a service to update the DHCP Client with the elapsed time between suspending and resuming the thread.</span></span>

## <a name="restoring-the-dhcp-client-between-reboots"></a><span data-ttu-id="df029-107">再起動の間に DHCP クライアントを復元する</span><span class="sxs-lookup"><span data-stu-id="df029-107">Restoring the DHCP Client between Reboots</span></span>

<span data-ttu-id="df029-108">再起動後に DHCP クライアントを復元する前に、以前に作成された DHCP クライアントが、バインドされた状態になり、DHCP サーバーから IP アドレスが割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="df029-108">Before restoring a DHCP Client after rebooting, a previously created DHCP Client that must reach the Bound state and be is assigned an IP address from the DHCP server.</span></span> <span data-ttu-id="df029-109">電源を切る前に、DHCP アプリケーションで現在の DHCP クライアント レコードを不揮発性メモリに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df029-109">Before it powers down, the DHCP application must then save the current DHCP Client record to non-volatile memory.</span></span> <span data-ttu-id="df029-110">また、電源がオフの状態で経過した時間を追跡するために、独立した "タイム キーパー" がシステムの他の場所に必要になります。</span><span class="sxs-lookup"><span data-stu-id="df029-110">There must also be an independent ‘time keeper’ elsewhere in the system to keep track of the time elapsed during this powered down state.</span></span> <span data-ttu-id="df029-111">電源をオンにすると、アプリケーションでは、新しい DHCP クライアント インスタンスが作成され、以前に作成された DHCP クライアント レコードで更新されます。</span><span class="sxs-lookup"><span data-stu-id="df029-111">On powering up, the application creates a new DHCP Client instance, and then updates it with the previously created DHCP Client record.</span></span> <span data-ttu-id="df029-112">経過時間は、"タイム キーパー" から取得され、DHCP クライアントのリースの残りの時間に適用されます。</span><span class="sxs-lookup"><span data-stu-id="df029-112">The elapsed time is obtained from the “time keeper” and then applied to the time remaining on the DHCP Client lease.</span></span> <span data-ttu-id="df029-113">これにより、DHCP クライアントの状態が変更される可能性があることに注意してください (たとえば、バインドから更新に)。</span><span class="sxs-lookup"><span data-stu-id="df029-113">Note that this may cause the DHCP Client to change states e.g. from BOUND to RENEWING.</span></span> <span data-ttu-id="df029-114">この時点で、アプリケーションでは DHCP クライアントを再開できます。</span><span class="sxs-lookup"><span data-stu-id="df029-114">At this point, the application can resume the DHCP Client.</span></span>

<span data-ttu-id="df029-115">電源が切れている間に経過した時間によって DHCP クライアントの状態が更新または再バインドの状態になると、DHCP クライアントでは IP アドレスのリースの更新または再バインドを要求する DHCP メッセージが自動的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="df029-115">If the time elapsed during power down puts the DHCP Client state in either a RENEW or REBIND state, the DHCP Client will automatically initiate DHCP messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="df029-116">IP アドレスの有効期限が切れている場合、DHCP クライアントでは IP インスタンスの IP アドレスが自動的にクリアされ、新しい IP アドレスを要求する INIT 状態から DHCP プロセスが開始されます。</span><span class="sxs-lookup"><span data-stu-id="df029-116">If the IP address is expired, the DHCP Client will automatically clear the IP address on the IP instance and begin the DHCP process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="df029-117">この方法では、DHCP クライアントが、再起動間に中断されていないかのように動作することができます。</span><span class="sxs-lookup"><span data-stu-id="df029-117">In this manner the DHCP Client can operate between reboots as if uninterrupted.</span></span>

<span data-ttu-id="df029-118">この機能を下に示します。</span><span class="sxs-lookup"><span data-stu-id="df029-118">Below is an illustration of this feature.</span></span> <span data-ttu-id="df029-119">これは、DHCP クライアントがプライマリ インターフェイスでのみ実行されていることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="df029-119">This assumes DHCP Client is running only on the primary interface.</span></span>

```C
/* On the power up, create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) for the DHCP Client/application
   in tx_application_define(). */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCP_CLIENT_RECORD client_nv_record;


if (/* The application checks if there is a previously saved DHCP Client record. */)
{


  /* No previously saved Client record. Start the DHCP Client in the INIT state. */
  status =  nx_dhcp_start(&dhcp_0);

  if (status !=NX_SUCCESS)
    return;

  do
  {
  
    /* Wait for DHCP to assign the IP address. */
  } while (status != NX_SUCCESS);

  /* We have a valid IP address. */

  /* At some point decide we power down the system. */

  /* Save the Client state data which we will subsequently need to restore the DHCP  
     Client. */
  status = nx_dhcp_client_get_record(&dhcp_0, &client_nv_record);         

  /* Copy this memory to non-volatile memory (not shown). */

  /* Delete the IP and DHCP Client instances before powering down. */
  nx_dhcp_delete(&dhcp_0);

  nx_ip_delete(&ip_0);

  /* Ready to power down, having released other resources as necessary. */

}
else
{

  /* The application has determined there is a previously saved record. We will 
     restore it to the current DHCP Client instance. */

  /* Get the previous Client state data from non-volatile memory. */

  /* Apply the record to the current Client instance. This will also 
     update the IP instance with IP address, mask etc. */
  status = nx_dhcp_client_restore_record(&dhcp_0, &client_nv_record, time_elapsed);   

     if (status != NX_SUCCESS)
      return;

     /* We are ready to resume the DHCP Client thread and use the assigned IP address. */
     status = nx_dhcp_resume(&dhcp_0);

     if (status != NX_SUCCESS)
      return;

}
```

## <a name="resuming-the-dhcp-client-thread-after-suspension"></a><span data-ttu-id="df029-120">中断後に DHCP クライアントのスレッドを再開する</span><span class="sxs-lookup"><span data-stu-id="df029-120">Resuming the DHCP Client Thread after Suspension</span></span> 

<span data-ttu-id="df029-121">電源を切ることなく DHCP クライアントのスレッドを中断するには、バインドされた状態になり、有効な IP アドレスを持つ DHCP クライアントに対し、アプリケーションで *nx_dhcp_suspend* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="df029-121">To suspend a DHCP Client thread without powering down, the application calls *nx_dhcp_suspend* on a DHCP Client which has achieved the BOUND state and which has a valid IP address.</span></span> <span data-ttu-id="df029-122">DHCP クライアントを再開する準備ができたら、まず *nx_dhcp_client_update_time_remaining* を呼び出して、DHCP アドレスのリースの残り時間を更新します (独立したタイム キーパーから経過時間を取得します)。</span><span class="sxs-lookup"><span data-stu-id="df029-122">When it is ready to resume the DHCP Client it first calls *nx_dhcp_client_update_time_remaining* to update the time remaining on the DHCP address lease (obtaining the time elapsed from an independent time keeper).</span></span> <span data-ttu-id="df029-123">次に、*nx_dhcp_resume* を呼び出して、DHCP クライアントのスレッドを再開します。</span><span class="sxs-lookup"><span data-stu-id="df029-123">Then it calls the *nx_dhcp_resume* to resume the DHCP Client thread.</span></span>

<span data-ttu-id="df029-124">経過時間によって DHCP クライアントの状態が更新または再バインドの状態になると、DHCP クライアントでは IP アドレスのリースの更新または再バインドを要求する DHCP メッセージが自動的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="df029-124">If the time elapsed puts the DHCP Client state in either a RENEW or REBIND state, the DHCP Client will automatically initiate DHCP messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="df029-125">IP アドレスの有効期限が切れている場合、DHCP クライアントでは IP アドレスが自動的にクリアされ、新しい IP アドレスを要求する初期化状態から DHCP プロセスが開始されます。</span><span class="sxs-lookup"><span data-stu-id="df029-125">If the IP address is expired, the DHCP Client will automatically clear the IP address and begin the DHCP process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="df029-126">この機能の使用方法を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="df029-126">Below is an illustration of using this feature.</span></span>

```C
/* Create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) typically in tx_application_define(). */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

  /* Start the DHCP Client. */
  status =  nx_dhcp_start(&dhcp_0);

  if (status !=NX_SUCCESS)
    return;

  while(1)
  {
   
    /* Wait for DHCP to obtain an IP address. */
  }

  /* Do tasks with the IP address e.g. send pings to another host on the 
     network... */
  status =  nx_icmp_ping(…);

  if (status !=NX_SUCCESS)
          printf("Failed %d byte Ping!\n", length);

  /* At some later time, suspend the DHCP Client e.g. the device is going to low 
   power mode (sleep) so we do not want any threads to wake it up. */

  nx_dhcp_suspend(&dhcp_0);  

  /* During this suspended state, an independent timer is keeping track of the
     elapsed time. */


  /* At some point, we are ready to resume the DHCP Client thread. */

  /* Update the DHCP Client lease time remaining with the time elapsed. */
  status = nx_dhcp_client_update_time_remaining(&dhcp_0, time_elapsed);   

  if (status != NX_SUCCESS)
       return;

  /* We now can resume the DHCP Client thread. */
  status = nx_dhcp_resume(&dhcp_0);

  if (status != NX_SUCCESS)
       return;

  /* Resume tasks e.g. ping another host. */
  status =  nx_icmp_ping(…);

}
```

<span data-ttu-id="df029-127">DHCP クライアントの状態をメモリから復元したり、DHCP クライアントを中断および再開したりするためのサービスを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="df029-127">Below is a list of services for restoring a DHCP Client state from memory and for suspending and resuming the DHCP Client.</span></span>

## <a name="nx_dhcp_client_get_record"></a><span data-ttu-id="df029-128">nx_dhcp_client_get_record</span><span class="sxs-lookup"><span data-stu-id="df029-128">nx_dhcp_client_get_record</span></span>

<span data-ttu-id="df029-129">現在の DHCP クライアントの状態のレコードを作成する</span><span class="sxs-lookup"><span data-stu-id="df029-129">Create a record of the current DHCP Client state</span></span>

### <a name="prototype"></a><span data-ttu-id="df029-130">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="df029-130">Prototype</span></span>

```C
ULONG nx_dhcp_ client_get_record(NX_DHCP *dhcp_ptr, 
                                 NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="df029-131">説明</span><span class="sxs-lookup"><span data-stu-id="df029-131">Description</span></span>

<span data-ttu-id="df029-132">このサービスでは、DHCP クライアント インスタンスで検出された DHCP に対して有効になっている最初のインターフェイスで実行されている DHCP クライアントが、record_ptr で指すレコードに保存されます。</span><span class="sxs-lookup"><span data-stu-id="df029-132">This service saves the DHCP Client running on the first interface enabled for DHCP found on the DHCP Client instance to the record pointed to by record_ptr.</span></span> <span data-ttu-id="df029-133">これにより、DHCP クライアント アプリケーションでは、電源の切断、再起動などの後に、DHCP クライアントの状態を復元できます。</span><span class="sxs-lookup"><span data-stu-id="df029-133">This allows the DHCP Client application restore its DHCP Client state after, for example, a power down and reboot.</span></span>

<span data-ttu-id="df029-134">DHCP に対して複数のインターフェイスが有効になっている場合に、特定のインターフェイスの DHCP クライアント レコードを保存するには、*nx_dhcp_interface_client_get_record* サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="df029-134">To save a DHCP Client record on a specific interface if more than one interface is enabled for DHCP, use the *nx_dhcp_interface_client_get_record* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df029-135">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="df029-135">Input Parameters</span></span>

- <span data-ttu-id="df029-136">**dhcp_ptr** DHCP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="df029-136">**dhcp_ptr** Pointer to DHCP Client</span></span>

- <span data-ttu-id="df029-137">**record_ptr** DHCP クライアント レコードへのポインター</span><span class="sxs-lookup"><span data-stu-id="df029-137">**record_ptr** Pointer to DHCP Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="df029-138">戻り値</span><span class="sxs-lookup"><span data-stu-id="df029-138">Return Values</span></span>

- <span data-ttu-id="df029-139">**NX_SUCCESS** (0x0) クライアント レコードが作成されました</span><span class="sxs-lookup"><span data-stu-id="df029-139">**NX_SUCCESS** (0x0) Client record created</span></span>

- <span data-ttu-id="df029-140">**NX_DHCP_NOT_BOUND** (0x94) クライアントが Bound 状態ではありません</span><span class="sxs-lookup"><span data-stu-id="df029-140">**NX_DHCP_NOT_BOUND** (0x94) Client not in Bound state</span></span>

- <span data-ttu-id="df029-141">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) DHCP が有効になっているインターフェイスがありません</span><span class="sxs-lookup"><span data-stu-id="df029-141">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="df029-142">**NX_PTR_ERROR** (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="df029-142">**NX_PTR_ERROR** (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df029-143">許可元</span><span class="sxs-lookup"><span data-stu-id="df029-143">Allowed From</span></span>

<span data-ttu-id="df029-144">Threads</span><span class="sxs-lookup"><span data-stu-id="df029-144">Threads</span></span>

### <a name="example"></a><span data-ttu-id="df029-145">例</span><span class="sxs-lookup"><span data-stu-id="df029-145">Example</span></span>

```C
NX_DHCP_CLIENT_RECORD dhcp_record;


/* Obtain a record of the current client state. */
status=  nx_dhcp_client_get_record(dhcp_ptr, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_interface_client_get_record"></a><span data-ttu-id="df029-146">nx_dhcp_interface_client_get_record</span><span class="sxs-lookup"><span data-stu-id="df029-146">nx_dhcp_interface_client_get_record</span></span>

<span data-ttu-id="df029-147">指定したインターフェイスにおける現在の DHCP クライアントの状態のレコードを作成する</span><span class="sxs-lookup"><span data-stu-id="df029-147">Create a record of the current DHCP Client state on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="df029-148">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="df029-148">Prototype</span></span>

```C
ULONG nx_dhcp_interface_client_get_record(NX_DHCP *dhcp_ptr, 
                                 UINT interface_index,
                                 NX_DHCP_CLIENT_RECORD *record_ptr);
```
### <a name="description"></a><span data-ttu-id="df029-149">説明</span><span class="sxs-lookup"><span data-stu-id="df029-149">Description</span></span>

<span data-ttu-id="df029-150">このサービスでは、指定されたインターフェイスで実行されている DHCP クライアントが record_ptr が指すレコードに保存されます。</span><span class="sxs-lookup"><span data-stu-id="df029-150">This service saves the DHCP Client running on the specified interface to the record pointed to by record_ptr.</span></span> <span data-ttu-id="df029-151">これにより、DHCP クライアント アプリケーションでは、電源の切断、再起動などの後に、DHCP クライアントの状態を復元できます。</span><span class="sxs-lookup"><span data-stu-id="df029-151">This allows the DHCP Client application restore its DHCP Client state after, for example, a power down and reboot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df029-152">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="df029-152">Input Parameters</span></span>

- <span data-ttu-id="df029-153">**dhcp_ptr** DHCP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="df029-153">**dhcp_ptr** Pointer to DHCP Client</span></span>

- <span data-ttu-id="df029-154">**interface_index** レコードを取得するインデックス</span><span class="sxs-lookup"><span data-stu-id="df029-154">**interface_index** Index on which to get record</span></span>

- <span data-ttu-id="df029-155">**record_ptr** DHCP クライアント レコードへのポインター</span><span class="sxs-lookup"><span data-stu-id="df029-155">**record_ptr** Pointer to DHCP Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="df029-156">戻り値</span><span class="sxs-lookup"><span data-stu-id="df029-156">Return Values</span></span>

- <span data-ttu-id="df029-157">**NX_SUCCESS** (0x0) クライアント レコードが作成されました</span><span class="sxs-lookup"><span data-stu-id="df029-157">**NX_SUCCESS** (0x0) Client record created</span></span>

- <span data-ttu-id="df029-158">**NX_DHCP_NOT_BOUND** (0x94) クライアントが Bound 状態ではありません</span><span class="sxs-lookup"><span data-stu-id="df029-158">**NX_DHCP_NOT_BOUND** (0x94) Client not in Bound state</span></span>

- <span data-ttu-id="df029-159">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A) インターフェイスのインデックスが無効です</span><span class="sxs-lookup"><span data-stu-id="df029-159">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A) Invalid interface index</span></span>

- <span data-ttu-id="df029-160">NX_PTR_ERROR (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="df029-160">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="df029-161">NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="df029-161">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df029-162">許可元</span><span class="sxs-lookup"><span data-stu-id="df029-162">Allowed From</span></span>

<span data-ttu-id="df029-163">Threads</span><span class="sxs-lookup"><span data-stu-id="df029-163">Threads</span></span>

### <a name="example"></a><span data-ttu-id="df029-164">例</span><span class="sxs-lookup"><span data-stu-id="df029-164">Example</span></span>

```C
NX_DHCP_CLIENT_RECORD dhcp_record;


/* Obtain a record of the current client state on interface 1. */
status=  nx_dhcp_interface_client_get_record(dhcp_ptr, 1, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_-client_restore_record"></a><span data-ttu-id="df029-165">nx_dhcp_ client_restore_record</span><span class="sxs-lookup"><span data-stu-id="df029-165">nx_dhcp_ client_restore_record</span></span>

<span data-ttu-id="df029-166">以前に保存したレコードから DHCP クライアントを復元する</span><span class="sxs-lookup"><span data-stu-id="df029-166">Restore DHCP Client from a previously saved record</span></span>

### <a name="prototype"></a><span data-ttu-id="df029-167">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="df029-167">Prototype</span></span>

```C
ULONG nx_dhcp_client_restore_record(NX_DHCP *dhcp_ptr, 
                                    NX_DHCP_CLIENT_RECORD       
                                    *record_ptr, ULONG time_elapsed);
```
### <a name="description"></a><span data-ttu-id="df029-168">説明</span><span class="sxs-lookup"><span data-stu-id="df029-168">Description</span></span>

<span data-ttu-id="df029-169">このサービスを使用すると、アプリケーションでは、record_ptr が指す DHCP クライアント レコードを使用して、以前のセッションから DHCP クライアントを復元できます。</span><span class="sxs-lookup"><span data-stu-id="df029-169">This service enables an application to restore its DHCP Client from a previous session using the DHCP Client record pointed to by record_ptr.</span></span> <span data-ttu-id="df029-170">time_elapsed の入力は、DHCP クライアントのリースの残りの期間に適用されます。</span><span class="sxs-lookup"><span data-stu-id="df029-170">The time_elapsed input is applied to the time remaining on DHCP Client lease.</span></span>

<span data-ttu-id="df029-171">これを行うには、DHCP クライアント アプリケーションで、電源を切る前に DHCP クライアントのレコードを作成し、そのレコードを不揮発性メモリに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df029-171">This requires that the DHCP Client application created a record of the DHCP Client before powering down, and saved that record to nonvolatile memory.</span></span>

<span data-ttu-id="df029-172">DHCP クライアントに対して複数のインターフェイスが有効になっている場合、このサービスは DHCP クライアント インスタンスで検出された最初の有効なインターフェイスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="df029-172">If more than one interface is enabled for DHCP Client, this service is applied to the first valid interface found in the DHCP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df029-173">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="df029-173">Input Parameters</span></span>

- <span data-ttu-id="df029-174">**dhcp_ptr** DHCP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="df029-174">**dhcp_ptr** Pointer to DHCP Client</span></span>

- <span data-ttu-id="df029-175">**record_ptr** DHCP クライアント レコードへのポインター</span><span class="sxs-lookup"><span data-stu-id="df029-175">**record_ptr** Pointer to DHCP Client record</span></span>

- <span data-ttu-id="df029-176">**time_elapsed** 入力クライアント レコードの残りのリース期間から減算する時間</span><span class="sxs-lookup"><span data-stu-id="df029-176">**time_elapsed** Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="df029-177">戻り値</span><span class="sxs-lookup"><span data-stu-id="df029-177">Return Values</span></span>

- <span data-ttu-id="df029-178">**NX_SUCCESS** (0x0) クライアント レコードが復元されました</span><span class="sxs-lookup"><span data-stu-id="df029-178">**NX_SUCCESS** (0x0) Client record restored</span></span>

- <span data-ttu-id="df029-179">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) DHCP が実行されているインターフェイスがありません</span><span class="sxs-lookup"><span data-stu-id="df029-179">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces running DHCP</span></span>

- <span data-ttu-id="df029-180">**NX_PTR_ERROR** (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="df029-180">**NX_PTR_ERROR** (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df029-181">許可元</span><span class="sxs-lookup"><span data-stu-id="df029-181">Allowed From</span></span>

<span data-ttu-id="df029-182">Threads</span><span class="sxs-lookup"><span data-stu-id="df029-182">Threads</span></span>

### <a name="example"></a><span data-ttu-id="df029-183">例</span><span class="sxs-lookup"><span data-stu-id="df029-183">Example</span></span>
```C
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state. */
status=  nx_dhcp_client_restore_record(client_ptr, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr
   contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_interace_client_restore_record"></a><span data-ttu-id="df029-184">nx_dhcp_interace_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="df029-184">nx_dhcp_interace_client_restore_record</span></span>

<span data-ttu-id="df029-185">以前に保存したレコードから指定したインターフェイスに DHCP クライアントを復元する</span><span class="sxs-lookup"><span data-stu-id="df029-185">Restore DHCP Client from a previously saved record on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="df029-186">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="df029-186">Prototype</span></span>

```C
ULONG nx_dhcp_interface_client_restore_record(NX_DHCP *dhcp_ptr, 
                                              NX_DHCP_CLIENT_RECORD       
                                              *record_ptr, ULONG time_elapsed);
```
### <a name="description"></a><span data-ttu-id="df029-187">説明</span><span class="sxs-lookup"><span data-stu-id="df029-187">Description</span></span>

<span data-ttu-id="df029-188">このサービスを使用すると、アプリケーションでは、record_ptr が指す DHCP クライアント レコードを使用して、指定したインターフェイスに DHCP クライアントを復元できます。</span><span class="sxs-lookup"><span data-stu-id="df029-188">This service enables an application to restore its DHCP Client on the specified interface using the DHCP Client record pointed to by record_ptr.</span></span> <span data-ttu-id="df029-189">time_elapsed の入力は、DHCP クライアントのリースの残りの期間に適用されます。</span><span class="sxs-lookup"><span data-stu-id="df029-189">The time_elapsed input is applied to the time remaining on DHCP Client lease.</span></span>

<span data-ttu-id="df029-190">これを行うには、DHCP クライアント アプリケーションで、電源を切る前に DHCP クライアントのレコードを作成し、そのレコードを不揮発性メモリに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df029-190">This requires that the DHCP Client application created a record of the DHCP Client before powering down, and saved that record to nonvolatile memory.</span></span>

<span data-ttu-id="df029-191">DHCP クライアントに対して複数のインターフェイスが有効になっている場合、このサービスは DHCP クライアント インスタンスで検出された最初の有効なインターフェイスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="df029-191">If more than one interface is enabled for DHCP Client, this service is applied to the first valid interface found in the DHCP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df029-192">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="df029-192">Input Parameters</span></span>

- <span data-ttu-id="df029-193">**dhcp_ptr** DHCP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="df029-193">**dhcp_ptr** Pointer to DHCP Client</span></span>

- <span data-ttu-id="df029-194">**record_ptr** DHCP クライアント レコードへのポインター</span><span class="sxs-lookup"><span data-stu-id="df029-194">**record_ptr** Pointer to DHCP Client record</span></span>

- <span data-ttu-id="df029-195">**time_elapsed** 入力クライアント レコードの残りのリース期間から減算する時間</span><span class="sxs-lookup"><span data-stu-id="df029-195">**time_elapsed** Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="df029-196">戻り値</span><span class="sxs-lookup"><span data-stu-id="df029-196">Return Values</span></span>

- <span data-ttu-id="df029-197">**NX_SUCCESS** (0x0) クライアント レコードが復元されました</span><span class="sxs-lookup"><span data-stu-id="df029-197">**NX_SUCCESS** (0x0) Client record restored</span></span>

- <span data-ttu-id="df029-198">**NX_DHCP_NOT_BOUND** (0x94) クライアントが IP アドレスにバインドされていません</span><span class="sxs-lookup"><span data-stu-id="df029-198">**NX_DHCP_NOT_BOUND** (0x94) Client not bound to IP address</span></span>

- <span data-ttu-id="df029-199">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A) インターフェイスのインデックスが無効です</span><span class="sxs-lookup"><span data-stu-id="df029-199">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A) Invalid interface index</span></span>

- <span data-ttu-id="df029-200">NX_PTR_ERROR (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="df029-200">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="df029-201">NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="df029-201">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df029-202">許可元</span><span class="sxs-lookup"><span data-stu-id="df029-202">Allowed From</span></span>

<span data-ttu-id="df029-203">Threads</span><span class="sxs-lookup"><span data-stu-id="df029-203">Threads</span></span>

### <a name="example"></a><span data-ttu-id="df029-204">例</span><span class="sxs-lookup"><span data-stu-id="df029-204">Example</span></span>

```C
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state on the primary interface. */
status=  nx_dhcp_interface_client_restore_record(client_ptr, 0, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  
   contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_-client_update_time_remaining"></a><span data-ttu-id="df029-205">nx_dhcp_ client_update_time_remaining</span><span class="sxs-lookup"><span data-stu-id="df029-205">nx_dhcp_ client_update_time_remaining</span></span>

<span data-ttu-id="df029-206">DHCP クライアントのリースの残り時間を更新する</span><span class="sxs-lookup"><span data-stu-id="df029-206">Update the time remaining on DHCP Client lease</span></span>

### <a name="prototype"></a><span data-ttu-id="df029-207">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="df029-207">Prototype</span></span>

```C
ULONG nx_dhcp_client_update_time_remaining(NX_DHCP *dhcp_ptr
                                           ULONG time_elapsed);
```
### <a name="description"></a><span data-ttu-id="df029-208">説明</span><span class="sxs-lookup"><span data-stu-id="df029-208">Description</span></span>

<span data-ttu-id="df029-209">このサービスでは、DHCP クライアントの IP アドレスのリースの残り時間が、DHCP クライアント インスタンスで検出された DHCP に対して有効になっている最初のインターフェイスの time_elapsed の入力を使用して更新されます。</span><span class="sxs-lookup"><span data-stu-id="df029-209">This service updates the time remaining on the DHCP Client IP address lease with the time_elapsed input on the first interface enabled for DHCP found on the DHCP Client instance.</span></span> <span data-ttu-id="df029-210">アプリケーションでは、*nx_dhcp_suspend* を使用してこのサービスを使用する前に、DHCP クライアントのスレッドを中断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df029-210">The application must suspend the DHCP Client thread before using this service using *nx_dhcp_suspend*.</span></span> <span data-ttu-id="df029-211">このサービスを呼び出した後、アプリケーションでは *nx_dhcp_resume* を呼び出すことによって DHCP クライアントのスレッドを再開できます。</span><span class="sxs-lookup"><span data-stu-id="df029-211">After calling this service, the application can resume the DHCP Client thread by calling *nx_dhcp_resume*.</span></span>

<span data-ttu-id="df029-212">これは、DHCP クライアントのスレッドを一定期間中断してから、IP アドレスの残りのリース期間を更新する必要がある DHCP クライアント アプリケーションを対象としています。</span><span class="sxs-lookup"><span data-stu-id="df029-212">This is intended for DHCP Client applications that need to suspend the DHCP Client thread for a period of time, and then update the IP address lease time remaining.</span></span>

> [!NOTE]
> <span data-ttu-id="df029-213">このサービスは、前に説明した *nx_dhcp_client_get_record* および *nx_dhcp_client_restore_record* と使用することは意図されていません。</span><span class="sxs-lookup"><span data-stu-id="df029-213">This service is not intended to be used with *nx_dhcp_client_get_record* and *nx_dhcp_client_restore_record* described previously).</span></span> <span data-ttu-id="df029-214">これらのサービスについては、このセクションで既に説明しています。</span><span class="sxs-lookup"><span data-stu-id="df029-214">These services are previously described in this section.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df029-215">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="df029-215">Input Parameters</span></span>

- <span data-ttu-id="df029-216">**dhcp_ptr** DHCP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="df029-216">**dhcp_ptr** Pointer to DHCP Client</span></span>

- <span data-ttu-id="df029-217">**time_elapsed** IP アドレスのリースの残り時間から減算する時間</span><span class="sxs-lookup"><span data-stu-id="df029-217">**time_elapsed** Time to subtract from the time remaining on the IP address lease</span></span>

### <a name="return-values"></a><span data-ttu-id="df029-218">戻り値</span><span class="sxs-lookup"><span data-stu-id="df029-218">Return Values</span></span>

- <span data-ttu-id="df029-219">**NX_SUCCESS** (0x0) クライアントの IP のリースが更新されました</span><span class="sxs-lookup"><span data-stu-id="df029-219">**NX_SUCCESS** (0x0) Client IP lease updated</span></span>

- <span data-ttu-id="df029-220">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) DHCP が有効になっているインターフェイスがありません</span><span class="sxs-lookup"><span data-stu-id="df029-220">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="df029-221">**NX_PTR_ERROR** (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="df029-221">**NX_PTR_ERROR** (0x16) Invalid Pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df029-222">許可元</span><span class="sxs-lookup"><span data-stu-id="df029-222">Allowed From</span></span>

<span data-ttu-id="df029-223">Threads</span><span class="sxs-lookup"><span data-stu-id="df029-223">Threads</span></span>

### <a name="example"></a><span data-ttu-id="df029-224">例</span><span class="sxs-lookup"><span data-stu-id="df029-224">Example</span></span>

```C
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease. */
status=  nx_dhcp_client_update_time_remaining(client_ptr, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```


## <a name="nx_dhcp_interface_client_update_time_remaining"></a><span data-ttu-id="df029-225">nx_dhcp_interface_client_update_time_remaining</span><span class="sxs-lookup"><span data-stu-id="df029-225">nx_dhcp_interface_client_update_time_remaining</span></span>

<span data-ttu-id="df029-226">指定されたインターフェイスにおける DHCP クライアントのリースの残り時間を更新する</span><span class="sxs-lookup"><span data-stu-id="df029-226">Update the time remaining on DHCP Client lease on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="df029-227">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="df029-227">Prototype</span></span>

```C
ULONG nx_dhcp_interface_client_update_time_remaining(NX_DHCP *dhcp_ptr,
                                                     UINT interface_index,
                                                     ULONG time_elapsed);
```
### <a name="description"></a><span data-ttu-id="df029-228">説明</span><span class="sxs-lookup"><span data-stu-id="df029-228">Description</span></span>

<span data-ttu-id="df029-229">このサービスでは、DHCP クライアントの IP アドレスのリースの残り時間が、指定されたインターフェイスの time_elapsed の入力を使用して更新されます (そのインターフェイスが DHCP に対して有効になっている場合)。</span><span class="sxs-lookup"><span data-stu-id="df029-229">This service updates the time remaining on the DHCP Client IP address lease with the time_elapsed input on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="df029-230">アプリケーションでは、*nx_dhcp_suspend* を使用してこのサービスを使用する前に、DHCP クライアントのスレッドを中断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df029-230">The application must suspend the DHCP Client thread before using this service using *nx_dhcp_suspend*.</span></span> <span data-ttu-id="df029-231">このサービスを呼び出した後、アプリケーションでは *nx_dhcp_resume* を呼び出すことによって DHCP クライアントのスレッドを再開できます。</span><span class="sxs-lookup"><span data-stu-id="df029-231">After calling this service, the application can resume the DHCP Client thread by calling *nx_dhcp_resume*.</span></span> <span data-ttu-id="df029-232">DHCP クライアントのスレッドの中断と再開は、DHCP に対して有効になっているすべてのインターフェイスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="df029-232">Note suspending and resuming the DHCP Client thread applies to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="df029-233">これは、DHCP クライアントのスレッドを一定期間中断してから、IP アドレスの残りのリース期間を更新する必要がある DHCP クライアント アプリケーションを対象としています。</span><span class="sxs-lookup"><span data-stu-id="df029-233">This is intended for DHCP Client applications that need to suspend the DHCP Client thread for a period of time, and then update the IP address lease time remaining.</span></span>

> [!NOTE] 
> <span data-ttu-id="df029-234">このサービスは、前に説明した *nx_dhcp_client_get_record* および *nx_dhcp_client_restore_record* と使用することは意図されていません。</span><span class="sxs-lookup"><span data-stu-id="df029-234">This service is not intended to be used with *nx_dhcp_client_get_record* and *nx_dhcp_client_restore_record* described previously).</span></span> <span data-ttu-id="df029-235">これらのサービスについては、このセクションで既に説明しています。</span><span class="sxs-lookup"><span data-stu-id="df029-235">These services are previously described in this section.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df029-236">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="df029-236">Input Parameters</span></span>

- <span data-ttu-id="df029-237">**dhcp_ptr** DHCP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="df029-237">**dhcp_ptr** Pointer to DHCP Client</span></span>

- <span data-ttu-id="df029-238">**interface_index** 経過時間を適用するインターフェイスへのインデックス</span><span class="sxs-lookup"><span data-stu-id="df029-238">**interface_index** Index to interface to apply elapsed time to</span></span>

- <span data-ttu-id="df029-239">**time_elapsed** IP アドレスのリースの残り時間から減算する時間</span><span class="sxs-lookup"><span data-stu-id="df029-239">**time_elapsed** Time to subtract from the time remaining on the IP address lease</span></span>

### <a name="return-values"></a><span data-ttu-id="df029-240">戻り値</span><span class="sxs-lookup"><span data-stu-id="df029-240">Return Values</span></span>

- <span data-ttu-id="df029-241">**NX_SUCCESS** (0x0) クライアントの IP のリースが更新されました</span><span class="sxs-lookup"><span data-stu-id="df029-241">**NX_SUCCESS** (0x0) Client IP lease updated</span></span>

- <span data-ttu-id="df029-242">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A) インターフェイスのインデックスが無効です</span><span class="sxs-lookup"><span data-stu-id="df029-242">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A) Invalid interface index</span></span>

- <span data-ttu-id="df029-243">NX_PTR_ERROR (0x16) DHCP ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="df029-243">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="df029-244">NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です</span><span class="sxs-lookup"><span data-stu-id="df029-244">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df029-245">許可元</span><span class="sxs-lookup"><span data-stu-id="df029-245">Allowed From</span></span>

<span data-ttu-id="df029-246">Threads</span><span class="sxs-lookup"><span data-stu-id="df029-246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="df029-247">例</span><span class="sxs-lookup"><span data-stu-id="df029-247">Example</span></span>

```C
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease on interface 1. */
status=  nx_dhcp_interface_client_update_time_remaining(client_ptr, 1, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```


## <a name="nx_dhcp_suspend"></a><span data-ttu-id="df029-248">nx_dhcp_suspend</span><span class="sxs-lookup"><span data-stu-id="df029-248">nx_dhcp_suspend</span></span>

<span data-ttu-id="df029-249">DHCP クライアントのスレッドを中断する</span><span class="sxs-lookup"><span data-stu-id="df029-249">Suspend the DHCP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="df029-250">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="df029-250">Prototype</span></span>

```C
ULONG nx_dhcp_suspend(NX_DHCP *dhcp_ptr);
```
### <a name="description"></a><span data-ttu-id="df029-251">説明</span><span class="sxs-lookup"><span data-stu-id="df029-251">Description</span></span>

<span data-ttu-id="df029-252">このサービスでは、現在の DHCP クライアントのスレッドが中断されます。</span><span class="sxs-lookup"><span data-stu-id="df029-252">This service suspends the current DHCP Client thread.</span></span> <span data-ttu-id="df029-253">*nx_dhcp_stop* とは異なり、このサービスが呼び出されたときに DHCP クライアントの状態が変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="df029-253">Note that unlike *nx_dhcp_stop*, there is no change to the DHCP Client state when this service is called.</span></span>

<span data-ttu-id="df029-254">このサービスでは、DHCP が有効になっているすべてのインターフェイスで実行されている DHCP が中断されます。</span><span class="sxs-lookup"><span data-stu-id="df029-254">This service suspends DHCP running on all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="df029-255">DHCP クライアントが中断されていた間の経過時間で DHCP クライアントの状態を更新するには、前述の *nx_dhcp_client_update_time_remaining* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df029-255">To update the DHCP Client state with elapsed time while the DHCP Client is suspended, see the *nx_dhcp_client_update_time_remaining* described previously.</span></span> <span data-ttu-id="df029-256">中断された DHCP クライアントのスレッドを再開するには、アプリケーションで *nx_dhcp_resume* を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="df029-256">To resume a suspended DHCP Client thread, the application should call *nx_dhcp_resume*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df029-257">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="df029-257">Input Parameters</span></span>

- <span data-ttu-id="df029-258">**dhcp_ptr** DHCP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="df029-258">**dhcp_ptr** Pointer to DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="df029-259">戻り値</span><span class="sxs-lookup"><span data-stu-id="df029-259">Return Values</span></span>

- <span data-ttu-id="df029-260">**NX_SUCCESS** (0x0) クライアントのスレッドが中断されました</span><span class="sxs-lookup"><span data-stu-id="df029-260">**NX_SUCCESS** (0x0) Client thread is suspended</span></span>

- <span data-ttu-id="df029-261">**NX_PTR_ERROR** (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="df029-261">**NX_PTR_ERROR** (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df029-262">許可元</span><span class="sxs-lookup"><span data-stu-id="df029-262">Allowed From</span></span>

<span data-ttu-id="df029-263">Threads</span><span class="sxs-lookup"><span data-stu-id="df029-263">Threads</span></span>

### <a name="example"></a><span data-ttu-id="df029-264">例</span><span class="sxs-lookup"><span data-stu-id="df029-264">Example</span></span>

```C
/* Pause the DHCP client thread. */
status=  nx_dhcp_suspend(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is paused. */
```


## <a name="nx_dhcp_resume"></a><span data-ttu-id="df029-265">nx_dhcp_resume</span><span class="sxs-lookup"><span data-stu-id="df029-265">nx_dhcp_resume</span></span>

<span data-ttu-id="df029-266">中断された DHCP クライアントのスレッドを再開する</span><span class="sxs-lookup"><span data-stu-id="df029-266">Resume a suspended DHCP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="df029-267">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="df029-267">Prototype</span></span>

```C
ULONG nx_dhcp_resume(NX_DHCP *dhcp_ptr);
```
### <a name="description"></a><span data-ttu-id="df029-268">説明</span><span class="sxs-lookup"><span data-stu-id="df029-268">Description</span></span>

<span data-ttu-id="df029-269">このサービスでは、中断された DHCP クライアントのスレッドが再開されます。</span><span class="sxs-lookup"><span data-stu-id="df029-269">This service resumes a suspended DHCP Client thread.</span></span> <span data-ttu-id="df029-270">クライアントのスレッドが再開された後に、実際の DHCP クライアントの状態は変更されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="df029-270">Note that there is no change to the actual DHCP Client state after resuming the Client thread.</span></span> <span data-ttu-id="df029-271">*nx_dhcp_resume* を呼び出す前に DHCP クライアント の IP アドレスのリースの残り時間を経過時間で更新するには、前に説明した *nx_dhcp_client_update_time_remaining* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df029-271">To update the time remaining on the DHCP Client IP address lease with elapsed time before calling *nx_dhcp_resume*, see the *nx_dhcp_client_update_time_remaining* described previously.</span></span>

<span data-ttu-id="df029-272">このサービスでは、DHCP が有効になっているすべてのインターフェイスで実行されている DHCP が再開されます。</span><span class="sxs-lookup"><span data-stu-id="df029-272">This service resumes DHCP running on all interfaces enabled for DHCP.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df029-273">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="df029-273">Input Parameters</span></span>

- <span data-ttu-id="df029-274">**dhcp_ptr** DHCP クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="df029-274">**dhcp_ptr** Pointer to DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="df029-275">戻り値</span><span class="sxs-lookup"><span data-stu-id="df029-275">Return Values</span></span>

- <span data-ttu-id="df029-276">**NX_SUCCESS** (0x0) クライアントのスレッドが再開されました</span><span class="sxs-lookup"><span data-stu-id="df029-276">**NX_SUCCESS** (0x0) Client thread is resumed</span></span>

- <span data-ttu-id="df029-277">NX_PTR_ERROR (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="df029-277">NX_PTR_ERROR (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df029-278">許可元</span><span class="sxs-lookup"><span data-stu-id="df029-278">Allowed From</span></span>

<span data-ttu-id="df029-279">Threads</span><span class="sxs-lookup"><span data-stu-id="df029-279">Threads</span></span>

### <a name="example"></a><span data-ttu-id="df029-280">例</span><span class="sxs-lookup"><span data-stu-id="df029-280">Example</span></span>

```C
/* Resume the DHCP client thread. */
status=  nx_dhcp_resume(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is resumed. */
```