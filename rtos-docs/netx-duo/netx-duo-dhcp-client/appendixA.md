---
title: 付録 A - Azure RTOS NetX Duo DHCP クライアント サービスの復元状態機能の説明
description: この章では、Azure RTOS NetX Duo DHCP クライアント サービスの復元状態機能について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 008ca6fb0052339e188e0240cc38a81d3a6b40e8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810961"
---
# <a name="appendix-a--description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcp-client-services"></a>付録 A: Azure RTOS NetX Duo DHCP クライアント サービスの復元状態機能の説明

NetX Duo の DHDP クライアント構成オプションである NX_DHCP_CLIENT_RESTORE_STATE を使用すると、システムの再起動の間に、以前に作成された DHCP クライアント レコードをバインドされた状態で復元できます。

このオプションを有効にすると、アプリケーションでは DHCP クライアントのスレッドを中断および再開できます。 また、スレッドを中断して再開するまでの経過時間に DHCP クライアントを更新するサービスもあります。

## <a name="restoring-the-dhcp-client-between-reboots"></a>再起動の間に DHCP クライアントを復元する

再起動後に DHCP クライアントを復元する前に、以前に作成された DHCP クライアントが、バインドされた状態になり、DHCP サーバーから IP アドレスが割り当てられている必要があります。 電源を切る前に、DHCP アプリケーションで現在の DHCP クライアント レコードを不揮発性メモリに保存する必要があります。 また、電源がオフの状態で経過した時間を追跡するために、独立した "タイム キーパー" がシステムの他の場所に必要になります。 電源をオンにすると、アプリケーションでは、新しい DHCP クライアント インスタンスが作成され、以前に作成された DHCP クライアント レコードで更新されます。 経過時間は、"タイム キーパー" から取得され、DHCP クライアントのリースの残りの時間に適用されます。 これにより、DHCP クライアントの状態が変更される可能性があることに注意してください (たとえば、バインドから更新に)。 この時点で、アプリケーションでは DHCP クライアントを再開できます。

電源が切れている間に経過した時間によって DHCP クライアントの状態が更新または再バインドの状態になると、DHCP クライアントでは IP アドレスのリースの更新または再バインドを要求する DHCP メッセージが自動的に開始されます。 IP アドレスの有効期限が切れている場合、DHCP クライアントでは IP インスタンスの IP アドレスが自動的にクリアされ、新しい IP アドレスを要求する INIT 状態から DHCP プロセスが開始されます。

この方法では、DHCP クライアントが、再起動間に中断されていないかのように動作することができます。

この機能を下に示します。 これは、DHCP クライアントがプライマリ インターフェイスでのみ実行されていることを想定しています。

```c
/* On the power up, create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) for the DHCP Client/application
   in tx_application_define().  */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCP_CLIENT_RECORD client_nv_record;


if (/* The application checks if there is a previously saved DHCP Client record. */)
{
    /* No previously saved Client record. Start the DHCP Client in the INIT state.  */
    status =  nx_dhcp_start(&dhcp_0);

    if (status !=NX_SUCCESS)
        return;

    do
    {
        /* Wait for DHCP to assign the IP address.  */
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
        restore it to the current DHCP Client instance.  */

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
## <a name="resuming-the-dhcp-client-thread-after-suspension"></a>中断後に DHCP クライアントのスレッドを再開する 

電源を切ることなく DHCP クライアントのスレッドを中断するには、バインドされた状態になり、有効な IP アドレスを持つ DHCP クライアントに対し、アプリケーションで *nx_dhcp_suspend* を呼び出します。 DHCP クライアントを再開する準備ができたら、まず *nx_dhcp_client_update_time_remaining* を呼び出して、DHCP アドレスのリースの残り時間を更新します (独立したタイム キーパーから経過時間を取得します)。 次に、*nx_dhcp_resume* を呼び出して、DHCP クライアントのスレッドを再開します。

経過時間によって DHCP クライアントの状態が更新または再バインドの状態になると、DHCP クライアントでは IP アドレスのリースの更新または再バインドを要求する DHCP メッセージが自動的に開始されます。 IP アドレスの有効期限が切れている場合、DHCP クライアントでは IP アドレスが自動的にクリアされ、新しい IP アドレスを要求する初期化状態から DHCP プロセスが開始されます。

この機能の使用方法を以下に示します。

```c
/* Create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) typically in tx_application_define().  */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

  /* Start the DHCP Client.  */
  status =  nx_dhcp_start(&dhcp_0);

  if (status !=NX_SUCCESS)
    return;

  while(1)
  {
   /* Wait for DHCP to obtain an IP address.  */
  }

  /* Do tasks with the IP address e.g. send pings to another host on the network...  */
  status =  nx_icmp_ping(…);

  if (status !=NX_SUCCESS)
          printf("Failed %d byte Ping!\n", length);

  /* At some later time, suspend the DHCP Client e.g. the device is going to low 
   power mode (sleep) so we do not want any threads to wake it up. */

  nx_dhcp_suspend(&dhcp_0);  

  /* During this suspended state, an independent timer is keeping track of the elapsed      
     time. */


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
DHCP クライアントの状態をメモリから復元したり、DHCP クライアントを中断および再開したりするためのサービスを以下に示します。

## <a name="nx_dhcp_client_get_record"></a>nx_dhcp_client_get_record

現在の DHCP クライアントの状態のレコードを作成する

### <a name="prototype"></a>プロトタイプ

```c
ULONG nx_dhcp_ client_get_record(NX_DHCP *dhcp_ptr, NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>説明

このサービスでは、DHCP クライアント インスタンスで検出された DHCP に対して有効になっている最初のインターフェイスで実行されている DHCP クライアントが、record_ptr で指すレコードに保存されます。 これにより、DHCP クライアント アプリケーションでは、電源の切断、再起動などの後に、DHCP クライアントの状態を復元できます。

DHCP に対して複数のインターフェイスが有効になっている場合に、特定のインターフェイスの DHCP クライアント レコードを保存するには、*nx_dhcp_interface_client_get_record* サービスを使用します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr**: DHCP クライアントへのポインター
- **record_ptr**: DHCP クライアント レコードへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** : (0x0) クライアント レコードが作成されました
- **NX_DHCP_NOT_BOUND**: (0x94) クライアントがバインド状態ではありません
- **NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) DHCP に対して有効になっているインターフェイスがありません
- NX_PTR_ERROR: (0x16) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
NX_DHCP_CLIENT_RECORD dhcp_record;

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_get_record(dhcp_ptr, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_interface_client_get_record"></a>nx_dhcp_interface_client_get_record

指定したインターフェイスにおける現在の DHCP クライアントの状態のレコードを作成する

### <a name="prototype"></a>プロトタイプ

```c
ULONG nx_dhcp_interface_client_get_record(NX_DHCP *dhcp_ptr, UINT interface_index,
                                          NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>説明

このサービスでは、指定されたインターフェイスで実行されている DHCP クライアントが record_ptr が指すレコードに保存されます。 これにより、DHCP クライアント アプリケーションでは、電源の切断、再起動などの後に、DHCP クライアントの状態を復元できます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr**: DHCP クライアントへのポインター
- **interface_index**: レコードを取得するインデックス
- **record_ptr**: DHCP クライアント レコードへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** : (0x0) クライアント レコードが作成されました
- **NX_DHCP_NOT_BOUND**: (0x94) **クライアントがバインド状態ではありません**
- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) インターフェイスのインデックスが無効です
- NX_PTR_ERROR: (0x16) DHCP ポインターが無効です。
- NX_INVALID_INTERFACE: (0x4C) ネットワーク インターフェイスが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
/* Obtain a record of the current client state on interface 1. */
status=  nx_dhcp_interface_client_get_record(dhcp_ptr, 1, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_-client_restore_record"></a>nx_dhcp_ client_restore_record

以前に保存したレコードから DHCP クライアントを復元する

### <a name="prototype"></a>プロトタイプ

```c
ULONG nx_dhcp_client_restore_record(NX_DHCP *dhcp_ptr, 
                                    NX_DHCP_CLIENT_RECORD *record_ptr, 
                                    ULONG time_elapsed);

```

### <a name="description"></a>説明

このサービスを使用すると、アプリケーションでは、record_ptr が指す DHCP クライアント レコードを使用して、以前のセッションから DHCP クライアントを復元できます。 time_elapsed の入力は、DHCP クライアントのリースの残りの期間に適用されます。

これを行うには、DHCP クライアント アプリケーションで、電源を切る前に DHCP クライアントのレコードを作成し、そのレコードを不揮発性メモリに保存する必要があります。

DHCP クライアントに対して複数のインターフェイスが有効になっている場合、このサービスは DHCP クライアント インスタンスで検出された最初の有効なインターフェイスに適用されます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr**: DHCP クライアントへのポインター
- **record_ptr**: DHCP クライアント レコードへのポインター 
- **time_elapsed**: 入力クライアント レコードの残りのリース期間から減算する時間

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x0) クライアント レコードが復元されました
- **NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) DHCP が実行されているインターフェイスがありません
- NX_PTR_ERROR: (0x16) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_restore_record(client_ptr, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_interace_client_restore_record"></a>nx_dhcp_interace_client_restore_record

以前に保存したレコードから指定したインターフェイスに DHCP クライアントを復元する

### <a name="prototype"></a>プロトタイプ

```c
ULONG nx_dhcp_interface_client_restore_record(NX_DHCP *dhcp_ptr, 
                                              NX_DHCP_CLIENT_RECORD *record_ptr, 
                                              ULONG time_elapsed);
```

### <a name="description"></a>説明

このサービスを使用すると、アプリケーションでは、record_ptr が指す DHCP クライアント レコードを使用して、指定したインターフェイスに DHCP クライアントを復元できます。 time_elapsed の入力は、DHCP クライアントのリースの残りの期間に適用されます。

これを行うには、DHCP クライアント アプリケーションで、電源を切る前に DHCP クライアントのレコードを作成し、そのレコードを不揮発性メモリに保存する必要があります。

DHCP クライアントに対して複数のインターフェイスが有効になっている場合、このサービスは DHCP クライアント インスタンスで検出された最初の有効なインターフェイスに適用されます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr**: DHCP クライアントへのポインター
- **record_ptr**: DHCP クライアント レコードへのポインター 
- **time_elapsed**: 入力クライアント レコードの残りのリース期間から減算する時間

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x0) クライアント レコードが復元されました
- **NX_DHCP_NOT_BOUND**: (0x94) クライアントが IP アドレスにバインドされていません
- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) インターフェイスのインデックスが無効です
- NX_PTR_ERROR: (0x16) DHCP ポインターが無効です。
- NX_INVALID_INTERFACE: (0x4C) ネットワーク インターフェイスが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state on the primary interface. */
status=  nx_dhcp_interface_client_restore_record(client_ptr, 0, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_-client_update_time_remaining"></a>nx_dhcp_ client_update_time_remaining

DHCP クライアントのリースの残り時間を更新する

### <a name="prototype"></a>プロトタイプ

```c
ULONG nx_dhcp_client_update_time_remaining(NX_DHCP *dhcp_ptr, ULONG time_elapsed);
```

### <a name="description"></a>説明

このサービスでは、DHCP クライアントの IP アドレスのリースの残り時間が、DHCP クライアント インスタンスで検出された DHCP に対して有効になっている最初のインターフェイスの time_elapsed の入力を使用して更新されます。 アプリケーションでは、*nx_dhcp_suspend* を使用してこのサービスを使用する前に、DHCP クライアントのスレッドを中断する必要があります。 このサービスを呼び出した後、アプリケーションでは *nx_dhcp_resume* を呼び出すことによって DHCP クライアントのスレッドを再開できます。

これは、DHCP クライアントのスレッドを一定期間中断してから、IP アドレスの残りのリース期間を更新する必要がある DHCP クライアント アプリケーションを対象としています。

注: このサービスは、前に説明した *nx_dhcp_client_get_record* および *nx_dhcp_client_restore_record* と使用することは意図されていません。 これらのサービスについては、このセクションで既に説明しています。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr**: DHCP クライアントへのポインター 
- **time_elapsed**: IP アドレスのリースの残り時間から減算する時間

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x0) クライアントの IP のリースが更新されました
- **NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) DHCP に対して有効になっているインターフェイスがありません
- NX_PTR_ERROR: (0x16) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease. */
status=  nx_dhcp_client_update_time_remaining(client_ptr, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```

## <a name="nx_dhcp_interface_client_update_time_remaining"></a>nx_dhcp_interface_client_update_time_remaining

指定されたインターフェイスにおける DHCP クライアントのリースの残り時間を更新する

### <a name="prototype"></a>プロトタイプ

```c
ULONG nx_dhcp_interface_client_update_time_remaining(NX_DHCP *dhcp_ptr,
                                                     UINT interface_index,
                                                     ULONG time_elapsed);
```

### <a name="description"></a>説明

このサービスでは、DHCP クライアントの IP アドレスのリースの残り時間が、指定されたインターフェイスの time_elapsed の入力を使用して更新されます (そのインターフェイスが DHCP に対して有効になっている場合)。 アプリケーションでは、*nx_dhcp_suspend* を使用してこのサービスを使用する前に、DHCP クライアントのスレッドを中断する必要があります。 このサービスを呼び出した後、アプリケーションでは *nx_dhcp_resume* を呼び出すことによって DHCP クライアントのスレッドを再開できます。 DHCP クライアントのスレッドの中断と再開は、DHCP に対して有効になっているすべてのインターフェイスに適用されます。

これは、DHCP クライアントのスレッドを一定期間中断してから、IP アドレスの残りのリース期間を更新する必要がある DHCP クライアント アプリケーションを対象としています。

注: このサービスは、前に説明した *nx_dhcp_client_get_record* および *nx_dhcp_client_restore_record* と使用することは意図されていません。 これらのサービスについては、このセクションで既に説明しています。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr**: DHCP クライアントへのポインター
- **interface_index**: 経過時間を適用するインターフェイスへのインデックス
- **time_elapsed**: IP アドレスのリースの残り時間から減算する時間

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x0) クライアントの IP のリースが更新されました
- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) インターフェイスのインデックスが無効です
- NX_PTR_ERROR: (0x16) DHCP ポインターが無効です。
- NX_INVALID_INTERFACE: (0x4C) ネットワーク インターフェイスが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease on interface 1. */
status=  nx_dhcp_interface_client_update_time_remaining(client_ptr, 1, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */

```

## <a name="nx_dhcp_suspend"></a>nx_dhcp_suspend

DHCP クライアントのスレッドを中断する

### <a name="prototype"></a>プロトタイプ

```c
ULONG nx_dhcp_suspend(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>説明

このサービスでは、現在の DHCP クライアントのスレッドが中断されます。 *nx_dhcp_stop* とは異なり、このサービスが呼び出されたときに DHCP クライアントの状態が変更されることはありません。

このサービスでは、DHCP が有効になっているすべてのインターフェイスで実行されている DHCP が中断されます。

DHCP クライアントが中断されていた間の経過時間で DHCP クライアントの状態を更新するには、前述の *nx_dhcp_client_update_time_remaining* を参照してください。 中断された DHCP クライアントのスレッドを再開するには、アプリケーションで *nx_dhcp_resume* を呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr**: DHCP クライアントへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x0) クライアントのスレッドが中断されました
- NX_PTR_ERROR: (0x16) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Pause the DHCP client thread. */
status=  nx_dhcp_suspend(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is paused. */
```

## <a name="nx_dhcp_resume"></a>nx_dhcp_resume

中断された DHCP クライアントのスレッドを再開する

### <a name="prototype"></a>プロトタイプ

```c
ULONG nx_dhcp_resume(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>説明

このサービスでは、中断された DHCP クライアントのスレッドが再開されます。 クライアントのスレッドが再開された後に、実際の DHCP クライアントの状態は変更されないことに注意してください。 *nx_dhcp_resume* を呼び出す前に DHCP クライアント の IP アドレスのリースの残り時間を経過時間で更新するには、前に説明した *nx_dhcp_client_update_time_remaining* を参照してください。

このサービスでは、DHCP が有効になっているすべてのインターフェイスで実行されている DHCP が再開されます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr**: DHCP クライアントへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x0) クライアントのスレッドが再開されました
- NX_PTR_ERROR: (0x16) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Resume the DHCP client thread. */
status=  nx_dhcp_resume(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is resumed. */
```