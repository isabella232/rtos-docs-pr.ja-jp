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
# <a name="appendix-a---description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcpv6-client"></a>付録 A - Azure RTOS NetX Duo DHCPv6 クライアントの状態復元機能の説明

Azure RTOS NetX Duo DHDPv6 クライアントの構成オプション NX_DHCPV6_CLIENT_RESTORE_STATE を使用すると、システムの再起動の間に、以前に作成された DHCP クライアントを Bound 状態で復元できます。

このオプションを使用すると、アプリケーションで、DHCPv6 クライアント スレッドを中断して再開し、電源を切ることなくスレッドを中断してから再開するまでの経過時間を使用して更新することもできます。

## <a name="restoring-the-dhcpv6-client-between-reboots"></a>再起動の間に DHCPv6 クライアントを復元する

再起動の間に DHCPv6 クライアントを復元するには、DHCPv6 アプリケーションで、DHCPv6 クライアントのインスタンスを作成した後、通常の DHCPv6 プロトコルを使用して *nx_dhcpv6_start* を呼び出し、IP アドレス リースを取得します。 その後、プロトコルが完了するのを DHCPv6 アプリケーションで待機します。 すべて正常に行われると、デバイスは、DHCPv6 サーバーから有効な IP アドレスが割り当てられた BOUND 状態になります。 電源を切る前に、DHCPv6 クライアント アプリケーションによって、現在の DHCPv6 クライアント インスタンスを DHCPv6 クライアント レコードに保存し、それは不揮発性メモリに格納されます。 システムの他の場所にある独立した "タイム キーパー" により、電源がオフの状態で経過した時間を追跡します。 電源をオンにすると、アプリケーションによって、新しい DHCPv6 クライアント インスタンスが作成された後、以前に作成された DHCPv6 クライアント レコードで更新されます。 経過時間が、"タイム キーパー" から取得され、DHCP Clientv6 のリースの残りの時間に適用されます。 この時点で、アプリケーションで DHCPv6 クライアントを再開できます。

電源が切れている間に経過した時間によって DHCPv6 クライアントの状態が RENEW または REBIND 状態になると、DHCPv6 クライアントによって IP アドレスのリースの更新または再バインドを要求する DHCPv6 メッセージが自動的に開始されます。 IP アドレスの有効期限が切れている場合、DHCPv6 クライアントにより IP インスタンスの IP アドレスが自動的にクリアされ、INIT 状態から DHCPv6 プロセスが開始されて、新しい IP アドレスが要求されます。

この方法では、DHCPv6 クライアントは、再起動間に中断されていないかのように動作することができます。

この機能を下に示します。

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

## <a name="nx_dhcpv6_client_get_record"></a>nx_dhcpv6_client_get_record

現在の DHCPv6 クライアントの状態のレコードを作成します

### <a name="prototype"></a>プロトタイプ

```C
ULONG nx_dhcpv6_client_get_record(NX_DHCPV6 *dhcpv6_ptr, 
                                  NX_DHCPV6_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、record_ptr によって示されるレコードに DHCPv6 クライアントが保存されます。 これにより、DHCPv6 クライアント アプリケーションで、電源を切断して再起動した後などに、DHCPv6 クライアントの状態を復元できます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr** DHCPv6 クライアントへのポインター

- **record_ptr** DHCPv6 クライアント レコードへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x0) 有効なクライアント レコードが作成されました

- **NX_DHCPV6_NOT_BOUND** (0xE94) クライアントが BOUND 状態ではないため、有効な IP アドレスが割り当てられませんでした

- **NX_PTR_ERROR** (0x16) ポインターの入力が無効です

### <a name="allowed-from"></a>使用可能な場所

Threads

### <a name="example"></a>例

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;


/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_get_record(&dhcpv6_ptr, &dhcpv6_record);

/* If status is NX_SUCCESS dhcpv6_record contains the current DHCPv6 client record. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_client_restore_record

## <a name="nx_dhcpv6_client_restore_record"></a>nx_dhcpv6_client_restore_record

保存されたレコードから DHCPv6 クライアントの状態を復元します

### <a name="prototype"></a>プロトタイプ

```C
ULONG nx_dhcpv6_client_restore_record(NX_DHCPV6 *dhcpv6_ptr, 
                                      NX_DHCPV6_CLIENT_RECORD       
                                      *record_ptr, ULONG time_elapsed);
```

### <a name="description"></a>説明

このサービスを使用すると、DHCPv6 アプリケーションにより、record_ptr によって示される DHCPv6 クライアント レコードを使用して DHCPv6 クライアントを更新することで、前のセッションから DHCPv6 クライアントの状態を再作成し、time_elapsed の入力で DHCPv6 クライアント リースの残り時間を更新することができます。 これにより、DHCPv6 クライアント アプリケーションで、電源切断後などに、DHCPv6 クライアントを再作成できます。 これを行うには、DHCPv6 クライアント アプリケーションで、電源を切る前に DHCPv6 クライアントのレコードを作成し、そのレコードを不揮発性メモリに保存する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr** DHCPv6 クライアントへのポインター

- **record_ptr** DHCPv6 クライアント レコードへのポインター

- **time_elapsed** 入力クライアント レコードの残りのリース期間から減算する時間

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x0) クライアント レコードが復元されました

- NX_PTR_ERROR (0x16) ポインターの入力が無効です

### <a name="allowed-from"></a>使用可能な場所

Threads

### <a name="example"></a>例

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_restore_record(&dhcpv6_ptr, &dhcpv6_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCPv6 Client pointed to by dhcpv6_ptr contains the current client record updated for time elapsed during power down. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_client_get_record