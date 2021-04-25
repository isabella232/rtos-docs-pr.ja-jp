---
title: 第 3 章 - Azure RTOS NetX Duo DNS クライアント サービスの説明
description: この章では、すべての Azure RTOS NetX Duo DNS サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9634adab3944c29f64d26dd688b5053dc1bd9bcb
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810832"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dns-client-services"></a>第 3 章 - Azure RTOS NetX Duo DNS クライアント サービスの説明

この章では、すべての Azure RTOS NetX DNS サービス (以下に記載) をアルファベット順に説明します。

以下の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。

- **nx_dns_authority_zone_start_get** *指定されたホスト名に関連付けられている権限のゾーンの開始を検索します。*

- **nx_dns_cache_initialize** *DNS キャッシュを初期化します。*

- **nx_dns_cache_notify_clear** *キャッシュの完全な通知機能をクリアします。*

- **nx_dns_cache_notify_set** *キャッシュの完全な通知機能を設定します。*

- **nx_dns_cname_get** *入力ドメイン名の別名の正規のドメイン名を検索します*

- **nx_dns_create** *DNS クライアント インスタンスを作成します*

- **nx_dns_delete** *DNS クライアント インスタンスを削除します*

- **nx_dns_domain_name_server_get** *入力ドメイン ゾーンの権限のあるネーム サーバーを検索します*

- **nx_dns_domain_mail_exchange_get** *指定したホスト名に関連付けられているメール交換を検索します。*

- **nx_dns_domain_service_get** *指定したホスト名に関連付けられているサービスを検索します*

- **nx_dns_get_serverlist_size** *DNS クライアント サーバ リストのサイズを返します*

- **nx_dns_info_by_name_get** *入力ホスト名に対してクエリを実行し、IP アドレス、ポートを返します*

- **nx_dns_ipv4_address_by_name_get** *指定したホスト名から IPv4 アドレスを検索します*

- **nxd_dns_ipv6_address_by_name_get** *指定したホスト名から IPv6 アドレスを検索します*

- **nx_dns_host_by_address_get** *指定した IP アドレスからホスト名を検索するための nxd_dns_host_by_address_get のラッパー関数 (IPv4 アドレスのみをサポートします)*

- **nxd_dns_host_by_address_get** *入力ホスト名から IP アドレスを検索します (IPv4 と IPv6 の両方のアドレスをサポートします)*

- **nx_dns_host_by_name_get** *指定したアドレスからホスト名を検索するための nxd_dns_host_by_address_get のラッパー関数 (IPv4 アドレスのみをサポートします)*

- **nxd_dns_host_by_name_get** *入力ホスト名から IP アドレスを検索します (IPv4 と IPv6 の両方のアドレスをサポートします)*

- **nx_dns_host_text_get** *入力ドメイン名からテキスト データを検索します*

- **nx_dns_packet_pool_set** *DNS クライアント パケット プールを設定します*

- **nx_dns_server_add** *指定したアドレスでクライアント リストに DNS サーバーを追加するための*  nxd_dns_server_add  *のラッパー関数 (IPv4 のみをサポートします)*

- **nxd_dns_server_add** *指定した IP アドレスの DNS サーバーをクライアント サーバー リストに追加します (IPv4 と IPv6 の両方のアドレスをサポートします)*

- **nx_dns_server_get** *クライアント リストで DNS サーバーを返します (IPv4 アドレスのみをサポートします)*

- **nx_dns_server_get** *クライアント リストで DNS サーバーを返します (IPv4 と IPv6 の両方のアドレスのみをサポートします)*

- **nx_dns_server_remove** *クライアント リストから DNS サーバーを削除するための nxd_dns_server_remove のラッパー関数*

- **nxd_dns_server_remove** *指定した IP アドレスの DNS サーバーをクライアント リストから削除します (IPv4 と IPv6 の両方のアドレスをサポートします)*

- **nx_dns_server_remove_all** *クライアント リストからすべての DNS サーバーを削除します*

## <a name="nx_dns_authority_zone_start_get"></a>nx_dns_authority_zone_start_get

入力ホストの権限のゾーンの開始を検索します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,                                        
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```
### <a name="description"></a>説明

NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスによって指定したドメイン名の SOA 型のクエリが送信され、入力ドメイン名の権限のゾーンの開始が取得されます。 DNS クライアントによって、DNS サーバーの応答で返された SOA レコードが *record_buffer* のメモリの場所にコピーされます。

> [!NOTE]
> データを受信するには、*record_buffer* が 4 バイトで配置されている必要があります。

NetX Duo DNS クライアントでは、SOA レコードの種類 NX_DNS_SOA_ENTRY が 7 個の 4 バイトのパラメーター (合計 28 バイト) として保存されます

- **nx_dns_soa_host_mname_ptr** このゾーンのデータのプライマリ ソースへのポインター。
- **nx_dns_soa_host_rname_ptr** このゾーンを処理するメールボックスへのポインター
- **nx_dns_soa_serial** ゾーンのバージョン番号
- **nx_dns_soa_refresh** 更新間隔
- **nx_dns_soa_retry** SOA クエリ再試行の間隔
- **nx_dns_soa_expire** SOA の有効期限が切れるまでの期間
- **nx_dns_soa_minmum** SOA ホスト名 DNS 応答メッセージの最小 TTL フィールド

2 つの SOA レコードのストレージは次のようになります。 固定長データを含む SOA レコードは、バッファーの先頭から入力を開始されます。 ポインター MNAME および RNAME は、バッファーの末尾に格納されている可変長データ (ホスト名) を指します。 最初のレコードの後に追加の SOA レコードが入力され (“additional SOA records…”)、その可変長データが最後のエントリの可変長データの上に格納されます (“additional SOA variable length data”)

![2 つの SOA レコードのストレージ](media/image4.png)

入力 *record_buffer* にサーバー応答内のすべての SOA データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。

**Record_count* で返された SOA レコードの数を使用することで、アプリケーションで *record_buffer* からのデータを解析し、ゾーンの権限ホスト名の文字列の先頭を抽出できます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr** DNS クライアントへのポインター。  
- **host_name** SOA データを取得するためのホスト名へのポインター
- **record_buffer** SOA データを抽出する場所へのポインター
- **buffer_size** SOA データを保持するバッファーのサイズ
- **record_count** 取得した SOA レコードの数へのポインター
- **wait_option** DNS サーバーの応答を受信するための待機オプション

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): SOA データの取得に成功しました
- **NX_DNS_NO_SERVER** (0xA1) クライアント サーバー リストが空です
- **NX_DNS_QUERY_FAILED** (0xA3) 有効な DNS 応答を受信していません
- NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です
- NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
UCHAR  record_buffer[50];
UINT   record_count;   
NX_DNS_SOA_ENTRY *nx_dns_soa_entry_ptr;

/* Request the start of authority zone(s) for the specified host. */
status =  nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com",  
                                          record _buffer, sizeof(record_buffer), 
                                          &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
         error_counter++;
}
else 
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SOA data 
       is returned in soa_buffer. */

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

[Output]
----------------------------------------------------
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

DNS キャッシュを初期化します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                            VOID *cache_ptr, UINT cache_size);
```

### <a name="description"></a>説明

このサービスを使用すると、DNS キャッシュが作成されて初期化されます。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: DNS 制御ブロックを指すポインター。
- **cache_ptr** DNS キャッシュへのポインター。
- **cache_size** DNS キャッシュのサイズ (バイト単位)。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DNS キャッシュの初期化に成功しました
- NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です
- NX_DNS_CACHE_ERROR (0xB7) キャッシュ ポインターが無効です
- NX_PTR_ERROR (0x07) DNS ポインターが無効です。 
- NX_DNS_ERROR (0xA0) キャッシュが 4 バイトで配置されていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, &dns_cache, 2048);

/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a>nx_dns_cache_notify_clear

DNS キャッシュの完全な通知機能をクリアします

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、キャッシュの完全な通知機能がクリアされます。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: DNS 制御ブロックを指すポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DNS キャッシュ通知の設定に成功しました
- NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です
- NX_PTR_ERROR (0x07) DNS ポインターが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
/* Clear the DNS Cache full notify function. */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a>nx_dns_cache_notify_set

DNS キャッシュの完全な通知機能を設定します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr,
                            VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a>説明

このサービスを使用すると、キャッシュの完全な通知機能が設定されます。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: DNS 制御ブロックを指すポインター。
- **cache_full_notify_cb** キャッシュがいっぱいになったときに呼び出されるコールバック関数。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DNS キャッシュ通知の設定に成功しました
- NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です
- NX_PTR_ERROR (0x07) DNS ポインターが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
/* Set the DNS Cache full notify function. */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set. */
```

## <a name="nx_dns_cname_get"></a>nx_dns_cname_get

入力ホスト名の正規名を検索します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                     UCHAR *record_buffer, UINT buffer_size, 
                     ULONG wait_option);
```

### <a name="description"></a>説明

*nxd_dns.h* で NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスによって、指定されたドメイン名を持つ CNAME 型のクエリが送信され、正規のドメイン名が取得されます。 DNS クライアントによって、DNS サーバーの応答で返された CNAME 文字列が *record_buffer* のメモリの場所にコピーされます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr** DNS クライアントへのポインター。  
- **host_name** CNAME データを取得するためのホスト名へのポインター
- **record_buffer** CNAME データを抽出する場所へのポインター
- **buffer_size** CNAME データを保持するバッファーのサイズ
- **wait_option** DNS サーバーの応答を受信するための待機オプション

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): CNAME データの取得に成功しました
- **NX_DNS_NO_SERVER** (0xA1) クライアント サーバー リストが空です
- **NX_DNS_QUERY_FAILED** (0xA3) 有効な DNS 応答を受信していません
- NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です
- NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
CHAR            record _buffer[50];

/* Request the canonical name for the specified host. */
status =  nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                                   record_buffer, sizeof(record_buffer), 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and 
   the canonical host name is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test CNAME: %s\n", record_buffer);
} 

[Output]
----------------------------------------------------
Test CNAME: my_example.com
```

##  <a name="nx_dns_create"></a>nx_dns_create

DNS クライアント インスタンスを作成します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```
### <a name="description"></a>説明

このサービスを使用すると、以前に作成された IP インスタンスの DNS クライアント インスタンスが作成されます。

> [!IMPORTANT]
> アプリケーションは、DNS クライアントによって使用されるパケット プールのパケット ペイロードが、最大 512 バイトの DNS メッセージに加えて、UDP、IP、およびイーサネット ヘッダーに対して十分な大きさであることを確認する必要があります。 DNS クライアントによって独自のパケット プールが作成された場合、これは、NX_DNS_PACKET_PAYLOAD と NX_DNS_PACKET_POOL_SIZE によって定義されます。

DNS クライアント アプリケーションで、以前に作成されたパケット プールを提供することが優先される場合、IPv4 DNS クライアントのペイロードは、最大 DNS 用の 512 バイトに加えて、IP ヘッダー用の 20 バイト、UDP ヘッダー用の 8 バイト、イーサネット ヘッダー用の 14 バイトになります。 IPv6 の場合、唯一の違いは、IP ヘッダーが 40 バイトであるため、パケットは 40 バイトの IPv6 ヘッダーを収容できる必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr** DNS クライアントへのポインター。  
- **ip_ptr** 以前に作成された IP インスタンスへのポインター。  
- **domain_name** DNS インスタンスのドメイン名へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DNS の作成に成功しました
- **NX_DNS_ERROR** (0xA0) DNS 作成エラー
- NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
/* Create a DNS Client instance. */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created. */
```

## <a name="nx_dns_delete"></a>nx_dns_delete

DNS クライアント インスタンスを削除します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_delete(NX_DNS *dns_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、以前に作成された DNS クライアント インスタンスが削除され、リソースが解放されます。 

> [!NOTE]
> NX_DNS_CLIENT_USER_CREATE_PACKET_POOL が定義されていて、DNS クライアントにユーザー定義のパケット プールが割り当てられている場合、不要になった DNS クライアントのパケット プールの削除はアプリケーションが行う必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr** 以前に作成した DNS クライアント インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DNS クライアントの削除に成功しました。
- NX_PTR_ERROR (0x07) IP または DNS クライアント ポインターが無効です。
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
/* Delete a DNS Client instance. */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted. */
```

## <a name="nx_dns_domain_name_server_get"></a>nx_dns_domain_name_server_get

入力ドメイン ゾーンの権限のあるネーム サーバーを検索します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>説明

NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスによって指定したドメイン名の NS 型のクエリが送信され、入力ドメイン名のネーム サーバーが取得されます。 DNS クライアントによって、DNS サーバーの応答で返された NS レコードが *record_buffer* のメモリの場所にコピーされます。

> [!NOTE]
> データを受信するには、*record_buffer* が 4 バイトで配置されている必要があります。

NetX Duo DNS クライアントでは、NS データ型の NX_DNS_NS_ENTRY は、2 つの 4 バイトのパラメーターとして保存されます。

- **nx_dns_ns_ipv4_address** ネーム サーバーの IPv4 アドレス
- **nx_dns_ns_hostname_ptr** ネーム サーバーのホスト名へのポインター

次に示すバッファーには、4 つの NX_DNS_NS_ENTRY レコードが含まれています。 各エントリのホスト名文字列へのポインターは、バッファーの下半分にある対応するホスト名文字列を指します。

![4 つの NX_DNS_NS_ENTRY レコードが含まれます](media/image5.png)

入力 *record_buffer* にサーバー応答内のすべての NS データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。

**record_countt* で返された NS レコードの数を使用することで、アプリケーションで *record_buffer* 内の各レコードの IP アドレスとホスト名を解析できます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr** DNS クライアントへのポインター。  
- **host_name** NS データを取得するためのホスト名へのポインター
- **record_buffer** NS データを抽出する場所へのポインター
- **buffer_size** NS データを保持するバッファーのサイズ
- **record_count** 取得した NS レコードの数へのポインター
- **wait_option** DNS サーバーの応答を受信するための待機オプション

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): NS データの取得に成功しました
- **NX_DNS_NO_SERVER** (0xA1) クライアント サーバー リストが空です
- **NX_DNS_QUERY_FAILED** (0xA3) 有効な DNS 応答を受信していません
- NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です
- NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
#define RECORD_COUNT    10

ULONG  record_buffer[50];
UINT   record_count;          
NX_DNS_NS_ENTRY  *nx_dns_ns_entry_ptr[RECORD_COUNT];

/* Request the name server(s) for the specified host. */
status =  nx_dns_domain_name_server_get(&client_dns, (UCHAR *)" www.my_example.com ",  
                                        record_buffer, sizeof(record_buffer),  
                                        &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and NS data
   is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test NS: ");
    printf("record_count = %d \n", record_count);      

    /* Get the name server. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)
                               (record_buffer + i * sizeof(NX_DNS_NS_ENTRY)); 

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

[Output]
------------------------------------------------------
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

入力ホスト名のメール交換を検索します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                     VOID *record_buffer,                                        
                                     UINT buffer_size, 
                                     UINT *record_count, 
                                     ULONG wait_option);
```

### <a name="description"></a>説明

NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスによって指定したドメイン名の MX 型のクエリが送信され、入力ドメイン名のメール交換が取得されます。 DNS クライアントによって、DNS サーバーの応答で返された MX レコードが *record_buffer* のメモリの場所にコピーされます。 

> [!NOTE]
> データを受信するには、*record_buffer* が 4 バイトで配置されている必要があります。

NetX Duo DNS クライアントでは、メール交換レコードの種類 NX_DNS_MAIL_EXCHANGE_ENTRY が、次の 4 つのパラメーター (合計 12 バイト) として保存されます。

- **nx_dns_mx_ipv4_address** メール交換 IPv4 アドレス (4 バイト)
- **nx_dns_mx_preference** 優先順位 (2 バイト)
- **nx_dns_mx_reserved0** 予約済み (2 バイト)
- **nx_dns_mx_hostname_ptr** メール交換サーバー ホスト名へのポインター (4 バイト)

次に、4 つの MX レコードを含むバッファーを示します。 各レコードには、上記のリストの固定長データが含まれています。 メール交換サーバー ホスト名へのポインターは、バッファーの下部にある対応するホスト名を指します。

![4 つの MX レコードを含むバッファー](media/image6.png)

入力 *record_buffer* にサーバー応答内のすべての MX データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。

**record_countt* で返された MX レコードの数を使用することで、アプリケーションで *record_buffer* 内の各レコードのメール ホスト名を含む MX パラメーターの解析を行うことができます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr** DNS クライアントへのポインター。  
- **host_name** MX データを取得するためのホスト名へのポインター
- **record_buffer** MX データを抽出する場所へのポインター
- **buffer_size** MX データを保持するバッファーのサイズ
- **record_count** 取得した MX レコードの数へのポインター
- **wait_option** DNS サーバーの応答を受信するための待機オプション

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): MX データの取得に成功しました
- **NX_DNS_NO_SERVER** (0xA1) クライアント サーバー リストが空です
- **NX_DNS_QUERY_FAILED** (0xA3) 有効な DNS 応答を受信していません
- NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です
- NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
#define MAX_RECORD_COUNT 10

ULONG  record_buffer[50];
UINT   record_count;  
NX_DNS_MX_ENTRY  *nx_dns_mx_entry_ptr[MAX_RECORD_COUNT];        

/* Request the mail exchange data for the specified host. */
status =  nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)" www.my_example.com ", 
                                          record_buffer, sizeof(record_buffer),   
                                          &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
       
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and MX
   data is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test MX: ");
    printf("record_count = %d \n", record_count);      


    /* Get the mail exchange. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)
               (record_buffer + i * sizeof(NX_DNS_MX_ENTRY));   

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,                   
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);

        printf("preference = %d \n ", 
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);

        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", 
                    nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
}


[Output]

-----------------------------------------------------
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

入力ホスト名で提供されるサービスを検索します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>説明

NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスによって指定したドメイン名が使用されて SRV 型のクエリが送信され、指定したドメインに関連付けられているサービスとそのポート番号が検索されます。 DNS クライアントによって、DNS サーバーの応答で返された SRV レコードが *record_buffer* のメモリの場所にコピーされます。 

> [!NOTE]
> データを受信するには、*record_buffer* が 4 バイトで配置されている必要があります。

NetX Duo DNS クライアントでは、サービス レコードの種類 NX_DNS_SRV_ ENTRY が 6 個のパラメーター (合計 16 バイト) として保存されます。 これにより、可変長の SRV データをメモリ効率の高い方法で格納できます。

- **サーバー IPv4 アドレス** nx_dns_srv_ipv4_address (4 バイト)
- **サーバーの優先度** nx_dns_srv_priority (2 バイト)
- **サーバーの重み** nx_dns_srv_weight (2 バイト)
- **サービス ポート番号** nx_dns_srv_port_number (2 バイト)
- **4 バイトの配置用に予約済み** nx_dns_srv_reserved0 (2 バイト)
- **サーバー ホスト名へのポインター** *nx_dns_srv_hostname_ptr (4 バイト)

4 つの SRV レコードが、提供されるバッファーに格納されます。 各 NX_DNS_SRV_ENTRY レコードには、レコード バッファーの一番下にある対応するホスト名文字列を指すポインター (*nx_dns_srv_hostname_ptr*) が含まれています。

![SRV レコード用](media/image7.png)

入力 *record_buffer* にサーバー応答内のすべての SRV データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。

**record_count* で返された SRV レコードの数を使用することで、アプリケーションで *record_buffer* 内の各レコードのサーバー ホスト名を含む SRV パラメーターを解析できます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr** DNS クライアントへのポインター。  
- **host_name** SRV データを取得するためのホスト名へのポインター
- **record_buffer** SRV データを抽出する場所へのポインター
- **buffer_size** SRV データを保持するバッファーのサイズ
- **record_count** 取得した SRV レコードの数へのポインター
- **wait_option** DNS サーバーの応答を受信するための待機オプション

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): SRV データの取得に成功しました
- **NX_DNS_NO_SERVER** (0xA1) クライアント サーバー リストが空です
- **NX_DNS_QUERY_FAILED** (0xA3) 有効な DNS 応答を受信していません
- NX_DNS_PARAM_ERROR (0xA8) 非ポインター パラメーターが無効です。
- NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
#define MAX_RECORD_COUNT  10

UCHAR  record_buffer[50];
UINT   record_count;          
NX_DNS_SRV_ENTRY *nx_dns_srv_entry_ptr[MAX_RECORD_COUNT];

/* Request the service(s) provided by the specified host. */
status =  nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                                    record_buffer, sizeof(record_buffer), 
                                    &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SRV data
       is returned in record_buffer. */

        printf("------------------------------------------------------\n");
        printf("Test SRV: ");
        printf("record_count = %d \n", record_count);      

           
        /* Get the location of services. */
        for(i =0; i< record_count; i++)
        {
            nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)
                                    (record_buffer + i * sizeof(NX_DNS_SRV_ENTRY)); 

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

[Output]
----------------------------------------------------
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

DNS クライアントのサーバー リストのサイズを返します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```
### <a name="description"></a>説明

このサービスを使用すると、クライアント リストの有効な DNS サーバー (IPv4 と IPv6 の両方) の数が返されます。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: DNS 制御ブロックを指すポインター  
- **size** リスト内のサーバーの数を返します

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DNS サーバー リストのサイズが正常に返されました
- NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です。
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list. */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned. */
```

## <a name="nx_dns_info_by_name_get"></a>nx_dns_info_by_name_get

DNS サーバーの IP アドレスとポートをホスト名別に返します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスを使用すると、DNS クエリによる入力ホスト名に基づいて、サーバーの IP とポート (サービス レコード) が返されます。 サービス レコードが見つからない場合、このルーチンは、入力アドレス ポインターでゼロの IP アドレスを返し、0 以外のエラー状態を返してエラーを通知します。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: DNS 制御ブロックを指すポインター  
- **host_name**: ホスト名バッファーを指すポインター
- **host_address_ptr** 返されるアドレスへのポインター
- **host_address_ptr** 返されるポートへのポインター
- **wait_option** DNS 応答の待機オプション

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DNS サーバー レコードが正常に返されました
- **NX_DNS_NO_SERVER** (0xA1) ホスト名のクエリを送信するためにクライアントに登録されている DNS サーバーがありません
- **NX_DNS_QUERY_FAILED** (0xA3) DNS クエリが失敗しました。クライアント リストに DN サーバーからの応答がないか、入力ホスト名に使用できるサービス レコードがありません。
- NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR: (0x11) 呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
ULONG ip_address
USHORT port;

/* Attempt to resolve the IP address and ports for this host name. */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned. */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a>nx_dns_ipv4_address_by_name_get

入力ホスト名の IPv4 アドレスを検索します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_ dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたホスト名で A 型のクエリが送信され、入力ホスト名の IP アドレスが取得されます。 DNS クライアントによって、DNS サーバーの応答で返された A レコードからの IPv4 アドレスが *record_buffer* のメモリの場所にコピーされます。

> [!NOTE]
> データを受信するには、*record_buffer* が 4 バイトで配置されている必要があります。

次に示すように、複数の IPv4 アドレスが 4 バイトで配置されたバッファーに格納されます。

![複数のアドレスが 4 バイトで配置されたバッファー](media/image8.png)

提供されたバッファーがすべての IP アドレス データを保持できない場合、残りの A レコードは *record_buffer* に格納されません。 これにより、アプリケーションは、サーバーの応答で使用可能な IP アドレス データの 1 つ、一部、またはすべてを取得できます。

**Record_count* で返される A レコードの数を使用することで、アプリケーションで *record_buffer* からの IPv4 アドレス データを解析できます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr** DNS クライアントへのポインター。  
- **host_name_ptr** IPv4 アドレスを取得するためのホスト名へのポインター
- **buffer** IPv4 データを抽出する場所へのポインター
- **buffer_size** IPv4 データを保持するバッファーのサイズ
- **wait_option** DNS サーバーの応答を受信するための待機オプション

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): IPv4 データの取得に成功しました
- **NX_DNS_NO_SERVER** (0xA1) クライアント サーバー リストが空です
- **NX_DNS_QUERY_FAILED** (0xA3) 有効な DNS 応答を受信していません
- NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です
- NX_DNS_PARAM_ERROR (0xA8) 非ポインター パラメーターが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
#define MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
ULONG           *ipv4_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host. */
status =  nx_dns_ipv4_address_by_name_get(&client_dns, 
                                          (UCHAR *)"www.my_example.com",  
                                           record_buffer,                  
                                           sizeof(record_buffer),&record_count,                
                                           500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
        else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed the IPv4
       address(es) is returned in record_buffer. */

          
            printf("------------------------------------------------------\n");
            printf("Test A: ");
            printf("record_count = %d \n", record_count);      


           /* Get the IPv4 addresses of host. */
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

[Output]

------------------------------------------------------
Test A: record_count = 5 
record 0: IP address: 192.2.2.10
record 1: IP address: 192.2.2.11
record 2: IP address: 192.2.2.12
record 3: IP address: 192.2.2.13
record 4: IP address: 192.2.2.14
```

## <a name="nxd_dns_ipv6_address_by_name_get"></a>nxd_dns_ipv6_address_by_name_get

入力ホスト名の IPv6 アドレスを検索します

### <a name="prototype"></a>プロトタイプ
```C
UINT nxd_ dns_ipv6_address_by_name_get(NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたドメイン名で AAAA 型のクエリが送信され、入力ドメイン名の IP アドレスが取得されます。 DNS クライアントによって、DNS サーバーの応答で返された AAAA レコードからの IPv6 アドレスが *record_buffer* のメモリの場所にコピーされます。 

> [!NOTE]
> データを受信するには、*record_buffer* が 4 バイトで配置されている必要があります。

4 バイトで配置されたバッファーに格納されている IPv6 アドレスの形式を次に示します。

![IPv6 形式の 4 バイト配置バッファー](media/image9.png)

入力 *record_buffer* にサーバー応答内のすべての AAAA データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。

**record_countt* で返された AAAA レコードの数を使用することで、アプリケーションで *record_buffer* 内の各レコードの IPv6 アドレスを解析できます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr** DNS クライアントへのポインター。  
- **host_name_ptr** IPv6 アドレスを取得するためのホスト名へのポインター
- **buffer** IPv6 データの情報を抽出する場所へのポインター
- **buffer_size** IPv6 データを保持するバッファーのサイズ
- **wait_option** DNS サーバーの応答を受信するための待機オプション

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): IPv6 データの取得に成功しました
- **NX_DNS_NO_SERVER** (0xA1) クライアント サーバー リストが空です
- **NX_DNS_QUERY_FAILED** (0xA3) 有効な DNS 応答を受信していません
- NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です
- NX_DNS_PARAM_ERROR (0xA8) 非ポインター パラメーターが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
#define      MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
NXD_ADDRESS    *ipv6_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host. */
status =  nxd_dns_ipv6_address_by_name_get(&client_dns, 
                                           (UCHAR *)"www.my_example.com", 
                                           record__buffer,                  
                                           sizeof(record_buffer), 
                                           &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
        else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed the IPv6 
    address(es) is (are) returned in record_buffer. */
      
    printf("------------------------------------------------------\n");
    printf("Test AAAA: ");
    printf("record_count = %d \n", record_count);      

    /* Get the IPv6 addresses of host. */
    for(i =0; i< record_count; i++)
    {

        ipv6_address_ptr[i] = 
            (NX_DNS_IPV6_ADDRESS *)(record_buffer + i * sizeof(NX_DNS_IPV6_ADDRESS)); 
             
        printf("record %d: IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", i, 
                ipv6_address_ptr[i] -> ipv6_address[0]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[0]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[1]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[1]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[2]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[2]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[3]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[3]  & 0xFFFF);
            }
}


[Output]
------------------------------------------------------
Test AAAA: record_count = 1 
record 0: IP address: 2001:0db8:0000:f101: 0000: 0000: 0000:01003
```

## <a name="nx_dns_host_by_address_get"></a>nx_dns_host_by_address_get

IP アドレスからホスト名を検索します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a>説明

このサービスを使用すると、アプリケーションによって以前に指定された 1 つまたは複数の DNS サーバーから提供された IP アドレスの名前解決が要求されます。 成功した場合は、*host_name_ptr* によって指定された文字列で NULL で終了するホスト名が返されます。 これは *nxd_dns_host_by_address_get* サービスのラッパー関数であり、IPv6 アドレスは指定できません。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr** 以前に作成された DNS インスタンスへのポインター。
- **ip_address** 名前に解決する IP アドレス
- **host_name_ptr** ホスト名の宛先領域へのポインター
- **max_host_name_size** ホスト名の宛先領域のサイズ
- **wait_option** 各 DNS クエリおよびクエリ再試行の後に、サービスで DNS サーバーの応答を待機する時間をタイマー刻みで定義します。 この待機オプションは次のように定義されます。

  タイムアウト値 (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)

  TX_WAIT_FOREVER を選択すると、DNS サーバーが要求に応答するまで、呼び出しスレッドが無期限に停止されます。

  数値 (1-0xFFFFFFFE) を選択すると、DNS 解決を待機して停止を続ける時間 (タイマー刻みの最大数) が指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS の解決に成功しました  
- **NX_DNS_TIMEOUT** (0xA2) DNS ミューテックスの取得がタイムアウトになりました
- **NX_DNS_NO_SERVER** (0xA1) DNS サーバー アドレスが指定されていません
- **NX_DNS_QUERY_FAILED** (0xA3) クエリの応答を受信しませんでした
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) 入力アドレスが Null です
- **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) インデックスが無効なアドレスの種類 (IPv6 など) を指しています
- **NX_DNS_PARAM_ERROR** (0xA8) 非ポインター入力が無効です
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) IPv6 が無効になっているレコードは処理できません
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

**例**
```C
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */
```

## <a name="nxd_dns_host_by_address_get"></a>nxd_dns_host_by_address_get

IP アドレスからホスト名を検索します

### <a name="prototype"></a>プロトタイプ
```C
UINT nxd_dns_host_by_address_get(NX_DNS *dns_ptr, 
                                 NXD_ADDRESS ip_address, 
                                 ULONG *host_name_ptr, 
                                 ULONG max_host_name_size, 
                                 ULONG wait_option);
```

### <a name="description"></a>説明

このサービスを使用すると、アプリケーションによって以前に指定された 1 つまたは複数の DNS サーバーからの IPv6 または IPv4 アドレスの名前解決を、*ip_address* 入力引数で要求します。 成功した場合は、*host_name_ptr* によって指定された文字列で NULL で終了するホスト名が返されます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr** 以前に作成された DNS インスタンスへのポインター。
- **ip_address** 名前に解決する IP アドレス
- **host_name_ptr** ホスト名の宛先領域へのポインター
- **max_host_name_size** ホスト名の宛先領域のサイズ
- **wait_option** 各 DNS クエリおよびクエリ再試行の後に、サービスで DNS サーバーの応答を待機する時間をタイマー刻みで定義します。 この待機オプションは次のように定義されます。

  タイムアウト値 (0x00000001～0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)  

  TX_WAIT_FOREVER を選択すると、DNS サーバーが要求に応答するまで、呼び出しスレッドが無期限に停止されます。

  数値 (1-0xFFFFFFFE) を選択すると、DNS 解決を待機して停止を続ける時間 (タイマー刻みの最大数) が指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS の解決に成功しました  
- **NX_DNS_TIMEOUT** (0xA2) DNS ミューテックスの取得がタイムアウトになりました
- **NX_DNS_NO_SERVER** (0xA1) DNS サーバー アドレスが指定されていません
- **NX_DNS_QUERY_FAILED** (0xA3) クエリの応答を受信しませんでした
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) 入力アドレスが Null です
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) IPv6 が無効になっているレコードは処理できません
- NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です
- NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です

### <a name="allowed-from"></a>許可元

Threads

**例**
```C
UCHAR   resolved_name[200];
NXD_ADDRESS host_address;

host_address.nxd_ip_version = NX_IP_VERISON_V6;
host_address.nxd_ip_address.v6[0] = 0x20010db8;
host_address.nxd_ip_address.v6[1] = 0x0;
host_address.nxd_ip_address.v6[2] = 0xf101;
host_address.nxd_ip-address.v6[3] = 0x108;

/* Get the name associated with theinput host_address. */
status =  nxd_dns_host_by_address_get(&my_dns, &host_address,
                                      resolved_name, sizeof(resolved_name), 4000);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
     error_counter++;
}     
else     
{
     printf("------------------------------------------------------\n");
     printf("Test PTR: %s\n", record_buffer);
}

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable. */


[Output]

 ------------------------------------------------------
 Test PTR: my_example.net
```

## <a name="nx_dns_host_by_name_get"></a>nx_dns_host_by_name_get

ホスト名から IP アドレスを検索します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスを使用すると、アプリケーションによって以前に指定された 1 つまたは複数の DNS サーバーから提供された名前の名前解決が要求されます。 成功した場合、関連付けられた IP アドレスが、host_address_ptr によって指定された宛先に返されます。 これは、*nxd_dns_host_by_name_get* サービスのラッパー関数であり、入力は IPv4 アドレスに限定されています。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr** 以前に作成された DNS インスタンスへのポインター。
- **host_name**: ホスト名を指すポインター
- **host_address_ptr** 返された DNS サーバーの IP アドレス
- **wait_option** サービスで DNS 解決を待機する時間を定義します。 この待機オプションは次のように定義されます。

  タイムアウト値 (0x00000001～0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)

  TX_WAIT_FOREVER を選択すると、DNS サーバーが要求に応答するまで、呼び出しスレッドが無期限に停止されます。

  数値 (1-0xFFFFFFFE) を選択すると、DNS 解決を待機して停止を続ける時間 (タイマー刻みの最大数) が指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DNS の解決に成功しました
- **NX_DNS_NO_SERVER** (0xA1) DNS サーバー アドレスが指定されていません
- **NX_DNS_QUERY_FAILED** (0xA3) クエリの応答を受信しませんでした
- NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

**例**
```C
ULONG host_address;

/* Get the IP address for the name “www.my_example.com”. */
   status =  nx_dns_host_by_name_get(&my_dns, “www.my_example.com”, &host_address, 4000);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{

    /* If status is NX_SUCCESS the IP address for “www.my_example.com” can be found 
        in the “ip_address” variable. */
        
    printf("------------------------------------------------------\n");
    printf("Test A: \n");
    printf("IP address: %d.%d.%d.%d\n",
    host_address >> 24,
    host_address >> 16 & 0xFF,                   
    host_address >> 8 & 0xFF,
    host_address & 0xFF);
}

[Output]
 ------------------------------------------------------
Test A: 
IP address: 192.2.2.10
```

## <a name="nxd_dns_host_by_name_get"></a>nxd_dns_host_by_name_get

ホスト名から IP アドレスを検索します

### <a name="prototype"></a>プロトタイプ
```C
UINT nxd_dns_host_by_name_get(NX_DNS *dns_ptr, ULONG *host_name, 
                              NXD_ADDRESS *host_address_ptr, 
                              ULONG wait_option, UINT lookup_type);
```

### <a name="description"></a>説明

このサービスを使用すると、アプリケーションによって以前に指定された 1 つまたは複数の DNS サーバーから提供された IP アドレスの名前解決が要求されます。 成功した場合、関連付けられた IP アドレスが、*host_address_ptr* によって指定された NXD_ADDRESS に返されます。 呼び出し元が lookup_type 入力を NX_IP_VERSION_V6 に明示的に設定した場合、このサービスによってホスト IPv6 アドレス (AAAA レコード) のクエリが送信されます。 呼び出し元が lookup_type 入力を NX_IP_VERSION_V4 に明示的に設定した場合、このサービスによってホスト IPv4 アドレス (A レコード) のクエリが送信されます。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr** 以前に作成した DNS クライアント インスタンスへのポインター。
- **host_name** IP アドレスを検索するためのホスト名へのポインター
- **host_address_ptr** IP アドレスを含む NXD_ADDRESS の宛先へのポインター
- **wait_option** クエリの送信と再送信ごとに、サービスが DNS サーバーの応答を待機する時間をタイマー刻みで定義します。 この待機オプションは次のように定義されます。

  タイムアウト値 (0x00000001～0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)  

  TX_WAIT_FOREVER を選択すると、DNS サーバーが要求に応答するまで、呼び出しスレッドが無期限に停止されます。

  数値 (1-0xFFFFFFFE) を選択すると、DNS 解決を待機して停止を続ける時間 (タイマー刻みの最大数) が指定されます。

- **lookup_type** 検索の種類 (A または AAAA) を示します。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DNS の解決に成功しました
- **NX_DNS_NO_SERVER** (0xA1) DNS サーバー アドレスが指定されていません
- **NX_DNS_QUERY_FAILED** (0xA3) クエリの応答を受信しませんでした
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) 入力アドレスが Null です
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) IPv6 が無効になっているレコードは処理できません
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です
- NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です

### <a name="allowed-from"></a>許可元

Threads

**例**
```C
NXD_ADDRESS host_ipduo_address;

/* Create an AAAA query to obtain the IPv6 address for the host “www.my_example.com”. */
status =  nxd_dns_host_by_name_get(&my_dns, “www.my_example.com”, 
                                   &host_ipduo_address, 4000, 
                                   NX_IP_VERSION_V6);

if (status != NX_SUCCESS)
{
        error_counter++;
}
else
{
/* If status is NX_SUCCESS the IP address for “www.my_example.com” can be 
   found in the “ip_address” variable. */

    printf("------------------------------------------------------\n");
    printf("Test AAAA: \n");

    printf("IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", 
           host_ipduo_address.nxd_ip_address.v6[0]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[0]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[1]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[1]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[2]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[2]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[3]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[3]  & 0xFFFF);
}

[Output]

------------------------------------------------------
Test AAAA: 
IP address: 2607:f8b0:4007:800:0:0:0:1008
```

このタイム サービスを使用するもう 1 つの例を次に示します。ここでは、IPv4 アドレスと A レコード型を使用しています。
```C
/* Create a query to obtain the IPv4 address for the host “www.my_example.com”. */
status =  nxd_dns_host_by_name_get(&my_dns, “www.my_example.com”, &ip_address, 4000, 
                                   NX_IP_VERSION_V4);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{   
/* If status is NX_SUCCESS the IP address for “www.my_example.com” can be 
   found in the “ip_address” variable. */
  
     printf("------------------------------------------------------\n");
     printf("Test A: \n");
     printf("IP address: %d.%d.%d.%d\n",
            host_ipduo_address.nxd_ip_address.v4 >> 24,
            host_ipduo_address.nxd_ip_address.v4 >> 16 & 0xFF,                   
            host_ipduo_address.nxd_ip_address.v4 >> 8 & 0xFF,
            host_ipduo_address.nxd_ip_address.v4 & 0xFF);
 }

[Output]

------------------------------------------------------
Test A: 
IP address: 192.2.2.10
```

## <a name="nx_dns_host_text_get"></a>nx_dns_host_text_get

入力ドメイン名のテキスト文字列を検索します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたドメイン名とバッファーを使用して TXT 型のクエリが送信され、任意の文字列データが取得されます。

DNS クライアントによって、DNS サーバーの応答の TXT レコードのテキスト文字列が *record_buffer* のメモリ位置にコピーされます。 

> [!NOTE]
> データを受信するために record_buffer が 4 バイトで配置されている必要はありません。

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr** DNS クライアントへのポインター。  
- **host_name** 検索するホストの名前へのポインター
- **record_buffer** TXT データを抽出する場所へのポインター
- **buffer_size** TXT データを保持するバッファーのサイズ
- **wait_option** DNS サーバーの応答を受信するための待機オプション

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) TXT 文字列の取得に成功しました
- **NX_DNS_NO_SERVER** (0xA1) クライアント サーバー リストが空です
- **NX_DNS_QUERY_FAILED** (0xA3) 有効な DNS 応答を受信していません
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です
- NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です

### <a name="allowed-from"></a>許可元

Threads

######   
例
```C
CHAR            record_buffer[50];

/* Request the text string for the specified host. */
status =  nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", 
                               record_buffer, 
                               sizeof(record_buffer), 500);


/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
     error_counter++;
}
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and the
       text string is returned in record_buffer. */
 
     printf("------------------------------------------------------\n");
     printf("Test TXT:\n %s\n", record_buffer);
} 


[Output]

------------------------------------------------------
Test TXT: 
v=spf1 include:_www.my_example.com ip4:192.2.2.10/31 ip4:192.2.2.11/31 ~all
```

## <a name="nx_dns_packet_pool_set"></a>nx_dns_packet_pool_set

DNS クライアントのパケット プールを設定します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、以前に作成したパケット プールが DNS クライアント パケット プールとして設定されます。 DNS クライアントによってこのパケット プールが使用されて DNS クエリが送信されます。そのため、パケット ペイロードは、イーサネット、IP、および UDP ヘッダーを含み、*nxd_dns* で定義されている NX_DNS_PACKET_PAYLOAD よりも小さくすることはできません。 

> [!NOTE]
> *D* NS クライアントが削除された場合、パケット プールは削除されず、不要になったパケット プールの削除はアプリケーションの役割になります。
>
> このサービスは、構成オプション NX_DNS_CLIENT_USER_CREATE_PACKET_POOL が *nxd_dns.h* に定義されている場合にのみ使用できます

### <a name="input-parameters"></a>入力パラメーター

- **dns_ptr** 以前に作成した DNS クライアント インスタンスへのポインター。
- **pool_ptr** 以前に作成されたパケット プールへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 正常に完了しました。
- **NX_NOT_ENABLED** (0x14) クライアントがこのオプション用に構成されていません
- NX_PTR_ERROR (0x07) IP または DNS クライアント ポインターが無効です。
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
NXD_DNS my_dns;
NX_PACKET_POOL client_pool;
NX_IP *ip_ptr;


/* Create the DNS Client. */
status =  nx_dns_create(&my_dns, ip_ptr, “My DNS Client”);

/* Create a packet pool for the DNS Client. */
status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                NX_DNS_PACKET_PAYLOAD, free_mem_pointer, 
                                NX_DNS_PACKET_POOL_SIZE);

/* Set the DNS Client packet pool. */
status =  nx_dns_packet_pool_set(&my_dns, &client_pool);

/* If status is NX_SUCCESS the DNS Client packet pool was successfully set. */
```

## <a name="nx_dns_server_add"></a>nx_dns_server_add

DNS サーバーの IP アドレスを追加します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a>説明

このサービスを使用すると、サーバー リストに IPv4 DNS サーバーが追加されます。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: DNS 制御ブロックを指すポインター。  
- **server_address** DNS サーバーの IP アドレス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) サーバーの追加に成功しました
- **NX_DNS_DUPLICATE_ENTRY**  
**NX_NO_MORE_ENTRIES** (0x17) これ以上の DNS サーバーは許可されません (リストがいっぱいです)
- **NX_DNS_PARAM_ERROR** (0xA8) 非ポインター入力が無効です
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) IPv6 が無効になっているレコードは処理できません
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です
- NX_DNS_BAD_ADDRESS_ERROR (0xA4) サーバー アドレスの入力が Null です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
/* Add a DNS Server at IP address 202.2.2.13. */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nxd_dns_server_add"></a>nxd_dns_server_add

DNS サーバーをクライアント リストに追加します

### <a name="prototype"></a>プロトタイプ
```C
UINT nxd_dns_server_add(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a>説明

このサービスを使用すると、DNS サーバーの IP アドレスが DNS クライアント サーバー リストに追加されます。 server_address には、IPv4 または IPv6 アドレスを指定できます。 クライアントから IPv4 アドレスまたは IPv6 アドレスのいずれかで同じサーバーにアクセスできるようにする場合は、両方の IP アドレスをエントリとしてサーバー リストに追加する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: DNS 制御ブロックを指すポインター。
- **server_address** DNS サーバーの IP アドレスが含まれている NXD_ADDRESS へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) サーバーの追加に成功しました
- **NX_DNS_DUPLICATE_ENTRY**  
**NX_NO_MORE_ENTRIES** (0x17) これ以上の DNS サーバーは許可されません (リストがいっぱいです) 
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) IPv6 が無効になっているレコードは処理できません
- **NX_DNS_PARAM_ERROR** (0xA8) 非ポインター入力が無効です
- NX_PTR_ERROR (0x07) ポインター入力が無効です
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です
- NX_DNS_BAD_ADDRESS_ERROR (0xA4) サーバー アドレスの入力が Null です
- NX_DNS_INVALID_ADDRESS_TYPE (0xB2) インデックスが無効なアドレスの種類 (IPv6 など) を指しています

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
NXD_ADDRESS server_address;

server_address.nxd_ip_version = NX_IP_VERISON_V6;
server_address.nxd_ip_address.v6[0] = 0x20010db8;
server_address.nxd_ip_address.v6[1] = 0x0;
server_address.nxd_ip_address.v6[2] = 0xf101;
server_address.nxd_ip-address.v6[3] = 0x108;


/* Add a DNS Server with the IP address pointed to by the server_address input. */
status =  nxd_dns_server_add(&my_dns, &server_address);

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nx_dns_server_get"></a>nx_dns_server_get

クライアント リストから IPv4 DNS サーバーを返します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        ULONG *dns_server_address);
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたインデックス位置にあるサーバー リストから IPv4 DNS サーバー アドレスが返されます。 

> [!NOTE]
> インデックスは 0 から始まります。 入力インデックスが DNS クライアント リストのサイズを超えた場合は、そのインデックスで IPv6 アドレスが見つかるか、または指定されたインデックスで null アドレスが見つかると、エラーが返されます。 クライアント リスト内の DNS サーバーの数を取得するため、*Nx_dns_get_serverlist_size* サービスを最初に呼び出すことができます。

このサービスでは、IPv4 アドレスのみがサポートされています。 IPv4 アドレスと IPv6 アドレスの両方をサポートする *nxd_dns_server_get* サービスを呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: DNS 制御ブロックを指すポインター  
- **index** DNS クライアントのサーバーのリストにインデックスを作成します
- **dns_server_address** DNS サーバーの IP アドレスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) サーバーが正常に返されました
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) インデックスが空のスロットを指しています
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) インデックスが Null アドレスを指しています
- **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) インデックスが無効なアドレスの種類 (IPv6 など) を指しています
- **NX_DNS_PARAM_ERROR** (0xA8) 非ポインター入力が無効です
- NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です。
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
ULONG my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nxd_dns_server_get"></a>nxd_dns_server_get

クライアント リストから DNS サーバーを返します

### <a name="prototype"></a>プロトタイプ
```C
UINT nxd_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        NXD_ADDRESS *dns_server_address);
```

### <a name="description"></a>説明

このサービスを使用すると、指定されたインデックス位置にあるサーバー リストから DNS サーバー IP アドレスが返されます。 

> [!NOTE]
> インデックスは 0 から始まります。 入力インデックスが DNS クライアント リストのサイズを超えた場合、または指定されたインデックスで null アドレスが見つかった場合、エラーが返されます。 サーバー リスト内の DNS サーバーの数を取得するため、*Nx_dns_get_serverlist_size* サービスを最初に呼び出すことができます。

このサービスでは、IPv4 および IPv6 アドレスがサポートされています。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: DNS 制御ブロックを指すポインター  
- **index** DNS クライアントのサーバーのリストにインデックスを作成します
- **dns_server_address** DNS サーバーの IP アドレスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) サーバーの IP アドレスが正常に返されました
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) インデックスが空のスロットを指しています
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) インデックスが Null サーバー アドレスを指しています
- **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) インデックスが無効なアドレスの種類 (IPv6 など) を指しています
- **NX_DNS_PARAM_ERROR** (0xA8) 非ポインター入力が無効です
- NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です。
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
NXD_ADDRESS my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nxd_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nx_dns_server_remove"></a>nx_dns_server_remove

クライアント リストから IPv4 DNS サーバーを削除します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a>説明

このサービスを使用すると、クライアント リストから IPv4 DNS サーバーが削除されます。 これは *nxd_dns_server_remove* のラッパー関数です。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: DNS 制御ブロックを指すポインター。
- **server_address** DNS サーバーの IP アドレス。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DNS サーバーの削除に成功しました
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) サーバーがクライアント リストにありません
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) サーバー アドレスの入力が Null です
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) IPv6 が無効になっているレコードは処理できません
- NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です。
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nxd_dns_server_remove"></a>nxd_dns_server_remove

クライアント リストから DNS サーバーを削除します

### <a name="prototype"></a>プロトタイプ
```C
UINT nxd_dns_server_remove(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a>説明

このサービスを使用すると、指定された IP アドレスの DNS サーバーがクライアント リストから削除されます。 入力 IP アドレスには、IPv4 アドレスと IPv6 アドレスの両方を指定できます。 サーバーを削除すると、空いているスロットを埋めるために、残っているサーバーは、リスト内の 1 つ下のインデックスに移動します。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: DNS 制御ブロックを指すポインター。
- **server_address** サーバーの IP アドレスを含む DNS サーバー NXD_ADDRESS へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DNS サーバーの削除に成功しました
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) サーバーがクライアント リストにありません
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) サーバー アドレスの入力が Null です
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) IPv6 が無効になっているレコードは処理できません
- NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です。
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です
- NX_DNS_INVALID_ADDRESS_TYPE (0xB2) インデックスが無効なアドレスの種類 (IPv6 など) を指しています

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
NXD_ADDRESS server_address;

server_address.nxd_ip_version = NX_IP_VERISON_V6;
server_address.nxd_ip_address.v6[0] = 0x20010db8;
server_address.nxd_ip_address.v6[1] = 0x0;
server_address.nxd_ip_address.v6[2] = 0xf101;
server_address.nxd_ip-address.v6[3] = 0x108;


/* Remove the DNS Server at the specified IP address from the Client list. */
status =  nxd_dns_server_remove(&my_dns,&server_ADDRESS);

/* If status is NX_SUCCESS a DNS Server was successfully removed. */
```

## <a name="nx_dns_server_remove_all"></a>nx_dns_server_remove_all

すべての DNS サーバーをクライアント リストから削除します

### <a name="prototype"></a>プロトタイプ
```C
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、クライアント リストからすべての DNS サーバーが削除されます。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: DNS 制御ブロックを指すポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DNS サーバーの削除に成功しました
- **NX_DNS_ERROR** (0xA0) 保護ミューテックスを取得できません
- NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です。
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
/* Remove all DNS Servers from the Client list. */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed. */
```