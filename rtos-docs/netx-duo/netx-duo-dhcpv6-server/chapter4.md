---
title: 第 4 章 - Azure RTOS NetX Duo DHCPv6 サーバーのサービス
description: この章では、NetX Duo DHCPv6Server のすべてのサービスについて説明します
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf6b43f70a7159af6c24496ec2ae2276d5e271af2ad3af99687181df3bf6be6c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792028"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-server-services"></a>第 4 章 - Azure RTOS NetX Duo DHCPv6 サーバーのサービス

この章では、NetX Duo DHCPv6Server のすべてのサービスについて説明します (以下の一覧を参照)。

以下の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。

- nx_dhcpv6_server_create *DHCPv6 サーバー インスタンスを作成します*
- nx_dhcpv6_server_delete *DHCPv6 サーバー インスタンスを削除します*
- nx_dhcpv6_server_start *DHCPv6 サーバー タスクを開始します*
- nx_dhcpv6_server_suspend *DHCPv6 サーバー タスクを一時停止します*
- nx_dhcpv6_server_resume *DHCPv6 クライアントの処理を再開します*
- nx_dhcpv6_server_suspend *DHCPv6 クライアントの処理を一時停止します*
- nx_dhcpv6_create_dns_address *DNS サーバーをオプション要求用に設定します*
- nx_dhcpv6_create_ip_address_range *リースする IP アドレスの範囲を作成します*
- nx_dhcpv6_reserve_ip_address_range *サーバー リストで IP アドレスの範囲を予約します*
- nx_dhcpv6_set_server_duid *DHCPv6 パケット用のサーバー DUID を設定します*
- nx_dhcpv6_add_ip_address_lease *DHCPv6 サーバー テーブルにリース レコードを追加します*
- Nx_dhcpv6_retrieve_ip_address_lease *サーバー テーブルから IP リース レコードを取得します*
- nx_dhcpv6_add_client_record *サーバー テーブルに DHCPv6 クライアント レコードを追加します*
- nx_dhcpv6_retrieve_client_record *サーバー テーブルからクライアント レコードを取得します*
- nx_dhcpv6_server_interface_set *サーバー DHCPv6 サービス用の インターフェイス インデックスを設定します*
- nx_dhcpv6_server_option_request_handler_set *オプション要求ハンドラーを設定します*

## <a name="nx_dhcpv6_create_dns_address"></a>nx_dhcpv6_create_dns_address

### <a name="set-the-network-dns-server"></a>ネットワーク DNS サーバーを設定する

**プロトタイプ**

```
UINT nx_dhcpv6_create_dns_address(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *dns_ipv6_address);
```

**説明**

このサービスを使用すると、サーバー DHCPv6 ネットワーク インターフェイス用の DNS サーバー アドレスが DHCPv6 サーバーに読み込まれます。

**入力パラメーター**

- **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター
- **dns_ipv6_address** DNS サーバーへのポインター

**戻り値**

- **NX_SUCCESS** (0x00) DNS サーバーが DHCPv6 サーバー インスタンスに保存されました
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) 無効なアドレスが指定されています
- NX_PTR_ERROR (0x16) ポインターの入力が無効です

**使用可能な場所**

アプリケーション コード

**例**

```
/* Set the network DNS server with the input address for the Server DHCPv6interface. */
status = nx_dhcpv6_create__dns_address(&dhcp_server_0, &dns_ipv6_address);
/* If this service returns NX_SUCCESS the DNS server data was accepted. */
```

## <a name="nx_dhcpv6_create_ip_address_range"></a>nx_dhcpv6_create_ip_address_range

### <a name="create-the-server-ip-address-list"></a>サーバーの IP アドレス リストを作成します

**プロトタイプ**

```
UINT _nx_dhcpv6_create_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_added)
```

**説明**

このサービスを使用すると、サーバーの割り当て可能なアドレス範囲の開始アドレスと終了アドレスによって指定された IP アドレス リストが作成されます。 開始アドレスと終了アドレスは、サーバー インターフェイスのアドレス プレフィックスと一致している必要があります (サーバー DHCPv6 インターフェイスと同じリンク上にある必要があります)。 実際に追加されたアドレスの数が返されます。

**入力パラメーター**

- **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター
- **start_ipv6_address** 追加するアドレスの先頭
- **end_ipv6_address** 追加するアドレスの末尾
- ***addresses_added** 追加されたアドレスの出力

**戻り値**

- **NX_SUCCESS** (0x00) IP アドレス リストが正常に作成されました
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) 無効なアドレスが指定されています
- NX_PTR_ERROR (0x16) ポインターの入力が無効です

**使用可能な場所**

アプリケーション コード

**例**

```
/* Create the Server IP address list for the server DHCPv6 interface. */
status = nx_dhcpv6_create_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);
/* If status is NX_SUCCESS one or more addresses were successfully added. */
```

## <a name="nx_dhcpv6_reserve_ip_address_range"></a>nx_dhcpv6_reserve_ip_address_range

### <a name="reserve-specified-range-of-ip-addresses"></a>指定した IP アドレスの範囲を予約します

**プロトタイプ**

```
UINT _nx_dhcpv6_reserve_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_reserved)
```

**説明**

このサービスを使用すると、開始アドレスと終了アドレスによって指定した IP アドレスの範囲が予約されます。 これらのアドレスは、前に作成したサーバーの IP アドレス範囲内に含まれる必要があります。 これらのアドレスは、DHCPv6 サーバーによってクライアントに割り当てられなくなります。 開始アドレスと終了アドレスは、サーバー インターフェイスのアドレス プレフィックスと一致している必要があります (サーバー DHCPv6 ネットワーク インターフェイスと同じリンク上にある必要があります)。 実際に予約されたアドレスの数が返されます。

**入力パラメーター**

- **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター
- **start_ipv6_address** 予約するアドレスの先頭
- **end_ipv6_address** 予約するアドレスの末尾
- ***addresses_reserved** 予約されたアドレスの数

**戻り値**

- **NX_SUCCESS** (0x00) RELEASE メッセージが正常に作成され、処理されました
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) 無効なアドレスが指定されています
- **NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) サーバー アドレス リストに開始アドレスが見つかりません。
- NX_PTR_ERROR (0x16) ポインターの入力が無効です

**使用可能な場所**

アプリケーション コード

**例**

```
/* Reserve a range of ip addresses in the Server address table for the server DHCPv6 
network interface. */

status = nx_dhcpv6_reserve_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);

/* If status is NX_SUCCESS one or more addresses were successfully reserved. */
```

## <a name="nx_dhcpv6_server_create"></a>nx_dhcpv6_server_create

### <a name="create-the-dhcpv6-server-instance"></a>DHCPv6 サーバー インスタンスを作成します 

**プロトタイプ**

```
UINT nx_dhcpv6_server_create(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
        NX_IP *ip_ptr, CHAR *name_ptr, 
        NX_PACKET_POOL *packet_pool_ptr, 
        VOID *stack_ptr,ULONG stack_size,
    VOID (*dhcpv6_address_declined_handler)(struct 
        NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        NX_DHCPV6_CLIENT *dhcpv6_client_ptr, 
        UINT message),
    VOID (*dhcpv6_option_request_handler)(
        struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        UINT option_request, UCHAR *buffer_ptr, UINT *index));
```

**説明**

このサービスを使用すると、指定した入力を使用して DHCPv6 サーバー タスクが作成されます。 コールバック ハンドラーは、省略可能な入力です。 スタック ポインター、IP インスタンス、パケット プールの入力は必須です。 IP インスタンスとパケット プールは、既に作成されている必要があります。

ユーザーには、nx_dhcpv6_server_option_request_handler_set を呼び出して、オプション要求ハンドラーを設定することをお勧めします。

**入力パラメーター**

- **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター
- **ip_ptr** IP インスタンスへのポインター。
- **name_str** サーバー名へのポインター
- **packet_pool_ptr** サーバーのパケット プールへのポインター
- **stack_ptr** サーバーのスタック メモリへのポインター
- **stack_size** サーバーのスタック メモリのサイズ
- **dhcpv6_address_declined_handler** クライアントの拒否または解放メッセージ ハンドラーへのポインター
- **dhcpv6_option_request_handler** オプション要求オプション ハンドラーへのポインター

**戻り値**

- **NX_SUCCESS** (0x00) サーバーが正常に再開されました
- NX_PTR_ERROR (0x16) ポインターの入力が無効です
- NX_DHCPV6_PARAM_ERROR 無効なポインターではない入力です

**使用可能な場所**

アプリケーション コード

**例**

```
/* Create the DHCPv6 Server. */
status = nx_dhcpv6_server_create(&dhcp_server_0, &ip_0, "DHCPv6 Server",
         &pool_0, stack_pointer,2048, dhcpv6_decline_handler,
         dhcpv6_get_time_handler);
/* If status is NX_SUCCESS the Server successfully created. */
```

## <a name="nx_dhcpv6_server_delete"></a>nx_dhcpv6_server_delete

### <a name="delete-the-dhcpv6-server"></a>DHCPv6 サーバーを削除します

**プロトタイプ**

```
UINT _nx_dhcpv6_server_delee(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**説明**

このサービスを使用すると、DHCPv6 サーバー タスクと、サーバーによって処理されていたすべての要求が削除されます。

**入力パラメーター**

- **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター

**戻り値**

- **NX_SUCCESS** (0x00) サーバーが正常に削除されました
- NX_PTR_ERROR (0x16) ポインターの入力が無効です

**使用可能な場所**

Threads

**例**

```
/* Delete the DHCPv6 Serve. */
status = nx_dhcpv6_server_delete(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully deleted. */
```

## <a name="nx_dhcpv6_server_resume"></a>nx_dhcpv6_server_resume

### <a name="resume-dhcpv6-server-task"></a>DHCPv6 サーバー タスクを再開します 

**プロトタイプ**

```
UINT _nx_dhcpv6_server_resume(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**説明**

このサービスを使用すると、DHCPv6 サーバー タスクと、サーバーによって処理されていたすべての要求が再開されます。

**入力パラメーター**

- **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター

**戻り値**

- **NX_SUCCESS** (0x00) サーバーが正常に再開されました
- **NX_DHCPV6_ALREADY_STARTED** (0xE91) サーバーは既に実行されています
- **状態** (可変) ThreadX と NetX Duo のエラー ステータス
- NX_PTR_ERROR (0x16) ポインターの入力が無効です

**使用可能な場所**

Threads

**例**

```
/* Resume the DHCPv6 Server task. */
status = nx_dhcpv6_server_resume(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully resumed. */
```

## <a name="nx_dhcpv6_server_suspend"></a>nx_dhcpv6_server_suspend

### <a name="suspend-dhcpv6-server-task"></a>DHCPv6 サーバー タスクを一時停止します 

**プロトタイプ**

```
UINT _nx_dhcpv6_server_suspend(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**説明**

このサービスを使用すると、DHCPv6 サーバー タスクと、サーバーによって処理されていたすべての要求が一時停止されます。

**入力パラメーター**

- **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター

**戻り値**

- **NX_SUCCESS** (0x00) サーバーが正常に再開されました
- **NX_DHCPV6_NOT_STARTED** (0xE92) サーバーが開始されていません 
- **状態** (可変) ThreadX と Netx Duo のエラー ステータス
- NX_PTR_ERROR (0x16) ポインターの入力が無効です

**使用可能な場所**

Threads

**例**

```
/* Suspend the DHCPv6 Server task. */
status = nx_dhcpv6_server_suspend(&dhcp_server_0);

/* If status is NX_SUCCESS the Server successfully suspended. */
```

## <a name="nx_dhcpv6_server_start"></a>nx_dhcpv6_server_start

### <a name="start-the-dhcpv6-server-task"></a>DHCPv6 サーバー タスクを開始します 

**プロトタイプ**

```
UINT _nx_dhcpv6_server_start(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**説明**

このサービスを使用すると、DHCPv6 サーバー タスクが開始され、DHCPv6 クライアント メッセージを受信するためのアプリケーション要求を処理するようにサーバーが準備されます。 サーバー インスタンスに十分な情報 (サーバーの DUID) があることが確認され、DHCPv6 メッセージを送受信するための UDP ソケットが作成されてバインドされます。また、セッション時間と IP リースの有効期限を追跡するためのタイマーがアクティブ化されます。

>[!NOTE] 
> DHCPv6 サーバーを実行する前に、ホスト アプリケーションで、サーバーが IP アドレスを割り当てることができる IP アドレス範囲を作成する必要があります。 また、サーバーの DUID と DHCPv6 インターフェイスを設定する必要もあります (それぞれ、*nx_dhcpv6_server_duid_set* と *nx_dhcpv6_server_interface_set* を参照してください)。

**入力パラメーター**

- **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター

**戻り値**

- **NX_SUCCESS** (0x00) サーバーが正常に開始されました
- **NX_DHCPV6_ALREADY_STARTED** (0xE91) サーバーは既に実行されています
- **NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) リースのための割り当て可能なアドレスがサーバーにありません
- **NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) グローバル アドレス インデックスが設定されていません
- **NX_DHCPV6_NO_SERVER_DUID** (0xE92) サーバーの DUID が作成されていません 
- **状態** (可変) ThreadX と NetX Duo のエラー ステータス
- NX_PTR_ERROR (0x16) ポインターの入力が無効です

**使用可能な場所**

Threads

**例**

```
/* Start the DHCPv6 Server task. */
status = nx_dhcpv6_server_start(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_retrieve_ip_address_lease"></a>nx_dhcpv6_retrieve_ip_address_lease

### <a name="get-an-ip-address-lease-from-the-server-table"></a>サーバー テーブルから IP アドレスのリースを取得します

**プロトタイプ**

```
UINT _nx_dhcpv6_retrieve_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, 
     NXD_ADDRESS *lease_IP_address, ULONG *T1, ULONG *T2, 
     ULONG *valid_lifetime, ULONG *preferred_lifetime)
```

**説明**

このサービスを使用すると、サーバー テーブルの指定したテーブル インデックス位置にある IP アドレス リース レコードが取得されます。 これは、クライアント レコード データを取得する前でも後でも行うことができます。

DHCPv6 サーバーと不揮発性メモリの間でデータの格納と取得を行う機能は、DHCPv6 プロトコルの要件です。 IP リース データとクライアント レコード データを不揮発性メモリに保存する順序は重要ではありません。

>[!NOTE] 
> サーバー テーブルに、またはサーバー テーブルからデータをコピーするときは、最初に DHCPv6 サーバーを停止または一時停止することをお勧めします。

**入力パラメーター**

- **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター
- **table_index** リースを格納するテーブル インデックス
- **lease_IP_address** クライアントにリースする IP アドレスへのポインター
- **T1** クライアントが要求した更新時間
- **T2** クライアントが要求した再バインド時間
- **valid_lifetime** クライアント リースが非推奨になります
- **preferred_lifetime** クライアント リースが無効になります

**戻り値**

- **NX_SUCCESS** (0x00) サーバーが正常に開始されました
- **NX_DHCPV6_PARAMETER_ERROR** (0xE93) 無効な IP リース データ入力
- NX_PTR_ERROR (0x16) ポインターの入力が無効です

**使用可能な場所**

アプリケーション コード

**例**

```
/* Retrieve the DHCPv6 Server lease data. */
For (I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
{
    /* Get the next lease record. */
    status = nx_dhcpv6_server_startdhcpv6_server_ptr, i, &next_ipv6_address, &T1,
             &T2, &preferred_lifetime, &valid_lifetime);
    /* The host application then saves this record to memory.
}
/* If status is NX_SUCCESS the Server data is successfully downloaded. */
```

## <a name="nx_dhcpv6_add_ip_address_lease"></a>nx_dhcpv6_add_ip_address_lease

### <a name="add-an-ip-address-lease-to-the-server-table"></a>サーバー テーブルに IP アドレスのリースを追加します

**プロトタイプ**

```
UINT _nx_dhcpv6_add_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, NXD_ADDRESS *lease_IP_address, ULONG T1, ULONG T2, 
     ULONG valid_lifetime, ULONG preferred_lifetime)
```

**説明**

このサービスを使用すると、前の DHCPv6 サーバー セッションの IP リース データが、不揮発性メモリからサーバー リース テーブルに読み込まれます。 サーバーが初めて実行され、以前のリース データがない場合、これは必要ありません。 ホスト アプリケーションで IP アドレスを割り当てるための IP アドレス範囲を作成する必要がある場合は、*nx_dhcpv6_create_ip_address_range* サービスを使用します。 データは、DHCPv6 リース レコードを再構築するのに十分です。 テーブル インデックスを指定する必要はありません。 0xFFFFFFFF (無限大) に設定すると、データのコピー先として使用可能な次のスロットが DHCPv6 サーバーによって検出されます。

>[!NOTE] 
> クライアント レコードをアップロードする前に、IP リース データをアップロードする必要があります。どちらも、DHCPv6 サーバーを開始または再開する前に行う必要があります。

DHCPv6 サーバーと不揮発性メモリの間でデータの格納と取得を行う機能は、DHCPv6 プロトコルの要件です。

**入力パラメーター**

- **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター
- **table_index** リースを格納するテーブル インデックス
- **lease_IP_address** クライアントにリースする IP アドレスへのポインター
- **T1** クライアントが要求した更新時間
- **T2** クライアントが要求した再バインド時間
- **valid_lifetime** クライアント リースが非推奨になります
- **preferred_lifetime** クライアント リースが無効になります

**戻り値**

- **NX_SUCCESS** (0x00) サーバーが正常に開始されました
- **NX_DHCPV6_TABLE_FULL** (0xEC4) リース データを増やすための空き領域がありません**
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) リース データがサーバー DHCPV6 インターフェイスとのリンク上にないようです
- **NX_DHCPV6_PARAM_ERROR** (0xE93) 無効な IP リース データ入力
- NX_PTR_ERROR (0x16) ポインターの入力が無効です

**使用可能な場所**

アプリケーション コード

**例**

```
/* Copy the IP lease data to the Server address table. Note that the table index
is defaulted to 0xFFFFFFFF meaning the DHCPv6 Server will find an empty slot 
for each lease. */

    For(I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
    {
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr, 0xFFFFFFFF,
                 &next_ipv6_address, &T1, &T2, &preferred_lifetime, &valid_lifetime);
        /* Get the next lease address from memory… */
    }
    
    /* If status is NX_SUCCESS the lease data was successfully uploaded. It is opk
    to add the Client records to the Server table now. */
```

## <a name="nx_dhcpv6_add_client_record"></a>nx_dhcpv6_add_client_record

### <a name="add-a-client-record-to-the-server-table"></a>クライアント レコードをサーバー テーブルに追加します

**プロトタイプ**

```
UINT _nx_dhcpv6_add_client_record(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG message_xid, 
     NXD_ADDRESS *client_address, UINT client_state, 
     ULONG IP_lease_time_accrued, ULONG valid_lifetime, UINT duid_type, UINTduid_hardware, 
     ULONG physical_address_msw, ULONG physical_address_lsw, ULONG duid_time, 
     ULONG duid_vendor_number, UCHAR *duid_vendor_private, UINT duid_private_length)
```

**説明**

このサービスを使用すると、不揮発性メモリからサーバー テーブルに、クライアント データが一度に 1 レコードずつコピーされます。 これは、サーバーが再起動されていて、前のセッションのクライアント データをメモリから復元する場合にのみ必要です。 サーバーに前のデータがない場合、クライアント テーブルはクライアント レコードを追加できるように DHCPv6 サーバーによって初期化されます。

テーブル インデックスを指定する必要はありません。 0xFFFFFFFF (無限大) に設定すると、次に使用可能なスロットが DHCPv6 サーバーによって検出されます。 DHCPv6 サーバーにより、このデータからクライアント レコードを再構築できます。

>[!NOTE] 
> ホスト アプリケーションでは、クライアント レコード データの前に、IP リース データをアップロードする必要があります。 これは、各クライアント レコードがそれぞれのテーブルの対応する IP リース レコードと結合されるように、DHCPv6 サーバーで内部的にテーブルをクロスリンクできるようにするためです。 メモリから IP リース データをアップロードする方法の詳細については、*nx_dhcpv6_add_ip_address_lease* を参照してください。

>[!NOTE] 
> DUID の種類によっては、すべてのデータを指定する必要はありません。 たとえば、ベンダーによって割り当てられた DUID の種類がクライアントにある場合、DUID リンク レイヤー パラメーターに対して 0 を送信できます (MAC アドレス、ハードウェアの種類、DUID 時間)。

DHCPv6 サーバーと不揮発性メモリの間でデータの格納と取得を行う機能は、DHCPv6 プロトコルの要件です。

**入力パラメーター**

- **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター

**戻り値**

- **NX_SUCCESS** (0x00) サーバーが正常に開始されました
- **NX_INVALID_PARAMETERS** (0x4D) ポインターではない無効な値の入力**
- **NX_DHCPV6_TABLE_FULL** (0xEC4) 別のクライアント レコードを追加するための空のスロットが残っていません
- **NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) クライアントによって割り当てられたアドレスがサーバー リース テーブルに見つかりません。
- NX_PTR_ERROR (0x16) ポインターの入力が無効です

**使用可能な場所**

アプリケーション コード

**例**

```
/*Add the IP lease data and Client records back to the server before starting
theServer. */
    /* Copy the 'lease data' to the server table FIRST. */
for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {

        /* Add the next lease record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr,
                 0xFFFFFFFF,,&next_ipv6_address, NX_DHCPV6_DEFAULT_T1_TIME, 
                 NX_DHCPV6_DEFAULT_T2_TIME, NX_DHCPV6_DEFAULT_PREFERRED_TIME, 
                 NX_DHCPV6_DEFAULT_VALID_TIME);
if (status != NX_SUCCESS)
return status;
        /* Get the next IP lease record from memory. */
        …
    }
    /* Copy the client records to the Server table NEXT.
    for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {
        /* Add the next client record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_client_record(dhcpv6_server_ptr, 0xFFFFFFFF,
                 message_xid, &client_ipv6_address, NX_DHCPV6_STATE_BOUND,
                 IP_lifetime_time_accrued, valid_lifetime, duid_type, 
                 duid_hardware, physical_address_msw, physical_address_lsw, 
                 duid_time, 0, NX_NULL, 0);
if (status != NX_SUCCESS)
return status;
        /* Get the next Client record from memory. */
        …
    }

/* If status is NX_SUCCESS the Server data was successfully restored and 
it is ok to start the DHCPv6 server now. */
```

## <a name="nx_dhcpv6_retrieve_client_record"></a>nx_dhcpv6_retrieve_client_record

### <a name="retrieve-a-client-record-from-the-server-table"></a>サーバー テーブルからクライアント レコードを取得します

**プロトタイプ**

```
UINT _nx_dhcpv6_retrieve_client_record(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG *message_xid, 
     NXD_ADDRESS *client_address, UINT *client_state, 
     ULONG IP_lease_time_accrued, 
     ULONG *valid_lifetime, UINT *duid_type, 
     UINT *duid_hardware, ULONG *physical_address_msw, 
     ULONG *physical_address_lsw, ULONG *duid_time, 
     ULONG *duid_vendor_number, 
     UCHAR *duid_vendor_private, 
     UINT *duid_private_length)
```

**説明**

このサービスを使用すると、記憶域用のサーバーのクライアント レコード テーブルから不揮発性メモリに重要なデータがコピーされます。 サーバーで、逆のプロセスでこのようなデータから適切なクライアント レコードを再構築できます(サーバー テーブルにデータをアップロードする)。 DUID の種類に関係なく、ポインターを NULL ポインターにすることはできません。すべてのパラメーターについて、データは 0 に初期化されます。 たとえば、クライアントの DUID の種類がリンク レイヤー + 時間の場合、ベンダー番号はゼロとして返され、プライベート ID は空の文字列になります。

DHCPv6 サーバーと不揮発性メモリの間でデータの格納と取得を行う機能は、DHCPv6 プロトコルの要件です。 IP リース データとクライアント レコード データを不揮発性メモリに保存する順序は重要ではありません。

>[!NOTE] 
> サーバー テーブルに、またはサーバー テーブルからデータをコピーするときは、最初に DHCPv6 サーバーを停止または一時停止することをお勧めします。

**入力パラメーター**

- **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター
- **table_index** サーバーのクライアント テーブルへのインデックス
- **message_xid** クライアント サーバーのトランザクション ID
- **client_address** クライアントにリースされた IPv6 アドレス
- **client_state** クライアントの DHCPv6 の状態 (例: バインド)
- **IP_lease_time_accrued** リースで既に切れている有効期限 **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター
- **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター

**戻り値**

- **NX_SUCCESS** (0x00) サーバーが正常に開始されました
- **NX_DHCPV6_INVALID_DUID** (0xECC) 無効または矛盾する DUID データ
- **NX_PTR_ERROR** (0x16) ポインターの入力が無効です
- NX_INVALID_PARAMETERS (0x4D) ポインターではない無効な値の入力

**使用可能な場所**

アプリケーション コード

**例**

```
/* Retrieve the Client records from the DHCPv6 Server table. */
For (i = 0; i< NX_MAX_DHCPV6_CLIENTS; i++)
{
    status = nx_dhcpv6_retrieve_client_recorddhcpv6_server_ptr, i, &message_xid,
             &client_ipv6_address, &client_state, &IP_lifetime_time_accrued, 
             valid_lifetime, &duid_type, &duid_hardware, &physical_address_msw,
             &physical_address_lsw, &duid_time, &duid_vendor_number, &private_id[0], 
             &length);
    /* The host application can save this data to memory now.
}
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_server_interface_set"></a>nx_dhcpv6_server_interface_set

### <a name="setthe-interface-index-for-server-dhcpv6-interface"></a>サーバー DHCPv6 インターフェイスのインターフェイス インデックスを設定します

**プロトタイプ**

```
UINT _nx_dhcpv6_server_interface_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT iface_index, UINT ga_address_index)
```

**説明**

このサービスを使用すると、DHCPv6 サーバーによって DHCPv6 クライアント要求が処理されるネットワーク インターフェイスが設定されます。 マルチホームがサポートされていない NetX Duo のバージョンでは、インターフェイスの値は既定で 0 になることに注意してください。 DHCPv6 インターフェイスでサーバー グローバル アドレスを取得するには、グローバル アドレス インデックスが必要です。 これは、リース アドレスと他の DHCPv6 データが DHCPv6 サーバーとのリンク上にあることを確認するるために、DHCPv6 のロジックによって使用されます。

シングルホーム デバイス上のアプリケーションや、マルチホームのサポートがないアプリケーションでも、DHCPv6 サーバーが開始される前に、これを呼び出す必要があります。

**入力パラメーター**

- **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター
- **iface_index** サーバーの DHCPv6 サーバー インターフェイス
- **ga_address_index** サーバーの IP インスタンス アドレス テーブル内のサーバー グローバル アドレスのインデックス

**戻り値**

- **NX_SUCCESS** (0x00) サーバーが正常に開始されました
- **NX_INVALID_INTERFACE** (0x4C) インターフェイスが存在しません
- NX_NO_INTERFACE_ADDRESS (0x50) グローバル インデックスが、IP インスタンスの最大 IPv6 アドレス (NX_MAX_IPV6_ADDRESSES) を超えています
- NX_PTR_ERROR (0x16) ポインターの入力が無効です

**使用可能な場所**

アプリケーション コード

**例**

```
/* Set the Server DHCPv6 interface to the primary interface. The global IP 
address is at the index 1 in the IP address table. */
status = nx_dhcpv6_server_interface_set(&dhcp_server_0, 0, 1);

/* If status is NX_SUCCESS the Server interface is successfully set. */
```
## <a name="nx_dhcpv6_set_server_duid"></a>nx_dhcpv6_set_server_duid

### <a name="set-the-server-duid-for-dhcpv6-packets"></a>DHCPv6 パケットのサーバー DUID を設定します

**プロトタイプ**

```
UINT _nx_dhcpv6_set_server_duid(NX_DHCPV6_SERVER *dhcpv6_server_ptr,
     UINT duid_type, UINT hardware_type, 
     ULONG mac_address_msw, ULONG mac_address_lsw, 
     ULONG time)
```

**説明**

このサービスを使用すると、サーバーの DUID が設定されます。ホスト アプリケーションによってサーバーが起動される前に、このサービスを呼び出す必要があります。 リンク レイヤーとリンク レイヤー時間の DUID の種類の場合、ホスト アプリケーションでハードウェアの種類と MAC アドレスのデータを指定する必要があります。 リンク レイヤー時間の DUID の場合、時刻ポインターは有効な時間を指している必要があります。 2000 年 1 月 1 日からの秒数が、一般的なシード値です。 サーバーの DUID の種類がエンタープライズまたはベンダーによる割り当ての種類の場合、DUID はユーザーが構成可能なオプション NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID と NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID から作成され、時間と MAC アドレスの値は NULL に設定できます。

>[!NOTE] 
> 再起動の前後で、同じ DUID がクライアントへのメッセージで使用されように、サーバーの DUID パラメーターを不揮発性メモリに保存するのは、ホスト アプリケーションの責任です。 これは、DHCPv6 プロトコルの要件です (RFC 3315)。

**入力パラメーター**

- **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター
- **duid_type** DHCPv6 サーバーの DUID の種類
- **hardware_type** ハードウェアの種類 (例: イーサネット)
- **mac_address_msw** DHCPv6 サーバーへのポインター
- **mac_address_lsw** DHCPv6 サーバーへのポインター
- **time** DUID の時刻値

**戻り値**

- **NX_SUCCESS** (0x00) サーバーは正常に一時停止されました
- **NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) 不明またはサポートされていない DUID の種類
- **NX_INVALID_PARAMETERS** (0x4D) ポインターではない無効な値の入力
- NX_PTR_ERROR (0x16) ポインターの入力が無効です

**使用可能な場所**

アプリケーション コード

**例**

```
/* Set the DHCPv6 ServerDUID as Link layer plus time, over Ethernet hardware. */
duid_time = SECONDS_SINCE_JAN_1_2000_MOD_32 + rand();

status = nx_dhcpv6_set_server_duid(&dhcp_server_0,1, 0x6,
         physical_address_msw,physical_address_lsw,duid_time);

/* If status is NX_SUCCESS the ServerDUID is successfully set. */
```

## <a name="nx_dhcpv6_server_option_request_handler_set"></a>nx_dhcpv6_server_option_request_handler_set

### <a name="set-the-option-request-handler-for-dhcpv6-server-instance"></a>DHCPv6 サーバー インスタンスのオプション要求ハンドラーを設定します 

**プロトタイプ**

```
UINT nx_dhcpv6_server_option_request_handler_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     VOID (*dhcpv6_option_request_handler_extended)(
          struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
          UINT option_request, UCHAR *buffer_ptr, 
          UINT *index, UINT available_payload));
```

**説明**

このサービスを使用すると、DHCPv6 サーバー拡張オプション要求ハンドラーが設定されます。

**入力パラメーター**

- **dhcpv6_server_ptr** DHCPv6 サーバーへのポインター
- **dhcpv6_option_request_handler_extended** 拡張オプション要求ハンドラーへのポインター

**戻り値**

- **NX_SUCCESS** (0x00) サーバーが正常に再開されました
- NX_PTR_ERROR (0x16) ポインターの入力が無効です

**使用可能な場所**

アプリケーション コード

**例**

```
/* Set the option request handler for DHCPv6 Server. */
status = nx_dhcpv6_server_option_request_handler_set(&dhcp_server_0,
         dhcpv6_option_request_handler_extended);

/* If status is NX_SUCCESS the extended handler successfully set. */
```