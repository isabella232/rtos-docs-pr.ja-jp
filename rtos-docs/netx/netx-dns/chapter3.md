---
title: 第 3 章 - Azure RTOS NetX DNS クライアント サービスの説明
description: この章では、すべての Azure RTOS NetX DNS サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 18e059e79f9742eaaafffbf15b55b4b5063363f8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811567"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dns-client-services"></a><span data-ttu-id="9ef81-103">第 3 章 - Azure RTOS NetX DNS クライアント サービスの説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-103">Chapter 3 - Description of Azure RTOS NetX DNS Client Services</span></span>

<span data-ttu-id="9ef81-104">この章では、すべての Azure RTOS NetX DNS サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-104">This chapter contains a description of all Azure RTOS NetX DNS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="9ef81-105">以下の API の説明の「戻り値」セクションで、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字でない値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="9ef81-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="9ef81-106">**nx_dns_authority_zone_start_get**: "*指定されたホスト名に関連付けられている権威のゾーンの開始を検索する*"</span><span class="sxs-lookup"><span data-stu-id="9ef81-106">**nx_dns_authority_zone_start_get**: *Look up the start of a zone of authority associated with the specified host name*</span></span>
- <span data-ttu-id="9ef81-107">**nx_dns_cache_initialize**: "*DNS キャッシュを初期化する。* "</span><span class="sxs-lookup"><span data-stu-id="9ef81-107">**nx_dns_cache_initialize**: *Initialize a DNS Cache.*</span></span>
- <span data-ttu-id="9ef81-108">**nx_dns_cache_notify_clear**: "*キャッシュ満杯通知関数をクリアする。* "</span><span class="sxs-lookup"><span data-stu-id="9ef81-108">**nx_dns_cache_notify_clear**: *Clear the cache full notify function.*</span></span>
- <span data-ttu-id="9ef81-109">**nx_dns_cache_notify_set**: "*キャッシュ満杯通知関数を設定する。* "</span><span class="sxs-lookup"><span data-stu-id="9ef81-109">**nx_dns_cache_notify_set**: *Set the cache full notify function.*</span></span>
- <span data-ttu-id="9ef81-110">**nx_dns_cname_get**: "*入力ドメイン名の別名に対応する正規のドメイン名を検索する*"</span><span class="sxs-lookup"><span data-stu-id="9ef81-110">**nx_dns_cname_get**: *Look up the canonical domain name for the input domain name alias*</span></span>
- <span data-ttu-id="9ef81-111">**nx_dns_create**: "*DNS クライアント インスタンスを作成する*"</span><span class="sxs-lookup"><span data-stu-id="9ef81-111">**nx_dns_create**: *Create a DNS Client instance*</span></span>
- <span data-ttu-id="9ef81-112">**nx_dns_delete**: "*DNS クライアント インスタンスを削除する*"</span><span class="sxs-lookup"><span data-stu-id="9ef81-112">**nx_dns_delete**: *Delete a DNS Client instance*</span></span>
- <span data-ttu-id="9ef81-113">**nx_dns_domain_name_server_get**: "*入力ドメイン ゾーンの権威ネーム サーバーを検索する*"</span><span class="sxs-lookup"><span data-stu-id="9ef81-113">**nx_dns_domain_name_server_get**: *Look up the authoritative name servers for the input domain zone*</span></span>
- <span data-ttu-id="9ef81-114">**nx_dns_domain_mail_exchange_get**: "*指定されたホスト名に関連付けられているメール交換を検索する。* "</span><span class="sxs-lookup"><span data-stu-id="9ef81-114">**nx_dns_domain_mail_exchange_get**: *Look up the mail exchange associated the specified host name.*</span></span>
- <span data-ttu-id="9ef81-115">**nx_dns_domain_service_get**: "*指定されたホスト名に関連付けられているサービスを検索する*"</span><span class="sxs-lookup"><span data-stu-id="9ef81-115">**nx_dns_domain_service_get**: *Look up the service(s) associated with the specified host name*</span></span>
- <span data-ttu-id="9ef81-116">**nx_dns_get_serverlist_size**: "*DNS クライアントのサーバー リストのサイズを返す*"</span><span class="sxs-lookup"><span data-stu-id="9ef81-116">**nx_dns_get_serverlist_size**: *Return the size of the DNS Client server list*</span></span>
- <span data-ttu-id="9ef81-117">**nx_dns_info_by_name_get**: "*入力ホスト名のクエリを実行して IP アドレスとポートを返す*"</span><span class="sxs-lookup"><span data-stu-id="9ef81-117">**nx_dns_info_by_name_get**: *Return IP address, port querying on input host name*</span></span>
- <span data-ttu-id="9ef81-118">**nx_dns_ipv4_address_by_name_get**: "*指定されたホスト名から IPv4 アドレスを検索する*"</span><span class="sxs-lookup"><span data-stu-id="9ef81-118">**nx_dns_ipv4_address_by_name_get**: *Look up the IPv4 address from the specified host name*</span></span>
- <span data-ttu-id="9ef81-119">**nx_dns_host_by_address_get**: "*指定された IP アドレスからホスト名を検索する*"</span><span class="sxs-lookup"><span data-stu-id="9ef81-119">**nx_dns_host_by_address_get**: *Look up a host name from a specified IP address*</span></span>
- <span data-ttu-id="9ef81-120">**nx_dns_host_by_name_get**: "*指定されたホスト名から IPv4 アドレスを検索する*"</span><span class="sxs-lookup"><span data-stu-id="9ef81-120">**nx_dns_host_by_name_get**: *Look up the IPv4 address from the specified host name*</span></span>
- <span data-ttu-id="9ef81-121">**nx_dns_host_text_get**: "*入力ドメイン名のテキスト データを検索する*"</span><span class="sxs-lookup"><span data-stu-id="9ef81-121">**nx_dns_host_text_get**: *Look up the text data for the input domain name*</span></span>
- <span data-ttu-id="9ef81-122">**nx_dns_packet_pool_set**: "*DNS クライアントのパケット プールを設定する*"</span><span class="sxs-lookup"><span data-stu-id="9ef81-122">**nx_dns_packet_pool_set**: *Set the DNS Client packet pool*</span></span>
- <span data-ttu-id="9ef81-123">**nx_dns_server_add**: "*指定されたアドレスの DNS サーバーをクライアントのリストに追加する*"</span><span class="sxs-lookup"><span data-stu-id="9ef81-123">**nx_dns_server_add**: *Add a DNS Server at the specified address to the Client list*</span></span>
- <span data-ttu-id="9ef81-124">**nx_dns_server_get**: "*クライアントのリスト内の DNS サーバーを返す*"</span><span class="sxs-lookup"><span data-stu-id="9ef81-124">**nx_dns_server_get**: *Return the DNS Server in the Client list*</span></span>
- <span data-ttu-id="9ef81-125">**nx_dns_server_remove**: "*クライアントのリストから DNS サーバーを削除する*"</span><span class="sxs-lookup"><span data-stu-id="9ef81-125">**nx_dns_server_remove**: *Remove a DNS Server from the Client list*</span></span>
- <span data-ttu-id="9ef81-126">**nx_dns_server_remove_all**: "*クライアント リストからすべての DNS サーバーを削除する*"</span><span class="sxs-lookup"><span data-stu-id="9ef81-126">**nx_dns_server_remove_all**: *Remove all DNS Servers from the Client list*</span></span>

## <a name="nx_dns_authority_zone_start_get"></a><span data-ttu-id="9ef81-127">nx_dns_authority_zone_start_get</span><span class="sxs-lookup"><span data-stu-id="9ef81-127">nx_dns_authority_zone_start_get</span></span>

<span data-ttu-id="9ef81-128">入力ホストの権威のゾーンの開始を検索する</span><span class="sxs-lookup"><span data-stu-id="9ef81-128">Look up the start of the zone of authority for the input host</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-129">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-129">Prototype</span></span>

```c
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="9ef81-130">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-130">Description</span></span>

<span data-ttu-id="9ef81-131">NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスは指定されたドメイン名で SOA タイプのクエリを送信して、入力ドメイン名の権威のゾーンの開始を取得します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-131">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SOA with the specified domain name to obtain the start of the zone of authority for the input domain name.</span></span> <span data-ttu-id="9ef81-132">DNS クライアントは、DNS サーバー応答で返された SOA レコードを、*record_buffer* のメモリ位置にコピーします。</span><span class="sxs-lookup"><span data-stu-id="9ef81-132">The DNS Client copies the SOA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 
>[!NOTE]
> <span data-ttu-id="9ef81-133">データを受信するには、*record_buffer* が 4 バイト アラインされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef81-133">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="9ef81-134">NetX DNS クライアントでは、SOA レコード NX_DNS_SOA_ENTRY は、7 個の 4 バイトのパラメーター (合計 28 バイト) として保存されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-134">In NetX DNS Client, the SOA record type, NX_DNS_SOA_ENTRY, is saved as seven 4 byte parameters, totaling 28 bytes:</span></span>

- <span data-ttu-id="9ef81-135">**nx_dns_soa_host_mname_ptr**: このゾーンのデータのプライマリ ソースへのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-135">**nx_dns_soa_host_mname_ptr**: Pointer to primary source of data for this zone</span></span>
- <span data-ttu-id="9ef81-136">**nx_dns_soa_host_rname_ptr**: このゾーンに対応するメールボックスへのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-136">**nx_dns_soa_host_rname_ptr**: Pointer to mailbox responsible for this zone</span></span>
- <span data-ttu-id="9ef81-137">**nx_dns_soa_serial**: ゾーンのバージョン番号</span><span class="sxs-lookup"><span data-stu-id="9ef81-137">**nx_dns_soa_serial**: Zone version number</span></span>
- <span data-ttu-id="9ef81-138">**nx_dns_soa_refresh**: 更新間隔</span><span class="sxs-lookup"><span data-stu-id="9ef81-138">**nx_dns_soa_refresh**: Refresh interval</span></span>
- <span data-ttu-id="9ef81-139">**nx_dns_soa_retry**: SOA クエリの再試行の間隔</span><span class="sxs-lookup"><span data-stu-id="9ef81-139">**nx_dns_soa_retry**: Interval between SOA query retries</span></span>
- <span data-ttu-id="9ef81-140">**nx_dns_soa_expire**: SOA の有効期限が切れるまでの期間</span><span class="sxs-lookup"><span data-stu-id="9ef81-140">**nx_dns_soa_expire**: Time duration when SOA expires</span></span>
- <span data-ttu-id="9ef81-141">**nx_dns_soa_minmum**: SOA ホスト名 DNS 応答メッセージの最小 TTL フィールド</span><span class="sxs-lookup"><span data-stu-id="9ef81-141">**nx_dns_soa_minmum**: Minimum TTL field in SOA hostname DNS reply messages</span></span>

<span data-ttu-id="9ef81-142">2 つの SOA レコードの格納を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-142">The storage of a two SOA records is shown below.</span></span> <span data-ttu-id="9ef81-143">固定長データを含む SOA レコードは、バッファーの先頭から入力が開始されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-143">The SOA records containing fixed length data are entered starting at the top of the buffer.</span></span> <span data-ttu-id="9ef81-144">ポインター MNAME および RNAME は、バッファーの末尾に格納されている可変長データ (ホスト名) を指します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-144">The pointers MNAME and RNAME point to the variable length data (host names) which are stored at the bottom of the buffer.</span></span> <span data-ttu-id="9ef81-145">最初のレコードの後に追加の SOA レコードが入力され ("additional SOA records…")、その可変長データが最後のエントリの可変長データ上に格納されます ("additional SOA variable length data")。</span><span class="sxs-lookup"><span data-stu-id="9ef81-145">Additional SOA records are entered after the first record (“additional SOA records…”) and their variable length data is stored above the last entry’s variable length data (“additional SOA variable length data”):</span></span>

![2 つの S O A レコードの格納を表す図](media/image2.png)

<span data-ttu-id="9ef81-147">入力 *record_buffer* にサーバー応答内のすべての SOA データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-147">If the input *record_buffer* cannot hold all the SOA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="9ef81-148">\**record_count* で返された SOA レコードの数を使用して、アプリケーションは *record_buffer* からのデータを解析し、ホスト名文字列の権威のゾーンの開始を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-148">With the number of SOA records returned in \**record_count,* the application can parse the data from *record_buffer* and extract the start of zone authority host name strings.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-149">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-149">Input Parameters</span></span>

- <span data-ttu-id="9ef81-150">**dns_ptr**: DNS クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-150">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="9ef81-151">**host_name**: SOA データを取得するホスト名へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-151">**host_name**: Pointer to host name to obtain SOA data for</span></span>
- <span data-ttu-id="9ef81-152">**record_buffer**: SOA データを抽出する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-152">**record_buffer**: Pointer to location to extract SOA data into</span></span>
- <span data-ttu-id="9ef81-153">**buffer_size**: SOA データを保持するバッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="9ef81-153">**buffer_size**: Size of buffer to hold SOA data</span></span>
- <span data-ttu-id="9ef81-154">**record_count**: 取得した SOA レコードの数へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-154">**record_count**: Pointer to the number of SOA records retrieved</span></span>
- <span data-ttu-id="9ef81-155">**wait_option**: DNS サーバー応答を受信する際の待機オプション</span><span class="sxs-lookup"><span data-stu-id="9ef81-155">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-156">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-156">Return Values</span></span>

- <span data-ttu-id="9ef81-157">**NX_SUCCESS**: (0x00) SOA データが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="9ef81-157">**NX_SUCCESS**: (0x00) Successfully obtained SOA data</span></span>
- <span data-ttu-id="9ef81-158">**NX_DNS_NO_SERVER**: (0xA1) クライアントのサーバー リストが空です</span><span class="sxs-lookup"><span data-stu-id="9ef81-158">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="9ef81-159">**NX_DNS_QUERY_FAILED**: (0xA3) 有効な DNS 応答を受信していません</span><span class="sxs-lookup"><span data-stu-id="9ef81-159">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="9ef81-160">NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-160">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9ef81-161">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-161">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="9ef81-162">NX_DNS_PARAM_ERROR: (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-162">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-163">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-163">Allowed From</span></span>

<span data-ttu-id="9ef81-164">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-164">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-165">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-165">Example</span></span>
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


## <a name="nx_dns_cache_initialize"></a><span data-ttu-id="9ef81-166">nx_dns_cache_initialize</span><span class="sxs-lookup"><span data-stu-id="9ef81-166">nx_dns_cache_initialize</span></span>

<span data-ttu-id="9ef81-167">DNS キャッシュを初期化する</span><span class="sxs-lookup"><span data-stu-id="9ef81-167">Initialize the DNS Cache</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-168">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-168">Prototype</span></span>

```c
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                             VOID *cache_ptr, UINT cache_size);

```
### <a name="description"></a><span data-ttu-id="9ef81-169">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-169">Description</span></span>

<span data-ttu-id="9ef81-170">このサービスは、DNS キャッシュを作成して初期化します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-170">This service creates and initializes a DNS Cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-171">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-171">Input Parameters</span></span>

- <span data-ttu-id="9ef81-172">**dns_ptr**: DNS 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-172">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="9ef81-173">**cache_ptr**: DNS キャッシュへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-173">**cache_ptr**: Pointer to DNS Cache.</span></span>
- <span data-ttu-id="9ef81-174">**cache_size**: DNS キャッシュのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="9ef81-174">**cache_size**: Size of DNS Cache, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-175">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-175">Return Values</span></span>

- <span data-ttu-id="9ef81-176">**NX_SUCCESS**: (0x00) DNS キャッシュが正常に初期化されました</span><span class="sxs-lookup"><span data-stu-id="9ef81-176">**NX_SUCCESS**: (0x00) DNS Cache successfully initialized</span></span>
- <span data-ttu-id="9ef81-177">NX_DNS_ERROR: (0xA0) キャッシュが 4 バイト アラインされていません。</span><span class="sxs-lookup"><span data-stu-id="9ef81-177">NX_DNS_ERROR: (0xA0) Cache is not 4-byte aligned.</span></span>
- <span data-ttu-id="9ef81-178">NX_DNS_PARAM_ERROR: (0xA8) DNS ID が無効です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-178">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="9ef81-179">NX_PTR_ERROR: (0x07) DNS ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-179">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>
- <span data-ttu-id="9ef81-180">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-180">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-181">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-181">Allowed From</span></span>

<span data-ttu-id="9ef81-182">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-182">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-183">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-183">Example</span></span>
```c
UCHAR          dns_cache [2048]; 

/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, dns_cache, 2048);
/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a><span data-ttu-id="9ef81-184">nx_dns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="9ef81-184">nx_dns_cache_notify_clear</span></span>

<span data-ttu-id="9ef81-185">DNS キャッシュ満杯通知関数をクリアする</span><span class="sxs-lookup"><span data-stu-id="9ef81-185">Clear the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-186">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-186">Prototype</span></span>

```c
UINT     nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="9ef81-187">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-187">Description</span></span>

<span data-ttu-id="9ef81-188">このサービスは、キャッシュ満杯通知関数をクリアします。</span><span class="sxs-lookup"><span data-stu-id="9ef81-188">This service clears the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-189">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-189">Input Parameters</span></span>

- <span data-ttu-id="9ef81-190">**dns_ptr**: DNS 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-190">**dns_ptr**: Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-191">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-191">Return Values</span></span>

- <span data-ttu-id="9ef81-192">**NX_SUCCESS**: (0x00) DNS キャッシュ通知が正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="9ef81-192">**NX_SUCCESS**: (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="9ef81-193">NX_DNS_PARAM_ERROR: (0xA8) DNS ID が無効です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-193">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="9ef81-194">NX_PTR_ERROR: (0x07) DNS ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-194">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-195">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-195">Allowed From</span></span>

<span data-ttu-id="9ef81-196">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-197">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-197">Example</span></span>

```c
/* Clear the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a><span data-ttu-id="9ef81-198">nx_dns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="9ef81-198">nx_dns_cache_notify_set</span></span>

<span data-ttu-id="9ef81-199">DNS キャッシュ満杯通知関数を設定する</span><span class="sxs-lookup"><span data-stu-id="9ef81-199">Set the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-200">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-200">Prototype</span></span>

```c
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr, VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a><span data-ttu-id="9ef81-201">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-201">Description</span></span>

<span data-ttu-id="9ef81-202">このサービスは、キャッシュ満杯通知関数を設定します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-202">This service sets the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-203">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-203">Input Parameters</span></span>

- <span data-ttu-id="9ef81-204">**dns_ptr**: DNS 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-204">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="9ef81-205">**cache_full_notify_cb**: キャッシュがいっぱいになったときに呼び出されるコールバック関数。</span><span class="sxs-lookup"><span data-stu-id="9ef81-205">**cache_full_notify_cb**: The callback function to be invoked when cache become full.</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-206">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-206">Return Values</span></span>

- <span data-ttu-id="9ef81-207">**NX_SUCCESS**: (0x00) DNS キャッシュ通知が正常に設定されました</span><span class="sxs-lookup"><span data-stu-id="9ef81-207">**NX_SUCCESS**: (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="9ef81-208">NX_DNS_PARAM_ERROR: (0xA8) DNS ID が無効です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-208">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="9ef81-209">NX_PTR_ERROR: (0x07) DNS ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-209">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-210">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-210">Allowed From</span></span>

<span data-ttu-id="9ef81-211">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-211">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-212">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-212">Example</span></span>

```c
/* Set the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set.  */
 
```

## <a name="nx_dns_cname_get"></a><span data-ttu-id="9ef81-213">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="9ef81-213">nx_dns_cname_get</span></span>

<span data-ttu-id="9ef81-214">入力ホスト名の正規名を検索する</span><span class="sxs-lookup"><span data-stu-id="9ef81-214">Look up the canonical name for the input hostname</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-215">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-215">Prototype</span></span>
```c
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                      UCHAR *record_buffer, UINT buffer_size, 
                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9ef81-216">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-216">Description</span></span>

<span data-ttu-id="9ef81-217">*nx_dns.h* で NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスは、指定されたドメイン名で CNAME タイプのクエリを送信して正規のドメイン名を取得します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-217">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined in *nx_dns.h*, this service sends a query of type CNAME with the specified domain name to obtain the canonical domain name.</span></span> <span data-ttu-id="9ef81-218">DNS クライアントは、DNS サーバー応答で返された CNAME 文字列を、*record_buffer* のメモリ位置にコピーします。</span><span class="sxs-lookup"><span data-stu-id="9ef81-218">The DNS Client copies the CNAME string returned in the DNS Server response into the *record_buffer* memory location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-219">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-219">Input Parameters</span></span>

- <span data-ttu-id="9ef81-220">**dns_ptr**: DNS クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-220">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="9ef81-221">**host_name**: CNAME データを取得するホスト名へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-221">**host_name**: Pointer to host name to obtain CNAME data for</span></span>
- <span data-ttu-id="9ef81-222">**record_buffer**: CNAME データを抽出する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-222">**record_buffer**: Pointer to location to extract CNAME data into</span></span>
- <span data-ttu-id="9ef81-223">**buffer_size**: CNAME データを保持するバッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="9ef81-223">**buffer_size**: Size of buffer to hold CNAME data</span></span>
- <span data-ttu-id="9ef81-224">**wait_option**: DNS サーバー応答を受信する際の待機オプション</span><span class="sxs-lookup"><span data-stu-id="9ef81-224">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-225">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-225">Return Values</span></span>

- <span data-ttu-id="9ef81-226">**NX_SUCCESS**: (0x00) CNAME データが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="9ef81-226">**NX_SUCCESS**: (0x00) Successfully obtained CNAME data</span></span>
- <span data-ttu-id="9ef81-227">**NX_DNS_NO_SERVER**: (0xA1) クライアントのサーバー リストが空です</span><span class="sxs-lookup"><span data-stu-id="9ef81-227">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="9ef81-228">**NX_DNS_QUERY_FAILED**: (0xA3) 有効な DNS 応答を受信していません</span><span class="sxs-lookup"><span data-stu-id="9ef81-228">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="9ef81-229">NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-229">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9ef81-230">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-230">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="9ef81-231">NX_DNS_PARAM_ERROR: (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-231">NX_DNS_PARAM_ERROR: (0xA8) Invalid non-pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-232">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-232">Allowed From</span></span>

<span data-ttu-id="9ef81-233">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-233">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-234">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-234">Example</span></span>

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

## <a name="nx_dns_create"></a><span data-ttu-id="9ef81-235">nx_dns_create</span><span class="sxs-lookup"><span data-stu-id="9ef81-235">nx_dns_create</span></span>

<span data-ttu-id="9ef81-236">DNS クライアント インスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="9ef81-236">Create a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-237">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-237">Prototype</span></span>

```c
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```

### <a name="description"></a><span data-ttu-id="9ef81-238">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-238">Description</span></span>

<span data-ttu-id="9ef81-239">このサービスでは、以前に作成された IP インスタンスの DNS クライアント インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-239">This service creates a DNS Client instance for the previously created IP instance.</span></span>

>[!NOTE]
><span data-ttu-id="9ef81-240">アプリケーションでは、DNS クライアントによって使用されるパケット プールのパケット ペイロードが、最大 512 バイトの DNS メッセージに加えて、UDP、IP、イーサネットの各ヘッダーを含めることができる十分な大きさであることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef81-240">The application must ensure that the packet payload of the packet pool used by the DNS Client is large enough for the maximum 512 byte DNS message, plus UDP, IP and Ethernet headers.</span></span> <span data-ttu-id="9ef81-241">DNS クライアントが独自のパケット プールを作成する場合、これは、NX_DNS_PACKET_POOL_SIZE と NX_DNS_PACKET_PAYLOAD で定義されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-241">If the DNS Client creates its own packet pool, this is defined by NX_DNS_PACKET_POOL_SIZE and NX_DNS_PACKET_PAYLOAD.</span></span> <span data-ttu-id="9ef81-242">DNS クライアント アプリケーションが、以前に作成されたパケット プールを提供する場合、IPv4 DNS クライアントのペイロードは、DNS メッセージの最大サイズである 512 バイトに、IP ヘッダー用の 20 バイト、UDP ヘッダー用の 8 バイト、イーサネット ヘッダー用の 14 バイトを加えたサイズである必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef81-242">If the DNS Client application prefers to supply a previously created packet pool, the payload for IPv4 DNS Client should be 512 bytes for the maximum DNS plus 20 bytes for the IP header, 8 bytes for the UDP header and 14 bytes for the Ethernet header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-243">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-243">Input Parameters</span></span>

- <span data-ttu-id="9ef81-244">**dns_ptr**: DNS クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-244">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="9ef81-245">**ip_ptr**: 以前に作成された IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-245">**ip_ptr**: Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="9ef81-246">**domain_name**: DNS インスタンスのドメイン名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-246">**domain_name**: Pointer to domain name for DNS instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-247">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-247">Return Values</span></span>

- <span data-ttu-id="9ef81-248">**NX_SUCCESS**: (0x00) DNS が正常に作成されました</span><span class="sxs-lookup"><span data-stu-id="9ef81-248">**NX_SUCCESS**: (0x00) Successful DNS create</span></span>
- <span data-ttu-id="9ef81-249">**NX_DNS_ERROR**: (0xA0) DNS 作成エラー</span><span class="sxs-lookup"><span data-stu-id="9ef81-249">**NX_DNS_ERROR**: (0xA0) DNS create error</span></span>
- <span data-ttu-id="9ef81-250">NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-250">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9ef81-251">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-251">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-252">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-252">Allowed From</span></span>

<span data-ttu-id="9ef81-253">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-253">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-254">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-254">Example</span></span>

```c
/* Create a DNS Client instance.  */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created.  */
```
## <a name="nx_dns_delete"></a><span data-ttu-id="9ef81-255">nx_dns_delete</span><span class="sxs-lookup"><span data-stu-id="9ef81-255">nx_dns_delete</span></span>

<span data-ttu-id="9ef81-256">DNS クライアント インスタンスを削除する</span><span class="sxs-lookup"><span data-stu-id="9ef81-256">Delete a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-257">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-257">Prototype</span></span>

```c
UINT     nx_dns_delete(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="9ef81-258">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-258">Description</span></span>

<span data-ttu-id="9ef81-259">このサービスは、以前に作成された DNS クライアント インスタンスを削除し、そのリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-259">This service deletes a previously created DNS Client instance and frees up its resources.</span></span> 
>[!NOTE]
> <span data-ttu-id="9ef81-260">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** が定義されており、DNS クライアントにユーザー定義のパケット プールが割り当てられている場合、DNS クライアントの不要になったパケット プールを削除するのはアプリケーションの役割です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-260">If **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** is defined and the DNS Client was assigned a user defined packet pool, it is up to the application to delete the DNS Client packet pool if it no longer needs it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-261">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-261">Input Parameters</span></span>

- <span data-ttu-id="9ef81-262">**dns_ptr**: 以前に作成された DNS **クライアント** インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-262">**dns_ptr**: Pointer to previously created DNS **Client** instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-263">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-263">Return Values</span></span>

- <span data-ttu-id="9ef81-264">**NX_SUCCESS**: (0x00) DNS クライアントが正常に削除されました。</span><span class="sxs-lookup"><span data-stu-id="9ef81-264">**NX_SUCCESS**: (0x00) Successful DNS Client delete.</span></span>
- <span data-ttu-id="9ef81-265">NX_PTR_ERROR: (0x07) IP または DNS クライアント ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-265">NX_PTR_ERROR: (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="9ef81-266">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-266">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-267">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-267">Allowed From</span></span>

<span data-ttu-id="9ef81-268">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-268">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-269">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-269">Example</span></span>

```c
/* Delete a DNS Client instance.  */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted.  */
```
## <a name="nx_dns_domain_name_server_get"></a><span data-ttu-id="9ef81-270">nx_dns_domain_name_server_get</span><span class="sxs-lookup"><span data-stu-id="9ef81-270">nx_dns_domain_name_server_get</span></span>

<span data-ttu-id="9ef81-271">入力ドメイン ゾーンの権威ネーム サーバーを検索する</span><span class="sxs-lookup"><span data-stu-id="9ef81-271">Look up the authoritative name servers for the input domain zone</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-272">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-272">Prototype</span></span>

```c
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9ef81-273">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-273">Description</span></span>

<span data-ttu-id="9ef81-274">NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスは指定されたドメイン名で NS タイプのクエリを送信して、入力ドメイン名のネーム サーバーを取得します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-274">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type NS with the specified domain name to obtain the name servers for the input domain name.</span></span> <span data-ttu-id="9ef81-275">DNS クライアントは、DNS サーバー応答で返された NS レコードを、*record_buffer* のメモリ位置にコピーします。</span><span class="sxs-lookup"><span data-stu-id="9ef81-275">The DNS Client copies the NS record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="9ef81-276">データを受信するには、*record_buffer* が 4 バイト アラインされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef81-276">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="9ef81-277">NetX DNS クライアントでは、NS データ型の NX_DNS_NS_ENTRY は、2 つの 4 バイトのパラメーターとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-277">In NetX DNS Client the NS data type, NX_DNS_NS_ENTRY, is saved as two 4-byte parameters:</span></span>

- <span data-ttu-id="9ef81-278">**nx_dns_ns_ipv4_address**: ネーム サーバーの IPv4 アドレス</span><span class="sxs-lookup"><span data-stu-id="9ef81-278">**nx_dns_ns_ipv4_address**: Name server’s IPv4 address</span></span>
- <span data-ttu-id="9ef81-279">**nx_dns_ns_hostname_ptr**: ネーム サーバーのホスト名へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-279">**nx_dns_ns_hostname_ptr**: Pointer to the name server’s hostname</span></span>

<span data-ttu-id="9ef81-280">次に示すバッファーには、4 つの NX_DNS_NS_ENTRY レコードが格納されています。</span><span class="sxs-lookup"><span data-stu-id="9ef81-280">The buffer shown below contains four NX_DNS_NS_ENTRY records.</span></span> <span data-ttu-id="9ef81-281">各エントリのホスト名文字列へのポインターは、バッファーの下半分にある対応するホスト名文字列を指します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-281">The pointer to host name string in each entry points to the corresponding host name string in the bottom half of the buffer:</span></span>

![4 つの N X D N S N S エントリ レコードが格納されたバッファーの図。](media/image3.png)

<span data-ttu-id="9ef81-283">入力 *record_buffer* にサーバー応答内のすべての NS データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-283">If the input *record_buffer* cannot hold all the NS data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="9ef81-284">\**record_count* で返された NS レコードの数を使用して、アプリケーションは *record_buffer* 内の各レコードの IP アドレスとホスト名を解析できます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-284">With the number of NS records returned in \**record_count,* the application can parse the IP address and host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-285">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-285">Input Parameters</span></span>

- <span data-ttu-id="9ef81-286">**dns_ptr**: DNS クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-286">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="9ef81-287">**host_name**: NS データを取得するホスト名へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-287">**host_name**: Pointer to host name to obtain NS data for</span></span>
- <span data-ttu-id="9ef81-288">**record_buffer**: NS データを抽出する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-288">**record_buffer**: Pointer to location to extract NS data into</span></span>
- <span data-ttu-id="9ef81-289">**buffer_size**: NS データを保持するバッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="9ef81-289">**buffer_size**: Size of buffer to hold NS data</span></span>
- <span data-ttu-id="9ef81-290">**record_count**: 取得した NS レコードの数へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-290">**record_count**: Pointer to the number of NS records retrieved</span></span>
- <span data-ttu-id="9ef81-291">**wait_option**: DNS サーバー応答を受信する際の待機オプション</span><span class="sxs-lookup"><span data-stu-id="9ef81-291">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-292">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-292">Return Values</span></span>

- <span data-ttu-id="9ef81-293">**NX_SUCCESS**: (0x00) NS データが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="9ef81-293">**NX_SUCCESS**: (0x00) Successfully obtained NS data</span></span>
- <span data-ttu-id="9ef81-294">**NX_DNS_NO_SERVER**: (0xA1) クライアントのサーバー リストが空です</span><span class="sxs-lookup"><span data-stu-id="9ef81-294">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="9ef81-295">**NX_DNS_QUERY_FAILED**: (0xA3) 有効な DNS 応答を受信していません</span><span class="sxs-lookup"><span data-stu-id="9ef81-295">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="9ef81-296">NX_DNS_PARAM_ERROR: (0xA8) DNS ID が無効です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-296">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="9ef81-297">NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-297">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9ef81-298">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-298">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-299">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-299">Allowed From</span></span>

<span data-ttu-id="9ef81-300">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-300">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-301">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-301">Example</span></span>
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

## <a name="nx_dns_domain_mail_exchange_get"></a><span data-ttu-id="9ef81-302">nx_dns_domain_mail_exchange_get</span><span class="sxs-lookup"><span data-stu-id="9ef81-302">nx_dns_domain_mail_exchange_get</span></span>

<span data-ttu-id="9ef81-303">入力ホスト名のメール交換を検索する</span><span class="sxs-lookup"><span data-stu-id="9ef81-303">Look up the mail exchange(s) for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-304">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-304">Prototype</span></span>
```c
UINT     nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                        VOID *record_buffer,                                        
                                        UINT buffer_size, 
                                        UINT *record_count, 
                                        ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="9ef81-305">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-305">Description</span></span>

<span data-ttu-id="9ef81-306">NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスは指定されたドメイン名で MX タイプのクエリを送信して、入力ドメイン名のメール交換を取得します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-306">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type MX with the specified domain name to obtain the mail exchange for the input domain name.</span></span> <span data-ttu-id="9ef81-307">DNS クライアントは、DNS サーバー応答で返された MX レコードを、*record_buffer* のメモリ位置にコピーします。</span><span class="sxs-lookup"><span data-stu-id="9ef81-307">The DNS Client copies the MX record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

>[!NOTE]
><span data-ttu-id="9ef81-308">データを受信するには、*record_buffer* が 4 バイト アラインされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef81-308">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="9ef81-309">NetX DNS クライアントでは、メール交換レコード NX_DNS_MAIL_EXCHANGE_ENTRY は、4 つのパラメーター (合計 12 バイト) として保存されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-309">In NetX DNS Client, the mail exchange record type, NX_DNS_MAIL_EXCHANGE_ENTRY, is saved as four parameters, totaling 12 bytes:</span></span>

- <span data-ttu-id="9ef81-310">**nx_dns_mx_ipv4_address**: メール交換 IPv4 アドレス (4 バイト)</span><span class="sxs-lookup"><span data-stu-id="9ef81-310">**nx_dns_mx_ipv4_address**: Mail exchange IPv4 address 4 bytes</span></span>
- <span data-ttu-id="9ef81-311">**nx_dns_mx_preference**: 優先順位 (2 バイト)</span><span class="sxs-lookup"><span data-stu-id="9ef81-311">**nx_dns_mx_preference**: Preference 2 bytes</span></span>
- <span data-ttu-id="9ef81-312">**nx_dns_mx_reserved0**: 予約済み (2 バイト)</span><span class="sxs-lookup"><span data-stu-id="9ef81-312">**nx_dns_mx_reserved0**: Reserved 2 bytes</span></span>
- <span data-ttu-id="9ef81-313">**nx_dns_mx_hostname_ptr**: メール交換サーバー ホスト名へのポインター (4 バイト)</span><span class="sxs-lookup"><span data-stu-id="9ef81-313">**nx_dns_mx_hostname_ptr**: Pointer to mail exchange server host name 4 bytes</span></span>

<span data-ttu-id="9ef81-314">4 つの MX レコードが格納されたバッファーを次に示します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-314">A buffer containing four MX records is shown below.</span></span> <span data-ttu-id="9ef81-315">各レコードには、上記の一覧の固定長データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9ef81-315">Each record contains the fixed length data from the list above.</span></span> <span data-ttu-id="9ef81-316">メール交換サーバー ホスト名へのポインターは、バッファーの下部にある対応するホスト名を指します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-316">The pointer to the mail exchange server host name points to the corresponding host name at the bottom of the buffer.</span></span>

![4 つの M X レコードが格納されたバッファーを示す図。](media/image4.png)

<span data-ttu-id="9ef81-318">入力 *record_buffer* にサーバー応答内のすべての MX データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-318">If the input *record_buffer* cannot hold all the MX data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="9ef81-319">\**record_countt* で返された MX レコードの数を使用して、アプリケーションは *record_buffer* 内の各レコードのメール ホスト名などの MX パラメーターを解析できます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-319">With the number of MX records returned in \**record_count,* the application can parse the MX parameters, including the mail host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-320">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-320">Input Parameters</span></span>

- <span data-ttu-id="9ef81-321">**dns_ptr**: DNS クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-321">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="9ef81-322">**host_name**: MX データを取得するホスト名へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-322">**host_name**: Pointer to host name to obtain MX data for</span></span>
- <span data-ttu-id="9ef81-323">**record_buffer**: MX データを抽出する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-323">**record_buffer**: Pointer to location to extract MX data into</span></span>
- <span data-ttu-id="9ef81-324">**buffer_size**: MX データを保持するバッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="9ef81-324">**buffer_size**: Size of buffer to hold MX data</span></span>
- <span data-ttu-id="9ef81-325">**record_count**: 取得した MX レコードの数へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-325">**record_count**: Pointer to the number of MX records retrieved</span></span>
- <span data-ttu-id="9ef81-326">**wait_option**: DNS サーバー応答を受信する際の待機オプション</span><span class="sxs-lookup"><span data-stu-id="9ef81-326">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-327">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-327">Return Values</span></span>

- <span data-ttu-id="9ef81-328">**NX_SUCCESS**: (0x00) MX データが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="9ef81-328">**NX_SUCCESS**: (0x00) Successfully obtained MX data</span></span>
- <span data-ttu-id="9ef81-329">**NX_DNS_NO_SERVER**: (0xA1) クライアントのサーバー リストが空です</span><span class="sxs-lookup"><span data-stu-id="9ef81-329">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="9ef81-330">**NX_DNS_QUERY_FAILED**: (0xA3) 有効な DNS 応答を受信していません</span><span class="sxs-lookup"><span data-stu-id="9ef81-330">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="9ef81-331">NX_DNS_PARAM_ERROR: (0xA8) DNS ID が無効です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-331">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="9ef81-332">NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-332">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9ef81-333">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-333">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-334">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-334">Allowed From</span></span>

<span data-ttu-id="9ef81-335">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-335">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-336">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-336">Example</span></span>
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


## <a name="nx_dns_domain_service_get"></a><span data-ttu-id="9ef81-337">nx_dns_domain_service_get</span><span class="sxs-lookup"><span data-stu-id="9ef81-337">nx_dns_domain_service_get</span></span>

<span data-ttu-id="9ef81-338">入力ホスト名で提供されるサービスを検索する</span><span class="sxs-lookup"><span data-stu-id="9ef81-338">Look up the service(s) provided by the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-339">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-339">Prototype</span></span>

```c
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9ef81-340">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-340">Description</span></span>

<span data-ttu-id="9ef81-341">NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスは指定されたドメイン名で SRV タイプのクエリを送信して、指定されたドメインに関連付けられているサービスとそのポート番号を検索します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-341">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SRV with the specified domain name to look up the service(s) and their port number associated with the specified domain.</span></span> <span data-ttu-id="9ef81-342">DNS クライアントは、DNS サーバー応答で返された SRV レコードを、*record_buffer* のメモリ位置にコピーします。</span><span class="sxs-lookup"><span data-stu-id="9ef81-342">The DNS Client copies the SRV record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="9ef81-343">データを受信するには、*record_buffer* が 4 バイト アラインされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef81-343">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="9ef81-344">NetX DNS クライアントでは、サービス レコード NX_DNS_SRV_ ENTRY は、6 個のパラメーター (合計 16 バイト) として保存されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-344">In NetX DNS Client, the service record type, NX_DNS_SRV_ ENTRY, is saved as six parameters, totaling 16 bytes.</span></span> <span data-ttu-id="9ef81-345">これにより、可変長の SRV データをメモリ効率の高い方法で格納できます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-345">This enables variable length SRV data to be stored in a memory efficient manner:</span></span>

- <span data-ttu-id="9ef81-346">**サーバー IPv4 アドレス**: nx_dns_srv_ipv4_address (4 バイト)</span><span class="sxs-lookup"><span data-stu-id="9ef81-346">**Server IPv4 address**: nx_dns_srv_ipv4_address 4 bytes</span></span>
- <span data-ttu-id="9ef81-347">**サーバーの優先順位**: nx_dns_srv_priority (2 バイト)</span><span class="sxs-lookup"><span data-stu-id="9ef81-347">**Server priority**: nx_dns_srv_priority 2 bytes</span></span>
- <span data-ttu-id="9ef81-348">**サーバーの重み**: nx_dns_srv_weight (2 バイト)</span><span class="sxs-lookup"><span data-stu-id="9ef81-348">**Server weight**: nx_dns_srv_weight 2 bytes</span></span>
- <span data-ttu-id="9ef81-349">**サービス ポート番号**: nx_dns_srv_port_number (2 バイト)</span><span class="sxs-lookup"><span data-stu-id="9ef81-349">**Service port number**: nx_dns_srv_port_number 2 bytes</span></span>
- <span data-ttu-id="9ef81-350">**4 バイト アラインメント用に予約済み**: nx_dns_srv_reserved0 (2 バイト)</span><span class="sxs-lookup"><span data-stu-id="9ef81-350">**Reserved for 4-byte alignment**: nx_dns_srv_reserved0 2 bytes</span></span>
- <span data-ttu-id="9ef81-351">**サーバー ホスト名へのポインター**: \*nx_dns_srv_hostname_ptr (4 バイト)</span><span class="sxs-lookup"><span data-stu-id="9ef81-351">**Pointer to server host name**: \*nx_dns_srv_hostname_ptr 4 bytes</span></span>

<span data-ttu-id="9ef81-352">指定されたバッファーに 4 つの SRV レコードが格納されています。</span><span class="sxs-lookup"><span data-stu-id="9ef81-352">Four SRV records are stored in the supplied buffer.</span></span> <span data-ttu-id="9ef81-353">各 NX_DNS_SRV_ENTRY レコードには、レコード バッファーの下部にある対応するホスト名文字列を指すポインター *nx_dns_srv_hostname_ptr* が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9ef81-353">Each NX_DNS_SRV_ENTRY record contains a pointer, *nx_dns_srv_hostname_ptr*, that points to the corresponding host name string in the bottom of the record buffer:</span></span>

![指定されたバッファーに格納されている 4 個の S R V レコードの図。](media/image5.png)

<span data-ttu-id="9ef81-355">入力 *record_buffer* にサーバー応答内のすべての SRV データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-355">If the input *record_buffer* cannot hold all the SRV data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="9ef81-356">\**record_count* で返された SRV レコードの数を使用して、アプリケーションは *record_buffer* 内の各レコードのサーバー ホスト名などの SRV パラメーターを解析できます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-356">With the number of SRV records returned in \**record_count,* the application can parse the SRV parameters, including the server host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-357">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-357">Input Parameters</span></span>

- <span data-ttu-id="9ef81-358">**dns_ptr**: DNS クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-358">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="9ef81-359">**host_name**: SRV データを取得するホスト名へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-359">**host_name**: Pointer to host name to obtain SRV data for</span></span>
- <span data-ttu-id="9ef81-360">**record_buffer**: SRV データを抽出する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-360">**record_buffer**: Pointer to location to extract SRV data into</span></span>
- <span data-ttu-id="9ef81-361">**buffer_size**: SRV データを保持するバッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="9ef81-361">**buffer_size**: Size of buffer to hold SRV data</span></span>
- <span data-ttu-id="9ef81-362">**record_count**: 取得した SRV レコードの数へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-362">**record_count**: Pointer to the number of SRV records retrieved</span></span>
- <span data-ttu-id="9ef81-363">**wait_option**: DNS サーバー応答を受信する際の待機オプション</span><span class="sxs-lookup"><span data-stu-id="9ef81-363">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-364">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-364">Return Values</span></span>

- <span data-ttu-id="9ef81-365">**NX_SUCCESS**: (0x00) SRV データが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="9ef81-365">**NX_SUCCESS**: (0x00) Successfully obtained SRV data</span></span>
- <span data-ttu-id="9ef81-366">**NX_DNS_NO_SERVER**: (0xA1) クライアントのサーバー リストが空です</span><span class="sxs-lookup"><span data-stu-id="9ef81-366">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="9ef81-367">**NX_DNS_QUERY_FAILED**: (0xA3) 有効な DNS 応答を受信していません</span><span class="sxs-lookup"><span data-stu-id="9ef81-367">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="9ef81-368">NX_DNS_PARAM_ERROR: (0xA8) DNS ID が無効です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-368">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="9ef81-369">NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-369">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9ef81-370">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-370">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-371">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-371">Allowed From</span></span>

<span data-ttu-id="9ef81-372">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-372">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-373">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-373">Example</span></span>

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

## <a name="nx_dns_get_serverlist_size"></a><span data-ttu-id="9ef81-374">nx_dns_get_serverlist_size</span><span class="sxs-lookup"><span data-stu-id="9ef81-374">nx_dns_get_serverlist_size</span></span>

<span data-ttu-id="9ef81-375">DNS クライアントのサーバー リストのサイズを返す</span><span class="sxs-lookup"><span data-stu-id="9ef81-375">Return the size of the DNS Client’s Server list</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-376">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-376">Prototype</span></span>

```c
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```

### <a name="description"></a><span data-ttu-id="9ef81-377">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-377">Description</span></span>

<span data-ttu-id="9ef81-378">このサービスは、クライアントのリスト内の有効な DNS サーバーの数を返します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-378">This service returns the number of valid DNS Servers in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-379">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-379">Input Parameters</span></span>

- <span data-ttu-id="9ef81-380">**dns_ptr**: DNS 制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-380">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="9ef81-381">**size**: リスト内のサーバーの数を返します</span><span class="sxs-lookup"><span data-stu-id="9ef81-381">**size**: Returns the number of servers in the list</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-382">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-382">Return Values</span></span>

- <span data-ttu-id="9ef81-383">**NX_SUCCESS**: (0x00) DNS サーバー リストのサイズが正常に返されました</span><span class="sxs-lookup"><span data-stu-id="9ef81-383">**NX_SUCCESS**: (0x00) DNS Server list size successfully returned</span></span>
- <span data-ttu-id="9ef81-384">NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-384">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="9ef81-385">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-385">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-386">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-386">Allowed From</span></span>

<span data-ttu-id="9ef81-387">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-387">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-388">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-388">Example</span></span>

```c
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list.  */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned.  */
```

## <a name="nx_dns_info_by_name_get"></a><span data-ttu-id="9ef81-389">nx_dns_info_by_name_get</span><span class="sxs-lookup"><span data-stu-id="9ef81-389">nx_dns_info_by_name_get</span></span>

<span data-ttu-id="9ef81-390">ホスト名に基づいて DNS サーバーの IP アドレスとポートを返す</span><span class="sxs-lookup"><span data-stu-id="9ef81-390">Return ip address and port of DNS server by host name</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-391">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-391">Prototype</span></span>

```c
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9ef81-392">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-392">Description</span></span>

<span data-ttu-id="9ef81-393">このサービスは、DNS クエリによる入力ホスト名に基づいて、サーバーの IP とポート (サービス レコード) を返します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-393">This service returns the Server IP and port (service record) based on the input host name by DNS query.</span></span> <span data-ttu-id="9ef81-394">サービス レコードが見つからない場合、このルーチンは入力アドレス ポインターに 0 の IP アドレスを返し、0 以外のエラー状態を返してエラーを通知します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-394">If a service record is not found, this routine returns a zero IP address in the input address pointer and a non-zero error status return to signal an error.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-395">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-395">Input Parameters</span></span>

- <span data-ttu-id="9ef81-396">**dns_ptr**: DNS 制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-396">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="9ef81-397">**host_name**: ホスト名バッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-397">**host_name**: Pointer to host name buffer</span></span>
- <span data-ttu-id="9ef81-398">**host_address_ptr**: 返されるアドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-398">**host_address_ptr**: Pointer to address to return</span></span>
- <span data-ttu-id="9ef81-399">**host_port_ptr**: 返されるポートへのポインター wait_option: DNS 応答の待機オプション</span><span class="sxs-lookup"><span data-stu-id="9ef81-399">**host_port_ptr**: Pointer to port to return wait_option Wait option for the DNS response</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-400">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-400">Return Values</span></span>

- <span data-ttu-id="9ef81-401">**NX_SUCCESS**: (0x00) DNS サーバー レコードが正常に返されました</span><span class="sxs-lookup"><span data-stu-id="9ef81-401">**NX_SUCCESS**: (0x00) DNS Server record successfully returned</span></span>
- <span data-ttu-id="9ef81-402">**NX_DNS_NO_SERVER**: (0xA1) ホスト名のクエリを送信するためにクライアントに登録されている DNS サーバーがありません</span><span class="sxs-lookup"><span data-stu-id="9ef81-402">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server registered with Client to send query on hostname</span></span>
- <span data-ttu-id="9ef81-403">**NX_DNS_QUERY_FAILED**: (0xA3) DNS クエリが失敗しました。クライアントのリストに DNS サーバーからの応答がないか、入力ホスト名で使用できるサービス レコードがありません。</span><span class="sxs-lookup"><span data-stu-id="9ef81-403">**NX_DNS_QUERY_FAILED**: (0xA3) DNS query failed; no response from any DNS servers in Client list or no service record is available for the input hostname.</span></span>
- <span data-ttu-id="9ef81-404">NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-404">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9ef81-405">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-405">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-406">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-406">Allowed From</span></span>

<span data-ttu-id="9ef81-407">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-407">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-408">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-408">Example</span></span>
```c
ULONG         ip_address;
USHORT         port;

/* Attempt to resolve the IP address and ports for this host name.  */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned.  */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a><span data-ttu-id="9ef81-409">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="9ef81-409">nx_dns_ipv4_address_by_name_get</span></span>

<span data-ttu-id="9ef81-410">入力ホスト名の IPv4 アドレスを検索する</span><span class="sxs-lookup"><span data-stu-id="9ef81-410">Look up the IPv4 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-411">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-411">Prototype</span></span>

```c
UINT nx_dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                       UCHAR *host_name_ptr, VOID *buffer, 
                                       UINT buffer_size, 
                                       UINT *record_count,
                                       ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9ef81-412">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-412">Description</span></span>

<span data-ttu-id="9ef81-413">このサービスは、指定されたホスト名で A タイプのクエリを送信して、入力ホスト名の IP アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-413">This service sends a query of Type A with the specified host name to obtain the IP addresses for the input host name.</span></span> <span data-ttu-id="9ef81-414">DNS クライアントは、DNS サーバー応答で返された A レコードの IPv4 アドレスを、*record_buffer* のメモリ位置にコピーします。</span><span class="sxs-lookup"><span data-stu-id="9ef81-414">The DNS Client copies the IPv4 address from the A record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="9ef81-415">データを受信するには、*record_buffer* が 4 バイト アラインされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ef81-415">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="9ef81-416">次に示すように、4 バイト アラインされたバッファーに複数の IPv4 アドレスが格納されています。</span><span class="sxs-lookup"><span data-stu-id="9ef81-416">Multiple IPv4 addresses are stored in the 4-byte aligned buffer as shown below:</span></span>

![4 バイト アラインされたバッファーに格納されている複数の I P v 4 アドレスの図。](media/image6.png)

<span data-ttu-id="9ef81-418">指定されたバッファーにすべての IP アドレス データを保持できない場合、残りの A レコードは *record_buffer* に格納されません。</span><span class="sxs-lookup"><span data-stu-id="9ef81-418">If the supplied buffer cannot hold all the IP address data, the remaining A records are not stored in *record_buffer*.</span></span> <span data-ttu-id="9ef81-419">これにより、アプリケーションは、サーバー応答の使用可能な IP アドレス データの 1 つ、一部、またはすべてを取得できます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-419">This enables the application to retrieve one, some or all of the available IP address data in the server reply.</span></span>

<span data-ttu-id="9ef81-420">\**record_count* で返される A レコードの数を使用して、アプリケーションは *record_buffer* 内の IPv4 アドレス データを解析できます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-420">With the number of A records returned in \**record_count* the application can parse the IPv4 address data from the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-421">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-421">Input Parameters</span></span>

- <span data-ttu-id="9ef81-422">**dns_ptr**: DNS クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-422">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="9ef81-423">**host_name_ptr**: IPv4 アドレスを取得するホスト名へのポインター buffer: IPv4 データを抽出する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-423">**host_name_ptr**: Pointer to host name to obtain IPv4 address buffer Pointer to location to extract IPv4 data into</span></span>
- <span data-ttu-id="9ef81-424">**buffer_size**: IPv4 データを保持するバッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="9ef81-424">**buffer_size**: Size of buffer to hold IPv4 data</span></span>
- <span data-ttu-id="9ef81-425">**wait_option**: DNS サーバー応答を受信する際の待機オプション</span><span class="sxs-lookup"><span data-stu-id="9ef81-425">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-426">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-426">Return Values</span></span>

- <span data-ttu-id="9ef81-427">**NX_SUCCESS**: (0x00) IPv4 データが正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="9ef81-427">**NX_SUCCESS**: (0x00) Successfully obtained IPv4 data</span></span>
- <span data-ttu-id="9ef81-428">**NX_DNS_NO_SERVER**: (0xA1) クライアントのサーバー リストが空です</span><span class="sxs-lookup"><span data-stu-id="9ef81-428">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="9ef81-429">**NX_DNS_QUERY_FAILED**: (0xA3) 有効な DNS 応答を受信していません</span><span class="sxs-lookup"><span data-stu-id="9ef81-429">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="9ef81-430">NX_DNS_PARAM_ERROR: (0xA8) 入力パラメーターが無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-430">NX_DNS_PARAM_ERROR: (0xA8) Invalid input parameter.</span></span>
- <span data-ttu-id="9ef81-431">NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-431">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="9ef81-432">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-432">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-433">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-433">Allowed From</span></span>

<span data-ttu-id="9ef81-434">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-434">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-435">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-435">Example</span></span>

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

## <a name="nx_dns_host_by_address_get"></a><span data-ttu-id="9ef81-436">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="9ef81-436">nx_dns_host_by_address_get</span></span>

<span data-ttu-id="9ef81-437">IP アドレスからホスト名を検索する</span><span class="sxs-lookup"><span data-stu-id="9ef81-437">Look up a host name from an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-438">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-438">Prototype</span></span>

```c
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9ef81-439">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-439">Description</span></span>

<span data-ttu-id="9ef81-440">このサービスは、アプリケーションによって以前に指定された 1 つ以上の DNS サーバーに、指定された IP アドレスの名前解決を要求します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-440">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="9ef81-441">成功すると、*host_name_ptr* で指定された文字列で、NULL で終わるホスト名が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-441">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-442">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-442">Input Parameters</span></span>

- <span data-ttu-id="9ef81-443">**dns_ptr**: 以前に作成された DNS インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-443">**dns_ptr**: Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="9ef81-444">**ip_address**: 名前に解決する IP アドレス</span><span class="sxs-lookup"><span data-stu-id="9ef81-444">**ip_address**: IP address to resolve into a name</span></span>
- <span data-ttu-id="9ef81-445">**host_name_ptr**: ホスト名の宛先領域へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-445">**host_name_ptr**: Pointer to destination area for host name</span></span>
- <span data-ttu-id="9ef81-446">**max_host_name_size**: ホスト名の宛先領域のサイズ</span><span class="sxs-lookup"><span data-stu-id="9ef81-446">**max_host_name_size**: Size of destination area for host name</span></span>
- <span data-ttu-id="9ef81-447">**wait_option**: 各 DNS クエリおよびクエリ再試行の後に、サービスが DNS サーバーの応答を待機する時間をタイマー刻みで定義します。待機オプションは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="9ef81-447">**wait_option**: Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry The wait options are defined as follows:</span></span>
    - <span data-ttu-id="9ef81-448">**タイムアウト値**: (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択すると、DNS 解決を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-448">**timeout value**: (0x00000001-0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>
    - <span data-ttu-id="9ef81-449">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、DNS サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-449">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-450">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-450">Return Values</span></span>

- <span data-ttu-id="9ef81-451">**NX_SUCCESS**: (0x00) DNS 解決が成功しました</span><span class="sxs-lookup"><span data-stu-id="9ef81-451">**NX_SUCCESS**: (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="9ef81-452">**NX_DNS_TIMEOUT**: (0xA2) DNS ミューテックスの取得がタイムアウトしました</span><span class="sxs-lookup"><span data-stu-id="9ef81-452">**NX_DNS_TIMEOUT**: (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="9ef81-453">**NX_DNS_NO_SERVER**: (0xA1) DNS サーバー アドレスが指定されていません</span><span class="sxs-lookup"><span data-stu-id="9ef81-453">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="9ef81-454">**NX_DNS_QUERY_FAILED**: (0xA3) クエリの応答を受信しませんでした</span><span class="sxs-lookup"><span data-stu-id="9ef81-454">**NX_DNS_QUERY_FAILED**: (0xA3) Received no response to query</span></span>
- <span data-ttu-id="9ef81-455">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) 入力アドレスが Null です</span><span class="sxs-lookup"><span data-stu-id="9ef81-455">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null input address</span></span>
- <span data-ttu-id="9ef81-456">**NX_DNS_INVALID_ADDRESS_TYPE**: (0xB2) インデックスが無効なアドレスの種類 (IPv6 など) を指しています</span><span class="sxs-lookup"><span data-stu-id="9ef81-456">**NX_DNS_INVALID_ADDRESS_TYPE**: (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="9ef81-457">**NX_DNS_PARAM_ERROR**: (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-457">**NX_DNS_PARAM_ERROR**: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="9ef81-458">NX_PTR_ERROR: (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-458">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9ef81-459">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-459">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-460">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-460">Allowed From</span></span>

<span data-ttu-id="9ef81-461">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-461">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-462">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-462">Example</span></span>

```c
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */

```

## <a name="nx_dns_host_by_name_get"></a><span data-ttu-id="9ef81-463">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="9ef81-463">nx_dns_host_by_name_get</span></span>

<span data-ttu-id="9ef81-464">ホスト名から IP アドレスを検索する</span><span class="sxs-lookup"><span data-stu-id="9ef81-464">Look up an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-465">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-465">Prototype</span></span>

```c
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9ef81-466">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-466">Description</span></span>

<span data-ttu-id="9ef81-467">このサービスは、アプリケーションによって以前に指定された 1 つ以上の DNS サーバーに、*host_name* が指す指定された名前の名前解決を要求します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-467">This service requests name resolution of the supplied name, pointed to by *host_name*, from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="9ef81-468">成功すると、関連付けられた IP アドレスが、*host_address_ptr* が指す宛先に返されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-468">If successful, the associated IP address is returned in the destination pointed to by *host_address_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-469">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-469">Input Parameters</span></span>

- <span data-ttu-id="9ef81-470">**dns_ptr**: 以前に作成された DNS インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-470">**dns_ptr**: Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="9ef81-471">**host_name**: ホスト名へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-471">**host_name**: Pointer to host name</span></span>
- <span data-ttu-id="9ef81-472">**host_address_ptr**: DNS ホストの IP アドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-472">**host_address_ptr**: Pointer to DNS host IP address</span></span>
- <span data-ttu-id="9ef81-473">**wait_option**: このサービスが DNS 解決を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-473">**wait_option**: Defines how long the service will wait for the DNS resolution.</span></span> <span data-ttu-id="9ef81-474">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-474">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="9ef81-475">**タイムアウト値**: (0x00000001 から 0xFFFFFFFE) 数値 (1 から 0xFFFFFFFE) を選択すると、DNS 解決を待機して中断を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-475">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>
    - <span data-ttu-id="9ef81-476">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、DNS サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-476">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-477">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-477">Return Values</span></span>

- <span data-ttu-id="9ef81-478">**NX_SUCCESS**: (0x00) DNS 解決が成功しました</span><span class="sxs-lookup"><span data-stu-id="9ef81-478">**NX_SUCCESS**: (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="9ef81-479">**NX_DNS_NO_SERVER**: (0xA1) DNS サーバー アドレスが指定されていません</span><span class="sxs-lookup"><span data-stu-id="9ef81-479">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="9ef81-480">**NX_DNS_QUERY_FAILED**: (0xA3) クエリの応答を受信しませんでした</span><span class="sxs-lookup"><span data-stu-id="9ef81-480">**NX_DNS_QUERY_FAILED**: (0xA3) Received no response to query</span></span>
- <span data-ttu-id="9ef81-481">NX_DNS_PARAM_ERROR: (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-481">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="9ef81-482">NX_PTR_ERROR: (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-482">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9ef81-483">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-483">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-484">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-484">Allowed From</span></span>

<span data-ttu-id="9ef81-485">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-485">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-486">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-486">Example</span></span>
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

## <a name="nx_dns_host_text_get"></a><span data-ttu-id="9ef81-487">nx_dns_host_text_get</span><span class="sxs-lookup"><span data-stu-id="9ef81-487">nx_dns_host_text_get</span></span>

<span data-ttu-id="9ef81-488">入力ドメイン名のテキスト文字列を検索する</span><span class="sxs-lookup"><span data-stu-id="9ef81-488">Look up the text string for the input domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-489">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-489">Prototype</span></span>

```c
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9ef81-490">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-490">Description</span></span>

<span data-ttu-id="9ef81-491">このサービスでは、指定されたドメイン名とバッファーを使用して TXT タイプのクエリを送信し、任意の文字列データを取得します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-491">This service sends a query of type TXT with the specified domain name and buffer to obtain the arbitrary string data.</span></span>

<span data-ttu-id="9ef81-492">DNS クライアントは、DNS サーバー応答の TXT レコードのテキスト文字列を、*record_buffer* のメモリ位置にコピーします。</span><span class="sxs-lookup"><span data-stu-id="9ef81-492">The DNS Client copies the text string in the TXT record in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="9ef81-493">データを受信するために、*record_buffer* が 4 バイト アラインされている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9ef81-493">The *record_buffer* does not need to be 4-byte aligned to receive the data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-494">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-494">Input Parameters</span></span>

- <span data-ttu-id="9ef81-495">**dns_ptr**: DNS クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-495">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="9ef81-496">**host_name**: 検索を実行するホストの名前へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-496">**host_name**: Pointer to name of host to search on</span></span>
- <span data-ttu-id="9ef81-497">**record_buffer**: TXT データを抽出する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-497">**record_buffer**: Pointer to location to extract TXT data into</span></span>
- <span data-ttu-id="9ef81-498">**buffer_size**: TXT データを保持するバッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="9ef81-498">**buffer_size**: Size of buffer to hold TXT data</span></span>
- <span data-ttu-id="9ef81-499">**wait_option**: DNS サーバー応答を受信する際の待機オプション</span><span class="sxs-lookup"><span data-stu-id="9ef81-499">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-500">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-500">Return Values</span></span>

- <span data-ttu-id="9ef81-501">**NX_SUCCESS**: (0x00) TXT 文字列が正常に取得されました</span><span class="sxs-lookup"><span data-stu-id="9ef81-501">**NX_SUCCESS**: (0x00) Successfully TXT string obtained</span></span>
- <span data-ttu-id="9ef81-502">**NX_DNS_NO_SERVER**: (0xA1) クライアントのサーバー リストが空です</span><span class="sxs-lookup"><span data-stu-id="9ef81-502">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="9ef81-503">**NX_DNS_QUERY_FAILED**: (0xA3) 有効な DNS 応答を受信していません</span><span class="sxs-lookup"><span data-stu-id="9ef81-503">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="9ef81-504">NX_PTR_ERROR: (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-504">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9ef81-505">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-505">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="9ef81-506">NX_DNS_PARAM_ERROR: (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-506">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-507">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-507">Allowed From</span></span>

<span data-ttu-id="9ef81-508">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-508">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-509">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-509">Example</span></span>

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

## <a name="nx_dns_packet_pool_set"></a><span data-ttu-id="9ef81-510">nx_dns_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="9ef81-510">nx_dns_packet_pool_set</span></span>

<span data-ttu-id="9ef81-511">DNS クライアントのパケット プールを設定する</span><span class="sxs-lookup"><span data-stu-id="9ef81-511">Set the DNS Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-512">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-512">Prototype</span></span>

```c
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="9ef81-513">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-513">Description</span></span>

<span data-ttu-id="9ef81-514">このサービスは、以前に作成されたパケット プールを、DNS **クライアント** のパケット プールとして設定します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-514">This service sets a previously created packet pool as the DNS **Client** packet pool.</span></span> <span data-ttu-id="9ef81-515">DNS クライアントでは、このパケット プールを使用して DNS クエリを送信します。そのため、パケット ペイロードは、イーサネット フレーム、IP ヘッダー、および UDP ヘッダーを含む NX_DNS_PACKET_PAYLOAD_UNALIGNED (*nx_dns.h* で定義) よりも小さくすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9ef81-515">The DNS Client will use this packet pool to send DNS queries, so the packet payload should not be less than NX_DNS_PACKET_PAYLOAD_UNALIGNED which includes the Ethernet frame, IP and UDP headers and is defined in *nx_dns.h*.</span></span>
 
>[!NOTE]
><span data-ttu-id="9ef81-516">DNS クライアントが削除されても、パケット プールは一緒に削除されません。不要になったパケット プールを削除するのはアプリケーションの役割です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-516">When the DNS Client is deleted, the packet pool is not deleted with it and it is the responsibility of the application to delete the packet pool when it no longer needs it.</span></span>

>[!NOTE]
><span data-ttu-id="9ef81-517">このサービスは、*nx_dns.h* で構成オプション NX_DNS_CLIENT_USER_CREATE_PACKET_POOL が定義されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-517">This service is only available if the configuration option NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined in *nx_dns.h*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-518">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-518">Input Parameters</span></span>

- <span data-ttu-id="9ef81-519">**dns_ptr**: 以前に作成された DNS **クライアント** インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-519">**dns_ptr**: Pointer to previously created DNS **Client** instance.</span></span>
- <span data-ttu-id="9ef81-520">**pool_ptr**: 以前に作成されたパケット プールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-520">**pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-521">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-521">Return Values</span></span>

- <span data-ttu-id="9ef81-522">**NX_SUCCESS**: (0x00) 正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="9ef81-522">**NX_SUCCESS**: (0x00) Successful completion.</span></span>
- <span data-ttu-id="9ef81-523">**NX_NOT_ENABLED**: (0x14) クライアントがこのオプション用に構成されていません</span><span class="sxs-lookup"><span data-stu-id="9ef81-523">**NX_NOT_ENABLED**: (0x14) Client not configured for this option</span></span>
- <span data-ttu-id="9ef81-524">NX_PTR_ERROR: (0x07) IP または DNS **クライアント** ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-524">NX_PTR_ERROR: (0x07) Invalid IP or DNS **Client** pointer.</span></span>
- <span data-ttu-id="9ef81-525">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-525">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-526">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-526">Allowed From</span></span>

<span data-ttu-id="9ef81-527">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-527">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-528">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-528">Example</span></span>
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

## <a name="nx_dns_server_add"></a><span data-ttu-id="9ef81-529">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="9ef81-529">nx_dns_server_add</span></span>

<span data-ttu-id="9ef81-530">DNS サーバーの IP アドレスを追加する</span><span class="sxs-lookup"><span data-stu-id="9ef81-530">Add DNS Server IP Address</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-531">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-531">Prototype</span></span>

```c
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="9ef81-532">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-532">Description</span></span>

<span data-ttu-id="9ef81-533">このサービスは、サーバー リストに IPv4 DNS サーバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-533">This service adds an IPv4 DNS Server to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-534">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-534">Input Parameters</span></span>

- <span data-ttu-id="9ef81-535">**dns_ptr**: DNS 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-535">**dns_ptr**: Pointer to DNS control block.</span></span>  
- <span data-ttu-id="9ef81-536">**server_address**: DNS サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="9ef81-536">**server_address**: IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-537">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-537">Return Values</span></span>

- <span data-ttu-id="9ef81-538">**NX_SUCCESS**: (0x00) サーバーが正常に追加されました</span><span class="sxs-lookup"><span data-stu-id="9ef81-538">**NX_SUCCESS**: (0x00) Server successfully added</span></span>
- <span data-ttu-id="9ef81-539">**NX_DNS_DUPLICATE_ENTRY** または **NX_NO_MORE_ENTRIES**: (0x17) これ以上の DNS サーバーは許可されません (リストがいっぱいです)</span><span class="sxs-lookup"><span data-stu-id="9ef81-539">**NX_DNS_DUPLICATE_ENTRY** or **NX_NO_MORE_ENTRIES**: (0x17) No more DNS Servers Allowed (list is full)</span></span>
- <span data-ttu-id="9ef81-540">**NX_DNS_PARAM_ERROR**: (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-540">**NX_DNS_PARAM_ERROR**: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="9ef81-541">NX_PTR_ERROR: (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-541">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9ef81-542">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-542">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="9ef81-543">NX_DNS_BAD_ADDRESS_ERROR: (0xA4) サーバー アドレス入力が Null です</span><span class="sxs-lookup"><span data-stu-id="9ef81-543">NX_DNS_BAD_ADDRESS_ERROR: (0xA4) Null server address input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-544">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-544">Allowed From</span></span>

<span data-ttu-id="9ef81-545">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-545">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-546">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-546">Example</span></span>

```c
/* Add a DNS Server at IP address 202.2.2.13.  */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added.  */
```

## <a name="nx_dns_server_get"></a><span data-ttu-id="9ef81-547">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="9ef81-547">nx_dns_server_get</span></span>

<span data-ttu-id="9ef81-548">クライアント リストから IPv4 DNS サーバーを返す</span><span class="sxs-lookup"><span data-stu-id="9ef81-548">Return an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-549">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-549">Prototype</span></span>

```c
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                       ULONG *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="9ef81-550">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-550">Description</span></span>

<span data-ttu-id="9ef81-551">このサービスは、サーバー リストの指定されたインデックスにある IPv4 DNS サーバー アドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-551">This service returns the IPv4 DNS Server address from the server list at the specified index.</span></span> <span data-ttu-id="9ef81-552">インデックスは 0 から始まることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9ef81-552">Note that the index is zero based.</span></span> <span data-ttu-id="9ef81-553">入力インデックスが DNS クライアントのリストのサイズを超えた場合は、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-553">If the input index exceeds the size of the DNS Client list, an error is returned.</span></span> <span data-ttu-id="9ef81-554">*nx_dns_get_serverlist_size* サービスを最初に呼び出して、クライアントのリスト内の DNS サーバーの数を取得できます。</span><span class="sxs-lookup"><span data-stu-id="9ef81-554">The *nx_dns_get_serverlist_size* service may be called first obtain the number of DNS servers in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-555">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-555">Input Parameters</span></span>

- <span data-ttu-id="9ef81-556">**dns_ptr**: DNS 制御ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-556">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="9ef81-557">**index**: DNS クライアントのサーバー リストへのインデックス</span><span class="sxs-lookup"><span data-stu-id="9ef81-557">**index**: Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="9ef81-558">**dns_server_address**: DNS サーバーの IP アドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="9ef81-558">**dns_server_address**: Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-559">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-559">Return Values</span></span>

- <span data-ttu-id="9ef81-560">**NX_SUCCESS**: (0x00) サーバーが正常に返されました</span><span class="sxs-lookup"><span data-stu-id="9ef81-560">**NX_SUCCESS**: (0x00) Successful server returned</span></span>
- <span data-ttu-id="9ef81-561">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) インデックスが空のスロットを指しています</span><span class="sxs-lookup"><span data-stu-id="9ef81-561">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="9ef81-562">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) インデックスが Null アドレスを指しています</span><span class="sxs-lookup"><span data-stu-id="9ef81-562">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Index points to Null address</span></span>
- <span data-ttu-id="9ef81-563">**NX_DNS_PARAM_ERROR**: (0xA8) インデックスがリストのサイズを超えています</span><span class="sxs-lookup"><span data-stu-id="9ef81-563">**NX_DNS_PARAM_ERROR**: (0xA8) Index exceeds size of list</span></span>
- <span data-ttu-id="9ef81-564">NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-564">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="9ef81-565">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-565">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-566">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-566">Allowed From</span></span>

<span data-ttu-id="9ef81-567">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-568">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-568">Example</span></span>

```c
ULONG     my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list.  */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned.  */
```

## <a name="nx_dns_server_remove"></a><span data-ttu-id="9ef81-569">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="9ef81-569">nx_dns_server_remove</span></span>

<span data-ttu-id="9ef81-570">クライアントのリストから IPv4 DNS サーバーを削除する</span><span class="sxs-lookup"><span data-stu-id="9ef81-570">Remove an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-571">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-571">Prototype</span></span>

```c
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="9ef81-572">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-572">Description</span></span>

<span data-ttu-id="9ef81-573">このサービスは、クライアントのリストから IPv4 DNS サーバーを削除します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-573">This service removes an IPv4 DNS Server from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-574">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-574">Input Parameters</span></span>

- <span data-ttu-id="9ef81-575">**dns_ptr**: DNS 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-575">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="9ef81-576">**server_address**: DNS サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="9ef81-576">**server_address**: IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-577">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-577">Return Values</span></span>

- <span data-ttu-id="9ef81-578">**NX_SUCCESS**: (0x00) DNS サーバーが正常に削除されました</span><span class="sxs-lookup"><span data-stu-id="9ef81-578">**NX_SUCCESS**: (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="9ef81-579">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) サーバーがクライアントのリストにありません</span><span class="sxs-lookup"><span data-stu-id="9ef81-579">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="9ef81-580">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) サーバー アドレス入力が Null です</span><span class="sxs-lookup"><span data-stu-id="9ef81-580">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null server address input</span></span>
- <span data-ttu-id="9ef81-581">NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-581">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="9ef81-582">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-582">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-583">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-583">Allowed From</span></span>

<span data-ttu-id="9ef81-584">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-584">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-585">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-585">Example</span></span>

```c
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nx_dns_server_remove_all"></a><span data-ttu-id="9ef81-586">nx_dns_server_remove_all</span><span class="sxs-lookup"><span data-stu-id="9ef81-586">nx_dns_server_remove_all</span></span>

<span data-ttu-id="9ef81-587">クライアントのリストからすべての DNS サーバーを削除する</span><span class="sxs-lookup"><span data-stu-id="9ef81-587">Remove all DNS Servers from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="9ef81-588">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="9ef81-588">Prototype</span></span>

```c
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="9ef81-589">説明</span><span class="sxs-lookup"><span data-stu-id="9ef81-589">Description</span></span>

<span data-ttu-id="9ef81-590">このサービスは、クライアントのリストからすべての DNS サーバーを削除します。</span><span class="sxs-lookup"><span data-stu-id="9ef81-590">This service removes all DNS Servers from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ef81-591">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef81-591">Input Parameters</span></span>

- <span data-ttu-id="9ef81-592">**dns_ptr**: DNS 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ef81-592">**dns_ptr**: Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="9ef81-593">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef81-593">Return Values</span></span>

- <span data-ttu-id="9ef81-594">**NX_SUCCESS**: (0x00) DNS サーバーが正常に削除されました</span><span class="sxs-lookup"><span data-stu-id="9ef81-594">**NX_SUCCESS**: (0x00) DNS Servers successfully removed</span></span>
- <span data-ttu-id="9ef81-595">**NX_DNS_ERROR**: (0xA0) 保護ミューテックスを取得できません</span><span class="sxs-lookup"><span data-stu-id="9ef81-595">**NX_DNS_ERROR**: (0xA0) Unable to obtain protection mutex</span></span>
- <span data-ttu-id="9ef81-596">NX_PTR_ERROR: (0x07) IP または DNS ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="9ef81-596">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="9ef81-597">NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="9ef81-597">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ef81-598">許可元</span><span class="sxs-lookup"><span data-stu-id="9ef81-598">Allowed From</span></span>

<span data-ttu-id="9ef81-599">Threads</span><span class="sxs-lookup"><span data-stu-id="9ef81-599">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ef81-600">例</span><span class="sxs-lookup"><span data-stu-id="9ef81-600">Example</span></span>

```c

/* Remove all DNS Servers from the Client list.  */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed.  */
```