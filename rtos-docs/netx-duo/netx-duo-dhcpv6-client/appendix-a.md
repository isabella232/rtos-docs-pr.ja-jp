---
title: 付録 A - Azure RTOS NetX Duo DHCPv6 クライアントの状態復元機能の説明
description: Azure RTOS NetX Duo DHDPv6 クライアントの構成オプション NX_DHCPV6_CLIENT_RESTORE_STATE を使用すると、システムの再起動の間に、以前に作成された DHCP クライアントを Bound 状態で復元できます。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3e642af158202bb3b2a4e2a37397b47d707b566e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810916"
---
# <a name="appendix-a---description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcpv6-client"></a><span data-ttu-id="71820-103">付録 A - Azure RTOS NetX Duo DHCPv6 クライアントの状態復元機能の説明</span><span class="sxs-lookup"><span data-stu-id="71820-103">Appendix A - Description of the Restore State Feature for Azure RTOS NetX Duo DHCPv6 Client</span></span>

<span data-ttu-id="71820-104">Azure RTOS NetX Duo DHDPv6 クライアントの構成オプション NX_DHCPV6_CLIENT_RESTORE_STATE を使用すると、システムの再起動の間に、以前に作成された DHCP クライアントを Bound 状態で復元できます。</span><span class="sxs-lookup"><span data-stu-id="71820-104">The Azure RTOS NetX Duo DHDPv6 Client configuration option, NX_DHCPV6_CLIENT_RESTORE_STATE, allows a system to restore a previously created DHCP Client in a Bound state between system reboots.</span></span>

<span data-ttu-id="71820-105">このオプションを使用すると、アプリケーションで、DHCPv6 クライアント スレッドを中断して再開し、電源を切ることなくスレッドを中断してから再開するまでの経過時間を使用して更新することもできます。</span><span class="sxs-lookup"><span data-stu-id="71820-105">This option also allows an application to suspend the DHCPv6 Client thread and resume it, updated with the elapsed time between suspending and resuming the thread without powering down.</span></span>

## <a name="restoring-the-dhcpv6-client-between-reboots"></a><span data-ttu-id="71820-106">再起動の間に DHCPv6 クライアントを復元する</span><span class="sxs-lookup"><span data-stu-id="71820-106">Restoring the DHCPv6 Client between Reboots</span></span>

<span data-ttu-id="71820-107">再起動の間に DHCPv6 クライアントを復元するには、DHCPv6 アプリケーションで、DHCPv6 クライアントのインスタンスを作成した後、通常の DHCPv6 プロトコルを使用して *nx_dhcpv6_start* を呼び出し、IP アドレス リースを取得します。</span><span class="sxs-lookup"><span data-stu-id="71820-107">To restore a DHCPv6 Client between reboots, the DHCPv6 application creates an instance of the DHCPv6 Client, and then obtains an IP address lease using the normal DHCPv6 protocol and calling *nx_dhcpv6_start*.</span></span> <span data-ttu-id="71820-108">その後、プロトコルが完了するのを DHCPv6 アプリケーションで待機します。</span><span class="sxs-lookup"><span data-stu-id="71820-108">Then the DHCPv6 application waits for the protocol to complete.</span></span> <span data-ttu-id="71820-109">すべて正常に行われると、デバイスは、DHCPv6 サーバーから有効な IP アドレスが割り当てられた BOUND 状態になります。</span><span class="sxs-lookup"><span data-stu-id="71820-109">If all goes well, the device achieves the BOUND state with an assigned valid IP address from its DHCPv6 Server.</span></span> <span data-ttu-id="71820-110">電源を切る前に、DHCPv6 クライアント アプリケーションによって、現在の DHCPv6 クライアント インスタンスを DHCPv6 クライアント レコードに保存し、それは不揮発性メモリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="71820-110">Before it powers down, the DHCPv6 Client application saves the current DHCPv6 Client instance to a DHCPv6 Client record which is then stored in non-volatile memory.</span></span> <span data-ttu-id="71820-111">システムの他の場所にある独立した "タイム キーパー" により、電源がオフの状態で経過した時間を追跡します。</span><span class="sxs-lookup"><span data-stu-id="71820-111">An independent ‘time keeper’ elsewhere in the system keeps track of the time elapsed during this powered down state.</span></span> <span data-ttu-id="71820-112">電源をオンにすると、アプリケーションによって、新しい DHCPv6 クライアント インスタンスが作成された後、以前に作成された DHCPv6 クライアント レコードで更新されます。</span><span class="sxs-lookup"><span data-stu-id="71820-112">On powering up, the application creates a new DHCPv6 Client instance, and then updates it with the previously created DHCPv6 Client record.</span></span> <span data-ttu-id="71820-113">経過時間が、"タイム キーパー" から取得され、DHCP Clientv6 のリースの残りの時間に適用されます。</span><span class="sxs-lookup"><span data-stu-id="71820-113">The elapsed time is obtained from the “time keeper” and then applied to the time remaining on the DHCP Clientv6 lease.</span></span> <span data-ttu-id="71820-114">この時点で、アプリケーションで DHCPv6 クライアントを再開できます。</span><span class="sxs-lookup"><span data-stu-id="71820-114">At this point, the application can resume the DHCPv6 Client.</span></span>

<span data-ttu-id="71820-115">電源が切れている間に経過した時間によって DHCPv6 クライアントの状態が RENEW または REBIND 状態になると、DHCPv6 クライアントによって IP アドレスのリースの更新または再バインドを要求する DHCPv6 メッセージが自動的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="71820-115">If the time elapsed during power down puts the DHCPv6 Client state in either a RENEW or REBIND state, the DHCPv6 Client will automatically initiate DHCPv6 messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="71820-116">IP アドレスの有効期限が切れている場合、DHCPv6 クライアントにより IP インスタンスの IP アドレスが自動的にクリアされ、INIT 状態から DHCPv6 プロセスが開始されて、新しい IP アドレスが要求されます。</span><span class="sxs-lookup"><span data-stu-id="71820-116">If the IP address is expired, the DHCPv6 Client will automatically clear the IP address on the IP instance and begin the DHCPv6 process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="71820-117">この方法では、DHCPv6 クライアントは、再起動間に中断されていないかのように動作することができます。</span><span class="sxs-lookup"><span data-stu-id="71820-117">In this manner the DHCPv6 Client can operate between reboots as if uninterrupted.</span></span>

<span data-ttu-id="71820-118">この機能を下に示します。</span><span class="sxs-lookup"><span data-stu-id="71820-118">Below is an illustration of this feature.</span></span>

```C
/* On the power up, create an IP instance, DHCPv6 Client, enable ICMPv6 and UDP
   and other resources (not shown) for the DHCPv6 Client/application
   in tx_application_define(). */
 
/* Define the DHCPv6 Client application thread. */     
void    thread_dhcpv6_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCPV6_CLIENT_RECORD client_my_record;


    /* No previously saved Client record. Start the DHCPv6 Client in the INIT state. */
    status =  nx_dhcpv6_start(&dhcp_0);

    if (status !=NX_SUCCESS)
        return;

    while(1)    
    {
    
        /* Wait for DHCPv6 Client to get the IP address. */
    }

    /* At some point decide we power down the system. */

    /* Save the Client state data which we will subsequently need to restore the DHCPv6    
       Client. */
    status = nx_dhcpv6_client_get_record(&dhcp_0, &client_my_record);               

    /* Copy this memory to non-volatile memory (not shown). */

    /* Delete the IP and DHCPv6 Client instances before powering down. */
    nx_dhcpv6_client_delete(&dhcp_0);

    nx_ip_delete(&ip_0);

    /* Ready to power down, having released other resources as necessary. */

    /* The application has determined there is a previously saved record. We will 
       restore it to the current DHCPv6 Client instance. */

/* Create the IP and DHCPv6 Client instances, enable ICMPv6 and UDP after powering up. */

/* Calculate the time elapsed during power down */

    /* Get the previous Client state data from non-volatile memory. */

    /* Apply the record to the current Client instance. This will also 
       update the IP instance with IP address, mask etc. */
    status = nx_dhcpv6_client_restore_record(&dhcp_0, &client_my_record, time_elapsed);   

     if (status != NX_SUCCESS)
          return;

     /* We are ready to resume the DHCPv6 Client thread and use the assigned IP address. */
     status = nx_dhcpv6_resume(&dhcp_0);

     if (status != NX_SUCCESS)
          return;

}
```

## <a name="nx_dhcpv6_client_get_record"></a><span data-ttu-id="71820-119">nx_dhcpv6_client_get_record</span><span class="sxs-lookup"><span data-stu-id="71820-119">nx_dhcpv6_client_get_record</span></span>

<span data-ttu-id="71820-120">現在の DHCPv6 クライアントの状態のレコードを作成します</span><span class="sxs-lookup"><span data-stu-id="71820-120">Create a record of the current DHCPv6 Client state</span></span>

### <a name="prototype"></a><span data-ttu-id="71820-121">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="71820-121">Prototype</span></span>

```C
ULONG nx_dhcpv6_client_get_record(NX_DHCPV6 *dhcpv6_ptr, 
                                  NX_DHCPV6_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="71820-122">説明</span><span class="sxs-lookup"><span data-stu-id="71820-122">Description</span></span>

<span data-ttu-id="71820-123">このサービスを使用すると、record_ptr によって示されるレコードに DHCPv6 クライアントが保存されます。</span><span class="sxs-lookup"><span data-stu-id="71820-123">This service saves the DHCPv6 Client to the record pointed to by record_ptr.</span></span> <span data-ttu-id="71820-124">これにより、DHCPv6 クライアント アプリケーションで、電源を切断して再起動した後などに、DHCPv6 クライアントの状態を復元できます。</span><span class="sxs-lookup"><span data-stu-id="71820-124">This allows the DHCPv6 Client application restore its DHCPv6 Client state after, for example, a power down and reboot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71820-125">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="71820-125">Input Parameters</span></span>

- <span data-ttu-id="71820-126">**dhcpv6_ptr** DHCPv6 クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="71820-126">**dhcpv6_ptr** Pointer to DHCPv6 Client</span></span>

- <span data-ttu-id="71820-127">**record_ptr** DHCPv6 クライアント レコードへのポインター</span><span class="sxs-lookup"><span data-stu-id="71820-127">**record_ptr** Pointer to DHCPv6 Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="71820-128">戻り値</span><span class="sxs-lookup"><span data-stu-id="71820-128">Return Values</span></span>

- <span data-ttu-id="71820-129">**NX_SUCCESS** (0x0) 有効なクライアント レコードが作成されました</span><span class="sxs-lookup"><span data-stu-id="71820-129">**NX_SUCCESS (0x0)** Valid Client record created</span></span>

- <span data-ttu-id="71820-130">**NX_DHCPV6_NOT_BOUND** (0xE94) クライアントが BOUND 状態ではないため、有効な IP アドレスが割り当てられませんでした</span><span class="sxs-lookup"><span data-stu-id="71820-130">**NX_DHCPV6_NOT_BOUND** (0xE94) Client not in bound state, therefore not assigned valid IP address</span></span>

- <span data-ttu-id="71820-131">**NX_PTR_ERROR** (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="71820-131">**NX_PTR_ERROR** (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71820-132">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="71820-132">Allowed From</span></span>

<span data-ttu-id="71820-133">Threads</span><span class="sxs-lookup"><span data-stu-id="71820-133">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71820-134">例</span><span class="sxs-lookup"><span data-stu-id="71820-134">Example</span></span>

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;


/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_get_record(&dhcpv6_ptr, &dhcpv6_record);

/* If status is NX_SUCCESS dhcpv6_record contains the current DHCPv6 client record. */
```

### <a name="see-also"></a><span data-ttu-id="71820-135">参照</span><span class="sxs-lookup"><span data-stu-id="71820-135">See Also</span></span>

- <span data-ttu-id="71820-136">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="71820-136">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="71820-137">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="71820-137">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="71820-138">nx_dhcpv6_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="71820-138">nx_dhcpv6_client_restore_record</span></span>

## <a name="nx_dhcpv6_client_restore_record"></a><span data-ttu-id="71820-139">nx_dhcpv6_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="71820-139">nx_dhcpv6_client_restore_record</span></span>

<span data-ttu-id="71820-140">保存されたレコードから DHCPv6 クライアントの状態を復元します</span><span class="sxs-lookup"><span data-stu-id="71820-140">Restore DHCPv6 Client state from saved record</span></span>

### <a name="prototype"></a><span data-ttu-id="71820-141">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="71820-141">Prototype</span></span>

```C
ULONG nx_dhcpv6_client_restore_record(NX_DHCPV6 *dhcpv6_ptr, 
                                      NX_DHCPV6_CLIENT_RECORD       
                                      *record_ptr, ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="71820-142">説明</span><span class="sxs-lookup"><span data-stu-id="71820-142">Description</span></span>

<span data-ttu-id="71820-143">このサービスを使用すると、DHCPv6 アプリケーションにより、record_ptr によって示される DHCPv6 クライアント レコードを使用して DHCPv6 クライアントを更新することで、前のセッションから DHCPv6 クライアントの状態を再作成し、time_elapsed の入力で DHCPv6 クライアント リースの残り時間を更新することができます。</span><span class="sxs-lookup"><span data-stu-id="71820-143">This service enables a DHCPv6 application to recreate its DHCPv6 Client state from a previous session by updating the DHCPv6 Client with the DHCPv6 Client record pointed to by record_ptr, and updates the time remaining on DHCPv6 Client lease with the time_elapsed input.</span></span> <span data-ttu-id="71820-144">これにより、DHCPv6 クライアント アプリケーションで、電源切断後などに、DHCPv6 クライアントを再作成できます。</span><span class="sxs-lookup"><span data-stu-id="71820-144">This allows the DHCPv6 Client application to recreate its DHCPv6 Client, for example, after powering down.</span></span> <span data-ttu-id="71820-145">これを行うには、DHCPv6 クライアント アプリケーションで、電源を切る前に DHCPv6 クライアントのレコードを作成し、そのレコードを不揮発性メモリに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71820-145">This requires that the DHCPv6 Client application created a record of the DHCPv6 Client before powering down, and saved that record to non-volatile memory.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71820-146">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="71820-146">Input Parameters</span></span>

- <span data-ttu-id="71820-147">**dhcpv6_ptr** DHCPv6 クライアントへのポインター</span><span class="sxs-lookup"><span data-stu-id="71820-147">**dhcpv6_ptr** Pointer to DHCPv6 Client</span></span>

- <span data-ttu-id="71820-148">**record_ptr** DHCPv6 クライアント レコードへのポインター</span><span class="sxs-lookup"><span data-stu-id="71820-148">**record_ptr** Pointer to DHCPv6 Client record</span></span>

- <span data-ttu-id="71820-149">**time_elapsed** 入力クライアント レコードの残りのリース期間から減算する時間</span><span class="sxs-lookup"><span data-stu-id="71820-149">**time_elapsed** Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="71820-150">戻り値</span><span class="sxs-lookup"><span data-stu-id="71820-150">Return Values</span></span>

- <span data-ttu-id="71820-151">**NX_SUCCESS** (0x0) クライアント レコードが復元されました</span><span class="sxs-lookup"><span data-stu-id="71820-151">**NX_SUCCESS (0x0)** Client record restored</span></span>

- <span data-ttu-id="71820-152">NX_PTR_ERROR (0x16) ポインターの入力が無効です</span><span class="sxs-lookup"><span data-stu-id="71820-152">NX_PTR_ERROR (0x16) Invalid Pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71820-153">使用可能な場所</span><span class="sxs-lookup"><span data-stu-id="71820-153">Allowed From</span></span>

<span data-ttu-id="71820-154">Threads</span><span class="sxs-lookup"><span data-stu-id="71820-154">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71820-155">例</span><span class="sxs-lookup"><span data-stu-id="71820-155">Example</span></span>

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_restore_record(&dhcpv6_ptr, &dhcpv6_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCPv6 Client pointed to by dhcpv6_ptr contains the current client record updated for time elapsed during power down. */
```

### <a name="see-also"></a><span data-ttu-id="71820-156">参照</span><span class="sxs-lookup"><span data-stu-id="71820-156">See Also</span></span>

- <span data-ttu-id="71820-157">nx_dhcpv6_client_get_record</span><span class="sxs-lookup"><span data-stu-id="71820-157">nx_dhcpv6_client_get_record</span></span>