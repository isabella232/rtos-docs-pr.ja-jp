---
title: 第 3 章 - Azure RTOS NetX DNS クライアント サービスの説明
description: この章では、すべての Azure RTOS NetX DNS サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 922d41dc374ccd782809404776f18f2aed8f5e3c34b7c9e143075c0ee5567220
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782492"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dns-client-services"></a>第 3 章 - Azure RTOS NetX DNS クライアント サービスの説明

この章では、すべての Azure RTOS NetX DNS サービス (以下に記載) をアルファベット順に説明します。

以下の API の説明の「戻り値」セクションで、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字でない値は完全に無効になります。

- **nx_dns_authority_zone_start_get**: "*指定されたホスト名に関連付けられている権威のゾーンの開始を検索する*"
- **nx_dns_cache_initialize**: "*DNS キャッシュを初期化する。* "
- **nx_dns_cache_notify_clear**: "*キャッシュ満杯通知関数をクリアする。* "
- **nx_dns_cache_notify_set**: "*キャッシュ満杯通知関数を設定する。* "
- **nx_dns_cname_get**: "*入力ドメイン名の別名に対応する正規のドメイン名を検索する*"
- **nx_dns_create**: "*DNS クライアント インスタンスを作成する*"
- **nx_dns_delete**: "*DNS クライアント インスタンスを削除する*"
- **nx_dns_domain_name_server_get**: "*入力ドメイン ゾーンの権威ネーム サーバーを検索する*"
- **nx_dns_domain_mail_exchange_get**: "*指定されたホスト名に関連付けられているメール交換を検索する。* "
- **nx_dns_domain_service_get**: "*指定されたホスト名に関連付けられているサービスを検索する*"
- **nx_dns_get_serverlist_size**: "*DNS クライアントのサーバー リストのサイズを返す*"
- **nx_dns_info_by_name_get**: "*入力ホスト名のクエリを実行して IP アドレスとポートを返す*"
- **nx_dns_ipv4_address_by_name_get**: "*指定されたホスト名から IPv4 アドレスを検索する*"
- **nx_dns_host_by_address_get**: "*指定された IP アドレスからホスト名を検索する*"
- **nx_dns_host_by_name_get**: "*指定されたホスト名から IPv4 アドレスを検索する*"
- **nx_dns_host_text_get**: "*入力ドメイン名のテキスト データを検索する*"
- **nx_dns_packet_pool_set**: "*DNS クライアントのパケット プールを設定する*"
- **nx_dns_server_add**: "*指定されたアドレスの DNS サーバーをクライアントのリストに追加する*"
- **nx_dns_server_get**: "*クライアントのリスト内の DNS サーバーを返す*"
- **nx_dns_server_remove**: "*クライアントのリストから DNS サーバーを削除する*"
- **nx_dns_server_remove_all**: "*クライアント リストからすべての DNS サーバーを削除する*"

## <a name="nx_dns_authority_zone_start_get"></a>nx_dns_authority_zone_start_get

入力ホストの権威のゾーンの開始を検索する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);

```

### <a name="description"></a>説明

NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスは指定されたドメイン名で SOA タイプのクエリを送信して、入力ドメイン名の権威のゾーンの開始を取得します。 DNS クライアントは、DNS サーバー応答で返された SOA レコードを、*record_buffer* のメモリ位置にコピーします。 
>[!NOTE]
> データを受信するには、*record_buffer* が 4 バイト アラインされている必要があります。

NetX DNS クライアントでは、SOA レコード NX_DNS_SOA_ENTRY は、7 個の 4 バイトのパラメーター (合計 28 バイト) として保存されます。

- **nx_dns_soa_host_mname_ptr**: このゾーンのデータのプライマリ ソースへのポインター
- **nx_dns_soa_host_rname_ptr**: このゾーンに対応するメールボックスへのポインター
- **nx_dns_soa_serial**: ゾーンのバージョン番号
- **nx_dns_soa_refresh**: 更新間隔
- **nx_dns_soa_retry**: SOA クエリの再試行の間隔
- **nx_dns_soa_expire**: SOA の有効期限が切れるまでの期間
- **nx_dns_soa_minmum**: SOA ホスト名 DNS 応答メッセージの最小 TTL フィールド

2 つの SOA レコードの格納を次に示します。 固定長データを含む SOA レコードは、バッファーの先頭から入力が開始されます。 ポインター MNAME および RNAME は、バッファーの末尾に格納されている可変長データ (ホスト名) を指します。 最初のレコードの後に追加の SOA レコードが入力され ("additional SOA records…")、その可変長データが最後のエントリの可変長データ上に格納されます ("additional SOA variable length data")。

![2 つの S O A レコードの格納を表す図](media/image2.png)

入力 *record_buffer* にサーバー応答内のすべての SOA データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。

**record_count* で返された SOA レコードの数を使用して、アプリケーションは *record_buffer* からのデータを解析し、ホスト名文字列の権威のゾーンの開始を抽出できます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: DNS クライアントへのポインター。  
- **host_name**: SOA データを取得するホスト名へのポインター
- **record_buffer**: SOA データを抽出する場所へのポインター
- **buffer_size**: SOA データを保持するバッファーのサイズ
- **record_count**: 取得した SOA レコードの数へのポインター
- **wait_option**: DNS サーバー応答を受信する際の待機オプション

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) SOA データが正常に取得されました
- **NX_DNS_NO_SERVER**: (0xA1) クライアントのサーバー リストが空です
- **NX_DNS_QUERY_FAILED**: (0xA3) 有効な DNS 応答を受信していません
- NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です
- NX_DNS_PARAM_ERROR: (0xA8) 非ポインター入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```c
UCHAR                  record_buffer[50];
UINT                   record_count;   
NX_DNS_SOA_ENTRY       *nx_dns_soa_entry_ptr;

/* Request the start of authority zone(s) for the specified host.  */
status =  nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com",
                                          record _buffer, sizeof(record_buffer), 
                                          &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else 
{
/* If status is NX_SUCCESS a DNS query was successfully completed and SOA data is returned in soa_buffer.  */

/* Set a local pointer to the SOA buffer. */
    nx_dns_soa_entry_ptr = (NX_DNS_SOA_ENTRY *) record_buffer;
    
    printf("------------------------------------------------------\n");
    printf("Test SOA: \n");
    printf("serial = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_serial );
    printf("refresh = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_refresh );
    printf("retry = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_retry );
    printf("expire = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_expire );
    printf("minmum = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_minmum );
    
    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr)
    {
        printf("host mname = %s\n", 
               nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr);
    }
    else
    {
        printf("host mame is not set\n");
    }
    
    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr)
    {
        printf("host rname = %s\n", 
               nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr);
    }
    else
    {
     
        printf("host rname is not set\n");
    }
}

```

```Output
Test SOA:
serial = 2012111212
refresh = 7200
retry = 1800
expire = 1209600
minmum = 300
host mname = ns1.www.my_example.com
host rname = dns-admin.www.my_example.com
```


## <a name="nx_dns_cache_initialize"></a>nx_dns_cache_initialize

DNS キャッシュを初期化する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                             VOID *cache_ptr, UINT cache_size);

```
### <a name="description"></a>説明

このサービスは、DNS キャッシュを作成して初期化します。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: DNS 制御ブロックへのポインター。
- **cache_ptr**: DNS キャッシュへのポインター。
- **cache_size**: DNS キャッシュのサイズ (バイト単位)。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS キャッシュが正常に初期化されました
- NX_DNS_ERROR: (0xA0) キャッシュが 4 バイト アラインされていません。
- NX_DNS_PARAM_ERROR: (0xA8) DNS ID が無効です。
- NX_PTR_ERROR: (0x07) DNS ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```c
UCHAR          dns_cache [2048]; 

/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, dns_cache, 2048);
/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a>nx_dns_cache_notify_clear

DNS キャッシュ満杯通知関数をクリアする

### <a name="prototype"></a>プロトタイプ

```c
UINT     nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```
### <a name="description"></a>説明

このサービスは、キャッシュ満杯通知関数をクリアします。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: DNS 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS キャッシュ通知が正常に設定されました
- NX_DNS_PARAM_ERROR: (0xA8) DNS ID が無効です。
- NX_PTR_ERROR: (0x07) DNS ポインターが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Clear the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a>nx_dns_cache_notify_set

DNS キャッシュ満杯通知関数を設定する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr, VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a>説明

このサービスは、キャッシュ満杯通知関数を設定します。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: DNS 制御ブロックへのポインター。
- **cache_full_notify_cb**: キャッシュがいっぱいになったときに呼び出されるコールバック関数。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS キャッシュ通知が正常に設定されました
- NX_DNS_PARAM_ERROR: (0xA8) DNS ID が無効です。
- NX_PTR_ERROR: (0x07) DNS ポインターが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Set the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set.  */
 
```

## <a name="nx_dns_cname_get"></a>nx_dns_cname_get

入力ホスト名の正規名を検索する

### <a name="prototype"></a>プロトタイプ
```c
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                      UCHAR *record_buffer, UINT buffer_size, 
                      ULONG wait_option);
```

### <a name="description"></a>説明

*nx_dns.h* で NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスは、指定されたドメイン名で CNAME タイプのクエリを送信して正規のドメイン名を取得します。 DNS クライアントは、DNS サーバー応答で返された CNAME 文字列を、*record_buffer* のメモリ位置にコピーします。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: DNS クライアントへのポインター。  
- **host_name**: CNAME データを取得するホスト名へのポインター
- **record_buffer**: CNAME データを抽出する場所へのポインター
- **buffer_size**: CNAME データを保持するバッファーのサイズ
- **wait_option**: DNS サーバー応答を受信する際の待機オプション

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) CNAME データが正常に取得されました
- **NX_DNS_NO_SERVER**: (0xA1) クライアントのサーバー リストが空です
- **NX_DNS_QUERY_FAILED**: (0xA3) 有効な DNS 応答を受信していません
- NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です
- NX_DNS_PARAM_ERROR: (0xA8) 非ポインター入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
CHAR            record _buffer[50];

/* Request the canonical name for the specified host.  */
status =  nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                            record_buffer, sizeof(record_buffer), 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and the canonical host name is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test CNAME: %s\n", record_buffer);
} 
```

```Output
Test CNAME: **my_example**.com
```

## <a name="nx_dns_create"></a>nx_dns_create

DNS クライアント インスタンスを作成する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```

### <a name="description"></a>説明

このサービスでは、以前に作成された IP インスタンスの DNS クライアント インスタンスを作成します。

>[!NOTE]
>アプリケーションでは、DNS クライアントによって使用されるパケット プールのパケット ペイロードが、最大 512 バイトの DNS メッセージに加えて、UDP、IP、イーサネットの各ヘッダーを含めることができる十分な大きさであることを確認する必要があります。 DNS クライアントが独自のパケット プールを作成する場合、これは、NX_DNS_PACKET_POOL_SIZE と NX_DNS_PACKET_PAYLOAD で定義されます。 DNS クライアント アプリケーションが、以前に作成されたパケット プールを提供する場合、IPv4 DNS クライアントのペイロードは、DNS メッセージの最大サイズである 512 バイトに、IP ヘッダー用の 20 バイト、UDP ヘッダー用の 8 バイト、イーサネット ヘッダー用の 14 バイトを加えたサイズである必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: DNS クライアントへのポインター。  
- **ip_ptr**: 以前に作成された IP インスタンスへのポインター。  
- **domain_name**: DNS インスタンスのドメイン名へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS が正常に作成されました
- **NX_DNS_ERROR**: (0xA0) DNS 作成エラー
- NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Create a DNS Client instance.  */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created.  */
```
## <a name="nx_dns_delete"></a>nx_dns_delete

DNS クライアント インスタンスを削除する

### <a name="prototype"></a>プロトタイプ

```c
UINT     nx_dns_delete(NX_DNS *dns_ptr);
```

### <a name="description"></a>説明

このサービスは、以前に作成された DNS クライアント インスタンスを削除し、そのリソースを解放します。 
>[!NOTE]
> **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** が定義されており、DNS クライアントにユーザー定義のパケット プールが割り当てられている場合、DNS クライアントの不要になったパケット プールを削除するのはアプリケーションの役割です。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: 以前に作成された DNS **クライアント** インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS クライアントが正常に削除されました。
- NX_PTR_ERROR: (0x07) IP または DNS クライアント ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Delete a DNS Client instance.  */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted.  */
```
## <a name="nx_dns_domain_name_server_get"></a>nx_dns_domain_name_server_get

入力ドメイン ゾーンの権威ネーム サーバーを検索する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>説明

NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスは指定されたドメイン名で NS タイプのクエリを送信して、入力ドメイン名のネーム サーバーを取得します。 DNS クライアントは、DNS サーバー応答で返された NS レコードを、*record_buffer* のメモリ位置にコピーします。 

>[!NOTE]
>データを受信するには、*record_buffer* が 4 バイト アラインされている必要があります。

NetX DNS クライアントでは、NS データ型の NX_DNS_NS_ENTRY は、2 つの 4 バイトのパラメーターとして保存されます。

- **nx_dns_ns_ipv4_address**: ネーム サーバーの IPv4 アドレス
- **nx_dns_ns_hostname_ptr**: ネーム サーバーのホスト名へのポインター

次に示すバッファーには、4 つの NX_DNS_NS_ENTRY レコードが格納されています。 各エントリのホスト名文字列へのポインターは、バッファーの下半分にある対応するホスト名文字列を指します。

![4 つの N X D N S N S エントリ レコードが格納されたバッファーの図。](media/image3.png)

入力 *record_buffer* にサーバー応答内のすべての NS データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。

**record_count* で返された NS レコードの数を使用して、アプリケーションは *record_buffer* 内の各レコードの IP アドレスとホスト名を解析できます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: DNS クライアントへのポインター。  
- **host_name**: NS データを取得するホスト名へのポインター
- **record_buffer**: NS データを抽出する場所へのポインター
- **buffer_size**: NS データを保持するバッファーのサイズ
- **record_count**: 取得した NS レコードの数へのポインター
- **wait_option**: DNS サーバー応答を受信する際の待機オプション

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) NS データが正常に取得されました
- **NX_DNS_NO_SERVER**: (0xA1) クライアントのサーバー リストが空です
- **NX_DNS_QUERY_FAILED**: (0xA3) 有効な DNS 応答を受信していません
- NX_DNS_PARAM_ERROR: (0xA8) DNS ID が無効です。
- NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```c
#define RECORD_COUNT        10

ULONG                      record_buffer[50];
UINT                       record_count;          
NX_DNS_NS_ENTRY            *nx_dns_ns_entry_ptr[RECORD_COUNT];

/* Request the name server(s) for the specified host.  */
status =  nx_dns_domain_name_server_get(&client_dns, (UCHAR *)" www.my_example.com ",  
                                        record_buffer, sizeof(record_buffer),  
                                        &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and NS data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test NS: ");
    printf("record_count = %d \n", record_count);      

    /* Get the name server.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)(record_buffer + i * sizeof(NX_DNS_NS_ENTRY)); 

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address  >> 24,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 16 & 0xFF,                   
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 8 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address & 0xFF);
        if(nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr)
        {
            printf("hostname = %s\n", 
                    nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr);
        }
        else
            printf("hostname is not set\n");
    }
}
```

```Output
Test NS: record_count = 4 
record 0: IP address: 192.2.2.10
hostname = ns2.www.my_example.com
record 1: IP address: 192.2.2.11
hostname = ns1.www.my_example.com
record 2: IP address: 192.2.2.12
hostname = ns3.www.my_example.com
record 3: IP address: 192.2.2.13
hostname = ns4.www.my_example.com
```

## <a name="nx_dns_domain_mail_exchange_get"></a>nx_dns_domain_mail_exchange_get

入力ホスト名のメール交換を検索する

### <a name="prototype"></a>プロトタイプ
```c
UINT     nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                        VOID *record_buffer,                                        
                                        UINT buffer_size, 
                                        UINT *record_count, 
                                        ULONG wait_option);

```

### <a name="description"></a>説明

NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスは指定されたドメイン名で MX タイプのクエリを送信して、入力ドメイン名のメール交換を取得します。 DNS クライアントは、DNS サーバー応答で返された MX レコードを、*record_buffer* のメモリ位置にコピーします。

>[!NOTE]
>データを受信するには、*record_buffer* が 4 バイト アラインされている必要があります。

NetX DNS クライアントでは、メール交換レコード NX_DNS_MAIL_EXCHANGE_ENTRY は、4 つのパラメーター (合計 12 バイト) として保存されます。

- **nx_dns_mx_ipv4_address**: メール交換 IPv4 アドレス (4 バイト)
- **nx_dns_mx_preference**: 優先順位 (2 バイト)
- **nx_dns_mx_reserved0**: 予約済み (2 バイト)
- **nx_dns_mx_hostname_ptr**: メール交換サーバー ホスト名へのポインター (4 バイト)

4 つの MX レコードが格納されたバッファーを次に示します。 各レコードには、上記の一覧の固定長データが含まれています。 メール交換サーバー ホスト名へのポインターは、バッファーの下部にある対応するホスト名を指します。

![4 つの M X レコードが格納されたバッファーを示す図。](media/image4.png)

入力 *record_buffer* にサーバー応答内のすべての MX データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。

**record_countt* で返された MX レコードの数を使用して、アプリケーションは *record_buffer* 内の各レコードのメール ホスト名などの MX パラメーターを解析できます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: DNS クライアントへのポインター。  
- **host_name**: MX データを取得するホスト名へのポインター
- **record_buffer**: MX データを抽出する場所へのポインター
- **buffer_size**: MX データを保持するバッファーのサイズ
- **record_count**: 取得した MX レコードの数へのポインター
- **wait_option**: DNS サーバー応答を受信する際の待機オプション

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) MX データが正常に取得されました
- **NX_DNS_NO_SERVER**: (0xA1) クライアントのサーバー リストが空です
- **NX_DNS_QUERY_FAILED**: (0xA3) 有効な DNS 応答を受信していません
- NX_DNS_PARAM_ERROR: (0xA8) DNS ID が無効です。
- NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```c
#define           MAX_RECORD_COUNT 10

ULONG             record_buffer[50];
UINT              record_count;  
NX_DNS_MX_ENTRY  *nx_dns_mx_entry_ptr[MAX_RECORD_COUNT];        

/* Request the mail exchange data for the specified host.  */
status =  nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)" www.my_example.com ", 
                                          record_buffer, sizeof(record_buffer),   
                                          &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
       
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and MX data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test MX: ");
    printf("record_count = %d \n", record_count);      


    /* Get the mail exchange.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)(record_buffer + i * sizeof(NX_DNS_MX_ENTRY));   

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,                   
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);

        printf("preference = %d \n ", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);

        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
    }
}
```

```Output
Test MX: record_count = 5 
record 0: IP address: 192.2.2.10
preference = 40 
hostname = alt3.aspmx.l.www.my_example.com
record 1: IP address: 192.2.2.11
preference = 50 
hostname = alt4.aspmx.l.www.my_example.com
record 2: IP address: 192.2.2.12
preference = 10 
hostname = aspmx.l.www.my_example.com
record 3: IP address: 192.2.2.13
preference = 20 
hostname = alt1.aspmx.l.www.my_example.com
record 4: IP address: 192.2.2.14
preference = 30 
hostname = alt2.aspmx.l.www.my_example.com
```


## <a name="nx_dns_domain_service_get"></a>nx_dns_domain_service_get

入力ホスト名で提供されるサービスを検索する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>説明

NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスは指定されたドメイン名で SRV タイプのクエリを送信して、指定されたドメインに関連付けられているサービスとそのポート番号を検索します。 DNS クライアントは、DNS サーバー応答で返された SRV レコードを、*record_buffer* のメモリ位置にコピーします。 

>[!NOTE]
>データを受信するには、*record_buffer* が 4 バイト アラインされている必要があります。

NetX DNS クライアントでは、サービス レコード NX_DNS_SRV_ ENTRY は、6 個のパラメーター (合計 16 バイト) として保存されます。 これにより、可変長の SRV データをメモリ効率の高い方法で格納できます。

- **サーバー IPv4 アドレス**: nx_dns_srv_ipv4_address (4 バイト)
- **サーバーの優先順位**: nx_dns_srv_priority (2 バイト)
- **サーバーの重み**: nx_dns_srv_weight (2 バイト)
- **サービス ポート番号**: nx_dns_srv_port_number (2 バイト)
- **4 バイト アラインメント用に予約済み**: nx_dns_srv_reserved0 (2 バイト)
- **サーバー ホスト名へのポインター**: *nx_dns_srv_hostname_ptr (4 バイト)

指定されたバッファーに 4 つの SRV レコードが格納されています。 各 NX_DNS_SRV_ENTRY レコードには、レコード バッファーの下部にある対応するホスト名文字列を指すポインター *nx_dns_srv_hostname_ptr* が含まれています。

![指定されたバッファーに格納されている 4 個の S R V レコードの図。](media/image5.png)

入力 *record_buffer* にサーバー応答内のすべての SRV データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。

**record_count* で返された SRV レコードの数を使用して、アプリケーションは *record_buffer* 内の各レコードのサーバー ホスト名などの SRV パラメーターを解析できます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: DNS クライアントへのポインター。  
- **host_name**: SRV データを取得するホスト名へのポインター
- **record_buffer**: SRV データを抽出する場所へのポインター
- **buffer_size**: SRV データを保持するバッファーのサイズ
- **record_count**: 取得した SRV レコードの数へのポインター
- **wait_option**: DNS サーバー応答を受信する際の待機オプション

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) SRV データが正常に取得されました
- **NX_DNS_NO_SERVER**: (0xA1) クライアントのサーバー リストが空です
- **NX_DNS_QUERY_FAILED**: (0xA3) 有効な DNS 応答を受信していません
- NX_DNS_PARAM_ERROR: (0xA8) DNS ID が無効です。
- NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
#define MAX_RECORD_COUNT  10

UCHAR                  record_buffer[50];
UINT                   record_count;
NX_DNS_SRV_ENTRY       *nx_dns_srv_entry_ptr[MAX_RECORD_COUNT];

/* Request the service(s) provided by the specified host.  */
status =  nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                    record_buffer, sizeof(record_buffer), 
                                    &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SRV data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test SRV: ");
    printf("record_count = %d \n", record_count);      

       
    /* Get the location of services.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)(record_buffer + i * sizeof(NX_DNS_SRV_ENTRY)); 

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 24,
        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 16 & 0xFF,                   
        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 8 & 0xFF,
        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address & 0xFF);

       printf("port number = %d\n", 
               nx_dns_srv_entry_ptr[i] -> nx_dns_srv_port_number );
               printf("priority = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_priority );
       printf("weight = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_weight );

       if(nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr)
       {
            printf("hostname = %s\n", 
            nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr);
        }
       else
            printf("hostname is not set\n");
    }
}
```

```Output
Test SRV: record_count = 3 
record 0: IP address: 192.2.2.10
port number = 5222
priority = 20
weight = 0
hostname = alt4.xmpp.l.www.my_example.com
record 1: IP address: 192.2.2.11
port number = 5222
priority = 5
weight = 0
hostname = xmpp.l.www.my_example.com
record 2: IP address: 192.2.2.12
port number = 5222
priority = 20
weight = 0
hostname = alt1.xmpp.l.www.my_example.com
```

## <a name="nx_dns_get_serverlist_size"></a>nx_dns_get_serverlist_size

DNS クライアントのサーバー リストのサイズを返す

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```

### <a name="description"></a>説明

このサービスは、クライアントのリスト内の有効な DNS サーバーの数を返します。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: DNS 制御ブロックへのポインター  
- **size**: リスト内のサーバーの数を返します

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS サーバー リストのサイズが正常に返されました
- NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list.  */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned.  */
```

## <a name="nx_dns_info_by_name_get"></a>nx_dns_info_by_name_get

ホスト名に基づいて DNS サーバーの IP アドレスとポートを返す

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスは、DNS クエリによる入力ホスト名に基づいて、サーバーの IP とポート (サービス レコード) を返します。 サービス レコードが見つからない場合、このルーチンは入力アドレス ポインターに 0 の IP アドレスを返し、0 以外のエラー状態を返してエラーを通知します。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: DNS 制御ブロックへのポインター  
- **host_name**: ホスト名バッファーへのポインター
- **host_address_ptr**: 返されるアドレスへのポインター
- **host_port_ptr**: 返されるポートへのポインター wait_option: DNS 応答の待機オプション

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS サーバー レコードが正常に返されました
- **NX_DNS_NO_SERVER**: (0xA1) ホスト名のクエリを送信するためにクライアントに登録されている DNS サーバーがありません
- **NX_DNS_QUERY_FAILED**: (0xA3) DNS クエリが失敗しました。クライアントのリストに DNS サーバーからの応答がないか、入力ホスト名で使用できるサービス レコードがありません。
- NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```c
ULONG         ip_address;
USHORT         port;

/* Attempt to resolve the IP address and ports for this host name.  */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned.  */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a>nx_dns_ipv4_address_by_name_get

入力ホスト名の IPv4 アドレスを検索する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                       UCHAR *host_name_ptr, VOID *buffer, 
                                       UINT buffer_size, 
                                       UINT *record_count,
                                       ULONG wait_option);
```

### <a name="description"></a>説明

このサービスは、指定されたホスト名で A タイプのクエリを送信して、入力ホスト名の IP アドレスを取得します。 DNS クライアントは、DNS サーバー応答で返された A レコードの IPv4 アドレスを、*record_buffer* のメモリ位置にコピーします。 

>[!NOTE]
>データを受信するには、*record_buffer* が 4 バイト アラインされている必要があります。

次に示すように、4 バイト アラインされたバッファーに複数の IPv4 アドレスが格納されています。

![4 バイト アラインされたバッファーに格納されている複数の I P v 4 アドレスの図。](media/image6.png)

指定されたバッファーにすべての IP アドレス データを保持できない場合、残りの A レコードは *record_buffer* に格納されません。 これにより、アプリケーションは、サーバー応答の使用可能な IP アドレス データの 1 つ、一部、またはすべてを取得できます。

**record_count* で返される A レコードの数を使用して、アプリケーションは *record_buffer* 内の IPv4 アドレス データを解析できます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: DNS クライアントへのポインター。  
- **host_name_ptr**: IPv4 アドレスを取得するホスト名へのポインター buffer: IPv4 データを抽出する場所へのポインター
- **buffer_size**: IPv4 データを保持するバッファーのサイズ
- **wait_option**: DNS サーバー応答を受信する際の待機オプション

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) IPv4 データが正常に取得されました
- **NX_DNS_NO_SERVER**: (0xA1) クライアントのサーバー リストが空です
- **NX_DNS_QUERY_FAILED**: (0xA3) 有効な DNS 応答を受信していません
- NX_DNS_PARAM_ERROR: (0xA8) 入力パラメーターが無効です
- NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
#define MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
ULONG           *ipv4_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host.  */
status =  nx_dns_ipv4_address_by_name_get(&client_dns, 
                                          (UCHAR *)"www.my_example.com",  
                                           record_buffer,                  
                                           sizeof(record_buffer),&record_count,                
                                           500);

        /* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed the IPv4 address(es) is returned in record_buffer.  */
    printf("------------------------------------------------------\n");
    printf("Test A: ");
    printf("record_count = %d \n", record_count);      


    /* Get the IPv4 addresses of host.  */
    for(i =0; i< record_count; i++)
    {
        ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG)); 
        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                *ipv4_address_ptr[i] >> 24,
                *ipv4_address_ptr[i] >> 16 & 0xFF,                   
                *ipv4_address_ptr[i] >> 8 & 0xFF,
                *ipv4_address_ptr[i] & 0xFF);
    }
}
```

```Output
------------------------------------------------------
Test A: record_count = 5 
record 0: IP address: 192.2.2.10
record 1: IP address: 192.2.2.11
record 2: IP address: 192.2.2.12
record 3: IP address: 192.2.2.13
record 4: IP address: 192.2.2.14
```

## <a name="nx_dns_host_by_address_get"></a>nx_dns_host_by_address_get

IP アドレスからホスト名を検索する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a>説明

このサービスは、アプリケーションによって以前に指定された 1 つ以上の DNS サーバーに、指定された IP アドレスの名前解決を要求します。 成功すると、*host_name_ptr* で指定された文字列で、NULL で終わるホスト名が返されます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: 以前に作成された DNS インスタンスへのポインター。
- **ip_address**: 名前に解決する IP アドレス
- **host_name_ptr**: ホスト名の宛先領域へのポインター
- **max_host_name_size**: ホスト名の宛先領域のサイズ
- **wait_option**: 各 DNS クエリおよびクエリ再試行の後に、サービスが DNS サーバーの応答を待機する時間をタイマー刻みで定義します。待機オプションは次のように定義されています。
    - **タイムアウト値**: (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択すると、DNS 解決を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、DNS サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS 解決が成功しました  
- **NX_DNS_TIMEOUT**: (0xA2) DNS ミューテックスの取得がタイムアウトしました
- **NX_DNS_NO_SERVER**: (0xA1) DNS サーバー アドレスが指定されていません
- **NX_DNS_QUERY_FAILED**: (0xA3) クエリの応答を受信しませんでした
- **NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) 入力アドレスが Null です
- **NX_DNS_INVALID_ADDRESS_TYPE**: (0xB2) インデックスが無効なアドレスの種類 (IPv6 など) を指しています
- **NX_DNS_PARAM_ERROR**: (0xA8) 非ポインター入力が無効です
- NX_PTR_ERROR: (0x07) ポインター入力が無効です
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */

```

## <a name="nx_dns_host_by_name_get"></a>nx_dns_host_by_name_get

ホスト名から IP アドレスを検索する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスは、アプリケーションによって以前に指定された 1 つ以上の DNS サーバーに、*host_name* が指す指定された名前の名前解決を要求します。 成功すると、関連付けられた IP アドレスが、*host_address_ptr* が指す宛先に返されます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: 以前に作成された DNS インスタンスへのポインター。
- **host_name**: ホスト名へのポインター
- **host_address_ptr**: DNS ホストの IP アドレスへのポインター
- **wait_option**: このサービスが DNS 解決を待機する時間を定義します。 この待機オプションは次のように定義されます。
    - **タイムアウト値**: (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択すると、DNS 解決を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、DNS サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS 解決が成功しました
- **NX_DNS_NO_SERVER**: (0xA1) DNS サーバー アドレスが指定されていません
- **NX_DNS_QUERY_FAILED**: (0xA3) クエリの応答を受信しませんでした
- NX_DNS_PARAM_ERROR: (0xA8) 非ポインター入力が無効です
- NX_PTR_ERROR: (0x07) ポインター入力が無効です
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```c
ULONG ip_address;

    /* Get the IP address for the name “www.my_example.com”.  */
    status =  nx_dns_host_by_name_get(&my_dns, “www.my_example.com”, &ip_address, 4000);

    /* Check for DNS query error.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else     
    {

    /* If status is NX_SUCCESS the IP address for “www.my_example.com” can be found in the “ip_address” variable.  */
        
        printf("------------------------------------------------------\n");
        printf("Test A: \n");
        printf("IP address: %d.%d.%d.%d\n",
                host_ip_address >> 24,
                host_ip_address >> 16 & 0xFF,                   
                host_ip_address >> 8 & 0xFF,
                host_ip_address & 0xFF);
    }
```

```Output
Test A: 
IP address: 192.2.2.10
```

## <a name="nx_dns_host_text_get"></a>nx_dns_host_text_get

入力ドメイン名のテキスト文字列を検索する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスでは、指定されたドメイン名とバッファーを使用して TXT タイプのクエリを送信し、任意の文字列データを取得します。

DNS クライアントは、DNS サーバー応答の TXT レコードのテキスト文字列を、*record_buffer* のメモリ位置にコピーします。 

>[!NOTE]
>データを受信するために、*record_buffer* が 4 バイト アラインされている必要はありません。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: DNS クライアントへのポインター。  
- **host_name**: 検索を実行するホストの名前へのポインター
- **record_buffer**: TXT データを抽出する場所へのポインター
- **buffer_size**: TXT データを保持するバッファーのサイズ
- **wait_option**: DNS サーバー応答を受信する際の待機オプション

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) TXT 文字列が正常に取得されました
- **NX_DNS_NO_SERVER**: (0xA1) クライアントのサーバー リストが空です
- **NX_DNS_QUERY_FAILED**: (0xA3) 有効な DNS 応答を受信していません
- NX_PTR_ERROR: (0x07) ポインター入力が無効です
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です
- NX_DNS_PARAM_ERROR: (0xA8) 非ポインター入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
CHAR            record_buffer[50];

/* Request the text string for the specified host.  */
status =  nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                record_buffer, 
                                sizeof(record_buffer), 500);


/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
     error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and the text string is returned in record_buffer.  */
 
     printf("------------------------------------------------------\n");
     printf("Test TXT:\n %s\n", record_buffer);
} 
```

```Output
Test TXT: 
v=spf1 include:_www.my_example.com ip4:192.2.2.10/31 ip4:192.2.2.11/31 ~all
```

## <a name="nx_dns_packet_pool_set"></a>nx_dns_packet_pool_set

DNS クライアントのパケット プールを設定する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a>説明

このサービスは、以前に作成されたパケット プールを、DNS **クライアント** のパケット プールとして設定します。 DNS クライアントでは、このパケット プールを使用して DNS クエリを送信します。そのため、パケット ペイロードは、イーサネット フレーム、IP ヘッダー、および UDP ヘッダーを含む NX_DNS_PACKET_PAYLOAD_UNALIGNED (*nx_dns.h* で定義) よりも小さくすることはできません。
 
>[!NOTE]
>DNS クライアントが削除されても、パケット プールは一緒に削除されません。不要になったパケット プールを削除するのはアプリケーションの役割です。

>[!NOTE]
>このサービスは、*nx_dns.h* で構成オプション NX_DNS_CLIENT_USER_CREATE_PACKET_POOL が定義されている場合にのみ使用できます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: 以前に作成された DNS **クライアント** インスタンスへのポインター。
- **pool_ptr**: 以前に作成されたパケット プールへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) 正常に完了しました。
- **NX_NOT_ENABLED**: (0x14) クライアントがこのオプション用に構成されていません
- NX_PTR_ERROR: (0x07) IP または DNS **クライアント** ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```c
NX_DNS             my_dns;
NX_PACKET_POOL     client_pool;
NX_IP             *ip_ptr;


/* Create the DNS Client.  */
status =  nx_dns_create(&my_dns, ip_ptr, “My DNS Client”);

/* Create a packet pool for the DNS Client.  */
status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                 NX_DNS_PACKET_PAYLOAD, free_mem_pointer, 
                                 NX_DNS_PACKET_POOL_SIZE);

/* Set the DNS Client packet pool.  */
status =  nx_dns_packet_pool_set(&my_dns, &client_pool);

/* If status is NX_SUCCESS the DNS Client packet pool was successfully set.  */
```

## <a name="nx_dns_server_add"></a>nx_dns_server_add

DNS サーバーの IP アドレスを追加する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a>説明

このサービスは、サーバー リストに IPv4 DNS サーバーを追加します。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: DNS 制御ブロックへのポインター。  
- **server_address**: DNS サーバーの IP アドレス。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) サーバーが正常に追加されました
- **NX_DNS_DUPLICATE_ENTRY** または **NX_NO_MORE_ENTRIES**: (0x17) これ以上の DNS サーバーは許可されません (リストがいっぱいです)
- **NX_DNS_PARAM_ERROR**: (0xA8) 非ポインター入力が無効です
- NX_PTR_ERROR: (0x07) ポインター入力が無効です
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です
- NX_DNS_BAD_ADDRESS_ERROR: (0xA4) サーバー アドレス入力が Null です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Add a DNS Server at IP address 202.2.2.13.  */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added.  */
```

## <a name="nx_dns_server_get"></a>nx_dns_server_get

クライアント リストから IPv4 DNS サーバーを返す

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                       ULONG *dns_server_address);
```

### <a name="description"></a>説明

このサービスは、サーバー リストの指定されたインデックスにある IPv4 DNS サーバー アドレスを返します。 インデックスは 0 から始まることに注意してください。 入力インデックスが DNS クライアントのリストのサイズを超えた場合は、エラーが返されます。 *nx_dns_get_serverlist_size* サービスを最初に呼び出して、クライアントのリスト内の DNS サーバーの数を取得できます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: DNS 制御ブロックへのポインター  
- **index**: DNS クライアントのサーバー リストへのインデックス
- **dns_server_address**: DNS サーバーの IP アドレスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) サーバーが正常に返されました
- **NX_DNS_SERVER_NOT_FOUND**: (0xA9) インデックスが空のスロットを指しています
- **NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) インデックスが Null アドレスを指しています
- **NX_DNS_PARAM_ERROR**: (0xA8) インデックスがリストのサイズを超えています
- NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
ULONG     my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list.  */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned.  */
```

## <a name="nx_dns_server_remove"></a>nx_dns_server_remove

クライアントのリストから IPv4 DNS サーバーを削除する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a>説明

このサービスは、クライアントのリストから IPv4 DNS サーバーを削除します。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: DNS 制御ブロックへのポインター。
- **server_address**: DNS サーバーの IP アドレス。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS サーバーが正常に削除されました
- **NX_DNS_SERVER_NOT_FOUND**: (0xA9) サーバーがクライアントのリストにありません
- **NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) サーバー アドレス入力が Null です
- NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nx_dns_server_remove_all"></a>nx_dns_server_remove_all

クライアントのリストからすべての DNS サーバーを削除する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```

### <a name="description"></a>説明

このサービスは、クライアントのリストからすべての DNS サーバーを削除します。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr**: DNS 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS サーバーが正常に削除されました
- **NX_DNS_ERROR**: (0xA0) 保護ミューテックスを取得できません
- NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c

/* Remove all DNS Servers from the Client list.  */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed.  */
```